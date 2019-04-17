---
title: Renderização de volume
description: Imagens volumétricas contêm informações ricas com opacidade e a cor em todo o volume que não pode ser facilmente expressos como superfícies. Saiba como processar com eficiência volumétricas imagens em realidade mista do Windows.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: imagem volumétricas, renderização de volume, desempenho, realidade mista
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590813"
---
# <a name="volume-rendering"></a>Renderização de volume

Para os médicos MRI ou volumes de engenharia, consulte [Volume de processamento na Wikipédia](https://en.wikipedia.org/wiki/Volume_rendering). Essas 'imagens volumétricas' contêm informações ricas com opacidade e a cor em todo o volume que não pode ser facilmente expressos como superfícies, como [malhas poligonais](https://en.wikipedia.org/wiki/Polygon_mesh).

Soluções-chave para melhorar o desempenho
1. RUIM: Abordagem simples: Mostrar o Volume inteiro, geralmente é executado muito lentamente
2. BOA: Plano de recorte: Mostrar apenas uma única fatia do volume
3. BOA: Volume de subpropriedades Cutting: Mostrar apenas algumas camadas do volume
4. BOA: Diminuir a resolução do processamento de volume (consulte 'Misto a renderização de cena resolução')

Há apenas uma determinada quantidade de informações que podem ser transferidas do aplicativo para a tela em um quadro específico, essa é a largura de banda total de memória. Também qualquer processamento (ou 'sombreamento') necessárias para transformar os dados para a apresentação também requer tempo. Principais considerações ao fazer a renderização de volume são assim:
* Largura da tela * altura da tela * contagem de tela * Volume camadas-em-que-Pixel = Total de amostras de Volume por quadro
* 1028 * 720 * 2 * 256 = 378961920 (100%) (res de volume completo: muitas amostras)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% do total) (fatia fina de: 1 exemplo por pixel, é executado sem problemas)
* 1028 * 720 * 2 * 10 = 14803200 (3.9% do total) (fatia subpropriedades de volume: 10 amostras por pixel, executado perfeitamente bem, parece 3d)
* 200 * 200 * 2 * 256 = 20480000 (5% do total) (Diminuir volume res: menos pixels, volume completo, desfoqueY 3d, mas um pouco de pesquisa)

## <a name="representing-3d-textures"></a>Que representa as texturas 3D

CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

Na GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Sombreamento e gradientes

Como sombrear um volume, como MRI, para visualização útil. O método principal é ter uma janela de intensidade' ' (um min e max) que você deseja ver intensidades dentro e simplesmente dimensionar nesse espaço para ver a intensidade de preto e branca. 'Rampa de cores' pode ser aplicada aos valores dentro desse intervalo e armazenada como uma textura para que diferentes partes do espectro intensidade possam ser sombreadas cores diferentes:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

Em muitos nossos aplicativos armazenamos em nosso volume de um valor de intensidade brutos e um índice de segmentação' ' (para segmentar partes diferentes, como capa e bem-acabados, esses segmentos são geralmente criados por especialistas em ferramentas dedicados). Isso pode ser combinado com a abordagem acima para colocar uma cor diferente ou painel de cores diferentes para cada índice de segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Volume em um sombreador de divisão

Uma excelente primeira etapa é criar um "plano de recorte" que pode percorrer o volume 'divisão', e como a verificação de valores em cada ponto. Isso pressupõe que há um cubo 'VolumeSpace', que representa onde o volume é no espaço de mundo, que pode ser usado como uma referência para colocar os pontos:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Rastreamento de volume em sombreadores

Como usar a GPU para fazer o rastreamento de subpropriedades de volume (orienta voxels algumas camadas profunda, em seguida, nos dados de volta para a frente):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Renderização de Volume inteiro

Modificando o código de subpropriedades de volume acima, podemos obter:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Renderização de cena resolução misto

Como renderizar uma parte da cena com uma baixa resolução e colocá-lo no lugar:
1. Configurar dois câmeras fora da tela, uma para siga cada olho que atualizar cada quadro
2. A instalação duas baixa resolução renderizar destinos (digamos 200 x 200 cada), que as câmeras renderizam em
3. Configurar um quad que se move na frente do usuário

Cada quadro:
1. Desenhar os destinos de renderização para cada olho em baixa resolução (dados de volume, sombreadores caros, etc.)
2. Desenhar a cena normalmente como uma solução completa (malhas, interface do usuário, etc.)
3. Desenhe um quad na frente do usuário, ao longo da cena e projetar os renderizadores de baixa resolução em que.
4. Resultado: a combinação visual de elementos de alta resolução com dados do volume de baixa resolução mas alta densidade.

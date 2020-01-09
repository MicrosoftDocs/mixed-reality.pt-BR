---
title: Renderização de volume
description: As imagens volumétricos contêm informações ricas com opacidade e cores em todo o volume que não podem ser facilmente expressas como superfícies. Saiba como renderizar com eficiência imagens volumétricos dentro da realidade mista do Windows.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: imagem volumétricos, renderização de volume, desempenho, realidade misturada
ms.openlocfilehash: 04931df5e4225225e4c11c3f6d72801e2d58f646
ms.sourcegitcommit: 317653cd8500563c514464f0337c1f230a6f3653
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/28/2019
ms.locfileid: "75503824"
---
# <a name="volume-rendering"></a>Renderização de volume

Para MRI médico ou volumes de engenharia, confira [renderização de volume na Wikipédia](https://en.wikipedia.org/wiki/Volume_rendering). Essas "imagens volumétricoss" contêm informações avançadas com opacidade e cor em todo o volume que não podem ser facilmente expressas como superfícies como [malhas poligonal](https://en.wikipedia.org/wiki/Polygon_mesh).

Principais soluções para melhorar o desempenho
1. MÁ: abordagem ingênua: mostrar volume inteiro, geralmente é executado muito lentamente
2. BOM: plano de corte: mostra apenas uma única fatia do volume
3. BOA: recortando o subvolume: mostrar apenas algumas camadas do volume
4. BOM: Reduza a resolução da renderização de volume (consulte ' renderização de cena de resolução mista ')

Há apenas uma determinada quantidade de informações que podem ser transferidas do aplicativo para a tela em qualquer quadro específico, que é a largura de banda de memória total. Além disso, qualquer processamento (ou ' sombreamento ') necessário para transformar os dados para apresentação requer tempo. As principais considerações ao fazer a renderização de volume são:
* Largura da tela * tela-altura * tela-contagem * volume-camadas-em-pixel = total-volume-amostras por quadro
* 1028 * 720 * 2 * 256 = 378961920 (100%) (volume de resolução completa: muitos exemplos)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% de completo) (fatia fina: 1 amostra por pixel, é executado sem problemas)
* 1028 * 720 * 2 * 10 = 14803200 (3,9% de completo) (fatia de subvolume: 10 amostras por pixel, é executada razoavelmente suavemente, parece 3D)
* 200 * 200 * 2 * 256 = 20480000 (5% de completo) (volume de resolução inferior: menos pixels, volume completo, parece 3D, mas um pouco borrado)

## <a name="representing-3d-textures"></a>Representando texturas 3D

Na CPU:

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

Como sombrear um volume, como MRI, para visualização útil. O método principal é ter uma ' janela de intensidade ' (um mínimo e um máximo) que você deseja ver as intensidades dentro e simplesmente dimensionar esse espaço para ver a intensidade de preto e branco. Um ' Ramp de cores ' pode ser aplicado aos valores dentro desse intervalo e armazenado como uma textura, de modo que partes diferentes do espectro de intensidade possam ser sombreadas em cores diferentes:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

Em muitos de nossos aplicativos, armazenamos em nosso volume um valor de intensidade bruta e um "índice de segmentação" (para segmentar partes diferentes, como Skin e Bone; geralmente, esses segmentos são criados por especialistas em ferramentas dedicadas). Isso pode ser combinado com a abordagem acima para colocar uma cor diferente ou até mesmo uma rampa de cores diferente para cada índice de segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Divisão de volume em um sombreador

Uma ótima primeira etapa é criar um "plano de divisão" que possa passar pelo volume, "dividindo-o" e como os valores de verificação em cada ponto. Isso pressupõe que haja um cubo ' VolumeSpace ', que representa onde o volume está no espaço de mundo, que pode ser usado como uma referência para colocar os pontos:

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

Como usar a GPU para fazer o rastreamento de subvolume (percorre algumas voxels de fundo e camadas nos dados de volta para frente):

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

## <a name="whole-volume-rendering"></a>Renderização de volume inteira

Modificando o código de subvolume acima, obtemos:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Renderização de cena de resolução mista

Como renderizar uma parte da cena com uma baixa resolução e colocá-la de volta em vigor:
1. Configurar duas câmeras fora da tela, uma para seguir cada olho que atualiza cada quadro
2. Configurar dois destinos de renderização de baixa resolução (ou seja, 200 x 200 cada) que as câmeras renderizam
3. Configurar um quad que se move para a frente do usuário

Cada quadro:
1. Desenhe os destinos de renderização para cada olho em baixa resolução (dados de volume, sombreadores caros, etc.)
2. Desenhe a cena normalmente como resolução completa (malhas, interface do usuário, etc.)
3. Desenhe um quad na frente do usuário, por meio da cena, e projeto os renderizadores de baixa res para isso
4. Resultado: combinação visual de elementos de resolução completa com dados de volume de baixa resolução, mas de alta densidade

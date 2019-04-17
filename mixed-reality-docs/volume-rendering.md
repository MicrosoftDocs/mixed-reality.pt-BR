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
# <a name="volume-rendering"></a><span data-ttu-id="6f983-105">Renderização de volume</span><span class="sxs-lookup"><span data-stu-id="6f983-105">Volume rendering</span></span>

<span data-ttu-id="6f983-106">Para os médicos MRI ou volumes de engenharia, consulte [Volume de processamento na Wikipédia](https://en.wikipedia.org/wiki/Volume_rendering).</span><span class="sxs-lookup"><span data-stu-id="6f983-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="6f983-107">Essas 'imagens volumétricas' contêm informações ricas com opacidade e a cor em todo o volume que não pode ser facilmente expressos como superfícies, como [malhas poligonais](https://en.wikipedia.org/wiki/Polygon_mesh).</span><span class="sxs-lookup"><span data-stu-id="6f983-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="6f983-108">Soluções-chave para melhorar o desempenho</span><span class="sxs-lookup"><span data-stu-id="6f983-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="6f983-109">RUIM: Abordagem simples: Mostrar o Volume inteiro, geralmente é executado muito lentamente</span><span class="sxs-lookup"><span data-stu-id="6f983-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="6f983-110">BOA: Plano de recorte: Mostrar apenas uma única fatia do volume</span><span class="sxs-lookup"><span data-stu-id="6f983-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="6f983-111">BOA: Volume de subpropriedades Cutting: Mostrar apenas algumas camadas do volume</span><span class="sxs-lookup"><span data-stu-id="6f983-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="6f983-112">BOA: Diminuir a resolução do processamento de volume (consulte 'Misto a renderização de cena resolução')</span><span class="sxs-lookup"><span data-stu-id="6f983-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="6f983-113">Há apenas uma determinada quantidade de informações que podem ser transferidas do aplicativo para a tela em um quadro específico, essa é a largura de banda total de memória.</span><span class="sxs-lookup"><span data-stu-id="6f983-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="6f983-114">Também qualquer processamento (ou 'sombreamento') necessárias para transformar os dados para a apresentação também requer tempo.</span><span class="sxs-lookup"><span data-stu-id="6f983-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="6f983-115">Principais considerações ao fazer a renderização de volume são assim:</span><span class="sxs-lookup"><span data-stu-id="6f983-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="6f983-116">Largura da tela \* altura da tela \* contagem de tela \* Volume camadas-em-que-Pixel = Total de amostras de Volume por quadro</span><span class="sxs-lookup"><span data-stu-id="6f983-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="6f983-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (res de volume completo: muitas amostras)</span><span class="sxs-lookup"><span data-stu-id="6f983-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="6f983-118">1028 \* 720 \* 2 \* 1 = 1480320 (0,3% do total) (fatia fina de: 1 exemplo por pixel, é executado sem problemas)</span><span class="sxs-lookup"><span data-stu-id="6f983-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="6f983-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% do total) (fatia subpropriedades de volume: 10 amostras por pixel, executado perfeitamente bem, parece 3d)</span><span class="sxs-lookup"><span data-stu-id="6f983-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="6f983-120">200 \* 200 \* 2 \* 256 = 20480000 (5% do total) (Diminuir volume res: menos pixels, volume completo, desfoqueY 3d, mas um pouco de pesquisa)</span><span class="sxs-lookup"><span data-stu-id="6f983-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="6f983-121">Que representa as texturas 3D</span><span class="sxs-lookup"><span data-stu-id="6f983-121">Representing 3D Textures</span></span>

<span data-ttu-id="6f983-122">CPU:</span><span class="sxs-lookup"><span data-stu-id="6f983-122">On the CPU:</span></span>

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

<span data-ttu-id="6f983-123">Na GPU:</span><span class="sxs-lookup"><span data-stu-id="6f983-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="6f983-124">Sombreamento e gradientes</span><span class="sxs-lookup"><span data-stu-id="6f983-124">Shading and Gradients</span></span>

<span data-ttu-id="6f983-125">Como sombrear um volume, como MRI, para visualização útil.</span><span class="sxs-lookup"><span data-stu-id="6f983-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="6f983-126">O método principal é ter uma janela de intensidade' ' (um min e max) que você deseja ver intensidades dentro e simplesmente dimensionar nesse espaço para ver a intensidade de preto e branca.</span><span class="sxs-lookup"><span data-stu-id="6f983-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="6f983-127">'Rampa de cores' pode ser aplicada aos valores dentro desse intervalo e armazenada como uma textura para que diferentes partes do espectro intensidade possam ser sombreadas cores diferentes:</span><span class="sxs-lookup"><span data-stu-id="6f983-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="6f983-128">Em muitos nossos aplicativos armazenamos em nosso volume de um valor de intensidade brutos e um índice de segmentação' ' (para segmentar partes diferentes, como capa e bem-acabados, esses segmentos são geralmente criados por especialistas em ferramentas dedicados).</span><span class="sxs-lookup"><span data-stu-id="6f983-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="6f983-129">Isso pode ser combinado com a abordagem acima para colocar uma cor diferente ou painel de cores diferentes para cada índice de segmento:</span><span class="sxs-lookup"><span data-stu-id="6f983-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="6f983-130">Volume em um sombreador de divisão</span><span class="sxs-lookup"><span data-stu-id="6f983-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="6f983-131">Uma excelente primeira etapa é criar um "plano de recorte" que pode percorrer o volume 'divisão', e como a verificação de valores em cada ponto.</span><span class="sxs-lookup"><span data-stu-id="6f983-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="6f983-132">Isso pressupõe que há um cubo 'VolumeSpace', que representa onde o volume é no espaço de mundo, que pode ser usado como uma referência para colocar os pontos:</span><span class="sxs-lookup"><span data-stu-id="6f983-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="6f983-133">Rastreamento de volume em sombreadores</span><span class="sxs-lookup"><span data-stu-id="6f983-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="6f983-134">Como usar a GPU para fazer o rastreamento de subpropriedades de volume (orienta voxels algumas camadas profunda, em seguida, nos dados de volta para a frente):</span><span class="sxs-lookup"><span data-stu-id="6f983-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="6f983-135">Renderização de Volume inteiro</span><span class="sxs-lookup"><span data-stu-id="6f983-135">Whole Volume Rendering</span></span>

<span data-ttu-id="6f983-136">Modificando o código de subpropriedades de volume acima, podemos obter:</span><span class="sxs-lookup"><span data-stu-id="6f983-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="6f983-137">Renderização de cena resolução misto</span><span class="sxs-lookup"><span data-stu-id="6f983-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="6f983-138">Como renderizar uma parte da cena com uma baixa resolução e colocá-lo no lugar:</span><span class="sxs-lookup"><span data-stu-id="6f983-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="6f983-139">Configurar dois câmeras fora da tela, uma para siga cada olho que atualizar cada quadro</span><span class="sxs-lookup"><span data-stu-id="6f983-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="6f983-140">A instalação duas baixa resolução renderizar destinos (digamos 200 x 200 cada), que as câmeras renderizam em</span><span class="sxs-lookup"><span data-stu-id="6f983-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="6f983-141">Configurar um quad que se move na frente do usuário</span><span class="sxs-lookup"><span data-stu-id="6f983-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="6f983-142">Cada quadro:</span><span class="sxs-lookup"><span data-stu-id="6f983-142">Each Frame:</span></span>
1. <span data-ttu-id="6f983-143">Desenhar os destinos de renderização para cada olho em baixa resolução (dados de volume, sombreadores caros, etc.)</span><span class="sxs-lookup"><span data-stu-id="6f983-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="6f983-144">Desenhar a cena normalmente como uma solução completa (malhas, interface do usuário, etc.)</span><span class="sxs-lookup"><span data-stu-id="6f983-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="6f983-145">Desenhe um quad na frente do usuário, ao longo da cena e projetar os renderizadores de baixa resolução em que.</span><span class="sxs-lookup"><span data-stu-id="6f983-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="6f983-146">Resultado: a combinação visual de elementos de alta resolução com dados do volume de baixa resolução mas alta densidade.</span><span class="sxs-lookup"><span data-stu-id="6f983-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>

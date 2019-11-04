---
title: Estudo de caso-dimensionamento de Datascape em dispositivos com desempenho diferente
description: Esse estudo de caso oferece informações sobre como os desenvolvedores da Microsoft otimizaram o aplicativo Datascape para fornecer uma experiência atraente nos dispositivos com uma variedade de recursos de desempenho.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Headset de imersão, otimização de desempenho, VR, estudo de caso
ms.openlocfilehash: 05f97188c81d85685540be998111ecfc47d9ef9c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436509"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="f74b4-104">Estudo de caso-dimensionamento de Datascape em dispositivos com desempenho diferente</span><span class="sxs-lookup"><span data-stu-id="f74b4-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="f74b4-105">O Datascape é um aplicativo de realidade mista do Windows desenvolvido internamente na Microsoft, no qual nos concentramos na exibição de dados meteorológicos sobre os dados do terreno.</span><span class="sxs-lookup"><span data-stu-id="f74b4-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="f74b4-106">O aplicativo explora os usuários de insights exclusivos que aproveitam a descoberta de dados em realidade misturada ao redor do usuário com a visualização de dados do Holographic.</span><span class="sxs-lookup"><span data-stu-id="f74b4-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="f74b4-107">Para o Datascape, queríamos ter como alvo uma variedade de plataformas com diferentes recursos de hardware, desde o Microsoft HoloLens até o Windows Mixed realness headsets e de PCs de baixo consumo até os computadores mais recentes com GPU de ponta.</span><span class="sxs-lookup"><span data-stu-id="f74b4-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="f74b4-108">O principal desafio era renderizar nossa cena em uma questão visualmente atraente em dispositivos com recursos gráficos muito diferentes durante a execução em uma taxa de quadros alta.</span><span class="sxs-lookup"><span data-stu-id="f74b4-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="f74b4-109">Esse estudo de caso examinará o processo e as técnicas usadas para criar alguns de nossos sistemas mais intensivos de GPU, descrevendo os problemas encontrados e como superou-los.</span><span class="sxs-lookup"><span data-stu-id="f74b4-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="f74b4-110">Transparência e sobredesenho</span><span class="sxs-lookup"><span data-stu-id="f74b4-110">Transparency and overdraw</span></span>

<span data-ttu-id="f74b4-111">Nosso principal esforço de renderização foi resolvido com transparência, pois a transparência pode ser cara em uma GPU.</span><span class="sxs-lookup"><span data-stu-id="f74b4-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="f74b4-112">A geometria sólida pode ser renderizada de frente para trás durante a gravação no buffer de profundidade, interrompendo os pixels futuros localizados atrás desse pixel de serem descartados.</span><span class="sxs-lookup"><span data-stu-id="f74b4-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="f74b4-113">Isso impede que os pixels ocultos executem o sombreador de pixel, acelerando significativamente o processo.</span><span class="sxs-lookup"><span data-stu-id="f74b4-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="f74b4-114">Se a geometria for classificada de forma ideal, cada pixel na tela será desenhado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f74b4-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="f74b4-115">A geometria transparente precisa ser classificada de volta para a frente e se baseia na mesclagem da saída do sombreador de pixel com o pixel atual na tela.</span><span class="sxs-lookup"><span data-stu-id="f74b4-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="f74b4-116">Isso pode resultar em cada pixel na tela que está sendo desenhada várias vezes por quadro, chamado de sobreempate.</span><span class="sxs-lookup"><span data-stu-id="f74b4-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="f74b4-117">Para os computadores HoloLens e mainstream, a tela só pode ser preenchida algumas vezes, tornando o processo transparente de processamento.</span><span class="sxs-lookup"><span data-stu-id="f74b4-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="f74b4-118">Introdução aos componentes de cena do Datascape</span><span class="sxs-lookup"><span data-stu-id="f74b4-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="f74b4-119">Tínhamos três componentes principais para nossa cena; **a interface do usuário, o mapa**e **o clima**.</span><span class="sxs-lookup"><span data-stu-id="f74b4-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="f74b4-120">Sabíamos no início que nossos efeitos meteorológicos exigiriam todo o tempo de GPU que poderia obter, então criamos de forma intencional a interface do usuário e o terreno de uma maneira que reduza qualquer sobreempate.</span><span class="sxs-lookup"><span data-stu-id="f74b4-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="f74b4-121">Retrabalhamos a interface do usuário várias vezes para minimizar a quantidade de sobreempates que ela produziria.</span><span class="sxs-lookup"><span data-stu-id="f74b4-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="f74b4-122">Nós erramosmos o lado da geometria mais complexa em vez de sobrecarregar arte transparente sobre as outras para componentes como botões brilhantes e visões gerais de mapa.</span><span class="sxs-lookup"><span data-stu-id="f74b4-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="f74b4-123">Para o mapa, usamos um sombreador personalizado que distribuiva recursos padrão do Unity, como sombras e iluminação complexa, substituindo-os por um único modelo simples de iluminação de sol e um cálculo de neblina personalizado.</span><span class="sxs-lookup"><span data-stu-id="f74b4-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="f74b4-124">Isso produziu um sombreador de pixel simples e libera ciclos de GPU.</span><span class="sxs-lookup"><span data-stu-id="f74b4-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="f74b4-125">Nós gerenciamos para obter a interface do usuário e o mapa para renderizar no orçamento, onde não precisamos de nenhuma alteração para elas, dependendo do hardware; no entanto, a visualização do clima, em particular, a renderização na nuvem, provou ser mais um desafio!</span><span class="sxs-lookup"><span data-stu-id="f74b4-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="f74b4-126">Plano de fundo em dados de nuvem</span><span class="sxs-lookup"><span data-stu-id="f74b4-126">Background on cloud data</span></span>

<span data-ttu-id="f74b4-127">Nossos dados de nuvem foram baixados de servidores NOAA (https://nomads.ncep.noaa.gov/) e nos vieram em três camadas 2D distintas, cada uma com a altura superior e inferior da nuvem, bem como a densidade da nuvem para cada célula da grade.</span><span class="sxs-lookup"><span data-stu-id="f74b4-127">Our cloud data was downloaded from NOAA servers (https://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="f74b4-128">Os dados foram processados em uma textura de informações de nuvem, em que cada componente foi armazenado no componente vermelho, verde e azul da textura para facilitar o acesso na GPU.</span><span class="sxs-lookup"><span data-stu-id="f74b4-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="f74b4-129">Nuvens de geometria</span><span class="sxs-lookup"><span data-stu-id="f74b4-129">Geometry clouds</span></span>

<span data-ttu-id="f74b4-130">Para garantir que nossos computadores com menor capacidade possam renderizar nossas nuvens, decidimos começar com uma abordagem que usaria uma geometria sólida para minimizar o sobreempate.</span><span class="sxs-lookup"><span data-stu-id="f74b4-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="f74b4-131">Primeiro, tentamos produzir nuvens gerando uma malha heightmap sólida para cada camada usando o raio da textura de informações de nuvem por vértice para gerar a forma.</span><span class="sxs-lookup"><span data-stu-id="f74b4-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="f74b4-132">Usamos um sombreador Geometry para produzir os vértices na parte superior e a parte inferior da nuvem gerando formas de nuvem sólidas.</span><span class="sxs-lookup"><span data-stu-id="f74b4-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="f74b4-133">Usamos o valor de densidade da textura para colorir a nuvem com cores mais escuras para nuvens mais densas.</span><span class="sxs-lookup"><span data-stu-id="f74b4-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="f74b4-134">**Sombreador para criar os vértices:**</span><span class="sxs-lookup"><span data-stu-id="f74b4-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="f74b4-135">Apresentamos um pequeno padrão de ruído para obter mais detalhes sobre os dados reais.</span><span class="sxs-lookup"><span data-stu-id="f74b4-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="f74b4-136">Para produzir bordas de nuvem arredondadas, cortamos os pixels no sombreador de pixel quando o valor de raio interpolado atinge um limite para descartar valores quase zero.</span><span class="sxs-lookup"><span data-stu-id="f74b4-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Nuvens de geometria](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="f74b4-138">Como as nuvens são uma geometria sólida, elas podem ser renderizadas antes que o terreno oculte os pixels de mapa caros abaixo para melhorar ainda mais a taxa de quadros.</span><span class="sxs-lookup"><span data-stu-id="f74b4-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="f74b4-139">Essa solução foi executada bem em todas as placas gráficas de min-spec a placas gráficas de ponta, bem como no HoloLens, devido à abordagem de renderização de geometria sólida.</span><span class="sxs-lookup"><span data-stu-id="f74b4-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="f74b4-140">Nuvens de partículas sólidas</span><span class="sxs-lookup"><span data-stu-id="f74b4-140">Solid particle clouds</span></span>

<span data-ttu-id="f74b4-141">Agora tivemos uma solução de backup que produzia uma representação razoável de nossos dados em nuvem, mas era um pouco Lackluster no fator "Wow" e não transmitiu a sensação de volumétricos que queríamos para nossos computadores de alto nível.</span><span class="sxs-lookup"><span data-stu-id="f74b4-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="f74b4-142">Nossa próxima etapa foi criar as nuvens, representando-as com aproximadamente 100.000 partículas para produzir uma aparência mais orgânica e volumétricos.</span><span class="sxs-lookup"><span data-stu-id="f74b4-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="f74b4-143">Se as partículas permanecerem sólidas e classificarem de volta para trás, ainda podemos nos beneficiar com a remoção do buffer de profundidade dos pixels por trás das partículas renderizadas anteriormente, reduzindo o sobreempate.</span><span class="sxs-lookup"><span data-stu-id="f74b4-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="f74b4-144">Além disso, com uma solução baseada em partículas, podemos alterar a quantidade de partículas usadas para direcionar diferentes hardwares.</span><span class="sxs-lookup"><span data-stu-id="f74b4-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="f74b4-145">No entanto, todos os pixels ainda precisam ser testados com profundidade, o que resulta em alguma sobrecarga adicional.</span><span class="sxs-lookup"><span data-stu-id="f74b4-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="f74b4-146">Primeiro, criamos posições de partícula em todo o ponto central da experiência na inicialização.</span><span class="sxs-lookup"><span data-stu-id="f74b4-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="f74b4-147">Distribuímos as partículas mais densas em todo o centro e menos para a distância.</span><span class="sxs-lookup"><span data-stu-id="f74b4-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="f74b4-148">Nós classificamos previamente todas as partículas do centro para trás para que as partículas mais próximas sejam renderizadas primeiro.</span><span class="sxs-lookup"><span data-stu-id="f74b4-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="f74b4-149">Um sombreador de computação deve obter uma amostra da textura de informações de nuvem para posicionar cada partícula em uma altura correta e Colorá-la com base na densidade.</span><span class="sxs-lookup"><span data-stu-id="f74b4-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="f74b4-150">Usamos *DrawProcedural* para renderizar um quad por partícula, permitindo que os dados de partícula permaneçam sempre na GPU.</span><span class="sxs-lookup"><span data-stu-id="f74b4-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="f74b4-151">Cada partícula continha uma altura e um raio.</span><span class="sxs-lookup"><span data-stu-id="f74b4-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="f74b4-152">A altura foi baseada nos dados de nuvem amostrados da textura de informações de nuvem, e o raio era baseado na distribuição inicial em que seria calculado para armazenar a distância horizontal para o vizinho mais próximo.</span><span class="sxs-lookup"><span data-stu-id="f74b4-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="f74b4-153">Os quatro processadores usariam esses dados para se orientarem em ângulo pela altura, de modo que, quando os usuários olharem isso horizontalmente, a altura seja mostrada e, quando os usuários olhassem de cima para baixo, a área entre seus vizinhos seria coberta.</span><span class="sxs-lookup"><span data-stu-id="f74b4-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Forma de partícula](images/particle-shape-700px.png)

<span data-ttu-id="f74b4-155">**Código do sombreador mostrando a distribuição:**</span><span class="sxs-lookup"><span data-stu-id="f74b4-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="f74b4-156">Como classificamos as partículas front-to-back e ainda usamos um sombreador de estilo sólido para recortar (não misturar) pixels transparentes, essa técnica trata de uma quantidade surpreendente de partículas, evitando um dispendioso excesso de empates mesmo nos computadores com menor capacidade.</span><span class="sxs-lookup"><span data-stu-id="f74b4-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="f74b4-157">Nuvens de partículas transparentes</span><span class="sxs-lookup"><span data-stu-id="f74b4-157">Transparent particle clouds</span></span>

<span data-ttu-id="f74b4-158">As partículas sólidas forneciam uma boa sensação orgânica à forma das nuvens, mas ainda precisavam de algo para vender o fluffiness de nuvens.</span><span class="sxs-lookup"><span data-stu-id="f74b4-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="f74b4-159">Decidimos tentar uma solução personalizada para as placas gráficas de alto nível em que podemos introduzir transparência.</span><span class="sxs-lookup"><span data-stu-id="f74b4-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="f74b4-160">Para fazer isso, simplesmente alternamos a ordem de classificação inicial das partículas e alteramos o sombreador para usar as texturas alfa.</span><span class="sxs-lookup"><span data-stu-id="f74b4-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Nuvens Fluffys](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="f74b4-162">Parece ótimo, mas provou ser muito pesado para até mesmo as máquinas mais difíceis, pois isso resultaria na renderização de cada pixel na tela centenas de vezes!</span><span class="sxs-lookup"><span data-stu-id="f74b4-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="f74b4-163">Renderizar fora da tela com resolução mais baixa</span><span class="sxs-lookup"><span data-stu-id="f74b4-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="f74b4-164">Para reduzir o número de pixels processados pelas nuvens, começamos a renderizá-los em um buffer de resolução de trimestre (em comparação à tela) e esticar o resultado final de volta para a tela depois que todas as partículas tivessem sido desenhadas.</span><span class="sxs-lookup"><span data-stu-id="f74b4-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="f74b4-165">Isso nos deu aproximadamente um 4x aumento de velocidade, mas vem com algumas advertências.</span><span class="sxs-lookup"><span data-stu-id="f74b4-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="f74b4-166">**Código para renderização fora da tela:**</span><span class="sxs-lookup"><span data-stu-id="f74b4-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="f74b4-167">Primeiro, ao renderizar em um buffer fora da tela, perdemos todas as informações de profundidade de nossa cena principal, resultando em partículas por trás da renderização de montanhas sobre a montanha.</span><span class="sxs-lookup"><span data-stu-id="f74b4-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="f74b4-168">Em segundo lugar, o alongamento do buffer também introduziu artefatos nas bordas de nossas nuvens em que a alteração da resolução foi perceptível.</span><span class="sxs-lookup"><span data-stu-id="f74b4-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="f74b4-169">As próximas duas seções falam sobre como resolvemos esses problemas.</span><span class="sxs-lookup"><span data-stu-id="f74b4-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="f74b4-170">Buffer de profundidade de partícula</span><span class="sxs-lookup"><span data-stu-id="f74b4-170">Particle depth buffer</span></span>

<span data-ttu-id="f74b4-171">Para fazer com que as partículas coexistam com a geometria mundial em que uma montanha ou um objeto possa cobrir partículas por trás dela, populamos o buffer fora da tela com um buffer de profundidade que contém a geometria da cena principal.</span><span class="sxs-lookup"><span data-stu-id="f74b4-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="f74b4-172">Para produzir esse buffer de profundidade, criamos uma segunda câmera, Renderizando apenas a geometria sólida e a profundidade da cena.</span><span class="sxs-lookup"><span data-stu-id="f74b4-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="f74b4-173">Em seguida, usamos a nova textura no sombreador de pixel das nuvens para occlude pixels.</span><span class="sxs-lookup"><span data-stu-id="f74b4-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="f74b4-174">Usamos a mesma textura para calcular a distância para a geometria por trás de um pixel de nuvem.</span><span class="sxs-lookup"><span data-stu-id="f74b4-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="f74b4-175">Ao usar essa distância e aplicá-la ao alfa do pixel, agora tínhamos o efeito das nuvens desaparecendo à medida que elas ficam perto do terreno, removendo qualquer recorte fixo onde as partículas e o terreno se encontram.</span><span class="sxs-lookup"><span data-stu-id="f74b4-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Nuvens mescladas no terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="f74b4-177">Ajustando as bordas</span><span class="sxs-lookup"><span data-stu-id="f74b4-177">Sharpening the edges</span></span>

<span data-ttu-id="f74b4-178">As nuvens ampliadas se parecevam quase idênticas às nuvens de tamanho normal no centro das partículas ou nas quais elas se sobrepostam, mas mostraram alguns artefatos nas bordas da nuvem.</span><span class="sxs-lookup"><span data-stu-id="f74b4-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="f74b4-179">Caso contrário, as bordas nítidas aparecerão borradas e os efeitos de alias foram introduzidos quando a câmera fosse movida.</span><span class="sxs-lookup"><span data-stu-id="f74b4-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="f74b4-180">Resolvemos isso executando um sombreador simples no buffer fora da tela para determinar onde ocorreram grandes alterações (1).</span><span class="sxs-lookup"><span data-stu-id="f74b4-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="f74b4-181">Colocamos os pixels com grandes alterações em um novo buffer de estêncil (2).</span><span class="sxs-lookup"><span data-stu-id="f74b4-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="f74b4-182">Em seguida, usamos o buffer de estêncil para mascarar essas áreas de alto contraste ao aplicar o buffer fora da tela de volta à tela, resultando em buracos em e em todas as nuvens (3).</span><span class="sxs-lookup"><span data-stu-id="f74b4-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="f74b4-183">Em seguida, renderizamos todas as partículas novamente no modo de tela inteira, mas desta vez usamos o buffer de estêncil para mascarar tudo, exceto as bordas, resultando em um conjunto mínimo de pixels tocadas (4).</span><span class="sxs-lookup"><span data-stu-id="f74b4-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="f74b4-184">Como o buffer de comando já foi criado para as partículas, simplesmente tivemos que renderizá-lo novamente na nova câmera.</span><span class="sxs-lookup"><span data-stu-id="f74b4-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Progressão do processamento de bordas de nuvem](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="f74b4-186">O resultado final foi bordas nítidas com seções do centro barato das nuvens.</span><span class="sxs-lookup"><span data-stu-id="f74b4-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="f74b4-187">Embora isso fosse muito mais rápido do que renderizar todas as partículas em tela inteira, ainda há um custo associado ao teste de um pixel em relação ao buffer do estêncil, de modo que uma grande quantidade de sobreempates ainda veio com um custo.</span><span class="sxs-lookup"><span data-stu-id="f74b4-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="f74b4-188">Remoção de partículas</span><span class="sxs-lookup"><span data-stu-id="f74b4-188">Culling particles</span></span>

<span data-ttu-id="f74b4-189">Para nosso efeito de vento, geramos extensões de triângulo longos em um sombreador de computação, criando muitos WISPs de vento no mundo.</span><span class="sxs-lookup"><span data-stu-id="f74b4-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="f74b4-190">Embora o efeito de vento não tenha sido pesado na taxa de preenchimento devido a faixas skinnis geradas, ele produziu muitas centenas de milhares de vértices, resultando em uma carga pesada para o sombreador de vértice.</span><span class="sxs-lookup"><span data-stu-id="f74b4-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="f74b4-191">Introduzimos buffers de acréscimo no sombreador de computação para alimentar um subconjunto das faixas de vento a serem desenhadas.</span><span class="sxs-lookup"><span data-stu-id="f74b4-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="f74b4-192">Com alguns frustum de exibição simples de seleção de lógica no sombreador de computação, poderíamos determinar se uma tira estava fora do modo de exibição de câmera e impedir que ela fosse adicionada ao buffer de envio por push.</span><span class="sxs-lookup"><span data-stu-id="f74b4-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="f74b4-193">Isso reduziu significativamente a quantidade de faixas, liberando alguns ciclos necessários na GPU.</span><span class="sxs-lookup"><span data-stu-id="f74b4-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="f74b4-194">**Código que demonstra um buffer de acréscimo:**</span><span class="sxs-lookup"><span data-stu-id="f74b4-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="f74b4-195">*Sombreador de computação:*</span><span class="sxs-lookup"><span data-stu-id="f74b4-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="f74b4-196">*C#auto-completar*</span><span class="sxs-lookup"><span data-stu-id="f74b4-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="f74b4-197">Tentamos usar a mesma técnica nas partículas de nuvem, em que poderíamos alterá-las no sombreador de computação e apenas enviar por push as partículas visíveis a serem renderizadas.</span><span class="sxs-lookup"><span data-stu-id="f74b4-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="f74b4-198">Na verdade, essa técnica não nos salvou muito na GPU, uma vez que o maior afunilamento era a quantidade de pixels renderizados na tela, e não o custo de calcular os vértices.</span><span class="sxs-lookup"><span data-stu-id="f74b4-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="f74b4-199">O outro problema dessa técnica era que o buffer de acréscimo foi populado em ordem aleatória devido à sua natureza paralelizada de computação das partículas, fazendo com que as partículas classificadas não sejam classificadas, resultando na cintilação de partículas de nuvem.</span><span class="sxs-lookup"><span data-stu-id="f74b4-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="f74b4-200">Há técnicas para classificar o buffer de push, mas a quantidade limitada de acertos de desempenho que acabamos de escolher partículas provavelmente seria compensada com uma classificação adicional, portanto, decidimos não buscar essa otimização.</span><span class="sxs-lookup"><span data-stu-id="f74b4-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="f74b4-201">Renderização adaptável</span><span class="sxs-lookup"><span data-stu-id="f74b4-201">Adaptive rendering</span></span>

<span data-ttu-id="f74b4-202">Para garantir uma taxa de quadros constante em um aplicativo com condições de renderização diferentes, como uma nuvem versus uma exibição clara, introduzimos a renderização adaptável em nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f74b4-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="f74b4-203">A primeira etapa da renderização adaptável é medir a GPU.</span><span class="sxs-lookup"><span data-stu-id="f74b4-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="f74b4-204">Fizemos isso inserindo código personalizado no buffer de comando da GPU no início e no final de um quadro renderizado, capturando o horário da tela de olho à esquerda e à direita.</span><span class="sxs-lookup"><span data-stu-id="f74b4-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="f74b4-205">Medindo o tempo gasto renderizando e comparando-o à nossa taxa de atualização desejada, temos uma noção de como devemos descartar os quadros.</span><span class="sxs-lookup"><span data-stu-id="f74b4-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="f74b4-206">Ao fechar os quadros, adaptamos nossa renderização para torná-lo mais rápido.</span><span class="sxs-lookup"><span data-stu-id="f74b4-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="f74b4-207">Uma maneira simples de adaptar-se é alterar o tamanho do visor da tela, exigindo menos pixels para ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="f74b4-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="f74b4-208">Usando *UnityEngine. XR. XRSettings. renderViewportScale* , o sistema reduz o visor de destino e alonga automaticamente o resultado de volta para o ajuste à tela.</span><span class="sxs-lookup"><span data-stu-id="f74b4-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="f74b4-209">Uma pequena alteração na escala é mal perceptível na geometria mundial, e um fator de escala de 0,7 requer metade da quantidade de pixels a serem renderizados.</span><span class="sxs-lookup"><span data-stu-id="f74b4-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% de escala, metade dos pixels](images/datascape-scaling-700px.jpg)

<span data-ttu-id="f74b4-211">Quando detectamos que estamos prestes a descartar os quadros, reduzimos a escala por um número fixo e o aumentamos quando estamos executando rápido o suficiente novamente.</span><span class="sxs-lookup"><span data-stu-id="f74b4-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="f74b4-212">Embora decidimos qual técnica de nuvem usar com base nos recursos gráficos do hardware na inicialização, é possível baseá-la nos dados da medição da GPU para impedir que o sistema permaneça em baixa resolução por um longo tempo, mas isso é algo que não temos tempo  para explorar em Datascape.</span><span class="sxs-lookup"><span data-stu-id="f74b4-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="f74b4-213">Pensamentos finais</span><span class="sxs-lookup"><span data-stu-id="f74b4-213">Final thoughts</span></span>

<span data-ttu-id="f74b4-214">O direcionamento a uma variedade de hardware é desafiador e requer algum planejamento.</span><span class="sxs-lookup"><span data-stu-id="f74b4-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="f74b4-215">Recomendamos que você comece a direcionar computadores com menor capacidade para se familiarizar com o espaço do problema e desenvolver uma solução de backup que será executada em todos os seus computadores.</span><span class="sxs-lookup"><span data-stu-id="f74b4-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="f74b4-216">Projete sua solução com a taxa de preenchimento em mente, pois os pixels serão seus recursos mais preciosos.</span><span class="sxs-lookup"><span data-stu-id="f74b4-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="f74b4-217">Direcionar a geometria sólida sobre transparência.</span><span class="sxs-lookup"><span data-stu-id="f74b4-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="f74b4-218">Com uma solução de backup, você pode iniciar a disposição em camadas em mais complexidade para máquinas de alto nível ou talvez apenas aprimorar a resolução da solução de backup.</span><span class="sxs-lookup"><span data-stu-id="f74b4-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="f74b4-219">Design para cenários de pior caso e talvez considere o uso de processamento adaptável para situações pesadas.</span><span class="sxs-lookup"><span data-stu-id="f74b4-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="f74b4-220">Sobre os autores</span><span class="sxs-lookup"><span data-stu-id="f74b4-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="f74b4-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="f74b4-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="f74b4-222">Engenheiro de software @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f74b4-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="f74b4-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="f74b4-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="f74b4-224">Engenheiro de software @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f74b4-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="f74b4-225">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f74b4-225">See also</span></span>
* [<span data-ttu-id="f74b4-226">Entendendo o desempenho da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f74b4-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="f74b4-227">Recomendações de desempenho para o Unity</span><span class="sxs-lookup"><span data-stu-id="f74b4-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 

---
title: Estudo de caso - dimensionamento Datascape em todos os dispositivos com diferentes de desempenho
description: Este estudo de caso oferece informações sobre como o aplicativo de Datascape para fornecer uma experiência atraente em vários dispositivos com uma variedade de recursos de desempenho com otimização de desenvolvedores da Microsoft.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: headset imersivo, estudo de caso de otimização, VR, desempenho
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590974"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="259c7-104">Estudo de caso - dimensionamento Datascape em todos os dispositivos com diferentes de desempenho</span><span class="sxs-lookup"><span data-stu-id="259c7-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="259c7-105">Datascape é um aplicativo de realidade mista do Windows desenvolvido internamente na Microsoft em que nos concentramos sobre como exibir dados meteorológicos sobre os dados de terreno.</span><span class="sxs-lookup"><span data-stu-id="259c7-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="259c7-106">O aplicativo explora as percepções exclusivas que os usuários obtêm da descoberta de dados na realidade mista, envolvendo o usuário com a visualização de dados holographic.</span><span class="sxs-lookup"><span data-stu-id="259c7-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="259c7-107">Para Datascape queríamos uma variedade de plataformas de destino com recursos de hardware diferentes que variam do Microsoft HoloLens para fones imersivos em exposição Windows Mixed Reality e de PCs baseados em inferior para os PCs mais recentes com GPU high-end.</span><span class="sxs-lookup"><span data-stu-id="259c7-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="259c7-108">O principal desafio era renderizando nossa cena em questão visualmente atraente em dispositivos com recursos gráficos totalmente diferente durante a execução de uma alta taxa de quadros.</span><span class="sxs-lookup"><span data-stu-id="259c7-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="259c7-109">Este estudo de caso percorrerá o processo e as técnicas usadas para criar alguns dos nossos mais sistemas de uso intenso da GPU, que descrevem os problemas encontrados e como podemos superou.</span><span class="sxs-lookup"><span data-stu-id="259c7-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="259c7-110">Transparência e excedente</span><span class="sxs-lookup"><span data-stu-id="259c7-110">Transparency and overdraw</span></span>

<span data-ttu-id="259c7-111">Nosso lutas renderização principal lidam com transparência, como transparência pode ser cara em uma GPU.</span><span class="sxs-lookup"><span data-stu-id="259c7-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="259c7-112">Geometria sólida pode ser renderizada de frente para trás ao gravar no buffer de profundidade, interrompendo os pixels futuras localizados por trás desse pixel de ser descartado.</span><span class="sxs-lookup"><span data-stu-id="259c7-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="259c7-113">Isso impede que oculta pixels executando o sombreador de pixel, acelerando o processo consideravelmente.</span><span class="sxs-lookup"><span data-stu-id="259c7-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="259c7-114">Se a geometria é classificada de maneira ideal, cada pixel na tela será desenhada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="259c7-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="259c7-115">Necessidades de geometria transparente a ser classificada de volta para a frente e se baseia em mistura a saída do sombreador de pixel para o pixel atual na tela.</span><span class="sxs-lookup"><span data-stu-id="259c7-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="259c7-116">Isso pode resultar em cada pixel na tela que está sendo desenhada para várias vezes por quadro, conhecido como excedente.</span><span class="sxs-lookup"><span data-stu-id="259c7-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="259c7-117">Para o HoloLens e PCs predominantes, a tela só pode ser preenchida inúmeras vezes, tornando transparente de um problema de renderização.</span><span class="sxs-lookup"><span data-stu-id="259c7-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="259c7-118">Introdução aos componentes de cena Datascape</span><span class="sxs-lookup"><span data-stu-id="259c7-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="259c7-119">Tivemos três componentes principais de nossa cena; **a interface do usuário, o mapa**, e **o clima**.</span><span class="sxs-lookup"><span data-stu-id="259c7-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="259c7-120">Sabíamos desde o início que nosso efeitos de clima exigiria GPU sempre foi possível obter, portanto, propositadamente projetamos a interface do usuário e o terreno, de forma que reduziria qualquer excedentes.</span><span class="sxs-lookup"><span data-stu-id="259c7-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="259c7-121">Retrabalhamos a interface do usuário várias vezes para minimizar a quantidade de excedente produziria.</span><span class="sxs-lookup"><span data-stu-id="259c7-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="259c7-122">Erramos na lateral da geometria mais complexa em vez de arte transparente sobreposição sobre o outro para componentes como brilhantes visões gerais de botões e o mapa.</span><span class="sxs-lookup"><span data-stu-id="259c7-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="259c7-123">Para o mapa, usamos um sombreador personalizado que seria retirar os recursos padrão do Unity como sombras e iluminação complexa, substituí-los com um modelo de iluminação simples sun único e um cálculo personalizado neblina.</span><span class="sxs-lookup"><span data-stu-id="259c7-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="259c7-124">Isso produziu um sombreador de pixel simples e liberar ciclos GPU.</span><span class="sxs-lookup"><span data-stu-id="259c7-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="259c7-125">Nós conseguimos obter a interface do usuário e o mapa para renderização no orçamento onde não é necessário todas as alterações a eles dependendo do hardware; No entanto, a visualização de previsão do tempo, em particular a renderização de nuvem, provou para ser um desafio!</span><span class="sxs-lookup"><span data-stu-id="259c7-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="259c7-126">Em segundo plano nos dados de nuvem</span><span class="sxs-lookup"><span data-stu-id="259c7-126">Background on cloud data</span></span>

<span data-ttu-id="259c7-127">Nossos dados de nuvem tiver sido baixados de servidores da NOAA (http://nomads.ncep.noaa.gov/) e veio para nós em três camadas distintas de 2D, cada um com a altura da parte superior e inferior da nuvem, bem como a densidade da nuvem para cada célula da grade.</span><span class="sxs-lookup"><span data-stu-id="259c7-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="259c7-128">Os dados obteve processados em uma textura de informações da nuvem em que cada componente foi armazenado no componente vermelho, verde e azul da textura para facilitar o acesso na GPU.</span><span class="sxs-lookup"><span data-stu-id="259c7-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="259c7-129">Nuvens de geometria</span><span class="sxs-lookup"><span data-stu-id="259c7-129">Geometry clouds</span></span>

<span data-ttu-id="259c7-130">Para garantir que nossos computadores baseados em inferior possa renderizar nossas nuvens, decidimos que começar com uma abordagem que usaria a geometria sólida para minimizar o excedente.</span><span class="sxs-lookup"><span data-stu-id="259c7-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="259c7-131">Primeiro, tentamos produzindo nuvens por meio da geração de uma malha de heightmap sólida para cada camada usando o raio da textura de informações de nuvem por vértice para gerar a forma.</span><span class="sxs-lookup"><span data-stu-id="259c7-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="259c7-132">Usamos um sombreador de geometria para produzir os vértices na parte superior e a parte inferior da nuvem gera formas de nuvem sólida.</span><span class="sxs-lookup"><span data-stu-id="259c7-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="259c7-133">Usamos o valor de densidade de textura para a nuvem de cores com cores mais escuras para mais densas nuvens.</span><span class="sxs-lookup"><span data-stu-id="259c7-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="259c7-134">**Sombreador para criar vértices:**</span><span class="sxs-lookup"><span data-stu-id="259c7-134">**Shader for creating the vertices:**</span></span>

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

<span data-ttu-id="259c7-135">Apresentamos um padrão de ruído pequeno para obter mais detalhes sobre os dados reais.</span><span class="sxs-lookup"><span data-stu-id="259c7-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="259c7-136">Para produzir bordas de nuvem redonda, podemos recortada os pixels no sombreador de pixel quando o valor de raio interpolada atinge um limite para descartar os valores de quase zero.</span><span class="sxs-lookup"><span data-stu-id="259c7-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Nuvens de geometria](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="259c7-138">Como as nuvens são geometria sólida, eles podem ser processados antes do terreno para ocultar qualquer pixels mapa caro abaixo para melhorar ainda mais a taxa de quadros.</span><span class="sxs-lookup"><span data-stu-id="259c7-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="259c7-139">Essa solução foi executado bem em todas as placas gráficas da especificação de min placas gráficas high-end, bem como em HoloLens, devido à abordagem de processamento a geometria sólida.</span><span class="sxs-lookup"><span data-stu-id="259c7-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="259c7-140">Nuvens de partícula sólida</span><span class="sxs-lookup"><span data-stu-id="259c7-140">Solid particle clouds</span></span>

<span data-ttu-id="259c7-141">Agora tínhamos uma solução de backup que produziu uma representação decente de nossos dados de nuvem, mas foi um pouco lackluster no fator de "wow" e não transmitem a sensação volumétricas que queríamos para nosso máquinas high-end.</span><span class="sxs-lookup"><span data-stu-id="259c7-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="259c7-142">Nossa próxima etapa foi criando as nuvens, que representa-los com aproximadamente 100.000 partículas para produzir uma aparência mais orgânica e volumétricas.</span><span class="sxs-lookup"><span data-stu-id="259c7-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="259c7-143">Se partículas permanecem estável e classificar de frente para trás, podemos ainda podem se beneficiar do buffer de profundidade traseira dos pixels por trás de partículas anteriormente renderizadas, reduzindo a excedentes.</span><span class="sxs-lookup"><span data-stu-id="259c7-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="259c7-144">Além disso, com uma solução baseada em partículas, podemos alterar a quantidade de partículas usado para hardware de destino diferente.</span><span class="sxs-lookup"><span data-stu-id="259c7-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="259c7-145">No entanto, todos os pixels ainda precisam ser testado em profundidade, que resulta em alguma sobrecarga adicional.</span><span class="sxs-lookup"><span data-stu-id="259c7-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="259c7-146">Primeiro, criamos posições de partícula em torno do ponto central da experiência na inicialização.</span><span class="sxs-lookup"><span data-stu-id="259c7-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="259c7-147">Podemos distribuído as partículas mais densamente em torno do centro e, portanto, menos na distância.</span><span class="sxs-lookup"><span data-stu-id="259c7-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="259c7-148">Podemos previamente classificados todas as partículas no centro para trás de modo que as partículas mais próximas renderização pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="259c7-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="259c7-149">A textura de informações da nuvem para posicionar cada partícula em uma altura correta e a cor de acordo com a densidade de exemplo seria um sombreador de cálculo.</span><span class="sxs-lookup"><span data-stu-id="259c7-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="259c7-150">Usamos *DrawProcedural* renderizar um quad por partículas, permitindo que os dados de partícula permanecer na GPU em todos os tempos.</span><span class="sxs-lookup"><span data-stu-id="259c7-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="259c7-151">Cada partícula continha uma altura e um raio.</span><span class="sxs-lookup"><span data-stu-id="259c7-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="259c7-152">A altura foi com base nos dados de nuvem exemplificados a textura de informações de nuvem e o raio foi com base na distribuição inicial onde ele será calculado para armazenar a distância horizontal para seu vizinho mais próximo.</span><span class="sxs-lookup"><span data-stu-id="259c7-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="259c7-153">Os quadrados usaria esses dados para orientar o próprio angular pela altura para que quando os usuários examiná-la horizontalmente, a altura seria mostrada e quando os usuários olhar de cima para baixo, a área entre seus vizinhos seria abordada.</span><span class="sxs-lookup"><span data-stu-id="259c7-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Forma de partícula](images/particle-shape-700px.png)

<span data-ttu-id="259c7-155">**Código do sombreador mostrando a distribuição:**</span><span class="sxs-lookup"><span data-stu-id="259c7-155">**Shader code showing the distribution:**</span></span>

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

<span data-ttu-id="259c7-156">Como podemos classificar a partículas frente para trás e ainda, usamos um sombreador de estilo sólido para pixels transparentes do clipe (não blend), essa técnica trata uma quantidade surpreendente de partículas, evitando a dispendioso desenho em excesso, mesmo em computadores baseados em inferior.</span><span class="sxs-lookup"><span data-stu-id="259c7-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="259c7-157">Nuvens de partícula transparente</span><span class="sxs-lookup"><span data-stu-id="259c7-157">Transparent particle clouds</span></span>

<span data-ttu-id="259c7-158">As partículas sólidas fornecido uma boa ideia orgânica na forma de nuvens, mas ainda precisava algo para vender o fluffiness de nuvens.</span><span class="sxs-lookup"><span data-stu-id="259c7-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="259c7-159">Decidimos tentar uma solução personalizada para os cartões de gráficos avançados, onde podemos apresentar transparência.</span><span class="sxs-lookup"><span data-stu-id="259c7-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="259c7-160">Para fazer isso simplesmente alternado a ordem de classificação inicial das partículas e alterou o sombreador para usar o alfa de texturas.</span><span class="sxs-lookup"><span data-stu-id="259c7-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![A Fluffy nuvens](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="259c7-162">Pareciam ótimo, mas provou para ser muito pesada para até mesmo as máquinas mais difíceis, pois resultaria no processamento de cada pixel na tela de centenas de vezes!</span><span class="sxs-lookup"><span data-stu-id="259c7-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="259c7-163">Processar fora da tela com resolução mais baixa</span><span class="sxs-lookup"><span data-stu-id="259c7-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="259c7-164">Para reduzir o número de pixels renderizados por nuvens, começamos a renderização-los no buffer de resolução de um trimestre (em comparação comparada a tela) e ampliar o resultado final faça backup para a tela depois que todas as partículas tivessem sido desenhadas.</span><span class="sxs-lookup"><span data-stu-id="259c7-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="259c7-165">Isso nos deu aproximadamente um aumento de velocidade 4 x, mas veio com algumas limitações.</span><span class="sxs-lookup"><span data-stu-id="259c7-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="259c7-166">**Código para a renderização de fora da tela:**</span><span class="sxs-lookup"><span data-stu-id="259c7-166">**Code for rendering off-screen:**</span></span>

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

<span data-ttu-id="259c7-167">Primeiro, ao renderizar em um buffer fora da tela, perdemos todas as informações de profundidade da cena nosso principal, resultando em partículas por trás de montanhas renderização na parte superior a montanha.</span><span class="sxs-lookup"><span data-stu-id="259c7-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="259c7-168">Em segundo lugar, alongando o buffer também introduziu artefatos nas bordas do nosso nuvens em que a alteração de resolução foi perceptível.</span><span class="sxs-lookup"><span data-stu-id="259c7-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="259c7-169">As duas próximas seções falam sobre como resolvemos esses problemas.</span><span class="sxs-lookup"><span data-stu-id="259c7-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="259c7-170">Buffer de profundidade de partícula</span><span class="sxs-lookup"><span data-stu-id="259c7-170">Particle depth buffer</span></span>

<span data-ttu-id="259c7-171">Para tornar as partículas coexiste com a geometria do mundo em que um objeto ou mountain poderia englobar partículas por trás dele, preenchemos o buffer fora da tela com um buffer de profundidade que contém a geometria da cena principal.</span><span class="sxs-lookup"><span data-stu-id="259c7-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="259c7-172">Para produzir esse buffer de profundidade, criamos uma segunda câmera, renderizar apenas a geometria sólida e a profundidade da cena.</span><span class="sxs-lookup"><span data-stu-id="259c7-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="259c7-173">Em seguida, usamos a nova textura no sombreador de pixel das nuvens para occlude pixels.</span><span class="sxs-lookup"><span data-stu-id="259c7-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="259c7-174">Nós usamos a mesma textura para calcular a distância à geometria por trás de um pixel de nuvem.</span><span class="sxs-lookup"><span data-stu-id="259c7-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="259c7-175">Usando essa distância e aplicá-lo para o alfa do pixel, podemos agora tinha o efeito de nuvens desaparecimento conforme eles chegarem perto o terreno, removendo qualquer cortes onde se encontram partículas e terreno.</span><span class="sxs-lookup"><span data-stu-id="259c7-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Nuvens em um terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="259c7-177">Nitidez bordas</span><span class="sxs-lookup"><span data-stu-id="259c7-177">Sharpening the edges</span></span>

<span data-ttu-id="259c7-178">As nuvens alongados para cima tinha quase idênticas para as nuvens de tamanho normal no centro das partículas ou onde eles sobrepostas, mas mostraram alguns artefatos nas bordas de nuvem.</span><span class="sxs-lookup"><span data-stu-id="259c7-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="259c7-179">Caso contrário, bordas nítidas apareceria desfocadas e efeitos de alias foram introduzidos quando movido a câmera.</span><span class="sxs-lookup"><span data-stu-id="259c7-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="259c7-180">Solucionamos essa questão, executando um sombreador simple no buffer de fora da tela para determinar em que grandes alterações ocorreram por outro lado (1).</span><span class="sxs-lookup"><span data-stu-id="259c7-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="259c7-181">Colocamos os pixels com grandes alterações em um novo buffer de estêncil (2).</span><span class="sxs-lookup"><span data-stu-id="259c7-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="259c7-182">Em seguida, usamos o buffer de estêncil máscara essas áreas de alto contraste ao aplicar o buffer fora da tela na tela, resultando em falhas em e relacionado as nuvens (3).</span><span class="sxs-lookup"><span data-stu-id="259c7-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="259c7-183">Podemos então processado todas as partículas novamente no modo de tela inteira, mas este tempo usado para mascarar tudo o que o buffer de estêncil, mas as bordas, resultando em um conjunto mínimo de pixels tocadas (4).</span><span class="sxs-lookup"><span data-stu-id="259c7-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="259c7-184">Uma vez que o buffer de comando já foi criado para as partículas, simplesmente tivemos para renderizá-lo novamente para a nova câmera.</span><span class="sxs-lookup"><span data-stu-id="259c7-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Progressão de renderização de bordas de nuvem](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="259c7-186">O resultado final era bordas nítidas com seções barato center das nuvens.</span><span class="sxs-lookup"><span data-stu-id="259c7-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="259c7-187">Embora isso era muito mais rápido que a renderização de tela cheia de todas as partículas de, há ainda um custo associado com o teste de um pixel no buffer de estêncil, portanto, uma grande quantidade de excedente ainda veio com um custo.</span><span class="sxs-lookup"><span data-stu-id="259c7-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="259c7-188">Remoção de partículas</span><span class="sxs-lookup"><span data-stu-id="259c7-188">Culling particles</span></span>

<span data-ttu-id="259c7-189">Para nosso efeito de vento, geramos faixas de triângulo longa em um sombreador de cálculo, a criação de muitos wisps de vento no mundo.</span><span class="sxs-lookup"><span data-stu-id="259c7-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="259c7-190">Enquanto o efeito de vento não estava pesado na taxa de preenchimento devido a faixas magro gerado, ele produziu várias centenas de milhares de vértices, resultando em uma carga pesada para o sombreador de vértices.</span><span class="sxs-lookup"><span data-stu-id="259c7-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="259c7-191">Introduzimos o acréscimo de buffers no sombreador de cálculo para alimentar um subconjunto das faixas vento a ser desenhado.</span><span class="sxs-lookup"><span data-stu-id="259c7-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="259c7-192">Com alguma exibição simples frustum escolhidos lógica no sombreador de cálculo, poderíamos determinar se uma faixa estava fora do modo de exibição da câmera e impedi-lo de que está sendo adicionada ao buffer de envio por push.</span><span class="sxs-lookup"><span data-stu-id="259c7-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="259c7-193">Isso reduziu a quantidade de faixas significativamente, liberando alguns ciclos necessários na GPU.</span><span class="sxs-lookup"><span data-stu-id="259c7-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="259c7-194">**Código que demonstra um buffer de acréscimo:**</span><span class="sxs-lookup"><span data-stu-id="259c7-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="259c7-195">*Sombreador de cálculo:*</span><span class="sxs-lookup"><span data-stu-id="259c7-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="259c7-196">*C#código:*</span><span class="sxs-lookup"><span data-stu-id="259c7-196">*C# code:*</span></span>

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

<span data-ttu-id="259c7-197">Tentamos usando a mesma técnica sobre as partículas de nuvem, onde podemos seria analisá-los sobre o sombreador de cálculo e apenas enviar por push as partículas visíveis a ser renderizado.</span><span class="sxs-lookup"><span data-stu-id="259c7-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="259c7-198">Essa técnica, na verdade, não salvou nos muito na GPU, já que o maior afunilamento foi os pixels de quantidade renderizados na tela e não o custo de calcular os vértices.</span><span class="sxs-lookup"><span data-stu-id="259c7-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="259c7-199">O outro problema com essa técnica foi que o buffer de acréscimo é populado em ordem aleatória devido à sua natureza em paralelo de partículas, fazendo com que as partículas classificadas seja não classificada, resultando em cintilantes partículas de nuvem de computação.</span><span class="sxs-lookup"><span data-stu-id="259c7-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="259c7-200">Há técnicas para classificar o buffer de envio por push, mas a quantidade limitada de ganho de desempenho, temos fora traseira partículas provavelmente seria deslocamento com uma classificação adicional, portanto, decidimos não buscar essa otimização.</span><span class="sxs-lookup"><span data-stu-id="259c7-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="259c7-201">Renderização adaptável</span><span class="sxs-lookup"><span data-stu-id="259c7-201">Adaptive rendering</span></span>

<span data-ttu-id="259c7-202">Para garantir uma taxa de quadros estável em um aplicativo com diferentes condições, como um nublado vs de renderização uma visão clara, introduzimos renderização adaptável ao nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="259c7-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="259c7-203">A primeira etapa de renderização adaptável é medir a GPU.</span><span class="sxs-lookup"><span data-stu-id="259c7-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="259c7-204">Fizemos isso inserindo o código personalizado no buffer de comandos GPU no início e no final de um quadro renderizado, capturando ambos esquerda e direita olho tempo da tela.</span><span class="sxs-lookup"><span data-stu-id="259c7-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="259c7-205">Medindo o tempo gasto de renderização e compará-lo a nossa desejado-taxa de atualização, temos uma ideia de quão próximo precisássemos descarte de quadros.</span><span class="sxs-lookup"><span data-stu-id="259c7-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="259c7-206">Quando perto de descarte de quadros, podemos adaptar nosso processamento para torná-lo mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="259c7-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="259c7-207">Uma maneira simples de se adaptar está mudando o tamanho do visor da tela, exigindo menos pixels a serem renderizado.</span><span class="sxs-lookup"><span data-stu-id="259c7-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="259c7-208">Usando *UnityEngine.XR.XRSettings.renderViewportScale* o sistema reduz o visor do destino e estende-se automaticamente o resultado para a tela de ajuste.</span><span class="sxs-lookup"><span data-stu-id="259c7-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="259c7-209">Uma pequena alteração no dimensionamento é quase imperceptível no geometria mundial, e um fator de escala de 0,7 requer metade da quantidade de pixels a serem renderizados.</span><span class="sxs-lookup"><span data-stu-id="259c7-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![escala de 70%, metade dos pixels](images/datascape-scaling-700px.jpg)

<span data-ttu-id="259c7-211">Quando Detectamos que estamos prestes a descartar quadros, podemos reduzir a escala por um número fixo e aumentar-o novamente quando estamos executando novamente rápido o suficiente.</span><span class="sxs-lookup"><span data-stu-id="259c7-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="259c7-212">Embora, decidimos qual técnica de nuvem para usar com base em elementos gráficos, recursos do hardware na inicialização, é possível baseá-la em dados da medida GPU para impedir que o sistema permaneça em baixa resolução por um longo tempo, mas isso é algo que não tínhamos tempo  para explorar o Datascape.</span><span class="sxs-lookup"><span data-stu-id="259c7-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="259c7-213">Considerações finais</span><span class="sxs-lookup"><span data-stu-id="259c7-213">Final thoughts</span></span>

<span data-ttu-id="259c7-214">Direcionamento de uma variedade de hardware é um desafio e exige algum planejamento.</span><span class="sxs-lookup"><span data-stu-id="259c7-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="259c7-215">É recomendável que você comece a direcionar computadores baseados em inferior para se familiarizar com o espaço do problema e desenvolver uma solução de backup que será executado em todos os seus computadores.</span><span class="sxs-lookup"><span data-stu-id="259c7-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="259c7-216">Crie sua solução com taxa de preenchimento em mente, já que pixels será seu recurso mais precioso.</span><span class="sxs-lookup"><span data-stu-id="259c7-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="259c7-217">Geometria sólida de destino de transparência.</span><span class="sxs-lookup"><span data-stu-id="259c7-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="259c7-218">Com uma solução de backup, você pode iniciar, em seguida, disposição em camadas em mais de complexidade para máquinas de high-end ou talvez apenas aprimorar a resolução de sua solução de backup.</span><span class="sxs-lookup"><span data-stu-id="259c7-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="259c7-219">Design para os piores cenários e talvez considere usando renderização adaptável para situações pesadas.</span><span class="sxs-lookup"><span data-stu-id="259c7-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="259c7-220">Sobre os autores</span><span class="sxs-lookup"><span data-stu-id="259c7-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="259c7-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="259c7-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="259c7-222">Engenheiro de software @Microsoft</span><span class="sxs-lookup"><span data-stu-id="259c7-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="259c7-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="259c7-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="259c7-224">Engenheiro de software @Microsoft</span><span class="sxs-lookup"><span data-stu-id="259c7-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="259c7-225">Consulte também</span><span class="sxs-lookup"><span data-stu-id="259c7-225">See also</span></span>
* [<span data-ttu-id="259c7-226">Noções básicas sobre desempenho para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="259c7-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="259c7-227">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="259c7-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 

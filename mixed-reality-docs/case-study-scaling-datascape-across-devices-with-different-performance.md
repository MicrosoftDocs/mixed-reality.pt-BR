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
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Estudo de caso-dimensionamento de Datascape em dispositivos com desempenho diferente

O Datascape é um aplicativo de realidade mista do Windows desenvolvido internamente na Microsoft, no qual nos concentramos na exibição de dados meteorológicos sobre os dados do terreno. O aplicativo explora os usuários de insights exclusivos que aproveitam a descoberta de dados em realidade misturada ao redor do usuário com a visualização de dados do Holographic.

Para o Datascape, queríamos ter como alvo uma variedade de plataformas com diferentes recursos de hardware, desde o Microsoft HoloLens até o Windows Mixed realness headsets e de PCs de baixo consumo até os computadores mais recentes com GPU de ponta. O principal desafio era renderizar nossa cena em uma questão visualmente atraente em dispositivos com recursos gráficos muito diferentes durante a execução em uma taxa de quadros alta.

Esse estudo de caso examinará o processo e as técnicas usadas para criar alguns de nossos sistemas mais intensivos de GPU, descrevendo os problemas encontrados e como superou-los.

## <a name="transparency-and-overdraw"></a>Transparência e sobredesenho

Nosso principal esforço de renderização foi resolvido com transparência, pois a transparência pode ser cara em uma GPU.

A geometria sólida pode ser renderizada de frente para trás durante a gravação no buffer de profundidade, interrompendo os pixels futuros localizados atrás desse pixel de serem descartados. Isso impede que os pixels ocultos executem o sombreador de pixel, acelerando significativamente o processo. Se a geometria for classificada de forma ideal, cada pixel na tela será desenhado apenas uma vez.

A geometria transparente precisa ser classificada de volta para a frente e se baseia na mesclagem da saída do sombreador de pixel com o pixel atual na tela. Isso pode resultar em cada pixel na tela que está sendo desenhada várias vezes por quadro, chamado de sobreempate.

Para os computadores HoloLens e mainstream, a tela só pode ser preenchida algumas vezes, tornando o processo transparente de processamento.

## <a name="introduction-to-datascape-scene-components"></a>Introdução aos componentes de cena do Datascape

Tínhamos três componentes principais para nossa cena; **a interface do usuário, o mapa**e **o clima**. Sabíamos no início que nossos efeitos meteorológicos exigiriam todo o tempo de GPU que poderia obter, então criamos de forma intencional a interface do usuário e o terreno de uma maneira que reduza qualquer sobreempate.

Retrabalhamos a interface do usuário várias vezes para minimizar a quantidade de sobreempates que ela produziria. Nós erramosmos o lado da geometria mais complexa em vez de sobrecarregar arte transparente sobre as outras para componentes como botões brilhantes e visões gerais de mapa.

Para o mapa, usamos um sombreador personalizado que distribuiva recursos padrão do Unity, como sombras e iluminação complexa, substituindo-os por um único modelo simples de iluminação de sol e um cálculo de neblina personalizado. Isso produziu um sombreador de pixel simples e libera ciclos de GPU.

Nós gerenciamos para obter a interface do usuário e o mapa para renderizar no orçamento, onde não precisamos de nenhuma alteração para elas, dependendo do hardware; no entanto, a visualização do clima, em particular, a renderização na nuvem, provou ser mais um desafio!

## <a name="background-on-cloud-data"></a>Plano de fundo em dados de nuvem

Nossos dados de nuvem foram baixados de servidores NOAA (https://nomads.ncep.noaa.gov/) e nos vieram em três camadas 2D distintas, cada uma com a altura superior e inferior da nuvem, bem como a densidade da nuvem para cada célula da grade. Os dados foram processados em uma textura de informações de nuvem, em que cada componente foi armazenado no componente vermelho, verde e azul da textura para facilitar o acesso na GPU.

## <a name="geometry-clouds"></a>Nuvens de geometria

Para garantir que nossos computadores com menor capacidade possam renderizar nossas nuvens, decidimos começar com uma abordagem que usaria uma geometria sólida para minimizar o sobreempate.

Primeiro, tentamos produzir nuvens gerando uma malha heightmap sólida para cada camada usando o raio da textura de informações de nuvem por vértice para gerar a forma. Usamos um sombreador Geometry para produzir os vértices na parte superior e a parte inferior da nuvem gerando formas de nuvem sólidas. Usamos o valor de densidade da textura para colorir a nuvem com cores mais escuras para nuvens mais densas.

**Sombreador para criar os vértices:**

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

Apresentamos um pequeno padrão de ruído para obter mais detalhes sobre os dados reais. Para produzir bordas de nuvem arredondadas, cortamos os pixels no sombreador de pixel quando o valor de raio interpolado atinge um limite para descartar valores quase zero.

![Nuvens de geometria](images/datascape-geometry-clouds-700px.jpg)

Como as nuvens são uma geometria sólida, elas podem ser renderizadas antes que o terreno oculte os pixels de mapa caros abaixo para melhorar ainda mais a taxa de quadros. Essa solução foi executada bem em todas as placas gráficas de min-spec a placas gráficas de ponta, bem como no HoloLens, devido à abordagem de renderização de geometria sólida.

## <a name="solid-particle-clouds"></a>Nuvens de partículas sólidas

Agora tivemos uma solução de backup que produzia uma representação razoável de nossos dados em nuvem, mas era um pouco Lackluster no fator "Wow" e não transmitiu a sensação de volumétricos que queríamos para nossos computadores de alto nível.

Nossa próxima etapa foi criar as nuvens, representando-as com aproximadamente 100.000 partículas para produzir uma aparência mais orgânica e volumétricos.

Se as partículas permanecerem sólidas e classificarem de volta para trás, ainda podemos nos beneficiar com a remoção do buffer de profundidade dos pixels por trás das partículas renderizadas anteriormente, reduzindo o sobreempate. Além disso, com uma solução baseada em partículas, podemos alterar a quantidade de partículas usadas para direcionar diferentes hardwares. No entanto, todos os pixels ainda precisam ser testados com profundidade, o que resulta em alguma sobrecarga adicional.

Primeiro, criamos posições de partícula em todo o ponto central da experiência na inicialização. Distribuímos as partículas mais densas em todo o centro e menos para a distância. Nós classificamos previamente todas as partículas do centro para trás para que as partículas mais próximas sejam renderizadas primeiro.

Um sombreador de computação deve obter uma amostra da textura de informações de nuvem para posicionar cada partícula em uma altura correta e Colorá-la com base na densidade.

Usamos *DrawProcedural* para renderizar um quad por partícula, permitindo que os dados de partícula permaneçam sempre na GPU.

Cada partícula continha uma altura e um raio. A altura foi baseada nos dados de nuvem amostrados da textura de informações de nuvem, e o raio era baseado na distribuição inicial em que seria calculado para armazenar a distância horizontal para o vizinho mais próximo. Os quatro processadores usariam esses dados para se orientarem em ângulo pela altura, de modo que, quando os usuários olharem isso horizontalmente, a altura seja mostrada e, quando os usuários olhassem de cima para baixo, a área entre seus vizinhos seria coberta.

![Forma de partícula](images/particle-shape-700px.png)

**Código do sombreador mostrando a distribuição:**

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

Como classificamos as partículas front-to-back e ainda usamos um sombreador de estilo sólido para recortar (não misturar) pixels transparentes, essa técnica trata de uma quantidade surpreendente de partículas, evitando um dispendioso excesso de empates mesmo nos computadores com menor capacidade.

## <a name="transparent-particle-clouds"></a>Nuvens de partículas transparentes

As partículas sólidas forneciam uma boa sensação orgânica à forma das nuvens, mas ainda precisavam de algo para vender o fluffiness de nuvens. Decidimos tentar uma solução personalizada para as placas gráficas de alto nível em que podemos introduzir transparência.

Para fazer isso, simplesmente alternamos a ordem de classificação inicial das partículas e alteramos o sombreador para usar as texturas alfa.

![Nuvens Fluffys](images/fluffy-clouds-700px.jpg)

Parece ótimo, mas provou ser muito pesado para até mesmo as máquinas mais difíceis, pois isso resultaria na renderização de cada pixel na tela centenas de vezes!

## <a name="render-off-screen-with-lower-resolution"></a>Renderizar fora da tela com resolução mais baixa

Para reduzir o número de pixels processados pelas nuvens, começamos a renderizá-los em um buffer de resolução de trimestre (em comparação à tela) e esticar o resultado final de volta para a tela depois que todas as partículas tivessem sido desenhadas. Isso nos deu aproximadamente um 4x aumento de velocidade, mas vem com algumas advertências.

**Código para renderização fora da tela:**

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

Primeiro, ao renderizar em um buffer fora da tela, perdemos todas as informações de profundidade de nossa cena principal, resultando em partículas por trás da renderização de montanhas sobre a montanha.

Em segundo lugar, o alongamento do buffer também introduziu artefatos nas bordas de nossas nuvens em que a alteração da resolução foi perceptível. As próximas duas seções falam sobre como resolvemos esses problemas.

## <a name="particle-depth-buffer"></a>Buffer de profundidade de partícula

Para fazer com que as partículas coexistam com a geometria mundial em que uma montanha ou um objeto possa cobrir partículas por trás dela, populamos o buffer fora da tela com um buffer de profundidade que contém a geometria da cena principal. Para produzir esse buffer de profundidade, criamos uma segunda câmera, Renderizando apenas a geometria sólida e a profundidade da cena.

Em seguida, usamos a nova textura no sombreador de pixel das nuvens para occlude pixels. Usamos a mesma textura para calcular a distância para a geometria por trás de um pixel de nuvem. Ao usar essa distância e aplicá-la ao alfa do pixel, agora tínhamos o efeito das nuvens desaparecendo à medida que elas ficam perto do terreno, removendo qualquer recorte fixo onde as partículas e o terreno se encontram.

![Nuvens mescladas no terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Ajustando as bordas

As nuvens ampliadas se parecevam quase idênticas às nuvens de tamanho normal no centro das partículas ou nas quais elas se sobrepostam, mas mostraram alguns artefatos nas bordas da nuvem. Caso contrário, as bordas nítidas aparecerão borradas e os efeitos de alias foram introduzidos quando a câmera fosse movida.

Resolvemos isso executando um sombreador simples no buffer fora da tela para determinar onde ocorreram grandes alterações (1). Colocamos os pixels com grandes alterações em um novo buffer de estêncil (2). Em seguida, usamos o buffer de estêncil para mascarar essas áreas de alto contraste ao aplicar o buffer fora da tela de volta à tela, resultando em buracos em e em todas as nuvens (3).

Em seguida, renderizamos todas as partículas novamente no modo de tela inteira, mas desta vez usamos o buffer de estêncil para mascarar tudo, exceto as bordas, resultando em um conjunto mínimo de pixels tocadas (4). Como o buffer de comando já foi criado para as partículas, simplesmente tivemos que renderizá-lo novamente na nova câmera.

![Progressão do processamento de bordas de nuvem](images/cloud-steps-1-4-700px.jpg)

O resultado final foi bordas nítidas com seções do centro barato das nuvens.

Embora isso fosse muito mais rápido do que renderizar todas as partículas em tela inteira, ainda há um custo associado ao teste de um pixel em relação ao buffer do estêncil, de modo que uma grande quantidade de sobreempates ainda veio com um custo.

## <a name="culling-particles"></a>Remoção de partículas

Para nosso efeito de vento, geramos extensões de triângulo longos em um sombreador de computação, criando muitos WISPs de vento no mundo. Embora o efeito de vento não tenha sido pesado na taxa de preenchimento devido a faixas skinnis geradas, ele produziu muitas centenas de milhares de vértices, resultando em uma carga pesada para o sombreador de vértice.

Introduzimos buffers de acréscimo no sombreador de computação para alimentar um subconjunto das faixas de vento a serem desenhadas. Com alguns frustum de exibição simples de seleção de lógica no sombreador de computação, poderíamos determinar se uma tira estava fora do modo de exibição de câmera e impedir que ela fosse adicionada ao buffer de envio por push. Isso reduziu significativamente a quantidade de faixas, liberando alguns ciclos necessários na GPU.

**Código que demonstra um buffer de acréscimo:**

*Sombreador de computação:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#auto-completar*

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

Tentamos usar a mesma técnica nas partículas de nuvem, em que poderíamos alterá-las no sombreador de computação e apenas enviar por push as partículas visíveis a serem renderizadas. Na verdade, essa técnica não nos salvou muito na GPU, uma vez que o maior afunilamento era a quantidade de pixels renderizados na tela, e não o custo de calcular os vértices.

O outro problema dessa técnica era que o buffer de acréscimo foi populado em ordem aleatória devido à sua natureza paralelizada de computação das partículas, fazendo com que as partículas classificadas não sejam classificadas, resultando na cintilação de partículas de nuvem.

Há técnicas para classificar o buffer de push, mas a quantidade limitada de acertos de desempenho que acabamos de escolher partículas provavelmente seria compensada com uma classificação adicional, portanto, decidimos não buscar essa otimização.

## <a name="adaptive-rendering"></a>Renderização adaptável

Para garantir uma taxa de quadros constante em um aplicativo com condições de renderização diferentes, como uma nuvem versus uma exibição clara, introduzimos a renderização adaptável em nosso aplicativo.

A primeira etapa da renderização adaptável é medir a GPU. Fizemos isso inserindo código personalizado no buffer de comando da GPU no início e no final de um quadro renderizado, capturando o horário da tela de olho à esquerda e à direita.

Medindo o tempo gasto renderizando e comparando-o à nossa taxa de atualização desejada, temos uma noção de como devemos descartar os quadros.

Ao fechar os quadros, adaptamos nossa renderização para torná-lo mais rápido. Uma maneira simples de adaptar-se é alterar o tamanho do visor da tela, exigindo menos pixels para ser renderizado.

Usando *UnityEngine. XR. XRSettings. renderViewportScale* , o sistema reduz o visor de destino e alonga automaticamente o resultado de volta para o ajuste à tela. Uma pequena alteração na escala é mal perceptível na geometria mundial, e um fator de escala de 0,7 requer metade da quantidade de pixels a serem renderizados.

![70% de escala, metade dos pixels](images/datascape-scaling-700px.jpg)

Quando detectamos que estamos prestes a descartar os quadros, reduzimos a escala por um número fixo e o aumentamos quando estamos executando rápido o suficiente novamente.

Embora decidimos qual técnica de nuvem usar com base nos recursos gráficos do hardware na inicialização, é possível baseá-la nos dados da medição da GPU para impedir que o sistema permaneça em baixa resolução por um longo tempo, mas isso é algo que não temos tempo  para explorar em Datascape.

## <a name="final-thoughts"></a>Pensamentos finais

O direcionamento a uma variedade de hardware é desafiador e requer algum planejamento.

Recomendamos que você comece a direcionar computadores com menor capacidade para se familiarizar com o espaço do problema e desenvolver uma solução de backup que será executada em todos os seus computadores. Projete sua solução com a taxa de preenchimento em mente, pois os pixels serão seus recursos mais preciosos. Direcionar a geometria sólida sobre transparência.

Com uma solução de backup, você pode iniciar a disposição em camadas em mais complexidade para máquinas de alto nível ou talvez apenas aprimorar a resolução da solução de backup.

Design para cenários de pior caso e talvez considere o uso de processamento adaptável para situações pesadas.

## <a name="about-the-authors"></a>Sobre os autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>Engenheiro de software @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Engenheiro de software @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Consulte também
* [Entendendo o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para o Unity](performance-recommendations-for-unity.md)

 

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
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Estudo de caso - dimensionamento Datascape em todos os dispositivos com diferentes de desempenho

Datascape é um aplicativo de realidade mista do Windows desenvolvido internamente na Microsoft em que nos concentramos sobre como exibir dados meteorológicos sobre os dados de terreno. O aplicativo explora as percepções exclusivas que os usuários obtêm da descoberta de dados na realidade mista, envolvendo o usuário com a visualização de dados holographic.

Para Datascape queríamos uma variedade de plataformas de destino com recursos de hardware diferentes que variam do Microsoft HoloLens para fones imersivos em exposição Windows Mixed Reality e de PCs baseados em inferior para os PCs mais recentes com GPU high-end. O principal desafio era renderizando nossa cena em questão visualmente atraente em dispositivos com recursos gráficos totalmente diferente durante a execução de uma alta taxa de quadros.

Este estudo de caso percorrerá o processo e as técnicas usadas para criar alguns dos nossos mais sistemas de uso intenso da GPU, que descrevem os problemas encontrados e como podemos superou.

## <a name="transparency-and-overdraw"></a>Transparência e excedente

Nosso lutas renderização principal lidam com transparência, como transparência pode ser cara em uma GPU.

Geometria sólida pode ser renderizada de frente para trás ao gravar no buffer de profundidade, interrompendo os pixels futuras localizados por trás desse pixel de ser descartado. Isso impede que oculta pixels executando o sombreador de pixel, acelerando o processo consideravelmente. Se a geometria é classificada de maneira ideal, cada pixel na tela será desenhada apenas uma vez.

Necessidades de geometria transparente a ser classificada de volta para a frente e se baseia em mistura a saída do sombreador de pixel para o pixel atual na tela. Isso pode resultar em cada pixel na tela que está sendo desenhada para várias vezes por quadro, conhecido como excedente.

Para o HoloLens e PCs predominantes, a tela só pode ser preenchida inúmeras vezes, tornando transparente de um problema de renderização.

## <a name="introduction-to-datascape-scene-components"></a>Introdução aos componentes de cena Datascape

Tivemos três componentes principais de nossa cena; **a interface do usuário, o mapa**, e **o clima**. Sabíamos desde o início que nosso efeitos de clima exigiria GPU sempre foi possível obter, portanto, propositadamente projetamos a interface do usuário e o terreno, de forma que reduziria qualquer excedentes.

Retrabalhamos a interface do usuário várias vezes para minimizar a quantidade de excedente produziria. Erramos na lateral da geometria mais complexa em vez de arte transparente sobreposição sobre o outro para componentes como brilhantes visões gerais de botões e o mapa.

Para o mapa, usamos um sombreador personalizado que seria retirar os recursos padrão do Unity como sombras e iluminação complexa, substituí-los com um modelo de iluminação simples sun único e um cálculo personalizado neblina. Isso produziu um sombreador de pixel simples e liberar ciclos GPU.

Nós conseguimos obter a interface do usuário e o mapa para renderização no orçamento onde não é necessário todas as alterações a eles dependendo do hardware; No entanto, a visualização de previsão do tempo, em particular a renderização de nuvem, provou para ser um desafio!

## <a name="background-on-cloud-data"></a>Em segundo plano nos dados de nuvem

Nossos dados de nuvem tiver sido baixados de servidores da NOAA (http://nomads.ncep.noaa.gov/) e veio para nós em três camadas distintas de 2D, cada um com a altura da parte superior e inferior da nuvem, bem como a densidade da nuvem para cada célula da grade. Os dados obteve processados em uma textura de informações da nuvem em que cada componente foi armazenado no componente vermelho, verde e azul da textura para facilitar o acesso na GPU.

## <a name="geometry-clouds"></a>Nuvens de geometria

Para garantir que nossos computadores baseados em inferior possa renderizar nossas nuvens, decidimos que começar com uma abordagem que usaria a geometria sólida para minimizar o excedente.

Primeiro, tentamos produzindo nuvens por meio da geração de uma malha de heightmap sólida para cada camada usando o raio da textura de informações de nuvem por vértice para gerar a forma. Usamos um sombreador de geometria para produzir os vértices na parte superior e a parte inferior da nuvem gera formas de nuvem sólida. Usamos o valor de densidade de textura para a nuvem de cores com cores mais escuras para mais densas nuvens.

**Sombreador para criar vértices:**

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

Apresentamos um padrão de ruído pequeno para obter mais detalhes sobre os dados reais. Para produzir bordas de nuvem redonda, podemos recortada os pixels no sombreador de pixel quando o valor de raio interpolada atinge um limite para descartar os valores de quase zero.

![Nuvens de geometria](images/datascape-geometry-clouds-700px.jpg)

Como as nuvens são geometria sólida, eles podem ser processados antes do terreno para ocultar qualquer pixels mapa caro abaixo para melhorar ainda mais a taxa de quadros. Essa solução foi executado bem em todas as placas gráficas da especificação de min placas gráficas high-end, bem como em HoloLens, devido à abordagem de processamento a geometria sólida.

## <a name="solid-particle-clouds"></a>Nuvens de partícula sólida

Agora tínhamos uma solução de backup que produziu uma representação decente de nossos dados de nuvem, mas foi um pouco lackluster no fator de "wow" e não transmitem a sensação volumétricas que queríamos para nosso máquinas high-end.

Nossa próxima etapa foi criando as nuvens, que representa-los com aproximadamente 100.000 partículas para produzir uma aparência mais orgânica e volumétricas.

Se partículas permanecem estável e classificar de frente para trás, podemos ainda podem se beneficiar do buffer de profundidade traseira dos pixels por trás de partículas anteriormente renderizadas, reduzindo a excedentes. Além disso, com uma solução baseada em partículas, podemos alterar a quantidade de partículas usado para hardware de destino diferente. No entanto, todos os pixels ainda precisam ser testado em profundidade, que resulta em alguma sobrecarga adicional.

Primeiro, criamos posições de partícula em torno do ponto central da experiência na inicialização. Podemos distribuído as partículas mais densamente em torno do centro e, portanto, menos na distância. Podemos previamente classificados todas as partículas no centro para trás de modo que as partículas mais próximas renderização pela primeira vez.

A textura de informações da nuvem para posicionar cada partícula em uma altura correta e a cor de acordo com a densidade de exemplo seria um sombreador de cálculo.

Usamos *DrawProcedural* renderizar um quad por partículas, permitindo que os dados de partícula permanecer na GPU em todos os tempos.

Cada partícula continha uma altura e um raio. A altura foi com base nos dados de nuvem exemplificados a textura de informações de nuvem e o raio foi com base na distribuição inicial onde ele será calculado para armazenar a distância horizontal para seu vizinho mais próximo. Os quadrados usaria esses dados para orientar o próprio angular pela altura para que quando os usuários examiná-la horizontalmente, a altura seria mostrada e quando os usuários olhar de cima para baixo, a área entre seus vizinhos seria abordada.

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

Como podemos classificar a partículas frente para trás e ainda, usamos um sombreador de estilo sólido para pixels transparentes do clipe (não blend), essa técnica trata uma quantidade surpreendente de partículas, evitando a dispendioso desenho em excesso, mesmo em computadores baseados em inferior.

## <a name="transparent-particle-clouds"></a>Nuvens de partícula transparente

As partículas sólidas fornecido uma boa ideia orgânica na forma de nuvens, mas ainda precisava algo para vender o fluffiness de nuvens. Decidimos tentar uma solução personalizada para os cartões de gráficos avançados, onde podemos apresentar transparência.

Para fazer isso simplesmente alternado a ordem de classificação inicial das partículas e alterou o sombreador para usar o alfa de texturas.

![A Fluffy nuvens](images/fluffy-clouds-700px.jpg)

Pareciam ótimo, mas provou para ser muito pesada para até mesmo as máquinas mais difíceis, pois resultaria no processamento de cada pixel na tela de centenas de vezes!

## <a name="render-off-screen-with-lower-resolution"></a>Processar fora da tela com resolução mais baixa

Para reduzir o número de pixels renderizados por nuvens, começamos a renderização-los no buffer de resolução de um trimestre (em comparação comparada a tela) e ampliar o resultado final faça backup para a tela depois que todas as partículas tivessem sido desenhadas. Isso nos deu aproximadamente um aumento de velocidade 4 x, mas veio com algumas limitações.

**Código para a renderização de fora da tela:**

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

Primeiro, ao renderizar em um buffer fora da tela, perdemos todas as informações de profundidade da cena nosso principal, resultando em partículas por trás de montanhas renderização na parte superior a montanha.

Em segundo lugar, alongando o buffer também introduziu artefatos nas bordas do nosso nuvens em que a alteração de resolução foi perceptível. As duas próximas seções falam sobre como resolvemos esses problemas.

## <a name="particle-depth-buffer"></a>Buffer de profundidade de partícula

Para tornar as partículas coexiste com a geometria do mundo em que um objeto ou mountain poderia englobar partículas por trás dele, preenchemos o buffer fora da tela com um buffer de profundidade que contém a geometria da cena principal. Para produzir esse buffer de profundidade, criamos uma segunda câmera, renderizar apenas a geometria sólida e a profundidade da cena.

Em seguida, usamos a nova textura no sombreador de pixel das nuvens para occlude pixels. Nós usamos a mesma textura para calcular a distância à geometria por trás de um pixel de nuvem. Usando essa distância e aplicá-lo para o alfa do pixel, podemos agora tinha o efeito de nuvens desaparecimento conforme eles chegarem perto o terreno, removendo qualquer cortes onde se encontram partículas e terreno.

![Nuvens em um terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Nitidez bordas

As nuvens alongados para cima tinha quase idênticas para as nuvens de tamanho normal no centro das partículas ou onde eles sobrepostas, mas mostraram alguns artefatos nas bordas de nuvem. Caso contrário, bordas nítidas apareceria desfocadas e efeitos de alias foram introduzidos quando movido a câmera.

Solucionamos essa questão, executando um sombreador simple no buffer de fora da tela para determinar em que grandes alterações ocorreram por outro lado (1). Colocamos os pixels com grandes alterações em um novo buffer de estêncil (2). Em seguida, usamos o buffer de estêncil máscara essas áreas de alto contraste ao aplicar o buffer fora da tela na tela, resultando em falhas em e relacionado as nuvens (3).

Podemos então processado todas as partículas novamente no modo de tela inteira, mas este tempo usado para mascarar tudo o que o buffer de estêncil, mas as bordas, resultando em um conjunto mínimo de pixels tocadas (4). Uma vez que o buffer de comando já foi criado para as partículas, simplesmente tivemos para renderizá-lo novamente para a nova câmera.

![Progressão de renderização de bordas de nuvem](images/cloud-steps-1-4-700px.jpg)

O resultado final era bordas nítidas com seções barato center das nuvens.

Embora isso era muito mais rápido que a renderização de tela cheia de todas as partículas de, há ainda um custo associado com o teste de um pixel no buffer de estêncil, portanto, uma grande quantidade de excedente ainda veio com um custo.

## <a name="culling-particles"></a>Remoção de partículas

Para nosso efeito de vento, geramos faixas de triângulo longa em um sombreador de cálculo, a criação de muitos wisps de vento no mundo. Enquanto o efeito de vento não estava pesado na taxa de preenchimento devido a faixas magro gerado, ele produziu várias centenas de milhares de vértices, resultando em uma carga pesada para o sombreador de vértices.

Introduzimos o acréscimo de buffers no sombreador de cálculo para alimentar um subconjunto das faixas vento a ser desenhado. Com alguma exibição simples frustum escolhidos lógica no sombreador de cálculo, poderíamos determinar se uma faixa estava fora do modo de exibição da câmera e impedi-lo de que está sendo adicionada ao buffer de envio por push. Isso reduziu a quantidade de faixas significativamente, liberando alguns ciclos necessários na GPU.

**Código que demonstra um buffer de acréscimo:**

*Sombreador de cálculo:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#código:*

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

Tentamos usando a mesma técnica sobre as partículas de nuvem, onde podemos seria analisá-los sobre o sombreador de cálculo e apenas enviar por push as partículas visíveis a ser renderizado. Essa técnica, na verdade, não salvou nos muito na GPU, já que o maior afunilamento foi os pixels de quantidade renderizados na tela e não o custo de calcular os vértices.

O outro problema com essa técnica foi que o buffer de acréscimo é populado em ordem aleatória devido à sua natureza em paralelo de partículas, fazendo com que as partículas classificadas seja não classificada, resultando em cintilantes partículas de nuvem de computação.

Há técnicas para classificar o buffer de envio por push, mas a quantidade limitada de ganho de desempenho, temos fora traseira partículas provavelmente seria deslocamento com uma classificação adicional, portanto, decidimos não buscar essa otimização.

## <a name="adaptive-rendering"></a>Renderização adaptável

Para garantir uma taxa de quadros estável em um aplicativo com diferentes condições, como um nublado vs de renderização uma visão clara, introduzimos renderização adaptável ao nosso aplicativo.

A primeira etapa de renderização adaptável é medir a GPU. Fizemos isso inserindo o código personalizado no buffer de comandos GPU no início e no final de um quadro renderizado, capturando ambos esquerda e direita olho tempo da tela.

Medindo o tempo gasto de renderização e compará-lo a nossa desejado-taxa de atualização, temos uma ideia de quão próximo precisássemos descarte de quadros.

Quando perto de descarte de quadros, podemos adaptar nosso processamento para torná-lo mais rapidamente. Uma maneira simples de se adaptar está mudando o tamanho do visor da tela, exigindo menos pixels a serem renderizado.

Usando *UnityEngine.XR.XRSettings.renderViewportScale* o sistema reduz o visor do destino e estende-se automaticamente o resultado para a tela de ajuste. Uma pequena alteração no dimensionamento é quase imperceptível no geometria mundial, e um fator de escala de 0,7 requer metade da quantidade de pixels a serem renderizados.

![escala de 70%, metade dos pixels](images/datascape-scaling-700px.jpg)

Quando Detectamos que estamos prestes a descartar quadros, podemos reduzir a escala por um número fixo e aumentar-o novamente quando estamos executando novamente rápido o suficiente.

Embora, decidimos qual técnica de nuvem para usar com base em elementos gráficos, recursos do hardware na inicialização, é possível baseá-la em dados da medida GPU para impedir que o sistema permaneça em baixa resolução por um longo tempo, mas isso é algo que não tínhamos tempo  para explorar o Datascape.

## <a name="final-thoughts"></a>Considerações finais

Direcionamento de uma variedade de hardware é um desafio e exige algum planejamento.

É recomendável que você comece a direcionar computadores baseados em inferior para se familiarizar com o espaço do problema e desenvolver uma solução de backup que será executado em todos os seus computadores. Crie sua solução com taxa de preenchimento em mente, já que pixels será seu recurso mais precioso. Geometria sólida de destino de transparência.

Com uma solução de backup, você pode iniciar, em seguida, disposição em camadas em mais de complexidade para máquinas de high-end ou talvez apenas aprimorar a resolução de sua solução de backup.

Design para os piores cenários e talvez considere usando renderização adaptável para situações pesadas.

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
* [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)

 

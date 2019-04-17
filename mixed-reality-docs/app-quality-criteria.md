---
title: Critérios de qualidade do aplicativo
description: Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: critérios de qualidade do aplicativo, realidade, misturada misto de aplicativo de realidade
ms.openlocfilehash: 8070a434be462a636b314527c59f299ca77fb6d4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590413"
---
# <a name="app-quality-criteria"></a>Critérios de qualidade do aplicativo

Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada. Para cada fator as informações a seguir são fornecidas
* Visão geral – uma breve descrição de como o fator de qualidade e por que é importante.
* Impacto do dispositivo - qual tipo de dispositivo de realidade misturada da janela é afetado.
* Critérios de qualidade – como avaliar o fator de qualidade.
* Como medir – métodos de medir (ou experiência) o problema.
* Recomendações – resumidas das abordagens para proporcionar uma melhor experiência de usuário.
* Recursos – desenvolvedor relevante e recursos de design que são úteis para criar melhores experiências de aplicativo.

## <a name="frame-rate"></a>Taxa de quadros

Taxa de quadros é o primeiro pilar de conforto holograma de estabilidade e o usuário. Taxa de quadros abaixo os destinos de recomendada pode causar hologramas apareçam instável, afetando negativamente a credibilidade da experiência e possivelmente causando fadiga olho. A taxa de quadros de destino para a sua experiência em fones imersivos em exposição Windows Mixed Reality será 60Hz ou 90Hz, dependendo de quais computadores de compatível com Windows misto realidade você deseja dar suporte. Para HoloLens a taxa de quadros de destino é 60Hz.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
| O aplicativo atender consistentemente quadros por segundo objetivo (FPS) para o dispositivo de destino: 60fps em HoloLens; 90fps em PCs Ultra; e 60fps em PCs de base. | O aplicativo tem descartes de intermitente de quadro não prejudicam a experiência de principal; ou FPS é consistentemente inferiores a meta desejada, mas não impessa a experiência de aplicativo. | O aplicativo está passando por uma queda na taxa de quadros em média a cada dez segundos ou menos. |

### <a name="how-to-measure"></a>Como medir

* Um gráfico de taxa de quadro em tempo real é fornecido por meio de pela [Windows Device Portal](using-the-windows-device-portal.md#system-performance) sob "Desempenho do sistema".
* Para desenvolvimento de depuração, adicione um contador de diagnóstico de taxa de quadros no aplicativo. Consulte os recursos de um contador de exemplo.
* Descartes de taxa de quadros podem ser experimentadas no dispositivo, enquanto o aplicativo está em execução, movendo sua cabeça de lado a lado. Se o holograma mostra movimentação trêmulo inesperada, em seguida, baixa taxa de quadros ou o plano de estabilidade provavelmente é a causa.

### <a name="recommendations"></a>Recomendações

* Adicione um contador da taxa de quadros no início do trabalho de desenvolvimento.
* As alterações que incorrem em uma queda na taxa de quadros devem ser avaliadas e resolvidas adequadamente como um bug de desempenho.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)
* [Taxa de quadros e a estabilidade de holograma](hologram-stability.md#frame-rate)
* [Orçamento de desempenho de ativos](asset-creation-process.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [MRToolkit, exibição de contador FPS](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, sombreadores](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Referências externas

* [Unity, otimização de aplicativos móveis](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Estabilidade holograma

Hologramas estáveis aumentar a usabilidade e a credibilidade do seu aplicativo e criar uma experiência de exibição mais à vontade para o usuário. A qualidade da estabilidade holograma é um resultado de desenvolvimento de aplicativos boa e capacidade do dispositivo entender (faixa) seu ambiente. Embora a taxa de quadros é o primeiro pilar de estabilidade, outros fatores podem afetar a estabilidade incluindo:

* Uso do plano de estabilização
* Distância até âncoras espaciais
* Acompanhamento

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  Hologramas consistentemente aparecem estáveis. | Exibe o conteúdo secundário movimentação inesperada; ou movimentação inesperada não impede a experiência geral do aplicativo. | Conteúdo principal em quadro exibe movimentação inesperada. |

### <a name="how-to-measure"></a>Como medir

Ao mesmo tempo usando o dispositivo e a experiência de exibição:

* Mover sua cabeça de lado a lado, se o hologramas mostram a movimentação inesperada, em seguida, baixa taxa de quadros ou alinhamento incorreto do plano de estabilidade para o plano focal é a causa provável.
* Mover-se o ambiente e hologramas, procure comportamentos como raias e jumpiness. Esse tipo de movimento provavelmente é causado pelo dispositivo não controla o ambiente ou a distância para a âncora espacial.
* Se for grande ou vários hologramas estão no quadro, observar o comportamento de holograma em várias intensidades enquanto mover sua posição principal de lado a lado, se shakiness for exibida, isso provavelmente causado por plano de estabilização.

### <a name="recomendations"></a>Recomendações de

* Adicione um contador da taxa de quadros no início do trabalho de desenvolvimento.
* Use o plano de estabilização.
* Sempre processa hologramas ancoradas dentro de 3 medidores de sua âncora.
* Verifique se o que seu ambiente está configurado para o controle apropriado.
* Projetar sua experiência para evitar hologramas em vários níveis de profundidade focal dentro do quadro.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Taxa de quadros e a estabilidade de holograma](hologram-stability.md#frame-rate)
* [Estudo de caso, usando o plano de estabilização](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Âncoras espaciais](spatial-anchors.md)
* [Rastreamento de tratamento de erros](coordinate-systems.md#handling-tracking-errors)
* [Quadro estacionário de referência](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Kit de complementar MR, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Posição hologramas em superfícies real

Misalignments de hologramas com objetos físicos (se se destina a ser colocado em relação a um outro) é uma indicação clara do que a não-união hologramas e reais. Precisão da colocação deve ser relativo às necessidades do cenário. Por exemplo, posicionamento superfície geral pode usar o mapa espacial, mas o posicionamento mais preciso exigirá algum uso de marcadores e de calibração.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
| Hologramas alinham para a superfície normalmente nos centímetros para intervalo polegadas. Se mais precisão for necessária, o aplicativo deve fornecer um meio eficaz para colaboração entre as especificações do aplicativo desejado. | N/D | As hologramas aparecem não alinhadas com o objeto de destino físico, quebrando o plano de superfície ou que aparecem para float para fora da superfície de. Se a precisão for necessária, hologramas devem atender a especificação de proximidade do cenário. | 

### <a name="how-to-measure"></a>Como medir

* Hologramas que são colocadas no mapa espacial não devem aparecer drasticamente flutuando acima ou abaixo da superfície.
* Hologramas que exigem colocação precisa devem ter alguma forma de marcador e calibragem sistema que tem a precisão do requisito do cenário.

### <a name="recommendations"></a>Recomendações

* Mapa espacial é útil para colocar objetos em superfícies quando a precisão não é necessária.
* Para obter a melhor precisão, use marcadores ou cartazes para definir as hologramas e um controlador do Xbox (ou algum mecanismo de alinhamento manual) para calibragem final.
* Considere dividir hologramas extra grandes em partes lógicas e alinhar cada parte para a superfície.
* Incorretamente conjunto interpupilary distância (IPD) também pode afetar o alinhamento de holograma. Sempre configure HoloLens para IPD do usuário.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Posicionamento de mapeamento espacial](spatial-mapping.md#placement)
* [Processo de verificação de espaço](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Práticas recomendadas de âncoras espacial](spatial-anchors.md#best-practices)
* [Rastreamento de tratamento de erros](coordinate-systems.md#handling-tracking-errors)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Visão geral do desenvolvimento Vuforia](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [MR Spatial 230: Mapeamento espacial](holograms-230.md)
* [MR o Kit de ferramentas, bibliotecas de mapeamento espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [Kit de complementar MR, exemplo de calibragem de pôster](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [Kit de complementar MR, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Referências externas

* [Estudo de caso de Lowes, alinhamento de precisão](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Exibição de zona de conforto

Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergirem colocando conteúdo e hologramas em várias intensidades. Os usuários vestindo HoloLens sempre acomodará 2.0 m para manter uma imagem clara como HoloLens exibe são corrigidos em uma distância óptica aproximadamente 2.0m do usuário. Profundidade do conteúdo inadequada pode levar a discomfort visual ou fadiga.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

<table>
<tr>
<td> Melhor </td><td><ul>
<li>Colocar o conteúdo em 2m.</li><li>Quando hologramas não podem ser colocadas em 2m, e não podem ser evitados conflitos entre a convergência e acomodação, a zona ideal para posicionamento holograma é entre 1,25 milhões e milhões de 5.</li><li>Em todos os casos, designers devem estruturar o conteúdo a fim de incentivar os usuários interajam 1 + m imediatamente (por exemplo, ajustar o tamanho do conteúdo e padrão de parâmetros de posicionamento).</li><li>A menos que especificamente não exigido pelo cenário, um plano de corte deve ser implementar com fadeout começando em 1 milhão.</li><li>Em casos onde uma observação mais próxima de um holograma imóvel é necessária, o conteúdo não deve ser mais próximo do que 50cm.</li>
</ul></td>
</tr><tr>
<td> Atenda às</td><td> O conteúdo é dentro a orientação de exibição e movimento, mas o uso inadequado ou nenhum uso do plano de recorte.</td>
</tr><tr>
<td> falhar </td><td> O conteúdo é apresentado muito próximas (normalmente &lt;1,25 m, ou &lt;50 cm para hologramas estáticos que exigem mais próxima Observação.)</td>
</tr>
</table>

### <a name="how-to-measure"></a>Como medir

* Conteúdo deve ser 2m geralmente ausente, mas não mais próximo que 1,25 ou mais de 5 minutos.
* Com poucas exceções, a distância de renderização de recorte do HoloLens deve ser definida como .85CM com fadeout começando em 1 milhão de conteúdo. Abordar o conteúdo e observe o efeito de plano de recorte.
* Conteúdo estático não deve ficar mais próximo do que 50cm de distância.

### <a name="recommendations"></a>Recomendações

* Criar conteúdo para a distância de exibição ideal de 2M.
* Defina a distância de renderização de recorte para 85cm com fadeout começando em 1 milhão de conteúdo.
* Para hologramas estacionários que precisam exibir mais próximo, o plano de corte deve ser não mais próximo do que 30cm e fadeout deve começar pelo menos 10cm para longe do plano de recorte.

### <a name="resources"></a>Recursos

* [Renderizar distância](hologram-stability.md#hologram-render-distances)
* [Ponto de foco no Unity](focus-point-in-unity.md)
* [Experimentar a escala](scale.md#experimenting-with-scale)
* [Texto, tamanho da fonte recomendado](typography.md#recommended-font-size)

## <a name="depth-switching"></a>Alternância de profundidade

Independentemente da zona de exibição de problemas de conforto, as exigências do usuário alterne rapidamente ou com frequência entre quase e muito focal objetos (incluindo hologramas e conteúdo do mundo real) podem levar a fadiga oculomotor e discomfort geral.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  Profundidade natural ou limitada alternância que não fazem com que o usuário se concentre em unnaturally. | Comutador de profundidade abrupta esse é o núcleo e projetado para a experiência de aplicativo, ou comutador de profundidade abrupta causada por conteúdo inesperado do mundo real. | Comutador de profundidade consistente, ou profundidade abrupta alternância que não é necessário ou núcleo para a experiência de aplicativo. | 

### <a name="how-to-measure"></a>Como medir

* Se o aplicativo requer que o usuário para consistentemente e/ou abruptamente mudar o foco de profundidade, não há profundidade, alternando o problema.

### <a name="recommendations"></a>Recomendações

* Manter o conteúdo principal em um plano focal consistente e verifique se que o plano de estabilização corresponde ao plano focal. Isso irá aliviar fadiga oculomotor e movimentação holograma inesperado.

### <a name="resources"></a>Recursos

* [Renderizar distância](hologram-stability.md#hologram-render-distances)
* [Ponto de foco no Unity](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Uso de som espacial

Na realidade mista do Windows, o mecanismo de áudio fornece o componente auricular da experiência de realidade misturada, simulando 3D som usando simulações ambientais, distância e direção. Usando o som espacial em um aplicativo permite aos desenvolvedores colocar convincingly sons em um espaço dimensional 3 (esfera) em todo o usuário. Os sons, em seguida, parecerá como se eles foram provenientes de objetos físicos real ou as hologramas de realidade misturada no ambiente do usuário. Som espacial é uma ferramenta poderosa para uma imersão, acessibilidade e design UX em aplicativos de realidade misturada.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  Som é logicamente spatialized e a experiência do usuário adequadamente usa som para ajudá-lo com comentários de usuário e a descoberta de objeto. Som é natural e relevantes para objetos e normalizada entre o cenário. | Áudio espacial é usada adequadamente para credibilidade mas ausente como meio para ajudar com a capacidade de descoberta e comentários do usuário. | Som não é spatialized conforme o esperado, e/ou falta de som para auxiliar o usuário dentro a experiência do usuário. Ou áudio espacial não foi considerado ou usado no design do cenário. | 

### <a name="how-to-measure"></a>Como medir

* Em geral, os sons relevantes devem emitir de hologramas de destino (por exemplo,., som latido provenientes de dog holográfica.)
* Indicações de som devem ser usadas em toda a experiência do usuário para ajudar o usuário com reconhecimento de ações fora do quadro holográfica ou comentários.

### <a name="recommendations"></a>Recomendações

* Use o áudio espacial para ajudá-lo com interfaces de usuário e a descoberta de objeto.
* Sons real funcionam melhor do que sintetização ou som não natural.
* A maioria dos sons devem ser spatialized.
* Evite os emissores invisíveis.
* Evite mascaramento espacial.
* Normalize todos os sons.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Som espacial](spatial-sound.md)
* [Design de som espacial](spatial-sound-design.md)
* [Som espacial no Unity](spatial-sound-in-unity.md)
* [Estudo de caso, espacial som para HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Estudo de caso, usando o som espacial RoboRaid](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [MR Spatial 220: Som espacial](holograms-220.md)
* [MRToolkit, áudio espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Concentre-se em limites de quadro holográfica (FOV)

Experiências de usuário bem projetado podem criar e manter o contexto úteis do ambiente virtual que se estende em torno dos usuários. Reduzir o efeito dos limites FOV envolve um design elaborado de escala de conteúdo e contexto, o uso de áudio espacial, sistemas de orientação e a posição do usuário. Se feito corretamente, o usuário se sentirão que menor prejudicada por limites de FOV tendo uma experiência de aplicativo à vontade.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  Usuário nunca perde o contexto e exibição se sente confortável. Assistência de contexto é fornecida para objetos grandes. Detectabilidade e exibindo a orientação é fornecida para objetos fora do quadro. Em geral, o design de movimento e a escala das hologramas são apropriadas para uma experiência visual confortável. | Usuário nunca perde o contexto, mas o movimento do pescoço extra pode ser necessário em algumas situações. Em algumas situações escala faz com que hologramas quebrar tanto o quadro vertical ou horizontal, fazendo com que algum movimento pescoço exibir hologramas. | Usuário poderá perder o contexto e/ou movimento do pescoço consistente é necessária para exibir hologramas. Nenhuma orientação de contexto para objetos grandes holográfica, mover objetos muito fácil perder fora do quadro sem diretrizes de capacidade de descoberta ou a altura hologramas requer movimento pescoço regular para exibir. | 

### <a name="how-to-measure"></a>Como medir

* Contexto para um holograma (grande) for perdido ou não é compreendido devido ao que está sendo cortado nos limites.
* Local do hologramas são difíceis de encontrar devido à falta de diretores de atenção ou conteúdo que se move rapidamente para dentro e fora do quadro holográfico.
* Cenário requer regular e repetitivas para cima e para a animação principal para ver totalmente um holograma resultando em fadiga pescoço.

### <a name="recommendations"></a>Recomendações

* Inicie a experiência com objetos pequenos que se ajustar a FOV, em seguida, fazer a transição com visuais para versões maiores.
* Use espaciais diretores de áudio e atenção para conteúdo de localizar o usuário que está fora do FOV da Ajuda.
* Tanto quanto possível, evite hologramas que recortar verticalmente o FOV.
* Fornece ao usuário uma diretriz no aplicativo para melhor visualização local.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Quadro holográfico](holographic-frame.md)
* [Estudo de caso, a UI HoloStudio e lições aprendidas de design de interação](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Escala de objetos e ambientes](scale.md)
* [Cursores, indicações visuais](cursors.md#visual-cues)

#### <a name="external-references"></a>Referências externas

* [Muitos ados sobre o FOV](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>Conteúdo reage a posição do usuário

Hologramas devem reagir para a posição do usuário aproximadamente da mesma maneira que objetos de "real". Uma consideração de design importantes é a elementos de interface do usuário que não não necessariamente assumem que a posição de um usuário está parados e adaptar-se a animação do usuário. Criação de um aplicativo que corretamente se adapta a posição de usuário criar uma experiência mais verossímeis e torná-lo mais fácil de usar.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

<table>
<tr>
<td> Melhor </td><td> Conteúdo e a interface do usuário se adaptar às posições de usuário, permitindo que o usuário interagir naturalmente com o conteúdo dentro do escopo de movimentação do usuário esperado.</td>
</tr><tr>
<td> Atenda às </td><td> Interface do usuário se adapta para a posição do usuário, mas pode impedir a exibição do conteúdo da chave exigir que o usuário ajustar sua posição.</td>
</tr><tr>
<td> falhar </td><td><ol>
<li>Elementos de interface do usuário são perdidos ou bloqueados durante usuário causando movimentação controles unnaturally retornar a (ou encontrar).</li><li>Elementos de interface do usuário limitam a exibição do conteúdo principal.</li><li>Movimentação da interface do usuário não é otimizada para exibição de distância e momentum particularmente com <a href="billboarding-and-tag-along.md">tag-along</a> elementos de interface do usuário.</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Como medir

* Todas as medidas devem ser feitas dentro de um escopo razoável do cenário. Enquanto o movimento do usuário irá variar, não tente fazer o aplicativo com a movimentação de usuário extremo.
* Para elementos de interface do usuário, controles relevantes devem estar disponíveis, independentemente de movimentação do usuário. Por exemplo, se o usuário está exibindo e andar de um mapa 3D com o zoom, o controle de zoom deve ser prontamente disponível para o usuário, independentemente do local.

### <a name="recommendations"></a>Recomendações

* O usuário é a câmera e eles controlam a movimentação. Deixe-os da unidade.
* Considere billboarding para texto e os sistemas de menus que caso contrário, seriam bloqueada pelo mundo ou obscurecidos se um usuário eram mover-se.
* Use tag-along conteúdo que precisa acompanhar o usuário enquanto ainda permite que o usuário veja o que está na frente delas.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Design de interação](hologram.md)
* [Cor, luz e material](color,-light-and-materials.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)
* [Conceitos básicos de interação](interaction-fundamentals.md)
* [O motion Self e locomotion do usuário](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Entrada MR 210: Gaze](holograms-210.md)

## <a name="input-interaction-clarity"></a>Clareza de interação de entrada

Clareza de interação de entrada é essencial para facilidade de uso do aplicativo e inclui a entrada consistência, acessibilidade, detectabilidade de métodos de interação. Usuário deve ser capaz de usar toda a plataforma de interações comuns sem que eles reaprendessem. Se o aplicativo tem uma entrada personalizada, ele deve ser claramente comunicado e demonstrado.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  Métodos de interação de entrada são consistentes com o Windows Mixed Reality fornecidos [orientação](interaction-fundamentals.md). Qualquer entrada personalizada não deve ser redundante com a entrada padrão (em vez disso, use padrão interação) e deve ser comunicada claramente e demonstrou que o usuário. | Semelhante às entradas melhor, mas personalizadas são redundantes com métodos de entrada padrão. Usuário ainda pode alcançar a meta e o progresso por meio da experiência do aplicativo. | Difícil de entender o mapeamento de método ou o botão de entrada. Entrada é muito personalizado, não dá suporte a entrada padrão, não há instruções, ou pode causar problemas de fadiga e conforto. | 

### <a name="how-to-measure"></a>Como medir

* O aplicativo usa consistente [métodos de entrada padrão.](interaction-fundamentals.md)
* Se o aplicativo tem uma entrada de Customer, ele claramente é comunicado por meio de:
* Experiência de primeira execução
* Telas introdutórias
* Dicas de ferramenta
* Coach mão
* Seção de ajuda
* Comando de voz

### <a name="recommendations"></a>Recomendações

* Use os métodos de entrada padrão sempre que possível.
* Fornece demonstrações, tutoriais e dicas de ferramenta para métodos de entrada não padrão.
* Use um modelo de interação consistente em todo o aplicativo.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Conceitos básicos de interação de Windows MR](interaction-fundamentals.md)
* [Objetos interagível](interactable-object.md)
* [Mantenha o foco de direcionamento](gaze-targeting.md)
* [Cursores](cursors.md)
* [Conforto e olhar](comfort.md#gaze-direction)
* [Gestos](gestures.md)
* [Entrada de voz](voice-input.md)
* [Design de voz](voice-design.md)
* [Controladores de movimento](motion-controllers.md)
* [Entrada de portabilidade de guia para Unity](input-porting-guide-for-unity.md)
* [Entrada do teclado no Unity](keyboard-input-in-unity.md)
* [Mantenha o foco no Unity](gaze-in-unity.md)
* [Gestos e controladores de movimento no Unity](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz no Unity](voice-input-in-unity.md)
* [Teclado, mouse e entrada do controlador em DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)
* [Olhar, gesto e controladores de movimento no DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Estudo de caso: A busca de computação mais pessoais](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Estudo de conversão: UI HoloStudio e lições aprendidas de design de interação](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Aplicativo de exemplo: Tabela periódica dos elementos](periodic-table-of-the-elements.md)
* [Aplicativo de exemplo: Módulo Lunar](lunar-module.md)
* [Entrada MR 210: Gaze](holograms-210.md)
* [Entrada MR 211: Gestos](holograms-211.md)
* [Entrada MR 212: Voz](holograms-212.md)

## <a name="interactable-objects"></a>Objetos interagível

Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D. No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais. Nada pode ser um objeto Interagível que dispara um evento. Um objeto interagível pode ser representado como qualquer coisa uma xícara de café na tabela para um balão flutuar no ar. Independentemente da forma, objetos interagível devem ser claramente reconhecíveis por usuário por meio de indicações de áudio e vídeo.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  Independentemente do formulário, objetos interagível são reconhecidos por meio de indicações de áudio e vídeo em três estados: ocioso, direcionadas e selecionado. "Consulte, diga" é claro e consistente usado em toda a experiência. Objetos são dimensionados e distribuídos para permitir o direcionamento de sem erros. | Usuário pode reconhecer o objeto como interagível por meio de comentários de áudio ou de visual e de destino e ativar o objeto. | Considerando sem indicações de áudio ou de visual, usuário não pode reconhecer um objeto interagível. As interações são propenso a falhas devido a escala do objeto ou a distância entre os objetos. | 

### <a name="how-to-measure"></a>Como medir

* Objetos interagível podem ser reconhecidos como 'interagível'; incluindo conteúdo específico do aplicativo, menus e botões. Como regra geral deve haver uma indicação visual e áudio ao direcionar objetos interagível.

### <a name="recommendations"></a>Recomendações

* Use comentários de áudio e vídeo para interações.
* Feedback visual deve ser diferenciada para cada estado (ocioso, destino, selecionado) de entrada
* Objetos interagível devem ser dimensionados e colocados para direcionamento de sem erros.
* Os objetos agrupados interagível (por exemplo, uma barra de menus ou lista) devem ter espaçamento correto para o direcionamento.
* Botões e menus que dão suporte ao comando de voz devem fornecer rótulos de texto para a palavra-chave de comando ("vê-lo, diga")

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Objeto interagível](interactable-object.md)
* [Texto no Unity](text-in-unity.md)
* [Barra de aplicativo e a caixa delimitadora](app-bar-and-bounding-box.md)
* [Design de voz](voice-design.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Kit de ferramentas de realidade misturada - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Espaço disponível para verificação

Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo. A integridade e a qualidade dos dados depende de vários fatores, incluindo a quantidade de exploração que o usuário tenha feito, quanto tempo se passou desde a exploração e se os objetos como móveis e portas foram movidas desde a área de verificação de dispositivo. Muitos aplicativos analisará os dados de mapeamento espacial no início da experiência para avaliar se o usuário deve executar etapas adicionais para melhorar a integridade e a qualidade do mapa espacial. Se o usuário é necessário para verificar o ambiente, desmarque diretrizes devem ser fornecida durante a experiência de verificação.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  Visualização da malha espacial informar os usuários de verificação está em andamento. Claramente o usuário sabe o que fazer e quando a varredura inicia e para. | Visualização da malha espacial for fornecida, mas o usuário pode não sabe claramente o que fazer e nenhuma informação de progresso é fornecida. | Nenhuma visualização da malha. Nenhuma informação de orientação fornecida ao usuário sobre onde procurar, ou quando a varredura inicia/para. |

### <a name="how-to-measure"></a>Como medir

* Durante uma verificação de espaço necessário, são fornecidas orientações de áudio e vídeo que indica onde procurar e quando iniciar e Parar verificação.

### <a name="recommendations"></a>Recomendações

* Indica quanto o volume total nas proximidades usuários precisa fazer parte da experiência.
* Comunicar-se quando a verificação é iniciado e é interrompido, como um indicador de progresso.
* Use uma visualização da malha durante a verificação.
* Fornece indicações de áudio e vídeo para incentivar o usuário procure e mover-se na sala.
* Informar ao usuário aonde ir para melhorar os dados. Em muitos casos, talvez seja melhor informar ao usuário o que precisam (por exemplo, examinar o limite, procure por trás de móveis), para obter a qualidade de verificação necessárias.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Visualização de verificação de espaço](room-scan-visualization.md)
* [Estudo de caso: Expandindo os recursos de mapeamento espacial do HoloLens](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Estudo de caso: Projeto de som espacial para HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Estudo de caso: Criando uma experiência imersiva em fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Kit de ferramentas de realidade misturada - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicadores direcionais

Em um aplicativo de realidade misturada, o conteúdo pode estar fora de vista do campo ou obstruídos pelo objetos do mundo real. Um aplicativo bem projetado tornará mais fácil para o usuário localizar conteúdo não visíveis. Indicadores direcionais alertam um usuário ao conteúdo importante e fornecem orientação para o conteúdo em relação à posição do usuário. Diretrizes para o conteúdo não visíveis podem assumir a forma de emissores de som, as setas direcionais ou indicações visuais diretas.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  As indicações de áudio e vídeo diretamente guiam o usuário ao conteúdo relevante fora o campo de visualização. | Uma seta ou alguns indicador que aponta para o usuário na direção geral do conteúdo. | Conteúdo relevante é fora do campo de visão e ruim ou nenhuma orientação para a localização é fornecida ao usuário. | 

### <a name="how-to-measure"></a>Como medir

* O conteúdo relevante fora do campo de vista do usuário é descoberto por meio de indicações visuais e/ou áudio.

### <a name="recommendations"></a>Recomendações

* Quando o conteúdo relevante estiver fora de vista de campo do usuário, use indicadores direcionais e as indicações de áudio para orientar o usuário ao conteúdo. Em muitos casos, um guia visual direto é preferível as setas direcionais.
* Indicadores direcionais não devem ser criados no cursor.

### <a name="resources"></a>Recursos

* [Quadro holográfico](holographic-frame.md)

## <a name="data-loading"></a>Carregamento de dados

Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento. Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso é visível e também pode indicar quanto tempo o tempo de espera pode ser.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Melhor  |  Atenda às |  falhar |
--- | --- | ---
|  Indicador visual animado, na forma de uma barra de progresso ou um anel, mostrando o progresso durante qualquer carregando ou processamento de dados. O indicador visual fornece orientações sobre quanto tempo de espera pode ser. | Usuário é informado de que o carregamento de dados está em andamento, mas não há nenhuma indicação de quanto tempo de espera pode ser. | Nenhum carregamento de dados ou indicadores de processo para a tarefa demorando mais do que 5 segundos. |

### <a name="how-to-measure"></a>Como medir

* Durante o carregamento de dados, verifique se que não houver nenhum estado em branco por mais de 5 segundos.

### <a name="recommendations"></a>Recomendações

* Forneça um animator de carregamento de dados mostrando o progresso em qualquer situação, quando o usuário poderão perceber esse aplicativo tenha interrompido ou falhou. Uma regra prática razoável é qualquer atividade de 'carregamento' que pode levar mais de 5 segundos.

### <a name="resources"></a>Recursos

* [Exibindo o progresso](progress.md)

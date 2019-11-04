---
title: Critérios de qualidade do aplicativo
description: Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: critérios de qualidade do aplicativo, realidade misturada, aplicativo de realidade misturada
ms.openlocfilehash: f98111ebe9aacc30778e86501be41e6ac5f6d165
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437042"
---
# <a name="app-quality-criteria"></a>Critérios de qualidade do aplicativo

Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada. Para cada fator, as informações a seguir são fornecidas
* Visão geral – uma breve descrição do fator de qualidade e por que ele é importante.
* Impacto do dispositivo – qual tipo de o dispositivo de realidade misturada da janela é afetado.
* Critérios de qualidade – como avaliar o fator de qualidade.
* Como medir – métodos para medir (ou experimentar) o problema.
* Recomendações – Resumo de abordagens para fornecer uma melhor experiência do usuário.
* Recursos – desenvolvedor relevante e recursos de design que são úteis para criar melhores experiências de aplicativo.

## <a name="frame-rate"></a>Taxa de quadros

A taxa de quadros é o primeiro pilar da estabilidade do holograma e do conforto do usuário. A taxa de quadros abaixo dos destinos recomendados pode fazer com que os hologramas pareçam tremulação, afetando negativamente a believability da experiência e potencialmente causando fadiga de olho. A taxa de quadros de destino para sua experiência em headsets de imersão de realidade mista do Windows será de 60Hz ou 90Hz, dependendo de quais computadores compatíveis com o Windows Mixed Reality você deseja dar suporte. Para o HoloLens, a taxa de quadros de destino é 60.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
| O aplicativo atende consistentemente a meta de quadros por segundo (FPS) para o dispositivo de destino: 60fps no HoloLens; 90fps em ultra PCs; e 60fps nos PCs de base. | O aplicativo tem quedas de quadros intermitentes que não impedem a experiência principal; ou FPS é consistentemente menor do que a meta desejada, mas não impede a experiência do aplicativo. | O aplicativo está apresentando uma queda na taxa de quadros em média a cada dez segundos ou menos. |

### <a name="how-to-measure"></a>Como medir

* Um grafo de taxa de quadros em tempo real é fornecido pelo [portal do dispositivo do Windows](using-the-windows-device-portal.md#system-performance) em "desempenho do sistema".
* Para a depuração de desenvolvimento, adicione um contador de diagnóstico de taxa de quadros ao aplicativo. Consulte recursos para um contador de exemplo.
* Quedas de taxa de quadros podem ser experimentadas no dispositivo enquanto o aplicativo está em execução, movendo seu cabeçalho de lado para o outro. Se o holograma mostrar uma movimentação de tremulação inesperada, a taxa de quadros baixa ou o plano de estabilidade provavelmente será a causa.

### <a name="recommendations"></a>Recomendações

* Adicione um contador de taxa de quadros no início do trabalho de desenvolvimento.
* As alterações que incorrem em uma taxa de quadros de queda devem ser avaliadas e resolvidas adequadamente como um bug de desempenho.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Entendendo o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Estabilidade e taxa de quadros do holograma](hologram-stability.md#frame-rate)
* [Orçamento de desempenho do ativo](asset-creation-process.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [MRToolkit, exibição do contador de FPS](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, sombreadores](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Referências externas

* [Unity, otimizando aplicativos móveis](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Estabilidade do holograma

Os hologramas estáveis aumentarão a usabilidade e a believability de seu aplicativo e criarão uma experiência de exibição mais confortável para o usuário. A qualidade da estabilidade do holograma é um resultado do bom desenvolvimento de aplicativos e da capacidade do dispositivo de entender (controlar) seu ambiente. Embora a taxa de quadros seja o primeiro pilar da estabilidade, outros fatores podem afetar a estabilidade, incluindo:

* Uso do plano de estabilização
* Distâncias para âncoras espaciais
* Controle alterações

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  Os hologramas parecem consistentemente estáveis. | Conteúdo secundário exibe movimento inesperado; ou o movimento inesperado não impede a experiência geral do aplicativo. | O conteúdo principal no quadro exibe movimento inesperado. |

### <a name="how-to-measure"></a>Como medir

Ao desgastar o dispositivo e exibir a experiência:

* Mova seu cabeçalho do lado a lado, se os hologramas mostrarem movimento inesperado, a taxa de quadros baixa ou o alinhamento impróprio do plano de estabilidade para o plano focal é a causa provável.
* Mova-se para os hologramas e o ambiente, procure comportamentos como, por exemplo, nada e salto. Esse tipo de movimento é provavelmente causado pelo dispositivo não rastreando o ambiente ou pela distância para a âncora espacial.
* Se houver grandes ou vários hologramas no quadro, observe o comportamento do holograma em várias profundidades ao mover sua posição de cabeçalho de lado a lado, se shakiness parecer que isso é provavelmente causado pelo plano de estabilização.

### <a name="recomendations"></a>Recomendações

* Adicione um contador de taxa de quadros no início do trabalho de desenvolvimento.
* Use o plano de estabilização.
* Sempre renderizar hologramas ancorados dentro de 3 metros de sua âncora.
* Verifique se o ambiente está configurado para o acompanhamento adequado.
* Projete sua experiência para evitar hologramas em vários níveis de profundidade focal dentro do quadro.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Estabilidade e taxa de quadros do holograma](hologram-stability.md#frame-rate)
* [Estudo de caso, usando o plano de estabilização](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Entendendo o desempenho da realidade misturada](understanding-performance-for-mixed-reality.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Âncoras espaciais](spatial-anchors.md)
* [Manipulação de erros de controle](coordinate-systems.md#handling-tracking-errors)
* [Quadro estacionário de referência](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Sr Companion Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Posição dos hologramas em superfícies reais

Os desalinhamentos de hologramas com objetos físicos (se a intenção de serem colocados em relação uns aos outros) são uma indicação clara da não União de hologramas e do mundo real. A precisão do posicionamento deve ser relativa às necessidades do cenário; por exemplo, o posicionamento de superfície geral pode usar o mapa espacial, mas o posicionamento mais preciso exigirá algum uso de marcadores e calibragem.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
| Os hologramas se alinham à superfície normalmente no intervalo de centímetros para polegadas. Se for necessário mais precisão, o aplicativo deverá fornecer um meio eficiente de colaboração na especificação do aplicativo desejado. | N/D | Os hologramas aparecem desalinhados com o objeto de destino físico, dividindo o plano de superfície ou aparecendo flutuando para fora da superfície. Se a precisão for necessária, os hologramas devem atender à especificação de proximidade do cenário. | 

### <a name="how-to-measure"></a>Como medir

* Os hologramas que são colocados no mapa espacial não devem parecer muito flutuar acima ou abaixo da superfície.
* Os hologramas que exigem posicionamento preciso devem ter alguma forma de marcador e sistema de calibração que seja precisa do requisito do cenário.

### <a name="recommendations"></a>Recomendações

* O mapa espacial é útil para colocar objetos em superfícies quando a precisão não é necessária.
* Para obter a melhor precisão, use marcadores ou cartazes para definir os hologramas e um controlador Xbox (ou algum mecanismo de alinhamento manual) para a calibragem final.
* Considere quebrar hologramas grandes e extras em partes lógicas e alinhar cada parte à superfície.
* O IPD (Interpupilary Distance) definido incorretamente também pode afetar o alinhamento do holograma. Sempre configure o HoloLens para o IPD do usuário.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Posicionamento de mapeamento espacial](spatial-mapping.md#placement)
* [Processo de verificação de sala](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Práticas recomendadas das âncoras espaciais](spatial-anchors.md#best-practices)
* [Manipulação de erros de controle](coordinate-systems.md#handling-tracking-errors)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Visão geral do desenvolvimento do Vuforia](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [MR espacial 230: mapeamento espacial](holograms-230.md)
* [Sr Toolkit, bibliotecas de mapeamento espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [Sr Companion Kit, exemplo de calibração de pôster](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [Sr Companion Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Referências externas

* [Estudo de caso do Lowes, alinhamento de precisão](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Exibindo a zona de conforto

Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergem colocando o conteúdo e os hologramas em várias profundidades. Os usuários com o HoloLens serão sempre acomodados a 2,0 m para manter uma imagem clara porque as exibições do HoloLens são corrigidas a uma distância óptica de aproximadamente 2,0 m para longe do usuário. A profundidade de conteúdo inadequado pode levar ao Visual discomfort ou fadiga.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

<table>
<tr>
<td> Recomendá </td><td><ul>
<li>Coloque o conteúdo em 2m.</li><li>Quando os hologramas não podem ser colocados em 2m e os conflitos entre a convergência e a acomodação não podem ser evitados, a zona ideal para o posicionamento do holograma é entre 1,25 m e 5 min.</li><li>Em todos os casos, os designers devem estruturar o conteúdo para incentivar os usuários a interagir de 1 + m (por exemplo, ajustar o tamanho do conteúdo e os parâmetros de posicionamento padrão).</li><li>A menos que não seja especificamente exigido pelo cenário, um plano de recorte deve ser implementado com FadeOut a partir de 1m.</li><li>Nos casos em que a observação mais próxima de um holograma sem movimento é necessária, o conteúdo não deve ser mais próximo de 50cm.</li>
</ul></td>
</tr><tr>
<td> Corresponde</td><td> O conteúdo está dentro das diretrizes de visualização e movimentação, mas uso inadequado ou não uso do plano de recorte.</td>
</tr><tr>
<td> Recuperação </td><td> O conteúdo é apresentado muito próximo (normalmente &lt;1,25 m ou &lt;50cm para hologramas fixos que exigem uma observação mais detalhada.)</td>
</tr>
</table>

### <a name="how-to-measure"></a>Como medir

* O conteúdo normalmente deve ser de 2m, mas não mais de 1,25 ou mais do que 5 min.
* Com poucas exceções, a distância de renderização de recorte de HoloLens deve ser definida como. 85CM com esmaecimento de conteúdo a partir de 1m. Aborde o conteúdo e observe o efeito do plano de recorte.
* O conteúdo estacionário não deve estar mais próximo do que 50cm.

### <a name="recommendations"></a>Recomendações

* Crie conteúdo para a distância de exibição ideal de 2m.
* Defina a distância de renderização de recorte como 85cm com esmaecimento de conteúdo a partir de 1m.
* Para hologramas estáticos que precisam de exibição mais próxima, o plano de recorte não deve ser mais próximo que 30cm e FadeOut deve iniciar pelo menos 10cm fora do plano de recorte.

### <a name="resources"></a>Recursos

* [Distância de renderização](hologram-stability.md#hologram-render-distances)
* [Ponto de foco no Unity](focus-point-in-unity.md)
* [Experimentando a escala](scale.md#experimenting-with-scale)
* [Texto, tamanho de fonte recomendado](typography.md#recommended-font-size)

## <a name="depth-switching"></a>Alternância de profundidade

Independentemente da exibição da zona de problemas de conforto, as demandas pelo usuário de alternar com frequência ou rapidamente entre objetos focalmente próximos e distantes (incluindo hologramas e conteúdo do mundo real) podem levar a oculomotor fadiga e discomfort geral.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  Alternância de profundidade limitada ou natural que não faz com que o usuário se concentre de volta natural. | A mudança de profundidade abrupta é fundamental e projetada para a experiência do aplicativo ou para o interruptor de profundidade abrupta que é causado pelo conteúdo real do mundo inesperado. | Opção de profundidade consistente ou alternância de profundidade abrupta que não é necessária ou essencial para a experiência do aplicativo. | 

### <a name="how-to-measure"></a>Como medir

* Se o aplicativo exigir que o usuário altere o foco de profundidade de forma consistente e/ou abruptamente, haverá um problema de alternância de profundidade.

### <a name="recommendations"></a>Recomendações

* Mantenha o conteúdo principal em um plano focal consistente e verifique se o plano de estabilização corresponde ao plano focal. Isso aliviará o oculomotor fadiga e o movimento de holograma inesperado.

### <a name="resources"></a>Recursos

* [Distância de renderização](hologram-stability.md#hologram-render-distances)
* [Ponto de foco no Unity](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Uso de som espacial

No Windows Mixed Reality, o mecanismo de áudio fornece o componente auricular da experiência de realidade misturada por meio da simulação de som 3D usando a direção, a distância e as simulações ambientais. O uso de som espacial em um aplicativo permite que os desenvolvedores coloquem os sons de forma convincente em um espaço 3 dimensional (esfera) em todo o usuário. Esses sons parecerão como se estivessem vindo de objetos físicos reais ou de hologramas de realidade misturada no ambiente do usuário. O som espacial é uma ferramenta poderosa para imersão, acessibilidade e design de UX em aplicativos de realidade misturada.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  O som é logicamente espacial e o UX usa o som adequadamente para auxiliar na descoberta de objetos e nos comentários dos usuários. O som é natural e relevante para objetos e normalizados em todo o cenário. | O áudio espacial é usado adequadamente para believability, mas ausente como meio de ajudar com os comentários do usuário e a descoberta. | O som não está espacial como esperado e/ou falta de som para auxiliar o usuário no UX. Ou o áudio espacial não foi considerado ou usado no design do cenário. | 

### <a name="how-to-measure"></a>Como medir

* Em geral, os sons relevantes devem emitir de hologramas de destino (por exemplo, som latido proveniente do Holographic Dog.)
* As indicações de som devem ser usadas em todo o UX para ajudar o usuário com comentários ou conscientização de ações fora do quadro do Holographic.

### <a name="recommendations"></a>Recomendações

* Use o áudio espacial para auxiliar na descoberta de objeto e nas interfaces do usuário.
* Os sons reais funcionam melhor que o sintetizado ou o som não natural.
* A maioria dos sons deve ser espacial.
* Evite emissores invisíveis.
* Evite mascaramento espacial.
* Normalizar todos os sons.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Som espacial](spatial-sound.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Som espacial no Unity](spatial-sound-in-unity.md)
* [Estudo de caso, som espacial para HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Estudo de caso, usando o som espacial em RoboRaid](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [MR espacial 220: som espacial](holograms-220.md)
* [MRToolkit, áudio espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Foco nos limites do quadro Holographic (FOV)

Experiências de usuário bem projetadas podem criar e manter um contexto útil do ambiente virtual que se estende pelos usuários. Reduzir o efeito dos limites de FOV envolve um design elaborado de escala e contexto de conteúdo, uso de áudio espacial, sistemas de orientação e posição do usuário. Se for feito certo, o usuário se sentirá menos prejudicado pelos limites do FOV enquanto tem uma experiência de aplicativo confortável.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  O usuário nunca perde o contexto e a exibição é confortável. A assistência de contexto é fornecida para objetos grandes. As diretrizes de descoberta e exibição são fornecidas para objetos fora do quadro. Em geral, o design de movimento e a escala dos hologramas são apropriados para uma experiência de exibição confortável. | O usuário nunca perde o contexto, mas o movimento de pescoço extra pode ser necessário em situações limitadas. Em situações limitadas, a escala faz com que os hologramas quebrem o quadro vertical ou horizontal, fazendo com que um movimento de pescoço exiba os hologramas. | O usuário provavelmente perderá o contexto e/ou o movimento de pescoço consistente é necessário para exibir hologramas. Não há diretrizes de contexto para objetos Holographic grandes, movendo objetos fáceis de serem perdidos fora do quadro sem orientação de descoberta ou hologramas altos requer movimento de pescoço regular para exibição. | 

### <a name="how-to-measure"></a>Como medir

* O contexto de um holograma (grande) é perdido ou não compreendido devido a ser recortado nos limites.
* É difícil encontrar o local dos hologramas devido à falta de diretores de atenção ou conteúdo que se movem rapidamente para dentro e para fora do quadro do Holographic.
* O cenário requer um movimento regular e repetitivo para cima e para baixo para ver totalmente um holograma, resultando em fadiga de pescoço.

### <a name="recommendations"></a>Recomendações

* Inicie a experiência com objetos pequenos que se ajustam ao FOV e, em seguida, migre com indicações visuais para versões maiores.
* Use os diretores espaciais de áudio e atenção para ajudar o usuário a encontrar conteúdo fora do FOV.
* Tanto quanto possível, evite hologramas que recortem verticalmente o FOV.
* Forneça ao usuário diretrizes no aplicativo para melhor localização de exibição.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Quadro holográfico](holographic-frame.md)
* [Estudo de caso, interface do usuário do HoloStudio e aprendizado de design de interação](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Escala de objetos e ambientes](scale.md)
* [Cursores, indicações visuais](cursors.md#visual-cues)

#### <a name="external-references"></a>Referências externas

* [Muito ado sobre o FOV](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>O conteúdo reage à posição do usuário

Os hologramas devem reagir à posição do usuário praticamente da mesma maneira que os objetos "reais". Uma consideração de design notável são os elementos da interface do usuário que não podem, necessariamente, supor que a posição dos usuários seja imóvel e se adapte ao movimento do usuário. A criação de um aplicativo que se adapta corretamente à posição do usuário criará uma experiência mais verossímeis e facilitará o uso.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

<table>
<tr>
<td> Recomendá </td><td> O conteúdo e a interface do usuário se adaptam às posições dos usuários, permitindo que o usuário interaja naturalmente com o conteúdo dentro do escopo do movimento de usuário esperado.</td>
</tr><tr>
<td> Corresponde </td><td> A IU se adapta à posição do usuário, mas pode impedir a exibição do conteúdo da chave que exige que o usuário ajuste sua posição.</td>
</tr><tr>
<td> Recuperação </td><td><ol>
<li>Os elementos da interface do usuário são perdidos ou bloqueados durante a movimentação, fazendo com que o usuário volte de volta para (ou localize) controles.</li><li>Os elementos da interface do usuário limitam a exibição do conteúdo primário.</li><li>O movimento da interface do usuário não é otimizado para exibir a distância e a dinâmica particularmente com elementos de interface do usuário com <a href="billboarding-and-tag-along.md">marcas</a> .</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Como medir

* Todas as medidas devem ser feitas dentro de um escopo razoável do cenário. Embora a movimentação do usuário varie, não tente enganar o aplicativo com movimento extremo do usuário.
* Para elementos de interface do usuário, os controles relevantes devem estar disponíveis independentemente do movimento do usuário. Por exemplo, se o usuário estiver exibindo e percorrendo um mapa 3D com zoom, o controle de zoom deverá estar prontamente disponível para o usuário, independentemente do local.

### <a name="recommendations"></a>Recomendações

* O usuário é a câmera e controla o movimento. Deixe-os na unidade.
* Considere a mensagem para os sistemas de texto e de menu que, de outra forma, seriam bloqueados no mundo, se um usuário fosse se movimentando.
* Use uma marca para o conteúdo que precisa seguir o usuário enquanto ainda permite que o usuário veja o que está na frente deles.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Design de interação](hologram.md)
* [Cor, luz e material](color,-light-and-materials.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Locomotion de automovimento e usuário](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Entrada MR 210: olhar](holograms-210.md)

## <a name="input-interaction-clarity"></a>Clareza da interação de entrada

A clareza da interação de entrada é essencial para a usabilidade de um aplicativo e inclui consistência de entrada, capacidade de detecção, descoberta de métodos de interação. O usuário deve ser capaz de usar interações comuns em toda a plataforma sem reaprender. Se o aplicativo tiver uma entrada personalizada, ele deverá ser claramente comunicado e demonstrado.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  Os métodos de interação de entrada são consistentes com as [diretrizes](interaction-fundamentals.md)do Windows Mixed Reality fornecidas. Qualquer entrada personalizada não deve ser redundante com entrada padrão (em vez disso, usar a interação padrão) e deve ser claramente comunicada e demonstrada para o usuário. | Semelhante à melhor, mas as entradas personalizadas são redundantes com métodos de entrada padrão. O usuário ainda pode alcançar a meta e o progresso por meio da experiência do aplicativo. | É difícil entender o método de entrada ou o mapeamento de botão. A entrada é bastante personalizada, não dá suporte à entrada padrão, não há instruções ou provavelmente causar problemas de fadiga e conforto. | 

### <a name="how-to-measure"></a>Como medir

* O aplicativo usa [métodos de entrada padrão](interaction-fundamentals.md) consistentes.
* Se o aplicativo tiver uma entrada personalizada, ele será claramente comunicado por meio de:
* Experiência de primeira execução
* Telas introdutórias
* Dicas de ferramenta
* Mão-executiva
* Seção de ajuda
* Voz sobre

### <a name="recommendations"></a>Recomendações

* Use métodos de entrada padrão sempre que possível.
* Forneça demonstrações, tutoriais e dicas de ferramenta para métodos de entrada não padrão.
* Use um modelo de interação consistente em todo o aplicativo.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Interações instinctuais](interaction-fundamentals.md)
* [Objetos que interagem](interactable-object.md)
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Cursores](cursors.md)
* [Conforto e olhar](comfort.md#gaze-direction)
* [Entrada de voz](voice-input.md)
* [Controladores de movimentos](motion-controllers.md)
* [Guia de portabilidade de entrada para Unity](input-porting-guide-for-unity.md)
* [Entrada do teclado no Unity](keyboard-input-in-unity.md)
* [Foco no Unity](gaze-in-unity.md)
* [Gestos e controladores de movimento no Unity](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz no Unity](voice-input-in-unity.md)
* [Teclado, mouse e entrada do controlador no DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)
* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Estudo de caso: a busca de mais computação pessoal](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Estudo de conversão: aprendizado de HoloStudio de interface do usuário e interação do projeto](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Aplicativo de exemplo: tabela periódica dos elementos](periodic-table-of-the-elements.md)
* [Aplicativo de exemplo: módulo lunar](lunar-module.md)
* [Entrada MR 210: olhar](holograms-210.md)
* [Entrada MR 211: gestos](holograms-211.md)
* [Entrada MR 212: voz](holograms-212.md)

## <a name="interactable-objects"></a>Objetos que interagem

Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D. No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração. Qualquer coisa pode ser um objeto que possa ser interagindo que dispara um evento. Um objeto de interação pode ser representado como qualquer coisa de uma xícara de café na mesa até um balão flutuante no ar. Independentemente do formulário, os objetos interajantes devem ser claramente reconhecidos pelo usuário por meio de indicações visuais e de áudio.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  Independentemente do formulário, os objetos que podem interagir são reconhecidos por meio de indicações visuais e de áudio em três Estados: ocioso, direcionado e selecionado. "Vê-lo, digamos que" é claro e consistentemente usado em toda a experiência. Os objetos são dimensionados e distribuídos para permitir o direcionamento livre de erros. | O usuário pode reconhecer o objeto como interagindo por meio de áudio ou comentários visuais e pode direcionar e ativar o objeto. | Não devido a indicações visuais ou de áudio, o usuário não consegue reconhecer um objeto que pode ser interagindo. As interações são propensas a erros devido à escala ou à distância do objeto entre objetos. | 

### <a name="how-to-measure"></a>Como medir

* Os objetos que podem interagir são reconhecíveis como ' interagindo '; incluindo botões, menus e conteúdo específico do aplicativo. Como regra prática, deve haver um Visual e uma indicação de áudio ao direcionar objetos que podem interagir.

### <a name="recommendations"></a>Recomendações

* Use comentários visuais e de áudio para interações.
* Os comentários visuais devem ser diferenciados para cada Estado de entrada (ocioso, direcionado, selecionado)
* Os objetos que podem ser interagindo devem ser dimensionados e colocados para direcionamento de erro livre.
* Objetos de interação agrupada (como uma barra de menus ou lista) devem ter o espaçamento adequado para o direcionamento.
* Os botões e menus que dão suporte ao comando de voz devem fornecer rótulos de texto para a palavra-chave Command ("vê-lo, digamos")

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Objeto interativo](interactable-object.md)
* [Texto no Unity](text-in-unity.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Entrada de voz](voice-input.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Kit de ferramentas de realidade misturada-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Verificação de sala

Os aplicativos que exigem dados de mapeamento espacial dependem do dispositivo para coletar automaticamente esses dados ao longo do tempo e entre as sessões, à medida que o usuário explora seu ambiente com o dispositivo ativo. A integridade e a qualidade desses dados dependem de vários fatores, incluindo a quantidade de explorações que o usuário fez, quanto tempo passou desde a exploração e se os objetos como mobília e portas foram movidos desde que o dispositivo examinou a área. Muitos aplicativos analisarão os dados de mapeamento espacial no início da experiência para avaliar se o usuário deve executar etapas adicionais para melhorar a integridade e a qualidade do mapa espacial. Se o usuário for solicitado a verificar o ambiente, as diretrizes claras devem ser fornecidas durante a experiência de verificação.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  A visualização da malha espacial informa aos usuários que a verificação está em andamento. O usuário sabe claramente o que fazer e quando a verificação é iniciada e interrompida. | A visualização da malha espacial é fornecida, mas o usuário pode não saber claramente o que fazer e nenhuma informação de progresso é fornecida. | Nenhuma visualização da malha. Nenhuma informação de orientação fornecida ao usuário sobre onde procurar ou quando a verificação é iniciada/interrompida. |

### <a name="how-to-measure"></a>Como medir

* Durante uma verificação de sala necessária, as diretrizes de áudio e visuais são fornecidas, indicando onde procurar e quando iniciar e parar a verificação.

### <a name="recommendations"></a>Recomendações

* Indique quanto do volume total nos arredores dos usuários precisa fazer parte da experiência.
* Comunique-se quando a verificação for iniciada e parada como um indicador de progresso.
* Use uma visualização da malha durante a verificação.
* Forneça visuais e indicações de áudio para incentivar o usuário a procurar e se movimentar pela sala.
* Informe ao usuário onde ir para melhorar os dados. Em muitos casos, pode ser melhor informar ao usuário o que eles precisam fazer (por exemplo, examinar o teto, examinar os móveis) para obter a qualidade de digitalização necessária.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentação

* [Visualização de varredura do ambiente](room-scan-visualization.md)
* [Estudo de caso: expandindo os recursos de mapeamento espacial do HoloLens](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Estudo de caso: design de som espacial para HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Estudo de caso: criando uma experiência de imersão em fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Ferramentas e tutoriais

* [Kit de ferramentas de realidade misturada-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicadores direcionais

Em um aplicativo de realidade misturada, o conteúdo pode estar fora do campo de exibição ou obstruído por objetos do mundo real. Um aplicativo bem projetado tornará mais fácil para o usuário encontrar conteúdo não visível. Indicadores direcionais alertam um usuário sobre o conteúdo importante e fornecem orientação para o conteúdo relativo à posição do usuário. As diretrizes para conteúdo não visível podem assumir a forma de emissores de som, setas direcionais ou indicações visuais diretas.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  As indicações visuais e de áudio orientam diretamente o usuário ao conteúdo relevante fora do campo de exibição. | Uma seta ou algum indicador que aponta o usuário na direção geral do conteúdo. | O conteúdo relevante está fora do campo de exibição e uma orientação de localização ruim ou nenhuma é fornecida ao usuário. | 

### <a name="how-to-measure"></a>Como medir

* O conteúdo relevante fora do campo de exibição do usuário é detectável por meio de indicações visuais e/ou de áudio.

### <a name="recommendations"></a>Recomendações

* Quando o conteúdo relevante está fora do campo de exibição do usuário, use indicadores direcionais e indicações de áudio para orientar o usuário no conteúdo. Em muitos casos, um guia visual direto é preferencial sobre setas direcionais.
* Indicadores direcionais não devem ser incorporados ao cursor.

### <a name="resources"></a>Recursos

* [Quadro holográfico](holographic-frame.md)

## <a name="data-loading"></a>Carregamento de dados

Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento. Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar quanto tempo de espera pode ser.

### <a name="device-impact"></a>Impacto do dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Critérios de qualidade

|  Recomendá  |  Corresponde |  Recuperação |
--- | --- | ---
|  Indicador visual animado, na forma de uma barra de progresso ou anel, mostrando o progresso durante qualquer carregamento ou processamento de dados. O indicador visual fornece orientação sobre quanto tempo a espera pode ser. | O usuário é informado de que o carregamento de dados está em andamento, mas não há nenhuma indicação de quanto tempo a espera poderia ser. | Nenhum indicador de carregamento ou processo de dados para a tarefa demorando mais do que 5 segundos. |

### <a name="how-to-measure"></a>Como medir

* Durante o carregamento de dados, verifique se não há nenhum estado em branco por mais de 5 segundos.

### <a name="recommendations"></a>Recomendações

* Forneça um Animator de carregamento de dados mostrando o progresso em qualquer situação em que o usuário possa perceber que esse aplicativo está parado ou falhou. Uma regra prática razoável é qualquer atividade de ' carregamento ' que pode levar mais de 5 segundos.

### <a name="resources"></a>Recursos

* [Exibindo o progresso](progress.md)

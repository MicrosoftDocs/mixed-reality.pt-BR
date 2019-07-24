---
title: Introdução ao MRTK versão 2
description: Para novos desenvolvedores interessados em aproveitar o MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, teste, kit de ferramentas de realidade mista, MRTK versão 2, MRTK, ferramentas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750386"
---
# <a name="getting-started-with-mrtk-v2"></a>Introdução ao MRTK v2

## <a name="mrtk-getting-started-guide"></a>Guia de Introdução do MRTK
Consulte o [Guia de introdução do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obter informações sobre como começar a usar o MRTK v2.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>O que é o MRTK (Kit de ferramentas de realidade mista)?
O MRTK é um incrível kit de ferramentas de código-fonte aberto que já existe desde que o HoloLens foi lançado pela primeira vez e não seria onde ele está hoje sem o trabalho árduo de nossa comunidade de desenvolvedores que contribuiu para ele. Nos últimos três anos, ouvimos os comentários da nossa comunidade de desenvolvedores e criamos o MRTK v2 para levar em conta as maiores preocupações.  

O MRTK V2 com Unity é um kit de desenvolvimento de plataforma cruzada de software livre para aplicativos de realidade misturada.  A versão 2 do MRTK tem como objetivo acelerar o desenvolvimento de aplicativos destinados ao Microsoft HoloLens, fones de ouvido (VR) de realidade mista do Windows e plataforma OpenVR. O projeto visa reduzir as barreiras de entrada para criar aplicativos de realidade misturada e contribuir com a comunidade à medida que todos nós crescemos. 


Consulte o [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para saber mais.

## <a name="feature-areas"></a>Áreas de recursos

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema de entrada" width="105"> Sistema de entrada 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Acompanhamento à mão (HoloLens 2)" width="105"> Acompanhamento à mão (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Acompanhamento de olho (HoloLens 2)" width="105">
    Acompanhamento de olho (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comando de voz" width="105"> Comando de voz
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Olhar + Select (HoloLens (1ª gen))" width="105">
    Olhar + Select (HoloLens (1ª gen))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportação" width="105"> Teleportação
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controles de interface de usuário" width="105"> Controles de interface de usuário
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Resolvedor e interações" width="105"> Resolvedor e interações
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualização do controlador" width="105"> Visualização do controlador
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Compreensão espacial" width="105"> Compreensão espacial
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Ferramenta de diagnóstico" width="105"> Ferramenta de diagnóstico
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Sombreador padrão MRTK" width="105"> Sombreador padrão MRTK
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Blocos de construção da interface do usuário e da interação

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Botão" width="250"><br>
    **Button**<br>
    Um controle de botão que dá suporte a vários métodos de entrada, incluindo a mão articulada do HoloLens 2<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Caixa delimitadora" width="250"><br>
    **Caixa delimitadora**<br>
    Interface do usuário padrão para manipular objetos no espaço 3D<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Manipulador de manipulação" width="250"><br>
    **Manipulador de manipulação**<br>
    Script para manipular objetos com uma ou duas mãos<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Slate" width="250"><br>
    **Slate** <br>
    plano de estilo 2D que dá suporte à rolagem com entrada de mão articulada<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Teclado do sistema" width="250"><br>
    **Teclado do sistema**<br>
    Exemplo de script de uso do teclado do sistema no Unity<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interagir" width="250"><br>
     **Interagir** <br>
     Um script para tornar os objetos interagirem com os Estados visuais e o suporte a temas<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    **Solver** <br>
    Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e Magnetism de superfície<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Coleção de objetos" width="250"><br>
    **Coleção de objetos**<br>
    Script para dispor uma matriz de objetos em uma forma tridimensional<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Dica de ferramenta" width="250">  <br>
    **Dessa**<br>
    IU de anotações com sistema âncora/dinâmico flexível que pode ser usado para rotular os controladores de movimento e o objeto<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra de aplicativos" width="250"><br>
    **Barra de aplicativos**<br>
    Interface do usuário para ativação manual da caixa delimitadora<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Ponteiros" width="250"><br>
    **Ponteiro**<br>
    Saiba mais sobre os vários tipos de ponteiros<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualização de mãos" width="250"><br>
     **Visualização de mãos**<br>
     A condireção Visual está no alcance que melhora a confiança da interação direta<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Controle deslizante" width="250"><br>
    **Slider**<br>
    Interface do usuário do slider para ajustar valores que dão suporte à interação de rastreamento direto<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Sombreador padrão MRTK" width="250"><br>
    **Sombreador padrão MRTK**<br>
    O sombreador padrão de MRTK dá suporte a vários elementos de design fluentes com desempenho<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Conjunto de conjunção à mão" width="250"><br>
     **Conjunto de conjunção à mão**<br>
     Demonstra como usar o Solver para anexar objetos às junções de mão<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Acompanhamento de olho: Seleção de destino" width="250"><br>
    **Acompanhamento de olho: Seleção de destino**<br>
    Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Acompanhamento de olho: Navegação" width="250"><br>
    **Acompanhamento de olho: Navega**<br>
    Saiba como rolar automaticamente o texto ou ampliar de forma fluente o conteúdo focado com base no que você está vendo<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Acompanhamento de olho: Mapa de calor" width="250"><br>
    **Acompanhamento de olho: Mapa de calor**<br>
    Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Requisito mínimo para MRTK v2
* Unity 2018.3.x
* Microsoft Visual Studio 2017 ou posterior
* SDK do Windows 18362 + 
* Windows 10 1803 ou posterior

## <a name="new-with-mrtk-v2"></a>Novo com MRTK v2
Queremos enfatizar nosso compromisso com essas ferramentas de plataforma.  Na verdade, aproveitamos o MRTK versão 2 para desenvolver nossas experiências de caixa de entrada, como a OOBE (experiência de configuração) e nosso aplicativo de aprendizado de realidade misturada.  Você também pode esperar ver os novos recursos do HoloLens 2 apresentados pela primeira vez por meio de MRTK, pois acreditamos que é a melhor maneira de desenvolver em nossa plataforma. 

### <a name="modular"></a>Modula
Nós o criamos de uma maneira modular, para que você não precise usar todos os trechos do kit de ferramentas em seu projeto.  Na verdade, há alguns benefícios para isso.  Ele mantém o tamanho do projeto menor, bem como torna mais fácil de gerenciar.  Além disso, como ele é criado com objetos programáveis e é orientado por interface, também é possível substituir os componentes que estão incluídos com os seus próprios, para dar suporte a outros serviços, sistemas e plataformas.


### <a name="cross-platform"></a>Plataforma cruzada
Falando em outras plataformas, ele tem suporte para várias plataformas.  E, embora isso não signifique que todas as plataformas tenham suporte pronto para uso, garantimos que nenhum código do kit de ferramentas será interrompido quando você mudar seu destino de Build para outras plataformas.  A robustez e a extensibilidade com o design modular definem um bom caminho para poder dar suporte a várias plataformas, como ARCore, ARKit e OpenVR.


### <a name="performant"></a>Alto desempenho
Trabalhando com plataformas móveis, nós a construímos com o desempenho em mente.  Isso é extremamente importante, e queríamos garantir que as ferramentas não funcionarão em você.


## <a name="see-also"></a>Consulte também
* [Guia de introdução do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Página inicial da documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Instalar as ferramentas](install-the-tools.md)
* [Portando de HTK/MRTK para MRTK versão 2](mrtk-porting-guide.md)

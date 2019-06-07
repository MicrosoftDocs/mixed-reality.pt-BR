---
title: Introdução ao MRTK versão 2
description: Para novos desenvolvedores que estejam interessados em aproveitando MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, testar, Kit de ferramentas de realidade misturada, MRTK versão 2, MRTK, ferramentas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750386"
---
# <a name="getting-started-with-mrtk-v2"></a>Introdução ao MRTK v2

## <a name="mrtk-getting-started-guide"></a>MRTK guia de Introdução
Consulte a [MRTK guia de Introdução](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obter informações sobre como começar com MRTK V2.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>O que é o Kit de ferramentas de realidade misturada (MRTK)?
O MRTK é um kit de ferramentas incríveis do código-fonte aberto que já existe, pois o HoloLens foi lançado pela primeira vez e não seria onde está sem o trabalho pesado de nossa comunidade de desenvolvedores que contribuíram para ele. Nos últimos 3 anos, temos ouviu os comentários de nossa comunidade de desenvolvedores e criados MRTK v2 para levar as maiores preocupações em conta.  

O v2 MRTK com o Unity é um kit de desenvolvimento de plataforma cruzada do código-fonte aberto para aplicativos de realidade misturada.  MRTK versão 2 destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, headsets do Windows Mixed Reality imersivos (VR) e plataforma OpenVR. O projeto é voltado para reduzir as barreiras à entrada para criar aplicativos de realidade mista e contribuem na comunidade, como todos nós crescer. 


Consulte a [portal de documentação MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para saber mais.

## <a name="feature-areas"></a>Áreas de recurso

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema de entrada" width="105"> Sistema de entrada 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Mão de acompanhamento (HoloLens 2)" width="105"> Mão de acompanhamento (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="(HoloLens 2) de acompanhamento a olho nu" width="105">
    (HoloLens 2) de acompanhamento a olho nu
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comandos de voz" width="105"> Comandos de voz
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Mantenha o foco + selecionar (HoloLens (1º gen))" width="105">
    Mantenha o foco + selecionar (HoloLens (1º gen))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> Teleportation
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controles de interface de usuário" width="105"> Controles de interface de usuário
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Solver e interações" width="105"> Solver e interações
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualização do controlador" width="105"> Visualização do controlador
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Noções básicas sobre espacial" width="105"> Noções básicas sobre espacial
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Ferramenta de diagnóstico" width="105"> Ferramenta de diagnóstico
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Sombreador MRTK padrão" width="105"> Sombreador MRTK padrão
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Blocos da interface do usuário e a criação de interação

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Botão" width="250"><br>
    **Button**<br>
    Um controle de botão que dá suporte a vários métodos de entrada, incluindo a mão de articuladas do HoloLens 2 <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Caixa delimitadora" width="250"><br>
    **Caixa delimitadora**<br>
    Interface do usuário padrão para manipular objetos no espaço 3D <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Manipulador de manipulação" width="250"><br>
    **Manipulador de manipulação**<br>
    Script para manipular objetos com uma ou duas mãos <a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Tablet" width="250"><br>
    **Tablet** <br>
    Plano de estilo 2D que oferece suporte à rolagem com uma entrada articuladas mão <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Teclado do sistema" width="250"><br>
    **Teclado do sistema**<br>
    Script de exemplo de como usar o teclado de sistema no Unity <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interagível" width="250"><br>
     **Interagível** <br>
     Um script para fazer objetos interagível com estados visuais e suporte de tema <a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    **Solver** <br>
    Vários comportamentos de posicionamento como tag-along, o bloqueio de corpo, tamanho de modo constante e magnetismo superfície do objeto <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Coleção de objetos" width="250"><br>
    **Coleção de objetos**<br>
    Script para dispor de uma matriz de objetos em uma forma tridimensional <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Dica de ferramenta" width="250">  <br>
    **Dica de ferramenta**<br>
    Anotação da interface do usuário com o sistema de âncora/dinâmico flexível que pode ser usado para rotular o objeto e controladores de movimento <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra de aplicativo" width="250"><br>
    **Barra de aplicativo**<br>
    Interface do usuário para a ativação manual da caixa delimitadora <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Ponteiros" width="250"><br>
    **Ponteiros**<br>
    Saiba mais sobre os vários tipos de ponteiros <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualização de ponta do dedo" width="250"><br>
     **Visualização de ponta do dedo**<br>
     Funcionalidade Visual na ponta do dedo que melhora a confiança para a interação direta <a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Controle deslizante" width="250"><br>
    **Slider**<br>
    Controle deslizante de interface do usuário para ajustar valores suporte mão direto de interação de controle <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Sombreador MRTK padrão" width="250"><br>
    **Sombreador MRTK padrão**<br>
    Sombreador de padrão do MRTK dá suporte a vários elementos de design Fluent com desempenho <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Chaser conjunta de mão" width="250"><br>
     **Chaser conjunta de mão**<br>
     Demonstra como usar o Solver anexar objetos junções mão <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Acompanhamento a olho nu: Seleção de destino" width="250"><br>
    **Acompanhamento a olho nu: Seleção de destino**<br>
    Combinar os olhos, voz e mão rapidamente e facilmente selecionar hologramas entre sua cena de entrada <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Acompanhamento a olho nu: Navegação" width="250"><br>
    **Acompanhamento a olho nu: Navegação**<br>
    Saiba como auto texto de rolagem ou ampliar fluentemente focalizado conteúdo com base no qual você está examinando <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Acompanhamento a olho nu: Mapa de calor" width="250"><br>
    **Acompanhamento a olho nu: Mapa de calor**<br>
    Exemplos para registro em log, carregar e visualizar o que os usuários têm sido observando em seu aplicativo <a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Requisito mínimo para MRTK v2
* Unity 2018.3.x
* Microsoft Visual Studio 2017 ou posterior
* Windows SDK 18362 + 
* Windows 10 1803 ou posterior

## <a name="new-with-mrtk-v2"></a>Novo com MRTK v2
Gostaríamos de enfatizar o nosso compromisso com essas ferramentas de plataforma.  Na verdade, aproveitamos MRTK versão 2 para desenvolver nossas experiências de caixa de entrada, como a experiência de instalação (OOBE) e o nosso aplicativo de aprendizado de realidade mista.  Você também pode esperar ver os novos recursos do HoloLens 2 expostos pela primeira vez por meio de MRTK porque acreditamos que é a melhor maneira de desenvolver em nossa plataforma. 

### <a name="modular"></a>Modular
Criamos-lo de forma modular, para que você não precise levar cada bit do Kit de ferramentas em seu projeto.  Há, na verdade, alguns benefícios para isso.  Ele mantém o tamanho do seu projeto menores, como também torna mais fácil de gerenciar.  Acima disso, porque ele foi criado com objetos passíveis de script e é controlado por interface, também é possível substituir os componentes que estão incluídos com seu próprio, para dar suporte a outros serviços, sistemas e plataformas.


### <a name="cross-platform"></a>Plataforma cruzada
Falando em outras plataformas, ele tem suporte de plataforma cruzada.  E, embora isso não significa que todas as plataformas única é suporte imediato, nós nos certificamos de que nenhum código Kit de ferramentas será interrompido quando você alternar o seu destino de compilação para outras plataformas.  A robustez e a extensibilidade com o design modular define você em um caminho bom ser capaz de dar suporte a várias plataformas, como ARCore, ARKit e OpenVR.


### <a name="performant"></a>Alto desempenho
Trabalhando com plataformas móveis, nós criamos-lo com o desempenho em mente.  Isso é muito importante, e queremos garantir que as ferramentas não vão funcionar contra você.


## <a name="see-also"></a>Consulte também
* [MRTK guia de Introdução](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Página inicial da documentação MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Instalar as ferramentas](install-the-tools.md)
* [Portabilidade de HTK/MRTK para MRTK versão 2](mrtk-porting-guide.md)

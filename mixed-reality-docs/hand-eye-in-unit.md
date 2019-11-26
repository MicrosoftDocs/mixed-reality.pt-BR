---
title: Controle de mão e de olho articulado no Unity
description: Há duas maneiras principais de agir em seu olhar no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, Unity, olhar, entrada
ms.openlocfilehash: b60c5567714893f2d1f2cc929e832bb851dd9e34
ms.sourcegitcommit: 4081dc2356fec0ea3625f1d989689cfbbb3fcf5f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203321"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Controle de mão e de olho articulado no Unity

O HoloLens 2 apresentou alguns novos recursos empolgantes: mãos articuladas e acompanhamento de olho.

A maneira mais fácil de aproveitar a nova funcionalidade no Unity é por meio do MRTK v2. Também há alguns exemplos de cenas para ajudá-lo a começar. 

* [Introdução à mão articulada no MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [Introdução ao acompanhamento de olho no MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)


## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Blocos de construção com suporte a mãos, olhos e outros no MRTK v2

O MRTK v2 fornece um conjunto de controles de interface do usuário e blocos de construção para ajudá-lo a acelerar seu desenvolvimento. 

|  [](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [botão](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) de botão de![ | ![[caixa](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) delimitadora de [caixa delimitadora](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [manipulador de manipulação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) do [manipulador de manipulação![](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Um controle de botão que dá suporte a vários métodos de entrada, incluindo a mão HoloLens2's articulada | Interface do usuário padrão para manipular objetos no espaço 3D | Script para manipular objetos com uma ou duas mãos |
|  [](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [Tablet](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html)![ | [teclado do sistema](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) de [teclado do sistema![](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![Interagir](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [interagindo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| plano de estilo 2D que dá suporte à rolagem com entrada de mão articulada | Exemplo de script de uso do teclado do sistema no Unity  | Um script para tornar os objetos interagirem com os Estados visuais e o suporte a temas |
|  [solucionador](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) de [![resolvedor](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [coleção de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) da [coleção de objetos![](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [dica](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) de ferramenta de [dica de ferramenta![](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e Magnetism de superfície | Script para dispor uma matriz de objetos em uma forma tridimensional | A interface do usuário de anotações com um sistema de âncora/dinâmico flexível que pode ser usada para rotular os controladores de movimento e o objeto. |
|  [barra de aplicativos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) da [barra de aplicativos![](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![Ponteiros](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) de [ponteiros](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) | [](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) [Visualização](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) de![de visualização de mãos |
| Interface do usuário para ativação manual da caixa delimitadora | Saiba mais sobre os vários tipos de ponteiros | A condireção Visual está no alcance que melhora a confiança da interação direta |
|  [acompanhamento de olho de![:](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) acompanhamento de olho de seleção de destino [: seleção de destino](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [acompanhamento de olho![:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) [acompanhamento de olho de navegação: navegação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [acompanhamento de olho![:](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) acompanhamento de olho do mapa de calor [: mapa de calor](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena | Saiba como rolar automaticamente o texto ou ampliar de forma fluente o conteúdo focado com base no que você está vendo| Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo |

## <a name="example-scenes"></a>Cenas de exemplo
Explore os vários tipos de interações e controles de interface do usuário do MRTK nesta [cena de exemplo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Você pode encontrar outros exemplos de cenas no [GitHub do kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity) em **assets/MixedRealityToolkit. examples/demos**Folder.

[![exemplo de cena](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>Consulte também

* [Interação ocular] (eye-gaze-interaction.md)
* [Acompanhamento ocular no HoloLens 2] (eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Controladores de movimentos](motion-controllers.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)

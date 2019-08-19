---
title: Controle de mão e de olho articulado no Unity
description: Há duas maneiras principais de agir em seu olhar no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, Unity, olhar, entrada
ms.openlocfilehash: 13016879e47b3b61eb417ce9425e48ea56c1b726
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2019
ms.locfileid: "64580885"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Controle de mão e de olho articulado no Unity

O HoloLens 2 apresentou alguns novos recursos empolgantes: mãos articuladas e acompanhamento de olho.

A maneira mais fácil de aproveitar a nova funcionalidade no Unity é por meio do MRTK v2. Também há alguns exemplos de cenas para ajudá-lo a começar. 

* [Introdução à mão articulada no MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSystem/HandTracking.html)
* [Introdução ao acompanhamento de olho no MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)


# <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Blocos de construção com suporte a mãos, olhos e outros no MRTK v2

O MRTK v2 fornece um conjunto de controles de interface do usuário e blocos de construção para ajudá-lo a acelerar seu desenvolvimento. 

|  [Botão de](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) botão [ ![](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [Caixa](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) delimitadora de caixa delimitada [ ![](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | [Manipulador de manipulação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) do manipulador de manipulação [ ![](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Um controle de botão que dá suporte a vários métodos de entrada, incluindo a mão HoloLens2's articulada | Interface do usuário padrão para manipular objetos no espaço 3D | Script para manipular objetos com uma ou duas mãos |
|  [Ardósia-](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) ardósia [ ![](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [Teclado do sistema](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) de teclado do sistema [ ![](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![Interagir](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [interagindo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| plano de estilo 2D que dá suporte à rolagem com entrada de mão articulada | Exemplo de script de uso do teclado do sistema no Unity  | Um script para tornar os objetos interagirem com os Estados visuais e o suporte a temas |
|  [Solucionador](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) de resolução [ ![](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [Coleção de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) da coleção de objetos [ ![](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [Dica de ferramenta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) ToolTip [ ![](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e Magnetism de superfície | Script para dispor uma matriz de objetos em uma forma tridimensional | A interface do usuário de anotações com um sistema de âncora/dinâmico flexível que pode ser usada para rotular os controladores de movimento e o objeto. |
|  [Barra de aplicativos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) da barra de aplicativos [ ![](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![Ponteiros](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) de [ponteiros](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) | [Visualização da](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) disposição da visualização [ ![](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| Interface do usuário para ativação manual da caixa delimitadora | Saiba mais sobre os vários tipos de ponteiros | A condireção Visual está no alcance que melhora a confiança da interação direta |
|  [![Acompanhamento de olho: Acompanhamento de](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) olho de seleção [de destino: Seleção de destino](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [![Acompanhamento de olho: Acompanhamento](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) dos olhos de navegação [: Navega](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [![Acompanhamento de olho: Acompanhamento dos](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) olhos do mapa [de calor: Mapa de calor](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena | Saiba como rolar automaticamente o texto ou ampliar de forma fluente o conteúdo focado com base no que você está vendo| Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo |

# <a name="example-scenes"></a>Cenas de exemplo
Explore os vários tipos de interações e controles de interface do usuário do MRTK nesta [cena de exemplo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html).

Você pode encontrar outros exemplos de cenas no [GitHub do kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity) em assets **/MixedRealityToolkit. examples/demos**Folder.

[![Cena de exemplo](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>Consulte também

* [Gestos](gestures.md)
* [Controladores de movimentos](motion-controllers.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)

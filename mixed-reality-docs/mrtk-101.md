---
title: MRTK 101 – como usar a Unity do kit de ferramentas da realidade misturada para interações básicas (HoloLens 2, HoloLens, realidade do Windows Mixed, Open VR)
description: Como usar a Unity do kit de ferramentas da realidade misturada para interações básicas (HoloLens 2, HoloLens, realidade do Windows Mixed, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, kit de ferramentas de realidade misturada, realidade misturada do Windows, design, aplicativo de exemplo, controles
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623504"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101: como usar a Unity do kit de ferramentas da realidade misturada para interações básicas (HoloLens 2, HoloLens, realidade do Windows Mixed, Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

Saiba mais sobre como usar o MRTK para obter alguns dos padrões comuns de interação mais amplamente usados na realidade misturada.

- Como simular interações de entrada no editor do Unity?
- Como pegar e mover um objeto?
- Como redimensionar um objeto?
- Como mover ou girar um objeto com precisão?
- Como fazer um objeto responder a eventos de entrada?
- Como adicionar comentários visuais?
- Como adicionar comentários de áudio?
- Como usar o botão de estilo do HoloLens 2 pré-fabricados?
- Como fazer um objeto seguir você?
- Como fazer um objeto lhe encarar?

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Como simular interações de entrada no editor do Unity?
O MRTK dá suporte à simulação de entrada no editor. Basta executar sua cena clicando no botão reproduzir do Unity. Use essas chaves para simular a entrada.
Pressione W, A, S, as teclas D para mover a câmera.
Mantenha o botão direito do mouse e mova o mouse para examinar.
Para exibir as mãos simuladas, pressione a barra de espaço (à direita) ou a tecla SHIFT esquerda (à esquerda) para manter as mãos simuladas na exibição, pressione T ou a tecla Y para girar as mãos simuladas, pressione Q ou E (horizontal)/R ou F (vertical)

- [Saiba mais sobre a simulação de entrada na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>Como pegar e mover um objeto?
Para tornar um objeto que seja impossibilitado, atribua estes dois scripts: ManipulationHandler.cs e NearInteractionGrabbable. cs (para captura direta com entrada de acompanhamento à mão) ManipulationHandler dá suporte a interações tanto à direita quanto à extrema. Você pode pegar e mover um objeto com a entrada de controle de mão articulada do HoloLens 2 (próximo), Hand Ray (longe), feixe do controlador de movimento (muito), cursor olhar do HoloLens & Air-TAP (longe).

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>Como redimensionar um objeto?
O ManipulationHandler.cs dá suporte à escala/rotação de duas mãos. Isso funciona com vários tipos de entrada, como entrada de mão articulada do HoloLens 2, entrada do olhar + gesto do HoloLens 1 e entrada do controlador de movimento do headset de imersão do Windows Mixed realm.

- [Saiba mais sobre o manipulador de manipulação na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>Como mover ou girar um objeto com precisão?
Atribua BoundingBox.cs a um objeto para usar a caixa delimitadora, que é a interface para dimensionar e girar um objeto. Por padrão, ele mostra os cabos e identificadores azuis do estilo do HoloLens 1. Para usar os identificadores animados com base em proximidades no estilo do HoloLens 2, você precisa atribuir pré-fabricados e materiais. Veja a [documentação da caixa delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) e a cena BoundingBoxExamples. Unity para obter os detalhes de configuração.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [Saiba mais sobre a caixa delimitadora na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>Como fazer um objeto responder a eventos de entrada?
Atribua PointerHandler.cs a um objeto. No Inspetor, você poderá usar os eventos OnPointerDown (), OnPointerUp (), OnPointerClicked (), OnPointerDragged () para usar esses eventos em um script, implementar IMixedRealityPointerHandler.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Saiba mais sobre o sistema de entrada na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>Como adicionar comentários visuais?
Atribua Interactable.cs a um objeto. No Inspetor, crie um novo tema. Usando perfis de tema de interação, você pode adicionar facilmente comentários visuais a todos os Estados de interação de entrada disponíveis.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


O interagir fornece vários tipos de temas, incluindo o tema do sombreador, que permite controlar as propriedades do sombreador por estado de interação.

- [Saiba mais sobre o interagir na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Outro bloco de construção importante para comentários visuais é o sombreador padrão MRTK. Com o sombreador MRTK Standard, você pode adicionar facilmente efeitos de comentários visuais, como luz de foco e luz de proximidade. Como o sombreador MRTK Standard executa significativamente menos cálculos do que o sombreador padrão do Unity, você pode criar uma experiência de alto desempenho.

Crie um novo material e selecione o sombreador "Mixed Reality Toolkit > Standard". Ou você pode escolher um dos materiais existentes que usam o sombreador padrão MRTK.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Saiba mais sobre o sombreador Standard MRTK na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>Como adicionar comentários de áudio?
Adicione o Áudioname a um objeto. Em seguida, nos scripts que expõem eventos de entrada (por exemplo, Interactable.cs ou PointerHandler.cs), atribua o objeto ao evento e selecione Audioname. PlayOneShot (). Você pode usar seus clipes de áudio ou escolher um dos ativos de áudio do MRTK.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>Como usar o botão de estilo do HoloLens 2 pré-fabricados?
O MRTK fornece vários tipos de botões de estilo do Shell (SO) do HoloLens 2. Ele fornece comentários visuais sofisticados, como luz de proximidade, caixa de compactação e um efeito de ondulação na superfície do botão.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

Basta arrastar e soltar um dos botões de pré-fabricado de estilo do HoloLens 2 em sua cena. O pré-fabricado usa Interactable.cs que é apresentado acima. Você pode usar eventos expostos, como OnClick (), em ações de gatilho de interação.

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Saiba mais sobre o botão pré-fabricados na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>Como fazer um objeto seguir você?
Atribua o script RadialView.cs a um objeto. Ele faz parte da série de script do Solver que permite alcançar vários tipos de posicionamento de objeto no espaço 3D. SolverHandler.cs será adicionado automaticamente.
Veja abaixo um exemplo de configuração do RadialView para obter a marca "acompanhamento lento" – ao longo do comportamento, assim como o menu iniciar no Shell do HoloLens. Você pode especificar a distância mínima/máxima e os graus de exibição mínimo/máximo. O exemplo a seguir mostra o posicionamento do objeto entre o intervalo de 0.4 m e 0,8 m dentro de 15 °. Ajuste os valores de tempo de Lerp para tornar a atualização posicional mais rápida ou mais lenta.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Saiba mais sobre os resolvedores na documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>Como fazer um objeto lhe encarar?
Atribua o script Billboard.cs a um objeto. Ele sempre vai encarar você, independentemente da sua posição. Você pode especificar a opção de eixo dinâmico.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Pronto para criar experiências incríveis para realidade misturada? Visite as páginas abaixo e saiba mais sobre MRTK e realidade misturada.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Parque Yoon Dong</b><br>@Microsoft do designer de UX</td>
</tr>
</table>

## <a name="see-also"></a>Veja também

* [Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Introdução com MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Diretrizes de portabilidade do HoloToolkit para MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

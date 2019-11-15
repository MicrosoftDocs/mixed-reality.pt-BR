---
title: Contorno e marcação
description: Os objetos com o mural sempre se orientam para enfrentar o usuário.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade misturada do Windows, mensagem de contorno
ms.openlocfilehash: 06cd1c6f67f8aa2dd94173d4089adbdbd0765211
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105718"
---
# <a name="billboarding-and-tag-along"></a>Contorno e marcação

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>O que é o mural?

A mensagem é um conceito comportamental que pode ser aplicado a objetos em realidade misturada. Os objetos com o mural sempre se orientam para enfrentar o usuário. Isso é especialmente útil com os sistemas de texto e de menu em que os objetos estáticos colocados no ambiente do usuário (bloqueado pelo mundo) seriam obscuros ou ilegíveis se um usuário fosse migrado.

Os objetos com o mural habilitado podem girar livremente no ambiente do usuário. Eles também podem ser restritos a um único eixo, dependendo das considerações de design. Lembre-se de que os objetos configurados podem recortar ou occlude-los se forem colocados muito próximos a outros objetos, ou no HoloLens, fechar as superfícies digitalizadas. Para evitar isso, pense na superfície total que um objeto pode produzir quando girado no eixo habilitado para a mensagem.

<br>

---
## <a name="what-is-a-tag-along"></a>O que é uma marca?

A marcação é um conceito comportamental que pode ser adicionado a hologramas. Um objeto de marca ao longo das tentativas de permanecer em um intervalo que permite que o usuário interaja confortavelmente.

![o painel Pins do HoloLens é um ótimo exemplo de como a tag se comporta](images/tagalong-1000px.jpg)<br>
*O menu Iniciar do HoloLens é um ótimo exemplo de comportamento de marcação*

Os objetos de marcação têm parâmetros que podem ajustar a forma com que se comportam. O conteúdo pode estar dentro ou fora da linha de visão do usuário, conforme desejado, enquanto o usuário se move em torno de seu ambiente. À medida que o usuário se move, o conteúdo tentará permanecer dentro do periferia do usuário, deslizando para a borda da exibição, dependendo da rapidez com que um usuário se move pode deixar o conteúdo temporariamente fora da exibição. Quando o usuário gazes em direção ao objeto de marca, ele é mais totalmente na exibição. Imagine que o conteúdo esteja sempre sendo "um relance" para que os usuários nunca se esqueçam em que direção seu conteúdo está.

Parâmetros adicionais podem fazer com que a marca de objeto seja anexada à cabeça do usuário por uma faixa de borracha. A aceleração ou a desaceleração proporciona peso ao objeto, fazendo com que ele fique mais fisicamente presente. Esse comportamento de mola é uma forma que ajuda o usuário a criar um modelo mental preciso de como o Tag-by funciona. O áudio ajuda a fornecer capacidades adicionais para quando os usuários têm objetos no modo de marca. O áudio deve reforçar a velocidade de movimento; uma rodada de cabeça rápida deve fornecer um efeito de som mais perceptível enquanto a movimentação em uma velocidade natural deve ter um áudio mínimo se houver algum efeito.

Assim como o conteúdo realmente bloqueado, os objetos de marca podem se comprovar de forma exagerada ou nauseating se se moverem intensamente ou se acabarem muito na exibição do usuário. Como um usuário procura e, em seguida, pára rapidamente, seus sentidos dizem que eles foram interrompidos. Seu saldo informa que sua cabeça parou de ser ativada, bem como sua visão vê o mundo parar de ligar. No entanto, se a marca ainda mantiver a movimentação quando o usuário for interrompido, ele poderá confundir seus sentidos.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtkmixed-reality-toolkit-for-unity"></a>Contorno e marcação em MRTK (Kit de ferramentas de realidade misturada) para o Unity
O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts para o comportamento de etiqueta e de contorno. Basta atribuir o script Billboard.cs a qualquer objeto para adicionar o comportamento de mensagem e fazer com que o objeto sempre fique à frente. Para adicionar o comportamento de marca, use o script RadialView.cs. Você pode ajustar várias opções, como lerping time, Distance e diploma.

* [MRTK-solucionador de exibição radial](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK-script do mural](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>Consulte também

* [Cursores](cursors.md)
* [Raio da mão](point-and-commit.md)
* [Button](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manusei](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dessa](tooltip.md)
* [Slate](slate.md)
* [Slider](slider.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetism Surface](surface-magnetism.md)

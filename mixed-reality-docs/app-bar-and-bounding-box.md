---
title: Caixa delimitadora e barra de aplicativos
description: A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realidade mista do Windows, barra de aplicativos, caixa delimitadora
ms.openlocfilehash: dab41207c2558fe8bb3fe07fca666cb2668f4e45
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723195"
---
# <a name="bounding-box-and-app-bar"></a>Caixa delimitadora e barra de aplicativos
o limite de ![é a interface padrão para manipulação de objeto em realidade misturada.](images/UX/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>O que é a caixa delimitadora?

O limite é a interface padrão para a manipulação de objetos em realidade misturada. Ele fornece ao usuário uma economia de que o objeto está ajustável no momento. No HoloLens 2, a caixa delimitadora funciona com a manipulação direta e responde à proximidade finger's do usuário. Ele mostra os comentários visuais para ajudar o usuário a perceber a distância do objeto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Dimensionando um objeto<br>
        Os cantos da caixa delimitadora informam ao usuário que o objeto pode ser dimensionado. Os identificadores seguem um padrão amplamente compreendido para ajustar a escala. Essa contratação Visual mostra aos usuários a área total do objeto – mesmo se ele não estiver visível fora de um modo de ajuste. Isso é especialmente importante porque, se não existisse, um objeto encaixado em outro objeto ou superfície pode parecer funcionar como se houvesse espaço em volta dele que não deveria estar lá.<br>
        <br>
        *Loop de vídeo: dimensionando um objeto por meio da caixa delimitadora*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![ponto de vista do HoloLens para dimensionar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Girando um objeto<br>
        Os capacidades retangulares verticais nas bordas da caixa delimitadora são indicadores de rotação. Isso dá ao usuário um ajuste mais fino sobre seus hologramas posicionados. Elas não só podem ser ajustadas e dimensionadas, mas agora giram também.<br>
        <br>
        *Loop de vídeo: girando um objeto por meio da caixa delimitadora*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![ponto de vista do HoloLens de girar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Comentário visual sobre a proximidade no HoloLens 2<br>
        No HoloLens 2, há uma indicação visual adicional que pode ajudar a percepção de profundidade do usuário. Um anel próximo a ele é exibido e escala verticalmente conforme o alcance fica mais próximo do objeto. O anel, eventualmente, convergi em um ponto quando o estado pressionado é atingido. Essa unificação Visual ajuda o usuário a entender a distância deles do objeto.<br>
        <br>
        *Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa delimitadora*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![os comentários visuais sobre a proximidade](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Para o desenvolvimento de aplicativos do Unity, consulte [a caixa delimitadora no kit de ferramentas da realidade misturada-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>O que é a barra de aplicativos?

A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma. Esse padrão geralmente é usado para fornecer aos usuários a capacidade de remover e ajustar os hologramas. A barra de aplicativos foi projetada principalmente como uma maneira de gerenciar objetos posicionados no ambiente de um usuário. Junto com a caixa delimitadora, um usuário tem controle total sobre onde e como os objetos são orientados em realidade misturada.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>A barra de aplicativos segue o usuário<br>
        Como esse padrão é usado com objetos que são protegidos pelo mundo, à medida que um usuário se move pelo objeto, a barra de aplicativos sempre será exibida no lado dos objetos mais próximo do usuário. Embora isso não seja o mural, ele efetivamente obtém o mesmo resultado; impedir que a posição de um usuário occlude ou bloqueie a funcionalidade que, de outra forma, estaria disponível em um local diferente em seu ambiente. <br>
        <br>
        *Loop de vídeo: percorrendo um holograma, a barra de aplicativos segue*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![percorrendo um holograma. A barra de aplicativos é a seguinte.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Caixa delimitadora no MRTK (Kit de ferramentas de realidade misturada) para Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e pré-fabricados para a caixa delimitadora e a barra de aplicativos. Você pode adicionar uma caixa delimitadora simplesmente atribuindo o script BoundingBox.cs em qualquer objeto.

* [MRTK-caixa delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a>Veja também

* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)

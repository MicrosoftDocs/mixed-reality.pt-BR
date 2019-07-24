---
title: Caixa delimitadora e barra de aplicativos
description: A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realidade mista do Windows, barra de aplicativos, caixa delimitadora
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829679"
---
# <a name="bounding-box-and-app-bar"></a>Caixa delimitadora e barra de aplicativos
![O limite é a interface padrão para a manipulação de objetos em realidade misturada.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>O que é a caixa delimitadora?

O limite é a interface padrão para a manipulação de objetos em realidade misturada. Ele fornece ao usuário uma economia de que o objeto está ajustável no momento. Os cantos informam ao usuário que o objeto também pode ser dimensionado. Essa contratação Visual mostra aos usuários a área total do objeto – mesmo se ele não estiver visível fora de um modo de ajuste. Isso é especialmente importante porque, se não existisse, um objeto encaixado em outro objeto ou superfície pode parecer funcionar como se houvesse espaço em volta dele que não deveria estar lá. No HoloLens 2, a caixa delimitadora funciona com a manipulação direta e responde à proximidade finger's do usuário. Ele mostra os comentários visuais para ajudar o usuário a perceber a distância do objeto. 

![Ponto de exibição do HoloLens para dimensionar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox.gif)<br>
*Dimensionando um objeto por meio da caixa delimitadora*

As alças nos cantos da caixa delimitadora seguem um padrão amplamente compreendido para ajustar a escala. 

![Ponto de exibição do HoloLens para girar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*Girando um objeto por meio da caixa delimitadora*


![Comentário visual sobre a proximidade](images/HoloLens2_Proximity.gif)<br>
*Comentários visuais com base na proximidade*

Os capacidades retangulares verticais nas bordas da caixa delimitadora são indicadores de rotação. Isso dá ao usuário um ajuste mais fino sobre seus hologramas posicionados. Elas não só podem ser ajustadas e dimensionadas, mas agora giram também.

* Para o desenvolvimento de aplicativos do Unity, consulte [a caixa delimitadora no kit de ferramentas da realidade misturada-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>O que é a barra de aplicativos?

A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma. Esse padrão geralmente é usado para fornecer aos usuários a capacidade de remover e ajustar os hologramas.

Como esse padrão é usado com objetos que são protegidos pelo mundo, à medida que um usuário se move pelo objeto, a barra de aplicativos sempre será exibida no lado dos objetos mais próximo do usuário. Embora isso não seja o mural, ele efetivamente obtém o mesmo resultado; impedir que a posição de um usuário occlude ou bloqueie a funcionalidade que, de outra forma, estaria disponível em um local diferente em seu ambiente.

![Percorrendo um holograma. A barra de aplicativos é a seguinte.](images/HoloLens2_AppBarFollowing.gif)<br>
*Percorrendo um holograma, a barra de aplicativos segue*

A barra de aplicativos foi projetada principalmente como uma maneira de gerenciar objetos posicionados no ambiente de um usuário. Junto com a caixa delimitadora, um usuário tem controle total sobre onde e como os objetos são orientados em realidade misturada.

* Para o desenvolvimento de aplicativos do Unity, consulte [barra de aplicativos no kit de ferramentas de realidade misturada – Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Consulte também
* [Objeto interativo](interactable-object.md)
* [Texto no Unity](text-in-unity.md)
* [Coleção de objetos](object-collection.md)
* [Exibindo o progresso](progress.md)

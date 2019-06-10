---
title: Barra de aplicativo e a caixa delimitadora
description: A barra de aplicativo é um menu de nível de objeto que contém uma série de botões que exibe na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, barra, caixa delimitadora de aplicativo
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813865"
---
# <a name="bounding-box-and-app-bar"></a>Delimitador de caixa e a barra de aplicativo
![A delimitação é a interface padrão para manipulação de objetos na realidade mista.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>O que é a caixa delimitadora?

A delimitação é a interface padrão para manipulação de objetos na realidade mista. Ele fornece ao usuário uma funcionalidade que o objeto está atualmente ajustável. Os cantos informar ao usuário que o objeto também pode ser dimensionado. Essa funcionalidade visual mostra os usuários a área total do objeto – mesmo se ele não é visível fora de um modo de ajuste. Isso é especialmente importante porque se ele não estava lá, um objeto ajustado para outro objeto ou superfície pode aparecer se comporte como se havia espaço ao redor dele que não deveria estar lá. Em 2 de HoloLens, a caixa delimitadora funciona com a manipulação direta de mão e responde a proximidade do dedo do usuário. Ele mostra os comentários visuais para ajudar o usuário a perceber a distância do objeto. 

![HoloLens o ponto de vista do dimensionamento de um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox.gif)<br>
*Dimensionar um objeto por meio da caixa delimitadora*

Os identificadores nos cantos da caixa delimitadora seguem um padrão amplamente entendido para ajustar a escala. 

![HoloLens o ponto de vista de girar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*Girar um objeto por meio da caixa delimitadora*


![Comentários visuais na proximidade de mão](images/HoloLens2_Proximity.gif)<br>
*Comentários visuais com base na proximidade*

As capacidades de retangulares verticais nas bordas da caixa delimitadora são indicadores de rotação. Isso fornece ao usuário mais ajuste fino sobre seus hologramas inseridas. Não apenas podem eles ajustar e dimensionar, mas agora gire também.

* Para o desenvolvimento de aplicativo do Unity, consulte [caixa delimitadora no Kit de ferramentas-Unity realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>O que é a barra de aplicativo?

A barra de aplicativo é um menu de nível de objeto que contém uma série de botões que exibe na borda inferior dos limites de um holograma. Esse padrão geralmente é usado para dar aos usuários a capacidade de remover e ajustar hologramas.

Uma vez que esse padrão é usado com objetos que são bloqueado, do mundo, conforme um usuário se move ao redor do objeto que a barra de aplicativo será sempre exibido no lado de objetos mais próximo do usuário. Embora isso não é billboarding, efetivamente alcançam o mesmo resultado; impedindo a posição para occlude ou a funcionalidade de bloco que estaria disponível de um local diferente em seu ambiente do usuário.

![Andando um holograma. Segue a barra de aplicativo.](images/HoloLens2_AppBarFollowing.gif)<br>
*Andando um holograma, segue da barra de aplicativos*

A barra de aplicativo foi desenvolvida principalmente como uma maneira de gerenciar objetos colocados em um ambiente de usuário. Juntamente com a caixa delimitadora, um usuário tem controle total sobre onde e como os objetos são orientados em realidade misturada.

* Para o desenvolvimento de aplicativo do Unity, consulte [barra de aplicativos no Kit de ferramentas-Unity realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Consulte também
* [Objeto interativo](interactable-object.md)
* [Texto no Unity](text-in-unity.md)
* [Coleção de objetos](object-collection.md)
* [Exibindo o progresso](progress.md)

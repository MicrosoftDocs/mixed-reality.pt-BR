---
title: Tabela periódica dos elementos
description: A tabela periódica dos elementos é um aplicativo de exemplo de software livre dos laboratórios de design da realidade misturada da Microsoft, em que você pode aprender a criar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, aplicativo de exemplo, controles
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525335"
---
# <a name="periodic-table-of-the-elements"></a>Tabela periódica dos elementos

>[!NOTE]
>Este artigo discute um exemplo exploratório que criamos nos laboratórios de [design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde compartilhamos nossas aprendeções e sugestões para o desenvolvimento de aplicativos de realidade misturada. Nossos artigos e códigos relacionados ao design irão evoluir à medida que fizermos novas descobertas.

[A tabela periódica dos elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) é um aplicativo de exemplo de código-fonte aberto dos laboratórios de design de realidade misturada da Microsoft. Com esse projeto, você pode aprender a formatar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma **[coleção de objetos](object-collection.md)** . Saiba também como criar objetos que respondam às entradas padrão do HoloLens. Você pode usar os componentes deste projeto para criar sua própria experiência de aplicativo de realidade misturada.

![Tabela de período do aplicativo de elementos](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>Sobre o aplicativo

A tabela periódica dos elementos visualiza os elementos químicos e cada uma de suas propriedades em um espaço 3D. Ele incorpora as interações básicas de HoloLens, como olhar e toque de ar. Os usuários podem aprender sobre os elementos com modelos 3D animados. Eles podem entender visualmente o Shell de um dos elementos do seu núcleo, que é composto de protoneladas e neutrons.

## <a name="background"></a>Informações preliminares

Depois de ter experimentado o HoloLens pela primeira vez, um aplicativo de tabela periódico foi uma ideia que eu sabia que queria experimentar em realidade misturada. Como cada elemento tem muitos pontos de dados que são exibidos com texto, pensei que seria um ótimo assunto para explorar a composição tipográfica em um espaço 3D. Ser capaz de visualizar o modelo de sem interesse do elemento foi outra parte interessante deste projeto.

## <a name="design"></a>Criar

Para a exibição padrão da tabela periódica, Imaginai caixas tridimensionais que conteriam o modelo de todos os elementos. A superfície de cada caixa seria translúcida para que o usuário pudesse obter uma ideia aproximada do volume do elemento. Com o olhar e o toque do Air, o usuário pode abrir uma exibição detalhada de cada elemento. Para fazer com que a transição entre a exibição de tabela e a exibição de detalhes seja suave e natural, eu o fiz de forma semelhante à interação física de uma abertura de caixa na vida real.

![Esboço de design](images/640px-sketch20170406.jpg)<br>
*Esboços de design*

No modo de exibição de detalhes, eu queria visualizar as informações de cada elemento com o texto renderizado linda em espaço 3D. O modelo de rede 3D animada é exibido na área central e pode ser exibido a partir de diferentes ângulos.

![Interação](images/640px-periodictable-interaction.jpg)

![Protótipos](images/640px-periodictable-prototypes.jpg)<br>
*Protótipos de interação*

O usuário pode alterar o tipo de superfície por ar tocando nos botões na parte inferior da tabela-eles podem alternar entre plano, cilindro, esfera e dispersão.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Controles e padrões comuns usados neste aplicativo

### <a name="interactable-object-button"></a>Objeto interagir (botão)

O [objeto de interação](interactable-object.md) é um objeto que pode responder às entradas básicas do HoloLens. Ele é fornecido como um pré-fabricado/script que você pode aplicar facilmente a qualquer objeto. Por exemplo, você pode fazer com que uma xícara de café em sua cena interaja e responda a entradas como olhar, toque de ar, navegação e gestos de manipulação. [Saiba mais](interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Coleção de objetos

A [coleção de objetos](object-collection.md) é um objeto que ajuda você a dispor vários objetos em várias formas. Ele dá suporte a plano, cilindro, esfera e dispersão. Você pode configurar propriedades adicionais, como RADIUS, número de linhas e espaçamento. [Saiba mais](object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

Por padrão, os hologramas serão colocados no local onde o usuário está nuvens no momento em que o aplicativo é iniciado. Às vezes, isso leva a um resultado indesejado, como os hologramas sendo colocados atrás de uma parede ou no meio de uma tabela. Um fitbox permite que um usuário use olhar para determinar o local onde o holograma será colocado. Ele é feito com uma simples textura de imagem PNG que pode ser facilmente personalizada com suas próprias imagens ou objetos 3D.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>Detalhes técnicos

Você pode encontrar scripts e pré-fabricados para a tabela periódica do aplicativo de elementos no [GitHub de laboratórios de design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="application-examples"></a>Exemplos de aplicativos

Aqui estão algumas ideias para o que você poderia criar aproveitando os componentes neste projeto.

### <a name="stock-data-visualization-app"></a>Aplicativo de visualização de dados de ações

Usando os mesmos controles e modelos de interação que a tabela periódica dos elementos de exemplo, você poderia criar um aplicativo que visualize os dados do mercado de ações. Este exemplo usa o controle de coleção de objetos para dispor dados de ações em uma forma esférica. Você pode imaginar uma exibição de detalhes em que informações adicionais sobre cada ação podem ser exibidas de forma interessante.

![Exemplo de aplicativo: Finanças (1 de 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Exemplo de aplicativo: Finanças (2 de 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![Exemplo de aplicativo: Finanças (3 de 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*Um exemplo de como a coleção de objetos usada na tabela periódica do aplicativo de exemplo de elementos pode ser usada em um aplicativo de finanças*

### <a name="sports-app"></a>Aplicativo esportivo

Este é um exemplo de visualização de dados de esportes usando a coleta de objetos e outros componentes da tabela periódica do aplicativo de exemplo de elementos.

![Exemplo de aplicativo: Esportes (1 de 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Exemplo de aplicativo: Esportes (2 de 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![Exemplo de aplicativo: Esportes (3 de 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*Um exemplo de como a coleção de objetos usada na tabela periódica dos elementos de exemplo appcould ser usada em um aplicativo esportivo*

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Parque Yoon Dong</b><br>Designer de UX@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também

* [Objeto interativo](interactable-object.md)
* [Coleção de objetos](object-collection.md)

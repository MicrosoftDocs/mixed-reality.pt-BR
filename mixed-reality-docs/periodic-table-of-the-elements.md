---
title: Tabela periódica dos elementos
description: Tabela periódica dos elementos é um aplicativo de exemplo de código-fonte aberto do laboratórios da Microsoft misto realidade Design onde você pode aprender como criar uma matriz de objetos no espaço 3D com vários tipos de superfície usando uma coleção de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, o aplicativo de exemplo, controles
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590817"
---
# <a name="periodic-table-of-the-elements"></a>Tabela periódica dos elementos

>[!NOTE]
>Este artigo descreve um exemplo de análise exploratório que criamos na [laboratórios de Design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde podemos compartilhar nossos aprendizados sobre e sugestões para desenvolvimento de aplicativos de realidade de misto. Nossos artigos relacionados ao design e código evolui à medida que fizermos novas descobertas.

[Tabela periódica dos elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) é um aplicativo de exemplo de código-fonte aberto de laboratórios de Design de realidade misturada da Microsoft. Com este projeto, você pode aprender como dispor de uma matriz de objetos no espaço 3D com vários tipos de superfície usando um  **[coleção de objetos](object-collection.md)**. Saiba também como criar objetos interagível que respondem a entradas padrão do HoloLens. Você pode usar os componentes deste projeto para criar seus próprios misto experiência de aplicativo de realidade.

![Tabela Períoda do aplicativo elementos](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>Sobre o aplicativo

Tabela periódica dos elementos visualiza os elementos químicos e cada uma de suas propriedades em um espaço 3D. Ele incorpora as interações básicas do HoloLens, como toque olhar e ar. Os usuários podem aprender sobre os elementos com modelos 3D animados. Eles possam entender visualmente shell electron de um elemento e seu núcleo - que é composto de protons e neutrons.

## <a name="background"></a>Histórico

Depois que experimentei primeiro HoloLens, um aplicativo de tabela periódica era uma ideia que eu sabia que queria fazer experiências com na realidade mista. Como cada elemento tem muitos pontos de dados que são exibidos com texto, pensei que seria ótimo no assunto para explorar tipográfica composição em um espaço 3D. Ser capaz de visualizar o modelo do elemento electron era outra parte interessante deste projeto.

## <a name="design"></a>Criar

Modo de exibição padrão da tabela periódica, imaginei caixas tridimensionais que contém o modelo do bombardeador de cada elemento. A superfície de cada caixa seria translúcida para que o usuário pode ter uma noção aproximada do volume do elemento. Com toque olhar e ar, o usuário pode abrir uma exibição detalhada de cada elemento. Para fazer a transição entre a exibição de tabela e exibição de detalhes suave e natural, eu o tornei semelhante à interação física de uma caixa de abertura na vida real.

![Esboço de design](images/640px-sketch20170406.jpg)<br>
*Esboços de design*

No modo de exibição de detalhes, eu queria visualizar as informações de cada elemento com o texto lindamente renderizado no espaço 3D. O modelo de elétrons 3D animados é exibido na área central e pode ser exibido de ângulos diferentes.

![Interação](images/640px-periodictable-interaction.jpg)

![Protótipos](images/640px-periodictable-prototypes.jpg)<br>
*Protótipos de interação*

O usuário pode alterar o tipo de superfície por via aérea tocando os botões na parte inferior da tabela - eles podem alternar entre o plano, cilindro, esfera e dispersão.

## <a name="common-controls-and-patterns-used-in-this-app"></a>Padrões usados neste aplicativo e controles comuns

### <a name="interactable-object-button"></a>Objeto interagível (botão)

[Objeto interagível](interactable-object.md) é um objeto que pode responder a entradas básicas do HoloLens. Ele é fornecido como um pré-fabricado/script que você pode aplicar facilmente a qualquer objeto. Por exemplo, você pode fazer uma xícara de café na sua cena interagível e responder a entradas como olhar, indicador e polegar, navegação e manipulação de gestos. [Saiba mais](interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>Coleção de objetos

[Coleção de objetos](object-collection.md) é um objeto que ajuda você a dispor vários objetos em diversas formas. Ele dá suporte ao plano, cilindro, esfera e dispersão. Você pode configurar propriedades adicionais, como o raio, o número de linhas e espaçamento. [Saiba mais](object-collection.md)

![Coleção de objetos](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

Por padrão, hologramas serão colocadas no local em que o usuário é Observação no momento, o aplicativo é iniciado. Às vezes, isso leva a resultados indesejados como hologramas que está sendo colocado atrás de uma parede ou no meio de uma tabela. Um fitbox permite que um usuário use olhar para determinar o local onde o holograma será colocado. Ela é feita com uma textura de imagem PNG simple que pode ser facilmente personalizada com suas próprias imagens ou objetos 3D.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>Detalhes técnicos

Você pode encontrar scripts e pré-fabricados para a tabela de atividades periódicas do aplicativo de elementos na [GitHub de laboratórios de Design de realidade mista](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).

## <a name="application-examples"></a>Exemplos de aplicativos

Aqui estão algumas ideias para o que você pode criar, aproveitando os componentes neste projeto.

### <a name="stock-data-visualization-app"></a>Aplicativo de visualização de dados de estoque

Usando os mesmos controles e o modelo de interação como a tabela periódica da amostra de elementos, você pode criar um aplicativo que visualiza dados de mercado de ações. Este exemplo usa o controle de coleta de objeto para dispor os dados de estoque em uma forma esférica. Você pode imaginar um modo de exibição de detalhes em que informações adicionais sobre cada ação poderiam ser exibidas em uma forma interessante.

![Exemplo de aplicativo: Finanças (1 de 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Exemplo de aplicativo: Finanças (2 de 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![Exemplo de aplicativo: Finanças (3 de 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*Um exemplo de como a coleção de objetos usada na tabela periódica o elementos do aplicativo de exemplo poderia ser usada em um aplicativo de finanças*

### <a name="sports-app"></a>Aplicativo de esportes

Este é um exemplo de visualização de dados de esportes, usando a coleção de objetos e outros componentes da tabela de atividades periódicas do aplicativo de exemplo de elementos.

![Exemplo de aplicativo: Esportes (1 de 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Exemplo de aplicativo: Esportes (2 de 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![Exemplo de aplicativo: Esportes (3 de 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*Um exemplo de como a coleção de objetos usados na tabela de atividades periódicas de appcould de exemplo de elementos a ser usado em um aplicativo de esportes*

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Designer de UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também

* [Objeto interagível](interactable-object.md)
* [Coleção de objetos](object-collection.md)

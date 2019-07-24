---
title: Diretrizes de design do iniciador de aplicativo 3D
description: Um iniciador de aplicativo 3D é um objeto "físico" na casa de realidade misturada do usuário que pode selecionar para iniciar um aplicativo.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, iniciador de aplicativos 3D, headset de imersão, cubo ao vivo
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517651"
---
# <a name="3d-app-launcher-design-guidance"></a>Diretrizes de design do iniciador de aplicativo 3D

Quando você coloca em um headset do Windows Mixed Reality (VR), entra na casa do Windows Mixed Reality, é visualizado como uma casa em uma Cliff cercada por montanhas e água (embora você possa [escolher outros ambientes e até mesmo criar o seu próprio](add-custom-home-environments.md)). No espaço desta página inicial, um usuário é livre para organizar e organizar os objetos 3D e os aplicativos que eles se preocupam de qualquer forma que desejarem. Um **iniciador de aplicativo 3D** é um objeto "físico" na casa de realidade misturada do usuário que pode selecionar para iniciar um aplicativo.

![Exemplo: Inicializador de aplicativo 3D de pássaro flutuante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Exemplo de inicializador de aplicativo 3D de pássaro flutuante (aplicativo fictício)*

## <a name="3d-app-launcher-creation-process"></a>processo de criação do inicializador de aplicativo 3D

Há três etapas para criar um iniciador de aplicativo 3D:
1. Design e conceito (este artigo)
2. [Modelagem e exportação](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrando-o em seu aplicativo:
    * [Aplicativos UWP](implementing-3d-app-launchers.md)
    * [Aplicativos Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Conceitos de design

### <a name="fantastic-yet-familiar"></a>Fantástico ainda familiar

O ambiente de realidade mista do Windows em que seu inicializador de aplicativo reside faz parte familiar, parte fantástica/Sci-Fi. Os melhores iniciadores seguem as regras deste mundo. Imagine como você pode pegar um objeto familiar e representativo de seu aplicativo, mas dobre algumas das regras da realidade real. A mágica será resultado.

### <a name="intuitive"></a>Simples

Ao examinar seu iniciador de aplicativo, sua finalidade-para iniciar seu aplicativo-deve ser óbvio e não deve causar qualquer confusão. Por exemplo, certifique-se de que o iniciador é um representante óbvio o suficiente do seu aplicativo que não será confundido por uma parte do décor na casa Cliff. Seu iniciador de aplicativo deve convidar pessoas para tocar/selecionar.

![Exemplo: Atualizado o iniciador do aplicativo 3D](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Observação de novo exemplo de inicializador de aplicativo 3D (aplicativo fictício)*

### <a name="home-scale"></a>Escala inicial

os iniciadores de aplicativos 3D residem na casa Cliff e seu tamanho padrão deve fazer sentido com os outros objetos "físicos" no espaço. Se você colocar seu iniciador ao lado de, digamos, uma planta de casa ou em algumas mobílias, deverá sentir em casa, com tamanho próprio. Um bom ponto de partida é ver como ele analisa 30 centímetros cúbicos, mas lembre-se de que os usuários podem escalá-los ou diminuí-los se quiserem.

### <a name="own-able"></a>Com capacidade própria

O inicializador de aplicativos deve se parecer com um objeto que uma pessoa estaria empolgando em seu espaço. Eles estarão praticamente circundando-se com essas coisas, portanto, o iniciador deve se sentir como algo que o usuário pensava o suficiente para buscar e manter o próximo.

![Exemplo: Inicializador de aplicativo 3D Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Exemplo de inicializador de aplicativo 3D Astro Warp (aplicativo fictício)*

### <a name="recognizable"></a>Reconhecível

Seu iniciador de aplicativo 3D deve expressar instantaneamente "a marca do aplicativo" para as pessoas que a veem. Se você tiver um caractere de estrela ou um objeto especialmente identificável em seu aplicativo, é recomendável usá-lo como uma grande parte do design. Em um mundo de realidade misturada, um objeto desenhará mais interesse dos usuários do que apenas um logotipo. Os objetos reconhecíveis comunicam a marca de forma rápida e clara.

### <a name="volumetric"></a>Volumétricos

Seu aplicativo merece mais do que apenas colocar seu logotipo em um plano plano e chamá-lo por dia. Seu iniciador deve parecer um objeto físico empolgante e 3D no espaço do usuário. Uma boa abordagem é imaginar que seu aplicativo terá um balão no dia de graças do Macy liderança. Pergunte-se, o que realmente seria Wow quando ele chegou à rua? O que pareceria muito com todos os ângulos de exibição?


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>Dicas para bons modelos 3D

### <a name="best-practices"></a>Práticas recomendadas
* Ao planejar dimensões para seu inicializador de aplicativo, retenha para aproximadamente um cubo 30cm. Portanto, uma proporção de tamanho de 1:1:1.
* Os modelos devem estar abaixo de 10.000 polígonos. [Saiba mais sobre contagens de triângulos e níveis de detalhes (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Teste em um headset de imersão quando possível.
* Crie detalhes na geometria do modelo quando possível – não confie em texturas para obter detalhes.
* Crie uma geometria de "água justa" fechada. Não há buracos que não são modelados no.
* Use materiais naturais em seu objeto. Imagine criá-lo no mundo real.
* Certifique-se de que seu modelo Leia bem em diferentes distâncias e tamanhos.
* Quando seu modelo estiver pronto para começar, leia as [diretrizes de exportação de ativos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modelo com detalhes sutis na textura](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modelo com detalhes sutis na textura*

### <a name="what-to-avoid"></a>O que evitar
* Não use detalhes de alto contraste ou padrões e texturas pequenos e ocupados.
* Não use a geometria fina – ela não funciona bem em uma distância e terá alias incorreto.
* Não deixe que partes do seu modelo estendam muito além da proporção de tamanho de 1:1:1. Ele criará problemas de dimensionamento.

![Evitar padrões de alto contraste e pequenos ocupados](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evitar padrões de alto contraste, pequenos e ocupados*

## <a name="how-to-handle-type"></a>Como tratar o tipo

### <a name="best-practices"></a>Práticas recomendadas
* Recomendamos que seu tipo seja composto por cerca de 1/3 de seu iniciador de aplicativo (ou mais). O tipo é o principal coisa que dá às pessoas uma ideia de que seu iniciador é, na verdade, um iniciador, portanto, é bom se ele é bastante substancial.
* Evite fazer o tipo superlargo – tente mantê-lo dentro dos limites das dimensões principais de iniciadores de aplicativo (mais ou menos).
* O tipo flat pode funcionar, mas lembre-se de que pode ser difícil de exibir alguns ângulos e em determinados ambientes. Você pode considerar colocá-lo em um objeto sólido ou fazer um pano por trás dele para ajudar com isso.
* A adição de dimensão ao seu tipo é agradável em 3D. Sombreamento dos lados do tipo uma cor diferente e mais escura pode ajudar na legibilidade.


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


**Digitar cores que funcionam**
* Branco
* Preto
* Cor semisaturada brilhante

![Digite as cores que funcionam.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Digitar cores que funcionam*

### <a name="what-to-avoid"></a>O que evitar

**Digitar cores que causam problemas**
* Tons médios
* Cinza
* Cores sobresaturadas ou cores dessaturadas

![Digite as cores que causam problemas.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Digitar cores que causam problemas*

## <a name="lighting"></a>Iluminação

A iluminação para seu inicializador de aplicativos vem do ambiente de casa da Cliff. Certifique-se de testar seu iniciador em vários lugares em toda a casa para que ele fique bom na luz e nas sombras. A boa notícia é que, se você seguiu as outras diretrizes de design deste documento, o iniciador deve estar em uma forma muito boa para a maior parte da luz na casa Cliff.

Bons lugares para testar como o iniciador analisa as várias luzes no ambiente são o estúdio, a sala de mídia, em qualquer lugar fora e na Patio de fundo (a área concreta com o gramado). Outro bom teste é colocá-lo na metade e na metade da sombra e ver como ele se parece.

![Verifique se o iniciador parece bom tanto na luz quanto nas sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Verifique se o iniciador parece bom tanto na luz quanto nas sombras*

## <a name="texturing"></a>Texturing

### <a name="authoring-your-textures"></a>Criando suas texturas

O formato final do seu iniciador de aplicativo 3D será um arquivo. glb, que é feito usando o pipeline PBR (processamento com base fisicamente). Isso pode ser um processo complicado – agora é um bom momento para empregar um artista técnico, caso ainda não tenha feito isso. Se você for um corajoso DIY, dedicar o tempo para [Pesquisar e aprender a terminologia do PBR](http://wiki.polycount.com/wiki/PBR) e o que está acontecendo nos bastidores antes de começar irá ajudá-lo a evitar erros comuns. 

![Exemplo: Novo aplicativo de anotações](images/pbr-freshnote1-640px-500px.png)<br>
*Observação de novo exemplo de inicializador de aplicativo 3D (aplicativo fictício)*

**Ferramenta de criação recomendada**

É recomendável usar a [pincel de substância](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic para criar o arquivo final. Se você não estiver familiarizado com a criação de sombreadores de PBR no pintor da substância, aqui está um [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(Alternativamente [3D-revestimento](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)ou [Marmoset Toolbag](https://www.marmoset.co/toolbag/) também funcionaria se você estivesse mais familiarizado com um deles.)

### <a name="best-practices"></a>Práticas recomendadas

* Se o objeto iniciador do aplicativo foi criado para o PBR, deve ser bem simples convertê-lo para o ambiente de casa Cliff.
* Nosso sombreador está esperando um fluxo de trabalho de metal/áspero – o sombreador do PBR inreal é um fax próximo.
* Ao exportar suas texturas, mantenha os [tamanhos de textura recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) em mente.
* Certifique-se de criar seus objetos para iluminação em tempo real – isso significa:
    * Evite sombras inclusass – ou sombras pintadas
    * Evite a iluminação inclusas nas texturas
    * Use um dos pacotes de criação de material do PBR para obter os mapas corretos gerados para nosso sombreador

## <a name="see-also"></a>Consulte também

* [Crie modelos 3D para uso na página inicial misturada de realidade](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementar inicializadores de aplicativos 3D (aplicativos UWP)](implementing-3d-app-launchers.md)
* [Implementar inicializadores de aplicativos 3D (aplicativos Win32)](implementing-3d-app-launchers-win32.md)

---
title: Diretrizes de design de iniciador do aplicativo 3D
description: Um inicializador de aplicativos 3D é um objeto "físico" casa de realidade mista do usuário que eles podem selecionar para iniciar um aplicativo.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, o iniciador do aplicativo 3D, fone de ouvido imersivo, live cubo
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589282"
---
# <a name="3d-app-launcher-design-guidance"></a>Diretrizes de design de iniciador do aplicativo 3D

Quando você coloca em um headset do Windows Mixed Reality imersivo (VR), insira o Windows Mixed Reality doméstica, visualizados como a Paciência com um precipício cercada por Montanhas e água (embora você possa [escolher outros ambientes e até mesmo criar seu próprio](add-custom-home-environments.md)). Página inicial, dentro do espaço do que isso um usuário é livre para organizar os objetos 3D e os aplicativos que ele está preocupado quando desejado. Um **inicializador de aplicativos 3D** é um objeto "físico" o usuário do misto casa realidade que eles podem selecionar para iniciar um aplicativo.

![Exemplo: Iniciador de aplicativos 3D de pássaro flutuante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Exemplo de iniciador de aplicativo 3D de pássaro flutuante (aplicativo fictício)*

## <a name="3d-app-launcher-creation-process"></a>Processo de criação de iniciador do aplicativo 3D

Há 3 etapas para criar um inicializador de aplicativos 3D:
1. Criando e concepting (Este artigo)
2. [Modelagem e exportando](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integração ao seu aplicativo:
    * [Aplicativos UWP](implementing-3d-app-launchers.md)
    * [Aplicativos do Win32](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Conceitos de design

### <a name="fantastic-yet-familiar"></a>Fantástico ainda familiar

O ambiente do Windows Mixed Reality que seu iniciador do aplicativo reside no é parte familiar, parte maço de folhas/sci-fi. Os iniciadores melhor seguem as regras esse mundo. Pense como você pode tirar um objeto familiar e representativo do seu aplicativo, mas curvar algumas das regras de realidade real. Resultará mágica.

### <a name="intuitive"></a>Intuitivo

Quando você examinar seu inicializador de aplicativos, sua finalidade - o para iniciar seu aplicativo - deve ser óbvia e não deve causar confusão. Por exemplo, certifique-se de que o iniciador é um representante óbvio o suficiente do seu aplicativo que não será confundido para uma parte da decoração no Cliff House. O inicializador de aplicativos deve convidar pessoas touch/selecioná-lo.

![Exemplo: Iniciador de aplicativo 3D novo Observação](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Exemplo de iniciador de aplicativo 3D de Observação atualizado (aplicativo fictício)*

### <a name="home-scale"></a>Dimensionamento inicial

Inicializadores de aplicativos 3D ao vivo no Cliff House e seu tamanho padrão deve fazer sentido com os outros objetos "físicos" no espaço. Se você colocar seu inicializador ao lado, digamos, uma fábrica de casa ou alguma móveis, ele deve se sentir em casa, size-wise. É um bom ponto de partida ver a aparência dele em centímetros cúbicos 30, mas lembre-se de que os usuários podem escalá-lo para cima ou para baixo se desejarem.

### <a name="own-able"></a>Capaz de proprietário

O iniciador do aplicativo deve se sentir como um objeto de uma pessoa seria entusiasmada por ter em seu espaço. Eles vai ser praticamente ao redor em si com essas coisas, para que o iniciador deve se sentir como algo que o pensamento do usuário era desejável para buscar e mantenha próximos.

![Exemplo: Iniciador do aplicativo 3D astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Exemplo de iniciador de aplicativo 3D astro Warp (aplicativo fictício)*

### <a name="recognizable"></a>Reconhecível

Seu inicializador de aplicativos 3D instantaneamente deva expressar a "marca do aplicativo" para as pessoas que vê-lo. Se você tiver um caractere de estrela ou um objeto especialmente identificável em seu aplicativo, é recomendável usá-la como uma grande parte do seu design. Em um mundo de realidade misturada, um objeto desenhará mais interesse dos usuários que apenas um logotipo sozinho. Objetos reconhecíveis se comunicar da marca de maneira rápida e clara.

### <a name="volumetric"></a>Volumétricas

Seu aplicativo merece mais do que apenas colocando seu logotipo em um plano simples e encerrando o expediente. O iniciador deve parecer como um objeto interessante, 3D e físico no espaço do usuário. Uma boa abordagem é imaginar o que seu aplicativo iria ter um balão em vez de dia de ação de Graças de Macy. Se perguntar o que seria realmente o wow pessoas como vieram da rua de baixo? O que seria ótimo de todos os ângulos de exibição?


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


## <a name="tips-for-good-3d-models"></a>Dicas de bons modelos 3D

### <a name="best-practices"></a>Práticas recomendadas
* Ao planejar dimensões para seu iniciador do aplicativo, envie-o para aproximadamente um cubo de 30cm. Portanto, um 1: proporção de tamanho de 1:1.
* Modelos devem ser menos de 10.000 polígonos. [Saiba mais sobre níveis de detalhes (LODs) e contagens de triângulo](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Teste em um fone de ouvido imersivo quando possível.
* Detalhes da compilação na geometria do seu modelo sempre que possível – não dependem de texturas para obter detalhes.
* Geometria "água apertados" fechada de compilação. Não há buracos que não são modelados no.
* Use materiais naturais em seu objeto. Imagine criá-lo no mundo real.
* Verifique se que seu modelo lê bem nesse tamanho e a distância diferente.
* Quando o modelo estiver pronto para começar, leia as [exportando diretrizes ativos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modelo com detalhes sutis na textura](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modelo com detalhes sutis na textura*

### <a name="what-to-avoid"></a>O que evitar
* Não use os detalhes de alto contraste ou padrões de pequenos, ocupados e texturas.
* Não use geometria thin – ele não funcionar bem em uma distância e alias incorretamente.
* Não deixe que partes do seu modelo estender muito além de 1: proporção de tamanho de 1:1. Ele cria problemas de dimensionamento.

![Evite padrões ocupados pequenas, de alto contraste](images/20171013-143603-mixedreality-640px.jpg)<br>
*Evite padrões de alto contraste, pequeno, ocupados*

## <a name="how-to-handle-type"></a>Como lidar com tipo

### <a name="best-practices"></a>Práticas recomendadas
* É recomendável que seu tipo consiste em cerca de 1/3 do seu inicializador de aplicativos (ou mais). Tipo é a coisa principal que dá uma ideia que o iniciador é, na verdade, um inicializador, portanto, é bom se ele é bastante significativo de pessoas.
* Evite fazer tipo super amplo – tente mantê-lo dentro dos limites de iniciadores de aplicativo dimensões do core (mais ou menos).
* Tipo simples pode funcionar, mas lembre-se de que ele pode ser difícil de ler de determinados ângulos e em determinados ambientes. Você pode considerar a colocação de um objeto sólido ou pano de fundo atrás dele para ajudar com isso.
* Adicionar dimensão ao seu tipo parece bom em 3D. Sombreamento os lados do tipo de uma cor mais escura diferente pode ajudar a legibilidade.


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


**Cores de tipo que funcionam**
* Branco
* Preto
* Cor semisaturado brilhante

![Tipo de cores que funcionam.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Cores de tipo que funcionam*

### <a name="what-to-avoid"></a>O que evitar

**Cores de tipo que causam problemas**
* Mid tons
* Cinza
* Cores em excesso saturadas ou sem saturação de cores

![Tipo de cores que causam problemas.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Cores de tipo que causam problemas*

## <a name="lighting"></a>Iluminação

A iluminação seu iniciador do aplicativo é proveniente do ambiente Cliff House. Certifique-se de testar seu inicializador em vários locais em toda a casa para que fique BOM na luz e sombras. A boa notícia é que se você seguiu as outras diretrizes de design neste documento, o iniciador deve ser em boa forma para a maioria dos iluminação no Cliff House.

Bons locais para a aparência do seu iniciador no várias luzes no ambiente de teste são o Studio, a sala de mídia, em qualquer lugar fora e no volta quintal (a área com o jardim concreta). Outro bom teste é colocá-lo na metade de luz e sombra metade e ver sua aparência.

![Certifique-se de que seu inicializador ficou BOM na luz e sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Certifique-se de que seu inicializador ficou BOM na luz e sombras*

## <a name="texturing"></a>Texturização

### <a name="authoring-your-textures"></a>As texturas de criação

O formato de final de seu inicializador de aplicativos 3D será um arquivo de .glb, que é feito usando o pipeline PBR (fisicamente com base em renderização). Isso pode ser um processo complicado - agora é um bom momento para empregar um artista técnico se você ainda não fez isso. Se você for um corajoso DIY faça você mesmo-er, pena [pesquisar e aprenda a terminologia PBR](http://wiki.polycount.com/wiki/PBR) e o que está acontecendo nos bastidores, antes de começar o ajudará a evitar erros comuns. 

![Exemplo: Observação de novo aplicativo](images/pbr-freshnote1-640px-500px.png)<br>
*Exemplo de iniciador de aplicativo 3D de Observação atualizado (aplicativo fictício)*

**Ferramenta de criação recomendada**

É recomendável usar [substância pintor](https://www.allegorithmic.com/products/substance-painter) por Allegorithmic para criar o arquivo final. Se você não estiver familiarizado com a criação de sombreadores PBR substância, aqui de pincel uma [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(Alternativamente [3D Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), ou [Marmoset Toolbag](https://www.marmoset.co/toolbag/) também funcionaria se você estiver familiarizado com uma destas opções.)

### <a name="best-practices"></a>Práticas recomendadas

* Se seu objeto iniciador de aplicativo foi criado para PBR, ele deve ser bem simples para convertê-lo para o ambiente Cliff House.
* Nosso sombreador está esperando um fluxo de trabalho do sistema operacional/Aspereza – sombreador PBR Unreal o é um fax fechar.
* Ao exportar as texturas manter o [textura tamanhos recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) em mente.
* Certifique-se de criar objetos de iluminação em tempo real — isso significa que:
    * Evite sombras assadas – ou sombras pintadas
    * Evite assada iluminação em texturas
    * Usar um do material PBR criação de pacotes para instalar os mapas direita gerados para nosso sombreador

## <a name="see-also"></a>Consulte também

* [Criar modelos 3D para uso na realidade misturada inicial](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementar iniciadores de aplicativo 3D (aplicativos UWP)](implementing-3d-app-launchers.md)
* [Implementar iniciadores de aplicativo 3D (aplicativos Win32)](implementing-3d-app-launchers-win32.md)

---
title: Sobre estas diretrizes de design
description: Essa orientação foi criada pelos designers, desenvolvedores, gerentes de programa e pesquisadores da Microsoft, cujo trabalho abrange dispositivos holográficos (como o HoloLens) e dispositivos imersivos (como os headsets Windows Mixed Reality da Acer e da HP).
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, introdução, orientação
ms.openlocfilehash: fd2b8d704c9053d9eeb63ab2cceca1e4257d86ed
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437100"
---
# <a name="about-this-design-guidance"></a>Sobre estas diretrizes de design

## <a name="introduction"></a>Introdução

**Olá, e bem-vindo às suas diretrizes de design para realidade misturada.**

Essas diretrizes são criadas pelos designers, desenvolvedores, gerentes de programa e pesquisadores da Microsoft, cujo trabalho abrange dispositivos Holographic, como os dispositivos HoloLens e imersiva, como o Acer e o HP Windows Mixed realness headsets. Considere este trabalho como um conjunto de tópicos sobre como projetar para os monitores montados no cabeçalho do Windows.

Com você, estamos inserindo uma nova era imensamente empolgante de computação. As inovações em telas com montagem de cabeça, som espacial, sensores, conscientização ambiental, entrada e gráficos 3D nos levam e nos desafiamos a definir novos tipos de experiências – uma nova fronteira drasticamente mais pessoal, intuitiva, imersiva e contextual.

Sempre que possível, ofereceremos diretrizes de design acionáveis com o código relacionado no GitHub. Dito isso, como estamos aprendendo bem junto com você, nem sempre será capaz de oferecer orientações específicas e acionáveis aqui. Parte do que compartilharemos será o espírito de "lições que aprendemos" e "evitará reduzir esse caminho".

E sabemos, muitas inovações serão geradas pela comunidade de design maior. Então, esperamos ouvir você, aprender com você e trabalhar junto com você. Para nossa parte, faremos o nosso melhor para compartilhar nossas ideias, mesmo que elas sejam exploratórios e no início da intenção de capacitar desenvolvedores e designers com raciocínio de design, práticas recomendadas e controles de software livre relacionados, padrões e aplicativos de exemplo que você pode usar diretamente em seu próprio trabalho.

## <a name="overview"></a>Visão geral

Aqui está uma rápida visão geral de como essas diretrizes de design são organizadas. 
* **[Visão geral](design.md)** -saiba mais sobre o processo de design, os principais conceitos e fatores de interação a serem considerados.
* **[Conceitos principais](core-concepts-landingpage.md)** -saiba mais sobre o conforto, o quadro Holographic, o mapeamento espacial e outros conceitos principais a serem considerados.
* **[Modelos de interação](interaction-fundamentals.md)** – estas diretrizes são estruturadas em três modelos principais de interação.
* **[Elementos de UX](app-patterns-landingpage.md)** – use controles e comportamentos como blocos de construção para criar sua própria experiência de aplicativo.
* **[Recursos](design.md#choose-a-prototyping-option)** -Inicie seu projeto com as ferramentas de design e as opções de protótipo.

Para todos os itens acima, visamos fornecer a combinação certa de texto, ilustrações e diagramas, e vídeos, para que você nos veja experimentando diferentes formatos e técnicas, tudo com a intenção de fornecer o que você precisa. E, nos meses de antecedência, expandiremos essa taxonomia para incluir um conjunto mais amplo de tópicos de design. Sempre que possível, daremos um cara sobre o que está chegando em seguida, portanto, continue verificando novamente.

## <a name="objectives"></a>Objetivos

Veja aqui uma rápida visão geral de alguns objetivos de alto nível que estão orientando esse trabalho para que você possa entender de onde estão vindo

### <a name="help-solve-customer-challenges"></a>Ajudar a resolver os desafios do cliente

![Ajudar a resolver os desafios do cliente](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Nós rodar com muitos dos mesmos problemas que você faz e entendemos o nível de desafio do seu trabalho. É empolgante explorar e definir uma nova fronteira... e também pode ser assustador. Os paradigmas e as práticas anteriores precisam ser repensados; Os clientes precisam de novas experiências; e há muito potencial para inovação. Considerando que queremos que esse trabalho seja o mais abrangente possível, indo além de um guia de estilo. Nós visamos fornecer um conjunto abrangente de diretrizes de design que abordam a interação de realidade misturada, comandos, navegação, entrada e estilo – tudo com base em comportamentos e cenários humanos. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Aponte o caminho para uma maneira nova e mais humana de calcular

![Aponte o caminho para uma maneira nova e mais humana de calcular](images/500px-man-and-women-with-holograph-on-table.png)<br>

Embora seja importante concentrar-se em problemas específicos do cliente, também queremos nos levar além disso e fornecer mais. Acreditamos que o bom design não é "apenas" solução de problemas, mas também uma maneira de ativar a evolução humana de forma significativa. Novas maneiras de comportamento humano; novas maneiras de pessoas relacionadas a si mesmas, suas atividades e seus ambientes; novas maneiras de ver nosso mundo... Queremos que nossas diretrizes reflitam todas essas maneiras mais aspiraçãos de pensar também. 

### <a name="meet-creators-where-they-are"></a>Conheça os criadores onde eles estão

![Conheça os criadores onde eles estão](images/500px-creators.jpg) <br>

Esperamos que muitos públicos descubram essas diretrizes para serem úteis. Você tem conjuntos de habilidades diferentes (começando, intermediários, avançados), usam ferramentas diferentes (Unity, DirectX C++, C#,, outros), estão familiarizados com várias plataformas (Windows, Ios, Android), provenientes de diferentes planos de fundo (dispositivos móveis, empresariais e jogos ) e estão trabalhando em equipes de tamanho diferente (solo, pequena, média, grande). Portanto, essas diretrizes podem ser exibidas com perspectivas e necessidades diferentes. Sempre que possível, tentaremos manter essa diversidade em mente e tornar nossas diretrizes o mais relevantes possível para o máximo possível de pessoas. Além disso, sabemos que muitos de vocês já estão no GitHub. Portanto, Vincularemos diretamente a repositórios e fóruns do GitHub para que você se encontre onde você já está. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Compartilhe o máximo possível, de experimental a explícito

![Compartilhe o máximo possível, de experimental a explícito](images/500px-man-playinggame.jpg) <br>

Um dos desafios de oferecer diretrizes de design nesse novo 3D medido é que nem sempre temos orientação definitiva para oferecer. Assim como você, estamos aprendendo, experimentando, criando protótipos, resolvendo problemas e ajustando à medida que pressionamos obstáculos. Em vez de esperar por algum tempo mítico no futuro quando todos descobrimos, visamos compartilhar nosso pensamento em tempo real, mesmo se não for conclusivo. É claro que nosso objetivo final é defini-lo sempre que pudermos, fornecendo diretrizes de design claras e flexíveis vinculadas a código-fonte aberto e acionável em ferramentas de desenvolvimento e design da Microsoft. Mas chegar a esse ponto leva muitos arredondamentos de iteração e aprendizado. Queremos entrar em contato com você e aprender com você, ao longo do caminho. Com tudo isso em mente, faremos o melhor para compartilhar enquanto vamos, mesmo com nossas coisas experimentais. 

### <a name="the-right-balance-of-global-and-local-design"></a>O equilíbrio certo entre design global e local

![O equilíbrio certo entre design global e local](images/500px-fluentdesign.jpg) <br>

Ofereceremos dois níveis de diretrizes de design: global e local. Nossas diretrizes de design ' globais ' estão incorporadas ao [sistema de design fluente](https://fluent.microsoft.com). Detalhes fluentes de como achamos sobre conceitos básicos como luz, profundidade, movimento, material e escala em todo o design da Microsoft – nossos dispositivos, produtos, ferramentas e serviços. Dito isso, existem diferenças significativas específicas do dispositivo em um sistema maior. Portanto, nossas diretrizes de design "locais" para os monitores montados na cabeça descrevem o design de dispositivos Holographic e imersiva que geralmente têm diferentes métodos de entrada e saída, bem como diferentes necessidades e cenários de usuários. As diretrizes de design local abordam os tópicos exclusivos do HMDs. Por exemplo: ambientes e objetos 3D; ambientes compartilhados; o uso de sensores, controle de olho e mapeamento espacial; e as oportunidades de áudio espacial. Em nossas diretrizes, você provavelmente verá que nos vemos com esses aspectos globais e locais. Espero que isso o ajudará a aumentar seu trabalho em uma base maior de design, aproveitando as diferenças de design entre dispositivos específicos.

### <a name="have-a-discussion"></a>Ter uma discussão

![Ter uma discussão](images/500px-share.jpg) <br>

Talvez o mais importante, queremos nos envolver com você, a comunidade de designers holographics e de imersão e desenvolvedores, a fim de definir essa nova era empolgante de design. Como mencionado acima, sabemos que não temos todas as respostas. É por isso que acreditamos que muitas soluções e inovações empolgantes serão fornecidas por você. Nós visamos ser abertos e disponíveis para ouvi-los e discutir com você online e em eventos e agregar valor sempre que pudermos. Estamos empolgados para fazer parte dessa comunidade de design incrível, embarcando em uma aventura em conjunto. 

## <a name="please-dive-in"></a>Mergulhe em

Esperamos que este artigo introdutório forneça algum contexto significativo à medida que você explorar nossas diretrizes de design. Vamos nos aprofundar e nos informar suas ideias nos fóruns do GitHub que você encontrará vinculados em nossos artigos ou no design da Microsoft no [Twitter](https://twitter.com/MicrosoftDesign) e no [Facebook](https://www.facebook.com/microsoftdesign/). Vamos projetar o futuro juntos!

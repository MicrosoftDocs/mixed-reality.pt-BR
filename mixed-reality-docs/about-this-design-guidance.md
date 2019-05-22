---
title: Sobre este guia de design
description: Essa orientação é criada pela Microsoft designers, desenvolvedores, gerentes de programa e pesquisadores, cujo trabalho abrange holográfico dispositivos (como HoloLens) e imersivos dispositivos (como headsets Acer e HP Windows Mixed Reality).
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, introdução, diretrizes
ms.openlocfilehash: ca69118dfeb766c1386420cd81053b9acb485ba7
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974853"
---
# <a name="about-this-design-guidance"></a>Sobre este guia de design

## <a name="introduction"></a>Introdução

**Olá, bem-vindo para suas diretrizes de design para realidade misturada.**

Essa orientação é criada pela Microsoft designers, desenvolvedores, gerentes de programa e pesquisadores, cujo trabalho abrange holográfico dispositivos (como HoloLens) e imersivos dispositivos (como headsets Acer e HP Windows Mixed Reality). Portanto, considere esse trabalho como um conjunto de tópicos 'como projetar para monitores de fone de ouvido do Windows'.

Com você, podemos inserir uma nova era bastante interessante de computação. As inovações em head montado exibe, som espacial, sensores, consciência ambiental, de entrada, e elementos gráficos 3D nos levam e desafiá-us, definir novos tipos de experiências de... uma nova fronteira é consideravelmente mais pessoal, intuitiva, envolventes e contextuais.

Sempre que possível, oferecemos orientações de design acionáveis, com o código relacionado no GitHub. Dito isso, como aprendemos direita junto com você, podemos sempre não será capazes de oferecer diretrizes específicas e acionáveis aqui. Algumas das quais podemos compartilhar será no espírito do 'lições que aprendemos' e 'evitar aquele caminho'.

E sabemos que muitas inovações serão geradas pela maior comunidade de design, portanto, estamos ansiosos para ouvir de você, aprendendo com você e trabalhar em conjunto com você. Para nossa parte, faremos nosso melhor para compartilhar nosso análises, mesmo que eles sejam exploratórios e no início, com a intenção de capacitando os desenvolvedores e designers ao pensamento do design, práticas recomendadas e relacionado abre controles de fonte, padrões e aplicativos de exemplo que você pode usar diretamente em seu próprio trabalho.

## <a name="overview"></a>Visão geral

Aqui está uma visão geral de como essas diretrizes de design é organizado. Você encontrará seções para cada uma dessas áreas, com links para vários artigos.
* **[Introdução ao design](mixed-reality.md)**  - leia nossos pensamentos de alto nível e entender os princípios que seguimos.
* **[Interações instinctual](interaction-fundamentals.md)**  -Saiba mais sobre a entrada, comandando, navegação e outros conceitos básicos de interação para a criação de seus aplicativos.
* **[Estilo](typography.md)**  -tornar seu aplicativo e interessantes, usando a cor, a tipografia e movimento.
* **[Padrões de aplicativo](types-of-mixed-reality-apps.md)**  -Saiba como aplicativos podem abranger cenários em ambientes imersivos e reais.
* **[Controles](interactable-object.md)**  -usar controles e padrões, como a experiência de blocos de construção para criar seu próprio aplicativo.
* **[Aplicativos de exemplo](design.md#sample-apps)**  -criar grandes experiências de exemplos projetado e criado pela nossa equipe.
* **[Ferramentas e recursos de design](design.md#design-tools)**  -iniciar rapidamente seu projeto com modelos de design e ferramentas.

Para todos os itens acima, nosso objetivo é oferecer a combinação certa de texto, ilustrações e diagramas e vídeos, você verá nos experimentar diferentes formatos e técnicas, tudo isso com a intenção de oferecer o que você precisa. E nos meses futuros, expandiremos esta taxonomia para incluir um conjunto mais amplo de tópicos de design. Sempre que possível, que daremos a você uma alerta sobre o que está por vir, portanto, mantenha a verificação de volta.

## <a name="objectives"></a>Objetivos

Aqui está uma rápida olhada alguns objetivos de alto nível que estão orientando esse trabalho para que você possa entender onde estamos vindo da:

### <a name="help-solve-customer-challenges"></a>Ajudar a resolver os desafios do cliente

![Ajudar a resolver os desafios do cliente](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Podemos resolver muitos dos mesmos problemas que você faz, e sabemos que seu trabalho como um desafio é. É interessante explorar e definir uma nova fronteira... e também pode ser desanimador. Práticas recomendadas e desses paradigmas antigos precisam ser considerado novamente; cliente necessidade de novas experiências; e há muito potencial para a inovação. Considerando que queremos que esse trabalho para ser abrangente quanto for possível, movendo bem além de um guia de estilo. Nosso objetivo é fornecer um conjunto abrangente de diretrizes de design que abrange misturadas interação realidade, comandando, navegação, entrada e estilo – tudo com base em cenários e o comportamento humano. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Aponte o sentido de uma maneira nova e mais humano da computação

![Aponte o sentido de uma maneira nova e mais humano da computação](images/500px-man-and-women-with-holograph-on-table.png)<br>

Embora seja importante para se concentrar em problemas específicos do cliente, também queremos que enviar por push sozinhos pensar além disso e para oferecer maior. Acreditamos que ótimo design não é "just" solução de problemas, mas também uma maneira de ativar significativamente evolução humana. Novas maneiras de comportamento humano. novas maneiras de pessoas relacionadas a mesmos, suas atividades e seus ambientes; novas maneiras de ver nosso mundo... queremos que nossas diretrizes para refletir todas as essas maneiras mais ambiciosos de pensar muito. 

### <a name="meet-creators-where-they-are"></a>Atender aos criadores de onde eles estão

![Atender aos criadores de onde eles estão](images/500px-creators.jpg) <br>

Esperamos que muitos públicos encontrar esta diretriz para ser útil. Você tem diferentes conjuntos de habilidades (começando, intermediário, Avançado), usam ferramentas diferentes (Unity, DirectX, C++, C#, outros), estão familiarizados com várias plataformas (Windows, iOS, Android), provenientes de diferentes planos de fundo (mobile, enterprise, jogos ) e estamos trabalhando nas equipes de tamanho diferente (solo, pequeno, médio, grande). Portanto, neste guia será exibido com as necessidades e perspectivas diferentes. Sempre que possível, tentaremos manter essa diversidade em mente e tornar nossa orientação tão relevante quanto possível para muitas pessoas quanto possível. Além disso, nós sabemos que muitos de vocês já estão no GitHub, portanto, vamos vincular diretamente para repositórios do GitHub e fóruns para atender a você onde já estão. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Compartilhar um tanto quanto possível, de experimental para explícita

![Compartilhar um tanto quanto possível, de experimental para explícita](images/500px-man-playinggame.jpg) <br>

Um dos desafios da oferta de diretrizes de design nesse novo meio 3D é que nem sempre temos de orientação propriamente dita a oferecer. Assim como você, aprendemos, testar, criação de protótipos, solução de problemas e ajustar e como atingimos obstáculos. Em vez de esperar por algum momento futuro mítico quando tivermos ele descobriu, nosso objetivo compartilhar nosso pensamento com você em tempo real, mesmo se ele não é conclusivo. É claro, nossa meta final é ser definitivo, sempre que possível, fornecendo diretrizes de design flexível, claro, vinculado ao código-fonte aberto e acionáveis em ferramentas de desenvolvimento e design da Microsoft. Mas Introdução a esse ponto leva a muitas rodadas de iteração e aprendizado. Queremos entre em contato com você e aprenda com você, ao longo do caminho, portanto, podemos realizar a melhor forma possível para compartilhar à medida que avançarmos, até mesmo nossos materiais de experimental. 

### <a name="the-right-balance-of-global-and-local-design"></a>O equilíbrio correto de design global e local

![O equilíbrio correto de design global e local](images/500px-fluentdesign.jpg) <br>

Iremos oferecer dois níveis de diretrizes de design: global e local. Nossas diretrizes de design 'global' é incorporada na [Fluent Design System](http://fluent.microsoft.com). Detalhes do Fluent como pensamos sobre conceitos básicos de como a luz, profundidade, movimento, material e escala em todos os Microsoft design – nossos dispositivos, produtos, ferramentas e serviços. Que existem diferenças de específicos do dispositivo do dito isso, significativas todo esse sistema maior, para que nossa 'local' diretrizes de design para controlava head descreverá projetar para dispositivos holográfico e de imersão que geralmente têm métodos de saída e entrada diferentes e cenários e diferentes necessidades dos usuários. Então, as diretrizes de design de local aborda tópicos exclusivos para HMDs, por exemplo 3D ambientes e objetos; ambientes compartilhados; o uso de sensores, acompanhamento de olho e mapeamento espacial; e as oportunidades de áudio espacial. Em toda a nossa orientação você provavelmente verá-nos se referir a essas global e os aspectos de locais, e espero que isso o ajudará a Terra seu trabalho em uma base maior de design, aproveitando as diferenças de design de dispositivos específicos.

### <a name="have-a-discussion"></a>Ter uma discussão

![Ter uma discussão](images/500px-share.jpg) <br>

Talvez mais importante, queremos entre em contato com você, a comunidade de holográfica e imersivos designers e desenvolvedores, para definir nesta nova era interessante de design. Conforme mencionado acima, nós sabemos que não temos todas as respostas e acreditamos que muitas soluções empolgantes e inovações serão provenientes de você. Temos o objetivo de ser aberta e disponível para ouvi-los e discutir com você, online e em eventos e adicione o valor sempre que possível. Estamos muito animados para sermos uma parte desta comunidade incrível de design, embarcar em uma aventura juntos. 

## <a name="please-dive-in"></a>Aprofunde-se

Esperamos que este artigo de boas-vindo fornece algum contexto significativo conforme você explora nossas diretrizes de design. Aprofunde-se e informe-nos seus comentários nos fóruns do GitHub você encontrará dados vinculados em nossos artigos, ou ao Design da Microsoft em [Twitter](https://twitter.com/MicrosoftDesign) e [Facebook](https://www.facebook.com/microsoftdesign/). Vamos conjunta projetar o futuro juntos!

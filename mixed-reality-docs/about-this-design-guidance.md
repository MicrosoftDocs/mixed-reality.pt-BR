---
title: Sobre este guia de design
description: Essa orientação foi criada pelos designers, desenvolvedores, gerentes de programa e pesquisadores da Microsoft, cujo trabalho abrange dispositivos holográficos (como o HoloLens) e dispositivos imersivos (como os headsets Windows Mixed Reality da Acer e da HP).
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, introdução, diretrizes
ms.openlocfilehash: 0e5601898c2b1f351b5ab2aaa491a7c64ae57f7e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414158"
---
# <a name="about-this-design-guidance"></a>Sobre este guia de design

## <a name="introduction"></a>Introdução

**Olá, bem-vindo para suas diretrizes de design para realidade misturada.**

Essa orientação é de autoria de designers, desenvolvedores, gerentes de programa e pesquisadores, cujo trabalho abrange holográfico dispositivos, como o HoloLens e dispositivos imersivos, como fones de ouvido Acer e HP Windows Mixed Reality Microsoft. Considere esse trabalho como um conjunto de tópicos sobre como projetar para monitores de fone de ouvido do Windows.

Com você, podemos inserir uma nova era bastante interessante de computação. As inovações em controlava head, som espacial, sensores, consciência ambiental, elementos gráficos 3D e entrados nos levam e desafiá-us, definir novos tipos de experiências – uma nova fronteira drasticamente mais pessoal, intuitiva, envolvente e contextual.

Sempre que possível, oferecemos orientações de design acionáveis com o código relacionado no GitHub. Dito isso, como aprendemos direita junto com você, podemos sempre não será capazes de oferecer diretrizes específicas e acionáveis aqui. Algumas das quais podemos compartilhar será no espírito do 'lições que aprendemos' e 'evitar aquele caminho'.

E nós sabemos, muitas inovações serão geradas pela maior comunidade de design. Portanto, estamos ansiosos para ouvir de você, aprendendo com você e trabalhar em conjunto com você. Para nossa parte, faremos nosso melhor para compartilhar nosso análises, mesmo se eles estiverem exploratório e antecipado com a intenção de capacitando os desenvolvedores e designers com pensamento do design, práticas recomendadas e os controles relacionados de software livre, padrões e aplicativos de exemplo que você pode usar diretamente em seu próprio trabalho.

## <a name="overview"></a>Visão geral

Aqui está uma visão geral de como essas diretrizes de design é organizado. Você encontrará seções para cada uma dessas áreas com links para vários artigos.
* **[Introdução ao design](mixed-reality.md)**  - leia nossos pensamentos de alto nível e entender os princípios que seguimos.
* **[Interações instinctual](interaction-fundamentals.md)**  -Saiba mais sobre a entrada, comandando, navegação e outros conceitos básicos de interação para a criação de seus aplicativos.
* **[Estilo](typography.md)**  -tornar seu aplicativo e interessantes, usando a cor, a tipografia e movimento.
* **[Padrões de aplicativo](types-of-mixed-reality-apps.md)**  -Saiba como aplicativos podem abranger cenários em ambientes imersivos e reais.
* **[Controles](interactable-object.md)**  -usar controles e padrões como blocos de construção para criar sua própria experiência de aplicativo.
* **[Aplicativos de exemplo](design.md#sample-apps)**  -criar grandes experiências de exemplos projetado e criado pela nossa equipe.
* **[Ferramentas e recursos de design](design.md#design-tools)**  -iniciar rapidamente seu projeto com modelos de design e ferramentas.

Para todos os itens acima, nosso objetivo é oferecer a combinação certa de texto, ilustrações e diagramas e vídeos, você verá nos experimentar diferentes formatos e técnicas, tudo isso com a intenção de oferecer o que você precisa. E nos meses futuros, expandiremos esta taxonomia para incluir um conjunto mais amplo de tópicos de design. Sempre que possível, que daremos a você uma alerta sobre o que está por vir, portanto, mantenha a verificação de volta.

## <a name="objectives"></a>Objetivos

Aqui está uma rápida olhada alguns objetivos de alto nível que estão orientando esse trabalho para que você possa entender onde estamos vindo da

### <a name="help-solve-customer-challenges"></a>Ajudar a resolver os desafios do cliente

![Ajudar a resolver os desafios do cliente](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Podemos resolver muitos dos mesmos problemas que você faz, e sabemos que seu trabalho como um desafio é. É interessante explorar e definir uma nova fronteira... e também pode ser desanimador. Práticas recomendadas e desses paradigmas antigos precisam ser considerado novamente; os clientes precisam de novas experiências; e há muito potencial para a inovação. Considerando que queremos que esse trabalho para ser abrangente quanto for possível, movendo bem além de um guia de estilo. Nosso objetivo é fornecer um conjunto abrangente de diretrizes de design que abrange misturadas interação realidade, comandando, navegação, entrada e estilo – tudo com base em cenários e o comportamento humano. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Aponte o sentido de uma maneira nova e mais humano da computação

![Aponte o sentido de uma maneira nova e mais humano da computação](images/500px-man-and-women-with-holograph-on-table.png)<br>

Embora seja importante para se concentrar em problemas específicos do cliente, também queremos que enviar por push sozinhos pensar além disso e para oferecer maior. Acreditamos que ótimo design não é "just" solução de problemas, mas também uma maneira de ativar significativamente evolução humana. Novas maneiras de comportamento humano. novas maneiras de pessoas relacionadas a mesmos, suas atividades e seus ambientes; novas maneiras de ver nosso mundo... queremos que nossas diretrizes para refletir todas as essas maneiras mais ambiciosos de pensar muito. 

### <a name="meet-creators-where-they-are"></a>Atender aos criadores de onde eles estão

![Atender aos criadores de onde eles estão](images/500px-creators.jpg) <br>

Esperamos que muitos públicos encontrar esta diretriz para ser útil. Você tem diferentes conjuntos de habilidades (começando, intermediário, Avançado), usam ferramentas diferentes (Unity, DirectX, C++, C#, outros), estão familiarizados com várias plataformas (Windows, iOS, Android), provenientes de diferentes planos de fundo (mobile, enterprise, jogos ) e estamos trabalhando nas equipes de tamanho diferente (solo, pequeno, médio, grande). Portanto, neste guia pode ser exibido com necessidades e perspectivas diferentes. Sempre que possível, tentaremos manter essa diversidade em mente e tornar nossa orientação tão relevante quanto possível para muitas pessoas quanto possível. Além disso, nós sabemos que muitos de vocês já estão no GitHub. Portanto, vamos diretamente vincular repositórios do GitHub e fóruns para atender a você onde já estão. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Compartilhar um tanto quanto possível, de experimental para explícita

![Compartilhar um tanto quanto possível, de experimental para explícita](images/500px-man-playinggame.jpg) <br>

Um dos desafios da oferta de diretrizes de design nesse novo meio 3D é que nem sempre temos de orientação propriamente dita a oferecer. Assim como você, aprendemos, testar, criação de protótipos, solução de problemas e ajustar e como atingimos obstáculos. Em vez de esperar por algum momento futuro mítico quando tivermos ele descobriu, nosso objetivo compartilhar nosso pensamento com você em tempo real, mesmo se ele não é conclusivo. É claro, nossa meta final é ser definitivo, sempre que possível, clear, fornecendo um design flexível diretrizes vinculados ao código-fonte aberto e acionáveis em ferramentas de design e desenvolvimento da Microsoft. Mas Introdução a esse ponto leva a muitas rodadas de iteração e aprendizado. Queremos entre em contato com você e aprenda com você, ao longo do caminho. Com tudo isso em mente, faremos nosso melhor para compartilhar à medida que avançarmos, mesmo com nossos materiais de experimental. 

### <a name="the-right-balance-of-global-and-local-design"></a>O equilíbrio correto de design global e local

![O equilíbrio correto de design global e local](images/500px-fluentdesign.jpg) <br>

Iremos oferecer dois níveis de diretrizes de design: global e local. Nossas diretrizes de design 'global' é incorporada na [Fluent Design System](http://fluent.microsoft.com). Detalhes do Fluent como pensamos sobre conceitos básicos de como a luz, profundidade, movimento, material e escala em todos os Microsoft design – nossos dispositivos, produtos, ferramentas e serviços. Dito isso, diferenças significativas de dispositivo específico existem em todo este sistema maior. Assim, nossas diretrizes de design 'local' de fone de ouvido exibe descrevem o desenvolvimento para dispositivos holográfico e imersivos que geralmente tem uma entrada diferente e métodos, bem como diferentes necessidades dos usuários e cenários de saída. Diretrizes de design local aborda tópicos HMDs exclusivos. Por exemplo:  Ambientes 3D e objetos. ambientes compartilhados; o uso de sensores, acompanhamento de olho e mapeamento espacial; e as oportunidades de áudio espacial. Em toda a nossa orientação você provavelmente verá-nos se referir a essas global e os aspectos de locais. Espero que isso ajudará a Terra seu trabalho em uma base maior de design, aproveitando as diferenças de design entre dispositivos específicos.

### <a name="have-a-discussion"></a>Ter uma discussão

![Ter uma discussão](images/500px-share.jpg) <br>

Talvez mais importante, queremos entre em contato com você, a comunidade de holográfica e imersivos designers e desenvolvedores, para definir nesta nova era interessante de design. Conforme mencionado acima, nós sabemos que não temos todas as respostas. Que por que acreditamos que muitas soluções empolgantes e inovações serão provenientes de você. Temos o objetivo de ser aberta e disponível para ouvi-los e discutir com você, online e em eventos e adicione o valor sempre que possível. Estamos muito animados para sermos uma parte desta comunidade incrível de design, embarcar em uma aventura juntos. 

## <a name="please-dive-in"></a>Aprofunde-se

Esperamos que este artigo introdutório fornece algum contexto significativo, conforme você explora nossas diretrizes de design. Aprofunde-se e informe-nos seus comentários nos fóruns do GitHub você encontrará dados vinculados em nossos artigos, ou ao Design da Microsoft em [Twitter](https://twitter.com/MicrosoftDesign) e [Facebook](https://www.facebook.com/microsoftdesign/). Vamos conjunta projetar o futuro juntos!

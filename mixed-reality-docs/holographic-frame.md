---
title: Quadro holográfico
description: Os usuários veem o mundo da realidade misturada por meio do quadro holográfica.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, quadro holográfico, de campo de visão
ms.openlocfilehash: 6773bc03dea471c97d0c6006d2ab7853a5ef3669
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589330"
---
# <a name="holographic-frame"></a>Quadro holográfico

Os usuários veem o mundo da realidade misturada por meio de um visor retangular alimentado por seu fone de ouvido. No HoloLens, desta área retangular é chamada de quadro holográfico e permite que os usuários vejam o conteúdo digital sobreposto no mundo real ao redor deles. Projetar experiências otimizadas para o quadro holográfico cria oportunidades, minimiza os desafios e aprimora a experiência do usuário de aplicativos de realidade misturada.

## <a name="designing-for-content"></a>Projetando para o conteúdo

Muitas vezes designers se sentir a necessidade de limitar o escopo de sua experiência, o que o usuário pode ver imediatamente, sacrificar a escala do mundo real para garantir que o usuário vê um objeto em sua totalidade. Da mesma forma designers com aplicativos complexos geralmente sobrecarregam o quadro holographic com o conteúdo, sobrecarregar os usuários com interfaces desorganizados e difíceis de interações. Designers de criação de realidade misturada conteúdo não precisam limitar sua experiência para diretamente na frente do usuário e dentro de sua exibição imediata. Se mundo físico em torno do usuário é mapeado, em seguida, todas estas superfícies devem ser consideradas uma tela de potencial de conteúdo digital e interações. Design apropriado de interações e conteúdo dentro de uma experiência deve incentivar o usuário mover em torno de seu espaço, direcionar sua atenção para o conteúdo da chave e ajudando a ver todo o potencial de realidade misturada.

Talvez seja a técnica mais importante para movimentação e a exploração de dentro de um aplicativo incentivando **permitem que os usuários ajustar à experiência**. Oferece um curto período de tempo 'livre de tarefa' com o dispositivo. Isso pode ser tão simples como colocar um objeto no espaço e permitindo que os usuários mover ao redor dele ou narração uma introdução à experiência. Esse tempo deverão estar livre de quaisquer tarefas críticas ou específicos de gestos (por exemplo, ar-tocando), em vez disso, a finalidade de permitir que os usuários acomodar para exibir o conteúdo por meio do dispositivo antes de exigir interatividade ou está em andamento pelos estágios do aplicativo. Se essa for a primeira vez que um usuário com o dispositivo, isso é especialmente importante quando eles obtêm conteúdo vendo confortável por meio do quadro holográfico e da natureza da hologramas.

### <a name="large-objects"></a>Objetos grandes

Muitas vezes o conteúdo requer uma experiência, especialmente reais conteúdo, será maior que o quadro holográfico. Objetos que normalmente não couberem dentro do quadro holográfico devem ser reduzidos para caber quando eles forem introduzidos pela primeira vez (em uma escala menor ou a uma distância). A chave é **permitem que os usuários ver o tamanho total do objeto** antes que a escala domina o quadro. Por exemplo, um elefante holográfica deve ser exibida para caber completamente dentro do quadro, permitindo que os usuários formar um entendimento espacial de forma geral do animal, antes de dimensioná-la para [reais escala](scale.md) perto do usuário.

Com o tamanho total do objeto em mente, os usuários, em seguida, têm uma expectativa de onde mover-se e procure a partes específicas desse objeto. Da mesma forma, em uma experiência com conteúdo imersivo, ele pode ajudar a ter alguma maneira para referir-se de volta para o tamanho total do conteúdo. Por exemplo, se a experiência de envolver a andar de um modelo de uma casa virtual, ela pode ajudar para ter uma versão menor do tamanho da própria doll empresa da experiência que os usuários podem acionar para entender onde eles estão dentro de casa.

Para obter um exemplo de criação de objetos grandes, consulte [Volvo Cars](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Muitos objetos

Experiências com muitos objetos ou componentes devem considerar a usar o espaço total em torno do usuário para evitar problemas de quadro holográfico diretamente na frente do usuário. Em geral, é recomendável apresentar o conteúdo para uma experiência lenta e isso é especialmente verdadeiro com experiências que pretende atender muitos objetos ao usuário. Assim como com objetos grandes, a chave é **permitem que os usuários a entender o layout do conteúdo** na experiência, ajudando a obter uma compreensão espacial do qual é em torno deles conforme o conteúdo é adicionado à experiência.

Uma técnica para fazer isso é fornecer pontos de persistentes (também conhecido como pontos de referência) na experiência esse conteúdo de âncora para o mundo real. Por exemplo, um ponto de referência pode ser um objeto físico no mundo real, como uma tabela onde o conteúdo digital é exibido, ou um objeto digital, como um conjunto de telas digitais em que o conteúdo com frequência é exibido. Objetos também podem ser colocados na periferia do quadro para incentivar o usuário procurar em direção a chave de conteúdo, enquanto a descoberta de conteúdo além daqueles periferia pode ser facilitada pelo holographic [diretores de atenção](holographic-frame.md#attention-directors).

Colocando objetos na periferia pode incentivar os usuários consultem ao lado, e isso pode ser auxiliado pela diretoria de atenção, conforme descrito abaixo.

## <a name="user-comfort"></a>Conforto do usuário

Para experiências de realidade misturada com muitos objetos ou objetos grandes, é fundamental levar em consideração quanto head e movimentação do pescoço é necessária interagir com o conteúdo. Experiências podem ser divididas em três categorias em termos de movimentação do cabeçote: **Horizontal** (lado a lado), **vertical** (para cima e para baixo), ou **imersivos** (horizontal e vertical). Quando possível, limite o ideal é que a maioria das interações a categorias horizontais ou verticais, com a maioria das experiências que estão ocorrendo no centro do quadro holográfico enquanto head do usuário está em uma posição neutra. Evite as interações que fazem com que o usuário mover constantemente sua exibição para um artificial posições principal (por exemplo, pesquisar sempre acessar uma interação de menu de chave).

![A região ideal para o conteúdo é graus de 0 a 35 abaixo horizonte](images/optimal-field-of-view-2-750px.png)<br>
*A região ideal para o conteúdo é graus de 0 a 35 abaixo horizonte*

Movimentação do cabeçote horizontal é mais [confortável](comfort.md) para interações frequentes, enquanto os movimentos verticais devem ser reservados para eventos incomuns. Por exemplo, uma experiência que envolvem uma linha do tempo horizontal longa deve limitar a movimentação do cabeçote vertical para interações (como olhando para baixo um menu).

Considere a possibilidade de incentivar a movimentação de corpo completo, em vez de movimentação do cabeçote apenas, colocando objetos em torno do espaço do usuário. Experiências com movimentação de objetos ou objetos grandes devem prestar atenção especial a movimentação do cabeçote, especialmente em que eles exigem a movimentação frequente ao longo dos eixos horizontais e verticais.

## <a name="interaction-considerations"></a>Considerações de interação

Assim como acontece com o conteúdo, as interações em uma experiência de realidade misturada não precisam ser limitadas a que o usuário pode ver imediatamente. Interações podem ocorrer em qualquer lugar no espaço do mundo real em torno do usuário e essas interações podem ajudar a incentivar os usuários a mover-se e explore as experiências.

### <a name="attention-directors"></a>Diretores de atenção

Indicando que pontos de interesse ou interações de chaves podem ser cruciais para usuários de progresso por meio de uma experiência. Atenção do usuário e a movimentação do quadro holográfica podem ser direcionadas de maneiras sutis ou agressiva. Lembre-se de saldo diretores de atenção com períodos de exploração gratuita na realidade misturada (especialmente no início de uma experiência) para evitar sobrecarregar o usuário. Em geral, há dois tipos de diretores de atenção:
* **Diretores Visual:** A maneira mais fácil para avisar ao usuário que eles devem mover em uma direção específica é fornecer uma indicação visual. Isso pode ser feito por meio de um efeito visual (por exemplo, um caminho que o usuário pode seguir visualmente em direção a próxima parte da experiência) ou até mesmo como setas direcionais simples. Observe que qualquer indicador visual deve com aterramento dentro do ambiente do usuário, não 'conectado' para o quadro holográfico ou o cursor.
* **Diretores de áudio:** [Som espacial](spatial-sound-design.md) pode fornecer uma maneira eficiente para estabelecer a objetos em uma cena (usuários de objetos inserindo uma experiência de alertas) ou chamar a atenção para um ponto específico no espaço (para mover a exibição do usuário para objetos de chave). Usar diretores de áudio para orientar a atenção do usuário pode ser mais sutis e menos intrusivo que diretores de visual. Em alguns casos, é melhor começar com um diretor de áudio e, em seguida, passar para um diretor visual se o usuário não reconhece a indicação. Diretores de áudio também podem ser emparelhadas com directors visual para enfatizar ainda mais.

### <a name="commanding-navigation-and-menus"></a>Navegação, comandos e menus

Interfaces nas experiências de realidade misturada idealmente são emparelhados estreitamente com conteúdo digital, que eles controlam. Como tal, menus 2D flutuantes geralmente não são ideais para interação e podem ser difícil para os usuários confortavelmente com dentro do quadro holográfico. Para experiências que exigir que elementos de interface, como menus ou campos de texto, considere o uso de um [método tag-along](billboarding-and-tag-along.md) a seguir o quadro holográfico após um pequeno atraso. Evite o bloqueio de conteúdo para o quadro como um HUD, pois isso pode ser confusão para o usuário e a quebra o sentido de imersão para outros objetos digitais na cena.

Como alternativa, considere posicionar elementos da interface diretamente no específicos do conteúdo de controle, permitindo interações acontecer naturalmente em torno do espaço físico do usuário. Por exemplo, divida um menu de complexo em partes separadas. Com cada botão ou um grupo de controles anexados para o objeto específico que afeta a interação. Para aprofundar ainda mais esse conceito, considere o uso de [interagível objetos](interactable-object.md).

### <a name="gaze-and-gaze-targeting"></a>Mantenha o foco e mantenha o foco de direcionamento

O quadro holográfico apresenta uma ferramenta para o desenvolvedor às interações do gatilho, bem como avaliar onde dwells a atenção de um usuário. [Olhares](gaze.md) é um da [chave interações no HoloLens](interaction-fundamentals.md), onde olhar pode ser emparelhado com [gestos](gestures.md) (como com ar tocar) ou [voz](voice-input.md) (permitindo mais curto interações de voz com base em mais naturais). Dessa forma, isso torna o quadro holográfico ambas as um espaço para observar o conteúdo digital, bem como interagir com ele. Se a experiência de chamadas para interagir com vários objetos em torno do espaço do usuário (por exemplo, a seleção de vários objetos em torno do espaço do usuário com olhar + gesto), considere colocar esses objetos em modo de exibição do usuário ou limitando a quantidade de cabeçalho necessários movimentação para promover [conforto](comfort.md).

Olhar também pode ser usado para acompanhar a atenção do usuário por meio de uma experiência e ver quais objetos ou partes da cena usuário pago muita atenção ao. Isso pode ser especialmente uso para uma experiência, permitindo a ferramentas analíticas, como mapas de calor para ver onde os usuários gastam mais tempo ou estão ausentes determinados objetos ou a interação de depuração. Olhar rastreamento também pode fornecer uma ferramenta poderosa para facilitadores nas experiências (consulte a [cozinha do Lowe](holographic-frame.md#lowes-kitchen) exemplo).

## <a name="performance"></a>Desempenho

O uso adequado do quadro holográfico é fundamental para o [qualidade de desempenho](understanding-performance-for-mixed-reality.md) experiências. Um desafio técnico (e a usabilidade) comum está sobrecarregando o quadro do usuário com conteúdo digital, causando a degradação de desempenho de renderização. Considere em vez de usar o espaço total em torno do usuário para organizar o conteúdo digital, usando as técnicas descritas acima, para diminuir a carga de processamento e certifique-se de uma qualidade de exibição ideal.

Conteúdo digital dentro do quadro holográfico do HoloLens também pode ser emparelhado com o [plano de estabilização](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) para otimizar o desempenho e [estabilidade holograma](hologram-stability.md).

## <a name="examples"></a>Exemplos

### <a name="volvo-cars"></a>Volvo Cars

>[!VIDEO https://www.youtube.com/embed/DilzwF90vec]

Na experiência de sala de exposições de carros Volvo, os clientes são convidados a saber mais sobre os recursos de um carro novo HoloLens experiência orientada por um parceiro Volvo. Volvo enfrentou um desafio com o quadro holográfico: um carro em tamanho normal é muito grande para colocar bem ao lado de um usuário. A solução era começar a experiência com um ponto de referência físico, uma tabela central em sala de exposições, com um modelo de digital menor do carro colocado sobre a tabela. Isso garante que o usuário esteja vendo o carro completo quando ele é introduzido, permitindo um senso de espacial Noções básicas sobre depois que o carro cresce para sua escala do mundo real mais tarde na experiência.

Volvo experiência também possibilita usar visual diretoria, criando um efeito visual longo do modelo do carro em pequena escala na tabela para uma parede na sala de mostrar. Isso leva a um efeito de "janela mágica", mostrando a exibição completa do carro em uma distância, que ilustra recursos adicionais do carro em escala do mundo real. A movimentação do cabeçote é horizontal, sem qualquer interação direta do usuário (em vez disso, reunindo indicações visualmente e de narração de associar o Volvo da experiência).

### <a name="lowes-kitchen"></a>Cozinha do Lowe

Uma experiência de repositório do Lowe convida os clientes em um modelo de grande escala de uma cozinha para apresentar várias oportunidades reforma como visto pelo HoloLens. Cozinha no repositório de fornece o pano de fundo de físico para objetos digitais, uma tela em branco de aparelhos domésticos, Granito e gabinetes para a experiência de realidade mista Desdobrar.

As superfícies de físico atuam como pontos de referência estáticos para o usuário terra em si na experiência, como associar de um Lowe orienta o usuário por meio de opções de produto diferente e é concluída. Dessa forma, o associado verbalmente pode direcionar a atenção do usuário para o 'Refrigerator (Refrigerador)' ou 'Centro da cozinha' ao conteúdo digital de demonstração.

![Associar de um Lowe usa um tablet para guiar os clientes por meio da experiência do HoloLens.](images/loweskitchen-750px.jpg)<br>
*Associar de um Lowe usa um tablet para guiar os clientes por meio da experiência do HoloLens.*

A experiência do usuário é gerenciada, em parte, por uma experiência de tablet controlada pela associação do Lowe. Parte da função do vendedor nesse caso, também seria limitar a movimentação do cabeçote excessiva, direcionar sua atenção perfeitamente entre os pontos de interesse na cozinha. A experiência de tablet também fornece associado do Lowe olhar dados na forma de um modo de exibição de mapa de calor de cozinha, ajudando a entender onde o usuário é dwelling (por exemplo, em uma área específica do gabinete) com mais precisão fornecê-las com orientação de reforma.

Para uma análise mais profunda experiência de cozinha do Lowe, consulte [palestra da Microsoft no Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

### <a name="fragments"></a>Fragmentos

Em fragmentos de jogo o HoloLens, sala de estar é transformada em cena do crime virtual mostrando pistas e evidências, bem como uma sala de reunião virtual, onde você pode se comunicar com os caracteres que ficam em suas cadeiras e confie na parede.

![Fragmentos foi projetado para entrar em vigor na página inicial do usuário, com caracteres interagindo com superfícies e objetos do mundo real.](images/fragments-750px.jpg)<br>
*Fragmentos foi projetado para entrar em vigor na página inicial do usuário, com caracteres interagindo com superfícies e objetos do mundo real.*

Quando os usuários começar inicialmente a experiência, eles são dado um curto período de ajuste, onde muito pouca interação é necessária, em vez disso, encorajando-os a olhar em volta. Isso também ajuda a garantir que a sala está mapeada corretamente para o conteúdo interativo do jogo.

Em toda a experiência caracteres se tornarem os pontos de focal e atuam como visual directors (principais movimentações entre caracteres, a ativação para examinar ou de gesto em direção a áreas de interesse). O jogo também conta com mais proeminentes indicações visuais quando um usuário leva muito tempo para localizar um objeto ou um evento e faz uso intenso de áudio espacial (especialmente com vozes de caracteres ao inserir uma cena).

### <a name="destination-mars"></a>Destino: MARS

No destino: Experiência de MARS em destaque no [Kennedy espaço Center da NASA](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/), visitantes foram convidados em um processamento envolvente para a superfície do Mars, orientada por representação virtual da astronaut lendário repercussão Aldrin.

![Um Aldrin de repercussão virtual se torna o ponto focal para os usuários no destino: MARS.](images/destinationmars-750px.png)<br>
*Um Aldrin de repercussão virtual se torna o ponto focal para os usuários no destino: MARS.*

Como uma experiência imersiva, esses usuários foram incentivados a olhar em volta, movendo suas cabeças em todas as direções para ver o panorama Martian virtual. Embora para garantir o conforto dos usuários, Aldrin repercussão narração e presença virtual fornecido um ponto focal em toda a experiência. Essa gravação virtual alvoroço (criado pelo [estúdios de captura de realidade misturada da Microsoft](https://www.microsoft.com/mixed-reality/capture-studios)) resistiu em tamanho real, humanos, no canto da sala, permitindo que os usuários de vê-lo no modo de exibição quase completa. Narração de agitação direcionado a usuários para se concentrar em pontos diferentes no ambiente (por exemplo, um conjunto de Martian é o máximo no chão ou uma variedade de montanha na distância) com alterações de cena específica ou objetos introduzidos por ele.

![Os narradores virtuais se tornará a seguir a movimentação de um usuário, criando um ponto focal poderoso em toda a experiência.](images/gazereset-750px.png)<br>
*Os narradores virtuais se tornará a seguir a movimentação de um usuário, criando um ponto focal poderoso em toda a experiência.*

A representação realista alvoroço fornecido um poderoso ponto focal, completo com técnicas sutis para ativar a agitação em direção ao usuário para se sentir como se ele está lá, fala para você. Quando o usuário se move sobre a experiência, repercussões mudará em direção a você para um limite antes de retornar a um estado neutro, se o usuário vai muito além do seu periferia. Se o usuário tiver a aparência de agitação completamente (por exemplo, para olhar para algo em outro lugar na cena), em seguida, voltar ao repercussões, uma vez será de posição direcional do narrator novamente se concentrar no usuário. Técnicas como este fornecem uma noção poderosa de imersão e criar um ponto focal dentro do quadro holográfico, reduzindo a movimentação do cabeçote excessiva e promovendo [conforto](comfort.md).

## <a name="see-also"></a>Consulte também
* [Conceitos básicos de interação](interaction-fundamentals.md)
* [Conforto](comfort.md)
* [Escala](scale.md)
* [Mantenha o foco de direcionamento](gaze-targeting.md)
* [Estabilidade holograma](hologram-stability.md)

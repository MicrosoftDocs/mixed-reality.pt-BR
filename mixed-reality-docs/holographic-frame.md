---
title: Quadro Holographic
description: Os usuários veem o mundo da realidade misturada por meio do quadro Holographic.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, realidade misturada do Windows, quadro Holographic, campo de exibição
ms.openlocfilehash: c505eadbc16bb59143313aa62dd7c9d95384e0c8
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974922"
---
# <a name="holographic-frame"></a>Quadro Holographic

Os usuários veem o mundo da realidade misturada por meio de um visor retangular equipado com o headset. No HoloLens, essa área retangular é chamada de quadro Holographic e permite que os usuários vejam o conteúdo digital sobreposto ao mundo real em relação a eles. A criação de experiências otimizadas para o quadro Holographic cria oportunidades, reduz os desafios e aprimora a experiência do usuário de aplicativos de realidade misturada.

## <a name="designing-for-content"></a>Design de conteúdo

Geralmente, os designers sentem a necessidade de limitar o escopo de sua experiência com o que o usuário pode ver imediatamente, sacrificando a escala do mundo real para garantir que o usuário veja sua totalidade. Os designers da mesma forma com aplicativos complexos geralmente sobrecarregam o quadro Holographic com o conteúdo, sobrecarregam os usuários com interações difíceis e interfaces congestionadas. Os designers que criam o conteúdo de realidade misturada não precisam limitar sua experiência diretamente na frente do usuário e em sua exibição imediata. Se o mundo físico em todo o usuário for mapeado, todas essas superfícies deverão ser consideradas uma tela potencial para conteúdo digital e interações. O design adequado de interações e conteúdo em uma experiência deve incentivar o usuário a se movimentar em seu espaço, direcionando sua atenção para o conteúdo principal e ajudando a ver todo o potencial da realidade misturada.

Talvez a técnica mais importante para incentivar o movimento e a exploração em um aplicativo seja **permitir que os usuários se ajustem à experiência**. Dê aos usuários um curto período de tempo de "tarefa livre" com o dispositivo. Isso pode ser tão simples quanto colocar um objeto no espaço e permitir que os usuários se movam por volta ou narrando uma introdução à experiência. Esse tempo deve ser livre de qualquer tarefa crítica ou de gestos específicos (como toque de ar), em vez do objetivo de permitir que os usuários acomodem a exibição de conteúdo por meio do dispositivo antes de exigir interatividade ou progredir nos estágios do aplicativo. Se essa for a primeira vez que um usuário tiver o dispositivo, isso é especialmente importante, pois ele se sente confortável ao ver o conteúdo por meio do quadro Holographic e a natureza dos hologramas.

### <a name="large-objects"></a>Objetos grandes

Geralmente, o conteúdo que uma experiência chama, especialmente o conteúdo real, será maior do que o quadro Holographic. Os objetos que normalmente não se ajustam no quadro Holographic devem ser reduzidos quando são introduzidos pela primeira vez (em uma escala menor ou em uma distância). A chave é **permitir que os usuários vejam o tamanho total do objeto** antes que a escala sobrecarregue o quadro. Por exemplo, um elefante Holographic deve ser exibido para se ajustar totalmente dentro do quadro, permitindo que os usuários formem uma compreensão espacial da forma geral do animal, antes de dimensioná-lo para a [escala do mundo real](scale.md) perto do usuário.

Com o tamanho total do objeto em mente, os usuários têm uma expectativa de onde mover e procurar partes específicas desse objeto. Da mesma forma, em uma experiência com conteúdo de imersão, ele pode ajudar a ter alguma forma de referir-se ao tamanho completo desse conteúdo. Por exemplo, se a experiência envolve a movimentação de um modelo de uma casa virtual, pode ajudar a ter uma versão de tamanho menor do Doll da experiência que os usuários podem disparar para entender onde estão dentro da casa.

Para obter um exemplo de criação de objetos grandes, consulte [carros de Volvo](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Muitos objetos

Experiências com muitos objetos ou componentes devem considerar o uso de espaço completo em todo o usuário para evitar a aglomeração do quadro Holographic diretamente na frente do usuário. Em geral, é uma boa prática introduzir o conteúdo a uma experiência lenta e isso é especialmente verdadeiro com experiências que planejam fornecer muitos objetos ao usuário. Assim como ocorre com objetos grandes, a chave é **permitir que os usuários compreendam o layout do conteúdo** na experiência, ajudando-os a obter um entendimento espacial do que há em volta, pois o conteúdo é adicionado à experiência.

Uma técnica para conseguir isso é fornecer pontos persistentes (também conhecidos como pontos de referência) na experiência que ancora o conteúdo ao mundo real. Por exemplo, um ponto de referência pode ser um objeto físico no mundo real, como uma tabela em que o conteúdo digital aparece, ou um objeto digital, como um conjunto de telas digitais em que o conteúdo é exibido com frequência. Os objetos também podem ser colocados no periferia do quadro Holographic para incentivar o usuário a procurar o conteúdo da chave, enquanto a descoberta de conteúdo além da periferia pode ser auxiliada por [diretores de atenção](holographic-frame.md#attention-directors).

Colocar objetos no periferia pode encorajar os usuários a olhar para o lado e isso pode ser auxiliado por diretores de atenção, conforme descrito abaixo.

## <a name="user-comfort"></a>Conforto do usuário

Para experiências de realidade misturada com objetos grandes ou muitos objetos, é crucial considerar o quanto movimento de cabeça e pescoço é necessário para interagir com o conteúdo. As experiências podem ser divididas em três categorias em termos de movimento de cabeçalho: **Horizontal** (lado a lado), **vertical** (para cima e para baixo) ou **imersiva** (horizontal e vertical). Quando possível, limite a maioria das interações a categorias horizontais ou verticais, idealmente com a maioria das experiências ocorrendo no centro do quadro do Holographic, enquanto o cabeçalho do usuário está em uma posição neutra. Evite interações que fazem com que o usuário mova constantemente sua exibição para uma posição de cabeçalho não natural (por exemplo, sempre procurando acessar uma interação de menu de chave).

![A região ideal para conteúdo é de 0 a 35 graus abaixo do horizonte](images/optimal-field-of-view-2-750px.png)<br>
*A região ideal para conteúdo é de 0 a 35 graus abaixo do horizonte*

O movimento de cabeçalho horizontal é mais [confortável](comfort.md) para interações frequentes, enquanto os movimentos verticais devem ser reservados para eventos incomuns. Por exemplo, uma experiência que envolva uma linha de tempo horizontal longa deve limitar o movimento de cabeçalho vertical para interações (como olhar para baixo em um menu).

Considere a possibilidade de incentivar a movimentação de corpo completo, em vez de apenas a movimentação de cabeçalho, colocando objetos em todo o espaço do usuário. Experiências com movimentação de objetos ou objetos grandes devem prestar atenção especial ao movimento de cabeçalho, especialmente onde eles exigem movimento freqüente ao longo dos eixos horizontal e vertical.

## <a name="interaction-considerations"></a>Considerações sobre interação

Assim como acontece com o conteúdo, as interações em uma experiência de realidade misturada não precisam ser limitadas ao que o usuário pode ver imediatamente. As interações podem ocorrer em qualquer lugar do espaço do mundo real em relação ao usuário e essas interações podem ajudar a incentivar os usuários a se movimentarem e explorarem experiências.

### <a name="attention-directors"></a>Diretores de atenção

Indicar pontos de interesse ou interações de chave pode ser crucial para progredir os usuários por meio de uma experiência. A atenção do usuário e a movimentação do quadro Holographic podem ser direcionadas de formas sutis ou pesadas. Lembre-se de direcionar os diretores de atenção com períodos de exploração gratuita em realidade misturada (especialmente no início de uma experiência) para evitar sobrecarregar o usuário. Em geral, há dois tipos de diretores de atenção:
* **Diretores visuais:** A maneira mais fácil de permitir que o usuário saiba que ele deve se mover em uma direção específica é fornecer uma indicação visual. Isso pode ser feito por meio de um efeito visual (por exemplo, um caminho que o usuário pode seguir visualmente para a próxima parte da experiência) ou até mesmo como setas direcionais simples. Observe que qualquer indicador visual deve se basear no ambiente do usuário, não ' anexado ' ao quadro Holographic ou ao cursor.
* **Diretores de áudio:** O [som espacial](spatial-sound-design.md) pode fornecer uma maneira poderosa de estabelecer objetos em uma cena (alertando os usuários de objetos que entram em uma experiência) ou direcionar a atenção para um ponto específico no espaço (para mover a exibição do usuário para objetos de chave). Usar os diretores de áudio para orientar a atenção do usuário pode ser mais sutil e menos invasivo do que os diretores visuais. Em alguns casos, pode ser melhor começar com um diretor de áudio e, em seguida, passar para um diretor Visual se o usuário não reconhecer a indicação. Os diretores de áudio também podem ser emparelhados com os diretores visuais para dar ênfase adicional.

### <a name="commanding-navigation-and-menus"></a>Comandos, navegação e menus

As interfaces em experiências mistas de realidade são emparelhadas de maneira adequada com o conteúdo digital que eles controlam. Assim, os menus 2D sem flutuação livre geralmente não são ideais para interação e podem ser difíceis para os usuários se tornarem confortavelmente dentro do quadro Holographic. Para experiências que exigem elementos de interface como menus ou campos de texto, considere usar um [método de marca](billboarding-and-tag-along.md) para seguir o quadro Holographic após um pequeno atraso. Evite bloquear conteúdo para o quadro como uma exibição de cabeçotes, pois isso pode ser desorientado para o usuário e quebrar o sentido do imersão para outros objetos digitais na cena.

Como alternativa, considere colocar elementos de interface diretamente no conteúdo específico que eles controlam, permitindo que as interações ocorram naturalmente em relação ao espaço físico do usuário. Por exemplo, quebre um menu complexo em partes separadas. Com cada botão ou grupo de controles anexados ao objeto específico, a interação afeta. Para obter esse conceito mais detalhadamente, considere o uso de [objetos](interactable-object.md)que interagem.

### <a name="gaze-and-gaze-targeting"></a>Direcionamento de olhar e olhar

O quadro Holographic apresenta uma ferramenta para o desenvolvedor disparar interações, bem como avaliar onde a atenção de um usuário faz as comparações. [Olhar](gaze.md) é uma das [principais interações no HoloLens](interaction-fundamentals.md), em que olhar pode ser emparelhado com [gestos](gestures.md) (como com toque de ar) ou [voz](voice-input.md) (permitindo interações mais curtas e naturais baseadas em voz). Dessa forma, isso torna o quadro Holographic um espaço para observar o conteúdo digital, bem como interagir com ele. Se a experiência chamar a interação com vários objetos em todo o espaço do usuário (por exemplo, várias seleções de objetos em todo o espaço do usuário com olhar + gesto), considere colocar esses objetos na exibição do usuário ou limitar a quantidade de cabeçalho necessária movimento para promover o [conforto do usuário](comfort.md).

O olhar também pode ser usado para controlar a atenção do usuário por meio de uma experiência e ver quais objetos ou partes da cena o usuário pagou mais atenção. Isso pode ser usado especialmente para depurar uma experiência, permitindo que ferramentas analíticas como o calor vejam onde os usuários estão gastando mais tempo ou faltam determinados objetos ou interação. O acompanhamento de olhar também pode fornecer uma ferramenta poderosa para os facilitadores em experiências (consulte o exemplo de [cozinha do Lowe](holographic-frame.md#lowes-kitchen) ).

## <a name="performance"></a>Desempenho

O uso adequado do quadro Holographic é fundamental para as experiências de [qualidade de desempenho](understanding-performance-for-mixed-reality.md) . Um desafio comum (e usabilidade) é sobrecarregar o quadro do usuário com conteúdo digital, causando degradação do desempenho de renderização. Considere, em vez disso, usar o espaço completo em volta do usuário para organizar o conteúdo digital, usando as técnicas descritas acima, para diminuir a carga da renderização e garantir uma qualidade de exibição ideal.

O conteúdo digital dentro do quadro Holographic do HoloLens também pode ser emparelhado com o [plano](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) de estabilização para obter o desempenho ideal e a [estabilidade do holograma](hologram-stability.md).

## <a name="examples"></a>Exemplos

### <a name="volvo-cars"></a>Carros Volvo

>[!VIDEO https://www.youtube.com/embed/DilzwF90vec]

Na experiência do showroom da Volvo carros, os clientes são convidados a aprender sobre os novos recursos de carros em uma experiência de HoloLens guiada por um associado Volvo. Volvo enfrentou um desafio com o quadro Holographic: um carro de tamanho completo é muito grande para ser colocado ao lado de um usuário. A solução era iniciar a experiência com um ponto de referência físico, uma tabela central no showroom, com um modelo digital menor do carro colocado sobre a tabela. Isso garante que o usuário esteja vendo o carro completo quando ele é introduzido, permitindo um entendimento espacial, uma vez que o carro cresce para a escala do mundo real posteriormente na experiência.

A experiência do Volvo também usa os directors visuais, criando um efeito visual longo do modelo de carro de pequena escala na tabela para uma parede na sala de apresentação. Isso leva a um efeito de "janela mágica", mostrando a visão completa do carro a uma distância, ilustrando outros recursos do carro em escala do mundo real. O movimento da cabeça é horizontal, sem qualquer interação direta do usuário (em vez de reunir indicações visualmente e da narração da experiência do Volvo Association).

### <a name="lowes-kitchen"></a>Cozinha de Lowe

Uma experiência de armazenamento do Lowe convida os clientes em uma modelo em escala completa de uma cozinha para demonstrar várias oportunidades de reforma, como visto por meio do HoloLens. A cozinha na loja fornece um pano de fundo físico para objetos digitais, uma tela em branco de dispositivos, a tops e os gabinetes para a experiência mista da realidade para desdobrar.

As superfícies físicas atuam como pontos de referência estáticos para que o usuário se baseie na experiência, uma vez que o associado de um Lowe orienta o usuário por meio de diferentes opções de produtos e é concluído. Dessa forma, a associação pode direcionar verbalmente a atenção do usuário para o ' refrigerador ' ou ' centro da cozinha ' para demonstrar o conteúdo digital.

![A associação de um Lowe usa um tablet para guiar os clientes por meio da experiência do HoloLens.](images/loweskitchen-750px.jpg)<br>
*A associação de um Lowe usa um tablet para guiar os clientes por meio da experiência do HoloLens.*

A experiência do usuário é gerenciada, em parte, por uma experiência do Tablet controlada pela associação do Lowe. Parte da função do associado, nesse caso, também seria limitar a movimentação de cabeçalho excessiva, direcionando sua atenção tranqüilamente em todos os pontos de interesse na cozinha. A experiência do Tablet também fornece a associação do Lowe com os dados do olhar na forma de uma exibição calor da cozinha, ajudando a entender onde o usuário está acessando a pesquisa (por exemplo, em uma área específica do gabinete) para fornecê-las com mais precisão com as diretrizes de reforma.

Para obter uma análise mais profunda da experiência de cozinha do Lowe, consulte a [palestra da Microsoft em Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

### <a name="fragments"></a>Fragments

Nos fragmentos de jogos do HoloLens, a sala de vida é transformada em uma cena de crimes virtuais mostrando pistas e evidências, bem como em uma sala de reunião virtual, na qual você conversa com caracteres que ficam em suas cadeiras e que se fala em suas paredes.

![Os fragmentos foram projetados para ocorrer na casa de um usuário, com caracteres que interagem com objetos e superfícies do mundo real.](images/fragments-750px.jpg)<br>
*Os fragmentos foram projetados para ocorrer na casa de um usuário, com caracteres que interagem com objetos e superfícies do mundo real.*

Quando os usuários iniciam inicialmente a experiência, eles recebem um curto período de ajuste, onde muito pouca interação é necessária, em vez disso, incentivando-os a examinar. Isso também ajuda a garantir que a sala seja mapeada corretamente para o conteúdo interativo do jogo.

Durante toda a experiência, os caracteres se tornam pontos focal e atuam como diretores visuais (movimentos de cabeçalho entre caracteres, voltando à aparência ou ao gesto para áreas de interesse). O jogo também se baseia em indicações visuais mais proeminentes quando um usuário leva muito tempo para localizar um objeto ou evento e faz uso intenso de áudio espacial (especialmente com caracteres vozes ao inserir uma cena).

### <a name="destination-mars"></a>Destino: Mars

No destino: Experiência de Mars em destaque no [centro de espaço Kennedy da NASA](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/), os visitantes foram convidados em uma corrida de imersão para a superfície do Mars, guiado pela representação virtual de lendárias Astronaut de repercussão Aldrin.

![Um Aldrin de repercussão virtual se torna o ponto focal para os usuários no destino: Mars.](images/destinationmars-750px.png)<br>
*Um Aldrin de repercussão virtual se torna o ponto focal para os usuários no destino: Mars.*

Como uma experiência de imersão, esses usuários foram incentivados a examinar, mudando seu rumo em todas as direções para ver o cenário de Martian virtual. Embora seja possível garantir o conforto dos usuários, a presença virtual e a narração de Aldrin de repercussão forneceu um ponto focal durante toda a experiência. Esse registro virtual de repercussão (criado pela [estúdios de captura da realidade misturada da Microsoft) foi](https://www.microsoft.com/mixed-reality/capture-studios)orientado a real, de tamanho humano, no canto da sala, permitindo que os usuários o vejam no modo de exibição quase completo. A narração de repercussão direcionou os usuários a se concentrarem em diferentes pontos no ambiente (por exemplo, um conjunto de Martian Rocks no chão ou um intervalo de montanhas na distância) com alterações de cena específicas ou objetos introduzidos por ele.

![Os narradores virtuais mudarão o movimento de um usuário, criando um ponto focal poderoso em toda a experiência.](images/gazereset-750px.png)<br>
*Os narradores virtuais mudarão o movimento de um usuário, criando um ponto focal poderoso em toda a experiência.*

A representação realista de repercussão proporcionou um poderoso ponto focal, completo com técnicas sutis a serem revisadas para que o usuário se sinta como se estivesse lá, falando com você. À medida que o usuário se move sobre a experiência, a repercussão mudará para você até um limite antes de retornar a um estado neutro se o usuário se movimentar muito além de seu periferia. Se o usuário se parecer totalmente (por exemplo, para examinar algo em outro lugar na cena) e voltar para repercussão, a posição direcional do narrador se concentrará novamente no usuário. Técnicas como essa fornecem uma noção poderosa de imersão e criam um ponto focal dentro do quadro Holographic, reduzindo a movimentação de cabeça excessiva e promovendo o [conforto do usuário](comfort.md).

## <a name="see-also"></a>Consulte também
* [Interações instinctuais](interaction-fundamentals.md)
* [Conforto](comfort.md)
* [Escala](scale.md)
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Estabilidade do holograma](hologram-stability.md)

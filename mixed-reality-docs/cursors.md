---
title: Cursores
description: Um cursor ou indicador de seu vetor de direcionamento, fornece comentários contínuos para que o usuário entenda o que o HoloLens entende sobre suas intenções.
author: thetuvix
ms.author: alexturn, thgable
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1º gen), HoloLens 2, realidade misturada, cursores, direcionamento, olhar, gestos
ms.openlocfilehash: cdedcaffabe0f90e7956fdb19a7b85e202fcf403
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526219"
---
# <a name="cursors"></a>Cursores

> [!NOTE]
> Mais diretrizes específicas para o HoloLens 2 em [breve](index.md#news-and-notes).


Um cursor ou indicador de seu vetor de direcionamento atual, fornece comentários contínuos para que o usuário entenda onde o HoloLens acredita que o foco atual está nesse momento. O cursor permite que o usuário entenda seu ponto de direcionamento atual e atue como feedback para indicar qual área, holograma ou ponto responderá à entrada. É a representação digital de onde o dispositivo entende a atenção do usuário (embora isso possa não ser o mesmo que determinar qualquer coisa sobre suas intenções).

Os comentários fornecidos pelo cursor oferecem aos usuários a capacidade de prever como o sistema responderá, usará esse sinal como comentários para comunicar melhor sua intenção ao dispositivo e, por fim, ser mais confiante em relação às suas interações.

## <a name="hololens-1st-gen"></a>HoloLens (1ª geração)

O direcionamento de conteúdo no HoloLens (1º gen) é feito principalmente com o vetor [olhar](gaze.md) (um raio controlado pela posição e rotação da cabeça). Isso fornece uma forma de entrada direta para o usuário que precisa de pouco ensinando. No entanto, os usuários têm dificuldade em usar um centro desmarcado de olhar para direcionamento preciso para que um cursor garanta que os usuários saibam o ponto em que estão se concentrando no momento. 


## <a name="positioning"></a>Posicionamento

Em geral, o indicador deve ser movido em aproximadamente uma proporção de 1:1 com movimento de cabeçalho. Há alguns casos em que o lucro (aumentar ou diminuir visivelmente a movimentação) pode ser usado como um mecânico intencional, mas causará problemas para os usuários se for usado inesperadamente (Observe que há um pequeno bit de "retardo" recomendado para o cursor para evitar problemas com exibir conteúdo totalmente bloqueado). No entanto, as experiências devem ser "honestas" na representação da posição do cursor – se a suavidade, Magnetism, obter ou outros efeitos estiverem incluídos, o sistema ainda deverá mostrar o cursor onde quer que o entendimento do sistema seja, com esses efeitos incluídos. O cursor é a maneira do sistema informar ao usuário o que eles podem ou não interessam, não a maneira de informar o sistema ao usuário.

O indicador deve, teoricamente, bloquear em profundidade a quaisquer elementos que o usuário possa plausívelr de destino. Isso pode significar o bloqueio de superfície se houver alguma malha de [mapeamento espacial](spatial-mapping.md) ou o bloqueio para a profundidade de qualquer elemento de interface do usuário "flutuante", para ajudar o usuário a entender o que eles podem interagir em tempo real.

## <a name="cursor-design-principles"></a>Princípios de design do cursor

### <a name="always-present"></a>Sempre presente
* É recomendável que o cursor esteja sempre presente.
* Se o usuário não conseguir localizar o cursor, ele será perdido.
* Exceções a isso são instâncias em que um cursor fornece uma experiência de qualidade inferior para o usuário. Um exemplo é quando um usuário está assistindo a um vídeo. O cursor se torna indesejável neste ponto como está no meio do vídeo o tempo todo. Esse é um cenário em que você pode considerar tornar o cursor visível somente quando o usuário tiver a mão indicando um desejo de agir. Caso contrário, ele não será visível no vídeo.

### <a name="cursor-scale"></a>Escala do cursor
* O cursor não deve ser maior do que os destinos disponíveis, permitindo que os usuários interajam com facilidade e exibam o conteúdo.
* Dependendo da experiência que você criar, dimensionar o cursor à medida que o usuário procura também é uma consideração importante. Por exemplo, à medida que o usuário fica mais distante em sua experiência, talvez o cursor não se torne muito pequeno, de modo que ele se perca.
* Ao dimensionar o cursor, considere a possibilidade de aplicar uma animação suave a ela à medida que ela é dimensionada, dando-lhe uma sensação orgânica.
* Evite obstruir o conteúdo. Os hologramas são o que torna a experiência fácil de memorizar e o cursor não deve ser retirado delas.

### <a name="directionless-cursor"></a>Cursor com direção
* Embora não haja uma forma de cursor à direita, recomendamos que você use uma forma sem direção como uma Torus ou outra coisa. Um cursor que aponta em alguma direção (por exemplo: um cursor de seta tradicional) pode confundir o usuário para sempre verificar dessa forma.
* Uma exceção a isso é quando se usa o cursor para comunicar a instrução de interação ao usuário. Por exemplo, ao dimensionar hologramas no Shell Holographic do Windows, o cursor inclui temporariamente setas que ajudam a instruir o usuário sobre como mover sua mão para dimensionar o holograma.

### <a name="look-and-feel"></a>Aparência
* Um cursor com formato de rosca ou Torus funciona para muitos aplicativos.
* Escolha uma cor e forma que melhor represente a experiência que você está criando.
* Os cursores estão especialmente sujeitos à [separação de cores](hologram-stability.md#color-separation).
* Um cursor pequeno com opacidade equilibrada mantém-o informativo sem a predominante da hierarquia visual.
* Seja Cognizant de usar sombras ou realces por trás do cursor, pois eles podem obstruir o conteúdo e desviar da finalidade.
* Os cursores devem alinhar e Hug as superfícies em seu aplicativo, isso dará ao usuário a sensação de que o sistema pode ver onde estão olhando, mas também que o sistema está ciente de seus arredores.
* Por exemplo, no sistema operacional Windows Holographic, o cursor está alinhado às superfícies do mundo do usuário, criando uma sensação de conscientização do mundo, mesmo quando o usuário não está olhando diretamente para um holograma.
* Bloquear magneticamente o cursor para um elemento interativo quando estiver dentro do próximo proximidade. Isso pode ajudar a melhorar a confiança que o usuário irá interagir com esse elemento quando executar uma ação de seleção.

### <a name="visual-cues"></a>Indicações visuais
* Há muitas informações em nosso mundo e com os hologramas que estamos adicionando mais informações. Um cursor é uma ótima maneira de se comunicar com o usuário o que é importante.
* Se sua experiência estiver concentrada em um único holograma, talvez o cursor alinhe e Hugs apenas esse holograma e altere a forma quando você sair desse holograma. Isso pode transmitir ao usuário que o holograma é especial e pode interagir com ele.
* Se seu aplicativo usar o mapeamento espacial, o cursor poderá ser alinhado e Hug cada superfície que vê. Isso fornece comentários aos usuários que o HoloLens e seu aplicativo podem ver seu espaço.
* Essas coisas ajudam a reforçar o fato de que os hologramas são reais e em nosso mundo. Eles ajudam a preencher a lacuna entre o real e o virtual.
* Tenha uma ideia do que o cursor deve fazer quando não há hologramas ou superfícies na exibição. Colocá-lo em uma distância predeterminada na frente do usuário é uma opção.

## <a name="cursor-feedback"></a>Comentários do cursor

Como mencionamos, é uma boa prática ter o cursor sempre presente, pois você pode usar o cursor para transmitir algumas partes importantes de informações.

### <a name="possible-actions"></a>Ações possíveis
* Como o usuário está nuvens em um holograma e o cursor está nesse holograma, você pode usar o cursor para transmitir possíveis ações nesse holograma.
* Você pode exibir um ícone no cursor que o usuário pode, por exemplo, comprar esse item ou talvez dimensionar esse holograma. Ou até mesmo algo tão simples como o holograma pode ser tocado.
* Somente adicione informações extras sobre o cursor se isso significa algo para o usuário. Caso contrário, os usuários talvez não percebam as alterações de estado ou ficam confusos com o cursor.

### <a name="input-state"></a>Estado de entrada
* Poderíamos usar o cursor para exibir o estado de entrada do usuário. Por exemplo, podemos exibir um ícone informando ao usuário se o sistema vê seu estado de mão. Isso informará ao usuário que o aplicativo sabe que o usuário está pronto para agir.
* Também poderíamos usar o cursor para fazer com que o usuário saiba que há um comando de voz disponível. Ou, talvez, alterar a cor do cursor momentaneamente para informar ao usuário que o comando de voz foi ouvido pelo sistema.

Esses diferentes Estados de cursor podem ser implementados de maneiras diferentes. Você pode implementar esses Estados diferentes modelando o cursor como um computador de estado. Por exemplo:
* Estado ocioso é onde você mostra o cursor padrão.
* Estado pronto é quando você detecta a mão do usuário na posição pronta.
* O estado de interação é quando o usuário está executando uma interação específica.
* O estado de ações possíveis é quando você transmite possíveis ações que podem ser executadas em um holograma.

Você também pode implementar esses Estados em uma maneira que permite que você possa exibir ativos de arte diferentes quando diferentes Estados forem detectados.

## <a name="going-cursor-free"></a>Indo "sem cursor"

A criação sem um cursor é recomendada apenas quando o sentido do imersão é um componente-chave de uma experiência, e as interações que envolvem o direcionamento (por meio de olhar e gesto) não exigem uma ótima precisão. O sistema ainda deve atender às necessidades que normalmente são atendidas por um cursor, fornecendo aos usuários comentários contínuos sobre a compreensão do sistema de seus direcionamentos e ajudando-os a comunicar com segurança suas intenções ao sistema. Isso pode ser alcançado por meio de outras alterações de estado perceptível.

## <a name="see-also"></a>Consulte também
* [Gestos](gestures.md)
* [Focar direcionamento](gaze-targeting.md)

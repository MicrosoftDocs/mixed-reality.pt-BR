---
title: Cursores
description: Um cursor, ou indicador de vetor de direcionamento, fornece comentários contínuos para o usuário entender o que compreende HoloLens sobre suas intenções.
author: thetuvix
ms.author: alexturn, thgable
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1º gen), 2 HoloLens, realidade mista, cursores, direcionamento, olhar, gestos
ms.openlocfilehash: cdedcaffabe0f90e7956fdb19a7b85e202fcf403
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590931"
---
# <a name="cursors"></a>Cursores

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).


Um cursor, ou indicador de seu vetor atual de direcionamento, fornece comentários contínuos para o usuário entender onde o HoloLens acredita que seu foco está no momento. O cursor permite que o usuário para entender seu direcionamento atual de ponto e enviará uma resposta atua como comentários para indicar qual área, holograma ou ponto de entrada. É o digital representação de onde o dispositivo compreende a atenção do usuário para ser (mesmo que não pode ser o mesmo que determinando nada sobre suas intenções).

Comentários fornecidos pelo cursor oferece aos usuários a capacidade de prever como o sistema responde, use esse sinal como comentários para comunicar melhor suas intenções ao dispositivo e, por fim, ser mais seguros sobre suas interações.

## <a name="hololens-1st-gen"></a>HoloLens (1ª geração)

Direcionamento de conteúdo no HoloLens (1º gen) é feito principalmente com o [olhares](gaze.md) vetor (um raio controlado pela posição e rotação do head). Isso fornece um formulário de entrada direta para o usuário que precisa de ensino pouco. No entanto, os usuários têm dificuldade em usar um centro desmarcado de olhar para o direcionamento preciso, portanto, um cursor garante que os usuários saibam o ponto em que eles estão visando atualmente. 


## <a name="positioning"></a>Posicionamento

Em geral, o indicador deve mover em aproximadamente uma proporção de 1:1 com movimentação do cabeçote. Há alguns casos em que o ganho (aumentando ou diminuindo o movimento visivelmente) pode ser usado como uma oficina intencional, mas causará problemas para os usuários se usado inesperadamente (Observe que há uma pequena parte do 'lag' recomendado para o cursor evitar problemas com exibição totalmente bloqueado conteúdo). Mais importante é que experiências devem ser "honestas" na representação da posição do cursor - se a suavização, magnetismo, ganho, no entanto, ou outros efeitos são incluídos, o sistema ainda deve mostrar o cursor onde quer que seja a compreensão do sistema da posição, com aqueles efeitos incluídos. O cursor é a maneira do sistema de informando ao usuário o que eles podem ou não é possível interagir com, não o caminho do usuário informar o sistema.

O indicador deve bloquear o ideal é que em camadas para quaisquer elementos que o usuário pode direcionar plausível. Isso pode significar a superfície de bloqueio se não houver algumas [mapeamento espacial](spatial-mapping.md) malha ou bloqueio para a profundidade de quaisquer elementos de interface do usuário "flutuantes", para ajudar o usuário a entender o que eles podem interagir com em tempo real.

## <a name="cursor-design-principles"></a>Princípios de design de cursor

### <a name="always-present"></a>Sempre presente
* É recomendável que o cursor está sempre presente.
* Se o usuário não é possível localizar o cursor, em seguida, elas são perdidas.
* As exceções a isso são instâncias em que ter um cursor fornece uma experiência de qualidade inferior para o usuário. Um exemplo é quando um usuário está assistindo a um vídeo. O cursor se transforma indesejável neste ponto, como ele está no meio do vídeo o tempo todo. Isso é um cenário onde você pode considerar fazer o cursor estará visível apenas quando o usuário tem sua mão indicando um desejo de agir. Caso contrário, ele não é visível no vídeo.

### <a name="cursor-scale"></a>Escala de cursor
* O cursor deve ser maior do que os destinos disponíveis, permitindo que os usuários interagem com facilmente e exibir o conteúdo.
* Dependendo da experiência que você cria, escalando o cursor, conforme o usuário procura ao redor também é uma consideração importante. Por exemplo, como o usuário se parece mais distante em sua experiência talvez o cursor não deve se tornar muito pequeno, de modo que seu perdido.
* Quando o cursor de dimensionamento, considere a aplicação de uma animação suave a ela conforme é dimensionado, dando a ele uma sensação orgânica.
* Evite obstruindo o conteúdo. Hologramas fazem com que a experiência fácil de lembrar e não deve estar demorando o cursor para longe-los.

### <a name="directionless-cursor"></a>Cursor sem direção
* Embora não haja nenhum uma forma de cursor para a direita, é recomendável que você use uma forma sem direção, como uma rosca ou alguma outra coisa. Um cursor que aponta em alguns direção (ex: um cursor de seta tradicional) pode confundir o usuário sempre tem essa aparência.
* Uma exceção a isso é ao usar o cursor para comunicar-se a instrução de interação ao usuário. Por exemplo, ao escalar hologramas no shell do Windows Holographic, o cursor temporariamente inclui setas que ajudam a orientar o usuário sobre como mover sua mão para dimensionar o holograma.

### <a name="look-and-feel"></a>Aparência
* A forma de uma rosca ou rosca funciona de cursor para muitos aplicativos.
* Escolha uma cor e forma que melhor representa a experiência que você está criando.
* Os cursores são especialmente propensos a [separação de cores](hologram-stability.md#color-separation).
* Um cursor pequeno com opacidade equilibrada mantém informativo sem dominar a hierarquia visual.
* Estar ciente de como usar sombras ou destaques do seu cursor como elas podem obstruir o conteúdo e for distraí-lo da finalidade.
* Cursores devem se alinhar à e unir as superfícies em seu aplicativo, isso concederá ao usuário uma sensação de que o sistema pode ver onde eles estão procurando, mas também que o sistema está ciente do seu ambiente.
* Por exemplo, no SO Windows Holographic, o cursor alinha as superfícies do mundo do usuário, criando uma sensação de reconhecimento do mundo, mesmo quando o usuário não estiver examinando diretamente um holograma...
* Bloqueio magneticamente o cursor para um elemento interativo quando ele estiver em proximidade imediata. Isso pode ajudar a melhorar a confiança que o usuário irá interagir com esse elemento ao executar uma ação de seleção.

### <a name="visual-cues"></a>Indicações visuais
* Há muitas informações em nosso mundo e com hologramas estamos adicionando mais informações. Um cursor é uma ótima maneira de se comunicar ao usuário o que é importante.
* Se a sua experiência se concentra em um único holograma, em seguida, talvez o cursor alinha e o ponteiro só que holograma e alterações de forma quando você olha para longe desse holograma. Isso pode transmitir para um usuário que o holograma é especial e eles podem interagir com ele.
* Se seu aplicativo usa mapeamento espacial, o cursor pode alinhar e unir cada superfície que ele vê. Isso fornece comentários aos usuários que HoloLens e seu aplicativo poderá ver seu espaço.
* Essas coisas ajudam a reforçar o fato de que hologramas são reais e em nosso mundo. Eles ajudam a preencher a lacuna entre real e virtual.
* Ter uma ideia do que o cursor deve fazer quando não há nenhum hologramas ou trazer à tona no modo de exibição. Colocando-o em uma distância predeterminada na frente do usuário é uma opção.

## <a name="cursor-feedback"></a>Comentários do cursor

Como já mencionamos, é recomendável ter o cursor sempre estar presente, como você pode usar o cursor para transmitir alguns dos bits de informações importantes.

### <a name="possible-actions"></a>Ações possíveis
* Conforme o usuário é Observação em um holograma e o cursor estiver sobre esse holograma, você pode usar o cursor para transmitir as ações possíveis em que holograma.
* Você pode exibir um ícone no cursor que o usuário pode comprar por exemplo o item ou talvez dimensionáveis que holograma. Ou, até mesmo algo tão simples, como o holograma pode ser ligado no.
* Adicione informações extras no cursor somente se ela significa algo para o usuário. Caso contrário, os usuários também não podem observar as alterações de estado ou se confundir com o cursor.

### <a name="input-state"></a>Estado de entrada
* Poderíamos usar o cursor para exibir o estado de entrada do usuário. Por exemplo, podemos pode exibir um ícone informando ao usuário se o sistema de ver seu estado de mão. Isso instruirá o usuário que o aplicativo sabe que o usuário está pronto para agir.
* Também poderíamos usar o cursor para tornar o ciente de que há um comando de voz do usuário. Ou talvez alterar a cor do cursor momentaneamente para informar ao usuário que o comando de voz foi ouvido pelo sistema.

Esses estados diferentes de cursor podem ser implementados de maneiras diferentes. Você pode implementar esses estados diferentes ao modelar o cursor, como uma máquina de estado. Por exemplo: 
* Estado ocioso é onde você pode mostrar o cursor padrão.
* Estado pronto é quando você tiver detectado mão do usuário na posição pronta.
* Estado de interação é quando o usuário está executando uma interação específica.
* Estado de ações possíveis é quando você transmite ações possíveis que podem ser executadas em um holograma.

Você também pode implementar esses estados de maneira capaz de capa, de modo que você pode exibir ativos de arte diferentes quando diferentes estados são detectados.

## <a name="going-cursor-free"></a>Vai "cursor livre"

Projetando sem um cursor é recomendado somente quando o sentido de imersão é um componente fundamental de uma experiência e interações que envolvem o direcionamento (por meio de olhar e gesto) não exigem grande precisão. O sistema ainda deve atender às necessidades que são normalmente atendidas por um cursor entanto – fornecendo aos usuários com comentários contínuos na compreensão do sistema de seu direcionamento e ajudando a eles se comuniquem com confiança suas intenções ao sistema. Isso pode ser que pode ser obtido por meio de outras alterações de estado perceptível.

## <a name="see-also"></a>Consulte também
* [Gestos](gestures.md)
* [Mantenha o foco de direcionamento](gaze-targeting.md)

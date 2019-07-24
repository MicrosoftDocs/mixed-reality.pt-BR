---
title: Módulo lunar
description: O LunarModule é um aplicativo de exemplo de software livre dos laboratórios de design de realidade misturada da Microsoft. Com este projeto, você pode aprender a estender os gestos de base do Hololens com o acompanhamento de duas mãos e a entrada do controlador Xbox, criar objetos reativos para o mapeamento de superfície e o plano, localizando e implementando sistemas de menu simples.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, aplicativos de exemplo, design, HoloLens
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516030"
---
# <a name="lunar-module"></a>Módulo lunar

>[!NOTE]
>Este artigo discute um exemplo exploratório que criamos nos laboratórios de [design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde compartilhamos nossas aprendeções e sugestões para o desenvolvimento de aplicativos de realidade misturada. Nossos artigos e códigos relacionados ao design irão evoluir à medida que fizermos novas descobertas.

O [módulo lunar](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) é um aplicativo de exemplo de código-fonte aberto dos laboratórios de design de realidade misturada da Microsoft. Com este projeto, você pode aprender a estender os gestos de base do Hololens com o acompanhamento de duas mãos e a entrada do controlador Xbox, criar objetos reativos para o mapeamento de superfície e o plano, localizando e implementando sistemas de menu simples. Todos os componentes do projeto estão disponíveis para uso em suas próprias experiências de aplicativo de realidade misturada.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Reconsiderando experiências clássicas para a realidade mista do Windows

Alto na atmosfera, uma pequena que sobrou de remessa do módulo Apollo pesquisa metodicamente o terreno irregular abaixo. Nosso piloto Fearless é uma área de aterrissagem adequada. A descendente é árdua, mas felizmente, essa jornada foi feita muitas vezes antes...

![Interface original da Atari lander lunar 1979](images/640px-atari-lunar-lander.png)<br>
*Interface original da Atari lander lunar 1979*

[Lunar Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) é um clássico, em que os jogadores tentam fazer um piloto de uma lua Lander em um ponto simples de terreno lunar. Qualquer pessoa nasceu na 70 tem mais chances de horas em um horário comercial com seus olhos colados com esse vetor entregue plummeting do céu. Como um player navega pelo seu envio para uma área de aterrissagem desejada, o terreno é dimensionado para revelar cada vez mais detalhes. Sucesso significa o patamar dentro do limite seguro de velocidade horizontal e vertical. Os pontos são concedidos para o tempo gasto e o combustível restante, com um multiplicador com base no tamanho da área de aterrissagem.

Além do jogo, a época de partida dos jogos trouxe inovação constante de esquemas de controle. Do joystick e das configurações de botão mais simples de 4 vias (visto no icônico [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) para os esquemas altamente específicos e complicados vistos no final anos 90 e 00s (como aqueles em simuladores de golfe e emissores de trilho). O esquema de entrada usado na máquina lander lunar é particularmente intrigante por dois motivos: moderação e imersão.

![Console de Atari lunar Lander](images/atariconsole.png)<br>
*Console Atari lunar Lander*

Por que Atari e tantas outras empresas de jogos decidem reconsiderar a entrada?

Um criança percorrendo um intrigada será naturalmente o mais novo computador flashiest. Mas o lunar Lander apresenta um mecânico de entrada romance que me esgotou da sua escala.

O lander lunar usa dois botões para girar o envio para a esquerda e para a direita e uma **alavanca de Thrustmaster** para controlar a quantidade de Thrustmaster que o navio produz. Essa alavanca dá aos usuários um determinado nível de astúcia que um joystick regular não pode fornecer. Também é um componente comum às ferramentas cockpit de aviação modernas. Atari queria lander lunar para aprofundar o usuário na sensação de que eles estavam na verdade, realizando um piloto de um módulo lunar. Esse conceito é conhecido como **tactile imersão**.

TACTILE imersão é a experiência de comentários de sensor de execução de ações de redundante. Nesse caso, a ação repetitiva de ajustar a alavanca de limitação e a rotação que nossos olhos veem e nossos ouvidos ouvem, ajuda a conectar o jogador ao ato de pouso de uma entrega na superfície da lua. Esse conceito pode ser vinculado ao conceito de psicológica de "Flow". Onde um usuário é totalmente absorvido em uma tarefa que tem a combinação certa de desafio e recompensa, ou ainda mais simplesmente, eles estão "na zona".

De forma improvada, o tipo mais proeminente de imersão em realidade misturada é imersão espacial. O ponto total da realidade misturada é nos enganar a acreditar que esses objetos digitais existem no mundo real. Estamos sintetizando hologramas em nossos arredores, imersos espacialmente em ambientes e experiências inteiros. Isso não significa que ainda podemos empregar outros tipos de imersão em nossas experiências, assim como Atari fez com tactile imersão no lunar Lander.

## <a name="designing-with-immersion"></a>Criando com imersão

Como podemos aplicar tactile imersão a uma atualização volumétricos sequência para o Atari clássico? Antes de lidar com o esquema de entrada, a construção de jogos para espaço tridimensional precisa ser resolvida.

![Visualizando o mapeamento de superfície no HoloLens](images/surfacemapping.png)<br>
*Visualizando o mapeamento espacial no HoloLens*

Aproveitando o ambiente de um usuário, nós efetivamente temos opções de terrenos infinitas para o patamar do nosso módulo lunar. Para tornar o jogo mais parecido com o título original, um usuário poderia potencialmente manipular e colocar os pads de pouso de diversas dificuldades em seu ambiente.

![Pilotando o módulo lunar](images/640px-lm-hero.jpg)<br>
*Pilotando o módulo lunar*

Exigir que o usuário Aprenda o esquema de entrada, controle a remessa e faça com que um pequeno destino seja um grande alvo é muito a ser solicitado. Uma experiência de jogo bem-sucedida apresenta a combinação certa de desafio e recompensa. O usuário deve ser capaz de escolher um nível de dificuldade, com o modo mais fácil simplesmente exigir que o usuário alcance com êxito uma área definida pelo usuário em uma superfície verificada pelo HoloLens. Quando um usuário sai do jogo, ele pode então se ajustar à dificuldade que eles veem.

### <a name="adding-input-for-hand-gestures"></a>Adicionando entrada para gestos de mão

A entrada base do HoloLens tem apenas dois gestos – [toque e flor](gestures.md). Os usuários não precisam lembrar nuances contextuais ou uma lista lavanderia de gestos específicos que tornam a interface da plataforma versátil e fácil de aprender. Embora o sistema possa expor apenas esses dois gestos, o HoloLens como um dispositivo é capaz de rastrear duas mãos ao mesmo tempo. Nosso ode para lunar Lander é um [aplicativo de imersão](app-model.md) que significa que temos a capacidade de estender o conjunto base de gestos para aproveitar duas mãos e adicionar nossa própria agradavelmente tactile significa para a navegação de módulo lunar.

Voltando ao esquema de controle original, **precisávamos resolver para Thrustmaster e Rotation**. A limitação é a rotação no novo contexto adiciona um eixo adicional (tecnicamente, dois, mas o eixo Y é menos importante para a aterrissagem). Os dois movimentos de envio distintos naturalmente se prestam para serem mapeados para cada mão:

![Gesto de tocar e arrastar para girar Lander em todos os três eixos](images/module-handdrag.gif)<br>
*Gesto de tocar e arrastar para girar Lander em todos os três eixos*

**Thrustmaster**

A alavanca no computador original de alta prioridade mapeada para uma escala de valores, quanto mais alta a alavanca foi movida, mais o ThrustMaster foi aplicado à remessa. Uma nuance importante para destacar aqui é que o usuário pode tirar seu alcance do controle e manter um valor desejado. Podemos usar efetivamente o comportamento de toque e arrastar para obter o mesmo resultado. O valor de Thrustmaster começa em zero. O usuário toca e arrasta para aumentar o valor. Nesse ponto, eles poderiam deixar de continuar a mantê-lo. Qualquer alteração de valor de gesto de toque e arrastar seria o Delta do valor original.

**Rotação**

Isso é um pouco mais complicado. Ter os botões "girar" de Holographic para tocar para uma experiência terrível. Não há um controle físico para aproveitar, portanto, o comportamento deve vir da manipulação de um objeto que representa o Lander ou com o próprio Lander. Nós reunimos um método usando TAP-and-arraste, que permite que um usuário "empurre e empurre" com eficiência na direção que desejam que ele tenha uma face. Sempre que um usuário toca e se mantém, o ponto no espaço em que o gesto foi iniciado se torna a origem para rotação. Arrastar da origem converte o Delta da tradução do lado (X, Y, Z) e o aplica ao Delta dos valores de rotação do Lander. Ou, mais simplesmente, arrastando para *a esquerda <-> direito, < > para baixo, encaminhar <-> de volta em espaços gira a remessa de acordo*.

Como o HoloLens pode acompanhar duas mãos, a rotação pode ser atribuída à mão à direita enquanto o ThrustMaster é controlado pela esquerda. Astúcia é o fator determinante para o sucesso neste jogo. A *sensação* dessas interações é a prioridade mais alta absoluta. Especialmente no contexto de tactile imersão. Um envio que reage muito rapidamente seria desnecessariamente difícil de ser direcionado, enquanto um pouco lento exigiria que o usuário "Envie por push e puxe" na entrega por um longo período de tempo estranho.

### <a name="adding-input-for-game-controllers"></a>Adicionando entrada para controladores de jogo

Enquanto os gestos de mão no HoloLens fornecem um método romance de controle refinado, ainda há uma certa falta de comentários de tactile "verdadeiro" que você obtém de controles analógicos. Conectar um controlador de jogo do Xbox permite voltar essa sensação de física, aproveitando os pentes de controle para manter o controle refinado.

Há várias maneiras de aplicar o esquema de controle relativamente direto ao controlador Xbox. Como estamos tentando permanecer o mais próximo possível da configuração original, o **Thrustmaster** mapeia melhor para o botão disparador. Esses botões são controles analógicos, o que significa que eles têm mais do que Estados simples *e* desligados, eles realmente respondem ao grau de pressão colocados neles. Isso nos dá um constructo semelhante à **alavanca de Thrustmaster**. Ao contrário do jogo original e do gesto de mão, esse controle recortará a Thrustmaster do navio quando um usuário parar de colocar a pressão no gatilho. Ele ainda dá ao usuário o mesmo grau de astúcia que o jogo de Altova original.

![Thumbstick à esquerda é mapeada para guinada e roll, a Thumbstick direita é mapeada para pitch e roll](images/thumbsticksidebyside.gif)<br>
*O Thumbstick esquerdo é mapeado para guinada e roll; o Thumbstick direito é mapeado para pitch e roll*

O Thumbsticks duplo se presta naturalmente ao controle da rotação de remessa. Infelizmente, há 3 eixos nos quais a remessa pode girar e duas Thumbsticks que dão suporte a dois eixos. Essa incompatibilidade significa que um Thumbstick controla um eixo; ou há uma sobreposição de eixos para o Thumbsticks. A solução anterior acabou de se sentir "quebrada", já que Thumbsticks de forma inerente mesclar seus valores X e Y locais. A última solução exigiu algum teste para descobrir quais eixos redundantes se sentem mais naturais. O exemplo final usa  a guinada e *roll* (eixos Y e x) para o Thumbstick esquerdo, e *pitch* e *roll* (eixos Z e x) para a Thumbstick direita. Isso parecia que a rolagem  mais natural parece ser bem emparelhada com *desvio* e *inclinação*. Como uma observação adicional, o uso de Thumbsticks para *roll* também ocorre para dobrar o valor de rotação; é muito divertido ter os loops Lander.

Este aplicativo de exemplo demonstra como o reconhecimento espacial e tactile imersão podem alterar significativamente uma experiência graças às modalidades de entrada extensível da realidade mista do Windows. Embora o lunar Lander possa estar perto de 40 anos de idade, os conceitos expostos com esse pequeno octógono-com-pernas residirão sempre. Ao imaginar o futuro, por que não examinar o passado?

## <a name="technical-details"></a>Detalhes técnicos

Você pode encontrar scripts e pré-fabricados para o aplicativo de exemplo de módulo lunar no [GitHub de laboratórios de design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Linville de Addison</b><br>Designer de UX@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Controladores de movimentos](motion-controllers.md)
* [Gestos](gestures.md)
* [Tipos de aplicativos de realidade misturada](types-of-mixed-reality-apps.md)

---
title: Módulo Lunar
description: LunarModule é um aplicativo de exemplo de código-fonte aberto de laboratórios de Design de realidade misturada da Microsoft. Com este projeto, você pode aprender como estender os gestos de base dos Hololens com o acompanhamento de duas mãos e controlador do Xbox de entrada, criar objetos que são reativos para mapeamento de superfície e localização do plano e implementar sistemas de menu simples.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows misto realidade, HoloLens de aplicativos, Design, de exemplo
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590434"
---
# <a name="lunar-module"></a>Módulo Lunar

>[!NOTE]
>Este artigo descreve um exemplo de análise exploratório que criamos na [laboratórios de Design de realidade misturada](https://github.com/Microsoft/MRDesignLabs_Unity), um lugar onde podemos compartilhar nossos aprendizados sobre e sugestões para desenvolvimento de aplicativos de realidade de misto. Nossos artigos relacionados ao design e código evolui à medida que fizermos novas descobertas.

[Módulo Lunar](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) é um aplicativo de exemplo de código-fonte aberto de laboratórios de Design de realidade misturada da Microsoft. Com este projeto, você pode aprender como estender os gestos de base dos Hololens com o acompanhamento de duas mãos e controlador do Xbox de entrada, criar objetos que são reativos para mapeamento de superfície e localização do plano e implementar sistemas de menu simples. Todos os componentes do projeto estão disponíveis para uso em suas próprias experiências de aplicativo de realidade misturada.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Repensando experiências clássicas para o Windows Mixed Reality

Up alta na atmosfera, um navio pequeno que sobrou do módulo Apollo metodicamente pesquisas denteado terreno abaixo. Nosso projeto-piloto fearless identifica uma área de aterrissagem adequado. O descendente é árdua, mas felizmente, essa jornada foi feita antes de muitas vezes...

![Interface original do 1979 Lunar Lander do Atari](images/640px-atari-lunar-lander.png)<br>
*Interface original do 1979 Lunar Lander do Atari*

[Lander Lunar](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) é uma clássico arcade onde jogadores tentam criar um piloto um lander lua em um simples ponto de terreno lunar. Alguém nasceu na década de 1970 provavelmente passou horas em um arcade com seus olhos colados para esta remessa de vetor decaindo rapidamente do céu. Como um player navega seu ship em direção a uma área de aterrissagem desejada o terreno é dimensionado para revelar progressivamente mais detalhadamente. O sucesso significa inicial dentro do limite seguro de velocidade horizontal e vertical. Os pontos são concedidos para o tempo gasto inicial e o restante de combustível, com um multiplicador de acordo com o tamanho da área de aterrissagem.

Além do jogo, era de jogos arcade trouxe constante inovação de esquemas de controle. Das configurações mais simples de joystick e botão de 4 vias (visto no icônico [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) para os esquemas altamente específicos e complicados vistos no final dos anos 90 e 00s (como aqueles em simuladores de Golfe e atiradores de trilho). O esquema de entrada usado na máquina Lander Lunar é particularmente interessante por dois motivos: moderar imersão e apelo.

![Console do Lunar Lander do Atari arcade](images/atariconsole.png)<br>
*Console do Atari Lunar Lander arcade*

Por que Atari e muitas outras empresas jogos decidiu repensar a entrada?

Uma criança percorrendo um arcade naturalmente será ser intrigada com os mais recente e flashiest de máquina. Mas Lander Lunar apresenta uma oficina de entrada novel que me chamou a atenção na multidão.

Lander Lunar usa dois botões para trocar a nave esquerda e direita e um **foco alavanca** para controlar a quantidade de foco que produz a nave. Essa alavanca oferece aos usuários um certo nível de sofisticação que um joystick regular não pode fornecer. Também é um componente comum para cabines de aviação modernos. Atari queria Lunar Lander para que o usuário na sensação de que eles foram de fato um piloto de um módulo lunar. Esse conceito é conhecido como **imersão táteis**.

Imersão táteis é a experiência de comentários de aparelhos de executar ações repetitivas. Nesse caso, a ação repetitiva de ajustar a alavanca de limitação e a rotação que seus olhos veriam e ouvir nossos ouvidos, ajuda a conectar-se o jogador para o ato de um navio de aterrissagem na superfície da lua. Esse conceito pode ser vinculado ao psicológico conceito de "fluxo". Em que um usuário é totalmente absorvido em uma tarefa que tem a mistura certa de desafio e a recompensa, ou em termos mais simples, eles são "na"zona.

Sem dúvida, o tipo mais proeminente de imersão na realidade mista é imersão espacial. O ponto de realidade misturada é enganar sozinhos acreditar que esses objetos digitais existem no mundo real. Podemos estiver sintetizar hologramas em nossos arredores espacialmente imersos no experiências e ambientes inteiros. Isso não significa que podemos ainda não é possível empregar outros tipos de imersão em nossas experiências assim como Atari fez com táteis imersão no Lander Lunar.

## <a name="designing-with-immersion"></a>Criação de imersão

Como talvez aplicamos táteis imersão para uma continuação atualizada, volumétricas o Atari clássico? Antes de lidar com o esquema de entrada, a construção de jogo para espaço dimensional de 3 precisa ser resolvida.

![Visualizando o mapeamento de superfície no HoloLens](images/surfacemapping.png)<br>
*Visualizando o mapeamento espacial no HoloLens*

Aproveitando o ambiente do usuário, temos efetivamente opções de terreno infinito para nosso módulo lunar de aterrissagem. Para tornar o jogo mais parecido com o título original, um usuário poderia potencialmente manipular e colocar os painéis de aterrissagem das dificuldades de variáveis em seu ambiente.

![Pilotando o módulo Lunar](images/640px-lm-hero.jpg)<br>
*Pilotando o módulo Lunar*

Exigir que o usuário saiba o esquema de entrada, controlar a nave e ter um destino pequeno cheguem em é pedir muito. Uma experiência de jogo bem-sucedida de recursos a combinação certa de desafio e a recompensa. O usuário deve ser capaz de escolher um nível de dificuldade, com o modo mais fácil simplesmente exigir que o usuário com êxito cheguem em uma área definida pelo usuário em uma superfície verificados pelo HoloLens. Depois que um usuário obtém o travamento do jogo, eles podem, em seguida, ligue a dificuldade como acharem melhor.

### <a name="adding-input-for-hand-gestures"></a>Adicionando entrada para gestos de mão

Entrada de base do HoloLens tem apenas dois gestos - [ar toque e Bloom](gestures.md). Os usuários não precisam se lembrar de nuances contextuais ou uma lista de gestos específicos que torna a interface da plataforma versátil e fácil de aprender. Enquanto o sistema só pode expor esses gestos de dois, HoloLens, como um dispositivo é capaz de controlar duas mãos ao mesmo tempo. Nossos ode para Lander Lunar é um [aplicativo imersivo](app-model.md) que significa que temos a capacidade de estender o conjunto de gestos para aproveitar duas mãos e adicionar nossos própria fantasticamente táteis meios para navegação de módulo lunar base.

Examinando o esquema de controle original, **precisávamos resolver para o foco e a rotação**. A limitação é a rotação no novo contexto adiciona um eixo adicional (tecnicamente, duas, mas o eixo Y é menos importante para inicial). Os movimentos de remessa distintos duas naturalmente se presta a ser mapeado para cada mão:

![Toque e gesto para girar lander em todos os três eixos de arrastar](images/module-handdrag.gif)<br>
*Toque e gesto para girar lander em todos os três eixos de arrastar*

**Foco**

A alavanca na máquina arcade original mapeada para uma escala de valores, maior será a alavanca foi movida o foco mais foi aplicado à nave. Uma nuance importante ressaltar aqui é que o usuário pode levar sua mão do controle e manter um valor desejado. Podemos efetivamente usar o comportamento de toque e arraste para alcançar o mesmo resultado. O valor de foco começa em zero. O usuário tocar e arrasta para aumentar o valor. Nesse ponto pode permitir que vá para mantê-lo. Qualquer alteração de valor de gesto de tocar e arrastar seria o delta do valor original.

**Rotação**

Isso é um pouco mais complicado. Tendo holográfica botões "girar" tocar o faz para obter uma experiência terrível. Há não um controle físico aproveitar, portanto, o comportamento deve vir de manipulação de um objeto que representa o lander, ou com o lander em si. Criamos um método usando o toque e arrastar que permite que um usuário efetivamente "push e pull"-lo na direção eles querem enfrentam. Qualquer momento em que um usuário toca e segura, o ponto no espaço em que o gesto foi iniciado se torna a origem para a rotação. Arrastando da origem converte o delta de tradução da mão (X, Y, Z) e aplica-se para o delta dos valores de rotação do lander. Ou, mais simplesmente, *arrastar esquerda <> – logo, <> – para baixo, para frente <> – em espaços gira a nave adequadamente*.

Uma vez que o HoloLens podem acompanhar duas mãos, rotação pode ser atribuída para a direita enquanto o foco é controlado à esquerda. Sofisticação é o fator determinante para o sucesso nesse jogo. O *sentir* dessas interações é a mais alta prioridade absoluta. Especialmente no contexto de imersão táteis. Um navio que reaja rápido demais seria desnecessariamente difícil conduzam, enquanto um muito lento exigiria que o usuário "por push e pull" na nave por um incômoda longo período de tempo.

### <a name="adding-input-for-game-controllers"></a>Adicionando entrada para controladores de jogos

Embora os gestos de mão no HoloLens fornecem um método novel de um controle refinado, ainda há determinada falta de comentários táteis 'true' obtida da analog controles. Conectar-se um controlador de jogo do Xbox permite trazer de volta nesse sentido de relacionamento físico tem posto, aproveitando os cartões de controle para manter o controle refinado.

Há várias maneiras de aplicar o esquema de controle relativamente simples para o controlador do Xbox. Uma vez que estamos tentando permanecer o mais próximo do arcade original configurar possível, **motivação** mapeia o melhor para o botão de gatilho. Esses botões são controles analógicos, que significa que eles têm mais de simples *e desativar* afirma, eles realmente responder ao grau de pressão para colocar neles. Isso nos dá uma construção semelhante como o **foco alavanca**. Ao contrário do jogo original e o gesto de mão, esse controle será recortar o foco da nave depois que um usuário para exercendo pressão sobre o gatilho. Ele ainda fornece ao usuário o mesmo grau de sofisticação como fez o jogo arcade original.

![Analógico esquerdo é mapeado para Yaw e reverter, direcional direita é mapeado para vende e reverter](images/thumbsticksidebyside.gif)<br>
*Analógico esquerdo é mapeado para yaw e reverter; alavanca direcional direita é mapeado para vende e reverter*

Os alavancas direcionais duplas naturalmente se presta à rotação controladora de remessa. Infelizmente, há 3 eixos em que a nave pode girar e duas alavancas direcionais que dão suporte a dois eixos. Essa incompatibilidade significa um analógico controles um eixo; ou, não há sobreposição dos eixos para o alavancas direcionais. A solução anterior terminou se sentindo "interrompida", pois alavancas direcionais inerentemente seu local de mesclagem valores X e Y. A última solução necessários alguns testes para encontrar quais eixos redundantes se sentir mais natural. O exemplo final usa *yaw* e *roll* (eixos Y e X) para o analógico esquerdo, e *tom* e *roll* (eixos Z e X) para a direita direcional. Isso achamos mais natural quanto *roll* parece independentemente emparelhar bem com *yaw* e *tom*. Como uma observação adicional, usando os dois alavancas direcionais para *roll* também acontece dobrar o valor de rotação; é muito divertido para ter o lander fazer loops.

Este aplicativo de exemplo demonstra como espacial reconhecimento e imersão táteis significativamente pode alterar uma experiência graças ao modalidades de entrada extensíveis do Windows Mixed Reality. Enquanto o Lunar Lander pode ser se aproximando 40 anos de idade, os conceitos expostos com pouca octógono com legs ficará ativo para sempre. Quando imaginando o futuro, por que não parecem passado?

## <a name="technical-details"></a>Detalhes técnicos

Você pode encontrar scripts e pré-fabricados para o aplicativo de exemplo do módulo Lunar sobre o [GitHub de laboratórios de Design de realidade mista](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>Designer de UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Controladores de movimento](motion-controllers.md)
* [Gestos](gestures.md)
* [Tipos de aplicativos de realidade misturada](types-of-mixed-reality-apps.md)

---
title: Estudo de caso-usando som espacial em RoboRaid
description: O som espacial é um dos recursos mais empolgantes do Microsoft HoloLens, fornecendo uma maneira para os usuários perceberem o que está acontecendo em torno deles quando os objetos estão fora da linha de visão.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, RoboRaid, som espacial
ms.openlocfilehash: 1482c914d261cae698a1460873b217b0683cd16b
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181936"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Estudo de caso-usando som espacial em RoboRaid

Este artigo descreve os desafios exclusivos que a equipe de experiência do Microsoft HoloLens encontrou ao criar áudio para [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j), uma shooter da primeira pessoa de realidade mista.

## <a name="the-tech"></a>O Tech

O [som espacial](spatial-sound.md) é um dos recursos mais empolgantes do Microsoft HoloLens, fornecendo uma maneira para os usuários perceberem o que está acontecendo em torno deles quando os objetos estão fora da linha de visão.

No RoboRaid, o uso mais óbvio e eficaz de som espacial é alertar o jogador sobre algo que está acontecendo fora da visão periférica do usuário. Por exemplo, o violador pode entrar em qualquer uma das paredes digitalizadas na sala, mas se você não estiver voltado para o local onde está inserindo, poderá perder isso. Para alertá-lo sobre essa invasão, você ouvirá um pouco de áudio proveniente de onde o violador está entrando, o que lhe permite saber que você precisa agir rapidamente para interrompê-lo.

## <a name="behind-the-scenes"></a>Nos bastidores

O processo de criação de som espacial para aplicativos do HoloLens é tão novo e exclusivo e a falta de projetos passados a serem usados para referência pode levar a uma grande quantidade de riscos quando você encontrar um problema. Espero que esses exemplos de desafios de áudio que enfrentamos durante a criação de RoboRaid ajudarão você a criar áudio para seus próprios aplicativos.

### <a name="be-mindful-of-taxing-the-cpu"></a>Tenha o cuidado de concarregar a CPU

O som espacial pode ser exigente na CPU. Para uma experiência ocupada como o RoboRaid, era crucial manter as instâncias de som espacial de menos de oito em um determinado momento. Na maioria das vezes, era tão fácil quanto definir o limite de instâncias de eventos de áudio diferentes para que qualquer instância que aconteça após o limite ser atingido seja eliminada. Por exemplo, quando a geração de drones, seus Screams são limitados a três instâncias em um determinado momento. Considerando que apenas quatro drones podem ser geradas de uma só vez, três Screams são muito bem, já que não há como o cérebro pode acompanhar esse número de eventos de áudio semelhantes. Isso liberou recursos para outros eventos de som espaciais, como explosões de inimigo ou inimigos se preparando.

### <a name="rewarding-a-successful-dodge"></a>Recompensar um subexposição bem-sucedido

O dodging mecânico é um dos aspectos mais importantes do jogo em RoboRaid, e também algo que sentimos ser verdadeiramente exclusivos à experiência do HoloLens. Como tal, queríamos tornar as subexposiçãos bem-sucedidas muito compensadoras para o jogador. Temos o Doppler "Whizz-by" para soar bastante cedo no desenvolvimento. Inicialmente, meu plano era usar um loop e manipulá-lo em tempo real usando volume, densidade e filtro. A implementação para isso seria muito elaborada, portanto, antes de confirmar os recursos para criar isso, criamos um protótipo barato usando um ativo com o efeito Doppler inclusas em apenas para descobrir como ele parecia *. Nosso desenvolvimento de talentos fez isso para que esse ativo de whizzção reproduza exatamente 0,7 segundos antes que o Projectile tenha passado pelo ear do jogador e os resultados sejam realmente impressionantes! Não é necessário dizer que nós eliminoumos a solução mais complexa e implementamos o protótipo.

*(Para obter mais informações sobre como criar um ativo de áudio com o efeito de Doppler interno, consulte [100 whooshes em 2 minutos](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/).)*  
<br>
![dodging Projectile de um inimigo recompensa o jogador com um som Whizz-por satisfatório.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Sons ineficazes do ditching

Originalmente, queríamos reproduzir um som de explosão por trás do jogador após a subexposição bem-sucedida do inimigo Projectile, mas decidimos eliminar isso por vários motivos. Primeiro, não se sente tão eficiente quanto o SFX WHIZZ que usamos para a subexposição. No momento em que o Projectile atinge uma parede por trás de você, outra coisa teria ocorrido no jogo que iria muito mascarar esse som. Em segundo lugar, não tínhamos colisão no chão, portanto, não pudemos fazer a explosão brincar quando o Projectile atingir o andar em vez das paredes. E, finalmente, houve o custo de CPU do som espacial. O Scorpion inimigo de elite (um que pode ser rastreado dentro da parede) tem um ataque especial que emite cerca de oito projéteis. Além de não fazer uma grande confusão na mistura, ela também introduziu o horrível, pois estava atingindo a CPU muito difícil.

### <a name="communicating-a-hit"></a>Comunicando um problema

Um problema interessante que encontramos, que sentimos ser exclusivos da experiência de HoloLens, foi a dificuldade de se comunicar efetivamente com os jogadores que eles foram atingidos. O que torna uma experiência de realidade misturada bem-sucedida é a sensação de que a história está acontecendo para você. Isso significa que você deve acreditar que está combatendo uma invasão de robô alienígena em seu próprio espaço de vida.

Obviamente, os jogadores não sentirão nada quando chegarem, então tivemos que encontrar uma maneira de realmente convencer o jogador de que algo mau happed a eles. Em jogos convencionais, você pode ver uma animação que lhe permite saber que seu caractere levou um clique, ou a tela pode piscar vermelho e seu caractere pode Grunt um pouco. Como esses tipos de indicações não funcionam em uma experiência de realidade misturada, decidimos combinar a indicação visual com um som bem exagerado que indica que você teve danos. Eu criei um grande som e o fiz tão proeminente na mistura de que ele espatou tudo. Em seguida, para deixá-lo se destacar ainda mais, adicionamos um pequeno som de aviso como se uma sub-rotina nuclear estivesse afundando. 
<br>
![quando um jogador é atingido no RoboRaid, eles veem uma indicação visual, mas também recebem uma indicação de áudio exagerada que informa que eles levaram danos.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Obtendo som grande de alto-falantes pequenos

Os alto-falantes do HoloLens são pequenos e leves para atender às necessidades do dispositivo, portanto, você não pode esperar ouvir muito menos. Semelhante ao desenvolvimento de dispositivos Smart Phone ou de jogos de mão, os designers de som e os criadores precisam ser atentos ao conteúdo de frequência de seu áudio. Sempre crio sons ou escrevo música com o intervalo de frequência total, pois o desenvolvimento de fones de ouvido é uma opção para os usuários. No entanto, para garantir a compatibilidade com os alto-falantes do HoloLens, executo um teste ocasionalmente colocando um EQ no mestre de qualquer DAW em que eu esteja trabalhando. A configuração EQ consiste em um filtro de alta passagem em cerca de 600 a 700 Hz (não muito acentuada) e filtro de baixa Pass em cerca de 10K (muito acentuação). Isso deve dar a você uma ideia aproximada de como seus sons serão reproduzidos no dispositivo.

Se você estiver contando com os graves para dar a sensação de mudança de corda em suas músicas, poderá descobrir que sua música perde completamente o sentido da raiz quando você aplicar essa configuração de EQ. Para corrigir isso, adicionei outra camada ao baixo que é um Octave mais alto (com algumas harmônicas sofisticadas) e misturei a ti para obter o sentido da raiz de volta. Às vezes, usar distorção para acelerar as harmônicas fornecerá conteúdo de frequência suficiente no intervalo superior para fazer com que o nosso cérebro ache que há algo abaixo dele. Isso é verdadeiro para SFX como impactos, explosões ou sons por momentos especiais, como os supertipos de um chefe. Você realmente não pode contar com o low-end para dar ao jogador um sentido de impacto ou peso. Assim como acontece com música, o uso de distorção para dar um pouco de defragmentação definitivamente ajudou.

### <a name="making-your-audio-cues-stand-out"></a>Fazendo suas indicações de áudio se destacarem

Naturalmente, todos na equipe queriam Bombastic música, alta bombardeadores e explosões loucos; Mas eles também queriam ser capazes de ouvir a VoiceOver ou qualquer outra indicação de áudio de jogo crítico.

Em um jogo de console com uma gama completa de frequência, você tem mais opções para dividir as frequências dependendo da importância do som. No entanto, para RoboRaid, eu estava limitado no número de intervalos de frequências que eu poderia destacar de sons. Por exemplo, se você usar o filtro de baixa Pass e curvar muito da extremidade superior do espectro, não terá nada restante no som, pois não há muito menos.

Para tornar o RoboRaid Sound tão grande quanto ele pode no dispositivo, tivemos que reduzir o intervalo dinâmico da experiência inteira e fazer uso extensivo do pato criando uma hierarquia clara de importância para diferentes tipos de sons. Defini o pato de-2 a-6 dB, dependendo da importância. Pessoalmente, não gosto de um pato óbvio em jogos, por isso, passei muito tempo ajustando o tempo de fade in/out e a quantidade de atenuação de volume. Configuramos barramentos separados para som espacial, som não espacial, VO e barramento seco sem reverberação de música e, depois, criamos barramentos de prioridade muito alta, críticos e não críticos. Os ativos foram então configurados para ir para seus ônibus apropriados.

Espero que os profissionais de áudio por aí tenham tanta diversão e empolgante trabalhando em seus próprios aplicativos, como eu fiz para trabalhar em RoboRaid. Não posso esperar para ver (e ouvir!) o que os pessoal talentos fora da Microsoft virão para o HoloLens.

## <a name="do-it-yourself"></a>Faça você mesmo

Um truque que descobri para tornar determinados eventos (como explosões) um som "maior" — como eles estão preenchendo a sala — foi criar um ativo de mono para o som espacial e misturá-lo com um ativo estéreo 2D, a ser reproduzido em 3D. Isso faz um ajuste, pois ter muitas informações no conteúdo estéreo diminuirá a direcionalidade dos ativos do mono. No entanto, obter o equilíbrio certo resultará em grandes sons que levarão os jogadores a transformar seus cabeçotes na direção certa.

Você pode experimentar isso usando os ativos de áudio abaixo:

**Cenário 1**
1. Baixe [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) e defina para reprodução por meio de som espacial e atribua-o a um evento.
2. Baixe [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) e defina para reprodução em 2D estéreo e atribua ao mesmo evento acima. Como esses ativos são normalizados para o Unity, atenua o volume de ambos os ativos para que ele não seja recortado.
3. Jogue os dois sons juntos. Mude sua cabeça para sentir a sua espacial.

**Cenário 2**
1. Baixe [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) e defina para reprodução por meio de som espacial e atribua a um evento.
2. Execute este ativo por si só e compare-o com o evento do cenário 1.
3. Experimente um balanceamento diferente de arquivos mono e estéreo.



## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [RoboRaid para Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)

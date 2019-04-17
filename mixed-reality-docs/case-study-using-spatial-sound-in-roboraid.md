---
title: Estudo de caso - usando o som espacial RoboRaid
description: Som espacial é um dos recursos mais interessantes do Microsoft HoloLens, fornecendo uma maneira para que os usuários percebem que está acontecendo em torno delas quando objetos são fora de linha de visão.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, RoboRaid, som espacial
ms.openlocfilehash: 4bb050b4a4051c121c488ea38e150a8973bd7c04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589728"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Estudo de caso - usando o som espacial RoboRaid

Charles Sinex, áudio líder da equipe de experiência do Microsoft HoloLens, fala sobre os desafios únicos encontradas durante a criação de áudio para [RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j), shooter de primeira pessoa uma realidade misturada.

## <a name="the-tech"></a>O técnico

[Som espacial](spatial-sound.md) é um dos recursos mais interessantes do Microsoft HoloLens, fornecendo uma maneira para que os usuários percebem que está acontecendo em torno delas quando objetos são fora de linha de visão.

No RoboRaid, o uso mais óbvio e eficaz de som espacial é alertar o jogador para algo que esteja acontecendo fora de visão periférica do usuário. Por exemplo, o Breacher pode inserir de qualquer uma das paredes digitalizadas na sala, mas se você não estiver voltada para o local onde ele está inserindo, você poderá perdê-lo. Para alertá-lo para esta invasão, você ouvirá distinta de bits de áudio proveniente de onde está inserindo o Breacher, que permite que você saiba o que você precisará agir rapidamente para interrompê-lo.

## <a name="behind-the-scenes"></a>Nos bastidores

O processo de criação de som espacial para aplicativos do HoloLens é tão novo e exclusivo e a falta de projetos anteriores a ser usado para referência pode levar a muita head uma pequena quando você encontrar um problema. Esperamos que esses exemplos dos desafios áudio nós nos deparamos enquanto tornar RoboRaid ajudará você a que você crie áudio para seus próprios aplicativos.

### <a name="be-mindful-of-taxing-the-cpu"></a>Lembre-se de uma sobrecarga de CPU

Som espacial pode ser exigentes na CPU. Para obter uma experiência ocupada como RoboRaid foi crucial para manter as instâncias do som espacial em oito em um determinado momento. Na maior parte, foi tão fácil quanto configurar o limite de instâncias de eventos de áudio diferentes, de modo que todas as instâncias que ocorrer depois que o limite for atingido serão eliminadas. Por exemplo, ao geram drones, suas screams limitam a três instâncias em um determinado momento. Considerando que apenas cerca de quatro drones podem gerar ao mesmo tempo, três screams são muitos, pois não há seu cérebro pode manter o controle de que muitos eventos de áudio com som-semelhante. Isso liberaram o de outros eventos de som espaciais, como o inimigas explosões ou inimigos se preparando para levar.

### <a name="rewarding-a-successful-dodge"></a>Recompensando um dodge bem-sucedida

O mecânico dodging é um dos aspectos mais importantes do jogo no RoboRaid, além de algo que achávamos que era realmente exclusivo para a experiência do HoloLens. Como tal, queríamos fazer subexpõe bem-sucedida muito gratificante do Player. Temos o Doppler em razão "whizz-por" para parecer atraente bastante logo no início do desenvolvimento. Inicialmente, meu plano era usar um loop e manipulá-los em tempo real usando o volume, densidade e filtro. A implementação para isso seria muito elaborada, antes de confirmar os recursos para realmente criar isso, criamos um protótipo barato usando um ativo com o efeito do Doppler em razão embutidos apenas para descobrir como ele sentiu *. Nossos desenvolvedores talentosos feita a ele para que esse ativo por whizz seria reproduzir exatamente 0,7 segundos antes do projectile terá passado pelo ear do player e os resultados sentiram impressionantes! Obviamente, estamos eliminou a solução mais complexa e implementou o protótipo.

* * (Se você quiser obter mais informações sobre como criar um ativo de áudio com o efeito do Doppler em razão interno, check-out de um artigo pelo designer som chamado Charles Deenan [100 Whooshes em 2 minutos](http://designingsound.org/2010/02/charles-deenen-special-100-whooshes-in-2-minutes/).) *
<br>
![Com êxito, evitando projectile do inimigo uma recompensa o jogador com um som whizz por satisfatória.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Eliminação das ineficazes sons

Originalmente, tinha queríamos soar um detalhamento por trás do player depois que eles já subexposta com êxito o inimigo projectile, mas estamos decidiu eliminar isso por vários motivos. Primeiro, ele sentia tão eficaz quanto a usamos para o dodge whizz por SFX. No momento em que o projectile atinge uma parede atrás de você, outra coisa teria acontecido no jogo que seria muito muito máscara de som. Em segundo lugar, tínhamos colisão no chão, portanto, não foi possível obter o detalhamento seja executado quando o projectile a andar, em vez das paredes de ocorrências. E, finalmente, não havia o custo de CPU de som espacial. O inimigo Elite Scorpion (um que pode rastrear dentro da parede) tem um ataque especial que lança projéteis cerca de oito. Não apenas o que fez uma grande confusão na combinação, também introduziu barulho awful porque ele foi atingindo a CPU muito difícil.

### <a name="communicating-a-hit"></a>Comunicando-se uma ocorrência

Um problema interessante tivemos, que acreditamos que seja exclusivo da experiência do HoloLens, foi a dificuldade de comunicação eficiente aos jogadores que foi ativados. O que torna uma realidade misturada experiência bem-sucedida é a sensação que a história estiver acontecendo com você. Isso significa que você tem que acredita que combatem uma invasão de robô alienígena na sala de estar.

Players, obviamente, não se sentir nada quando eles são atingidos, portanto, precisamos encontrar uma maneira realmente convencer o player que algo ruim tinha happed a eles. Em jogos convencionais, você poderá ver uma animação que permite que você saiba seu caractere tiver obtido uma ocorrência, ou a tela pode piscar vermelho e seu caractere pode grunt um pouco. Como esses tipos de indicações não funcionam em uma experiência de realidade misturada, decidimos combinar a indicação visual com um som realmente exagerado indicando que você executou o dano. Criei um som grande e tornou tão proeminentes na combinação de que ele ducked tudo para baixo. Em seguida, para destacá-lo ainda mais, adicionamos um som de aviso curto como se uma sub-rotina nuclear foi recepção. 
<br>
![Quando um player é atingido em RoboRaid, eles ver uma indicação visual, mas também pode obter uma indicação de áudio exagerada informando tiradas com danos.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Obtendo big som dos alto-falantes pequeno

Alto-falantes do HoloLens são pequeno e leve atender às necessidades do dispositivo, portanto, você não pode esperar ouvir muito baixa gama. Semelhante ao desenvolvimento para Smartphones ou dispositivos de jogos portáteis, designers de som e compositores têm estar atento o conteúdo de frequência de seu áudio. Eu sempre sons de design ou gravar as músicas com um intervalo de frequência de completo porque o uso de fones de ouvido é uma opção para os usuários. No entanto, para garantir a compatibilidade com alto-falantes do HoloLens, posso executar um teste, ocasionalmente, colocando um EQ no mestre de qualquer DAW que estou trabalhando em. A configuração de EQ consiste em um filtro passa alta cerca de 600 para 700 Hz (não muito acentuada) e passa baixa de filtro em cerca de 10 K (muito acentuada). Que deve lhe dar uma ideia aproximada de como seu sons serão reprodução no dispositivo.

Se você está confiando na graves para dar a sensação de corda alterando em seus arquivos de música, você pode achar que seus arquivos de música completamente perde o sentido da raiz quando você aplicar essa configuração EQ. Para corrigir isso, adicionei outra camada para os graves que é uma oitava superior (com algumas harmônicas avançadas) e misto-lo para obter o sentido de voltar de raiz. Às vezes, o uso distorção em amp inscrever as harmônicas oferecerá conteúdo suficiente frequência no intervalo superior para tornar nosso cérebro pensar que há algo abaixo dela. Isso é verdadeiro para SFX como impactos, explosões ou sons para momentos especiais, como ataques de super um chefe. Você realmente não pode contar a low-end para dar o jogador uma ideia do impacto ou peso. Assim como acontece com música, usando distorção para dar um pouco de juntar definitivamente ajudou a.

### <a name="making-your-audio-cues-stand-out"></a>Tornando seus as indicações de áudio se destacam

Naturalmente, todos da equipe queriam bombastic música, armas altos e explosões loucos; mas também queria ser capaz de ouvir voiceover ou qualquer outras jogo críticos as indicações de áudio.

Em um jogo de console com uma gama completa de frequência, você tem mais opções para dividir as frequências dependendo da importância do som. Para RoboRaid, no entanto, eu estava limitado no número de intervalos de frequências que eu poderia curva-out de sons. Por exemplo, se você usar o filtro passa baixa e a curva em excesso da extremidade superior do espectro, você não terá qualquer coisa deixado no som porque não há muito baixa gama.

Para fazer RoboRaid som tão grande quanto possível no dispositivo, tivéssemos que diminuir o intervalo dinâmico de toda a experiência e faz uso extensivo de desviando, criando uma hierarquia clara de importância para diferentes tipos de sons. Eu defino o desviando de -2 para dB-6 dependendo da importância. Eu não gosto desviando óbvio em jogos, para que o passei muito tempo, ajuste o fade in/out de medição de tempo e a quantidade de atenuação de volume. Podemos configurar separados barramentos de som espacial, som não espaciais, VO e barramento dry sem reverberação para música, então criado barramentos de prioridade muito alta, críticas e não-críticas. Os ativos foram configurados para acessar seus ônibus apropriados.

Espero que profissionais de áudio por aí terá tanto diversão e empolgação trabalhando em seus próprios aplicativos, como eu fiz trabalhando em RoboRaid. Posso esperar para ver (e ouça!) o que as pessoas talentosas fora da Microsoft serão exibida com para o HoloLens.

## <a name="do-it-yourself"></a>Faça você mesmo

Um truque que descobri, certifique-se de eventos (como explosões) de som "maiores" — como eles estiverem enchendo sala — era criar um ativo de mono para o som espacial e combiná-lo com um ativo de estéreo 2D, para ser reproduzido em 3D. Levar algum ajuste, já que ter muitas informações no conteúdo estéreo diminuir a direcionalidade dos ativos mono. No entanto, obter o equilíbrio correto resulta em enormes sons que receberão os jogadores para ativar suas cabeças na direção certa.

Você pode tentar isso sozinho usando os ativos de áudio abaixo:

**Cenário 1**
1. Baixe [roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav) e definido como reprodução por meio de som espacial e atribuí-lo a um evento.
2. Baixe [roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav) e definido para a reprodução em estéreo 2D e atribuir o mesmo evento como acima. Porque esses ativos são normalizados para o Unity, atenuam volume de ambos os ativos para que ele não recortar.
3. Ambos os sons são executados em conjunto. Mova sua cabeça alternativa para se sentir como espacial que parece.

**Cenário 2**
1. Baixe [roboraid_enemy_explo_summed.wav](images/roboraid-enemy-explo-summed.wav) e definido como reprodução por meio de som espacial e atribuir a um evento.
2. Reproduzir esse ativo por si só e compará-lo para o evento do cenário 1.
3. Tente diferente saldo dos arquivos estéreo e mono.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Charles Sinex" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Charles Sinex</b><br>Engenheiro de áudio @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [RoboRaid para o Microsoft HoloLens](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)

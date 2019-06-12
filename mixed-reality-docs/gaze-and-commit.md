---
title: Foco com a cabeça e confirmação
description: Visão geral do modelo de entrada de foco com a cabeça e confirmação
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design
ms.openlocfilehash: d9eae3c0cfceba7c2c31425941dfce865f3aa609
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692307"
---
# <a name="head-gaze-and-commit"></a>Foco com a cabeça e confirmação
O foco com a cabeça e confirmação é um modelo de entrada que envolve o direcionamento do foco para um objeto com a cabeça apontando para a frente (direção da cabeça) e, em seguida, a execução de uma ação baseada nela com uma entrada secundária, como o gesto com a mão de fechar e abrir dedos indicador e polegar ou o comando de voz “Selecionar”. Ele é considerado um modelo de entrada "distante" com manipulação indireta, ou seja, é mais adequado para interagir com o conteúdo que está além do alcance dos braços.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Foco com a cabeça e confirmação</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</td>
        <td>➕ Opção alternativa</td>
    </tr>
</table>

## <a name="head-gaze"></a>Foco com a cabeça
Os headsets de realidade misturada usam a posição e a orientação da cabeça do usuário para determinar seu vetor de direção da cabeça. Você pode considerar isso como um laser que aponta para a frente, diretamente entre os olhos do usuário. Essa é uma aproximação bastante grosseira da direção para a qual o usuário está olhando. Seu aplicativo pode interseccionar esse raio com objetos virtuais ou do mundo real e desenhar um cursor nessa localização para informar o usuário do que ele está direcionando o foco.

Além do foco com a cabeça, alguns headsets de realidade misturada, como o HoloLens 2, incluem sistemas de acompanhamento ocular que produzem um vetor de foco com o olhar. Isso fornece uma medida refinada da direção para a qual o usuário está olhando. É possível criar interações de foco e confirmação usando o foco com o olhar, mas isso vem com um conjunto muito diferente de restrições de design, que será abordado separadamente no [artigo sobre acompanhamento ocular](eye-tracking.md).

## <a name="commit"></a>Confirmação
Depois de direcionar o foco para um objeto ou um elemento de interface do usuário, o usuário pode interagir com ele ou "clicar" nele usando uma entrada secundária. Isso é conhecido como a etapa de confirmação do modelo. Os seguintes métodos de confirmação são compatíveis:

- Gesto de fechar e abrir dedos indicador e polegar
- Emitir o comando de voz "Selecionar" ou um dos comandos de voz direcionados
- Pressionar o único botão em um [HoloLens Clicker](hardware-accessories.md#hololens-clicker)
- Pressionar o botão 'A' em um gamepad Xbox
- Pressionar o botão 'A' em um Controle Adaptável Xbox

### <a name="head-gaze-and-air-tap-gesture"></a>Foco com a cabeça e gesto de fechar e abrir dedos indicador e polegar
Fechar e abrir dedos indicador e polegar é um gesto de tocar feito com a mão levantada. Para fazer um gesto de fechar e abrir dedos indicador e polegar, levante o dedo indicador apontando-o para cima e, em seguida, faça um gesto de pinçagem com o polegar e levante o dedo indicador novamente para soltá-lo. No HoloLens 1, o gesto de fechar e abrir dedos indicador e polegar é a entrada secundária mais comum.

![Dedo apontado para cima e, em seguida, um movimento de toque ou clique](images/readyandpress.jpg)<br>

O gesto de fechar e abrir dedos indicador e polegar também está disponível no HoloLens 2 e foi suavizado comparado à versão original. Agora quase todos os tipos de gestos de pinçagem são compatíveis, desde que a mão esteja levantada e parada. Isso facilita muito para os usuários aprenderem e fazerem o gesto.  Esse novo gesto de fechar e abrir dedos indicador e polegar substitui o antigo por meio da mesma API e, portanto, os aplicativos existentes obterão o novo comportamento automaticamente após a recompilação para o HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Foco com a cabeça e comando de voz "Selecionar"
Os comandos de voz são um dos principais métodos de interação de Realidade Misturada. Eles fornecem um mecanismo muito eficiente de "mãos livres" para controlar o sistema. Há diferentes tipos de modelos de interação de voz:

- O comando genérico "Selecionar", que permite executar um acionamento ou uma confirmação por "clique" como uma entrada secundária.
- Comandos de objeto, como "Fechar" ou "Aumentar", que permitem executar e confirmar uma ação como uma entrada secundária.
- Comandos globais, como "Ir para o início", que não exigem um alvo.
- Interfaces de usuário de conversa ou entidades, como a Cortana, que têm uma funcionalidade de Idioma Natural de IA.
- Comandos personalizados

Para encontrar mais detalhes e uma lista abrangente de comandos disponíveis e como usá-los, confira nossas diretrizes de [comandos de voz](voice-design.md).


### <a name="head-gaze-and-hololens-clicker"></a>Foco com a cabeça e HoloLens Clicker
O HoloLens Clicker é o primeiro dispositivo periférico criado especificamente para o HoloLens e está incluído no HoloLens 1 Development Edition. O HoloLens Clicker permite que um usuário faça um clique com movimentos mínimos com as mãos e uma confirmação como uma entrada secundária. O HoloLens Clicker conecta-se ao HoloLens 1 ou 2 usando o BTLE (Bluetooth de Baixa Energia).

![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
*HoloLens Clicker*

Mais informações e instruções sobre como emparelhar o dispositivo podem ser encontradas [aqui](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Foco com a cabeça e Controle sem Fio Xbox
O Controle sem Fio Xbox permite executar um acionamento por "clique" como uma entrada secundária usando o botão A. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar pelo sistema e controlá-lo. Caso você deseje personalizar o controle, use o Aplicativo de Acessórios Xbox para configurar o Controle sem Fio Xbox.

![Controle sem Fio Xbox](images/xboxcontroller.jpg)<br>
*Controle sem Fio Xbox*

[Como emparelhar um controle Xbox com o computador](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Foco com a cabeça e Controle Adaptável Xbox
Desenvolvido principalmente para atender às necessidades de jogadores com mobilidade limitada, o Controle Adaptável Xbox é um hub unificado para dispositivos que ajuda a tornar a Realidade Misturada mais acessível.

O Controle Adaptável Xbox permite executar um acionamento por "clique" como uma entrada secundária usando o botão A. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar pelo sistema e controlá-lo. Caso você deseje personalizar o controle, use o Aplicativo de Acessórios Xbox para configurar o Controle Adaptável Xbox.

![Controle Adaptável Xbox](images/xbox-adaptive-controller-devices.jpg)<br>
*Controle Adaptável Xbox*

Conecte dispositivos externos, como comutadores, botões, montagens e joysticks, para criar uma experiência personalizada de controles exclusivamente sua. As entradas de botão, thumbstick e gatilho são controladas com dispositivos adaptativos conectados por meio de entradas de 3,5 mm e portas USB.

![Portas do Controle Adaptável Xbox](images/xbox-adaptive-controller-ports.jpg)<br>
*Portas do Controle Adaptável Xbox*

[Instruções para emparelhar o dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Mais informações disponíveis no site do Xbox</a>


## <a name="design-guidelines"></a>Diretrizes de design
> [!NOTE]
> Mais diretrizes específicas ao design de foco [em breve](index.md).

## <a name="head-gaze-targeting"></a>Direcionamento de foco com a cabeça
Todas as interações baseiam-se na capacidade de um usuário direcionar seu foco para o elemento com o qual deseja interagir, independentemente da modalidade de entrada. No Windows Mixed Reality, isso geralmente é feito com o foco do usuário.
Para permitir que um usuário trabalhe com uma experiência bem-sucedida, o entendimento calculado do sistema da intenção de um usuário e a intenção real do usuário devem estar os mais alinhados possíveis. Na medida em que o sistema interpreta as ações pretendidas do usuário corretamente, a satisfação e o desempenho melhoram.


## <a name="target-sizing-and-feedback"></a>Dimensionamento e comentários sobre o alvo
O vetor de foco demonstrou repetidamente ser utilizável para o direcionamento refinado, mas geralmente funciona melhor para o direcionamento bruto (adquirindo, de certa forma, alvos maiores). Os tamanhos mínimos do alvo de 1 a 1,5 grau devem permitir ações bem-sucedidas do usuário na maioria dos cenários, embora os alvos de 3 graus normalmente permitam uma maior velocidade. Observe que o tamanho do alvo escolhido pelo usuário é efetivamente uma área 2D até mesmo para elementos 3D – qualquer que seja a projeção que esteja voltada para eles deverá ser a área de alvo. O fornecimento de alguma indicação evidente de que um elemento está "ativo" (ao qual o usuário está direcionando o foco) é extremamente útil – isso pode incluir tratamentos como efeitos de "focalização" visíveis, destaques de áudio ou cliques ou alinhamento claro de um cursor com um elemento.

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho ideal do alvo em uma distância de 2 metros*

![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-640px.jpg)<br>
*Um exemplo de realce de um objeto direcionado por foco*

## <a name="target-placement"></a>Posicionamento do alvo
Em geral, os usuários não encontrarão elementos de interface do usuário posicionados muito acima ou muito abaixo de seu campo de visão, concentrando a maior parte de sua atenção nas áreas em torno de seu foco principal (em geral, aproximadamente no nível dos olhos). O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar. Dada a tendência dos usuários de se concentrarem em uma área visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), o agrupamento de elementos de interface do usuário na medida em que eles estejam relacionados conceitualmente pode aproveitar os comportamentos de encadeamento da atenção de item a item conforme um usuário move o foco por uma área. Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.

![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Como melhorar os comportamentos de direcionamento
Se a intenção do usuário de direcionar o foco para algo puder ser determinada (ou aproximada), poderá ser muito útil aceitar tentativas "quase certas" na interação como se elas tivessem sido direcionadas corretamente. Há diversos métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:

### <a name="head-gaze-stabilization-gravity-wells"></a>Estabilização do foco com a cabeça ("poços gravitacionais")
Isso deve estar ligado na maior parte do tempo ou todo o tempo. Essa técnica remove as tremulações naturais da cabeça/do pescoço que os usuários possam ter. Além disso, o movimento devido a comportamentos de visão/fala.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo mais próximo
Eles funcionam melhor em áreas com conteúdo interativo esparso. Se houver uma grande probabilidade de que você determine com o que um usuário estava tentando interagir, você poderá complementar suas habilidades de direcionamento apenas supondo algum nível de intenção.

### <a name="backdatingpostdating-actions"></a>Ações de antedatar/pós-datar
Esse mecanismo é útil para tarefas que exigem velocidade. Quando um usuário se move por uma série de manobras de direcionamento/ativação com velocidade, pode ser útil supor uma intenção e permitir etapas ausentes para executar ações em alvos que o usuário tinha em foco um pouco antes ou depois do toque (50 ms antes/depois do que foi eficaz no início do teste).

### <a name="smoothing"></a>Suavização
Esse mecanismo é útil para movimentos de caminhos, reduzindo leve tremulação/tremor devido às características de movimentação natural da cabeça. Durante a suavização em movimentos de caminhos, aplique a suavização por tamanho/distância de movimentos em vez de ao longo do tempo

### <a name="magnetism"></a>Magnetismo
Esse mecanismo pode ser considerado uma versão mais geral dos algoritmos de "Vínculo mais próximo" – desenhar um cursor em direção a um alvo ou apenas aumentar os hitboxes (seja visivelmente ou não) conforme os usuários se aproximam de prováveis alvos, usando algum conhecimento sobre o layout interativo para uma melhor abordagem da intenção do usuário. Isso pode ser particularmente eficiente para alvos pequenos.

### <a name="focus-stickiness"></a>Adesão do foco
Ao determinar a quais elementos interativos nas proximidades o foco deve ser dado, forneça um desvio para o elemento que tem o foco atualmente. Isso ajudará a reduzir os comportamentos de alternância de foco instável durante a flutuação em um ponto médio entre dois elementos com ruído natural.


## <a name="composite-gestures"></a>Gestos compostos
Os aplicativos podem reconhecer mais do que apenas toques individuais. Pela combinação do toque, do gesto de manter e de soltar com o movimento da mão, gestos compostos mais complexos podem ser feitos. Esses gestos compostos ou de alto nível baseiam-se nos dados de entrada espaciais de baixo nível (do fechar e abrir dedos indicador e polegar ao abrir a mão) aos quais os desenvolvedores têm acesso.

### <a name="air-tap"></a>Fechar e abrir dedos indicador e polegar
O gesto de fechar e abrir dedos indicador e polegar (bem como os outros gestos abaixo) responde somente a um toque específico. Para detectar outros toques, como menu ou segurar, o aplicativo precisa usar diretamente as interações de baixo nível descritas na seção de gestos de dois componentes principais acima.

### <a name="tap-and-hold"></a>Fechar e abrir dedos indicador e polegar e manter
Manter é simplesmente manter a posição do dedo para baixo no gesto de fechar e abrir dedos indicador e polegar. A combinação dos gestos de fechar e abrir dedos indicador e polegar e manter permite uma variedade de interações mais complexas de "clicar e arrastar" quando usada em conjunto com a movimentação do braço, como pegar um objeto em vez de ativá-lo, ou interações secundárias "mousedown", como mostrar um menu de contexto.
No entanto, tenha cuidado ao projetar o uso desse gesto, pois os usuários podem estar propensos a relaxar suas posturas de mão no decorrer de qualquer gesto estendido.

### <a name="manipulation"></a>Manipulação
Os gestos de manipulação poderão ser usados para mover, redimensionar ou girar um holograma quando você desejar que o holograma responda com uma proporção 1:1 às movimentações de mão do usuário. Um uso para essas movimentações de 1:1 é permitir que o usuário desenhe ou pinte no mundo.
O direcionamento inicial de um gesto de manipulação deve ser feito pelo foco ou apontando. Depois que o gesto de fechar e abrir dedos indicador e polegar e manter for iniciado, qualquer manipulação do objeto será tratada pelos movimentos da mão, liberando o usuário para olhar em volta durante a manipulação.

### <a name="navigation"></a>Navegação
Os gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar por widgets de interface do usuário, como menus radiais. Feche e abra os dedos indicador e polegar e mantenha para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizado em torno do pressionamento inicial. Você pode mover a mão ao longo do eixo X, Y ou Z de um valor -1 a 1, sendo 0 o ponto de partida.
A navegação pode ser usada para criar gestos de rolagem ou zoom contínuo baseados em velocidade, semelhante à rolagem de uma interface do usuário 2D com um clique no botão do meio do mouse e, em seguida, a movimentação do mouse para cima e para baixo.

A navegação com trilhos refere-se à capacidade de reconhecer movimentos em determinado eixo até certo limite ser atingido nesse eixo. Isso só é útil quando o movimento em mais de um eixo é habilitado em um aplicativo pelo desenvolvedor, por exemplo, se um aplicativo é configurado para reconhecer gestos de navegação nos eixos X e Y, mas também no eixo X especificado com trilhos. Nesse caso, o sistema reconhecerá os movimentos de mão no eixo X, desde que eles permaneçam dentro de um trilho imaginário (guia) no eixo, X caso o movimento de mão também ocorra no eixo Y.

Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolagem, zoom ou operações de arrastar dentro do aplicativo. Isso injeta toques de dedo virtuais no aplicativo para simular gestos de toque do mesmo tipo. Os usuários podem selecionar quais dessas ações ocorrem alternando entre as ferramentas na barra acima do aplicativo, selecionando o botão ou falando 'Ferramenta de <Rolagem/Arrastar/Zoom>'.

[Mais informações sobre gestos compostos](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconhecedores de gestos

Uma vantagem do uso do reconhecimento de gestos é que você pode configurar um reconhecedor de gestos apenas para os gestos que o holograma direcionado atualmente pode aceitar. A plataforma fará apenas a desambiguidade necessária para distinguir esses gestos compatíveis específicos. Dessa forma, um holograma que só é compatível com o gesto de fechar e abrir dedos indicador e polegar pode aceitar qualquer período de tempo entre o pressionamento e a liberação, enquanto um holograma que é compatível com o gesto de fechar e abrir dedos indicador e polegar e manter pode promover o toque a um gesto de manter após o limite de tempo em que o toque é mantido.

## <a name="hand-recognition"></a>Reconhecimento de mão
O HoloLens reconhece gestos de mão acompanhando a posição de uma ou das duas mãos visíveis para o dispositivo. O HoloLens vê as mãos quando elas estão no estado pronto (parte posterior da mão voltada para você com o dedo indicador para cima) ou no estado pressionado (parte posterior da mão voltada para você com o dedo indicador para baixo). Quando as mãos estiverem em outras poses, o HoloLens as ignorará.
Para cada mão detectada pelo HoloLens, você pode acessar sua posição (sem orientação) e seu estado pressionado. Conforme a mão se aproxima da borda do quadro de gesto, você também recebe um vetor de direção, que você pode mostrar ao usuário para que ele saiba como mover a mão para retorná-la ao local em que o HoloLens possa vê-la.

## <a name="gesture-frame"></a>Quadro de gesto
Para os gestos no HoloLens, a mão precisa estar em um “quadro de gesto”, em um alcance no qual as câmeras de detecção de gesto possam vê-la de forma adequada (muito aproximadamente, do nariz até a cintura e entre os ombros). Os usuários precisam ser treinados nessa área de reconhecimento para o sucesso da ação e para seu próprio conforto (muitos usuários inicialmente presumirão que o quadro de gesto está dentro de sua visão por meio do HoloLens e manterão os braços levantados de forma desconfortável para interagir com ele). Ao usar o HoloLens Clicker, suas mãos não precisam estar dentro do quadro de gesto.

No caso de gestos contínuos em particular, há algum risco de que os usuários movam as mãos para fora do quadro de gesto durante o gesto intermediário (ao mover um objeto holográfico, por exemplo) e percam seu resultado pretendido.

Há três coisas que você deve considerar:

- Educação do usuário sobre a existência do quadro de gesto e os limites aproximados (isso é ensinado durante a instalação do HoloLens).

- Notificação dos usuários quando seus gestos estiverem se aproximando ou saírem dos limites do quadro de gesto em um aplicativo, na medida em que um gesto perdido levará a resultados indesejados. As pesquisas mostram as principais qualidades de um sistema de notificação como esse e o shell do HoloLens oferece um bom exemplo desse tipo de notificação (visual, no cursor central, indicando a direção na qual o limite está sendo ultrapassado).

- As consequências de sair dos limites do quadro do gesto deverão ser minimizadas. Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite, mas não revertido. Por exemplo, se um usuário estiver movendo algum objeto holográfico em uma sala, a movimentação deverá parar quando o quadro de gesto for ultrapassado, mas não retornar ao ponto de partida. Assim, o usuário poderá se frustrar, mas poderá mais rapidamente entender os limites e não precisar reiniciar suas ações pretendidas completas sempre.


## <a name="see-also"></a>Consulte também
* [Manipulação direta com as mãos](direct-manipulation.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Comando de voz](voice-design.md)






---
title: Foco com a cabeça e confirmação
description: Visão geral do modelo de entrada de foco com a cabeça e confirmação
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design
ms.openlocfilehash: aeca5ceacf5ae350aa06cb58cc68162f885f6d78
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387674"
---
# <a name="head-gaze-and-commit"></a>Foco com a cabeça e confirmação
Head-olhar e commit é um modelo de entrada que envolve o direcionamento de um objeto com a direção da sua cabeça apontando para a frente (direção do cabeçalho) e, em seguida, agindo com uma entrada secundária, como o toque do ar do gesto de mão ou o comando de voz selecionado. Ele é considerado um modelo de entrada distante com manipulação indireta, o que significa que ele é melhor usado para interagir com conteúdo que está além dos braços.

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
Os headsets de realidade misturada usam a posição e a orientação da cabeça do usuário para determinar seu vetor de direção da cabeça. Você pode considerar isso como um laser que aponta para a frente, diretamente entre os olhos do usuário. Essa é uma aproximação bastante grosseira da direção para a qual o usuário está olhando. Seu aplicativo pode interceptar esse raio com objetos virtuais ou do mundo real e desenhar um cursor nesse local para permitir que o usuário saiba o que eles têm como destino no momento.

Além do Head olhar, alguns headsets de realidade misturada, como o HoloLens 2, incluem sistemas de controle de olhos que produzem um vetor olhar de olho. Isso fornece uma medida refinada da direção para a qual o usuário está olhando. É possível criar olhar e confirmar interações usando olho olhar. Mas isso é fornecido com um conjunto muito diferente de restrições de design, que serão abordadas separadamente no [artigo de olho-olhar](eye-tracking.md).

## <a name="commit"></a>Confirmação
Depois de direcionar um objeto ou elemento de interface do usuário, o usuário pode interagir ou clicar nele usando uma entrada secundária. Isso é conhecido como a etapa de confirmação do modelo. Os seguintes métodos de confirmação são compatíveis:

- Gesto de toque do ar
- Fale com o comando de voz, selecione ou um dos comandos de voz de destino
- Pressione um único botão em um [clicador de HoloLens](hardware-accessories.md#hololens-clicker)
- Pressione o botão ' A ' em um gamepad do Xbox
- Pressione o botão ' A ' em um controlador adaptável do Xbox

### <a name="head-gaze-and-air-tap-gesture"></a>Foco com a cabeça e gesto de fechar e abrir dedos indicador e polegar
Fechar e abrir dedos indicador e polegar é um gesto de tocar feito com a mão levantada. Para executar um toque de ar, aumente o seu indicador para a posição pronta, aperte o polegar e aumente o seu dedo de índice de volta para o lançamento. No HoloLens (1ª gen), o Air Tap é a entrada secundária mais comum.

![Dedo apontado para cima e, em seguida, um movimento de toque ou clique](images/readyandpress.jpg)<br>

O toque de ar também está disponível no HoloLens 2. Ele foi relaxado da versão original. Quase todos os tipos de pinçações agora têm suporte, contanto que a mão esteja na vertical e mantendo ainda. Isso facilita muito para os usuários aprenderem e fazerem o gesto. Esse novo toque de ar substitui o antigo por meio da mesma API, de modo que os aplicativos existentes terão o novo comportamento automaticamente após a recompilação para o HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Foco com a cabeça e comando de voz "Selecionar"
A linha de comando de voz é um dos principais métodos de interação na realidade misturada. Ele fornece um mecanismo sem intervenção e eficiência para controlar o sistema. Há diferentes tipos de modelos de interação de voz:

- O comando genérico SELECT que executa um clique actuation ou Commit como uma entrada secundária.
- Comandos de objeto como fechar ou torná-los maiores são executados e confirmados em uma ação como uma entrada secundária.
- Commnads global como ir para iniciar não requer um destino.
- As interfaces de usuário de conversa ou entidades como Cortana têm um recurso de linguagem natural de ia.
- Comandos personalizados

Para obter mais detalhes, bem como uma lista comprenhesive de comandos disponíveis e como usá-los, confira nossas diretrizes de [comando de voz](voice-design.md) .


### <a name="head-gaze-and-hololens-clicker"></a>Foco com a cabeça e HoloLens Clicker
O clicador de HoloLens é o primeiro dispositivo periférico criado especificamente para o HoloLens. Ele está incluído com o HoloLens (1ª gen) Development Edition. O clicador do HoloLens permite que um usuário clique com o movimento mínimo e confirme como uma entrada secundária. O clico do HoloLens se conecta ao HoloLens (1º gen) ou ao HoloLens 2 usando o Bluetooth de baixa energia (BTLE).

![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
*HoloLens Clicker*

Mais informações e instruções sobre como emparelhar o dispositivo podem ser encontradas [aqui](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Foco com a cabeça e Controle sem Fio Xbox
O controlador sem fio do Xbox executa um clique actuation como uma entrada secundária usando o botão ' A '. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar pelo sistema e controlá-lo. Se você quiser personalizar o controlador, use o aplicativo Xbox accesories para configurar o controlador sem fio do Xbox.

![Controle sem Fio Xbox](images/xboxcontroller.jpg)<br>
*Controle sem Fio Xbox*

[Como emparelhar um controle Xbox com o computador](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Foco com a cabeça e Controle Adaptável Xbox
Projetado principalmente para atender às necessidades de jogos com mobilidade limitada, o controlador adaptável do Xbox é um hub unificado para dispositivos que ajuda a tornar a realidade misturada mais acessível.

O controlador adaptável do Xbox executa um clique actuation como uma entrada secundária usando o botão ' A '. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema. Se você quiser personalizar o controlador, use o aplicativo Xbox accesories para configurar o controlador adaptável do Xbox.

![Controle Adaptável Xbox](images/xbox-adaptive-controller-devices.jpg)<br>
*Controle Adaptável Xbox*

Conecte dispositivos externos, como comutadores, botões, montagens e joysticks, para criar uma experiência de controlador personalizada que seja exclusivamente sua. As entradas de botão, Thumbstick e gatilho são controladas com dispositivos assistenciais conectados por meio de conectores de 3,5 mm e portas USB.

![Portas do Controle Adaptável Xbox](images/xbox-adaptive-controller-ports.jpg)<br>
*Portas do Controle Adaptável Xbox*

[Instruções para emparelhar o dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Mais informações disponíveis no site do Xbox</a>


## <a name="design-guidelines"></a>Diretrizes de design
> [!NOTE]
> Mais diretrizes específicas ao design de foco [em breve](index.md).

## <a name="head-gaze-targeting"></a>Direcionamento de foco com a cabeça
Todas as interações baseiam-se na capacidade de um usuário direcionar seu foco para o elemento com o qual deseja interagir, independentemente da modalidade de entrada. No Windows Mixed Reality, isso geralmente é feito com o foco do usuário.
Para permitir que um usuário trabalhe com uma experiência com êxito, a compreensão calculada do sistema da intenção de um usuário e a intenção real do usuário devem ser alinhadas o mais próximo possível. Na medida em que o sistema interpreta as ações pretendidas do usuário corretamente, a satisfação e o desempenho melhoram.


## <a name="target-sizing-and-feedback"></a>Dimensionamento e comentários sobre o alvo
O vetor olhar foi mostrado repetidamente para ser usado para direcionamento fino, mas geralmente funciona melhor para direcionamento bruto, adquirindo destinos um pouco maiores. Os tamanhos de destino mínimos de 1 a 1,5 graus permitem ações de usuário bem-sucedidas na maioria dos cenários, embora os destinos de 3 graus geralmente permitam maior velocidade. Observe que o tamanho do alvo escolhido pelo usuário é efetivamente uma área 2D até mesmo para elementos 3D – qualquer que seja a projeção que esteja voltada para eles deverá ser a área de alvo. Fornecer uma indicação evidente de que um elemento é "ativo" (que o usuário está direcionando para ele) é extremamente útil. Isso pode incluir tratamentos como efeitos "focalizar" visíveis, realces ou cliques de áudio ou alinhamento claro de um cursor com um elemento.

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho ideal do alvo em uma distância de 2 metros*

![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-640px.jpg)<br>
*Um exemplo de realce de um objeto direcionado por foco*

## <a name="target-placement"></a>Posicionamento do alvo
Geralmente, os usuários não conseguem localizar elementos da interface do usuário que estão posicionados muito altos ou muito baixos em seu campo de exibição, concentrando a maior parte de sua atenção em áreas em torno do foco principal, que é aproximadamente no nível dos olhos. O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar. Dada a tendência dos usuários de se concentrarem em uma área visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), o agrupamento de elementos de interface do usuário na medida em que eles estejam relacionados conceitualmente pode aproveitar os comportamentos de encadeamento da atenção de item a item conforme um usuário move o foco por uma área. Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.

![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Como melhorar os comportamentos de direcionamento
Se a intenção do usuário para o destino de algo puder ser determinada (ou aproximada), pode ser muito útil aceitar tentativas quase sem erros na interação, como se elas estivessem corretas. Aqui estão alguns métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:

### <a name="head-gaze-stabilization-gravity-wells"></a>Estabilização do foco com a cabeça ("poços gravitacionais")
Isso deve ser ativado na maior parte das vezes. Essa técnica remove a cabeça natural e as tremulações do pescoço que os usuários podem ter também movimento devido a comportamentos de aparência e fala.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo mais próximo
Eles funcionam melhor em áreas com conteúdo interativo esparso. Se houver uma alta probabilidade de que você possa determinar o que um usuário estava tentando interagir, você pode complementar seus recursos de direcionamento assumindo algum nível de intenção.

### <a name="backdating-and-postdating-actions"></a>Ações de backencontros e de reencontros
Esse mecanismo é útil para tarefas que exigem velocidade. Quando um usuário passa por uma série de manobras de direcionamento e ativação em velocidade, é útil assumir alguma intenção e permitir que as etapas perdidas atuem em destinos que o usuário tinha em foco ligeiramente antes ou ligeiramente após o toque (50 ms antes/depois era efetivo em ea teste de Rly).

### <a name="smoothing"></a>Suavização
Esse mecanismo é útil para a trajetória de movimentos, reduzindo a ligeira tremulação e Wobble devido a características de movimento de cabeçalho natural. Ao suavizar movimentos de caminho, Smooth pelo tamanho e distância dos movimentos em vez de ao longo do tempo.

### <a name="magnetism"></a>Magnetismo
Esse mecanismo pode ser considerado como uma versão mais comum dos algoritmos de link mais próximos – desenhar um cursor em direção a um destino ou simplesmente aumentar o hitboxes, seja visivelmente ou não, à medida que os usuários abordam os alvos prováveis usando algum conhecimento do layout interativo para melhor objetivo de usuário da abordagem. Isso pode ser particularmente eficiente para alvos pequenos.

### <a name="focus-stickiness"></a>Adesão do foco
Ao determinar a quais elementos interativos próximos dar foco, a adesão do foco fornece uma tendência para o elemento que está atualmente focado. Isso ajuda a reduzir os comportamentos de alternância de foco errático ao flutuar em um ponto médio entre dois elementos com ruído natural.


## <a name="composite-gestures"></a>Gestos compostos

### <a name="air-tap"></a>Fechar e abrir dedos indicador e polegar
O gesto de toque do Air (bem como os outros gestos abaixo) reage apenas a um toque específico. Para detectar outros toques, como menu ou compreender, seu aplicativo deve usar diretamente as interações de nível inferior descritas na seção dois principais gestos de componente acima.

### <a name="tap-and-hold"></a>Fechar e abrir dedos indicador e polegar e manter
Manter é simplesmente manter a posição do dedo para baixo no gesto de fechar e abrir dedos indicador e polegar. A combinação de toque e espera de ar permite uma variedade de interações mais complexas de "clicar e arrastar" quando combinadas com a movimentação do ARM, como a seleção de um objeto, em vez de ativá-lo ou interações de secundários de MouseDown, como mostrar um menu de contexto.
No entanto, tenha cuidado ao projetar o uso desse gesto, pois os usuários podem estar propensos a relaxar suas posturas de mão no decorrer de qualquer gesto estendido.

### <a name="manipulation"></a>Manipulação
Os gestos de manipulação podem ser usados para mover, redimensionar ou girar um holograma quando você quiser que o holograma reaja 1:1 aos movimentos da mão do usuário. Um uso para essas movimentações de 1:1 é permitir que o usuário desenhe ou pinte no mundo.
O direcionamento inicial de um gesto de manipulação deve ser feito pelo foco ou apontando. Quando o toque e a suspensão são iniciados, qualquer manipulação do objeto é tratada por movimentos de mão, liberando o usuário para examinar enquanto eles manipulam.

### <a name="navigation"></a>Navegação
Os gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar por widgets de interface do usuário, como menus radiais. Feche e abra os dedos indicador e polegar e mantenha para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizado em torno do pressionamento inicial. Você pode mover a mão ao longo do eixo X, Y ou Z de um valor -1 a 1, sendo 0 o ponto de partida.
A navegação pode ser usada para criar gestos de rolagem ou zoom contínuo baseados em velocidade, semelhante à rolagem de uma interface do usuário 2D com um clique no botão do meio do mouse e, em seguida, a movimentação do mouse para cima e para baixo.

A navegação com Rails refere-se à capacidade de reconhecer movimentos em determinado eixo até que um determinado limite seja atingido nesse eixo. Isso só é útil quando a movimentação em mais de um eixo está habilitada em um aplicativo pelo desenvolvedor, como se um aplicativo estiver configurado para reconhecer gestos de navegação no eixo X, Y, mas também especificado eixo X com Rails. Nesse caso, o sistema reconhecerá movimentos de mão no eixo X, desde que eles permaneçam dentro de um trilho imaginário (guia) no eixo X, se a movimentação à mão também ocorrer no eixo Y.

Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolagem, zoom ou operações de arrastar dentro do aplicativo. Isso injeta toques de dedo virtuais no aplicativo para simular gestos de toque do mesmo tipo. Os usuários podem selecionar quais dessas ações ocorrem alternando entre as ferramentas na barra acima do aplicativo, seja selecionando o botão ou dizendo ' < rolar/arrastar/aplicar zoom na ferramenta de > '.

[Mais informações sobre gestos compostos](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconhecedores de gestos

Um dos benefícios de usar o reconhecimento de gesto é que você pode configurar um reconhecedor de gesto somente para os gestos que o holograma atualmente direcionado pode aceitar. A plataforma apenas faz a desambiguidade, conforme necessário, para distinguir os gestos com suporte específicos. Dessa forma, um holograma que apenas dá suporte ao toque de ar pode aceitar qualquer período de tempo entre Press e Release, enquanto um holograma que dá suporte a TAP e Hold pode promover o toque para uma espera após o limite de tempo de espera.

## <a name="hand-recognition"></a>Reconhecimento de mão
O HoloLens reconhece gestos de mão acompanhando a posição de uma ou das duas mãos visíveis para o dispositivo. O HoloLens vê as mãos quando elas estão no estado pronto (parte posterior da mão voltada para você com o dedo indicador para cima) ou no estado pressionado (parte posterior da mão voltada para você com o dedo indicador para baixo). Quando as mãos estão em outras poses, o HoloLens ignora themz.
Para cada mão que o HoloLens detecta, você pode acessar sua posição sem orientação e seu estado pressionado. Conforme a mão se aproxima da borda do quadro de gesto, você também recebe um vetor de direção, que você pode mostrar ao usuário para que ele saiba como mover a mão para retorná-la ao local em que o HoloLens possa vê-la.

## <a name="gesture-frame"></a>Quadro de gesto
Para gestos no HoloLens, a mão deve estar dentro de um quadro de gesto, em um intervalo que as câmeras de detecção de gestos podem ver de forma apropriada, de nariz para Estou e entre ombros. Os usuários precisam ser treinados nessa área de reconhecimento para o sucesso da ação e para seus próprios confortos. Inicialmente, muitos usuários assumirão que o quadro de gesto deve estar dentro de sua exibição por meio do HoloLens e manter seus braços de forma inconfortável para interagir. Ao usar o clicador de HoloLens, não é necessário que as mãos estejam dentro do quadro de gesto.

No caso de gestos contínuos em particular, há algum risco de que os usuários movam suas mãos fora do quadro de gestos enquanto estiverem em um gesto médio ao mover um objeto Holographic, por exemplo, e perder o resultado pretendido.

Há três coisas que você deve considerar:

- Educação do usuário na existência do quadro gesto e limites aproximados. Isso é ensinado durante a configuração do HoloLens.

- Notificar os usuários quando seus gestos estiverem se aproximando ou dividindo os limites de quadro de gesto dentro de um aplicativo no grau de um gesto perdido levar a resultados indesejados. A pesquisa mostrou as principais qualidades desse sistema de notificação. O Shell do HoloLens fornece um bom exemplo desse tipo de notificação – Visual, no cursor central, indicando a direção na qual o cruzamento de limites está ocorrendo.

- As consequências de sair dos limites do quadro do gesto deverão ser minimizadas. Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite e não revertido. Por exemplo, se um usuário estiver movendo algum objeto Holographic em uma sala, a movimentação deverá parar quando o quadro do gesto for violado e não retornar ao ponto de partida. O usuário pode enfrentar alguma frustração, mas pode entender mais rapidamente os limites e não precisa reiniciar suas ações pretendidas todas as vezes.


## <a name="see-also"></a>Consulte também
* [Manipulação direta com as mãos](direct-manipulation.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Comando de voz](voice-design.md)






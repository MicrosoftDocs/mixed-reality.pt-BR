---
title: Focar e confirmar
description: Visão geral do modelo de entrada "olhar e Commit"-usando a entrada de olho ou de cabeçalho.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade misturada, olhar, direcionamento de olhar, interação, design, acompanhamento de cabeça, acompanhamento de cabeçalho
ms.openlocfilehash: c44c1a75e831869a3ed4d12bb6c9e87c478daf56
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866886"
---
# <a name="gaze-and-commit"></a>Focar e confirmar

_Olhar e commit_ é um modelo de entrada fundamental que está fortemente relacionado com a maneira como estamos interagindo com nossos computadores usando o mouse: _Point & clique_.
Nesta página, apresentamos dois tipos de entrada olhar (cabeça e olho-olhar) e tipos diferentes de ações de confirmação. 
_Olhar e commit_ são considerados um modelo de entrada distante com manipulação indireta.
Isso significa que ele é melhor usado para interagir com conteúdo Holographic que está fora do alcance.

Os headsets de realidade misturada podem usar a posição e a orientação da cabeça do usuário para determinar o vetor de direção da cabeça. Você pode considerar isso como um laser que aponta para a frente, diretamente entre os olhos do usuário. Essa é uma aproximação bastante grosseira da direção para a qual o usuário está olhando. Seu aplicativo pode interceptar esse raio com objetos virtuais ou do mundo real e desenhar um cursor nesse local para permitir que o usuário saiba o que eles têm como destino no momento.

Além do Head olhar, alguns headsets de realidade misturada, como o HoloLens 2, incluem sistemas de controle ocular que produzem um vetor olhar de olho. Isso fornece uma medida refinada da direção para a qual o usuário está olhando. Em ambos os casos, o olhar representa um sinal importante para a intenção do usuário. Quanto melhor o sistema, é possível interpretar e prever as ações pretendidas do usuário, a satisfação do usuário aumenta e o desempenho melhora.

Abaixo estão alguns exemplos de como um desenvolvedor de realidade misturada pode se beneficiar do olhar de cabeça ou olho:
* Seu aplicativo pode Interseccionar olhar com os hologramas em sua cena para determinar onde a atenção do usuário é (mais precisa com o olho-olhar).
* Seu aplicativo pode canalizar gestos de canal e pressionamentos de controlador com base no olhar do usuário, permitindo que o usuário selecione, ative, pegue, role ou interaja, de outra maneira, com seus hologramas.
* Seu aplicativo pode permitir que o usuário Coloque os hologramas em superfícies do mundo real interseccionando seu olhar Ray com a malha de mapeamento espacial.
* Seu aplicativo pode saber quando o usuário *não* está olhando para a direção de um objeto importante, o que pode levar seu aplicativo a dar indicações visuais e de áudio para virar esse objeto.

<br>


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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Foco com a cabeça e confirmação</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</td>
        <td>➕ Opção alternativa</td>
    </tr>
         <tr>
        <td>Focar com o olhar e confirmar</td>
        <td>❌Não disponível</td>
        <td>✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</td>
        <td>❌Não disponível</td>
    </tr>
</table>


## <a name="gaze"></a>Focar

### <a name="eye--or-head-gaze"></a>Olho ou cabeça-olhar?
Há várias considerações a serem levadas em conta ao enfrentar a pergunta se você deve usar o modelo de entrada "olho-olhar e confirmação" ou "Head-olhar e Commit". Se você estiver desenvolvendo para um headset de imersão ou para o HoloLens (1º gen), a escolha será simples: Head-olhar e Commit. Se você estiver desenvolvendo para o HoloLens 2, a escolha se tornará um pouco mais difícil, por isso é importante entender as vantagens e os desafios que acompanham cada um deles.
Compilamos alguns dos nossos profissionais e contratados na tabela abaixo para contrastars em contraste com a olhar de direcionamento. Isso está longe de ser concluído e sugerimos saber mais sobre o direcionamento olhar para a realidade misturada aqui:
* [Acompanhamento de olho no hololens 2](eye-tracking.md): introdução geral do nosso novo recurso de acompanhamento de olho no hololens 2, incluindo algumas diretrizes para desenvolvedores. 
* [Olhar interação](eye-gaze-interaction.md)entre os olhos: considerações de design e recomendações ao planejar o uso de acompanhamento de olho como uma entrada.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>Direcionamento de olhar de olho</strong></td>
        <td><strong>Direcionamento de foco com a cabeça</strong></td>
    </tr>
    <tr>
        <td>Rápida!</td>
        <td>Mais lento</td>
    </tr>
    <tr>
        <td>Baixo esforço (mal que qualquer movimento do corpo seja necessário)</td>
        <td>Pode ser fatiguing-possível discomfort (por exemplo, tensão do pescoço)</td>
    </tr>
    <tr>
        <td>Não requer um cursor, mas é recomendado um comentário sutil</td>
        <td>Requer para mostrar um cursor</td>
    </tr>
    <tr>
        <td>Não há movimentos de olho suaves – por exemplo, não é bom para desenhar</td>
        <td>Mais controlado e explícito</td>
    </tr>
    <tr>
        <td>Difícil para destinos muito pequenos (por exemplo, pequenos botões ou weblinks)</td>
        <td>Liable! Ótimo fallback!</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

Se você usar Head-olhar ou olho-olhar para seu modelo de entrada de olhar e confirmação é fornecido com diferentes conjuntos de restrições de design, que serão abordados separadamente nos artigos de [olho-olhar e confirmação](gaze-and-commit-eyes.md) e [cabeça-olhar e de confirmação](gaze-and-commit-head.md) .

<br>

---

### <a name="cursor"></a>Cursor

:::row:::
    :::column:::
        Para o Head olhar, a maioria dos aplicativos deve usar um [cursor](cursors.md) (ou outra indicação de auditoria/Visual) para dar ao usuário a confiança no que eles estão prestes a interagir. Normalmente, você posiciona esse cursor no mundo em que o Head olhar Ray primeiro cruza um objeto, que pode ser um holograma ou uma superfície do mundo real.<br>
        <br>
        Para olhar de olho, geralmente recomendamos *não* mostrar um cursor, pois isso pode rapidamente se tornar confuso e irritante para o usuário. Em vez disso, destaque sutilmente os destinos visuais ou use um cursor de olho muito fraco para fornecer confiança sobre o que o usuário está prestes a interagir. Para obter mais informações, confira nossas [diretrizes de design para entrada baseada em olhos](eye-tracking.md) no HoloLens 2.
    :::column-end:::
        :::column:::
       ![Um cursor visual de exemplo para mostrar olhar](images/cursor.jpg)<br>
       *Imagem: um cursor visual de exemplo para mostrar olhar*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
Depois de falar sobre diferentes maneiras de _olhar_ em um alvo, vamos falar um pouco mais sobre a parte de _confirmação_ em _olhar e commit_.
Depois de direcionar um objeto ou elemento de interface do usuário, o usuário pode interagir ou clicar nele usando uma entrada secundária. Isso é conhecido como a etapa de confirmação do modelo de entrada. 

Os seguintes métodos de confirmação são compatíveis:
- Gesto de toque do ar à mão (ou seja, levante sua mão na frente e reúna o dedo e o polegar)
- Diga _"Select"_ ou um dos comandos de voz de destino
- Pressione um único botão em um [clicador de HoloLens](https://docs.microsoft.com/hololens/hololens1-clicker)
- Pressione o botão ' A ' em um gamepad do Xbox
- Pressione o botão ' A ' em um controlador adaptável do Xbox

### <a name="gaze-and-air-tap-gesture"></a>Gesto de toque olhar e Air
Fechar e abrir dedos indicador e polegar é um gesto de tocar feito com a mão levantada. Para executar um toque de ar, aumente o seu indicador para a posição pronta, aperte o polegar e aumente o seu dedo de índice de volta para o lançamento. No HoloLens (1ª gen), o Air Tap é a entrada secundária mais comum.


:::row:::
    :::column:::
       ![Dedo na posição pronta](images/readyandpress-ready.jpg)<br>
       **Dedo na posição pronta**<br>
    :::column-end:::
    :::column:::
       ![Pressione dedo para baixo para tocar ou clique](images/readyandpress-press.jpg)<br>
        **Pressione dedo para baixo para tocar ou clique**<br>
    :::column-end:::
:::row-end:::


O toque de ar também está disponível no HoloLens 2. Ele foi relaxado da versão original. Quase todos os tipos de pinçações agora têm suporte, contanto que a mão esteja na vertical e mantendo ainda. Isso facilita muito para os usuários aprenderem e fazerem o gesto. Esse novo toque de ar substitui o antigo por meio da mesma API, de modo que os aplicativos existentes terão o novo comportamento automaticamente após a recompilação para o HoloLens 2.

<br>

---

### <a name="gaze-and-select-voice-command"></a>Olhar e comando de voz "Select"
A linha de comando de voz é um dos principais métodos de interação na realidade misturada. Ele fornece um mecanismo sem intervenção e eficiência para controlar o sistema. Há diferentes tipos de modelos de interação de voz:

- O comando genérico "Select" que executa um clique actuation ou Commit como uma entrada secundária.
- Os comandos de objeto (por exemplo, "fechar" ou "torná-lo maior") executam e se confirmam em uma ação como uma entrada secundária.
- Os comandos globais (por exemplo, "ir para o início") não exigem um destino.
- As interfaces de usuário de conversa ou entidades como Cortana têm um recurso de linguagem natural de ia.
- Comandos de voz personalizados

Para obter mais detalhes, bem como uma lista abrangente de comandos de voz disponíveis e como usá-los, confira nossas diretrizes de [comando de voz](voice-design.md) .

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Olhar e clicador de HoloLens

:::row:::
    :::column:::
        O clicador de HoloLens é o primeiro dispositivo periférico criado especificamente para o HoloLens. Ele está incluído com o HoloLens (1ª gen) Development Edition. O clicador do HoloLens permite que um usuário clique com o movimento mínimo e confirme como uma entrada secundária. O clico do HoloLens se conecta ao HoloLens (1º gen) ou ao HoloLens 2 usando o Bluetooth de baixa energia (BTLE).<br>
        <br>
        [Mais informações e instruções para emparelhar o dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Imagem: clicador de HoloLens*
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>Controlador sem fio olhar e Xbox

:::row:::
    :::column:::
        O controlador sem fio do Xbox executa um clique actuation como uma entrada secundária usando o botão ' A '. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema. Se você quiser personalizar o controlador, use o aplicativo de acessórios do Xbox para configurar o controlador sem fio do Xbox.<br>
        <br>
        [Como emparelhar um controlador Xbox com seu PC](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Imagem: controlador sem fio do Xbox*
    :::column-end:::
        :::column:::
       ![Controle sem Fio Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>Controlador adaptável olhar e Xbox
Projetado principalmente para atender às necessidades de jogos com mobilidade limitada, o controlador adaptável do Xbox é um hub unificado para dispositivos que ajuda a tornar a realidade misturada mais acessível.

O controlador adaptável do Xbox executa um clique actuation como uma entrada secundária usando o botão ' A '. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema. Se você quiser personalizar o controlador, use o aplicativo de acessórios do Xbox para configurar o controlador adaptável do Xbox.

![Controle Adaptável Xbox](images/xbox-adaptive-controller-devices.jpg)<br>
*Controle Adaptável Xbox*

Conecte dispositivos externos, como comutadores, botões, montagens e joysticks, para criar uma experiência de controlador personalizada que seja exclusivamente sua. As entradas de botão, Thumbstick e gatilho são controladas com dispositivos assistenciais conectados por meio de conectores de 3,5 mm e portas USB.

![Portas do Controle Adaptável Xbox](images/xbox-adaptive-controller-ports.jpg)<br>
*Portas do Controle Adaptável Xbox*

[Instruções para emparelhar o dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Mais informações disponíveis no site do Xbox</a>

<br>

---

## <a name="composite-gestures"></a>Gestos compostos

### <a name="air-tap"></a>Fechar e abrir dedos indicador e polegar
O gesto de toque do Air (bem como os outros gestos abaixo) reage apenas a um toque específico. Para detectar outros toques, como menu ou compreender, seu aplicativo deve usar diretamente as interações de nível inferior descritas na seção dois principais gestos de componente acima.

### <a name="tap-and-hold"></a>Fechar e abrir dedos indicador e polegar e manter
Manter é simplesmente manter a posição do dedo para baixo no gesto de fechar e abrir dedos indicador e polegar. A combinação de toque e espera de ar permite uma variedade de interações mais complexas de "clicar e arrastar" quando combinadas com a movimentação do ARM, como a seleção de um objeto, em vez de ativá-lo ou interações de secundários de MouseDown, como mostrar um menu de contexto.
No entanto, tenha cuidado ao projetar o uso desse gesto, pois os usuários podem estar propensos a relaxar suas posturas de mão no decorrer de qualquer gesto estendido.

### <a name="manipulation"></a>manipulação
Os gestos de manipulação podem ser usados para mover, redimensionar ou girar um holograma quando você quiser que o holograma reaja 1:1 aos movimentos da mão do usuário. Um uso para essas movimentações de 1:1 é permitir que o usuário desenhe ou pinte no mundo.
O direcionamento inicial de um gesto de manipulação deve ser feito pelo foco ou apontando. Quando o toque e a suspensão são iniciados, qualquer manipulação do objeto é tratada por movimentos de mão, liberando o usuário para examinar enquanto eles manipulam.

### <a name="navigation"></a>Navegação
Os gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar por widgets de interface do usuário, como menus radiais. Feche e abra os dedos indicador e polegar e mantenha para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizado em torno do pressionamento inicial. Você pode mover a mão ao longo do eixo X, Y ou Z de um valor -1 a 1, sendo 0 o ponto de partida.
A navegação pode ser usada para criar gestos de rolagem ou zoom contínuo baseados em velocidade, semelhante à rolagem de uma interface do usuário 2D com um clique no botão do meio do mouse e, em seguida, a movimentação do mouse para cima e para baixo.

A navegação com Rails refere-se à capacidade de reconhecer movimentos em determinado eixo até que um determinado limite seja atingido nesse eixo. Isso só é útil quando a movimentação em mais de um eixo está habilitada em um aplicativo pelo desenvolvedor, como se um aplicativo estiver configurado para reconhecer gestos de navegação no eixo X, Y, mas também especificado eixo X com Rails. Nesse caso, o sistema reconhecerá movimentos de mão no eixo X, desde que eles permaneçam dentro de um trilho imaginário (guia) no eixo X, se a movimentação à mão também ocorrer no eixo Y.

Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolagem, zoom ou operações de arrastar dentro do aplicativo. Isso injeta toques de dedo virtuais no aplicativo para simular gestos de toque do mesmo tipo. Os usuários podem selecionar quais dessas ações ocorrem alternando entre as ferramentas na barra acima do aplicativo, seja selecionando o botão ou dizendo ' <rolar/arrastar/aplicar zoom na ferramenta de> '.

[Mais informações sobre gestos compostos](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconhecedores de gestos

Um dos benefícios de usar o reconhecimento de gesto é que você pode configurar um reconhecedor de gesto somente para os gestos que o holograma atualmente direcionado pode aceitar. A plataforma apenas faz a desambiguidade, conforme necessário, para distinguir os gestos com suporte específicos. Dessa forma, um holograma que apenas dá suporte ao toque de ar pode aceitar qualquer período de tempo entre Press e Release, enquanto um holograma que dá suporte a TAP e Hold pode promover o toque para uma espera após o limite de tempo de espera.

## <a name="hand-recognition"></a>Reconhecimento de mão
O HoloLens reconhece gestos de mão acompanhando a posição de uma ou das duas mãos visíveis para o dispositivo. O HoloLens vê as mãos quando elas estão no estado pronto (parte posterior da mão voltada para você com o dedo indicador para cima) ou no estado pressionado (parte posterior da mão voltada para você com o dedo indicador para baixo). Quando as mãos estão em outras poses, o HoloLens as ignora.
Para cada mão que o HoloLens detecta, você pode acessar sua posição sem orientação e seu estado pressionado. Conforme a mão se aproxima da borda do quadro de gesto, você também recebe um vetor de direção, que você pode mostrar ao usuário para que ele saiba como mover a mão para retorná-la ao local em que o HoloLens possa vê-la.

## <a name="gesture-frame"></a>Quadro de gesto
Para gestos no HoloLens, a mão deve estar dentro de um quadro de gesto, em um intervalo que as câmeras de detecção de gestos podem ver de forma apropriada, de nariz para Estou e entre ombros. Os usuários precisam ser treinados nessa área de reconhecimento para o sucesso da ação e para seus próprios confortos. Inicialmente, muitos usuários assumirão que o quadro de gesto deve estar dentro de sua exibição por meio do HoloLens e manter seus braços de forma inconfortável para interagir. Ao usar o clicador de HoloLens, não é necessário que as mãos estejam dentro do quadro de gesto.

No caso de gestos contínuos em particular, há algum risco de que os usuários movam suas mãos fora do quadro de gestos enquanto estiverem em um gesto médio ao mover um objeto Holographic, por exemplo, e perder o resultado pretendido.

Há três coisas que você deve considerar:

- Educação do usuário na existência do quadro gesto e limites aproximados. Isso é ensinado durante a configuração do HoloLens.

- Notificar os usuários quando seus gestos estiverem se aproximando ou dividindo os limites de quadro de gesto dentro de um aplicativo no grau de um gesto perdido levar a resultados indesejados. A pesquisa mostrou as principais qualidades desse sistema de notificação. O Shell do HoloLens fornece um bom exemplo desse tipo de notificação – Visual, no cursor central, indicando a direção na qual o cruzamento de limites está ocorrendo.

- As consequências de sair dos limites do quadro do gesto deverão ser minimizadas. Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite e não revertido. Por exemplo, se um usuário estiver movendo algum objeto Holographic em uma sala, a movimentação deverá parar quando o quadro do gesto for violado e não retornar ao ponto de partida. O usuário pode enfrentar alguma frustração, mas pode entender mais rapidamente os limites e não precisa reiniciar suas ações pretendidas todas as vezes.



## <a name="see-also"></a>Confira também
* [Interação ocular](eye-gaze-interaction.md)
* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)


---
title: Gestos
description: Os gestos de mão permitem que os usuários executem ações em realidade misturada.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, gestos, interação, design
ms.openlocfilehash: 70b03c6fa327bd987a681bba59abb725c3ddc6b4
ms.sourcegitcommit: e5b677f92ac4b1dff9aad6c329345a5aca4fcef5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69020219"
---
# <a name="gestures"></a>Gestos

Os gestos de mão permitem que os usuários executem ações em realidade misturada. A interação é criada em **olhar** para direcionar e **gesto** ou **voz** para agir sobre qualquer elemento que tenha sido direcionado. Os gestos de mão não fornecem um local preciso no espaço, mas a simplicidade de colocar em um HoloLens e interagir imediatamente com o conteúdo permite que os usuários trabalhem sem nenhum outro acessório.

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Gestos</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Mãos articuladas</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Mais diretrizes específicas para o HoloLens 2 em [breve](index.md#news-and-notes).

## <a name="gaze-and-commit"></a>Olhar-e-Commit

Para executar ações, os gestos à mão usam [olhar de cabeçalho](gaze.md) como o mecanismo de direcionamento. A combinação de **olhar** e o gesto de **toque do Air** resulta em uma interação de **olhar e confirmação** . Uma alternativa ao olhar-and-commit é o **ponto e a confirmação**, habilitado pelos [controladores de movimento](motion-controllers.md). Os aplicativos executados no HoloLens só precisam dar suporte a olhar-and-Commit, já que o HoloLens não oferece suporte a controladores de movimento. Os aplicativos que são executados em headsets de HoloLens e de imersão devem dar suporte a interações controladas por olhar e por ponto, para dar aos usuários a opção de qual dispositivo de entrada eles usam.

## <a name="the-two-core-gestures-of-hololens"></a>Os dois gestos principais do HoloLens

Atualmente, o HoloLens reconhece dois gestos de componentes principais – **toque** e **flor**. Essas duas interações principais são o nível mais baixo de dados de entrada espaciais que um desenvolvedor pode acessar. Eles formam a base para uma variedade de possíveis ações do usuário.

### <a name="air-tap"></a>Fechar e abrir dedos indicador e polegar

O toque de ar é um gesto de toque com a mão mantida na vertical, semelhante a um clique do mouse ou selecionar. Isso é usado na maioria das experiências de HoloLens para o equivalente a um "clique" em um elemento de interface do usuário depois de direcioná-lo com [olhar](gaze.md). É uma ação universal que você aprende uma vez e, em seguida, se aplica em todos os seus aplicativos. Outras maneiras de executar SELECT são pressionar o botão único em um selecionador de [HoloLens](hardware-accessories.md#hololens-clicker) ou falando sobre o comando de voz "Select".

![Estado pronto para gestos de mão no HoloLens](images/image9.png)<br>
*Estado pronto para toque de ar no HoloLens.*

O toque de ar é um gesto discreto. Uma seleção está concluída ou não é, uma ação é ou não é executada em uma experiência. É possível, embora não seja recomendado sem alguma finalidade específica, criar outros gestos discretos de combinações dos componentes principais (por exemplo, um gesto de toque duplo para significar algo diferente de um toque único).

![Dedo na posição pronta e, em seguida, um toque ou clique em movimento](images/readyandpress.jpg)<br>
*Como executar um toque de ar: Eleve o dedo do índice à posição pronta, pressione o dedo para baixo para tocar ou selecionar e, em seguida, faça backup para o lançamento.*

### <a name="bloom"></a>Cair

A flor é o gesto de "início" e é reservado para isso sozinho. É uma ação especial do sistema que é usada para voltar ao menu iniciar. É equivalente a pressionar a tecla Windows em um teclado ou o botão Xbox em um controlador Xbox. O usuário pode usar qualquer uma das mãos.

![Gesto de cair no HoloLens](images/image10-640px.png)

Para fazer o gesto de cair no HoloLens, mantenha sua mão em mãos, com suas mãos juntas. Em seguida, abra sua mão. Observe que você também pode retornar para começar dizendo "Ei Cortana, Go Home". Os aplicativos não podem reagir especificamente a uma ação inicial, pois são tratados pelo sistema.

![Gesto de cair](images/bloom-giphy.gif)<br>
*Como executar o gesto de flor no HoloLens.*

## <a name="composite-gestures"></a>Gestos compostos

Os aplicativos podem reconhecer mais do que apenas toques individuais. Pela combinação do toque, do gesto de manter e de soltar com o movimento da mão, gestos compostos mais complexos podem ser feitos. Esses gestos compostos ou de alto nível baseiam-se nos dados de entrada espaciais de baixo nível (do fechar e abrir dedos indicador e polegar ao abrir a mão) aos quais os desenvolvedores têm acesso.

<table>
<tr>
<th> Gesto de composição</th><th> Como aplicar</th>
</tr><tr>
<td>Fechar e abrir dedos indicador e polegar</td><td>O gesto de fechar e abrir dedos indicador e polegar (bem como os outros gestos abaixo) responde somente a um toque específico. Para detectar outros toques, como menu ou segurar, o aplicativo precisa usar diretamente as interações de baixo nível descritas na seção de gestos de dois componentes principais acima.</td>
</tr><tr>
<td>Fechar e abrir dedos indicador e polegar e manter</td><td><p>Manter é simplesmente manter a posição do dedo para baixo no gesto de fechar e abrir dedos indicador e polegar. A combinação de toque e suspensão do ar permite uma variedade de interações &quot;mais complexas de&quot; clicar e arrastar quando combinadas com movimento de ARM, como a seleção de um objeto &quot;,&quot; em vez de ativá-lo ou MouseDown interações secundárias, como mostrar um menu de contexto.</p><p>No entanto, tenha cuidado ao projetar o uso desse gesto, pois os usuários podem estar propensos a relaxar suas posturas de mão no decorrer de qualquer gesto estendido.</p></td>
</tr><tr>
<td>Manipulação</td><td><p>Os gestos de manipulação podem ser usados para mover, redimensionar ou girar um holograma quando você quiser que o holograma reaja 1:1&#39;aos movimentos do usuário. Um uso para essas movimentações de 1:1 é permitir que o usuário desenhe ou pinte no mundo.</p><p>O direcionamento inicial de um gesto de manipulação deve ser feito pelo foco ou apontando. Depois que o gesto de fechar e abrir dedos indicador e polegar e manter for iniciado, qualquer manipulação do objeto será tratada pelos movimentos da mão, liberando o usuário para olhar em volta durante a manipulação.</p></td>
</tr><tr>
<td>Navegação</td><td><p>Os gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar por widgets de interface do usuário, como menus radiais. Feche e abra os dedos indicador e polegar e mantenha para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizado em torno do pressionamento inicial. Você pode mover a mão ao longo do eixo X, Y ou Z de um valor -1 a 1, sendo 0 o ponto de partida.</p><p>A navegação pode ser usada para criar gestos de rolagem ou zoom contínuo baseados em velocidade, semelhante à rolagem de uma interface do usuário 2D com um clique no botão do meio do mouse e, em seguida, a movimentação do mouse para cima e para baixo.</p><p>A navegação com trilhos refere-se à capacidade de reconhecer movimentos em determinado eixo até certo limite ser atingido nesse eixo. Isso só é útil quando o movimento em mais de um eixo é habilitado em um aplicativo pelo desenvolvedor, por exemplo, se um aplicativo é configurado para reconhecer gestos de navegação nos eixos X e Y, mas também no eixo X especificado com trilhos. Nesse caso, o sistema reconhecerá os movimentos de mão no eixo X, desde que eles permaneçam dentro de um trilho imaginário (guia) no eixo, X caso o movimento de mão também ocorra no eixo Y.</p><p>Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolagem, zoom ou operações de arrastar dentro do aplicativo. Isso injeta toques de dedo virtuais no aplicativo para simular gestos de toque do mesmo tipo. Os usuários podem selecionar quais dessas ações ocorrem alternando entre as ferramentas na barra acima do aplicativo, seja selecionando o botão ou dizendo &#39; &lt;a ferramenta&#39;rolar/arrastar/aplicar zoom&gt; .</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>Reconhecedores de gestos

Uma vantagem do uso do reconhecimento de gestos é que você pode configurar um reconhecedor de gestos apenas para os gestos que o holograma direcionado atualmente pode aceitar. A plataforma fará apenas a desambiguidade necessária para distinguir esses gestos compatíveis específicos. Dessa forma, um holograma que só é compatível com o gesto de fechar e abrir dedos indicador e polegar pode aceitar qualquer período de tempo entre o pressionamento e a liberação, enquanto um holograma que é compatível com o gesto de fechar e abrir dedos indicador e polegar e manter pode promover o toque a um gesto de manter após o limite de tempo em que o toque é mantido.

## <a name="hand-recognition"></a>Reconhecimento de mão

O HoloLens reconhece gestos de mão acompanhando a posição de uma ou das duas mãos visíveis para o dispositivo. O HoloLens vê as mãos quando estão no **estado pronto** (o verso da mão com o dedo para cima) ou o **estado pressionado** (no verso da mão com o dedo do índice). Quando as mãos estiverem em outras poses, o HoloLens as ignorará.

Para cada mão detectada pelo HoloLens, você pode acessar sua posição (sem orientação) e seu estado pressionado. Conforme a mão se aproxima da borda do quadro de gesto, você também recebe um vetor de direção, que você pode mostrar ao usuário para que ele saiba como mover a mão para retorná-la ao local em que o HoloLens possa vê-la.

## <a name="gesture-frame"></a>Quadro de gesto

Para os gestos no HoloLens, a mão precisa estar em um “quadro de gesto”, em um alcance no qual as câmeras de detecção de gesto possam vê-la de forma adequada (muito aproximadamente, do nariz até a cintura e entre os ombros). Os usuários precisam ser treinados nessa área de reconhecimento para o sucesso da ação e para seu próprio conforto (muitos usuários inicialmente presumirão que o quadro de gesto está dentro de sua visão por meio do HoloLens e manterão os braços levantados de forma desconfortável para interagir com ele). Ao usar o HoloLens Clicker, suas mãos não precisam estar dentro do quadro de gesto.

No caso de gestos contínuos em particular, há algum risco de que os usuários movam as mãos para fora do quadro de gesto durante o gesto intermediário (ao mover um objeto holográfico, por exemplo) e percam seu resultado pretendido.

Há três coisas que você deve considerar:
* Educação do usuário sobre a existência do quadro de gesto e os limites aproximados (isso é ensinado durante a instalação do HoloLens).
* Notificação dos usuários quando seus gestos estiverem se aproximando ou saírem dos limites do quadro de gesto em um aplicativo, na medida em que um gesto perdido levará a resultados indesejados. As pesquisas mostram as principais qualidades de um sistema de notificação como esse e o shell do HoloLens oferece um bom exemplo desse tipo de notificação (visual, no cursor central, indicando a direção na qual o limite está sendo ultrapassado).
* As consequências de sair dos limites do quadro do gesto deverão ser minimizadas. Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite, mas não revertido. Por exemplo, se um usuário estiver movendo algum objeto Holographic por uma sala, a movimentação deverá parar quando o quadro do gesto for violado, mas **não** será retornado para o ponto de partida. Assim, o usuário poderá se frustrar, mas poderá mais rapidamente entender os limites e não precisar reiniciar suas ações pretendidas completas sempre.

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e esperar](gaze-and-dwell.md)
* [Design de voz](voice-design.md)
* [Entrada do MR 211: gesto](holograms-211.md)
* [Gestos e controladores de movimento no Unity](gestures-and-motion-controllers-in-unity.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Controladores de movimentos](motion-controllers.md)

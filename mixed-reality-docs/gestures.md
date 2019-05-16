---
title: Gestos
description: Gestos de mão permitem aos usuários executar a ação em realidade misturada.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, gestos, interação, o design
ms.openlocfilehash: fabd47fef424186b826c410de725f805ff7005f5
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629062"
---
# <a name="gestures"></a>Gestos

Gestos de mão permitem que os usuários realizar uma ação na realidade mista. Interação baseia **olhares** ao destino e **gesto** ou **voz** para atuar em qualquer elemento foram direcionado. Gestos de mão não fornecem um local exato no espaço, mas a simplicidade de colocar em um HoloLens e estão interagindo imediatamente com conteúdo permite que os usuários começar a trabalhar sem os outros acessórios.

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> Gestos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
<tr>
<td> Mãos articuladas</td><td></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

## <a name="gaze-and-commit"></a>Olhar e confirmação

Para executar ações, use gestos de mão [olhar principal](gaze.md) como o mecanismo de direcionamento. A combinação de **olhares** e o **polegar** gesto resulta em um **olhar e confirmação** interação. É uma alternativa à confirmação olhar **ponto-e-confirmação**, habilitado por [controladores de movimento](motion-controllers.md). Aplicativos que são executados em HoloLens só precisam dar suporte à confirmação olhar como HoloLens não oferece suporte a controladores de movimento. Aplicativos que são executados em HoloLens e fones imersivos em exposição devem dar suporte a interações de tanto orientado a olhar e controlado por apontando para fornecer opções dos usuários nos dispositivos de entrada que eles utilizam.

## <a name="the-two-core-gestures-of-hololens"></a>As duas principais gestos do HoloLens

Atualmente, HoloLens reconhece dois principais gestos-componentes - **polegar** e **Bloom**. Essas interações de dois núcleos são o nível mais baixo de dados espaciais de entrada que um desenvolvedor possa acessar. Eles formam a base para uma variedade de ações possíveis do usuário.

### <a name="air-tap"></a>Indicador e polegar

Indicador e polegar é um gesto de tocar com a mão na vertical, semelhante a um clique do mouse ou selecione. Isso é usado na maioria das experiências do HoloLens para o equivalente de "clique" em um elemento de interface do usuário após para direcioná-lo com [olhares](gaze.md). Ele é uma ação universal que você saiba mais uma vez e, em seguida, aplicar em todos os seus aplicativos. Outras maneiras de executar select são pressionando o botão único uma [HoloLens Clicker](hardware-accessories.md#hololens-clicker) ou falando a voz de comando "Select".

![Estado pronto para gestos de mão em HoloLens](images/image9.png)<br>
*Estado pronto para o indicador e polegar no HoloLens.*

Indicador e polegar é um gesto discreto. Uma seleção é concluída ou não é, uma ação é ou não ocorrer dentro de uma experiência. É possível, embora não seja recomendado sem alguma finalidade específica, para criar outros gestos discretos de combinações de componentes principais (por exemplo, um gesto de toque duplo para significar algo diferente de um único toque).

![Com o dedo na posição pronta e, em seguida, um movimento de toque ou clique em](images/readyandpress.jpg)<br>
*Como executar um indicador e polegar: Gerar o dedo para a posição de pronto, pressione o dedo para baixo até o toque ou selecione e, em seguida, fazer backup para liberar.*

### <a name="bloom"></a>Bloom

Bloom é o gesto de "home" e é reservada para que apenas. É uma ação de sistema especial que é usada para retornar ao Menu Iniciar. É equivalente a pressionar a tecla do Windows em um teclado ou o botão do Xbox em um controlador do Xbox. O usuário pode usar qualquer um dos mão.

![Gesto de bloom em HoloLens](images/image10-640px.png)

Para fazer o gesto de bloom em HoloLens, mantenha a sua mão, palm, junto com seu alcance. Em seguida, abra a mão. Observe que você também sempre pode retornar ao início dizendo "Ei Cortana, Go Home". Aplicativos não é possível reagir especificamente a uma ação inicial, como elas são tratadas pelo sistema.

![Gesto de bloom](images/bloom-giphy.gif)<br>
*Como executar o gesto de bloom em HoloLens.*

## <a name="composite-gestures"></a>Gestos de composição

Aplicativos podem reconhecer os toques de mais de apenas individuais. Pela combinação de toque, mantenha e de versão com o movimento da mão, gestos de composição mais complexos podem ser executados. Esses gestos de alto nível ou compostos dependem de baixo nível entrados dados espaciais (de indicador e polegar e Bloom) que os desenvolvedores têm acesso ao.

<table>
<tr>
<th> Gesto de composição</th><th> Como aplicar</th>
</tr><tr>
<td>Indicador e polegar</td><td>O gesto de toque de ar (bem como outros gestos abaixo) reage somente a um toque específico. Para detectar outras toques, como o Menu ou compreensão, seu aplicativo deve usar diretamente as interações de baixo nível descritas na seção de gestos de dois componentes principais acima.</td>
</tr><tr>
<td>Tap e hold</td><td><p>Espera é simplesmente manter a posição do dedo para baixo do indicador e polegar. A combinação do ar tap e hold permite para uma variedade de mais complexos &quot;clique e arraste&quot; interações quando combinado com o arm movimentação como pegar um objeto em vez de ativá-la ou &quot;mousedown&quot; interações secundárias como mostrar um menu de contexto.</p><p>Tenha cuidado ao projetar para esse gesto no entanto, como os usuários pode estar sujeita a relaxar postures suas mãos no decorrer de quaisquer gesto estendido.</p></td>
</tr><tr>
<td>Manipulação</td><td><p>Gestos de manipulação que podem ser usados para mover, redimensionar ou girar um holograma quando desejar que o holograma reagir 1:1 para o usuário&#39;movimentos de mão de s. Um uso para tais movimentações de 1:1 é permitir que o usuário desenha ou pintar no mundo.</p><p>O direcionamento inicial um gesto de manipulação de deve ser feito pelo olhar ou apontando. Depois que o tap e hold é iniciado, qualquer manipulação do objeto, em seguida, é tratada manualmente os movimentos, liberando o usuário para olhar em volta, embora eles manipulam.</p></td>
</tr><tr>
<td>Navegação</td><td><p>Gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar de widgets de interface do usuário, como menus radiais. Toque e segure para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizada em torno de imprensa inicial. Você pode mover sua mão ao longo do eixo X, Y ou Z de um valor de -1 para 1 com 0 sendo o ponto de partida.</p><p>Navegação pode ser usada para criar com base em velocidade de rolagem contínua ou gestos de zoom, semelhantes a uma interface do usuário de 2D de rolagem clicando no botão do meio do mouse e, em seguida, mover o mouse para cima para baixo.</p><p>A navegação com o rails refere-se à capacidade de reconhecer os movimentos no certo eixo até certo limite é atingido naquele eixo. Isso só é útil, quando o movimento em mais de um eixo está habilitado em um aplicativo pelo desenvolvedor, por exemplo, se um aplicativo é configurado para reconhecer gestos de navegação em X, eixo Y, mas também especificado eixo com trilhos X. Nesse caso, sistema reconhecerá movimentos de mão em eixo X, desde que eles permaneçam dentro de um imaginário rails (guia) no eixo, X se o movimento de mão também ocorre eixo Y.</p><p>Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolar, aplicar zoom ou arraste dentro do aplicativo. Isso injeta toques de dedo virtual para o aplicativo para simular os gestos de toque do mesmo tipo. Os usuários podem selecionar qual das seguintes ações ocorrem alternando entre as ferramentas na barra de acima do aplicativo, selecionando o botão ou dizendo &#39; &lt;arrastar/rolagem/Zoom&gt; ferramenta&#39;.</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>Reconhecedores de gestos

Uma vantagem de usar o reconhecimento de gesto é que você pode configurar um reconhecedor de gestos apenas para os gestos que de destino atual holograma pode aceitar. A plataforma fará apenas a necessário para distinguir os gestos com suporte específicos de Desambiguidade. Dessa forma, um holograma que suporta apenas o polegar pode aceitar qualquer período de tempo entre press e versão, enquanto um holograma que dá suporte tanto tocar e segurar pode promover o tap a uma isenção após o limite de tempo de espera.

## <a name="hand-recognition"></a>Reconhecimento de mão

HoloLens reconhece gestos de mão acompanhando a posição de uma ou ambas as mãos que são visíveis para o dispositivo. HoloLens vê mãos quando estão em qualquer um de **estado está pronto** (parte posterior a mão voltada para o usuário com o dedo para cima) ou o **estado pressionado** (parte posterior a mão voltada para o usuário com o dedo para baixo). Quando as mãos estiverem em outras poses, o HoloLens irá ignorá-los.

Para cada mão que HoloLens detecta, você pode acessar sua posição (sem orientação) e seu estado pressionado. Como a mão se aproximar a borda do quadro de gesto, também são fornecidas com um vetor de direção, você pode mostrar ao usuário para que eles saibam como mover sua mão para obtê-lo novamente no qual o HoloLens podem vê-lo.

## <a name="gesture-frame"></a>Quadro de gesto

Para gestos em HoloLens, a mão deve estar em um "gesto quadro", em um intervalo em que a detecção de gesto câmeras podem ver adequadamente (muito aproximadamente de nariz para foi muito e entre os ombros). Os usuários precisam ser treinados para essa área de reconhecimento para o sucesso da ação e para seu próprios conforto (muitos usuários inicialmente pressupor que o quadro de gesto deve ser dentro de sua exibição por meio do HoloLens e mantenha a manter-se uncomfortably para interagir). Ao usar o HoloLens Clicker, suas mãos não precisa estar dentro do quadro de gesto.

No caso de gestos contínuos em particular, há alguns riscos de usuários movendo suas mãos fora do quadro de gesto no gesto intermediário (ao mover um objeto holográfico, por exemplo) e perder seu resultado pretendido.

Há três coisas que você deve considerar:
* Formação do usuário sobre o quadro de gesto existência e limites aproximados (Isso é ministrado durante a instalação do HoloLens).
* Notificar os usuários quando seus gestos estão se aproximando/últimas os limites do quadro de gesto dentro de um aplicativo, para o grau que um gesto perdido leva a resultados indesejados. Pesquisas mostram as qualidades principais de tal um sistema de notificação e o shell do HoloLens oferece um bom exemplo desse tipo de notificação (visual, no cursor central, que indica a direção em limites em que está ocorrendo cruzamento).
* Consequências de quebrar os limites de quadro do gesto devem ser minimizadas. Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite, mas não invertido. Por exemplo, se um usuário está mudando algum objeto holographic em uma sala, movimentação deve parar quando o quadro de gesto é violado, mas **não** ser retornado para o ponto de partida. O usuário pode experimentar alguns frustração em seguida, mas pode mais rapidamente entender os limites e não precisa reiniciar suas ações pretendidas completas de cada vez.

## <a name="see-also"></a>Consulte também
* [Focar direcionamento](gaze-targeting.md)
* [Design de voz](voice-design.md)
* [Entrada do MR 211: gesto](holograms-211.md)
* [Gestos e controladores de movimento no Unity](gestures-and-motion-controllers-in-unity.md)
* [Mãos e controladores de movimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Controladores de movimentos](motion-controllers.md)

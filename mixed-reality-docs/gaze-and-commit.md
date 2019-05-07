---
title: Olhar e confirmar
description: Visão geral do modelo de entrada olhar e confirmar
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Misto realidade, olhar, olhar direcionamento, interação, de design
ms.openlocfilehash: 7bce18853e46d71d963574b35c393e5a5dbf2cd0
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873983"
---
# <a name="head-gaze-and-commit"></a>Olhar head e confirmar
Olhar head e confirmação é um modelo de entrada que envolve o direcionamento de um objeto com a direção da sua cabeça que aponta para a frente (head-direção), e, em seguida, agir sobre eles com um secundário de entrada, como o gesto de mão ar toque ou a voz de comando "Select". Ele é considerado um modelo de "agora" entrado com a manipulação indireta, ou seja, que ele é mais adequado para interagir com o conteúdo que está além do braços atingir.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Olhar head e confirmar</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado (terceira opção - <a href="interaction-fundamentals.md">ver as outras opções</a>)</td>
        <td>Opção alternativa de ➕</td>
    </tr>
</table>

## <a name="head-gaze"></a>Olhar head
Realidade misturada headsets usarem a posição e orientação da cabeça do usuário para determinar seu vetor de direção principal. Você pode pensar isso como um laser que aponte diretamente para frente do diretamente entre a atenção do usuário. Isso é bastante grosso aproximação de onde o usuário está procurando. Seu aplicativo pode se cruzam esse ray com objetos reais ou virtuais e desenhar um cursor nesse local para que o usuário saiba o que eles estão visando atualmente.

Além de olhar principal, alguns fones de ouvido de realidade misturada, como o HoloLens 2 incluem sistemas que produzem um vetor de olho olhar de acompanhamento a olho nu. Isso fornece uma medida refinada de onde o usuário está procurando. É possível compilar olhar e interações de olhar de olho de confirmação, mas isso vem com um conjunto muito diferente das restrições de design, que será abordado em separadamente a [artigo de acompanhamento a olho nu](eye-tracking.md).

## <a name="commit"></a>Confirmação
Depois de direcionar um objeto ou um elemento de interface do usuário, o usuário pode interagir ou "click" nele usando uma entrada secundária. Isso é conhecido como a etapa de confirmação do modelo. Há suporte para os seguintes métodos de confirmação:

- Gesto de ar
- Fale o comando de voz "Select" ou um dos comandos de voz de destino
- Pressione o botão único um [HoloLens Clicker](hardware-accessories.md#hololens-clicker)
- Pressione o botão 'A' em um Xbox Gamepad
- Pressione o botão 'A' em um controlador adaptável do Xbox

### <a name="gaze-and-air-tap-gesture"></a>Gesto de toque de olhar e ar
Indicador e polegar é um gesto de tocar com a mão na vertical. Para executar um indicador e polegar, acionar o dedo para a posição de pronto, em seguida, aperto com o dedo e acionar seu dedo fazer backup para liberar. Em HoloLens 1, o indicador e polegar é a entrada de secundária mais comuns.

![Com o dedo na posição pronta e, em seguida, um movimento de toque ou clique em](images/readyandpress.jpg)<br>

Indicador e polegar também está disponível em HoloLens 2 e foi abrandado da versão original. Quase todos os tipos de pinches agora têm suporte, desde que a mão é ainda vertical e a espera. Isso torna muito mais fácil para os usuários a aprender e faça o gesto.  Esse novo indicador e polegar substitui o antigo por meio da API do mesma, para que os aplicativos existentes obterão o novo comportamento automaticamente após a recompilação do HoloLens 2.

### <a name="gaze-and-select-voice-command"></a>Mantenha o foco e "Selecionar" comando de voz
Comandos de voz são um dos métodos de interação primário na realidade misturada. Ele fornece um mecanismo muito eficiente "Mãos livre" para o sistema de controle. Há tipos diferente dos modelos de interação de voz:

- O comando genérico "Selecionar" que permite executar uma confirmação como uma entrada secundária ou acionar "clique".
- Comandos de objeto, como "Fechar" ou "Aumentá-lo", que permitem executar e confirmar a uma ação como uma entrada secundária.
- Commnads globais, como "Ir para iniciar" que não exigem um destino.
- Interfaces de usuário de conversa ou entidades, como Cortana que têm um recurso de linguagem Natural de inteligência Artificial.
- Commnads personalizado

Para encontrar mais detalhes e uma lista de comprenhesive de comandos disponíveis e como usar, Confira nossos [design de voz](voice-design.md) diretrizes.


### <a name="gaze-and-hololens-clicker"></a>Olhar e HoloLens Clicker
O HoloLens Clicker é o primeiro dispositivo periférico criado especificamente para o HoloLens e está incluído com a edição de desenvolvimento HoloLens 1. O HoloLens Clicker permite que um usuário clicar com o movimento de mão mínima e confirmadas como uma entrada secundária. O HoloLens clicker conecta-se para o HoloLens 1 ou 2 usando Bluetooth baixa energia (BTLE).

![](images/hololens-clicker-500px.jpg)<br>
HoloLens Clicker

Mais informações e instruções para emparelhar o dispositivo podem ser encontradas [aqui](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="gaze-and-xbox-wireless-controller"></a>Olhar e controlador sem fio do Xbox
O controlador do Xbox sem fio permite executar acionar um "clique" como um secundário, usando o botão de entrada. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema. Se você desejar personalizar o controlador, use o Xbox Accesories App para configurar seu controlador do Xbox sem fio.

![](images/xboxcontroller.jpg)<br>
Controlador sem fio do Xbox

[Emparelhamento de um controlador do Xbox com seu PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="gaze-and-xbox-adaptive-controller"></a>Controlador adaptável olhar e Xbox
O controlador do Xbox adaptável projetado principalmente para atender às necessidades de jogadores com mobilidade limitada, é um hub unificado para dispositivos que ajuda a tornar realidade misturada mais acessível.

O controlador de adaptável do Xbox permite executar acionar um "clique" como um secundário, usando o botão de entrada. O dispositivo é mapeado para um conjunto padrão de ações que ajudam a navegar e controlar o sistema. Se você desejar personalizar o controlador, use o Xbox Accesories App para configurar seu controlador adaptável do Xbox.

![](images/xbox-adaptive-controller-devices.jpg)<br>
Controlador do Xbox adaptável

Conecte dispositivos externos, como comutadores, botões, montagens e joysticks para criar uma experiência personalizada de controladores que é exclusivamente sua. Entradas de botão, direcional e disparador são controladas com dispositivos assistenciais conectados por meio de tomadas de 3,5 mm e portas USB.

![](images/xbox-adaptive-controller-ports.jpg)<br>
Portas de controle adaptável do Xbox

[Instruções para emparelhar o dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Mais informações disponíveis no site do Xbox</a>


# <a name="device-support"></a>Suporte a dispositivos
Mantenha o foco principal e confirmação está disponível em todos os fones de ouvido de realidade misturada. É o modelo de entrada primário em HoloLens v1. Outros headsets normalmente incluem um mecanismo apontador com base em mãos, de como os controladores de movimento ou articulada mão de acompanhamento. Nesses dispositivos, aplicativos devem preferir [ponto-e-confirmação](point-and-commit.md) para interações mais distantes quando possível.

Olhar olho e confirmação está disponível em HoloLens 2, mas não é o modelo de entrada principal. Vá para a seção de "Diretrizes de design de olhar olho" para uma discussão sobre isso fizer sentido para seu aplicativo.

# <a name="head-gaze-design-guidelines"></a>Diretrizes de design de olhares head
> [!NOTE]
> Orientação mais específica para design de olhares [em breve](index.md).

## <a name="gaze-targeting"></a>Mantenha o foco de direcionamento
Todas as interações baseiam-se a capacidade de um usuário para o elemento que eles querem interagir, independentemente da modalidade de entrada de destino. Na realidade mista do Windows, isso geralmente é feito usando olhar do usuário.
Para habilitar um usuário trabalhar com uma experiência com êxito, as Noções básicas sobre calculado do sistema de intenção do usuário e a intenção do usuário real, deve se alinhar o mais próximo possível. Para o grau que o sistema interpreta as ações do usuário pretendida corretamente, aumenta a satisfação e o desempenho melhora.


## <a name="target-sizing-and-feedback"></a>Comentários e dimensionamento de destino
O vetor de olhar mostrado repetidamente para ser usado para direcionar tudo bem, mas geralmente funciona melhor para brutos direcionamento (ao adquirir um pouco maiores destinos). Tamanhos de destino mínimo de 1 a 1,5 graus devem permitir que as ações do usuário bem-sucedida na maioria dos cenários, embora normalmente permitem destinos de graus de 3 para maior velocidade. Observe que o tamanho que os destinos de usuário é efetivamente uma área 2D até mesmo para elementos 3D – qualquer projeção é voltado para a eles deve ser a área a ser direcionada. Fornecer alguma indicação evidente que um elemento está "ativo" (que o usuário está direcionando-la) é extremamente útil – isso pode incluir tratamentos como efeitos de "passagem" visível, destaques de áudio ou cliques ou desmarque o alinhamento de um cursor com um elemento.

![Tamanho de destino ideal a distância do medidor 2](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho de destino ideal a distância do medidor 2*

![Um exemplo de realce de um objeto de destino de olhar](images/gazetargeting-highlighting-640px.jpg)<br>
*Um exemplo de realce de um objeto de destino de olhar*

## <a name="target-placement"></a>Posicionamento de destino
Os usuários geralmente não encontrarão encontrar elementos de interface do usuário são posicionados muito alto ou muito baixo em seu campo de visão, concentrando-se a maior parte de sua atenção nas áreas em torno de seu foco principal (geralmente aproximadamente nível dos olhos). Pode ajudar a colocar a maioria dos destinos em alguns banda razoável em torno do nível dos olhos. Dada a tendência para os usuários para se concentrar em uma área visual relativamente pequena a qualquer momento (attentional cone de visão é aproximadamente 10 graus), agrupar elementos de interface do usuário para o grau que elas estão relacionadas conceitualmente pode aproveitar comportamentos de encadeamento de atenção do item a item como um usuário move seu olhar por meio de uma área. Ao projetar a interface do usuário, tenha em mente a variação grande potencial no campo de exibição entre HoloLens e fones imersivos em exposição.

![Um exemplo dos elementos de interface do usuário agrupados para olhar mais fáceis de direcionamento no Explorer Galaxy](images/gazetargeting-grouping-1000px.jpg)<br>
*Um exemplo dos elementos de interface do usuário agrupados para olhar mais fáceis de direcionamento no Explorer Galaxy*

## <a name="improving-targeting-behaviors"></a>Melhorando a comportamentos de direcionamento
Se a intenção do usuário para algo de destino pode ser determinada (ou aproximada de perto), ele pode ser muito útil aceitar "near Srta" tenta a interação como se eles foram direcionados corretamente. Há um punhado de métodos bem-sucedidas que podem ser incorporados em experiências de realidade mista:

### <a name="gaze-stabilization-gravity-wells"></a>Estabilização olhar ("wells gravidade")
Essa deve ser ligado a maioria ou todos do tempo. Essa técnica remove os jitters head/pescoço natural que os usuários podem ter. Também movimento devido a comportamentos de busca/falando.

### <a name="closest-link-algorithms"></a>Algoritmos mais próximo do link
Eles funcionam melhor em áreas com conteúdo interativo esparsa. Se houver uma grande probabilidade de que você pode determinar o que um usuário estava tentando interagir com, você pode complementar suas habilidades de direcionamento por simplesmente supondo que algum nível de intenção.

### <a name="backdatingpostdating-actions"></a>Ações backdating/postdating
Esse mecanismo é útil para tarefas que precisam de velocidade. Quando um usuário está movendo por meio de uma série de direcionamento/ativação evasivas na velocidade, pode ser útil a assumir alguns intenção e permitir etapas ausentes atuar em destinos que o usuário tinha em foco um pouco antes ou depois de um pouco o tap (50 ms antes/depois foi eficaz em no início de teste).

### <a name="smoothing"></a>Suavização
Esse mecanismo é útil para movimentos de caminhos, reduzindo a tremulação/wobble pequena devido às características de movimentação do cabeçote natural. Quando a suavização ao longo de movimentos de caminhos, suaves por tamanho/distância de movimentos em vez de ao longo do tempo

### <a name="magnetism"></a>Magnetism
Esse mecanismo pode ser pensado como uma versão mais geral de algoritmos "Vincular mais próximo" - desenhar um cursor em direção a um destino ou simplesmente aumentar hitboxes (seja visivelmente ou não) como os usuários provavelmente destinos de abordagem, usando algum conhecimento sobre o layout interativo para intenção do usuário abordagem melhor. Isso pode ser particularmente poderoso para destinos pequeno.

### <a name="focus-stickiness"></a>Adesão de foco
Ao determinar qual próximos elementos interativos para dar o foco para o, forneça uma tendência para o elemento que tem o foco. Isso ajudará a reduzir o foco irregular alternância comportamentos quando flutuante em um ponto médio entre dois elementos com ruído natural.


## <a name="composite-gestures"></a>Gestos de composição
Aplicativos podem reconhecer os toques de mais de apenas individuais. Pela combinação de toque, mantenha e de versão com o movimento da mão, gestos de composição mais complexos podem ser executados. Esses gestos de alto nível ou compostos dependem de baixo nível entrados dados espaciais (de indicador e polegar e Bloom) que os desenvolvedores têm acesso ao.

### <a name="air-tap"></a>Indicador e polegar
O gesto de toque de ar (bem como outros gestos abaixo) reage somente a um toque específico. Para detectar outras toques, como o Menu ou compreensão, seu aplicativo deve usar diretamente as interações de baixo nível descritas na seção de gestos de dois componentes principais acima.

### <a name="tap-and-hold"></a>Tap e hold
Espera é simplesmente manter a posição do dedo para baixo do indicador e polegar. A combinação de ar tap e hold permite uma variedade de interações mais complexas de "clique e arraste" quando combinado com a movimentação do arm como pegar um objeto em vez de ativá-la ou interações de secundário "mousedown" como mostrar um menu de contexto.
Tenha cuidado ao projetar para esse gesto no entanto, como os usuários pode estar sujeita a relaxar postures suas mãos no decorrer de quaisquer gesto estendido.

### <a name="manipulation"></a>Manipulação
Gestos de manipulação podem ser usados para mover, redimensionar ou girar um holograma quando desejar que o holograma reagir 1:1 para movimentações de mão do usuário. Um uso para tais movimentações de 1:1 é permitir que o usuário desenha ou pintar no mundo.
O direcionamento inicial um gesto de manipulação de deve ser feito pelo olhar ou apontando. Depois que o tap e hold é iniciado, qualquer manipulação do objeto, em seguida, é tratada manualmente os movimentos, liberando o usuário para olhar em volta, embora eles manipulam.

### <a name="navigation"></a>Navegação
Gestos de navegação funcionam como um joystick virtual e podem ser usados para navegar de widgets de interface do usuário, como menus radiais. Toque e segure para iniciar o gesto e, em seguida, mova a mão dentro de um cubo 3D normalizado, centralizada em torno de imprensa inicial. Você pode mover sua mão ao longo do eixo X, Y ou Z de um valor de -1 para 1 com 0 sendo o ponto de partida.
Navegação pode ser usada para criar com base em velocidade de rolagem contínua ou gestos de zoom, semelhantes a uma interface do usuário de 2D de rolagem clicando no botão do meio do mouse e, em seguida, mover o mouse para cima para baixo.

A navegação com o rails refere-se à capacidade de reconhecer os movimentos no certo eixo até certo limite é atingido naquele eixo. Isso só é útil, quando o movimento em mais de um eixo está habilitado em um aplicativo pelo desenvolvedor, por exemplo, se um aplicativo é configurado para reconhecer gestos de navegação em X, eixo Y, mas também especificado eixo com trilhos X. Nesse caso, sistema reconhecerá movimentos de mão em eixo X, desde que eles permaneçam dentro de um imaginário rails (guia) no eixo, X se o movimento de mão também ocorre eixo Y.

Em aplicativos 2D, os usuários podem usar gestos de navegação vertical para rolar, aplicar zoom ou arraste dentro do aplicativo. Isso injeta toques de dedo virtual para o aplicativo para simular os gestos de toque do mesmo tipo. Os usuários podem selecionar qual das seguintes ações ocorrem alternando entre as ferramentas na barra de acima do aplicativo, selecionando o botão ou dizendo '< rolagem/arrastar/Zoom > ferramenta'.

[Mais informações sobre gestos de composição](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconhecedores de gestos

Uma vantagem de usar o reconhecimento de gesto é que você pode configurar um reconhecedor de gestos apenas para os gestos que de destino atual holograma pode aceitar. A plataforma fará apenas a necessário para distinguir os gestos com suporte específicos de Desambiguidade. Dessa forma, um holograma que suporta apenas o polegar pode aceitar qualquer período de tempo entre press e versão, enquanto um holograma que dá suporte tanto tocar e segurar pode promover o tap a uma isenção após o limite de tempo de espera.

## <a name="hand-recognition"></a>Reconhecimento de mão
HoloLens reconhece gestos de mão acompanhando a posição de uma ou ambas as mãos que são visíveis para o dispositivo. HoloLens vê mãos quando estiverem no estado pronto (parte posterior a mão voltada para o usuário com o dedo para cima) ou no estado pressionado (parte posterior a mão voltada para o usuário com o dedo para baixo). Quando as mãos estiverem em outras poses, o HoloLens irá ignorá-los.
Para cada mão que HoloLens detecta, você pode acessar sua posição (sem orientação) e seu estado pressionado. Como a mão se aproximar a borda do quadro de gesto, também são fornecidas com um vetor de direção, você pode mostrar ao usuário para que eles saibam como mover sua mão para obtê-lo novamente no qual o HoloLens podem vê-lo.

## <a name="gesture-frame"></a>Quadro de gesto
Para gestos em HoloLens, a mão deve estar em um "gesto quadro", em um intervalo em que a detecção de gesto câmeras podem ver adequadamente (muito aproximadamente de nariz para foi muito e entre os ombros). Os usuários precisam ser treinados para essa área de reconhecimento para o sucesso da ação e para seu próprios conforto (muitos usuários inicialmente pressupor que o quadro de gesto deve ser dentro de sua exibição por meio do HoloLens e mantenha a manter-se uncomfortably para interagir). Ao usar o HoloLens Clicker, suas mãos não precisa estar dentro do quadro de gesto.

No caso de gestos contínuos em particular, há alguns riscos de usuários movendo suas mãos fora do quadro de gesto no gesto intermediário (ao mover um objeto holográfico, por exemplo) e perder seu resultado pretendido.

Há três coisas que você deve considerar:

- Formação do usuário sobre o quadro de gesto existência e limites aproximados (Isso é ministrado durante a instalação do HoloLens).

- Notificar os usuários quando seus gestos estão se aproximando/últimas os limites do quadro de gesto dentro de um aplicativo, para o grau que um gesto perdido leva a resultados indesejados. Pesquisas mostram as qualidades principais de tal um sistema de notificação e o shell do HoloLens oferece um bom exemplo desse tipo de notificação (visual, no cursor central, que indica a direção em limites em que está ocorrendo cruzamento).

- Consequências de quebrar os limites de quadro do gesto devem ser minimizadas. Em geral, isso significa que o resultado de um gesto deve ser interrompido no limite, mas não invertido. Por exemplo, se um usuário está mudando algum objeto holographic em uma sala, movimentação deve parar quando o quadro de gesto for ultrapassado, mas não ser retornado para o ponto de partida. O usuário pode experimentar alguns frustração em seguida, mas pode mais rapidamente entender os limites e não precisa reiniciar suas ações pretendidas completas de cada vez.


## <a name="see-also"></a>Consulte também
* [Manipulação direta](direct-manipulation.md)
* [Ponto e confirmar](point-and-commit.md)
* [Conceitos básicos de interação](interaction-fundamentals.md)
* [Olhar e duração](gaze-targeting.md)
* [Olhar e voz](voice-design.md)






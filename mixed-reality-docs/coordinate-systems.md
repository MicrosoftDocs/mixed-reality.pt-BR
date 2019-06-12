---
title: Sistemas de coordenadas
description: Os sistemas de coordenadas espaciais usados para construir sentado, permanente, sala de escala e dimensionamento do mundo misto experiências realidade.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espacial, somente orientação, encaixado em escala, escala de pé, sala de escala, escala mundial, 360 graus, encaixado, permanente, sala, mundo, escala, posição, orientação, parado, anexado, estágio, âncora, âncora espacial, bloqueado pelo mundo, bloqueando o mundo, bloqueado de corpo, bloqueio de corpo, limites, persistência, compartilhamento, controlando a perda, espacial âncora de nuvem
ms.openlocfilehash: f4b945a3ffb83b9ac0a94e0d793a19939aece3bb
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829865"
---
# <a name="coordinate-systems"></a>Sistemas de coordenadas

Em sua essência, misto local de aplicativos de realidade [hologramas](hologram.md) no seu mundo que pareçam e parecer objetos reais. Isso envolve precisamente posicionamento e a orientação desses hologramas em locais no mundo que são significativas para o usuário, se o mundo é seu espaço físico ou um território virtual que você criou. Ao raciocinar sobre a posição e orientação de seu hologramas ou qualquer outro tipo de geometria, como o [olhares](gaze.md) ray ou [entregar posições](gestures.md), Windows fornece diversos sistemas de coordenadas do mundo real na qual geometria pode ser expressos, conhecido como **sistemas de coordenadas espaciais**.

<br>

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td><a href="coordinate-systems.md#stationary-frame-of-reference">Quadro estacionário de referência</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#attached-frame-of-reference">Quadro de referência anexado</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#stage-frame-of-reference">Estágio de quadro de referência</a></td>
        <td>Ainda não tem suporte</td>
        <td>Ainda não tem suporte</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#spatial-anchors">Âncoras espaciais</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="spatial-mapping.md">Mapeamento espacial</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="mixed-reality-experience-scales"></a>Escalas de experiência de realidade misturada

Aplicativos de realidade misturada podem projetar uma ampla variedade de experiências do usuário, dos visualizadores de vídeos de 360 graus que precisam apenas de orientação do fone de ouvido, para aplicativos de escala mundial completo e jogos, que precisam de mapeamento espacial e âncoras espaciais:
<br>

| Escala de experiência | Requisitos | Experiência de exemplo | 
|----------|----------|----------|
|  **Somente orientação** |  **Orientação de fone de ouvido** (alinhado à gravidade) |  Visualizador de vídeo de 360° | 
|  **Seated-scale** |  Acima, o sinal de adição **posição fone de ouvido** em relação à posição zero |  Simulador de jogo ou no espaço de corrida | 
|  **Escala permanente** |  Acima, plus **preparar origem floor** |  Jogo de ação onde você jantar e dodge em vigor  | 
|  **Room-scale** |  Acima, plus **polígono de limites de estágio** |  Quebra-cabeça jogo em que você percorrer o quebra-cabeça | 
|  **World-scale** |  **Âncoras espaciais** (e geralmente [mapeamento espacial](spatial-mapping.md)) |  Jogo com inimigos provenientes de parede real, tais como [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

Essas experiência escalas seguem um modelo de "bonecas de aninhamento". O princípio de design fundamental para o Windows Mixed Reality é determinado um fone de ouvido dá suporte a aplicativos criados para uma escala de experiência de destino, bem como dimensiona todos menos:
<br>

| Acompanhamento de 6DOF | Floor definido | Acompanhamento de 360° | Dos limites definidos | Âncoras espaciais | Experiência de max | 
|----------|----------|----------|----------|----------|----------|
|  Não |  - |  - |  - |  - |  **Somente orientação** | 
|  **Sim** |  Não |  - |  - |  - |  **Encaixado** | 
|  **Sim** |  **Sim** |  Não |  - |  - |  **Aguardando - Forward** | 
|  **Sim** |  **Sim** |  **Sim** |  Não |  - |  **Posição - 360°** | 
|  **Sim** |  **Sim** |  **Sim** |  **Sim** |  Não |  **Room** | 
|  **Sim** |  **Sim** |  **Sim** |  **Sim** |  **Sim** |  **mundo** | 

Observe que o estágio quadro de referência ainda não é suportado em HoloLens. Um aplicativo em escala de espaço em HoloLens atualmente precisa usar [mapeamento espacial](spatial-mapping.md) para localizar o usuário piso e paredes.

## <a name="spatial-coordinate-systems"></a>Sistemas de coordenadas espaciais

Usam todos os aplicativos de gráficos 3D [sistemas de coordenadas cartesianas](https://docs.microsoft.com/windows/uwp/graphics-concepts/coordinate-systems) raciocinar sobre as posições e orientações de objetos nos mundos virtuais que eles sejam renderizados. Esses sistemas de coordenadas estabelecer 3 eixos perpendiculares ao longo do qual posicionar objetos: um eixo X, Y e Z.

Na [realidade misturada](mixed-reality.md), seus aplicativos serão argumentar sobre os sistemas de coordenadas físicos e virtuais. Windows chama um sistema de coordenadas que tem um significado real no mundo físico uma **sistema de coordenadas espacial**.

Sistemas de coordenadas espaciais expressar seus valores de coordenada em metros. Isso significa que os objetos colocados 2 unidades de distância no X, eixo Y ou Z aparecerá 2 metros distantes um do outro quando renderizado em realidade misturada. Isso permite que você facilmente processar objetos e ambientes em escala do mundo real.

Em geral, os sistemas de coordenadas cartesianas podem ser destro ou canhoto. Sistemas de coordenadas espaciais no Windows são sempre destros, que significa que o positivo eixo x aponta diretamente, os positivos do eixo y aponta para cima (alinhado à gravidade) e o positivo eixo z aponta em direção a você.

Em ambos os tipos de sistemas de coordenadas, positivo eixo x aponta para a direita e o eixo y positivo aponta para cima. A diferença é se o positivos do eixo z aponta em direção ou para fora. Você pode se lembrar a direção na qual o positivos do eixo z aponta, apontando os dedos do seu esquerda ou direita em positivo X direção e ondulação-los para a direção de Y positiva. A direção em que o polegar aponta, em direção ou para fora, é a direção do eixo positivo z aponta para esse sistema de coordenadas.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Criação de uma experiência somente orientação ou encaixado em escala

A chave para holographic [renderização](rendering.md) está mudando a exibição do seu aplicativo de seus hologramas cada quadro quando o usuário move ao redor, para corresponder ao seu movimento principal previsto. Você pode compilar **escala encaixado experiências** que respeito muda para a posição do usuário principal e orientação principal usando uma **quadro estacionário de referência**.

Algum conteúdo deve ignorar as atualizações de posição principal, permanecendo fixo em um título escolhido e distância do usuário em todos os momentos. O principal exemplo é um vídeo de 360 graus: porque o vídeo é capturado de uma única perspectiva fixa, ele seria arruinando a ilusão para a posição de exibição mover em relação ao conteúdo, mesmo que a orientação da exibição deve alterar conforme o usuário procura ao redor. Você pode criar tal **experiências de orientação** usando uma **anexado o quadro de referência**.

### <a name="stationary-frame-of-reference"></a>Quadro estacionário de referência

O sistema de coordenadas fornecido por um quadro estacionário de referência funciona para manter as posições dos objetos próxima ao usuário mais estável possível em relação ao mundo, respeitando as alterações na posição de principal do usuário.

Para dimensionamento encaixado experiências, como em um mecanismo de jogo [Unity](https://unity3d.com/), um quadro estacionário de referência é o que define "mundo origem" do mecanismo. Objetos que são colocados em uma coordenada de mundo específica usam o quadro estacionário de referência para definir sua posição no mundo real usando essas mesmas coordenadas. Conteúdo que permanece é colocado no mundo, mesmo que os usuários se deslocam, é conhecido como **bloqueada pelo mundo** conteúdo.

Um aplicativo normalmente será criar um quadro estacionário de referência na inicialização e usar seu sistema de coordenadas em todo o tempo de vida do aplicativo. Como desenvolvedor de aplicativos no Unity, você pode iniciar apenas colocando conteúdo relativo à origem, que estará em posição de cabeçalho inicial e a orientação do usuário. Se o usuário move para um novo local e deseja continuar sua experiência de escala encaixado, você pode centralizar novamente a origem do mundo nesse local.

Ao longo do tempo, como o sistema aprende mais sobre o ambiente do usuário, ele pode determinar que as distâncias entre vários pontos no mundo real são menor ou maior que o sistema anteriormente acredita-se. Se você renderizar hologramas em um quadro estacionário de referência para um aplicativo em HoloLens, em que os usuários Peregrino além de uma área amplas cerca de 5 metros, seu aplicativo pode observar o descompasso no local desses hologramas observado. Se a sua experiência tem usuários wandering além dos medidores de 5, você está compilando uma [experiência de dimensionamento do mundo](#building-a-world-scale-experience), que exigirá técnicas adicionais para manter hologramas estável, conforme descrito abaixo.

### <a name="attached-frame-of-reference"></a>Quadro de referência anexado

Um quadro de referência anexado move-se com o usuário conforme eles ir, com um título fixo definido quando o aplicativo primeiro cria o quadro. Isso permite que o usuário ver confortavelmente em torno do conteúdo colocado dentro desse quadro de referência. Conteúdo renderizado dessa maneira relativo do usuário é chamado **bloqueado de corpo** conteúdo.

Quando o fone de ouvido não consegue descobrir onde ele está no mundo, um quadro de referência anexado fornece o único sistema de coordenadas que pode ser usado para renderizar hologramas. Isso o torna ideal para a exibição de fallback da interface do usuário para informar ao usuário que seu dispositivo não é possível encontrá-las no mundo. Aplicativos que estão encaixadas em escala ou superior devem incluir um fallback apenas orientação para ajudar o usuário comece novamente, com a interface do usuário semelhante à mostrada na [realidade misturada doméstica](navigating-the-windows-mixed-reality-home.md).

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Criar uma experiência de escala permanente ou de escala de espaço

Para ir além do dimensionamento encaixado em um fone de ouvido envolvente e criar uma **experiência de escala de pé**, você pode usar o **estágio quadro de referência**.

Para fornecer um **experiência de escala de sala**, permitindo usuários ronda dentro do limite do medidor de 5 elas previamente definidas, você pode verificar **estágio limites** também.

### <a name="stage-frame-of-reference"></a>Estágio de quadro de referência

Ao configurar primeiro um fone de ouvido imersivo, o usuário define uma **estágio**, que representa o espaço no qual eles terão de realidade misturada. O estágio minimamente define uma **preparar origem**, um sistema de coordenadas espacial centralizado no usuário escolhida posição de base e a orientação de encaminhamento em que ele pretende usar o dispositivo. Colocando o conteúdo no sistema de coordenadas estágio no plano de Chão de Y = 0, você pode garantir seu hologramas confortavelmente aparecem no chão quando o usuário está aguardando, fornecendo aos usuários com um **experiência de escala de pé**.

### <a name="stage-bounds"></a>Limites de estágio

O usuário também pode definir **estágio limites**, realidade misturada de uma área dentro da sala que eles desmarcou móvel em que ele pretende mover-se no. Se assim, o aplicativo pode criar uma **experiência de escala de sala**, usando esses limites para garantir que hologramas sempre são colocadas em que o usuário pode encontrá-los.

Como o quadro de referência do estágio oferece que fixo de um único sistema de coordenadas na qual você deseja colocar o conteúdo relativo ao chão, ele é o caminho mais fácil para portabilidade de escala de uma posição e aplicativos de escala de sala desenvolvidos para fones de ouvido de realidade virtual. No entanto, como com essas plataformas VR, um único sistema de coordenadas só pode se estabilizar conteúdo sobre um diâmetro do medidor 5 (16 pés), antes de arm alavanca efeitos causam conteúdo longe de ser o centro para deslocar visivelmente conforme o sistema ajusta. Para ir além dos 5 metros, âncoras espaciais são necessários.

## <a name="building-a-world-scale-experience"></a>Criar uma experiência de dimensionamento do mundo

True permite HoloLens **experiências do mundo em escala** que permitem aos usuários percorrer além dos 5 metros. Para criar um aplicativo de dimensionamento do mundo, você precisará de novas técnicas além daquelas usadas para experiências de sala em escala.

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>Por que um único sistema de coordenadas rígido não pode ser usado além dos medidores de 5

Hoje, ao escrever jogos, aplicativos de visualização de dados ou aplicativos de realidade virtual, a abordagem típica é estabelecer um sistema de coordenadas de mundo absoluto todas as outras coordenadas confiável podem mapear para. Nesse ambiente, você sempre pode encontrar uma transformação estável que define uma relação entre dois objetos nesse mundo. Se você não mover esses objetos, suas transformações relativas sempre permanecerão os mesmos. Esse sistema de coordenadas global de funciona bem quando a renderização de um mundo puramente virtual em que você sabe tudo da geometria com antecedência. Aplicativos em escala de sala de VR hoje em dia normalmente estabelecem esse tipo de sistema de coordenadas absolutas de escala de sala com sua origem no chão.

Por outro lado, um dispositivo de realidade misturada ilimitado, como o HoloLens tem uma compreensão dinâmica controlado por sensor do mundo, ajustando continuamente seu conhecimento ao longo do tempo do ambiente do usuário como conduzem vários medidores em um inteiro andar de um prédio. Em uma experiência de dimensionamento do mundo, se você colocou todos os seus hologramas em um único sistema de coordenadas rígido, esses hologramas seriam necessariamente descompasso ao longo do tempo, em relação ao mundo ou uns aos outros.

Por exemplo, o fone de ouvido pode acreditar no momento, os dois locais no mundo ser 4 metros de distância e, em seguida, posteriormente, refinar essa compreensão, os locais são na verdade 3.9 metros de distância de aprendizado. Se esses hologramas tinham inicialmente foi colocadas 4 medidores separados em um único sistema de coordenadas rígido, um deles, em seguida, sempre apareceria 0,1 metros fora do mundo real.

### <a name="spatial-anchors"></a>Âncoras espaciais

Windows Mixed Reality resolve o problema descrito na seção anterior, permitindo que você crie [âncoras espaciais](spatial-anchors.md) para marcar pontos importantes no mundo em que o usuário tiver efetuado hologramas. Uma âncora espacial representa um ponto importante no mundo do que o sistema deve manter o controle de ao longo do tempo.

Como o dispositivo aprende sobre o mundo, essas âncoras espaciais podem ajustar sua posição em relação a uma outra conforme necessário para garantir que cada âncora permaneça precisamente onde ele foi colocado em relação ao mundo real. Colocando uma âncora espacial no local em que o usuário coloca um holograma e, em seguida, posicionamento desse holograma em relação à sua âncora espacial, você pode garantir que o holograma mantém estabilidade ideal, mesmo que o usuário passa em dezenas de medidores.

Esse ajuste contínuo das âncoras espaciais a relação é a principal diferença entre coordinate systems de âncoras espaciais e quadros de referência estáticos:

* Hologramas colocadas no quadro estacionário de referência todos os mantêm uma relação rígida umas às outras. No entanto, como os usuários se deslocam longas distâncias, sistema de coordenadas do quadro pode descompasso em relação ao mundo para garantir que hologramas ao lado do usuário aparecem estáveis.

* Hologramas colocadas no estágio quadro de referência também mantêm uma relação rígida umas às outras. Em contraste com o quadro estacionário, o quadro de estágio sempre permanece fixado em vigor em relação à origem física definida. No entanto, conteúdo renderizado no sistema de coordenadas do estágio além do seu limite de 5 medidor só aparecerá estável enquanto o usuário está tentando funcionar dentro desse limite.

* Hologramas colocadas usando uma âncora espacial pode oscilar em relação ao hologramas colocado usando outro âncora espacial. Isso permite que o Windows melhorar sua compreensão da posição de cada âncora espacial, mesmo se, por exemplo, um por âncora precisa ajustar próprio à esquerda e outro por âncora precisa ajustar à direita.

Em contraste com um quadro estacionário de referência, que sempre otimiza para estabilidade próxima ao usuário, o estágio de quadro de referência e âncoras espaciais garantem a estabilidade do próximo suas origens. Isso ajuda a esses hologramas continuam com precisão no lugar ao longo do tempo, mas isso também significa que hologramas renderizadas muito longe da origem do seu sistema de coordenadas experimentará os efeitos de cada vez mais graves alavanca-arm. Isso ocorre porque os pequenos ajustes para a posição e orientação do estágio ou âncora são ampliados proporcional à distância dessa âncora. 

Uma boa regra prática é garantir que nada que é renderizado com base no sistema de coordenadas de um distante âncora espaciais está em cerca de 3 medidores de sua origem. Para uma origem de estágio próximos, o conteúdo de distante de renderização é Okey, pois qualquer erro posicional maior afetará hologramas apenas pequenas que não mudará muito no modo de exibição do usuário.

### <a name="spatial-anchor-persistence"></a>Persistência de âncora espacial

Âncoras espaciais também podem permitir que seu aplicativo se lembrar de um local importante mesmo depois que seu aplicativo for suspenso ou o dispositivo está desligado.

Você pode salvar as âncoras espaciais cria seu aplicativo de disco e, em seguida, carregá-los novamente mais tarde, mantendo-os para seu aplicativo **repositório de âncora espacial**. Ao salvar ou carregar uma âncora, você fornece uma chave de cadeia de caracteres que seja significativa para seu aplicativo, para identificar a âncora mais tarde. Considere esta chave como o nome do arquivo para a âncora. Se você deseja associar a essa âncora de outros dados, como um modelo 3D que o usuário é colocado nesse local, salve que para o armazenamento local do seu aplicativo e associá-la com a chave que você escolheu.

Por âncoras persistir no armazenamento, seus usuários podem colocar hologramas individuais ou colocar um espaço de trabalho ao redor do qual um aplicativo colocar seus vários hologramas e, em seguida, localize esses hologramas posteriormente em que eles esperam que, ao longo de muitos usos do seu aplicativo.

Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para persistência holograma assíncrona em dispositivos Android, iOS e HoloLens.  Compartilhando uma âncora de nuvem durável espacial, vários dispositivos podem observar o holograma persistente mesmo ao longo do tempo, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo.

### <a name="spatial-anchor-sharing"></a>Compartilhamento de âncora espacial

Seu aplicativo também pode compartilhar uma âncora espacial em tempo real com outros dispositivos, permitindo em tempo real compartilhado experiências.

Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a>, seu aplicativo pode compartilhar uma âncora espacial entre vários HoloLens, dispositivos iOS e Android. Fazendo com que cada dispositivo renderizar um holograma usando a mesma âncora espacial, todos os usuários verão o holograma aparecem no mesmo lugar no mundo real.

## <a name="avoid-head-locked-content"></a>Evite conteúdo bloqueado de cabeça

Nós não recomendamos a renderização de conteúdo bloqueado de cabeçalho, que permanece em um ponto fixo na exibição (como um HUD). Em geral, conteúdo bloqueado de cabeça é desconfortável para usuários e não se parecem com uma parte natural do seu mundo.

Conteúdo bloqueado pelo head geralmente deve ser substituído pelo hologramas que estão anexadas ao usuário ou colocadas no mundo em si. Por exemplo, [cursores](cursors.md) deve normalmente ser enviado para o mundo, dimensionamento naturalmente para refletir a posição e a distância do objeto em olhar do usuário.

## <a name="handling-tracking-errors"></a>Rastreamento de tratamento de erros

Em alguns ambientes, como corredores escuros, pode não ser possível que um fone de ouvido usando o controle de dentro para fora para localizar-se corretamente no mundo. Isso pode levar hologramas não aparecem ou aparecem em locais incorretos se tratadas de forma incorreta. Agora, discutiremos as condições em que isso pode acontecer, seu impacto na experiência do usuário, e dicas para melhor lidar com essa situação.

### <a name="headset-cannot-track-due-to-insufficient-sensor-data"></a>Não é possível acompanhar o fone de ouvido devido a dados de sensor insuficiente

Às vezes, os sensores do fone de ouvido não são capazes de descobrir onde está o fone de ouvido. Isso pode acontecer se a sala está escura, ou se os sensores são cobertos por fios ou mãos, ou se o ambiente não tem suficiente textura.

Quando isso acontece, o fone de ouvido será possível acompanhar sua posição com precisão suficiente para processar hologramas bloqueado pelo mundo. Você não conseguirá descobrir onde uma âncora espacial, o quadro estacionário ou o quadro de estágio é relativo ao dispositivo, mas você ainda pode renderizar conteúdo bloqueado de corpo o quadro de referência anexado.

Seu aplicativo deve informar ao usuário como obter posicionais de acompanhamento, algum conteúdo fallback bloqueado de corpo que descreve algumas dicas, como descobrir os sensores e ativar mais luzes de renderização.

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>Controla o fone de ouvido incorretamente devido a alterações dinâmicas no ambiente

Às vezes, o dispositivo não é possível acompanhar corretamente se houver muitas alterações dinâmicas no ambiente, como muitas pessoas andando na sala. Nesse caso, as hologramas podem parecer saltar ou descompasso conforme o dispositivo tenta controlar em si neste ambiente dinâmico. É recomendável usar o dispositivo em um ambiente dinâmico menos se você atingir esse cenário.

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>Headset rastreia incorretamente porque o ambiente foi alterado significativamente ao longo do tempo

Às vezes, quando você começar a usar um fone de ouvido em um ambiente que passou por muitas alterações (por exemplo, a movimentação significativa móvel, parede hangings etc.), é possível que alguns hologramas poderão parecer deslocadas de seus locais originais. As hologramas anteriores também podem pular em torno de quando o usuário move ao redor nesse novo espaço. Isso ocorre porque não contém uma compreensão do sistema do seu espaço e tenta remapear o ambiente durante a tentativa de reconciliar os recursos da sala. Nesse cenário, é recomendável encorajar os usuários a colocar novamente hologramas eles fixado no mundo se eles não estão aparecendo em que o esperado.

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>Controla o fone de ouvido incorretamente devido a espaços idêntico em um ambiente

Às vezes, uma casa ou outro espaço pode ter duas áreas idênticas. Por exemplo, duas salas de conferência idênticos, dois idênticos canto áreas, dois grandes cartazes idênticos que abrangem o campo de visão do dispositivo. Nesses cenários, o dispositivo pode, às vezes, ficam confuso entre as partes idênticas e marcá-los como o mesmo em sua representação interna. Isso pode causar as hologramas de algumas áreas para aparecer em outros locais. O dispositivo pode começar a perder o controle com frequência, pois sua representação interna do ambiente foi corrompida. Nesse caso, é aconselhável para redefinir a compreensão de ambiente do sistema. Observe que redefinir o mapa leva à perda de todos os posicionamentos de âncora espacial. Isso fará com que o headset controlar o exclusivo para áreas do ambiente. No entanto, o problema pode ocorrer novamente se o dispositivo obtém confuso entre as áreas idênticas novamente.

## <a name="see-also"></a>Consulte também
* [Apresentação do GDC 2017 na renderização holográfica e sistemas de coordenadas espaciais](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Sistemas de coordenadas no Unity](coordinate-systems-in-unity.md)
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md)
* [Âncoras espaciais](spatial-anchors.md)
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* [Estudo de caso - examinando buracos na sua realidade](case-study-looking-through-holes-in-your-reality.md)

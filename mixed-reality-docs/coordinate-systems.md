---
title: Sistemas de coordenadas
description: Os sistemas de coordenadas espaciais usados para criar experiências de realidade misturada, em pé, em escala de sala e em escala mundial.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciais, somente orientação, escala em posição, escala de posto, escala de sala, escala mundial, 360 graus, encaixado, posicionado, sala, mundo, escala, posição, orientação, fixo, anexado, estágio, âncora, âncora espacial, World-Locked, bloqueio mundial, corpo-bloqueado, bloqueio de corpo, limites, persistência, compartilhamento, perda de rastreamento, âncora espacial da nuvem
ms.openlocfilehash: 228f46f1962c39012571234da47ccec07aa67118
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375633"
---
# <a name="coordinate-systems"></a>Sistemas de coordenadas

Em seu núcleo, os aplicativos de realidade misturada colocam os [hologramas](hologram.md) em seu mundo que parecem e são semelhantes a objetos reais. Isso envolve o posicionamento preciso e a orientação desses hologramas em lugares do mundo que são significativos para o usuário, seja o mundo de sua sala física ou um realm que você criou. Ao se deparar com a posição e a orientação de seus hologramas, ou qualquer outra geometria como as [posições](hands-and-tools.md) [olhar](gaze-and-commit.md) Ray ou Hand, o Windows fornece vários sistemas de coordenadas do mundo real em que a geometria pode ser expressa, conhecida como **sistemas de coordenadas espaciais**.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/TneGSeqVAXQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
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
        <td><a href="coordinate-systems.md#stage-frame-of-reference">Quadro de referência de estágio</a></td>
        <td>Ainda sem suporte</td>
        <td>Ainda sem suporte</td>
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
    <tr>
        <td><a href="scene-understanding.md">Reconhecimento de cena</a></td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="mixed-reality-experience-scales"></a>Escalas de experiência de realidade misturada

Os aplicativos de realidade misturada podem projetar para uma ampla gama de experiências de usuário, desde visualizadores de vídeo de 360 graus que precisam apenas da orientação do headset, até aplicativos e jogos completos de escala mundial, que precisam de mapeamento espacial e âncoras espaciais:
<br>

| Escala de experiência | {1&gt;{2&gt;Requisitos&lt;2}&lt;1} | Experiência de exemplo | 
|----------|----------|----------|
|  **Somente orientação** |  **Orientação do headset** (alinhada a gravidade) |  Visualizador de vídeo 360 ° | 
|  **Escala colocada** |  Acima, além da **posição do headset** em relação à posição zero |  Jogo de corrida ou simulador de espaço | 
|  **Escala em posição** |  Acima, mais a **origem do estágio de andar** |  Jogo de ação onde você Patou e subexposição em vigor  | 
|  **Espaço em escala** |  Acima, mais o **polígono dos limites do estágio** |  Jogo de quebra-cabeça onde você se movimenta pelo quebra-cabeça | 
|  **Escala mundial** |  **Âncoras espaciais** (e normalmente o [mapeamento espacial](spatial-mapping.md)) |  Jogo com inimigos provenientes de suas paredes reais, como [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

Esses dimensionamentos de experiência seguem um modelo de "aninhamento de bobblehead". O principal princípio de design aqui para a realidade mista do Windows é que um determinado Headset dá suporte a aplicativos criados para uma escala de experiência de destino, bem como a todas as escalas menores:
<br>

| acompanhamento de 6DOF | Definido pelo piso | acompanhamento de 360 ° | Limites definidos | Âncoras espaciais | Experiência máxima | 
|----------|----------|----------|----------|----------|----------|
|  Não |  - |  - |  - |  - |  **Somente orientação** | 
|  **Sim** |  Não |  - |  - |  - |  **Sentados** | 
|  **Sim** |  **Sim** |  Não |  - |  - |  **Avançar** | 
|  **Sim** |  **Sim** |  **Sim** |  Não |  - |  **Pé-360 °** | 
|  **Sim** |  **Sim** |  **Sim** |  **Sim** |  Não |  **Espaço** | 
|  **Sim** |  **Sim** |  **Sim** |  **Sim** |  **Sim** |  **Países** | 

Observe que o conjunto de teste de referência ainda não tem suporte no HoloLens. Um aplicativo de escala de sala no HoloLens atualmente precisa usar o [mapeamento espacial](spatial-mapping.md) ou a [compreensão da cena](scene-understanding.md) para localizar o piso e as paredes do usuário.

## <a name="spatial-coordinate-systems"></a>Sistemas de coordenadas espaciais

Todos os aplicativos gráficos 3D usam [sistemas de coordenadas cartesianas](https://docs.microsoft.com/windows/uwp/graphics-concepts/coordinate-systems) para ponderar sobre as posições e orientações dos objetos nos mundos virtuais que eles renderizam. Tais sistemas de coordenadas estabelecem 3 eixos perpendiculares ao longo do qual posicionar objetos: um eixo X, Y e Z.

Em [realidade misturada](mixed-reality.md), seus aplicativos serão um motivo para os sistemas de coordenadas física e virtual. O Windows chama um sistema de coordenadas que tem significado real no mundo físico um **sistema de coordenadas espaciais**.

Os sistemas de coordenadas espaciais expressam seus valores de coordenadas em metros. Isso significa que os objetos colocados 2 unidades separadas no eixo X, Y ou Z aparecerão 2 metros uns dos outros quando renderizados em realidade misturada. Isso permite que você processe objetos e ambientes com facilidade em escala do mundo real.

Em geral, os sistemas de coordenadas cartesianas podem ser destros ou destros. Os sistemas de coordenadas espaciais no Windows são sempre destros, o que significa que os pontos positivos do eixo X estão certos, o eixo Y positivo aponta para cima (alinhado à gravidade) e os pontos positivos do eixo Z em direção a você.

Em ambos os tipos de sistemas de coordenadas, o eixo X positivo aponta para a direita e o eixo Y positivo aponta para cima. A diferença é se os pontos positivos do eixo Z estão em direção ou afastadas de você. Você pode lembrar qual direção os pontos positivos do eixo Z apontando os dedos de sua mão esquerda ou direita na direção X positiva e enrolando-os para a direção Y positiva. A direção em que seu thumb aponta, para ou longe de você, é a direção que os pontos positivos do eixo Z para esse sistema de coordenadas.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Criando uma experiência somente de orientação ou de escala assentada

A chave para a [renderização](rendering.md) de Holographic é alterar a exibição do aplicativo de seus hologramas cada quadro à medida que o usuário se movimenta, para corresponder ao seu movimento de cabeça previsto. Você pode criar **experiências em escala** em conjunto que respeitam as alterações na posição de cabeçalho e na orientação da cabeça do usuário usando um **quadro estacionário de referência**.

Alguns conteúdos devem ignorar as atualizações de posição de cabeçalho, permanecendo fixo em um título e distância escolhidos do usuário em todos os momentos. O exemplo principal é o vídeo de 360 graus: como o vídeo é capturado de uma perspectiva fixa única, ele arruinaria a ilusão da posição da exibição para se mover em relação ao conteúdo, mesmo que a orientação da exibição deva mudar conforme o usuário for examinado. Você pode criar essas **experiências somente de orientação** usando um **quadro de referência anexado**.

### <a name="stationary-frame-of-reference"></a>Quadro estacionário de referência

O sistema de coordenadas fornecido por um quadro estacionário de referência funciona para manter as posições de objetos perto do usuário o mais estável possível em relação ao mundo, ao mesmo tempo em que respeitam as alterações na posição de cabeçalho do usuário.

Para experiências em escala em estado em um mecanismo de jogo, como o [Unity](https://unity3d.com/), um quadro estacionário de referência é o que define a "origem mundial" do mecanismo. Os objetos que são colocados em uma coordenada específica do mundo usam o quadro estacionário de referência para definir sua posição no mundo real usando as mesmas coordenadas. O conteúdo que permanece no mundo, mesmo quando o usuário percorra, é conhecido como conteúdo **bloqueado pelo mundo** .

Normalmente, um aplicativo criará um quadro estacionário de referência na inicialização e usará seu sistema de coordenadas durante o tempo de vida do aplicativo. Como desenvolvedor de aplicativos no Unity, você pode simplesmente começar a colocar o conteúdo em relação à origem, que estará na posição e orientação da cabeça inicial do usuário. Se o usuário se mover para um novo local e quiser continuar sua experiência em escala, você poderá recentralizar a origem mundial nesse local.

Ao longo do tempo, à medida que o sistema aprende mais sobre o ambiente do usuário, ele pode determinar que as distâncias entre vários pontos do mundo real sejam mais curtas ou maiores do que o sistema acreditar anteriormente. Se você renderizar hologramas em um quadro estacionário de referência para um aplicativo no HoloLens onde os usuários perfrentem além de uma área cerca de 5 metros de largura, seu aplicativo pode observar descompasso no local observado desses hologramas. Se sua experiência tiver usuários indo além de 5 metros, você estará criando uma [experiência de escala mundial](#building-a-world-scale-experience), o que exigirá técnicas adicionais para manter os hologramas estáveis, conforme descrito abaixo.

### <a name="attached-frame-of-reference"></a>Quadro de referência anexado

Um quadro de referência anexado é movido com o usuário conforme ele percorre, com um título fixo definido quando o aplicativo cria o quadro pela primeira vez. Isso permite que o usuário examine confortavelmente o conteúdo colocado dentro desse quadro de referência. O conteúdo renderizado nesse modo relativo ao usuário é chamado de conteúdo **bloqueado pelo corpo** .

Quando o headset não consegue descobrir onde ele está no mundo, um quadro de referência anexado fornece o único sistema de coordenadas que pode ser usado para renderizar hologramas. Isso o torna ideal para exibir a interface de usuário de fallback para informar ao usuário que seu dispositivo não consegue encontrá-los no mundo. Os aplicativos que são recolocados em escala ou superior devem incluir um fallback somente de orientação para ajudar o usuário a entrar novamente, com a interface do usuário semelhante à mostrada na [página inicial mistura de realidade](navigating-the-windows-mixed-reality-home.md).

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Criando uma experiência em escala ou em escala de sala

Para ir além da escala em um headset de imersão e criar uma **experiência de escala em posição**, você pode usar o **quadro de referência de estágio**.

Para fornecer uma **experiência em escala de sala**, permitindo que os usuários percorram o limite de 5 medidores predefinidos, você também pode verificar **limites de estágio** .

### <a name="stage-frame-of-reference"></a>Quadro de referência de estágio

Ao configurar pela primeira vez um headset de imersão, o usuário define um **estágio**, que representa a sala em que haverá realidade misturada. O estágio define minimamente uma **origem de estágio**, um sistema de coordenadas espaciais centralizado na posição de piso escolhida do usuário e orientação de encaminhamento onde pretendem usar o dispositivo. Ao colocar o conteúdo neste estágio sistema de coordenadas no plano Y = 0, você pode garantir que os hologramas pareçam confortavelmente no chão quando o usuário estiver em pé, fornecendo aos usuários uma **experiência de escala em pé**.

### <a name="stage-bounds"></a>Limites de estágio

O usuário também pode definir, opcionalmente, **limites de estágio**, uma área dentro da sala que foi limpa de mobília, onde pretendem se mover em realidade misturada. Nesse caso, o aplicativo pode criar uma **experiência de escala de sala**, usando esses limites para garantir que os hologramas sempre sejam colocados onde o usuário possa contatá-los.

Como o quadro de referência de estágio fornece um único sistema de coordenadas fixos no qual posicionar o conteúdo relativo, é o caminho mais fácil para portar aplicativos de escala em estado e de colocação em pé desenvolvidos para a realidade virtual headsets. No entanto, assim como acontece com essas plataformas de VR, um único sistema de coordenadas só pode estabilizar conteúdo em cerca de um diâmetro de 5 metros (16 pés), antes que os efeitos de braço de alavanca façam com que o conteúdo longe do centro mude notavelmente à medida que o sistema se ajusta. Para ir além de 5 metros, são necessárias âncoras espaciais.

## <a name="building-a-world-scale-experience"></a>Criando uma experiência de escala mundial

O HoloLens permite **experiências reais em grande escala** que permitem que os usuários perfrentem mais de 5 metros. Para criar um aplicativo de escala mundial, você precisará de novas técnicas além das usadas para experiências em escala de sala.

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>Por que um único sistema de coordenadas rígidos não pode ser usado além de 5 metros

Hoje em dia, ao escrever jogos, aplicativos de visualização de dados ou aplicativos de realidade virtual, a abordagem típica é estabelecer um sistema de coordenadas do mundo absoluto que todas as outras coordenadas possam Mapear de forma confiável de volta para o. Nesse ambiente, você sempre pode encontrar uma transformação estável que define uma relação entre quaisquer dois objetos nesse mundo. Se você não moveu esses objetos, suas transformações relativas sempre permanecerão as mesmas. Esse tipo de sistema de coordenadas global funciona bem ao renderizar um mundo puramente virtual em que você conhece toda a geometria com antecedência. Atualmente, os aplicativos VR em escala de sala normalmente estabelecem esse tipo de sistema de coordenadas de escala de sala absoluto com sua origem no chão.

Por outro lado, um dispositivo de realidade misturada sem compartilhamento de porta, como o HoloLens, tem uma compreensão dinâmica orientada por sensor do mundo, ajustando continuamente seu conhecimento ao longo do tempo do ambiente do usuário à medida que eles orientam muitos medidores em todo um andar de um edifício. Em uma experiência de escala mundial, se você colocou todos os seus hologramas em um único sistema de coordenadas rígidos, esses hologramas seriam necessariamente desfeitos com o passar do tempo, seja em relação ao mundo ou entre si.

Por exemplo, o headset pode acreditar, no momento, que dois locais do mundo tenham 4 metros de distância e depois refinam essa compreensão, aprendendo que os locais estão na verdade 3,9 metros de distância. Se esses hologramas tiverem sido inicialmente colocados quatro metros de distância em um único sistema de coordenadas rígidos, um deles sempre pareceria de 0,1 metros do mundo real.

### <a name="spatial-anchors"></a>Âncoras espaciais

A realidade mista do Windows resolve o problema descrito na seção anterior, permitindo que você crie [âncoras espaciais](spatial-anchors.md) para marcar pontos importantes no mundo em que o usuário colocou os hologramas. Uma âncora espacial representa um ponto importante no mundo que o sistema deve acompanhar ao longo do tempo.

Como o dispositivo aprende sobre o mundo, essas âncoras espaciais podem ajustar sua posição em relação umas às outras, conforme necessário, para garantir que cada âncora permaneça precisamente onde foi colocado em relação ao mundo real. Ao colocar uma âncora espacial no local em que o usuário coloca um holograma e, em seguida, posicionar esse holograma em relação à sua âncora espacial, você pode garantir que o holograma mantenha a estabilidade ideal, mesmo que o usuário se movimente entre dezenas de medidores.

Esse ajuste contínuo de âncoras espaciais em relação umas com as outras é a principal diferença entre sistemas de coordenadas de âncoras espaciais e quadros de referência estáticos:

* Os hologramas colocados no quadro estacionário de referência todos retêm uma relação rígida entre si. No entanto, à medida que o usuário passa por longas distâncias, o sistema de coordenadas desse quadro pode descompassor em relação ao mundo para garantir que os hologramas ao lado do usuário pareçam estáveis.

* Os hologramas colocados no quadro do estágio de referência também retêm uma relação rígida entre si. Ao contrário do quadro estacionário, o quadro de estágio sempre permanece fixo em vigor em relação à sua origem física definida. No entanto, o conteúdo renderizado no sistema de coordenadas do estágio além de seu limite de 5 metros só aparecerá estável quando o usuário estiver dentro desse limite.

* Os hologramas colocados usando uma âncora espacial podem descompassor em relação aos hologramas colocados usando outra âncora espacial. Isso permite que o Windows aprimore sua compreensão da posição de cada âncora espacial, mesmo que, por exemplo, uma âncora precise se ajustar à esquerda e outra âncora precise se ajustar à direita.

Ao contrário de um quadro estacionário de referência, que sempre otimiza a estabilidade próxima ao usuário, o quadro de referência e as âncoras espaciais garantem a estabilidade perto de suas origens. Isso ajuda esses hologramas a permanecerem precisamente com o passar do tempo, mas também significa que os hologramas renderizados muito longe da origem do seu sistema de coordenadas sofrerão efeitos cada vez mais graves na alavanca. Isso ocorre porque pequenos ajustes na posição e na orientação do estágio ou da âncora são ampliados proporcionalmente à distância dessa âncora. 

Uma boa regra geral é garantir que tudo que você renderiza com base em um sistema de coordenadas da âncora espacial distante esteja em cerca de 3 metros de sua origem. Para uma origem de estágio próximo, a renderização de conteúdo distante está OK, pois qualquer maior erro posicional afetará apenas os pequenos hologramas que não mudarão muito na exibição do usuário.

### <a name="spatial-anchor-persistence"></a>Persistência de ancoragem espacial

As âncoras espaciais também podem permitir que seu aplicativo se lembre de um local importante mesmo depois que o aplicativo é suspenso ou o dispositivo é desligado.

Você pode salvar em disco as âncoras espaciais que seu aplicativo cria e, em seguida, carregá-las novamente mais tarde, persistindo-as para o **repositório de âncora espacial**do seu aplicativo. Ao salvar ou carregar uma âncora, você fornece uma chave de cadeia de caracteres que é significativa para seu aplicativo, a fim de identificar a âncora mais tarde. Considere essa chave como o nome de arquivo para sua âncora. Se você quiser associar outros dados a essa âncora, como um modelo 3D que o usuário colocou nesse local, salve-o no armazenamento local do seu aplicativo e associe-o à chave escolhida.

Ao persistir âncoras para a loja, os usuários podem posicionar hologramas individuais ou posicionar um espaço de trabalho em volta do qual um aplicativo coloca seus diversos hologramas e, em seguida, encontrar esses hologramas posteriormente, onde eles esperam, em muitos usos de seu aplicativo.

Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a> para persistência assíncrona de holograma em dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial em nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que os dispositivos não estejam presentes ao mesmo tempo.

### <a name="spatial-anchor-sharing"></a>Compartilhamento de âncora espacial

Seu aplicativo também pode compartilhar uma âncora espacial em tempo real com outros dispositivos, permitindo experiências compartilhadas em tempo real.

Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a>, seu aplicativo pode compartilhar uma âncora espacial entre vários dispositivos de HoloLens, Ios e Android. Ao fazer cada dispositivo renderizar um holograma usando a mesma âncora espacial, todos os usuários verão o holograma aparecer no mesmo lugar no mundo real.

## <a name="avoid-head-locked-content"></a>Evitar conteúdo bloqueado por cabeçalho

Não é altamente recomendável renderizar conteúdo de cabeça bloqueada, que permanece em um local fixo na exibição (como um HUD). Em geral, o conteúdo bloqueado por cabeça é desconfortável para os usuários e não parece uma parte natural do seu mundo.

O conteúdo bloqueado no cabeçalho deve ser normalmente substituído por hologramas anexados ao usuário ou colocados no próprio mundo. Por exemplo, os [cursores](cursors.md) devem, em geral, ser enviados para o mundo, dimensionando naturalmente para refletir a posição e a distância do objeto sob o olhar do usuário.

## <a name="handling-tracking-errors"></a>Manipulação de erros de controle

Em alguns ambientes, como corredores escuros, talvez não seja possível que um headset Use controle interno para se localizar corretamente no mundo. Isso pode levar os hologramas a não aparecer ou aparecerem em locais incorretos se forem manipulados incorretamente. Agora, discutiremos as condições em que isso pode acontecer, seu impacto na experiência do usuário e dicas para lidar melhor com essa situação.

### <a name="headset-cannot-track-due-to-insufficient-sensor-data"></a>O headset não pode ser acompanhado devido a dados insuficientes do sensor

Às vezes, os sensores do headset não conseguem descobrir onde está o headset. Isso pode acontecer se a sala for escura ou se os sensores estiverem cobertos por cabelo ou mãos ou se os arredores não tiverem textura suficiente.

Quando isso acontecer, o headset não poderá controlar sua posição com precisão suficiente para renderizar hologramas bloqueados ao mundo. Você não conseguirá descobrir onde uma âncora espacial, um quadro estacionário ou um quadro de estágio é relativo ao dispositivo, mas ainda poderá renderizar conteúdo bloqueado no corpo do quadro de referência anexado.

Seu aplicativo deve informar ao usuário como obter o controle posicional de volta, Renderizando algum conteúdo bloqueado com corpo de fallback que descreve algumas dicas, como a descoberta de sensores e a ativação de mais luzes.

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>Fone de ouvido acompanha incorretamente devido a alterações dinâmicas no ambiente

Às vezes, o dispositivo não poderá rastrear corretamente se houver muitas alterações dinâmicas no ambiente, como muitas pessoas percorrendo na sala. Nesse caso, os hologramas podem parecer para o salto ou descompasso, pois o dispositivo tenta acompanhar-se nesse ambiente dinâmico. É recomendável usar o dispositivo em um ambiente menos dinâmico se você atingir esse cenário.

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>O fone de ouvido acompanha incorretamente porque o ambiente mudou significativamente ao longo do tempo

Às vezes, quando você começa a usar um headset em um ambiente que passou por muitas alterações (por exemplo, movimento significativo de mobília, travamentos de parede etc.), é possível que alguns hologramas possam parecer deslocados de seus locais originais. Os hologramas anteriores também podem saltar à medida que o usuário se movimentar nesse novo espaço. Isso ocorre porque a compreensão do sistema do seu espaço não é mais segura e tenta remapear o ambiente ao tentar reconciliar os recursos da sala. Nesse cenário, é aconselhável encorajar os usuários a reposicionar os hologramas que eles fixaram no mundo se não estiverem aparecendo onde esperado.

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>Fone de ouvido acompanha incorretamente devido a espaços idênticos em um ambiente

Às vezes, uma casa ou outro espaço pode ter duas áreas idênticas. Por exemplo, duas salas de conferência idênticas, duas áreas de canto idênticas, dois grandes pôsteres idênticos que abrangem o campo de exibição do dispositivo. Nesses cenários, o dispositivo pode, às vezes, ficar confuso entre as partes idênticas e marcá-las como a mesma em sua representação interna. Isso pode fazer com que os hologramas de algumas áreas apareçam em outros locais. O dispositivo pode começar a perder o controle com frequência, pois sua representação interna do ambiente foi corrompida. Nesse caso, é aconselhável redefinir a compreensão ambiental do sistema. Observe que a redefinição do mapa leva à perda de todos os posicionamentos de âncora espaciais. Isso fará com que o fone de ouvido acompanhe bem nas áreas exclusivas do ambiente. No entanto, o problema pode ocorrer novamente se o dispositivo ficar confuso entre as áreas idênticas novamente.

## <a name="see-also"></a>Consulte também
* [Apresentação do GDC 2017 em sistemas de coordenadas espaciais e renderização Holographic](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Sistemas de coordenadas no Unity](coordinate-systems-in-unity.md)
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md)
* [Âncoras espaciais](spatial-anchors.md)
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* [Estudo de caso - Como olhar através dos buracos na sua realidade](case-study-looking-through-holes-in-your-reality.md)

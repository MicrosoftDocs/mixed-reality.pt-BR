---
title: Experiências compartilhadas em realidade misturada
description: Os aplicativos Holographic podem compartilhar âncoras espaciais de um HoloLens para outro, permitindo que os usuários processem um holograma no mesmo local do mundo real, em vários dispositivos.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: experiência compartilhada, realidade misturada, holograma, âncora espacial, vários usuários, vários
ms.openlocfilehash: 4e71bdefa32d2f6cf3b85b074c3d9fcbdb6aa909
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437464"
---
# <a name="shared-experiences-in-mixed-reality"></a>Experiências compartilhadas em realidade misturada

Os hologramas não precisam permanecer privados a apenas um usuário. Os aplicativos Holographic podem compartilhar [âncoras espaciais](spatial-anchors.md) de um dispositivo HoloLens, Ios ou Android para outro, permitindo que os usuários processem um holograma no mesmo local do mundo real em vários dispositivos.

## <a name="six-questions-to-define-shared-scenarios"></a>Seis perguntas para definir cenários compartilhados

Antes de começar a projetar para experiências compartilhadas, é importante definir os cenários de destino. Esses cenários ajudam a esclarecer o que você está criando e estabelecem um vocabulário comum para ajudar a comparar e contrastar os recursos necessários em sua experiência. Compreender o problema principal, e os diferentes caminhos para soluções, é a chave para descobrir oportunidades inerentes a esse novo meio.

Por meio de protótipos internos e explorações de nossos órgãos de parceiros de HoloLens, criamos seis perguntas para ajudá-lo a definir cenários compartilhados. Essas perguntas formam uma estrutura, não deve ser exaustiva, para ajudar a filtrar os atributos importantes dos seus cenários.

### <a name="1-how-are-they-sharing"></a>1. como eles estão compartilhando?

Uma apresentação pode ser conduzida por um único usuário virtual, enquanto vários usuários podem colaborar ou um professor pode fornecer orientação para estudantes virtuais trabalhando com materiais virtuais – a complexidade das experiências aumenta com base no nível de agência que um usuário tem ou pode ter em um cenário.

![Homem e mulheres com holograph na tabela](images/man-and-women-with-holograph-on-table-500px.png)

Há várias maneiras de compartilhar, mas descobrimos que a maioria deles se enquadra em três categorias:

* **Apresentação**: quando o mesmo conteúdo está sendo mostrado para vários usuários. Por exemplo: um professor está dando uma palestra para vários alunos usando o mesmo material de Holographic que está sendo apresentado a todos. O professor, no entanto, pode ter suas próprias dicas e anotações que podem não estar visíveis para outras pessoas.
* **Colaboração**: quando as pessoas trabalham em conjunto para alcançar algumas metas comuns. Por exemplo: o professor deu um projeto para aprender sobre a execução de um coração cirurgia. Os alunos emparelham e criam uma experiência de laboratório de habilidades compartilhadas que permite que os alunos médicos colaborem no modelo de coração e aprendam.
* **Diretrizes**: quando uma pessoa está ajudando alguém a resolver um problema em uma interação de estilo um-para-um. Por exemplo: o professor que oferece orientação a um aluno quando ele está realizando o laboratório de conhecimentos de cirurgia de coração na experiência compartilhada.

### <a name="2-what-is-the-group-size"></a>2. qual é o tamanho do grupo?

As experiências de compartilhamento de **um para um** podem fornecer uma linha de base forte e, teoricamente, suas provas de conceito podem ser criadas nesse nível. Mas esteja ciente de que o compartilhamento com grupos grandes (além de 6 pessoas) pode levar a problemas técnicos (dados e redes) e sociais (o impacto de estar em uma sala com [vários avatars](https://vimeo.com/160704056)). A complexidade aumenta exponencialmente à medida que você vai de **pequenos** a **grandes grupos**.

Descobrimos que as necessidades dos grupos podem se enquadrar em três categorias de tamanho:
* 1:1
* Pequeno < 7
* > Grande = 7

O tamanho do grupo faz uma pergunta importante porque ele influencia:

* Representações de pessoas no espaço de Holographic
* Escala de objetos
* Escala de ambiente

### <a name="3-where-is-everyone"></a>3. onde está todos?

A força da realidade misturada entra em cena quando uma experiência compartilhada pode ocorrer no mesmo local. Chamamos isso de **colocalizado**. Por outro lado, quando o grupo é distribuído e pelo menos um participante não está no mesmo espaço físico (como geralmente é o caso com VR), chamamos isso de uma **experiência remota**. Geralmente, é o caso de seu **grupo ter participantes** colocalizados e remotos (por exemplo, dois grupos em salas de conferência).

![Três pessoas com holograph na tabela](images/three-people-with-holograph-on-table-500px.png)

As categorias a seguir ajudam a transmitir onde os usuários estão localizados:

* **Colocalizado**: todos os usuários estarão no mesmo espaço físico.
* **Remoto**: todos os usuários estarão em espaços físicos separados.
* **Ambos**: os usuários serão uma combinação de espaços colocalizados e remotos.

Essa pergunta é crucial porque influencia:

* Como as pessoas se comunicam?
    * Por exemplo: se eles devem ter avatars?
* Quais objetos eles veem. Todos os objetos são compartilhados?
* Se precisamos adaptar-se ao seu ambiente?

### <a name="4-when-are-they-sharing"></a>4. quando eles estão compartilhando?

Normalmente, pensamos em experiências **síncronas** quando as experiências compartilhadas vêm à mente: estamos tudo isso juntos. Mas se incluírmos um único elemento virtual que foi adicionado por outra pessoa, temos um cenário **assíncrono** . Imagine uma nota, ou memorando de voz, deixado em um ambiente virtual. Como você lida com os memorandos virtuais 100 no seu design? E se eles forem de dezenas de pessoas com diferentes níveis de privacidade?

Considere suas experiências como uma destas categorias de tempo:

* De forma **síncrona**: compartilhar a experiência do Holographic ao mesmo tempo. Por exemplo: dois alunos que executam o laboratório de habilidades ao mesmo tempo.
* De **forma assíncrona**: compartilhar a experiência do Holographic em momentos diferentes. Por exemplo: dois alunos executando o laboratório de habilidades, mas trabalhando em seções separadas em momentos diferentes.
* **Ambos**: os usuários às vezes serão compartilhados de forma síncrona, mas outras vezes assincronamente. Por exemplo: um professor que reduz a atribuição realizada pelos alunos em um momento posterior e deixa anotações para os alunos no próximo dia.

Essa pergunta é importante porque influencia:

* Persistência de objeto e ambiente. Por exemplo: armazenar os Estados para que eles possam ser recuperados.
* Perspectiva do usuário. Por exemplo: talvez lembrar o que o usuário estava olhando ao deixar anotações.

### <a name="5-how-similar-are-their-physical-environments"></a>5. quão semelhantes são seus ambientes físicos?

A probabilidade de dois ambientes reais idênticos, fora de experiências colocalizadas, é Slim, a menos que esses ambientes tenham sido projetados para serem idênticos. É mais provável que você tenha ambientes **semelhantes** . Por exemplo, as salas de conferência são semelhantes — elas normalmente têm uma tabela localizada centralmente envolvida por cadeiras. As salas de vida, por outro lado, geralmente são **diferentes** e podem incluir qualquer número de peças de mobília em uma matriz infinita de layouts.

![Holograph na tabela](images/holograph-on-table-500px.png)

Considere suas experiências de compartilhamento se ajustando a uma destas duas categorias:

* **Semelhante**: ambientes que tendem a ter móveis semelhantes, luz ambiente e som, tamanho da sala física. Por exemplo: professor está no Hall da palestra A e os alunos estão na sala de palestras B. A Hall da palestra A pode ter menos cadeiras que B, mas ambas podem ter uma escrivaninha física para posicionar os hologramas.
* **Disimilar**: ambientes que são bastante diferentes nas configurações de mobília, tamanhos de sala, considerações de luz e som. Por exemplo: um professor está em uma sala de foco, enquanto os alunos estão em uma grande sala de palestras, preenchida com alunos e professores.

É importante [pensar no ambiente](environment-considerations-for-hololens.md), pois ele influenciará:

* Como as pessoas experimentarão esses objetos. Por exemplo: se sua experiência funcionar melhor em uma tabela e o usuário não tiver uma tabela? Ou em uma superfície de piso plana, mas o usuário tem um espaço desorganizado.
* Escala dos objetos. Por exemplo: colocar um modelo humano de 6 pés em uma tabela poderia ser desafiador, mas um modelo de coração funcionaria muito bem.

### <a name="6-what-devices-are-they-using"></a>6. quais dispositivos estão usando?

Hoje, geralmente é provável que você veja experiências compartilhadas entre dois [**dispositivos de imersão**](immersive-headset-hardware-details.md) (esses dispositivos podem diferir ligeiramente em termos de botões e recursos relativos, mas não muito) ou dois **dispositivos holographics** dadas as soluções que estão sendo direcionadas nesses dispositivos. Mas considere se os **dispositivos 2D** (um participante móvel/de área de trabalho ou observador) serão uma consideração necessária, especialmente em situações de **dispositivos 2D e 3D mistos**. Compreender os tipos de dispositivos que seus participantes usarão é importante, não só porque eles vêm com diferentes limitações de fidelidade e de dados e oportunidades, mas porque os usuários têm expectativas exclusivas para cada plataforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Explorando o potencial de experiências compartilhadas

As respostas às perguntas acima podem ser combinadas para entender melhor seu cenário compartilhado, crystallizingndo os desafios à medida que você expandir a experiência. Para a equipe da Microsoft, isso ajudou a estabelecer um mapa de estrada para melhorar as experiências que usamos hoje, compreendendo a nuance desses problemas complexos e como aproveitar as experiências compartilhadas na realidade misturada.

Por exemplo, considere um dos cenários do Skype do lançamento do HoloLens: um usuário trabalhou por meio de [como corrigir uma mudança de luz quebrada](https://www.youtube.com/watch?v=iBfzs3G8BEA) com a ajuda de um especialista localizado remotamente.

![Corrigindo uma mudança de luz com assistência por meio do Skype para o HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*Um especialista fornece diretrizes de **1:1** de seu computador desktop **2D**para um usuário de um dispositivo **3D, de realidade mista** . A **diretriz** é **síncrona** e os ambientes físicos são **diferentes**.*

Uma experiência como esta é uma mudança na nossa experiência atual, aplicando o paradigma de vídeo e voz a um novo meio. Mas à medida que olhamos para o futuro, devemos definir melhor a oportunidade de nossos cenários e criar experiências que reflitam a força da realidade misturada.

Considere a [ferramenta de colaboração onsight](https://www.youtube.com/watch?v=XtUyUJAVQ6w), desenvolvida pelo laboratório Jet propulsão da NASA. Os cientistas que trabalham com dados das missões de Rover do Mars podem colaborar com colegas em tempo real dentro dos dados do Martian Landscape.

![Colaboração entre colegas separados remotamente para planejar o trabalho para o Rover Mars](images/onsight-nasa-jpl.gif)

*Um cientista explora um ambiente usando um dispositivo **3D, de realidade misturada,** com um **pequeno** grupo de colegas **remotos** usando dispositivos **3D e 2D** . A **colaboração** é **síncrona** (mas pode ser revisitada de forma assíncrona) e os ambientes físicos são (virtualmente) **semelhantes**.*

Experiências como o onsight apresentam novas oportunidades para colaborar. De apontar elementos fisicamente no ambiente virtual para posicionar ao lado de um colega e compartilhar sua perspectiva à medida que eles explicam suas descobertas. O onsight usa a lente de imersão e a presença para reconsiderar as experiências de compartilhamento em realidade misturada.

A colaboração intuitiva é a Fundação da conversa, trabalhando em conjunto e entender como podemos aplicar essa intuição à complexidade da realidade misturada é crucial. Se não pudermos recriar experiências de compartilhamento apenas em realidade misturada, mas Potencialize-las, será uma mudança de paradigma para o futuro do trabalho. A criação de experiências compartilhadas na realidade misturada é um espaço novo e empolgante, e estamos apenas no começo.

## <a name="get-started-building-shared-experiences"></a>Introdução à criação de experiências compartilhadas

Dependendo do seu aplicativo e cenário, haverá vários requisitos para atingir a experiência desejada. Alguns deles incluem:

* **Tomada de correspondência**: capacidade de criar sessões, anunciar sessões, descobrir e convidar pessoas específicas, tanto localmente quanto remotamente para ingressar na sua sessão.
* **Compartilhamento de âncora**: capacidade de alinhar coordenadas em vários dispositivos em um espaço local comum, portanto, os hologramas aparecem no mesmo local para todas as pessoas.
* **Rede**: capacidade de ter posições, interações e movimentos de pessoas e hologramas sincronizados em tempo real em todos os participantes.
* **Armazenamento de estado**: capacidade de armazenar características e locais de holograma em espaço para ingresso de sessão intermediária, recall em um momento posterior e robustez contra problemas de rede.

A chave para experiências compartilhadas é ter vários usuários vendo os mesmos hologramas no mundo em seu próprio dispositivo, frequentemente feito com o compartilhamento de âncoras para alinhar as coordenadas entre os dispositivos.

Para compartilhar âncoras, use as [âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors):

* Primeiro, o usuário coloca o holograma.
* O aplicativo cria uma [âncora espacial](spatial-anchors.md), para fixar esse holograma precisamente no mundo.
* As âncoras podem ser compartilhadas para dispositivos de HoloLens, iOS e Android por meio de [âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/).

Com uma âncora espacial compartilhada, o aplicativo em cada dispositivo agora tem um [sistema de coordenadas comum](coordinate-systems.md) no qual eles podem inserir conteúdo. Agora o aplicativo pode garantir a posição e a orientação do holograma no mesmo local.

Em dispositivos HoloLens, você também pode compartilhar âncoras offline de um dispositivo para outro.  Use os links abaixo para decidir o que é melhor para seu aplicativo.

## <a name="evaluating-tech-options"></a>Avaliando opções de tecnologia

Há várias opções de serviço e tecnologia disponíveis para ajudar a criar experiências de realidade mista de vários usuários.  Pode ser difícil escolher um caminho, portanto, tomando uma perspectiva com foco no cenário, algumas opções são detalhadas abaixo.

## <a name="shared-static-holograms-no-interactions"></a>Hologramas estáticos compartilhados (sem interações)

Aproveite as [âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/) em seu aplicativo.  A habilitação e o compartilhamento de âncoras espaciais entre dispositivos permite que você crie um aplicativo onde os usuários vejam os hologramas no mesmo local ao mesmo tempo.  A sincronização adicional entre dispositivos é necessária para permitir que os usuários interajam com hologramas e veja movimentos ou atualizações de estado de hologramas.

## <a name="share-1st-person-perspective"></a>Compartilhar perspectiva da 1ª pessoa

Aproveite o suporte ao Miracast interno, para usuários locais quando você tem um receptor de Miracast com suporte, como um PC ou TV, nenhum código de aplicativo adicional é necessário.

Aproveite o [MixedReality-WebRTC](https://github.com/microsoft/mixedreality-webrtc) em seu aplicativo, para usuários remotos ou quando você tiver dispositivos não Miracast que gostaria de compartilhar.  A habilitação de uma conexão WebRTC permite fluxos de áudio/vídeo 1:1 entre usuários, com um canal de dados para mensagens entre dispositivos também.  A implementação da realidade misturada otimiza para o HoloLens, fornecendo um fluxo de vídeo de captura de realidade misturada da exibição do usuário do HoloLens para outras pessoas.  Se você quiser escalar verticalmente o streaming de vídeo para vários clientes remotos, um [provedor de serviços de MCU](https://webrtcglossary.com/mcu/) (unidade de conferência do MultiPoint) normalmente será usado, como [SignalWire](https://signalwire.com/).  Uma implantação de SignalWire de um clique no Azure está disponível por meio do [FreeSwitch](https://github.com/andywolk/azure-freeswitch-gpu-windows).

> [!NOTE]
> Observe que o SignalWire é um serviço pago e não é de propriedade/afiliado à Microsoft.

## <a name="presenter-spectator-applications-and-demos"></a>Apresentador – demonstrações e aplicativos Spectator

Aproveite o [MixedReality-SpectatorView](https://github.com/microsoft/MixedReality-SpectatorView) para trazer a [funcionalidade do specator View](spectator-view.md) para seu aplicativo.  Habilite outros dispositivos (HL, Android, iOS e câmeras de vídeo) para ver o que o HoloLens vê de uma perspectiva diferente no mesmo local e receber atualizações de interações do usuário de HoloLens host interagindo com os hologramas.  Assista, tire fotos e grave vídeo sobre o que o host faz com os hologramas no aplicativo de sua própria perspectiva espacial com o Spectator Companion do mesmo aplicativo.

**Observação:** As imagens são obtidas por meio de captura de tela em dispositivos iOS/Android.

## <a name="multi-user-collaborative-experience"></a>Experiência colaborativa de vários usuários

Comece com nosso [tutorial de aprendizado de vários usuários](mrlearning-sharing(photon)-ch1.md), que aproveita as [âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/) para usuários locais e o [SDK do Photon](https://www.photonengine.com/PUN) para sincronizar o conteúdo/estado na cena. Crie aplicativos de colaboração localmente em que cada usuário tem sua própria perspectiva sobre os hologramas na cena e pode interagir totalmente com os hologramas.  As atualizações são fornecidas em todos os dispositivos e o gerenciamento de conflitos de interação é tratado pelo Photon.

> [!NOTE]
> Observe que o [Photon](https://www.photonengine.com/) é um produto que não é da Microsoft, portanto, uma relação de cobrança com Photon pode ser necessária para produto e dimensionamento para maior uso.

## <a name="future-work"></a>Trabalho futuro

As interfaces e os recursos do componente ajudarão a fornecer consistência comum e suporte robusto em vários cenários e tecnologias subjacentes.  Até lá, escolha o melhor caminho que se alinhe ao cenário que você está tentando atingir em seu aplicativo.

Cenário diferente ou desejo de usar um Tech/Service diferente? Forneça comentários como problemas do GitHub no repositório correspondente, na parte inferior desta página ou entre em contato com a [margem de atraso do HoloDevelopers](https://holodevelopers.slack.com/).

## <a name="see-also"></a>Consulte também

* [Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors)
* [Âncoras espaciais compartilhadas no DirectX](shared-spatial-anchors-in-directx.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)
* [Modo de exibição Espectador](spectator-view.md)

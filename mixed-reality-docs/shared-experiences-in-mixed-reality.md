---
title: Experiências compartilhadas em realidade misturada
description: Os aplicativos Holographic podem compartilhar âncoras espaciais de um HoloLens para outro, permitindo que os usuários processem um holograma no mesmo lugar do mundo real em vários dispositivos.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: experiência compartilhada, realidade misturada, holograma, âncora espacial, vários usuários, vários
ms.openlocfilehash: fbc636a5d65e605ae9e9f9655eb15550ff8de7b7
ms.sourcegitcommit: e5b677f92ac4b1dff9aad6c329345a5aca4fcef5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69020203"
---
# <a name="shared-experiences-in-mixed-reality"></a>Experiências compartilhadas em realidade misturada

Os hologramas não precisam permanecer privados a apenas um usuário. Os aplicativos Holographic podem compartilhar [âncoras espaciais](coordinate-systems.md) de um dispositivo HoloLens, Ios ou Android para outro, permitindo que os usuários processem um holograma no mesmo local do mundo real em vários dispositivos.

## <a name="six-questions-to-define-shared-scenarios"></a>Seis perguntas para definir cenários compartilhados

Antes de começar a projetar para experiências compartilhadas, é importante definir os cenários de destino. Esses cenários ajudam a esclarecer o que você está criando e estabelecem um vocabulário comum para ajudar a comparar e contrastar os recursos necessários em sua experiência. Compreender o problema principal, e os diferentes caminhos para soluções, é a chave para descobrir oportunidades inerentes a esse novo meio.

Por meio de protótipos internos e explorações de nossos órgãos de parceiros de HoloLens, criamos seis perguntas para ajudá-lo a definir cenários compartilhados. Essas perguntas formam uma estrutura, não deve ser exaustiva, para ajudar a filtrar os atributos importantes dos seus cenários.

### <a name="1-how-are-they-sharing"></a>1. Como eles estão compartilhando?

Uma apresentação pode ser conduzida por um único usuário virtual, enquanto vários usuários podem colaborar ou um professor pode fornecer orientação para estudantes virtuais trabalhando com materiais virtuais – a complexidade das experiências aumenta com base no nível de agência que um usuário tem ou pode ter em um cenário.

![Homem e mulheres com holograph na tabela](images/man-and-women-with-holograph-on-table-500px.png)

Há várias maneiras de compartilhar, mas descobrimos que a maioria deles se enquadra em três categorias:
* **Apresentação**: Quando o mesmo conteúdo está sendo mostrado para vários usuários. Por exemplo: Um professor está dando uma palestra para vários alunos usando o mesmo material de Holographic que está sendo apresentado a todos. No entanto, o professor poderia ter suas próprias dicas e anotações que podem não estar visíveis para outras pessoas.
* **Colaboração**: Quando as pessoas trabalham em conjunto para alcançar algumas metas comuns. Por exemplo: O professor deu um projeto para aprender sobre a execução de um coração cirurgia. Os alunos emparelham e criam uma experiência de laboratório de habilidades compartilhadas que permite que os alunos médicos colaborem no modelo de coração e aprendam.
* **Diretrizes**: Quando uma pessoa está ajudando alguém a resolver um problema em uma interação de estilo um ou mais um. Por exemplo: O professor que oferece orientação a um aluno quando ele está realizando o laboratório de conhecimentos de cirurgia de coração na experiência compartilhada.

### <a name="2-what-is-the-group-size"></a>2. Qual é o tamanho do grupo?

As experiências de compartilhamento de **um para um** podem fornecer uma linha de base forte e, teoricamente, suas provas de conceito podem ser criadas nesse nível. Mas esteja ciente de que o compartilhamento com grupos grandes (além de 6 pessoas) pode levar a dificuldades de técnicas (dados e rede) para o social (o impacto de estar em sala com [vários avatars](https://vimeo.com/160704056)). A complexidade aumenta exponencialmente à medida que você vai de **pequenos** a **grandes grupos**.

Descobrimos que as necessidades dos grupos podem se enquadrar em três categorias de tamanho:
* 1:1
* Pequeno < 7
* > Grande = 7

O tamanho do grupo faz uma pergunta importante porque ele influencia:
* Representações de pessoas no espaço de Holographic
* Escala de objetos
* Escala de ambiente

### <a name="3-where-is-everyone"></a>3. Onde está todos?

A força da realidade misturada entra em cena quando uma experiência compartilhada pode ocorrer no mesmo local. Chamamos isso de **colocalizado**. Por outro lado, quando o grupo é distribuído e pelo menos um participante não está no mesmo espaço físico (como geralmente é o caso com VR), chamamos isso de uma experiência remota. Geralmente, é o caso de seu **grupo ter participantes** colocalizados e remotos (por exemplo, dois grupos em salas de conferência).

![Três pessoas com holograph na tabela](images/three-people-with-holograph-on-table-500px.png)

As categorias a seguir ajudam a transmitir onde os usuários estão localizados:
* Colocalizado: Todos os usuários estarão no mesmo espaço físico.
* Controle Todos os usuários estarão em espaços físicos separados.
* Mesmo Os usuários serão uma combinação de espaços colocalizados e remotos.

Alguns motivos pelos quais essa pergunta é crucial porque influencia:
* Como as pessoas se comunicam?
* Por exemplo: Se eles devem ter avatars?
* Quais objetos eles veem. Todos os objetos são compartilhados?
* Se precisamos adaptar-se ao seu ambiente?

### <a name="4-when-are-they-sharing"></a>4. Quando estão compartilhando?

Normalmente, pensamos em experiências **síncronas** quando as experiências compartilhadas vêm à mente: Estamos todos fazendo isso juntos. Mas inclua um único elemento virtual que foi adicionado por outra pessoa e que você tenha um cenário **assíncrono** . Imagine uma nota, ou memorando de voz, deixado em um ambiente virtual. Como você lida com os memorandos virtuais 100 no seu design? E se eles forem de dezenas de pessoas com diferentes níveis de privacidade?

Considere suas experiências como uma destas categorias de tempo:
* De forma **síncrona**: Compartilhar a experiência do Holographic ao mesmo tempo. Por exemplo: Dois alunos que executam o laboratório de habilidades ao mesmo tempo.
* De **forma assíncrona**: Compartilhar a experiência do Holographic em momentos diferentes. Por exemplo: Dois alunos executando o laboratório de habilidades, mas trabalhando em seções separadas em momentos diferentes.
* **Ambos**: Os usuários às vezes serão compartilhados de forma síncrona, mas outras vezes assincronamente. Por exemplo: O professor está interrompendo a atribuição realizada pelos alunos em um momento posterior e deixando as anotações para o aluno no dia seguinte.

Alguns motivos pelos quais essa pergunta é importante porque influencia:
* Persistência de objeto e ambiente. Por exemplo: Armazenando os Estados para que eles possam ser recuperados.
* Perspectiva do usuário. Por exemplo: Talvez se lembre do que o usuário estava olhando ao deixar anotações.

### <a name="5-how-similar-are-their-physical-environments"></a>5. Quão semelhantes são seus ambientes físicos?

A probabilidade de dois ambientes reais idênticos, fora de experiências colocalizadas, é Slim, a menos que esses ambientes tenham sido projetados para serem idênticos. É mais provável que você tenha ambientes **semelhantes** . Por exemplo, as salas de conferência são semelhantes — elas normalmente têm uma tabela localizada centralmente envolvida por cadeiras. As salas de vida, por outro lado, geralmente são **diferentes** e podem incluir qualquer número de peças de mobília em uma matriz infinita de layouts.

![Holograph na tabela](images/holograph-on-table-500px.png)

Considere suas experiências de compartilhamento se ajustando a uma destas duas categorias:
* **Semelhante**: Ambientes que tendem a ter móveis semelhantes, luz ambiente e som, tamanho da sala física. Por exemplo: O professor está na sala de palestras A e os alunos estão na sala de palestras B. a Hall da palestra A pode ter menos cadeiras que B, mas ambas podem ter uma escrivaninha física para posicionar os hologramas.
* **Diferente**: Ambientes que são bastante diferentes nas configurações de mobília, tamanhos de sala, considerações de luz e som. Por exemplo: O professor está em um quarto de foco, enquanto os alunos estão em uma grande sala de palestras preenchida com alunos e professores.

É importante pensar no ambiente, pois ele influenciará:
* Como as pessoas irão experimentar esses objetos. Por exemplo: Se sua experiência funciona melhor em uma tabela e o usuário não tem nenhuma tabela? Ou em uma superfície de piso plana, mas o usuário tem um espaço desorganizado.
* Escala dos objetos. Por exemplo: Colocar um modelo humano de 6 pés em uma tabela pode ser desafiador, mas um modelo de coração funcionaria muito bem.

### <a name="6-what-devices-are-they-using"></a>6. Quais dispositivos estão usando?

Hoje, geralmente é provável que você veja experiências compartilhadas entre dois **dispositivos de imersão** (esses dispositivos podem diferir ligeiramente em termos de botões e recursos relativos, mas não muito) ou dois **dispositivos holographics** dadas as soluções que estão sendo direcionadas nesses dispositivos. Mas considere que os **dispositivos 2D** (um participante móvel/de área de trabalho ou observador) serão uma consideração necessária, especialmente em situações de **dispositivos 2D e 3D mistos**. Compreender os tipos de dispositivos que seus participantes usarão é importante, não só porque eles vêm com diferentes limitações de fidelidade e de dados e oportunidades, mas porque os usuários têm expectativas exclusivas para cada plataforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Explorando o potencial de experiências compartilhadas

As respostas às perguntas acima podem ser combinadas para entender melhor seu cenário compartilhado, crystallizingndo os desafios à medida que você expandir a experiência. Para a equipe da Microsoft, isso ajudou a estabelecer um mapa de estrada para melhorar as experiências que usamos hoje, compreendendo a nuance desses problemas complexos e como aproveitar as experiências compartilhadas na realidade misturada.

Por exemplo, considere um dos cenários do Skype do lançamento do HoloLens: um usuário trabalhou por meio de [como corrigir uma mudança de luz quebrada](https://www.youtube.com/watch?v=iBfzs3G8BEA) com a ajuda de um especialista localizado remotamente.

![Corrigindo uma mudança de luz com assistência por meio do Skype para o HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>Um especialista fornece diretrizes de <b>1:1</b> de seu computador desktop <b>2D</b>para um usuário de um dispositivo <b>3D, de realidade mista</b> . A <b>diretriz</b> é <b>síncrona</b> e os ambientes físicos são <b>diferentes</b>.</i>

Uma experiência como esta é uma mudança na nossa experiência atual, aplicando o paradigma de vídeo e voz a um novo meio. Mas à medida que olhamos para o futuro, devemos definir melhor a oportunidade de nossos cenários e criar experiências que reflitam a força da realidade misturada.

Considere a [ferramenta de colaboração do onsight](https://www.youtube.com/watch?v=ZOWQp0-Bkkw) desenvolvida pelo laboratório Jet propulsão da NASA. Os cientistas que trabalham com dados das missões de Rover do Mars podem colaborar com colegas em tempo real dentro dos dados do Martian Landscape.

![Colaboração entre colegas separados remotamente para planejar o trabalho para o Rover Mars](images/onsight-nasa-jpl.gif)

<i>Um cientista explora um ambiente usando um dispositivo <b>3D, de realidade misturada,</b> com um <b>pequeno</b> grupo de colegas <b>remotos</b> usando dispositivos <b>3D e 2D</b> . A <b>colaboração</b> é <b>síncrona</b> (mas pode ser revisitada de forma assíncrona) e os ambientes físicos são (virtualmente) <b>semelhantes</b>.</i>

Experiências como o onsight apresentam novas oportunidades para colaborar. De apontar elementos fisicamente no ambiente virtual para posicionar ao lado de um colega e compartilhar sua perspectiva à medida que eles explicam suas descobertas. O onsight usa a lente de imersão e a presença para reconsiderar as experiências de compartilhamento em realidade misturada.

A colaboração intuitiva é a Fundação da conversa e o trabalho em conjunto e a compreensão de como podemos aplicar essa intuição à complexidade da realidade misturada é crucial. Se não pudermos recriar experiências de compartilhamento apenas em realidade misturada, mas Potencialize-las, será uma mudança de paradigma para o futuro do trabalho. A criação de experiências compartilhadas na realidade misturada é um espaço novo e empolgante, e estamos apenas no começo.

## <a name="get-started-building-shared-experiences"></a>Introdução à criação de experiências compartilhadas

Dependendo do seu aplicativo e cenário, haverá vários requisitos para atingir a experiência desejada. Alguns desses incluem
* Criação de correspondência: Capacidade de criar sessões, anunciar sessão e descobrir e convidar pessoas específicas, localmente e remotamente, para ingressar na sua sessão.
* Compartilhamento de âncora: Capacidade de alinhar as coordenadas em vários dispositivos em um espaço local comum, portanto, os hologramas aparecem no mesmo lugar para todas as pessoas.
* Rede Capacidade de ter posições, interações e movimentos de pessoas e hologramas sincronizados em tempo real em todos os participantes.
* Armazenamento de Estado: Capacidade de armazenar as características e os locais do holograma em espaço para a junção de sessão intermediária, recall em um momento posterior e robustez contra problemas de rede.


A chave para experiências compartilhadas é que vários usuários veem os mesmos hologramas no mundo em seu próprio dispositivo, frequentemente feito por meio do compartilhamento de âncoras para alinhar as coordenadas entre os dispositivos.
Para compartilhar âncoras, use as <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espaciais do Azure</a>:
* Primeiro, o usuário coloca o holograma.
* O aplicativo cria uma [âncora espacial](coordinate-systems.md) para fixar esse holograma precisamente no mundo.
* As âncoras podem ser compartilhadas para dispositivos de HoloLens, iOS e Android por meio das <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espaciais do Azure</a>. 

Com uma âncora espacial compartilhada, o aplicativo em cada dispositivo agora tem um sistema de coordenadas comum no qual eles podem inserir conteúdo. Agora o aplicativo pode garantir a posição e a orientação do holograma no mesmo local.
Em dispositivos HoloLens, você também pode compartilhar âncoras offline de um dispositivo para outro.  Use os links abaixo para decidir o que é melhor para seu aplicativo.


## <a name="evaluating-tech-options"></a>Avaliando opções de tecnologia:
Há várias opções de serviço e tecnologia disponíveis para ajudar a criar experiências de realidade mista de vários usuários.  Pode ser difícil escolher um caminho, portanto, tomando uma perspectiva com foco no cenário, algumas opções são detalhadas abaixo.

## <a name="shared-static-holograms-no-interactions"></a>Hologramas estáticos compartilhados (sem interações):
Aproveite as <a href="https://docs.microsoft.com/azure/spatial-anchors/" target="_blank">âncoras espaciais do Azure</a> em seu aplicativo.  A habilitação e o compartilhamento de âncoras espaciais entre dispositivos permite que você crie um aplicativo onde os usuários vejam os hologramas no mesmo local ao mesmo tempo.  A sincronização adicional entre dispositivos é necessária para permitir que os usuários interajam com hologramas e veja movimentos ou atualizações de estado de hologramas.

## <a name="share-1st-person-perspective"></a>Compartilhar a perspectiva da 1ª pessoa:
Aproveite o suporte ao Miracast interno, para usuários locais quando você tem um receptor de Miracast com suporte, como um PC ou TV, nenhum código de aplicativo adicional é necessário.

Aproveite o <a href="https://github.com/microsoft/mixedreality-webrtc" target="_blank">MixedReality-WebRTC</a> em seu aplicativo, para usuários remotos ou quando você tiver dispositivos não Miracast que gostaria de compartilhar.  A habilitação de uma conexão WebRTC permite fluxos de áudio/vídeo 1:1 entre usuários, com um canal de dados para mensagens entre dispositivos também.  A implementação da realidade misturada otimiza para o HoloLens, fornecendo um fluxo de vídeo de captura de realidade misturada da exibição do usuário do HoloLens para outras pessoas.  Se você quiser escalar verticalmente o streaming de vídeo para vários clientes remotos, um <a href="https://webrtcglossary.com/mcu/" target="_blank">provedor de serviços de MCU</a> (unidade de conferência do MultiPoint) normalmente será usado, como SignalWire.  Uma implantação de SignalWire de um clique no Azure está disponível por meio do <a href="https://github.com/andywolk/azure-freeswitch-gpu-windows" target="_blank">FreeSwitch</a>.  Observe que este é um serviço pago e o SignalWire não é de propriedade/afiliado à Microsoft.

## <a name="presenter-spectator-applications-and-demos"></a>Apresentador-Spectator aplicativos e demonstrações:
Aproveite o <a href="https://github.com/microsoft/MixedReality-SpectatorView" target="_blank">MixedReality-SpectatorView</a> em seu aplicativo.  Habilite outros dispositivos (HL, Android, iOS e câmeras de vídeo) para ver o que o HoloLens vê de uma perspectiva diferente no mesmo local e receber atualizações de interações do usuário de HoloLens host interagindo com os hologramas.  Assista, tire fotos * e grave vídeo sobre o que o host faz com os hologramas no aplicativo de sua própria perspectiva espacial com o Spectator Companion do mesmo aplicativo.

Anotações As imagens são obtidas por meio de captura de tela em dispositivos iOS/Android.

## <a name="multi-user-collaborative-experience"></a>Experiência colaborativa de vários usuários:
Comece com nosso [tutorial de aprendizado de vários usuários](mrlearning-sharing(photon)-ch1.md), que aproveita as <a href="https://docs.microsoft.com/azure/spatial-anchors/" target="_blank">âncoras espaciais do Azure</a> para usuários locais e o <a href="https://www.photonengine.com/PUN" target="_blank">SDK do Photon</a> para sincronizar o conteúdo/estado na cena.  Crie aplicativos de colaboração localmente em que cada usuário tem sua própria perspectiva sobre os hologramas na cena e pode interagir totalmente com os hologramas.  As atualizações são fornecidas em todos os dispositivos e o gerenciamento de conflitos de interação é tratado pelo Photon.  Observe que o Photon é um produto que não é da Microsoft, portanto, uma relação de cobrança com Photon pode ser necessária para produto e dimensionamento para maior uso.

## <a name="future-work"></a>Trabalho futuro:
As interfaces e os recursos do componente ajudarão a fornecer consistência comum e suporte robusto em vários cenários e tecnologias subjacentes.  Até lá, escolha o melhor caminho que se alinhe ao cenário que você está tentando atingir em seu aplicativo.

Cenário diferente ou desejo de usar um Tech/Service diferente?  
Forneça comentários como problemas do GitHub no repositório correspondente, na parte inferior desta página ou entre em contato com a <a href="https://holodevelopers.slack.com/">margem de atraso do HoloDevelopers</a>.


## <a name="see-also"></a>Consulte também
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* [Âncoras espaciais compartilhadas no DirectX](shared-spatial-anchors-in-directx.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)
* [Modo de exibição Espectador](spectator-view.md)

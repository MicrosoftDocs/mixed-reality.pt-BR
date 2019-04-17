---
title: MR 250 - HoloLens e fones imersivos em exposição de compartilhamento
description: Siga este passo a passo usando o Unity, o Visual Studio, o HoloLens e o Windows Mixed Reality headsets para saber os detalhes de compartilhamento hologramas entre dispositivos de realidade mista de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, imersivo, controlador, compartilhamento, o controlador do xbox, rede, entre dispositivos de movimento
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589181"
---
>[!NOTE]
>Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.  Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.  Eles serão mantidos para continuar trabalhando nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.  Este aviso será atualizado com um link para esses tutoriais quando são lançadas.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR Sharing 250: HoloLens e fones imersivos em exposição

Com a flexibilidade de plataforma Universal do Windows (UWP), é fácil criar um aplicativo que abrange vários dispositivos. Com essa flexibilidade, podemos criar experiências que aproveitam os pontos fortes de cada dispositivo. Este tutorial abordará uma experiência básica de compartilhado que é executado em HoloLens e o Windows Mixed Reality fones imersivos em exposição. Este conteúdo foi originalmente entregue na conferência Microsoft Build 2017 em Seattle, WA.

**Neste tutorial, nós iremos:**

* Configure uma rede usando UNET.
* Compartilhar hologramas entre dispositivos de realidade misturada.
* Estabeleça uma exibição diferente do aplicativo, dependendo de quais dispositivos de realidade mista está sendo usado.
* Crie uma experiência de compartilhada em que os usuários do HoloLens orientar usuários fones imersivos em exposição por meio de alguns quebra-cabeças simples.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td>MR Sharing 250: HoloLens e fones imersivos em exposição</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um computador Windows 10 com o [ferramentas de desenvolvimento necessárias](install-the-tools.md) e [configurado para dar suporte a um fone de ouvido imersivo Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Um controlador do Xbox que funciona com o seu PC.
* Pelo menos um dispositivo HoloLens e um fone de ouvido envolvente.
* Uma rede que permite a difusão do UDP para descoberta.

### <a name="project-files"></a>Arquivos de projeto

* Baixe o [arquivos](https://github.com/Microsoft/MixedReality250/archive/master.zip) exigidos pelo projeto. Extraia os arquivos em uma forma fácil de lembrar local.
* Este projeto requer o [uma versão recomendada do Unity com suporte do Windows Mixed Reality](install-the-tools.md).

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capítulo 1 - Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Objetivos

Verifique se que o ambiente de desenvolvimento está pronto para começar com um projeto simples.

### <a name="what-we-will-build"></a>O que devemos criar

Um aplicativo que mostra um holograma em HoloLens ou um fone de ouvido Windows Mixed Reality envolvente.

### <a name="steps"></a>Etapas
* Abrir o Unity.
    * Selecione **aberto**.
    * Navegue até onde você extraiu os arquivos de projeto.
    * Clique em **Selecionar Pasta**.
    * *Levará um pouco enquanto para o Unity processar o projeto na primeira vez.*
* Verifique se a realidade misturada é habilitada no Unity.
    * Abra a caixa de diálogo de configurações de compilação (**Control + Shift + B** ou **arquivo > configurações de compilação...** ).
    * Selecione **plataforma Universal do Windows** , em seguida, clique em **alternar plataforma**.
    * Selecione **Editar > configurações do Player**.
    * No **Inspector** no lado direito do painel, expanda **XR configurações**.
    * Verifique as **suporte de realidade Virtual** caixa.
    * *Realidade mista do Windows deve ser o SDK de realidade Virtual.*
* Crie uma cena.
    * No **hierarquia** clique com botão direito **câmera principal** selecionar **excluir**.
    * Partir **HoloToolkit > entrada > pré-fabricados** arraste **MixedRealityCameraParent** para o **hierarquia**.
* Adicionar hologramas à cena
    * Partir **AppPrefabs** arraste **Skybox** para o **exibição de cena**.
    * Da **AppPrefabs** arraste **gerentes** para o **hierarquia**.
    * Partir **AppPrefabs** arraste **Ilha** para o **hierarquia**.
* Salve e compile
    * Salvar (qualquer um dos **controle + S** ou **arquivo > Salvar cena**)
    * Como essa é uma nova cena, será necessário nomeá-lo. Nome não importa, mas podemos usar SharedMixedReality.
* Exportar para o Visual Studio
    * Abra o menu de compilação (**Control + Shift + B** ou **arquivo > configurações de Build**)
    * Clique em **adicionar cenas abertas.**
    * Verifique **Unity C# projetos**
    * Clique em **Compilar**.
    * Na janela de Gerenciador de arquivo que aparece, crie uma nova pasta chamada **aplicativo**.
    * Único clique a **aplicativo** pasta.
    * Pressione **Selecionar pasta.**
    * **Aguarde a conclusão da compilação**
    * Na janela de Gerenciador de arquivo que aparece, navegue até a **aplicativo** pasta.
    * Clique duas vezes em **SharedMixedReality.sln** para iniciar o Visual Studio
* Compilar do Visual Studio
    * Usando a barra de ferramentas superior alterar destino **Release** e **x86**.
    * Clique na seta ao lado **computador Local** e selecione **dispositivo** para implantar em HoloLens
    * Clique na seta ao lado **dispositivo** e selecione **Máquina Local** implantar para o headset de realidade misturada.
    * Clique em **Depurar -> Iniciar sem depuração** ou **controle + F5** para iniciar o aplicativo.

### <a name="digging-into-the-code"></a>Compreendendo o código

No painel de projeto, navegue até **Assets\HoloToolkit\Input\Scripts\Utilities** e clique duas vezes **MixedRealityCameraManager.cs** para abri-lo.

**Visão geral:** MixedRealityCameraManager.cs é um script simples que ajusta as configurações de plano de fundo e o nível de qualidade com base no dispositivo. Chave aqui é HolographicSettings.IsDisplayOpaque, que permite que um script para detectar se o dispositivo é um HoloLens (IsDisplayOpaque retorna false) ou um fone de ouvido imersivo (IsDisplayOpaque retorna true).

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Neste ponto o aplicativo simplesmente renderizará um holograma. Vamos adicionar interação para o holograma mais tarde. Ambos os dispositivos renderizará o holograma o mesmo. O fone de ouvido envolvente também processará um plano de fundo de nuvens e céu azul.

## <a name="chapter-2---interaction"></a>Capítulo 2 - interação

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Objetivos

Mostram como manipular a entrada para um aplicativo de realidade mista do Windows.

### <a name="what-we-will-build"></a>O que devemos criar

Criando o aplicativo do capítulo 1, vamos adicionar funcionalidade para permitir que o usuário selecionar o holograma e coloque-o em uma superfície do mundo real no HoloLens ou em uma tabela virtual em um fone de ouvido imersivo.

**Atualizador de entrada:** No HoloLens o gesto de select é a **polegar**. Em fones imersivos em exposição, usaremos o **um** botão no controlador do Xbox. Para obter mais informações sobre entrada [comece por aqui](gestures.md).

### <a name="steps"></a>Etapas
* Adicionar Gerenciador de entrada
    * Partir **HoloToolkit > entrada > pré-fabricados** arraste **InputManager** para **hierarquia** como um filho do **gerenciadores de**.
    * Partir **HoloToolkit > entrada > pré-fabricados > Cursor** arraste **Cursor** para **hierarquia**.
* Adicionar mapeamento espacial
    * Partir **HoloToolkit > SpatialMapping > pré-fabricados** arraste **SpatialMapping** para **hierarquia**.
* Adicionar Playspace Virtual
    * Na **hierarquia** expandir **MixedRealityCameraParent** selecione **limites**
    * Na **Inspector** painel de marcar a caixa para habilitar **limites**
    * Partir **AppPrefabs** arraste **VRRoom** para **hierarquia**.
* Add WorldAnchorManager
    * Na **hierarquia**, selecione **gerenciadores**.
    * Na **Inspector**, clique em **adicionar componente**.
    * Tipo de **Gerenciador de âncora do mundo**.
    * Selecione **Gerenciador de âncora do mundo** para adicioná-lo.
* Adicionar TapToPlace a ilha de
    * Na **hierarquia**, expanda **Ilha**.
    * Selecione **MixedRealityLand**.
    * Na **Inspector**, clique em **adicionar componente**.
    * Tipo de **toque para outro** e selecioná-lo.
    * Verifique **colocar pai com um toque de**.
    * Definir **deslocamento de posicionamento** à **(0, 0,1, 0)**.
* Salve e compile como antes

### <a name="digging-into-the-code"></a>Compreendendo o código

**Script 1 - GamepadInput.cs**

No painel de projeto, navegue até **Assets\HoloToolkit\Input\Scripts\InputSources** e clique duas vezes **GamepadInput.cs** para abri-lo. Do mesmo caminho no painel de projeto, também clicar duas vezes **InteractionSourceInputSource.cs**.

Observe que os dois scripts têm uma classe base comum, BaseInputSource.

BaseInputSource mantém uma referência a um InputManager, que permite que um script para disparar eventos. Nesse caso, o evento InputClicked é relevante. Isso será importante lembrar quando chegamos ao script 2, TapToPlace. No caso de GamePadInput, podemos sondar o botão no controlador seja pressionado, em seguida, podemos gerar o evento de InputClicked. No caso de InteractionSourceInputSource, podemos gerar o evento de InputClicked em resposta ao TappedEvent.

**Script 2 - TapToPlace.cs**

No painel de projeto, navegue até **Assets\HoloToolkit\SpatialMapping\Scripts** e clique duas vezes **TapToPlace.cs** para abri-lo.

A primeira coisa de que muitos desenvolvedores querem implementar ao criar um aplicativo holográfico está se movendo hologramas com a entrada do gesto. Como tal, já podemos endeavored comentar completamente esse script. Algumas coisas que vale a pena destacar para este tutorial.

Primeiro, observe que TapToPlace implementa IInputClickHandler. IInputClickHandler expõe as funções que manipular o evento InputClicked gerado por GamePadInput.cs ou InteractionSourceInputSource.cs. OnInputClicked é chamado quando um BaseInputSource detecta um clique, enquanto o objeto com TapToPlace está em foco. Airtapping em HoloLens ou pressionando o botão no controlador do Xbox irá disparar o evento.

Em segundo lugar, é o código ser executado em update para verificar se uma superfície está sendo examinada para que podemos pode colocar o objeto do jogo em uma superfície, como uma tabela. O fone de ouvido imersivo não tem um conceito de superfícies real, portanto, o objeto que representa o table-top (Vroom > TableThingy > cubo) foi marcada com a camada física de SpatialMapping, portanto, o raio converter na atualização vai de encontro com o topo da tabela virtual.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Neste momento você pode selecionar a ilha para movê-lo. Em HoloLens, você pode mover a ilha para uma superfície real. O Headset imersivo, você pode mover a ilha para a tabela virtual que adicionamos.

## <a name="chapter-3---sharing"></a>Capítulo 3 - compartilhamento

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Objetivos

Certifique-se de que a rede está configurada corretamente e detalham como âncoras espaciais são compartilhadas entre dispositivos.

### <a name="what-we-will-build"></a>O que devemos criar

Converteremos nosso projeto a um projeto com vários participantes. Adicionaremos interface do usuário e a lógica ao host ou junção de sessões. HoloLens usuários verá uns aos outros na sessão com nuvens grego e usuários de imersão fone de ouvido têm nuvens perto de onde é a âncora. Usuários no fones imersivos em exposição verão os usuários do HoloLens relativo à origem da cena. Os usuários do HoloLens todos verão que o holograma da ilha de no mesmo local. É importante observar que os usuários no fones imersivos em exposição não será a ilha durante este capítulo, mas irão se comportar de maneira muito semelhante ao HoloLens, com um modo de exibição de olho pássaros da ilha de.

### <a name="steps"></a>Etapas
* Ilha de remover e VRRoom
    * Na **hierarquia** com o botão direito **Ilha** selecione **excluir**
    * Na **hierarquia** com o botão direito **VRRoom** selecione **excluir**
* Adicionar Usland
    * Partir **AppPrefabs** arraste **Usland** para **hierarquia**.
* Partir **AppPrefabs** arraste cada um dos procedimentos a seguir para **hierarquia**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Salve e compile como antes

### <a name="digging-into-the-code"></a>Compreendendo o código

No painel de projeto, navegue até **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** e clique duas vezes em **UnetAnchorManager.cs**. A capacidade para um HoloLens compartilhar informações de rastreamento com outro HoloLens, de modo que ambos os dispositivos podem compartilhar o mesmo espaço é quase mágico. O poder da realidade misturada é ativado quando duas ou mais pessoas podem colaborar usando os mesmos dados digitais.

Algumas coisas a destacar neste script:

A função de início, observe a verificação de **IsDisplayOpaque**. Nesse caso, vamos fingir que a âncora é estabelecida. Isso ocorre porque os fones imersivos em exposição não expõem uma maneira de importar ou exportar as âncoras. No entanto, se estamos executando em um HoloLens, esse script implementa as âncoras de compartilhamento entre os dispositivos. O dispositivo que inicia a sessão irá criar uma âncora de exportação. O dispositivo que ingressa em uma sessão solicita a âncora do dispositivo que iniciou a sessão.

**Exportando:**

Quando um usuário cria uma sessão, NetworkDiscoveryWithAnchors chamará a função UNETAnchorManagers CreateAnchor. Vamos acompanhar CreateAnchor fluxo.

Vamos começar fazendo um pouco de manutenção, apagando todos os dados que podem coletamos para âncoras anteriores. Em seguida, verificamos se há uma âncora em cache para carregar. Os dados de âncora tendem a ser entre 5 e 20 MB, então reutilizar âncoras em cache pode salvar a quantidade de dados, precisamos transferir via rede. Veremos como isso funciona um pouco mais tarde. Mesmo que podemos estiver reutilizando a âncora, precisamos obter a âncora de dados prontos no caso de um novo cliente junções que não possuem a âncora.

Falando em Preparando os dados de ancoragem, a classe WorldAnchorTransferBatch expõe a funcionalidade para preparar os dados de âncora para o envio para outro dispositivo ou aplicativo e a funcionalidade para importar os dados de âncora. Já que estamos no caminho de exportação, vamos adicionar nossa âncora para o WorldAnchorTransferBatch e chamar a função ExportAsync. ExportAsync, em seguida, chamará o retorno de chamada WriteBuffer ao gerar dados para exportação. Quando todos os dados foram exportados ExportComplete será chamado. WriteBuffer adicionamos o bloco de dados a uma lista que mantemos para exportação. No ExportComplete podemos converter a lista em uma matriz. A variável AnchorName é também definida, que irá disparar outros dispositivos para solicitar a âncora se eles não o tiver.

Em alguns casos, a âncora não exportar ou criará dados tão pouco que tentaremos novamente. Aqui podemos simplesmente chamar CreateAnchor novamente.

Uma função final no caminho de exportação é AnchorFoundRemotely. Quando o outro dispositivo encontra a âncora, que o dispositivo informará o host e o host de usá-lo como um sinal de que a âncora é uma "âncora bom" e pode ser armazenados em cache.

**Importando:**

Quando um HoloLens ingressa em uma sessão, ela precisa importar uma âncora. Na função de atualização do UNETAnchorManager, o AnchorName é sondada. Quando o nome de âncora for alterado, inicia o processo de importação. Primeiro, tentamos carregar a âncora com o nome especificado do repositório local de ancoragem. Se ela já, podemos usar isso sem baixar os dados novamente. Se ele não for necessário, em seguida, chamamos WaitForAnchor que iniciará o download.

Quando o download for concluído, NetworkTransmitter_dataReadyEvent é chamado. Isso sinalizará o loop de atualização chamar ImportAsync com os dados baixados. ImportAsync chamará ImportComplete quando o processo de importação for concluído. Se a importação for bem-sucedida, a âncora será salvo no repositório local do player. PlayerController.cs realmente faz a chamada para AnchorFoundRemotely para informar o host que uma boa âncora foi estabelecida.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Esse tempo um usuário com um HoloLens hospedará uma sessão usando o **iniciar sessão** botão na interface do usuário. Outros usuários, tanto no HoloLens ou um fone de ouvido imersivo, serão selecione a sessão e, em seguida, selecione a **ingressar sessão** botão na interface do usuário. Se você tiver várias pessoas com dispositivos HoloLens, elas terão nuvens vermelhos grego. Também haverá uma nuvem azul para cada fone de ouvido imersivo, mas as nuvens azuis não será acima fones de ouvido, pois os fones de ouvido não estão tentando localizar o mesmo espaço de coordenadas do mundo que os dispositivos do HoloLens.

Neste ponto do projeto é um aplicativo de compartilhamento independente; ele não faz muita coisa e pode atuar como uma linha de base. Nos próximos capítulos, vamos começar criando uma experiência para as pessoas poder aproveitar. Para obter mais diretrizes de experiência de design, clique aqui.

## <a name="chapter-4---immersion-and-teleporting"></a>Capítulo 4 - imersão e teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Objetivos

Atendem a experiência de cada tipo de dispositivo de realidade misturada.

### <a name="what-we-will-build"></a>O que devemos criar

Atualizaremos o aplicativo para colocar os usuários de imersão fone de ouvido na ilha de um modo de exibição de imersão. Os usuários do HoloLens ainda terá o panorama da ilha de. Os usuários de cada tipo de dispositivo podem ver outros usuários como eles aparecem no mundo. Por exemplo, usuários de imersão fone de ouvido podem ver os outros avatares de outros caminhos na ilha de, e eles veem os usuários do HoloLens como nuvens gigantes acima da ilha de. Os usuários de imersão fone de ouvido também verá o cursor de ray de olhar o HoloLens do usuário se o usuário HoloLens está observando a ilha. Os usuários do HoloLens verá um avatar a ilha para representar cada usuário envolventes fone de ouvido.

**Entrada atualizada para o dispositivo imersivo:**
* Os botões esquerdos amortecedores e à direita amortecedores no controlador do Xbox girar o player
* Segurando o botão Y no controlador do Xbox permitirá uma [ser transportado](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) cursor. Se o cursor tem um indicador de seta giratória quando você solta o botão de Y, será teleported ao local do cursor.

### <a name="steps"></a>Etapas
* Adicionar MixedRealityTeleport a MixedRealityCameraParent
    * Na **hierarquia**, selecione **Usland**.
    * No **Inspetor**, habilite **nível de controle**.
    * Na **hierarquia**, selecione **MixedRealityCameraParent**.
    * Na **Inspector**, clique em **adicionar componente**.
    * Tipo de **ser transportado de realidade misturada** e selecioná-lo.

### <a name="digging-into-the-code"></a>Compreendendo o código

Os usuários de imersão fone de ouvido serão ser vinculados a seus PCs com um cabo, mas nosso Ilha é maior do que o cabo é longo. Para compensar, é necessário ter a capacidade de mover a câmera independentemente do movimento do usuário. Consulte a [página de conforto](comfort.md) para obter mais informações sobre como projetar seu aplicativo de realidade misturada (movimento self em particular e locomotion).

Para descrever esse processo é útil definir dois termos. Primeiro, **carrinho de mão** será o objeto que move a câmera de forma independente do usuário. Um objeto do jogo de filho a **carrinho de mão** será o **câmera principal**. A câmera principal está anexada ao cabeçalho do usuário.

No painel de projeto, navegue até **Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **MixedRealityTeleport.cs**.

MixedRealityTeleport tem dois trabalhos. Primeiro, ele trata a rotação usando os complementos. Na função atualizar nós sondar ButtonUp em LeftBumper e RightBumper. GetButtonUp retorna true somente no primeiro quadro de que um botão está ativo após ter ficado inativo. Se um dos botões foram aumentados, nós sabemos que o usuário precisa girar.

Quando estamos girar podemos fazer um fade out e aplicar fade-in usando um script simples chamado 'fade controle'. Fazemos isso para impedir que o usuário visualizem um movimento artificial que pode levar a discomfort. O fade in e check-out em vigor é bastante simple. Temos um quad preto deslocado na frente do **câmera principal**. Quando o desaparecimento passamos o valor alfa de 0 a 1. Isso gradualmente faz com que os pixels pretos do quad para renderizar e ocultar qualquer coisa por trás delas. Quando esmaecido no passamos o valor alfa para zero.

Quando podemos calcular a rotação, observe que estamos está girando nossos **carrinho de mão** mas Calculando a rotação em torno de **câmera principal**. Isso é importante como mais distantes a **câmera principal** esteja distante 0, 0,0, menos precisa uma rotação em torno de carrinho de mão se tornaria do ponto de vista do usuário. Na verdade, se você não giram em torno a posição da câmera, o usuário passará um arco em torno de **carrinho de mão** em vez de girar.

O segundo trabalho para MixedRealityTeleport é manipular movendo o **carrinho de mão**. Isso é feito no SetWorldPosition. SetWorldPosition leva a posição do mundo desejado, a posição em que o usuário se deseja percieve habitam por eles. Precisamos colocar nossos **carrinho de mão** naquela posição menos a posição de local da **câmera principal**, pois esse deslocamento será adicionado a cada quadro.

Um segundo script chama SetWorldPosition. Vamos dar uma olhada no script. No painel de projeto, navegue até **Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **TeleportScript.cs**.

Esse script é um pouco mais envolvido do que MixedRealityTeleport. O script está verificando o botão de Y no controlador do Xbox para ser pressionada. Enquanto o botão é mantido para baixo um ser transportado cursor é renderizado e o script converte um raio de posição de olhar do usuário. Se esse ray entra em conflito com uma superfície que é mais ou menos apontando para cima, a superfície será considerada uma superfície boa para ser transportado para e a animação no cursor de ser transportado será habilitada. Se o raio não entrarem em conflito com uma superfície mais ou menos apontando para cima, em seguida, a animação no cursor será desabilitada. Quando o botão de Y é liberado e o ponto calculado do raio é uma posição válida, o script chama SetWorldPosition com a posição que cruzam o raio.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Neste momento você precisará encontrar um amigo.

Mais uma vez, um usuário com o HoloLens irá hospedar uma sessão. Outros usuários serão ingressar na sessão. O aplicativo colocará os três primeiros usuários para ingresso em um fone de ouvido imersão em um dos três caminhos a ilha. Fique à vontade explorar a ilha nesta seção.

Detalhes a observar:
1. Você pode ver os rostos nas nuvens, que ajuda um usuário immersed ver a direção na qual um usuário do HoloLens está procurando.
2. Os avatares na ilha de tem necks giram. Eles não seguem o que o usuário está fazendo é realidade real (não temos informações), mas faz uma boa experiência.
3. Se o usuário HoloLens está observando a ilha, os usuários immersed podem ver seu cursor.
4. As nuvens que representam os usuários do HoloLens converter sombras.

## <a name="chapter-5---finale"></a>Capítulo 5 - finale:

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Objetivos

Crie uma experiência interativa de colaboração entre os tipos de dispositivo de duas.

### <a name="what-we-will-build"></a>O que devemos criar

Aproveitando o capítulo 4, quando um usuário com um fone de ouvido imersivo obtém perto de um quebra-cabeça a ilha, os usuários do HoloLens obterá uma dica de ferramenta com uma dica sobre o quebra-cabeça. Depois que todos os usuários de fone de ouvido imersivo obtém após quebra-cabeças e para o "painel pronto" na sala de foguetes, iniciará o rocket.

### <a name="steps"></a>Etapas
* Na **hierarquia**, selecione **Usland**.
* No **Inspetor**, na **nível de controle**, verificar **habilitar colaboração**.

### <a name="digging-into-the-code"></a>Compreendendo o código

Agora vamos dar uma olhada no LevelControl.cs. Esse script é o núcleo da lógica do jogo e mantém o estado do jogo. Como esse é um jogo usando UNET precisamos entender como os dados fluem, pelo menos bem o suficiente para modificar este tutorial. Para obter uma visão mais completa de UNET, consulte a documentação do Unity.

No painel de projeto, navegue até **Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **LevelControl.cs**.

Vamos entenda como um fone de ouvido imersivo indica que eles estão prontos para o lançamento dos rocket. Preparação de inicialização do Rocket é comunicada, definindo uma das três bools em uma lista de bools que correspondem aos três caminhos a ilha. Bool de um caminho será definido quando o usuário atribuído para o caminho é sobre o painel marrom dentro de sala rocket. Okey agora para os detalhes.

Vamos começar na função Update (). Você observará que há uma função 'trapacear'. Nós usamos isso no desenvolvimento para testar o lançamento dos rocket e redefinir a sequência. Ele não funcionará na experiência do usuário com várias. Espero que no momento em que você incorporar as informações a seguir você pode fazê-lo funcionar. Depois, confirmamos se deve trapaceamos, verificamos para ver se o jogador local é aprofundar. Gostaríamos de se concentrar em como podemos encontrar que estamos na meta. Dentro do if (Imersos) verificar, há uma chamada para CheckGoal por trás de **EnableCollaboration** bool. Isso corresponde à caixa de seleção marcada ao concluir as etapas para este capítulo. Dentro de EnableCollaboration vemos uma chamada para CheckGoal().

CheckGoal faz alguns cálculos matemáticos para ver se estamos mais ou menos no teclado de uma posição. Quando for, podemos debug "Recebido na meta de" e, em seguida, podemos chamar 'SendAtGoalMessage()'. No SendAtGoalMessage chamamos playerController.SendAtGoal. Para que você economize algum tempo, aqui está o código:

```cs
private void CmdSendAtGoal(int GoalIndex)
       {
           levelState.SetGoalIndex(GoalIndex);
       }
```

```cs
public void SendAtGoal(int GoalIndex)
       {
           if (isLocalPlayer)
           {
               Debug.Log("sending at goal " + GoalIndex);
               CmdSendAtGoal(GoalIndex);
           }
       }
```

Observe que SendAtGoalMessage chama CmdSendAtGoal, quais levelState.SetGoalIndex chamadas, que está de volta ao LevelControl.cs. A princípio, isso parece estranho. Por que não basta chamar SetGoalIndex em vez de isso estranho roteamento por meio do controlador do jogador? O motivo é que podemos estão em conformidade com o modelo de dados que UNET usa para manter os dados em sincronia. Para evitar trapaça e ultrapaginação, UNET requer que cada objeto tem um usuário que tem autoridade para alterar as variáveis sincronizadas. Além disso, somente o host (o usuário que iniciou a sessão) pode alterar os dados diretamente. Os usuários que não são o host, mas tem autoridade, precisarão enviar um comando para o host que vai alterar a variável. Por padrão o host tem autoridade sobre todos os objetos, exceto para o objeto gerado para representar o usuário. Em nosso caso, esse objeto tem o script playercontroller. Há uma maneira para autoridade para um objeto de solicitação e, em seguida, fazer alterações, mas podemos optar por utilizar o fato de que o controlador do jogador possui autoridade e rota self comandos por meio do controlador do jogador.

Dito outra forma, quando descobrimos que nós mesmos em nosso objetivo, o jogador precisa informar ao host e o host informa todos os outros.

Em LevelControl.cs examinar SetGoalIndex. Aqui definimos o valor de um valor em um synclist (AtGoal). Lembre-se de que estamos no contexto do host enquanto fazemos isso. Semelhante a um comando, uma RPC é algo o host pode emitir que fará com que todos os clientes devem executar algum código. Aqui, podemos chamar 'RpcCheckAllGoals'. Cada cliente individualmente Verifique se todos os três AtGoals estiverem definidas e nesse caso, inicie o rocket.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Compilar no capítulo anterior, começaremos a sessão como antes. Neste momento que os usuários no fone de ouvido imersivo get a "porta" no seu caminho, uma dica de ferramenta será exibida que apenas os usuários do HoloLens podem ver. Os usuários do HoloLens são responsáveis por comunicar essa dica para os usuários o fone de ouvido envolvente. O rocket será iniciado para o espaço após cada avatar tenha passado no seu teclado marrom correspondente dentro do vulcão. A cena será redefinido após 60 segundos, para que você pode fazê-lo novamente.

## <a name="see-also"></a>Consulte também
* [Entrada MR 213: Controladores de movimento](mixed-reality-213.md)

---
title: Sr Sharing 250-o HoloLens e os headsets de imersão
description: Siga este passo a passo de codificação usando headsets de Unity, Visual Studio, HoloLens e Windows Mixed Reality para aprender os detalhes do compartilhamento de hologramas entre dispositivos de realidade misturada.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, imersiva, controlador de movimento, compartilhamento, controlador Xbox, rede, dispositivo cruzado
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63506118"
---
>[!NOTE]
>Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.  Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.  Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.  Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte. Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.  Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>Sr Sharing 250: Headsets de HoloLens e de imersão

Com a flexibilidade do Plataforma Universal do Windows (UWP), é fácil criar um aplicativo que abranja vários dispositivos. Com essa flexibilidade, podemos criar experiências que aproveitam os pontos fortes de cada dispositivo. Este tutorial abordará uma experiência compartilhada básica que é executada em headsets de uso de realidade mista do HoloLens e do Windows. Este conteúdo foi originalmente entregue na conferência do Microsoft Build 2017 em Seattle, WA.

**Neste tutorial, iremos:**

* Configure uma rede usando o UNET.
* Compartilhe hologramas entre dispositivos de realidade misturada.
* Estabeleça uma exibição diferente do aplicativo dependendo de qual dispositivo de realidade misturada está sendo usado.
* Crie uma experiência compartilhada em que os usuários do HoloLens guiam os usuários do headset com um quebra-cabeças simples.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Course</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Sr Sharing 250: Headsets de HoloLens e de imersão</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um PC com Windows 10 com as [ferramentas de desenvolvimento necessárias](install-the-tools.md) e [configurado para dar suporte a um headset de imersão de realidade mista do Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Um controlador Xbox que funciona com seu PC.
* Pelo menos um dispositivo HoloLens e um headset de imersão.
* Uma rede que permite a difusão UDP para descoberta.

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/MixedReality250/archive/master.zip) exigidos pelo projeto. Extraia os arquivos para um local fácil de lembrar.
* Este projeto requer [uma versão recomendada do Unity com o suporte do Windows Mixed Reality](install-the-tools.md).

>[!NOTE]
>Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capítulo 1 – holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Objetivos

Verifique se o ambiente de desenvolvimento está pronto para ser usado com um projeto simples.

### <a name="what-we-will-build"></a>O que iremos criar

Um aplicativo que mostra um holograma sobre o HoloLens ou um headset de imersão de realidade mista do Windows.

### <a name="steps"></a>Etapas
* Abra o Unity.
    * Selecione **abrir**.
    * Navegue até onde você extraiu os arquivos de projeto.
    * Clique em **Selecionar Pasta**.
    * *Levará algum tempo para que o Unity processe o projeto pela primeira vez.*
* Verifique se a realidade misturada está habilitada no Unity.
    * Abra a caixa de diálogo Configurações de compilação (**Control + Shift + B** ou **arquivo > configurações de Build...** ).
    * Selecione **plataforma universal do Windows** , em seguida, clique em **alternar plataforma**.
    * Selecione **Editar configurações do Player >** .
    * No painel **Inspetor** no lado direito, expanda Configurações de **XR**.
    * Verifique a caixa **suporte à realidade virtual** .
    * *A realidade mista do Windows deve ser o SDK da realidade virtual.*
* Crie uma cena.
    * Na **hierarquia** , clique na **câmera principal** selecionar **excluir**.
    * Em **HoloToolkit > entrada > pré-fabricados** arraste **MixedRealityCameraParent** para a **hierarquia**.
* Adicionar hologramas à cena
    * Em **AppPrefabs** , arraste **Skybox** para a **exibição cena**.
    * De **AppPrefabs** , arraste **os gerentes** para a **hierarquia**.
    * Da **ilha** de arrastar **AppPrefabs** para a **hierarquia**.
* Salvar e compilar
    * Salvar ( **controle + S** ou **arquivo > salvar cena**)
    * Como essa é uma nova cena, você precisará nomeá-la. O nome não é importante, mas usamos SharedMixedReality.
* Exportar para o Visual Studio
    * Abra o menu Compilar (**Control + Shift + B** ou **arquivos > configurações de Build**)
    * Clique em **Adicionar abrir cenas.**
    * Verificar **projetos C# do Unity**
    * Clique em **Compilar**.
    * Na janela Explorador de arquivos que aparece, crie uma nova pasta chamada **aplicativo**.
    * Clique uma vez na pasta do **aplicativo** .
    * Pressione **Selecionar pasta.**
    * **Aguarde a conclusão da compilação**
    * Na janela Explorador de arquivos que aparece, navegue até a pasta do **aplicativo** .
    * Clique duas vezes em **SharedMixedReality. sln** para iniciar o Visual Studio
* Compilar a partir do Visual Studio
    * Usando o destino de alteração da barra de ferramentas superior para **liberar** e **x86**.
    * Clique na seta ao lado de **computador local** e selecione **dispositivo** para implantar no HoloLens
    * Clique na seta ao lado de **dispositivo** e selecione **computador local** para implantar para o headset de realidade misturada.
    * Clique em **depurar-> iniciar sem Depurar** ou **controlar + F5** para iniciar o aplicativo.

### <a name="digging-into-the-code"></a>Aprofundando-se no código

No painel projeto, navegue até **Assets\HoloToolkit\Input\Scripts\Utilities** e clique duas vezes em **MixedRealityCameraManager.cs** para abri-lo.

**Sobre** MixedRealityCameraManager.cs é um script simples que ajusta as configurações de nível de qualidade e de segundo plano com base no dispositivo. A chave aqui é HolographicSettings. IsDisplayOpaque, que permite que um script detecte se o dispositivo é um HoloLens (IsDisplayOpaque retorna false) ou um headset de imersão (IsDisplayOpaque retorna true).

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Neste ponto, o aplicativo apenas renderizará um holograma. Adicionaremos interação com o holograma posteriormente. Ambos os dispositivos processarão o holograma da mesma forma. O headset de imersão também renderizará uma fundo azul céu e nuvens.

## <a name="chapter-2---interaction"></a>Capítulo 2-interação

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Objetivos

Mostre como tratar a entrada para um aplicativo do Windows Mixed Reality.

### <a name="what-we-will-build"></a>O que iremos criar

Criando o aplicativo no capítulo 1, adicionaremos funcionalidade para permitir que o usuário pegue o holograma e coloque-o em uma superfície do mundo real no HoloLens ou em uma tabela virtual em um headset de imersão.

**Atualizador de entrada:** No HoloLens, o gesto de seleção é o **toque de ar**. Em headsets de imersão, usaremos **o botão a** no controlador Xbox. Para obter mais informações sobre a entrada, [comece aqui](gestures.md).

### <a name="steps"></a>Etapas
* Adicionar Gerenciador de entrada
    * Em **HoloToolkit > entrada > pré-fabricados** arraste **InputManager** para **hierarquia** como um filho de **gerentes**.
    * From **HoloToolkit > entrada > pré-fabricados >** cursor arrastar **cursor** para **hierarquia**.
* Adicionar mapeamento espacial
    * Em **HoloToolkit > SpatialMapping > pré-fabricados** arraste **SpatialMapping** para **hierarquia**.
* Adicionar Playspace virtual
    * Em **hierarquia** , expanda **MixedRealityCameraParent** selecionar **limite**
    * No painel **Inspetor** , marque a caixa para habilitar o **limite**
    * Em **AppPrefabs** , arraste **VRRoom** para **hierarquia**.
* Adicionar WorldAnchorManager
    * Em **hierarquia**, selecione **gerentes**.
    * No **Inspetor**, clique em **Adicionar componente**.
    * Digite **gerente de âncora mundial**.
    * Selecione **gerente de âncora mundial** para adicioná-lo.
* Adicionar TapToPlace à ilha
    * Em **hierarquia**, expanda **ilha**.
    * Selecione **MixedRealityLand**.
    * No **Inspetor**, clique em **Adicionar componente**.
    * Digite **toque para inserir** e selecione-o.
    * Verifique o **pai ao tocar**.
    * Defina **deslocamento de posicionamento** como **(0, 0,1, 0)** .
* Salvar e compilar como antes

### <a name="digging-into-the-code"></a>Aprofundando-se no código

**Script 1-GamepadInput.cs**

No painel projeto, navegue até **Assets\HoloToolkit\Input\Scripts\InputSources** e clique duas vezes em **GamepadInput.cs** para abri-lo. No mesmo caminho no painel de projeto, também clique duas vezes em **InteractionSourceInputSource.cs**.

Observe que ambos os scripts têm uma classe base comum, BaseInputSource.

BaseInputSource mantém uma referência a um InputManager, que permite que um script dispare eventos. Nesse caso, o evento InputClicked é relevante. Será importante lembrar-se de quando chegarmos ao script 2, TapToPlace. No caso do GamePadInput, pesquisamos um botão no controlador a ser pressionado e, em seguida, geramos o evento InputClicked. No caso do InteractionSourceInputSource, geramos o evento InputClicked em resposta ao TappedEvent.

**Script 2-TapToPlace.cs**

No painel projeto, navegue até **Assets\HoloToolkit\SpatialMapping\Scripts** e clique duas vezes em **TapToPlace.cs** para abri-lo.

A primeira coisa que muitos desenvolvedores desejam implementar ao criar um aplicativo Holographic está movendo hologramas com entrada de gestos. Assim, fizemos um comentário completo sobre esse script. Algumas coisas valem a pena destacar este tutorial.

Primeiro, observe que TapToPlace implementa IInputClickHandler. IInputClickHandler expõe as funções que manipulam o evento InputClicked gerado por GamePadInput.cs ou InteractionSourceInputSource.cs. OnInputClicked é chamado quando um BaseInputSource detecta um clique enquanto o objeto com TapToPlace está em foco. Ao tocar no HoloLens ou pressionar o botão a no controlador Xbox, o evento será disparado.

O segundo é que o código seja executado na atualização para ver se uma superfície está sendo examinada para que possamos posicionar o objeto de jogo em uma superfície, como uma tabela. O headset de imersão não tem um conceito de superfícies reais, portanto, o objeto que representa a tabela superior (Vroom > TableThingy > Cube) foi marcado com a camada física SpatialMapping, portanto, o Ray Cast na atualização irá colidir com a tabela virtual superior.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Desta vez, você pode selecionar a ilha para movê-la. No HoloLens, você pode mover a ilha para uma superfície real. No headset de imersão, você pode mover a ilha para a tabela virtual que adicionamos.

## <a name="chapter-3---sharing"></a>Capítulo 3 – compartilhando

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Objetivos

Verifique se a rede está configurada corretamente e detalhe como as âncoras espaciais são compartilhadas entre os dispositivos.

### <a name="what-we-will-build"></a>O que iremos criar

Converteremos nosso projeto em um projeto de vários participantes. Adicionaremos a interface do usuário e a lógica para hospedar ou ingressar em sessões. Os usuários do HoloLens verão um ao outro na sessão com nuvens em seus cabeçotes e os usuários do headset de imersão têm nuvens perto de onde está a âncora. Os usuários em headsets de imersão verão os usuários do HoloLens em relação à origem da cena. Os usuários do HoloLens verão o holograma da ilha no mesmo local. É importante observar que os usuários nos headsets de imersão não estarão na ilha durante este capítulo, mas se comportarão de forma semelhante ao HoloLens, com uma visão de olho da ilha.

### <a name="steps"></a>Etapas
* Remover ilha e VRRoom
    * Em **hierarquia** , clique com o botão direito do mouse em **ilha** selecionar **excluir**
    * Em **hierarquia** , clique com o botão direito do mouse em **VRRoom** selecionar **excluir**
* Adicionar Usland
    * Em **AppPrefabs** , arraste **Usland** para **hierarquia**.
* Em **AppPrefabs** , arraste cada um dos seguintes para **hierarquia**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Salvar e compilar como antes

### <a name="digging-into-the-code"></a>Aprofundando-se no código

No painel projeto, navegue até **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** e clique duas vezes em **UnetAnchorManager.cs**. A capacidade de um HoloLens compartilhar informações de rastreamento com outro HoloLens, de modo que ambos os dispositivos possam compartilhar o mesmo espaço é quase mágico. O poder da realidade misturada vem ativo quando duas ou mais pessoas podem colaborar usando os mesmos dados digitais.

Algumas coisas para destacar esse script:

Na função iniciar, observe a verificação de **IsDisplayOpaque**. Nesse caso, vamos fingir que a âncora é estabelecida. Isso ocorre porque os headsets de imersão não expõem uma maneira de importar ou exportar âncoras. No entanto, se estivermos executando em um HoloLens, esse script implementará âncoras de compartilhamento entre os dispositivos. O dispositivo que inicia a sessão criará uma âncora para exportação. O dispositivo que ingressa em uma sessão solicitará a âncora do dispositivo que iniciou a sessão.

**Exportar**

Quando um usuário cria uma sessão, NetworkDiscoveryWithAnchors chamará a função createanchor UNETAnchorManagers. Vamos seguir o fluxo de createanchor.

Começamos fazendo algumas realizações, limpando todos os dados que poderemos ter coletado para âncoras anteriores. Em seguida, verificamos se há uma âncora em cache a ser carregada. Os dados de âncora tendem a estar entre 5 e 20 MB, portanto, reutilizar âncoras em cache pode economizar na quantidade de dados que precisamos transferir pela rede. Veremos como isso funciona um pouco mais tarde. Mesmo que estejamos reutilizando a âncora, precisamos obter os dados de âncora prontos caso um novo cliente ingresse que não tenha a âncora.

Falando em colocar os dados de ancoragem prontos, a classe WorldAnchorTransferBatch expõe a funcionalidade para preparar dados âncora para enviar para outro dispositivo ou aplicativo e a funcionalidade para importar os dados de âncora. Como estamos no caminho de exportação, adicionaremos nossa âncora ao WorldAnchorTransferBatch e chamarei a função ExportAsync. Em seguida, ExportAsync chamará o retorno de chamada WriteBuffer, pois ele gera dados para exportação. Quando todos os dados forem exportados, ExportComplete será chamado. No WriteBuffer, adicionamos a parte dos dados a uma lista que mantemos para a exportação. No ExportComplete, convertemos a lista em uma matriz. A variável anchorName também é definida, o que disparará outros dispositivos para solicitar a âncora se eles não o tiverem.

Em alguns casos, a âncora não será exportada ou criará poucos dados que tentaremos novamente. Aqui, basta chamar createanchor novamente.

Uma função final no caminho de exportação é AnchorFoundRemotely. Quando outro dispositivo encontrar a âncora, esse dispositivo dirá o host, e o host usará isso como um sinal de que a âncora é uma "boa âncora" e pode ser armazenada em cache.

**Importar**

Quando um HoloLens ingressa em uma sessão, ele precisa importar uma âncora. Na função Update do UNETAnchorManager, o ancoraname é sondado. Quando o nome da âncora é alterado, o processo de importação é iniciado. Primeiro, tentamos carregar a âncora com o nome especificado do repositório de âncora local. Se já o tiver, podemos usá-lo sem baixar os dados novamente. Se não tivermos, chamamos o WaitForAnchor, que iniciará o download.

Quando o download for concluído, NetworkTransmitter_dataReadyEvent será chamado. Isso sinalizará o loop de atualização para chamar ImportAsync com os dados baixados. ImportAsync chamará ImportComplete quando o processo de importação for concluído. Se a importação for bem-sucedida, a âncora será salva no repositório local do Player. PlayerController.cs realmente faz a chamada para AnchorFoundRemotely para permitir que o host saiba que uma boa âncora foi estabelecida.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Desta vez, um usuário com um HoloLens hospedará uma sessão usando o botão **iniciar sessão** na interface do usuário. Outros usuários, tanto no HoloLens quanto em um headset de imersão, selecionarão a sessão e, em seguida, selecionarão o botão de **sessão de junção** na interface do usuário. Se você tiver várias pessoas com dispositivos de HoloLens, elas terão nuvens vermelhas sobre suas cabeças. Também haverá uma nuvem azul para cada headset de imersão, mas as nuvens azuis não estarão acima dos headsets, pois os headsets não estão tentando encontrar o mesmo espaço de coordenadas do mundo que os dispositivos HoloLens.

Esse ponto no projeto é um aplicativo de compartilhamento independente; Ele não faz muita coisa e pode agir como uma linha de base. Nos próximos capítulos, começaremos a criar uma experiência para as pessoas gostarem. Para obter mais orientações sobre o design de experiência compartilhada, acesse aqui.

## <a name="chapter-4---immersion-and-teleporting"></a>Capítulo 4-imersão e teleportabilidade

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Objetivos

Atenda à experiência de cada tipo de dispositivo de realidade misturada.

### <a name="what-we-will-build"></a>O que iremos criar

Atualizaremos o aplicativo para colocar os usuários de headsets imersivas na ilha com uma exibição imersiva. Os usuários do HoloLens ainda terão a visão panorâmica da ilha. Os usuários de cada tipo de dispositivo podem ver outros usuários como aparecem no mundo. Por exemplo, os usuários de headsets de imersão podem ver os outros avatars em outros caminhos na ilha e eles veem os usuários do HoloLens como nuvens Giant acima da ilha. Os usuários do headset de imersão também verão o cursor do olhar Ray do usuário do HoloLens se o usuário do HoloLens estiver olhando para a ilha. Os usuários do HoloLens verão um avatar na ilha para representar cada usuário do headset de imersão.

**Entrada atualizada para o dispositivo de imersão:**
* Os botões do amortecedor esquerdo e do amortecedor direito no controlador Xbox giram o Player
* Manter o botão Y no controlador Xbox habilitará um cursor [teleport](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) . Se o cursor tiver um indicador de seta girando quando você liberar o botão Y, você será teleportado para o local do cursor.

### <a name="steps"></a>Etapas
* Adicionar MixedRealityTeleport a MixedRealityCameraParent
    * Em **hierarquia**, selecione **Usland**.
    * No **Inspetor**, habilite o **controle de nível**.
    * Em **hierarquia**, selecione **MixedRealityCameraParent**.
    * No **Inspetor**, clique em **Adicionar componente**.
    * Digite **teleport de realidade misturada** e selecione-o.

### <a name="digging-into-the-code"></a>Aprofundando-se no código

Os usuários do headset de imersão serão conectados a seus PCs com um cabo, mas nossa ilha é maior do que o cabo é longo. Para compensar, precisamos da capacidade de mover a câmera independentemente do movimento do usuário. Consulte a [página de conforto](comfort.md) para obter mais informações sobre como criar seu aplicativo de realidade misturada (em particular e Locomotion).

Para descrever esse processo, será útil definir dois termos. Primeiro, **Dolly** será o objeto que move a câmera independentemente do usuário. Um objeto de jogo filho do **Dolly** será a **câmera principal**. A câmera principal é anexada à cabeça do usuário.

No painel projeto, navegue até **Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **MixedRealityTeleport.cs**.

MixedRealityTeleport tem dois trabalhos. Primeiro, ele lida com a rotação usando os amortecedores. Na função Update, pesquisamos por ' ButtonUp ' em LeftBumper e RightBumper. GetButtonUp retorna true no primeiro quadro em que um botão está ativo depois de ter sido desativado. Se um dos botões tivesse sido gerado, sabemos que o usuário precisa girar.

Quando giramos, fazemos um fade out e esmaecemos usando um script simples chamado ' Fade Control '. Fazemos isso para impedir que o usuário veja um movimento não natural que poderia levar a discomfort. O efeito de fade in e saída é bastante simples. Temos um buraco de cruz preto na frente da **câmera principal**. Ao desbotar, fazemos a transição do valor alfa de 0 para 1. Isso gradualmente faz com que os pixels pretos do Quad sejam renderizados e obscurecem qualquer coisa por trás deles. Ao retroceder, fazemos a transição do valor alfa de volta para zero.

Quando calculamos a rotação, observe que estamos girando nosso **Dolly** , mas calculando a rotação em toda a **câmera principal**. Isso é importante, pois o mais distante da **câmera principal** está longe de 0, 0, a rotação menos precisa em relação ao Dolly se tornaria do ponto de vista do usuário. Na verdade, se você não girar a posição da câmera, o usuário será movido em um arco em volta do **Dolly** em vez de girar.

O segundo trabalho para MixedRealityTeleport é manipular a movimentação de **Dolly**. Isso é feito em SetWorldPosition. SetWorldPosition usa a posição do mundo desejada, a posição onde o usuário deseja percieve que estar. Precisamos colocar nosso **Dolly** nessa posição menos a posição local da **câmera principal**, pois esse deslocamento será adicionado a cada quadro.

Um segundo script chama SetWorldPosition. Vamos examinar esse script. No painel projeto, navegue até **Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **TeleportScript.cs**.

Esse script é um pouco mais envolvido do que MixedRealityTeleport. O script está verificando se o botão Y no controlador Xbox será mantido. Enquanto o botão é mantido para baixo, um cursor teleport é renderizado e o script converte um Ray a partir da posição de olhar do usuário. Se esse raio colidir com uma superfície que está mais ou menos apontando para cima, a superfície será considerada uma boa superfície para teleport e a animação no cursor teleport será habilitada. Se o raio não colidir com uma superfície mais ou menos apontando para cima, a animação no cursor será desabilitada. Quando o botão Y é liberado e o ponto calculado do raio é uma posição válida, o script chama SetWorldPosition com a posição do raio interseccionado.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Desta vez, você precisará encontrar um amigo.

Mais uma vez, um usuário com o HoloLens hospedará uma sessão. Outros usuários ingressarão na sessão. O aplicativo fará com que os três primeiros usuários ingressem de um headset de imersão em um dos três caminhos na ilha. Sinta-se à vontade para explorar a ilha nesta seção.

Detalhes a serem observados:
1. Você pode ver os rostos nas nuvens, o que ajuda um usuário imersos a ver qual direção um usuário do HoloLens está olhando.
2. Os avatars na ilha têm pescoços que giram. Eles não seguirão o que o usuário está fazendo é realidade real (não temos essas informações), mas isso faz uma boa experiência.
3. Se o usuário do HoloLens estiver olhando para a ilha, os usuários do imersos poderão ver o cursor.
4. As nuvens que representam os usuários do HoloLens convertem sombras.

## <a name="chapter-5---finale"></a>Capítulo 5 – final

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Objetivos

Crie uma experiência interativa colaborativa entre os dois tipos de dispositivo.

### <a name="what-we-will-build"></a>O que iremos criar

Com base no capítulo 4, quando um usuário com um headset de imersão fica perto de um quebra-cabeça na ilha, os usuários do HoloLens terão uma dica de ferramenta com uma pista para o quebra-cabeça. Depois que todos os usuários do headset de imersão passarem do quebra-cabeças e para a "área pronta" na sala de Rocket, o Rocket será iniciado.

### <a name="steps"></a>Etapas
* Em **hierarquia**, selecione **Usland**.
* No **Inspetor**, em **controle de nível**, marque **habilitar colaboração**.

### <a name="digging-into-the-code"></a>Aprofundando-se no código

Agora vamos examinar LevelControl.cs. Esse script é o núcleo da lógica do jogo e mantém o estado do jogo. Como este é um jogo com vários participantes usando o UNET, precisamos entender como os fluxos de dados, pelo menos, o suficiente para modificar este tutorial. Para obter uma visão geral mais completa do UNET, consulte a documentação do Unity.

No painel projeto, navegue até **Assets\AppPrefabs\Support\Scripts\GameLogic** e clique duas vezes em **LevelControl.cs**.

Vamos entender como um headset de imersão indica que eles estão prontos para o lançamento do Rocket. O Rocket Launch Readiness é comunicado pela definição de um dos Três BOOLs em uma lista de BOOLs que correspondem aos três caminhos na ilha. O bool de um caminho será definido quando o usuário atribuído ao caminho estiver na parte superior do painel marrom dentro da sala de Rocket. Bem, agora para os detalhes.

Começaremos a usar a função Update (). Você observará que há uma função ' enganar '. Nós usamos isso em desenvolvimento para testar a sequência de inicialização e redefinição do Rocket. Ele não funcionará na experiência de vários usuários. Espero que, no momento em que você internalizar o seguinte inprocedimento, você possa fazê-lo funcionar. Depois de verificarmos para ver se devemos enganar, verificamos se o player local é imersos. Queremos nos concentrar em como descobrimos que estamos no objetivo. Dentro da verificação if (imersos), há uma chamada para CheckGoal ocultando por trás do **EnableCollaboration** bool. Isso corresponde à caixa de seleção selecionada ao concluir as etapas deste capítulo. Dentro de EnableCollaboration, vemos uma chamada para CheckGoal ().

CheckGoal faz algumas matemáticas para ver se estamos mais ou menos em pé no painel. Quando estamos, Depuramos. log "chegou ao objetivo" e, em seguida, chamamos ' SendAtGoalMessage () '. Em SendAtGoalMessage, chamamos playerController. SendAtGoal. Para economizar algum tempo, aqui está o código:

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

Observe que SendAtGoalMessage chama CmdSendAtGoal, que chama levelstate. SetGoalIndex, que está de volta em LevelControl.cs. À primeira vista, isso parece estranho. Por que não apenas chamar SetGoalIndex em vez desse roteamento estranho por meio do controlador do jogador? O motivo é que estamos em conformidade com o modelo de dados que o UNET usa para manter os dados sincronizados. Para evitar trapaceando e ultrapaginação, o UNET requer que cada objeto tenha um usuário que tenha autoridade para alterar as variáveis sincronizadas. Além disso, somente o host (o usuário que iniciou a sessão) pode alterar os dados diretamente. Os usuários que não são o host, mas têm autoridade, precisam enviar um ' Command ' para o host que alterará a variável. Por padrão, o host tem autoridade sobre todos os objetos, exceto pelo objeto gerado para representar o usuário. Em nosso caso, esse objeto tem o script playercontroller. Há uma maneira de solicitar autoridade para um objeto e, em seguida, fazer alterações, mas optamos por aproveitar o fato de que o controlador do Player tem comandos Self Authority e Route por meio do controlador do jogador.

Dito outra maneira, quando nos encontramos em nossa meta, o jogador precisa dizer ao host, e o host informará a todos os outros.

De volta ao LevelControl.cs, consulte SetGoalIndex. Aqui, estamos definindo o valor de um valor em uma synclist (AtGoal). Lembre-se de que estamos no contexto do host enquanto fazemos isso. Semelhante a um comando, um RPC é algo que o host pode emitir e fará com que todos os clientes executem algum código. Aqui, chamamos ' RpcCheckAllGoals '. Cada cliente verifica individualmente se todos os três AtGoals estão definidos e, nesse caso, inicia o Rocket.

### <a name="enjoy-your-progress"></a>Aproveite seu progresso

Criando no capítulo anterior, iniciaremos a sessão como antes. Desta vez, à medida que os usuários no headset de imersão chegarem à "porta" em seu caminho, uma dica de ferramenta aparecerá para que apenas os usuários do HoloLens possam ver. Os usuários do HoloLens são responsáveis por comunicar essa pista aos usuários no headset de imersão. O Rocket será iniciado em espaço depois que cada avatar tiver passado em seu painel marrom correspondente dentro do vulcão. A cena será redefinida após 60 segundos para que você possa fazer isso novamente.

## <a name="see-also"></a>Consulte também
* [Entrada do MR 213: controladores de movimentos](mixed-reality-213.md)

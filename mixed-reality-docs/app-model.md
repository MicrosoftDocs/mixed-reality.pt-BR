---
title: Modelo de aplicativo
description: Realidade mista do Windows usa o modelo de aplicativo fornecido pela plataforma Universal do Windows, um modelo e o ambiente para aplicativos modernos do Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, o modelo de aplicativo, o ciclo de vida, suspender, retomar, lado a lado, exibições e contratos
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590538"
---
# <a name="app-model"></a>Modelo de aplicativo

Realidade mista do Windows usa o modelo de aplicativo fornecido pelo [plataforma Universal do Windows](https://docs.microsoft.com/windows/uwp/get-started/) (UWP), um modelo de ambiente e para aplicativos modernos do Windows. O modelo de aplicativo UWP define como os aplicativos são instalados, atualizados, com controle de versão e removido com segurança e completamente. Ele controla o ciclo de vida do aplicativo como aplicativos executarem, suspender e encerrariam - e como eles podem preservar o estado. Ele também aborda a integração e a interação com o sistema operacional, arquivos e outros aplicativos.

![Aplicativos 2D organizados em que o Windows Mixed Reality inicial em uma área de café da manhã](images/20160112-055908-hololens-500px.jpg)<br>
*Aplicativos com uma exibição 2D organizados em que o Windows Mixed Reality inicial*

## <a name="app-lifecycle"></a>Ciclo de vida do app

O ciclo de vida de um aplicativo de realidade misturada envolve conceitos de aplicativo padrão, como posicionamento, inicialização, encerramento e remoção.

### <a name="placement-is-launch"></a>O posicionamento é inicialização

Cada aplicativo é iniciado na realidade mista, colocando um bloco de aplicativo (apenas um [bloco secundário do Windows](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) na [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md). Esses blocos de aplicativos no posicionamento, serão iniciado executando o aplicativo. Esses blocos de aplicativo persistir e permanecer no local em que são colocados, atuando como iniciadores para a qualquer momento você desejam voltar para o aplicativo.

![Posicionamento coloca um bloco secundário do mundo](images/slide1-600px.png)<br>
*Posicionamento coloca um bloco secundário do mundo*

Assim que o posicionamento é concluída (a menos que o posicionamento foi iniciado por um [um aplicativo para](app-model.md#protocols) Iniciar), o aplicativo começa a inicializar. Realidade mista do Windows pode executar um número limitado de aplicativos ao mesmo tempo. Assim que você colocar e inicia um aplicativo, outros aplicativos do Active Directory podem suspender, deixando uma captura de tela do estado da última do aplicativo em seu bloco de aplicativo sempre que você o colocou. Ver [ciclo de vida do aplicativo de UWP do Windows 10](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) para obter mais informações sobre o tratamento de currículo e outros eventos de ciclo de vida do aplicativo.

![Depois de colocar um bloco, o aplicativo começa a ser executado](images/slide2-500px.png) ![diagrama de estado do aplicativo em execução, suspenso ou não está em execução](images/ic576232-500px.png)<br>
*À esquerda: depois de colocar um bloco, o aplicativo começa a ser executado. Da direita: diagrama de estado para o aplicativo em execução, suspenso ou não está em execução.*

### <a name="remove-is-closeterminate-process"></a>Remover é fechar/encerrar processo

Quando você remove um bloco do aplicativo inserido do mundo, isso fecha os processos subjacentes. Isso pode ser útil para garantir que seu aplicativo é encerrado ou reiniciar um aplicativo problemático.

### <a name="app-suspensiontermination"></a>Suspensão de aplicativo/encerramento

No [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md), o usuário é capaz de criar vários pontos de entrada para um aplicativo. Eles fazem isso iniciar seu aplicativo no menu Iniciar e colocando o bloco do aplicativo do mundo. Cada bloco de aplicativo se comporta como um ponto de entrada diferentes e tem uma instância separada do bloco no sistema. Uma consulta para [SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) resultará em um **SecondaryTile** para cada instância do aplicativo.

Quando um aplicativo UWP suspende, uma captura de tela é obtida do estado atual.

![Capturas de tela são mostradas para aplicativos suspensos](images/slide9-800px.png)<br>
*Capturas de tela são mostradas para aplicativos suspensos*

Uma das principais diferenças de outros shells do Windows 10 é como o aplicativo é informado de uma ativação de instância de aplicativo por meio de [CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) e [CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) eventos.

|  Cenário |  Retomando  |  Ativado | 
|----------|----------|----------|
|  Iniciar nova instância do aplicativo no menu Iniciar  |   |  **Ativado** com um novo [TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Inicie a segunda instância do aplicativo no menu Iniciar  |   |  **Ativado** com um novo **TileId** | 
|  Selecione a instância do aplicativo que não está ativo no momento  |   |  **Ativado** com o **TileId** associado à instância | 
|  Selecione um aplicativo diferente, e em seguida, selecione a instância anteriormente ativa  |  **Retomando** gerado  |  | 
|  Selecione um aplicativo diferente, em seguida, selecione a instância que estava inativa anteriormente  |  **Retomando** gerado  |  Em seguida **Activated** com o **TileId** associado à instância | 

### <a name="extended-execution"></a>Execução estendida

Às vezes, seu aplicativo precisa para continuar fazendo o trabalho em segundo plano ou a reprodução de áudio. [Tarefas em segundo plano](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) estão disponíveis em HoloLens.

![Aplicativos podem ser executados em segundo plano](images/slide10-800px.png)<br>
*Aplicativos podem ser executados em segundo plano*

## <a name="app-views"></a>Modos de exibição do aplicativo

Quando seu aplicativo é ativado, você pode escolher qual tipo de exibição você deseja exibir. Para um aplicativo **CoreApplication**, sempre há um primário [modo de exibição do aplicativo](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) e qualquer número de ainda mais as exibições de aplicativo que deseja criar. Na área de trabalho, você pode pensar um modo de exibição do aplicativo como uma janela. Nossos modelos de aplicativos de realidade misturada criam um projeto do Unity em que é o modo de exibição do aplicativo primário [imersivos](app-views.md). 

Seu aplicativo pode criar uma exibição de aplicativo 2D adicionais usando a tecnologia como o XAML, para usar recursos do Windows 10 como compra no aplicativo. Se seu aplicativo é iniciado como um aplicativo UWP para outros dispositivos Windows 10, o modo de exibição primário é 2D, mas você pode se "acender" na realidade mista, adicionando uma exibição de aplicativo adicionais envolvente para mostrar uma experiência volumetrically. Imagine criar um aplicativo de Visualizador de fotos no XAML em que o botão de apresentação de slides alternado para um modo de exibição do aplicativo imersão que salvei fotos do aplicativo entre o mundo e superfícies.

![O aplicativo em execução pode ter um modo de exibição 2D ou uma imersão](images/slide3-800px.png)<br>
*O aplicativo em execução pode ter um modo de exibição 2D ou uma imersão*

### <a name="creating-an-immersive-view"></a>Criação de uma exibição de imersão

Aplicativos de realidade misturada são aqueles que criam uma exibição imersiva, que é obtida com o [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) tipo.

Um aplicativo que é puramente imersivo sempre deve criar uma exibição de imersão na inicialização, mesmo se iniciado a partir da área de trabalho. Exibições imersivas sempre mostram headset, independentemente de onde foram criadas. Ativar um modo de exibição de imersão exibir o Portal de realidade mista e orientar o usuário para colocar em sua fone de ouvido.

Um aplicativo que inicia com uma exibição 2D no monitor da área de trabalho pode criar uma exibição de imersão secundária para mostrar o conteúdo no fone de ouvido. Um exemplo disso é uma janela de borda 2D no monitor exibindo um vídeo de 360 graus no fone de ouvido.

![Aplicativos em execução no modo imersivo são o único visível](images/slide4-800px.png)<br>
*Um aplicativo em execução em uma exibição de imersão é a única visível*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Modo de exibição 2D no Windows Mixed Reality inicial

Algo diferente de uma exibição de imersão é renderizado como uma exibição 2D no seu mundo.

Um aplicativo pode ter modos de exibição 2D no monitor da área de trabalho e o Headset. Observe que uma nova exibição 2D será colocada no mesmo shell como o modo de exibição que o criou, no monitor ou o Headset. Não é possível no momento para um aplicativo ou um usuário para mover uma exibição 2D entre a página inicial de realidade mista e o monitor.

![Aplicativos em execução no modo de exibição 2D compartilham o espaço do mundo misto com outros aplicativos](images/slide5-800px.png)<br>
*Aplicativos em execução em uma exibição 2D compartilham o espaço com outros aplicativos*

### <a name="placement-of-additional-app-tiles"></a>Posicionamento de blocos de aplicativos adicionais

Você pode colocar que vários aplicativos com um 2D exibir no seu mundo desejar com o [APIs do bloco secundário](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Esses blocos "fixados" serão exibido como telas de abertura que os usuários devem colocar e, em seguida, podem usar posteriormente para iniciar seu aplicativo. Realidade mista do Windows não suporta no momento, qualquer conteúdo 2D do bloco de renderização como blocos dinâmicos.

![Os aplicativos podem ter vários posicionamentos usando blocos secundários](images/slide6-800px.png)<br>
*Os aplicativos podem ter vários posicionamentos usando blocos secundários*

### <a name="switching-views"></a>Alternar entre as exibições

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Alternar do modo de exibição XAML 2D para a exibição de imersão

Se o aplicativo usa XAML e, em seguida, o XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) controlará a primeira exibição do aplicativo. O aplicativo precisará alternar para o modo imersivo antes de ativar o **CoreWindow**, para garantir que o aplicativo é iniciado diretamente na experiência imersiva.

Use [CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) e [ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) para facilitar a exibição ativa.

> [!NOTE]
>* Não especifique a [ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) sinalizador como **SwitchAsync** quando alternar do modo de exibição XAML para o modo de exibição de imersão ou o Tablet que iniciou o aplicativo será removido do mundo.
>* **SwitchAsync** deve ser chamado usando o [Dispatcher](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) associado com o modo de exibição que você está ativando na.
>* Você precisará **SwitchAsync** volta para o modo de exibição XAML, se você precisar iniciar um teclado virtual ou deseja ativar outro aplicativo.

![Aplicativos podem alternar entre modos de exibição 2D e imersivo](images/slide7-600px.png) ![quando um aplicativo entra em um modo de exibição imersivo, desaparecerem mundo misto e outros aplicativos](images/slide8-600px.png)<br>
*À esquerda: aplicativos podem alternar entre exibições 2D e envolventes. Direita: quando um aplicativo entra em um modo de exibição imersivo, os aplicativos do Windows Mixed Reality domésticos e outros desaparecem.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Alternar do modo de exibição imersivo para um modo de exibição XAML de teclado

Uma razão comum para back bidirecional alternar entre modos de exibição está exibindo um teclado em um aplicativo de realidade misturada. O shell só é capaz de exibir o teclado de sistema se o aplicativo está mostrando uma exibição 2D. Se o aplicativo precisar obter entrada de texto, ele pode fornecer uma exibição personalizada de XAML com um campo de entrada de texto, alterne para ele e, em seguida, alterne novamente depois que a entrada for concluída.

Como na seção anterior, você pode usar **ApplicationViewSwitcher.SwitchAsync** para transição de volta para um modo de exibição XAML de seu modo de exibição envolvente.

## <a name="app-size"></a>Tamanho do aplicativo

Modos de exibição 2D app sempre aparecem em uma ficha virtual fixa. Isso faz com que todas as exibições 2D mostram a mesma quantidade exata de conteúdo. Aqui estão alguns detalhes adicionais sobre o tamanho da exibição 2D do seu aplicativo:
* A taxa de proporção do aplicativo é preservada durante o redimensionamento.
* Aplicativo [fator de escala e resolução](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) não são alteradas por redimensionamento.
* Aplicativos não são capazes de consultar o tamanho real do mundo.

![Aplicativos 2D aparecem com tamanhos de janela fixo](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Aplicativos com uma exibição 2D aparecem com tamanhos de janela fixo*

## <a name="app-tiles"></a>Blocos de aplicativos

No menu Iniciar usa o pequeno bloco padrão e o bloco médio para pins e o **todos os aplicativos** lista na realidade mista. 

![O menu Iniciar de realidade mista do Windows](images/start-500px.png)<br>
*O menu Iniciar de realidade mista do Windows*

## <a name="app-to-app-interactions"></a>Aplicativo às interações do aplicativo

Conforme você cria aplicativos, você tem acesso para os mecanismos de comunicação de um aplicativo para avançados disponíveis no Windows 10. Muitas das novas APIs de protocolo e registros de arquivo funcionam perfeitamente em HoloLens para habilitar a comunicação e iniciar o aplicativo. 

Observe que para fones de ouvido da área de trabalho, o aplicativo associado com uma extensão de arquivo fornecido ou protocolo pode ser um aplicativo Win32 que só pode aparecer no monitor da área de trabalho ou em slate da área de trabalho.

### <a name="protocols"></a>Protocolos

HoloLens dá suporte a um aplicativo para iniciar por meio de [Windows.System.Launcher APIs](https://docs.microsoft.com/uwp/api/Windows.System.Launcher).

Há algumas coisas a considerar ao iniciar outro aplicativo:

* Ao fazer um lançamento não modal, tais como [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), o usuário deve colocar o aplicativo antes de interagir com ele.

* Ao realizar uma inicialização modal, como por meio [LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), o aplicativo modal é colocado na parte superior da janela.

* Realidade mista do Windows não pode sobrepor aplicativos com base em modos de exibição exclusivos. Para mostrar o aplicativo iniciado, o Windows leva o usuário voltar para o mundo para exibir o aplicativo.

### <a name="file-pickers"></a>Seletor de arquivo

HoloLens dá suporte a ambos [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) e [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) contratos. No entanto, nenhum aplicativo vem pré-instalado que atenda os contratos de seletor de arquivo. Esses aplicativos - por exemplo, OneDrive - podem ser instalados da Microsoft Store.

Se você tiver mais de um aplicativo de seletor de arquivo instalado, você não verá qualquer Desambiguidade da interface do usuário para a escolha de qual aplicativo sejam abertos; em vez disso, o seletor de arquivos primeiro instalado será escolhido. Ao salvar um arquivo, o nome do arquivo é gerado que inclui o carimbo de hora. Isso não pode ser alterado pelo usuário.

Por padrão, as extensões a seguir têm suporte localmente:

|  Aplicativo  |  Extensões | 
|----------|----------|
|  Fotos  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>{1&gt;{2&gt;contratos e extensões de realidade mista do Windows

{1&gt;{2&gt;contratos e pontos de extensão permitem que você registre seu aplicativo para tirar proveito dos recursos mais profundos do sistema operacional, como tratamento de uma extensão de arquivo ou usando as tarefas em segundo plano. Esta é uma lista dos pontos de extensão no HoloLens e contratos compatíveis e sem suportados.

|  Contrato ou extensão  |  Suporte? | 
|----------|----------|
| [Provedor de imagem da conta (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | Sem Suporte | 
| [Alarme](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | Sem Suporte | 
| [Serviço de aplicativo](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | Com suporte, mas não totalmente funcional | 
| [Provedor de compromissos](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | Sem Suporte | 
| [Reprodução automática (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | Sem Suporte | 
| [Tarefas em segundo plano (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | Suporte parcial (nem todos os disparadores de trabalho) | 
| [Tarefa de atualização (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | Com suporte | 
| [Contrato do atualizador de arquivo armazenado em cache](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | Com suporte | 
| [Configurações da câmera (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | Sem Suporte | 
| [Protocolo de discagem](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | Sem Suporte | 
| [Ativação de arquivo (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | Com suporte | 
| [Contrato do seletor de abertura de arquivo](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | Com suporte | 
| [Contrato do seletor de salvamento de arquivo](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | Com suporte | 
| [Chamada de tela de bloqueio](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | Sem Suporte | 
| [Reprodução de mídia](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | Sem Suporte | 
| [Reproduzir em contrato](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | Sem Suporte | 
| [Tarefa de configuração pré-instalada](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | Sem Suporte | 
| [Imprimir o fluxo de trabalho 3D](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | Com suporte | 
| [Configurações da tarefa de impressão (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | Sem Suporte | 
| [Ativação de URI (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | Com suporte | 
| [Lançamento restrito](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | Sem Suporte | 
| [Contrato de pesquisa](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | Sem Suporte | 
| [Contrato de configurações](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | Sem Suporte | 
| [Contrato de compartilhamento](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | Sem Suporte | 
| [SSL/certificates (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | Com suporte | 
| [Provedor de conta na Web](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | Com suporte | 

## <a name="app-file-storage"></a>Armazenamento de arquivos do aplicativo

Todo o armazenamento é por meio de [namespace Windows Storage](https://docs.microsoft.com/uwp/api/Windows.Storage). Consulte a documentação a seguir para obter mais detalhes. HoloLens não oferece suporte a sincronização/roaming de armazenamento do aplicativo.

* [Arquivos, pastas e bibliotecas](https://docs.microsoft.com/windows/uwp/files/index)
* [Armazene e recupere configurações e outros dados de aplicativo](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Pastas conhecidas

Ver [KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) para os detalhes completos para aplicativos UWP.

<table>
<tr>
<th> Propriedade</th><th> Com suporte no HoloLens</th><th> Com suporte no fones imersivos em exposição</th><th> Descrição</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta aplicativo captura.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta de câmera.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a biblioteca de documentos. A biblioteca de documentos não se destina para uso geral.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a biblioteca de música.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta de objetos 3D.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a biblioteca de imagens.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Listas de reprodução</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta de listas de reprodução.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta fotos salvas.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a biblioteca de vídeos.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtém a pasta grupo doméstico.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtém a pasta de mídia em dispositivos de servidor (Digital vivendo Network Alliance (DLNA)).</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtém a pasta de chamadas gravadas.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtém a pasta de dispositivos removíveis.</td>
</tr>
</table>

## <a name="app-package"></a>Pacote do aplicativo

Com o Windows 10 você não precisa mais direcionar um sistema operacional, mas em vez disso [seu aplicativo para um ou mais famílias de dispositivos de destino](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families). Uma família de dispositivos identifica as APIs, as características do sistema e os comportamentos esperados entre dispositivos na família de dispositivos. Ele também determina o conjunto de dispositivos nos quais seu aplicativo pode ser instalado do [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Para direcionar headsets da área de trabalho e HoloLens, direcionar seu aplicativo para o **universal** família do dispositivo.
* Para direcionar os fones de ouvido apenas da área de trabalho, direcionar seu aplicativo para o **Windows.Desktop** família do dispositivo.
* Para direcionar apenas HoloLens, direcionar seu aplicativo para o **Windows.Holographic** família do dispositivo.

## <a name="see-also"></a>Consulte também

* [Modos de exibição do aplicativo](app-views.md)
* [Atualizando aplicativos da UWP 2D para realidade misturada](building-2d-apps.md)
* [Diretrizes de design de iniciador do aplicativo 3D](3d-app-launcher-design-guidance.md)
* [Implementando os inicializadores de aplicativos 3D](implementing-3d-app-launchers.md)

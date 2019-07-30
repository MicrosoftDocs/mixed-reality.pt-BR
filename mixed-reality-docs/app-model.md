---
title: Modelo de aplicativo
description: O Windows Mixed Reality usa o modelo de aplicativo fornecido pelo Plataforma Universal do Windows, um modelo e um ambiente para aplicativos modernos do Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, modelo de aplicativo, ciclo de vida, suspensão, retomada, bloco, exibições, contratos
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517296"
---
# <a name="app-model"></a>Modelo de aplicativo

O Windows Mixed Reality usa o modelo de aplicativo fornecido pelo [plataforma universal do Windows](https://docs.microsoft.com/windows/uwp/get-started/) (UWP), um modelo e um ambiente para aplicativos modernos do Windows. O modelo de aplicativo UWP define como os aplicativos são instalados, atualizados, com controle de versão e removidos de forma segura e completa. Ele governa o ciclo de vida do aplicativo-como os aplicativos são executados, suspensos e encerrados e como eles podem preservar o estado. Ele também aborda a integração e a interação com o sistema operacional, arquivos e outros aplicativos.

![aplicativos 2D organizados no Windows Mixed Reality Home em uma área de café](images/20160112-055908-hololens-500px.jpg)<br>
*Aplicativos com uma exibição 2D organizada na página inicial do Windows Mixed Reality*

## <a name="app-lifecycle"></a>Ciclo de vida do app

O ciclo de vida de um aplicativo de realidade misturada envolve conceitos de aplicativos padrão, como posicionamento, inicialização, rescisão e remoção.

### <a name="placement-is-launch"></a>O posicionamento é iniciado

Cada aplicativo é iniciado em realidade misturada colocando um bloco de aplicativo (apenas um [bloco secundário do Windows](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) na [página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md). Esses blocos de aplicativo, no posicionamento, começarão a executar o aplicativo. Esses blocos de aplicativo persistem e permanecem no local onde eles são colocados, agindo como iniciadores para sempre que você quiser voltar ao aplicativo.

![O posicionamento coloca um bloco secundário no mundo](images/slide1-600px.png)<br>
*O posicionamento coloca um bloco secundário no mundo*

Assim que o posicionamento for concluído (a menos que o posicionamento seja iniciado por um [aplicativo para](app-model.md#protocols) inicialização do aplicativo), o aplicativo começará a ser iniciado. A realidade mista do Windows pode executar um número limitado de aplicativos ao mesmo tempo. Assim que você coloca e inicia um aplicativo, outros aplicativos ativos podem ser suspensos, deixando uma captura de tela do último estado do aplicativo no bloco do aplicativo onde quer que você o colocou. Consulte [ciclo de vida do aplicativo UWP do Windows 10](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) para obter mais informações sobre como lidar com currículo e outros eventos do ciclo de vida do aplicativo.

![Depois de colocar um bloco, o aplicativo inicia](images/slide2-500px.png) a execução ![do diagrama de estado para o aplicativo em execução, suspenso ou não em execução](images/ic576232-500px.png)<br>
*Esquerda: depois de colocar um bloco, o aplicativo começa a ser executado. Direita: diagrama de estado para o aplicativo em execução, suspenso ou não em execução.*

### <a name="remove-is-closeterminate-process"></a>Remover é um processo de fechamento/encerramento

Quando você remove um bloco do aplicativo colocado do mundo, isso fecha os processos subjacentes. Isso pode ser útil para garantir que seu aplicativo seja encerrado ou reiniciando um aplicativo problemático.

### <a name="app-suspensiontermination"></a>Suspensão/encerramento do aplicativo

Na [página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md), o usuário é capaz de criar vários pontos de entrada para um aplicativo. Eles fazem isso iniciando seu aplicativo no menu iniciar e colocando o bloco do aplicativo no mundo. Cada bloco de aplicativo se comporta como um ponto de entrada diferente e tem uma instância de bloco separada no sistema. Uma consulta para [SecondaryTile. FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) resultará em um **SecondaryTile** para cada instância do aplicativo.

Quando um aplicativo UWP é suspenso, uma captura de tela é tirada do estado atual.

![Capturas de tela são mostradas para aplicativos suspensos](images/slide9-800px.png)<br>
*Capturas de tela são mostradas para aplicativos suspensos*

Uma diferença importante de outros shells do Windows 10 é como o aplicativo é informado de uma ativação de instância de aplicativo por meio dos eventos [CoreApplication. retomar](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) e [CoreWindow. Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) .

|  Cenário |  Retomando  |  Ativado | 
|----------|----------|----------|
|  Iniciar nova instância do aplicativo no menu iniciar  |   |  **Ativado** com uma nova [tileid](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Iniciar a segunda instância do aplicativo no menu iniciar  |   |  **Ativado** com uma nova **tileid** | 
|  Selecione a instância do aplicativo que não está ativa no momento  |   |  **Ativado** com o **tileid** associado à instância | 
|  Selecione um aplicativo diferente e, em seguida, selecione a instância ativa anteriormente  |  Retomando o gerado  |  | 
|  Selecione um aplicativo diferente e, em seguida, selecione a instância que estava inativa anteriormente  |  Retomando o gerado  |  Em seguida, **ativado** com o **tileid** associado à instância | 

### <a name="extended-execution"></a>Execução estendida

Às vezes, seu aplicativo precisa continuar a trabalhar em segundo plano ou tocar áudio. [As tarefas em segundo plano](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) estão disponíveis no HoloLens.

![Os aplicativos podem ser executados em segundo plano](images/slide10-800px.png)<br>
*Os aplicativos podem ser executados em segundo plano*

## <a name="app-views"></a>Modos de exibição do aplicativo

Quando o aplicativo é ativado, você pode escolher o tipo de exibição que deseja exibir. Para o **CoreApplication**de um aplicativo, sempre há uma [exibição de aplicativo](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) primário e qualquer número de exibições de aplicativo adicionais que você gostaria de criar. Na área de trabalho, você pode considerar uma exibição de aplicativo como uma janela. Nossos modelos de aplicativos de realidade misturada criam um projeto do Unity em que a exibição do aplicativo primário é [imersiva](app-views.md). 

Seu aplicativo pode criar uma exibição de aplicativo 2D adicional usando tecnologia como XAML, para usar recursos do Windows 10, como compra no aplicativo. Se seu aplicativo foi iniciado como um aplicativo UWP para outros dispositivos Windows 10, seu modo de exibição principal é 2D, mas você poderia "se acender" na realidade misturada adicionando uma exibição de aplicativo adicional que seja de imersão para mostrar uma experiência volumetrically. Imagine criar um aplicativo de visualizador de fotos em XAML em que o botão de apresentação de slides mudou para uma exibição de aplicativo imersiva que visitou fotos do aplicativo em todo o mundo e superfícies.

![O aplicativo em execução pode ter uma exibição 2D ou uma exibição imersiva](images/slide3-800px.png)<br>
*O aplicativo em execução pode ter uma exibição 2D ou uma exibição imersiva*

### <a name="creating-an-immersive-view"></a>Criando uma exibição de imersão

Os aplicativos de realidade misturada são aqueles que criam uma exibição de imersão, que é obtida com o tipo [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) .

Um aplicativo que é puramente envolvente sempre deve criar uma exibição de imersão na inicialização, mesmo que seja iniciado na área de trabalho. Exibições de imersão sempre aparecem no headset, independentemente de onde foram criadas. Ativar uma exibição de imersão exibirá o portal de realidade misturada e orientará o usuário a colocar em seu headset.

Um aplicativo que começa com uma exibição 2D no monitor da área de trabalho pode criar uma exibição imersiva secundária para mostrar o conteúdo no headset. Um exemplo disso é uma janela de borda 2D no monitor que exibe um vídeo de 360 graus no headset.

![Os aplicativos em execução na exibição imersiva são os únicos visíveis](images/slide4-800px.png)<br>
*Um aplicativo em execução em uma exibição imersiva é o único visível*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>exibição 2D na página inicial do Windows Mixed Reality

Qualquer coisa que não seja uma exibição imersiva é renderizada como uma exibição 2D em seu mundo.

Um aplicativo pode ter exibições 2D no monitor da área de trabalho e no headset. Observe que uma nova exibição 2D será colocada no mesmo shell que a exibição que a criou, seja no monitor ou no headset. No momento, não é possível que um aplicativo ou um usuário mova uma exibição 2D entre o início da realidade misturada e o monitor.

![Aplicativos em execução no modo de exibição 2D compartilham o espaço no mundo misto com outros aplicativos](images/slide5-800px.png)<br>
*Aplicativos em execução em uma exibição 2D compartilham o espaço com outros aplicativos*

### <a name="placement-of-additional-app-tiles"></a>Posicionamento de blocos de aplicativo adicionais

Você pode colocar tantos aplicativos com uma exibição 2D em seu mundo quanto desejar com as [APIs de bloco secundárias](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Esses blocos "fixados" aparecerão como telas de abertura que os usuários devem posicionar e, posteriormente, poderão usar para iniciar seu aplicativo. Atualmente, a realidade mista do Windows não dá suporte à renderização de qualquer conteúdo de bloco 2D como blocos dinâmicos.

![Os aplicativos podem ter vários posicionamentos usando blocos secundários](images/slide6-800px.png)<br>
*Os aplicativos podem ter vários posicionamentos usando blocos secundários*

### <a name="switching-views"></a>Alternando exibições

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Alternando da exibição do XAML 2D para a exibição de imersão

Se o aplicativo usar XAML, o XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) controlará a primeira exibição do aplicativo. O aplicativo precisará alternar para a exibição imersiva antes de ativar o **CoreWindow**, para garantir que o aplicativo seja iniciado diretamente na experiência de imersão.

Use [CoreApplication. CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) e [ApplicationViewSwitcher. SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) para torná-lo o modo de exibição ativo.

> [!NOTE]
>* Não especifique o sinalizador [ApplicationViewSwitchingOptions. ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) para **SwitchAsync** ao alternar da exibição XAML para a exibição imersiva, ou o Slate que iniciou o aplicativo será removido do mundo.
>* **SwitchAsync** deve ser chamado usando o [Dispatcher](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) associado ao modo de exibição que você está alternando.
>* Você precisará **SwitchAsync** de volta ao modo de exibição XAML se precisar iniciar um teclado virtual ou desejar ativar outro aplicativo.

![Os aplicativos podem alternar entre exibições 2D e](images/slide7-600px.png) exibições ![de imersão quando um aplicativo entra em uma exibição imersiva, o mundo misto e outros aplicativos desaparecem](images/slide8-600px.png)<br>
*À esquerda: os aplicativos podem alternar entre exibição 2D e exibição de imersão. Certo: quando um aplicativo entra em uma exibição de imersão, o Windows Mixed Reality Home e outros aplicativos desaparecem.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Alternando da exibição de imersão de volta para um modo de exibição de XAML do teclado

Um motivo comum para alternar entre modos de exibição entre exibições é exibir um teclado em um aplicativo de realidade misturada. O shell só poderá exibir o teclado do sistema se o aplicativo estiver mostrando uma exibição 2D. Se o aplicativo precisar obter entrada de texto, ele poderá fornecer uma exibição XAML personalizada com um campo de entrada de texto, alternar para ele e, em seguida, voltar depois que a entrada for concluída.

Como na seção anterior, você pode usar **ApplicationViewSwitcher. SwitchAsync** para fazer a transição de volta para uma exibição XAML de sua exibição de imersão.

## <a name="app-size"></a>Tamanho do aplicativo

exibições de aplicativo 2D sempre aparecem em um Slate virtual fixo. Isso faz com que todas as exibições 2D mostrem exatamente a mesma quantidade de conteúdo. Aqui estão alguns detalhes adicionais sobre o tamanho da exibição 2D do seu aplicativo:
* A taxa de proporção do aplicativo é preservada durante o redimensionamento.
* A [resolução](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) do aplicativo e o fator de escala não são alterados pelo redimensionamento.
* Os aplicativos não podem consultar seu tamanho real no mundo.

![aplicativos 2D aparecem com tamanhos de janela fixas](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Os aplicativos com uma exibição 2D aparecem com tamanhos de janela fixas*

## <a name="app-tiles"></a>Blocos de aplicativo

O menu iniciar usa o bloco pequeno padrão e o bloco médio para Pins e a lista **todos os aplicativos** em realidade misturada. 

![O menu Iniciar para a realidade mista do Windows](images/start-500px.png)<br>
*O menu Iniciar para a realidade mista do Windows*

## <a name="app-to-app-interactions"></a>Interações entre aplicativos

Ao criar aplicativos, você tem acesso ao aplicativo avançado para mecanismos de comunicação de aplicativo disponíveis no Windows 10. Muitas das novas APIs de protocolo e registros de arquivo funcionam perfeitamente no HoloLens para habilitar a inicialização e a comunicação do aplicativo. 

Observe que para os headsets da área de trabalho, o aplicativo associado a uma determinada extensão de arquivo ou protocolo pode ser um aplicativo Win32 que só pode aparecer no monitor da área de trabalho ou no Tablet desktop.

### <a name="protocols"></a>Protocolos

O HoloLens dá suporte ao aplicativo para iniciar o aplicativo por meio das [APIs do Windows. System. Launcher](https://docs.microsoft.com/uwp/api/Windows.System.Launcher).

Há algumas coisas a serem consideradas ao iniciar outro aplicativo:

* Ao fazer uma inicialização não modal, como [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), o usuário deve posicionar o aplicativo antes de interagir com ele.

* Ao fazer uma inicialização modal, como por meio de [LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), o aplicativo modal é colocado na parte superior da janela.

* A realidade mista do Windows não pode sobrepor aplicativos sobre exibições exclusivas. Para mostrar o aplicativo iniciado, o Windows leva o usuário de volta ao mundo para exibir o aplicativo.

### <a name="file-pickers"></a>Seletores de arquivos

O HoloLens dá suporte a contratos [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) e [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) . No entanto, nenhum aplicativo vem pré-instalado que atende aos contratos de seletor de arquivo. Esses aplicativos – OneDrive, por exemplo, podem ser instalados por meio do Microsoft Store.

Se você tiver mais de um aplicativo de seletor de arquivos instalado, não verá nenhuma interface do usuário de Desambigüidade para escolher qual aplicativo será iniciado; em vez disso, o primeiro seletor de arquivo instalado será escolhido. Ao salvar um arquivo, o nome de arquivo é gerado, o que inclui o carimbo de data/hora. Isso não pode ser alterado pelo usuário.

Por padrão, as seguintes extensões têm suporte localmente:

|  Aplicativo  |  Extensões | 
|----------|----------|
|  Fotos  |  BMP, GIF, jpg, png, AVI, MOV, MP4, WMV | 
|  Microsoft Edge  |  htm, HTML, PDF, SVG, XML | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>Contratos de aplicativo e extensões de realidade mista do Windows

Os contratos de aplicativo e os pontos de extensão permitem que você registre seu aplicativo para aproveitar os recursos mais aprofundados do sistema operacional, como o tratamento de uma extensão de arquivo ou o uso de tarefas em segundo plano. Esta é uma lista dos contratos e pontos de extensão com suporte e sem suporte no HoloLens.

|  Contrato ou extensão  |  Porta? | 
|----------|----------|
| [Provedor de imagens de conta (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | Sem Suporte | 
| [Assustador](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | Sem Suporte | 
| [Serviço de aplicativo](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | Com suporte, mas não totalmente funcional | 
| [Provedor de compromissos](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | Sem Suporte | 
| [Reprodução automática (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | Sem Suporte | 
| [Tarefas em segundo plano (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | Com suporte parcial (nem todos os gatilhos funcionam) | 
| [Atualizar tarefa (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | Com suporte | 
| [Contrato de atualizador de arquivo em cache](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | Com suporte | 
| [Configurações da câmera (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | Sem Suporte | 
| [Protocolo de discagem](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | Sem Suporte | 
| [Ativação de arquivo (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | Com suporte | 
| [Contrato do seletor de abertura de arquivo](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | Com suporte | 
| [Contrato do seletor de salvamento de arquivo](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | Com suporte | 
| [Chamada de tela de bloqueio](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | Sem Suporte | 
| [Reprodução de mídia](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | Sem Suporte | 
| [Participar do contrato](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | Sem Suporte | 
| [Tarefa de configuração pré-instalada](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | Sem Suporte | 
| [Imprimir fluxo de trabalho 3D](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | Com suporte | 
| [Configurações de tarefa de impressão (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | Sem Suporte | 
| [Ativação de URI (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | Com suporte | 
| [Inicialização restrita](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | Sem Suporte | 
| [Pesquisar contrato](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | Sem Suporte | 
| [Contrato de configurações](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | Sem Suporte | 
| [Compartilhar contrato](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | Sem Suporte | 
| [SSL/certificados (extensão)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | Com suporte | 
| [Provedor de conta da Web](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | Com suporte | 

## <a name="app-file-storage"></a>Armazenamento de arquivos do aplicativo

Todo o armazenamento é por meio do [namespace Windows. Storage](https://docs.microsoft.com/uwp/api/Windows.Storage). Consulte a documentação a seguir para obter mais detalhes. O HoloLens não dá suporte à sincronização/roaming de armazenamento de aplicativos.

* [Arquivos, pastas e bibliotecas](https://docs.microsoft.com/windows/uwp/files/index)
* [Armazene e recupere configurações e outros dados de aplicativo](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Pastas conhecidas

Consulte [KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) para obter os detalhes completos dos aplicativos UWP.

<table>
<tr>
<th> Propriedade</th><th> Com suporte no HoloLens</th><th> Com suporte em headsets de imersão</th><th> Descrição</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta capturas de aplicativo.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta de rolagem da câmera.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a biblioteca de documentos. A biblioteca de documentos não se destina ao uso geral.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a biblioteca de músicas.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta de objetos 3D.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a biblioteca de imagens.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Playlists</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta de listas de reprodução.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a pasta imagens salvas.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtém a biblioteca de vídeos.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Base</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtém a pasta do grupo doméstico.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtém a pasta do servidor de mídia (dispositivos de rede de vida digital (DLNA)).</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtém a pasta de chamadas gravadas.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtém a pasta dispositivos removíveis.</td>
</tr>
</table>

## <a name="app-package"></a>Pacote do aplicativo

Com o Windows 10, você não visa mais um sistema operacional, mas sim [direcionar seu aplicativo para uma ou mais famílias de dispositivos](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families). Uma família de dispositivos identifica as APIs, as características do sistema e os comportamentos esperados entre dispositivos na família de dispositivos. Ele também determina o conjunto de dispositivos nos quais seu aplicativo pode ser instalado do [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Para direcionar os headsets da área de trabalho e o HoloLens, direcione seu aplicativo para a família de dispositivos **Windows. universal** .
* Para direcionar apenas headsets de área de trabalho, direcione seu aplicativo para a família de dispositivos **Windows. desktop** .
* Para direcionar apenas o HoloLens, direcione seu aplicativo para a família de dispositivos **Windows. Holographic** .

## <a name="see-also"></a>Consulte também

* [Modos de exibição do aplicativo](app-views.md)
* [Como atualizar aplicativos UWP 2D para realidade misturada](building-2d-apps.md)
* [Diretrizes de projeto do inicializador de aplicativos 3D](3d-app-launcher-design-guidance.md)
* [Implementando iniciadores de aplicativos 3D](implementing-3d-app-launchers.md)

---
title: Criando um projeto do DirectX Holographic
description: Explica como criar um novo aplicativo Holographic com base no modelo de aplicativo do Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, aplicativo Holographic, novo aplicativo, aplicativo UWP, aplicativo de modelo, hologramas, novo projeto, passo a passos, download, código de exemplo
ms.openlocfilehash: 24f217021cd448f19a744696de42f580f139f76f
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387618"
---
# <a name="creating-a-holographic-directx-project"></a>Criando um projeto do DirectX Holographic

Um aplicativo Holographic que você cria para um HoloLens será um <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">aplicativo plataforma universal do Windows (UWP)</a>.  Se estiver direcionando headsets de área de trabalho mista do Windows, você pode criar um aplicativo UWP ou um aplicativo Win32.

O modelo de aplicativo do DirectX 11 Holographic UWP é muito parecido com o modelo de aplicativo do DirectX 11 UWP; Ele inclui um loop de programa (ou "loop de jogo"), uma classe **DeviceResources** para gerenciar o dispositivo e o contexto do Direct3D e uma classe de processador de conteúdo simplificada. Ele também tem um <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, assim como qualquer outro aplicativo UWP.

No entanto, o aplicativo de realidade misturada tem alguns recursos adicionais que não estão presentes em um típico aplicativo UWP do Direct3D 11. O modelo de aplicativo Holographic do Windows é capaz de:
* Manipule recursos do dispositivo Direct3D associados a câmeras holographics.
* Recupere buffers de fundo da câmera do sistema.
* Manipule a entrada do [olhar](gaze.md) e reconheça um [gesto](gestures.md)simples.
* Vá para o modo de renderização estéreo de tela inteira.

## <a name="how-do-i-get-started"></a>Como fazer começar?

Primeiro, [Instale as ferramentas](install-the-tools.md), seguindo as instruções sobre como baixar o Visual Studio 2019 e o emulador Microsoft HoloLens. Os modelos de aplicativo Holographic estão incluídos no mesmo instalador que o emulador Microsoft HoloLens. Verifique também se a opção para instalar os modelos está selecionada antes de instalar o.

Agora você está pronto para criar seu aplicativo de realidade mista do Windows DirectX 11! Observe que, para remover o conteúdo de exemplo, comente a diretiva de pré-processador **DRAW_SAMPLE_CONTENT** em *PCH. h*.

## <a name="creating-a-uwp-project"></a>Criando um projeto UWP

Depois que as [ferramentas forem instaladas](install-the-tools.md) , você poderá criar um projeto Holographic DirectX UWP.

Para criar um novo projeto:
1. Inicie o **Visual Studio**.
2. No menu **arquivo** , aponte para **novo** e selecione **projeto** no menu de contexto. A caixa de diálogo **novo projeto** é aberta.
3. Expanda **instalado** à esquerda e expanda o nó de linguagem **Visual C++**  .
4. Navegue até o nó **Windows Universal > Holographic** e selecione **aplicativo Holographic DirectX 11 (Universal Windows) (C++/WinRT)** .
   ![Captura de tela do modelo de C++projeto de aplicativo Holographic DirectX 11/WinRT UWP no Visual Studio](images/holographic-directx-app-cpp-new-project.png)<br>
   *Modelo de projeto C++de aplicativo Holographic DirectX 11/WinRT UWP no Visual Studio*
   >[!IMPORTANT]
   >Certifique-se de que o nome do modelo de projetoC++inclui "(/WinRT)".  Caso contrário, você tem uma versão mais antiga dos modelos de projeto do Holographic instalados.  Para obter os modelos de projeto mais recentes, [Instale o emulador do HoloLens mais recente](using-the-hololens-emulator.md).
5. Preencha as caixas de texto **nome** e **local** e clique ou toque em **OK**. O projeto de aplicativo Holographic é criado.
6. Para o desenvolvimento direcionado apenas para o HoloLens 2, verifique se a **versão de destino** e a **versão mínima** estão definidas como **Windows 10, versão 1903**.  Se você também estiver visando headsets de HoloLens (1ª gen) ou área de trabalho mista do Windows do desktop, poderá definir a **versão mínima** para o **Windows 10, versão 1809** , embora isso exija algumas <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">verificações adaptáveis de versão</a> em seu código ao usar o novo recursos do HoloLens 2.
   ![Captura de tela da configuração do Windows 10, versão 1903 como o destino e as versões mínimas](images/new-uwp-project.png)<br>
   *Configurando o **Windows 10, versão 1903** como o destino e as versões mínimas*
   >[!IMPORTANT]
   >Se você não vir o **Windows 10, versão 1903** como uma opção, você não tem o SDK do Windows 10 mais recente instalado.  Para que essa opção seja exibida, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">Instale a versão 10.0.18362.0 ou posterior do SDK do Windows 10</a>.

O modelo gera um projeto usando <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, uma projeção de linguagem c++ 17 das APIs de Windows Runtime que dá suporte a qualquer compilador c++ 17 compatível com padrões.  O projeto mostra como criar um cubo protegido por mundo que é colocado em dois medidores do usuário. O usuário pode [tocar em ar](gestures.md#air-tap) ou pressionar um botão no controlador para colocar o cubo em uma posição diferente especificada pelo [olhar](gaze.md)do usuário. Você pode modificar este projeto para criar qualquer aplicativo de realidade misturada.

Como alternativa, você pode criar um novo projeto usando o modelo de projeto do **Visual C#**  Holographic, que se baseia em SharpDX.  Se seu projeto C# do Holographic não foi iniciado no modelo de aplicativo Holographic do Windows, você precisará copiar o arquivo MS. fxcompile. targets de um projeto C# de modelo do Windows Mixed Reality e importá-lo em seu arquivo. csproj para compilar HLSL arquivos que você adiciona ao seu projeto.

Examine [usando o Visual Studio para implantar e depurar](using-visual-studio.md) para obter informações sobre como criar e implantar o exemplo em seu HOLOLENS, PC com dispositivo de imersão anexado ou um emulador.

O restante das instruções a seguir pressupõe que você esteja usando C++ o para criar seu aplicativo.

### <a name="uwp-app-entry-point"></a>Ponto de entrada de aplicativo UWP

Seu aplicativo Holographic UWP é iniciado na função **wWinMain** em AppView. cpp. A função **wWinMain** cria o <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> do aplicativo e inicia o <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> com ele.

De **AppView. cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

A partir desse ponto, a classe AppView lida com a interação com eventos de entrada do Windows Basic, eventos e mensagens do CoreWindow e assim por diante. Ele também criará o HolographicSpace usado pelo seu aplicativo.

## <a name="creating-a-win32-project"></a>Criando um projeto Win32

A maneira mais fácil de começar a criar um projeto Holographic do Win32 é adaptar o <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">exemplo do Win32 *BasicHologram* </a>.

Este exemplo do Win32 usa <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, uma projeção de linguagem c++ 17 das APIs de Windows Runtime que dá suporte a qualquer compilador c++ 17 compatível com padrões.  O projeto mostra como criar um cubo protegido por mundo que é colocado em dois medidores do usuário. O usuário pode pressionar um botão no controlador para colocar o cubo em uma posição diferente especificada pelo [olhar](gaze.md)do usuário. Você pode modificar este projeto para criar qualquer aplicativo de realidade misturada.

### <a name="win32-app-entry-point"></a>Ponto de entrada do aplicativo Win32

Seu aplicativo Win32 Holographic é iniciado na função **wWinMain** em AppMain. cpp. A função **wWinMain** cria o HWND do aplicativo e inicia seu loop de mensagem.

De **AppMain. cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

Desse ponto em diante, a classe AppMain lida com a interação com as mensagens básicas de janela e assim por diante. Ele também criará o HolographicSpace usado pelo seu aplicativo.

## <a name="render-holographic-content"></a>Renderizar conteúdo Holographic

A pasta de **conteúdo** do projeto contém classes para renderizar hologramas no [espaço Holographic](getting-a-holographicspace.md). O holograma padrão no modelo é um cubo de rotação que é colocado em dois medidores longe do usuário. O desenho desse cubo é implementado em **SpinningCubeRenderer. cpp**, que tem estes métodos principais:

|  Método  |  Explicação | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carrega sombreadores e cria a malha do cubo. | 
|  `PositionHologram` |  Coloca o holograma no local especificado pelo <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>fornecido. | 
|  `Update` |  Gira o cubo e define a matriz do modelo. | 
|  `Render` |  Renderiza um quadro usando o vértice e os sombreadores de pixel. | 

A  subpasta shaders contém quatro implementações de sombreador padrão:

|  Shader  |  Explicação | 
|----------|----------|
|  `GeometryShader.hlsl` |  Uma passagem que deixa a geometria não modificada. | 
|  `PixelShader.hlsl` |  Passa pelos dados de cor. Os dados de cor são interpolados e atribuídos a um pixel na etapa de rasterização. | 
|  `VertexShader.hlsl` |  Sombreador simples para fazer processamento de vértice na GPU. | 
|  `VPRTVertexShader.hlsl` |  Sombreador simples para fazer o processamento de vértice na GPU, que é otimizado para a renderização de estéreo de realidade mista do Windows. | 

`VertexShaderShared.hlsl`contém o código comum compartilhado `VertexShader.hlsl` entre `VPRTVertexShader.hlsl`e.

Os sombreadores são compilados quando o projeto é compilado e são carregados no método **SpinningCubeRenderer:: CreateDeviceDependentResources** .

## <a name="interact-with-your-holograms"></a>Interaja com os hologramas

A entrada do usuário é processada na classe **SpatialInputHandler** , que obtém uma instância de <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> e assina o evento <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> . Isso permite detectar o gesto de toque do ar e outros eventos de entrada espaciais.

## <a name="update-holographic-content"></a>Atualizar conteúdo do Holographic

O aplicativo de realidade misturada é atualizado em um loop de jogo, que por padrão  é implementado no `AppMain.cpp`método Update no. O método **Update** atualiza objetos de cena, como o cubo girando, e retorna um objeto <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> que é usado para obter matrizes de exibição e projeção atualizadas e apresentar a cadeia de troca.

O método **render** em `AppMain.cpp` usa o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> e renderiza o quadro atual para cada câmera Holographic, de acordo com o aplicativo atual e o estado de posicionamento espacial.

## <a name="see-also"></a>Consulte também
* [Como obter um HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Como renderizar no DirectX](rendering-in-directx.md)
* [Como usar o Visual Studio para implantar e depurar](using-visual-studio.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como usar o XAML com aplicativos DirectX holográficos](using-xaml-with-holographic-directx-apps.md)

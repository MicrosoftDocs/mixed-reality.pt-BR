---
title: Criando um projeto holográfico do DirectX
description: Explica como criar um novo aplicativo holográfico com base no modelo de aplicativo de realidade mista do Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, aplicativo holográfico, novo aplicativo, aplicativo UWP, modelo de aplicativo, hologramas, novo projeto, passo a passo, download, o código de exemplo
ms.openlocfilehash: a7eac9d8056fe5f7bcc442d6441f71331fa96cf6
ms.sourcegitcommit: 19c9bff21061d485821b61c9f3498daef8fa8235
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828126"
---
# <a name="creating-a-holographic-directx-project"></a>Criando um projeto holográfico do DirectX

Um aplicativo holográfico criar para um HoloLens será um <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">aplicativo de plataforma Universal do Windows (UWP)</a>.  Se o destino da área de trabalho fones de ouvido Windows Mixed Reality, você pode criar um aplicativo UWP ou um aplicativo Win32.

O modelo de aplicativo UWP holográfico do DirectX 11 é muito semelhante o modelo de aplicativo de UWP do DirectX 11; Ele inclui um programa loop (ou "loop do jogo"), uma **DeviceResources** classe para gerenciar o dispositivo Direct3D e o contexto e uma classe de renderizador simplificado de conteúdo. Ele também tem um <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, assim como qualquer outro aplicativo UWP.

O aplicativo de realidade misturada, no entanto, tem alguns recursos adicionais que não estão presentes em um aplicativo Direct3D 11 UWP típico. O modelo de aplicativo do Windows Holographic é capaz de:
* Lidar com recursos de dispositivo de Direct3D associados com câmeras holográfica.
* Recupere os buffers de fundo de câmera do sistema.
* Manipular [olhares](gaze.md) de entrada e reconhecer um simples [gesto](gestures.md).
* Entre no modo de renderização estéreo de tela inteira.

## <a name="how-do-i-get-started"></a>Como posso começar?

Primeira [instalar as ferramentas](install-the-tools.md), seguindo as instruções sobre como baixar o Visual Studio 2017 e o emulador do Microsoft HoloLens. Os modelos de aplicativo holográfica são incluídos no instalador do mesmo que o emulador do Microsoft HoloLens. Além disso, verifique se a opção para instalar os modelos é selecionada antes de instalar.

Agora você está pronto para criar seu aplicativo DirectX 11 Windows Mixed Reality! Observe que para remover o conteúdo de exemplo, comente a **DRAW_SAMPLE_CONTENT** na diretiva de pré-processador *pch*.

## <a name="creating-a-uwp-project"></a>Criar um projeto UWP

Uma vez a [as ferramentas são instaladas](install-the-tools.md) , em seguida, você pode criar um projeto UWP DirectX holográfico.

Para criar um novo projeto:
1. Inicie **Visual Studio**.
2. Dos **arquivo** , aponte para **New** e selecione **projeto** no menu de contexto. O **novo projeto** caixa de diálogo é aberta.
3. Expandir **Installed** à esquerda e expanda o **Visual C++**  nó de linguagem.
4. Navegue até a **Universal do Windows > Holographic** nó e selecione **aplicativo de 11 holográfica DirectX (Windows Universal) (C++/WinRT)**.
   ![Captura de tela do DirectX 11 holográfica C++modelo de projeto de aplicativo do WinRT UWP no Visual Studio](images/holographic-directx-app-cpp-new-project.png)<br>
   *Holográfica DirectX 11 C++modelo de projeto de aplicativo do WinRT UWP no Visual Studio*
   >[!IMPORTANT]
   >Certifique-se de que o nome do modelo de projeto inclui "(C++/WinRT)".  Caso contrário, você tem uma versão mais antiga dos modelos de projeto holográfica instalado.  Para obter os últimos modelos de projeto, [instalar o emulador mais recente do HoloLens](using-the-hololens-emulator.md).
5. Preencha a **nome** e **local** caixas de texto e clique ou toque **Okey**. O projeto de aplicativo holográfica é criado.
6. Para o desenvolvimento direcionando apenas 2 HoloLens, certifique-se de que o **versão de destino** e **versão mínima** estiver definido como **Windows 10, versão 1903**.  Se você estiver direcionando também HoloLens (1º gen) ou headsets da área de trabalho do Windows Mixed Reality, você pode definir **versão mínima** ao **Windows 10, versão 1809** em vez disso, embora isso exigirá algumas <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> verificações de versão adaptável</a> em seu código ao usar os novos recursos do HoloLens 2.
   ![Captura de tela da configuração do Windows 10, versão 1903 como as versões de destino e mínima](images/new-uwp-project.png)<br>
   *Definindo **Windows 10, versão 1903** como as versões de destino e mínima*
   >[!IMPORTANT]
   >Se você não vir **Windows 10, versão 1903** como opção, você não tiver o Windows 10 SDK mais recente instalado.  Para obter essa opção apareça, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">instalar a versão 10.0.18362.0 ou posterior do SDK do Windows 10</a>.

O modelo gera um projeto usando <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, uma projeção de c++17 linguagem C + + das APIs de tempo de execução do Windows que dá suporte a qualquer compilador que 17 compatível com os padrões C + +.  O projeto mostra como criar um cubo bloqueado pelo mundo que colocou os dois medidores do usuário. O usuário pode [-indicador e polegar](gestures.md#air-tap) ou pressionar um botão no controlador para colocar o cubo em uma posição diferente que é especificada pelo usuário [olhares](gaze.md). Você pode modificar este projeto para criar qualquer aplicativo de realidade misturada.

Como alternativa, você pode criar um novo projeto usando o **Visual C#**  modelo de projeto holográfica, que se baseia no SharpDX.  Se seu holográfica C# projeto não foi iniciado a partir do modelo de aplicativo do Windows Holographic, será necessário copiar o arquivo ms.fxcompile.targets de um Windows Mixed Reality C# projeto de modelo e import-lo no seu. csproj arquivo para compilar HLSL arquivos que você adicionar ao seu projeto.

Revisão [usando o Visual Studio para implantar e depurar](using-visual-studio.md) para obter informações sobre como criar e implantar o exemplo para o HoloLens, PC com imersivo dispositivo conectado ou um emulador.

O restante das instruções a seguir assumirá que você está usando C++ para criar seu aplicativo.

### <a name="uwp-app-entry-point"></a>Ponto de entrada do aplicativo UWP

Seu aplicativo UWP holográfico inicia na **wWinMain** função em AppView.cpp. O **wWinMain** função cria o aplicativo <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> e inicia o <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> com ele.

Partir **AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

Daí em diante, a classe AppView trata a interação com eventos de entrada básicos do Windows, eventos de CoreWindow e sistema de mensagens e assim por diante. Ele também criará o HolographicSpace usado pelo seu aplicativo.

## <a name="creating-a-win32-project"></a>Criando um projeto do Win32

A maneira mais fácil começar a compilar Win32 holográfico projeto deve se adaptar a <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 sample</a>.

Este exemplo do Win32 usa <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, uma projeção de c++17 linguagem C + + das APIs de tempo de execução do Windows que dá suporte a qualquer compilador que 17 compatível com os padrões C + +.  O projeto mostra como criar um cubo bloqueado pelo mundo que colocou os dois medidores do usuário. O usuário pode pressionar um botão no controlador para colocar o cubo em uma posição diferente que é especificada pelo usuário [olhares](gaze.md). Você pode modificar este projeto para criar qualquer aplicativo de realidade misturada.

### <a name="win32-app-entry-point"></a>Ponto de entrada do aplicativo Win32

Seu aplicativo Win32 holográfico é iniciado na **wWinMain** função em AppMain.cpp. O **wWinMain** função cria o HWND do aplicativo e começa seu loop de mensagem.

Partir **AppMain.cpp**:

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

Daí em diante, a classe AppMain trata a interação com mensagens de janela básica e assim por diante. Ele também criará o HolographicSpace usado pelo seu aplicativo.

## <a name="render-holographic-content"></a>Renderizar conteúdo holográfico

O projeto **conteúdo** pasta contém classes para hologramas de renderização na [holográfico espaço](getting-a-holographicspace.md). O holograma padrão no modelo é um cubo de rotação que colocou os dois medidores direção contrária ao usuário. Esse cubo de desenho é implementada no **SpinningCubeRenderer.cpp**, que tem esses métodos principais:

|  Método  |  Explicação | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carrega os sombreadores e cria a malha de cubo. | 
|  `PositionHologram` |  Coloca o holograma no local especificado por fornecido <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>. | 
|  `Update` |  Gira o cubo e define a matriz do modelo. | 
|  `Render` |  Renderiza um quadro usando os sombreadores de pixel e vértice. | 

O **sombreadores** subpasta contém quatro implementações de sombreador padrão:

|  Shader  |  Explicação | 
|----------|----------|
|  `GeometryShader.hlsl` |  Uma passagem que deixa a geometria sem modificações. | 
|  `PixelShader.hlsl` |  Passe os dados de cor. Os dados de cores são interpolados e atribuídos a um pixel na etapa rasterização. | 
|  `VertexShader.hlsl` |  Sombreador simples para realizar o processamento de vértice no GPU. | 
|  `VPRTVertexShader.hlsl` |  Sombreador simples para realizar o processamento de vértice no GPU, que é otimizado para a renderização de Windows Mixed Reality estéreo. | 

`VertexShaderShared.hlsl` contém o código comum compartilhado entre `VertexShader.hlsl` e `VPRTVertexShader.hlsl`.

Os sombreadores são compilados quando o projeto é compilado, e eles são carregados na **SpinningCubeRenderer::CreateDeviceDependentResources** método.

## <a name="interact-with-your-holograms"></a>Interagir com seu hologramas

Entrada do usuário é processada na **SpatialInputHandler** classe, que é um <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> da instância e assina o <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> eventos. Isso permite detectar o gesto de toque de ar e outros eventos de entrada espaciais.

## <a name="update-holographic-content"></a>Atualizar conteúdo holográfico

Suas atualizações de aplicativo de realidade mista em um loop do jogo, que, por padrão, é implementado de **atualização** método na `AppMain.cpp`. O **atualização** método atualiza os objetos de cena, como o cubo de rotação e retorna um <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> objeto que é usado para obter as matrizes de projeção e exibição atualizadas e apresentar a cadeia de troca.

O **renderizar** método na `AppMain.cpp` leva a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> e renderiza o quadro atual para cada câmera holográfica, acordo com o aplicativo atual e o estado de posicionamento espacial.

## <a name="see-also"></a>Consulte também
* [Como obter um HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Como renderizar no DirectX](rendering-in-directx.md)
* [Como usar o Visual Studio para implantar e depurar](using-visual-studio.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como usar o XAML com aplicativos DirectX holográficos](using-xaml-with-holographic-directx-apps.md)

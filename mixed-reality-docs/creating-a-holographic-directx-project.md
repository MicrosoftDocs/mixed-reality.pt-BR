---
title: Criando um projeto holográfico do DirectX
description: Explica como criar um novo aplicativo holográfico com base no modelo de aplicativo de realidade mista do Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, aplicativo holográfico, novo aplicativo, aplicativo UWP, modelo de aplicativo, hologramas, novo projeto, passo a passo, download, o código de exemplo
ms.openlocfilehash: 7d1ea0246cf823f74e68b4e67fbcfc275d081688
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591019"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="363b8-104">Criando um projeto holográfico do DirectX</span><span class="sxs-lookup"><span data-stu-id="363b8-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="363b8-105">Um aplicativo holográfico criar para um HoloLens será um <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">aplicativo de plataforma Universal do Windows (UWP)</a>.</span><span class="sxs-lookup"><span data-stu-id="363b8-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="363b8-106">Se o destino da área de trabalho fones de ouvido Windows Mixed Reality, você pode criar um aplicativo UWP ou um aplicativo Win32.</span><span class="sxs-lookup"><span data-stu-id="363b8-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="363b8-107">O modelo de aplicativo UWP holográfico do DirectX 11 é muito semelhante o modelo de aplicativo de UWP do DirectX 11; Ele inclui um programa loop (ou "loop do jogo"), uma **DeviceResources** classe para gerenciar o dispositivo Direct3D e o contexto e uma classe de renderizador simplificado de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="363b8-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="363b8-108">Ele também tem um <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, assim como qualquer outro aplicativo UWP.</span><span class="sxs-lookup"><span data-stu-id="363b8-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="363b8-109">O aplicativo de realidade misturada, no entanto, tem alguns recursos adicionais que não estão presentes em um aplicativo Direct3D 11 UWP típico.</span><span class="sxs-lookup"><span data-stu-id="363b8-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="363b8-110">O modelo de aplicativo do Windows Holographic é capaz de:</span><span class="sxs-lookup"><span data-stu-id="363b8-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="363b8-111">Lidar com recursos de dispositivo de Direct3D associados com câmeras holográfica.</span><span class="sxs-lookup"><span data-stu-id="363b8-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="363b8-112">Recupere os buffers de fundo de câmera do sistema.</span><span class="sxs-lookup"><span data-stu-id="363b8-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="363b8-113">Manipular [olhares](gaze.md) de entrada e reconhecer um simples [gesto](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="363b8-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="363b8-114">Entre no modo de renderização estéreo de tela inteira.</span><span class="sxs-lookup"><span data-stu-id="363b8-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="363b8-115">Como posso começar?</span><span class="sxs-lookup"><span data-stu-id="363b8-115">How do I get started?</span></span>

<span data-ttu-id="363b8-116">Primeira [instalar as ferramentas](install-the-tools.md), seguindo as instruções sobre como baixar o Visual Studio 2017 e o emulador do Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="363b8-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2017 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="363b8-117">Os modelos de aplicativo holográfica são incluídos no instalador do mesmo que o emulador do Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="363b8-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="363b8-118">Além disso, verifique se a opção para instalar os modelos é selecionada antes de instalar.</span><span class="sxs-lookup"><span data-stu-id="363b8-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="363b8-119">Agora você está pronto para criar seu aplicativo DirectX 11 Windows Mixed Reality!</span><span class="sxs-lookup"><span data-stu-id="363b8-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="363b8-120">Observe que para remover o conteúdo de exemplo, comente a **DRAW_SAMPLE_CONTENT** na diretiva de pré-processador *pch*.</span><span class="sxs-lookup"><span data-stu-id="363b8-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="363b8-121">Criar um projeto UWP</span><span class="sxs-lookup"><span data-stu-id="363b8-121">Creating a UWP project</span></span>

<span data-ttu-id="363b8-122">Depois que as ferramentas são instaladas, você pode criar um projeto UWP DirectX holográfico.</span><span class="sxs-lookup"><span data-stu-id="363b8-122">Once the tools are installed you can then create a holographic DirectX UWP project.</span></span> <span data-ttu-id="363b8-123">Para criar um novo projeto:</span><span class="sxs-lookup"><span data-stu-id="363b8-123">To create a new project:</span></span>
1. <span data-ttu-id="363b8-124">Inicie **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="363b8-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="363b8-125">Dos **arquivo** , aponte para **New** e selecione **projeto** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="363b8-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="363b8-126">O **novo projeto** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="363b8-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="363b8-127">Expandir **Installed** à esquerda e expanda o **Visual C++**  nó de linguagem.</span><span class="sxs-lookup"><span data-stu-id="363b8-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="363b8-128">Navegue até a **Universal do Windows > Holographic** nó e selecione **aplicativo de 11 holográfica DirectX (Windows Universal) (C++/WinRT)**.</span><span class="sxs-lookup"><span data-stu-id="363b8-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="363b8-129">Certifique-se de que o nome do modelo de projeto inclui "(C++/WinRT)".</span><span class="sxs-lookup"><span data-stu-id="363b8-129">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="363b8-130">Caso contrário, você tem uma versão mais antiga dos modelos de projeto holográfica instalado.</span><span class="sxs-lookup"><span data-stu-id="363b8-130">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="363b8-131">Para obter os últimos modelos de projeto, [instalar o emulador mais recente do HoloLens](using-the-hololens-emulator.md).</span><span class="sxs-lookup"><span data-stu-id="363b8-131">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="363b8-132">Preencha a **nome** e **local** caixas de texto e clique ou toque **Okey**.</span><span class="sxs-lookup"><span data-stu-id="363b8-132">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="363b8-133">O projeto de aplicativo holográfica é criado.</span><span class="sxs-lookup"><span data-stu-id="363b8-133">The holographic app project is created.</span></span>
6. <span data-ttu-id="363b8-134">Para o desenvolvimento direcionando apenas 2 HoloLens, certifique-se de que o **versão de destino** e **versão mínima** estiver definido como **Windows 10, versão 1903**.</span><span class="sxs-lookup"><span data-stu-id="363b8-134">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="363b8-135">Se você estiver direcionando também HoloLens (1º gen) ou headsets da área de trabalho do Windows Mixed Reality, você pode definir **versão mínima** ao **Windows 10, versão 1809** em vez disso, embora isso exigirá algumas <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> verificações de versão de adapative</a> em seu código ao usar os novos recursos do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="363b8-135">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adapative checks</a> in your code when using new features of HoloLens 2.</span></span>

<span data-ttu-id="363b8-136">![Captura de tela do modelo de projeto aplicativo holográfica no Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="363b8-136">![Screenshot of the holographic app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
<span data-ttu-id="363b8-137">*Modelo de projeto de aplicativo holográfica no Visual Studio*</span><span class="sxs-lookup"><span data-stu-id="363b8-137">*Holographic app project template in Visual Studio*</span></span>

<span data-ttu-id="363b8-138">O modelo gera um projeto usando <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, uma projeção de c++17 linguagem C + + das APIs de tempo de execução do Windows que dá suporte a qualquer compilador que 17 compatível com os padrões C + +.</span><span class="sxs-lookup"><span data-stu-id="363b8-138">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="363b8-139">O projeto mostra como criar um cubo bloqueado pelo mundo que colocou os dois medidores do usuário.</span><span class="sxs-lookup"><span data-stu-id="363b8-139">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="363b8-140">O usuário pode [-indicador e polegar](gestures.md#air-tap) ou pressionar um botão no controlador para colocar o cubo em uma posição diferente que é especificada pelo usuário [olhares](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="363b8-140">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="363b8-141">Você pode modificar este projeto para criar qualquer aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="363b8-141">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="363b8-142">Como alternativa, você pode criar um novo projeto usando o **Visual C#**  modelo de projeto holográfica, que se baseia no SharpDX.</span><span class="sxs-lookup"><span data-stu-id="363b8-142">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="363b8-143">Se seu holográfica C# projeto não foi iniciado a partir do modelo de aplicativo do Windows Holographic, será necessário copiar o arquivo ms.fxcompile.targets de um Windows Mixed Reality C# projeto de modelo e import-lo no seu. csproj arquivo para compilar HLSL arquivos que você adicionar ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="363b8-143">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="363b8-144">Revisão [usando o Visual Studio para implantar e depurar](using-visual-studio.md) para obter informações sobre como criar e implantar o exemplo para o HoloLens, PC com imersivo dispositivo conectado ou um emulador.</span><span class="sxs-lookup"><span data-stu-id="363b8-144">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="363b8-145">O restante das instruções a seguir assumirá que você está usando C++ para criar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="363b8-145">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="363b8-146">Ponto de entrada do aplicativo UWP</span><span class="sxs-lookup"><span data-stu-id="363b8-146">UWP app entry point</span></span>

<span data-ttu-id="363b8-147">Seu aplicativo UWP holográfico inicia na **wWinMain** função em AppView.cpp.</span><span class="sxs-lookup"><span data-stu-id="363b8-147">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="363b8-148">O **wWinMain** função cria o aplicativo <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> e inicia o <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> com ele.</span><span class="sxs-lookup"><span data-stu-id="363b8-148">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="363b8-149">Partir **AppView.cpp**:</span><span class="sxs-lookup"><span data-stu-id="363b8-149">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="363b8-150">Daí em diante, a classe AppView trata a interação com eventos de entrada básicos do Windows, eventos de CoreWindow e sistema de mensagens e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="363b8-150">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="363b8-151">Ele também criará o HolographicSpace usado pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="363b8-151">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="363b8-152">Criando um projeto do Win32</span><span class="sxs-lookup"><span data-stu-id="363b8-152">Creating a Win32 project</span></span>

<span data-ttu-id="363b8-153">A maneira mais fácil começar a compilar Win32 holográfico projeto deve se adaptar a <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 sample</a>.</span><span class="sxs-lookup"><span data-stu-id="363b8-153">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="363b8-154">Este exemplo do Win32 usa <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, uma projeção de c++17 linguagem C + + das APIs de tempo de execução do Windows que dá suporte a qualquer compilador que 17 compatível com os padrões C + +.</span><span class="sxs-lookup"><span data-stu-id="363b8-154">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="363b8-155">O projeto mostra como criar um cubo bloqueado pelo mundo que colocou os dois medidores do usuário.</span><span class="sxs-lookup"><span data-stu-id="363b8-155">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="363b8-156">O usuário pode pressionar um botão no controlador para colocar o cubo em uma posição diferente que é especificada pelo usuário [olhares](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="363b8-156">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="363b8-157">Você pode modificar este projeto para criar qualquer aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="363b8-157">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="363b8-158">Ponto de entrada do aplicativo Win32</span><span class="sxs-lookup"><span data-stu-id="363b8-158">Win32 app entry point</span></span>

<span data-ttu-id="363b8-159">Seu aplicativo Win32 holográfico é iniciado na **wWinMain** função em AppMain.cpp.</span><span class="sxs-lookup"><span data-stu-id="363b8-159">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="363b8-160">O **wWinMain** função cria o HWND do aplicativo e começa seu loop de mensagem.</span><span class="sxs-lookup"><span data-stu-id="363b8-160">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="363b8-161">Partir **AppMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="363b8-161">From **AppMain.cpp**:</span></span>

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

<span data-ttu-id="363b8-162">Daí em diante, a classe AppMain trata a interação com mensagens de janela básica e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="363b8-162">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="363b8-163">Ele também criará o HolographicSpace usado pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="363b8-163">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="363b8-164">Renderizar conteúdo holográfico</span><span class="sxs-lookup"><span data-stu-id="363b8-164">Render holographic content</span></span>

<span data-ttu-id="363b8-165">O projeto **conteúdo** pasta contém classes para hologramas de renderização na [holográfico espaço](getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="363b8-165">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="363b8-166">O holograma padrão no modelo é um cubo de rotação que colocou os dois medidores direção contrária ao usuário.</span><span class="sxs-lookup"><span data-stu-id="363b8-166">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="363b8-167">Esse cubo de desenho é implementada no **SpinningCubeRenderer.cpp**, que tem esses métodos principais:</span><span class="sxs-lookup"><span data-stu-id="363b8-167">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="363b8-168">Método</span><span class="sxs-lookup"><span data-stu-id="363b8-168">Method</span></span>  |  <span data-ttu-id="363b8-169">Explicação</span><span class="sxs-lookup"><span data-stu-id="363b8-169">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="363b8-170">Carrega os sombreadores e cria a malha de cubo.</span><span class="sxs-lookup"><span data-stu-id="363b8-170">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="363b8-171">Coloca o holograma no local especificado por fornecido <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span><span class="sxs-lookup"><span data-stu-id="363b8-171">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="363b8-172">Gira o cubo e define a matriz do modelo.</span><span class="sxs-lookup"><span data-stu-id="363b8-172">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="363b8-173">Renderiza um quadro usando os sombreadores de pixel e vértice.</span><span class="sxs-lookup"><span data-stu-id="363b8-173">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="363b8-174">O **sombreadores** subpasta contém quatro implementações de sombreador padrão:</span><span class="sxs-lookup"><span data-stu-id="363b8-174">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="363b8-175">Shader</span><span class="sxs-lookup"><span data-stu-id="363b8-175">Shader</span></span>  |  <span data-ttu-id="363b8-176">Explicação</span><span class="sxs-lookup"><span data-stu-id="363b8-176">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="363b8-177">Uma passagem que deixa a geometria sem modificações.</span><span class="sxs-lookup"><span data-stu-id="363b8-177">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="363b8-178">Passe os dados de cor.</span><span class="sxs-lookup"><span data-stu-id="363b8-178">Passes through the color data.</span></span> <span data-ttu-id="363b8-179">Os dados de cores são interpolados e atribuídos a um pixel na etapa rasterização.</span><span class="sxs-lookup"><span data-stu-id="363b8-179">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="363b8-180">Sombreador simples para realizar o processamento de vértice no GPU.</span><span class="sxs-lookup"><span data-stu-id="363b8-180">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="363b8-181">Sombreador simples para realizar o processamento de vértice no GPU, que é otimizado para a renderização de Windows Mixed Reality estéreo.</span><span class="sxs-lookup"><span data-stu-id="363b8-181">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="363b8-182">`VertexShaderShared.hlsl` contém o código comum compartilhado entre `VertexShader.hlsl` e `VPRTVertexShader.hlsl`.</span><span class="sxs-lookup"><span data-stu-id="363b8-182">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="363b8-183">Os sombreadores são compilados quando o projeto é compilado, e eles são carregados na **SpinningCubeRenderer::CreateDeviceDependentResources** método.</span><span class="sxs-lookup"><span data-stu-id="363b8-183">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="363b8-184">Interagir com seu hologramas</span><span class="sxs-lookup"><span data-stu-id="363b8-184">Interact with your holograms</span></span>

<span data-ttu-id="363b8-185">Entrada do usuário é processada na **SpatialInputHandler** classe, que é um <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> da instância e assina o <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> eventos.</span><span class="sxs-lookup"><span data-stu-id="363b8-185">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="363b8-186">Isso permite detectar o gesto de toque de ar e outros eventos de entrada espaciais.</span><span class="sxs-lookup"><span data-stu-id="363b8-186">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="363b8-187">Atualizar conteúdo holográfico</span><span class="sxs-lookup"><span data-stu-id="363b8-187">Update holographic content</span></span>

<span data-ttu-id="363b8-188">Suas atualizações de aplicativo de realidade mista em um loop do jogo, que, por padrão, é implementado de **atualização** método na `AppMain.cpp`.</span><span class="sxs-lookup"><span data-stu-id="363b8-188">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="363b8-189">O **atualização** método atualiza os objetos de cena, como o cubo de rotação e retorna um <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> objeto que é usado para obter as matrizes de projeção e exibição atualizadas e apresentar a cadeia de troca.</span><span class="sxs-lookup"><span data-stu-id="363b8-189">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="363b8-190">O **renderizar** método na `AppMain.cpp` leva a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> e renderiza o quadro atual para cada câmera holográfica, acordo com o aplicativo atual e o estado de posicionamento espacial.</span><span class="sxs-lookup"><span data-stu-id="363b8-190">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="363b8-191">Consulte também</span><span class="sxs-lookup"><span data-stu-id="363b8-191">See also</span></span>
* [<span data-ttu-id="363b8-192">Obtendo um HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="363b8-192">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="363b8-193"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="363b8-193"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="363b8-194">Processamento no DirectX</span><span class="sxs-lookup"><span data-stu-id="363b8-194">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="363b8-195">Usando o Visual Studio para implantar e depurar</span><span class="sxs-lookup"><span data-stu-id="363b8-195">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="363b8-196">Usando o emulador do HoloLens</span><span class="sxs-lookup"><span data-stu-id="363b8-196">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="363b8-197">Usando XAML com aplicativos de DirectX holográfico</span><span class="sxs-lookup"><span data-stu-id="363b8-197">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)

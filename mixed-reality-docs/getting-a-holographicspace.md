---
title: Obtendo um HolographicSpace
description: Explica a API do HolographicSpace, um conceito básico para a renderização Holographic e a entrada espacial.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, entrada espacial, renderização, Cadeia de permuta, quadro Holographic, loop de atualização, loop de jogo, quadro de referência, locatability, código de exemplo, passo a passos
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525440"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="b5bc0-104">Obtendo um HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="b5bc0-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="b5bc0-105">A classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> é o seu portal no mundo Holographic.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="b5bc0-106">Ele controla a renderização de imersão, fornece dados de câmera e fornece acesso a APIs de raciocínio espacial.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="b5bc0-107">Você criará um para o <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> do seu aplicativo UWP ou o HWND do seu aplicativo Win32.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="b5bc0-108">Configurar o espaço Holographic</span><span class="sxs-lookup"><span data-stu-id="b5bc0-108">Set up the holographic space</span></span>

<span data-ttu-id="b5bc0-109">Criar o objeto Holographic Space é a primeira etapa para tornar seu aplicativo Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="b5bc0-110">Os aplicativos tradicionais do Windows são renderizados para uma cadeia de permuta do Direct3D criada para a janela principal de sua exibição de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="b5bc0-111">Essa cadeia de permuta é exibida para um Slate na interface do usuário do amholographic.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="b5bc0-112">Para fazer com que seu aplicativo exiba Holographic em vez de um Tablet 2D, crie um espaço Holographic para sua janela principal em vez de uma cadeia de permuta.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="b5bc0-113">Apresentar quadros Holographic criados por esse espaço de Holographic coloca seu aplicativo no modo de renderização de tela inteira.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="b5bc0-114">Para um **aplicativo UWP** [a partir do *modelo de aplicativo Holographic DirectX 11 (universal do Windows)* ](creating-a-holographic-directx-project.md), procure esse código no  método SetWindow em AppView. cpp:</span><span class="sxs-lookup"><span data-stu-id="b5bc0-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="b5bc0-115">Para um **aplicativo Win32** a [partir do exemplo do Win32 *BasicHologram* ](creating-a-holographic-directx-project.md#creating-a-win32-project), examine o **aplicativo:: CreateWindowAndHolographicSpace** para obter um exemplo de como criar um HWND e, em seguida, convertê-lo em um HWND de imersão criando um associado <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank"> HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="b5bc0-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="b5bc0-116">Agora que você já obteve um HolographicSpace para o seu CoreWindow UWP ou o HWND do Win32, usará esse HolographicSpace para lidar com as câmeras de Holographic, criar sistemas de coordenadas e fazer Holographic renderização.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="b5bc0-117">O espaço Holographic atual é usado em vários locais no modelo do DirectX:</span><span class="sxs-lookup"><span data-stu-id="b5bc0-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="b5bc0-118">A classe **DeviceResources** precisa obter algumas informações do objeto HolographicSpace para criar o dispositivo Direct3D.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="b5bc0-119">Esta é a ID do adaptador DXGI associada à exibição Holographic.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="b5bc0-120">A classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> usa o dispositivo Direct3D 11 de seu aplicativo para criar e gerenciar recursos baseados em dispositivo, como os buffers de fundo para cada câmera Holographic.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="b5bc0-121">Se você estiver interessado em ver o que essa função faz nos bastidores, você a encontrará em DeviceResources. cpp.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="b5bc0-122">A função **DeviceResources:: InitializeUsingHolographicSpace** demonstra como obter o adaptador pesquisando a LUID – e como escolher um adaptador padrão quando nenhum adaptador preferencial for especificado.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="b5bc0-123">A classe principal do aplicativo usa o espaço Holographic de **AppView:: SetWindow** ou **App:: CreateWindowAndHolographicSpace** para atualizações e renderização.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="b5bc0-124">Embora as seções a seguir mencionem nomes de funções do modelo, como **AppView:: SetWindow** , que pressupõem que você começou do modelo de aplicativo Holographic UWP, os trechos de código que você vê serão aplicados igualmente entre os aplicativos UWP e Win32.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="b5bc0-125">Em seguida, vamos nos aprofundar no processo de configuração que **SetHolographicSpace** é responsável pela classe AppMain.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="b5bc0-126">Assinar eventos de câmera, criar e remover recursos de câmera</span><span class="sxs-lookup"><span data-stu-id="b5bc0-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="b5bc0-127">O conteúdo do Holographic do aplicativo reside em seu espaço de Holographic e é exibido por meio de uma ou mais câmeras de Holographic que representam perspectivas diferentes na cena.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="b5bc0-128">Agora que você tem o espaço Holographic, você pode receber dados para câmeras Holographic.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="b5bc0-129">Seu aplicativo precisa responder a eventos de **CameraAdded** criando qualquer recurso que seja específico para essa câmera, como a exibição de destino de renderização de buffer de fundo.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="b5bc0-130">Você pode ver esse código na função **DeviceResources:: SetHolographicSpace** , chamada por **AppView:: SetWindow** antes que o aplicativo crie qualquer quadro de Holographic:</span><span class="sxs-lookup"><span data-stu-id="b5bc0-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="b5bc0-131">Seu aplicativo também precisa responder a eventos do **CameraRemoved** liberando recursos que foram criados para essa câmera.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="b5bc0-132">De **DeviceResources:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="b5bc0-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="b5bc0-133">Os manipuladores de eventos devem concluir algum trabalho para manter a renderização de Holographic fluindo sem problemas, e para que seu aplicativo seja capaz de renderizar.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="b5bc0-134">Leia o código e os comentários para obter os detalhes: você pode procurar **OnCameraAdded** e **OnCameraRemoved** em sua classe principal para entender como o mapa do **M_cameraResources** é manipulado pelo **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="b5bc0-135">No momento, estamos concentrados no AppMain e na configuração que ele faz para permitir que seu aplicativo saiba sobre câmeras Holographic.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="b5bc0-136">Com isso em mente, é importante anotar os dois requisitos a seguir:</span><span class="sxs-lookup"><span data-stu-id="b5bc0-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="b5bc0-137">Para o manipulador de eventos **CameraAdded** , o aplicativo pode trabalhar de forma assíncrona para concluir a criação de recursos e o carregamento de ativos para a nova câmera Holographic.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="b5bc0-138">Os aplicativos que levam mais de um quadro para concluir esse trabalho devem solicitar um adiamento e concluir o adiamento após o carregamento de forma assíncrona; uma [tarefa ppl](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) pode ser usada para fazer trabalhos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="b5bc0-139">Seu aplicativo deve garantir que esteja pronto para renderizar para essa câmera imediatamente quando ele sair do manipulador de eventos ou quando concluir o adiamento.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="b5bc0-140">A saída do manipulador de eventos ou a conclusão do adiamento diz ao sistema que seu aplicativo agora está pronto para receber quadros Holographic com essa câmera incluída.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="b5bc0-141">Quando o aplicativo recebe um evento **CameraRemoved** , ele deve liberar todas as referências para o buffer de fundo e sair da função imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="b5bc0-142">Isso inclui exibições de destino de renderização e qualquer outro recurso que possa conter uma referência para o [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="b5bc0-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="b5bc0-143">O aplicativo também deve garantir que o buffer de fundo não esteja anexado como um destino de renderização, conforme mostrado em **CameraResources:: ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="b5bc0-144">Para ajudar a acelerar as coisas, seu aplicativo pode liberar o buffer de fundo e, em seguida, iniciar uma tarefa para concluir de forma assíncrona qualquer outro trabalho que seja necessário para desmontar essa câmera.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="b5bc0-145">O modelo de aplicativo Holographic inclui uma tarefa PPL que você pode usar para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="b5bc0-146">Se você quiser determinar quando uma câmera adicionada ou removida aparece no quadro, use as propriedades **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .</span><span class="sxs-lookup"><span data-stu-id="b5bc0-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="b5bc0-147">Criar um quadro de referência para o conteúdo do Holographic</span><span class="sxs-lookup"><span data-stu-id="b5bc0-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="b5bc0-148">O conteúdo do aplicativo deve ser posicionado em um [sistema de coordenadas espaciais](coordinate-systems-in-directx.md) a ser processado no HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="b5bc0-149">O sistema fornece dois quadros principais de referência que você pode usar para estabelecer um sistema de coordenadas para seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="b5bc0-150">Há dois tipos de quadros de referência no Windows Holographic: quadros de referência anexados ao dispositivo e quadros de referência que permanecem estacionários à medida que o dispositivo passa pelo ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="b5bc0-151">O modelo de aplicativo Holographic usa um quadro de referência estacionário por padrão; Essa é uma das maneiras mais simples de renderizar hologramas com bloqueios mundiais.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="b5bc0-152">Quadros de referência estacionários são projetados para estabilizar posições perto do local atual do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="b5bc0-153">Isso significa que as coordenadas mais adiante do dispositivo têm permissão para se descompassorem um pouco em relação ao ambiente do usuário, pois o dispositivo aprende mais sobre o espaço em torno dele.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="b5bc0-154">Há duas maneiras de criar um quadro estacionário de referência: Adquira o sistema de coordenadas do [estágio espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)ou use o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>padrão.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="b5bc0-155">Se você estiver criando um aplicativo de realidade mista do Windows para headsets de imersão, o ponto de partida recomendado é o [estágio espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), que também fornece informações sobre os recursos do headset de imersão gastados pelo jogador.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="b5bc0-156">Aqui, mostramos como usar o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>padrão.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="b5bc0-157">O localizador espacial representa o dispositivo Windows Mixed Reality e rastreia o movimento do dispositivo e fornece sistemas de coordenadas que podem ser compreendidos em relação à sua localização.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="b5bc0-158">De **AppMain:: OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="b5bc0-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="b5bc0-159">Crie o quadro de referência estacionário uma vez quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="b5bc0-160">Isso é análogo à definição de um sistema de coordenadas mundiais, com a origem colocada na posição do dispositivo quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="b5bc0-161">Este quadro de referência não se move com o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="b5bc0-162">De **AppMain:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="b5bc0-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="b5bc0-163">Todos os quadros de referência estão alinhados com a gravidade, o que significa que o eixo y aponta "para cima" em relação ao ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="b5bc0-164">Como o Windows usa sistemas de coordenadas "destros", a direção do eixo – z coincide com a direção "encaminhar" que o dispositivo está enfrentando quando o quadro de referência é criado.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="b5bc0-165">Quando seu aplicativo exige o posicionamento preciso de hologramas individuais, use um <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> para ancorar o holograma individual em uma posição no mundo real.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="b5bc0-166">Por exemplo, use uma âncora espacial quando o usuário indicar um ponto para ser um interesse especial.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="b5bc0-167">As posições de âncora não são descompassos, mas podem ser ajustadas.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="b5bc0-168">Por padrão, quando uma âncora é ajustada, ela facilita sua posição nos próximos vários quadros depois que a correção ocorre.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="b5bc0-169">Dependendo do seu aplicativo, quando isso ocorrer, talvez você queira lidar com o ajuste de uma maneira diferente (por exemplo, adiando-o até que o holograma esteja fora da exibição).</span><span class="sxs-lookup"><span data-stu-id="b5bc0-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="b5bc0-170">A propriedade <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> e os eventos <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> permitem essas personalizações.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="b5bc0-171">Responder a eventos alterados do locatability</span><span class="sxs-lookup"><span data-stu-id="b5bc0-171">Respond to locatability changed events</span></span>

<span data-ttu-id="b5bc0-172">A renderização de hologramas bloqueados em todo o mundo exige que o dispositivo seja capaz de se localizar no mundo.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="b5bc0-173">Isso nem sempre pode ser possível devido a condições ambientais e, nesse caso, o usuário pode esperar uma indicação visual da interrupção do controle.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="b5bc0-174">Essa indicação visual deve ser renderizada usando quadros de referência anexados ao dispositivo, em vez de ser estacionário ao mundo.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="b5bc0-175">O aplicativo pode solicitar a notificação se o rastreamento for interrompido por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="b5bc0-176">Registre-se no evento LocatabilityChanged para detectar quando a capacidade do dispositivo de se localizar no mundo é alterada.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="b5bc0-177">De **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="b5bc0-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="b5bc0-178">Em seguida, use esse evento para determinar quando os hologramas não podem ser renderizados como estáticos para o mundo.</span><span class="sxs-lookup"><span data-stu-id="b5bc0-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5bc0-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5bc0-179">See also</span></span>
* [<span data-ttu-id="b5bc0-180">Como renderizar no DirectX</span><span class="sxs-lookup"><span data-stu-id="b5bc0-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="b5bc0-181">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="b5bc0-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)

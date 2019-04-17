---
title: Obtendo um HolographicSpace
description: Explica a API HolographicSpace, um conceito central para renderização holográfica e entrada espacial.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, espacial de entrada, renderização, trocar a cadeia, quadro holográfico, loop de atualização, loop do jogo, quadro de referência, locatability, código de exemplo e instruções passo a passo
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591016"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="73828-104">Obtendo um HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="73828-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="73828-105">O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> classe é o seu portal para o mundo holographic.</span><span class="sxs-lookup"><span data-stu-id="73828-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="73828-106">Controla a renderização imersiva, fornece dados de câmera e fornece acesso às APIs de raciocínio espacial.</span><span class="sxs-lookup"><span data-stu-id="73828-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="73828-107">Você criará um para seu aplicativo UWP <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> ou HWND do seu aplicativo Win32.</span><span class="sxs-lookup"><span data-stu-id="73828-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="73828-108">Configurar o espaço holográfico</span><span class="sxs-lookup"><span data-stu-id="73828-108">Set up the holographic space</span></span>

<span data-ttu-id="73828-109">Criar o objeto de espaço holográfica é a primeira etapa para tornar seu aplicativo de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="73828-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="73828-110">Renderizam aplicativos tradicionais do Windows para uma cadeia de troca do Direct3D criada para a janela principal do modo de exibição de seu aplicativos.</span><span class="sxs-lookup"><span data-stu-id="73828-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="73828-111">A cadeia de troca é exibida em um slate na interface do usuário holographic.</span><span class="sxs-lookup"><span data-stu-id="73828-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="73828-112">Para tornar seu modo de exibição do aplicativo holographic em vez de um slate 2D, crie um espaço holographic para sua janela principal, em vez de uma cadeia de troca.</span><span class="sxs-lookup"><span data-stu-id="73828-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="73828-113">Apresentar holográfico quadros que são criados por esse espaço holográfico coloca seu aplicativo no modo de renderização em tela inteira.</span><span class="sxs-lookup"><span data-stu-id="73828-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="73828-114">Para um **aplicativo UWP** [a partir de *modelo de aplicativo de 11 holográfica DirectX (Windows Universal)*](creating-a-holographic-directx-project.md), procure esse código no **SetWindow** método na AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="73828-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="73828-115">Para um **aplicativo Win32** [a partir de *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), examinar **App::CreateWindowAndHolographicSpace** para um exemplo de como criar um HWND e, em seguida, convertê-la em um HWND imersivo, criando um associado <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="73828-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
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

<span data-ttu-id="73828-116">Agora que você já adquiriu um HolographicSpace para o CoreWindow do UWP ou Win32 HWND, você usará esse HolographicSpace para manipular câmeras holográfica, criar sistemas de coordenadas e fazer a renderização holográfica.</span><span class="sxs-lookup"><span data-stu-id="73828-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="73828-117">O espaço de holográfico atual é usado em vários lugares no modelo de DirectX:</span><span class="sxs-lookup"><span data-stu-id="73828-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="73828-118">O **DeviceResources** classe precisa obter algumas informações do objeto HolographicSpace para criar o dispositivo Direct3D.</span><span class="sxs-lookup"><span data-stu-id="73828-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="73828-119">Isso é a ID do adaptador DXGI associada à exibição holográfica.</span><span class="sxs-lookup"><span data-stu-id="73828-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="73828-120">O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> classe usa o dispositivo de Direct3D 11 do seu aplicativo para criar e gerenciar recursos com base em dispositivo, como os buffers de voltar para cada câmera holográfica.</span><span class="sxs-lookup"><span data-stu-id="73828-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="73828-121">Se você estiver interessado em ver o que essa função faz nos bastidores, você o encontrará em Deviceresources.</span><span class="sxs-lookup"><span data-stu-id="73828-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="73828-122">A função **DeviceResources::InitializeUsingHolographicSpace** demonstra como obter o adaptador pesquisando o LUID – e como escolher um adaptador padrão quando nenhum adaptador preferencial é especificado.</span><span class="sxs-lookup"><span data-stu-id="73828-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="73828-123">Classe de principal do aplicativo usa o espaço holográfico do **AppView::SetWindow** ou **App::CreateWindowAndHolographicSpace** para atualizações e renderização.</span><span class="sxs-lookup"><span data-stu-id="73828-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="73828-124">Embora as seções abaixo mencionam nomes de função do modelo, como **AppView::SetWindow** que supõem que você começou a partir do modelo de aplicativo UWP holográfico, os trechos de código que você consulte serão aplicado igualmente entre os aplicativos UWP e Win32.</span><span class="sxs-lookup"><span data-stu-id="73828-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="73828-125">Em seguida, vamos nos aprofundar na configuração do processo que **SetHolographicSpace** é responsável por na classe AppMain.</span><span class="sxs-lookup"><span data-stu-id="73828-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="73828-126">Assinar eventos de câmera, criar e remover recursos de câmera</span><span class="sxs-lookup"><span data-stu-id="73828-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="73828-127">Conteúdo holográfica do seu aplicativo reside em seu espaço de holográfico e é exibido por meio de um ou mais câmeras holográfica que representam diferentes perspectivas na cena.</span><span class="sxs-lookup"><span data-stu-id="73828-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="73828-128">Agora que você tem o espaço holográfico, você pode receber dados de câmeras holográfica.</span><span class="sxs-lookup"><span data-stu-id="73828-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="73828-129">Seu aplicativo precisa responder às **CameraAdded** eventos com a criação de todos os recursos que são específicos para essa câmera, como seu buffer de fundo renderizar a exibição de destino.</span><span class="sxs-lookup"><span data-stu-id="73828-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="73828-130">Você pode ver esse código na **DeviceResources::SetHolographicSpace** função, chamada pelo **AppView::SetWindow** antes que o aplicativo cria todos os quadros holográfico:</span><span class="sxs-lookup"><span data-stu-id="73828-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="73828-131">Seu aplicativo também precisa responder às **CameraRemoved** eventos por liberação de recursos que foram criados para essa câmera.</span><span class="sxs-lookup"><span data-stu-id="73828-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="73828-132">Partir **DeviceResources::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="73828-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="73828-133">Os manipuladores de eventos devem completar algum trabalho para manter a renderização holográfica fluindo sem problemas, e para que seu aplicativo seja capaz de renderizar em todos os.</span><span class="sxs-lookup"><span data-stu-id="73828-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="73828-134">Ler o código e comentários para obter detalhes: você pode procurar por **OnCameraAdded** e **OnCameraRemoved** em sua classe principal para compreender como o **m_cameraResources** é de mapa tratados pelo **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="73828-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="73828-135">Agora, estamos concentrados em AppMain e a configuração que faz para habilitar seu aplicativo saber sobre holográfica câmeras.</span><span class="sxs-lookup"><span data-stu-id="73828-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="73828-136">Com isso em mente, é importante tomar nota dos dois requisitos a seguir:</span><span class="sxs-lookup"><span data-stu-id="73828-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="73828-137">Para o **CameraAdded** manipulador de eventos, o aplicativo pode trabalhar assincronamente para concluir a criação de recursos e carregar ativos para a nova câmera holográfica.</span><span class="sxs-lookup"><span data-stu-id="73828-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="73828-138">Aplicativos que usam mais de um quadro para concluir o trabalho devem solicitar um adiamento e conclua o adiamento após o carregamento de forma assíncrona; uma [tarefas PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) pode ser usado para fazer o trabalho assíncrono.</span><span class="sxs-lookup"><span data-stu-id="73828-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="73828-139">Seu aplicativo deve garantir que ele está pronto para processar para essa câmera imediatamente quando o manipulador de eventos é encerrada, ou quando o adiamento é concluído.</span><span class="sxs-lookup"><span data-stu-id="73828-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="73828-140">Sair do manipulador de eventos ou concluir o adiamento informa ao sistema que seu aplicativo agora está pronto para receber quadros holográfico com essa câmera incluída.</span><span class="sxs-lookup"><span data-stu-id="73828-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="73828-141">Quando o aplicativo recebe um **CameraRemoved** evento, ele deve liberar todas as referências para o buffer de fundo e saia imediatamente e a função.</span><span class="sxs-lookup"><span data-stu-id="73828-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="73828-142">Isso inclui modos de exibição de destino de renderização e qualquer outro recurso que pode conter uma referência para o [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="73828-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="73828-143">O aplicativo também deve garantir que o buffer de fundo não está anexado como um destino de renderização, conforme mostrado na **CameraResources::ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="73828-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="73828-144">Para ajudar a agilizar as coisas ao longo, seu aplicativo pode liberar o buffer de fundo e, em seguida, inicie uma tarefa para concluir a qualquer outro trabalho que é necessário para subdividir esse câmera assincronamente.</span><span class="sxs-lookup"><span data-stu-id="73828-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="73828-145">O modelo de aplicativo holográfica inclui uma tarefa PPL que você pode usar para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="73828-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="73828-146">Se você desejar determinar quando uma câmera tiver adicionada ou removida aparece no quadro, use o **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) propriedades.</span><span class="sxs-lookup"><span data-stu-id="73828-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="73828-147">Criar um quadro de referência para o seu conteúdo holográfico</span><span class="sxs-lookup"><span data-stu-id="73828-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="73828-148">Conteúdo do seu aplicativo deve ser posicionado em um [sistema de coordenadas espacial](coordinate-systems-in-directx.md) a ser renderizada no HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="73828-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="73828-149">O sistema fornece dois primários quadros de referência que pode ser usado para estabelecer um sistema de coordenadas para seu hologramas.</span><span class="sxs-lookup"><span data-stu-id="73828-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="73828-150">Há dois tipos de quadros de referência no Windows Holographic: referência anexados ao dispositivo de quadros e quadros de referência que permanecem parados conforme se move o dispositivo por meio do ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="73828-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="73828-151">O modelo de aplicativo holográfica usa um quadro estacionário de referência por padrão. Essa é uma das maneiras mais simples para renderizar hologramas bloqueado pelo mundo.</span><span class="sxs-lookup"><span data-stu-id="73828-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="73828-152">Quadros de referência estáticos são projetados para se estabilizar posições de perto a localização do dispositivo atual.</span><span class="sxs-lookup"><span data-stu-id="73828-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="73828-153">Isso significa que as coordenadas mais longe de dispositivo têm permissão para descompasso ligeiramente em relação ao ambiente do usuário, como o dispositivo lado aprende mais sobre o espaço em torno dele.</span><span class="sxs-lookup"><span data-stu-id="73828-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="73828-154">Há duas maneiras de criar um quadro estacionário de referência: adquirir o sistema de coordenadas do [estágio espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), ou use o padrão <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="73828-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="73828-155">Se você estiver criando um aplicativo de realidade mista do Windows para fones imersivos em exposição, o ponto de partida recomendado é o [estágio espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), que também fornece informações sobre os recursos de imersão fone de ouvido gasta pelo player.</span><span class="sxs-lookup"><span data-stu-id="73828-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="73828-156">Aqui, mostramos como usar o padrão <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="73828-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="73828-157">O localizador espacial representa o dispositivo Windows Mixed Reality e controla o movimento do dispositivo e fornece sistemas de coordenadas que possa ser compreendidos em relação ao seu local.</span><span class="sxs-lookup"><span data-stu-id="73828-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="73828-158">Partir **AppMain::OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="73828-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="73828-159">Crie o quadro estacionário de referência de uma vez quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="73828-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="73828-160">Isso é análogo à definição de um sistema de coordenadas do mundo, com a origem colocada na posição do dispositivo quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="73828-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="73828-161">Esse quadro de referência não é movido com o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="73828-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="73828-162">Partir **AppMain::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="73828-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="73828-163">Todos os quadros de referência são gravidade alinhada, que significa que o eixo y aponta "para cima" em relação ao ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="73828-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="73828-164">Como o Windows usa "destros" sistemas de coordenadas, a direção do eixo z – coincide com a direção "forward", o dispositivo estiver voltada para quando o quadro de referência é criado.</span><span class="sxs-lookup"><span data-stu-id="73828-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="73828-165">Quando seu aplicativo requer o posicionamento exato dos hologramas individuais, use uma <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> ancorar o holograma individual para uma posição no mundo real.</span><span class="sxs-lookup"><span data-stu-id="73828-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="73828-166">Por exemplo, use uma âncora espacial quando o usuário indica um ponto de interesse especial.</span><span class="sxs-lookup"><span data-stu-id="73828-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="73828-167">Posições de âncora não descompasso, mas eles podem ser ajustados.</span><span class="sxs-lookup"><span data-stu-id="73828-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="73828-168">Por padrão, quando uma âncora é ajustada, facilita a sua posição no lugar ao longo de vários quadros próxima depois que a correção ocorreu.</span><span class="sxs-lookup"><span data-stu-id="73828-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="73828-169">Dependendo do seu aplicativo, quando isso ocorrer você talvez queira lidar com o ajuste de maneira diferente (por exemplo, adiamento até que o holograma está fora do modo de exibição).</span><span class="sxs-lookup"><span data-stu-id="73828-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="73828-170">O <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> propriedade e <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> eventos permitem que essas personalizações.</span><span class="sxs-lookup"><span data-stu-id="73828-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="73828-171">Responder a eventos locatability alterado</span><span class="sxs-lookup"><span data-stu-id="73828-171">Respond to locatability changed events</span></span>

<span data-ttu-id="73828-172">Renderização bloqueado pelo mundo hologramas requer que o dispositivo para poder localizar-se no mundo.</span><span class="sxs-lookup"><span data-stu-id="73828-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="73828-173">Isso talvez nem sempre seja possível devido a condições ambientais e, nesse caso, o usuário pode esperar uma indicação visual de que a interrupção do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="73828-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="73828-174">Essa indicação visual deve ser renderizada usando quadros de referência anexados ao dispositivo, em vez de estático para o mundo.</span><span class="sxs-lookup"><span data-stu-id="73828-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="73828-175">Seu aplicativo pode solicitar para ser notificado se o rastreamento é interrompido por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="73828-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="73828-176">Registre-se para o evento LocatabilityChanged detectar quando a capacidade do dispositivo para localizar-se nas alterações do mundo.</span><span class="sxs-lookup"><span data-stu-id="73828-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="73828-177">De **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="73828-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="73828-178">Em seguida, use esse evento para determinar quando hologramas não podem ser renderizadas estáticos para o mundo.</span><span class="sxs-lookup"><span data-stu-id="73828-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="73828-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73828-179">See also</span></span>
* [<span data-ttu-id="73828-180">Processamento no DirectX</span><span class="sxs-lookup"><span data-stu-id="73828-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="73828-181">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="73828-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)

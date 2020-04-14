---
title: Adicionar comunicação remota do Holographic
description: Explica como usar a comunicação remota do Holographic para renderizar hologramas em um HoloLens pela rede.
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Realidade mista do Windows, hologramas, comunicação remota Holographic, renderização remota, renderização de rede, HoloLens, hologramas remotos
ms.openlocfilehash: 2f6ade5552c993f66281d0be8a7e62c8f076deac
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277704"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a><span data-ttu-id="b44c8-104">Adicionar comunicação remota Holographic (HoloLens (1ª gen))</span><span class="sxs-lookup"><span data-stu-id="b44c8-104">Add Holographic Remoting (HoloLens (1st gen))</span></span>

>[!IMPORTANT]
><span data-ttu-id="b44c8-105">Este documento descreve a criação de um aplicativo host para o HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="b44c8-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="b44c8-106">O aplicativo de host para o **HoloLens (1º gen)** deve usar o pacote NuGet versão **1. x**. x.</span><span class="sxs-lookup"><span data-stu-id="b44c8-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="b44c8-107">Isso implica que os aplicativos host escritos para o HoloLens 1 não são compatíveis com o HoloLens 2 e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="b44c8-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="b44c8-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b44c8-108">HoloLens 2</span></span>

<span data-ttu-id="b44c8-109">Os desenvolvedores de HoloLens que usam a comunicação remota do Holographic precisarão atualizar seus aplicativos para torná-los compatíveis com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b44c8-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="b44c8-110">Isso requer uma nova versão do pacote NuGet de comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="b44c8-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="b44c8-111">Se um aplicativo que usa o pacote NuGet de comunicação remota do Holographic com um número de versão menor do que o 2.0.0.0 tentar se conectar ao Player de comunicação remota do Holographic no HoloLens 2, a conexão falhará.</span><span class="sxs-lookup"><span data-stu-id="b44c8-111">If an application using the Holographic Remoting NuGet package with a version number smaller than 2.0.0.0 attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>

>[!NOTE]
><span data-ttu-id="b44c8-112">As diretrizes específicas para o HoloLens 2 podem ser encontradas [aqui](holographic-remoting-create-host.md).</span><span class="sxs-lookup"><span data-stu-id="b44c8-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-host.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="b44c8-113">Adicionar a comunicação remota do Holographic ao seu aplicativo da área de trabalho ou UWP</span><span class="sxs-lookup"><span data-stu-id="b44c8-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="b44c8-114">Esta página descreve como adicionar o Holographic Remoting a um aplicativo desktop ou UWP.</span><span class="sxs-lookup"><span data-stu-id="b44c8-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="b44c8-115">A comunicação remota do Holographic permite que seu aplicativo direcione um HoloLens com conteúdo Holographic hospedado em um PC desktop ou em um dispositivo UWP, como o Xbox One, permitindo o acesso a mais recursos do sistema e possibilitando a integração de [exibições de imersão](app-views.md) remotas ao software de PC desktop existente.</span><span class="sxs-lookup"><span data-stu-id="b44c8-115">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="b44c8-116">Um aplicativo host de comunicação remota recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição de imersão virtual e transmite quadros de conteúdo de volta para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b44c8-116">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="b44c8-117">A conexão é feita usando Wi-Fi padrão.</span><span class="sxs-lookup"><span data-stu-id="b44c8-117">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="b44c8-118">Para usar a comunicação remota, você usará um pacote NuGet para adicionar o Holographic Remoting ao seu aplicativo de área de trabalho ou UWP e escreverá código para lidar com a conexão e para renderizar em uma exibição de imersão.</span><span class="sxs-lookup"><span data-stu-id="b44c8-118">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="b44c8-119">As bibliotecas auxiliares são incluídas no exemplo de código que simplificam a tarefa de lidar com a conexão do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b44c8-119">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="b44c8-120">Uma conexão de comunicação remota típica terá um mínimo de 50 ms de latência.</span><span class="sxs-lookup"><span data-stu-id="b44c8-120">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="b44c8-121">O aplicativo de player pode relatar a latência em tempo real.</span><span class="sxs-lookup"><span data-stu-id="b44c8-121">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="b44c8-122">Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="b44c8-122">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="b44c8-123">Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="b44c8-123">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="b44c8-124">Obter os pacotes de NuGet de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="b44c8-124">Get the remoting NuGet packages</span></span>

<span data-ttu-id="b44c8-125">Siga estas etapas para obter o pacote NuGet para a comunicação remota do Holographic e adicione uma referência do seu projeto:</span><span class="sxs-lookup"><span data-stu-id="b44c8-125">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="b44c8-126">Vá para seu projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b44c8-126">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="b44c8-127">Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="b44c8-127">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="b44c8-128">No painel que aparece, clique em **procurar** e procure "comunicação remota do Holographic".</span><span class="sxs-lookup"><span data-stu-id="b44c8-128">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="b44c8-129">Selecione **Microsoft. Holographic. Remoting** e clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="b44c8-129">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="b44c8-130">Se a caixa de diálogo **Visualizar** for exibida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b44c8-130">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="b44c8-131">A próxima caixa de diálogo exibida é o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="b44c8-131">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="b44c8-132">Clique em **aceito** para aceitar o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="b44c8-132">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="b44c8-133">Criar o HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="b44c8-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="b44c8-134">Primeiro, precisamos de uma instância de HolographicStreamerHelpers.</span><span class="sxs-lookup"><span data-stu-id="b44c8-134">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="b44c8-135">Adicione isso à classe que tratará de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="b44c8-135">Add this to the class that will be handling remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="b44c8-136">Você também precisará acompanhar o estado da conexão.</span><span class="sxs-lookup"><span data-stu-id="b44c8-136">You'll also need to track connection state.</span></span> <span data-ttu-id="b44c8-137">Se você quiser renderizar a visualização, precisará ter uma textura para copiá-la para.</span><span class="sxs-lookup"><span data-stu-id="b44c8-137">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="b44c8-138">Você também precisa de algumas coisas como um bloqueio de estado de conexão, alguma maneira de armazenar o endereço IP do HoloLens e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b44c8-138">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="b44c8-139">Inicializar o HolographicStreamerHelpers e conectar-se ao HoloLens</span><span class="sxs-lookup"><span data-stu-id="b44c8-139">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="b44c8-140">Para se conectar a um dispositivo HoloLens, crie uma instância do HolographicStreamerHelpers e conecte-se ao endereço IP de destino.</span><span class="sxs-lookup"><span data-stu-id="b44c8-140">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="b44c8-141">Você precisará definir o tamanho do quadro de vídeo para corresponder à largura e altura de exibição do HoloLens, pois a biblioteca de comunicação remota Holographic espera que as resoluções do codificador e do decodificador correspondam exatamente.</span><span class="sxs-lookup"><span data-stu-id="b44c8-141">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="b44c8-142">A conexão do dispositivo é assíncrona.</span><span class="sxs-lookup"><span data-stu-id="b44c8-142">The device connection is asynchronous.</span></span> <span data-ttu-id="b44c8-143">Seu aplicativo precisa fornecer manipuladores de eventos para eventos de conexão, desconexão e quadros de envio.</span><span class="sxs-lookup"><span data-stu-id="b44c8-143">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="b44c8-144">O evento onconnected pode atualizar a interface do usuário, iniciar a renderização e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b44c8-144">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="b44c8-145">Em nosso exemplo de código de área de trabalho, atualizamos o título da janela com uma mensagem "conectada".</span><span class="sxs-lookup"><span data-stu-id="b44c8-145">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="b44c8-146">O evento ondisconnectd pode lidar com a reconexão, as atualizações da interface do usuário e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b44c8-146">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="b44c8-147">Neste exemplo, reconectamos se houver uma falha transitória.</span><span class="sxs-lookup"><span data-stu-id="b44c8-147">In this example, we reconnect if there is a transient failure.</span></span>

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="b44c8-148">Quando o componente de comunicação remota está pronto para enviar um quadro, seu aplicativo recebe uma oportunidade de fazer uma cópia dele no SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="b44c8-148">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="b44c8-149">Aqui, copiamos o quadro em uma cadeia de permuta para que possamos exibi-lo em uma janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="b44c8-149">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="b44c8-150">Renderizar conteúdo Holographic</span><span class="sxs-lookup"><span data-stu-id="b44c8-150">Render holographic content</span></span>

<span data-ttu-id="b44c8-151">Para renderizar o conteúdo usando comunicação remota, você configura um IFrameworkView virtual em seu aplicativo de área de trabalho ou UWP e processa os quadros Holographic da comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="b44c8-151">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="b44c8-152">Todas as APIs Holographic do Windows são usadas da mesma forma por essa exibição, mas elas são configuradas de forma ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="b44c8-152">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="b44c8-153">Em vez de criá-los por conta própria, os componentes de espaço e fala do Holographic vêm de sua classe HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="b44c8-153">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="b44c8-154">Em vez de usar um loop de atualização dentro de um método Run, você fornece atualizações em escala do loop principal de seu aplicativo de desktop ou UWP.</span><span class="sxs-lookup"><span data-stu-id="b44c8-154">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="b44c8-155">Isso permite que seu aplicativo da área de trabalho ou UWP permaneça no controle do processamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b44c8-155">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="b44c8-156">O método Tick () da exibição do aplicativo Holographic conclui uma iteração do loop Update, Draw e Present.</span><span class="sxs-lookup"><span data-stu-id="b44c8-156">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="b44c8-157">O loop de atualização de exibição do aplicativo Holographic, render e Present é exatamente o mesmo que é quando executado no HoloLens, exceto pelo fato de que você tem acesso a uma quantidade muito maior de recursos do sistema no seu PC desktop.</span><span class="sxs-lookup"><span data-stu-id="b44c8-157">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="b44c8-158">Você pode renderizar muitos triângulos, ter mais passagens de desenho, realizar mais física e usar processos x64 para carregar o conteúdo que exige mais de 2 GB de RAM.</span><span class="sxs-lookup"><span data-stu-id="b44c8-158">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="b44c8-159">Desconectar e encerrar a sessão remota</span><span class="sxs-lookup"><span data-stu-id="b44c8-159">Disconnect and end the remote session</span></span>

<span data-ttu-id="b44c8-160">Para desconectar-por exemplo, quando o usuário clica em um botão da interface do usuário para desconectar-chamada Disconnect () no HolographicStreamerHelpers e, em seguida, libera o objeto.</span><span class="sxs-lookup"><span data-stu-id="b44c8-160">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="b44c8-161">Obter o reprodutor de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="b44c8-161">Get the remoting player</span></span>

<span data-ttu-id="b44c8-162">O player de comunicação remota do Windows Holographic é oferecido na loja de aplicativos do Windows como um ponto de extremidade para aplicativos de host remotos se conectarem ao.</span><span class="sxs-lookup"><span data-stu-id="b44c8-162">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="b44c8-163">Para obter o Windows Holographic Remoting Player, visite a Windows App Store do seu HoloLens, pesquise por comunicação remota e baixe o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b44c8-163">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="b44c8-164">O player de comunicação remota inclui um recurso para exibir estatísticas na tela, o que pode ser útil ao depurar aplicativos de host de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="b44c8-164">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="b44c8-165">Notas e recursos</span><span class="sxs-lookup"><span data-stu-id="b44c8-165">Notes and resources</span></span>

<span data-ttu-id="b44c8-166">A exibição do aplicativo Holographic precisará de uma maneira de fornecer seu aplicativo com o dispositivo Direct3D, que deve ser usado para inicializar o espaço do Holographic.</span><span class="sxs-lookup"><span data-stu-id="b44c8-166">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="b44c8-167">Seu aplicativo deve usar este dispositivo Direct3D para copiar e exibir o quadro de visualização.</span><span class="sxs-lookup"><span data-stu-id="b44c8-167">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="b44c8-168">**Exemplo de código:** Um exemplo de código remoto Holographic completo está disponível, que inclui uma exibição de aplicativo Holographic compatível com projetos de host remoto e de comunicação remota para desktop Win32, UWP DirectX e UWP com XAML.</span><span class="sxs-lookup"><span data-stu-id="b44c8-168">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="b44c8-169">Para obtê-lo, acesse:</span><span class="sxs-lookup"><span data-stu-id="b44c8-169">To get it, go here:</span></span>
* [<span data-ttu-id="b44c8-170">Exemplo de código do Windows Holographic para comunicação remota</span><span class="sxs-lookup"><span data-stu-id="b44c8-170">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="b44c8-171">**Observação de depuração:** A biblioteca de comunicação remota do Holographic pode gerar exceções de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="b44c8-171">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="b44c8-172">Essas exceções podem ser visíveis em sessões de depuração, dependendo das configurações de exceção do Visual Studio que estão ativas no momento.</span><span class="sxs-lookup"><span data-stu-id="b44c8-172">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="b44c8-173">Essas exceções são detectadas internamente pela biblioteca de comunicação remota do Holographic e podem ser ignoradas.</span><span class="sxs-lookup"><span data-stu-id="b44c8-173">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>

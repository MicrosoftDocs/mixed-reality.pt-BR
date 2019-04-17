---
title: Adicionar holográfica remoting
description: Explica como usar comunicação remota holográfica renderizar hologramas um HoloLens pela rede.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, comunicação remota holográfica, processamento remoto, renderização, HoloLens, hologramas remotas de rede
ms.openlocfilehash: 4726c6af43fe1b89fc8298e459a1af9dfa5fc667
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591025"
---
# <a name="add-holographic-remoting"></a><span data-ttu-id="95cfa-104">Adicionar holográfica remoting</span><span class="sxs-lookup"><span data-stu-id="95cfa-104">Add holographic remoting</span></span>

> [!NOTE]
> <span data-ttu-id="95cfa-105">Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="95cfa-105">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="95cfa-106">Adicionar remoting holográfica à sua área de trabalho ou um aplicativo UWP</span><span class="sxs-lookup"><span data-stu-id="95cfa-106">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="95cfa-107">Esta página descreve como adicionar Remoting Holographic para uma área de trabalho ou um aplicativo UWP.</span><span class="sxs-lookup"><span data-stu-id="95cfa-107">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="95cfa-108">Comunicação remota holográfica permite que seu aplicativo para ter como destino um HoloLens com holográfico conteúdo hospedado em um desktop PC ou em um dispositivo UWP como o Xbox One, permitindo o acesso a mais recursos do sistema e torná-lo possível integrar remoto [exibições imersivas](app-views.md) para o software de PC do desktop existente.</span><span class="sxs-lookup"><span data-stu-id="95cfa-108">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="95cfa-109">Um aplicativo de host de comunicação remota recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em um modo de exibição virtual envolvente e transmite o conteúdo quadros de volta para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="95cfa-109">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="95cfa-110">A conexão é feita usando o padrão de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="95cfa-110">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="95cfa-111">Para usar a comunicação remota, você usar um pacote do NuGet para adicionar remoting holográfica a sua área de trabalho ou um aplicativo UWP e escrever código para lidar com a conexão e a renderização de um modo de exibição envolvente.</span><span class="sxs-lookup"><span data-stu-id="95cfa-111">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="95cfa-112">Bibliotecas auxiliares estão incluídas no exemplo de código que simplificam a tarefa de lidar com a conexão do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="95cfa-112">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="95cfa-113">Uma conexão de comunicação remota típica terá baixo como 50 ms de latência.</span><span class="sxs-lookup"><span data-stu-id="95cfa-113">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="95cfa-114">O aplicativo de player pode relatar a latência em tempo real.</span><span class="sxs-lookup"><span data-stu-id="95cfa-114">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="95cfa-115">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="95cfa-115">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="95cfa-116">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="95cfa-116">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="95cfa-117">Obter a comunicação remota pacotes do NuGet</span><span class="sxs-lookup"><span data-stu-id="95cfa-117">Get the remoting NuGet packages</span></span>

<span data-ttu-id="95cfa-118">Siga estas etapas para obter o pacote do NuGet para comunicação remota holográfica e adicione uma referência do seu projeto:</span><span class="sxs-lookup"><span data-stu-id="95cfa-118">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="95cfa-119">Vá para seu projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="95cfa-119">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="95cfa-120">Clique com botão direito no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="95cfa-120">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="95cfa-121">No painel que aparece, clique em **procurar** e, em seguida, pesquise por "Holográfica a comunicação remota".</span><span class="sxs-lookup"><span data-stu-id="95cfa-121">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="95cfa-122">Selecione **Microsoft.Holographic.Remoting** e clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="95cfa-122">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="95cfa-123">Se o **versão prévia** caixa de diálogo for exibida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="95cfa-123">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="95cfa-124">A próxima caixa de diálogo que aparece é o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="95cfa-124">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="95cfa-125">Clique em **aceito** para aceitar o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="95cfa-125">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="95cfa-126">Criar o HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="95cfa-126">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="95cfa-127">Primeiro, precisamos de uma instância de HolographicStreamerHelpers.</span><span class="sxs-lookup"><span data-stu-id="95cfa-127">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="95cfa-128">Adicione isso à classe que manipulará a comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="95cfa-128">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="95cfa-129">Você também será necessário controlar o estado da conexão.</span><span class="sxs-lookup"><span data-stu-id="95cfa-129">You'll also need to track connection state.</span></span> <span data-ttu-id="95cfa-130">Se você deseja renderizar a visualização, você precisa ter uma textura para copiá-lo para.</span><span class="sxs-lookup"><span data-stu-id="95cfa-130">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="95cfa-131">Você também precisa de alguns itens como um bloqueio de estado de conexão, alguma forma de armazenar o endereço IP do HoloLens e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="95cfa-131">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```
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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="95cfa-132">Inicializar HolographicStreamerHelpers e conecte-se ao HoloLens</span><span class="sxs-lookup"><span data-stu-id="95cfa-132">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="95cfa-133">Para se conectar a um dispositivo HoloLens, crie uma instância de HolographicStreamerHelpers e conecte-se para o endereço IP de destino.</span><span class="sxs-lookup"><span data-stu-id="95cfa-133">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="95cfa-134">Você precisará definir o tamanho do quadro de vídeo para coincidir com a largura da exibição HoloLens e a altura, porque a biblioteca de comunicação remota holográfica espera que as resoluções de codificador e decodificador de uma correspondência exata.</span><span class="sxs-lookup"><span data-stu-id="95cfa-134">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```
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

<span data-ttu-id="95cfa-135">A conexão do dispositivo é assíncrona.</span><span class="sxs-lookup"><span data-stu-id="95cfa-135">The device connection is asynchronous.</span></span> <span data-ttu-id="95cfa-136">Necessidades de seu aplicativo para fornecer manipuladores de eventos para conectar, desconectar e quadro enviar eventos.</span><span class="sxs-lookup"><span data-stu-id="95cfa-136">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="95cfa-137">O evento OnConnected pode atualizar a interface do usuário, iniciar a renderização e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="95cfa-137">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="95cfa-138">Em nosso exemplo de código de área de trabalho, podemos atualizar o título da janela com uma mensagem "conectada".</span><span class="sxs-lookup"><span data-stu-id="95cfa-138">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="95cfa-139">O evento OnDisconnected pode lidar com a reconexão, atualizações de interface do usuário e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="95cfa-139">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="95cfa-140">Neste exemplo, podemos reconexão se houver uma falha temporária.</span><span class="sxs-lookup"><span data-stu-id="95cfa-140">In this example, we reconnect if there is a transient failure.</span></span>

```
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

<span data-ttu-id="95cfa-141">Quando o componente de comunicação remota estiver pronto para enviar um quadro, seu aplicativo é fornecido a oportunidade de fazer uma cópia no SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="95cfa-141">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="95cfa-142">Aqui, podemos copiar o quadro para uma cadeia de troca para que podemos pode exibi-lo em uma janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="95cfa-142">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```
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

### <a name="render-holographic-content"></a><span data-ttu-id="95cfa-143">Renderizar conteúdo holográfico</span><span class="sxs-lookup"><span data-stu-id="95cfa-143">Render holographic content</span></span>

<span data-ttu-id="95cfa-144">Para renderizar conteúdo usando a comunicação remota, você configura um virtual IFrameworkView dentro de sua área de trabalho ou um aplicativo UWP e processar holográfico quadros de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="95cfa-144">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="95cfa-145">Todas as APIs do Windows Holographic são usados que da mesma forma por este modo de exibição, mas ele é definida um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="95cfa-145">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="95cfa-146">Em vez de criá-las por conta própria, os componentes de fala e espaço holográfico provenientes de sua classe HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="95cfa-146">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="95cfa-147">Em vez de usar um loop de atualização dentro de um método de execução, você fornecer atualizações de escala do loop principal do seu desktop ou um aplicativo UWP.</span><span class="sxs-lookup"><span data-stu-id="95cfa-147">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="95cfa-148">Isso permite que seu computador desktop ou um aplicativo UWP para manter o controle do processamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="95cfa-148">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="95cfa-149">Método de Tick() do modo de exibição holográfico do aplicativo conclui uma iteração de atualização, draw, loop presente.</span><span class="sxs-lookup"><span data-stu-id="95cfa-149">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```
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

<span data-ttu-id="95cfa-150">A atualização de exibição do aplicativo holográfica, renderização e loop presente é exatamente o mesmo que quando em execução no HoloLens - exceto que você tem acesso a uma maior quantidade de recursos do sistema no computador desktop.</span><span class="sxs-lookup"><span data-stu-id="95cfa-150">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="95cfa-151">Você pode processar vários triângulos mais, ter mais de passagens de desenho, fazer mais física e usam x64 processos para carregar o conteúdo que requer mais de 2 GB de RAM.</span><span class="sxs-lookup"><span data-stu-id="95cfa-151">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="95cfa-152">Desconectar e encerrar a sessão remota</span><span class="sxs-lookup"><span data-stu-id="95cfa-152">Disconnect and end the remote session</span></span>

<span data-ttu-id="95cfa-153">Para desconectar - por exemplo, quando o usuário clica em um botão de interface do usuário para se desconectar - chamar o HolographicStreamerHelpers Disconnect () e, em seguida, liberar o objeto.</span><span class="sxs-lookup"><span data-stu-id="95cfa-153">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```
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

## <a name="get-the-remoting-player"></a><span data-ttu-id="95cfa-154">Obtenha o player de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="95cfa-154">Get the remoting player</span></span>

<span data-ttu-id="95cfa-155">O player de comunicação remota do Windows Holographic é oferecido na loja de aplicativos do Windows como um ponto de extremidade para hospedar aplicativos de comunicação remota para se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="95cfa-155">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="95cfa-156">Para obter o player de comunicação remota do Windows Holographic, visite a loja de aplicativos do Windows de seu HoloLens, pesquise a comunicação remota e baixar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95cfa-156">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="95cfa-157">O player de comunicação remota inclui um recurso para exibir as estatísticas na tela, que pode ser útil ao depurar aplicativos de host de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="95cfa-157">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="95cfa-158">Notas e recursos</span><span class="sxs-lookup"><span data-stu-id="95cfa-158">Notes and resources</span></span>

<span data-ttu-id="95cfa-159">O modo de exibição holográfico aplicativo precisará de uma maneira de fornecer o seu aplicativo com o dispositivo Direct3D, que deve ser usado para inicializar o espaço holographic.</span><span class="sxs-lookup"><span data-stu-id="95cfa-159">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="95cfa-160">Seu aplicativo deve usar este dispositivo Direct3D para copiar e exibir o quadro de visualização.</span><span class="sxs-lookup"><span data-stu-id="95cfa-160">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="95cfa-161">**Exemplo de código:** Um exemplo de código de comunicação remota holográfica completo está disponível, o que inclui um modo de exibição holográfico do aplicativo que é compatível com projetos de host de comunicação remota para área de trabalho Win32, UWP DirectX e UWP com XAML e comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="95cfa-161">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="95cfa-162">Para fazer isso, acesse aqui:</span><span class="sxs-lookup"><span data-stu-id="95cfa-162">To get it, go here:</span></span>
* [<span data-ttu-id="95cfa-163">Exemplo de código holográfico do Windows para comunicação remota</span><span class="sxs-lookup"><span data-stu-id="95cfa-163">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="95cfa-164">**Observação de depuração:** A biblioteca de comunicação remota holográfica pode lançar exceções de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="95cfa-164">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="95cfa-165">Essas exceções podem estar visíveis na depuração de sessões, dependendo das configurações de exceção do Visual Studio que estão ativas no momento.</span><span class="sxs-lookup"><span data-stu-id="95cfa-165">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="95cfa-166">Essas exceções são capturadas internamente pela biblioteca de comunicação remota holográfica e podem ser ignoradas.</span><span class="sxs-lookup"><span data-stu-id="95cfa-166">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>

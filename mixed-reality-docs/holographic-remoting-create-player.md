---
title: Escrevendo um player de comunicação remota do Holographic personalizado
description: Ao criar um aplicativo de player de comunicação remota Holographic personalizado, você pode criar um aplicativo personalizado capaz de exibir o conteúdo renderizado em um computador remoto para o seu HoloLens 2. Este artigo descreve como isso pode ser feito.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 1f8a0cbe0f6da88c0c5e5a695737d8694020635c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926662"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="09b3c-105">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="09b3c-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="09b3c-106">Este documento descreve a criação de um aplicativo de player personalizado para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="09b3c-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="09b3c-107">Os players personalizados escritos para o HoloLens 2 não são compatíveis com os aplicativos host escritos para o HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="09b3c-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="09b3c-108">Isso implica que ambos os aplicativos devem usar o pacote NuGet versão **2. x**. x.</span><span class="sxs-lookup"><span data-stu-id="09b3c-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="09b3c-109">Ao criar um aplicativo de player de comunicação remota do Holographic personalizado, você pode criar um aplicativo personalizado capaz de exibir [exibições de imersão](app-views.md) em um computador remoto no seu HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="09b3c-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="09b3c-110">Este artigo descreve como isso pode ser feito.</span><span class="sxs-lookup"><span data-stu-id="09b3c-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="09b3c-111">Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="09b3c-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="09b3c-112">Um player de comunicação remota do Holographic permite que seu aplicativo exiba o conteúdo do Holographic [processado](rendering.md) em um computador desktop ou em um dispositivo UWP, como o Xbox One, permitindo o acesso a mais recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="09b3c-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="09b3c-113">Um aplicativo de player de comunicação remota Holographic transmite dados de entrada para um aplicativo de host de comunicação remota Holographic e retorna uma exibição de imersão como fluxo de áudio e vídeo.</span><span class="sxs-lookup"><span data-stu-id="09b3c-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="09b3c-114">A conexão é feita usando Wi-Fi padrão.</span><span class="sxs-lookup"><span data-stu-id="09b3c-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="09b3c-115">Para criar um aplicativo de Player, você usará um pacote NuGet para adicionar a comunicação remota do Holographic ao seu aplicativo UWP e escreverá código para lidar com a conexão e para exibir uma exibição de imersão.</span><span class="sxs-lookup"><span data-stu-id="09b3c-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="09b3c-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="09b3c-116">Prerequisites</span></span>

<span data-ttu-id="09b3c-117">Um bom ponto de partida é um aplicativo UWP de trabalho baseado em DirectX que já tem como alvo a API de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="09b3c-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="09b3c-118">Para obter detalhes, consulte [visão geral do desenvolvimento do DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="09b3c-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="09b3c-119">Se você não tiver um aplicativo existente e quiser começar do zero, o [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md) será um bom ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="09b3c-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="09b3c-120">Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="09b3c-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="09b3c-121">O uso de um [Appartment de thread único](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="09b3c-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="09b3c-122">Ao usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.</span><span class="sxs-lookup"><span data-stu-id="09b3c-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="09b3c-123">Obter o pacote NuGet de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="09b3c-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="09b3c-124">As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09b3c-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="09b3c-125">Abra o projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09b3c-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="09b3c-126">Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="09b3c-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="09b3c-127">No painel que aparece, clique em **procurar** e procure "comunicação remota do Holographic".</span><span class="sxs-lookup"><span data-stu-id="09b3c-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="09b3c-128">Selecione **Microsoft. Holographic. Remoting**, certifique-se de selecionar a versão **2. x. x** mais recente e clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="09b3c-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="09b3c-129">Se a caixa de diálogo **Visualizar** for exibida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="09b3c-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="09b3c-130">A próxima caixa de diálogo exibida é o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="09b3c-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="09b3c-131">Clique em **aceito** para aceitar o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="09b3c-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="09b3c-132">O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API exposta pela comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="09b3c-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="09b3c-133">Modificar o Package. appxmanifest do aplicativo</span><span class="sxs-lookup"><span data-stu-id="09b3c-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="09b3c-134">Para fazer com que o aplicativo reconheça o Microsoft. Holographic. AppRemoting. dll adicionado pelo pacote NuGet, as etapas a seguir precisam ser executadas no projeto:</span><span class="sxs-lookup"><span data-stu-id="09b3c-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="09b3c-135">No Gerenciador de Soluções clique com o botão direito do mouse no arquivo **Package. appxmanifest** e selecione **abrir com...**</span><span class="sxs-lookup"><span data-stu-id="09b3c-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="09b3c-136">Selecione **Editor de XML (texto)** e clique em OK</span><span class="sxs-lookup"><span data-stu-id="09b3c-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="09b3c-137">Adicione as seguintes linhas ao arquivo e salve</span><span class="sxs-lookup"><span data-stu-id="09b3c-137">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="09b3c-138">Criar o contexto do Player</span><span class="sxs-lookup"><span data-stu-id="09b3c-138">Create the player context</span></span>

<span data-ttu-id="09b3c-139">Como primeira etapa, o aplicativo deve criar um contexto de Player.</span><span class="sxs-lookup"><span data-stu-id="09b3c-139">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="09b3c-140">O Holographic Remoting funciona substituindo o tempo de execução do Windows Mixed Reality que faz parte do Windows com um tempo de execução específico de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="09b3c-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="09b3c-141">Isso é feito durante a criação do contexto do Player.</span><span class="sxs-lookup"><span data-stu-id="09b3c-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="09b3c-142">Por esse motivo, qualquer chamada em qualquer API de realidade mista do Windows antes de criar o contexto do player pode resultar em um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="09b3c-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="09b3c-143">A abordagem recomendada é criar o contexto do Player o mais cedo possível antes da interação com qualquer API de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="09b3c-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="09b3c-144">Nunca misture objetos criados ou recuperados por meio de qualquer API de realidade mista do Windows antes da chamada para ```PlayerContext::Create()``` com objetos criados ou recuperados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="09b3c-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="09b3c-145">Em seguida, o HolographicSpace pode ser criado chamando [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span><span class="sxs-lookup"><span data-stu-id="09b3c-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="09b3c-146">Conectar-se ao host</span><span class="sxs-lookup"><span data-stu-id="09b3c-146">Connect to the host</span></span>

<span data-ttu-id="09b3c-147">Depois que o aplicativo de Player estiver pronto para o processamento de conteúdo, pode ser estabelecida uma conexão com o host.</span><span class="sxs-lookup"><span data-stu-id="09b3c-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="09b3c-148">A conexão pode ser estabelecida de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="09b3c-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="09b3c-149">O aplicativo de Player em execução no HoloLens 2 se conecta ao aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="09b3c-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="09b3c-150">O aplicativo host se conecta ao aplicativo de Player em execução no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="09b3c-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="09b3c-151">Para se conectar do aplicativo Player ao host, chame o método ```Connect``` no contexto do Player especificando o nome do host e a porta.</span><span class="sxs-lookup"><span data-stu-id="09b3c-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="09b3c-152">A porta padrão é **8265**.</span><span class="sxs-lookup"><span data-stu-id="09b3c-152">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="09b3c-153">Assim como ocorre C++com qualquer API/WinRT ```Connect``` pode lançar um WinRT:: hresult_error que precisa ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="09b3c-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="09b3c-154">A escuta de conexões de entrada no aplicativo do player pode ser feita chamando o método ```Listen```.</span><span class="sxs-lookup"><span data-stu-id="09b3c-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="09b3c-155">A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada.</span><span class="sxs-lookup"><span data-stu-id="09b3c-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="09b3c-156">A porta de handshake é usada para o handshake inicial.</span><span class="sxs-lookup"><span data-stu-id="09b3c-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="09b3c-157">Os dados são enviados pela porta de transporte.</span><span class="sxs-lookup"><span data-stu-id="09b3c-157">The data is then send over the transport port.</span></span> <span data-ttu-id="09b3c-158">Por padrão, o número da porta **8265** e **8266** são usados.</span><span class="sxs-lookup"><span data-stu-id="09b3c-158">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="09b3c-159">Manipulando eventos relacionados à conexão</span><span class="sxs-lookup"><span data-stu-id="09b3c-159">Handling connection related events</span></span>

<span data-ttu-id="09b3c-160">O ```PlayerContext``` expõe três eventos para monitorar o estado da conexão</span><span class="sxs-lookup"><span data-stu-id="09b3c-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="09b3c-161">Onconnected: disparado quando uma conexão com o host tiver sido estabelecida com êxito.</span><span class="sxs-lookup"><span data-stu-id="09b3c-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="09b3c-162">OnDisconnect: disparado se uma conexão estabelecida for encerrada ou uma conexão não puder ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="09b3c-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="09b3c-163">Os valores possíveis de ```ConnectionFailureReason``` são documentados no [arquivo](#idl)de ```Microsoft.Holographic.AppRemoting.idl```.</span><span class="sxs-lookup"><span data-stu-id="09b3c-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="09b3c-164">Desescutando: quando a escuta de conexões de entrada é iniciada.</span><span class="sxs-lookup"><span data-stu-id="09b3c-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="09b3c-165">Além disso, o estado da conexão pode ser consultado usando a propriedade ```ConnectionState``` no contexto do Player.</span><span class="sxs-lookup"><span data-stu-id="09b3c-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="09b3c-166">Exibir o quadro processado remotamente</span><span class="sxs-lookup"><span data-stu-id="09b3c-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="09b3c-167">Para exibir o conteúdo processado remotamente, chame ```PlayerContext::BlitRemoteFrame()``` ao renderizar um [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="09b3c-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="09b3c-168">```BlitRemoteFrame()``` requer que o buffer de fundo para o HolographicFrame atual seja associado como destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="09b3c-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="09b3c-169">O buffer de fundo pode ser recebido do [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) por meio da propriedade [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .</span><span class="sxs-lookup"><span data-stu-id="09b3c-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="09b3c-170">Quando chamado, ```BlitRemoteFrame()``` copia o último quadro recebido do aplicativo host para o BackBuffer do HolographicFrame.</span><span class="sxs-lookup"><span data-stu-id="09b3c-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="09b3c-171">Além disso, o conjunto de pontos de foco é definido, se o aplicativo remoto tiver especificado um ponto de foco durante a renderização do quadro remoto.</span><span class="sxs-lookup"><span data-stu-id="09b3c-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="09b3c-172">```PlayerContext::BlitRemoteFrame()``` potencialmente substitui o ponto de foco do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="09b3c-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="09b3c-173">Para especificar um ponto de foco de fallback, chame [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes de ```PlayerContext::BlitRemoteFrame()```.</span><span class="sxs-lookup"><span data-stu-id="09b3c-173">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="09b3c-174">Para substituir o ponto de foco remoto, chame [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) após ```PlayerContext::BlitRemoteFrame()```.</span><span class="sxs-lookup"><span data-stu-id="09b3c-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="09b3c-175">Em caso de sucesso, ```BlitRemoteFrame()``` retorna ```BlitResult::Success_Color```.</span><span class="sxs-lookup"><span data-stu-id="09b3c-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="09b3c-176">Caso contrário, ele retornará o motivo da falha:</span><span class="sxs-lookup"><span data-stu-id="09b3c-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="09b3c-177">```BlitResult::Failed_NoRemoteFrameAvailable```: falhou porque nenhum quadro remoto está disponível.</span><span class="sxs-lookup"><span data-stu-id="09b3c-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="09b3c-178">```BlitResult::Failed_NoCamera```: falhou porque nenhuma câmera presente.</span><span class="sxs-lookup"><span data-stu-id="09b3c-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="09b3c-179">```BlitResult::Failed_RemoteFrameTooOld```: falhou porque o quadro remoto é muito antigo (consulte a propriedade PlayerContext:: BlitRemoteFrameTimeout).</span><span class="sxs-lookup"><span data-stu-id="09b3c-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

## <span data-ttu-id="09b3c-180">Opcional: definir BlitRemoteFrameTimeout<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="09b3c-180">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="09b3c-181">```PlayerContext::BlitRemoteFrameTimeout``` tem suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="09b3c-181">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="09b3c-182">A propriedade ```PlayerContext::BlitRemoteFrameTimeout``` especifica a quantidade de tempo que um quadro remoto será reutilizado se nenhum quadro remoto novo for recebido.</span><span class="sxs-lookup"><span data-stu-id="09b3c-182">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="09b3c-183">Um caso de uso comum é habilitar o tempo limite de BlitRemoteFrame para exibir uma tela em branco se nenhum novo quadro for recebido por um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="09b3c-183">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="09b3c-184">Quando habilitado, o tipo de retorno do método ```BlitRemoteFrame``` também pode ser usado para alternar para um conteúdo de fallback processado localmente.</span><span class="sxs-lookup"><span data-stu-id="09b3c-184">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="09b3c-185">Para habilitar o tempo limite, defina o valor da propriedade como uma duração igual ou maior que 100 ms.</span><span class="sxs-lookup"><span data-stu-id="09b3c-185">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="09b3c-186">Para desabilitar o tempo limite, defina a propriedade como duração zero.</span><span class="sxs-lookup"><span data-stu-id="09b3c-186">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="09b3c-187">Se o tempo limite for habilitado e nenhum quadro remoto for recebido para a duração definida, o BlitRemoteFrame falhará e retornará ```Failed_RemoteFrameTooOld``` até que um novo quadro remoto seja recebido.</span><span class="sxs-lookup"><span data-stu-id="09b3c-187">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="09b3c-188">Opcional: obter estatísticas sobre o último quadro remoto</span><span class="sxs-lookup"><span data-stu-id="09b3c-188">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="09b3c-189">Para diagnosticar problemas de desempenho ou de rede, as estatísticas sobre o último quadro remoto podem ser recuperadas por meio da propriedade ```PlayerContext::LastFrameStatistics```.</span><span class="sxs-lookup"><span data-stu-id="09b3c-189">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="09b3c-190">As estatísticas são atualizadas durante a chamada para [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span><span class="sxs-lookup"><span data-stu-id="09b3c-190">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="09b3c-191">Para obter mais detalhes, consulte a documentação ```PlayerFrameStatistics``` no [arquivo](#idl)```Microsoft.Holographic.AppRemoting.idl```.</span><span class="sxs-lookup"><span data-stu-id="09b3c-191">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="09b3c-192">Opcional: canais de dados personalizados</span><span class="sxs-lookup"><span data-stu-id="09b3c-192">Optional: Custom data channels</span></span>

<span data-ttu-id="09b3c-193">Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida.</span><span class="sxs-lookup"><span data-stu-id="09b3c-193">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="09b3c-194">Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="09b3c-194">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="09b3c-195">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09b3c-195">See Also</span></span>
* [<span data-ttu-id="09b3c-196">Escrevendo um aplicativo de host de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="09b3c-196">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="09b3c-197">Canais de dados personalizados de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="09b3c-197">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="09b3c-198">Estabelecendo uma conexão segura com o Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="09b3c-198">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="09b3c-199">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="09b3c-199">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="09b3c-200">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="09b3c-200">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="09b3c-201">Política de privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="09b3c-201">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

---
title: Escrevendo um player de comunicação remota do Holographic personalizado
description: Ao criar um aplicativo de player de comunicação remota Holographic personalizado, você pode criar um aplicativo personalizado capaz de exibir o conteúdo renderizado em um computador remoto para o seu HoloLens 2. Este artigo descreve como isso pode ser feito.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: fdc3d3bbd72d0812377d6a70c975f2111e1a2224
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718090"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="474a1-105">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="474a1-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="474a1-106">Este documento descreve a criação de um aplicativo de player personalizado para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="474a1-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="474a1-107">Os players personalizados escritos para o HoloLens 2 não são compatíveis com os aplicativos host escritos para o HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="474a1-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="474a1-108">Isso implica que ambos os aplicativos devem usar o pacote NuGet versão **2. x**. x.</span><span class="sxs-lookup"><span data-stu-id="474a1-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="474a1-109">Ao criar um aplicativo de player de comunicação remota do Holographic personalizado, você pode criar um aplicativo personalizado capaz de exibir exibições de [imersão](app-views.md) em um computador remoto no seu HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="474a1-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="474a1-110">Este artigo descreve como isso pode ser feito.</span><span class="sxs-lookup"><span data-stu-id="474a1-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="474a1-111">Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="474a1-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="474a1-112">Um player de comunicação remota do Holographic permite que seu aplicativo exiba o conteúdo do Holographic [processado](rendering.md) em um computador desktop ou em um dispositivo UWP, como o Xbox One, permitindo o acesso a mais recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="474a1-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="474a1-113">Um aplicativo de player de comunicação remota Holographic transmite dados de entrada para um aplicativo de host de comunicação remota Holographic e retorna uma exibição de imersão como fluxo de áudio e vídeo.</span><span class="sxs-lookup"><span data-stu-id="474a1-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="474a1-114">A conexão é feita usando Wi-Fi padrão.</span><span class="sxs-lookup"><span data-stu-id="474a1-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="474a1-115">Para criar um aplicativo de Player, você usará um pacote NuGet para adicionar a comunicação remota do Holographic ao seu aplicativo UWP e escreverá código para lidar com a conexão e para exibir uma exibição de imersão.</span><span class="sxs-lookup"><span data-stu-id="474a1-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="474a1-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="474a1-116">Prerequisites</span></span>

<span data-ttu-id="474a1-117">Um bom ponto de partida é um aplicativo UWP de trabalho baseado em DirectX que já tem como alvo a API de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="474a1-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="474a1-118">Para obter detalhes, consulte [visão geral do desenvolvimento do DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="474a1-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="474a1-119">Se você não tiver um aplicativo existente e quiser começar do zero, o [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md) será um bom ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="474a1-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="474a1-120">Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="474a1-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="474a1-121">O uso de um [Appartment de thread único](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="474a1-121">The use of a [single-threaded appartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="474a1-122">Ao usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.</span><span class="sxs-lookup"><span data-stu-id="474a1-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="474a1-123">Obter o pacote NuGet de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="474a1-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="474a1-124">As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="474a1-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="474a1-125">Abra o projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="474a1-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="474a1-126">Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="474a1-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="474a1-127">No painel que aparece, clique em **procurar** e procure "comunicação remota do Holographic".</span><span class="sxs-lookup"><span data-stu-id="474a1-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="474a1-128">Selecione **Microsoft. Holographic. Remoting**, certifique-se de selecionar a versão **2. x. x** mais recente e clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="474a1-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="474a1-129">Se a caixa de diálogo **Visualizar** for exibida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="474a1-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="474a1-130">A próxima caixa de diálogo exibida é o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="474a1-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="474a1-131">Clique em **aceito** para aceitar o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="474a1-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="474a1-132">O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API exposta pela comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="474a1-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="474a1-133">Modificar o Package. appxmanifest do aplicativo</span><span class="sxs-lookup"><span data-stu-id="474a1-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="474a1-134">Para fazer com que o aplicativo reconheça o Microsoft. Holographic. AppRemoting. dll adicionado pelo pacote NuGet, as etapas a seguir precisam ser executadas no projeto:</span><span class="sxs-lookup"><span data-stu-id="474a1-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="474a1-135">No Gerenciador de Soluções clique com o botão direito do mouse no arquivo **Package. appxmanifest** e selecione **abrir com...**</span><span class="sxs-lookup"><span data-stu-id="474a1-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="474a1-136">Selecione **Editor de XML (texto)** e clique em OK</span><span class="sxs-lookup"><span data-stu-id="474a1-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="474a1-137">Adicione as seguintes linhas ao arquivo e salve</span><span class="sxs-lookup"><span data-stu-id="474a1-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="474a1-138">Criar o contexto do Player</span><span class="sxs-lookup"><span data-stu-id="474a1-138">Create the player context</span></span>

<span data-ttu-id="474a1-139">Como primeira etapa, o aplicativo deve criar um contexto de Player.</span><span class="sxs-lookup"><span data-stu-id="474a1-139">As a first step the application should create a player context.</span></span>

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
><span data-ttu-id="474a1-140">O Holographic Remoting funciona substituindo o tempo de execução do Windows Mixed Reality que faz parte do Windows com um tempo de execução específico de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="474a1-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="474a1-141">Isso é feito durante a criação do contexto do Player.</span><span class="sxs-lookup"><span data-stu-id="474a1-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="474a1-142">Por esse motivo, qualquer chamada em qualquer API de realidade mista do Windows antes de criar o contexto do player pode resultar em um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="474a1-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="474a1-143">A abordagem recomendada é criar o contexto do Player o mais cedo possível antes da interação com qualquer API de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="474a1-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="474a1-144">Nunca misture objetos criados ou recuperados por meio de qualquer API de realidade mista do ```PlayerContext::Create()``` Windows antes da chamada para com objetos criados ou recuperados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="474a1-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="474a1-145">Em seguida, o HolographicSpace pode ser criado chamando [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span><span class="sxs-lookup"><span data-stu-id="474a1-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="474a1-146">Conectar-se ao host</span><span class="sxs-lookup"><span data-stu-id="474a1-146">Connect to the host</span></span>

<span data-ttu-id="474a1-147">Depois que o aplicativo de Player estiver pronto para o processamento de conteúdo, pode ser estabelecida uma conexão com o host.</span><span class="sxs-lookup"><span data-stu-id="474a1-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="474a1-148">A conexão pode ser estabelecida de uma das maneiras seguintes:</span><span class="sxs-lookup"><span data-stu-id="474a1-148">The connection can be established in one of the follwing ways:</span></span>
1) <span data-ttu-id="474a1-149">O aplicativo de Player em execução no HoloLens 2 se conecta ao aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="474a1-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="474a1-150">O aplicativo host se conecta ao aplicativo de Player em execução no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="474a1-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="474a1-151">Para se conectar do aplicativo Player ao host, chame o ```Connect``` método no contexto do Player especificando o nome do host e a porta.</span><span class="sxs-lookup"><span data-stu-id="474a1-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="474a1-152">A porta padrão é **8265**.</span><span class="sxs-lookup"><span data-stu-id="474a1-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="474a1-153">Assim como qualquer C++API ```Connect``` /WinRT pode lançar um WinRT:: hresult_error que precisa ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="474a1-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="474a1-154">A escuta de conexões de entrada no aplicativo de player pode ser feita chamando ```Listen``` o método.</span><span class="sxs-lookup"><span data-stu-id="474a1-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="474a1-155">A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada.</span><span class="sxs-lookup"><span data-stu-id="474a1-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="474a1-156">A porta de handshake é usada para o handshake inicial.</span><span class="sxs-lookup"><span data-stu-id="474a1-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="474a1-157">Os dados são enviados pela porta de transporte.</span><span class="sxs-lookup"><span data-stu-id="474a1-157">The data is then send over the transport port.</span></span> <span data-ttu-id="474a1-158">Por padrão, o número da porta **8265** e **8266** são usados.</span><span class="sxs-lookup"><span data-stu-id="474a1-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="474a1-159">Manipulando eventos relacionados à conexão</span><span class="sxs-lookup"><span data-stu-id="474a1-159">Handling connection related events</span></span>

<span data-ttu-id="474a1-160">O ```PlayerContext``` expõe três eventos para monitorar o estado da conexão</span><span class="sxs-lookup"><span data-stu-id="474a1-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="474a1-161">Onconnected: Disparado quando uma conexão com o host foi estabelecida com êxito.</span><span class="sxs-lookup"><span data-stu-id="474a1-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="474a1-162">OnDisconnect: Disparado se uma conexão estabelecida for encerrada ou uma conexão não puder ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="474a1-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="474a1-163">Os ```ConnectionFailureReason``` valores possíveis são documentados ```Microsoft.Holographic.AppRemoting.idl``` no [arquivo](#idl).</span><span class="sxs-lookup"><span data-stu-id="474a1-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="474a1-164">Desescutando: Quando a escuta de conexões de entrada é iniciada.</span><span class="sxs-lookup"><span data-stu-id="474a1-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="474a1-165">Além disso, o estado da conexão pode ser consultado usando a ```ConnectionState``` Propriedade no contexto do Player.</span><span class="sxs-lookup"><span data-stu-id="474a1-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="474a1-166">Exibir o quadro processado remotamente</span><span class="sxs-lookup"><span data-stu-id="474a1-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="474a1-167">Para exibir o conteúdo renderizado remotamente, ```PlayerContext::BlitRemoteFrame()``` chame ao renderizar um [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="474a1-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="474a1-168">```BlitRemoteFrame()```requer que o buffer de fundo para o HolographicFrame atual seja associado como destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="474a1-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="474a1-169">O buffer de fundo pode ser recebido do [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) por meio da propriedade [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .</span><span class="sxs-lookup"><span data-stu-id="474a1-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="474a1-170">Quando chamado, ```BlitRemoteFrame()``` o copia o último quadro recebido do aplicativo host para o BackBuffer do HolographicFrame.</span><span class="sxs-lookup"><span data-stu-id="474a1-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="474a1-171">Além disso, o conjunto de pontos de foco é definido, se o aplicativo remoto tiver especificado um ponto de foco durante a renderização do quadro remoto.</span><span class="sxs-lookup"><span data-stu-id="474a1-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="474a1-172">```PlayerContext::BlitRemoteFrame()```Substitui potencialmente o ponto de foco do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="474a1-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="474a1-173">Para especificar um ponto de foco de fallback, chame [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes ```PlayerContext::BlitRemoteFrame()```de.</span><span class="sxs-lookup"><span data-stu-id="474a1-173">To specifiy a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="474a1-174">Para overrwrite o ponto de foco remoto, chame [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) após ```PlayerContext::BlitRemoteFrame()```.</span><span class="sxs-lookup"><span data-stu-id="474a1-174">To overrwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="474a1-175">Em caso de ```BlitRemoteFrame()``` sucesso ```BlitResult::Success_Color```, retorna.</span><span class="sxs-lookup"><span data-stu-id="474a1-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="474a1-176">Caso contrário, ele retornará o motivo da falha:</span><span class="sxs-lookup"><span data-stu-id="474a1-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="474a1-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Falha porque nenhum quadro remoto está disponível.</span><span class="sxs-lookup"><span data-stu-id="474a1-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="474a1-178">```BlitResult::Failed_NoCamera```: Falha porque nenhuma câmera presente.</span><span class="sxs-lookup"><span data-stu-id="474a1-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="474a1-179">Opcional: Obter estatísticas sobre o último quadro remoto</span><span class="sxs-lookup"><span data-stu-id="474a1-179">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="474a1-180">Para diagnosticar problemas de desempenho ou de rede, as estatísticas sobre o último quadro remoto podem ```PlayerContext::LastFrameStatistics``` ser recuperadas por meio da propriedade.</span><span class="sxs-lookup"><span data-stu-id="474a1-180">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="474a1-181">As estatísticas são atualizadas durante a chamada para [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span><span class="sxs-lookup"><span data-stu-id="474a1-181">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="474a1-182">Para obter mais detalhes, consulte ```PlayerFrameStatistics``` a documentação ```Microsoft.Holographic.AppRemoting.idl``` no [arquivo](#idl).</span><span class="sxs-lookup"><span data-stu-id="474a1-182">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="474a1-183">Opcional: Canais de dados personalizados</span><span class="sxs-lookup"><span data-stu-id="474a1-183">Optional: Custom data channels</span></span>

<span data-ttu-id="474a1-184">Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida.</span><span class="sxs-lookup"><span data-stu-id="474a1-184">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="474a1-185">Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="474a1-185">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="474a1-186">Consulte também</span><span class="sxs-lookup"><span data-stu-id="474a1-186">See Also</span></span>
* [<span data-ttu-id="474a1-187">Escrevendo um aplicativo de host de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="474a1-187">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="474a1-188">Canais de dados de comunicação remota Holographic personalizados</span><span class="sxs-lookup"><span data-stu-id="474a1-188">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="474a1-189">Estabelecendo uma conexão segura com o Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="474a1-189">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="474a1-190">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="474a1-190">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="474a1-191">Termos de licença de software de comunicação remota Holographic</span><span class="sxs-lookup"><span data-stu-id="474a1-191">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="474a1-192">Política de privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="474a1-192">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
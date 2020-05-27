---
title: Como criar um aplicativo remoto de comunicação remota holográfica
description: Ao criar um conteúdo remoto do aplicativo remoto de comunicação remota do Holographic, que é processado em um computador remoto, pode ser transmitido para o HoloLens 2. Este artigo descreve como isso pode ser feito.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 53f370dc32b4fe56eb610b6e5687022e0908f7a8
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866856"
---
# <a name="writing-a-holographic-remoting-remote-app"></a><span data-ttu-id="ed313-105">Como criar um aplicativo remoto de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="ed313-105">Writing a Holographic Remoting remote app</span></span>

>[!IMPORTANT]
><span data-ttu-id="ed313-106">Este documento descreve a criação de um aplicativo remoto para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ed313-106">This document describes the creation of a remote application for HoloLens 2.</span></span> <span data-ttu-id="ed313-107">Os aplicativos remotos para o **HoloLens (1º gen)** devem usar o pacote NuGet versão **1. x**. x.</span><span class="sxs-lookup"><span data-stu-id="ed313-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="ed313-108">Isso significa que os aplicativos remotos escritos para o HoloLens 2 não são compatíveis com o HoloLens 1 e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="ed313-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="ed313-109">A documentação do HoloLens 1 pode ser encontrada [aqui](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="ed313-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="ed313-110">Ao criar um aplicativo remoto de comunicação remota do Holographic, o conteúdo remoto que é processado em um computador remoto pode ser transmitido para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ed313-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="ed313-111">Este artigo descreve como isso pode ser feito.</span><span class="sxs-lookup"><span data-stu-id="ed313-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="ed313-112">Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="ed313-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="ed313-113">A comunicação remota do Holographic permite que um aplicativo direcione o HoloLens 2 com conteúdo Holographic processado em um PC desktop ou em um dispositivo UWP, como o Xbox One, permitindo o acesso a mais recursos do sistema e possibilitando a integração de [exibições de imersão](app-views.md) remotas ao software de PC desktop existente.</span><span class="sxs-lookup"><span data-stu-id="ed313-113">Holographic remoting allows an app to target HoloLens 2 with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="ed313-114">Um aplicativo remoto recebe um fluxo de dados de entrada do HoloLens 2, renderiza o conteúdo em uma exibição de imersão virtual e transmite os quadros de conteúdo de volta para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ed313-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="ed313-115">A conexão é feita usando Wi-Fi padrão.</span><span class="sxs-lookup"><span data-stu-id="ed313-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="ed313-116">A comunicação remota do Holographic é adicionada a um aplicativo de desktop ou UWP por meio de um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ed313-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="ed313-117">É necessário um código adicional que manipula a conexão e é renderizado em uma exibição de imersão.</span><span class="sxs-lookup"><span data-stu-id="ed313-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="ed313-118">Uma conexão de comunicação remota típica terá um mínimo de 50 ms de latência.</span><span class="sxs-lookup"><span data-stu-id="ed313-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="ed313-119">O aplicativo de player pode relatar a latência em tempo real.</span><span class="sxs-lookup"><span data-stu-id="ed313-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ed313-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ed313-120">Prerequisites</span></span>

<span data-ttu-id="ed313-121">Um bom ponto de partida é um aplicativo de área de trabalho baseado em DirectX em funcionamento ou UWP que visa a API de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="ed313-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="ed313-122">Para obter detalhes, consulte [visão geral do desenvolvimento do DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ed313-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="ed313-123">O [modelo de projeto C++ Holographic](creating-a-holographic-directx-project.md) é um bom ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="ed313-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ed313-124">Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="ed313-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="ed313-125">O uso de um [apartamento de thread único](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="ed313-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="ed313-126">Ao usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.</span><span class="sxs-lookup"><span data-stu-id="ed313-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="ed313-127">Obter o pacote NuGet de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="ed313-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="ed313-128">As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ed313-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="ed313-129">Abra o projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ed313-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="ed313-130">Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="ed313-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="ed313-131">No painel que aparece, clique em **procurar** e procure "comunicação remota do Holographic".</span><span class="sxs-lookup"><span data-stu-id="ed313-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="ed313-132">Selecione **Microsoft. Holographic. Remoting**, certifique-se de selecionar a versão **2. x. x** mais recente e clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="ed313-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="ed313-133">Se a caixa de diálogo **Visualizar** for exibida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ed313-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="ed313-134">A próxima caixa de diálogo exibida é o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="ed313-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="ed313-135">Clique em **aceito** para aceitar o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="ed313-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="ed313-136">A versão **1. x. x** do pacote NuGet ainda está disponível para desenvolvedores que desejam direcionar para o HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="ed313-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="ed313-137">Para obter detalhes, consulte [Add Holographic Remoting (HoloLens (1º gen))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="ed313-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="ed313-138">Criar o contexto remoto</span><span class="sxs-lookup"><span data-stu-id="ed313-138">Create the remote context</span></span>

<span data-ttu-id="ed313-139">Como primeira etapa, o aplicativo deve criar um contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="ed313-139">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="ed313-140">O Holographic Remoting funciona substituindo o tempo de execução do Windows Mixed Reality que faz parte do Windows com um tempo de execução específico de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="ed313-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="ed313-141">Isso é feito durante a criação do contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="ed313-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="ed313-142">Por esse motivo, qualquer chamada em qualquer API de realidade mista do Windows antes de criar o contexto remoto pode resultar em um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="ed313-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="ed313-143">A abordagem recomendada é criar o contexto remoto o mais cedo possível antes da interação com qualquer API de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="ed313-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="ed313-144">Nunca misture objetos criados ou recuperados por meio de qualquer API de realidade mista do Windows antes da chamada para CreateRemoteContext com objetos criados ou recuperados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="ed313-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="ed313-145">Em seguida, o espaço Holographic precisa ser criado.</span><span class="sxs-lookup"><span data-stu-id="ed313-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="ed313-146">Não é necessário especificar um CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="ed313-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="ed313-147">Os aplicativos da área de trabalho que não têm um CoreWindow podem apenas passar um ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="ed313-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="ed313-148">Conectar-se ao dispositivo</span><span class="sxs-lookup"><span data-stu-id="ed313-148">Connect to the device</span></span>

<span data-ttu-id="ed313-149">Depois que o aplicativo remoto estiver pronto para renderizar o conteúdo, pode ser estabelecida uma conexão com o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ed313-149">Once the remote app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="ed313-150">A conexão pode ser feita de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="ed313-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="ed313-151">O aplicativo remoto se conecta ao Player em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ed313-151">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="ed313-152">O Player em execução no dispositivo se conecta ao aplicativo remoto.</span><span class="sxs-lookup"><span data-stu-id="ed313-152">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="ed313-153">Para estabelecer uma conexão do aplicativo remoto para o HoloLens 2, chame o ```Connect``` método no contexto remoto especificando o nome do host e a porta.</span><span class="sxs-lookup"><span data-stu-id="ed313-153">To establish a connection from the remote app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="ed313-154">A porta usada pelo Holographic Remoting Player é **8265**.</span><span class="sxs-lookup"><span data-stu-id="ed313-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="ed313-155">Assim como acontece com qualquer API do C++/WinRT, você ```Connect``` pode lançar um WinRT:: hresult_error que precisa ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="ed313-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="ed313-156">Para evitar o uso da projeção de linguagem [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) , o arquivo ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` localizado no pacote NuGet de comunicação remota do Holographic pode ser incluído.</span><span class="sxs-lookup"><span data-stu-id="ed313-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="ed313-157">Ele contém declarações das interfaces COM subjacentes.</span><span class="sxs-lookup"><span data-stu-id="ed313-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="ed313-158">No entanto, o uso de C++/WinRT é recomendado.</span><span class="sxs-lookup"><span data-stu-id="ed313-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="ed313-159">A escuta de conexões de entrada no aplicativo remoto pode ser feita chamando o ```Listen``` método.</span><span class="sxs-lookup"><span data-stu-id="ed313-159">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="ed313-160">A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada.</span><span class="sxs-lookup"><span data-stu-id="ed313-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="ed313-161">A porta de handshake é usada para o handshake inicial.</span><span class="sxs-lookup"><span data-stu-id="ed313-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="ed313-162">Os dados são enviados pela porta de transporte.</span><span class="sxs-lookup"><span data-stu-id="ed313-162">The data is then send over the transport port.</span></span> <span data-ttu-id="ed313-163">Por padrão, **8265** e **8266** são usados.</span><span class="sxs-lookup"><span data-stu-id="ed313-163">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="ed313-164">O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API exposta pela comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="ed313-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="ed313-165">Manipulando eventos específicos de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="ed313-165">Handling Remoting specific events</span></span>

<span data-ttu-id="ed313-166">O contexto remoto expõe três eventos que são importantes para monitorar o estado de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="ed313-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="ed313-167">Onconnected: disparado quando uma conexão com o dispositivo tiver sido estabelecida com êxito.</span><span class="sxs-lookup"><span data-stu-id="ed313-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="ed313-168">OnDisconnect: disparado se uma conexão estabelecida é fechada ou uma conexão não pôde ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="ed313-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="ed313-169">Desescutando: quando a escuta de conexões de entrada é iniciada.</span><span class="sxs-lookup"><span data-stu-id="ed313-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="ed313-170">Além disso, o estado da conexão pode ser consultado usando a ```ConnectionState``` propriedade no contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="ed313-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="ed313-171">Manipulando eventos de fala</span><span class="sxs-lookup"><span data-stu-id="ed313-171">Handling speech events</span></span>

<span data-ttu-id="ed313-172">Usando a interface de fala remota, é possível registrar gatilhos de fala com o HoloLens 2 e tê-los remotos no aplicativo remoto.</span><span class="sxs-lookup"><span data-stu-id="ed313-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="ed313-173">Esse membro adicional é necessário para acompanhar o estado da fala remota.</span><span class="sxs-lookup"><span data-stu-id="ed313-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="ed313-174">Primeiro, a interface de fala remota precisa ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="ed313-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="ed313-175">Usando um método auxiliar assíncrono, você pode inicializar a fala remota.</span><span class="sxs-lookup"><span data-stu-id="ed313-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="ed313-176">Isso deve ser feito de forma assíncrona, pois a inicialização pode levar um tempo considerável.</span><span class="sxs-lookup"><span data-stu-id="ed313-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="ed313-177">[Operações de simultaneidade e assíncronas com c++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explica como criar funções assíncronas com c++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="ed313-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="ed313-178">Há duas maneiras de especificar frases a serem reconhecidas.</span><span class="sxs-lookup"><span data-stu-id="ed313-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="ed313-179">Especificação dentro de um arquivo XML de gramática de fala.</span><span class="sxs-lookup"><span data-stu-id="ed313-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="ed313-180">Consulte [como criar uma gramática XML básica](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="ed313-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="ed313-181">Especifique ao passá-los dentro do vetor do dicionário para ```ApplyParameters``` .</span><span class="sxs-lookup"><span data-stu-id="ed313-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="ed313-182">Dentro do retorno de chamada OnRecognizedSpeech, os eventos de fala podem ser processados:</span><span class="sxs-lookup"><span data-stu-id="ed313-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="ed313-183">Visualizar conteúdo transmitido localmente</span><span class="sxs-lookup"><span data-stu-id="ed313-183">Preview streamed content locally</span></span>

<span data-ttu-id="ed313-184">Para exibir o mesmo conteúdo no aplicativo remoto que é enviado para o dispositivo, o ```OnSendFrame``` evento do contexto remoto pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="ed313-184">To display the same content in the remote app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="ed313-185">O ```OnSendFrame``` evento é disparado toda vez que a biblioteca de comunicação remota do Holographic envia o quadro atual para o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="ed313-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="ed313-186">Esse é o momento ideal para pegar o conteúdo e também blit-lo na janela Desktop ou UWP.</span><span class="sxs-lookup"><span data-stu-id="ed313-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="ed313-187">Reprojeção de profundidade</span><span class="sxs-lookup"><span data-stu-id="ed313-187">Depth Reprojection</span></span>

<span data-ttu-id="ed313-188">A partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0), a comunicação remota Holographic dá suporte à [Reprojeção de profundidade](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="ed313-188">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="ed313-189">Isso requer, além do buffer de cores, também transmitir o buffer de profundidade do aplicativo remoto para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ed313-189">This requires, in addition to the color buffer, to also stream the depth buffer from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="ed313-190">Por padrão, o streaming de buffer de profundidade é habilitado e configurado para usar metade da resolução do buffer de cores.</span><span class="sxs-lookup"><span data-stu-id="ed313-190">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="ed313-191">Isso pode ser alterado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ed313-191">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="ed313-192">Observe que, se os valores padrão não devem ser usados, ```ConfigureDepthVideoStream``` deve ser chamado antes de estabelecer uma conexão com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ed313-192">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="ed313-193">O melhor local é logo após a criação do contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="ed313-193">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="ed313-194">Os valores possíveis para DepthBufferStreamResolution são:</span><span class="sxs-lookup"><span data-stu-id="ed313-194">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="ed313-195">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="ed313-195">Full_Resolution</span></span>
* <span data-ttu-id="ed313-196">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="ed313-196">Half_Resolution</span></span>
* <span data-ttu-id="ed313-197">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="ed313-197">Quarter_Resolution</span></span>
* <span data-ttu-id="ed313-198">Disabled (adicionado com a versão [2.1.3](holographic-remoting-version-history.md#v2.1.3) e, se usado, nenhum fluxo de vídeo de profundidade adicional é criado)</span><span class="sxs-lookup"><span data-stu-id="ed313-198">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="ed313-199">Tenha em mente que o uso de um buffer de profundidade de resolução completa também afeta os requisitos de largura de banda e precisa ser considerado no valor máximo de largura de banda fornecido para o ```CreateRemoteContext``` .</span><span class="sxs-lookup"><span data-stu-id="ed313-199">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="ed313-200">Ao lado de configurar a resolução, você também precisa confirmar um buffer de profundidade por meio de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="ed313-200">Beside configuring the resolution you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="ed313-201">Para verificar se a Reprojeção de profundidade está correclty funcionando no HoloLens 2, você pode habilitar um visualizador de profundidade por meio do portal do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ed313-201">To verify if depth reprojection is correclty working on HoloLens 2 you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="ed313-202">Consulte [verificação de profundidade está definido corretamente](hologram-stability.md#verifying-depth-is-set-correctly) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="ed313-202">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="ed313-203">Opcional: canais de dados personalizados</span><span class="sxs-lookup"><span data-stu-id="ed313-203">Optional: Custom data channels</span></span>

<span data-ttu-id="ed313-204">Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida.</span><span class="sxs-lookup"><span data-stu-id="ed313-204">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="ed313-205">Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ed313-205">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed313-206">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ed313-206">See Also</span></span>
* [<span data-ttu-id="ed313-207">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="ed313-207">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="ed313-208">Canais de dados personalizados de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="ed313-208">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="ed313-209">Estabelecendo uma conexão segura com o Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="ed313-209">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="ed313-210">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="ed313-210">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="ed313-211">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="ed313-211">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="ed313-212">Política de Privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="ed313-212">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

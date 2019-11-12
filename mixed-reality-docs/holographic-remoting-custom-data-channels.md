---
title: Canais de dados de comunicação remota Holographic personalizados
description: Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota Holographic já estabelecida.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 2861c780c5d7e516d5b7ddc757bbcba6da7e6559
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926665"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="acd47-104">Canais de dados de comunicação remota Holographic personalizados</span><span class="sxs-lookup"><span data-stu-id="acd47-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="acd47-105">Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="acd47-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="acd47-106">Use canais de dados personalizados para enviar dados personalizados por meio de uma conexão remota estabelecida.</span><span class="sxs-lookup"><span data-stu-id="acd47-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="acd47-107">Os canais de dados personalizados exigem um aplicativo host personalizado e um aplicativo de player personalizado, pois ele permite a comunicação entre os dois aplicativos personalizados.</span><span class="sxs-lookup"><span data-stu-id="acd47-107">Custom data channels require a custom host app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="acd47-108">Um exemplo simples de pingue-pongue pode ser encontrado nos exemplos de host e de Player dentro do [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="acd47-108">A simple ping-pong example can be found in the host and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="acd47-109">Remova os comentários ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` nos arquivos SampleHostMain. h/SamplePlayerMain. h para habilitar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="acd47-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleHostMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="acd47-110">Criar um canal de dados personalizado</span><span class="sxs-lookup"><span data-stu-id="acd47-110">Create a custom data channel</span></span>


<span data-ttu-id="acd47-111">Para criar um canal de dados personalizado, são necessários os seguintes campos:</span><span class="sxs-lookup"><span data-stu-id="acd47-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="acd47-112">Depois que uma conexão foi estabelecida com êxito, a criação de novos canais de dados pode ser iniciada por meio do lado do host e/ou do lado do jogador.</span><span class="sxs-lookup"><span data-stu-id="acd47-112">After a connection was successfully established, the creation of new data channels can be initiated from either the host side and/or the player side.</span></span> <span data-ttu-id="acd47-113">O RemoteContext e o PlayerContext fornecem um método ```CreateDataChannel()``` para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="acd47-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="acd47-114">O primeiro parâmetro é a ID do canal que é usada para identificar o canal de dados em operações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="acd47-114">The first parameter is the channel ID which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="acd47-115">O segundo parâmetro é a prioridade que especifica a prioridade com a qual os dados desse canal são transferidos para o outro lado.</span><span class="sxs-lookup"><span data-stu-id="acd47-115">The second parameter is the priority which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="acd47-116">O intervalo válido para as IDs de canal é de 0 até e incluindo 63 para o lado do host e 64 até e incluindo 127 para o lado do jogador.</span><span class="sxs-lookup"><span data-stu-id="acd47-116">The valid range for channel IDs is 0 up to and including 63 for the host side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="acd47-117">As prioridades válidas são ```Low```, ```Medium``` ou ```High``` (em ambos os lados).</span><span class="sxs-lookup"><span data-stu-id="acd47-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="acd47-118">Para iniciar a criação de um canal de dados no lado do **host** :</span><span class="sxs-lookup"><span data-stu-id="acd47-118">To initiate the creation of a data channel on the **host** side:</span></span>
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="acd47-119">Para iniciar a criação de um canal de dados no lado do **jogador** :</span><span class="sxs-lookup"><span data-stu-id="acd47-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="acd47-120">Para criar um novo canal de dados personalizado, apenas um lado (host ou Player) precisa chamar o método ```CreateDataChannel```.</span><span class="sxs-lookup"><span data-stu-id="acd47-120">To create a new custom data channel, only one side (either host or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="acd47-121">Manipulando eventos de canal de dados personalizados</span><span class="sxs-lookup"><span data-stu-id="acd47-121">Handling custom data channel events</span></span>

<span data-ttu-id="acd47-122">Para estabelecer um canal de dados personalizado, o evento ```OnDataChannelCreated``` precisa ser tratado (tanto no Player quanto no lado do host).</span><span class="sxs-lookup"><span data-stu-id="acd47-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the host side).</span></span> <span data-ttu-id="acd47-123">Ele é disparado quando um canal de dados do usuário é criado por um dos lados e fornece um objeto ```IDataChannel```, que pode ser usado para enviar e receber dados por esse canal.</span><span class="sxs-lookup"><span data-stu-id="acd47-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="acd47-124">Para registrar um ouvinte no evento ```OnDataChannelCreated```:</span><span class="sxs-lookup"><span data-stu-id="acd47-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="acd47-125">Para ser notificado quando os dados são recebidos, registre-se no evento ```OnDataReceived``` no objeto ```IDataChannel``` fornecido pelo manipulador de ```OnDataChannelCreated```.</span><span class="sxs-lookup"><span data-stu-id="acd47-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="acd47-126">Registre-se no evento ```OnClosed```, para ser notificado quando o canal de dados tiver sido fechado.</span><span class="sxs-lookup"><span data-stu-id="acd47-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a><span data-ttu-id="acd47-127">Enviando dados</span><span class="sxs-lookup"><span data-stu-id="acd47-127">Sending data</span></span>

<span data-ttu-id="acd47-128">Para enviar dados por um canal de dados personalizado, use o método ```IDataChannel::SendData()```.</span><span class="sxs-lookup"><span data-stu-id="acd47-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="acd47-129">O primeiro parâmetro é um ```winrt::array_view<const uint8_t>``` para os dados que devem ser enviados.</span><span class="sxs-lookup"><span data-stu-id="acd47-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="acd47-130">O segundo parâmetro especifica onde os dados devem ser reenviados, até o outro lado reconhecer a recepção.</span><span class="sxs-lookup"><span data-stu-id="acd47-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="acd47-131">No caso de condições de rede inadequadas, o mesmo pacote de dados pode chegar mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="acd47-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="acd47-132">O código de recebimento deve ser capaz de lidar com essa situação.</span><span class="sxs-lookup"><span data-stu-id="acd47-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="acd47-133">Fechando um canal de dados personalizado</span><span class="sxs-lookup"><span data-stu-id="acd47-133">Closing a custom data channel</span></span>

<span data-ttu-id="acd47-134">Para fechar um canal de dados personalizado, use o método ```IDataChannel::Close()```.</span><span class="sxs-lookup"><span data-stu-id="acd47-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="acd47-135">Os dois lados serão notificados pelo evento de ```OnClosed``` depois que o canal de dados personalizado for fechado.</span><span class="sxs-lookup"><span data-stu-id="acd47-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="acd47-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acd47-136">See Also</span></span>
* [<span data-ttu-id="acd47-137">Escrevendo um aplicativo de host de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="acd47-137">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="acd47-138">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="acd47-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="acd47-139">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="acd47-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="acd47-140">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="acd47-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="acd47-141">Política de privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="acd47-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

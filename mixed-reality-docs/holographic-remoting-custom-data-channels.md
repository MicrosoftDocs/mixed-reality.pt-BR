---
title: Canais de dados de comunicação remota Holographic personalizados
description: Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota Holographic já estabelecida.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 9f7f20023d496412b331606e03d0c5110bb4864f
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718080"
---
# <a name="custom-holographic-remoting-data-channels"></a>Canais de dados de comunicação remota Holographic personalizados

>[!NOTE]
>Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

Use canais de dados personalizados para enviar dados personalizados por meio de uma conexão remota estabelecida.

>[!IMPORTANT]
>Os canais de dados personalizados exigem um aplicativo host personalizado e um aplicativo de player personalizado, pois ele permite a comunicação entre os dois aplicativos personalizados.

>[!TIP]
>Um exemplo simples de pingue-pongue pode ser encontrado nos exemplos de host e de Player dentro do [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Remova os ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` comentários nos arquivos SampleHostMain. h/SamplePlayerMain. h para habilitar o código de exemplo.


# <a name="create-a-custom-data-channel"></a>Criar um canal de dados personalizado


Para criar um canal de dados personalizado, são necessários os seguintes campos:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Depois que uma conexão foi estabelecida com êxito, a criação de novos canais de dados pode ser iniciada por meio do lado do host e/ou do lado do jogador. O RemoteContext e o PlayerContext fornecem um ```CreateDataChannel()``` método para fazer isso. O primeiro parâmetro é a ID do canal que é usada para identificar o canal de dados em operações susequent. O segundo parâmetro é a prioridade que especifica a prioridade com a qual os dados desse canal são transferidos para o outro lado. O intervalo válido para as IDs de canal é de 0 até e incluindo 63 para o lado do host e 64 até e incluindo 127 para o lado do jogador. As prioridades válidas ```Medium``` são ```High``` ```Low```ou (em ambos os lados).

Para iniciar a criação de um canal de dados no lado do **host** :
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Para iniciar a criação de um canal de dados no lado do **jogador** :
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Para criar um novo canal de dados personalizado, apenas um lado (host ou Player) precisa chamar o ```CreateDataChannel``` método.

## <a name="handling-custom-data-channel-events"></a>Manipulando eventos de canal de dados personalizados

Para estabelecer um canal de dados personalizado, ```OnDataChannelCreated``` o evento precisa ser tratado (tanto no Player quanto no lado do host). Ele é disparado quando um canal de dados do usuário é criado por um ```IDataChannel``` dos lados e fornece um objeto, que pode ser usado para enviar e receber dados por esse canal.

Para registrar um ouvinte no ```OnDataChannelCreated``` evento:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Para ser notificado quando os dados são recebidos, registre ```OnDataReceived``` -se ```IDataChannel``` no evento no objeto fornecido ```OnDataChannelCreated``` pelo manipulador. Registre-se ```OnClosed``` no evento para ser notificado quando o canal de dados tiver sido fechado.

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

## <a name="sending-data"></a>Enviando dados

Para enviar dados por um canal de dados personalizado, use ```IDataChannel::SendData()``` o método. O primeiro parâmetro é um ```winrt::array_view<const uint8_t>``` para os dados que devem ser enviados. O segundo parâmetro especifica wheter os dados devem ser reenviados, até o outro lado reconhecer a recepção. 

>[!IMPORTANT]
>No caso de condições de rede inadequadas, o mesmo pacote de dados pode chegar mais de uma vez. O código de recebimento deve ser capaz de lidar com essa situação.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Fechando um canal de dados personalizado

Para fechar um canal de dados personalizado, use ```IDataChannel::Close()``` o método. Os dois lados serão notificados pelo ```OnClosed``` evento depois que o canal de dados personalizado for fechado.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Consulte também
* [Escrevendo um aplicativo de host de comunicação remota do Holographic](holographic-remoting-create-host.md)
* [Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota Holographic](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
---
title: Canais de dados de comunicação remota Holographic personalizados
description: Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota Holographic já estabelecida.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 8bfa19b7af0f3429130aabf70d9d11083bc56a52
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092299"
---
# <a name="custom-holographic-remoting-data-channels"></a>Canais de dados de comunicação remota Holographic personalizados

>[!NOTE]
>Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

Use canais de dados personalizados para enviar dados personalizados por meio de uma conexão remota estabelecida.

>[!IMPORTANT]
>Os canais de dados personalizados exigem um aplicativo remoto personalizado e um aplicativo de player personalizado, pois ele permite a comunicação entre os dois aplicativos personalizados.

>[!TIP]
>Um exemplo simples de pingue-pongue pode ser encontrado nos exemplos remoto e de Player dentro do [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Remova os comentários ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` nos arquivos SampleRemoteMain. h/SamplePlayerMain. h para habilitar o código de exemplo.


## <a name="create-a-custom-data-channel"></a>Criar um canal de dados personalizado


Para criar um canal de dados personalizado, são necessários os seguintes campos:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Depois que uma conexão foi estabelecida com êxito, a criação de novos canais de dados pode ser iniciada tanto do lado remoto quanto do lado do jogador. O RemoteContext e o PlayerContext fornecem um método ```CreateDataChannel()``` para fazer isso. O primeiro parâmetro é a ID do canal que é usada para identificar o canal de dados em operações subsequentes. O segundo parâmetro é a prioridade que especifica a prioridade com a qual os dados desse canal são transferidos para o outro lado. O intervalo válido para as IDs de canal é de 0 até e incluindo 63 para o lado remoto e 64 até e incluindo 127 para o lado do jogador. As prioridades válidas são ```Low```, ```Medium``` ou ```High``` (em ambos os lados).

Para iniciar a criação de um canal de dados no lado **remoto** :
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Para iniciar a criação de um canal de dados no lado do **jogador** :
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Para criar um novo canal de dados personalizado, apenas um lado (remoto ou Player) precisa chamar o método ```CreateDataChannel```.

## <a name="handling-custom-data-channel-events"></a>Manipulando eventos de canal de dados personalizados

Para estabelecer um canal de dados personalizado, o evento ```OnDataChannelCreated``` precisa ser tratado (tanto no Player quanto no lado remoto). Ele é disparado quando um canal de dados do usuário é criado por um dos lados e fornece um objeto ```IDataChannel```, que pode ser usado para enviar e receber dados por esse canal.

Para registrar um ouvinte no evento ```OnDataChannelCreated```:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Para ser notificado quando os dados são recebidos, registre-se no evento ```OnDataReceived``` no objeto ```IDataChannel``` fornecido pelo manipulador de ```OnDataChannelCreated```. Registre-se no evento ```OnClosed```, para ser notificado quando o canal de dados tiver sido fechado.

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

Para enviar dados por um canal de dados personalizado, use o método ```IDataChannel::SendData()```. O primeiro parâmetro é um ```winrt::array_view<const uint8_t>``` para os dados que devem ser enviados. O segundo parâmetro especifica onde os dados devem ser reenviados, até o outro lado reconhecer a recepção. 

>[!IMPORTANT]
>No caso de condições de rede inadequadas, o mesmo pacote de dados pode chegar mais de uma vez. O código de recebimento deve ser capaz de lidar com essa situação.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Fechando um canal de dados personalizado

Para fechar um canal de dados personalizado, use o método ```IDataChannel::Close()```. Os dois lados serão notificados pelo evento de ```OnClosed``` depois que o canal de dados personalizado for fechado.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Consulte também
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic](holographic-remoting-create-host.md)
* [Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

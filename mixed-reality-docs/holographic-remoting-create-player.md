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
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado

>[!IMPORTANT]
>Este documento descreve a criação de um aplicativo de player personalizado para o HoloLens 2. Os players personalizados escritos para o HoloLens 2 não são compatíveis com os aplicativos host escritos para o HoloLens 1. Isso implica que ambos os aplicativos devem usar o pacote NuGet versão **2. x**. x.

Ao criar um aplicativo de player de comunicação remota do Holographic personalizado, você pode criar um aplicativo personalizado capaz de exibir exibições de [imersão](app-views.md) em um computador remoto no seu HoloLens 2. Este artigo descreve como isso pode ser feito. Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Um player de comunicação remota do Holographic permite que seu aplicativo exiba o conteúdo do Holographic [processado](rendering.md) em um computador desktop ou em um dispositivo UWP, como o Xbox One, permitindo o acesso a mais recursos do sistema. Um aplicativo de player de comunicação remota Holographic transmite dados de entrada para um aplicativo de host de comunicação remota Holographic e retorna uma exibição de imersão como fluxo de áudio e vídeo. A conexão é feita usando Wi-Fi padrão. Para criar um aplicativo de Player, você usará um pacote NuGet para adicionar a comunicação remota do Holographic ao seu aplicativo UWP e escreverá código para lidar com a conexão e para exibir uma exibição de imersão. 

## <a name="prerequisites"></a>Pré-requisitos

Um bom ponto de partida é um aplicativo UWP de trabalho baseado em DirectX que já tem como alvo a API de realidade mista do Windows. Para obter detalhes, consulte [visão geral do desenvolvimento do DirectX](directx-development-overview.md). Se você não tiver um aplicativo existente e quiser começar do zero, o [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md) será um bom ponto de partida.

>[!IMPORTANT]
>Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)multi-threaded. O uso de um [Appartment de thread único](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução. Ao usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obter o pacote NuGet de comunicação remota do Holographic

As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.
1. Abra o projeto no Visual Studio.
2. Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**
3. No painel que aparece, clique em **procurar** e procure "comunicação remota do Holographic".
4. Selecione **Microsoft. Holographic. Remoting**, certifique-se de selecionar a versão **2. x. x** mais recente e clique em **instalar**.
5. Se a caixa de diálogo **Visualizar** for exibida, clique em **OK**.
6. A próxima caixa de diálogo exibida é o contrato de licença. Clique em **aceito** para aceitar o contrato de licença.

>[!IMPORTANT]
><a name="idl"></a>O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API exposta pela comunicação remota do Holographic.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modificar o Package. appxmanifest do aplicativo

Para fazer com que o aplicativo reconheça o Microsoft. Holographic. AppRemoting. dll adicionado pelo pacote NuGet, as etapas a seguir precisam ser executadas no projeto:

1. No Gerenciador de Soluções clique com o botão direito do mouse no arquivo **Package. appxmanifest** e selecione **abrir com...**
2. Selecione **Editor de XML (texto)** e clique em OK
3. Adicione as seguintes linhas ao arquivo e salve
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
## <a name="create-the-player-context"></a>Criar o contexto do Player

Como primeira etapa, o aplicativo deve criar um contexto de Player.

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
>O Holographic Remoting funciona substituindo o tempo de execução do Windows Mixed Reality que faz parte do Windows com um tempo de execução específico de comunicação remota. Isso é feito durante a criação do contexto do Player. Por esse motivo, qualquer chamada em qualquer API de realidade mista do Windows antes de criar o contexto do player pode resultar em um comportamento inesperado. A abordagem recomendada é criar o contexto do Player o mais cedo possível antes da interação com qualquer API de realidade misturada. Nunca misture objetos criados ou recuperados por meio de qualquer API de realidade mista do ```PlayerContext::Create()``` Windows antes da chamada para com objetos criados ou recuperados posteriormente.

Em seguida, o HolographicSpace pode ser criado chamando [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>Conectar-se ao host

Depois que o aplicativo de Player estiver pronto para o processamento de conteúdo, pode ser estabelecida uma conexão com o host.

A conexão pode ser estabelecida de uma das maneiras seguintes:
1) O aplicativo de Player em execução no HoloLens 2 se conecta ao aplicativo host.
2) O aplicativo host se conecta ao aplicativo de Player em execução no HoloLens 2.

Para se conectar do aplicativo Player ao host, chame o ```Connect``` método no contexto do Player especificando o nome do host e a porta. A porta padrão é **8265**.

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
>Assim como qualquer C++API ```Connect``` /WinRT pode lançar um WinRT:: hresult_error que precisa ser manipulado.

A escuta de conexões de entrada no aplicativo de player pode ser feita chamando ```Listen``` o método. A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada. A porta de handshake é usada para o handshake inicial. Os dados são enviados pela porta de transporte. Por padrão, o número da porta **8265** e **8266** são usados.

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


## <a name="handling-connection-related-events"></a>Manipulando eventos relacionados à conexão

O ```PlayerContext``` expõe três eventos para monitorar o estado da conexão
1) Onconnected: Disparado quando uma conexão com o host foi estabelecida com êxito.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnect: Disparado se uma conexão estabelecida for encerrada ou uma conexão não puder ser estabelecida.
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
>Os ```ConnectionFailureReason``` valores possíveis são documentados ```Microsoft.Holographic.AppRemoting.idl``` no [arquivo](#idl).

3) Desescutando: Quando a escuta de conexões de entrada é iniciada.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Além disso, o estado da conexão pode ser consultado usando a ```ConnectionState``` Propriedade no contexto do Player.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Exibir o quadro processado remotamente

Para exibir o conteúdo renderizado remotamente, ```PlayerContext::BlitRemoteFrame()``` chame ao renderizar um [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). 

```BlitRemoteFrame()```requer que o buffer de fundo para o HolographicFrame atual seja associado como destino de renderização. O buffer de fundo pode ser recebido do [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) por meio da propriedade [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .

Quando chamado, ```BlitRemoteFrame()``` o copia o último quadro recebido do aplicativo host para o BackBuffer do HolographicFrame. Além disso, o conjunto de pontos de foco é definido, se o aplicativo remoto tiver especificado um ponto de foco durante a renderização do quadro remoto.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()```Substitui potencialmente o ponto de foco do quadro atual. 
>- Para especificar um ponto de foco de fallback, chame [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes ```PlayerContext::BlitRemoteFrame()```de. 
>- Para overrwrite o ponto de foco remoto, chame [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) após ```PlayerContext::BlitRemoteFrame()```.

Em caso de ```BlitRemoteFrame()``` sucesso ```BlitResult::Success_Color```, retorna. Caso contrário, ele retornará o motivo da falha:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: Falha porque nenhum quadro remoto está disponível.
- ```BlitResult::Failed_NoCamera```: Falha porque nenhuma câmera presente.

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Opcional: Obter estatísticas sobre o último quadro remoto

Para diagnosticar problemas de desempenho ou de rede, as estatísticas sobre o último quadro remoto podem ```PlayerContext::LastFrameStatistics``` ser recuperadas por meio da propriedade. As estatísticas são atualizadas durante a chamada para [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Para obter mais detalhes, consulte ```PlayerFrameStatistics``` a documentação ```Microsoft.Holographic.AppRemoting.idl``` no [arquivo](#idl).

## <a name="optional-custom-data-channels"></a>Opcional: Canais de dados personalizados

Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida. Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.

## <a name="see-also"></a>Consulte também
* [Escrevendo um aplicativo de host de comunicação remota do Holographic](holographic-remoting-create-host.md)
* [Canais de dados de comunicação remota Holographic personalizados](holographic-remoting-custom-data-channels.md)
* [Estabelecendo uma conexão segura com o Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota Holographic](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
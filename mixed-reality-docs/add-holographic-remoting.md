---
title: Adicionar comunicação remota do Holographic
description: Explica como usar a comunicação remota do Holographic para renderizar hologramas em um HoloLens pela rede.
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Realidade mista do Windows, hologramas, comunicação remota Holographic, renderização remota, renderização de rede, HoloLens, hologramas remotos
ms.openlocfilehash: 8d645f634ff0fc820893f5554fd602aa3a2f38e3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829626"
---
# <a name="add-holographic-remoting"></a>Adicionar comunicação remota do Holographic

## <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> Mais diretrizes específicas para o HoloLens 2 em [breve](index.md#news-and-notes).

Os desenvolvedores de HoloLens que usam a comunicação remota do Holographic precisarão atualizar seus aplicativos para torná-los compatíveis com o HoloLens 2.  Isso exigirá uma nova versão do pacote NuGet de comunicação remota do Holographic que ainda não está disponível publicamente.  Se um aplicativo que usa o pacote NuGet do HoloLens tentar se conectar ao Player de comunicação remota do Holographic no HoloLens 2, a conexão falhará.  Assista a esta página para obter atualizações depois que o pacote NuGet do HoloLens 2 estiver disponível.

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Adicionar a comunicação remota do Holographic ao seu aplicativo da área de trabalho ou UWP

Esta página descreve como adicionar o Holographic Remoting a um aplicativo desktop ou UWP.

A comunicação remota do Holographic permite que seu aplicativo direcione um HoloLens com conteúdo Holographic hospedado em um computador desktop ou em um dispositivo UWP, como o Xbox One, permitindo o acesso a mais recursos do sistema e possibilitando a integração de exibições de [imersão](app-views.md) remotas ao software de PC desktop existente. Um aplicativo host de comunicação remota recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição de imersão virtual e transmite quadros de conteúdo de volta para o HoloLens. A conexão é feita usando Wi-Fi padrão. Para usar a comunicação remota, você usará um pacote NuGet para adicionar o Holographic Remoting ao seu aplicativo de área de trabalho ou UWP e escreverá código para lidar com a conexão e para renderizar em uma exibição de imersão. As bibliotecas auxiliares são incluídas no exemplo de código que simplificam a tarefa de lidar com a conexão do dispositivo.

Uma conexão de comunicação remota típica terá um mínimo de 50 ms de latência. O aplicativo de player pode relatar a latência em tempo real.

>[!NOTE]
>Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.

### <a name="get-the-remoting-nuget-packages"></a>Obter os pacotes de NuGet de comunicação remota

Siga estas etapas para obter o pacote NuGet para a comunicação remota do Holographic e adicione uma referência do seu projeto:
1. Vá para seu projeto no Visual Studio.
2. Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**
3. No painel que aparece, clique em **procurar** e procure "comunicação remota do Holographic".
4. Selecione **Microsoft. Holographic. Remoting** e clique em **instalar**.
5. Se a caixa de diálogo **Visualizar** for exibida, clique em **OK**.
6. A próxima caixa de diálogo exibida é o contrato de licença. Clique em **aceito** para aceitar o contrato de licença.

### <a name="create-the-holographicstreamerhelpers"></a>Criar o HolographicStreamerHelpers

Primeiro, precisamos de uma instância de HolographicStreamerHelpers. Adicione isso à classe que tratará de comunicação remota.

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Você também precisará acompanhar o estado da conexão. Se você quiser renderizar a visualização, precisará ter uma textura para copiá-la para. Você também precisa de algumas coisas como um bloqueio de estado de conexão, alguma maneira de armazenar o endereço IP do HoloLens e assim por diante.

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Inicializar o HolographicStreamerHelpers e conectar-se ao HoloLens

Para se conectar a um dispositivo HoloLens, crie uma instância do HolographicStreamerHelpers e conecte-se ao endereço IP de destino. Você precisará definir o tamanho do quadro de vídeo para corresponder à largura e altura de exibição do HoloLens, pois a biblioteca de comunicação remota Holographic espera que as resoluções do codificador e do decodificador correspondam exatamente.

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

A conexão do dispositivo é assíncrona. Seu aplicativo precisa fornecer manipuladores de eventos para eventos de conexão, desconexão e quadros de envio.

O evento onconnected pode atualizar a interface do usuário, iniciar a renderização e assim por diante. Em nosso exemplo de código de área de trabalho, atualizamos o título da janela com uma mensagem "conectada".

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

O evento ondisconnectd pode lidar com a reconexão, as atualizações da interface do usuário e assim por diante. Neste exemplo, reconectamos se houver uma falha transitória.

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

Quando o componente de comunicação remota está pronto para enviar um quadro, seu aplicativo recebe uma oportunidade de fazer uma cópia dele no SendFrameEvent. Aqui, copiamos o quadro em uma cadeia de permuta para que possamos exibi-lo em uma janela de visualização.

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

### <a name="render-holographic-content"></a>Renderizar conteúdo Holographic

Para renderizar o conteúdo usando comunicação remota, você configura um IFrameworkView virtual em seu aplicativo de área de trabalho ou UWP e processa os quadros Holographic da comunicação remota. Todas as APIs Holographic do Windows são usadas da mesma forma por essa exibição, mas elas são configuradas de forma ligeiramente diferente.

Em vez de criá-los por conta própria, os componentes de espaço e fala do Holographic vêm de sua classe HolographicRemotingHelpers:

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Em vez de usar um loop de atualização dentro de um método Run, você fornece atualizações em escala do loop principal de seu aplicativo de desktop ou UWP. Isso permite que seu aplicativo da área de trabalho ou UWP permaneça no controle do processamento de mensagens.

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

O método Tick () da exibição do aplicativo Holographic conclui uma iteração do loop Update, Draw e Present.

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

O loop de atualização de exibição do aplicativo Holographic, render e Present é exatamente o mesmo que é quando executado no HoloLens, exceto pelo fato de que você tem acesso a uma quantidade muito maior de recursos do sistema no seu PC desktop. Você pode renderizar muitos triângulos, ter mais passagens de desenho, realizar mais física e usar processos x64 para carregar o conteúdo que exige mais de 2 GB de RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Desconectar e encerrar a sessão remota

Para desconectar-por exemplo, quando o usuário clica em um botão da interface do usuário para desconectar-chamada Disconnect () no HolographicStreamerHelpers e, em seguida, libera o objeto.

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

## <a name="get-the-remoting-player"></a>Obter o reprodutor de comunicação remota

O player de comunicação remota do Windows Holographic é oferecido na loja de aplicativos do Windows como um ponto de extremidade para aplicativos de host remotos se conectarem ao. Para obter o Windows Holographic Remoting Player, visite a Windows App Store do seu HoloLens, pesquise por comunicação remota e baixe o aplicativo. O player de comunicação remota inclui um recurso para exibir estatísticas na tela, o que pode ser útil ao depurar aplicativos de host de comunicação remota.

## <a name="notes-and-resources"></a>Notas e recursos

A exibição do aplicativo Holographic precisará de uma maneira de fornecer seu aplicativo com o dispositivo Direct3D, que deve ser usado para inicializar o espaço do Holographic. Seu aplicativo deve usar este dispositivo Direct3D para copiar e exibir o quadro de visualização.

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Exemplo de código:** Um exemplo de código remoto Holographic completo está disponível, que inclui uma exibição de aplicativo Holographic compatível com projetos de host remoto e de comunicação remota para desktop Win32, UWP DirectX e UWP com XAML. Para obtê-lo, acesse:
* [Exemplo de código do Windows Holographic para comunicação remota](https://github.com/Microsoft/HoloLensCompanionKit/)

**Observação de depuração:** A biblioteca de comunicação remota do Holographic pode gerar exceções de primeira chance. Essas exceções podem ser visíveis em sessões de depuração, dependendo das configurações de exceção do Visual Studio que estão ativas no momento. Essas exceções são detectadas internamente pela biblioteca de comunicação remota do Holographic e podem ser ignoradas.

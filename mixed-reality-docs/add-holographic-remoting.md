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
# <a name="add-holographic-remoting"></a>Adicionar holográfica remoting

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Adicionar remoting holográfica à sua área de trabalho ou um aplicativo UWP

Esta página descreve como adicionar Remoting Holographic para uma área de trabalho ou um aplicativo UWP.

Comunicação remota holográfica permite que seu aplicativo para ter como destino um HoloLens com holográfico conteúdo hospedado em um desktop PC ou em um dispositivo UWP como o Xbox One, permitindo o acesso a mais recursos do sistema e torná-lo possível integrar remoto [exibições imersivas](app-views.md) para o software de PC do desktop existente. Um aplicativo de host de comunicação remota recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em um modo de exibição virtual envolvente e transmite o conteúdo quadros de volta para o HoloLens. A conexão é feita usando o padrão de Wi-Fi. Para usar a comunicação remota, você usar um pacote do NuGet para adicionar remoting holográfica a sua área de trabalho ou um aplicativo UWP e escrever código para lidar com a conexão e a renderização de um modo de exibição envolvente. Bibliotecas auxiliares estão incluídas no exemplo de código que simplificam a tarefa de lidar com a conexão do dispositivo.

Uma conexão de comunicação remota típica terá baixo como 50 ms de latência. O aplicativo de player pode relatar a latência em tempo real.

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

### <a name="get-the-remoting-nuget-packages"></a>Obter a comunicação remota pacotes do NuGet

Siga estas etapas para obter o pacote do NuGet para comunicação remota holográfica e adicione uma referência do seu projeto:
1. Vá para seu projeto no Visual Studio.
2. Clique com botão direito no nó do projeto e selecione **gerenciar pacotes NuGet...**
3. No painel que aparece, clique em **procurar** e, em seguida, pesquise por "Holográfica a comunicação remota".
4. Selecione **Microsoft.Holographic.Remoting** e clique em **instalar**.
5. Se o **versão prévia** caixa de diálogo for exibida, clique em **Okey**.
6. A próxima caixa de diálogo que aparece é o contrato de licença. Clique em **aceito** para aceitar o contrato de licença.

### <a name="create-the-holographicstreamerhelpers"></a>Criar o HolographicStreamerHelpers

Primeiro, precisamos de uma instância de HolographicStreamerHelpers. Adicione isso à classe que manipulará a comunicação remota.

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Você também será necessário controlar o estado da conexão. Se você deseja renderizar a visualização, você precisa ter uma textura para copiá-lo para. Você também precisa de alguns itens como um bloqueio de estado de conexão, alguma forma de armazenar o endereço IP do HoloLens e assim por diante.

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Inicializar HolographicStreamerHelpers e conecte-se ao HoloLens

Para se conectar a um dispositivo HoloLens, crie uma instância de HolographicStreamerHelpers e conecte-se para o endereço IP de destino. Você precisará definir o tamanho do quadro de vídeo para coincidir com a largura da exibição HoloLens e a altura, porque a biblioteca de comunicação remota holográfica espera que as resoluções de codificador e decodificador de uma correspondência exata.

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

A conexão do dispositivo é assíncrona. Necessidades de seu aplicativo para fornecer manipuladores de eventos para conectar, desconectar e quadro enviar eventos.

O evento OnConnected pode atualizar a interface do usuário, iniciar a renderização e assim por diante. Em nosso exemplo de código de área de trabalho, podemos atualizar o título da janela com uma mensagem "conectada".

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

O evento OnDisconnected pode lidar com a reconexão, atualizações de interface do usuário e assim por diante. Neste exemplo, podemos reconexão se houver uma falha temporária.

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

Quando o componente de comunicação remota estiver pronto para enviar um quadro, seu aplicativo é fornecido a oportunidade de fazer uma cópia no SendFrameEvent. Aqui, podemos copiar o quadro para uma cadeia de troca para que podemos pode exibi-lo em uma janela de visualização.

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

### <a name="render-holographic-content"></a>Renderizar conteúdo holográfico

Para renderizar conteúdo usando a comunicação remota, você configura um virtual IFrameworkView dentro de sua área de trabalho ou um aplicativo UWP e processar holográfico quadros de comunicação remota. Todas as APIs do Windows Holographic são usados que da mesma forma por este modo de exibição, mas ele é definida um pouco diferente.

Em vez de criá-las por conta própria, os componentes de fala e espaço holográfico provenientes de sua classe HolographicRemotingHelpers:

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Em vez de usar um loop de atualização dentro de um método de execução, você fornecer atualizações de escala do loop principal do seu desktop ou um aplicativo UWP. Isso permite que seu computador desktop ou um aplicativo UWP para manter o controle do processamento de mensagens.

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Método de Tick() do modo de exibição holográfico do aplicativo conclui uma iteração de atualização, draw, loop presente.

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

A atualização de exibição do aplicativo holográfica, renderização e loop presente é exatamente o mesmo que quando em execução no HoloLens - exceto que você tem acesso a uma maior quantidade de recursos do sistema no computador desktop. Você pode processar vários triângulos mais, ter mais de passagens de desenho, fazer mais física e usam x64 processos para carregar o conteúdo que requer mais de 2 GB de RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Desconectar e encerrar a sessão remota

Para desconectar - por exemplo, quando o usuário clica em um botão de interface do usuário para se desconectar - chamar o HolographicStreamerHelpers Disconnect () e, em seguida, liberar o objeto.

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

## <a name="get-the-remoting-player"></a>Obtenha o player de comunicação remota

O player de comunicação remota do Windows Holographic é oferecido na loja de aplicativos do Windows como um ponto de extremidade para hospedar aplicativos de comunicação remota para se conectar ao. Para obter o player de comunicação remota do Windows Holographic, visite a loja de aplicativos do Windows de seu HoloLens, pesquise a comunicação remota e baixar o aplicativo. O player de comunicação remota inclui um recurso para exibir as estatísticas na tela, que pode ser útil ao depurar aplicativos de host de comunicação remota.

## <a name="notes-and-resources"></a>Notas e recursos

O modo de exibição holográfico aplicativo precisará de uma maneira de fornecer o seu aplicativo com o dispositivo Direct3D, que deve ser usado para inicializar o espaço holographic. Seu aplicativo deve usar este dispositivo Direct3D para copiar e exibir o quadro de visualização.

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Exemplo de código:** Um exemplo de código de comunicação remota holográfica completo está disponível, o que inclui um modo de exibição holográfico do aplicativo que é compatível com projetos de host de comunicação remota para área de trabalho Win32, UWP DirectX e UWP com XAML e comunicação remota. Para fazer isso, acesse aqui:
* [Exemplo de código holográfico do Windows para comunicação remota](https://github.com/Microsoft/HoloLensCompanionKit/)

**Observação de depuração:** A biblioteca de comunicação remota holográfica pode lançar exceções de primeira chance. Essas exceções podem estar visíveis na depuração de sessões, dependendo das configurações de exceção do Visual Studio que estão ativas no momento. Essas exceções são capturadas internamente pela biblioteca de comunicação remota holográfica e podem ser ignoradas.

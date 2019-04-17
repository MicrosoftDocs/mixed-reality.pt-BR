---
title: Obtendo um HolographicSpace
description: Explica a API HolographicSpace, um conceito central para renderização holográfica e entrada espacial.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, espacial de entrada, renderização, trocar a cadeia, quadro holográfico, loop de atualização, loop do jogo, quadro de referência, locatability, código de exemplo e instruções passo a passo
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591016"
---
# <a name="getting-a-holographicspace"></a>Obtendo um HolographicSpace

O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> classe é o seu portal para o mundo holographic. Controla a renderização imersiva, fornece dados de câmera e fornece acesso às APIs de raciocínio espacial. Você criará um para seu aplicativo UWP <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> ou HWND do seu aplicativo Win32.

## <a name="set-up-the-holographic-space"></a>Configurar o espaço holográfico

Criar o objeto de espaço holográfica é a primeira etapa para tornar seu aplicativo de realidade mista do Windows. Renderizam aplicativos tradicionais do Windows para uma cadeia de troca do Direct3D criada para a janela principal do modo de exibição de seu aplicativos. A cadeia de troca é exibida em um slate na interface do usuário holographic. Para tornar seu modo de exibição do aplicativo holographic em vez de um slate 2D, crie um espaço holographic para sua janela principal, em vez de uma cadeia de troca. Apresentar holográfico quadros que são criados por esse espaço holográfico coloca seu aplicativo no modo de renderização em tela inteira.

Para um **aplicativo UWP** [a partir de *modelo de aplicativo de 11 holográfica DirectX (Windows Universal)*](creating-a-holographic-directx-project.md), procure esse código no **SetWindow** método na AppView.cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Para um **aplicativo Win32** [a partir de *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), examinar **App::CreateWindowAndHolographicSpace** para um exemplo de como criar um HWND e, em seguida, convertê-la em um HWND imersivo, criando um associado <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

Agora que você já adquiriu um HolographicSpace para o CoreWindow do UWP ou Win32 HWND, você usará esse HolographicSpace para manipular câmeras holográfica, criar sistemas de coordenadas e fazer a renderização holográfica. O espaço de holográfico atual é usado em vários lugares no modelo de DirectX:
* O **DeviceResources** classe precisa obter algumas informações do objeto HolographicSpace para criar o dispositivo Direct3D. Isso é a ID do adaptador DXGI associada à exibição holográfica. O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> classe usa o dispositivo de Direct3D 11 do seu aplicativo para criar e gerenciar recursos com base em dispositivo, como os buffers de voltar para cada câmera holográfica. Se você estiver interessado em ver o que essa função faz nos bastidores, você o encontrará em Deviceresources.
* A função **DeviceResources::InitializeUsingHolographicSpace** demonstra como obter o adaptador pesquisando o LUID – e como escolher um adaptador padrão quando nenhum adaptador preferencial é especificado.
* Classe de principal do aplicativo usa o espaço holográfico do **AppView::SetWindow** ou **App::CreateWindowAndHolographicSpace** para atualizações e renderização.

>[!NOTE]
>Embora as seções abaixo mencionam nomes de função do modelo, como **AppView::SetWindow** que supõem que você começou a partir do modelo de aplicativo UWP holográfico, os trechos de código que você consulte serão aplicado igualmente entre os aplicativos UWP e Win32.

Em seguida, vamos nos aprofundar na configuração do processo que **SetHolographicSpace** é responsável por na classe AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Assinar eventos de câmera, criar e remover recursos de câmera

Conteúdo holográfica do seu aplicativo reside em seu espaço de holográfico e é exibido por meio de um ou mais câmeras holográfica que representam diferentes perspectivas na cena. Agora que você tem o espaço holográfico, você pode receber dados de câmeras holográfica.

Seu aplicativo precisa responder às **CameraAdded** eventos com a criação de todos os recursos que são específicos para essa câmera, como seu buffer de fundo renderizar a exibição de destino. Você pode ver esse código na **DeviceResources::SetHolographicSpace** função, chamada pelo **AppView::SetWindow** antes que o aplicativo cria todos os quadros holográfico:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

Seu aplicativo também precisa responder às **CameraRemoved** eventos por liberação de recursos que foram criados para essa câmera.

Partir **DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Os manipuladores de eventos devem completar algum trabalho para manter a renderização holográfica fluindo sem problemas, e para que seu aplicativo seja capaz de renderizar em todos os. Ler o código e comentários para obter detalhes: você pode procurar por **OnCameraAdded** e **OnCameraRemoved** em sua classe principal para compreender como o **m_cameraResources** é de mapa tratados pelo **DeviceResources**.

Agora, estamos concentrados em AppMain e a configuração que faz para habilitar seu aplicativo saber sobre holográfica câmeras. Com isso em mente, é importante tomar nota dos dois requisitos a seguir:

1. Para o **CameraAdded** manipulador de eventos, o aplicativo pode trabalhar assincronamente para concluir a criação de recursos e carregar ativos para a nova câmera holográfica. Aplicativos que usam mais de um quadro para concluir o trabalho devem solicitar um adiamento e conclua o adiamento após o carregamento de forma assíncrona; uma [tarefas PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) pode ser usado para fazer o trabalho assíncrono. Seu aplicativo deve garantir que ele está pronto para processar para essa câmera imediatamente quando o manipulador de eventos é encerrada, ou quando o adiamento é concluído. Sair do manipulador de eventos ou concluir o adiamento informa ao sistema que seu aplicativo agora está pronto para receber quadros holográfico com essa câmera incluída.

2. Quando o aplicativo recebe um **CameraRemoved** evento, ele deve liberar todas as referências para o buffer de fundo e saia imediatamente e a função. Isso inclui modos de exibição de destino de renderização e qualquer outro recurso que pode conter uma referência para o [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). O aplicativo também deve garantir que o buffer de fundo não está anexado como um destino de renderização, conforme mostrado na **CameraResources::ReleaseResourcesForBackBuffer**. Para ajudar a agilizar as coisas ao longo, seu aplicativo pode liberar o buffer de fundo e, em seguida, inicie uma tarefa para concluir a qualquer outro trabalho que é necessário para subdividir esse câmera assincronamente. O modelo de aplicativo holográfica inclui uma tarefa PPL que você pode usar para essa finalidade.

>[!NOTE]
>Se você desejar determinar quando uma câmera tiver adicionada ou removida aparece no quadro, use o **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) e [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) propriedades.

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Criar um quadro de referência para o seu conteúdo holográfico

Conteúdo do seu aplicativo deve ser posicionado em um [sistema de coordenadas espacial](coordinate-systems-in-directx.md) a ser renderizada no HolographicSpace. O sistema fornece dois primários quadros de referência que pode ser usado para estabelecer um sistema de coordenadas para seu hologramas.

Há dois tipos de quadros de referência no Windows Holographic: referência anexados ao dispositivo de quadros e quadros de referência que permanecem parados conforme se move o dispositivo por meio do ambiente do usuário. O modelo de aplicativo holográfica usa um quadro estacionário de referência por padrão. Essa é uma das maneiras mais simples para renderizar hologramas bloqueado pelo mundo.

Quadros de referência estáticos são projetados para se estabilizar posições de perto a localização do dispositivo atual. Isso significa que as coordenadas mais longe de dispositivo têm permissão para descompasso ligeiramente em relação ao ambiente do usuário, como o dispositivo lado aprende mais sobre o espaço em torno dele. Há duas maneiras de criar um quadro estacionário de referência: adquirir o sistema de coordenadas do [estágio espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), ou use o padrão <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>. Se você estiver criando um aplicativo de realidade mista do Windows para fones imersivos em exposição, o ponto de partida recomendado é o [estágio espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), que também fornece informações sobre os recursos de imersão fone de ouvido gasta pelo player. Aqui, mostramos como usar o padrão <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.

O localizador espacial representa o dispositivo Windows Mixed Reality e controla o movimento do dispositivo e fornece sistemas de coordenadas que possa ser compreendidos em relação ao seu local.

Partir **AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Crie o quadro estacionário de referência de uma vez quando o aplicativo é iniciado. Isso é análogo à definição de um sistema de coordenadas do mundo, com a origem colocada na posição do dispositivo quando o aplicativo é iniciado. Esse quadro de referência não é movido com o dispositivo.

Partir **AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Todos os quadros de referência são gravidade alinhada, que significa que o eixo y aponta "para cima" em relação ao ambiente do usuário. Como o Windows usa "destros" sistemas de coordenadas, a direção do eixo z – coincide com a direção "forward", o dispositivo estiver voltada para quando o quadro de referência é criado.

>[!NOTE]
>Quando seu aplicativo requer o posicionamento exato dos hologramas individuais, use uma <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> ancorar o holograma individual para uma posição no mundo real. Por exemplo, use uma âncora espacial quando o usuário indica um ponto de interesse especial. Posições de âncora não descompasso, mas eles podem ser ajustados. Por padrão, quando uma âncora é ajustada, facilita a sua posição no lugar ao longo de vários quadros próxima depois que a correção ocorreu. Dependendo do seu aplicativo, quando isso ocorrer você talvez queira lidar com o ajuste de maneira diferente (por exemplo, adiamento até que o holograma está fora do modo de exibição). O <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> propriedade e <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> eventos permitem que essas personalizações.

## <a name="respond-to-locatability-changed-events"></a>Responder a eventos locatability alterado

Renderização bloqueado pelo mundo hologramas requer que o dispositivo para poder localizar-se no mundo. Isso talvez nem sempre seja possível devido a condições ambientais e, nesse caso, o usuário pode esperar uma indicação visual de que a interrupção do rastreamento. Essa indicação visual deve ser renderizada usando quadros de referência anexados ao dispositivo, em vez de estático para o mundo.

Seu aplicativo pode solicitar para ser notificado se o rastreamento é interrompido por qualquer motivo. Registre-se para o evento LocatabilityChanged detectar quando a capacidade do dispositivo para localizar-se nas alterações do mundo. De **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

Em seguida, use esse evento para determinar quando hologramas não podem ser renderizadas estáticos para o mundo.

## <a name="see-also"></a>Consulte também
* [Processamento no DirectX](rendering-in-directx.md)
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md)

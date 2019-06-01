---
title: Cabeçalho e olho olhar no DirectX
description: Guia do desenvolvedor para o uso principal olhar e rastreamento de aplicativos de DirectX nativos de olho.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: olhar, olhar cabeçalho, controle de cabeçalho, acompanhamento a olho nu, directx, entrada, hologramas
ms.openlocfilehash: ac72c5305527ed2d68945aeb32051cf2246a736e
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453736"
---
# <a name="head-and-eye-gaze-input-in-directx"></a>Cabeçalho e olho olhares entrada no DirectX

No Windows Mixed Reality, olho e olhar principal entrada é usada para determinar o que o usuário está observando. Isso pode ser usado para gerar modelos principais de entrada, como [olhar e confirmação de cabeçalho](gaze-and-commit.md)e também para fornecer contexto para tipos de interações. Há dois tipos de olhar vetores disponíveis por meio da API: olhar e olhar de olho de cabeçalho.  Ambos são fornecidas como um três ray dimensional com uma origem e a direção. Aplicativos, em seguida, podem raycast no mundo real, ou suas cenas e determinar o que o usuário está definindo como destino.

**Mantenha o foco principal** representa a direção apontado no cabeçalho do usuário. Pense nisso como a posição e direção de avanço do próprio dispositivo, com a posição que representa o centro do ponto entre as duas exibições.  Olhar de cabeça está disponível em todos os dispositivos de realidade misturada.

**Olhar olho** representa a direção que quer a atenção do usuário. A origem está localizada entre a atenção do usuário.  Ele está disponível em dispositivos de realidade mista que incluem um sistema de acompanhamento a olho nu.

Cabeçalho e olho raios de olhar são acessíveis por meio de [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API. Basta chamar [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto de SpatialPointerPose no carimbo de hora especificado e [sistema de coordenadas](coordinate-systems-in-directx.md). Este SpatialPointerPose contém uma origem de olhar principal e uma direção. Ele também contém uma origem de olhar de olho e a direção se acompanhamento a olho nu estiver disponível.

## <a name="using-head-gaze"></a>Usando olhar principal

Para acessar o olhar principal, inicie chamando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose. Você precisará passar os parâmetros a seguir.
 - Um [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa o sistema de coordenadas desejado para o cabeçalho olhar. Isso é representado pela *coordinateSystem* variável no código a seguir. Para obter mais informações, visite nosso [sistemas de coordenadas](coordinate-systems-in-directx.md) guia do desenvolvedor.
 - Um [carimbo de hora](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) que representa a hora exata da pose principal solicitada.  Normalmente, você usará um carimbo de hora que corresponde ao tempo de quando o quadro atual será exibido. Você pode obter esse carimbo de hora de exibição previstos de um [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) objeto, que é acessível por meio de atual [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).  Esse objeto HolographicFramePrediction é representado pela *previsão* variável no código a seguir.

 Quando você tiver um SpatialPointerPose válido, a posição principal e a direção para frente são acessíveis como propriedades.  O código a seguir mostra como acessá-los.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a>Usando um olhar de olhos

A API de olhar olho é muito semelhante ao olhar principal.  Ele usa as mesmas [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, que fornece um raio de origem e a direção que você pode raycast em relação a sua cena.  A única diferença é que você precisa habilitar o acompanhamento de olho antes de usá-lo explicitamente. Para isso, você precisa fazer duas etapas:
1. Solicite permissão de usuário para usar em seu aplicativo de acompanhamento de olho.
2. Habilite a funcionalidade "Mantenha o foco de entrada" em seu manifesto de pacote.

### <a name="requesting-access-to-gaze-input"></a>Solicitar acesso a mantenha o foco de entrada
Quando seu aplicativo está sendo inicializado, chame [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acesso ao acompanhamento de olho. O sistema solicitar que o usuário se necessário e retornar [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) depois que o acesso foi concedido. Isso é uma chamada assíncrona, portanto, requer um pouco de gerenciamento adicional. O exemplo a seguir gira um std:: thread desanexado para aguardar o resultado, que armazena a uma variável de membro chamada *m_isEyeTrackingEnabled*.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas.  Como alternativa, você pode usar o novo [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funcionalidade com suporte de C++/WinRT.
Aqui está outro exemplo para solicitando permissão do usuário:
-   EyesPose::IsSupported() permite que o aplicativo disparar a caixa de diálogo de permissão somente se houver um controlador de olho.
-   GazeInputAccessStatus m_gazeInputAccessStatus; Isso é para evitar o pop-up de prompt de permissão repetidamente.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a>Declarando o *olhares entrada* funcionalidade

Clique duas vezes no arquivo appxmanifest no *Gerenciador de soluções*.  Em seguida, navegue até a *funcionalidades* seção e verifique o *olhares entrada* funcionalidade. 

![Mantenha o foco de entrada de recurso](images/gaze-input-capability.png)

Isso adiciona as seguintes linhas para o *pacote* seção no arquivo appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Obtendo o raio de olhar olho
Depois de ter recebido acesso ao ET, você é livre para captar o raio de olhar olho cada quadro.  Assim como ocorre com cabeçalho olhar, obter o [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chamando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com um carimbo de data desejado e o sistema de coordenadas. O SpatialPointerPose contém um [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) por meio do objeto de [olhos](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) propriedade. Isso é não nulo somente se o acompanhamento a olho nu está habilitado. A partir daí, você pode verificar se o usuário no dispositivo tem um acompanhamento calibragem chamando a olho nu [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Em seguida, use o [olhares](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) propriedade a ser obtida de um [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing olhos olhares posição e direção. A propriedade de olhar pode, às vezes, ser nulo, portanto, certifique-se de verificar isso. Isso pode acontecer é se um usuário calibrado temporariamente fecha seus olhos.

O código a seguir mostra como acessar o raio de olhar olho.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>Correlacionando olhar com outras entradas

Às vezes, você pode achar que você precisa de uma [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) que corresponde com um evento no passado. Por exemplo, se o usuário executa um toque de ar, seu aplicativo talvez queira saber o que eles estavam vendo. Para essa finalidade, simplesmente usando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com o quadro previsto tempo seria impreciso devido à latência entre o processamento de entrada do sistema e o tempo de exibição. Além disso, se usar olhar de olho para direcionamento, seus olhos tendem mover-se até mesmo antes de concluir uma ação de confirmação. Isso é um problema menor para um simples ar toque, mas se torna mais crítico ao combinar longa comandos de voz com os deslocamentos de olho rápida. Uma maneira de lidar com esse cenário é fazer uma chamada adicional para [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando um carimbo de hora histórico que corresponde ao evento de entrada.  

No entanto, para a entrada que roteia por meio de SpatialInteractionManager, há um método mais fácil. O [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tem seu próprio [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) função. Chamar que fornecerá perfeitamente correlacionado [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) sem as suposições. Para obter mais informações sobre como trabalhar com SpatialInteractionSourceStates, dê uma olhada a [mãos e controladores de movimento no DirectX](hands-and-motion-controllers-in-directx.md) documentação.

## <a name="see-also"></a>Consulte também
* [Olhar de cabeçalho e confirmar o modelo de entrada](gaze-and-commit.md)
* [Acompanhamento em HoloLens 2 a olho nu](eye-tracking.md)
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)

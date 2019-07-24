---
title: Olhar de cabeça e olho no DirectX
description: Guia do desenvolvedor para usar o Head olhar e o acompanhamento de olho em aplicativos nativos do DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: olhar, Head olhar, acompanhamento de cabeçalho, controle ocular, DirectX, entrada, hologramas
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414415"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="43b87-104">Entrada de olhar de cabeça e olho no DirectX</span><span class="sxs-lookup"><span data-stu-id="43b87-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="43b87-105">No Windows Mixed Reality, os olhos e a entrada olhar de cabeça são usados para determinar o que o usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="43b87-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="43b87-106">Isso pode ser usado para direcionar modelos de entrada primários, como [Head olhar e commit](gaze-and-commit.md), e também fornecer contexto para tipos de interações.</span><span class="sxs-lookup"><span data-stu-id="43b87-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="43b87-107">Há dois tipos de vetores olhar disponíveis por meio da API: Head olhar e olho olhar.</span><span class="sxs-lookup"><span data-stu-id="43b87-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="43b87-108">Ambos são fornecidos como um raio de três dimensões com uma origem e uma direção.</span><span class="sxs-lookup"><span data-stu-id="43b87-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="43b87-109">Os aplicativos podem então raycastr em suas cenas ou no mundo real e determinar o que o usuário está direcionando.</span><span class="sxs-lookup"><span data-stu-id="43b87-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="43b87-110">**Olhar de cabeçalho** representa a direção na qual a cabeça do usuário é apontada.</span><span class="sxs-lookup"><span data-stu-id="43b87-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="43b87-111">Considere isso como a posição e direção de encaminhamento do próprio dispositivo, com a posição que representa o ponto central entre as duas exibições.</span><span class="sxs-lookup"><span data-stu-id="43b87-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="43b87-112">O Head olhar está disponível em todos os dispositivos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="43b87-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="43b87-113">**Olho olhar** representa a direção que os olhos do usuário estão procurando.</span><span class="sxs-lookup"><span data-stu-id="43b87-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="43b87-114">A origem está localizada entre os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="43b87-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="43b87-115">Ele está disponível em dispositivos com realidade misturada que incluem um sistema de controle de olho.</span><span class="sxs-lookup"><span data-stu-id="43b87-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="43b87-116">Os raios de olhar de cabeça e olho podem ser acessados por meio da API do [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="43b87-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="43b87-117">Basta chamar [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose no carimbo de data/hora e no [sistema de coordenadas](coordinate-systems-in-directx.md)especificado.</span><span class="sxs-lookup"><span data-stu-id="43b87-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="43b87-118">Esse SpatialPointerPose contém uma origem e direção de olhar de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="43b87-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="43b87-119">Ele também contém uma origem e direção de olhar de olho, se o acompanhamento de olho estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="43b87-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="43b87-120">Usando o Head olhar</span><span class="sxs-lookup"><span data-stu-id="43b87-120">Using head gaze</span></span>

<span data-ttu-id="43b87-121">Para acessar o cabeçalho olhar, comece chamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="43b87-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="43b87-122">Você precisa passar os parâmetros a seguir.</span><span class="sxs-lookup"><span data-stu-id="43b87-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="43b87-123">Um [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa o sistema de coordenadas desejado para o olhar de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="43b87-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="43b87-124">Isso é representado pela variável *coordinateSystem* no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="43b87-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="43b87-125">Para obter mais informações, visite nosso guia do desenvolvedor de [sistemas de coordenadas](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="43b87-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="43b87-126">Um [carimbo de data/](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) hora que representa o tempo exato necessário para a pose de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="43b87-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="43b87-127">Normalmente, você usará um carimbo de data/hora que corresponde ao horário em que o quadro atual será exibido.</span><span class="sxs-lookup"><span data-stu-id="43b87-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="43b87-128">Você pode obter esse carimbo de data/hora de exibição previsto de um objeto [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que é acessível por meio do [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)atual.</span><span class="sxs-lookup"><span data-stu-id="43b87-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="43b87-129">Esse objeto HolographicFramePrediction é representado pela variável de *previsão* no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="43b87-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="43b87-130">Quando você tiver um SpatialPointerPose válido, a posição de cabeçalho e a direção de encaminhamento serão acessíveis como propriedades.</span><span class="sxs-lookup"><span data-stu-id="43b87-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="43b87-131">O código a seguir mostra como acessá-los.</span><span class="sxs-lookup"><span data-stu-id="43b87-131">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="43b87-132">Usando os olhos olhar</span><span class="sxs-lookup"><span data-stu-id="43b87-132">Using eye gaze</span></span>

<span data-ttu-id="43b87-133">A API de olho olhar é muito semelhante à olhar de cabeça.</span><span class="sxs-lookup"><span data-stu-id="43b87-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="43b87-134">Ele usa a mesma API [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , que fornece uma Ray Origin e uma direção que você pode Raycast em sua cena.</span><span class="sxs-lookup"><span data-stu-id="43b87-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="43b87-135">A única diferença é que você precisa habilitar explicitamente o controle de olho antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="43b87-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="43b87-136">Para isso, você precisa executar duas etapas:</span><span class="sxs-lookup"><span data-stu-id="43b87-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="43b87-137">Solicite permissão do usuário para usar o acompanhamento de olho em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="43b87-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="43b87-138">Habilite a funcionalidade de "entrada olhar" no manifesto do pacote.</span><span class="sxs-lookup"><span data-stu-id="43b87-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="43b87-139">Solicitando acesso à entrada olhar</span><span class="sxs-lookup"><span data-stu-id="43b87-139">Requesting access to gaze input</span></span>
<span data-ttu-id="43b87-140">Quando seu aplicativo estiver sendo inicializado, chame [EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acesso ao controle ocular.</span><span class="sxs-lookup"><span data-stu-id="43b87-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="43b87-141">O sistema solicitará o usuário se necessário e retornará [GazeInputAccessStatus:: allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) depois que o acesso tiver sido concedido.</span><span class="sxs-lookup"><span data-stu-id="43b87-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="43b87-142">Essa é uma chamada assíncrona, portanto, requer um pouco de gerenciamento extra.</span><span class="sxs-lookup"><span data-stu-id="43b87-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="43b87-143">O exemplo a seguir gira um std:: thread desanexado para aguardar o resultado, que ele armazena em uma variável de membro chamada *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="43b87-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="43b87-144">Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="43b87-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="43b87-145">Como alternativa, você pode usar a nova funcionalidade [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) com suporte C++do/WinRT.</span><span class="sxs-lookup"><span data-stu-id="43b87-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="43b87-146">Aqui está outro exemplo para solicitar permissão de usuário:</span><span class="sxs-lookup"><span data-stu-id="43b87-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="43b87-147">EyesPose:: IsSupported () permite que o aplicativo dispare a caixa de diálogo de permissão somente se houver um rastreador ocular.</span><span class="sxs-lookup"><span data-stu-id="43b87-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="43b87-148">GazeInputAccessStatus m_gazeInputAccessStatus; Isso é para evitar o pop-up do prompt de permissão repetidamente.</span><span class="sxs-lookup"><span data-stu-id="43b87-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="43b87-149">Declarando o recurso de *entrada olhar*</span><span class="sxs-lookup"><span data-stu-id="43b87-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="43b87-150">Clique duas vezes no arquivo appxmanifest em *Gerenciador de soluções*.</span><span class="sxs-lookup"><span data-stu-id="43b87-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="43b87-151">Em seguida, navegue até a seção de *recursos* e verifique o recurso de *entrada olhar* .</span><span class="sxs-lookup"><span data-stu-id="43b87-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Funcionalidade de entrada do olhar](images/gaze-input-capability.png)

<span data-ttu-id="43b87-153">Isso adiciona as seguintes linhas à seção *Package* no arquivo appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="43b87-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="43b87-154">Obtendo o olho olhar Ray</span><span class="sxs-lookup"><span data-stu-id="43b87-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="43b87-155">Depois de ter recebido o acesso ao ET, você fica livre para pegar o olho olhar Ray a cada quadro.</span><span class="sxs-lookup"><span data-stu-id="43b87-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="43b87-156">Assim como acontece com o Head olhar, obtenha o [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chamando [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com um carimbo de data/hora desejado e sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="43b87-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="43b87-157">O SpatialPointerPose contém um objeto [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) por meio da propriedade [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="43b87-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="43b87-158">Isso será não nulo somente se o controle de olho estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="43b87-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="43b87-159">A partir daí, você pode verificar se o usuário no dispositivo tem uma calibragem de acompanhamento de olho chamando [EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="43b87-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="43b87-160">Em seguida, use a propriedade [olhar](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obter um [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing a posição e a direção de olhar de olho.</span><span class="sxs-lookup"><span data-stu-id="43b87-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="43b87-161">Às vezes, a propriedade olhar pode ser nula, portanto certifique-se de verificar isso.</span><span class="sxs-lookup"><span data-stu-id="43b87-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="43b87-162">Isso pode acontecer se um usuário calibrado fechar temporariamente seus olhos.</span><span class="sxs-lookup"><span data-stu-id="43b87-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="43b87-163">O código a seguir mostra como acessar o olho olhar Ray.</span><span class="sxs-lookup"><span data-stu-id="43b87-163">The following code shows how to access the eye gaze ray.</span></span>

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

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="43b87-164">Correlacionando olhar com outras entradas</span><span class="sxs-lookup"><span data-stu-id="43b87-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="43b87-165">Às vezes, você pode achar que precisa de um [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) que corresponda a um evento no passado.</span><span class="sxs-lookup"><span data-stu-id="43b87-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="43b87-166">Por exemplo, se o usuário executar um toque de ar, seu aplicativo poderá querer saber o que ele estava observando.</span><span class="sxs-lookup"><span data-stu-id="43b87-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="43b87-167">Para essa finalidade, simplesmente usar [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com o tempo de quadro previsto não seria preciso devido à latência entre o processamento de entrada do sistema e o tempo de exibição.</span><span class="sxs-lookup"><span data-stu-id="43b87-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="43b87-168">Além disso, se estiver usando olho olhar para direcionamento, nossos olhos tendem a se mover até mesmo antes de concluir uma ação de confirmação.</span><span class="sxs-lookup"><span data-stu-id="43b87-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="43b87-169">Isso é menos um problema para um toque simples de ar, mas se torna mais crítico ao combinar comandos de voz longos com movimentos de olho rápido.</span><span class="sxs-lookup"><span data-stu-id="43b87-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="43b87-170">Uma maneira de lidar com esse cenário é fazer uma chamada adicional para [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando um carimbo de data/hora histórico que corresponde ao evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="43b87-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="43b87-171">No entanto, para entrada que roteiam o SpatialInteractionManager, há um método mais fácil.</span><span class="sxs-lookup"><span data-stu-id="43b87-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="43b87-172">O [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tem sua própria função [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="43b87-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="43b87-173">Chamar isso fornecerá um [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) perfeitamente correlacionado sem as suposições.</span><span class="sxs-lookup"><span data-stu-id="43b87-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="43b87-174">Para saber mais sobre como trabalhar com o SpatialInteractionSourceStates, confira os [controladores de mãos e de movimento na documentação do DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="43b87-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="43b87-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43b87-175">See also</span></span>
* [<span data-ttu-id="43b87-176">Olhar de cabeça e modelo de entrada de confirmação</span><span class="sxs-lookup"><span data-stu-id="43b87-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="43b87-177">Olho-olhar no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="43b87-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="43b87-178">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="43b87-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="43b87-179">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="43b87-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="43b87-180">Controladores de mãos e emovimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="43b87-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)

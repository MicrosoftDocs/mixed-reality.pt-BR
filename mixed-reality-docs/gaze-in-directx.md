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
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="63d3b-104">Cabeçalho e olho olhares entrada no DirectX</span><span class="sxs-lookup"><span data-stu-id="63d3b-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="63d3b-105">No Windows Mixed Reality, olho e olhar principal entrada é usada para determinar o que o usuário está observando.</span><span class="sxs-lookup"><span data-stu-id="63d3b-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="63d3b-106">Isso pode ser usado para gerar modelos principais de entrada, como [olhar e confirmação de cabeçalho](gaze-and-commit.md)e também para fornecer contexto para tipos de interações.</span><span class="sxs-lookup"><span data-stu-id="63d3b-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="63d3b-107">Há dois tipos de olhar vetores disponíveis por meio da API: olhar e olhar de olho de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="63d3b-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="63d3b-108">Ambos são fornecidas como um três ray dimensional com uma origem e a direção.</span><span class="sxs-lookup"><span data-stu-id="63d3b-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="63d3b-109">Aplicativos, em seguida, podem raycast no mundo real, ou suas cenas e determinar o que o usuário está definindo como destino.</span><span class="sxs-lookup"><span data-stu-id="63d3b-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="63d3b-110">**Mantenha o foco principal** representa a direção apontado no cabeçalho do usuário.</span><span class="sxs-lookup"><span data-stu-id="63d3b-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="63d3b-111">Pense nisso como a posição e direção de avanço do próprio dispositivo, com a posição que representa o centro do ponto entre as duas exibições.</span><span class="sxs-lookup"><span data-stu-id="63d3b-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="63d3b-112">Olhar de cabeça está disponível em todos os dispositivos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="63d3b-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="63d3b-113">**Olhar olho** representa a direção que quer a atenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="63d3b-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="63d3b-114">A origem está localizada entre a atenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="63d3b-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="63d3b-115">Ele está disponível em dispositivos de realidade mista que incluem um sistema de acompanhamento a olho nu.</span><span class="sxs-lookup"><span data-stu-id="63d3b-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="63d3b-116">Cabeçalho e olho raios de olhar são acessíveis por meio de [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span><span class="sxs-lookup"><span data-stu-id="63d3b-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="63d3b-117">Basta chamar [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto de SpatialPointerPose no carimbo de hora especificado e [sistema de coordenadas](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="63d3b-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="63d3b-118">Este SpatialPointerPose contém uma origem de olhar principal e uma direção.</span><span class="sxs-lookup"><span data-stu-id="63d3b-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="63d3b-119">Ele também contém uma origem de olhar de olho e a direção se acompanhamento a olho nu estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="63d3b-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="63d3b-120">Usando olhar principal</span><span class="sxs-lookup"><span data-stu-id="63d3b-120">Using head gaze</span></span>

<span data-ttu-id="63d3b-121">Para acessar o olhar principal, inicie chamando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para receber um novo objeto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="63d3b-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="63d3b-122">Você precisará passar os parâmetros a seguir.</span><span class="sxs-lookup"><span data-stu-id="63d3b-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="63d3b-123">Um [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa o sistema de coordenadas desejado para o cabeçalho olhar.</span><span class="sxs-lookup"><span data-stu-id="63d3b-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="63d3b-124">Isso é representado pela *coordinateSystem* variável no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="63d3b-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="63d3b-125">Para obter mais informações, visite nosso [sistemas de coordenadas](coordinate-systems-in-directx.md) guia do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="63d3b-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="63d3b-126">Um [carimbo de hora](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) que representa a hora exata da pose principal solicitada.</span><span class="sxs-lookup"><span data-stu-id="63d3b-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="63d3b-127">Normalmente, você usará um carimbo de hora que corresponde ao tempo de quando o quadro atual será exibido.</span><span class="sxs-lookup"><span data-stu-id="63d3b-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="63d3b-128">Você pode obter esse carimbo de hora de exibição previstos de um [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) objeto, que é acessível por meio de atual [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="63d3b-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="63d3b-129">Esse objeto HolographicFramePrediction é representado pela *previsão* variável no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="63d3b-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="63d3b-130">Quando você tiver um SpatialPointerPose válido, a posição principal e a direção para frente são acessíveis como propriedades.</span><span class="sxs-lookup"><span data-stu-id="63d3b-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="63d3b-131">O código a seguir mostra como acessá-los.</span><span class="sxs-lookup"><span data-stu-id="63d3b-131">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="63d3b-132">Usando um olhar de olhos</span><span class="sxs-lookup"><span data-stu-id="63d3b-132">Using eye gaze</span></span>

<span data-ttu-id="63d3b-133">A API de olhar olho é muito semelhante ao olhar principal.</span><span class="sxs-lookup"><span data-stu-id="63d3b-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="63d3b-134">Ele usa as mesmas [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, que fornece um raio de origem e a direção que você pode raycast em relação a sua cena.</span><span class="sxs-lookup"><span data-stu-id="63d3b-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="63d3b-135">A única diferença é que você precisa habilitar o acompanhamento de olho antes de usá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="63d3b-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="63d3b-136">Para isso, você precisa fazer duas etapas:</span><span class="sxs-lookup"><span data-stu-id="63d3b-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="63d3b-137">Solicite permissão de usuário para usar em seu aplicativo de acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="63d3b-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="63d3b-138">Habilite a funcionalidade "Mantenha o foco de entrada" em seu manifesto de pacote.</span><span class="sxs-lookup"><span data-stu-id="63d3b-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="63d3b-139">Solicitar acesso a mantenha o foco de entrada</span><span class="sxs-lookup"><span data-stu-id="63d3b-139">Requesting access to gaze input</span></span>
<span data-ttu-id="63d3b-140">Quando seu aplicativo está sendo inicializado, chame [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acesso ao acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="63d3b-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="63d3b-141">O sistema solicitar que o usuário se necessário e retornar [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) depois que o acesso foi concedido.</span><span class="sxs-lookup"><span data-stu-id="63d3b-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="63d3b-142">Isso é uma chamada assíncrona, portanto, requer um pouco de gerenciamento adicional.</span><span class="sxs-lookup"><span data-stu-id="63d3b-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="63d3b-143">O exemplo a seguir gira um std:: thread desanexado para aguardar o resultado, que armazena a uma variável de membro chamada *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="63d3b-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="63d3b-144">Iniciar um thread desanexado é apenas uma opção para lidar com chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="63d3b-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="63d3b-145">Como alternativa, você pode usar o novo [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funcionalidade com suporte de C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="63d3b-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="63d3b-146">Aqui está outro exemplo para solicitando permissão do usuário:</span><span class="sxs-lookup"><span data-stu-id="63d3b-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="63d3b-147">EyesPose::IsSupported() permite que o aplicativo disparar a caixa de diálogo de permissão somente se houver um controlador de olho.</span><span class="sxs-lookup"><span data-stu-id="63d3b-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="63d3b-148">GazeInputAccessStatus m_gazeInputAccessStatus; Isso é para evitar o pop-up de prompt de permissão repetidamente.</span><span class="sxs-lookup"><span data-stu-id="63d3b-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="63d3b-149">Declarando o *olhares entrada* funcionalidade</span><span class="sxs-lookup"><span data-stu-id="63d3b-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="63d3b-150">Clique duas vezes no arquivo appxmanifest no *Gerenciador de soluções*.</span><span class="sxs-lookup"><span data-stu-id="63d3b-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="63d3b-151">Em seguida, navegue até a *funcionalidades* seção e verifique o *olhares entrada* funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="63d3b-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Mantenha o foco de entrada de recurso](images/gaze-input-capability.png)

<span data-ttu-id="63d3b-153">Isso adiciona as seguintes linhas para o *pacote* seção no arquivo appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="63d3b-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="63d3b-154">Obtendo o raio de olhar olho</span><span class="sxs-lookup"><span data-stu-id="63d3b-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="63d3b-155">Depois de ter recebido acesso ao ET, você é livre para captar o raio de olhar olho cada quadro.</span><span class="sxs-lookup"><span data-stu-id="63d3b-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="63d3b-156">Assim como ocorre com cabeçalho olhar, obter o [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) chamando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com um carimbo de data desejado e o sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="63d3b-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="63d3b-157">O SpatialPointerPose contém um [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) por meio do objeto de [olhos](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) propriedade.</span><span class="sxs-lookup"><span data-stu-id="63d3b-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="63d3b-158">Isso é não nulo somente se o acompanhamento a olho nu está habilitado.</span><span class="sxs-lookup"><span data-stu-id="63d3b-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="63d3b-159">A partir daí, você pode verificar se o usuário no dispositivo tem um acompanhamento calibragem chamando a olho nu [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="63d3b-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="63d3b-160">Em seguida, use o [olhares](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) propriedade a ser obtida de um [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing olhos olhares posição e direção.</span><span class="sxs-lookup"><span data-stu-id="63d3b-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="63d3b-161">A propriedade de olhar pode, às vezes, ser nulo, portanto, certifique-se de verificar isso.</span><span class="sxs-lookup"><span data-stu-id="63d3b-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="63d3b-162">Isso pode acontecer é se um usuário calibrado temporariamente fecha seus olhos.</span><span class="sxs-lookup"><span data-stu-id="63d3b-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="63d3b-163">O código a seguir mostra como acessar o raio de olhar olho.</span><span class="sxs-lookup"><span data-stu-id="63d3b-163">The following code shows how to access the eye gaze ray.</span></span>

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

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="63d3b-164">Correlacionando olhar com outras entradas</span><span class="sxs-lookup"><span data-stu-id="63d3b-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="63d3b-165">Às vezes, você pode achar que você precisa de uma [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) que corresponde com um evento no passado.</span><span class="sxs-lookup"><span data-stu-id="63d3b-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="63d3b-166">Por exemplo, se o usuário executa um toque de ar, seu aplicativo talvez queira saber o que eles estavam vendo.</span><span class="sxs-lookup"><span data-stu-id="63d3b-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="63d3b-167">Para essa finalidade, simplesmente usando [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) com o quadro previsto tempo seria impreciso devido à latência entre o processamento de entrada do sistema e o tempo de exibição.</span><span class="sxs-lookup"><span data-stu-id="63d3b-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="63d3b-168">Além disso, se usar olhar de olho para direcionamento, seus olhos tendem mover-se até mesmo antes de concluir uma ação de confirmação.</span><span class="sxs-lookup"><span data-stu-id="63d3b-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="63d3b-169">Isso é um problema menor para um simples ar toque, mas se torna mais crítico ao combinar longa comandos de voz com os deslocamentos de olho rápida.</span><span class="sxs-lookup"><span data-stu-id="63d3b-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="63d3b-170">Uma maneira de lidar com esse cenário é fazer uma chamada adicional para [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), usando um carimbo de hora histórico que corresponde ao evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="63d3b-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="63d3b-171">No entanto, para a entrada que roteia por meio de SpatialInteractionManager, há um método mais fácil.</span><span class="sxs-lookup"><span data-stu-id="63d3b-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="63d3b-172">O [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tem seu próprio [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) função.</span><span class="sxs-lookup"><span data-stu-id="63d3b-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="63d3b-173">Chamar que fornecerá perfeitamente correlacionado [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) sem as suposições.</span><span class="sxs-lookup"><span data-stu-id="63d3b-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="63d3b-174">Para obter mais informações sobre como trabalhar com SpatialInteractionSourceStates, dê uma olhada a [mãos e controladores de movimento no DirectX](hands-and-motion-controllers-in-directx.md) documentação.</span><span class="sxs-lookup"><span data-stu-id="63d3b-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="63d3b-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63d3b-175">See also</span></span>
* [<span data-ttu-id="63d3b-176">Olhar de cabeçalho e confirmar o modelo de entrada</span><span class="sxs-lookup"><span data-stu-id="63d3b-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="63d3b-177">Acompanhamento em HoloLens 2 a olho nu</span><span class="sxs-lookup"><span data-stu-id="63d3b-177">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="63d3b-178">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="63d3b-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="63d3b-179">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="63d3b-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="63d3b-180">Controladores de mãos e emovimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="63d3b-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)

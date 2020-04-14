---
title: Renderização no DirectX
description: Explica o processamento de Holographic para a realidade mista do Windows.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, hologramas, renderização, gráficos 3D, HolographicFrame, loop de processamento, loop de atualização, passo a passos, código de exemplo, Direct3D
ms.openlocfilehash: a781093e0054a986b81a0e284e03076dd018f8c0
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277504"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="10f18-104">Renderização no DirectX</span><span class="sxs-lookup"><span data-stu-id="10f18-104">Rendering in DirectX</span></span>

<span data-ttu-id="10f18-105">A realidade mista do Windows se baseia no DirectX para produzir experiências gráficas 3D ricas para os usuários.</span><span class="sxs-lookup"><span data-stu-id="10f18-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="10f18-106">A abstração de renderização fica logo acima do DirectX e permite a um motivo do aplicativo sobre a posição e a orientação de um ou mais observadores de uma cena Holographic, conforme previsto pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="10f18-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="10f18-107">O desenvolvedor pode então localizar seus hologramas em relação a cada câmera, permitindo que o aplicativo processe esses hologramas em vários sistemas de coordenadas espaciais à medida que o usuário se movimenta.</span><span class="sxs-lookup"><span data-stu-id="10f18-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="10f18-108">Observação: este passo a passos descreve a renderização Holographic no Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="10f18-108">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="10f18-109">Um modelo de aplicativo de realidade misturada do Windows do Direct3D 12 também é fornecido com a extensão de modelos de aplicativo da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="10f18-109">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="10f18-110">Atualizar para o quadro atual</span><span class="sxs-lookup"><span data-stu-id="10f18-110">Update for the current frame</span></span>

<span data-ttu-id="10f18-111">Para atualizar o estado do aplicativo para hologramas, uma vez por quadro, o aplicativo irá:</span><span class="sxs-lookup"><span data-stu-id="10f18-111">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="10f18-112">Obtenha um <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> do sistema de gerenciamento de vídeo.</span><span class="sxs-lookup"><span data-stu-id="10f18-112">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="10f18-113">Atualize a cena com a previsão atual de onde a exibição da câmera será quando o processamento for concluído.</span><span class="sxs-lookup"><span data-stu-id="10f18-113">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="10f18-114">Observe que pode haver mais de uma câmera para a cena Holographic.</span><span class="sxs-lookup"><span data-stu-id="10f18-114">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="10f18-115">Para renderizar para exibições de câmera Holographic, uma vez por quadro, o aplicativo irá:</span><span class="sxs-lookup"><span data-stu-id="10f18-115">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="10f18-116">Para cada câmera, processe a cena para o quadro atual, usando a exibição de câmera e as matrizes de projeção do sistema.</span><span class="sxs-lookup"><span data-stu-id="10f18-116">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="10f18-117">Criar um novo quadro do Holographic e obter sua previsão</span><span class="sxs-lookup"><span data-stu-id="10f18-117">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="10f18-118">O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tem informações de que o aplicativo precisa para atualizar e renderizar o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="10f18-118">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="10f18-119">O aplicativo começa cada novo quadro chamando o método **CreateNextFrame** .</span><span class="sxs-lookup"><span data-stu-id="10f18-119">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="10f18-120">Quando esse método é chamado, as previsões são feitas usando os dados de sensor mais recentes disponíveis e encapsuladas no objeto **CurrentPrediction** .</span><span class="sxs-lookup"><span data-stu-id="10f18-120">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="10f18-121">Um novo objeto de quadro deve ser usado para cada quadro renderizado, pois ele só é válido para um instante no tempo.</span><span class="sxs-lookup"><span data-stu-id="10f18-121">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="10f18-122">A propriedade **CurrentPrediction** contém informações como a posição da câmera.</span><span class="sxs-lookup"><span data-stu-id="10f18-122">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="10f18-123">As informações são extrapoladas para o momento exato no momento em que o quadro deve ficar visível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="10f18-123">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="10f18-124">O código a seguir é extraído de **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="10f18-124">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="10f18-125">Processar atualizações da câmera</span><span class="sxs-lookup"><span data-stu-id="10f18-125">Process camera updates</span></span>

<span data-ttu-id="10f18-126">Buffers de fundo podem mudar de quadro para quadro.</span><span class="sxs-lookup"><span data-stu-id="10f18-126">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="10f18-127">Seu aplicativo precisa validar o buffer de fundo para cada câmera e liberar e recriar exibições de recursos e buffers de profundidade, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="10f18-127">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="10f18-128">Observe que o conjunto de poses na previsão é a lista autoritativa de câmeras que estão sendo usadas no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="10f18-128">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="10f18-129">Normalmente, você usa essa lista para iterar no conjunto de câmeras.</span><span class="sxs-lookup"><span data-stu-id="10f18-129">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="10f18-130">De **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="10f18-130">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="10f18-131">De **DeviceResources:: EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="10f18-131">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="10f18-132">Obter o sistema de coordenadas para usar como base para renderização</span><span class="sxs-lookup"><span data-stu-id="10f18-132">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="10f18-133">A realidade mista do Windows permite que seu aplicativo crie vários [sistemas de coordenadas](coordinate-systems-in-directx.md) conforme necessário, como o quadro de referência anexado e o quadro de referência estacionário, que controla os locais no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="10f18-133">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="10f18-134">Seu aplicativo pode, então, usar esses sistemas de coordenadas para saber por onde renderizar os hologramas em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="10f18-134">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="10f18-135">Ao solicitar coordenadas de uma API, você sempre passará o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> dentro do qual deseja que essas coordenadas sejam expressas.</span><span class="sxs-lookup"><span data-stu-id="10f18-135">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="10f18-136">De **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="10f18-136">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="10f18-137">Esses sistemas de coordenadas podem ser usados para gerar matrizes de exibição de estéreo ao renderizar o conteúdo em sua cena.</span><span class="sxs-lookup"><span data-stu-id="10f18-137">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="10f18-138">De **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="10f18-138">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="10f18-139">Olhar de processo e entrada de gesto</span><span class="sxs-lookup"><span data-stu-id="10f18-139">Process gaze and gesture input</span></span>

<span data-ttu-id="10f18-140">As entradas [olhar](gaze-in-directx.md) e [Hand](hands-and-motion-controllers-in-directx.md) não são baseadas em tempo e, portanto, não precisam ser atualizadas na função **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="10f18-140">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="10f18-141">No entanto, essa entrada é algo que o aplicativo precisa para examinar cada quadro.</span><span class="sxs-lookup"><span data-stu-id="10f18-141">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="10f18-142">Processar atualizações baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="10f18-142">Process time-based updates</span></span>

<span data-ttu-id="10f18-143">Qualquer aplicativo de renderização em tempo real precisará de alguma maneira de processar atualizações baseadas em tempo; fornecemos uma maneira de fazer isso no modelo de aplicativo Holographic do Windows por meio de uma implementação de **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="10f18-143">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="10f18-144">Isso é semelhante ao StepTimer fornecido no modelo de aplicativo UWP DirectX 11, portanto, se você já examinou o modelo, deve estar familiarizado com o solo.</span><span class="sxs-lookup"><span data-stu-id="10f18-144">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="10f18-145">Esta classe auxiliar de exemplo do StepTimer é capaz de fornecer atualizações de etapa de tempo fixas, bem como atualizações de etapa de tempo variável, e o modo padrão são etapas de tempo variável.</span><span class="sxs-lookup"><span data-stu-id="10f18-145">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="10f18-146">No caso da renderização Holographic, optamos especificamente por não colocar muito na função de temporizador.</span><span class="sxs-lookup"><span data-stu-id="10f18-146">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="10f18-147">Isso ocorre porque você pode configurá-lo para ser uma etapa fixa, caso em que ele pode ser chamado mais de uma vez por quadro – ou não, para alguns quadros, e nossas atualizações de dados Holographic devem ocorrer uma vez por quadro.</span><span class="sxs-lookup"><span data-stu-id="10f18-147">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="10f18-148">De **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="10f18-148">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="10f18-149">Posicionar e girar os hologramas em seu sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="10f18-149">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="10f18-150">Se você estiver operando em um único sistema de coordenadas, como o modelo faz com o **SpatialStationaryReferenceFrame**, esse processo não é diferente do que é usado de outra forma em gráficos 3D.</span><span class="sxs-lookup"><span data-stu-id="10f18-150">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="10f18-151">Aqui, giramos o cubo e definimos a matriz do modelo em relação à posição no sistema de coordenadas do estacionário.</span><span class="sxs-lookup"><span data-stu-id="10f18-151">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="10f18-152">De **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="10f18-152">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="10f18-153">**Observação sobre cenários avançados:** O cubo girando é um exemplo muito simples de como posicionar um holograma em um único quadro de referência.</span><span class="sxs-lookup"><span data-stu-id="10f18-153">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="10f18-154">Também é possível [usar vários SpatialCoordinateSystems](coordinate-systems-in-directx.md) no mesmo quadro renderizado, ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="10f18-154">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="10f18-155">Atualizar dados de buffer constante</span><span class="sxs-lookup"><span data-stu-id="10f18-155">Update constant buffer data</span></span>

<span data-ttu-id="10f18-156">As transformações de modelo para conteúdo são atualizadas como de costume.</span><span class="sxs-lookup"><span data-stu-id="10f18-156">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="10f18-157">Agora, você terá transformações válidas computadas para o sistema de coordenadas em que será renderizado.</span><span class="sxs-lookup"><span data-stu-id="10f18-157">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="10f18-158">De **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="10f18-158">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="10f18-159">E quanto às transformações de exibição e projeção?</span><span class="sxs-lookup"><span data-stu-id="10f18-159">What about view and projection transforms?</span></span> <span data-ttu-id="10f18-160">Para obter melhores resultados, queremos esperar até que esteja quase pronto para nossas chamadas de desenho antes de obtê-las.</span><span class="sxs-lookup"><span data-stu-id="10f18-160">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="10f18-161">Renderizar o quadro atual</span><span class="sxs-lookup"><span data-stu-id="10f18-161">Render the current frame</span></span>

<span data-ttu-id="10f18-162">A renderização na realidade mista do Windows não é muito diferente da renderização em uma exibição mono 2D, mas há algumas diferenças que você precisa conhecer:</span><span class="sxs-lookup"><span data-stu-id="10f18-162">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="10f18-163">As previsões de quadros Holographic são importantes.</span><span class="sxs-lookup"><span data-stu-id="10f18-163">Holographic frame predictions are important.</span></span> <span data-ttu-id="10f18-164">Quanto mais próximo a previsão for quando seu quadro for apresentado, melhor será o seu holograma.</span><span class="sxs-lookup"><span data-stu-id="10f18-164">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="10f18-165">A realidade mista do Windows controla as exibições da câmera.</span><span class="sxs-lookup"><span data-stu-id="10f18-165">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="10f18-166">Você precisa renderizar para cada um porque o quadro Holographic será apresentado para você posteriormente.</span><span class="sxs-lookup"><span data-stu-id="10f18-166">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="10f18-167">É recomendável que a renderização de estéreo seja realizada usando o desenho em instância para uma matriz de destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="10f18-167">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="10f18-168">O modelo de aplicativo Holographic usa a abordagem recomendada de desenho em instância para uma matriz de destino de renderização, que usa uma exibição de destino de renderização em um **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="10f18-168">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="10f18-169">Se você quiser renderizar sem usar a instanciação de estéreo, será necessário criar duas RenderTargetViews não matrizes (uma para cada olho) que cada referência a uma das duas fatias do **Texture2DArray** fornecida ao aplicativo do sistema.</span><span class="sxs-lookup"><span data-stu-id="10f18-169">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="10f18-170">Isso não é recomendado, pois normalmente é significativamente mais lento do que usar a instanciação.</span><span class="sxs-lookup"><span data-stu-id="10f18-170">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="10f18-171">Obter uma previsão HolographicFrame atualizada</span><span class="sxs-lookup"><span data-stu-id="10f18-171">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="10f18-172">A atualização da previsão de quadros aprimora a eficácia da estabilização de imagem e permite um posicionamento mais preciso de hologramas devido ao tempo menor entre a previsão e quando o quadro é visível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="10f18-172">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="10f18-173">Idealmente, atualize sua previsão de quadros logo antes da renderização.</span><span class="sxs-lookup"><span data-stu-id="10f18-173">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="10f18-174">Renderizar para cada câmera</span><span class="sxs-lookup"><span data-stu-id="10f18-174">Render to each camera</span></span>

<span data-ttu-id="10f18-175">O loop no conjunto da câmera representa a previsão e renderizado para cada câmera nesse conjunto.</span><span class="sxs-lookup"><span data-stu-id="10f18-175">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="10f18-176">**Configurar sua passagem de renderização**</span><span class="sxs-lookup"><span data-stu-id="10f18-176">**Set up your rendering pass**</span></span>

<span data-ttu-id="10f18-177">A realidade mista do Windows usa a renderização estereoscópico para aprimorar a ilusão de profundidade e para renderizar stereoscopically, para que ambas as exibições à esquerda e à direita estejam ativas.</span><span class="sxs-lookup"><span data-stu-id="10f18-177">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="10f18-178">Com a renderização estereoscópico, há um deslocamento entre as duas exibições, que o cérebro pode reconciliar como profundidade real.</span><span class="sxs-lookup"><span data-stu-id="10f18-178">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="10f18-179">Esta seção aborda a renderização de estereoscópico usando a instanciação, usando código do modelo de aplicativo do Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="10f18-179">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="10f18-180">Cada câmera tem seu próprio destino de renderização (buffer de fundo) e matrizes de exibição e projeção no espaço Holographic.</span><span class="sxs-lookup"><span data-stu-id="10f18-180">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="10f18-181">Seu aplicativo precisará criar outros recursos baseados em câmera, como o buffer de profundidade, por câmera.</span><span class="sxs-lookup"><span data-stu-id="10f18-181">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="10f18-182">No modelo de aplicativo Holographic do Windows, fornecemos uma classe auxiliar para agrupar esses recursos em DX:: CameraResources.</span><span class="sxs-lookup"><span data-stu-id="10f18-182">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="10f18-183">Comece configurando as exibições de destino de renderização:</span><span class="sxs-lookup"><span data-stu-id="10f18-183">Start by setting up the render target views:</span></span>

<span data-ttu-id="10f18-184">De **AppMain:: render**:</span><span class="sxs-lookup"><span data-stu-id="10f18-184">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="10f18-185">**Usar a previsão para obter as matrizes de exibição e projeção da câmera**</span><span class="sxs-lookup"><span data-stu-id="10f18-185">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="10f18-186">As matrizes de exibição e projeção para cada câmera Holographic serão alteradas em todos os quadros.</span><span class="sxs-lookup"><span data-stu-id="10f18-186">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="10f18-187">Atualize os dados no buffer de constantes para cada câmera Holographic.</span><span class="sxs-lookup"><span data-stu-id="10f18-187">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="10f18-188">Faça isso depois de atualizar a previsão e antes de fazer qualquer chamada de desenho para essa câmera.</span><span class="sxs-lookup"><span data-stu-id="10f18-188">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="10f18-189">De **AppMain:: render**:</span><span class="sxs-lookup"><span data-stu-id="10f18-189">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="10f18-190">Aqui, mostramos como as matrizes são adquiridas da pose da câmera.</span><span class="sxs-lookup"><span data-stu-id="10f18-190">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="10f18-191">Durante esse processo, também obtemos o visor atual para a câmera.</span><span class="sxs-lookup"><span data-stu-id="10f18-191">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="10f18-192">Observe como fornecemos um sistema de coordenadas: esse é o mesmo sistema de coordenadas que usamos para entender olhar e é o mesmo que usamos para posicionar o cubo girando.</span><span class="sxs-lookup"><span data-stu-id="10f18-192">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="10f18-193">De **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="10f18-193">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="10f18-194">O visor deve ser definido em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="10f18-194">The viewport should be set each frame.</span></span> <span data-ttu-id="10f18-195">Seu sombreador de vértice (pelo menos) geralmente precisará de acesso aos dados de exibição/projeção.</span><span class="sxs-lookup"><span data-stu-id="10f18-195">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="10f18-196">De **CameraResources:: AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="10f18-196">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="10f18-197">**Renderizar para o buffer de fundo da câmera e confirmar o buffer de profundidade**:</span><span class="sxs-lookup"><span data-stu-id="10f18-197">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="10f18-198">É uma boa ideia verificar se o **TryGetViewTransform** foi bem-sucedido antes de tentar usar os dados de exibição/projeção, porque se o sistema de coordenadas não for localizável (por exemplo, o controle foi interrompido), seu aplicativo não poderá renderizar com ele para esse quadro.</span><span class="sxs-lookup"><span data-stu-id="10f18-198">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="10f18-199">O modelo só chamará **render** no cubo girando se a classe **CameraResources** indicar uma atualização bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="10f18-199">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="10f18-200">Para manter os hologramas onde um desenvolvedor ou um usuário os coloca no mundo, a realidade mista do Windows inclui recursos para [estabilização de imagem](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="10f18-200">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="10f18-201">A estabilização de imagem ajuda a ocultar a latência inerente em um pipeline de renderização para garantir as melhores experiências de Holographic para os usuários; um ponto de foco pode ser especificado para aprimorar ainda mais a estabilização de imagem ou um buffer de profundidade pode ser fornecido para computar a estabilização de imagem otimizada em tempo real.</span><span class="sxs-lookup"><span data-stu-id="10f18-201">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="10f18-202">Para obter melhores resultados, seu aplicativo deve fornecer um buffer de profundidade usando a API <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> .</span><span class="sxs-lookup"><span data-stu-id="10f18-202">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="10f18-203">A realidade mista do Windows pode usar informações de geometria do buffer de profundidade para otimizar a estabilização de imagem em tempo real.</span><span class="sxs-lookup"><span data-stu-id="10f18-203">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="10f18-204">O modelo de aplicativo Holographic do Windows confirma o buffer de profundidade do aplicativo por padrão, ajudando a otimizar a estabilidade do holograma.</span><span class="sxs-lookup"><span data-stu-id="10f18-204">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="10f18-205">De **AppMain:: render**:</span><span class="sxs-lookup"><span data-stu-id="10f18-205">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="10f18-206">O Windows processará sua textura de profundidade na GPU, portanto, deve ser possível usar o buffer de profundidade como um recurso de sombreador.</span><span class="sxs-lookup"><span data-stu-id="10f18-206">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="10f18-207">O ID3D11Texture2D que você cria deve estar em um formato sem tipo e deve ser associado como um modo de exibição de recurso de sombreador.</span><span class="sxs-lookup"><span data-stu-id="10f18-207">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="10f18-208">Aqui está um exemplo de como criar uma textura de profundidade que pode ser confirmada para estabilização de imagem.</span><span class="sxs-lookup"><span data-stu-id="10f18-208">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="10f18-209">Código para a **criação de recursos de buffer de profundidade para CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="10f18-209">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="10f18-210">**Desenhar conteúdo do Holographic**</span><span class="sxs-lookup"><span data-stu-id="10f18-210">**Draw holographic content**</span></span>

<span data-ttu-id="10f18-211">O modelo de aplicativo Holographic do Windows renderiza o conteúdo em estéreo usando a técnica recomendada de desenho de geometria de instância para um Texture2DArray de tamanho 2.</span><span class="sxs-lookup"><span data-stu-id="10f18-211">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="10f18-212">Vamos examinar a parte de instanciação disso e como ela funciona no Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="10f18-212">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="10f18-213">De **SpinningCubeRenderer:: render**:</span><span class="sxs-lookup"><span data-stu-id="10f18-213">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="10f18-214">Cada instância acessa uma matriz de exibição/projeção diferente do buffer de constantes.</span><span class="sxs-lookup"><span data-stu-id="10f18-214">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="10f18-215">Aqui está a estrutura de buffer constante, que é apenas uma matriz de 2 matrizes.</span><span class="sxs-lookup"><span data-stu-id="10f18-215">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="10f18-216">De **VertexShaderShared. HLSL**, incluído por **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="10f18-216">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="10f18-217">O índice de matriz de destino de renderização deve ser definido para cada pixel.</span><span class="sxs-lookup"><span data-stu-id="10f18-217">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="10f18-218">No trecho a seguir, output. ViewId é mapeado para a semântica de **SV_RenderTargetArrayIndex** .</span><span class="sxs-lookup"><span data-stu-id="10f18-218">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="10f18-219">Observe que isso requer suporte para um recurso de Direct3D 11,3 opcional, que permite que a semântica de índice de matriz de destino de renderização seja definida em qualquer estágio do sombreador.</span><span class="sxs-lookup"><span data-stu-id="10f18-219">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="10f18-220">De **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="10f18-220">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="10f18-221">De **VertexShaderShared. HLSL**, incluído por **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="10f18-221">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="10f18-222">Se você quiser usar suas técnicas de desenho com instância existente com esse método de desenho em uma matriz de destino de renderização estéreo, tudo o que você precisa fazer é desenhar duas vezes o número de instâncias que você normalmente tem.</span><span class="sxs-lookup"><span data-stu-id="10f18-222">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="10f18-223">No sombreador, divida **Input. Instid** por 2 para obter a ID da instância original, que pode ser indexada em (por exemplo) um buffer de dados por objeto: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="10f18-223">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="10f18-224">Observação importante sobre o processamento de conteúdo estéreo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="10f18-224">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="10f18-225">O Windows Mixed Reality dá suporte à capacidade de definir o índice de matriz de destino de renderização de qualquer estágio do sombreador; Normalmente, essa é uma tarefa que só podia ser feita no estágio do sombreador Geometry devido à maneira como a semântica é definida para o Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="10f18-225">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="10f18-226">Aqui, mostramos um exemplo completo de como configurar um pipeline de renderização apenas com os estágios do vértice e do sombreador de pixel definidos.</span><span class="sxs-lookup"><span data-stu-id="10f18-226">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="10f18-227">O código do sombreador é conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="10f18-227">The shader code is as described above.</span></span>

<span data-ttu-id="10f18-228">De **SpinningCubeRenderer:: render**:</span><span class="sxs-lookup"><span data-stu-id="10f18-228">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="10f18-229">Observação importante sobre a renderização em dispositivos não HoloLens</span><span class="sxs-lookup"><span data-stu-id="10f18-229">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="10f18-230">Definir o índice de matriz de destino de renderização no sombreador de vértice requer que o driver de gráficos dê suporte a um recurso de Direct3D 11,3 opcional, ao qual o HoloLens oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="10f18-230">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="10f18-231">Seu aplicativo pode ser capaz de implementar com segurança apenas essa técnica para renderização e todos os requisitos serão atendidos para execução no Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10f18-231">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="10f18-232">Pode ser o caso em que você também deseja usar o emulador do HoloLens, que pode ser uma poderosa ferramenta de desenvolvimento para seu aplicativo Holographic e dar suporte a dispositivos de headset de imersão de realidade mista do Windows que estão conectados a PCs com Windows 10.</span><span class="sxs-lookup"><span data-stu-id="10f18-232">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="10f18-233">O suporte para o caminho de renderização não HoloLens-e, portanto, para toda a realidade mista do Windows, também é incorporado ao modelo de aplicativo Holographic do Windows.</span><span class="sxs-lookup"><span data-stu-id="10f18-233">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="10f18-234">No código do modelo, você encontrará código para permitir que seu aplicativo Holographic seja executado na GPU em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="10f18-234">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="10f18-235">Veja como a classe **DeviceResources** verifica esse suporte de recurso opcional.</span><span class="sxs-lookup"><span data-stu-id="10f18-235">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="10f18-236">De **DeviceResources:: CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="10f18-236">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="10f18-237">Para dar suporte à renderização sem esse recurso opcional, seu aplicativo deve usar um sombreador de geometria para definir o índice de matriz de destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="10f18-237">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="10f18-238">Esse trecho de código seria adicionado *após* **VSSetConstantBuffers**, e *antes* de **PSSetShader** no exemplo de códigos mostrado na seção anterior que explica como renderizar o estéreo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10f18-238">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="10f18-239">De **SpinningCubeRenderer:: render**:</span><span class="sxs-lookup"><span data-stu-id="10f18-239">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="10f18-240">**HLSL observação**: nesse caso, você também deve carregar um sombreador de vértice ligeiramente modificado que passa o índice de matriz de destino de renderização para o sombreador de geometria usando uma semântica de sombreador sempre permitido, como TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="10f18-240">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="10f18-241">O sombreador de geometria não precisa fazer nenhum trabalho; o sombreador de geometria de modelo passa por todos os dados, com exceção do índice de matriz de destino de renderização, que é usado para definir a semântica de SV_RenderTargetArrayIndex.</span><span class="sxs-lookup"><span data-stu-id="10f18-241">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="10f18-242">Código de modelo de aplicativo para **GeometryShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="10f18-242">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="10f18-243">Apresentar</span><span class="sxs-lookup"><span data-stu-id="10f18-243">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="10f18-244">Habilitar o quadro Holographic para apresentar a cadeia de permuta</span><span class="sxs-lookup"><span data-stu-id="10f18-244">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="10f18-245">Com a realidade mista do Windows, o sistema controla a cadeia de permuta.</span><span class="sxs-lookup"><span data-stu-id="10f18-245">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="10f18-246">Em seguida, o sistema gerencia a apresentação de quadros para cada câmera Holographic para garantir uma experiência de usuário de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="10f18-246">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="10f18-247">Ele também fornece uma atualização de visor a cada quadro, para cada câmera, para otimizar aspectos do sistema, como estabilização de imagem ou captura de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="10f18-247">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="10f18-248">Portanto, um aplicativo Holographic usando o DirectX não chama a **presente** em uma cadeia de permuta dxgi.</span><span class="sxs-lookup"><span data-stu-id="10f18-248">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="10f18-249">Em vez disso, você usa a classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> para apresentar todos os permuta de um quadro depois de terminar de desenhá-lo.</span><span class="sxs-lookup"><span data-stu-id="10f18-249">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="10f18-250">De **DeviceResources::P reenviada**:</span><span class="sxs-lookup"><span data-stu-id="10f18-250">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="10f18-251">Por padrão, essa API aguarda a conclusão do quadro antes de retornar.</span><span class="sxs-lookup"><span data-stu-id="10f18-251">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="10f18-252">Os aplicativos Holographic devem aguardar até que o quadro anterior seja concluído antes de iniciar o trabalho em um novo quadro, pois isso reduz a latência e permite resultados melhores de previsões de quadro Holographic.</span><span class="sxs-lookup"><span data-stu-id="10f18-252">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="10f18-253">Essa não é uma regra difícil e, se você tiver quadros que demoram mais de uma atualização de tela para renderização, você pode desabilitar essa espera passando o parâmetro HolographicFramePresentWaitBehavior para <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="10f18-253">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="10f18-254">Nesse caso, você provavelmente usaria um thread de renderização assíncrona para manter uma carga contínua na GPU.</span><span class="sxs-lookup"><span data-stu-id="10f18-254">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="10f18-255">Observe que a taxa de atualização do dispositivo HoloLens é 60, em que um quadro tem uma duração de aproximadamente 16 ms.</span><span class="sxs-lookup"><span data-stu-id="10f18-255">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="10f18-256">Os dispositivos de headset de imersão podem variar de 60 a 90Hz; ao atualizar a exibição em 90 Hz, cada quadro terá uma duração de aproximadamente 11 MS.</span><span class="sxs-lookup"><span data-stu-id="10f18-256">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="10f18-257">Manipule cenários DeviceLost em cooperação com o HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="10f18-257">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="10f18-258">Os aplicativos DirectX 11 normalmente desejariam verificar o HRESULT retornado pela função **presente** da cadeia de permuta dxgi para descobrir se houve um erro de **DeviceLost** .</span><span class="sxs-lookup"><span data-stu-id="10f18-258">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="10f18-259">A classe <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> lida com isso para você.</span><span class="sxs-lookup"><span data-stu-id="10f18-259">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="10f18-260">Inspecione o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> que ele retorna para descobrir se você precisa liberar e recriar o dispositivo Direct3D e os recursos baseados em dispositivo.</span><span class="sxs-lookup"><span data-stu-id="10f18-260">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="10f18-261">Observe que, se o dispositivo Direct3D foi perdido e você o recriou, precisa dizer ao <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> para começar a usar o novo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="10f18-261">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="10f18-262">A cadeia de permuta será recriada para este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="10f18-262">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="10f18-263">De **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="10f18-263">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="10f18-264">Depois que o quadro for apresentado, você poderá retornar ao loop do programa principal e permitir que ele continue para o próximo quadro.</span><span class="sxs-lookup"><span data-stu-id="10f18-264">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="10f18-265">PCs de gráficos híbridos e aplicativos de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="10f18-265">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="10f18-266">**Os** PCs de atualização do Windows 10 para criadores podem ser configurados com GPUs discretas e integradas.</span><span class="sxs-lookup"><span data-stu-id="10f18-266">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="10f18-267">Com esses tipos de computadores, o Windows escolherá o adaptador ao qual o headset está conectado.</span><span class="sxs-lookup"><span data-stu-id="10f18-267">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="10f18-268">Os aplicativos devem garantir que o dispositivo DirectX criado por ele use o mesmo adaptador.</span><span class="sxs-lookup"><span data-stu-id="10f18-268">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="10f18-269">O código de exemplo de Direct3D mais geral demonstra como criar um dispositivo DirectX usando o adaptador de hardware padrão, que em um sistema híbrido pode não ser o mesmo usado para o headset.</span><span class="sxs-lookup"><span data-stu-id="10f18-269">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="10f18-270">Para solucionar os problemas que isso possa causar, use o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> de <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId () ou <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. Adaptadorid ().</span><span class="sxs-lookup"><span data-stu-id="10f18-270">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="10f18-271">Esse adaptadorid pode então ser usado para selecionar o DXGIAdapter correto usando IDXGIFactory4. EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="10f18-271">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="10f18-272">De **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="10f18-272">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="10f18-273">Código para **Atualizar DeviceResources:: CreateDeviceResources para usar IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="10f18-273">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="10f18-274">**Gráficos híbridos e Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="10f18-274">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="10f18-275">O uso de Media Foundation em sistemas híbridos pode causar problemas em que o vídeo não será renderizado ou a textura do vídeo está corrompida.</span><span class="sxs-lookup"><span data-stu-id="10f18-275">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="10f18-276">Isso pode ocorrer porque Media Foundation está padronizando para um comportamento do sistema, conforme mencionado acima.</span><span class="sxs-lookup"><span data-stu-id="10f18-276">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="10f18-277">Em alguns cenários, a criação de um ID3D11Device separado é necessária para dar suporte a vários threads e os sinalizadores de criação corretos são definidos.</span><span class="sxs-lookup"><span data-stu-id="10f18-277">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="10f18-278">Ao inicializar o ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT sinalizador deve ser definido como parte do D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="10f18-278">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="10f18-279">Depois que o dispositivo e o contexto forem criados, chame <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar multithreading.</span><span class="sxs-lookup"><span data-stu-id="10f18-279">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="10f18-280">Para associar o dispositivo ao <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use a função <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: ResetDevice</a> .</span><span class="sxs-lookup"><span data-stu-id="10f18-280">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="10f18-281">Código para **associar um ID3D11Device com IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="10f18-281">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="10f18-282">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10f18-282">See also</span></span>
* [<span data-ttu-id="10f18-283">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="10f18-283">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="10f18-284">Como usar o emulador do HoloLens</span><span class="sxs-lookup"><span data-stu-id="10f18-284">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)

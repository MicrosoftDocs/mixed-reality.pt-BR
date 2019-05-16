---
title: Processamento no DirectX
description: Explica a renderização holographic para Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, renderização, gráficos 3D, HolographicFrame, renderizar loop, o loop de atualização, o passo a passo, o código de exemplo
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629032"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="15b5d-104">Processamento no DirectX</span><span class="sxs-lookup"><span data-stu-id="15b5d-104">Rendering in DirectX</span></span>

<span data-ttu-id="15b5d-105">Realidade mista do Windows se baseia no DirectX para produzir rico, 3D gráfica experiências para os usuários.</span><span class="sxs-lookup"><span data-stu-id="15b5d-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="15b5d-106">A abstração de renderização fica logo acima DirectX e permite que um aplicativo justificar a posição e orientação de um ou mais observadores de uma cena holográfica, previstos pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="15b5d-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="15b5d-107">O desenvolvedor pode, em seguida, localizar seus hologramas em relação a cada câmera, permitindo que o aplicativo renderizar essas hologramas em vários sistemas de coordenadas espaciais conforme o usuário move.</span><span class="sxs-lookup"><span data-stu-id="15b5d-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="15b5d-108">Atualização para o quadro atual</span><span class="sxs-lookup"><span data-stu-id="15b5d-108">Update for the current frame</span></span>

<span data-ttu-id="15b5d-109">Para atualizar o estado do aplicativo para hologramas, uma vez por quadro, o aplicativo irá:</span><span class="sxs-lookup"><span data-stu-id="15b5d-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="15b5d-110">Obter um <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> do sistema de gerenciamento de exibição.</span><span class="sxs-lookup"><span data-stu-id="15b5d-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="15b5d-111">Renderizar a cena com a previsão atual em que a visualização da câmera será quando a atualização é concluída.</span><span class="sxs-lookup"><span data-stu-id="15b5d-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="15b5d-112">Observe que pode haver mais de uma câmera para a cena holográfica.</span><span class="sxs-lookup"><span data-stu-id="15b5d-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="15b5d-113">Para renderizar a modos de exibição holográfico câmera, uma vez por quadro, o aplicativo irá:</span><span class="sxs-lookup"><span data-stu-id="15b5d-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="15b5d-114">Para cada câmera renderizar a cena do quadro atual, usando as matrizes de projeção e exibição de câmera do sistema.</span><span class="sxs-lookup"><span data-stu-id="15b5d-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="15b5d-115">Criar um novo quadro holográfico e obtenha sua previsão</span><span class="sxs-lookup"><span data-stu-id="15b5d-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="15b5d-116">O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tem informações de que o aplicativo precisa para atualizar e renderizar o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="15b5d-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="15b5d-117">O aplicativo começa a cada novo quadro chamando o **CreateNextFrame** método.</span><span class="sxs-lookup"><span data-stu-id="15b5d-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="15b5d-118">Quando este método é chamado, as previsões são feitas usando os dados de sensor mais recentes disponíveis e encapsulados no **CurrentPrediction** objeto.</span><span class="sxs-lookup"><span data-stu-id="15b5d-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="15b5d-119">Um novo objeto de quadro deve ser usado para cada quadro processado conforme ele é válido somente por um instante no tempo.</span><span class="sxs-lookup"><span data-stu-id="15b5d-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="15b5d-120">O **CurrentPrediction** propriedade contém informações como a posição da câmera.</span><span class="sxs-lookup"><span data-stu-id="15b5d-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="15b5d-121">As informações são extrapoladas para o momento exato no tempo quando o quadro deve ser visível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="15b5d-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="15b5d-122">O código a seguir foi extraído do livro **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="15b5d-123">Atualizações do processo de câmera</span><span class="sxs-lookup"><span data-stu-id="15b5d-123">Process camera updates</span></span>

<span data-ttu-id="15b5d-124">Buffers de fundo podem alterar o quadro a quadro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="15b5d-125">Necessidades de seu aplicativo para validar o de volta do buffer para cada câmera e de versão e recriar as exibições de recursos e buffers de profundidade conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="15b5d-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="15b5d-126">Observe que o conjunto de poses na previsão é a lista autoritativa de câmeras que está sendo usado no quadro atual.</span><span class="sxs-lookup"><span data-stu-id="15b5d-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="15b5d-127">Normalmente, você deve usar esta lista para iterar no conjunto de câmeras.</span><span class="sxs-lookup"><span data-stu-id="15b5d-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="15b5d-128">Partir **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="15b5d-129">Partir **DeviceResources::EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="15b5d-130">Obter o sistema de coordenadas para usar como base para renderização</span><span class="sxs-lookup"><span data-stu-id="15b5d-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="15b5d-131">Realidade mista do Windows permite que seu aplicativo crie vários [sistemas de coordenadas](coordinate-systems-in-directx.md) conforme necessário, como o quadro de referência anexadas e o quadro estacionário de referência, que monitoram locais no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="15b5d-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="15b5d-132">Seu aplicativo pode usar esses sistemas de coordenadas raciocinar sobre onde a renderizar hologramas cada quadro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="15b5d-133">Ao solicitar as coordenadas de uma API, você sempre passará a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> dentro do qual você deseja que essas coordenadas sejam expressas.</span><span class="sxs-lookup"><span data-stu-id="15b5d-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="15b5d-134">Partir **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="15b5d-135">Esses sistemas de coordenadas, em seguida, pode ser usados para gerar as matrizes de exibição estéreo ao renderizar o conteúdo na sua cena.</span><span class="sxs-lookup"><span data-stu-id="15b5d-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="15b5d-136">Partir **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="15b5d-137">Olhar de processo e o gesto de entrada</span><span class="sxs-lookup"><span data-stu-id="15b5d-137">Process gaze and gesture input</span></span>

<span data-ttu-id="15b5d-138">[Olhares](gaze-in-directx.md) e [mão](hands-and-motion-controllers-in-directx.md) não são baseados em tempo de entrada e, portanto, não precisa atualizar no **StepTimer** função.</span><span class="sxs-lookup"><span data-stu-id="15b5d-138">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="15b5d-139">No entanto, essa entrada é algo que o aplicativo precisa examinar cada quadro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-139">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="15b5d-140">Processar atualizações baseadas em tempo</span><span class="sxs-lookup"><span data-stu-id="15b5d-140">Process time-based updates</span></span>

<span data-ttu-id="15b5d-141">Qualquer aplicativo de renderização em tempo real precisará de alguma forma para processar atualizações com base no tempo; nós fornecemos uma maneira de fazer isso no modelo de aplicativo do Windows Holographic por meio de um **StepTimer** implementação.</span><span class="sxs-lookup"><span data-stu-id="15b5d-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="15b5d-142">Isso é semelhante ao StepTimer fornecido no modelo de aplicativo de UWP do DirectX 11, portanto, se você já viu esse modelo você deverá estar na Terra familiar.</span><span class="sxs-lookup"><span data-stu-id="15b5d-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="15b5d-143">A classe auxiliar StepTimer exemplo é capaz de fornecer atualizações de etapa de tempo fixas, bem como atualizações de etapa de tempo variável e o modo padrão é a variável de períodos.</span><span class="sxs-lookup"><span data-stu-id="15b5d-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="15b5d-144">No caso de renderização holográfica, especificamente escolhemos não colocar muito na função de temporizador.</span><span class="sxs-lookup"><span data-stu-id="15b5d-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="15b5d-145">Isso ocorre porque você pode configurá-lo para ser uma etapa tempo fixo, caso em que ele pode ser chamado mais de uma vez por quadro – ou não, para alguns quadros – e nossas atualizações de dados holográfica devem acontecer uma vez por quadro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="15b5d-146">Partir **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="15b5d-147">Posição e rotação hologramas em seu sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="15b5d-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="15b5d-148">Se você estiver operando em um único sistema de coordenadas, assim como o modelo com o **SpatialStationaryReferenceFrame**, esse processo não é diferente da que você está caso contrário, usado para em gráficos 3D.</span><span class="sxs-lookup"><span data-stu-id="15b5d-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="15b5d-149">Aqui, podemos girar o cubo e definir a matriz do modelo em relação a posição no sistema de coordenadas parado.</span><span class="sxs-lookup"><span data-stu-id="15b5d-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="15b5d-150">Partir **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-150">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="15b5d-151">**Nota sobre cenários avançados:** O cubo de rotação é um exemplo muito simples de como posicionar um holograma dentro de um quadro de referência único.</span><span class="sxs-lookup"><span data-stu-id="15b5d-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="15b5d-152">Também é possível [usar vários SpatialCoordinateSystems](coordinate-systems-in-directx.md) no mesmo quadro renderizado, ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="15b5d-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="15b5d-153">Atualizar dados do buffer de constantes</span><span class="sxs-lookup"><span data-stu-id="15b5d-153">Update constant buffer data</span></span>

<span data-ttu-id="15b5d-154">Transformações de modelo de conteúdo são atualizadas como de costume.</span><span class="sxs-lookup"><span data-stu-id="15b5d-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="15b5d-155">Agora, você será computada transformações válidas para o sistema de coordenadas que você vai ser renderizar em.</span><span class="sxs-lookup"><span data-stu-id="15b5d-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="15b5d-156">Partir **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-156">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="15b5d-157">E sobre as transformações de projeção e exibição?</span><span class="sxs-lookup"><span data-stu-id="15b5d-157">What about view and projection transforms?</span></span> <span data-ttu-id="15b5d-158">Para obter melhores resultados, podemos desejar esperar até que quase tudo pronto para nossas chamadas de desenho antes de passarmos esses.</span><span class="sxs-lookup"><span data-stu-id="15b5d-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="15b5d-159">Renderizar o quadro atual</span><span class="sxs-lookup"><span data-stu-id="15b5d-159">Render the current frame</span></span>

<span data-ttu-id="15b5d-160">Renderização no Windows Mixed Reality não é muito diferente da renderização em uma exibição mono 2D, mas há algumas diferenças que você precisa estar atento:</span><span class="sxs-lookup"><span data-stu-id="15b5d-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="15b5d-161">Previsões de quadro holográfica são importantes.</span><span class="sxs-lookup"><span data-stu-id="15b5d-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="15b5d-162">Quanto mais próximo a previsão é quando o quadro é apresentado, serão a sua hologramas melhor aparência.</span><span class="sxs-lookup"><span data-stu-id="15b5d-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="15b5d-163">Windows Mixed Reality controla os modos de exibição da câmera.</span><span class="sxs-lookup"><span data-stu-id="15b5d-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="15b5d-164">Você precisa renderizar a cada um, porque o quadro holográfico será ser apresentando-os para que você mais tarde.</span><span class="sxs-lookup"><span data-stu-id="15b5d-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="15b5d-165">É recomendável estéreo renderização ser feito usando a instância de desenho para uma matriz de destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="15b5d-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="15b5d-166">O modelo de aplicativo holográfica usa a abordagem recomendada de desenho de instância para uma matriz de destino de renderização, que usa um modo de exibição de destino de renderização em um **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="15b5d-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="15b5d-167">Se você deseja processar sem o uso de instanciação estéreo, você precisará criar dois não matriz RenderTargetViews (uma para cada olho) que cada referência dos dois intervalos nos **Texture2DArray** fornecido para o aplicativo do sistema.</span><span class="sxs-lookup"><span data-stu-id="15b5d-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="15b5d-168">Isso não é recomendado, pois normalmente é significativamente mais lenta do que de instanciação.</span><span class="sxs-lookup"><span data-stu-id="15b5d-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="15b5d-169">Obter uma previsão HolographicFrame atualizada</span><span class="sxs-lookup"><span data-stu-id="15b5d-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="15b5d-170">Atualizando a previsão de quadro aumenta a eficácia de estabilização da imagem e permite o posicionamento mais preciso de hologramas devido ao tempo mais curto entre a previsão e quando o quadro é visível para o usuário.</span><span class="sxs-lookup"><span data-stu-id="15b5d-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="15b5d-171">Idealmente, atualize sua previsão de quadro apenas antes da renderização.</span><span class="sxs-lookup"><span data-stu-id="15b5d-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="15b5d-172">Renderizar para cada câmera</span><span class="sxs-lookup"><span data-stu-id="15b5d-172">Render to each camera</span></span>

<span data-ttu-id="15b5d-173">Executar um loop no conjunto de câmera poses na previsão e renderizar em cada câmera neste conjunto.</span><span class="sxs-lookup"><span data-stu-id="15b5d-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="15b5d-174">**Configurar sua passagem de renderização**</span><span class="sxs-lookup"><span data-stu-id="15b5d-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="15b5d-175">Realidade mista do Windows usa renderização estereoscópica para aprimorar a ilusão de profundidade e renderizar stereoscopically, portanto, à esquerda e a exibição à direita são Active Directory.</span><span class="sxs-lookup"><span data-stu-id="15b5d-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="15b5d-176">Com a renderização estereoscópica há um deslocamento entre as duas exibições, o cérebro pode reconciliar como profundidade real.</span><span class="sxs-lookup"><span data-stu-id="15b5d-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="15b5d-177">Esta seção aborda estereoscópica renderização usando instanciamento, usando o código do modelo de aplicativo do Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="15b5d-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="15b5d-178">Cada câmera tem suas própria renderização projeção e exibição e de destino (buffer de fundo), as matrizes, no espaço de holographic.</span><span class="sxs-lookup"><span data-stu-id="15b5d-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="15b5d-179">Seu aplicativo precisará criar os outros com base em câmera recursos - como o buffer de profundidade – em uma base por câmera.</span><span class="sxs-lookup"><span data-stu-id="15b5d-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="15b5d-180">O modelo de aplicativo do Windows Holographic, fornecemos uma classe auxiliar para agrupar esses recursos em DX::CameraResources.</span><span class="sxs-lookup"><span data-stu-id="15b5d-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="15b5d-181">Comece definindo os modos de exibição de destino de renderização:</span><span class="sxs-lookup"><span data-stu-id="15b5d-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="15b5d-182">Partir **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-182">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="15b5d-183">**Use a previsão para obter as matrizes de projeção e exibição para a câmera**</span><span class="sxs-lookup"><span data-stu-id="15b5d-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="15b5d-184">As matrizes de projeção e exibição para cada câmera holográfica serão alterado em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="15b5d-185">Atualize os dados no buffer de constantes para cada câmera holográfica.</span><span class="sxs-lookup"><span data-stu-id="15b5d-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="15b5d-186">Fazer isso depois que você atualizou a previsão e antes de fazer qualquer desenho chama para essa câmera.</span><span class="sxs-lookup"><span data-stu-id="15b5d-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="15b5d-187">Partir **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-187">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="15b5d-188">Aqui, mostramos como as matrizes são adquiridas do pose a câmera.</span><span class="sxs-lookup"><span data-stu-id="15b5d-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="15b5d-189">Durante esse processo também obtemos o visor atual para a câmera.</span><span class="sxs-lookup"><span data-stu-id="15b5d-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="15b5d-190">Observe como fornecemos um sistema de coordenadas: isso é o mesmo sistema de coordenadas são usados para entender a olhar e é o mesmo são usados para posicionar o cubo giratório.</span><span class="sxs-lookup"><span data-stu-id="15b5d-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="15b5d-191">Partir **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="15b5d-192">O visor deve ser definido de cada quadro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-192">The viewport should be set each frame.</span></span> <span data-ttu-id="15b5d-193">Seu sombreador de vértice (pelo menos) geralmente precisará ter acesso aos dados/projeção de exibição.</span><span class="sxs-lookup"><span data-stu-id="15b5d-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="15b5d-194">Partir **CameraResources::AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="15b5d-195">**Renderizar o buffer de fundo da câmera e confirmar o buffer de profundidade**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="15b5d-196">É uma boa ideia verificar isso **TryGetViewTransform** com êxito antes de tentar usar os dados de exibição/projeção, porque se o sistema de coordenadas nao é localizável (por exemplo, rastreamento foi interrompido) seu aplicativo não é possível renderizar com ele para que quadro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="15b5d-197">O modelo só chama **renderizar** no cubo de rotação se o **CameraResources** classe indica uma atualização bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="15b5d-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="15b5d-198">Para manter hologramas onde um desenvolvedor ou um usuário coloca no mundo, Windows Mixed Reality inclui recursos para [estabilização da imagem](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="15b5d-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="15b5d-199">Estabilização da imagem ajuda a ocultar a latência inerente em um pipeline de renderização para garantir que as experiências holográfica melhor para os usuários. um ponto de foco pode ser especificado para aprimorar ainda mais a estabilização de imagem ou um buffer de profundidade pode ser fornecido computar otimizado estabilização da imagem em tempo real.</span><span class="sxs-lookup"><span data-stu-id="15b5d-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="15b5d-200">Para obter melhores resultados, seu aplicativo deve fornecer um buffer de profundidade usando o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span><span class="sxs-lookup"><span data-stu-id="15b5d-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="15b5d-201">Realidade mista do Windows, em seguida, pode usar informações de geometria do buffer de profundidade para otimizar a estabilização da imagem em tempo real.</span><span class="sxs-lookup"><span data-stu-id="15b5d-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="15b5d-202">O modelo de aplicativo do Windows Holographic confirma o buffer de profundidade do aplicativo por padrão, ajudando a otimizar a estabilidade holograma.</span><span class="sxs-lookup"><span data-stu-id="15b5d-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="15b5d-203">Partir **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-203">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="15b5d-204">Windows processará sua textura de profundidade na GPU, portanto, deve ser possível usar seu buffer de profundidade como um recurso de sombreador.</span><span class="sxs-lookup"><span data-stu-id="15b5d-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="15b5d-205">O ID3D11Texture2D que você criar deve estar em um formato sem especificação de tipo e deve estar associado como um modo de exibição de recurso do sombreador.</span><span class="sxs-lookup"><span data-stu-id="15b5d-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="15b5d-206">Aqui está um exemplo de como criar uma textura de profundidade que pode ser confirmada para a estabilização da imagem.</span><span class="sxs-lookup"><span data-stu-id="15b5d-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="15b5d-207">Código para o **criação de recursos de buffer de profundidade para CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="15b5d-208">**Desenhar conteúdo holográfico**</span><span class="sxs-lookup"><span data-stu-id="15b5d-208">**Draw holographic content**</span></span>

<span data-ttu-id="15b5d-209">O modelo de aplicativo do Windows Holographic renderiza o conteúdo em estéreo, usando a técnica recomendada da instância de geometria de desenho para uma Texture2DArray de tamanho 2.</span><span class="sxs-lookup"><span data-stu-id="15b5d-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="15b5d-210">Vamos examinar a instanciação parte dessa situação, e como ele funciona no Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="15b5d-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="15b5d-211">Partir **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-211">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="15b5d-212">Cada instância acessa uma matriz de projeção/de exibição diferente do buffer constante.</span><span class="sxs-lookup"><span data-stu-id="15b5d-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="15b5d-213">Aqui está a estrutura de buffer de constantes, que é apenas uma matriz de matrizes de 2.</span><span class="sxs-lookup"><span data-stu-id="15b5d-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="15b5d-214">Partir **VertexShaderShared.hlsl**, incluído por **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="15b5d-215">O índice de matriz de destino de renderização deve ser definido para cada pixel.</span><span class="sxs-lookup"><span data-stu-id="15b5d-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="15b5d-216">No trecho a seguir, output.viewId é mapeado para o **SV_RenderTargetArrayIndex** semântica.</span><span class="sxs-lookup"><span data-stu-id="15b5d-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="15b5d-217">Observe que isso requer suporte para um recurso opcional do Direct3D 11.3, que permite que o índice de matriz de destino de renderização semântica seja definida de qualquer estágio de sombreador.</span><span class="sxs-lookup"><span data-stu-id="15b5d-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="15b5d-218">From **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-218">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="15b5d-219">Partir **VertexShaderShared.hlsl**, incluído por **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="15b5d-220">Se você quiser usar a instância existente, técnicas de desenho com esse método de desenho para um aparelho de som renderizam a matriz de destino, tudo o que você precisa fazer é desenhar duas vezes o número de instâncias que você normalmente precisa.</span><span class="sxs-lookup"><span data-stu-id="15b5d-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="15b5d-221">No sombreador, divida **input.instId** por 2 para obter a ID da instância original, que podem ser indexadas em (por exemplo) em um buffer de dados por objeto: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="15b5d-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="15b5d-222">Observação importante sobre como renderizar conteúdo estéreo em HoloLens</span><span class="sxs-lookup"><span data-stu-id="15b5d-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="15b5d-223">Realidade mista do Windows oferece suporte a capacidade de definir o índice de matriz de destino de renderização de qualquer estágio de sombreador; Normalmente, essa é uma tarefa que só pode ser feita no estágio de sombreador de geometria devido à maneira como a semântica é definida para o Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="15b5d-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="15b5d-224">Aqui, mostramos um exemplo completo de como configurar um pipeline de renderização com apenas o conjunto de estágios de pixel e vértice sombreador.</span><span class="sxs-lookup"><span data-stu-id="15b5d-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="15b5d-225">O código de sombreador é conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="15b5d-225">The shader code is as described above.</span></span>

<span data-ttu-id="15b5d-226">Partir **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-226">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="15b5d-227">Observação importante sobre como renderizar em dispositivos não HoloLens</span><span class="sxs-lookup"><span data-stu-id="15b5d-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="15b5d-228">A definição de índice da matriz de destino de renderização no sombreador de vértice requer que o driver de gráficos oferece suporte a um recurso opcional do Direct3D 11.3, que oferece suporte a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15b5d-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="15b5d-229">Seu aplicativo pode ser capaz de implementar com segurança apenas essa técnica para renderização e todos os requisitos para execução em que o Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15b5d-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="15b5d-230">Ele pode ser o caso em que você deseja usar o emulador de HoloLens, bem, o que pode ser uma ferramenta de desenvolvimento avançado para seu aplicativo holográfica – e dar suporte a dispositivos de fone de ouvido imersivo Windows Mixed Reality anexados a computadores com Windows 10.</span><span class="sxs-lookup"><span data-stu-id="15b5d-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="15b5d-231">Suporte para o caminho de renderização não HoloLens - e, portanto, para todos os Windows Mixed Reality - também é criado no modelo de aplicativo do Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="15b5d-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="15b5d-232">O código de modelo, você encontrará o código para habilitar seu aplicativo holográfico seja executado no GPU no seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="15b5d-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="15b5d-233">Aqui está como o **DeviceResources** classe procura esse suporte de recurso opcional.</span><span class="sxs-lookup"><span data-stu-id="15b5d-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="15b5d-234">Partir **DeviceResources::CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="15b5d-235">Para dar suporte à renderização sem esse recurso opcional, seu aplicativo deve usar um sombreador de geometria para definir o índice de matriz de destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="15b5d-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="15b5d-236">Este trecho de código seria adicionado *após* **VSSetConstantBuffers**, e *antes* **PSSetShader** no exemplo de código mostrado anteriormente na seção que explica como renderizar estéreo em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15b5d-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="15b5d-237">Partir **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-237">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="15b5d-238">**OBSERVAÇÃO DE HLSL**: Nesse caso, você também deve carregar um sombreador de vértice ligeiramente modificada que passa o índice de matriz de destino de renderização para o sombreador de geometria usando uma semântica, como TEXCOORD0 de sombreador sempre permitidos.</span><span class="sxs-lookup"><span data-stu-id="15b5d-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="15b5d-239">O sombreador de geometria não tem que fazer qualquer trabalho; o sombreador de geometria do modelo passa por todos os dados, exceto o índice de matriz de destino de renderização, que é usado para definir o SV_RenderTargetArrayIndex semântica.</span><span class="sxs-lookup"><span data-stu-id="15b5d-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="15b5d-240">Código de modelo de aplicativo do **GeometryShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-240">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="15b5d-241">Apresentar</span><span class="sxs-lookup"><span data-stu-id="15b5d-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="15b5d-242">Habilitar o quadro holographic apresentar a cadeia de troca</span><span class="sxs-lookup"><span data-stu-id="15b5d-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="15b5d-243">Com o Windows Mixed Reality, o sistema controla a cadeia de troca.</span><span class="sxs-lookup"><span data-stu-id="15b5d-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="15b5d-244">O sistema, em seguida, gerencia os quadros de apresentação para cada câmera holographic para garantir uma experiência de usuário de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="15b5d-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="15b5d-245">Ele também fornece uma atualização do visor em cada quadro, para cada câmera, para otimizar os aspectos do sistema, como a estabilização da imagem ou a captura de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="15b5d-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="15b5d-246">Portanto, um aplicativo holográfico usando o DirectX não chama **presente** corrente de troca um DXGI.</span><span class="sxs-lookup"><span data-stu-id="15b5d-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="15b5d-247">Em vez disso, você usa o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> classe apresentar todas as cadeias de permuta para um quadro quando você terminar desenhá-la.</span><span class="sxs-lookup"><span data-stu-id="15b5d-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="15b5d-248">Partir **DeviceResources::Present**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="15b5d-249">Por padrão, essa API aguarda o quadro concluir antes de retornar.</span><span class="sxs-lookup"><span data-stu-id="15b5d-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="15b5d-250">Aplicativos holográfico devem aguardar o quadro anterior seja concluída antes de começar a trabalhar em um novo quadro, porque isso reduz a latência e permite que para obter melhores resultados de previsões de quadro holográfica.</span><span class="sxs-lookup"><span data-stu-id="15b5d-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="15b5d-251">Isso não é uma regra de disco rígida e, se você tiver quadros que demoram mais do que a atualização de uma tela para renderizar, você podem desabilitar essa espera, passando o parâmetro HolographicFramePresentWaitBehavior <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="15b5d-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="15b5d-252">Nesse caso, você usaria provavelmente um thread de renderização assíncrona para manter uma carga contínua na GPU.</span><span class="sxs-lookup"><span data-stu-id="15b5d-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="15b5d-253">Observe que a taxa de atualização do dispositivo HoloLens é 60hz, em que um quadro tem uma duração de aproximadamente 16 ms.</span><span class="sxs-lookup"><span data-stu-id="15b5d-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="15b5d-254">Dispositivos de fone de ouvido imersivo podem variar de 60hz a 90hz; ao atualizar a exibição a 90 hz, cada quadro terá uma duração de aproximadamente 11 ms.</span><span class="sxs-lookup"><span data-stu-id="15b5d-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="15b5d-255">Lidar com cenários de DeviceLost em cooperação com o HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="15b5d-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="15b5d-256">Aplicativos DirectX 11 geralmente deseja verificar o HRESULT retornado pela cadeia de troca DXGI **presente** função para descobrir se houve uma **DeviceLost** erro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="15b5d-257">O <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> classe manipula isso para você.</span><span class="sxs-lookup"><span data-stu-id="15b5d-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="15b5d-258">Inspecione o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> retorna para descobrir se você precisa liberar e recriar o dispositivo Direct3D e os recursos com base em dispositivo.</span><span class="sxs-lookup"><span data-stu-id="15b5d-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="15b5d-259">Observe que, se o dispositivo Direct3D foi perdido e você recriá-lo, você precisa informar o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> para começar a usar o novo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="15b5d-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="15b5d-260">A cadeia de troca será recriada para este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="15b5d-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="15b5d-261">Partir **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="15b5d-262">Depois que o quadro é apresentado, você pode retornar para o loop de programa principal e permitir que ele continue para o próximo quadro.</span><span class="sxs-lookup"><span data-stu-id="15b5d-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="15b5d-263">PCs de elementos gráficos híbridos e aplicativos de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="15b5d-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="15b5d-264">Windows 10 Creators Update PCs podem ser configurados com **ambos** discretos e integradas de GPUs.</span><span class="sxs-lookup"><span data-stu-id="15b5d-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="15b5d-265">Com esses tipos de computadores, o Windows escolherá o fone de ouvido está conectado ao adaptador.</span><span class="sxs-lookup"><span data-stu-id="15b5d-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="15b5d-266">Aplicativos devem garantir que o dispositivo DirectX cria usa o mesmo adaptador.</span><span class="sxs-lookup"><span data-stu-id="15b5d-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="15b5d-267">Código de exemplo mais geral do Direct3D demonstra como criar um dispositivo DirectX usando o adaptador de hardware padrão, que, em um sistema híbrido pode não ser o mesmo que aquele usado para o fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="15b5d-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="15b5d-268">Para contornar isso pode causar problemas, use o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> partir <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() ou <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId().</span><span class="sxs-lookup"><span data-stu-id="15b5d-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="15b5d-269">Este IdentificaçãoDoAdaptador, em seguida, pode ser usado para selecionar o direito DXGIAdapter usando IDXGIFactory4.EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="15b5d-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="15b5d-270">Partir **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="15b5d-271">Código para **atualizar DeviceResources::CreateDeviceResources para usar IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="15b5d-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="15b5d-272">**Gráficos híbridos e Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="15b5d-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="15b5d-273">Usar o Media Foundation em sistemas híbrida pode causar problemas em que o vídeo não será renderizado ou textura de vídeo está corrompida.</span><span class="sxs-lookup"><span data-stu-id="15b5d-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="15b5d-274">Isso pode ocorrer porque o Media Foundation é padronizar para um comportamento do sistema conforme mencionado acima.</span><span class="sxs-lookup"><span data-stu-id="15b5d-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="15b5d-275">Em alguns cenários, é necessário para suporte a multithreading e a criação correta sinalizadores são definidos como criar um ID3D11Device separado.</span><span class="sxs-lookup"><span data-stu-id="15b5d-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="15b5d-276">Ao inicializar o ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT sinalizador deve ser definido como parte do D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="15b5d-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="15b5d-277">Depois que o dispositivo e o contexto é criado, chame <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar multithreading.</span><span class="sxs-lookup"><span data-stu-id="15b5d-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="15b5d-278">Para associar o dispositivo com o <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use o <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> função.</span><span class="sxs-lookup"><span data-stu-id="15b5d-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="15b5d-279">Código para **associar um ID3D11Device IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="15b5d-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="15b5d-280">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15b5d-280">See also</span></span>
* [<span data-ttu-id="15b5d-281">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="15b5d-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="15b5d-282">Usando o emulador do HoloLens</span><span class="sxs-lookup"><span data-stu-id="15b5d-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)

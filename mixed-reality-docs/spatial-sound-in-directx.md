---
title: Som espacial no DirectX
description: Adicione som espacial aos seus aplicativos de realidade mista do Windows com base em DirectX usando as bibliotecas de áudio XAudio2 e xAPO.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows misturadas realidade, som espacial, aplicativos, o XAudio2, de baixo nível, xAPO, biblioteca de áudio, passo a passo, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591028"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="85739-104">Som espacial no DirectX</span><span class="sxs-lookup"><span data-stu-id="85739-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="85739-105">Adicionar som espacial aos seus aplicativos de realidade mista do Windows com base em DirectX usando o [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) e [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) bibliotecas de áudio.</span><span class="sxs-lookup"><span data-stu-id="85739-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="85739-106">Este tópico usa o código de exemplo do HolographicHRTFAudioSample.</span><span class="sxs-lookup"><span data-stu-id="85739-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="85739-107">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="85739-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="85739-108">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="85739-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="85739-109">Visão geral de som espacial relativo de cabeça</span><span class="sxs-lookup"><span data-stu-id="85739-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="85739-110">Som espacial é implementado como um **o objeto de processamento de áudio (APO)** que usa um **head relacionados a função de transferência (HRTF)** filtrar por *spatialize* um fluxo de áudio comum.</span><span class="sxs-lookup"><span data-stu-id="85739-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="85739-111">Inclua esses arquivos de cabeçalho em pch. h para acessar o APIs de áudio:</span><span class="sxs-lookup"><span data-stu-id="85739-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="85739-112">XAudio2.h</span><span class="sxs-lookup"><span data-stu-id="85739-112">XAudio2.h</span></span>
* <span data-ttu-id="85739-113">xapo.h</span><span class="sxs-lookup"><span data-stu-id="85739-113">xapo.h</span></span>
* <span data-ttu-id="85739-114">hrtfapoapi.h</span><span class="sxs-lookup"><span data-stu-id="85739-114">hrtfapoapi.h</span></span>

<span data-ttu-id="85739-115">Para definir o som espacial:</span><span class="sxs-lookup"><span data-stu-id="85739-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="85739-116">Chame [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) para inicializar um novo APO para áudio HRTF.</span><span class="sxs-lookup"><span data-stu-id="85739-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="85739-117">Atribuir a [parâmetros HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) e [ambiente HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) para definir as características acústicas do espacial APO de som.</span><span class="sxs-lookup"><span data-stu-id="85739-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="85739-118">Configure o mecanismo XAudio2 para processamento de HRTF.</span><span class="sxs-lookup"><span data-stu-id="85739-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="85739-119">Criar uma [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) objeto e chame [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span><span class="sxs-lookup"><span data-stu-id="85739-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="85739-120">Implementando HRTF e espacial som em seu aplicativo DirectX</span><span class="sxs-lookup"><span data-stu-id="85739-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="85739-121">Você pode obter uma variedade de efeitos, configurando o APO HRTF com ambientes e parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="85739-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="85739-122">Use o seguinte código para explorar as possibilidades.</span><span class="sxs-lookup"><span data-stu-id="85739-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="85739-123">Baixe o exemplo de código da plataforma Universal do Windows aqui: [Exemplo Spatial de som](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="85739-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="85739-124">Tipos auxiliares estão disponíveis nesses arquivos:</span><span class="sxs-lookup"><span data-stu-id="85739-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="85739-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Carrega arquivos de áudio usando o Media Foundation e o [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span><span class="sxs-lookup"><span data-stu-id="85739-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="85739-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementa o **SetupXAudio2** função para inicializar o XAudio2 para processamento de HRTF.</span><span class="sxs-lookup"><span data-stu-id="85739-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="85739-127">Adicionar som espacial para uma fonte onidirecional</span><span class="sxs-lookup"><span data-stu-id="85739-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="85739-128">Alguns hologramas no ambiente do usuário emitem um som igualmente em todas as direções.</span><span class="sxs-lookup"><span data-stu-id="85739-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="85739-129">O código a seguir mostra como inicializar um APO para emitir um som unidirecional.</span><span class="sxs-lookup"><span data-stu-id="85739-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="85739-130">Neste exemplo, conseguimos aplicar esse conceito para o cubo giratório do modelo de aplicativo do Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="85739-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="85739-131">Para a listagem de código completo, consulte [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span><span class="sxs-lookup"><span data-stu-id="85739-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="85739-132">**O mecanismo de som espacial da janela só oferece suporte a 48 samplerate de k para reprodução. A maioria dos programas de middleware, como o Unity, converterá automaticamente arquivos de som no formato desejado, mas se você começar a mexer em níveis inferiores no sistema de áudio ou fazer seus próprios, isso é muito importante lembrar-se de evitar falhas ou comportamento indesejado, como Falha do sistema HRTF.**</span><span class="sxs-lookup"><span data-stu-id="85739-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="85739-133">Primeiro, é necessário inicializar o APO.</span><span class="sxs-lookup"><span data-stu-id="85739-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="85739-134">Em nosso aplicativo de exemplo holográfica, podemos optar por fazer isso assim que tivermos a **HolographicSpace**.</span><span class="sxs-lookup"><span data-stu-id="85739-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="85739-135">Partir *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="85739-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="85739-136">A implementação de inicialização, de *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="85739-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

<span data-ttu-id="85739-137">Depois que o APO estiver configurado para HRTF, você chama [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) sobre a voz fonte para reproduzir o áudio.</span><span class="sxs-lookup"><span data-stu-id="85739-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="85739-138">Em nosso aplicativo de exemplo, escolhemos colocá-lo em um loop, para que você possa continuar ouvir o som provenientes do cubo.</span><span class="sxs-lookup"><span data-stu-id="85739-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="85739-139">Partir *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="85739-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="85739-140">Partir *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="85739-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="85739-141">Agora, sempre que atualizamos o quadro, precisamos atualizar a posição do holograma em relação ao próprio dispositivo.</span><span class="sxs-lookup"><span data-stu-id="85739-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="85739-142">Isso ocorre porque HRTF posições sempre são expressas em relação ao cabeçalho do usuário, incluindo o cabeça posição e orientação.</span><span class="sxs-lookup"><span data-stu-id="85739-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="85739-143">Para fazer isso em um HolographicSpace, precisamos construir uma matriz de transformação de nosso sistema de coordenadas SpatialStationaryFrameOfReference para um sistema de coordenadas é fixo para o próprio dispositivo.</span><span class="sxs-lookup"><span data-stu-id="85739-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="85739-144">Partir *HolographicHrtfAudioSampleMain::Update()*:</span><span class="sxs-lookup"><span data-stu-id="85739-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

<span data-ttu-id="85739-145">A posição de HRTF é aplicada diretamente para o som APO pela classe auxiliar OmnidirectionalSound.</span><span class="sxs-lookup"><span data-stu-id="85739-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="85739-146">Partir *OmnidirectionalSound::OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="85739-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="85739-147">É só isso!</span><span class="sxs-lookup"><span data-stu-id="85739-147">That's it!</span></span> <span data-ttu-id="85739-148">Continue lendo para saber mais sobre o que você pode fazer com áudio HRTF e Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="85739-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="85739-149">Inicializar o som espacial para uma fonte direcional</span><span class="sxs-lookup"><span data-stu-id="85739-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="85739-150">Alguns hologramas no ambiente do usuário emitem um som principalmente em uma única direção.</span><span class="sxs-lookup"><span data-stu-id="85739-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="85739-151">Esse padrão de som é denominado *cardioid* porque ele se parece com um núcleo de desenho animado.</span><span class="sxs-lookup"><span data-stu-id="85739-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="85739-152">O código a seguir mostra como inicializar um APO para emitir direcional som.</span><span class="sxs-lookup"><span data-stu-id="85739-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="85739-153">Para a listagem de código completo, consulte [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span><span class="sxs-lookup"><span data-stu-id="85739-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="85739-154">Depois que o APO estiver configurado para HRTF, chame [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) sobre a voz fonte para reproduzir o áudio.</span><span class="sxs-lookup"><span data-stu-id="85739-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a><span data-ttu-id="85739-155">Implementar o declínio personalizado</span><span class="sxs-lookup"><span data-stu-id="85739-155">Implement custom decay</span></span>

<span data-ttu-id="85739-156">Você pode substituir a taxa na qual um som espacial fica com distância e/ou a que distância-corta completamente.</span><span class="sxs-lookup"><span data-stu-id="85739-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="85739-157">Para implementar o comportamento de decaimento personalizado em um som espacial, preencher um [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) e atribuí-lo para o **distanceDecay** campo em um [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) antes de passá-lo para o [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) função.</span><span class="sxs-lookup"><span data-stu-id="85739-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="85739-158">Adicione o seguinte código para o **inicializar** método mostrado anteriormente para especificar o comportamento de decaimento personalizado.</span><span class="sxs-lookup"><span data-stu-id="85739-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="85739-159">Para a listagem de código completo, consulte [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span><span class="sxs-lookup"><span data-stu-id="85739-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```

---
title: Som espacial no DirectX
description: Adicione som espacial aos seus aplicativos de realidade mista do Windows com base no DirectX usando as bibliotecas de áudio XAudio2 e xAPO.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, som espacial, aplicativos, XAudio2, nível baixo, xAPO, biblioteca de áudio, passo a passos, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550436"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="8c6b0-104">Som espacial no DirectX</span><span class="sxs-lookup"><span data-stu-id="8c6b0-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="8c6b0-105">Adicione som espacial aos seus aplicativos de realidade mista do Windows com base no DirectX usando as bibliotecas de áudio [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) e [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8c6b0-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="8c6b0-106">Este tópico usa o código de exemplo do HolographicHRTFAudioSample.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="8c6b0-107">Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="8c6b0-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="8c6b0-108">Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="8c6b0-109">Visão geral do som espacial relativo da cabeça</span><span class="sxs-lookup"><span data-stu-id="8c6b0-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="8c6b0-110">O som espacial é implementado como um **APO (objeto de processamento de áudio)** que usa um filtro **HRTF (função de transferência relacionada à cabeça)** para *espacialar* um fluxo de áudio comum.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="8c6b0-111">Inclua esses arquivos de cabeçalho em PCH. h para acessar as APIs de áudio:</span><span class="sxs-lookup"><span data-stu-id="8c6b0-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="8c6b0-112">XAudio2. h</span><span class="sxs-lookup"><span data-stu-id="8c6b0-112">XAudio2.h</span></span>
* <span data-ttu-id="8c6b0-113">xAPO. h</span><span class="sxs-lookup"><span data-stu-id="8c6b0-113">xapo.h</span></span>
* <span data-ttu-id="8c6b0-114">hrtfapoapi. h</span><span class="sxs-lookup"><span data-stu-id="8c6b0-114">hrtfapoapi.h</span></span>

<span data-ttu-id="8c6b0-115">Para configurar o som espacial:</span><span class="sxs-lookup"><span data-stu-id="8c6b0-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="8c6b0-116">Chame [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) para inicializar um novo APO para o HRTF Audio.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="8c6b0-117">Atribua os [parâmetros HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) e o [ambiente HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) para definir as características acústicas do som espacial APO.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="8c6b0-118">Configure o mecanismo de XAudio2 para processamento de HRTF.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="8c6b0-119">Crie um objeto [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) e chame [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span><span class="sxs-lookup"><span data-stu-id="8c6b0-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="8c6b0-120">Implementando HRTF e som espacial em seu aplicativo DirectX</span><span class="sxs-lookup"><span data-stu-id="8c6b0-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="8c6b0-121">Você pode obter uma variedade de efeitos Configurando o HRTF APO com diferentes parâmetros e ambientes.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="8c6b0-122">Use o código a seguir para explorar as possibilidades.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="8c6b0-123">Baixe o exemplo de código de Plataforma Universal do Windows aqui: [Amostra de som espacial](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="8c6b0-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="8c6b0-124">Os tipos auxiliares estão disponíveis nestes arquivos:</span><span class="sxs-lookup"><span data-stu-id="8c6b0-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="8c6b0-125">[AudioFileReader. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Carrega arquivos de áudio usando Media Foundation e a [interface IMFSourceReader](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span><span class="sxs-lookup"><span data-stu-id="8c6b0-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="8c6b0-126">[XAudio2Helpers. h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementa a função **SetupXAudio2** para inicializar o XAudio2 para processamento HRTF.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="8c6b0-127">Adicionar som espacial para uma fonte de onidirecionais</span><span class="sxs-lookup"><span data-stu-id="8c6b0-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="8c6b0-128">Alguns hologramas nos arredores do usuário emitem o som igualmente em todas as direções.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="8c6b0-129">O código a seguir mostra como inicializar um APO para emitir um som onidirecionais.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="8c6b0-130">Neste exemplo, aplicamos esse conceito ao cubo de rotação do modelo de aplicativo Holographic do Windows.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="8c6b0-131">Para obter a listagem de código completa, consulte [OmnidirectionalSound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span><span class="sxs-lookup"><span data-stu-id="8c6b0-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="8c6b0-132">**O mecanismo de som espacial da janela dá suporte apenas à amostra de 48K para reprodução. A maioria dos programas de middleware, como o Unity, converterá automaticamente os arquivos de som no formato desejado, mas se você começar a fazer a reformulação em níveis inferiores no sistema de áudio ou fizer o seu próprio, é muito importante lembrar-se de evitar falhas ou comportamentos indesejados como Falha do sistema HRTF.**</span><span class="sxs-lookup"><span data-stu-id="8c6b0-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="8c6b0-133">Primeiro, precisamos inicializar o APO.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="8c6b0-134">Em nosso aplicativo de exemplo Holographic, optamos por fazer isso assim que tivermos o **HolographicSpace**.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="8c6b0-135">De *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="8c6b0-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="8c6b0-136">A implementação de Initialize, de *OmnidirectionalSound. cpp*:</span><span class="sxs-lookup"><span data-stu-id="8c6b0-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="8c6b0-137">Depois que o APO estiver configurado para HRTF, você chamará [Iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) na voz de origem para reproduzir o áudio.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="8c6b0-138">Em nosso aplicativo de exemplo, escolhemos colocá-lo em um loop para que você possa continuar a ouvir o som vindo do cubo.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="8c6b0-139">De *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :</span><span class="sxs-lookup"><span data-stu-id="8c6b0-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="8c6b0-140">De *OmnidirectionalSound. cpp*:</span><span class="sxs-lookup"><span data-stu-id="8c6b0-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="8c6b0-141">Agora, sempre que atualizarmos o quadro, precisaremos atualizar a posição do holograma em relação ao próprio dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="8c6b0-142">Isso ocorre porque as posições de HRTF são sempre expressas em relação à cabeça do usuário, incluindo a posição e a orientação da cabeça.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="8c6b0-143">Para fazer isso em um HolographicSpace, precisamos construir uma matriz de transformação de nosso sistema de coordenadas SpatialStationaryFrameOfReference para um sistema de coordenadas que é corrigido para o próprio dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="8c6b0-144">De *HolographicHrtfAudioSampleMain:: Update ()* :</span><span class="sxs-lookup"><span data-stu-id="8c6b0-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="8c6b0-145">A posição HRTF é aplicada diretamente ao APO de som pela classe auxiliar OmnidirectionalSound.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="8c6b0-146">De *OmnidirectionalSound:: OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="8c6b0-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="8c6b0-147">É só isso!</span><span class="sxs-lookup"><span data-stu-id="8c6b0-147">That's it!</span></span> <span data-ttu-id="8c6b0-148">Continue lendo para saber mais sobre o que você pode fazer com o HRTF audio e o Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="8c6b0-149">Inicializar o som espacial para uma fonte direcional</span><span class="sxs-lookup"><span data-stu-id="8c6b0-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="8c6b0-150">Alguns hologramas nos arredores do usuário emitem o som principalmente em uma direção.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="8c6b0-151">Esse padrão de som é chamado de *cardioid* porque parece um coração animador.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="8c6b0-152">O código a seguir mostra como inicializar um APO para emitir um som direcional.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="8c6b0-153">Para obter a listagem de código completa, consulte [CardioidSound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span><span class="sxs-lookup"><span data-stu-id="8c6b0-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="8c6b0-154">Depois que o APO estiver configurado para HRTF, chame [Iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) na voz de origem para reproduzir o áudio.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="8c6b0-155">Implementar decaimento personalizado</span><span class="sxs-lookup"><span data-stu-id="8c6b0-155">Implement custom decay</span></span>

<span data-ttu-id="8c6b0-156">Você pode substituir a taxa na qual um som espacial fica desativado com distância e/ou em qual distância ele corta completamente.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="8c6b0-157">Para implementar o comportamento decaimento personalizado em um som espacial, preencha um [struct HrtfDistanceDecay](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) e atribua-o ao campo **distanceDecay** em um [struct HrtfApoInit](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) antes de passá-lo para a função [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8c6b0-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="8c6b0-158">Adicione o código a seguir ao método **Initialize** mostrado anteriormente para especificar o comportamento decaimento personalizado.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="8c6b0-159">Para obter a listagem de código completa, consulte [CustomDecay. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span><span class="sxs-lookup"><span data-stu-id="8c6b0-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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

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
# <a name="spatial-sound-in-directx"></a>Som espacial no DirectX

Adicione som espacial aos seus aplicativos de realidade mista do Windows com base no DirectX usando as bibliotecas de áudio [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) e [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) .

Este tópico usa o código de exemplo do HolographicHRTFAudioSample.

>[!NOTE]
>Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.

## <a name="overview-of-head-relative-spatial-sound"></a>Visão geral do som espacial relativo da cabeça

O som espacial é implementado como um **APO (objeto de processamento de áudio)** que usa um filtro **HRTF (função de transferência relacionada à cabeça)** para *espacialar* um fluxo de áudio comum.

Inclua esses arquivos de cabeçalho em PCH. h para acessar as APIs de áudio:
* XAudio2. h
* xAPO. h
* hrtfapoapi. h

Para configurar o som espacial:
1. Chame [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) para inicializar um novo APO para o HRTF Audio.
2. Atribua os [parâmetros HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) e o [ambiente HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) para definir as características acústicas do som espacial APO.
3. Configure o mecanismo de XAudio2 para processamento de HRTF.
4. Crie um objeto [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) e chame [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>Implementando HRTF e som espacial em seu aplicativo DirectX

Você pode obter uma variedade de efeitos Configurando o HRTF APO com diferentes parâmetros e ambientes. Use o código a seguir para explorar as possibilidades. Baixe o exemplo de código de Plataforma Universal do Windows aqui: [Amostra de som espacial](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

Os tipos auxiliares estão disponíveis nestes arquivos:
* [AudioFileReader. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Carrega arquivos de áudio usando Media Foundation e a [interface IMFSourceReader](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).
* [XAudio2Helpers. h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementa a função **SetupXAudio2** para inicializar o XAudio2 para processamento HRTF.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>Adicionar som espacial para uma fonte de onidirecionais

Alguns hologramas nos arredores do usuário emitem o som igualmente em todas as direções. O código a seguir mostra como inicializar um APO para emitir um som onidirecionais. Neste exemplo, aplicamos esse conceito ao cubo de rotação do modelo de aplicativo Holographic do Windows. Para obter a listagem de código completa, consulte [OmnidirectionalSound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).

**O mecanismo de som espacial da janela dá suporte apenas à amostra de 48K para reprodução. A maioria dos programas de middleware, como o Unity, converterá automaticamente os arquivos de som no formato desejado, mas se você começar a fazer a reformulação em níveis inferiores no sistema de áudio ou fizer o seu próprio, é muito importante lembrar-se de evitar falhas ou comportamentos indesejados como Falha do sistema HRTF.**

Primeiro, precisamos inicializar o APO. Em nosso aplicativo de exemplo Holographic, optamos por fazer isso assim que tivermos o **HolographicSpace**.

De *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

A implementação de Initialize, de *OmnidirectionalSound. cpp*:

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

Depois que o APO estiver configurado para HRTF, você chamará [Iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) na voz de origem para reproduzir o áudio. Em nosso aplicativo de exemplo, escolhemos colocá-lo em um loop para que você possa continuar a ouvir o som vindo do cubo.

De *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

De *OmnidirectionalSound. cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

Agora, sempre que atualizarmos o quadro, precisaremos atualizar a posição do holograma em relação ao próprio dispositivo. Isso ocorre porque as posições de HRTF são sempre expressas em relação à cabeça do usuário, incluindo a posição e a orientação da cabeça.

Para fazer isso em um HolographicSpace, precisamos construir uma matriz de transformação de nosso sistema de coordenadas SpatialStationaryFrameOfReference para um sistema de coordenadas que é corrigido para o próprio dispositivo.

De *HolographicHrtfAudioSampleMain:: Update ()* :

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

A posição HRTF é aplicada diretamente ao APO de som pela classe auxiliar OmnidirectionalSound.

De *OmnidirectionalSound:: OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

É só isso! Continue lendo para saber mais sobre o que você pode fazer com o HRTF audio e o Windows Holographic.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>Inicializar o som espacial para uma fonte direcional

Alguns hologramas nos arredores do usuário emitem o som principalmente em uma direção. Esse padrão de som é chamado de *cardioid* porque parece um coração animador. O código a seguir mostra como inicializar um APO para emitir um som direcional. Para obter a listagem de código completa, consulte [CardioidSound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .

Depois que o APO estiver configurado para HRTF, chame [Iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) na voz de origem para reproduzir o áudio.

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

### <a name="implement-custom-decay"></a>Implementar decaimento personalizado

Você pode substituir a taxa na qual um som espacial fica desativado com distância e/ou em qual distância ele corta completamente. Para implementar o comportamento decaimento personalizado em um som espacial, preencha um [struct HrtfDistanceDecay](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) e atribua-o ao campo **distanceDecay** em um [struct HrtfApoInit](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) antes de passá-lo para a função [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) .

Adicione o código a seguir ao método **Initialize** mostrado anteriormente para especificar o comportamento decaimento personalizado. Para obter a listagem de código completa, consulte [CustomDecay. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).

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

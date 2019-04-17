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
# <a name="spatial-sound-in-directx"></a>Som espacial no DirectX

Adicionar som espacial aos seus aplicativos de realidade mista do Windows com base em DirectX usando o [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) e [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) bibliotecas de áudio.

Este tópico usa o código de exemplo do HolographicHRTFAudioSample.

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

## <a name="overview-of-head-relative-spatial-sound"></a>Visão geral de som espacial relativo de cabeça

Som espacial é implementado como um **o objeto de processamento de áudio (APO)** que usa um **head relacionados a função de transferência (HRTF)** filtrar por *spatialize* um fluxo de áudio comum.

Inclua esses arquivos de cabeçalho em pch. h para acessar o APIs de áudio:
* XAudio2.h
* xapo.h
* hrtfapoapi.h

Para definir o som espacial:
1. Chame [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) para inicializar um novo APO para áudio HRTF.
2. Atribuir a [parâmetros HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) e [ambiente HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) para definir as características acústicas do espacial APO de som.
3. Configure o mecanismo XAudio2 para processamento de HRTF.
4. Criar uma [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) objeto e chame [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>Implementando HRTF e espacial som em seu aplicativo DirectX

Você pode obter uma variedade de efeitos, configurando o APO HRTF com ambientes e parâmetros diferentes. Use o seguinte código para explorar as possibilidades. Baixe o exemplo de código da plataforma Universal do Windows aqui: [Exemplo Spatial de som](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

Tipos auxiliares estão disponíveis nesses arquivos:
* [AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Carrega arquivos de áudio usando o Media Foundation e o [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).
* [XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementa o **SetupXAudio2** função para inicializar o XAudio2 para processamento de HRTF.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>Adicionar som espacial para uma fonte onidirecional

Alguns hologramas no ambiente do usuário emitem um som igualmente em todas as direções. O código a seguir mostra como inicializar um APO para emitir um som unidirecional. Neste exemplo, conseguimos aplicar esse conceito para o cubo giratório do modelo de aplicativo do Windows Holographic. Para a listagem de código completo, consulte [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).

**O mecanismo de som espacial da janela só oferece suporte a 48 samplerate de k para reprodução. A maioria dos programas de middleware, como o Unity, converterá automaticamente arquivos de som no formato desejado, mas se você começar a mexer em níveis inferiores no sistema de áudio ou fazer seus próprios, isso é muito importante lembrar-se de evitar falhas ou comportamento indesejado, como Falha do sistema HRTF.**

Primeiro, é necessário inicializar o APO. Em nosso aplicativo de exemplo holográfica, podemos optar por fazer isso assim que tivermos a **HolographicSpace**.

Partir *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

A implementação de inicialização, de *OmnidirectionalSound.cpp*:

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

Depois que o APO estiver configurado para HRTF, você chama [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) sobre a voz fonte para reproduzir o áudio. Em nosso aplicativo de exemplo, escolhemos colocá-lo em um loop, para que você possa continuar ouvir o som provenientes do cubo.

Partir *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

Partir *OmnidirectionalSound.cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

Agora, sempre que atualizamos o quadro, precisamos atualizar a posição do holograma em relação ao próprio dispositivo. Isso ocorre porque HRTF posições sempre são expressas em relação ao cabeçalho do usuário, incluindo o cabeça posição e orientação.

Para fazer isso em um HolographicSpace, precisamos construir uma matriz de transformação de nosso sistema de coordenadas SpatialStationaryFrameOfReference para um sistema de coordenadas é fixo para o próprio dispositivo.

Partir *HolographicHrtfAudioSampleMain::Update()*:

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

A posição de HRTF é aplicada diretamente para o som APO pela classe auxiliar OmnidirectionalSound.

Partir *OmnidirectionalSound::OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

É só isso! Continue lendo para saber mais sobre o que você pode fazer com áudio HRTF e Windows Holographic.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>Inicializar o som espacial para uma fonte direcional

Alguns hologramas no ambiente do usuário emitem um som principalmente em uma única direção. Esse padrão de som é denominado *cardioid* porque ele se parece com um núcleo de desenho animado. O código a seguir mostra como inicializar um APO para emitir direcional som. Para a listagem de código completo, consulte [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .

Depois que o APO estiver configurado para HRTF, chame [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) sobre a voz fonte para reproduzir o áudio.

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

### <a name="implement-custom-decay"></a>Implementar o declínio personalizado

Você pode substituir a taxa na qual um som espacial fica com distância e/ou a que distância-corta completamente. Para implementar o comportamento de decaimento personalizado em um som espacial, preencher um [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) e atribuí-lo para o **distanceDecay** campo em um [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) antes de passá-lo para o [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) função.

Adicione o seguinte código para o **inicializar** método mostrado anteriormente para especificar o comportamento de decaimento personalizado. Para a listagem de código completo, consulte [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).

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

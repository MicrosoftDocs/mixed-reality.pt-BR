---
title: Câmera localizável
description: Informações gerais sobre a câmera frontal do HoloLens, como ela funciona e os perfis e as resoluções disponíveis para os desenvolvedores.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: câmera, hololens, câmera colorida, frente, hololens 2, CV, pesquisa Visual computacional, fiducial, marcadores, código QR, QR, foto, vídeo
ms.openlocfilehash: b8e9d926db09d277b3fde7572dd68257599c8d5e
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83520011"
---
# <a name="locatable-camera"></a>Câmera localizável

O HoloLens inclui uma câmera voltada para o mundo montada na frente do dispositivo, o que permite que os aplicativos vejam o que o usuário vê. Os desenvolvedores têm acesso e controle da câmera, assim como fariam para câmeras coloridas em smartphones, portáteis ou desktops. As mesmas APIs universal do Windows Media [Capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) e do Windows Media Foundation que funcionam em dispositivos móveis e de área de trabalho no HoloLens. O Unity [também reuniu essas APIs do Windows](locatable-camera-in-unity.md) para abstrair o uso simples da câmera no HoloLens para tarefas como a realização de fotos e vídeos regulares (com ou sem hologramas) e a localização da posição da câmera em e na perspectiva da cena.

## <a name="device-camera-information"></a>Informações sobre a câmera do dispositivo

### <a name="hololens-first-generation"></a>HoloLens (primeira geração)

* Câmera de foco de foto/vídeo (PV) fixa com balanceamento de branco automático, exposição automática e pipeline de processamento de imagem completo.
* O LED de privacidade branco enfrentado pelo mundo se acenderá sempre que a câmera estiver ativa
* A câmera dá suporte aos seguintes modos (todos os modos são 16:9 taxa de proporção) a 30, 24, 20, 15 e 5 fps:

  |  Vídeo  |  Versão Prévia  |  Também  |  Campo de exibição horizontal (H-FOV) |  Uso sugerido | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45deg  |  (modo padrão com estabilização de vídeo) | 
  |  N/D |  N/D |  2048x1152 |  67deg |  Imagem da resolução mais alta ainda | 
  |  1408x792 |  1408x792 |  1408x792 |  48deg |  Resolução de sobrevarredura (preenchimento) antes da estabilização de vídeo | 
  |  1344x756 |  1344x756 |  1344x756 |  67deg |  Modo de vídeo FOV grande com overscan | 
  |  896x504 |  896x504 |  896x504 |  48deg |  Modo de baixa energia/baixa resolução para tarefas de processamento de imagens | 

### <a name="hololens-2"></a>HoloLens 2

* Câmera de foto/vídeo (PV) de foco automático com balanceamento de branco automático, exposição automática e pipeline de processamento de imagem completo.
* O LED de privacidade branco enfrentado pelo mundo se acenderá sempre que a câmera estiver ativa.
* O HoloLens 2 dá suporte a perfis de câmera diferentes. Saiba como [descobrir e selecionar recursos de câmera](https://docs.microsoft.com//windows/uwp/audio-video-camera/camera-profiles).
* A câmera dá suporte aos seguintes perfis e resoluções (todos os modos de vídeo são taxa de proporção de 16:9):
  
  | Perfil                                         | Vídeo     | Versão Prévia   | Também     | Taxas de quadros | Campo de exibição horizontal (H-FOV) | Uso sugerido                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Herdado, 0 BalancedVideoAndPhoto, 100             | 2272x1278 | 2272x1278 |           | 15, 30       | 64,69                            | Gravação de vídeo de alta qualidade                |
  | Herdado, 0 BalancedVideoAndPhoto, 100             | 896x504   | 896x504   |           | 15, 30       | 64,69                            | Fluxo de visualização para captura de foto de alta qualidade |
  | Herdado, 0 BalancedVideoAndPhoto, 100             |           |           | 3904x2196 |             | 64,69                            | Captura de foto de alta qualidade                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30       | 64,69                            | Cenários de duração longa                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15, 30       | 64,69                            | Cenários de duração longa                     |
  | Videoconferência, 100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15, 30, 60    | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100                           | 1504x846  | 1504x846  |           | 5, 15, 30, 60  | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100 BalancedVideoAndPhoto, 120 | 1920 x 1080 | 1920 x 1080 | 1920 x 1080 | 15, 30       | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100 BalancedVideoAndPhoto, 120 | 1280x720  | 1280x720  | 1280x720  | 15, 30       | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100 BalancedVideoAndPhoto, 120 | 1128x636  |           |           | 15, 30       | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100 BalancedVideoAndPhoto, 120 | 960 x 540   |           |           | 15, 30       | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100 BalancedVideoAndPhoto, 120 | 760x428   |           |           | 15, 30       | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100 BalancedVideoAndPhoto, 120 | 640 x 360   |           |           | 15, 30       | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100 BalancedVideoAndPhoto, 120 | 500x282   |           |           | 15, 30       | 64,69                            | Videoconferência, cenários de longa duração |
  | Videoconferência, 100 BalancedVideoAndPhoto, 120 | 424x240   |           |           | 15, 30       | 64,69                            | Videoconferência, cenários de longa duração |

>[!NOTE]
>Os clientes podem aproveitar a [captura de realidade misturada](mixed-reality-capture.md) para tirar vídeos ou fotos de seu aplicativo, o que inclui hologramas e estabilização de vídeo.
>
>Como desenvolvedor, há considerações que você deve levar em conta ao criar seu aplicativo se quiser que ele pareça o mais bom possível quando um cliente capturar o conteúdo. Você também pode habilitar (e personalizar) a captura de realidade misturada diretamente no seu aplicativo. Saiba mais em uma [captura de realidade mista para desenvolvedores](mixed-reality-capture-for-developers.md).

## <a name="locating-the-device-camera-in-the-world"></a>Localizando a câmera do dispositivo no mundo

Quando o HoloLens usa fotos e vídeos, os quadros capturados incluem o local da câmera do mundo, bem como o modelo de lente da câmera. Isso permite que os aplicativos dediquem a posição da câmera no mundo real para cenários de geração de imagens aumentados. Os desenvolvedores podem lançar de forma criativa seus próprios cenários usando seu processamento de imagem favorito ou bibliotecas personalizadas da pesquisa Visual computacional.

A "câmera" em outro lugar na documentação do HoloLens pode se referir à "câmera do jogo virtual" (o frustum ao qual o aplicativo é renderizado). A menos que seja indicado de outra forma, "câmera" nesta página refere-se à câmera de cores RGB do mundo real.

### <a name="using-unity"></a>Usando o Unity

Para ir do ' CameraIntrinsics ' e ' CameraCoordinateSystem ' para seu sistema/coordenado do mundo, siga as instruções no artigo da [câmera localizável no Unity](locatable-camera-in-unity.md) .  O CameraToWorldMatrix é fornecido automaticamente pela classe PhotoCaptureFrame e, portanto, você não precisa se preocupar com as transformações CameraCoordinateSystem discutidas abaixo.

### <a name="using-mediaframereference"></a>Usando MediaFrameReference

Essas instruções se aplicam se você estiver usando a classe [MediaFrameReference](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference) para ler quadros de imagem da câmera.

Cada quadro de imagem (seja foto ou vídeo) inclui um [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) com raiz na câmera no momento da captura, que pode ser acessado usando a propriedade [CoordinateSystem](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) de seu [MediaFrameReference](https://docs.microsoft.com//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference). Além disso, cada quadro contém uma descrição do modelo de lente da câmera, que pode ser encontrado na propriedade [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) . Juntas, essas transformações definem para cada pixel um raio em um espaço 3D que representa o caminho usado pelo fótons que produziu o pixel. Esses raios podem estar relacionados a outro conteúdo no aplicativo por meio da obtenção da transformação do sistema de coordenadas do quadro para outro sistema de coordenadas (por exemplo, de um [quadro estacionário de referência](coordinate-systems.md#stationary-frame-of-reference)). Para resumir, cada quadro de imagem fornece o seguinte:
* Dados de pixel (em formato RGB/NV12/JPEG/etc.)
* Um [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) do local da captura
* Uma classe [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) que contém o modo de lente da câmera

O [exemplo HolographicFaceTracking](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) mostra a maneira bastante simples de consultar a transformação entre o sistema de coordenadas da câmera e seus próprios sistemas de coordenadas do aplicativo.

### <a name="using-media-foundation"></a>Usando Media Foundation

Se você estiver usando Media Foundation diretamente para ler quadros de imagem da câmera, poderá usar o [atributo MFSampleExtension_CameraExtrinsics](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-cameraextrinsics) de cada quadro e [MFSampleExtension_PinholeCameraIntrinsics atributo](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) para localizar quadros de câmera relativos aos outros sistemas de coordenadas do seu aplicativo, conforme mostrado neste código de exemplo:

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeQpc = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeQpc)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpanFrodmQpcTicks(sampleTimeQpc));
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }
 
private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
 
    // Convert a duration value from a source tick frequency to a destination tick frequency.
    static inline int64_t SourceDurationTicksToDestDurationTicks(int64_t sourceDurationInTicks, int64_t sourceTicksPerSecond, int64_t destTicksPerSecond)
    {
        int64_t whole = (sourceDurationInTicks / sourceTicksPerSecond) * destTicksPerSecond;                          // 'whole' is rounded down in the target time units.
        int64_t part = (sourceDurationInTicks % sourceTicksPerSecond) * destTicksPerSecond / sourceTicksPerSecond;    // 'part' is the remainder in the target time units.
        return whole + part;
    }
 
    static inline TimeSpan TimeSpanFromQpcTicks(int64_t qpcTicks)
    {
        static const int64_t qpcFrequency = []
        {
            LARGE_INTEGER frequency;
            QueryPerformanceFrequency(&frequency);
            return frequency.QuadPart;
        }();
 
        return TimeSpan{ SourceDurationTicksToDestDurationTicks(qpcTicks, qpcFrequency, winrt::clock::period::den) / winrt::clock::period::num };
    }
};
```

### <a name="distortion-error"></a>Erro de distorção

No HoloLens, os fluxos de vídeo e de imagem ainda não são distorcidos no pipeline de processamento de imagens do sistema antes que os quadros sejam disponibilizados para o aplicativo (o fluxo de visualização contém os quadros originais distorcidos). Como somente os CameraIntrinsics são disponibilizados, os aplicativos devem assumir que os quadros de imagem representam uma câmera pinhole perfeita.

No HoloLens (primeira geração), a função de distorção no processador de imagem ainda pode deixar um erro de até 10 pixels ao usar o CameraIntrinsics nos metadados do quadro. Em muitos casos de uso, esse erro não importa, mas se você estiver alinhando hologramas a pôsteres/marcadores do mundo real, por exemplo, e observar um deslocamento de <10px (aproximadamente 11mm para hologramas posicionados 2 metros de distância), esse erro de distorção poderá ser a causa. 

## <a name="locatable-camera-usage-scenarios"></a>Cenários de uso de câmera localizável

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>Mostrar uma foto ou um vídeo no mundo onde ele foi capturado

Os quadros de câmera do dispositivo vêm com uma transformação "câmera para o mundo", que pode ser usada para mostrar exatamente onde o dispositivo estava quando a imagem foi tirada. Por exemplo, você pode posicionar um pequeno ícone de Holographic nesse local (CameraToWorld. MultiplyPoint (Vector3. zero)) e até mesmo desenhar uma pequena seta na direção em que a câmera esteve voltada (CameraToWorld. MultiplyVector (Vector3. Forward)).

### <a name="tag--pattern--poster--object-tracking"></a>Rastreamento de marca/padrão/pôster/objeto

Muitos aplicativos de realidade misturada usam uma imagem reconhecível ou um padrão Visual para criar um ponto de controle no espaço. Isso é usado para renderizar objetos relativos a esse ponto ou criar um local conhecido. Alguns usos do HoloLens incluem localizar um objeto do mundo real marcado com fiducials (por exemplo, um monitor de TV com um código QR), colocar hologramas sobre fiducials e emparelhar visualmente com dispositivos não HoloLens, como tablets que foram configurados para se comunicar com o HoloLens via Wi-Fi.

Para reconhecer um padrão Visual e, em seguida, colocar esse objeto no espaço do mundo dos aplicativos, você precisará de algumas coisas:
1. Um kit de ferramentas de reconhecimento de padrões de imagem, como código QR, marcas AR, localizador de rosto, rastreadores de círculo, OCR, etc.
2. Coletar quadros de imagem em tempo de execução e passá-los para a camada de reconhecimento
3. Desprojetar seus locais de imagem de volta nas posições mundiais ou em raios mundiais prováveis. 
4. Posicione seus modelos virtuais nesses locais mundiais

Alguns links importantes de processamento de imagens:
* [OpenCV](https://opencv.org/)
* [Marcas QR](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

Manter uma taxa de quadros de aplicativo interativo é fundamental, especialmente ao lidar com algoritmos de reconhecimento de imagem de longa execução. Por esse motivo, normalmente usamos o seguinte padrão:
1. Thread principal: gerencia o objeto Camera
2. Thread principal: solicitações de novos quadros (Async)
3. Thread principal: passe novos quadros para o thread de acompanhamento
4. Thread de acompanhamento: processa a imagem para coletar pontos-chave
5. Thread principal: move o modelo virtual para corresponder aos pontos-chave encontrados
6. Thread principal: repetir da etapa 2

Alguns sistemas de marcador de imagem fornecem apenas um único local de pixel (outros fornecem a transformação completa, caso em que esta seção não será necessária), que é igual a um raio de locais possíveis. Para chegar a um único local 3D, podemos aproveitar vários raios e encontrar o resultado final por sua interseção aproximada. Para fazer isso, você precisará:
1. Obter um loop indo coletando várias imagens de câmera
2. Encontre os pontos de recursos associados e seus raios mundiais
3. Quando você tem um dicionário de recursos, cada um com vários raios mundiais, você pode usar o seguinte código para resolver a interseção desses raios:

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

Considerando dois ou mais locais de marca rastreados, você pode posicionar uma cena modeladas para se ajustar ao cenário atual do usuário. Se você não puder assumir a gravidade, precisará de três locais de marca. Em muitos casos, usamos um esquema de cores simples em que os pontos brancos representam locais de marcas rastreadas em tempo real, e as bolsas azuis representam locais de marcas modeladas. Isso permite que o usuário avalie visualmente a qualidade do alinhamento. Supomos a seguinte configuração em todos os nossos aplicativos:
* Dois ou mais locais de marcas de modeladas
* Um ' espaço de calibragem ', que na cena é o pai das marcas
* Identificador de recurso da câmera
* Comportamento que move o espaço de calibragem para alinhar as marcas modeladas com as marcas em tempo real (temos o cuidado de mover o espaço pai, não os marcadores de modeladas em si, porque outra conexão é posicionada em relação a eles).

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Acompanhe ou identifique os objetos/faces do mundo marcado ou movendo os controles/rostos reais usando LEDs ou outras bibliotecas do reconhecedor

Exemplos:
* Robôs industriais com LEDs (ou códigos QR para movimentação mais lenta de objetos)
* Identificar e reconhecer objetos na sala
* Identifique e reconheça pessoas na sala (por exemplo, coloque os cartões de contato Holographic em rostos)

## <a name="see-also"></a>Veja também
* [Exemplo de câmera localizável](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Câmera localizável no Unity](locatable-camera-in-unity.md)
* [Captura de realidade misturada](mixed-reality-capture.md)
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Introdução à captura de mídia](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [Exemplo de acompanhamento facial do Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)

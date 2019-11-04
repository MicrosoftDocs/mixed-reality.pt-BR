---
title: Controle de código QR
description: Saiba como detectar códigos QR no HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, entretenimento baseado na localização, VR de los, de los, de imersão, QR, QR Code, hololens2
ms.openlocfilehash: e14fe14fd76bceaf506dd7b85a57825c3f18d223
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438113"
---
# <a name="qr-code-tracking"></a>Controle de código QR

O HoloLens 2 pode detectar códigos QR no ambiente em todo o headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Detecção de código QR</td><td style="text-align: center;">‎</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">Consulte a observação</td>
</tr>
</table>

>[!NOTE]
>No momento, não há suporte para o suporte a headsets de imersão misturadas do Windows em computadores desktop com o pacote NuGet abaixo.  Fique atento para obter mais atualizações sobre o suporte a desktops.

## <a name="getting-the-qr-package"></a>Obtendo o pacote QR
Você pode baixar o pacote NuGet para detecção de código QR [aqui](https://nuget.org/Packages/Microsoft.MixedReality.QR).

## <a name="detecting-qr-codes"></a>Detectando códigos QR

### <a name="adding-the-webcam-capability"></a>Adicionando o recurso de webcam
Será necessário adicionar o recurso `webcam` ao seu manifesto para detectar códigos QR. Esse recurso é necessário, pois os dados dentro de códigos detectados no ambiente do usuário podem conter informações confidenciais.

A permissão pode ser solicitada chamando `QRCodeWatcher.RequestAccessAsync()`:

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

A permissão deve ser solicitada antes de construir um objeto QRCodeWatcher.

Embora a detecção de código QR exija o recurso `webcam`, a detecção ocorre usando as câmeras de rastreamento do dispositivo. Isso fornece uma FOV de detecção mais ampla e uma melhor vida útil da bateria em comparação com a detecção com a câmera de foto/vídeo (PV) do dispositivo.

### <a name="detecting-qr-codes-in-unity"></a>Detectando códigos QR no Unity

Você pode usar a API de detecção de código QR no Unity sem usar uma dependência no MRTK. Para fazer isso, você deve instalar o pacote NuGet usando o [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity).

Há um aplicativo do Unity de exemplo que exibe um quadrado Holographic sobre códigos QR, juntamente com os dados associados, como GUID, tamanho físico, carimbo de data/hora e dados decodificados. Esse aplicativo pode estar localizado em https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.

### <a name="detecting-qr-codes-in-c"></a>Detectando códigos QR noC++

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Obtendo o sistema de coordenadas para um código QR

Cada código QR detectado expõe um [sistema de coordenadas espaciais](coordinate-systems.md) alinhado com o código QR no canto superior esquerdo do quadrado de detecção rápida na parte superior esquerda, conforme mostrado abaixo.  Ao usar o SDK QR diretamente, o eixo Z está apontando para o papel (não mostrado)-quando convertido em coordenadas do Unity, o eixo Z aponta para fora do papel e é canhoto.

Um SpatialCoordinateSystem de código QR é alinhado conforme mostrado. Esse sistema de coordenadas pode ser obtido na plataforma chamando <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> e passando o SpatialGraphNodeId do código.

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

Para um objeto QRCode, o código C++ a seguir mostra como criar um retângulo e colocá-lo usando o sistema de coordenadas do código QR:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

Você pode usar o tamanho físico para criar o retângulo QR:

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas ao local:

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

Totalmente, seu *QRCodeAddedHandler* pode ser semelhante a este:

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>Práticas recomendadas para detecção de código QR

### <a name="quiet-zones-around-qr-codes"></a>Zonas silenciosas em cerca de códigos QR

Para ser lido corretamente, os códigos QR exigem uma margem em volta de todos os lados do código. Essa margem não deve conter nenhum conteúdo impresso e deve ter quatro módulos (um único quadrado preto no código) de largura. 

A [especificação QR](https://www.qrcode.com/en/howto/code.html) contém mais informações sobre zonas silenciosas.

### <a name="lighting-and-backdrop"></a>Iluminação e pano de fundo
A qualidade de detecção de código QR é suscetível à iluminação e ao pano de fundo variadas. 

Em uma cena com iluminação particularmente brilhante, imprima um código preto em um plano de fundo cinza. Caso contrário, imprima um código QR preto em um plano de fundo branco.

Se o pano de fundo para o código for particularmente escuro, experimente um preto no código cinza se a taxa de detecção for baixa. Se o pano de fundo for relativamente claro, um código regular deverá funcionar bem.

### <a name="size-of-qr-codes"></a>Tamanho dos códigos QR
Os dispositivos Windows Mixed Reality não funcionam com códigos QR com lados menores que 5 cm cada.

Para códigos QR entre os lados de comprimento de 5 e 10 cm, você deve estar bastante perto de detectar o código. Também levará mais tempo para detectar códigos nesse tamanho. 

O tempo exato para detectar códigos depende não apenas do tamanho dos códigos QR, mas o quanto você está longe do código. Avançar para o código ajudará a deslocar os problemas com o tamanho.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Distância e posição angular do código QR
As câmeras de rastreamento só podem detectar um determinado nível de detalhe. Para códigos realmente pequenos – < 10cm ao longo dos lados – você deve estar bastante perto. Para um código QR da versão 1 variando de 10 a 25 cm de largura, a distância mínima de detecção varia de 0,15 metros a 0,5 metros. 

A distância de detecção para o tamanho aumenta linearmente. 

A detecção QR funciona com um intervalo de ângulos + = 45deg. Isso é para garantir que tenhamos a resolução adequada para detectar o código.

### <a name="qr-codes-with-logos"></a>Códigos QR com logotipos
Códigos QR com logotipos não foram testados e não têm suporte no momento.

### <a name="managing-qr-code-data"></a>Gerenciando dados de código QR
Dispositivos Windows Mixed Reality detectam códigos QR no nível do sistema no driver. Quando o dispositivo é reinicializado, os códigos QR detectados são desfeitos e serão detectados novamente como novos objetos da próxima vez.

É recomendável configurar seu aplicativo para ignorar códigos QR anteriores a um carimbo de data/hora específico. Atualmente, a API não dá suporte à limpeza do histórico de código QR.

### <a name="qr-code-placement-in-a-space"></a>Posicionamento de código QR em um espaço
Para obter recomendações sobre onde e como inserir códigos QR, consulte [considerações de ambiente para o HoloLens](environment-considerations-for-hololens.md).

## <a name="qr-api-reference"></a>Referência de API QR

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas](coordinate-systems.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a>

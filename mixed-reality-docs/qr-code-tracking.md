---
title: Acompanhamento de código QR
description: Saiba como detectar códigos QR no HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, entretenimento baseado na localização, VR de los, de los, de imersão, QR, QR Code, hololens2
ms.openlocfilehash: 6d3dc442c28e498cc00e14325398de2026261a17
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476758"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="76f61-104">Acompanhamento de código QR</span><span class="sxs-lookup"><span data-stu-id="76f61-104">QR code tracking</span></span>

<span data-ttu-id="76f61-105">O HoloLens 2 pode detectar códigos QR no ambiente em todo o headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código.</span><span class="sxs-lookup"><span data-stu-id="76f61-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="76f61-106">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="76f61-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="76f61-107">Recurso</span><span class="sxs-lookup"><span data-stu-id="76f61-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="76f61-108"><a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></span><span class="sxs-lookup"><span data-stu-id="76f61-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="76f61-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="76f61-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="76f61-110"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="76f61-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="76f61-111">Detecção de código QR</span><span class="sxs-lookup"><span data-stu-id="76f61-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="76f61-112">️</span><span class="sxs-lookup"><span data-stu-id="76f61-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="76f61-113">✔️</span><span class="sxs-lookup"><span data-stu-id="76f61-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="76f61-114">✔️</span><span class="sxs-lookup"><span data-stu-id="76f61-114">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="76f61-115">O controle de código QR com alto-se com o Windows Mixed Realm headsets em computadores desktop tem suporte no Windows 10 versão 2004 e superior.</span><span class="sxs-lookup"><span data-stu-id="76f61-115">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="76f61-116">Use a API Microsoft. MixedReality. QRCodeWatcher. IsSupported () para determinar se o recurso tem suporte no dispositivo atual.</span><span class="sxs-lookup"><span data-stu-id="76f61-116">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="76f61-117">Obtendo o pacote QR</span><span class="sxs-lookup"><span data-stu-id="76f61-117">Getting the QR package</span></span>
<span data-ttu-id="76f61-118">Você pode baixar o pacote NuGet para detecção de código QR [aqui](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span><span class="sxs-lookup"><span data-stu-id="76f61-118">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="76f61-119">Detectando códigos QR</span><span class="sxs-lookup"><span data-stu-id="76f61-119">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="76f61-120">Adicionando o recurso de webcam</span><span class="sxs-lookup"><span data-stu-id="76f61-120">Adding the webcam capability</span></span>
<span data-ttu-id="76f61-121">Você precisará adicionar a capacidade `webcam` ao seu manifesto para detectar códigos QR.</span><span class="sxs-lookup"><span data-stu-id="76f61-121">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="76f61-122">Esse recurso é necessário, pois os dados dentro de códigos detectados no ambiente do usuário podem conter informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="76f61-122">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="76f61-123">A permissão pode ser solicitada chamando `QRCodeWatcher.RequestAccessAsync()` :</span><span class="sxs-lookup"><span data-stu-id="76f61-123">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="76f61-124">_C#_</span><span class="sxs-lookup"><span data-stu-id="76f61-124">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="76f61-125">_C_</span><span class="sxs-lookup"><span data-stu-id="76f61-125">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="76f61-126">A permissão deve ser solicitada antes de construir um objeto QRCodeWatcher.</span><span class="sxs-lookup"><span data-stu-id="76f61-126">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="76f61-127">Embora a detecção de código QR exija o `webcam` recurso, a detecção ocorre usando as câmeras de rastreamento do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="76f61-127">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="76f61-128">Isso fornece uma FOV de detecção mais ampla e uma melhor vida útil da bateria em comparação com a detecção com a câmera de foto/vídeo (PV) do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="76f61-128">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="76f61-129">Detectando códigos QR no Unity</span><span class="sxs-lookup"><span data-stu-id="76f61-129">Detecting QR codes in Unity</span></span>

<span data-ttu-id="76f61-130">Você pode usar a API de detecção de código QR no Unity sem usar uma dependência no MRTK.</span><span class="sxs-lookup"><span data-stu-id="76f61-130">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="76f61-131">Para fazer isso, você deve instalar o pacote NuGet usando o [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="76f61-131">To do so, you must install the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>

<span data-ttu-id="76f61-132">Há um aplicativo do Unity de exemplo que exibe um quadrado Holographic sobre códigos QR, juntamente com os dados associados, como GUID, tamanho físico, carimbo de data/hora e dados decodificados.</span><span class="sxs-lookup"><span data-stu-id="76f61-132">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="76f61-133">Esse aplicativo pode ser localizado em https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes .</span><span class="sxs-lookup"><span data-stu-id="76f61-133">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="76f61-134">Detectando códigos QR em C++</span><span class="sxs-lookup"><span data-stu-id="76f61-134">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="76f61-135">Obtendo o sistema de coordenadas para um código QR</span><span class="sxs-lookup"><span data-stu-id="76f61-135">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="76f61-136">Cada código QR detectado expõe um [sistema de coordenadas espaciais](coordinate-systems.md) alinhado com o código QR no canto superior esquerdo do quadrado de detecção rápida na parte superior esquerda, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="76f61-136">Each detected QR code exposes a [spatial coordinate system](coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="76f61-137">Ao usar o SDK QR diretamente, o eixo Z está apontando para o papel (não mostrado)-quando convertido em coordenadas do Unity, o eixo Z aponta para fora do papel e é canhoto.</span><span class="sxs-lookup"><span data-stu-id="76f61-137">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="76f61-138">Um SpatialCoordinateSystem de código QR é alinhado conforme mostrado.</span><span class="sxs-lookup"><span data-stu-id="76f61-138">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="76f61-139">Esse sistema de coordenadas pode ser obtido na plataforma chamando <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> e passando o SpatialGraphNodeId do código.</span><span class="sxs-lookup"><span data-stu-id="76f61-139">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="76f61-141">Para um objeto QRCode, o código C++ a seguir mostra como criar um retângulo e colocá-lo usando o sistema de coordenadas do código QR:</span><span class="sxs-lookup"><span data-stu-id="76f61-141">For a QRCode object, the following C++ code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="76f61-142">Você pode usar o tamanho físico para criar o retângulo QR:</span><span class="sxs-lookup"><span data-stu-id="76f61-142">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="76f61-143">O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas ao local:</span><span class="sxs-lookup"><span data-stu-id="76f61-143">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="76f61-144">Totalmente, seu *QRCodeAddedHandler* pode ser semelhante a este:</span><span class="sxs-lookup"><span data-stu-id="76f61-144">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="76f61-145">Práticas recomendadas para detecção de código QR</span><span class="sxs-lookup"><span data-stu-id="76f61-145">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="76f61-146">Zonas silenciosas em cerca de códigos QR</span><span class="sxs-lookup"><span data-stu-id="76f61-146">Quiet zones around QR Codes</span></span>

<span data-ttu-id="76f61-147">Para ser lido corretamente, os códigos QR exigem uma margem em volta de todos os lados do código.</span><span class="sxs-lookup"><span data-stu-id="76f61-147">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="76f61-148">Essa margem não deve conter nenhum conteúdo impresso e deve ter quatro módulos (um único quadrado preto no código) de largura.</span><span class="sxs-lookup"><span data-stu-id="76f61-148">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="76f61-149">A [especificação QR](https://www.qrcode.com/en/howto/code.html) contém mais informações sobre zonas silenciosas.</span><span class="sxs-lookup"><span data-stu-id="76f61-149">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="76f61-150">Iluminação e pano de fundo</span><span class="sxs-lookup"><span data-stu-id="76f61-150">Lighting and backdrop</span></span>
<span data-ttu-id="76f61-151">A qualidade de detecção de código QR é suscetível à iluminação e ao pano de fundo variadas.</span><span class="sxs-lookup"><span data-stu-id="76f61-151">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="76f61-152">Em uma cena com iluminação particularmente brilhante, imprima um código preto em um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="76f61-152">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="76f61-153">Caso contrário, imprima um código QR preto em um plano de fundo branco.</span><span class="sxs-lookup"><span data-stu-id="76f61-153">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="76f61-154">Se o pano de fundo para o código for particularmente escuro, experimente um preto no código cinza se a taxa de detecção for baixa.</span><span class="sxs-lookup"><span data-stu-id="76f61-154">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="76f61-155">Se o pano de fundo for relativamente claro, um código regular deverá funcionar bem.</span><span class="sxs-lookup"><span data-stu-id="76f61-155">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="76f61-156">Tamanho dos códigos QR</span><span class="sxs-lookup"><span data-stu-id="76f61-156">Size of QR codes</span></span>
<span data-ttu-id="76f61-157">Os dispositivos Windows Mixed Reality não funcionam com códigos QR com lados menores que 5 cm cada.</span><span class="sxs-lookup"><span data-stu-id="76f61-157">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="76f61-158">Para códigos QR entre os lados de comprimento de 5 e 10 cm, você deve estar bastante perto de detectar o código.</span><span class="sxs-lookup"><span data-stu-id="76f61-158">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="76f61-159">Também levará mais tempo para detectar códigos nesse tamanho.</span><span class="sxs-lookup"><span data-stu-id="76f61-159">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="76f61-160">O tempo exato para detectar códigos depende não apenas do tamanho dos códigos QR, mas o quanto você está longe do código.</span><span class="sxs-lookup"><span data-stu-id="76f61-160">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="76f61-161">Avançar para o código ajudará a deslocar os problemas com o tamanho.</span><span class="sxs-lookup"><span data-stu-id="76f61-161">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="76f61-162">Distância e posição angular do código QR</span><span class="sxs-lookup"><span data-stu-id="76f61-162">Distance and angular position from the QR code</span></span>
<span data-ttu-id="76f61-163">As câmeras de rastreamento só podem detectar um determinado nível de detalhe.</span><span class="sxs-lookup"><span data-stu-id="76f61-163">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="76f61-164">Para códigos realmente pequenos – < 10cm ao longo dos lados – você deve estar bastante perto.</span><span class="sxs-lookup"><span data-stu-id="76f61-164">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="76f61-165">Para um código QR da versão 1 variando de 10 a 25 cm de largura, a distância mínima de detecção varia de 0,15 metros a 0,5 metros.</span><span class="sxs-lookup"><span data-stu-id="76f61-165">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="76f61-166">A distância de detecção para o tamanho aumenta linearmente.</span><span class="sxs-lookup"><span data-stu-id="76f61-166">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="76f61-167">A detecção QR funciona com um intervalo de ângulos + = 45deg.</span><span class="sxs-lookup"><span data-stu-id="76f61-167">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="76f61-168">Isso é para garantir que tenhamos a resolução adequada para detectar o código.</span><span class="sxs-lookup"><span data-stu-id="76f61-168">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="76f61-169">Códigos QR com logotipos</span><span class="sxs-lookup"><span data-stu-id="76f61-169">QR codes with logos</span></span>
<span data-ttu-id="76f61-170">Códigos QR com logotipos não foram testados e não têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="76f61-170">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="76f61-171">Gerenciando dados de código QR</span><span class="sxs-lookup"><span data-stu-id="76f61-171">Managing QR code data</span></span>
<span data-ttu-id="76f61-172">Dispositivos Windows Mixed Reality detectam códigos QR no nível do sistema no driver.</span><span class="sxs-lookup"><span data-stu-id="76f61-172">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="76f61-173">Quando o dispositivo é reinicializado, os códigos QR detectados são desfeitos e serão detectados novamente como novos objetos da próxima vez.</span><span class="sxs-lookup"><span data-stu-id="76f61-173">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="76f61-174">É recomendável configurar seu aplicativo para ignorar códigos QR anteriores a um carimbo de data/hora específico.</span><span class="sxs-lookup"><span data-stu-id="76f61-174">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="76f61-175">Atualmente, a API não dá suporte à limpeza do histórico de código QR.</span><span class="sxs-lookup"><span data-stu-id="76f61-175">Currently, the API does not support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="76f61-176">Posicionamento de código QR em um espaço</span><span class="sxs-lookup"><span data-stu-id="76f61-176">QR code placement in a space</span></span>
<span data-ttu-id="76f61-177">Para obter recomendações sobre onde e como inserir códigos QR, consulte [considerações de ambiente para o HoloLens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="76f61-177">For recommendations on where and how to place QR codes, please refer to [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="76f61-178">Referência de API QR</span><span class="sxs-lookup"><span data-stu-id="76f61-178">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="76f61-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76f61-179">See also</span></span>
* [<span data-ttu-id="76f61-180">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="76f61-180">Coordinate systems</span></span>](coordinate-systems.md)
* <span data-ttu-id="76f61-181"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="76f61-181"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>

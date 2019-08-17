---
title: Controle de código QR
description: Saiba como detectar códigos QR no HoloLens 2.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, entretenimento baseado na localização, VR de los, de los, de imersão, QR, QR Code, hololens2
ms.openlocfilehash: d51da88aa7bff1dc5c6d3068cb31793891c71e61
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566002"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="4045e-104">Controle de código QR</span><span class="sxs-lookup"><span data-stu-id="4045e-104">QR code tracking</span></span>

<span data-ttu-id="4045e-105">O HoloLens 2 pode detectar códigos QR no ambiente em todo o headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código.</span><span class="sxs-lookup"><span data-stu-id="4045e-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="4045e-106">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="4045e-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4045e-107">Recurso</span><span class="sxs-lookup"><span data-stu-id="4045e-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4045e-108"><a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></span><span class="sxs-lookup"><span data-stu-id="4045e-108"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="4045e-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4045e-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="4045e-110"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="4045e-110"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4045e-111">Detecção de código QR</span><span class="sxs-lookup"><span data-stu-id="4045e-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="4045e-112">️</span><span class="sxs-lookup"><span data-stu-id="4045e-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4045e-113">✔️</span><span class="sxs-lookup"><span data-stu-id="4045e-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4045e-114">Consulte a observação</span><span class="sxs-lookup"><span data-stu-id="4045e-114">See note</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="4045e-115">No momento, não há suporte para o suporte a headsets de imersão misturadas do Windows em computadores desktop com o pacote NuGet abaixo.</span><span class="sxs-lookup"><span data-stu-id="4045e-115">Support for immersive Windows Mixed Reality headsets on desktop PCs is not currently supported with the NuGet package below.</span></span>  <span data-ttu-id="4045e-116">Fique atento para obter mais atualizações sobre o suporte a desktops.</span><span class="sxs-lookup"><span data-stu-id="4045e-116">Stay tuned for further updates on desktop support.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="4045e-117">Obtendo o pacote QR</span><span class="sxs-lookup"><span data-stu-id="4045e-117">Getting the QR package</span></span>
<span data-ttu-id="4045e-118">Você pode baixar um pacote NuGet para detecção de código QR [aqui](https://github.com/dorreneb/mixed-reality/releases).</span><span class="sxs-lookup"><span data-stu-id="4045e-118">You can download a NuGet package for QR code detection [here](https://github.com/dorreneb/mixed-reality/releases).</span></span>

<span data-ttu-id="4045e-119">Versões futuras deste pacote estarão disponíveis por meio do repositório público de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="4045e-119">Future versions of this package will be available through the public NuGet package repository.</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="4045e-120">Detectando códigos QR</span><span class="sxs-lookup"><span data-stu-id="4045e-120">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="4045e-121">Adicionando o recurso de webcam</span><span class="sxs-lookup"><span data-stu-id="4045e-121">Adding the webcam capability</span></span>
<span data-ttu-id="4045e-122">Você precisará adicionar a capacidade `webcam` ao seu manifesto para detectar códigos QR.</span><span class="sxs-lookup"><span data-stu-id="4045e-122">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="4045e-123">Esse recurso é necessário, pois os dados dentro de códigos detectados no ambiente do usuário podem conter informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="4045e-123">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="4045e-124">A permissão pode ser solicitada `QRCodeWatcher.RequestAccessAsync()`chamando:</span><span class="sxs-lookup"><span data-stu-id="4045e-124">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="4045e-125">_C#:_</span><span class="sxs-lookup"><span data-stu-id="4045e-125">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="4045e-126">_C++:_</span><span class="sxs-lookup"><span data-stu-id="4045e-126">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="4045e-127">A permissão deve ser solicitada antes de construir um objeto QRCodeWatcher.</span><span class="sxs-lookup"><span data-stu-id="4045e-127">Permission should be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="4045e-128">Embora a detecção de código QR `webcam` exija o recurso, a detecção ocorre usando as câmeras de rastreamento do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4045e-128">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="4045e-129">Isso fornece uma FOV de detecção mais ampla e uma melhor vida útil da bateria em comparação com a detecção com a câmera de foto/vídeo (PV) do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4045e-129">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="4045e-130">Detectando códigos QR no Unity</span><span class="sxs-lookup"><span data-stu-id="4045e-130">Detecting QR codes in Unity</span></span>

<span data-ttu-id="4045e-131">Você pode usar a API de detecção de código QR no Unity sem usar uma dependência no MRTK.</span><span class="sxs-lookup"><span data-stu-id="4045e-131">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="4045e-132">Para fazer isso, você deve:</span><span class="sxs-lookup"><span data-stu-id="4045e-132">To do so, you must:</span></span>

1. <span data-ttu-id="4045e-133">Crie uma nova pasta na pasta ativos do seu projeto do Unity com os nomes de *plug-ins*.</span><span class="sxs-lookup"><span data-stu-id="4045e-133">Create a new folder in the assets folder of your unity project with the name *Plugins*.</span></span>
2. <span data-ttu-id="4045e-134">Copie todos os arquivos necessários dessa pasta para a pasta "plugins" local que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="4045e-134">Copy all the required files from this folder into the local "Plugins" folder you just created.</span></span>

<span data-ttu-id="4045e-135">Há um aplicativo do Unity de exemplo que exibe um quadrado Holographic sobre códigos QR, juntamente com os dados associados, como GUID, tamanho físico, carimbo de data/hora e dados decodificados.</span><span class="sxs-lookup"><span data-stu-id="4045e-135">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="4045e-136">Esse aplicativo pode ser localizado em https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span><span class="sxs-lookup"><span data-stu-id="4045e-136">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="4045e-137">Detectando códigos QR noC++</span><span class="sxs-lookup"><span data-stu-id="4045e-137">Detecting QR codes in C++</span></span>

>[!NOTE]
><span data-ttu-id="4045e-138">Os C++ trechos de código neste artigo demonstram atualmente o uso C++de/CX em vez de/WinRT em conformidade C++com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="4045e-138">The C++ code snippets in this article currently demonstrate the use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="4045e-139">Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="4045e-139">The concepts are equivalent for a C++/WinRT project, though you need to translate the code.</span></span>

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="4045e-140">Obtendo o sistema de coordenadas para um código QR</span><span class="sxs-lookup"><span data-stu-id="4045e-140">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="4045e-141">Cada código QR detectado expõe um [sistema de coordenadas espaciais](coordinate-systems.md) alinhado com o código QR no canto superior esquerdo do quadrado de detecção rápida na parte superior esquerda, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="4045e-141">Each detected QR code exposes a [spatial coordinate system](coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="4045e-142">Ao usar o SDK QR diretamente, o eixo Z está apontando para o papel (não mostrado)-quando convertido em coordenadas do Unity, o eixo Z aponta para fora do papel e é canhoto.</span><span class="sxs-lookup"><span data-stu-id="4045e-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="4045e-143">Um código QR SpatialCoordinateSystem alinha os alinhamentos mostrados.</span><span class="sxs-lookup"><span data-stu-id="4045e-143">A QR code's SpatialCoordinateSystem aligns shown.</span></span> <span data-ttu-id="4045e-144">Esse sistema de coordenadas pode ser obtido na plataforma chamando <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview:: CreateCoordinateSystemForNode</a> e passando o SpatialGraphNodeId do código.</span><span class="sxs-lookup"><span data-stu-id="4045e-144">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="4045e-146">Para um objeto QRCode, o código C++/CX a seguir mostra como criar um retângulo e colocá-lo usando o sistema de coordenadas do código QR:</span><span class="sxs-lookup"><span data-stu-id="4045e-146">For a QRCode object, the following C++/CX code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="4045e-147">Você pode usar o tamanho físico para criar o retângulo QR:</span><span class="sxs-lookup"><span data-stu-id="4045e-147">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="4045e-148">O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas ao local:</span><span class="sxs-lookup"><span data-stu-id="4045e-148">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

<span data-ttu-id="4045e-149">Totalmente, seu *QRCodeWatcher:: QRCodeAddedHandler* pode ser semelhante a este:</span><span class="sxs-lookup"><span data-stu-id="4045e-149">Altogether, your *QRCodeWatcher::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="4045e-150">Práticas recomendadas para detecção de código QR</span><span class="sxs-lookup"><span data-stu-id="4045e-150">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="4045e-151">Zonas silenciosas em cerca de códigos QR</span><span class="sxs-lookup"><span data-stu-id="4045e-151">Quiet zones around QR Codes</span></span>

<span data-ttu-id="4045e-152">Para ser lido corretamente, os códigos QR exigem uma margem em volta de todos os lados do código.</span><span class="sxs-lookup"><span data-stu-id="4045e-152">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="4045e-153">Essa margem não deve conter nenhum conteúdo impresso e deve ter quatro módulos (um único quadrado preto no código) de largura.</span><span class="sxs-lookup"><span data-stu-id="4045e-153">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="4045e-154">A [especificação QR](https://www.qrcode.com/en/howto/code.html) contém mais informações sobre zonas silenciosas.</span><span class="sxs-lookup"><span data-stu-id="4045e-154">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="4045e-155">Iluminação e pano de fundo</span><span class="sxs-lookup"><span data-stu-id="4045e-155">Lighting and backdrop</span></span>
<span data-ttu-id="4045e-156">A qualidade de detecção de código QR é suscetível à iluminação e ao pano de fundo variadas.</span><span class="sxs-lookup"><span data-stu-id="4045e-156">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="4045e-157">Em uma cena com iluminação particularmente brilhante, imprima um código preto em um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="4045e-157">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="4045e-158">Caso contrário, imprima um código QR preto em um plano de fundo branco.</span><span class="sxs-lookup"><span data-stu-id="4045e-158">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="4045e-159">Se o pano de fundo para o código for particularmente escuro, experimente um preto no código cinza se a taxa de detecção for baixa.</span><span class="sxs-lookup"><span data-stu-id="4045e-159">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="4045e-160">Se o pano de fundo for relativamente claro, um código regular deverá funcionar bem.</span><span class="sxs-lookup"><span data-stu-id="4045e-160">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="4045e-161">Tamanho dos códigos QR</span><span class="sxs-lookup"><span data-stu-id="4045e-161">Size of QR codes</span></span>
<span data-ttu-id="4045e-162">Os dispositivos Windows Mixed Reality não funcionam com códigos QR com lados menores que 5 cm cada.</span><span class="sxs-lookup"><span data-stu-id="4045e-162">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="4045e-163">Para códigos QR entre os lados de comprimento de 5 e 10 cm, você deve estar bastante perto de detectar o código.</span><span class="sxs-lookup"><span data-stu-id="4045e-163">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="4045e-164">Também levará mais tempo para detectar códigos nesse tamanho.</span><span class="sxs-lookup"><span data-stu-id="4045e-164">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="4045e-165">O tempo exato para detectar códigos depende não apenas do tamanho dos códigos QR, mas o quanto você está longe do código.</span><span class="sxs-lookup"><span data-stu-id="4045e-165">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="4045e-166">Avançar para o código ajudará a deslocar os problemas com o tamanho.</span><span class="sxs-lookup"><span data-stu-id="4045e-166">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="4045e-167">Distância e posição angular do código QR</span><span class="sxs-lookup"><span data-stu-id="4045e-167">Distance and angular position from the QR code</span></span>
<span data-ttu-id="4045e-168">As câmeras de rastreamento só podem detectar um determinado nível de detalhe.</span><span class="sxs-lookup"><span data-stu-id="4045e-168">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="4045e-169">Para códigos realmente pequenos – < 10cm ao longo dos lados – você deve estar bastante perto.</span><span class="sxs-lookup"><span data-stu-id="4045e-169">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="4045e-170">Para um código QR da versão 1 variando de 10 a 25 cm de largura, a distância mínima de detecção varia de 0,15 metros a 0,5 metros.</span><span class="sxs-lookup"><span data-stu-id="4045e-170">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="4045e-171">A distância de detecção para o tamanho aumenta linearmente.</span><span class="sxs-lookup"><span data-stu-id="4045e-171">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="4045e-172">A detecção QR funciona com um intervalo de ângulos + = 45deg.</span><span class="sxs-lookup"><span data-stu-id="4045e-172">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="4045e-173">Isso é para garantir que tenhamos a resolução adequada para detectar o código.</span><span class="sxs-lookup"><span data-stu-id="4045e-173">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="4045e-174">Códigos QR com logotipos</span><span class="sxs-lookup"><span data-stu-id="4045e-174">QR codes with logos</span></span>
<span data-ttu-id="4045e-175">Códigos QR com logotipos não foram testados e não têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="4045e-175">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="4045e-176">Gerenciando dados de código QR</span><span class="sxs-lookup"><span data-stu-id="4045e-176">Managing QR code data</span></span>
<span data-ttu-id="4045e-177">Dispositivos Windows Mixed Reality detectam códigos QR no nível do sistema no driver.</span><span class="sxs-lookup"><span data-stu-id="4045e-177">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="4045e-178">Quando o dispositivo é reinicializado, os códigos QR detectados são desfeitos e serão detectados novamente como novos objetos da próxima vez.</span><span class="sxs-lookup"><span data-stu-id="4045e-178">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="4045e-179">É recomendável configurar seu aplicativo para ignorar códigos QR anteriores a um carimbo de data/hora específico.</span><span class="sxs-lookup"><span data-stu-id="4045e-179">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="4045e-180">Atualmente, a API não dá suporte à limpeza do histórico de código QR.</span><span class="sxs-lookup"><span data-stu-id="4045e-180">Currently, the API does not support clearing QR code history.</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="4045e-181">Referência de API QR</span><span class="sxs-lookup"><span data-stu-id="4045e-181">QR API reference</span></span>

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
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

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
    public enum VersionInfo
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

## <a name="see-also"></a><span data-ttu-id="4045e-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4045e-182">See also</span></span>
* [<span data-ttu-id="4045e-183">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="4045e-183">Coordinate systems</span></span>](coordinate-systems.md)
* <span data-ttu-id="4045e-184"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="4045e-184"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>
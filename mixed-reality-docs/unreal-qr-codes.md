---
title: Códigos QR no Unreal
description: Um guia para usar códigos QR no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: a53fad14ab76136f1da419379dd39eca3a29701a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376098"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="3b588-104">Códigos QR no Unreal</span><span class="sxs-lookup"><span data-stu-id="3b588-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="3b588-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3b588-105">Overview</span></span>

<span data-ttu-id="3b588-106">O HoloLens 2 pode ver códigos QR no espaço de mundo usando a webcam, que os renderiza como hologramas usando um sistema de coordenadas na posição de cada código no mundo real.</span><span class="sxs-lookup"><span data-stu-id="3b588-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="3b588-107">Além de códigos QR individuais, o HoloLens 2 também pode renderizar hologramas em vários dispositivos no mesmo local para criar uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="3b588-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="3b588-108">Verifique se você está seguindo as melhores práticas para adicionar códigos QR aos aplicativos:</span><span class="sxs-lookup"><span data-stu-id="3b588-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="3b588-109">Zonas silenciosas</span><span class="sxs-lookup"><span data-stu-id="3b588-109">Quiet zones</span></span>
- <span data-ttu-id="3b588-110">Iluminação e pano de fundo</span><span class="sxs-lookup"><span data-stu-id="3b588-110">Lighting and backdrop</span></span>
- <span data-ttu-id="3b588-111">Tamanho, distância e posição angular</span><span class="sxs-lookup"><span data-stu-id="3b588-111">Size, distance, and angular position</span></span>

<span data-ttu-id="3b588-112">Preste atenção especial às [considerações sobre o ambiente](environment-considerations-for-hololens.md) quando os códigos QR estiverem sendo posicionados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b588-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="3b588-113">Você pode encontrar mais informações sobre cada um desses tópicos e instruções sobre como baixar o pacote NuGet necessário no documento principal [rastreamento de código QR](qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="3b588-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="3b588-114">Como habilitar a detecção de QR</span><span class="sxs-lookup"><span data-stu-id="3b588-114">Enabling QR detection</span></span>
<span data-ttu-id="3b588-115">Como o HoloLens 2 precisa usar a webcam para ver os códigos QR, você precisará habilitá-la nas configurações do projeto:</span><span class="sxs-lookup"><span data-stu-id="3b588-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="3b588-116">Abra **Editar > Configurações do Projeto**, role até a seção **Plataformas** e clique em **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="3b588-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="3b588-117">Expanda a seção **Funcionalidades** e marque **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="3b588-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="3b588-118">Você também precisará aceitar o controle de código QR [adicionando um ativo ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="3b588-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="3b588-119">Logo antes do uso, habilite manualmente o rastreamento chamando `UHoloLensARFunctionLibrary::StartQRCodeCapture()`.</span><span class="sxs-lookup"><span data-stu-id="3b588-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartQRCodeCapture()`.</span></span> <span data-ttu-id="3b588-120">Depois de encerrar o rastreamento do código QR, desabilite-o com `UHoloLensARFunctionLibrary::StopCameraCapture()` para salvar os recursos do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3b588-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span> 

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="3b588-121">Configurar uma imagem rastreada</span><span class="sxs-lookup"><span data-stu-id="3b588-121">Setting up a tracked image</span></span>

<span data-ttu-id="3b588-122">Os códigos QR são exibidos por meio do sistema de geometria controlado pelo RA do Unreal como uma imagem rastreada.</span><span class="sxs-lookup"><span data-stu-id="3b588-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="3b588-123">Para fazer isso funcionar, você precisará:</span><span class="sxs-lookup"><span data-stu-id="3b588-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="3b588-124">Criar um Blueprint e adicionar um componente **ARTrackableNotify** a ele.</span><span class="sxs-lookup"><span data-stu-id="3b588-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![AR Trackable Notify de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="3b588-126">Selecione **ARTrackableNotify** e expanda a seção **Eventos** no painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="3b588-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![Eventos de QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="3b588-128">Clique em **+** ao lado de **Ao Adicionar Geometria Rastreada** para adicionar o nó ao Grafo de Eventos.</span><span class="sxs-lookup"><span data-stu-id="3b588-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="3b588-129">Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="3b588-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![Exemplo de renderização de QR](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="3b588-131">Como usar uma imagem rastreada</span><span class="sxs-lookup"><span data-stu-id="3b588-131">Using a tracked image</span></span>
<span data-ttu-id="3b588-132">O Grafo de Eventos na imagem a seguir mostra o evento **OnUpdateTrackedImage** que está sendo usado para processar um ponto no centro de um código QR e imprimir os dados desse código.</span><span class="sxs-lookup"><span data-stu-id="3b588-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![Exemplo de renderização de QR](images/unreal-qr-render.PNG)

<span data-ttu-id="3b588-134">Isto é o que está acontecendo:</span><span class="sxs-lookup"><span data-stu-id="3b588-134">Here's what's going on:</span></span>
1. <span data-ttu-id="3b588-135">Primeiro, a imagem rastreada é convertida em um **ARTrackedQRCode** para verificar se a imagem atualizada atual é um código QR.</span><span class="sxs-lookup"><span data-stu-id="3b588-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="3b588-136">Os dados codificados são recuperados da variável **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="3b588-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="3b588-137">Com o local de **GetLocalToWorldTransform**, é possível obter as coordenadas do canto superior esquerdo do código QR; já com **GetEstimateSize**, é possível obter as dimensões desse código.</span><span class="sxs-lookup"><span data-stu-id="3b588-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="3b588-138">Você também pode [obter o sistema de coordenadas de um código QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) no código.</span><span class="sxs-lookup"><span data-stu-id="3b588-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="3b588-139">Como localizar a ID exclusiva</span><span class="sxs-lookup"><span data-stu-id="3b588-139">Finding the unique ID</span></span>
<span data-ttu-id="3b588-140">Todo código QR tem uma ID GUID exclusiva, que pode ser encontrada:</span><span class="sxs-lookup"><span data-stu-id="3b588-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="3b588-141">Arrastando e soltando o marcador **Como QRCode ARTracked** e pesquisando por **Obter ID Exclusiva**.</span><span class="sxs-lookup"><span data-stu-id="3b588-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID de QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="3b588-143">Há muita coisa acontecendo nos bastidores envolvendo códigos QR, portanto, esse não é o fim da linha.</span><span class="sxs-lookup"><span data-stu-id="3b588-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="3b588-144">Não deixe de conferir os links a seguir para obter mais detalhes sobre o que está acontecendo nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="3b588-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b588-145">Veja também</span><span class="sxs-lookup"><span data-stu-id="3b588-145">See also</span></span>
* [<span data-ttu-id="3b588-146">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="3b588-146">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="3b588-147">Hologramas</span><span class="sxs-lookup"><span data-stu-id="3b588-147">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="3b588-148">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="3b588-148">Coordinate systems</span></span>](coordinate-systems.md)

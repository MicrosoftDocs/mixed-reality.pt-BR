---
title: Códigos QR no Unreal
description: Um guia para usar códigos QR no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: cf6c113f6bf4a13a96f46d6420a3093966455c3b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720382"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="56fd2-104">Códigos QR no Unreal</span><span class="sxs-lookup"><span data-stu-id="56fd2-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="56fd2-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="56fd2-105">Overview</span></span>

<span data-ttu-id="56fd2-106">O HoloLens 2 pode ver códigos QR no espaço de mundo usando a webcam, que os renderiza como hologramas usando um sistema de coordenadas na posição de cada código no mundo real.</span><span class="sxs-lookup"><span data-stu-id="56fd2-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="56fd2-107">Além de códigos QR individuais, o HoloLens 2 também pode renderizar hologramas em vários dispositivos no mesmo local para criar uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="56fd2-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="56fd2-108">Verifique se você está seguindo as melhores práticas para adicionar códigos QR aos aplicativos:</span><span class="sxs-lookup"><span data-stu-id="56fd2-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="56fd2-109">Zonas silenciosas</span><span class="sxs-lookup"><span data-stu-id="56fd2-109">Quiet zones</span></span>
- <span data-ttu-id="56fd2-110">Iluminação e pano de fundo</span><span class="sxs-lookup"><span data-stu-id="56fd2-110">Lighting and backdrop</span></span>
- <span data-ttu-id="56fd2-111">Tamanho, distância e posição angular</span><span class="sxs-lookup"><span data-stu-id="56fd2-111">Size, distance, and angular position</span></span>

<span data-ttu-id="56fd2-112">Preste atenção especial às [considerações sobre o ambiente](environment-considerations-for-hololens.md) quando os códigos QR estiverem sendo posicionados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="56fd2-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="56fd2-113">Você pode encontrar mais informações sobre cada um desses tópicos e instruções sobre como baixar o pacote NuGet necessário no documento principal [rastreamento de código QR](qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="56fd2-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="56fd2-114">Como habilitar a detecção de QR</span><span class="sxs-lookup"><span data-stu-id="56fd2-114">Enabling QR detection</span></span>
<span data-ttu-id="56fd2-115">Como o HoloLens 2 precisa usar a webcam para ver os códigos QR, você precisará habilitá-la nas configurações do projeto:</span><span class="sxs-lookup"><span data-stu-id="56fd2-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="56fd2-116">Abra **Editar > Configurações do Projeto**, role até a seção **Plataformas** e clique em **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="56fd2-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="56fd2-117">Expanda a seção **Funcionalidades** e marque **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="56fd2-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="56fd2-118">Você também precisará aceitar o controle de código QR [adicionando um ativo ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="56fd2-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="56fd2-119">Configurar uma imagem rastreada</span><span class="sxs-lookup"><span data-stu-id="56fd2-119">Setting up a tracked image</span></span>

<span data-ttu-id="56fd2-120">Os códigos QR são exibidos por meio do sistema de geometria controlado pelo RA do Unreal como uma imagem rastreada.</span><span class="sxs-lookup"><span data-stu-id="56fd2-120">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="56fd2-121">Para fazer isso funcionar, você precisará:</span><span class="sxs-lookup"><span data-stu-id="56fd2-121">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="56fd2-122">Criar um Blueprint e adicionar um componente **ARTrackableNotify** a ele.</span><span class="sxs-lookup"><span data-stu-id="56fd2-122">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![AR Trackable Notify de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="56fd2-124">Selecione **ARTrackableNotify** e expanda a seção **Eventos** no painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="56fd2-124">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![Eventos de QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="56fd2-126">Clique em **+** ao lado de **Ao Adicionar Geometria Rastreada** para adicionar o nó ao Grafo de Eventos.</span><span class="sxs-lookup"><span data-stu-id="56fd2-126">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="56fd2-127">Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="56fd2-127">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![Exemplo de renderização de QR](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="56fd2-129">Como usar uma imagem rastreada</span><span class="sxs-lookup"><span data-stu-id="56fd2-129">Using a tracked image</span></span>
<span data-ttu-id="56fd2-130">O Grafo de Eventos na imagem a seguir mostra o evento **OnUpdateTrackedImage** que está sendo usado para processar um ponto no centro de um código QR e imprimir os dados desse código.</span><span class="sxs-lookup"><span data-stu-id="56fd2-130">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![Exemplo de renderização de QR](images/unreal-qr-render.PNG)

<span data-ttu-id="56fd2-132">Isto é o que está acontecendo:</span><span class="sxs-lookup"><span data-stu-id="56fd2-132">Here's what's going on:</span></span>
1. <span data-ttu-id="56fd2-133">Primeiro, a imagem rastreada é convertida em um **ARTrackedQRCode** para verificar se a imagem atualizada atual é um código QR.</span><span class="sxs-lookup"><span data-stu-id="56fd2-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="56fd2-134">Os dados codificados são recuperados da variável **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="56fd2-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="56fd2-135">Com o local de **GetLocalToWorldTransform**, é possível obter as coordenadas do canto superior esquerdo do código QR; já com **GetEstimateSize**, é possível obter as dimensões desse código.</span><span class="sxs-lookup"><span data-stu-id="56fd2-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="56fd2-136">Você também pode [obter o sistema de coordenadas de um código QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) no código.</span><span class="sxs-lookup"><span data-stu-id="56fd2-136">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="56fd2-137">Como localizar a ID exclusiva</span><span class="sxs-lookup"><span data-stu-id="56fd2-137">Finding the unique ID</span></span>
<span data-ttu-id="56fd2-138">Todo código QR tem uma ID GUID exclusiva, que pode ser encontrada:</span><span class="sxs-lookup"><span data-stu-id="56fd2-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="56fd2-139">Arrastando e soltando o marcador **Como QRCode ARTracked** e pesquisando por **Obter ID Exclusiva**.</span><span class="sxs-lookup"><span data-stu-id="56fd2-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID de QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="56fd2-141">Há muita coisa acontecendo nos bastidores envolvendo códigos QR, portanto, esse não é o fim da linha.</span><span class="sxs-lookup"><span data-stu-id="56fd2-141">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="56fd2-142">Não deixe de conferir os links a seguir para obter mais detalhes sobre o que está acontecendo nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="56fd2-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="56fd2-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="56fd2-143">See also</span></span>
* [<span data-ttu-id="56fd2-144">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="56fd2-144">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="56fd2-145">Hologramas</span><span class="sxs-lookup"><span data-stu-id="56fd2-145">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="56fd2-146">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="56fd2-146">Coordinate systems</span></span>](coordinate-systems.md)
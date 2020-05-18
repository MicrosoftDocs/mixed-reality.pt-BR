---
title: Códigos QR no Unreal
description: Guia para usar códigos QR no Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342654"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="5825a-104">Códigos QR no Unreal</span><span class="sxs-lookup"><span data-stu-id="5825a-104">QR codes in Unreal</span></span>

<span data-ttu-id="5825a-105">O HoloLens pode localizar códigos QR no espaço do mundo para renderizar hologramas em posições conhecidas no mundo real.</span><span class="sxs-lookup"><span data-stu-id="5825a-105">HoloLens can locate QR codes in world space to render holograms at known positions in the real world.</span></span>  <span data-ttu-id="5825a-106">Isso também pode ser usado para renderizar hologramas em vários dispositivos no mesmo local para criar uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="5825a-106">This can also be used to render holograms on multiple devices in the same location to create a shared experience.</span></span> 

<span data-ttu-id="5825a-107">Para habilitar a detecção de QR no HoloLens, verifique se a funcionalidade "Webcam" está marcada no editor do Unreal em Configurações do Projeto > Plataforma > HoloLens > Funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="5825a-107">To enable QR detection on HoloLens, ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="5825a-108">Aceite o uso do controle de código QR no Unreal iniciando uma ARSession com a função StartARSession.</span><span class="sxs-lookup"><span data-stu-id="5825a-108">Opt into using QR code tracking in Unreal by starting an ARSession with the StartARSession function.</span></span> 

<span data-ttu-id="5825a-109">Os códigos QR são exibidos por meio do sistema de geometria controlado pelo RA do Unreal como uma imagem rastreada.</span><span class="sxs-lookup"><span data-stu-id="5825a-109">QR Codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span>  <span data-ttu-id="5825a-110">Para usar isso, adicione um componente AR Trackable Notify a um ator do Blueprint:</span><span class="sxs-lookup"><span data-stu-id="5825a-110">To use this, add an AR Trackable Notify component to a Blueprint actor:</span></span> 

![AR Trackable Notify de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="5825a-112">Em seguida, acesse os detalhes do componente e clique no botão "+" verde nos eventos a serem monitorados.</span><span class="sxs-lookup"><span data-stu-id="5825a-112">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span>  

![Eventos de QR](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="5825a-114">Aqui, assinamos o OnUpdateTrackedImage para renderizar um ponto no centro de um código QR e imprimir os dados codificados do código QR.</span><span class="sxs-lookup"><span data-stu-id="5825a-114">Here, we have subscribed to OnUpdateTrackedImage to render a point in the center of a QR Code and print the QR code’s encoded data.</span></span> 

![Exemplo de renderização de QR](images/unreal-qr-render.PNG)

<span data-ttu-id="5825a-116">Primeiro, converta a imagem rastreada em um ARTrackedQRCode para verificar se a imagem atualizada atual é um código QR.</span><span class="sxs-lookup"><span data-stu-id="5825a-116">First cast the tracked image to an ARTrackedQRCode to verify that the current updated image is a QR code.</span></span>  <span data-ttu-id="5825a-117">Em seguida, os dados codificados podem ser recuperados com a variável QRCode.</span><span class="sxs-lookup"><span data-stu-id="5825a-117">Then the encoded data can be retrieved with the QRCode variable.</span></span>  <span data-ttu-id="5825a-118">A parte superior esquerda do código QR pode ser recuperada do local de GetLocalToWorldTransform.</span><span class="sxs-lookup"><span data-stu-id="5825a-118">The top-left of the QR code can be retrieved from the location of GetLocalToWorldTransform.</span></span>  <span data-ttu-id="5825a-119">As dimensões podem ser recuperadas com GetEstimateSize.</span><span class="sxs-lookup"><span data-stu-id="5825a-119">The dimensions can be retrieved with GetEstimateSize.</span></span> 

<span data-ttu-id="5825a-120">Todo código QR também tem uma ID de GUID exclusiva:</span><span class="sxs-lookup"><span data-stu-id="5825a-120">Every QR code also has a unique guid ID:</span></span> 

![GUID de QR](images/unreal-qr-guid.PNG)

## <a name="see-also"></a><span data-ttu-id="5825a-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="5825a-122">See also</span></span>
* [<span data-ttu-id="5825a-123">Acompanhamento de código QR</span><span class="sxs-lookup"><span data-stu-id="5825a-123">QR code tracking</span></span>](qr-code-tracking.md)

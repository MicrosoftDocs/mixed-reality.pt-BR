---
title: Histórico de versões de comunicação remota do Holographic
description: Histórico de versão da comunicação remota do Holographic no HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: f051dbf24cab550470a312933ffb99e1ba595257
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181956"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="caff8-104">Histórico de versões de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="caff8-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="caff8-105">Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="caff8-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="caff8-106">Versão 2.0.18.0 (17 de dezembro de 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="caff8-106">Version 2.0.18.0 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="caff8-107">Adicionado suporte para HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="caff8-107">Added support for HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span></span>
* <span data-ttu-id="caff8-108">Correção de vários bugs que levam a falhas.</span><span class="sxs-lookup"><span data-stu-id="caff8-108">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="caff8-109">Corrigido o bug em que um retorno de chamada HolographicSpace. CameraAdded era necessário para um HolographicCamera ser aceito e exibido como uma câmera adicionada no HoloraphicFrame.</span><span class="sxs-lookup"><span data-stu-id="caff8-109">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="caff8-110">Versão 2.0.16 (11 de novembro de 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="caff8-110">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="caff8-111">Correção de deadlock no controle de código QR.</span><span class="sxs-lookup"><span data-stu-id="caff8-111">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="caff8-112">Correção da exceção unhandeled devido à espera de bloqueio no thread principal.</span><span class="sxs-lookup"><span data-stu-id="caff8-112">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="caff8-113">Versão 2.0.14 (26 de outubro de 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="caff8-113">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="caff8-114">Suporte para novas APIs PerceptionDevice (atualização de novembro de 2019 do Windows 10).</span><span class="sxs-lookup"><span data-stu-id="caff8-114">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="caff8-115">Correção do problema que impede que eventos de gesto de manutenção sejam disparados por SpatialGestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="caff8-115">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="caff8-116">Corrigido o problema de Threading ao usar SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="caff8-116">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="caff8-117">Versão 2.0.12 (18 de outubro de 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="caff8-117">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="caff8-118">Correção de falha em SpatialGestureRecognizer ao usar NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="caff8-118">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="caff8-119">Versão 2.0.10 (10 de outubro de 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="caff8-119">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="caff8-120">Correção de falha ao usar o botão de gatilho de controladores VR.</span><span class="sxs-lookup"><span data-stu-id="caff8-120">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="caff8-121">A comunicação remota do Holographic não dá suporte total a controladores, apenas o botão de gatilho e o botão do Windows estão funcionando se emparelhados com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="caff8-121">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="caff8-122">Versão 2.0.9 (19 de setembro de 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="caff8-122">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="caff8-123">Adicionado suporte para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="caff8-123">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="caff8-124">Adicionada nova ```IPlayerContext2``` de interface (implementada por ```PlayerContext```) fornecendo os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="caff8-124">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="caff8-125">Propriedade [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="caff8-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="caff8-126">Adicionado ```Failed_RemoteFrameTooOld``` valor a ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="caff8-126">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="caff8-127">Aprimoramentos de estabilidade e confiabilidade</span><span class="sxs-lookup"><span data-stu-id="caff8-127">Stability and reliability improvements</span></span>

## <span data-ttu-id="caff8-128">Versão 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="caff8-128">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="caff8-129">Correção de falha ao chamar [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) com um [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="caff8-129">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="caff8-130">Aprimoramentos de estabilidade e confiabilidade</span><span class="sxs-lookup"><span data-stu-id="caff8-130">Stability and reliability improvements</span></span>

## <span data-ttu-id="caff8-131">Versão 2.0.7 (26 de julho de 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="caff8-131">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="caff8-132">Primeira versão pública da comunicação remota do Holographic para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="caff8-132">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="caff8-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="caff8-133">See Also</span></span>
* [<span data-ttu-id="caff8-134">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="caff8-134">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="caff8-135">Escrevendo um aplicativo de host de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="caff8-135">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="caff8-136">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="caff8-136">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="caff8-137">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="caff8-137">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="caff8-138">Política de Privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="caff8-138">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

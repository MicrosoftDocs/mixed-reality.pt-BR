---
title: Histórico de versões de comunicação remota do Holographic
description: Histórico de versão da comunicação remota do Holographic no HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 75e7c276560b4efbbdcbf2ea7579ed5ad7aadb4d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439227"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="14c7f-104">Histórico de versões de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="14c7f-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14c7f-105">Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="14c7f-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="14c7f-106">Versão 2.0.14 (26 de outubro de 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="14c7f-106">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="14c7f-107">Suporte para novas APIs PerceptionDevice (atualização de novembro de 2019 do Windows 10).</span><span class="sxs-lookup"><span data-stu-id="14c7f-107">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="14c7f-108">Correção do problema que impede que eventos de gesto de manutenção sejam disparados por SpatialGestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="14c7f-108">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="14c7f-109">Correção do problema de theading ao usar SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="14c7f-109">Fixed theading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="14c7f-110">Versão 2.0.12 (18 de outubro de 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="14c7f-110">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="14c7f-111">Correção de falha em SpatialGestureRecognizer ao usar NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="14c7f-111">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="14c7f-112">Versão 2.0.10 (10 de outubro de 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="14c7f-112">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="14c7f-113">Correção de falha ao usar o botão de gatilho de controladores VR.</span><span class="sxs-lookup"><span data-stu-id="14c7f-113">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="14c7f-114">A comunicação remota do Holographic não dá suporte total a controladores, apenas o botão de gatilho e o botão do Windows estão funcionando se emparelhados com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="14c7f-114">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="14c7f-115">Versão 2.0.9 (19 de setembro de 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="14c7f-115">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="14c7f-116">Adicionado suporte para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="14c7f-116">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="14c7f-117">Adicionada nova ```IPlayerContext2``` de interface (implementada por ```PlayerContext```) fornecendo os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="14c7f-117">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="14c7f-118">Propriedade [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="14c7f-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="14c7f-119">Adicionado ```Failed_RemoteFrameTooOld``` valor a ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="14c7f-119">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="14c7f-120">Aprimoramentos de estabilidade e confiabilidade</span><span class="sxs-lookup"><span data-stu-id="14c7f-120">Stability and reliability improvements</span></span>

## <span data-ttu-id="14c7f-121">Versão 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="14c7f-121">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="14c7f-122">Correção de falha ao chamar [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) com um [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="14c7f-122">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="14c7f-123">Aprimoramentos de estabilidade e confiabilidade</span><span class="sxs-lookup"><span data-stu-id="14c7f-123">Stability and reliability improvements</span></span>

## <span data-ttu-id="14c7f-124">Versão 2.0.7 (26 de julho de 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="14c7f-124">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="14c7f-125">Primeira versão pública da comunicação remota do Holographic para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="14c7f-125">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="14c7f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14c7f-126">See Also</span></span>
* [<span data-ttu-id="14c7f-127">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="14c7f-127">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="14c7f-128">Escrevendo um aplicativo de host de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="14c7f-128">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="14c7f-129">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="14c7f-129">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="14c7f-130">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="14c7f-130">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="14c7f-131">Política de privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="14c7f-131">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

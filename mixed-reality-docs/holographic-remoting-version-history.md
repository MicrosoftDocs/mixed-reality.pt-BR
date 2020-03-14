---
title: Histórico de versões de comunicação remota do Holographic
description: Histórico de versão da comunicação remota do Holographic no HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 62f54dbcf5327cdd5f13622704684a2cb0606d7d
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375653"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="a6207-104">Histórico de versões de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="a6207-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6207-105">Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a6207-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="a6207-106">Versão 2.1.0 (11 de março de 2020)<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-106">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="a6207-107">Transporte de rede alternado para usar [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span><span class="sxs-lookup"><span data-stu-id="a6207-107">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="a6207-108">As conexões seguras usam o [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) agora.</span><span class="sxs-lookup"><span data-stu-id="a6207-108">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="a6207-109">Observe que o [player de comunicação remota do Holographic](holographic-remoting-player.md) ainda é compatível com todas as versões de comunicação remota do Holographic de versão anterior.</span><span class="sxs-lookup"><span data-stu-id="a6207-109">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="a6207-110">Para se beneficiar do novo transporte de rede, o Holographic Remoting Player e o aplicativo remoto em questão precisam usar a versão 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="a6207-110">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="a6207-111">Adicionado suporte para [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="a6207-111">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <span data-ttu-id="a6207-112">Versão 2.0.20 (2 de fevereiro de 2020)<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-112">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="a6207-113">Correção de vários bugs que levam a falhas.</span><span class="sxs-lookup"><span data-stu-id="a6207-113">Fixed various bugs that lead to crashes.</span></span>

## <span data-ttu-id="a6207-114">Versão 2.0.18 (17 de dezembro de 2019)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-114">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="a6207-115">Adicionado suporte para [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span><span class="sxs-lookup"><span data-stu-id="a6207-115">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="a6207-116">Correção de vários bugs que levam a falhas.</span><span class="sxs-lookup"><span data-stu-id="a6207-116">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="a6207-117">Corrigido o bug em que um retorno de chamada HolographicSpace. CameraAdded era necessário para um HolographicCamera ser aceito e exibido como uma câmera adicionada no HoloraphicFrame.</span><span class="sxs-lookup"><span data-stu-id="a6207-117">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="a6207-118">Versão 2.0.16 (11 de novembro de 2019)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-118">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="a6207-119">Correção de deadlock no controle de código QR.</span><span class="sxs-lookup"><span data-stu-id="a6207-119">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="a6207-120">Correção da exceção unhandeled devido à espera de bloqueio no thread principal.</span><span class="sxs-lookup"><span data-stu-id="a6207-120">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="a6207-121">Versão 2.0.14 (26 de outubro de 2019)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-121">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="a6207-122">Suporte para novas APIs PerceptionDevice (atualização de novembro de 2019 do Windows 10).</span><span class="sxs-lookup"><span data-stu-id="a6207-122">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="a6207-123">Correção do problema que impede que eventos de gesto de manutenção sejam disparados por SpatialGestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="a6207-123">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="a6207-124">Corrigido o problema de Threading ao usar SpatialSurfaceObserver. SetBoundingVolume.</span><span class="sxs-lookup"><span data-stu-id="a6207-124">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="a6207-125">Versão 2.0.12 (18 de outubro de 2019)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-125">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="a6207-126">Correção de falha em SpatialGestureRecognizer ao usar NavigationRail (X/Y/Z).</span><span class="sxs-lookup"><span data-stu-id="a6207-126">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="a6207-127">Versão 2.0.10 (10 de outubro de 2019)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-127">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="a6207-128">Correção de falha ao usar o botão de gatilho de controladores VR.</span><span class="sxs-lookup"><span data-stu-id="a6207-128">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="a6207-129">A comunicação remota do Holographic não dá suporte total a controladores, apenas o botão de gatilho e o botão do Windows estão funcionando se emparelhados com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a6207-129">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="a6207-130">Versão 2.0.9 (19 de setembro de 2019)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-130">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="a6207-131">Adicionado suporte para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span><span class="sxs-lookup"><span data-stu-id="a6207-131">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="a6207-132">Adicionada nova ```IPlayerContext2``` de interface (implementada por ```PlayerContext```) fornecendo os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="a6207-132">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="a6207-133">Propriedade [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .</span><span class="sxs-lookup"><span data-stu-id="a6207-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="a6207-134">Adicionado ```Failed_RemoteFrameTooOld``` valor a ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="a6207-134">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="a6207-135">Aprimoramentos de estabilidade e confiabilidade</span><span class="sxs-lookup"><span data-stu-id="a6207-135">Stability and reliability improvements</span></span>

## <span data-ttu-id="a6207-136">Versão 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-136">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="a6207-137">Correção de falha ao chamar [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) com um [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a6207-137">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="a6207-138">Aprimoramentos de estabilidade e confiabilidade</span><span class="sxs-lookup"><span data-stu-id="a6207-138">Stability and reliability improvements</span></span>

## <span data-ttu-id="a6207-139">Versão 2.0.7 (26 de julho de 2019)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="a6207-139">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="a6207-140">Primeira versão pública da comunicação remota do Holographic para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a6207-140">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6207-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6207-141">See Also</span></span>
* [<span data-ttu-id="a6207-142">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="a6207-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="a6207-143">Escrevendo um aplicativo de host de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="a6207-143">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="a6207-144">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="a6207-144">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="a6207-145">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="a6207-145">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="a6207-146">Política de privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="a6207-146">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

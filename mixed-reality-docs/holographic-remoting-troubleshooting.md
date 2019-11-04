---
title: Solução de problemas e limitações de comunicação remota do Holographic
description: Etapas de solução de problemas para a comunicação remota do Holographic no HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 10/28/2019
ms.topic: article
keywords: Realidade mista do Windows, hologramas, comunicação remota Holographic, renderização remota, renderização de rede, HoloLens, hologramas remotos, solução de problemas, ajuda
ms.openlocfilehash: 7b438d9169c9306e0056655e561c04b62b1662cf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434237"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="24068-104">Solução de problemas de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="24068-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24068-105">Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="24068-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="24068-106">Bibliotecas atenuadas do Spectre não encontradas.</span><span class="sxs-lookup"><span data-stu-id="24068-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="24068-107">Os aplicativos de exemplo de comunicação remota Holographic têm/Qspectre (mitigação de Spectre) habilitada na configuração de versão.</span><span class="sxs-lookup"><span data-stu-id="24068-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="24068-108">Se você receber um erro de vinculador fatal que declara que ' vccorlib. lib ' não pode ser aberto, certifique-se de que sua carga de trabalho do Visual Studio inclui as bibliotecas atenuadas do Spectre.</span><span class="sxs-lookup"><span data-stu-id="24068-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="24068-109">Consulte https://aka.ms/Ofhn4c para mais informações.</span><span class="sxs-lookup"><span data-stu-id="24068-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="24068-110">Limitações</span><span class="sxs-lookup"><span data-stu-id="24068-110">Limitations</span></span>

<span data-ttu-id="24068-111">Atualmente, **não** há suporte para as seguintes APIs ao usar a comunicação remota do Holographic para o HoloLens 2 e gerará um erro de ```ERROR_NOT_SUPPORTED```, salvo indicação em contrário:</span><span class="sxs-lookup"><span data-stu-id="24068-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="24068-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="24068-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="24068-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="24068-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="24068-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="24068-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="24068-115">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="24068-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="24068-116">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="24068-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="24068-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="24068-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="24068-118">Não falha, mas o buffer de profundidade não será remoto.</span><span class="sxs-lookup"><span data-stu-id="24068-118">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="24068-119">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="24068-119">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="24068-120">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="24068-120">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="24068-121">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="24068-121">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="24068-122">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="24068-122">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="24068-123">SpatialLocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="24068-123">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="24068-124">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="24068-124">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="24068-125">SpatialLocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="24068-125">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="24068-126">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="24068-126">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="24068-127">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="24068-127">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="24068-128">SpatialStageFrameOfReference. Current</span><span class="sxs-lookup"><span data-stu-id="24068-128">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="24068-129">Sempre retorna ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="24068-129">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="24068-130">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="24068-130">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="24068-131">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="24068-131">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="24068-132">SpatialAnchorExporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="24068-132">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="24068-133">Com suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="24068-133">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="24068-134">Nas versões anteriores, sempre retorna ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="24068-134">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="24068-135">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="24068-135">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="24068-136">Com suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="24068-136">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="24068-137">Em versões anteriores, a operação assíncrona sempre foi concluída com ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="24068-137">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="24068-138">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="24068-138">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="24068-139">A operação assíncrona sempre é concluída com ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="24068-139">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="24068-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="24068-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="24068-141">A operação assíncrona sempre é concluída com ```false```.</span><span class="sxs-lookup"><span data-stu-id="24068-141">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="24068-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="24068-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="24068-143">A operação assíncrona sempre é concluída com ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="24068-143">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="24068-144">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="24068-144">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="24068-145">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="24068-145">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="24068-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="24068-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="24068-147">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="24068-147">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="24068-148">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="24068-148">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="24068-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="24068-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="24068-150">SpatialInteractionSource. Controller</span><span class="sxs-lookup"><span data-stu-id="24068-150">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="24068-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24068-151">See Also</span></span>
* [<span data-ttu-id="24068-152">Histórico de versões de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="24068-152">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="24068-153">Escrevendo um aplicativo de host de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="24068-153">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="24068-154">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="24068-154">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="24068-155">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="24068-155">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="24068-156">Política de privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="24068-156">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

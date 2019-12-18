---
title: Solução de problemas e limitações de comunicação remota do Holographic
description: Etapas de solução de problemas para a comunicação remota do Holographic no HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 12/17/2019
ms.topic: article
keywords: Realidade mista do Windows, hologramas, comunicação remota Holographic, renderização remota, renderização de rede, HoloLens, hologramas remotos, solução de problemas, ajuda
ms.openlocfilehash: 05333c8911010945a543cf603b9925eb30c841db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181966"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="6fb51-104">Solução de problemas de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="6fb51-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fb51-105">Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6fb51-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="6fb51-106">Bibliotecas atenuadas do Spectre não encontradas.</span><span class="sxs-lookup"><span data-stu-id="6fb51-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="6fb51-107">Os aplicativos de exemplo de comunicação remota Holographic têm/Qspectre (mitigação de Spectre) habilitada na configuração de versão.</span><span class="sxs-lookup"><span data-stu-id="6fb51-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="6fb51-108">Se você receber um erro de vinculador fatal que declara que ' vccorlib. lib ' não pode ser aberto, certifique-se de que sua carga de trabalho do Visual Studio inclui as bibliotecas atenuadas do Spectre.</span><span class="sxs-lookup"><span data-stu-id="6fb51-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="6fb51-109">Consulte https://aka.ms/Ofhn4c para mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fb51-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="6fb51-110">Limitações</span><span class="sxs-lookup"><span data-stu-id="6fb51-110">Limitations</span></span>

<span data-ttu-id="6fb51-111">Atualmente, **não** há suporte para as seguintes APIs ao usar a comunicação remota do Holographic para o HoloLens 2 e gerará um erro de ```ERROR_NOT_SUPPORTED```, salvo indicação em contrário:</span><span class="sxs-lookup"><span data-stu-id="6fb51-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="6fb51-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="6fb51-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="6fb51-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fb51-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="6fb51-114">Com suporte a partir da versão [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="6fb51-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="6fb51-115">Em versões anteriores sempre gera um erro.</span><span class="sxs-lookup"><span data-stu-id="6fb51-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="6fb51-116">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="6fb51-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="6fb51-117">Não falha, mas o tamanho do destino de renderização não será alterado.</span><span class="sxs-lookup"><span data-stu-id="6fb51-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="6fb51-118">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="6fb51-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="6fb51-119">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="6fb51-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="6fb51-120">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="6fb51-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="6fb51-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="6fb51-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="6fb51-122">Não falha, mas o buffer de profundidade não será remoto.</span><span class="sxs-lookup"><span data-stu-id="6fb51-122">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="6fb51-123">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fb51-123">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="6fb51-124">Consultar HolographicViewConfigurationKind. PhotoVideoCamera sempre retornará um ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="6fb51-124">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="6fb51-125">Com suporte a partir da versão [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span><span class="sxs-lookup"><span data-stu-id="6fb51-125">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="6fb51-126">Em versões anteriores sempre gera um erro.</span><span class="sxs-lookup"><span data-stu-id="6fb51-126">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="6fb51-127">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="6fb51-127">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="6fb51-128">HolographicDisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="6fb51-128">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="6fb51-129">Relatará um erro se chamado antes de uma conexão ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="6fb51-129">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="6fb51-130">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="6fb51-130">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="6fb51-131">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="6fb51-131">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="6fb51-132">SpatialLocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="6fb51-132">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="6fb51-133">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="6fb51-133">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="6fb51-134">SpatialLocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="6fb51-134">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="6fb51-135">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="6fb51-135">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="6fb51-136">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="6fb51-136">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="6fb51-137">SpatialStageFrameOfReference. Current</span><span class="sxs-lookup"><span data-stu-id="6fb51-137">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="6fb51-138">Retorna sempre ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="6fb51-138">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="6fb51-139">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="6fb51-139">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="6fb51-140">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="6fb51-140">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="6fb51-141">SpatialAnchorExporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="6fb51-141">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="6fb51-142">Com suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="6fb51-142">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="6fb51-143">Nas versões anteriores, sempre retorna ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="6fb51-143">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="6fb51-144">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="6fb51-144">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="6fb51-145">Com suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="6fb51-145">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="6fb51-146">Em versões anteriores, a operação assíncrona sempre foi concluída com ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="6fb51-146">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="6fb51-147">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="6fb51-147">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="6fb51-148">A operação assíncrona sempre é concluída com ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span><span class="sxs-lookup"><span data-stu-id="6fb51-148">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="6fb51-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="6fb51-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="6fb51-150">A operação assíncrona sempre é concluída com ```false```.</span><span class="sxs-lookup"><span data-stu-id="6fb51-150">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="6fb51-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="6fb51-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="6fb51-152">A operação assíncrona sempre é concluída com ```nullptr```.</span><span class="sxs-lookup"><span data-stu-id="6fb51-152">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="6fb51-153">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="6fb51-153">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="6fb51-154">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="6fb51-154">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="6fb51-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="6fb51-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="6fb51-156">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="6fb51-156">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="6fb51-157">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="6fb51-157">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="6fb51-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="6fb51-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="6fb51-159">SpatialInteractionSource. Controller</span><span class="sxs-lookup"><span data-stu-id="6fb51-159">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="6fb51-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fb51-160">See Also</span></span>
* [<span data-ttu-id="6fb51-161">Histórico de versões de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="6fb51-161">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="6fb51-162">Escrevendo um aplicativo de host de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="6fb51-162">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="6fb51-163">Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado</span><span class="sxs-lookup"><span data-stu-id="6fb51-163">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="6fb51-164">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="6fb51-164">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="6fb51-165">Política de Privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="6fb51-165">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

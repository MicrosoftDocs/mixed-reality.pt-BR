---
title: Solução de problemas e limitações de comunicação remota do Holographic
description: Etapas de solução de problemas para a comunicação remota do Holographic no HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, comunicação remota Holographic, renderização remota, renderização de rede, HoloLens, hologramas remotos, solução de problemas, ajuda
ms.openlocfilehash: 79650ceab5d0125a8a06c776a59a45a78d0aa20c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061109"
---
# <a name="holographic-remoting-troubleshooting"></a>Solução de problemas de comunicação remota do Holographic

> [!IMPORTANT]
> Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Bibliotecas atenuadas do Spectre não encontradas.

Os aplicativos de exemplo de comunicação remota Holographic têm/Qspectre (mitigação de Spectre) habilitada na configuração de versão.

Se você receber um erro de vinculador fatal que declara que ' vccorlib. lib ' não pode ser aberto, certifique-se de que sua carga de trabalho do Visual Studio inclui as bibliotecas atenuadas do Spectre. Consulte https://aka.ms/Ofhn4c para obter mais informações.

## <a name="speech"></a>Fala

O player de comunicação remota do Holographic dá suporte a uma sobreposição de diagnóstico que pode ser habilitada dizendo ```Enable Diagnostics``` e desabilitada dizendo ```Disable Diagnostics``` . Se você tiver problemas com esses comandos de voz, também poderá iniciar o player de comunicação remota do Holographic por meio de um navegador da Web usando ```ms-holographic-remoting:?stats``` como uma URL.

## <a name="limitations"></a>Limitações

Atualmente, **não** há suporte para as seguintes APIs ao usar a comunicação remota do Holographic para o HoloLens 2 e gerará um ```ERROR_NOT_SUPPORTED``` erro, salvo indicação em contrário:

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Com suporte a partir da versão [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Em versões anteriores sempre gera um erro.
* [HolographicCamera.IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Não falha, mas o tamanho do destino de renderização não será alterado.
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Não falha, mas o buffer de profundidade não será remoto.
  - Com suporte a partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Consultar HolographicViewConfigurationKind. PhotoVideoCamera sempre retornará um ```nullptr``` .
  - Com suporte a partir da versão [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - Em versões anteriores sempre gera um erro.
* [HolographicSpace.CreateFramePresentationMonitor](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay. GetDefault](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Relatará um erro se chamado antes de uma conexão ser estabelecida.


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Com suporte a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - Nas versões anteriores, sempre retorna ```nullptr``` .
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Com suporte a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [SpatialAnchor.RemovedByUser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Com suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - Nas versões anteriores, sempre retorna ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Com suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - Em versões anteriores, a operação assíncrona sempre foi concluída com ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - A operação assíncrona sempre é concluída com ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - A operação assíncrona sempre é concluída com ```false``` .
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - A operação assíncrona sempre é concluída com ```nullptr``` .

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Com suporte a partir da versão [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Consulte Também
* [Histórico de versões de comunicação remota do Holographic](holographic-remoting-version-history.md)
* [Como criar um aplicativo remoto de comunicação remota holográfica](holographic-remoting-create-host.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

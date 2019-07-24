---
title: Objetos nativos da realidade misturada no Unity
description: Obtenha acesso aos objetos Holographic nativos subjacentes no Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, realidade misturada, nativa, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942092"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="77754-104">Objetos nativos da realidade misturada no Unity</span><span class="sxs-lookup"><span data-stu-id="77754-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="77754-105">[Obter um HolographicSpace](getting-a-holographicspace.md) é o que todo aplicativo de realidade misturada faz antes de começar a receber dados de câmera e renderizar quadros.</span><span class="sxs-lookup"><span data-stu-id="77754-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="77754-106">No Unity, o mecanismo cuida dessas etapas para você, manipulando objetos Holographic e atualizações internamente como parte de seu loop de processamento.</span><span class="sxs-lookup"><span data-stu-id="77754-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="77754-107">No entanto, em cenários avançados, talvez seja necessário obter acesso aos objetos nativos subjacentes, como o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>atual.</span><span class="sxs-lookup"><span data-stu-id="77754-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="77754-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> é o que fornece acesso a esses objetos nativos.</span><span class="sxs-lookup"><span data-stu-id="77754-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="77754-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="77754-109">XRDevice</span></span> 

<span data-ttu-id="77754-110">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="77754-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="77754-111">**Escreva** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="77754-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="77754-112">O tipo *XRDevice* permite que você obtenha acesso a objetos nativos subjacentes usando o método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="77754-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="77754-113">O que GetNativePtr retorna varia entre diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="77754-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="77754-114">No Plataforma Universal do Windows, ao direcionar o SDK do Windows Mixed Reality XR, XRDevice. GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="77754-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
<span data-ttu-id="77754-115">Você pode convertê-lo em HolographicFrameNativeData usando o método Marshal. PtrToStructure:</span><span class="sxs-lookup"><span data-stu-id="77754-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="77754-116">***IHolographicCameraPtr** é uma matriz de IntPtr empacotada como UnmanagedType. ByValArray com um comprimento igual a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="77754-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="77754-117">Usando HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="77754-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="77754-118">Alterar o estado dos objetos nativos recebidos por meio de HolographicFrameNativeData pode causar comportamentos imprevisíveis e renderizar artefatos, especialmente se o Unity também tiver motivos sobre o mesmo estado.</span><span class="sxs-lookup"><span data-stu-id="77754-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="77754-119">Por exemplo, você não deve chamar HolographicFrame. UpdateCurrentPrediction ou a previsão de pose que o Unity renderiza com esse quadro estará fora de sincronia com a pose esperada pelo Windows, o que reduzirá a [estabilidade do holograma](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="77754-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="77754-120">Você pode usar dados do HolographicFrameNativeData quando o acesso a interfaces nativas é necessário para fins de processamento ou depuração, em seus C# plug-ins nativos ou código.</span><span class="sxs-lookup"><span data-stu-id="77754-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="77754-121">Aqui está um exemplo de como você pode usar HolographicFrameNativeData para obter a previsão do quadro atual para o tempo de Photon.</span><span class="sxs-lookup"><span data-stu-id="77754-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a><span data-ttu-id="77754-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77754-122">See Also</span></span>
* <span data-ttu-id="77754-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="77754-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="77754-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="77754-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="77754-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="77754-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="77754-126">Como renderizar no DirectX</span><span class="sxs-lookup"><span data-stu-id="77754-126">Rendering in DirectX</span></span>](rendering-in-directx.md)

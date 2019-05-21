---
title: Objetos de nativo de realidade mistos no Unity
description: Obtenha acesso a objetos nativos holográfico subjacentes no Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, misturadas realidade, nativo, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942092"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="37d19-104">Objetos de nativo de realidade mistos no Unity</span><span class="sxs-lookup"><span data-stu-id="37d19-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="37d19-105">[Obtendo um HolographicSpace](getting-a-holographicspace.md) é o que cada aplicativo faz antes de começar a receber dados da câmera e a renderização de realidade misturada quadros.</span><span class="sxs-lookup"><span data-stu-id="37d19-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="37d19-106">No Unity, o mecanismo cuida dessas etapas para você, manipulando objetos holográfico e atualiza internamente como parte de seu loop de renderização.</span><span class="sxs-lookup"><span data-stu-id="37d19-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="37d19-107">No entanto, em cenários avançados talvez seja necessário obter acesso aos objetos subjacentes nativos, como o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e atuais <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span><span class="sxs-lookup"><span data-stu-id="37d19-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="37d19-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> é o que fornece acesso a esses objetos nativos.</span><span class="sxs-lookup"><span data-stu-id="37d19-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="37d19-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="37d19-109">XRDevice</span></span> 

<span data-ttu-id="37d19-110">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="37d19-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="37d19-111">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="37d19-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="37d19-112">O *XRDevice* tipo permite que você obtenha acesso aos objetos nativos subjacentes usando a <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> método.</span><span class="sxs-lookup"><span data-stu-id="37d19-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="37d19-113">O que retorna GetNativePtr varia entre diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="37d19-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="37d19-114">Na plataforma Universal do Windows, quando direcionados ao SDK de XR realidade mista do Windows, o XRDevice.GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="37d19-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="37d19-115">Você pode convertê-la para HolographicFrameNativeData usando Marshal. PtrToStructure método:</span><span class="sxs-lookup"><span data-stu-id="37d19-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="37d19-116">***IHolographicCameraPtr** é uma matriz de IntPtr o marshaling realizado como UnmanagedType. ByValArray com um comprimento igual a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="37d19-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="37d19-117">Usando HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="37d19-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="37d19-118">Alterando o estado dos objetos nativos recebidos por meio de HolographicFrameNativeData pode causar um comportamento imprevisível e artefatos de renderização, especialmente se o Unity também questões sobre esse mesmo estado.</span><span class="sxs-lookup"><span data-stu-id="37d19-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="37d19-119">Por exemplo, você não deve chamar HolographicFrame.UpdateCurrentPrediction, caso contrário, a previsão de pose que renderiza o Unity com o quadro será fora de sincronia com a pose Windows está esperando, o que reduzirá [estabilidade holograma](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="37d19-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="37d19-120">Você pode usar dados de HolographicFrameNativeData quando for necessário para renderização ou para fins de depuração, no seu plug-ins nativo acesso às interfaces nativas ou C# código.</span><span class="sxs-lookup"><span data-stu-id="37d19-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="37d19-121">Aqui está um exemplo de como você pode usar HolographicFrameNativeData para obter a previsão do quadro atual para o tempo de photon.</span><span class="sxs-lookup"><span data-stu-id="37d19-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="37d19-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37d19-122">See Also</span></span>
* <span data-ttu-id="37d19-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="37d19-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="37d19-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="37d19-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="37d19-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="37d19-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="37d19-126">Como renderizar no DirectX</span><span class="sxs-lookup"><span data-stu-id="37d19-126">Rendering in DirectX</span></span>](rendering-in-directx.md)

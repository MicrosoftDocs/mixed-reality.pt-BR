---
title: Objetos nativos da realidade misturada no Unity
description: Obtenha acesso aos objetos Holographic nativos subjacentes no Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, realidade misturada, nativa, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 975775f64a19fe5fff4bc395a3e954cbf529dfa9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437336"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="2a83a-104">Objetos nativos da realidade misturada no Unity</span><span class="sxs-lookup"><span data-stu-id="2a83a-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="2a83a-105">[Obter um HolographicSpace](getting-a-holographicspace.md) é o que todo aplicativo de realidade misturada faz antes de começar a receber dados de câmera e renderizar quadros.</span><span class="sxs-lookup"><span data-stu-id="2a83a-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="2a83a-106">No Unity, o mecanismo cuida dessas etapas para você, manipulando objetos Holographic e atualizações internamente como parte de seu loop de processamento.</span><span class="sxs-lookup"><span data-stu-id="2a83a-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="2a83a-107">No entanto, em cenários avançados, talvez seja necessário obter acesso aos objetos nativos subjacentes, como o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>atual.</span><span class="sxs-lookup"><span data-stu-id="2a83a-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="2a83a-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> é o que fornece acesso a esses objetos nativos.</span><span class="sxs-lookup"><span data-stu-id="2a83a-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="2a83a-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="2a83a-109">XRDevice</span></span> 

<span data-ttu-id="2a83a-110">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="2a83a-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="2a83a-111">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="2a83a-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="2a83a-112">O tipo *XRDevice* permite que você obtenha acesso a objetos nativos subjacentes usando o método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="2a83a-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="2a83a-113">O que GetNativePtr retorna varia entre diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="2a83a-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="2a83a-114">No Plataforma Universal do Windows, ao direcionar o SDK do Windows Mixed Reality XR, XRDevice. GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="2a83a-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="2a83a-115">Você pode convertê-lo em HolographicFrameNativeData usando o método Marshal. PtrToStructure:</span><span class="sxs-lookup"><span data-stu-id="2a83a-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="2a83a-116">***IHolographicCameraPtr** é uma matriz de IntPtr empacotada como UnmanagedType. ByValArray com um comprimento igual a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="2a83a-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="2a83a-117">Desempacotamento de ponteiros nativos</span><span class="sxs-lookup"><span data-stu-id="2a83a-117">Unmarshaling native pointers</span></span>

<span data-ttu-id="2a83a-118">Se você estiver usando [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) , poderá construir um objeto gerenciado a partir de um ponteiro nativo usando o método `FromNativePtr()`:</span><span class="sxs-lookup"><span data-stu-id="2a83a-118">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

<span data-ttu-id="2a83a-119">Caso contrário, use `Marshal.GetObjectForIUnknown()` e converta para o tipo desejado:</span><span class="sxs-lookup"><span data-stu-id="2a83a-119">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the desired type:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="2a83a-120">Convertendo entre sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="2a83a-120">Converting between coordinate systems</span></span>

<span data-ttu-id="2a83a-121">O Unity usa um sistema de coordenadas à esquerda, enquanto as APIs de percepção do Windows usam sistemas de coordenadas à mão.</span><span class="sxs-lookup"><span data-stu-id="2a83a-121">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="2a83a-122">Para converter entre essas duas convenções, você pode usar os seguintes auxiliares:</span><span class="sxs-lookup"><span data-stu-id="2a83a-122">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="2a83a-123">Usando dados nativos do HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="2a83a-123">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="2a83a-124">Alterar o estado dos objetos nativos recebidos por meio de HolographicFrameNativeData pode causar comportamentos imprevisíveis e renderizar artefatos, especialmente se o Unity também tiver motivos sobre o mesmo estado.</span><span class="sxs-lookup"><span data-stu-id="2a83a-124">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="2a83a-125">Por exemplo, você não deve chamar HolographicFrame. UpdateCurrentPrediction ou a previsão de pose que o Unity renderiza com esse quadro estará fora de sincronia com a pose esperada pelo Windows, o que reduzirá a [estabilidade do holograma](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="2a83a-125">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="2a83a-126">Você pode usar dados do HolographicFrameNativeData quando o acesso a interfaces nativas é necessário para fins de processamento ou depuração, em seus C# plug-ins nativos ou código.</span><span class="sxs-lookup"><span data-stu-id="2a83a-126">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="2a83a-127">Aqui está um exemplo de como você pode usar HolographicFrameNativeData para obter a previsão do quadro atual para o tempo de Photon.</span><span class="sxs-lookup"><span data-stu-id="2a83a-127">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="2a83a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a83a-128">See Also</span></span>
* [<span data-ttu-id="2a83a-129">Como usar o namespace do Windows com aplicativos Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="2a83a-129">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="2a83a-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="2a83a-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="2a83a-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="2a83a-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="2a83a-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="2a83a-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="2a83a-133">Como renderizar no DirectX</span><span class="sxs-lookup"><span data-stu-id="2a83a-133">Rendering in DirectX</span></span>](rendering-in-directx.md)

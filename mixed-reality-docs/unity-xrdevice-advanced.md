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
# <a name="mixed-reality-native-objects-in-unity"></a>Objetos nativos da realidade misturada no Unity

[Obter um HolographicSpace](getting-a-holographicspace.md) é o que todo aplicativo de realidade misturada faz antes de começar a receber dados de câmera e renderizar quadros. No Unity, o mecanismo cuida dessas etapas para você, manipulando objetos Holographic e atualizações internamente como parte de seu loop de processamento.

No entanto, em cenários avançados, talvez seja necessário obter acesso aos objetos nativos subjacentes, como o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>atual. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> é o que fornece acesso a esses objetos nativos.

## <a name="xrdevice"></a>XRDevice 

**Namespace:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

O tipo *XRDevice* permite que você obtenha acesso a objetos nativos subjacentes usando o método <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . O que GetNativePtr retorna varia entre diferentes plataformas. No Plataforma Universal do Windows, ao direcionar o SDK do Windows Mixed Reality XR, XRDevice. GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura: 

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
Você pode convertê-lo em HolographicFrameNativeData usando o método Marshal. PtrToStructure:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** é uma matriz de IntPtr empacotada como UnmanagedType. ByValArray com um comprimento igual a MaxNumberOfCameras* 

### <a name="unmarshaling-native-pointers"></a>Desempacotamento de ponteiros nativos

Se você estiver usando [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) , poderá construir um objeto gerenciado a partir de um ponteiro nativo usando o método `FromNativePtr()`:

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

Caso contrário, use `Marshal.GetObjectForIUnknown()` e converta para o tipo desejado:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a>Convertendo entre sistemas de coordenadas

O Unity usa um sistema de coordenadas à esquerda, enquanto as APIs de percepção do Windows usam sistemas de coordenadas à mão. Para converter entre essas duas convenções, você pode usar os seguintes auxiliares:

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

### <a name="using-holographicframe-native-data"></a>Usando dados nativos do HolographicFrame

> [!NOTE]
> Alterar o estado dos objetos nativos recebidos por meio de HolographicFrameNativeData pode causar comportamentos imprevisíveis e renderizar artefatos, especialmente se o Unity também tiver motivos sobre o mesmo estado.  Por exemplo, você não deve chamar HolographicFrame. UpdateCurrentPrediction ou a previsão de pose que o Unity renderiza com esse quadro estará fora de sincronia com a pose esperada pelo Windows, o que reduzirá a [estabilidade do holograma](hologram-stability.md).

Você pode usar dados do HolographicFrameNativeData quando o acesso a interfaces nativas é necessário para fins de processamento ou depuração, em seus C# plug-ins nativos ou código. 

Aqui está um exemplo de como você pode usar HolographicFrameNativeData para obter a previsão do quadro atual para o tempo de Photon. 
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

## <a name="see-also"></a>Consulte também
* [Como usar o namespace do Windows com aplicativos Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Como renderizar no DirectX](rendering-in-directx.md)

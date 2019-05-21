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
# <a name="mixed-reality-native-objects-in-unity"></a>Objetos de nativo de realidade mistos no Unity

[Obtendo um HolographicSpace](getting-a-holographicspace.md) é o que cada aplicativo faz antes de começar a receber dados da câmera e a renderização de realidade misturada quadros. No Unity, o mecanismo cuida dessas etapas para você, manipulando objetos holográfico e atualiza internamente como parte de seu loop de renderização.

No entanto, em cenários avançados talvez seja necessário obter acesso aos objetos subjacentes nativos, como o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e atuais <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> é o que fornece acesso a esses objetos nativos.

## <a name="xrdevice"></a>XRDevice 

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

O *XRDevice* tipo permite que você obtenha acesso aos objetos nativos subjacentes usando a <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> método. O que retorna GetNativePtr varia entre diferentes plataformas. Na plataforma Universal do Windows, quando direcionados ao SDK de XR realidade mista do Windows, o XRDevice.GetNativePtr retorna um ponteiro (IntPtr) para a seguinte estrutura: 

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
Você pode convertê-la para HolographicFrameNativeData usando Marshal. PtrToStructure método:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** é uma matriz de IntPtr o marshaling realizado como UnmanagedType. ByValArray com um comprimento igual a MaxNumberOfCameras* 


### <a name="using-holographicframenativedata"></a>Usando HolographicFrameNativeData

> [!NOTE]
> Alterando o estado dos objetos nativos recebidos por meio de HolographicFrameNativeData pode causar um comportamento imprevisível e artefatos de renderização, especialmente se o Unity também questões sobre esse mesmo estado.  Por exemplo, você não deve chamar HolographicFrame.UpdateCurrentPrediction, caso contrário, a previsão de pose que renderiza o Unity com o quadro será fora de sincronia com a pose Windows está esperando, o que reduzirá [estabilidade holograma](hologram-stability.md).

Você pode usar dados de HolographicFrameNativeData quando for necessário para renderização ou para fins de depuração, no seu plug-ins nativo acesso às interfaces nativas ou C# código. 

Aqui está um exemplo de como você pode usar HolographicFrameNativeData para obter a previsão do quadro atual para o tempo de photon. 
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
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Como renderizar no DirectX](rendering-in-directx.md)

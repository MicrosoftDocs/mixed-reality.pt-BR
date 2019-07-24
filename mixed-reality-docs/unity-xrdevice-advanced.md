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
# <a name="mixed-reality-native-objects-in-unity"></a>Objetos nativos da realidade misturada no Unity

[Obter um HolographicSpace](getting-a-holographicspace.md) é o que todo aplicativo de realidade misturada faz antes de começar a receber dados de câmera e renderizar quadros. No Unity, o mecanismo cuida dessas etapas para você, manipulando objetos Holographic e atualizações internamente como parte de seu loop de processamento.

No entanto, em cenários avançados, talvez seja necessário obter acesso aos objetos nativos subjacentes, como o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>atual. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> é o que fornece acesso a esses objetos nativos.

## <a name="xrdevice"></a>XRDevice 

**Namespace:** *UnityEngine. XR*<br>
**Escreva** *XRDevice*

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


### <a name="using-holographicframenativedata"></a>Usando HolographicFrameNativeData

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
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Como renderizar no DirectX](rendering-in-directx.md)

---
title: Câmera localizável no DirectX
description: Explica como usar a câmera de ponto de vista (POV) em um aplicativo do HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, câmera localizável, ponto de vista, ângulo de visão, unporoject, Media Foundation, MF, coletor personalizado, Walkthrough, código de exemplo
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516862"
---
# <a name="locatable-camera-in-directx"></a>Câmera localizável no DirectX

Este tópico descreve como configurar um pipeline de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) para acessar a [câmera](locatable-camera.md) em um aplicativo DirectX, incluindo os metadados do quadro que permitirão que você localize as imagens produzidas no mundo real.

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows Media Capture e desenvolvimento de Media Foundation: IMFAttributes

Cada quadro [de imagem inclui um sistema de coordenadas](locatable-camera.md#images-with-coordinate-systems) , bem como duas transformações importantes. A transformação "exibição" mapeia do sistema de coordenadas fornecido para a câmera e a "projeção" mapeia da câmera para pixels na imagem. O sistema de coordenadas e as duas transformações são inseridos como metadados em cada quadro de imagem via [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)do Media Foundation.

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>Exemplo de uso de ler atributos com o coletor personalizado MF e fazer projeção

Em seu fluxo de coletor MF personalizado ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), você receberá [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) com atributos de exemplo:

O MediaExtensions a seguir deve ser definido para o código baseado em WinRT:

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

Você não pode acessar esses atributos de APIs do WinRT, mas requer a implementação da extensão de mídia de [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (para efeito) ou [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) e [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (para o coletor personalizado). Quando você processa o exemplo nessa extensão em [IMFTransform::P rocessinput ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::P rocessoutput ()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) ou [IMFStreamSink::P rocesssample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), você pode consultar atributos como este exemplo.

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

Para acessar a textura da câmera, você precisará do mesmo dispositivo D3D que cria a textura da moldura da câmera. Este dispositivo D3D está em [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) no pipeline de captura. Para obter o Gerenciador de dispositivos DXGI da captura de mídia, você pode usar as interfaces [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) e [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) .

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

Você também pode habilitar a entrada de mouse e teclado como métodos de entrada opcionais para seu aplicativo do Windows Mixed Reality. Isso também pode ser um ótimo recurso de depuração para dispositivos como o HoloLens, e pode ser desejável para entrada do usuário em aplicativos de realidade misturados em execução em headsets de imersão conectados a PCs.

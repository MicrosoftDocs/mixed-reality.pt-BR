---
title: Histórico de versões de comunicação remota do Holographic
description: Histórico de versão da comunicação remota do Holographic no HoloLens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: 62f54dbcf5327cdd5f13622704684a2cb0606d7d
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375653"
---
# <a name="holographic-remoting-version-history"></a>Histórico de versões de comunicação remota do Holographic

> [!IMPORTANT]
> Estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

## Versão 2.1.0 (11 de março de 2020)<a name="v2.1.0"></a>
* Transporte de rede alternado para usar [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP. As conexões seguras usam o [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) agora. Observe que o [player de comunicação remota do Holographic](holographic-remoting-player.md) ainda é compatível com todas as versões de comunicação remota do Holographic de versão anterior. Para se beneficiar do novo transporte de rede, o Holographic Remoting Player e o aplicativo remoto em questão precisam usar a versão 2.1.0.
* Adicionado suporte para [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## Versão 2.0.20 (2 de fevereiro de 2020)<a name="v2.0.20"></a>
* Correção de vários bugs que levam a falhas.

## Versão 2.0.18 (17 de dezembro de 2019)<a name="v2.0.18"></a>
* Adicionado suporte para [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Correção de vários bugs que levam a falhas.
* Corrigido o bug em que um retorno de chamada HolographicSpace. CameraAdded era necessário para um HolographicCamera ser aceito e exibido como uma câmera adicionada no HoloraphicFrame.

## Versão 2.0.16 (11 de novembro de 2019)<a name="2.0.16"></a>
* Correção de deadlock no controle de código QR.
* Correção da exceção unhandeled devido à espera de bloqueio no thread principal.

## Versão 2.0.14 (26 de outubro de 2019)<a name="v2.0.14"></a>
* Suporte para novas APIs PerceptionDevice (atualização de novembro de 2019 do Windows 10).
* Correção do problema que impede que eventos de gesto de manutenção sejam disparados por SpatialGestureRecognizer.
* Corrigido o problema de Threading ao usar SpatialSurfaceObserver. SetBoundingVolume.

## Versão 2.0.12 (18 de outubro de 2019)<a name="v2.0.12"></a>
* Correção de falha em SpatialGestureRecognizer ao usar NavigationRail (X/Y/Z).

## Versão 2.0.10 (10 de outubro de 2019)<a name="v2.0.10"></a>
* Correção de falha ao usar o botão de gatilho de controladores VR. A comunicação remota do Holographic não dá suporte total a controladores, apenas o botão de gatilho e o botão do Windows estão funcionando se emparelhados com o HoloLens 2.

## Versão 2.0.9 (19 de setembro de 2019)<a name="v2.0.9"></a>
* Adicionado suporte para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Adicionada nova ```IPlayerContext2``` de interface (implementada por ```PlayerContext```) fornecendo os seguintes membros:
  - Propriedade [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* Adicionado ```Failed_RemoteFrameTooOld``` valor a ```BlitResult```
* Aprimoramentos de estabilidade e confiabilidade

## Versão 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a>

* Correção de falha ao chamar [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) com um [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como parâmetro.
* Aprimoramentos de estabilidade e confiabilidade

## Versão 2.0.7 (26 de julho de 2019)<a name="v2.0.7"></a>

* Primeira versão pública da comunicação remota do Holographic para o HoloLens 2.

## <a name="see-also"></a>Consulte também
* [Escrevendo um aplicativo de player de comunicação remota do Holographic personalizado](holographic-remoting-create-player.md)
* [Escrevendo um aplicativo de host de comunicação remota do Holographic](holographic-remoting-create-host.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

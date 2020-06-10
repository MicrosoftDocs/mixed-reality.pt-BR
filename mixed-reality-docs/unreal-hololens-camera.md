---
title: Câmera de foto/vídeo do HoloLens no Unreal
description: Guia para usar a câmera de foto/vídeo do HoloLens no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, PV camera, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451331"
---
# <a name="hololens-photovideo-camera-in-unreal"></a>Câmera de foto/vídeo do HoloLens no Unreal

O HoloLens tem uma câmera de foto/vídeo (PV) que é usada para a MRC (captura de realidade misturada) e pode também ser usada por um aplicativo para acessar elementos visuais do mundo real.

## <a name="render-from-the-pv-camera-for-mrc"></a>Renderizar da câmera de PV para MRC

> [!NOTE]
> Isso requer o **Unreal Engine 4.25** ou posterior.

O sistema e os gravadores personalizados de MRC criam capturas de realidade misturada combinando a câmera de PV com hologramas renderizados pelo aplicativo de imersão.

Por padrão, a captura de realidade misturada usa a saída holográfica do olho direito. Se um aplicativo de imersão optar por [renderizar da câmera de PV](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), isso será usado em vez do padrão citado acima. Isso melhora o mapeamento entre o mundo real e os hologramas no vídeo do MRC.

Para aceitar a renderização da câmera de PV:

1. Chamar **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**
    * Use os valores de **Tamanho X** e **Tamanho Y** para definir as dimensões do vídeo.

![Terceira câmera](images/unreal-camera-3rd.PNG)

Em seguida, o Unreal lidará com as solicitações da MRC para renderizar da perspectiva da câmera de PV.

> [!NOTE]
> Somente quando a [Captura de Realidade Misturada](mixed-reality-capture.md) for disparada, o aplicativo será solicitado a renderizar partindo da perspectiva da câmera de foto/vídeo.

## <a name="using-the-pv-camera"></a>Usando a câmera de PV

A textura de webcam pode ser recuperada no jogo em runtime, mas precisa ser habilitada no menu **Editar > Configurações de Projeto** do editor:
1. Acesse **Plataformas > HoloLens > Funcionalidades** e marque **Webcam**.
    * Use a função **StartCameraCapture** para usar a webcam em runtime e a função **StopCameraCapture** para interromper a gravação.

![Iniciar/interromper câmera](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Renderização de uma imagem
Para renderizar a imagem da câmera:
1. Crie uma instância de material dinâmico com base em um material no projeto, nomeado **PVCamMat** na captura de tela abaixo.  
2. Defina a instância de material dinâmico para uma variável de **Referência de Objeto Dinâmico da Instância de Material**.  
3. Defina o material do objeto na cena que renderizará o feed da câmera para essa nova instância de material dinâmico.
    * Inicie um temporizador que será usado para associar a imagem da câmera ao material. 

![Renderização da câmera](images/unreal-camera-render.PNG)

4. Crie uma função para esse temporizador (neste caso, **MaterialTimer**) e chame **GetARCameraImage** para obter a textura da webcam.  
5. Se a textura for válida, defina um parâmetro de textura no sombreador para a imagem.  Caso contrário, inicie o temporizador de material novamente. 

![Textura da câmera](images/unreal-camera-texture.PNG)

5. Verifique se o material tem um parâmetro correspondente ao nome em **SetTextureParameterValue** que esteja associado a uma entrada de cor. Sem isso, a imagem da câmera não pode ser exibida corretamente.

![Textura da câmera](images/unreal-camera-material.PNG)

## <a name="see-also"></a>Veja também
* [Câmera localizável](locatable-camera.md)
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)

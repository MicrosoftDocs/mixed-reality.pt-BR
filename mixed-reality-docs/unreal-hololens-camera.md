---
title: Câmera do HoloLens no Unreal
description: Guia para usar a câmera do HoloLens no Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, 3rd camera, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840115"
---
# <a name="hololens-camera-in-unreal"></a>Câmera do HoloLens no Unreal

## <a name="third-camera-mixed-reality-capture"></a>Captura de realidade misturada de terceira câmera

A terceira câmera do MRC (Captura de Realidade Misturada) pode ser usada para renderizar uma captura de realidade misturada da perspectiva da câmera no visor do HoloLens em vez da perspectiva das texturas do olho.  Isso melhora o mapeamento entre o mundo real e os hologramas no vídeo do MRC. 

Para optar por usar a terceira câmera do MRC, chame SetEnabledMixedRealityCamera e ResizeMixedRealityCamera com as dimensões de vídeo desejadas. 

![Terceira câmera](images/unreal-camera-3rd.PNG)

Em seguida, registre um vídeo do MRC no portal do dispositivo do HoloLens. 

## <a name="pv-camera"></a>Câmera de PV

A textura da webcam também pode ser recuperada no jogo em runtime.  Para obter a textura da webcam no HoloLens, primeiro a funcionalidade "Webcam" deve estar marcada no editor do Unreal em Configurações do Projeto > Plataforma > HoloLens > Funcionalidades. 

Opte por usar a webcam em runtime com a função StartCameraCapture.  Pare a captura com a função StopCameraCapture. 

![Iniciar/interromper câmera](images/unreal-camera-startstop.PNG)

Para renderizar a imagem da câmera, primeiro crie uma instância de material dinâmica com base em um material no projeto.  Nesse caso, com base em um material chamado PVCamMat.  Defina isso como uma variável com o tipo Referência de Objeto Dinâmico de Instância de Material.  Em seguida, defina o material do objeto na cena que renderizará o feed da câmera para essa nova instância de material dinâmica e inicie um temporizador que será usado para associar a imagem da câmera ao material. 

![Renderização da câmera](images/unreal-camera-render.PNG)

Crie uma função para esse temporizador, neste caso, MaterialTimer, e chame GetARCameraImage para obter a textura da webcam.  Se essa textura for válida, defina um parâmetro de textura no sombreador para esta imagem.  Caso contrário, inicie o temporizador de material novamente. 

![Textura da câmera](images/unreal-camera-texture.PNG)

O material deve ter um parâmetro correspondente ao nome em SetTextureParameterValue associado a uma entrada de cor para exibir corretamente a imagem da câmera. 

![Textura da câmera](images/unreal-camera-material.PNG)

## <a name="see-also"></a>Veja também
* [Câmera localizável](locatable-camera.md)
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)

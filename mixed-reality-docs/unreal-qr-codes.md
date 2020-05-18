---
title: Códigos QR no Unreal
description: Guia para usar códigos QR no Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342654"
---
# <a name="qr-codes-in-unreal"></a>Códigos QR no Unreal

O HoloLens pode localizar códigos QR no espaço do mundo para renderizar hologramas em posições conhecidas no mundo real.  Isso também pode ser usado para renderizar hologramas em vários dispositivos no mesmo local para criar uma experiência compartilhada. 

Para habilitar a detecção de QR no HoloLens, verifique se a funcionalidade "Webcam" está marcada no editor do Unreal em Configurações do Projeto > Plataforma > HoloLens > Funcionalidades.  

Aceite o uso do controle de código QR no Unreal iniciando uma ARSession com a função StartARSession. 

Os códigos QR são exibidos por meio do sistema de geometria controlado pelo RA do Unreal como uma imagem rastreada.  Para usar isso, adicione um componente AR Trackable Notify a um ator do Blueprint: 

![AR Trackable Notify de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

Em seguida, acesse os detalhes do componente e clique no botão "+" verde nos eventos a serem monitorados.  

![Eventos de QR](images/unreal-spatialmapping-events.PNG)

Aqui, assinamos o OnUpdateTrackedImage para renderizar um ponto no centro de um código QR e imprimir os dados codificados do código QR. 

![Exemplo de renderização de QR](images/unreal-qr-render.PNG)

Primeiro, converta a imagem rastreada em um ARTrackedQRCode para verificar se a imagem atualizada atual é um código QR.  Em seguida, os dados codificados podem ser recuperados com a variável QRCode.  A parte superior esquerda do código QR pode ser recuperada do local de GetLocalToWorldTransform.  As dimensões podem ser recuperadas com GetEstimateSize. 

Todo código QR também tem uma ID de GUID exclusiva: 

![GUID de QR](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>Veja também
* [Acompanhamento de código QR](qr-code-tracking.md)

---
title: Códigos QR no Unreal
description: Um guia para usar códigos QR no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: a53fad14ab76136f1da419379dd39eca3a29701a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376098"
---
# <a name="qr-codes-in-unreal"></a>Códigos QR no Unreal

## <a name="overview"></a>Visão geral

O HoloLens 2 pode ver códigos QR no espaço de mundo usando a webcam, que os renderiza como hologramas usando um sistema de coordenadas na posição de cada código no mundo real.  Além de códigos QR individuais, o HoloLens 2 também pode renderizar hologramas em vários dispositivos no mesmo local para criar uma experiência compartilhada. Verifique se você está seguindo as melhores práticas para adicionar códigos QR aos aplicativos:

- Zonas silenciosas
- Iluminação e pano de fundo
- Tamanho, distância e posição angular

Preste atenção especial às [considerações sobre o ambiente](environment-considerations-for-hololens.md) quando os códigos QR estiverem sendo posicionados em seu aplicativo. Você pode encontrar mais informações sobre cada um desses tópicos e instruções sobre como baixar o pacote NuGet necessário no documento principal [rastreamento de código QR](qr-code-tracking.md). 

## <a name="enabling-qr-detection"></a>Como habilitar a detecção de QR
Como o HoloLens 2 precisa usar a webcam para ver os códigos QR, você precisará habilitá-la nas configurações do projeto:
- Abra **Editar > Configurações do Projeto**, role até a seção **Plataformas** e clique em **HoloLens**.
    + Expanda a seção **Funcionalidades** e marque **Webcam**.  

Você também precisará aceitar o controle de código QR [adicionando um ativo ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

Logo antes do uso, habilite manualmente o rastreamento chamando `UHoloLensARFunctionLibrary::StartQRCodeCapture()`. Depois de encerrar o rastreamento do código QR, desabilite-o com `UHoloLensARFunctionLibrary::StopCameraCapture()` para salvar os recursos do dispositivo. 

## <a name="setting-up-a-tracked-image"></a>Configurar uma imagem rastreada

Os códigos QR são exibidos por meio do sistema de geometria controlado pelo RA do Unreal como uma imagem rastreada. Para fazer isso funcionar, você precisará:
1. Criar um Blueprint e adicionar um componente **ARTrackableNotify** a ele.

![AR Trackable Notify de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Selecione **ARTrackableNotify** e expanda a seção **Eventos** no painel **Detalhes**. 

![Eventos de QR](images/unreal-spatialmapping-events.PNG)

3. Clique em **+** ao lado de **Ao Adicionar Geometria Rastreada** para adicionar o nó ao Grafo de Eventos.
    - Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

![Exemplo de renderização de QR](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a>Como usar uma imagem rastreada
O Grafo de Eventos na imagem a seguir mostra o evento **OnUpdateTrackedImage** que está sendo usado para processar um ponto no centro de um código QR e imprimir os dados desse código. 

![Exemplo de renderização de QR](images/unreal-qr-render.PNG)

Isto é o que está acontecendo:
1. Primeiro, a imagem rastreada é convertida em um **ARTrackedQRCode** para verificar se a imagem atualizada atual é um código QR.  
2. Os dados codificados são recuperados da variável **QRCode**. Com o local de **GetLocalToWorldTransform**, é possível obter as coordenadas do canto superior esquerdo do código QR; já com **GetEstimateSize**, é possível obter as dimensões desse código. 

Você também pode [obter o sistema de coordenadas de um código QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) no código.

## <a name="finding-the-unique-id"></a>Como localizar a ID exclusiva
Todo código QR tem uma ID GUID exclusiva, que pode ser encontrada:
- Arrastando e soltando o marcador **Como QRCode ARTracked** e pesquisando por **Obter ID Exclusiva**.

![GUID de QR](images/unreal-qr-guid.PNG)

Há muita coisa acontecendo nos bastidores envolvendo códigos QR, portanto, esse não é o fim da linha. Não deixe de conferir os links a seguir para obter mais detalhes sobre o que está acontecendo nos bastidores.

## <a name="see-also"></a>Veja também
* [Mapeamento espacial](spatial-mapping.md)
* [Hologramas](hologram.md)
* [Sistemas de coordenadas](coordinate-systems.md)

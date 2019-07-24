---
title: Âncoras espaciais compartilhadas no DirectX
description: Explica como sincronizar dois dispositivos HoloLens compartilhando âncoras espaciais.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, sincronizar, âncora espacial, transferência, vários participantes, exibição, cenário, passo a passos, código de exemplo, Azure, âncoras espaciais do Azure, ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516876"
---
# <a name="shared-experiences-in-directx"></a>Experiências compartilhadas no DirectX

Uma experiência compartilhada é aquela em que vários usuários, cada um com seu próprio dispositivo de HoloLens, iOS ou Android, exibem e interagem coletivamente com o mesmo holograma que é posicionado em um ponto fixo no espaço. Isso é feito por meio do compartilhamento de âncora espacial.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar âncoras espaciais duráveis com suporte de nuvem, que seu aplicativo pode localizar em vários dispositivos HoloLens, Ios e Android.  Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a> para persistência assíncrona de holograma em dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial em nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que os dispositivos não estejam presentes ao mesmo tempo.

Para começar a criar experiências compartilhadas em seu aplicativo de HoloLens, experimente o início rápido de 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">do Azure espaciais do hololens</a>.

Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">criar e localizar âncoras no HoloLens</a>.  Os passo a passos também estão disponíveis para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e Ios</a> , permitindo que você compartilhe as mesmas âncoras em todos os dispositivos.

## <a name="local-anchor-transfers"></a>Transferências de âncora local

Em situações em que você não pode usar âncoras espaciais do Azure, as [transferências de âncora local](local-anchor-transfers-in-directx.md) permitem que um dispositivo de hololens exporte uma âncora a ser importada por um segundo dispositivo hololens.  Observe que essa abordagem fornece uma recall de ancoragem menos robusta do que as âncoras espaciais do Azure, e os dispositivos iOS e Android não são compatíveis com essa abordagem.

## <a name="see-also"></a>Consulte também
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">SDK de âncoras espaciais do Azure para HoloLens</a>
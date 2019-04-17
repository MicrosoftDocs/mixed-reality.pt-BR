---
title: Experiências compartilhadas no Unity
description: Compartilhe as mesmas hologramas entre vários usuários em um aplicativo do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Compartilhando, âncora, WorldAnchor, MR compartilhamento 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure âncoras espaciais, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591014"
---
# <a name="shared-experiences-in-unity"></a>Experiências compartilhadas no Unity

Uma experiência compartilhada é um onde vários usuários, cada um com suas próprias HoloLens, dispositivo iOS ou Android, coletivamente exibir e interagem com o mesmo holograma que está posicionado em um ponto fixo no espaço. Isso é feito por meio do compartilhamento de âncora espacial.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> criar durável com backup em nuvem espaciais âncoras, que seu aplicativo pode, em seguida, localizar em vários HoloLens, dispositivos iOS e Android.  Compartilhando uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para persistência holograma assíncrona em dispositivos Android, iOS e HoloLens.  Compartilhando uma âncora de nuvem durável espacial, vários dispositivos podem observar o holograma persistente mesmo ao longo do tempo, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo.

Para começar a criação de experiências compartilhadas no Unity, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guias de início rápido do Azure espacial âncoras Unity</a>.

Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar as âncoras no Unity</a>.

## <a name="local-anchor-transfers"></a>Transferências de âncora local

Em situações em que você não pode usar âncoras espacial do Azure, [transferências de âncora local](local-anchor-transfers-in-unity.md) permitem que um dispositivo HoloLens exportar uma âncora para ser importado por um segundo dispositivo HoloLens.  Observe que essa abordagem fornece menos robustas do recolhimento de âncora que âncoras espacial do Azure, e não há suporte para dispositivos iOS e Android por essa abordagem.

## <a name="see-also"></a>Consulte também
* [Compartilhado experiências na realidade mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Âncoras espaciais do Azure SDK para Unity</a>
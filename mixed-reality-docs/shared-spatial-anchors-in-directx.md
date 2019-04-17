---
title: Compartilhado âncoras espaciais no DirectX
description: Explica como sincronizar dois dispositivos HoloLens, compartilhando âncoras espaciais.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, sincronizar, âncora espacial, transferência, com vários participantes, exibição, o cenário, o passo a passo, código de exemplo, Azure, as âncoras espacial do Azure, o ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591012"
---
# <a name="shared-experiences-in-directx"></a>Experiências compartilhadas no DirectX

Uma experiência compartilhada é um onde vários usuários, cada um com suas próprias HoloLens, dispositivo iOS ou Android, coletivamente exibir e interagem com o mesmo holograma que está posicionado em um ponto fixo no espaço. Isso é feito por meio do compartilhamento de âncora espacial.

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> criar durável com backup em nuvem espaciais âncoras, que seu aplicativo pode, em seguida, localizar em vários HoloLens, dispositivos iOS e Android.  Compartilhando uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para persistência holograma assíncrona em dispositivos Android, iOS e HoloLens.  Compartilhando uma âncora de nuvem durável espacial, vários dispositivos podem observar o holograma persistente mesmo ao longo do tempo, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo.

Para começar a criação de experiências compartilhadas em seu aplicativo HoloLens, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">guia de início rápido do Azure espacial âncoras HoloLens</a>.

Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">criar e localizar as âncoras em HoloLens</a>.  Instruções passo a passo está disponível para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> também, permitindo que você compartilhe as âncoras mesmas em todos os dispositivos.

## <a name="local-anchor-transfers"></a>Transferências de âncora local

Em situações em que você não pode usar âncoras espacial do Azure, [transferências de âncora local](local-anchor-transfers-in-directx.md) permitem que um dispositivo HoloLens exportar uma âncora para ser importado por um segundo dispositivo HoloLens.  Observe que essa abordagem fornece menos robustas do recolhimento de âncora que âncoras espacial do Azure, e não há suporte para dispositivos iOS e Android por essa abordagem.

## <a name="see-also"></a>Consulte também
* [Compartilhado experiências na realidade mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Âncoras espaciais do Azure SDK para HoloLens</a>
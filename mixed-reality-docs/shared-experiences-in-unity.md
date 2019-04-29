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
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="12ee4-104">Experiências compartilhadas no Unity</span><span class="sxs-lookup"><span data-stu-id="12ee4-104">Shared experiences in Unity</span></span>

<span data-ttu-id="12ee4-105">Uma experiência compartilhada é um onde vários usuários, cada um com suas próprias HoloLens, dispositivo iOS ou Android, coletivamente exibir e interagem com o mesmo holograma que está posicionado em um ponto fixo no espaço.</span><span class="sxs-lookup"><span data-stu-id="12ee4-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="12ee4-106">Isso é feito por meio do compartilhamento de âncora espacial.</span><span class="sxs-lookup"><span data-stu-id="12ee4-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="12ee4-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="12ee4-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="12ee4-108">Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> criar durável com backup em nuvem espaciais âncoras, que seu aplicativo pode, em seguida, localizar em vários HoloLens, dispositivos iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="12ee4-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="12ee4-109">Compartilhando uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="12ee4-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="12ee4-110">Isso permite experiências compartilhadas em tempo real.</span><span class="sxs-lookup"><span data-stu-id="12ee4-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="12ee4-111">Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para persistência holograma assíncrona em dispositivos Android, iOS e HoloLens.</span><span class="sxs-lookup"><span data-stu-id="12ee4-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="12ee4-112">Compartilhando uma âncora de nuvem durável espacial, vários dispositivos podem observar o holograma persistente mesmo ao longo do tempo, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="12ee4-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="12ee4-113">Para começar a criação de experiências compartilhadas no Unity, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guias de início rápido do Azure espacial âncoras Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="12ee4-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="12ee4-114">Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar as âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="12ee4-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="12ee4-115">Transferências de âncora local</span><span class="sxs-lookup"><span data-stu-id="12ee4-115">Local anchor transfers</span></span>

<span data-ttu-id="12ee4-116">Em situações em que você não pode usar âncoras espacial do Azure, [transferências de âncora local](local-anchor-transfers-in-unity.md) permitem que um dispositivo HoloLens exportar uma âncora para ser importado por um segundo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="12ee4-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="12ee4-117">Observe que essa abordagem fornece menos robustas do recolhimento de âncora que âncoras espacial do Azure, e não há suporte para dispositivos iOS e Android por essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="12ee4-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="12ee4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12ee4-118">See also</span></span>
* [<span data-ttu-id="12ee4-119">Compartilhado experiências na realidade mista</span><span class="sxs-lookup"><span data-stu-id="12ee4-119">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="12ee4-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="12ee4-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="12ee4-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Âncoras espaciais do Azure SDK para Unity</a></span><span class="sxs-lookup"><span data-stu-id="12ee4-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
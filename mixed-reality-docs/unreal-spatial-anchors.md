---
title: Âncoras espaciais no Unreal
description: Guia para uso de âncoras espaciais em Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840135"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="e72db-104">Âncoras espaciais no Unreal</span><span class="sxs-lookup"><span data-stu-id="e72db-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="e72db-105">As âncoras espaciais são usadas para persistir os hologramas no espaço do mundo real entre as sessões do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e72db-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="e72db-106">Elas são exibidas por meio do Unreal como ARPins e são salvas no repositório de âncoras do HoloLens para serem carregadas em sessões futuras.</span><span class="sxs-lookup"><span data-stu-id="e72db-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="e72db-107">Antes de salvar ou carregar âncoras, primeiro verifique se o repositório de âncoras está pronto.</span><span class="sxs-lookup"><span data-stu-id="e72db-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="e72db-108">A tentativa de chamar qualquer uma das funções de âncora do HoloLens antes que o repositório de âncora esteja pronto não terá sucesso.</span><span class="sxs-lookup"><span data-stu-id="e72db-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="e72db-110">Salvar âncoras</span><span class="sxs-lookup"><span data-stu-id="e72db-110">Save Anchors</span></span>

<span data-ttu-id="e72db-111">Quando o aplicativo tem um componente que precisa ser fixado no mundo, ele pode ser salvo no repositório de âncoras com a seguinte sequência:</span><span class="sxs-lookup"><span data-stu-id="e72db-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Salvar âncoras espaciais](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="e72db-113">Aqui, estamos gerando um ator em um local conhecido, criando um ARPin com esse local e um nome com base na classe do ator, adicionando o ator ao ARPin e salvando o pino no repositório de âncora do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e72db-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="e72db-114">O nome da âncora que escolhemos deve ser exclusivo, portanto, neste exemplo, acrescentamos o carimbo de data/hora atual.</span><span class="sxs-lookup"><span data-stu-id="e72db-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="e72db-115">Se a âncora for salva com êxito no repositório de âncoras, ela poderá ser inspecionada no portal do dispositivo do HoloLens em Sistema > Gerenciador de mapas > Arquivos de Âncora Salvos no Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e72db-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="e72db-116">Carregar âncoras</span><span class="sxs-lookup"><span data-stu-id="e72db-116">Load Anchors</span></span>

<span data-ttu-id="e72db-117">Quando um aplicativo é iniciado, o blueprint a seguir pode ser chamado para restaurar os componentes aos respectivos locais de âncora:</span><span class="sxs-lookup"><span data-stu-id="e72db-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![Carregar âncoras espaciais](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="e72db-119">Neste exemplo, iteramos em todas as âncoras no repositório de âncoras, geramos um ator na identidade e fixamos o ator no ARPin do repositório de âncoras.</span><span class="sxs-lookup"><span data-stu-id="e72db-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="e72db-120">É importante gerar o ator na identidade, uma vez que a âncora é responsável por reposicionar o holograma no mundo com base no local em que ele foi salvo, de modo que qualquer transformação adicionada aqui adicionará um deslocamento à âncora.</span><span class="sxs-lookup"><span data-stu-id="e72db-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="e72db-121">A ID da âncora também é consultada para que atores diferentes possam ser gerados dependendo do nome salvo da âncora.</span><span class="sxs-lookup"><span data-stu-id="e72db-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="e72db-122">Remover âncoras</span><span class="sxs-lookup"><span data-stu-id="e72db-122">Remove Anchors</span></span> 

<span data-ttu-id="e72db-123">Quando terminar de usar uma âncora, o repositório de âncoras inteiro pode ser limpo ou âncoras individuais podem ser removidas do repositório de âncoras para que não sejam incluídas em sessões futuras:</span><span class="sxs-lookup"><span data-stu-id="e72db-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![Remover âncoras espaciais](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="e72db-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="e72db-125">See also</span></span>
* [<span data-ttu-id="e72db-126">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="e72db-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="e72db-127">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="e72db-127">Coordinate systems</span></span>](coordinate-systems.md)

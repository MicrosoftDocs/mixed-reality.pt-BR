---
title: Âncoras espaciais no Unreal
description: Guia para uso de âncoras espaciais em Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: 1100704cae40de1997eb869bfc6c82bba3d0dc6e
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428735"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="5f2f8-104">Âncoras espaciais no Unreal</span><span class="sxs-lookup"><span data-stu-id="5f2f8-104">Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="5f2f8-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5f2f8-105">Overview</span></span>

<span data-ttu-id="5f2f8-106">As âncoras espaciais são usadas para salvar os hologramas no espaço do mundo real entre as sessões do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="5f2f8-107">Elas são exibidas por meio do Unreal como **ARPin**s e são salvas no repositório de âncoras do HoloLens, que é carregado em sessões futuras.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> 

## <a name="checking-the-anchor-store"></a><span data-ttu-id="5f2f8-108">Como verificar o repositório de âncoras</span><span class="sxs-lookup"><span data-stu-id="5f2f8-108">Checking the anchor store</span></span>

<span data-ttu-id="5f2f8-109">Antes de salvar ou carregar âncoras, você precisa verificar se o repositório de âncoras está pronto.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-109">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="5f2f8-110">A tentativa de chamar qualquer uma das funções de âncora do HoloLens antes que o repositório de âncora esteja pronto não terá sucesso.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-110">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="5f2f8-112">Como salvar âncoras</span><span class="sxs-lookup"><span data-stu-id="5f2f8-112">Saving anchors</span></span>

<span data-ttu-id="5f2f8-113">Quando o aplicativo tem um componente que precisa ser fixado no mundo, ele pode ser salvo no repositório de âncoras com a seguinte sequência:</span><span class="sxs-lookup"><span data-stu-id="5f2f8-113">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Salvar âncoras espaciais](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="5f2f8-115">Passo a passo detalhado:</span><span class="sxs-lookup"><span data-stu-id="5f2f8-115">Breaking this down:</span></span>
1. <span data-ttu-id="5f2f8-116">Gere um ator em um local conhecido.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-116">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="5f2f8-117">Crie um **ARPin** com esse local e um nome com base na classe do ator.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-117">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="5f2f8-118">Adicione o ator ao **ARPin** e salve o marcador no repositório de âncoras do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-118">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="5f2f8-119">O nome da âncora que você escolhe, que neste exemplo é o carimbo de data/hora atual, precisa ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-119">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="5f2f8-120">Se a âncora for salva com êxito no repositório de âncoras, você poderá inspecioná-la no portal do dispositivo do HoloLens em **Sistema > Gerenciador de mapas > Arquivos de Âncora Salvos no Dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-120">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="5f2f8-121">Como carregar âncoras</span><span class="sxs-lookup"><span data-stu-id="5f2f8-121">Loading anchors</span></span>

<span data-ttu-id="5f2f8-122">Quando um aplicativo é iniciado, é possível usar o blueprint a seguir para restaurar os componentes aos respectivos locais de âncora:</span><span class="sxs-lookup"><span data-stu-id="5f2f8-122">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Carregar âncoras espaciais](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="5f2f8-124">Passo a passo detalhado:</span><span class="sxs-lookup"><span data-stu-id="5f2f8-124">Breaking this down:</span></span>
1. <span data-ttu-id="5f2f8-125">Itere por todas as âncoras no repositório de âncoras.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="5f2f8-126">Gere um ator na identidade.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="5f2f8-127">Fixe esse ator no **ARPin** do repositório de âncoras.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="5f2f8-128">É importante gerar o ator na identidade, uma vez que a âncora é responsável por reposicionar o holograma no mundo com base no local em que ele foi salvo.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="5f2f8-129">Transformações adicionadas aqui adicionarão um deslocamento à âncora.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="5f2f8-130">A ID da âncora também é consultada para que atores diferentes possam ser gerados dependendo do nome salvo da âncora.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="5f2f8-131">Como remover âncoras</span><span class="sxs-lookup"><span data-stu-id="5f2f8-131">Removing anchors</span></span> 

<span data-ttu-id="5f2f8-132">Quando você terminar de usar uma âncora, poderá limpar âncoras individuais ou o repositório de âncoras inteiro com os componentes **Remover ARPin do Repositório WMRAnchor** e **Remover Todos os ARPins do Repositório WMRAnchor**.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-132">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Remover âncoras espaciais](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="5f2f8-134">Tenha em mente que as Âncoras Espaciais ainda estão na versão beta, portanto, lembre-se de conferir este material novamente para obter informações e recursos atualizados.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-134">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f2f8-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="5f2f8-135">See also</span></span>
* [<span data-ttu-id="5f2f8-136">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="5f2f8-136">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="5f2f8-137">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="5f2f8-137">Coordinate systems</span></span>](coordinate-systems.md)

---
title: Âncoras Espaciais locais no Unreal
description: Guia para uso de âncoras espaciais em Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: b102d506b1d670291c3b97ca34d277e2597af043
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376039"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="df5e2-104">Âncoras Espaciais locais no Unreal</span><span class="sxs-lookup"><span data-stu-id="df5e2-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="df5e2-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="df5e2-105">Overview</span></span>

<span data-ttu-id="df5e2-106">As âncoras espaciais são usadas para salvar os hologramas no espaço do mundo real entre as sessões do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df5e2-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="df5e2-107">Elas são exibidas por meio do Unreal como **ARPin**s e são salvas no repositório de âncoras do HoloLens, que é carregado em sessões futuras.</span><span class="sxs-lookup"><span data-stu-id="df5e2-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="df5e2-108">As âncoras locais são ideais como fallback quando não há nenhuma conectividade com a Internet.</span><span class="sxs-lookup"><span data-stu-id="df5e2-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df5e2-109">Elas são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem.</span><span class="sxs-lookup"><span data-stu-id="df5e2-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="df5e2-110">Se você pretende usar os serviços de nuvem do Azure para armazenar suas âncoras, temos um documento que pode orientar você na integração das [Âncoras Espaciais do Azure](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="df5e2-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="df5e2-111">Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.</span><span class="sxs-lookup"><span data-stu-id="df5e2-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="df5e2-112">Como verificar o repositório de âncoras</span><span class="sxs-lookup"><span data-stu-id="df5e2-112">Checking the anchor store</span></span>

<span data-ttu-id="df5e2-113">Antes de salvar ou carregar âncoras, você precisa verificar se o repositório de âncoras está pronto.</span><span class="sxs-lookup"><span data-stu-id="df5e2-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="df5e2-114">A tentativa de chamar qualquer uma das funções de âncora do HoloLens antes que o repositório de âncora esteja pronto não terá sucesso.</span><span class="sxs-lookup"><span data-stu-id="df5e2-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="df5e2-116">Como salvar âncoras</span><span class="sxs-lookup"><span data-stu-id="df5e2-116">Saving anchors</span></span>

<span data-ttu-id="df5e2-117">Quando o aplicativo tem um componente que precisa ser fixado no mundo, ele pode ser salvo no repositório de âncoras com a seguinte sequência:</span><span class="sxs-lookup"><span data-stu-id="df5e2-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Salvar âncoras espaciais](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="df5e2-119">Passo a passo detalhado:</span><span class="sxs-lookup"><span data-stu-id="df5e2-119">Breaking this down:</span></span>
1. <span data-ttu-id="df5e2-120">Gere um ator em um local conhecido.</span><span class="sxs-lookup"><span data-stu-id="df5e2-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="df5e2-121">Crie um **ARPin** com esse local e um nome com base na classe do ator.</span><span class="sxs-lookup"><span data-stu-id="df5e2-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="df5e2-122">Adicione o ator ao **ARPin** e salve o marcador no repositório de âncoras do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="df5e2-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="df5e2-123">O nome da âncora que você escolhe, que neste exemplo é o carimbo de data/hora atual, precisa ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="df5e2-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="df5e2-124">Se a âncora for salva com êxito no repositório de âncoras, você poderá inspecioná-la no portal do dispositivo do HoloLens em **Sistema > Gerenciador de mapas > Arquivos de Âncora Salvos no Dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="df5e2-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="df5e2-125">Como carregar âncoras</span><span class="sxs-lookup"><span data-stu-id="df5e2-125">Loading anchors</span></span>

<span data-ttu-id="df5e2-126">Quando um aplicativo é iniciado, é possível usar o blueprint a seguir para restaurar os componentes aos respectivos locais de âncora:</span><span class="sxs-lookup"><span data-stu-id="df5e2-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Carregar âncoras espaciais](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="df5e2-128">Passo a passo detalhado:</span><span class="sxs-lookup"><span data-stu-id="df5e2-128">Breaking this down:</span></span>
1. <span data-ttu-id="df5e2-129">Itere por todas as âncoras no repositório de âncoras.</span><span class="sxs-lookup"><span data-stu-id="df5e2-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="df5e2-130">Gere um ator na identidade.</span><span class="sxs-lookup"><span data-stu-id="df5e2-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="df5e2-131">Fixe esse ator no **ARPin** do repositório de âncoras.</span><span class="sxs-lookup"><span data-stu-id="df5e2-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="df5e2-132">É importante gerar o ator na identidade, uma vez que a âncora é responsável por reposicionar o holograma no mundo com base no local em que ele foi salvo.</span><span class="sxs-lookup"><span data-stu-id="df5e2-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="df5e2-133">Transformações adicionadas aqui adicionarão um deslocamento à âncora.</span><span class="sxs-lookup"><span data-stu-id="df5e2-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="df5e2-134">A ID da âncora também é consultada para que atores diferentes possam ser gerados dependendo do nome salvo da âncora.</span><span class="sxs-lookup"><span data-stu-id="df5e2-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="df5e2-135">Como remover âncoras</span><span class="sxs-lookup"><span data-stu-id="df5e2-135">Removing anchors</span></span> 

<span data-ttu-id="df5e2-136">Quando você terminar de usar uma âncora, poderá limpar âncoras individuais ou o repositório de âncoras inteiro com os componentes **Remover ARPin do Repositório WMRAnchor** e **Remover Todos os ARPins do Repositório WMRAnchor**.</span><span class="sxs-lookup"><span data-stu-id="df5e2-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Remover âncoras espaciais](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="df5e2-138">Tenha em mente que as Âncoras Espaciais ainda estão na versão beta, portanto, lembre-se de conferir este material novamente para obter informações e recursos atualizados.</span><span class="sxs-lookup"><span data-stu-id="df5e2-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="df5e2-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="df5e2-139">See also</span></span>
* [<span data-ttu-id="df5e2-140">Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="df5e2-140">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="df5e2-141">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="df5e2-141">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="df5e2-142">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="df5e2-142">Coordinate systems</span></span>](coordinate-systems.md)

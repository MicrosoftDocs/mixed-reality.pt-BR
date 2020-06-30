---
title: Mapeamento espacial no Unreal
description: Guia para usar o mapeamento espacial no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720402"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="2dd79-104">Mapeamento espacial no Unreal</span><span class="sxs-lookup"><span data-stu-id="2dd79-104">Spatial Mapping in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="2dd79-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="2dd79-105">Overview</span></span>
<span data-ttu-id="2dd79-106">O mapeamento espacial torna possível posicionar objetos em superfícies no mundo físico, mostrando o mundo em todo o HoloLens, o que torna os hologramas mais reais para o usuário.</span><span class="sxs-lookup"><span data-stu-id="2dd79-106">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="2dd79-107">O mapeamento espacial também ancora objetos no mundo do usuário, tirando proveito de indicações de profundidade do mundo real. Isso ajuda a convencer o usuário de que esses hologramas estão na verdade no espaço dele; hologramas que flutuam no espaço ou se movem com o usuário não parecem tão reais.</span><span class="sxs-lookup"><span data-stu-id="2dd79-107">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="2dd79-108">Sempre que possível, convém que você posicione os itens a fim de obter um maior conforto.</span><span class="sxs-lookup"><span data-stu-id="2dd79-108">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="2dd79-109">No documento [Mapeamento espacial](spatial-mapping.md), você pode encontrar mais informações sobre posicionamento, oclusão, renderização e qualidade do mapeamento espacial, além de outras informações.</span><span class="sxs-lookup"><span data-stu-id="2dd79-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="2dd79-110">Como habilitar o mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="2dd79-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="2dd79-111">Para habilitar o mapeamento espacial no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="2dd79-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="2dd79-112">Abra **Editar > Configurações do Projeto** e role para baixo até a seção **Plataformas**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="2dd79-113">Selecione **HoloLens** e marque **Percepção Espacial**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

<span data-ttu-id="2dd79-114">Para aceitar o mapeamento espacial e depurar o **MRMesh** em um jogo do HoloLens:</span><span class="sxs-lookup"><span data-stu-id="2dd79-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="2dd79-115">Abra o **ARSessionConfig** e expanda a seção **ARSettings > Mapeamento do Mundo**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="2dd79-116">Verifique **Gerar Dados de Malha de Geometria Rastreada**, que diz ao plug-in do HoloLens para iniciar a obtenção assíncrona de dados de mapeamento espacial e exibi-los no Unreal por meio do **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="2dd79-117">Marque **Renderizar Dados de Malha em Grade de Linhas** para mostrar um contorno de grade de linhas branco de todos os triângulos no **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="2dd79-119">Mapeamento espacial em runtime</span><span class="sxs-lookup"><span data-stu-id="2dd79-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="2dd79-120">Você pode modificar os seguintes parâmetros para atualizar o comportamento do runtime de mapeamento espacial:</span><span class="sxs-lookup"><span data-stu-id="2dd79-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="2dd79-121">Abra **Editar > Configurações de Projeto**, role para baixo até a seção **Plataformas** e selecione **HoloLens > Mapeamento Espacial**:</span><span class="sxs-lookup"><span data-stu-id="2dd79-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Configurações do projeto de âncoras espaciais](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="2dd79-123">A opção **Máximo de Triângulos por Metro Cúbico** atualiza a densidade dos triângulos na malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2dd79-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="2dd79-124">A opção **Tamanho do Volume de Malha Espacial** é o tamanho do cubo em volta do jogador para renderizar e atualizar os dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2dd79-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="2dd79-125">Se for previsto que o ambiente do runtime do aplicativo será grande, esse valor precisará ser grande para corresponder ao espaço do mundo real.</span><span class="sxs-lookup"><span data-stu-id="2dd79-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="2dd79-126">Por outro lado, se o aplicativo precisar apenas posicionar hologramas nas superfícies imediatamente próximas do usuário, esse campo poderá ser menor.</span><span class="sxs-lookup"><span data-stu-id="2dd79-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="2dd79-127">À medida que o usuário se movimenta pelo mundo, o volume de mapeamento espacial se moverá com ele.</span><span class="sxs-lookup"><span data-stu-id="2dd79-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="2dd79-128">Como trabalhar com o MRMesh</span><span class="sxs-lookup"><span data-stu-id="2dd79-128">Working with MRMesh</span></span>
<span data-ttu-id="2dd79-129">Para obter acesso ao **MRMesh** em runtime:</span><span class="sxs-lookup"><span data-stu-id="2dd79-129">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="2dd79-130">Adicione um componente **ARTrackableNotify** a um ator do Blueprint.</span><span class="sxs-lookup"><span data-stu-id="2dd79-130">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![AR Trackable Notify de âncoras espaciais](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="2dd79-132">Selecione o componente **ARTrackableNotify** e expanda a seção **Eventos** no painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-132">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="2dd79-133">Clique no botão **+** nos eventos que você deseja monitorar.</span><span class="sxs-lookup"><span data-stu-id="2dd79-133">Click the **+** button on the events you want to monitor.</span></span> 

![Eventos de âncoras espaciais](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="2dd79-135">Nesse caso, o evento **adicionar geometria rastreada** está sendo monitorado, o qual procura malhas válidas do mundo que correspondem aos dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2dd79-135">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="2dd79-136">Você pode encontrar a lista completa de eventos na API do componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="2dd79-136">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="2dd79-137">Você pode alterar o material da malha no Gráfico de Eventos do Blueprint ou no C++.</span><span class="sxs-lookup"><span data-stu-id="2dd79-137">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="2dd79-138">A captura de tela a seguir mostra a rota de Blueprint:</span><span class="sxs-lookup"><span data-stu-id="2dd79-138">The screenshot below shows the Blueprint route:</span></span> 

![Exemplo de âncoras espaciais](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="2dd79-140">No C++, você pode assinar o delegado `OnTrackableAdded` para obter a `ARTrackedGeometry` assim que ela estiver disponível, conforme mostrado no código abaixo.</span><span class="sxs-lookup"><span data-stu-id="2dd79-140">In C++, you can subscribe to the `OnTrackableAdded` delegate to get the `ARTrackedGeometry` as soon as it is available, shown in the code below.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="2dd79-141">O arquivo build.cs do projeto **PRECISA** ter **AugmentedReality** na lista **PublicDependencyModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-141">The project’s build.cs file **MUST** have **AugmentedReality** in the **PublicDependencyModuleNames** list.</span></span>
> - <span data-ttu-id="2dd79-142">Isso inclui **ARBlueprintLibrary.h** e **MRMeshComponent.h**, o que permite a você inspecionar o componente **MRMesh** do **UARTrackedGeometry**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-142">This includes **ARBlueprintLibrary.h** and **MRMeshComponent.h**, which lets you inspect the **MRMesh** component of the **UARTrackedGeometry**.</span></span> 

![Código de exemplo de âncoras espaciais em C++](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="2dd79-144">O mapeamento espacial não é o único tipo de dados que é exibido por meio de **ARTrackedGeometries**.</span><span class="sxs-lookup"><span data-stu-id="2dd79-144">Spatial mapping is not the only type of data that gets surfaced through **ARTrackedGeometries**.</span></span> <span data-ttu-id="2dd79-145">Você pode verificar que o `EARObjectClassification` é `World`, o que significa que isso é a geometria de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2dd79-145">You can check that the `EARObjectClassification` is `World`, which means this is spatial mapping geometry.</span></span> 

<span data-ttu-id="2dd79-146">Há delegados semelhantes para eventos atualizados e removidos:</span><span class="sxs-lookup"><span data-stu-id="2dd79-146">There are similar delegates for updated and removed events:</span></span> 
- `AddOnTrackableUpdatedDelegate_Handle` 
- <span data-ttu-id="2dd79-147">`AddOnTrackableRemovedDelegate_Handle`.</span><span class="sxs-lookup"><span data-stu-id="2dd79-147">`AddOnTrackableRemovedDelegate_Handle`.</span></span> 

<span data-ttu-id="2dd79-148">Você pode encontrar a lista completa de eventos na API de [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="2dd79-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dd79-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="2dd79-149">See also</span></span>
* [<span data-ttu-id="2dd79-150">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="2dd79-150">Spatial mapping</span></span>](spatial-mapping.md)

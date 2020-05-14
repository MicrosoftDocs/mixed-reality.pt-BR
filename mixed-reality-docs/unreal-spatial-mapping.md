---
title: Mapeamento espacial no Unreal
description: Guia para usar o mapeamento espacial no Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840075"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="9edfb-104">Mapeamento espacial no Unreal</span><span class="sxs-lookup"><span data-stu-id="9edfb-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="9edfb-105">Para habilitar o mapeamento espacial no HoloLens, marque a funcionalidade "Percepção Espacial" no editor do Unreal em Configurações do Projeto > Plataforma > HoloLens > Funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="9edfb-105">To enable spatial mapping on HoloLens, ensure that the “Spatial Perception” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="9edfb-106">Para optar pelo uso do mapeamento espacial em um jogo do HoloLens, habilite "Gerar Dados de Malha de Geometria Rastreada" no ARSessionConfig.</span><span class="sxs-lookup"><span data-stu-id="9edfb-106">To opt into using spatial mapping in a HoloLens game, enable the “Generate Mesh Data from Tracked Geometry” in the ARSessionConfig.</span></span>  <span data-ttu-id="9edfb-107">Dessa maneira, o plug-in do HoloLens obterá dados de mapeamento espacial de maneira assíncrona e os entregará ao Unreal por meio do MRMesh.</span><span class="sxs-lookup"><span data-stu-id="9edfb-107">The HoloLens plugin will then asynchronously get spatial mapping data and surface it to Unreal through the MRMesh.</span></span> 

![Armazenamento de âncoras espaciais pronto](images/unreal-spatialmapping-arsettings.PNG)

<span data-ttu-id="9edfb-109">Para ver uma visualização de depuração da malha de mapeamento espacial, habilite a caixa de seleção "Renderizar Dados de Malha no Delineado" no ARSessionConfig para ver um contorno delineado branco de cada triângulo no MRMesh.</span><span class="sxs-lookup"><span data-stu-id="9edfb-109">To see a debug visualization of the spatial mapping mesh, enable the “Render Mesh Data in Wireframe” checkbox in the ARSessionConfig to see a white wireframe outline of every triangle in the MRMesh.</span></span> 

<span data-ttu-id="9edfb-110">Em Configurações do Projeto > Plataforma > HoloLens > Mapeamento Espacial, os seguintes parâmetros podem ser modificados para atualizar o comportamento do runtime do mapeamento espacial:</span><span class="sxs-lookup"><span data-stu-id="9edfb-110">In Project Settings > Platform > HoloLens > Spatial Mapping, the following parameters can be modified to update spatial mapping’s runtime behavior:</span></span> 

![Configurações do projeto de âncoras espaciais](images/unreal-spatialmapping-projectsettings.PNG)

<span data-ttu-id="9edfb-112">A opção Máximo de Triângulos por Metro Cúbico atualizará a densidade dos triângulos na malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="9edfb-112">Max Triangles Per Cubic Meter will update the density of the triangles in the spatial mapping mesh.</span></span>  <span data-ttu-id="9edfb-113">A opção Tamanho do Volume de Malha Espacial indica o tamanho do cubo em volta do jogador para renderizar e atualizar os dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="9edfb-113">Spatial Meshing Volume Size indicates the size of the cube around the player to render and update spatial mapping data.</span></span>  <span data-ttu-id="9edfb-114">Se for previsto que o ambiente do runtime do aplicativo será grande, esse campo precisará ser grande para corresponder ao espaço do mundo real.</span><span class="sxs-lookup"><span data-stu-id="9edfb-114">If the expected application runtime environment is expected to be large, this field may need to be large to match the real-world space.</span></span>  <span data-ttu-id="9edfb-115">Por outro lado, se o aplicativo precisar apenas posicionar hologramas nas superfícies imediatamente próximas do usuário, esse campo poderá ser menor.</span><span class="sxs-lookup"><span data-stu-id="9edfb-115">Conversely, if the application only needs to place holograms on surfaces immediately around the user, this field can be smaller.</span></span>  <span data-ttu-id="9edfb-116">À medida que o usuário se movimenta pelo mundo, o volume de mapeamento espacial se moverá com ele.</span><span class="sxs-lookup"><span data-stu-id="9edfb-116">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

<span data-ttu-id="9edfb-117">Para obter acesso ao MRMesh em runtime, primeiro adicione um Componente AR Trackable Notify a um ator do Blueprint:</span><span class="sxs-lookup"><span data-stu-id="9edfb-117">To get access to the MRMesh at runtime, first add an AR Trackable Notify Component to a Blueprint actor:</span></span> 

![AR Trackable Notify de âncoras espaciais](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="9edfb-119">Em seguida, acesse os detalhes do componente e clique no botão "+" verde nos eventos a serem monitorados.</span><span class="sxs-lookup"><span data-stu-id="9edfb-119">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span> 

![Eventos de âncoras espaciais](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="9edfb-121">Nesse caso, monitoramos o evento On Add Tracked Geometry procurando por malhas válidas do mundo que correspondam aos dados de mapeamento espacial e alterem o material da malha:</span><span class="sxs-lookup"><span data-stu-id="9edfb-121">In this case we monitor the On Add Tracked Geometry event looking for valid world meshes which correspond to spatial mapping data, and change the mesh’s material:</span></span> 

![Exemplo de âncoras espaciais](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="9edfb-123">No C++, podemos assinar o delegado OnTrackableAdded para obter o ARTrackedGeometry assim que ele estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="9edfb-123">In C++, we can subscribe to the OnTrackableAdded delegate to get the ARTrackedGeometry as soon as it is available.</span></span>  <span data-ttu-id="9edfb-124">Há delegados semelhantes para eventos atualizados e removidos: AddOnTrackableUpdatedDelegate_Handle e AddOnTrackableRemovedDelegate_Handle.</span><span class="sxs-lookup"><span data-stu-id="9edfb-124">There are similar delegates for updated and removed events: AddOnTrackableUpdatedDelegate_Handle and AddOnTrackableRemovedDelegate_Handle.</span></span> 

![Código de exemplo de âncoras espaciais em C++](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="9edfb-126">O build.cs do projeto deve ter "AugmentedReality" na lista PublicDependencyModuleNames para incluir "ARBlueprintLibrary.h" e "MRMesh" para inspecionar o componente MRMesh do UARTrackedGeometry.</span><span class="sxs-lookup"><span data-stu-id="9edfb-126">The project’s build.cs must have “AugmentedReality” in the PublicDependencyModuleNames list to include “ARBlueprintLibrary.h” and “MRMesh” to inspect the MRMesh component of the UARTrackedGeometry.</span></span> 

<span data-ttu-id="9edfb-127">O mapeamento espacial não é o único tipo de dados que é exibido por meio do ARTrackedGeometries, portanto, primeiro verificamos se o EARObjectClassification é Mundo, o que indica que isso é geometria de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="9edfb-127">Spatial mapping is not the only type of data that gets surfaced through ARTrackedGeometries, so we first check that the EARObjectClassification is World, which indicates that this is spatial mapping geometry.</span></span> 

## <a name="see-also"></a><span data-ttu-id="9edfb-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="9edfb-128">See also</span></span>
* [<span data-ttu-id="9edfb-129">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="9edfb-129">Spatial mapping</span></span>](spatial-mapping.md)

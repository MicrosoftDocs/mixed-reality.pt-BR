---
title: Visualização de malha espacial
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realidade misturada, HoloLens, controles de interface do usuário, interação, interface do usuário, UX, design de UX, interface do usuário espacial, interação espacial, interface do usuário 3D, UX 3D
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346092"
---
# <a name="spatial-mesh"></a><span data-ttu-id="e429c-103">Malha espacial</span><span class="sxs-lookup"><span data-stu-id="e429c-103">Spatial mesh</span></span>

![Malha espacial](images/UX/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="e429c-105">Por meio da visualização de malha espacial, o usuário pode aprender como um dispositivo percebe e entende o ambiente físico.</span><span class="sxs-lookup"><span data-stu-id="e429c-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="e429c-106">Além de fornecer o contexto espacial, a visualização da malha espacial adequada pode criar uma experiência interessantes e mágico.</span><span class="sxs-lookup"><span data-stu-id="e429c-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="e429c-107">Diretriz de design</span><span class="sxs-lookup"><span data-stu-id="e429c-107">Design guideline</span></span>
<span data-ttu-id="e429c-108">Como é importante permitir que o usuário se concentre e interaja com o conteúdo, a visualização contínua e repetida da malha espacial em segundo plano poderia ser uma distração.</span><span class="sxs-lookup"><span data-stu-id="e429c-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="e429c-109">É recomendável Visualizar o ambiente com moderação, seja apenas uma vez na inicialização inicial ou quando o usuário mostrar uma intenção clara de ver a malha ambiental por direcionamento e espaço de toque.</span><span class="sxs-lookup"><span data-stu-id="e429c-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="e429c-110">Você pode observar esse comportamento no Shell do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e429c-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e429c-111">Visualização de malha espacial no MRTK (Kit de ferramentas de realidade mista) para Unity</span><span class="sxs-lookup"><span data-stu-id="e429c-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e429c-112">O MRTK fornece vários materiais para a visualização de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="e429c-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="e429c-113">**MRTK_Wireframe. esteira, MRTK_Wireframe. passe-partout**: material de malha espacial estática padrão que mostra os contornos de malha sem animação.</span><span class="sxs-lookup"><span data-stu-id="e429c-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="e429c-114">Esse material é útil para fins de depuração, pois mostra as geometrias de malha espacial inteiras.</span><span class="sxs-lookup"><span data-stu-id="e429c-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="e429c-115">No entanto, não é recomendável para produção.</span><span class="sxs-lookup"><span data-stu-id="e429c-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="e429c-116">**MRTK_SurfaceReconstruction. passe-partout**: esse material oferece um efeito de pulso animado na malha espacial.</span><span class="sxs-lookup"><span data-stu-id="e429c-116">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="e429c-117">Você pode usar esse material para visualizar o ambiente em um momento específico da sua experiência ou na entrada do toque do usuário.</span><span class="sxs-lookup"><span data-stu-id="e429c-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="e429c-118">Consulte a cena **PulseShaderExamples. Unity** para ver os exemplos.</span><span class="sxs-lookup"><span data-stu-id="e429c-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="e429c-119">Consulte [reconhecimento espacial MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) e [sombreador MRTK-Pulse](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="e429c-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="e429c-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="e429c-120">See also</span></span>

* [<span data-ttu-id="e429c-121">Cursores</span><span class="sxs-lookup"><span data-stu-id="e429c-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e429c-122">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="e429c-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e429c-123">Botão</span><span class="sxs-lookup"><span data-stu-id="e429c-123">Button</span></span>](button.md)
* [<span data-ttu-id="e429c-124">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="e429c-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e429c-125">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="e429c-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e429c-126">Manipulação</span><span class="sxs-lookup"><span data-stu-id="e429c-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e429c-127">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="e429c-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e429c-128">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="e429c-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e429c-129">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="e429c-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e429c-130">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="e429c-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e429c-131">Teclado</span><span class="sxs-lookup"><span data-stu-id="e429c-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e429c-132">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="e429c-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e429c-133">Slate</span><span class="sxs-lookup"><span data-stu-id="e429c-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="e429c-134">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="e429c-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="e429c-135">Sombreador</span><span class="sxs-lookup"><span data-stu-id="e429c-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="e429c-136">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="e429c-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e429c-137">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="e429c-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e429c-138">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="e429c-138">Surface magnetism</span></span>](surface-magnetism.md)

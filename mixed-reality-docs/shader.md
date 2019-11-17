---
title: Shader
description: ''
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, UX
ms.openlocfilehash: 23371ae5d70e5e792415fd25c0d58def0a7cefbb
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143266"
---
# <a name="shader"></a><span data-ttu-id="03d73-103">Shader</span><span class="sxs-lookup"><span data-stu-id="03d73-103">Shader</span></span>

![Shader](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="03d73-105">Como os objetos Holographic são misturados com os físicos no ambiente, fornecer a indicação visual é importante na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="03d73-105">Since holographic objects are mixed with the physical ones in the environment, providing visual cue is important in mixed reality.</span></span> <span data-ttu-id="03d73-106">O sombreador standard do MRTK fornece vários tipos de efeitos visuais que podem ser usados com hologramas.</span><span class="sxs-lookup"><span data-stu-id="03d73-106">MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="03d73-107">O sistema de sombreamento padrão MRTK utiliza um único sombreador flexível que pode obter visuais semelhantes ao sombreador padrão do Unity, implementar princípios de sistema de design fluente e manter o desempenho em dispositivos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="03d73-107">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement Fluent Design System principles, and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="03d73-108">Exemplos de efeitos visuais usando o sombreador padrão do MRTK</span><span class="sxs-lookup"><span data-stu-id="03d73-108">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="03d73-109">![Mover](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="03d73-109">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="03d73-110">**Luz de proximidade**</span><span class="sxs-lookup"><span data-stu-id="03d73-110">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="03d73-111">![Girar](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="03d73-111">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="03d73-112">**Luz de borda**</span><span class="sxs-lookup"><span data-stu-id="03d73-112">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

---

## <a name="mrtk-standard-shader-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="03d73-113">Sombreador Standard MRTK no MRTK (Kit de ferramentas de realidade mista) para Unity</span><span class="sxs-lookup"><span data-stu-id="03d73-113">MRTK Standard shader in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="03d73-114">MRTK-sombreador padrão</span><span class="sxs-lookup"><span data-stu-id="03d73-114">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="03d73-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03d73-115">See also</span></span>

* [<span data-ttu-id="03d73-116">Cursores</span><span class="sxs-lookup"><span data-stu-id="03d73-116">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="03d73-117">Raio da mão</span><span class="sxs-lookup"><span data-stu-id="03d73-117">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="03d73-118">Button</span><span class="sxs-lookup"><span data-stu-id="03d73-118">Button</span></span>](button.md)
* [<span data-ttu-id="03d73-119">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="03d73-119">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="03d73-120">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="03d73-120">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="03d73-121">Manusei</span><span class="sxs-lookup"><span data-stu-id="03d73-121">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="03d73-122">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="03d73-122">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="03d73-123">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="03d73-123">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="03d73-124">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="03d73-124">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="03d73-125">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="03d73-125">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="03d73-126">Teclado</span><span class="sxs-lookup"><span data-stu-id="03d73-126">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="03d73-127">Dessa</span><span class="sxs-lookup"><span data-stu-id="03d73-127">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="03d73-128">Slate</span><span class="sxs-lookup"><span data-stu-id="03d73-128">Slate</span></span>](slate.md)
* [<span data-ttu-id="03d73-129">Slider</span><span class="sxs-lookup"><span data-stu-id="03d73-129">Slider</span></span>](slider.md)
* [<span data-ttu-id="03d73-130">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="03d73-130">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="03d73-131">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="03d73-131">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="03d73-132">Magnetism Surface</span><span class="sxs-lookup"><span data-stu-id="03d73-132">Surface magnetism</span></span>](surface-magnetism.md)

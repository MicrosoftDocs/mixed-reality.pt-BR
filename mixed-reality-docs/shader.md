---
title: Shader
description: O sombreador MRTK Standard fornece vários tipos de efeitos visuais que podem ser usados com hologramas.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, UX
ms.openlocfilehash: 4d95e335b3f7020766beae916423d0588ee66572
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694160"
---
# <a name="shader"></a><span data-ttu-id="77163-104">Shader</span><span class="sxs-lookup"><span data-stu-id="77163-104">Shader</span></span>

![Shader](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="77163-106">Como os objetos Holographic são misturados com os físicos no ambiente, é importante fornecer indicações visuais em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="77163-106">Since holographic objects are mixed with the physical ones in the environment, it's important to provide visual cues in mixed reality.</span></span> <span data-ttu-id="77163-107">O sombreador MRTK Standard fornece vários tipos de efeitos visuais que podem ser usados com hologramas.</span><span class="sxs-lookup"><span data-stu-id="77163-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="77163-108">O sistema de sombreamento padrão do MRTK utiliza um único sombreador flexível que pode obter visuais semelhantes ao sombreador padrão do Unity, implementa os [princípios do sistema de design fluente](https://www.microsoft.com/design/fluent/#/)e manter o desempenho em dispositivos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="77163-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="77163-109">Exemplos de efeitos visuais usando o sombreador padrão do MRTK</span><span class="sxs-lookup"><span data-stu-id="77163-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="77163-110">![Mover](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="77163-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="77163-111">**Luz de proximidade**</span><span class="sxs-lookup"><span data-stu-id="77163-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="77163-112">![Girar](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="77163-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="77163-113">**Luz de borda**</span><span class="sxs-lookup"><span data-stu-id="77163-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="77163-114">Sombreador Standard MRTK no MRTK (Kit de ferramentas de realidade mista) para Unity</span><span class="sxs-lookup"><span data-stu-id="77163-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="77163-115">MRTK-sombreador padrão</span><span class="sxs-lookup"><span data-stu-id="77163-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="77163-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="77163-116">See also</span></span>

* [<span data-ttu-id="77163-117">Cursores</span><span class="sxs-lookup"><span data-stu-id="77163-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="77163-118">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="77163-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="77163-119">Botão</span><span class="sxs-lookup"><span data-stu-id="77163-119">Button</span></span>](button.md)
* [<span data-ttu-id="77163-120">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="77163-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="77163-121">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="77163-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="77163-122">Manipulação</span><span class="sxs-lookup"><span data-stu-id="77163-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="77163-123">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="77163-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="77163-124">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="77163-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="77163-125">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="77163-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="77163-126">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="77163-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="77163-127">Teclado</span><span class="sxs-lookup"><span data-stu-id="77163-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="77163-128">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="77163-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="77163-129">Slate</span><span class="sxs-lookup"><span data-stu-id="77163-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="77163-130">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="77163-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="77163-131">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="77163-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="77163-132">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="77163-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="77163-133">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="77163-133">Surface magnetism</span></span>](surface-magnetism.md)

---
title: Delimitador de caixa e a barra de aplicativo
description: A barra de aplicativo é um menu de nível de objeto que contém uma série de botões que exibe na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra, caixa delimitadora de aplicativo
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829679"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="d6944-104">Delimitador de caixa e a barra de aplicativo</span><span class="sxs-lookup"><span data-stu-id="d6944-104">Bounding box and App bar</span></span>
![A delimitação é a interface padrão para manipulação de objetos na realidade mista.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="d6944-106">O que é a caixa delimitadora?</span><span class="sxs-lookup"><span data-stu-id="d6944-106">What is the Bounding box?</span></span>

<span data-ttu-id="d6944-107">A delimitação é a interface padrão para manipulação de objetos na realidade mista.</span><span class="sxs-lookup"><span data-stu-id="d6944-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="d6944-108">Ele fornece ao usuário uma funcionalidade que o objeto está atualmente ajustável.</span><span class="sxs-lookup"><span data-stu-id="d6944-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="d6944-109">Os cantos informar ao usuário que o objeto também pode ser dimensionado.</span><span class="sxs-lookup"><span data-stu-id="d6944-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="d6944-110">Essa funcionalidade visual mostra os usuários a área total do objeto – mesmo se ele não é visível fora de um modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="d6944-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="d6944-111">Isso é especialmente importante porque se ele não estava lá, um objeto ajustado para outro objeto ou superfície pode aparecer se comporte como se havia espaço ao redor dele que não deveria estar lá.</span><span class="sxs-lookup"><span data-stu-id="d6944-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="d6944-112">Em 2 de HoloLens, a caixa delimitadora funciona com a manipulação direta de mão e responde a proximidade do dedo do usuário.</span><span class="sxs-lookup"><span data-stu-id="d6944-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="d6944-113">Ele mostra os comentários visuais para ajudar o usuário a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="d6944-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="d6944-114">![HoloLens o ponto de vista do dimensionamento de um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="d6944-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="d6944-115">*Dimensionar um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="d6944-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="d6944-116">Os identificadores nos cantos da caixa delimitadora seguem um padrão amplamente entendido para ajustar a escala.</span><span class="sxs-lookup"><span data-stu-id="d6944-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="d6944-117">![HoloLens o ponto de vista de girar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="d6944-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="d6944-118">*Girar um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="d6944-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="d6944-119">![Comentários visuais na proximidade de mão](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="d6944-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="d6944-120">*Comentários visuais com base na proximidade*</span><span class="sxs-lookup"><span data-stu-id="d6944-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="d6944-121">As capacidades de retangulares verticais nas bordas da caixa delimitadora são indicadores de rotação.</span><span class="sxs-lookup"><span data-stu-id="d6944-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="d6944-122">Isso fornece ao usuário mais ajuste fino sobre seus hologramas inseridas.</span><span class="sxs-lookup"><span data-stu-id="d6944-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="d6944-123">Não apenas podem eles ajustar e dimensionar, mas agora gire também.</span><span class="sxs-lookup"><span data-stu-id="d6944-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="d6944-124">Para o desenvolvimento de aplicativo do Unity, consulte [caixa delimitadora no Kit de ferramentas-Unity realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="d6944-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="d6944-125">O que é a barra de aplicativo?</span><span class="sxs-lookup"><span data-stu-id="d6944-125">What is the App bar?</span></span>

<span data-ttu-id="d6944-126">A barra de aplicativo é um menu de nível de objeto que contém uma série de botões que exibe na borda inferior dos limites de um holograma.</span><span class="sxs-lookup"><span data-stu-id="d6944-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="d6944-127">Esse padrão geralmente é usado para dar aos usuários a capacidade de remover e ajustar hologramas.</span><span class="sxs-lookup"><span data-stu-id="d6944-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="d6944-128">Uma vez que esse padrão é usado com objetos que são bloqueado, do mundo, conforme um usuário se move ao redor do objeto que a barra de aplicativo será sempre exibido no lado de objetos mais próximo do usuário.</span><span class="sxs-lookup"><span data-stu-id="d6944-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="d6944-129">Embora isso não é billboarding, efetivamente alcançam o mesmo resultado; impedindo a posição para occlude ou a funcionalidade de bloco que estaria disponível de um local diferente em seu ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="d6944-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="d6944-130">![Andando um holograma.</span><span class="sxs-lookup"><span data-stu-id="d6944-130">![Walking around a hologram.</span></span> <span data-ttu-id="d6944-131">Segue a barra de aplicativo.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="d6944-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="d6944-132">*Andando um holograma, segue da barra de aplicativos*</span><span class="sxs-lookup"><span data-stu-id="d6944-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="d6944-133">A barra de aplicativo foi desenvolvida principalmente como uma maneira de gerenciar objetos colocados em um ambiente de usuário.</span><span class="sxs-lookup"><span data-stu-id="d6944-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="d6944-134">Juntamente com a caixa delimitadora, um usuário tem controle total sobre onde e como os objetos são orientados em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="d6944-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="d6944-135">Para o desenvolvimento de aplicativo do Unity, consulte [barra de aplicativos no Kit de ferramentas-Unity realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="d6944-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="d6944-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6944-136">See also</span></span>
* [<span data-ttu-id="d6944-137">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="d6944-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d6944-138">Texto no Unity</span><span class="sxs-lookup"><span data-stu-id="d6944-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="d6944-139">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="d6944-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d6944-140">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="d6944-140">Displaying progress</span></span>](progress.md)

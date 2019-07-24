---
title: Caixa delimitadora e barra de aplicativos
description: A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realidade mista do Windows, barra de aplicativos, caixa delimitadora
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829679"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="a38ab-104">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="a38ab-104">Bounding box and App bar</span></span>
![O limite é a interface padrão para a manipulação de objetos em realidade misturada.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="a38ab-106">O que é a caixa delimitadora?</span><span class="sxs-lookup"><span data-stu-id="a38ab-106">What is the Bounding box?</span></span>

<span data-ttu-id="a38ab-107">O limite é a interface padrão para a manipulação de objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a38ab-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="a38ab-108">Ele fornece ao usuário uma economia de que o objeto está ajustável no momento.</span><span class="sxs-lookup"><span data-stu-id="a38ab-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="a38ab-109">Os cantos informam ao usuário que o objeto também pode ser dimensionado.</span><span class="sxs-lookup"><span data-stu-id="a38ab-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="a38ab-110">Essa contratação Visual mostra aos usuários a área total do objeto – mesmo se ele não estiver visível fora de um modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="a38ab-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="a38ab-111">Isso é especialmente importante porque, se não existisse, um objeto encaixado em outro objeto ou superfície pode parecer funcionar como se houvesse espaço em volta dele que não deveria estar lá.</span><span class="sxs-lookup"><span data-stu-id="a38ab-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="a38ab-112">No HoloLens 2, a caixa delimitadora funciona com a manipulação direta e responde à proximidade finger's do usuário.</span><span class="sxs-lookup"><span data-stu-id="a38ab-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="a38ab-113">Ele mostra os comentários visuais para ajudar o usuário a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="a38ab-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="a38ab-114">![Ponto de exibição do HoloLens para dimensionar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="a38ab-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="a38ab-115">*Dimensionando um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="a38ab-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="a38ab-116">As alças nos cantos da caixa delimitadora seguem um padrão amplamente compreendido para ajustar a escala.</span><span class="sxs-lookup"><span data-stu-id="a38ab-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="a38ab-117">![Ponto de exibição do HoloLens para girar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="a38ab-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="a38ab-118">*Girando um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="a38ab-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="a38ab-119">![Comentário visual sobre a proximidade](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="a38ab-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="a38ab-120">*Comentários visuais com base na proximidade*</span><span class="sxs-lookup"><span data-stu-id="a38ab-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="a38ab-121">Os capacidades retangulares verticais nas bordas da caixa delimitadora são indicadores de rotação.</span><span class="sxs-lookup"><span data-stu-id="a38ab-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="a38ab-122">Isso dá ao usuário um ajuste mais fino sobre seus hologramas posicionados.</span><span class="sxs-lookup"><span data-stu-id="a38ab-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="a38ab-123">Elas não só podem ser ajustadas e dimensionadas, mas agora giram também.</span><span class="sxs-lookup"><span data-stu-id="a38ab-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="a38ab-124">Para o desenvolvimento de aplicativos do Unity, consulte [a caixa delimitadora no kit de ferramentas da realidade misturada-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="a38ab-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="a38ab-125">O que é a barra de aplicativos?</span><span class="sxs-lookup"><span data-stu-id="a38ab-125">What is the App bar?</span></span>

<span data-ttu-id="a38ab-126">A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.</span><span class="sxs-lookup"><span data-stu-id="a38ab-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="a38ab-127">Esse padrão geralmente é usado para fornecer aos usuários a capacidade de remover e ajustar os hologramas.</span><span class="sxs-lookup"><span data-stu-id="a38ab-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="a38ab-128">Como esse padrão é usado com objetos que são protegidos pelo mundo, à medida que um usuário se move pelo objeto, a barra de aplicativos sempre será exibida no lado dos objetos mais próximo do usuário.</span><span class="sxs-lookup"><span data-stu-id="a38ab-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="a38ab-129">Embora isso não seja o mural, ele efetivamente obtém o mesmo resultado; impedir que a posição de um usuário occlude ou bloqueie a funcionalidade que, de outra forma, estaria disponível em um local diferente em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="a38ab-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="a38ab-130">![Percorrendo um holograma.</span><span class="sxs-lookup"><span data-stu-id="a38ab-130">![Walking around a hologram.</span></span> <span data-ttu-id="a38ab-131">A barra de aplicativos é a seguinte.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="a38ab-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="a38ab-132">*Percorrendo um holograma, a barra de aplicativos segue*</span><span class="sxs-lookup"><span data-stu-id="a38ab-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="a38ab-133">A barra de aplicativos foi projetada principalmente como uma maneira de gerenciar objetos posicionados no ambiente de um usuário.</span><span class="sxs-lookup"><span data-stu-id="a38ab-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="a38ab-134">Junto com a caixa delimitadora, um usuário tem controle total sobre onde e como os objetos são orientados em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a38ab-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="a38ab-135">Para o desenvolvimento de aplicativos do Unity, consulte [barra de aplicativos no kit de ferramentas de realidade misturada – Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="a38ab-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="a38ab-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a38ab-136">See also</span></span>
* [<span data-ttu-id="a38ab-137">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="a38ab-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a38ab-138">Texto no Unity</span><span class="sxs-lookup"><span data-stu-id="a38ab-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="a38ab-139">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="a38ab-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a38ab-140">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="a38ab-140">Displaying progress</span></span>](progress.md)

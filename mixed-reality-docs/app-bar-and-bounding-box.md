---
title: Caixa delimitadora e barra de aplicativos
description: A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realidade mista do Windows, barra de aplicativos, caixa delimitadora
ms.openlocfilehash: f09187bc2a3969a8f844711052e15433f5449d6d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437058"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="8cdd6-104">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="8cdd6-104">Bounding box and App bar</span></span>
![O limite é a interface padrão para a manipulação de objetos em realidade misturada.](images/640px-boundingbox-hero.jpg)<br>

<br>

---

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="8cdd6-106">O que é a caixa delimitadora?</span><span class="sxs-lookup"><span data-stu-id="8cdd6-106">What is the Bounding box?</span></span>

<span data-ttu-id="8cdd6-107">O limite é a interface padrão para a manipulação de objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="8cdd6-108">Ele fornece ao usuário uma economia de que o objeto está ajustável no momento.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="8cdd6-109">No HoloLens 2, a caixa delimitadora funciona com a manipulação direta e responde à proximidade finger's do usuário.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="8cdd6-110">Ele mostra os comentários visuais para ajudar o usuário a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="8cdd6-111">Dimensionando um objeto</span><span class="sxs-lookup"><span data-stu-id="8cdd6-111">Scaling an object</span></span><br>
        <span data-ttu-id="8cdd6-112">Os cantos da caixa delimitadora informam ao usuário que o objeto pode ser dimensionado.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="8cdd6-113">Os identificadores seguem um padrão amplamente compreendido para ajustar a escala.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="8cdd6-114">Essa contratação Visual mostra aos usuários a área total do objeto – mesmo se ele não estiver visível fora de um modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="8cdd6-115">Isso é especialmente importante porque, se não existisse, um objeto encaixado em outro objeto ou superfície pode parecer funcionar como se houvesse espaço em volta dele que não deveria estar lá.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="8cdd6-116">*Loop de vídeo: dimensionando um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="8cdd6-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="8cdd6-117">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="8cdd6-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="8cdd6-118">![ponto de vista do HoloLens para dimensionar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="8cdd6-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="8cdd6-119">Girando um objeto</span><span class="sxs-lookup"><span data-stu-id="8cdd6-119">Rotating an object</span></span><br>
        <span data-ttu-id="8cdd6-120">Os capacidades retangulares verticais nas bordas da caixa delimitadora são indicadores de rotação.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="8cdd6-121">Isso dá ao usuário um ajuste mais fino sobre seus hologramas posicionados.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="8cdd6-122">Elas não só podem ser ajustadas e dimensionadas, mas agora giram também.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="8cdd6-123">*Loop de vídeo: girando um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="8cdd6-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="8cdd6-124">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="8cdd6-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="8cdd6-125">![ponto de vista do HoloLens de girar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="8cdd6-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="8cdd6-126">Comentário visual sobre a proximidade no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8cdd6-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="8cdd6-127">No HoloLens 2, há uma indicação visual adicional que pode ajudar a percepção de profundidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="8cdd6-128">Um anel próximo a ele é exibido e escala verticalmente conforme o alcance fica mais próximo do objeto.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="8cdd6-129">O anel, eventualmente, convergi em um ponto quando o estado pressionado é atingido.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="8cdd6-130">Essa unificação Visual ajuda o usuário a entender a distância deles do objeto.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="8cdd6-131">*Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="8cdd6-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="8cdd6-132">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="8cdd6-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="8cdd6-133">![os comentários visuais sobre a proximidade](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="8cdd6-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="8cdd6-134">**Para o desenvolvimento de aplicativos do Unity, consulte [a caixa delimitadora no kit de ferramentas da realidade misturada-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="8cdd6-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="8cdd6-135">O que é a barra de aplicativos?</span><span class="sxs-lookup"><span data-stu-id="8cdd6-135">What is the App bar?</span></span>

<span data-ttu-id="8cdd6-136">A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="8cdd6-137">Esse padrão geralmente é usado para fornecer aos usuários a capacidade de remover e ajustar os hologramas.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="8cdd6-138">A barra de aplicativos foi projetada principalmente como uma maneira de gerenciar objetos posicionados no ambiente de um usuário.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="8cdd6-139">Junto com a caixa delimitadora, um usuário tem controle total sobre onde e como os objetos são orientados em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="8cdd6-140">A barra de aplicativos segue o usuário</span><span class="sxs-lookup"><span data-stu-id="8cdd6-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="8cdd6-141">Como esse padrão é usado com objetos que são protegidos pelo mundo, à medida que um usuário se move pelo objeto, a barra de aplicativos sempre será exibida no lado dos objetos mais próximo do usuário.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="8cdd6-142">Embora isso não seja o mural, ele efetivamente obtém o mesmo resultado; impedir que a posição de um usuário occlude ou bloqueie a funcionalidade que, de outra forma, estaria disponível em um local diferente em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="8cdd6-143">*Loop de vídeo: percorrendo um holograma, a barra de aplicativos segue*</span><span class="sxs-lookup"><span data-stu-id="8cdd6-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="8cdd6-144">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="8cdd6-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="8cdd6-145">![percorrendo um holograma.</span><span class="sxs-lookup"><span data-stu-id="8cdd6-145">![Walking around a hologram.</span></span> <span data-ttu-id="8cdd6-146">A barra de aplicativos é a seguinte.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="8cdd6-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>



<span data-ttu-id="8cdd6-147">**Para o desenvolvimento de aplicativos do Unity, consulte [a barra de aplicativos no kit de ferramentas da realidade misturada-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span><span class="sxs-lookup"><span data-stu-id="8cdd6-147">**For Unity app development, see [App bar in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="8cdd6-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cdd6-148">See also</span></span>
* [<span data-ttu-id="8cdd6-149">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="8cdd6-149">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8cdd6-150">Texto no Unity</span><span class="sxs-lookup"><span data-stu-id="8cdd6-150">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="8cdd6-151">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="8cdd6-151">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8cdd6-152">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="8cdd6-152">Displaying progress</span></span>](progress.md)

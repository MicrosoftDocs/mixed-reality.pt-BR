---
title: Caixa delimitadora e barra de aplicativos
description: A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Realidade mista do Windows, barra de aplicativos, caixa delimitadora
ms.openlocfilehash: 97afc0df02fd8460547e955d4fcf3e33a4e9f566
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105763"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="5b625-104">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="5b625-104">Bounding box and App bar</span></span>
<span data-ttu-id="5b625-105">o limite de ![é a interface padrão para manipulação de objeto em realidade misturada.](images/640px-boundingbox-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="5b625-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/640px-boundingbox-hero.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="5b625-106">O que é a caixa delimitadora?</span><span class="sxs-lookup"><span data-stu-id="5b625-106">What is the Bounding box?</span></span>

<span data-ttu-id="5b625-107">O limite é a interface padrão para a manipulação de objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="5b625-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="5b625-108">Ele fornece ao usuário uma economia de que o objeto está ajustável no momento.</span><span class="sxs-lookup"><span data-stu-id="5b625-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="5b625-109">No HoloLens 2, a caixa delimitadora funciona com a manipulação direta e responde à proximidade finger's do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b625-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="5b625-110">Ele mostra os comentários visuais para ajudar o usuário a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="5b625-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="5b625-111">Dimensionando um objeto</span><span class="sxs-lookup"><span data-stu-id="5b625-111">Scaling an object</span></span><br>
        <span data-ttu-id="5b625-112">Os cantos da caixa delimitadora informam ao usuário que o objeto pode ser dimensionado.</span><span class="sxs-lookup"><span data-stu-id="5b625-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="5b625-113">Os identificadores seguem um padrão amplamente compreendido para ajustar a escala.</span><span class="sxs-lookup"><span data-stu-id="5b625-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="5b625-114">Essa contratação Visual mostra aos usuários a área total do objeto – mesmo se ele não estiver visível fora de um modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="5b625-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="5b625-115">Isso é especialmente importante porque, se não existisse, um objeto encaixado em outro objeto ou superfície pode parecer funcionar como se houvesse espaço em volta dele que não deveria estar lá.</span><span class="sxs-lookup"><span data-stu-id="5b625-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="5b625-116">*Loop de vídeo: dimensionando um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="5b625-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="5b625-117">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="5b625-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="5b625-118">![ponto de vista do HoloLens para dimensionar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="5b625-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="5b625-119">Girando um objeto</span><span class="sxs-lookup"><span data-stu-id="5b625-119">Rotating an object</span></span><br>
        <span data-ttu-id="5b625-120">Os capacidades retangulares verticais nas bordas da caixa delimitadora são indicadores de rotação.</span><span class="sxs-lookup"><span data-stu-id="5b625-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="5b625-121">Isso dá ao usuário um ajuste mais fino sobre seus hologramas posicionados.</span><span class="sxs-lookup"><span data-stu-id="5b625-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="5b625-122">Elas não só podem ser ajustadas e dimensionadas, mas agora giram também.</span><span class="sxs-lookup"><span data-stu-id="5b625-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="5b625-123">*Loop de vídeo: girando um objeto por meio da caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="5b625-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="5b625-124">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="5b625-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="5b625-125">![ponto de vista do HoloLens de girar um objeto por meio da caixa delimitadora](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="5b625-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="5b625-126">Comentário visual sobre a proximidade no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5b625-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="5b625-127">No HoloLens 2, há uma indicação visual adicional que pode ajudar a percepção de profundidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b625-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="5b625-128">Um anel próximo a ele é exibido e escala verticalmente conforme o alcance fica mais próximo do objeto.</span><span class="sxs-lookup"><span data-stu-id="5b625-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="5b625-129">O anel, eventualmente, convergi em um ponto quando o estado pressionado é atingido.</span><span class="sxs-lookup"><span data-stu-id="5b625-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="5b625-130">Essa unificação Visual ajuda o usuário a entender a distância deles do objeto.</span><span class="sxs-lookup"><span data-stu-id="5b625-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="5b625-131">*Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="5b625-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="5b625-132">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="5b625-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="5b625-133">![os comentários visuais sobre a proximidade](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="5b625-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="5b625-134">**Para o desenvolvimento de aplicativos do Unity, consulte [a caixa delimitadora no kit de ferramentas da realidade misturada-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="5b625-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="5b625-135">O que é a barra de aplicativos?</span><span class="sxs-lookup"><span data-stu-id="5b625-135">What is the App bar?</span></span>

<span data-ttu-id="5b625-136">A barra de aplicativos é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.</span><span class="sxs-lookup"><span data-stu-id="5b625-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="5b625-137">Esse padrão geralmente é usado para fornecer aos usuários a capacidade de remover e ajustar os hologramas.</span><span class="sxs-lookup"><span data-stu-id="5b625-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="5b625-138">A barra de aplicativos foi projetada principalmente como uma maneira de gerenciar objetos posicionados no ambiente de um usuário.</span><span class="sxs-lookup"><span data-stu-id="5b625-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="5b625-139">Junto com a caixa delimitadora, um usuário tem controle total sobre onde e como os objetos são orientados em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="5b625-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="5b625-140">A barra de aplicativos segue o usuário</span><span class="sxs-lookup"><span data-stu-id="5b625-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="5b625-141">Como esse padrão é usado com objetos que são protegidos pelo mundo, à medida que um usuário se move pelo objeto, a barra de aplicativos sempre será exibida no lado dos objetos mais próximo do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b625-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="5b625-142">Embora isso não seja o mural, ele efetivamente obtém o mesmo resultado; impedir que a posição de um usuário occlude ou bloqueie a funcionalidade que, de outra forma, estaria disponível em um local diferente em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="5b625-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="5b625-143">*Loop de vídeo: percorrendo um holograma, a barra de aplicativos segue*</span><span class="sxs-lookup"><span data-stu-id="5b625-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="5b625-144">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="5b625-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="5b625-145">![percorrendo um holograma.</span><span class="sxs-lookup"><span data-stu-id="5b625-145">![Walking around a hologram.</span></span> <span data-ttu-id="5b625-146">A barra de aplicativos é a seguinte.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="5b625-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="5b625-147">Caixa delimitadora no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="5b625-147">Bounding box in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="5b625-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e pré-fabricados para a caixa delimitadora e a barra de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5b625-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="5b625-149">Você pode adicionar uma caixa delimitadora simplesmente atribuindo o script BoundingBox.cs em qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="5b625-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="5b625-150">MRTK-caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="5b625-150">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="5b625-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b625-151">See also</span></span>

* [<span data-ttu-id="5b625-152">Cursores</span><span class="sxs-lookup"><span data-stu-id="5b625-152">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5b625-153">Raio da mão</span><span class="sxs-lookup"><span data-stu-id="5b625-153">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5b625-154">Button</span><span class="sxs-lookup"><span data-stu-id="5b625-154">Button</span></span>](button.md)
* [<span data-ttu-id="5b625-155">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="5b625-155">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5b625-156">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="5b625-156">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5b625-157">Manusei</span><span class="sxs-lookup"><span data-stu-id="5b625-157">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5b625-158">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="5b625-158">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5b625-159">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="5b625-159">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5b625-160">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="5b625-160">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5b625-161">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="5b625-161">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5b625-162">Teclado</span><span class="sxs-lookup"><span data-stu-id="5b625-162">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5b625-163">Dessa</span><span class="sxs-lookup"><span data-stu-id="5b625-163">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5b625-164">Slate</span><span class="sxs-lookup"><span data-stu-id="5b625-164">Slate</span></span>](slate.md)
* [<span data-ttu-id="5b625-165">Slider</span><span class="sxs-lookup"><span data-stu-id="5b625-165">Slider</span></span>](slider.md)
* [<span data-ttu-id="5b625-166">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="5b625-166">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5b625-167">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="5b625-167">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5b625-168">Magnetism Surface</span><span class="sxs-lookup"><span data-stu-id="5b625-168">Surface magnetism</span></span>](surface-magnetism.md)
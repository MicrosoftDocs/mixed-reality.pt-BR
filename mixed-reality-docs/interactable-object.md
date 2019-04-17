---
title: Objeto interagível
description: Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D. No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, experiência do usuário
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589808"
---
# <a name="interactable-object"></a><span data-ttu-id="1ff3f-105">Objeto interagível</span><span class="sxs-lookup"><span data-stu-id="1ff3f-105">Interactable object</span></span>

<span data-ttu-id="1ff3f-106">Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="1ff3f-107">No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="1ff3f-108">Nada pode ser um **Interagível objeto** que dispara um evento.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="1ff3f-109">Um objeto interagível pode ser representado como qualquer coisa uma xícara de café na tabela para um balão flutuar no ar.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="1ff3f-110">Estamos ainda fazer uso dos botões tradicionais em determinada situação como a caixa de diálogo da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="1ff3f-111">A representação visual do botão depende do contexto.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-111">The visual representation of the button depends on the context.</span></span>

![Imagem do herói de objeto interactible](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="1ff3f-113">No  **[Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, criamos uma série de scripts do Unity e pré-fabricados que ajudarão você a criar objetos Interagível.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="1ff3f-114">Você pode usá-los para criar qualquer tipo de objeto que o usuário pode interagir com o, usando esses estados de interação padrão: Observação, direcionadas e pressionado.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="1ff3f-115">Você pode personalizar facilmente o design visual com seus próprios ativos.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="1ff3f-116">Animações detalhadas podem ser personalizadas criando e atribuindo clipes de animação correspondente para os estados de interação no controlador de animação do Unity ou usando o deslocamento e a escala.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="1ff3f-117">Comentários visuais para os estados diferentes de interação de entrada</span><span class="sxs-lookup"><span data-stu-id="1ff3f-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="1ff3f-118">Na realidade mista, como os objetos holográfico são combinados com o ambiente do mundo real, pode ser difícil de entender quais objetos são interagível.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="1ff3f-119">Para quaisquer objetos interagível em sua experiência, é importante fornecer comentários visuais diferenciados para cada estado de entrada.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="1ff3f-120">Isso ajuda o usuário a entender qual parte da sua experiência é interagível e faz com que o usuário confiantes com o método de interação consistente.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="1ff3f-121">Para todos os objetos que o usuário pode interagir com, é recomendável ter comentários visuais diferentes para esses três estados de entrada:</span><span class="sxs-lookup"><span data-stu-id="1ff3f-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="1ff3f-122">**Observação**: Estado ocioso de padrão do objeto.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="1ff3f-123">**Destino**: Quando o objeto é afetado com o cursor de olhar, finger ponteiro do controlador proximidade ou a animação.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="1ff3f-124">**Pressionado**: Quando o objeto é pressionado com gestos de toque de ar, pressione dedo ou botão de seleção do controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="1ff3f-125">![Botão holographic](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1ff3f-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="1ff3f-126">*Observação de estado, estado de destino e estado pressionado*</span><span class="sxs-lookup"><span data-stu-id="1ff3f-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="1ff3f-127">Na realidade mista do Windows, você pode encontrar os exemplos de visualizar estados diferentes de entrada no menu Iniciar e botões da barra de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="1ff3f-128">Você pode usar técnicas, como realce ou dimensionamento para fornecer comentários visuais para estados de entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="1ff3f-129">Em 2 de HoloLens, já que ele dá suporte à mão completamente articulado rastreamento de entrada, podemos fornecer capacidades adicionais com base na proximidade para mãos.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="1ff3f-130">O [botão no HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) mostra este exemplo.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Botão pressable](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="1ff3f-132">Exemplos de objeto interagível</span><span class="sxs-lookup"><span data-stu-id="1ff3f-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="1ff3f-133">Botão de malha</span><span class="sxs-lookup"><span data-stu-id="1ff3f-133">Mesh button</span></span>

![Botão de malha](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="1ff3f-135">Estes são exemplos usando primitivos e malhas 3D importadas como objetos Interagível.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="1ff3f-136">Você pode facilmente atribuir valores diferentes de escala, deslocamento e a cor para responder a cada estado de interação de entrada.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="1ff3f-137">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="1ff3f-137">Toolbar</span></span>

![Barra de ferramentas](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="1ff3f-139">Uma barra de ferramentas é um padrão amplamente usado em experiências de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="1ff3f-140">Ele é uma coleção simples de botões com comportamentos adicionais, como [Billboarding e tag-along](billboarding-and-tag-along.md).</span><span class="sxs-lookup"><span data-stu-id="1ff3f-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="1ff3f-141">Este exemplo usa um script Billboarding e tag-along do MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="1ff3f-142">Você pode controlar comportamentos detalhados, incluindo a distância, movendo a velocidade e os valores limite.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="1ff3f-143">Botão tradicional</span><span class="sxs-lookup"><span data-stu-id="1ff3f-143">Traditional button</span></span>

![Botão tradicional](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="1ff3f-145">Este exemplo mostra um botão no tradicional estilo 2D.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="1ff3f-146">O estado de cada entrada tem uma profundidade ligeiramente diferente e a propriedade de animação.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="1ff3f-147">Outros exemplos</span><span class="sxs-lookup"><span data-stu-id="1ff3f-147">Other examples</span></span>

<span data-ttu-id="1ff3f-148">![Botão de ação](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="1ff3f-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="1ff3f-149">*Botão de ação*</span><span class="sxs-lookup"><span data-stu-id="1ff3f-149">*Push button*</span></span>
<br>
<span data-ttu-id="1ff3f-150">![Objeto de vida real](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="1ff3f-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="1ff3f-151">*Objeto da vida real*</span><span class="sxs-lookup"><span data-stu-id="1ff3f-151">*Real life object*</span></span>

<span data-ttu-id="1ff3f-152">Com o HoloLens, você pode aproveitar o espaço físico.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="1ff3f-153">Imagine um botão de envio por push holographic em uma parede físico.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="1ff3f-154">Ou tal uma xícara de café em uma tabela real?</span><span class="sxs-lookup"><span data-stu-id="1ff3f-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="1ff3f-155">Usando modelos 3D importados do software de modelagem, podemos criar um objeto Interagível que se parece com o objeto da vida real.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="1ff3f-156">Uma vez que ele é um objeto digital, podemos adicionar interações mágicas a ele.</span><span class="sxs-lookup"><span data-stu-id="1ff3f-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="1ff3f-157">Objeto interagível no Kit de ferramentas de realidade mista</span><span class="sxs-lookup"><span data-stu-id="1ff3f-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="1ff3f-158">Você pode encontrar o [exemplos de Interactable do objeto no Kit de ferramentas de realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="1ff3f-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="1ff3f-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ff3f-159">See also</span></span>
* [<span data-ttu-id="1ff3f-160">Botão pressable no Kit de ferramentas de realidade misturada-Unity</span><span class="sxs-lookup"><span data-stu-id="1ff3f-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="1ff3f-161">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="1ff3f-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1ff3f-162">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="1ff3f-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)

---
title: Objeto que interage
description: Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D. No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, UX
ms.openlocfilehash: 87979d2d7b7de4a384b42b5059239e9b830a92e8
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723225"
---
# <a name="interactable-object"></a><span data-ttu-id="01969-105">Objeto que interage</span><span class="sxs-lookup"><span data-stu-id="01969-105">Interactable object</span></span>

![Objetos Interactible](images/UX/UX_Hero_Interactable.jpg)

<span data-ttu-id="01969-107">Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D.</span><span class="sxs-lookup"><span data-stu-id="01969-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="01969-108">No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração.</span><span class="sxs-lookup"><span data-stu-id="01969-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="01969-109">Qualquer coisa pode ser um objeto que possa ser **interagindo** que dispara um evento.</span><span class="sxs-lookup"><span data-stu-id="01969-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="01969-110">Um objeto de interação pode ser representado como qualquer coisa de uma xícara de café na mesa até um balão flutuante no ar.</span><span class="sxs-lookup"><span data-stu-id="01969-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="01969-111">Ainda fazemos uso de botões tradicionais em determinadas situações, como na interface do usuário da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="01969-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="01969-112">A representação visual do botão depende do contexto.</span><span class="sxs-lookup"><span data-stu-id="01969-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="01969-113">Propriedades importantes do objeto que interage</span><span class="sxs-lookup"><span data-stu-id="01969-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="01969-114">Indicações visuais</span><span class="sxs-lookup"><span data-stu-id="01969-114">Visual cues</span></span>

<span data-ttu-id="01969-115">As indicações visuais são indicações de sensor recebidas pelo olho na forma de luz e processadas pelo sistema visual durante a percepção visual.</span><span class="sxs-lookup"><span data-stu-id="01969-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="01969-116">Como o sistema visual é dominante em muitas espécies, especialmente nas pessoas, as indicações visuais são uma grande fonte de informações sobre como o mundo é percebido.</span><span class="sxs-lookup"><span data-stu-id="01969-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="01969-117">Como os objetos Holographic são mesclados com o ambiente do mundo real em realidade misturada, pode ser difícil entender de quais objetos você pode interagir.</span><span class="sxs-lookup"><span data-stu-id="01969-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="01969-118">Para qualquer objeto interagindo em sua experiência, é importante fornecer indicações visuais diferenciadas para cada Estado de entrada.</span><span class="sxs-lookup"><span data-stu-id="01969-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="01969-119">Isso ajuda o usuário a entender qual parte da sua experiência é interagir e torna o usuário confiante usando um método de interação consistente.</span><span class="sxs-lookup"><span data-stu-id="01969-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="01969-120">Interações distantes</span><span class="sxs-lookup"><span data-stu-id="01969-120">Far interactions</span></span>

<span data-ttu-id="01969-121">Para todos os objetos que o usuário pode interagir com olhar, Hand Ray e Ray Controller ' s, é recomendável ter uma indicação visual diferente para esses três Estados de entrada:</span><span class="sxs-lookup"><span data-stu-id="01969-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="01969-122">![interactibleobject-padrão](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="01969-123">**Estado padrão (observação)**</span><span class="sxs-lookup"><span data-stu-id="01969-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="01969-124">Estado ocioso padrão do objeto.</span><span class="sxs-lookup"><span data-stu-id="01969-124">Default idle state of the object.</span></span>
    <span data-ttu-id="01969-125">O cursor não está no objeto.</span><span class="sxs-lookup"><span data-stu-id="01969-125">The cursor is not on the object.</span></span> <span data-ttu-id="01969-126">A mão não foi detectada.</span><span class="sxs-lookup"><span data-stu-id="01969-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01969-127">![interactibleobject-direcionados](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="01969-128">**Estado de destino (focalizar)**</span><span class="sxs-lookup"><span data-stu-id="01969-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="01969-129">Quando o objeto é direcionado com o cursor olhar, a proximidade do dedo ou o ponteiro do controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="01969-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="01969-130">O cursor está no objeto.</span><span class="sxs-lookup"><span data-stu-id="01969-130">The cursor is on the object.</span></span> <span data-ttu-id="01969-131">A mão foi detectada, pronto.</span><span class="sxs-lookup"><span data-stu-id="01969-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01969-132">![interactibleobject-](images/interactibleobject-states-pressed.jpg) pressionadas</span><span class="sxs-lookup"><span data-stu-id="01969-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="01969-133">**Estado pressionado**</span><span class="sxs-lookup"><span data-stu-id="01969-133">**Pressed state**</span></span><br>
        <span data-ttu-id="01969-134">Quando o objeto for pressionado com um gesto de toque de ar, pressione o botão de seleção de dedo ou controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="01969-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="01969-135">O cursor está no objeto.</span><span class="sxs-lookup"><span data-stu-id="01969-135">The cursor is on the object.</span></span> <span data-ttu-id="01969-136">A mão é detectada, o ar está tocado.</span><span class="sxs-lookup"><span data-stu-id="01969-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="01969-137">Você pode usar técnicas como realce ou dimensionamento para fornecer indicações visuais para o estado de entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="01969-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="01969-138">Em realidade misturada, você pode encontrar os exemplos de visualização de diferentes Estados de entrada no menu iniciar e com os botões da barra de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="01969-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="01969-139">Veja como esses Estados se parecem em um **botão de Holographic**:</span><span class="sxs-lookup"><span data-stu-id="01969-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="01969-140">![interactibleobject-padrão](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="01969-141">**Estado padrão (observação)**</span><span class="sxs-lookup"><span data-stu-id="01969-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01969-142">![interactibleobject-direcionados](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="01969-143">**Estado de destino (focalizar)**</span><span class="sxs-lookup"><span data-stu-id="01969-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01969-144">![interactibleobject-](images/MRTK_InteractableState-pressed.jpg) pressionadas</span><span class="sxs-lookup"><span data-stu-id="01969-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="01969-145">**Estado pressionado**</span><span class="sxs-lookup"><span data-stu-id="01969-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="01969-146">Interações próximas (diretas)</span><span class="sxs-lookup"><span data-stu-id="01969-146">Near interactions (direct)</span></span> 

<span data-ttu-id="01969-147">O HoloLens 2 dá suporte à entrada de controle de mão articulada que permite interagir com objetos.</span><span class="sxs-lookup"><span data-stu-id="01969-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="01969-148">Sem comentários haptics e percepção de profundidade perfeita, às vezes pode ser difícil dizer de quanto longe sua mão é de um objeto ou se você está tocando.</span><span class="sxs-lookup"><span data-stu-id="01969-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="01969-149">É importante fornecer indicações visuais suficientes para comunicar o estado do objeto e, em particular, o estado de suas mãos em relação a esse objeto.</span><span class="sxs-lookup"><span data-stu-id="01969-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="01969-150">Use comentários visuais para comunicar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="01969-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="01969-151">**Padrão (observação)** : estado ocioso padrão do objeto.</span><span class="sxs-lookup"><span data-stu-id="01969-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="01969-152">**Focalizar**: quando uma mão está perto de um holograma, alterar elementos visuais para se comunicar que essa mão está direcionando o holograma.</span><span class="sxs-lookup"><span data-stu-id="01969-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="01969-153">**Distância e ponto de interação**: à medida que a mão se aproxima de um holograma, o design de comentários para comunicar o ponto de interação projetado, bem como a distância do objeto que o dedo é</span><span class="sxs-lookup"><span data-stu-id="01969-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="01969-154">**Contato começa**: alterar visuais (claro, cor) para comunicar que um toque ocorreu</span><span class="sxs-lookup"><span data-stu-id="01969-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="01969-155">**Segure**: alterar visuais (Light, Color) quando o objeto for Segure</span><span class="sxs-lookup"><span data-stu-id="01969-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="01969-156">**Contatos termina**: alterar visuais (claro, cor) quando o toque terminar</span><span class="sxs-lookup"><span data-stu-id="01969-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="01969-157">![focalizar (longe)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="01969-158">**Focalizar (longe)**</span><span class="sxs-lookup"><span data-stu-id="01969-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="01969-159">Realce com base na proximidade da mão.</span><span class="sxs-lookup"><span data-stu-id="01969-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="01969-160">![em foco (próximo)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="01969-161">**Focalizar (próximo)**</span><span class="sxs-lookup"><span data-stu-id="01969-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="01969-162">Realçar alterações de tamanho com base na distância para a mão.</span><span class="sxs-lookup"><span data-stu-id="01969-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="01969-163">![toque/pressione](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="01969-164">**Toque/pressione**</span><span class="sxs-lookup"><span data-stu-id="01969-164">**Touch / press**</span></span><br>
        <span data-ttu-id="01969-165">Comentários sobre áudio visual Plus.</span><span class="sxs-lookup"><span data-stu-id="01969-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="01969-166">![Segure](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="01969-167">**Compreendi**</span><span class="sxs-lookup"><span data-stu-id="01969-167">**Grasp**</span></span><br>
        <span data-ttu-id="01969-168">Comentários sobre áudio visual Plus.</span><span class="sxs-lookup"><span data-stu-id="01969-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="01969-169">Um [botão no HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) é um exemplo de como os diferentes Estados de interação de entrada são visualizados:</span><span class="sxs-lookup"><span data-stu-id="01969-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="01969-170">![Padrão](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="01969-171">**Padrão**</span><span class="sxs-lookup"><span data-stu-id="01969-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="01969-172">![](images/640px-interactibleobject-pressablebutton-hover.jpg) em foco</span><span class="sxs-lookup"><span data-stu-id="01969-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="01969-173">**Operação**</span><span class="sxs-lookup"><span data-stu-id="01969-173">**Hover**</span></span><br>
        <span data-ttu-id="01969-174">Revelar um efeito de iluminação baseada em proximidade.</span><span class="sxs-lookup"><span data-stu-id="01969-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="01969-175">![Tocar](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="01969-176">**Tocar**</span><span class="sxs-lookup"><span data-stu-id="01969-176">**Touch**</span></span><br>
        <span data-ttu-id="01969-177">Mostrar efeito de ondulação.</span><span class="sxs-lookup"><span data-stu-id="01969-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="01969-178">![Pressione](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="01969-179">**Pressione**</span><span class="sxs-lookup"><span data-stu-id="01969-179">**Press**</span></span><br>
        <span data-ttu-id="01969-180">Mova a placa frontal.</span><span class="sxs-lookup"><span data-stu-id="01969-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="01969-181">A indicação visual "anel" no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="01969-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="01969-182">No HoloLens 2, há uma indicação visual adicional que pode ajudar a percepção de profundidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="01969-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="01969-183">Um anel próximo a ele é exibido e escala verticalmente conforme o alcance fica mais próximo do objeto.</span><span class="sxs-lookup"><span data-stu-id="01969-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="01969-184">O anel, eventualmente, convergi em um ponto quando o estado pressionado é atingido.</span><span class="sxs-lookup"><span data-stu-id="01969-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="01969-185">Essa unificação Visual ajuda o usuário a entender a distância deles do objeto.</span><span class="sxs-lookup"><span data-stu-id="01969-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="01969-186">*Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa delimitadora*</span><span class="sxs-lookup"><span data-stu-id="01969-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="01969-187">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="01969-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="01969-188">![os comentários visuais sobre a proximidade](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="01969-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="01969-189">Indicações de áudio</span><span class="sxs-lookup"><span data-stu-id="01969-189">Audio cues</span></span>

<span data-ttu-id="01969-190">Para interações diretas, os comentários de áudio adequados podem melhorar drasticamente a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="01969-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="01969-191">Use comentários de áudio para comunicar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="01969-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="01969-192">**Contato começa**: Tocar som quando o toque começar</span><span class="sxs-lookup"><span data-stu-id="01969-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="01969-193">**Contatos termina**: Tocar som no ponto de toque</span><span class="sxs-lookup"><span data-stu-id="01969-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="01969-194">**Captura começa**: reproduzir som quando a captura começar</span><span class="sxs-lookup"><span data-stu-id="01969-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="01969-195">**Captações de captura**: Tocar som quando a captura terminar</span><span class="sxs-lookup"><span data-stu-id="01969-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="01969-196">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="01969-196">Voice commanding</span></span><br>
        <span data-ttu-id="01969-197">Para qualquer objeto que interaja, é importante dar suporte a opções de interação alternativas.</span><span class="sxs-lookup"><span data-stu-id="01969-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="01969-198">Por padrão, recomendamos que os [comandos de voz](voice-design.md) tenham suporte para todos os objetos que estiverem interagindo.</span><span class="sxs-lookup"><span data-stu-id="01969-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="01969-199">Para melhorar a descoberta, você também pode fornecer uma dica de ferramenta durante o estado de foco.</span><span class="sxs-lookup"><span data-stu-id="01969-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="01969-200">*Imagem: dica de ferramenta para o comando de voz*</span><span class="sxs-lookup"><span data-stu-id="01969-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comando de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="01969-202">Recomendações de dimensionamento</span><span class="sxs-lookup"><span data-stu-id="01969-202">Sizing recommendations</span></span> 

<span data-ttu-id="01969-203">Para garantir que todos os objetos interajantes possam ser facilmente tocadas pelos usuários, recomendamos que você verifique se o que pode interagir atende a um tamanho mínimo (o ângulo visual geralmente medido em graus de arco Visual) com base na distância em que ele é colocado do usuário.</span><span class="sxs-lookup"><span data-stu-id="01969-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="01969-204">O ângulo visual se baseia na distância entre os olhos do usuário e o objeto e permanece constante, enquanto o tamanho físico do destino pode mudar à medida que a distância do usuário é alterada.</span><span class="sxs-lookup"><span data-stu-id="01969-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="01969-205">Para determinar o tamanho físico necessário de um objeto com base na distância do usuário, tente usar uma calculadora de ângulo visual como [esta](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="01969-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="01969-206">Abaixo estão as recomendações para tamanhos mínimos de conteúdo de interação.</span><span class="sxs-lookup"><span data-stu-id="01969-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="01969-207">Tamanho de destino para interação direta</span><span class="sxs-lookup"><span data-stu-id="01969-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="01969-208">Distância</span><span class="sxs-lookup"><span data-stu-id="01969-208">Distance</span></span> | <span data-ttu-id="01969-209">Ângulo de exibição</span><span class="sxs-lookup"><span data-stu-id="01969-209">Viewing angle</span></span> | <span data-ttu-id="01969-210">Size</span><span class="sxs-lookup"><span data-stu-id="01969-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="01969-211">45cm</span><span class="sxs-lookup"><span data-stu-id="01969-211">45cm</span></span>  | <span data-ttu-id="01969-212">Não é menor que 2 °</span><span class="sxs-lookup"><span data-stu-id="01969-212">no smaller than 2°</span></span> | <span data-ttu-id="01969-213">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="01969-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="01969-214">![tamanho de destino para interação direta](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="01969-215">*Tamanho de destino para interação direta*</span><span class="sxs-lookup"><span data-stu-id="01969-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="01969-216">Tamanho de destino para botões</span><span class="sxs-lookup"><span data-stu-id="01969-216">Target size for buttons</span></span>

<span data-ttu-id="01969-217">Ao criar botões para interação direta, recomendamos um tamanho mínimo maior de 3,2 x 3,2 cm para garantir que haja espaço suficiente para conter um ícone e potencialmente algum texto.</span><span class="sxs-lookup"><span data-stu-id="01969-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="01969-218">Distância</span><span class="sxs-lookup"><span data-stu-id="01969-218">Distance</span></span> | <span data-ttu-id="01969-219">Tamanho mínimo</span><span class="sxs-lookup"><span data-stu-id="01969-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="01969-220">45cm</span><span class="sxs-lookup"><span data-stu-id="01969-220">45cm</span></span>  | <span data-ttu-id="01969-221">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="01969-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="01969-222">![tamanho do destino para os botões](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="01969-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="01969-223">*Tamanho do destino dos botões*</span><span class="sxs-lookup"><span data-stu-id="01969-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="01969-224">Tamanho de destino para interação de olhar</span><span class="sxs-lookup"><span data-stu-id="01969-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="01969-225">Distância</span><span class="sxs-lookup"><span data-stu-id="01969-225">Distance</span></span> | <span data-ttu-id="01969-226">Ângulo de exibição</span><span class="sxs-lookup"><span data-stu-id="01969-226">Viewing angle</span></span> | <span data-ttu-id="01969-227">Size</span><span class="sxs-lookup"><span data-stu-id="01969-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="01969-228">m</span><span class="sxs-lookup"><span data-stu-id="01969-228">2m</span></span>  | <span data-ttu-id="01969-229">Não é menor que 1 °</span><span class="sxs-lookup"><span data-stu-id="01969-229">no smaller than 1°</span></span> | <span data-ttu-id="01969-230">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="01969-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="01969-231">![o tamanho de destino para a interação de olhar de raio ou para a direita](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="01969-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="01969-232">*Tamanho de destino para interação de olhar*</span><span class="sxs-lookup"><span data-stu-id="01969-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="01969-233">Objeto de interação no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="01969-233">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="01969-234">No **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , você pode usar o script de forma a [**interagir**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para fazer com que os objetos respondam a vários tipos de Estados de interação de entrada.</span><span class="sxs-lookup"><span data-stu-id="01969-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="01969-235">Ele dá suporte a vários tipos de temas que permitem definir estados visuais controlando Propriedades de objeto, como cor, tamanho, material e sombreador.</span><span class="sxs-lookup"><span data-stu-id="01969-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="01969-236">Interagir</span><span class="sxs-lookup"><span data-stu-id="01969-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="01969-237">Botão</span><span class="sxs-lookup"><span data-stu-id="01969-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="01969-238">Exemplos de interação de mão cena</span><span class="sxs-lookup"><span data-stu-id="01969-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="01969-239">O sombreador padrão de MixedRealityToolkit fornece várias opções, como a **luz de proximidade** que ajuda você a criar indicações visuais e de áudio.</span><span class="sxs-lookup"><span data-stu-id="01969-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="01969-240">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="01969-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="01969-241">Veja também</span><span class="sxs-lookup"><span data-stu-id="01969-241">See also</span></span>

* [<span data-ttu-id="01969-242">Cursores</span><span class="sxs-lookup"><span data-stu-id="01969-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="01969-243">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="01969-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="01969-244">Botão</span><span class="sxs-lookup"><span data-stu-id="01969-244">Button</span></span>](button.md)
* [<span data-ttu-id="01969-245">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="01969-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="01969-246">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="01969-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="01969-247">Manipulação</span><span class="sxs-lookup"><span data-stu-id="01969-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="01969-248">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="01969-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="01969-249">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="01969-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="01969-250">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="01969-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="01969-251">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="01969-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="01969-252">Teclado</span><span class="sxs-lookup"><span data-stu-id="01969-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="01969-253">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="01969-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="01969-254">Slate</span><span class="sxs-lookup"><span data-stu-id="01969-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="01969-255">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="01969-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="01969-256">Sombreador</span><span class="sxs-lookup"><span data-stu-id="01969-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="01969-257">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="01969-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="01969-258">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="01969-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="01969-259">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="01969-259">Surface magnetism</span></span>](surface-magnetism.md)

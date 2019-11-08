---
title: Apontar e confirmar com as mãos
description: Visão geral do modelo de entrada de apontar e confirmar
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade misturada, interação, design, HoloLens, mãos, à distância, apontar e confirmar
ms.openlocfilehash: e454b7f26b402d5c168323762865d10f7feb8a17
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437663"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="6385b-104">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="6385b-104">Point and commit with hands</span></span>

<span data-ttu-id="6385b-105">Apontar e confirmar com as mãos é um modelo de entrada que permite aos usuários focalizar, selecionar e manipular objetos 3D e conteúdo 2D que estão fora do alcance.</span><span class="sxs-lookup"><span data-stu-id="6385b-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects that are out of reach.</span></span> <span data-ttu-id="6385b-106">Essa técnica de interação "à distância" é exclusiva da realidade misturada e não é uma forma natural de interação humana com o mundo real.</span><span class="sxs-lookup"><span data-stu-id="6385b-106">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally interact with the real world.</span></span> <span data-ttu-id="6385b-107">Por exemplo, no filme de super-heróis *X-Men*, o personagem [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) é capaz de manipular um objeto à distância com suas mãos.</span><span class="sxs-lookup"><span data-stu-id="6385b-107">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="6385b-108">Isso não é algo que os humanos podem fazer na realidade.</span><span class="sxs-lookup"><span data-stu-id="6385b-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="6385b-109">No HoloLens (RA) e na MR (Realidade Misturada), nós equipamos os usuários com esse poder mágico, quebrando a restrição física do mundo real para não somente permitir uma experiência divertida com o conteúdo holográfico, como também tornar as interações do usuário mais eficazes e eficientes.</span><span class="sxs-lookup"><span data-stu-id="6385b-109">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic content but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="6385b-110">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="6385b-110">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="6385b-111"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="6385b-111"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="6385b-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6385b-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="6385b-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6385b-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="6385b-114"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="6385b-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="6385b-115">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="6385b-115">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="6385b-116">❌ Sem suporte</span><span class="sxs-lookup"><span data-stu-id="6385b-116">❌ Not supported</span></span></td>
     <td><span data-ttu-id="6385b-117">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="6385b-117">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="6385b-118">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="6385b-118">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="6385b-119">O modelo _“Apontar e confirmar com as mãos”_ é um dos novos recursos que utiliza o novo sistema articulado de acompanhamento com as mãos.</span><span class="sxs-lookup"><span data-stu-id="6385b-119">_"Point and commit with hands"_ is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="6385b-120">Esse modelo de entrada também é o modelo de entrada primário em headsets imersivos com o uso de controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="6385b-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="6385b-121">Raios de mão</span><span class="sxs-lookup"><span data-stu-id="6385b-121">Hand rays</span></span>

<span data-ttu-id="6385b-122">No HoloLens 2, criamos um raio de mão que é disparado do centro da palma da mão do usuário.</span><span class="sxs-lookup"><span data-stu-id="6385b-122">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="6385b-123">Este raio é tratado como uma extensão da mão.</span><span class="sxs-lookup"><span data-stu-id="6385b-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="6385b-124">Um cursor em forma de rosca é anexado ao final do raio para indicar o local onde o raio cruza com um objeto-alvo.</span><span class="sxs-lookup"><span data-stu-id="6385b-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="6385b-125">O objeto sobre o cursor pode receber comandos gestuais da mão.</span><span class="sxs-lookup"><span data-stu-id="6385b-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="6385b-126">Esse comando gestual básico é disparado usando o polegar e o dedo indicador para executar uma ação de fechar e abrir os dedos indicador e polegar.</span><span class="sxs-lookup"><span data-stu-id="6385b-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="6385b-127">Usando o raio de mão para apontar e a ação de fechar e abrir os dedos indicador e polegar para confirmar, os usuários podem ativar um botão ou um hiperlink.</span><span class="sxs-lookup"><span data-stu-id="6385b-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="6385b-128">Com gestos mais complexos, os usuários podem navegar pelo conteúdo da Web e manipular objetos 3D à distância.</span><span class="sxs-lookup"><span data-stu-id="6385b-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="6385b-129">O design visual do raio de mão também deve reagir com esses estados de apontar e confirmar, conforme descrito e mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="6385b-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="6385b-130">![apontar com raios de mão](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-130">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="6385b-131">**Estado de apontar**</span><span class="sxs-lookup"><span data-stu-id="6385b-131">**Pointing state**</span></span><br>
        <span data-ttu-id="6385b-132">Ao *apontar*, o raio é mostrado como uma linha tracejada e o cursor assume a forma de uma rosca.</span><span class="sxs-lookup"><span data-stu-id="6385b-132">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6385b-133">![confirmar com raios de mão](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-133">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="6385b-134">**Estado de confirmação**</span><span class="sxs-lookup"><span data-stu-id="6385b-134">**Commit state**</span></span><br>
        <span data-ttu-id="6385b-135">Ao *confirmar*, o raio se transforma em uma linha sólida e o cursor se reduz a um ponto.</span><span class="sxs-lookup"><span data-stu-id="6385b-135">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a><span data-ttu-id="6385b-136">Transição entre próximo e distante</span><span class="sxs-lookup"><span data-stu-id="6385b-136">Transition between near and far</span></span>

<span data-ttu-id="6385b-137">Em vez de usar gestos específicos, como apontar com o dedo indicador, para direcionar o raio, projetamos o raio de modo a sair do centro da palma da mão, liberando e reservando os cinco dedos para gestos mais manipulativos, como pinçar e segurar.</span><span class="sxs-lookup"><span data-stu-id="6385b-137">Instead of using specific gestures, such as "pointing with index finger", to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="6385b-138">Com esse design, criamos um só modelo mental – o mesmo conjunto de gestos de mão é usado para uma interação próxima e distante.</span><span class="sxs-lookup"><span data-stu-id="6385b-138">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="6385b-139">Você pode usar o mesmo gesto de captura para manipular objetos em distâncias diferentes.</span><span class="sxs-lookup"><span data-stu-id="6385b-139">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="6385b-140">A invocação dos raios é automática e baseada na proximidade, conforme demonstrado a seguir:</span><span class="sxs-lookup"><span data-stu-id="6385b-140">The invocation of the rays is automatic and proximity based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="6385b-141">![Manipulação próxima](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-141">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="6385b-142">**Manipulação próxima**</span><span class="sxs-lookup"><span data-stu-id="6385b-142">**Near manipulation**</span></span><br>
        <span data-ttu-id="6385b-143">Quando um objeto está dentro da distância de alcance do braço (aproximadamente 50 cm), os raios são desativados automaticamente, incentivando a interação próxima.</span><span class="sxs-lookup"><span data-stu-id="6385b-143">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6385b-144">![Manipulação distante](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-144">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="6385b-145">**Manipulação distante**</span><span class="sxs-lookup"><span data-stu-id="6385b-145">**Far manipulation**</span></span><br>
        <span data-ttu-id="6385b-146">Quando o objeto está mais distante do que 50 cm, os raios são ativados.</span><span class="sxs-lookup"><span data-stu-id="6385b-146">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="6385b-147">A transição deve ser simples e direta.</span><span class="sxs-lookup"><span data-stu-id="6385b-147">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="6385b-148">Interação do slate 2D</span><span class="sxs-lookup"><span data-stu-id="6385b-148">2D slate interaction</span></span>

<span data-ttu-id="6385b-149">Um slate 2D é um contêiner holográfico que hospeda o conteúdo do aplicativo 2D, assim como um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="6385b-149">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="6385b-150">O conceito de design da interação distante com um slate 2D é usar os raios de mão para focalizar e fechar e abrir os dedos indicador e polegar para selecionar.</span><span class="sxs-lookup"><span data-stu-id="6385b-150">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="6385b-151">Após focalizar com um raio de mão, os usuários podem fechar e abrir os dedos indicador e polegar para disparar um hiperlink ou um botão.</span><span class="sxs-lookup"><span data-stu-id="6385b-151">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="6385b-152">Eles podem usar uma mão para "fechar e abrir os dedos indicador e polegar" para rolar o conteúdo de um slate para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="6385b-152">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="6385b-153">O movimento relativo do uso das duas mãos para fechar e abrir os dedos indicador e polegar e arrastar pode aumentar e diminuir o zoom do conteúdo do slate.</span><span class="sxs-lookup"><span data-stu-id="6385b-153">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="6385b-154">Focalizar o raio de mão nos cantos e bordas revela a funcionalidade de manipulação mais próxima.</span><span class="sxs-lookup"><span data-stu-id="6385b-154">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="6385b-155">Por meio das funcionalidades de manipulação do tipo "segurar e arrastar", os usuários podem realizar o dimensionamento uniforme utilizando as funcionalidades de canto e refluir o slate utilizando as funcionalidades de borda.</span><span class="sxs-lookup"><span data-stu-id="6385b-155">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="6385b-156">Ao segurar e arrastar a barra holográfica na parte superior do slate 2D, os usuários podem mover todo o slate.</span><span class="sxs-lookup"><span data-stu-id="6385b-156">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="6385b-157">![Clique de interação do slate 2D](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-157">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="6385b-158">**Clicar**</span><span class="sxs-lookup"><span data-stu-id="6385b-158">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6385b-159">![Rolagem de interação do slate 2D](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-159">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="6385b-160">**Rolar**</span><span class="sxs-lookup"><span data-stu-id="6385b-160">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6385b-161">![Zoom de interação do slate 2D](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-161">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="6385b-162">**Aplicar zoom**</span><span class="sxs-lookup"><span data-stu-id="6385b-162">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="6385b-163">**Para manipular o slate 2D**</span><span class="sxs-lookup"><span data-stu-id="6385b-163">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="6385b-164">Os usuários apontam o raio de mão para os cantos ou bordas para revelar a funcionalidade de manipulação mais próxima.</span><span class="sxs-lookup"><span data-stu-id="6385b-164">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="6385b-165">Aplicando um gesto de manipulação na funcionalidade, os usuários podem realizar o dimensionamento uniforme utilizando a funcionalidade de canto e podem refluir o slate utilizando a funcionalidade de borda.</span><span class="sxs-lookup"><span data-stu-id="6385b-165">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="6385b-166">Aplicando um gesto de manipulação na barra holográfica na parte superior do slate 2D, os usuários podem mover todo o slate.</span><span class="sxs-lookup"><span data-stu-id="6385b-166">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>


<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="6385b-167">Manipulação de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="6385b-167">3D object manipulation</span></span>

<span data-ttu-id="6385b-168">Na manipulação direta, há duas maneiras de os usuários manipularem objetos 3D: a manipulação baseada em funcionalidade e a manipulação não baseada em funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="6385b-168">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="6385b-169">No modelo de apontar e confirmar, os usuários podem realizar exatamente as mesmas tarefas utilizando os raios de mão.</span><span class="sxs-lookup"><span data-stu-id="6385b-169">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="6385b-170">Nenhum aprendizado adicional é necessário.</span><span class="sxs-lookup"><span data-stu-id="6385b-170">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="6385b-171">Manipulação baseada em funcionalidade</span><span class="sxs-lookup"><span data-stu-id="6385b-171">Affordance-based manipulation</span></span>
<span data-ttu-id="6385b-172">Os usuários podem usar os raios de mão para apontar e revelar a caixa delimitadora e as funcionalidades de manipulação.</span><span class="sxs-lookup"><span data-stu-id="6385b-172">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="6385b-173">Os usuários podem aplicar o gesto de manipulação na caixa delimitadora para mover todo o objeto, nas funcionalidades de borda para girá-lo e nas funcionalidades de canto para dimensioná-lo de maneira uniforme.</span><span class="sxs-lookup"><span data-stu-id="6385b-173">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="6385b-174">![Movimento a distância da manipulação de objetos 3D](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-174">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="6385b-175">**Mover**</span><span class="sxs-lookup"><span data-stu-id="6385b-175">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6385b-176">![Rotação a distância da manipulação de objetos 3D](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-176">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="6385b-177">**Girar**</span><span class="sxs-lookup"><span data-stu-id="6385b-177">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6385b-178">![Escala a distância da manipulação de objetos 3D](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-178">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="6385b-179">**Escala**</span><span class="sxs-lookup"><span data-stu-id="6385b-179">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="6385b-180">Manipulação não baseada em funcionalidade</span><span class="sxs-lookup"><span data-stu-id="6385b-180">Non-affordance based manipulation</span></span>
<span data-ttu-id="6385b-181">Os usuários apontam com os raios de mão para revelar a caixa delimitadora e aplicam gestos de manipulação diretamente nela.</span><span class="sxs-lookup"><span data-stu-id="6385b-181">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="6385b-182">Com uma mão, a translação e a rotação do objeto estão associadas ao movimento e à orientação da mão.</span><span class="sxs-lookup"><span data-stu-id="6385b-182">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="6385b-183">Com as duas mãos, os usuários podem transladar, dimensionar e girar o objeto de acordo com os movimentos relativos das duas mãos.</span><span class="sxs-lookup"><span data-stu-id="6385b-183">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="6385b-184">Gestos instintuais</span><span class="sxs-lookup"><span data-stu-id="6385b-184">Instinctual gestures</span></span>
<span data-ttu-id="6385b-185">O conceito de gestos instintuais para apontar e confirmar é semelhante ao da [manipulação direta com as mãos](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="6385b-185">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="6385b-186">Os gestos que os usuários realizam em um objeto 3D são orientados pelo design de funcionalidades da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="6385b-186">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="6385b-187">Por exemplo, um ponto de controle pequeno pode motivar os usuários a pinçar com o polegar e o dedo indicador, enquanto que, para um objeto maior, os usuários podem preferir segurar usando todos os cinco dedos.</span><span class="sxs-lookup"><span data-stu-id="6385b-187">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="6385b-188">![gestos instintivos para objeto pequeno](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-188">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="6385b-189">**Objeto pequeno**</span><span class="sxs-lookup"><span data-stu-id="6385b-189">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6385b-190">![gestos instintivos para objeto médio](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-190">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="6385b-191">**Objeto médio**</span><span class="sxs-lookup"><span data-stu-id="6385b-191">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6385b-192">![gestos instintivos para objeto grande](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-192">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="6385b-193">**Objeto grande**</span><span class="sxs-lookup"><span data-stu-id="6385b-193">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="6385b-194">Design simétrico entre os controladores de mão e DoF 6</span><span class="sxs-lookup"><span data-stu-id="6385b-194">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="6385b-195">O conceito de apontar e confirmar para interações à distância foi inicialmente criado e definido para o MRP (Portal de Realidade Misturada), no qual um usuário usa um headset imersivo e interage com objetos 3D por meio de controladores de movimentos.</span><span class="sxs-lookup"><span data-stu-id="6385b-195">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="6385b-196">Os controladores de movimento disparam raios para apontar e manipular objetos distantes.</span><span class="sxs-lookup"><span data-stu-id="6385b-196">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="6385b-197">Existem botões nos controladores para confirmar diferentes ações.</span><span class="sxs-lookup"><span data-stu-id="6385b-197">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="6385b-198">Utilizamos o modelo de interação de raios e os anexamos às duas mãos.</span><span class="sxs-lookup"><span data-stu-id="6385b-198">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="6385b-199">Com esse design simétrico, os usuários que estão familiarizados com o MRP não precisarão aprender a usar outro modelo de interação para apontar e manipular à distância quando usarem o HoloLen 2 e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="6385b-199">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="6385b-200">![design simétrico para raios com controladores](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-200">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="6385b-201">**Raios do controlador**</span><span class="sxs-lookup"><span data-stu-id="6385b-201">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6385b-202">![design simétrico para raios com as mãos](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="6385b-202">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="6385b-203">**Raios de mão**</span><span class="sxs-lookup"><span data-stu-id="6385b-203">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="6385b-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6385b-204">See also</span></span>
* [<span data-ttu-id="6385b-205">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="6385b-205">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6385b-206">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="6385b-206">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="6385b-207">Mãos – Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="6385b-207">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6385b-208">Mãos – Gestos</span><span class="sxs-lookup"><span data-stu-id="6385b-208">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="6385b-209">Interações instintivas</span><span class="sxs-lookup"><span data-stu-id="6385b-209">Instinctual interactions</span></span>](interaction-fundamentals.md)
---
title: Menu do lado
description: Os menus à mão permitem que os usuários tragam rapidamente a interface do usuário conectada à mão para funções usadas com frequência. Essas são nossas práticas recomendadas e recomendações para menus à mão.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mão, menu, botão, acesso rápido, layout
ms.openlocfilehash: b4ea7411be22633e82a88d1c91b6b2b1edbea735
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105641"
---
# <a name="hand-menu"></a><span data-ttu-id="45917-105">Menu do lado</span><span class="sxs-lookup"><span data-stu-id="45917-105">Hand menu</span></span>

![Local do ulnar](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="45917-107">Os menus à mão permitem que os usuários tragam rapidamente a interface do usuário conectada à mão para funções usadas com frequência.</span><span class="sxs-lookup"><span data-stu-id="45917-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="45917-108">Veja abaixo as práticas recomendadas que encontramos para os menus à mão.</span><span class="sxs-lookup"><span data-stu-id="45917-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="45917-109">Você também pode encontrar uma cena de exemplo demonstrando o menu à mão em [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span><span class="sxs-lookup"><span data-stu-id="45917-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="45917-110">Práticas recomendadas de comportamento</span><span class="sxs-lookup"><span data-stu-id="45917-110">Behavior best practices</span></span>
<span data-ttu-id="45917-111">**A. Mantenha o número de botões pequenos:** devido à distância de proximidade entre um menu protegido por mão e os olhos, e também a tendência do usuário de se concentrar em uma área Visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), recomendamos mantendo o número de botões pequenos.</span><span class="sxs-lookup"><span data-stu-id="45917-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="45917-112">Com base em nossa exploração, uma coluna com três botões funciona bem, mantendo todo o conteúdo dentro do campo de exibição (FOV), mesmo quando os usuários movem suas mãos para o centro do FOV.</span><span class="sxs-lookup"><span data-stu-id="45917-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="45917-113">**B. Utilize o menu à mão para ação rápida:** gerar um ARM e manter a posição pode facilmente causar fadiga ARM.</span><span class="sxs-lookup"><span data-stu-id="45917-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="45917-114">Use um método protegido por mão para o menu que requer uma pequena interação.</span><span class="sxs-lookup"><span data-stu-id="45917-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="45917-115">Se o seu menu for complexo e exigir tempos de interação estendidos, considere usar o World-Locked ou o corpo bloqueado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="45917-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="45917-116">**C. botão/ângulo do painel:** os menus devem ser contratados em direção ao ressalto oposto e ao meio do cabeçalho: isso permite que uma mudança natural interaja com o menu com o lado oposto e evite qualquer posição de mão estranha ou desconfortável ao tocar botões.</span><span class="sxs-lookup"><span data-stu-id="45917-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="45917-117">**D. considere o suporte a uma operação única ou viva-mão:** não presuma que as mãos do usuário estejam sempre disponíveis.</span><span class="sxs-lookup"><span data-stu-id="45917-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="45917-118">Considere uma ampla gama de contextos quando um ou ambos os Hands não estiverem disponíveis e certifique-se de que suas contas de design para essas situações.</span><span class="sxs-lookup"><span data-stu-id="45917-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="45917-119">Para dar suporte a um menu de mão única, você pode tentar fazer a transição do posicionamento do menu de bloqueio manual para mundo bloqueado quando a mão é invertida (vai para o Palm).</span><span class="sxs-lookup"><span data-stu-id="45917-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="45917-120">Para cenários sem intervenção, considere usar um comando de voz para invocar os botões de menu do lado.</span><span class="sxs-lookup"><span data-stu-id="45917-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="45917-121">**Invocação de duas etapas:** se você usar apenas o Palm-up como um evento para disparar o menu à mão, ele poderá ser exibido acidentalmente quando você não precisar dele (falso-positivo), pois as pessoas movem suas mãos muito intencionalmente (para comunicação e manipulação de objetos) e não intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="45917-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="45917-122">Se você tiver falsos positivos em seu aplicativo, considere adicionar uma etapa adicional além do evento de palmeira para invocar o menu à mão, como dedos totalmente abertos.</span><span class="sxs-lookup"><span data-stu-id="45917-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="45917-123">**F. Evite adicionar botões próximos ao pulso (botão início do sistema):** se os botões do menu à mão estiverem posicionados muito próximos ao botão página inicial, ele poderá ser disparado acidentalmente ao interagir com o menu à mão.</span><span class="sxs-lookup"><span data-stu-id="45917-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="45917-124">**G. testar, testar, testar:** as pessoas têm corpos diferentes, com limites diferentes para conforto e discomfort, etc. Certifique-se de testar seu design e obter comentários de uma variedade de pessoas.</span><span class="sxs-lookup"><span data-stu-id="45917-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="45917-125">Práticas recomendadas de posicionamento do menu à mão</span><span class="sxs-lookup"><span data-stu-id="45917-125">Hand menu placement best practices</span></span>

<span data-ttu-id="45917-126">Na anatomia humana, o ulnar núcleo é um núcleo que é executado próximo ao Bone ulna.</span><span class="sxs-lookup"><span data-stu-id="45917-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="45917-127">O ulna é um Bone longo encontrado no forearm que se estende do cotovelo para o menor dedo.</span><span class="sxs-lookup"><span data-stu-id="45917-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="45917-128">Abaixo estão dois posicionamentos recomendados com base em nossas explorações:</span><span class="sxs-lookup"><span data-stu-id="45917-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="45917-129">![local do ulnar](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="45917-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="45917-130">**A. ulnar dentro do Palm**</span><span class="sxs-lookup"><span data-stu-id="45917-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="45917-131">Essa posição é confiável porque as mãos não se sobrepõem.</span><span class="sxs-lookup"><span data-stu-id="45917-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="45917-132">Isso é essencial para a detecção e o acompanhamento precisos.</span><span class="sxs-lookup"><span data-stu-id="45917-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="45917-133">![local do ulnar](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="45917-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="45917-134">**B. ulnar acima da mão**</span><span class="sxs-lookup"><span data-stu-id="45917-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="45917-135">Esse local é confortável para os usuários porque eles não precisam aumentar seu braço para interagir com o menu à mão.</span><span class="sxs-lookup"><span data-stu-id="45917-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="45917-136">É recomendável colocar os menus **13cm** acima do Palm e alinhar os botões dentro do Palm ulnar.</span><span class="sxs-lookup"><span data-stu-id="45917-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="45917-137">Leia mais sobre o tamanho do botão ideal</span><span class="sxs-lookup"><span data-stu-id="45917-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="45917-138">Por motivos técnicos, recomendamos esse local com uma implementação necessária: o desenvolvedor precisará congelar o menu quando a mão oposta do usuário ficar próxima de interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="45917-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="45917-139">Isso evitará a tremulação de mãos sobrepostas e também permite um direcionamento mais rápido dos botões.</span><span class="sxs-lookup"><span data-stu-id="45917-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="45917-140">As câmeras do HoloLens 2 identificam as mãos com precisão quando são separadas umas das outras.</span><span class="sxs-lookup"><span data-stu-id="45917-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="45917-141">Qualquer mão sobreposta pode fazer com que os menus à mão se afastem do local de ancoragem.</span><span class="sxs-lookup"><span data-stu-id="45917-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="45917-142">Posições de menu que não são recomendadas</span><span class="sxs-lookup"><span data-stu-id="45917-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="45917-143">Fizemos a pesquisa de usuários com diferentes layouts e locais de menus, os locais de menu a seguir **não são recomendados**, encontre os contras de cada estudo abaixo:</span><span class="sxs-lookup"><span data-stu-id="45917-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="45917-144">![](images/AboveArm.gif) do ARM</span><span class="sxs-lookup"><span data-stu-id="45917-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="45917-145">**Acima do ARM**</span><span class="sxs-lookup"><span data-stu-id="45917-145">**Above the arm**</span></span><br>
        <span data-ttu-id="45917-146">1-difícil de manter o acompanhamento de bom alcance</span><span class="sxs-lookup"><span data-stu-id="45917-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="45917-147">2-causa fadiga de usuário devido à posição não natural</span><span class="sxs-lookup"><span data-stu-id="45917-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="45917-148">![de dedos acima](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="45917-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="45917-149">**Acima dos dedos**</span><span class="sxs-lookup"><span data-stu-id="45917-149">**Above fingers**</span></span><br>
        <span data-ttu-id="45917-150">fadiga de 1 mão devido à suspensão por muito tempo</span><span class="sxs-lookup"><span data-stu-id="45917-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="45917-151">problemas de acompanhamento de duas mãos no índice e no meio do dedo</span><span class="sxs-lookup"><span data-stu-id="45917-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="45917-152">![](images/handCenter.gif) de Palm central</span><span class="sxs-lookup"><span data-stu-id="45917-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="45917-153">**Acima do centro-Palm**</span><span class="sxs-lookup"><span data-stu-id="45917-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="45917-154">problemas de acompanhamento de uma mão devido a sobreposição de mãos</span><span class="sxs-lookup"><span data-stu-id="45917-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="45917-155">fadiga de 2 mãos devido à suspensão de mãos por muito tempo para interagir com os menus</span><span class="sxs-lookup"><span data-stu-id="45917-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="45917-156">![superior](images/TopFingerTip.gif) **ponta**</span><span class="sxs-lookup"><span data-stu-id="45917-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="45917-157">problemas de acompanhamento de uma mão</span><span class="sxs-lookup"><span data-stu-id="45917-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="45917-158">fadiga de duas mãos mantendo a postura normal</span><span class="sxs-lookup"><span data-stu-id="45917-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="45917-159">3-problemas ao pressionar os botões com outros dedos por acidente devido ao espaço limitado entre os dedos</span><span class="sxs-lookup"><span data-stu-id="45917-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="45917-160">![de trás do ARM](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="45917-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="45917-161">**Trás do ARM**</span><span class="sxs-lookup"><span data-stu-id="45917-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="45917-162">1-pode disparar o botão página inicial por acidente</span><span class="sxs-lookup"><span data-stu-id="45917-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="45917-163">2-não é uma posição natural ou confortável para os usuários</span><span class="sxs-lookup"><span data-stu-id="45917-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="45917-164">Menu de mão no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="45917-164">Hand menu in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="45917-165">O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e exemplos de cenas para o menu da mão.</span><span class="sxs-lookup"><span data-stu-id="45917-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="45917-166">O script do Solver HandConstraintPalmUp permite que você anexe facilmente qualquer objeto às mãos com várias opções configuráveis.</span><span class="sxs-lookup"><span data-stu-id="45917-166">HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.</span></span>

* [<span data-ttu-id="45917-167">Menu do MRTK com HandConstraint e HandConstraintPalmUp</span><span class="sxs-lookup"><span data-stu-id="45917-167">MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp </span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a><span data-ttu-id="45917-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45917-168">See also</span></span>

* [<span data-ttu-id="45917-169">Cursores</span><span class="sxs-lookup"><span data-stu-id="45917-169">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="45917-170">Raio da mão</span><span class="sxs-lookup"><span data-stu-id="45917-170">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="45917-171">Button</span><span class="sxs-lookup"><span data-stu-id="45917-171">Button</span></span>](button.md)
* [<span data-ttu-id="45917-172">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="45917-172">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="45917-173">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="45917-173">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="45917-174">Manusei</span><span class="sxs-lookup"><span data-stu-id="45917-174">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="45917-175">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="45917-175">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="45917-176">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="45917-176">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="45917-177">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="45917-177">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="45917-178">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="45917-178">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="45917-179">Teclado</span><span class="sxs-lookup"><span data-stu-id="45917-179">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="45917-180">Dessa</span><span class="sxs-lookup"><span data-stu-id="45917-180">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="45917-181">Slate</span><span class="sxs-lookup"><span data-stu-id="45917-181">Slate</span></span>](slate.md)
* [<span data-ttu-id="45917-182">Slider</span><span class="sxs-lookup"><span data-stu-id="45917-182">Slider</span></span>](slider.md)
* [<span data-ttu-id="45917-183">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="45917-183">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="45917-184">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="45917-184">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="45917-185">Magnetism Surface</span><span class="sxs-lookup"><span data-stu-id="45917-185">Surface magnetism</span></span>](surface-magnetism.md)
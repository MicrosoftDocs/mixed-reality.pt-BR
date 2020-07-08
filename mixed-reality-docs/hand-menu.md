---
title: Menu lateral
description: Os menus à mão permitem que os usuários tragam rapidamente a interface do usuário conectada à mão para funções usadas com frequência. Essas são nossas práticas recomendadas e recomendações para menus à mão.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mão, menu, botão, acesso rápido, layout
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061159"
---
# <a name="hand-menu"></a><span data-ttu-id="ea9f7-105">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="ea9f7-105">Hand menu</span></span>

![Local do ulnar](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="ea9f7-107">O menu à mão é um dos padrões mais exclusivos de UX no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-107">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="ea9f7-108">Ele permite que você traga rapidamente a interface do usuário anexada à mão.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-108">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="ea9f7-109">Como ele é acessível a qualquer momento e pode ser mostrado e ocultado facilmente, é ótimo para ações rápidas.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-109">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="ea9f7-110">Você encontrará nossas práticas recomendadas para trabalhar com menus à mão na lista abaixo.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-110">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="ea9f7-111">Você também pode encontrar uma cena de exemplo demonstrando o menu à mão em [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span><span class="sxs-lookup"><span data-stu-id="ea9f7-111">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>


---

## <a name="best-practices"></a><span data-ttu-id="ea9f7-112">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="ea9f7-112">Best practices</span></span>
<span data-ttu-id="ea9f7-113">**Manter o número de botões pequenos**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-113">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="ea9f7-114">Devido à distância de proximidade entre um menu protegido por mão e os olhos, e também a tendência do usuário de se concentrar em uma área Visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), recomendamos manter o número de botões pequenos.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-114">Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="ea9f7-115">Com base em nossa exploração, uma coluna com três botões funciona bem mantendo todo o conteúdo dentro do campo de exibição (FOV) mesmo quando um usuário move suas mãos para o centro do FOV.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-115">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="ea9f7-116">**Utilizar menu à mão para ação rápida**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-116">**Utilize hand menu for quick action**</span></span> 

<span data-ttu-id="ea9f7-117">Elevar um ARM e manter a posição pode facilmente causar fadiga ARM.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-117">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="ea9f7-118">Use um método protegido por mão para o menu que requer uma pequena interação.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-118">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="ea9f7-119">Se o seu menu for complexo e exigir tempos de interação estendidos, considere usar o World-Locked ou o corpo bloqueado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-119">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="ea9f7-120">**Ângulo do botão/painel**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-120">**Button / Panel angle**</span></span>

<span data-ttu-id="ea9f7-121">Os menus devem ser contratados em direção ao colado oposto e ao meio do cabeçalho: isso permite uma movimentação natural para interagir com o menu com o lado oposto e evita qualquer posição de mão estranha ou desconfortável ao tocar nos botões.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-121">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="ea9f7-122">**Considere dar suporte a uma operação única ou viva-mão**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-122">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="ea9f7-123">Não presuma que as mãos do usuário estejam sempre disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-123">Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="ea9f7-124">Considere uma ampla gama de contextos quando um ou ambos os Hands não estiverem disponíveis e certifique-se de que suas contas de design para essas situações.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-124">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="ea9f7-125">Para dar suporte a um menu de mão única, você pode tentar fazer a transição do posicionamento do menu de bloqueio manual para mundo bloqueado quando a mão é invertida (vai para o Palm).</span><span class="sxs-lookup"><span data-stu-id="ea9f7-125">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="ea9f7-126">Para cenários sem intervenção, considere usar um comando de voz para invocar o menu à mão.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-126">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="ea9f7-127">**Evite adicionar botões próximos ao pulso (botão início do sistema)**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-127">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="ea9f7-128">Se os botões do menu à mão forem colocados muito perto do botão página inicial, ele poderá ser disparado acidentalmente ao interagir com o menu da mão.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-128">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="ea9f7-129">Menu à mão com controles de interface do usuário grandes e complexos</span><span class="sxs-lookup"><span data-stu-id="ea9f7-129">Hand menu with large and complex UI controls</span></span>
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="ea9f7-130">É recomendável limitar o número de botões ou controles de interface do usuário em menus anexados à mão.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-130">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="ea9f7-131">Isso ocorre porque a interação estendida com um grande número de elementos da interface do usuário pode causar fadiga ARM.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-131">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="ea9f7-132">Se sua experiência exigir um menu grande, forneça uma maneira fácil para o usuário para o mundo bloquear o menu.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-132">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="ea9f7-133">Uma técnica que recomendamos é bloquear, em seguida, o menu quando a mão cai ou sai do usuário.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-133">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="ea9f7-134">Uma segunda técnica é permitir que o usuário pegue diretamente o menu por outro lado.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-134">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="ea9f7-135">Quando o usuário libera o menu, o menu deve ser bloqueado pelo mundo.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-135">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="ea9f7-136">Dessa forma, um usuário pode interagir com vários elementos de interface de usuário confortavelmente e com confiança em um longo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-136">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="ea9f7-137">Quando o menu estiver bloqueado pelo mundo, certifique-se de fornecer uma maneira de mover o menu e fechar o menu quando ele não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-137">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="ea9f7-138">Torne o menu móvel fornecendo identificadores nos lados ou no início do menu.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-138">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="ea9f7-139">Adicione um botão fechar para permitir que o menu seja fechado.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-139">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="ea9f7-140">Permita que o menu seja anexado novamente à mão quando o usuário se conectar ao usuário.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-140">Allow for the menu to re-attach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="ea9f7-141">Também é recomendável exigir que os usuários gazesm à sua mão para evitar ativações falsas (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="ea9f7-141">We also recommend requiring that the users gazes at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="ea9f7-142">**Menu grande que mostra um problema de usabilidade**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-142">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="ea9f7-143">**Menu suspenso ao lado do mundo**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-143">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="ea9f7-144">**Captura manual & pull para o mundo-bloquear o menu**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-144">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="ea9f7-145">Como evitar a ativação falsa</span><span class="sxs-lookup"><span data-stu-id="ea9f7-145">How to prevent false activation</span></span>

<span data-ttu-id="ea9f7-146">Se você usar apenas o Palm-up como um evento para disparar o menu à mão, ele poderá parecer acidentalmente quando você não precisar dele (falso-positivo), pois as pessoas movem suas mãos de forma intencional (para a manipulação de comunicação e objeto) e não intencionalmente.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-146">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="ea9f7-147">Para reduzir as ativações falsas, adicione uma etapa adicional além do evento de Palm para invocar o menu à mão (como dedos totalmente abertos ou o usuário intencionalmente nuvens em sua mão).</span><span class="sxs-lookup"><span data-stu-id="ea9f7-147">To reduce false activations, add an additional step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="ea9f7-148">**Exigir Palm simples**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-148">**Require Flat Palm**</span></span>

<span data-ttu-id="ea9f7-149">Ao exigir uma mão aberta simples, você pode evitar a ativação falsa que pode ocorrer, pois o usuário manipula objetos ou gestos enquanto se comunica em um ambiente.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-149">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="ea9f7-150">**Exigir olhar**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-150">**Require Gaze**</span></span>

<span data-ttu-id="ea9f7-151">Ao exigir que o usuário olhar a sua mão (com os olhos olhar ou Head olhar), ele impede as ativações falsas devido ao usuário precisar direcionar intencionalmente sua atenção para a mão como uma etapa de ativação secundária (com um limite de distância ajustável usado para permitir o conforto do usuário).</span><span class="sxs-lookup"><span data-stu-id="ea9f7-151">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations due to the user having to intentionally direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="ea9f7-152">Práticas recomendadas de posicionamento do menu à mão</span><span class="sxs-lookup"><span data-stu-id="ea9f7-152">Hand menu placement best practices</span></span>

<span data-ttu-id="ea9f7-153">Na anatomia humana, o ulnar núcleo é um núcleo que é executado próximo ao Bone ulna.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-153">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="ea9f7-154">O ulna é um Bone longo encontrado no forearm que se estende do cotovelo para o menor dedo.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-154">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="ea9f7-155">Abaixo estão dois posicionamentos recomendados com base em nossas explorações:</span><span class="sxs-lookup"><span data-stu-id="ea9f7-155">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="ea9f7-156">![Local do ulnar](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="ea9f7-156">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="ea9f7-157">**A. ulnar dentro do Palm**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-157">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="ea9f7-158">Essa posição é confiável porque as mãos não se sobrepõem.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-158">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="ea9f7-159">Isso é essencial para a detecção e o acompanhamento precisos.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-159">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ea9f7-160">![Local do ulnar](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="ea9f7-160">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="ea9f7-161">**B. ulnar acima da mão**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-161">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="ea9f7-162">Esse local é confortável para os usuários porque eles não precisam aumentar seu braço para interagir com o menu à mão.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-162">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="ea9f7-163">É recomendável colocar os menus **13cm** acima do Palm e alinhar os botões dentro do Palm ulnar.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-163">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="ea9f7-164">Leia mais sobre o tamanho do botão ideal</span><span class="sxs-lookup"><span data-stu-id="ea9f7-164">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="ea9f7-165">Por motivos técnicos, recomendamos esse local com uma implementação necessária: o desenvolvedor precisará congelar o menu quando a mão oposta do usuário ficar próxima de interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-165">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="ea9f7-166">Isso evitará a tremulação de mãos sobrepostas e também permite um direcionamento mais rápido dos botões.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-166">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="ea9f7-167">As câmeras do HoloLens 2 identificam as mãos com precisão quando são separadas umas das outras.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-167">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="ea9f7-168">Qualquer mão sobreposta pode fazer com que os menus à mão se afastem do local de ancoragem.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-168">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="ea9f7-169">Posições de menu que não são recomendadas</span><span class="sxs-lookup"><span data-stu-id="ea9f7-169">Menu positions that are not recommended</span></span>
<span data-ttu-id="ea9f7-170">Fizemos a pesquisa de usuários com diferentes layouts e locais de menus, os locais de menu a seguir **não são recomendados**, encontre os contras de cada estudo abaixo:</span><span class="sxs-lookup"><span data-stu-id="ea9f7-170">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="ea9f7-171">![Acima do ARM](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="ea9f7-171">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="ea9f7-172">**Acima do ARM**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-172">**Above the arm**</span></span><br>
        <span data-ttu-id="ea9f7-173">1-difícil de manter o acompanhamento de bom alcance</span><span class="sxs-lookup"><span data-stu-id="ea9f7-173">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="ea9f7-174">2-causa fadiga de usuário devido à posição não natural</span><span class="sxs-lookup"><span data-stu-id="ea9f7-174">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ea9f7-175">![Acima dos dedos](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="ea9f7-175">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="ea9f7-176">**Acima dos dedos**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-176">**Above fingers**</span></span><br>
        <span data-ttu-id="ea9f7-177">fadiga de 1 mão devido à falta de mão por muito tempo</span><span class="sxs-lookup"><span data-stu-id="ea9f7-177">1 - Hand fatigue due to holding out hand for a long time</span></span><br>
        <span data-ttu-id="ea9f7-178">problemas de acompanhamento de duas mãos no índice e nos dedos centrais</span><span class="sxs-lookup"><span data-stu-id="ea9f7-178">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="ea9f7-179">![Acima do centro do Palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="ea9f7-179">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="ea9f7-180">**Acima do centro-Palm**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-180">**Above-center palm**</span></span><br>
        <span data-ttu-id="ea9f7-181">problemas de acompanhamento de uma mão devido a sobreposição de mãos</span><span class="sxs-lookup"><span data-stu-id="ea9f7-181">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="ea9f7-182">fadiga de 2 mãos devido à suspensão de mãos por muito tempo para interagir com os menus</span><span class="sxs-lookup"><span data-stu-id="ea9f7-182">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ea9f7-183">![Topo ](images/TopFingerTip.gif) **superior** da ponta</span><span class="sxs-lookup"><span data-stu-id="ea9f7-183">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="ea9f7-184">problemas de acompanhamento de uma mão</span><span class="sxs-lookup"><span data-stu-id="ea9f7-184">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="ea9f7-185">fadiga de duas mãos da manutenção da postura normal</span><span class="sxs-lookup"><span data-stu-id="ea9f7-185">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="ea9f7-186">3-problemas ao pressionar os botões com outros dedos por acidente devido ao espaço limitado entre os dedos</span><span class="sxs-lookup"><span data-stu-id="ea9f7-186">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="ea9f7-187">![Trás do ARM](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="ea9f7-187">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="ea9f7-188">**Trás do ARM**</span><span class="sxs-lookup"><span data-stu-id="ea9f7-188">**Back of the arm**</span></span><br>
        <span data-ttu-id="ea9f7-189">1-pode disparar o botão página inicial por acidente</span><span class="sxs-lookup"><span data-stu-id="ea9f7-189">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="ea9f7-190">2-não é uma posição natural ou confortável</span><span class="sxs-lookup"><span data-stu-id="ea9f7-190">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="ea9f7-191">Menu de mão no MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="ea9f7-191">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="ea9f7-192">O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e exemplos de cenas para o menu da mão.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="ea9f7-193">O script do resolvedor HandConstraintPalmUp permite que você anexe qualquer objeto às mãos com várias opções configuráveis.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-193">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="ea9f7-194">Os exemplos de menu do MRTK incluem opções úteis, como o requisito simples de Palm e olhar para impedir a ativação falsa.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-194">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="ea9f7-195">Documentações de menus à mão</span><span class="sxs-lookup"><span data-stu-id="ea9f7-195">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="ea9f7-196">Cenário de exemplo do menu à mão</span><span class="sxs-lookup"><span data-stu-id="ea9f7-196">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="ea9f7-197">Você pode experimentar exemplos de menu à mão no HoloLens 2 com exemplos de MRTK aplicativo de Hub.</span><span class="sxs-lookup"><span data-stu-id="ea9f7-197">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="ea9f7-198">Cena de menu do lado no Hub de exemplos do MRTK</span><span class="sxs-lookup"><span data-stu-id="ea9f7-198">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a><span data-ttu-id="ea9f7-199">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea9f7-199">See also</span></span>

* [<span data-ttu-id="ea9f7-200">Cursores</span><span class="sxs-lookup"><span data-stu-id="ea9f7-200">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="ea9f7-201">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="ea9f7-201">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="ea9f7-202">Botão</span><span class="sxs-lookup"><span data-stu-id="ea9f7-202">Button</span></span>](button.md)
* [<span data-ttu-id="ea9f7-203">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="ea9f7-203">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ea9f7-204">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ea9f7-204">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ea9f7-205">Manipulação</span><span class="sxs-lookup"><span data-stu-id="ea9f7-205">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ea9f7-206">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="ea9f7-206">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="ea9f7-207">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="ea9f7-207">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="ea9f7-208">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="ea9f7-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="ea9f7-209">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="ea9f7-209">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="ea9f7-210">Teclado</span><span class="sxs-lookup"><span data-stu-id="ea9f7-210">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="ea9f7-211">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="ea9f7-211">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="ea9f7-212">Slate</span><span class="sxs-lookup"><span data-stu-id="ea9f7-212">Slate</span></span>](slate.md)
* [<span data-ttu-id="ea9f7-213">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="ea9f7-213">Slider</span></span>](slider.md)
* [<span data-ttu-id="ea9f7-214">Sombreador</span><span class="sxs-lookup"><span data-stu-id="ea9f7-214">Shader</span></span>](shader.md)
* [<span data-ttu-id="ea9f7-215">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="ea9f7-215">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="ea9f7-216">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="ea9f7-216">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="ea9f7-217">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="ea9f7-217">Surface magnetism</span></span>](surface-magnetism.md)

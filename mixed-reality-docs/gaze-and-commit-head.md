---
title: Foco com a cabeça e confirmação
description: Visão geral do modelo de entrada de foco com a cabeça e confirmação
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441090"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="b0b99-104">Foco com a cabeça e confirmação</span><span class="sxs-lookup"><span data-stu-id="b0b99-104">Head-gaze and commit</span></span>
<span data-ttu-id="b0b99-105">_Head-olhar e commit_ é um caso especial do modelo de entrada [olhar e commit](gaze-and-commit.md) que envolve o direcionamento de um objeto com a direção da sua cabeça apontando para a frente (direção da cabeça) e, em seguida, agindo com uma entrada secundária, como o gesto de toque à mão toque ou o comando de voz "Select".</span><span class="sxs-lookup"><span data-stu-id="b0b99-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with the direction of your head pointing forward (head-direction), and then acting on it with a secondary input, such as the hand gesture air tap or the voice command "Select".</span></span> 

## <a name="device-support"></a><span data-ttu-id="b0b99-106">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="b0b99-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b0b99-107"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="b0b99-107"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="b0b99-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0b99-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b0b99-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b0b99-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b0b99-110"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0b99-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b0b99-111">Foco com a cabeça e confirmação</span><span class="sxs-lookup"><span data-stu-id="b0b99-111">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="b0b99-112">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="b0b99-112">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="b0b99-113">✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</span><span class="sxs-lookup"><span data-stu-id="b0b99-113">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="b0b99-114">➕ Opção alternativa</span><span class="sxs-lookup"><span data-stu-id="b0b99-114">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="b0b99-115">Dimensionamento e comentários sobre o alvo</span><span class="sxs-lookup"><span data-stu-id="b0b99-115">Target sizing and feedback</span></span>
<span data-ttu-id="b0b99-116">O vetor olhar de cabeçalho foi mostrado repetidamente para ser usado para direcionamento fino, mas geralmente funciona melhor para direcionamento bruto, adquirindo destinos um pouco maiores.</span><span class="sxs-lookup"><span data-stu-id="b0b99-116">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring somewhat larger targets.</span></span> <span data-ttu-id="b0b99-117">Os tamanhos de destino mínimos de 1 a 1,5 graus permitem ações de usuário bem-sucedidas na maioria dos cenários, embora os destinos de 3 graus geralmente permitam maior velocidade.</span><span class="sxs-lookup"><span data-stu-id="b0b99-117">Minimum target sizes of 1 to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="b0b99-118">Observe que o tamanho do alvo escolhido pelo usuário é efetivamente uma área 2D até mesmo para elementos 3D – qualquer que seja a projeção que esteja voltada para eles deverá ser a área de alvo.</span><span class="sxs-lookup"><span data-stu-id="b0b99-118">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="b0b99-119">Fornecer uma indicação evidente de que um elemento é "ativo" (que o usuário está direcionando para ele) é extremamente útil.</span><span class="sxs-lookup"><span data-stu-id="b0b99-119">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful.</span></span> <span data-ttu-id="b0b99-120">Isso pode incluir tratamentos como efeitos "focalizar" visíveis, realces ou cliques de áudio ou alinhamento claro de um cursor com um elemento.</span><span class="sxs-lookup"><span data-stu-id="b0b99-120">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="b0b99-121">![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b0b99-121">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="b0b99-122">*Tamanho ideal do alvo em uma distância de 2 metros*</span><span class="sxs-lookup"><span data-stu-id="b0b99-122">*Optimal target size at 2 meter distance*</span></span>

<br>

<span data-ttu-id="b0b99-123">![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b0b99-123">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="b0b99-124">*Um exemplo de realce de um objeto direcionado por foco*</span><span class="sxs-lookup"><span data-stu-id="b0b99-124">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="b0b99-125">Posicionamento do alvo</span><span class="sxs-lookup"><span data-stu-id="b0b99-125">Target placement</span></span>
<span data-ttu-id="b0b99-126">Geralmente, os usuários não conseguem localizar elementos da interface do usuário que estão posicionados muito altos ou muito baixos em seu campo de exibição, concentrando a maior parte de sua atenção em áreas em torno do foco principal, que é aproximadamente no nível dos olhos.</span><span class="sxs-lookup"><span data-stu-id="b0b99-126">Users often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="b0b99-127">O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar.</span><span class="sxs-lookup"><span data-stu-id="b0b99-127">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="b0b99-128">Dada a tendência dos usuários de se concentrarem em uma área visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), o agrupamento de elementos de interface do usuário na medida em que eles estejam relacionados conceitualmente pode aproveitar os comportamentos de encadeamento da atenção de item a item conforme um usuário move o foco por uma área.</span><span class="sxs-lookup"><span data-stu-id="b0b99-128">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="b0b99-129">Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.</span><span class="sxs-lookup"><span data-stu-id="b0b99-129">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="b0b99-130">![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b0b99-130">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="b0b99-131">*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="b0b99-131">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="b0b99-132">Como melhorar os comportamentos de direcionamento</span><span class="sxs-lookup"><span data-stu-id="b0b99-132">Improving targeting behaviors</span></span>
<span data-ttu-id="b0b99-133">Se a intenção do usuário para o destino de algo puder ser determinada (ou aproximada), pode ser muito útil aceitar tentativas quase sem erros na interação, como se elas estivessem corretas.</span><span class="sxs-lookup"><span data-stu-id="b0b99-133">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept near miss attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="b0b99-134">Aqui estão alguns métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="b0b99-134">Here are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="b0b99-135">Estabilização do foco com a cabeça ("poços gravitacionais")</span><span class="sxs-lookup"><span data-stu-id="b0b99-135">Head-gaze stabilization ("gravity wells")</span></span>
<span data-ttu-id="b0b99-136">Isso deve ser ativado na maior parte das vezes.</span><span class="sxs-lookup"><span data-stu-id="b0b99-136">This should be turned on most or all of the time.</span></span> <span data-ttu-id="b0b99-137">Essa técnica remove a cabeça natural e as tremulações do pescoço que os usuários podem ter também movimento devido a comportamentos de aparência e fala.</span><span class="sxs-lookup"><span data-stu-id="b0b99-137">This technique removes the natural head and neck jitters that users might have as well movement due to looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="b0b99-138">Algoritmos de vínculo mais próximo</span><span class="sxs-lookup"><span data-stu-id="b0b99-138">Closest link algorithms</span></span>
<span data-ttu-id="b0b99-139">Eles funcionam melhor em áreas com conteúdo interativo esparso.</span><span class="sxs-lookup"><span data-stu-id="b0b99-139">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="b0b99-140">Se houver uma alta probabilidade de que você possa determinar o que um usuário estava tentando interagir, você pode complementar seus recursos de direcionamento assumindo algum nível de intenção.</span><span class="sxs-lookup"><span data-stu-id="b0b99-140">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="b0b99-141">Ações de backencontros e de reencontros</span><span class="sxs-lookup"><span data-stu-id="b0b99-141">Backdating and postdating actions</span></span>
<span data-ttu-id="b0b99-142">Esse mecanismo é útil para tarefas que exigem velocidade.</span><span class="sxs-lookup"><span data-stu-id="b0b99-142">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="b0b99-143">Quando um usuário passa por uma série de manobras de direcionamento e ativação em velocidade, é útil assumir alguma intenção e permitir que as etapas perdidas atuem em destinos que o usuário tinha em foco ligeiramente antes ou ligeiramente após o toque (50 ms antes/depois era efetivo em ea teste de Rly).</span><span class="sxs-lookup"><span data-stu-id="b0b99-143">When a user is moving through a series of targeting and activation maneuvers at speed, it is useful to assume some intent, and allow missed steps to act upon targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="b0b99-144">Suavização</span><span class="sxs-lookup"><span data-stu-id="b0b99-144">Smoothing</span></span>
<span data-ttu-id="b0b99-145">Esse mecanismo é útil para a trajetória de movimentos, reduzindo a ligeira tremulação e Wobble devido a características de movimento de cabeçalho natural.</span><span class="sxs-lookup"><span data-stu-id="b0b99-145">This mechanism is useful for pathing movements, reducing the slight jitter and wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="b0b99-146">Ao suavizar movimentos de caminho, Smooth pelo tamanho e distância dos movimentos em vez de ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="b0b99-146">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="b0b99-147">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="b0b99-147">Magnetism</span></span>
<span data-ttu-id="b0b99-148">Esse mecanismo pode ser considerado como uma versão mais comum dos algoritmos de link mais próximos – desenhar um cursor em direção a um destino ou simplesmente aumentar o hitboxes, seja visivelmente ou não, à medida que os usuários abordam os alvos prováveis usando algum conhecimento do layout interativo para melhor objetivo de usuário da abordagem.</span><span class="sxs-lookup"><span data-stu-id="b0b99-148">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="b0b99-149">Isso pode ser particularmente eficiente para alvos pequenos.</span><span class="sxs-lookup"><span data-stu-id="b0b99-149">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="b0b99-150">Adesão do foco</span><span class="sxs-lookup"><span data-stu-id="b0b99-150">Focus stickiness</span></span>
<span data-ttu-id="b0b99-151">Ao determinar a quais elementos interativos próximos dar foco, a adesão do foco fornece uma tendência para o elemento que está atualmente focado.</span><span class="sxs-lookup"><span data-stu-id="b0b99-151">When determining which nearby interactive elements to give focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="b0b99-152">Isso ajuda a reduzir os comportamentos incorretos de alternância de foco ao flutuar em um ponto médio entre dois elementos com ruído natural.</span><span class="sxs-lookup"><span data-stu-id="b0b99-152">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>


## <a name="see-also"></a><span data-ttu-id="b0b99-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0b99-153">See also</span></span>
* [<span data-ttu-id="b0b99-154">Interação com base nos olhos</span><span class="sxs-lookup"><span data-stu-id="b0b99-154">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="b0b99-155">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="b0b99-155">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="b0b99-156">Manipulação de mãos direta</span><span class="sxs-lookup"><span data-stu-id="b0b99-156">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b0b99-157">Gestos práticos</span><span class="sxs-lookup"><span data-stu-id="b0b99-157">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="b0b99-158">Ponto de mãos e confirmação</span><span class="sxs-lookup"><span data-stu-id="b0b99-158">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="b0b99-159">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="b0b99-159">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b0b99-160">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="b0b99-160">Voice input</span></span>](voice-input.md)




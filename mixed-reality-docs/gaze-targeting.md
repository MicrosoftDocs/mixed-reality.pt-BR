---
title: Direcionamento olhar
description: Todas as interações baseiam-se na capacidade de um usuário direcionar seu foco para o elemento com o qual deseja interagir, independentemente da modalidade de entrada.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, olhar, direcionamento olhar, interação, design
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829844"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="b0418-104">Olhar e a pesquisa</span><span class="sxs-lookup"><span data-stu-id="b0418-104">Gaze and dwell</span></span>
<span data-ttu-id="b0418-105">Há várias maneiras diferentes de confirmar uma _confirmação_ , como combinar olhar com gestos de _voz_ ou _mão_.</span><span class="sxs-lookup"><span data-stu-id="b0418-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="b0418-106">No entanto, há vários cenários de usuário, nos quais as mãos dos usuários podem estar ocupadas ou não podem ser controladas (por exemplo, funcionários de fábrica com luvas de imposto pesado muito grandes).</span><span class="sxs-lookup"><span data-stu-id="b0418-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="b0418-107">A entrada de voz também pode não estar disponível devido a preferências do usuário, contexto social ou ambientes altos.</span><span class="sxs-lookup"><span data-stu-id="b0418-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="b0418-108">Como uma solução de fallback, outra opção para executar uma _confirmação_ é simplesmente manter a estrela em um elemento de interface do usuário que nos referimos como uma _pesquisa_.</span><span class="sxs-lookup"><span data-stu-id="b0418-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="b0418-109">Uma _pesquisa_ pode ser executada com olhar de cabeça ou de olho.</span><span class="sxs-lookup"><span data-stu-id="b0418-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="b0418-110">A ideia é simples e pode ser dividida nas seguintes fases:</span><span class="sxs-lookup"><span data-stu-id="b0418-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="b0418-111">O usuário inicia o nuvens em um botão Holographic</span><span class="sxs-lookup"><span data-stu-id="b0418-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="b0418-112">Após um breve atraso de início (por exemplo, 150 ms), algumas animações de comentários visuais são iniciadas.</span><span class="sxs-lookup"><span data-stu-id="b0418-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="b0418-113">O atraso de início é usado para evitar sobrecarregar o usuário imediatamente ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b0418-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="b0418-114">Para _olhar de olho_, recomendamos o seguinte para o design dos comentários sobre a pesquisa Visual:</span><span class="sxs-lookup"><span data-stu-id="b0418-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="b0418-115">**Misturar**: Mescle suavemente os comentários do mal visíveis a princípio para totalmente opaco.</span><span class="sxs-lookup"><span data-stu-id="b0418-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="b0418-116">Isso torna os comentários menos confusos e overwhlemings e alinha-se perfeitamente com a confiança que o sistema tem que o usuário realmente deseja envolver com esse botão.</span><span class="sxs-lookup"><span data-stu-id="b0418-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="b0418-117">Efetuar **pull**: Crie um comentário visual que diminui em tamanho e se move para o centro do destino, puxando a atenção visual do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0418-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="b0418-118">Após uma duração de uma pesquisa predefinida (por exemplo, 800 MS), a pesquisa é concluída e um evento associado é disparado.</span><span class="sxs-lookup"><span data-stu-id="b0418-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="b0418-119">Forneça alguns comentários de auditoria ou visuais finais para realmente colocar em casa que o item foi selecionado agora.</span><span class="sxs-lookup"><span data-stu-id="b0418-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![Estados de pesquisa](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="b0418-121">Direcionamento olhar</span><span class="sxs-lookup"><span data-stu-id="b0418-121">Gaze targeting</span></span>

<span data-ttu-id="b0418-122">Todas as interações baseiam-se na capacidade de um usuário direcionar seu foco para o elemento com o qual deseja interagir, independentemente da modalidade de entrada.</span><span class="sxs-lookup"><span data-stu-id="b0418-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="b0418-123">No Windows Mixed Reality, isso geralmente é feito com o foco do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0418-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="b0418-124">Para permitir que um usuário trabalhe com uma experiência bem-sucedida, o entendimento calculado do sistema da intenção de um usuário e a intenção real do usuário devem estar os mais alinhados possíveis.</span><span class="sxs-lookup"><span data-stu-id="b0418-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="b0418-125">Na medida em que o sistema interpreta as ações pretendidas do usuário corretamente, a satisfação e o desempenho melhoram.</span><span class="sxs-lookup"><span data-stu-id="b0418-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="b0418-126">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="b0418-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b0418-127"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="b0418-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b0418-128"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0418-128"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b0418-129"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b0418-129"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b0418-130"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="b0418-130"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b0418-131">Direcionamento olhar</span><span class="sxs-lookup"><span data-stu-id="b0418-131">Gaze targeting</span></span></td>
        <td><span data-ttu-id="b0418-132">✔️</span><span class="sxs-lookup"><span data-stu-id="b0418-132">✔️</span></span></td>
        <td><span data-ttu-id="b0418-133">✔️</span><span class="sxs-lookup"><span data-stu-id="b0418-133">✔️</span></span></td>
        <td><span data-ttu-id="b0418-134">✔️</span><span class="sxs-lookup"><span data-stu-id="b0418-134">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b0418-135">Direcionamento de olho</span><span class="sxs-lookup"><span data-stu-id="b0418-135">Eye targeting</span></span></td>
        <td><span data-ttu-id="b0418-136">❌</span><span class="sxs-lookup"><span data-stu-id="b0418-136">❌</span></span></td>
        <td><span data-ttu-id="b0418-137">✔️</span><span class="sxs-lookup"><span data-stu-id="b0418-137">✔️</span></span></td>
        <td><span data-ttu-id="b0418-138">❌</span><span class="sxs-lookup"><span data-stu-id="b0418-138">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="b0418-139">Mais diretrizes específicas para o HoloLens 2 em [breve](index.md).</span><span class="sxs-lookup"><span data-stu-id="b0418-139">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="b0418-140">Dimensionamento e comentários sobre o alvo</span><span class="sxs-lookup"><span data-stu-id="b0418-140">Target sizing and feedback</span></span>

<span data-ttu-id="b0418-141">O vetor de foco demonstrou repetidamente ser utilizável para o direcionamento refinado, mas geralmente funciona melhor para o direcionamento bruto (adquirindo, de certa forma, alvos maiores).</span><span class="sxs-lookup"><span data-stu-id="b0418-141">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="b0418-142">Os tamanhos mínimos do alvo de 1 a 1,5 grau devem permitir ações bem-sucedidas do usuário na maioria dos cenários, embora os alvos de 3 graus normalmente permitam uma maior velocidade.</span><span class="sxs-lookup"><span data-stu-id="b0418-142">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="b0418-143">Observe que o tamanho do alvo escolhido pelo usuário é efetivamente uma área 2D até mesmo para elementos 3D – qualquer que seja a projeção que esteja voltada para eles deverá ser a área de alvo.</span><span class="sxs-lookup"><span data-stu-id="b0418-143">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="b0418-144">O fornecimento de alguma indicação evidente de que um elemento está "ativo" (ao qual o usuário está direcionando o foco) é extremamente útil – isso pode incluir tratamentos como efeitos de "focalização" visíveis, destaques de áudio ou cliques ou alinhamento claro de um cursor com um elemento.</span><span class="sxs-lookup"><span data-stu-id="b0418-144">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="b0418-145">![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b0418-145">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="b0418-146">*Tamanho ideal do alvo em uma distância de 2 metros*</span><span class="sxs-lookup"><span data-stu-id="b0418-146">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="b0418-147">![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b0418-147">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="b0418-148">*Um exemplo de realce de um objeto direcionado por foco*</span><span class="sxs-lookup"><span data-stu-id="b0418-148">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="b0418-149">Posicionamento do alvo</span><span class="sxs-lookup"><span data-stu-id="b0418-149">Target placement</span></span>

<span data-ttu-id="b0418-150">Em geral, os usuários não encontrarão elementos de interface do usuário posicionados muito acima ou muito abaixo de seu campo de visão, concentrando a maior parte de sua atenção nas áreas em torno de seu foco principal (em geral, aproximadamente no nível dos olhos).</span><span class="sxs-lookup"><span data-stu-id="b0418-150">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="b0418-151">O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar.</span><span class="sxs-lookup"><span data-stu-id="b0418-151">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="b0418-152">Dada a tendência dos usuários de se concentrarem em uma área visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), o agrupamento de elementos de interface do usuário na medida em que eles estejam relacionados conceitualmente pode aproveitar os comportamentos de encadeamento da atenção de item a item conforme um usuário move o foco por uma área.</span><span class="sxs-lookup"><span data-stu-id="b0418-152">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="b0418-153">Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.</span><span class="sxs-lookup"><span data-stu-id="b0418-153">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="b0418-154">![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b0418-154">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="b0418-155">*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="b0418-155">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="b0418-156">Como melhorar os comportamentos de direcionamento</span><span class="sxs-lookup"><span data-stu-id="b0418-156">Improving targeting behaviors</span></span>

<span data-ttu-id="b0418-157">Se a intenção do usuário de direcionar o foco para algo puder ser determinada (ou aproximada), poderá ser muito útil aceitar tentativas "quase certas" na interação como se elas tivessem sido direcionadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="b0418-157">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="b0418-158">Há diversos métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="b0418-158">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="b0418-159">Estabilização de olhar ("gravidade caixas")</span><span class="sxs-lookup"><span data-stu-id="b0418-159">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="b0418-160">Isso deve estar ligado na maior parte do tempo ou todo o tempo.</span><span class="sxs-lookup"><span data-stu-id="b0418-160">This should be turned on most/all of the time.</span></span> <span data-ttu-id="b0418-161">Essa técnica remove as tremulações naturais da cabeça/do pescoço que os usuários possam ter.</span><span class="sxs-lookup"><span data-stu-id="b0418-161">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="b0418-162">Além disso, o movimento devido a comportamentos de visão/fala.</span><span class="sxs-lookup"><span data-stu-id="b0418-162">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="b0418-163">Algoritmos de vínculo mais próximo</span><span class="sxs-lookup"><span data-stu-id="b0418-163">Closest link algorithms</span></span>

<span data-ttu-id="b0418-164">Eles funcionam melhor em áreas com conteúdo interativo esparso.</span><span class="sxs-lookup"><span data-stu-id="b0418-164">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="b0418-165">Se houver uma grande probabilidade de que você determine com o que um usuário estava tentando interagir, você poderá complementar suas habilidades de direcionamento apenas supondo algum nível de intenção.</span><span class="sxs-lookup"><span data-stu-id="b0418-165">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="b0418-166">Ações de antedatar/pós-datar</span><span class="sxs-lookup"><span data-stu-id="b0418-166">Backdating/postdating actions</span></span>

<span data-ttu-id="b0418-167">Esse mecanismo é útil para tarefas que exigem velocidade.</span><span class="sxs-lookup"><span data-stu-id="b0418-167">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="b0418-168">Quando um usuário passa por uma série de manobras de direcionamento/ativação em velocidade, pode ser útil assumir alguma intenção e permitir que *as etapas perdidas* atuem em destinos que o usuário tinha em foco um pouco antes ou ligeiramente após o toque (50 ms antes/depois foi eficaz em testes iniciais).</span><span class="sxs-lookup"><span data-stu-id="b0418-168">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="b0418-169">Suavização</span><span class="sxs-lookup"><span data-stu-id="b0418-169">Smoothing</span></span>

<span data-ttu-id="b0418-170">Esse mecanismo é útil para movimentos de caminhos, reduzindo leve tremulação/tremor devido às características de movimentação natural da cabeça.</span><span class="sxs-lookup"><span data-stu-id="b0418-170">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="b0418-171">Durante a suavização em movimentos de caminhos, aplique a suavização por tamanho/distância de movimentos em vez de ao longo do tempo</span><span class="sxs-lookup"><span data-stu-id="b0418-171">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="b0418-172">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="b0418-172">Magnetism</span></span>

<span data-ttu-id="b0418-173">Esse mecanismo pode ser considerado uma versão mais geral dos algoritmos de "Vínculo mais próximo" – desenhar um cursor em direção a um alvo ou apenas aumentar os hitboxes (seja visivelmente ou não) conforme os usuários se aproximam de prováveis alvos, usando algum conhecimento sobre o layout interativo para uma melhor abordagem da intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0418-173">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="b0418-174">Isso pode ser particularmente eficiente para alvos pequenos.</span><span class="sxs-lookup"><span data-stu-id="b0418-174">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="b0418-175">Adesão do foco</span><span class="sxs-lookup"><span data-stu-id="b0418-175">Focus stickiness</span></span>

<span data-ttu-id="b0418-176">Ao determinar a quais elementos interativos nas proximidades o foco deve ser dado, forneça um desvio para o elemento que tem o foco atualmente.</span><span class="sxs-lookup"><span data-stu-id="b0418-176">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="b0418-177">Isso ajudará a reduzir os comportamentos de alternância de foco instável durante a flutuação em um ponto médio entre dois elementos com ruído natural.</span><span class="sxs-lookup"><span data-stu-id="b0418-177">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0418-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0418-178">See also</span></span>
* [<span data-ttu-id="b0418-179">Gestos</span><span class="sxs-lookup"><span data-stu-id="b0418-179">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="b0418-180">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="b0418-180">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="b0418-181">Cursores</span><span class="sxs-lookup"><span data-stu-id="b0418-181">Cursors</span></span>](cursors.md)

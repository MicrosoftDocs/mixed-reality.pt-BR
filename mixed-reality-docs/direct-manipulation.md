---
title: Manipulação direta com as mãos
description: Visão geral do modelo de entrada de manipulação direta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design, mãos nas proximidades, HoloLens
ms.openlocfilehash: 6811fe0b09ecff1ddc76d9df9ddc440f9c934ce3
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "75723245"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="c6a42-104">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="c6a42-104">Direct manipulation with hands</span></span>

![Botão](images/UX/UX_Hero_Manipulation.jpg)

<span data-ttu-id="c6a42-106">A manipulação direta é um modelo de entrada que envolve tocar hologramas diretamente com suas mãos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="c6a42-107">A ideia por trás desse conceito é que os objetos se comportem exatamente como no mundo real.</span><span class="sxs-lookup"><span data-stu-id="c6a42-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="c6a42-108">Os botões podem ser ativados simplesmente pressionando-os, os objetos podem ser pegados e o conteúdo 2D se comporta como uma tela de toque virtual.</span><span class="sxs-lookup"><span data-stu-id="c6a42-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="c6a42-109">Isso torna a manipulação direta fácil para os usuários aprenderem e se divertirem.</span><span class="sxs-lookup"><span data-stu-id="c6a42-109">This makes direct manipulation easy for users to learn, and fun.</span></span> <span data-ttu-id="c6a42-110">Ela é considerada um modelo de entrada "próximo", ou seja, é mais adequado para interagir com o conteúdo que está no alcance dos braços.</span><span class="sxs-lookup"><span data-stu-id="c6a42-110">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="c6a42-111">A manipulação direta é baseada em funcionalidade, o que significa que é amigável ao usuário.</span><span class="sxs-lookup"><span data-stu-id="c6a42-111">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="c6a42-112">Não há nenhum gesto simbólico para ensinar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="c6a42-112">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="c6a42-113">Todas as interações são criadas em torno de um elemento visual que você pode tocar ou pegar.</span><span class="sxs-lookup"><span data-stu-id="c6a42-113">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="c6a42-114">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="c6a42-114">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="c6a42-115"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="c6a42-115"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="c6a42-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c6a42-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="c6a42-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c6a42-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="c6a42-118"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c6a42-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="c6a42-119">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="c6a42-119">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="c6a42-120">❌ Sem suporte</span><span class="sxs-lookup"><span data-stu-id="c6a42-120">❌ Not supported</span></span></td>
     <td><span data-ttu-id="c6a42-121">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="c6a42-121">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="c6a42-122">➕ Uma alternativa, <a href="point-and-commit.md">apontar e confirmar com as mãos</a> é recomendado.</span><span class="sxs-lookup"><span data-stu-id="c6a42-122">➕ An alternative, <a href="point-and-commit.md">point and commit with hands</a> is recommended.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="c6a42-123">A manipulação direta é um modelo de entrada primário no HoloLens 2, que usa o novo sistema articulado de acompanhamento com as mãos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="c6a42-124">O modelo de entrada também está disponível nos headsets imersivos com o uso de controladores de movimento, mas não é recomendado como o principal meio de interação, apenas para a manipulação de objetos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-124">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="c6a42-125">A manipulação direta não está disponível no HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="c6a42-125">Direct manipulation is not available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="c6a42-126">Ponta do dedo colidente</span><span class="sxs-lookup"><span data-stu-id="c6a42-126">Collidable fingertip</span></span>

<span data-ttu-id="c6a42-127">No HoloLens 2, as mãos do usuário são reconhecidas e interpretadas como modelos estruturais esquerdo e direito.</span><span class="sxs-lookup"><span data-stu-id="c6a42-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="c6a42-128">Para implementar a ideia de tocar hologramas diretamente com mãos, idealmente, cinco colisores podem ser anexados às pontas dos cinco dedos de cada modelo estrutural de mão.</span><span class="sxs-lookup"><span data-stu-id="c6a42-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="c6a42-129">No entanto, devido à falta de retorno tátil, dez pontas de dedo colidentes podem causar colisões inesperadas e imprevisíveis com os hologramas.</span><span class="sxs-lookup"><span data-stu-id="c6a42-129">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="c6a42-130">Portanto, sugerimos colocar apenas um colisor em cada dedo indicador.</span><span class="sxs-lookup"><span data-stu-id="c6a42-130">Hence, we suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="c6a42-131">As pontas de dedo indicador colidentes ainda podem servir como pontos de toque ativo para diversos gestos de toque que envolvam outros dedos, como ao pressionar com um dedo, tocar com um dedo e pressionar com dois e cinco dedos, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="c6a42-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as One-finger press, One-finger tap, Two-finger press and Five-finger press, as shown in the image below.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c6a42-132">![ponta do dedo colidente](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-132">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="c6a42-133">**Ponta do dedo colidente**</span><span class="sxs-lookup"><span data-stu-id="c6a42-133">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-134">![Pressionar com um dedo](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-134">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="c6a42-135">**Pressionar com um dedo**</span><span class="sxs-lookup"><span data-stu-id="c6a42-135">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-136">![Tocar com um dedo](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-136">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="c6a42-137">**Tocar com um dedo**</span><span class="sxs-lookup"><span data-stu-id="c6a42-137">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-138">![Pressionar com cinco dedos](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-138">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="c6a42-139">**Pressionar com cinco dedos**</span><span class="sxs-lookup"><span data-stu-id="c6a42-139">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="c6a42-140">Colisor esférico</span><span class="sxs-lookup"><span data-stu-id="c6a42-140">Sphere collider</span></span>

<span data-ttu-id="c6a42-141">Em vez de usar uma forma genérica aleatória, sugerimos que você use um colisor esférico.</span><span class="sxs-lookup"><span data-stu-id="c6a42-141">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="c6a42-142">Em seguida, você pode renderizá-lo visualmente para fornecer indicações melhores para direcionamento próximo.</span><span class="sxs-lookup"><span data-stu-id="c6a42-142">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="c6a42-143">O diâmetro da esfera deve corresponder à espessura do dedo indicador para aumentar a precisão do toque.</span><span class="sxs-lookup"><span data-stu-id="c6a42-143">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="c6a42-144">É mais fácil recuperar a variável de espessura do dedo chamando a API da mão.</span><span class="sxs-lookup"><span data-stu-id="c6a42-144">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="c6a42-145">Cursor de ponta do dedo</span><span class="sxs-lookup"><span data-stu-id="c6a42-145">Fingertip cursor</span></span>

<span data-ttu-id="c6a42-146">Além de renderizar uma esfera colidente na ponta do dedo indicador, criamos um cursor avançado de ponta do dedo para obter uma melhor experiência de direcionamento próximo, de maneira interativa.</span><span class="sxs-lookup"><span data-stu-id="c6a42-146">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="c6a42-147">É um cursor em forma de rosca anexado à ponta do dedo indicador.</span><span class="sxs-lookup"><span data-stu-id="c6a42-147">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="c6a42-148">De acordo com a proximidade, ele reage dinamicamente a um alvo em termos de orientação e tamanho, conforme especificado abaixo:</span><span class="sxs-lookup"><span data-stu-id="c6a42-148">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="c6a42-149">Quando um dedo indicador se move em direção a um holograma, o cursor sempre está paralelo à superfície do holograma e diminui gradualmente seu tamanho.</span><span class="sxs-lookup"><span data-stu-id="c6a42-149">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="c6a42-150">Assim que o dedo toca a superfície, o cursor é reduzido a um ponto e emite um evento de toque.</span><span class="sxs-lookup"><span data-stu-id="c6a42-150">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="c6a42-151">Com o retorno interativo, os usuários podem realizar tarefas de direcionamento próximo com alta precisão, como disparar um hiperlink ou pressionar um botão, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="c6a42-151">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="c6a42-152">![Cursor de ponta do dedo distante](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-152">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="c6a42-153">**Cursor de ponta do dedo distante**</span><span class="sxs-lookup"><span data-stu-id="c6a42-153">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-154">![Cursor de ponta do dedo próximo](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-154">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="c6a42-155">**Cursor de ponta do dedo próximo**</span><span class="sxs-lookup"><span data-stu-id="c6a42-155">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-156">![Cursor de ponta do dedo com contato](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-156">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="c6a42-157">**Cursor de ponta do dedo com contato**</span><span class="sxs-lookup"><span data-stu-id="c6a42-157">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="c6a42-158">Caixa delimitadora com o sombreador de proximidade</span><span class="sxs-lookup"><span data-stu-id="c6a42-158">Bounding box with proximity shader</span></span>

<span data-ttu-id="c6a42-159">O holograma em si também requer a capacidade de fornecer retorno visual e sonoro para compensar a falta do retorno tátil.</span><span class="sxs-lookup"><span data-stu-id="c6a42-159">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="c6a42-160">Para isso, criamos o conceito de uma caixa delimitadora com um sombreador de proximidade.</span><span class="sxs-lookup"><span data-stu-id="c6a42-160">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="c6a42-161">Uma caixa delimitadora é uma área volumétrica mínima que inclui um objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="c6a42-161">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="c6a42-162">A caixa delimitadora tem um mecanismo de renderização interativo chamado de sombreador de proximidade.</span><span class="sxs-lookup"><span data-stu-id="c6a42-162">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="c6a42-163">O sombreador de proximidade se comporta da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c6a42-163">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c6a42-164">![Focalizar (distante) com comentários visuais](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-164">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="c6a42-165">**Focalizar (distante)**</span><span class="sxs-lookup"><span data-stu-id="c6a42-165">**Hover (far)**</span></span><br>
       <span data-ttu-id="c6a42-166">Quando o dedo indicador está em um intervalo, um destaque da ponta do dedo é mostrado na superfície da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="c6a42-166">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-167">![Focalizar (próximo) com comentários visuais](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-167">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="c6a42-168">**Focalizar (próximo)**</span><span class="sxs-lookup"><span data-stu-id="c6a42-168">**Hover (near)**</span></span><br>
        <span data-ttu-id="c6a42-169">Quando a ponta do dedo se aproxima da superfície, o destaque é reduzido correspondentemente.</span><span class="sxs-lookup"><span data-stu-id="c6a42-169">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-170">![O contato começa](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-170">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="c6a42-171">**O contato começa**</span><span class="sxs-lookup"><span data-stu-id="c6a42-171">**Contact begins**</span></span><br>
       <span data-ttu-id="c6a42-172">Quando a ponta do dedo toca a superfície, toda a caixa delimitadora tem sua cor alterada ou gera efeitos visuais para refletir o estado de toque.</span><span class="sxs-lookup"><span data-stu-id="c6a42-172">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-173">![O contato termina](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-173">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="c6a42-174">**O contato termina**</span><span class="sxs-lookup"><span data-stu-id="c6a42-174">**Contact ends**</span></span><br>
       <span data-ttu-id="c6a42-175">Um efeito sonoro pode ser ativado para aprimorar o retorno visual do toque.</span><span class="sxs-lookup"><span data-stu-id="c6a42-175">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="c6a42-176">Botão de pressão</span><span class="sxs-lookup"><span data-stu-id="c6a42-176">Pressable button</span></span>

<span data-ttu-id="c6a42-177">Com uma ponta do dedo colidente, os usuários podem interagir com um componente holográfico da interface do usuário fundamental, como o botão de pressionar.</span><span class="sxs-lookup"><span data-stu-id="c6a42-177">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="c6a42-178">Um botão de pressão é um botão holográfico adaptado para o pressionar direto do dedo.</span><span class="sxs-lookup"><span data-stu-id="c6a42-178">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="c6a42-179">Novamente, devido à falta de retorno tátil, um botão de pressão ativa alguns mecanismos para lidar com os problemas relacionados ao retorno tátil.</span><span class="sxs-lookup"><span data-stu-id="c6a42-179">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="c6a42-180">O primeiro mecanismo é uma caixa delimitadora com um sombreador de proximidade, o qual é detalhado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="c6a42-180">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="c6a42-181">Ele fornece aos usuários uma melhor sensação de proximidade quando eles se aproximam e fazem contato com um botão.</span><span class="sxs-lookup"><span data-stu-id="c6a42-181">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="c6a42-182">O segundo mecanismo é o de liberação.</span><span class="sxs-lookup"><span data-stu-id="c6a42-182">The second mechanism is depression.</span></span> <span data-ttu-id="c6a42-183">A liberação cria uma ideia de pressionar para baixo depois da ponta de um dedo entrar em contato com um botão.</span><span class="sxs-lookup"><span data-stu-id="c6a42-183">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="c6a42-184">O mecanismo verifica se o botão se move intimamente com a ponta do dedo ao longo do eixo de profundidade.</span><span class="sxs-lookup"><span data-stu-id="c6a42-184">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="c6a42-185">O botão pode ser disparado quando atinge uma profundidade designada (ao pressionar) ou ao ser liberado depois de passar por ela.</span><span class="sxs-lookup"><span data-stu-id="c6a42-185">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="c6a42-186">O efeito sonoro deve ser adicionado para melhorar o retorno quando o botão é disparado.</span><span class="sxs-lookup"><span data-stu-id="c6a42-186">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c6a42-187">![botão de pressionar a distância](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-187">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="c6a42-188">**O dedo está longe**</span><span class="sxs-lookup"><span data-stu-id="c6a42-188">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-189">![botão de pressionar próximo](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-189">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="c6a42-190">**O dedo se aproxima**</span><span class="sxs-lookup"><span data-stu-id="c6a42-190">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-191">![o contato com o botão de pressionar começa](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-191">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="c6a42-192">**O contato começa**</span><span class="sxs-lookup"><span data-stu-id="c6a42-192">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-193">![pressionar o botão de pressionar](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-193">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="c6a42-194">**Pressione**</span><span class="sxs-lookup"><span data-stu-id="c6a42-194">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="c6a42-195">Interação do slate 2D</span><span class="sxs-lookup"><span data-stu-id="c6a42-195">2D slate interaction</span></span>

<span data-ttu-id="c6a42-196">Um [slate](slate.md) 2D é um contêiner holográfico usado para hospedar o conteúdo do aplicativo 2D, assim como um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="c6a42-196">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="c6a42-197">O conceito de design para interagir com um slate 2D por meio da manipulação direta é aproveitar o modelo mental da interação com uma tela de toque física.</span><span class="sxs-lookup"><span data-stu-id="c6a42-197">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="c6a42-198">Para interagir com o contato do slate</span><span class="sxs-lookup"><span data-stu-id="c6a42-198">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c6a42-199">![Tocar](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-199">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="c6a42-200">**Tocar**</span><span class="sxs-lookup"><span data-stu-id="c6a42-200">**Touch**</span></span><br>
       <span data-ttu-id="c6a42-201">Use o dedo indicador para pressionar um botão ou hiperlink.</span><span class="sxs-lookup"><span data-stu-id="c6a42-201">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-202">![Rolar](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-202">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="c6a42-203">**Rolar**</span><span class="sxs-lookup"><span data-stu-id="c6a42-203">**Scroll**</span></span><br>
        <span data-ttu-id="c6a42-204">Use o dedo indicador para rolar um slate de conteúdo para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="c6a42-204">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-205">![Aplicar zoom](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-205">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="c6a42-206">**Aplicar zoom**</span><span class="sxs-lookup"><span data-stu-id="c6a42-206">**Zoom**</span></span><br>
       <span data-ttu-id="c6a42-207">O usuário usa os dois dedos indicadores para aumentar e diminuir o zoom no conteúdo do slate, de acordo com o movimento relativo dos dedos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-207">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="c6a42-208">Para manipular o slate 2D em si</span><span class="sxs-lookup"><span data-stu-id="c6a42-208">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c6a42-209">![Mover](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-209">![Move](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="c6a42-210">**Mover**</span><span class="sxs-lookup"><span data-stu-id="c6a42-210">**Move**</span></span><br>
       <span data-ttu-id="c6a42-211">Movimente suas mãos para os cantos e bordas para revelar as funcionalidades de manipulação mais próximas.</span><span class="sxs-lookup"><span data-stu-id="c6a42-211">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="c6a42-212">Segure a barra holográfica na parte superior do slate 2D, o que permite mover todo o slate.</span><span class="sxs-lookup"><span data-stu-id="c6a42-212">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-213">![Dimensionar](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-213">![Scale](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="c6a42-214">**Dimensionar**</span><span class="sxs-lookup"><span data-stu-id="c6a42-214">**Scale**</span></span><br>
        <span data-ttu-id="c6a42-215">Segure as funcionalidades de manipulação e realize um dimensionamento uniforme utilizando as funcionalidades de canto.</span><span class="sxs-lookup"><span data-stu-id="c6a42-215">Grab the manipulation affordances and perform uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-216">![Refluxo](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-216">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="c6a42-217">**Refluxo**</span><span class="sxs-lookup"><span data-stu-id="c6a42-217">**Reflow**</span></span><br>
       <span data-ttu-id="c6a42-218">Segure as funcionalidades de manipulação e realize um refluxo por meio das funcionalidades de borda.</span><span class="sxs-lookup"><span data-stu-id="c6a42-218">Grab the manipulation affordances and perform reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="c6a42-219">Manipulação de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="c6a42-219">3D object manipulation</span></span>

<span data-ttu-id="c6a42-220">O HoloLens 2 permite que os usuários habilitem suas mãos para orientar e manipular objetos holográficos 3D, aplicando uma caixa delimitadora a cada objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="c6a42-220">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="c6a42-221">A caixa delimitadora fornece uma melhor percepção da profundidade por meio do sombreador de proximidade.</span><span class="sxs-lookup"><span data-stu-id="c6a42-221">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="c6a42-222">Com a caixa delimitadora, há duas abordagens de design para a manipulação de objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="c6a42-222">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="c6a42-223">Manipulação baseada em funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c6a42-223">Affordance-based manipulation</span></span>

<span data-ttu-id="c6a42-224">A manipulação com base em funcionalidade permite manipular o objeto 3D por meio de uma caixa delimitadora, junto com as funcionalidades de manipulação em torno dela.</span><span class="sxs-lookup"><span data-stu-id="c6a42-224">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="c6a42-225">![Mover](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-225">![Move](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="c6a42-226">**Mover**</span><span class="sxs-lookup"><span data-stu-id="c6a42-226">**Move**</span></span><br>
       <span data-ttu-id="c6a42-227">Quando a mão de um usuário estiver próxima a um objeto 3D, a caixa delimitadora e a funcionalidade mais próxima são reveladas.</span><span class="sxs-lookup"><span data-stu-id="c6a42-227">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="c6a42-228">Os usuários podem segurar a caixa delimitadora para mover todo o objeto.</span><span class="sxs-lookup"><span data-stu-id="c6a42-228">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-229">![Girar](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-229">![Rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="c6a42-230">**Girar**</span><span class="sxs-lookup"><span data-stu-id="c6a42-230">**Rotate**</span></span><br>
        <span data-ttu-id="c6a42-231">Os usuários podem segurar as funcionalidades de borda para girar.</span><span class="sxs-lookup"><span data-stu-id="c6a42-231">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-232">![Dimensionar](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-232">![Scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="c6a42-233">**Dimensionar**</span><span class="sxs-lookup"><span data-stu-id="c6a42-233">**Scale**</span></span><br>
       <span data-ttu-id="c6a42-234">Os usuários podem segurar as funcionalidades de borda para dimensionar uniformemente.</span><span class="sxs-lookup"><span data-stu-id="c6a42-234">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="c6a42-235">Manipulação não baseada em funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c6a42-235">Non-affordance based manipulation</span></span>

<span data-ttu-id="c6a42-236">A manipulação que não é baseada em funcionalidade não anexa a funcionalidade à caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="c6a42-236">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="c6a42-237">Os usuários podem revelar apenas a caixa delimitadora e interagir diretamente com ela.</span><span class="sxs-lookup"><span data-stu-id="c6a42-237">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="c6a42-238">Se a caixa delimitadora for pega com uma mão, a translação e rotação do objeto estarão associadas ao movimento e à orientação da mão.</span><span class="sxs-lookup"><span data-stu-id="c6a42-238">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="c6a42-239">Quando o objeto é pego com as duas mãos, os usuários podem transladá-lo, dimensioná-lo e girá-lo de acordo com os movimentos relativos das duas mãos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-239">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="c6a42-240">A manipulação específica requer precisão.</span><span class="sxs-lookup"><span data-stu-id="c6a42-240">Specific manipulation requires precision.</span></span> <span data-ttu-id="c6a42-241">Recomendamos usar a **manipulação baseada em funcionalidade**, pois ela fornece um alto nível de granularidade.</span><span class="sxs-lookup"><span data-stu-id="c6a42-241">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="c6a42-242">Para a manipulação flexível, recomendamos usar a **manipulação não baseada em funcionalidade**, pois ela permite experiências instantâneas e divertidas.</span><span class="sxs-lookup"><span data-stu-id="c6a42-242">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="c6a42-243">Gestos instintuais</span><span class="sxs-lookup"><span data-stu-id="c6a42-243">Instinctual gestures</span></span>

<span data-ttu-id="c6a42-244">Com o HoloLens (1ª geração), ensinamos aos usuários alguns gestos predefinidos, como abrir a mão e fechar e abrir dedos indicador e polegar.</span><span class="sxs-lookup"><span data-stu-id="c6a42-244">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="c6a42-245">Para o HoloLens 2, não pedimos para os usuários memorizarem gestos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-245">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="c6a42-246">Todos os gestos exigidos do usuário, em que os usuários precisam interagir com os hologramas e o conteúdo, são instintivos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-246">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="c6a42-247">A forma de atingir gestos instintuais é ajudar os usuários a realizar os gestos por meio do design de funcionalidades da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6a42-247">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="c6a42-248">Por exemplo, se nós incentivarmos o usuário a segurar um objeto ou um ponto de controle com uma pinçagem de dois dedos, o objeto ou o ponto de controle deverá ser pequeno.</span><span class="sxs-lookup"><span data-stu-id="c6a42-248">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="c6a42-249">Se quisermos que o usuário segure com cinco dedos, o objeto ou o ponto de controle deverá ser relativamente grande.</span><span class="sxs-lookup"><span data-stu-id="c6a42-249">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="c6a42-250">Isso funciona de modo semelhante para os botões: um botão pequeno limitaria os usuários a pressioná-lo com apenas um dedo, enquanto que um botão grande encorajaria os usuários a pressioná-lo com as mãos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-250">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="c6a42-251">![Mover](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-251">![Move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="c6a42-252">**Objeto pequeno**</span><span class="sxs-lookup"><span data-stu-id="c6a42-252">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-253">![Girar](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-253">![Rotate](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="c6a42-254">**Objeto médio**</span><span class="sxs-lookup"><span data-stu-id="c6a42-254">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c6a42-255">![Dimensionar](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="c6a42-255">![Scale](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="c6a42-256">**Objeto grande**</span><span class="sxs-lookup"><span data-stu-id="c6a42-256">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="c6a42-257">Design simétrico entre os controladores de mão e DoF 6</span><span class="sxs-lookup"><span data-stu-id="c6a42-257">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="c6a42-258">Talvez você tenha observado que há interações paralelas que podemos utilizar entre as mãos em controladores de RA e de movimento na VR.</span><span class="sxs-lookup"><span data-stu-id="c6a42-258">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="c6a42-259">Ambas as entradas podem ser usadas para disparar manipulações diretas em seus respectivos ambientes.</span><span class="sxs-lookup"><span data-stu-id="c6a42-259">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="c6a42-260">No HoloLens 2, os movimentos de segurar e arrastar com mãos em distância próxima funcionam da mesma maneira que o botão para segurar nos controladores de movimentos do WMR.</span><span class="sxs-lookup"><span data-stu-id="c6a42-260">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="c6a42-261">Isso fornece aos usuários familiaridade de interação entre as duas plataformas, que poderão ser úteis se você decidir portar seu aplicativo de uma para a outra.</span><span class="sxs-lookup"><span data-stu-id="c6a42-261">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application from one to the other.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="c6a42-262">Otimizar com acompanhamento ocular</span><span class="sxs-lookup"><span data-stu-id="c6a42-262">Optimize with eye tracking</span></span>

<span data-ttu-id="c6a42-263">A manipulação direta poderá proporcionar uma sensação mágica se funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="c6a42-263">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="c6a42-264">No entanto, ela também poderá se tornar frustrante se você não puder mover sua mão para algum lugar sem disparar inadvertidamente um holograma.</span><span class="sxs-lookup"><span data-stu-id="c6a42-264">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="c6a42-265">O acompanhamento ocular ajuda potencialmente a identificar melhor qual é a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="c6a42-265">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="c6a42-266">**Quando**: reduzir o disparo involuntário de uma resposta de manipulação.</span><span class="sxs-lookup"><span data-stu-id="c6a42-266">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="c6a42-267">O acompanhamento ocular permite entender melhor o que um usuário realmente deseja fazer.</span><span class="sxs-lookup"><span data-stu-id="c6a42-267">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="c6a42-268">Por exemplo, imagine que você esteja lendo um texto (instrutivo) holográfico e se aproxime para pegar uma ferramenta de trabalho do mundo real.</span><span class="sxs-lookup"><span data-stu-id="c6a42-268">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="c6a42-269">Ao fazer isso, você move acidentalmente sua mão sobre alguns botões holográficos interativos que não tinha observado (por ex., ela pode estar fora do FoV (campo de visão) do usuário).</span><span class="sxs-lookup"><span data-stu-id="c6a42-269">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (e.g. it  may be outside the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="c6a42-270">Em resumo: se o usuário não olhar para um holograma por algum tempo, mas for detectado um evento de toque ou compreensão, provavelmente não foi a intenção do usuário interagir com esse holograma.</span><span class="sxs-lookup"><span data-stu-id="c6a42-270">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="c6a42-271">**Qual deles**:  além de lidar com ativações falso-positivas, outro exemplo inclui a melhor identificação dos hologramas a serem segurados ou tocados, já que o ponto de interseção preciso pode não ser claro da sua perspectiva, especialmente se vários hologramas estão posicionados próximos uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="c6a42-271">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="c6a42-272">Embora o acompanhamento ocular no HoloLens 2 tenha limitações com base na precisão com a que ele pode determinar seu foco ocular, isso ainda pode ser muito útil para interações próximas devido à disparidade de profundidade ao interagir com a entrada de mão.</span><span class="sxs-lookup"><span data-stu-id="c6a42-272">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="c6a42-273">Isso significa que, às vezes, é difícil determinar se sua mão está atrás ou na frente de um holograma para segurar precisamente um widget de manipulação, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="c6a42-273">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="c6a42-274">**Onde**: usar informações sobre o que um usuário está vendo com gestos de lançamento rápido.</span><span class="sxs-lookup"><span data-stu-id="c6a42-274">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="c6a42-275">Segure um holograma e lance-o para seu destino pretendido.</span><span class="sxs-lookup"><span data-stu-id="c6a42-275">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="c6a42-276">Embora isso geralmente funcione bem, gestos de mão muito rápidos podem resultar em destinos altamente imprecisos.</span><span class="sxs-lookup"><span data-stu-id="c6a42-276">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="c6a42-277">No entanto, o acompanhamento ocular poderia melhorar a precisão do gesto.</span><span class="sxs-lookup"><span data-stu-id="c6a42-277">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c6a42-278">Manipulação no MRTK (Kit de Ferramentas de Realidade Misturada) para o Unity</span><span class="sxs-lookup"><span data-stu-id="c6a42-278">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="c6a42-279">Com o **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , você pode alcançar facilmente o comportamento de manipulação comum usando o script **ManipulationHandler**.</span><span class="sxs-lookup"><span data-stu-id="c6a42-279">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ManipulationHandler**.</span></span> <span data-ttu-id="c6a42-280">Com o ManipulationHandler, você pode pegar e mover objetos diretamente com mãos ou com o raio de mão.</span><span class="sxs-lookup"><span data-stu-id="c6a42-280">With ManipulationHandler, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="c6a42-281">Ele também dá suporte à manipulação com as duas mãos para dimensionar e girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="c6a42-281">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="c6a42-282">MRTK – Manipulação</span><span class="sxs-lookup"><span data-stu-id="c6a42-282">MRTK - Manipulation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)


---

## <a name="see-also"></a><span data-ttu-id="c6a42-283">Veja também</span><span class="sxs-lookup"><span data-stu-id="c6a42-283">See also</span></span>

* [<span data-ttu-id="c6a42-284">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="c6a42-284">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="c6a42-285">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="c6a42-285">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="c6a42-286">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="c6a42-286">Instinctual interactions</span></span>](interaction-fundamentals.md)

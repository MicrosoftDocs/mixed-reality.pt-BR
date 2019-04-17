---
title: Conceitos básicos de interação
description: Como criamos experiências em HoloLens (1º gen), 2 HoloLens e fones imersivos em exposição, iniciamos anotar algumas coisas que encontramos útil para compartilhar.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realidade, interação, de design
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589082"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="abc72-104">Conceitos básicos de interação</span><span class="sxs-lookup"><span data-stu-id="abc72-104">Interaction fundamentals</span></span>

<span data-ttu-id="abc72-105">Como criamos experiências em HoloLens e fones imersivos em exposição, começamos a escrever algumas coisas que encontramos útil para compartilhar.</span><span class="sxs-lookup"><span data-stu-id="abc72-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="abc72-106">Pense nisso como blocos de construção fundamentais para o design de interação de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="abc72-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="abc72-107">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="abc72-107">Device support</span></span>

<span data-ttu-id="abc72-108">Aqui está uma estrutura de tópicos de artigos de design de interação disponíveis e o tipo de dispositivo ou tipos que se aplicam a.</span><span class="sxs-lookup"><span data-stu-id="abc72-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="abc72-109"><strong>entrada</strong></span><span class="sxs-lookup"><span data-stu-id="abc72-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="abc72-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="abc72-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="abc72-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="abc72-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="abc72-112"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="abc72-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="abc72-113"><a href="gestures.md">Mãos articuladas</a></span><span class="sxs-lookup"><span data-stu-id="abc72-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="abc72-114">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="abc72-115"><a href="gaze-targeting.md">Direcionamento de olhos</a></span><span class="sxs-lookup"><span data-stu-id="abc72-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="abc72-116">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="abc72-117"><a href="gaze-targeting.md">Mantenha o foco de direcionamento</a></span><span class="sxs-lookup"><span data-stu-id="abc72-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-118">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-119">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-120">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="abc72-121"><a href="gestures.md">Gestos</a></span><span class="sxs-lookup"><span data-stu-id="abc72-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-122">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-123">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="abc72-124"><a href="voice-design.md">Design de voz</a></span><span class="sxs-lookup"><span data-stu-id="abc72-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-125">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-126">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-127">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="abc72-128">Gamepad</span><span class="sxs-lookup"><span data-stu-id="abc72-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-129">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-130">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-131">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="abc72-132"><a href="motion-controllers.md">Controladores de movimento</a></span><span class="sxs-lookup"><span data-stu-id="abc72-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="abc72-133">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="abc72-134"><strong>Percepção e recursos espaciais</strong></span><span class="sxs-lookup"><span data-stu-id="abc72-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="abc72-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="abc72-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="abc72-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="abc72-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="abc72-137"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="abc72-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="abc72-138"><a href="spatial-sound-design.md">Design de som espacial</a></span><span class="sxs-lookup"><span data-stu-id="abc72-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-139">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-140">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-141">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="abc72-142"><a href="spatial-mapping-design.md">Design de mapeamento espacial</a></span><span class="sxs-lookup"><span data-stu-id="abc72-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-143">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-144">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="abc72-145"><a href="hologram.md">Hologramas</a></span><span class="sxs-lookup"><span data-stu-id="abc72-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-146">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="abc72-147">✔️</span><span class="sxs-lookup"><span data-stu-id="abc72-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="abc72-148">O usuário é a câmera</span><span class="sxs-lookup"><span data-stu-id="abc72-148">The user is the camera</span></span>

![Usuário é a câmera](images/useriscamera-640px.jpg)

<span data-ttu-id="abc72-150">Sempre pense sobre design para o ponto de vista do seu usuário quando eles passam sobre seus mundos reais e virtuais.</span><span class="sxs-lookup"><span data-stu-id="abc72-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="abc72-151">**Algumas perguntas a serem feitas**</span><span class="sxs-lookup"><span data-stu-id="abc72-151">**Some questions to ask**</span></span>
* <span data-ttu-id="abc72-152">É o usuário sentado, reclinável, aguardando ou percorrer durante o uso de sua experiência?</span><span class="sxs-lookup"><span data-stu-id="abc72-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="abc72-153">Como o seu conteúdo se ajustará para posições diferentes?</span><span class="sxs-lookup"><span data-stu-id="abc72-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="abc72-154">O usuário poderá ajustá-lo?</span><span class="sxs-lookup"><span data-stu-id="abc72-154">Can the user adjust it?</span></span>
* <span data-ttu-id="abc72-155">O usuário estará familiarizado com o uso de seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="abc72-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="abc72-156">**Práticas recomendadas**</span><span class="sxs-lookup"><span data-stu-id="abc72-156">**Best practices**</span></span>
* <span data-ttu-id="abc72-157">O usuário é a câmera e eles controlam a movimentação.</span><span class="sxs-lookup"><span data-stu-id="abc72-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="abc72-158">Deixe-os da unidade.</span><span class="sxs-lookup"><span data-stu-id="abc72-158">Let them drive.</span></span>
* <span data-ttu-id="abc72-159">Se você precisar praticamente o usuário de transporte, se sensível a problemas de discomfort vestibular.</span><span class="sxs-lookup"><span data-stu-id="abc72-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="abc72-160">Usar animações mais curtas</span><span class="sxs-lookup"><span data-stu-id="abc72-160">Use shorter animations</span></span>
* <span data-ttu-id="abc72-161">Animar de inferior/esquerda/direita ou aplicar fade-in, em vez de Z</span><span class="sxs-lookup"><span data-stu-id="abc72-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="abc72-162">Reduzir a velocidade de medição de tempo</span><span class="sxs-lookup"><span data-stu-id="abc72-162">Slow down timing</span></span>
* <span data-ttu-id="abc72-163">Permitir que o usuário ver o mundo em segundo plano</span><span class="sxs-lookup"><span data-stu-id="abc72-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="abc72-164">**O que evitar**</span><span class="sxs-lookup"><span data-stu-id="abc72-164">**What to avoid**</span></span>
* <span data-ttu-id="abc72-165">Não shake a câmera ou propositadamente bloqueá-la para 3DOF (apenas orientação, nenhuma conversão), ele pode fazer com que os usuários não se sinta confortável.</span><span class="sxs-lookup"><span data-stu-id="abc72-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="abc72-166">Nenhum movimento abrupto.</span><span class="sxs-lookup"><span data-stu-id="abc72-166">No abrupt movement.</span></span> <span data-ttu-id="abc72-167">Se você precisar levar conteúdo de ou para o usuário, movê-lo lentamente e sem problemas em direção a eles para máximo conforto.</span><span class="sxs-lookup"><span data-stu-id="abc72-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="abc72-168">Os usuários serão reagir a menus grandes, chegando até eles.</span><span class="sxs-lookup"><span data-stu-id="abc72-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="abc72-169">Não acelerar ou ativar a câmera do usuário.</span><span class="sxs-lookup"><span data-stu-id="abc72-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="abc72-170">Os usuários são sensíveis a aceleração (angular e conversão).</span><span class="sxs-lookup"><span data-stu-id="abc72-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="abc72-171">Aproveite a perspectiva do usuário</span><span class="sxs-lookup"><span data-stu-id="abc72-171">Leverage the user's perspective</span></span>

<span data-ttu-id="abc72-172">Os usuários veem o mundo da realidade misturada por meio de exibições em dispositivos envolventes e holographic.</span><span class="sxs-lookup"><span data-stu-id="abc72-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="abc72-173">Em HoloLens, essa exibição é chamada a [quadro holográfico](holographic-frame.md).</span><span class="sxs-lookup"><span data-stu-id="abc72-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="abc72-174">No desenvolvimento de 2D, configurações e conteúdo acessado com frequência podem ser colocadas nos cantos de uma tela para torná-los facilmente acessíveis.</span><span class="sxs-lookup"><span data-stu-id="abc72-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="abc72-175">No entanto, nos aplicativos holográfico, o conteúdo nos cantos do modo de exibição do usuário pode ser desconfortável para acesso.</span><span class="sxs-lookup"><span data-stu-id="abc72-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="abc72-176">Nesse caso, o centro do quadro holográfico é o local principal para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="abc72-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="abc72-177">O usuário talvez precise ser guiado para ajudar a localizar os eventos importantes ou objetos além do modo de exibição de imediato.</span><span class="sxs-lookup"><span data-stu-id="abc72-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="abc72-178">Você pode usar as setas, trilhas de luz, movimentação do cabeçote de caractere, balões de pensamento, ponteiros, som espacial e prompts de voz para ajudar a orientar o usuário ao conteúdo importante em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abc72-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="abc72-179">É recomendável não bloqueio de conteúdo na tela de conforto do usuário.</span><span class="sxs-lookup"><span data-stu-id="abc72-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="abc72-180">Se você precisar manter o conteúdo no modo de exibição, coloque-o no mundo e tornar o conteúdo "tag-along" como o menu Iniciar.</span><span class="sxs-lookup"><span data-stu-id="abc72-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="abc72-181">Conteúdo que é retirado, juntamente com a perspectiva do usuário se sentirão mais natural no ambiente.</span><span class="sxs-lookup"><span data-stu-id="abc72-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="abc72-182">![No menu Iniciar segue o modo de exibição do usuário quando ele atinge a borda do quadro](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="abc72-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="abc72-183">*No menu Iniciar segue o modo de exibição do usuário quando ele atinge a borda do quadro*</span><span class="sxs-lookup"><span data-stu-id="abc72-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="abc72-184">Em HoloLens, hologramas se sentir reais quando eles se ajustarem dentro do quadro holográfico, pois eles não sejam cortados.</span><span class="sxs-lookup"><span data-stu-id="abc72-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="abc72-185">Os usuários se moverá para ver os limites de um holograma dentro do quadro.</span><span class="sxs-lookup"><span data-stu-id="abc72-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="abc72-186">Em HoloLens, é importante simplificar sua interface do usuário para se ajustar no modo de exibição do usuário e mantém o foco na ação principal.</span><span class="sxs-lookup"><span data-stu-id="abc72-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="abc72-187">Para fones imersivos em exposição, é importante manter a ilusão de um mundo virtual persistente dentro do campo de visão do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="abc72-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="abc72-188">Conforto do usuário</span><span class="sxs-lookup"><span data-stu-id="abc72-188">User comfort</span></span>

<span data-ttu-id="abc72-189">Para garantir a máxima [conforto](comfort.md) em telas de fone de ouvido, é importante para designers e desenvolvedores criar e apresentar o conteúdo de uma maneira que simule como humanos interpretam formas 3D e a posição relativa dos objetos no natural mundo.</span><span class="sxs-lookup"><span data-stu-id="abc72-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="abc72-190">De uma perspectiva de física, também é importante projetar o conteúdo que não exija fatiguing movimentos do pescoço ou braços.</span><span class="sxs-lookup"><span data-stu-id="abc72-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="abc72-191">Desenvolvendo para HoloLens ou fones imersivos em exposição, é importante renderizar elementos visuais para ambos os olhos.</span><span class="sxs-lookup"><span data-stu-id="abc72-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="abc72-192">Renderizar uma exibição de alerta em um olho só pode fazer uma interface difíceis de entender, bem como causando uneasiness olho e o cérebro do usuário.</span><span class="sxs-lookup"><span data-stu-id="abc72-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="abc72-193">Compartilhe sua experiência</span><span class="sxs-lookup"><span data-stu-id="abc72-193">Share your experience</span></span>

<span data-ttu-id="abc72-194">Usando o [misto captura realidade](mixed-reality-capture.md), os usuários podem capturar uma foto ou vídeo de sua experiência a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="abc72-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="abc72-195">Considere a possibilidade de experiências em seu aplicativo em que você talvez queira incentivar instantâneos ou vídeos.</span><span class="sxs-lookup"><span data-stu-id="abc72-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="abc72-196">Aproveite os elementos de interface do usuário básicos do Windows Mixed Reality inicial</span><span class="sxs-lookup"><span data-stu-id="abc72-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="abc72-197">Assim como a experiência de PC do Windows é iniciado com a área de trabalho, Windows Mixed Reality começa com a página inicial.</span><span class="sxs-lookup"><span data-stu-id="abc72-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="abc72-198">O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) usa nossa capacidade inata para compreender e navegar lugares 3D.</span><span class="sxs-lookup"><span data-stu-id="abc72-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="abc72-199">Com o HoloLens, sua página inicial é o espaço físico.</span><span class="sxs-lookup"><span data-stu-id="abc72-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="abc72-200">Com fones imersivos em exposição, sua página inicial é um lugar virtual.</span><span class="sxs-lookup"><span data-stu-id="abc72-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="abc72-201">Sua casa também é onde você usará o menu Iniciar para abrir e colocar aplicativos e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="abc72-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="abc72-202">Você pode preencher sua casa com conteúdo de realidade mista e multitarefa com o uso de vários aplicativos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="abc72-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="abc72-203">As coisas que você coloca na sua casa permanecem lá, mesmo se você reiniciar seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="abc72-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="abc72-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abc72-204">See also</span></span>
* [<span data-ttu-id="abc72-205">Mantenha o foco de direcionamento</span><span class="sxs-lookup"><span data-stu-id="abc72-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="abc72-206">Gestos</span><span class="sxs-lookup"><span data-stu-id="abc72-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="abc72-207">Design de voz</span><span class="sxs-lookup"><span data-stu-id="abc72-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="abc72-208">Controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="abc72-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="abc72-209">Design de som espacial</span><span class="sxs-lookup"><span data-stu-id="abc72-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="abc72-210">Design de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="abc72-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="abc72-211">Conforto</span><span class="sxs-lookup"><span data-stu-id="abc72-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="abc72-212">Navegando o Windows Mixed Reality inicial</span><span class="sxs-lookup"><span data-stu-id="abc72-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)

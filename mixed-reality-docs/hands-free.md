---
title: Viva voz
description: Otimizando seu aplicativo para as mãos
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade misturada, mãos gratuitas, olhar, direcionamento olhar, interação, design
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435076"
---
# <a name="hands-free"></a><span data-ttu-id="acbb9-104">Viva voz</span><span class="sxs-lookup"><span data-stu-id="acbb9-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="acbb9-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="acbb9-105">Scenarios</span></span>

<span data-ttu-id="acbb9-106">Conforme descrito na [visão geral do modelo de interação](interaction-fundamentals.md), depois de identificar os usuários e suas metas, pergunte-se quais desafios ambientais ou de situação eles podem enfrentar enquanto trabalham para realizar suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="acbb9-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="acbb9-107">Por exemplo, muitos usuários precisam usar suas mãos para realizar suas metas reais e terão dificuldade para interagir com uma interface baseada em controladores e mãos.</span><span class="sxs-lookup"><span data-stu-id="acbb9-107">For example, many users need to use their hands to accomplish their real-world goals, and they will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="acbb9-108">Alguns cenários específicos incluem:</span><span class="sxs-lookup"><span data-stu-id="acbb9-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="acbb9-109">Guiado por uma tarefa, enquanto as mãos do usuário estão ocupadas</span><span class="sxs-lookup"><span data-stu-id="acbb9-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="acbb9-110">Fazendo referência a materiais enquanto as mãos do usuário estão ocupadas</span><span class="sxs-lookup"><span data-stu-id="acbb9-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="acbb9-111">Fadiga mão</span><span class="sxs-lookup"><span data-stu-id="acbb9-111">Hand fatigue</span></span>
* <span data-ttu-id="acbb9-112">Luvas que não podem ser rastreados</span><span class="sxs-lookup"><span data-stu-id="acbb9-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="acbb9-113">Executando algo em suas mãos</span><span class="sxs-lookup"><span data-stu-id="acbb9-113">Carrying something in their hands</span></span>
* <span data-ttu-id="acbb9-114">Inconveniente social para executar gestos de grande mão</span><span class="sxs-lookup"><span data-stu-id="acbb9-114">Social awkwardness to perform large hand gestures</span></span>
* <span data-ttu-id="acbb9-115">Espaços apertados</span><span class="sxs-lookup"><span data-stu-id="acbb9-115">Tight spaces</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="acbb9-116">Modalidades sem intervenção</span><span class="sxs-lookup"><span data-stu-id="acbb9-116">Hands-free modalities</span></span>

### <a name="voice-inputvoice-inputmd"></a>[<span data-ttu-id="acbb9-117">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="acbb9-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="acbb9-118">Usar sua voz para comando e controlar uma interface oferece uma maneira conveniente de operar sem interrupções e usar atalhos para ignorar várias etapas de forma flexível, se desejado.</span><span class="sxs-lookup"><span data-stu-id="acbb9-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to flexibly skip multiple steps if desired.</span></span> <span data-ttu-id="acbb9-119">Com a entrada de voz, o usuário pode simplesmente ler o nome de qualquer botão para ativá-lo _("vê-lo, dizer")_ e conversar com um agente digital que pode realizar tarefas para você.</span><span class="sxs-lookup"><span data-stu-id="acbb9-119">With voice input, the user can simply read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="acbb9-120">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="acbb9-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="acbb9-121">Em algumas situações práticas, usar sua voz não é ideal ou até mesmo possível.</span><span class="sxs-lookup"><span data-stu-id="acbb9-121">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="acbb9-122">Ambientes de fábrica altos, privacidade ou normas sociais podem ser restrições.</span><span class="sxs-lookup"><span data-stu-id="acbb9-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="acbb9-123">O modelo de olhar + de duração permite que o usuário navegue por um aplicativo sem nenhuma entrada adicional além de seu olho ou olhar de cabeça: o usuário simplesmente mantém nuvens (com seus cabeçotes ou olhos) no destino e permanece lá por um momento para ativá-lo.</span><span class="sxs-lookup"><span data-stu-id="acbb9-123">The gaze + dwell model allows the user to navigate an app without any additional input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="acbb9-124">Para saber mais sobre as considerações de design individuais para olhar + acessation, confira os [olhos-olhar +](gaze-and-dwell-eyes.md) acessation e [Head-olhar +](gaze-and-dwell-head.md)acessation.</span><span class="sxs-lookup"><span data-stu-id="acbb9-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="acbb9-125">Transição para dentro e para fora de mãos gratuitas</span><span class="sxs-lookup"><span data-stu-id="acbb9-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="acbb9-126">Para esses cenários, liberar suas mãos de interagir com hologramas para comando e navegação pode variar de ser um requisito absoluto para operar o aplicativo, de ponta a ponta, a uma conveniência adicional de que o usuário pode fazer a transição para dentro e fora de qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="acbb9-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="acbb9-127">Se o requisito do aplicativo for que ele sempre será usado sem intervenções, seja usando a pesquisa, comandos de voz personalizados ou o comando de voz simples, "Select", certifique-se de fazer as acomodações apropriadas em sua interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="acbb9-127">If the requirement of the application is that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="acbb9-128">Se o seu usuário de destino precisar ser capaz de alternar de mãos para mãos gratuitas a seu critério, é importante levar os princípios a seguir em conta.</span><span class="sxs-lookup"><span data-stu-id="acbb9-128">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="acbb9-129">Suponha que o usuário já esteja no modo que deseja alternar para</span><span class="sxs-lookup"><span data-stu-id="acbb9-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="acbb9-130">Por exemplo, se o usuário estiver no chão de fábrica, observando uma referência de vídeo em seu HoloLens e decidir pegar uma chave inglesa para começar a trabalhar, ela provavelmente começaria a trabalhar em mãos sem precisar colocar a chave de fenda para pressionar um botão.</span><span class="sxs-lookup"><span data-stu-id="acbb9-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="acbb9-131">Ela deve ser capaz de invocar uma sessão de voz com um comando de voz, a pesquisa em uma interface do usuário já visível para iniciar a pesquisa ou dizer a palavra "Select".</span><span class="sxs-lookup"><span data-stu-id="acbb9-131">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="acbb9-132">O usuário deve ter a capacidade de:</span><span class="sxs-lookup"><span data-stu-id="acbb9-132">The user should have the ability to:</span></span> 
* <span data-ttu-id="acbb9-133">Mude para o hands sem intervenção</span><span class="sxs-lookup"><span data-stu-id="acbb9-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="acbb9-134">Mude para as mãos com suas mãos</span><span class="sxs-lookup"><span data-stu-id="acbb9-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="acbb9-135">Alternar para o controlador usando um controlador</span><span class="sxs-lookup"><span data-stu-id="acbb9-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="acbb9-136">Criar maneiras redundantes de alternar entre modos</span><span class="sxs-lookup"><span data-stu-id="acbb9-136">Create redundant ways to switch modes</span></span>
<span data-ttu-id="acbb9-137">Embora o primeiro princípio seja sobre o acesso, o segundo é sobre a disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="acbb9-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="acbb9-138">Não deve haver apenas uma única maneira de fazer a transição para dentro e para fora de um modo.</span><span class="sxs-lookup"><span data-stu-id="acbb9-138">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="acbb9-139">Alguns exemplos seriam:</span><span class="sxs-lookup"><span data-stu-id="acbb9-139">Some examples would be:</span></span> 
* <span data-ttu-id="acbb9-140">Um botão para iniciar as interações de voz</span><span class="sxs-lookup"><span data-stu-id="acbb9-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="acbb9-141">Um comando de voz para o qual fazer a transição, usando Head-olhar e a pesquisa</span><span class="sxs-lookup"><span data-stu-id="acbb9-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="acbb9-142">Adicionar um traço de baixo-claro</span><span class="sxs-lookup"><span data-stu-id="acbb9-142">Add a dash of drama</span></span>
<span data-ttu-id="acbb9-143">Uma opção de modo é um grande problema – é importante que, quando essas transições acontecem, elas sejam um interruptor explícito, até mesmo um drástico, para permitir que o usuário saiba o que aconteceu.</span><span class="sxs-lookup"><span data-stu-id="acbb9-143">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="acbb9-144">Lista de verificação de usabilidade</span><span class="sxs-lookup"><span data-stu-id="acbb9-144">Usability checklist</span></span>

<span data-ttu-id="acbb9-145">**O usuário pode fazer tudo e tudo sem intervenção, de ponta a ponta?**</span><span class="sxs-lookup"><span data-stu-id="acbb9-145">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="acbb9-146">Todos os interagir devem estar acessíveis sem intervenções</span><span class="sxs-lookup"><span data-stu-id="acbb9-146">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="acbb9-147">Certifique-se de que haja uma substituição para todos os gestos personalizados, como redimensionamento, colocação, passes, toques, etc.</span><span class="sxs-lookup"><span data-stu-id="acbb9-147">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="acbb9-148">Certifique-se de que o usuário tenha o controle seguro de presença, posicionamento e detalhes de interface do usuário em todos os momentos</span><span class="sxs-lookup"><span data-stu-id="acbb9-148">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="acbb9-149">Obtendo a interface do usuário fora do caminho</span><span class="sxs-lookup"><span data-stu-id="acbb9-149">Getting UI out of the way</span></span>
    * <span data-ttu-id="acbb9-150">Endereçando a interface do usuário que está fora do campo de visão (FOV)</span><span class="sxs-lookup"><span data-stu-id="acbb9-150">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="acbb9-151">Quanto vejo, onde, quando</span><span class="sxs-lookup"><span data-stu-id="acbb9-151">How much I see, where, when</span></span>

<span data-ttu-id="acbb9-152">**A mecânica da interação está sendo ensinada e reforçada com a capacidades correta?**</span><span class="sxs-lookup"><span data-stu-id="acbb9-152">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="acbb9-153">O usuário entende...</span><span class="sxs-lookup"><span data-stu-id="acbb9-153">Does the user understand ...</span></span>
* <span data-ttu-id="acbb9-154">... Em que modo eles estão?</span><span class="sxs-lookup"><span data-stu-id="acbb9-154">... What mode they are in?</span></span>
* <span data-ttu-id="acbb9-155">... O que eles podem fazer neste modo?</span><span class="sxs-lookup"><span data-stu-id="acbb9-155">... What they can do in this mode?</span></span>
* <span data-ttu-id="acbb9-156">... O que é o estado atual?</span><span class="sxs-lookup"><span data-stu-id="acbb9-156">... What is the current state?</span></span>
* <span data-ttu-id="acbb9-157">... Como eles podem fazer a transição?</span><span class="sxs-lookup"><span data-stu-id="acbb9-157">... How they can transition out?</span></span>
    
<span data-ttu-id="acbb9-158">**A interface do usuário é otimizada para mãos gratuitas?**</span><span class="sxs-lookup"><span data-stu-id="acbb9-158">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="acbb9-159">Exemplo: a capacidades de pesquisa não é interna a padrões 2D típicos</span><span class="sxs-lookup"><span data-stu-id="acbb9-159">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="acbb9-160">Exemplo: o direcionamento de voz é melhor com o realce de objeto</span><span class="sxs-lookup"><span data-stu-id="acbb9-160">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="acbb9-161">Exemplo: as interações de voz são melhores com legendas que precisam ser ativadas</span><span class="sxs-lookup"><span data-stu-id="acbb9-161">Example: Voice interactions are better with captions that need to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="acbb9-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acbb9-162">See also</span></span>
* [<span data-ttu-id="acbb9-163">Acompanhamento de olho no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="acbb9-163">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="acbb9-164">Olhar e confirmar</span><span class="sxs-lookup"><span data-stu-id="acbb9-164">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="acbb9-165">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="acbb9-165">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="acbb9-166">Manipulação de mãos direta</span><span class="sxs-lookup"><span data-stu-id="acbb9-166">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="acbb9-167">Gestos práticos</span><span class="sxs-lookup"><span data-stu-id="acbb9-167">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="acbb9-168">Ponto de mãos e confirmação</span><span class="sxs-lookup"><span data-stu-id="acbb9-168">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="acbb9-169">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="acbb9-169">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="acbb9-170">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="acbb9-170">Voice input</span></span>](voice-input.md)

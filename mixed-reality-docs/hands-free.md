---
title: Viva voz
description: Otimizando seu aplicativo para as mãos
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade misturada, mãos gratuitas, olhar, direcionamento olhar, interação, design
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414391"
---
# <a name="hands-free"></a><span data-ttu-id="b8ac0-104">Viva voz</span><span class="sxs-lookup"><span data-stu-id="b8ac0-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="b8ac0-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="b8ac0-105">Scenarios</span></span>

<span data-ttu-id="b8ac0-106">Conforme descrito na [visão geral do modelo de interação](interaction-fundamentals.md), depois de identificar os usuários e suas metas, pergunte-se quais desafios ambientais ou de situação eles podem enfrentar enquanto trabalham para realizar suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="b8ac0-107">Por exemplo, muitos usuários precisam usar suas mãos para realizar suas metas reais e terão dificuldade para interagir com uma interface baseada em controladores e mãos.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="b8ac0-108">Alguns cenários específicos podem ser:</span><span class="sxs-lookup"><span data-stu-id="b8ac0-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="b8ac0-109">Guiado por uma tarefa, enquanto as mãos estão ocupadas</span><span class="sxs-lookup"><span data-stu-id="b8ac0-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="b8ac0-110">Fazendo referência a materiais enquanto suas mãos estão ocupadas</span><span class="sxs-lookup"><span data-stu-id="b8ac0-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="b8ac0-111">Fadiga mão</span><span class="sxs-lookup"><span data-stu-id="b8ac0-111">Hand fatigue</span></span>
* <span data-ttu-id="b8ac0-112">Luvas que não podem ser rastreados</span><span class="sxs-lookup"><span data-stu-id="b8ac0-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="b8ac0-113">Carregando algo</span><span class="sxs-lookup"><span data-stu-id="b8ac0-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="b8ac0-114">Modalidades sem intervenção</span><span class="sxs-lookup"><span data-stu-id="b8ac0-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="b8ac0-115">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="b8ac0-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="b8ac0-116">Usar sua voz para comando e controlar uma interface só pode permitir que o usuário opere Handsfree, mas também ignore várias etapas.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="b8ac0-117">O uso dessa modalidade pode variar de permitir que o usuário simplesmente Leia o nome de qualquer botão para ativá-lo, como em consulte-it-diga-it, para conversar com um agente que pode realizar tarefas para você.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="b8ac0-118">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="b8ac0-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="b8ac0-119">Em algumas situações práticas, usar sua voz não é ideal ou até mesmo possível.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="b8ac0-120">Ambientes de fábrica altos, privacidade ou normas sociais podem ser restrições.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="b8ac0-121">O modelo Head olhar + de pesquisa permite que o usuário navegue pelo aplicativo usando seu vetor de cabeçalho para apontar, enquanto o modo de navegação ou de pausar em um botão o ativará após um determinado período de tempo, geralmente em cerca de 1 segundo ou assim por diante.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="b8ac0-122">Transição para dentro e para fora de mãos gratuitas</span><span class="sxs-lookup"><span data-stu-id="b8ac0-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="b8ac0-123">Para esses cenários, liberar suas mãos de interagir com hologramas para comando e navegação pode variar de ser um requisito absoluto para operar o aplicativo, de ponta a ponta, a uma conveniência adicional de que o usuário pode fazer a transição para dentro e fora de qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="b8ac0-124">Se o requisito do aplicativo for que ele sempre será usado sem intervenções, seja usando a pesquisa, comandos de voz ou o comando de voz simples, "Select", certifique-se de tornar o accomodations apropriado em sua interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="b8ac0-125">Se o seu usuário de destino precisar ser capaz de alternar de mãos para mãos gratuitas a seu critério, é importante levar os princípios a seguir em conta.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="b8ac0-126">Suponha que o usuário já esteja no modo que deseja alternar para</span><span class="sxs-lookup"><span data-stu-id="b8ac0-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="b8ac0-127">Por exemplo, se o usuário estiver no chão de fábrica, observando uma referência de vídeo em seu Hololens e decidir pegar uma chave de fenda para começar a trabalhar, ela provavelmente começaria a trabalhar no handsfree sem precisar colocar a chave de fenda para pressionar um botão.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="b8ac0-128">Ela deve ser capaz de invocar uma sessão de voz com um comando de voz, a pesquisa em uma interface do usuário já visível para iniciar a pesquisa ou dizer a palavra "Select".</span><span class="sxs-lookup"><span data-stu-id="b8ac0-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="b8ac0-129">O usuário deve ter a capacidade de:</span><span class="sxs-lookup"><span data-stu-id="b8ac0-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="b8ac0-130">Mude para o hands sem intervenção</span><span class="sxs-lookup"><span data-stu-id="b8ac0-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="b8ac0-131">Mude para as mãos com suas mãos</span><span class="sxs-lookup"><span data-stu-id="b8ac0-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="b8ac0-132">Alternar para o controlador usando um controlador</span><span class="sxs-lookup"><span data-stu-id="b8ac0-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="b8ac0-133">Criar maneiras redundantes de alternar entre modos</span><span class="sxs-lookup"><span data-stu-id="b8ac0-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="b8ac0-134">Embora o primeiro princípio seja sobre o acesso, o segundo é sobre a disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="b8ac0-135">Não deve haver apenas uma única maneira de fazer a transição para dentro e para fora de um modo.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="b8ac0-136">Alguns exemplos seriam:</span><span class="sxs-lookup"><span data-stu-id="b8ac0-136">Some examples would be:</span></span> 
* <span data-ttu-id="b8ac0-137">Um botão para iniciar as interações de voz</span><span class="sxs-lookup"><span data-stu-id="b8ac0-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="b8ac0-138">Um comando de voz para fazer a transição para usar o olhar + a pesquisa</span><span class="sxs-lookup"><span data-stu-id="b8ac0-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="b8ac0-139">Adicionar um traço de baixo-claro</span><span class="sxs-lookup"><span data-stu-id="b8ac0-139">Add a dash of drama</span></span>
<span data-ttu-id="b8ac0-140">Uma opção de modo é um grande problema – é importante que, quando essas transições acontecem, elas sejam um interruptor explícito e até mesmo drástico, para permitir que o usuário saiba o que aconteceu.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="b8ac0-141">Lista de verificação de usabilidade</span><span class="sxs-lookup"><span data-stu-id="b8ac0-141">Usability checklist</span></span>

<span data-ttu-id="b8ac0-142">**O usuário pode fazer tudo e tudo sem intervenção, de ponta a ponta?**</span><span class="sxs-lookup"><span data-stu-id="b8ac0-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="b8ac0-143">Todos os interactible devem estar acessíveis sem intervenções</span><span class="sxs-lookup"><span data-stu-id="b8ac0-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="b8ac0-144">Certifique-se de que haja uma substituição para todos os gestos personalizados, como redimensionamento, colocação, passes, toques, etc.</span><span class="sxs-lookup"><span data-stu-id="b8ac0-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="b8ac0-145">Certifique-se de que o usuário tenha o controle seguro de presença, posicionamento e detalhes de interface do usuário em todos os momentos</span><span class="sxs-lookup"><span data-stu-id="b8ac0-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="b8ac0-146">Obtendo a interface do usuário fora do caminho</span><span class="sxs-lookup"><span data-stu-id="b8ac0-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="b8ac0-147">Endereçando a interface do usuário que está fora do campo de visão (FOV)</span><span class="sxs-lookup"><span data-stu-id="b8ac0-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="b8ac0-148">Quanto vejo, onde, quando</span><span class="sxs-lookup"><span data-stu-id="b8ac0-148">How much I see, where, when</span></span>

<span data-ttu-id="b8ac0-149">**A mecânica da interação está sendo ensinada e reforçada com a capacidades correta?**</span><span class="sxs-lookup"><span data-stu-id="b8ac0-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="b8ac0-150">O usuário entende...</span><span class="sxs-lookup"><span data-stu-id="b8ac0-150">Does the user understand ...</span></span>
* <span data-ttu-id="b8ac0-151">... Em que modo eles estão?</span><span class="sxs-lookup"><span data-stu-id="b8ac0-151">... What mode they are in?</span></span>
* <span data-ttu-id="b8ac0-152">... O que eles podem fazer neste modo?</span><span class="sxs-lookup"><span data-stu-id="b8ac0-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="b8ac0-153">... O que é o estado atual?</span><span class="sxs-lookup"><span data-stu-id="b8ac0-153">... What is the current state?</span></span>
* <span data-ttu-id="b8ac0-154">... Como eles podem fazer a transição?</span><span class="sxs-lookup"><span data-stu-id="b8ac0-154">... How they can transition out?</span></span>
    
<span data-ttu-id="b8ac0-155">**A interface do usuário é otimizada para mãos gratuitas?**</span><span class="sxs-lookup"><span data-stu-id="b8ac0-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="b8ac0-156">Exemplo: Capacidades de pesquisa não são internos para padrões 2D típicos</span><span class="sxs-lookup"><span data-stu-id="b8ac0-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="b8ac0-157">Exemplo: O direcionamento de voz é melhor com o realce de objeto</span><span class="sxs-lookup"><span data-stu-id="b8ac0-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="b8ac0-158">Exemplo: As interações de voz são melhores com legendas que precisam ser ativadas</span><span class="sxs-lookup"><span data-stu-id="b8ac0-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="b8ac0-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8ac0-159">See also</span></span>
* [<span data-ttu-id="b8ac0-160">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="b8ac0-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b8ac0-161">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="b8ac0-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b8ac0-162">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="b8ac0-162">Point and commit with hands</span></span>](point-and-commit.md)

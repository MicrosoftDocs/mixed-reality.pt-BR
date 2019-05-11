---
title: Otimizando seu aplicativo para mãos livres
description: Otimizando seu aplicativo para mãos livres
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade misturada, viva-voz, mantenha o foco, olhares direcionamento, interação, design
ms.openlocfilehash: f39a9524831161997b59be6cf89b124fa5b29c78
ms.sourcegitcommit: d6d96d552ec10cd7e6502fbbc1905432e2878325
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524326"
---
# <a name="optimizing-your-app-for-hands-free"></a><span data-ttu-id="c9df2-104">Otimizando seu aplicativo para mãos livres</span><span class="sxs-lookup"><span data-stu-id="c9df2-104">Optimizing your app for hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="c9df2-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="c9df2-105">Scenarios</span></span>

<span data-ttu-id="c9df2-106">Conforme descrito na [visão geral do modelo de interação](interaction-fundamentals.md), depois de você ter identificado os usuários e suas metas, pergunte-se que desafios ambientais ou situacional eles poderá enfrentar como eles trabalham para realizar suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="c9df2-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="c9df2-107">Por exemplo, muitos usuários precisam usar suas mãos para alcançar seus objetivos do mundo real e será ter dificuldade para interagir com uma interface com base prática e controladores.</span><span class="sxs-lookup"><span data-stu-id="c9df2-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="c9df2-108">Alguns cenários específicos podem ser:</span><span class="sxs-lookup"><span data-stu-id="c9df2-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="c9df2-109">Que está sendo guiado por meio de uma tarefa, enquanto as mãos estão ocupadas</span><span class="sxs-lookup"><span data-stu-id="c9df2-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="c9df2-110">Referenciando materiais enquanto suas mãos estão ocupadas</span><span class="sxs-lookup"><span data-stu-id="c9df2-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="c9df2-111">Fadiga mão</span><span class="sxs-lookup"><span data-stu-id="c9df2-111">Hand fatigue</span></span>
* <span data-ttu-id="c9df2-112">Luvas que não podem ser controladas</span><span class="sxs-lookup"><span data-stu-id="c9df2-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="c9df2-113">Portando algo</span><span class="sxs-lookup"><span data-stu-id="c9df2-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="c9df2-114">Viva-voz modalidades</span><span class="sxs-lookup"><span data-stu-id="c9df2-114">Hands-free modalities</span></span>

### <a name="voice-commanding"></a><span data-ttu-id="c9df2-115">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="c9df2-115">Voice commanding</span></span>

<span data-ttu-id="c9df2-116">Usando a voz para comando e controle de que uma interface pode não apenas permitir que o usuário opere para mãos livres, mas também ignorar várias etapas.</span><span class="sxs-lookup"><span data-stu-id="c9df2-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="c9df2-117">O uso desse modalidade pode variar de permitindo que o usuário simplesmente lê o nome do qualquer botão em voz alta para ativá-lo, como em Consulte-it-say-it, para conversar com um agente que pode realizar tarefas para você.</span><span class="sxs-lookup"><span data-stu-id="c9df2-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>

* [<span data-ttu-id="c9df2-118">Design de voz</span><span class="sxs-lookup"><span data-stu-id="c9df2-118">Voice design</span></span>](voice-design.md)


### <a name="head-gaze-and-dwell"></a><span data-ttu-id="c9df2-119">Olhar head e duração</span><span class="sxs-lookup"><span data-stu-id="c9df2-119">Head gaze and dwell</span></span>

<span data-ttu-id="c9df2-120">Em algumas situações viva-voz, usando a voz não é ideal ou até mesmo possível.</span><span class="sxs-lookup"><span data-stu-id="c9df2-120">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="c9df2-121">Ambientes fabris alto, privacidade ou sociais normas podem ser restrições.</span><span class="sxs-lookup"><span data-stu-id="c9df2-121">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="c9df2-122">O cabeçalho olhares + lidam bem com modelo permite que o usuário navegue o aplicativo usando seu principal vetor para apontar ao remanescentes, ou dwelling em um botão irá ativá-lo após um determinado período de tempo (normalmente, de cerca de 1 segundo ou menos).</span><span class="sxs-lookup"><span data-stu-id="c9df2-122">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 

* [<span data-ttu-id="c9df2-123">Focar e esperar</span><span class="sxs-lookup"><span data-stu-id="c9df2-123">Gaze and dwell</span></span>](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="c9df2-124">A transição para dentro e fora de mãos livres</span><span class="sxs-lookup"><span data-stu-id="c9df2-124">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="c9df2-125">Liberar as mãos de interagir com hologramas para comandos e navegação pode variar para esses cenários, seja um requisito absoluto para operar o aplicativo, de ponta a ponta para uma conveniência adicional que o usuário pode fazer a transição da qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="c9df2-125">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="c9df2-126">Se o requisito do aplicativo é que ela será sempre usada viva-voz, usando o único comando de voz, comandos de voz ou duração, "select" e, em seguida, certifique-se de fazer as acomodações apropriadas em sua interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c9df2-126">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="c9df2-127">Se o usuário de destino precisa ser capaz de alternar de mãos para mãos livres a seu critério, é importante levar esses princípios em conta:</span><span class="sxs-lookup"><span data-stu-id="c9df2-127">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="c9df2-128">Suponha que o usuário já está no modo que eles desejam mudar para</span><span class="sxs-lookup"><span data-stu-id="c9df2-128">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="c9df2-129">Por exemplo, se o usuário estiver no chão de fábrica, assistindo a uma referência de vídeo em seu Hololens e decide pegar uma chave inglesa para começar a trabalhar, ela provavelmente gostaria de começar a trabalhar para mãos livres sem a necessidade de criar a chave inglesa ao pressionar um botão.</span><span class="sxs-lookup"><span data-stu-id="c9df2-129">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="c9df2-130">Ela deve ser capaz de invocar uma sessão de voz com um comando de voz, lidam bem com já visíveis da interface do usuário para começar a duração ou, digamos que a palavra "select".</span><span class="sxs-lookup"><span data-stu-id="c9df2-130">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="c9df2-131">O usuário deve ter a capacidade de:</span><span class="sxs-lookup"><span data-stu-id="c9df2-131">The user should have the ability to:</span></span> 
* <span data-ttu-id="c9df2-132">Alterne para mãos livres, enquanto para mãos livres</span><span class="sxs-lookup"><span data-stu-id="c9df2-132">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="c9df2-133">Alterne para mãos com suas mãos</span><span class="sxs-lookup"><span data-stu-id="c9df2-133">Switch to hands with your hands</span></span>
* <span data-ttu-id="c9df2-134">Alterne para o controlador usando um controlador</span><span class="sxs-lookup"><span data-stu-id="c9df2-134">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="c9df2-135">Criar formas redundantes para alternar entre modos</span><span class="sxs-lookup"><span data-stu-id="c9df2-135">Create redundant ways to switch modes</span></span>
<span data-ttu-id="c9df2-136">Embora seja o primeiro princípio sobre o acesso, a segunda é sobre a disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="c9df2-136">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="c9df2-137">Apenas não deve haver uma única maneira de fazer a transição para dentro e fora de um modo.</span><span class="sxs-lookup"><span data-stu-id="c9df2-137">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="c9df2-138">Alguns exemplos seriam:</span><span class="sxs-lookup"><span data-stu-id="c9df2-138">Some examples would be:</span></span> 
* <span data-ttu-id="c9df2-139">Um botão para começar a interações de voz</span><span class="sxs-lookup"><span data-stu-id="c9df2-139">A button to begin voice interactions</span></span>
* <span data-ttu-id="c9df2-140">Um comando de voz para fazer a transição usando olhar + duração</span><span class="sxs-lookup"><span data-stu-id="c9df2-140">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="c9df2-141">Adicionar um traço de drama</span><span class="sxs-lookup"><span data-stu-id="c9df2-141">Add a dash of drama</span></span>
<span data-ttu-id="c9df2-142">Uma opção do modo é muito importante – é importante que quando ocorrem essas transições, que eles sejam uma opção explícita, até mesmo dramática, para que o usuário saiba o que aconteceu.</span><span class="sxs-lookup"><span data-stu-id="c9df2-142">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="c9df2-143">Lista de verificação de usabilidade</span><span class="sxs-lookup"><span data-stu-id="c9df2-143">Usability checklist</span></span>

<span data-ttu-id="c9df2-144">**O usuário pode fazer tudo e qualquer coisa viva-voz, de ponta a ponta?**</span><span class="sxs-lookup"><span data-stu-id="c9df2-144">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="c9df2-145">Cada interactible deve ser acessível viva-voz</span><span class="sxs-lookup"><span data-stu-id="c9df2-145">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="c9df2-146">Certifique-se de que há uma substituição para todos os gestos personalizados, como o redimensionamento, colocando, dedo, toques, etc.</span><span class="sxs-lookup"><span data-stu-id="c9df2-146">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="c9df2-147">Certifique-se de que o usuário tem certeza de controle de presença de interface do usuário, o posicionamento, o detalhamento em todos os momentos</span><span class="sxs-lookup"><span data-stu-id="c9df2-147">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="c9df2-148">Obtendo a interface do usuário do caminho</span><span class="sxs-lookup"><span data-stu-id="c9df2-148">Getting UI out of the way</span></span>
    * <span data-ttu-id="c9df2-149">Endereçamento de interface do usuário que está fora do campo de exibição (FOV)</span><span class="sxs-lookup"><span data-stu-id="c9df2-149">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="c9df2-150">Quanto eu vejo, onde, quando</span><span class="sxs-lookup"><span data-stu-id="c9df2-150">How much I see, where, when</span></span>

<span data-ttu-id="c9df2-151">**São a mecânica da interação que está sendo ensinada e reforçada com as capacidades certas?**</span><span class="sxs-lookup"><span data-stu-id="c9df2-151">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="c9df2-152">O usuário entender...</span><span class="sxs-lookup"><span data-stu-id="c9df2-152">Does the user understand ...</span></span>
* <span data-ttu-id="c9df2-153">... O modo que eles estão em?</span><span class="sxs-lookup"><span data-stu-id="c9df2-153">... What mode they are in?</span></span>
* <span data-ttu-id="c9df2-154">... O que eles podem fazer nesse modo?</span><span class="sxs-lookup"><span data-stu-id="c9df2-154">... What they can do in this mode?</span></span>
* <span data-ttu-id="c9df2-155">... O que é o estado atual?</span><span class="sxs-lookup"><span data-stu-id="c9df2-155">... What is the current state?</span></span>
* <span data-ttu-id="c9df2-156">... Como eles podem fazer a transição-out?</span><span class="sxs-lookup"><span data-stu-id="c9df2-156">... How they can transition out?</span></span>
    
<span data-ttu-id="c9df2-157">**É a interface do usuário otimizada para mãos livres?**</span><span class="sxs-lookup"><span data-stu-id="c9df2-157">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="c9df2-158">Ex.</span><span class="sxs-lookup"><span data-stu-id="c9df2-158">Ex.</span></span> <span data-ttu-id="c9df2-159">Capacidades de duração não são recursos internas para os padrões típicos de 2D</span><span class="sxs-lookup"><span data-stu-id="c9df2-159">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="c9df2-160">Ex.</span><span class="sxs-lookup"><span data-stu-id="c9df2-160">Ex.</span></span> <span data-ttu-id="c9df2-161">O direcionamento de voz é melhor com realce de objeto</span><span class="sxs-lookup"><span data-stu-id="c9df2-161">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="c9df2-162">Ex.</span><span class="sxs-lookup"><span data-stu-id="c9df2-162">Ex.</span></span> <span data-ttu-id="c9df2-163">Interações de voz são melhores com legendas que precisam ser ligado</span><span class="sxs-lookup"><span data-stu-id="c9df2-163">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="c9df2-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9df2-164">See also</span></span>
* [<span data-ttu-id="c9df2-165">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="c9df2-165">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="c9df2-166">Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="c9df2-166">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c9df2-167">Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="c9df2-167">Point and commit</span></span>](point-and-commit.md)

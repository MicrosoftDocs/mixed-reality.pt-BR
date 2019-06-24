---
title: Viva voz
description: Otimizando seu aplicativo para mãos livres
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade misturada, viva-voz, mantenha o foco, olhares direcionamento, interação, design
ms.openlocfilehash: 4d21fa10eabb446565bddebccdbde5e2e7bcc72a
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326149"
---
# <a name="hands-free"></a><span data-ttu-id="d7975-104">Viva voz</span><span class="sxs-lookup"><span data-stu-id="d7975-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="d7975-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="d7975-105">Scenarios</span></span>

<span data-ttu-id="d7975-106">Conforme descrito na [visão geral do modelo de interação](interaction-fundamentals.md), depois de você ter identificado os usuários e suas metas, pergunte-se que desafios ambientais ou situacional eles poderá enfrentar como eles trabalham para realizar suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="d7975-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="d7975-107">Por exemplo, muitos usuários precisam usar suas mãos atingir seus objetivos do mundo real e terá dificuldade para interagir com uma interface com base prática e controladores.</span><span class="sxs-lookup"><span data-stu-id="d7975-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="d7975-108">Alguns cenários específicos podem ser:</span><span class="sxs-lookup"><span data-stu-id="d7975-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="d7975-109">Que está sendo guiado por meio de uma tarefa, enquanto as mãos estão ocupadas</span><span class="sxs-lookup"><span data-stu-id="d7975-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="d7975-110">Referenciando materiais enquanto suas mãos estão ocupadas</span><span class="sxs-lookup"><span data-stu-id="d7975-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="d7975-111">Fadiga mão</span><span class="sxs-lookup"><span data-stu-id="d7975-111">Hand fatigue</span></span>
* <span data-ttu-id="d7975-112">Luvas que não podem ser controladas</span><span class="sxs-lookup"><span data-stu-id="d7975-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="d7975-113">Portando algo</span><span class="sxs-lookup"><span data-stu-id="d7975-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="d7975-114">Viva-voz modalidades</span><span class="sxs-lookup"><span data-stu-id="d7975-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="d7975-115">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="d7975-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="d7975-116">Usando a voz para comando e controle de que uma interface pode não apenas permitir que o usuário opere para mãos livres, mas também ignorar várias etapas.</span><span class="sxs-lookup"><span data-stu-id="d7975-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="d7975-117">O uso desse modalidade pode variar de permitindo que o usuário simplesmente ler nome do qualquer botão em voz alta para ativá-lo, como em Consulte-it-say-it, para conversar com um agente que pode realizar tarefas para você.</span><span class="sxs-lookup"><span data-stu-id="d7975-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="d7975-118">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="d7975-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="d7975-119">Em algumas situações viva-voz, usando a voz não é ideal ou até mesmo possível.</span><span class="sxs-lookup"><span data-stu-id="d7975-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="d7975-120">Ambientes fabris alto, privacidade ou sociais normas podem ser restrições.</span><span class="sxs-lookup"><span data-stu-id="d7975-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="d7975-121">O cabeçalho olhares + lidam bem com modelo permite que o usuário navegue o aplicativo usando seu principal vetor para apontar ao remanescentes, ou dwelling em um botão irá ativá-lo após um determinado período de tempo, tpically aproximadamente 1 segundo mais ou menos.</span><span class="sxs-lookup"><span data-stu-id="d7975-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, tpically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-freey"></a><span data-ttu-id="d7975-122">A transição para dentro e fora de mãos freey</span><span class="sxs-lookup"><span data-stu-id="d7975-122">Transitioning in and out of hands-freey</span></span>

<span data-ttu-id="d7975-123">Para esses cenários, liberar as mãos de interagir com hologramas para comandos e navegação pode variar de sendo um requisito absoluto para operar o aplicativo ponta a ponta, para uma conveniência adicional que o usuário pode fazer a transição do qualquer tempo.</span><span class="sxs-lookup"><span data-stu-id="d7975-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="d7975-124">Se o requisito do aplicativo é que ela será sempre usada viva-voz, usando o único comando de voz, comandos de voz ou duração, "select" e, em seguida, certifique-se de fazer as acomodações apropriadas em sua interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d7975-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="d7975-125">Se o usuário de destino precisa ser capaz de alternar de mãos para mãos livres a seu critério, em seguida, é importante considerar os seguintes princípios.</span><span class="sxs-lookup"><span data-stu-id="d7975-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="d7975-126">Suponha que o usuário já está no modo que eles desejam mudar para</span><span class="sxs-lookup"><span data-stu-id="d7975-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="d7975-127">Por exemplo, se o usuário está no chão de fábrica, assistir a uma referência de vídeo no seu Hololens e decide pegar uma chave inglesa para começar a trabalhar, ela provavelmente seria começar a trabalhar para mãos livres sem a necessidade de criar a chave inglesa ao pressionar um botão.</span><span class="sxs-lookup"><span data-stu-id="d7975-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="d7975-128">Ela deve ser capaz de invocar uma sessão de voz com um comando de voz, lidam bem com uma interface do usuário já visível para começar a duração ou, digamos que a palavra "select".</span><span class="sxs-lookup"><span data-stu-id="d7975-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="d7975-129">O usuário deve ter a capacidade de:</span><span class="sxs-lookup"><span data-stu-id="d7975-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="d7975-130">Alterne para mãos livres, enquanto para mãos livres</span><span class="sxs-lookup"><span data-stu-id="d7975-130">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="d7975-131">Alterne para mãos com suas mãos</span><span class="sxs-lookup"><span data-stu-id="d7975-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="d7975-132">Alterne para o controlador usando um controlador</span><span class="sxs-lookup"><span data-stu-id="d7975-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="d7975-133">Criar formas redundantes para alternar entre modos</span><span class="sxs-lookup"><span data-stu-id="d7975-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="d7975-134">Embora seja o primeiro princípio sobre o acesso, a segunda é sobre a disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="d7975-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="d7975-135">Apenas não deve haver uma única maneira de fazer a transição para dentro e fora de um modo.</span><span class="sxs-lookup"><span data-stu-id="d7975-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="d7975-136">Alguns exemplos seriam:</span><span class="sxs-lookup"><span data-stu-id="d7975-136">Some examples would be:</span></span> 
* <span data-ttu-id="d7975-137">Um botão para começar a interações de voz</span><span class="sxs-lookup"><span data-stu-id="d7975-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="d7975-138">Um comando de voz para fazer a transição usando olhar + duração</span><span class="sxs-lookup"><span data-stu-id="d7975-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="d7975-139">Adicionar um traço de drama</span><span class="sxs-lookup"><span data-stu-id="d7975-139">Add a dash of drama</span></span>
<span data-ttu-id="d7975-140">Uma opção do modo é muito importante – é importante que quando essas transições acontecem que eles sejam uma opção explícita, até mesmo dramática, para que o usuário saiba o que aconteceu.</span><span class="sxs-lookup"><span data-stu-id="d7975-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="d7975-141">Lista de verificação de usabilidade</span><span class="sxs-lookup"><span data-stu-id="d7975-141">Usability checklist</span></span>

<span data-ttu-id="d7975-142">**O usuário pode fazer tudo e qualquer coisa viva-voz, de ponta a ponta?**</span><span class="sxs-lookup"><span data-stu-id="d7975-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="d7975-143">Cada interactible deve ser acessível viva-voz</span><span class="sxs-lookup"><span data-stu-id="d7975-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="d7975-144">Certifique-se de que há uma substituição para todos os gestos personalizados, como o redimensionamento, colocando, dedo, toques, etc.</span><span class="sxs-lookup"><span data-stu-id="d7975-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="d7975-145">Certifique-se de que o usuário tem certeza de controle de presença, posicionamento e detalhamento da interface do usuário em todos os momentos</span><span class="sxs-lookup"><span data-stu-id="d7975-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="d7975-146">Obtendo a interface do usuário do caminho</span><span class="sxs-lookup"><span data-stu-id="d7975-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="d7975-147">Endereçamento de interface do usuário que está fora do campo de exibição (FOV)</span><span class="sxs-lookup"><span data-stu-id="d7975-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="d7975-148">Quanto eu vejo, onde, quando</span><span class="sxs-lookup"><span data-stu-id="d7975-148">How much I see, where, when</span></span>

<span data-ttu-id="d7975-149">**São a mecânica da interação que está sendo ensinada e reforçada com as capacidades certas?**</span><span class="sxs-lookup"><span data-stu-id="d7975-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="d7975-150">O usuário entender...</span><span class="sxs-lookup"><span data-stu-id="d7975-150">Does the user understand ...</span></span>
* <span data-ttu-id="d7975-151">... O modo que eles estão em?</span><span class="sxs-lookup"><span data-stu-id="d7975-151">... What mode they are in?</span></span>
* <span data-ttu-id="d7975-152">... O que eles podem fazer nesse modo?</span><span class="sxs-lookup"><span data-stu-id="d7975-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="d7975-153">... O que é o estado atual?</span><span class="sxs-lookup"><span data-stu-id="d7975-153">... What is the current state?</span></span>
* <span data-ttu-id="d7975-154">... Como eles podem fazer a transição-out?</span><span class="sxs-lookup"><span data-stu-id="d7975-154">... How they can transition out?</span></span>
    
<span data-ttu-id="d7975-155">**É a interface do usuário otimizada para mãos livres?**</span><span class="sxs-lookup"><span data-stu-id="d7975-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="d7975-156">Exemplo: Capacidades de duração não são recursos internas para os padrões típicos de 2D</span><span class="sxs-lookup"><span data-stu-id="d7975-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="d7975-157">Exemplo: O direcionamento de voz é melhor com realce de objeto</span><span class="sxs-lookup"><span data-stu-id="d7975-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="d7975-158">Exemplo: Interações de voz são melhores com legendas que precisam ser ligado</span><span class="sxs-lookup"><span data-stu-id="d7975-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="d7975-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7975-159">See also</span></span>
* [<span data-ttu-id="d7975-160">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="d7975-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d7975-161">Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="d7975-161">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d7975-162">Apontar e confirmar</span><span class="sxs-lookup"><span data-stu-id="d7975-162">Point and commit</span></span>](point-and-commit.md)

---
title: Focar com a cabeça e esperar
description: Visão geral do modelo de entrada de focar com a cabeça e esperar
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Realidade Misturada, focar, esperar, interação, design
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439307"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="635ce-104">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="635ce-104">Head-gaze and dwell</span></span>

<span data-ttu-id="635ce-105">Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis.</span><span class="sxs-lookup"><span data-stu-id="635ce-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="635ce-106">Os comandos de voz, assim como os gestos, podem não ser confiáveis em determinados contextos (por exemplo, em ambientes excessivamente barulhentos).</span><span class="sxs-lookup"><span data-stu-id="635ce-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="635ce-107">Além disso, usar a voz para controlar computadores não é universalmente comum, mas certamente está ganhando força!</span><span class="sxs-lookup"><span data-stu-id="635ce-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="635ce-108">O modelo de focar com a cabeça e esperar oferece o mecanismo mais familiar e fácil de dominar para trabalhar sem utilizar as mãos no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="635ce-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="635ce-109">Além disso, esse modelo é 100% confiável, independentemente da interferência de ruído e das restrições de silêncio do ambiente operacional.</span><span class="sxs-lookup"><span data-stu-id="635ce-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="635ce-110">Cenários</span><span class="sxs-lookup"><span data-stu-id="635ce-110">Scenarios</span></span>

<span data-ttu-id="635ce-111">A olhar e a pesquisa são Excel em cenários nos quais as mãos de uma pessoa estão ocupadas com outras tarefas, e a voz não é 100% confiável ou está disponível devido a restrições ambientais ou sociais.</span><span class="sxs-lookup"><span data-stu-id="635ce-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="635ce-112">Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro.</span><span class="sxs-lookup"><span data-stu-id="635ce-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="635ce-113">Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor.</span><span class="sxs-lookup"><span data-stu-id="635ce-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="635ce-114">O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="635ce-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="635ce-115">O Head-olhar e a pesquisa permitem que a pessoa que usa o HoloLens Navegue com confiança no material de referência sem interromper o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="635ce-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="635ce-116">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="635ce-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="635ce-117"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="635ce-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="635ce-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="635ce-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="635ce-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="635ce-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="635ce-120"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="635ce-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="635ce-121">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="635ce-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="635ce-122">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="635ce-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="635ce-123">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="635ce-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="635ce-124">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="635ce-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="635ce-125">Princípios do design</span><span class="sxs-lookup"><span data-stu-id="635ce-125">Design principles</span></span>

<span data-ttu-id="635ce-126">**Evite "olhar como uma arma"**</span><span class="sxs-lookup"><span data-stu-id="635ce-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="635ce-127">A ação de focar com a cabeça e esperar exige que o retorno visual seja intuitivo, mas seu excesso pode induzir a ansiedade.</span><span class="sxs-lookup"><span data-stu-id="635ce-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="635ce-128">Os retornos devem ajudar um usuário a saber o que está sendo focalizando, mas não selecionar automaticamente se essa não for sua intenção.</span><span class="sxs-lookup"><span data-stu-id="635ce-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="635ce-129">Ler textos, ícones e rótulos exige consideração adicional para dar tempo para a pessoa absorver as informações antes de selecionar.</span><span class="sxs-lookup"><span data-stu-id="635ce-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="635ce-130">**Buscar velocidade de Cachinhos dourados**</span><span class="sxs-lookup"><span data-stu-id="635ce-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="635ce-131">As interações de espera podem ter tempos diferentes com base no impacto na navegação: as funções usadas com mais frequência geralmente se beneficiam de tempos de preenchimento mais rápidos, enquanto que as funções mais consequentes podem se beneficiar de tempos de preenchimento mais longos.</span><span class="sxs-lookup"><span data-stu-id="635ce-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="635ce-132">Ao usar um efeito de preenchimento para mostrar esses tempos, curvas de animação da cor de preenchimento podem influenciar positivamente uma sensação de tempo mais rápido.</span><span class="sxs-lookup"><span data-stu-id="635ce-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="635ce-133">Consideração deve ser tomada para permitir a decisão do usuário a partir de substituições das velocidades de preenchimento rápidas/médias/lentas.</span><span class="sxs-lookup"><span data-stu-id="635ce-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="635ce-134">**Diga não-no para o efeito de Yo Yo**</span><span class="sxs-lookup"><span data-stu-id="635ce-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="635ce-135">O efeito ioiô é um padrão desconfortável de movimentação da cabeça que pode surgir quando o posicionamento do conteúdo e dos controles de focar com a cabeça e esperar força as pessoas a olharem para cima e para baixo repetidamente.</span><span class="sxs-lookup"><span data-stu-id="635ce-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="635ce-136">Por exemplo, uma barra de navegação de lista com o botão de olhar e de duração na parte inferior induzi um loop de-Look to acessation, look up in Results, olhe Down to acessation, etc. Esse padrão resultante é desconfortável e deve ser evitado colocando-se controles de navegação em um local centralizado que requer menos suporte.</span><span class="sxs-lookup"><span data-stu-id="635ce-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="635ce-137">O posicionamento dos botões de espera próximo aos seus efeitos é importante para o conforto.</span><span class="sxs-lookup"><span data-stu-id="635ce-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="635ce-138">Diretrizes e práticas recomendadas para a experiência do usuário</span><span class="sxs-lookup"><span data-stu-id="635ce-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="635ce-139">Tamanhos do alvo</span><span class="sxs-lookup"><span data-stu-id="635ce-139">Target sizes</span></span>
  <span data-ttu-id="635ce-140">Para ser facilmente acessível, os destinos de olhar e de duração de pesquisa precisam ser grandes o suficiente para examinar de maneira confortável e manter um rumo estável no destino pelo tempo prescrito.</span><span class="sxs-lookup"><span data-stu-id="635ce-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="635ce-141">Recomendamos um tamanho mínimo de destino de 2 graus para alcançar a experiência mais confortável.</span><span class="sxs-lookup"><span data-stu-id="635ce-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="635ce-142">Feedback visual</span><span class="sxs-lookup"><span data-stu-id="635ce-142">Visual feedback</span></span>

<span data-ttu-id="635ce-143">Ao usar um preenchimento radial para representar o tempo de espera, comece do centro do botão.</span><span class="sxs-lookup"><span data-stu-id="635ce-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="635ce-144">Uma resposta consistente é menos confusa que diferentes direções em botões diferentes.</span><span class="sxs-lookup"><span data-stu-id="635ce-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="635ce-145">Essa regra não precisa ser seguida para interações direcionais (por exemplo, navegação para cima/para baixo/para a esquerda/para a direita etc.).</span><span class="sxs-lookup"><span data-stu-id="635ce-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="635ce-146">Por exemplo, os Guias do Microsoft Dynamics 365 fazem uma exceção a essa regra nos botões AVANÇAR/VOLTAR, que são preenchidos da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="635ce-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="635ce-147">Considere a possibilidade de inverter o preenchimento radial, de fora para dentro, em cenários que exigem a ativação/desativação de um botão de alternância, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="635ce-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="635ce-148">A sensação inversa de apertar um botão é um padrão visual adequado para manter.</span><span class="sxs-lookup"><span data-stu-id="635ce-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="635ce-149">Divulgação progressiva</span><span class="sxs-lookup"><span data-stu-id="635ce-149">Progressive disclosure</span></span>

<span data-ttu-id="635ce-150">A divulgação progressiva significa mostrar apenas a quantidade de detalhes relevante em cada estágio de uma interação.</span><span class="sxs-lookup"><span data-stu-id="635ce-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="635ce-151">Para a espera, isso significa que o alvo é revelado no realce (por exemplo, em um controle de lista).</span><span class="sxs-lookup"><span data-stu-id="635ce-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="635ce-152">Alvos muito grandes</span><span class="sxs-lookup"><span data-stu-id="635ce-152">Oversized targets</span></span>
<span data-ttu-id="635ce-153">A região de espera pode ser maior do que o ícone inativo para facilitar o uso, como o botão Voltar nos Guias do Microsoft Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="635ce-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="635ce-154">Evite a cintilação usando retornos atrasados</span><span class="sxs-lookup"><span data-stu-id="635ce-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="635ce-155">Aplique um pequeno atraso antes de iniciar o retorno visual para evitar cintilação ao passar sobre um alvo de espera.</span><span class="sxs-lookup"><span data-stu-id="635ce-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="635ce-156">Para botões interagir com frequência, mantenha o atraso muito curto para que o aplicativo se sinta reativo.</span><span class="sxs-lookup"><span data-stu-id="635ce-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="635ce-157">Para botões que são interagindo com pouca frequência, um atraso mais longo pode ser apropriado para evitar que a interface se sinta twitchy.</span><span class="sxs-lookup"><span data-stu-id="635ce-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="635ce-158">Padrões da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="635ce-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="635ce-159">Botões de alta frequência</span><span class="sxs-lookup"><span data-stu-id="635ce-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="635ce-160">Botões de alta frequência são botões que são usados normalmente em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="635ce-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="635ce-161">Um bom exemplo são os botões Voltar e Avançar nos Guias do Microsoft Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="635ce-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="635ce-162">**Recommendations**</span><span class="sxs-lookup"><span data-stu-id="635ce-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="635ce-163">Botões de alta frequência devem ser grandes, mais fáceis de atingir com Head-olhar</span><span class="sxs-lookup"><span data-stu-id="635ce-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="635ce-164">Fique à altura dos olhos para evitar sobrecarregar o ergonômicos.</span><span class="sxs-lookup"><span data-stu-id="635ce-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="635ce-165">*Imagem: botão Avançar dos guias do Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="635ce-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Botão Avançar dos guias do Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="635ce-167">Botões de baixa frequência</span><span class="sxs-lookup"><span data-stu-id="635ce-167">Low frequency buttons</span></span>
<span data-ttu-id="635ce-168">Botões de baixa frequência são botões que não são regularmente usados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="635ce-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="635ce-169">Um bom exemplo é um botão para acessar o menu de configurações ou um botão para limpar toda a tarefa.</span><span class="sxs-lookup"><span data-stu-id="635ce-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="635ce-170">Tente manter esses botões longe dos caminhos de ações frequentes de focar com a cabeça para evitar ativação acidental.</span><span class="sxs-lookup"><span data-stu-id="635ce-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="635ce-171">Confirmações</span><span class="sxs-lookup"><span data-stu-id="635ce-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="635ce-172">Quando uma ação tem um impacto significativo, como cobrar dinheiro, excluir uma tarefa ou iniciar um processo longo, é útil confirmar se a pessoa teve a intenção de selecionar o botão.</span><span class="sxs-lookup"><span data-stu-id="635ce-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="635ce-173">**Recommendations**</span><span class="sxs-lookup"><span data-stu-id="635ce-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="635ce-174">Mostre o realce de seleção no botão principal.</span><span class="sxs-lookup"><span data-stu-id="635ce-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="635ce-175">Revele o alvo da espera ao mesmo tempo que o realce da seleção.</span><span class="sxs-lookup"><span data-stu-id="635ce-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="635ce-176">Para o botão secundário, revele o alvo da espera ao focar com a cabeça.</span><span class="sxs-lookup"><span data-stu-id="635ce-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="635ce-177">*Imagem: caixa de diálogo de confirmação de guias do Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="635ce-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Caixa de diálogo de confirmação dos guias do Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="635ce-179">Botões de alternância</span><span class="sxs-lookup"><span data-stu-id="635ce-179">Toggle buttons</span></span>
<span data-ttu-id="635ce-180">Botões de alternância exigem uma lógica sutil para funcionarem corretamente.</span><span class="sxs-lookup"><span data-stu-id="635ce-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="635ce-181">Quando uma pessoa olha fixo para um botão de alternância e o ativa, ela precisa sair do botão e retornar para reiniciar a lógica de espera.</span><span class="sxs-lookup"><span data-stu-id="635ce-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="635ce-182">É importante que os botões de alternância tenham estados ativo e inativo claros.</span><span class="sxs-lookup"><span data-stu-id="635ce-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="635ce-183">Modos de exibição de lista</span><span class="sxs-lookup"><span data-stu-id="635ce-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="635ce-184">As exibições de lista apresentam um desafio específico para a entrada de olhar e de duração da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="635ce-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="635ce-185">As pessoas devem poder verificar o conteúdo sem sentirem que precisam tomar cuidado com os alvos de espera.</span><span class="sxs-lookup"><span data-stu-id="635ce-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="635ce-186">**Recommendations**</span><span class="sxs-lookup"><span data-stu-id="635ce-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="635ce-187">Tenha toda a linha realçada quando Head-gazed, mas não inicia a pesquisa, a menos que Head-olhar esteja no destino de duração específico.</span><span class="sxs-lookup"><span data-stu-id="635ce-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="635ce-188">Mostrar somente o destino de duração de pesquisa quando a linha for realçada para reduzir o ruído visual.</span><span class="sxs-lookup"><span data-stu-id="635ce-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="635ce-189">Fique claro e consistente com a posição dos destinos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="635ce-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="635ce-190">Não mostre todos os destinos de pesquisa de uma só vez para evitar a interface do usuário repetitiva.</span><span class="sxs-lookup"><span data-stu-id="635ce-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="635ce-191">Reutilize o mesmo padrão o mais comum possível para estabelecer a familiaridade de UX.</span><span class="sxs-lookup"><span data-stu-id="635ce-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="635ce-192">*Imagem: lista de guias do Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="635ce-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Lista de guias do Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="635ce-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="635ce-194">See also</span></span>
* [<span data-ttu-id="635ce-195">Olhar e confirmar</span><span class="sxs-lookup"><span data-stu-id="635ce-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="635ce-196">Manipulação de mãos direta</span><span class="sxs-lookup"><span data-stu-id="635ce-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="635ce-197">Gestos práticos</span><span class="sxs-lookup"><span data-stu-id="635ce-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="635ce-198">Ponto de mãos e confirmação</span><span class="sxs-lookup"><span data-stu-id="635ce-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="635ce-199">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="635ce-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="635ce-200">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="635ce-200">Voice input</span></span>](voice-input.md)

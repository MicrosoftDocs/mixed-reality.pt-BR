---
title: Olhar e duração
description: Visão geral do modelo de entrada olhar e duração
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Misto realidade, olhar, duração, interação, de design
ms.openlocfilehash: a50ae948a351f5152ebb98778da9be8c08090d72
ms.sourcegitcommit: 222cba2d622b47f75949bf8af80d5c62de4dceab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64914616"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="5312f-104">Olhar e duração</span><span class="sxs-lookup"><span data-stu-id="5312f-104">Gaze and dwell</span></span>

<span data-ttu-id="5312f-105">Quando prático está ocupados com partes e as ferramentas, gestos podem ser entediante ou impossível.</span><span class="sxs-lookup"><span data-stu-id="5312f-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="5312f-106">Os comandos de voz, como o gesto, podem ser circunstancialmente não confiáveis, por exemplo, sob condições excessivamente altos.</span><span class="sxs-lookup"><span data-stu-id="5312f-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="5312f-107">Além disso, o uso de voz para controlar computadores não é ainda uma interação de base, mas certamente está ganhando steam!</span><span class="sxs-lookup"><span data-stu-id="5312f-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="5312f-108">Duração de olhar oferece o mecanismo mais familiar e fácil em mestre para heads-up de trabalho viva-voz em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5312f-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="5312f-109">Além disso, a duração de olhar é 100% confiável independentes de restrições de interferência nem de silêncio de ruído no ambiente operacional.</span><span class="sxs-lookup"><span data-stu-id="5312f-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="5312f-110">Metas</span><span class="sxs-lookup"><span data-stu-id="5312f-110">Goals</span></span>

<span data-ttu-id="5312f-111">Fornece um mecanismo para interações assistido completo, sem o uso de voz.</span><span class="sxs-lookup"><span data-stu-id="5312f-111">Provide a mechanism for full hands-free interactions, without using Voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="5312f-112">Princípios de design</span><span class="sxs-lookup"><span data-stu-id="5312f-112">Design principles</span></span>

1. <span data-ttu-id="5312f-113">Olhar não é uma arma</span><span class="sxs-lookup"><span data-stu-id="5312f-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="5312f-114">Olhar requer comentários visuais para interação intuitiva, mas muitos comentários podem induzir a ansiedade.</span><span class="sxs-lookup"><span data-stu-id="5312f-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="5312f-115">Os comentários devem ajudar um usuário sabe o que eles está visando, mas não-seleção automática em relação a sua intenção.</span><span class="sxs-lookup"><span data-stu-id="5312f-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="5312f-116">Lendo texto requer uma consideração extra para fornecer um espaço de usuário para absorver as informações antes de selecionar.</span><span class="sxs-lookup"><span data-stu-id="5312f-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="5312f-117">Busca de velocidade Cachinhos Dourados</span><span class="sxs-lookup"><span data-stu-id="5312f-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="5312f-118">O preenchimento de duração de exibição pode ter temporizadores diferentes com base no impacto do painel de navegação - funções usadas com mais frequência geralmente se beneficiará tempos mais rápidos de preenchimento, enquanto as funções mais CONSEQUENCIAIS podem se beneficiar de tempos de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="5312f-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="5312f-119">Curvas de animação da cor de preenchimento positivamente podem influenciar uma sensação de tempos mais rápidos de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="5312f-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="5312f-120">Consideração deve ser tomada para habilitar a decisão de usuário do fast/médio/lento preencher substituições de velocidade.</span><span class="sxs-lookup"><span data-stu-id="5312f-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="5312f-121">Digamos que pseudocódigos para efeito de yo-yo</span><span class="sxs-lookup"><span data-stu-id="5312f-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="5312f-122">O efeito de yo-yo (também conhecido como "noite em the Roxbury") é um padrão de desagradáveis que pode surgir de determinados posicionamento de conteúdo e controles com base em olhar.</span><span class="sxs-lookup"><span data-stu-id="5312f-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="5312f-123">Por exemplo, uma barra de navegação da lista com o botão de preenchimento na parte inferior induz um loop do - aparência para baixo lidam bem com, examine os resultados, examine a duração, etc. Esse padrão resultante é desconfortável e deve ser evitado, colocando os controles de navegação em um local centralizado que exige menos back bidirecional.</span><span class="sxs-lookup"><span data-stu-id="5312f-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="5312f-124">Posicionamento dos botões de duração em relação a seus efeitos se torna importante de conforto.</span><span class="sxs-lookup"><span data-stu-id="5312f-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="5312f-125">Padrões de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5312f-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="5312f-126">Botões de alta frequência</span><span class="sxs-lookup"><span data-stu-id="5312f-126">High frequency buttons</span></span>
    
* <span data-ttu-id="5312f-127">Botões Avançar/voltar</span><span class="sxs-lookup"><span data-stu-id="5312f-127">Next/Back buttons</span></span>
  * <span data-ttu-id="5312f-128">Pré-preenchimento de atraso muito curto (buffer de cintilação popups)</span><span class="sxs-lookup"><span data-stu-id="5312f-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="5312f-129">Botões maiores são mais fáceis de atingir com olhar</span><span class="sxs-lookup"><span data-stu-id="5312f-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="5312f-130">BOM para mantê-los na altura de olho para que não haja pressão para interagir</span><span class="sxs-lookup"><span data-stu-id="5312f-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="5312f-131">Região de duração pode ser maior que o ícone de inativo para torná-lo mais fácil de usar (VERSO)</span><span class="sxs-lookup"><span data-stu-id="5312f-131">Dwell region can be larger than inactive icon to make it easier to use (BACK)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="5312f-132">Botões de baixa frequência</span><span class="sxs-lookup"><span data-stu-id="5312f-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="5312f-133">Ativar o menu Configurações</span><span class="sxs-lookup"><span data-stu-id="5312f-133">Activate settings menu</span></span>
  * <span data-ttu-id="5312f-134">Atrasar mais pré-preenchimento okey (buffer de cintilação popups)</span><span class="sxs-lookup"><span data-stu-id="5312f-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="5312f-135">Tente manter esses botões fora caminhos frequente de cursor</span><span class="sxs-lookup"><span data-stu-id="5312f-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="5312f-136">Confirmações (ou seja, verificação de fluxo, caixas de diálogo)</span><span class="sxs-lookup"><span data-stu-id="5312f-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="5312f-137">Mostrar Realce de seleção no botão principal</span><span class="sxs-lookup"><span data-stu-id="5312f-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="5312f-138">Revelar lidam bem com destino ao mesmo tempo que o realce de seleção</span><span class="sxs-lookup"><span data-stu-id="5312f-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="5312f-139">Use lidam bem com destino ao redor de ícone para manter a interface simples</span><span class="sxs-lookup"><span data-stu-id="5312f-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="5312f-140">Decisão importante, portanto, não ativa o realce, revela a duração de destino para o tempo de uma reconsideração</span><span class="sxs-lookup"><span data-stu-id="5312f-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="5312f-141">Botões de alternância</span><span class="sxs-lookup"><span data-stu-id="5312f-141">Toggle buttons</span></span>

* <span data-ttu-id="5312f-142">Pin</span><span class="sxs-lookup"><span data-stu-id="5312f-142">Pin</span></span>
  * <span data-ttu-id="5312f-143">Estado visual clara ativo/inativo</span><span class="sxs-lookup"><span data-stu-id="5312f-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="5312f-144">Preenchimento radial ajuda o usuário de foco e fornece o andamento natural</span><span class="sxs-lookup"><span data-stu-id="5312f-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="5312f-145">Configurações individuais</span><span class="sxs-lookup"><span data-stu-id="5312f-145">Individual settings</span></span>
  * <span data-ttu-id="5312f-146">Estados claro ativo/inativo</span><span class="sxs-lookup"><span data-stu-id="5312f-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="5312f-147">Lidam bem com destinos todos no ícone adjacente à esquerda</span><span class="sxs-lookup"><span data-stu-id="5312f-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="5312f-148">Duração tem como alvo apenas aparecem quando a seleção de realçar ativo</span><span class="sxs-lookup"><span data-stu-id="5312f-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="5312f-149">"Lidam bem com controle deslizante" no lado direito, para ativar/desativar configurações</span><span class="sxs-lookup"><span data-stu-id="5312f-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="5312f-150">Modos de exibição de lista</span><span class="sxs-lookup"><span data-stu-id="5312f-150">List views</span></span>

* <span data-ttu-id="5312f-151">Exibição de lista de navegação - guia arquivos para abrir</span><span class="sxs-lookup"><span data-stu-id="5312f-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="5312f-152">Destaques do cursor de linha de qualquer lugar na linha, mas não começa a duração</span><span class="sxs-lookup"><span data-stu-id="5312f-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="5312f-153">Quando a linha é realçada pelo cursor, o destino de duração é exibida à esquerda</span><span class="sxs-lookup"><span data-stu-id="5312f-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="5312f-154">Lidam bem com o destino sempre um círculo no lado esquerdo do texto em todos os modos de exibição de lista</span><span class="sxs-lookup"><span data-stu-id="5312f-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="5312f-155">Não mostrar que todos os destinos de uma vez para evitar repetitiva da interface do usuário de duração da pesquisa</span><span class="sxs-lookup"><span data-stu-id="5312f-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="5312f-156">Use novamente o mesmo padrão para estabelecer a familiaridade da experiência do usuário</span><span class="sxs-lookup"><span data-stu-id="5312f-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="5312f-157">Exibição de lista - hierarquia de tarefas/etapas em um guia de navegação</span><span class="sxs-lookup"><span data-stu-id="5312f-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="5312f-158">Lidam bem com o destino sempre um círculo no lado esquerdo do texto</span><span class="sxs-lookup"><span data-stu-id="5312f-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="5312f-159">Expandir/recolher lidam bem com funcionalidade</span><span class="sxs-lookup"><span data-stu-id="5312f-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="5312f-160">Exibição de lista de navegação - Selecione modo</span><span class="sxs-lookup"><span data-stu-id="5312f-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="5312f-161">Siga os padrões estabelecidos acima</span><span class="sxs-lookup"><span data-stu-id="5312f-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="5312f-162">Botões contextuais</span><span class="sxs-lookup"><span data-stu-id="5312f-162">Contextual buttons</span></span>

* <span data-ttu-id="5312f-163">Mostrar/ocultar 3D - mostra-se em 3D ao longo de corda quase hologramas</span><span class="sxs-lookup"><span data-stu-id="5312f-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="5312f-164">Estado visual clara ativo/inativo</span><span class="sxs-lookup"><span data-stu-id="5312f-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="5312f-165">Tabelas dinâmicas</span><span class="sxs-lookup"><span data-stu-id="5312f-165">Pivots</span></span>

* <span data-ttu-id="5312f-166">Lista de guias recentes/All</span><span class="sxs-lookup"><span data-stu-id="5312f-166">Recent/All guides list</span></span>
  * <span data-ttu-id="5312f-167">Preencher a funcionalidade da interface do usuário que permanece para indicar qual guia está ativo</span><span class="sxs-lookup"><span data-stu-id="5312f-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="5312f-168">Para tabelas dinâmicas de única palavra curta, podemos optou por antecipar o padrão de duração de destino</span><span class="sxs-lookup"><span data-stu-id="5312f-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="5312f-169">Podemos favorecida a interface simplificada em relação a outro destinos de círculo 2 e uma interface do usuário mais ampla</span><span class="sxs-lookup"><span data-stu-id="5312f-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="5312f-170">Em nosso caso, as palavras são curtas o suficiente para que um atraso fornece suficiente conforto antes de preenchimento</span><span class="sxs-lookup"><span data-stu-id="5312f-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="5312f-171">Práticas recomendadas e diretrizes de experiência do usuário</span><span class="sxs-lookup"><span data-stu-id="5312f-171">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="5312f-172">Tamanhos do alvo</span><span class="sxs-lookup"><span data-stu-id="5312f-172">Target sizes</span></span>

  * <span data-ttu-id="5312f-173">Tamanho mínimo do PIN ícone: 6cm no espaço de mundo no Unity, 30 MRUs (30cm @ 2m)</span><span class="sxs-lookup"><span data-stu-id="5312f-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="5312f-174">Ficam em todos os destinos "magnetizados" ou "adesivo"?</span><span class="sxs-lookup"><span data-stu-id="5312f-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="5312f-175">(ou seja, olhares suavização de cursor)</span><span class="sxs-lookup"><span data-stu-id="5312f-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="5312f-176">Animação</span><span class="sxs-lookup"><span data-stu-id="5312f-176">Animation</span></span>

  * <span data-ttu-id="5312f-177">Atraso antes de duração visual dispara .5sec</span><span class="sxs-lookup"><span data-stu-id="5312f-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="5312f-178">Duração de duração visual 1,2 s</span><span class="sxs-lookup"><span data-stu-id="5312f-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="5312f-179">Curva na animação?</span><span class="sxs-lookup"><span data-stu-id="5312f-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="5312f-180">Feedback visual</span><span class="sxs-lookup"><span data-stu-id="5312f-180">Visual feedback</span></span>

  * <span data-ttu-id="5312f-181">Preenchimento radial do local de início do cursor olhar</span><span class="sxs-lookup"><span data-stu-id="5312f-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="5312f-182">Preenchimento sempre radial do centro do botão.</span><span class="sxs-lookup"><span data-stu-id="5312f-182">Always radial fill from center of button.</span></span> <span data-ttu-id="5312f-183">Uma resposta consistente é menos confusa que todas as direções diferentes nos botões diferentes.</span><span class="sxs-lookup"><span data-stu-id="5312f-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="5312f-184">Essa regra pode ser interrompida para interações direcionais (por exemplo, etc. para cima/baixo/esquerda/direita, nav.).</span><span class="sxs-lookup"><span data-stu-id="5312f-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="5312f-185">Por exemplo, faz uma exceção em Avançar/voltar sendo deixado com guias com o botão direito preenchimentos.</span><span class="sxs-lookup"><span data-stu-id="5312f-185">For example, Guides makes an exception on NEXT/BACK being left right fills.</span></span>
    * <span data-ttu-id="5312f-186">Considere a possibilidade de inversão de preenchimento radial de fora (se a alternância desativada).</span><span class="sxs-lookup"><span data-stu-id="5312f-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="5312f-187">A inversa sensação de apertar um botão é um bom padrão visual para manter.</span><span class="sxs-lookup"><span data-stu-id="5312f-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="5312f-188">Divulgação progressiva</span><span class="sxs-lookup"><span data-stu-id="5312f-188">Progressive Disclosure</span></span>

 * <span data-ttu-id="5312f-189">Divulgação progressiva significa que o destino de duração é revelado no realce (por exemplo, em um controle de lista)</span><span class="sxs-lookup"><span data-stu-id="5312f-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="5312f-190">Destaques da barra de texto com o spotlight revelam em olhar em qualquer lugar no texto</span><span class="sxs-lookup"><span data-stu-id="5312f-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="5312f-191">Destino de preenchimento de olhar sempre aparece à esquerda, mas apenas para o item de lista que é realçado</span><span class="sxs-lookup"><span data-stu-id="5312f-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="5312f-192">Evite ter todos os destinos de duração de todo o tempo devido a aparência repetitiva de círculos empilhadas</span><span class="sxs-lookup"><span data-stu-id="5312f-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="5312f-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5312f-193">See also</span></span>
* [<span data-ttu-id="5312f-194">Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="5312f-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5312f-195">Ponto e confirmar</span><span class="sxs-lookup"><span data-stu-id="5312f-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="5312f-196">Conceitos básicos de interação</span><span class="sxs-lookup"><span data-stu-id="5312f-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="5312f-197">Olhar head e confirmar</span><span class="sxs-lookup"><span data-stu-id="5312f-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5312f-198">Olhar e voz</span><span class="sxs-lookup"><span data-stu-id="5312f-198">Gaze and voice</span></span>](voice-design.md)

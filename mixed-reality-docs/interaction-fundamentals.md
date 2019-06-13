---
title: Visão geral de interação multimodal
description: Visão geral de interação multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design, hololens, MMR, multimodal
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516018"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="9cedb-104">Apresentação de interações instintivas</span><span class="sxs-lookup"><span data-stu-id="9cedb-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="9cedb-105">A filosofia de interações simples e instintivas está presente em toda a plataforma de Realidade Misturada da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9cedb-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="9cedb-106">Temos três etapas para garantir que os desenvolvedores e designers de aplicativos possam fornecer interações fáceis e intuitivas para seus clientes.</span><span class="sxs-lookup"><span data-stu-id="9cedb-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="9cedb-107">Primeiro, nos asseguramos que nossos incríveis sensores e tecnologia de entrada, incluindo o acompanhamento da mão, de olho e linguagem natural se combinassem em modelos descomplicados de interação multimodal.</span><span class="sxs-lookup"><span data-stu-id="9cedb-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="9cedb-108">Com base em nossa pesquisa, projetar e desenvolver de forma multimodal, e não com base em entradas únicas, é a chave para criar experiências instintivas.</span><span class="sxs-lookup"><span data-stu-id="9cedb-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="9cedb-109">Em segundo lugar, reconhecemos que muitos desenvolvedores têm vários dispositivos como alvo, sejam HoloLens 2 e HoloLens (1ª geração) ou HoloLens e VR.</span><span class="sxs-lookup"><span data-stu-id="9cedb-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="9cedb-110">Portanto, criamos nossos modelos de interação para que funcionem em vários dispositivos (mesmo que a tecnologia de entrada varie em cada dispositivo).</span><span class="sxs-lookup"><span data-stu-id="9cedb-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="9cedb-111">Por exemplo, interação distante em um fone de ouvido de imersão do Windows com um controlador 6DOF e interação distante em um HoloLens 2 usam as capacidades e os padrões idênticos, facilitando para os aplicativos que funcionam em vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="9cedb-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="9cedb-112">Isso não só é conveniente para desenvolvedores e designers, mas também parece natural para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="9cedb-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="9cedb-113">Por fim, ainda que reconheçamos que há milhares de interações eficazes, envolventes e mágicas possíveis no MR, descobrimos que empregar intencionalmente um único modelo de interação de ponta a ponta em um aplicativo é a melhor maneira de garantir que os usuários sejam bem-sucedidos e tenha uma ótima experiência.</span><span class="sxs-lookup"><span data-stu-id="9cedb-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="9cedb-114">Para isso, incluímos três coisas neste guia de interação:</span><span class="sxs-lookup"><span data-stu-id="9cedb-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="9cedb-115">Estruturamos este guia de acordo com os três principais modelos de interação e os componentes e os padrões necessários para cada um</span><span class="sxs-lookup"><span data-stu-id="9cedb-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="9cedb-116">Incluímos orientação complementar sobre os outros benefícios fornecidos por nossa plataforma</span><span class="sxs-lookup"><span data-stu-id="9cedb-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="9cedb-117">Incluímos orientação para ajudar a selecionar o modelo de interação apropriado para seu cenário</span><span class="sxs-lookup"><span data-stu-id="9cedb-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="9cedb-118">Modelos de interação multimodal</span><span class="sxs-lookup"><span data-stu-id="9cedb-118">Multimodal interaction models</span></span>

<span data-ttu-id="9cedb-119">Com base na pesquisa e no trabalho com os clientes até o momento, descobrimos que três modelos de interação principais atendem à maioria das experiências de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="9cedb-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="9cedb-120">Em muitos aspectos, o modelo de interação é o modelo mental do usuário para concluir seus fluxos.</span><span class="sxs-lookup"><span data-stu-id="9cedb-120">In many ways, the interaction model is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="9cedb-121">Cada um desses modelos de interação é otimizado para um conjunto de necessidades do cliente e cada um é conveniente, potente e pode ser usado sozinho.</span><span class="sxs-lookup"><span data-stu-id="9cedb-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="9cedb-122">O gráfico abaixo é uma visão geral simplificada.</span><span class="sxs-lookup"><span data-stu-id="9cedb-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="9cedb-123">Há links para informações detalhadas de uso de cada modelo de interação nas páginas abaixo com imagens e exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="9cedb-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9cedb-124"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="9cedb-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="9cedb-125"><strong>Cenários de exemplo</strong></span><span class="sxs-lookup"><span data-stu-id="9cedb-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="9cedb-126"><strong>Ajustar</strong></span><span class="sxs-lookup"><span data-stu-id="9cedb-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="9cedb-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="9cedb-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9cedb-128"><a href="hands-and-tools.md">Controladores de movimentos e mãos</a></span><span class="sxs-lookup"><span data-stu-id="9cedb-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="9cedb-129">Experiências 3D espaciais, por exemplo, design e layout espacial, manipulação de conteúdo ou simulação.</span><span class="sxs-lookup"><span data-stu-id="9cedb-129">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="9cedb-130">Excelente para novos usuários, juntamente com voz, acompanhamento ocular ou movimento de cabeça.</span><span class="sxs-lookup"><span data-stu-id="9cedb-130">Great for new users, coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="9cedb-131">Baixa curva de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="9cedb-131">Low learning curve.</span></span> <span data-ttu-id="9cedb-132">Experiência do usuário consistente com acompanhamento da mão e 6 controladores DoF.</span><span class="sxs-lookup"><span data-stu-id="9cedb-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span></td>
        <td><span data-ttu-id="9cedb-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9cedb-133">HoloLens 2</span></span><br><span data-ttu-id="9cedb-134">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="9cedb-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9cedb-135"><a href="hands-free.md">Mãos livres</a></span><span class="sxs-lookup"><span data-stu-id="9cedb-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="9cedb-136">Experiências contextuais, nas quais as mãos de um usuário estão ocupadas, por exemplo, no aprendizado no trabalho, na manutenção.</span><span class="sxs-lookup"><span data-stu-id="9cedb-136">Contextual experiences where a user's hands are occupied, e.g. on-the-job learning, maintenance.</span></span></td>
        <td><span data-ttu-id="9cedb-137">Algum aprendizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="9cedb-137">Some learning required.</span></span> <span data-ttu-id="9cedb-138">Caso as mãos não estejam disponíveis, emparelha bem com voz e linguagem natural.</span><span class="sxs-lookup"><span data-stu-id="9cedb-138">If hands are unavailable pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="9cedb-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9cedb-139">HoloLens 2</span></span><br><span data-ttu-id="9cedb-140">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="9cedb-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="9cedb-141">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="9cedb-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9cedb-142"><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></span><span class="sxs-lookup"><span data-stu-id="9cedb-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="9cedb-143">Clique pelas experiências, p.ex., apresentações e demonstrações 3D.</span><span class="sxs-lookup"><span data-stu-id="9cedb-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="9cedb-144">Requer treinamento em HMDs, mas não em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="9cedb-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="9cedb-145">Melhor para controladores acessíveis.</span><span class="sxs-lookup"><span data-stu-id="9cedb-145">Best for accessible controllers.</span></span> <span data-ttu-id="9cedb-146">Melhor para HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="9cedb-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="9cedb-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9cedb-147">HoloLens 2</span></span><br><span data-ttu-id="9cedb-148">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="9cedb-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="9cedb-149">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="9cedb-149">Immersive headsets</span></span><br><span data-ttu-id="9cedb-150">AR móvel</span><span class="sxs-lookup"><span data-stu-id="9cedb-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="9cedb-151">A melhor maneira de garantir que não existem lacunas ou problemas na interação de sua experiência é seguir as diretrizes para um único modelo do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="9cedb-151">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="9cedb-152">Para acelerar o desenvolvimento e o design, incluímos informações detalhadas e links para exemplos de código e imagens em nossa cobertura de cada modelo.</span><span class="sxs-lookup"><span data-stu-id="9cedb-152">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="9cedb-153">Mas primeiro, as seções a seguir seguem as etapas de seleção e implementação de um desses modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="9cedb-153">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="9cedb-154">No final desta página, você entenderá nossas diretrizes em:</span><span class="sxs-lookup"><span data-stu-id="9cedb-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="9cedb-155">Escolhendo um modelo de interação para seu cliente</span><span class="sxs-lookup"><span data-stu-id="9cedb-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="9cedb-156">Usando as diretrizes de modelo de interação</span><span class="sxs-lookup"><span data-stu-id="9cedb-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="9cedb-157">Transição entre os modelos de interação</span><span class="sxs-lookup"><span data-stu-id="9cedb-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="9cedb-158">Próximas etapas de design</span><span class="sxs-lookup"><span data-stu-id="9cedb-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="9cedb-159">Escolha um modelo de interação para seu cliente</span><span class="sxs-lookup"><span data-stu-id="9cedb-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="9cedb-160">Muito provavelmente, os desenvolvedores e os criadores de também já tem algumas ideias em mente dos tipos de experiência de interação que querem que seus usuários tenham.</span><span class="sxs-lookup"><span data-stu-id="9cedb-160">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="9cedb-161">Para incentivar uma abordagem do design voltada para o cliente, é recomendável seguir as diretrizes abaixo para selecionar o modelo de interação que é otimizado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="9cedb-161">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="9cedb-162">Por que seguir esta orientação?</span><span class="sxs-lookup"><span data-stu-id="9cedb-162">Why follow this guidance?</span></span>

* <span data-ttu-id="9cedb-163">Nossos modelos de interação são testados com critérios objetivos e subjetivos, como esforço físico e cognitivo, intuitividade e capacidade de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="9cedb-163">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="9cedb-164">Como a interação é diferente, as capacidades de áudio e vídeo e o comportamento de objeto também podem ser diferentes entre os modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="9cedb-164">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="9cedb-165">Combinar partes de vários modelos de interação, cria o risco de capacidades conflitantes, como raios de mão simultâneos e um cursor de foco com a cabeça que pode sobrecarregar e confundir os usuários.</span><span class="sxs-lookup"><span data-stu-id="9cedb-165">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which can overwhelm and confuse users.</span></span>

<span data-ttu-id="9cedb-166">Aqui estão alguns exemplos de como as capacidades e os comportamentos são otimizados para cada modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="9cedb-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="9cedb-167">Vemos com frequência que novos usuários têm perguntas semelhantes, como "como faço para saber se o sistema está funcionando, como saber o que posso fazer e como saber se entendi o que acabei de fazer?"</span><span class="sxs-lookup"><span data-stu-id="9cedb-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9cedb-168"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="9cedb-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="9cedb-169"><strong>Como saber se está funcionando?</strong></span><span class="sxs-lookup"><span data-stu-id="9cedb-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="9cedb-170"><strong>Como saber o que posso fazer?</strong></span><span class="sxs-lookup"><span data-stu-id="9cedb-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="9cedb-171"><strong>Como saber o que eu acabei de fazer?</strong></span><span class="sxs-lookup"><span data-stu-id="9cedb-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9cedb-172"><a href="hands-and-tools.md">Controladores de movimentos e mãos</a></span><span class="sxs-lookup"><span data-stu-id="9cedb-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="9cedb-173">Vejo uma malha de mão, vejo uma funcionalidade de ponta do dedo ou raios de controlador/mão.</span><span class="sxs-lookup"><span data-stu-id="9cedb-173">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="9cedb-174">Vejo uma caixa delimitadora ou alças que aparecem quando a minha mão está próxima.</span><span class="sxs-lookup"><span data-stu-id="9cedb-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="9cedb-175">Posso ouvir sons e ver animações ao capturar e soltar.</span><span class="sxs-lookup"><span data-stu-id="9cedb-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9cedb-176"><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></span><span class="sxs-lookup"><span data-stu-id="9cedb-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="9cedb-177">Eu vejo um cursor no centro do meu campo de visão.</span><span class="sxs-lookup"><span data-stu-id="9cedb-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="9cedb-178">O cursor do foco com a cabeça muda de estado quando está sobre determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="9cedb-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="9cedb-179">Posso ver/ouvir confirmações visuais e audíveis quando executo uma ação.</span><span class="sxs-lookup"><span data-stu-id="9cedb-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="9cedb-180"><a href="hands-free.md">Mãos livres (foco com a cabeça e permanência)</a></span><span class="sxs-lookup"><span data-stu-id="9cedb-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="9cedb-181">Eu vejo um cursor no centro do meu campo de visão.</span><span class="sxs-lookup"><span data-stu-id="9cedb-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="9cedb-182">Vejo um indicador de progresso quando paro em um objeto com o qual posso interagir.</span><span class="sxs-lookup"><span data-stu-id="9cedb-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="9cedb-183">Posso ver/ouvir confirmações visuais e audíveis quando executo uma ação.</span><span class="sxs-lookup"><span data-stu-id="9cedb-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="9cedb-184"><a href="hands-free.md">Mãos livres (comandos de voz)</a></span><span class="sxs-lookup"><span data-stu-id="9cedb-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="9cedb-185">Vejo um indicador de escuta e legendas que mostram o que o sistema ouviu.</span><span class="sxs-lookup"><span data-stu-id="9cedb-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="9cedb-186">Obtenho prompts de voz e dicas.</span><span class="sxs-lookup"><span data-stu-id="9cedb-186">I get voice prompts and hints.</span></span>  <span data-ttu-id="9cedb-187">Quando digo "o que posso dizer?"</span><span class="sxs-lookup"><span data-stu-id="9cedb-187">When I say "what can I say?"</span></span> <span data-ttu-id="9cedb-188">Vejo feedback.</span><span class="sxs-lookup"><span data-stu-id="9cedb-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="9cedb-189">Vejo/ouço confirmações visuais e auditivas quando emito um comando ou obtenho uma experiência de usuário de desambiguidade quando necessário.</span><span class="sxs-lookup"><span data-stu-id="9cedb-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="9cedb-190">Veja as perguntas que descobrimos ajudar as equipes e selecionar um modelo de interação:</span><span class="sxs-lookup"><span data-stu-id="9cedb-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="9cedb-191">P:  Meus usuários desejam tocar em hologramas e executar manipulações holográficas de precisão?</span><span class="sxs-lookup"><span data-stu-id="9cedb-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="9cedb-192">R:  Nesse caso, confira o modelo de interação de mãos e ferramentas para direcionamento de precisão e a manipulação com as mãos ou com controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="9cedb-192">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="9cedb-193">P:  Meus usuários precisam manter as mãos livres para tarefas do mundo real?</span><span class="sxs-lookup"><span data-stu-id="9cedb-193">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="9cedb-194">R:  Nesse caso, examine o modelo de interação mãos livres, que fornece uma ótima experiência de mãos livres por meio de interações de movimento e voz.</span><span class="sxs-lookup"><span data-stu-id="9cedb-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="9cedb-195">P:  Meus usuários têm tempo para aprender as interações de meu aplicativo de realidade misturada ou precisam das interações com a curva de aprendizado mais baixa possível?</span><span class="sxs-lookup"><span data-stu-id="9cedb-195">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="9cedb-196">R:  Recomendamos o modelo de mãos e ferramentas para a mais baixa curva de aprendizado e interações mais intuitivas, desde que os usuários sejam capazes de usar as mãos para interagir.</span><span class="sxs-lookup"><span data-stu-id="9cedb-196">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="9cedb-197">P:  Meus usuários usam controladores de movimento para apontar e manipular?</span><span class="sxs-lookup"><span data-stu-id="9cedb-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="9cedb-198">R:  O modelo de mãos e de ferramentas inclui todas as diretrizes para uma ótima experiência com os controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="9cedb-198">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="9cedb-199">P:  Meus usuários usam um controlador de acessibilidade ou um controlador de Bluetooth comum, como um clicker?</span><span class="sxs-lookup"><span data-stu-id="9cedb-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="9cedb-200">R:  Recomendamos o modelo de foco com a cabeça e de confirmação para todos os controles não acompanhados.</span><span class="sxs-lookup"><span data-stu-id="9cedb-200">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="9cedb-201">Ele foi projetado para permitir que um usuário passe por uma experiência completa com uma mecânica simples de “direcionar e confirmar".</span><span class="sxs-lookup"><span data-stu-id="9cedb-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="9cedb-202">P: Meus usuários progridem por uma experiência somente "clicando" (por exemplo em um ambiente de apresentação de slides 3D), em vez de navegar por layouts densos de controles de interface de usuário?</span><span class="sxs-lookup"><span data-stu-id="9cedb-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="9cedb-203">R:  Caso os usuários não precisem controlar muita interface de usuário, o foco de cabeça e confirmação oferece uma opção que pode ser aprendida, na qual os usuários não precisam se preocupar com direcionamento.</span><span class="sxs-lookup"><span data-stu-id="9cedb-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="9cedb-204">P:  Meus usuários usam o HoloLens (1ª geração) e HoloLens 2/ Imersivo do Windows (headsets VR)</span><span class="sxs-lookup"><span data-stu-id="9cedb-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="9cedb-205">R:  Como o foco de cabeça e confirmação é o modelo de interação do HoloLens (1ª geração), recomendamos que os criadores que oferecem suporte ao HoloLens (1ª geração) use o foco de cabeça e confirmação para os recursos ou modos que os usuários podem experimentar em um headset HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="9cedb-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="9cedb-206">Consulte a próxima seção abaixo em *Transição de modelos de interação* para obter detalhes sobre como ter uma excelente experiência em várias gerações do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9cedb-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="9cedb-207">P: E quanto aos usuários que normalmente usam dispositivos móveis (que abrangem um grande espaço ou o movimento entre espaços) em relação aos usuários que tendem a trabalhar em um único espaço?</span><span class="sxs-lookup"><span data-stu-id="9cedb-207">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="9cedb-208">R:  Qualquer um dos modelos de interação funcionará para esses usuários.</span><span class="sxs-lookup"><span data-stu-id="9cedb-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="9cedb-209">Mais diretrizes específicas ao design de aplicativo [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="9cedb-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="9cedb-210">Modelos de interação de transição</span><span class="sxs-lookup"><span data-stu-id="9cedb-210">Transition interaction models</span></span>
<span data-ttu-id="9cedb-211">Também há casos em que seus casos de uso podem exigir a utilização de mais de um modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="9cedb-211">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="9cedb-212">Por exemplo, o “fluxo de criação” do aplicativo utiliza o modelo de mãos e controladores de movimento, mas você deseja empregar um modo mãos livres para técnicos de campo.</span><span class="sxs-lookup"><span data-stu-id="9cedb-212">For example, your app's "creation flow" utilizes the Hands and motion controllers interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="9cedb-213">Caso sua experiência precise de vários modelos de interação, descobrimos que muitos usuários finais podem encontrar dificuldade para fazer a transição de um modelo para outro – especialmente os usuários que são novos na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="9cedb-213">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="9cedb-214">Para ajudar a guiar os designers e desenvolvedores por meio de opções que podem ser difíceis na MR, estamos trabalhando em mais orientações para usar vários modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="9cedb-214">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="9cedb-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cedb-215">See also</span></span>
* [<span data-ttu-id="9cedb-216">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="9cedb-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="9cedb-217">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="9cedb-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="9cedb-218">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="9cedb-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9cedb-219">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="9cedb-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="9cedb-220">Gestos</span><span class="sxs-lookup"><span data-stu-id="9cedb-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="9cedb-221">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="9cedb-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="9cedb-222">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="9cedb-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="9cedb-223">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="9cedb-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="9cedb-224">Projeto de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="9cedb-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="9cedb-225">Conforto</span><span class="sxs-lookup"><span data-stu-id="9cedb-225">Comfort</span></span>](comfort.md)


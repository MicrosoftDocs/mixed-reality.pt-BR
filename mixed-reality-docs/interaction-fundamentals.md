---
title: Visão geral de interação multimodal
description: Visão geral da interação multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Misto realidade, olhar, olhar direcionamento, interação, de design
ms.openlocfilehash: f52a0cd8ec53bfe0f4c5da2c054c538eda1c93ca
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993597"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="486b5-104">Introdução ao instinctual interações</span><span class="sxs-lookup"><span data-stu-id="486b5-104">Introducing instinctual interactions</span></span>
<span data-ttu-id="486b5-105">A filosofia de interações simples, instinctual entrelaçada-se em toda a plataforma Microsoft de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="486b5-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="486b5-106">Pegamos três etapas para garantir que os desenvolvedores e designers de aplicativos podem fornecer as interações e intuitivas para seus clientes.</span><span class="sxs-lookup"><span data-stu-id="486b5-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="486b5-107">Primeiro, tornamos-se de que nosso sensores incríveis e a tecnologia de entrada, incluindo o acompanhamento de mão, acompanhamento a olho nu e linguagem natural, combinam em modelos de interação multimodal contínuo.</span><span class="sxs-lookup"><span data-stu-id="486b5-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="486b5-108">Com base em nossa pesquisa, projetar e desenvolver multimodally – e não com base em entradas únicas--é a chave para a criação de experiências instinctual.</span><span class="sxs-lookup"><span data-stu-id="486b5-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="486b5-109">Em segundo lugar, reconhecemos que muitos desenvolvedores direcionar vários dispositivos, se isso significa que 2 HoloLens e HoloLens (1º gen) ou HoloLens e VR.</span><span class="sxs-lookup"><span data-stu-id="486b5-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="486b5-110">Portanto, criamos nossos modelos de interação funcione em todos os dispositivos (mesmo que a tecnologia de entrada varia em cada dispositivo).</span><span class="sxs-lookup"><span data-stu-id="486b5-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="486b5-111">Por exemplo, interação mais distante em um fone de ouvido imersão do Windows com um controlador 6DOF e interação mais distante em um 2 HoloLens os dois usam as capacidades idênticas e os padrões, tornando mais fácil para aplicativos entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="486b5-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="486b5-112">Não é apenas nesse conveniente para desenvolvedores e designers, mas ele parece natural para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="486b5-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="486b5-113">Por fim, reconhecemos que há milhares de eficaz, envolventes, e interações de mágicas possíveis no MR, descobrimos que intencionalmente empregar um modelo de interação única ponta a ponta em um aplicativo é a melhor maneira de garantir que os usuários forem bem-sucedidas e tenha uma ótima experiência.</span><span class="sxs-lookup"><span data-stu-id="486b5-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="486b5-114">Para esse fim, incluímos três coisas neste guia de interação:</span><span class="sxs-lookup"><span data-stu-id="486b5-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="486b5-115">Podemos estruturou essa orientação sobre os três modelos de interação primário e os componentes e os padrões de para cada</span><span class="sxs-lookup"><span data-stu-id="486b5-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="486b5-116">Incluímos orientação complementar sobre os outros benefícios de nossa plataforma fornece</span><span class="sxs-lookup"><span data-stu-id="486b5-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="486b5-117">Incluímos orientação para ajudar a selecionar o modelo de interação apropriado para seu cenário</span><span class="sxs-lookup"><span data-stu-id="486b5-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>


## <a name="three-multimodal-interaction-models"></a><span data-ttu-id="486b5-118">Três modelos de interação multimodal</span><span class="sxs-lookup"><span data-stu-id="486b5-118">Three multimodal interaction models</span></span>
<span data-ttu-id="486b5-119">Com base em nossa pesquisa e trabalho com clientes até o momento, descobrimos que três modelos de interação primário atender a maioria das experiências de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="486b5-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of Mixed Reality experiences.</span></span>

<span data-ttu-id="486b5-120">Em muitos aspectos, o modelo de interação é o modelo mental do usuário para concluir seus fluxos.</span><span class="sxs-lookup"><span data-stu-id="486b5-120">In many ways, the interaction model  is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="486b5-121">Cada um desses modelos de interação é otimizada para um conjunto de necessidades do cliente, e cada um é conveniente, potente e pode ser usada em seus próprios méritos.</span><span class="sxs-lookup"><span data-stu-id="486b5-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="486b5-122">O gráfico abaixo é uma visão geral simplificada.</span><span class="sxs-lookup"><span data-stu-id="486b5-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="486b5-123">Informações detalhadas de uso de cada modelo de interação é vinculadas nas páginas abaixo com imagens e exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="486b5-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span>  

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="486b5-124"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="486b5-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="486b5-125"><strong>Cenários de exemplo</strong></span><span class="sxs-lookup"><span data-stu-id="486b5-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="486b5-126"><strong>ajustar</strong></span><span class="sxs-lookup"><span data-stu-id="486b5-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="486b5-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="486b5-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="486b5-128"><a href="hands-and-tools.md">Mãos e ferramentas</a></span><span class="sxs-lookup"><span data-stu-id="486b5-128"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="486b5-129">Experiências espaciais 3D</span><span class="sxs-lookup"><span data-stu-id="486b5-129">3D spatial experiences</span></span><br><span data-ttu-id="486b5-130">Por exemplo, espacial layout e design, manipulação de conteúdo ou simulação</span><span class="sxs-lookup"><span data-stu-id="486b5-130">e.g. spatial layout and design, content manipulation, or simulation</span></span></td>
        <td><span data-ttu-id="486b5-131">Ótimo para novos usuários</span><span class="sxs-lookup"><span data-stu-id="486b5-131">Great for new users</span></span><br><span data-ttu-id="486b5-132">Baixa curva de aprendizado</span><span class="sxs-lookup"><span data-stu-id="486b5-132">Low learning curve</span></span><br><span data-ttu-id="486b5-133">Com base na fácil capacidades visual</span><span class="sxs-lookup"><span data-stu-id="486b5-133">Grounded in easy visual affordances</span></span><br><span data-ttu-id="486b5-134">Experiência do usuário consistente em mão de acompanhamento e controladores de DoF 6</span><span class="sxs-lookup"><span data-stu-id="486b5-134">Consistent UX across hand tracking and 6 DoF controllers</span></span><br><span data-ttu-id="486b5-135">Olhares excelente quando combinado com voz, de acompanhamento a olho nu ou head</span><span class="sxs-lookup"><span data-stu-id="486b5-135">Great when coupled with voice, eye tracking, or head gaze</span></span></td>
        <td><span data-ttu-id="486b5-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="486b5-136">HoloLens 2</span></span><br><span data-ttu-id="486b5-137">Windows envolventes com controladores 6DOF</span><span class="sxs-lookup"><span data-stu-id="486b5-137">Windows Immersive w/ 6DOF Controllers</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="486b5-138"><a href="hands-free.md">Mãos livres</a></span><span class="sxs-lookup"><span data-stu-id="486b5-138"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="486b5-139">Experiências contextuais, onde as mãos do usuário estiverem ocupadas, por exemplo, sobre o trabalho de aprendizado, manutenção</span><span class="sxs-lookup"><span data-stu-id="486b5-139">Contextual experiences where a user's hands are occupied e.g. on the-job learning, maintenance</span></span></td>
        <td><span data-ttu-id="486b5-140">Alguns de aprendizado necessário</span><span class="sxs-lookup"><span data-stu-id="486b5-140">Some learning required</span></span><br><span data-ttu-id="486b5-141">Se não estiverem disponíveis intervenção</span><span class="sxs-lookup"><span data-stu-id="486b5-141">If hands are unavailable</span></span><br><span data-ttu-id="486b5-142">pares bem com voz e de linguagem natural</span><span class="sxs-lookup"><span data-stu-id="486b5-142">pairs well with voice and natural language</span></span></td>
        <td><span data-ttu-id="486b5-143">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="486b5-143">HoloLens 2</span></span><br><span data-ttu-id="486b5-144">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="486b5-144">HoloLens (1st gen)</span></span><br> <span data-ttu-id="486b5-145">Imersão do Windows</span><span class="sxs-lookup"><span data-stu-id="486b5-145">Windows Immersive</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="486b5-146"><a href="gaze-and-commit.md">Olhar head e confirmar</a></span><span class="sxs-lookup"><span data-stu-id="486b5-146"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="486b5-147">Por exemplo, 3D apresentações, demonstrações experiências de Clickthrough</span><span class="sxs-lookup"><span data-stu-id="486b5-147">Click-through experiences e.g. 3D presentations, demos</span></span></td>
        <td><span data-ttu-id="486b5-148">Requer treinamento em HMDs, mas não em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="486b5-148">Requires training on HMDs but not on mobile</span></span><br><span data-ttu-id="486b5-149">Melhor para controladores acessíveis</span><span class="sxs-lookup"><span data-stu-id="486b5-149">Best for accessible controllers</span></span><br><span data-ttu-id="486b5-150">Melhor para HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="486b5-150">Best for HoloLens (1st gen)</span></span></td>
        <td><span data-ttu-id="486b5-151">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="486b5-151">HoloLens 2</span></span><br><span data-ttu-id="486b5-152">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="486b5-152">HoloLens (1st gen)</span></span><br> <span data-ttu-id="486b5-153">Imersão do Windows</span><span class="sxs-lookup"><span data-stu-id="486b5-153">Windows Immersive</span></span><br> <span data-ttu-id="486b5-154">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="486b5-154">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="486b5-155">A melhor maneira de garantir que não existem lacunas ou buracos na interação para a sua experiência é seguir as diretrizes para um único modelo do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="486b5-155">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="486b5-156">Para acelerar o desenvolvimento e design, incluímos informações detalhadas e links para exemplos de código e imagens dentro de nossa cobertura de cada modelo.</span><span class="sxs-lookup"><span data-stu-id="486b5-156">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="486b5-157">Mas primeiro, as seções a seguir siga as etapas de seleção e implementação de um desses modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="486b5-157">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="486b5-158">No final desta página, você entenderá nossas diretrizes em:</span><span class="sxs-lookup"><span data-stu-id="486b5-158">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="486b5-159">Escolhendo um modelo de interação para seu cliente</span><span class="sxs-lookup"><span data-stu-id="486b5-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="486b5-160">Usando as diretrizes de modelo de interação</span><span class="sxs-lookup"><span data-stu-id="486b5-160">Using the interaction model guidance</span></span>
* <span data-ttu-id="486b5-161">A transição entre os modelos de interação</span><span class="sxs-lookup"><span data-stu-id="486b5-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="486b5-162">Próximas etapas de design</span><span class="sxs-lookup"><span data-stu-id="486b5-162">Design next steps</span></span>

## <a name="choosing-an-interaction-model-for-your-customer"></a><span data-ttu-id="486b5-163">Escolhendo um modelo de interação para seu cliente</span><span class="sxs-lookup"><span data-stu-id="486b5-163">Choosing an interaction model for your customer</span></span>

<span data-ttu-id="486b5-164">Provavelmente, os desenvolvedores e os criadores já tem algumas ideias em mente dos tipos de experiência de interação que desejarem para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="486b5-164">Most likely, developers and creators already have some ideas in mind of the kinds of interaction experience they want for their users.</span></span>
<span data-ttu-id="486b5-165">Para incentivar uma abordagem voltada para projetar, é recomendável seguir as diretrizes abaixo para selecionar o modelo de interação é otimizado para seu cliente.</span><span class="sxs-lookup"><span data-stu-id="486b5-165">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="486b5-166">Por que siga esta orientação?</span><span class="sxs-lookup"><span data-stu-id="486b5-166">Why follow this guidance?</span></span>

* <span data-ttu-id="486b5-167">Nossos modelos de interação são testados para o objetivo e critérios subjetivos como físico e cognitivo esforço, intuitiveness e learnability.</span><span class="sxs-lookup"><span data-stu-id="486b5-167">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="486b5-168">Como interação é diferente, as capacidades de áudio e vídeo e o comportamento de objeto também podem ser diferentes entre os modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="486b5-168">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="486b5-169">Combinar partes de vários modelos de interação, cria o risco de capacidades de concorrentes, como raios de mão simultâneas e um cursor de olhar, que sobrecarregar e confundir os usuários.</span><span class="sxs-lookup"><span data-stu-id="486b5-169">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="486b5-170">Aqui estão alguns exemplos de como as capacidades e comportamentos são otimizados para cada modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="486b5-170">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="486b5-171">Vemos com frequência novos usuários como perguntas semelhantes, como "como faço para saber se o sistema estiver funcionando, como saber o que posso fazer, e como saber se é compreender o que eu acabei de fazer?"</span><span class="sxs-lookup"><span data-stu-id="486b5-171">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="486b5-172"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="486b5-172"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="486b5-173"><strong>Como sabê-lo está funcionando?</strong></span><span class="sxs-lookup"><span data-stu-id="486b5-173"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="486b5-174"><strong>Como saber o que posso fazer?</strong></span><span class="sxs-lookup"><span data-stu-id="486b5-174"><strong>How do I know what can I do?</strong></span></span></td>
        <td><span data-ttu-id="486b5-175"><strong>Como saber o que eu acabei de fazer?</strong></span><span class="sxs-lookup"><span data-stu-id="486b5-175"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="486b5-176"><a href="hands-and-tools.md">Mãos e ferramentas</a></span><span class="sxs-lookup"><span data-stu-id="486b5-176"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="486b5-177">Eu vejo uma mão de malha, vejo uma funcionalidade de ponta do dedo ou mão / controlador raios.</span><span class="sxs-lookup"><span data-stu-id="486b5-177">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="486b5-178">Eu vejo uma caixa delimitadora que aparecem quando a minha mão está próximo ou identificadores grabbable.</span><span class="sxs-lookup"><span data-stu-id="486b5-178">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="486b5-179">Posso ouvir sons e ver animações na captura e versão.</span><span class="sxs-lookup"><span data-stu-id="486b5-179">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="486b5-180"><a href="gaze-and-commit.md">Olhar head e confirmar</a></span><span class="sxs-lookup"><span data-stu-id="486b5-180"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="486b5-181">Eu vejo um cursor no centro do meu campo de visão.</span><span class="sxs-lookup"><span data-stu-id="486b5-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="486b5-182">O cursor de olhar muda de estado quando estiver sobre determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="486b5-182">The gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="486b5-183">Posso ver / ouvir confirmações visuais e audíveis quando eu executar ação.</span><span class="sxs-lookup"><span data-stu-id="486b5-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="486b5-184"><a href="hands-free.md">Viva-voz (olhar e duração)</a></span><span class="sxs-lookup"><span data-stu-id="486b5-184"><a href="hands-free.md">Hands-free (Gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="486b5-185">Eu vejo um cursor no centro do meu campo de visão.</span><span class="sxs-lookup"><span data-stu-id="486b5-185">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="486b5-186">Eu vejo um indicador de progresso quando eu lidam bem com um objeto interagível.</span><span class="sxs-lookup"><span data-stu-id="486b5-186">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="486b5-187">Posso ver / ouvir confirmações visuais e audíveis quando eu executar ação.</span><span class="sxs-lookup"><span data-stu-id="486b5-187">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="486b5-188"><a href="hands-free.md">Viva-voz (comandos de voz)</a></span><span class="sxs-lookup"><span data-stu-id="486b5-188"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="486b5-189">Eu vejo um indicador de escutando e legendas que mostram o que o sistema ouvido.</span><span class="sxs-lookup"><span data-stu-id="486b5-189">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="486b5-190">Posso obter prompts de voz e dicas.</span><span class="sxs-lookup"><span data-stu-id="486b5-190">I get voice prompts and hints.</span></span>  <span data-ttu-id="486b5-191">Quando eu digo "o que posso dizer?"</span><span class="sxs-lookup"><span data-stu-id="486b5-191">When I say "what can I say?"</span></span> <span data-ttu-id="486b5-192">Posso ver comentários.</span><span class="sxs-lookup"><span data-stu-id="486b5-192">I see feedback.</span></span></td>
        <td><span data-ttu-id="486b5-193">Posso ver / ouvir confirmações visuais e audíveis quando emitir um comando, ou obter Desambiguidade UX quando necessário.</span><span class="sxs-lookup"><span data-stu-id="486b5-193">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="486b5-194">Veja as perguntas que descobrimos que as equipes de ajudar a selecionar um modelo de interação a seguir:</span><span class="sxs-lookup"><span data-stu-id="486b5-194">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="486b5-195">P:  Meus usuários deseja tocar hologramas e executar manipulações de holográfica precisão?</span><span class="sxs-lookup"><span data-stu-id="486b5-195">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span>
<span data-ttu-id="486b5-196">R:  Nesse caso, confira o modelo de interação de mãos e ferramentas para direcionamento de precisão e a manipulação com mãos ou controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="486b5-196">A:  If so, check out the Hands and Tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="486b5-197">P:  Meus usuários precisam manter suas mãos livres para tarefas do mundo real?</span><span class="sxs-lookup"><span data-stu-id="486b5-197">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span>
<span data-ttu-id="486b5-198">R:  Nesse caso, examine o modelo de interação viva-voz, que fornece uma ótima experiência viva-voz por meio de interações baseadas em olhar e voz.</span><span class="sxs-lookup"><span data-stu-id="486b5-198">A:  If so, take a look at the Hands-Free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="486b5-199">P:  Meus usuários têm tempo para aprender as interações para meu aplicativo de realidade misturada, ou eles precisam as interações com a curva de aprendizado mais baixa possível?</span><span class="sxs-lookup"><span data-stu-id="486b5-199">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span>
<span data-ttu-id="486b5-200">R:  É recomendável o modelo de mãos e ferramentas para a mais baixa curva de aprendizado e interações mais intuitivas, desde que os usuários são capazes de usar suas mãos para interação.</span><span class="sxs-lookup"><span data-stu-id="486b5-200">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="486b5-201">P:  Fazer meus usuários usar controladores de movimento para a manipulação e apontando?</span><span class="sxs-lookup"><span data-stu-id="486b5-201">Q:  Do my users use motion controllers for pointing and manipulation?</span></span>
<span data-ttu-id="486b5-202">R:  O modelo de mãos e de ferramentas inclui todas as diretrizes para uma ótima experiência com os controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="486b5-202">A:  The Hands and Tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="486b5-203">P:  Fazer meus usuários usar um controlador de acessibilidade ou um controlador de Bluetooth comuns, como um clicker?</span><span class="sxs-lookup"><span data-stu-id="486b5-203">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span>
<span data-ttu-id="486b5-204">R:  Recomendamos que o modelo de olhar Head e confirmação para todos os controladores não controladas.</span><span class="sxs-lookup"><span data-stu-id="486b5-204">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="486b5-205">Ele foi projetado para permitir que um usuário percorrer toda a experiência com um mecânico simple de "destino e confirmação".</span><span class="sxs-lookup"><span data-stu-id="486b5-205">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="486b5-206">P: Meus usuários somente de progresso por meio de uma experiência clicando em"por meio de" (por exemplo, em um apresentação de slides como ambiente 3d), em vez de navegar densos layouts de controles de interface do usuário?</span><span class="sxs-lookup"><span data-stu-id="486b5-206">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span>
<span data-ttu-id="486b5-207">R:  Se os usuários precisam controlar muitas da interface do usuário, o Head olhar e confirmação oferece uma opção de learnable em que os usuários não precisam se preocupar sobre direcionamento.</span><span class="sxs-lookup"><span data-stu-id="486b5-207">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="486b5-208">P:  Fazer meus usuários usar ambos os HoloLens (1º gen) e HoloLens 2 / r Windows imersivo (headsets VR):  Uma vez que o Head olhar e a confirmação é o modelo de interação para HoloLens (1º gen), é recomendável que criadores que oferecem suporte a HoloLens (1º gen) usar olhar Head e de confirmação para quaisquer recursos ou os modos de que os usuários podem enfrentar em um HoloLens (1º gen) fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="486b5-208">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets) A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="486b5-209">Consulte a próxima seção abaixo em *fazendo a transição de modelos de interação* para obter detalhes sobre como tornar uma ótima experiência para várias gerações HoloLens.</span><span class="sxs-lookup"><span data-stu-id="486b5-209">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="486b5-210">P: E quanto para usuários que são geralmente móveis (que abrangem um grande espaço ou movendo entre espaços), em comparação com os usuários que tendem a funcionar em um único espaço?</span><span class="sxs-lookup"><span data-stu-id="486b5-210">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span>  
<span data-ttu-id="486b5-211">R:  Qualquer um dos modelos de interação funcionará para esses usuários.</span><span class="sxs-lookup"><span data-stu-id="486b5-211">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="486b5-212">Mais orientações específicas para o design de aplicativos [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="486b5-212">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="486b5-213">Modelos de interação de transição</span><span class="sxs-lookup"><span data-stu-id="486b5-213">Transition interaction models</span></span>
<span data-ttu-id="486b5-214">Também há casos em que seus casos de uso podem exigir que utiliza mais de um modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="486b5-214">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="486b5-215">Por exemplo, o fluxo do aplicativo"criação" utiliza o modelo de interação de mãos e ferramentas, mas você deseja empregar um modo assistido para técnicos de campo.</span><span class="sxs-lookup"><span data-stu-id="486b5-215">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="486b5-216">Se precisar de sua experiência de vários modelos de interação, descobrimos que muitos usuários finais podem encontrar dificuldade para fazer a transição de um modelo para outro – especialmente os usuários finais não familiarizados com MR.</span><span class="sxs-lookup"><span data-stu-id="486b5-216">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="486b5-217">Para ajudar os designers de guia e desenvolvedores por meio de opções que podem ser difíceis em MR, estamos trabalhando para obter mais diretrizes para usar vários modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="486b5-217">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="486b5-218">Consulte também</span><span class="sxs-lookup"><span data-stu-id="486b5-218">See also</span></span>
* [<span data-ttu-id="486b5-219">Olhar head e confirmar</span><span class="sxs-lookup"><span data-stu-id="486b5-219">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="486b5-220">Manipulação direta</span><span class="sxs-lookup"><span data-stu-id="486b5-220">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="486b5-221">Ponto e confirmar</span><span class="sxs-lookup"><span data-stu-id="486b5-221">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="486b5-222">Focar direcionamento</span><span class="sxs-lookup"><span data-stu-id="486b5-222">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="486b5-223">Gestos</span><span class="sxs-lookup"><span data-stu-id="486b5-223">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="486b5-224">Design de voz</span><span class="sxs-lookup"><span data-stu-id="486b5-224">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="486b5-225">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="486b5-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="486b5-226">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="486b5-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="486b5-227">Projeto de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="486b5-227">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="486b5-228">Conforto</span><span class="sxs-lookup"><span data-stu-id="486b5-228">Comfort</span></span>](comfort.md)

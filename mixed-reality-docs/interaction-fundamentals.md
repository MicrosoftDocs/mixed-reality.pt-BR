---
title: Visão geral de interação multimodal
description: Visão geral de interação multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design, hololens, MMR, multimodal
ms.openlocfilehash: 7b04141c832597be4bb58447629e0ef6e248dc2b
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415253"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="0ff56-104">Apresentação de interações instintivas</span><span class="sxs-lookup"><span data-stu-id="0ff56-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="0ff56-105">A filosofia de interações simples e instintivas está presente em toda a plataforma de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="0ff56-105">The philosophy of simple, instinctual interactions is interwoven throughout the Mixed Reality platform.</span></span>  <span data-ttu-id="0ff56-106">Temos três etapas para os desenvolvedores e designers de aplicativos fornecerem interações fáceis e intuitivas para os clientes deles.</span><span class="sxs-lookup"><span data-stu-id="0ff56-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="0ff56-107">Primeiro, fizemos nossos incríveis sensores e tecnologia de entrada, incluindo o acompanhamento da mão, de olho e de linguagem natural, serem combinados em modelos descomplicados de interação multimodal.</span><span class="sxs-lookup"><span data-stu-id="0ff56-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  <span data-ttu-id="0ff56-108">Com base em nossa pesquisa, projetar e desenvolver em uma estrutura multimodal, em vez de com base em entradas únicas, é o segredo para criar experiências instintivas.</span><span class="sxs-lookup"><span data-stu-id="0ff56-108">Based on our research, designing and developing within a multimodal framework, and not based on single inputs, is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="0ff56-109">Em segundo lugar, reconhecemos que muitos desenvolvedores destinam suas criações a vários dispositivos HoloLens, por exemplo, HoloLens 2 e HoloLens (1ª geração) ou então HoloLens e VR.</span><span class="sxs-lookup"><span data-stu-id="0ff56-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="0ff56-110">Sendo assim, criamos nossos modelos de interação para que funcionem em vários dispositivos (mesmo que a tecnologia de entrada varie em cada dispositivo).</span><span class="sxs-lookup"><span data-stu-id="0ff56-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  <span data-ttu-id="0ff56-111">Por exemplo, interação distante em um headset imersivo do Windows com um controlador 6DoF e interação distante em um HoloLens 2 usam as capacidades e os padrões idênticos, facilitando o desenvolvimento de aplicativos que funcionam entre diferentes dispositivos e proporcionam uma sensação natural para interações do usuário final.</span><span class="sxs-lookup"><span data-stu-id="0ff56-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use  identical affordances and patterns, making it easy for cross-device application development that provides a natural feel to end-user interactions.</span></span> 

<span data-ttu-id="0ff56-112">Ainda que reconheçamos que há milhares de interações eficazes, envolventes e mágicas possíveis na MR (realidade misturada), descobrimos que empregar intencionalmente um único modelo de interação de ponta a ponta em um aplicativo é a melhor maneira de garantir que os usuários sejam bem-sucedidos e tenha uma ótima experiência.</span><span class="sxs-lookup"><span data-stu-id="0ff56-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in mixed reality (MR), we've found that intentionally employing a single interaction model, end-to-end, in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="0ff56-113">Para isso, incluímos três coisas neste guia de interação:</span><span class="sxs-lookup"><span data-stu-id="0ff56-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="0ff56-114">Estruturamos esta diretriz de acordo com os três principais modelos de interação e os componentes e os padrões necessários para cada um.</span><span class="sxs-lookup"><span data-stu-id="0ff56-114">This guidance is structured around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="0ff56-115">Incluímos diretrizes complementares sobre os outros benefícios fornecidos por nossa plataforma.</span><span class="sxs-lookup"><span data-stu-id="0ff56-115">Supplemental guidance has been included about other benefits that our platform provides.</span></span>
* <span data-ttu-id="0ff56-116">Também incluímos diretrizes para ajudar a selecionar o modelo de interação apropriado para seu cenário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0ff56-116">Guidance has also been included to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="0ff56-117">Modelos de interação multimodal</span><span class="sxs-lookup"><span data-stu-id="0ff56-117">Multimodal interaction models</span></span>

<span data-ttu-id="0ff56-118">Com base na pesquisa e nos comentários recebidos dos clientes, descobrimos que três modelos de interação principais atendem à maioria das experiências de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0ff56-118">Based on our research as well as feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="0ff56-119">Em muitos aspectos, o modelo de interação é o modelo mental do usuário para concluir seus fluxos.</span><span class="sxs-lookup"><span data-stu-id="0ff56-119">In many ways, the interaction model is the user's mental model for completing their flows.</span></span> <span data-ttu-id="0ff56-120">Cada um desses modelos de interação é otimizado para um conjunto de necessidades dos clientes.</span><span class="sxs-lookup"><span data-stu-id="0ff56-120">Each of these interaction models is optimized for a set of customer needs.</span></span> <span data-ttu-id="0ff56-121">Cada um deles é prático, poderoso e utilizável por si só.</span><span class="sxs-lookup"><span data-stu-id="0ff56-121">Each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="0ff56-122">O gráfico abaixo é uma visão geral simplificada.</span><span class="sxs-lookup"><span data-stu-id="0ff56-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="0ff56-123">Há links para informações detalhadas de uso de cada modelo de interação nas páginas abaixo com imagens e exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="0ff56-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0ff56-124"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="0ff56-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="0ff56-125"><strong>Cenários de exemplo</strong></span><span class="sxs-lookup"><span data-stu-id="0ff56-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="0ff56-126"><strong>Ajustar</strong></span><span class="sxs-lookup"><span data-stu-id="0ff56-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="0ff56-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="0ff56-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0ff56-128"><a href="hands-and-tools.md">Controladores de movimentos e mãos</a></span><span class="sxs-lookup"><span data-stu-id="0ff56-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="0ff56-129">Experiências 3D espaciais, por exemplo, design e layout espacial, manipulação de conteúdo ou simulação.</span><span class="sxs-lookup"><span data-stu-id="0ff56-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="0ff56-130">Excelente para novos usuários, juntamente com voz, acompanhamento ocular ou foco com a cabeça.</span><span class="sxs-lookup"><span data-stu-id="0ff56-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="0ff56-131">Baixa curva de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="0ff56-131">Low learning curve.</span></span> <span data-ttu-id="0ff56-132">Experiência do usuário consistente com acompanhamento da mão e controladores 6DoF.</span><span class="sxs-lookup"><span data-stu-id="0ff56-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="0ff56-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0ff56-133">HoloLens 2</span></span><br><span data-ttu-id="0ff56-134">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="0ff56-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0ff56-135"><a href="hands-free.md">Mãos livres</a></span><span class="sxs-lookup"><span data-stu-id="0ff56-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="0ff56-136">Experiências contextuais, nas quais as mãos de um usuário estão ocupadas, por exemplo, no aprendizado no trabalho e na manutenção.</span><span class="sxs-lookup"><span data-stu-id="0ff56-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning, and maintenance.</span></span></td>
        <td><span data-ttu-id="0ff56-137">Algum aprendizado é necessário.</span><span class="sxs-lookup"><span data-stu-id="0ff56-137">Some learning required.</span></span> <span data-ttu-id="0ff56-138">Caso as mãos não estejam disponíveis, o dispositivo emparelha bem com voz e linguagem natural.</span><span class="sxs-lookup"><span data-stu-id="0ff56-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="0ff56-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0ff56-139">HoloLens 2</span></span><br><span data-ttu-id="0ff56-140">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="0ff56-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="0ff56-141">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="0ff56-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0ff56-142"><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></span><span class="sxs-lookup"><span data-stu-id="0ff56-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="0ff56-143">Clique pelas experiências, p.ex., apresentações e demonstrações 3D.</span><span class="sxs-lookup"><span data-stu-id="0ff56-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="0ff56-144">Requer treinamento em HMDs, mas não em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="0ff56-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="0ff56-145">Melhor para controladores acessíveis.</span><span class="sxs-lookup"><span data-stu-id="0ff56-145">Best for accessible controllers.</span></span> <span data-ttu-id="0ff56-146">Melhor para HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="0ff56-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="0ff56-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0ff56-147">HoloLens 2</span></span><br><span data-ttu-id="0ff56-148">HoloLens (1ª geração)</span><span class="sxs-lookup"><span data-stu-id="0ff56-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="0ff56-149">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="0ff56-149">Immersive headsets</span></span><br><span data-ttu-id="0ff56-150">AR móvel</span><span class="sxs-lookup"><span data-stu-id="0ff56-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="0ff56-151">A melhor maneira de garantir que não existem lacunas ou problemas na interação de sua experiência é seguir as orientações para um único modelo, do início ao fim.</span><span class="sxs-lookup"><span data-stu-id="0ff56-151">To ensure that there are no gaps or holes in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="0ff56-152">Para acelerar o desenvolvimento e o design, incluímos informações detalhadas e links para exemplos de código e imagens em nossa cobertura de cada modelo.</span><span class="sxs-lookup"><span data-stu-id="0ff56-152">To speed up design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="0ff56-153">As seções a seguir seguem as etapas de seleção e implementação de um desses modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="0ff56-153">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="0ff56-154">No final desta página, você entenderá nossas diretrizes em:</span><span class="sxs-lookup"><span data-stu-id="0ff56-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="0ff56-155">Escolhendo um modelo de interação para seu cliente</span><span class="sxs-lookup"><span data-stu-id="0ff56-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="0ff56-156">Usando as diretrizes de modelo de interação</span><span class="sxs-lookup"><span data-stu-id="0ff56-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="0ff56-157">Transição entre os modelos de interação</span><span class="sxs-lookup"><span data-stu-id="0ff56-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="0ff56-158">Próximas etapas de design</span><span class="sxs-lookup"><span data-stu-id="0ff56-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="0ff56-159">Escolha um modelo de interação para seu cliente</span><span class="sxs-lookup"><span data-stu-id="0ff56-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="0ff56-160">Na maioria dos casos, os desenvolvedores e criadores pensaram nos tipos de interações que seus clientes podem ter.</span><span class="sxs-lookup"><span data-stu-id="0ff56-160">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="0ff56-161">Para incentivar uma abordagem do design voltada para o cliente, é recomendável seguir as orientações abaixo para selecionar o modelo de interação que é otimizado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="0ff56-161">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="0ff56-162">Por que seguir esta orientação?</span><span class="sxs-lookup"><span data-stu-id="0ff56-162">Why follow this guidance?</span></span>

* <span data-ttu-id="0ff56-163">Nossos modelos de interação são testados com critérios objetivos e subjetivos, tais como esforço físico e cognitivo, intuitividade e capacidade de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="0ff56-163">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="0ff56-164">Como a interação é diferente, as capacidades de áudio e vídeo e o comportamento de objeto podem ser diferentes entre os modelos de interação.</span><span class="sxs-lookup"><span data-stu-id="0ff56-164">Because interactions differ, visual and audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="0ff56-165">Combinar partes de vários modelos de interação cria o risco de capacidades conflitantes, tais como raios de mão simultâneos e um cursor de foco com a cabeça que pode sobrecarregar e confundir os usuários.</span><span class="sxs-lookup"><span data-stu-id="0ff56-165">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor that can overwhelm and confuse users.</span></span>

<span data-ttu-id="0ff56-166">Aqui estão alguns exemplos de como as capacidades e os comportamentos são otimizados para cada modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="0ff56-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="0ff56-167">Vemos com frequência que novos usuários têm perguntas semelhantes, como "como faço para saber se o sistema está funcionando, como saber o que posso fazer e como saber se entendi o que acabei de fazer?"</span><span class="sxs-lookup"><span data-stu-id="0ff56-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0ff56-168"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="0ff56-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="0ff56-169"><strong>Como saber se está funcionando?</strong></span><span class="sxs-lookup"><span data-stu-id="0ff56-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="0ff56-170"><strong>Como saber o que posso fazer?</strong></span><span class="sxs-lookup"><span data-stu-id="0ff56-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="0ff56-171"><strong>Como saber o que eu acabei de fazer?</strong></span><span class="sxs-lookup"><span data-stu-id="0ff56-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0ff56-172"><a href="hands-and-tools.md">Controladores de movimentos e mãos</a></span><span class="sxs-lookup"><span data-stu-id="0ff56-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="0ff56-173">Vejo uma malha de mão, vejo uma funcionalidade de ponta do dedo ou raios de controlador ou de mão.</span><span class="sxs-lookup"><span data-stu-id="0ff56-173">I see a hand mesh, I see a fingertip affordance or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="0ff56-174">Vejo uma caixa delimitadora ou alças que aparecem quando a minha mão está próxima.</span><span class="sxs-lookup"><span data-stu-id="0ff56-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="0ff56-175">Posso ouvir sons e ver animações ao capturar e soltar.</span><span class="sxs-lookup"><span data-stu-id="0ff56-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0ff56-176"><a href="gaze-and-commit.md">Focar com a cabeça e confirmar</a></span><span class="sxs-lookup"><span data-stu-id="0ff56-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="0ff56-177">Eu vejo um cursor no centro do meu campo de visão.</span><span class="sxs-lookup"><span data-stu-id="0ff56-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="0ff56-178">O cursor do foco com a cabeça muda de estado quando está sobre determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="0ff56-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="0ff56-179">Posso ver/ouvir confirmações visuais e audíveis quando executo uma ação.</span><span class="sxs-lookup"><span data-stu-id="0ff56-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="0ff56-180"><a href="hands-free.md">Mãos livres (foco com a cabeça e permanência)</a></span><span class="sxs-lookup"><span data-stu-id="0ff56-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="0ff56-181">Eu vejo um cursor no centro do meu campo de visão.</span><span class="sxs-lookup"><span data-stu-id="0ff56-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="0ff56-182">Vejo um indicador de progresso quando paro em um objeto com o qual posso interagir.</span><span class="sxs-lookup"><span data-stu-id="0ff56-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="0ff56-183">Posso ver/ouvir confirmações visuais e audíveis quando executo uma ação.</span><span class="sxs-lookup"><span data-stu-id="0ff56-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0ff56-184"><a href="hands-free.md">Mãos livres (comandos de voz)</a></span><span class="sxs-lookup"><span data-stu-id="0ff56-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="0ff56-185">Vejo um indicador de escuta e legendas que mostram o que o sistema ouviu.</span><span class="sxs-lookup"><span data-stu-id="0ff56-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="0ff56-186">Obtenho prompts de voz e dicas.</span><span class="sxs-lookup"><span data-stu-id="0ff56-186">I get voice prompts and hints.</span></span> <span data-ttu-id="0ff56-187">Quando digo: "o que posso dizer?"</span><span class="sxs-lookup"><span data-stu-id="0ff56-187">When I say: "what can I say?"</span></span> <span data-ttu-id="0ff56-188">Vejo feedback.</span><span class="sxs-lookup"><span data-stu-id="0ff56-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="0ff56-189">Vejo/ouço confirmações visuais e auditivas quando emito um comando ou obtenho uma experiência de usuário de desambiguidade quando necessário.</span><span class="sxs-lookup"><span data-stu-id="0ff56-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="0ff56-190">Veja as perguntas que descobrimos ajudar as equipes e selecionar um modelo de interação:</span><span class="sxs-lookup"><span data-stu-id="0ff56-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="0ff56-191">P:  Meus usuários desejam tocar em hologramas e executar manipulações holográficas de precisão?</span><span class="sxs-lookup"><span data-stu-id="0ff56-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="0ff56-192">R:  Nesse caso, confira o modelo de interação de mãos e de controladores de movimentos para direcionamento de precisão e a manipulação com as mãos ou com controladores de movimentos.</span><span class="sxs-lookup"><span data-stu-id="0ff56-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="0ff56-193">P:  Meus usuários precisam manter as mãos livres para tarefas do mundo real?</span><span class="sxs-lookup"><span data-stu-id="0ff56-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="0ff56-194">R:  Nesse caso, examine o modelo de interação de mãos livres, que fornece uma ótima experiência de mãos livres por meio de interações de movimento e voz.</span><span class="sxs-lookup"><span data-stu-id="0ff56-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="0ff56-195">P:  Meus usuários têm tempo para aprender as interações de meu aplicativo de realidade misturada ou precisam das interações com a curva de aprendizado mais baixa possível?</span><span class="sxs-lookup"><span data-stu-id="0ff56-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="0ff56-196">R:  Recomendamos o modelo de mãos e de controladores de movimentos para a mais baixa curva de aprendizado e interações mais intuitivas, desde que os usuários sejam capazes de usar as mãos para interagir.</span><span class="sxs-lookup"><span data-stu-id="0ff56-196">A:  We recommend the Hands and motion controllers model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="0ff56-197">P:  Meus usuários usam controladores de movimento para apontar e manipular?</span><span class="sxs-lookup"><span data-stu-id="0ff56-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="0ff56-198">R:  O modelo de mãos e de controladores de movimentos inclui todas as orientações para uma ótima experiência com os controladores de movimentos.</span><span class="sxs-lookup"><span data-stu-id="0ff56-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="0ff56-199">P:  Meus usuários usam um controlador de acessibilidade ou um controlador de Bluetooth comum, como um clicker?</span><span class="sxs-lookup"><span data-stu-id="0ff56-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="0ff56-200">R:  Recomendamos o modelo de foco com a cabeça e de confirmação para todos os controladores não acompanhados.</span><span class="sxs-lookup"><span data-stu-id="0ff56-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="0ff56-201">Ele foi projetado para permitir que um usuário passe por uma experiência completa com um mecanismo simples de "direcionar e confirmar".</span><span class="sxs-lookup"><span data-stu-id="0ff56-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="0ff56-202">P: Meus usuários progridem por uma experiência somente "clicando" (por exemplo em um ambiente de apresentação de slides 3D), em vez de navegar por layouts densos de controles de interface de usuário?</span><span class="sxs-lookup"><span data-stu-id="0ff56-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="0ff56-203">R:  Caso os usuários não precisem controlar muita interface de usuário, o foco de cabeça e confirmação oferece uma opção que pode ser aprendida, na qual os usuários não precisam se preocupar com direcionamento.</span><span class="sxs-lookup"><span data-stu-id="0ff56-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="0ff56-204">P:  Meus usuários usam o HoloLens (1ª geração) e HoloLens 2/headsets imersivos do Windows Mixed Reality (VR)?</span><span class="sxs-lookup"><span data-stu-id="0ff56-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="0ff56-205">R:  Como o foco com a cabeça e confirmação é o modelo de interação do HoloLens (1ª geração), recomendamos que os criadores que dão suporte ao HoloLens (1ª geração) usem o foco com a cabeça e confirmação para os recursos ou modos que os usuários experimentarão em um headset HoloLens (1ª geração).</span><span class="sxs-lookup"><span data-stu-id="0ff56-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="0ff56-206">Consulte a próxima seção abaixo em *Transição de modelos de interação* para obter detalhes sobre como ter uma excelente experiência em várias gerações do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ff56-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="0ff56-207">P: E quanto aos usuários que normalmente usam dispositivos móveis, que abrangem um grande espaço ou o movimento entre espaços, em relação aos usuários que tendem a trabalhar em um único espaço?</span><span class="sxs-lookup"><span data-stu-id="0ff56-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="0ff56-208">R:  Qualquer um dos modelos de interação funcionará para esses usuários.</span><span class="sxs-lookup"><span data-stu-id="0ff56-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="0ff56-209">Mais diretrizes específicas ao design de aplicativo [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="0ff56-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="0ff56-210">Modelos de interação de transição</span><span class="sxs-lookup"><span data-stu-id="0ff56-210">Transitioning interaction models</span></span>
<span data-ttu-id="0ff56-211">Também há casos de uso que podem exigir a utilização de mais de um modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="0ff56-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="0ff56-212">Por exemplo, o fluxo de criação do aplicativo utiliza o modelo de interação de mãos e controladores de movimentos, mas convém empregar um modo de mãos livres para técnicos de campo.</span><span class="sxs-lookup"><span data-stu-id="0ff56-212">For example, your application's creation flow utilizes the Hands and motion controllers interaction model, but you want to employ a hands-free mode for field technicians.</span></span>  

<span data-ttu-id="0ff56-213">Caso sua experiência precise de vários modelos de interação, tenha em mente que muitos usuários finais podem encontrar dificuldade ao fazer a transição de um modelo para outro, especialmente os usuários que são novos na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0ff56-213">If your experience does require multiple interaction models, keep in mind that many end users might encounter difficulty when transitioning from one model to another--especially for users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="0ff56-214">Estamos trabalhando constantemente em mais diretrizes que estarão disponíveis para desenvolvedores e designers, informando-os sobre como, quando e por que usar vários modelos de interação de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0ff56-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="0ff56-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ff56-215">See also</span></span>
* [<span data-ttu-id="0ff56-216">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="0ff56-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0ff56-217">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="0ff56-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="0ff56-218">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="0ff56-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0ff56-219">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="0ff56-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="0ff56-220">Gestos</span><span class="sxs-lookup"><span data-stu-id="0ff56-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="0ff56-221">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="0ff56-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="0ff56-222">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="0ff56-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="0ff56-223">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="0ff56-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="0ff56-224">Projeto de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="0ff56-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="0ff56-225">Conforto</span><span class="sxs-lookup"><span data-stu-id="0ff56-225">Comfort</span></span>](comfort.md)


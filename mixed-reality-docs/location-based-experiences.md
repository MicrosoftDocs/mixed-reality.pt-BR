---
title: Entretenimento baseado na localização com realidade do Windows Mixed
description: Obtenha acesso aos objetos Holographic nativos subjacentes no Unity.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: realidade misturada, VR, LBE, local
ms.openlocfilehash: e23d17ff2b07c636c98a9f19a5dd20f4dc558bf7
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69983394"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="a8abd-104">Entretenimento baseado na localização com realidade do Windows Mixed</span><span class="sxs-lookup"><span data-stu-id="a8abd-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="a8abd-105">Nos últimos anos, testemunhamos uma quantidade incrível de crescimento e inovação na categoria de entretenimento baseada na localização.</span><span class="sxs-lookup"><span data-stu-id="a8abd-105">In the last couple of years, we have witnessed an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="a8abd-106">Os locais tradicionais, como os parques de tema e os teatros, começaram a oferecer experiências de imersão e de vários jogadores como experiências complementares a corridas e instalações existentes.</span><span class="sxs-lookup"><span data-stu-id="a8abd-106">Traditional venues like theme parks and theatres have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="a8abd-107">Novos operadores e locais estão trazendo experiências exclusivas de vários sensorials e vários jogadores a um preço atraente para as massas.</span><span class="sxs-lookup"><span data-stu-id="a8abd-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="a8abd-108">Todas essas experiências estão empurrando o envelope para saber o que é possível com realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a8abd-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="a8abd-109">Este documento é um guia para começar a usar a realidade mista do Windows na categoria entretenimento baseado na localização.</span><span class="sxs-lookup"><span data-stu-id="a8abd-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="a8abd-110">As diretrizes abaixo também podem ser aplicáveis a experiências baseadas em local além de entretenimento, como treinamento, design de produto ou outros casos de uso.</span><span class="sxs-lookup"><span data-stu-id="a8abd-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design or other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="a8abd-111">Perguntas frequentes sobre Engenharia</span><span class="sxs-lookup"><span data-stu-id="a8abd-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="a8abd-112">Hardware</span><span class="sxs-lookup"><span data-stu-id="a8abd-112">Hardware</span></span>

<span data-ttu-id="a8abd-113">**PERGUNTAS Qual hardware está disponível da Microsoft e de seus parceiros que posso usar na minha configuração?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="a8abd-114">R: A Microsoft e seus parceiros OEM oferecem um portfólio atraente de dispositivos para sua escolha, dependendo de suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="a8abd-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="a8abd-115">Se as experiências que você está fornecendo aos seus clientes exigem headsets de realidade virtual, os seguintes headsets no mercado da HP, Samsung e Acer são uma ótima opção.</span><span class="sxs-lookup"><span data-stu-id="a8abd-115">If the experiences you’re providing to your customers require virtual reality headsets, the following in-market headsets from HP, Samsung and Acer are a great fit.</span></span> <span data-ttu-id="a8abd-116">Cada headset tem seus próprios atributos diferenciados.</span><span class="sxs-lookup"><span data-stu-id="a8abd-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="a8abd-117">Mais detalhes sobre cada um deles.</span><span class="sxs-lookup"><span data-stu-id="a8abd-117">More details on each below.</span></span>

<span data-ttu-id="a8abd-118">Reverbo HP: [Detalhes](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="a8abd-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="a8abd-119">Samsung Odyssey +: [Detalhes](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="a8abd-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="a8abd-120">Acer [Detalhes](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="a8abd-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="a8abd-121">Se o seu local for especializado em experiências de realidade mistas ou incrementais que exigem o uso de um headset, você poderá adquirir o Microsoft HoloLens 2 (agora aberto para interesse de ordem anterior).</span><span class="sxs-lookup"><span data-stu-id="a8abd-121">If your location specializes in mixed or augmented reality experiences requiring the use of a see-through headset, you can procure the Microsoft HoloLens 2 (now open for pre-order interest).</span></span>  

<span data-ttu-id="a8abd-122">HoloLens 2: [Interesse de pré-ordem](https://www.microsoft.com/en-us/hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="a8abd-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com/en-us/hololens/buy)</span></span>

<span data-ttu-id="a8abd-123">Se você estiver experimentando experiências que exigem visão avançada da computação, fala e controle de corpo, você pode encontrar o Azure Kinect DK para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="a8abd-123">If you’re experimenting with experiences that require advanced computer vision, speech and body tracking, you may find the Azure Kinect DK a fit for your needs.</span></span>  

<span data-ttu-id="a8abd-124">Kinect do Azure: [Detalhes](https://azure.microsoft.com/en-us/services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="a8abd-124">Azure Kinect: [Details](https://azure.microsoft.com/en-us/services/kinect-dk/)</span></span>

<span data-ttu-id="a8abd-125">**PERGUNTAS Qual é o portfólio de PCs mochila que posso usar para executar minhas experiências de VR no meu PC?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="a8abd-126">Para experiências de VR para PC, nossos OEMs oferecem uma seleção incrível de PCs mochila criados exatamente para essa necessidade.</span><span class="sxs-lookup"><span data-stu-id="a8abd-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="a8abd-127">A HP acabou de lançar seu HP VR mochila G2, o PC de portátil mais poderoso do mundo – otimizado para experiências de mobilidade gratuita, agora com 30% mais energia com uma GPU de RTX 2080 dentro.</span><span class="sxs-lookup"><span data-stu-id="a8abd-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="a8abd-128">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a8abd-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="a8abd-129">Configuração</span><span class="sxs-lookup"><span data-stu-id="a8abd-129">Setup</span></span>

<span data-ttu-id="a8abd-130">**PERGUNTAS Como posso configurar com mais facilidade a instalação e personalizar o portal de realidade misturada para o LBE?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="a8abd-131">Este recurso requer a versão 2000.19061.1011.0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="a8abd-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="a8abd-132">Você pode achar que precisa de mais personalização do portal de realidade misturada do que normalmente está disponível por meio do aplicativo para implantar aplicativos em quiosques ou experiências personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a8abd-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="a8abd-133">A atualização mais recente de julho do portal de realidade misturada dá suporte a várias configurações avançadas que podem ser por meio de um arquivo de configuração para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a8abd-133">The latest July update of Mixed Reality Portal supports several advanced settings that can be via a configuration file to do the following:</span></span>  

<span data-ttu-id="a8abd-134">Permitir verificações do sistema com falha – normalmente, o processo de instalação verifica a compatibilidade do computador com o Windows Mixed Reality antes de concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="a8abd-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="a8abd-135">Ignorar isso pode causar problemas ao tentar executar a realidade mista do Windows se houver problemas de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="a8abd-135">Bypassing this may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="a8abd-136">Ignorar aplicativo complementar do dispositivo – o DCA fornece etapas de configuração específicas do headset fornecidas pelo fabricante e permite a atualização do firmware do headset.</span><span class="sxs-lookup"><span data-stu-id="a8abd-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="a8abd-137">Ignorar a configuração da sala – em vez de ser solicitado a criar um limite de sala, você pode prosseguir diretamente para o headset no modo encaixado/em pé.</span><span class="sxs-lookup"><span data-stu-id="a8abd-137">Skip room setup – instead of being prompted to create a room boundary, you can proceed directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="a8abd-138">Ignorar a instalação de aplicativos da loja-a instalação normal instala vários aplicativos da loja, incluindo o visualizador 3D e o complemento do Visualizador do Edge 360.</span><span class="sxs-lookup"><span data-stu-id="a8abd-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="a8abd-139">Isso ignorará a instalação desses aplicativos, mas você poderá estar sem a funcionalidade do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a8abd-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="a8abd-140">Mostrar visualização em tela inteira – o portal de realidade misturada padrão mostrará a visualização do headset em tela inteira no PC desktop enquanto o headset está em uso.</span><span class="sxs-lookup"><span data-stu-id="a8abd-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="a8abd-141">Ocultar novo no painel lateral – isso impede que o novo painel para você seja expandido no lançamento do portal de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a8abd-141">Hide New for you side panel – this prevent the New for you panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="a8abd-142">Como configurar:</span><span class="sxs-lookup"><span data-stu-id="a8abd-142">How to configure:</span></span>  

<span data-ttu-id="a8abd-143">Para definir qualquer uma dessas configurações, você precisa criar um arquivo chamado _userconfig. JSON_ neste diretório: _\\ $env: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState_</span><span class="sxs-lookup"><span data-stu-id="a8abd-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="a8abd-144">Para a maioria dos usuários, isso parecerá _C:\Users\<username\\ > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState_</span><span class="sxs-lookup"><span data-stu-id="a8abd-144">For most users this will look like _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="a8abd-145">O arquivo JSON deve ter o conteúdo abaixo com "true" definido para qualquer uma das configurações acima que você deseja habilitar:</span><span class="sxs-lookup"><span data-stu-id="a8abd-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="a8abd-146">**PERGUNTAS Há alguma orientação sobre como configurar o Playspace?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="a8abd-147">R: A configuração de um Playspace deve ser feita como você faria com uma experiência de configuração do consumidor.</span><span class="sxs-lookup"><span data-stu-id="a8abd-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="a8abd-148">O processo de configuração de sala também permitirá que você defina os limites de sala.</span><span class="sxs-lookup"><span data-stu-id="a8abd-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="a8abd-149">Mais detalhes sobre como configurar os limites de sala podem ser lidos [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span><span class="sxs-lookup"><span data-stu-id="a8abd-149">More details on configuring room boundaries can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="a8abd-150">Conforme discutido no documento acima, a Playspace de coordenadas únicas razoável máxima é cerca de 5mx5m.</span><span class="sxs-lookup"><span data-stu-id="a8abd-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="a8abd-151">Se você quiser ter uma área maior, poderá usar o recurso âncoras espaciais na pilha da API do Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="a8abd-151">If you want to have a larger area you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="a8abd-152">Usar essa API exigirá engenharia personalizada nas experiências que você está produzindo.</span><span class="sxs-lookup"><span data-stu-id="a8abd-152">Using this API will require custom engineering in the experiences you are producing.</span></span>  

<span data-ttu-id="a8abd-153">Mais detalhes sobre como otimizar o conteúdo para diferentes tamanhos de espaço podem ser lidos [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="a8abd-153">More details on how to optimize your content for different space sizes can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="a8abd-154">**PERGUNTAS Meu espaço é muito grande e estou com erros quando tento configurar uma experiência de navegação com limites. O que devo fazer para configurar minha experiência de grande roaming de alta disponibilidade?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to setup my large free-roam experience work?**</span></span>

<span data-ttu-id="a8abd-155">R: Para configurar um espaço maior que ~ 18x18ft, você não poderá usar a experiência de limite fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="a8abd-155">A: To setup a larger space than ~18x18ft you won’t be able to use the boundary experience provided by the system.</span></span>  <span data-ttu-id="a8abd-156">Os sistemas de limite se baseiam no aproveitamento de uma única "âncora" de coordenada fixa, que pode se tornar instável quando um usuário estiver muito longe da âncora do estágio central.</span><span class="sxs-lookup"><span data-stu-id="a8abd-156">The boundary systems relies on leveraging a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="a8abd-157">Em vez disso, você pode configurar o modo "encaixado", que não exibirá o limite ou configurará um limite de estágio ou Playspace.</span><span class="sxs-lookup"><span data-stu-id="a8abd-157">Instead, you can setup “seated” mode, which will not display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="a8abd-158">Em seguida, você precisará configurar várias âncoras espaciais dentro do aplicativo para fazer referência a áreas de limite físicas.</span><span class="sxs-lookup"><span data-stu-id="a8abd-158">Then, you’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="a8abd-159">O desenvolvedor do aplicativo é responsável por exibir as proteções necessárias para que os usuários não colidem com os arredores físicos.</span><span class="sxs-lookup"><span data-stu-id="a8abd-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="a8abd-160">Elas podem ser paredes digitais dentro da experiência ou um Visual personalizado de limite de jogo.</span><span class="sxs-lookup"><span data-stu-id="a8abd-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="a8abd-161">Orientação sobre como configurar o limite de sala com WMR pode ser encontrada [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span><span class="sxs-lookup"><span data-stu-id="a8abd-161">Guidance on setting up the room boundary with WMR can be found [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="a8abd-162">**PERGUNTAS Onde está a origem do Playspace?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="a8abd-163">R: A origem do Playspace é determinada pela experiência de configuração da sala, mais especificamente a posição de HMD quando o botão central é pressionado durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="a8abd-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="a8abd-164">INSTALAÇÃO DE VÁRIOS JOGADORES</span><span class="sxs-lookup"><span data-stu-id="a8abd-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="a8abd-165">**PERGUNTAS Estou implantando uma experiência de vários jogadores no meu local. Isso tem suporte no Windows Mixed Reality?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="a8abd-166">R: A ferramenta de pacote de dados espaciais da realidade misturada é um recurso beta que permite localizar vários players no mesmo espaço, permitindo a portabilidade dos dados espaciais de um PC para outro.</span><span class="sxs-lookup"><span data-stu-id="a8abd-166">A: The Mixed Reality Spatial Data Packager tool is a beta feature that allows localizing multiple players in the same space by enabling porting of the spatial data from one PC to another.</span></span> <span data-ttu-id="a8abd-167">Você pode acessar a ferramenta e saber mais sobre ela [aqui](mixedrealityspatialdatapackager.md).</span><span class="sxs-lookup"><span data-stu-id="a8abd-167">You can access the tool and learn more about it [here](mixedrealityspatialdatapackager.md).</span></span>

### <a name="tracking"></a><span data-ttu-id="a8abd-168">CONTROLE ALTERAÇÕES</span><span class="sxs-lookup"><span data-stu-id="a8abd-168">TRACKING</span></span>

<span data-ttu-id="a8abd-169">P: Como funciona a tecnologia de rastreamento em headsets de realidade mista do Windows?</span><span class="sxs-lookup"><span data-stu-id="a8abd-169">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="a8abd-170">A realidade misturada compartilha a mesma tecnologia de controle que o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a8abd-170">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="a8abd-171">Para saber mais sobre o sistema de acompanhamento interno, confira a documentação [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system).</span><span class="sxs-lookup"><span data-stu-id="a8abd-171">To learn more about the inside-out tracking system, check out the documentation [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="a8abd-172">Para obter uma descrição de como o sistema de mapeamento espacial de nível superior funciona, você pode ler nossa descrição [aqui](spatial-mapping-design.md).</span><span class="sxs-lookup"><span data-stu-id="a8abd-172">For a description of how the higher-level spatial mapping system works you can read our description [here](spatial-mapping-design.md).</span></span>

<span data-ttu-id="a8abd-173">**PERGUNTAS Há alguma prática recomendada para obter um volume de controle confiável?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-173">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="a8abd-174">Para configurar melhor o ambiente para acompanhar o sucesso, você pode ler as práticas recomendadas nesta [postagem](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="a8abd-174">To best configure the environment for tracking success, you can read best practices in this [post](environment-considerations-for-hololens.md).</span></span>

<span data-ttu-id="a8abd-175">**PERGUNTAS Há alguma nuance específica com acompanhamento em espaços de escala de depósito ou otimizações a serem consideradas?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-175">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="a8abd-176">R: As práticas a seguir podem ajudar com a obtenção de um volume de controle mais confiável:</span><span class="sxs-lookup"><span data-stu-id="a8abd-176">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="a8abd-177">Fornecer uma variedade de recursos na sala que se sobrepõem a várias posições ajudará o sistema de controle a obter um bloqueio sólido.</span><span class="sxs-lookup"><span data-stu-id="a8abd-177">Providing a variety of features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="a8abd-178">Imagine a interlinhagem de pintura aleatória e a hachura, em vez de usar linhas de estilo de delimitação sólida.</span><span class="sxs-lookup"><span data-stu-id="a8abd-178">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="a8abd-179">Minimize o intervalo dinâmico de iluminação em sua área sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="a8abd-179">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="a8abd-180">As câmeras de rastreamento em nossa realidade misturada HMDs não são HDR e têm AGC (lucro automático) e o AEC (exposição automática) em ordem para lidar com iluminaçãos diferentes.</span><span class="sxs-lookup"><span data-stu-id="a8abd-180">The tracking cameras on our Mixed Reality HMDs are not HDR and have AGC (auto gain) and AEC (auto exposure) going in order to deal with different lighting.</span></span> <span data-ttu-id="a8abd-181">Dependendo da distribuição da luz da superfície, os padrões e o contraste, AGC ou AEC podem concluir que você está em um quarto de branco ou preto que pode desbotar seus recursos que podem estar na "cor" oposta.</span><span class="sxs-lookup"><span data-stu-id="a8abd-181">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a pretty much all white or black room which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="a8abd-182">Se você estiver tentando pegar uma imagem interior na frente de uma janela exterior com um plano de fundo brilhante e ajustar a exposição para que possa ver os detalhes fora, tudo no interior será doexposto e preto.</span><span class="sxs-lookup"><span data-stu-id="a8abd-182">If you are trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="a8abd-183">Ou, se definido para dentro, tudo o que está fora agora estará superexposto e todos os brancos.</span><span class="sxs-lookup"><span data-stu-id="a8abd-183">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="a8abd-184">Destaques em uma sala (até mesmo sobrecarga) que estão na exibição se as câmeras de acompanhamento às vezes podem ser culpadas, o que confundi o AEC/AGC das câmeras de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="a8abd-184">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="a8abd-185">A iluminação plana/difusa ajuda.</span><span class="sxs-lookup"><span data-stu-id="a8abd-185">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="a8abd-186">SERVIÇOS DE NUVEM DE REALIDADE MISTURADA E AZURE</span><span class="sxs-lookup"><span data-stu-id="a8abd-186">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="a8abd-187">**PERGUNTAS Como Microsoft Azure pode ajudar minha escala comercial?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-187">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="a8abd-188">R: O gerenciamento remoto e local com base no Azure podem ajudar sua empresa a ser controlado por dados, reduzir os custos operacionais e dimensionar a implantação em locais novos e existentes.</span><span class="sxs-lookup"><span data-stu-id="a8abd-188">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="a8abd-189">Os serviços de nuvem do Azure, como o armazenamento do Azure, Azure Functions, serviço de aplicativo, rede do Azure e Hub IOT podem ajudar com os seguintes casos de uso:</span><span class="sxs-lookup"><span data-stu-id="a8abd-189">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="a8abd-190">Gerenciamento de & de implantação de dispositivo remoto</span><span class="sxs-lookup"><span data-stu-id="a8abd-190">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="a8abd-191">Análise no local em tempo real</span><span class="sxs-lookup"><span data-stu-id="a8abd-191">Real Time Onsite Analytics</span></span> 

<span data-ttu-id="a8abd-192">LBE cheia de adaptação inteligente</span><span class="sxs-lookup"><span data-stu-id="a8abd-192">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="a8abd-193">Streaming e implantação de conteúdo do LBE</span><span class="sxs-lookup"><span data-stu-id="a8abd-193">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="a8abd-194">Calor de preferência do LBE Player</span><span class="sxs-lookup"><span data-stu-id="a8abd-194">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="a8abd-195">LBE reserva e sistema de reservas</span><span class="sxs-lookup"><span data-stu-id="a8abd-195">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="a8abd-196">**PERGUNTAS Estou desenvolvendo um MMOG espacial para implantar em grande quantidade de espaço. Todos os serviços que me ajudam a gerenciar meu conteúdo e minha persistência de objetos?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-196">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="a8abd-197">R: As âncoras espaciais do Azure são um novo serviço de realidade misturada que permite experiências de realidade mista de vários usuários, com reconhecimento espacial, em dispositivos de HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="a8abd-197">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS and Android devices.</span></span> <span data-ttu-id="a8abd-198">Você pode aprender mais sobre as âncoras espaciais do Azure [aqui](https://azure.microsoft.com/en-us/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="a8abd-198">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com/en-us/services/spatial-anchors/).</span></span>

<span data-ttu-id="a8abd-199">**PERGUNTAS. Nosso local é especialista em experiências de vários jogadores e gostaria de concentrar nosso tempo de desenvolvimento em conteúdo e desenvolvimento de front-end. Há ofertas que podem me ajudar a inicializar ou descarregar o desenvolvimento de back-end?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-199">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="a8abd-200">R: O Azure PlayFab é uma plataforma de back-end completa para jogos ao vivo.</span><span class="sxs-lookup"><span data-stu-id="a8abd-200">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="a8abd-201">Você pode aprender mais sobre isso [aqui](https://playfab.com/).</span><span class="sxs-lookup"><span data-stu-id="a8abd-201">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="a8abd-202">Diversos</span><span class="sxs-lookup"><span data-stu-id="a8abd-202">Misc</span></span>

<span data-ttu-id="a8abd-203">**PERGUNTAS Eu uso o SteamVR para implantar minhas experiências. A realidade mista do Windows funciona com o SteamVR?**</span><span class="sxs-lookup"><span data-stu-id="a8abd-203">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="a8abd-204">R: O Windows Mixed Reality for SteamVR permite que os usuários executem experiências de SteamVR em headsets de imersão de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8abd-204">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="a8abd-205">Saiba mais sobre SteamVR com WMR [aqui](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="a8abd-205">Learn more about SteamVR with WMR [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="a8abd-206">Suporte e comunidade</span><span class="sxs-lookup"><span data-stu-id="a8abd-206">Support and community</span></span>  

<span data-ttu-id="a8abd-207">Abaixo estão alguns recursos úteis para envolver especialistas em nossa equipe, obter suporte para solução de problemas e contribuir para a comunidade de desenvolvimento de realidade misturada mais ampla.</span><span class="sxs-lookup"><span data-stu-id="a8abd-207">Below are a few helpful resources to engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="a8abd-208">Se você tiver problemas com recursos lançados publicamente, registre um bug usando o Hub de comentários. para obter diretrizes, consulte esta [página](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback).</span><span class="sxs-lookup"><span data-stu-id="a8abd-208">If you run into issues with any publicly released features, please file a bug using Feedback Hub.For guidance, please refer to this [page](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="a8abd-209">Para obter ajuda adicional sobre solução de problemas com o WMR, entre em contato com nossa equipe de suporte ao cliente ao arquivar uma [solicitação de suporte](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).</span><span class="sxs-lookup"><span data-stu-id="a8abd-209">For additional troubleshooting help with WMR please get in touch with our customer support team by filing a [support request](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).</span></span>

<span data-ttu-id="a8abd-210">Junte-se ao nosso canal de margem de atraso HoloDevelopers para envolver os desenvolvedores que trabalham em realidade misturada e especialistas no assunto da equipe: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="a8abd-210">Join our HoloDevelopers Slack channel to engage with the developers working on mixed reality and subject matter experts from the team: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="a8abd-211">Twitter Siga nossa equipe de relações de desenvolvedor da realidade misturada para notícias, eventos e atualizações@MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="a8abd-211">Twitter: Follow our Mixed Reality Developer Relations team for news, events and updates @MxdRealityDev</span></span> 

<span data-ttu-id="a8abd-212">Se você estiver em ou em volta de San Francisco, sempre haverá algo acontecendo no reator da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a8abd-212">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="a8abd-213">Você pode ver nosso calendário de eventos [aqui](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco).</span><span class="sxs-lookup"><span data-stu-id="a8abd-213">You can see our calendar of events [here](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco).</span></span>
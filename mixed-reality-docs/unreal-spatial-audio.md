---
title: Áudio espacial no Unreal
description: Visão geral do plug-in de áudio espacial do Unreal Engine.
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446782"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="78f6e-104">Áudio espacial no Unreal</span><span class="sxs-lookup"><span data-stu-id="78f6e-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="78f6e-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="78f6e-105">Overview</span></span>

<span data-ttu-id="78f6e-106">Ao contrário da visão, os seres humanos ouvem o som ao redor em 360 graus.</span><span class="sxs-lookup"><span data-stu-id="78f6e-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="78f6e-107">O som espacial emula o modo como a audição humana funciona, fornecendo as indicações necessárias para identificar localizações de som no espaço do mundo.</span><span class="sxs-lookup"><span data-stu-id="78f6e-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="78f6e-108">Ao adicionar som espacial aos seus aplicativos de realidade misturada, você está aprimorando o nível de imersão experimentado pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="78f6e-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="78f6e-109">O processamento de som espacial de alta qualidade é complexo e, portanto, o HoloLens 2 é fornecido com um hardware dedicado para processar esses objetos de som.</span><span class="sxs-lookup"><span data-stu-id="78f6e-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="78f6e-110">Para acessar esse suporte de processamento de hardware, instale o plug-in **MicrosoftSpatialSound** no seu projeto do Unreal.</span><span class="sxs-lookup"><span data-stu-id="78f6e-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="78f6e-111">Este artigo descreverá a instalação e a configuração desse plug-in e indicará recursos mais aprofundados para o uso de som espacial no Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="78f6e-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span> 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="78f6e-112">Como instalar o plug-in do Microsoft Spatial Sound</span><span class="sxs-lookup"><span data-stu-id="78f6e-112">Installing the Microsoft Spatial Sound plugin</span></span> 

<span data-ttu-id="78f6e-113">A primeira etapa para adicionar som espacial ao seu projeto é instalar o plug-in do Microsoft Spatial Sound, que pode ser encontrado com as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="78f6e-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span> 

1. <span data-ttu-id="78f6e-114">Clicando em **Editar > Plug-ins** e procurando **MicrosoftSpatialSound** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="78f6e-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span> 
2. <span data-ttu-id="78f6e-115">Marcando a caixa de seleção **Habilitado** no plug-in **MicrosoftSpatialSound**.</span><span class="sxs-lookup"><span data-stu-id="78f6e-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span> 
3. <span data-ttu-id="78f6e-116">Reiniciando o editor do Unreal selecionando **Reiniciar Agora** na página de plug-ins.</span><span class="sxs-lookup"><span data-stu-id="78f6e-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span> 

> [!NOTE]
> <span data-ttu-id="78f6e-117">Se ainda não tiver feito isso, você precisará instalar os plug-ins do **Microsoft Windows Mixed Reality** e do **HoloLens** seguindo as instruções da seção **[Como inicializar seu projeto](unreal-uxt-ch2.md)** da nossa série de tutoriais do Unreal.</span><span class="sxs-lookup"><span data-stu-id="78f6e-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Plug-in de áudio espacial do Unreal](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="78f6e-119">Depois que o editor for reiniciado, o projeto estará pronto.</span><span class="sxs-lookup"><span data-stu-id="78f6e-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="78f6e-120">Como configurar o plug-in de espacialização para a plataforma HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="78f6e-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="78f6e-121">A configuração do plug-in de espacialização é feita de acordo com a plataforma.</span><span class="sxs-lookup"><span data-stu-id="78f6e-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="78f6e-122">Habilite o plug-in do Microsoft Spatial Sound para o HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="78f6e-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="78f6e-123">Selecionando **Editar > Configurações do Projeto**, rolando a página até **Plataformas** e clicando em **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="78f6e-123">Selecting **Edit > Project Settings**, scrolling to **Platforms** and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="78f6e-124">Expandindo as propriedades de **Áudio** e definindo o campo **Plug-in de Espacialização** como **Microsoft Spatial Sound**.</span><span class="sxs-lookup"><span data-stu-id="78f6e-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![Plug-in de espacialização para a plataforma HoloLens](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="78f6e-126">Se você pretende visualizar seu aplicativo no editor do Unreal em um computador desktop, repita as etapas acima para a plataforma **Windows**:</span><span class="sxs-lookup"><span data-stu-id="78f6e-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Plug-in de espacialização para a plataforma Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="78f6e-128">Como habilitar o áudio espacial na sua estação de trabalho</span><span class="sxs-lookup"><span data-stu-id="78f6e-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="78f6e-129">O áudio espacial está desabilitado por padrão nas versões de área de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="78f6e-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="78f6e-130">Habilite-o:</span><span class="sxs-lookup"><span data-stu-id="78f6e-130">You can enable it by:</span></span>
* <span data-ttu-id="78f6e-131">Clicando com o botão direito do mouse no ícone de **volume** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="78f6e-131">Right-clicking on the **volume** icon in the task bar.</span></span> 
    + <span data-ttu-id="78f6e-132">Escolha **Som espacial -> Windows Sonic para Fones de Ouvido** para obter a melhor representação do que você ouvirá no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="78f6e-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![Plug-in de espacialização](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="78f6e-134">Essa configuração só é necessária se você planeja testar seu projeto no editor do Unreal.</span><span class="sxs-lookup"><span data-stu-id="78f6e-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="78f6e-135">Como criar objetos de Atenuação</span><span class="sxs-lookup"><span data-stu-id="78f6e-135">Creating Attenuation objects</span></span>
<span data-ttu-id="78f6e-136">Depois de instalar e configurar os plug-ins necessários:</span><span class="sxs-lookup"><span data-stu-id="78f6e-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="78f6e-137">Procure um ator de **Som Ambiente** na janela **Posicionar Atores** e arraste-o para a janela **Cena**.</span><span class="sxs-lookup"><span data-stu-id="78f6e-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![Como adicionar o ator de som ambiente](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="78f6e-139">Torne o ator de **Som Ambiente** um filho de um elemento visual na cena.</span><span class="sxs-lookup"><span data-stu-id="78f6e-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span> 
    * <span data-ttu-id="78f6e-140">Um ator de Som Ambiente não tem nenhuma representação visual por padrão; portanto, você só ouvirá um som da posição dele na cena.</span><span class="sxs-lookup"><span data-stu-id="78f6e-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="78f6e-141">A anexação dele a um elemento visual permite que você veja e mova o ator como qualquer outro ativo.</span><span class="sxs-lookup"><span data-stu-id="78f6e-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="78f6e-142">Clique com o botão direito do mouse no **Navegador de Conteúdo** e selecione **Criar Ativo Avançado -> Sons -> Atenuação de Som**:</span><span class="sxs-lookup"><span data-stu-id="78f6e-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![Como criar um ativo de atenuação de som](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="78f6e-144">Clique com o botão direito do mouse no ativo de **Atenuação de Som** na janela **Navegador de Conteúdo** e selecione a opção **Editar** para abrir a janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="78f6e-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="78f6e-145">Alterne o **Método de Espacialização** para **Binaural**.</span><span class="sxs-lookup"><span data-stu-id="78f6e-145">Switch the **Spatialization Method** to **Binaural**.</span></span>

![Definir o método de espacialização](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="78f6e-147">Selecione o ator de **Som Ambiente** e role a página para baixo até a seção **Atenuação** no painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="78f6e-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span> 
    * <span data-ttu-id="78f6e-148">Defina a propriedade de **Configurações de Atenuação** como o ativo de **Atenuação de Som** criado.</span><span class="sxs-lookup"><span data-stu-id="78f6e-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![Definir a configuração de atenuação](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="78f6e-150">Defina o **Ativo de Som** que deseja anexar ao ator de Som Ambiente atualizando a propriedade **Som** do ator de Som Ambiente para especificar o arquivo de SoundAsset a ser usado.</span><span class="sxs-lookup"><span data-stu-id="78f6e-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![Definir o ativo de som](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> <span data-ttu-id="78f6e-152">O arquivo de SoundAsset precisa ser mono para ser espacializado com o plug-in do Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="78f6e-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="78f6e-153">Encontre as propriedades do arquivo de som posicionando o cursor sobre o ativo na janela Navegador de Conteúdo, conforme mostrado na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="78f6e-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![Novo ativo de atenuação de som](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="78f6e-155">Quando tudo isso estiver configurado, o som ambiente poderá ser espacializado por meio do suporte de descarregamento de hardware dedicado no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="78f6e-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="78f6e-156">Como configurar objetos para espacialização</span><span class="sxs-lookup"><span data-stu-id="78f6e-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="78f6e-157">Trabalhar com áudio espacial significa que você é responsável pelo gerenciamento de como o som se comporta em um ambiente virtual.</span><span class="sxs-lookup"><span data-stu-id="78f6e-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="78f6e-158">Seu foco principal é a criação de objetos de som que parecem soar mais alto quando o usuário está próximo e mais baixo quando o usuário está distante.</span><span class="sxs-lookup"><span data-stu-id="78f6e-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="78f6e-159">Isso é conhecido como atenuação de som, fazendo com que os sons pareçam como se estivessem posicionados em uma localização fixa.</span><span class="sxs-lookup"><span data-stu-id="78f6e-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="78f6e-160">Todos os objetos de atenuação são fornecidos com as configurações modificáveis de:</span><span class="sxs-lookup"><span data-stu-id="78f6e-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="78f6e-161">Distância</span><span class="sxs-lookup"><span data-stu-id="78f6e-161">Distance</span></span>
* <span data-ttu-id="78f6e-162">Espacialização</span><span class="sxs-lookup"><span data-stu-id="78f6e-162">Spatialization</span></span>
* <span data-ttu-id="78f6e-163">Absorção de ar</span><span class="sxs-lookup"><span data-stu-id="78f6e-163">Air Absorption</span></span>
* <span data-ttu-id="78f6e-164">Foco do ouvinte</span><span class="sxs-lookup"><span data-stu-id="78f6e-164">Listener Focus</span></span>
* <span data-ttu-id="78f6e-165">Envio de reverberação</span><span class="sxs-lookup"><span data-stu-id="78f6e-165">Reverb Send</span></span>
* <span data-ttu-id="78f6e-166">Oclusão</span><span class="sxs-lookup"><span data-stu-id="78f6e-166">Occlusion</span></span>

<span data-ttu-id="78f6e-167">O artigo [Atenuação de som no Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) traz detalhes e especificações de implementação sobre cada um desses tópicos.</span><span class="sxs-lookup"><span data-stu-id="78f6e-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>


## <a name="see-also"></a><span data-ttu-id="78f6e-168">Veja também</span><span class="sxs-lookup"><span data-stu-id="78f6e-168">See also</span></span>
* [<span data-ttu-id="78f6e-169">Som espacial</span><span class="sxs-lookup"><span data-stu-id="78f6e-169">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="78f6e-170">Design de som espacial</span><span class="sxs-lookup"><span data-stu-id="78f6e-170">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="78f6e-171">MR Espacial 220: som espacial</span><span class="sxs-lookup"><span data-stu-id="78f6e-171">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)
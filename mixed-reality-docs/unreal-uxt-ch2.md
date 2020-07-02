---
title: 2. Inicializar o projeto e seu primeiro aplicativo
description: Parte 2 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 150fee721bb9cd72d287737aca4262bd87dccba8
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345726"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="3144e-104">2. Inicializar o projeto e seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="3144e-104">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="3144e-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3144e-105">Overview</span></span>

<span data-ttu-id="3144e-106">Neste primeiro tutorial, você começará com um novo aplicativo do Unreal para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3144e-106">In this first tutorial, you'll get started with a new Unreal application for HoloLens 2.</span></span> <span data-ttu-id="3144e-107">Isso incluirá adicionar o plug-in do HoloLens, criar e iluminar um nível e populá-lo com um jogo de tabuleiro e uma peça de xadrez.</span><span class="sxs-lookup"><span data-stu-id="3144e-107">This is going to include adding the HoloLens plugin, creating and lighting a level, and populating it with a game board and chess piece.</span></span> <span data-ttu-id="3144e-108">Você usará ativos pré-criados para a peça de xadrez 3D e materiais de objeto, então não será necessário fazer a modelagem de nada do zero.</span><span class="sxs-lookup"><span data-stu-id="3144e-108">You'll be using pre-made assets for the 3D chess piece and object materials, so don't worry about modeling anything from scratch.</span></span> <span data-ttu-id="3144e-109">No final deste tutorial, você terá uma tela em branco que está pronta para a realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3144e-109">By the end of this tutorial you'll have a blank canvas that's ready for mixed reality.</span></span>

<span data-ttu-id="3144e-110">Antes de continuar, verifique se você atende a todos os pré-requisitos da página [Introdução](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="3144e-110">Before continuing, make sure you have all the prerequisites from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="3144e-111">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3144e-111">Objectives</span></span>
* <span data-ttu-id="3144e-112">Como configurar um projeto do Unreal para desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="3144e-112">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="3144e-113">Como importar ativos e configurar um cenário</span><span class="sxs-lookup"><span data-stu-id="3144e-113">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="3144e-114">Como criar Atores e eventos em nível de script com blueprints</span><span class="sxs-lookup"><span data-stu-id="3144e-114">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="3144e-115">Como criar um projeto do Unreal</span><span class="sxs-lookup"><span data-stu-id="3144e-115">Creating a new Unreal project</span></span>
<span data-ttu-id="3144e-116">A primeira coisa que você precisa é de um projeto com o qual trabalhar.</span><span class="sxs-lookup"><span data-stu-id="3144e-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="3144e-117">Se esta é a primeira vez que você empacota um aplicativo do Unreal para o HoloLens, [baixe os arquivos de suporte](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="3144e-117">If this is your first time creating an Unreal app for HoloLens, you'll need to [download supporting files](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) from the Epic Launcher.</span></span>

1. <span data-ttu-id="3144e-118">Iniciar Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="3144e-118">Launch Unreal Engine</span></span>

2. <span data-ttu-id="3144e-119">Selecione **Jogos** em **Novas Categorias de Projeto** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3144e-119">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Selecionar um modelo de projeto de jogos](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="3144e-121">Selecione o modelo **Em Branco** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3144e-121">Select the **Blank** Template and click **Next**.</span></span> 

![Selecionar o modelo Em Branco](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="3144e-123">Defina **C++** , **3D ou 2D escalonável, Mobile/Tablet** e **Nenhum Conteúdo Inicial** como suas **Configurações de Projeto**.</span><span class="sxs-lookup"><span data-stu-id="3144e-123">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**.</span></span> 
    * <span data-ttu-id="3144e-124">Escolha um local para salvar e clique em **Criar Projeto**.</span><span class="sxs-lookup"><span data-stu-id="3144e-124">Choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="3144e-125">Você precisará selecionar um projeto C++ em vez de um projeto Blueprint para criar o plug-in das Ferramentas de UX, que você vai configurar mais adiante na seção 4.</span><span class="sxs-lookup"><span data-stu-id="3144e-125">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Configurações iniciais do projeto](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="3144e-127">O projeto deve ser aberto automaticamente no editor Unreal, o que significa que você está pronto para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="3144e-127">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="3144e-128">Como habilitar os plugins necessários</span><span class="sxs-lookup"><span data-stu-id="3144e-128">Enabling required plugins</span></span>
<span data-ttu-id="3144e-129">Antes de começar a adicionar objetos à cena, você precisará habilitar dois plug-ins.</span><span class="sxs-lookup"><span data-stu-id="3144e-129">Before you start adding objects to the scene you'll need to enable two plugins.</span></span>

1. <span data-ttu-id="3144e-130">Abra **Editar > Plug-ins** e selecione **Realidade Aumentada** na lista de opções internas.</span><span class="sxs-lookup"><span data-stu-id="3144e-130">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="3144e-131">Role para baixo até **HoloLens** e marque **Habilitado**.</span><span class="sxs-lookup"><span data-stu-id="3144e-131">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Como habilitar plugins do HoloLens](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="3144e-133">Selecione **Realidade Virtual** na lista de opções internas.</span><span class="sxs-lookup"><span data-stu-id="3144e-133">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="3144e-134">Role a página para baixo até **Microsoft Windows Mixed Reality**, marque a opção **Habilitado** e reinicie o editor.</span><span class="sxs-lookup"><span data-stu-id="3144e-134">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Como habilitar o plug-in do Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="3144e-136">Os dois plug-ins são necessários para o desenvolvimento no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3144e-136">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="3144e-137">Com isso feito, o nível vazio estará pronto para ter companhia.</span><span class="sxs-lookup"><span data-stu-id="3144e-137">With that done your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="3144e-138">Criar um nível</span><span class="sxs-lookup"><span data-stu-id="3144e-138">Creating a level</span></span>
<span data-ttu-id="3144e-139">A sua próxima tarefa é criar uma configuração de jogador simples com um ponto de partida e um cubo para referência e escala.</span><span class="sxs-lookup"><span data-stu-id="3144e-139">Your next task is to create a simple player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="3144e-140">Selecione **Arquivo > Novo Nível** e escolha **Nível Vazio**.</span><span class="sxs-lookup"><span data-stu-id="3144e-140">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="3144e-141">A cena padrão no visor agora deve estar vazia.</span><span class="sxs-lookup"><span data-stu-id="3144e-141">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="3144e-142">Selecione **Básico** na guia **Modos** e arraste **PlayerStart** para a cena.</span><span class="sxs-lookup"><span data-stu-id="3144e-142">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="3144e-143">Defina **Localização** como **X = 0**, **Y = 0** e **Z = 0** na guia **Detalhes**. Isso define a localização do usuário no centro da cena quando o aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="3144e-143">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab. This sets the user at the center of the scene when the app starts up.</span></span>

![Visor com PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="3144e-145">Arraste um **Cubo** da guia **Básico** para a cena.</span><span class="sxs-lookup"><span data-stu-id="3144e-145">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="3144e-146">Defina **Localização** como **X = 50**, **Y = 0** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="3144e-146">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="3144e-147">Isso posiciona o cubo a 50 cm do jogador na hora de início.</span><span class="sxs-lookup"><span data-stu-id="3144e-147">This positions the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="3144e-148">Altere **Escala** para **X = 0,2**, **Y = 0,2** e **Z = 0,2** para diminuir o cubo.</span><span class="sxs-lookup"><span data-stu-id="3144e-148">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="3144e-149">Você não poderá ver o cubo, a menos que adicione uma luz à sua cena, que é sua última tarefa antes de testar a cena em questão.</span><span class="sxs-lookup"><span data-stu-id="3144e-149">You won’t be able to see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="3144e-150">Alterne para a guia **Luzes** no painel **Modos** e arraste uma **Luz Direcional** até a cena.</span><span class="sxs-lookup"><span data-stu-id="3144e-150">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="3144e-151">Posicione a luz acima **PlayerStart** para que você possa vê-la.</span><span class="sxs-lookup"><span data-stu-id="3144e-151">Position the light above **PlayerStart** so you can see it.</span></span>

![Visor com luz adicionada](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="3144e-153">Vá para **Arquivo > Salvar Atual**, nomeie seu nível **Principal** e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="3144e-153">Go to **File > Save Current**, name your level **Main**, and click **Save**.</span></span> 

<span data-ttu-id="3144e-154">Com a cena preparada, pressione **Jogar** na barra de ferramentas para ver o cubo em ação!</span><span class="sxs-lookup"><span data-stu-id="3144e-154">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="3144e-155">Quando tiver terminado de admirar seu trabalho, pressione **Esc** para interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3144e-155">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Um cubo no visor](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="3144e-157">Agora que a cena está configurada, você pode começar a adicionar o tabuleiro de xadrez e a peça para completar o ambiente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3144e-157">Now that the scene is setup, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="3144e-158">Como importar ativos</span><span class="sxs-lookup"><span data-stu-id="3144e-158">Importing assets</span></span>
<span data-ttu-id="3144e-159">A cena está parecendo um tanto vazia no momento, mas você corrigirá isso importando os ativos prontos para o projeto.</span><span class="sxs-lookup"><span data-stu-id="3144e-159">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="3144e-160">Baixe e descompacte a pasta de ativos do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span><span class="sxs-lookup"><span data-stu-id="3144e-160">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder.</span></span>

2. <span data-ttu-id="3144e-161">Clique em **Adicionar Novo > Nova Pasta** do **Navegador de Conteúdo** e nomeie-o como **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="3144e-161">Click **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="3144e-162">Clique duas vezes na nova pasta: é nela que você importará os ativos 3D.</span><span class="sxs-lookup"><span data-stu-id="3144e-162">Double-click the new folder - this is where you'll import the 3D assets.</span></span>

![Mostrar ou ocultar o painel de fontes](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="3144e-164">Clique em **Importar** do **Navegador de Conteúdo**, selecione todos os itens na pasta de ativos descompactados e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="3144e-164">Click **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="3144e-165">Essa pasta contém as malhas de objetos 3D para o tabuleiro de xadrez e as peças no formato FBX, bem como os mapas de textura no formato TGA que você usará para os materiais.</span><span class="sxs-lookup"><span data-stu-id="3144e-165">This folder contains the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="3144e-166">Quando a janela Opções de Importação do FBX for exibida, expanda a seção **Material** e altere **Método de Importação de Material** para **Não Criar o Material**.</span><span class="sxs-lookup"><span data-stu-id="3144e-166">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="3144e-167">Clique em **Importar Tudo**.</span><span class="sxs-lookup"><span data-stu-id="3144e-167">Click **Import All**.</span></span>

![Opções em Importar FBX](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="3144e-169">Isso é tudo o que você precisa fazer com relação aos ativos.</span><span class="sxs-lookup"><span data-stu-id="3144e-169">That's all you need to do for the assets.</span></span> <span data-ttu-id="3144e-170">Seu próximo conjunto de tarefas é criar os blocos de construção do aplicativo com blueprints.</span><span class="sxs-lookup"><span data-stu-id="3144e-170">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="3144e-171">Como adicionar blueprints</span><span class="sxs-lookup"><span data-stu-id="3144e-171">Adding blueprints</span></span>

1. <span data-ttu-id="3144e-172">Clique em **Adicionar Novo > Nova Pasta** no **Navegador de Conteúdo** e nomeie-o como **Navegador de Conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="3144e-172">Click **Add New > New Folder** in the **Content Browser** and name it **Content Browser**.</span></span> 

> [!NOTE]
> <span data-ttu-id="3144e-173">Se você não está familiarizado com [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), saiba que eles são ativos especiais que fornecem uma interface baseada em nó para criação de tipos de Atores e eventos de nível de script.</span><span class="sxs-lookup"><span data-stu-id="3144e-173">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="3144e-174">Clique duas vezes na pasta **Blueprints**, depois clique com o botão direito do mouse e selecione **Classe de Blueprint**.</span><span class="sxs-lookup"><span data-stu-id="3144e-174">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="3144e-175">Selecione **Ator** e nomeie o novo blueprint como **Tabuleiro**.</span><span class="sxs-lookup"><span data-stu-id="3144e-175">Select **Actor** and name the blueprint **Board**.</span></span> 

![Selecione uma classe pai para seu Blueprint](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="3144e-177">O novo blueprint **Tabuleiro** agora aparece na pasta **Blueprints**, conforme mostrado na captura de tela a seguir.</span><span class="sxs-lookup"><span data-stu-id="3144e-177">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![O novo Blueprint Board](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="3144e-179">Você está pronto para começar a adicionar materiais aos objetos criados.</span><span class="sxs-lookup"><span data-stu-id="3144e-179">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="3144e-180">Como trabalhar com materiais</span><span class="sxs-lookup"><span data-stu-id="3144e-180">Working with materials</span></span>
<span data-ttu-id="3144e-181">Os objetos que você criou são no padrão cinza, o que não os deixa com uma aparência muito divertida.</span><span class="sxs-lookup"><span data-stu-id="3144e-181">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="3144e-182">Adicionar materiais e malhas a seus objetos é o último conjunto de tarefas neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="3144e-182">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="3144e-183">Clique duas vezes em **Painel** para abrir o editor de blueprints.</span><span class="sxs-lookup"><span data-stu-id="3144e-183">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="3144e-184">Clique em **Adicionar Componente > Cena** no painel **Componentes** e nomeie-o como **Root**.</span><span class="sxs-lookup"><span data-stu-id="3144e-184">Click **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="3144e-185">Observe que **Root** aparece como um filho de **DefaultSceneRoot** na captura de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="3144e-185">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Substituindo a raiz](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="3144e-187">Clique e arraste **Root** para **DefaultSceneRoot** para substituí-lo e livrar-se da esfera no visor.</span><span class="sxs-lookup"><span data-stu-id="3144e-187">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Substituindo a raiz](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="3144e-189">Clique em **Adicionar Componente > Malha Estática** no painel **Componentes** e nomeie-o como **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="3144e-189">Click **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="3144e-190">Ele será exibido como um objeto filho em **Root**.</span><span class="sxs-lookup"><span data-stu-id="3144e-190">It will appear as a child object under **Root**.</span></span>

![Adicionando uma malha estática](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="3144e-192">Clique em **SM_Board**, role para baixo até a seção **Malha Estática** do painel **Detalhes** e selecione **ChessBoard** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="3144e-192">Click **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![A malha do tabuleiro no visor](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="3144e-194">Ainda no painel **Detalhes**, expanda a seção **Materiais** e clique em **Criar Ativo > Material** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="3144e-194">Still in the **Details** panel, expand the **Materials** section and click **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="3144e-195">Nomeie o material **M_ChessBoard** e salve-o na pasta **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="3144e-195">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Criar um material](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="3144e-197">Clique duas vezes na imagem do material **M_ChessBoard** para abrir o editor de material.</span><span class="sxs-lookup"><span data-stu-id="3144e-197">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Abrir editor de material](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="3144e-199">No Editor de Material, clique com o botão direito do mouse e procure **Exemplo de Textura**.</span><span class="sxs-lookup"><span data-stu-id="3144e-199">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="3144e-200">Expanda a seção **Base de Textura de Expressão do Material** no painel **Detalhes** e defina **Textura** para **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="3144e-200">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="3144e-201">Arraste o marcador de saída **RGB** para o marcador de Cor Base de **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="3144e-201">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Definir a cor base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="3144e-203">Repita a etapa anterior quatro mais vezes para criar mais quatro nós **Exemplo de Textura** com as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="3144e-203">Repeat the previous step four more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="3144e-204">Defina **Textura** como **ChessBoard_AO** e vincule o **RGB** ao marcador **Oclusão Ambiente**.</span><span class="sxs-lookup"><span data-stu-id="3144e-204">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="3144e-205">Defina **Textura** como **ChessBoard_Metal** e vincule o **RGB** ao marcador **Metálico**.</span><span class="sxs-lookup"><span data-stu-id="3144e-205">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="3144e-206">Defina **Textura** como **ChessBoard_Normal** e vincule o **RGB** ao marcador **Normal**.</span><span class="sxs-lookup"><span data-stu-id="3144e-206">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="3144e-207">Defina **Textura** como **ChessBoard_Rough** e vincule o **RGB** ao marcador **Aspereza**.</span><span class="sxs-lookup"><span data-stu-id="3144e-207">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="3144e-208">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="3144e-208">Click **Save**.</span></span> 

![Conectar as texturas restantes](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="3144e-210">Verifique se a configuração do material está parecida com a captura de tela acima antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3144e-210">Make sure the your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="3144e-211">Como popular a cena</span><span class="sxs-lookup"><span data-stu-id="3144e-211">Populating the scene</span></span>
<span data-ttu-id="3144e-212">Se você retornar ao blueprint **Tabuleiro**, verá que o material que acabou de criar foi aplicado.</span><span class="sxs-lookup"><span data-stu-id="3144e-212">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="3144e-213">Tudo o que falta fazer é configurar a cena!</span><span class="sxs-lookup"><span data-stu-id="3144e-213">All that's left is setting up the scene!</span></span> <span data-ttu-id="3144e-214">Primeiro, altere as propriedades a seguir para assegurar que o tabuleiro seja de um tamanho razoável e esteja inclinado corretamente quando posicionado na cena:</span><span class="sxs-lookup"><span data-stu-id="3144e-214">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="3144e-215">Defina **Escala** como **(0,05, 0,05, 0,05)** e **Rotação Z** como **90**.</span><span class="sxs-lookup"><span data-stu-id="3144e-215">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="3144e-216">Clique em **Compilar** na barra de ferramentas superior e depois em **Salvar**, então volte para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="3144e-216">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Tabuleiro de xadrez com material aplicado](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="3144e-218">Clique com o botão direito do mouse em **Cubo > Editar > Excluir** e arraste **Tabuleiro** do **Navegador de Conteúdo** para o visor.</span><span class="sxs-lookup"><span data-stu-id="3144e-218">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="3144e-219">Defina **Localização** como **X = 80**, **Y = 0** e **Z = -20**.</span><span class="sxs-lookup"><span data-stu-id="3144e-219">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="3144e-220">Clique no botão **Jogar** para exibir o novo tabuleiro no nível.</span><span class="sxs-lookup"><span data-stu-id="3144e-220">Click the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="3144e-221">Pressione **ESC** para retornar ao editor.</span><span class="sxs-lookup"><span data-stu-id="3144e-221">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="3144e-222">Agora você seguirá as mesmas etapas para criar uma peça de xadrez, do mesmo modo que você fez com o tabuleiro:</span><span class="sxs-lookup"><span data-stu-id="3144e-222">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="3144e-223">Acesse a pasta **Blueprints**, clique com o botão direito do mouse e selecione **Classe de Blueprint**, depois escolha **Ator**.</span><span class="sxs-lookup"><span data-stu-id="3144e-223">Go to the **Blueprints** folder, right-click and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="3144e-224">Nomeie esse ator como **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="3144e-224">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="3144e-225">Clique duas vezes em **WhiteKing** para abri-lo no Editor do Blueprint, clique em **Adicionar Componente > Cena** e nomeie-o como **Root**.</span><span class="sxs-lookup"><span data-stu-id="3144e-225">Double click **WhiteKing** to open it in the Blueprint Editor, click **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="3144e-226">Arraste e solte **Root** em **DefaultSceneRoot** para substituí-lo.</span><span class="sxs-lookup"><span data-stu-id="3144e-226">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="3144e-227">Clique em **Adicionar Componente > Malha Estática** e nomeie-o como **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="3144e-227">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="3144e-228">No painel Detalhes, defina **Malha Estática** como **Chess_King** e **Material** como um novo material chamado **M_ChessWhite**.</span><span class="sxs-lookup"><span data-stu-id="3144e-228">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="3144e-229">Abra **M_ChessWhite** no Editor de material e conecte os nós de **Exemplo de Textura** a seguir ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="3144e-229">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
    * <span data-ttu-id="3144e-230">Defina **Textura** como **ChessWhite_AO** e vincule o **RGB** ao marcador **Oclusão Ambiente**.</span><span class="sxs-lookup"><span data-stu-id="3144e-230">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="3144e-231">Defina **Textura** como **ChessWhite_Metal** e vincule o **RGB** ao marcador **Metálico**.</span><span class="sxs-lookup"><span data-stu-id="3144e-231">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="3144e-232">Defina **Textura** como **ChessWhite_Normal** e vincule o **RGB** ao marcador **Normal**.</span><span class="sxs-lookup"><span data-stu-id="3144e-232">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="3144e-233">Defina **Textura** como **ChessWhite_Rough** e vincule o **RGB** ao marcador **Aspereza**.</span><span class="sxs-lookup"><span data-stu-id="3144e-233">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="3144e-234">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="3144e-234">Click **Save**.</span></span> 

<span data-ttu-id="3144e-235">Verifique se o material **M_ChessKing** tem aparência semelhante à da imagem a seguir antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3144e-235">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Criar o material para o rei do xadrez](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="3144e-237">Você está quase lá, falta apenas adicionar a nova peça de xadrez à cena:</span><span class="sxs-lookup"><span data-stu-id="3144e-237">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="3144e-238">Abra o blueprint **WhiteKing**, altere a **Escala** para **(0,05; 0,05; 0,05)** e a **Rotação em Z** para **90**.</span><span class="sxs-lookup"><span data-stu-id="3144e-238">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="3144e-239">Compile e salve o blueprint e, em seguida, retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="3144e-239">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="3144e-240">Arraste **WhiteKing** para o visor, alterne para o painel **Esboço do Mundo** e arraste **WhiteKing** para o **Tabuleiro** para torná-lo um objeto filho.</span><span class="sxs-lookup"><span data-stu-id="3144e-240">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Contorno do Mundo](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="3144e-242">No painel **Detalhes**, em **Transformar**, defina a **Localização** de **WhiteKing** como **X = -26**, **Y = 4** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="3144e-242">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="3144e-243">Tudo concluído!</span><span class="sxs-lookup"><span data-stu-id="3144e-243">That's a wrap!</span></span> <span data-ttu-id="3144e-244">Clique em **Jogar** para ver o nível preenchido em ação e pressione **Esc** quando estiver pronto para sair.</span><span class="sxs-lookup"><span data-stu-id="3144e-244">Click **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="3144e-245">Este tutorial abordou muito conteúdo sobre a criação de um projeto simples, mas seu projeto está pronto para passar para a próxima parte da série: configuração para a realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="3144e-245">This tutorial covered a lot of ground creating a simple project, but your project is ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="3144e-246">Próxima seção: 3. Configurar seu projeto para a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="3144e-246">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)

---
title: 3. Como configurar seu projeto para a realidade misturada
description: Parte 3 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: d22c3d8c9048f53171298642768877d7bcdcb972
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330273"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="e4857-104">3. Como configurar seu projeto para a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="e4857-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="e4857-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e4857-105">Overview</span></span>

<span data-ttu-id="e4857-106">No tutorial anterior, você passou tempo configurando o projeto de aplicativo de xadrez.</span><span class="sxs-lookup"><span data-stu-id="e4857-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="e4857-107">Esta seção vai orientá-lo pela configuração do aplicativo para o desenvolvimento de realidade misturada, o que significa adicionar uma sessão de RA.</span><span class="sxs-lookup"><span data-stu-id="e4857-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="e4857-108">Para essa tarefa, você usará um ativo de dados ARSessionConfig que tem muitas configurações úteis de RA, como mapeamento espacial e oclusão.</span><span class="sxs-lookup"><span data-stu-id="e4857-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="e4857-109">Se você quiser se aprofundar, a documentação do Unreal Engine tem mais detalhes sobre o ativo [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) e a classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="e4857-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="e4857-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e4857-110">Objectives</span></span>
* <span data-ttu-id="e4857-111">Como trabalhar com configurações de RA do Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="e4857-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="e4857-112">Como usar um ativo de dados do ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="e4857-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="e4857-113">Como configurar um peão e um modo de jogo</span><span class="sxs-lookup"><span data-stu-id="e4857-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="e4857-114">Como adicionar o ativo de sessão</span><span class="sxs-lookup"><span data-stu-id="e4857-114">Adding the session asset</span></span>
<span data-ttu-id="e4857-115">As sessões de RA no Unreal não acontecem espontaneamente.</span><span class="sxs-lookup"><span data-stu-id="e4857-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="e4857-116">Para usar uma sessão, você precisa de um ativo de dados do ARSessionConfig com o qual trabalhar, que é sua próxima tarefa:</span><span class="sxs-lookup"><span data-stu-id="e4857-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="e4857-117">Clique em **Adicionar Novo > Diversos > Ativo de Dados** no **Navegador de Conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="e4857-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="e4857-118">Verifique se você está no nível raiz da pasta **Conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="e4857-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="e4857-119">Selecione **ARSessionConfig**, clique em **Selecionar** e nomeie o ativo **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="e4857-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Criar um ativo de dados](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="e4857-121">Clique duas vezes em **ARSessionConfig** para abri-lo, deixe todas as configurações padrão e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="e4857-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="e4857-122">Volte para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="e4857-122">Return to the Main window.</span></span> 

![Configuração de sessão de RA](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="e4857-124">Com isso feito, a próxima etapa é verificar se a sessão de RA começa quando o nível é carregado.</span><span class="sxs-lookup"><span data-stu-id="e4857-124">With that done, your next step is to make sure that the AR session starts when the level loads.</span></span> <span data-ttu-id="e4857-125">O Unreal tem um tipo especial de blueprint chamado **Blueprint de Nível**, que atua como um grafo de eventos global em todo esse nível.</span><span class="sxs-lookup"><span data-stu-id="e4857-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="e4857-126">Conectar o ativo ARSessionConfig no **Blueprint de Nível** garante que a sessão de RA será disparada exatamente quando o jogo começar.</span><span class="sxs-lookup"><span data-stu-id="e4857-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="e4857-127">Clique em **Blueprints > Abrir Blueprint de Nível** na barra de ferramentas do editor:</span><span class="sxs-lookup"><span data-stu-id="e4857-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![Abrir Blueprint de Nível](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="e4857-129">Arraste o nó de execução (ícone de seta para a esquerda) saindo de **Evento BeginPlay** e solte-o.</span><span class="sxs-lookup"><span data-stu-id="e4857-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="e4857-130">Pesquise por **Iniciar Sessão de RA** e pressione enter.</span><span class="sxs-lookup"><span data-stu-id="e4857-130">Search for the **Start AR Session** and hit enter.</span></span>  
    * <span data-ttu-id="e4857-131">Clique na lista suspensa **Selecionar Ativo** em **Configuração de Sessão** e escolha o ativo **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="e4857-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 
    * <span data-ttu-id="e4857-132">Escolha **Compilar**, depois **Salvar** e retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="e4857-132">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Iniciar Sessão de RA](images/unreal-uxt/3-start-ar-session.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="e4857-134">Criar um Peão</span><span class="sxs-lookup"><span data-stu-id="e4857-134">Create a Pawn</span></span>
<span data-ttu-id="e4857-135">Neste ponto, o projeto ainda precisa de um objeto de jogador.</span><span class="sxs-lookup"><span data-stu-id="e4857-135">At this point, the project still needs a player object.</span></span> <span data-ttu-id="e4857-136">No Unreal, um **Peão** representa o usuário no jogo, mas neste caso, será a experiência do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e4857-136">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="e4857-137">Clique em **Adicionar Novo > Classe de Blueprint** na pasta **Conteúdo** e expanda a seção **Todas as Classes** na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="e4857-137">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="e4857-138">Pesquise por **DefaultPawn**, clique em **Selecionar** e clique duas vezes no ativo para abrir.</span><span class="sxs-lookup"><span data-stu-id="e4857-138">Search for **DefaultPawn**, click **Select** and double-click the asset to open.</span></span> 

![Criar um Peão herdando de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="e4857-140">Por padrão, os Peões têm componentes de malha e colisão.</span><span class="sxs-lookup"><span data-stu-id="e4857-140">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="e4857-141">Na maioria dos projetos do Unreal, os Peões são objetos sólidos que podem colidir com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="e4857-141">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="e4857-142">Já que o peão e o usuário são a mesma coisa em realidade misturada, você deseja ser capaz de passar pelos hologramas sem nenhuma colisão.</span><span class="sxs-lookup"><span data-stu-id="e4857-142">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="e4857-143">Selecione **CollisionComponent** no painel **Componentes** e role para baixo até a seção **Colisão** do painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="e4857-143">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="e4857-144">Clique na lista suspensa de **Predefinições de Colisão** e altere o valor para **NoCollision**.</span><span class="sxs-lookup"><span data-stu-id="e4857-144">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="e4857-145">Faça o mesmo para o **MeshComponent** e, em seguida, escolha **Compilar** e **Salvar** o Blueprint.</span><span class="sxs-lookup"><span data-stu-id="e4857-145">Do the same for the **MeshComponent**, then **Compile** and **Save** the Blueprint.</span></span> 

![Ajustar as Predefinições de Colisão do Peão](images/unreal-uxt/3-nocollision.PNG)

<span data-ttu-id="e4857-147">Com seu trabalho aqui terminado, retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="e4857-147">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="e4857-148">Criar um Modo de Jogo</span><span class="sxs-lookup"><span data-stu-id="e4857-148">Create a Game Mode</span></span>
<span data-ttu-id="e4857-149">A última peça do quebra-cabeça da configuração da realidade misturada é o Modo de Jogo.</span><span class="sxs-lookup"><span data-stu-id="e4857-149">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="e4857-150">O Modo de Jogo determina um diversas configurações para o jogo ou a experiência, incluindo o peão padrão a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e4857-150">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="e4857-151">Clique em **Adicionar Novo > Classe de Blueprint** na pasta **Conteúdo** e expanda a seção **Todas as Classes** na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="e4857-151">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="e4857-152">Pesquise por **Base do Modo de Jogo**, nomeie-a como **MRGameMode** e clique duas vezes para abri-la.</span><span class="sxs-lookup"><span data-stu-id="e4857-152">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![MRGameMode no Navegador de Conteúdo](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="e4857-154">Vá para a seção **Classes** no painel **Detalhes** e altere a **Classe de Peão Padrão** para **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="e4857-154">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="e4857-155">Escolha **Compilar**, depois **Salvar** e retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="e4857-155">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![Definir a Classe Peão Padrão](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="e4857-157">Selecione **Editar > Configurações de Projetos** e clique em **Mapas e Modos** na lista à esquerda.</span><span class="sxs-lookup"><span data-stu-id="e4857-157">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="e4857-158">Expanda **Modos Padrão** e altere **Modo de Jogo Padrão** para **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="e4857-158">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="e4857-159">Expanda **Mapas Padrão** e altere **EditorStartupMap** e **GameDefaultMap** para **Principal**.</span><span class="sxs-lookup"><span data-stu-id="e4857-159">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="e4857-160">Dessa forma, quando você fechar o editor e abri-lo novamente ou jogar o jogo, o mapa Principal estará selecionado por padrão.</span><span class="sxs-lookup"><span data-stu-id="e4857-160">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![Configurações do projeto – Mapas e Modos](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="e4857-162">Com o projeto totalmente configurado para realidade misturada, você está pronto para passar para o próximo tutorial e começar a adicionar a entrada do usuário ao cenário.</span><span class="sxs-lookup"><span data-stu-id="e4857-162">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="e4857-163">Próxima seção: 4. Como tornar sua cena interativa</span><span class="sxs-lookup"><span data-stu-id="e4857-163">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
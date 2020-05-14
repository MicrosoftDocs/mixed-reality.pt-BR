---
title: 2. Inicializar o projeto e seu primeiro aplicativo
description: Parte 2 de um tutorial para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851570"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="8f363-104">2. Inicializar o projeto e seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="8f363-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="8f363-105">Esta seção apresenta a você uma introdução à criação de um aplicativo Unreal para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8f363-105">This section gets you started with creating a new Unreal application for HoloLens 2.</span></span> 

## <a name="objectives"></a><span data-ttu-id="8f363-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8f363-106">Objectives</span></span>

* <span data-ttu-id="8f363-107">Configurar o Unreal para o desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="8f363-107">Configure Unreal for HoloLens development</span></span>
* <span data-ttu-id="8f363-108">Importar ativos e configurar a cena</span><span class="sxs-lookup"><span data-stu-id="8f363-108">Import assets and set up the scene</span></span>

## <a name="create-a-new-unreal-project"></a><span data-ttu-id="8f363-109">Criar um projeto do Unreal</span><span class="sxs-lookup"><span data-stu-id="8f363-109">Create a new Unreal project</span></span>

1. <span data-ttu-id="8f363-110">Iniciar Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="8f363-110">Launch Unreal Engine</span></span>

2. <span data-ttu-id="8f363-111">Em **Novas Categorias de Projeto**, selecione **Jogos** e clique em Avançar.</span><span class="sxs-lookup"><span data-stu-id="8f363-111">Under **New Project Categories**, select **Games** and click Next.</span></span> <span data-ttu-id="8f363-112">Selecione um modelo **Em Branco** e clique em Avançar.</span><span class="sxs-lookup"><span data-stu-id="8f363-112">Select a **Blank** Template and click Next.</span></span> 

![Selecionar o modelo Em Branco](images/unreal-uxt/2-template.PNG)

3. <span data-ttu-id="8f363-114">Nas Configurações do Projeto, escolha **C++, 3D ou 2D escalonável, Mobile/Tablet** e **Nenhum Conteúdo Inicial**.</span><span class="sxs-lookup"><span data-stu-id="8f363-114">In Project Settings, choose **C++, Scalable 3D or 2D, Mobile / Tablet**, and **No Starter Content**.</span></span> <span data-ttu-id="8f363-115">Selecione um local para salvar o projeto e clique em **Criar Projeto**.</span><span class="sxs-lookup"><span data-stu-id="8f363-115">Select a location for your project to be saved and click **Create Project**.</span></span> <span data-ttu-id="8f363-116">Isso abrirá os arquivos do C++ em um projeto do Visual Studio e o editor do Unreal.</span><span class="sxs-lookup"><span data-stu-id="8f363-116">This will open up your C++ files in a Visual Studio project and the Unreal editor.</span></span> 

![Configurações iniciais do projeto](images/unreal-uxt/2-project-settings.PNG)

4. <span data-ttu-id="8f363-118">No canto superior esquerdo, vá para **Editar > Plug-ins**.</span><span class="sxs-lookup"><span data-stu-id="8f363-118">In the top left-hand corner, go to **Edit > Plugins**.</span></span> <span data-ttu-id="8f363-119">Em Realidade Aumentada, marque a caixa para habilitar o plug-in do **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="8f363-119">Under Augmented Reality, check the box to enable the **HoloLens** plugin.</span></span> <span data-ttu-id="8f363-120">Role para baixo até a seção Realidade Virtual e marque a caixa para habilitar o plug-in do **Microsoft Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="8f363-120">Scroll down to the Virtual Reality section and check the box to enable the **Microsoft Windows Mixed Reality** plugin.</span></span> <span data-ttu-id="8f363-121">Os dois plug-ins são necessários para o desenvolvimento no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8f363-121">Both plugins are required for HoloLens 2 development.</span></span> <span data-ttu-id="8f363-122">Reinicie o editor.</span><span class="sxs-lookup"><span data-stu-id="8f363-122">Restart your editor.</span></span> 

![Plug-ins](images/unreal-uxt/2-plugins.PNG)

5. <span data-ttu-id="8f363-124">No canto superior esquerdo, vá para **Arquivo > Novo Nível**.</span><span class="sxs-lookup"><span data-stu-id="8f363-124">In the top left-hand corner, go to **File > New Level**.</span></span> <span data-ttu-id="8f363-125">Selecione **Nível Vazio**.</span><span class="sxs-lookup"><span data-stu-id="8f363-125">Select **Empty Level**.</span></span> <span data-ttu-id="8f363-126">A cena padrão no visor agora deve estar vazia.</span><span class="sxs-lookup"><span data-stu-id="8f363-126">The default scene in the viewport should now be empty.</span></span>

6. <span data-ttu-id="8f363-127">Arraste e solte PlayerStart no painel Modos à esquerda, localizado na guia Básico. No painel Detalhes à direita, defina o local como X = 0, Y = 0, Z = 0 para que o usuário inicie na origem quando o aplicativo iniciar.</span><span class="sxs-lookup"><span data-stu-id="8f363-127">Drag PlayerStart and drop PlayerStart from the Modes panel on the left, located in the Basic tab. In the Details panel on the right, set the location to X = 0, Y = 0, Z = 0 in order to have the user start at the origin when the app stars.</span></span>

![Visor com PlayerStart](images/unreal-uxt/2-playerstart.PNG)

7. <span data-ttu-id="8f363-129">Arraste um **Cubo** da guia Básico do painel Modos para o visor.</span><span class="sxs-lookup"><span data-stu-id="8f363-129">Drag a **Cube** from the Basic tab of the Modes panel into the viewport.</span></span> <span data-ttu-id="8f363-130">No painel Detalhes, defina o local como X = 50, Y = 0, Z = 0 para definir o cubo a 50 cm de distância do jogador no momento do início.</span><span class="sxs-lookup"><span data-stu-id="8f363-130">In the Details panel, set the location to X = 50, Y = 0, Z = 0 to set the cube to 50 cm away from the player at start time.</span></span> <span data-ttu-id="8f363-131">Como o cubo padrão é muito grande, altere a escala do cubo para (0,2; 0,2; 0,2).</span><span class="sxs-lookup"><span data-stu-id="8f363-131">Since the default cube is quite large, change the Scale of the cube to (0.2, 0.2, 0.2).</span></span> 

8. <span data-ttu-id="8f363-132">Você não conseguirá ver o cubo a menos que adicione uma luz à cena.</span><span class="sxs-lookup"><span data-stu-id="8f363-132">You won’t be able to see the cube unless you add a light to your scene.</span></span> <span data-ttu-id="8f363-133">Alterne para a guia **Luzes** no painel Modos e arraste uma **Luz Direcional** até a cena, acima do PlayerStart.</span><span class="sxs-lookup"><span data-stu-id="8f363-133">Switch to the **Lights** tab on the Modes panel and drag a **Directional Light** into the scene, above the PlayerStart.</span></span>

![Visor com luz adicionada](images/unreal-uxt/2-light.PNG)

9.  <span data-ttu-id="8f363-135">Pressione o botão **Reproduzir** na barra de ferramentas para ver o cubo no visor!</span><span class="sxs-lookup"><span data-stu-id="8f363-135">Press the **Play** button on the toolbar to see your cube in the viewport!</span></span> <span data-ttu-id="8f363-136">Pressione **ESC** para parar o nível.</span><span class="sxs-lookup"><span data-stu-id="8f363-136">Press **Esc** to stop the level.</span></span> 

![Um cubo no visor](images/unreal-uxt/2-cube.PNG)

10. <span data-ttu-id="8f363-138">Vamos salvar o nível.</span><span class="sxs-lookup"><span data-stu-id="8f363-138">Let’s save your level.</span></span> <span data-ttu-id="8f363-139">No canto superior esquerdo, clique em **Arquivo > Salvar Atual**.</span><span class="sxs-lookup"><span data-stu-id="8f363-139">In the top left corner, click on **File > Save Current**.</span></span> <span data-ttu-id="8f363-140">Dê o nome "Main" ao nível e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="8f363-140">Name your level "Main" and click **Save**.</span></span> 

## <a name="set-up-a-chess-scene"></a><span data-ttu-id="8f363-141">Configurar uma cena de xadrez</span><span class="sxs-lookup"><span data-stu-id="8f363-141">Set up a chess scene</span></span>

1. <span data-ttu-id="8f363-142">No Navegador de Conteúdo, clique no ícone em Adicionar Novo para mostrar o painel de fontes.</span><span class="sxs-lookup"><span data-stu-id="8f363-142">In your Content Browser, click icon under Add New to show the sources panel.</span></span> <span data-ttu-id="8f363-143">Em seguida, clique em **Adicionar Novo > Nova Pasta** e nomeie a pasta como "ChessAssets".</span><span class="sxs-lookup"><span data-stu-id="8f363-143">Then click on **Add New > New Folder** and name the folder “ChessAssets”.</span></span> <span data-ttu-id="8f363-144">Clique duas vezes nessa pasta para navegar.</span><span class="sxs-lookup"><span data-stu-id="8f363-144">Double-click this folder to navigate in.</span></span> <span data-ttu-id="8f363-145">É aqui que vamos importar os ativos de 3D para nosso conjunto de xadrez.</span><span class="sxs-lookup"><span data-stu-id="8f363-145">This is where we’ll import the 3D assets for our chess set.</span></span>

![Mostrar ou ocultar o painel de fontes](images/unreal-uxt/2-showhidesources.PNG)

2. <span data-ttu-id="8f363-147">Baixe o arquivo zip de ativos do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span><span class="sxs-lookup"><span data-stu-id="8f363-147">Download the zip file of assets from [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span></span> <span data-ttu-id="8f363-148">Esse arquivo contém os modelos 3D para um tabuleiro de xadrez e um conjunto de xadrez.</span><span class="sxs-lookup"><span data-stu-id="8f363-148">This file contains the 3D models for a chess board and chess set.</span></span> <span data-ttu-id="8f363-149">Descompacte este arquivo.</span><span class="sxs-lookup"><span data-stu-id="8f363-149">Unzip this file.</span></span>

3. <span data-ttu-id="8f363-150">Na parte superior do Navegador de Conteúdo, clique em **Importar**.</span><span class="sxs-lookup"><span data-stu-id="8f363-150">At the top of the Content Browser, click on **Import**.</span></span> <span data-ttu-id="8f363-151">Navegue até a pasta que você acabou de descompactar e selecione todos os itens.</span><span class="sxs-lookup"><span data-stu-id="8f363-151">Navigate to the folder that you just unzipped and select all the items within.</span></span> <span data-ttu-id="8f363-152">Essa pasta contém arquivos FBX, que são as malhas do objeto 3D do tabuleiro e das peças de xadrez, bem como arquivos TGA que são os mapas de textura que usaremos para criar materiais para o tabuleiro e as peças.</span><span class="sxs-lookup"><span data-stu-id="8f363-152">This folder contains FBX files which are the 3D object meshes for our chess board and pieces, as well as TGA files which are the texture maps we’ll use to create materials for our board and pieces.</span></span> <span data-ttu-id="8f363-153">Clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="8f363-153">Click **Open**.</span></span> 

4. <span data-ttu-id="8f363-154">Uma janela de Opções de Importação do FBX será exibida.</span><span class="sxs-lookup"><span data-stu-id="8f363-154">An FBX Import Options window will pop up.</span></span> <span data-ttu-id="8f363-155">Na seção **Material**, altere o **Método de Importação de Material** para **Não Criar Material**.</span><span class="sxs-lookup"><span data-stu-id="8f363-155">In the **Material** section, change the **Material Import Method** to **Do Not Create Material**.</span></span> <span data-ttu-id="8f363-156">Em seguida, clique em **Importar Tudo**.</span><span class="sxs-lookup"><span data-stu-id="8f363-156">Then, click **Import All**.</span></span>

![Opções em Importar FBX](images/unreal-uxt/2-nocreatemat.PNG)

5. <span data-ttu-id="8f363-158">De volta à pasta de Conteúdo, crie uma pasta chamada **Blueprints**.</span><span class="sxs-lookup"><span data-stu-id="8f363-158">Back in your Content folder, create a new folder called **Blueprints**.</span></span> <span data-ttu-id="8f363-159">É aí que armazenaremos todos os blueprints, que são ativos especiais que fornecem uma interface baseada em nó para criar novos tipos de Atores e eventos de nível de script.</span><span class="sxs-lookup"><span data-stu-id="8f363-159">This is where we will store all our blueprints, which are special assets that provide a node-based interface to create new types of Actors and script level events.</span></span> 

6. <span data-ttu-id="8f363-160">Clique duas vezes na pasta **Blueprints** para navegar dentro dela e, em seguida, clique com o botão direito do mouse no Navegador de Conteúdo e selecione **Classe de Blueprint**.</span><span class="sxs-lookup"><span data-stu-id="8f363-160">Double click the **Blueprints** folder to navigate inside, then right click in your Content Browser and select **Blueprint Class**.</span></span> <span data-ttu-id="8f363-161">Clique em **Ator** e nomeie o novo blueprint como "Board".</span><span class="sxs-lookup"><span data-stu-id="8f363-161">Click on **Actor** and name the new blueprint “Board”.</span></span> <span data-ttu-id="8f363-162">Clique duas vezes em Board para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="8f363-162">Double click Board to open it.</span></span> 

![Selecione uma classe pai para seu Blueprint](images/unreal-uxt/2-bpparent.PNG)

![O novo Blueprint Board](images/unreal-uxt/2-bpboard.PNG)

7. <span data-ttu-id="8f363-165">No editor de Blueprint, navegue até o painel Componentes e clique em **Adicionar Componente > Cena**.</span><span class="sxs-lookup"><span data-stu-id="8f363-165">In the Blueprint editor, navigate to the Components panel and click **Add Component > Scene**.</span></span> <span data-ttu-id="8f363-166">Nomeie a cena criada recentemente como "Root" e, em seguida, clique e arraste Root sobre DefaultSceneRoot.</span><span class="sxs-lookup"><span data-stu-id="8f363-166">Name the newly created scene “Root”, and then click and drag Root over the DefaultSceneRoot.</span></span> <span data-ttu-id="8f363-167">Isso substituirá a raiz da cena padrão e se livrará da esfera no visor.</span><span class="sxs-lookup"><span data-stu-id="8f363-167">This will replace the default scene root and get rid of the sphere in the viewport.</span></span> 

![Substituindo a raiz](images/unreal-uxt/2-root.PNG)

8. <span data-ttu-id="8f363-169">Clique em **Adicionar Componente** novamente e, desta vez, escolha **Malha Estática**.</span><span class="sxs-lookup"><span data-stu-id="8f363-169">Click **Add Component** again, and this time choose **Static Mesh**.</span></span> <span data-ttu-id="8f363-170">Nomeie a nova malha estática como "SM_Board".</span><span class="sxs-lookup"><span data-stu-id="8f363-170">Name the new static mesh “SM_Board”.</span></span> 

![Adicionando uma malha estática](images/unreal-uxt/2-sm-board.PNG)

9. <span data-ttu-id="8f363-172">No painel **Detalhes**, localize a seção **Malha Estática** e clique na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="8f363-172">In the **Details** panel, locate the **Static Mesh** section and click the dropdown.</span></span> <span data-ttu-id="8f363-173">Selecione **ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="8f363-173">Select **ChessBoard**.</span></span> 

![A malha do tabuleiro no visor](images/unreal-uxt/2-sm-board-view.PNG)

10. <span data-ttu-id="8f363-175">Ainda no painel **Detalhes**, localize a seção **Materiais** e clique na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="8f363-175">Still in the **Details** panel, locate the **Materials** section and click the dropdown.</span></span> <span data-ttu-id="8f363-176">Em **Criar Ativo**, selecione **Material**.</span><span class="sxs-lookup"><span data-stu-id="8f363-176">Under **Create New Asset**, select **Material**.</span></span> <span data-ttu-id="8f363-177">Nomeie este ativo **M_ChessBoard** e salve-o na pasta **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="8f363-177">Name this asset **M_ChessBoard** and save it in the **ChessAssets** folder.</span></span> 

![Criar um material](images/unreal-uxt/2-newmat.PNG)

11. <span data-ttu-id="8f363-179">Clique duas vezes no quadrado ao lado da lista suspensa M_ChessBoard para abrir o material M_ChessBoard recém-criado.</span><span class="sxs-lookup"><span data-stu-id="8f363-179">Double click the square next to M_ChessBoard dropdown to open your newly created M_ChessBoard material.</span></span> <span data-ttu-id="8f363-180">No Editor de Material, clique com o botão direito do mouse e procure o nó **Exemplo de Textura**.</span><span class="sxs-lookup"><span data-stu-id="8f363-180">In the Material Editor, right click and search for the **Texture Sample** node.</span></span> <span data-ttu-id="8f363-181">No painel **Detalhes**, na seção **Base de Textura de Expressão do Material**, clique na lista suspensa e selecione **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="8f363-181">In the **Details** panel under the **Material Expression Texture Base** section, click the dropdown and select **ChessBoard_Albedo**.</span></span> <span data-ttu-id="8f363-182">Por fim, arraste o pino de saída **RGB** para o pino de Cor Base de **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="8f363-182">Finally, drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Definir a cor base](images/unreal-uxt/2-boardalbedomat.PNG)

12. <span data-ttu-id="8f363-184">Faça o mesmo mais quatro vezes, vinculando o Exemplo de Textura **ChessBoard_AO** ao pino **Oclusão de Ambiente**, o Exemplo de Textura **ChessBoard_Metal** ao pino **Metálico**, o Exemplo de Textura **ChessBoard_Normal** ao pino **Normal** e o Exemplo de Textura **ChessBoard_Rough** ao pino **Rugosidade**.</span><span class="sxs-lookup"><span data-stu-id="8f363-184">Do the same four more times, linking the **ChessBoard_AO** Texture Sample to the **Ambient Occlusion** pin, the **ChessBoard_Metal** Texture Sample to the **Metallic** pin, the **ChessBoard_Normal** Texture Sample to the **Normal** pin, and the **ChessBoard_Rough** Texture Sample to the **Roughness** pin.</span></span> <span data-ttu-id="8f363-185">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="8f363-185">Click **Save**.</span></span> 

![Conectar as texturas restantes](images/unreal-uxt/2-boardmat.PNG)

13. <span data-ttu-id="8f363-187">Retorne ao Blueprint **Board**.</span><span class="sxs-lookup"><span data-stu-id="8f363-187">Return to your **Board** Blueprint.</span></span> <span data-ttu-id="8f363-188">Você deve ver que o material que você acabou de criar foi aplicado ao Blueprint.</span><span class="sxs-lookup"><span data-stu-id="8f363-188">You should see that the material you just created has been applied to your Blueprint.</span></span> <span data-ttu-id="8f363-189">Para garantir que o tabuleiro esteja em um tamanho e posição razoáveis depois de colocá-lo em nossa cena, altere a **Escala** do tabuleiro para (0,05; 0,05; 0,05) e a **Rotação** para Z = 90.</span><span class="sxs-lookup"><span data-stu-id="8f363-189">To ensure the board is at a reasonable size and position once we place it in our scene, change the **Scale** of the board to (0.05, 0.05, 0.05) and the **Rotation** to Z = 90.</span></span> <span data-ttu-id="8f363-190">Na barra de ferramentas na parte superior, clique em **Compilar** e, em seguida, **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="8f363-190">In the toolbar at the top, click **Compile**, then **Save**.</span></span> <span data-ttu-id="8f363-191">Volte para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="8f363-191">Return to your Main window.</span></span> 

![Tabuleiro de xadrez com material aplicado](images/unreal-uxt/2-chessboard.PNG)

14. <span data-ttu-id="8f363-193">Agora, vamos excluir o cubo e substituí-lo pelo ator Board recém-criado.</span><span class="sxs-lookup"><span data-stu-id="8f363-193">Let’s now delete the cube and replace it with your newly created Board actor.</span></span> <span data-ttu-id="8f363-194">No **Contorno do Mundo**, clique com o botão direito do mouse em **Cubo > Editar > Excluir**.</span><span class="sxs-lookup"><span data-stu-id="8f363-194">In the **World Outliner**, right click your **Cube > Edit > Delete**.</span></span> <span data-ttu-id="8f363-195">Arraste o Board do Navegador de Conteúdo para o visor.</span><span class="sxs-lookup"><span data-stu-id="8f363-195">Drag Board from your Content Browser into the viewport.</span></span> <span data-ttu-id="8f363-196">Defina o local do tabuleiro como X = 80, Y = 0, Z = -20.</span><span class="sxs-lookup"><span data-stu-id="8f363-196">Set the location of the board to X = 80, Y = 0, Z = -20.</span></span> 

15. <span data-ttu-id="8f363-197">Clique no botão **Reproduzir** para exibir o novo tabuleiro em seu nível.</span><span class="sxs-lookup"><span data-stu-id="8f363-197">Click the **Play** button to view your new board in your level.</span></span> <span data-ttu-id="8f363-198">Pressione **ESC** para retornar ao editor.</span><span class="sxs-lookup"><span data-stu-id="8f363-198">Press **Esc** to return to the editor.</span></span> 

16. <span data-ttu-id="8f363-199">Agora, seguiremos as mesmas etapas para criar uma peça de xadrez, assim como fizemos com o tabuleiro, desta vez selecionando a malha e o material para a peça de xadrez:</span><span class="sxs-lookup"><span data-stu-id="8f363-199">Now we’ll follow the same steps to create a chess piece as we did with the board, this time selecting the mesh and material for the chess piece:</span></span>

    <span data-ttu-id="8f363-200">a) Navegue até a pasta Blueprints no Navegador de Conteúdo e crie uma classe Blueprint do tipo Ator.</span><span class="sxs-lookup"><span data-stu-id="8f363-200">a) Navigate to the Blueprints folder in the Content Browser and create a new Blueprint class of type Actor.</span></span> <span data-ttu-id="8f363-201">Nomeie esse ator como "WhiteKing".</span><span class="sxs-lookup"><span data-stu-id="8f363-201">Name this actor “WhiteKing”.</span></span>

    <span data-ttu-id="8f363-202">b) Clique duas vezes em WhiteKing para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="8f363-202">b) Double click WhiteKing to open it.</span></span> <span data-ttu-id="8f363-203">Adicione um novo componente Cena chamado "Root" e use-o para substituir DefaultSceneRoot.</span><span class="sxs-lookup"><span data-stu-id="8f363-203">Add a new Scene component named “Root” and use it to replace DefaultSceneRoot.</span></span> 

    <span data-ttu-id="8f363-204">c) Adicione um novo componente Malha Estática chamado "SM_King".</span><span class="sxs-lookup"><span data-stu-id="8f363-204">c) Add a new Static Mesh component named “SM_King”.</span></span> <span data-ttu-id="8f363-205">No painel Detalhes, defina **Malha Estática** como **Chess_King** e **Material** como um novo material chamado **M_ChessWhite**.</span><span class="sxs-lookup"><span data-stu-id="8f363-205">In the Details panel, set the **Static Mesh** to **Chess_King** and the **Material** to a new Material called **M_ChessWhite**.</span></span> 

    <span data-ttu-id="8f363-206">d) Abra o novo material **M_ChessWhite** e conecte as texturas pertinentes às respectivas entradas de material.</span><span class="sxs-lookup"><span data-stu-id="8f363-206">d) Open the new **M_ChessWhite** Material and hook up the relevant textures to their corresponding material inputs.</span></span> 

    ![Criar o material para o rei do xadrez](images/unreal-uxt/2-chesskingmat.PNG)

    <span data-ttu-id="8f363-208">e) De volta ao Blueprint **WhiteKing**, altere a **Escala** para (0,05; 0,05; 0,05) e a **Rotação** para Z = 90.</span><span class="sxs-lookup"><span data-stu-id="8f363-208">e) Back in your **WhiteKing** Blueprint, change the **Scale** to (0.05, 0.05, 0.05) and **Rotation** to Z = 90.</span></span>

    <span data-ttu-id="8f363-209">f) Compile e salve o blueprint e, em seguida, navegue de volta para a janela principal.</span><span class="sxs-lookup"><span data-stu-id="8f363-209">f) Compile and save your blueprint, then navigate back to your main window.</span></span> 

17. <span data-ttu-id="8f363-210">Arraste WhiteKing para o visor.</span><span class="sxs-lookup"><span data-stu-id="8f363-210">Drag WhiteKing into your viewport.</span></span> <span data-ttu-id="8f363-211">No **Contorno do Mundo**, arraste WhiteKing até Board para que WhiteKing agora seja um filho de Board.</span><span class="sxs-lookup"><span data-stu-id="8f363-211">In the **World Outliner**, drag WhiteKing onto Board so that WhiteKing is now a child of Board.</span></span> 

![Contorno do Mundo](images/unreal-uxt/2-child.PNG)

18. <span data-ttu-id="8f363-213">No painel **Detalhes**, em **Transformar**, defina o **Local** de WhiteKing como X = -26, Y = 4, Z = 0</span><span class="sxs-lookup"><span data-stu-id="8f363-213">In the **Details** panel under **Transform**, set the **Location** of WhiteKing to X = -26, Y = 4, Z = 0</span></span>

19. <span data-ttu-id="8f363-214">Clique em **Reproduzir** para ver seu nível.</span><span class="sxs-lookup"><span data-stu-id="8f363-214">Click **Play** to see your level.</span></span> <span data-ttu-id="8f363-215">Pressione **ESC** para sair.</span><span class="sxs-lookup"><span data-stu-id="8f363-215">Press **Esc** to exit.</span></span> 

[<span data-ttu-id="8f363-216">Próxima seção: 3. Configurar seu projeto para a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="8f363-216">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)
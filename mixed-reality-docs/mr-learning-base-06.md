---
title: Tutoriais de introdução – 6. Como criar interfaces do usuário
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4eecbd7d292a4d23e0dddc8e9244ed2701a10381
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376618"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="cbd4a-105">6. Como criar interfaces do usuário</span><span class="sxs-lookup"><span data-stu-id="cbd4a-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="cbd4a-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="cbd4a-106">Overview</span></span>

<span data-ttu-id="cbd4a-107">Neste tutorial, você aprenderá a criar uma interface do usuário simples usando os pré-fabricados de menu e de botão do MRTK junto com o componente TextMeshPro do Unity.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="cbd4a-108">Você também aprenderá a configurar os botões para disparar eventos e adicionar elementos de interface do usuário de dica de ferramenta dinâmica para fornecer ao usuário informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="cbd4a-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cbd4a-109">Objectives</span></span>

* <span data-ttu-id="cbd4a-110">Saber como organizar botões em uma coleção</span><span class="sxs-lookup"><span data-stu-id="cbd4a-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="cbd4a-111">Saber como usar os pré-fabricados de menu do MRTK</span><span class="sxs-lookup"><span data-stu-id="cbd4a-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="cbd4a-112">Saber como interagir com hologramas usando os botões e menus da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="cbd4a-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="cbd4a-113">Saber como adicionar elementos de texto</span><span class="sxs-lookup"><span data-stu-id="cbd4a-113">Learn how to add text elements</span></span>
* <span data-ttu-id="cbd4a-114">Saber como gerar dicas de ferramentas em objetos dinamicamente</span><span class="sxs-lookup"><span data-stu-id="cbd4a-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="cbd4a-115">Criar um painel estático de botões</span><span class="sxs-lookup"><span data-stu-id="cbd4a-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="cbd4a-116">Na janela Hierarquia, clique com o botão direito do mouse no objeto **RoverExplorer** e selecione **Criar Vazio** para adicionar um objeto vazio como um filho do RoverExplorer, nomeie o objeto **Buttons** e configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="cbd4a-117">**Posição**: X = -0,6, Y = 0,036, Z = -0,5</span><span class="sxs-lookup"><span data-stu-id="cbd4a-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="cbd4a-118">**Rotação**: X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cbd4a-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="cbd4a-119">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="cbd4a-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="cbd4a-121">Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados**, clique e arraste o pré-fabricado **PressableRoundButton** no objeto **Buttons** e, em seguida, clique com o botão direito do mouse no PressableRoundButton e selecione **Duplicar** para criar uma cópia, repita até que você tenha um total de três objetos PressableRoundButton:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="cbd4a-123">Na janela hierarquia, selecione o objeto **Buttons**, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **GridObjectCollection** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="cbd4a-124">**Tipo de Classificação**: Ordem do Filho</span><span class="sxs-lookup"><span data-stu-id="cbd4a-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="cbd4a-125">**Layout**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="cbd4a-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="cbd4a-126">**Largura da Célula**: 0,2</span><span class="sxs-lookup"><span data-stu-id="cbd4a-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="cbd4a-127">**Âncora**: Centro Esquerda</span><span class="sxs-lookup"><span data-stu-id="cbd4a-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="cbd4a-128">Em seguida, clique no botão **Atualizar Coleção** para atualizar a posição dos objetos filho do objeto Buttons:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="cbd4a-130">Na janela Hierarquia, nomeie os botões **Dicas**, **Detalhar** e **Redefinir**.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="cbd4a-131">Para cada botão, selecione o objeto filho **SeeItSayItLabel** > **TextMeshPro** e, em seguida, na janela Inspetor, altere o respectivo texto de componente **TextMeshPro – Texto** para corresponder aos nomes dos botões:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="cbd4a-133">Quando tiver terminado, recolha os objetos filho do objeto Buttons.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="cbd4a-134">Na janela Hierarquia, selecione o objeto do botão **Dicas** e, na janela Inspetor, configure o evento **OnClick ()** Interativo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="cbd4a-135">Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cbd4a-136">Na lista suspensa **Sem Função**, selecione **PlacementHintsController** > **TogglePlacementHints ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="cbd4a-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

<span data-ttu-id="cbd4a-138">Na janela Hierarquia, selecione o objeto do botão **Detalhar** e, na janela Inspetor, configure o evento **OnClick ()** Interativo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-138">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="cbd4a-139">Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-139">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cbd4a-140">Na lista suspensa **Sem Função**, selecione **ExplodedViewController** > **ToggleExplodedView ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="cbd4a-140">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="cbd4a-142">Pressione o botão Reproduzir para entrar no Modo de jogo e pressione e segure o botão barra de espaço para ativar a mão; e use o mouse para pressionar o botão **Dicas** para alternar a visibilidade dos objetos de dica de posicionamento:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-142">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="cbd4a-144">e o botão **Detalhar** para ativar e desativar a exibição detalhada:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-144">and the **Explode** button to toggle the exploded view on and off:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="cbd4a-146">Como criar um menu dinâmico que segue o usuário</span><span class="sxs-lookup"><span data-stu-id="cbd4a-146">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="cbd4a-147">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK** > **SDK** > **UX** > **Pré-fabricados** > **Menus**, clique e arraste o pré-fabricado **NearMenu4x1** para a janela Hierarquia, defina a sua **Posição** de Transformar como X = 0, Y = -0,4, Z = 0 e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-147">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="cbd4a-148">Verifique se o **Tipo de Destino Rastreado** do componente **SolverHandler** está definido como **Cabeça**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-148">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="cbd4a-149">Marque a caixa de seleção ao lado do componente Solucionador **RadialView** para que ele seja habilitado por padrão</span><span class="sxs-lookup"><span data-stu-id="cbd4a-149">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="cbd4a-151">Na janela Hierarquia, renomeie o objeto para **Menu** e, em seguida, expanda o seu objeto filho **ButtonCollection** para revelar os quatro botões:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-151">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="cbd4a-153">Renomeie o primeiro botão como **Indicador** e, na janela Inspetor, configure o componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-153">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="cbd4a-154">Altere o **Texto do Rótulo Principal** para que ele corresponda ao nome do botão</span><span class="sxs-lookup"><span data-stu-id="cbd4a-154">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="cbd4a-155">Atribua o objeto **Indicador** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-155">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cbd4a-156">Na lista suspensa **Sem Função**, selecione **GameObject** > **SetActive (bool)** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="cbd4a-156">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="cbd4a-157">Verifique se a caixa de seleção do argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-157">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="cbd4a-158">Altere o **Ícone** para o ícone "pesquisar"</span><span class="sxs-lookup"><span data-stu-id="cbd4a-158">Change the **Icon** to the 'search' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="cbd4a-160">Na janela Hierarquia, selecione o objeto **Indicador** e, na janela Inspetor, desmarque a caixa de seleção ao lado do nome para torná-lo inativo por padrão:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-160">In the Hierarchy window, select the **Indicator** object, then in the Inspector window, uncheck the checkbox next to its name to make it inactive by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="cbd4a-162">Agora, quando o aplicativo é iniciado, o Indicador é desabilitado por padrão e pode ser habilitado pressionando o botão Indicador.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-162">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="cbd4a-163">Renomeie o segundo botão como **TapToPlace** e, na janela Inspetor, configure o componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-163">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="cbd4a-164">Altere o **Texto do Rótulo Principal** para que ele corresponda ao nome do botão</span><span class="sxs-lookup"><span data-stu-id="cbd4a-164">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="cbd4a-165">Atribua o objeto RoverExplorer > **RoverAssembly** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-165">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cbd4a-166">Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="cbd4a-166">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="cbd4a-167">Verifique se a caixa de seleção do argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-167">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="cbd4a-168">Altere o **Ícone** para o ícone "mão com raio"</span><span class="sxs-lookup"><span data-stu-id="cbd4a-168">Change the **Icon** to the 'hand with ray' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="cbd4a-170">Na janela Hierarquia, selecione o objeto **RoverAssembly** e, na janela Inspetor, configure o componente **Tocar para Posicionar (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-170">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="cbd4a-171">Desmarque a caixa de seleção ao lado do nome para torná-la inativa por padrão</span><span class="sxs-lookup"><span data-stu-id="cbd4a-171">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="cbd4a-172">Na seção de evento **On Placing Started ()** , clique no ícone **+** para adicionar um novo evento:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-172">In the **On Placing Started ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="cbd4a-173">Atribua o objeto RoverExplorer > **RoverAssembly** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-173">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="cbd4a-174">Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="cbd4a-174">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="cbd4a-175">Verifique se a caixa de seleção do argumento está **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-175">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="cbd4a-177">Agora, quando o aplicativo é iniciado, a funcionalidade Tocar para Posicionar é desabilitada por padrão e pode ser habilitada pressionando o botão Tocar para Posicionar.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-177">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="cbd4a-178">Além disso, quando o recurso tocar para posicionar for concluído, ele se desabilitará sozinho.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-178">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="cbd4a-179">Como adicionar texto à cena</span><span class="sxs-lookup"><span data-stu-id="cbd4a-179">Adding text to the scene</span></span>

<span data-ttu-id="cbd4a-180">Na janela Hierarquia, clique com o botão direito do mouse no objeto **Tabela** e selecione **Objeto 3D** > **Texto – TextMeshPro** para adicionar um objeto de texto como um filho do objeto Table e, em seguida, na janela Inspetor, configure o componente **Transformação de Retângulo** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-180">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="cbd4a-181">Altere a **Posição Y** para 1</span><span class="sxs-lookup"><span data-stu-id="cbd4a-181">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="cbd4a-182">Altere a **Largura** para 1</span><span class="sxs-lookup"><span data-stu-id="cbd4a-182">Change **Width** to 1</span></span>
* <span data-ttu-id="cbd4a-183">Altere a **Altura** para 1</span><span class="sxs-lookup"><span data-stu-id="cbd4a-183">Change **Height** to 1</span></span>
* <span data-ttu-id="cbd4a-184">Altere a **Rotação X** para 90</span><span class="sxs-lookup"><span data-stu-id="cbd4a-184">Change **Rotation X** to 90</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="cbd4a-186">Em seguida, configure o componente **TextMeshPro – Texto** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-186">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="cbd4a-187">Altere o **Texto** para o Explorador do Rover</span><span class="sxs-lookup"><span data-stu-id="cbd4a-187">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="cbd4a-188">Altere o **Estilo da Fonte** para Negrito</span><span class="sxs-lookup"><span data-stu-id="cbd4a-188">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="cbd4a-189">Altere o **Tamanho da Fonte** para 1</span><span class="sxs-lookup"><span data-stu-id="cbd4a-189">Change **Font Size** to 1</span></span>
* <span data-ttu-id="cbd4a-190">Altere as Configurações Adicionais > **Margens** para 0,03</span><span class="sxs-lookup"><span data-stu-id="cbd4a-190">Change Extra Settings > **Margins** to 0.03</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="cbd4a-192">Como adicionar dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="cbd4a-192">Adding tooltips</span></span>

<span data-ttu-id="cbd4a-193">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK** > **SDK** > **Recursos** > **UX** > **Pré-fabricados** > **Dica de Ferramenta** para localizar os pré-fabricados de dica de ferramenta:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-193">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="cbd4a-195">Na janela Hierarquia, expanda o objeto RoverExplorer > **RoverParts** e selecione todos os seus objetos filhos de peças do rover. Em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **ToolTipSpawner** e configurá-lo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-195">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="cbd4a-196">Verifique se a caixa de seleção **Foco Habilitado** está marcada para exigir que o usuário olhe a peça para que a dica de ferramenta apareça</span><span class="sxs-lookup"><span data-stu-id="cbd4a-196">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="cbd4a-197">Atribua o pré-fabricado **Dica de Ferramenta de Linha Simples** da janela Projeto para o campo **Pré-fabricado da Dica de Ferramenta**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-197">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="cbd4a-198">Altere as Configurações de Substituição da Dica de Ferramenta > **Modo de Configurações** para **Substituir**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-198">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="cbd4a-199">Altere as Configurações de Substituição da Dica de Ferramenta > **Dinamizar Manualmente a Posição da Localização Y** para **1,5**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-199">Change the ToolTip Override Settings > **Manual Pivot Location Position Y** to **1.5**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="cbd4a-201">Na janela Hierarquia, selecione a primeira peça do Rover, RoverParts > **Camera_Part** e configure o componente **ToolTipSpawner** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-201">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="cbd4a-202">Altere o **Texto da Dica de Ferramenta** para refletir o nome da peça, ou seja, **Câmera**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-202">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="cbd4a-204">**Repita** essa etapa para cada um dos objetos da peça do Rover para configurar o componente **ToolTipSpawner** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-204">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="cbd4a-205">Para o **Generator_Part**, altere o **Texto da Dica de Ferramenta** para **Gerador**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-205">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="cbd4a-206">Para o **Lights_Part**, altere o **Texto da Dica de Ferramenta** para **Luzes**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-206">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="cbd4a-207">Para o **UHFAntenna_Part**, altere o **Texto da Dica de Ferramenta** para o campo **Antena UHF**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-207">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="cbd4a-208">Para o **Spectrometer_Part**, altere o **Texto da Dica de Ferramenta** para **Espectrômetro**</span><span class="sxs-lookup"><span data-stu-id="cbd4a-208">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="cbd4a-209">Pressione o botão Reproduzir para entrar no Modo de jogo e pressione e segure o botão direito do mouse enquanto move o mouse até que o olhar esteja em uma das peças e a dica de ferramenta para essa peça seja exibida:</span><span class="sxs-lookup"><span data-stu-id="cbd4a-209">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="cbd4a-211">Parabéns</span><span class="sxs-lookup"><span data-stu-id="cbd4a-211">Congratulations</span></span>

<span data-ttu-id="cbd4a-212">Neste tutorial, você aprendeu a criar uma interface do usuário simples usando os pré-fabricados de menu e de botão fornecidos do MRTK junto com o componente TextMeshPro do Unity e como configurar os botões para disparar eventos quando eles forem pressionados.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-212">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="cbd4a-213">Você também aprendeu como adicionar elementos de interface do usuário de dica de ferramenta dinâmicos para fornecer ao usuário informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="cbd4a-213">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="cbd4a-214">Próximo tutorial: 7. Interagir com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="cbd4a-214">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)

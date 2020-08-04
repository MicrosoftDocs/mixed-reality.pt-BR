---
title: Tutoriais de introdução – 4. Como posicionar objetos na cena
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 71990db23b5154de916f0eda86a978885ab53547
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376628"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="cfd60-105">4. Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="cfd60-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="cfd60-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="cfd60-106">Overview</span></span>

<span data-ttu-id="cfd60-107">Neste tutorial, você importará os ativos do tutorial e posicionará os objetos fornecidos na cena.</span><span class="sxs-lookup"><span data-stu-id="cfd60-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="cfd60-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cfd60-108">Objectives</span></span>

* <span data-ttu-id="cfd60-109">Saiba como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="cfd60-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="cfd60-110">Saiba como usar o recurso Coleção de Objetos de Grade do MRTK</span><span class="sxs-lookup"><span data-stu-id="cfd60-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="cfd60-111">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="cfd60-111">Importing the tutorial assets</span></span>

<span data-ttu-id="cfd60-112">Baixe e importe o seguinte pacote personalizado do Unity:</span><span class="sxs-lookup"><span data-stu-id="cfd60-112">Download and import the following Unity custom package:</span></span>

* [<span data-ttu-id="cfd60-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cfd60-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="cfd60-114">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="cfd60-114">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="cfd60-116">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Como importar o MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="cfd60-116">For a reminder on how to import a Unity custom package, you can refer to the [Importing the MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="cfd60-117">Como criar um objeto pai</span><span class="sxs-lookup"><span data-stu-id="cfd60-117">Creating the parent object</span></span>

<span data-ttu-id="cfd60-118">Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Criar Vazio** para adicionar um objeto vazio à sua cena:</span><span class="sxs-lookup"><span data-stu-id="cfd60-118">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="cfd60-120">Para exibir a janela Cena e Jogo lado a lado como mostra a imagem acima, arraste a janela Jogo para o lado direito da janela Cena.</span><span class="sxs-lookup"><span data-stu-id="cfd60-120">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="cfd60-121">Para saber mais sobre como personalizar o seu workspace, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Como personalizar o seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="cfd60-121">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="cfd60-122">Clique com o botão direito do mouse no objeto recém-criado, selecione **Renomear** e altere o nome para **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="cfd60-122">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="cfd60-124">Com o objeto RoverExplorer ainda selecionado, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cfd60-124">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="cfd60-125">**Posição**: X = 0, Y = -0,6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="cfd60-125">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="cfd60-126">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cfd60-126">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="cfd60-127">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="cfd60-127">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="cfd60-129">A câmera representa a cabeça do usuário e é posicionada na origem, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="cfd60-129">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="cfd60-130">Em geral, uma unidade no Unity corresponde a aproximadamente um metro no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="cfd60-130">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="cfd60-131">Porém, há exceções, por exemplo, quando objetos são filhos de objetos dimensionados.</span><span class="sxs-lookup"><span data-stu-id="cfd60-131">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="cfd60-132">No cenário acima, o RoverExplorer é posicionado 2 metros na frente e 0,6 metros abaixo da cabeça do usuário.</span><span class="sxs-lookup"><span data-stu-id="cfd60-132">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="cfd60-133">Como adicionar os pré-fabricados do tutorial</span><span class="sxs-lookup"><span data-stu-id="cfd60-133">Adding the tutorial prefabs</span></span>

<span data-ttu-id="cfd60-134">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados**:</span><span class="sxs-lookup"><span data-stu-id="cfd60-134">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="cfd60-136">Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um GameObject pré-configurado armazenado como um Ativo Unitário e pode ser reutilizado em todo o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="cfd60-136">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="cfd60-137">Na janela Projeto, clique e arraste o pré-fabricado **Tabela** no objeto **RoverExplorer** para torná-la um filho do objeto RoverExplorer e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cfd60-137">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="cfd60-138">**Posição**: X = 0, Y = -0,005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cfd60-138">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="cfd60-139">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cfd60-139">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="cfd60-140">**Escala**: X = 1,2, Y = 0,01, Z = 1,2</span><span class="sxs-lookup"><span data-stu-id="cfd60-140">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="cfd60-142">Para exibir a cena conforme mostrado na imagem acima use o <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Utensílio de Cena</a>, localizado no canto superior direito da janela Cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço, clique duas vezes no objeto MixedRealityPlayspace para colocá-lo em foco na câmera e amplie se necessário.</span><span class="sxs-lookup"><span data-stu-id="cfd60-142">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="cfd60-143">Na janela Projeto, clique e arraste o pré-fabricado **RoverAssembly** para o objeto **RoverExplorer** para torná-lo um filho do objeto RoverExplorer e, em seguida, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cfd60-143">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="cfd60-144">**Posição**: X = -0,1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cfd60-144">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="cfd60-145">**Rotação**: X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cfd60-145">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="cfd60-146">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="cfd60-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="cfd60-148">Como organizar objetos em uma coleção</span><span class="sxs-lookup"><span data-stu-id="cfd60-148">Organizing objects in a collection</span></span>

<span data-ttu-id="cfd60-149">Na janela Hierarquia, clique com o botão direito do mouse no objeto **RoverExplorer** e selecione **Criar Vazio** para adicionar um objeto vazio como um filho do RoverExplorer, nomeie o objeto **RoverParts** e configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cfd60-149">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="cfd60-150">**Posição**: X = 0, Y = 0,06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cfd60-150">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="cfd60-151">**Rotação**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="cfd60-151">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="cfd60-152">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="cfd60-152">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="cfd60-154">Na janela Hierarquia, selecione todos os objetos filhos em RoverExplorer > RoverAssembly > RoverModel > **Parts** clique com o botão direito do mouse neles e selecione **Duplicar** para criar uma cópia de cada uma das peças:</span><span class="sxs-lookup"><span data-stu-id="cfd60-154">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="cfd60-156">Para selecionar vários objetos adjacentes, pressione e segure a tecla SHIFT enquanto usa o mouse para selecionar o primeiro e o último objeto.</span><span class="sxs-lookup"><span data-stu-id="cfd60-156">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="cfd60-157">Com os objetos filho de Peças recentemente duplicados ainda selecionados, clique e arraste-os para o objeto **RoverParts** para torná-los objetos filho do objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="cfd60-157">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="cfd60-159">Para facilitar o trabalho com a sua cena, na janela Hierarquia clique no ícone de **olho** à esquerda do objeto para desativar a **visibilidade da cena** para o objeto **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="cfd60-159">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverExplorer** object off.</span></span> <span data-ttu-id="cfd60-160">Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo:</span><span class="sxs-lookup"><span data-stu-id="cfd60-160">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="cfd60-162">Para saber mais sobre os controles de Visibilidade da Cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="cfd60-162">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="cfd60-163">Na janela Hierarquia, limpe os nomes dos objetos filho RoverParts substituindo o **(1)** acrescentado por **_Part**:</span><span class="sxs-lookup"><span data-stu-id="cfd60-163">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="cfd60-165">Na janela Hierarquia, selecione o objeto **RoverParts** e, em seguida, na janela Inspetor, clique no botão **Adicionar Componente** e pesquise e selecione **GridObjectCollection** para adicionar o componente GridObjectCollection ao objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="cfd60-165">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="cfd60-167">Configure os valores de componente **GridObjectCollection** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cfd60-167">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="cfd60-168">**Tipo de Classificação**: Alfabético</span><span class="sxs-lookup"><span data-stu-id="cfd60-168">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="cfd60-169">**Layout**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="cfd60-169">**Layout**: Horizontal</span></span>
* <span data-ttu-id="cfd60-170">**Largura da Célula**: 0,25</span><span class="sxs-lookup"><span data-stu-id="cfd60-170">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="cfd60-171">**Distância do pai**: 0,38</span><span class="sxs-lookup"><span data-stu-id="cfd60-171">**Distance from parent**: 0.38</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="cfd60-173">Em seguida, clique no botão **Atualizar Coleção** para atualizar a posição dos objetos filho RoverParts:</span><span class="sxs-lookup"><span data-stu-id="cfd60-173">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="cfd60-175">Parabéns</span><span class="sxs-lookup"><span data-stu-id="cfd60-175">Congratulations</span></span>

<span data-ttu-id="cfd60-176">Neste tutorial, você aprendeu a posicionar objetos na cena em relação ao usuário e a usar o recurso Coleção de Objetos de Grade do MRTK para organizar objetos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="cfd60-176">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

[<span data-ttu-id="cfd60-177">Próximo tutorial: 5. Criar conteúdo dinâmico usando Solucionadores</span><span class="sxs-lookup"><span data-stu-id="cfd60-177">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)

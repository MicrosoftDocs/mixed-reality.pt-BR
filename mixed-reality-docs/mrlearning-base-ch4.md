---
title: Tutoriais de introdução-5. Interagindo com objetos 3D
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130187"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="51387-104">5. interagindo com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="51387-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="51387-105">Neste tutorial, você aprenderá sobre o conteúdo básico de 3D e a experiência do usuário, como organizar objetos 3D como parte de uma coleção, caixas delimitadoras para manipulação básica, interação próxima e extrema e gestos de toque e captura com acompanhamento manual.</span><span class="sxs-lookup"><span data-stu-id="51387-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="51387-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="51387-106">Objectives</span></span>

* <span data-ttu-id="51387-107">Criar um painel de objetos 3D que serão usados para os outros objetivos de aprendizado</span><span class="sxs-lookup"><span data-stu-id="51387-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="51387-108">Implementar caixas delimitadoras</span><span class="sxs-lookup"><span data-stu-id="51387-108">Implement bounding boxes</span></span>
* <span data-ttu-id="51387-109">Configurar objetos 3D para manipulação básica, como mover, girar e dimensionar</span><span class="sxs-lookup"><span data-stu-id="51387-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="51387-110">Explorar a interação próxima e distante</span><span class="sxs-lookup"><span data-stu-id="51387-110">Explore near and far interaction</span></span>
* <span data-ttu-id="51387-111">Saiba mais sobre gestos de acompanhamento de mão, como pegar e tocar</span><span class="sxs-lookup"><span data-stu-id="51387-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="51387-112">Importando os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="51387-112">Importing the tutorial assets</span></span>

<span data-ttu-id="51387-113">Baixe e importe o pacote personalizado do Unity:</span><span class="sxs-lookup"><span data-stu-id="51387-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="51387-114">MRTK. HoloLens2. Unity. tutoriais. assets. GettingStarted. 2.2.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="51387-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

<span data-ttu-id="51387-115">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="51387-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="51387-117">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções de [importação do kit de ferramentas da realidade misturada](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="51387-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="51387-118">Desobstruindo o modo de exibição de cena</span><span class="sxs-lookup"><span data-stu-id="51387-118">Decluttering the scene view</span></span>

<span data-ttu-id="51387-119">Para facilitar o trabalho com sua cena, defina a visibilidade da **cena** para os objetos Cube e buttoncollection como off clicando no ícone de **olho** à esquerda dos objetos.</span><span class="sxs-lookup"><span data-stu-id="51387-119">To make it easier to work with your scene, set the **scene visibility** for the Cube and ButtonCollection objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="51387-120">Isso oculta o objeto na janela de cena sem alterar sua visibilidade no jogo:</span><span class="sxs-lookup"><span data-stu-id="51387-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="51387-122">Para saber mais sobre os controles de visibilidade da cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode visitar a documentação de <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidade da cena</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="51387-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="51387-123">Organizando objetos 3D em uma coleção</span><span class="sxs-lookup"><span data-stu-id="51387-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="51387-124">Nesta seção, você criará um painel de objetos 3D que será usado ao explorar várias maneiras de interagir com objetos 3D nas seções a seguir deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="51387-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="51387-125">Especificamente, você configurará os objetos 3D a serem posicionados em uma grade 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="51387-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="51387-126">Da mesma forma que quando você [criou um painel de botões](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), as principais etapas que você seguirá para fazer isso são:</span><span class="sxs-lookup"><span data-stu-id="51387-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="51387-127">Pai dos objetos 3D para um objeto pai</span><span class="sxs-lookup"><span data-stu-id="51387-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="51387-128">Adicionar e configurar o componente de coleção de objetos de grade (script)</span><span class="sxs-lookup"><span data-stu-id="51387-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="51387-129">1. pai dos objetos 3D para um objeto pai</span><span class="sxs-lookup"><span data-stu-id="51387-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="51387-130">Na janela hierarquia, **crie um objeto vazio**, dê a ele um nome adequado, por exemplo, **3DObjectCollection**, e posicione-o em um local adequado, por exemplo, X = 0, Y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="51387-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="51387-131">Na janela do projeto, navegue até **ativos** > **MRTK. Tutoriais. GettingStarted** > **pré-fabricados**e, em seguida, **pai** o seguinte pré-fabricados para o **3DObjectCollection**:</span><span class="sxs-lookup"><span data-stu-id="51387-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **Parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="51387-132">Queijo</span><span class="sxs-lookup"><span data-stu-id="51387-132">Cheese</span></span>
* <span data-ttu-id="51387-133">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="51387-133">CoffeeCup</span></span>
* <span data-ttu-id="51387-134">EarthCore</span><span class="sxs-lookup"><span data-stu-id="51387-134">EarthCore</span></span>
* <span data-ttu-id="51387-135">Octa</span><span class="sxs-lookup"><span data-stu-id="51387-135">Octa</span></span>
* <span data-ttu-id="51387-136">Platão</span><span class="sxs-lookup"><span data-stu-id="51387-136">Platonic</span></span>
* <span data-ttu-id="51387-137">O módulo</span><span class="sxs-lookup"><span data-stu-id="51387-137">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="51387-139">Na janela hierarquia, **crie três cubos** como objetos filho do **3DObjectCollection** e defina a **escala** de transformação como X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="51387-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> <span data-ttu-id="51387-141">Para obter um lembrete sobre como executar as etapas listadas acima, você pode consultar o tutorial [criando a interface do usuário e configurar o kit de ferramentas de realidade misturada](mrlearning-base-ch2.md) .</span><span class="sxs-lookup"><span data-stu-id="51387-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="51387-142">Reposicione os cubos para que você possa ver cada cubo:</span><span class="sxs-lookup"><span data-stu-id="51387-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="51387-144">Na janela do projeto, navegue até **ativos** > **MixedRealityToolkit. SDK** > **StandardAssets** > **materiais** para ver os materiais fornecidos com o MRTK.</span><span class="sxs-lookup"><span data-stu-id="51387-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="51387-145">**Clique e arraste** um material adequado para a propriedade elemento 0 de **materiais** do processador de malha de cada cubo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="51387-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="51387-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="51387-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="51387-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="51387-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="51387-148">MRTK_Standard_Green:</span><span class="sxs-lookup"><span data-stu-id="51387-148">MRTK_Standard_Green:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="51387-150">2. adicionar e configurar o componente de coleção de objetos de grade (script)</span><span class="sxs-lookup"><span data-stu-id="51387-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="51387-151">Adicione um componente de **coleção de objetos de grade (script)** ao objeto 3DObjectCollection e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="51387-151">Add a **Grid Object Collection (Script)** component to the 3DObjectCollection object, and configure it as follows:</span></span>

* <span data-ttu-id="51387-152">Altere o **tipo de classificação** para ordem filho para garantir que os objetos filho sejam classificados na ordem em que você os colocou sob o objeto pai</span><span class="sxs-lookup"><span data-stu-id="51387-152">Change **Sort Type** to Child Order to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="51387-153">Em seguida, clique no botão **Atualizar coleção** para aplicar a nova configuração:</span><span class="sxs-lookup"><span data-stu-id="51387-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="51387-155">Manipulando objetos 3D</span><span class="sxs-lookup"><span data-stu-id="51387-155">Manipulating 3D objects</span></span>

<span data-ttu-id="51387-156">Nesta seção, você adicionará a capacidade de manipular todos os objetos 3D no painel criado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="51387-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="51387-157">Além disso, para os objetos pré-fabricado, você permitirá que os usuários atinjam e peguem esses objetos com mãos controladas.</span><span class="sxs-lookup"><span data-stu-id="51387-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="51387-158">Em seguida, você irá explorar alguns comportamentos de manipulação que podem ser aplicados aos seus objetos.</span><span class="sxs-lookup"><span data-stu-id="51387-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="51387-159">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="51387-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="51387-160">Adicionar o componente manipulador de manipulação (script) a todos os objetos</span><span class="sxs-lookup"><span data-stu-id="51387-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="51387-161">Adicionar o componente de proximidade de interação Near (script) aos objetos pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="51387-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="51387-162">Configurar o componente manipulador de manipulação (script)</span><span class="sxs-lookup"><span data-stu-id="51387-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51387-163">Para poder **manipular um objeto**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="51387-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="51387-164">Componente **colisor** , por exemplo, um colisor de caixa</span><span class="sxs-lookup"><span data-stu-id="51387-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="51387-165">Componente **manipulador de manipulação (script)**</span><span class="sxs-lookup"><span data-stu-id="51387-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="51387-166">Para poder **manipular** e **obter um objeto com mãos controladas**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="51387-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="51387-167">Componente **colisor** , por exemplo, um colisor de caixa</span><span class="sxs-lookup"><span data-stu-id="51387-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="51387-168">Componente **manipulador de manipulação (script)**</span><span class="sxs-lookup"><span data-stu-id="51387-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="51387-169">Componente **de captura de proximidade (script) próximo de interação**</span><span class="sxs-lookup"><span data-stu-id="51387-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="51387-170">1. Adicionar o componente manipulador de manipulação (script) a todos os objetos</span><span class="sxs-lookup"><span data-stu-id="51387-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="51387-171">Na janela hierarquia, selecione o objeto **queijo** , mantenha pressionada a tecla **Shift** e, em seguida, selecione o objeto **Cube ()** e adicione o componente **manipulador de manipulação (script)** a todos os objetos:</span><span class="sxs-lookup"><span data-stu-id="51387-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube ()** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="51387-173">Para fins deste tutorial, os colisors já foram adicionados ao pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="51387-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="51387-174">Para primitivos do Unity, como os objetos de cubo, o componente colisor é adicionado automaticamente quando o objeto é criado.</span><span class="sxs-lookup"><span data-stu-id="51387-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="51387-175">Na imagem acima, os colisors são representados pelos contornos verdes.</span><span class="sxs-lookup"><span data-stu-id="51387-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="51387-176">Para saber mais sobre os colisors, você pode visitar a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colider</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="51387-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="51387-177">2. Adicione o componente de "script" de interação Near a objetos pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="51387-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="51387-178">Na janela hierarquia, selecione o objeto **queijo** , mantenha pressionada a tecla **Shift** e, em seguida, selecione o objeto do **módulo** e adicione o componente de controle de **interação Near (script)** a todos os objetos:</span><span class="sxs-lookup"><span data-stu-id="51387-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="51387-180">3. configurar o componente manipulador de manipulação (script)</span><span class="sxs-lookup"><span data-stu-id="51387-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="51387-181">Manipulação padrão</span><span class="sxs-lookup"><span data-stu-id="51387-181">Default manipulation</span></span>

<span data-ttu-id="51387-182">Para o objeto **Cube** , deixe todas as propriedades em padrão, para experimentar o comportamento de manipulação padrão:</span><span class="sxs-lookup"><span data-stu-id="51387-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="51387-184">Para redefinir um componente para seus valores padrão, você pode selecionar o ícone de configurações do componente e selecionar redefinir.</span><span class="sxs-lookup"><span data-stu-id="51387-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="51387-185">Restringir a manipulação somente para escala</span><span class="sxs-lookup"><span data-stu-id="51387-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="51387-186">Para o objeto **Cube (1)** , altere o **tipo de manipulação de duas mãos** para dimensionar para permitir que o usuário altere o tamanho do objeto:</span><span class="sxs-lookup"><span data-stu-id="51387-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to Scale to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="51387-188">Restringir o movimento a uma distância fixa do usuário</span><span class="sxs-lookup"><span data-stu-id="51387-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="51387-189">Para o objeto **Cube (2)** , altere a **restrição no movimento** para corrigir a distância do cabeçalho para que, quando o objeto for movido, ele permaneça à mesma distância do usuário:</span><span class="sxs-lookup"><span data-stu-id="51387-189">For the **Cube (2)** object, change **Constraint On Movement** to Fix Distance From Head so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="51387-191">Manipulação de captura padrão</span><span class="sxs-lookup"><span data-stu-id="51387-191">Default grabbable manipulation</span></span>

<span data-ttu-id="51387-192">Para os objetos **queijo**, **CoffeCup**e **EarthCore** , deixe todas as propriedades em padrão para experimentar o comportamento de manipulação de captura padrão:</span><span class="sxs-lookup"><span data-stu-id="51387-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="51387-194">Remover a capacidade de manipulação distante</span><span class="sxs-lookup"><span data-stu-id="51387-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="51387-195">Para o objeto **Octa** , desmarque a caixa de seleção **permitir manipulação distante** para que o usuário possa interagir apenas com o objeto diretamente usando as mãos rastreadas:</span><span class="sxs-lookup"><span data-stu-id="51387-195">For the **Octa** object, uncheck the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="51387-197">Fazer um objeto girar em volta do seu centro</span><span class="sxs-lookup"><span data-stu-id="51387-197">Make an object rotate around its center</span></span>

<span data-ttu-id="51387-198">Para o objeto **Platão** , altere o **modo de rotação de uma mão próximo** e o **modo de rotação de uma mão** para girar sobre a central de objetos para fazê-lo quando o usuário girar o objeto com uma mão, ele gira em torno do centro do objeto:</span><span class="sxs-lookup"><span data-stu-id="51387-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to Rotate About Object Center to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a><span data-ttu-id="51387-200">Impedir movimento após o lançamento do objeto</span><span class="sxs-lookup"><span data-stu-id="51387-200">Prevent movement after object is released</span></span>

<span data-ttu-id="51387-201">Para o objeto do **módulo** , altere o **comportamento da liberação** para nada, de modo que depois que o objeto for liberado da mão do usuário, ele não continuará a ser movido:</span><span class="sxs-lookup"><span data-stu-id="51387-201">For the **TheModule** object, change **Release Behavior** to Nothing so that once the object is released from the user's hand, it doesn’t continue to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="51387-203">Para saber mais sobre o componente do manipulador de manipulação e suas propriedades associadas, você pode visitar o guia do [manipulador de manipulação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) no portal de [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="51387-203">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="51387-204">Adicionando caixas delimitadoras</span><span class="sxs-lookup"><span data-stu-id="51387-204">Adding bounding boxes</span></span>

<span data-ttu-id="51387-205">As caixas delimitadoras tornam mais fácil e mais intuitivo manipular objetos com uma mão para interação próxima e extrema, fornecendo identificadores que podem ser usados para dimensionamento e rotação.</span><span class="sxs-lookup"><span data-stu-id="51387-205">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="51387-206">Neste exemplo, você adicionará uma caixa delimitadora ao objeto EarthCore para que esse objeto agora possa interagir usando a manipulação de objeto configurada na seção anterior, bem como, dimensionada e girada usando os identificadores da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="51387-206">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51387-207">Para poder usar uma **caixa delimitadora**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="51387-207">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="51387-208">Componente **colisor** , por exemplo, um colisor de caixa</span><span class="sxs-lookup"><span data-stu-id="51387-208">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="51387-209">Componente **de caixa delimitadora (script)**</span><span class="sxs-lookup"><span data-stu-id="51387-209">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="51387-210">1. Adicionar o componente de caixa delimitadora (script) ao objeto EarthCore</span><span class="sxs-lookup"><span data-stu-id="51387-210">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="51387-211">Na janela Inspetor, selecione o objeto **EarthCore** e adicione o componente de **caixa delimitadora (script)** ao objeto EarthCore:</span><span class="sxs-lookup"><span data-stu-id="51387-211">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="51387-213">As visualizações da caixa delimitadora são criadas em tempo de execução e, portanto, não são visíveis antes de você entrar no modo de jogo.</span><span class="sxs-lookup"><span data-stu-id="51387-213">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="51387-214">2. visualize e teste a caixa delimitadora usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="51387-214">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="51387-215">Pressione o botão reproduzir para entrar no modo de jogo.</span><span class="sxs-lookup"><span data-stu-id="51387-215">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="51387-216">Em seguida, pressione e segure a barra de espaços para abrir a mão e use o mouse para interagir com a caixa delimitadora:</span><span class="sxs-lookup"><span data-stu-id="51387-216">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="51387-218">Para saber mais sobre o componente de caixa delimitadora e suas propriedades associadas, você pode visitar o guia de [caixa delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="51387-218">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="51387-219">Adicionando efeitos de toque</span><span class="sxs-lookup"><span data-stu-id="51387-219">Adding touch effects</span></span>

<span data-ttu-id="51387-220">Neste exemplo, você permitirá que os eventos sejam disparados quando você tocar em um objeto com sua mão.</span><span class="sxs-lookup"><span data-stu-id="51387-220">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="51387-221">Especificamente, você configurará o objeto Octa para reproduzir um efeito de som quando o usuário o tocar.</span><span class="sxs-lookup"><span data-stu-id="51387-221">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="51387-222">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="51387-222">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="51387-223">Adicionar um componente de fonte de áudio ao objeto</span><span class="sxs-lookup"><span data-stu-id="51387-223">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="51387-224">Adicionar o componente de interação de proximidade (script) ao objeto</span><span class="sxs-lookup"><span data-stu-id="51387-224">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="51387-225">Adicionar o componente de toque de interação à mão (script) ao objeto</span><span class="sxs-lookup"><span data-stu-id="51387-225">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="51387-226">Implementar o evento on Touch Started</span><span class="sxs-lookup"><span data-stu-id="51387-226">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="51387-227">Testar a interação de toque usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="51387-227">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51387-228">Para poder **disparar eventos de toque**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="51387-228">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="51387-229">Componente **colisor** , preferencialmente um colisor de caixa</span><span class="sxs-lookup"><span data-stu-id="51387-229">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="51387-230">Componente **de toque próximo à interação (script)**</span><span class="sxs-lookup"><span data-stu-id="51387-230">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="51387-231">Componente **de toque de interação manual (script)**</span><span class="sxs-lookup"><span data-stu-id="51387-231">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="51387-232">O componente de toque de interação manual (script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="51387-232">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="51387-233">Ele foi importado com os ativos deste tutorial e, originalmente, parte dos exemplos do MixedReality Toolkit Unity.</span><span class="sxs-lookup"><span data-stu-id="51387-233">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="51387-234">1. adicionar um componente de fonte de áudio ao objeto</span><span class="sxs-lookup"><span data-stu-id="51387-234">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="51387-235">Na janela hierarquia, selecione o objeto **Octa** , adicione um componente **fonte de áudio** ao objeto Octa e altere a **mistura espacial** para 1 para habilitar o áudio espacial:</span><span class="sxs-lookup"><span data-stu-id="51387-235">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="51387-237">2. Adicionar o componente de interação Near-toque (script) ao objeto</span><span class="sxs-lookup"><span data-stu-id="51387-237">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="51387-238">Com o objeto **Octa** ainda selecionado, adicione o componente de inclusão de **interação Near (script)** ao objeto Octa e, em seguida, clique nos botões **corrigir limites** e **corrigir centro** para atualizar as propriedades centro local e limites da interação próxima touchável (script) para corresponder ao BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="51387-238">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="51387-240">3. Adicionar o componente de toque de interação da mão (script) ao objeto</span><span class="sxs-lookup"><span data-stu-id="51387-240">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="51387-241">Com o objeto **Octa** ainda selecionado, adicione o componente de **toque de interação da mão (script)** ao objeto Octa:</span><span class="sxs-lookup"><span data-stu-id="51387-241">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="51387-243">4. implementar o evento on Touch Started</span><span class="sxs-lookup"><span data-stu-id="51387-243">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="51387-244">No componente de toque de interação à mão (script), clique no ícone de **+** pequeno para criar um novo **no evento de toque iniciado ()** .</span><span class="sxs-lookup"><span data-stu-id="51387-244">On the Hand Interaction Touch (Script) component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="51387-245">Em seguida, configure o objeto **Octa** para receber o evento e defina o **audioname. PlayOneShot** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="51387-245">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="51387-247">Navegue até **ativos** > **MixedRealityToolkit. SDK** > **StandardAssets** > materiais para ver os clipes de áudio fornecidos com o MRTK e, em seguida, atribua um clipe de áudio adequado ao campo **clipe de áudio** , por exemplo, o clipe de áudio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="51387-247">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="51387-249">Para obter um lembrete sobre como implementar eventos, consulte as instruções [gestos de acompanhamento de mão e botões](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) que podem interagir.</span><span class="sxs-lookup"><span data-stu-id="51387-249">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="51387-250">5. testar a interação de toque usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="51387-250">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="51387-251">Pressione o botão reproduzir para entrar no modo de jogo.</span><span class="sxs-lookup"><span data-stu-id="51387-251">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="51387-252">Em seguida, pressione e segure a barra de espaços para abrir a mão e usar o mouse para tocar no objeto Octa e disparar o efeito de som:</span><span class="sxs-lookup"><span data-stu-id="51387-252">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="51387-254">Como vimos ao testar a interação de toque e, conforme mostrado na imagem acima, a cor do objeto Octa pulsated enquanto ela foi tocada.</span><span class="sxs-lookup"><span data-stu-id="51387-254">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="51387-255">Esse efeito é embutido em código no componente de toque de interação manual (script) e não resultado da configuração de evento que você concluiu nas etapas acima.</span><span class="sxs-lookup"><span data-stu-id="51387-255">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="51387-256">Se você quiser desabilitar esse efeito, poderá, por exemplo, comentar ou a linha 32 ' TargetRenderer = GetComponentInChildren<Renderer>(); ', o que resultará em TargetRenderer nulo restante e a cor não Pulsating.</span><span class="sxs-lookup"><span data-stu-id="51387-256">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="51387-257">Parabéns</span><span class="sxs-lookup"><span data-stu-id="51387-257">Congratulations</span></span>

<span data-ttu-id="51387-258">Neste tutorial, você aprendeu a organizar objetos 3D em uma coleção de grade e a manipular esses objetos (dimensionamento, rotação e movimentação) usando a interação próxima (pegando diretamente com as mãos controladas) e a interação extrema (usando raios olhar ou raios de mão).</span><span class="sxs-lookup"><span data-stu-id="51387-258">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="51387-259">Você também aprendeu como colocar caixas delimitadoras em objetos 3D e aprendeu como usar e personalizar as alças nas caixas delimitadoras.</span><span class="sxs-lookup"><span data-stu-id="51387-259">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="51387-260">Por fim, você aprendeu a disparar eventos ao tocar um objeto.</span><span class="sxs-lookup"><span data-stu-id="51387-260">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="51387-261">Próxima lição: 6. explorando opções de entrada avançadas</span><span class="sxs-lookup"><span data-stu-id="51387-261">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)

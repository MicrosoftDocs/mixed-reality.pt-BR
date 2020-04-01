---
title: Tutoriais de introdução – 5. Como interagir com objetos 3D
description: Saiba mais sobre as experiências básicas de conteúdo e de usuário 3D, como organizar objetos 3D e caixas delimitadoras para manipulação básica.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 65bcef6a7c10450816d7a928302b0b266b132f0f
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362073"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="6605a-105">5. Como interagir com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="6605a-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="6605a-106">Neste tutorial, você aprenderá sobre o conteúdo básico de 3D e a experiência do usuário, como organizar objetos 3D como parte de uma coleção, caixas delimitadoras para manipulação básica, interação próxima e distante e gestos de toque e captura com acompanhamento de mão.</span><span class="sxs-lookup"><span data-stu-id="6605a-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="6605a-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6605a-107">Objectives</span></span>

* <span data-ttu-id="6605a-108">Criar um painel de objetos 3D que serão usados para os outros objetivos de aprendizado</span><span class="sxs-lookup"><span data-stu-id="6605a-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="6605a-109">Implementar caixas delimitadoras</span><span class="sxs-lookup"><span data-stu-id="6605a-109">Implement bounding boxes</span></span>
* <span data-ttu-id="6605a-110">Configurar objetos 3D para manipulação básica, como mover, girar e dimensionar</span><span class="sxs-lookup"><span data-stu-id="6605a-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="6605a-111">Explorar a interação próxima e distante</span><span class="sxs-lookup"><span data-stu-id="6605a-111">Explore near and far interaction</span></span>
* <span data-ttu-id="6605a-112">Conhecer gestos adicionais de acompanhamento de mãos, como toque e segurar</span><span class="sxs-lookup"><span data-stu-id="6605a-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="6605a-113">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="6605a-113">Importing the tutorial assets</span></span>

<span data-ttu-id="6605a-114">Baixe e importe o pacote personalizado do Unity:</span><span class="sxs-lookup"><span data-stu-id="6605a-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="6605a-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="6605a-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="6605a-116">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="6605a-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="6605a-118">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="6605a-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="6605a-119">Como desobstruir o modo de exibição de cena</span><span class="sxs-lookup"><span data-stu-id="6605a-119">Decluttering the scene view</span></span>

<span data-ttu-id="6605a-120">Para facilitar o trabalho com sua cena, defina a **visibilidade da cena** para os objetos **Cube** e **ButtonCollection** como desligada clicando no ícone de **olho** à esquerda dos objetos.</span><span class="sxs-lookup"><span data-stu-id="6605a-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="6605a-121">Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo:</span><span class="sxs-lookup"><span data-stu-id="6605a-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="6605a-123">Para saber mais sobre os controles de visibilidade da cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode acessar a documentação de <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="6605a-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="6605a-124">Como organizar objetos 3D em uma coleção</span><span class="sxs-lookup"><span data-stu-id="6605a-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="6605a-125">Nesta seção, você criará um painel de objetos 3D que será usado ao explorar várias maneiras de interagir com objetos 3D nas seções a seguir deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="6605a-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="6605a-126">Especificamente, você configurará os objetos 3D a serem posicionados em uma grade 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="6605a-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="6605a-127">Da mesma forma que quando você [criou um painel de botões](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), as principais etapas que você seguirá para fazer isso são:</span><span class="sxs-lookup"><span data-stu-id="6605a-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="6605a-128">Subordinar os objetos 3D a um objeto pai</span><span class="sxs-lookup"><span data-stu-id="6605a-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="6605a-129">Adicionar e configurar o componente de Coleção de Objetos de Grade (Script)</span><span class="sxs-lookup"><span data-stu-id="6605a-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="6605a-130">1. Subordinar os objetos 3D a um objeto pai</span><span class="sxs-lookup"><span data-stu-id="6605a-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="6605a-131">Na janela Hierarquia, **criar um objeto vazio**, dê a ele um nome adequado, por exemplo, **3DObjectCollection** e posicione-o em uma localização adequada, por exemplo, X = 0, Y = -0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="6605a-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="6605a-132">Na janela Projeto, navegue até **Ativos** > **MRTK.Tutoriais.GettingStarted** > **Pré-fabricados**, então **subordine** os seguintes pré-fabricados à **3DObjectCollection**:</span><span class="sxs-lookup"><span data-stu-id="6605a-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="6605a-133">Cheese</span><span class="sxs-lookup"><span data-stu-id="6605a-133">Cheese</span></span>
* <span data-ttu-id="6605a-134">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="6605a-134">CoffeeCup</span></span>
* <span data-ttu-id="6605a-135">EarthCore</span><span class="sxs-lookup"><span data-stu-id="6605a-135">EarthCore</span></span>
* <span data-ttu-id="6605a-136">Octa</span><span class="sxs-lookup"><span data-stu-id="6605a-136">Octa</span></span>
* <span data-ttu-id="6605a-137">Platonic</span><span class="sxs-lookup"><span data-stu-id="6605a-137">Platonic</span></span>
* <span data-ttu-id="6605a-138">TheModule</span><span class="sxs-lookup"><span data-stu-id="6605a-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="6605a-140">Na janela Hierarquia, **crie três cubos** como objetos filho do objeto **3DObjectCollection** e defina sua **Escala** de Transformação para X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="6605a-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="6605a-142">Para obter um lembrete sobre como executar as etapas listadas acima, confira o tutorial [Como criar a interface do usuário e configurar o Mixed Reality Toolkit](mrlearning-base-ch2.md).</span><span class="sxs-lookup"><span data-stu-id="6605a-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="6605a-143">Reposicione os cubos para que você possa ver cada cubo:</span><span class="sxs-lookup"><span data-stu-id="6605a-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="6605a-145">Na janela Projeto, navegue até **Ativos** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materiais** para ver os materiais fornecidos com o MRTK.</span><span class="sxs-lookup"><span data-stu-id="6605a-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="6605a-146">**Clique e arraste** um material adequado para cada propriedade de Elemento 0 de **Materiais** do Renderizador de Malha, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6605a-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="6605a-147">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="6605a-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="6605a-148">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="6605a-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="6605a-149">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="6605a-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="6605a-151">2. Adicionar e configurar o componente de Coleção de Objetos de Grade (Script)</span><span class="sxs-lookup"><span data-stu-id="6605a-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="6605a-152">Adicione um componente da **Coleção de objetos de grade (script)** ao objeto **3DObjectCollection** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6605a-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="6605a-153">Altere **Tipo de Classificação** para **Ordem Filho** para garantir que os objetos filho sejam classificados na ordem em que você os colocou sob o objeto pai</span><span class="sxs-lookup"><span data-stu-id="6605a-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="6605a-154">Em seguida, clique no botão **Atualizar Coleção** para aplicar a nova configuração:</span><span class="sxs-lookup"><span data-stu-id="6605a-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="6605a-156">Como manipular objetos 3D</span><span class="sxs-lookup"><span data-stu-id="6605a-156">Manipulating 3D objects</span></span>

<span data-ttu-id="6605a-157">Nesta seção, você adicionará a capacidade de manipular todos os objetos 3D no painel criado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="6605a-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="6605a-158">Além disso, para os objetos pré-fabricado, você permitirá que os usuários atinjam e peguem esses objetos com mãos controladas.</span><span class="sxs-lookup"><span data-stu-id="6605a-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="6605a-159">Em seguida, você vai explorar alguns comportamentos de manipulação que podem ser aplicados aos seus objetos.</span><span class="sxs-lookup"><span data-stu-id="6605a-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="6605a-160">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="6605a-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="6605a-161">Adicionar o componente Manipulador de Manipulação (Script) a todos os objetos</span><span class="sxs-lookup"><span data-stu-id="6605a-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="6605a-162">Adicionar o componente de Capturável de Interação Próxima (Script) aos objetos pré-fabricados</span><span class="sxs-lookup"><span data-stu-id="6605a-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="6605a-163">Configurar o componente Manipulador de Manipulação (Script)</span><span class="sxs-lookup"><span data-stu-id="6605a-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6605a-164">Para poder **manipular um objeto**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="6605a-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="6605a-165">Componente **Colisor**, por exemplo, um Colisor de Caixa</span><span class="sxs-lookup"><span data-stu-id="6605a-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="6605a-166">Componente **Manipulador de Manipulação (Script)**</span><span class="sxs-lookup"><span data-stu-id="6605a-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="6605a-167">Para poder **manipular** e **capturar um objeto com as mãos acompanhadas**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="6605a-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="6605a-168">Componente **Colisor**, por exemplo, um Colisor de Caixa</span><span class="sxs-lookup"><span data-stu-id="6605a-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="6605a-169">Componente **Manipulador de Manipulação (Script)**</span><span class="sxs-lookup"><span data-stu-id="6605a-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="6605a-170">Componente **Capturável de Interação Próxima (Script)**</span><span class="sxs-lookup"><span data-stu-id="6605a-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="6605a-171">1. Adicionar o componente Manipulador de Manipulação (Script) a todos os objetos</span><span class="sxs-lookup"><span data-stu-id="6605a-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="6605a-172">Na janela Hierarquia, selecione o objeto **Cheese**, mantenha pressionada a tecla **Shift** e, em seguida, selecione o objeto **Cube () 2** e adicione o componente **Manipulador de Manipulação (Script)** a todos os objetos:</span><span class="sxs-lookup"><span data-stu-id="6605a-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="6605a-174">Para os fins deste tutorial, os colisores já foram adicionados aos pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="6605a-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="6605a-175">Para primitivos do Unity, como os objetos Cube, o componente Colisor é adicionado automaticamente quando o objeto é criado.</span><span class="sxs-lookup"><span data-stu-id="6605a-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="6605a-176">Na imagem acima, os colisores são representados pelos contornos verdes.</span><span class="sxs-lookup"><span data-stu-id="6605a-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="6605a-177">Para saber mais sobre os colisores, acesse a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisor</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="6605a-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="6605a-178">2. Adicionar o componente de Capturável de Interação Próxima (Script) aos objetos pré-fabricados</span><span class="sxs-lookup"><span data-stu-id="6605a-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="6605a-179">Na janela Hierarquia, selecione o objeto **Cheese**, mantenha pressionada a tecla **Shift** e, em seguida, selecione o objeto **TheModule** e adicione o componente **Capturável de Interação Próxima (Script)** a todos os objetos:</span><span class="sxs-lookup"><span data-stu-id="6605a-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="6605a-181">3. Configurar o componente Manipulador de Manipulação (Script)</span><span class="sxs-lookup"><span data-stu-id="6605a-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="6605a-182">Manipulação padrão</span><span class="sxs-lookup"><span data-stu-id="6605a-182">Default manipulation</span></span>

<span data-ttu-id="6605a-183">Para o objeto **Cube**, deixe todas as propriedades em padrão para obter o comportamento de manipulação padrão:</span><span class="sxs-lookup"><span data-stu-id="6605a-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="6605a-185">Para redefinir um componente para seus valores padrão, você pode selecionar o ícone de Configurações do componente e selecionar Redefinir.</span><span class="sxs-lookup"><span data-stu-id="6605a-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="6605a-186">Restringir a manipulação somente para escala</span><span class="sxs-lookup"><span data-stu-id="6605a-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="6605a-187">Para o objeto **Cube (1)** , altere **Tipo de Manipulação de Duas Mãos** para **Escala** para permitir apenas que o usuário altere o tamanho do objeto:</span><span class="sxs-lookup"><span data-stu-id="6605a-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="6605a-189">Restringir o movimento a uma distância fixa do usuário</span><span class="sxs-lookup"><span data-stu-id="6605a-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="6605a-190">Para o objeto **Cubo (2)** , altere **Restrição no Movimento** para **Distância Fixa da Cabeça** de modo que, quando o objeto for movido, ele permaneça à mesma distância do usuário:</span><span class="sxs-lookup"><span data-stu-id="6605a-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="6605a-192">Manipulação capturável padrão</span><span class="sxs-lookup"><span data-stu-id="6605a-192">Default grabbable manipulation</span></span>

<span data-ttu-id="6605a-193">Para os objetos **Cheese**, **CoffeCup** e **EarthCore**, deixe todas as propriedades conforme o padrão para obter o comportamento de manipulação capturável padrão:</span><span class="sxs-lookup"><span data-stu-id="6605a-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="6605a-195">Remover a capacidade de manipulação distante</span><span class="sxs-lookup"><span data-stu-id="6605a-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="6605a-196">Para o objeto **Octa**, desmarque a caixa de seleção **Permitir Manipulação Distante** para que o usuário possa interagir apenas com o objeto diretamente usando as mãos acompanhadas:</span><span class="sxs-lookup"><span data-stu-id="6605a-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="6605a-198">Fazer um objeto girar em torno do seu centro</span><span class="sxs-lookup"><span data-stu-id="6605a-198">Make an object rotate around its center</span></span>

<span data-ttu-id="6605a-199">Para o objeto **Platonic**, altere **Modo de Rotação de Uma Mão Próxima** e **Modo de Rotação de Uma Mão Distante** para **Girar Sobre o Centro do Objeto** para que, quando o usuário gira o objeto com uma mão, ele gire em torno do centro do objeto:</span><span class="sxs-lookup"><span data-stu-id="6605a-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="6605a-201">Manter movimento após soltar o objeto</span><span class="sxs-lookup"><span data-stu-id="6605a-201">Keep movement after object is released</span></span>

<span data-ttu-id="6605a-202">Para o objeto **TheModule**, adicione um componente **Rigidbody** para habilitar a física e desmarque a caixa de seleção **Usar Gravidade** para que o objeto não seja afetado pela gravidade:</span><span class="sxs-lookup"><span data-stu-id="6605a-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="6605a-204">De volta ao componente Manipulador de Manipulação (Script), verifique se o **Comportamento ao Liberar** está definido como **Manter a Velocidade** e **Manter a Velocidade Angular** para que, depois que o objeto for solto da mão do usuário, ele continue a se mover:</span><span class="sxs-lookup"><span data-stu-id="6605a-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="6605a-206">Para saber mais sobre o componente do Manipulador de Manipulação e suas propriedades associadas, você pode acessar o guia do [Manipulador de Manipulação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="6605a-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="6605a-207">Como adicionar caixas delimitadoras</span><span class="sxs-lookup"><span data-stu-id="6605a-207">Adding bounding boxes</span></span>

<span data-ttu-id="6605a-208">As caixas delimitadoras tornam mais fácil e mais intuitivo manipular objetos com uma mão para interação próxima e distante fornecendo alças que podem ser usadas para dimensionamento e rotação.</span><span class="sxs-lookup"><span data-stu-id="6605a-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="6605a-209">Neste exemplo, você adicionará uma caixa delimitadora ao objeto EarthCore para que esse objeto agora possa interagir usando a manipulação de objeto configurada na seção anterior, bem como, dimensionado e girado usando os identificadores da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="6605a-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6605a-210">Para poder usar uma **caixa delimitadora**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="6605a-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="6605a-211">Componente **Colisor**, por exemplo, um Colisor de Caixa</span><span class="sxs-lookup"><span data-stu-id="6605a-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="6605a-212">Componente **Caixa Delimitadora (Script)**</span><span class="sxs-lookup"><span data-stu-id="6605a-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="6605a-213">1. Adicionar o componente de Caixa Delimitadora (Script) ao objeto EarthCore</span><span class="sxs-lookup"><span data-stu-id="6605a-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="6605a-214">Na janela Inspetor, selecione o objeto **EarthCore** e adicione o componente **Caixa Delimitadora (Script)** ao objeto EarthCore:</span><span class="sxs-lookup"><span data-stu-id="6605a-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="6605a-216">As visualizações da Caixa Delimitadora são criadas em tempo de execução e, portanto, não são visíveis antes de você entrar no modo de Jogo.</span><span class="sxs-lookup"><span data-stu-id="6605a-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="6605a-217">2. Visualizar e testar a caixa delimitadora usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="6605a-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="6605a-218">Pressione o botão Reproduzir para entrar no modo de Jogo.</span><span class="sxs-lookup"><span data-stu-id="6605a-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="6605a-219">Em seguida, pressione e segure a barra de espaços para abrir a mão e use o mouse para interagir com a caixa delimitadora:</span><span class="sxs-lookup"><span data-stu-id="6605a-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="6605a-221">Para saber mais sobre o componente de Caixa Delimitadora e suas propriedades associadas, acesse o guia da [Caixa Delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="6605a-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="6605a-222">Como adicionar efeitos de toque</span><span class="sxs-lookup"><span data-stu-id="6605a-222">Adding touch effects</span></span>

<span data-ttu-id="6605a-223">Neste exemplo, você permitirá que os eventos sejam disparados quando você tocar em um objeto com sua mão.</span><span class="sxs-lookup"><span data-stu-id="6605a-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="6605a-224">Especificamente, você configurará o objeto Octa para reproduzir um efeito de som quando o usuário o tocar.</span><span class="sxs-lookup"><span data-stu-id="6605a-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="6605a-225">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="6605a-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="6605a-226">Adicionar um componente de Fonte de Áudio ao objeto</span><span class="sxs-lookup"><span data-stu-id="6605a-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="6605a-227">Adicionar o componente Tocável de Interação Próxima (Script) ao objeto</span><span class="sxs-lookup"><span data-stu-id="6605a-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="6605a-228">Adicionar o componente de Toque de Interação Manual (Script) ao objeto</span><span class="sxs-lookup"><span data-stu-id="6605a-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="6605a-229">Implementar o evento No Toque Iniciado</span><span class="sxs-lookup"><span data-stu-id="6605a-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="6605a-230">Testar a interação de toque usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="6605a-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6605a-231">Para poder **disparar eventos de toque**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="6605a-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="6605a-232">Componente **Colisor**, preferencialmente um Colisor de Caixa</span><span class="sxs-lookup"><span data-stu-id="6605a-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="6605a-233">Componente **Tocável de Interação Próxima (Script)**</span><span class="sxs-lookup"><span data-stu-id="6605a-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="6605a-234">Componente **Toque de Interação da Mão (Script)**</span><span class="sxs-lookup"><span data-stu-id="6605a-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="6605a-235">O componente de Toque de Interação da Mão (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="6605a-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="6605a-236">Ele foi importado com os ativos deste tutorial e, originalmente, faz parte dos exemplos do MixedReality Toolkit do Unity.</span><span class="sxs-lookup"><span data-stu-id="6605a-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="6605a-237">1. Adicionar um componente de Fonte de Áudio ao objeto</span><span class="sxs-lookup"><span data-stu-id="6605a-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="6605a-238">Na janela Hierarquia, selecione o objeto **Octa**, adicione um componente **Fonte de Áudio** ao objeto Octa e, em seguida, altere **Mistura Espacial** para 1 para habilitar o áudio espacial:</span><span class="sxs-lookup"><span data-stu-id="6605a-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="6605a-240">2. Adicionar o componente Tocável de Interação Próxima (Script) ao objeto</span><span class="sxs-lookup"><span data-stu-id="6605a-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="6605a-241">Com o objeto **Octa** ainda selecionado, adicione o componente **Tocável de Interação Próxima (Script)** ao objeto Octa e clique nos botões **Corrigir Limites** e **Corrigir Centro** para atualizar as propriedades Limites e Centro Local do Tocável de Interação Próxima (Script) para que correspondam ao BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="6605a-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="6605a-243">3. Adicionar o componente de Toque de Interação Manual (Script) ao objeto</span><span class="sxs-lookup"><span data-stu-id="6605a-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="6605a-244">Com o objeto **Octa** ainda selecionado, adicione o componente **Toque de Interação da Mão (Script)** ao objeto Octa:</span><span class="sxs-lookup"><span data-stu-id="6605a-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="6605a-246">4. Implementar o evento No Toque Iniciado</span><span class="sxs-lookup"><span data-stu-id="6605a-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="6605a-247">No componente **Toque de Interação da Mão (Script)** , clique no ícone **+** pequeno para criar um evento **No Toque Iniciado ()** .</span><span class="sxs-lookup"><span data-stu-id="6605a-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="6605a-248">Em seguida, configure o objeto **Octa** para receber o evento e defina **AudioSource.PlayOneShot** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="6605a-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="6605a-250">Navegue até **Ativos** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Áudio** para ver os clipes de áudio fornecidos com o MRTK e, em seguida, atribua um clipe de áudio adequado ao campo **Clipe de Áudio**, por exemplo, o clipe de áudio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="6605a-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio** to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="6605a-252">Para obter um lembrete sobre como implementar eventos, você pode consultar as instruções de [Gestos de acompanhamento da mão e botões interativos](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="6605a-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="6605a-253">5. Testar a interação de toque usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="6605a-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="6605a-254">Pressione o botão Reproduzir para entrar no modo de Jogo.</span><span class="sxs-lookup"><span data-stu-id="6605a-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="6605a-255">Em seguida, pressione e segure a barra de espaços para abrir a mão e usar o mouse para tocar no objeto Octa e disparar o efeito de som:</span><span class="sxs-lookup"><span data-stu-id="6605a-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="6605a-257">Como vimos ao testar a interação de toque e, conforme mostrado na imagem acima, a cor do objeto Octa pulsou enquanto ele foi tocado.</span><span class="sxs-lookup"><span data-stu-id="6605a-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="6605a-258">Esse efeito é embutido em código no componente de Toque de Interação Manual (Script) e não o resultado da configuração de evento que você concluiu nas etapas acima.</span><span class="sxs-lookup"><span data-stu-id="6605a-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="6605a-259">Se você quiser desabilitar esse efeito, poderá, por exemplo, comentar ou a linha 32 'TargetRenderer = GetComponentInChildren<Renderer>();', o que resultará em TargetRenderer permanecer nulo e a cor não pulsar.</span><span class="sxs-lookup"><span data-stu-id="6605a-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6605a-260">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6605a-260">Congratulations</span></span>

<span data-ttu-id="6605a-261">Neste tutorial, você aprendeu a organizar esses objetos em uma coleção de grades e manipulá-los (dimensionamento, rotação e movimentação) usando a interação próxima (segurar com as mãos rastreadas) e a interação distante (usando os raios de foco ou os raios de mãos).</span><span class="sxs-lookup"><span data-stu-id="6605a-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="6605a-262">Você também aprendeu a colocar caixas delimitadoras em torno de objetos 3D e usar e personalizar as alças nas caixas delimitadoras.</span><span class="sxs-lookup"><span data-stu-id="6605a-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="6605a-263">Por fim, você aprendeu a disparar eventos ao tocar um objeto.</span><span class="sxs-lookup"><span data-stu-id="6605a-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="6605a-264">Próxima lição: 6. Explorar as opções avançadas de entrada</span><span class="sxs-lookup"><span data-stu-id="6605a-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)

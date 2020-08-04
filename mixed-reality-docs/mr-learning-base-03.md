---
title: Tutoriais de introdução – 3. Como configurar os perfis do MRTK
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d3381241bb1418fb0e1fb7e5d29d552a533faa32
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376638"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="b3aff-105">3. Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="b3aff-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="b3aff-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b3aff-106">Overview</span></span>

<span data-ttu-id="b3aff-107">Neste tutorial, você aprenderá a personalizar e configurar os perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b3aff-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="b3aff-108">Este exemplo específico mostrará como ocultar a malha de reconhecimento espacial alterando as configurações do Observador de Malha Espacial.</span><span class="sxs-lookup"><span data-stu-id="b3aff-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="b3aff-109">No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b3aff-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="b3aff-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b3aff-110">Objectives</span></span>

* <span data-ttu-id="b3aff-111">Saiba como personalizar e configurar perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="b3aff-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="b3aff-112">Ocultar a malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="b3aff-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="b3aff-113">Como alterar a opção de exibição de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="b3aff-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="b3aff-114">As principais etapas que você seguirá para ocultar a malha de reconhecimento espacial são:</span><span class="sxs-lookup"><span data-stu-id="b3aff-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="b3aff-115">Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="b3aff-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="b3aff-116">Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="b3aff-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="b3aff-117">Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="b3aff-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="b3aff-118">Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="b3aff-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="b3aff-119">Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="b3aff-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="b3aff-120">Por padrão, os perfis do MRTK não são editáveis.</span><span class="sxs-lookup"><span data-stu-id="b3aff-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="b3aff-121">Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados.</span><span class="sxs-lookup"><span data-stu-id="b3aff-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="b3aff-122">Há várias camadas aninhadas de perfis.</span><span class="sxs-lookup"><span data-stu-id="b3aff-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="b3aff-123">Portanto, é comum clonar e editar vários perfis ao definir uma ou mais configurações.</span><span class="sxs-lookup"><span data-stu-id="b3aff-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="b3aff-124">1. Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="b3aff-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="b3aff-125">O perfil de configuração é o perfil de nível superior.</span><span class="sxs-lookup"><span data-stu-id="b3aff-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="b3aff-126">Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.</span><span class="sxs-lookup"><span data-stu-id="b3aff-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="b3aff-127">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, altere o Perfil de Configuração do **MixedRealityToolkit** para o **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="b3aff-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="b3aff-129">Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="b3aff-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="b3aff-131">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_HoloLens2ConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="b3aff-131">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="b3aff-133">Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:</span><span class="sxs-lookup"><span data-stu-id="b3aff-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="b3aff-135">No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.</span><span class="sxs-lookup"><span data-stu-id="b3aff-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="b3aff-136">Lembre-se de salvar seu trabalho ao longo dos tutoriais.</span><span class="sxs-lookup"><span data-stu-id="b3aff-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="b3aff-137">2. Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="b3aff-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="b3aff-138">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:</span><span class="sxs-lookup"><span data-stu-id="b3aff-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="b3aff-140">3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="b3aff-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="b3aff-141">Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="b3aff-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="b3aff-143">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="b3aff-143">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="b3aff-145">O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:</span><span class="sxs-lookup"><span data-stu-id="b3aff-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="b3aff-147">4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="b3aff-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="b3aff-148">Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality** e clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="b3aff-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="b3aff-150">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="b3aff-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="b3aff-152">O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:</span><span class="sxs-lookup"><span data-stu-id="b3aff-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="b3aff-154">5. Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="b3aff-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="b3aff-155">Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:</span><span class="sxs-lookup"><span data-stu-id="b3aff-155">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="b3aff-157">Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional.</span><span class="sxs-lookup"><span data-stu-id="b3aff-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="b3aff-158">Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="b3aff-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="b3aff-159">Você acabou de aprender como modificar uma configuração do perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b3aff-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="b3aff-160">Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão.</span><span class="sxs-lookup"><span data-stu-id="b3aff-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="b3aff-161">Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="b3aff-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="b3aff-162">Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="b3aff-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="b3aff-163">Parabéns</span><span class="sxs-lookup"><span data-stu-id="b3aff-163">Congratulations</span></span>

<span data-ttu-id="b3aff-164">Neste tutorial, você aprendeu a clonar, personalizar e definir uma configurações e perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b3aff-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

[<span data-ttu-id="b3aff-165">Próximo tutorial: 4. Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="b3aff-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)

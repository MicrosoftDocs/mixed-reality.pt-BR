---
title: Tutoriais de introdução – 3. Criar a interface do usuário e configurar o Mixed Reality Toolkit
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376133"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="e5d51-105">3. Criar a interface do usuário e configurar o Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="e5d51-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="e5d51-106">No tutorial anterior, você aprendeu sobre algumas das funcionalidades que o MRTK (Mixed Reality Toolkit) tem a oferecer, iniciando seu primeiro aplicativo para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e5d51-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="e5d51-107">Neste tutorial, você aprenderá como criar e organizar os botões, juntamente com os painéis de texto de interface do usuário e usar a interação padrão (toque) para interagir com cada botão.</span><span class="sxs-lookup"><span data-stu-id="e5d51-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="e5d51-108">Você também explorará a adição de ações e efeitos simples, como alterar o tamanho, o som e a cor de objetos.</span><span class="sxs-lookup"><span data-stu-id="e5d51-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="e5d51-109">Este módulo apresenta os conceitos básicos sobre como modificar perfis do MRTK, começando com a desativação da visualização da malha de [mapeamento espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e5d51-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="e5d51-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e5d51-110">Objectives</span></span>

* <span data-ttu-id="e5d51-111">Personalizar e configurar perfis do Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="e5d51-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="e5d51-112">Interagir com hologramas usando os botões e elementos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="e5d51-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="e5d51-113">Interações e entrada de acompanhamento de mão básicas</span><span class="sxs-lookup"><span data-stu-id="e5d51-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="e5d51-114">Como configurar os perfis do Mixed Reality Toolkit (alterar a opção de exibição de reconhecimento espacial)</span><span class="sxs-lookup"><span data-stu-id="e5d51-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="e5d51-115">Nesta seção, você aprenderá a personalizar e configurar os perfis do MRTK padrão.</span><span class="sxs-lookup"><span data-stu-id="e5d51-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="e5d51-116">Este exemplo específico mostrará como ocultar a malha de reconhecimento espacial alterando as configurações do Observador de Malha Espacial.</span><span class="sxs-lookup"><span data-stu-id="e5d51-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="e5d51-117">No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e5d51-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="e5d51-118">As principais etapas que você seguirá para ocultar a malha de reconhecimento espacial são:</span><span class="sxs-lookup"><span data-stu-id="e5d51-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="e5d51-119">Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="e5d51-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="e5d51-120">Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="e5d51-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="e5d51-121">Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="e5d51-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="e5d51-122">Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="e5d51-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="e5d51-123">Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="e5d51-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="e5d51-124">Por padrão, os perfis do MRTK não são editáveis.</span><span class="sxs-lookup"><span data-stu-id="e5d51-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="e5d51-125">Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados.</span><span class="sxs-lookup"><span data-stu-id="e5d51-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="e5d51-126">Há várias camadas aninhadas de perfis.</span><span class="sxs-lookup"><span data-stu-id="e5d51-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="e5d51-127">Portanto, é comum clonar e editar vários perfis ao definir uma ou mais configurações.</span><span class="sxs-lookup"><span data-stu-id="e5d51-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="e5d51-128">1. Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="e5d51-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="e5d51-129">O perfil de configuração é o perfil de nível superior.</span><span class="sxs-lookup"><span data-stu-id="e5d51-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="e5d51-130">Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.</span><span class="sxs-lookup"><span data-stu-id="e5d51-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="e5d51-131">Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, altere o **Perfil de Configuração** do Mixed Reality Toolkit na janela Inspetor para **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="e5d51-133">Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="e5d51-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="e5d51-135">Na janela Clonar Perfil, clique no botão **Clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="e5d51-137">Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:</span><span class="sxs-lookup"><span data-stu-id="e5d51-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="e5d51-139">No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.</span><span class="sxs-lookup"><span data-stu-id="e5d51-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="e5d51-140">Lembre-se de salvar seu trabalho em todo o tutorial.</span><span class="sxs-lookup"><span data-stu-id="e5d51-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="e5d51-141">2. Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="e5d51-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="e5d51-142">Com o objeto **MixedRealityToolkit** ainda selecionado na janela Hierarquia, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="e5d51-144">3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="e5d51-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="e5d51-145">Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="e5d51-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="e5d51-147">Na janela Clonar Perfil, clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="e5d51-149">O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:</span><span class="sxs-lookup"><span data-stu-id="e5d51-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="e5d51-151">4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="e5d51-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="e5d51-152">Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality** e clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="e5d51-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="e5d51-154">Na janela Clonar Perfil, clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="e5d51-156">O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:</span><span class="sxs-lookup"><span data-stu-id="e5d51-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="e5d51-158">5. Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="e5d51-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="e5d51-159">Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:</span><span class="sxs-lookup"><span data-stu-id="e5d51-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="e5d51-161">Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional.</span><span class="sxs-lookup"><span data-stu-id="e5d51-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="e5d51-162">Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="e5d51-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="e5d51-163">Você acabou de aprender como modificar uma configuração do perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e5d51-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="e5d51-164">Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão.</span><span class="sxs-lookup"><span data-stu-id="e5d51-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="e5d51-165">Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="e5d51-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="e5d51-166">Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode visitar o [Guia de configuração do perfil do Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e5d51-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="e5d51-167">Botões interativos e gestos de acompanhamento da mão</span><span class="sxs-lookup"><span data-stu-id="e5d51-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="e5d51-168">Nesta seção, você aprenderá a usar o acompanhamento de mão para pressionar um botão e disparar eventos para provocar uma ação quando o botão for pressionado.</span><span class="sxs-lookup"><span data-stu-id="e5d51-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="e5d51-169">Este exemplo específico mostrará como alterar a cor de um cubo quando o botão for pressionado e alterá-la de volta para a cor original quando o botão for liberado.</span><span class="sxs-lookup"><span data-stu-id="e5d51-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="e5d51-170">No entanto, você pode seguir esses mesmos princípios para criar outros eventos.</span><span class="sxs-lookup"><span data-stu-id="e5d51-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="e5d51-171">As principais etapas que você seguirá para alterar a cor do cubo são:</span><span class="sxs-lookup"><span data-stu-id="e5d51-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="e5d51-172">Adicionar um botão pressionável pré-fabricado à cena</span><span class="sxs-lookup"><span data-stu-id="e5d51-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="e5d51-173">Adicione um cubo à cena</span><span class="sxs-lookup"><span data-stu-id="e5d51-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="e5d51-174">Configurar o tipo de evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="e5d51-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="e5d51-175">Configurar o cubo para receber o evento On Press</span><span class="sxs-lookup"><span data-stu-id="e5d51-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="e5d51-176">Definir a ação a ser disparada pelo evento On Press</span><span class="sxs-lookup"><span data-stu-id="e5d51-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="e5d51-177">Configurar o cubo para receber o evento Ao Liberar</span><span class="sxs-lookup"><span data-stu-id="e5d51-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="e5d51-178">Definir a ação a ser disparada pelo evento Ao Liberar</span><span class="sxs-lookup"><span data-stu-id="e5d51-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="e5d51-179">Testar o botão usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="e5d51-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="e5d51-180">1. Adicionar um botão pressionável pré-fabricado à cena</span><span class="sxs-lookup"><span data-stu-id="e5d51-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="e5d51-181">Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um GameObject pré-configurado armazenado como um Ativo Unitário e pode ser reutilizado em todo o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e5d51-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="e5d51-182">Na **janela Projeto**, pesquise **PressableButtonHoloLens2** para localizar o pré-fabricado que será usado para este exemplo:</span><span class="sxs-lookup"><span data-stu-id="e5d51-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="e5d51-184">No resultado de **Pesquisar**, selecione o pré-fabricado **PressableButtonHoloLens2** e **arraste-o** para a janela **Hierarquia** para adicioná-la à sua cena:</span><span class="sxs-lookup"><span data-stu-id="e5d51-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="e5d51-186">Para exibir sua cena conforme mostrado na imagem abaixo, clique duas vezes no objeto PressableButtonHoloLens2 na janela Hierarquia para colocá-lo em foco e, em seguida, use o <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Gizmo de Cena</a>, localizado no canto superior direito da janela Cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço.</span><span class="sxs-lookup"><span data-stu-id="e5d51-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="e5d51-187">Com o objeto **PressableButtonHoloLens2** ainda selecionado, na janela **Inspetor**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="e5d51-188">Altere sua **Posição** de Transformação de modo que ela esteja posicionada na frente da câmera, que está posicionada na origem, por exemplo, x = 0, y = 0 e z = 0,5</span><span class="sxs-lookup"><span data-stu-id="e5d51-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="e5d51-190">Em geral, 1 unidade de posição no Unity é aproximadamente equivalente a 1 metro no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="e5d51-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="e5d51-191">Porém, há exceções, por exemplo, quando objetos são filhos de objetos dimensionados.</span><span class="sxs-lookup"><span data-stu-id="e5d51-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="e5d51-192">2. Adicione um cubo à cena</span><span class="sxs-lookup"><span data-stu-id="e5d51-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="e5d51-193">Clique com o botão direito do mouse em um ponto vazio dentro da janela Hierarquia e selecione **Objeto 3D** > **Cubo** para adicionar um cubo à sua cena:</span><span class="sxs-lookup"><span data-stu-id="e5d51-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="e5d51-195">Com o objeto **Cubo** ainda selecionado, na janela **Inspetor**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="e5d51-196">Altere sua **Posição** de Transformação para que fique perto do botão pressionável, mas não se sobreponha a ela, por exemplo, x = 0, y = 0,04 e z = 0,5</span><span class="sxs-lookup"><span data-stu-id="e5d51-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="e5d51-197">Altere sua **Escala** de Transformação para um tamanho adequado, por exemplo, x = 0,02, y = 0,02 e z = 0,02</span><span class="sxs-lookup"><span data-stu-id="e5d51-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="e5d51-199">3. Configurar o tipo de evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="e5d51-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="e5d51-200">Na janela Hierarquia, selecione o objeto **PressableButtonHoloLens2** e, em seguida, na janela **Inspetor**, **menu de hambúrguer**, selecione **Recolher Todos os Componentes** para obter uma visão geral de todos os componentes neste objeto:</span><span class="sxs-lookup"><span data-stu-id="e5d51-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="e5d51-202">Expanda o componente **Item Passível de Interação (Script)** e, em seguida, localize e expanda a seção **Eventos** > **Receptores**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="e5d51-204">Clique no botão **Adicionar Evento** para criar um receptor de evento do Tipo de Receptor de Evento **InteractableOnPressReceiver**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="e5d51-206">O Tipo de Receptor de Evento chamado InteractableOnPressReceiver permite que o botão responda a um evento pressionado quando uma mão acompanhada pressiona o botão.</span><span class="sxs-lookup"><span data-stu-id="e5d51-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="e5d51-207">Para o receptor de eventos que acaba de ser criado, altere **Filtro de Interação** para **Próximo e Distante**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="e5d51-209">4. Configurar o cubo para receber o evento On Press</span><span class="sxs-lookup"><span data-stu-id="e5d51-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="e5d51-210">Na janela Hierarquia, **clique e arraste** o **Cubo** para o campo **Propriedades do Evento** para o evento **On Press ()**  para atribuir o cubo como um destinatário do evento On Press ():</span><span class="sxs-lookup"><span data-stu-id="e5d51-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="e5d51-212">5. Definir a ação a ser disparada pelo evento On Press</span><span class="sxs-lookup"><span data-stu-id="e5d51-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="e5d51-213">Clique no menu suspenso de ação, atribuído no momento a **Nenhuma Função**, e selecione **MeshRenderer** > **Material de material** para definir a propriedade de material do Cubo a ser alterada quando o evento On Press () for disparado:</span><span class="sxs-lookup"><span data-stu-id="e5d51-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="e5d51-215">Clique no ícone de **círculo** pequeno ao lado do campo material, atualmente preenchido com **Nenhum (Material)** , para abrir a janela Selecionar Material:</span><span class="sxs-lookup"><span data-stu-id="e5d51-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="e5d51-217">Na janela Selecionar Material, **pesquise** **MRTK_Standard** e selecione um material adequado, por exemplo, **MRTK_Standard_Cyan** para que a cor do Cubo seja alterada para ciano quando o botão for pressionado:</span><span class="sxs-lookup"><span data-stu-id="e5d51-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="e5d51-219">6. Configurar o cubo para receber o evento Ao Liberar</span><span class="sxs-lookup"><span data-stu-id="e5d51-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="e5d51-220">**Repita** a Etapa 4 para o evento Ao Liberar para atribuir o **Cubo** como um receptor do evento **Ao Liberar ()** .</span><span class="sxs-lookup"><span data-stu-id="e5d51-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="e5d51-221">7. Definir a ação a ser disparada pelo evento Ao Liberar</span><span class="sxs-lookup"><span data-stu-id="e5d51-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="e5d51-222">**Repita** a Etapa 5 para o evento Ao Liberar, mas escolha o material **MRTK_Standard_LightGray** para que a cor do Cubo retorne à cor cinza-claro original quando o botão for liberado:</span><span class="sxs-lookup"><span data-stu-id="e5d51-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="e5d51-224">8. Testar o botão usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="e5d51-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="e5d51-225">Pressione o botão **Reproduzir** para entrar no modo de jogo e use a simulação de entrada no editor para testar seu botão recentemente configurado.</span><span class="sxs-lookup"><span data-stu-id="e5d51-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="e5d51-226">Botão não pressionado (barra de espaços + roda de rolagem do mouse para trás):</span><span class="sxs-lookup"><span data-stu-id="e5d51-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="e5d51-228">Botão pressionado (barra de espaços + roda de rolagem do mouse para frente):</span><span class="sxs-lookup"><span data-stu-id="e5d51-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="e5d51-230">Para saber como usar a simulação de entrada no editor, você pode consultar o guia [Como usar a simulação de entrada de mão no editor para testar uma cena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) no [Portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e5d51-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="e5d51-231">Como criar um painel de botões usando a coleção de objetos de grade do MRTK</span><span class="sxs-lookup"><span data-stu-id="e5d51-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="e5d51-232">Nesta seção, você aprenderá como alinhar automaticamente vários botões em uma interface do usuário nítida usando a ferramenta Coleção de Objetos de Grade do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e5d51-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="e5d51-233">Este exemplo específico mostrará como criar um painel com cinco botões alinhados horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="e5d51-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="e5d51-234">No entanto, você pode seguir esses mesmos princípios para criar outros layouts.</span><span class="sxs-lookup"><span data-stu-id="e5d51-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="e5d51-235">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="e5d51-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e5d51-236">Subordine os objetos de botão a um objeto pai</span><span class="sxs-lookup"><span data-stu-id="e5d51-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="e5d51-237">Adicionar e configurar o componente de Coleção de Objetos de Grade (Script)</span><span class="sxs-lookup"><span data-stu-id="e5d51-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="e5d51-238">Testar os botões usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="e5d51-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="e5d51-239">1. Subordine os objetos de botão a um objeto pai</span><span class="sxs-lookup"><span data-stu-id="e5d51-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="e5d51-240">Clique com o botão direito do mouse em um ponto vazio dentro da janela Hierarquia e selecione **Criar Vazio**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="e5d51-242">Clique com o botão direito do mouse no objeto recém-criado, selecione **Renomear** e dê a ele um nome adequado, por exemplo, **ButtonCollection**:</span><span class="sxs-lookup"><span data-stu-id="e5d51-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="e5d51-244">Selecione o objeto **PressableButtonHoloLens2** e **arraste**-o para a parte superior do objeto **ButtonCollection** para torná-lo um filho do objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="e5d51-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="e5d51-246">Clique com o botão direito do mouse no objeto **PressableButtonHoloLens2** e selecione **Duplicar** para criar uma cópia dele:</span><span class="sxs-lookup"><span data-stu-id="e5d51-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="e5d51-248">**Repita** esta etapa quatro vezes até que você tenha um total de cinco objetos PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="e5d51-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="e5d51-249">2. Adicionar e configurar o componente de Coleção de Objetos de Grade (Script)</span><span class="sxs-lookup"><span data-stu-id="e5d51-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="e5d51-250">Com o objeto ButtonCollection selecionado na janela Hierarquia, na janela Inspetor, clique no botão **Adicionar Componente**. Em seguida, pesquise e selecione **Coleção de Objetos de Grade** para adicionar um componente Coleção de Objetos de Grade (Script) ao objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="e5d51-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="e5d51-252">Configure a Coleção de Objetos de Grade (Script) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e5d51-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="e5d51-253">Altere **Número de Linhas** para 1 para alinhar todos os botões em uma só linha</span><span class="sxs-lookup"><span data-stu-id="e5d51-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="e5d51-254">Altere **Largura da Célula** para 0,05 para espaçar os botões dentro da linha</span><span class="sxs-lookup"><span data-stu-id="e5d51-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="e5d51-255">Em seguida, clique no botão **Atualizar Coleção** para aplicar a nova configuração:</span><span class="sxs-lookup"><span data-stu-id="e5d51-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="e5d51-257">As alterações de configuração que você acabou de aplicar representam as alterações mínimas necessárias para atingir o objetivo de colocar os botões em uma só linha.</span><span class="sxs-lookup"><span data-stu-id="e5d51-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="e5d51-258">No entanto, em projetos futuros, dependendo de fatores como a orientação dos objetos pai e filho, talvez seja necessário ajustar outras configurações, como o tipo de orientação.</span><span class="sxs-lookup"><span data-stu-id="e5d51-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="e5d51-259">Para saber mais sobre a coleção de objetos de grade do MRTK, você pode acessar o guia [Scripts da coleção de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) no [Portal da Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e5d51-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="e5d51-260">Com o objeto ButtonCollection ainda selecionado na janela Hierarquia, na janela Inspetor, altere a **Posição** da Transformação do objeto ButtonCollection para que seus objetos de botão filho sejam posicionados na frente da câmera, que está posicionada na origem, por exemplo, x = 0, y = 0 e z = 0,5:</span><span class="sxs-lookup"><span data-stu-id="e5d51-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="e5d51-262">Quando você adicionou pela primeira vez o pré-fabricado PressableButtonHoloLens2 à cena na seção [Gestos de acompanhamento de mão e botões de interação](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) acima, você o posicionou na frente da câmera.</span><span class="sxs-lookup"><span data-stu-id="e5d51-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="e5d51-263">No entanto, como a Coleção de Objetos de Grade controla a posição de objetos filho imediatos, a posição Z dos objetos filho PressableButtonHoloLens2 foi redefinida como 0 de acordo com a Distância padrão da Coleção de Objetos de Grade do valor pai 0.</span><span class="sxs-lookup"><span data-stu-id="e5d51-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="e5d51-264">Esse (e para manter a relação posicional pai/filho organizada) é o motivo pelo qual mudamos a posição do objeto ButtonCollection pai para frente, em vez de configurar a Distância do valor pai para mover os objetos filho PressableButtonHoloLens2 para frente.</span><span class="sxs-lookup"><span data-stu-id="e5d51-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="e5d51-265">3. Testar os botões usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="e5d51-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="e5d51-266">Pressione o botão Reproduzir para entrar no modo de Jogo e use a simulação de entrada no editor para testar cada um dos botões no painel de botões que acaba de ser criado:</span><span class="sxs-lookup"><span data-stu-id="e5d51-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="e5d51-268">No momento, quando você pressiona qualquer um dos cinco botões, a cor do cubo muda para ciano.</span><span class="sxs-lookup"><span data-stu-id="e5d51-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="e5d51-269">Para tornar a experiência mais interessante, use o que você acaba de aprender para configurar cada botão para alterar o cubo para uma cor diferente.</span><span class="sxs-lookup"><span data-stu-id="e5d51-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="e5d51-270">Como adicionar texto à sua cena</span><span class="sxs-lookup"><span data-stu-id="e5d51-270">Adding text into your scene</span></span>

<span data-ttu-id="e5d51-271">Nesta seção, você aprenderá a adicionar texto às suas experiências de realidade misturada usando o TextMesh Pro da Unity, que você preparou na seção [Importar Recursos Essenciais do TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) do tutorial anterior.</span><span class="sxs-lookup"><span data-stu-id="e5d51-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="e5d51-272">Neste exemplo específico, você adicionará um rótulo simples sob a coleção de botões que você criou na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="e5d51-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="e5d51-273">Clique com o botão direito do mouse no objeto ButtonCollection e selecione **Objeto 3D** > **Text-TextMeshPro** para criar um objeto TextMeshPro como um filho do objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="e5d51-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="e5d51-275">Com o objeto TextMeshPro que acaba de ser criado, o Texto nomeado (TMP), ainda selecionado, na janela Inspetor, muda de posição e tamanho para que o rótulo seja posicionado de maneira organizada abaixo da coleção de botões, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e5d51-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="e5d51-276">Alterar a **Pos Y** de Rect Transform para -0,0425</span><span class="sxs-lookup"><span data-stu-id="e5d51-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="e5d51-277">Alterar a **Largura** de Rect Transform para 0,24</span><span class="sxs-lookup"><span data-stu-id="e5d51-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="e5d51-278">Alterar a **Altura** de Rect Transform para 0,024</span><span class="sxs-lookup"><span data-stu-id="e5d51-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="e5d51-279">Em seguida, atualize o texto para refletir qual é o rótulo e escolha as propriedades da fonte para que o texto caiba no rótulo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e5d51-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="e5d51-280">Alterar o **Texto** do Text Mesh Pro (Script) para Coleção de Botões</span><span class="sxs-lookup"><span data-stu-id="e5d51-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="e5d51-281">Alterar o **Estilo da Fonte** do Text Mesh Pro (Script) para Negrito</span><span class="sxs-lookup"><span data-stu-id="e5d51-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="e5d51-282">Alterar o **Tamanho da Fonte** do Text Mesh Pro (Script) para 0,2</span><span class="sxs-lookup"><span data-stu-id="e5d51-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="e5d51-283">Alterar o **Alinhamento** do Text Mesh Pro (Script) para Centro e Meio</span><span class="sxs-lookup"><span data-stu-id="e5d51-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="e5d51-285">Parabéns</span><span class="sxs-lookup"><span data-stu-id="e5d51-285">Congratulations</span></span>

<span data-ttu-id="e5d51-286">Neste tutorial, você aprendeu a clonar, personalizar e definir uma configuração de perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e5d51-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="e5d51-287">Você também aprendeu a interagir com botões para disparar eventos usando mãos rastreadas no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e5d51-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="e5d51-288">Por fim, você aprendeu a criar uma interface do usuário simples usando o componente Coleção de Objetos de Grade do MRTK e o Text Mesh Pro do Unity.</span><span class="sxs-lookup"><span data-stu-id="e5d51-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="e5d51-289">Próximo tutorial: 4. Colocar o conteúdo dinâmico e usar solucionadores</span><span class="sxs-lookup"><span data-stu-id="e5d51-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)

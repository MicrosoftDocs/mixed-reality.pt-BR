---
title: Tutoriais de introdução-3. Criando interface do usuário e Configurando o kit de ferramentas de realidade mista
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: f1d042150d1c81940e672b174c6c02ac71e05883
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554794"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="e34e4-105">3. criando a interface do usuário e Configurando o kit de ferramentas de realidade mista</span><span class="sxs-lookup"><span data-stu-id="e34e4-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="e34e4-106">No tutorial anterior, você aprendeu sobre alguns dos recursos que o MRTK (Kit de ferramentas de realidade misturada) tem a oferecer ao iniciar seu primeiro aplicativo para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e34e4-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="e34e4-107">Neste tutorial, você aprenderá a criar e organizar botões juntamente com os painéis de texto da interface do usuário e usar a interação padrão (toque) para interagir com cada botão.</span><span class="sxs-lookup"><span data-stu-id="e34e4-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="e34e4-108">Você também explorará a adição de ações e efeitos simples, como alterar o tamanho, o som e a cor de objetos.</span><span class="sxs-lookup"><span data-stu-id="e34e4-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="e34e4-109">Este módulo apresentará conceitos básicos sobre a modificação de perfis MRTK, começando pela desativação da visualização de malha de [mapeamento espacial](spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="e34e4-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="e34e4-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e34e4-110">Objectives</span></span>

* <span data-ttu-id="e34e4-111">Personalizar e configurar perfis do Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="e34e4-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="e34e4-112">Interagir com hologramas usando elementos e botões de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="e34e4-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="e34e4-113">Interações e entrada de acompanhamento de mão básicas</span><span class="sxs-lookup"><span data-stu-id="e34e4-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="e34e4-114">Como configurar os perfis do kit de ferramentas de realidade misturada (alterar a opção de exibição de conscientização espacial)</span><span class="sxs-lookup"><span data-stu-id="e34e4-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="e34e4-115">Nesta seção, você aprenderá a personalizar e configurar os perfis de MRTK padrão.</span><span class="sxs-lookup"><span data-stu-id="e34e4-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="e34e4-116">Este exemplo específico mostrará como ocultar a malha de conscientização espacial alterando as configurações do observador de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="e34e4-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="e34e4-117">No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis MRTK.</span><span class="sxs-lookup"><span data-stu-id="e34e4-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="e34e4-118">As principais etapas que você seguirá para ocultar a malha de conscientização espacial são:</span><span class="sxs-lookup"><span data-stu-id="e34e4-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="e34e4-119">Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="e34e4-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="e34e4-120">Habilitar o sistema de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="e34e4-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="e34e4-121">Clonar o perfil do sistema de reconhecimento espacial padrão</span><span class="sxs-lookup"><span data-stu-id="e34e4-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="e34e4-122">Clonar o perfil de observador de malha de conscientização espacial padrão</span><span class="sxs-lookup"><span data-stu-id="e34e4-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="e34e4-123">Alterar a visibilidade da malha de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="e34e4-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="e34e4-124">Por padrão, os perfis do MRTK não são editáveis.</span><span class="sxs-lookup"><span data-stu-id="e34e4-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="e34e4-125">Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados.</span><span class="sxs-lookup"><span data-stu-id="e34e4-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="e34e4-126">Há várias camadas aninhadas de perfis.</span><span class="sxs-lookup"><span data-stu-id="e34e4-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="e34e4-127">Portanto, é comum clonar e editar vários perfis ao configurar uma ou mais configurações.</span><span class="sxs-lookup"><span data-stu-id="e34e4-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="e34e4-128">1. clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="e34e4-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="e34e4-129">O perfil de configuração é o perfil de nível superior.</span><span class="sxs-lookup"><span data-stu-id="e34e4-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="e34e4-130">Consequentemente, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.</span><span class="sxs-lookup"><span data-stu-id="e34e4-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="e34e4-131">Com o objeto **MixedRealityToolkit** selecionado na janela hierarquia, na janela Inspetor, altere o **perfil de configuração** do kit de ferramentas da realidade misturada para **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="e34e4-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="e34e4-133">Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **copiar & Personalizar** para abrir a janela clonar perfil:</span><span class="sxs-lookup"><span data-stu-id="e34e4-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="e34e4-135">Na janela clonar perfil, clique no botão **clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="e34e4-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="e34e4-137">Agora, o perfil de configuração recém-criado é atribuído como o perfil de configuração para sua cena:</span><span class="sxs-lookup"><span data-stu-id="e34e4-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="e34e4-139">No menu do Unity, selecione **arquivo** > **salvar** para salvar sua cena.</span><span class="sxs-lookup"><span data-stu-id="e34e4-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="e34e4-140">Lembre-se de salvar seu trabalho em todo o tutorial.</span><span class="sxs-lookup"><span data-stu-id="e34e4-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="e34e4-141">2. habilitar o sistema de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="e34e4-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="e34e4-142">Com o objeto **MixedRealityToolkit** ainda selecionado na janela hierarquia, na janela Inspetor, selecione a guia **reconhecimento espacial** e marque a caixa de seleção **habilitar sistema de conscientização espacial** :</span><span class="sxs-lookup"><span data-stu-id="e34e4-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="e34e4-144">3. clonar o perfil do sistema de reconhecimento espacial padrão</span><span class="sxs-lookup"><span data-stu-id="e34e4-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="e34e4-145">Na guia **reconhecimento espacial** , clique no botão **clonar** para abrir a janela clonar perfil:</span><span class="sxs-lookup"><span data-stu-id="e34e4-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="e34e4-147">Na janela clonar perfil, clique no botão **clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="e34e4-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="e34e4-149">O perfil do sistema de conscientização espacial recém-criado agora é atribuído automaticamente ao seu perfil de configuração:</span><span class="sxs-lookup"><span data-stu-id="e34e4-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="e34e4-151">4. clonar o perfil de observador de malha de conscientização espacial padrão</span><span class="sxs-lookup"><span data-stu-id="e34e4-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="e34e4-152">Com a guia **conscientização espacial** ainda selecionada, expanda a seção **observador de malha espacial do Windows Mixed Realm** e clique no botão **clonar** para abrir a janela clonar perfil:</span><span class="sxs-lookup"><span data-stu-id="e34e4-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="e34e4-154">Na janela clonar perfil, clique no botão **clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="e34e4-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="e34e4-156">O perfil de observador de malha de conscientização espacial recém-criado agora é automaticamente atribuído ao seu perfil do sistema de conscientização espacial:</span><span class="sxs-lookup"><span data-stu-id="e34e4-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="e34e4-158">5. alterar a visibilidade da malha de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="e34e4-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="e34e4-159">Nas **configurações de observador de malha espacial**, altere a **opção de exibição** para **oclusão** para tornar a malha de mapeamento espacial invisível ao mesmo tempo em funcionamento:</span><span class="sxs-lookup"><span data-stu-id="e34e4-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="e34e4-161">Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional.</span><span class="sxs-lookup"><span data-stu-id="e34e4-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="e34e4-162">Por exemplo, todos os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="e34e4-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="e34e4-163">Você acabou de aprender como modificar uma configuração do perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e34e4-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="e34e4-164">Como você pode ver, para personalizar as configurações de MRTK, primeiro você precisa criar cópias dos perfis padrão.</span><span class="sxs-lookup"><span data-stu-id="e34e4-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="e34e4-165">Como os perfis padrão não são editáveis, você sempre os terá como referência se desejar reverter para as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="e34e4-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="e34e4-166">Para saber mais sobre os perfis de MRTK e sua arquitetura, você pode visitar o [Guia de configuração do perfil do reality Toolkit misto](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e34e4-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="e34e4-167">Gestos de acompanhamento de mão e botões de interação</span><span class="sxs-lookup"><span data-stu-id="e34e4-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="e34e4-168">Nesta seção, você aprenderá a usar o rastreamento manual para pressionar um botão e disparar eventos para causar uma ação quando o botão for pressionado.</span><span class="sxs-lookup"><span data-stu-id="e34e4-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="e34e4-169">Este exemplo específico mostrará como alterar a cor de um cubo quando o botão for pressionado e alterá-lo de volta para a cor original quando o botão for liberado.</span><span class="sxs-lookup"><span data-stu-id="e34e4-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="e34e4-170">No entanto, você pode seguir esses mesmos princípios para criar outros eventos.</span><span class="sxs-lookup"><span data-stu-id="e34e4-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="e34e4-171">As principais etapas que você seguirá para alterar a cor do cubo são:</span><span class="sxs-lookup"><span data-stu-id="e34e4-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="e34e4-172">Adicionar um botão pressionável pré-fabricado à cena</span><span class="sxs-lookup"><span data-stu-id="e34e4-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="e34e4-173">Adicionar um cubo à cena</span><span class="sxs-lookup"><span data-stu-id="e34e4-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="e34e4-174">Configurar o tipo de evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="e34e4-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="e34e4-175">Configurar o cubo para receber o evento on Press</span><span class="sxs-lookup"><span data-stu-id="e34e4-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="e34e4-176">Definir a ação a ser disparada pelo evento on Press</span><span class="sxs-lookup"><span data-stu-id="e34e4-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="e34e4-177">Configurar o cubo para receber o evento on Release</span><span class="sxs-lookup"><span data-stu-id="e34e4-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="e34e4-178">Definir a ação a ser disparada pelo evento na versão</span><span class="sxs-lookup"><span data-stu-id="e34e4-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="e34e4-179">Testar o botão usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="e34e4-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="e34e4-180">1. adicionar um botão pressionável pré-fabricado à cena</span><span class="sxs-lookup"><span data-stu-id="e34e4-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="e34e4-181">Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um gameobject pré-configurado armazenado como um ativo de Unity e pode ser reutilizado em todo o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e34e4-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="e34e4-182">Na **janela do projeto**, procure **PressableButtonHoloLens2** para localizar o pré-fabricado que será usado para este exemplo:</span><span class="sxs-lookup"><span data-stu-id="e34e4-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="e34e4-184">No resultado da **pesquisa** , selecione **PressableButtonHoloLens2** pré-fabricado e **Arraste** -o para a janela **hierarquia** para adicioná-lo à sua cena:</span><span class="sxs-lookup"><span data-stu-id="e34e4-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="e34e4-186">Para exibir sua cena, conforme mostrado na imagem abaixo, clique duas vezes no objeto PressableButtonHoloLens2 na janela hierarquia para colocá-lo em foco e, em seguida, use a <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">cena Gizmo</a>, localizada no canto superior direito da janela cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço.</span><span class="sxs-lookup"><span data-stu-id="e34e4-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="e34e4-187">Com o objeto **PressableButtonHoloLens2** ainda selecionado, na janela **Inspetor** :</span><span class="sxs-lookup"><span data-stu-id="e34e4-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="e34e4-188">Altere sua **posição** de transformação para que ela esteja posicionada na frente da câmera, que está posicionada na origem, por exemplo, x = 0, y = 0 e z = 0,5</span><span class="sxs-lookup"><span data-stu-id="e34e4-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="e34e4-190">Em geral, uma unidade de posição no Unity é aproximadamente equivalente a 1 metro no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="e34e4-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="e34e4-191">No entanto, há exceções a isso, por exemplo, quando os objetos são filhos de objetos dimensionados.</span><span class="sxs-lookup"><span data-stu-id="e34e4-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="e34e4-192">2. adicionar um cubo à cena</span><span class="sxs-lookup"><span data-stu-id="e34e4-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="e34e4-193">Clique com o botão direito do mouse em um ponto vazio dentro da janela hierarquia e selecione o **objeto 3d** > **cubo** para adicionar um cubo à sua cena:</span><span class="sxs-lookup"><span data-stu-id="e34e4-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="e34e4-195">Com o objeto de **cubo** ainda selecionado, na janela **Inspetor** :</span><span class="sxs-lookup"><span data-stu-id="e34e4-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="e34e4-196">Altere sua **posição** de transformação para que fique perto do botão pressionável, mas não se sobreponha a ela, por exemplo, x = 0, y = 0, 4 e z = 0,5</span><span class="sxs-lookup"><span data-stu-id="e34e4-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="e34e4-197">Altere sua **escala** de transformação para um tamanho adequado, por exemplo, x = 0, 2, y = 0, 2 e z = 0, 2</span><span class="sxs-lookup"><span data-stu-id="e34e4-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="e34e4-199">3. configurar o tipo de evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="e34e4-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="e34e4-200">Na janela hierarquia, selecione o objeto **PressableButtonHoloLens2** e, em seguida, na janela **Inspetor** **menu**de etc, selecione **recolher todos os componentes** para obter uma visão geral de todos os componentes neste objeto:</span><span class="sxs-lookup"><span data-stu-id="e34e4-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="e34e4-202">Expanda o componente **interagir (script)** e localize e expanda a seção **eventos** > **receptores** :</span><span class="sxs-lookup"><span data-stu-id="e34e4-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="e34e4-204">Clique no botão **Adicionar evento** para criar um novo receptor de evento do tipo de receptor de evento **InteractableOnPressReceiver**:</span><span class="sxs-lookup"><span data-stu-id="e34e4-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="e34e4-206">O tipo de receptor de evento chamado InteractableOnPressReceiver permite que o botão responda a um evento pressionado quando uma mão controlada pressiona o botão.</span><span class="sxs-lookup"><span data-stu-id="e34e4-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="e34e4-207">Para o receptor de eventos recém-criado, altere o **filtro de interação** para **quase e longe**:</span><span class="sxs-lookup"><span data-stu-id="e34e4-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="e34e4-209">4. configurar o cubo para receber o evento on Press</span><span class="sxs-lookup"><span data-stu-id="e34e4-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="e34e4-210">Na janela hierarquia, **clique e arraste** o **cubo** para o campo objeto **Propriedades de evento** do evento **on Press ()** para atribuir o cubo como um receptor do evento on Press ():</span><span class="sxs-lookup"><span data-stu-id="e34e4-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="e34e4-212">5. definir a ação a ser disparada pelo evento on Press</span><span class="sxs-lookup"><span data-stu-id="e34e4-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="e34e4-213">Clique no menu suspenso ação, atualmente atribuído a **nenhuma função**e selecione MeshRenderer \*\* > material material para\*\* definir a propriedade material do cubo a ser alterada quando o evento on Press () for disparado:</span><span class="sxs-lookup"><span data-stu-id="e34e4-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="e34e4-215">Clique no ícone de **círculo** pequeno ao lado do campo material, preenchido atualmente com **nenhum (material)** , para abrir a janela Selecionar material:</span><span class="sxs-lookup"><span data-stu-id="e34e4-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="e34e4-217">Na janela Selecionar material, **pesquise** **MRTK_Standard** e selecione um material adequado, por exemplo, **MRTK_Standard_Cyan** para que a cor do cubo seja alterada para ciano quando o botão for pressionado:</span><span class="sxs-lookup"><span data-stu-id="e34e4-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="e34e4-219">6. configurar o cubo para receber o evento on Release</span><span class="sxs-lookup"><span data-stu-id="e34e4-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="e34e4-220">**Repetir** Etapa 4 do evento on Release para atribuir o **cubo** como um destinatário do evento **on Release ()** .</span><span class="sxs-lookup"><span data-stu-id="e34e4-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="e34e4-221">7. definir a ação a ser disparada pelo evento na versão</span><span class="sxs-lookup"><span data-stu-id="e34e4-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="e34e4-222">**Repetir** Etapa 5 para o evento na versão, mas escolha o material de **MRTK_Standard_LightGray** para que a cor do cubo retorne para sua cor cinza clara original quando o botão for liberado:</span><span class="sxs-lookup"><span data-stu-id="e34e4-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="e34e4-224">8. testar o botão usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="e34e4-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="e34e4-225">Pressione o botão **reproduzir** para entrar no modo de jogo e use a simulação de entrada no editor para testar seu botão recentemente configurado.</span><span class="sxs-lookup"><span data-stu-id="e34e4-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="e34e4-226">Botão não pressionado (barra de espaços + mouse de rolagem para trás):</span><span class="sxs-lookup"><span data-stu-id="e34e4-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="e34e4-228">Botão pressionado (barra de espaços + mouse de rolagem para frente):</span><span class="sxs-lookup"><span data-stu-id="e34e4-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="e34e4-230">Para saber como usar a simulação de entrada no editor, você pode consultar o [usando a simulação de entrada da edição do editor para testar um](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guia de cena no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e34e4-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="e34e4-231">Criando um painel de botões usando a coleção de objetos de grade do MRTK</span><span class="sxs-lookup"><span data-stu-id="e34e4-231">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="e34e4-232">Nesta seção, você aprenderá a alinhar automaticamente vários botões em uma interface de usuário clara usando a ferramenta de coleção de objetos de grade do MRTK.</span><span class="sxs-lookup"><span data-stu-id="e34e4-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="e34e4-233">Este exemplo específico mostrará como criar um painel com cinco botões alinhados horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="e34e4-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="e34e4-234">No entanto, você pode seguir esses mesmos princípios para criar outros layouts.</span><span class="sxs-lookup"><span data-stu-id="e34e4-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="e34e4-235">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="e34e4-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e34e4-236">Pai os objetos Button para um objeto pai</span><span class="sxs-lookup"><span data-stu-id="e34e4-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="e34e4-237">Adicionar e configurar o componente de coleção de objetos de grade (script)</span><span class="sxs-lookup"><span data-stu-id="e34e4-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="e34e4-238">Testar os botões usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="e34e4-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="e34e4-239">1. pai os objetos Button para um objeto pai</span><span class="sxs-lookup"><span data-stu-id="e34e4-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="e34e4-240">Clique com o botão direito do mouse em um ponto vazio dentro da janela hierarquia e selecione **criar vazio**:</span><span class="sxs-lookup"><span data-stu-id="e34e4-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="e34e4-242">Clique com o botão direito do mouse no objeto recém-criado, selecione **renomear**e dê a ele um nome adequado, por exemplo, **buttoncollection**:</span><span class="sxs-lookup"><span data-stu-id="e34e4-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="e34e4-244">Selecione o objeto **PressableButtonHoloLens2** e **Arraste** -o para cima do objeto **buttoncollection** para torná-lo um filho do objeto buttoncollection:</span><span class="sxs-lookup"><span data-stu-id="e34e4-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="e34e4-246">Clique com o botão direito do mouse no objeto **PressableButtonHoloLens2** e selecione **duplicar** para criar uma cópia dele:</span><span class="sxs-lookup"><span data-stu-id="e34e4-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="e34e4-248">**Repita** esta etapa quatro vezes até que você tenha um total de cinco objetos PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="e34e4-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="e34e4-249">2. adicionar e configurar o componente de coleção de objetos de grade (script)</span><span class="sxs-lookup"><span data-stu-id="e34e4-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="e34e4-250">Com o objeto Buttoncollection selecionado na janela hierarquia, na janela Inspetor, clique no botão **Adicionar componente** , procure e selecione coleção de objetos de **grade** para adicionar um componente Script (coleção de objetos de grade) ao objeto buttoncollection:</span><span class="sxs-lookup"><span data-stu-id="e34e4-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="e34e4-252">Configure a coleção de objetos de grade (script) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e34e4-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="e34e4-253">Alterar o **número de linhas** para 1 para que todos os botões sejam alinhados em uma única linha</span><span class="sxs-lookup"><span data-stu-id="e34e4-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="e34e4-254">Alterar a **largura da célula** para 0, 5 para espaçar os botões dentro da linha</span><span class="sxs-lookup"><span data-stu-id="e34e4-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="e34e4-255">Em seguida, clique no botão **Atualizar coleção** para aplicar a nova configuração:</span><span class="sxs-lookup"><span data-stu-id="e34e4-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="e34e4-257">As alterações de configuração que você acabou de aplicar representam as alterações mínimas necessárias para atingir o objetivo de colocar os botões em uma única linha.</span><span class="sxs-lookup"><span data-stu-id="e34e4-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="e34e4-258">No entanto, em projetos futuros, dependendo de fatores como, por exemplo, a orientação dos objetos pai e filho, talvez seja necessário ajustar outras configurações, como, por exemplo, o tipo de orientação.</span><span class="sxs-lookup"><span data-stu-id="e34e4-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="e34e4-259">Para saber mais sobre a coleção de objetos de grade do MRTK, você pode visitar o guia de [scripts da coleção de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) no portal de documentação do [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="e34e4-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="e34e4-260">Com o objeto Buttoncollection ainda selecionado na janela hierarquia, na janela Inspetor, altere a **posição** de transformação do objeto buttoncollection para que seus objetos de botão filho sejam posicionados na frente da câmera, que está posicionada na origem, por exemplo, x = 0, y = 0 e z = 0,5:</span><span class="sxs-lookup"><span data-stu-id="e34e4-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="e34e4-262">Quando você adicionou pela primeira vez o PressableButtonHoloLens2 pré-fabricado à cena na seção [gestos de acompanhamento de mão e botões que interagem](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) acima, você o posicionou na frente da câmera.</span><span class="sxs-lookup"><span data-stu-id="e34e4-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="e34e4-263">No entanto, como a coleção de objetos de grade controla sua posição de objetos filho imediatos, a posição Z dos objetos filho PressableButtonHoloLens2 foi redefinida como 0 de acordo com a distância padrão da coleção de objetos de grade do valor pai 0.</span><span class="sxs-lookup"><span data-stu-id="e34e4-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="e34e4-264">Isso, e para manter a relação posicional pai/filho organizada, é por isso que mudamos a posição do objeto Buttoncollection pai em vez de configurar a distância do valor pai para mover os objetos filho PressableButtonHoloLens2 para frente.</span><span class="sxs-lookup"><span data-stu-id="e34e4-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="e34e4-265">3. testar os botões usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="e34e4-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="e34e4-266">Pressione o botão reproduzir para entrar no modo de jogo e use a simulação de entrada no editor para testar cada um dos botões em no painel recém-criado dos botões:</span><span class="sxs-lookup"><span data-stu-id="e34e4-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="e34e4-268">Atualmente, quando você pressiona qualquer um dos cinco botões, a cor do cubo muda para ciano.</span><span class="sxs-lookup"><span data-stu-id="e34e4-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="e34e4-269">Para tornar a experiência mais interessante, use o que você apenas aprende para configurar cada botão para alterar o cubo para uma cor diferente.</span><span class="sxs-lookup"><span data-stu-id="e34e4-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="e34e4-270">Adicionando texto à sua cena</span><span class="sxs-lookup"><span data-stu-id="e34e4-270">Adding text into your scene</span></span>

<span data-ttu-id="e34e4-271">Nesta seção, você aprenderá a adicionar texto às suas experiências de realidade misturada usando o netmesh pro da Unity, que você preparou na seção [importar recursos do Textmesh pro Essentials](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) do tutorial anterior.</span><span class="sxs-lookup"><span data-stu-id="e34e4-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="e34e4-272">Neste exemplo específico, você adicionará um rótulo simples sob a coleção de botões que você criou na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="e34e4-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="e34e4-273">Clique com o botão direito do mouse no objeto Buttoncollection e selecione **objeto 3d** > **Text-TextMeshPro** para criar um objeto TextMeshPro como um filho do objeto buttoncollection:</span><span class="sxs-lookup"><span data-stu-id="e34e4-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="e34e4-275">Com o objeto TextMeshPro recém-criado, o texto nomeado (TMP), ainda selecionado, na janela Inspetor, altere sua posição e tamanho para que o rótulo seja posicionado de forma organizada na coleção de botões, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e34e4-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="e34e4-276">Alterar a transformação Rect **pos Y** para-0, 425</span><span class="sxs-lookup"><span data-stu-id="e34e4-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="e34e4-277">Altere a **largura** do Rect Transform para 0,24</span><span class="sxs-lookup"><span data-stu-id="e34e4-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="e34e4-278">Altere a **altura** do Rect Transform para 0, 24</span><span class="sxs-lookup"><span data-stu-id="e34e4-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="e34e4-279">Em seguida, atualize o texto para refletir qual é o rótulo e escolha Propriedades de fonte para que o texto caiba no rótulo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e34e4-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="e34e4-280">Alterar o **texto** da malha de texto pro (script) para a coleção de botões</span><span class="sxs-lookup"><span data-stu-id="e34e4-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="e34e4-281">Altere o **estilo de fonte** pro (script) de malha de texto para negrito</span><span class="sxs-lookup"><span data-stu-id="e34e4-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="e34e4-282">Altere o **tamanho da fonte** do pro (script de malha de texto) para 0,2</span><span class="sxs-lookup"><span data-stu-id="e34e4-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="e34e4-283">Alterar o **alinhamento** pro (script) da malha de texto para o centro e o meio</span><span class="sxs-lookup"><span data-stu-id="e34e4-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="e34e4-285">Parabéns</span><span class="sxs-lookup"><span data-stu-id="e34e4-285">Congratulations</span></span>

<span data-ttu-id="e34e4-286">Neste tutorial, você aprendeu a clonar, personalizar e definir uma configuração de perfil MRTK.</span><span class="sxs-lookup"><span data-stu-id="e34e4-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="e34e4-287">Você também aprendeu como interagir com botões para disparar eventos usando mãos controladas no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e34e4-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="e34e4-288">Por fim, você aprendeu a criar uma interface de interface do usuário simples usando o componente de coleção de objetos de grade do MRTK e a malha de texto do Unity pro.</span><span class="sxs-lookup"><span data-stu-id="e34e4-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="e34e4-289">Próximo tutorial: 4. colocando conteúdo dinâmico e usando os solveres</span><span class="sxs-lookup"><span data-stu-id="e34e4-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)

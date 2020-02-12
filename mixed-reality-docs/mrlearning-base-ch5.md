---
title: Tutoriais de introdução-6. Explorando opções de entrada avançadas
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129567"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="08329-105">6. explorando opções de entrada avançadas</span><span class="sxs-lookup"><span data-stu-id="08329-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="08329-106">Neste tutorial, você vai explorar algumas opções de entrada avançadas para o HoloLens 2, incluindo o uso de comandos de voz, gesto de panorâmica e acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="08329-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="08329-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="08329-107">Objectives</span></span>

* <span data-ttu-id="08329-108">Disparar eventos usando comandos de voz e palavras-chave</span><span class="sxs-lookup"><span data-stu-id="08329-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="08329-109">Usar mãos controladas para deslocar texturas e objetos 3D com mãos controladas</span><span class="sxs-lookup"><span data-stu-id="08329-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="08329-110">Aproveitar os recursos de acompanhamento de olho do HoloLens 2 para selecionar objetos</span><span class="sxs-lookup"><span data-stu-id="08329-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="08329-111">Habilitando comandos de voz</span><span class="sxs-lookup"><span data-stu-id="08329-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="08329-112">Nesta seção, você implementará um comando de fala para permitir que o usuário reproduza um som no objeto Octa.</span><span class="sxs-lookup"><span data-stu-id="08329-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="08329-113">Para isso, você criará um novo comando de fala e, em seguida, configurará o evento para que ele dispare a ação desejada quando a palavra-chave do comando de fala for falada.</span><span class="sxs-lookup"><span data-stu-id="08329-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="08329-114">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="08329-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="08329-115">Clonar o perfil do sistema de entrada padrão</span><span class="sxs-lookup"><span data-stu-id="08329-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="08329-116">Clonar o perfil de comandos de fala padrão</span><span class="sxs-lookup"><span data-stu-id="08329-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="08329-117">Criar um novo comando de fala</span><span class="sxs-lookup"><span data-stu-id="08329-117">Create a new speech command</span></span>
4. <span data-ttu-id="08329-118">Adicionar e configurar o componente do manipulador de entrada de fala (script)</span><span class="sxs-lookup"><span data-stu-id="08329-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="08329-119">Implementar o evento de resposta para o comando de fala</span><span class="sxs-lookup"><span data-stu-id="08329-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="08329-120">1. clonar o perfil do sistema de entrada padrão</span><span class="sxs-lookup"><span data-stu-id="08329-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="08329-121">Na janela hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, selecione a guia **entrada** e clone o **DefaultHoloLens2InputSystemProfile** para substituí-lo pelo seu próprio **perfil de sistema de entrada**personalizável:</span><span class="sxs-lookup"><span data-stu-id="08329-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="08329-123">Para obter um lembrete sobre como clonar perfis MRTK, você pode consultar as instruções [como configurar os perfis do kit de ferramentas de realidade misturada](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .</span><span class="sxs-lookup"><span data-stu-id="08329-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="08329-124">2. clonar o perfil de comandos de fala padrão</span><span class="sxs-lookup"><span data-stu-id="08329-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="08329-125">Expanda a seção **fala** e clone o **DefaultMixedRealitySpeechCommandsProfile** para substituí-lo por seu próprio **perfil de comandos de fala**personalizável:</span><span class="sxs-lookup"><span data-stu-id="08329-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="08329-127">3. criar um novo comando de fala</span><span class="sxs-lookup"><span data-stu-id="08329-127">3. Create a new speech command</span></span>

<span data-ttu-id="08329-128">Na seção **comandos de fala** , clique no botão **+ Adicionar um novo comando de fala** para adicionar um novo comando de fala à parte inferior da lista de comandos de fala existentes. em seguida, no campo **palavra-chave** , insira uma palavra ou frase adequada, por exemplo, **reproduzir música**:</span><span class="sxs-lookup"><span data-stu-id="08329-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="08329-130">Se o computador não tiver um microfone e você quiser testar o comando de fala usando a simulação no editor, você poderá atribuir um código de chave ao comando de fala, o que permitirá que você o dispare quando a chave correspondente for pressionada.</span><span class="sxs-lookup"><span data-stu-id="08329-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="08329-131">4. adicionar e configurar o componente do manipulador de entrada de fala (script)</span><span class="sxs-lookup"><span data-stu-id="08329-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="08329-132">Na janela hierarquia, selecione o objeto **Octa** e adicione o componente **manipulador de entrada de fala (script)** ao objeto Octa.</span><span class="sxs-lookup"><span data-stu-id="08329-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="08329-133">Em seguida, desmarque a caixa de seleção **é o foco necessário** para que o usuário não precise examinar o objeto Octa para disparar o comando de fala:</span><span class="sxs-lookup"><span data-stu-id="08329-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="08329-135">5. implementar o evento de resposta para o comando de fala</span><span class="sxs-lookup"><span data-stu-id="08329-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="08329-136">No componente manipulador de entrada de fala (script), clique no pequeno **+** botão para adicionar uma palavra-chave e, em seguida, na lista suspensa de **palavras-chave** , escolha a palavra-chave **reproduzir música** criada anteriormente:</span><span class="sxs-lookup"><span data-stu-id="08329-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="08329-138">As palavras-chave no menu suspenso de palavras-chaves são preenchidas com base nas palavras-chaves definidas na lista de comandos de fala no perfil de comandos de fala.</span><span class="sxs-lookup"><span data-stu-id="08329-138">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="08329-139">Crie um novo evento **Response ()** , configure o objeto **Octa** para receber o evento, defina **audioname. PlayOneShot** como a ação a ser disparada e atribua um clipe de áudio adequado ao campo de **clipe de áudio** , por exemplo, o clipe de áudio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="08329-139">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> <span data-ttu-id="08329-141">Para obter um lembrete sobre como implementar eventos e atribuir um clipe de áudio, você pode consultar as instruções [implementar o evento on Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) .</span><span class="sxs-lookup"><span data-stu-id="08329-141">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="08329-142">O gesto de panorâmica</span><span class="sxs-lookup"><span data-stu-id="08329-142">The Pan Gesture</span></span>

<span data-ttu-id="08329-143">O gesto de panorâmica é útil para rolar usando o dedo ou a mão para rolar pelo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="08329-143">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="08329-144">Neste exemplo, você aprenderá primeiro a rolar uma interface do usuário 2D e, em seguida, expandir isso para poder percorrer uma coleção de objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="08329-144">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="08329-145">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="08329-145">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="08329-146">Criar um objeto Quad que pode ser usado para panorâmica</span><span class="sxs-lookup"><span data-stu-id="08329-146">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="08329-147">Adicionar o componente Near-Touch (script) de interação próxima</span><span class="sxs-lookup"><span data-stu-id="08329-147">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="08329-148">Adicionar o componente de zoom (script) de panorâmica de interação à mão</span><span class="sxs-lookup"><span data-stu-id="08329-148">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="08329-149">Adicionar conteúdo 2D a ser rolado</span><span class="sxs-lookup"><span data-stu-id="08329-149">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="08329-150">Adicionar conteúdo 3D a ser rolado</span><span class="sxs-lookup"><span data-stu-id="08329-150">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="08329-151">Adicionar a movimentação com componente Pan (script)</span><span class="sxs-lookup"><span data-stu-id="08329-151">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="08329-152">O componente mover com Pan (script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="08329-152">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="08329-153">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="08329-153">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="08329-154">1. criar um objeto Quad que pode ser usado para movimento panorâmico</span><span class="sxs-lookup"><span data-stu-id="08329-154">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="08329-155">Na janela hierarquia, clique com o botão direito do mouse em uma área vazia e selecione **objeto 3d** > **quatro** para adicionar uma quádrupla à sua cena.</span><span class="sxs-lookup"><span data-stu-id="08329-155">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="08329-156">Dê a ele um nome adequado, por exemplo, **PanGesture**, e posicione-o em um local adequado, por exemplo, X = 0, Y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="08329-156">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="08329-158">Para um lembrete sobre como adicionar primitivos do Unity, como um 3D Quad, à sua cena, você pode consultar o [Adicionar um cubo às instruções da cena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) .</span><span class="sxs-lookup"><span data-stu-id="08329-158">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="08329-159">Assim como acontece com qualquer outra interação, o gesto de Pan também requer um colisor.</span><span class="sxs-lookup"><span data-stu-id="08329-159">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="08329-160">Por padrão, um quad tem um colisor de malha.</span><span class="sxs-lookup"><span data-stu-id="08329-160">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="08329-161">No entanto, o colisor de malha não é o ideal porque é extremamente fino.</span><span class="sxs-lookup"><span data-stu-id="08329-161">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="08329-162">Para facilitar para o usuário interagir com o colisor, substituiremos o colisor de malha por um colisor de caixa.</span><span class="sxs-lookup"><span data-stu-id="08329-162">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="08329-163">Com o objeto PanGesture ainda selecionado, clique no ícone de **configurações** do componente **Colider de malha** e selecione **remover componente** para remover o colisor de malha:</span><span class="sxs-lookup"><span data-stu-id="08329-163">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="08329-165">Na janela Inspetor, use o botão **Adicionar componente** para adicionar um **Colisor de caixa**e, em seguida, altere o **tamanho** de Colisor de caixa Z para 0,15 para aumentar a espessura do colisor de caixa:</span><span class="sxs-lookup"><span data-stu-id="08329-165">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="08329-167">2. Adicionar o componente de interatividade de interação Near (script)</span><span class="sxs-lookup"><span data-stu-id="08329-167">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="08329-168">Com o objeto **PanGesture** ainda selecionado, adicione o componente de inclusão de **interação Near (script)** ao objeto PanGesture e, em seguida, clique nos botões **corrigir limites** e **corrigir centro** para atualizar as propriedades centro local e limites da interação próxima touchável (script) para corresponder ao BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="08329-168">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="08329-170">3. Adicionar o componente de zoom (script) de panorâmica de interação à mão</span><span class="sxs-lookup"><span data-stu-id="08329-170">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="08329-171">Com o objeto **PanGesture** ainda selecionado, adicione o componente de **zoom de Pan de interação à mão (script)** ao objeto PanGesture e marque a caixa de seleção **Bloquear horizontal** para permitir somente a rolagem vertical:</span><span class="sxs-lookup"><span data-stu-id="08329-171">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="08329-173">4. adicionar conteúdo 2D a ser rolado</span><span class="sxs-lookup"><span data-stu-id="08329-173">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="08329-174">No painel projeto, procure o material **PanContent** e clique-e arraste-o para a propriedade **do elemento do** processador de malha do objeto **PanGesture** 0:</span><span class="sxs-lookup"><span data-stu-id="08329-174">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="08329-176">Na janela Inspetor, expanda o componente **material do** **PanContent** recém-adicionado e, em seguida, altere-o para 0,5 para que ele corresponda ao valor X e os blocos apareçam no quadrado:</span><span class="sxs-lookup"><span data-stu-id="08329-176">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="08329-178">Se agora você entrar no modo de jogo, poderá testar a rolagem do conteúdo 2D usando o gesto de Pan na simulação de editor:</span><span class="sxs-lookup"><span data-stu-id="08329-178">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="08329-180">5. adicionar conteúdo 3D a ser rolado</span><span class="sxs-lookup"><span data-stu-id="08329-180">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="08329-181">Na janela hierarquia, **Crie quatro cubos** como objetos filho do **PanContent** e defina a **escala** de transformação como X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="08329-181">In the Hierarchy window, **create four cubes** as a child objects of the **PanContent** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="08329-183">Para espaçar os cubos uniformemente e economizar algum tempo, adicione o componente de coleção de objetos de grade (script) ao objeto pai dos cubos, ou seja, o objeto PanGesture e configure a coleção de objetos de grade (script) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="08329-183">To space the cubes out evenly, and save some time, add the Grid Object Collection (Script) component, to the cubes' parent object, i.e. the PanGesture object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="08329-184">Alterar o **número de linhas** para 1 para que todos os cubos sejam alinhados em uma única linha</span><span class="sxs-lookup"><span data-stu-id="08329-184">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="08329-185">Alterar a **largura da célula** para 0,25 para espaçar os cubos dentro da linha</span><span class="sxs-lookup"><span data-stu-id="08329-185">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="08329-186">Em seguida, clique no botão **Atualizar coleção** para aplicar a nova configuração:</span><span class="sxs-lookup"><span data-stu-id="08329-186">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="08329-188">6. adicionar a movimentação com o componente Pan (script)</span><span class="sxs-lookup"><span data-stu-id="08329-188">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="08329-189">Na janela hierarquia, selecione todos os **objetos filho do cubo**e, em seguida, na janela Inspetor, use o botão **Adicionar componente** para adicionar o componente **mover com Pan (script)** a todos os cubos:</span><span class="sxs-lookup"><span data-stu-id="08329-189">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="08329-191">Para obter um lembrete sobre como selecionar vários objetos na janela hierarquia, tou pode referir-se ao [componente adicionar o manipulador de manipulação (script) a todas as instruções de objetos](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) .</span><span class="sxs-lookup"><span data-stu-id="08329-191">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="08329-192">Com todos os cubos ainda selecionados, clique e arraste o objeto **PanGesture** para o campo **fonte de entrada de Pan** :</span><span class="sxs-lookup"><span data-stu-id="08329-192">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="08329-194">O componente mover com Pan (script) em cada cubo escuta o evento de panorâmica atualizada enviado pelo componente HandInteractionPanZoom (script) no objeto PanGesture, que você atribuiu como a fonte de entrada Pan na etapa acima e atualiza a posição de cada cubo adequados.</span><span class="sxs-lookup"><span data-stu-id="08329-194">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="08329-195">Na janela hierarquia, selecione o objeto **PanGesture** e, em seguida, no Inspetor, **desmarque** a caixa de seleção **processador de malha** para desabilitar o componente de processador de malha:</span><span class="sxs-lookup"><span data-stu-id="08329-195">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="08329-197">Se agora você entrar no modo de jogo, poderá testar a rolagem do conteúdo 3D usando o gesto de Pan na simulação de editor:</span><span class="sxs-lookup"><span data-stu-id="08329-197">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="08329-199">Acompanhamento Ocular</span><span class="sxs-lookup"><span data-stu-id="08329-199">Eye Tracking</span></span>

<span data-ttu-id="08329-200">Nesta seção, você vai explorar como habilitar o controle de olho em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="08329-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="08329-201">Para este exemplo, você implementará a funcionalidade para tornar cada objeto na rotação 3DObjectCollection lentamente durante a pesquisa pelo olhar de olho do usuário, bem como disparará um efeito de blip quando o objeto que está sendo examinado for selecionado pelo toque de ar ou comando de fala.</span><span class="sxs-lookup"><span data-stu-id="08329-201">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="08329-202">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="08329-202">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="08329-203">Adicionar o componente de destino de acompanhamento de olho (script) a todos os objetos de destino</span><span class="sxs-lookup"><span data-stu-id="08329-203">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="08329-204">Adicionar o componente de demonstração do tutorial de acompanhamento de olho (script) a todos os objetos de destino</span><span class="sxs-lookup"><span data-stu-id="08329-204">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="08329-205">Implementar o ao examinar o evento de destino</span><span class="sxs-lookup"><span data-stu-id="08329-205">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="08329-206">Implementar o evento on Selected</span><span class="sxs-lookup"><span data-stu-id="08329-206">Implement the On Selected event</span></span>
5. <span data-ttu-id="08329-207">Habilitar o controle de olho simulado para simulações no editor</span><span class="sxs-lookup"><span data-stu-id="08329-207">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="08329-208">Habilitar a entrada olhar nos recursos de aplicativo do projeto do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="08329-208">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="08329-209">1. Adicionar o componente de destino de acompanhamento de olho (script) a todos os objetos de destino</span><span class="sxs-lookup"><span data-stu-id="08329-209">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="08329-210">Na janela hierarquia, expanda o objeto **3DObjectCollection** e selecione todos os **objetos filho**e, na janela Inspetor, use o botão **Adicionar componente** para adicionar o componente de **destino de acompanhamento de olho (script)** a todos os objetos filho:</span><span class="sxs-lookup"><span data-stu-id="08329-210">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="08329-212">Com todos os **objetos filho** ainda selecionados, configure o componente de **destino de acompanhamento de olho (script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="08329-212">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="08329-213">Altere a **ação Select** a **selecionar**para definir a ação de toque de ar para este objeto como SELECT</span><span class="sxs-lookup"><span data-stu-id="08329-213">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="08329-214">Expandir **voz selecione** e defina o **tamanho** da lista de comandos de voz como 1 e, em seguida, na nova lista de elementos exibida, altere o **elemento 0** para **selecionar**, para definir a ação de comando de fala para esse objeto como SELECT</span><span class="sxs-lookup"><span data-stu-id="08329-214">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="08329-216">2. Adicionar o componente de demonstração do tutorial de acompanhamento de olho (script) a todos os objetos de destino</span><span class="sxs-lookup"><span data-stu-id="08329-216">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="08329-217">Com todos os **objetos filho** ainda selecionados, use o botão **Adicionar componente** para adicionar o componente **demonstração do tutorial de acompanhamento de olho (script)** a todos os objetos filho:</span><span class="sxs-lookup"><span data-stu-id="08329-217">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="08329-219">O componente de destino de acompanhamento de olho (script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="08329-219">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="08329-220">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="08329-220">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="08329-221">3. implementar o ao examinar o evento de destino</span><span class="sxs-lookup"><span data-stu-id="08329-221">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="08329-222">Na janela hierarquia, selecione o objeto **queijo** e crie um novo **ao examinar o evento Target ()** , configure o objeto **queijo** para receber o evento e defina **EyeTrackingTutorialDemo. RotateTarget** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="08329-222">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="08329-224">**Repita** para cada um dos objetos filho no 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="08329-224">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="08329-225">Para obter um lembrete sobre como implementar eventos, consulte as instruções [gestos de acompanhamento de mão e botões](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) que podem interagir.</span><span class="sxs-lookup"><span data-stu-id="08329-225">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="08329-226">4. implementar o no evento selecionado</span><span class="sxs-lookup"><span data-stu-id="08329-226">4. Implement the On Selected event</span></span>

<span data-ttu-id="08329-227">Na janela hierarquia, selecione o objeto **queijo** e crie um novo no evento **selecionado ()** , configure o objeto **queijo** para receber o evento e defina **EyeTrackingTutorialDemo. RotateTarget** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="08329-227">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="08329-229">**Repita** para cada um dos objetos filho no 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="08329-229">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="08329-230">5. habilitar o controle de olho simulado para simulações no editor</span><span class="sxs-lookup"><span data-stu-id="08329-230">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="08329-231">Na janela hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, selecione a guia **entrada** , expanda a seção **provedores de dados de entrada** e, em seguida, a seção serviço de simulação de **entrada** e clone o **DefaultMixedRealityInputSimulationProfile** para substituí-lo pelo seu próprio perfil de **simulação de entrada**personalizável:</span><span class="sxs-lookup"><span data-stu-id="08329-231">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="08329-233">Para obter um lembrete sobre como clonar perfis MRTK, você pode consultar as instruções [como configurar os perfis do kit de ferramentas de realidade misturada](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .</span><span class="sxs-lookup"><span data-stu-id="08329-233">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="08329-234">Na seção **simulação de olho** , marque a caixa de seleção **simular posição de olho** para habilitar a simulação de acompanhamento ocular:</span><span class="sxs-lookup"><span data-stu-id="08329-234">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="08329-236">Se agora você inserir o modo de jogo, poderá testar os efeitos de rotação e blip que você implementou ajustando a exibição para que o cursor atinja um dos objetos e o comando de interação manual ou de fala para selecionar o objeto:</span><span class="sxs-lookup"><span data-stu-id="08329-236">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="08329-238">Se você não usou o DefaultHoloLens2ConfigurationProfile para clonar seu perfil de configuração MRTK personalizável, conforme instruído nas instruções de [Configurar o kit de ferramentas da realidade misturada, o](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) controle de olhos pode não ser habilitado em seu projeto e precisará ser ativado.</span><span class="sxs-lookup"><span data-stu-id="08329-238">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="08329-239">Para isso, você pode consultar as instruções de [introdução ao acompanhamento de olho em MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) .</span><span class="sxs-lookup"><span data-stu-id="08329-239">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="08329-240">6. habilitar a entrada olhar nos recursos de aplicativo do projeto do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="08329-240">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="08329-241">Antes de criar e implantar seu aplicativo do Visual Studio em seu dispositivo, a entrada olhar deve ser habilitada nos recursos de aplicativo do projeto.</span><span class="sxs-lookup"><span data-stu-id="08329-241">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="08329-242">Para isso, você pode seguir as instruções [testando seu aplicativo Unity em um HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) .</span><span class="sxs-lookup"><span data-stu-id="08329-242">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="08329-243">Parabéns</span><span class="sxs-lookup"><span data-stu-id="08329-243">Congratulations</span></span>

<span data-ttu-id="08329-244">Você adicionou com êxito os recursos básicos de acompanhamento de olho ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08329-244">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="08329-245">Essas ações são apenas o começo de um mundo de possibilidades com o acompanhamento ocular.</span><span class="sxs-lookup"><span data-stu-id="08329-245">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="08329-246">Neste tutorial, você também aprendeu sobre outros recursos de entrada avançados, como comandos de voz e gestos de panorâmica.</span><span class="sxs-lookup"><span data-stu-id="08329-246">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="08329-247">Próxima lição: 7. criando um aplicativo de exemplo de módulo lunar</span><span class="sxs-lookup"><span data-stu-id="08329-247">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)

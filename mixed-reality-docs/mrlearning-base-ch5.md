---
title: Tutoriais de introdução – 6. Explorar as opções avançadas de entrada
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376083"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="10fec-105">6. Explorar as opções avançadas de entrada</span><span class="sxs-lookup"><span data-stu-id="10fec-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="10fec-106">Neste tutorial, você explorará várias algumas opções avançadas de entrada para o HoloLens 2, incluindo o uso de comandos de voz, o gesto de panorâmica e o acompanhamento ocular.</span><span class="sxs-lookup"><span data-stu-id="10fec-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="10fec-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="10fec-107">Objectives</span></span>

* <span data-ttu-id="10fec-108">Disparar eventos usando palavras-chave e comandos de voz</span><span class="sxs-lookup"><span data-stu-id="10fec-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="10fec-109">Usar mãos rastreadas para aplicar a panorâmica de texturas e objetos 3D com mãos acompanhadas</span><span class="sxs-lookup"><span data-stu-id="10fec-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="10fec-110">Aproveitar funcionalidades de acompanhamento ocular do HoloLens 2 para selecionar objetos</span><span class="sxs-lookup"><span data-stu-id="10fec-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="10fec-111">Habilitando comandos de voz</span><span class="sxs-lookup"><span data-stu-id="10fec-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="10fec-112">Nesta seção, você implementará um comando de fala para permitir que o usuário reproduza um som no objeto Octa.</span><span class="sxs-lookup"><span data-stu-id="10fec-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="10fec-113">Para isso, você criará um comando de fala e, em seguida, configurará o evento para que ele dispare a ação desejada quando a palavra-chave do comando de fala for falada.</span><span class="sxs-lookup"><span data-stu-id="10fec-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="10fec-114">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="10fec-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="10fec-115">Clonar o Perfil do Sistema de Entrada padrão</span><span class="sxs-lookup"><span data-stu-id="10fec-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="10fec-116">Clonar o Perfil de Comandos de Fala padrão</span><span class="sxs-lookup"><span data-stu-id="10fec-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="10fec-117">Criar um comando de fala</span><span class="sxs-lookup"><span data-stu-id="10fec-117">Create a new speech command</span></span>
4. <span data-ttu-id="10fec-118">Adicionar e configurar o componente do Manipulador de Entrada de Fala (Script)</span><span class="sxs-lookup"><span data-stu-id="10fec-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="10fec-119">Implementar o evento de Resposta para o comando de fala</span><span class="sxs-lookup"><span data-stu-id="10fec-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="10fec-120">1. Clonar o Perfil do Sistema de Entrada padrão</span><span class="sxs-lookup"><span data-stu-id="10fec-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="10fec-121">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, selecione a guia **Entrada** e clone o **DefaultHoloLens2InputSystemProfile** para substituí-lo por seu **Perfil do Sistema de Entrada** personalizável:</span><span class="sxs-lookup"><span data-stu-id="10fec-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="10fec-123">Para obter um lembrete de como clonar perfis MRTK, você pode consultar as instruções de [Como configurar os perfis do Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="10fec-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="10fec-124">2. Clonar o Perfil de Comandos de Fala padrão</span><span class="sxs-lookup"><span data-stu-id="10fec-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="10fec-125">Expanda a seção **Fala** e clone **DefaultMixedRealitySpeechCommandsProfile** para substituí-lo pelo seu **Perfil de Comandos de Fala** personalizável:</span><span class="sxs-lookup"><span data-stu-id="10fec-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="10fec-127">3. Criar um comando de fala</span><span class="sxs-lookup"><span data-stu-id="10fec-127">3. Create a new speech command</span></span>

<span data-ttu-id="10fec-128">Na seção **Comandos de Fala**, clique no botão **+ Adicionar Novo Comando de Fala** para adicionar um novo comando de fala à parte inferior da lista de comandos de fala existentes e, em seguida, no campo **Palavra-chave**, insira uma palavra ou frase adequada, por exemplo **Reproduzir Música**:</span><span class="sxs-lookup"><span data-stu-id="10fec-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="10fec-130">Se o computador não tiver um microfone e você quiser testar o comando de fala usando a simulação no editor, poderá atribuir um KeyCode ao comando de fala, o que permitirá que você o dispare quando a chave correspondente for pressionada.</span><span class="sxs-lookup"><span data-stu-id="10fec-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="10fec-131">4. Adicionar e configurar o componente do Manipulador de Entrada de Fala (Script)</span><span class="sxs-lookup"><span data-stu-id="10fec-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="10fec-132">Na janela Hierarquia, selecione o objeto **Octa** e adicione o componente **Manipulador de Entrada de Fala (Script)** ao objeto Octa.</span><span class="sxs-lookup"><span data-stu-id="10fec-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="10fec-133">Em seguida, desmarque a caixa de seleção **Foco É Necessário** para que o usuário não precise examinar o objeto Octa para disparar o comando de fala:</span><span class="sxs-lookup"><span data-stu-id="10fec-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="10fec-135">5. Implementar o evento de Resposta para o comando de fala</span><span class="sxs-lookup"><span data-stu-id="10fec-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="10fec-136">No componente Manipulador de Entrada de Fala (Script), clique no botão **+** pequeno para adicionar um elemento de palavra-chave à lista de palavras-chaves:</span><span class="sxs-lookup"><span data-stu-id="10fec-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="10fec-138">Clique no **Elemento 0** que acaba de ser criado para expandi-lo e, em seguida, na lista suspensa de **Palavra-chave**, escolha a palavra-chave **Reproduzir Música** criada anteriormente:</span><span class="sxs-lookup"><span data-stu-id="10fec-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="10fec-140">As palavras-chave na lista suspensa Palavras-chaves são preenchidas com base nas palavras-chaves definidas na lista Comandos de Fala no Perfil de Comandos de Fala.</span><span class="sxs-lookup"><span data-stu-id="10fec-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="10fec-141">Crie um evento **Response ()** , configure o objeto **Octa** para receber o evento, defina **AudioSource.PlayOneShot** como a ação a ser disparada e atribua um clipe de áudio adequado ao campo **Clipe de Áudio**, por exemplo, o clipe de áudio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="10fec-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="10fec-143">Para obter um lembrete sobre como implementar eventos e atribuir um clipe de áudio, você pode consultar as instruções para [Implementar o evento On Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event).</span><span class="sxs-lookup"><span data-stu-id="10fec-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="10fec-144">O gesto de panorâmica</span><span class="sxs-lookup"><span data-stu-id="10fec-144">The Pan Gesture</span></span>

<span data-ttu-id="10fec-145">O gesto de panorâmica é útil para rolagem usando o dedo ou a mão para rolar pelo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="10fec-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="10fec-146">Neste exemplo, você aprenderá primeiro a rolar uma interface do usuário 2D e, em seguida, expandir isso para poder rolar em uma coleção de objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="10fec-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="10fec-147">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="10fec-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="10fec-148">Criar um objeto Quad que pode ser usado para panorâmica</span><span class="sxs-lookup"><span data-stu-id="10fec-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="10fec-149">Adicionar o componente Tocável de Interação Próxima (Script)</span><span class="sxs-lookup"><span data-stu-id="10fec-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="10fec-150">Adicionar o componente de Zoom e Panorâmica da Interação Manual (Script)</span><span class="sxs-lookup"><span data-stu-id="10fec-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="10fec-151">Adicionar conteúdo 2D a ser rolado</span><span class="sxs-lookup"><span data-stu-id="10fec-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="10fec-152">Adicionar conteúdo 3D a ser rolado</span><span class="sxs-lookup"><span data-stu-id="10fec-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="10fec-153">Adicionar o componente Mover com Panorâmica (Script)</span><span class="sxs-lookup"><span data-stu-id="10fec-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="10fec-154">O componente Mover com Panorâmica (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="10fec-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="10fec-155">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="10fec-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="10fec-156">1. Criar um objeto Quad que pode ser usado para panorâmica</span><span class="sxs-lookup"><span data-stu-id="10fec-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="10fec-157">Na janela Hierarquia, clique com o botão direito do mouse em uma área vazia e selecione **Objeto 3D** > **Quad** para adicionar um quad à sua cena.</span><span class="sxs-lookup"><span data-stu-id="10fec-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="10fec-158">Dê a ele um nome adequado, por exemplo, **PanGesture** e posicione-o em uma localização adequada, por exemplo, X = 0, Y = -0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="10fec-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="10fec-160">Para um lembrete sobre como adicionar primitivos do Unity, como um quad 3D, à sua cena, veja as instruções para [Adicionar um cubo à cena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene).</span><span class="sxs-lookup"><span data-stu-id="10fec-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="10fec-161">Assim como acontece com qualquer outra interação, o gesto de panorâmica também requer um colisor.</span><span class="sxs-lookup"><span data-stu-id="10fec-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="10fec-162">Por padrão, um Quad tem um colisor de malha.</span><span class="sxs-lookup"><span data-stu-id="10fec-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="10fec-163">No entanto, o colisor de malha não é ideal, porque ele é extremamente fino e difícil de selecionar.</span><span class="sxs-lookup"><span data-stu-id="10fec-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="10fec-164">Para facilitar para o usuário interagir com o colisor, substituiremos o colisor de malha por um colisor de caixa.</span><span class="sxs-lookup"><span data-stu-id="10fec-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="10fec-165">Com o objeto PanGesture ainda selecionado, clique no ícone **Configurações** do componente **Colisor de Malha** e selecione **Remover Componente** para remover o colisor de malha:</span><span class="sxs-lookup"><span data-stu-id="10fec-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="10fec-167">Na janela Inspetor, use o botão **Adicionar Componente** para adicionar um **Colisor de Caixa**, então altere o **Tamanho** Z do Colisor de Caixa para 0,15 para aumentar a espessura do colisor da caixa:</span><span class="sxs-lookup"><span data-stu-id="10fec-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="10fec-169">2. Adicionar o componente Tocável de Interação Próxima (Script)</span><span class="sxs-lookup"><span data-stu-id="10fec-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="10fec-170">Com o objeto **PanGesture** ainda selecionado, adicione o componente **Tocável de Interação Próxima (Script)** ao objeto PanGesture e clique nos botões **Corrigir Limites** e **Corrigir Centro** para atualizar as propriedades Limites e Centro Local do Tocável de Interação Próxima (Script) para que correspondam ao BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="10fec-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="10fec-172">3. Adicionar o componente de Zoom e Panorâmica da Interação Manual (Script)</span><span class="sxs-lookup"><span data-stu-id="10fec-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="10fec-173">Com o objeto **PanGesture** ainda selecionado, adicione o componente **Panorâmica e Zoom da Interação da Mão (Script)** ao objeto PanGesture e marque a caixa de seleção **Bloqueio Horizontal** para permitir somente a rolagem vertical:</span><span class="sxs-lookup"><span data-stu-id="10fec-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="10fec-175">4. Adicionar conteúdo 2D a ser rolado</span><span class="sxs-lookup"><span data-stu-id="10fec-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="10fec-176">No painel Projeto, pesquise o material **PanContent** e, em seguida, clique e arraste-o para a propriedade de Elemento 0 do **Material** do Renderizador de Malha do objeto **PanGesture**:</span><span class="sxs-lookup"><span data-stu-id="10fec-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="10fec-178">Na janela Inspetor, expanda o componente de material **PanContent** que acaba de ser adicionado e, em seguida, altere seu valor Y de **Blocos** para 0,5 para que corresponda ao valor X e os blocos apareçam quadrados:</span><span class="sxs-lookup"><span data-stu-id="10fec-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="10fec-180">Se agora você entrar no modo de Jogo, poderá testar a rolagem do conteúdo 2D usando o gesto de panorâmica na simulação no editor:</span><span class="sxs-lookup"><span data-stu-id="10fec-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="10fec-182">5. Adicionar conteúdo 3D a ser rolado</span><span class="sxs-lookup"><span data-stu-id="10fec-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="10fec-183">Na janela Hierarquia, **crie quatro cubos** como objetos filho do objeto **PanGesture** e defina sua **Escala** de Transformação para X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="10fec-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="10fec-185">Para espaçar os cubos uniformemente e economizar algum tempo, adicione o componente **Coleção de Objetos de Grade (Script)** ao objeto pai dos cubos, ou seja, o objeto **PanGesture**, e configure a Coleção de Objetos de grade (Script) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="10fec-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="10fec-186">Altere **Número de Linhas** para 1 para alinhar todos os cubos em uma só linha</span><span class="sxs-lookup"><span data-stu-id="10fec-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="10fec-187">Altere **Largura da Célula** para 0,25 para espaçar os cubos dentro da linha</span><span class="sxs-lookup"><span data-stu-id="10fec-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="10fec-188">Em seguida, clique no botão **Atualizar Coleção** para aplicar a nova configuração:</span><span class="sxs-lookup"><span data-stu-id="10fec-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="10fec-190">6. Adicionar o componente Mover com Panorâmica (Script)</span><span class="sxs-lookup"><span data-stu-id="10fec-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="10fec-191">Na janela Hierarquia, selecione todos os **Objetos filho de cubo**, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Mover Com Panorâmica (Script)** a todos os cubos:</span><span class="sxs-lookup"><span data-stu-id="10fec-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="10fec-193">Para um lembrete de como selecionar vários objetos na janela Hierarquia, você pode consultar as instruções para [Adicionar o componente Manipulador de Manipulação (Script) a todos os objetos](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects).</span><span class="sxs-lookup"><span data-stu-id="10fec-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="10fec-194">Com todos os cubos ainda selecionados, clique e arraste o objeto **PanGesture** para o campo **Fonte de Entrada Panorâmica**:</span><span class="sxs-lookup"><span data-stu-id="10fec-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="10fec-196">O componente Mover com Pan (Script) em cada cubo escuta o evento de Panorâmica Atualizada enviado pelo componente HandInteractionPanZoom (Script) no objeto PanGesture, que você atribuiu como a Fonte de Entrada Panorâmica na etapa acima e atualiza a posição de cada cubo de acordo.</span><span class="sxs-lookup"><span data-stu-id="10fec-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="10fec-197">Na janela Hierarquia, selecione o objeto **PanGesture** e, em seguida, no inspetor, **desmarque** caixa de seleção **Renderizador de Malha** para desabilitar o componente Renderizador de Malha:</span><span class="sxs-lookup"><span data-stu-id="10fec-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="10fec-199">Se agora você entrar no modo de Jogo, poderá testar a rolagem do conteúdo 3D usando o gesto de panorâmica na simulação no editor:</span><span class="sxs-lookup"><span data-stu-id="10fec-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="10fec-201">Acompanhamento Ocular</span><span class="sxs-lookup"><span data-stu-id="10fec-201">Eye Tracking</span></span>

<span data-ttu-id="10fec-202">Nesta seção, você vai explorar como habilitar o Acompanhamento Ocular em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="10fec-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="10fec-203">Para este exemplo, você implementará a funcionalidade para fazer cada objeto na 3DObjectCollection girar lentamente enquanto estiver sendo olhado pelo usuário, bem como disparará um efeito de blip quando o objeto que está sendo observado for selecionado por toque no ar ou comando de fala.</span><span class="sxs-lookup"><span data-stu-id="10fec-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="10fec-204">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="10fec-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="10fec-205">Adicione o componente de Destino de Acompanhamento Ocular (Script) a todos os objetos de destino</span><span class="sxs-lookup"><span data-stu-id="10fec-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="10fec-206">Adicione o componente de Demonstração do Tutorial de Acompanhamento Ocular (Script) a todos os objetos de destino</span><span class="sxs-lookup"><span data-stu-id="10fec-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="10fec-207">Implementar o evento Ao Olhar para o Alvo</span><span class="sxs-lookup"><span data-stu-id="10fec-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="10fec-208">Implementar o evento Quando Selecionado</span><span class="sxs-lookup"><span data-stu-id="10fec-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="10fec-209">Habilitar o Acompanhamento Ocular simulado para simulações no editor</span><span class="sxs-lookup"><span data-stu-id="10fec-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="10fec-210">Habilitar Entrada de Olhar nas funcionalidades do aplicativo do projeto do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10fec-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="10fec-211">1. Adicione o componente de Destino de Acompanhamento Ocular (Script) a todos os objetos de destino</span><span class="sxs-lookup"><span data-stu-id="10fec-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="10fec-212">Na janela Hierarquia, expanda o objeto **3DObjectCollection** e selecione todos os **objetos filho** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Alvo de Acompanhamento Ocular (Script)** a todos os objetos filho:</span><span class="sxs-lookup"><span data-stu-id="10fec-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="10fec-214">Com todos os **objetos filho** ainda selecionados, configure o componente **Alvo do Acompanhamento Ocular (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="10fec-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="10fec-215">Altere **Selecionar Ação** para **Selecionar** para definir a ação de toque no ar para esse objeto como Selecionar</span><span class="sxs-lookup"><span data-stu-id="10fec-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="10fec-216">Expanda **Seleção de Voz** e defina o **Tamanho** da lista de comandos de voz como 1 e, em seguida, na nova lista de elementos exibida, altere **Elemento 0** para **Selecionar** para definir a ação de comando de fala para esse objeto como Selecionar</span><span class="sxs-lookup"><span data-stu-id="10fec-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="10fec-218">2. Adicione o componente de Demonstração do Tutorial de Acompanhamento Ocular (Script) a todos os objetos de destino</span><span class="sxs-lookup"><span data-stu-id="10fec-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="10fec-219">Com todos os **objetos filho** ainda selecionados, use o botão **Adicionar Componente** para adicionar o componente **Demonstração do Tutorial de Acompanhamento Ocular (Script)** a todos os objetos filho:</span><span class="sxs-lookup"><span data-stu-id="10fec-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="10fec-221">O componente Alvo de Acompanhamento Ocular (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="10fec-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="10fec-222">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="10fec-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="10fec-223">3. Implementar o evento Ao Olhar para o Alvo</span><span class="sxs-lookup"><span data-stu-id="10fec-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="10fec-224">Na janela Hierarquia, selecione o objeto **Queijo**, crie um evento **Ao Olhar para o Alvo ()** , configure o objeto **Queijo** para receber o evento e defina **EyeTrackingTutorialDemo.RotateTarget** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="10fec-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="10fec-226">**Repita** para cada um dos objetos filho na 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="10fec-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="10fec-227">Para obter um lembrete sobre como implementar eventos, você pode consultar as instruções de [Gestos de acompanhamento da mão e botões interativos](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="10fec-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="10fec-228">4. Implementar o evento Quando Selecionado</span><span class="sxs-lookup"><span data-stu-id="10fec-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="10fec-229">Na janela Hierarquia, selecione o objeto **Queijo**, crie um evento **No Selecionado ()** , configure o objeto **Queijo** para receber o evento e defina **EyeTrackingTutorialDemo.BlipTarget** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="10fec-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="10fec-231">**Repita** para cada um dos objetos filho na 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="10fec-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="10fec-232">5. Habilitar o Acompanhamento Ocular simulado para simulações no editor</span><span class="sxs-lookup"><span data-stu-id="10fec-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="10fec-233">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, em seguida, na janela Inspetor, selecione a guia **Entrada**, expanda a seção **Provedores de Dados de Entrada** e a seção **Serviço de Simulação de Entrada** e clone o **DefaultMixedRealityInputSimulationProfile** para substituí-lo pelo seu **Perfil de Simulação de Entrada** personalizável:</span><span class="sxs-lookup"><span data-stu-id="10fec-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="10fec-235">Para obter um lembrete de como clonar perfis MRTK, você pode consultar as instruções de [Como configurar os perfis do Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="10fec-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="10fec-236">Na seção **Simulação de Olho**, marque a caixa de seleção **Simular a Posição do Olho** para habilitar a simulação de acompanhamento ocular:</span><span class="sxs-lookup"><span data-stu-id="10fec-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="10fec-238">Se agora você entrar no modo de Jogo, poderá testar os efeitos de rotação e blip que você implementou ajustando a exibição para que o cursor atinja um dos objetos e o comando de interação manual ou de fala para selecionar o objeto:</span><span class="sxs-lookup"><span data-stu-id="10fec-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="10fec-240">Se você não tiver usado o DefaultHoloLens2ConfigurationProfile para clonar seu perfil de configuração MRTK personalizável, conforme orientado nas instruções para [Configurar o Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), o acompanhamento ocular poderá não estar habilitado em seu projeto e precisará ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="10fec-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="10fec-241">Para isso, você pode consultar as instruções de [Introdução ao acompanhamento ocular no MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html).</span><span class="sxs-lookup"><span data-stu-id="10fec-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="10fec-242">6. Habilitar Entrada de Olhar nas funcionalidades do aplicativo do projeto do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10fec-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="10fec-243">Antes de criar e implantar seu aplicativo do Visual Studio em seu dispositivo, a Entrada de Olhar deve ser habilitada nos recursos de aplicativo do projeto.</span><span class="sxs-lookup"><span data-stu-id="10fec-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="10fec-244">Para isso, você pode seguir as instruções em [Testar seu aplicativo Unity em um HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="10fec-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="10fec-245">Parabéns</span><span class="sxs-lookup"><span data-stu-id="10fec-245">Congratulations</span></span>

<span data-ttu-id="10fec-246">Você adicionou com êxito as funcionalidades de acompanhamento ocular ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10fec-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="10fec-247">Essas ações são apenas o começo de um mundo de possibilidades com o acompanhamento ocular.</span><span class="sxs-lookup"><span data-stu-id="10fec-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="10fec-248">Neste tutorial, você também aprendeu sobre outros recursos de entrada avançados, como comandos de voz e gestos de panorâmica.</span><span class="sxs-lookup"><span data-stu-id="10fec-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="10fec-249">Próxima lição: 7. Criar um aplicativo de exemplo do módulo Lunar</span><span class="sxs-lookup"><span data-stu-id="10fec-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)

---
title: Tutoriais de introdução-7. Criando um aplicativo de exemplo de módulo lunar
description: Nesta lição, você combinará vários conceitos aprendidos das lições anteriores para criar uma experiência de amostra exclusiva.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926516"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="56a64-105">7. criando um aplicativo de exemplo de módulo lunar</span><span class="sxs-lookup"><span data-stu-id="56a64-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="56a64-106">Neste tutorial, vários conceitos são combinados de lições anteriores para criar uma experiência de amostra exclusiva.</span><span class="sxs-lookup"><span data-stu-id="56a64-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="56a64-107">Você aprenderá a criar um aplicativo de assembly de módulo lunar, no qual um usuário precisa usar mãos controladas para pegar partes de módulo lunares e tentar montar um módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="56a64-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="56a64-108">Usamos botões pressionáveis para alternar dicas de posicionamento, redefinir nossa experiência e iniciar nosso módulo lunar no espaço!</span><span class="sxs-lookup"><span data-stu-id="56a64-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="56a64-109">Em Tutoriais futuros, continuaremos a criar essa experiência, que inclui casos avançados de uso de vários usuários que aproveitam as âncoras espaciais do Azure para o alinhamento espacial.</span><span class="sxs-lookup"><span data-stu-id="56a64-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="56a64-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="56a64-110">Objectives</span></span>

- <span data-ttu-id="56a64-111">Combine vários conceitos das lições anteriores para criar uma experiência exclusiva</span><span class="sxs-lookup"><span data-stu-id="56a64-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="56a64-112">Saiba como alternar objetos</span><span class="sxs-lookup"><span data-stu-id="56a64-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="56a64-113">Dispare eventos complexos usando os botões pressionáveis</span><span class="sxs-lookup"><span data-stu-id="56a64-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="56a64-114">Use força e física de corpo rígido</span><span class="sxs-lookup"><span data-stu-id="56a64-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="56a64-115">Explore o uso de dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="56a64-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="56a64-116">Instruções</span><span class="sxs-lookup"><span data-stu-id="56a64-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="56a64-117">Configuração do módulo lunar</span><span class="sxs-lookup"><span data-stu-id="56a64-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="56a64-118">Nesta seção, apresentamos os vários componentes necessários para criar nossa experiência de exemplo.</span><span class="sxs-lookup"><span data-stu-id="56a64-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="56a64-119">Adicione o assembly de módulo lunar pré-fabricado à sua cena base.</span><span class="sxs-lookup"><span data-stu-id="56a64-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="56a64-120">Para fazer isso, na guia projeto, navegue até ativos > BaseModuleAssets > pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="56a64-120">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="56a64-121">Você verá duas pré-fabricados do iniciador de Rocket, arrastar o Rocket Launcher_Tutorial pré-fabricado para sua cena e posicioná-lo como desejar.</span><span class="sxs-lookup"><span data-stu-id="56a64-121">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="56a64-122">O Rocket Launcher_Complete pré-fabricado é o iniciador concluído, fornecido para referência.</span><span class="sxs-lookup"><span data-stu-id="56a64-122">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="56a64-124">Se você expandir o objeto de jogo do Rocket Launcher_Tutorial em sua hierarquia e expandir ainda mais o objeto do módulo lunar, encontrará vários objetos filho que têm um material chamado "x-ray".</span><span class="sxs-lookup"><span data-stu-id="56a64-124">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="56a64-125">O material "x-ray" permite uma cor levemente translúcida que será usada como dicas de posicionamento para o usuário.</span><span class="sxs-lookup"><span data-stu-id="56a64-125">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

    ![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="56a64-127">Há cinco partes para o módulo lunar com o qual o usuário irá interagir, conforme mostrado na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="56a64-127">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="56a64-128">O compartimento da Rover</span><span class="sxs-lookup"><span data-stu-id="56a64-128">The Rover Enclosure</span></span>
    2. <span data-ttu-id="56a64-129">O tanque de combustível</span><span class="sxs-lookup"><span data-stu-id="56a64-129">The Fuel Tank</span></span>
    3. <span data-ttu-id="56a64-130">A célula de energia</span><span class="sxs-lookup"><span data-stu-id="56a64-130">The Energy Cell</span></span>
    4. <span data-ttu-id="56a64-131">O Portal de Encaixe</span><span class="sxs-lookup"><span data-stu-id="56a64-131">The Docking Portal</span></span>
    5. <span data-ttu-id="56a64-132">O sensor externo</span><span class="sxs-lookup"><span data-stu-id="56a64-132">The External sensor</span></span>

    ![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="56a64-134">Os nomes de objeto do jogo que você vê em sua hierarquia da cena base não correspondem aos nomes dos objetos na cena.</span><span class="sxs-lookup"><span data-stu-id="56a64-134">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="56a64-135">Adicione uma fonte de áudio ao objeto de jogo LunarModule.</span><span class="sxs-lookup"><span data-stu-id="56a64-135">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="56a64-136">Verifique se o LunarModule está selecionado na sua hierarquia de cena e clique em Adicionar componente.</span><span class="sxs-lookup"><span data-stu-id="56a64-136">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="56a64-137">Pesquise fonte de áudio e adicione-a ao objeto Game.</span><span class="sxs-lookup"><span data-stu-id="56a64-137">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="56a64-138">Deixe o campo AudioClip em branco por enquanto, mas altere a configuração de mistura especial de 0 para 1 para habilitar o áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="56a64-138">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="56a64-139">Você usará essa fonte de áudio para reproduzir o som de inicialização mais tarde.</span><span class="sxs-lookup"><span data-stu-id="56a64-139">You will use this audio source to play the launching sound later.</span></span>

    ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="56a64-141">Adicione as dicas de posicionamento de alternância de script.</span><span class="sxs-lookup"><span data-stu-id="56a64-141">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="56a64-142">Clique em Adicionar componente e procure alternar dicas de posicionamento.</span><span class="sxs-lookup"><span data-stu-id="56a64-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="56a64-143">Esse é um script personalizado que permite ativar e desativar as dicas translúcidas (objetos com o material x-ray), conforme mencionado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="56a64-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="56a64-145">Como temos cinco objetos, digite "5" para o tamanho da matriz de objetos do jogo.</span><span class="sxs-lookup"><span data-stu-id="56a64-145">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="56a64-146">Em seguida, você verá cinco novos elementos aparecerem.</span><span class="sxs-lookup"><span data-stu-id="56a64-146">You will then see five new elements appear.</span></span>

    ![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="56a64-148">Arraste cada um dos objetos translúcidas para todas as caixas nome (objeto de jogo).</span><span class="sxs-lookup"><span data-stu-id="56a64-148">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="56a64-149">Arraste os seguintes objetos do módulo lunar em sua cena para os campos da matriz de objetos, conforme mostrado na imagem acima:</span><span class="sxs-lookup"><span data-stu-id="56a64-149">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="56a64-151">O script alternar dicas de posicionamento agora está configurado, o que nos permite ativar e desativar as dicas.</span><span class="sxs-lookup"><span data-stu-id="56a64-151">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="56a64-152">Adicione o script abrir módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="56a64-152">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="56a64-153">Clique no botão Adicionar componente, pesquise "Iniciar módulo lunar" e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="56a64-153">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="56a64-154">Esse script inicia o módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="56a64-154">This script launches the lunar module.</span></span> <span data-ttu-id="56a64-155">Quando pressionamos um botão configurado, ele adiciona uma força ascendente ao componente de corpo rígido do módulo lunar e faz com que o módulo seja iniciado para cima.</span><span class="sxs-lookup"><span data-stu-id="56a64-155">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="56a64-156">Se você estiver em um local fechado, o módulo lunar pode bater na malha de teto.</span><span class="sxs-lookup"><span data-stu-id="56a64-156">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="56a64-157">Se você estiver em uma área com grandes tetos ou sem teto, o módulo lunar irá para o espaço indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="56a64-157">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="56a64-159">Ajuste o impulso para que o módulo lunar voe para cima sem problemas.</span><span class="sxs-lookup"><span data-stu-id="56a64-159">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="56a64-160">Tente um valor de 0,01.</span><span class="sxs-lookup"><span data-stu-id="56a64-160">Try a value of 0.01.</span></span> <span data-ttu-id="56a64-161">Deixe o campo "Rb" em branco.</span><span class="sxs-lookup"><span data-stu-id="56a64-161">Leave the "Rb" field blank.</span></span> <span data-ttu-id="56a64-162">RB significa corpo rígido e este campo será preenchido automaticamente durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="56a64-162">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="56a64-164">Visão geral das partes do módulo lunar</span><span class="sxs-lookup"><span data-stu-id="56a64-164">Lunar Module Parts overview</span></span>

<span data-ttu-id="56a64-165">O objeto pai das partes do módulo lunar é a coleção dos objetos com os quais o usuário interage.</span><span class="sxs-lookup"><span data-stu-id="56a64-165">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="56a64-166">Os nomes de objeto do jogo com a cena rotulada nomes entre parênteses, são fornecidos na lista abaixo:</span><span class="sxs-lookup"><span data-stu-id="56a64-166">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="56a64-167">Mochila (célula de energia)</span><span class="sxs-lookup"><span data-stu-id="56a64-167">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="56a64-168">GasTank (tanque de combustível)</span><span class="sxs-lookup"><span data-stu-id="56a64-168">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="56a64-169">Corpo Superior Esquerdo (compartimento da Rover)</span><span class="sxs-lookup"><span data-stu-id="56a64-169">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="56a64-170">Nariz (Portal de Encaixe)</span><span class="sxs-lookup"><span data-stu-id="56a64-170">Nose (Docking Portal)</span></span>
- <span data-ttu-id="56a64-171">Giro Esquerdo (sensor externo)</span><span class="sxs-lookup"><span data-stu-id="56a64-171">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="56a64-172">Observe que cada um desses objetos tem um manipulador de manipulação, conforme explicado na lição 4.</span><span class="sxs-lookup"><span data-stu-id="56a64-172">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="56a64-173">Esse recurso permite que os usuários obtenham e manipulem o objeto.</span><span class="sxs-lookup"><span data-stu-id="56a64-173">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="56a64-174">Observe também que a configuração, tipo de manipulação de duas mãos, está definida como mover e girar.</span><span class="sxs-lookup"><span data-stu-id="56a64-174">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="56a64-175">Essa opção só permite que o usuário mova o objeto e não altere seu tamanho, que é a funcionalidade desejada para um aplicativo de assembly.</span><span class="sxs-lookup"><span data-stu-id="56a64-175">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="56a64-176">Além disso, a manipulação distante está desmarcada para permitir apenas a interação direta de partes do módulo.</span><span class="sxs-lookup"><span data-stu-id="56a64-176">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="56a64-178">O script de demonstração do assembly de parte (mostrado acima) é o script que gerencia os objetos que o usuário coloca no módulo lunar pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="56a64-178">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="56a64-179">O campo objeto a ser colocado é a transformação selecionada, conforme mostrado na imagem acima, o tanque de mochila/combustível associado ao objeto ao qual ele se conecta.</span><span class="sxs-lookup"><span data-stu-id="56a64-179">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="56a64-180">As configurações de distância aproximada e distante determinam a proximidade com a qual as partes se encaixam ou podem ser lançadas.</span><span class="sxs-lookup"><span data-stu-id="56a64-180">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="56a64-181">Por exemplo, o tanque de mochila/combustível precisa ter 0,1 unidades fora do módulo lunar antes que ele se encaixe no local.</span><span class="sxs-lookup"><span data-stu-id="56a64-181">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="56a64-182">A configuração de distância distante define o local onde o objeto pode ser antes que ele possa ser desanexado do módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="56a64-182">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="56a64-183">Nesse caso, a mão do usuário precisa pegar a mochila/tanque de combustível e puxá-la para 0,2 unidades de distância do módulo lunar para remover.</span><span class="sxs-lookup"><span data-stu-id="56a64-183">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="56a64-184">O objeto de dica de ferramenta é o rótulo de dica de ferramenta na cena.</span><span class="sxs-lookup"><span data-stu-id="56a64-184">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="56a64-185">Quando os objetos são encaixados no lugar, o rótulo é desabilitado.</span><span class="sxs-lookup"><span data-stu-id="56a64-185">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="56a64-186">A fonte de áudio é automaticamente capturada.</span><span class="sxs-lookup"><span data-stu-id="56a64-186">The Audio Source is automatically grabbed.</span></span>

### <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="56a64-187">Configurando o botão de dicas de posicionamento</span><span class="sxs-lookup"><span data-stu-id="56a64-187">Configuring the Placement Hints button</span></span>

<span data-ttu-id="56a64-188">Na [lição 2](mrlearning-base-ch2.md), você aprendeu a colocar e configurar botões para fazer coisas como alterar a cor de um item ou fazê-lo tocar um som quando enviado por push.</span><span class="sxs-lookup"><span data-stu-id="56a64-188">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="56a64-189">Continuaremos a usar esses princípios conforme configuramos os botões para alternar dicas de posicionamento.</span><span class="sxs-lookup"><span data-stu-id="56a64-189">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="56a64-190">O objetivo é configurar nosso botão para que sempre que o usuário pressionar o botão de dica de posicionamento, ele alterne a visibilidade das dicas de posicionamento translúcidas.</span><span class="sxs-lookup"><span data-stu-id="56a64-190">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="56a64-191">Mova o módulo lunar para o slot somente de tempo de execução vazio no painel Inspetor enquanto o objeto de dicas de posicionamento estiver selecionado na sua hierarquia de cena base.</span><span class="sxs-lookup"><span data-stu-id="56a64-191">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="56a64-193">Clique na lista suspensa nenhuma função.</span><span class="sxs-lookup"><span data-stu-id="56a64-193">Click the No Function dropdown list.</span></span> <span data-ttu-id="56a64-194">Vá até TogglePlacementHints e selecione ToggleGameObjects () no menu.</span><span class="sxs-lookup"><span data-stu-id="56a64-194">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="56a64-195">ToggleGameObjects () alterna as dicas de posicionamento ativadas e desativadas para que fiquem visíveis ou invisíveis sempre que o botão for pressionado.</span><span class="sxs-lookup"><span data-stu-id="56a64-195">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a><span data-ttu-id="56a64-197">Configurando o botão redefinir</span><span class="sxs-lookup"><span data-stu-id="56a64-197">Configuring the Reset button</span></span>

<span data-ttu-id="56a64-198">Haverá situações em que o usuário cometer um erro, emitirá acidentalmente o objeto para longe ou apenas deseja redefinir a experiência.</span><span class="sxs-lookup"><span data-stu-id="56a64-198">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="56a64-199">O botão redefinir adiciona a capacidade de reiniciar a experiência.</span><span class="sxs-lookup"><span data-stu-id="56a64-199">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="56a64-200">Selecione o botão redefinir.</span><span class="sxs-lookup"><span data-stu-id="56a64-200">Select the Reset button.</span></span> <span data-ttu-id="56a64-201">Na cena base, ele é chamado de ResetRoundButton.</span><span class="sxs-lookup"><span data-stu-id="56a64-201">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="56a64-202">Arraste o módulo lunar da hierarquia de cena base para o slot vazio em botão pressionado no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="56a64-202">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="56a64-204">Selecione o menu suspenso sem função e focalize LaunchLunarModule e, em seguida, selecione resetModule ().</span><span class="sxs-lookup"><span data-stu-id="56a64-204">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="56a64-206">Observe que, por padrão, o gameobject. BroadcastMessage é configurado como ResetPlacement.</span><span class="sxs-lookup"><span data-stu-id="56a64-206">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="56a64-207">Isso transmite uma mensagem chamada ResetPlacement para cada objeto filho do RocketLauncher_Tutorial.</span><span class="sxs-lookup"><span data-stu-id="56a64-207">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="56a64-208">Qualquer objeto que tenha um método para ResetPlacement () responde a essa mensagem redefinindo sua posição.</span><span class="sxs-lookup"><span data-stu-id="56a64-208">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

### <a name="configuring-the-launch-button"></a><span data-ttu-id="56a64-209">Configurando o botão iniciar</span><span class="sxs-lookup"><span data-stu-id="56a64-209">Configuring the Launch button</span></span>

<span data-ttu-id="56a64-210">Esta seção explica como configurar o botão Iniciar, que permite ao usuário pressionar o botão e iniciar o módulo lunar no espaço.</span><span class="sxs-lookup"><span data-stu-id="56a64-210">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="56a64-211">Selecione o botão Iniciar.</span><span class="sxs-lookup"><span data-stu-id="56a64-211">Select the Launch button.</span></span> <span data-ttu-id="56a64-212">Na cena base, ele é chamado de LaunchRoundButton.</span><span class="sxs-lookup"><span data-stu-id="56a64-212">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="56a64-213">Arraste o módulo lunar para o slot vazio em extremidade de toque no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="56a64-213">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="56a64-215">Selecione o menu suspenso sem função e focalize LaunchLunarModule e selecione StopThruster ().</span><span class="sxs-lookup"><span data-stu-id="56a64-215">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="56a64-216">Isso controla a quantidade de Thrustmaster que o usuário deseja dar ao módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="56a64-216">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="56a64-218">Arraste o módulo lunar da hierarquia de cena base para o slot vazio em botão pressionado no painel de Inspetor.</span><span class="sxs-lookup"><span data-stu-id="56a64-218">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="56a64-219">Clique no menu suspenso sem função e, em seguida, em LaunchLunarModule e selecione StartThruster ().</span><span class="sxs-lookup"><span data-stu-id="56a64-219">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="56a64-221">Adicione música ao módulo lunar para que a música seja reproduzida quando o Rocket retirar.</span><span class="sxs-lookup"><span data-stu-id="56a64-221">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="56a64-222">Para fazer isso, arraste o módulo lunar para o próximo slot vazio em botão pressionado ().</span><span class="sxs-lookup"><span data-stu-id="56a64-222">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="56a64-223">Selecione o menu suspenso sem função, passe o mouse sobre Audioname e selecione PlayOneShot (AudioClip).</span><span class="sxs-lookup"><span data-stu-id="56a64-223">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="56a64-224">Fique à vontade para explorar a variedade de sons incluídos no MRTK.</span><span class="sxs-lookup"><span data-stu-id="56a64-224">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="56a64-225">Neste exemplo, vamos usar "MRTK_Gem".</span><span class="sxs-lookup"><span data-stu-id="56a64-225">In this example, we'll use "MRTK_Gem."</span></span>

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a><span data-ttu-id="56a64-227">Parabéns</span><span class="sxs-lookup"><span data-stu-id="56a64-227">Congratulations</span></span>

<span data-ttu-id="56a64-228">Você configurou totalmente este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="56a64-228">You have fully configured this application.</span></span> <span data-ttu-id="56a64-229">Agora, ao pressionar reproduzir, você pode montar totalmente o módulo lunar, alternar dicas, iniciar o módulo lunar e redefini-lo para iniciar novamente.</span><span class="sxs-lookup"><span data-stu-id="56a64-229">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>

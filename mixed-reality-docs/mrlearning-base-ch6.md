---
title: Tutoriais de introdução – 7. Criar um aplicativo de exemplo do módulo Lunar
description: Nesta lição, você vai combinar vários conceitos aprendidos em lições anteriores para criar uma experiência de exemplo exclusiva.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031552"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="6ad26-105">7. Criar um aplicativo de exemplo do módulo Lunar</span><span class="sxs-lookup"><span data-stu-id="6ad26-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="6ad26-106">Neste tutorial, vários conceitos são combinados de lições anteriores para criar uma experiência de exemplo exclusiva.</span><span class="sxs-lookup"><span data-stu-id="6ad26-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="6ad26-107">Você aprenderá a criar um aplicativo de montagem de peça no qual um usuário precisa usar mãos acompanhadas para pegar peças e tentar montar um módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="6ad26-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="6ad26-108">Você usará botões pressionáveis para alternar as dicas de posicionamento entre ligadas e desligadas, redefinir a experiência e para lançar o módulo lunar no espaço!</span><span class="sxs-lookup"><span data-stu-id="6ad26-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="6ad26-109">Em tutoriais futuros, você continuará a aproveitar essa experiência, incluindo poderosos casos de uso de vários usuários que aproveitam as Âncoras Espaciais do Azure para fins de alinhamento espacial.</span><span class="sxs-lookup"><span data-stu-id="6ad26-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="6ad26-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6ad26-110">Objectives</span></span>

* <span data-ttu-id="6ad26-111">Combine vários conceitos das lições anteriores para criar uma experiência exclusiva</span><span class="sxs-lookup"><span data-stu-id="6ad26-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="6ad26-112">Saiba como alternar objetos</span><span class="sxs-lookup"><span data-stu-id="6ad26-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="6ad26-113">Dispare eventos complexos usando os botões pressionáveis</span><span class="sxs-lookup"><span data-stu-id="6ad26-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="6ad26-114">Use força e física de corpo rígido</span><span class="sxs-lookup"><span data-stu-id="6ad26-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="6ad26-115">Explore o uso de dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="6ad26-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="6ad26-116">Visão geral das peças do Módulo Lunar</span><span class="sxs-lookup"><span data-stu-id="6ad26-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="6ad26-117">Nesta seção, você criará um desafio de montagem de peças simples em que a meta do usuário é posicionar cinco peças distribuídas na mesa na localização correta do Módulo Lunar.</span><span class="sxs-lookup"><span data-stu-id="6ad26-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="6ad26-118">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="6ad26-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="6ad26-119">Adicionar o pré-fabricado do Lançador de Foguete à cena</span><span class="sxs-lookup"><span data-stu-id="6ad26-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="6ad26-120">Habilitar a manipulação de objetos para todas as partes</span><span class="sxs-lookup"><span data-stu-id="6ad26-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="6ad26-121">Adicionar e configurar o componente de Demonstração do Assembly de Parte (Script)</span><span class="sxs-lookup"><span data-stu-id="6ad26-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="6ad26-122">O componente de Demonstração de Montagem de Peças (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="6ad26-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="6ad26-123">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="6ad26-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="6ad26-124">1. Adicionar o pré-fabricado do Lançador de Foguete à cena</span><span class="sxs-lookup"><span data-stu-id="6ad26-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="6ad26-125">Na janela Projeto, navegue até a pasta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, arraste o pré-fabricado **RocketLauncher** para a janela Hierarquia para adicioná-lo à sua cena e posicione-o em uma localização adequada, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6ad26-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="6ad26-126">Posição da Transformação X = 1,5, Y = -0,4, Z = 0, de modo que esteja posicionada à direita do usuário na altura da cintura</span><span class="sxs-lookup"><span data-stu-id="6ad26-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="6ad26-127">Rotação da Transformação X = 0, Y = 180, Z = 0, de modo que os principais recursos da experiência estejam voltados para o usuário</span><span class="sxs-lookup"><span data-stu-id="6ad26-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="6ad26-129">2. Habilitar a manipulação de objetos para todas as partes</span><span class="sxs-lookup"><span data-stu-id="6ad26-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="6ad26-130">Na janela Hierarquia, localize o objeto RocketLauncher > **LunarModuleParts** e selecione todos os **objetos filho**, adicione o componente **Manipulador de Manipulação (Script)** e o componente **Capturável de Interação Próxima (Script)** , então configure o Manipulador de Manipulação (Script) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ad26-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="6ad26-131">Desmarque a caixa de seleção **Permitir Manipulação Distante** para permitir apenas interação próxima</span><span class="sxs-lookup"><span data-stu-id="6ad26-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="6ad26-132">Altere **Tipo de Manipulação de Duas Mãos** para **Mover Girar** para que o dimensionamento seja desabilitado</span><span class="sxs-lookup"><span data-stu-id="6ad26-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="6ad26-134">Como um lembrete, para obter instruções passo a passo sobre como implementar a manipulação de objetos, você pode consultar as instruções de [Como manipular objetos 3D](mrlearning-base-ch4.md#manipulating-3d-objects).</span><span class="sxs-lookup"><span data-stu-id="6ad26-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="6ad26-135">3. Adicionar e configurar o componente de Demonstração do Assembly de Parte (Script)</span><span class="sxs-lookup"><span data-stu-id="6ad26-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="6ad26-136">Com todos os objetos filho LunarModuleParts ainda selecionados, adicione um componente de **Fonte de Áudio** e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ad26-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="6ad26-137">Atribua um clipe de áudio adequado ao campo **AudioClip**, por exemplo, MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="6ad26-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="6ad26-138">Desmarque a caixa de seleção **Reproduzir ao Despertar** para que o clipe de áudio não seja automaticamente tocado quando a cena for carregada</span><span class="sxs-lookup"><span data-stu-id="6ad26-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="6ad26-139">Alterar **Mistura Espacial** para 1 para habilitar o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="6ad26-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="6ad26-141">Com todos os objetos filho LunarModuleParts ainda selecionados, adicione o componente **Demonstração do Assembly de Parte (Script)** :</span><span class="sxs-lookup"><span data-stu-id="6ad26-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="6ad26-143">Na janela Hierarquia, selecione o objeto **RoverEnclosure** e configure seu componente **Demonstração do Assembly de Parte (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ad26-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="6ad26-144">Para o campo **objeto a ser Posicionado**, atribua o objeto **em si**, neste caso, o objeto RoverEnclosure</span><span class="sxs-lookup"><span data-stu-id="6ad26-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="6ad26-145">Para o campo **Localização a Posicionar**, atribua o objeto **PlacementHints** correspondente, neste caso, o objeto RoverEnclosure_PlacementHint</span><span class="sxs-lookup"><span data-stu-id="6ad26-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="6ad26-146">Para o campo **Objeto de Dica de Ferramenta**, atribua a **Dica de Ferramenta** correspondente, neste caso, o objeto RoverEnclosure_ToolTip</span><span class="sxs-lookup"><span data-stu-id="6ad26-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="6ad26-147">Para o campo **Fonte de Áudio**, atribua o objeto **em si**, neste caso, o objeto RoverEnclosure</span><span class="sxs-lookup"><span data-stu-id="6ad26-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="6ad26-149">**Repita** para cada um dos outros objetos filho LunarModuleParts, ou seja, FuelTank, EnergyCell, DockingPortal e ExternalSensor.</span><span class="sxs-lookup"><span data-stu-id="6ad26-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="6ad26-150">Se agora você inserir o modo de Jogo e mover um "Objeto a Posicionar" próximo de seu "Localização a Posicionar" correspondente, você notará:</span><span class="sxs-lookup"><span data-stu-id="6ad26-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="6ad26-151">O objeto será encaixado no lugar e subordinado sob o objeto LunarModule para que ele passe a fazer parte do Módulo Lunar</span><span class="sxs-lookup"><span data-stu-id="6ad26-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="6ad26-152">A Fonte de Áudio no objeto reproduzirá o Clipe de Áudio atribuído na localização do objeto</span><span class="sxs-lookup"><span data-stu-id="6ad26-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="6ad26-153">O objeto da Dica de Ferramenta correspondente ficará oculto</span><span class="sxs-lookup"><span data-stu-id="6ad26-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="6ad26-155">Para um lembrete de como usar a simulação de entrada no editor, você pode consultar o guia [Como usar a simulação de entrada de mão no editor para testar uma cena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) no [Portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="6ad26-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="6ad26-156">Configuração do módulo lunar</span><span class="sxs-lookup"><span data-stu-id="6ad26-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="6ad26-157">Nesta seção, você adicionará mais recursos ao aplicativo Lançador de Foguete para que o usuário possa:</span><span class="sxs-lookup"><span data-stu-id="6ad26-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="6ad26-158">Interagir com o Módulo Lunar</span><span class="sxs-lookup"><span data-stu-id="6ad26-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="6ad26-159">Lançar o Módulo Lunar no espaço e tocar um som quando ele for lançado</span><span class="sxs-lookup"><span data-stu-id="6ad26-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="6ad26-160">Redefinir o aplicativo para que o Módulo Lunar e todas as partes sejam colocados de volta em sua posição original</span><span class="sxs-lookup"><span data-stu-id="6ad26-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="6ad26-161">Oculte as dicas de posicionamento para tornar o desafio de montagem de peças mais difícil.</span><span class="sxs-lookup"><span data-stu-id="6ad26-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="6ad26-162">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="6ad26-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="6ad26-163">Habilitar a manipulação de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="6ad26-163">Enable object manipulation</span></span>
2. <span data-ttu-id="6ad26-164">Habilitar a física</span><span class="sxs-lookup"><span data-stu-id="6ad26-164">Enable physics</span></span>
3. <span data-ttu-id="6ad26-165">Adicionar um componente de Fonte de Áudio</span><span class="sxs-lookup"><span data-stu-id="6ad26-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="6ad26-166">Adicionar e configurar o componente de Iniciar o Módulo Lunar (Script)</span><span class="sxs-lookup"><span data-stu-id="6ad26-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="6ad26-167">Adicionar e configurar o componente Alternar Dicas de Posicionamento (Script)</span><span class="sxs-lookup"><span data-stu-id="6ad26-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="6ad26-168">O componente do Lançar Módulo Lunar (Script) e o componente Alternar Dicas de Posicionamento (Script) não fazem parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="6ad26-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="6ad26-169">Eles foram fornecidos com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="6ad26-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="6ad26-170">1. Habilitar a manipulação de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="6ad26-170">1. Enable object manipulation</span></span>

<span data-ttu-id="6ad26-171">Na janela Hierarquia, selecione o objeto RocketLauncher > **LunarModule**, adicione o componente **Manipulador de Manipulação (Script)** e o componente **Capturável de Interação Próxima (Script)** , então configure o Manipulador de Manipulação (Script) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ad26-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="6ad26-172">Desmarque a caixa de seleção **Permitir Manipulação Distante** para permitir apenas interação próxima</span><span class="sxs-lookup"><span data-stu-id="6ad26-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="6ad26-173">Altere **Tipo de Manipulação de Duas Mãos** para Mover Girar para que o dimensionamento seja desabilitado</span><span class="sxs-lookup"><span data-stu-id="6ad26-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="6ad26-175">2. Habilitar a física</span><span class="sxs-lookup"><span data-stu-id="6ad26-175">2. Enable physics</span></span>

<span data-ttu-id="6ad26-176">Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione um componente **Rigidbody** e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ad26-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="6ad26-177">Desmarque a caixa de seleção **Usar Gravidade** para que o módulo lunar não seja afetado pela gravidade</span><span class="sxs-lookup"><span data-stu-id="6ad26-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="6ad26-178">Marque a caixa de seleção **Is Kinematic** para que o Módulo Lunar inicialmente não seja afetado por forças físicas</span><span class="sxs-lookup"><span data-stu-id="6ad26-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="6ad26-180">3. Adicionar um componente de Fonte de Áudio</span><span class="sxs-lookup"><span data-stu-id="6ad26-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="6ad26-181">Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione um componente **Fonte de Áudio** e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ad26-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="6ad26-182">Alterar **Mistura Espacial** para 1 para habilitar o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="6ad26-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="6ad26-184">4. Adicionar e configurar o componente de Iniciar o Módulo Lunar (Script)</span><span class="sxs-lookup"><span data-stu-id="6ad26-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="6ad26-185">Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione o componente **Lançar Módulo Lunar (Script)** e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ad26-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="6ad26-186">Altere o valor **Confiança** de modo que o Módulo Lunar voe de modo gracioso quando lançado, por exemplo, para 0,01</span><span class="sxs-lookup"><span data-stu-id="6ad26-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="6ad26-188">5. Adicionar e configurar o componente Alternar Dicas de Posicionamento (Script)</span><span class="sxs-lookup"><span data-stu-id="6ad26-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="6ad26-189">Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione o componente **Alternar Dicas de Posicionamento (Script)** e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6ad26-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="6ad26-190">Defina a propriedade **Tamanho** da Matriz de Objetos do Jogo como 5</span><span class="sxs-lookup"><span data-stu-id="6ad26-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="6ad26-191">Atribua cada um dos **objetos filho** do objeto RocketLauncher > LunarModule > **PlacementHints** para o campo **Elemento** na Matriz de Objeto do Jogo:</span><span class="sxs-lookup"><span data-stu-id="6ad26-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="6ad26-193">Como configurar o botão Lançar</span><span class="sxs-lookup"><span data-stu-id="6ad26-193">Configuring the Launch button</span></span>

<span data-ttu-id="6ad26-194">Na janela Hierarquia, selecione o objeto RocketLauncher > Botões > **LaunchButton**, então, no componente **Botão Pressionável (Script)** , crie um evento **Botão Pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule.StartThruster** como a ação a ser acionada:</span><span class="sxs-lookup"><span data-stu-id="6ad26-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="6ad26-196">Para obter um lembrete sobre como implementar eventos, você pode consultar as instruções de [Gestos de acompanhamento da mão e botões interativos](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="6ad26-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="6ad26-197">Com o objeto RocketLauncher > Botões > **LaunchButton** ainda selecionado, no componente **Botão Pressionável (Script)** , crie um evento **Botão Pressionado ()** , configure o objeto **LunarModule** para receber o evento, defina **AudioSource.PlayOneShot** como a ação a ser acionada e atribua um clipe de áudio adequado ao campo **Clipe de Áudio**, por exemplo, o clipe de áudio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="6ad26-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="6ad26-199">Com o objeto RocketLauncher > Botões > **LaunchButton** ainda selecionado, no componente **Botão Pressionável (Script)** , crie um evento **Extremidade de Toque ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule.StopThruster** como a ação a ser acionada:</span><span class="sxs-lookup"><span data-stu-id="6ad26-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="6ad26-201">Se agora você inserir o modo de Jogo e pressionar o botão Lançar, ouvirá a reprodução do clipe de áudio e, se mantiver o botão Lançar pressionado por aproximadamente um segundo ou mais, verá o Módulo Lunar ser lançado no espaço:</span><span class="sxs-lookup"><span data-stu-id="6ad26-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="6ad26-203">Como configurar o botão Redefinir</span><span class="sxs-lookup"><span data-stu-id="6ad26-203">Configuring the Reset button</span></span>

<span data-ttu-id="6ad26-204">Na janela hierarquia, selecione o objeto RocketLauncher > Botões > **ResetButton** e, em seguida, no componente **Botão Pressionável (Script)** , crie um evento de **Botão Pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule.ResetModule** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="6ad26-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="6ad26-206">Com o objeto RocketLauncher > Botões > **ResetButton** ainda selecionado, no componente **Botão Pressionável (Script)** , crie um evento **Botão Pressionado ()** , configure o objeto **RocketLauncher** para receber o evento, defina **GameObject.BroadcastMessage** como a ação a ser disparada e insira **ResetPlacement** no campo de mensagem:</span><span class="sxs-lookup"><span data-stu-id="6ad26-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="6ad26-208">A ação GameObject.BroadcastMessage envia a mensagem ResetPlacement do objeto RocketLauncher para todos os seus objetos filho.</span><span class="sxs-lookup"><span data-stu-id="6ad26-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="6ad26-209">Qualquer objeto filho que tenha a função ResetPlacement, que é definida no componente de Demonstração de Montagem de Peças (script) que você adicionou a todos os objetos filho LunarModuleParts, invocará a função ResetPlacement, que redefinirá o posicionamento do objeto filho.</span><span class="sxs-lookup"><span data-stu-id="6ad26-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="6ad26-210">Se agora você entrar no modo de Jogo, mover algumas peças e/ou iniciar o Módulo Lunar e então pressionar o botão Redefinir, verá as peças e/ou o Módulo Lunar sendo redefinido para a posição original:</span><span class="sxs-lookup"><span data-stu-id="6ad26-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="6ad26-212">Como configurar o botão Dicas de Posicionamento</span><span class="sxs-lookup"><span data-stu-id="6ad26-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="6ad26-213">Na janela hierarquia, selecione o objeto RocketLauncher > Botões > **HintsButton** e, em seguida, no componente **Botão Pressionável (Script)** , crie um evento de **Botão Pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **TogglePlacementHints.ToggleGameObjects** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="6ad26-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="6ad26-215">Se agora você entrar no modo Jogo, observará que as dicas de posicionamento translúcidas estão desabilitadas por padrão, mas que você pode ativá-las e desativá-las pressionando o botão Dicas:</span><span class="sxs-lookup"><span data-stu-id="6ad26-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="6ad26-217">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6ad26-217">Congratulations</span></span>

<span data-ttu-id="6ad26-218">Você configurou totalmente este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ad26-218">You have fully configured this application.</span></span> <span data-ttu-id="6ad26-219">Agora, seu aplicativo permite que os usuários montem totalmente o Módulo Lunar, lancem o Módulo Lunar, alternem dicas e redefinam o aplicativo para que ele seja iniciado novamente.</span><span class="sxs-lookup"><span data-stu-id="6ad26-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>

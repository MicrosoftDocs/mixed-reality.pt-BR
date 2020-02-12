---
title: Tutoriais de introdução-7. Criando um aplicativo de exemplo de módulo lunar
description: Nesta lição, você combinará vários conceitos aprendidos das lições anteriores para criar uma experiência de amostra exclusiva.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129357"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="2a527-105">7. criando um aplicativo de exemplo de módulo lunar</span><span class="sxs-lookup"><span data-stu-id="2a527-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="2a527-106">Neste tutorial, vários conceitos são combinados de lições anteriores para criar uma experiência de amostra exclusiva.</span><span class="sxs-lookup"><span data-stu-id="2a527-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="2a527-107">Você aprenderá a criar um aplicativo de assembly de parte, no qual um usuário precisa usar mãos controladas para pegar partes e tentar montar um módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="2a527-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="2a527-108">Você usará botões que poderão ser prensados para ativar e desativar Dicas de posicionamento, para redefinir a experiência e para iniciar o módulo lunar no espaço!</span><span class="sxs-lookup"><span data-stu-id="2a527-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="2a527-109">Em Tutoriais futuros, você continuará a se basear nessa experiência, que inclui casos avançados de uso de vários usuários que aproveitam as âncoras espaciais do Azure para o alinhamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2a527-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="2a527-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2a527-110">Objectives</span></span>

* <span data-ttu-id="2a527-111">Combine vários conceitos das lições anteriores para criar uma experiência exclusiva</span><span class="sxs-lookup"><span data-stu-id="2a527-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="2a527-112">Saiba como alternar objetos</span><span class="sxs-lookup"><span data-stu-id="2a527-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="2a527-113">Dispare eventos complexos usando os botões pressionáveis</span><span class="sxs-lookup"><span data-stu-id="2a527-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="2a527-114">Use força e física de corpo rígido</span><span class="sxs-lookup"><span data-stu-id="2a527-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="2a527-115">Explore o uso de dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="2a527-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="2a527-116">Visão geral das partes do módulo lunar</span><span class="sxs-lookup"><span data-stu-id="2a527-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="2a527-117">Nesta seção, você criará um desafio de assembly de parte simples, em que o objetivo do usuário é posicionar cinco partes que são distribuídas na tabela no local correto do módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="2a527-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="2a527-118">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="2a527-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2a527-119">Adicionar o pré-fabricado do iniciador de Rocket à cena</span><span class="sxs-lookup"><span data-stu-id="2a527-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="2a527-120">Habilitar a manipulação de objetos para todas as partes</span><span class="sxs-lookup"><span data-stu-id="2a527-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="2a527-121">Adicionar e configurar o componente de demonstração do assembly de parte (script)</span><span class="sxs-lookup"><span data-stu-id="2a527-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="2a527-122">O componente de demonstração do assembly de parte (script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="2a527-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="2a527-123">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="2a527-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="2a527-124">1. Adicionar o pré-fabricado do iniciador de Rocket à cena</span><span class="sxs-lookup"><span data-stu-id="2a527-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="2a527-125">Na janela do projeto, navegue até os **ativos** > **MRTK. Tutoriais. GettingStarted** > **pré-fabricados** > pasta **RocketLauncher** , arraste o **RocketLauncher** pré-fabricado para a janela hierarquia para adicioná-lo à sua cena e, em seguida, posicione-o em um local adequado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2a527-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="2a527-126">Transforme a posição X = 1,5, Y =-0,4, Z = 0, portanto ela está posicionada à direita do usuário na altura de estou</span><span class="sxs-lookup"><span data-stu-id="2a527-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="2a527-127">Rotação de transformação X = 0, Y = 180, Z = 0, portanto, os principais recursos da experiência enfrentam o usuário</span><span class="sxs-lookup"><span data-stu-id="2a527-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="2a527-129">2. habilitar a manipulação de objetos para todas as partes</span><span class="sxs-lookup"><span data-stu-id="2a527-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="2a527-130">Na janela hierarquia, localize o objeto RocketLauncher > **LunarModuleParts** e selecione todos os **objetos filho**, adicione o componente **manipulador de manipulação (script)** e o componente de **captura de interação Near (script)** e, em seguida, configure o manipulador de manipulação (script) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2a527-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="2a527-131">Altere o **tipo de manipulação de duas mãos** para mover girar para que o dimensionamento seja desabilitado</span><span class="sxs-lookup"><span data-stu-id="2a527-131">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="2a527-132">Desmarque a caixa de seleção **permitir manipulação distante** para permitir apenas interação próxima</span><span class="sxs-lookup"><span data-stu-id="2a527-132">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="2a527-134">Para um lembrete, com instruções passo a passo, sobre como implementar a manipulação de objetos, você pode consultar as instruções [manipulando objetos 3D](mrlearning-base-ch4.md#manipulating-3d-objects) .</span><span class="sxs-lookup"><span data-stu-id="2a527-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="2a527-135">3. adicionar e configurar o componente de demonstração (script) do assembly de parte</span><span class="sxs-lookup"><span data-stu-id="2a527-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="2a527-136">Com todos os objetos filho LunarModuleParts ainda selecionados, adicione um componente de **fonte de áudio** e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2a527-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="2a527-137">Atribua um clipe de áudio adequado ao campo **AudioClip** , por exemplo, MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="2a527-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="2a527-138">Desmarque a caixa de seleção **reproduzir no ativo** , portanto, o clipe de áudio não é tocado automaticamente quando a cena é carregada</span><span class="sxs-lookup"><span data-stu-id="2a527-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="2a527-139">Alterar a **mistura espacial** para 1 para habilitar o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="2a527-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="2a527-141">Com todos os objetos filho LunarModuleParts ainda selecionados, adicione o componente de **demonstração do assembly de parte (script)** :</span><span class="sxs-lookup"><span data-stu-id="2a527-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="2a527-143">Na janela hierarquia, selecione o objeto **RoverEnclosure** e configure seu componente de **demonstração do assembly de parte (script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2a527-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="2a527-144">Para o campo **objeto a ser colocado** , atribua o objeto em si, neste caso, o objeto **RoverEnclosure**</span><span class="sxs-lookup"><span data-stu-id="2a527-144">To the **Object To Place** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>
* <span data-ttu-id="2a527-145">Para o campo **local para colocação** , atribua o objeto PlacementHints correspondente, nesse caso, o objeto **RoverEnclosure_PlacementHints**</span><span class="sxs-lookup"><span data-stu-id="2a527-145">To the **Location To Place** field, assign the corresponding PlacementHints object, in this case, the **RoverEnclosure_PlacementHints** object</span></span>
* <span data-ttu-id="2a527-146">Para o campo **objeto de dica de ferramenta** , atribua o tooltipobject correspondente, nesse caso, o objeto **RoverEnclosure_ToolTip**</span><span class="sxs-lookup"><span data-stu-id="2a527-146">To the **Tool Tip Object** field, assign the corresponding ToolTipObject, in this case, the **RoverEnclosure_ToolTip** object</span></span>
* <span data-ttu-id="2a527-147">Para o campo **fonte de áudio** , atribua o próprio objeto, neste caso, o objeto **RoverEnclosure**</span><span class="sxs-lookup"><span data-stu-id="2a527-147">To the **Audio Source** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="2a527-149">**Repita** para cada um dos outros objetos filho LunarModuleParts, ou seja, FuelTank, EnergyCell, DockingPortal e ExternalSensor.</span><span class="sxs-lookup"><span data-stu-id="2a527-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="2a527-150">Se agora você inserir o modo de jogo e mover um ' objeto para o local ' próximo ao ' local para colocação ' correspondente, você notará:</span><span class="sxs-lookup"><span data-stu-id="2a527-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="2a527-151">O objeto será ajustado no lugar e será pai do objeto LunarModule para que ele se torne parte do módulo lunar</span><span class="sxs-lookup"><span data-stu-id="2a527-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="2a527-152">A fonte de áudio no objeto reproduzirá o clipe de áudio atribuído no local do objeto</span><span class="sxs-lookup"><span data-stu-id="2a527-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="2a527-153">O objeto da dica de ferramenta correspondente ficará oculto</span><span class="sxs-lookup"><span data-stu-id="2a527-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="2a527-155">Para obter um lembrete sobre como usar a simulação de entrada no editor, você pode consultar o [usando a simulação de entrada do no editor para testar um](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guia de cena no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="2a527-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="2a527-156">Configuração do módulo lunar</span><span class="sxs-lookup"><span data-stu-id="2a527-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="2a527-157">Nesta seção, você adicionará recursos adicionais ao aplicativo de iniciador do Rocket para que o usuário possa:</span><span class="sxs-lookup"><span data-stu-id="2a527-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="2a527-158">Interagir com o módulo lunar</span><span class="sxs-lookup"><span data-stu-id="2a527-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="2a527-159">Iniciar o módulo lunar no espaço e tocar um som quando ele for iniciado</span><span class="sxs-lookup"><span data-stu-id="2a527-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="2a527-160">Redefinir o aplicativo para que o módulo lunar e toda a parte sejam colocados de volta para sua posição original</span><span class="sxs-lookup"><span data-stu-id="2a527-160">Reset the application so the Lunar Module and all the part are placed back to their original position</span></span>
* <span data-ttu-id="2a527-161">Oculte as dicas de posicionamento para tornar o desafio do assembly da parte mais difícil.</span><span class="sxs-lookup"><span data-stu-id="2a527-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="2a527-162">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="2a527-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="2a527-163">Habilitar manipulação de objeto</span><span class="sxs-lookup"><span data-stu-id="2a527-163">Enable object manipulation</span></span>
2. <span data-ttu-id="2a527-164">Habilitar física</span><span class="sxs-lookup"><span data-stu-id="2a527-164">Enable physics</span></span>
3. <span data-ttu-id="2a527-165">Adicionar um componente de fonte de áudio</span><span class="sxs-lookup"><span data-stu-id="2a527-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="2a527-166">Adicionar e configurar o componente módulo lunar (script) de inicialização</span><span class="sxs-lookup"><span data-stu-id="2a527-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="2a527-167">Adicionar e configurar o componente alternar dicas de posicionamento (script)</span><span class="sxs-lookup"><span data-stu-id="2a527-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="2a527-168">O componente do módulo lunar de inicialização (script) e o componente alternar dicas de posicionamento (script) não fazem parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="2a527-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="2a527-169">Eles foram fornecidos com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="2a527-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="2a527-170">1. habilitar a manipulação de objetos</span><span class="sxs-lookup"><span data-stu-id="2a527-170">1. Enable object manipulation</span></span>

<span data-ttu-id="2a527-171">Na janela hierarquia, selecione o objeto RocketLauncher > **LunarModule** , adicione o componente **manipulador de manipulação (script)** e o componente de **captura de interação Near (script)** e, em seguida, configure o manipulador de manipulação (script) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2a527-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="2a527-172">Altere o **tipo de manipulação de duas mãos** para mover girar para que o dimensionamento seja desabilitado</span><span class="sxs-lookup"><span data-stu-id="2a527-172">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="2a527-173">Desmarque a caixa de seleção **permitir manipulação distante** para permitir apenas interação próxima</span><span class="sxs-lookup"><span data-stu-id="2a527-173">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="2a527-175">2. habilitar a física</span><span class="sxs-lookup"><span data-stu-id="2a527-175">2. Enable physics</span></span>

<span data-ttu-id="2a527-176">Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione um componente Rigidbody e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2a527-176">With the RocketLauncher > **LunarModule** object still selected, add a Rigidbody component and then configure it as follows:</span></span>

* <span data-ttu-id="2a527-177">Desmarque a caixa de seleção **usar gravidade** para que o módulo lunar não seja afetado pela gravidade</span><span class="sxs-lookup"><span data-stu-id="2a527-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="2a527-178">Marque a caixa de seleção **é cinemática** para que o módulo lunar inicialmente não seja afetado por Physic Forces</span><span class="sxs-lookup"><span data-stu-id="2a527-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="2a527-180">3. adicionar um componente de fonte de áudio</span><span class="sxs-lookup"><span data-stu-id="2a527-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="2a527-181">Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione um componente **fonte de áudio** e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2a527-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="2a527-182">Altere a **mistura espacial** para 1 para habilitar o áudio espacial</span><span class="sxs-lookup"><span data-stu-id="2a527-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="2a527-184">4. adicionar e configurar o componente do módulo lunar de abertura (script)</span><span class="sxs-lookup"><span data-stu-id="2a527-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="2a527-185">Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione o componente **módulo lunar de abertura (script)** e, em seguida, configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2a527-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="2a527-186">Altere o valor de **Thrustmaster** para que o módulo lunar seja ativado normalmente quando iniciado, por exemplo, para 0, 1</span><span class="sxs-lookup"><span data-stu-id="2a527-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="2a527-188">5. adicionar e configurar o componente alternar dicas de posicionamento (script)</span><span class="sxs-lookup"><span data-stu-id="2a527-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="2a527-189">Com o objeto RocketLauncher > **LunarModule** ainda selecionado, adicione o componente **alternar dicas de posicionamento (script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2a527-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="2a527-190">Defina a propriedade **tamanho** da matriz de objetos do jogo como 5</span><span class="sxs-lookup"><span data-stu-id="2a527-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="2a527-191">Atribua cada um dos **objetos filho** do objeto **PlacementHints** para o campo **elemento** na matriz do objeto Game:</span><span class="sxs-lookup"><span data-stu-id="2a527-191">Assign each of the **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="2a527-193">Configurando o botão iniciar</span><span class="sxs-lookup"><span data-stu-id="2a527-193">Configuring the Launch button</span></span>

<span data-ttu-id="2a527-194">Na janela hierarquia, selecione os botões de > de RocketLauncher > objeto **LaunchButton** e, em seguida, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule. StartThruster** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="2a527-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="2a527-196">Para obter um lembrete sobre como implementar eventos, consulte as instruções [gestos de acompanhamento de mão e botões](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) que podem interagir.</span><span class="sxs-lookup"><span data-stu-id="2a527-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="2a527-197">Com os botões de > RocketLauncher > objeto **LaunchButton** ainda selecionado, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **LunarModule** para receber o evento, defina **audioname. PlayOneShot** como a ação a ser disparada e atribua um clipe de áudio adequado ao campo de **clipe de áudio** , por exemplo, o clipe de áudio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="2a527-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="2a527-199">Com os botões de > RocketLauncher > objeto **LaunchButton** ainda selecionado, no componente de **botão prensado (script)** , crie um novo evento de **toque terminado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule. StopThruster** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="2a527-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch Ended ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="2a527-201">Se agora você inserir o modo de jogo e pressionar o botão Iniciar, ouvirá a reprodução do clipe de áudio e, se mantiver o botão iniciar por cerca de um segundo ou mais, você verá o módulo lunar aberto no espaço:</span><span class="sxs-lookup"><span data-stu-id="2a527-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="2a527-203">Configurando o botão redefinir</span><span class="sxs-lookup"><span data-stu-id="2a527-203">Configuring the Reset button</span></span>

<span data-ttu-id="2a527-204">Na janela hierarquia, selecione os botões de > de RocketLauncher > objeto **ResetButton** e, em seguida, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **LaunchLunarModule. ResetModule** como a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="2a527-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="2a527-206">Com os botões de > RocketLauncher > objeto **ResetButton** ainda selecionado, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **RocketLauncher** para receber o evento, defina **gameobject. BroadcastMessage** como a ação a ser disparada e digite **ResetPlacement** no campo de mensagem:</span><span class="sxs-lookup"><span data-stu-id="2a527-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="2a527-208">A ação gameobject. BroadcastMessage envia a mensagem ResetPlacement do objeto RocketLauncher para todos os seus objetos filho.</span><span class="sxs-lookup"><span data-stu-id="2a527-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="2a527-209">Qualquer objeto filho que tenha a função ResetPlacement, que é definida no componente de demonstração de assembly de parte (script) que você adicionou a todos os objetos filho LunarModuleParts, invocará a função ResetPlacement, que redefinirá o posicionamento do objeto filho.</span><span class="sxs-lookup"><span data-stu-id="2a527-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="2a527-210">Se agora você inserir o modo de jogo e pressionar o botão redefinir, ouvirá o clipe de áudio que está sendo reproduzido e verá o módulo lunar sendo iniciado no espaço:</span><span class="sxs-lookup"><span data-stu-id="2a527-210">If you now enter Game mode and press the Reset button you will hear the audio clip being played and see the Lunar Module being launched into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="2a527-212">Configurando o botão de dicas de posicionamento</span><span class="sxs-lookup"><span data-stu-id="2a527-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="2a527-213">Na janela hierarquia, selecione os botões de > de RocketLauncher > objeto **HintsButton** e, em seguida, no componente de **botão pressionável (script)** , crie um novo evento **botão pressionado ()** , configure o objeto **LunarModule** para receber o evento e defina **TogglePlacementHints. ToggleGameObjects** a ação a ser disparada:</span><span class="sxs-lookup"><span data-stu-id="2a527-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="2a527-215">Se você agora entrar no modo de jogo, observará que as dicas de posicionamento translúcidas estão desabilitadas por padrão, mas que você pode ativá-las e desativá-las pressionando o botão de dicas:</span><span class="sxs-lookup"><span data-stu-id="2a527-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="2a527-217">Parabéns</span><span class="sxs-lookup"><span data-stu-id="2a527-217">Congratulations</span></span>

<span data-ttu-id="2a527-218">Você configurou totalmente este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2a527-218">You have fully configured this application.</span></span> <span data-ttu-id="2a527-219">Agora, seu aplicativo permite que os usuários montem totalmente o módulo lunar, iniciem o módulo lunar, alternem dicas e redefinam o aplicativo para que ele seja iniciado novamente.</span><span class="sxs-lookup"><span data-stu-id="2a527-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>

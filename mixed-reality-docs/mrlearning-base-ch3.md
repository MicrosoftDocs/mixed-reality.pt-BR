---
title: Tutoriais de introdução-4. Colocando conteúdo dinâmico e usando os solveres
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 5463f363291790fd5e5d76ffa322a61ca7bf8e31
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553854"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="0e926-105">4. colocando o conteúdo dinâmico e usando os Solveres</span><span class="sxs-lookup"><span data-stu-id="0e926-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="0e926-106">Os hologramas ganham vida no HoloLens 2 quando acompanham intuitivamente o usuário e são colocados no ambiente físico de forma a tornar a interação direta e elegante.</span><span class="sxs-lookup"><span data-stu-id="0e926-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="0e926-107">Neste tutorial, exploraremos maneiras de colocar os hologramas dinamicamente usando as ferramentas de posicionamento disponíveis do MRTK, conhecidas como resolvedores, para resolver cenários de posicionamento espacial complexos.</span><span class="sxs-lookup"><span data-stu-id="0e926-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="0e926-108">No MRTK, os resolvedores são um sistema de scripts e comportamentos que são usados para permitir que elementos da interface do usuário sigam você, o usuário ou outros objetos de jogo na cena.</span><span class="sxs-lookup"><span data-stu-id="0e926-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="0e926-109">Também podem ser usados para se ajustarem a determinadas posições rapidamente, tornando seu aplicativo mais intuitivo.</span><span class="sxs-lookup"><span data-stu-id="0e926-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="0e926-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0e926-110">Objectives</span></span>

* <span data-ttu-id="0e926-111">Introduza os resolvedores do MRTK</span><span class="sxs-lookup"><span data-stu-id="0e926-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="0e926-112">Usar os resolvedores para que um conjunto de botões siga o usuário</span><span class="sxs-lookup"><span data-stu-id="0e926-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="0e926-113">Use os Solveres para que um objeto de jogo siga as mãos controladas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="0e926-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="0e926-114">Local dos resolvedores no MRTK</span><span class="sxs-lookup"><span data-stu-id="0e926-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="0e926-115">Os resolvedores do MRTK estão localizados na pasta MRTK SDK.</span><span class="sxs-lookup"><span data-stu-id="0e926-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="0e926-116">Para ver os resolvedores disponíveis em seu projeto, na janela do projeto, navegue até **ativos** > **MixedRealityToolkit. SDK** > **recursos** > **utilitários** > **solveres**:</span><span class="sxs-lookup"><span data-stu-id="0e926-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="0e926-118">Neste tutorial, examinaremos a implementação do solucionador de orbital e o solucionador de exibição radial.</span><span class="sxs-lookup"><span data-stu-id="0e926-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="0e926-119">Para saber mais sobre a gama completa de resolvedores disponíveis no MRTK, você pode visitar o guia de [resolvedores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no portal de [documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0e926-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="0e926-120">Usar um resolvedor para seguir o usuário</span><span class="sxs-lookup"><span data-stu-id="0e926-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="0e926-121">Nesta seção, você aprimorará a coleção de botões criada no tutorial anterior para que ele siga a direção do olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="0e926-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="0e926-122">Além disso, você também configurará o resolvedor para que a coleção de botões sempre seja:</span><span class="sxs-lookup"><span data-stu-id="0e926-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="0e926-123">Girado paralelamente à direção de leitura do usuário, para leitura natural da esquerda para a direita</span><span class="sxs-lookup"><span data-stu-id="0e926-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="0e926-124">Posicionado ligeiramente abaixo da direção da olhar horizontal do usuário, portanto, não está obstruindo os outros objetos que serão adicionados posteriormente neste tutorial</span><span class="sxs-lookup"><span data-stu-id="0e926-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="0e926-125">Posicionado aproximadamente o comprimento de um semestre do usuário, para que os botões possam ser facilmente pressionados</span><span class="sxs-lookup"><span data-stu-id="0e926-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="0e926-126">Para isso, você usará o **resolvedor orbital** que bloqueia o objeto para uma posição especificada e o deslocamento do objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="0e926-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="0e926-127">1. Adicionar o resolvedor orbital</span><span class="sxs-lookup"><span data-stu-id="0e926-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="0e926-128">Na janela hierarquia, selecione o objeto **buttoncollection** e, em seguida, na janela Inspetor, use o botão **Adicionar componente** para adicionar o componente **orbital (script)** ao objeto buttoncollection.</span><span class="sxs-lookup"><span data-stu-id="0e926-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="0e926-129">Quando você adiciona um resolvedor, nesse caso, o componente orbital (script), o componente manipulador (script) do Solver é adicionado automaticamente, pois é exigido pelo resolvedor.</span><span class="sxs-lookup"><span data-stu-id="0e926-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="0e926-130">2. configurar o resolvedor orbital</span><span class="sxs-lookup"><span data-stu-id="0e926-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="0e926-131">Configure o componente **manipulador (script) do Solver** :</span><span class="sxs-lookup"><span data-stu-id="0e926-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="0e926-132">Verifique se o **tipo de destino controlado** está definido como **Head**</span><span class="sxs-lookup"><span data-stu-id="0e926-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="0e926-133">Configure o componente **orbital (script)** :</span><span class="sxs-lookup"><span data-stu-id="0e926-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="0e926-134">Verifique se o **tipo de orientação** está definido como **seguir objeto acompanhado**</span><span class="sxs-lookup"><span data-stu-id="0e926-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="0e926-135">Redefinir **deslocamento local** para X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="0e926-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="0e926-136">Alterar o **deslocamento do mundo** para X = 0, Y =-0,4, Z = 0,3</span><span class="sxs-lookup"><span data-stu-id="0e926-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="0e926-138">3. testar o resolvedor orbital usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="0e926-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="0e926-139">Pressione o botão reproduzir para entrar no modo de jogo e pressione e mantenha o botão direito do mouse para girar sua direção olhar e observe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0e926-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="0e926-140">A posição de transformação de Buttoncollection agora é controlada pelas configurações do Solver</span><span class="sxs-lookup"><span data-stu-id="0e926-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="0e926-141">O cubo, que não é afetado pelo resolvedor, permanece na mesma posição</span><span class="sxs-lookup"><span data-stu-id="0e926-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="0e926-143">Se você não vir a câmera Ray em sua janela de cena, verifique se o menu utensílios está habilitado.</span><span class="sxs-lookup"><span data-stu-id="0e926-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="0e926-144">Para saber mais sobre o menu utensílios e como você pode usá-lo para otimizar sua exibição de cena, você pode visitar a documentação do <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu utensílios</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="0e926-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="0e926-145">Para exibir sua cena e a janela do jogo lado a lado, conforme mostrado na imagem acima, basta arrastar a janela do jogo para o lado direito da janela cena.</span><span class="sxs-lookup"><span data-stu-id="0e926-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="0e926-146">Para saber mais sobre como personalizar seu espaço de trabalho, você pode visitar a documentação de <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalização de espaço de trabalho</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="0e926-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="0e926-147">Habilitando objetos para seguir as mãos controladas</span><span class="sxs-lookup"><span data-stu-id="0e926-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="0e926-148">Nesta seção, você configurará o objeto de cubo criado no tutorial anterior para que ele siga as mãos controladas pelo usuário, especificamente o pulso à direita.</span><span class="sxs-lookup"><span data-stu-id="0e926-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="0e926-149">Além disso, você também configurará o resolvedor para que o cubo:</span><span class="sxs-lookup"><span data-stu-id="0e926-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="0e926-150">Altera a orientação com a rotação da mão do usuário</span><span class="sxs-lookup"><span data-stu-id="0e926-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="0e926-151">Posicionado no pulso do usuário</span><span class="sxs-lookup"><span data-stu-id="0e926-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="0e926-152">Para isso, você usará o **solucionador de exibição radial** que mantém o objeto em uma conversão de cone de exibição pelo objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="0e926-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="0e926-153">1. Adicionar o solucionador de exibição radial</span><span class="sxs-lookup"><span data-stu-id="0e926-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="0e926-154">Na janela hierarquia, selecione o objeto **cubo** e, na janela Inspetor, use o botão **Adicionar componente** para adicionar o objeto de cubo de componente de **exibição radial (script)** .</span><span class="sxs-lookup"><span data-stu-id="0e926-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="0e926-155">2. configurar o solucionador de exibição radial</span><span class="sxs-lookup"><span data-stu-id="0e926-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="0e926-156">Configure o componente **manipulador (script) do Solver** :</span><span class="sxs-lookup"><span data-stu-id="0e926-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="0e926-157">Alterar o **tipo de destino controlado** para a **junção à mão**</span><span class="sxs-lookup"><span data-stu-id="0e926-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="0e926-158">Alterar a **mão controlada** à **direita**</span><span class="sxs-lookup"><span data-stu-id="0e926-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="0e926-159">Alterar **mão controlada conjunta** para **pulso**</span><span class="sxs-lookup"><span data-stu-id="0e926-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="0e926-160">Configure o componente de **exibição radial (script)** :</span><span class="sxs-lookup"><span data-stu-id="0e926-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="0e926-161">Altere a **direção de referência** para **orientado a objeto**e marque a caixa de seleção **orientar para direção de referência**</span><span class="sxs-lookup"><span data-stu-id="0e926-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="0e926-162">Alterar a distância **mínima** e a **distância máxima** para 0</span><span class="sxs-lookup"><span data-stu-id="0e926-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="0e926-164">3. testar o solucionador de exibição radial usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="0e926-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="0e926-165">Pressione o botão reproduzir para entrar no modo de jogo e pressione e segure a barra de espaços para abrir a mão.</span><span class="sxs-lookup"><span data-stu-id="0e926-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="0e926-166">Mova o cursor do mouse para mover a mão e clique e mantenha o botão esquerdo do mouse para girar a mão:</span><span class="sxs-lookup"><span data-stu-id="0e926-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="0e926-168">Parabéns</span><span class="sxs-lookup"><span data-stu-id="0e926-168">Congratulations</span></span>

<span data-ttu-id="0e926-169">Neste tutorial, você aprendeu a usar os resolvedores do MRTK para ter uma interface do usuário intuitivamente seguir o User.</span><span class="sxs-lookup"><span data-stu-id="0e926-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="0e926-170">Você também aprendeu como anexar um resolvedor a um objeto (ou seja, cubo) para seguir as mãos controladas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0e926-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="0e926-171">Para saber mais sobre esses e outros resolvedores incluídos no MRTK, você pode visitar o guia de [resolvedores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0e926-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="0e926-172">Próximo tutorial: 5. interagindo com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="0e926-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)

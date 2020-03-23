---
title: Tutoriais de introdução – 4. Como posicionar o conteúdo dinâmico e usar Solucionadores
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2825f99f49eca6fd7277d02828bfe1bc3c23291a
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031219"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="90753-105">4. Como posicionar o conteúdo dinâmico e usar Solucionadores</span><span class="sxs-lookup"><span data-stu-id="90753-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="90753-106">Os hologramas ganham vida no HoloLens 2 quando seguem intuitivamente o usuário e são posicionados no ambiente físico de maneira a tornar a interação simples e elegante.</span><span class="sxs-lookup"><span data-stu-id="90753-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="90753-107">Neste tutorial, exploraremos maneiras de posicionar hologramas dinamicamente usando as ferramentas de posicionamento disponíveis do MRTK, conhecidas como Solucionadores, para resolver cenários de posicionamento espacial complexos.</span><span class="sxs-lookup"><span data-stu-id="90753-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="90753-108">No MRTK, os Solucionadores são um sistema de scripts e comportamentos usados para permitir que os elementos da interface do usuário sigam você, o usuário ou outros objetos do jogo na cena.</span><span class="sxs-lookup"><span data-stu-id="90753-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="90753-109">Também podem ser usados para se ajustarem a determinadas posições rapidamente, tornando seu aplicativo mais intuitivo.</span><span class="sxs-lookup"><span data-stu-id="90753-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="90753-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="90753-110">Objectives</span></span>

* <span data-ttu-id="90753-111">Apresentar os Solucionadores do MRTK</span><span class="sxs-lookup"><span data-stu-id="90753-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="90753-112">Usar os Solucionadores para fazer um conjunto de botões seguir o usuário</span><span class="sxs-lookup"><span data-stu-id="90753-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="90753-113">Usar os Solucionadores para fazer um objeto do jogo seguir as mãos do usuário</span><span class="sxs-lookup"><span data-stu-id="90753-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="90753-114">Localização dos Solucionadores no MRTK</span><span class="sxs-lookup"><span data-stu-id="90753-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="90753-115">Os Solucionadores do MRTK estão localizados na pasta MRTK SDK.</span><span class="sxs-lookup"><span data-stu-id="90753-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="90753-116">Para ver os Solucionadores disponíveis em seu projeto, na janela Projeto, navegue até **Ativos** > **MixedRealityToolkit.SDK** > **Recursos** > **Utilitários** > **Solucionadores**:</span><span class="sxs-lookup"><span data-stu-id="90753-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="90753-118">Neste tutorial, examinaremos a implementação do Solucionador Orbital e do Solucionador de Exibição Radial.</span><span class="sxs-lookup"><span data-stu-id="90753-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="90753-119">Para saber mais sobre a gama completa de Solucionadores disponíveis no MRTK, você pode visitar o guia [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="90753-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="90753-120">Usar um solucionador para seguir o usuário</span><span class="sxs-lookup"><span data-stu-id="90753-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="90753-121">Nesta seção, você aprimorará a coleção de botões criada no tutorial anterior para que siga a direção do olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="90753-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="90753-122">Além disso, você também configurará o Solucionador para que a coleção de botões sempre seja:</span><span class="sxs-lookup"><span data-stu-id="90753-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="90753-123">Girado paralelamente à direção de leitura do usuário, para leitura natural da esquerda para a direita</span><span class="sxs-lookup"><span data-stu-id="90753-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="90753-124">Posicionado ligeiramente abaixo da direção do olhar horizontal do usuário, portanto, não está obstruindo os outros objetos que serão adicionados posteriormente neste tutorial</span><span class="sxs-lookup"><span data-stu-id="90753-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="90753-125">Posicionado aproximadamente na metade do comprimento do braço do usuário, de modo que seja fácil pressionar os botões</span><span class="sxs-lookup"><span data-stu-id="90753-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="90753-126">Para isso, você usará o **Solucionador Orbital** que bloqueia o objeto a uma posição e deslocamento especificados do objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="90753-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="90753-127">1. Adicionar o Solucionador Orbital</span><span class="sxs-lookup"><span data-stu-id="90753-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="90753-128">Na janela Hierarquia, selecione o objeto **ButtonCollection** e, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Orbital (Script)** ao objeto ButtonCollection.</span><span class="sxs-lookup"><span data-stu-id="90753-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="90753-129">Quando você adiciona um Solucionador, nesse caso, o componente Orbital (Script), o componente Manipulador do Solucionador (Script) é adicionado automaticamente, pois é exigido pelo Solucionador.</span><span class="sxs-lookup"><span data-stu-id="90753-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="90753-130">2. Configurar o Solucionador Orbital</span><span class="sxs-lookup"><span data-stu-id="90753-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="90753-131">Configure o componente **Manipulador do Solucionador (Script)** :</span><span class="sxs-lookup"><span data-stu-id="90753-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="90753-132">Verifique se **Tipo de Alvo Acompanhado** está definido como **Cabeça**</span><span class="sxs-lookup"><span data-stu-id="90753-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="90753-133">Configure o componente **Orbital (Script)** :</span><span class="sxs-lookup"><span data-stu-id="90753-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="90753-134">Verifique se **Tipo de Orientação** está definido como **Seguir Objeto Acompanhado**</span><span class="sxs-lookup"><span data-stu-id="90753-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="90753-135">Redefinir **Deslocamento Local** para X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="90753-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="90753-136">Alterar **Deslocamento Mundial** para X = 0, Y =-0,4, Z = 0,3</span><span class="sxs-lookup"><span data-stu-id="90753-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="90753-138">3. Testar o Solucionador Orbital usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="90753-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="90753-139">Pressione o botão Reproduzir para entrar no modo de Jogo e pressione e mantenha pressionado o botão direito do mouse para girar a direção do olhar e observe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="90753-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="90753-140">A Posição de Transformação de ButtonCollection agora é controlada pelas configurações do Solucionador</span><span class="sxs-lookup"><span data-stu-id="90753-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="90753-141">O Cubo, que não é afetado pelo Solucionador, permanece na mesma posição</span><span class="sxs-lookup"><span data-stu-id="90753-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="90753-143">Se você não vir o raio da câmera na janela Cena, verifique se o menu Gizmos está habilitado.</span><span class="sxs-lookup"><span data-stu-id="90753-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="90753-144">Para saber mais sobre o menu Gizmos e como você pode usá-lo para otimizar a exibição de cena, acesse a documentação do <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu Gizmos</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="90753-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="90753-145">Para exibir a janela Cena e Jogo lado a lado como mostra a imagem acima, basta arrastar a janela Jogo para o lado direito da janela Cena.</span><span class="sxs-lookup"><span data-stu-id="90753-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="90753-146">Para saber mais sobre como personalizar seu workspace, você pode visitar a documentação <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Como personalizar seu workspace</a>.</span><span class="sxs-lookup"><span data-stu-id="90753-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="90753-147">Como habilitar os objetos a seguir mãos acompanhadas</span><span class="sxs-lookup"><span data-stu-id="90753-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="90753-148">Nesta seção, você configurará o objeto de cubo criado no tutorial anterior para que ele siga as mãos controladas pelo usuário, especificamente o pulso direito.</span><span class="sxs-lookup"><span data-stu-id="90753-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="90753-149">Além disso, você também configurará o Solucionador para que o cubo:</span><span class="sxs-lookup"><span data-stu-id="90753-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="90753-150">Altere sua orientação com a rotação da mão do usuário</span><span class="sxs-lookup"><span data-stu-id="90753-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="90753-151">Posicionado no pulso do usuário</span><span class="sxs-lookup"><span data-stu-id="90753-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="90753-152">Para isso, você usará o **Solucionador de Exibição Radial** que mantém o objeto em uma conversão de cone de exibição pelo objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="90753-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="90753-153">1. Adicionar o Solucionador de Exibição Radial</span><span class="sxs-lookup"><span data-stu-id="90753-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="90753-154">Na janela Hierarquia, selecione o objeto **Cubo** e, em seguida, na janela Inspetor, use o botão **Adicionar componente** para adicionar o objeto de Cubo do componente **Exibição Radial (Script)** .</span><span class="sxs-lookup"><span data-stu-id="90753-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="90753-155">2. Configurar o Solucionador de Exibição Radial</span><span class="sxs-lookup"><span data-stu-id="90753-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="90753-156">Configure o componente **Manipulador do Solucionador (Script)** :</span><span class="sxs-lookup"><span data-stu-id="90753-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="90753-157">Alterar **Tipo de Destino Controlado** para **Articulação da Mão**</span><span class="sxs-lookup"><span data-stu-id="90753-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="90753-158">Alterar **Mão Rastreada** para **Direita**</span><span class="sxs-lookup"><span data-stu-id="90753-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="90753-159">Alterar **Articulação da Mão Rastreada** para **Pulso**</span><span class="sxs-lookup"><span data-stu-id="90753-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="90753-160">Configure o componente **Exibição Radial (Script)** :</span><span class="sxs-lookup"><span data-stu-id="90753-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="90753-161">Altere a **Direção de Referência** para **Orientada pelo Objeto** e, em seguida, marque a caixa **Orientar para Direção de Referência**</span><span class="sxs-lookup"><span data-stu-id="90753-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="90753-162">Altere **Distância Mínima** e **Distância Máxima** para 0</span><span class="sxs-lookup"><span data-stu-id="90753-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="90753-164">3. Testar o Solucionador de Exibição Radial usando a simulação no editor</span><span class="sxs-lookup"><span data-stu-id="90753-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="90753-165">Pressione o botão Reproduzir para entrar no modo de Jogo e pressione e segure a barra de espaços para levantar a mão.</span><span class="sxs-lookup"><span data-stu-id="90753-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="90753-166">Mova o cursor do mouse para mover a mão e clique e mantenha o botão esquerdo do mouse pressionado para girar a mão:</span><span class="sxs-lookup"><span data-stu-id="90753-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="90753-168">Parabéns</span><span class="sxs-lookup"><span data-stu-id="90753-168">Congratulations</span></span>

<span data-ttu-id="90753-169">Neste tutorial, você aprendeu a usar os solucionadores do MRTK para fazer uma interface do usuário intuitiva seguir o usuário.</span><span class="sxs-lookup"><span data-stu-id="90753-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="90753-170">Você também aprendeu a anexar um Solucionador a um objeto do jogo (ou seja, o cubo) para seguir as mãos acompanhadas do usuário.</span><span class="sxs-lookup"><span data-stu-id="90753-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="90753-171">Para saber mais sobre esses e outros solucionadores incluídos no MRTK, acesse o guia [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="90753-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="90753-172">Próximo tutorial: 5. Interagir com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="90753-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)

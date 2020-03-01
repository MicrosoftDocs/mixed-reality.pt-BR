---
title: Mão-executiva
description: as mãos 3D disparadas quando o sistema não detecta as mãos do usuário para ajudar a auxiliá-las.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Realidade mista do Windows, design, direito à mão, headset de imersão, MRTK, mãos, mãos de ajuda
ms.openlocfilehash: c5f0a0c241ff71dc93f370a5a8caa627128bfb1a
ms.sourcegitcommit: 1ec628a9107194c0a9d4073b5ca09ee816030e85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2020
ms.locfileid: "78202727"
---
# <a name="hand-coach"></a><span data-ttu-id="077ca-104">Mão-executiva</span><span class="sxs-lookup"><span data-stu-id="077ca-104">Hand coach</span></span>

<span data-ttu-id="077ca-105">A mão do direito são as mãos modeladas em 3D que são disparadas quando o sistema não detecta as mãos do usuário.</span><span class="sxs-lookup"><span data-stu-id="077ca-105">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="077ca-106">Isso é implementado como um componente "ensinando" que ajuda a orientar o usuário quando o gesto não foi ensinado.</span><span class="sxs-lookup"><span data-stu-id="077ca-106">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="077ca-107">Se os usuários não tiverem feito o gesto especificado por um período, as mãos entrarão em loop com um atraso.</span><span class="sxs-lookup"><span data-stu-id="077ca-107">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="077ca-108">A mão da direita poderia ser usada para representar o pressionamento de um botão ou a seleção de um holograma.</span><span class="sxs-lookup"><span data-stu-id="077ca-108">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  


<span data-ttu-id="077ca-109">Exemplo de ![: mão-](images/HandCoach/MRTK_handCoach.jpg)</span><span class="sxs-lookup"><span data-stu-id="077ca-109">![Example: Hand coach](images/HandCoach/MRTK_handCoach.jpg)</span></span><br>
<span data-ttu-id="077ca-110">*Exemplo de HandCoach de MRTK*</span><span class="sxs-lookup"><span data-stu-id="077ca-110">*HandCoach Example from MRTK*</span></span>

## <a name="hand-coach-provided"></a><span data-ttu-id="077ca-111">Mão da direita fornecida</span><span class="sxs-lookup"><span data-stu-id="077ca-111">Hand coach provided</span></span>

<span data-ttu-id="077ca-112">O modelo de interação atual representa uma ampla variedade de controles de gesto, como rolagem, seleção extrema e quase toque.</span><span class="sxs-lookup"><span data-stu-id="077ca-112">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="077ca-113">Abaixo está uma lista completa dos gestos de mão existentes fornecidos no<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span><span class="sxs-lookup"><span data-stu-id="077ca-113">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="077ca-114">![exemplo de próximo Select](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-114">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="077ca-115">**Exemplo de próximo Select-used mostrar como selecionar botões ou fechar objetos que interagem**</span><span class="sxs-lookup"><span data-stu-id="077ca-115">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="077ca-116">![exemplo de toque de ar](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-116">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="077ca-117">**Exemplo de toque de ar – usado para mostrar como selecionar objetos que estão distantes**</span><span class="sxs-lookup"><span data-stu-id="077ca-117">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="077ca-118">![exemplo de mover](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-118">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="077ca-119">**Exemplo de movimentação de um objeto em espaço-usado para mostrar como mover um holograma no espaço**</span><span class="sxs-lookup"><span data-stu-id="077ca-119">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="077ca-120">![exemplo de girar](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-120">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="077ca-121">**Exemplo de rotação – usado para mostrar como girar hologramas ou objetos**</span><span class="sxs-lookup"><span data-stu-id="077ca-121">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="077ca-122">![exemplo de escala](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-122">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="077ca-123">**Exemplo de escala-usado para mostrar como manipular hologramas para serem maiores ou menores**</span><span class="sxs-lookup"><span data-stu-id="077ca-123">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="077ca-124">![exemplo de Palm up](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-124">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="077ca-125">**Exemplo de Palm up – sugestão de uso, para exibir menus à mão**</span><span class="sxs-lookup"><span data-stu-id="077ca-125">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="077ca-126">![exemplo de HandFlip](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-126">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="077ca-127">**Exbordo de mão invertida – outra maneira de exibir menus à mão**</span><span class="sxs-lookup"><span data-stu-id="077ca-127">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="077ca-128">![exemplo de](images/HandCoach/Scoll.gif) de rolagem</span><span class="sxs-lookup"><span data-stu-id="077ca-128">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="077ca-129">**Exemplo de Scroll – usado para rolar uma lista ou um documento longo**</span><span class="sxs-lookup"><span data-stu-id="077ca-129">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="077ca-130">Conceitos de design</span><span class="sxs-lookup"><span data-stu-id="077ca-130">Design concepts</span></span>

<span data-ttu-id="077ca-131">Para Hololens2, criamos interações de mão com base em gestos de instinctual e de mão natural.</span><span class="sxs-lookup"><span data-stu-id="077ca-131">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="077ca-132">Acreditamos que eles sejam intuitivos para a maioria dos usuários e, portanto, não criamos momentos de aprendizado de gestos dedicados.</span><span class="sxs-lookup"><span data-stu-id="077ca-132">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="077ca-133">Em vez disso, criamos a assistência de mão para ajudar os usuários que podem ficar presos ou que não estão familiarizados com a interação com os hologramas sobre esses gestos.</span><span class="sxs-lookup"><span data-stu-id="077ca-133">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="077ca-134">Sem um momento de aprendizado, sentimos que mostrar aos usuários como executar uma ação demonstrando que seria a melhor opção.</span><span class="sxs-lookup"><span data-stu-id="077ca-134">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="077ca-135">Em nossos estudos, descobrimos que os usuários conseguiram descobrir o gesto, mas precisavam de uma pequena orientação.</span><span class="sxs-lookup"><span data-stu-id="077ca-135">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="077ca-136">Se detectarmos que um usuário não interage com um objeto por um período, uma mão orientada seria disparada demonstrando o posicionamento correto e o local do dedo.</span><span class="sxs-lookup"><span data-stu-id="077ca-136">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="077ca-137">Simples</span><span class="sxs-lookup"><span data-stu-id="077ca-137">Intuitive</span></span>

<span data-ttu-id="077ca-138">Ao animar as mãos, deve ser óbvio e shoudn't causar qualquer confusão.</span><span class="sxs-lookup"><span data-stu-id="077ca-138">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="077ca-139">A animação das mãos é uma representação do gesto que você está tentando evocar ao usuário para entender sua finalidade.</span><span class="sxs-lookup"><span data-stu-id="077ca-139">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="077ca-140">Por exemplo, se você quiser que um usuário pressione um botão, um botão à mão será disparado.</span><span class="sxs-lookup"><span data-stu-id="077ca-140">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="077ca-141">![exemplo: mão com o direito ao lado de toque](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-141">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="077ca-142">*Mão da direita demonstrando perto de tocar em uma gem*</span><span class="sxs-lookup"><span data-stu-id="077ca-142">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="077ca-143">Escala manual</span><span class="sxs-lookup"><span data-stu-id="077ca-143">Hand scale</span></span>

<span data-ttu-id="077ca-144">Testamos vários tamanhos de mão com os menus da interface do usuário e sentimos que, se as mãos fossem verdadeiras para o tamanho, ela deu uma menacing, mas se fosse muito pequena, era difícil ver e entender o gesto.</span><span class="sxs-lookup"><span data-stu-id="077ca-144">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="077ca-145">**Voz e mãos**</span><span class="sxs-lookup"><span data-stu-id="077ca-145">**Voice over and hands**</span></span>

<span data-ttu-id="077ca-146">Não espere que os usuários possam ouvir um conjunto de instruções por meio de voz e assistir a instruções diferentes por meio da mão.</span><span class="sxs-lookup"><span data-stu-id="077ca-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="077ca-147">Sequenciar suas instruções para ajudar os usuários a se concentrarem em relação à sua atenção para reduzir a sobrecarga do sensor.</span><span class="sxs-lookup"><span data-stu-id="077ca-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="077ca-148">Posso criar o meu próprio?</span><span class="sxs-lookup"><span data-stu-id="077ca-148">Can I create my own?</span></span>

<span data-ttu-id="077ca-149">Sim!</span><span class="sxs-lookup"><span data-stu-id="077ca-149">Yes!</span></span> <span data-ttu-id="077ca-150">Incentivamos você a criar seu próprio gesto exclusivo para seu jogo e contribuir de volta para a Comunidade!</span><span class="sxs-lookup"><span data-stu-id="077ca-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="077ca-151">Fornecemos um arquivo Maya de um rigged Hand que pode ser usado para seu aplicativo que pode ser baixado aqui: <a href="files/HandCoach_MRTK.zip">baixar HandCoach_MRTK. zip</a></span><span class="sxs-lookup"><span data-stu-id="077ca-151">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="077ca-152">![exemplo de mãos animadas no Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="077ca-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="077ca-153">*Exemplo de mão animada ao investigar uma caixa no Maya*</span><span class="sxs-lookup"><span data-stu-id="077ca-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="077ca-154">**Ferramenta de criação recomendada**</span><span class="sxs-lookup"><span data-stu-id="077ca-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="077ca-155">Entre artistas 3D, muitos optam por usar o [Maya do Autodesk, que é capaz de usar o HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar a maneira como os ativos são criados.</span><span class="sxs-lookup"><span data-stu-id="077ca-155">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="077ca-156">O arquivo hands fornecido é um arquivo binário Maya, portanto, é recomendável usar Maya para animar e exportar as mãos.</span><span class="sxs-lookup"><span data-stu-id="077ca-156">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="077ca-157">Se você preferir usar outro programa 3D, aqui está um <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">Baixe HandCoachMRTK_FBX. zip</a> para criar sua própria configuração de controlador.</span><span class="sxs-lookup"><span data-stu-id="077ca-157">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="077ca-158">Se estiver usando o arquivo de mão Maya baixado fornecido, é recomendável reduzir verticalmente as mãos no Unity para 0,6.</span><span class="sxs-lookup"><span data-stu-id="077ca-158">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="077ca-159">![exemplo: mão do Maya Rig em](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="077ca-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="077ca-160">*Rigged hands*</span><span class="sxs-lookup"><span data-stu-id="077ca-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="077ca-161">Especificações técnicas</span><span class="sxs-lookup"><span data-stu-id="077ca-161">Technical Specs</span></span>

*   <span data-ttu-id="077ca-162">O arquivo de dois mãos está disponível no formato ASCII Maya</span><span class="sxs-lookup"><span data-stu-id="077ca-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="077ca-163">A mão direita e esquerda está disponível no formato binário Maya</span><span class="sxs-lookup"><span data-stu-id="077ca-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="077ca-164">Definir o arquivo Maya para 24 FPS</span><span class="sxs-lookup"><span data-stu-id="077ca-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="077ca-165">Dentro do arquivo, há um lado esquerdo e direito que pode ser usado para gestos de dois mão ou de mão única.</span><span class="sxs-lookup"><span data-stu-id="077ca-165">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="077ca-166">A mão direita só estará visível por padrão.</span><span class="sxs-lookup"><span data-stu-id="077ca-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="077ca-167">É recomendável deixar um buffer de cerca de 10 quadros no início e no final para esmaecer</span><span class="sxs-lookup"><span data-stu-id="077ca-167">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="077ca-168">Se animar um objeto com um destino especificado, sua prática recomendada será animar para uma caixa padrão ou NULL.</span><span class="sxs-lookup"><span data-stu-id="077ca-168">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="077ca-169">Se a mão estiver animando um objeto físico, como uma caixa, sua melhor prática para não animar a tradução em Maya, mas esperar para animá-la no Unity ou no código.</span><span class="sxs-lookup"><span data-stu-id="077ca-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="077ca-170">A animação visível deve ser 1,5 segundos para que todas as informações significativas sejam transmitidas</span><span class="sxs-lookup"><span data-stu-id="077ca-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="077ca-171">Quando você sentir satisfeito com sua animação:</span><span class="sxs-lookup"><span data-stu-id="077ca-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="077ca-172">Selecionar todas as junções e distortar quadros-chave</span><span class="sxs-lookup"><span data-stu-id="077ca-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="077ca-173">Exclua os controladores, selecione as junções e a malha e exporte como um FBX</span><span class="sxs-lookup"><span data-stu-id="077ca-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="077ca-174">Se houver várias animações, você poderá usar o exportador de jogos interno do Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="077ca-174">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="077ca-175">Exportando do Maya</span><span class="sxs-lookup"><span data-stu-id="077ca-175">Exporting from Maya</span></span>

<span data-ttu-id="077ca-176">Depois de estar satisfeito com sua animação</span><span class="sxs-lookup"><span data-stu-id="077ca-176">After you are satisfied with your animation</span></span>
* <span data-ttu-id="077ca-177">Selecionar todas as junções: selecionar hierarquia de ></span><span class="sxs-lookup"><span data-stu-id="077ca-177">Select all joints: Select > Hierarchy</span></span>

     ![Exemplo: local do menu](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="077ca-179">Distortar sua animação: alternar para animação > chave > animação de torta</span><span class="sxs-lookup"><span data-stu-id="077ca-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Exemplo: local do menu](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="077ca-181">Excluir o dispositivo de controlador: contorno > MainR_Grp ou MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="077ca-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Exemplo: local do menu](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="077ca-183">Exportar como FBX: selecione JNT + malha: arquivo > Exportar seleção (caixa de opção) > Exportar seleção</span><span class="sxs-lookup"><span data-stu-id="077ca-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Exemplo: local do menu](images/HandCoach/OptionBox.png)<br>

     ![Exemplo: local do menu](images/HandCoach/SelectionExport.png)<br>

     ![Exemplo: local do menu](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="077ca-187">Ao exportar como um FBX e trazido para o Unity, dimensione as mãos para 0,6.</span><span class="sxs-lookup"><span data-stu-id="077ca-187">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="077ca-188">Descobrimos que esse foi um equilíbrio perfeito para a exibição das mãos.</span><span class="sxs-lookup"><span data-stu-id="077ca-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="077ca-189">Exemplo de ![: configurações de Unity](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="077ca-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="077ca-190">*Configurações de Unity para HandCoach_R pré-fabricado encontradas em MRTK*</span><span class="sxs-lookup"><span data-stu-id="077ca-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="077ca-191">Implementando mãos em seu projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="077ca-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="077ca-192">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="077ca-192">Best practices</span></span>
*    <span data-ttu-id="077ca-193">É recomendável reduzir verticalmente as mãos no Unity para 0,6</span><span class="sxs-lookup"><span data-stu-id="077ca-193">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="077ca-194">As mãos devem ser executadas duas vezes e, se não forem concluídas, passarão continuamente em loop até que o gesto seja concluído.</span><span class="sxs-lookup"><span data-stu-id="077ca-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="077ca-195">As mãos devem ser repetidas duas vezes para garantir que o usuário tenha tempo para se registrar e ver o gesto.</span><span class="sxs-lookup"><span data-stu-id="077ca-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="077ca-196">As mãos devem aparecer e desaparecer entre os loops.</span><span class="sxs-lookup"><span data-stu-id="077ca-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="077ca-197">Se as mãos do usuário estiverem visíveis por câmeras HL2, mas os usuários não estiverem fazendo a interação necessária, as mãos serão exibidas após 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="077ca-197">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="077ca-198">Se as mãos do usuário não estiverem visíveis por câmeras HL2, as mãos aparecerão após 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="077ca-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="077ca-199">Se as mãos do usuário forem visivelmente rastreadas por câmeras HL2s no meio da animação, a animação será concluída e desaparecer.</span><span class="sxs-lookup"><span data-stu-id="077ca-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="077ca-200">Se você estiver incluindo a voz, sugerimos que ela corresponda ao gesto da mão.</span><span class="sxs-lookup"><span data-stu-id="077ca-200">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="077ca-201">Se você tiver ensinado as mãos pelo menos uma vez, repita o gesto se tiver detectado que o usuário está preso.</span><span class="sxs-lookup"><span data-stu-id="077ca-201">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="077ca-202">Se as posições de dedos/mãos específicas forem críticas, verifique se os usuários podem ver claramente essas nuances na animação.</span><span class="sxs-lookup"><span data-stu-id="077ca-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="077ca-203">Experimente Angling as mãos para que as partes mais importantes fiquem claramente visíveis.</span><span class="sxs-lookup"><span data-stu-id="077ca-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="077ca-204">Se você perceber distorção nas mãos, precisará ir para as configurações de qualidade do Unity aumentar a quantidade de Bones.</span><span class="sxs-lookup"><span data-stu-id="077ca-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="077ca-205">Acesse as configurações de projeto de > de edição do Unity > qualidade > outros pesos do Blend >.</span><span class="sxs-lookup"><span data-stu-id="077ca-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="077ca-206">Verifique se "4 Bones" estão selecionados para ver as junções suaves.</span><span class="sxs-lookup"><span data-stu-id="077ca-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![Exemplo: local do menu](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="077ca-208">O que evitar</span><span class="sxs-lookup"><span data-stu-id="077ca-208">What to avoid</span></span>
* <span data-ttu-id="077ca-209">Dimensionar as mãos muito grandes</span><span class="sxs-lookup"><span data-stu-id="077ca-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="077ca-210">colocar as mãos muito próximas ao usuário</span><span class="sxs-lookup"><span data-stu-id="077ca-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="077ca-211">As mãos só devem ser ensinadas uma vez.</span><span class="sxs-lookup"><span data-stu-id="077ca-211">Hands should only be taught once.</span></span> <span data-ttu-id="077ca-212">O excesso de ensino pode causar confusão e bagunças</span><span class="sxs-lookup"><span data-stu-id="077ca-212">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="077ca-213">Colocando-o no Unity, baixe o MRTK mais recente aqui: https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="077ca-213">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="077ca-214">Material: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="077ca-214">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="077ca-215">Scripts: consulte as diretrizes do MRTK para o <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">MRTK Hand</a></span><span class="sxs-lookup"><span data-stu-id="077ca-215">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="077ca-216">Configuração por projeto</span><span class="sxs-lookup"><span data-stu-id="077ca-216">Per- project setting</span></span>
        *   <span data-ttu-id="077ca-217">Cena definida como UWP: a instrução pode ser encontrada no [projeto do Unity de configuração](Configure-Unity-Project.md) para o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="077ca-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="077ca-218">Consulte também</span><span class="sxs-lookup"><span data-stu-id="077ca-218">See also</span></span>
* [<span data-ttu-id="077ca-219">Interação-conceitos básicos</span><span class="sxs-lookup"><span data-stu-id="077ca-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="077ca-220">Processo de criação de ativos</span><span class="sxs-lookup"><span data-stu-id="077ca-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="077ca-221">Gestos</span><span class="sxs-lookup"><span data-stu-id="077ca-221">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="077ca-222">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="077ca-222">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="077ca-223">Configurar projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="077ca-223">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="077ca-224">Visão geral do desenvolvimento do Unity</span><span class="sxs-lookup"><span data-stu-id="077ca-224">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="077ca-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="077ca-225">MRTK 101</span></span>](mrtk-101.md)

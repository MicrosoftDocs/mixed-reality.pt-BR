---
title: Módulo de compartilhamento de aprendizagem do MR para o HoloLens 2
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 77ae779b4bb32dd66a722c9793d1b83c4a64ae2e
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485671"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="77449-104">4. Compartilhando movimentos de objetos com vários usuários</span><span class="sxs-lookup"><span data-stu-id="77449-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="77449-105">Neste tutorial, aprenderemos como compartilhar os movimentos dos objetos para que todos os participantes de uma sessão compartilhada possam colaborar juntos e exibir as interações de cada um deles.</span><span class="sxs-lookup"><span data-stu-id="77449-105">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="77449-106">Esta lição baseia-se no iniciador lunar criado como parte dos [tutoriais do módulo base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="77449-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="77449-107">Seus</span><span class="sxs-lookup"><span data-stu-id="77449-107">Objectives:</span></span>

- <span data-ttu-id="77449-108">Traga o iniciador lunar como o modelo 3D a ser compartilhado</span><span class="sxs-lookup"><span data-stu-id="77449-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="77449-109">Configure seu projeto para compartilhar os movimentos do modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="77449-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="77449-110">Saiba como criar um aplicativo de colaboração de vários usuários básico</span><span class="sxs-lookup"><span data-stu-id="77449-110">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="77449-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="77449-111">Instructions</span></span>


1. <span data-ttu-id="77449-112">Salve a cena da lição anterior (Control + S).</span><span class="sxs-lookup"><span data-stu-id="77449-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="77449-113">Você pode nomeá-lo, HLSharedProjectMainPart4. Unity, para que seja mais fácil encontrá-lo quando precisar.</span><span class="sxs-lookup"><span data-stu-id="77449-113">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="77449-114">Na janela do projeto, na pasta ativos-> scripts, clique duas vezes em GenericNetSync para abri-lo no Visual Studio ou no editor de código que você está usando.</span><span class="sxs-lookup"><span data-stu-id="77449-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="77449-116">Nas linhas 34 e 38, remova o//para ativar o código da tabela que usaremos nesta lição.</span><span class="sxs-lookup"><span data-stu-id="77449-116">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="77449-117">em seguida, salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="77449-117">next, Save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="77449-119">Na janela do projeto, clique duas vezes no arquivo PhotonRoom.cs na pasta Assets-> scripts para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77449-119">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="77449-121">Assim como na etapa 3, precisamos remover o//para ativar o código nas linhas 25, 26 e 106.</span><span class="sxs-lookup"><span data-stu-id="77449-121">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="77449-124">Na exibição hierarquia, selecione o objeto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="77449-124">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="77449-126">Na exibição do projeto, navegue até ativos-> recursos-> pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="77449-126">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="77449-127">Primeiro, arraste e solte a tabela pré-fabricado para o slot Tableprefab na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="77449-127">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="77449-128">Em seguida, arraste e solte o RocketLauncherCompleteVariantprefab para o slot pré-fabricado do módulo na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="77449-128">Next drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   <span data-ttu-id="77449-130">Observação: Se você clicar em um dos objetos pré-fabricado e liberar, o Inspetor alternará para esse objeto.</span><span class="sxs-lookup"><span data-stu-id="77449-130">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="77449-131">Clique em, arraste, solte e libere cada objeto para seu slot apropriado.</span><span class="sxs-lookup"><span data-stu-id="77449-131">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="77449-132">Clique na seta à esquerda de MixedRealityPlayspace e mova o objeto de jogo filho, MainCamera para baixo até o SharedPlayground pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="77449-132">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="77449-133">Em seguida, exclua o pré-fabricado, MixedRealityPlayspace, para excluir, selecione o pré-fabricado e toque em "excluir" no teclado).</span><span class="sxs-lookup"><span data-stu-id="77449-133">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="77449-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="77449-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="77449-135">Observação:  Verifique se as posições principal da câmera e do SharedPlayground estão definidas como 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="77449-135">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="77449-136">Crie um novo objeto Game definido como um objeto filho para o objeto pai SharedPlayground para criar um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="77449-136">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="77449-137">Clique com o botão direito do mouse no objeto pai e selecione criar vazio.</span><span class="sxs-lookup"><span data-stu-id="77449-137">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="77449-138">Com o novo objeto selecionado em sua hierarquia, altere o nome do objeto para TableAnchor no painel de Inspetor.</span><span class="sxs-lookup"><span data-stu-id="77449-138">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="77449-139">Além disso, clique em Adicionar componente e procure o componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="77449-139">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="77449-140">Selecione-o e adicione-o ao objeto.</span><span class="sxs-lookup"><span data-stu-id="77449-140">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="77449-142">Agora, no painel projeto na pasta pré-fabricados, arraste a tabela pré-fabricado para o objeto filho "TableAnchor" que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="77449-142">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="77449-144">Por fim, no objeto DebugWindow, altere a largura para 50 e a altura para 20.</span><span class="sxs-lookup"><span data-stu-id="77449-144">Finally, in the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="77449-146">Parabéns</span><span class="sxs-lookup"><span data-stu-id="77449-146">Congratulations</span></span>


<span data-ttu-id="77449-147">Depois que isso for concluído, todos os usuários que ingressarem em seu projeto do Unity poderão mover o iniciador lunar.</span><span class="sxs-lookup"><span data-stu-id="77449-147">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="77449-148">Todos os movimentos são sincronizados para que cada usuário possa ver as interações das outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="77449-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="77449-149">Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhadas com recursos completos.</span><span class="sxs-lookup"><span data-stu-id="77449-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="77449-150">Embora todos os usuários estejam conectados como parte de uma experiência compartilhada e possam ver os movimentos relativos dos objetos, o aplicativo ainda não consegue alinhar com precisão os avatars e os objetos para que os usuários locais vejam uns aos outros e os objetos no mesmo local dentro do físico países.</span><span class="sxs-lookup"><span data-stu-id="77449-150">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="77449-151">Para ancorar experiências compartilhadas locais, cada dispositivo requer uma compreensão comum do ambiente físico.</span><span class="sxs-lookup"><span data-stu-id="77449-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="77449-152">Neste módulo, faremos isso usando o asa ( [âncoras espaciais) do Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) que será implementado na próxima lição.</span><span class="sxs-lookup"><span data-stu-id="77449-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="77449-153">Antes de prosseguir para a próxima lição, precisaremos concluir o módulo de aprendizado do ASA que aborda noções básicas do ASA, criação de contas e recursos do Azure e outros blocos de edifícios fundamentais necessários para que possamos integrá-lo à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="77449-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="77449-154">[Próxima lição: 5. Integrar Âncoras Espaciais do Azure em uma experiência compartilhada](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="77449-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>


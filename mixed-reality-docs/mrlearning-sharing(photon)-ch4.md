---
title: Tutoriais de funcionalidades de vários usuários-4. Compartilhando movimentos de objetos com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b4713caf2c4d913fe8f5b01c08b3cd0152e32cd9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438371"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="32519-105">4. compartilhando movimentos de objeto com vários usuários</span><span class="sxs-lookup"><span data-stu-id="32519-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="32519-106">Neste tutorial, você aprenderá a compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada possam colaborar e exibir as interações de cada uma das outras.</span><span class="sxs-lookup"><span data-stu-id="32519-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="32519-107">Esta lição baseia-se no iniciador lunar criado como parte dos [tutoriais do módulo base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="32519-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="32519-108">Seus</span><span class="sxs-lookup"><span data-stu-id="32519-108">Objectives:</span></span>

- <span data-ttu-id="32519-109">Traga o iniciador lunar como o modelo 3D a ser compartilhado</span><span class="sxs-lookup"><span data-stu-id="32519-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="32519-110">Configurar seu projeto para compartilhar os movimentos do modelo 3D</span><span class="sxs-lookup"><span data-stu-id="32519-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="32519-111">Saiba como criar um aplicativo de colaboração de vários usuários básico</span><span class="sxs-lookup"><span data-stu-id="32519-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="32519-112">Instruções</span><span class="sxs-lookup"><span data-stu-id="32519-112">Instructions</span></span>


1. <span data-ttu-id="32519-113">Salve a cena da lição anterior (Control + S).</span><span class="sxs-lookup"><span data-stu-id="32519-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="32519-114">Você pode nomeá-lo de HLSharedProjectMainPart4. Unity para que seja mais fácil encontrá-lo quando precisar.</span><span class="sxs-lookup"><span data-stu-id="32519-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="32519-115">Na janela do projeto, na pasta ativos-> scripts, clique duas vezes em GenericNetSync para abri-lo no Visual Studio ou no editor de código que você está usando.</span><span class="sxs-lookup"><span data-stu-id="32519-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="32519-117">Nas linhas 34 e 38, remova "//" para ativar o código da tabela que será usada nesta lição.</span><span class="sxs-lookup"><span data-stu-id="32519-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="32519-118">Em seguida, salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="32519-118">Next, save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="32519-120">Na janela do projeto, clique duas vezes no arquivo PhotonRoom.cs na pasta Assets-> scripts para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32519-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="32519-122">Assim como na etapa 3, precisamos remover "//" para ativar o código nas linhas 25, 26 e 106.</span><span class="sxs-lookup"><span data-stu-id="32519-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="32519-125">Na exibição hierarquia, selecione o objeto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="32519-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="32519-127">Na exibição do projeto, navegue até ativos-> recursos-> pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="32519-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="32519-128">Primeiro, arraste e solte a tabela pré-fabricado para o slot Tableprefab na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="32519-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="32519-129">Em seguida, arraste e solte o RocketLauncherCompleteVariantprefab para o slot pré-fabricado do módulo na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="32519-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

<span data-ttu-id="32519-131">Observação: se você clicar em um dos objetos pré-fabricado e liberar, o Inspetor alternará para esse objeto.</span><span class="sxs-lookup"><span data-stu-id="32519-131">Note: If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="32519-132">Clique em, arraste, solte e libere cada objeto para seu slot apropriado.</span><span class="sxs-lookup"><span data-stu-id="32519-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="32519-133">Clique na seta à esquerda de MixedRealityPlayspace e mova o objeto de jogo filho MainCamera para baixo para o SharedPlayground pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="32519-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="32519-134">Em seguida, exclua o pré-fabricado, MixedRealityPlayspace selecionando o pré-fabricado e toque em "excluir" no teclado).</span><span class="sxs-lookup"><span data-stu-id="32519-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="32519-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="32519-135">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="32519-136">Observação: Verifique se as posições principal da câmera e do SharedPlayground estão definidas como 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="32519-136">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="32519-137">Crie um novo objeto Game definido como um objeto filho para o objeto pai SharedPlayground para criar um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="32519-137">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="32519-138">Clique com o botão direito do mouse no objeto pai e selecione criar vazio.</span><span class="sxs-lookup"><span data-stu-id="32519-138">Right-click the parent object and select Create Empty.</span></span> 

10. <span data-ttu-id="32519-139">Com o novo objeto selecionado em sua hierarquia, altere o nome do objeto para TableAnchor no painel de Inspetor.</span><span class="sxs-lookup"><span data-stu-id="32519-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="32519-140">Além disso, clique em Adicionar componente e procure o componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="32519-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="32519-141">Selecione-o e adicione-o ao objeto.</span><span class="sxs-lookup"><span data-stu-id="32519-141">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="32519-143">No painel projeto na pasta pré-fabricados, arraste a tabela pré-fabricado para o objeto filho "TableAnchor" que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="32519-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="32519-145">No objeto DebugWindow, altere a largura para 50 e a altura para 20.</span><span class="sxs-lookup"><span data-stu-id="32519-145">In the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="32519-147">Parabéns</span><span class="sxs-lookup"><span data-stu-id="32519-147">Congratulations</span></span>


<span data-ttu-id="32519-148">Depois que isso for concluído, todos os usuários que ingressarem em seu projeto do Unity poderão mover o iniciador lunar.</span><span class="sxs-lookup"><span data-stu-id="32519-148">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="32519-149">Todos os movimentos são sincronizados para que cada usuário possa ver as interações das outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="32519-149">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="32519-150">Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhadas com recursos completos.</span><span class="sxs-lookup"><span data-stu-id="32519-150">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="32519-151">Embora todos os usuários estejam conectados como parte de uma experiência compartilhada e possam ver os movimentos relativos dos objetos, o aplicativo ainda não consegue alinhar precisamente os avatars e objetos para que os usuários locais vejam uns aos outros e que estejam no mesmo local dentro do físico países.</span><span class="sxs-lookup"><span data-stu-id="32519-151">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="32519-152">Para ancorar experiências compartilhadas locais, cada dispositivo requer uma compreensão comum do ambiente físico.</span><span class="sxs-lookup"><span data-stu-id="32519-152">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="32519-153">Neste módulo, faremos isso usando o asa ( [âncoras espaciais) do Azure](<https://azure.microsoft.com//services/spatial-anchors/>) que será implementado na próxima lição.</span><span class="sxs-lookup"><span data-stu-id="32519-153">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="32519-154">Antes de prosseguir para a próxima lição, precisaremos concluir o módulo de aprendizagem do ASA que aborda as noções básicas do ASA, a criação de contas e recursos do Azure, bem como outros blocos de edifícios fundamentais necessários para que possamos integrá-lo à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="32519-154">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="32519-155">[Próxima lição: 5. integração das âncoras espaciais do Azure em uma experiência compartilhada](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="32519-155">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>


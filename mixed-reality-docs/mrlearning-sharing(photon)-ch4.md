---
title: Tutoriais de funcionalidades de vários usuários-4. Compartilhando movimentos de objetos com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: f1bcbbd368635c25207127142f21ff50f26a7b58
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901487"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="79109-105">4. compartilhando movimentos de objeto com vários usuários</span><span class="sxs-lookup"><span data-stu-id="79109-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="79109-106">Neste tutorial, você aprenderá a compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada possam colaborar e exibir as interações de cada uma das outras.</span><span class="sxs-lookup"><span data-stu-id="79109-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="79109-107">Esta lição baseia-se no iniciador lunar criado como parte dos [tutoriais do módulo base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="79109-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="79109-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="79109-108">Objectives</span></span>

- <span data-ttu-id="79109-109">Traga o iniciador lunar como o modelo 3D a ser compartilhado</span><span class="sxs-lookup"><span data-stu-id="79109-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="79109-110">Configurar seu projeto para compartilhar os movimentos do modelo 3D</span><span class="sxs-lookup"><span data-stu-id="79109-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="79109-111">Saiba como criar um aplicativo de colaboração de vários usuários básico</span><span class="sxs-lookup"><span data-stu-id="79109-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="79109-112">Instruções</span><span class="sxs-lookup"><span data-stu-id="79109-112">Instructions</span></span>

1. <span data-ttu-id="79109-113">Salve a cena da lição anterior (Control + S).</span><span class="sxs-lookup"><span data-stu-id="79109-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="79109-114">Você pode nomeá-lo de HLSharedProjectMainPart4. Unity para que seja mais fácil encontrá-lo quando precisar.</span><span class="sxs-lookup"><span data-stu-id="79109-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="79109-115">Na janela do projeto, na pasta ativos-> scripts, clique duas vezes em GenericNetSync para abri-lo no Visual Studio ou no editor de código que você está usando.</span><span class="sxs-lookup"><span data-stu-id="79109-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="79109-117">Nas linhas 34 e 38, remova "//" para ativar o código da tabela que será usada nesta lição.</span><span class="sxs-lookup"><span data-stu-id="79109-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="79109-118">Em seguida, salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="79109-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="79109-120">Na janela do projeto, clique duas vezes no arquivo PhotonRoom.cs na pasta Assets-> scripts para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79109-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="79109-122">Assim como na etapa 3, precisamos remover "//" para ativar o código nas linhas 25, 26 e 106.</span><span class="sxs-lookup"><span data-stu-id="79109-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="79109-125">Na exibição hierarquia, selecione o objeto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="79109-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="79109-127">Na exibição do projeto, navegue até ativos-> recursos-> pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="79109-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="79109-128">Primeiro, arraste e solte a tabela pré-fabricado para o slot Tableprefab na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="79109-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="79109-129">Em seguida, arraste e solte o RocketLauncherCompleteVariantprefab para o slot pré-fabricado do módulo na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="79109-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="79109-131">Se você clicar em um dos objetos pré-fabricado e liberar, o Inspetor alternará para esse objeto.</span><span class="sxs-lookup"><span data-stu-id="79109-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="79109-132">Clique em, arraste, solte e libere cada objeto para seu slot apropriado.</span><span class="sxs-lookup"><span data-stu-id="79109-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="79109-133">Clique na seta à esquerda de MixedRealityPlayspace e mova o objeto de jogo filho MainCamera para baixo para o SharedPlayground pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="79109-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="79109-134">Em seguida, exclua o pré-fabricado, MixedRealityPlayspace selecionando o pré-fabricado e toque em "excluir" no teclado).</span><span class="sxs-lookup"><span data-stu-id="79109-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="79109-136">Verifique se as posições principal da câmera e do SharedPlayground estão definidas como 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="79109-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="79109-137">Selecione o objeto "SharedPlayground" e clique com o botão direito do mouse para escolher a opção "criar vazio" para criar um objeto de jogo vazio como um filho do objeto de jogo "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="79109-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="79109-139">Com o novo objeto selecionado em sua hierarquia, altere o nome do objeto para TableAnchor no painel de Inspetor.</span><span class="sxs-lookup"><span data-stu-id="79109-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="79109-140">Além disso, clique em Adicionar componente e procure o componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="79109-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="79109-141">Selecione-o e adicione-o ao objeto.</span><span class="sxs-lookup"><span data-stu-id="79109-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="79109-143">No painel projeto na pasta pré-fabricados, arraste a tabela pré-fabricado para o objeto filho "TableAnchor" que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="79109-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="79109-145">Parabéns</span><span class="sxs-lookup"><span data-stu-id="79109-145">Congratulations</span></span>

<span data-ttu-id="79109-146">Quando isso for concluído, procure localizar o módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="79109-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="79109-147">Depois disso, todos os usuários que ingressarem em seu projeto do Unity poderão mover o iniciador lunar.</span><span class="sxs-lookup"><span data-stu-id="79109-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="79109-148">Todos os movimentos são sincronizados para que cada usuário possa ver as interações das outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="79109-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="79109-149">Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhadas com recursos completos.</span><span class="sxs-lookup"><span data-stu-id="79109-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="79109-150">Embora todos os usuários estejam conectados como parte de uma experiência compartilhada e possam ver os movimentos relativos dos objetos, o aplicativo ainda não consegue alinhar precisamente os avatars e objetos para que os usuários locais não possam ver uns aos outros e os objetos no mesmo local dentro do mundo físico.</span><span class="sxs-lookup"><span data-stu-id="79109-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="79109-151">Para ancorar experiências compartilhadas locais, cada dispositivo requer uma compreensão comum do ambiente físico.</span><span class="sxs-lookup"><span data-stu-id="79109-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="79109-152">Neste módulo, faremos isso usando o asa ( [âncoras espaciais) do Azure](<https://azure.microsoft.com//services/spatial-anchors/>) que será implementado na próxima lição.</span><span class="sxs-lookup"><span data-stu-id="79109-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="79109-153">Antes de prosseguir para a próxima lição, precisaremos concluir o módulo de aprendizagem do ASA que aborda as noções básicas do ASA, a criação de contas e recursos do Azure, bem como outros blocos de edifícios fundamentais necessários para que possamos integrá-lo à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="79109-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="79109-154">[Próxima lição: 5. integração das âncoras espaciais do Azure em uma experiência compartilhada](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="79109-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>

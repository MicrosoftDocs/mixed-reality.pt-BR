---
title: Tutoriais de recursos multiusuário – 4. Compartilhar movimentações de objeto com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031245"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="3cb00-105">4. Compartilhar movimentações de objeto com vários usuários</span><span class="sxs-lookup"><span data-stu-id="3cb00-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="3cb00-106">Neste tutorial, você aprenderá a compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada possam colaborar e exibir as interações uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="3cb00-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="3cb00-107">Esta lição baseia-se no Iniciador Lunar criado como parte dos [Tutoriais do Módulo Base](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="3cb00-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="3cb00-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3cb00-108">Objectives</span></span>

- <span data-ttu-id="3cb00-109">Traga o iniciador lunar como o modelo 3D a ser compartilhado</span><span class="sxs-lookup"><span data-stu-id="3cb00-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="3cb00-110">Configurar seu projeto para compartilhar os movimentos do modelo 3D</span><span class="sxs-lookup"><span data-stu-id="3cb00-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="3cb00-111">Saiba como criar um aplicativo básico de colaboração de vários usuários</span><span class="sxs-lookup"><span data-stu-id="3cb00-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="3cb00-112">Instruções</span><span class="sxs-lookup"><span data-stu-id="3cb00-112">Instructions</span></span>

1. <span data-ttu-id="3cb00-113">Salve a cena da lição anterior (Control+S).</span><span class="sxs-lookup"><span data-stu-id="3cb00-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="3cb00-114">Você pode dar a ela o nome de HLSharedProjectMainPart4.Unity para que seja mais fácil encontrá-la quando precisar.</span><span class="sxs-lookup"><span data-stu-id="3cb00-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="3cb00-115">Na janela Projeto, na pasta Ativos->Scripts, clique duas vezes em GenericNetSync para abri-la no Visual Studio ou no editor de código que você está usando.</span><span class="sxs-lookup"><span data-stu-id="3cb00-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="3cb00-117">Nas linhas 34 e 38, remova "//" para ativar o código da tabela que será usada nesta lição.</span><span class="sxs-lookup"><span data-stu-id="3cb00-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="3cb00-118">Em seguida, salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="3cb00-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="3cb00-120">Na janela Projeto, clique duas vezes no arquivo PhotonRoom.cs na pasta Ativos->Scripts para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3cb00-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="3cb00-122">Assim como na Etapa 3, precisamos remover "//" para ativar o código nas linhas 25, 26 e 106.</span><span class="sxs-lookup"><span data-stu-id="3cb00-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="3cb00-125">Na exibição Hierarquia, selecione o objeto NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="3cb00-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="3cb00-127">Na exibição do projeto, navegue até Ativos->Recursos->Pré-Fabricados.</span><span class="sxs-lookup"><span data-stu-id="3cb00-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="3cb00-128">Primeiro, arraste e solte o pré-fabricado Tabela para o slot Tableprefab na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="3cb00-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="3cb00-129">Em seguida, arraste e solte o RocketLauncherCompleteVariantprefab para o slot Pré-Fabricado do Módulo na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="3cb00-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="3cb00-131">Se você clicar em um dos objetos pré-fabricado e soltar, o Inspetor alternará para esse objeto.</span><span class="sxs-lookup"><span data-stu-id="3cb00-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="3cb00-132">Clique, arraste, solte e libere cada objeto para seu slot apropriado.</span><span class="sxs-lookup"><span data-stu-id="3cb00-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="3cb00-133">Clique na seta à esquerda de MixedRealityPlayspace e mova o objeto de jogo filho MainCamera para baixo para o pré-fabricado SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="3cb00-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="3cb00-134">Em seguida, exclua o pré-fabricado MixedRealityPlayspace selecionando o pré-fabricado e toque em "delete" no teclado).</span><span class="sxs-lookup"><span data-stu-id="3cb00-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="3cb00-136">Verifique se as posições de SharedPlayground e Câmera Principal estão definidas como 0,0,0.</span><span class="sxs-lookup"><span data-stu-id="3cb00-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="3cb00-137">Selecione o objeto "SharedPlayground" e clique com o botão direito do mouse para escolher a opção "criar vazio" para criar um objeto de jogo vazio como um filho do objeto de jogo "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="3cb00-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="3cb00-139">Com o novo objeto selecionado em sua hierarquia, altere o nome do objeto para TableAnchor no painel de Inspetor.</span><span class="sxs-lookup"><span data-stu-id="3cb00-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="3cb00-140">Além disso, clique em Adicionar Componente e pesquise o componente TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="3cb00-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="3cb00-141">Selecione-o e adicione-o ao objeto.</span><span class="sxs-lookup"><span data-stu-id="3cb00-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="3cb00-143">No painel Projeto na pasta Pré-Fabricados, arraste a tabela Pré-Fabricado para o objeto filho "TableAnchor" que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="3cb00-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="3cb00-145">Parabéns</span><span class="sxs-lookup"><span data-stu-id="3cb00-145">Congratulations</span></span>

<span data-ttu-id="3cb00-146">Quando isso for concluído, procure localizar o módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="3cb00-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="3cb00-147">Depois disso, todos os usuários que ingressarem em seu projeto do Unity poderão mover o iniciador lunar.</span><span class="sxs-lookup"><span data-stu-id="3cb00-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="3cb00-148">Todos os movimentos são sincronizados para que cada usuário possa ver as interações das outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="3cb00-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="3cb00-149">Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhadas com recursos completos.</span><span class="sxs-lookup"><span data-stu-id="3cb00-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="3cb00-150">Embora todos os usuários estejam conectados como parte de uma experiência compartilhada e possam ver os movimentos relativos dos objetos, o aplicativo ainda não consegue alinhar os avatars e os objetos com precisão, de modo que os usuários locais não conseguem ver uns aos outros e os objetos no mesmo local dentro do mundo físico.</span><span class="sxs-lookup"><span data-stu-id="3cb00-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="3cb00-151">Para ancorar experiências compartilhadas locais, cada dispositivo requer uma compreensão comum do ambiente físico.</span><span class="sxs-lookup"><span data-stu-id="3cb00-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="3cb00-152">Neste módulo, faremos isso usando ASA ([Âncoras Espaciais do Azure](<https://azure.microsoft.com//services/spatial-anchors/>)), que serão implementadas na próxima lição.</span><span class="sxs-lookup"><span data-stu-id="3cb00-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="3cb00-153">Antes de prosseguir para a próxima lição, precisaremos concluir o Módulo de Aprendizagem de ASA que aborda as noções básicas do ASA, a criação de contas e recursos do Azure, bem como outros blocos de construção fundamentais necessários antes que seja possível integrá-los à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="3cb00-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="3cb00-154">[Próxima lição: 5. Integrar Âncoras Espaciais do Azure em uma experiência compartilhada](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="3cb00-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>

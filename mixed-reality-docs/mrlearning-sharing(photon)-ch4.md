---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416007"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="c49c3-104">Sincronizando os movimentos de objetos compartilhados</span><span class="sxs-lookup"><span data-stu-id="c49c3-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="c49c3-105">Nesta lição, vamos aprenderá como compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada podem colaborar em conjunto e exibir as interações uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="c49c3-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="c49c3-106">Essa lição aproveita o iniciador Lunar que foi criado como parte do [base de dados de módulo tutoriais](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="c49c3-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="c49c3-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="c49c3-107">Objectives:</span></span>

- <span data-ttu-id="c49c3-108">Inclua o iniciador Lunar como o modelo 3D para ser compartilhado</span><span class="sxs-lookup"><span data-stu-id="c49c3-108">Bring in the Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="c49c3-109">Configure seu projeto para compartilhar os movimentos do modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="c49c3-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="c49c3-110">Saiba como criar um aplicativo básico de colaboração de multiusuário</span><span class="sxs-lookup"><span data-stu-id="c49c3-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="c49c3-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="c49c3-111">Instructions</span></span>

1. <span data-ttu-id="c49c3-112">Salve a cena da lição anterior (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="c49c3-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="c49c3-113">Você pode renomeá-lo "HLSharedProjectMainPart4.unity" para que ele seja mais fácil de encontrar quando precisar dele novamente.</span><span class="sxs-lookup"><span data-stu-id="c49c3-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="c49c3-114">Na janela do projeto, os ativos > pasta de Scripts, clique duas vezes na GenericNetSync para abri-lo no Visual Studio ou que nunca code editor que você está usando.</span><span class="sxs-lookup"><span data-stu-id="c49c3-114">In the Project window, in the Assets > Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="c49c3-115">Em linhas 34 e 38, remova o "/ /" para ativar o código para a tabela que serão usadas nesta lição.</span><span class="sxs-lookup"><span data-stu-id="c49c3-115">On lines 34 and 38, remove the "//" to activate the code for the Table that we will use in this lesson.</span></span>  <span data-ttu-id="c49c3-116">Em seguida, salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c49c3-116">Then Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="c49c3-117">Na janela do projeto, clique duas vezes no arquivo PhotonRoom.cs nos ativos > pasta de Scripts novamente abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c49c3-117">In the project window, double click on the PhotonRoom.cs file in the Assets > Scripts folder to again open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="c49c3-118">Assim como na etapa 3, é preciso remover o "/ /" para ativar o código em linhas, 25, 26 e 106.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="c49c3-118">Just like in step 3 we need to remove the "//" to activate the code at lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="c49c3-119">Na exibição de hierarquia, selecione o objeto NetworkRoom.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="c49c3-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="c49c3-120">Na exibição do projeto, navegue até ativos > recursos > pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="c49c3-120">In the project view, navigate to Assets > Resources > Prefabs.</span></span> <span data-ttu-id="c49c3-121">Primeiro, arraste e solte pré-fabricado tabela para o slot de "Tableprefab" na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="c49c3-121">First, drag and drop the Table prefab to the "Tableprefab" slot on the PhotonRoom class.</span></span> <span data-ttu-id="c49c3-122">Em seguida arraste e solte pré-fabricado LunarModule para o slot "Módulo pré-fabricado" na classe PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="c49c3-122">Next drag and drop the LunarModule prefab to the "Module Prefab" slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="c49c3-123">Observação: Se você clicar em um dos objetos pré-fabricado e versão, o Inspetor de alternará para o objeto.</span><span class="sxs-lookup"><span data-stu-id="c49c3-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="c49c3-124">Clique em, arraste, solte e liberar cada objeto em seu slot apropriado.</span><span class="sxs-lookup"><span data-stu-id="c49c3-124">Click, drag, drop and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="c49c3-125">Agora, clique na seta à esquerda de "MixedRealityPlayspace" e mover o objeto do jogo filho, "MainCamera" para baixo em pré-fabricado "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="c49c3-125">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="c49c3-126">Em seguida, exclua o pré-fabricado "MixedRealityPlayspace" (para excluir, selecione pré-fabricado e toque em "excluir" em seu teclado).</span><span class="sxs-lookup"><span data-stu-id="c49c3-126">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

<span data-ttu-id="c49c3-128">Observação:  Certifique-se de que as posições de câmera principal e o SharedPlayground serão definidas como 0, 0,0.</span><span class="sxs-lookup"><span data-stu-id="c49c3-128">note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="c49c3-129">Crie um novo objeto do jogo definido como um objeto filho ao objeto pai "SharedPlayground" (para criar um novo objeto, clique com botão direito no objeto pai e selecione "criar vazio").</span><span class="sxs-lookup"><span data-stu-id="c49c3-129">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span> 

10. <span data-ttu-id="c49c3-130">Com o novo objeto selecionado na sua hierarquia, altere o nome do objeto para "TableAnchor" no painel Inspetor.</span><span class="sxs-lookup"><span data-stu-id="c49c3-130">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="c49c3-131">Além disso, clique em "adicionar o componente" e pesquise o componente "TableAnchor".</span><span class="sxs-lookup"><span data-stu-id="c49c3-131">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="c49c3-132">Selecioná-lo e adicioná-lo ao objeto.</span><span class="sxs-lookup"><span data-stu-id="c49c3-132">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="c49c3-134">Observação: definir o posicionamento para x = 1, 0,55 = y e z = 2.</span><span class="sxs-lookup"><span data-stu-id="c49c3-134">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="c49c3-135">Além disso, definir a rotação com y = 90.</span><span class="sxs-lookup"><span data-stu-id="c49c3-135">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="c49c3-137">Agora no painel de projeto, na pasta "pré-fabricados", arraste pré-fabricado "table" para o objeto filho de "TableAnchor" você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="c49c3-137">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="c49c3-139">Por fim, no objeto "DebugWindow", altere a largura para 80 e a altura para 10.</span><span class="sxs-lookup"><span data-stu-id="c49c3-139">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="c49c3-141">Parabéns</span><span class="sxs-lookup"><span data-stu-id="c49c3-141">Congratulations</span></span>

<span data-ttu-id="c49c3-142">Quando isso for concluído, todos os usuários que unem a seu projeto do Unity podem se mover o iniciador Lunar.</span><span class="sxs-lookup"><span data-stu-id="c49c3-142">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="c49c3-143">Todos os movimentos são sincronizados para que cada usuário possa ver as interações uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="c49c3-143">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="c49c3-144">Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhado completos.</span><span class="sxs-lookup"><span data-stu-id="c49c3-144">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="c49c3-145">Embora todos os usuários estão conectados como parte de uma experiência de compartilhado e podem ver os movimentos relativos dos objetos, o aplicativo é ainda não é possível alinhar com precisão avatares e objetos para que os usuários locais veem uns aos outros e objetos no mesmo local físico dentro do mundo.</span><span class="sxs-lookup"><span data-stu-id="c49c3-145">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="c49c3-146">Para ancorar um local experiências compartilhadas, cada dispositivo requer um entendimento comum do ambiente físico.</span><span class="sxs-lookup"><span data-stu-id="c49c3-146">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="c49c3-147">Neste módulo, vamos fazer isso usando [âncoras espacial do Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), que será implementado na próxima lição.</span><span class="sxs-lookup"><span data-stu-id="c49c3-147">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="c49c3-148">Antes de prosseguir para a próxima lição, é necessário concluir o módulo de aprendizagem do ASA, que abordará Noções básicas do ASA, conta do Azure e criação de recursos e outros blocos de prédios fundamentais necessárias antes de nós pode integrar isso em nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="c49c3-148">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="c49c3-149">[Próxima lição: Sharing(Photon) lição 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="c49c3-149">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>


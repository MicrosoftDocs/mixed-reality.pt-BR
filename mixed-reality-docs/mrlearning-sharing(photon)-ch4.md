---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326579"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="7be89-104">Sincronizando os movimentos de objetos compartilhados</span><span class="sxs-lookup"><span data-stu-id="7be89-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="7be89-105">Nesta lição, vamos aprenderá como compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada podem colaborar em conjunto e exibir as interações uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="7be89-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="7be89-106">Essa lição aproveita o iniciador Lunar que foi criado como parte do [base de dados de módulo tutoriais](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="7be89-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="7be89-107">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="7be89-107">Objectives:</span></span>

- <span data-ttu-id="7be89-108">Importar o iniciador Lunar concluído como o modelo 3D sejam compartilhados</span><span class="sxs-lookup"><span data-stu-id="7be89-108">Import the completed Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="7be89-109">Configure seu projeto para compartilhar os movimentos do modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="7be89-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="7be89-110">Saiba como criar um aplicativo básico de colaboração de multiusuário</span><span class="sxs-lookup"><span data-stu-id="7be89-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="7be89-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="7be89-111">Instructions</span></span>

1. <span data-ttu-id="7be89-112">Salve a cena da lição anterior (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="7be89-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="7be89-113">Você pode renomeá-lo "HLSharedProjectMainPart4.unity" para que ele seja mais fácil de encontrar quando precisar dele novamente.</span><span class="sxs-lookup"><span data-stu-id="7be89-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="7be89-114">Exclua o objeto "NetworkLobby" (selecionando-o e pressionando a tecla delete).</span><span class="sxs-lookup"><span data-stu-id="7be89-114">Delete the "NetworkLobby" object (by selecting it and pressing delete).</span></span> <span data-ttu-id="7be89-115">Além disso, vá para a pasta "pré-fabricados" da lição 2 e excluir pré-fabricado "NetworkLobby" também.</span><span class="sxs-lookup"><span data-stu-id="7be89-115">Also, go into the "prefabs" folder from lesson 2 and delete the "NetworkLobby" prefab from there as well.</span></span>

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. <span data-ttu-id="7be89-117">Importar um novo pacote personalizado (como na etapa 2 da lição 2) e importe as [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) e o [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span><span class="sxs-lookup"><span data-stu-id="7be89-117">Import a new custom package (like step 2 from the lesson 2) and import the [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) and the [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span></span>

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. <span data-ttu-id="7be89-119">Agora, na pasta "pré-fabricados", arraste pré-fabricado "NetworkLobby" novo para a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="7be89-119">Now, in the "prefabs" folder, drag the new "NetworkLobby" prefab into the hierarchy .</span></span> 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> <span data-ttu-id="7be89-121">Observação: os dois pacotes que importamos nas etapas anteriores atualizado pré-fabricado "NetworkLobby".</span><span class="sxs-lookup"><span data-stu-id="7be89-121">note: the two packages we imported in the previous steps updated the "NetworkLobby" prefab.</span></span> <span data-ttu-id="7be89-122">Ele evita que você muita digitação!</span><span class="sxs-lookup"><span data-stu-id="7be89-122">It saves you from a lot of typing!</span></span>

5. <span data-ttu-id="7be89-123">Agora, clique na seta à esquerda de "MixedRealityPlayspace" e mover o objeto do jogo filho, "MainCamera" para baixo em pré-fabricado "SharedPlayground".</span><span class="sxs-lookup"><span data-stu-id="7be89-123">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="7be89-124">Em seguida, exclua o pré-fabricado "MixedRealityPlayspace" (para excluir, selecione pré-fabricado e toque em "excluir" em seu teclado).</span><span class="sxs-lookup"><span data-stu-id="7be89-124">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. <span data-ttu-id="7be89-126">Crie um novo objeto do jogo definido como um objeto filho ao objeto pai "SharedPlayground" (para criar um novo objeto, clique com botão direito no objeto pai e selecione "criar vazio").</span><span class="sxs-lookup"><span data-stu-id="7be89-126">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span>
7. <span data-ttu-id="7be89-127">Com o novo objeto selecionado na sua hierarquia, altere o nome do objeto para "TableAnchor" no painel Inspetor.</span><span class="sxs-lookup"><span data-stu-id="7be89-127">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="7be89-128">Além disso, clique em "adicionar o componente" e pesquise o componente "TableAnchor".</span><span class="sxs-lookup"><span data-stu-id="7be89-128">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="7be89-129">Selecioná-lo e adicioná-lo ao objeto.</span><span class="sxs-lookup"><span data-stu-id="7be89-129">Select it and add it to the object.</span></span>

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="7be89-131">Observação: definir o posicionamento para x = 1, 0,55 = y e z = 2.</span><span class="sxs-lookup"><span data-stu-id="7be89-131">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="7be89-132">Além disso, definir a rotação com y = 90.</span><span class="sxs-lookup"><span data-stu-id="7be89-132">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. <span data-ttu-id="7be89-134">Agora no painel de projeto, na pasta "pré-fabricados", arraste pré-fabricado "table" para o objeto filho de "TableAnchor" você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="7be89-134">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. <span data-ttu-id="7be89-136">Selecione "NetworkRoom", um objeto filho em "NetworkLobby" na hierarquia e clique em "Adicionar componente" no painel Inspetor e procure "PhotonView" e adicione o script para o "*NetworkRoom*" objeto.</span><span class="sxs-lookup"><span data-stu-id="7be89-136">Select "NetworkRoom," a child object under "NetworkLobby" in the hierachy, and click "add component" in the inspector panel and search for "PhotonView" and add the script to the "*NetworkRoom*" object.</span></span>

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. <span data-ttu-id="7be89-138">Por fim, no objeto "DebugWindow", altere a largura para 80 e a altura para 10.</span><span class="sxs-lookup"><span data-stu-id="7be89-138">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="7be89-140">Parabéns</span><span class="sxs-lookup"><span data-stu-id="7be89-140">Congratulations</span></span>

<span data-ttu-id="7be89-141">Quando isso for concluído, todos os usuários que unem a seu projeto do Unity podem se mover o iniciador Lunar.</span><span class="sxs-lookup"><span data-stu-id="7be89-141">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="7be89-142">Todos os movimentos são sincronizados para que cada usuário possa ver as interações uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="7be89-142">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="7be89-143">Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhado completos.</span><span class="sxs-lookup"><span data-stu-id="7be89-143">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="7be89-144">Embora todos os usuários estão conectados como parte de uma experiência de compartilhado e podem ver os movimentos relativos dos objetos, o aplicativo é ainda não é possível alinhar com precisão avatares e objetos para que os usuários locais veem uns aos outros e objetos no mesmo local físico dentro do mundo.</span><span class="sxs-lookup"><span data-stu-id="7be89-144">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="7be89-145">Para ancorar um local experiências compartilhadas, cada dispositivo requer um entendimento comum do ambiente físico.</span><span class="sxs-lookup"><span data-stu-id="7be89-145">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="7be89-146">Neste módulo, vamos fazer isso usando [âncoras espacial do Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), que será implementado na próxima lição.</span><span class="sxs-lookup"><span data-stu-id="7be89-146">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="7be89-147">Antes de prosseguir para a próxima lição, é necessário concluir o módulo de aprendizagem do ASA, que abordará Noções básicas do ASA, conta do Azure e criação de recursos e outros blocos de prédios fundamentais necessárias antes de nós pode integrar isso em nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="7be89-147">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="7be89-148">[Próxima lição: Sharing(Photon) lição 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="7be89-148">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>


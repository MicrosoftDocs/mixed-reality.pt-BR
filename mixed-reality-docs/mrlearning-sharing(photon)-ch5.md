---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327890"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="b6227-104">Âncoras espaciais do Azure e experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="b6227-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="b6227-105">Nesta lição, podemos aprenderá a integrar espacial âncoras ASA (Azure) em nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="b6227-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="b6227-106">ASA permite que vários dispositivos localizados ter um entendimento comum se o seu ambiente físico para virtual de ancoragem experiências, de modo que todos os participantes ver objetos no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="b6227-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="b6227-107">Antes de continuar com esta lição, é necessário concluir o módulo de aprendizagem do ASA, que abordará Noções básicas do ASA, conta do Azure e criação de recursos e outros blocos de prédios fundamentais que são necessários para que podemos pode integrar o ASA em nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="b6227-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="b6227-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="b6227-108">Objectives:</span></span>

- <span data-ttu-id="b6227-109">Integrar o ASA em uma experiência de compartilhado para o alinhamento de vários dispositivo</span><span class="sxs-lookup"><span data-stu-id="b6227-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="b6227-110">Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência de compartilhado local</span><span class="sxs-lookup"><span data-stu-id="b6227-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="b6227-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="b6227-111">Instructions</span></span>

1. <span data-ttu-id="b6227-112">Salve o projeto da lição anterior (CTRL + S) e nome "HLSharedProjectMainPart5.unity" para que ele seja mais fácil de encontrar quando precisar dele novamente.</span><span class="sxs-lookup"><span data-stu-id="b6227-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="b6227-113">Selecione pré-fabricado TableAnchor sob o objeto pai "MixedRealityPlayspace" e excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="b6227-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. <span data-ttu-id="b6227-115">Assim como algumas das lições anteriores, importar um novo pacote personalizado que você pode obter [aqui.](placeholderlink)</span><span class="sxs-lookup"><span data-stu-id="b6227-115">Just like some of the previous lessons, import a new custom package that you can get [here.](placeholderlink)</span></span>

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. <span data-ttu-id="b6227-117">Depois que ele é importado, pegue a âncora de tabela atualizada recentemente (a partir do pacote do unity importado na etapa anterior) da pasta "pré-fabricados" no painel de projeto e solte-o no objeto pai "MixedRealityPlayspace".</span><span class="sxs-lookup"><span data-stu-id="b6227-117">Once it's imported, grab the newly updated table anchor (from the unity package imported in the previous step) from the "prefabs" folder in the project panel and drop it into the parent object "MixedRealityPlayspace."</span></span>

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. <span data-ttu-id="b6227-119">Expanda o objeto pai "MixedRealityPlayspace" e, em seguida, o objeto "TableAnchor" e, em seguida, expanda o objeto "botões".</span><span class="sxs-lookup"><span data-stu-id="b6227-119">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. <span data-ttu-id="b6227-121">Agora, na hierarquia, selecione "ShareAzureAnchorButton" e mover sua atenção para o painel do Inspetor.</span><span class="sxs-lookup"><span data-stu-id="b6227-121">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="b6227-122">Role para baixo até o menu suspenso, mostrado na imagem abaixo e selecione "AnchorModuleScript" e clique em "ShareAnchorNetework()".</span><span class="sxs-lookup"><span data-stu-id="b6227-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. <span data-ttu-id="b6227-124">Assim como a etapa 6, selecione "GetAzureAnchorButton" e mova sua atenção para o painel do Inspetor.</span><span class="sxs-lookup"><span data-stu-id="b6227-124">Much like step 6, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="b6227-125">Role para baixo até o menu suspenso, mostrado na imagem abaixo e selecione "AnchorModuleScript" e clique em "GetSharedAnchorNetwork()".</span><span class="sxs-lookup"><span data-stu-id="b6227-125">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="b6227-126">Em seguida, salve.</span><span class="sxs-lookup"><span data-stu-id="b6227-126">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="b6227-128">Parabéns</span><span class="sxs-lookup"><span data-stu-id="b6227-128">Congratulations</span></span>

<span data-ttu-id="b6227-129">Nesta lição, você aprendeu como a integração poderosas novas espacial âncoras do Azure para alinhar os dispositivos localizados em uma experiência compartilhada!</span><span class="sxs-lookup"><span data-stu-id="b6227-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="b6227-130">Esta lição também conclui o módulo de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="b6227-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="b6227-131">Aprendemos como definir uma nova conta Photon, integrar Photon e TROCADILHO em um novo aplicativo do Unity, configurando avatares e objetos compartilhados e, finalmente, alinhando vários participantes usando o ASA.</span><span class="sxs-lookup"><span data-stu-id="b6227-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 


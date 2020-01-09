---
title: Tutoriais de funcionalidades de vários usuários-5. Integrando âncoras espaciais do Azure em uma experiência compartilhada
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 78e3e70e4dc9a32cd9871621d7fe1e07d35ff8c3
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334429"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="f4090-105">5. integrando âncoras espaciais do Azure em uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="f4090-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="f4090-106">Nesta lição, você aprenderá a integrar o ASA (âncoras espaciais) do Azure à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="f4090-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="f4090-107">O ASA permite que vários dispositivos colocalizados tenham uma referência comum se o seu ambiente físico for ancorar experiências virtuais de forma que todos os participantes vejam objetos no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="f4090-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="f4090-108">Antes de prosseguir com esta lição, você precisará concluir o módulo de aprendizagem do ASA, que abordará as noções básicas do ASA, a criação de contas e recursos do Azure, bem como outros blocos de construção fundamentais necessários antes de integrar o ASA à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="f4090-108">Before proceeding with this lesson, you'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, as well as other fundamental building blocks required before integrating ASA into our shared experience.</span></span>

## <a name="objectives"></a><span data-ttu-id="f4090-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f4090-109">Objectives</span></span>

* <span data-ttu-id="f4090-110">Integre o ASA em uma experiência compartilhada para o alinhamento de vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f4090-110">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="f4090-111">Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência compartilhada local.</span><span class="sxs-lookup"><span data-stu-id="f4090-111">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="f4090-112">Instruções</span><span class="sxs-lookup"><span data-stu-id="f4090-112">Instructions</span></span>

1. <span data-ttu-id="f4090-113">Salve o projeto da lição anterior (Control + S) e nomeie-o como "HLSharedProjectMainPart5. Unity" para que seja mais fácil localizá-lo quando você precisar dele novamente.</span><span class="sxs-lookup"><span data-stu-id="f4090-113">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="f4090-114">Selecione TableAnchor pré-fabricado abaixo do objeto pai MixedRealityPlayspace e exclua-o.</span><span class="sxs-lookup"><span data-stu-id="f4090-114">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. <span data-ttu-id="f4090-116">Na exibição de projeto, acesse ativos-> recursos-> pré-fabricados e arraste o TableAnchor pré-fabricado sobre o objeto SharedPlayground para torná-lo um filho.</span><span class="sxs-lookup"><span data-stu-id="f4090-116">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

4. <span data-ttu-id="f4090-117">Expanda o objeto pai MixedRealityPlayspace, o objeto TableAnchor e expanda o objeto Buttons também.</span><span class="sxs-lookup"><span data-stu-id="f4090-117">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

5. <span data-ttu-id="f4090-119">Agora, na hierarquia, selecione ShareAzureAnchorButton e mova sua atenção para o painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="f4090-119">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="f4090-120">Role para baixo até o menu suspenso mostrado na imagem abaixo, selecione AnchorModuleScript e clique em ShareAnchorNetwork ().</span><span class="sxs-lookup"><span data-stu-id="f4090-120">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

6. <span data-ttu-id="f4090-122">Selecione GetAzureAnchorButton (consulte a etapa 4) e mude sua atenção de volta para o painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="f4090-122">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="f4090-123">Role para baixo até o menu suspenso exibido na imagem abaixo, selecione AnchorModuleScript, clique em GetSharedAnchorNetwork () e salve.</span><span class="sxs-lookup"><span data-stu-id="f4090-123">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

7. <span data-ttu-id="f4090-125">Para testar o módulo de compartilhamento, clique no botão "iniciar sessão do ASA do Azure", que iniciará a sessão de âncoras espaciais do Azure e, em seguida, criará a âncora do Azure clicando no botão "criar âncora do Azure".</span><span class="sxs-lookup"><span data-stu-id="f4090-125">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="f4090-126">Aguarde até que a âncora do Azure seja criada.</span><span class="sxs-lookup"><span data-stu-id="f4090-126">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="f4090-127">Depois que a âncora do Azure for criada, clique no botão "compartilhar âncora do Azure" para compartilhar a âncora do Azure criada do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f4090-127">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

8. <span data-ttu-id="f4090-128">Para receber a âncora do Azure compartilhada em outro HoloLens, clique em "iniciar a sessão do ASA do Azure" para iniciar e entrar na sessão do ASA atual</span><span class="sxs-lookup"><span data-stu-id="f4090-128">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

9. <span data-ttu-id="f4090-129">Clique no botão "obter âncora do Azure" para obter a âncora do Azure compartilhada do outro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f4090-129">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

    >[!NOTE]
    ><span data-ttu-id="f4090-130">Todos os detalhes das ações correspondentes nos botões individuais serão exibidos na janela Depurar.</span><span class="sxs-lookup"><span data-stu-id="f4090-130">All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f4090-131">Parabéns</span><span class="sxs-lookup"><span data-stu-id="f4090-131">Congratulations</span></span>

<span data-ttu-id="f4090-132">Nesta lição, você aprendeu a integrar as novas âncoras espaciais do Azure para alinhar dispositivos colocalizados em uma experiência compartilhada!</span><span class="sxs-lookup"><span data-stu-id="f4090-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="f4090-133">Isso também conclui o módulo de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="f4090-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="f4090-134">Aprendemos como configurar uma nova conta do Photon, integrar Photon e trocadilho em um novo aplicativo Unity, configurar avatars e objetos compartilhados e, por fim, alinhar vários participantes usando o ASA.</span><span class="sxs-lookup"><span data-stu-id="f4090-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>

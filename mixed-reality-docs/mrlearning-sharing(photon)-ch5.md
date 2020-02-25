---
title: Tutoriais de funcionalidades de vários usuários-5. Integrando âncoras espaciais do Azure em uma experiência compartilhada
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553804"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="4a009-105">5. integrando âncoras espaciais do Azure em uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="4a009-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="4a009-106">Nesta lição, você aprenderá a integrar o ASA (âncoras espaciais) do Azure à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="4a009-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="4a009-107">O ASA permite que vários dispositivos colocalizados tenham uma referência comum se o seu ambiente físico for ancorar experiências virtuais de forma que todos os participantes vejam objetos no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="4a009-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="4a009-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4a009-108">Objectives</span></span>

* <span data-ttu-id="4a009-109">Integre o ASA em uma experiência compartilhada para o alinhamento de vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4a009-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="4a009-110">Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência compartilhada local.</span><span class="sxs-lookup"><span data-stu-id="4a009-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="4a009-111">Instructions</span><span class="sxs-lookup"><span data-stu-id="4a009-111">Instructions</span></span>

1. <span data-ttu-id="4a009-112">Selecione TableAnchor pré-fabricado abaixo do objeto pai MixedRealityPlayspace e exclua-o.</span><span class="sxs-lookup"><span data-stu-id="4a009-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="4a009-114">Na exibição de projeto, acesse ativos-> recursos-> pré-fabricados e arraste o TableAnchor pré-fabricado sobre o objeto SharedPlayground para torná-lo um filho.</span><span class="sxs-lookup"><span data-stu-id="4a009-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="4a009-115">Expanda o objeto pai MixedRealityPlayspace, o objeto TableAnchor e expanda o objeto Buttons também.</span><span class="sxs-lookup"><span data-stu-id="4a009-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="4a009-117">Agora, na hierarquia, selecione ShareAzureAnchorButton e mova sua atenção para o painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="4a009-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="4a009-118">Role para baixo até o menu suspenso mostrado na imagem abaixo, selecione AnchorModuleScript e clique em ShareAnchorNetwork ().</span><span class="sxs-lookup"><span data-stu-id="4a009-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="4a009-120">Selecione GetAzureAnchorButton (consulte a etapa 4) e mude sua atenção de volta para o painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="4a009-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="4a009-121">Role para baixo até o menu suspenso exibido na imagem abaixo, selecione AnchorModuleScript, clique em GetSharedAnchorNetwork () e salve.</span><span class="sxs-lookup"><span data-stu-id="4a009-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="4a009-123">Repita a etapa 4 para conectar a função StartAzureSession () ao StartAzureSessionButton.</span><span class="sxs-lookup"><span data-stu-id="4a009-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="4a009-124">Repita a etapa 4 para conectar a função CreateAzureAnchor () ao CreateAzureAnchorButton e verificar se o objeto TableAnchor está atribuído ao campo ' Game Object ' do parâmetro da função.</span><span class="sxs-lookup"><span data-stu-id="4a009-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="4a009-125">Siga as instruções [Connect The Scene to the Azure Resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) para adicionar suas credenciais de serviço de âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="4a009-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="4a009-126">Para testar o módulo de compartilhamento, clique no botão "iniciar sessão do ASA do Azure", que iniciará a sessão de âncoras espaciais do Azure e, em seguida, criará a âncora do Azure clicando no botão "criar âncora do Azure".</span><span class="sxs-lookup"><span data-stu-id="4a009-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="4a009-127">Aguarde até que a âncora do Azure seja criada.</span><span class="sxs-lookup"><span data-stu-id="4a009-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="4a009-128">Depois que a âncora do Azure for criada, clique no botão "compartilhar âncora do Azure" para compartilhar a âncora do Azure criada do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4a009-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="4a009-129">Para receber a âncora do Azure compartilhada em outro HoloLens, clique em "iniciar a sessão do ASA do Azure" para iniciar e entrar na sessão do ASA atual</span><span class="sxs-lookup"><span data-stu-id="4a009-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="4a009-130">Clique no botão "obter âncora do Azure" para obter a âncora do Azure compartilhada do outro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4a009-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4a009-131">Parabéns</span><span class="sxs-lookup"><span data-stu-id="4a009-131">Congratulations</span></span>

<span data-ttu-id="4a009-132">Nesta lição, você aprendeu a integrar as novas âncoras espaciais do Azure para alinhar dispositivos colocalizados em uma experiência compartilhada!</span><span class="sxs-lookup"><span data-stu-id="4a009-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="4a009-133">Isso também conclui o módulo de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="4a009-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="4a009-134">Aprendemos como configurar uma nova conta do Photon, integrar Photon e trocadilho em um novo aplicativo Unity, configurar avatars e objetos compartilhados e, por fim, alinhar vários participantes usando o ASA.</span><span class="sxs-lookup"><span data-stu-id="4a009-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>

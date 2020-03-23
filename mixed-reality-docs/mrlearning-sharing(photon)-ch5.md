---
title: Tutoriais de recursos multiusuário – 5. Integrar Âncoras Espaciais do Azure a uma experiência compartilhada
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031682"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="3d6ed-105">5. Integrar Âncoras Espaciais do Azure a uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="3d6ed-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="3d6ed-106">Nesta lição, você aprenderá a integrar ASA (Âncoras Espaciais do Azure) à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="3d6ed-107">O ASA permitirá que vários dispositivos colocalizados tenham uma referência comum se o seu ambiente físico precisar ancorar experiências virtuais de maneira que todos os participantes vejam objetos no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="3d6ed-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3d6ed-108">Objectives</span></span>

* <span data-ttu-id="3d6ed-109">Integre o ASA a uma experiência compartilhada para o alinhamento de vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="3d6ed-110">Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência compartilhada local.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="3d6ed-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="3d6ed-111">Instructions</span></span>

1. <span data-ttu-id="3d6ed-112">Selecione o pré-fabricado TableAnchor abaixo do objeto pai MixedRealityPlayspace e exclua-a.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="3d6ed-114">Na exibição de projeto, acesse Ativos->Recursos->Pré-Fabricados e arraste o pré-fabricado TableAnchor para cima do objeto SharedPlayground para torná-lo um filho.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="3d6ed-115">Expanda o objeto pai MixedRealityPlayspace, o objeto TableAnchor e expanda o objeto Botões também.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="3d6ed-117">Agora, na hierarquia, selecione ShareAzureAnchorButton e concentre-se no painel Inspetor.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="3d6ed-118">Role para baixo até o menu suspenso mostrado na imagem abaixo, selecione AnchorModuleScript e clique em ShareAnchorNetwork().</span><span class="sxs-lookup"><span data-stu-id="3d6ed-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="3d6ed-120">Selecione GetAzureAnchorButton (consulte a Etapa 4) e concentre sua atenção de volta no painel Inspetor.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="3d6ed-121">Role para baixo até o menu suspenso exibido na imagem abaixo, selecione AnchorModuleScript, clique em GetSharedAnchorNetwork() e salve.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="3d6ed-123">Repita a etapa 4 para conectar a função StartAzureSession() ao StartAzureSessionButton.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="3d6ed-124">Repita a etapa 4 para conectar a função CreateAzureAnchor () ao CreateAzureAnchorButton e verificar se o objeto TableAnchor está atribuído ao campo "Objeto do Jogo" do parâmetro da função.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="3d6ed-125">Siga as instruções em [Conectar a cena ao recurso do Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) para adicionar suas credenciais de serviço de Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="3d6ed-126">Para testar o módulo de compartilhamento, clique no botão "Iniciar Sessão do ASA do Azure", que iniciará a sessão de âncoras espaciais do Azure e, em seguida, criará a âncora do Azure clicando no botão "Criar Âncora do Azure".</span><span class="sxs-lookup"><span data-stu-id="3d6ed-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="3d6ed-127">Aguarde até a âncora do Azure ser criada.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="3d6ed-128">Depois que a âncora do Azure for criada, clique no botão "Compartilhar Âncora do Azure" para compartilhar a âncora do Azure criada do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="3d6ed-129">Para receber a Âncora do Azure compartilhada em outro HoloLens, clique em "Iniciar a Sessão do ASA do Azure" para iniciar e entrar na sessão do ASA atual</span><span class="sxs-lookup"><span data-stu-id="3d6ed-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="3d6ed-130">Clique no botão "Obter Âncora do Azure" para obter a âncora do Azure compartilhada do outro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3d6ed-131">Parabéns</span><span class="sxs-lookup"><span data-stu-id="3d6ed-131">Congratulations</span></span>

<span data-ttu-id="3d6ed-132">Nesta lição, você aprendeu a integrar as novas Âncoras Espaciais do Azure eficientes para alinhar dispositivos colocalizados em uma experiência compartilhada!</span><span class="sxs-lookup"><span data-stu-id="3d6ed-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="3d6ed-133">Isso também conclui o módulo de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="3d6ed-134">Aprendemos a configurar uma nova conta do Photon, integrar o Photon e o PUN a um novo aplicativo Unity, configurar avatars e objetos compartilhados e, por fim, alinhar vários participantes usando o ASA.</span><span class="sxs-lookup"><span data-stu-id="3d6ed-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>

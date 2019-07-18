---
title: Módulo de compartilhamento de aprendizagem do MR para o HoloLens 2
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293623"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="f335b-104">Âncoras espaciais e experiências compartilhadas do Azure</span><span class="sxs-lookup"><span data-stu-id="f335b-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="f335b-105">Nesta lição, aprenderemos a integrar o ASA (âncoras espaciais) do Azure em nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="f335b-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="f335b-106">O ASA permite que vários dispositivos colocalizados tenham uma referência comum se o seu ambiente físico for ancorar experiências virtuais de forma que todos os participantes vejam objetos no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="f335b-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="f335b-107">Antes de prosseguir com esta lição, precisaremos concluir o módulo de aprendizagem do ASA, que abordará as noções básicas do ASA, a criação de contas e recursos do Azure e outros blocos de edifícios fundamentais que são necessários antes que possamos integrar o ASA à nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="f335b-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="f335b-108">Seus</span><span class="sxs-lookup"><span data-stu-id="f335b-108">Objectives:</span></span>

- <span data-ttu-id="f335b-109">Integre o ASA em uma experiência compartilhada para o alinhamento de vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f335b-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="f335b-110">Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência compartilhada local.</span><span class="sxs-lookup"><span data-stu-id="f335b-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="f335b-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="f335b-111">Instructions</span></span>

1. <span data-ttu-id="f335b-112">Salve o projeto da lição anterior (Control + S) e nomeie-o como "HLSharedProjectMainPart5. Unity" para que seja mais fácil localizá-lo quando você precisar dele novamente.</span><span class="sxs-lookup"><span data-stu-id="f335b-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="f335b-113">Selecione TableAnchor pré-fabricado abaixo do objeto pai MixedRealityPlayspace e exclua-o.</span><span class="sxs-lookup"><span data-stu-id="f335b-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="f335b-115">Na exibição de projeto, acesse ativos-> recursos-> pré-fabricados e arraste o TableAnchor pré-fabricado sobre o objeto SharedPlayground para torná-lo um filho.</span><span class="sxs-lookup"><span data-stu-id="f335b-115">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="f335b-116">Expanda o objeto pai MixedRealityPlayspace, o objeto TableAnchor e expanda o objeto Buttons também.</span><span class="sxs-lookup"><span data-stu-id="f335b-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="f335b-118">Agora, na hierarquia, selecione ShareAzureAnchorButton e mova sua atenção para o painel do inaspectr.</span><span class="sxs-lookup"><span data-stu-id="f335b-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="f335b-119">Role para baixo até o menu suspenso mostrado na imagem abaixo e selecione AnchorModuleScript e clique em ShareAnchorNetework ().</span><span class="sxs-lookup"><span data-stu-id="f335b-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="f335b-121">Selecione GetAzureAnchorButton (consulte a etapa 4) e mude sua atenção de volta para o painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="f335b-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="f335b-122">Role para baixo até o menu suspenso mostrado na imagem abaixo e selecione AnchorModuleScript e clique em GetSharedAnchorNetwork () e em salvar.</span><span class="sxs-lookup"><span data-stu-id="f335b-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="f335b-124">Para testar o módulo de compartilhamento, clique no botão "iniciar sessão do ASA do Azure", que iniciará a sessão de âncoras espaciais do Azure e, em seguida, criará a âncora do Azure clicando no botão "criar âncora do Azure" e aguarde um momento até que a âncora do Azure seja criada.</span><span class="sxs-lookup"><span data-stu-id="f335b-124">To test the sharing module, click on the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button and wait for sometime for the azure anchor to get created.</span></span> <span data-ttu-id="f335b-125">Depois que a âncora do Azure for criada, clique no botão "compartilhar âncora do Azure" para compartilhar a âncora do Azure criada do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f335b-125">Once the azure anchor is created then click on the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="f335b-126">Para receber a âncora do Azure compartilhada em outro HoloLens, clique em "iniciar a sessão do ASA do Azure" para iniciar e entrar na sessão atual do ASA e clique no botão "obter âncora do Azure" para obter a âncora do Azure compartilhada do outro HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f335b-126">To recieve the shared azure anchor in another HoloLens, click on the "Start Azure ASA Session" to start and get in to the current ASA session and click on "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="f335b-127">Observação: Todos os detalhes das ações correspondentes nos botões individuais serão exibidos na janela Depurar.</span><span class="sxs-lookup"><span data-stu-id="f335b-127">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f335b-128">Parabéns</span><span class="sxs-lookup"><span data-stu-id="f335b-128">Congratulations</span></span>

<span data-ttu-id="f335b-129">Nesta lição, você aprendeu a integrar as novas âncoras espaciais do Azure para alinhar dispositivos colocalizados em uma experiência compartilhada!</span><span class="sxs-lookup"><span data-stu-id="f335b-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="f335b-130">Esta lição também conclui o módulo de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="f335b-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="f335b-131">Aprendemos como configurar uma nova conta do Photon, integrar o Photon e o trocadilho em um novo aplicativo Unity, configurar avatars e objetos compartilhados e, finalmente, alinhar vários participantes usando o ASA.</span><span class="sxs-lookup"><span data-stu-id="f335b-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 


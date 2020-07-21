---
title: Tutoriais de recursos multiusuário – 4. Compartilhar movimentações de objeto com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cd8f0cb8888e7225566acc8c4b26aced3e4d977e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304008"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="3172b-105">4. Compartilhar movimentações de objeto com vários usuários</span><span class="sxs-lookup"><span data-stu-id="3172b-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="3172b-106">Neste tutorial, você aprenderá a compartilhar os movimentos de objetos, de modo que todos os participantes de uma experiência compartilhada possam colaborar e exibir as interações uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="3172b-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="3172b-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3172b-107">Objectives</span></span>

* <span data-ttu-id="3172b-108">Configurar o projeto para compartilhar os movimentos de objetos</span><span class="sxs-lookup"><span data-stu-id="3172b-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="3172b-109">Saber como criar um aplicativo básico de colaboração de vários usuários</span><span class="sxs-lookup"><span data-stu-id="3172b-109">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="3172b-110">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="3172b-110">Preparing the scene</span></span>

<span data-ttu-id="3172b-111">Nesta seção, você vai preparar a cena adicionando o pré-fabricado do tutorial.</span><span class="sxs-lookup"><span data-stu-id="3172b-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="3172b-112">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e arraste o pré-fabricado **TableAnchor** sobre o objeto **SharedPlayground** na janela Hierarquia para adicioná-lo à cena como um filho do objeto SharedPlayground:</span><span class="sxs-lookup"><span data-stu-id="3172b-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="3172b-114">Como configurar o PUN para criar uma instância dos objetos</span><span class="sxs-lookup"><span data-stu-id="3172b-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="3172b-115">Nesta seção, você vai configurar o projeto para usar a experiência do Explorador do Rover criada durante os [Tutoriais de introdução](mr-learning-base-01.md) e definir onde ele será instanciado.</span><span class="sxs-lookup"><span data-stu-id="3172b-115">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="3172b-116">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="3172b-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="3172b-117">Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3172b-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="3172b-118">Para o campo **Pré-fabricado do Rover Explorer**, atribua o pré-fabricado **RoverExplorer_Complete_Variant** da pasta Recursos</span><span class="sxs-lookup"><span data-stu-id="3172b-118">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="3172b-120">Com o objeto filho **NetworkRoom** ainda selecionado, na janela Hierarquia, expanda o objeto **TableAnchor** e, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3172b-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="3172b-121">No campo **Localização do Explorador do Rover**, atribua o objeto filho TableAnchor > **Table** por meio da janela Hierarquia</span><span class="sxs-lookup"><span data-stu-id="3172b-121">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="3172b-123">Como testar a experiência com a movimentação de objetos compartilhados</span><span class="sxs-lookup"><span data-stu-id="3172b-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="3172b-124">Se você criar e implantar agora o projeto do Unity no HoloLens e, no Unity, selecionar o botão Reproduzir para entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá o objeto se mover no Unity ao mover o objeto no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="3172b-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="3172b-126">Parabéns</span><span class="sxs-lookup"><span data-stu-id="3172b-126">Congratulations</span></span>

<span data-ttu-id="3172b-127">Você configurou com êxito o projeto para sincronizar os movimentos do objeto para que os usuários possam ver os objetos se moverem quando os outros usuários os moverem.</span><span class="sxs-lookup"><span data-stu-id="3172b-127">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="3172b-128">No próximo tutorial, você implementará a funcionalidade para alinhar a experiência no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="3172b-128">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="3172b-129">Isso garantirá que os usuários vejam uns aos outros na sua localização física real e, portanto, os objetos aparecerão na mesma posição física e rotação para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="3172b-129">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

[<span data-ttu-id="3172b-130">Próximo tutorial: 5. Integrar âncoras espaciais do Azure a uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="3172b-130">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

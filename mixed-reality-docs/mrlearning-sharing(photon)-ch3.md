---
title: Tutoriais de recursos multiusuário – 4. Compartilhar movimentações de objeto com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610658"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="93363-105">3. Compartilhar movimentações de objeto com vários usuários</span><span class="sxs-lookup"><span data-stu-id="93363-105">3. Sharing object movements with multiple users</span></span>

<span data-ttu-id="93363-106">Neste tutorial, você aprenderá a compartilhar os movimentos de objetos, de modo que todos os participantes de uma experiência compartilhada possam colaborar e ver as interações uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="93363-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each others' interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="93363-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="93363-107">Objectives</span></span>

* <span data-ttu-id="93363-108">Configurar o projeto para compartilhar os movimentos de objetos</span><span class="sxs-lookup"><span data-stu-id="93363-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="93363-109">Saiba como criar um aplicativo básico de colaboração de vários usuários</span><span class="sxs-lookup"><span data-stu-id="93363-109">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="93363-110">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="93363-110">Preparing the scene</span></span>

<span data-ttu-id="93363-111">Nesta seção, você vai preparar a cena adicionando o pré-fabricado do tutorial.</span><span class="sxs-lookup"><span data-stu-id="93363-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="93363-112">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e arraste o pré-fabricado **TableAnchor** sobre o objeto **SharedPlayground** na janela Hierarquia para adicioná-lo à cena como um filho do objeto SharedPlayground:</span><span class="sxs-lookup"><span data-stu-id="93363-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab on top of the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="93363-114">Como configurar o PUN para criar uma instância dos objetos</span><span class="sxs-lookup"><span data-stu-id="93363-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="93363-115">Nesta seção, você vai configurar o projeto para usar o pré-fabricado RocketLauncher_Complete_Variant criado na seção anterior e definir em que local a instância dele será criada.</span><span class="sxs-lookup"><span data-stu-id="93363-115">In this section, you will configure the project to use the RocketLauncher_Complete_Variant prefab you created in the previous section and define where it will be instantiated.</span></span>

<span data-ttu-id="93363-116">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="93363-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="93363-117">Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="93363-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="93363-118">Ao campo **Pré-fabricado do Usuário do Photon**, atribua o pré-fabricado **PhotonUser** da pasta Recursos</span><span class="sxs-lookup"><span data-stu-id="93363-118">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

<span data-ttu-id="93363-120">Com o objeto filho **NetworkRoom** ainda selecionado, na janela Hierarquia, expanda o objeto **TableAnchor** e, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="93363-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="93363-121">Ao campo **Localização do Rocket Launcher**, atribua o objeto filho **Table** por meio da janela Hierarquia</span><span class="sxs-lookup"><span data-stu-id="93363-121">To the **Rocket Launcher Location** field, assign the **Table** child object from the Hierarchy window</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="93363-123">Como testar a experiência com a movimentação de objetos compartilhados</span><span class="sxs-lookup"><span data-stu-id="93363-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="93363-124">Se você criar e implantar agora o projeto do Unity no HoloLens e, no Unity, selecionar o botão Reproduzir para entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá o objeto se mover no Unity ao mover o objeto no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="93363-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="93363-126">Parabéns</span><span class="sxs-lookup"><span data-stu-id="93363-126">Congratulations</span></span>

<span data-ttu-id="93363-127">Você configurou com êxito o projeto, para que os movimentos de objeto sejam sincronizados e os usuários possam ver os objetos se moverem quando os outros usuários moverem os objetos.</span><span class="sxs-lookup"><span data-stu-id="93363-127">You have successfully configured your project so object movements are synchronized and users can see the objects move when other users move the objects.</span></span> <span data-ttu-id="93363-128">No próximo tutorial, você implementará uma funcionalidade para que a experiência compartilhada seja alinhada no mundo físico e os usuários vejam uns aos outros na respectiva localização física real e para que os objetos apareçam na mesma posição física e rotação para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="93363-128">In the next tutorial, you will implement functionality so the shared experience is aligned in the physical world and the users see each other in their actual physical location and so the objects appear in the same physical position and rotation for all users.</span></span>

<span data-ttu-id="93363-129">[Próximo tutorial: 4. Integrar âncoras espaciais do Azure a uma experiência compartilhada](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="93363-129">[Next tutorial: 4. Integrating Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch4.md)</span></span>

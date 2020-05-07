---
title: Tutoriais de recursos multiusuário – 3. Como conectar vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610972"
---
# <a name="2-connecting-multiple-users"></a><span data-ttu-id="ac834-105">2. Como conectar vários usuários</span><span class="sxs-lookup"><span data-stu-id="ac834-105">2. Connecting multiple users</span></span>

<span data-ttu-id="ac834-106">Neste tutorial, você aprenderá a conectar vários usuários como parte de uma experiência compartilhada ao vivo.</span><span class="sxs-lookup"><span data-stu-id="ac834-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="ac834-107">Ao final do tutorial, você estará apto a executar o aplicativo em vários dispositivos e fazer com que cada usuário veja o avatar dos outros usuários se mover em tempo real.</span><span class="sxs-lookup"><span data-stu-id="ac834-107">By the end of the tutorial you will be able to run the application on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="ac834-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ac834-108">Objectives</span></span>

* <span data-ttu-id="ac834-109">Saiba como conectar vários usuários em uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="ac834-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ac834-110">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="ac834-110">Preparing the scene</span></span>

<span data-ttu-id="ac834-111">Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.</span><span class="sxs-lookup"><span data-stu-id="ac834-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="ac834-112">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados**.</span><span class="sxs-lookup"><span data-stu-id="ac834-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder.</span></span> <span data-ttu-id="ac834-113">Enquanto segura o botão CTRL, clique em **DebugWindow**, **NetworkLobby** e **SharedPlayground** para selecionar os três pré-fabricados:</span><span class="sxs-lookup"><span data-stu-id="ac834-113">While holding down the CTRL button, click on **DebugWindow**, **NetworkLobby**, and **SharedPlayground** to select the three prefabs:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

<span data-ttu-id="ac834-115">Com os três pré-fabricados ainda selecionados, arraste-os para a janela Hierarquia para adicioná-los à cena:</span><span class="sxs-lookup"><span data-stu-id="ac834-115">With the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="ac834-117">Como criar o pré-fabricado do usuário</span><span class="sxs-lookup"><span data-stu-id="ac834-117">Creating the user prefab</span></span>

<span data-ttu-id="ac834-118">Nesta seção, você criará um pré-fabricado que será usado para representar os usuários na experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="ac834-118">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="ac834-119">1. Criar e configurar o usuário</span><span class="sxs-lookup"><span data-stu-id="ac834-119">1. Create and configure the user</span></span>

<span data-ttu-id="ac834-120">Na janela Hierarquia, clique com o botão direito do mouse em uma área vazia e selecione **Criar Vazio** para adicionar um objeto vazio à cena, nomeie o objeto **PhotonUser** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ac834-120">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="ac834-121">Verifique se a **Posição** da transformação está definida como X = 0, Y = 0 e Z = 0:</span><span class="sxs-lookup"><span data-stu-id="ac834-121">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

<span data-ttu-id="ac834-123">Com o objeto **PhotonUser** ainda selecionado, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Usuário do Photon (Script)** ao objeto PhotonUser:</span><span class="sxs-lookup"><span data-stu-id="ac834-123">With the **PhotonUser** object still selected, in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

<span data-ttu-id="ac834-125">Na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Sincronização de Rede Genérica (Script)** ao objeto PhotonUser e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ac834-125">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ac834-126">Marque a caixa de seleção **É um Usuário**</span><span class="sxs-lookup"><span data-stu-id="ac834-126">Check the **Is User** checkbox</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

<span data-ttu-id="ac834-128">Na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Exibição do Photon (Script)** ao objeto PhotonUser e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ac834-128">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ac834-129">Ao campo **Componentes Observados**, atribua o componente Sincronização de Rede Genérica (Script)</span><span class="sxs-lookup"><span data-stu-id="ac834-129">To the **Observed Components** field, assign the Generic Net Sync (Script) component</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="ac834-131">2. Criar o avatar</span><span class="sxs-lookup"><span data-stu-id="ac834-131">2. Create the avatar</span></span>

<span data-ttu-id="ac834-132">Na janela Hierarquia, clique com o botão direito do mouse no objeto **PhotonUser** e selecione **Objeto 3D** > **Esfera** para criar um objeto de esfera como um filho do objeto PhotonUser e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ac834-132">In the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ac834-133">Verifique se a **Posição** da transformação está definida como X = 0, Y = 0 e Z = 0</span><span class="sxs-lookup"><span data-stu-id="ac834-133">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="ac834-134">Altere a **Escala** da transformação para um tamanho adequado, por exemplo, X = 0,15, Y = 0,15 e Z = 0,15</span><span class="sxs-lookup"><span data-stu-id="ac834-134">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="ac834-136">3. Criar o pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="ac834-136">3. Create the prefab</span></span>

<span data-ttu-id="ac834-137">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**:</span><span class="sxs-lookup"><span data-stu-id="ac834-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

<span data-ttu-id="ac834-139">Com a pasta Recursos ainda selecionada, **clique e arraste** o objeto **PhotonUser** da janela Hierarquia para a pasta **Recursos** a fim de tornar o objeto PhotonUser um pré-fabricado:</span><span class="sxs-lookup"><span data-stu-id="ac834-139">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

<span data-ttu-id="ac834-141">Na janela Hierarquia, clique com o botão direito do mouse no objeto **PhotonUser** e selecione **Excluir** para removê-lo da cena:</span><span class="sxs-lookup"><span data-stu-id="ac834-141">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="ac834-143">Como configurar o PUN para criar uma instância do pré-fabricado do usuário</span><span class="sxs-lookup"><span data-stu-id="ac834-143">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="ac834-144">Nesta seção, você vai configurar o projeto para usar o pré-fabricado do PhotonUser criado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="ac834-144">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="ac834-145">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="ac834-145">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="ac834-146">Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ac834-146">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="ac834-147">Ao campo **Pré-fabricado do Usuário do Photon**, atribua o pré-fabricado **PhotonUser** da pasta Recursos</span><span class="sxs-lookup"><span data-stu-id="ac834-147">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="ac834-149">Como testar a experiência com vários usuários</span><span class="sxs-lookup"><span data-stu-id="ac834-149">Trying the experience with multiple users</span></span>

<span data-ttu-id="ac834-150">Se você criar e implantar agora o projeto do Unity no HoloLens e, no Unity, selecionar o botão Reproduzir para entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá a movimentação do avatar do usuário do HoloLens quando mover a cabeça (HoloLens):</span><span class="sxs-lookup"><span data-stu-id="ac834-150">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="ac834-152">Para obter um lembrete sobre como criar e implantar seu projeto do Unity no HoloLens 2, confira as instruções para [Criar o aplicativo para seu dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="ac834-152">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="ac834-153">O aplicativo precisa se conectar ao Photon; portanto, verifique se o computador/o dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="ac834-153">The application needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ac834-154">Parabéns</span><span class="sxs-lookup"><span data-stu-id="ac834-154">Congratulations</span></span>

<span data-ttu-id="ac834-155">Você configurou com êxito seu projeto para permitir que vários usuários se conectem à mesma experiência e vejam os movimentos uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="ac834-155">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="ac834-156">No próximo tutorial, você implementará uma funcionalidade para que os movimentos dos objetos também sejam compartilhados entre vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ac834-156">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

<span data-ttu-id="ac834-157">[Próximo tutorial: 2. Compartilhar movimentações de objeto com vários usuários](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="ac834-157">[Next tutorial: 2. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

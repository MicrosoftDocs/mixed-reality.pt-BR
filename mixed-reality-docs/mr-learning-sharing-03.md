---
title: Tutoriais de recursos multiusuário – 3. Como conectar vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376388"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="deb84-105">3. Como conectar vários usuários</span><span class="sxs-lookup"><span data-stu-id="deb84-105">3. Connecting multiple users</span></span>

<span data-ttu-id="deb84-106">Neste tutorial, você aprenderá a conectar vários usuários como parte de uma experiência compartilhada ao vivo.</span><span class="sxs-lookup"><span data-stu-id="deb84-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="deb84-107">Ao final do tutorial, você estará apto a executar o aplicativo em vários dispositivos e fazer com que cada usuário veja o avatar dos outros usuários se mover em tempo real.</span><span class="sxs-lookup"><span data-stu-id="deb84-107">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="deb84-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="deb84-108">Objectives</span></span>

* <span data-ttu-id="deb84-109">Saiba como conectar vários usuários em uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="deb84-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="deb84-110">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="deb84-110">Preparing the scene</span></span>

<span data-ttu-id="deb84-111">Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.</span><span class="sxs-lookup"><span data-stu-id="deb84-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="deb84-112">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:</span><span class="sxs-lookup"><span data-stu-id="deb84-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="deb84-113">Pré-fabricado **NetworkLobby**</span><span class="sxs-lookup"><span data-stu-id="deb84-113">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="deb84-114">Pré-fabricado **SharedPlayground**</span><span class="sxs-lookup"><span data-stu-id="deb84-114">**SharedPlayground** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="deb84-116">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureSpatialAnchors** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:</span><span class="sxs-lookup"><span data-stu-id="deb84-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="deb84-117">**DebugWindow** pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="deb84-117">**DebugWindow** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="deb84-119">Como criar o pré-fabricado do usuário</span><span class="sxs-lookup"><span data-stu-id="deb84-119">Creating the user prefab</span></span>

<span data-ttu-id="deb84-120">Nesta seção, você criará um pré-fabricado que será usado para representar os usuários na experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="deb84-120">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="deb84-121">1. Criar e configurar o usuário</span><span class="sxs-lookup"><span data-stu-id="deb84-121">1. Create and configure the user</span></span>

<span data-ttu-id="deb84-122">Na janela Hierarquia, clique com o botão direito do mouse em uma área vazia e selecione **Criar Vazio** para adicionar um objeto vazio à cena, nomeie o objeto **PhotonUser** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="deb84-122">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="deb84-123">Verifique se a **Posição** da transformação está definida como X = 0, Y = 0 e Z = 0:</span><span class="sxs-lookup"><span data-stu-id="deb84-123">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="deb84-125">Na janela Hierarquia, selecione o objeto **PhotonUser**, então, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Usuário do Photon (Script)** ao objeto PhotonUser:</span><span class="sxs-lookup"><span data-stu-id="deb84-125">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="deb84-127">Na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Sincronização de Rede Genérica (Script)** ao objeto PhotonUser e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="deb84-127">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="deb84-128">Marque a caixa de seleção **É um Usuário**</span><span class="sxs-lookup"><span data-stu-id="deb84-128">Check the **Is User** checkbox</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="deb84-130">Na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Exibição do Photon (Script)** ao objeto PhotonUser e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="deb84-130">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="deb84-131">Ao campo **Componentes Observados**, atribua o componente **Sincronização de Rede Genérica (Script)**</span><span class="sxs-lookup"><span data-stu-id="deb84-131">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="deb84-133">2. Criar o avatar</span><span class="sxs-lookup"><span data-stu-id="deb84-133">2. Create the avatar</span></span>

<span data-ttu-id="deb84-134">Na janela do projeto, navegue até a pasta **Ativos** > **MRTK** > **SDK** > **StandardAssets** > **Materiais** para localizar os materiais do MRTK.</span><span class="sxs-lookup"><span data-stu-id="deb84-134">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="deb84-135">Em seguida, na janela Hierarquia, clique com o botão direito do mouse no objeto **PhotonUser** e selecione **Objeto 3D** > **Esfera** para criar um objeto de esfera como um filho do objeto PhotonUser e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="deb84-135">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="deb84-136">Verifique se a **Posição** da transformação está definida como X = 0, Y = 0 e Z = 0</span><span class="sxs-lookup"><span data-stu-id="deb84-136">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="deb84-137">Altere a **Escala** da transformação para um tamanho adequado, por exemplo, X = 0,15, Y = 0,15 e Z = 0,15</span><span class="sxs-lookup"><span data-stu-id="deb84-137">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="deb84-138">Para o campo MeshRenderer > Materiais > **Elemento 0**, atribua o material **MRTK_Standard_White**</span><span class="sxs-lookup"><span data-stu-id="deb84-138">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="deb84-140">3. Criar o pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="deb84-140">3. Create the prefab</span></span>

<span data-ttu-id="deb84-141">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**:</span><span class="sxs-lookup"><span data-stu-id="deb84-141">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="deb84-143">Com a pasta Recursos ainda selecionada, **clique e arraste** o objeto **PhotonUser** da janela Hierarquia para a pasta **Recursos** a fim de tornar o objeto PhotonUser um pré-fabricado:</span><span class="sxs-lookup"><span data-stu-id="deb84-143">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="deb84-145">Na janela Hierarquia, clique com o botão direito do mouse no objeto **PhotonUser** e selecione **Excluir** para removê-lo da cena:</span><span class="sxs-lookup"><span data-stu-id="deb84-145">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="deb84-147">Como configurar o PUN para criar uma instância do pré-fabricado do usuário</span><span class="sxs-lookup"><span data-stu-id="deb84-147">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="deb84-148">Nesta seção, você vai configurar o projeto para usar o pré-fabricado do PhotonUser criado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="deb84-148">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="deb84-149">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="deb84-149">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="deb84-150">Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="deb84-150">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="deb84-151">Ao campo **Pré-fabricado do Usuário do Photon**, atribua o pré-fabricado **PhotonUser** da pasta Recursos</span><span class="sxs-lookup"><span data-stu-id="deb84-151">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="deb84-153">Como testar a experiência com vários usuários</span><span class="sxs-lookup"><span data-stu-id="deb84-153">Trying the experience with multiple users</span></span>

<span data-ttu-id="deb84-154">Se você criar e implantar agora o projeto do Unity no HoloLens, então, no Unity, entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá a movimentação do avatar do usuário do HoloLens quando mover a cabeça (HoloLens):</span><span class="sxs-lookup"><span data-stu-id="deb84-154">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="deb84-156">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="deb84-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="deb84-157">O aplicativo precisa se conectar ao Photon; portanto, verifique se o computador/o dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="deb84-157">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="deb84-158">Parabéns</span><span class="sxs-lookup"><span data-stu-id="deb84-158">Congratulations</span></span>

<span data-ttu-id="deb84-159">Você configurou com êxito seu projeto para permitir que vários usuários se conectem à mesma experiência e vejam os movimentos uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="deb84-159">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="deb84-160">No próximo tutorial, você implementará uma funcionalidade para que os movimentos dos objetos também sejam compartilhados entre vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="deb84-160">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

[<span data-ttu-id="deb84-161">Próximo tutorial: 4. Compartilhar movimentações de objeto com vários usuários</span><span class="sxs-lookup"><span data-stu-id="deb84-161">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)

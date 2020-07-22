---
title: Tutoriais de recursos multiusuário – 5. Integrar Âncoras Espaciais do Azure a uma experiência compartilhada
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 79be23c9371bf90d03df0070b74f6cff3f0afafa
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304108"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="e435a-105">5. Integrar Âncoras Espaciais do Azure a uma experiência compartilhada</span><span class="sxs-lookup"><span data-stu-id="e435a-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="e435a-106">Neste tutorial, você aprenderá a integrar a ASA (Âncoras Espaciais do Azure) à experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="e435a-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="e435a-107">A ASA permite que vários dispositivos tenham uma referência comum ao mundo físico, de modo que os usuários vejam uns aos outros na respectiva localização física real e vejam a experiência compartilhada no mesmo lugar.</span><span class="sxs-lookup"><span data-stu-id="e435a-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="e435a-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e435a-108">Objectives</span></span>

* <span data-ttu-id="e435a-109">Integrar a ASA a uma experiência compartilhada para o alinhamento de vários dispositivos</span><span class="sxs-lookup"><span data-stu-id="e435a-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="e435a-110">Conhecer os conceitos básicos de como a ASA funciona no contexto de uma experiência compartilhada local</span><span class="sxs-lookup"><span data-stu-id="e435a-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="e435a-111">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="e435a-111">Preparing the scene</span></span>

<span data-ttu-id="e435a-112">Na janela Hierarquia, expanda o objeto **SharedPlayground** e expanda o objeto **TableAnchor** para expor os objetos filho:</span><span class="sxs-lookup"><span data-stu-id="e435a-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="e435a-114">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e arraste o pré-fabricado **Buttons** sobre o objeto filho **TableAnchor** para adicioná-lo à cena como um filho do objeto TableAnchor:</span><span class="sxs-lookup"><span data-stu-id="e435a-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="e435a-116">Como configurar os botões para operar a cena</span><span class="sxs-lookup"><span data-stu-id="e435a-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="e435a-117">Nesta seção, você vai configurar uma série de eventos de botão que demonstram os conceitos básicos de como as Âncoras Espaciais do Azure podem ser usadas para obter o alinhamento espacial em uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="e435a-117">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="e435a-118">Na janela Hierarquia, expanda o objeto **Button** e selecione o primeiro objeto de botão filho chamado **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="e435a-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="e435a-120">Na janela Inspetor, localize o componente **Interativo (Script)** e configure o evento **OnClick ()** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e435a-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e435a-121">Ao campo **Nenhum (Objeto)** , atribua o objeto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="e435a-121">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="e435a-122">No menu suspenso **Nenhuma Função**, selecione a função **AnchorModuleScript** > **StartAzureSession ()**</span><span class="sxs-lookup"><span data-stu-id="e435a-122">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="e435a-124">Na janela Hierarquia, selecione o segundo objeto de botão filho chamado **CreateAzureAnchor**. Em seguida, na janela Inspetor, localize o componente **Interativo (Script)** e configure o evento **OnClick ()** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e435a-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e435a-125">Ao campo **Nenhum (Objeto)** , atribua o objeto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="e435a-125">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="e435a-126">No menu suspenso **Nenhuma Função**, selecione a função **AnchorModuleScript** > **CreateAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="e435a-126">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="e435a-127">Ao novo campo **Nenhum (Objeto de Jogo)** exibido, atribua o objeto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="e435a-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="e435a-129">Na janela Hierarquia, selecione o terceiro objeto de botão filho chamado **ShareAzureAnchor**. Em seguida, na janela Inspetor, localize o componente **Interativo (Script)** e configure o evento **OnClick ()** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e435a-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e435a-130">Ao campo **Nenhum (Objeto)** , atribua o objeto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="e435a-130">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="e435a-131">No menu suspenso **Nenhuma Função**, selecione a função **SharingModuleScript** > **ShareAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="e435a-131">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="e435a-133">Na janela Hierarquia, selecione o quarto objeto de botão filho chamado **GetAzureAnchor**. Em seguida, na janela Inspetor, localize o componente **Interativo (Script)** e configure o evento **OnClick ()** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e435a-133">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="e435a-134">Ao campo **Nenhum (Objeto)** , atribua o objeto **TableAnchor**</span><span class="sxs-lookup"><span data-stu-id="e435a-134">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="e435a-135">No menu suspenso **Nenhuma Função**, selecione a função **SharingModuleScript** > **GetAzureAnchor ()**</span><span class="sxs-lookup"><span data-stu-id="e435a-135">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="e435a-137">Como conectar a cena ao recurso do Azure</span><span class="sxs-lookup"><span data-stu-id="e435a-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="e435a-138">Na janela Hierarquia, expanda o objeto **SharedPlayground** e selecione o objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="e435a-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="e435a-139">Na janela Inspetor, localize o componente **Gerenciador de Âncora Espacial (Script)** e configure a seção **Credenciais** com as credenciais da conta das Âncoras Espaciais do Azure criada como parte dos [Pré-requisitos](mr-learning-sharing-01.md#prerequisites) desta série de tutoriais:</span><span class="sxs-lookup"><span data-stu-id="e435a-139">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="e435a-140">No campo **ID da Conta das Âncoras Espaciais**, cole a **ID da Conta** da sua conta das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="e435a-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="e435a-141">No campo **Chave de Conta das Âncoras Espaciais**, cole a **Chave de Acesso** primária ou secundária da sua conta das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="e435a-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="e435a-143">Em vez de definir a ID da Conta de Âncoras Espaciais e a chave na cena, você pode defini-la para todo o seu projeto, isso poderá ser vantajoso se você tiver várias cenas usando o ASA.</span><span class="sxs-lookup"><span data-stu-id="e435a-143">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="e435a-144">Para fazer isso, na janela do projeto, navegue até o ativo em Ativos > AzureSpatialAnchors.SDK > Recursos > **SpatialAnchorConfig** e defina os valores na janela Inspetor.</span><span class="sxs-lookup"><span data-stu-id="e435a-144">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="e435a-145">Na janela Hierarquia, selecione o objeto **TableAnchor** e, em seguida, na janela Inspetor, localize o componente **Módulo de Âncora (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e435a-145">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="e435a-146">No campo **PIN de Compartilhamento Público**, altere alguns dígitos para que o PIN se torne exclusivo ao seu projeto</span><span class="sxs-lookup"><span data-stu-id="e435a-146">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="e435a-148">Com o objeto **TableAnchor** ainda selecionado, na janela Inspetor, verifique se todos os componentes de script estão **habilitados**:</span><span class="sxs-lookup"><span data-stu-id="e435a-148">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled**:</span></span>

* <span data-ttu-id="e435a-149">Marque a caixa de seleção ao lado dos componentes **Gerenciador de Âncora Espacial (Script)** para habilitá-los</span><span class="sxs-lookup"><span data-stu-id="e435a-149">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="e435a-150">Marque a caixa de seleção ao lado dos componentes **Script do Módulo de Âncora (Script)** para habilitá-los</span><span class="sxs-lookup"><span data-stu-id="e435a-150">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="e435a-151">Marque a caixa de seleção ao lado dos componentes **Script do Módulo de Compartilhamento (Script)** para habilitá-los</span><span class="sxs-lookup"><span data-stu-id="e435a-151">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="e435a-153">Como testar a experiência com o alinhamento espacial</span><span class="sxs-lookup"><span data-stu-id="e435a-153">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="e435a-154">As Âncoras Espaciais do Azure não podem ser executadas no Unity.</span><span class="sxs-lookup"><span data-stu-id="e435a-154">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="e435a-155">Consequentemente, para testar a funcionalidade das Âncoras Espaciais do Azure, você precisará implantar o projeto em um mínimo de dois dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e435a-155">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="e435a-156">Se você criar e implantar agora o projeto do Unity em dois dispositivos, poderá obter o alinhamento espacial entre os dispositivos compartilhando a ID da Âncora do Azure.</span><span class="sxs-lookup"><span data-stu-id="e435a-156">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="e435a-157">Para testá-lo, você pode seguir estas etapas:</span><span class="sxs-lookup"><span data-stu-id="e435a-157">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="e435a-158">No dispositivo 1: **Iniciar o aplicativo** (o Gerenciador de Rover é instanciado e colocado na tabela)</span><span class="sxs-lookup"><span data-stu-id="e435a-158">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="e435a-159">No dispositivo 2: **Inicie o aplicativo** (os dois usuários veem a mesa com o Rover Explorer, mas ela não aparece no mesmo lugar, e os avatars do usuário não aparecem no local em que os usuários estão)</span><span class="sxs-lookup"><span data-stu-id="e435a-159">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="e435a-160">No dispositivo 1: Selecione o botão **Iniciar Sessão do Azure**</span><span class="sxs-lookup"><span data-stu-id="e435a-160">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="e435a-161">No dispositivo 1: Selecione o botão **Criar Âncora do Azure** (cria a âncora na localização do objeto TableAnchor e armazena as informações de âncora no recurso do Azure).</span><span class="sxs-lookup"><span data-stu-id="e435a-161">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="e435a-162">No dispositivo 1: Selecione o botão **Compartilhar Âncora do Azure** (compartilha a ID da âncora com os outros usuários em tempo real)</span><span class="sxs-lookup"><span data-stu-id="e435a-162">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="e435a-163">No dispositivo 2: Selecione o botão **Iniciar Sessão do Azure**</span><span class="sxs-lookup"><span data-stu-id="e435a-163">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="e435a-164">No dispositivo 2: Selecione o botão **Obter Âncora do Azure** (conecta-se ao recurso do Azure para recuperar as informações de âncora da ID da âncora compartilhada e, em seguida, move o objeto TableAnchor para a localização em que a âncora foi criada com o dispositivo 1)</span><span class="sxs-lookup"><span data-stu-id="e435a-164">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="e435a-165">Se você não tiver acesso a dois dispositivos HoloLens, poderá seguir [Como criar Âncoras Espaciais do Azure para dispositivos móveis](mr-learning-asa-05.md) para implantar o projeto em seu dispositivo móvel.</span><span class="sxs-lookup"><span data-stu-id="e435a-165">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e435a-166">Parabéns</span><span class="sxs-lookup"><span data-stu-id="e435a-166">Congratulations</span></span>

<span data-ttu-id="e435a-167">Neste tutorial, você aprendeu a integrar as Âncoras Espaciais do Azure avançadas para alinhar dispositivos em uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="e435a-167">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="e435a-168">Isso também conclui esta série de tutoriais em que você aprendeu a configurar uma conta do Photon, criar um aplicativo PUN, integrar o PUN ao projeto do Unity, configurar os avatars e objetos compartilhados do usuário e, por fim, alinhar vários participantes usando as Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="e435a-168">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>

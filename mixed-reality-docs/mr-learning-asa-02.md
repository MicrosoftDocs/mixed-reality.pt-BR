---
title: Tutoriais de Âncoras Espaciais do Azure – 2. Introdução às Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d117839e51e586f4b905a20510fffc670d34cd4e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376488"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="94811-105">2. Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="94811-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="94811-106">Overview</span></span>

<span data-ttu-id="94811-107">Neste tutorial, você vai explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure e criar, carregar e baixá-las em apenas um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="94811-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="94811-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="94811-108">Objectives</span></span>

* <span data-ttu-id="94811-109">Conheça os conceitos básicos do desenvolvimento com Âncoras Espaciais do Azure para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="94811-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="94811-110">Saber como criar âncoras espaciais e buscá-las no Azure</span><span class="sxs-lookup"><span data-stu-id="94811-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="94811-111">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="94811-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="94811-112">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="94811-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="94811-113">Para isso, primeiro siga [Como inicializar o seu projeto e implantar o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar o seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="94811-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="94811-114">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="94811-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="94811-115">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="94811-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="94811-116">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="94811-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="94811-117">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="94811-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="94811-118">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="94811-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="94811-119">[Criar e configurar a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar um nome adequado à cena, por exemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="94811-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="94811-120">Em seguida, siga as instruções em [Alterar a opção de exibição de reconhecimento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:</span><span class="sxs-lookup"><span data-stu-id="94811-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="94811-121">Alterar o **perfil de configuração do MRTK** para **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="94811-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="94811-122">Alterar as **opções de exibição da malha de reconhecimento espacial** para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="94811-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="94811-123">Instalar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="94811-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="94811-124">No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes** para abrir a janela Gerenciador de Pacotes e selecione **AR Foundation** e clique no botão **Instalar** para instalar o pacote:</span><span class="sxs-lookup"><span data-stu-id="94811-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="94811-126">Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure e será importado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="94811-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="94811-127">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="94811-127">Importing the tutorial assets</span></span>

<span data-ttu-id="94811-128">Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:</span><span class="sxs-lookup"><span data-stu-id="94811-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="94811-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versão 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="94811-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="94811-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="94811-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="94811-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="94811-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="94811-132">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="94811-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="94811-134">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções em [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="94811-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="94811-135">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="94811-135">Preparing the scene</span></span>

<span data-ttu-id="94811-136">Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.</span><span class="sxs-lookup"><span data-stu-id="94811-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="94811-137">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureSpatialAnchors** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:</span><span class="sxs-lookup"><span data-stu-id="94811-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="94811-138">Pré-fabricados **ButtonParent**</span><span class="sxs-lookup"><span data-stu-id="94811-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="94811-139">Pré-fabricados **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="94811-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="94811-140">Pré-fabricados **Instructions**</span><span class="sxs-lookup"><span data-stu-id="94811-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="94811-141">Pré-fabricados **ParentAnchor**</span><span class="sxs-lookup"><span data-stu-id="94811-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="94811-143">Se você considerar que ícones grandes na sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Utensílio</a> para a posição de desligado, conforme mostrado na imagem acima.</span><span class="sxs-lookup"><span data-stu-id="94811-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="94811-144">Como configurar os botões para operar a cena</span><span class="sxs-lookup"><span data-stu-id="94811-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="94811-145">Nesta seção, você adicionará scripts à cena para criar uma série de eventos de botão que demonstram os conceitos básicos de como as âncoras locais e as Âncoras Espaciais do Azure se comportam em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94811-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="94811-146">Na janela Hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="94811-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="94811-147">Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="94811-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="94811-148">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **StartAzureSession ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="94811-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="94811-150">Na janela Hierarquia, selecione o próximo botão denominado **StopAzureSession**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="94811-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="94811-151">Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="94811-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="94811-152">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **StopAzureSession ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="94811-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="94811-154">Na janela Hierarquia, selecione o próximo botão denominado **CreateAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="94811-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="94811-155">Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="94811-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="94811-156">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **CreateAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="94811-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="94811-157">Atribua o objeto **ParentAnchor** ao campo vazio **Nenhum (Objeto de Jogo)** para torná-lo o argumento para a função CreateAzureAnchor ()</span><span class="sxs-lookup"><span data-stu-id="94811-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="94811-159">Na janela Hierarquia, selecione o próximo botão denominado **RemoveLocalAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="94811-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="94811-160">Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="94811-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="94811-161">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **RemoveLocalAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="94811-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="94811-162">Atribua o objeto **ParentAnchor** ao campo vazio **Nenhum (Objeto de Jogo)** para torná-lo o argumento para a função RemoveLocalAnchor ()</span><span class="sxs-lookup"><span data-stu-id="94811-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="94811-164">Na janela Hierarquia, selecione o próximo botão denominado **FindAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="94811-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="94811-165">Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="94811-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="94811-166">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **FindAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="94811-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="94811-168">Na janela Hierarquia, selecione o próximo botão denominado **DeleteAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="94811-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="94811-169">Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="94811-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="94811-170">Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **DeleteAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="94811-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="94811-172">Como conectar a cena ao recurso do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="94811-173">Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, localize o componente **Gerenciador de Âncora Espacial (Script)** .</span><span class="sxs-lookup"><span data-stu-id="94811-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="94811-174">Configure a seção **Credenciais** com as credenciais da conta das Âncoras Espaciais do Azure criada como parte dos [Pré-requisitos](mr-learning-asa-01.md#prerequisites) desta série de tutoriais:</span><span class="sxs-lookup"><span data-stu-id="94811-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="94811-175">No campo **ID da Conta das Âncoras Espaciais**, cole a **ID da Conta** da sua conta das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="94811-176">No campo **Chave de Conta das Âncoras Espaciais**, cole a **Chave de Acesso** primária ou secundária da sua conta das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="94811-178">Experimentando os comportamentos básicos das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="94811-179">As Âncoras Espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade delas, você precisa criar o projeto e implantar o aplicativo no seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="94811-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="94811-180">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="94811-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="94811-181">Quando o aplicativo for executado no seu dispositivo, siga as instruções na tela exibidas no painel Instruções do Tutorial de Âncora Espacial do Azure:</span><span class="sxs-lookup"><span data-stu-id="94811-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="94811-182">Mover o cubo para uma localização diferente</span><span class="sxs-lookup"><span data-stu-id="94811-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="94811-183">Iniciar a Sessão do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-183">Start Azure Session</span></span>
1. <span data-ttu-id="94811-184">Criar Âncora do Azure (cria uma âncora na localização do cubo).</span><span class="sxs-lookup"><span data-stu-id="94811-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="94811-185">Interromper a Sessão do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-185">Stop Azure Session</span></span>
1. <span data-ttu-id="94811-186">Remover a Âncora Local (permite que o usuário mova o cubo)</span><span class="sxs-lookup"><span data-stu-id="94811-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="94811-187">Mover o cubo para outro lugar</span><span class="sxs-lookup"><span data-stu-id="94811-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="94811-188">Iniciar a Sessão do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-188">Start Azure Session</span></span>
1. <span data-ttu-id="94811-189">Localizar a Âncora do Azure (posiciona o cubo na localização da etapa 3)</span><span class="sxs-lookup"><span data-stu-id="94811-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="94811-190">Excluir a Âncora do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="94811-191">Interromper a sessão do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="94811-193">As Âncoras Espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="94811-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="94811-194">Como ancorar uma experiência</span><span class="sxs-lookup"><span data-stu-id="94811-194">Anchoring an experience</span></span>

<span data-ttu-id="94811-195">Nas seções anteriores, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="94811-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="94811-196">Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada.</span><span class="sxs-lookup"><span data-stu-id="94811-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="94811-197">Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="94811-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="94811-198">Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="94811-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="94811-199">Altere a **Escala X** para 1,1</span><span class="sxs-lookup"><span data-stu-id="94811-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="94811-200">Altere a **Escala Z** para 1,1</span><span class="sxs-lookup"><span data-stu-id="94811-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="94811-202">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados** > **Rover** e, em seguida, clique e arraste o pré-fabricado **RoverExplorer_Complete** na janela Hierarquia para adicioná-lo à cena:</span><span class="sxs-lookup"><span data-stu-id="94811-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="94811-204">Com o objeto RocketLauncher_Complete recém-adicionado ainda selecionado na janela Hierarquia, arraste-o sobre o objeto **ParentAnchor** para torná-lo um filho do objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="94811-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="94811-206">Se agora você recompilar o projeto e implantar o aplicativo no seu dispositivo, você poderá reposicionar toda a experiência do Explorador do Rover movendo o cubo redimensionado.</span><span class="sxs-lookup"><span data-stu-id="94811-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="94811-207">Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de utensílios de posição e rotação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="94811-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="94811-208">Parabéns</span><span class="sxs-lookup"><span data-stu-id="94811-208">Congratulations</span></span>

<span data-ttu-id="94811-209">Neste tutorial, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="94811-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="94811-210">Este tutorial forneceu vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="94811-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="94811-211">Além disso, para criar, carregar e baixar Âncoras Espaciais do Azure em um único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="94811-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="94811-212">No próximo tutorial, você aprenderá a salvar as IDs de âncora do Azure no seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado, bem como a transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.</span><span class="sxs-lookup"><span data-stu-id="94811-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="94811-213">Próximo tutorial: 3. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="94811-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)

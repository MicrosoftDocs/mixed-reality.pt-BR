---
title: Tutoriais de âncoras espaciais do Azure-1. Introdução às âncoras espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334452"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="99912-105">1. Introdução às âncoras espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="99912-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="99912-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="99912-106">Overview</span></span>

<span data-ttu-id="99912-107">Bem-vindo à segunda série dos tutoriais do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="99912-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="99912-108">Nesta série de tutoriais de três partes, você aprenderá os conceitos básicos das âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="99912-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="99912-109">Neste primeiro tutorial, [introdução às âncoras espaciais do Azure](mrlearning-asa-ch1.md), você irá explorar as várias etapas necessárias para iniciar e parar uma sessão do Azure e criar, carregar e baixar âncoras do Azure em um único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="99912-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="99912-110">No segundo tutorial, [salvando, recuperando e compartilhando âncoras espaciais do Azure](mrlearning-asa-ch2.md), você aprenderá como salvar âncoras espaciais do Azure em várias sessões de aplicativo salvando informações de âncora no armazenamento do HoloLens 2 e como compartilhar essas informações de âncora para outros dispositivos para um alinhamento de âncora de vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="99912-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="99912-111">No terceiro tutorial, [exibindo comentários de âncora espacial do Azure](mrlearning-asa-ch3.md), você aprenderá a fornecer aos usuários comentários sobre eventos de âncora e status ao usar âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="99912-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="99912-112">Objetivos</span><span class="sxs-lookup"><span data-stu-id="99912-112">Objectives</span></span>

* <span data-ttu-id="99912-113">Conheça os conceitos básicos do desenvolvimento com âncoras espaciais do Azure para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="99912-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="99912-114">Criar, carregar e baixar âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="99912-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99912-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="99912-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="99912-116">Se você ainda não concluiu a série de [tutoriais de introdução](mrlearning-base.md) , é recomendável que você conclua esses tutoriais primeiro.</span><span class="sxs-lookup"><span data-stu-id="99912-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="99912-117">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="99912-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="99912-118">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="99912-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="99912-119">Alguma capacidade C# básica de programação</span><span class="sxs-lookup"><span data-stu-id="99912-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="99912-120">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="99912-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="99912-121">Conclua a seção [criar um recurso de âncoras espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [início rápido: criar um aplicativo de HoloLens do Unity que usa âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="99912-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

>[!IMPORTANT]
><span data-ttu-id="99912-122">Esta série de tutoriais requer o <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> e a versão recomendada é o Unity 2019.1.14.</span><span class="sxs-lookup"><span data-stu-id="99912-122">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="99912-123">Isso substitui quaisquer requisitos de versão do Unity ou recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="99912-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="99912-124">Criando o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="99912-124">Creating the Unity project</span></span>

<span data-ttu-id="99912-125">Nesta seção, você criará um novo projeto do Unity e o configurará para a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="99912-125">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="99912-126">Crie um projeto do Unity e dê a ele um nome adequado, por exemplo, _tutorial de âncoras espaciais do Azure_.</span><span class="sxs-lookup"><span data-stu-id="99912-126">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="99912-127">Configure o projeto do Unity para a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="99912-127">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="99912-128">Para um lembrete sobre como criar um projeto do Unity e configurá-lo para a realidade mista do Windows, você pode consultar as seções [criar novo projeto](mrlearning-base-ch1.md#create-new-unity-project) do Unity e [Configurar o projeto do Unity para a realidade mista do Windows](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) do tutorial [inicializando seu projeto e primeiro aplicativo](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) que faz parte da série de [tutoriais de introdução](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="99912-128">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="99912-129">Adicionando pacotes de Unity embutidos</span><span class="sxs-lookup"><span data-stu-id="99912-129">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="99912-130">Nesta seção, você adicionará ativos e pacotes de Unity embutidos exigidos pelos kits de recursos e SDKs que você usará no projeto.</span><span class="sxs-lookup"><span data-stu-id="99912-130">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="99912-131">Importar recursos essenciais do TMP.</span><span class="sxs-lookup"><span data-stu-id="99912-131">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="99912-132">Estamos adicionando este pacote porque ele é exigido pelo kit de ferramentas da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="99912-132">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="99912-133">No menu do Unity, selecione **janela** > **TextMeshPro** > **importar recursos essenciais do tmp**.</span><span class="sxs-lookup"><span data-stu-id="99912-133">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="99912-135">Na janela pop-up importar pacote do Unity, primeiro verifique se todos os ativos estão selecionados clicando no botão **tudo** e, em seguida, importe os ativos clicando no botão **importar** .</span><span class="sxs-lookup"><span data-stu-id="99912-135">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="99912-137">Instale o AR Foundation.</span><span class="sxs-lookup"><span data-stu-id="99912-137">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="99912-138">Estamos adicionando este pacote porque ele é exigido pelo SDK de âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="99912-138">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="99912-139">No menu do Unity, selecione **janela** > **Gerenciador de pacotes**.</span><span class="sxs-lookup"><span data-stu-id="99912-139">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="99912-141">Na janela Gerenciador de pacotes, selecione **ar Foundation** e instale o pacote clicando no botão **instalar** .</span><span class="sxs-lookup"><span data-stu-id="99912-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="99912-142">Pode levar alguns segundos até que o pacote do AR Foundation seja exibido na lista.</span><span class="sxs-lookup"><span data-stu-id="99912-142">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="99912-144">Importando os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="99912-144">Importing the tutorial assets</span></span>

<span data-ttu-id="99912-145">Nesta seção, você baixará e importará todos os ativos do tutorial.</span><span class="sxs-lookup"><span data-stu-id="99912-145">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="99912-146">Baixe os ativos.</span><span class="sxs-lookup"><span data-stu-id="99912-146">Download the assets.</span></span>

    * <span data-ttu-id="99912-147">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versão 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="99912-147">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="99912-148">Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="99912-148">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="99912-149">MRTK. HoloLens2. Unity. tutoriais. assets. GettingStarted. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="99912-149">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="99912-150">MRTK. HoloLens2. Unity. tutoriais. assets. AzureSpatialAnchors. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="99912-150">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="99912-151">Importe os ativos.</span><span class="sxs-lookup"><span data-stu-id="99912-151">Import the assets.</span></span>

    <span data-ttu-id="99912-152">No menu do Unity, selecione **ativos** > **Importar pacote** > **pacote personalizado...** .</span><span class="sxs-lookup"><span data-stu-id="99912-152">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="99912-154">No pacote de importação... janela pop-up, selecione **AzureSpatialAnchors. unitypackage** e clique no botão **abrir** .</span><span class="sxs-lookup"><span data-stu-id="99912-154">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="99912-156">Na janela pop-up importar pacote do Unity, primeiro verifique se todos os ativos estão selecionados clicando no botão **tudo** e, em seguida, importe os ativos clicando no botão **importar** .</span><span class="sxs-lookup"><span data-stu-id="99912-156">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="99912-158">Repita essas etapas para importar os pacotes de ativos restantes.</span><span class="sxs-lookup"><span data-stu-id="99912-158">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="99912-159">Depois de concluído, a pasta de **ativos** do seu projeto de Unity deve conter essas subpastas.</span><span class="sxs-lookup"><span data-stu-id="99912-159">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="99912-161">Criando e preparando a cena</span><span class="sxs-lookup"><span data-stu-id="99912-161">Creating and preparing the scene</span></span>

<span data-ttu-id="99912-162">Nesta seção, você criará e preparará a cena adicionando o kit de ferramentas de realidade misturada e algumas das pré-fabricados do tutorial.</span><span class="sxs-lookup"><span data-stu-id="99912-162">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="99912-163">Crie uma nova cena.</span><span class="sxs-lookup"><span data-stu-id="99912-163">Create a new scene.</span></span>

    <span data-ttu-id="99912-164">No menu do Unity, selecione **arquivo** > **nova cena**.</span><span class="sxs-lookup"><span data-stu-id="99912-164">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="99912-166">No menu do Unity, selecione **arquivo** > **salvar como...** .</span><span class="sxs-lookup"><span data-stu-id="99912-166">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="99912-168">Na janela pop-up salvar cena, navegue até a pasta de **cenas** do projeto, dê um nome adequado à sua cena, por exemplo, _ASATutorialScene_, e salve a cena clicando no botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="99912-168">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="99912-170">Você pode salvar a cena em qualquer lugar em que desejar, desde que ela esteja dentro da pasta de ativos do projeto.</span><span class="sxs-lookup"><span data-stu-id="99912-170">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="99912-171">No entanto, para manter seu projeto organizado, é geralmente recomendável salvá-lo na pasta de cenas do projeto.</span><span class="sxs-lookup"><span data-stu-id="99912-171">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="99912-172">Adicione o kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="99912-172">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="99912-173">No menu do Unity, selecione o **Kit de ferramentas de realidade misturada** > **Adicionar à cena e configurar...** .</span><span class="sxs-lookup"><span data-stu-id="99912-173">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="99912-175">Na janela pop-up selecionar MixedRealityToolkitConfigurationProfile, clique no **DefaultHoloLens2ConfigurationProfile** para defini-lo como o perfil de configuração de MRTK da cena.</span><span class="sxs-lookup"><span data-stu-id="99912-175">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="99912-177">No menu do Unity, selecione **arquivo** > **salvar** para salvar a cena.</span><span class="sxs-lookup"><span data-stu-id="99912-177">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="99912-179">Você pode usar o atalho de teclado CTRL + S (comando + S no macOS) para salvar rapidamente sua cena enquanto estiver trabalhando neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="99912-179">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="99912-180">Adicione o tutorial pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="99912-180">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="99912-181">No painel projeto, navegue até **ativos** > **MRTK. Tutoriais. AzureSpatialAnchors** > pasta **pré-fabricados**</span><span class="sxs-lookup"><span data-stu-id="99912-181">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="99912-182">Enquanto pressiona o botão CTRL (comando no macOS), clique em **ButtonParent**, **DebugWindow**e **ParentAnchor** para selecionar os três pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="99912-182">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="99912-184">Com os três pré-fabricados ainda selecionados, arraste-os para o painel hierarquia para adicioná-los à cena.</span><span class="sxs-lookup"><span data-stu-id="99912-184">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="99912-186">Para se concentrar nos objetos da cena, você pode clicar duas vezes no objeto ParentAnchor e, em seguida, aplicar um pouco mais zoom novamente.</span><span class="sxs-lookup"><span data-stu-id="99912-186">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="99912-188">Se você encontrar os ícones grandes em sua cena, por exemplo, os ícones grandes, você poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o utensílios</a> para a posição desligado.</span><span class="sxs-lookup"><span data-stu-id="99912-188">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="99912-189">Configurando os botões para operar a cena</span><span class="sxs-lookup"><span data-stu-id="99912-189">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="99912-190">Nesta seção, você adicionará pré-fabricados e scripts à cena para criar uma série de botões que demonstram os conceitos básicos de como as âncoras locais e as âncoras espaciais do Azure se comportam em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99912-190">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="99912-191">Configure o componente de botão pressionável holo Lens 2 (script).</span><span class="sxs-lookup"><span data-stu-id="99912-191">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="99912-192">No painel hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**.</span><span class="sxs-lookup"><span data-stu-id="99912-192">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="99912-194">No painel Inspetor, role para baixo até o componente de **botão pressionável holo lente 2 (script)** e adicione um novo ouvinte de eventos ao evento **botão pressionado ()** clicando no ícone de **+** .</span><span class="sxs-lookup"><span data-stu-id="99912-194">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="99912-196">Com o objeto StartAzureSession ainda selecionado no painel hierarquia, clique e arraste o objeto **ParentAnchor** do painel hierarquia para o campo **nenhum (objeto)** vazio do ouvinte de eventos que você acabou de adicionar para fazer com que o objeto ParentAnchor escute eventos pressionados desse botão.</span><span class="sxs-lookup"><span data-stu-id="99912-196">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="99912-198">Clique no menu suspenso **sem função** do mesmo ouvinte de evento e selecione **AnchorModuleScript** > **StartAzureSession ()** para definir a função StartAzureSession () como a ação disparada quando os eventos pressionados pelo botão são acionados desse botão.</span><span class="sxs-lookup"><span data-stu-id="99912-198">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="99912-200">Configure o componente de interação (script).</span><span class="sxs-lookup"><span data-stu-id="99912-200">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="99912-201">Com o objeto StartAzureSession ainda selecionado no painel hierarquia, no painel Inspetor, role para baixo até o componente **interagir (script)** e repita o mesmo processo como na etapa 1 acima para o evento **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="99912-201">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="99912-203">Configurar os botões restantes</span><span class="sxs-lookup"><span data-stu-id="99912-203">Configure the remaining buttons</span></span>

    <span data-ttu-id="99912-204">Para cada um dos botões restantes, conclua o processo descrito na etapa 1 e 2 acima para atribuir funções a ambos os eventos de botão pressionado () e OnClick () a seguir:</span><span class="sxs-lookup"><span data-stu-id="99912-204">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="99912-205">Para o objeto **StopAzureSession** , atribua a função **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="99912-205">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="99912-206">Para o objeto **createanchor** , atribua a função **CreateAzureAnchor ()** e, em seguida, arraste o **ParentAnchor** novamente para o campo **nenhum (objeto de jogo)** vazio.</span><span class="sxs-lookup"><span data-stu-id="99912-206">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="99912-207">Para o objeto **começar a procurar âncora** , atribua a função **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="99912-207">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="99912-208">Para o objeto **excluir âncora do Azure** , atribua a função **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="99912-208">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="99912-209">Para o objeto **excluir âncora local** , atribua a função **RemoveLocalAnchor ()** e, em seguida, arraste o **ParentAnchor** novamente para o campo **nenhum (objeto de jogo)** vazio.</span><span class="sxs-lookup"><span data-stu-id="99912-209">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="99912-210">Conectar a cena ao recurso do Azure</span><span class="sxs-lookup"><span data-stu-id="99912-210">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="99912-211">No painel hierarquia, selecione o objeto **ParentAnchor** e, no painel Inspetor, role para baixo até o componente **Gerenciador de âncora espacial (script)** .</span><span class="sxs-lookup"><span data-stu-id="99912-211">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="99912-212">Em seguida, na seção **credenciais** , Cole a ID da conta de âncoras espaciais e a chave nos campos ID da conta das **âncoras espaciais** e **âncoras** espaciais correspondentes.</span><span class="sxs-lookup"><span data-stu-id="99912-212">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="99912-213">Você criou sua ID e chave de conta de âncoras espaciais como parte dos [pré-requisitos](mrlearning-asa-ch1.md#prerequisites)deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="99912-213">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="99912-215">Certifique-se de salvar sua cena.</span><span class="sxs-lookup"><span data-stu-id="99912-215">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="99912-216">Experimentando os comportamentos básicos das âncoras espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="99912-216">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="99912-217">Agora que sua cena está configurada para demonstrar os conceitos básicos das âncoras espaciais do Azure, é hora de implantar o aplicativo para que você possa experimentar as âncoras espaciais do Azure em primeira mão.</span><span class="sxs-lookup"><span data-stu-id="99912-217">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="99912-218">Adicione recursos adicionais necessários.</span><span class="sxs-lookup"><span data-stu-id="99912-218">Add additional required capabilities.</span></span>

    <span data-ttu-id="99912-219">No menu do Unity, selecione **editar** > **configurações do projeto...** para abrir o painel configurações do Player.</span><span class="sxs-lookup"><span data-stu-id="99912-219">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="99912-221">No painel configurações do Player, selecione **Player** e, em seguida, **Publicar configurações**.</span><span class="sxs-lookup"><span data-stu-id="99912-221">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="99912-223">Nas **configurações de publicação**, role para baixo até a seção **recursos** e verifique se o **SpatialPerception**, que você habilitou quando criou o projeto no início do tutorial, está habilitado.</span><span class="sxs-lookup"><span data-stu-id="99912-223">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="99912-224">Em seguida, habilitou os recursos **internetclient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **webcam**e **Microphone** .</span><span class="sxs-lookup"><span data-stu-id="99912-224">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="99912-226">Implante o aplicativo no seu HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="99912-226">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="99912-227">Para obter um lembrete sobre como criar e implantar seu projeto do Unity no HoloLens 2, você pode consultar as seções [criar seu aplicativo em seu dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) do tutorial [inicializando seu projeto e primeiro aplicativo](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , que faz parte da série de [tutoriais de introdução](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="99912-227">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="99912-228">Execute o aplicativo e siga as instruções no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99912-228">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="99912-229">As âncoras espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="99912-229">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="99912-230">Quando o aplicativo estiver em execução no seu dispositivo, siga as instruções na tela exibidas no painel de **instruções do módulo âncora espacial do Azure** .</span><span class="sxs-lookup"><span data-stu-id="99912-230">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="99912-232">Ancorando uma experiência</span><span class="sxs-lookup"><span data-stu-id="99912-232">Anchoring an experience</span></span>

<span data-ttu-id="99912-233">Nas seções anteriores, você aprendeu os conceitos básicos das âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="99912-233">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="99912-234">Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada.</span><span class="sxs-lookup"><span data-stu-id="99912-234">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="99912-235">Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="99912-235">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="99912-236">Adicione a experiência do Rocket Launcher.</span><span class="sxs-lookup"><span data-stu-id="99912-236">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="99912-237">No painel projeto, navegue até **ativos** > **MRTK. Tutoriais. GettingStarted** > pasta **pré-fabricados** e selecione o **Rocket Launcher_Complete** pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="99912-237">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="99912-239">Com o Rocket Launcher_Complete pré-fabricado ainda selecionado, arraste-o sobre o objeto **ParentAnchor** no painel hierarquia para torná-lo um filho do objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="99912-239">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="99912-241">Reposicione a experiência do Rocket Launcher.</span><span class="sxs-lookup"><span data-stu-id="99912-241">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="99912-242">Mova o objeto de Launcher_Complete do módulo **Rocket** para que o **ParentAnchor** (o cubo) ainda seja exposto.</span><span class="sxs-lookup"><span data-stu-id="99912-242">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="99912-244">No aplicativo, os usuários agora podem reposicionar toda a experiência do Rocket Launcher movendo o cubo.</span><span class="sxs-lookup"><span data-stu-id="99912-244">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="99912-245">Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de posição e rotação utensílios e muito mais.</span><span class="sxs-lookup"><span data-stu-id="99912-245">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="99912-246">Parabéns</span><span class="sxs-lookup"><span data-stu-id="99912-246">Congratulations</span></span>

<span data-ttu-id="99912-247">Neste tutorial, você aprendeu os conceitos básicos das âncoras espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="99912-247">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="99912-248">Esta lição forneceu a você vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão do Azure e criar, carregar e baixar âncoras do Azure em um único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="99912-248">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="99912-249">Na próxima lição, você aprenderá a salvar as IDs de âncora do Azure em seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado e como transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.</span><span class="sxs-lookup"><span data-stu-id="99912-249">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="99912-250">Próxima lição: 2. salvando, recuperando e compartilhando âncoras espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="99912-250">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

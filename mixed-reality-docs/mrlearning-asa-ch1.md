---
title: Tutoriais de Âncoras Espaciais do Azure – 1. Introdução às Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: fa0ebc409fa38f664bdd0966906c6fd77f7a6081
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376143"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="a2014-105">1. Introdução às Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="a2014-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="a2014-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="a2014-106">Overview</span></span>

<span data-ttu-id="a2014-107">Bem-vindo à segunda série de tutoriais do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a2014-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="a2014-108">Nesta série de tutoriais de três partes, você aprenderá os conceitos básicos das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="a2014-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="a2014-109">Neste primeiro tutorial, [Introdução às Âncoras Espaciais do Azure](mrlearning-asa-ch1.md), você vai explorar as várias etapas necessárias para iniciar e parar uma sessão do Azure e criar, carregar e baixar âncoras do Azure em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a2014-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="a2014-110">No segundo tutorial, [Salvar, recuperar e compartilhar Âncoras Espaciais do Azure](mrlearning-asa-ch2.md), você aprenderá a salvar Âncoras Espaciais do Azure em várias sessões de aplicativo salvando informações de âncora no armazenamento do HoloLens 2 e como compartilhar essas informações de âncora para outros dispositivos para um alinhamento de âncora de vários dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a2014-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="a2014-111">No terceiro tutorial, [Exibir feedback de Âncora Espacial do Azure](mrlearning-asa-ch3.md), você aprenderá a fornecer aos usuários comentários sobre eventos de âncora e status ao usar Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="a2014-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="a2014-112">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a2014-112">Objectives</span></span>

* <span data-ttu-id="a2014-113">Conheça os conceitos básicos do desenvolvimento com Âncoras Espaciais do Azure para o HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a2014-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="a2014-114">Criar, carregar e baixar âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="a2014-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a2014-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a2014-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="a2014-116">Se você ainda não concluiu a série de [Tutoriais de introdução](mrlearning-base.md), recomendamos que você a conclua primeiro.</span><span class="sxs-lookup"><span data-stu-id="a2014-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="a2014-117">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="a2014-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="a2014-118">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="a2014-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a2014-119">Alguma habilidade básica de programação em C#</span><span class="sxs-lookup"><span data-stu-id="a2014-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="a2014-120">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="a2014-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a2014-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="a2014-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="a2014-122">Conclua a seção [Criar um recurso de Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Guia de início rápido: criar um aplicativo HoloLens do Unity que usa Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="a2014-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2014-123">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="a2014-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="a2014-124">Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="a2014-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="a2014-125">Como criar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="a2014-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="a2014-126">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a2014-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="a2014-127">Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mrlearning-base-ch1.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="a2014-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="a2014-128">[Criar um projeto do Unity](mrlearning-base-ch1.md#create-new-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*.</span><span class="sxs-lookup"><span data-stu-id="a2014-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="a2014-129">Configurar o projeto do Unity para o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a2014-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="a2014-130">Importar recursos do TextMesh Pro Essential</span><span class="sxs-lookup"><span data-stu-id="a2014-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="a2014-131">Importar o Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a2014-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="a2014-132">Configurar o projeto do Unity para o Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a2014-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="a2014-133">[Adicionar o Mixed Reality Toolkit à cena do Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e dar um nome adequado à cena, por exemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="a2014-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="a2014-134">Então siga as instruções de [Como configurar os perfis do Mixed Reality Toolkit (Opção de Alterar Exibição de Reconhecimento Espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição para a malha de reconhecimento espacial para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="a2014-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="a2014-135">Conforme mencionado nas instruções de [Como configurar o projeto do Unity para o Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) vinculadas acima, é altamente recomendável não habilitar o MSBuild para o Unity.</span><span class="sxs-lookup"><span data-stu-id="a2014-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="a2014-136">Como adicionar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="a2014-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="a2014-137">Nesta seção, você instalará o pacote interno da AR Foundation do Unity porque ele é exigido pelo SDK de Âncoras Espaciais do Azure que será importado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="a2014-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="a2014-138">No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes**:</span><span class="sxs-lookup"><span data-stu-id="a2014-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a2014-140">Pode levar alguns segundos até que o pacote de AR Foundation seja exibido na lista.</span><span class="sxs-lookup"><span data-stu-id="a2014-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="a2014-141">Na janela Gerenciador de Pacotes, selecione **AR Foundation** e instale o pacote clicando no botão **Instalar**:</span><span class="sxs-lookup"><span data-stu-id="a2014-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a2014-143">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="a2014-143">Importing the tutorial assets</span></span>

<span data-ttu-id="a2014-144">Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:</span><span class="sxs-lookup"><span data-stu-id="a2014-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="a2014-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versão 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="a2014-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="a2014-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a2014-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="a2014-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a2014-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="a2014-148">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="a2014-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="a2014-149">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="a2014-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="a2014-151">Como criar e preparar a cena</span><span class="sxs-lookup"><span data-stu-id="a2014-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="a2014-152">Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.</span><span class="sxs-lookup"><span data-stu-id="a2014-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="a2014-153">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.AzureSpatialAnchors** > **Pré-Fabricados**.</span><span class="sxs-lookup"><span data-stu-id="a2014-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="a2014-154">Mantendo o botão CTRL pressionado, clique em **ButtonParent**, **DebugWindow**, **Instruções** e **ParentAnchor** para selecionar os quatro pré-fabricados:</span><span class="sxs-lookup"><span data-stu-id="a2014-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="a2014-156">Com os quatro pré-fabricados ainda selecionados, arraste-os para a janela Hierarquia para adicioná-los à cena:</span><span class="sxs-lookup"><span data-stu-id="a2014-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="a2014-158">Para se concentrar nos objetos da cena, você pode clicar duas vezes no objeto ParentAnchor e, em seguida, reduzir levemente o zoom de novo:</span><span class="sxs-lookup"><span data-stu-id="a2014-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="a2014-160">Se você considerar que ícones grandes em sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição de desligado.</span><span class="sxs-lookup"><span data-stu-id="a2014-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="a2014-161">Como configurar os botões para operar a cena</span><span class="sxs-lookup"><span data-stu-id="a2014-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="a2014-162">Nesta seção, você adicionará scripts à cena para criar uma série de eventos de botão que demonstram os conceitos básicos de como as âncoras locais e as Âncoras Espaciais do Azure se comportam em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2014-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="a2014-163">1. Configurar o componente de botão pressionável HoloLens 2 (Script)</span><span class="sxs-lookup"><span data-stu-id="a2014-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="a2014-164">Na janela Hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="a2014-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="a2014-166">Na janela Inspetor, localize o componente **Botão Pressionável HoloLens 2 (Script)** e adicione um novo ouvinte de eventos ao evento **Botão Pressionado ()** clicando no ícone **+** :</span><span class="sxs-lookup"><span data-stu-id="a2014-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="a2014-168">Com o objeto StartAzureSession ainda selecionado na janela Hierarquia, clique e arraste o objeto **ParentAnchor** da janela Hierarquia para o campo **Nenhum (Objeto)** vazio do ouvinte de eventos que você acabou de adicionar para fazer com que o objeto ParentAnchor escute eventos pressionados desse botão:</span><span class="sxs-lookup"><span data-stu-id="a2014-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="a2014-170">Clique no menu suspenso **Nenhuma Função** do mesmo ouvinte de eventos e selecione **AnchorModuleScript** > **StartAzureSession ()** para definir a função StartAzureSession () como a ação disparada quando os eventos pressionados pelo botão são acionados desse botão:</span><span class="sxs-lookup"><span data-stu-id="a2014-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="a2014-172">2. Configurar o componente Interação (Script)</span><span class="sxs-lookup"><span data-stu-id="a2014-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="a2014-173">Com o objeto StartAzureSession ainda selecionado na janela hierarquia, na janela Inspetor, localize o componente **Interação (Script)** e repita o mesmo processo, como na etapa 1 acima, para o evento **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="a2014-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="a2014-175">3. Configurar os botões restantes</span><span class="sxs-lookup"><span data-stu-id="a2014-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="a2014-176">Para cada um dos botões restantes, conclua o processo descrito nas etapas 1 e 2 acima para atribuir funções aos eventos **Botão Pressionado ()** e **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="a2014-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="a2014-177">Para o objeto **StopAzureSession**, atribua a função AnchorModuleScript > **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="a2014-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="a2014-178">Para o objeto **CreateAzureAnchor**, atribua a função AnchorModuleScript > **CreateAzureAnchor ()** ,</span><span class="sxs-lookup"><span data-stu-id="a2014-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="a2014-179">em seguida, arraste **ParentAnchor** novamente para o campo **Nenhum (Objeto de Jogo)** vazio.</span><span class="sxs-lookup"><span data-stu-id="a2014-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="a2014-180">Para o objeto **RemoveLocalAnchor**, atribua a função AnchorModuleScript > **RemoveLocalAnchor ()** ,</span><span class="sxs-lookup"><span data-stu-id="a2014-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="a2014-181">em seguida, arraste **ParentAnchor** novamente para o campo **Nenhum (Objeto de Jogo)** vazio.</span><span class="sxs-lookup"><span data-stu-id="a2014-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="a2014-182">Para o objeto **FindAzureAnchor**, atribua a função AnchorModuleScript > **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="a2014-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="a2014-183">Para o objeto **DeleteAzureAnchor**, atribua a função AnchorModuleScript > **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="a2014-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="a2014-184">4. Conectar a cena ao recurso do Azure</span><span class="sxs-lookup"><span data-stu-id="a2014-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="a2014-185">Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, role para baixo até o componente **Gerenciador de Âncora Espacial (Script)** .</span><span class="sxs-lookup"><span data-stu-id="a2014-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="a2014-186">Em seguida, na seção **Credenciais**, cole a ID e a chave de conta de Âncoras Espaciais que você criou como parte dos [Pré-requisitos](mrlearning-asa-ch1.md#prerequisites) do tutorial, para os campos **ID da Conta de Âncoras Espaciais** e **Chave da Conta de Âncoras Espaciais** correspondentes:</span><span class="sxs-lookup"><span data-stu-id="a2014-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="a2014-188">Experimentando os comportamentos básicos das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="a2014-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="a2014-189">Agora que sua cena está configurada para demonstrar os conceitos básicos das âncoras espaciais do Azure, é hora de implantar o aplicativo para que você possa experimentar as Âncoras Espaciais do Azure em primeira mão.</span><span class="sxs-lookup"><span data-stu-id="a2014-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="a2014-190">1. Adicionar funcionalidades adicionais necessárias</span><span class="sxs-lookup"><span data-stu-id="a2014-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="a2014-191">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Jogador:</span><span class="sxs-lookup"><span data-stu-id="a2014-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="a2014-193">Na janela Configurações do Jogador, selecione **Jogador** e **Configurações de Publicação**:</span><span class="sxs-lookup"><span data-stu-id="a2014-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="a2014-195">Em **Configurações de Publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="a2014-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="a2014-196">Em seguida, habilite as funcionalidades **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** e **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="a2014-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="a2014-198">2. Implantar o aplicativo em seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a2014-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="a2014-199">As Âncoras Espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade delas, você precisa implantar o projeto em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a2014-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="a2014-200">Para obter um lembrete sobre como criar e implantar seu projeto do Unity no HoloLens 2, confira as instruções para [Criar o aplicativo para seu dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="a2014-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="a2014-201">3. Execute o aplicativo no seu HoloLens 2 e siga as instruções no aplicativo</span><span class="sxs-lookup"><span data-stu-id="a2014-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="a2014-202">As Âncoras Espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="a2014-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="a2014-203">Quando o aplicativo estiver em execução no seu dispositivo, siga as instruções na tela exibidas no painel Instruções do Tutorial de Âncora Espacial do Azure:</span><span class="sxs-lookup"><span data-stu-id="a2014-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="a2014-205">Como ancorar uma experiência</span><span class="sxs-lookup"><span data-stu-id="a2014-205">Anchoring an experience</span></span>

<span data-ttu-id="a2014-206">Nas seções anteriores, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="a2014-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a2014-207">Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada.</span><span class="sxs-lookup"><span data-stu-id="a2014-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="a2014-208">Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="a2014-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="a2014-209">1. Adicionar a experiência do Lançador de Foguete</span><span class="sxs-lookup"><span data-stu-id="a2014-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="a2014-210">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.GettingStarted** > **Pré-fabricados** > **RocketLauncher** e selecione o pré-fabricado **RocketLauncher_Complete**:</span><span class="sxs-lookup"><span data-stu-id="a2014-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="a2014-212">Com o pré-fabricado RocketLauncher_Complete ainda selecionado, arraste-o sobre o objeto **ParentAnchor** na janela Hierarquia para torná-lo um filho do objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="a2014-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="a2014-214">2. Reposicionar a experiência do Lançador de Foguete</span><span class="sxs-lookup"><span data-stu-id="a2014-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="a2014-215">Posicione, gire e dimensione o objeto **RocketLauncher_Complete** para uma escala e uma orientação adequadas e, ao mesmo tempo, garanta que o objeto **ParentAnchor** ainda seja exposto, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a2014-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="a2014-216">**Posição** da Transformação X = 0, Y = 0, Z = 3,75</span><span class="sxs-lookup"><span data-stu-id="a2014-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="a2014-217">**Rotação** da Transformação X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="a2014-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="a2014-218">**Escala** da Transformação X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="a2014-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="a2014-220">No aplicativo, os usuários agora podem reposicionar toda a experiência do Lançador de Foguete movendo o cubo.</span><span class="sxs-lookup"><span data-stu-id="a2014-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="a2014-221">Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de utensílios de posição e rotação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="a2014-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a2014-222">Parabéns</span><span class="sxs-lookup"><span data-stu-id="a2014-222">Congratulations</span></span>

<span data-ttu-id="a2014-223">Neste tutorial, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="a2014-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a2014-224">O tutorial forneceu vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure e criar, carregar e baixar as Âncoras Espaciais do Azure em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a2014-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="a2014-225">Na próxima lição, você aprenderá a salvar as IDs de âncora do Azure em seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado, bem como a transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.</span><span class="sxs-lookup"><span data-stu-id="a2014-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="a2014-226">Próxima lição: 2. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="a2014-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)

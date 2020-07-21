---
title: Tutoriais de Nuvem do Azure – 1. Serviços de Nuvem do Azure para HoloLens 2
description: Conclua este curso para aprender a implementar diversos serviços do Azure em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: azure, mixed reality, unity, tutorial, hololens, hololens 2, azure blob storage, azure table storage, azure spatial anchors, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303925"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="20337-105">1. Serviços de Nuvem do Azure para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="20337-105">1. Azure Cloud Services for HoloLens 2</span></span>

## <a name="overview"></a><span data-ttu-id="20337-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="20337-106">Overview</span></span>

<span data-ttu-id="20337-107">Bem-vindo(a) a esta série de tutoriais voltados para colocar serviços de **Nuvem do Azure** em um aplicativo do **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="20337-107">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="20337-108">Nesta série de tutoriais em cinco partes, você aprenderá a integrar vários serviços de **Nuvem do Azure** em um projeto **Unity** para o **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="20337-108">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="20337-109">Ao passar em cada capítulo, você adicionará novos serviços de **Nuvem do Azure** para expandir os recursos do aplicativo e a experiência do usuário, aprendendo ao mesmo tempo os conceitos básicos de cada serviço de **Nuvem do Azure**.</span><span class="sxs-lookup"><span data-stu-id="20337-109">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="20337-110">Esta série de tutoriais se concentrará no **HoloLens 2** mas, devido à natureza multiplataforma do Unity, a maioria dos seus aprendizados também se aplicará a aplicativos para Desktop e Smartphone.</span><span class="sxs-lookup"><span data-stu-id="20337-110">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="20337-111">Neste primeiro tutorial, [Apresentação dos Serviços de Nuvem do Azure para o HoloLens 2](mr-learning-azure-01.md), você vai começar explicando as metas do aplicativo, vai apresentar brevemente cada serviço de Nuvem do Azure e vai configurar o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="20337-111">In this first tutorial, [Introducing Azure Cloud Services for HoloLens 2](mr-learning-azure-01.md), you begin by explaining the goals of the application, briefly introduce you to each Azure Cloud service and set up the unity project.</span></span>

<span data-ttu-id="20337-112">No segundo tutorial, [Integração do Armazenamento do Azure](mr-learning-azure-02.md), você vai começar integrando o Armazenamento do Azure como a solução de persistência para o aplicativo de demonstração, vai aprender as diferenças entre Armazenamento de Blobs e Armazenamento de Tabelas, vai preparar os recursos de projeto necessários, vai configurar a cena e vai verificar as operações de leitura, atualização e exclusão de dados.</span><span class="sxs-lookup"><span data-stu-id="20337-112">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you start off by integrating Azure Storage as the persistence solution for the demo application, learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene and verify the read, update and delete data operations.</span></span>

<span data-ttu-id="20337-113">Continuando com o terceiro tutorial, [Integração da Visão Personalizada do Azure](mr-learning-azure-03.md), você usará a Visão Personalizada do Azure para treinar e detectar imagens no aplicativo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="20337-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="20337-114">O capítulo começa com a configuração de seu próprio recurso de Visão Personalizada do Azure, preparando os componentes da cena e entrando em ação treinando e detectando suas próprias imagens de dentro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20337-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="20337-115">Em seguida, você avançará para o quarto tutorial, [Integração de Âncoras Espaciais do Azure](mr-learning-azure-04.md), com a exploração do serviço Âncoras Espaciais do Azure para salvar e encontrar locais, aprender os principais conceitos, preparar os recursos necessários, configurar a cena e começar a usar o novo recurso no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20337-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="20337-116">Com o quinto tutorial, [Integração do Serviço de Bot do Azure com o LUIS](mr-learning-azure-05.md), você finaliza fornecendo ao aplicativo um novo método de interação do usuário: idioma natural!</span><span class="sxs-lookup"><span data-stu-id="20337-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="20337-117">Esse recurso será realizado usando o Azure Bot Framework junto com o LUIS (Reconhecimento Vocal).</span><span class="sxs-lookup"><span data-stu-id="20337-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="20337-118">Este capítulo final ensina os conceitos básicos do Serviço de Bot do Azure e para acelerar o processo, você usará o Bot Framework Composer como uma solução sem código.</span><span class="sxs-lookup"><span data-stu-id="20337-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="20337-119">Depois que o bot for criado, você o integrará à cena e fará com que ele seja executado com o estágio final do aplicativo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="20337-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="20337-120">Metas do aplicativo</span><span class="sxs-lookup"><span data-stu-id="20337-120">Application goals</span></span>

<span data-ttu-id="20337-121">Nesta série de tutoriais, você criará um aplicativo do **HoloLens 2** que poderá detectar objetos em imagens e encontrar seu local espacial.</span><span class="sxs-lookup"><span data-stu-id="20337-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="20337-122">Para definir um idioma de domínio, essas entidades passarão a ser chamadas de **Objeto Rastreado**.</span><span class="sxs-lookup"><span data-stu-id="20337-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="20337-123">O usuário pode criar um **Objeto Rastreado** para associar um conjunto de imagens por meio da pesquisa visual computacional e/ou de um local espacial.</span><span class="sxs-lookup"><span data-stu-id="20337-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="20337-124">Todos os dados devem ser persistidos na nuvem.</span><span class="sxs-lookup"><span data-stu-id="20337-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="20337-125">Além disso, alguns aspectos do aplicativo serão controlados opcionalmente pelo idioma natural por meio de um bot.</span><span class="sxs-lookup"><span data-stu-id="20337-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="20337-126">Recursos</span><span class="sxs-lookup"><span data-stu-id="20337-126">Features</span></span>

* <span data-ttu-id="20337-127">Gerenciamento básico de dados e imagens</span><span class="sxs-lookup"><span data-stu-id="20337-127">Basic managing of data and images</span></span>
* <span data-ttu-id="20337-128">Treinamento e detecção de imagem</span><span class="sxs-lookup"><span data-stu-id="20337-128">Image training and detection</span></span>
* <span data-ttu-id="20337-129">Armazenamento de um local espacial e diretrizes para ele</span><span class="sxs-lookup"><span data-stu-id="20337-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="20337-130">Assistente de bot para usar alguns recursos por meio de linguagem natural</span><span class="sxs-lookup"><span data-stu-id="20337-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="20337-131">Serviços de Nuvem do Azure</span><span class="sxs-lookup"><span data-stu-id="20337-131">Azure Cloud services</span></span>

<span data-ttu-id="20337-132">Para resolver os recursos necessários para o aplicativo, você usará esses serviços de **Nuvem do Azure**:</span><span class="sxs-lookup"><span data-stu-id="20337-132">To solve the required features for the application, you will use these **Azure Cloud** services:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="20337-133">Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="20337-133">Azure Storage</span></span>

<span data-ttu-id="20337-134">Você usará o [Armazenamento do Azure](https://azure.microsoft.com/services/storage/) para a solução de persistência.</span><span class="sxs-lookup"><span data-stu-id="20337-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="20337-135">Ele permite que você armazene dados em uma tabela e carregue binários grandes, como imagens.</span><span class="sxs-lookup"><span data-stu-id="20337-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="20337-136">Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="20337-136">Azure Custom Vision</span></span>

<span data-ttu-id="20337-137">Com a [Visão Personalizada do Azure](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (parte dos [Serviços Cognitivos do Azure](https://azure.microsoft.com/services/cognitive-services/)), você pode associar um conjunto de imagens a *Objetos Rastreados*, treinar um modelo de machine learning no conjunto e detectar o *Objeto Rastreado*.</span><span class="sxs-lookup"><span data-stu-id="20337-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="20337-138">Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="20337-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="20337-139">Para armazenar o local de um *Objeto Rastreado* e fornecer instruções guiadas para encontrá-lo, você usa [Âncoras Espaciais do Azure](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="20337-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="20337-140">Serviço de Bot do Azure</span><span class="sxs-lookup"><span data-stu-id="20337-140">Azure Bot Service</span></span>

<span data-ttu-id="20337-141">O aplicativo é conduzido principalmente pela interface do usuário tradicional, por isso você usa o [Serviço de Bot do Azure](https://azure.microsoft.com/services/bot-service/) para adicionar alguma personalidade e agir como um novo método de interação.</span><span class="sxs-lookup"><span data-stu-id="20337-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20337-142">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="20337-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="20337-143">Se você ainda não concluiu a série de [Tutoriais de introdução](mr-learning-base-01.md), recomendamos que você a conclua primeiro.</span><span class="sxs-lookup"><span data-stu-id="20337-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="20337-144">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="20337-144">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="20337-145">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="20337-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="20337-146">Alguma habilidade básica de programação em C#</span><span class="sxs-lookup"><span data-stu-id="20337-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="20337-147">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="20337-147">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="20337-148">Uma webcam conectada se você quiser testar no editor do Unity</span><span class="sxs-lookup"><span data-stu-id="20337-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="20337-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="20337-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="20337-150">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.3.X.</span><span class="sxs-lookup"><span data-stu-id="20337-150">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="20337-151">Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="20337-151">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="20337-152">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="20337-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="20337-153">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="20337-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="20337-154">Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="20337-154">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="20337-155">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais de Nuvem do Azure*</span><span class="sxs-lookup"><span data-stu-id="20337-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="20337-156">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="20337-156">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="20337-157">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="20337-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="20337-158">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="20337-158">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="20337-159">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="20337-159">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="20337-160">[Criar e configurar a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar um nome adequado à cena, por exemplo, *AzureCloudServices*</span><span class="sxs-lookup"><span data-stu-id="20337-160">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="20337-161">Então siga as instruções em [Alterar a opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição para a malha de reconhecimento espacial para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="20337-161">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="20337-162">Instalar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="20337-162">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="20337-163">No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes** para abrir a janela Gerenciador de Pacotes e selecione **AR Foundation** e clique no botão **Instalar** para instalar o pacote:</span><span class="sxs-lookup"><span data-stu-id="20337-163">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="20337-165">Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure e será importado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="20337-165">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="20337-166">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="20337-166">Importing the tutorial assets</span></span>

<span data-ttu-id="20337-167">Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:</span><span class="sxs-lookup"><span data-stu-id="20337-167">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="20337-168">Armazenamento do Azure para Unity</span><span class="sxs-lookup"><span data-stu-id="20337-168">Azure storage for Unity</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="20337-169">Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="20337-169">Azure Spatial Anchors</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [<span data-ttu-id="20337-170">MRTK.Tutorials.AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="20337-170">MRTK.Tutorials.AzureCloudServices</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="20337-171">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="20337-171">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="20337-172">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="20337-172">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="20337-174">Como criar e preparar a cena</span><span class="sxs-lookup"><span data-stu-id="20337-174">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="20337-175">Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.</span><span class="sxs-lookup"><span data-stu-id="20337-175">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="20337-176">Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**.</span><span class="sxs-lookup"><span data-stu-id="20337-176">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="20337-177">Mantendo pressionada a tecla CTRL, clique em **SceneController**, **RootMenu** e **DataManager** para selecionar os três pré-fabricados:</span><span class="sxs-lookup"><span data-stu-id="20337-177">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="20337-179">O **SceneController (prefab)** contém dois scripts: **SceneController (script)** e **UnityDispatcher (script)** .</span><span class="sxs-lookup"><span data-stu-id="20337-179">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="20337-180">O componente de script **SceneController** contém várias funções de UX e facilita a funcionalidade de captura de fotos e o **UnityDispatcher** é uma classe auxiliar para permitir a execução de ações no thread principal do Unity.</span><span class="sxs-lookup"><span data-stu-id="20337-180">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="20337-181">O **RootMenu (prefab)** é o pré-fabricado da interface do usuário principal que mantém todas as janelas da interface do usuário conectadas entre si por meio de vários pequenos componentes de script e que controla o fluxo geral de UX do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20337-181">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="20337-182">O **DataManager (prefab)** é responsável por conversar com o armazenamento do Azure e será explicado mais detalhadamente no próximo tutorial.</span><span class="sxs-lookup"><span data-stu-id="20337-182">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="20337-183">Agora, com os três pré-fabricados ainda selecionados, arraste-os para a janela Hierarquia para adicioná-los à cena:</span><span class="sxs-lookup"><span data-stu-id="20337-183">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="20337-185">Para se concentrar nos objetos da cena, clique duas vezes no objeto **RootMenu** e, em seguida, reduzir levemente o zoom de novo:</span><span class="sxs-lookup"><span data-stu-id="20337-185">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="20337-187">Se você considerar que ícones grandes em sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição de desligado.</span><span class="sxs-lookup"><span data-stu-id="20337-187">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="20337-188">Configurando a cena</span><span class="sxs-lookup"><span data-stu-id="20337-188">Configuring the scene</span></span>

<span data-ttu-id="20337-189">Nesta seção, você conectará *SceneManager*, *DataManager* e *RootMenu* juntos para ter uma cena funcional pronta para o seguinte tutorial, [Integrar o armazenamento do Azure](mr-learning-azure-01.md).</span><span class="sxs-lookup"><span data-stu-id="20337-189">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="20337-190">Conectar os objetos</span><span class="sxs-lookup"><span data-stu-id="20337-190">Connect the objects</span></span>

<span data-ttu-id="20337-191">Na janela Hierarquia, selecione o objeto **DataManager**:</span><span class="sxs-lookup"><span data-stu-id="20337-191">In the Hierarchy window, select the **DataManager** object:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="20337-193">Na janela do Inspetor, localize o componente **DataManager (script)** e você verá um slot vazio no evento **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="20337-193">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="20337-194">Agora, na janela Hierarquia, arraste o objeto **SceneController** para o evento **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="20337-194">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="20337-196">Você observará que o menu suspenso do evento se tornou ativo; clique no menu suspenso e navegue até **SceneController** e, no submenu, selecione a opção **Init ()** :</span><span class="sxs-lookup"><span data-stu-id="20337-196">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="20337-198">Na janela Hierarquia, selecione o objeto **SceneController**; então, no Inspetor, você encontrará o componente **SceneController** (script).</span><span class="sxs-lookup"><span data-stu-id="20337-198">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="20337-200">Você verá que há vários campos não preenchidos; nós vamos alterar isso.</span><span class="sxs-lookup"><span data-stu-id="20337-200">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="20337-201">Mova o objeto **DataManager** da Hierarquia para o campo *Gerenciador de Dados* e mova o GameObject **RootMenu** da Hierarquia para o campo *Menu Principal*.</span><span class="sxs-lookup"><span data-stu-id="20337-201">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="20337-203">Agora, sua cena está pronta para os próximos tutoriais.</span><span class="sxs-lookup"><span data-stu-id="20337-203">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="20337-204">Não se esqueça de salvá-la em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="20337-204">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="20337-205">Preparar pipeline de Build do projeto</span><span class="sxs-lookup"><span data-stu-id="20337-205">Prepare project build pipeline</span></span>

<span data-ttu-id="20337-206">Embora o projeto ainda tenha que ser preenchido com conteúdo, você precisa executar alguns preparativos para que o projeto fique pronto para a compilação para o **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="20337-206">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="20337-207">1. Adicionar funcionalidades adicionais necessárias</span><span class="sxs-lookup"><span data-stu-id="20337-207">1. Add additional required capabilities</span></span>

<span data-ttu-id="20337-208">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="20337-208">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="20337-210">Na janela Configurações do Projeto, selecione **Jogador** e **Configurações de Publicação**:</span><span class="sxs-lookup"><span data-stu-id="20337-210">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="20337-212">Em **Configurações de Publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="20337-212">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="20337-213">Em seguida, habilite as funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** e **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="20337-213">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="20337-215">2. Implantar o aplicativo em seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="20337-215">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="20337-216">Nem todos os recursos que você usará nesta série de tutoriais podem ser executados dentro do editor do Unity; isso significa que você precisa estar familiarizado com a implantação do aplicativo em seu dispositivo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="20337-216">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="20337-217">Para se lembrar de como criar e implantar seu projeto do Unity no HoloLens 2, confira as instruções em [Tutoriais de introdução – Criar o aplicativo para seu dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="20337-217">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="20337-218">3. Execute o aplicativo no seu HoloLens 2 e siga as instruções no aplicativo</span><span class="sxs-lookup"><span data-stu-id="20337-218">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="20337-219">Todos os Serviços do Azure usam a Internet, portanto, verifique se o dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="20337-219">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="20337-220">Quando o aplicativo estiver em execução no dispositivo, aceite o acesso às seguintes funcionalidades solicitadas:</span><span class="sxs-lookup"><span data-stu-id="20337-220">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="20337-221">Microfone</span><span class="sxs-lookup"><span data-stu-id="20337-221">Microphone</span></span>
* <span data-ttu-id="20337-222">Câmera</span><span class="sxs-lookup"><span data-stu-id="20337-222">Camera</span></span>

<span data-ttu-id="20337-223">Esses recursos são necessários para serviços como *Chat Bot* e *Visão Personalizada* funcionarem corretamente.</span><span class="sxs-lookup"><span data-stu-id="20337-223">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="20337-224">Parabéns</span><span class="sxs-lookup"><span data-stu-id="20337-224">Congratulations</span></span>

<span data-ttu-id="20337-225">Neste tutorial, você foi apresentado à série de tutoriais, aprendeu sobre os recursos que você implementará e como os serviços de **Nuvem do Azure** se unem para dar vida ao seu aplicativo do *HoloLens 2*.</span><span class="sxs-lookup"><span data-stu-id="20337-225">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="20337-226">Você adicionou os componentes necessários ao projeto e preparou a cena para esta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="20337-226">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="20337-227">Na próxima lição, você usará o armazenamento do Azure como uma solução de persistência baseada em nuvem para armazenar dados e imagens.</span><span class="sxs-lookup"><span data-stu-id="20337-227">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

[<span data-ttu-id="20337-228">Próximo tutorial: 2. Integrar o armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="20337-228">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)

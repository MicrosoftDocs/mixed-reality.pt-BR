---
title: Tutoriais de recursos multiusuário – 1. Configurar o Photon Unity Networking
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610768"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="b8621-105">1. Configurar o Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="b8621-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="b8621-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b8621-106">Overview</span></span>

<span data-ttu-id="b8621-107">Neste tutorial, você aprenderá a se preparar para criar uma experiência compartilhada usando o PUN (Photon Unity Networking).</span><span class="sxs-lookup"><span data-stu-id="b8621-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="b8621-108">O Photon é uma das várias opções de rede disponíveis para os desenvolvedores de realidade misturada criarem experiências compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="b8621-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="b8621-109">Você aprenderá a criar um aplicativo Photon PUN, importar ativos do Photon PUN para o seu projeto do Unity e conectá-lo ao aplicativo Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="b8621-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="b8621-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b8621-110">Objectives</span></span>

* <span data-ttu-id="b8621-111">Aprender a criar um aplicativo Photon PUN</span><span class="sxs-lookup"><span data-stu-id="b8621-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="b8621-112">Aprender a encontrar e importar os ativos do Photon PUN</span><span class="sxs-lookup"><span data-stu-id="b8621-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="b8621-113">Aprender a conectar seu projeto do Unity ao aplicativo Photon PUN</span><span class="sxs-lookup"><span data-stu-id="b8621-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b8621-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b8621-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="b8621-115">Se você ainda não concluiu os [Tutoriais de introdução](mrlearning-base.md) e a série de [Tutoriais das Âncoras Espaciais do Azure](mrlearning-asa-ch1.md), recomendamos que você conclua esses tutoriais primeiro.</span><span class="sxs-lookup"><span data-stu-id="b8621-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="b8621-116">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="b8621-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="b8621-117">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="b8621-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b8621-118">Alguma habilidade básica de programação em C#</span><span class="sxs-lookup"><span data-stu-id="b8621-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="b8621-119">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="b8621-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="b8621-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="b8621-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="b8621-121">Conclua a seção [Criar um recurso de Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Guia de início rápido: Criar um aplicativo HoloLens do Unity que usa as Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="b8621-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8621-122">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="b8621-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="b8621-123">Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="b8621-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="b8621-124">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="b8621-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="b8621-125">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="b8621-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="b8621-126">Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mrlearning-base-ch1.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="b8621-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="b8621-127">[Criar um projeto do Unity](mrlearning-base-ch1.md#create-new-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="b8621-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="b8621-128">Configurar o projeto do Unity para o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b8621-128">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="b8621-129">Importar recursos do TextMesh Pro Essential</span><span class="sxs-lookup"><span data-stu-id="b8621-129">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="b8621-130">Importar o Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b8621-130">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="b8621-131">Configurar o projeto do Unity para o Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b8621-131">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="b8621-132">[Adicionar o Kit de Ferramentas de Realidade Misturada à cena do Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e dar um nome adequado à cena, por exemplo, *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="b8621-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="b8621-133">Então siga as instruções de [Como configurar os perfis do Mixed Reality Toolkit (Opção de Alterar Exibição de Reconhecimento Espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição para a malha de reconhecimento espacial para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="b8621-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="b8621-134">Conforme mencionado nas instruções de [Como configurar o projeto do Unity para o Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) vinculadas acima, é altamente recomendável não habilitar o MSBuild para o Unity.</span><span class="sxs-lookup"><span data-stu-id="b8621-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="b8621-135">Como configurar as funcionalidades</span><span class="sxs-lookup"><span data-stu-id="b8621-135">Configuring the capabilities</span></span>

<span data-ttu-id="b8621-136">No menu do Unity, selecione **Editar** > **Configurações de projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Configurações de Publicação**:</span><span class="sxs-lookup"><span data-stu-id="b8621-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="b8621-138">Em **Configurações de Publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="b8621-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="b8621-139">Em seguida, habilite as funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** e **RemovableStorage**:</span><span class="sxs-lookup"><span data-stu-id="b8621-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="b8621-141">Como adicionar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="b8621-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="b8621-142">Nesta seção, você instalará o pacote interno da AR Foundation do Unity porque ele é exigido pelo SDK de Âncoras Espaciais do Azure que será importado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="b8621-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="b8621-143">No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes**:</span><span class="sxs-lookup"><span data-stu-id="b8621-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b8621-145">Pode levar alguns segundos até que o pacote de AR Foundation seja exibido na lista.</span><span class="sxs-lookup"><span data-stu-id="b8621-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="b8621-146">Na janela Gerenciador de Pacotes, selecione **AR Foundation** e instale o pacote clicando no botão **Instalar**:</span><span class="sxs-lookup"><span data-stu-id="b8621-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b8621-148">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="b8621-148">Importing the tutorial assets</span></span>

<span data-ttu-id="b8621-149">Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:</span><span class="sxs-lookup"><span data-stu-id="b8621-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="b8621-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versão 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="b8621-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="b8621-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b8621-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="b8621-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b8621-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="b8621-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b8621-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="b8621-154">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="b8621-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="b8621-155">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="b8621-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b8621-157">Depois de importar o pacote de ativos do tutorial de MultiUserCapabilities, você verá vários erros [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) na janela do console informando que o tipo ou o namespace está ausente.</span><span class="sxs-lookup"><span data-stu-id="b8621-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="b8621-158">Isso deve ser esperado e será resolvido na próxima seção quando você importar os ativos do Photon.</span><span class="sxs-lookup"><span data-stu-id="b8621-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="b8621-159">Como importar os ativos do Photon</span><span class="sxs-lookup"><span data-stu-id="b8621-159">Importing the Photon assets</span></span>

<span data-ttu-id="b8621-160">Nesta seção, você importará os ativos do PUN (Photon Unity Network) na Asset Store do Unity.</span><span class="sxs-lookup"><span data-stu-id="b8621-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="b8621-161">No menu do Unity, selecione **Janela** > **Asset Store** para abrir a janela da Asset Store, procure e selecione **PUN 2 – GRATUITO** em Sair dos Jogos e clique no botão **Baixar** para baixar o pacote de ativos para a sua conta do Unity:</span><span class="sxs-lookup"><span data-stu-id="b8621-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="b8621-163">Quando o download for concluído, clique no botão **Importar** para abrir a janela Importar Pacote do Unity:</span><span class="sxs-lookup"><span data-stu-id="b8621-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="b8621-165">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="b8621-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="b8621-167">Depois que o Unity concluir o processo de importação, a janela do Assistente do PUN será exibida com o menu Instalação do PUN carregado; ignore ou feche essa janela por enquanto:</span><span class="sxs-lookup"><span data-stu-id="b8621-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="b8621-169">Como configurar o Photon</span><span class="sxs-lookup"><span data-stu-id="b8621-169">Setting up Photon</span></span>

<span data-ttu-id="b8621-170">Nesta seção, você criará uma conta do Photon, se ainda não tiver uma, e criará um aplicativo PUN.</span><span class="sxs-lookup"><span data-stu-id="b8621-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="b8621-171">Navegue até o <a href="https://dashboard.photonengine.com/account/signin" target="_blank">painel</a> do Photon e entre nele caso já tenha uma conta que deseja usar; caso contrário, clique no link **Criar Uma** e siga as instruções para registrar uma nova conta:</span><span class="sxs-lookup"><span data-stu-id="b8621-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="b8621-173">Depois que estiver conectado, clique no botão **Criar um Aplicativo**:</span><span class="sxs-lookup"><span data-stu-id="b8621-173">Once signed in, click the **Create a New App** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="b8621-175">Na página Criar um Aplicativo, insira os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="b8621-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="b8621-176">Em Tipo do Photon, selecione Photon PUN</span><span class="sxs-lookup"><span data-stu-id="b8621-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="b8621-177">Em Nome, insira um nome adequado, por exemplo, _Tutoriais do MRTK_</span><span class="sxs-lookup"><span data-stu-id="b8621-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="b8621-178">Em Descrição, opcionalmente, insira uma descrição adequada</span><span class="sxs-lookup"><span data-stu-id="b8621-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="b8621-179">Em URL, deixe o campo vazio</span><span class="sxs-lookup"><span data-stu-id="b8621-179">For Url, leave the field empty</span></span>

<span data-ttu-id="b8621-180">Em seguida, clique no botão **Criar** para criar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b8621-180">Then click the **Create** button to create the new application:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="b8621-182">Depois que o Photon tiver concluído o processo de criação, o novo aplicativo PUN será exibido no painel:</span><span class="sxs-lookup"><span data-stu-id="b8621-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="b8621-184">Como conectar o projeto do Unity ao aplicativo PUN</span><span class="sxs-lookup"><span data-stu-id="b8621-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="b8621-185">Nesta seção, você conectará seu projeto do Unity ao aplicativo PUN criado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="b8621-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="b8621-186">No painel do Photon, clique no campo **ID do Aplicativo** para revelar a ID do aplicativo e, em seguida, copie-o para a área de transferência:</span><span class="sxs-lookup"><span data-stu-id="b8621-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="b8621-188">No menu do Unity, selecione **Janela** > **Photon Unity Networking** > **Assistente do PUN** para abrir a janela do Assistente do PUN, clique no botão **Projeto de Instalação** para abrir o menu Instalação do PUN e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b8621-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="b8621-189">No campo **ID do Aplicativo ou Email**, cole a ID do aplicativo PUN copiado na etapa anterior</span><span class="sxs-lookup"><span data-stu-id="b8621-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="b8621-190">Em seguida, clique no botão **Projeto de Instalação** para aplicar a ID do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b8621-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="b8621-192">Depois que o Unity concluir o processo de configuração do PUN, o menu Instalação do PUN exibirá a mensagem **Concluído!**</span><span class="sxs-lookup"><span data-stu-id="b8621-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="b8621-193">e selecionará automaticamente o ativo **PhotonServerSettings** na janela Projeto, de modo que as propriedades sejam exibidas na janela Inspetor:</span><span class="sxs-lookup"><span data-stu-id="b8621-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="b8621-195">Parabéns</span><span class="sxs-lookup"><span data-stu-id="b8621-195">Congratulations</span></span>

<span data-ttu-id="b8621-196">Você criou um aplicativo Photon PUN com êxito e o conectou ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="b8621-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="b8621-197">A próxima etapa será permitir conexões com outros usuários para que vários usuários possam ver uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="b8621-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="b8621-198">[Próximo tutorial: 2. Conectar vários usuários](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="b8621-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>

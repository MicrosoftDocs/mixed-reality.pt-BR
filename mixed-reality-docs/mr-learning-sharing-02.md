---
title: Tutoriais de recursos multiusuário – 2. Configurar o Photon Unity Networking
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: e5817338dbed944232664a86f8b0625bc9d3e1e7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304133"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="0669f-105">2. Configurar o Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="0669f-105">2. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="0669f-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="0669f-106">Overview</span></span>

<span data-ttu-id="0669f-107">Neste tutorial, você vai se preparar para criar uma experiência compartilhada usando o PUN (Photon Unity Networking).</span><span class="sxs-lookup"><span data-stu-id="0669f-107">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="0669f-108">Você aprenderá a criar um aplicativo PUN, importar ativos PUN para seu projeto do Unity e conectar seu projeto do Unity ao aplicativo PUN.</span><span class="sxs-lookup"><span data-stu-id="0669f-108">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="0669f-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0669f-109">Objectives</span></span>

* <span data-ttu-id="0669f-110">Saiba como criar um aplicativo PUN</span><span class="sxs-lookup"><span data-stu-id="0669f-110">Learn how to create a PUN app</span></span>
* <span data-ttu-id="0669f-111">Saber como encontrar e importar os ativos PUN</span><span class="sxs-lookup"><span data-stu-id="0669f-111">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="0669f-112">Saiba como conectar seu projeto do Unity ao aplicativo PUN</span><span class="sxs-lookup"><span data-stu-id="0669f-112">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="0669f-113">Como criar e preparar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="0669f-113">Creating and preparing the Unity project</span></span>

<span data-ttu-id="0669f-114">Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.</span><span class="sxs-lookup"><span data-stu-id="0669f-114">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="0669f-115">Para isso, primeiro siga [Como inicializar o seu projeto e implantar o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar o seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="0669f-115">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="0669f-116">[Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*</span><span class="sxs-lookup"><span data-stu-id="0669f-116">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="0669f-117">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="0669f-117">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="0669f-118">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="0669f-118">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="0669f-119">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="0669f-119">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="0669f-120">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="0669f-120">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="0669f-121">[Criar e configurar a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar um nome adequado à cena, por exemplo, *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="0669f-121">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="0669f-122">Em seguida, siga as instruções em [Alterar a opção de exibição de reconhecimento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:</span><span class="sxs-lookup"><span data-stu-id="0669f-122">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="0669f-123">Alterar o **perfil de configuração do MRTK** para **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="0669f-123">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="0669f-124">Alterar as **opções de exibição da malha de reconhecimento espacial** para **Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="0669f-124">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="0669f-125">Como habilitar funcionalidades adicionais</span><span class="sxs-lookup"><span data-stu-id="0669f-125">Enabling additional capabilities</span></span>

<span data-ttu-id="0669f-126">No menu do Unity, selecione **Editar** > **Configurações de projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Configurações de Publicação**:</span><span class="sxs-lookup"><span data-stu-id="0669f-126">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="0669f-128">Em **Configurações de publicação**, role para baixo até a seção **Funcionalidades** e verifique novamente se as funcionalidades **InternetClient**, **Microfone**, **SpatialPerception** e **GazeInput**, que você habilitou durante a etapa [Como configurar o projeto Unity](mr-learning-base-02.md#configuring-the-unity-project) acima estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="0669f-128">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="0669f-129">Em seguida, habilite as seguintes funcionalidades adicionais:</span><span class="sxs-lookup"><span data-stu-id="0669f-129">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="0669f-130">Funcionalidade **InternetClientServer**</span><span class="sxs-lookup"><span data-stu-id="0669f-130">**InternetClientServer** capability</span></span>
* <span data-ttu-id="0669f-131">Funcionalidade **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="0669f-131">**PrivateNetworkClientServer** capability</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="0669f-133">Instalar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="0669f-133">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="0669f-134">No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes** para abrir a janela Gerenciador de Pacotes e selecione **AR Foundation** e clique no botão **Instalar** para instalar o pacote:</span><span class="sxs-lookup"><span data-stu-id="0669f-134">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="0669f-136">Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure que você importará na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="0669f-136">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="0669f-137">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="0669f-137">Importing the tutorial assets</span></span>

<span data-ttu-id="0669f-138">Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:</span><span class="sxs-lookup"><span data-stu-id="0669f-138">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="0669f-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versão 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="0669f-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="0669f-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="0669f-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="0669f-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="0669f-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="0669f-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="0669f-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="0669f-143">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="0669f-143">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="0669f-145">Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções em [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="0669f-145">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="0669f-146">Depois de importar o pacote de ativos do tutorial de MultiUserCapabilities, você verá vários erros [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) na janela do console informando que o tipo ou o namespace está ausente.</span><span class="sxs-lookup"><span data-stu-id="0669f-146">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="0669f-147">Isso deve ser esperado e será resolvido na próxima seção quando você importar os ativos PUN.</span><span class="sxs-lookup"><span data-stu-id="0669f-147">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="0669f-148">Como importar os ativos PUN</span><span class="sxs-lookup"><span data-stu-id="0669f-148">Importing the PUN assets</span></span>

<span data-ttu-id="0669f-149">No menu do Unity, selecione **Janela** > **Asset Store** para abrir a janela da Asset Store, pesquise e selecione **PUN 2 – GRATUITO** em Sair dos Jogos e clique no botão **Baixar** para baixar o pacote de ativos para a sua conta do Unity.</span><span class="sxs-lookup"><span data-stu-id="0669f-149">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="0669f-150">Quando o download for concluído, clique no botão **Importar** para abrir a janela Importar Pacote do Unity:</span><span class="sxs-lookup"><span data-stu-id="0669f-150">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="0669f-152">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="0669f-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="0669f-154">Depois que o Unity concluir o processo de importação, a janela do Assistente do PUN será exibida com o menu Instalação do PUN carregado; ignore ou feche essa janela por enquanto:</span><span class="sxs-lookup"><span data-stu-id="0669f-154">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="0669f-156">Como criar o aplicativo PUN</span><span class="sxs-lookup"><span data-stu-id="0669f-156">Creating the PUN application</span></span>

<span data-ttu-id="0669f-157">Nesta seção, você criará uma conta do Photon, se ainda não tiver uma, e criará um aplicativo PUN.</span><span class="sxs-lookup"><span data-stu-id="0669f-157">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="0669f-158">Navegue até o <a href="https://dashboard.photonengine.com/account/signin" target="_blank">painel</a> do Photon e entre nele caso já tenha uma conta que deseja usar; caso contrário, clique no link **Criar Uma** e siga as instruções para registrar uma nova conta:</span><span class="sxs-lookup"><span data-stu-id="0669f-158">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="0669f-160">Depois que estiver conectado, clique no botão **Criar um Aplicativo**:</span><span class="sxs-lookup"><span data-stu-id="0669f-160">Once signed in, click the **Create a New App** button:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="0669f-162">Na página Criar um Aplicativo, insira os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="0669f-162">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="0669f-163">Para o tipo Photon, selecione PUN</span><span class="sxs-lookup"><span data-stu-id="0669f-163">For Photon Type, select PUN</span></span>
* <span data-ttu-id="0669f-164">Em Nome, insira um nome adequado, por exemplo, _Tutoriais do MRTK_</span><span class="sxs-lookup"><span data-stu-id="0669f-164">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="0669f-165">Em Descrição, opcionalmente, insira uma descrição adequada</span><span class="sxs-lookup"><span data-stu-id="0669f-165">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="0669f-166">Em URL, deixe o campo vazio</span><span class="sxs-lookup"><span data-stu-id="0669f-166">For Url, leave the field empty</span></span>

<span data-ttu-id="0669f-167">Em seguida, clique no botão **Criar** para criar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0669f-167">Then click the **Create** button to create the new app:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="0669f-169">Depois que o Photon tiver concluído o processo de criação, o novo aplicativo PUN será exibido no painel:</span><span class="sxs-lookup"><span data-stu-id="0669f-169">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="0669f-171">Como conectar o projeto do Unity ao aplicativo PUN</span><span class="sxs-lookup"><span data-stu-id="0669f-171">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="0669f-172">Nesta seção, você conectará seu projeto do Unity ao aplicativo PUN criado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="0669f-172">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="0669f-173">No painel do Photon, clique no campo **ID do Aplicativo** para revelar a ID do aplicativo e, em seguida, copie-o para a área de transferência:</span><span class="sxs-lookup"><span data-stu-id="0669f-173">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="0669f-175">No menu do Unity, selecione **Janela** > **Photon Unity Networking** > **Assistente do PUN** para abrir a janela do Assistente do PUN, clique no botão **Projeto de Instalação** para abrir o menu Instalação do PUN e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0669f-175">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="0669f-176">No campo **ID do Aplicativo ou Email**, cole a ID do aplicativo PUN copiado na etapa anterior</span><span class="sxs-lookup"><span data-stu-id="0669f-176">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="0669f-177">Em seguida, clique no botão **Projeto de Instalação** para aplicar a ID do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0669f-177">Then click the **Setup Project** button to apply the app ID:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="0669f-179">Depois que o Unity concluir o processo de configuração do PUN, o menu Instalação do PUN exibirá a mensagem **Concluído!**</span><span class="sxs-lookup"><span data-stu-id="0669f-179">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="0669f-180">e selecionará automaticamente o ativo **PhotonServerSettings** na janela Projeto, de modo que as propriedades sejam exibidas na janela Inspetor:</span><span class="sxs-lookup"><span data-stu-id="0669f-180">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="0669f-182">Parabéns</span><span class="sxs-lookup"><span data-stu-id="0669f-182">Congratulations</span></span>

<span data-ttu-id="0669f-183">Você criou um aplicativo PUN com êxito e o conectou ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="0669f-183">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="0669f-184">A próxima etapa será permitir conexões com outros usuários para que vários usuários possam ver uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="0669f-184">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

[<span data-ttu-id="0669f-185">Próximo tutorial: 3. Conectar vários usuários</span><span class="sxs-lookup"><span data-stu-id="0669f-185">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)

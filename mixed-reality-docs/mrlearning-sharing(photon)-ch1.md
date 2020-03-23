---
title: Tutoriais de recursos multiusuário – 1. Configurar o Photon Unity Networking
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031337"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="d3a5f-105">1. Configurar o Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="d3a5f-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="d3a5f-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d3a5f-106">Overview</span></span>

<span data-ttu-id="d3a5f-107">Neste tutorial, você aprenderá a se preparar para criar uma experiência compartilhada importando o PUN (Photon Unity Networking) para seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="d3a5f-108">O Photon é uma das várias opções de rede disponíveis para os desenvolvedores de realidade misturada criarem experiências compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="d3a5f-109">Você aprenderá a criar uma conta do Photon, a importar o Photon e a criar um servidor local opcional</span><span class="sxs-lookup"><span data-stu-id="d3a5f-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="d3a5f-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d3a5f-110">Objectives</span></span>

* <span data-ttu-id="d3a5f-111">Saiba como criar uma conta do Photon</span><span class="sxs-lookup"><span data-stu-id="d3a5f-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="d3a5f-112">Saiba como localizar e importar o Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="d3a5f-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="d3a5f-113">Configurar um servidor local do Photon</span><span class="sxs-lookup"><span data-stu-id="d3a5f-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3a5f-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d3a5f-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="d3a5f-115">Se você ainda não concluiu os [Tutoriais de introdução](mrlearning-base.md) e a série de [Tutoriais de introdução de Âncoras Espaciais do Azure](mrlearning-asa-ch1.md), recomendamos que você conclua esses tutoriais primeiro.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="d3a5f-116">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="d3a5f-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="d3a5f-117">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="d3a5f-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="d3a5f-118">Alguma habilidade básica de programação em C#</span><span class="sxs-lookup"><span data-stu-id="d3a5f-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="d3a5f-119">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="d3a5f-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d3a5f-120">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="d3a5f-121">Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="d3a5f-122">Como configurar o Photon</span><span class="sxs-lookup"><span data-stu-id="d3a5f-122">Setting up Photon</span></span>

1. <span data-ttu-id="d3a5f-123">Configure uma conta do [Photon](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="d3a5f-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="d3a5f-124">Navegue até a página de Inscrição do Photon clicando [neste link](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="d3a5f-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="d3a5f-125">Siga as instruções na página de inscrição para criar a conta.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="d3a5f-128">Crie uma ID de aplicativo clicando no botão Criar um Aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="d3a5f-130">Selecione o PUN do Photon no menu suspenso, em Tipo de Photon.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="d3a5f-131">Em seguida, dê um nome a ele.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-131">Then give it a name.</span></span> <span data-ttu-id="d3a5f-132">Neste exemplo, demos o nome HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="d3a5f-133">Depois de terminar, clique no botão Criar.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="d3a5f-135">Volte para a página de aplicativos e você verá algo semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="d3a5f-136">Clique na ID do aplicativo e copie-a.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-136">Click the application ID and copy it.</span></span> <span data-ttu-id="d3a5f-137">Cole-a em algum lugar que você possa acessar facilmente.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="d3a5f-139">Crie um projeto do Unity e dê a ele o nome de HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="d3a5f-140">Para obter instruções sobre como criar um projeto do Unity, confira a [seção "Criar projeto do Unity" do Módulo Base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="d3a5f-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="d3a5f-141">Depois que o projeto for carregado, clique na guia Repositório de Ativos, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="d3a5f-142">Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite PUN e selecione o ativo Photon PUN 2 – FREE nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="d3a5f-144">Baixe e importe esse ativo pressionando os botões Baixar e Importar.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="d3a5f-146">Depois que o Photon tiver concluído o processo de importação, o Assistente do PUN será exibido.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="d3a5f-147">Pegue a ID do aplicativo (que deve estar na área de transferência) da etapa 4, cole-a na caixa AppID e pressione o botão Configurar Projeto.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="d3a5f-149">Depois de adicionar com sucesso a AppID, navegue até Photon-> PhotonUnityNetworking->Recursos->PhotonServerSettings em Ativos.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="d3a5f-150">Selecione a opção Usar Servidor de Nomes e defina a região fixa como EUA ou sua região de serviço do Photon.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="d3a5f-152">Parabéns</span><span class="sxs-lookup"><span data-stu-id="d3a5f-152">Congratulations</span></span>

<span data-ttu-id="d3a5f-153">Você criou uma conta do Photon com êxito, configurou um servidor Photon local e importou o PUN para o Unity.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="d3a5f-154">A próxima etapa é configurar o projeto e permitir conexões com outros usuários para que vários usuários possam ver seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="d3a5f-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="d3a5f-155">[Próximo tutorial: 2. Preparar o Unity para o desenvolvimento](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="d3a5f-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

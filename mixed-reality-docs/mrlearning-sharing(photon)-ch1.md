---
title: Tutoriais de funcionalidades de vários usuários-1. Configurando a rede do Photon Unity
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 57a23e34404e4bff653d74b7f6afc65adff8b19c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334337"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="89838-105">1. Configurando a rede do Photon Unity</span><span class="sxs-lookup"><span data-stu-id="89838-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="89838-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="89838-106">Overview</span></span>

<span data-ttu-id="89838-107">Neste tutorial, você aprenderá a se preparar para criar uma experiência compartilhada importando o trocadilho (Photon Unity Networking) para seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="89838-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="89838-108">O Photon é uma das várias opções de rede disponíveis para que os desenvolvedores de realidade mista criem experiências compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="89838-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="89838-109">Você aprenderá a criar uma conta do Photon, a importar Photon e a criar um servidor local opcional</span><span class="sxs-lookup"><span data-stu-id="89838-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="89838-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="89838-110">Objectives</span></span>

* <span data-ttu-id="89838-111">Saiba como criar uma conta do Photon</span><span class="sxs-lookup"><span data-stu-id="89838-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="89838-112">Saiba como localizar e importar a rede Photon Unity</span><span class="sxs-lookup"><span data-stu-id="89838-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="89838-113">Configurar um servidor Photon local</span><span class="sxs-lookup"><span data-stu-id="89838-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89838-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="89838-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="89838-115">Se você ainda não concluiu a série de [tutoriais de introdução](mrlearning-base.md) , é recomendável que você conclua esses tutoriais primeiro.</span><span class="sxs-lookup"><span data-stu-id="89838-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="89838-116">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="89838-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="89838-117">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="89838-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="89838-118">Alguma capacidade C# básica de programação</span><span class="sxs-lookup"><span data-stu-id="89838-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="89838-119">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="89838-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="89838-120">Esta série de tutoriais requer o <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> e a versão recomendada é o Unity 2019.1.14.</span><span class="sxs-lookup"><span data-stu-id="89838-120">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="89838-121">Isso substitui quaisquer requisitos de versão do Unity ou recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="89838-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="89838-122">Configurando o Photon</span><span class="sxs-lookup"><span data-stu-id="89838-122">Setting up Photon</span></span>

1. <span data-ttu-id="89838-123">Configure uma conta do [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="89838-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="89838-124">Navegue até a página de inscrição do Photon clicando neste [link](https://dashboard.photonengine.com//Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="89838-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="89838-125">Siga as instruções na página de inscrição para criar a conta.</span><span class="sxs-lookup"><span data-stu-id="89838-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="89838-128">Crie uma ID de aplicativo clicando no botão criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="89838-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="89838-130">Selecione Photon trocadilho no menu suspenso, em Photon Type.</span><span class="sxs-lookup"><span data-stu-id="89838-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="89838-131">Em seguida, dê um nome a ele.</span><span class="sxs-lookup"><span data-stu-id="89838-131">Then give it a name.</span></span> <span data-ttu-id="89838-132">Neste exemplo, nomeamos HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="89838-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="89838-133">Quando terminar, clique no botão criar.</span><span class="sxs-lookup"><span data-stu-id="89838-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="89838-135">Volte para a página de aplicativos e você verá algo semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="89838-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="89838-136">Clique na ID do aplicativo e copie-a.</span><span class="sxs-lookup"><span data-stu-id="89838-136">Click the application ID and copy it.</span></span> <span data-ttu-id="89838-137">Cole em algum lugar que você possa acessar facilmente.</span><span class="sxs-lookup"><span data-stu-id="89838-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="89838-139">Crie um novo projeto do Unity e nomeie-o HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="89838-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="89838-140">Para obter instruções sobre como criar um novo projeto do Unity, consulte [a seção "criar projeto do Unity" do módulo base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="89838-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="89838-141">Depois que o projeto for carregado, clique na guia repositório de ativos, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="89838-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="89838-142">Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite trocadilho e selecione o ativo Photon trocadilho 2-FREE "nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="89838-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="89838-144">Baixe e importe esse ativo pressionando os botões baixar e importar.</span><span class="sxs-lookup"><span data-stu-id="89838-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="89838-146">Depois que o Photon tiver concluído o processo de importação, o assistente de trocadilho será exibido.</span><span class="sxs-lookup"><span data-stu-id="89838-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="89838-147">Pegue a ID do aplicativo (que deve estar na área de transferência) da etapa 4, Cole-a na caixa AppID e pressione o botão configurar projeto.</span><span class="sxs-lookup"><span data-stu-id="89838-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="89838-149">Depois de adicionar o AppID com êxito, navegue até Photon-> PhotonUnityNetworking-> recursos-> PhotonServerSettings em ativos.</span><span class="sxs-lookup"><span data-stu-id="89838-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="89838-150">Selecione a opção usar servidor de nomes e defina a região fixa como US ou sua região de serviço Photon.</span><span class="sxs-lookup"><span data-stu-id="89838-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="89838-152">Parabéns</span><span class="sxs-lookup"><span data-stu-id="89838-152">Congratulations</span></span>

<span data-ttu-id="89838-153">Você criou uma conta do Photon com êxito, configurou um servidor Photon local e importou o trocadilho para o Unity.</span><span class="sxs-lookup"><span data-stu-id="89838-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="89838-154">A próxima etapa é configurar o projeto e permitir conexões com outros usuários para que vários usuários possam ver seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="89838-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="89838-155">[Próximo tutorial: 2. obtendo o Unity pronto para desenvolvimento](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="89838-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

---
title: Tutoriais de funcionalidades de vários usuários-1. Configurando a rede do Photon Unity
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: acb6966ace81180e95e6a0fe447d350572f7c0dd
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701967"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="ee983-105">1. Configurando a rede do Photon Unity</span><span class="sxs-lookup"><span data-stu-id="ee983-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="ee983-106">Neste tutorial, aprenderemos como preparar-se para criar uma experiência compartilhada importando o trocadilho (Photon Unity Networking) para seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="ee983-106">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="ee983-107">O Photon é uma das várias opções de rede disponíveis para que os desenvolvedores de realidade mista criem experiências compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="ee983-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="ee983-108">Nós aprenderemos como criar uma conta do Photon, importar Photon e criar um servidor local opcional</span><span class="sxs-lookup"><span data-stu-id="ee983-108">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="ee983-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ee983-109">Objectives</span></span>

* <span data-ttu-id="ee983-110">Saiba como criar uma conta do Photon</span><span class="sxs-lookup"><span data-stu-id="ee983-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="ee983-111">Saiba como localizar e importar a rede Photon Unity</span><span class="sxs-lookup"><span data-stu-id="ee983-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="ee983-112">Configurar um servidor Photon local</span><span class="sxs-lookup"><span data-stu-id="ee983-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="ee983-113">Configurando o Photon</span><span class="sxs-lookup"><span data-stu-id="ee983-113">Setting up Photon</span></span>

1. <span data-ttu-id="ee983-114">Configure uma conta do [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="ee983-114">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="ee983-115">Navegue até a página de inscrição do Photon clicando neste [link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="ee983-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="ee983-116">Siga as instruções na página de inscrição para criar a conta.</span><span class="sxs-lookup"><span data-stu-id="ee983-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="ee983-119">Crie uma ID de aplicativo clicando no botão criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee983-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="ee983-121">Selecione Photon trocadilho no menu suspenso, em Photon Type.</span><span class="sxs-lookup"><span data-stu-id="ee983-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="ee983-122">Em seguida, dê um nome a ele.</span><span class="sxs-lookup"><span data-stu-id="ee983-122">Then give it a name.</span></span> <span data-ttu-id="ee983-123">Neste exemplo, nomeamos HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="ee983-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="ee983-124">Quando terminar, clique no botão criar.</span><span class="sxs-lookup"><span data-stu-id="ee983-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="ee983-126">Depois disso, volte para a página de aplicativos e você verá algo semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="ee983-126">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="ee983-127">Clique na ID do aplicativo e copie-a.</span><span class="sxs-lookup"><span data-stu-id="ee983-127">Click on the application ID and copy it.</span></span> <span data-ttu-id="ee983-128">Cole em algum lugar que você possa acessar facilmente.</span><span class="sxs-lookup"><span data-stu-id="ee983-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="ee983-130">Crie um novo projeto do Unity e nomeie-o HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="ee983-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="ee983-131">Para obter instruções sobre como criar um novo projeto do Unity, consulte [a seção "criar projeto do Unity" do módulo base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="ee983-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="ee983-132">Depois que o projeto for carregado, clique na guia repositório de ativos, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="ee983-132">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="ee983-133">Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite trocadilho e selecione o ativo Photon trocadilho 2-FREE "nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ee983-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="ee983-135">Baixe e importe esse ativo pressionando os botões baixar e importar.</span><span class="sxs-lookup"><span data-stu-id="ee983-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="ee983-137">Depois que o Photon tiver concluído o processo de importação, o assistente de trocadilho será exibido.</span><span class="sxs-lookup"><span data-stu-id="ee983-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="ee983-138">Pegue a ID do aplicativo (que deve estar na área de transferência) da etapa 4 e cole-a na caixa AppID e pressione o botão configurar projeto.</span><span class="sxs-lookup"><span data-stu-id="ee983-138">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="ee983-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="ee983-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="ee983-140">Depois de adicionar o AppID com êxito, navegue até Photon-> PhotonUnityNetworking-> recursos-> PhotonServerSettings em ativos.</span><span class="sxs-lookup"><span data-stu-id="ee983-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="ee983-141">Selecione a opção usar servidor de nomes e defina a região fixa como US ou sua região de serviço Photon.</span><span class="sxs-lookup"><span data-stu-id="ee983-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="ee983-143">Parabéns</span><span class="sxs-lookup"><span data-stu-id="ee983-143">Congratulations</span></span>

<span data-ttu-id="ee983-144">Você criou uma conta do Photon com êxito, configurou um servidor Photon local e importou o trocadilho para o Unity.</span><span class="sxs-lookup"><span data-stu-id="ee983-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="ee983-145">A próxima etapa é configurar o projeto e, em seguida, permitir conexões com outros usuários para que vários usuários possam ver seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee983-145">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="ee983-146">[Próximo tutorial: 2. Preparar o Unity para o desenvolvimento](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="ee983-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>


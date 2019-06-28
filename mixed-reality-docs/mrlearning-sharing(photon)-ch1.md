---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416117"
---
# <a name="setting-up-photon"></a><span data-ttu-id="3037d-104">Configurando Photon</span><span class="sxs-lookup"><span data-stu-id="3037d-104">Setting Up Photon</span></span>

<span data-ttu-id="3037d-105">Nesta lição, vamos aprenderá como se preparar para a criação de uma experiência de compartilhado com a importação de sistema de rede de Unity Photon (TROCADILHO) no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="3037d-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="3037d-106">Photon é uma das várias opções de rede disponíveis para desenvolvedores de realidade mista para criar experiências compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="3037d-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="3037d-107">Podemos, aprenderemos a criar uma conta de Photon, importar Photon e criar um servidor de local opcional</span><span class="sxs-lookup"><span data-stu-id="3037d-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="3037d-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="3037d-108">Objectives:</span></span>

* <span data-ttu-id="3037d-109">Saiba como criar conta Photon</span><span class="sxs-lookup"><span data-stu-id="3037d-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="3037d-110">Saiba como localizar e importar Photon Unity de rede</span><span class="sxs-lookup"><span data-stu-id="3037d-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="3037d-111">Configurar um servidor local do Photon</span><span class="sxs-lookup"><span data-stu-id="3037d-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="3037d-112">Configurando Photon</span><span class="sxs-lookup"><span data-stu-id="3037d-112">Setting Up Photon</span></span>

1. <span data-ttu-id="3037d-113">Configurar uma [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) conta.</span><span class="sxs-lookup"><span data-stu-id="3037d-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="3037d-114">Navegue até a página de inscrição Photon clicando em [esse link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="3037d-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="3037d-115">Siga as instruções na página de inscrição para criar a conta.</span><span class="sxs-lookup"><span data-stu-id="3037d-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="3037d-118">Crie uma ID de aplicativo clicando no botão "criar um novo aplicativo".</span><span class="sxs-lookup"><span data-stu-id="3037d-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="3037d-120">Selecione "Photon TROCADILHO" no menu suspenso em "tipo de photon".</span><span class="sxs-lookup"><span data-stu-id="3037d-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="3037d-121">Em seguida, dê a ele um nome, neste exemplo, podemos denominado "HoloLensPhotonProject".</span><span class="sxs-lookup"><span data-stu-id="3037d-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="3037d-122">Quando terminar, clique no botão "Criar".</span><span class="sxs-lookup"><span data-stu-id="3037d-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="3037d-124">Depois disso, retornar à página de seus aplicativos e você deverá ver algo semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="3037d-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="3037d-125">Clique na ID do aplicativo e copie-o.</span><span class="sxs-lookup"><span data-stu-id="3037d-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="3037d-126">Colar é em algum lugar, que você pode acessar facilmente.</span><span class="sxs-lookup"><span data-stu-id="3037d-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="3037d-128">Crie um novo projeto do unity e nomeie-a como "HLSharingProject".</span><span class="sxs-lookup"><span data-stu-id="3037d-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="3037d-129">Para obter instruções sobre como criar um novo projeto do Unity, consulte [seção de "Criar o projeto do Unity" Base do módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="3037d-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="3037d-130">Depois que o projeto é carregado, clique na guia "loja de ativos", conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="3037d-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="3037d-131">Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite "TROCADILHO" e selecione o ativo de "Photon TROCADILHO 2 - livre" nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="3037d-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="3037d-133">Baixe e importe este ativo ao pressionar os botões "Download" e "Importar".</span><span class="sxs-lookup"><span data-stu-id="3037d-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="3037d-135">Depois de Photon tiver concluído o processo de importação, o Assistente de trocadilho será exibido.</span><span class="sxs-lookup"><span data-stu-id="3037d-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="3037d-136">Levar a ID do aplicativo (que deve estar na sua área de transferência) da etapa 4 e cole-o na caixa de AppID e pressione o botão de "Projeto de instalação".</span><span class="sxs-lookup"><span data-stu-id="3037d-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="3037d-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="3037d-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="3037d-138">Depois de adicionar com êxito o AppID, navegue até "Photon"->"PhotonUnityNetworking" -> "Recursos" -> "PhotonServerSettings" em ativos.</span><span class="sxs-lookup"><span data-stu-id="3037d-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="3037d-139">Selecionar a opção "Usar servidor de nome" e defina a região fixa como "EUA" ou sua região do serviço photon.</span><span class="sxs-lookup"><span data-stu-id="3037d-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="3037d-141">Parabéns</span><span class="sxs-lookup"><span data-stu-id="3037d-141">Congratulations</span></span>

<span data-ttu-id="3037d-142">Com êxito ter criado uma conta de Photon, configurar um servidor local do Photon e importados TROCADILHO para Unity.</span><span class="sxs-lookup"><span data-stu-id="3037d-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="3037d-143">A próxima etapa é configurar o projeto e, em seguida, permitir conexões com outros usuários para que vários usuários podem ver seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="3037d-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="3037d-144">[Próxima lição: Sharing(Photon) lição 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="3037d-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>


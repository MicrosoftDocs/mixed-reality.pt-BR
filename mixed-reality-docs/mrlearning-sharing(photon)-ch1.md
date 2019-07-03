---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523293"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="f3096-104">Configuração de rede de Unity Photon</span><span class="sxs-lookup"><span data-stu-id="f3096-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="f3096-105">Neste tutorial, aprendemos como se preparar para a criação de uma experiência de compartilhado com a importação de sistema de rede de Unity Photon (TROCADILHO) no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="f3096-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="f3096-106">Photon é uma das várias opções de rede disponíveis para desenvolvedores de realidade mista para criar experiências compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="f3096-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="f3096-107">Podemos, aprenderemos a criar uma conta de Photon, importar Photon e criar um servidor de local opcional</span><span class="sxs-lookup"><span data-stu-id="f3096-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="f3096-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="f3096-108">Objectives:</span></span>

* <span data-ttu-id="f3096-109">Saiba como criar uma conta de Photon</span><span class="sxs-lookup"><span data-stu-id="f3096-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="f3096-110">Saiba como localizar e importar Photon Unity de rede</span><span class="sxs-lookup"><span data-stu-id="f3096-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="f3096-111">Configurar um servidor local do Photon</span><span class="sxs-lookup"><span data-stu-id="f3096-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="f3096-112">Configurando Photon</span><span class="sxs-lookup"><span data-stu-id="f3096-112">Setting up Photon</span></span>

1. <span data-ttu-id="f3096-113">Configurar uma [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) conta.</span><span class="sxs-lookup"><span data-stu-id="f3096-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="f3096-114">Navegue até a página de inscrição Photon clicando em [esse link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="f3096-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="f3096-115">Siga as instruções na página de inscrição para criar a conta.</span><span class="sxs-lookup"><span data-stu-id="f3096-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="f3096-118">Crie uma ID de aplicativo, clicando em criar um botão novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3096-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="f3096-120">Selecione o TROCADILHO Photon no menu suspenso em tipo Photon.</span><span class="sxs-lookup"><span data-stu-id="f3096-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="f3096-121">Em seguida, dê um nome.</span><span class="sxs-lookup"><span data-stu-id="f3096-121">Then give it a name.</span></span> <span data-ttu-id="f3096-122">Neste exemplo, nomeamos a ele HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="f3096-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="f3096-123">Quando terminar, clique no botão Criar.</span><span class="sxs-lookup"><span data-stu-id="f3096-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="f3096-125">Depois disso, retornar à página de seus aplicativos e você deverá ver algo semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="f3096-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="f3096-126">Clique na ID do aplicativo e copie-o.</span><span class="sxs-lookup"><span data-stu-id="f3096-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="f3096-127">Colar é em algum lugar, que você pode acessar facilmente.</span><span class="sxs-lookup"><span data-stu-id="f3096-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="f3096-129">Crie um novo projeto do unity e nomeie-a como HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="f3096-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="f3096-130">Para obter instruções sobre como criar um novo projeto do Unity, consulte [seção de "Criar o projeto do Unity" Base do módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="f3096-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="f3096-131">Depois que o projeto é carregado, clique na guia Store ativos, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="f3096-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="f3096-132">Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite TROCADILHO e selecione 2 o TROCADILHO Photon - FRE"ativo dos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="f3096-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="f3096-134">Baixe e importe este ativo ao pressionar os botões baixar e importar.</span><span class="sxs-lookup"><span data-stu-id="f3096-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="f3096-136">Depois de Photon tiver concluído o processo de importação, o Assistente de trocadilho é exibido.</span><span class="sxs-lookup"><span data-stu-id="f3096-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="f3096-137">Levar a ID do aplicativo (que deve estar na sua área de transferência) da etapa 4 e cole-o na caixa de AppID e pressione o botão de projeto de instalação.</span><span class="sxs-lookup"><span data-stu-id="f3096-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="f3096-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f3096-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="f3096-139">Depois de adicionar com êxito o AppID, navegue até Photon -> PhotonUnityNetworking -> recursos -> PhotonServerSettings em ativos.</span><span class="sxs-lookup"><span data-stu-id="f3096-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="f3096-140">Selecione a opção de usar o servidor de nome e defina a região fixa conosco ou a região do serviço yourPphoton.</span><span class="sxs-lookup"><span data-stu-id="f3096-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="f3096-142">Parabéns</span><span class="sxs-lookup"><span data-stu-id="f3096-142">Congratulations</span></span>

<span data-ttu-id="f3096-143">Com êxito ter criado uma conta de Photon, configurar um servidor local do Photon e importados TROCADILHO para Unity.</span><span class="sxs-lookup"><span data-stu-id="f3096-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="f3096-144">A próxima etapa é configurar o projeto e, em seguida, permitir conexões com outros usuários para que vários usuários podem ver seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="f3096-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="f3096-145">[Próximo tutorial: Preparando para o desenvolvimento do Unity](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="f3096-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>


---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327727"
---
# <a name="setting-up-photon"></a><span data-ttu-id="a4f62-104">Configurando Photon</span><span class="sxs-lookup"><span data-stu-id="a4f62-104">Setting Up Photon</span></span>

<span data-ttu-id="a4f62-105">Nesta lição, vamos aprenderá como se preparar para a criação de uma experiência de compartilhado com a importação de sistema de rede de Unity Photon (TROCADILHO) no projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="a4f62-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="a4f62-106">Photon é uma das várias opções de rede disponíveis para desenvolvedores de realidade mista para criar experiências compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="a4f62-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="a4f62-107">Podemos, aprenderemos a criar uma conta de Photon, importar Photon e criar um servidor de local opcional</span><span class="sxs-lookup"><span data-stu-id="a4f62-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="a4f62-108">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="a4f62-108">Objectives:</span></span>

* <span data-ttu-id="a4f62-109">Saiba como criar conta Photon</span><span class="sxs-lookup"><span data-stu-id="a4f62-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="a4f62-110">Saiba como localizar e importar Photon Unity de rede</span><span class="sxs-lookup"><span data-stu-id="a4f62-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="a4f62-111">Configurar um servidor local do Photon</span><span class="sxs-lookup"><span data-stu-id="a4f62-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="a4f62-112">Configurando Photon</span><span class="sxs-lookup"><span data-stu-id="a4f62-112">Setting Up Photon</span></span>

1. <span data-ttu-id="a4f62-113">Configurar uma [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) conta.</span><span class="sxs-lookup"><span data-stu-id="a4f62-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="a4f62-114">Navegue até a página de inscrição Photon clicando em [esse link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="a4f62-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="a4f62-115">Siga as instruções na página de inscrição para criar a conta.</span><span class="sxs-lookup"><span data-stu-id="a4f62-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="a4f62-117">Depois que você se inscreveu, clique em SDKs.</span><span class="sxs-lookup"><span data-stu-id="a4f62-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="a4f62-118">Quando você estiver nessa página, clique em "servidor" e faça a garantir que ela diz, "auto-hospedado."</span><span class="sxs-lookup"><span data-stu-id="a4f62-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="a4f62-119">Em seguida, role para baixo e clique em "servidor", como visto na segunda imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="a4f62-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="a4f62-122">Isso fará com que uma caixa de texto aparecer rotulados, "Leia-me".</span><span class="sxs-lookup"><span data-stu-id="a4f62-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="a4f62-123">Vá em frente e lê-lo.</span><span class="sxs-lookup"><span data-stu-id="a4f62-123">Go ahead and read it.</span></span> <span data-ttu-id="a4f62-124">Quando terminar, clique no link ao lado de "downloadSDK" para baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="a4f62-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="a4f62-126">Clique duas vezes na pasta após a conclusão do download.</span><span class="sxs-lookup"><span data-stu-id="a4f62-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="a4f62-127">Depois que o Explorador de arquivos é aberto, revelando a pasta do SDK, copie a pasta do SDK.</span><span class="sxs-lookup"><span data-stu-id="a4f62-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="a4f62-128">A próxima etapa seria ir na unidade c: windows e criar uma nova pasta chamada 'server'.</span><span class="sxs-lookup"><span data-stu-id="a4f62-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="a4f62-130">Agora abra a pasta e cole a pasta do SDK que você copiou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a4f62-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="a4f62-132">Após a conclusão, abra a pasta do SDK e vá para "implantar", em seguida, "bin_Win64", em seguida, clique duas vezes em "controle photon".</span><span class="sxs-lookup"><span data-stu-id="a4f62-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="a4f62-134">Observação: Se você tiver dúvidas sobre o endereço IP, ou quaisquer outras perguntas semelhantes, você pode encontrar a maior parte das suas informações na barra de ferramentas (conforme mostrado na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="a4f62-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="a4f62-136">Agora que o servidor está configurado e iniciado, volte para o site Photon e certifique-se de que você ainda está conectado (ou entre novamente, se você não estiver). Clique no ícone do perfil (demarcado no canto superior direito da imagem abaixo) e selecione "seus aplicativos".</span><span class="sxs-lookup"><span data-stu-id="a4f62-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="a4f62-138">Crie uma ID de aplicativo clicando no botão "criar um novo aplicativo".</span><span class="sxs-lookup"><span data-stu-id="a4f62-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="a4f62-140">Selecione "Photon TROCADILHO" no menu suspenso em "tipo de photon".</span><span class="sxs-lookup"><span data-stu-id="a4f62-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="a4f62-141">Em seguida, dê a ele um nome, neste exemplo, podemos denominado "HoloLensPhotonProject".</span><span class="sxs-lookup"><span data-stu-id="a4f62-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="a4f62-142">Quando terminar, clique no botão "Criar".</span><span class="sxs-lookup"><span data-stu-id="a4f62-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="a4f62-144">Depois disso, retornar à página de seus aplicativos e você deverá ver algo semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="a4f62-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="a4f62-145">Clique na ID do aplicativo e copie-o.</span><span class="sxs-lookup"><span data-stu-id="a4f62-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="a4f62-146">Colar é em algum lugar, que você pode acessar facilmente.</span><span class="sxs-lookup"><span data-stu-id="a4f62-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="a4f62-148">Crie um novo projeto do unity e nomeie-a como "HLSharingProject".</span><span class="sxs-lookup"><span data-stu-id="a4f62-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="a4f62-149">Para obter instruções sobre como criar um novo projeto do Unity, consulte [seção de "Criar o projeto do Unity" Base do módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="a4f62-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="a4f62-150">Depois que o projeto é carregado, clique na guia "loja de ativos", conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="a4f62-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="a4f62-151">Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite "TROCADILHO" e selecione o ativo "Photon TROCADILHO-2" gratuito"nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="a4f62-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="a4f62-153">Baixe e importe este ativo ao pressionar os botões "Download" e "Importar".</span><span class="sxs-lookup"><span data-stu-id="a4f62-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a4f62-155">Parabéns</span><span class="sxs-lookup"><span data-stu-id="a4f62-155">Congratulations</span></span>

<span data-ttu-id="a4f62-156">Com êxito ter criado uma conta de Photon, configurar um servidor local do Photon e importados TROCADILHO para Unity.</span><span class="sxs-lookup"><span data-stu-id="a4f62-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="a4f62-157">A próxima etapa é configurar o projeto e, em seguida, permitir conexões com outros usuários para que vários usuários podem ver seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="a4f62-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="a4f62-158">[Próxima lição: Sharing(Photon) lição 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="a4f62-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>


---
title: Módulo do ASA de aprendizado MR do Azure âncora espacial no HoloLens 2
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327978"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="8c38f-104">Photon (corrigir-me se eu estiver errado)</span><span class="sxs-lookup"><span data-stu-id="8c38f-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="8c38f-105">Nesta lição,</span><span class="sxs-lookup"><span data-stu-id="8c38f-105">In this lesson,</span></span> 

<span data-ttu-id="8c38f-106">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="8c38f-106">Objectives:</span></span>

* <span data-ttu-id="8c38f-107">Saiba como _</span><span class="sxs-lookup"><span data-stu-id="8c38f-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="8c38f-108">Saiba como _</span><span class="sxs-lookup"><span data-stu-id="8c38f-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="8c38f-109">Instruções</span><span class="sxs-lookup"><span data-stu-id="8c38f-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="8c38f-110">Configurando Photon</span><span class="sxs-lookup"><span data-stu-id="8c38f-110">Setting Up Photon</span></span>

1. <span data-ttu-id="8c38f-111">Configurar uma [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) conta.</span><span class="sxs-lookup"><span data-stu-id="8c38f-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="8c38f-112">Isso consistirá de entrada de seu email e passando por algumas etapas de verificação.</span><span class="sxs-lookup"><span data-stu-id="8c38f-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="8c38f-114">Depois que você se inscreveu, clique em SDKs.</span><span class="sxs-lookup"><span data-stu-id="8c38f-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="8c38f-115">Quando você estiver nessa página, clique em "servidor" e faça a garantir que ela diz, "auto-hospedado."</span><span class="sxs-lookup"><span data-stu-id="8c38f-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="8c38f-116">Em seguida, role para baixo e clique em "servidor", como visto na segunda imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="8c38f-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="8c38f-119">Isso fará com que uma caixa de texto aparecer rotulados, "Leia-me".</span><span class="sxs-lookup"><span data-stu-id="8c38f-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="8c38f-120">Vá em frente e lê-lo.</span><span class="sxs-lookup"><span data-stu-id="8c38f-120">Go ahead and read it.</span></span> <span data-ttu-id="8c38f-121">Quando terminar, clique no link ao lado de "downloadSDK" para baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="8c38f-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="8c38f-123">Clique duas vezes na pasta após a conclusão do download.</span><span class="sxs-lookup"><span data-stu-id="8c38f-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="8c38f-124">Depois que o Explorador de arquivos é aberto, revelando a pasta do SDK, copie a pasta do SDK.</span><span class="sxs-lookup"><span data-stu-id="8c38f-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="8c38f-125">A próxima etapa seria ir na unidade c: windows e criar uma nova pasta chamada 'server'.</span><span class="sxs-lookup"><span data-stu-id="8c38f-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="8c38f-127">Agora abra a pasta e cole a pasta do SDK que você copiou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8c38f-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="8c38f-129">Após a conclusão, abra a pasta do SDK e vá para "implantar", em seguida, "bin_Win64", em seguida, clique duas vezes em "controle photon".</span><span class="sxs-lookup"><span data-stu-id="8c38f-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="8c38f-131">Observação: Se você tiver dúvidas sobre o endereço IP, ou quaisquer outras perguntas semelhantes, você pode encontrar a maior parte das suas informações na barra de ferramentas (conforme mostrado na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="8c38f-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="8c38f-133">Agora que o servidor está configurado e iniciado, volte para o site Photon e clique no ícone do perfil (boxed na imagem abaixo) e selecione "seus aplicativos".</span><span class="sxs-lookup"><span data-stu-id="8c38f-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="8c38f-135">Crie uma ID de aplicativo clicando no botão "criar um novo aplicativo".</span><span class="sxs-lookup"><span data-stu-id="8c38f-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="8c38f-137">Selecione "Photon RUN" no menu suspenso em "tipo de photon".</span><span class="sxs-lookup"><span data-stu-id="8c38f-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="8c38f-138">Em seguida, dê a ele um nome, (algo que você deve se lembrar).</span><span class="sxs-lookup"><span data-stu-id="8c38f-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="8c38f-139">Neste exemplo, demos o nome "HoloLensPhotonProject".</span><span class="sxs-lookup"><span data-stu-id="8c38f-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="8c38f-140">Quando terminar, clique em "criar".</span><span class="sxs-lookup"><span data-stu-id="8c38f-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="8c38f-142">Depois disso, retornar à página de seus aplicativos e você deverá ver algo semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="8c38f-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="8c38f-143">Clique na ID do aplicativo e copie-o.</span><span class="sxs-lookup"><span data-stu-id="8c38f-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="8c38f-144">Colar é em algum lugar, que você pode acessar facilmente.</span><span class="sxs-lookup"><span data-stu-id="8c38f-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="8c38f-146">Crie um novo projeto do unity.</span><span class="sxs-lookup"><span data-stu-id="8c38f-146">Create a new unity project.</span></span> <span data-ttu-id="8c38f-147">Abra o Hub do Unity e clique em "nova".</span><span class="sxs-lookup"><span data-stu-id="8c38f-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="8c38f-148">Nomeie-a como "HLSharingProject".</span><span class="sxs-lookup"><span data-stu-id="8c38f-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="8c38f-149">Clique em criar.</span><span class="sxs-lookup"><span data-stu-id="8c38f-149">Then click create.</span></span> 

   > <span data-ttu-id="8c38f-150">Observação: Isso pode levar até 2 minutos para carregar, com base na velocidade do seu computador.</span><span class="sxs-lookup"><span data-stu-id="8c38f-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="8c38f-152">Observação: escolha um local para salvar seu projeto em seu computador, alterando a opção "local".</span><span class="sxs-lookup"><span data-stu-id="8c38f-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="8c38f-153">Salve-o em um lugar você lembrar e ter acesso fácil a.</span><span class="sxs-lookup"><span data-stu-id="8c38f-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="8c38f-154">Depois que o projeto é carregado, clique em "repositório de ativos".</span><span class="sxs-lookup"><span data-stu-id="8c38f-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="8c38f-155">Em seguida, na caixa de pesquisa mostrada na imagem abaixo, digite "TROCADILHO" e selecione o ativo "Photon TROCADILHO-2" gratuito".</span><span class="sxs-lookup"><span data-stu-id="8c38f-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="8c38f-157">Baixe e importe!</span><span class="sxs-lookup"><span data-stu-id="8c38f-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="8c38f-159">**Configurar o projeto do Unity**</span><span class="sxs-lookup"><span data-stu-id="8c38f-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="8c38f-160">Baixe um novo ativo necessário para configurar Photon no Unity clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="8c38f-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="8c38f-161">No Unity, clique no menu de ativos e selecione "Importar ativos", clique em "ativos personalizados".</span><span class="sxs-lookup"><span data-stu-id="8c38f-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="8c38f-163">Selecione o pacote do Unity que você acabou de baixar o link fornecido na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="8c38f-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="8c38f-164">Uma vez que aparece no botão Importar no Unity, clique nele.</span><span class="sxs-lookup"><span data-stu-id="8c38f-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="8c38f-166">Observação: sempre que você baixou o pacote será onde encontrá-lo.</span><span class="sxs-lookup"><span data-stu-id="8c38f-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="8c38f-167">A imagem acima não apresentação para onde você encontrará o pacote.</span><span class="sxs-lookup"><span data-stu-id="8c38f-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="8c38f-168">Criar uma nova cena (Isso pode ser feito usando o controle / command + N ou clicando em "file" e selecionando "nova cena.").</span><span class="sxs-lookup"><span data-stu-id="8c38f-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="8c38f-169">Salve a cena como "HLSharedProjectMain".</span><span class="sxs-lookup"><span data-stu-id="8c38f-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="8c38f-170">Observação: você pode receber um pop-up que é semelhante à imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="8c38f-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="8c38f-171">Por enquanto, basta clicar em "não".</span><span class="sxs-lookup"><span data-stu-id="8c38f-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="8c38f-173">Em, clique em "Toolkit de realidade mista" em "Adicionar à cena e configurar".</span><span class="sxs-lookup"><span data-stu-id="8c38f-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="8c38f-175">Assim que estiver concluído, um novo arquivo de configuração será exibida, oferecendo a opção para personalizar o perfil.</span><span class="sxs-lookup"><span data-stu-id="8c38f-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="8c38f-176">Clique em "copiar e personalizar."</span><span class="sxs-lookup"><span data-stu-id="8c38f-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="8c38f-178">Role para baixo e desmarque a opção "Habilitar sistema de diagnóstico".</span><span class="sxs-lookup"><span data-stu-id="8c38f-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="8c38f-179">Isso tornará mais fácil de configurar esse projeto.</span><span class="sxs-lookup"><span data-stu-id="8c38f-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="8c38f-181">Abra as configurações de compilação (controle + shift + B).</span><span class="sxs-lookup"><span data-stu-id="8c38f-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="8c38f-182">Observe que o programa está atualmente definido na plataforma "PC, Mac e Linux autônomo".</span><span class="sxs-lookup"><span data-stu-id="8c38f-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="8c38f-183">Para este projeto, defina a plataforma a ser "plataforma universal do windows".</span><span class="sxs-lookup"><span data-stu-id="8c38f-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="8c38f-184">Selecione-o e clique em "alternar plataforma".</span><span class="sxs-lookup"><span data-stu-id="8c38f-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="8c38f-186">Uma vez concluído, clique na caixa que diz "Adicionar cenas abertas".</span><span class="sxs-lookup"><span data-stu-id="8c38f-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="8c38f-187">Agora, vá para o painel do Inspetor e certifique-se de que a caixa de seleção à direita de "suportada de realidade virtual" (conforme mostrado na imagem abaixo) é verificada.</span><span class="sxs-lookup"><span data-stu-id="8c38f-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="8c38f-189">Observação: Certifique-se também de que a caixa de seleção ao lado de "cenas/HLSharedProjectMain" também é verificada.</span><span class="sxs-lookup"><span data-stu-id="8c38f-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="8c38f-190">Sob as "configurações de publicação" no painel Inspetor Role para baixo até "recursos" e certifique-se apenas as seguintes caixas de seleção são marcadas:</span><span class="sxs-lookup"><span data-stu-id="8c38f-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="8c38f-191">cliente da Internet</span><span class="sxs-lookup"><span data-stu-id="8c38f-191">internet client</span></span>
- <span data-ttu-id="8c38f-192">servidor de cliente da Internet</span><span class="sxs-lookup"><span data-stu-id="8c38f-192">internet client server</span></span>
- <span data-ttu-id="8c38f-193">servidor de cliente de rede privada</span><span class="sxs-lookup"><span data-stu-id="8c38f-193">private network client server</span></span>
- <span data-ttu-id="8c38f-194">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="8c38f-194">camera/webcam</span></span>
- <span data-ttu-id="8c38f-195">Microfone</span><span class="sxs-lookup"><span data-stu-id="8c38f-195">microphone</span></span>

21. <span data-ttu-id="8c38f-196">Assim como a etapa 12, a próxima etapa seria importar outro pacote personalizado chamado "Da lição 2", que pode ser baixado [aqui]. [link lesson2.unitypackage aqui] Importe o pacote.</span><span class="sxs-lookup"><span data-stu-id="8c38f-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="8c38f-198">Agora, no painel de projeto, vá para a pasta "pré-fabricados", já que nas próximas etapas você irá implementar alguns pré-fabricados na cena.</span><span class="sxs-lookup"><span data-stu-id="8c38f-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="8c38f-199">Na pasta "pré-fabricados", clique e arraste pré-fabricado, "DebugWindow" na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="8c38f-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="8c38f-200">Quando terminar, salve o projeto (clique em arquivo, em seguida, salvar, ou CTRL + S)</span><span class="sxs-lookup"><span data-stu-id="8c38f-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="8c38f-202">Observação: Você pode perceber um pop-up são exibidas à medida que você clicar no pré-fabricado, solicitando que você sobre o Essentials TMP.</span><span class="sxs-lookup"><span data-stu-id="8c38f-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="8c38f-203">Clique em "Importar TMP Essentials" como eles serão necessários.</span><span class="sxs-lookup"><span data-stu-id="8c38f-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="8c38f-205">**Conectar-se vários usuários**</span><span class="sxs-lookup"><span data-stu-id="8c38f-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="8c38f-206">Como na etapa 22, na pasta "pré-fabricados" no painel de projeto, a próxima etapa é arrastar e soltar "NetworkLobby" pré-fabricado na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="8c38f-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="8c38f-208">Quando você abrir pré-fabricado pai, "NetworkLobby", você deverá ver um filho pré-fabricado, "NetworkRoom".</span><span class="sxs-lookup"><span data-stu-id="8c38f-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="8c38f-209">Com ele selecionado, vá para o painel do Inspetor e clique em "Adicionar componente".</span><span class="sxs-lookup"><span data-stu-id="8c38f-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="8c38f-210">Pesquise "PhotonView" e adicione o componente.</span><span class="sxs-lookup"><span data-stu-id="8c38f-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="8c38f-212">Crie um novo objeto jogo vazio na hierarquia (botão direito do mouse na hierarquia e selecione "empty").</span><span class="sxs-lookup"><span data-stu-id="8c38f-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="8c38f-213">Verifique se o posicionamento é definido como x = 0, y = 0, z = 0 e nomear o objeto, "PhotonUser".</span><span class="sxs-lookup"><span data-stu-id="8c38f-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="8c38f-215">Parabéns</span><span class="sxs-lookup"><span data-stu-id="8c38f-215">Congratulations</span></span>




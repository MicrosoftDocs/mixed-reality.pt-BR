---
title: Módulo do ASA do Sr Learning âncora espacial do Azure no HoloLens 2
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 141aa90f2bf5d90527a0fe1e6a812c1ce56bd0eb
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437796"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="10299-104">Photon (corrigir-me se eu estiver errado)</span><span class="sxs-lookup"><span data-stu-id="10299-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="10299-105">Nesta lição,</span><span class="sxs-lookup"><span data-stu-id="10299-105">In this lesson,</span></span> 

<span data-ttu-id="10299-106">Seus</span><span class="sxs-lookup"><span data-stu-id="10299-106">Objectives:</span></span>

* <span data-ttu-id="10299-107">Saiba como _____________________________________________</span><span class="sxs-lookup"><span data-stu-id="10299-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="10299-108">Saiba como _________________________________________________</span><span class="sxs-lookup"><span data-stu-id="10299-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="10299-109">Instruções</span><span class="sxs-lookup"><span data-stu-id="10299-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="10299-110">Configurando o Photon</span><span class="sxs-lookup"><span data-stu-id="10299-110">Setting Up Photon</span></span>

1. <span data-ttu-id="10299-111">Configure uma conta do [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="10299-111">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="10299-112">Fazer isso consistirá em entrada seu email e passar por algumas etapas de verificação.</span><span class="sxs-lookup"><span data-stu-id="10299-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="10299-114">Depois de se inscrever, clique em SDKs.</span><span class="sxs-lookup"><span data-stu-id="10299-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="10299-115">Quando você estiver nessa página, clique em "servidor" e verifique se ele diz "auto-hospedado".</span><span class="sxs-lookup"><span data-stu-id="10299-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="10299-116">Em seguida, role para baixo e clique em "servidor", como visto na segunda imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="10299-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="10299-119">Isso fará com que uma caixa de texto apareça rotulada, "Leia-me".</span><span class="sxs-lookup"><span data-stu-id="10299-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="10299-120">Vá em frente e leia-o.</span><span class="sxs-lookup"><span data-stu-id="10299-120">Go ahead and read it.</span></span> <span data-ttu-id="10299-121">Quando terminar, clique no link ao lado de "downloadSDK" para baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="10299-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="10299-123">Clique duas vezes na pasta após a conclusão do download.</span><span class="sxs-lookup"><span data-stu-id="10299-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="10299-124">Quando o explorador de arquivos abrir revelar a pasta do SDK, copie a pasta do SDK.</span><span class="sxs-lookup"><span data-stu-id="10299-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="10299-125">A próxima etapa seria ir para a unidade C: do Windows e criar uma nova pasta chamada ' Server '.</span><span class="sxs-lookup"><span data-stu-id="10299-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="10299-127">Agora, abra a pasta e cole a pasta do SDK que você copiou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="10299-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="10299-129">Após a conclusão, abra a pasta do SDK e vá para "implantar", em seguida, "bin_Win64" e clique duas vezes em "controle Photon".</span><span class="sxs-lookup"><span data-stu-id="10299-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="10299-131">Observação: se você tiver alguma dúvida sobre o endereço IP ou outras perguntas semelhantes, poderá encontrar a maioria das suas informações na barra de ferramentas (conforme mostrado na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="10299-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="10299-133">Agora que o servidor está configurado e iniciado, volte para o site do photon e clique no ícone de perfil (na imagem abaixo) e selecione "seus aplicativos".</span><span class="sxs-lookup"><span data-stu-id="10299-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="10299-135">Crie uma ID de aplicativo clicando no botão "criar um novo aplicativo".</span><span class="sxs-lookup"><span data-stu-id="10299-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="10299-137">Selecione "Photon RUN" no menu suspenso em "Photon Type".</span><span class="sxs-lookup"><span data-stu-id="10299-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="10299-138">Em seguida, dê um nome a ele (algo que você se lembraria).</span><span class="sxs-lookup"><span data-stu-id="10299-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="10299-139">Neste exemplo, nomeamos "HoloLensPhotonProject".</span><span class="sxs-lookup"><span data-stu-id="10299-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="10299-140">Quando terminar, clique em "criar".</span><span class="sxs-lookup"><span data-stu-id="10299-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="10299-142">Depois disso, volte para a página de aplicativos e você verá algo semelhante à imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="10299-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="10299-143">Clique na ID do aplicativo e copie-a.</span><span class="sxs-lookup"><span data-stu-id="10299-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="10299-144">Colar é em algum lugar que você pode acessar facilmente.</span><span class="sxs-lookup"><span data-stu-id="10299-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="10299-146">Crie um novo projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="10299-146">Create a new unity project.</span></span> <span data-ttu-id="10299-147">Abra o Hub do Unity e clique em "novo".</span><span class="sxs-lookup"><span data-stu-id="10299-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="10299-148">Nomeie-o como "HLSharingProject".</span><span class="sxs-lookup"><span data-stu-id="10299-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="10299-149">Em seguida, clique em criar.</span><span class="sxs-lookup"><span data-stu-id="10299-149">Then click create.</span></span> 

   > <span data-ttu-id="10299-150">Observação: isso pode levar até 2 minutos para ser carregado, com base na velocidade do seu computador.</span><span class="sxs-lookup"><span data-stu-id="10299-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="10299-152">Observação: escolha um local para salvar o projeto em seu computador alterando a opção "local".</span><span class="sxs-lookup"><span data-stu-id="10299-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="10299-153">Salve-o em um lugar onde você se lembrará e terá acesso fácil ao.</span><span class="sxs-lookup"><span data-stu-id="10299-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="10299-154">Depois que o projeto for carregado, clique em "repositório de ativos".</span><span class="sxs-lookup"><span data-stu-id="10299-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="10299-155">Em seguida, na caixa de pesquisa mostrada na imagem abaixo, digite "trocadilho" e selecione o ativo "Photon trocadilho-2 FREE".</span><span class="sxs-lookup"><span data-stu-id="10299-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="10299-157">Baixe e importe!</span><span class="sxs-lookup"><span data-stu-id="10299-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="10299-159">**Configurando o projeto do Unity**</span><span class="sxs-lookup"><span data-stu-id="10299-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="10299-160">Baixe um novo ativo necessário para configurar o Photon no Unity clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="10299-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="10299-161">No Unity, clique no menu ativos e selecione "importar ativos" e clique em "ativos personalizados".</span><span class="sxs-lookup"><span data-stu-id="10299-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="10299-163">Selecione o pacote do Unity que você acabou de baixar do link fornecido na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="10299-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="10299-164">Depois que o botão importar aparecer no Unity, clique nele.</span><span class="sxs-lookup"><span data-stu-id="10299-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="10299-166">Observação: sempre que você baixou o pacote para será onde você o encontrará.</span><span class="sxs-lookup"><span data-stu-id="10299-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="10299-167">A imagem acima não retrata onde você encontrará o pacote.</span><span class="sxs-lookup"><span data-stu-id="10299-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="10299-168">Crie uma nova cena (isso pode ser feito usando o controle/comando + N ou clicando em "arquivo" e selecionando "nova cena.").</span><span class="sxs-lookup"><span data-stu-id="10299-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="10299-169">Salve a cena como "HLSharedProjectMain".</span><span class="sxs-lookup"><span data-stu-id="10299-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="10299-170">Observação: você pode receber um pop-up parecido com a imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="10299-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="10299-171">Por enquanto, basta clicar em "não".</span><span class="sxs-lookup"><span data-stu-id="10299-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="10299-173">Em "Mixed Reality Toolkit", clique em "adicionar à cena e configurar".</span><span class="sxs-lookup"><span data-stu-id="10299-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="10299-175">Quando isso for concluído, um novo arquivo de configuração será exibido, oferecendo a você a opção de personalizar o perfil.</span><span class="sxs-lookup"><span data-stu-id="10299-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="10299-176">Clique em "copiar e personalizar".</span><span class="sxs-lookup"><span data-stu-id="10299-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="10299-178">Role para baixo e desmarque "habilitar o sistema de diagnóstico".</span><span class="sxs-lookup"><span data-stu-id="10299-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="10299-179">Isso facilitará a configuração deste projeto.</span><span class="sxs-lookup"><span data-stu-id="10299-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="10299-181">Abra as configurações de compilação (Control + Shift + B).</span><span class="sxs-lookup"><span data-stu-id="10299-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="10299-182">Observe que o programa está definido atualmente na plataforma "PC, Mac e Linux standalone".</span><span class="sxs-lookup"><span data-stu-id="10299-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="10299-183">Para este projeto, defina a plataforma como "plataforma universal do Windows".</span><span class="sxs-lookup"><span data-stu-id="10299-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="10299-184">Selecione-o e clique em "alternar plataforma".</span><span class="sxs-lookup"><span data-stu-id="10299-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="10299-186">Após a conclusão, clique na caixa que diz "Adicionar cenas abertas".</span><span class="sxs-lookup"><span data-stu-id="10299-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="10299-187">Agora, acesse o painel Inspetor e verifique se a caixa de seleção à direita de "realidade virtual com suporte" (conforme mostrado na imagem abaixo) está marcada.</span><span class="sxs-lookup"><span data-stu-id="10299-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="10299-189">Observação: Verifique também se a caixa de seleção ao lado de "cenas/HLSharedProjectMain" também está marcada.</span><span class="sxs-lookup"><span data-stu-id="10299-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="10299-190">Em "configurações de publicação" no painel Inspetor, role para baixo até "recursos" e verifique se apenas as seguintes caixas de seleção estão marcadas:</span><span class="sxs-lookup"><span data-stu-id="10299-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="10299-191">cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="10299-191">internet client</span></span>
- <span data-ttu-id="10299-192">servidor de cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="10299-192">internet client server</span></span>
- <span data-ttu-id="10299-193">servidor de cliente de rede privada</span><span class="sxs-lookup"><span data-stu-id="10299-193">private network client server</span></span>
- <span data-ttu-id="10299-194">câmera/Webcam</span><span class="sxs-lookup"><span data-stu-id="10299-194">camera/webcam</span></span>
- <span data-ttu-id="10299-195">microfone</span><span class="sxs-lookup"><span data-stu-id="10299-195">microphone</span></span>

21. <span data-ttu-id="10299-196">Da mesma forma que a etapa 12, a próxima etapa seria importar outro pacote personalizado chamado "lição 2", que pode ser baixado [aqui.] [o link do lição 2. unitypackage é inserido aqui] Importe esse pacote.</span><span class="sxs-lookup"><span data-stu-id="10299-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="10299-198">Agora, no painel projeto, vá para a pasta "pré-fabricados", já que, nas próximas etapas, você implementará algumas pré-fabricados na cena.</span><span class="sxs-lookup"><span data-stu-id="10299-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="10299-199">Na pasta "pré-fabricados", clique e arraste o pré-fabricado, "DebugWindow" para a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="10299-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="10299-200">Quando terminar, salve o projeto (clique em arquivo, salvar ou controle + S)</span><span class="sxs-lookup"><span data-stu-id="10299-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="10299-202">Observação: você pode notar que um pop-up aparece ao clicar no pré-fabricado, solicitando-lhe informações sobre o TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="10299-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="10299-203">Clique em "importar os fundamentos do TMP", pois eles serão necessários.</span><span class="sxs-lookup"><span data-stu-id="10299-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="10299-205">**Conectando vários usuários**</span><span class="sxs-lookup"><span data-stu-id="10299-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="10299-206">Como a etapa 22, na pasta "pré-fabricados" no painel projeto, a próxima etapa é arrastar e soltar o pré-fabricado "NetworkLobby" na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="10299-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="10299-208">Quando você abrir o pré-fabricado pai, "NetworkLobby", verá um pré-fabricado filho, "NetworkRoom".</span><span class="sxs-lookup"><span data-stu-id="10299-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="10299-209">Com ele selecionado, vá para o painel Inspetor e clique em "Adicionar componente".</span><span class="sxs-lookup"><span data-stu-id="10299-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="10299-210">Pesquise por "PhotonView" e adicione o componente.</span><span class="sxs-lookup"><span data-stu-id="10299-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="10299-212">Crie um novo objeto de jogo vazio na hierarquia (clique com o botão direito do mouse na hierarquia e selecione "vazio").</span><span class="sxs-lookup"><span data-stu-id="10299-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="10299-213">Verifique se o posicionamento está definido como x = 0, y = 0, z = 0 e nomeie o objeto "PhotonUser".</span><span class="sxs-lookup"><span data-stu-id="10299-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="10299-215">Parabéns</span><span class="sxs-lookup"><span data-stu-id="10299-215">Congratulations</span></span>




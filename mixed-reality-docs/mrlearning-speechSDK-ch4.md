---
title: TUTORIAIS dos serviços de fala do Azure-4. Configurando a intenção e a compreensão do idioma natural
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: e712fc2fd66b1add5b16b7dd8e6c37551aefe43a
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003205"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="222da-105">4. Configurando o reconhecimento de intenções e idiomas naturais</span><span class="sxs-lookup"><span data-stu-id="222da-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="222da-106">Nesta lição, você vai explorar o recurso de intenção do serviço de fala do Azure.</span><span class="sxs-lookup"><span data-stu-id="222da-106">In this lesson, you will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="222da-107">O recurso de intenção permite que você equipate nosso aplicativo com comandos de voz alimentados por ia, onde os usuários podem dizer comandos de voz não específicos e ainda têm sua intenção compreendida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="222da-107">The Intent feature allows you to equip our application with AI-powered voice commands, where users can say non-specific voice commands and still have their intent understood by the system.</span></span> <span data-ttu-id="222da-108">Durante esta lição, vamos configurar nosso portal de LUIS do Azure, configurar nossa intenção/entidades/declarações, publicar nosso recurso de intenção, conectar nosso aplicativo do Unity ao nosso recurso de intenção e fazer nossa primeira chamada à API de nossa intenção.</span><span class="sxs-lookup"><span data-stu-id="222da-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="222da-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="222da-109">Objectives</span></span>

- <span data-ttu-id="222da-110">Saiba como configurar o reconhecimento de intenções e de idioma natural em nosso aplicativo</span><span class="sxs-lookup"><span data-stu-id="222da-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="222da-111">Saiba como configurar o portal LUIS do Azure</span><span class="sxs-lookup"><span data-stu-id="222da-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="222da-112">Saiba como configurar intenção, entidades e declarações no Azure</span><span class="sxs-lookup"><span data-stu-id="222da-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="222da-113">Instruções</span><span class="sxs-lookup"><span data-stu-id="222da-113">Instructions</span></span>

1. <span data-ttu-id="222da-114">Permitir que seu computador habilite o ditado.</span><span class="sxs-lookup"><span data-stu-id="222da-114">Allow your machine to enable Dictation.</span></span> <span data-ttu-id="222da-115">Para fazer isso, vá para configurações do Windows, selecione "privacidade", em seguida, "fala", seguido por "escrita à tinta & digitação" e ative os serviços de fala e as sugestões de digitação.</span><span class="sxs-lookup"><span data-stu-id="222da-115">To do this, go to Windows Settings, select "privacy," then "speech," followed by "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="222da-119">Faça logon no [portal do Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="222da-119">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="222da-120">Depois de fazer logon, clique em criar um recurso, pesquise por "Reconhecimento vocal" e clique em Enter.</span><span class="sxs-lookup"><span data-stu-id="222da-120">Once you are logged in, click on Create a resource, search for "Language Understanding" and click Enter.</span></span>

    ![mrlearning-Speech-CH4-1-Step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="222da-122">Clique no botão **criar** para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="222da-122">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="222da-124">Dê um **nome**a seu recurso, por exemplo, *fala-SDK-Learning-Module*.</span><span class="sxs-lookup"><span data-stu-id="222da-124">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="222da-125">Para **assinatura**, selecione *pagamento conforme o uso* ou *trilha gratuita* se você tiver uma conta de avaliação.</span><span class="sxs-lookup"><span data-stu-id="222da-125">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="222da-126">Em seguida, crie um novo **grupo de recursos** clicando no link **criar novo** , insira um nome, por exemplo, *HoloLens-2-tutoriais-Resource-Group*e clique no botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="222da-126">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and click the **OK** button.</span></span>

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="222da-128">Selecione o **local de criação** e o **local do tempo de execução**.</span><span class="sxs-lookup"><span data-stu-id="222da-128">Select your **Authoring location** and **Runtime location**.</span></span> <span data-ttu-id="222da-129">Para fins deste tutorial, use *(EUA) oeste dos EUA*e, em seguida, escolha *F0 (5 chamadas por segundo, 10K chamadas por mês)* para o **tipo de preço de criação** e tipo de preço de tempo de **execução**.</span><span class="sxs-lookup"><span data-stu-id="222da-129">For the purpose of this tutorial, use *(US) West US*, then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="222da-130">Por fim, clique no botão **criar** para criar o recurso, bem como o novo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="222da-130">Finally, click the **Create** button to create the resource, as well as the new resource group.</span></span>

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="222da-132">Depois de clicar no botão criar, você precisará aguardar até que o serviço seja criado, o que pode levar alguns minutos.</span><span class="sxs-lookup"><span data-stu-id="222da-132">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

5. <span data-ttu-id="222da-133">Depois que o processo de criação de recursos for concluído, você verá a mensagem **sua implantação está concluída**.</span><span class="sxs-lookup"><span data-stu-id="222da-133">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-Speech-CH4-1-Step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="222da-135">Usando a mesma conta de usuário, entre no portal do [Luis (serviço inteligente reconhecimento vocal)](https://www.luis.ai/) , selecione seu país e concorde com os termos de uso.</span><span class="sxs-lookup"><span data-stu-id="222da-135">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="222da-136">Ao acessar o portal de Reconhecimento vocal, talvez seja necessário fazer logon, se você ainda não tiver, com as mesmas credenciais que o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="222da-136">Upon reaching the Language Understanding portal, you may need to log in, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="222da-137">Se esta for a primeira vez que você usa o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vindas para localizar e clicar no botão "criar LUIS" do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="222da-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the Welcome page to find and click the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="222da-138">Depois de conectado, clique em meus aplicativos (se você ainda não estiver nesta seção).</span><span class="sxs-lookup"><span data-stu-id="222da-138">Once logged in, click My Apps (if you are not currently in that section).</span></span> <span data-ttu-id="222da-139">Em seguida, você pode clicar em criar novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="222da-139">You can then click on Create new app.</span></span> <span data-ttu-id="222da-140">Nomeie o novo aplicativo "módulo de aprendizagem SDK de fala".</span><span class="sxs-lookup"><span data-stu-id="222da-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="222da-141">Adicione "módulo de aprendizagem do SDK de fala" ao campo de descrição também.</span><span class="sxs-lookup"><span data-stu-id="222da-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="222da-142">Em seguida, clique em "concluído".</span><span class="sxs-lookup"><span data-stu-id="222da-142">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="222da-145">Se seu aplicativo deve entender uma linguagem diferente do inglês, você deve alterar a "cultura" para o idioma apropriado.</span><span class="sxs-lookup"><span data-stu-id="222da-145">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="222da-146">Clique em "Compilar" localizado no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="222da-146">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="222da-147">Em ativos do aplicativo à esquerda, selecione "intenções" e, em seguida, clique em "criar nova tentativa" e nomeie-o como "PressButton".</span><span class="sxs-lookup"><span data-stu-id="222da-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="222da-149">É importante usar os nomes de intenções e entidades usadas neste tutorial porque o aplicativo Lunarcom fará referência a eles por nome.</span><span class="sxs-lookup"><span data-stu-id="222da-149">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="222da-150">Agora você deve ter duas intenções – "PressButton" e "None".</span><span class="sxs-lookup"><span data-stu-id="222da-150">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="222da-151">Em ativos do aplicativo à esquerda, selecione "entidades", clique em "criar nova entidade", nomeie-a como "ação" e mantenha o tipo de entidade como "simples".</span><span class="sxs-lookup"><span data-stu-id="222da-151">Under App Assets on the left, select “Entities”, click “Create New Entity”, name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="222da-153">Clique em "criar nova entidade" novamente e nomeie-a como "destino".</span><span class="sxs-lookup"><span data-stu-id="222da-153">Click “Create New Entity” again and name it “Target”.</span></span> <span data-ttu-id="222da-154">Mantenha o tipo de entidade como "simples" também.</span><span class="sxs-lookup"><span data-stu-id="222da-154">Keep the Entity Type as “Simple”, as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="222da-156">Em ativos do aplicativo à esquerda, selecione "intenções" e clique na intenção de "PressButton" que você criou na etapa 10.</span><span class="sxs-lookup"><span data-stu-id="222da-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="222da-158">Clique na lista suspensa "opções de exibição" à direita e selecione "mostrar valores de entidade".</span><span class="sxs-lookup"><span data-stu-id="222da-158">Click the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="222da-160">Clique no botão "inserir um exemplo..."</span><span class="sxs-lookup"><span data-stu-id="222da-160">Click the “Enter an example…”</span></span> <span data-ttu-id="222da-161">.</span><span class="sxs-lookup"><span data-stu-id="222da-161">textbox.</span></span> <span data-ttu-id="222da-162">Em seguida, insira o seguinte declarações:</span><span class="sxs-lookup"><span data-stu-id="222da-162">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="222da-164">Clique na lista suspensa "opções de exibição" à direita e selecione "mostrar nomes de entidade".</span><span class="sxs-lookup"><span data-stu-id="222da-164">Click the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="222da-166">Verifique se cada um dos 10 declarações tem os seguintes rótulos de entidade nos seguintes lugares em 1.) clicando em palavras que são rotuladas e, no pop-up, selecionando "remover rótulo" e 2.) clicando em palavras que devem ser rotuladas e, no pop-up, selecionando o rótulo apropriado.</span><span class="sxs-lookup"><span data-stu-id="222da-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="222da-168">Agora, para publicar o modelo, clique em "treinar" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="222da-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="222da-169">Em seguida, depois de concluir o processamento, clique em "testar" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="222da-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="222da-171">Insira "Selecione o botão Iniciar" na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="222da-171">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="222da-172">Não adicionamos "Select" como uma ação em qualquer um de nossos declarações, mas se você clicar em "inspecionar", o modelo reconheceu "Select" como uma entidade de ação.</span><span class="sxs-lookup"><span data-stu-id="222da-172">We did not add “select” as an action in any of our Utterances, but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="222da-174">Clique em "publicar" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="222da-174">Click "publish" in the top right.</span></span> <span data-ttu-id="222da-175">Verifique se o menu suspenso diz "produção" e clique em "publicar" também no pop-up.</span><span class="sxs-lookup"><span data-stu-id="222da-175">Ensure the dropdown says “Production” and click "publish" on the popup, as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="222da-177">Depois de publicado, uma barra verde deve aparecer na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="222da-177">Once published, a green bar should appear at the top of the page.</span></span> <span data-ttu-id="222da-178">Clique na barra verde para exibir a página "gerenciar".</span><span class="sxs-lookup"><span data-stu-id="222da-178">Click the green bar to view the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="222da-180">Clique em "chaves e pontos de extremidade" em "configurações do aplicativo" à esquerda.</span><span class="sxs-lookup"><span data-stu-id="222da-180">Click "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="222da-181">Em seguida, defina a lista suspensa "publicar em" como "produção".</span><span class="sxs-lookup"><span data-stu-id="222da-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="222da-182">Defina o fuso horário para corresponder ao seu e marque a caixa para incluir todas as pontuações de intenção prevista.</span><span class="sxs-lookup"><span data-stu-id="222da-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="222da-183">Por fim, clique em "atribuir recurso".</span><span class="sxs-lookup"><span data-stu-id="222da-183">Lastly, click "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="222da-185">Selecione locatário na primeira lista suspensa e selecione "pré-pago" na lista suspensa nome da assinatura.</span><span class="sxs-lookup"><span data-stu-id="222da-185">Select tenant from the first dropdown and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="222da-186">Em nome do recurso LUIS, escolha o recurso que criamos acima nas etapas 1-5.</span><span class="sxs-lookup"><span data-stu-id="222da-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="222da-187">Em seguida, clique em "atribuir recurso".</span><span class="sxs-lookup"><span data-stu-id="222da-187">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="222da-189">Certifique-se de copiar e salvar a URL do ponto de extremidade associada ao recurso que acabamos de atribuir, para que seja facilmente acessível para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="222da-189">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="222da-190">Para o nome do locatário, coloque sua corporação ou perfil que você criou para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="222da-190">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="222da-191">Agora, abra o novo aplicativo no Unity e selecione o objeto Lunarcom_Base na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="222da-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="222da-192">Clique em "Adicionar componente" no painel Inspetor e procure e selecione "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="222da-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="222da-194">No campo ponto de extremidade Luis do "LunarcomIntentRecognizer" no painel Inspetor, insira a URL do ponto de extremidade que você salvou na etapa 22.</span><span class="sxs-lookup"><span data-stu-id="222da-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="222da-196">No componente "LunarcomOfflineRecognizer" no painel Inspetor, certifique-se de que "Desabilitar" esteja selecionado para "SimulateOfflineMode" caso contrário, o teste do programa não funcionará.</span><span class="sxs-lookup"><span data-stu-id="222da-196">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="222da-197">Pressione o botão reproduzir no editor do Unity e clique no botão Rocket para iniciar o reconhecimento de intenção.</span><span class="sxs-lookup"><span data-stu-id="222da-197">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="222da-198">Com a frase "Selecione o botão iniciar Rocket".</span><span class="sxs-lookup"><span data-stu-id="222da-198">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="222da-199">O aplicativo reconheceu a função desejada e ativou o botão Rocket.</span><span class="sxs-lookup"><span data-stu-id="222da-199">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="222da-201">Parabéns</span><span class="sxs-lookup"><span data-stu-id="222da-201">Congratulations</span></span>

<span data-ttu-id="222da-202">Nesta lição, você aprendeu a adicionar comandos de fala baseados em ia.</span><span class="sxs-lookup"><span data-stu-id="222da-202">In this lesson, you learned how to add AI-powered speech commands.</span></span> <span data-ttu-id="222da-203">Agora seu programa pode reconhecer a intenção dos usuários, mesmo que eles não excedam comandos de voz precisos!</span><span class="sxs-lookup"><span data-stu-id="222da-203">Now your program can recognize users' intent, even if they do not utter precise voice commands!</span></span>

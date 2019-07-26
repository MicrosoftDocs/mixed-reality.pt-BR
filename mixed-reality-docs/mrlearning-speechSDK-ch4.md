---
title: Módulo Sr Learning SpeechSDK – reconhecimento de fala e transcrição
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485784"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="f4402-104">4. Configurando a intenção e a compreensão do idioma natural</span><span class="sxs-lookup"><span data-stu-id="f4402-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="f4402-105">Nesta lição, exploraremos o recurso de intenção do serviço de fala do Azure.</span><span class="sxs-lookup"><span data-stu-id="f4402-105">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="f4402-106">O recurso de intenção nos permite equipar nosso aplicativo com comandos de voz alimentados por ia, onde os usuários podem dizer comandos de voz não específicos e ainda ter sua intenção compreendida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="f4402-106">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="f4402-107">Durante esta lição, vamos configurar nosso portal de LUIS do Azure, configurar nossa intenção/entidades/declarações, publicar nosso recurso de intenção, conectar nosso aplicativo do Unity ao nosso recurso de intenção e fazer nossa primeira chamada à API de nossa intenção.</span><span class="sxs-lookup"><span data-stu-id="f4402-107">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="f4402-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f4402-108">Objectives</span></span>

- <span data-ttu-id="f4402-109">Saiba como configurar o reconhecimento de intenções e de idioma natural em nosso aplicativo</span><span class="sxs-lookup"><span data-stu-id="f4402-109">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="f4402-110">Saiba como configurar o portal LUIS do Azure</span><span class="sxs-lookup"><span data-stu-id="f4402-110">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="f4402-111">Saiba como configurar intenção, entidades e declarações no Azure</span><span class="sxs-lookup"><span data-stu-id="f4402-111">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="f4402-112">Instruções</span><span class="sxs-lookup"><span data-stu-id="f4402-112">Instructions</span></span>
1. <span data-ttu-id="f4402-113">Permitir que seu computador habilite o ditado, vá para configurações do Windows, selecione "privacidade", depois "fala" e, finalmente, "escrita à tinta & digitação" e ative os serviços de fala e as sugestões de digitação.</span><span class="sxs-lookup"><span data-stu-id="f4402-113">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="f4402-117">Faça logon no [portal do Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="f4402-117">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="f4402-118">Depois de fazer logon, clique em criar um recurso e pesquise por "Reconhecimento vocal" e clique em Enter.</span><span class="sxs-lookup"><span data-stu-id="f4402-118">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="f4402-120">Selecione o botão criar para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="f4402-120">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="f4402-121">Nomeie seu projeto como "Speech_SDK_Learning_Module" e selecione "pré-pago".</span><span class="sxs-lookup"><span data-stu-id="f4402-121">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="f4402-124">Selecione sua região.</span><span class="sxs-lookup"><span data-stu-id="f4402-124">Select your Region.</span></span>  <span data-ttu-id="f4402-125">Para fins deste tutorial, selecione "(EUA) oeste dos EUA".</span><span class="sxs-lookup"><span data-stu-id="f4402-125">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="f4402-126">Em seguida, escolha "F0" para o tipo de preço.</span><span class="sxs-lookup"><span data-stu-id="f4402-126">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="f4402-127">Agora, clique em "criar" (localizado no canto inferior esquerdo) para criar o recurso.</span><span class="sxs-lookup"><span data-stu-id="f4402-127">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="f4402-128">Observação: depois de clicar em "criar", você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="f4402-128">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="f4402-129">Uma notificação será exibida no portal assim que o recurso for criado.</span><span class="sxs-lookup"><span data-stu-id="f4402-129">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="f4402-130">Clique nessa notificação e selecione "ir para o recurso".</span><span class="sxs-lookup"><span data-stu-id="f4402-130">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="f4402-131">Na página "Início Rápido" do serviço "API do LUIS", navegue até a primeira etapa, pegue suas "chaves" e clique em "chaves" (você também pode conseguir isso clicando no hiperlink azul "chaves", mostrado na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="f4402-131">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="f4402-132">Isso revelará seu serviço, "chaves".</span><span class="sxs-lookup"><span data-stu-id="f4402-132">This will reveal your service, "Keys."</span></span> <span data-ttu-id="f4402-133">Salve uma cópia de uma das chaves para que você possa usá-la posteriormente no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f4402-133">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="f4402-135">De volta à página "Início Rápido" na seção 2B, clique em "portal de Reconhecimento vocal" (mostrado na imagem acima) para ser redirecionado para a página da Web que você usará para criar seu novo serviço, dentro do aplicativo LUIS.</span><span class="sxs-lookup"><span data-stu-id="f4402-135">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="f4402-136">Observação: Ao atingir o "portal de Reconhecimento vocal", talvez seja necessário fazer logon, se você ainda não tiver, com as mesmas credenciais do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="f4402-136">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="f4402-137">Se esta for a primeira vez que você usa o LUIS, você precisará rolar para baixo até a parte inferior da página de boas-vindas, para localizar e clicar no botão "criar LUIS" do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f4402-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="f4402-138">Depois de conectado, clique em meus aplicativos (se você não estiver na seção no momento).</span><span class="sxs-lookup"><span data-stu-id="f4402-138">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="f4402-139">Em seguida, você pode clicar em criar novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f4402-139">You can then click on Create new app.</span></span> <span data-ttu-id="f4402-140">Nomeie o novo aplicativo "módulo de aprendizagem SDK de fala".</span><span class="sxs-lookup"><span data-stu-id="f4402-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="f4402-141">Adicione "módulo de aprendizagem do SDK de fala" ao campo de descrição também.</span><span class="sxs-lookup"><span data-stu-id="f4402-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="f4402-142">Em seguida, clique em "concluído".</span><span class="sxs-lookup"><span data-stu-id="f4402-142">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="f4402-145">anotações Se seu aplicativo deve entender uma linguagem diferente do inglês, você deve alterar a "cultura" para o idioma apropriado.</span><span class="sxs-lookup"><span data-stu-id="f4402-145">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="f4402-146">Clique em "Compilar" localizado no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="f4402-146">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="f4402-147">Em ativos do aplicativo à esquerda, selecione "intenções" e, em seguida, clique em "criar nova tentativa" e nomeie-o como "PressButton".</span><span class="sxs-lookup"><span data-stu-id="f4402-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="f4402-149">Observação: É importante usar os nomes de intenções e entidades usadas neste tutorial porque o aplicativo Lunarcom fará referência a eles por nome.</span><span class="sxs-lookup"><span data-stu-id="f4402-149">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="f4402-150">Observação: agora você deve ter duas intenções – "PressButton" e "None".</span><span class="sxs-lookup"><span data-stu-id="f4402-150">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="f4402-151">Em ativos do aplicativo à esquerda, selecione "entidades" e clique em "criar nova entidade" e nomeie-a como "ação" e mantenha o tipo de entidade como "simples".</span><span class="sxs-lookup"><span data-stu-id="f4402-151">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="f4402-153">Clique em "criar nova entidade" novamente e nomeie-a como "destino" e mantenha o tipo de entidade como "simples" também.</span><span class="sxs-lookup"><span data-stu-id="f4402-153">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="f4402-155">Em ativos do aplicativo à esquerda, selecione "intenções" e clique na intenção de "PressButton" que você criou na etapa 10.</span><span class="sxs-lookup"><span data-stu-id="f4402-155">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="f4402-157">Clique na lista suspensa "opções de exibição" à direita e selecione "mostrar valores de entidade".</span><span class="sxs-lookup"><span data-stu-id="f4402-157">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="f4402-159">Clique no botão "inserir um exemplo..."</span><span class="sxs-lookup"><span data-stu-id="f4402-159">Click on the “Enter an example…”</span></span> <span data-ttu-id="f4402-160">texto.</span><span class="sxs-lookup"><span data-stu-id="f4402-160">textbox.</span></span> <span data-ttu-id="f4402-161">Em seguida, insira o seguinte declarações:</span><span class="sxs-lookup"><span data-stu-id="f4402-161">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="f4402-163">Clique na lista suspensa "opções de exibição" à direita e selecione "mostrar nomes de entidade".</span><span class="sxs-lookup"><span data-stu-id="f4402-163">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="f4402-165">Verifique se cada um dos 10 declarações tem os seguintes rótulos de entidade nos seguintes lugares em 1.) clicando em palavras que são rotuladas e, no pop-up, selecionando "remover rótulo" e 2.) clicando em palavras que devem ser rotuladas e, no pop-up, selecionando o rótulo apropriado.</span><span class="sxs-lookup"><span data-stu-id="f4402-165">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="f4402-167">Agora, para publicar o modelo, clique em "treinar" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="f4402-167">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="f4402-168">Em seguida, depois de concluir o processamento, clique em "testar" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="f4402-168">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="f4402-170">Insira "Selecione o botão Iniciar" na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="f4402-170">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="f4402-171">Observação: não adicionamos "Select" como uma ação em qualquer um de nossos declarações-mas se você clicar em "inspecionar", o modelo reconheceu "Select" como uma entidade de ação.</span><span class="sxs-lookup"><span data-stu-id="f4402-171">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="f4402-173">Agora, clique em "publicar" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="f4402-173">Now, click "publish" in the top right.</span></span> <span data-ttu-id="f4402-174">Verifique se o menu suspenso diz "produção" e clique em "publicar" também no pop-up.</span><span class="sxs-lookup"><span data-stu-id="f4402-174">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="f4402-176">Depois de publicado, uma barra verde deve aparecer na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="f4402-176">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="f4402-177">Clique na barra verde a ser levada para a página "gerenciar".</span><span class="sxs-lookup"><span data-stu-id="f4402-177">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="f4402-179">Clique em "chaves e pontos de extremidade" em "configurações do aplicativo" à esquerda.</span><span class="sxs-lookup"><span data-stu-id="f4402-179">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="f4402-180">Em seguida, defina a lista suspensa "publicar em" como "produção".</span><span class="sxs-lookup"><span data-stu-id="f4402-180">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="f4402-181">Defina o fuso horário para corresponder ao seu e marque a caixa para incluir todas as pontuações de intenção prevista.</span><span class="sxs-lookup"><span data-stu-id="f4402-181">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="f4402-182">Por fim, clique em "atribuir recurso".</span><span class="sxs-lookup"><span data-stu-id="f4402-182">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="f4402-184">Selecione locatário na primeira lista suspensa e selecione "pré-pago" na lista suspensa nome da assinatura.</span><span class="sxs-lookup"><span data-stu-id="f4402-184">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="f4402-185">Em nome do recurso LUIS, escolha o recurso que criamos acima nas etapas 1-5.</span><span class="sxs-lookup"><span data-stu-id="f4402-185">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="f4402-186">Em seguida, clique em "atribuir recurso".</span><span class="sxs-lookup"><span data-stu-id="f4402-186">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="f4402-188">Observação: Certifique-se de copiar e salvar a URL do ponto de extremidade associada ao recurso que acabamos de atribuir para que ele seja facilmente acessível para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="f4402-188">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="f4402-189">Observação: Para o nome do locatário, coloque sua corporação ou perfil que você criou para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f4402-189">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="f4402-190">Agora, abra o novo aplicativo no Unity e selecione o objeto Lunarcom_Base na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="f4402-190">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="f4402-191">Clique em "Adicionar componente" no painel Inspetor e procure e selecione "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="f4402-191">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="f4402-193">No campo ponto de extremidade Luis do "LunarcomIntentRecognizer" no painel Inspetor, insira a URL do ponto de extremidade que você salvou na etapa 22.</span><span class="sxs-lookup"><span data-stu-id="f4402-193">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="f4402-195">Observação: No componente "LunarcomOfflineRecognizer" no painel Inspetor, certifique-se de que "Desabilitar" esteja selecionado para "SimulateOfflineMode" caso contrário, o teste do programa não funcionará.</span><span class="sxs-lookup"><span data-stu-id="f4402-195">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="f4402-196">Pressione o botão reproduzir no editor do Unity e clique no botão Rocket para iniciar o reconhecimento de intenção.</span><span class="sxs-lookup"><span data-stu-id="f4402-196">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="f4402-197">Com a frase "Selecione o botão iniciar Rocket".</span><span class="sxs-lookup"><span data-stu-id="f4402-197">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="f4402-198">Observação: O aplicativo reconheceu a função desejada e ativou o botão Rocket.</span><span class="sxs-lookup"><span data-stu-id="f4402-198">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="f4402-200">Parabéns</span><span class="sxs-lookup"><span data-stu-id="f4402-200">Congratulations</span></span>

<span data-ttu-id="f4402-201">Nesta lição, aprendemos como adicionar comandos de fala baseados em ia!</span><span class="sxs-lookup"><span data-stu-id="f4402-201">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="f4402-202">Agora, seu programa pode reconhecer a intenção dos usuários mesmo que eles não excedam comandos de voz precisos.</span><span class="sxs-lookup"><span data-stu-id="f4402-202">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>


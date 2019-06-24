## <a name="lesson-4"></a><span data-ttu-id="99b2a-101">Lição 4</span><span class="sxs-lookup"><span data-stu-id="99b2a-101">Lesson 4</span></span>

<span data-ttu-id="99b2a-102">Capítulo 4, vamos explorar o recurso de intenção de serviços de fala.</span><span class="sxs-lookup"><span data-stu-id="99b2a-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="99b2a-103">Nos conectamos irá configurar nosso Portal de LUIS do Azure, nossa intenção/entidades/declarações de instalação, publicar nosso recurso de intenção, nosso aplicativo Unity para nosso recurso de intenção e tornar nossa primeira chamada à API de intenção.</span><span class="sxs-lookup"><span data-stu-id="99b2a-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="99b2a-104">Permitir que seu computador habilitar o ditado, para fazer isso, vá para configurações do Windows, selecione "Privacidade", em seguida, "fala" e finalmente "escrita à tinta & digitando" e ative os serviços de fala e sugestões de digitação.</span><span class="sxs-lookup"><span data-stu-id="99b2a-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="99b2a-108">Observação: para obter informações sobre como fazer isso em um Mac/Macbook, clique em [aqui](linkgoeshere).</span><span class="sxs-lookup"><span data-stu-id="99b2a-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="99b2a-109">Faça logon na [Portal do Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="99b2a-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="99b2a-110">Quando você estiver conectado, clique em criar um recurso e pesquise por "Reconhecimento vocal" e clique em enter.</span><span class="sxs-lookup"><span data-stu-id="99b2a-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="99b2a-112">Selecione o botão Criar, para criar uma instância desse serviço.</span><span class="sxs-lookup"><span data-stu-id="99b2a-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="99b2a-113">Nomeie o projeto "Speech_SDK_Learning_Module" e selecione "Pago conforme o uso."</span><span class="sxs-lookup"><span data-stu-id="99b2a-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="99b2a-116">Selecione sua região.</span><span class="sxs-lookup"><span data-stu-id="99b2a-116">Select your Region.</span></span>  <span data-ttu-id="99b2a-117">Para fins deste tutorial, selecione "(EUA) Oeste dos EUA".</span><span class="sxs-lookup"><span data-stu-id="99b2a-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="99b2a-118">Em seguida, escolha "F0" para o tipo de preço.</span><span class="sxs-lookup"><span data-stu-id="99b2a-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="99b2a-119">Agora clique em "criar" (localizado no canto inferior esquerdo) para criar o recurso.</span><span class="sxs-lookup"><span data-stu-id="99b2a-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="99b2a-120">Observação: depois de clicar em "criar", você terá que aguardar o serviço a ser criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="99b2a-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="99b2a-121">Uma notificação será exibida no portal depois que o recurso é criado.</span><span class="sxs-lookup"><span data-stu-id="99b2a-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="99b2a-122">Clique nessa notificação e selecione "Ir para o recurso".</span><span class="sxs-lookup"><span data-stu-id="99b2a-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="99b2a-123">Na página "Início rápido" de seu serviço de "API do LUIS", navegue até a primeira etapa, pegue suas "chaves" e clique em "chaves" (você também pode fazer isso clicando no hiperlink azul "chaves", mostradas na imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="99b2a-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="99b2a-124">Isso irá revelar o seu serviço, "Chaves".</span><span class="sxs-lookup"><span data-stu-id="99b2a-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="99b2a-125">Salve uma cópia de uma das chaves para que você pode usá-lo mais tarde no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99b2a-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="99b2a-127">Volta na página "Início rápido" na seção 2b, clique em "Portal do reconhecimento vocal" (mostrado na imagem acima) para ser redirecionado à página da Web que você usará para criar seu novo serviço, dentro do aplicativo LUIS.</span><span class="sxs-lookup"><span data-stu-id="99b2a-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="99b2a-128">Observação: Ao atingir o "Portal do reconhecimento vocal", você talvez precise fazer logon, se você não ainda estiverem, com as mesmas credenciais que o seu portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="99b2a-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="99b2a-129">Se essa for sua primeira vez usando o LUIS, você precisará rolar para baixo para a parte inferior da página de boas-vinda, para localizar e clique no botão "Criar LUIS" aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99b2a-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="99b2a-130">Depois de conectado, clique em Meus aplicativos (se você não estiver nessa seção).</span><span class="sxs-lookup"><span data-stu-id="99b2a-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="99b2a-131">Você pode clicar em criar novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99b2a-131">You can then click on Create new app.</span></span> <span data-ttu-id="99b2a-132">Nomeie o novo aplicativo "Módulo de aprendizado de SDK da fala".</span><span class="sxs-lookup"><span data-stu-id="99b2a-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="99b2a-133">Adicione "Módulo de aprendizado de SDK de fala" para o campo de descrição.</span><span class="sxs-lookup"><span data-stu-id="99b2a-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="99b2a-134">Em seguida, clique em "concluído".</span><span class="sxs-lookup"><span data-stu-id="99b2a-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="99b2a-137">Observação: Se seu aplicativo deve para compreender um idioma diferente do inglês, você deve alterar a cultura"" para o idioma apropriado.</span><span class="sxs-lookup"><span data-stu-id="99b2a-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="99b2a-138">Clique em "Build", localizado no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="99b2a-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="99b2a-139">Em ativos de aplicativo à esquerda, selecione "Intenções", em seguida, clique em "Criar novo intenção" e nomeie-o "PressButton".</span><span class="sxs-lookup"><span data-stu-id="99b2a-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="99b2a-141">Observação: é importante usar os nomes das intenções e entidades usadas neste tutorial, porque o aplicativo Lunarcom referenciará-los por nome.</span><span class="sxs-lookup"><span data-stu-id="99b2a-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="99b2a-142">Para outros projetos, as convenções de nomenclatura podem ser tudo o que você escolher.</span><span class="sxs-lookup"><span data-stu-id="99b2a-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="99b2a-143">Observação: agora você deve ter 2 intenções - "PressButton" e "None".</span><span class="sxs-lookup"><span data-stu-id="99b2a-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="99b2a-144">Em ativos de aplicativo à esquerda, selecione "Entidades" e clique em "Criar nova entidade" e nomeie-a "Ação" e manter o tipo de entidade como "Simples".</span><span class="sxs-lookup"><span data-stu-id="99b2a-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="99b2a-146">Clique em "Criar nova entidade" novamente e nomeie-a "Destino" e manter o tipo de entidade como "Simples" também.</span><span class="sxs-lookup"><span data-stu-id="99b2a-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="99b2a-148">Em ativos de aplicativo à esquerda, selecione "Intenções" e clique em sua intenção de "PressButton" que você criou na etapa 10.</span><span class="sxs-lookup"><span data-stu-id="99b2a-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="99b2a-150">Clique no menu suspenso "Exibir opções" à direita e selecione "Mostrar valores de entidade".</span><span class="sxs-lookup"><span data-stu-id="99b2a-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="99b2a-152">Clique no "digite um exemplo..."</span><span class="sxs-lookup"><span data-stu-id="99b2a-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="99b2a-153">caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="99b2a-153">textbox.</span></span> <span data-ttu-id="99b2a-154">Em seguida, insira as seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="99b2a-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="99b2a-156">Clique no menu suspenso "Exibir opções" à direita e selecione "Mostrar nomes de entidade".</span><span class="sxs-lookup"><span data-stu-id="99b2a-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="99b2a-158">Certifique-se de que cada um a 10 declarações têm os seguintes rótulos de entidade nos locais a seguir por 1.) clicar em palavras que são rotulados de modo incorreto e, no pop-up, selecionando "remover o rótulo" e 2.) clicando em palavras que devem ser rotuladas e, no pop-up, selecionar o rótulo apropriado.</span><span class="sxs-lookup"><span data-stu-id="99b2a-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="99b2a-160">Agora, para publicar o modelo, clique em "Train" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="99b2a-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="99b2a-161">Depois que o processamento foi concluído, clique em "Test" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="99b2a-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="99b2a-163">Insira "Selecionar o botão de inicialização" na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="99b2a-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="99b2a-164">Observação: não adicionamos "selecionar" como uma ação em qualquer uma das nossas declarações - mas se você clicar em "Inspecionar", o modelo reconhecido "selecionar" como uma entidade de ação.</span><span class="sxs-lookup"><span data-stu-id="99b2a-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="99b2a-166">Agora, clique em "Publicar" no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="99b2a-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="99b2a-167">Verifique se que a lista suspensa diz "Produção" e clique em "Publicar" o pop-up também.</span><span class="sxs-lookup"><span data-stu-id="99b2a-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="99b2a-169">Depois de publicado, uma barra verde deve aparecer na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="99b2a-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="99b2a-170">Clique na barra de verde para ser levado à página "Gerenciar".</span><span class="sxs-lookup"><span data-stu-id="99b2a-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="99b2a-172">Clique em "Chaves e pontos de extremidade" em "Configurações de aplicativo" à esquerda.</span><span class="sxs-lookup"><span data-stu-id="99b2a-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="99b2a-173">Em seguida, defina a lista suspensa "Publish To" como "Produção".</span><span class="sxs-lookup"><span data-stu-id="99b2a-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="99b2a-174">Definir o fuso horário para corresponder às suas e marque a caixa para incluir todas as pontuações previstas de intenção.</span><span class="sxs-lookup"><span data-stu-id="99b2a-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="99b2a-175">Por fim, clique em "Atribuir recursos".</span><span class="sxs-lookup"><span data-stu-id="99b2a-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="99b2a-177">Selecione o locatário na primeira lista suspensa e selecione "Pré-pago" no menu suspenso o nome da assinatura.</span><span class="sxs-lookup"><span data-stu-id="99b2a-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="99b2a-178">Em nome do recurso LUIS, escolha o recurso que criamos acima nas etapas 1 a 5.</span><span class="sxs-lookup"><span data-stu-id="99b2a-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="99b2a-179">Em seguida, clique em "Atribuir recursos".</span><span class="sxs-lookup"><span data-stu-id="99b2a-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="99b2a-181">Observação: Certifique-se de copiar e salvar a URL de ponto de extremidade associado ao recurso que atribuímos apenas para que ele seja facilmente acessível para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="99b2a-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="99b2a-182">Observação: para o nome do locatário, colocar sua empresa ou o perfil que você criou para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99b2a-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="99b2a-183">Agora, abra o novo aplicativo no Unity e selecione o objeto Lunarcom_Base na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="99b2a-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="99b2a-184">Clique em "Adicionar componente" no painel Inspetor, pesquise e selecione "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="99b2a-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="99b2a-186">No campo de "LunarcomIntentRecognizer" no painel Inspetor Luis Endpoint, insira a URL de ponto de extremidade que você salvou na etapa 22.</span><span class="sxs-lookup"><span data-stu-id="99b2a-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="99b2a-188">Observação: No componente "LunarcomOfflineRecognizer" no painel Inspetor, certifique-se de que "Desabilitar" está selecionado para "SimulateOfflineMode" caso contrário, o programa de teste não funcionará.</span><span class="sxs-lookup"><span data-stu-id="99b2a-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="99b2a-189">Pressione o botão Reproduzir no Editor do Unity e clique no botão de rocket para iniciar o reconhecimento de intenção.</span><span class="sxs-lookup"><span data-stu-id="99b2a-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="99b2a-190">Emitido a frase "Selecionar o botão de bicho de inicialização".</span><span class="sxs-lookup"><span data-stu-id="99b2a-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="99b2a-191">Observação: O aplicativo reconhecido na função desejada e ativado no botão dos rocket.</span><span class="sxs-lookup"><span data-stu-id="99b2a-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="99b2a-193">Parabéns</span><span class="sxs-lookup"><span data-stu-id="99b2a-193">Congratulations</span></span>

<span data-ttu-id="99b2a-194">Oficialmente, você aprendeu como adicionar comandos de fala do programa fala SDK!</span><span class="sxs-lookup"><span data-stu-id="99b2a-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="99b2a-195">Agora seu programa possa reconhecer os comandos de fala de todos os tipos de variantes.</span><span class="sxs-lookup"><span data-stu-id="99b2a-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="99b2a-196">Testá-lo e se divertir um pouco com ele!</span><span class="sxs-lookup"><span data-stu-id="99b2a-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="99b2a-197">Próxima lição: SDK de fala lição 5</span><span class="sxs-lookup"><span data-stu-id="99b2a-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)


---
title: Tutoriais de Serviços de Fala do Azure – 4. Como configurar a intenção e o reconhecimento vocal natural
description: Conclua este curso para saber como implementar o SDK de Fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b2342e7d0d502af2787ca311d18a44f8726acf2d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028553"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="54f31-105">4. Como configurar a intenção e o reconhecimento vocal natural</span><span class="sxs-lookup"><span data-stu-id="54f31-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="54f31-106">Neste tutorial, você vai explorar o reconhecimento de intenção do Serviço de Fala do Azure.</span><span class="sxs-lookup"><span data-stu-id="54f31-106">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="54f31-107">O reconhecimento de intenção permite que você equipe o aplicativo com comandos de fala com IA, em que os usuários podem dizer comandos de fala não específicos e ainda ter sua intenção compreendida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="54f31-107">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="54f31-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="54f31-108">Objectives</span></span>

* <span data-ttu-id="54f31-109">Saiba como configurar intenção, entidades e enunciados no portal do LUIS</span><span class="sxs-lookup"><span data-stu-id="54f31-109">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="54f31-110">Saiba como implementar a intenção e o reconhecimento vocal natural em nosso aplicativo</span><span class="sxs-lookup"><span data-stu-id="54f31-110">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="54f31-111">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="54f31-111">Preparing the scene</span></span>

<span data-ttu-id="54f31-112">Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Intenção do Lunarcom (Script)** ao objeto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="54f31-112">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="54f31-114">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.GettingStarted** > **Pré-fabricados** > **RocketLauncher**, arraste o pré-fabricado **RocketLauncher_Complete** para a janela Hierarquia e coloque-o em uma localização adequada na frente da câmera, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="54f31-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="54f31-115">**Posição** da Transformação X = 0, Y = -0,4, Z = 1</span><span class="sxs-lookup"><span data-stu-id="54f31-115">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="54f31-116">**Rotação** da Transformação X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="54f31-116">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="54f31-118">Na janela Hierarquia, selecione o objeto **Lunarcom** novamente e, em seguida, expanda o objeto **RocketLauncher_Complete** > **Botão** e atribua a cada um dos botões filho do objeto **Botões** ao campo **Botões do Iniciador Lunar** correspondente:</span><span class="sxs-lookup"><span data-stu-id="54f31-118">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="54f31-120">Como criar o recurso de Reconhecimento vocal do Azure</span><span class="sxs-lookup"><span data-stu-id="54f31-120">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="54f31-121">Nesta seção, você criará um recurso de previsão do Azure para o aplicativo LUIS (Serviço Inteligente de Reconhecimento vocal) que será criado na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="54f31-121">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="54f31-122">Entre no <a href="https://portal.azure.com" target="_blank">Azure</a> e clique em **Criar um recurso**.</span><span class="sxs-lookup"><span data-stu-id="54f31-122">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="54f31-123">Em seguida, pesquise e selecione **Reconhecimento vocal**:</span><span class="sxs-lookup"><span data-stu-id="54f31-123">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="54f31-125">Clique no botão **Criar** para criar uma instância desse serviço:</span><span class="sxs-lookup"><span data-stu-id="54f31-125">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="54f31-127">Na página Criar, clique na opção **Previsão** e insira os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="54f31-127">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="54f31-128">Para **Assinatura**, selecione **Avaliação Gratuita** se você tiver uma assinatura de avaliação, caso contrário, selecione uma das outras assinaturas</span><span class="sxs-lookup"><span data-stu-id="54f31-128">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="54f31-129">Para o **Grupo de recursos**, clique no link **Criar**, insira um nome adequado, por exemplo, *MRKT-Tutoriais* e, em seguida, clique em **OK**</span><span class="sxs-lookup"><span data-stu-id="54f31-129">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click the **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="54f31-131">No momento da redação deste artigo, você não precisa criar um recurso de criação porque uma chave de avaliação de criação será gerada automaticamente no LUIS quando você criar o LUIS (Serviço Inteligente de Reconhecimento vocal) na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="54f31-131">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="54f31-132">Se você já tiver outro grupo de recursos adequado em sua conta do Azure, por exemplo, se tiver concluído o tutorial [Âncoras Espaciais do Azure](mrlearning-asa-ch1.md), poderá usar esse grupo de recursos em vez de criar um.</span><span class="sxs-lookup"><span data-stu-id="54f31-132">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mrlearning-asa-ch1.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="54f31-133">Enquanto ainda estiver na página Criar, insira os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="54f31-133">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="54f31-134">Para **Nome**, insira um nome adequado para o serviço, por exemplo, *MRTK-Tutoriais-AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="54f31-134">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="54f31-135">Para **Localização de previsão**, escolha uma localização próxima à localização física dos usuários do seu aplicativo, por exemplo, *(EUA) Oeste dos EUA*</span><span class="sxs-lookup"><span data-stu-id="54f31-135">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="54f31-136">Para **Tipo de preço de previsão**, para os fins deste tutorial, selecione **F0 (cinco chamadas por segundo, dez mil chamadas por mês)**</span><span class="sxs-lookup"><span data-stu-id="54f31-136">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="54f31-138">Em seguida, vá para a guia **Examinar + criar**, examine os detalhes e clique no botão **Criar**, localizado na parte inferior da página, para criar o recurso, bem como no novo grupo de recursos se você tiver configurado um para ser criado:</span><span class="sxs-lookup"><span data-stu-id="54f31-138">Next, go to the **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="54f31-140">Depois de clicar no botão Criar, você precisará aguardar até que o serviço seja criado, o que poderá levar alguns minutos.</span><span class="sxs-lookup"><span data-stu-id="54f31-140">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="54f31-141">Depois que o processo de criação de recursos for concluído, você verá a mensagem **Sua implantação foi concluída**:</span><span class="sxs-lookup"><span data-stu-id="54f31-141">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="54f31-143">Como criar o LUIS (Serviço Inteligente de Reconhecimento Vocal)</span><span class="sxs-lookup"><span data-stu-id="54f31-143">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="54f31-144">Nesta seção, você criará um aplicativo LUIS, configurará e treinará seu modelo de previsão e o conectará ao recurso de previsão do Azure criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="54f31-144">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="54f31-145">Especificamente, você criará uma intenção de que, se o usuário disser que uma ação deve ser executada, o aplicativo disparará o evento Interactable.OnClick() em um dos três botões vermelhos na cena, dependendo de a qual botão o usuário faz referência.</span><span class="sxs-lookup"><span data-stu-id="54f31-145">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="54f31-146">Por exemplo, se o usuário disser **ir em frente e lançar o foguete**, o aplicativo preverá que **vá em frente** significa que algumas **ações** devem ser executadas e que o evento Interactable.OnClick() para o **destino** está no botão **lançar**.</span><span class="sxs-lookup"><span data-stu-id="54f31-146">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="54f31-147">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="54f31-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="54f31-148">Criar um aplicativo LUIS</span><span class="sxs-lookup"><span data-stu-id="54f31-148">Create a LUIS app</span></span>
2. <span data-ttu-id="54f31-149">Criar intenções</span><span class="sxs-lookup"><span data-stu-id="54f31-149">Create intents</span></span>
3. <span data-ttu-id="54f31-150">Criar exemplos de enunciados</span><span class="sxs-lookup"><span data-stu-id="54f31-150">Create example utterances</span></span>
4. <span data-ttu-id="54f31-151">Criar entidades</span><span class="sxs-lookup"><span data-stu-id="54f31-151">Create entities</span></span>
5. <span data-ttu-id="54f31-152">Atribuir entidades a exemplos de enunciados</span><span class="sxs-lookup"><span data-stu-id="54f31-152">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="54f31-153">Treinar, testar e publicar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="54f31-153">Train, test, and publish the app</span></span>
7. <span data-ttu-id="54f31-154">Atribuir um recurso de previsão do Azure ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="54f31-154">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="54f31-155">1. Criar um aplicativo LUIS</span><span class="sxs-lookup"><span data-stu-id="54f31-155">1. Create a LUIS app</span></span>

<span data-ttu-id="54f31-156">Usando a mesma conta de usuário usada ao criar o recurso do Azure na seção anterior, entre no <a href="https://www.luis.ai" target="_blank">LUIS</a>, selecione seu país/região e concorde com os Termos de uso.</span><span class="sxs-lookup"><span data-stu-id="54f31-156">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="54f31-157">Na próxima etapa, quando você for solicitado a **Vincular sua conta do Azure**, escolha **Continuar usando sua chave de avaliação** para usar um recurso de criação do Azure em vez disso.</span><span class="sxs-lookup"><span data-stu-id="54f31-157">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="54f31-158">Se você já se inscreveu no LUIS e sua chave de avaliação de criação expirou, pode ver a documentação [Migrar para uma chave de criação de recursos do Azure](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) para alternar o recurso de criação do LUIS para o Azure.</span><span class="sxs-lookup"><span data-stu-id="54f31-158">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="54f31-159">Depois de conectado, navegue até a página **Meus aplicativos**, clique em **Criar aplicativo** e insira os seguintes valores na janela pop-up **Criar aplicativo**:</span><span class="sxs-lookup"><span data-stu-id="54f31-159">Once signed in, navigate to the **My apps** page, then click **Create new app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="54f31-160">Para **Nome**, insira um nome adequado, por exemplo, *Tutoriais do MRTK – AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="54f31-160">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="54f31-161">Para **Cultura**, selecione **Inglês**</span><span class="sxs-lookup"><span data-stu-id="54f31-161">For **Culture**, select **English**</span></span>
* <span data-ttu-id="54f31-162">Para **Descrição**, opcionalmente, insira uma descrição adequada</span><span class="sxs-lookup"><span data-stu-id="54f31-162">For **Description**, optionally enter a suitable description</span></span>

<span data-ttu-id="54f31-163">Em seguida, clique no botão **Concluído** para criar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="54f31-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="54f31-165">Quando o aplicativo tiver sido criado, você será levado para a página **Painel** desse aplicativo:</span><span class="sxs-lookup"><span data-stu-id="54f31-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="54f31-167">2. Criar intenções</span><span class="sxs-lookup"><span data-stu-id="54f31-167">2. Create intents</span></span>

<span data-ttu-id="54f31-168">Na página Painel, navegue até a página Criar > Ativos de Aplicativo > **Intenções**, clique em **Criar intenção** e insira o seguinte valor na janela pop-up **Criar intenção**:</span><span class="sxs-lookup"><span data-stu-id="54f31-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create new intent** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="54f31-169">Para **Nome da intenção**, insira **PressButton**</span><span class="sxs-lookup"><span data-stu-id="54f31-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="54f31-170">Em seguida, clique no botão **Concluído** para criar a intenção:</span><span class="sxs-lookup"><span data-stu-id="54f31-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="54f31-172">Para os fins deste tutorial, seu projeto do Unity fará referência a essa intenção por seu nome, ou seja, 'PressButton'.</span><span class="sxs-lookup"><span data-stu-id="54f31-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="54f31-173">Assim, é extremamente importante que você dê à sua intenção um nome exatamente igual.</span><span class="sxs-lookup"><span data-stu-id="54f31-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="54f31-174">Quando a intenção for criada, você será levado para a página dessa intenção:</span><span class="sxs-lookup"><span data-stu-id="54f31-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="54f31-176">3. Criar exemplos de enunciados</span><span class="sxs-lookup"><span data-stu-id="54f31-176">3. Create example utterances</span></span>

<span data-ttu-id="54f31-177">Para a lista **Enunciado de exemplo** da intenção **PressButton**, adicione os seguintes enunciados de exemplo:</span><span class="sxs-lookup"><span data-stu-id="54f31-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="54f31-178">ativar sequência de inicialização</span><span class="sxs-lookup"><span data-stu-id="54f31-178">activate launch sequence</span></span>
* <span data-ttu-id="54f31-179">mostrar-me uma dica de posicionamento</span><span class="sxs-lookup"><span data-stu-id="54f31-179">show me a placement hint</span></span>
* <span data-ttu-id="54f31-180">iniciar a sequência de inicialização</span><span class="sxs-lookup"><span data-stu-id="54f31-180">initiate the launch sequence</span></span>
* <span data-ttu-id="54f31-181">pressionar o botão de dicas de posicionamento</span><span class="sxs-lookup"><span data-stu-id="54f31-181">press placement hints button</span></span>
* <span data-ttu-id="54f31-182">dê-me uma dica</span><span class="sxs-lookup"><span data-stu-id="54f31-182">give me a hint</span></span>
* <span data-ttu-id="54f31-183">pressione o botão iniciar</span><span class="sxs-lookup"><span data-stu-id="54f31-183">push the launch button</span></span>
* <span data-ttu-id="54f31-184">preciso de uma dica</span><span class="sxs-lookup"><span data-stu-id="54f31-184">i need a hint</span></span>
* <span data-ttu-id="54f31-185">pressione o botão redefinir</span><span class="sxs-lookup"><span data-stu-id="54f31-185">press the reset button</span></span>
* <span data-ttu-id="54f31-186">tempo para redefinir a experiência</span><span class="sxs-lookup"><span data-stu-id="54f31-186">time to reset the experience</span></span>
* <span data-ttu-id="54f31-187">Ir em frente e lançar o foguete</span><span class="sxs-lookup"><span data-stu-id="54f31-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="54f31-188">Quando todos os enunciados de exemplo tiverem sido adicionados, sua página de intenção de PressButton deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="54f31-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="54f31-190">Para os fins deste tutorial, seu projeto do Unity fará referência às palavras "dica", "dicas", "redefinir" e "iniciar".</span><span class="sxs-lookup"><span data-stu-id="54f31-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="54f31-191">Assim, é extremamente importante que você escreva essas palavras exatamente da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="54f31-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="54f31-192">4. Criar entidades</span><span class="sxs-lookup"><span data-stu-id="54f31-192">4. Create entities</span></span>

<span data-ttu-id="54f31-193">Na página de intenção PressButton, navegue até a página Criar > Ativos de Aplicativo > **Entidades** e clique em **Criar entidade**, então insira os seguintes valores na janela pop-up **Criar entidade**:</span><span class="sxs-lookup"><span data-stu-id="54f31-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create new entity** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="54f31-194">Para **Nome da entidade**, insira **Ação**</span><span class="sxs-lookup"><span data-stu-id="54f31-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="54f31-195">Para **Tipo de entidade**, selecione **Simples**</span><span class="sxs-lookup"><span data-stu-id="54f31-195">For **Entity type**, select **Simple**</span></span>

<span data-ttu-id="54f31-196">Em seguida, clique no botão **Concluído** para criar a entidade:</span><span class="sxs-lookup"><span data-stu-id="54f31-196">Then click the **Done** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="54f31-198">**Repita** a etapa anterior para criar outra entidade chamada **Destino** para que você tenha duas entidades chamadas Ação e Destino:</span><span class="sxs-lookup"><span data-stu-id="54f31-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="54f31-200">Para os fins deste tutorial, seu projeto do Unity fará referência a essas entidades pelo nome, ou seja, "Ação" e "Alvo".</span><span class="sxs-lookup"><span data-stu-id="54f31-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="54f31-201">Assim, é extremamente importante que você dê às suas entidades um nome exatamente igual.</span><span class="sxs-lookup"><span data-stu-id="54f31-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="54f31-202">5. Atribuir entidades a exemplos de enunciados</span><span class="sxs-lookup"><span data-stu-id="54f31-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="54f31-203">Na página entidades, navegue de volta para a página de intenção de **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="54f31-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="54f31-204">Depois de voltar para a página de intenção de PressButton, clique na palavra **ir** e, em seguida, na palavra **em frente** e selecione **Ação (Simples)** no menu pop-up contextual para rotular **ir em frente** como um valor de entidade de **Ação**:</span><span class="sxs-lookup"><span data-stu-id="54f31-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="54f31-206">A frase **ir em frente** frase agora é definida como um valor de entidade de **Ação**.</span><span class="sxs-lookup"><span data-stu-id="54f31-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="54f31-207">Se você passar o cursor do mouse sobre o nome da entidade de Ação, poderá ver o valor da entidade de Ação associada:</span><span class="sxs-lookup"><span data-stu-id="54f31-207">If you hover your mouse cursor above the Action entity name, you can see the associated Action entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="54f31-209">A linha vermelha que você vê sob o rótulo na imagem acima indica que o valor da entidade não foi previsto. Isso será resolvido quando você treinar o modelo na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="54f31-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="54f31-210">Em seguida, clique na palavra **iniciar** e, em seguida, selecione **Destino (Simples)** no menu pop-up contextual para rotular **iniciar** como um valor de entidade de **destino**:</span><span class="sxs-lookup"><span data-stu-id="54f31-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="54f31-212">A palavra **iniciar** agora está definida como um valor de entidade de **Destino**.</span><span class="sxs-lookup"><span data-stu-id="54f31-212">The **launch** word is now defined as a **Target** entity value.</span></span> <span data-ttu-id="54f31-213">Se você passar o cursor do mouse sobre o nome da entidade de Destino, poderá ver o valor da entidade de Destino associada:</span><span class="sxs-lookup"><span data-stu-id="54f31-213">If you hover your mouse cursor above the Target entity name, you can see the associated Target entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="54f31-215">O enunciado de exemplo de intenção PressButton "ir em frente e lançar o foguete" agora está configurado para ser previsto da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="54f31-215">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="54f31-216">Intenção: PressButton</span><span class="sxs-lookup"><span data-stu-id="54f31-216">Intent: PressButton</span></span>
* <span data-ttu-id="54f31-217">Entidade de ação: vá em frente</span><span class="sxs-lookup"><span data-stu-id="54f31-217">Action entity: go ahead</span></span>
* <span data-ttu-id="54f31-218">Entidade de destino: iniciar</span><span class="sxs-lookup"><span data-stu-id="54f31-218">Target entity: launch</span></span>

<span data-ttu-id="54f31-219">**Repita** o processo anterior de duas etapas para atribuir uma ação e um rótulo de entidade de Destino a cada um dos exemplos de enunciado, tendo em mente que as seguintes palavras devem ser rotuladas como entidades de **Destino**:</span><span class="sxs-lookup"><span data-stu-id="54f31-219">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="54f31-220">**dica** (tem como destino HintsButton no projeto do Unity)</span><span class="sxs-lookup"><span data-stu-id="54f31-220">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="54f31-221">**dicas** (tem como destino HintsButton no projeto do Unity)</span><span class="sxs-lookup"><span data-stu-id="54f31-221">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="54f31-222">**redefinir** (tem como destino ResetButton no projeto do Unity)</span><span class="sxs-lookup"><span data-stu-id="54f31-222">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="54f31-223">**iniciar** (tem como destino LaunchButton no projeto do Unity)</span><span class="sxs-lookup"><span data-stu-id="54f31-223">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="54f31-224">Quando todos os enunciados de exemplo tiverem sido rotulados, sua página de intenção de PressButton deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="54f31-224">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

<span data-ttu-id="54f31-226">Como alternativa para verificar novamente se você atribuiu as entidades corretas, clique no menu **Exibir opções** e alterne a exibição para **Mostrar valores de entidade**:</span><span class="sxs-lookup"><span data-stu-id="54f31-226">For an alternative way to double-check that you have assigned the correct entities, click the **View options** menu and switch the view to **Show entity values**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

<span data-ttu-id="54f31-228">Agora, com o modo de exibição definido para mostrar valores de entidade, você pode focalizar o curso do mouse sobre as palavras e frases rotuladas para verificar rapidamente o nome da entidade atribuída:</span><span class="sxs-lookup"><span data-stu-id="54f31-228">Now, with the view set to show entity values, you can hover the mouse courser over the labeled words and phrases to quickly verify the assigned entity name:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="54f31-230">6. Treinar, testar e publicar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="54f31-230">6. Train, test, and publish the app</span></span>

<span data-ttu-id="54f31-231">Para treinar o aplicativo, clique no botão **Treinar** e aguarde a conclusão do processo de treinamento:</span><span class="sxs-lookup"><span data-stu-id="54f31-231">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="54f31-233">Como você pode ver na imagem acima, as linhas vermelhas em todos os rótulos foram removidas, indicando que todos os valores de entidade foram previstos.</span><span class="sxs-lookup"><span data-stu-id="54f31-233">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="54f31-234">Observe também que o ícone de status à esquerda do botão Treinar mudou a cor de vermelho para verde.</span><span class="sxs-lookup"><span data-stu-id="54f31-234">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="54f31-235">Quando o processamento do treinamento for concluído, clique no botão **Testar**, digite **ir em frente e lançar o foguete** e pressione a tecla Enter:</span><span class="sxs-lookup"><span data-stu-id="54f31-235">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="54f31-237">Quando o enunciado de teste tiver sido processado, clique em **Inspecionar** para ver o resultado do teste:</span><span class="sxs-lookup"><span data-stu-id="54f31-237">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="54f31-238">Intenção: PressButton (com uma certeza de 98,5%)</span><span class="sxs-lookup"><span data-stu-id="54f31-238">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="54f31-239">Entidade de ação: vá em frente</span><span class="sxs-lookup"><span data-stu-id="54f31-239">Action entity: go ahead</span></span>
* <span data-ttu-id="54f31-240">Entidade de destino: iniciar</span><span class="sxs-lookup"><span data-stu-id="54f31-240">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="54f31-242">Para publicar o aplicativo, clique no botão **Publicar** no canto superior direito e, em seguida, na janela **Escolher o slot e as configurações de publicação**, selecione **Produção** e clique no botão **Publicar**:</span><span class="sxs-lookup"><span data-stu-id="54f31-242">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Publish** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="54f31-244">Aguarde a conclusão do processo de publicação:</span><span class="sxs-lookup"><span data-stu-id="54f31-244">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a><span data-ttu-id="54f31-246">7. Atribuir um recurso de previsão do Azure ao aplicativo</span><span class="sxs-lookup"><span data-stu-id="54f31-246">7. Assign an Azure prediction resource to the app</span></span>

<span data-ttu-id="54f31-247">Navegue até a página Gerenciar > Configurações do Aplicativo > **Recursos do Azure**:</span><span class="sxs-lookup"><span data-stu-id="54f31-247">Navigate to the Manage > Application Settings > **Azure Resources** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

<span data-ttu-id="54f31-249">Na página Recursos do Azure, clique no botão **Adicionar recurso de previsão** e selecione os seguintes valores na janela pop-up **Atribuir um recurso ao aplicativo**:</span><span class="sxs-lookup"><span data-stu-id="54f31-249">On the Azure Resources page, click the **Add prediction resource** button and select the following values in the **Assign a resource to your app** popup window:</span></span>

* <span data-ttu-id="54f31-250">Para **Nome do locatário**, selecione o nome do locatário</span><span class="sxs-lookup"><span data-stu-id="54f31-250">For **Tenant name**, select your tenant name</span></span>
* <span data-ttu-id="54f31-251">Para **Nome da assinatura**, selecione a mesma assinatura que você usou anteriormente ao [Criar o recurso de Reconhecimento vocal do Azure](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span><span class="sxs-lookup"><span data-stu-id="54f31-251">For **Subscription Name**, select the same subscription you used earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>
* <span data-ttu-id="54f31-252">Para **Nome de recurso LUIS**, selecione o recurso de previsão que você criou anteriormente ao [Criar o recurso de Reconhecimento vocal do Azure](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span><span class="sxs-lookup"><span data-stu-id="54f31-252">For **LUIS resource name**, select the prediction resource you created earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>

<span data-ttu-id="54f31-253">Em seguida, clique no botão **Atribuir recurso** para atribuir o recurso de previsão do Azure ao seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="54f31-253">Then click the **Assign resource** button to assign the Azure prediction resource to your app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

<span data-ttu-id="54f31-255">Quando o recurso tiver sido atribuído, sua página de recursos do Azure deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="54f31-255">When the resource has been assigned, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="54f31-257">Como conectar o projeto do Unity ao aplicativo LUIS</span><span class="sxs-lookup"><span data-stu-id="54f31-257">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="54f31-258">Na página Gerenciar > Configurações do Aplicativo > **Recursos do Azure**, clique no ícone **copiar** para copiar a **Consulta de Exemplo**:</span><span class="sxs-lookup"><span data-stu-id="54f31-258">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="54f31-260">De volta ao seu projeto do Unity, na janela Hierarquia, selecione o objeto **Lunarcom** e, em seguida, na janela Inspetor, localize o componente **Lunarcom do Reconhecedor de Intenção (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="54f31-260">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="54f31-261">No campo **Ponto de Extremidade LUIS**, após a **Consulta de Exemplo** que você copiou na etapa anterior:</span><span class="sxs-lookup"><span data-stu-id="54f31-261">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="54f31-263">Como testar e aprimorar o reconhecimento de intenção</span><span class="sxs-lookup"><span data-stu-id="54f31-263">Testing and improving the intent recognition</span></span>

<span data-ttu-id="54f31-264">Para usar o reconhecimento de intenção diretamente no editor do Unity, você deve permitir que seu computador de desenvolvimento use ditado.</span><span class="sxs-lookup"><span data-stu-id="54f31-264">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="54f31-265">Para verificar essa configuração, abra as **Configurações** do Windows e escolha **Privacidade** > **Fala** e garanta que **Reconhecimento de fala online** esteja ativado:</span><span class="sxs-lookup"><span data-stu-id="54f31-265">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="54f31-267">Se agora você entrar no modo de Jogo, poderá testar o reconhecimento de intenção pressionando primeiro o botão foguete.</span><span class="sxs-lookup"><span data-stu-id="54f31-267">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="54f31-268">Em seguida, supondo que o computador tenha um microfone, quando você disser o primeiro enunciado de exemplo, **ir em frente e lançar o foguete**, você verá o lançamento do LunarModule no espaço:</span><span class="sxs-lookup"><span data-stu-id="54f31-268">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="54f31-270">Experimente todos os **enunciados de exemplo**, então algumas **variações dos enunciados de exemplo**, bem como alguns **enunciados aleatórios**.</span><span class="sxs-lookup"><span data-stu-id="54f31-270">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="54f31-271">Em seguida, retorne para <a href="https://www.luis.ai" target="_blank">LUIS</a> e navegue para a página Criar > Aprimorar o desempenho do aplicativo > **Examinar enunciados do ponto de extremidade**, use o botão de **alternância** para alternar da Exibição de Entidades padrão para **Exibição de Tokens** e, em seguida, examine os enunciados:</span><span class="sxs-lookup"><span data-stu-id="54f31-271">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="54f31-272">Na coluna **Enunciado**, altere e remova os rótulos atribuídos conforme necessário para que eles se alinhem com a sua intenção</span><span class="sxs-lookup"><span data-stu-id="54f31-272">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="54f31-273">Na coluna **Intenção alinhada**, verifique se a intenção está correta</span><span class="sxs-lookup"><span data-stu-id="54f31-273">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="54f31-274">Na coluna **Adicionar/Excluir**, clique no botão de marca de seleção verde para adicionar o enunciado ou o botão x vermelho para excluí-lo</span><span class="sxs-lookup"><span data-stu-id="54f31-274">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="54f31-275">Quando você tiver examinado o número de enunciados que desejar, clique no botão **Treinar** para treinar novamente o modelo e, em seguida, no botão **Publicar** para republicar o aplicativo atualizado:</span><span class="sxs-lookup"><span data-stu-id="54f31-275">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="54f31-277">Se um enunciado do ponto de extremidade não se alinhar com a intenção PressButton, mas você quiser que seu modelo saiba que o enunciado não tem nenhuma intenção, poderá alterar a intenção Alinhada para Nenhum.</span><span class="sxs-lookup"><span data-stu-id="54f31-277">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="54f31-278">**Repita** esse processo quantas vezes desejar para aprimorar seu modelo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="54f31-278">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="54f31-279">Parabéns</span><span class="sxs-lookup"><span data-stu-id="54f31-279">Congratulations</span></span>

<span data-ttu-id="54f31-280">Seu projeto agora tem comandos de fala habilitados para IA, permitindo que seu aplicativo reconheça a intenção dos usuários, mesmo que eles não enunciem comandos precisos.</span><span class="sxs-lookup"><span data-stu-id="54f31-280">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="54f31-281">Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="54f31-281">Run the application on your device to ensure the feature is working properly.</span></span>

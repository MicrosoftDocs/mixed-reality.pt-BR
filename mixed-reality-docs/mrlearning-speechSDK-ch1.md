---
title: TUTORIAIS dos serviços de fala do Azure-1. Integrando e usando o reconhecimento de fala e a transcrição
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 501e8bc2e70248a4ca8a79f90d74d30129830701
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701958"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="e6009-105">1. Integrando e usando o reconhecimento de fala e a transcrição</span><span class="sxs-lookup"><span data-stu-id="e6009-105">1. Integrating and using speech recognition and transcription</span></span>

<span data-ttu-id="e6009-106">Este tutorial cria um aplicativo de realidade misturada que explora o uso do SDK de fala dos serviços cognitivas do Azure com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e6009-106">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="e6009-107">Quando terminar com esta série de tutoriais, você poderá usar o microfone do dispositivo para transcrever a fala para o texto em tempo real, traduzir sua fala em outras linguagens e aproveitar o recurso de intenção do SDK de fala para entender os comandos de voz usando inteligência artificial.</span><span class="sxs-lookup"><span data-stu-id="e6009-107">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="e6009-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e6009-108">Objectives</span></span>

- <span data-ttu-id="e6009-109">Saiba como integrar o SDK de fala do Azure em um aplicativo do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e6009-109">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="e6009-110">Saiba como usar comandos de voz</span><span class="sxs-lookup"><span data-stu-id="e6009-110">Learn how to use voice commands</span></span>
- <span data-ttu-id="e6009-111">Saiba como usar os recursos de fala para texto</span><span class="sxs-lookup"><span data-stu-id="e6009-111">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="e6009-112">Instruções</span><span class="sxs-lookup"><span data-stu-id="e6009-112">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="e6009-113">Guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="e6009-113">Getting Started</span></span>

1. <span data-ttu-id="e6009-114">Inicie o Unity e crie um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="e6009-114">Start Unity, and create a new project.</span></span> <span data-ttu-id="e6009-115">Insira o nome do projeto módulo de aprendizagem do SDK de fala.</span><span class="sxs-lookup"><span data-stu-id="e6009-115">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="e6009-116">Escolha um local para onde salvar o projeto.</span><span class="sxs-lookup"><span data-stu-id="e6009-116">Choose a location for where to save your project.</span></span> <span data-ttu-id="e6009-117">Em seguida, clique em criar projeto.</span><span class="sxs-lookup"><span data-stu-id="e6009-117">Then click Create Project.</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="e6009-119">Observação: Verifique se o modelo está definido como 3D, conforme mostrado na imagem acima.</span><span class="sxs-lookup"><span data-stu-id="e6009-119">Note: Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="e6009-120">Baixe o pacote de Unity do [Kit de ferramentas da realidade mista](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) e salve-o em uma pasta no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e6009-120">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package, and save it to a folder on your PC.</span></span> <span data-ttu-id="e6009-121">Importe o pacote para o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="e6009-121">Import the package into your Unity project.</span></span> <span data-ttu-id="e6009-122">Para obter instruções detalhadas sobre como fazer isso, consulte a [lição 1 do módulo base](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="e6009-122">For detailed instructions on how to do this, please see [Base Module Lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="e6009-123">Baixe e importe o [SDK de fala](https://aka.ms/csspeech/unitypackage) do Azure para o pacote de ativos do Unity.</span><span class="sxs-lookup"><span data-stu-id="e6009-123">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="e6009-124">Importe o pacote do SDK de fala clicando em ativos, selecionando importar pacote e, em seguida, selecionando pacote personalizado.</span><span class="sxs-lookup"><span data-stu-id="e6009-124">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="e6009-125">Localize o pacote do SDK de fala baixado anteriormente e abra-o para iniciar o processo de importação.</span><span class="sxs-lookup"><span data-stu-id="e6009-125">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span> 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="e6009-128">Na próxima janela pop-up, clique em importar para começar a importar o pacote do SDK de fala.</span><span class="sxs-lookup"><span data-stu-id="e6009-128">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="e6009-129">Verifique se todos os itens estão marcados conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="e6009-129">Ensure all items are checked as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. <span data-ttu-id="e6009-131">Baixe o pacote de ativos do módulo SDK de fala, também conhecido como pacote Lunarcom clicando nesse [link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span><span class="sxs-lookup"><span data-stu-id="e6009-131">Download the Speech SDK Module asset pack, also know as Lunarcom package by clicking on [this link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span></span> <span data-ttu-id="e6009-132">O pacote de ativos do Lunarcom é uma coleção de ativos e scripts desenvolvidos para esta série de lições para demonstrar um uso prático do SDK de fala do Azure.</span><span class="sxs-lookup"><span data-stu-id="e6009-132">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="e6009-133">É um terminal de comando de voz que, por fim, fará a interface com a experiência de montagem do módulo lunar desenvolvida no [tutorial do módulo base.](mrlearning-base-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="e6009-133">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>

6. <span data-ttu-id="e6009-134">Importe o pacote de ativos do Lunarcom para seu projeto do Unity seguindo as etapas semelhantes que você levou para importar o kit de ferramentas e o SDK de fala misturados da realidade.</span><span class="sxs-lookup"><span data-stu-id="e6009-134">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="e6009-135">Configure o MRTK (Kit de ferramentas de realidade mista).</span><span class="sxs-lookup"><span data-stu-id="e6009-135">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="e6009-136">Para fazer isso, clique no painel do kit de ferramentas da realidade misturada na parte superior da janela e, em seguida, selecione Adicionar à cena e configurar.</span><span class="sxs-lookup"><span data-stu-id="e6009-136">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. <span data-ttu-id="e6009-140">Sua cena agora tem vários novos itens da MRTK.</span><span class="sxs-lookup"><span data-stu-id="e6009-140">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="e6009-141">Salve sua cena com um nome diferente clicando em "arquivo" e, em seguida, em "salvar como" e nomeie sua cena como SpeechScene.</span><span class="sxs-lookup"><span data-stu-id="e6009-141">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span> 

> <span data-ttu-id="e6009-142">Observação: Se você pressionar reproduzir em sua cena depois de adicionar o MRTK ao seu projeto e ele não entrar no modo de reprodução, talvez seja necessário reiniciar o Unity.</span><span class="sxs-lookup"><span data-stu-id="e6009-142">Note: If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span> 

9. <span data-ttu-id="e6009-143">Com o objeto MixedRealityToolkit selecionado em sua hierarquia, clique em copiar e personalizar no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="e6009-143">With the MixedRealityToolkit object selected in your hierarchy, click Copy and Customize in the Inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="e6009-145">Também no painel Inspetor (com o objeto MixedRealityToolkit selecionado em sua hierarquia), desabilite o sistema de diagnóstico desmarcando a caixa à direita de habilitar o sistema de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="e6009-145">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. <span data-ttu-id="e6009-147">Para habilitar os comandos de voz, selecione o perfil MRTK recém-criado a ser personalizado.</span><span class="sxs-lookup"><span data-stu-id="e6009-147">To enable voice commands, select the newly created MRTK profile to customize.</span></span> <span data-ttu-id="e6009-148">Neste tutorial, estamos usando os comandos de fala de entrada para reconhecimento e transcrição de fala.</span><span class="sxs-lookup"><span data-stu-id="e6009-148">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="e6009-149">Vamos clonar o perfil de entrada para fazer alterações nas configurações de fala.</span><span class="sxs-lookup"><span data-stu-id="e6009-149">Lets clone the input profile to make changes to speech settings.</span></span>

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. <span data-ttu-id="e6009-152">Depois que o perfil de entrada for clonado, vá para comandos de fala e clone os comandos de fala.</span><span class="sxs-lookup"><span data-stu-id="e6009-152">Once the input profile is cloned, go to speech commands and clone the speech commands.</span></span>

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. <span data-ttu-id="e6009-155">Agora, em comandos de fala, vá para "configurações gerais" e defina "Iniciar comportamento" como "início manual"</span><span class="sxs-lookup"><span data-stu-id="e6009-155">Now under speech commands, go to "General Settings" and set "Start Behavior" to "Manual Start"</span></span>

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. <span data-ttu-id="e6009-157">No painel projeto, expanda a pasta Lunarcom e arraste Lunarcom_Base pré-fabricado para sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="e6009-157">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. <span data-ttu-id="e6009-159">Selecione o objeto Lunarcom_Base em sua hierarquia e verifique se a posição está definida como x = 0, y = 0 e z = 0, bem como a rotação definida como x = 0, y = 0 e z = 0.</span><span class="sxs-lookup"><span data-stu-id="e6009-159">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="e6009-160">Defina a escala como leitura x = 0.008, y = 0.008 e z = 0,01.</span><span class="sxs-lookup"><span data-stu-id="e6009-160">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="e6009-162">Clique em Adicionar componente e procure e selecione LunarcomController.</span><span class="sxs-lookup"><span data-stu-id="e6009-162">Click Add Component, and search for and select LunarcomController.</span></span> <span data-ttu-id="e6009-163">Esse script está incluído no pacote de ativos do Lunarcom que você importou na etapa 6.</span><span class="sxs-lookup"><span data-stu-id="e6009-163">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="e6009-165">Para conectar nosso aplicativo aos serviços cognitivas do Azure, você deve inserir uma chave de assinatura (também conhecida como chave de API) para o serviço de fala.</span><span class="sxs-lookup"><span data-stu-id="e6009-165">To connect our applicaiton to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="e6009-166">Siga as instruções [aqui](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) para obter uma chave de assinatura gratuita.</span><span class="sxs-lookup"><span data-stu-id="e6009-166">Follow the instructions at [here](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="e6009-167">Depois de obter a chave de assinatura, insira-a no campo chave de API do serviço de fala do componente LunarcomController no painel Inspetor, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="e6009-167">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

18. <span data-ttu-id="e6009-168">Insira a região que você escolheu ao se inscrever na chave de assinatura no campo região do serviço de fala do componente LunarcomController no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="e6009-168">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="e6009-169">Por exemplo, para o tipo de região "oeste dos EUA" em "westus"</span><span class="sxs-lookup"><span data-stu-id="e6009-169">For example, for the region "West US" type in "westus"</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="e6009-171">Em sua hierarquia, expanda o objeto Lunarcom_Base clicando na seta à esquerda dele.</span><span class="sxs-lookup"><span data-stu-id="e6009-171">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="e6009-172">Em seguida, faça o mesmo para seu objeto filho "terminal", conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="e6009-172">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="e6009-173">Enquanto Lunarcom_Base estiver selecionado, clique e arraste Lunarcom texto da hierarquia para o slot de texto de saída no componente LunarcomController no painel Inspetor, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="e6009-173">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

21. <span data-ttu-id="e6009-174">Faça a mesma coisa com o objeto de terminal no slot de terminal e no objeto de luz de conexão para o slot do controlador de luz de conexão.</span><span class="sxs-lookup"><span data-stu-id="e6009-174">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="e6009-176">Clique na seta ao lado da seção de botões Lunarcom do script LunarcomController no painel Inspetor e altere o tamanho para 3.</span><span class="sxs-lookup"><span data-stu-id="e6009-176">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="e6009-177">Pressione Enter ou Return.</span><span class="sxs-lookup"><span data-stu-id="e6009-177">Press Enter or Return.</span></span> <span data-ttu-id="e6009-178">Isso faz com que três novos campos de elemento sejam exibidos.</span><span class="sxs-lookup"><span data-stu-id="e6009-178">This causes three new Element fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="e6009-180">Expanda os botões Lunarcom clicando na seta ao lado dele em sua hierarquia e usando o mesmo processo acima, arraste o MIC, o satélite e o Rocket Gameobjects para o elemento 0, 1 e 2 referências, respectivamente, no componente LunarcomController no Painel de Inspetor.</span><span class="sxs-lookup"><span data-stu-id="e6009-180">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="e6009-182">Selecione o objeto Lunarcom_Base "em sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="e6009-182">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="e6009-183">Clique em Adicionar componente no painel Inspetor e procure e selecione LunarcomWakeWordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="e6009-183">Click Add Component in the inspector panel, and search for and select LunarcomWakeWordRecognizer.</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="e6009-185">No slot de palavra de ativação, digite ativar terminal.</span><span class="sxs-lookup"><span data-stu-id="e6009-185">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="e6009-186">No slot de palavras ignorar, digite fechar terminal.</span><span class="sxs-lookup"><span data-stu-id="e6009-186">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="e6009-188">Crie o aplicativo para seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="e6009-188">Build your application to your device</span></span>

1. <span data-ttu-id="e6009-189">Abra a janela configurações de compilação novamente indo para arquivo > configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="e6009-189">Open the build settings window again by going to File>Build Settings.</span></span>

![Lição 1 Chapter5 etapa 1](images/Lesson1Chapter5Step1.JPG)

2. <span data-ttu-id="e6009-191">Verifique se a cena que você deseja experimentar está na lista de "Cenas em Compilação", clicando no botão "Adicionar Cenas Abertas".</span><span class="sxs-lookup"><span data-stu-id="e6009-191">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="e6009-192">Pressione o botão Compilar para iniciar o processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="e6009-192">Press the Build button to begin the build process.</span></span>

![Lição 1 Chapter5 etapa 3](images/Lesson1Chapter5Step3.JPG)

4. <span data-ttu-id="e6009-194">Crie e dê um nome para uma nova pasta para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6009-194">Create and name a new folder for your application.</span></span> <span data-ttu-id="e6009-195">Na imagem abaixo, uma pasta com o nome "Aplicativo" foi criada para armazenar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6009-195">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="e6009-196">Clique em "Selecionar Pasta" para começar a compilar na pasta recém-criada.</span><span class="sxs-lookup"><span data-stu-id="e6009-196">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="e6009-197">Após a compilação, você pode fechar a janela "Configurações de Compilação" no Unity.</span><span class="sxs-lookup"><span data-stu-id="e6009-197">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 

![Lição 1 Chapter5 etapa 4](images/Lesson1Chapter5Step4.JPG)

> <span data-ttu-id="e6009-199">OBSERVAÇÃO: se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente.</span><span class="sxs-lookup"><span data-stu-id="e6009-199">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="e6009-200">Se você vir um erro, como "Erro: CS0246 = O nome do tipo ou do namespace ‘XX’ não pôde ser encontrado (não pode ser encontrado (está faltando uma diretiva using ou uma referência de assembly?) ", talvez precise instalar o [SDK do Windows 10 (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>).</span><span class="sxs-lookup"><span data-stu-id="e6009-200">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span>

5. <span data-ttu-id="e6009-201">Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6009-201">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="e6009-202">Clique duas vezes no arquivo de solução ". sln" para abrir o arquivo de solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6009-202">Double click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

> <span data-ttu-id="e6009-203">Observação: certifique-se de abrir a pasta recém-criada (ou seja, "Aplicativo", se estiver seguindo as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo .sln com nome semelhante fora dessa pasta que não deve ser confundido com o arquivo .sln dentro da pasta de compilação.</span><span class="sxs-lookup"><span data-stu-id="e6009-203">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lição1 Capítulo5 Etapa5](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="e6009-205">Observação: se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para garantir que todos os componentes necessários sejam instalados conforme especificado na [página "Instalar as ferramentas"](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="e6009-205">Note: If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

6. <span data-ttu-id="e6009-206">Conecte o HoloLens 2 ao computador usando o cabo USB.</span><span class="sxs-lookup"><span data-stu-id="e6009-206">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="e6009-207">Embora essas instruções pressuponham que você esteja implantando um teste com um dispositivo HoloLens 2, também é possível optar por implantar o [emulador do HoloLens 2](using-the-hololens-emulator.md) ou criar um [pacote do aplicativo para sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="e6009-207">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="e6009-208">Antes de compilar para seu dispositivo, verifique se ele está no Modo de Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="e6009-208">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="e6009-209">Se for a primeira vez que você implanta o HoloLens 2, o Visual Studio pode solicitar o emparelhamento do seu HoloLens 2 com um pin.</span><span class="sxs-lookup"><span data-stu-id="e6009-209">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="e6009-210">Siga [estas instruções](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se você precisar ativar o modo de desenvolvedor ou emparelhar com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6009-210">Please follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="e6009-211">Configure o Visual Studio para compilar seu HoloLens 2, selecionando a configuração "Versão" e a arquitetura "ARM".</span><span class="sxs-lookup"><span data-stu-id="e6009-211">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

![Lição 1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. <span data-ttu-id="e6009-213">A etapa final é compilar para seu dispositivo, selecionando Depurar > Iniciar sem Depuração.</span><span class="sxs-lookup"><span data-stu-id="e6009-213">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="e6009-214">Selecionar "Iniciar sem Depuração" fará com que o aplicativo inicie imediatamente em seu dispositivo após uma compilação bem-sucedida, mas sem exibir informações de Depuração no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6009-214">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="e6009-215">Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6009-215">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="e6009-216">Você também pode selecionar Compilação > Implantar Solução para implantar seu dispositivo sem iniciar o aplicativo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e6009-216">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

![Lição 1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a><span data-ttu-id="e6009-218">Parabéns</span><span class="sxs-lookup"><span data-stu-id="e6009-218">Congratulations</span></span>

<span data-ttu-id="e6009-219">Você configurou o reconhecimento de voz em seu aplicativo, da plataforma Azure.</span><span class="sxs-lookup"><span data-stu-id="e6009-219">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="e6009-220">Execute o aplicativo para garantir que todas as funções e recursos estejam funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="e6009-220">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="e6009-221">Comece dizendo a palavra de ativação que você digitou na etapa 22, ativar terminal.</span><span class="sxs-lookup"><span data-stu-id="e6009-221">Start with saying the wake word you typed in Step 22, Activate Terminal.</span></span> <span data-ttu-id="e6009-222">Selecione o botão de microfone para iniciar o reconhecimento de voz.</span><span class="sxs-lookup"><span data-stu-id="e6009-222">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="e6009-223">Comece a falar.</span><span class="sxs-lookup"><span data-stu-id="e6009-223">Begin speaking.</span></span> <span data-ttu-id="e6009-224">Você verá suas palavras transcritas no terminal enquanto fala.</span><span class="sxs-lookup"><span data-stu-id="e6009-224">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="e6009-225">Pressione o botão de microfone uma segunda vez para parar o reconhecimento de voz.</span><span class="sxs-lookup"><span data-stu-id="e6009-225">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="e6009-226">Diga ignorar terminal para ocultar o terminal Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="e6009-226">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="e6009-227">Na próxima lição, aprenderemos como alternar dinamicamente para usar o reconhecimento de voz alimentada por dispositivo em situações em que o SDK de fala do Azure não está disponível devido ao HoloLens 2 estar offline.</span><span class="sxs-lookup"><span data-stu-id="e6009-227">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="e6009-228">Próximo tutorial: 2. Adicionar um modo offline para tradução de fala em texto local</span><span class="sxs-lookup"><span data-stu-id="e6009-228">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)


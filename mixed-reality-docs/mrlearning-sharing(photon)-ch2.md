<span data-ttu-id="c082a-101">**Preparando para o desenvolvimento do Unity**</span><span class="sxs-lookup"><span data-stu-id="c082a-101">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="c082a-102">Nesta lição, vamos aprenderá como preparar e configurar o Unity para desenvolvimento de aplicativos, incluindo importando o Kit de ferramentas de realidade misturada, definindo as configurações de compilação e preparando nossa cena.</span><span class="sxs-lookup"><span data-stu-id="c082a-102">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="c082a-103">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="c082a-103">Objectives:</span></span>

- <span data-ttu-id="c082a-104">Configurar o Unity para desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="c082a-104">Configure Unity for app development</span></span>

- <span data-ttu-id="c082a-105">Importe o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c082a-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="c082a-106">Preparar sua cena do projeto</span><span class="sxs-lookup"><span data-stu-id="c082a-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="c082a-107">Instruções</span><span class="sxs-lookup"><span data-stu-id="c082a-107">Instructions</span></span>

1. <span data-ttu-id="c082a-108">Baixe e salve o pacote do Kit de ferramentas de realidade misturada unity clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="c082a-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="c082a-109">No Unity, clique no menu de ativos e selecione "Importar pacote", clique em "Pacote personalizado".</span><span class="sxs-lookup"><span data-stu-id="c082a-109">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="c082a-111">Selecione o pacote do Unity que você acabou de baixar o link fornecido na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="c082a-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="c082a-112">Quando aparece a janela pop-up da importação no Unity, clique no botão Importar para começar a importar.</span><span class="sxs-lookup"><span data-stu-id="c082a-112">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="c082a-113">Importar o MRTK pode levar vários minutos.</span><span class="sxs-lookup"><span data-stu-id="c082a-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="c082a-115">Observação: O pacote baixado será em sua pasta local onde você salvou o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c082a-115">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="c082a-116">A imagem acima não apresentação para onde você encontrará o pacote.</span><span class="sxs-lookup"><span data-stu-id="c082a-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="c082a-117">Crie uma nova cena (Isso pode ser feito clicando em "file" e selecionando "nova cena").</span><span class="sxs-lookup"><span data-stu-id="c082a-117">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="c082a-118">Salve a cena como "HLSharedProjectMain".</span><span class="sxs-lookup"><span data-stu-id="c082a-118">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="c082a-119">Observação: você pode receber um pop-up que é semelhante à imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="c082a-119">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="c082a-120">Por enquanto, basta clicar em "não".</span><span class="sxs-lookup"><span data-stu-id="c082a-120">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="c082a-122">Em, clique em "Toolkit de realidade mista" em "Adicionar à cena e configurar".</span><span class="sxs-lookup"><span data-stu-id="c082a-122">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="c082a-124">Assim que estiver concluído, um novo arquivo de configuração será exibida, oferecendo a opção para personalizar o perfil.</span><span class="sxs-lookup"><span data-stu-id="c082a-124">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="c082a-125">Clique em "copiar e personalizar."</span><span class="sxs-lookup"><span data-stu-id="c082a-125">Click "copy and customize."</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="c082a-129">Role para baixo e desmarque a opção "Habilitar sistema de diagnóstico" Se você quiser ocultar a janela de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="c082a-129">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="c082a-130">É recomendável manter a janela de diagnóstico habilitados durante o desenvolvimento de aplicativo para monitorar o desempenho e desabilitá-lo durante as demonstrações de produção ou de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c082a-130">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="c082a-132">Abra as configurações de build, pressionando CTRL + shift + B ou indo para arquivo > configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="c082a-132">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="c082a-133">Observe que o programa está atualmente definido na plataforma "PC, Mac e Linux autônomo".</span><span class="sxs-lookup"><span data-stu-id="c082a-133">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="c082a-134">Para o desenvolvimento de 2 HoloLens, definir a plataforma para ser "Plataforma Universal do Windows."</span><span class="sxs-lookup"><span data-stu-id="c082a-134">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="c082a-135">Selecione-o e clique em "alternar plataforma".</span><span class="sxs-lookup"><span data-stu-id="c082a-135">Select it and click "switch platform."</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="c082a-137">Uma vez concluído, clique na caixa que diz "Adicionar cenas abertas".</span><span class="sxs-lookup"><span data-stu-id="c082a-137">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="c082a-138">Agora, vá para o painel do Inspetor e certifique-se de que a caixa de seleção à direita de "suportada de realidade virtual" (conforme mostrado na imagem abaixo) é verificada.</span><span class="sxs-lookup"><span data-stu-id="c082a-138">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="c082a-139">Também Certifique-se de que a caixa de seleção ao lado de "cenas/HLSharedProjectMain" também é verificada, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="c082a-139">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="c082a-141">Sob as "configurações de publicação" seção de rolagem do painel de inspetor para baixo até "Recursos" e certifique-se de que as seguintes caixas de seleção são marcadas:</span><span class="sxs-lookup"><span data-stu-id="c082a-141">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="c082a-143">Importar o pacote personalizado chamado "SharingAssetCollection", que pode ser baixado [aqui.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="c082a-143">Import the custom package called "SharingAssetCollection" which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="c082a-144">Agora, no painel de projeto, vá para a pasta "pré-fabricados", já que nas próximas etapas você irá implementar alguns pré-fabricados na cena.</span><span class="sxs-lookup"><span data-stu-id="c082a-144">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="c082a-145">Na pasta "pré-fabricados", clique e arraste pré-fabricado, "DebugWindow" na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="c082a-145">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="c082a-146">Quando terminar, salve o projeto (clique em arquivo, em seguida, salvar, ou pressione CTRL + S)</span><span class="sxs-lookup"><span data-stu-id="c082a-146">Once finished, save the project (click file, then save, or press control+S)</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="c082a-148">Observação: Você pode perceber um pop-up são exibidas à medida que você clicar no pré-fabricado, solicitando que você sobre o Essentials TMP.</span><span class="sxs-lookup"><span data-stu-id="c082a-148">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="c082a-149">Clique em "Importar TMP Essentials" como eles serão necessários.</span><span class="sxs-lookup"><span data-stu-id="c082a-149">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="c082a-150">Se essa janela pop-up aparecer, você talvez precise excluir pré-fabricado da sua hierarquia e arraste-o novamente na sua hierarquia para evitar possíveis erros relacionados ao texto.</span><span class="sxs-lookup"><span data-stu-id="c082a-150">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="c082a-152">Parabéns</span><span class="sxs-lookup"><span data-stu-id="c082a-152">Congratulations</span></span>

<span data-ttu-id="c082a-153">Seu projeto do Unity agora está pronto para Photon!</span><span class="sxs-lookup"><span data-stu-id="c082a-153">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="c082a-154">Nas próximas lições, vamos compilar após esta cena e nosso projeto do Unity em direção uma experiência completa de compartilhado.</span><span class="sxs-lookup"><span data-stu-id="c082a-154">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="c082a-155">[Próxima lição: Sharing(Photon) lição 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="c082a-155">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>


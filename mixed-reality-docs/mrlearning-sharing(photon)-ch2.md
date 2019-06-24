---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326504"
---
# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="46afe-104">**Preparando para o desenvolvimento do Unity**</span><span class="sxs-lookup"><span data-stu-id="46afe-104">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="46afe-105">Nesta lição, vamos aprenderá como preparar e configurar o Unity para desenvolvimento de aplicativos, incluindo importando o Kit de ferramentas de realidade misturada, definindo as configurações de compilação e preparando nossa cena.</span><span class="sxs-lookup"><span data-stu-id="46afe-105">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="46afe-106">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="46afe-106">Objectives:</span></span>

- <span data-ttu-id="46afe-107">Configurar o Unity para desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="46afe-107">Configure Unity for app development</span></span>

- <span data-ttu-id="46afe-108">Importe o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="46afe-108">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="46afe-109">Preparar sua cena do projeto</span><span class="sxs-lookup"><span data-stu-id="46afe-109">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="46afe-110">Instruções</span><span class="sxs-lookup"><span data-stu-id="46afe-110">Instructions</span></span>

1. <span data-ttu-id="46afe-111">Baixe e salve o pacote do Kit de ferramentas de realidade misturada unity clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="46afe-111">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span></span>
2. <span data-ttu-id="46afe-112">No Unity, clique no menu de ativos e selecione "Importar pacote", clique em "Pacote personalizado".</span><span class="sxs-lookup"><span data-stu-id="46afe-112">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="46afe-114">Selecione o pacote do Unity que você acabou de baixar o link fornecido na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="46afe-114">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="46afe-115">Quando aparece a janela pop-up da importação no Unity, clique no botão Importar para começar a importar.</span><span class="sxs-lookup"><span data-stu-id="46afe-115">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="46afe-116">Importar o MRTK pode levar vários minutos.</span><span class="sxs-lookup"><span data-stu-id="46afe-116">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="46afe-118">Observação: O pacote baixado será em sua pasta local onde você salvou o arquivo.</span><span class="sxs-lookup"><span data-stu-id="46afe-118">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="46afe-119">A imagem acima não apresentação para onde você encontrará o pacote.</span><span class="sxs-lookup"><span data-stu-id="46afe-119">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="46afe-120">Crie uma nova cena (Isso pode ser feito clicando em "file" e selecionando "nova cena").</span><span class="sxs-lookup"><span data-stu-id="46afe-120">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="46afe-121">Salve a cena como "HLSharedProjectMain".</span><span class="sxs-lookup"><span data-stu-id="46afe-121">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="46afe-122">Observação: você pode receber um pop-up que é semelhante à imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="46afe-122">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="46afe-123">Por enquanto, basta clicar em "não".</span><span class="sxs-lookup"><span data-stu-id="46afe-123">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="46afe-125">Em, clique em "Toolkit de realidade mista" em "Adicionar à cena e configurar".</span><span class="sxs-lookup"><span data-stu-id="46afe-125">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="46afe-127">Assim que estiver concluído, um novo arquivo de configuração será exibida, oferecendo a opção para personalizar o perfil.</span><span class="sxs-lookup"><span data-stu-id="46afe-127">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="46afe-128">Clique em "copiar e personalizar."</span><span class="sxs-lookup"><span data-stu-id="46afe-128">Click "copy and customize."</span></span>

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. <span data-ttu-id="46afe-130">Role para baixo e desmarque a opção "Habilitar sistema de diagnóstico" Se você quiser ocultar a janela de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="46afe-130">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="46afe-131">É recomendável manter a janela de diagnóstico habilitados durante o desenvolvimento de aplicativo para monitorar o desempenho e desabilitá-lo durante as demonstrações de produção ou de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="46afe-131">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span>

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. <span data-ttu-id="46afe-133">Abra as configurações de build, pressionando CTRL + shift + B ou indo para arquivo > configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="46afe-133">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="46afe-134">Observe que o programa está atualmente definido na plataforma "PC, Mac e Linux autônomo".</span><span class="sxs-lookup"><span data-stu-id="46afe-134">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="46afe-135">Para o desenvolvimento de 2 HoloLens, definir a plataforma para ser "Plataforma Universal do Windows."</span><span class="sxs-lookup"><span data-stu-id="46afe-135">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="46afe-136">Selecione-o e clique em "alternar plataforma".</span><span class="sxs-lookup"><span data-stu-id="46afe-136">Select it and click "switch platform."</span></span>

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. <span data-ttu-id="46afe-138">Uma vez concluído, clique na caixa que diz "Adicionar cenas abertas".</span><span class="sxs-lookup"><span data-stu-id="46afe-138">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="46afe-139">Agora, vá para o painel do Inspetor e certifique-se de que a caixa de seleção à direita de "suportada de realidade virtual" (conforme mostrado na imagem abaixo) é verificada.</span><span class="sxs-lookup"><span data-stu-id="46afe-139">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="46afe-140">Também Certifique-se de que a caixa de seleção ao lado de "cenas/HLSharedProjectMain" também é verificada, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="46afe-140">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. <span data-ttu-id="46afe-142">Sob as "configurações de publicação" seção de rolagem do painel de inspetor para baixo até "Recursos" e certifique-se de que as seguintes caixas de seleção são marcadas:</span><span class="sxs-lookup"><span data-stu-id="46afe-142">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>
    - <span data-ttu-id="46afe-143">cliente da Internet</span><span class="sxs-lookup"><span data-stu-id="46afe-143">internet client</span></span>
       
       - <span data-ttu-id="46afe-144">servidor de cliente da Internet</span><span class="sxs-lookup"><span data-stu-id="46afe-144">internet client server</span></span>
       
       - <span data-ttu-id="46afe-145">servidor de cliente de rede privada</span><span class="sxs-lookup"><span data-stu-id="46afe-145">private network client server</span></span>
   
       - <span data-ttu-id="46afe-146">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="46afe-146">camera/webcam</span></span>

       - <span data-ttu-id="46afe-147">Microfone</span><span class="sxs-lookup"><span data-stu-id="46afe-147">microphone</span></span>
   
   11. <span data-ttu-id="46afe-148">Importe o pacote personalizado chamado "Da lição 2", que pode ser baixado aqui.</span><span class="sxs-lookup"><span data-stu-id="46afe-148">Import the custom package called "Lesson2" which can be downloaded here.</span></span> <span data-ttu-id="46afe-149">TODO: Forneça um link para o pacote de ativos.</span><span class="sxs-lookup"><span data-stu-id="46afe-149">TODO: Provide link to asset pack.</span></span>
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. <span data-ttu-id="46afe-151">Agora, no painel de projeto, vá para a pasta "pré-fabricados", já que nas próximas etapas você irá implementar alguns pré-fabricados na cena.</span><span class="sxs-lookup"><span data-stu-id="46afe-151">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="46afe-152">Na pasta "pré-fabricados", clique e arraste pré-fabricado, "DebugWindow" na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="46afe-152">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="46afe-153">Quando terminar, salve o projeto (clique em arquivo, em seguida, salvar, ou pressione CTRL + S)</span><span class="sxs-lookup"><span data-stu-id="46afe-153">Once finished, save the project (click file, then save, or press control+S)</span></span>
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > <span data-ttu-id="46afe-155">Observação: Você pode perceber um pop-up são exibidas à medida que você clicar no pré-fabricado, solicitando que você sobre o Essentials TMP.</span><span class="sxs-lookup"><span data-stu-id="46afe-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="46afe-156">Clique em "Importar TMP Essentials" como eles serão necessários.</span><span class="sxs-lookup"><span data-stu-id="46afe-156">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="46afe-157">Se essa janela pop-up aparecer, você talvez precise excluir pré-fabricado da sua hierarquia e arraste-o novamente na sua hierarquia para evitar possíveis erros relacionados ao texto.</span><span class="sxs-lookup"><span data-stu-id="46afe-157">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="46afe-159">Parabéns</span><span class="sxs-lookup"><span data-stu-id="46afe-159">Congratulations</span></span>

<span data-ttu-id="46afe-160">Seu projeto do Unity agora está pronto para Photon!</span><span class="sxs-lookup"><span data-stu-id="46afe-160">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="46afe-161">Nas próximas lições, vamos compilar após esta cena e nosso projeto do Unity em direção uma experiência completa de compartilhado.</span><span class="sxs-lookup"><span data-stu-id="46afe-161">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="46afe-162">[Próxima lição: Sharing(Photon) lição 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="46afe-162">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>


---
title: Tutoriais de funcionalidades de vários usuários-2. Obtendo o Unity pronto para desenvolvimento
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 9d42811157db108baad51eab3f367a06a11b7f7b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701974"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="8cd6a-105">2. Obtendo o Unity pronto para desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="8cd6a-105">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="8cd6a-106">Neste tutorial, aprendemos como preparar e configurar o Unity para o desenvolvimento de aplicativos, incluindo a importação do kit de ferramentas de realidade misturada, a definição de configurações de compilação e a preparação de nossa cena.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-106">In this tutorial, we learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="8cd6a-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8cd6a-107">Objectives</span></span>

- <span data-ttu-id="8cd6a-108">Configurar o Unity para o desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="8cd6a-108">Configure Unity for application development</span></span>

- <span data-ttu-id="8cd6a-109">Importe o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="8cd6a-109">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="8cd6a-110">Preparar a cena do projeto</span><span class="sxs-lookup"><span data-stu-id="8cd6a-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="8cd6a-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="8cd6a-111">Instructions</span></span>

1. <span data-ttu-id="8cd6a-112">Baixe e salve o pacote da Unity do kit de ferramentas da realidade mista clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="8cd6a-112">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="8cd6a-113">No Unity, clique no menu ativos e selecione Importar pacote e, em seguida, clique em pacote personalizado.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-113">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="8cd6a-115">Selecione o pacote do Unity que você acabou de baixar do link fornecido na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="8cd6a-116">Depois que a janela pop-up importar aparecer no Unity, clique no botão importar para começar a importação.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-116">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="8cd6a-117">A importação do MRTK pode levar vários minutos.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-117">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="8cd6a-119">Observação: O pacote baixado está na pasta local em que você salvou o arquivo.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-119">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="8cd6a-120">A imagem acima não retrata onde você encontrará o pacote.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="8cd6a-121">Crie uma nova cena.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-121">Create a new scene.</span></span> <span data-ttu-id="8cd6a-122">Isso pode ser feito clicando em arquivo e selecionando nova cena ").</span><span class="sxs-lookup"><span data-stu-id="8cd6a-122">This can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="8cd6a-123">Salve a cena como HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-123">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="8cd6a-124">Observação: você pode receber um pop-up parecido com a imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-124">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="8cd6a-125">Por enquanto, clique em não.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-125">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="8cd6a-127">Em kit de ferramentas de realidade mista, clique em Adicionar à cena e configurar.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="8cd6a-129">Quando isso for concluído, um novo arquivo de configuração será exibido, dando a você a opção de personalizar o perfil.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="8cd6a-130">Clique em copiar e personalizar.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-130">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="8cd6a-134">Role para baixo e desmarque Habilitar o sistema de diagnóstico se desejar ocultar a janela de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-134">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="8cd6a-135">É recomendável manter a janela de diagnóstico habilitada durante o desenvolvimento do aplicativo para monitorar o desempenho e desabilitá-lo durante as demonstrações de produção ou de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-135">We recommend keeping the diagnostics window enabled during application development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="8cd6a-137">Abra as configurações de Build pressionando Control + Shift + B ou indo para arquivo-> configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-137">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="8cd6a-138">Observe que o programa está definido atualmente na plataforma autônoma de PC, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-138">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="8cd6a-139">Para o desenvolvimento do HoloLens 2, defina a plataforma como Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-139">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="8cd6a-140">Selecione-o e clique em alternar plataforma.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-140">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="8cd6a-142">Após a conclusão, clique na caixa que diz adicionar cenas abertas.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-142">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="8cd6a-143">Agora, acesse o painel Inspetor e verifique se a caixa de seleção à direita da realidade virtual com suporte (conforme mostrado na imagem abaixo) está marcada.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-143">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="8cd6a-144">Verifique também se a caixa de seleção ao lado de cenas/HLSharedProjectMain também está marcada, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-144">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="8cd6a-146">Na seção Configurações de publicação no painel Inspetor, role para baixo até recursos e verifique se as seguintes caixas de seleção estão marcadas:</span><span class="sxs-lookup"><span data-stu-id="8cd6a-146">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="8cd6a-148">Importe o pacote personalizado chamado SharingAssetCollection, que pode ser baixado [aqui.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="8cd6a-148">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="8cd6a-150">No painel projeto, vá para a pasta pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-150">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="8cd6a-151">Nas próximas etapas, você implementará alguns pré-fabricados na cena.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-151">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="8cd6a-152">Na pasta pré-fabricados, clique e arraste a janela pré-fabricado, depurar para a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-152">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="8cd6a-153">Quando terminar, salve o projeto clicando em arquivo e, em seguida, salve ou pressione Control + S.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-153">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="8cd6a-155">Observação: Você pode observar que um pop-up aparece ao clicar no pré-fabricado, solicitando-lhe informações sobre o TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="8cd6a-156">Clique em importar o TMP Essentials conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-156">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="8cd6a-157">Se essa janela pop-up for exibida, talvez seja necessário excluir o pré-fabricado de sua hierarquia e arrastá-lo novamente para a hierarquia para evitar possíveis erros relacionados a texto.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-157">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="8cd6a-159">Parabéns</span><span class="sxs-lookup"><span data-stu-id="8cd6a-159">Congratulations</span></span>

<span data-ttu-id="8cd6a-160">Seu projeto de Unity agora está pronto para Photon.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-160">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="8cd6a-161">Nos próximos tutoriais, vamos criar essa cena e nosso projeto de Unity em direção a uma experiência compartilhada completa.</span><span class="sxs-lookup"><span data-stu-id="8cd6a-161">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="8cd6a-162">[Próximo tutorial: 3. Conectar vários usuários](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="8cd6a-162">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>


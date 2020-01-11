---
title: Tutoriais de funcionalidades de vários usuários-2. Obtendo o Unity pronto para desenvolvimento
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 6abf4fa8fc87afc7007d6f7c76becfbd88ed7a12
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901513"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="4520f-105">2. obtendo o Unity pronto para desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="4520f-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="4520f-106">Neste tutorial, você aprenderá a preparar e configurar o Unity para o desenvolvimento de aplicativos, incluindo a importação do kit de ferramentas de realidade mista, a definição de configurações de compilação e a preparação de sua cena.</span><span class="sxs-lookup"><span data-stu-id="4520f-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="4520f-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4520f-107">Objectives</span></span>

* <span data-ttu-id="4520f-108">Configurar o Unity para o desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="4520f-108">Configure Unity for application development</span></span>
* <span data-ttu-id="4520f-109">Importe o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="4520f-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="4520f-110">Preparar a cena do projeto</span><span class="sxs-lookup"><span data-stu-id="4520f-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="4520f-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="4520f-111">Instructions</span></span>

1. <span data-ttu-id="4520f-112">Baixe e salve o pacote do kit de ferramentas da realidade do infigurador do Foundationity, clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="4520f-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="4520f-113">No Unity, clique no menu ativos e selecione Importar pacote e, em seguida, clique em pacote personalizado.</span><span class="sxs-lookup"><span data-stu-id="4520f-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="4520f-115">Selecione o pacote do Unity que você acabou de baixar do link fornecido na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="4520f-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="4520f-116">Depois que a janela pop-up importar aparecer no Unity, clique no botão importar para começar a importar o MRTK.</span><span class="sxs-lookup"><span data-stu-id="4520f-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="4520f-117">Isso pode levar vários minutos.</span><span class="sxs-lookup"><span data-stu-id="4520f-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="4520f-119">O pacote baixado está em sua pasta local, em que você salvou o arquivo.</span><span class="sxs-lookup"><span data-stu-id="4520f-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="4520f-120">A imagem acima não retrata onde você encontrará o pacote.</span><span class="sxs-lookup"><span data-stu-id="4520f-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="4520f-121">Crie uma nova cena.</span><span class="sxs-lookup"><span data-stu-id="4520f-121">Create a new scene.</span></span> <span data-ttu-id="4520f-122">Isso pode ser feito clicando em arquivo e selecionando nova cena ".</span><span class="sxs-lookup"><span data-stu-id="4520f-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="4520f-123">Salve-o como HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="4520f-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="4520f-124">Você pode receber um pop-up parecido com a imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="4520f-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="4520f-125">Por enquanto, clique em não.</span><span class="sxs-lookup"><span data-stu-id="4520f-125">For now, click No.</span></span>
    <span data-ttu-id="4520f-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="4520f-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="4520f-127">Em kit de ferramentas de realidade mista, clique em Adicionar à cena e configurar.</span><span class="sxs-lookup"><span data-stu-id="4520f-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="4520f-129">Quando isso for concluído, um novo arquivo de configuração será exibido, dando a você a opção de personalizar o perfil.</span><span class="sxs-lookup"><span data-stu-id="4520f-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="4520f-131">Selecione MRTK (Kit de ferramentas de realidade mista) na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="4520f-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="4520f-132">No painel Inspetor, procure o script Mixed Reality Toolkit e pressione o botão "copiar & Personalizar", conforme mostrado na figura abaixo.</span><span class="sxs-lookup"><span data-stu-id="4520f-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="4520f-133">Um pop aparecerá depois dessa e selecione a opção clonar no menu pop-up.</span><span class="sxs-lookup"><span data-stu-id="4520f-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="4520f-136">Role para baixo e desmarque Habilitar o sistema de diagnóstico se desejar ocultar a janela de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="4520f-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="4520f-137">É recomendável manter a janela de diagnóstico habilitada durante o desenvolvimento do aplicativo para monitorar o desempenho e, em seguida, desabilitá-lo durante as demonstrações de produção ou de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4520f-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="4520f-139">Abra as configurações de Build pressionando Control + Shift + B ou indo para arquivo-> configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="4520f-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="4520f-140">Observe que o programa está definido atualmente na plataforma autônoma de PC, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="4520f-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="4520f-141">Para o desenvolvimento do HoloLens 2, defina a plataforma como Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="4520f-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="4520f-142">Selecione-o e clique em alternar plataforma.</span><span class="sxs-lookup"><span data-stu-id="4520f-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="4520f-144">Após a conclusão, clique na caixa chamada Add Open bastidores.</span><span class="sxs-lookup"><span data-stu-id="4520f-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="4520f-145">Agora, acesse o painel Inspetor e verifique se a caixa de seleção à direita da realidade virtual com suporte (conforme mostrado na imagem abaixo) está marcada.</span><span class="sxs-lookup"><span data-stu-id="4520f-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="4520f-146">Verifique também se a caixa de seleção ao lado de cenas/HLSharedProjectMain também está marcada, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="4520f-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="4520f-148">Na seção Configurações de publicação no painel Inspetor, role para baixo até recursos e verifique se as seguintes caixas de seleção estão marcadas:</span><span class="sxs-lookup"><span data-stu-id="4520f-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="4520f-150">Importe os pacotes personalizados listados:</span><span class="sxs-lookup"><span data-stu-id="4520f-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="4520f-151">a.</span><span class="sxs-lookup"><span data-stu-id="4520f-151">a.</span></span> <span data-ttu-id="4520f-152">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versão 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="4520f-152">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>

    <span data-ttu-id="4520f-153">b.</span><span class="sxs-lookup"><span data-stu-id="4520f-153">b.</span></span> [<span data-ttu-id="4520f-154">MRTK. HoloLens2. Unity. tutoriais. assets. GettingStarted. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="4520f-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)

    <span data-ttu-id="4520f-155">c.</span><span class="sxs-lookup"><span data-stu-id="4520f-155">c.</span></span> [<span data-ttu-id="4520f-156">MRTK. HoloLens2. Unity. tutoriais. assets. AzureSpatialAnchors. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="4520f-156">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

    <span data-ttu-id="4520f-157">d.</span><span class="sxs-lookup"><span data-stu-id="4520f-157">d.</span></span> [<span data-ttu-id="4520f-158">MRTK. HoloLens2. Unity. tutoriais. assets. MultiUserCapabilities. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="4520f-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="4520f-159">Para um lembrete sobre como configurar um projeto do Unity para âncoras espaciais do Azure, você pode consultar o tutorial [introdução ao Azure Spatial ancoras](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) que faz parte da série de tutoriais de [âncoras espaciais do Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) .</span><span class="sxs-lookup"><span data-stu-id="4520f-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="4520f-161">No painel projeto, vá para a pasta pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="4520f-161">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="4520f-162">Nas etapas a seguir, você implementará algumas pré-fabricados na cena.</span><span class="sxs-lookup"><span data-stu-id="4520f-162">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="4520f-163">Na pasta pré-fabricados, clique e arraste a janela pré-fabricado, depurar para a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="4520f-163">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="4520f-164">Quando terminar, salve o projeto clicando em arquivo e, em seguida, salve ou pressione Control + S.</span><span class="sxs-lookup"><span data-stu-id="4520f-164">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="4520f-166">Você pode observar que um pop-up aparece ao clicar no pré-fabricado, solicitando-lhe informações sobre o TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="4520f-166">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="4520f-167">Clique em importar o TMP Essentials conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="4520f-167">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="4520f-168">Se essa janela pop-up for exibida, talvez seja necessário excluir o pré-fabricado de sua hierarquia e arrastá-lo novamente para a hierarquia para evitar possíveis erros relacionados a texto.</span><span class="sxs-lookup"><span data-stu-id="4520f-168">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="4520f-170">Parabéns</span><span class="sxs-lookup"><span data-stu-id="4520f-170">Congratulations</span></span>

<span data-ttu-id="4520f-171">Seu projeto de Unity agora está pronto para Photon.</span><span class="sxs-lookup"><span data-stu-id="4520f-171">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="4520f-172">Nos próximos tutoriais, vamos criar essa cena e nosso projeto de Unity em direção a uma experiência compartilhada completa.</span><span class="sxs-lookup"><span data-stu-id="4520f-172">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="4520f-173">[Próximo tutorial: 3. conectando vários usuários](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="4520f-173">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

---
title: Tutoriais de recursos multiusuário – 2. Preparar o Unity para o desenvolvimento
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031235"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="45534-105">2. Preparar o Unity para o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="45534-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="45534-106">Neste tutorial, você aprenderá a preparar e configurar o Unity para o desenvolvimento de aplicativos, incluindo importar o Mixed Reality Toolkit, definir as configurações de build e preparar sua cena.</span><span class="sxs-lookup"><span data-stu-id="45534-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="45534-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="45534-107">Objectives</span></span>

* <span data-ttu-id="45534-108">Configurar o Unity para o desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="45534-108">Configure Unity for application development</span></span>
* <span data-ttu-id="45534-109">Importe o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="45534-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="45534-110">Preparar a cena do projeto</span><span class="sxs-lookup"><span data-stu-id="45534-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="45534-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="45534-111">Instructions</span></span>

1. <span data-ttu-id="45534-112">Baixe e salve o pacote do Unity de Fundação do Mixed Reality Toolkit clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="45534-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="45534-113">No Unity, clique no menu Ativos e selecione Importar Pacote, então clique em Pacote Personalizado.</span><span class="sxs-lookup"><span data-stu-id="45534-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="45534-115">Selecione o pacote do Unity que você acabou de baixar do link fornecido na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="45534-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="45534-116">Depois que a janela pop-up importar aparecer no Unity, clique no botão Importar para começar a importar o MRTK.</span><span class="sxs-lookup"><span data-stu-id="45534-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="45534-117">Isso pode levar vários minutos.</span><span class="sxs-lookup"><span data-stu-id="45534-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="45534-119">O pacote baixado está em pasta local em que você salvou o arquivo.</span><span class="sxs-lookup"><span data-stu-id="45534-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="45534-120">A imagem acima não retrata o local em que você encontrará o pacote.</span><span class="sxs-lookup"><span data-stu-id="45534-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="45534-121">Depois que o pacote tiver sido importado, a janela Configurador de Projeto do MRTK deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="45534-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="45534-122">Se ele não aparecer, abra-o selecionando Mixed Reality Toolkit > Utilitários > Configurar Projeto do Unity no menu Unity.</span><span class="sxs-lookup"><span data-stu-id="45534-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="45534-123">Na janela Configurador de Projeto do MRTK, expanda a seção Modificar Configurações, desmarque a caixa de seleção Habilitar MSBuild para Unity, verifique se todas as outras opções estão marcadas e clique no botão Aplicar para aplicar as configurações.</span><span class="sxs-lookup"><span data-stu-id="45534-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="45534-125">O MSBuild para Unity pode não ser compatível com todos os SDKs que você usará e pode ser complicado desabilitá-lo depois que ele tiver sido habilitado.</span><span class="sxs-lookup"><span data-stu-id="45534-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="45534-126">Consequentemente, é altamente recomendável não habilitar o MSBuild para o Unity.</span><span class="sxs-lookup"><span data-stu-id="45534-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="45534-127">Crie uma cena.</span><span class="sxs-lookup"><span data-stu-id="45534-127">Create a new scene.</span></span> <span data-ttu-id="45534-128">Isso pode ser feito clicando em Arquivo e selecionando Nova Cena.</span><span class="sxs-lookup"><span data-stu-id="45534-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="45534-129">Salve-o como HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="45534-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="45534-130">Em Mixed Reality Toolkit, clique em Adicionar à Cena e Configurar.</span><span class="sxs-lookup"><span data-stu-id="45534-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="45534-132">Quando isso for concluído, selecione MRTK (Mixed Reality Toolkit) na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="45534-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="45534-133">No painel Inspetor, altere o perfil de configuração MRTK para DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="45534-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="45534-135">Selecione o MRTK (Mixed Reality Toolkit) da hierarquia.</span><span class="sxs-lookup"><span data-stu-id="45534-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="45534-136">No painel do inspetor, procure o Script do Mixed Reality Toolkit e pressione o botão "Copiar e Personalizar", como mostra a figura abaixo.</span><span class="sxs-lookup"><span data-stu-id="45534-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="45534-137">Um pop aparecerá depois disso. Selecione a opção Clonar no menu pop-up.</span><span class="sxs-lookup"><span data-stu-id="45534-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="45534-140">Role para baixo e desmarque Habilitar Sistema de Diagnóstico se você quiser ocultar a janela de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="45534-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="45534-141">É recomendável manter a janela de diagnóstico habilitada durante o desenvolvimento do aplicativo para monitorar o desempenho e, em seguida, desabilitá-la durante as demonstrações de produção ou de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45534-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="45534-143">Abra as configurações de build pressionando Control+Shift+B ou acessando Arquivo->Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="45534-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="45534-144">Observe que o programa está definido atualmente na plataforma autônoma de PC, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="45534-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="45534-145">Para o desenvolvimento do HoloLens 2, defina a plataforma como Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="45534-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="45534-146">Selecione-a e clique em alternar plataforma.</span><span class="sxs-lookup"><span data-stu-id="45534-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="45534-148">Após a conclusão, clique na caixa chamada Adicionar Cenas Abertas.</span><span class="sxs-lookup"><span data-stu-id="45534-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="45534-149">Agora, acesse o painel Inspetor e verifique se a caixa de seleção à direita de Realidade Virtual Compatível (conforme mostra a imagem abaixo) está marcada.</span><span class="sxs-lookup"><span data-stu-id="45534-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="45534-150">Verifique também se a caixa de seleção ao lado de cenas/HLSharedProjectMain também está marcada, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="45534-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="45534-152">Na seção Configurações de Publicação no painel Inspetor, role para baixo até Funcionalidades e verifique se as seguintes caixas de seleção estão marcadas:</span><span class="sxs-lookup"><span data-stu-id="45534-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="45534-154">Importe os pacotes personalizados listados:</span><span class="sxs-lookup"><span data-stu-id="45534-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="45534-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versão 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="45534-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="45534-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="45534-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="45534-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="45534-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="45534-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="45534-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="45534-159">Para um lembrete sobre como configurar um projeto do Unity para Âncoras Espaciais do Azure, veja o tutorial [Introdução às Âncoras Espaciais do Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) que faz parte da série de tutoriais [Âncoras Espaciais do Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1).</span><span class="sxs-lookup"><span data-stu-id="45534-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="45534-160">No painel Projeto, vá para a pasta Pré-Fabricados.</span><span class="sxs-lookup"><span data-stu-id="45534-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="45534-161">Nas etapas a seguir, você implementará alguns Pré-Fabricados na cena.</span><span class="sxs-lookup"><span data-stu-id="45534-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="45534-162">Na pasta Pré-Fabricados, clique e arraste a Janela de Depuração do pré-fabricado para a hierarquia.</span><span class="sxs-lookup"><span data-stu-id="45534-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="45534-163">Quando terminar, salve o projeto clicando em Arquivo e, em seguida, escolha Salvar ou pressione Control+S.</span><span class="sxs-lookup"><span data-stu-id="45534-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="45534-165">Você pode observar que um pop-up aparece ao clicar no pré-fabricado solicitando informações sobre o TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="45534-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="45534-166">Clique em Importar TMP Essentials conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="45534-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="45534-167">Se essa janela pop-up for exibida, talvez seja necessário excluir o pré-fabricado da hierarquia e arrastá-lo novamente para a hierarquia para evitar possíveis erros relacionados a texto.</span><span class="sxs-lookup"><span data-stu-id="45534-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="45534-169">Parabéns</span><span class="sxs-lookup"><span data-stu-id="45534-169">Congratulations</span></span>

<span data-ttu-id="45534-170">Seu Projeto do Unity agora está pronto para Photon.</span><span class="sxs-lookup"><span data-stu-id="45534-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="45534-171">Nos próximos tutoriais, vamos criar essa cena e nosso projeto do Unity para uma experiência compartilhada completa.</span><span class="sxs-lookup"><span data-stu-id="45534-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="45534-172">[Próximo tutorial: 3. Conectar vários usuários](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="45534-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

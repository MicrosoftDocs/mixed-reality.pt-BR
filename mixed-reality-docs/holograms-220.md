---
title: MR espacial 220-som espacial
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de som espaciais.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, som espacial
ms.openlocfilehash: a3fc054927d73cf9ac21f831caa4ec23875977bd
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434728"
---
>[!NOTE]
><span data-ttu-id="419d8-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="419d8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="419d8-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="419d8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="419d8-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="419d8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="419d8-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="419d8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="419d8-108">[Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="419d8-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="419d8-109">MR espacial 220: som espacial</span><span class="sxs-lookup"><span data-stu-id="419d8-109">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="419d8-110">O [som espacial](spatial-sound.md) traz a vida para os hologramas e dá a eles presença em nosso mundo.</span><span class="sxs-lookup"><span data-stu-id="419d8-110">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="419d8-111">Os hologramas são compostos por luz e som e, se você perder a visão de seus hologramas, o som espacial poderá ajudá-lo a encontrá-los.</span><span class="sxs-lookup"><span data-stu-id="419d8-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="419d8-112">O som espacial não é como o som típico que você ouviria no rádio, é um som posicionado no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="419d8-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="419d8-113">Com o som espacial, você pode fazer com que os hologramas pareçam estar por trás de você, ao lado de você ou mesmo à sua cabeça!</span><span class="sxs-lookup"><span data-stu-id="419d8-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="419d8-114">Neste curso, você vai:</span><span class="sxs-lookup"><span data-stu-id="419d8-114">In this course, you will:</span></span>

* <span data-ttu-id="419d8-115">Configure seu ambiente de desenvolvimento para usar o som espacial da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="419d8-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="419d8-116">Use o som espacial para aprimorar as interações.</span><span class="sxs-lookup"><span data-stu-id="419d8-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="419d8-117">Use o som espacial em conjunto com o [mapeamento espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="419d8-117">Use Spatial Sound in conjunction with [Spatial Mapping](spatial-mapping.md).</span></span>
* <span data-ttu-id="419d8-118">Entenda as práticas recomendadas de design e mistura de som.</span><span class="sxs-lookup"><span data-stu-id="419d8-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="419d8-119">Use o som para aprimorar os efeitos especiais e trazer o usuário para o mundo da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="419d8-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="419d8-120">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="419d8-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="419d8-121">Course</span><span class="sxs-lookup"><span data-stu-id="419d8-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="419d8-122"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="419d8-122"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="419d8-123"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="419d8-123"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="419d8-124">MR espacial 220: som espacial</span><span class="sxs-lookup"><span data-stu-id="419d8-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="419d8-125">✔️</span><span class="sxs-lookup"><span data-stu-id="419d8-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="419d8-126">✔️</span><span class="sxs-lookup"><span data-stu-id="419d8-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="419d8-127">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="419d8-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="419d8-128">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="419d8-128">Prerequisites</span></span>

* <span data-ttu-id="419d8-129">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="419d8-129">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="419d8-130">Alguma capacidade C# básica de programação.</span><span class="sxs-lookup"><span data-stu-id="419d8-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="419d8-131">Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="419d8-131">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="419d8-132">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="419d8-132">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="419d8-133">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="419d8-133">Project files</span></span>

* <span data-ttu-id="419d8-134">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="419d8-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="419d8-135"> Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="419d8-135"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="419d8-136">Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="419d8-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="419d8-137">Esta versão pode não estar mais atualizada.</span><span class="sxs-lookup"><span data-stu-id="419d8-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="419d8-138">Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="419d8-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="419d8-139"> Esta versão pode não estar mais atualizada.</span><span class="sxs-lookup"><span data-stu-id="419d8-139"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="419d8-140">Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="419d8-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="419d8-141"> Esta versão pode não estar mais atualizada.</span><span class="sxs-lookup"><span data-stu-id="419d8-141"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="419d8-142">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="419d8-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="419d8-143">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="419d8-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="419d8-144">Errata e observações</span><span class="sxs-lookup"><span data-stu-id="419d8-144">Errata and Notes</span></span>

* <span data-ttu-id="419d8-145">"Habilitar Apenas Meu Código" precisa ser desabilitado (*desmarcado*) no Visual Studio em ferramentas-> opções-> depuração para acessar os pontos de interrupção no código.</span><span class="sxs-lookup"><span data-stu-id="419d8-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="419d8-146">Capítulo 1 – configuração do Unity</span><span class="sxs-lookup"><span data-stu-id="419d8-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="419d8-147">Objetivos</span><span class="sxs-lookup"><span data-stu-id="419d8-147">Objectives</span></span>

* <span data-ttu-id="419d8-148">Altere a configuração de som do Unity para usar o som espacial da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="419d8-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="419d8-149">Adicionar som 3D a um objeto no Unity.</span><span class="sxs-lookup"><span data-stu-id="419d8-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="419d8-150">Instruções</span><span class="sxs-lookup"><span data-stu-id="419d8-150">Instructions</span></span>

* <span data-ttu-id="419d8-151">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="419d8-151">Start Unity.</span></span>
* <span data-ttu-id="419d8-152">Selecione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="419d8-152">Select **Open**.</span></span>
* <span data-ttu-id="419d8-153">Navegue até sua área de trabalho e localize a pasta que você cancelou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="419d8-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="419d8-154">Clique na pasta **Starting\Decibel** e pressione o botão **Selecionar pasta** .</span><span class="sxs-lookup"><span data-stu-id="419d8-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="419d8-155">Aguarde até que o projeto seja carregado no Unity.</span><span class="sxs-lookup"><span data-stu-id="419d8-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="419d8-156">No painel **projeto** , abra **Scenes\Decibel.Unity**.</span><span class="sxs-lookup"><span data-stu-id="419d8-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="419d8-157">No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="419d8-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="419d8-158">No Inspetor, expanda o **áudio** e observe que não há nenhuma caixa de seleção **espacial** .</span><span class="sxs-lookup"><span data-stu-id="419d8-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="419d8-159">Por padrão, o Unity não carrega um plug-in spatializer.</span><span class="sxs-lookup"><span data-stu-id="419d8-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="419d8-160">As etapas a seguir habilitarão o som espacial no projeto.</span><span class="sxs-lookup"><span data-stu-id="419d8-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="419d8-161">No menu superior do Unity, vá para **editar > configurações do projeto > áudio**.</span><span class="sxs-lookup"><span data-stu-id="419d8-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="419d8-162">Localize a lista suspensa **plug-in do Spatializer** e selecione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="419d8-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="419d8-163">No painel **hierarquia** , selecione **hologramacollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="419d8-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="419d8-164">No painel **Inspetor** , localize o componente **fonte de áudio** .</span><span class="sxs-lookup"><span data-stu-id="419d8-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="419d8-165">Marque a caixa de seleção **espacialize** .</span><span class="sxs-lookup"><span data-stu-id="419d8-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="419d8-166">Arraste o controle deslizante de **mistura espacial** para **3D**ou digite **1** na caixa de edição.</span><span class="sxs-lookup"><span data-stu-id="419d8-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="419d8-167">Agora, criaremos o projeto no Unity e configuraremos a solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="419d8-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="419d8-168">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="419d8-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="419d8-169">Clique em **Adicionar abrir cenas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="419d8-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="419d8-170">Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="419d8-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="419d8-171">Se você estiver desenvolvendo especificamente para o HoloLens, defina o **dispositivo de destino** para o **hololens**.</span><span class="sxs-lookup"><span data-stu-id="419d8-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="419d8-172">Caso contrário, deixe em **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="419d8-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="419d8-173">Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="419d8-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="419d8-174">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="419d8-174">Click **Build**.</span></span>
7. <span data-ttu-id="419d8-175">Crie uma **nova pasta** chamada "app".</span><span class="sxs-lookup"><span data-stu-id="419d8-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="419d8-176">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="419d8-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="419d8-177">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="419d8-177">Press **Select Folder**.</span></span>

<span data-ttu-id="419d8-178">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="419d8-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="419d8-179">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="419d8-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="419d8-180">Abra a **solução de Decibéi Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="419d8-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="419d8-181">Se estiver implantando no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="419d8-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="419d8-182">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="419d8-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="419d8-183">Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="419d8-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="419d8-184">Insira **o endereço IP do dispositivo de HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)** .</span><span class="sxs-lookup"><span data-stu-id="419d8-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="419d8-185">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="419d8-185">Click **Select**.</span></span> <span data-ttu-id="419d8-186">Se você não souber o endereço IP do dispositivo, examine **configurações > rede & Internet > opções avançadas**.</span><span class="sxs-lookup"><span data-stu-id="419d8-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="419d8-187">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="419d8-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="419d8-188">Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="419d8-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="419d8-189">Se estiver implantando em um headset de imersão:</span><span class="sxs-lookup"><span data-stu-id="419d8-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="419d8-190">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="419d8-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="419d8-191">Verifique se o destino de implantação está definido como **computador local**.</span><span class="sxs-lookup"><span data-stu-id="419d8-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="419d8-192">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="419d8-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="419d8-193">Capítulo 2-som espacial e interação</span><span class="sxs-lookup"><span data-stu-id="419d8-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="419d8-194">Objetivos</span><span class="sxs-lookup"><span data-stu-id="419d8-194">Objectives</span></span>

* <span data-ttu-id="419d8-195">Aprimore o holograma de uso de um som.</span><span class="sxs-lookup"><span data-stu-id="419d8-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="419d8-196">Direcionar o olhar do usuário usando o som.</span><span class="sxs-lookup"><span data-stu-id="419d8-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="419d8-197">Forneça comentários sobre gestos usando som.</span><span class="sxs-lookup"><span data-stu-id="419d8-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="419d8-198">Parte 1-aprimorando o realm</span><span class="sxs-lookup"><span data-stu-id="419d8-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="419d8-199">Principais conceitos</span><span class="sxs-lookup"><span data-stu-id="419d8-199">Key Concepts</span></span>

* <span data-ttu-id="419d8-200">Esespaciair sons de holograma.</span><span class="sxs-lookup"><span data-stu-id="419d8-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="419d8-201">As fontes de som devem ser colocadas em um local apropriado no holograma.</span><span class="sxs-lookup"><span data-stu-id="419d8-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="419d8-202">O local apropriado para o som vai depender do holograma.</span><span class="sxs-lookup"><span data-stu-id="419d8-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="419d8-203">Por exemplo, se o holograma for de um humano, a origem do som deverá ser localizada perto da boca e não dos pés.</span><span class="sxs-lookup"><span data-stu-id="419d8-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="419d8-204">Instruções</span><span class="sxs-lookup"><span data-stu-id="419d8-204">Instructions</span></span>

<span data-ttu-id="419d8-205">As instruções a seguir anexarão um som espacial a um holograma.</span><span class="sxs-lookup"><span data-stu-id="419d8-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="419d8-206">No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="419d8-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="419d8-207">No painel **Inspetor** , na mensagem de **áudio**, clique no círculo ao lado de **AudioClip** e selecione **polifocalizar** no pop-up.</span><span class="sxs-lookup"><span data-stu-id="419d8-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="419d8-208">Clique no círculo ao lado de **saída** e selecione **SoundEffects** no pop-up.</span><span class="sxs-lookup"><span data-stu-id="419d8-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="419d8-209">O projeto Decibéi usa um componente **AudioMixer** do Unity para habilitar o ajuste dos níveis de som para grupos de sons.</span><span class="sxs-lookup"><span data-stu-id="419d8-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="419d8-210">Ao agrupar sons dessa forma, o volume geral pode ser ajustado mantendo o volume relativo de cada som.</span><span class="sxs-lookup"><span data-stu-id="419d8-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="419d8-211">Em **áudio**, expanda **configurações de som 3D**.</span><span class="sxs-lookup"><span data-stu-id="419d8-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="419d8-212">Defina o **nível de Doppler** como **0**.</span><span class="sxs-lookup"><span data-stu-id="419d8-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="419d8-213">Definir o nível de Doppler como zero desabilita as alterações em pitch causadas pelo Motion (do holograma ou do usuário).</span><span class="sxs-lookup"><span data-stu-id="419d8-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="419d8-214">Um exemplo clássico de Doppler é um carro com movimentação rápida.</span><span class="sxs-lookup"><span data-stu-id="419d8-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="419d8-215">À medida que o carro se aproxima de um ouvinte estacionário, a inclinação do motor aumenta.</span><span class="sxs-lookup"><span data-stu-id="419d8-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="419d8-216">Quando ele passa o ouvinte, a densidade diminui com distância.</span><span class="sxs-lookup"><span data-stu-id="419d8-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="419d8-217">Parte 2-direcionando o olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="419d8-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="419d8-218">Principais conceitos</span><span class="sxs-lookup"><span data-stu-id="419d8-218">Key Concepts</span></span>

* <span data-ttu-id="419d8-219">Use o som para chamar a atenção para hologramas importantes.</span><span class="sxs-lookup"><span data-stu-id="419d8-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="419d8-220">Os ouvidos ajudam a direcionar onde devem ser os olhos.</span><span class="sxs-lookup"><span data-stu-id="419d8-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="419d8-221">O cérebro tem algumas expectativas aprendidas.</span><span class="sxs-lookup"><span data-stu-id="419d8-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="419d8-222">Um exemplo de expectativas aprendidas é que os pássaros geralmente estão acima da cabeça dos seres humanos.</span><span class="sxs-lookup"><span data-stu-id="419d8-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="419d8-223">Se um usuário ouve um som de pássaro, sua reação inicial é Pesquisar.</span><span class="sxs-lookup"><span data-stu-id="419d8-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="419d8-224">Colocar um pássaro abaixo do usuário pode levar a eles voltados para a direção correta do som, mas não consegue encontrar o holograma com base na expectativa de precisar pesquisar.</span><span class="sxs-lookup"><span data-stu-id="419d8-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="419d8-225">Instruções</span><span class="sxs-lookup"><span data-stu-id="419d8-225">Instructions</span></span>

<span data-ttu-id="419d8-226">As instruções a seguir permitem que P0LY sejam ocultadas para trás, para que você possa usar o som para localizar o holograma.</span><span class="sxs-lookup"><span data-stu-id="419d8-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="419d8-227">No painel **hierarquia** , selecione **gerentes**.</span><span class="sxs-lookup"><span data-stu-id="419d8-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="419d8-228">No painel **Inspetor** , encontre o **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="419d8-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="419d8-229">Em **manipulador de entrada de fala**, expanda **ir ocultar**.</span><span class="sxs-lookup"><span data-stu-id="419d8-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="419d8-230">Altere **nenhuma função** para **GoHide**.</span><span class="sxs-lookup"><span data-stu-id="419d8-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Palavra-chave: ir ocultar](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="419d8-232">Parte 3-comentários do gesto</span><span class="sxs-lookup"><span data-stu-id="419d8-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="419d8-233">Principais conceitos</span><span class="sxs-lookup"><span data-stu-id="419d8-233">Key Concepts</span></span>

* <span data-ttu-id="419d8-234">Fornecer ao usuário uma confirmação de gesto positivo usando som</span><span class="sxs-lookup"><span data-stu-id="419d8-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="419d8-235">Não sobrecarregar os sons do usuário em alta</span><span class="sxs-lookup"><span data-stu-id="419d8-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="419d8-236">Os sons sutis funcionam melhor – não obscurecem a experiência</span><span class="sxs-lookup"><span data-stu-id="419d8-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="419d8-237">Instruções</span><span class="sxs-lookup"><span data-stu-id="419d8-237">Instructions</span></span>

* <span data-ttu-id="419d8-238">No painel **hierarquia** , expanda **hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="419d8-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="419d8-239">Expanda **EnergyHub** e selecione **base**.</span><span class="sxs-lookup"><span data-stu-id="419d8-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="419d8-240">No painel **Inspetor** , clique em **Adicionar componente** e adicionar **manipulador de som de gesto**.</span><span class="sxs-lookup"><span data-stu-id="419d8-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="419d8-241">Em **manipulador de som de gesto**, clique no círculo próximo ao **clipe de navegação** e ao clipe de navegação **atualizado** e selecione **RotateClick** do pop-up para ambos.</span><span class="sxs-lookup"><span data-stu-id="419d8-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="419d8-242">Clique duas vezes em "GestureSoundHandler" para carregar no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="419d8-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="419d8-243">O manipulador de som de gesto executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="419d8-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="419d8-244">Criar e configurar um **áudio**.</span><span class="sxs-lookup"><span data-stu-id="419d8-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="419d8-245">Coloque a **audioname** no local do **gameobject**apropriado.</span><span class="sxs-lookup"><span data-stu-id="419d8-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="419d8-246">Reproduz o **AudioClip** associado ao gesto.</span><span class="sxs-lookup"><span data-stu-id="419d8-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="419d8-247">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="419d8-247">Build and Deploy</span></span>

1. <span data-ttu-id="419d8-248">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="419d8-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="419d8-249">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="419d8-249">Click **Build**.</span></span>
3. <span data-ttu-id="419d8-250">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="419d8-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="419d8-251">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="419d8-251">Press **Select Folder**.</span></span>

<span data-ttu-id="419d8-252">Verifique se a barra de ferramentas diz "versão", "x86" ou "x64" e "dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="419d8-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="419d8-253">Caso contrário, essa é a instância de codificação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="419d8-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="419d8-254">Talvez seja necessário reabrir a solução na pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="419d8-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="419d8-255">Se solicitado, recarregue os arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="419d8-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="419d8-256">Como antes, implante a partir do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="419d8-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="419d8-257">Após a implantação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="419d8-257">After the application is deployed:</span></span>

* <span data-ttu-id="419d8-258">Observe como o som muda à medida que você se move ao P0LY.</span><span class="sxs-lookup"><span data-stu-id="419d8-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="419d8-259">Digamos que *"Vá ocultar"* para fazer com que o P0LY se mova para um local por trás de você.</span><span class="sxs-lookup"><span data-stu-id="419d8-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="419d8-260">Encontre-o pelo som.</span><span class="sxs-lookup"><span data-stu-id="419d8-260">Find it by the sound.</span></span>
* <span data-ttu-id="419d8-261">Olhar na base do hub de energia.</span><span class="sxs-lookup"><span data-stu-id="419d8-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="419d8-262">Toque e arraste para a esquerda ou direita para girar o holograma e observe como o clique do som confirma o gesto.</span><span class="sxs-lookup"><span data-stu-id="419d8-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="419d8-263">Observação: há um painel de texto que será rotulado com você.</span><span class="sxs-lookup"><span data-stu-id="419d8-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="419d8-264">Isso conterá os comandos de voz disponíveis que você pode usar ao longo deste curso.</span><span class="sxs-lookup"><span data-stu-id="419d8-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="419d8-265">Capítulo 3-som espacial e mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="419d8-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="419d8-266">Objetivos</span><span class="sxs-lookup"><span data-stu-id="419d8-266">Objectives</span></span>

* <span data-ttu-id="419d8-267">Confirme a interação entre os hologramas e o mundo real usando som.</span><span class="sxs-lookup"><span data-stu-id="419d8-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="419d8-268">Occlude sons usando o mundo físico.</span><span class="sxs-lookup"><span data-stu-id="419d8-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="419d8-269">Parte 1-interação física do mundo</span><span class="sxs-lookup"><span data-stu-id="419d8-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="419d8-270">Principais conceitos</span><span class="sxs-lookup"><span data-stu-id="419d8-270">Key Concepts</span></span>

* <span data-ttu-id="419d8-271">Os objetos físicos geralmente fazem um som ao encontrar uma superfície ou outro objeto.</span><span class="sxs-lookup"><span data-stu-id="419d8-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="419d8-272">Os sons devem ser apropriados para o contexto na experiência.</span><span class="sxs-lookup"><span data-stu-id="419d8-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="419d8-273">Por exemplo, definir uma xícara em uma tabela deve fazer um som mais silencioso do que descartar um Boulder em uma parte do metal.</span><span class="sxs-lookup"><span data-stu-id="419d8-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="419d8-274">Instruções</span><span class="sxs-lookup"><span data-stu-id="419d8-274">Instructions</span></span>

* <span data-ttu-id="419d8-275">No painel **hierarquia** , expanda **hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="419d8-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="419d8-276">Expanda **EnergyHub**, selecione **base**.</span><span class="sxs-lookup"><span data-stu-id="419d8-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="419d8-277">No painel **Inspetor** , clique em **Adicionar componente** e adicione **tocar para inserir com som e ação**.</span><span class="sxs-lookup"><span data-stu-id="419d8-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="419d8-278">Em **toque para posicionar com som e ação**:</span><span class="sxs-lookup"><span data-stu-id="419d8-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="419d8-279">Verifique o **pai ao tocar**.</span><span class="sxs-lookup"><span data-stu-id="419d8-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="419d8-280">Defina **som de posicionamento** como **local**.</span><span class="sxs-lookup"><span data-stu-id="419d8-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="419d8-281">Defina **som de retirada** para **retirada**.</span><span class="sxs-lookup"><span data-stu-id="419d8-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="419d8-282">Pressione a + no canto inferior direito em ambos **na ação de retirada** e **na ação de posicionamento**.</span><span class="sxs-lookup"><span data-stu-id="419d8-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="419d8-283">Arraste EnergyHub da cena para os campos **nenhum (objeto)** .</span><span class="sxs-lookup"><span data-stu-id="419d8-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="419d8-284">Em **ação de retirada**, clique em **sem função** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="419d8-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="419d8-285">Em **ação de posicionamento**, clique em **sem função** -> **EnergyHubBase** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="419d8-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Toque para posicionar com som e ação](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="419d8-287">Parte 2-som oclusão</span><span class="sxs-lookup"><span data-stu-id="419d8-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="419d8-288">Principais conceitos</span><span class="sxs-lookup"><span data-stu-id="419d8-288">Key Concepts</span></span>

* <span data-ttu-id="419d8-289">Som, como claro, pode ser obstruído.</span><span class="sxs-lookup"><span data-stu-id="419d8-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="419d8-290">Um exemplo clássico é uma sala de concerto.</span><span class="sxs-lookup"><span data-stu-id="419d8-290">A classic example is a concert hall.</span></span> <span data-ttu-id="419d8-291">Quando um ouvinte está fora do Hall e a porta é fechada, a música parece muffled.</span><span class="sxs-lookup"><span data-stu-id="419d8-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="419d8-292">Normalmente, também há uma redução no volume.</span><span class="sxs-lookup"><span data-stu-id="419d8-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="419d8-293">Quando a porta é aberta, o espectro completo do som é ouvido no volume real.</span><span class="sxs-lookup"><span data-stu-id="419d8-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="419d8-294">Sons de alta frequência geralmente são absorvidos mais do que frequências baixas.</span><span class="sxs-lookup"><span data-stu-id="419d8-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="419d8-295">Instruções</span><span class="sxs-lookup"><span data-stu-id="419d8-295">Instructions</span></span>

* <span data-ttu-id="419d8-296">No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="419d8-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="419d8-297">No painel **Inspetor** , clique em **Adicionar componente** e adicionar **emissor de áudio**.</span><span class="sxs-lookup"><span data-stu-id="419d8-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="419d8-298">A classe emissor de áudio fornece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="419d8-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="419d8-299">Restaura todas as alterações no volume de **audioname**.</span><span class="sxs-lookup"><span data-stu-id="419d8-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="419d8-300">Executa uma **física. RaycastNonAlloc** da posição do usuário na direção do **gameobject** ao qual o **AudioEmitter** está anexado.</span><span class="sxs-lookup"><span data-stu-id="419d8-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="419d8-301">O método RaycastNonAlloc é usado como uma otimização de desempenho para limitar as alocações, bem como o número de resultados retornados.</span><span class="sxs-lookup"><span data-stu-id="419d8-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="419d8-302">Para cada **IAudioInfluencer** encontrado, chama o método **ApplyEffect** .</span><span class="sxs-lookup"><span data-stu-id="419d8-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="419d8-303">Para cada **IAudioInfluencer** anterior que não é mais encontrado, chame o método **RemoveEffect** .</span><span class="sxs-lookup"><span data-stu-id="419d8-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="419d8-304">Observe que as atualizações do AudioEmitter em escalas de tempo humano, em oposição a por quadro.</span><span class="sxs-lookup"><span data-stu-id="419d8-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="419d8-305">Isso é feito porque as pessoas geralmente não se movem com rapidez suficiente para que o efeito precise ser atualizado com mais frequência do que cada trimestre ou metade de um segundo.</span><span class="sxs-lookup"><span data-stu-id="419d8-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="419d8-306">Os hologramas que teleport rapidamente de um local para outro podem quebrar a ilusão.</span><span class="sxs-lookup"><span data-stu-id="419d8-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="419d8-307">No painel **hierarquia** , expanda **hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="419d8-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="419d8-308">Expanda **EnergyHub** e selecione **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="419d8-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="419d8-309">No painel **Inspetor** , clique em **Adicionar componente** e adicione **áudio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="419d8-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="419d8-310">Em **áudio Occluder**, defina a **frequência de corte** como **1500**.</span><span class="sxs-lookup"><span data-stu-id="419d8-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="419d8-311">Essa configuração limita as frequências de áudio para 1500 Hz e abaixo.</span><span class="sxs-lookup"><span data-stu-id="419d8-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="419d8-312">Defina **passagem de volume** para **0,9**.</span><span class="sxs-lookup"><span data-stu-id="419d8-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="419d8-313">Essa configuração reduz o volume do áudio para 90% do seu nível atual.</span><span class="sxs-lookup"><span data-stu-id="419d8-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="419d8-314">O áudio Occluder implementa IAudioInfluencer para:</span><span class="sxs-lookup"><span data-stu-id="419d8-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="419d8-315">Aplique um efeito de oclusão usando um **AudioLowPassFilter** que é anexado ao **áudio** , gerenciado, comprar o **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="419d8-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="419d8-316">Aplica a atenuação de volume à Audioname.</span><span class="sxs-lookup"><span data-stu-id="419d8-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="419d8-317">Desabilita o efeito definindo uma frequência de corte neutra e desabilitando o filtro.</span><span class="sxs-lookup"><span data-stu-id="419d8-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="419d8-318">A frequência usada como neutra é 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="419d8-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="419d8-319">Essa frequência foi escolhida porque está acima da frequência máxima nominal que pode ser ouvida pelo Ear humano, isso não faz nenhum impacto discernido no som.</span><span class="sxs-lookup"><span data-stu-id="419d8-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="419d8-320">No painel **hierarquia** , selecione **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="419d8-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="419d8-321">No painel **Inspetor** , clique em **Adicionar componente** e adicione **áudio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="419d8-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="419d8-322">Em **áudio Occluder**, defina a **frequência de corte** como **750**.</span><span class="sxs-lookup"><span data-stu-id="419d8-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="419d8-323">Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a frequência mais baixa é aplicada ao filtro.</span><span class="sxs-lookup"><span data-stu-id="419d8-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="419d8-324">Defina **passagem de volume** para **0,75**.</span><span class="sxs-lookup"><span data-stu-id="419d8-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="419d8-325">Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a passagem do volume é aplicada de aditivo.</span><span class="sxs-lookup"><span data-stu-id="419d8-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="419d8-326">No painel **hierarquia** , selecione **gerentes**.</span><span class="sxs-lookup"><span data-stu-id="419d8-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="419d8-327">No painel **Inspetor** , expanda **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="419d8-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="419d8-328">Em **manipulador de entrada de fala**, expanda ir para o **encargo**.</span><span class="sxs-lookup"><span data-stu-id="419d8-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="419d8-329">Altere **nenhuma função** para **GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="419d8-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Palavra-chave: ir para a carga](images/gocharge.png)

* <span data-ttu-id="419d8-331">Expanda **aqui**.</span><span class="sxs-lookup"><span data-stu-id="419d8-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="419d8-332">Altere **nenhuma função** para **ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="419d8-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Palavra-chave: Venha aqui](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="419d8-334">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="419d8-334">Build and Deploy</span></span>

* <span data-ttu-id="419d8-335">Como antes, compile o projeto no Unity e implante-o no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="419d8-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="419d8-336">Após a implantação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="419d8-336">After the application is deployed:</span></span>

* <span data-ttu-id="419d8-337">Digamos que "faça o *encargo"* para que o P0LY Insira o Hub de energia.</span><span class="sxs-lookup"><span data-stu-id="419d8-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="419d8-338">Observe a alteração no som.</span><span class="sxs-lookup"><span data-stu-id="419d8-338">Note the change in the sound.</span></span> <span data-ttu-id="419d8-339">Ele deve parecer muffled e um pouco mais silencioso.</span><span class="sxs-lookup"><span data-stu-id="419d8-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="419d8-340">Se você for capaz de se posicionar com uma parede ou outro objeto entre você e o Hub de energia, você deve notar um Muffling adicional do som devido à oclusão pelo mundo real.</span><span class="sxs-lookup"><span data-stu-id="419d8-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="419d8-341">Diga *"Venha aqui"* para que P0LY deixe o Hub de energia e se posicione na frente de você.</span><span class="sxs-lookup"><span data-stu-id="419d8-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="419d8-342">Observe que o som oclusão é removido quando o P0LY sai do hub de energia.</span><span class="sxs-lookup"><span data-stu-id="419d8-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="419d8-343">Se você ainda estiver ouvindo oclusão, P0LY poderá ser obstruído pelo mundo real.</span><span class="sxs-lookup"><span data-stu-id="419d8-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="419d8-344">Tente mudar para garantir que você tenha uma clara linha de visão para P0LY.</span><span class="sxs-lookup"><span data-stu-id="419d8-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="419d8-345">Parte 3-modelos de sala</span><span class="sxs-lookup"><span data-stu-id="419d8-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="419d8-346">Principais conceitos</span><span class="sxs-lookup"><span data-stu-id="419d8-346">Key Concepts</span></span>

* <span data-ttu-id="419d8-347">O tamanho do espaço fornece filas subliminal que contribuem para a localização de som.</span><span class="sxs-lookup"><span data-stu-id="419d8-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="419d8-348">Os modelos de sala são definidos por**áudio**.</span><span class="sxs-lookup"><span data-stu-id="419d8-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="419d8-349">O [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece código para definir o modelo de sala.</span><span class="sxs-lookup"><span data-stu-id="419d8-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="419d8-350">Para experiências de realidade misturada, selecione o modelo de sala que melhor se adapta ao espaço do mundo real.</span><span class="sxs-lookup"><span data-stu-id="419d8-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="419d8-351">Se você estiver criando um cenário de realidade virtual, selecione o modelo de sala que melhor se adapta ao ambiente virtual.</span><span class="sxs-lookup"><span data-stu-id="419d8-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="419d8-352">Capítulo 4-design de som</span><span class="sxs-lookup"><span data-stu-id="419d8-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="419d8-353">Objetivos</span><span class="sxs-lookup"><span data-stu-id="419d8-353">Objectives</span></span>

* <span data-ttu-id="419d8-354">Entenda as considerações sobre o design de som efetivo.</span><span class="sxs-lookup"><span data-stu-id="419d8-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="419d8-355">Aprenda técnicas e diretrizes de combinação.</span><span class="sxs-lookup"><span data-stu-id="419d8-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="419d8-356">Parte 1-design de som e experiência</span><span class="sxs-lookup"><span data-stu-id="419d8-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="419d8-357">Esta seção aborda as principais considerações e diretrizes de design de som e experiência.</span><span class="sxs-lookup"><span data-stu-id="419d8-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="419d8-358">Normalizar todos os sons</span><span class="sxs-lookup"><span data-stu-id="419d8-358">Normalize all sounds</span></span>

<span data-ttu-id="419d8-359">Isso evita a necessidade de código de caso especial para ajustar os níveis de volume por som, o que pode ser demorado e limita a capacidade de atualizar facilmente os arquivos de som.</span><span class="sxs-lookup"><span data-stu-id="419d8-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="419d8-360">Design de uma experiência não de compartilhamento de Internet</span><span class="sxs-lookup"><span data-stu-id="419d8-360">Design for an untethered experience</span></span>

<span data-ttu-id="419d8-361">O HoloLens é um computador Holographic totalmente contido e desvinculado.</span><span class="sxs-lookup"><span data-stu-id="419d8-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="419d8-362">Os usuários podem e usarão suas experiências ao se moverem.</span><span class="sxs-lookup"><span data-stu-id="419d8-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="419d8-363">Certifique-se de testar sua mixagem de áudio ao percorrer.</span><span class="sxs-lookup"><span data-stu-id="419d8-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="419d8-364">Emitir som de locais lógicos em seus hologramas</span><span class="sxs-lookup"><span data-stu-id="419d8-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="419d8-365">No mundo real, um cachorro não latido de sua parte final e a voz de um humano não vem de seus pés.</span><span class="sxs-lookup"><span data-stu-id="419d8-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="419d8-366">Evite emitir seus sons de partes inesperadas de seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="419d8-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="419d8-367">Para hologramas pequenos, é razoável ter uma emissão sonora do centro da geometria.</span><span class="sxs-lookup"><span data-stu-id="419d8-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="419d8-368">Os sons conhecidos são mais localizáveis</span><span class="sxs-lookup"><span data-stu-id="419d8-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="419d8-369">A voz humana e a música são muito fáceis de localizar.</span><span class="sxs-lookup"><span data-stu-id="419d8-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="419d8-370">Se alguém chamar seu nome, você poderá determinar com precisão a direção de que a voz veio e de quanto longe.</span><span class="sxs-lookup"><span data-stu-id="419d8-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="419d8-371">Sons curtos e desconhecidos são mais difíceis de localizar.</span><span class="sxs-lookup"><span data-stu-id="419d8-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="419d8-372">Cognizant as expectativas dos usuários</span><span class="sxs-lookup"><span data-stu-id="419d8-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="419d8-373">A experiência de vida exerce uma parte em nossa capacidade de identificar o local de um som.</span><span class="sxs-lookup"><span data-stu-id="419d8-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="419d8-374">Esse é um dos motivos pelos quais a voz humana é particularmente fácil de localizar.</span><span class="sxs-lookup"><span data-stu-id="419d8-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="419d8-375">É importante estar atento às expectativas aprendidas do usuário ao colocar seus sons.</span><span class="sxs-lookup"><span data-stu-id="419d8-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="419d8-376">Por exemplo, quando alguém ouve uma música de pássaro, ele geralmente procura, pois os pássaros tendem a estar acima da linha de visão (voador ou em uma árvore).</span><span class="sxs-lookup"><span data-stu-id="419d8-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="419d8-377">Não é incomum um usuário ativar a direção correta de um som, mas examinar a direção vertical incorreta e ficar confuso ou frustrado quando não conseguir encontrar o holograma.</span><span class="sxs-lookup"><span data-stu-id="419d8-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="419d8-378">Evitar emissores ocultos</span><span class="sxs-lookup"><span data-stu-id="419d8-378">Avoid hidden emitters</span></span>

<span data-ttu-id="419d8-379">No mundo real, se ouvimos um som, geralmente podemos identificar o objeto que está emitindo o som.</span><span class="sxs-lookup"><span data-stu-id="419d8-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="419d8-380">Isso também deve se manter verdadeiro em suas experiências.</span><span class="sxs-lookup"><span data-stu-id="419d8-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="419d8-381">Pode ser muito desconcerto para os usuários ouvirem um som, saber de onde o som se origina e não conseguir ver um objeto.</span><span class="sxs-lookup"><span data-stu-id="419d8-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="419d8-382">Há algumas exceções a essa diretriz.</span><span class="sxs-lookup"><span data-stu-id="419d8-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="419d8-383">Por exemplo, sons de ambiente como Crickets em um campo não precisam estar visíveis.</span><span class="sxs-lookup"><span data-stu-id="419d8-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="419d8-384">A experiência de vida nos dá familiaridade com a origem desses sons sem a necessidade de vê-los.</span><span class="sxs-lookup"><span data-stu-id="419d8-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="419d8-385">Parte 2-mixagem de som</span><span class="sxs-lookup"><span data-stu-id="419d8-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="419d8-386">Direcione sua combinação para o volume de 70% no HoloLens</span><span class="sxs-lookup"><span data-stu-id="419d8-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="419d8-387">As experiências de realidade misturada permitem que os hologramas sejam vistos no mundo real.</span><span class="sxs-lookup"><span data-stu-id="419d8-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="419d8-388">Eles também devem permitir que sons do mundo real sejam ouvidos.</span><span class="sxs-lookup"><span data-stu-id="419d8-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="419d8-389">Um destino de volume de 70% permite que o usuário Ouça o mundo junto com o som de sua experiência.</span><span class="sxs-lookup"><span data-stu-id="419d8-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="419d8-390">O HoloLens em 100% volume deve se afogar em sons externos</span><span class="sxs-lookup"><span data-stu-id="419d8-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="419d8-391">Um nível de volume de 100% é semelhante a uma experiência de realidade virtual.</span><span class="sxs-lookup"><span data-stu-id="419d8-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="419d8-392">Visualmente, o usuário é transportado para um mundo diferente.</span><span class="sxs-lookup"><span data-stu-id="419d8-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="419d8-393">O mesmo deve conter verdadeiro forma audível.</span><span class="sxs-lookup"><span data-stu-id="419d8-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="419d8-394">Usar o AudioMixer do Unity para ajustar as categorias de sons</span><span class="sxs-lookup"><span data-stu-id="419d8-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="419d8-395">Ao projetar sua combinação, geralmente é útil criar categorias de som e ter a capacidade de aumentar ou diminuir seu volume como uma unidade.</span><span class="sxs-lookup"><span data-stu-id="419d8-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="419d8-396">Isso retém os níveis relativos de cada som, ao mesmo tempo em que permite alterações rápidas e fáceis na combinação geral.</span><span class="sxs-lookup"><span data-stu-id="419d8-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="419d8-397">As categorias comuns incluem; efeitos de som, Ambience, voz e música em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="419d8-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="419d8-398">Misturar sons com base no olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="419d8-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="419d8-399">Muitas vezes, pode ser útil alterar a mistura de som em sua experiência com base em onde um usuário está olhando (ou não).</span><span class="sxs-lookup"><span data-stu-id="419d8-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="419d8-400">Um uso comum para essa técnica é reduzir o nível de volume para hologramas que estão fora do quadro Holographic para tornar mais fácil para o usuário se concentrar nas informações em frente deles.</span><span class="sxs-lookup"><span data-stu-id="419d8-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="419d8-401">Outro uso é aumentar o volume de um som para chamar a atenção do usuário para um evento importante.</span><span class="sxs-lookup"><span data-stu-id="419d8-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="419d8-402">Criando sua combinação</span><span class="sxs-lookup"><span data-stu-id="419d8-402">Building your mix</span></span>

<span data-ttu-id="419d8-403">Ao criar sua combinação, é recomendável começar com o áudio de segundo plano da sua experiência e adicionar camadas com base na importância.</span><span class="sxs-lookup"><span data-stu-id="419d8-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="419d8-404">Geralmente, isso resulta em cada camada sendo mais alta do que a anterior.</span><span class="sxs-lookup"><span data-stu-id="419d8-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="419d8-405">Ao imaginar sua mistura como um funil invertido, com o menos importante (e geralmente sons mais silenciosos) na parte inferior, é recomendável estruturar sua mistura semelhante ao diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="419d8-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Estrutura da combinação de som](images/soundlevels.png)

<span data-ttu-id="419d8-407">A voz é um cenário interessante.</span><span class="sxs-lookup"><span data-stu-id="419d8-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="419d8-408">Com base na experiência que você está criando, talvez você queira ter um som estéreo (não localizado) ou para espacialar sua voz.</span><span class="sxs-lookup"><span data-stu-id="419d8-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="419d8-409">Duas experiências publicadas da Microsoft ilustram excelentes exemplos de cada cenário.</span><span class="sxs-lookup"><span data-stu-id="419d8-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="419d8-410">O [HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa uma voz estéreo.</span><span class="sxs-lookup"><span data-stu-id="419d8-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="419d8-411">Quando o narrador está descrevendo o local que está sendo exibido, o som é consistente e não varia de acordo com a posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="419d8-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="419d8-412">Isso permite que o narrador descreva a cena sem sair dos sons espaciais do ambiente.</span><span class="sxs-lookup"><span data-stu-id="419d8-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="419d8-413">Os [fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizam uma voz espacialada na forma de uma detecção.</span><span class="sxs-lookup"><span data-stu-id="419d8-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="419d8-414">A voz da detecção é usada para ajudar a levar a atenção do usuário a uma pista importante como se um humano real estivesse na sala.</span><span class="sxs-lookup"><span data-stu-id="419d8-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="419d8-415">Isso permite um sentido ainda maior de imersão na experiência de resolver o mistério.</span><span class="sxs-lookup"><span data-stu-id="419d8-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="419d8-416">Parte 3-desempenho</span><span class="sxs-lookup"><span data-stu-id="419d8-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="419d8-417">Uso da CPU</span><span class="sxs-lookup"><span data-stu-id="419d8-417">CPU usage</span></span>

<span data-ttu-id="419d8-418">Ao usar o som espacial, 10-12 emissores consumirão aproximadamente 12% da CPU.</span><span class="sxs-lookup"><span data-stu-id="419d8-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="419d8-419">Transmitir arquivos de áudio longos</span><span class="sxs-lookup"><span data-stu-id="419d8-419">Stream long audio files</span></span>

<span data-ttu-id="419d8-420">Os dados de áudio podem ser grandes, especialmente em taxas de exemplo comuns (44,1 e 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="419d8-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="419d8-421">Uma regra geral é que os arquivos de áudio com mais de 5-10 segundos devem ser transmitidos para reduzir o uso de memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="419d8-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="419d8-422">No Unity, você pode marcar um arquivo de áudio para streaming nas configurações de importação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="419d8-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Configurações de importação de áudio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="419d8-424">Capítulo 5-efeitos especiais</span><span class="sxs-lookup"><span data-stu-id="419d8-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="419d8-425">Objetivos</span><span class="sxs-lookup"><span data-stu-id="419d8-425">Objectives</span></span>

* <span data-ttu-id="419d8-426">Adicione profundidade a "janelas mágicas".</span><span class="sxs-lookup"><span data-stu-id="419d8-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="419d8-427">Traga o usuário para o mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="419d8-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="419d8-428">Janelas mágicas</span><span class="sxs-lookup"><span data-stu-id="419d8-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="419d8-429">Principais conceitos</span><span class="sxs-lookup"><span data-stu-id="419d8-429">Key Concepts</span></span>

* <span data-ttu-id="419d8-430">Criar exibições em um mundo oculto é visualmente atraente.</span><span class="sxs-lookup"><span data-stu-id="419d8-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="419d8-431">Aprimore o realm adicionando efeitos de áudio quando um holograma ou o usuário estiver perto do mundo oculto.</span><span class="sxs-lookup"><span data-stu-id="419d8-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="419d8-432">Instruções</span><span class="sxs-lookup"><span data-stu-id="419d8-432">Instructions</span></span>

* <span data-ttu-id="419d8-433">No painel **hierarquia** , expanda **hologramacollection** e selecione **Underworld**.</span><span class="sxs-lookup"><span data-stu-id="419d8-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="419d8-434">Expanda **Underworld** e selecione **voicename**.</span><span class="sxs-lookup"><span data-stu-id="419d8-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="419d8-435">No painel **Inspetor** , clique em **Adicionar componente** e adicionar **efeito de voz do usuário**.</span><span class="sxs-lookup"><span data-stu-id="419d8-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="419d8-436">Um componente de **aúdio** será adicionado à **voiceprovider**.</span><span class="sxs-lookup"><span data-stu-id="419d8-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="419d8-437">Em **áudio**, defina **saída** para **UserVoice (mixer)** .</span><span class="sxs-lookup"><span data-stu-id="419d8-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="419d8-438">Marque a caixa de seleção **espacialize** .</span><span class="sxs-lookup"><span data-stu-id="419d8-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="419d8-439">Arraste o controle deslizante de **mistura espacial** para **3D**ou digite **1** na caixa de edição.</span><span class="sxs-lookup"><span data-stu-id="419d8-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="419d8-440">Expanda **configurações de som 3D**.</span><span class="sxs-lookup"><span data-stu-id="419d8-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="419d8-441">Defina o **nível de Doppler** como **0**.</span><span class="sxs-lookup"><span data-stu-id="419d8-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="419d8-442">Em **efeito de voz do usuário**, defina **objeto pai** como o **Underworld** da cena.</span><span class="sxs-lookup"><span data-stu-id="419d8-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="419d8-443">Defina a **distância máxima** como **1**.</span><span class="sxs-lookup"><span data-stu-id="419d8-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="419d8-444">Definir a **distância máxima** informa o **efeito de voz do usuário** como fechar o usuário deve ser ao objeto pai antes de o efeito ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="419d8-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="419d8-445">Em **efeito de voz do usuário**, expanda **parâmetros Chorus**.</span><span class="sxs-lookup"><span data-stu-id="419d8-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="419d8-446">Defina **profundidade** como **0,1**.</span><span class="sxs-lookup"><span data-stu-id="419d8-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="419d8-447">Defina **tocar 1 volume**, **toque em 2 volume** e **toque em 3 volume** para **0,8**.</span><span class="sxs-lookup"><span data-stu-id="419d8-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="419d8-448">Defina o **volume de som original** como **0,5**.</span><span class="sxs-lookup"><span data-stu-id="419d8-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="419d8-449">As configurações anteriores configuram os parâmetros do Unity **AudioChorusFilter** usado para adicionar riqueza à voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="419d8-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="419d8-450">Em **efeito de voz do usuário**, expanda **parâmetros de eco**.</span><span class="sxs-lookup"><span data-stu-id="419d8-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="419d8-451">Definir **atraso** como **300**</span><span class="sxs-lookup"><span data-stu-id="419d8-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="419d8-452">Defina a **taxa de decaimento** como **0,2**.</span><span class="sxs-lookup"><span data-stu-id="419d8-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="419d8-453">Defina o **volume de som original** como **0**.</span><span class="sxs-lookup"><span data-stu-id="419d8-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="419d8-454">As configurações anteriores configuram os parâmetros do Unity **AudioEchoFilter** usado para fazer com que a voz do usuário seja ecoada.</span><span class="sxs-lookup"><span data-stu-id="419d8-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="419d8-455">O script de efeito de voz do usuário é responsável por:</span><span class="sxs-lookup"><span data-stu-id="419d8-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="419d8-456">Medindo a distância entre o usuário e o **gameobject** ao qual o script está anexado.</span><span class="sxs-lookup"><span data-stu-id="419d8-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="419d8-457">Determinando se o usuário está voltado para o **gameobject**.</span><span class="sxs-lookup"><span data-stu-id="419d8-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="419d8-458">O usuário deve estar voltado para o gameobject, independentemente da distância, para que o efeito seja habilitado.</span><span class="sxs-lookup"><span data-stu-id="419d8-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="419d8-459">Aplicando e configurando um **AudioChorusFilter** e um **AudioEchoFilter** para a **audioname**.</span><span class="sxs-lookup"><span data-stu-id="419d8-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="419d8-460">Desabilitando o efeito, desabilitando os filtros.</span><span class="sxs-lookup"><span data-stu-id="419d8-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="419d8-461">O efeito de voz do usuário usa o componente seletor de fluxo do MIC, do [MixedRealityToolkit para o Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), para selecionar o fluxo de voz de alta qualidade e roteá-lo no sistema de áudio do Unity.</span><span class="sxs-lookup"><span data-stu-id="419d8-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="419d8-462">No painel **hierarquia** , selecione **gerentes**.</span><span class="sxs-lookup"><span data-stu-id="419d8-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="419d8-463">No painel **Inspetor** , expanda **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="419d8-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="419d8-464">Em **manipulador de entrada de fala**, expanda **Mostrar Underworld**.</span><span class="sxs-lookup"><span data-stu-id="419d8-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="419d8-465">Altere **nenhuma função** para **UnderworldBase. OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="419d8-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Palavra-chave: show Underworld](images/showunderworld.png)

* <span data-ttu-id="419d8-467">Expanda **ocultar Underworld**.</span><span class="sxs-lookup"><span data-stu-id="419d8-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="419d8-468">Altere **nenhuma função** para **UnderworldBase. ondisable**.</span><span class="sxs-lookup"><span data-stu-id="419d8-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Palavra-chave: Ocultar Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="419d8-470">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="419d8-470">Build and Deploy</span></span>

* <span data-ttu-id="419d8-471">Como antes, compile o projeto no Unity e implante-o no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="419d8-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="419d8-472">Após a implantação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="419d8-472">After the application is deployed:</span></span>

* <span data-ttu-id="419d8-473">Face de uma superfície (parede, piso, tabela) e diga *"mostrar Underworld"* .</span><span class="sxs-lookup"><span data-stu-id="419d8-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="419d8-474">O Underworld será mostrado e todos os outros hologramas serão ocultados.</span><span class="sxs-lookup"><span data-stu-id="419d8-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="419d8-475">Se você não vir o Underworld, verifique se está enfrentando uma superfície do mundo real.</span><span class="sxs-lookup"><span data-stu-id="419d8-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="419d8-476">Abordagem em 1 metro do holograma do Underworld e comece a conversar.</span><span class="sxs-lookup"><span data-stu-id="419d8-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="419d8-477">Agora há efeitos de áudio aplicados à sua voz!</span><span class="sxs-lookup"><span data-stu-id="419d8-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="419d8-478">Desative o Underworld e observe como o efeito não é mais aplicado.</span><span class="sxs-lookup"><span data-stu-id="419d8-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="419d8-479">Diga *"Hide Underworld"* para ocultar o Underworld.</span><span class="sxs-lookup"><span data-stu-id="419d8-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="419d8-480">O Underworld ficará oculto e os hologramas ocultos anteriormente serão exibidos novamente.</span><span class="sxs-lookup"><span data-stu-id="419d8-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="419d8-481">Fim</span><span class="sxs-lookup"><span data-stu-id="419d8-481">The End</span></span>

<span data-ttu-id="419d8-482">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="419d8-482">Congratulations!</span></span> <span data-ttu-id="419d8-483">Agora você concluiu o **Sr spatial 220: som espacial**.</span><span class="sxs-lookup"><span data-stu-id="419d8-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="419d8-484">Ouça o mundo e dê vida às suas experiências com o som!</span><span class="sxs-lookup"><span data-stu-id="419d8-484">Listen to the world and bring your experiences to life with sound!</span></span>

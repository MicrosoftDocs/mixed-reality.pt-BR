---
title: Sr noções básicas 101 – projeto completo com o dispositivo
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender as noções básicas sobre a realidade mista do Windows.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidade misturada, realidade do Windows Mixed, HoloLens, holograma, Academia, tutorial
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524020"
---
>[!NOTE]
><span data-ttu-id="49df4-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="49df4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="49df4-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="49df4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="49df4-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="49df4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="49df4-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="49df4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="49df4-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="49df4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="49df4-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="49df4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="49df4-110">Noções básicas do Sr 101: Concluir o projeto com o dispositivo</span><span class="sxs-lookup"><span data-stu-id="49df4-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="49df4-111">Este tutorial o guiará por um projeto completo, criado no Unity, que demonstra os principais recursos do Windows Mixed Reality no HoloLens, incluindo [olhar](gaze.md), [gestos](gestures.md), [entrada de voz](voice-input.md), [som espacial](spatial-sound.md) e [mapeamento espacial](spatial-mapping.md)  .</span><span class="sxs-lookup"><span data-stu-id="49df4-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="49df4-112">O tutorial levará aproximadamente 1 hora para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="49df4-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="49df4-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="49df4-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="49df4-114">Course</span><span class="sxs-lookup"><span data-stu-id="49df4-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="49df4-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="49df4-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="49df4-116"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="49df4-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="49df4-117">Noções básicas do Sr 101: Concluir o projeto com o dispositivo</span><span class="sxs-lookup"><span data-stu-id="49df4-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="49df4-118">✔️</span><span class="sxs-lookup"><span data-stu-id="49df4-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="49df4-119">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="49df4-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="49df4-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="49df4-120">Prerequisites</span></span>

* <span data-ttu-id="49df4-121">Um PC com Windows 10 configurado com as [ferramentas](install-the-tools.md)corretas instaladas.</span><span class="sxs-lookup"><span data-stu-id="49df4-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="49df4-122">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="49df4-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="49df4-123">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="49df4-123">Project files</span></span>

* <span data-ttu-id="49df4-124">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="49df4-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="49df4-125"> Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="49df4-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="49df4-126">Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="49df4-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="49df4-127">Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="49df4-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="49df4-128">Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="49df4-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="49df4-129">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="49df4-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="49df4-130">Mantenha o nome da pasta como **origami**.</span><span class="sxs-lookup"><span data-stu-id="49df4-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="49df4-131">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="49df4-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="49df4-132">Capítulo 1 – mundo "holo"</span><span class="sxs-lookup"><span data-stu-id="49df4-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="49df4-133">Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer o processo de compilação e implantação.</span><span class="sxs-lookup"><span data-stu-id="49df4-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="49df4-134">Objetivos</span><span class="sxs-lookup"><span data-stu-id="49df4-134">Objectives</span></span>

* <span data-ttu-id="49df4-135">Configure o Unity para o desenvolvimento de Holographic.</span><span class="sxs-lookup"><span data-stu-id="49df4-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="49df4-136">Crie um holograma.</span><span class="sxs-lookup"><span data-stu-id="49df4-136">Make a hologram.</span></span>
* <span data-ttu-id="49df4-137">Veja um holograma que você fez.</span><span class="sxs-lookup"><span data-stu-id="49df4-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="49df4-138">Instruções</span><span class="sxs-lookup"><span data-stu-id="49df4-138">Instructions</span></span>

* <span data-ttu-id="49df4-139">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="49df4-139">Start Unity.</span></span>
* <span data-ttu-id="49df4-140">Selecione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="49df4-140">Select **Open**.</span></span>
* <span data-ttu-id="49df4-141">Insira o local como a pasta de **origami** que você cancelou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="49df4-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="49df4-142">Selecione **origami** e clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="49df4-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="49df4-143">Como o projeto de **origami** não contém uma cena, salve a cena padrão vazia em um novo arquivo usando:Arquivo / **salvar cena como**.</span><span class="sxs-lookup"><span data-stu-id="49df4-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="49df4-144">Nomeie o novo **origami** de cena e pressione o botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="49df4-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="49df4-145">Configurar a câmera virtual principal</span><span class="sxs-lookup"><span data-stu-id="49df4-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="49df4-146">No **painel hierarquia**, selecione **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="49df4-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="49df4-147">No **Inspetor** , defina sua posição de transformação como **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="49df4-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="49df4-148">Localize a propriedade **limpar sinalizadores** e altere a lista suspensa de **Skybox** para **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="49df4-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="49df4-149">Clique no campo **plano de fundo** para abrir um seletor de cores.</span><span class="sxs-lookup"><span data-stu-id="49df4-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="49df4-150">Defina **R, G, B e** a como **0**.</span><span class="sxs-lookup"><span data-stu-id="49df4-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="49df4-151">Configurar a cena</span><span class="sxs-lookup"><span data-stu-id="49df4-151">Setup the scene</span></span>

* <span data-ttu-id="49df4-152">No **painel hierarquia**, clique em **criar** e em **criar vazio**.</span><span class="sxs-lookup"><span data-stu-id="49df4-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="49df4-153">Clique com o botão direito do mouse no novo gameobject e selecione Renomear.</span><span class="sxs-lookup"><span data-stu-id="49df4-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="49df4-154">Renomeie o gameobject para **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="49df4-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="49df4-155">Na pasta **hologramas** do painel projeto (expanda ativos e selecione hologramas ou clique duas vezes na pasta hologramas no painel projeto):</span><span class="sxs-lookup"><span data-stu-id="49df4-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="49df4-156">Arraste o **estágio** para a hierarquia para ser um filho de **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="49df4-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="49df4-157">Arraste **Sphere1** para a hierarquia para ser um filho de **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="49df4-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="49df4-158">Arraste **Sphere2** para a hierarquia para ser um filho de **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="49df4-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="49df4-159">Clique com o botão direito do mouse no objeto de **luz direcional** no **painel hierarquia** e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="49df4-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="49df4-160">Na pasta **hologramas** , arraste as **luzes** para a raiz do **painel hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="49df4-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="49df4-161">Na **hierarquia**, selecione o **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="49df4-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="49df4-162">No **Inspetor**, defina a posição de transformação como **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="49df4-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="49df4-163">Pressione o botão **reproduzir** no Unity para visualizar os hologramas.</span><span class="sxs-lookup"><span data-stu-id="49df4-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="49df4-164">Você deve ver os objetos de origami na janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="49df4-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="49df4-165">Pressione **executar** uma segunda vez para parar o modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="49df4-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="49df4-166">Exportar o projeto do Unity para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49df4-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="49df4-167">Em Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="49df4-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="49df4-168">Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="49df4-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="49df4-169">Defina o **SDK** como **Universal 10** e o **tipo de compilação** como **D3D**.</span><span class="sxs-lookup"><span data-stu-id="49df4-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="49df4-170">Verifique **os C# projetos do Unity**.</span><span class="sxs-lookup"><span data-stu-id="49df4-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="49df4-171">Clique em **Adicionar abrir cenas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="49df4-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="49df4-172">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="49df4-172">Click **Build**.</span></span>
* <span data-ttu-id="49df4-173">Na janela Explorador de arquivos que aparece, crie uma **nova pasta** chamada "aplicativo".</span><span class="sxs-lookup"><span data-stu-id="49df4-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="49df4-174">Clique uma vez na **pasta do aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="49df4-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="49df4-175">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="49df4-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="49df4-176">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="49df4-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="49df4-177">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="49df4-177">Open the **App** folder.</span></span>
* <span data-ttu-id="49df4-178">Abra (clique duas vezes) **origami. sln**.</span><span class="sxs-lookup"><span data-stu-id="49df4-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="49df4-179">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="49df4-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="49df4-180">Clique na seta ao lado do botão dispositivo e selecione **computador remoto** para implantar por Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="49df4-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="49df4-181">Defina o **endereço** para o nome ou endereço IP do seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49df4-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="49df4-182">Se você não souber o endereço IP do dispositivo, procure **configurações > rede & Internet > opções avançadas** ou pergunte ao Cortana **"Ei Cortana, qual é meu endereço IP?"**</span><span class="sxs-lookup"><span data-stu-id="49df4-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="49df4-183">Se o HoloLens estiver conectado via USB, você poderá selecionar o **dispositivo** a ser implantado sobre USB.</span><span class="sxs-lookup"><span data-stu-id="49df4-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="49df4-184">Deixe o **modo de autenticação** definido como **Universal**.</span><span class="sxs-lookup"><span data-stu-id="49df4-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="49df4-185">Clique em **selecionar**</span><span class="sxs-lookup"><span data-stu-id="49df4-185">Click **Select**</span></span>

* <span data-ttu-id="49df4-186">Clique em **depurar > iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="49df4-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="49df4-187">Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span><span class="sxs-lookup"><span data-stu-id="49df4-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="49df4-188">O projeto de origami agora será compilado, implantado em seu HoloLens e, em seguida, executado.</span><span class="sxs-lookup"><span data-stu-id="49df4-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="49df4-189">Coloque em seu HoloLens e procure ver os novos hologramas.</span><span class="sxs-lookup"><span data-stu-id="49df4-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="49df4-190">Capítulo 2 – olhar</span><span class="sxs-lookup"><span data-stu-id="49df4-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="49df4-191">Neste capítulo, vamos apresentar a primeira das três maneiras de interagir com seus hologramas-- [olhar](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="49df4-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="49df4-192">Objetivos</span><span class="sxs-lookup"><span data-stu-id="49df4-192">Objectives</span></span>

* <span data-ttu-id="49df4-193">Visualize seu olhar usando um cursor com bloqueio mundial.</span><span class="sxs-lookup"><span data-stu-id="49df4-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="49df4-194">Instruções</span><span class="sxs-lookup"><span data-stu-id="49df4-194">Instructions</span></span>

* <span data-ttu-id="49df4-195">Volte ao seu projeto do Unity e feche a janela de configurações de Build se ela ainda estiver aberta.</span><span class="sxs-lookup"><span data-stu-id="49df4-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="49df4-196">Selecione a pasta hologramas no **painel Projeto**.</span><span class="sxs-lookup"><span data-stu-id="49df4-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="49df4-197">Arraste o objeto **cursor** para o **painel hierarquia** no nível raiz.</span><span class="sxs-lookup"><span data-stu-id="49df4-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="49df4-198">Clique duas vezes no objeto de **cursor** para examiná-lo mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="49df4-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="49df4-199">Clique com o botão direito do mouse na pasta **scripts** no painel projeto.</span><span class="sxs-lookup"><span data-stu-id="49df4-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="49df4-200">Clique no submenu **criar** .</span><span class="sxs-lookup"><span data-stu-id="49df4-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="49df4-201">Selecione  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="49df4-201">Select **C# Script**.</span></span>
* <span data-ttu-id="49df4-202">Nomeie o script **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="49df4-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="49df4-203">Observação: O nome diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="49df4-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="49df4-204">Você não precisa adicionar a extensão. cs.</span><span class="sxs-lookup"><span data-stu-id="49df4-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="49df4-205">Selecione o objeto **cursor** no **painel hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="49df4-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="49df4-206">Arraste e solte o script **WorldCursor** no **painel Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="49df4-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="49df4-207">Clique duas vezes no script **WorldCursor** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49df4-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="49df4-208">Copie e cole esse código em **WorldCursor.cs** e **Salve tudo**.</span><span class="sxs-lookup"><span data-stu-id="49df4-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="49df4-209">Recompile o aplicativo do **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="49df4-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="49df4-210">Retorne à solução do Visual Studio usada anteriormente para implantar em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49df4-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="49df4-211">Selecione ' recarregar tudo ' quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="49df4-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="49df4-212">Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="49df4-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="49df4-213">Agora, observe a cena e observe como o cursor interage com a forma de objetos.</span><span class="sxs-lookup"><span data-stu-id="49df4-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="49df4-214">Capítulo 3-gestos</span><span class="sxs-lookup"><span data-stu-id="49df4-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="49df4-215">Neste capítulo, adicionaremos suporte para [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="49df4-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="49df4-216">Quando o usuário seleciona uma esfera de papel, vamos fazer com que a esfera fique ativando a gravidade usando o mecanismo de física do Unity.</span><span class="sxs-lookup"><span data-stu-id="49df4-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="49df4-217">Objetivos</span><span class="sxs-lookup"><span data-stu-id="49df4-217">Objectives</span></span>

* <span data-ttu-id="49df4-218">Controle seus hologramas com o gesto de seleção.</span><span class="sxs-lookup"><span data-stu-id="49df4-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="49df4-219">Instruções</span><span class="sxs-lookup"><span data-stu-id="49df4-219">Instructions</span></span>

<span data-ttu-id="49df4-220">Vamos começar criando um script e, em seguida, pode detectar o gesto de seleção.</span><span class="sxs-lookup"><span data-stu-id="49df4-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="49df4-221">Na pasta **scripts** , crie um script chamado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="49df4-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="49df4-222">Arraste o script **GazeGestureManager** para o objeto **origamicollection** na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="49df4-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="49df4-223">Abra o script **GazeGestureManager** no Visual Studio e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="49df4-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="49df4-224">Crie outro script na pasta scripts, desta vez com o nome **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="49df4-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="49df4-225">Expanda o objeto origamicollection na exibição hierarquia.</span><span class="sxs-lookup"><span data-stu-id="49df4-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="49df4-226">Arraste o script **SphereCommands** para o objeto **Sphere1** no painel hierarquia.</span><span class="sxs-lookup"><span data-stu-id="49df4-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="49df4-227">Arraste o script **SphereCommands** para o objeto **Sphere2** no painel hierarquia.</span><span class="sxs-lookup"><span data-stu-id="49df4-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="49df4-228">Abra o script no Visual Studio para edição e substitua o código padrão por este:</span><span class="sxs-lookup"><span data-stu-id="49df4-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="49df4-229">Exporte, compile e implante o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49df4-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="49df4-230">Examine um dos seus próprios.</span><span class="sxs-lookup"><span data-stu-id="49df4-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="49df4-231">Execute o gesto de seleção e observe a caixa de círculo na superfície abaixo.</span><span class="sxs-lookup"><span data-stu-id="49df4-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="49df4-232">Capítulo 4-voz</span><span class="sxs-lookup"><span data-stu-id="49df4-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="49df4-233">Neste capítulo, adicionaremos suporte para dois comandos de [voz](voice-input.md): "Redefinir mundo" para retornar as respectivas esferas para seu local original e "soltar a esfera" para fazer a esfera cair.</span><span class="sxs-lookup"><span data-stu-id="49df4-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="49df4-234">Objetivos</span><span class="sxs-lookup"><span data-stu-id="49df4-234">Objectives</span></span>

* <span data-ttu-id="49df4-235">Adicione comandos de voz que sempre escutam em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="49df4-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="49df4-236">Crie um holograma que reage a um comando de voz.</span><span class="sxs-lookup"><span data-stu-id="49df4-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="49df4-237">Instruções</span><span class="sxs-lookup"><span data-stu-id="49df4-237">Instructions</span></span>

* <span data-ttu-id="49df4-238">Na pasta **scripts** , crie um script chamado **speechmanager**.</span><span class="sxs-lookup"><span data-stu-id="49df4-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="49df4-239">Arraste o script speechmanager para o objeto origamicollection na hierarquia</span><span class="sxs-lookup"><span data-stu-id="49df4-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="49df4-240">Abra o script speechmanager no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49df4-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="49df4-241">Copie e cole esse código em **SpeechManager.cs** e **Salve todos**:</span><span class="sxs-lookup"><span data-stu-id="49df4-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="49df4-242">Abra o script **SphereCommands** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49df4-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="49df4-243">Atualize o script para ler da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="49df4-243">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="49df4-244">Exporte, compile e implante o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49df4-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="49df4-245">Examine uma das esferas e, em seguida, diga "**drop Sphere**".</span><span class="sxs-lookup"><span data-stu-id="49df4-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="49df4-246">Diga "**Redefinir mundo**" para trazê-los de volta para suas posições iniciais.</span><span class="sxs-lookup"><span data-stu-id="49df4-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="49df4-247">Capítulo 5-som espacial</span><span class="sxs-lookup"><span data-stu-id="49df4-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="49df4-248">Neste capítulo, vamos adicionar música ao aplicativo e, em seguida, disparar efeitos sonoros em determinadas ações.</span><span class="sxs-lookup"><span data-stu-id="49df4-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="49df4-249">Vamos usar o [som espacial](spatial-sound.md) para dar sons a um local específico no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="49df4-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="49df4-250">Objetivos</span><span class="sxs-lookup"><span data-stu-id="49df4-250">Objectives</span></span>

* <span data-ttu-id="49df4-251">Ouça os hologramas em seu mundo.</span><span class="sxs-lookup"><span data-stu-id="49df4-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="49df4-252">Instruções</span><span class="sxs-lookup"><span data-stu-id="49df4-252">Instructions</span></span>

* <span data-ttu-id="49df4-253">Em Unity SELECT no menu superior, **edite > configurações do projeto > áudio**</span><span class="sxs-lookup"><span data-stu-id="49df4-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="49df4-254">No painel inspetor no lado direito, localize a configuração do **plug-in Spatializer** e selecione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="49df4-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="49df4-255">Na pasta **hologramas** no painel projeto, arraste o objeto **Ambience** para o objeto **origamicollection** no painel hierarquia.</span><span class="sxs-lookup"><span data-stu-id="49df4-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="49df4-256">Selecione **origamicollection** e localize o componente **fonte de áudio** no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="49df4-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="49df4-257">Altere estas propriedades:</span><span class="sxs-lookup"><span data-stu-id="49df4-257">Change these properties:</span></span>
  * <span data-ttu-id="49df4-258">Verifique a Propriedade espacialize.</span><span class="sxs-lookup"><span data-stu-id="49df4-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="49df4-259">Verifique o **jogo em ativo**.</span><span class="sxs-lookup"><span data-stu-id="49df4-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="49df4-260">Altere a **mistura espacial** para **3D** arrastando o controle deslizante para a direita.</span><span class="sxs-lookup"><span data-stu-id="49df4-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="49df4-261">O valor deve mudar de 0 para 1 quando você move o controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="49df4-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="49df4-262">Verifique a propriedade **loop** .</span><span class="sxs-lookup"><span data-stu-id="49df4-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="49df4-263">Expanda **configurações de som 3D**e insira **0,1** para o **nível de Doppler**.</span><span class="sxs-lookup"><span data-stu-id="49df4-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="49df4-264">Definir **rolloff de volume** para **rolloff logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="49df4-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="49df4-265">Defina a **distância máxima** como **20**.</span><span class="sxs-lookup"><span data-stu-id="49df4-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="49df4-266">Na pasta **scripts** , crie um script chamado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="49df4-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="49df4-267">Arraste e solte **SphereSounds** para os objetos **Sphere1** e **Sphere2** na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="49df4-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="49df4-268">Abra o **SphereSounds** no Visual Studio, atualize o código a seguir e **Salve tudo**.</span><span class="sxs-lookup"><span data-stu-id="49df4-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="49df4-269">Salve o script e retorne ao Unity.</span><span class="sxs-lookup"><span data-stu-id="49df4-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="49df4-270">Exporte, compile e implante o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49df4-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="49df4-271">Mova-se mais de perto do palco e gire-o lado a lado para ouvir a alteração dos sons.</span><span class="sxs-lookup"><span data-stu-id="49df4-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="49df4-272">Capítulo 6-mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="49df4-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="49df4-273">Agora vamos usar o [mapeamento espacial](spatial-mapping.md) para posicionar o tabuleiro em um objeto real no mundo real.</span><span class="sxs-lookup"><span data-stu-id="49df4-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="49df4-274">Objetivos</span><span class="sxs-lookup"><span data-stu-id="49df4-274">Objectives</span></span>

* <span data-ttu-id="49df4-275">Traga seu mundo real para o mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="49df4-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="49df4-276">Coloque seus hologramas onde forem mais importantes para você.</span><span class="sxs-lookup"><span data-stu-id="49df4-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="49df4-277">Instruções</span><span class="sxs-lookup"><span data-stu-id="49df4-277">Instructions</span></span>

* <span data-ttu-id="49df4-278">No Unity, clique na pasta **hologramas** no painel projeto.</span><span class="sxs-lookup"><span data-stu-id="49df4-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="49df4-279">Arraste o ativo de **mapeamento espacial** para a raiz da **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="49df4-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="49df4-280">Clique no objeto de **mapeamento espacial** na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="49df4-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="49df4-281">No **painel Inspetor**, altere as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="49df4-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="49df4-282">Marque a caixa **desenhar malhas visuais** .</span><span class="sxs-lookup"><span data-stu-id="49df4-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="49df4-283">Localize **material de desenho** e clique no círculo à direita.</span><span class="sxs-lookup"><span data-stu-id="49df4-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="49df4-284">Digite "**wireframe**" no campo de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="49df4-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="49df4-285">Clique no resultado e feche a janela.</span><span class="sxs-lookup"><span data-stu-id="49df4-285">Click on the result and then close the window.</span></span> <span data-ttu-id="49df4-286">Quando você fizer isso, o valor para o material de desenho deverá ser definido como wireframe.</span><span class="sxs-lookup"><span data-stu-id="49df4-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="49df4-287">Exporte, compile e implante o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49df4-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="49df4-288">Quando o aplicativo é executado, uma malha delineada se sobrepõe ao seu mundo real.</span><span class="sxs-lookup"><span data-stu-id="49df4-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="49df4-289">Observe como uma esfera de rolagem ficará fora do palco e até o andar!</span><span class="sxs-lookup"><span data-stu-id="49df4-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="49df4-290">Agora, mostraremos como mover o Origamicollection para um novo local:</span><span class="sxs-lookup"><span data-stu-id="49df4-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="49df4-291">Na pasta **scripts** , crie um script chamado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="49df4-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="49df4-292">Na **hierarquia**, expanda o **origamicollection** e selecione o objeto **Stage** .</span><span class="sxs-lookup"><span data-stu-id="49df4-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="49df4-293">Arraste o script **TapToPlaceParent** para o objeto Stage.</span><span class="sxs-lookup"><span data-stu-id="49df4-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="49df4-294">Abra o script **TapToPlaceParent** no Visual Studio e atualize-o para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="49df4-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="49df4-295">Exportar, compilar e implantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49df4-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="49df4-296">Agora você deve ser capaz de posicionar o jogo em um local específico por nuvens-lo, usando o gesto de seleção e, em seguida, movendo para um novo local e usando o gesto de seleção novamente.</span><span class="sxs-lookup"><span data-stu-id="49df4-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="49df4-297">Capítulo 7 – diversão Holographic</span><span class="sxs-lookup"><span data-stu-id="49df4-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="49df4-298">Objetivos</span><span class="sxs-lookup"><span data-stu-id="49df4-298">Objectives</span></span>

* <span data-ttu-id="49df4-299">Revele a entrada para um Holographic Underworld.</span><span class="sxs-lookup"><span data-stu-id="49df4-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="49df4-300">Instruções</span><span class="sxs-lookup"><span data-stu-id="49df4-300">Instructions</span></span>

<span data-ttu-id="49df4-301">Agora, mostraremos como descobrir o Holographic Underworld:</span><span class="sxs-lookup"><span data-stu-id="49df4-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="49df4-302">Na pasta **hologramas** no painel Projeto:</span><span class="sxs-lookup"><span data-stu-id="49df4-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="49df4-303">Arraste **Underworld** para a hierarquia para ser um filho de **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="49df4-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="49df4-304">Na pasta **scripts** , crie um script chamado **HitTarget**.</span><span class="sxs-lookup"><span data-stu-id="49df4-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="49df4-305">Na **hierarquia**, expanda o **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="49df4-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="49df4-306">Expanda o objeto de **estágio** e selecione o objeto de **destino** (ventilador azul).</span><span class="sxs-lookup"><span data-stu-id="49df4-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="49df4-307">Arraste o script **HitTarget** para o objeto de **destino** .</span><span class="sxs-lookup"><span data-stu-id="49df4-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="49df4-308">Abra o script **HitTarget** no Visual Studio e atualize-o para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="49df4-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="49df4-309">No Unity, selecione o objeto de **destino** .</span><span class="sxs-lookup"><span data-stu-id="49df4-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="49df4-310">Agora, duas propriedades públicas estão visíveis no componente de **destino de visita** e precisam fazer referência a objetos em nossa cena:</span><span class="sxs-lookup"><span data-stu-id="49df4-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="49df4-311">Arraste **Underworld** do painel **hierarquia** para a propriedade **Underworld** no componente de **destino de visita** .</span><span class="sxs-lookup"><span data-stu-id="49df4-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="49df4-312">Arraste o **estágio** do painel **hierarquia** até o **objeto para ocultar** a propriedade no componente de destino de **visita** .</span><span class="sxs-lookup"><span data-stu-id="49df4-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="49df4-313">Exportar, compilar e implantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49df4-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="49df4-314">Coloque a coleção de origami no piso e, em seguida, use o gesto de seleção para fazer uma queda de esfera.</span><span class="sxs-lookup"><span data-stu-id="49df4-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="49df4-315">Quando a esfera atinge o destino (ventilador azul), ocorrerá uma explosão.</span><span class="sxs-lookup"><span data-stu-id="49df4-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="49df4-316">A coleção será ocultada e um orifício para o Underworld será exibido.</span><span class="sxs-lookup"><span data-stu-id="49df4-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="49df4-317">Fim</span><span class="sxs-lookup"><span data-stu-id="49df4-317">The end</span></span>

<span data-ttu-id="49df4-318">E esse é o fim deste tutorial!</span><span class="sxs-lookup"><span data-stu-id="49df4-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="49df4-319">Você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="49df4-319">You learned:</span></span>

* <span data-ttu-id="49df4-320">Como criar um aplicativo Holographic no Unity.</span><span class="sxs-lookup"><span data-stu-id="49df4-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="49df4-321">Como fazer uso de olhar, gesto, voz, som e mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="49df4-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="49df4-322">Como criar e implantar um aplicativo usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49df4-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="49df4-323">Agora você está pronto para começar a criar sua própria experiência de Holographic!</span><span class="sxs-lookup"><span data-stu-id="49df4-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="49df4-324">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49df4-324">See also</span></span>

* [<span data-ttu-id="49df4-325">Noções básicas do MR 101E: projeto completo com emulador</span><span class="sxs-lookup"><span data-stu-id="49df4-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="49df4-326">Foco</span><span class="sxs-lookup"><span data-stu-id="49df4-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="49df4-327">Gestos</span><span class="sxs-lookup"><span data-stu-id="49df4-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="49df4-328">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="49df4-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="49df4-329">Som espacial</span><span class="sxs-lookup"><span data-stu-id="49df4-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="49df4-330">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="49df4-330">Spatial mapping</span></span>](spatial-mapping.md)

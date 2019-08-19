---
title: Sr Basics 101E – projeto completo com o emulador
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o emulador do HoloLens para aprender as noções básicas de um aplicativo Holographic.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidade misturada, realidade do Windows Mixed, HoloLens, holograma, Academia, tutorial, emulador
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522327"
---
>[!NOTE]
><span data-ttu-id="0b100-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0b100-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0b100-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="0b100-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0b100-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0b100-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0b100-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="0b100-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0b100-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0b100-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0b100-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="0b100-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="0b100-110">101E de noções básicas do Sr: Concluir o projeto com o emulador</span><span class="sxs-lookup"><span data-stu-id="0b100-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="0b100-111">Este tutorial o guiará por um projeto completo, criado no Unity, que demonstra os principais recursos do Windows Mixed Reality no HoloLens, incluindo [olhar](gaze.md), [gestos](gestures.md), [entrada de voz](voice-input.md), [som espacial](spatial-sound.md) e [mapeamento espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0b100-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="0b100-112">O tutorial levará aproximadamente 1 hora para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="0b100-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="0b100-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="0b100-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0b100-114">Course</span><span class="sxs-lookup"><span data-stu-id="0b100-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0b100-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0b100-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0b100-116"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="0b100-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0b100-117">101E de noções básicas do Sr: Concluir o projeto com o emulador</span><span class="sxs-lookup"><span data-stu-id="0b100-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="0b100-118">✔️</span><span class="sxs-lookup"><span data-stu-id="0b100-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0b100-119">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="0b100-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0b100-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0b100-120">Prerequisites</span></span>

* <span data-ttu-id="0b100-121">Um PC com Windows 10 configurado com as [ferramentas](install-the-tools.md)corretas instaladas.</span><span class="sxs-lookup"><span data-stu-id="0b100-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="0b100-122">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="0b100-122">Project files</span></span>

* <span data-ttu-id="0b100-123">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="0b100-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="0b100-124"> Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="0b100-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0b100-125">Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0b100-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="0b100-126">Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0b100-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="0b100-127">Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="0b100-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="0b100-128">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="0b100-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0b100-129">Mantenha o nome da pasta como **origami**.</span><span class="sxs-lookup"><span data-stu-id="0b100-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="0b100-130">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="0b100-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0b100-131">Capítulo 1 – mundo "holo"</span><span class="sxs-lookup"><span data-stu-id="0b100-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="0b100-132">Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer o processo de compilação e implantação.</span><span class="sxs-lookup"><span data-stu-id="0b100-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b100-133">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0b100-133">Objectives</span></span>

* <span data-ttu-id="0b100-134">Configure o Unity para o desenvolvimento de Holographic.</span><span class="sxs-lookup"><span data-stu-id="0b100-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="0b100-135">Crie um holograma.</span><span class="sxs-lookup"><span data-stu-id="0b100-135">Make a hologram.</span></span>
* <span data-ttu-id="0b100-136">Veja um holograma que você fez.</span><span class="sxs-lookup"><span data-stu-id="0b100-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b100-137">Instruções</span><span class="sxs-lookup"><span data-stu-id="0b100-137">Instructions</span></span>

* <span data-ttu-id="0b100-138">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="0b100-138">Start Unity.</span></span>
* <span data-ttu-id="0b100-139">Selecione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="0b100-139">Select **Open**.</span></span>
* <span data-ttu-id="0b100-140">Insira o local como a pasta de **origami** que você cancelou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b100-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="0b100-141">Selecione **origami** e clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="0b100-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="0b100-142">Salve a nova cena:Arquivo / **salvar cena como**.</span><span class="sxs-lookup"><span data-stu-id="0b100-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="0b100-143">Nomeie o **origami** da cena e pressione o botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="0b100-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="0b100-144">Configurar a câmera principal</span><span class="sxs-lookup"><span data-stu-id="0b100-144">Setup the main camera</span></span>

* <span data-ttu-id="0b100-145">No **painel hierarquia**, selecione **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="0b100-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="0b100-146">No **Inspetor** , defina sua posição de transformação como **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="0b100-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="0b100-147">Localize a propriedade **limpar sinalizadores** e altere a lista suspensa de **Skybox** para **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="0b100-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="0b100-148">Clique no campo **plano de fundo** para abrir um seletor de cores.</span><span class="sxs-lookup"><span data-stu-id="0b100-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="0b100-149">Defina **R, G, B e** a como **0**.</span><span class="sxs-lookup"><span data-stu-id="0b100-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="0b100-150">Configurar a cena</span><span class="sxs-lookup"><span data-stu-id="0b100-150">Setup the scene</span></span>

* <span data-ttu-id="0b100-151">No **painel hierarquia**, clique em **criar** e em **criar vazio**.</span><span class="sxs-lookup"><span data-stu-id="0b100-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="0b100-152">Clique com o botão direito do mouse no novo gameobject e selecione Renomear.</span><span class="sxs-lookup"><span data-stu-id="0b100-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="0b100-153">Renomeie o gameobject para **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0b100-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="0b100-154">Na pasta **hologramas** no **painel Projeto**:</span><span class="sxs-lookup"><span data-stu-id="0b100-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="0b100-155">Arraste o **estágio** para a hierarquia para ser um filho de **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0b100-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0b100-156">Arraste **Sphere1** para a hierarquia para ser um filho de **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0b100-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0b100-157">Arraste **Sphere2** para a hierarquia para ser um filho de **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0b100-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0b100-158">Clique com o botão direito do mouse no objeto de **luz direcional** no **painel hierarquia** e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="0b100-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="0b100-159">Na pasta **hologramas** , arraste as **luzes** para a raiz do **painel hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="0b100-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="0b100-160">Na **hierarquia**, selecione o **origamicollection**.</span><span class="sxs-lookup"><span data-stu-id="0b100-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0b100-161">No **Inspetor**, defina a posição de transformação como **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="0b100-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="0b100-162">Pressione o botão **reproduzir** no Unity para visualizar os hologramas.</span><span class="sxs-lookup"><span data-stu-id="0b100-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0b100-163">Você deve ver os objetos de origami na janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="0b100-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="0b100-164">Pressione **executar** uma segunda vez para parar o modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="0b100-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="0b100-165">Exportar o projeto do Unity para o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b100-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="0b100-166">Em Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="0b100-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="0b100-167">Selecione **Windows Store** na lista **plataforma** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="0b100-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="0b100-168">Defina o **SDK** como **Universal 10** e o **tipo de compilação** como **D3D**.</span><span class="sxs-lookup"><span data-stu-id="0b100-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="0b100-169">Verifique **os C# projetos do Unity**.</span><span class="sxs-lookup"><span data-stu-id="0b100-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="0b100-170">Clique em **Adicionar abrir cenas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="0b100-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0b100-171">Clique em **configurações do Player...** .</span><span class="sxs-lookup"><span data-stu-id="0b100-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="0b100-172">No painel Inspetor, selecione o **logotipo da Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="0b100-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="0b100-173">Em seguida, selecione **configurações de publicação**.</span><span class="sxs-lookup"><span data-stu-id="0b100-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="0b100-174">Na seção **recursos** , selecione os recursos de **microfone** e **SpatialPerception** .</span><span class="sxs-lookup"><span data-stu-id="0b100-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="0b100-175">De volta à janela configurações de compilação, clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="0b100-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="0b100-176">Crie uma **nova pasta** chamada "app".</span><span class="sxs-lookup"><span data-stu-id="0b100-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0b100-177">Clique uma vez na **pasta do aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="0b100-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="0b100-178">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="0b100-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="0b100-179">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="0b100-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0b100-180">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="0b100-180">Open the **App** folder.</span></span>
* <span data-ttu-id="0b100-181">Abra a **solução de origami do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0b100-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="0b100-182">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="0b100-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="0b100-183">Clique na seta ao lado do botão dispositivo e selecione emulador do **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0b100-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="0b100-184">Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="0b100-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="0b100-185">Após algum tempo, o emulador começará com o projeto de origami.</span><span class="sxs-lookup"><span data-stu-id="0b100-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="0b100-186">Ao iniciar o [emulador](using-the-hololens-emulator.md)pela primeira vez, pode levar até 15 minutos para que o emulador seja inicializado.</span><span class="sxs-lookup"><span data-stu-id="0b100-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="0b100-187">Quando ele for iniciado, não o feche.</span><span class="sxs-lookup"><span data-stu-id="0b100-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="0b100-188">Capítulo 2 – olhar</span><span class="sxs-lookup"><span data-stu-id="0b100-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="0b100-189">Neste capítulo, vamos apresentar a primeira das três maneiras de interagir com seus hologramas-- [olhar](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="0b100-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="0b100-190">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0b100-190">Objectives</span></span>

* <span data-ttu-id="0b100-191">Visualize seu olhar usando um cursor com bloqueio mundial.</span><span class="sxs-lookup"><span data-stu-id="0b100-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b100-192">Instruções</span><span class="sxs-lookup"><span data-stu-id="0b100-192">Instructions</span></span>

* <span data-ttu-id="0b100-193">Volte ao seu projeto do Unity e feche a janela de configurações de Build se ela ainda estiver aberta.</span><span class="sxs-lookup"><span data-stu-id="0b100-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="0b100-194">Selecione a pasta hologramas no **painel Projeto**.</span><span class="sxs-lookup"><span data-stu-id="0b100-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="0b100-195">Arraste o objeto **cursor** para o **painel hierarquia** no nível raiz.</span><span class="sxs-lookup"><span data-stu-id="0b100-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="0b100-196">Clique duas vezes no objeto de **cursor** para examiná-lo mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="0b100-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="0b100-197">Clique com o botão direito do mouse na pasta **scripts** no painel projeto.</span><span class="sxs-lookup"><span data-stu-id="0b100-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="0b100-198">Clique no submenu **criar** .</span><span class="sxs-lookup"><span data-stu-id="0b100-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="0b100-199">Selecione  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="0b100-199">Select **C# Script**.</span></span>
* <span data-ttu-id="0b100-200">Nomeie o script **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="0b100-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="0b100-201">Observação: O nome diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0b100-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="0b100-202">Você não precisa adicionar a extensão. cs.</span><span class="sxs-lookup"><span data-stu-id="0b100-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="0b100-203">Selecione o objeto **cursor** no **painel hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="0b100-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="0b100-204">Arraste e solte o script **WorldCursor** no **painel Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="0b100-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="0b100-205">Clique duas vezes no script **WorldCursor** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b100-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0b100-206">Copie e cole esse código em **WorldCursor.cs** e **Salve tudo**.</span><span class="sxs-lookup"><span data-stu-id="0b100-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move thecursor to the point where the raycast hit.
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

* <span data-ttu-id="0b100-207">Recompile o aplicativo do **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="0b100-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="0b100-208">Retorne à solução do Visual Studio usada anteriormente para implantar no emulador.</span><span class="sxs-lookup"><span data-stu-id="0b100-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="0b100-209">Selecione ' recarregar tudo ' quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="0b100-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="0b100-210">Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="0b100-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0b100-211">Use o controlador Xbox para examinar a cena.</span><span class="sxs-lookup"><span data-stu-id="0b100-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="0b100-212">Observe como o cursor interage com a forma de objetos.</span><span class="sxs-lookup"><span data-stu-id="0b100-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="0b100-213">Capítulo 3-gestos</span><span class="sxs-lookup"><span data-stu-id="0b100-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="0b100-214">Neste capítulo, adicionaremos suporte para [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="0b100-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="0b100-215">Quando o usuário seleciona uma esfera de papel, vamos fazer com que a esfera fique ativando a gravidade usando o mecanismo de física do Unity.</span><span class="sxs-lookup"><span data-stu-id="0b100-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b100-216">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0b100-216">Objectives</span></span>

* <span data-ttu-id="0b100-217">Controle seus hologramas com o gesto de seleção.</span><span class="sxs-lookup"><span data-stu-id="0b100-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b100-218">Instruções</span><span class="sxs-lookup"><span data-stu-id="0b100-218">Instructions</span></span>

<span data-ttu-id="0b100-219">Vamos começar criando um script do que pode detectar o gesto de seleção.</span><span class="sxs-lookup"><span data-stu-id="0b100-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="0b100-220">Na pasta **scripts** , crie um script chamado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="0b100-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="0b100-221">Arraste o script **GazeGestureManager** para o objeto **origamicollection** na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="0b100-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="0b100-222">Abra o script **GazeGestureManager** no Visual Studio e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0b100-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Start()
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

* <span data-ttu-id="0b100-223">Crie outro script na pasta scripts, desta vez com o nome **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="0b100-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="0b100-224">Expanda o objeto origamicollection na exibição hierarquia.</span><span class="sxs-lookup"><span data-stu-id="0b100-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="0b100-225">Arraste o script **SphereCommands** para o objeto **Sphere1** no painel hierarquia.</span><span class="sxs-lookup"><span data-stu-id="0b100-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0b100-226">Arraste o script **SphereCommands** para o objeto **Sphere2** no painel hierarquia.</span><span class="sxs-lookup"><span data-stu-id="0b100-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0b100-227">Abra o script no Visual Studio para edição e substitua o código padrão por este:</span><span class="sxs-lookup"><span data-stu-id="0b100-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="0b100-228">Exporte, compile e implante o aplicativo no emulador do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b100-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0b100-229">Examine a cena e centralize-a em um dos seus próprios.</span><span class="sxs-lookup"><span data-stu-id="0b100-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="0b100-230">Pressione o **botão a** no controlador Xbox ou pressione a barra de espaços para simular o gesto de seleção.</span><span class="sxs-lookup"><span data-stu-id="0b100-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="0b100-231">Capítulo 4-voz</span><span class="sxs-lookup"><span data-stu-id="0b100-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="0b100-232">Neste capítulo, adicionaremos suporte para dois comandos de [voz](voice-input.md): "Redefinir mundo" para retorna o que caiu para o local original e "soltar a esfera" para que a esfera caia.</span><span class="sxs-lookup"><span data-stu-id="0b100-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b100-233">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0b100-233">Objectives</span></span>

* <span data-ttu-id="0b100-234">Adicione comandos de voz que sempre escutam em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0b100-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="0b100-235">Crie um holograma que reage a um comando de voz.</span><span class="sxs-lookup"><span data-stu-id="0b100-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b100-236">Instruções</span><span class="sxs-lookup"><span data-stu-id="0b100-236">Instructions</span></span>

* <span data-ttu-id="0b100-237">Na pasta **scripts** , crie um script chamado **speechmanager**.</span><span class="sxs-lookup"><span data-stu-id="0b100-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="0b100-238">Arraste o script speechmanager para o objeto origamicollection na hierarquia</span><span class="sxs-lookup"><span data-stu-id="0b100-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="0b100-239">Abra o script speechmanager no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b100-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0b100-240">Copie e cole esse código em **SpeechManager.cs** e **Salve todos**:</span><span class="sxs-lookup"><span data-stu-id="0b100-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="0b100-241">Abra o script **SphereCommands** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b100-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="0b100-242">Atualize o script para ler da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0b100-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="0b100-243">Exporte, compile e implante o aplicativo no emulador do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b100-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0b100-244">O emulador dará suporte ao microfone do seu PC e responderá à sua voz: ajuste a exibição para que o cursor esteja em um dos seus esferas e, em seguida, diga "drop Sphere".</span><span class="sxs-lookup"><span data-stu-id="0b100-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="0b100-245">Diga "**Redefinir mundo**" para trazê-los de volta para suas posições iniciais.</span><span class="sxs-lookup"><span data-stu-id="0b100-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="0b100-246">Capítulo 5-som espacial</span><span class="sxs-lookup"><span data-stu-id="0b100-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="0b100-247">Neste capítulo, vamos adicionar música ao aplicativo e, em seguida, disparar efeitos sonoros em determinadas ações.</span><span class="sxs-lookup"><span data-stu-id="0b100-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="0b100-248">Vamos usar o [som espacial](spatial-sound.md) para dar sons a um local específico no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="0b100-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b100-249">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0b100-249">Objectives</span></span>

* <span data-ttu-id="0b100-250">Ouça os hologramas em seu mundo.</span><span class="sxs-lookup"><span data-stu-id="0b100-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b100-251">Instruções</span><span class="sxs-lookup"><span data-stu-id="0b100-251">Instructions</span></span>

* <span data-ttu-id="0b100-252">Na seleção do Unity, no menu superior, **edite > configurações do projeto > áudio**</span><span class="sxs-lookup"><span data-stu-id="0b100-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="0b100-253">Localize a configuração do **plug-in Spatializer** e selecione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="0b100-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="0b100-254">Na pasta **hologramas** , arraste o objeto **Ambience** para o objeto **origamicollection** no painel hierarquia.</span><span class="sxs-lookup"><span data-stu-id="0b100-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="0b100-255">Selecione **origamicollection** e localize o componente **fonte de áudio** .</span><span class="sxs-lookup"><span data-stu-id="0b100-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="0b100-256">Altere estas propriedades:</span><span class="sxs-lookup"><span data-stu-id="0b100-256">Change these properties:</span></span>
  * <span data-ttu-id="0b100-257">Verifique a Propriedade espacialize.</span><span class="sxs-lookup"><span data-stu-id="0b100-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="0b100-258">Verifique o **jogo em ativo**.</span><span class="sxs-lookup"><span data-stu-id="0b100-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="0b100-259">Altere a **mistura espacial** para **3D** arrastando o controle deslizante para a direita.</span><span class="sxs-lookup"><span data-stu-id="0b100-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="0b100-260">Verifique a propriedade **loop** .</span><span class="sxs-lookup"><span data-stu-id="0b100-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="0b100-261">Expanda **configurações de som 3D**e insira **0,1** para o **nível de Doppler**.</span><span class="sxs-lookup"><span data-stu-id="0b100-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="0b100-262">Definir **rolloff de volume** para **rolloff logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="0b100-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="0b100-263">Defina a **distância máxima** como **20**.</span><span class="sxs-lookup"><span data-stu-id="0b100-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="0b100-264">Na pasta **scripts** , crie um script chamado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="0b100-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="0b100-265">Arraste **SphereSounds** para os objetos **Sphere1** e **Sphere2** na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="0b100-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="0b100-266">Abra o **SphereSounds** no Visual Studio, atualize o código a seguir e **Salve tudo**.</span><span class="sxs-lookup"><span data-stu-id="0b100-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="0b100-267">Salve o script e retorne ao Unity.</span><span class="sxs-lookup"><span data-stu-id="0b100-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="0b100-268">Exporte, compile e implante o aplicativo no emulador do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b100-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0b100-269">Ouça os fones de ouvido para obter o efeito completo e avance mais de perto do palco para ouvir a alteração dos sons.</span><span class="sxs-lookup"><span data-stu-id="0b100-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="0b100-270">Capítulo 6-mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="0b100-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="0b100-271">Agora vamos usar o [mapeamento espacial](spatial-mapping.md) para posicionar o tabuleiro em um objeto real no mundo real.</span><span class="sxs-lookup"><span data-stu-id="0b100-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="0b100-272">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0b100-272">Objectives</span></span>

* <span data-ttu-id="0b100-273">Traga seu mundo real para o mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="0b100-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="0b100-274">Coloque seus hologramas onde forem mais importantes para você.</span><span class="sxs-lookup"><span data-stu-id="0b100-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="0b100-275">Instruções</span><span class="sxs-lookup"><span data-stu-id="0b100-275">Instructions</span></span>

* <span data-ttu-id="0b100-276">Clique na pasta **hologramas** no painel projeto.</span><span class="sxs-lookup"><span data-stu-id="0b100-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="0b100-277">Arraste o ativo de **mapeamento espacial** para a raiz da **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="0b100-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="0b100-278">Clique no objeto de **mapeamento espacial** na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="0b100-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="0b100-279">No **painel Inspetor**, altere as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="0b100-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="0b100-280">Marque a caixa **desenhar malhas visuais** .</span><span class="sxs-lookup"><span data-stu-id="0b100-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="0b100-281">Localize **material de desenho** e clique no círculo à direita.</span><span class="sxs-lookup"><span data-stu-id="0b100-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="0b100-282">Digite "**wireframe**" no campo de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="0b100-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="0b100-283">Clique no resultado e feche a janela.</span><span class="sxs-lookup"><span data-stu-id="0b100-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="0b100-284">Exporte, compile e implante o aplicativo no emulador do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0b100-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0b100-285">Quando o aplicativo é executado, uma malha de uma sala de vida real examinada anteriormente será renderizada em wireframe.</span><span class="sxs-lookup"><span data-stu-id="0b100-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="0b100-286">Observe como uma esfera de rolagem ficará fora do palco e até o andar!</span><span class="sxs-lookup"><span data-stu-id="0b100-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="0b100-287">Agora, mostraremos como mover o Origamicollection para um novo local:</span><span class="sxs-lookup"><span data-stu-id="0b100-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="0b100-288">Na pasta **scripts** , crie um script chamado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="0b100-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="0b100-289">Na **hierarquia**, expanda o **origamicollection** e selecione o objeto **Stage** .</span><span class="sxs-lookup"><span data-stu-id="0b100-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="0b100-290">Arraste o script **TapToPlaceParent** para o objeto Stage.</span><span class="sxs-lookup"><span data-stu-id="0b100-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="0b100-291">Abra o script **TapToPlaceParent** no Visual Studio e atualize-o para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0b100-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="0b100-292">Exportar, compilar e implantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b100-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0b100-293">Agora você deve ser capaz de posicionar o jogo em um local específico por nuvens-lo, usando o gesto de seleção (**uma barra de** espaços) e, em seguida, movendo para um novo local e usando o gesto de seleção novamente.</span><span class="sxs-lookup"><span data-stu-id="0b100-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="0b100-294">Fim</span><span class="sxs-lookup"><span data-stu-id="0b100-294">The end</span></span>

<span data-ttu-id="0b100-295">E esse é o fim deste tutorial!</span><span class="sxs-lookup"><span data-stu-id="0b100-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="0b100-296">Você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="0b100-296">You learned:</span></span>

* <span data-ttu-id="0b100-297">Como criar um aplicativo Holographic no Unity.</span><span class="sxs-lookup"><span data-stu-id="0b100-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="0b100-298">Como fazer uso de olhar, gesto, voz, sons e mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="0b100-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="0b100-299">Como criar e implantar um aplicativo usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b100-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="0b100-300">Agora você está pronto para começar a criar seus próprios aplicativos Holographic!</span><span class="sxs-lookup"><span data-stu-id="0b100-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="0b100-301">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b100-301">See also</span></span>

* [<span data-ttu-id="0b100-302">Noções básicas do MR 101: projeto completo com dispositivo</span><span class="sxs-lookup"><span data-stu-id="0b100-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="0b100-303">Foco</span><span class="sxs-lookup"><span data-stu-id="0b100-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="0b100-304">Gestos</span><span class="sxs-lookup"><span data-stu-id="0b100-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="0b100-305">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="0b100-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="0b100-306">Som espacial</span><span class="sxs-lookup"><span data-stu-id="0b100-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="0b100-307">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="0b100-307">Spatial mapping</span></span>](spatial-mapping.md)

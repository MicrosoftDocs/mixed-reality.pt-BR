---
title: Fundamentos do MR 101E - projeto completo com o emulador
description: Siga este passo a passo usando o Unity, o Visual Studio e o emulador do HoloLens para aprender os fundamentos de um aplicativo holográfico de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidade misturada, realidade mista do Windows, HoloLens, holograma, o emulador do tutorial, academy
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589453"
---
>[!NOTE]
><span data-ttu-id="5d1ab-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5d1ab-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5d1ab-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5d1ab-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5d1ab-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5d1ab-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="5d1ab-110">Noções básicas sobre MR 101E: Projeto completo com o emulador</span><span class="sxs-lookup"><span data-stu-id="5d1ab-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="5d1ab-111">Este tutorial orientará você por meio de um projeto completo, compilado no Unity, que demonstra os principais recursos do Windows Mixed Reality em, incluindo HoloLens [olhares](gaze.md), [gestos](gestures.md), [deentradadevoz](voice-input.md), [som espacial](spatial-sound.md) e [mapeamento espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="5d1ab-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="5d1ab-112">O tutorial levará cerca de 1 hora para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="5d1ab-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5d1ab-114">Curso</span><span class="sxs-lookup"><span data-stu-id="5d1ab-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5d1ab-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5d1ab-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5d1ab-116"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="5d1ab-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5d1ab-117">Noções básicas sobre MR 101E: Projeto completo com o emulador</span><span class="sxs-lookup"><span data-stu-id="5d1ab-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="5d1ab-118">✔️</span><span class="sxs-lookup"><span data-stu-id="5d1ab-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5d1ab-119">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="5d1ab-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5d1ab-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-120">Prerequisites</span></span>

* <span data-ttu-id="5d1ab-121">Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5d1ab-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="5d1ab-122">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="5d1ab-122">Project files</span></span>

* <span data-ttu-id="5d1ab-123">Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="5d1ab-124"> Requer o Unity 2017.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="5d1ab-125">Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="5d1ab-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="5d1ab-126">Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="5d1ab-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="5d1ab-127">Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="5d1ab-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="5d1ab-128">Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="5d1ab-129">Mantenha o nome da pasta como **Origami**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="5d1ab-130">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="5d1ab-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="5d1ab-131">Capítulo 1 - world "Holo"</span><span class="sxs-lookup"><span data-stu-id="5d1ab-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="5d1ab-132">Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer a compilação e o processo de implantação.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="5d1ab-133">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-133">Objectives</span></span>

* <span data-ttu-id="5d1ab-134">Configure o Unity para o desenvolvimento holográfico.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="5d1ab-135">Faça um holograma.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-135">Make a hologram.</span></span>
* <span data-ttu-id="5d1ab-136">Consulte um holograma que você fez.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="5d1ab-137">Instruções</span><span class="sxs-lookup"><span data-stu-id="5d1ab-137">Instructions</span></span>

* <span data-ttu-id="5d1ab-138">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-138">Start Unity.</span></span>
* <span data-ttu-id="5d1ab-139">Selecione **aberto**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-139">Select **Open**.</span></span>
* <span data-ttu-id="5d1ab-140">Insira o local como o **Origami** pasta você anteriormente não arquivadas.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="5d1ab-141">Selecione **Origami** e clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="5d1ab-142">Salve a nova cena: **Arquivo** / **salvar cena como**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="5d1ab-143">Nomeie a cena **Origami** e pressione a **salvar** botão.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="5d1ab-144">A câmera principal de instalação</span><span class="sxs-lookup"><span data-stu-id="5d1ab-144">Setup the main camera</span></span>

* <span data-ttu-id="5d1ab-145">No **painel de hierarquia**, selecione **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="5d1ab-146">No **Inspector** defina sua posição de transformação **0, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="5d1ab-147">Localizar o **Limpar sinalizadores** propriedade e altere a lista suspensa de **Skybox** para **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="5d1ab-148">Clique no **plano de fundo** campo para abrir um seletor de cores.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="5d1ab-149">Definir **R, G, B e A** à **0**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="5d1ab-150">Instalação da cena</span><span class="sxs-lookup"><span data-stu-id="5d1ab-150">Setup the scene</span></span>

* <span data-ttu-id="5d1ab-151">No **painel de hierarquia**, clique em **Create** e **criar vazio**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="5d1ab-152">Clique com botão direito a nova **GameObject** e selecione Renomear.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="5d1ab-153">Renomeie o GameObject para **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="5d1ab-154">Dos **hologramas** pasta o **painel projeto**:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="5d1ab-155">Arraste **estágio** na hierarquia para ser um filho do **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="5d1ab-156">Arraste **Sphere1** na hierarquia para ser um filho do **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="5d1ab-157">Arraste **Sphere2** na hierarquia para ser um filho do **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="5d1ab-158">Com o botão direito do **luz direcional** do objeto na **painel de hierarquia** e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="5d1ab-159">Dos **hologramas** pasta, arraste **luzes** na raiz do **painel de hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="5d1ab-160">No **hierarquia**, selecione o **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="5d1ab-161">No **Inspector**, defina a posição de transformação **0, -0,5, 2.0**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="5d1ab-162">Pressione a **reproduzir** botão no Unity para visualizar seu hologramas.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="5d1ab-163">Você deve ver os objetos do Origami na janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="5d1ab-164">Pressione **reproduzir** uma segunda vez para parar o modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="5d1ab-165">Exportar o projeto do Unity para Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5d1ab-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="5d1ab-166">No, selecione Unity **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="5d1ab-167">Selecione **Windows Store** na **plataforma** lista e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="5d1ab-168">Definir **SDK** à **10 Universal** e **tipo de Build** para **D3D**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="5d1ab-169">Verifique **Unity C# projetos**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="5d1ab-170">Clique em **cenas abra Adicionar** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="5d1ab-171">Clique em **configurações do Player...** .</span><span class="sxs-lookup"><span data-stu-id="5d1ab-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="5d1ab-172">No, selecione Painel Inspetor a **logotipo do Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="5d1ab-173">Em seguida, selecione **configurações de publicação**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="5d1ab-174">No **capacidades** seção, selecione a **microfone** e **SpatialPerception** recursos.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="5d1ab-175">Na janela Configurações de compilação, clique em **Build**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="5d1ab-176">Criar uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="5d1ab-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="5d1ab-177">Único clique a **pasta aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="5d1ab-178">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="5d1ab-179">Quando Unity é feito, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="5d1ab-180">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-180">Open the **App** folder.</span></span>
* <span data-ttu-id="5d1ab-181">Abra o **solução do Visual Studio Origami**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="5d1ab-182">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **X86**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="5d1ab-183">Clique na seta ao lado do botão de dispositivo e selecione **HoloLens emulador**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="5d1ab-184">Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="5d1ab-185">Após algum tempo, o emulador será iniciado com o projeto Origami.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="5d1ab-186">Ao iniciar pela primeira vez o [emulador](using-the-hololens-emulator.md), ele pode levar até 15 minutos para que o emulador será iniciado.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="5d1ab-187">Depois que ele é iniciado, não o feche.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="5d1ab-188">Capítulo 2 - olhar</span><span class="sxs-lookup"><span data-stu-id="5d1ab-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="5d1ab-189">Neste capítulo, vamos apresentar a primeira das três maneiras de interagir com seu hologramas – [olhares](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="5d1ab-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="5d1ab-190">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-190">Objectives</span></span>

* <span data-ttu-id="5d1ab-191">Visualize seu foco usando um cursor bloqueado pelo mundo.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="5d1ab-192">Instruções</span><span class="sxs-lookup"><span data-stu-id="5d1ab-192">Instructions</span></span>

* <span data-ttu-id="5d1ab-193">Volte para seu projeto do Unity e fechar a janela de configurações de compilação se ele ainda está aberto.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="5d1ab-194">Selecione o **hologramas** pasta o **painel projeto**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="5d1ab-195">Arraste o **Cursor** do objeto para o **painel de hierarquia** no nível raiz.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="5d1ab-196">Clique duas vezes no **Cursor** objeto para examiná-lo.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="5d1ab-197">Clique com botão direito no **Scripts** pasta no painel de projeto.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="5d1ab-198">Clique o **criar** submenu.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="5d1ab-199">Selecione  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-199">Select **C# Script**.</span></span>
* <span data-ttu-id="5d1ab-200">Nomeie o script **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="5d1ab-201">Observação: O nome diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="5d1ab-202">Você não precisará adicionar a extensão. cs.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="5d1ab-203">Selecione o **Cursor** do objeto na **painel de hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="5d1ab-204">Arraste e solte os **WorldCursor** o script na **painel Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="5d1ab-205">Clique duas vezes o **WorldCursor** script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="5d1ab-206">Copie e cole este código em **WorldCursor.cs** e **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="5d1ab-207">Recompile o aplicativo do **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="5d1ab-208">Retorne para a solução do Visual Studio usada anteriormente para implantar no emulador.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="5d1ab-209">Selecione 'Recarregar todos' quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="5d1ab-210">Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="5d1ab-211">Use o controlador do Xbox para olhar em volta da cena.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="5d1ab-212">Observe como o cursor interage com a forma de objetos.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="5d1ab-213">Capítulo 3 - gestos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="5d1ab-214">Neste capítulo, vamos adicionar suporte para [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="5d1ab-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="5d1ab-215">Quando o usuário seleciona uma esfera de papel, faremos a esfera se enquadram ativando gravidade usando o mecanismo de física do Unity.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="5d1ab-216">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-216">Objectives</span></span>

* <span data-ttu-id="5d1ab-217">Controle seu hologramas com o gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="5d1ab-218">Instruções</span><span class="sxs-lookup"><span data-stu-id="5d1ab-218">Instructions</span></span>

<span data-ttu-id="5d1ab-219">Vamos começar criando um script que pode detectar o gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="5d1ab-220">No **Scripts** pasta, crie um script chamado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="5d1ab-221">Arraste o **GazeGestureManager** de script para o **OrigamiCollection** objeto na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="5d1ab-222">Abra o **GazeGestureManager** script no Visual Studio e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="5d1ab-223">Criar outro script na pasta Scripts, desta vez denominada **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="5d1ab-224">Expanda o **OrigamiCollection** objeto na exibição de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="5d1ab-225">Arraste o **SphereCommands** gerar script para o **Sphere1** objeto no painel de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="5d1ab-226">Arraste o **SphereCommands** gerar script para o **Sphere2** objeto no painel de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="5d1ab-227">Abra o script no Visual Studio para edição e substitua o código padrão com este:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="5d1ab-228">Exportar, criar e implantar o aplicativo no emulador do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5d1ab-229">Olhar em volta da cena e center em um das esferas.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="5d1ab-230">Pressione a **um** botão no controlador Xbox ou pressione a Spacebar para simular o gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="5d1ab-231">Capítulo 4 - voz</span><span class="sxs-lookup"><span data-stu-id="5d1ab-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="5d1ab-232">Neste capítulo, vamos adicionar suporte para dois [comandos de voz](voice-input.md): "Redefinir world" para retorna esferas soltos no local original e "Soltar esfera" para fazer com que a esfera se encaixam.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="5d1ab-233">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-233">Objectives</span></span>

* <span data-ttu-id="5d1ab-234">Adicione comandos de voz que sempre escutam em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="5d1ab-235">Crie um holograma que reage a um comando de voz.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="5d1ab-236">Instruções</span><span class="sxs-lookup"><span data-stu-id="5d1ab-236">Instructions</span></span>

* <span data-ttu-id="5d1ab-237">No **Scripts** pasta, crie um script chamado **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="5d1ab-238">Arraste o **SpeechManager** de script para o **OrigamiCollection** objeto na hierarquia</span><span class="sxs-lookup"><span data-stu-id="5d1ab-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="5d1ab-239">Abra o **SpeechManager** script no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="5d1ab-240">Copie e cole este código em **SpeechManager.cs** e **Salvar tudo**:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="5d1ab-241">Abra o **SphereCommands** script no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="5d1ab-242">Atualize o script da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="5d1ab-243">Exportar, criar e implantar o aplicativo no emulador do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5d1ab-244">O emulador dará suporte microfone do PC e responder a sua voz: ajuste o modo de exibição, para que o cursor estiver em um das esferas e dizer "Drop esfera".</span><span class="sxs-lookup"><span data-stu-id="5d1ab-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="5d1ab-245">Dizer "**mundo redefinir**" para colocá-los de volta para suas posições iniciais.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="5d1ab-246">Capítulo 5 – som espacial</span><span class="sxs-lookup"><span data-stu-id="5d1ab-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="5d1ab-247">Neste capítulo, vamos adicionar música para o aplicativo e, em seguida, disparar efeitos de som em determinadas ações.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="5d1ab-248">Usaremos [som espacial](spatial-sound.md) dar sons um local específico no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="5d1ab-249">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-249">Objectives</span></span>

* <span data-ttu-id="5d1ab-250">Ouça hologramas seu mundo.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="5d1ab-251">Instruções</span><span class="sxs-lookup"><span data-stu-id="5d1ab-251">Instructions</span></span>

* <span data-ttu-id="5d1ab-252">No menu superior, selecione Unity **Editar > configurações do projeto > áudio**</span><span class="sxs-lookup"><span data-stu-id="5d1ab-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="5d1ab-253">Localizar o **plug-in do Spatializer** definição e selecione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="5d1ab-254">Dos **hologramas** pasta, arraste o **ambiente** do objeto para o **OrigamiCollection** objeto no painel de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="5d1ab-255">Selecione **OrigamiCollection** e localize o **Audio Source** componente.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="5d1ab-256">Altere essas propriedades:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-256">Change these properties:</span></span>
  * <span data-ttu-id="5d1ab-257">Verifique as **Spatialize** propriedade.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="5d1ab-258">Verifique as **tocar no ativo**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="5d1ab-259">Alteração **Blend espacial** à **3D** arrastando o controle deslizante para a direita.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="5d1ab-260">Verifique as **Loop** propriedade.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="5d1ab-261">Expandir **configurações de som 3D**e insira **0,1** para **nível Doppler**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="5d1ab-262">Definir **Volume Rolloff** à **Rolloff logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="5d1ab-263">Definir **distância máxima** à **20**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="5d1ab-264">No **Scripts** pasta, crie um script chamado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="5d1ab-265">Arraste **SphereSounds** para o **Sphere1** e **Sphere2** objetos na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="5d1ab-266">Abra **SphereSounds** no Visual Studio, atualize o código a seguir e **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="5d1ab-267">Salve o script e retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="5d1ab-268">Exportar, criar e implantar o aplicativo no emulador do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5d1ab-269">Use fones de ouvido para obter o efeito completo e mover mais próximo e mais longe ao Palco para ouvir os sons alterar.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="5d1ab-270">Mapeamento de capítulos 6 - espacial</span><span class="sxs-lookup"><span data-stu-id="5d1ab-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="5d1ab-271">Agora, vamos usar [mapeamento espacial](spatial-mapping.md) para colocar o tabuleiro do jogo em um objeto real no mundo real.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="5d1ab-272">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-272">Objectives</span></span>

* <span data-ttu-id="5d1ab-273">Traga o seu mundo real para o mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="5d1ab-274">Coloque seu hologramas onde eles mais importam para você.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="5d1ab-275">Instruções</span><span class="sxs-lookup"><span data-stu-id="5d1ab-275">Instructions</span></span>

* <span data-ttu-id="5d1ab-276">Clique no **hologramas** pasta no painel de projeto.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="5d1ab-277">Arraste o **mapeamento espacial** ativo na raiz do **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="5d1ab-278">Clique no **mapeamento espacial** objeto na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="5d1ab-279">No **painel Inspetor**, altere as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="5d1ab-280">Verifique as **desenhar malhas Visual** caixa.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="5d1ab-281">Localize **desenhar Material** e clique no círculo no lado direito.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="5d1ab-282">Tipo "**wireframe**" no campo de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="5d1ab-283">Clique no resultado e, em seguida, feche a janela.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="5d1ab-284">Exportar, criar e implantar o aplicativo no emulador do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5d1ab-285">Quando o aplicativo é executado, uma malha de uma sala de estar reais digitalizada anteriormente será renderizada no wireframe.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="5d1ab-286">Assista como uma esfera sem interrupção cairá desativar o estágio e, para o chão!</span><span class="sxs-lookup"><span data-stu-id="5d1ab-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="5d1ab-287">Agora, mostraremos como mover o OrigamiCollection para um novo local:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="5d1ab-288">No **Scripts** pasta, crie um script chamado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="5d1ab-289">No **hierarquia**, expanda o **OrigamiCollection** e selecione o **estágio** objeto.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="5d1ab-290">Arraste o **TapToPlaceParent** script para o objeto de estágio.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="5d1ab-291">Abra o **TapToPlaceParent** de script no Visual Studio e atualizá-lo para ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="5d1ab-292">Exportar, criar e implantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="5d1ab-293">Agora você agora deve ser capaz de colocar o jogo em um local específico, Observação nisso, usar o gesto de Select (**um** ou barra de espaços) e, em seguida, movendo para um novo local e usar o gesto de Select novamente.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="5d1ab-294">Fim</span><span class="sxs-lookup"><span data-stu-id="5d1ab-294">The end</span></span>

<span data-ttu-id="5d1ab-295">E esse é o final deste tutorial!</span><span class="sxs-lookup"><span data-stu-id="5d1ab-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="5d1ab-296">Você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="5d1ab-296">You learned:</span></span>

* <span data-ttu-id="5d1ab-297">Como criar um aplicativo holográfico no Unity.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="5d1ab-298">Como fazer uso de olhar, gesto, voz, sons e mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="5d1ab-299">Como criar e implantar um aplicativo usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5d1ab-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="5d1ab-300">Agora você está pronto para começar a criar seus próprios aplicativos holográfico!</span><span class="sxs-lookup"><span data-stu-id="5d1ab-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="5d1ab-301">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d1ab-301">See also</span></span>

* [<span data-ttu-id="5d1ab-302">Noções básicas sobre MR 101: Projeto completo do dispositivo</span><span class="sxs-lookup"><span data-stu-id="5d1ab-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="5d1ab-303">Gaze</span><span class="sxs-lookup"><span data-stu-id="5d1ab-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="5d1ab-304">Gestos</span><span class="sxs-lookup"><span data-stu-id="5d1ab-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="5d1ab-305">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="5d1ab-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="5d1ab-306">Som espacial</span><span class="sxs-lookup"><span data-stu-id="5d1ab-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="5d1ab-307">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="5d1ab-307">Spatial mapping</span></span>](spatial-mapping.md)

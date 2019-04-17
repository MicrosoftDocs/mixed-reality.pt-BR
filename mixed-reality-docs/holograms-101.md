---
title: Fundamentos do MR 101 - projeto completo do dispositivo
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os fundamentos da realidade mista do Windows.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidade, realidade mista do Windows, HoloLens, misturada holograma, academy, tutorial
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589444"
---
>[!NOTE]
><span data-ttu-id="b50f4-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="b50f4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b50f4-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b50f4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b50f4-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="b50f4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b50f4-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="b50f4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b50f4-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b50f4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b50f4-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="b50f4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="b50f4-110">Noções básicas sobre MR 101: Projeto completo do dispositivo</span><span class="sxs-lookup"><span data-stu-id="b50f4-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="b50f4-111">Este tutorial orientará você por meio de um projeto completo, compilado no Unity, que demonstra os principais recursos do Windows Mixed Reality em, incluindo HoloLens [olhares](gaze.md), [gestos](gestures.md), [deentradadevoz](voice-input.md), [som espacial](spatial-sound.md) e [mapeamento espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="b50f4-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="b50f4-112">O tutorial levará cerca de 1 hora para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="b50f4-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="b50f4-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="b50f4-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b50f4-114">Curso</span><span class="sxs-lookup"><span data-stu-id="b50f4-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b50f4-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b50f4-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b50f4-116"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="b50f4-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b50f4-117">Noções básicas sobre MR 101: Projeto completo do dispositivo</span><span class="sxs-lookup"><span data-stu-id="b50f4-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="b50f4-118">✔️</span><span class="sxs-lookup"><span data-stu-id="b50f4-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="b50f4-119">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="b50f4-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b50f4-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b50f4-120">Prerequisites</span></span>

* <span data-ttu-id="b50f4-121">Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="b50f4-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="b50f4-122">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="b50f4-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="b50f4-123">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="b50f4-123">Project files</span></span>

* <span data-ttu-id="b50f4-124">Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="b50f4-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="b50f4-125"> Requer o Unity 2017.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="b50f4-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="b50f4-126">Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="b50f4-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="b50f4-127">Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="b50f4-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="b50f4-128">Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="b50f4-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="b50f4-129">Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.</span><span class="sxs-lookup"><span data-stu-id="b50f4-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="b50f4-130">Mantenha o nome da pasta como **Origami**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="b50f4-131">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="b50f4-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="b50f4-132">Capítulo 1 - world "Holo"</span><span class="sxs-lookup"><span data-stu-id="b50f4-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="b50f4-133">Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer a compilação e o processo de implantação.</span><span class="sxs-lookup"><span data-stu-id="b50f4-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="b50f4-134">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b50f4-134">Objectives</span></span>

* <span data-ttu-id="b50f4-135">Configure o Unity para o desenvolvimento holográfico.</span><span class="sxs-lookup"><span data-stu-id="b50f4-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="b50f4-136">Faça um holograma.</span><span class="sxs-lookup"><span data-stu-id="b50f4-136">Make a hologram.</span></span>
* <span data-ttu-id="b50f4-137">Consulte um holograma que você fez.</span><span class="sxs-lookup"><span data-stu-id="b50f4-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="b50f4-138">Instruções</span><span class="sxs-lookup"><span data-stu-id="b50f4-138">Instructions</span></span>

* <span data-ttu-id="b50f4-139">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="b50f4-139">Start Unity.</span></span>
* <span data-ttu-id="b50f4-140">Selecione **aberto**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-140">Select **Open**.</span></span>
* <span data-ttu-id="b50f4-141">Insira o local como o **Origami** pasta você anteriormente não arquivadas.</span><span class="sxs-lookup"><span data-stu-id="b50f4-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="b50f4-142">Selecione **Origami** e clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="b50f4-143">Uma vez que o **Origami** projeto não contém uma cena, salve a cena padrão vazio para um novo arquivo usando: **Arquivo** / **salvar cena como**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="b50f4-144">Nomeie a nova cena **Origami** e pressione a **salvar** botão.</span><span class="sxs-lookup"><span data-stu-id="b50f4-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="b50f4-145">A câmera virtual principal de instalação</span><span class="sxs-lookup"><span data-stu-id="b50f4-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="b50f4-146">No **painel de hierarquia**, selecione **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="b50f4-147">No **Inspector** defina sua posição de transformação **0, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="b50f4-148">Localizar o **Limpar sinalizadores** propriedade e altere a lista suspensa de **Skybox** para **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="b50f4-149">Clique no **plano de fundo** campo para abrir um seletor de cores.</span><span class="sxs-lookup"><span data-stu-id="b50f4-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="b50f4-150">Definir **R, G, B e A** à **0**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="b50f4-151">Instalação da cena</span><span class="sxs-lookup"><span data-stu-id="b50f4-151">Setup the scene</span></span>

* <span data-ttu-id="b50f4-152">No **painel de hierarquia**, clique em **Create** e **criar vazio**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="b50f4-153">Clique com botão direito a nova **GameObject** e selecione Renomear.</span><span class="sxs-lookup"><span data-stu-id="b50f4-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="b50f4-154">Renomeie o GameObject para **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="b50f4-155">Dos **hologramas** pasta no painel projeto (expanda ativos e selecione hologramas ou clique duas vezes a pasta hologramas no painel de projeto):</span><span class="sxs-lookup"><span data-stu-id="b50f4-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="b50f4-156">Arraste **estágio** na hierarquia para ser um filho do **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="b50f4-157">Arraste **Sphere1** na hierarquia para ser um filho do **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="b50f4-158">Arraste **Sphere2** na hierarquia para ser um filho do **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="b50f4-159">Com o botão direito do **luz direcional** do objeto na **painel de hierarquia** e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="b50f4-160">Dos **hologramas** pasta, arraste **luzes** na raiz do **painel de hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="b50f4-161">No **hierarquia**, selecione o **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="b50f4-162">No **Inspector**, defina a posição de transformação **0, -0,5, 2.0**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="b50f4-163">Pressione a **reproduzir** botão no Unity para visualizar seu hologramas.</span><span class="sxs-lookup"><span data-stu-id="b50f4-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="b50f4-164">Você deve ver os objetos do Origami na janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="b50f4-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="b50f4-165">Pressione **reproduzir** uma segunda vez para parar o modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="b50f4-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="b50f4-166">Exportar o projeto do Unity para Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b50f4-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="b50f4-167">No, selecione Unity **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="b50f4-168">Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="b50f4-169">Definir **SDK** à **10 Universal** e **tipo de Build** para **D3D**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="b50f4-170">Verifique **Unity C# projetos**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="b50f4-171">Clique em **cenas abra Adicionar** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="b50f4-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="b50f4-172">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-172">Click **Build**.</span></span>
* <span data-ttu-id="b50f4-173">Na janela do Gerenciador de arquivo aparece, crie uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="b50f4-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="b50f4-174">Único clique a **pasta aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="b50f4-175">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="b50f4-176">Quando Unity é feito, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="b50f4-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="b50f4-177">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="b50f4-177">Open the **App** folder.</span></span>
* <span data-ttu-id="b50f4-178">Abrir (clique duas vezes) **Origami.sln**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="b50f4-179">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **X86**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="b50f4-180">Clique na seta ao lado do botão de dispositivo e selecione **computador remoto** para implantar por Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="b50f4-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="b50f4-181">Defina as **endereço** no nome ou endereço IP do seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b50f4-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="b50f4-182">Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas** ou perguntar ao Cortana **"Ei Cortana, o que é meu endereço IP?"**</span><span class="sxs-lookup"><span data-stu-id="b50f4-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="b50f4-183">Se o HoloLens estiver conectado por USB, em vez disso, você pode selecionar **dispositivo** para implantar por USB.</span><span class="sxs-lookup"><span data-stu-id="b50f4-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="b50f4-184">Deixe o **modo de autenticação** definido como **Universal**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="b50f4-185">Clique em **selecionar**</span><span class="sxs-lookup"><span data-stu-id="b50f4-185">Click **Select**</span></span>

* <span data-ttu-id="b50f4-186">Clique em **Depurar > Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="b50f4-187">Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span><span class="sxs-lookup"><span data-stu-id="b50f4-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="b50f4-188">O projeto Origami agora compilar, implantar para o HoloLens e, em seguida, execute.</span><span class="sxs-lookup"><span data-stu-id="b50f4-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="b50f4-189">Coloque o HoloLens e olhar em volta para ver seu novo hologramas.</span><span class="sxs-lookup"><span data-stu-id="b50f4-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="b50f4-190">Capítulo 2 - olhar</span><span class="sxs-lookup"><span data-stu-id="b50f4-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="b50f4-191">Neste capítulo, vamos apresentar a primeira das três maneiras de interagir com seu hologramas – [olhares](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="b50f4-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="b50f4-192">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b50f4-192">Objectives</span></span>

* <span data-ttu-id="b50f4-193">Visualize seu foco usando um cursor bloqueado pelo mundo.</span><span class="sxs-lookup"><span data-stu-id="b50f4-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="b50f4-194">Instruções</span><span class="sxs-lookup"><span data-stu-id="b50f4-194">Instructions</span></span>

* <span data-ttu-id="b50f4-195">Volte para seu projeto do Unity e fechar a janela de configurações de compilação se ele ainda está aberto.</span><span class="sxs-lookup"><span data-stu-id="b50f4-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="b50f4-196">Selecione o **hologramas** pasta o **painel projeto**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="b50f4-197">Arraste o **Cursor** do objeto para o **painel de hierarquia** no nível raiz.</span><span class="sxs-lookup"><span data-stu-id="b50f4-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="b50f4-198">Clique duas vezes no **Cursor** objeto para examiná-lo.</span><span class="sxs-lookup"><span data-stu-id="b50f4-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="b50f4-199">Clique com botão direito no **Scripts** pasta no painel de projeto.</span><span class="sxs-lookup"><span data-stu-id="b50f4-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="b50f4-200">Clique o **criar** submenu.</span><span class="sxs-lookup"><span data-stu-id="b50f4-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="b50f4-201">Selecione  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-201">Select **C# Script**.</span></span>
* <span data-ttu-id="b50f4-202">Nomeie o script **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="b50f4-203">Observação: O nome diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="b50f4-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="b50f4-204">Você não precisará adicionar a extensão. cs.</span><span class="sxs-lookup"><span data-stu-id="b50f4-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="b50f4-205">Selecione o **Cursor** do objeto na **painel de hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="b50f4-206">Arraste e solte os **WorldCursor** o script na **painel Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="b50f4-207">Clique duas vezes o **WorldCursor** script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b50f4-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="b50f4-208">Copie e cole este código em **WorldCursor.cs** e **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="b50f4-209">Recompile o aplicativo do **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="b50f4-210">Retorne para a solução do Visual Studio usada anteriormente para implantar para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b50f4-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="b50f4-211">Selecione 'Recarregar todos' quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="b50f4-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="b50f4-212">Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="b50f4-213">Agora olhar em volta da cena e observe como o cursor interage com a forma de objetos.</span><span class="sxs-lookup"><span data-stu-id="b50f4-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="b50f4-214">Capítulo 3 - gestos</span><span class="sxs-lookup"><span data-stu-id="b50f4-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="b50f4-215">Neste capítulo, vamos adicionar suporte para [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="b50f4-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="b50f4-216">Quando o usuário seleciona uma esfera de papel, faremos a esfera se enquadram ativando gravidade usando o mecanismo de física do Unity.</span><span class="sxs-lookup"><span data-stu-id="b50f4-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="b50f4-217">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b50f4-217">Objectives</span></span>

* <span data-ttu-id="b50f4-218">Controle seu hologramas com o gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="b50f4-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="b50f4-219">Instruções</span><span class="sxs-lookup"><span data-stu-id="b50f4-219">Instructions</span></span>

<span data-ttu-id="b50f4-220">Vamos começar criando um script e pode detectar o gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="b50f4-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="b50f4-221">No **Scripts** pasta, crie um script chamado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="b50f4-222">Arraste o **GazeGestureManager** de script para o **OrigamiCollection** objeto na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="b50f4-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="b50f4-223">Abra o **GazeGestureManager** script no Visual Studio e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b50f4-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="b50f4-224">Criar outro script na pasta Scripts, desta vez denominada **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="b50f4-225">Expanda o **OrigamiCollection** objeto na exibição de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="b50f4-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="b50f4-226">Arraste o **SphereCommands** gerar script para o **Sphere1** objeto no painel de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="b50f4-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="b50f4-227">Arraste o **SphereCommands** gerar script para o **Sphere2** objeto no painel de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="b50f4-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="b50f4-228">Abra o script no Visual Studio para edição e substitua o código padrão com este:</span><span class="sxs-lookup"><span data-stu-id="b50f4-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="b50f4-229">Exportar, criar e implantar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b50f4-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b50f4-230">Examinar um das esferas.</span><span class="sxs-lookup"><span data-stu-id="b50f4-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="b50f4-231">Faça o gesto de select e assista a esfera solte na superfície de abaixo.</span><span class="sxs-lookup"><span data-stu-id="b50f4-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="b50f4-232">Capítulo 4 - voz</span><span class="sxs-lookup"><span data-stu-id="b50f4-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="b50f4-233">Neste capítulo, vamos adicionar suporte para dois [comandos de voz](voice-input.md): "Redefinir world" para retornar as esferas soltos no local original e, em seguida, "Descartar esfera" para fazer com que a esfera se encaixam.</span><span class="sxs-lookup"><span data-stu-id="b50f4-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="b50f4-234">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b50f4-234">Objectives</span></span>

* <span data-ttu-id="b50f4-235">Adicione comandos de voz que sempre escutam em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="b50f4-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="b50f4-236">Crie um holograma que reage a um comando de voz.</span><span class="sxs-lookup"><span data-stu-id="b50f4-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="b50f4-237">Instruções</span><span class="sxs-lookup"><span data-stu-id="b50f4-237">Instructions</span></span>

* <span data-ttu-id="b50f4-238">No **Scripts** pasta, crie um script chamado **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="b50f4-239">Arraste o **SpeechManager** de script para o **OrigamiCollection** objeto na hierarquia</span><span class="sxs-lookup"><span data-stu-id="b50f4-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="b50f4-240">Abra o **SpeechManager** script no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b50f4-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="b50f4-241">Copie e cole este código em **SpeechManager.cs** e **Salvar tudo**:</span><span class="sxs-lookup"><span data-stu-id="b50f4-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="b50f4-242">Abra o **SphereCommands** script no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b50f4-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="b50f4-243">Atualize o script da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="b50f4-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="b50f4-244">Exportar, criar e implantar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b50f4-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b50f4-245">Examinar um das esferas e dizer "**Drop esfera**".</span><span class="sxs-lookup"><span data-stu-id="b50f4-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="b50f4-246">Dizer "**mundo redefinir**" para colocá-los de volta para suas posições iniciais.</span><span class="sxs-lookup"><span data-stu-id="b50f4-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="b50f4-247">Capítulo 5 – som espacial</span><span class="sxs-lookup"><span data-stu-id="b50f4-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="b50f4-248">Neste capítulo, vamos adicionar música para o aplicativo e, em seguida, disparar efeitos de som em determinadas ações.</span><span class="sxs-lookup"><span data-stu-id="b50f4-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="b50f4-249">Usaremos [som espacial](spatial-sound.md) dar sons um local específico no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="b50f4-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="b50f4-250">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b50f4-250">Objectives</span></span>

* <span data-ttu-id="b50f4-251">Ouça hologramas seu mundo.</span><span class="sxs-lookup"><span data-stu-id="b50f4-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="b50f4-252">Instruções</span><span class="sxs-lookup"><span data-stu-id="b50f4-252">Instructions</span></span>

* <span data-ttu-id="b50f4-253">No menu superior, selecione Unity **Editar > configurações do projeto > áudio**</span><span class="sxs-lookup"><span data-stu-id="b50f4-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="b50f4-254">No painel Inspetor no lado direito, localize o **plug-in do Spatializer** definição e selecione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="b50f4-255">Dos **hologramas** pasta no painel de projeto, arraste o **ambiente** do objeto para o **OrigamiCollection** objeto no painel de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="b50f4-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="b50f4-256">Selecione **OrigamiCollection** e localize o **Audio Source** componente no painel Inspetor.</span><span class="sxs-lookup"><span data-stu-id="b50f4-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="b50f4-257">Altere essas propriedades:</span><span class="sxs-lookup"><span data-stu-id="b50f4-257">Change these properties:</span></span>
  * <span data-ttu-id="b50f4-258">Verifique as **Spatialize** propriedade.</span><span class="sxs-lookup"><span data-stu-id="b50f4-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="b50f4-259">Verifique as **tocar no ativo**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="b50f4-260">Alteração **Blend espacial** à **3D** arrastando o controle deslizante para a direita.</span><span class="sxs-lookup"><span data-stu-id="b50f4-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="b50f4-261">O valor deve alterar de 0 para 1 quando você move o controle deslizante.</span><span class="sxs-lookup"><span data-stu-id="b50f4-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="b50f4-262">Verifique as **Loop** propriedade.</span><span class="sxs-lookup"><span data-stu-id="b50f4-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="b50f4-263">Expandir **configurações de som 3D**e insira **0,1** para **nível Doppler**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="b50f4-264">Definir **Volume Rolloff** à **Rolloff logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="b50f4-265">Definir **distância máxima** à **20**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="b50f4-266">No **Scripts** pasta, crie um script chamado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="b50f4-267">Arrastar e soltar **SphereSounds** para o **Sphere1** e **Sphere2** objetos na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="b50f4-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="b50f4-268">Abra **SphereSounds** no Visual Studio, atualize o código a seguir e **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="b50f4-269">Salve o script e retornar para o Unity.</span><span class="sxs-lookup"><span data-stu-id="b50f4-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="b50f4-270">Exportar, criar e implantar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b50f4-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b50f4-271">Mover mais próximo e mais longe do estágio e ativar lado a lado para ouvir os sons alterar.</span><span class="sxs-lookup"><span data-stu-id="b50f4-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="b50f4-272">Mapeamento de capítulos 6 - espacial</span><span class="sxs-lookup"><span data-stu-id="b50f4-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="b50f4-273">Agora, vamos usar [mapeamento espacial](spatial-mapping.md) para colocar o tabuleiro do jogo em um objeto real no mundo real.</span><span class="sxs-lookup"><span data-stu-id="b50f4-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="b50f4-274">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b50f4-274">Objectives</span></span>

* <span data-ttu-id="b50f4-275">Traga o seu mundo real para o mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="b50f4-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="b50f4-276">Coloque seu hologramas onde eles mais importam para você.</span><span class="sxs-lookup"><span data-stu-id="b50f4-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="b50f4-277">Instruções</span><span class="sxs-lookup"><span data-stu-id="b50f4-277">Instructions</span></span>

* <span data-ttu-id="b50f4-278">No Unity, clique no **hologramas** pasta no painel de projeto.</span><span class="sxs-lookup"><span data-stu-id="b50f4-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="b50f4-279">Arraste o **mapeamento espacial** ativo na raiz do **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="b50f4-280">Clique no **mapeamento espacial** objeto na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="b50f4-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="b50f4-281">No **painel Inspetor**, altere as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b50f4-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="b50f4-282">Verifique as **desenhar malhas Visual** caixa.</span><span class="sxs-lookup"><span data-stu-id="b50f4-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="b50f4-283">Localize **desenhar Material** e clique no círculo no lado direito.</span><span class="sxs-lookup"><span data-stu-id="b50f4-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="b50f4-284">Tipo "**wireframe**" no campo de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="b50f4-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="b50f4-285">Clique no resultado e, em seguida, feche a janela.</span><span class="sxs-lookup"><span data-stu-id="b50f4-285">Click on the result and then close the window.</span></span> <span data-ttu-id="b50f4-286">Quando você fizer isso, o valor para desenhar o Material deve obter definido como Wireframe.</span><span class="sxs-lookup"><span data-stu-id="b50f4-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="b50f4-287">Exportar, criar e implantar o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b50f4-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b50f4-288">Quando o aplicativo é executado, uma malha de wireframe irá sobrepor seu mundo real.</span><span class="sxs-lookup"><span data-stu-id="b50f4-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="b50f4-289">Assista como uma esfera sem interrupção cairá desativar o estágio e, para o chão!</span><span class="sxs-lookup"><span data-stu-id="b50f4-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="b50f4-290">Agora, mostraremos como mover o OrigamiCollection para um novo local:</span><span class="sxs-lookup"><span data-stu-id="b50f4-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="b50f4-291">No **Scripts** pasta, crie um script chamado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="b50f4-292">No **hierarquia**, expanda o **OrigamiCollection** e selecione o **estágio** objeto.</span><span class="sxs-lookup"><span data-stu-id="b50f4-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="b50f4-293">Arraste o **TapToPlaceParent** script para o objeto de estágio.</span><span class="sxs-lookup"><span data-stu-id="b50f4-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="b50f4-294">Abra o **TapToPlaceParent** de script no Visual Studio e atualizá-lo para ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b50f4-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="b50f4-295">Exportar, criar e implantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b50f4-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="b50f4-296">Agora você agora poderá colocar o jogo em um local específico Observação-lo, usando o gesto de Select e, em seguida, movendo para um novo local, e usando o gesto de Select novamente.</span><span class="sxs-lookup"><span data-stu-id="b50f4-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="b50f4-297">Capítulo 7 - holográfica diversão</span><span class="sxs-lookup"><span data-stu-id="b50f4-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="b50f4-298">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b50f4-298">Objectives</span></span>

* <span data-ttu-id="b50f4-299">Revele a porta de entrada para um mundo virtual holographic.</span><span class="sxs-lookup"><span data-stu-id="b50f4-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="b50f4-300">Instruções</span><span class="sxs-lookup"><span data-stu-id="b50f4-300">Instructions</span></span>

<span data-ttu-id="b50f4-301">Agora mostraremos a você como descobrir o mundo virtual holográfica:</span><span class="sxs-lookup"><span data-stu-id="b50f4-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="b50f4-302">Dos **hologramas** pasta no painel de projeto:</span><span class="sxs-lookup"><span data-stu-id="b50f4-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="b50f4-303">Arraste **mundo virtual** na hierarquia para ser um filho do **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="b50f4-304">No **Scripts** pasta, crie um script chamado **HitTarget**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="b50f4-305">No **hierarquia**, expanda o **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="b50f4-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="b50f4-306">Expanda o **estágio** do objeto e selecione o **destino** (ventilador azul) do objeto.</span><span class="sxs-lookup"><span data-stu-id="b50f4-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="b50f4-307">Arraste o **HitTarget** gerar script para o **destino** objeto.</span><span class="sxs-lookup"><span data-stu-id="b50f4-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="b50f4-308">Abra o **HitTarget** de script no Visual Studio e atualizá-lo para ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b50f4-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="b50f4-309">No Unity, selecione a **destino** objeto.</span><span class="sxs-lookup"><span data-stu-id="b50f4-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="b50f4-310">Duas propriedades públicas agora estão visíveis na **ocorrências destino** componente e a necessidade de objetos de referência em nossa cena:</span><span class="sxs-lookup"><span data-stu-id="b50f4-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="b50f4-311">Arraste **mundo virtual** da **hierarquia** do painel para o **mundo virtual** propriedade no **atingido o destino** componente.</span><span class="sxs-lookup"><span data-stu-id="b50f4-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="b50f4-312">Arraste **estágio** da **hierarquia** do painel para o **objeto para ocultar** propriedade no **atingido o destino** componente.</span><span class="sxs-lookup"><span data-stu-id="b50f4-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="b50f4-313">Exportar, criar e implantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b50f4-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="b50f4-314">Coloque a coleção do Origami no chão e, em seguida, usar o gesto de Select para tornar uma esfera drop.</span><span class="sxs-lookup"><span data-stu-id="b50f4-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="b50f4-315">Quando a esfera atinge o destino (ventilador azul), ocorrerá um detalhamento.</span><span class="sxs-lookup"><span data-stu-id="b50f4-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="b50f4-316">A coleção será ocultada e um buraco para o mundo virtual será exibida.</span><span class="sxs-lookup"><span data-stu-id="b50f4-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="b50f4-317">Fim</span><span class="sxs-lookup"><span data-stu-id="b50f4-317">The end</span></span>

<span data-ttu-id="b50f4-318">E esse é o final deste tutorial!</span><span class="sxs-lookup"><span data-stu-id="b50f4-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="b50f4-319">Você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="b50f4-319">You learned:</span></span>

* <span data-ttu-id="b50f4-320">Como criar um aplicativo holográfico no Unity.</span><span class="sxs-lookup"><span data-stu-id="b50f4-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="b50f4-321">Como fazer uso de olhar, gesto, voz, som e o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="b50f4-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="b50f4-322">Como criar e implantar um aplicativo usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b50f4-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="b50f4-323">Agora você está pronto para começar a criar sua própria experiência holográfica!</span><span class="sxs-lookup"><span data-stu-id="b50f4-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="b50f4-324">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b50f4-324">See also</span></span>

* [<span data-ttu-id="b50f4-325">Noções básicas sobre MR 101E: Projeto completo com o emulador</span><span class="sxs-lookup"><span data-stu-id="b50f4-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="b50f4-326">Gaze</span><span class="sxs-lookup"><span data-stu-id="b50f4-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="b50f4-327">Gestos</span><span class="sxs-lookup"><span data-stu-id="b50f4-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="b50f4-328">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="b50f4-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="b50f4-329">Som espacial</span><span class="sxs-lookup"><span data-stu-id="b50f4-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b50f4-330">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="b50f4-330">Spatial mapping</span></span>](spatial-mapping.md)

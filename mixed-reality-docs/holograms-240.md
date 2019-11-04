---
title: Sr Sharing 240-vários dispositivos HoloLens
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes do compartilhamento de hologramas.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, compartilhamento, rede, Academia, tutorial
ms.openlocfilehash: 0d8e8f4484546d82caadf162623a6f4059eb2f00
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434569"
---
>[!NOTE]
><span data-ttu-id="fb27d-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="fb27d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fb27d-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="fb27d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fb27d-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb27d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fb27d-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="fb27d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fb27d-108">[Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fb27d-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="fb27d-109">Sr Sharing 240: vários dispositivos HoloLens</span><span class="sxs-lookup"><span data-stu-id="fb27d-109">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="fb27d-110">Os hologramas têm a presença em nosso mundo, permanecendo em vigor conforme avançamos no espaço.</span><span class="sxs-lookup"><span data-stu-id="fb27d-110">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="fb27d-111">O HoloLens mantém os hologramas em vigor usando vários [sistemas de coordenadas](coordinate-systems.md) para controlar o local e a orientação dos objetos.</span><span class="sxs-lookup"><span data-stu-id="fb27d-111">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="fb27d-112">Quando compartilhamos esses sistemas de coordenadas entre dispositivos, podemos criar uma experiência compartilhada que nos permite participar de um mundo Holographic compartilhado.</span><span class="sxs-lookup"><span data-stu-id="fb27d-112">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="fb27d-113">Neste tutorial, iremos:</span><span class="sxs-lookup"><span data-stu-id="fb27d-113">In this tutorial, we will:</span></span>

* <span data-ttu-id="fb27d-114">Configure uma rede para uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="fb27d-114">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="fb27d-115">Compartilhe hologramas entre dispositivos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb27d-115">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="fb27d-116">Descubra outras pessoas em nosso mundo Holographic compartilhado.</span><span class="sxs-lookup"><span data-stu-id="fb27d-116">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="fb27d-117">Crie uma experiência interativa compartilhada onde você pode ter como alvo outros jogadores – e inicie o projéteis neles!</span><span class="sxs-lookup"><span data-stu-id="fb27d-117">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="fb27d-118">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="fb27d-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fb27d-119">Course</span><span class="sxs-lookup"><span data-stu-id="fb27d-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fb27d-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fb27d-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fb27d-121"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="fb27d-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="fb27d-122">Sr Sharing 240: vários dispositivos HoloLens</span><span class="sxs-lookup"><span data-stu-id="fb27d-122">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="fb27d-123">✔️</span><span class="sxs-lookup"><span data-stu-id="fb27d-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="fb27d-124">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="fb27d-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="fb27d-125">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fb27d-125">Prerequisites</span></span>

* <span data-ttu-id="fb27d-126">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md) com acesso à Internet.</span><span class="sxs-lookup"><span data-stu-id="fb27d-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="fb27d-127">Pelo menos dois dispositivos HoloLens [configurados para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="fb27d-127">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="fb27d-128">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="fb27d-128">Project files</span></span>

* <span data-ttu-id="fb27d-129">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="fb27d-129">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="fb27d-130">Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="fb27d-130">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="fb27d-131">Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="fb27d-131">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="fb27d-132">Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="fb27d-132">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="fb27d-133">Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="fb27d-133">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="fb27d-134">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="fb27d-134">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="fb27d-135">Mantenha o nome da pasta como **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-135">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="fb27d-136">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="fb27d-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="fb27d-137">Capítulo 1 – holo World</span><span class="sxs-lookup"><span data-stu-id="fb27d-137">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="fb27d-138">Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer o processo de compilação e implantação.</span><span class="sxs-lookup"><span data-stu-id="fb27d-138">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="fb27d-139">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fb27d-139">Objectives</span></span>

* <span data-ttu-id="fb27d-140">Configurar o Unity para desenvolver aplicativos Holographic.</span><span class="sxs-lookup"><span data-stu-id="fb27d-140">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="fb27d-141">Veja seu holograma!</span><span class="sxs-lookup"><span data-stu-id="fb27d-141">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="fb27d-142">Instruções</span><span class="sxs-lookup"><span data-stu-id="fb27d-142">Instructions</span></span>

* <span data-ttu-id="fb27d-143">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="fb27d-143">Start Unity.</span></span>
* <span data-ttu-id="fb27d-144">Selecione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-144">Select **Open**.</span></span>
* <span data-ttu-id="fb27d-145">Insira o local como a pasta **SharedHolograms** que você desarquivou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="fb27d-145">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="fb27d-146">Selecione **nome do projeto** e clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-146">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="fb27d-147">Na **hierarquia**, clique com o botão direito do mouse na **câmera principal** e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-147">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="fb27d-148">Na pasta **HoloToolkit-Sharing-240/pré-fabricados/Camera** , localize a **câmera principal** pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="fb27d-148">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="fb27d-149">Arraste e solte a **câmera principal** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-149">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="fb27d-150">Na **hierarquia**, clique em **criar** e em **criar vazio**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-150">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="fb27d-151">Clique com o botão direito do mouse no novo **gameobject** e selecione **renomear**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-151">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="fb27d-152">Renomeie o gameobject para **hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-152">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="fb27d-153">Selecione o objeto **hologramacollection** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-153">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="fb27d-154">No **Inspetor** , defina a **posição de transformação** como: **X: 0, Y:-0,25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-154">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="fb27d-155">Na pasta **hologramas** no **painel Projeto**, localize o ativo **EnergyHub** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-155">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="fb27d-156">Arraste e solte o objeto **EnergyHub** do **painel Projeto** para a **hierarquia** como um **filho de hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-156">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="fb27d-157">Selecione **arquivo > salvar cena como...**</span><span class="sxs-lookup"><span data-stu-id="fb27d-157">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="fb27d-158">Nomeie a cena **SharedHolograms** e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-158">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="fb27d-159">Pressione o botão **reproduzir** no Unity para visualizar os hologramas.</span><span class="sxs-lookup"><span data-stu-id="fb27d-159">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="fb27d-160">Pressione **executar** uma segunda vez para parar o modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="fb27d-160">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="fb27d-161">**Exportar o projeto do Unity para o Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="fb27d-161">**Export the project from Unity to Visual Studio**</span></span>

* <span data-ttu-id="fb27d-162">Em Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-162">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="fb27d-163">Clique em **Adicionar abrir cenas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="fb27d-163">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="fb27d-164">Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-164">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="fb27d-165">Defina o **SDK** como **Universal 10**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-165">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="fb27d-166">Defina **o dispositivo de destino** para o tipo de compilação **HoloLens** e **UWP** como **D3D**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-166">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="fb27d-167">Verifique **os C# projetos do Unity**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-167">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="fb27d-168">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-168">Click **Build**.</span></span>
* <span data-ttu-id="fb27d-169">Na janela Explorador de arquivos que aparece, crie uma **nova pasta** chamada "aplicativo".</span><span class="sxs-lookup"><span data-stu-id="fb27d-169">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="fb27d-170">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-170">Single click the **App** folder.</span></span>
* <span data-ttu-id="fb27d-171">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-171">Press **Select Folder**.</span></span>
* <span data-ttu-id="fb27d-172">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="fb27d-172">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="fb27d-173">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-173">Open the **App** folder.</span></span>
* <span data-ttu-id="fb27d-174">Abra **SharedHolograms. sln** para iniciar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb27d-174">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="fb27d-175">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-175">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="fb27d-176">Clique na seta suspensa ao lado de computador local e selecione **dispositivo remoto**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-176">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="fb27d-177">Defina o **endereço** para o nome ou endereço IP do seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb27d-177">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="fb27d-178">Se você não souber o endereço IP do dispositivo, procure **configurações > rede & Internet > opções avançadas** ou pergunte ao Cortana **"Ei Cortana, qual é meu endereço IP?"**</span><span class="sxs-lookup"><span data-stu-id="fb27d-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="fb27d-179">Deixe o **modo de autenticação** definido como **Universal**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-179">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="fb27d-180">Clique em **selecionar**</span><span class="sxs-lookup"><span data-stu-id="fb27d-180">Click **Select**</span></span>
* <span data-ttu-id="fb27d-181">Clique em **depurar > iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-181">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="fb27d-182">Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="fb27d-182">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
* <span data-ttu-id="fb27d-183">Coloque em seu HoloLens e encontre o holograma EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="fb27d-183">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="fb27d-184">Capítulo 2-interação</span><span class="sxs-lookup"><span data-stu-id="fb27d-184">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="fb27d-185">Neste capítulo, vamos interagir com nossos hologramas.</span><span class="sxs-lookup"><span data-stu-id="fb27d-185">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="fb27d-186">Primeiro, vamos adicionar um cursor para visualizar nosso [olhar](gaze-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="fb27d-186">First, we'll add a cursor to visualize our [Gaze](gaze-and-commit.md).</span></span> <span data-ttu-id="fb27d-187">Em seguida, vamos adicionar [gestos](gaze-and-commit.md#composite-gestures) e usar nossa mão para colocar nossos hologramas em espaço.</span><span class="sxs-lookup"><span data-stu-id="fb27d-187">Then, we'll add [Gestures](gaze-and-commit.md#composite-gestures) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="fb27d-188">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fb27d-188">Objectives</span></span>

* <span data-ttu-id="fb27d-189">Use a entrada olhar para controlar um cursor.</span><span class="sxs-lookup"><span data-stu-id="fb27d-189">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="fb27d-190">Use a entrada de gestos para interagir com os hologramas.</span><span class="sxs-lookup"><span data-stu-id="fb27d-190">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="fb27d-191">Instruções</span><span class="sxs-lookup"><span data-stu-id="fb27d-191">Instructions</span></span>

<span data-ttu-id="fb27d-192">**Foco**</span><span class="sxs-lookup"><span data-stu-id="fb27d-192">**Gaze**</span></span>

* <span data-ttu-id="fb27d-193">No **painel hierarquia** , selecione o objeto **hologramacollection** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-193">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="fb27d-194">No **painel Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-194">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="fb27d-195">No menu, digite na caixa de pesquisa **olhar Manager**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-195">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="fb27d-196">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-196">Select the search result.</span></span>
* <span data-ttu-id="fb27d-197">Na pasta **HoloToolkit-Sharing-240\Prefabs\Input** , localize o ativo de **cursor** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-197">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="fb27d-198">Arraste e solte o ativo do **cursor** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-198">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="fb27d-199">**Gesture**</span><span class="sxs-lookup"><span data-stu-id="fb27d-199">**Gesture**</span></span>

* <span data-ttu-id="fb27d-200">No **painel hierarquia** , selecione o objeto **hologramacollection** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-200">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="fb27d-201">Clique em **Adicionar componente** e digite **Gerenciador de gestos** no campo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-201">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="fb27d-202">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-202">Select the search result.</span></span>
* <span data-ttu-id="fb27d-203">No **painel hierarquia**, expanda **hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-203">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="fb27d-204">Selecione o objeto **EnergyHub** filho.</span><span class="sxs-lookup"><span data-stu-id="fb27d-204">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="fb27d-205">No **painel Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-205">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="fb27d-206">No menu, digite o **posicionamento do holograma**da caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-206">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="fb27d-207">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-207">Select the search result.</span></span>
* <span data-ttu-id="fb27d-208">Salve a cena selecionando **arquivo > salvar cena**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-208">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="fb27d-209">**Implantar e desfrutar**</span><span class="sxs-lookup"><span data-stu-id="fb27d-209">**Deploy and enjoy**</span></span>

* <span data-ttu-id="fb27d-210">Crie e implante em seu HoloLens, usando as instruções do capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="fb27d-210">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="fb27d-211">Depois que o aplicativo for iniciado no seu HoloLens, mova seu rumo e observe como o EnergyHub segue o olhar.</span><span class="sxs-lookup"><span data-stu-id="fb27d-211">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="fb27d-212">Observe como o cursor aparece quando você olhar sobre o holograma e muda para uma luz pontual quando não nuvens em um holograma.</span><span class="sxs-lookup"><span data-stu-id="fb27d-212">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="fb27d-213">Execute um toque de ar para posicionar o holograma.</span><span class="sxs-lookup"><span data-stu-id="fb27d-213">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="fb27d-214">No momento em nosso projeto, você só pode posicionar o holograma uma vez (reimplantar para tentar novamente).</span><span class="sxs-lookup"><span data-stu-id="fb27d-214">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="fb27d-215">Capítulo 3-coordenadas compartilhadas</span><span class="sxs-lookup"><span data-stu-id="fb27d-215">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="fb27d-216">É divertido ver e interagir com os hologramas, mas vamos continuar.</span><span class="sxs-lookup"><span data-stu-id="fb27d-216">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="fb27d-217">Vamos configurar nossa primeira experiência compartilhada-um holograma que todos possam ver em conjunto.</span><span class="sxs-lookup"><span data-stu-id="fb27d-217">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="fb27d-218">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fb27d-218">Objectives</span></span>

* <span data-ttu-id="fb27d-219">Configure uma rede para uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="fb27d-219">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="fb27d-220">Estabeleça um ponto de referência comum.</span><span class="sxs-lookup"><span data-stu-id="fb27d-220">Establish a common reference point.</span></span>
* <span data-ttu-id="fb27d-221">Compartilhe sistemas de coordenadas entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="fb27d-221">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="fb27d-222">Todos veem o mesmo holograma!</span><span class="sxs-lookup"><span data-stu-id="fb27d-222">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="fb27d-223">Os recursos **InternetClientServer** e **PrivateNetworkClientServer** devem ser declarados para que um aplicativo se conecte ao servidor de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="fb27d-223">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="fb27d-224">Isso é feito para você já nos hologramas 240, mas tenha isso em mente para seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="fb27d-224">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>

>1. <span data-ttu-id="fb27d-225">No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="fb27d-225">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="fb27d-226">Clique na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="fb27d-226">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="fb27d-227">Na seção "publicando Configurações > recursos", verifique o recurso **InternetClientServer** e o recurso **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="fb27d-227">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="fb27d-228">Instruções</span><span class="sxs-lookup"><span data-stu-id="fb27d-228">Instructions</span></span>

* <span data-ttu-id="fb27d-229">No **painel Projeto** , navegue até a pasta **HoloToolkit-Sharing-240\Prefabs\Sharing**</span><span class="sxs-lookup"><span data-stu-id="fb27d-229">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="fb27d-230">Arraste e solte o pré-fabricado de **compartilhamento** no **painel hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-230">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="fb27d-231">Em seguida, precisamos iniciar o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="fb27d-231">Next we need to launch the sharing service.</span></span> <span data-ttu-id="fb27d-232">Apenas **um PC** na experiência compartilhada precisa fazer essa etapa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-232">Only **one PC** in the shared experience needs to do this step.</span></span>

* <span data-ttu-id="fb27d-233">No Unity-no menu superior, selecione o **menu HoloToolkit-Sharing-240**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-233">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="fb27d-234">Selecione o item **Iniciar compartilhamento de serviço** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-234">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="fb27d-235">Marque a opção **rede privada** e clique em **permitir acesso** quando o prompt de firewall for exibido.</span><span class="sxs-lookup"><span data-stu-id="fb27d-235">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="fb27d-236">Anote o endereço IPv4 exibido na janela do console do serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="fb27d-236">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="fb27d-237">Esse é o mesmo IP que o computador no qual o serviço está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="fb27d-237">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="fb27d-238">Siga o restante das instruções em **todos os PCs** que ingressarão na experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="fb27d-238">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>

* <span data-ttu-id="fb27d-239">Na **hierarquia**, selecione o objeto de **compartilhamento** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-239">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="fb27d-240">No **Inspetor**, no componente **estágio de compartilhamento** , altere o **endereço do servidor** de ' localhost ' para o endereço IPv4 do computador que executa o SharingService. exe.</span><span class="sxs-lookup"><span data-stu-id="fb27d-240">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="fb27d-241">Na **hierarquia** , selecione o objeto **hologramacollection** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-241">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="fb27d-242">No **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-242">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="fb27d-243">Na caixa de pesquisa, digite **Gerenciador de importação e exportação**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-243">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="fb27d-244">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-244">Select the search result.</span></span>
* <span data-ttu-id="fb27d-245">No **painel Projeto** , navegue até a pasta **scripts** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-245">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="fb27d-246">Clique duas vezes no script **HologramPlacement** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb27d-246">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="fb27d-247">Substitua o conteúdo pelo código abaixo.</span><span class="sxs-lookup"><span data-stu-id="fb27d-247">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="fb27d-248">De volta ao Unity, selecione **hologramacollection** no **painel hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-248">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="fb27d-249">No **painel Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-249">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="fb27d-250">No menu, digite o Gerenciador de estado do **aplicativo**da caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-250">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="fb27d-251">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-251">Select the search result.</span></span>

<span data-ttu-id="fb27d-252">**Implantar e desfrutar**</span><span class="sxs-lookup"><span data-stu-id="fb27d-252">**Deploy and enjoy**</span></span>

* <span data-ttu-id="fb27d-253">Compile o projeto para seus dispositivos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb27d-253">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="fb27d-254">Designe um HoloLens para implantar primeiro.</span><span class="sxs-lookup"><span data-stu-id="fb27d-254">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="fb27d-255">Você precisará aguardar a âncora ser carregada no serviço antes de poder colocar o EnergyHub (isso pode levar aproximadamente 30-60 segundos).</span><span class="sxs-lookup"><span data-stu-id="fb27d-255">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="fb27d-256">Até que o upload seja feito, seus gestos de toque serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="fb27d-256">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="fb27d-257">Depois que o EnergyHub tiver sido colocado, seu local será carregado para o serviço e você poderá implantá-lo em todos os outros dispositivos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb27d-257">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="fb27d-258">Quando um novo HoloLens ingressa primeiro na sessão, o local do EnergyHub pode não estar correto nesse dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fb27d-258">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="fb27d-259">No entanto, assim que os locais de âncora e EnergyHub tiverem sido baixados do serviço, o EnergyHub deverá ir para o local novo e compartilhado.</span><span class="sxs-lookup"><span data-stu-id="fb27d-259">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="fb27d-260">Se isso não acontecer em cerca de 30-60 segundos, passe para o local em que o HoloLens original estava ao definir a âncora para reunir mais pistas de ambiente.</span><span class="sxs-lookup"><span data-stu-id="fb27d-260">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="fb27d-261">Se o local ainda não for bloqueado, reimplante-o no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fb27d-261">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="fb27d-262">Quando os dispositivos estiverem prontos e executando o aplicativo, procure o EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="fb27d-262">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="fb27d-263">Você pode concordar com o local do holograma e em qual direção o texto está voltado?</span><span class="sxs-lookup"><span data-stu-id="fb27d-263">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="fb27d-264">Capítulo 4-descoberta</span><span class="sxs-lookup"><span data-stu-id="fb27d-264">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="fb27d-265">Agora, todos podem ver o mesmo holograma!</span><span class="sxs-lookup"><span data-stu-id="fb27d-265">Everyone can now see the same hologram!</span></span> <span data-ttu-id="fb27d-266">Agora, vamos ver todos os outros conectados ao nosso mundo Holographic compartilhado.</span><span class="sxs-lookup"><span data-stu-id="fb27d-266">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="fb27d-267">Neste capítulo, vamos pegar o local e a rotação do cabeçalho de todos os outros dispositivos HoloLens na mesma sessão de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="fb27d-267">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="fb27d-268">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fb27d-268">Objectives</span></span>

* <span data-ttu-id="fb27d-269">Descubra um ao outro em nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="fb27d-269">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="fb27d-270">Escolha e compartilhe um avatar de jogador.</span><span class="sxs-lookup"><span data-stu-id="fb27d-270">Choose and share a player avatar.</span></span>
* <span data-ttu-id="fb27d-271">Anexe o avatar do jogador ao lado dos cabeçotes de todos.</span><span class="sxs-lookup"><span data-stu-id="fb27d-271">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="fb27d-272">Instruções</span><span class="sxs-lookup"><span data-stu-id="fb27d-272">Instructions</span></span>

* <span data-ttu-id="fb27d-273">No **painel Projeto** , navegue até a pasta **hologramas** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-273">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="fb27d-274">Arraste e solte o **PlayerAvatarStore** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-274">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="fb27d-275">No **painel Projeto** , navegue até a pasta **scripts** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-275">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="fb27d-276">Clique duas vezes no script **AvatarSelector** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb27d-276">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="fb27d-277">Substitua o conteúdo pelo código abaixo.</span><span class="sxs-lookup"><span data-stu-id="fb27d-277">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="fb27d-278">Na **hierarquia** , selecione o objeto **hologramacollection** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-278">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="fb27d-279">No **Inspetor** , clique em **Adicionar componente**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-279">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="fb27d-280">Na caixa de pesquisa, digite **Gerenciador do player local**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-280">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="fb27d-281">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-281">Select the search result.</span></span>
* <span data-ttu-id="fb27d-282">Na **hierarquia** , selecione o objeto **hologramacollection** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-282">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="fb27d-283">No **Inspetor** , clique em **Adicionar componente**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-283">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="fb27d-284">Na caixa de pesquisa, digite **Gerenciador de Player remoto**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-284">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="fb27d-285">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-285">Select the search result.</span></span>
* <span data-ttu-id="fb27d-286">Abra o script **HologramPlacement** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb27d-286">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="fb27d-287">Substitua o conteúdo pelo código abaixo.</span><span class="sxs-lookup"><span data-stu-id="fb27d-287">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="fb27d-288">Abra o script **AppStateManager** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb27d-288">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="fb27d-289">Substitua o conteúdo pelo código abaixo.</span><span class="sxs-lookup"><span data-stu-id="fb27d-289">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="fb27d-290">**Implantar e desfrutar**</span><span class="sxs-lookup"><span data-stu-id="fb27d-290">**Deploy and Enjoy**</span></span>

* <span data-ttu-id="fb27d-291">Crie e implante o projeto em seus dispositivos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb27d-291">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="fb27d-292">Quando você ouvir um som de ping, localize o menu de seleção de avatar e selecione um avatar com o gesto de toque do ar.</span><span class="sxs-lookup"><span data-stu-id="fb27d-292">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="fb27d-293">Se você não estiver olhando para nenhum holograma, o ponto leve em volta do cursor irá transformar uma cor diferente quando o seu HoloLens estiver se comunicando com o serviço: inicializando (roxo escuro), baixando a âncora (verde), importando/exportando dados do local (amarelo), carregando a âncora (azul).</span><span class="sxs-lookup"><span data-stu-id="fb27d-293">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="fb27d-294">Se o seu ponto leve em volta do cursor for a cor padrão (roxo claro), você estará pronto para interagir com outros jogadores em sua sessão!</span><span class="sxs-lookup"><span data-stu-id="fb27d-294">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="fb27d-295">Examine outras pessoas conectadas ao seu espaço – haverá um robô Holographic flutuante acima de seus ressaltos e imitandondo seus movimentos de cabeça!</span><span class="sxs-lookup"><span data-stu-id="fb27d-295">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="fb27d-296">Capítulo 5 – posicionamento</span><span class="sxs-lookup"><span data-stu-id="fb27d-296">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="fb27d-297">Neste capítulo, vamos tornar a âncora capaz de ser colocada em superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="fb27d-297">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="fb27d-298">Usaremos coordenadas compartilhadas para colocar essa âncora no ponto central entre todos conectados à experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="fb27d-298">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="fb27d-299">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fb27d-299">Objectives</span></span>

* <span data-ttu-id="fb27d-300">Coloque os hologramas na malha de mapeamento espacial com base na posição de cabeçalho dos jogadores.</span><span class="sxs-lookup"><span data-stu-id="fb27d-300">Place holograms on the spatial mapping mesh based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="fb27d-301">Instruções</span><span class="sxs-lookup"><span data-stu-id="fb27d-301">Instructions</span></span>

* <span data-ttu-id="fb27d-302">No **painel Projeto** , navegue até a pasta **hologramas** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-302">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="fb27d-303">Arraste e solte o **CustomSpatialMapping** pré-fabricado na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-303">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="fb27d-304">No **painel Projeto** , navegue até a pasta **scripts** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-304">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="fb27d-305">Clique duas vezes no script **AppStateManager** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb27d-305">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="fb27d-306">Substitua o conteúdo pelo código abaixo.</span><span class="sxs-lookup"><span data-stu-id="fb27d-306">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="fb27d-307">No **painel Projeto** , navegue até a pasta **scripts** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-307">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="fb27d-308">Clique duas vezes no script **HologramPlacement** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb27d-308">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="fb27d-309">Substitua o conteúdo pelo código abaixo.</span><span class="sxs-lookup"><span data-stu-id="fb27d-309">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="fb27d-310">**Implantar e desfrutar**</span><span class="sxs-lookup"><span data-stu-id="fb27d-310">**Deploy and enjoy**</span></span>

* <span data-ttu-id="fb27d-311">Crie e implante o projeto em seus dispositivos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb27d-311">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="fb27d-312">Quando o aplicativo estiver pronto, aguarde um círculo e observe como o EnergyHub aparece no centro de todos.</span><span class="sxs-lookup"><span data-stu-id="fb27d-312">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="fb27d-313">Toque para posicionar o EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="fb27d-313">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="fb27d-314">Experimente o comando de voz "redefinir destino" para escolher o EnergyHub de backup e trabalhar juntos como um grupo para mover o holograma para um novo local.</span><span class="sxs-lookup"><span data-stu-id="fb27d-314">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="fb27d-315">Capítulo 6-física do mundo real</span><span class="sxs-lookup"><span data-stu-id="fb27d-315">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="fb27d-316">Neste capítulo, adicionaremos hologramas que separam superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="fb27d-316">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="fb27d-317">Assista ao seu espaço preencha com projetos iniciados por você e seus amigos!</span><span class="sxs-lookup"><span data-stu-id="fb27d-317">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="fb27d-318">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fb27d-318">Objectives</span></span>

* <span data-ttu-id="fb27d-319">Inicie o projéteis que salta as superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="fb27d-319">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="fb27d-320">Compartilhe o projéteis para que outros jogadores possam vê-los.</span><span class="sxs-lookup"><span data-stu-id="fb27d-320">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="fb27d-321">Instruções</span><span class="sxs-lookup"><span data-stu-id="fb27d-321">Instructions</span></span>

* <span data-ttu-id="fb27d-322">Na **hierarquia** , selecione o objeto **hologramacollection** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-322">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="fb27d-323">No **Inspetor** , clique em **Adicionar componente**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-323">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="fb27d-324">Na caixa de pesquisa, digite **Projectile Launcher**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-324">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="fb27d-325">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-325">Select the search result.</span></span>

<span data-ttu-id="fb27d-326">**Implantar e desfrutar**</span><span class="sxs-lookup"><span data-stu-id="fb27d-326">**Deploy and enjoy**</span></span>

* <span data-ttu-id="fb27d-327">Crie e implante em seus dispositivos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb27d-327">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="fb27d-328">Quando o aplicativo estiver em execução em todos os dispositivos, execute um toque de ar para iniciar o Projectile em superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="fb27d-328">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="fb27d-329">Veja o que acontece quando seu Projectile colide com o Avatar de outro jogador!</span><span class="sxs-lookup"><span data-stu-id="fb27d-329">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="fb27d-330">Capítulo 7 – final geral</span><span class="sxs-lookup"><span data-stu-id="fb27d-330">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="fb27d-331">Neste capítulo, vamos descobrir um portal que só pode ser descoberto com a colaboração.</span><span class="sxs-lookup"><span data-stu-id="fb27d-331">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="fb27d-332">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fb27d-332">Objectives</span></span>

* <span data-ttu-id="fb27d-333">Trabalhe em conjunto para iniciar o projéteis suficiente na âncora para descobrir um portal secreto!</span><span class="sxs-lookup"><span data-stu-id="fb27d-333">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="fb27d-334">Instruções</span><span class="sxs-lookup"><span data-stu-id="fb27d-334">Instructions</span></span>

* <span data-ttu-id="fb27d-335">No **painel Projeto** , navegue até a pasta **hologramas** .</span><span class="sxs-lookup"><span data-stu-id="fb27d-335">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="fb27d-336">Arraste e solte o ativo **Underworld** como um **filho de hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-336">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="fb27d-337">Com o **hologramacollection** selecionado, clique no botão **Adicionar componente** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-337">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="fb27d-338">No menu, digite na caixa de pesquisa **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-338">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="fb27d-339">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb27d-339">Select the search result.</span></span>
* <span data-ttu-id="fb27d-340">Com o **hologramacollection** selecionado, na **hierarquia** , arraste o objeto **EnergyHub** para o campo de **destino** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-340">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="fb27d-341">Com o **hologramacollection** selecionado, na **hierarquia** , arraste o objeto **Underworld** para o campo **Underworld** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="fb27d-341">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="fb27d-342">**Implantar e desfrutar**</span><span class="sxs-lookup"><span data-stu-id="fb27d-342">**Deploy and enjoy**</span></span>

* <span data-ttu-id="fb27d-343">Crie e implante em seus dispositivos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fb27d-343">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="fb27d-344">Quando o aplicativo for iniciado, colabore em conjunto para iniciar o projéteis no EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="fb27d-344">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="fb27d-345">Quando o Underworld for exibido, inicie projéteis em Underworld robots (pressione um robô três vezes para diversão extra).</span><span class="sxs-lookup"><span data-stu-id="fb27d-345">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>

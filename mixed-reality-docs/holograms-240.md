---
title: MR compartilhamento 240 - vários dispositivos do HoloLens
description: Siga este passo a passo usando o Unity, o Visual Studio e o HoloLens para saber os detalhes de compartilhamento hologramas de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, compartilhamento, rede, academy, tutorial
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589850"
---
>[!NOTE]
><span data-ttu-id="345fe-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="345fe-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="345fe-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="345fe-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="345fe-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="345fe-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="345fe-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="345fe-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="345fe-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="345fe-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="345fe-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="345fe-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="345fe-110">MR Sharing 240: Vários dispositivos do HoloLens</span><span class="sxs-lookup"><span data-stu-id="345fe-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="345fe-111">Hologramas recebem presença em nosso mundo por restantes em vigor à medida que avançarmos no espaço.</span><span class="sxs-lookup"><span data-stu-id="345fe-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="345fe-112">HoloLens mantém hologramas no lugar usando vários [sistemas de coordenadas](coordinate-systems.md) para controlar o local e a orientação de objetos.</span><span class="sxs-lookup"><span data-stu-id="345fe-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="345fe-113">Quando podemos compartilhar esses sistemas de coordenadas entre dispositivos, podemos criar uma experiência compartilhada que permite fazer parte de um mundo holográfico compartilhado.</span><span class="sxs-lookup"><span data-stu-id="345fe-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="345fe-114">Neste tutorial, nós iremos:</span><span class="sxs-lookup"><span data-stu-id="345fe-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="345fe-115">Configure uma rede para uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="345fe-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="345fe-116">Compartilhar hologramas em todos os dispositivos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="345fe-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="345fe-117">Descubra outras pessoas em nosso mundo holográfica compartilhado.</span><span class="sxs-lookup"><span data-stu-id="345fe-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="345fe-118">Crie uma experiência interativa compartilhada onde você pode direcionar o outros jogadores - e iniciar os projéteis-los!</span><span class="sxs-lookup"><span data-stu-id="345fe-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="345fe-119">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="345fe-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="345fe-120">Curso</span><span class="sxs-lookup"><span data-stu-id="345fe-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="345fe-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="345fe-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="345fe-122"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="345fe-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="345fe-123">MR Sharing 240: Vários dispositivos do HoloLens</span><span class="sxs-lookup"><span data-stu-id="345fe-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="345fe-124">✔️</span><span class="sxs-lookup"><span data-stu-id="345fe-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="345fe-125">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="345fe-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="345fe-126">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="345fe-126">Prerequisites</span></span>

* <span data-ttu-id="345fe-127">Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md) com acesso à Internet.</span><span class="sxs-lookup"><span data-stu-id="345fe-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="345fe-128">Pelo menos dois dispositivos HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="345fe-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="345fe-129">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="345fe-129">Project files</span></span>

* <span data-ttu-id="345fe-130">Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="345fe-131">Requer o Unity 2017.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="345fe-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="345fe-132">Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="345fe-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="345fe-133">Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="345fe-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="345fe-134">Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="345fe-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="345fe-135">Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.</span><span class="sxs-lookup"><span data-stu-id="345fe-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="345fe-136">Mantenha o nome da pasta como **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="345fe-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="345fe-137">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="345fe-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="345fe-138">Capítulo 1 - Holo World</span><span class="sxs-lookup"><span data-stu-id="345fe-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="345fe-139">Neste capítulo, vamos configurar nosso primeiro projeto do Unity e percorrer a compilação e o processo de implantação.</span><span class="sxs-lookup"><span data-stu-id="345fe-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="345fe-140">Objetivos</span><span class="sxs-lookup"><span data-stu-id="345fe-140">Objectives</span></span>

* <span data-ttu-id="345fe-141">A instalação do Unity para desenvolver aplicativos holographic.</span><span class="sxs-lookup"><span data-stu-id="345fe-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="345fe-142">Consulte seu holograma!</span><span class="sxs-lookup"><span data-stu-id="345fe-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="345fe-143">Instruções</span><span class="sxs-lookup"><span data-stu-id="345fe-143">Instructions</span></span>

* <span data-ttu-id="345fe-144">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="345fe-144">Start Unity.</span></span>
* <span data-ttu-id="345fe-145">Selecione **aberto**.</span><span class="sxs-lookup"><span data-stu-id="345fe-145">Select **Open**.</span></span>
* <span data-ttu-id="345fe-146">Insira o local como o **SharedHolograms** pasta você anteriormente não arquivados.</span><span class="sxs-lookup"><span data-stu-id="345fe-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="345fe-147">Selecione **nome do projeto** e clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="345fe-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="345fe-148">No **hierarquia**, clique com botão direito do **câmera principal** e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="345fe-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="345fe-149">No **HoloToolkit-Sharing-240/pré-fabricados/câmera** pasta, localize a **câmera principal** pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="345fe-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="345fe-150">Arraste e solte os **câmera principal** para o **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="345fe-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="345fe-151">No **hierarquia**, clique em **Create** e **criar vazio**.</span><span class="sxs-lookup"><span data-stu-id="345fe-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="345fe-152">Clique com botão direito a nova **GameObject** e selecione **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="345fe-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="345fe-153">Renomeie o GameObject para **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="345fe-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="345fe-154">Selecione o **HologramCollection** do objeto na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="345fe-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="345fe-155">No **Inspetor** definir o **transformar posição** para: **X: 0, Y: -0,25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="345fe-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="345fe-156">No **hologramas** pasta no **painel projeto**, localize o **EnergyHub** ativo.</span><span class="sxs-lookup"><span data-stu-id="345fe-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="345fe-157">Arraste e solte a **EnergyHub** do objeto da **painel projeto** para o **hierarquia** como um **filho de HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="345fe-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="345fe-158">Selecione **arquivo > Salvar cena como...**</span><span class="sxs-lookup"><span data-stu-id="345fe-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="345fe-159">Nomeie a cena **SharedHolograms** e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="345fe-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="345fe-160">Pressione a **reproduzir** botão no Unity para visualizar seu hologramas.</span><span class="sxs-lookup"><span data-stu-id="345fe-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="345fe-161">Pressione **reproduzir** uma segunda vez para parar o modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="345fe-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="345fe-162">**Exportar o projeto do Unity para Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="345fe-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="345fe-163">No, selecione Unity **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="345fe-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="345fe-164">Clique em **cenas abra Adicionar** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="345fe-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="345fe-165">Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="345fe-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="345fe-166">Definir **SDK** à **10 Universal**.</span><span class="sxs-lookup"><span data-stu-id="345fe-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="345fe-167">Definir **dispositivo de destino** à **HoloLens** e **tipo de compilação de UWP** para **D3D**.</span><span class="sxs-lookup"><span data-stu-id="345fe-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="345fe-168">Verifique **Unity C# projetos**.</span><span class="sxs-lookup"><span data-stu-id="345fe-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="345fe-169">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="345fe-169">Click **Build**.</span></span>
* <span data-ttu-id="345fe-170">Na janela do Gerenciador de arquivo aparece, crie uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="345fe-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="345fe-171">Único clique a **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="345fe-172">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="345fe-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="345fe-173">Quando Unity é feito, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="345fe-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="345fe-174">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-174">Open the **App** folder.</span></span>
* <span data-ttu-id="345fe-175">Abra **SharedHolograms.sln** para iniciar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="345fe-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="345fe-176">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **X86**.</span><span class="sxs-lookup"><span data-stu-id="345fe-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="345fe-177">Clique na seta suspensa ao lado do computador Local e selecione **dispositivo remoto**.</span><span class="sxs-lookup"><span data-stu-id="345fe-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="345fe-178">Defina as **endereço** no nome ou endereço IP do seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="345fe-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="345fe-179">Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas** ou perguntar ao Cortana **"Ei Cortana, o que é meu endereço IP?"**</span><span class="sxs-lookup"><span data-stu-id="345fe-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="345fe-180">Deixe o **modo de autenticação** definido como **Universal**.</span><span class="sxs-lookup"><span data-stu-id="345fe-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="345fe-181">Clique em **selecionar**</span><span class="sxs-lookup"><span data-stu-id="345fe-181">Click **Select**</span></span>
* <span data-ttu-id="345fe-182">Clique em **Depurar > Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="345fe-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="345fe-183">Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="345fe-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="345fe-184">Coloque o HoloLens e localizar o holograma EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="345fe-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="345fe-185">Capítulo 2 - interação</span><span class="sxs-lookup"><span data-stu-id="345fe-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="345fe-186">Neste capítulo, vai interagimos com nossos hologramas.</span><span class="sxs-lookup"><span data-stu-id="345fe-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="345fe-187">Primeiro, vamos adicionar um cursor para visualizar nossos [olhares](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="345fe-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="345fe-188">Em seguida, adicionaremos [gestos](gestures.md) e use nossos mãos para colocar nosso hologramas no espaço.</span><span class="sxs-lookup"><span data-stu-id="345fe-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="345fe-189">Objetivos</span><span class="sxs-lookup"><span data-stu-id="345fe-189">Objectives</span></span>

* <span data-ttu-id="345fe-190">Use a olhar para controlar um cursor de entrada.</span><span class="sxs-lookup"><span data-stu-id="345fe-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="345fe-191">Use o gesto de entrada para interagir com hologramas.</span><span class="sxs-lookup"><span data-stu-id="345fe-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="345fe-192">Instruções</span><span class="sxs-lookup"><span data-stu-id="345fe-192">Instructions</span></span>

<span data-ttu-id="345fe-193">**Gaze**</span><span class="sxs-lookup"><span data-stu-id="345fe-193">**Gaze**</span></span>
* <span data-ttu-id="345fe-194">No **painel de hierarquia** selecionar a **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="345fe-195">No **painel Inspetor** clique a **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="345fe-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="345fe-196">No menu, digite na caixa de pesquisa **olhares Manager**.</span><span class="sxs-lookup"><span data-stu-id="345fe-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="345fe-197">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-197">Select the search result.</span></span>
* <span data-ttu-id="345fe-198">No **240\Prefabs\Input compartilhamento HoloToolkit** pasta, localize a **Cursor** ativo.</span><span class="sxs-lookup"><span data-stu-id="345fe-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="345fe-199">Arraste e solte os **Cursor** ativo para o **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="345fe-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="345fe-200">**Gesto**</span><span class="sxs-lookup"><span data-stu-id="345fe-200">**Gesture**</span></span>
* <span data-ttu-id="345fe-201">No **painel de hierarquia** selecionar a **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="345fe-202">Clique em **Add Component** e digite **gesto Manager** no campo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="345fe-203">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-203">Select the search result.</span></span>
* <span data-ttu-id="345fe-204">No **painel de hierarquia**, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="345fe-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="345fe-205">Selecione o filho **EnergyHub** objeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="345fe-206">No **painel Inspetor** clique a **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="345fe-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="345fe-207">No menu, digite na caixa de pesquisa **holograma posicionamento**.</span><span class="sxs-lookup"><span data-stu-id="345fe-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="345fe-208">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-208">Select the search result.</span></span>
* <span data-ttu-id="345fe-209">Salve a cena selecionando **arquivo > Salvar cena**.</span><span class="sxs-lookup"><span data-stu-id="345fe-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="345fe-210">**Implantar e aproveitar**</span><span class="sxs-lookup"><span data-stu-id="345fe-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="345fe-211">Criar e implantar para o HoloLens, usando as instruções do capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="345fe-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="345fe-212">Depois que o aplicativo for iniciado no seu HoloLens, mover sua cabeça e observe como o EnergyHub segue seu foco.</span><span class="sxs-lookup"><span data-stu-id="345fe-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="345fe-213">Observe como o cursor exibido quando você contempla após o holograma e muda para um ponto de luz quando não Observação em um holograma.</span><span class="sxs-lookup"><span data-stu-id="345fe-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="345fe-214">Execute um polegar para colocar o holograma.</span><span class="sxs-lookup"><span data-stu-id="345fe-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="345fe-215">No momento em nosso projeto, você só pode colocar uma vez o holograma (reimplantação para tentar novamente).</span><span class="sxs-lookup"><span data-stu-id="345fe-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="345fe-216">Coordenadas de capítulo 3 - compartilhado</span><span class="sxs-lookup"><span data-stu-id="345fe-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="345fe-217">É divertido ver e interagir com hologramas, mas vamos aprofundar.</span><span class="sxs-lookup"><span data-stu-id="345fe-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="345fe-218">Vamos definir nossa primeira experiência compartilhada - um holograma todos podem ver juntos.</span><span class="sxs-lookup"><span data-stu-id="345fe-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="345fe-219">Objetivos</span><span class="sxs-lookup"><span data-stu-id="345fe-219">Objectives</span></span>

* <span data-ttu-id="345fe-220">Configure uma rede para uma experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="345fe-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="345fe-221">Estabelecer um ponto de referência comum.</span><span class="sxs-lookup"><span data-stu-id="345fe-221">Establish a common reference point.</span></span>
* <span data-ttu-id="345fe-222">Compartilhe os sistemas de coordenadas em todos os dispositivos.</span><span class="sxs-lookup"><span data-stu-id="345fe-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="345fe-223">Todos veem o mesmo holograma!</span><span class="sxs-lookup"><span data-stu-id="345fe-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="345fe-224">O **InternetClientServer** e **PrivateNetworkClientServer** recursos devem ser declarados para um aplicativo para se conectar ao servidor de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="345fe-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="345fe-225">Isso é feito para que você já no hologramas 240, mas lembre-se para seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="345fe-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="345fe-226">No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"</span><span class="sxs-lookup"><span data-stu-id="345fe-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="345fe-227">Clique na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="345fe-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="345fe-228">Na seção "> recursos de publicação configurações", verifique as **InternetClientServer** capacidade e o **PrivateNetworkClientServer** capacidade</span><span class="sxs-lookup"><span data-stu-id="345fe-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="345fe-229">Instruções</span><span class="sxs-lookup"><span data-stu-id="345fe-229">Instructions</span></span>

* <span data-ttu-id="345fe-230">No **painel projeto** navegue até a **240\Prefabs\Sharing compartilhamento HoloToolkit** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="345fe-231">Arraste e solte a **compartilhamento** pré-fabricado para o **painel de hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="345fe-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="345fe-232">Em seguida, precisamos iniciar o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="345fe-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="345fe-233">Somente **um único PC** compartilhado experiência precisa realizar esta etapa.</span><span class="sxs-lookup"><span data-stu-id="345fe-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="345fe-234">No Unity - no menu superior - selecione a **240 compartilhamento HoloToolkit menu**.</span><span class="sxs-lookup"><span data-stu-id="345fe-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="345fe-235">Selecione o **inicie o serviço de compartilhamento** item na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="345fe-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="345fe-236">Verifique as **rede privada** opção e clique em **permitir o acesso** quando aparece o prompt do firewall.</span><span class="sxs-lookup"><span data-stu-id="345fe-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="345fe-237">Anote o endereço IPv4 exibido na janela do console de serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="345fe-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="345fe-238">Isso é o mesmo IP da máquina que o serviço está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="345fe-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="345fe-239">Siga o restante das instruções em **todos os PCs** que ingressará experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="345fe-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="345fe-240">No **hierarquia**, selecione o **Sharing** objeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="345fe-241">No **Inspetor**, no **estágio de compartilhamento** componente, altere a **endereço do servidor** do 'localhost' para o endereço IPv4 do computador que executa o SharingService.exe.</span><span class="sxs-lookup"><span data-stu-id="345fe-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="345fe-242">No **hierarquia** selecionar a **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="345fe-243">No **Inspector** clique a **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="345fe-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="345fe-244">Na caixa de pesquisa, digite **importação exportação âncora Manager**.</span><span class="sxs-lookup"><span data-stu-id="345fe-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="345fe-245">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-245">Select the search result.</span></span>
* <span data-ttu-id="345fe-246">No **painel projeto** navegue até a **Scripts** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="345fe-247">Clique duas vezes o **HologramPlacement** script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="345fe-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="345fe-248">Substitua o conteúdo pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="345fe-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="345fe-249">No Unity, selecione a **HologramCollection** na **painel de hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="345fe-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="345fe-250">No **painel Inspetor** clique a **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="345fe-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="345fe-251">No menu, digite na caixa de pesquisa **Gerenciador de estado do aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="345fe-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="345fe-252">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-252">Select the search result.</span></span>

<span data-ttu-id="345fe-253">**Implantar e aproveitar**</span><span class="sxs-lookup"><span data-stu-id="345fe-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="345fe-254">Compile o projeto para seus dispositivos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="345fe-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="345fe-255">Designe um HoloLens implantar primeiro.</span><span class="sxs-lookup"><span data-stu-id="345fe-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="345fe-256">Você precisará aguardar a âncora ser carregado para o serviço antes de colocar o EnergyHub (Isso pode levar cerca de 30 a 60 segundos).</span><span class="sxs-lookup"><span data-stu-id="345fe-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="345fe-257">Até que o carregamento for concluído, seu gestos de toque serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="345fe-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="345fe-258">Depois que o EnergyHub foi colocado, sua localização será carregada para o serviço e, em seguida, você pode implantar para todos os outros dispositivos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="345fe-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="345fe-259">Quando um novo HoloLens primeiro ingressar na sessão, o local do EnergyHub pode não estar correto no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="345fe-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="345fe-260">No entanto, assim que a âncora e os locais de EnergyHub tiverem sido baixados do serviço, o EnergyHub deve ir para o novo local compartilhado.</span><span class="sxs-lookup"><span data-stu-id="345fe-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="345fe-261">Se isso não acontece em cerca de 30 a 60 segundos, percorrer para onde o HoloLens original estava ao configurar a âncora para reunir mais dicas de ambiente.</span><span class="sxs-lookup"><span data-stu-id="345fe-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="345fe-262">Se o local ainda não bloqueia, reimplantar no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="345fe-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="345fe-263">Quando os dispositivos estão todos prontos e executando o aplicativo, procure o EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="345fe-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="345fe-264">Todos concordam na localização do holograma e a direção na qual o texto está enfrentando?</span><span class="sxs-lookup"><span data-stu-id="345fe-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="345fe-265">Capítulo 4 - descoberta</span><span class="sxs-lookup"><span data-stu-id="345fe-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="345fe-266">Agora, todos podem ver o holograma mesmo!</span><span class="sxs-lookup"><span data-stu-id="345fe-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="345fe-267">Agora vamos ver todos else conectados a nosso mundo holográfico compartilhado.</span><span class="sxs-lookup"><span data-stu-id="345fe-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="345fe-268">Neste capítulo, podemos irá obter o local principal e a rotação de todos os outros dispositivos do HoloLens na mesma sessão de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="345fe-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="345fe-269">Objetivos</span><span class="sxs-lookup"><span data-stu-id="345fe-269">Objectives</span></span>

* <span data-ttu-id="345fe-270">Descobrir uns aos outros em nossa experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="345fe-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="345fe-271">Escolha e compartilhar um avatar player.</span><span class="sxs-lookup"><span data-stu-id="345fe-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="345fe-272">Anexe o avatar do player ao lado de cabeça de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="345fe-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="345fe-273">Instruções</span><span class="sxs-lookup"><span data-stu-id="345fe-273">Instructions</span></span>

* <span data-ttu-id="345fe-274">No **painel projeto** navegue até a **hologramas** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="345fe-275">Arraste e solte os **PlayerAvatarStore** para o **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="345fe-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="345fe-276">No **painel projeto** navegue até a **Scripts** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="345fe-277">Clique duas vezes o **AvatarSelector** script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="345fe-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="345fe-278">Substitua o conteúdo pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="345fe-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="345fe-279">No **hierarquia** selecionar a **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="345fe-280">No **Inspector** clique em **adicionar componente**.</span><span class="sxs-lookup"><span data-stu-id="345fe-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="345fe-281">Na caixa de pesquisa, digite **Gerenciador de Player Local**.</span><span class="sxs-lookup"><span data-stu-id="345fe-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="345fe-282">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-282">Select the search result.</span></span>
* <span data-ttu-id="345fe-283">No **hierarquia** selecionar a **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="345fe-284">No **Inspector** clique em **adicionar componente**.</span><span class="sxs-lookup"><span data-stu-id="345fe-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="345fe-285">Na caixa de pesquisa, digite **Gerenciador de Player remota**.</span><span class="sxs-lookup"><span data-stu-id="345fe-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="345fe-286">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-286">Select the search result.</span></span>
* <span data-ttu-id="345fe-287">Abra o **HologramPlacement** script no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="345fe-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="345fe-288">Substitua o conteúdo pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="345fe-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="345fe-289">Abra o **AppStateManager** script no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="345fe-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="345fe-290">Substitua o conteúdo pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="345fe-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="345fe-291">**Implantar e aproveitar**</span><span class="sxs-lookup"><span data-stu-id="345fe-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="345fe-292">Criar e implantar o projeto para seus dispositivos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="345fe-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="345fe-293">Quando você ouve um som de ping, localize o menu de seleção de avatar e selecione um avatar com o gesto de toque de ar.</span><span class="sxs-lookup"><span data-stu-id="345fe-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="345fe-294">Se você não estiver olhando qualquer hologramas, o ponto de luz em torno de seu cursor ativará uma cor diferente quando o HoloLens está se comunicando com o serviço: inicializando (roxo escuro), baixar a âncora (verde), importar/exportar dados de localização (amarelo) Carregando a âncora (azul).</span><span class="sxs-lookup"><span data-stu-id="345fe-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="345fe-295">Se o ponto de luz em torno de seu cursor é a cor padrão (roxo-claro), em seguida, você está pronto para interagir com outros jogadores na sua sessão!</span><span class="sxs-lookup"><span data-stu-id="345fe-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="345fe-296">Examinar a outras pessoas conectado ao seu espaço - não haverá um robô holográfico flutuante acima seu shoulder e imitando seus movimentos de cabeçalho!</span><span class="sxs-lookup"><span data-stu-id="345fe-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="345fe-297">Capítulo 5 - posicionamento</span><span class="sxs-lookup"><span data-stu-id="345fe-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="345fe-298">Neste capítulo, faremos a âncora podem ser posicionados em superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="345fe-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="345fe-299">Vamos usar coordenadas compartilhadas para colocar essa âncora no ponto médio entre todos conectados a experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="345fe-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="345fe-300">Objetivos</span><span class="sxs-lookup"><span data-stu-id="345fe-300">Objectives</span></span>

* <span data-ttu-id="345fe-301">Coloque hologramas no mapa espacial com base na posição de cabeçalho dos jogadores.</span><span class="sxs-lookup"><span data-stu-id="345fe-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="345fe-302">Instruções</span><span class="sxs-lookup"><span data-stu-id="345fe-302">Instructions</span></span>

* <span data-ttu-id="345fe-303">No **painel projeto** navegue até a **hologramas** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="345fe-304">Arraste e solte os **CustomSpatialMapping** pré-fabricado até a **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="345fe-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="345fe-305">No **painel projeto** navegue até a **Scripts** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="345fe-306">Clique duas vezes o **AppStateManager** script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="345fe-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="345fe-307">Substitua o conteúdo pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="345fe-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="345fe-308">No **painel projeto** navegue até a **Scripts** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="345fe-309">Clique duas vezes o **HologramPlacement** script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="345fe-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="345fe-310">Substitua o conteúdo pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="345fe-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="345fe-311">**Implantar e aproveitar**</span><span class="sxs-lookup"><span data-stu-id="345fe-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="345fe-312">Criar e implantar o projeto para seus dispositivos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="345fe-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="345fe-313">Quando o aplicativo estiver pronto, coloque em funcionamento em um círculo e observe como o EnergyHub aparece no Centro de todas as pessoas.</span><span class="sxs-lookup"><span data-stu-id="345fe-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="345fe-314">Toque para colocar o EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="345fe-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="345fe-315">Tente o comando de voz 'Redefinir Target' para pegar o EnergyHub e trabalham juntos como um grupo para mover o holograma para um novo local.</span><span class="sxs-lookup"><span data-stu-id="345fe-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="345fe-316">Capítulos 6 - física do mundo Real</span><span class="sxs-lookup"><span data-stu-id="345fe-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="345fe-317">Neste capítulo vamos adicionar hologramas salte nas superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="345fe-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="345fe-318">Assista ao seu espaço preenchido com projetos iniciados por você e seus amigos!</span><span class="sxs-lookup"><span data-stu-id="345fe-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="345fe-319">Objetivos</span><span class="sxs-lookup"><span data-stu-id="345fe-319">Objectives</span></span>

* <span data-ttu-id="345fe-320">Inicie os projéteis salte nas superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="345fe-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="345fe-321">Compartilhe os projéteis para que outros jogadores podem vê-los.</span><span class="sxs-lookup"><span data-stu-id="345fe-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="345fe-322">Instruções</span><span class="sxs-lookup"><span data-stu-id="345fe-322">Instructions</span></span>

* <span data-ttu-id="345fe-323">No **hierarquia** selecionar a **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="345fe-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="345fe-324">No **Inspector** clique em **adicionar componente**.</span><span class="sxs-lookup"><span data-stu-id="345fe-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="345fe-325">Na caixa de pesquisa, digite **Projectile iniciador**.</span><span class="sxs-lookup"><span data-stu-id="345fe-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="345fe-326">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-326">Select the search result.</span></span>

<span data-ttu-id="345fe-327">**Implantar e aproveitar**</span><span class="sxs-lookup"><span data-stu-id="345fe-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="345fe-328">Compilar e implantar em seus dispositivos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="345fe-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="345fe-329">Quando o aplicativo está em execução em todos os dispositivos, execute um polegar para iniciar projectile em superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="345fe-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="345fe-330">Veja o que acontece quando sua projectile entra em conflito com o avatar do outro jogador!</span><span class="sxs-lookup"><span data-stu-id="345fe-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="345fe-331">Capítulo 7 - Grand finale:</span><span class="sxs-lookup"><span data-stu-id="345fe-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="345fe-332">Neste capítulo, vamos vai descobrir um portal que só pode ser descoberto com a colaboração.</span><span class="sxs-lookup"><span data-stu-id="345fe-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="345fe-333">Objetivos</span><span class="sxs-lookup"><span data-stu-id="345fe-333">Objectives</span></span>

* <span data-ttu-id="345fe-334">Trabalham juntos para iniciar o suficiente projéteis à âncora para revelar um portal secreto!</span><span class="sxs-lookup"><span data-stu-id="345fe-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="345fe-335">Instruções</span><span class="sxs-lookup"><span data-stu-id="345fe-335">Instructions</span></span>

* <span data-ttu-id="345fe-336">No **painel projeto** navegue até a **hologramas** pasta.</span><span class="sxs-lookup"><span data-stu-id="345fe-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="345fe-337">Arraste e solte os **mundo virtual** ativo como um **filho de HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="345fe-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="345fe-338">Com **HologramCollection** selecionado, clique no **Add Component** botão no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="345fe-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="345fe-339">No menu, digite na caixa de pesquisa **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="345fe-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="345fe-340">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="345fe-340">Select the search result.</span></span>
* <span data-ttu-id="345fe-341">Com **HologramCollection** selecionado, da **hierarquia** arrastar a **EnergyHub** do objeto para o **destino** campo o **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="345fe-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="345fe-342">Com **HologramCollection** selecionado, da **hierarquia** arrastar a **mundo virtual** do objeto para o **mundo virtual** campo o  **Inspetor de**.</span><span class="sxs-lookup"><span data-stu-id="345fe-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="345fe-343">**Implantar e aproveitar**</span><span class="sxs-lookup"><span data-stu-id="345fe-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="345fe-344">Compilar e implantar em seus dispositivos do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="345fe-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="345fe-345">Quando o aplicativo for iniciado, colaborem para iniciar os projéteis no EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="345fe-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="345fe-346">Quando aparece o mundo virtual, inicie projéteis nas robôs de mundo virtual (acerto de um robô três vezes por diversão extra).</span><span class="sxs-lookup"><span data-stu-id="345fe-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>

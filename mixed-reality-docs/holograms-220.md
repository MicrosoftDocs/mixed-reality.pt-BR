---
title: MR espacial 220-som espacial
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de som espaciais.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, som espacial
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526903"
---
>[!NOTE]
><span data-ttu-id="ae89b-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="ae89b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ae89b-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ae89b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ae89b-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ae89b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ae89b-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="ae89b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ae89b-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ae89b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ae89b-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="ae89b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="ae89b-110">MR espacial 220: Som espacial</span><span class="sxs-lookup"><span data-stu-id="ae89b-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="ae89b-111">O [som espacial](spatial-sound.md) traz a vida para os hologramas e dá a eles presença em nosso mundo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="ae89b-112">Os hologramas são compostos por luz e som e, se você perder a visão de seus hologramas, o som espacial poderá ajudá-lo a encontrá-los.</span><span class="sxs-lookup"><span data-stu-id="ae89b-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="ae89b-113">O som espacial não é como o som típico que você ouviria no rádio, é um som posicionado no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="ae89b-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="ae89b-114">Com o som espacial, você pode fazer com que os hologramas pareçam estar por trás de você, ao lado de você ou mesmo à sua cabeça!</span><span class="sxs-lookup"><span data-stu-id="ae89b-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="ae89b-115">Neste curso, você vai:</span><span class="sxs-lookup"><span data-stu-id="ae89b-115">In this course, you will:</span></span>

* <span data-ttu-id="ae89b-116">Configure seu ambiente de desenvolvimento para usar o som espacial da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ae89b-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="ae89b-117">Use o som espacial para aprimorar as interações.</span><span class="sxs-lookup"><span data-stu-id="ae89b-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="ae89b-118">Use o som espacial em conjunto com o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="ae89b-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="ae89b-119">Entenda as práticas recomendadas de design e mistura de som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="ae89b-120">Use o som para aprimorar os efeitos especiais e trazer o usuário para o mundo da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="ae89b-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="ae89b-121">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="ae89b-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ae89b-122">Course</span><span class="sxs-lookup"><span data-stu-id="ae89b-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ae89b-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ae89b-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ae89b-124"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="ae89b-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="ae89b-125">MR espacial 220: Som espacial</span><span class="sxs-lookup"><span data-stu-id="ae89b-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="ae89b-126">✔️</span><span class="sxs-lookup"><span data-stu-id="ae89b-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ae89b-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ae89b-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="ae89b-128">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="ae89b-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ae89b-129">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ae89b-129">Prerequisites</span></span>

* <span data-ttu-id="ae89b-130">Um PC com Windows 10 configurado com as [ferramentas](install-the-tools.md)corretas instaladas.</span><span class="sxs-lookup"><span data-stu-id="ae89b-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="ae89b-131">Alguma capacidade C# básica de programação.</span><span class="sxs-lookup"><span data-stu-id="ae89b-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="ae89b-132">Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="ae89b-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="ae89b-133">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="ae89b-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="ae89b-134">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="ae89b-134">Project files</span></span>

* <span data-ttu-id="ae89b-135">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="ae89b-136"> Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ae89b-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="ae89b-137">Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="ae89b-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="ae89b-138">Esta versão pode não estar mais atualizada.</span><span class="sxs-lookup"><span data-stu-id="ae89b-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="ae89b-139">Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="ae89b-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="ae89b-140"> Esta versão pode não estar mais atualizada.</span><span class="sxs-lookup"><span data-stu-id="ae89b-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="ae89b-141">Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="ae89b-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="ae89b-142"> Esta versão pode não estar mais atualizada.</span><span class="sxs-lookup"><span data-stu-id="ae89b-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="ae89b-143">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="ae89b-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="ae89b-144">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="ae89b-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="ae89b-145">Errata e observações</span><span class="sxs-lookup"><span data-stu-id="ae89b-145">Errata and Notes</span></span>

* <span data-ttu-id="ae89b-146">"Habilitar Apenas Meu Código" precisa ser desabilitado (desmarcado) no Visual Studio em ferramentas-> opções-> depuração para acessar os pontos de interrupção no código.</span><span class="sxs-lookup"><span data-stu-id="ae89b-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="ae89b-147">Capítulo 1 – configuração do Unity</span><span class="sxs-lookup"><span data-stu-id="ae89b-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="ae89b-148">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ae89b-148">Objectives</span></span>

* <span data-ttu-id="ae89b-149">Altere a configuração de som do Unity para usar o som espacial da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ae89b-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="ae89b-150">Adicionar som 3D a um objeto no Unity.</span><span class="sxs-lookup"><span data-stu-id="ae89b-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="ae89b-151">Instruções</span><span class="sxs-lookup"><span data-stu-id="ae89b-151">Instructions</span></span>

* <span data-ttu-id="ae89b-152">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="ae89b-152">Start Unity.</span></span>
* <span data-ttu-id="ae89b-153">Selecione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-153">Select **Open**.</span></span>
* <span data-ttu-id="ae89b-154">Navegue até sua área de trabalho e localize a pasta que você cancelou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ae89b-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="ae89b-155">Clique na pasta **Starting\Decibel** e pressione o botão **Selecionar pasta** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="ae89b-156">Aguarde até que o projeto seja carregado no Unity.</span><span class="sxs-lookup"><span data-stu-id="ae89b-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="ae89b-157">No painel **projeto** , abra **Scenes\Decibel.Unity**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="ae89b-158">No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="ae89b-159">No Inspetor, expanda o **áudio** e observe que não há nenhuma caixa de seleção **espacial** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="ae89b-160">Por padrão, o Unity não carrega um plug-in spatializer.</span><span class="sxs-lookup"><span data-stu-id="ae89b-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="ae89b-161">As etapas a seguir habilitarão o som espacial no projeto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="ae89b-162">No menu superior do Unity, vá para **editar > configurações do projeto > áudio**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="ae89b-163">Localize a lista suspensa **plug-in do Spatializer** e selecione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="ae89b-164">No painel **hierarquia** , selecione **hologramacollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="ae89b-165">No painel **Inspetor** , localize o componente **fonte de áudio** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="ae89b-166">Marque a  caixa de seleção espacialize.</span><span class="sxs-lookup"><span data-stu-id="ae89b-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="ae89b-167">Arraste o controle deslizante de **mistura espacial** para **3D**ou digite **1** na caixa de edição.</span><span class="sxs-lookup"><span data-stu-id="ae89b-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="ae89b-168">Agora, criaremos o projeto no Unity e configuraremos a solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae89b-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="ae89b-169">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="ae89b-170">Clique em **Adicionar abrir cenas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="ae89b-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="ae89b-171">Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="ae89b-172">Se você estiver desenvolvendo especificamente para o HoloLens, defina o **dispositivo de destino** para o **hololens**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="ae89b-173">Caso contrário, deixe em **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="ae89b-174">Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="ae89b-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="ae89b-175">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-175">Click **Build**.</span></span>
7. <span data-ttu-id="ae89b-176">Crie uma **nova pasta** chamada "app".</span><span class="sxs-lookup"><span data-stu-id="ae89b-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="ae89b-177">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="ae89b-178">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-178">Press **Select Folder**.</span></span>

<span data-ttu-id="ae89b-179">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="ae89b-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="ae89b-180">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="ae89b-181">Abra a **solução de Decibéi Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="ae89b-182">Se estiver implantando no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="ae89b-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="ae89b-183">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="ae89b-184">Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="ae89b-185">Insira **o endereço IP do dispositivo de HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="ae89b-186">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-186">Click **Select**.</span></span> <span data-ttu-id="ae89b-187">Se você não souber o endereço IP do dispositivo, examine **configurações > rede & Internet > opções avançadas**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="ae89b-188">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="ae89b-189">Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="ae89b-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="ae89b-190">Se estiver implantando em um headset de imersão:</span><span class="sxs-lookup"><span data-stu-id="ae89b-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="ae89b-191">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="ae89b-192">Verifique se o destino de implantação está definido como **computador local**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="ae89b-193">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="ae89b-194">Capítulo 2-som espacial e interação</span><span class="sxs-lookup"><span data-stu-id="ae89b-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="ae89b-195">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ae89b-195">Objectives</span></span>

* <span data-ttu-id="ae89b-196">Aprimore o holograma de uso de um som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="ae89b-197">Direcionar o olhar do usuário usando o som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="ae89b-198">Forneça comentários sobre gestos usando som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="ae89b-199">Parte 1-aprimorando o realm</span><span class="sxs-lookup"><span data-stu-id="ae89b-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="ae89b-200">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="ae89b-200">Key Concepts</span></span>

* <span data-ttu-id="ae89b-201">Esespaciair sons de holograma.</span><span class="sxs-lookup"><span data-stu-id="ae89b-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="ae89b-202">As fontes de som devem ser colocadas em um local apropriado no holograma.</span><span class="sxs-lookup"><span data-stu-id="ae89b-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="ae89b-203">O local apropriado para o som vai depender do holograma.</span><span class="sxs-lookup"><span data-stu-id="ae89b-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="ae89b-204">Por exemplo, se o holograma for de um humano, a origem do som deverá ser localizada perto da boca e não dos pés.</span><span class="sxs-lookup"><span data-stu-id="ae89b-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="ae89b-205">Instruções</span><span class="sxs-lookup"><span data-stu-id="ae89b-205">Instructions</span></span>

<span data-ttu-id="ae89b-206">As instruções a seguir anexarão um som espacial a um holograma.</span><span class="sxs-lookup"><span data-stu-id="ae89b-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="ae89b-207">No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="ae89b-208">No painel **Inspetor** , na mensagem de **áudio**, clique no círculo ao lado de **AudioClip** e selecione  polifocalizar no pop-up.</span><span class="sxs-lookup"><span data-stu-id="ae89b-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="ae89b-209">Clique no círculo ao lado de **saída** e selecione **SoundEffects** no pop-up.</span><span class="sxs-lookup"><span data-stu-id="ae89b-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="ae89b-210">O projeto Decibéi usa um componente **AudioMixer** do Unity para habilitar o ajuste dos níveis de som para grupos de sons.</span><span class="sxs-lookup"><span data-stu-id="ae89b-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="ae89b-211">Ao agrupar sons dessa forma, o volume geral pode ser ajustado mantendo o volume relativo de cada som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="ae89b-212">Em **áudio**, expanda **configurações de som 3D**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="ae89b-213">Defina o **nível de Doppler** como **0**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="ae89b-214">Definir o nível de Doppler como zero desabilita as alterações em pitch causadas pelo Motion (do holograma ou do usuário).</span><span class="sxs-lookup"><span data-stu-id="ae89b-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="ae89b-215">Um exemplo clássico de Doppler é um carro com movimentação rápida.</span><span class="sxs-lookup"><span data-stu-id="ae89b-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="ae89b-216">À medida que o carro se aproxima de um ouvinte estacionário, a inclinação do motor aumenta.</span><span class="sxs-lookup"><span data-stu-id="ae89b-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="ae89b-217">Quando ele passa o ouvinte, a densidade diminui com distância.</span><span class="sxs-lookup"><span data-stu-id="ae89b-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="ae89b-218">Parte 2-direcionando o olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="ae89b-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="ae89b-219">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="ae89b-219">Key Concepts</span></span>

* <span data-ttu-id="ae89b-220">Use o som para chamar a atenção para hologramas importantes.</span><span class="sxs-lookup"><span data-stu-id="ae89b-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="ae89b-221">Os ouvidos ajudam a direcionar onde devem ser os olhos.</span><span class="sxs-lookup"><span data-stu-id="ae89b-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="ae89b-222">O cérebro tem algumas expectativas aprendidas.</span><span class="sxs-lookup"><span data-stu-id="ae89b-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="ae89b-223">Um exemplo de expectativas aprendidas é que os pássaros geralmente estão acima da cabeça dos seres humanos.</span><span class="sxs-lookup"><span data-stu-id="ae89b-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="ae89b-224">Se um usuário ouve um som de pássaro, sua reação inicial é Pesquisar.</span><span class="sxs-lookup"><span data-stu-id="ae89b-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="ae89b-225">Colocar um pássaro abaixo do usuário pode levar a eles voltados para a direção correta do som, mas não consegue encontrar o holograma com base na expectativa de precisar pesquisar.</span><span class="sxs-lookup"><span data-stu-id="ae89b-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="ae89b-226">Instruções</span><span class="sxs-lookup"><span data-stu-id="ae89b-226">Instructions</span></span>

<span data-ttu-id="ae89b-227">As instruções a seguir permitem que P0LY sejam ocultadas para trás, para que você possa usar o som para localizar o holograma.</span><span class="sxs-lookup"><span data-stu-id="ae89b-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="ae89b-228">No painel **hierarquia** , selecione **gerentes**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="ae89b-229">No painel **Inspetor** , encontre o **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="ae89b-230">Em **manipulador de entrada de fala**, expanda **ir ocultar**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="ae89b-231">Altere **nenhuma função** para **GoHide**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Chaves Ir para ocultar](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="ae89b-233">Parte 3-comentários do gesto</span><span class="sxs-lookup"><span data-stu-id="ae89b-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="ae89b-234">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="ae89b-234">Key Concepts</span></span>

* <span data-ttu-id="ae89b-235">Fornecer ao usuário uma confirmação de gesto positivo usando som</span><span class="sxs-lookup"><span data-stu-id="ae89b-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="ae89b-236">Não sobrecarregar os sons do usuário em alta</span><span class="sxs-lookup"><span data-stu-id="ae89b-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="ae89b-237">Os sons sutis funcionam melhor – não obscurecem a experiência</span><span class="sxs-lookup"><span data-stu-id="ae89b-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="ae89b-238">Instruções</span><span class="sxs-lookup"><span data-stu-id="ae89b-238">Instructions</span></span>

* <span data-ttu-id="ae89b-239">No painel **hierarquia** , expanda **hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="ae89b-240">Expanda **EnergyHub** e selecione **base**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="ae89b-241">No painel **Inspetor** , clique em **Adicionar componente** e adicionar **manipulador de som de gesto**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="ae89b-242">Em **manipulador de som de gesto**, clique no círculo próximo ao **clipe de navegação** e ao clipe de navegação **atualizado** e selecione **RotateClick** do pop-up para ambos.</span><span class="sxs-lookup"><span data-stu-id="ae89b-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="ae89b-243">Clique duas vezes em "GestureSoundHandler" para carregar no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae89b-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="ae89b-244">O manipulador de som de gesto executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ae89b-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="ae89b-245">Criar e configurar um **áudio**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="ae89b-246">Coloque a **audioname** no local do gameobject apropriado .</span><span class="sxs-lookup"><span data-stu-id="ae89b-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="ae89b-247">Reproduz o **AudioClip** associado ao gesto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="ae89b-248">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="ae89b-248">Build and Deploy</span></span>

1. <span data-ttu-id="ae89b-249">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="ae89b-250">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-250">Click **Build**.</span></span>
3. <span data-ttu-id="ae89b-251">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="ae89b-252">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-252">Press **Select Folder**.</span></span>

<span data-ttu-id="ae89b-253">Verifique se a barra de ferramentas diz "versão", "x86" ou "x64" e "dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="ae89b-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="ae89b-254">Caso contrário, essa é a instância de codificação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae89b-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="ae89b-255">Talvez seja necessário reabrir a solução na pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="ae89b-256">Se solicitado, recarregue os arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="ae89b-257">Como antes, implante a partir do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae89b-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="ae89b-258">Após a implantação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ae89b-258">After the application is deployed:</span></span>

* <span data-ttu-id="ae89b-259">Observe como o som muda à medida que você se move ao P0LY.</span><span class="sxs-lookup"><span data-stu-id="ae89b-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="ae89b-260">Digamos que *"Vá ocultar"* para fazer com que o P0LY se mova para um local por trás de você.</span><span class="sxs-lookup"><span data-stu-id="ae89b-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="ae89b-261">Encontre-o pelo som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-261">Find it by the sound.</span></span>
* <span data-ttu-id="ae89b-262">Olhar na base do hub de energia.</span><span class="sxs-lookup"><span data-stu-id="ae89b-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="ae89b-263">Toque e arraste para a esquerda ou direita para girar o holograma e observe como o clique do som confirma o gesto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="ae89b-264">Observação: Há um painel de texto que será rotulado com você.</span><span class="sxs-lookup"><span data-stu-id="ae89b-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="ae89b-265">Isso conterá os comandos de voz disponíveis que você pode usar ao longo deste curso.</span><span class="sxs-lookup"><span data-stu-id="ae89b-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="ae89b-266">Capítulo 3-som espacial e mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="ae89b-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="ae89b-267">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ae89b-267">Objectives</span></span>

* <span data-ttu-id="ae89b-268">Confirme a interação entre os hologramas e o mundo real usando som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="ae89b-269">Occlude sons usando o mundo físico.</span><span class="sxs-lookup"><span data-stu-id="ae89b-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="ae89b-270">Parte 1-interação física do mundo</span><span class="sxs-lookup"><span data-stu-id="ae89b-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="ae89b-271">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="ae89b-271">Key Concepts</span></span>

* <span data-ttu-id="ae89b-272">Os objetos físicos geralmente fazem um som ao encontrar uma superfície ou outro objeto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="ae89b-273">Os sons devem ser apropriados para o contexto na experiência.</span><span class="sxs-lookup"><span data-stu-id="ae89b-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="ae89b-274">Por exemplo, definir uma xícara em uma tabela deve fazer um som mais silencioso do que descartar um Boulder em uma parte do metal.</span><span class="sxs-lookup"><span data-stu-id="ae89b-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="ae89b-275">Instruções</span><span class="sxs-lookup"><span data-stu-id="ae89b-275">Instructions</span></span>

* <span data-ttu-id="ae89b-276">No painel **hierarquia** , expanda **hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="ae89b-277">Expanda **EnergyHub**, selecione **base**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="ae89b-278">No painel **Inspetor** , clique em **Adicionar componente** e adicione **tocar para inserir com som e ação**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="ae89b-279">Em **toque para posicionar com som e ação**:</span><span class="sxs-lookup"><span data-stu-id="ae89b-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="ae89b-280">Verifique o **pai ao tocar**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="ae89b-281">Defina **som de posicionamento** como **local**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="ae89b-282">Defina **som de retirada** para **retirada**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="ae89b-283">Pressione a + no canto inferior direito em ambos **na ação de retirada** e **na ação de posicionamento**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="ae89b-284">Arraste EnergyHub da cena para os campos **nenhum (objeto)** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="ae89b-285">Em **ação de retirada**, clique em **sem função** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="ae89b-286">Em **ação de posicionamento**, clique em **sem função** -> **EnergyHubBase** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Toque para posicionar com som e ação](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="ae89b-288">Parte 2-som oclusão</span><span class="sxs-lookup"><span data-stu-id="ae89b-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="ae89b-289">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="ae89b-289">Key Concepts</span></span>

* <span data-ttu-id="ae89b-290">Som, como claro, pode ser obstruído.</span><span class="sxs-lookup"><span data-stu-id="ae89b-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="ae89b-291">Um exemplo clássico é uma sala de concerto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-291">A classic example is a concert hall.</span></span> <span data-ttu-id="ae89b-292">Quando um ouvinte está fora do Hall e a porta é fechada, a música parece muffled.</span><span class="sxs-lookup"><span data-stu-id="ae89b-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="ae89b-293">Normalmente, também há uma redução no volume.</span><span class="sxs-lookup"><span data-stu-id="ae89b-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="ae89b-294">Quando a porta é aberta, o espectro completo do som é ouvido no volume real.</span><span class="sxs-lookup"><span data-stu-id="ae89b-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="ae89b-295">Sons de alta frequência geralmente são absorvidos mais do que frequências baixas.</span><span class="sxs-lookup"><span data-stu-id="ae89b-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="ae89b-296">Instruções</span><span class="sxs-lookup"><span data-stu-id="ae89b-296">Instructions</span></span>

* <span data-ttu-id="ae89b-297">No painel **hierarquia** , expanda **hologramacollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="ae89b-298">No painel **Inspetor** , clique em **Adicionar componente** e adicionar **emissor de áudio**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="ae89b-299">A classe emissor de áudio fornece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="ae89b-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="ae89b-300">Restaura todas as alterações no volume de Audioname.</span><span class="sxs-lookup"><span data-stu-id="ae89b-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="ae89b-301">Executa uma **física. RaycastNonAlloc** da posição do usuário na direção do gameobject ao  qual o **AudioEmitter** está anexado.</span><span class="sxs-lookup"><span data-stu-id="ae89b-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="ae89b-302">O método RaycastNonAlloc é usado como uma otimização de desempenho para limitar as alocações, bem como o número de resultados retornados.</span><span class="sxs-lookup"><span data-stu-id="ae89b-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="ae89b-303">Para cada **IAudioInfluencer** encontrado, chama o método **ApplyEffect** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="ae89b-304">Para cada **IAudioInfluencer** anterior que não é mais encontrado, chame o método **RemoveEffect** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="ae89b-305">Observe que as atualizações do AudioEmitter em escalas de tempo humano, em oposição a por quadro.</span><span class="sxs-lookup"><span data-stu-id="ae89b-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="ae89b-306">Isso é feito porque as pessoas geralmente não se movem com rapidez suficiente para que o efeito precise ser atualizado com mais frequência do que cada trimestre ou metade de um segundo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="ae89b-307">Os hologramas que teleport rapidamente de um local para outro podem quebrar a ilusão.</span><span class="sxs-lookup"><span data-stu-id="ae89b-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="ae89b-308">No painel **hierarquia** , expanda **hologramacollection**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="ae89b-309">Expanda **EnergyHub** e selecione **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="ae89b-310">No painel **Inspetor** , clique em **Adicionar componente** e adicione **áudio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="ae89b-311">Em **áudio Occluder**, defina a **frequência de corte** como **1500**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="ae89b-312">Essa configuração limita as frequências de áudio para 1500 Hz e abaixo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="ae89b-313">Defina **passagem de volume** para **0,9**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="ae89b-314">Essa configuração reduz o volume do áudio para 90% do seu nível atual.</span><span class="sxs-lookup"><span data-stu-id="ae89b-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="ae89b-315">O áudio Occluder implementa IAudioInfluencer para:</span><span class="sxs-lookup"><span data-stu-id="ae89b-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="ae89b-316">Aplique um efeito de oclusão usando um **AudioLowPassFilter** que é anexado ao **áudio** , gerenciado, comprar o **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="ae89b-317">Aplica a atenuação de volume à Audioname.</span><span class="sxs-lookup"><span data-stu-id="ae89b-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="ae89b-318">Desabilita o efeito definindo uma frequência de corte neutra e desabilitando o filtro.</span><span class="sxs-lookup"><span data-stu-id="ae89b-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="ae89b-319">A frequência usada como neutra é 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="ae89b-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="ae89b-320">Essa frequência foi escolhida porque está acima da frequência máxima nominal que pode ser ouvida pelo Ear humano, isso não faz nenhum impacto discernido no som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="ae89b-321">No painel **hierarquia** , selecione **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="ae89b-322">No painel **Inspetor** , clique em **Adicionar componente** e adicione **áudio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="ae89b-323">Em **áudio Occluder**, defina a **frequência de corte** como **750**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="ae89b-324">Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a frequência mais baixa é aplicada ao filtro.</span><span class="sxs-lookup"><span data-stu-id="ae89b-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="ae89b-325">Defina **passagem de volume** para **0,75**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="ae89b-326">Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a passagem do volume é aplicada de aditivo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="ae89b-327">No painel **hierarquia** , selecione **gerentes**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="ae89b-328">No painel **Inspetor** , expanda **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="ae89b-329">Em **manipulador de entrada de fala**, expanda ir para o **encargo**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="ae89b-330">Altere **nenhuma função** para **GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Chaves Custo](images/gocharge.png)

* <span data-ttu-id="ae89b-332">Expanda **aqui**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="ae89b-333">Altere **nenhuma função** para **ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Chaves Vem cá](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="ae89b-335">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="ae89b-335">Build and Deploy</span></span>

* <span data-ttu-id="ae89b-336">Como antes, compile o projeto no Unity e implante-o no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae89b-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="ae89b-337">Após a implantação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ae89b-337">After the application is deployed:</span></span>

* <span data-ttu-id="ae89b-338">Digamos que "faça o *encargo"* para que o P0LY Insira o Hub de energia.</span><span class="sxs-lookup"><span data-stu-id="ae89b-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="ae89b-339">Observe a alteração no som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-339">Note the change in the sound.</span></span> <span data-ttu-id="ae89b-340">Ele deve parecer muffled e um pouco mais silencioso.</span><span class="sxs-lookup"><span data-stu-id="ae89b-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="ae89b-341">Se você for capaz de se posicionar com uma parede ou outro objeto entre você e o Hub de energia, você deve notar um Muffling adicional do som devido à oclusão pelo mundo real.</span><span class="sxs-lookup"><span data-stu-id="ae89b-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="ae89b-342">Diga *"Venha aqui"* para que P0LY deixe o Hub de energia e se posicione na frente de você.</span><span class="sxs-lookup"><span data-stu-id="ae89b-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="ae89b-343">Observe que o som oclusão é removido quando o P0LY sai do hub de energia.</span><span class="sxs-lookup"><span data-stu-id="ae89b-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="ae89b-344">Se você ainda estiver ouvindo oclusão, P0LY poderá ser obstruído pelo mundo real.</span><span class="sxs-lookup"><span data-stu-id="ae89b-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="ae89b-345">Tente mudar para garantir que você tenha uma clara linha de visão para P0LY.</span><span class="sxs-lookup"><span data-stu-id="ae89b-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="ae89b-346">Parte 3-modelos de sala</span><span class="sxs-lookup"><span data-stu-id="ae89b-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="ae89b-347">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="ae89b-347">Key Concepts</span></span>

* <span data-ttu-id="ae89b-348">O tamanho do espaço fornece filas subliminal que contribuem para a localização de som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="ae89b-349">Os modelos de sala são definidos por**áudio**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="ae89b-350">O [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece código para definir o modelo de sala.</span><span class="sxs-lookup"><span data-stu-id="ae89b-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="ae89b-351">Para experiências de realidade misturada, selecione o modelo de sala que melhor se adapta ao espaço do mundo real.</span><span class="sxs-lookup"><span data-stu-id="ae89b-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="ae89b-352">Se você estiver criando um cenário de realidade virtual, selecione o modelo de sala que melhor se adapta ao ambiente virtual.</span><span class="sxs-lookup"><span data-stu-id="ae89b-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="ae89b-353">Capítulo 4-design de som</span><span class="sxs-lookup"><span data-stu-id="ae89b-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="ae89b-354">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ae89b-354">Objectives</span></span>

* <span data-ttu-id="ae89b-355">Entenda as considerações sobre o design de som efetivo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="ae89b-356">Aprenda técnicas e diretrizes de combinação.</span><span class="sxs-lookup"><span data-stu-id="ae89b-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="ae89b-357">Parte 1-design de som e experiência</span><span class="sxs-lookup"><span data-stu-id="ae89b-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="ae89b-358">Esta seção aborda as principais considerações e diretrizes de design de som e experiência.</span><span class="sxs-lookup"><span data-stu-id="ae89b-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="ae89b-359">Normalizar todos os sons</span><span class="sxs-lookup"><span data-stu-id="ae89b-359">Normalize all sounds</span></span>

<span data-ttu-id="ae89b-360">Isso evita a necessidade de código de caso especial para ajustar os níveis de volume por som, o que pode ser demorado e limita a capacidade de atualizar facilmente os arquivos de som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="ae89b-361">Design de uma experiência não de compartilhamento de Internet</span><span class="sxs-lookup"><span data-stu-id="ae89b-361">Design for an untethered experience</span></span>

<span data-ttu-id="ae89b-362">O HoloLens é um computador Holographic totalmente contido e desvinculado.</span><span class="sxs-lookup"><span data-stu-id="ae89b-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="ae89b-363">Os usuários podem e usarão suas experiências ao se moverem.</span><span class="sxs-lookup"><span data-stu-id="ae89b-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="ae89b-364">Certifique-se de testar sua mixagem de áudio ao percorrer.</span><span class="sxs-lookup"><span data-stu-id="ae89b-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="ae89b-365">Emitir som de locais lógicos em seus hologramas</span><span class="sxs-lookup"><span data-stu-id="ae89b-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="ae89b-366">No mundo real, um cachorro não latido de sua parte final e a voz de um humano não vem de seus pés.</span><span class="sxs-lookup"><span data-stu-id="ae89b-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="ae89b-367">Evite emitir seus sons de partes inesperadas de seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="ae89b-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="ae89b-368">Para hologramas pequenos, é razoável ter uma emissão sonora do centro da geometria.</span><span class="sxs-lookup"><span data-stu-id="ae89b-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="ae89b-369">Os sons conhecidos são mais localizáveis</span><span class="sxs-lookup"><span data-stu-id="ae89b-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="ae89b-370">A voz humana e a música são muito fáceis de localizar.</span><span class="sxs-lookup"><span data-stu-id="ae89b-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="ae89b-371">Se alguém chamar seu nome, você poderá determinar com precisão a direção de que a voz veio e de quanto longe.</span><span class="sxs-lookup"><span data-stu-id="ae89b-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="ae89b-372">Sons curtos e desconhecidos são mais difíceis de localizar.</span><span class="sxs-lookup"><span data-stu-id="ae89b-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="ae89b-373">Cognizant as expectativas dos usuários</span><span class="sxs-lookup"><span data-stu-id="ae89b-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="ae89b-374">A experiência de vida exerce uma parte em nossa capacidade de identificar o local de um som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="ae89b-375">Esse é um dos motivos pelos quais a voz humana é particularmente fácil de localizar.</span><span class="sxs-lookup"><span data-stu-id="ae89b-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="ae89b-376">É importante estar atento às expectativas aprendidas do usuário ao colocar seus sons.</span><span class="sxs-lookup"><span data-stu-id="ae89b-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="ae89b-377">Por exemplo, quando alguém ouve uma música de pássaro, ele geralmente procura, pois os pássaros tendem a estar acima da linha de visão (voador ou em uma árvore).</span><span class="sxs-lookup"><span data-stu-id="ae89b-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="ae89b-378">Não é incomum um usuário ativar a direção correta de um som, mas examinar a direção vertical incorreta e ficar confuso ou frustrado quando não conseguir encontrar o holograma.</span><span class="sxs-lookup"><span data-stu-id="ae89b-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="ae89b-379">Evitar emissores ocultos</span><span class="sxs-lookup"><span data-stu-id="ae89b-379">Avoid hidden emitters</span></span>

<span data-ttu-id="ae89b-380">No mundo real, se ouvimos um som, geralmente podemos identificar o objeto que está emitindo o som.</span><span class="sxs-lookup"><span data-stu-id="ae89b-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="ae89b-381">Isso também deve se manter verdadeiro em suas experiências.</span><span class="sxs-lookup"><span data-stu-id="ae89b-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="ae89b-382">Pode ser muito desconcerto para os usuários ouvirem um som, saber de onde o som se origina e não conseguir ver um objeto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="ae89b-383">Há algumas exceções a essa diretriz.</span><span class="sxs-lookup"><span data-stu-id="ae89b-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="ae89b-384">Por exemplo, sons de ambiente como Crickets em um campo não precisam estar visíveis.</span><span class="sxs-lookup"><span data-stu-id="ae89b-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="ae89b-385">A experiência de vida nos dá familiaridade com a origem desses sons sem a necessidade de vê-los.</span><span class="sxs-lookup"><span data-stu-id="ae89b-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="ae89b-386">Parte 2-mixagem de som</span><span class="sxs-lookup"><span data-stu-id="ae89b-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="ae89b-387">Direcione sua combinação para o volume de 70% no HoloLens</span><span class="sxs-lookup"><span data-stu-id="ae89b-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="ae89b-388">As experiências de realidade misturada permitem que os hologramas sejam vistos no mundo real.</span><span class="sxs-lookup"><span data-stu-id="ae89b-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="ae89b-389">Eles também devem permitir que sons do mundo real sejam ouvidos.</span><span class="sxs-lookup"><span data-stu-id="ae89b-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="ae89b-390">Um destino de volume de 70% permite que o usuário Ouça o mundo junto com o som de sua experiência.</span><span class="sxs-lookup"><span data-stu-id="ae89b-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="ae89b-391">O HoloLens em 100% volume deve se afogar em sons externos</span><span class="sxs-lookup"><span data-stu-id="ae89b-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="ae89b-392">Um nível de volume de 100% é semelhante a uma experiência de realidade virtual.</span><span class="sxs-lookup"><span data-stu-id="ae89b-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="ae89b-393">Visualmente, o usuário é transportado para um mundo diferente.</span><span class="sxs-lookup"><span data-stu-id="ae89b-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="ae89b-394">O mesmo deve conter verdadeiro forma audível.</span><span class="sxs-lookup"><span data-stu-id="ae89b-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="ae89b-395">Usar o AudioMixer do Unity para ajustar as categorias de sons</span><span class="sxs-lookup"><span data-stu-id="ae89b-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="ae89b-396">Ao projetar sua combinação, geralmente é útil criar categorias de som e ter a capacidade de aumentar ou diminuir seu volume como uma unidade.</span><span class="sxs-lookup"><span data-stu-id="ae89b-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="ae89b-397">Isso retém os níveis relativos de cada som, ao mesmo tempo em que permite alterações rápidas e fáceis na combinação geral.</span><span class="sxs-lookup"><span data-stu-id="ae89b-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="ae89b-398">As categorias comuns incluem; efeitos de som, Ambience, voz e música em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="ae89b-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="ae89b-399">Misturar sons com base no olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="ae89b-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="ae89b-400">Muitas vezes, pode ser útil alterar a mistura de som em sua experiência com base em onde um usuário está olhando (ou não).</span><span class="sxs-lookup"><span data-stu-id="ae89b-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="ae89b-401">Um uso comum para essa técnica é reduzir o nível de volume para hologramas que estão fora do quadro Holographic para tornar mais fácil para o usuário se concentrar nas informações em frente deles.</span><span class="sxs-lookup"><span data-stu-id="ae89b-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="ae89b-402">Outro uso é aumentar o volume de um som para chamar a atenção do usuário para um evento importante.</span><span class="sxs-lookup"><span data-stu-id="ae89b-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="ae89b-403">Criando sua combinação</span><span class="sxs-lookup"><span data-stu-id="ae89b-403">Building your mix</span></span>

<span data-ttu-id="ae89b-404">Ao criar sua combinação, é recomendável começar com o áudio de segundo plano da sua experiência e adicionar camadas com base na importância.</span><span class="sxs-lookup"><span data-stu-id="ae89b-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="ae89b-405">Geralmente, isso resulta em cada camada sendo mais alta do que a anterior.</span><span class="sxs-lookup"><span data-stu-id="ae89b-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="ae89b-406">Ao imaginar sua mistura como um funil invertido, com o menos importante (e geralmente sons mais silenciosos) na parte inferior, é recomendável estruturar sua mistura semelhante ao diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="ae89b-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Estrutura da combinação de som](images/soundlevels.png)

<span data-ttu-id="ae89b-408">A voz é um cenário interessante.</span><span class="sxs-lookup"><span data-stu-id="ae89b-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="ae89b-409">Com base na experiência que você está criando, talvez você queira ter um som estéreo (não localizado) ou para espacialar sua voz.</span><span class="sxs-lookup"><span data-stu-id="ae89b-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="ae89b-410">Duas experiências publicadas da Microsoft ilustram excelentes exemplos de cada cenário.</span><span class="sxs-lookup"><span data-stu-id="ae89b-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="ae89b-411">O [HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa uma voz estéreo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="ae89b-412">Quando o narrador está descrevendo o local que está sendo exibido, o som é consistente e não varia de acordo com a posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="ae89b-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="ae89b-413">Isso permite que o narrador descreva a cena sem sair dos sons espaciais do ambiente.</span><span class="sxs-lookup"><span data-stu-id="ae89b-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="ae89b-414">Os [fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizam uma voz espacialada na forma de uma detecção.</span><span class="sxs-lookup"><span data-stu-id="ae89b-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="ae89b-415">A voz da detecção é usada para ajudar a levar a atenção do usuário a uma pista importante como se um humano real estivesse na sala.</span><span class="sxs-lookup"><span data-stu-id="ae89b-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="ae89b-416">Isso permite um sentido ainda maior de imersão na experiência de resolver o mistério.</span><span class="sxs-lookup"><span data-stu-id="ae89b-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="ae89b-417">Parte 3-desempenho</span><span class="sxs-lookup"><span data-stu-id="ae89b-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="ae89b-418">Uso da CPU</span><span class="sxs-lookup"><span data-stu-id="ae89b-418">CPU usage</span></span>

<span data-ttu-id="ae89b-419">Ao usar o som espacial, 10-12 emissores consumirão aproximadamente 12% da CPU.</span><span class="sxs-lookup"><span data-stu-id="ae89b-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="ae89b-420">Transmitir arquivos de áudio longos</span><span class="sxs-lookup"><span data-stu-id="ae89b-420">Stream long audio files</span></span>

<span data-ttu-id="ae89b-421">Os dados de áudio podem ser grandes, especialmente em taxas de exemplo comuns (44,1 e 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="ae89b-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="ae89b-422">Uma regra geral é que os arquivos de áudio com mais de 5-10 segundos devem ser transmitidos para reduzir o uso de memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="ae89b-423">No Unity, você pode marcar um arquivo de áudio para streaming nas configurações de importação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ae89b-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Configurações de importação de áudio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="ae89b-425">Capítulo 5-efeitos especiais</span><span class="sxs-lookup"><span data-stu-id="ae89b-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="ae89b-426">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ae89b-426">Objectives</span></span>

* <span data-ttu-id="ae89b-427">Adicione profundidade a "janelas mágicas".</span><span class="sxs-lookup"><span data-stu-id="ae89b-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="ae89b-428">Traga o usuário para o mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="ae89b-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="ae89b-429">Janelas mágicas</span><span class="sxs-lookup"><span data-stu-id="ae89b-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="ae89b-430">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="ae89b-430">Key Concepts</span></span>

* <span data-ttu-id="ae89b-431">Criar exibições em um mundo oculto é visualmente atraente.</span><span class="sxs-lookup"><span data-stu-id="ae89b-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="ae89b-432">Aprimore o realm adicionando efeitos de áudio quando um holograma ou o usuário estiver perto do mundo oculto.</span><span class="sxs-lookup"><span data-stu-id="ae89b-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="ae89b-433">Instruções</span><span class="sxs-lookup"><span data-stu-id="ae89b-433">Instructions</span></span>

* <span data-ttu-id="ae89b-434">No painel **hierarquia** , expanda **hologramacollection** e selecione **Underworld**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="ae89b-435">Expanda **Underworld** e selecione voicename.</span><span class="sxs-lookup"><span data-stu-id="ae89b-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="ae89b-436">No painel **Inspetor** , clique em **Adicionar componente** e adicionar **efeito de voz do usuário**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="ae89b-437">Um componente de **aúdio** será adicionado à **voiceprovider**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="ae89b-438">Em **áudio**, defina **saída** para **UserVoice (mixer)** .</span><span class="sxs-lookup"><span data-stu-id="ae89b-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="ae89b-439">Marque a  caixa de seleção espacialize.</span><span class="sxs-lookup"><span data-stu-id="ae89b-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="ae89b-440">Arraste o controle deslizante de **mistura espacial** para **3D**ou digite **1** na caixa de edição.</span><span class="sxs-lookup"><span data-stu-id="ae89b-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="ae89b-441">Expanda **configurações de som 3D**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="ae89b-442">Defina o **nível de Doppler** como **0**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="ae89b-443">Em **efeito de voz do usuário**, defina **objeto pai** como o **Underworld** da cena.</span><span class="sxs-lookup"><span data-stu-id="ae89b-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="ae89b-444">Defina a **distância máxima** como **1**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="ae89b-445">Definir a **distância máxima** informa o **efeito de voz do usuário** como fechar o usuário deve ser ao objeto pai antes de o efeito ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="ae89b-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="ae89b-446">Em **efeito de voz do usuário**, expanda **parâmetros Chorus**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="ae89b-447">Defina **profundidade** como **0,1**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="ae89b-448">Defina **tocar 1 volume**, **toque em 2 volume** e **toque em 3 volume** para **0,8**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="ae89b-449">Defina o **volume de som original** como **0,5**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="ae89b-450">As configurações anteriores configuram os parâmetros do Unity **AudioChorusFilter** usado para adicionar riqueza à voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="ae89b-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="ae89b-451">Em **efeito de voz do usuário**, expanda **parâmetros de eco**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="ae89b-452">Definir **atraso** como **300**</span><span class="sxs-lookup"><span data-stu-id="ae89b-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="ae89b-453">Defina a **taxa de decaimento** como **0,2**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="ae89b-454">Defina o **volume de som original** como **0**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="ae89b-455">As configurações anteriores configuram os parâmetros do Unity **AudioEchoFilter** usado para fazer com que a voz do usuário seja ecoada.</span><span class="sxs-lookup"><span data-stu-id="ae89b-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="ae89b-456">O script de efeito de voz do usuário é responsável por:</span><span class="sxs-lookup"><span data-stu-id="ae89b-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="ae89b-457">Medindo a distância entre o usuário e  o gameobject ao qual o script está anexado.</span><span class="sxs-lookup"><span data-stu-id="ae89b-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="ae89b-458">Determinando se o usuário está voltado para o gameobject.</span><span class="sxs-lookup"><span data-stu-id="ae89b-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="ae89b-459">O usuário deve estar voltado para o gameobject, independentemente da distância, para que o efeito seja habilitado.</span><span class="sxs-lookup"><span data-stu-id="ae89b-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="ae89b-460">Aplicando e configurando um **AudioChorusFilter** e um **AudioEchoFilter** para a **audioname**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="ae89b-461">Desabilitando o efeito, desabilitando os filtros.</span><span class="sxs-lookup"><span data-stu-id="ae89b-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="ae89b-462">O efeito de voz do usuário usa o componente seletor de fluxo do MIC, do [MixedRealityToolkit para o Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), para selecionar o fluxo de voz de alta qualidade e roteá-lo no sistema de áudio do Unity.</span><span class="sxs-lookup"><span data-stu-id="ae89b-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="ae89b-463">No painel **hierarquia** , selecione **gerentes**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="ae89b-464">No painel **Inspetor** , expanda **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="ae89b-465">Em **manipulador de entrada de fala**, expanda **Mostrar Underworld**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="ae89b-466">Altere **nenhuma função** para **UnderworldBase. OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Chaves Mostrar Underworld](images/showunderworld.png)

* <span data-ttu-id="ae89b-468">Expanda **ocultar Underworld**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="ae89b-469">Altere **nenhuma função** para **UnderworldBase. ondisable**.</span><span class="sxs-lookup"><span data-stu-id="ae89b-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Chaves Ocultar Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="ae89b-471">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="ae89b-471">Build and Deploy</span></span>

* <span data-ttu-id="ae89b-472">Como antes, compile o projeto no Unity e implante-o no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae89b-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="ae89b-473">Após a implantação do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ae89b-473">After the application is deployed:</span></span>

* <span data-ttu-id="ae89b-474">Face de uma superfície (parede, piso, tabela) e diga *"mostrar Underworld"* .</span><span class="sxs-lookup"><span data-stu-id="ae89b-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="ae89b-475">O Underworld será mostrado e todos os outros hologramas serão ocultados.</span><span class="sxs-lookup"><span data-stu-id="ae89b-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="ae89b-476">Se você não vir o Underworld, verifique se está enfrentando uma superfície do mundo real.</span><span class="sxs-lookup"><span data-stu-id="ae89b-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="ae89b-477">Abordagem em 1 metro do holograma do Underworld e comece a conversar.</span><span class="sxs-lookup"><span data-stu-id="ae89b-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="ae89b-478">Agora há efeitos de áudio aplicados à sua voz!</span><span class="sxs-lookup"><span data-stu-id="ae89b-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="ae89b-479">Desative o Underworld e observe como o efeito não é mais aplicado.</span><span class="sxs-lookup"><span data-stu-id="ae89b-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="ae89b-480">Diga *"Hide Underworld"* para ocultar o Underworld.</span><span class="sxs-lookup"><span data-stu-id="ae89b-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="ae89b-481">O Underworld ficará oculto e os hologramas ocultos anteriormente serão exibidos novamente.</span><span class="sxs-lookup"><span data-stu-id="ae89b-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="ae89b-482">Fim</span><span class="sxs-lookup"><span data-stu-id="ae89b-482">The End</span></span>

<span data-ttu-id="ae89b-483">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="ae89b-483">Congratulations!</span></span> <span data-ttu-id="ae89b-484">Agora você concluiu **o Sr Spatial 220: Som**espacial.</span><span class="sxs-lookup"><span data-stu-id="ae89b-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="ae89b-485">Ouça o mundo e dê vida às suas experiências com o som!</span><span class="sxs-lookup"><span data-stu-id="ae89b-485">Listen to the world and bring your experiences to life with sound!</span></span>

---
title: MR espacial 220 - som espacial
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para saber os detalhes dos conceitos de som espaciais.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, som espacial
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589375"
---
>[!NOTE]
><span data-ttu-id="87582-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="87582-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="87582-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="87582-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="87582-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="87582-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="87582-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="87582-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="87582-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="87582-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="87582-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="87582-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="87582-110">MR Spatial 220: Som espacial</span><span class="sxs-lookup"><span data-stu-id="87582-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="87582-111">[Som espacial](spatial-sound.md) dá vida em hologramas e lhes presença em nosso mundo.</span><span class="sxs-lookup"><span data-stu-id="87582-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="87582-112">Hologramas são compostas de luz e som e se você perder de vista seu hologramas, espacial som pode ajudá-lo a encontrá-los.</span><span class="sxs-lookup"><span data-stu-id="87582-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="87582-113">Som espacial não é como o som típico que você teria uma resposta no rádio, é o som que está posicionado no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="87582-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="87582-114">Com o som espacial, você pode fazer hologramas som que estão atrás de você, ao lado de você, ou até mesmo em sua cabeça!</span><span class="sxs-lookup"><span data-stu-id="87582-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="87582-115">Neste curso, você irá:</span><span class="sxs-lookup"><span data-stu-id="87582-115">In this course, you will:</span></span>

* <span data-ttu-id="87582-116">Configure seu ambiente de desenvolvimento para usar o Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="87582-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="87582-117">Use som espacial para aprimorar as interações.</span><span class="sxs-lookup"><span data-stu-id="87582-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="87582-118">Use som espacial em conjunto com o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="87582-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="87582-119">Entenda o design de som e misturar as práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="87582-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="87582-120">Usar som para aprimorar efeitos especiais e trazer o usuário para o mundo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="87582-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="87582-121">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="87582-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="87582-122">Curso</span><span class="sxs-lookup"><span data-stu-id="87582-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="87582-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="87582-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="87582-124"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="87582-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="87582-125">MR Spatial 220: Som espacial</span><span class="sxs-lookup"><span data-stu-id="87582-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="87582-126">✔️</span><span class="sxs-lookup"><span data-stu-id="87582-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="87582-127">✔️</span><span class="sxs-lookup"><span data-stu-id="87582-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="87582-128">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="87582-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="87582-129">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="87582-129">Prerequisites</span></span>

* <span data-ttu-id="87582-130">Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="87582-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="87582-131">Alguns basic C# capacidade de programação.</span><span class="sxs-lookup"><span data-stu-id="87582-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="87582-132">Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="87582-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="87582-133">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="87582-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="87582-134">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="87582-134">Project files</span></span>

* <span data-ttu-id="87582-135">Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="87582-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="87582-136"> Requer o Unity 2017.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="87582-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="87582-137">Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="87582-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="87582-138">Esta versão não pode ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="87582-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="87582-139">Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="87582-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="87582-140"> Esta versão não pode ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="87582-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="87582-141">Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="87582-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="87582-142"> Esta versão não pode ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="87582-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="87582-143">Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.</span><span class="sxs-lookup"><span data-stu-id="87582-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="87582-144">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="87582-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="87582-145">Errata e notas</span><span class="sxs-lookup"><span data-stu-id="87582-145">Errata and Notes</span></span>

* <span data-ttu-id="87582-146">"Habilitar apenas meu código" precisa ser desabilitado (*desmarcado*) no Visual Studio em Ferramentas -> Opções -> depuração para usar pontos de interrupção em seu código.</span><span class="sxs-lookup"><span data-stu-id="87582-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="87582-147">Capítulo 1 - instalação do Unity</span><span class="sxs-lookup"><span data-stu-id="87582-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="87582-148">Objetivos</span><span class="sxs-lookup"><span data-stu-id="87582-148">Objectives</span></span>

* <span data-ttu-id="87582-149">Altere configuração de som do Unity para usar o Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="87582-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="87582-150">Adicione som 3D a um objeto no Unity.</span><span class="sxs-lookup"><span data-stu-id="87582-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="87582-151">Instruções</span><span class="sxs-lookup"><span data-stu-id="87582-151">Instructions</span></span>

* <span data-ttu-id="87582-152">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="87582-152">Start Unity.</span></span>
* <span data-ttu-id="87582-153">Selecione **aberto**.</span><span class="sxs-lookup"><span data-stu-id="87582-153">Select **Open**.</span></span>
* <span data-ttu-id="87582-154">A área de trabalho e localizar a pasta que você navegue anteriormente não arquivadas.</span><span class="sxs-lookup"><span data-stu-id="87582-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="87582-155">Clique no **Starting\Decibel** pasta e, em seguida, pressione a **Selecionar pasta** botão.</span><span class="sxs-lookup"><span data-stu-id="87582-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="87582-156">Aguarde até que o projeto carregar no Unity.</span><span class="sxs-lookup"><span data-stu-id="87582-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="87582-157">No **Project** painel, abra **Scenes\Decibel.unity**.</span><span class="sxs-lookup"><span data-stu-id="87582-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="87582-158">No **hierarquia** do painel, expanda **HologramCollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="87582-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="87582-159">No Inspetor de propriedades, expanda **AudioSource** e observe que não há nenhum **Spatialize** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="87582-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="87582-160">Por padrão, o Unity não carrega um plug-in spatializer.</span><span class="sxs-lookup"><span data-stu-id="87582-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="87582-161">As etapas a seguir permitirá espacial som no projeto.</span><span class="sxs-lookup"><span data-stu-id="87582-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="87582-162">No menu superior do Unity, acesse **Editar > configurações do projeto > áudio**.</span><span class="sxs-lookup"><span data-stu-id="87582-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="87582-163">Localizar o **plug-in do Spatializer** dropdown e selecione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="87582-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="87582-164">No **hierarquia** painel, selecione **HologramCollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="87582-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="87582-165">No **Inspector** do painel, localize a **Audio Source** componente.</span><span class="sxs-lookup"><span data-stu-id="87582-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="87582-166">Verifique as **Spatialize** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="87582-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="87582-167">Arraste o **Blend espacial** controle deslizante até **3D**, ou insira **1** na caixa de edição.</span><span class="sxs-lookup"><span data-stu-id="87582-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="87582-168">Agora podemos compilar o projeto no Unity e configurar a solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87582-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="87582-169">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="87582-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="87582-170">Clique em **cenas abra Adicionar** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="87582-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="87582-171">Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="87582-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="87582-172">Se você estiver desenvolvendo especificamente para HoloLens, defina **dispositivo de destino** à **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="87582-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="87582-173">Caso contrário, deixe-nos **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="87582-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="87582-174">Certifique-se **Build Type** é definido como **D3D** e **SDK** é definido como **mais recente instalada** (que deve ser SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="87582-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="87582-175">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="87582-175">Click **Build**.</span></span>
7. <span data-ttu-id="87582-176">Criar uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="87582-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="87582-177">Único clique a **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="87582-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="87582-178">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="87582-178">Press **Select Folder**.</span></span>

<span data-ttu-id="87582-179">Quando Unity é feito, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="87582-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="87582-180">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="87582-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="87582-181">Abra o **solução do Visual Studio decibéis**.</span><span class="sxs-lookup"><span data-stu-id="87582-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="87582-182">Se a implantação para o HoloLens:</span><span class="sxs-lookup"><span data-stu-id="87582-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="87582-183">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="87582-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="87582-184">Clique na lista suspensa na seta ao lado do botão de computador Local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="87582-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="87582-185">Insira **seu endereço IP do dispositivo HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)**.</span><span class="sxs-lookup"><span data-stu-id="87582-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="87582-186">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="87582-186">Click **Select**.</span></span> <span data-ttu-id="87582-187">Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas de**.</span><span class="sxs-lookup"><span data-stu-id="87582-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="87582-188">Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="87582-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="87582-189">Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="87582-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="87582-190">Se implantar em um fone de ouvido imersivo:</span><span class="sxs-lookup"><span data-stu-id="87582-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="87582-191">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="87582-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="87582-192">Verifique se o destino de implantação é definido como **computador Local**.</span><span class="sxs-lookup"><span data-stu-id="87582-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="87582-193">Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="87582-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="87582-194">Capítulo 2 - interação e som espacial</span><span class="sxs-lookup"><span data-stu-id="87582-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="87582-195">Objetivos</span><span class="sxs-lookup"><span data-stu-id="87582-195">Objectives</span></span>

* <span data-ttu-id="87582-196">Aprimore o realismo holograma usando o som.</span><span class="sxs-lookup"><span data-stu-id="87582-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="87582-197">Direcione olhar do usuário usando o som.</span><span class="sxs-lookup"><span data-stu-id="87582-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="87582-198">Fornece comentários de gesto, uso de som.</span><span class="sxs-lookup"><span data-stu-id="87582-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="87582-199">Parte 1 - realismo melhorando</span><span class="sxs-lookup"><span data-stu-id="87582-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="87582-200">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="87582-200">Key Concepts</span></span>

* <span data-ttu-id="87582-201">Spatialize sons holograma.</span><span class="sxs-lookup"><span data-stu-id="87582-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="87582-202">Fontes de som devem ser colocados em um local apropriado no holograma.</span><span class="sxs-lookup"><span data-stu-id="87582-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="87582-203">O local apropriado para o som será dependem de holograma.</span><span class="sxs-lookup"><span data-stu-id="87582-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="87582-204">Por exemplo, se o holograma for de um ser humano, a fonte de som deve constar perto de boca e não os pés.</span><span class="sxs-lookup"><span data-stu-id="87582-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="87582-205">Instruções</span><span class="sxs-lookup"><span data-stu-id="87582-205">Instructions</span></span>

<span data-ttu-id="87582-206">As instruções a seguir se anexará um som spatialized um holograma.</span><span class="sxs-lookup"><span data-stu-id="87582-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="87582-207">No **hierarquia** do painel, expanda **HologramCollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="87582-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="87582-208">No **Inspector** painel, o **AudioSource**, clique no círculo ao lado de **AudioClip** e selecione **PolyHover** de pop-up.</span><span class="sxs-lookup"><span data-stu-id="87582-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="87582-209">Clique no círculo ao lado **saída** e selecione **SoundEffects** de pop-up.</span><span class="sxs-lookup"><span data-stu-id="87582-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="87582-210">Projeto decibéis usa um Unity **AudioMixer** para permitir que ajustar os níveis de som para grupos de sons.</span><span class="sxs-lookup"><span data-stu-id="87582-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="87582-211">Pelo agrupamento sons dessa forma, o volume total pode ser ajustado, mantendo o volume relativo de cada som.</span><span class="sxs-lookup"><span data-stu-id="87582-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="87582-212">No **AudioSource**, expanda **configurações de som 3D**.</span><span class="sxs-lookup"><span data-stu-id="87582-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="87582-213">Definir **Doppler em razão nível** à **0**.</span><span class="sxs-lookup"><span data-stu-id="87582-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="87582-214">Definindo Doppler em razão nível às alterações zero desabilita no tom causado pelo motion (seja o holograma ou o usuário).</span><span class="sxs-lookup"><span data-stu-id="87582-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="87582-215">Um exemplo clássico de Doppler em razão é que um carro ágeis.</span><span class="sxs-lookup"><span data-stu-id="87582-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="87582-216">Como o carro se aproxima de um ouvinte estacionário, aumenta o tom do mecanismo.</span><span class="sxs-lookup"><span data-stu-id="87582-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="87582-217">Ao passar o ouvinte, o tom reduz com distância.</span><span class="sxs-lookup"><span data-stu-id="87582-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="87582-218">Parte 2 - direcionando olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="87582-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="87582-219">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="87582-219">Key Concepts</span></span>

* <span data-ttu-id="87582-220">Usar som para chamar a atenção para hologramas importantes.</span><span class="sxs-lookup"><span data-stu-id="87582-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="87582-221">Os ouvidos ajudam a direcionar onde procurar os olhos.</span><span class="sxs-lookup"><span data-stu-id="87582-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="87582-222">O cérebro tem algumas expectativas aprendidas.</span><span class="sxs-lookup"><span data-stu-id="87582-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="87582-223">Um exemplo de expectativas aprendidos é pássaros geralmente são acima de cabeça de seres humanos.</span><span class="sxs-lookup"><span data-stu-id="87582-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="87582-224">Se um usuário ouve um som bird, sua reação inicial é pesquisar.</span><span class="sxs-lookup"><span data-stu-id="87582-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="87582-225">Colocar um pássaro abaixo do usuário pode levar a eles voltados para a direção correta do som, mas não ser capaz de localizar o holograma com base na expectativa de que precisam pesquisar.</span><span class="sxs-lookup"><span data-stu-id="87582-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="87582-226">Instruções</span><span class="sxs-lookup"><span data-stu-id="87582-226">Instructions</span></span>

<span data-ttu-id="87582-227">As instruções a seguir permitem P0LY ocultar atrás de você, para que você pode usar som para localizar o holograma.</span><span class="sxs-lookup"><span data-stu-id="87582-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="87582-228">No **hierarquia** painel, selecione **gerenciadores**.</span><span class="sxs-lookup"><span data-stu-id="87582-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="87582-229">No **Inspector** do painel, localize **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="87582-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="87582-230">Na **manipulador de entrada de fala**, expanda **vá ocultar**.</span><span class="sxs-lookup"><span data-stu-id="87582-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="87582-231">Alteração **nenhuma função** à **PolyActions.GoHide**.</span><span class="sxs-lookup"><span data-stu-id="87582-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![palavra-chave: Ocultar vá](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="87582-233">Parte 3 - comentários de gesto</span><span class="sxs-lookup"><span data-stu-id="87582-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="87582-234">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="87582-234">Key Concepts</span></span>

* <span data-ttu-id="87582-235">Fornecer ao usuário usando o som de confirmação de gesto positivo</span><span class="sxs-lookup"><span data-stu-id="87582-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="87582-236">Não sobrecarregar o usuário - get sons excessivamente altos da forma</span><span class="sxs-lookup"><span data-stu-id="87582-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="87582-237">Sons sutis funcionam melhor - não obscurecem a experiência</span><span class="sxs-lookup"><span data-stu-id="87582-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="87582-238">Instruções</span><span class="sxs-lookup"><span data-stu-id="87582-238">Instructions</span></span>

* <span data-ttu-id="87582-239">No **hierarquia** do painel, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="87582-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="87582-240">Expandir **EnergyHub** e selecione **Base**.</span><span class="sxs-lookup"><span data-stu-id="87582-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="87582-241">No **Inspector** do painel, clique em **Add Component** e adicione **manipulador do gesto de som**.</span><span class="sxs-lookup"><span data-stu-id="87582-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="87582-242">Na **manipulador do gesto de som**, clique no círculo ao lado de **navegação iniciado Clip** e **navegação atualizado Clip** e selecione **RotateClick**de pop-up para ambos.</span><span class="sxs-lookup"><span data-stu-id="87582-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="87582-243">Clique duas vezes em "GestureSoundHandler" para carregar no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87582-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="87582-244">Manipulador de gesto som executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="87582-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="87582-245">Criar e configurar uma **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="87582-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="87582-246">Coloque o **AudioSource** no local do apropriado **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="87582-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="87582-247">Reproduz o **AudioClip** associadas ao gesto.</span><span class="sxs-lookup"><span data-stu-id="87582-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="87582-248">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="87582-248">Build and Deploy</span></span>

1. <span data-ttu-id="87582-249">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="87582-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="87582-250">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="87582-250">Click **Build**.</span></span>
3. <span data-ttu-id="87582-251">Único clique a **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="87582-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="87582-252">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="87582-252">Press **Select Folder**.</span></span>

<span data-ttu-id="87582-253">Verifique se a barra de ferramentas diz "Versão", "x86" ou "x64" e "Dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="87582-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="87582-254">Caso contrário, a instância de codificação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87582-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="87582-255">Talvez você precise reabra a solução da pasta de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87582-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="87582-256">Se solicitado, recarregue os arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="87582-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="87582-257">Como antes, implante do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87582-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="87582-258">Depois que o aplicativo é implantado:</span><span class="sxs-lookup"><span data-stu-id="87582-258">After the application is deployed:</span></span>

* <span data-ttu-id="87582-259">Observe como o som é alterado conforme você movimenta P0LY.</span><span class="sxs-lookup"><span data-stu-id="87582-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="87582-260">Digamos *"Ocultar ir"* fazer P0LY mover para um local atrás de você.</span><span class="sxs-lookup"><span data-stu-id="87582-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="87582-261">Para encontrá-lo pelo som.</span><span class="sxs-lookup"><span data-stu-id="87582-261">Find it by the sound.</span></span>
* <span data-ttu-id="87582-262">Mantenha o foco na base do Hub de energia.</span><span class="sxs-lookup"><span data-stu-id="87582-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="87582-263">Toque e arraste a esquerda ou direita para girar o holograma e observe como o som clicando em confirma o gesto.</span><span class="sxs-lookup"><span data-stu-id="87582-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="87582-264">Observação: Há um painel de texto que será tag-along com você.</span><span class="sxs-lookup"><span data-stu-id="87582-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="87582-265">Isso irá conter os comandos de voz disponíveis que podem ser usados durante o curso.</span><span class="sxs-lookup"><span data-stu-id="87582-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="87582-266">Capítulo 3 - mapeamento espacial do som e espacial</span><span class="sxs-lookup"><span data-stu-id="87582-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="87582-267">Objetivos</span><span class="sxs-lookup"><span data-stu-id="87582-267">Objectives</span></span>

* <span data-ttu-id="87582-268">Confirme a interação entre hologramas e o mundo real usando o som.</span><span class="sxs-lookup"><span data-stu-id="87582-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="87582-269">Occlude som usando mundo físico.</span><span class="sxs-lookup"><span data-stu-id="87582-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="87582-270">Parte 1 – interação do mundo físico</span><span class="sxs-lookup"><span data-stu-id="87582-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="87582-271">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="87582-271">Key Concepts</span></span>

* <span data-ttu-id="87582-272">Objetos físicos geralmente emita um som quando se deparar com uma superfície ou outro objeto.</span><span class="sxs-lookup"><span data-stu-id="87582-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="87582-273">Sons devem ser apropriada em uma experiência de contexto.</span><span class="sxs-lookup"><span data-stu-id="87582-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="87582-274">Por exemplo, definindo uma xícara em uma tabela deve emitir um som mais discreta que descartar um boulder em um pedaço de metal.</span><span class="sxs-lookup"><span data-stu-id="87582-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="87582-275">Instruções</span><span class="sxs-lookup"><span data-stu-id="87582-275">Instructions</span></span>

* <span data-ttu-id="87582-276">No **hierarquia** do painel, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="87582-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="87582-277">Expandir **EnergyHub**, selecione **Base**.</span><span class="sxs-lookup"><span data-stu-id="87582-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="87582-278">No **Inspector** do painel, clique em **Add Component** e adicione **ação e toque em vigor para com som**.</span><span class="sxs-lookup"><span data-stu-id="87582-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="87582-279">Na **toque para local com o som e ação**:</span><span class="sxs-lookup"><span data-stu-id="87582-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="87582-280">Verifique **colocar pai com um toque de**.</span><span class="sxs-lookup"><span data-stu-id="87582-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="87582-281">Definir **som de posicionamento** à **lugar**.</span><span class="sxs-lookup"><span data-stu-id="87582-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="87582-282">Definir **som Pickup** à **Pickup**.</span><span class="sxs-lookup"><span data-stu-id="87582-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="87582-283">Pressione + na parte inferior direita em ambos **na ação de Pickup** e **na ação de posicionamento**.</span><span class="sxs-lookup"><span data-stu-id="87582-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="87582-284">Arraste EnergyHub da cena para o **None (objeto)** campos.</span><span class="sxs-lookup"><span data-stu-id="87582-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="87582-285">Sob **na ação de Pickup**, clique em **nenhuma função** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="87582-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="87582-286">Sob **na ação de posicionamento**, clique em **nenhuma função** -> **EnergyHubBase** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="87582-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Toque para local com o som e ação](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="87582-288">Parte 2 - oclusão som</span><span class="sxs-lookup"><span data-stu-id="87582-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="87582-289">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="87582-289">Key Concepts</span></span>

* <span data-ttu-id="87582-290">Som, como a luz, pode ser obstruído.</span><span class="sxs-lookup"><span data-stu-id="87582-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="87582-291">Um exemplo clássico é uma sala de concertos.</span><span class="sxs-lookup"><span data-stu-id="87582-291">A classic example is a concert hall.</span></span> <span data-ttu-id="87582-292">Quando um ouvinte está aguardando fora da empresa e a porta for fechada, os sons de música muffled.</span><span class="sxs-lookup"><span data-stu-id="87582-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="87582-293">Também há normalmente uma redução no volume.</span><span class="sxs-lookup"><span data-stu-id="87582-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="87582-294">Quando a porta é aberta, todo o espectro do som é ouvido no volume real.</span><span class="sxs-lookup"><span data-stu-id="87582-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="87582-295">Sons de alta frequência geralmente são absorvidas mais de frequências baixa.</span><span class="sxs-lookup"><span data-stu-id="87582-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="87582-296">Instruções</span><span class="sxs-lookup"><span data-stu-id="87582-296">Instructions</span></span>

* <span data-ttu-id="87582-297">No **hierarquia** do painel, expanda **HologramCollection** e selecione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="87582-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="87582-298">No **Inspector** do painel, clique em **Add Component** e adicione **emissor de áudio**.</span><span class="sxs-lookup"><span data-stu-id="87582-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="87582-299">A classe de emissor de áudio fornece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="87582-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="87582-300">Restaura todas as alterações para o volume do **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="87582-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="87582-301">Executa um **Physics.RaycastNonAlloc** da posição do usuário na direção do **GameObject** à qual o **AudioEmitter** está anexado.</span><span class="sxs-lookup"><span data-stu-id="87582-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="87582-302">O método RaycastNonAlloc é usado como uma otimização de desempenho para limitar as alocações, bem como o número de resultados retornados.</span><span class="sxs-lookup"><span data-stu-id="87582-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="87582-303">Para cada **IAudioInfluencer** encontrado, chamadas a **ApplyEffect** método.</span><span class="sxs-lookup"><span data-stu-id="87582-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="87582-304">Para cada anterior **IAudioInfluencer** que é chamada de não encontrada, o **RemoveEffect** método.</span><span class="sxs-lookup"><span data-stu-id="87582-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="87582-305">Observe que AudioEmitter atualiza em escalas de tempo humano, em vez de em uma base por quadro.</span><span class="sxs-lookup"><span data-stu-id="87582-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="87582-306">Isso é feito porque seres humanos geralmente não são movidos rápido o suficiente para o efeito para precisam ser atualizadas com mais frequência do que a cada trimestre ou meio segundo.</span><span class="sxs-lookup"><span data-stu-id="87582-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="87582-307">Hologramas que ser transportado rapidamente de um local para outro pode quebrar a ilusão.</span><span class="sxs-lookup"><span data-stu-id="87582-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="87582-308">No **hierarquia** do painel, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="87582-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="87582-309">Expandir **EnergyHub** e selecione **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="87582-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="87582-310">No **Inspector** do painel, clique em **Add Component** e adicione **Occluder áudio**.</span><span class="sxs-lookup"><span data-stu-id="87582-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="87582-311">Na **Occluder áudio**, defina **frequência de corte** para **1500**.</span><span class="sxs-lookup"><span data-stu-id="87582-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="87582-312">Essa configuração limita as frequências de AudioSource para 1500 Hz e abaixo.</span><span class="sxs-lookup"><span data-stu-id="87582-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="87582-313">Definir **passagem de Volume** à **0.9**.</span><span class="sxs-lookup"><span data-stu-id="87582-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="87582-314">Essa configuração reduz o volume do AudioSource a 90% de seu nível atual.</span><span class="sxs-lookup"><span data-stu-id="87582-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="87582-315">Áudio Occluder implementa IAudioInfluencer para:</span><span class="sxs-lookup"><span data-stu-id="87582-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="87582-316">Aplicar um efeito de oclusão usando um **AudioLowPassFilter** que é anexado ao **AudioSource** gerenciado comprar os **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="87582-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="87582-317">Aplica-se de atenuação de volume para o AudioSource.</span><span class="sxs-lookup"><span data-stu-id="87582-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="87582-318">Desabilita o efeito, definindo uma frequência de corte neutra e desabilitar o filtro.</span><span class="sxs-lookup"><span data-stu-id="87582-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="87582-319">A frequência usada como neutra é 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="87582-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="87582-320">Essa frequência foi escolhida estarem acima a nominal frequência máxima que pode ser ouvida pelo ouvido humano, este fazendo nenhum impacto perceptível para o som.</span><span class="sxs-lookup"><span data-stu-id="87582-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="87582-321">No **hierarquia** painel, selecione **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="87582-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="87582-322">No **Inspector** do painel, clique em **Add Component** e adicione **Occluder áudio**.</span><span class="sxs-lookup"><span data-stu-id="87582-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="87582-323">Na **Occluder áudio**, defina **frequência de corte** para **750**.</span><span class="sxs-lookup"><span data-stu-id="87582-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="87582-324">Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a frequência mais baixa é aplicada ao filtro.</span><span class="sxs-lookup"><span data-stu-id="87582-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="87582-325">Definir **passagem de Volume** à **0,75**.</span><span class="sxs-lookup"><span data-stu-id="87582-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="87582-326">Quando vários occluders estão no caminho entre o usuário e o **AudioEmitter**, a passagem do volume é aplicada de fogo.</span><span class="sxs-lookup"><span data-stu-id="87582-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="87582-327">No **hierarquia** painel, selecione **gerenciadores**.</span><span class="sxs-lookup"><span data-stu-id="87582-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="87582-328">No **Inspector** do painel, expanda **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="87582-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="87582-329">Na **manipulador de entrada de fala**, expanda **vá encargo**.</span><span class="sxs-lookup"><span data-stu-id="87582-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="87582-330">Alteração **nenhuma função** à **PolyActions.GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="87582-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![palavra-chave: Acesse o encargo](images/gocharge.png)

* <span data-ttu-id="87582-332">Expandir **vir aqui**.</span><span class="sxs-lookup"><span data-stu-id="87582-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="87582-333">Alteração **nenhuma função** à **PolyActions.ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="87582-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![palavra-chave: Vem cá](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="87582-335">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="87582-335">Build and Deploy</span></span>

* <span data-ttu-id="87582-336">Como antes, compile o projeto no Unity e implantar no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87582-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="87582-337">Depois que o aplicativo é implantado:</span><span class="sxs-lookup"><span data-stu-id="87582-337">After the application is deployed:</span></span>

* <span data-ttu-id="87582-338">Digamos *"Cobrança de ir"* ter P0LY insira o Hub de energia.</span><span class="sxs-lookup"><span data-stu-id="87582-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="87582-339">Observe a alteração no som.</span><span class="sxs-lookup"><span data-stu-id="87582-339">Note the change in the sound.</span></span> <span data-ttu-id="87582-340">Ele deve parecer um pouco mais discreta e muffled.</span><span class="sxs-lookup"><span data-stu-id="87582-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="87582-341">Se você for capaz de se posicionando com uma parede ou outro objeto entre você e o Hub de energia, você deve observar um muffling adicional do som devido à oclusão pelo mundo real.</span><span class="sxs-lookup"><span data-stu-id="87582-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="87582-342">Digamos *"Vir aqui"* ter P0LY deixe o Hub de energia e se posicionar na sua frente.</span><span class="sxs-lookup"><span data-stu-id="87582-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="87582-343">Observe que o som oclusão é removida depois P0LY sai no Hub de energia.</span><span class="sxs-lookup"><span data-stu-id="87582-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="87582-344">Se você ainda estiver oclusão auditivas, P0LY pode ser obstruídos pelo mundo real.</span><span class="sxs-lookup"><span data-stu-id="87582-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="87582-345">Tente mover para garantir que você tenha uma linha de visão clara para P0LY.</span><span class="sxs-lookup"><span data-stu-id="87582-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="87582-346">Parte 3 – modelos de espaço</span><span class="sxs-lookup"><span data-stu-id="87582-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="87582-347">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="87582-347">Key Concepts</span></span>

* <span data-ttu-id="87582-348">O tamanho do espaço fornece filas subliminar que contribuem para a localização de som.</span><span class="sxs-lookup"><span data-stu-id="87582-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="87582-349">Modelos de espaço são definidos por-**AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="87582-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="87582-350">O [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornece código para definir o modelo de espaço.</span><span class="sxs-lookup"><span data-stu-id="87582-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="87582-351">Para experiências de realidade misturada, selecione o modelo de espaço que melhor se adapta o espaço de mundo real.</span><span class="sxs-lookup"><span data-stu-id="87582-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="87582-352">Se você estiver criando um cenário de realidade Virtual, selecione o modelo de espaço que melhor se adapta o ambiente virtual.</span><span class="sxs-lookup"><span data-stu-id="87582-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="87582-353">Capítulo 4 - Design som</span><span class="sxs-lookup"><span data-stu-id="87582-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="87582-354">Objetivos</span><span class="sxs-lookup"><span data-stu-id="87582-354">Objectives</span></span>

* <span data-ttu-id="87582-355">Entenda as considerações sobre design eficaz de som.</span><span class="sxs-lookup"><span data-stu-id="87582-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="87582-356">Aprenda técnicas de mixagem e diretrizes.</span><span class="sxs-lookup"><span data-stu-id="87582-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="87582-357">Parte 1 - experiência de Design e som</span><span class="sxs-lookup"><span data-stu-id="87582-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="87582-358">Esta seção discute o som de chave e diretrizes e considerações de design de experiência.</span><span class="sxs-lookup"><span data-stu-id="87582-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="87582-359">Normalizar todos os sons</span><span class="sxs-lookup"><span data-stu-id="87582-359">Normalize all sounds</span></span>

<span data-ttu-id="87582-360">Isso evita a necessidade de código caso especial ajustar os níveis de volume por som, que pode ser demorado e limita a capacidade de atualizar facilmente os arquivos de som.</span><span class="sxs-lookup"><span data-stu-id="87582-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="87582-361">Design para uma experiência de ilimitado</span><span class="sxs-lookup"><span data-stu-id="87582-361">Design for an untethered experience</span></span>

<span data-ttu-id="87582-362">HoloLens é um computador holográfico totalmente independente, de forma independente.</span><span class="sxs-lookup"><span data-stu-id="87582-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="87582-363">Os usuários podem e usarão suas experiências durante a movimentação.</span><span class="sxs-lookup"><span data-stu-id="87582-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="87582-364">Certifique-se de testar sua combinação de áudio por andar.</span><span class="sxs-lookup"><span data-stu-id="87582-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="87582-365">Emitir um som de locais lógicos em seu hologramas</span><span class="sxs-lookup"><span data-stu-id="87582-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="87582-366">No mundo real, não de um cachorro latido de cauda e voz de um ser humano não vem de seus pés.</span><span class="sxs-lookup"><span data-stu-id="87582-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="87582-367">Evite ter que os sons de emissão de inesperado partes do seu hologramas.</span><span class="sxs-lookup"><span data-stu-id="87582-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="87582-368">Hologramas pequenas, é razoável para ter o som emitir a partir do centro da geometria.</span><span class="sxs-lookup"><span data-stu-id="87582-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="87582-369">Parece familiar é mais localizáveis</span><span class="sxs-lookup"><span data-stu-id="87582-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="87582-370">A voz humana e a música são muito fáceis de localizar.</span><span class="sxs-lookup"><span data-stu-id="87582-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="87582-371">Se alguém liga para seu nome, será possível com bastante precisão determinar de qual direção veio a voz e de como distantes.</span><span class="sxs-lookup"><span data-stu-id="87582-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="87582-372">Sons de curtos e desconhecidos são mais difíceis de localizar.</span><span class="sxs-lookup"><span data-stu-id="87582-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="87582-373">Estar ciente das expectativas do usuário</span><span class="sxs-lookup"><span data-stu-id="87582-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="87582-374">Experiência de vida desempenha um papel na nossa capacidade de identificar o local de um som.</span><span class="sxs-lookup"><span data-stu-id="87582-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="87582-375">Esse é um motivo por que a voz humana é particularmente fácil de localizar.</span><span class="sxs-lookup"><span data-stu-id="87582-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="87582-376">É importante estar ciente das expectativas de aprendido do seu usuário ao colocar sua sons.</span><span class="sxs-lookup"><span data-stu-id="87582-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="87582-377">Por exemplo, quando alguém ouve uma música bird geralmente pesquisados, como de pássaros tendem a ser acima da linha de visão (voadora ou em uma árvore).</span><span class="sxs-lookup"><span data-stu-id="87582-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="87582-378">Não é incomum para um usuário ativar na direção correta de um som, mas procurar na direção vertical errada e ficar frustrados ou confusos quando não for possível encontrar o holograma.</span><span class="sxs-lookup"><span data-stu-id="87582-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="87582-379">Evite os emissores ocultos</span><span class="sxs-lookup"><span data-stu-id="87582-379">Avoid hidden emitters</span></span>

<span data-ttu-id="87582-380">No mundo real, se você respondeu a um som, geralmente podemos pode identificar o objeto que está emitindo o som.</span><span class="sxs-lookup"><span data-stu-id="87582-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="87582-381">Isso também deve considerar verdadeiro em suas experiências.</span><span class="sxs-lookup"><span data-stu-id="87582-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="87582-382">Ele pode ser muito desconcertante para usuários de um som, saber por onde o som se origina e não conseguir ver a um objeto.</span><span class="sxs-lookup"><span data-stu-id="87582-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="87582-383">Há algumas exceções a essa diretriz.</span><span class="sxs-lookup"><span data-stu-id="87582-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="87582-384">Por exemplo, os sons de ambientes como crickets em um campo não precisam estar visíveis.</span><span class="sxs-lookup"><span data-stu-id="87582-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="87582-385">Experiência de vida nos dá a familiaridade com a origem desses sons sem a necessidade de vê-lo.</span><span class="sxs-lookup"><span data-stu-id="87582-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="87582-386">Parte 2 - mixagem de som</span><span class="sxs-lookup"><span data-stu-id="87582-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="87582-387">Direcionar sua combinação para o volume de 70% sobre o HoloLens</span><span class="sxs-lookup"><span data-stu-id="87582-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="87582-388">Experiências de realidade misturadas permitem hologramas sejam vistas no mundo real.</span><span class="sxs-lookup"><span data-stu-id="87582-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="87582-389">Eles também devem permitir que os sons do mundo real para ser ouvido.</span><span class="sxs-lookup"><span data-stu-id="87582-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="87582-390">Um destino de 70% volume permite que o usuário ouça o mundo ao redor deles junto com o som de sua experiência.</span><span class="sxs-lookup"><span data-stu-id="87582-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="87582-391">HoloLens no volume de 100% devem inundar out sons externos</span><span class="sxs-lookup"><span data-stu-id="87582-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="87582-392">Um nível de volume de 100% é semelhante de uma experiência de realidade Virtual.</span><span class="sxs-lookup"><span data-stu-id="87582-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="87582-393">Visualmente, o usuário é transportado para um mundo diferente.</span><span class="sxs-lookup"><span data-stu-id="87582-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="87582-394">O mesmo deve considerar verdadeiro poder ouvi-lo.</span><span class="sxs-lookup"><span data-stu-id="87582-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="87582-395">Usar o Unity AudioMixer para ajustar a categorias de sons</span><span class="sxs-lookup"><span data-stu-id="87582-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="87582-396">Ao projetar sua combinação, geralmente é útil criar categorias de som e ter a capacidade de aumentar ou diminuir o volume como uma unidade.</span><span class="sxs-lookup"><span data-stu-id="87582-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="87582-397">Isso mantém os níveis relativos de cada som ao mesmo tempo, permitindo que as alterações rápidas e fácil a combinação geral.</span><span class="sxs-lookup"><span data-stu-id="87582-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="87582-398">As categorias comuns incluem; efeitos sonoros, ambiente, os focos de voz e música em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="87582-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="87582-399">Sons de combinação com base em olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="87582-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="87582-400">Ele geralmente pode ser úteis alterar a combinação de som em sua experiência com base em onde um usuário é (ou não) procurando.</span><span class="sxs-lookup"><span data-stu-id="87582-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="87582-401">Um uso comum para essa técnica são para reduzir o nível de volume para hologramas que estão fora do quadro holográfica para tornar mais fácil para o usuário para se concentrar nas informações na frente delas.</span><span class="sxs-lookup"><span data-stu-id="87582-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="87582-402">Outro uso é para aumentar o volume de um som para chamar a atenção do usuário para um evento importante.</span><span class="sxs-lookup"><span data-stu-id="87582-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="87582-403">Criando sua combinação</span><span class="sxs-lookup"><span data-stu-id="87582-403">Building your mix</span></span>

<span data-ttu-id="87582-404">Ao criar sua combinação, é recomendável começar com o áudio de fundo da sua experiência e adicionar camadas com base na importância.</span><span class="sxs-lookup"><span data-stu-id="87582-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="87582-405">Geralmente, isso resulta em cada camada que está sendo mais alto do que o anterior.</span><span class="sxs-lookup"><span data-stu-id="87582-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="87582-406">Imaginando sua combinação como um funil invertido, com menos importante (e geralmente quietest sons) na parte inferior, é recomendável para estruturar sua combinação semelhante para o diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="87582-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Estrutura de mistura de som](images/soundlevels.png)

<span data-ttu-id="87582-408">Os focos de voz são um cenário interessante.</span><span class="sxs-lookup"><span data-stu-id="87582-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="87582-409">Com base na experiência que você está criando, talvez seja conveniente ter um som (não localizado) estéreo ou spatialize focos sua voz.</span><span class="sxs-lookup"><span data-stu-id="87582-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="87582-410">Dois a Microsoft publicou experiências ilustram excelentes exemplos de cada cenário.</span><span class="sxs-lookup"><span data-stu-id="87582-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="87582-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa uma voz estéreo sobre.</span><span class="sxs-lookup"><span data-stu-id="87582-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="87582-412">Quando o narrator está descrevendo o local que está sendo visualizado, o som é consistente e não variam de acordo com a posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="87582-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="87582-413">Isso permite que o Narrador descrever a cena sem tirar longe os sons spatialized do ambiente.</span><span class="sxs-lookup"><span data-stu-id="87582-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="87582-414">[Fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utiliza uma voz spatialized sobre na forma de um detetive.</span><span class="sxs-lookup"><span data-stu-id="87582-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="87582-415">Voz do detetive é usado para ajudar a trazer a atenção do usuário para uma dica importante, como se fosse de um real humanos na sala.</span><span class="sxs-lookup"><span data-stu-id="87582-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="87582-416">Isso permite que um senso ainda maior de imersão na experiência de resolver o mistério.</span><span class="sxs-lookup"><span data-stu-id="87582-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="87582-417">Parte 3 - desempenho</span><span class="sxs-lookup"><span data-stu-id="87582-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="87582-418">Uso da CPU</span><span class="sxs-lookup"><span data-stu-id="87582-418">CPU usage</span></span>

<span data-ttu-id="87582-419">Ao usar o som espacial, emissores de 10 a 12 consumirá aproximadamente 12% da CPU.</span><span class="sxs-lookup"><span data-stu-id="87582-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="87582-420">Arquivos de áudio longa Stream</span><span class="sxs-lookup"><span data-stu-id="87582-420">Stream long audio files</span></span>

<span data-ttu-id="87582-421">Dados de áudio podem ser grandes, especialmente em taxas de amostragem comuns (48 e 44,1 kHz).</span><span class="sxs-lookup"><span data-stu-id="87582-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="87582-422">Uma regra geral é que os arquivos de áudio com mais de 5 a 10 segundos devem ser transmitidos para reduzir o uso de memória do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="87582-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="87582-423">No Unity, você pode marcar um arquivo de áudio para streaming nas configurações de importação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="87582-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Configurações de importação de áudio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="87582-425">Capítulo 5 - efeitos especiais</span><span class="sxs-lookup"><span data-stu-id="87582-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="87582-426">Objetivos</span><span class="sxs-lookup"><span data-stu-id="87582-426">Objectives</span></span>

* <span data-ttu-id="87582-427">Adicione profundidade a "Mágica do Windows".</span><span class="sxs-lookup"><span data-stu-id="87582-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="87582-428">Traga o usuário para o mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="87582-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="87582-429">Windows mágico</span><span class="sxs-lookup"><span data-stu-id="87582-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="87582-430">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="87582-430">Key Concepts</span></span>

* <span data-ttu-id="87582-431">Criando modos de exibição para o mundo oculto, é visualmente atraente.</span><span class="sxs-lookup"><span data-stu-id="87582-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="87582-432">Aprimore o realismo adicionando efeitos de áudio, quando um holograma ou o usuário está próximo do mundo oculto.</span><span class="sxs-lookup"><span data-stu-id="87582-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="87582-433">Instruções</span><span class="sxs-lookup"><span data-stu-id="87582-433">Instructions</span></span>

* <span data-ttu-id="87582-434">No **hierarquia** do painel, expanda **HologramCollection** e selecione **mundo virtual**.</span><span class="sxs-lookup"><span data-stu-id="87582-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="87582-435">Expandir **mundo virtual** e selecione **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="87582-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="87582-436">No **Inspector** do painel, clique em **Add Component** e adicione **efeito de voz do usuário**.</span><span class="sxs-lookup"><span data-stu-id="87582-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="87582-437">Uma **AudioSource** será adicionado ao componente **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="87582-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="87582-438">Na **AudioSource**, defina **saída** para **UserVoice (Mixer)**.</span><span class="sxs-lookup"><span data-stu-id="87582-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="87582-439">Verifique as **Spatialize** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="87582-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="87582-440">Arraste o **Blend espacial** controle deslizante até **3D**, ou insira **1** na caixa de edição.</span><span class="sxs-lookup"><span data-stu-id="87582-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="87582-441">Expandir **configurações de som 3D**.</span><span class="sxs-lookup"><span data-stu-id="87582-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="87582-442">Definir **Doppler em razão nível** à **0**.</span><span class="sxs-lookup"><span data-stu-id="87582-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="87582-443">Na **efeito de voz do usuário**, defina **objeto pai** para o **mundo virtual** da cena.</span><span class="sxs-lookup"><span data-stu-id="87582-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="87582-444">Definir **distância máxima** à **1**.</span><span class="sxs-lookup"><span data-stu-id="87582-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="87582-445">Definindo **distância máxima** informa **efeito de voz do usuário** quão próximo o usuário deve ser feita no objeto pai antes do efeito está habilitado.</span><span class="sxs-lookup"><span data-stu-id="87582-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="87582-446">Na **efeito de voz do usuário**, expanda **coro parâmetros**.</span><span class="sxs-lookup"><span data-stu-id="87582-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="87582-447">Definir **profundidade** à **0,1**.</span><span class="sxs-lookup"><span data-stu-id="87582-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="87582-448">Definir **toque em 1 Volume**, **toque Volume 2** e **toque Volume 3** para **0.8**.</span><span class="sxs-lookup"><span data-stu-id="87582-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="87582-449">Definir **Volume do som Original** à **0,5**.</span><span class="sxs-lookup"><span data-stu-id="87582-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="87582-450">As configurações anteriores configuram os parâmetros do Unity **AudioChorusFilter** usado para adicionar a riqueza a voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="87582-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="87582-451">Na **efeito de voz do usuário**, expanda **parâmetros de eco**.</span><span class="sxs-lookup"><span data-stu-id="87582-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="87582-452">Definir **atraso** para **300**</span><span class="sxs-lookup"><span data-stu-id="87582-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="87582-453">Definir **Decay taxa** à **0,2**.</span><span class="sxs-lookup"><span data-stu-id="87582-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="87582-454">Definir **Volume do som Original** à **0**.</span><span class="sxs-lookup"><span data-stu-id="87582-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="87582-455">As configurações anteriores configuram os parâmetros do Unity **AudioEchoFilter** usado para fazer com que a voz do usuário repetir.</span><span class="sxs-lookup"><span data-stu-id="87582-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="87582-456">O script de efeito de voz do usuário é responsável por:</span><span class="sxs-lookup"><span data-stu-id="87582-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="87582-457">Medir a distância entre o usuário e o **GameObject** à qual o script está associado.</span><span class="sxs-lookup"><span data-stu-id="87582-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="87582-458">Determinando se o usuário estiver voltada para o **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="87582-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="87582-459">O usuário deve ser voltada para o GameObject, independentemente da distância, para o efeito a ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="87582-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="87582-460">Aplicar e definir um **AudioChorusFilter** e uma **AudioEchoFilter** para o **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="87582-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="87582-461">Desabilitando o efeito ao desabilitar os filtros.</span><span class="sxs-lookup"><span data-stu-id="87582-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="87582-462">Efeito de voz do usuário usa o componente de Mic Stream seletor, do [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)para selecionar o fluxo de voz de alta qualidade e encaminhá-lo no sistema de áudio do Unity.</span><span class="sxs-lookup"><span data-stu-id="87582-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="87582-463">No **hierarquia** painel, selecione **gerenciadores**.</span><span class="sxs-lookup"><span data-stu-id="87582-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="87582-464">No **Inspector** do painel, expanda **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="87582-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="87582-465">Na **manipulador de entrada de fala**, expanda **mundo virtual de mostrar**.</span><span class="sxs-lookup"><span data-stu-id="87582-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="87582-466">Alteração **nenhuma função** à **UnderworldBase.OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="87582-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![palavra-chave: Mostrar o mundo virtual](images/showunderworld.png)

* <span data-ttu-id="87582-468">Expandir **ocultar mundo virtual**.</span><span class="sxs-lookup"><span data-stu-id="87582-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="87582-469">Alteração **nenhuma função** à **UnderworldBase.OnDisable**.</span><span class="sxs-lookup"><span data-stu-id="87582-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![palavra-chave: Ocultar o mundo virtual](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="87582-471">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="87582-471">Build and Deploy</span></span>

* <span data-ttu-id="87582-472">Como antes, compile o projeto no Unity e implantar no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87582-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="87582-473">Depois que o aplicativo é implantado:</span><span class="sxs-lookup"><span data-stu-id="87582-473">After the application is deployed:</span></span>

* <span data-ttu-id="87582-474">Enfrentam uma superfície (parede, floor, tabela) e dizer *"Mundo virtual mostrar"*.</span><span class="sxs-lookup"><span data-stu-id="87582-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="87582-475">O mundo virtual será mostrada e todos os outras hologramas ficará oculta.</span><span class="sxs-lookup"><span data-stu-id="87582-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="87582-476">Se você não vir o mundo virtual, certifique-se de que você está enfrentando uma superfície do mundo real.</span><span class="sxs-lookup"><span data-stu-id="87582-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="87582-477">Abordagem de dentro de 1 metro da holograma mundo virtual e comece a falar.</span><span class="sxs-lookup"><span data-stu-id="87582-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="87582-478">Agora há efeitos de áudio aplicados a sua opinião!</span><span class="sxs-lookup"><span data-stu-id="87582-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="87582-479">Ativar para fora o mundo virtual e observe como o efeito não é mais aplicado.</span><span class="sxs-lookup"><span data-stu-id="87582-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="87582-480">Digamos *"Mundo virtual ocultar"* para ocultar o mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="87582-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="87582-481">O mundo virtual ficará oculta e as hologramas previamente ocultas reaparecerá.</span><span class="sxs-lookup"><span data-stu-id="87582-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="87582-482">Fim</span><span class="sxs-lookup"><span data-stu-id="87582-482">The End</span></span>

<span data-ttu-id="87582-483">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="87582-483">Congratulations!</span></span> <span data-ttu-id="87582-484">Agora você concluiu **MR de 220 espacial: Som espacial**.</span><span class="sxs-lookup"><span data-stu-id="87582-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="87582-485">Ouça o mundo e dinamize suas experiências com som!</span><span class="sxs-lookup"><span data-stu-id="87582-485">Listen to the world and bring your experiences to life with sound!</span></span>

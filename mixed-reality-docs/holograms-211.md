---
title: Entrada MR 211-gesto
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de gesto.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, gesto
ms.openlocfilehash: d7a92e4b2f196d6d8b0ba0fe3ccb2aed87479ac1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434700"
---
>[!NOTE]
><span data-ttu-id="b546c-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b546c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b546c-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b546c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b546c-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b546c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b546c-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="b546c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b546c-108">[Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b546c-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="b546c-109">Entrada MR 211: gesto</span><span class="sxs-lookup"><span data-stu-id="b546c-109">MR Input 211: Gesture</span></span>

<span data-ttu-id="b546c-110">Os [gestos](gaze-and-commit.md#composite-gestures) desativam a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="b546c-110">[Gestures](gaze-and-commit.md#composite-gestures) turn user intention into action.</span></span> <span data-ttu-id="b546c-111">Com gestos, os usuários podem interagir com os hologramas.</span><span class="sxs-lookup"><span data-stu-id="b546c-111">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="b546c-112">Neste curso, veremos como acompanhar as mãos do usuário, responder a entrada do usuário e fornecer comentários para o usuário com base no estado e no local.</span><span class="sxs-lookup"><span data-stu-id="b546c-112">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="b546c-113">No [Sr basics 101](holograms-101.md), usamos um gesto simples de toque de ar para interagir com nossos hologramas.</span><span class="sxs-lookup"><span data-stu-id="b546c-113">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="b546c-114">Agora, vamos passar além do gesto de toque do ar e explorar novos conceitos para:</span><span class="sxs-lookup"><span data-stu-id="b546c-114">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="b546c-115">Detectar quando a mão do usuário está sendo acompanhada e fornecer comentários ao usuário.</span><span class="sxs-lookup"><span data-stu-id="b546c-115">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="b546c-116">Use um gesto de navegação para girar nossos hologramas.</span><span class="sxs-lookup"><span data-stu-id="b546c-116">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="b546c-117">Forneça comentários quando a mão do usuário estiver prestes a sair da exibição.</span><span class="sxs-lookup"><span data-stu-id="b546c-117">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="b546c-118">Use eventos de manipulação para permitir que os usuários movam os hologramas com suas mãos.</span><span class="sxs-lookup"><span data-stu-id="b546c-118">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="b546c-119">Neste curso, Vamos revisitar o **Explorador de modelos**de projeto do Unity, que criamos no [Sr Input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="b546c-119">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="b546c-120">Nosso amigo Astronaut está voltado a nos ajudar em nossa exploração desses novos conceitos de gesto.</span><span class="sxs-lookup"><span data-stu-id="b546c-120">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="b546c-121">Os vídeos inseridos em cada um dos capítulos abaixo foram registrados usando uma versão mais antiga do Unity e o kit de ferramentas do Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b546c-121">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="b546c-122">Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão desatualizados.</span><span class="sxs-lookup"><span data-stu-id="b546c-122">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="b546c-123">Os vídeos permanecem incluídos para posterity e porque os conceitos abordados ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="b546c-123">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="b546c-124">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="b546c-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b546c-125">Course</span><span class="sxs-lookup"><span data-stu-id="b546c-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b546c-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b546c-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b546c-127"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="b546c-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b546c-128">Entrada MR 211: gesto</span><span class="sxs-lookup"><span data-stu-id="b546c-128">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="b546c-129">✔️</span><span class="sxs-lookup"><span data-stu-id="b546c-129">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b546c-130">✔️</span><span class="sxs-lookup"><span data-stu-id="b546c-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="b546c-131">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="b546c-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b546c-132">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b546c-132">Prerequisites</span></span>

* <span data-ttu-id="b546c-133">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="b546c-133">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="b546c-134">Alguma capacidade C# básica de programação.</span><span class="sxs-lookup"><span data-stu-id="b546c-134">Some basic C# programming ability.</span></span>
* <span data-ttu-id="b546c-135">Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="b546c-135">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="b546c-136">Você deve ter concluído o [Sr Input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="b546c-136">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="b546c-137">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="b546c-137">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="b546c-138">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="b546c-138">Project files</span></span>

* <span data-ttu-id="b546c-139">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="b546c-139">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="b546c-140"> Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="b546c-140"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="b546c-141">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="b546c-141">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="b546c-142">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="b546c-142">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="b546c-143">Errata e observações</span><span class="sxs-lookup"><span data-stu-id="b546c-143">Errata and Notes</span></span>

* <span data-ttu-id="b546c-144">"Habilitar Apenas Meu Código" precisa ser desabilitado (*desmarcado*) no Visual Studio em ferramentas-> opções-> depuração para acessar os pontos de interrupção no código.</span><span class="sxs-lookup"><span data-stu-id="b546c-144">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="b546c-145">Capítulo 0-configuração do Unity</span><span class="sxs-lookup"><span data-stu-id="b546c-145">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="b546c-146">Instruções</span><span class="sxs-lookup"><span data-stu-id="b546c-146">Instructions</span></span>

1. <span data-ttu-id="b546c-147">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="b546c-147">Start Unity.</span></span>
2. <span data-ttu-id="b546c-148">Selecione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="b546c-148">Select **Open**.</span></span>
3. <span data-ttu-id="b546c-149">Navegue até a pasta de **gestos** que você cancelou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b546c-149">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="b546c-150">Localize e selecione o/pasta do **Gerenciador de modelos** de **inicialização** .</span><span class="sxs-lookup"><span data-stu-id="b546c-150">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="b546c-151">Clique no botão **Selecionar pasta** .</span><span class="sxs-lookup"><span data-stu-id="b546c-151">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="b546c-152">No painel **projeto** , expanda a pasta **cenas** .</span><span class="sxs-lookup"><span data-stu-id="b546c-152">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="b546c-153">Clique duas vezes em cena **ModelExplorer** para carregá-la no Unity.</span><span class="sxs-lookup"><span data-stu-id="b546c-153">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="b546c-154">Builds</span><span class="sxs-lookup"><span data-stu-id="b546c-154">Building</span></span>

1. <span data-ttu-id="b546c-155">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="b546c-155">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="b546c-156">Se **cenas/ModelExplorer** não estiver listado em **cenas em compilação**, clique em **Adicionar cenas abertas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="b546c-156">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="b546c-157">Se você estiver desenvolvendo especificamente para o HoloLens, defina o **dispositivo de destino** para o **hololens**.</span><span class="sxs-lookup"><span data-stu-id="b546c-157">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="b546c-158">Caso contrário, deixe em **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="b546c-158">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="b546c-159">Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="b546c-159">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="b546c-160">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="b546c-160">Click **Build**.</span></span>
6. <span data-ttu-id="b546c-161">Crie uma **nova pasta** chamada "app".</span><span class="sxs-lookup"><span data-stu-id="b546c-161">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="b546c-162">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="b546c-162">Single click the **App** folder.</span></span>
8. <span data-ttu-id="b546c-163">Pressione **Selecionar pasta** e o Unity começará a compilar o projeto para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b546c-163">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="b546c-164">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="b546c-164">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="b546c-165">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="b546c-165">Open the **App** folder.</span></span>
2. <span data-ttu-id="b546c-166">Abra a **solução ModelExplorer do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b546c-166">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="b546c-167">Se estiver implantando no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="b546c-167">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="b546c-168">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="b546c-168">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="b546c-169">Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="b546c-169">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="b546c-170">Insira **o endereço IP do dispositivo de HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)** .</span><span class="sxs-lookup"><span data-stu-id="b546c-170">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="b546c-171">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="b546c-171">Click **Select**.</span></span> <span data-ttu-id="b546c-172">Se você não souber o endereço IP do dispositivo, examine **configurações > rede & Internet > opções avançadas**.</span><span class="sxs-lookup"><span data-stu-id="b546c-172">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="b546c-173">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b546c-173">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="b546c-174">Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="b546c-174">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="b546c-175">Quando o aplicativo tiver sido implantado, ignore o **Fitbox** com um **gesto de seleção**.</span><span class="sxs-lookup"><span data-stu-id="b546c-175">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="b546c-176">Se estiver implantando em um headset de imersão:</span><span class="sxs-lookup"><span data-stu-id="b546c-176">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="b546c-177">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="b546c-177">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="b546c-178">Verifique se o destino de implantação está definido como **computador local**.</span><span class="sxs-lookup"><span data-stu-id="b546c-178">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="b546c-179">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b546c-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="b546c-180">Quando o aplicativo tiver sido implantado, ignore o **Fitbox** puxando o gatilho em um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="b546c-180">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="b546c-181">Você pode observar alguns erros vermelhos no painel de erros do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b546c-181">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="b546c-182">É seguro ignorá-los.</span><span class="sxs-lookup"><span data-stu-id="b546c-182">It is safe to ignore them.</span></span> <span data-ttu-id="b546c-183">Alterne para o painel saída para exibir o andamento real da compilação.</span><span class="sxs-lookup"><span data-stu-id="b546c-183">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="b546c-184">Os erros no painel de saída exigirão que você faça uma correção (geralmente elas são causadas por um erro em um script).</span><span class="sxs-lookup"><span data-stu-id="b546c-184">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="b546c-185">Capítulo 1-comentários detectados</span><span class="sxs-lookup"><span data-stu-id="b546c-185">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="b546c-186">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b546c-186">Objectives</span></span>

* <span data-ttu-id="b546c-187">Assine os eventos de acompanhamento do Hand.</span><span class="sxs-lookup"><span data-stu-id="b546c-187">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="b546c-188">Use comentários do cursor para mostrar os usuários quando uma mão estiver sendo controlada.</span><span class="sxs-lookup"><span data-stu-id="b546c-188">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="b546c-189">No HoloLens 2, as mãos detectadas são acionadas sempre que as mãos ficam visíveis (não apenas quando um dedo está apontando para cima).</span><span class="sxs-lookup"><span data-stu-id="b546c-189">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="b546c-190">Instruções</span><span class="sxs-lookup"><span data-stu-id="b546c-190">Instructions</span></span>

* <span data-ttu-id="b546c-191">No painel **hierarquia** , expanda o objeto **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="b546c-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="b546c-192">Procure e selecione o objeto **GesturesInput** .</span><span class="sxs-lookup"><span data-stu-id="b546c-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="b546c-193">O script **InteractionInputSource.cs** executa estas etapas:</span><span class="sxs-lookup"><span data-stu-id="b546c-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="b546c-194">Assina os eventos InteractionSourceDetected e InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="b546c-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="b546c-195">Define o estado HandDetected.</span><span class="sxs-lookup"><span data-stu-id="b546c-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="b546c-196">Cancela a assinatura dos eventos InteractionSourceDetected e InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="b546c-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="b546c-197">Em seguida, atualizaremos nosso cursor da [entrada do sr 210](holograms-210.md) em um que mostre os comentários, dependendo das ações do usuário.</span><span class="sxs-lookup"><span data-stu-id="b546c-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="b546c-198">No painel **hierarquia** , selecione o objeto de **cursor** e exclua-o.</span><span class="sxs-lookup"><span data-stu-id="b546c-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="b546c-199">No painel **projeto** , pesquise **CursorWithFeedback** e arraste-o para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="b546c-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="b546c-200">Clique em **InputManager** no painel **hierarquia** e arraste o objeto **CursorWithFeedback** da **hierarquia** para o campo de **cursor** do **SimpleSinglePointerSelector**do InputManager, na parte inferior da **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="b546c-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="b546c-201">Clique em **CursorWithFeedback** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="b546c-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="b546c-202">No painel **Inspetor** , expanda **dados de estado do cursor** no script de **cursor do objeto** .</span><span class="sxs-lookup"><span data-stu-id="b546c-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="b546c-203">Os **dados de estado do cursor** funcionam da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b546c-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="b546c-204">Qualquer **estado** de observação significa que nenhuma mão é detectada e o usuário está simplesmente olhando.</span><span class="sxs-lookup"><span data-stu-id="b546c-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="b546c-205">Qualquer estado de **interação** significa que uma mão ou um controlador é detectado.</span><span class="sxs-lookup"><span data-stu-id="b546c-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="b546c-206">Qualquer estado de **foco** significa que o usuário está observando um holograma.</span><span class="sxs-lookup"><span data-stu-id="b546c-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="b546c-207">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="b546c-207">Build and Deploy</span></span>

* <span data-ttu-id="b546c-208">No Unity, use **as configurações de Build de > de arquivo** para recompilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b546c-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="b546c-209">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="b546c-209">Open the **App** folder.</span></span>
* <span data-ttu-id="b546c-210">Se ainda não estiver aberto, abra a **solução ModelExplorer Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b546c-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="b546c-211">(Se você já criou/implantou esse projeto no Visual Studio durante a instalação, poderá abrir essa instância do VS e clicar em ' recarregar tudo ' quando solicitado).</span><span class="sxs-lookup"><span data-stu-id="b546c-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="b546c-212">No Visual Studio, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b546c-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="b546c-213">Depois que o aplicativo for implantado no HoloLens, ignore o fitbox usando o gesto de toque do ar.</span><span class="sxs-lookup"><span data-stu-id="b546c-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="b546c-214">Mova sua mão para a exibição e aponte o dedo para o céu até o início do controle.</span><span class="sxs-lookup"><span data-stu-id="b546c-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="b546c-215">Mova sua mão para a esquerda, para a direita, para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="b546c-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="b546c-216">Observe como o cursor é alterado quando a sua mão é detectada e perdida da exibição.</span><span class="sxs-lookup"><span data-stu-id="b546c-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="b546c-217">Se você estiver em um headset de imersão, precisará se conectar e desconectar seu controlador.</span><span class="sxs-lookup"><span data-stu-id="b546c-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="b546c-218">Esse comentário se torna menos interessante em um dispositivo de imersão, pois um controlador conectado sempre será "disponível".</span><span class="sxs-lookup"><span data-stu-id="b546c-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="b546c-219">Capítulo 2-navegação</span><span class="sxs-lookup"><span data-stu-id="b546c-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="b546c-220">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b546c-220">Objectives</span></span>

* <span data-ttu-id="b546c-221">Use eventos de gesto de navegação para girar o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="b546c-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="b546c-222">Instruções</span><span class="sxs-lookup"><span data-stu-id="b546c-222">Instructions</span></span>

<span data-ttu-id="b546c-223">Para usar gestos de navegação em nosso aplicativo, vamos editar **GestureAction.cs** para girar objetos quando ocorrer o gesto de navegação.</span><span class="sxs-lookup"><span data-stu-id="b546c-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="b546c-224">Além disso, adicionaremos comentários ao cursor para exibir quando a navegação estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="b546c-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="b546c-225">No painel **hierarquia** , expanda **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="b546c-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="b546c-226">Na pasta **hologramas** , localize o ativo **ScrollFeedback** .</span><span class="sxs-lookup"><span data-stu-id="b546c-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="b546c-227">Arraste e solte o **ScrollFeedback** pré-fabricado no **CursorWithFeedback** gameobject na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="b546c-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="b546c-228">Clique em **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="b546c-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="b546c-229">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="b546c-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="b546c-230">No menu, digite na caixa de pesquisa **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="b546c-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="b546c-231">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-231">Select the search result.</span></span>
7. <span data-ttu-id="b546c-232">Arraste e solte o objeto **ScrollFeedback** da **hierarquia** na propriedade de **objeto de jogo scroll detected Game** no componente de **comentários do cursor** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="b546c-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="b546c-233">No painel **hierarquia** , selecione o objeto **AstroMan** .</span><span class="sxs-lookup"><span data-stu-id="b546c-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="b546c-234">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="b546c-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="b546c-235">No menu, digite a **ação de gesto**de caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="b546c-236">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-236">Select the search result.</span></span>

<span data-ttu-id="b546c-237">Em seguida, abra **GestureAction.cs** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b546c-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="b546c-238">Em código exercício 2. c, edite o script para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b546c-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="b546c-239">**Gire o objeto AstroMan** sempre que um gesto de navegação for executado.</span><span class="sxs-lookup"><span data-stu-id="b546c-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="b546c-240">Calcule o **rotationFactor** para controlar a quantidade de rotação aplicada ao objeto.</span><span class="sxs-lookup"><span data-stu-id="b546c-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="b546c-241">**Gire o objeto** ao lado do eixo y quando o usuário move sua mão para a esquerda ou para a direita.</span><span class="sxs-lookup"><span data-stu-id="b546c-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="b546c-242">Conclua os exercícios de codificação 2. c no script ou substitua o código pela solução concluída abaixo:</span><span class="sxs-lookup"><span data-stu-id="b546c-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="b546c-243">Você observará que os outros eventos de navegação já estão preenchidos com algumas informações.</span><span class="sxs-lookup"><span data-stu-id="b546c-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="b546c-244">Enviamos o gameobject para a pilha modal do InputSystem's do kit de ferramentas, para que o usuário não precise manter o foco no Astronaut depois que a rotação for iniciada.</span><span class="sxs-lookup"><span data-stu-id="b546c-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="b546c-245">De modo correspondente, vamos desencaixar o gameobject da pilha quando o gesto for concluído.</span><span class="sxs-lookup"><span data-stu-id="b546c-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="b546c-246">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="b546c-246">Build and Deploy</span></span>

1. <span data-ttu-id="b546c-247">Recompile o aplicativo no Unity e, em seguida, compile e implante a partir do Visual Studio para executá-lo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b546c-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="b546c-248">Olhar na Astronaut, duas setas devem aparecer em ambos os lados do cursor.</span><span class="sxs-lookup"><span data-stu-id="b546c-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="b546c-249">Esse novo visual indica que o Astronaut pode ser girado.</span><span class="sxs-lookup"><span data-stu-id="b546c-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="b546c-250">Coloque sua mão na posição pronta (o dedo aponta para o céu) para que o HoloLens comece a controlar sua mão.</span><span class="sxs-lookup"><span data-stu-id="b546c-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="b546c-251">Para girar o Astronaut, reduza o dedo do seu índice para uma posição de pinçagem e, em seguida, mova a mão para a esquerda ou para a direita para disparar o gesto de NavigationX.</span><span class="sxs-lookup"><span data-stu-id="b546c-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="b546c-252">Capítulo 3-orientação</span><span class="sxs-lookup"><span data-stu-id="b546c-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="b546c-253">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b546c-253">Objectives</span></span>

* <span data-ttu-id="b546c-254">Use a **Pontuação de orientação à mão** para ajudar a prever quando o rastreamento à mão será perdido.</span><span class="sxs-lookup"><span data-stu-id="b546c-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="b546c-255">Forneça **comentários sobre o cursor** para mostrar quando a mão do usuário se aproximar da borda da exibição da câmera.</span><span class="sxs-lookup"><span data-stu-id="b546c-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="b546c-256">Instruções</span><span class="sxs-lookup"><span data-stu-id="b546c-256">Instructions</span></span>

1. <span data-ttu-id="b546c-257">No painel **hierarquia** , selecione o objeto **CursorWithFeedback** .</span><span class="sxs-lookup"><span data-stu-id="b546c-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="b546c-258">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="b546c-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="b546c-259">No menu, digite as **orientações**da caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="b546c-260">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-260">Select the search result.</span></span>
4. <span data-ttu-id="b546c-261">Na pasta **hologramas** do painel **projeto** , localize o ativo **HandGuidanceFeedback** .</span><span class="sxs-lookup"><span data-stu-id="b546c-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="b546c-262">Arraste e solte o ativo **HandGuidanceFeedback** na propriedade **indicador de orientação à mão** no painel **Inspetor** .</span><span class="sxs-lookup"><span data-stu-id="b546c-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="b546c-263">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="b546c-263">Build and Deploy</span></span>

* <span data-ttu-id="b546c-264">Recompile o aplicativo no Unity e, em seguida, compile e implante a partir do Visual Studio para experimentar o aplicativo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b546c-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="b546c-265">Traga sua mão para a exibição e aumente o seu índice para ser acompanhado.</span><span class="sxs-lookup"><span data-stu-id="b546c-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="b546c-266">Comece a girar o Astronaut com o gesto de navegação (Aperte o dedo do índice e o polegar juntos).</span><span class="sxs-lookup"><span data-stu-id="b546c-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="b546c-267">Mova a mão para a extrema esquerda, para a direita, para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="b546c-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="b546c-268">À medida que a sua mão se aproximar da borda do quadro do gesto, uma seta deverá aparecer ao lado do cursor para avisá-lo de que o acompanhamento manual será perdido.</span><span class="sxs-lookup"><span data-stu-id="b546c-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="b546c-269">A seta indica em qual direção mover sua mão para evitar que o rastreamento seja perdido.</span><span class="sxs-lookup"><span data-stu-id="b546c-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="b546c-270">Capítulo 4-manipulação</span><span class="sxs-lookup"><span data-stu-id="b546c-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="b546c-271">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b546c-271">Objectives</span></span>

* <span data-ttu-id="b546c-272">Use eventos de manipulação para mover o Astronaut com suas mãos.</span><span class="sxs-lookup"><span data-stu-id="b546c-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="b546c-273">Forneça comentários sobre o cursor para permitir que o usuário saiba quando a manipulação pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="b546c-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="b546c-274">Instruções</span><span class="sxs-lookup"><span data-stu-id="b546c-274">Instructions</span></span>

<span data-ttu-id="b546c-275">GestureManager.cs e AstronautManager.cs nos permitirão fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b546c-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="b546c-276">Use a palavra-chave de fala "**move Astronaut**" para habilitar gestos de **manipulação** e "**girar Astronaut**" para desabilitá-los.</span><span class="sxs-lookup"><span data-stu-id="b546c-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="b546c-277">Alterne para responder ao **reconhecedor de gestos de manipulação**.</span><span class="sxs-lookup"><span data-stu-id="b546c-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="b546c-278">Vamos começar.</span><span class="sxs-lookup"><span data-stu-id="b546c-278">Let's get started.</span></span>

1. <span data-ttu-id="b546c-279">No painel **hierarquia** , crie um novo gameobject vazio.</span><span class="sxs-lookup"><span data-stu-id="b546c-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="b546c-280">Nomeie-o como "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="b546c-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="b546c-281">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="b546c-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="b546c-282">No menu, digite na caixa de pesquisa **Astronaut Manager**.</span><span class="sxs-lookup"><span data-stu-id="b546c-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="b546c-283">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-283">Select the search result.</span></span>
4. <span data-ttu-id="b546c-284">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="b546c-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="b546c-285">No menu, digite a caixa de pesquisa **fonte de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="b546c-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="b546c-286">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-286">Select the search result.</span></span>

<span data-ttu-id="b546c-287">Agora, vamos adicionar os comandos de fala necessários para controlar o estado de interação do Astronaut.</span><span class="sxs-lookup"><span data-stu-id="b546c-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="b546c-288">Expanda a seção **palavras-chave** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="b546c-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="b546c-289">Clique na **+** no lado direito para adicionar uma nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b546c-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="b546c-290">Digite a palavra-chave como **mover Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="b546c-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="b546c-291">Fique à vontade para adicionar um atalho de chave, se desejado.</span><span class="sxs-lookup"><span data-stu-id="b546c-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="b546c-292">Clique na **+** no lado direito para adicionar uma nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b546c-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="b546c-293">Digite a palavra-chave como **girar Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="b546c-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="b546c-294">Fique à vontade para adicionar um atalho de chave, se desejado.</span><span class="sxs-lookup"><span data-stu-id="b546c-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="b546c-295">O código de manipulador correspondente pode ser encontrado em **GestureAction.cs**, no manipulador **ISpeechHandler. OnSpeechKeywordRecognized** .</span><span class="sxs-lookup"><span data-stu-id="b546c-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Como configurar a fonte de entrada de fala para o capítulo 4](images/holograms211-speech.png)

<span data-ttu-id="b546c-297">Em seguida, vamos configurar os comentários de manipulação no cursor.</span><span class="sxs-lookup"><span data-stu-id="b546c-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="b546c-298">Na pasta **hologramas** do painel **projeto** , localize o ativo **PathingFeedback** .</span><span class="sxs-lookup"><span data-stu-id="b546c-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="b546c-299">Arraste e solte o **PathingFeedback** pré-fabricado no objeto **CursorWithFeedback** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="b546c-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="b546c-300">No painel **hierarquia** , clique em **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="b546c-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="b546c-301">Arraste e solte o objeto **PathingFeedback** da **hierarquia** para a propriedade **demarcar objeto de jogo detectado** no componente de **comentários do cursor** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="b546c-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="b546c-302">Agora, precisamos adicionar código a **GestureAction.cs** para habilitar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b546c-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="b546c-303">Adicione o código à função **IManipulationHandler. OnManipulationUpdated** , que moverá o Astronaut quando um gesto de **manipulação** for detectado.</span><span class="sxs-lookup"><span data-stu-id="b546c-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="b546c-304">Calcule o **vetor de movimento** para determinar onde o Astronaut deve ser movido com base na posição da mão.</span><span class="sxs-lookup"><span data-stu-id="b546c-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="b546c-305">**Mova** o Astronaut para a nova posição.</span><span class="sxs-lookup"><span data-stu-id="b546c-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="b546c-306">Conclua a codificação exercício 4. a no **GestureAction.cs**ou use nossa solução concluída abaixo:</span><span class="sxs-lookup"><span data-stu-id="b546c-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="b546c-307">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="b546c-307">Build and Deploy</span></span>

* <span data-ttu-id="b546c-308">Recompile no Unity e, em seguida, compile e implante a partir do Visual Studio para executar o aplicativo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b546c-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="b546c-309">Mova sua mão na frente do HoloLens e aumente o dedo do índice para que ele possa ser acompanhado.</span><span class="sxs-lookup"><span data-stu-id="b546c-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="b546c-310">Focalize o cursor sobre o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="b546c-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="b546c-311">Diga ' mover Astronaut ' para mover o Astronaut com um gesto de manipulação.</span><span class="sxs-lookup"><span data-stu-id="b546c-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="b546c-312">Quatro setas devem aparecer ao contrário do cursor para indicar que o programa agora responderá a eventos de manipulação.</span><span class="sxs-lookup"><span data-stu-id="b546c-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="b546c-313">Reduza o seu dedo de índice para o polegar e mantenha-os esmagados juntos.</span><span class="sxs-lookup"><span data-stu-id="b546c-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="b546c-314">À medida que você mudar de lado, o Astronaut se moverá também (isso é manipulação).</span><span class="sxs-lookup"><span data-stu-id="b546c-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="b546c-315">Gere o seu índice para parar de manipular o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="b546c-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="b546c-316">Observação: se você não disser ' mover Astronaut ' antes de mover sua mão, o gesto de navegação será usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b546c-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="b546c-317">Diga ' Rotate Astronaut ' para retornar ao estado de rotatable.</span><span class="sxs-lookup"><span data-stu-id="b546c-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="b546c-318">Capítulo 5 – expansão de modelo</span><span class="sxs-lookup"><span data-stu-id="b546c-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="b546c-319">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b546c-319">Objectives</span></span>

* <span data-ttu-id="b546c-320">Expanda o modelo Astronaut em várias partes menores com as quais o usuário pode interagir.</span><span class="sxs-lookup"><span data-stu-id="b546c-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="b546c-321">Mova cada peça individualmente usando gestos de navegação e manipulação.</span><span class="sxs-lookup"><span data-stu-id="b546c-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="b546c-322">Instruções</span><span class="sxs-lookup"><span data-stu-id="b546c-322">Instructions</span></span>

<span data-ttu-id="b546c-323">Nesta seção, realizaremos as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="b546c-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="b546c-324">Adicione uma nova palavra-chave "**Expand Model**" para expandir o modelo Astronaut.</span><span class="sxs-lookup"><span data-stu-id="b546c-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="b546c-325">Adicione uma nova palavra-chave "**Redefinir modelo**" para retornar o modelo ao seu formulário original.</span><span class="sxs-lookup"><span data-stu-id="b546c-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="b546c-326">Vamos fazer isso adicionando mais duas palavras-chave à fonte de entrada de fala do capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="b546c-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="b546c-327">Também demonstraremos outra maneira de lidar com eventos de reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="b546c-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="b546c-328">Clique em voltar em **AstronautManager** no **Inspetor** e expanda a seção **palavras-chave** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="b546c-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="b546c-329">Clique na **+** no lado direito para adicionar uma nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b546c-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="b546c-330">Digite a palavra-chave como **modelo de expansão**.</span><span class="sxs-lookup"><span data-stu-id="b546c-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="b546c-331">Fique à vontade para adicionar um atalho de chave, se desejado.</span><span class="sxs-lookup"><span data-stu-id="b546c-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="b546c-332">Clique na **+** no lado direito para adicionar uma nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b546c-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="b546c-333">Digite a palavra-chave como **modelo de redefinição**.</span><span class="sxs-lookup"><span data-stu-id="b546c-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="b546c-334">Fique à vontade para adicionar um atalho de chave, se desejado.</span><span class="sxs-lookup"><span data-stu-id="b546c-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="b546c-335">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="b546c-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="b546c-336">No menu, digite o manipulador de entrada de **fala**da caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="b546c-337">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b546c-337">Select the search result.</span></span>
8. <span data-ttu-id="b546c-338">Verifique **se o ouvinte global**, pois queremos que esses comandos funcionem independentemente do gameobject que estamos concentrando.</span><span class="sxs-lookup"><span data-stu-id="b546c-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="b546c-339">Clique no botão **+** e selecione **expandir modelo** na lista suspensa de palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="b546c-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="b546c-340">Clique na **+** em resposta e arraste o **AstronautManager** da **hierarquia** para o campo **nenhum (objeto)** .</span><span class="sxs-lookup"><span data-stu-id="b546c-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="b546c-341">Agora, clique no menu suspenso **sem função** , selecione **AstronautManager**e **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="b546c-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="b546c-342">Clique no botão **+** do manipulador de entrada de fala e selecione **Redefinir modelo** na lista suspensa de palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="b546c-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="b546c-343">Clique na **+** em resposta e arraste o **AstronautManager** da **hierarquia** para o campo **nenhum (objeto)** .</span><span class="sxs-lookup"><span data-stu-id="b546c-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="b546c-344">Agora, clique no menu suspenso **sem função** , selecione **AstronautManager**e **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="b546c-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Como configurar a fonte de entrada e o manipulador de fala para o capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="b546c-346">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="b546c-346">Build and Deploy</span></span>

* <span data-ttu-id="b546c-347">Experimente!</span><span class="sxs-lookup"><span data-stu-id="b546c-347">Try it!</span></span> <span data-ttu-id="b546c-348">Crie e implante o aplicativo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b546c-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="b546c-349">Digamos **expandir modelo** para ver o modelo de Astronaut expandido.</span><span class="sxs-lookup"><span data-stu-id="b546c-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="b546c-350">Use a **navegação** para girar partes individuais do naipe Astronaut.</span><span class="sxs-lookup"><span data-stu-id="b546c-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="b546c-351">Digamos **mover Astronaut** e, em seguida, usar a **manipulação** para mover partes individuais do naipe de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="b546c-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="b546c-352">Digamos **girar Astronaut** para girar as peças novamente.</span><span class="sxs-lookup"><span data-stu-id="b546c-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="b546c-353">Digamos que **redefina o modelo** para retornar o Astronaut para seu formato original.</span><span class="sxs-lookup"><span data-stu-id="b546c-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="b546c-354">Fim</span><span class="sxs-lookup"><span data-stu-id="b546c-354">The End</span></span>

<span data-ttu-id="b546c-355">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="b546c-355">Congratulations!</span></span> <span data-ttu-id="b546c-356">Agora você concluiu o **Sr Input 211: gesto**.</span><span class="sxs-lookup"><span data-stu-id="b546c-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="b546c-357">Você sabe como detectar e responder a eventos de rastreamento, navegação e manipulação à mão.</span><span class="sxs-lookup"><span data-stu-id="b546c-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="b546c-358">Você entende a diferença entre gestos de navegação e manipulação.</span><span class="sxs-lookup"><span data-stu-id="b546c-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="b546c-359">Você sabe como alterar o cursor para fornecer comentários visuais para quando uma mão é detectada, quando uma mão está prestes a ser perdida e para quando um objeto dá suporte a interações diferentes (navegação vs.).</span><span class="sxs-lookup"><span data-stu-id="b546c-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>

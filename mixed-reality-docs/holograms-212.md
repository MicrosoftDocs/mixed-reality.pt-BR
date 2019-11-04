---
title: Entrada MR 212-Voice
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, voz
ms.openlocfilehash: 9db503ea4c7db9a3eb272ad9663024ca3a407dda
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434593"
---
>[!NOTE]
><span data-ttu-id="d5bf7-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d5bf7-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d5bf7-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d5bf7-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d5bf7-108">[Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="d5bf7-109">Entrada MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="d5bf7-109">MR Input 212: Voice</span></span>

<span data-ttu-id="d5bf7-110">A [entrada de voz](voice-input.md) nos dá outra maneira de interagir com nossos hologramas.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-110">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="d5bf7-111">Os comandos de voz funcionam de maneira muito natural e fácil.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="d5bf7-112">Crie seus comandos de voz para que eles sejam:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="d5bf7-113">Natural</span><span class="sxs-lookup"><span data-stu-id="d5bf7-113">Natural</span></span>
* <span data-ttu-id="d5bf7-114">Fácil de lembrar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-114">Easy to remember</span></span>
* <span data-ttu-id="d5bf7-115">Contexto apropriado</span><span class="sxs-lookup"><span data-stu-id="d5bf7-115">Context appropriate</span></span>
* <span data-ttu-id="d5bf7-116">Suficientemente diferente de outras opções dentro do mesmo contexto</span><span class="sxs-lookup"><span data-stu-id="d5bf7-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="d5bf7-117">No [Sr basics 101](holograms-101.md), usamos o KeywordRecognizer para criar dois comandos simples de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-117">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="d5bf7-118">No Sr Input 212, vamos nos aprofundar e aprender como:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="d5bf7-119">Crie comandos de voz que são otimizados para o mecanismo de fala do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="d5bf7-120">Faça o usuário reconhecer quais comandos de voz estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="d5bf7-121">Confirme que ouvimos o comando de voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="d5bf7-122">Entenda o que o usuário está dizendo, usando um reconhecedor de ditado.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="d5bf7-123">Use um reconhecedor de gramática para escutar comandos com base em um arquivo de especificação de gramática de reconhecimento de fala ou SRGS.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="d5bf7-124">Neste curso, revisitaremos o Gerenciador de modelos, que criamos no [Sr input 210](holograms-210.md) e no [Sr Input 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="d5bf7-125">Os vídeos inseridos em cada um dos capítulos abaixo foram registrados usando uma versão mais antiga do Unity e o kit de ferramentas do Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="d5bf7-126">Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão desatualizados.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="d5bf7-127">Os vídeos permanecem incluídos para posterity e porque os conceitos abordados ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="d5bf7-128">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="d5bf7-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d5bf7-129">Course</span><span class="sxs-lookup"><span data-stu-id="d5bf7-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d5bf7-130"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d5bf7-130"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d5bf7-131"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="d5bf7-131"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d5bf7-132">Entrada MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="d5bf7-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="d5bf7-133">✔️</span><span class="sxs-lookup"><span data-stu-id="d5bf7-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d5bf7-134">✔️</span><span class="sxs-lookup"><span data-stu-id="d5bf7-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="d5bf7-135">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d5bf7-136">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d5bf7-136">Prerequisites</span></span>

* <span data-ttu-id="d5bf7-137">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-137">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="d5bf7-138">Alguma capacidade C# básica de programação.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="d5bf7-139">Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-139">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="d5bf7-140">Você deve ter concluído o [Sr Input 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="d5bf7-141">Você deve ter concluído o [Sr Input 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="d5bf7-142">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-142">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="d5bf7-143">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="d5bf7-143">Project files</span></span>

* <span data-ttu-id="d5bf7-144">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="d5bf7-145">Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="d5bf7-146">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="d5bf7-147">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="d5bf7-148">Errata e observações</span><span class="sxs-lookup"><span data-stu-id="d5bf7-148">Errata and Notes</span></span>

* <span data-ttu-id="d5bf7-149">"Habilitar Apenas Meu Código" precisa ser desabilitado (*desmarcado*) no Visual Studio em ferramentas-> opções-> depuração para acessar os pontos de interrupção no código.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-149">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="d5bf7-150">Configuração do Unity</span><span class="sxs-lookup"><span data-stu-id="d5bf7-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="d5bf7-151">Instruções</span><span class="sxs-lookup"><span data-stu-id="d5bf7-151">Instructions</span></span>

1. <span data-ttu-id="d5bf7-152">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-152">Start Unity.</span></span>
2. <span data-ttu-id="d5bf7-153">Selecione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-153">Select **Open**.</span></span>
3. <span data-ttu-id="d5bf7-154">Navegue até a pasta **HolographicAcademy-hologramas-212-Voice** que você cancelou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="d5bf7-155">Localize e selecione o/pasta do **Gerenciador de modelos** de **inicialização** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="d5bf7-156">Clique no botão **Selecionar pasta** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="d5bf7-157">No painel **projeto** , expanda a pasta **cenas** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="d5bf7-158">Clique duas vezes em cena **ModelExplorer** para carregá-la no Unity.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="d5bf7-159">Builds</span><span class="sxs-lookup"><span data-stu-id="d5bf7-159">Building</span></span>

1. <span data-ttu-id="d5bf7-160">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-160">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="d5bf7-161">Se **cenas/ModelExplorer** não estiver listado em **cenas em compilação**, clique em **Adicionar cenas abertas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="d5bf7-162">Se você estiver desenvolvendo especificamente para o HoloLens, defina o **dispositivo de destino** para o **hololens**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="d5bf7-163">Caso contrário, deixe em **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-163">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="d5bf7-164">Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="d5bf7-165">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-165">Click **Build**.</span></span>
6. <span data-ttu-id="d5bf7-166">Crie uma **nova pasta** chamada "app".</span><span class="sxs-lookup"><span data-stu-id="d5bf7-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="d5bf7-167">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="d5bf7-168">Pressione **Selecionar pasta** e o Unity começará a compilar o projeto para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="d5bf7-169">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="d5bf7-170">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="d5bf7-171">Abra a **solução ModelExplorer do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-171">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="d5bf7-172">Se estiver implantando no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="d5bf7-173">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="d5bf7-174">Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="d5bf7-175">Insira **o endereço IP do dispositivo de HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="d5bf7-176">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-176">Click **Select**.</span></span> <span data-ttu-id="d5bf7-177">Se você não souber o endereço IP do dispositivo, examine **configurações > rede & Internet > opções avançadas**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="d5bf7-178">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="d5bf7-179">Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="d5bf7-180">Quando o aplicativo tiver sido implantado, ignore o **Fitbox** com um **gesto de seleção**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="d5bf7-181">Se estiver implantando em um headset de imersão:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="d5bf7-182">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="d5bf7-183">Verifique se o destino de implantação está definido como **computador local**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-183">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="d5bf7-184">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="d5bf7-185">Quando o aplicativo tiver sido implantado, ignore o **Fitbox** puxando o gatilho em um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="d5bf7-186">Você pode observar alguns erros vermelhos no painel de erros do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="d5bf7-187">É seguro ignorá-los.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-187">It is safe to ignore them.</span></span> <span data-ttu-id="d5bf7-188">Alterne para o painel saída para exibir o andamento real da compilação.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="d5bf7-189">Os erros no painel de saída exigirão que você faça uma correção (geralmente elas são causadas por um erro em um script).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="d5bf7-190">Capítulo 1-reconhecimento</span><span class="sxs-lookup"><span data-stu-id="d5bf7-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="d5bf7-191">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d5bf7-191">Objectives</span></span>

* <span data-ttu-id="d5bf7-192">Aprenda sobre o **dos e não** sobre o design de comando de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="d5bf7-193">Use **KeywordRecognizer** para adicionar comandos de voz baseados em olhar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="d5bf7-194">Fazer com que os usuários reconheçam comandos de voz usando **comentários**do cursor.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-194">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="d5bf7-195">Design de comando de voz</span><span class="sxs-lookup"><span data-stu-id="d5bf7-195">Voice Command Design</span></span>

<span data-ttu-id="d5bf7-196">Neste capítulo, você aprenderá a criar comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="d5bf7-197">Ao criar comandos de voz:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="d5bf7-198">DO</span><span class="sxs-lookup"><span data-stu-id="d5bf7-198">DO</span></span>

* <span data-ttu-id="d5bf7-199">Crie comandos concisos.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-199">Create concise commands.</span></span> <span data-ttu-id="d5bf7-200">Você não deseja usar *"reproduzir o vídeo selecionado atualmente"* , porque esse comando não é conciso e seria facilmente esquecido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-200">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="d5bf7-201">Em vez disso, você deve usar: *"reproduzir vídeo"* , porque ele é conciso e tem várias sílabas.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-201">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="d5bf7-202">Use um vocabulário simples.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-202">Use a simple vocabulary.</span></span> <span data-ttu-id="d5bf7-203">Sempre tente usar palavras e frases comuns que sejam fáceis para o usuário descobrir e se lembrar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="d5bf7-204">Por exemplo, se o seu aplicativo tiver um objeto note que pudesse ser exibido ou oculto da exibição, você não usará o comando *"show letreiro"* , porque "letreiro" é um termo raramente usado.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="d5bf7-205">Em vez disso, você usaria o comando: *"mostrar nota"* , para revelar a nota em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-205">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="d5bf7-206">Ser consistente.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-206">Be consistent.</span></span> <span data-ttu-id="d5bf7-207">Os comandos de voz devem ser mantidos consistentes em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="d5bf7-208">Imagine que você tenha duas cenas em seu aplicativo e que ambas as cenas contenham um botão para fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="d5bf7-209">Se a primeira cena usou o comando *"Exit"* para disparar o botão, mas a segunda cena usou o comando *"Close app"* , o usuário vai ficar muito confuso.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="d5bf7-210">Se a mesma funcionalidade persistir em vários bastidores, o mesmo comando de voz deverá ser usado para dispará-lo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="d5bf7-211">Não</span><span class="sxs-lookup"><span data-stu-id="d5bf7-211">DON'T</span></span>

* <span data-ttu-id="d5bf7-212">Use comandos de sílaba única.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-212">Use single syllable commands.</span></span> <span data-ttu-id="d5bf7-213">Por exemplo, se você estivesse criando um comando de voz para reproduzir um vídeo, evite usar o comando simples *"Play"* , pois ele é apenas uma única sílaba e pode ser facilmente perdido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="d5bf7-214">Em vez disso, você deve usar: *"reproduzir vídeo"* , porque ele é conciso e tem várias sílabas.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-214">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="d5bf7-215">Use comandos do sistema.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-215">Use system commands.</span></span> <span data-ttu-id="d5bf7-216">O comando *"Select"* é reservado pelo sistema para disparar um evento TAP para o objeto atualmente focalizado.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="d5bf7-217">Não use novamente o comando *"Select"* em uma palavra-chave ou frase, pois ele pode não funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="d5bf7-218">Por exemplo, se o comando de voz para selecionar um cubo em seu aplicativo era *"Selecionar Cubo"* , mas o usuário estava olhando para uma esfera quando estivessem o comando, então a esfera seria selecionada em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-218">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="d5bf7-219">De forma semelhante, os comandos da barra de aplicativos estão habilitados para voz</span><span class="sxs-lookup"><span data-stu-id="d5bf7-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="d5bf7-220">Não use os seguintes comandos de fala em sua exibição do CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="d5bf7-221">Voltar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-221">Go Back</span></span>
    2. <span data-ttu-id="d5bf7-222">Ferramenta Scroll</span><span class="sxs-lookup"><span data-stu-id="d5bf7-222">Scroll Tool</span></span>
    3. <span data-ttu-id="d5bf7-223">Ferramenta de zoom</span><span class="sxs-lookup"><span data-stu-id="d5bf7-223">Zoom Tool</span></span>
    4. <span data-ttu-id="d5bf7-224">Ferramenta de arrastar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-224">Drag Tool</span></span>
    5. <span data-ttu-id="d5bf7-225">Ajustar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-225">Adjust</span></span>
    6. <span data-ttu-id="d5bf7-226">Remover</span><span class="sxs-lookup"><span data-stu-id="d5bf7-226">Remove</span></span>
* <span data-ttu-id="d5bf7-227">Use sons semelhantes.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-227">Use similar sounds.</span></span> <span data-ttu-id="d5bf7-228">Tente evitar o uso de comandos de voz que Rhyme.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="d5bf7-229">Se você tivesse um aplicativo de compras com suporte para *"mostrar armazenamento"* e *"mostrar mais"* como comandos de voz, convém desabilitar um dos comandos enquanto o outro estava em uso.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="d5bf7-230">Por exemplo, você pode usar o botão *"mostrar armazenamento"* para abrir o repositório e, em seguida, desabilitar esse comando quando o repositório foi exibido para que o comando *"mostrar mais"* pudesse ser usado para navegação.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="d5bf7-231">Instruções</span><span class="sxs-lookup"><span data-stu-id="d5bf7-231">Instructions</span></span>

* <span data-ttu-id="d5bf7-232">No painel **hierarquia** do Unity, use a ferramenta de pesquisa para localizar o objeto **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="d5bf7-233">Clique duas vezes no objeto **holoComm_screen_mesh** para exibi-lo na **cena**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="d5bf7-234">Essa é a inspeção do Astronaut, que responderá aos nossos comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="d5bf7-235">No painel **Inspetor** , localize o componente **fonte de entrada de fala (script)** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="d5bf7-236">Expanda a seção **palavras-chave** para ver o comando de voz com suporte: **abra o Communicator**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="d5bf7-237">Clique no engrenagem no lado direito e selecione **Editar script**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-237">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="d5bf7-238">Explore o **SpeechInputSource.cs** para entender como ele usa o **KeywordRecognizer** para adicionar comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="d5bf7-239">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-239">Build and Deploy</span></span>

* <span data-ttu-id="d5bf7-240">No Unity, use **as configurações de Build de > de arquivo** para recompilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="d5bf7-241">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-241">Open the **App** folder.</span></span>
* <span data-ttu-id="d5bf7-242">Abra a **solução ModelExplorer do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-242">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="d5bf7-243">(Se você já criou/implantou esse projeto no Visual Studio durante a instalação, poderá abrir essa instância do VS e clicar em ' recarregar tudo ' quando solicitado).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="d5bf7-244">No Visual Studio, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="d5bf7-245">Depois que o aplicativo for implantado no HoloLens, descartar a caixa ajustar usando o gesto de [toque do ar](gaze-and-commit.md#composite-gestures) .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="d5bf7-246">Olhar na inspeção do Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="d5bf7-247">Quando o relógio tiver foco, verifique se o cursor é alterado para um microfone.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="d5bf7-248">Isso fornece comentários que o aplicativo está ouvindo por comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="d5bf7-249">Verifique se uma dica de ferramenta aparece na inspeção.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="d5bf7-250">Isso ajuda os usuários a descobrir o comando *"Open Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="d5bf7-251">Enquanto nuvens no relógio, digamos que *"Abra o Communicator"* para abrir o painel do Communicator.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="d5bf7-252">Capítulo 2-confirmação</span><span class="sxs-lookup"><span data-stu-id="d5bf7-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="d5bf7-253">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d5bf7-253">Objectives</span></span>

* <span data-ttu-id="d5bf7-254">Registre uma mensagem usando a entrada do microfone.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="d5bf7-255">Envie comentários para o usuário que o aplicativo está ouvindo em sua voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="d5bf7-256">A capacidade do **microfone** deve ser declarada para um aplicativo gravar do microfone.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="d5bf7-257">Isso é feito para você já no Sr Input 212, mas tenha isso em mente para seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="d5bf7-258">No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="d5bf7-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="d5bf7-259">Clique na guia "Plataforma Universal do Windows"</span><span class="sxs-lookup"><span data-stu-id="d5bf7-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="d5bf7-260">Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**</span><span class="sxs-lookup"><span data-stu-id="d5bf7-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="d5bf7-261">Instruções</span><span class="sxs-lookup"><span data-stu-id="d5bf7-261">Instructions</span></span>

* <span data-ttu-id="d5bf7-262">No painel **hierarquia** do Unity, verifique se o objeto **holoComm_screen_mesh** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="d5bf7-263">No painel **Inspetor** , localize o componente **Astronaut Watch (script)** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="d5bf7-264">Clique no cubo azul pequeno, que é definido como o valor da propriedade **pré-fabricado do Communicator** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="d5bf7-265">No painel **projeto** , o pré-fabricado do **Communicator** agora deve ter foco.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="d5bf7-266">Clique no pré-fabricado do **Communicator** no painel do **projeto** para exibir seus componentes no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="d5bf7-267">Examine o componente do **Gerenciador de microfone (script)** , isso nos permitirá registrar a voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="d5bf7-268">Observe que o objeto do **Communicator** tem um componente de **manipulador de entrada de fala (script)** para responder ao comando **Enviar mensagem** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="d5bf7-269">Examine o componente do **Communicator (script)** e clique duas vezes no script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="d5bf7-270">Communicator.cs é responsável por definir os Estados de botão apropriados no dispositivo do Communicator.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="d5bf7-271">Isso permitirá que os usuários registrem uma mensagem, a reproduzam e enviem a mensagem para o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="d5bf7-272">Ele também iniciará e interromperá um formulário de onda animado para confirmar ao usuário que sua voz foi ouvido.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="d5bf7-273">No **Communicator.cs**, exclua as seguintes linhas (81 e 82) do método **Start** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-273">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="d5bf7-274">Isso habilitará o botão ' registro ' no Communicator.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="d5bf7-275">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-275">Build and Deploy</span></span>

* <span data-ttu-id="d5bf7-276">No Visual Studio, recompile seu aplicativo e implante-o no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="d5bf7-277">Olhar na inspeção do Astronaut e diga *"Open Communicator"* para mostrar o Communicator.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="d5bf7-278">Pressione o botão **gravar** (microfone) para começar a gravar uma mensagem verbal para o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="d5bf7-279">Comece a falar e verifique se a animação ondulada é reproduzida no Communicator, que fornece comentários para o usuário de que a voz é ouvida.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="d5bf7-280">Pressione o botão **parar** (quadrado à esquerda) e verifique se a animação de onda interrompe a execução.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="d5bf7-281">Pressione o botão **reproduzir** (triângulo à direita) para reproduzir a mensagem gravada e ouvi-la no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="d5bf7-282">Pressione o botão **parar** (quadrado direito) para parar a reprodução da mensagem gravada.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="d5bf7-283">Diga *"Enviar mensagem"* para fechar o Communicator e receber uma resposta "mensagem recebida" do Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="d5bf7-284">Capítulo 3-noções básicas e o reconhecedor de ditador</span><span class="sxs-lookup"><span data-stu-id="d5bf7-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="d5bf7-285">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d5bf7-285">Objectives</span></span>

* <span data-ttu-id="d5bf7-286">Use o reconhecedor de ditado para converter a fala do usuário em texto.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="d5bf7-287">Mostre os resultados hipotéticos e finais do reconhecedor de ditado no Communicator.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="d5bf7-288">Neste capítulo, usaremos o reconhecedor de ditado para criar uma mensagem para o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="d5bf7-289">Ao usar o reconhecedor de ditado, tenha em mente que:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="d5bf7-290">Você deve estar conectado a WiFi para que o reconhecedor de ditado funcione.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="d5bf7-291">Os tempos limite ocorrem após um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="d5bf7-292">Há dois tempos limite a serem cientes:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="d5bf7-293">Se o reconhecedor for iniciado e não ouvir nenhum áudio pelos primeiros cinco segundos, ele atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="d5bf7-294">Se o reconhecedor tiver dado um resultado, mas, em seguida, ouvir silêncio por vinte segundos, ele atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="d5bf7-295">Somente um tipo de reconhecedor (palavra-chave ou ditado) pode ser executado de cada vez.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="d5bf7-296">A capacidade do **microfone** deve ser declarada para um aplicativo gravar do microfone.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="d5bf7-297">Isso é feito para você já no Sr Input 212, mas tenha isso em mente para seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="d5bf7-298">No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="d5bf7-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="d5bf7-299">Clique na guia "Plataforma Universal do Windows"</span><span class="sxs-lookup"><span data-stu-id="d5bf7-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="d5bf7-300">Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**</span><span class="sxs-lookup"><span data-stu-id="d5bf7-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="d5bf7-301">Instruções</span><span class="sxs-lookup"><span data-stu-id="d5bf7-301">Instructions</span></span>

<span data-ttu-id="d5bf7-302">Vamos editar **MicrophoneManager.cs** para usar o reconhecedor de ditado.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="d5bf7-303">Isso é o que vamos adicionar:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-303">This is what we'll add:</span></span>

1. <span data-ttu-id="d5bf7-304">Quando o **botão gravar** for pressionado, vamos **iniciar o DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-304">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="d5bf7-305">Mostre a **hipótese** do que o DictationRecognizer entendeu.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="d5bf7-306">Bloqueie os **resultados** do que o DictationRecognizer entendeu.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="d5bf7-307">Verifique se há tempos limite do DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="d5bf7-308">Quando o **botão parar** é pressionado, ou a sessão do MIC atinge o tempo limite, **pare o DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="d5bf7-309">Reinicie o **KeywordRecognizer**, que escutará o comando **Enviar mensagem** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-309">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="d5bf7-310">Vamos começar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-310">Let's get started.</span></span> <span data-ttu-id="d5bf7-311">Conclua todos os exercícios de codificação para 3. a no **MicrophoneManager.cs**, ou copie e cole o código concluído encontrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="d5bf7-312">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-312">Build and Deploy</span></span>

* <span data-ttu-id="d5bf7-313">Recompile no Visual Studio e implante em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="d5bf7-314">Descartar a caixa ajustar com um gesto de toque de ar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="d5bf7-315">Olhar na inspeção do Astronaut e diga *"Open Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-315">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="d5bf7-316">Selecione o botão **gravar** (microfone) para registrar sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="d5bf7-317">Comece a falar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-317">Start speaking.</span></span> <span data-ttu-id="d5bf7-318">O **reconhecedor de ditado** irá interpretar a fala e mostrar o texto hipotético no Communicator.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="d5bf7-319">Tente dizer *"Enviar mensagem"* enquanto estiver gravando uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="d5bf7-320">Observe que o **reconhecedor de palavra-chave** não responde porque o **reconhecedor de ditado** ainda está ativo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="d5bf7-321">Pare de falar por alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="d5bf7-322">Observe como o reconhecedor de ditado conclui sua hipótese e mostra o resultado final.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="d5bf7-323">Comece a falar e, em seguida, pause por 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="d5bf7-324">Isso fará com que o **reconhecedor de ditado** tenha tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="d5bf7-325">Observe que o **reconhecedor de palavra-chave** é habilitado novamente após o tempo limite acima.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="d5bf7-326">Agora, o Communicator responderá aos comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="d5bf7-327">Diga *"Enviar mensagem"* para enviar a mensagem para o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="d5bf7-328">Capítulo 4-reconhecedor de gramática</span><span class="sxs-lookup"><span data-stu-id="d5bf7-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="d5bf7-329">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d5bf7-329">Objectives</span></span>

* <span data-ttu-id="d5bf7-330">Use o reconhecedor de gramática para reconhecer a fala do usuário de acordo com um arquivo SRGS ou especificação de gramática de reconhecimento de fala.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="d5bf7-331">A capacidade do **microfone** deve ser declarada para um aplicativo gravar do microfone.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="d5bf7-332">Isso é feito para você já no Sr Input 212, mas tenha isso em mente para seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="d5bf7-333">No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="d5bf7-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="d5bf7-334">Clique na guia "Plataforma Universal do Windows"</span><span class="sxs-lookup"><span data-stu-id="d5bf7-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="d5bf7-335">Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**</span><span class="sxs-lookup"><span data-stu-id="d5bf7-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="d5bf7-336">Instruções</span><span class="sxs-lookup"><span data-stu-id="d5bf7-336">Instructions</span></span>

1. <span data-ttu-id="d5bf7-337">No painel **hierarquia** , procure **Jetpack_Center** e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="d5bf7-338">Procure o script de **ação que** no painel **Inspetor** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="d5bf7-339">Clique no pequeno círculo à direita do campo **para marcar** ao lado do objeto.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="d5bf7-340">Na janela que aparece, pesquise por **SRGSToolbox** e selecione-o na lista.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="d5bf7-341">Dê uma olhada no arquivo **SRGSColor. xml** na pasta **StreamingAssets** .</span><span class="sxs-lookup"><span data-stu-id="d5bf7-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="d5bf7-342">A especificação de design SRGS pode ser encontrada no site W3C [aqui](https://www.w3.org/TR/speech-grammar/).</span><span class="sxs-lookup"><span data-stu-id="d5bf7-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="d5bf7-343">Em nosso arquivo SRGS, temos três tipos de regras:</span><span class="sxs-lookup"><span data-stu-id="d5bf7-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="d5bf7-344">Uma regra que permite que você diga uma cor de uma lista de doze cores.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="d5bf7-345">Três regras que escutam uma combinação da regra de cor e uma das três formas.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="d5bf7-346">A regra raiz, colorChooser, que escuta qualquer combinação das três regras de "cor + forma".</span><span class="sxs-lookup"><span data-stu-id="d5bf7-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="d5bf7-347">As formas podem ser consideradas em qualquer ordem e em qualquer quantidade de apenas uma para a terceira.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="d5bf7-348">Essa é a única regra que está escutada, pois ela é especificada como a regra raiz na parte superior do arquivo na marca&gt; de gramática inicial de &lt;.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="d5bf7-349">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="d5bf7-349">Build and Deploy</span></span>

* <span data-ttu-id="d5bf7-350">Recompile o aplicativo no Unity e, em seguida, compile e implante a partir do Visual Studio para experimentar o aplicativo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="d5bf7-351">Descartar a caixa ajustar com um gesto de toque de ar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="d5bf7-352">Olhar no jetpack do Astronaut e execute um gesto de toque de ar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="d5bf7-353">Comece a falar.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-353">Start speaking.</span></span> <span data-ttu-id="d5bf7-354">O **reconhecedor gramatical** irá interpretar sua fala e alterar as cores das formas com base no reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="d5bf7-355">Um comando de exemplo é "círculo azul, quadrado amarelo".</span><span class="sxs-lookup"><span data-stu-id="d5bf7-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="d5bf7-356">Execute outro gesto de toque de ar para ignorar a caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="d5bf7-357">Fim</span><span class="sxs-lookup"><span data-stu-id="d5bf7-357">The End</span></span>

<span data-ttu-id="d5bf7-358">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="d5bf7-358">Congratulations!</span></span> <span data-ttu-id="d5bf7-359">Agora você concluiu a **entrada MR 212: Voice**.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-359">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="d5bf7-360">Você conhece o dos e não os comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="d5bf7-361">Você viu como as dicas de ferramentas foram empregadas para fazer com que os usuários reconheçam os comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="d5bf7-362">Você viu vários tipos de comentários usados para confirmar que a voz do usuário foi ouvida.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="d5bf7-363">Você sabe como alternar entre o reconhecedor de palavra-chave e o reconhecedor de ditador e como esses dois recursos compreendem e interpretam sua voz.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="d5bf7-364">Você aprendeu a usar um arquivo SRGS e o reconhecedor de gramática para reconhecimento de fala em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d5bf7-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>

---
title: 212 - voz de entrada de MR
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para saber os detalhes dos conceitos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, voz
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589357"
---
>[!NOTE]
><span data-ttu-id="c4a28-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="c4a28-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c4a28-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c4a28-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c4a28-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="c4a28-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c4a28-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="c4a28-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c4a28-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c4a28-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c4a28-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="c4a28-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="c4a28-110">Entrada MR 212: Voz</span><span class="sxs-lookup"><span data-stu-id="c4a28-110">MR Input 212: Voice</span></span>

<span data-ttu-id="c4a28-111">[Entrada de voz](voice-input.md) nos dá uma outra maneira de interagir com nossa hologramas.</span><span class="sxs-lookup"><span data-stu-id="c4a28-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="c4a28-112">Comandos de voz funcionam de maneira muito natural e fácil.</span><span class="sxs-lookup"><span data-stu-id="c4a28-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="c4a28-113">Projete seus comandos de voz para que eles sejam:</span><span class="sxs-lookup"><span data-stu-id="c4a28-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="c4a28-114">Natural</span><span class="sxs-lookup"><span data-stu-id="c4a28-114">Natural</span></span>
* <span data-ttu-id="c4a28-115">Fácil de lembrar</span><span class="sxs-lookup"><span data-stu-id="c4a28-115">Easy to remember</span></span>
* <span data-ttu-id="c4a28-116">Contexto apropriado</span><span class="sxs-lookup"><span data-stu-id="c4a28-116">Context appropriate</span></span>
* <span data-ttu-id="c4a28-117">Suficientemente diferente de outras opções no mesmo contexto</span><span class="sxs-lookup"><span data-stu-id="c4a28-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="c4a28-118">Na [MR Noções básicas de 101](holograms-101.md), usamos o KeywordRecognizer para compilar os dois comandos simples de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="c4a28-119">MR 212 de entrada, vamos Aprofunde-se e aprender como:</span><span class="sxs-lookup"><span data-stu-id="c4a28-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="c4a28-120">Comandos de voz de design que são otimizados para o mecanismo de fala do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c4a28-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="c4a28-121">Que o usuário saiba quais voz comandos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c4a28-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="c4a28-122">Reconhece que ouvimos de comando de voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="c4a28-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="c4a28-123">Compreender o que o usuário está dizendo, usando um reconhecedor de ditado.</span><span class="sxs-lookup"><span data-stu-id="c4a28-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="c4a28-124">Use um reconhecedor de gramática para escutar comandos com base em um arquivo de especificação de gramática de reconhecimento de fala, ou SRGS.</span><span class="sxs-lookup"><span data-stu-id="c4a28-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="c4a28-125">Neste curso, voltaremos a Gerenciador de modelos, nós o construímos [MR entrada 210](holograms-210.md) e [MR entrada 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="c4a28-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="c4a28-126">Os vídeos incorporados em cada um dos capítulos a seguir foram registrados usando uma versão mais antiga do Unity e o Kit de ferramentas de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="c4a28-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="c4a28-127">Enquanto as instruções passo a passo são precisas e atuais, você poderá ver scripts e visuais nos vídeos correspondentes que estão desatualizados.</span><span class="sxs-lookup"><span data-stu-id="c4a28-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="c4a28-128">Os vídeos permanecem incluídos serão lidas depois e porque os conceitos abordados ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="c4a28-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="c4a28-129">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="c4a28-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c4a28-130">Curso</span><span class="sxs-lookup"><span data-stu-id="c4a28-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c4a28-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c4a28-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c4a28-132"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="c4a28-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c4a28-133">Entrada MR 212: Voz</span><span class="sxs-lookup"><span data-stu-id="c4a28-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="c4a28-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c4a28-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c4a28-135">✔️</span><span class="sxs-lookup"><span data-stu-id="c4a28-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c4a28-136">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="c4a28-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c4a28-137">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c4a28-137">Prerequisites</span></span>

* <span data-ttu-id="c4a28-138">Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c4a28-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="c4a28-139">Alguns basic C# capacidade de programação.</span><span class="sxs-lookup"><span data-stu-id="c4a28-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="c4a28-140">Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="c4a28-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="c4a28-141">Você deve ter concluído [MR entrada 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="c4a28-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="c4a28-142">Você deve ter concluído [MR entrada 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="c4a28-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="c4a28-143">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c4a28-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c4a28-144">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="c4a28-144">Project files</span></span>

* <span data-ttu-id="c4a28-145">Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="c4a28-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="c4a28-146">Requer o Unity 2017.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="c4a28-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="c4a28-147">Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.</span><span class="sxs-lookup"><span data-stu-id="c4a28-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="c4a28-148">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="c4a28-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="c4a28-149">Errata e notas</span><span class="sxs-lookup"><span data-stu-id="c4a28-149">Errata and Notes</span></span>

* <span data-ttu-id="c4a28-150">"Habilitar apenas meu código" precisa ser desabilitado (*desmarcado*) no Visual Studio em Ferramentas -> Opções -> depuração para usar pontos de interrupção em seu código.</span><span class="sxs-lookup"><span data-stu-id="c4a28-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="c4a28-151">Instalação do Unity</span><span class="sxs-lookup"><span data-stu-id="c4a28-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a28-152">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4a28-152">Instructions</span></span>

1. <span data-ttu-id="c4a28-153">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="c4a28-153">Start Unity.</span></span>
2. <span data-ttu-id="c4a28-154">Selecione **aberto**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-154">Select **Open**.</span></span>
3. <span data-ttu-id="c4a28-155">Navegue até a **HolographicAcademy-hologramas 212 voz** pasta você anteriormente não arquivadas.</span><span class="sxs-lookup"><span data-stu-id="c4a28-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="c4a28-156">Localize e selecione o **iniciando**/**Gerenciador de modelos** pasta.</span><span class="sxs-lookup"><span data-stu-id="c4a28-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="c4a28-157">Clique o **Selecionar pasta** botão.</span><span class="sxs-lookup"><span data-stu-id="c4a28-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="c4a28-158">No **Project** do painel, expanda o **cenas** pasta.</span><span class="sxs-lookup"><span data-stu-id="c4a28-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="c4a28-159">Clique duas vezes em **ModelExplorer** cena para carregá-lo no Unity.</span><span class="sxs-lookup"><span data-stu-id="c4a28-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="c4a28-160">Compilação</span><span class="sxs-lookup"><span data-stu-id="c4a28-160">Building</span></span>

1. <span data-ttu-id="c4a28-161">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c4a28-162">Se **cenas/ModelExplorer** não estiver listado em **cenas em compilação**, clique em **adicionar cenas aberto** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="c4a28-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="c4a28-163">Se você estiver desenvolvendo especificamente para HoloLens, defina **dispositivo de destino** à **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="c4a28-164">Caso contrário, deixe-nos **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="c4a28-165">Certifique-se **Build Type** é definido como **D3D** e **SDK** é definido como **mais recente instalada** (que deve ser SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="c4a28-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="c4a28-166">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-166">Click **Build**.</span></span>
6. <span data-ttu-id="c4a28-167">Criar uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="c4a28-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="c4a28-168">Único clique a **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="c4a28-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="c4a28-169">Pressione **Selecionar pasta** e Unity começará a compilar o projeto para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4a28-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="c4a28-170">Quando Unity é feito, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="c4a28-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="c4a28-171">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="c4a28-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="c4a28-172">Abra o **ModelExplorer Visual Studio Solution**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c4a28-173">Se a implantação para o HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c4a28-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="c4a28-174">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="c4a28-175">Clique na lista suspensa na seta ao lado do botão de computador Local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="c4a28-176">Insira **seu endereço IP do dispositivo HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="c4a28-177">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-177">Click **Select**.</span></span> <span data-ttu-id="c4a28-178">Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas de**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="c4a28-179">Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c4a28-180">Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="c4a28-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="c4a28-181">Quando o aplicativo foi implantado, ignorar as **Fitbox** com um **selecione gesto**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="c4a28-182">Se implantar em um fone de ouvido imersivo:</span><span class="sxs-lookup"><span data-stu-id="c4a28-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="c4a28-183">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="c4a28-184">Verifique se o destino de implantação é definido como **computador Local**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="c4a28-185">Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="c4a28-186">Quando o aplicativo foi implantado, ignorar as **Fitbox** puxando o gatilho em um controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="c4a28-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="c4a28-187">Você pode observar alguns erros vermelhos no painel de erros do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4a28-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="c4a28-188">É seguro para ignorá-los.</span><span class="sxs-lookup"><span data-stu-id="c4a28-188">It is safe to ignore them.</span></span> <span data-ttu-id="c4a28-189">Alternar para o painel de saída para exibir real o progresso da compilação.</span><span class="sxs-lookup"><span data-stu-id="c4a28-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="c4a28-190">Erros no painel Saída exigirá que você faça uma correção (com mais frequência eles são causados por um erro em um script).</span><span class="sxs-lookup"><span data-stu-id="c4a28-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="c4a28-191">Capítulo 1 - reconhecimento</span><span class="sxs-lookup"><span data-stu-id="c4a28-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="c4a28-192">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4a28-192">Objectives</span></span>

* <span data-ttu-id="c4a28-193">Aprenda a **dicas** do design de comando de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="c4a28-194">Use **KeywordRecognizer** adicionar olhar com base em comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="c4a28-195">E informar os usuários de comandos de voz usando o cursor **comentários**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="c4a28-196">Design de comando de voz</span><span class="sxs-lookup"><span data-stu-id="c4a28-196">Voice Command Design</span></span>

<span data-ttu-id="c4a28-197">Neste capítulo, você aprenderá sobre a criação de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="c4a28-198">Ao criar comandos de voz:</span><span class="sxs-lookup"><span data-stu-id="c4a28-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="c4a28-199">DO</span><span class="sxs-lookup"><span data-stu-id="c4a28-199">DO</span></span>

* <span data-ttu-id="c4a28-200">Crie comandos concisos.</span><span class="sxs-lookup"><span data-stu-id="c4a28-200">Create concise commands.</span></span> <span data-ttu-id="c4a28-201">Você não quiser usar *"Reproduzir o vídeo selecionado no momento"*, porque esse comando não é mais conciso e poderia ser facilmente esquecido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c4a28-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="c4a28-202">Em vez disso, você deve usar: *"Reproduzir o vídeo"*, pois ela é concisa e tem vários sílabas.</span><span class="sxs-lookup"><span data-stu-id="c4a28-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="c4a28-203">Use um vocabulário simple.</span><span class="sxs-lookup"><span data-stu-id="c4a28-203">Use a simple vocabulary.</span></span> <span data-ttu-id="c4a28-204">Sempre tente usar palavras e frases que são fáceis de descobrir e lembre-se o usuário comuns.</span><span class="sxs-lookup"><span data-stu-id="c4a28-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="c4a28-205">Por exemplo, se o aplicativo tiver um objeto de anotação que pode ser exibido ou ocultado da exibição, você não usaria o comando *"Mostrar letreiro"*, pois "letreiro" é um termo usado raramente.</span><span class="sxs-lookup"><span data-stu-id="c4a28-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="c4a28-206">Em vez disso, você usaria o comando: *"Mostrar Observação"* para revelar a anotação em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="c4a28-207">Ser consistente.</span><span class="sxs-lookup"><span data-stu-id="c4a28-207">Be consistent.</span></span> <span data-ttu-id="c4a28-208">Comandos de voz devem ser mantidos consistentes entre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="c4a28-209">Imagine que você tenha duas cenas no seu aplicativo e as duas cenas contêm um botão para fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="c4a28-210">Se a primeira cena usado o comando *"Sair"* para disparar o botão, mas o segundo cena usado o comando *"Fechar aplicativo"*, em seguida, o usuário vai ficar muito confuso.</span><span class="sxs-lookup"><span data-stu-id="c4a28-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="c4a28-211">Se a mesma funcionalidade persiste por várias cenas, o mesmo comando de voz deve ser usado para dispará-lo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="c4a28-212">NÃO</span><span class="sxs-lookup"><span data-stu-id="c4a28-212">DON'T</span></span>

* <span data-ttu-id="c4a28-213">Use os comandos Sílaba único.</span><span class="sxs-lookup"><span data-stu-id="c4a28-213">Use single syllable commands.</span></span> <span data-ttu-id="c4a28-214">Por exemplo, se você estivesse criando um comando de voz para reproduzir um vídeo, você deve evitar usar o comando simple *"Reproduzir"*, conforme ele é apenas uma Sílaba única e pode ser facilmente perdido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="c4a28-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="c4a28-215">Em vez disso, você deve usar: *"Reproduzir o vídeo"*, pois ela é concisa e tem vários sílabas.</span><span class="sxs-lookup"><span data-stu-id="c4a28-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="c4a28-216">Use os comandos do sistema.</span><span class="sxs-lookup"><span data-stu-id="c4a28-216">Use system commands.</span></span> <span data-ttu-id="c4a28-217">O *"Selecionar"* comando é reservado pelo sistema para acionar um evento de toque para o objeto focalizado no momento.</span><span class="sxs-lookup"><span data-stu-id="c4a28-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="c4a28-218">Não use novamente o *"Selecionar"* de comando em uma palavra-chave ou frase, pois ele pode não funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="c4a28-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="c4a28-219">Por exemplo, se o comando de voz para selecionar um cubo em seu aplicativo estava *"Selecione cubo"*, mas o usuário estava procurando em uma esfera quando eles escrevi o comando, em seguida, o círculo seria selecionado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c4a28-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="c4a28-220">Da mesma forma da barra de comandos do aplicativo está habilitado para voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="c4a28-221">Não use os seguintes comandos de voz no modo de exibição CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="c4a28-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="c4a28-222">Voltar</span><span class="sxs-lookup"><span data-stu-id="c4a28-222">Go Back</span></span>
    2. <span data-ttu-id="c4a28-223">Ferramenta de rolagem</span><span class="sxs-lookup"><span data-stu-id="c4a28-223">Scroll Tool</span></span>
    3. <span data-ttu-id="c4a28-224">Ferramenta de zoom</span><span class="sxs-lookup"><span data-stu-id="c4a28-224">Zoom Tool</span></span>
    4. <span data-ttu-id="c4a28-225">Ferramenta de arrastar</span><span class="sxs-lookup"><span data-stu-id="c4a28-225">Drag Tool</span></span>
    5. <span data-ttu-id="c4a28-226">Ajustar</span><span class="sxs-lookup"><span data-stu-id="c4a28-226">Adjust</span></span>
    6. <span data-ttu-id="c4a28-227">Remover</span><span class="sxs-lookup"><span data-stu-id="c4a28-227">Remove</span></span>
* <span data-ttu-id="c4a28-228">Use sons semelhantes.</span><span class="sxs-lookup"><span data-stu-id="c4a28-228">Use similar sounds.</span></span> <span data-ttu-id="c4a28-229">Tente evitar o uso de comandos de voz poesia.</span><span class="sxs-lookup"><span data-stu-id="c4a28-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="c4a28-230">Se você tiver um aplicativo de compras que tem suporte *"Mostrar Store"* e *"Mostrar mais"* como comandos de voz, em seguida, você desejaria desabilitar um dos comandos, enquanto a outra estava em uso.</span><span class="sxs-lookup"><span data-stu-id="c4a28-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="c4a28-231">Por exemplo, você pode usar o *"Mostrar Store"* botão para abrir a loja e, em seguida, desabilite esse comando quando o repositório foi exibido para que o *"Mostrar mais"* comando pode ser usado para navegação.</span><span class="sxs-lookup"><span data-stu-id="c4a28-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a28-232">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4a28-232">Instructions</span></span>

* <span data-ttu-id="c4a28-233">Do Unity **hierarquia** do painel, use a ferramenta de pesquisa para localizar o **holoComm_screen_mesh** objeto.</span><span class="sxs-lookup"><span data-stu-id="c4a28-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="c4a28-234">Clique duas vezes no **holoComm_screen_mesh** objeto para exibi-lo na **cena**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="c4a28-235">Essa é a inspeção do astronaut, que responderá a nossa comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="c4a28-236">No **Inspector** do painel, localize a **fonte de entrada de fala (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="c4a28-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="c4a28-237">Expanda o **palavras-chave** seção para ver o comando de voz com suporte: **Abra o Communicator**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="c4a28-238">Clique na engrenagem ao lado direito e, em seguida, selecione **Editar Script**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="c4a28-239">Explore **SpeechInputSource.cs** entender como ele usa o **KeywordRecognizer** para adicionar comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c4a28-240">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="c4a28-240">Build and Deploy</span></span>

* <span data-ttu-id="c4a28-241">No Unity, use **arquivo > configurações de Build** para recompilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="c4a28-242">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="c4a28-242">Open the **App** folder.</span></span>
* <span data-ttu-id="c4a28-243">Abra o **ModelExplorer Visual Studio Solution**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="c4a28-244">(Se você já criado/implantado esse projeto no Visual Studio durante a instalação, em seguida, você pode abrir aquela instância do VS e clique em 'Recarregar todos' quando solicitado).</span><span class="sxs-lookup"><span data-stu-id="c4a28-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="c4a28-245">No Visual Studio, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="c4a28-246">Depois que o aplicativo é implantado para o HoloLens, ignorar a caixa de ajuste usando o [polegar](gestures.md#air-tap) gesto.</span><span class="sxs-lookup"><span data-stu-id="c4a28-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="c4a28-247">Mantenha o foco em inspeção do astronaut.</span><span class="sxs-lookup"><span data-stu-id="c4a28-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="c4a28-248">Quando o relógio tem o foco, verifique se que o cursor muda para um microfone.</span><span class="sxs-lookup"><span data-stu-id="c4a28-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="c4a28-249">Isso fornece comentários que o aplicativo está escutando comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="c4a28-250">Verifique se uma dica de ferramenta aparece no relógio.</span><span class="sxs-lookup"><span data-stu-id="c4a28-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="c4a28-251">Isso ajuda os usuários a descobrir os *"Communicator aberto"* comando.</span><span class="sxs-lookup"><span data-stu-id="c4a28-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="c4a28-252">Durante a observação na inspeção, digamos *"Abrir Communicator"* para abrir o painel do communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a28-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="c4a28-253">Capítulo 2 - confirmação</span><span class="sxs-lookup"><span data-stu-id="c4a28-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="c4a28-254">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4a28-254">Objectives</span></span>

* <span data-ttu-id="c4a28-255">Grave uma mensagem usando a entrada do microfone.</span><span class="sxs-lookup"><span data-stu-id="c4a28-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="c4a28-256">Fornecer comentários ao usuário que o aplicativo está escutando a sua voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="c4a28-257">O **microfone** capacidade deve ser declarada para um aplicativo registrar-se do microfone.</span><span class="sxs-lookup"><span data-stu-id="c4a28-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c4a28-258">Isso é feito para que você já no MR 212 de entrada, mas lembre-se para seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="c4a28-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c4a28-259">No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"</span><span class="sxs-lookup"><span data-stu-id="c4a28-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c4a28-260">Clique na guia "Plataforma Universal do Windows"</span><span class="sxs-lookup"><span data-stu-id="c4a28-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c4a28-261">Na seção "> recursos de publicação configurações", verifique as **microfone** funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c4a28-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a28-262">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4a28-262">Instructions</span></span>

* <span data-ttu-id="c4a28-263">Do Unity **hierarquia** do painel, verifique se que o **holoComm_screen_mesh** objeto está selecionado.</span><span class="sxs-lookup"><span data-stu-id="c4a28-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="c4a28-264">No **Inspector** do painel, localize a **Astronaut Watch (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="c4a28-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="c4a28-265">Clique no cubo pequeno e azul que é definido como o valor da **Communicator pré-fabricado** propriedade.</span><span class="sxs-lookup"><span data-stu-id="c4a28-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="c4a28-266">No **Project** painel, o **Communicator** pré-fabricado agora deve ter o foco.</span><span class="sxs-lookup"><span data-stu-id="c4a28-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="c4a28-267">Clique no **Communicator** pré-fabricado na **projeto** painel para exibir seus componentes no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="c4a28-268">Examine os **microfone Manager (Script)** componente, isso nos permitirá gravar voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="c4a28-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="c4a28-269">Observe que o **Communicator** objeto tem um **manipulador de entrada de fala (Script)** componente de resposta para o **enviar mensagem** comando.</span><span class="sxs-lookup"><span data-stu-id="c4a28-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="c4a28-270">Examine os **Communicator (Script)** componente e clique duas vezes em que o script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4a28-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="c4a28-271">Communicator.cs é responsável por definir os estados do botão adequada no dispositivo communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a28-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="c4a28-272">Isso permitirá que nossos usuários gravar uma mensagem, reproduzi-lo e enviar a mensagem para o astronaut.</span><span class="sxs-lookup"><span data-stu-id="c4a28-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="c4a28-273">Ele também iniciar e parar um formulário do wave animado, para confirmar para o usuário que sua voz foi ouvido.</span><span class="sxs-lookup"><span data-stu-id="c4a28-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="c4a28-274">Na **Communicator.cs**, exclua as linhas a seguir (81 e 82) da **iniciar** método.</span><span class="sxs-lookup"><span data-stu-id="c4a28-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="c4a28-275">Isso permitirá que o botão 'Record' sobre o communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a28-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="c4a28-276">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="c4a28-276">Build and Deploy</span></span>

* <span data-ttu-id="c4a28-277">No Visual Studio, recompile seu aplicativo e implantar o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="c4a28-278">Mantenha o foco em inspeção do astronautas e dizer *"Communicator aberto"* para mostrar o communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a28-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="c4a28-279">Pressione a **registro** botão (microfone) para iniciar a gravação de uma mensagem textual para o astronaut.</span><span class="sxs-lookup"><span data-stu-id="c4a28-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="c4a28-280">Comece a falar e verifique se que a animação wave é reproduzido no communicator, que fornece comentários ao usuário que sua voz seja ouvida.</span><span class="sxs-lookup"><span data-stu-id="c4a28-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="c4a28-281">Pressione a **parar** botão (quadrado à esquerda) e, em seguida, verifique se a animação wave para em execução.</span><span class="sxs-lookup"><span data-stu-id="c4a28-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="c4a28-282">Pressione a **reproduzir** botão (triângulo) para reproduzir a mensagem gravada e ouvi-lo no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="c4a28-283">Pressione a **parar** botão (quadrado à direita) para parar a reprodução da mensagem gravada.</span><span class="sxs-lookup"><span data-stu-id="c4a28-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="c4a28-284">Digamos *"Enviar mensagem"* para fechar o communicator e receber uma resposta de 'Mensagem recebida' da astronautas.</span><span class="sxs-lookup"><span data-stu-id="c4a28-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="c4a28-285">Capítulo 3 - Noções básicas e o reconhecedor de ditado</span><span class="sxs-lookup"><span data-stu-id="c4a28-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="c4a28-286">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4a28-286">Objectives</span></span>

* <span data-ttu-id="c4a28-287">Use o reconhecedor de ditado para converter a voz do usuário em texto.</span><span class="sxs-lookup"><span data-stu-id="c4a28-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="c4a28-288">Mostre os resultados de hipotética e finais do reconhecedor de ditado do communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a28-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="c4a28-289">Neste capítulo, vamos usar o reconhecedor de ditado para criar uma mensagem para o astronaut.</span><span class="sxs-lookup"><span data-stu-id="c4a28-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="c4a28-290">Ao usar o reconhecedor de ditado, tenha em mente que:</span><span class="sxs-lookup"><span data-stu-id="c4a28-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="c4a28-291">Você deve estar conectado ao Wi-Fi para o reconhecedor de ditado funcione.</span><span class="sxs-lookup"><span data-stu-id="c4a28-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="c4a28-292">Tempos limite ocorre após um período de tempo definido.</span><span class="sxs-lookup"><span data-stu-id="c4a28-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="c4a28-293">Há dois tempos limite a serem consideradas:</span><span class="sxs-lookup"><span data-stu-id="c4a28-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="c4a28-294">Se o reconhecedor começa e não ouve o áudio para os primeiros cinco segundos, ela atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c4a28-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="c4a28-295">Se o reconhecedor tenha dado a um resultado, mas, em seguida, ouve silêncio por 20 segundos, ela atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c4a28-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="c4a28-296">Apenas um tipo de reconhecedor (palavra-chave ou ditado) pode executar por vez.</span><span class="sxs-lookup"><span data-stu-id="c4a28-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="c4a28-297">O **microfone** capacidade deve ser declarada para um aplicativo registrar-se do microfone.</span><span class="sxs-lookup"><span data-stu-id="c4a28-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c4a28-298">Isso é feito para que você já no MR 212 de entrada, mas lembre-se para seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="c4a28-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c4a28-299">No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"</span><span class="sxs-lookup"><span data-stu-id="c4a28-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c4a28-300">Clique na guia "Plataforma Universal do Windows"</span><span class="sxs-lookup"><span data-stu-id="c4a28-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c4a28-301">Na seção "> recursos de publicação configurações", verifique as **microfone** funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c4a28-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a28-302">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4a28-302">Instructions</span></span>

<span data-ttu-id="c4a28-303">Vamos editar **MicrophoneManager.cs** para usar o reconhecedor de ditado.</span><span class="sxs-lookup"><span data-stu-id="c4a28-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="c4a28-304">Este é o que vamos adicionar:</span><span class="sxs-lookup"><span data-stu-id="c4a28-304">This is what we'll add:</span></span>

1. <span data-ttu-id="c4a28-305">Quando o **botão Record** é pressionada, vamos **iniciar o DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="c4a28-306">Mostrar o **hipótese** do qual o DictationRecognizer compreendido.</span><span class="sxs-lookup"><span data-stu-id="c4a28-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="c4a28-307">Bloquear a **resultados** do qual o DictationRecognizer compreendido.</span><span class="sxs-lookup"><span data-stu-id="c4a28-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="c4a28-308">Verifique se há tempos limite do DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="c4a28-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="c4a28-309">Quando o **botão Parar** é pressionada, ou o tempo limite, a sessão de mic **interromper o DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="c4a28-310">Reinicie o **KeywordRecognizer**, que escutará as **enviar mensagem** comando.</span><span class="sxs-lookup"><span data-stu-id="c4a28-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="c4a28-311">Vamos começar.</span><span class="sxs-lookup"><span data-stu-id="c4a28-311">Let's get started.</span></span> <span data-ttu-id="c4a28-312">Conclua todos os exercícios de codificação para 3.a na **MicrophoneManager.cs**, ou copie e cole o código concluído encontrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="c4a28-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="c4a28-313">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="c4a28-313">Build and Deploy</span></span>

* <span data-ttu-id="c4a28-314">Recompile no Visual Studio e implantar seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="c4a28-315">Descarte a caixa de ajuste com um gesto de toque de ar.</span><span class="sxs-lookup"><span data-stu-id="c4a28-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="c4a28-316">Mantenha o foco em inspeção do astronautas e dizer *"Communicator aberto"*.</span><span class="sxs-lookup"><span data-stu-id="c4a28-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="c4a28-317">Selecione o **registro** botão (microfone) para gravar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c4a28-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="c4a28-318">Comece a falar.</span><span class="sxs-lookup"><span data-stu-id="c4a28-318">Start speaking.</span></span> <span data-ttu-id="c4a28-319">O **ditado reconhecedor** interpretará sua fala e mostrar o texto hipotética em do communicator.</span><span class="sxs-lookup"><span data-stu-id="c4a28-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="c4a28-320">Experimente o ditado *"Enviar mensagem"* enquanto você estiver gravando uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="c4a28-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="c4a28-321">Observe que o **reconhecedor de palavra-chave** não responde porque o **ditado reconhecedor** ainda está ativa.</span><span class="sxs-lookup"><span data-stu-id="c4a28-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="c4a28-322">Pare a fala por alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="c4a28-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="c4a28-323">Assista como o reconhecedor de ditado conclui sua hipótese e mostra o resultado final.</span><span class="sxs-lookup"><span data-stu-id="c4a28-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="c4a28-324">Começar a falar e, em seguida, pausa por 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="c4a28-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="c4a28-325">Isso fará com que o **ditado reconhecedor** atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c4a28-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="c4a28-326">Observe que o **palavra-chave reconhecedor** for habilitado novamente após o tempo de limite acima.</span><span class="sxs-lookup"><span data-stu-id="c4a28-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="c4a28-327">Agora, o communicator responderá aos comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="c4a28-328">Digamos *"Enviar mensagem"* para enviar a mensagem para o astronaut.</span><span class="sxs-lookup"><span data-stu-id="c4a28-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="c4a28-329">Capítulo 4 - reconhecedor de gramática</span><span class="sxs-lookup"><span data-stu-id="c4a28-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="c4a28-330">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4a28-330">Objectives</span></span>

* <span data-ttu-id="c4a28-331">Use o reconhecedor de gramática para reconhecer fala do usuário de acordo com um arquivo de especificação de gramática de reconhecimento de fala, ou SRGS.</span><span class="sxs-lookup"><span data-stu-id="c4a28-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="c4a28-332">O **microfone** capacidade deve ser declarada para um aplicativo registrar-se do microfone.</span><span class="sxs-lookup"><span data-stu-id="c4a28-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="c4a28-333">Isso é feito para que você já no MR 212 de entrada, mas lembre-se para seus próprios projetos.</span><span class="sxs-lookup"><span data-stu-id="c4a28-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="c4a28-334">No Editor do Unity, vá para as configurações de player, navegando até "Editar > projeto Configurações > Player"</span><span class="sxs-lookup"><span data-stu-id="c4a28-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c4a28-335">Clique na guia "Plataforma Universal do Windows"</span><span class="sxs-lookup"><span data-stu-id="c4a28-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="c4a28-336">Na seção "> recursos de publicação configurações", verifique as **microfone** funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c4a28-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c4a28-337">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4a28-337">Instructions</span></span>

1. <span data-ttu-id="c4a28-338">No **hierarquia** do painel, pesquise por **Jetpack_Center** e selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="c4a28-339">Procure os **que ação** de script na **Inspetor** painel.</span><span class="sxs-lookup"><span data-stu-id="c4a28-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="c4a28-340">Clique no círculo pequeno à direita do **objeto à marca ao longo de** campo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="c4a28-341">Na janela pop-up, pesquise **SRGSToolbox** e selecione-o na lista.</span><span class="sxs-lookup"><span data-stu-id="c4a28-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="c4a28-342">Dê uma olhada a **SRGSColor.xml** arquivo na **StreamingAssets** pasta.</span><span class="sxs-lookup"><span data-stu-id="c4a28-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="c4a28-343">A especificação de design SRGS pode ser encontrada no site do W3C [aqui](https://www.w3.org/TR/speech-grammar/).</span><span class="sxs-lookup"><span data-stu-id="c4a28-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="c4a28-344">Em nosso arquivo SRGS, temos três tipos de regras:</span><span class="sxs-lookup"><span data-stu-id="c4a28-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="c4a28-345">Uma regra que permite que você dizer em uma cor de uma lista de doze cores.</span><span class="sxs-lookup"><span data-stu-id="c4a28-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="c4a28-346">Três regras que escuta para uma combinação da regra de cor e uma das três formas.</span><span class="sxs-lookup"><span data-stu-id="c4a28-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="c4a28-347">A regra raiz, colorChooser, que escuta para qualquer combinação das regras de três "de cor + da forma".</span><span class="sxs-lookup"><span data-stu-id="c4a28-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="c4a28-348">As formas podem ser dito em qualquer ordem e em qualquer quantidade de apenas um para todos os três.</span><span class="sxs-lookup"><span data-stu-id="c4a28-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="c4a28-349">Isso é a única regra que é ouvida, conforme ele é especificado como a regra raiz na parte superior do arquivo na primeira &lt;gramática&gt; marca.</span><span class="sxs-lookup"><span data-stu-id="c4a28-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="c4a28-350">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="c4a28-350">Build and Deploy</span></span>

* <span data-ttu-id="c4a28-351">Recompilar o aplicativo no Unity, em seguida, criar e implantar do Visual Studio para experimentar o aplicativo em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c4a28-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="c4a28-352">Descarte a caixa de ajuste com um gesto de toque de ar.</span><span class="sxs-lookup"><span data-stu-id="c4a28-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="c4a28-353">Mantenha o foco em jetpack do astronautas e execute um gesto de toque de ar.</span><span class="sxs-lookup"><span data-stu-id="c4a28-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="c4a28-354">Comece a falar.</span><span class="sxs-lookup"><span data-stu-id="c4a28-354">Start speaking.</span></span> <span data-ttu-id="c4a28-355">O **gramática reconhecedor** interpretará sua fala e alterar as cores das formas com base no reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="c4a28-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="c4a28-356">Um exemplo de comando é "quadrado círculo azul, amarelo".</span><span class="sxs-lookup"><span data-stu-id="c4a28-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="c4a28-357">Execute outro gesto de toque de ar para descartar a caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="c4a28-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="c4a28-358">Fim</span><span class="sxs-lookup"><span data-stu-id="c4a28-358">The End</span></span>

<span data-ttu-id="c4a28-359">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="c4a28-359">Congratulations!</span></span> <span data-ttu-id="c4a28-360">Agora você concluiu **MR 212 de entrada: Voz**.</span><span class="sxs-lookup"><span data-stu-id="c4a28-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="c4a28-361">Você sabe que dicas de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="c4a28-362">Você viu como as dicas de ferramentas foram empregadas conscientizá usuários dos comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="c4a28-363">Você viu vários tipos de comentários usados para confirmar que a voz do usuário foi ouvida.</span><span class="sxs-lookup"><span data-stu-id="c4a28-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="c4a28-364">Você sabe como alternar entre o reconhecedor de palavra-chave e o reconhecedor de ditado, e como esses dois recursos entenderem e interpretam sua voz.</span><span class="sxs-lookup"><span data-stu-id="c4a28-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="c4a28-365">Você aprendeu como usar um arquivo SRGS e o reconhecedor de gramática de reconhecimento de fala em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4a28-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>

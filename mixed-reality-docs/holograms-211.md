---
title: 211 - gesto de entrada de MR
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para saber os detalhes dos conceitos de gesto.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, gesto
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590635"
---
>[!NOTE]
><span data-ttu-id="e2af3-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="e2af3-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e2af3-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e2af3-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e2af3-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="e2af3-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e2af3-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="e2af3-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e2af3-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e2af3-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e2af3-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="e2af3-110">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="e2af3-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="e2af3-111">[Gestos](gestures.md) transformar a intenção do usuário em ação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="e2af3-112">Com gestos, os usuários podem interagir com hologramas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="e2af3-113">Neste curso, aprenderemos como acompanhar as mãos do usuário, responder à entrada do usuário e fornecem comentários ao usuário com base por lado estado e local.</span><span class="sxs-lookup"><span data-stu-id="e2af3-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="e2af3-114">Na [MR Noções básicas de 101](holograms-101.md), usamos um gesto polegar simples para interagir com nossa hologramas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="e2af3-115">Agora, vamos ultrapassar o gesto de toque de ar e explorar os novos conceitos para:</span><span class="sxs-lookup"><span data-stu-id="e2af3-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="e2af3-116">Detectar quando mão do usuário está sendo rastreada e fornecer comentários ao usuário.</span><span class="sxs-lookup"><span data-stu-id="e2af3-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="e2af3-117">Use um gesto de navegação para girar o nosso hologramas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="e2af3-118">Fornece comentários ao lado do usuário está prestes a sair do modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="e2af3-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="e2af3-119">Use eventos de manipulação para permitir que os usuários movam hologramas com suas mãos.</span><span class="sxs-lookup"><span data-stu-id="e2af3-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="e2af3-120">Neste curso, voltaremos o projeto do Unity **Gerenciador de modelos**, que criamos [MR entrada 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="e2af3-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="e2af3-121">Nosso amigo astronaut está de volta para nos ajudar em nossa exploração desses novos conceitos de gesto.</span><span class="sxs-lookup"><span data-stu-id="e2af3-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e2af3-122">Os vídeos incorporados em cada um dos capítulos a seguir foram registrados usando uma versão mais antiga do Unity e o Kit de ferramentas de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="e2af3-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="e2af3-123">Enquanto as instruções passo a passo são precisas e atuais, você poderá ver scripts e visuais nos vídeos correspondentes que estão desatualizados.</span><span class="sxs-lookup"><span data-stu-id="e2af3-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="e2af3-124">Os vídeos permanecem incluídos serão lidas depois e porque os conceitos abordados ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="e2af3-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="e2af3-125">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="e2af3-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e2af3-126">Curso</span><span class="sxs-lookup"><span data-stu-id="e2af3-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e2af3-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e2af3-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e2af3-128"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="e2af3-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="e2af3-129">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="e2af3-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="e2af3-130">✔️</span><span class="sxs-lookup"><span data-stu-id="e2af3-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e2af3-131">✔️</span><span class="sxs-lookup"><span data-stu-id="e2af3-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e2af3-132">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="e2af3-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e2af3-133">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e2af3-133">Prerequisites</span></span>

* <span data-ttu-id="e2af3-134">Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="e2af3-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="e2af3-135">Alguns basic C# capacidade de programação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="e2af3-136">Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="e2af3-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="e2af3-137">Você deve ter concluído [MR entrada 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="e2af3-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="e2af3-138">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="e2af3-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="e2af3-139">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="e2af3-139">Project files</span></span>

* <span data-ttu-id="e2af3-140">Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="e2af3-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="e2af3-141"> Requer o Unity 2017.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="e2af3-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="e2af3-142">Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.</span><span class="sxs-lookup"><span data-stu-id="e2af3-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="e2af3-143">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="e2af3-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="e2af3-144">Errata e notas</span><span class="sxs-lookup"><span data-stu-id="e2af3-144">Errata and Notes</span></span>

* <span data-ttu-id="e2af3-145">"Habilitar apenas meu código" precisa ser desabilitado (*desmarcado*) no Visual Studio em Ferramentas -> Opções -> depuração para usar pontos de interrupção em seu código.</span><span class="sxs-lookup"><span data-stu-id="e2af3-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="e2af3-146">Capítulo 0 - instalação do Unity</span><span class="sxs-lookup"><span data-stu-id="e2af3-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="e2af3-147">Instruções</span><span class="sxs-lookup"><span data-stu-id="e2af3-147">Instructions</span></span>

1. <span data-ttu-id="e2af3-148">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="e2af3-148">Start Unity.</span></span>
2. <span data-ttu-id="e2af3-149">Selecione **aberto**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-149">Select **Open**.</span></span>
3. <span data-ttu-id="e2af3-150">Navegue até a **gesto** pasta você anteriormente não arquivadas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="e2af3-151">Localize e selecione o **iniciando**/**Gerenciador de modelos** pasta.</span><span class="sxs-lookup"><span data-stu-id="e2af3-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="e2af3-152">Clique o **Selecionar pasta** botão.</span><span class="sxs-lookup"><span data-stu-id="e2af3-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="e2af3-153">No **Project** do painel, expanda o **cenas** pasta.</span><span class="sxs-lookup"><span data-stu-id="e2af3-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="e2af3-154">Clique duas vezes em **ModelExplorer** cena para carregá-lo no Unity.</span><span class="sxs-lookup"><span data-stu-id="e2af3-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="e2af3-155">Compilação</span><span class="sxs-lookup"><span data-stu-id="e2af3-155">Building</span></span>

1. <span data-ttu-id="e2af3-156">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="e2af3-157">Se **cenas/ModelExplorer** não estiver listado em **cenas em compilação**, clique em **adicionar cenas aberto** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="e2af3-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="e2af3-158">Se você estiver desenvolvendo especificamente para HoloLens, defina **dispositivo de destino** à **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="e2af3-159">Caso contrário, deixe-nos **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="e2af3-160">Certifique-se **Build Type** é definido como **D3D** e **SDK** é definido como **mais recente instalada** (que deve ser SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="e2af3-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="e2af3-161">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-161">Click **Build**.</span></span>
6. <span data-ttu-id="e2af3-162">Criar uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="e2af3-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="e2af3-163">Único clique a **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="e2af3-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="e2af3-164">Pressione **Selecionar pasta** e Unity começará a compilar o projeto para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2af3-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="e2af3-165">Quando Unity é feito, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="e2af3-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="e2af3-166">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="e2af3-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="e2af3-167">Abra o **ModelExplorer Visual Studio Solution**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="e2af3-168">Se a implantação para o HoloLens:</span><span class="sxs-lookup"><span data-stu-id="e2af3-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="e2af3-169">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="e2af3-170">Clique na lista suspensa na seta ao lado do botão de computador Local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="e2af3-171">Insira **seu endereço IP do dispositivo HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="e2af3-172">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-172">Click **Select**.</span></span> <span data-ttu-id="e2af3-173">Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas de**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="e2af3-174">Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="e2af3-175">Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="e2af3-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="e2af3-176">Quando o aplicativo foi implantado, ignorar as **Fitbox** com um **selecione gesto**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="e2af3-177">Se implantar em um fone de ouvido imersivo:</span><span class="sxs-lookup"><span data-stu-id="e2af3-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="e2af3-178">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="e2af3-179">Verifique se o destino de implantação é definido como **computador Local**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="e2af3-180">Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="e2af3-181">Quando o aplicativo foi implantado, ignorar as **Fitbox** puxando o gatilho em um controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="e2af3-182">Você pode observar alguns erros vermelhos no painel de erros do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2af3-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="e2af3-183">É seguro para ignorá-los.</span><span class="sxs-lookup"><span data-stu-id="e2af3-183">It is safe to ignore them.</span></span> <span data-ttu-id="e2af3-184">Alternar para o painel de saída para exibir real o progresso da compilação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="e2af3-185">Erros no painel Saída exigirá que você faça uma correção (com mais frequência eles são causados por um erro em um script).</span><span class="sxs-lookup"><span data-stu-id="e2af3-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="e2af3-186">Capítulo 1 - comentários de mão detectado</span><span class="sxs-lookup"><span data-stu-id="e2af3-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="e2af3-187">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e2af3-187">Objectives</span></span>

* <span data-ttu-id="e2af3-188">Inscrever-se para entregar os eventos de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="e2af3-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="e2af3-189">Use comentários de cursor para mostrar aos usuários quando uma mão está sendo rastreada.</span><span class="sxs-lookup"><span data-stu-id="e2af3-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="e2af3-190">Instruções</span><span class="sxs-lookup"><span data-stu-id="e2af3-190">Instructions</span></span>

* <span data-ttu-id="e2af3-191">No **hierarquia** do painel, expanda o **InputManager** objeto.</span><span class="sxs-lookup"><span data-stu-id="e2af3-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="e2af3-192">Procure e selecione o **GesturesInput** objeto.</span><span class="sxs-lookup"><span data-stu-id="e2af3-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="e2af3-193">O **InteractionInputSource.cs** script executa estas etapas:</span><span class="sxs-lookup"><span data-stu-id="e2af3-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="e2af3-194">Assina os eventos InteractionSourceDetected e InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="e2af3-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="e2af3-195">Define o estado de HandDetected.</span><span class="sxs-lookup"><span data-stu-id="e2af3-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="e2af3-196">Cancela a assinatura dos eventos InteractionSourceDetected e InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="e2af3-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="e2af3-197">Em seguida, vamos fazer a atualização nosso cursor a partir [MR entrada 210](holograms-210.md) em uma que mostra os comentários, dependendo de ações do usuário.</span><span class="sxs-lookup"><span data-stu-id="e2af3-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="e2af3-198">No **hierarquia** painel, selecione o **Cursor** do objeto e excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="e2af3-199">No **Project** do painel, pesquise por **CursorWithFeedback** e arraste-o para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="e2af3-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="e2af3-200">Clique em **InputManager** na **hierarquia** do painel e, em seguida, arraste o **CursorWithFeedback** do objeto do **hierarquia** no Do InputManager **SimpleSinglePointerSelector**do **Cursor** campo na parte inferior a **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="e2af3-201">Clique no **CursorWithFeedback** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="e2af3-202">No **Inspector** do painel, expanda **dados de estado do Cursor** no **objeto Cursor** script.</span><span class="sxs-lookup"><span data-stu-id="e2af3-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="e2af3-203">O **dados de estado de Cursor** funciona como este:</span><span class="sxs-lookup"><span data-stu-id="e2af3-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="e2af3-204">Qualquer **observar** estado significa que nenhuma disponível for detectado e o usuário está procurando simplesmente ao redor.</span><span class="sxs-lookup"><span data-stu-id="e2af3-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="e2af3-205">Qualquer **interagir** estado significa que uma mão ou controlador foi detectado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="e2af3-206">Qualquer **passe o mouse** estado significa que o usuário está observando um holograma.</span><span class="sxs-lookup"><span data-stu-id="e2af3-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="e2af3-207">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="e2af3-207">Build and Deploy</span></span>

* <span data-ttu-id="e2af3-208">No Unity, use **arquivo > configurações de Build** para recompilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="e2af3-209">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="e2af3-209">Open the **App** folder.</span></span>
* <span data-ttu-id="e2af3-210">Se não ainda estiver aberto, abra o **solução do Visual Studio ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="e2af3-211">(Se você já criado/implantado esse projeto no Visual Studio durante a instalação, em seguida, você pode abrir aquela instância do VS e clique em 'Recarregar todos' quando solicitado).</span><span class="sxs-lookup"><span data-stu-id="e2af3-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="e2af3-212">No Visual Studio, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="e2af3-213">Depois que o aplicativo é implantado para o HoloLens, ignore o fitbox usando o gesto de toque de ar.</span><span class="sxs-lookup"><span data-stu-id="e2af3-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="e2af3-214">Mova a mão na exibição e apontar o dedo para o céu para iniciar o acompanhamento de mão.</span><span class="sxs-lookup"><span data-stu-id="e2af3-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="e2af3-215">Mover a mão esquerda, direita, para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="e2af3-216">Assista como o cursor muda quando sua mão é detectada e, em seguida, perdida do modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="e2af3-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="e2af3-217">Se você estiver em um fone de ouvido imersivo, você terá para se conectar e desconectar seu controlador.</span><span class="sxs-lookup"><span data-stu-id="e2af3-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="e2af3-218">Esses comentários se torna menos interessante em um dispositivo imersivo, como um controlador conectado sempre será "disponível".</span><span class="sxs-lookup"><span data-stu-id="e2af3-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="e2af3-219">Capítulo 2 - navegação</span><span class="sxs-lookup"><span data-stu-id="e2af3-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="e2af3-220">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e2af3-220">Objectives</span></span>

* <span data-ttu-id="e2af3-221">Use eventos de gesto de navegação para girar a astronautas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="e2af3-222">Instruções</span><span class="sxs-lookup"><span data-stu-id="e2af3-222">Instructions</span></span>

<span data-ttu-id="e2af3-223">Para usar gestos de navegação em nosso aplicativo, vamos editar **GestureAction.cs** girar objetos quando ocorre o gesto de navegação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="e2af3-224">Além disso, vamos adicionar comentários para o cursor a ser exibido quando a navegação está disponível.</span><span class="sxs-lookup"><span data-stu-id="e2af3-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="e2af3-225">No **hierarquia** do painel, expanda **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="e2af3-226">No **hologramas** pasta, localize a **ScrollFeedback** ativo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="e2af3-227">Arraste e solte a **ScrollFeedback** pré-fabricado até a **CursorWithFeedback** GameObject no **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="e2af3-228">Clique em **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="e2af3-229">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="e2af3-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="e2af3-230">No menu, digite na caixa de pesquisa **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="e2af3-231">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e2af3-231">Select the search result.</span></span>
7. <span data-ttu-id="e2af3-232">Arrastar e soltar a **ScrollFeedback** do objeto da **hierarquia** até o **rolagem detectado jogo objeto** propriedade no **comentários de Cursor**componente do **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="e2af3-233">No **hierarquia** painel, selecione o **AstroMan** objeto.</span><span class="sxs-lookup"><span data-stu-id="e2af3-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="e2af3-234">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="e2af3-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="e2af3-235">No menu, digite na caixa de pesquisa **ação de gesto**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="e2af3-236">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e2af3-236">Select the search result.</span></span>

<span data-ttu-id="e2af3-237">Em seguida, abra **GestureAction.cs** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2af3-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="e2af3-238">Na codificação Exercício 2.c, edite o script para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e2af3-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="e2af3-239">**Girar o AstroMan** do objeto sempre que um gesto de navegação é executado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="e2af3-240">Calcular a **rotationFactor** para controlar a quantidade de rotação aplicada ao objeto.</span><span class="sxs-lookup"><span data-stu-id="e2af3-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="e2af3-241">**Girar o objeto** em torno do eixo y quando o usuário move sua mão esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="e2af3-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="e2af3-242">Codificação completa exercita 2.c no script ou substitua o código com a solução completa abaixo:</span><span class="sxs-lookup"><span data-stu-id="e2af3-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="e2af3-243">Você observará que os outros eventos de navegação já são preenchidos com algumas informações.</span><span class="sxs-lookup"><span data-stu-id="e2af3-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="e2af3-244">Podemos enviar por push o GameObject para o Kit de ferramentas pilha modal do InputSystem, portanto, o usuário não precisa manter o foco na astronautas depois que começou a rotação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="e2af3-245">Do mesmo modo, podemos pop o GameObject da pilha depois que o gesto é concluído.</span><span class="sxs-lookup"><span data-stu-id="e2af3-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="e2af3-246">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="e2af3-246">Build and Deploy</span></span>

1. <span data-ttu-id="e2af3-247">Recompilar o aplicativo no Unity e, em seguida, criar e implantar do Visual Studio para executá-lo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e2af3-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="e2af3-248">Mantenha o foco em astronaut, duas setas devem aparecer em ambos os lados do cursor.</span><span class="sxs-lookup"><span data-stu-id="e2af3-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="e2af3-249">Este novo visual indica que o astronaut pode ser girado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="e2af3-250">Coloque a mão na posição (dedo apontada para o céu) pronta para o HoloLens começará a mão de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="e2af3-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="e2af3-251">Para girar a astronautas, diminua o dedo para uma posição de aperto e, em seguida, mova a mão esquerda ou direita para disparar o gesto de NavigationX.</span><span class="sxs-lookup"><span data-stu-id="e2af3-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="e2af3-252">Capítulo 3 - diretrizes de mão</span><span class="sxs-lookup"><span data-stu-id="e2af3-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="e2af3-253">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e2af3-253">Objectives</span></span>

* <span data-ttu-id="e2af3-254">Use **pontuação de diretrizes de entregar** para ajudar a prever quando mão de acompanhamento serão perdida.</span><span class="sxs-lookup"><span data-stu-id="e2af3-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="e2af3-255">Fornecer **comentários sobre o cursor** para mostrar quando a borda da câmera do modo de exibição se aproximar de mão do usuário.</span><span class="sxs-lookup"><span data-stu-id="e2af3-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="e2af3-256">Instruções</span><span class="sxs-lookup"><span data-stu-id="e2af3-256">Instructions</span></span>

1. <span data-ttu-id="e2af3-257">No **hierarquia** painel, selecione o **CursorWithFeedback** objeto.</span><span class="sxs-lookup"><span data-stu-id="e2af3-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="e2af3-258">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="e2af3-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="e2af3-259">No menu, digite na caixa de pesquisa **diretrizes de mão**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="e2af3-260">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e2af3-260">Select the search result.</span></span>
4. <span data-ttu-id="e2af3-261">No **projeto** painel **hologramas** pasta, localize o **HandGuidanceFeedback** ativo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="e2af3-262">Arrastar e soltar a **HandGuidanceFeedback** ativo para o **indicador de orientação da mão** propriedade no **Inspetor** painel.</span><span class="sxs-lookup"><span data-stu-id="e2af3-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="e2af3-263">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="e2af3-263">Build and Deploy</span></span>

* <span data-ttu-id="e2af3-264">Recompilar o aplicativo no Unity e, em seguida, criar e implantar do Visual Studio para experimentar o aplicativo em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e2af3-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="e2af3-265">Colocar a mão em modo de exibição e disparar o dedo para rastreada.</span><span class="sxs-lookup"><span data-stu-id="e2af3-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="e2af3-266">Iniciar a rotação a astronautas com o gesto de navegação (apertar o dedo e polegar juntos).</span><span class="sxs-lookup"><span data-stu-id="e2af3-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="e2af3-267">Mova suas mãos à extrema esquerda, direita, para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="e2af3-268">Conforme a mão se aproximar a borda do quadro de gesto, uma seta deve aparecer ao lado, o cursor para avisá-lo mão de acompanhamento serão perdido.</span><span class="sxs-lookup"><span data-stu-id="e2af3-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="e2af3-269">A seta indica a direção na qual para mover sua mão para evitar que o acompanhamento sejam perdidas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="e2af3-270">Capítulo 4 - manipulação</span><span class="sxs-lookup"><span data-stu-id="e2af3-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="e2af3-271">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e2af3-271">Objectives</span></span>

* <span data-ttu-id="e2af3-272">Use eventos de manipulação para mover a astronautas com suas mãos.</span><span class="sxs-lookup"><span data-stu-id="e2af3-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="e2af3-273">Fornece comentários sobre o cursor para que o usuário saiba quando a manipulação pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="e2af3-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="e2af3-274">Instruções</span><span class="sxs-lookup"><span data-stu-id="e2af3-274">Instructions</span></span>

<span data-ttu-id="e2af3-275">GestureManager.cs e AstronautManager.cs, poderemos fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e2af3-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="e2af3-276">Use a palavra-chave fala "**mover Astronaut**" para habilitar **manipulação** gestos e "**Astronaut girar**" desabilitá-los.</span><span class="sxs-lookup"><span data-stu-id="e2af3-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="e2af3-277">Alternar para responder para o **reconhecedor de gestos de manipulação**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="e2af3-278">Vamos começar.</span><span class="sxs-lookup"><span data-stu-id="e2af3-278">Let's get started.</span></span>

1. <span data-ttu-id="e2af3-279">No **hierarquia** painel, crie um novo GameObject vazio.</span><span class="sxs-lookup"><span data-stu-id="e2af3-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="e2af3-280">Nomeie-o "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="e2af3-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="e2af3-281">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="e2af3-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="e2af3-282">No menu, digite na caixa de pesquisa **Astronaut Manager**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="e2af3-283">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e2af3-283">Select the search result.</span></span>
4. <span data-ttu-id="e2af3-284">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="e2af3-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="e2af3-285">No menu, digite na caixa de pesquisa **fonte de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="e2af3-286">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e2af3-286">Select the search result.</span></span>

<span data-ttu-id="e2af3-287">Agora vamos adicionar os comandos de voz necessários para controlar o estado de interação da astronautas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="e2af3-288">Expanda o **palavras-chave** seção o **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="e2af3-289">Clique o **+** no lado direito para adicionar uma nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e2af3-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="e2af3-290">Digite a palavra-chave como **mover Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="e2af3-291">Fique à vontade adicionar um atalho de chave, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="e2af3-292">Clique o **+** no lado direito para adicionar uma nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e2af3-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="e2af3-293">Digite a palavra-chave como **girar Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="e2af3-294">Fique à vontade adicionar um atalho de chave, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="e2af3-295">O código de manipulador correspondente pode ser encontrado no **GestureAction.cs**, no **ISpeechHandler.OnSpeechKeywordRecognized** manipulador.</span><span class="sxs-lookup"><span data-stu-id="e2af3-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Como configurar a fonte de entrada de fala para o capítulo 4](images/holograms211-speech.png)

<span data-ttu-id="e2af3-297">Em seguida, podemos irá configurar os comentários da manipulação no cursor.</span><span class="sxs-lookup"><span data-stu-id="e2af3-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="e2af3-298">No **projeto** painel **hologramas** pasta, localize o **PathingFeedback** ativo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="e2af3-299">Arraste e solte a **PathingFeedback** pré-fabricado até a **CursorWithFeedback** do objeto no **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="e2af3-300">No **hierarquia** do painel, clique em **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="e2af3-301">Arrastar e soltar a **PathingFeedback** do objeto da **hierarquia** até o **objeto de jogo detectados caminhos** propriedade no **comentários de Cursor**componente do **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="e2af3-302">Agora, precisamos adicionar código para **GestureAction.cs** para habilitar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e2af3-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="e2af3-303">Adicione código para o **IManipulationHandler.OnManipulationUpdated** função, que moverá a astronautas quando um **manipulação** gesto é detectado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="e2af3-304">Calcular a **vetor de movimento** determinar onde a astronautas devem ser movidas para posição de base por lado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="e2af3-305">**Mover** a astronautas para a nova posição.</span><span class="sxs-lookup"><span data-stu-id="e2af3-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="e2af3-306">Codificação completa Exercício 4.a na **GestureAction.cs**, ou usar nossa solução concluída abaixo:</span><span class="sxs-lookup"><span data-stu-id="e2af3-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="e2af3-307">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="e2af3-307">Build and Deploy</span></span>

* <span data-ttu-id="e2af3-308">Recompilar no Unity e, em seguida, criar e implantar do Visual Studio para executar o aplicativo no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e2af3-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="e2af3-309">Mover a mão na frente do HoloLens e disparar o dedo para que ele pode ser rastreado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="e2af3-310">Concentre-se o cursor sobre o astronaut.</span><span class="sxs-lookup"><span data-stu-id="e2af3-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="e2af3-311">Digamos que 'Mover Astronaut' para mover a astronautas com um gesto de manipulação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="e2af3-312">Quatro setas devem aparecer ao redor do cursor para indicar que o programa agora responderá a eventos de manipulação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="e2af3-313">Diminua o dedo para baixo até o polegar e mantê-los preso durante juntos.</span><span class="sxs-lookup"><span data-stu-id="e2af3-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="e2af3-314">Ao mudar sua mão em torno de, a astronautas moverá muito (essa é a manipulação).</span><span class="sxs-lookup"><span data-stu-id="e2af3-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="e2af3-315">Acionar o dedo para parar de manipular a astronautas.</span><span class="sxs-lookup"><span data-stu-id="e2af3-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="e2af3-316">Observação: Se você não diz 'Mover Astronaut' antes de passar a mão, em seguida, o gesto de navegação será usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e2af3-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="e2af3-317">Digamos que 'Girar Astronaut' para retornar ao estado giratório.</span><span class="sxs-lookup"><span data-stu-id="e2af3-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="e2af3-318">Capítulo 5 - expansão do modelo</span><span class="sxs-lookup"><span data-stu-id="e2af3-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="e2af3-319">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e2af3-319">Objectives</span></span>

* <span data-ttu-id="e2af3-320">Expanda o modelo Astronaut em vários, partes menores que o usuário pode interagir com o.</span><span class="sxs-lookup"><span data-stu-id="e2af3-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="e2af3-321">Mova cada parte individualmente usando gestos de navegação e manipulação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="e2af3-322">Instruções</span><span class="sxs-lookup"><span data-stu-id="e2af3-322">Instructions</span></span>

<span data-ttu-id="e2af3-323">Nesta seção, podemos irá realizar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="e2af3-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="e2af3-324">Adicionar uma nova palavra-chave "**expanda modelo**" para expandir o modelo astronaut.</span><span class="sxs-lookup"><span data-stu-id="e2af3-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="e2af3-325">Adicionar uma nova palavra-chave "**redefinição de modelo**" para retornar o modelo em sua forma original.</span><span class="sxs-lookup"><span data-stu-id="e2af3-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="e2af3-326">Faremos isso adicionando mais duas palavras-chave para a fonte de entrada de fala do capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="e2af3-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="e2af3-327">Também demonstraremos outra maneira de lidar com eventos de reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="e2af3-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="e2af3-328">Clique em Voltar na **AstronautManager** na **Inspetor** e expanda o **palavras-chave** seção o **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="e2af3-329">Clique o **+** no lado direito para adicionar uma nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e2af3-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="e2af3-330">Digite a palavra-chave como **expandir modelo**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="e2af3-331">Fique à vontade adicionar um atalho de chave, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="e2af3-332">Clique o **+** no lado direito para adicionar uma nova palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e2af3-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="e2af3-333">Digite a palavra-chave como **redefinição de modelo**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="e2af3-334">Fique à vontade adicionar um atalho de chave, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e2af3-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="e2af3-335">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="e2af3-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="e2af3-336">No menu, digite na caixa de pesquisa **manipulador de entrada de fala**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="e2af3-337">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e2af3-337">Select the search result.</span></span>
8. <span data-ttu-id="e2af3-338">Verifique **ouvinte Global é**, pois queremos que esses comandos funcionem independentemente do GameObject estamos nos concentrando.</span><span class="sxs-lookup"><span data-stu-id="e2af3-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="e2af3-339">Clique o **+** botão e selecione **expanda modelo** na lista suspensa de palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e2af3-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="e2af3-340">Clique o **+** em resposta e arraste o **AstronautManager** do **hierarquia** no **None (objeto)** campo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="e2af3-341">Agora, clique o **nenhuma função** lista suspensa, selecione **AstronautManager**, em seguida, **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="e2af3-342">Clique o manipulador de entrada de fala **+** botão e selecione **redefinição de modelo** na lista suspensa de palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e2af3-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="e2af3-343">Clique o **+** em resposta e arraste o **AstronautManager** do **hierarquia** no **None (objeto)** campo.</span><span class="sxs-lookup"><span data-stu-id="e2af3-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="e2af3-344">Agora, clique o **nenhuma função** lista suspensa, selecione **AstronautManager**, em seguida, **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Como configurar a fonte de entrada de fala e o manipulador para o capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="e2af3-346">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="e2af3-346">Build and Deploy</span></span>

* <span data-ttu-id="e2af3-347">Experimente!</span><span class="sxs-lookup"><span data-stu-id="e2af3-347">Try it!</span></span> <span data-ttu-id="e2af3-348">Crie e implante o aplicativo para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e2af3-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="e2af3-349">Digamos **expanda modelo** para ver o modelo astronaut expandido.</span><span class="sxs-lookup"><span data-stu-id="e2af3-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="e2af3-350">Use **navegação** para girar a partes individuais do naipe astronaut.</span><span class="sxs-lookup"><span data-stu-id="e2af3-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="e2af3-351">Digamos **mover Astronaut** e, em seguida, use **manipulação** para mover as partes individuais do naipe astronaut.</span><span class="sxs-lookup"><span data-stu-id="e2af3-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="e2af3-352">Digamos **Astronaut girar** girar as partes novamente.</span><span class="sxs-lookup"><span data-stu-id="e2af3-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="e2af3-353">Digamos **redefinição de modelo** para retornar o astronaut para sua forma original.</span><span class="sxs-lookup"><span data-stu-id="e2af3-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="e2af3-354">Fim</span><span class="sxs-lookup"><span data-stu-id="e2af3-354">The End</span></span>

<span data-ttu-id="e2af3-355">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="e2af3-355">Congratulations!</span></span> <span data-ttu-id="e2af3-356">Agora você concluiu **MR 211 de entrada: Gesto**.</span><span class="sxs-lookup"><span data-stu-id="e2af3-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="e2af3-357">Você sabe como detectar e responder para entregar os eventos de rastreamento, navegação e manipulação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="e2af3-358">Você compreender a diferença entre os gestos de navegação e manipulação.</span><span class="sxs-lookup"><span data-stu-id="e2af3-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="e2af3-359">Você sabe como alterar o cursor para fornecer comentários visuais para quando uma mão é detectada, quando uma mão está prestes a ser perdidas, e para quando um objeto oferecer suporte a interações diferentes (vs manipulação de navegação).</span><span class="sxs-lookup"><span data-stu-id="e2af3-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>

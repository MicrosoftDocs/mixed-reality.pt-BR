---
title: Entrada MR 210-olhar
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos de olhar.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, olhar
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434687"
---
>[!NOTE]
><span data-ttu-id="53e1e-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="53e1e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="53e1e-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="53e1e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="53e1e-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="53e1e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="53e1e-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="53e1e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="53e1e-108">[Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="53e1e-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="53e1e-109">Entrada MR 210: olhar</span><span class="sxs-lookup"><span data-stu-id="53e1e-109">MR Input 210: Gaze</span></span>

<span data-ttu-id="53e1e-110">[Olhar](gaze-and-commit.md) é a primeira forma de entrada e revela a intenção e a conscientização do usuário.</span><span class="sxs-lookup"><span data-stu-id="53e1e-110">[Gaze](gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="53e1e-111">A entrada MR 210 (também conhecida como explorador de projeto) é aprofundada nos conceitos relacionados ao olhar para a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="53e1e-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="53e1e-112">Adicionaremos reconhecimento contextual ao cursor e aos hologramas, aproveitando ao máximo o que seu aplicativo sabe sobre o olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="53e1e-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="53e1e-113">Temos um Astronaut amigável aqui para ajudá-lo a aprender os conceitos de olhar.</span><span class="sxs-lookup"><span data-stu-id="53e1e-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="53e1e-114">No [Sr basics 101](holograms-101.md), tínhamos um simples cursor que logo seguiu o olhar.</span><span class="sxs-lookup"><span data-stu-id="53e1e-114">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="53e1e-115">Hoje, estamos movendo uma etapa além do cursor simples:</span><span class="sxs-lookup"><span data-stu-id="53e1e-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="53e1e-116">Estamos fazendo com que o cursor e nossos hologramas olhar: ambos mudarão de acordo com o local em que o usuário está olhando ou para onde o usuário *não* está olhando.</span><span class="sxs-lookup"><span data-stu-id="53e1e-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="53e1e-117">Isso faz com que eles reconheçam o contexto.</span><span class="sxs-lookup"><span data-stu-id="53e1e-117">This makes them context-aware.</span></span>
* <span data-ttu-id="53e1e-118">Vamos adicionar comentários ao cursor e aos hologramas para dar ao usuário mais contexto sobre o que está sendo direcionado.</span><span class="sxs-lookup"><span data-stu-id="53e1e-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="53e1e-119">Esses comentários podem ser áudio e Visual.</span><span class="sxs-lookup"><span data-stu-id="53e1e-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="53e1e-120">Mostraremos as técnicas de direcionamento para ajudar os usuários a atingirem destinos menores.</span><span class="sxs-lookup"><span data-stu-id="53e1e-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="53e1e-121">Mostraremos como atrair a atenção do usuário para seus hologramas com um indicador direcional.</span><span class="sxs-lookup"><span data-stu-id="53e1e-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="53e1e-122">Ensinaremos técnicas para levar seus hologramas com o usuário quando ele se movimentar em seu mundo.</span><span class="sxs-lookup"><span data-stu-id="53e1e-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="53e1e-123">Os vídeos inseridos em cada um dos capítulos abaixo foram registrados usando uma versão mais antiga do Unity e o kit de ferramentas do Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="53e1e-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="53e1e-124">Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão desatualizados.</span><span class="sxs-lookup"><span data-stu-id="53e1e-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="53e1e-125">Os vídeos permanecem incluídos para posterity e porque os conceitos abordados ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="53e1e-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="53e1e-126">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="53e1e-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="53e1e-127">Course</span><span class="sxs-lookup"><span data-stu-id="53e1e-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="53e1e-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="53e1e-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="53e1e-129"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="53e1e-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="53e1e-130">Entrada MR 210: olhar</span><span class="sxs-lookup"><span data-stu-id="53e1e-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="53e1e-131">✔️</span><span class="sxs-lookup"><span data-stu-id="53e1e-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="53e1e-132">✔️</span><span class="sxs-lookup"><span data-stu-id="53e1e-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="53e1e-133">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="53e1e-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="53e1e-134">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="53e1e-134">Prerequisites</span></span>

* <span data-ttu-id="53e1e-135">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="53e1e-135">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="53e1e-136">Alguma capacidade C# básica de programação.</span><span class="sxs-lookup"><span data-stu-id="53e1e-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="53e1e-137">Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="53e1e-137">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="53e1e-138">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="53e1e-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="53e1e-139">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="53e1e-139">Project files</span></span>

* <span data-ttu-id="53e1e-140">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="53e1e-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="53e1e-141"> Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="53e1e-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="53e1e-142">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="53e1e-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="53e1e-143">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="53e1e-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="53e1e-144">Errata e observações</span><span class="sxs-lookup"><span data-stu-id="53e1e-144">Errata and Notes</span></span>

* <span data-ttu-id="53e1e-145">No Visual Studio, "Apenas Meu Código" precisa ser desabilitado (desmarcado) em Ferramentas-> Opções-> depuração para acessar os pontos de interrupção no código.</span><span class="sxs-lookup"><span data-stu-id="53e1e-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="53e1e-146">Capítulo 1 – configuração do Unity</span><span class="sxs-lookup"><span data-stu-id="53e1e-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="53e1e-147">Objetivos</span><span class="sxs-lookup"><span data-stu-id="53e1e-147">Objectives</span></span>

* <span data-ttu-id="53e1e-148">Otimizar o Unity para o desenvolvimento no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53e1e-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="53e1e-149">Importar ativos e configurar a cena.</span><span class="sxs-lookup"><span data-stu-id="53e1e-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="53e1e-150">Exiba o Astronaut no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53e1e-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="53e1e-151">Instruções</span><span class="sxs-lookup"><span data-stu-id="53e1e-151">Instructions</span></span>

1. <span data-ttu-id="53e1e-152">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="53e1e-152">Start Unity.</span></span>
2. <span data-ttu-id="53e1e-153">Selecione **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-153">Select **New Project**.</span></span>
3. <span data-ttu-id="53e1e-154">Nomeie o projeto **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-154">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="53e1e-155">Insira o local como a pasta **olhar** que você cancelou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="53e1e-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="53e1e-156">Verifique se o projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-156">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="53e1e-157">Clique em **Criar Projeto**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-157">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="53e1e-158">Configurações de Unity para o HoloLens</span><span class="sxs-lookup"><span data-stu-id="53e1e-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="53e1e-159">Precisamos deixar que o Unity saiba que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D.</span><span class="sxs-lookup"><span data-stu-id="53e1e-159">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="53e1e-160">Fazemos isso adicionando o HoloLens como um dispositivo de realidade virtual.</span><span class="sxs-lookup"><span data-stu-id="53e1e-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="53e1e-161">Vá para **Editar configurações de projeto > > Player**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-161">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="53e1e-162">No **painel Inspetor** para configurações do Player, selecione o ícone **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="53e1e-163">Expanda o grupo de **configurações XR** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="53e1e-164">Na seção **renderização** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **SDKs de realidade virtual** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="53e1e-165">Verifique se a **realidade mista do Windows** aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="53e1e-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="53e1e-166">Caso contrário, selecione o botão **+** na parte inferior da lista e escolha **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="53e1e-167">Em seguida, precisamos definir nosso back-end de script para .NET.</span><span class="sxs-lookup"><span data-stu-id="53e1e-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="53e1e-168">Vá para **Editar configurações de projeto > > Player** (talvez você ainda tenha isso na etapa anterior).</span><span class="sxs-lookup"><span data-stu-id="53e1e-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="53e1e-169">No **painel Inspetor** para configurações do Player, selecione o ícone **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="53e1e-170">Na seção configuração de **outras configurações** , verifique se o **back-end de script** está definido como **.net**</span><span class="sxs-lookup"><span data-stu-id="53e1e-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="53e1e-171">Por fim, atualizaremos nossas configurações de qualidade para obter um desempenho rápido no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53e1e-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="53e1e-172">Vá para **Editar configurações de projeto > > qualidade**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-172">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="53e1e-173">Clique na seta apontando para baixo na linha **padrão** no ícone Windows Store.</span><span class="sxs-lookup"><span data-stu-id="53e1e-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="53e1e-174">Selecione **muito baixo** para **aplicativos da Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-174">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="53e1e-175">Importar ativos de projeto</span><span class="sxs-lookup"><span data-stu-id="53e1e-175">Import project assets</span></span>

1. <span data-ttu-id="53e1e-176">Clique com o botão direito do mouse na pasta **ativos** no painel **projeto** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="53e1e-177">Clique em **Importar pacote > pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-177">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="53e1e-178">Navegue até os arquivos de projeto que você baixou e clique em **ModelExplorer. unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="53e1e-179">Clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-179">Click **Open**.</span></span>
5. <span data-ttu-id="53e1e-180">Depois que o pacote for carregado, clique no botão **importar** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="53e1e-181">Configurar a cena</span><span class="sxs-lookup"><span data-stu-id="53e1e-181">Setup the scene</span></span>

1. <span data-ttu-id="53e1e-182">Na hierarquia, exclua a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-182">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="53e1e-183">Na pasta **HoloToolkit** , abra a pasta de **entrada** e, em seguida, abra a pasta **pré-fabricados** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="53e1e-184">Arraste e solte o **MixedRealityCameraParent** pré-fabricado da pasta **pré-fabricados** para a **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="53e1e-185">Clique com o botão direito do mouse na **luz direcional** na hierarquia e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-185">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="53e1e-186">Na pasta **hologramas** , arraste e solte os seguintes ativos na raiz da **hierarquia**:</span><span class="sxs-lookup"><span data-stu-id="53e1e-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="53e1e-187">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="53e1e-187">**AstroMan**</span></span>
    * <span data-ttu-id="53e1e-188">**Noturna**</span><span class="sxs-lookup"><span data-stu-id="53e1e-188">**Lights**</span></span>
    * <span data-ttu-id="53e1e-189">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="53e1e-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="53e1e-190">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="53e1e-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="53e1e-191">Inicie o **modo de reprodução** ▶ para exibir o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="53e1e-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="53e1e-192">Clique em **modo de reprodução** ▶ novamente para **parar**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-192">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="53e1e-193">Na pasta **hologramas** , localize o ativo **Fitbox** e arraste-o para a raiz da **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="53e1e-194">Selecione o **Fitbox** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="53e1e-195">Arraste a coleção **AstroMan** da **hierarquia** para a propriedade de **coleção de holograma** do Fitbox no painel de **Inspetor** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="53e1e-196">Salvar o projeto</span><span class="sxs-lookup"><span data-stu-id="53e1e-196">Save the project</span></span>

1. <span data-ttu-id="53e1e-197">Salve a nova cena: **arquivo > salvar cena como**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-197">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="53e1e-198">Clique em **nova pasta** e nomeie a pasta **cenas**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-198">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="53e1e-199">Nomeie o arquivo como "**ModelExplorer**" e salve-o na pasta de **cenas** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-199">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="53e1e-200">Compilar o projeto</span><span class="sxs-lookup"><span data-stu-id="53e1e-200">Build the project</span></span>

1. <span data-ttu-id="53e1e-201">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-201">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="53e1e-202">Clique em **Adicionar abrir cenas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="53e1e-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="53e1e-203">Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="53e1e-204">Se você estiver desenvolvendo especificamente para o HoloLens, defina o **dispositivo de destino** para o **hololens**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="53e1e-205">Caso contrário, deixe em **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-205">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="53e1e-206">Verifique se **tipo de compilação** está definido como **D3D** e se o **SDK** está definido para o **mais recente instalado** (que deve ser o SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="53e1e-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="53e1e-207">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-207">Click **Build**.</span></span>
7. <span data-ttu-id="53e1e-208">Crie uma **nova pasta** chamada "app".</span><span class="sxs-lookup"><span data-stu-id="53e1e-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="53e1e-209">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="53e1e-210">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-210">Press **Select Folder**.</span></span>

<span data-ttu-id="53e1e-211">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="53e1e-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="53e1e-212">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="53e1e-213">Abra a **solução ModelExplorer do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-213">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="53e1e-214">Se estiver implantando no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="53e1e-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="53e1e-215">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="53e1e-216">Clique na seta suspensa ao lado do botão computador local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="53e1e-217">Insira **o endereço IP do dispositivo de HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="53e1e-218">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-218">Click **Select**.</span></span> <span data-ttu-id="53e1e-219">Se você não souber o endereço IP do dispositivo, examine **configurações > rede & Internet > opções avançadas**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="53e1e-220">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="53e1e-221">Se esta for a primeira vez que você está implantando em seu dispositivo, será necessário [emparelhar com o Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="53e1e-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="53e1e-222">Quando o aplicativo tiver sido implantado, ignore o **Fitbox** com um **gesto de seleção**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="53e1e-223">Se estiver implantando em um headset de imersão:</span><span class="sxs-lookup"><span data-stu-id="53e1e-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="53e1e-224">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="53e1e-225">Verifique se o destino de implantação está definido como **computador local**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-225">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="53e1e-226">Na barra de menus superior, clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="53e1e-227">Quando o aplicativo tiver sido implantado, ignore o **Fitbox** puxando o gatilho em um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="53e1e-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="53e1e-228">Capítulo 2-comentários de cursor e destino</span><span class="sxs-lookup"><span data-stu-id="53e1e-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="53e1e-229">Objetivos</span><span class="sxs-lookup"><span data-stu-id="53e1e-229">Objectives</span></span>

* <span data-ttu-id="53e1e-230">Design e comportamento do Visual do cursor.</span><span class="sxs-lookup"><span data-stu-id="53e1e-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="53e1e-231">Comentários do cursor baseado em olhar.</span><span class="sxs-lookup"><span data-stu-id="53e1e-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="53e1e-232">Comentários sobre o holograma baseado em olhar.</span><span class="sxs-lookup"><span data-stu-id="53e1e-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="53e1e-233">Vamos basear nosso trabalho em alguns princípios de design de cursor, ou seja:</span><span class="sxs-lookup"><span data-stu-id="53e1e-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="53e1e-234">O cursor está sempre presente.</span><span class="sxs-lookup"><span data-stu-id="53e1e-234">The cursor is always present.</span></span>
* <span data-ttu-id="53e1e-235">Não deixe o cursor ficar muito pequeno ou grande.</span><span class="sxs-lookup"><span data-stu-id="53e1e-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="53e1e-236">Evite obstruir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="53e1e-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="53e1e-237">Instruções</span><span class="sxs-lookup"><span data-stu-id="53e1e-237">Instructions</span></span>

1. <span data-ttu-id="53e1e-238">Na pasta **HoloToolkit\Input\Prefabs** , localize o ativo **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="53e1e-239">Arraste e solte o **InputManager** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-239">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="53e1e-240">Na pasta **HoloToolkit\Input\Prefabs** , localize o ativo de **cursor** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="53e1e-241">Arraste e solte o **cursor** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-241">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="53e1e-242">Selecione o objeto **InputManager** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-242">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="53e1e-243">Arraste o objeto **cursor** da **hierarquia** para o campo de **cursor** do **SimpleSinglePointerSelector**da InputManager, na parte inferior do **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Configuração do seletor de ponteiro único simples](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="53e1e-245">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="53e1e-245">Build and Deploy</span></span>

1. <span data-ttu-id="53e1e-246">Recompile o aplicativo do **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-246">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="53e1e-247">Abra a **pasta do aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-247">Open the **App folder**.</span></span>
3. <span data-ttu-id="53e1e-248">Abra a **solução ModelExplorer do Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-248">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="53e1e-249">Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="53e1e-250">Observe como o cursor é desenhado e como ele muda de aparência se estiver tocando em um holograma.</span><span class="sxs-lookup"><span data-stu-id="53e1e-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="53e1e-251">Instruções</span><span class="sxs-lookup"><span data-stu-id="53e1e-251">Instructions</span></span>

1. <span data-ttu-id="53e1e-252">No painel **hierarquia** , expanda o **AstroMan**->**GEO_G**->objeto **Back_Center** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="53e1e-253">Clique duas vezes em **Interactible.cs** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53e1e-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="53e1e-254">Remova os comentários das linhas nos retornos de chamada **IFocusable. OnFocusEnter ()** e **IFocusable. OnFocusExit ()** em **Interactible.cs**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="53e1e-255">Eles são chamados pelo InputManager do kit de ferramentas da realidade misturada quando o foco (por olhar ou por controlador apontando) entra e sai do colisor do Jogoobject específico.</span><span class="sxs-lookup"><span data-stu-id="53e1e-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="53e1e-256">Usamos `EnableKeyword` e `DisableKeyword` acima.</span><span class="sxs-lookup"><span data-stu-id="53e1e-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="53e1e-257">Para fazer uso deles em seu próprio aplicativo com o sombreador padrão do kit de ferramentas, você precisará seguir as [diretrizes do Unity para acessar materiais por meio de script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="53e1e-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="53e1e-258">Nesse caso, já incluímos as [três variantes do material realçado](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessário na pasta de recursos (procure os três materiais com realce no nome).</span><span class="sxs-lookup"><span data-stu-id="53e1e-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="53e1e-259">Compilar e implantar</span><span class="sxs-lookup"><span data-stu-id="53e1e-259">Build and Deploy</span></span>

1. <span data-ttu-id="53e1e-260">Como antes, compile o projeto e implante-o no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53e1e-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="53e1e-261">Observe o que acontece quando o olhar é direcionado a um objeto e quando não é.</span><span class="sxs-lookup"><span data-stu-id="53e1e-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="53e1e-262">Capítulo 3-técnicas de direcionamento</span><span class="sxs-lookup"><span data-stu-id="53e1e-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="53e1e-263">Objetivos</span><span class="sxs-lookup"><span data-stu-id="53e1e-263">Objectives</span></span>

* <span data-ttu-id="53e1e-264">Facilite o direcionamento de hologramas.</span><span class="sxs-lookup"><span data-stu-id="53e1e-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="53e1e-265">Estabilizar movimentos de cabeça natural.</span><span class="sxs-lookup"><span data-stu-id="53e1e-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="53e1e-266">Instruções</span><span class="sxs-lookup"><span data-stu-id="53e1e-266">Instructions</span></span>

1. <span data-ttu-id="53e1e-267">No painel **hierarquia** , selecione o objeto **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="53e1e-268">No painel **Inspetor** , localize o script de **estabilizador olhar** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="53e1e-269">Clique para abrir no Visual Studio, se você quiser dar uma olhada.</span><span class="sxs-lookup"><span data-stu-id="53e1e-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="53e1e-270">Esse script itera sobre exemplos de dados do Raycast e ajuda a estabilizar o olhar do usuário para direcionamento de precisão.</span><span class="sxs-lookup"><span data-stu-id="53e1e-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="53e1e-271">No **Inspetor**, você pode editar o valor das **amostras de estabilidade armazenadas** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-271">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="53e1e-272">Esse valor representa o número de amostras que o estabilizador itera para calcular o valor estabilizado.</span><span class="sxs-lookup"><span data-stu-id="53e1e-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="53e1e-273">Capítulo 4 – Indicador direcional</span><span class="sxs-lookup"><span data-stu-id="53e1e-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="53e1e-274">Objetivos</span><span class="sxs-lookup"><span data-stu-id="53e1e-274">Objectives</span></span>

* <span data-ttu-id="53e1e-275">Adicione um indicador direcional no cursor para ajudar a encontrar hologramas.</span><span class="sxs-lookup"><span data-stu-id="53e1e-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="53e1e-276">Instruções</span><span class="sxs-lookup"><span data-stu-id="53e1e-276">Instructions</span></span>

<span data-ttu-id="53e1e-277">Vamos usar o arquivo **DirectionIndicator.cs** , que:</span><span class="sxs-lookup"><span data-stu-id="53e1e-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="53e1e-278">Mostre o indicador direcional se o usuário não estiver nuvens nos hologramas.</span><span class="sxs-lookup"><span data-stu-id="53e1e-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="53e1e-279">Oculte o indicador direcional se o usuário estiver nuvensndo nos hologramas.</span><span class="sxs-lookup"><span data-stu-id="53e1e-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="53e1e-280">Atualize o indicador direcional para apontar para os hologramas.</span><span class="sxs-lookup"><span data-stu-id="53e1e-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="53e1e-281">Vamos começar.</span><span class="sxs-lookup"><span data-stu-id="53e1e-281">Let's get started.</span></span>

1. <span data-ttu-id="53e1e-282">Clique no objeto **AstroMan** no painel **hierarquia** e **clique na seta** para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="53e1e-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="53e1e-283">No painel **hierarquia** , selecione o objeto **DirectionalIndicator** em **AstroMan**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="53e1e-284">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="53e1e-285">No menu, digite o **indicador de direção**da caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="53e1e-285">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="53e1e-286">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="53e1e-286">Select the search result.</span></span>
5. <span data-ttu-id="53e1e-287">No painel **hierarquia** , arraste e solte o objeto **cursor** na propriedade **cursor** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="53e1e-288">No painel **projeto** , na pasta **hologramas** , arraste e solte o ativo **DirectionalIndicator** para a propriedade **Indicador direcional** no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="53e1e-289">Crie e implante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53e1e-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="53e1e-290">Observe como o objeto indicador direcional ajuda a localizar o Astronaut.</span><span class="sxs-lookup"><span data-stu-id="53e1e-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="53e1e-291">Capítulo 5 – mural</span><span class="sxs-lookup"><span data-stu-id="53e1e-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="53e1e-292">Objetivos</span><span class="sxs-lookup"><span data-stu-id="53e1e-292">Objectives</span></span>

* <span data-ttu-id="53e1e-293">Use a mensagem para que os hologramas sempre se enfrentem para você.</span><span class="sxs-lookup"><span data-stu-id="53e1e-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="53e1e-294">Usaremos o arquivo **Billboard.cs** para manter um gameobject orientado para que ele esteja sempre voltado ao usuário.</span><span class="sxs-lookup"><span data-stu-id="53e1e-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="53e1e-295">No painel **hierarquia** , selecione o objeto **AstroMan** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="53e1e-296">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="53e1e-297">No menu, digite o **mural**da caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="53e1e-297">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="53e1e-298">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="53e1e-298">Select the search result.</span></span>
4. <span data-ttu-id="53e1e-299">No **Inspetor** , defina o **eixo dinâmico** como **Y**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-299">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="53e1e-300">Experimente!</span><span class="sxs-lookup"><span data-stu-id="53e1e-300">Try it!</span></span> <span data-ttu-id="53e1e-301">Crie e implante o aplicativo como antes.</span><span class="sxs-lookup"><span data-stu-id="53e1e-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="53e1e-302">Veja como o objeto do mural o rostos não importa como você altera o ponto de vista.</span><span class="sxs-lookup"><span data-stu-id="53e1e-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="53e1e-303">Exclua o script do **AstroMan** por enquanto.</span><span class="sxs-lookup"><span data-stu-id="53e1e-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="53e1e-304">Capítulo 6-marcar como</span><span class="sxs-lookup"><span data-stu-id="53e1e-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="53e1e-305">Objetivos</span><span class="sxs-lookup"><span data-stu-id="53e1e-305">Objectives</span></span>

* <span data-ttu-id="53e1e-306">Use a marca – junto com nossos hologramas nos seguem pela sala.</span><span class="sxs-lookup"><span data-stu-id="53e1e-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="53e1e-307">À medida que trabalharmos com esse problema, iremos ser guiado pelas seguintes restrições de design:</span><span class="sxs-lookup"><span data-stu-id="53e1e-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="53e1e-308">O conteúdo deve ser sempre um breve resumido.</span><span class="sxs-lookup"><span data-stu-id="53e1e-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="53e1e-309">O conteúdo não deve estar no caminho.</span><span class="sxs-lookup"><span data-stu-id="53e1e-309">Content should not be in the way.</span></span>
* <span data-ttu-id="53e1e-310">O conteúdo de bloqueio de cabeça é desconfortável.</span><span class="sxs-lookup"><span data-stu-id="53e1e-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="53e1e-311">A solução usada aqui é usar uma abordagem de "marca".</span><span class="sxs-lookup"><span data-stu-id="53e1e-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="53e1e-312">Um objeto de marca-ao mesmo nunca deixa totalmente a exibição do usuário.</span><span class="sxs-lookup"><span data-stu-id="53e1e-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="53e1e-313">Você pode considerar uma marca como sendo um objeto anexado à cabeça do usuário por faixas de borracha.</span><span class="sxs-lookup"><span data-stu-id="53e1e-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="53e1e-314">À medida que o usuário se move, o conteúdo permanecerá dentro de uma visão fácil, deslizando para a borda da exibição sem sair completamente.</span><span class="sxs-lookup"><span data-stu-id="53e1e-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="53e1e-315">Quando o usuário gazes em direção ao objeto de marca, ele é mais totalmente na exibição.</span><span class="sxs-lookup"><span data-stu-id="53e1e-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="53e1e-316">Vamos usar o arquivo **SimpleTagalong.cs** , que:</span><span class="sxs-lookup"><span data-stu-id="53e1e-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="53e1e-317">Determine se o objeto de marca está dentro dos limites da câmera.</span><span class="sxs-lookup"><span data-stu-id="53e1e-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="53e1e-318">Se não estiver dentro da exibição frustum, posicione a marca-junto com parcialmente dentro da exibição frustum.</span><span class="sxs-lookup"><span data-stu-id="53e1e-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="53e1e-319">Caso contrário, posicione a marca-junto com uma distância padrão do usuário.</span><span class="sxs-lookup"><span data-stu-id="53e1e-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="53e1e-320">Para fazer isso, primeiro devemos alterar o script **Interactible.cs** para chamar o **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="53e1e-321">Edite **Interactible.cs** concluindo o código exercício 6. a (removendo as linhas de comentário 84 a 87).</span><span class="sxs-lookup"><span data-stu-id="53e1e-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="53e1e-322">O script **InteractibleAction.cs** , emparelhado com **Interactible.cs** , executa ações personalizadas quando você toca em hologramas.</span><span class="sxs-lookup"><span data-stu-id="53e1e-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="53e1e-323">Nesse caso, usaremos um especificamente para a marca.</span><span class="sxs-lookup"><span data-stu-id="53e1e-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="53e1e-324">Na pasta **scripts** , clique em ativo **TagalongAction.cs** para abrir no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53e1e-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="53e1e-325">Conclua o exercício de codificação ou altere-o para:</span><span class="sxs-lookup"><span data-stu-id="53e1e-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="53e1e-326">Na parte superior da **hierarquia**, na barra de pesquisa, digite **ChestButton_Center** e selecione o resultado.</span><span class="sxs-lookup"><span data-stu-id="53e1e-326">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="53e1e-327">No painel **Inspetor** , clique no botão **Adicionar componente** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="53e1e-328">No menu, digite a **ação que**da caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="53e1e-328">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="53e1e-329">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="53e1e-329">Select the search result.</span></span>
  * <span data-ttu-id="53e1e-330">Na pasta **hologramas** , localize o ativo **que** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="53e1e-331">Selecione o objeto **ChestButton_Center** na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="53e1e-331">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="53e1e-332">Arraste e solte o objeto **que** do painel **projeto** para o **Inspetor** na propriedade **objeto para que** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="53e1e-333">Arraste o objeto de **ação que** do **Inspetor** para o campo de **ação Interactible** no script **Interactible** .</span><span class="sxs-lookup"><span data-stu-id="53e1e-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="53e1e-334">Clique duas vezes no script **TagalongAction** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53e1e-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Configuração do Interactible](images/holograms210-interactible.png)

<span data-ttu-id="53e1e-336">Precisamos adicionar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="53e1e-336">We need to add the following:</span></span>

* <span data-ttu-id="53e1e-337">Adicione funcionalidade à função performaaction no script TagalongAction (Herdado de InteractibleAction).</span><span class="sxs-lookup"><span data-stu-id="53e1e-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="53e1e-338">Adicione a mensagem ao objeto gazed e defina o eixo dinâmico como XY.</span><span class="sxs-lookup"><span data-stu-id="53e1e-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="53e1e-339">Em seguida, adicione uma marca simples-junto ao objeto.</span><span class="sxs-lookup"><span data-stu-id="53e1e-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="53e1e-340">Aqui está nossa solução, de **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="53e1e-340">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="53e1e-341">Experimente!</span><span class="sxs-lookup"><span data-stu-id="53e1e-341">Try it!</span></span> <span data-ttu-id="53e1e-342">Crie e implante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53e1e-342">Build and deploy the app.</span></span>
* <span data-ttu-id="53e1e-343">Observe como o conteúdo segue o centro do ponto de olhar, mas não continuamente e sem bloqueá-lo.</span><span class="sxs-lookup"><span data-stu-id="53e1e-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>

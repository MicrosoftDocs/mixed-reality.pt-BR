---
title: Entrada MR 210 - olhar
description: Siga este passo a passo usando o Unity, o Visual Studio e o HoloLens para saber os detalhes de olhar conceitos de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gaze
ms.openlocfilehash: 63c55e8a7a348f2a3e0cc29a9795d7fabcef5df0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589447"
---
>[!NOTE]
><span data-ttu-id="5c45b-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="5c45b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5c45b-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5c45b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5c45b-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="5c45b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5c45b-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="5c45b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5c45b-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5c45b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5c45b-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="5c45b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="5c45b-110">Entrada MR 210: Focar</span><span class="sxs-lookup"><span data-stu-id="5c45b-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="5c45b-111">[Mantenha o foco](gaze.md) é o primeiro formulário de entrada e revela a intenção do usuário e o reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="5c45b-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="5c45b-112">MR entrada 210 (também conhecido como o Explorador de projeto) é uma Visão aprofundada conceitos relacionados ao olhar para a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="5c45b-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="5c45b-113">Vamos adicionar reconhecimento contextual para nosso cursor e hologramas, aproveitando ao máximo o que seu aplicativo sabe sobre olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="5c45b-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="5c45b-114">Temos um astronaut amigável aqui para ajudá-lo a aprender os conceitos de olhar.</span><span class="sxs-lookup"><span data-stu-id="5c45b-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="5c45b-115">Na [MR Noções básicas de 101](holograms-101.md), tínhamos um cursor simple que acabou de acessar seu foco.</span><span class="sxs-lookup"><span data-stu-id="5c45b-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="5c45b-116">Hoje estamos movendo um passo além, o cursor simple:</span><span class="sxs-lookup"><span data-stu-id="5c45b-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="5c45b-117">Estamos disponibilizando o cursor e nossa hologramas reconhecimento de olhar: ambos serão alteradas com base em onde o usuário está procurando - ou onde o usuário está *não* procurando.</span><span class="sxs-lookup"><span data-stu-id="5c45b-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="5c45b-118">Isso os torna sensíveis ao contexto.</span><span class="sxs-lookup"><span data-stu-id="5c45b-118">This makes them context-aware.</span></span>
* <span data-ttu-id="5c45b-119">Vamos adicionar comentários ao nosso cursor e hologramas dar mais contexto sobre o que está sendo direcionado ao usuário.</span><span class="sxs-lookup"><span data-stu-id="5c45b-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="5c45b-120">Esses comentários podem ser áudio e vídeo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="5c45b-121">Mostraremos as técnicas de direcionamento para ajudar os usuários a atingir as metas menores.</span><span class="sxs-lookup"><span data-stu-id="5c45b-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="5c45b-122">Mostraremos a você como chamar a atenção do usuário para seu hologramas com um indicador direcional.</span><span class="sxs-lookup"><span data-stu-id="5c45b-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="5c45b-123">Podemos ensinam técnicas para aproveitar seu hologramas com o usuário conforme ela se move em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5c45b-124">Os vídeos incorporados em cada um dos capítulos a seguir foram registrados usando uma versão mais antiga do Unity e o Kit de ferramentas de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="5c45b-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="5c45b-125">Enquanto as instruções passo a passo são precisas e atuais, você poderá ver scripts e visuais nos vídeos correspondentes que estão desatualizados.</span><span class="sxs-lookup"><span data-stu-id="5c45b-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="5c45b-126">Os vídeos permanecem incluídos serão lidas depois e porque os conceitos abordados ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="5c45b-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="5c45b-127">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="5c45b-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5c45b-128">Curso</span><span class="sxs-lookup"><span data-stu-id="5c45b-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5c45b-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5c45b-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5c45b-130"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="5c45b-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5c45b-131">Entrada MR 210: Focar</span><span class="sxs-lookup"><span data-stu-id="5c45b-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="5c45b-132">✔️</span><span class="sxs-lookup"><span data-stu-id="5c45b-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5c45b-133">✔️</span><span class="sxs-lookup"><span data-stu-id="5c45b-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5c45b-134">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="5c45b-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5c45b-135">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5c45b-135">Prerequisites</span></span>

* <span data-ttu-id="5c45b-136">Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5c45b-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="5c45b-137">Alguns basic C# capacidade de programação.</span><span class="sxs-lookup"><span data-stu-id="5c45b-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="5c45b-138">Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="5c45b-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="5c45b-139">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="5c45b-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="5c45b-140">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="5c45b-140">Project files</span></span>

* <span data-ttu-id="5c45b-141">Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="5c45b-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="5c45b-142"> Requer o Unity 2017.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="5c45b-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="5c45b-143">Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.</span><span class="sxs-lookup"><span data-stu-id="5c45b-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="5c45b-144">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="5c45b-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="5c45b-145">Errata e notas</span><span class="sxs-lookup"><span data-stu-id="5c45b-145">Errata and Notes</span></span>

* <span data-ttu-id="5c45b-146">No Visual Studio, "Apenas meu código" precisa ser desabilitado (desmarcado) em Ferramentas -> Opções -> depuração para usar pontos de interrupção em seu código.</span><span class="sxs-lookup"><span data-stu-id="5c45b-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="5c45b-147">Capítulo 1 - instalação do Unity</span><span class="sxs-lookup"><span data-stu-id="5c45b-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="5c45b-148">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5c45b-148">Objectives</span></span>

* <span data-ttu-id="5c45b-149">Otimize o Unity para o desenvolvimento HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5c45b-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="5c45b-150">Importar ativos e configurar a cena.</span><span class="sxs-lookup"><span data-stu-id="5c45b-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="5c45b-151">Exiba a astronautas no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5c45b-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="5c45b-152">Instruções</span><span class="sxs-lookup"><span data-stu-id="5c45b-152">Instructions</span></span>

1. <span data-ttu-id="5c45b-153">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="5c45b-153">Start Unity.</span></span>
2. <span data-ttu-id="5c45b-154">Selecione **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-154">Select **New Project**.</span></span>
3. <span data-ttu-id="5c45b-155">Nomeie o projeto **ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="5c45b-156">Insira o local como o **olhares** pasta você anteriormente não arquivadas.</span><span class="sxs-lookup"><span data-stu-id="5c45b-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="5c45b-157">Verifique se o projeto é definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="5c45b-158">Clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="5c45b-159">Configurações do Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="5c45b-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="5c45b-160">Precisamos informar Unity que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D.</span><span class="sxs-lookup"><span data-stu-id="5c45b-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="5c45b-161">Fazemos isso adicionando o HoloLens como um dispositivo de realidade virtual.</span><span class="sxs-lookup"><span data-stu-id="5c45b-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="5c45b-162">Vá para **Editar > configurações do projeto > Player**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="5c45b-163">No **painel Inspetor** para configurações do Player, selecione o **Windows Store** ícone.</span><span class="sxs-lookup"><span data-stu-id="5c45b-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="5c45b-164">Expanda o **XR configurações** grupo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="5c45b-165">No **renderização** seção, verifique os **suporte de realidade Virtual** caixa de seleção para adicionar uma nova **SDKs de realidade Virtual** lista.</span><span class="sxs-lookup"><span data-stu-id="5c45b-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="5c45b-166">Verifique **Windows Mixed Reality** aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="5c45b-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="5c45b-167">Se não estiver, selecione a **+** botão na parte inferior da lista e escolha **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="5c45b-168">Em seguida, precisamos definir o nosso script back-end para o .NET.</span><span class="sxs-lookup"><span data-stu-id="5c45b-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="5c45b-169">Vá para **Editar > configurações do projeto > Player** (você ainda poderá ter esse da etapa anterior).</span><span class="sxs-lookup"><span data-stu-id="5c45b-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="5c45b-170">No **painel Inspetor** para configurações do Player, selecione o **Windows Store** ícone.</span><span class="sxs-lookup"><span data-stu-id="5c45b-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="5c45b-171">No **outras configurações** configuração de seção, certifique-se de que **back-end de script** é definido como **.NET**</span><span class="sxs-lookup"><span data-stu-id="5c45b-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="5c45b-172">Por fim, atualizaremos nossas configurações de qualidade para alcançar um desempenho rápido em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5c45b-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="5c45b-173">Vá para **Editar > configurações do projeto > qualidade**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="5c45b-174">Clique na seta apontando para baixo na **padrão** linha sob o ícone do Windows Store.</span><span class="sxs-lookup"><span data-stu-id="5c45b-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="5c45b-175">Selecione **mais rápido** para **aplicativos da Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-175">Select **Fastest** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="5c45b-176">Importar ativos do projeto</span><span class="sxs-lookup"><span data-stu-id="5c45b-176">Import project assets</span></span>

1. <span data-ttu-id="5c45b-177">Clique com botão direito do **ativos** pasta na **projeto** painel.</span><span class="sxs-lookup"><span data-stu-id="5c45b-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="5c45b-178">Clique em **Importar pacote > pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="5c45b-179">Navegue até os arquivos de projeto que você baixou e clique em **ModelExplorer.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="5c45b-180">Clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-180">Click **Open**.</span></span>
5. <span data-ttu-id="5c45b-181">Depois que o pacote é carregado, clique no **importação** botão.</span><span class="sxs-lookup"><span data-stu-id="5c45b-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="5c45b-182">Instalação da cena</span><span class="sxs-lookup"><span data-stu-id="5c45b-182">Setup the scene</span></span>

1. <span data-ttu-id="5c45b-183">Na hierarquia, exclua o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="5c45b-184">No **HoloToolkit** pasta, abra o **entrada** pasta, em seguida, abra o **pré-fabricados** pasta.</span><span class="sxs-lookup"><span data-stu-id="5c45b-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="5c45b-185">Arrastar e soltar a **MixedRealityCameraParent** pré-fabricado da **pré-fabricados** pasta para o **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="5c45b-186">Clique com botão direito do **luz direcional** na hierarquia e selecione **excluir**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="5c45b-187">No **hologramas** pasta, arraste e solte os seguintes ativos na raiz do **hierarquia**:</span><span class="sxs-lookup"><span data-stu-id="5c45b-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="5c45b-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="5c45b-188">**AstroMan**</span></span>
    * <span data-ttu-id="5c45b-189">**luzes**</span><span class="sxs-lookup"><span data-stu-id="5c45b-189">**Lights**</span></span>
    * <span data-ttu-id="5c45b-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="5c45b-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="5c45b-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="5c45b-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="5c45b-192">Inicie **reproduzir modo** ▶ para exibir a astronautas.</span><span class="sxs-lookup"><span data-stu-id="5c45b-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="5c45b-193">Clique em **modo de reprodução** ▶ novamente para **parar**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="5c45b-194">No **hologramas** pasta, localizar o **Fitbox** ativo e arraste-o para a raiz do **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="5c45b-195">Selecione o **Fitbox** na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="5c45b-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="5c45b-196">Arraste o **AstroMan** coleção da **hierarquia** para o **holograma coleção** o Fitbox na propriedade o **Inspetor** painel.</span><span class="sxs-lookup"><span data-stu-id="5c45b-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="5c45b-197">Salve o projeto</span><span class="sxs-lookup"><span data-stu-id="5c45b-197">Save the project</span></span>

1. <span data-ttu-id="5c45b-198">Salve a nova cena: **Arquivo > Salvar cena como**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="5c45b-199">Clique em **nova pasta** e nomeie a pasta **cenas**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="5c45b-200">Nomeie o arquivo "**ModelExplorer**" e salve-o na **cenas** pasta.</span><span class="sxs-lookup"><span data-stu-id="5c45b-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="5c45b-201">Compile o projeto</span><span class="sxs-lookup"><span data-stu-id="5c45b-201">Build the project</span></span>

1. <span data-ttu-id="5c45b-202">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="5c45b-203">Clique em **cenas abra Adicionar** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="5c45b-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="5c45b-204">Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="5c45b-205">Se você estiver desenvolvendo especificamente para HoloLens, defina **dispositivo de destino** à **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="5c45b-206">Caso contrário, deixe-nos **qualquer dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="5c45b-207">Certifique-se **Build Type** é definido como **D3D** e **SDK** é definido como **mais recente instalada** (que deve ser SDK 16299 ou mais recente).</span><span class="sxs-lookup"><span data-stu-id="5c45b-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="5c45b-208">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-208">Click **Build**.</span></span>
7. <span data-ttu-id="5c45b-209">Criar uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="5c45b-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="5c45b-210">Único clique a **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="5c45b-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="5c45b-211">Pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-211">Press **Select Folder**.</span></span>

<span data-ttu-id="5c45b-212">Quando Unity é feito, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="5c45b-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="5c45b-213">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="5c45b-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="5c45b-214">Abra o **ModelExplorer Visual Studio Solution**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="5c45b-215">Se a implantação para o HoloLens:</span><span class="sxs-lookup"><span data-stu-id="5c45b-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="5c45b-216">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="5c45b-217">Clique na lista suspensa na seta ao lado do botão de computador Local e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="5c45b-218">Insira **seu endereço IP do dispositivo HoloLens** e defina o modo de autenticação como **Universal (protocolo não criptografado)**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="5c45b-219">Clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-219">Click **Select**.</span></span> <span data-ttu-id="5c45b-220">Se você não souber o endereço IP do dispositivo, examine **Configurações > rede e Internet > Opções avançadas de**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="5c45b-221">Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="5c45b-222">Se essa for a primeira vez em que implantar seu dispositivo, você precisará [emparelhá-lo com o Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="5c45b-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="5c45b-223">Quando o aplicativo foi implantado, ignorar as **Fitbox** com um **selecione gesto**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="5c45b-224">Se implantar em um fone de ouvido imersivo:</span><span class="sxs-lookup"><span data-stu-id="5c45b-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="5c45b-225">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="5c45b-226">Verifique se o destino de implantação é definido como **computador Local**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="5c45b-227">Na barra de menus superior, clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="5c45b-228">Quando o aplicativo foi implantado, ignorar as **Fitbox** puxando o gatilho em um controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="5c45b-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="5c45b-229">Capítulo 2 - comentários do Cursor e de destino</span><span class="sxs-lookup"><span data-stu-id="5c45b-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="5c45b-230">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5c45b-230">Objectives</span></span>

* <span data-ttu-id="5c45b-231">Design visual do cursor e o comportamento.</span><span class="sxs-lookup"><span data-stu-id="5c45b-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="5c45b-232">Comentários de cursor com base em olhar.</span><span class="sxs-lookup"><span data-stu-id="5c45b-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="5c45b-233">Comentários de holograma com base em olhar.</span><span class="sxs-lookup"><span data-stu-id="5c45b-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="5c45b-234">Vamos basear nosso trabalho sobre alguns princípios de design de cursor, ou seja:</span><span class="sxs-lookup"><span data-stu-id="5c45b-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="5c45b-235">O cursor está sempre presente.</span><span class="sxs-lookup"><span data-stu-id="5c45b-235">The cursor is always present.</span></span>
* <span data-ttu-id="5c45b-236">Não deixe que o cursor obter muito pequeno ou grande.</span><span class="sxs-lookup"><span data-stu-id="5c45b-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="5c45b-237">Evite obstruindo o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="5c45b-238">Instruções</span><span class="sxs-lookup"><span data-stu-id="5c45b-238">Instructions</span></span>

1. <span data-ttu-id="5c45b-239">No **HoloToolkit\Input\Prefabs** pasta, localize a **InputManager** ativo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="5c45b-240">Arraste e solte os **InputManager** até a **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="5c45b-241">No **HoloToolkit\Input\Prefabs** pasta, localize a **Cursor** ativo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="5c45b-242">Arraste e solte os **Cursor** até a **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="5c45b-243">Selecione o **InputManager** do objeto na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="5c45b-244">Arraste o **Cursor** do objeto da **hierarquia** no InputManager **SimpleSinglePointerSelector**do **Cursor** no campo a parte inferior da **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Simples de configurar seletor único de ponteiro](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="5c45b-246">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="5c45b-246">Build and Deploy</span></span>

1. <span data-ttu-id="5c45b-247">Recompile o aplicativo do **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="5c45b-248">Abra o **pasta aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="5c45b-249">Abra o **ModelExplorer Visual Studio Solution**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="5c45b-250">Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="5c45b-251">Observe como o cursor é desenhado, e como ela altera a aparência se ele está tocando um holograma.</span><span class="sxs-lookup"><span data-stu-id="5c45b-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="5c45b-252">Instruções</span><span class="sxs-lookup"><span data-stu-id="5c45b-252">Instructions</span></span>

1. <span data-ttu-id="5c45b-253">No **hierarquia** do painel, expanda o **AstroMan**->**GEO_G**->**Back_Center** objeto.</span><span class="sxs-lookup"><span data-stu-id="5c45b-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="5c45b-254">Clique duas vezes em **Interactible.cs** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c45b-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="5c45b-255">Remova as linhas as **IFocusable.OnFocusEnter()** e **IFocusable.OnFocusExit()** retornos de chamada no **Interactible.cs**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="5c45b-256">Eles são chamados pelo InputManager do Toolkit de realidade misturada quando foco (seja por olhar ou apontando controlador) entra e sai do colisor do GameObject específico.</span><span class="sxs-lookup"><span data-stu-id="5c45b-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="5c45b-257">Usamos `EnableKeyword` e `DisableKeyword` acima.</span><span class="sxs-lookup"><span data-stu-id="5c45b-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="5c45b-258">Para fazer uso deles em seu próprio aplicativo com o sombreador de padrão do Kit de ferramentas, você precisará seguir as [diretrizes do Unity para acessar os materiais por meio de script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span><span class="sxs-lookup"><span data-stu-id="5c45b-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="5c45b-259">Nesse caso, estamos já incluiu o [três variantes do material realçado](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necessários na pasta de recursos (procure os materiais com realce o nome de três).</span><span class="sxs-lookup"><span data-stu-id="5c45b-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="5c45b-260">Criar e implantar</span><span class="sxs-lookup"><span data-stu-id="5c45b-260">Build and Deploy</span></span>

1. <span data-ttu-id="5c45b-261">Como antes, compile o projeto e implantar para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5c45b-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="5c45b-262">Observar o que acontece quando a olhar destina-se a um objeto e quando ele não é.</span><span class="sxs-lookup"><span data-stu-id="5c45b-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="5c45b-263">Capítulo 3 - técnicas de direcionamento</span><span class="sxs-lookup"><span data-stu-id="5c45b-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="5c45b-264">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5c45b-264">Objectives</span></span>

* <span data-ttu-id="5c45b-265">Torna mais fácil hologramas de destino.</span><span class="sxs-lookup"><span data-stu-id="5c45b-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="5c45b-266">Estabilize naturais movimentos principais.</span><span class="sxs-lookup"><span data-stu-id="5c45b-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="5c45b-267">Instruções</span><span class="sxs-lookup"><span data-stu-id="5c45b-267">Instructions</span></span>

1. <span data-ttu-id="5c45b-268">No **hierarquia** painel, selecione o **InputManager** objeto.</span><span class="sxs-lookup"><span data-stu-id="5c45b-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="5c45b-269">No **Inspector** do painel, localize a **olhares estabilizador** script.</span><span class="sxs-lookup"><span data-stu-id="5c45b-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="5c45b-270">Clique para abrir no Visual Studio, se você quiser dar uma olhada.</span><span class="sxs-lookup"><span data-stu-id="5c45b-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="5c45b-271">Esse script itera em amostras de dados Raycast e ajuda a se estabilizar olhar do usuário para o direcionamento de precisão.</span><span class="sxs-lookup"><span data-stu-id="5c45b-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="5c45b-272">No **Inspector**, você pode editar o **amostras de estabilidade armazenados** valor.</span><span class="sxs-lookup"><span data-stu-id="5c45b-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="5c45b-273">Esse valor representa o número de amostras que itera o estabilizador para calcular o valor estabilizar.</span><span class="sxs-lookup"><span data-stu-id="5c45b-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="5c45b-274">Capítulo 4 - indicadores direcionais</span><span class="sxs-lookup"><span data-stu-id="5c45b-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="5c45b-275">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5c45b-275">Objectives</span></span>

* <span data-ttu-id="5c45b-276">Adicione um indicador direcional no cursor para ajudar a localizar hologramas.</span><span class="sxs-lookup"><span data-stu-id="5c45b-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="5c45b-277">Instruções</span><span class="sxs-lookup"><span data-stu-id="5c45b-277">Instructions</span></span>

<span data-ttu-id="5c45b-278">Vamos usar o **DirectionIndicator.cs** arquivo que será:</span><span class="sxs-lookup"><span data-stu-id="5c45b-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="5c45b-279">Mostra os indicadores direcionais se o usuário não é Observação nas hologramas.</span><span class="sxs-lookup"><span data-stu-id="5c45b-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="5c45b-280">Oculte os indicadores direcionais, se o usuário é Observação nas hologramas.</span><span class="sxs-lookup"><span data-stu-id="5c45b-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="5c45b-281">Atualize os indicadores direcionais para apontar para as hologramas.</span><span class="sxs-lookup"><span data-stu-id="5c45b-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="5c45b-282">Vamos começar.</span><span class="sxs-lookup"><span data-stu-id="5c45b-282">Let's get started.</span></span>

1. <span data-ttu-id="5c45b-283">Clique no **AstroMan** do objeto na **hierarquia** painel e **clique na seta** para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="5c45b-284">No **hierarquia** painel, selecione o **DirectionalIndicator** objeto sob **AstroMan**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="5c45b-285">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="5c45b-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="5c45b-286">No menu, digite na caixa de pesquisa **indicador de direção**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="5c45b-287">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5c45b-287">Select the search result.</span></span>
5. <span data-ttu-id="5c45b-288">No **hierarquia** do painel, arraste e solte o **Cursor** do objeto para o **Cursor** propriedade no **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="5c45b-289">No **projeto** painel, o **hologramas** pasta, arrastar e soltar os **DirectionalIndicator** ativo para o **indicadores direcionais**propriedade de **Inspetor**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="5c45b-290">Crie e implante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="5c45b-291">Assista como o objeto de indicadores direcionais ajuda a encontrar o astronaut.</span><span class="sxs-lookup"><span data-stu-id="5c45b-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="5c45b-292">Capítulo 5 - Billboarding</span><span class="sxs-lookup"><span data-stu-id="5c45b-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="5c45b-293">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5c45b-293">Objectives</span></span>

* <span data-ttu-id="5c45b-294">Use billboarding ter hologramas sempre enfrentam na sua direção.</span><span class="sxs-lookup"><span data-stu-id="5c45b-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="5c45b-295">Vamos usar o **Billboard.cs** arquivo para manter um GameObject orientado a, de modo que ele é voltado para o usuário em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="5c45b-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="5c45b-296">No **hierarquia** painel, selecione o **AstroMan** objeto.</span><span class="sxs-lookup"><span data-stu-id="5c45b-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="5c45b-297">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="5c45b-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="5c45b-298">No menu, digite na caixa de pesquisa **mural**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="5c45b-299">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5c45b-299">Select the search result.</span></span>
4. <span data-ttu-id="5c45b-300">No **Inspector** definir os **eixo pivô** para **Y**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="5c45b-301">Experimente!</span><span class="sxs-lookup"><span data-stu-id="5c45b-301">Try it!</span></span> <span data-ttu-id="5c45b-302">Crie e implante o aplicativo como antes.</span><span class="sxs-lookup"><span data-stu-id="5c45b-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="5c45b-303">Veja como o objeto mural faces, independentemente de como você pode alterar o ponto de vista.</span><span class="sxs-lookup"><span data-stu-id="5c45b-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="5c45b-304">Excluir o script a partir de **AstroMan** por enquanto.</span><span class="sxs-lookup"><span data-stu-id="5c45b-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="5c45b-305">Capítulos 6 - Tag-Along</span><span class="sxs-lookup"><span data-stu-id="5c45b-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="5c45b-306">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5c45b-306">Objectives</span></span>

* <span data-ttu-id="5c45b-307">Use Tag-Along para nosso hologramas Siga-nos em torno da sala.</span><span class="sxs-lookup"><span data-stu-id="5c45b-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="5c45b-308">Enquanto trabalhamos sobre esse problema, podemos serão guiados pelas seguintes restrições de design:</span><span class="sxs-lookup"><span data-stu-id="5c45b-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="5c45b-309">O conteúdo sempre deve ser rapidamente imediatamente.</span><span class="sxs-lookup"><span data-stu-id="5c45b-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="5c45b-310">Conteúdo não deve ser da forma.</span><span class="sxs-lookup"><span data-stu-id="5c45b-310">Content should not be in the way.</span></span>
* <span data-ttu-id="5c45b-311">O conteúdo de bloqueio de cabeça é desconfortável.</span><span class="sxs-lookup"><span data-stu-id="5c45b-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="5c45b-312">A solução usada aqui é usar uma abordagem de "tag-along".</span><span class="sxs-lookup"><span data-stu-id="5c45b-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="5c45b-313">Um objeto tag-along nunca totalmente sai do modo de exibição do usuário.</span><span class="sxs-lookup"><span data-stu-id="5c45b-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="5c45b-314">Você pode considerar a um tag-along como sendo um objeto anexado a cabeça do usuário por elásticos.</span><span class="sxs-lookup"><span data-stu-id="5c45b-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="5c45b-315">Quando o usuário move, o conteúdo permanecerá em um relance fácil deslizando em direção à extremidade da exibição sem sair completamente.</span><span class="sxs-lookup"><span data-stu-id="5c45b-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="5c45b-316">Quando o usuário gazes para o objeto tag-along, se trata mais detalhadamente no modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="5c45b-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="5c45b-317">Vamos usar o **SimpleTagalong.cs** arquivo que será:</span><span class="sxs-lookup"><span data-stu-id="5c45b-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="5c45b-318">Determine se o objeto Tag-Along está dentro dos limites de câmera.</span><span class="sxs-lookup"><span data-stu-id="5c45b-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="5c45b-319">Se não estiver na frustum modo de exibição, posicionar o Tag-Along para parcialmente na frustum modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="5c45b-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="5c45b-320">Caso contrário, posicione o Tag-Along para uma distância padrão do usuário.</span><span class="sxs-lookup"><span data-stu-id="5c45b-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="5c45b-321">Para fazer isso, podemos primeiro deve alterar o **Interactible.cs** script para chamar o **TagalongAction**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="5c45b-322">Edite **Interactible.cs** ao concluir a codificação Exercício 6.a (linhas 1&gt;{2&gt;suporte 84 para 87).</span><span class="sxs-lookup"><span data-stu-id="5c45b-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="5c45b-323">O **InteractibleAction.cs** script, emparelhado com **Interactible.cs** executa ações personalizadas quando você toca em hologramas.</span><span class="sxs-lookup"><span data-stu-id="5c45b-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="5c45b-324">Nesse caso, usaremos um especificamente para tag-along.</span><span class="sxs-lookup"><span data-stu-id="5c45b-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="5c45b-325">No **Scripts** pasta clique em **TagalongAction.cs** ativo para abrir no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c45b-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="5c45b-326">Concluir o exercício de codificação ou alterá-la a este:</span><span class="sxs-lookup"><span data-stu-id="5c45b-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="5c45b-327">Na parte superior do **hierarquia**, no tipo de barra de pesquisa **ChestButton_Center** e selecione o resultado.</span><span class="sxs-lookup"><span data-stu-id="5c45b-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="5c45b-328">No **Inspector** do painel, clique no **adicionar componente** botão.</span><span class="sxs-lookup"><span data-stu-id="5c45b-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="5c45b-329">No menu, digite na caixa de pesquisa **que ação**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="5c45b-330">Selecione o resultado da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5c45b-330">Select the search result.</span></span>
  * <span data-ttu-id="5c45b-331">Na **hologramas** localizar pasta o ativo. \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5c45b-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="5c45b-332">Selecione o **ChestButton_Center** do objeto na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="5c45b-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="5c45b-333">Arrastar e soltar o  do objeto do **projeto** do painel para o **Inspetor** no **objeto** a que propriedade. \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="5c45b-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="5c45b-334">Arraste o **que ação** do objeto do **Inspetor** no **ação Interactible** campo o **Interactible** script.</span><span class="sxs-lookup"><span data-stu-id="5c45b-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="5c45b-335">Clique duas vezes o **TagalongAction** script para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c45b-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Configuração interactible](images/holograms210-interactible.png)

<span data-ttu-id="5c45b-337">Precisamos adicionar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5c45b-337">We need to add the following:</span></span>

* <span data-ttu-id="5c45b-338">Adicione funcionalidade à função PerformAction no script TagalongAction (herdado de InteractibleAction).</span><span class="sxs-lookup"><span data-stu-id="5c45b-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="5c45b-339">Adicione billboarding ao objeto gazed após e defina o eixo pivô para XY.</span><span class="sxs-lookup"><span data-stu-id="5c45b-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="5c45b-340">Em seguida, adicione Tag-Along simple para o objeto.</span><span class="sxs-lookup"><span data-stu-id="5c45b-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="5c45b-341">Aqui está nossa solução, de **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="5c45b-341">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="5c45b-342">Experimente!</span><span class="sxs-lookup"><span data-stu-id="5c45b-342">Try it!</span></span> <span data-ttu-id="5c45b-343">Crie e implante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c45b-343">Build and deploy the app.</span></span>
* <span data-ttu-id="5c45b-344">Assista como o conteúdo segue o centro do ponto de olhar, mas não é continuamente e sem bloquear a ele.</span><span class="sxs-lookup"><span data-stu-id="5c45b-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>

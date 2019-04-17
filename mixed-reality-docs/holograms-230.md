---
title: MR espacial 230 - mapeamento espacial
description: Siga este passo a passo usando o Unity, o Visual Studio e o HoloLens para saber os detalhes dos conceitos de mapeamento espacial de codificação.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, mapeamento espacial, superfície reconstrução, malha
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589757"
---
>[!NOTE]
><span data-ttu-id="94161-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="94161-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="94161-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="94161-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="94161-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="94161-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="94161-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="94161-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="94161-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="94161-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="94161-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="94161-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="94161-110">MR Spatial 230: Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="94161-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="94161-111">[Mapeamento espacial](spatial-mapping.md) combina o mundo real e o mundo virtual ensinando hologramas sobre o ambiente.</span><span class="sxs-lookup"><span data-stu-id="94161-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="94161-112">Em MR espacial 230 (projeto Planetarium), você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="94161-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="94161-113">Verificar os dados de ambiente e transferência do HoloLens para seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="94161-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="94161-114">Explore sombreadores e saiba como usá-las para visualizar seu espaço.</span><span class="sxs-lookup"><span data-stu-id="94161-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="94161-115">Divida a malha de sala em planos simples usando o processamento de malha.</span><span class="sxs-lookup"><span data-stu-id="94161-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="94161-116">Vá além das técnicas de posicionamento que aprendemos [MR Noções básicas de 101](holograms-101.md)e fornecer comentários sobre onde um holograma pode ser colocado no ambiente.</span><span class="sxs-lookup"><span data-stu-id="94161-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="94161-117">Explore os efeitos de oclusão, portanto, quando seu holograma estiver atrás de um objeto do mundo real, você ainda poderá observá-la com a visão de raios-x!</span><span class="sxs-lookup"><span data-stu-id="94161-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="94161-118">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="94161-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="94161-119">Curso</span><span class="sxs-lookup"><span data-stu-id="94161-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="94161-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="94161-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="94161-121"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="94161-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="94161-122">MR Spatial 230: Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="94161-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="94161-123">✔️</span><span class="sxs-lookup"><span data-stu-id="94161-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="94161-124">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="94161-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="94161-125">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="94161-125">Prerequisites</span></span>

* <span data-ttu-id="94161-126">Um computador com Windows 10 configurado com o nome correto [as ferramentas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="94161-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="94161-127">Alguns basic C# capacidade de programação.</span><span class="sxs-lookup"><span data-stu-id="94161-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="94161-128">Você deve ter concluído [MR Noções básicas de 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="94161-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="94161-129">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="94161-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="94161-130">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="94161-130">Project files</span></span>

* <span data-ttu-id="94161-131">Baixe o [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="94161-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="94161-132"> Requer o Unity 2017.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="94161-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="94161-133">Se você ainda precisar de suporte do Unity 5.6, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="94161-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="94161-134">Se você ainda precisar de suporte do Unity 5.5, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="94161-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="94161-135">Se você ainda precisar de suporte de Unity 5.4, use [nesta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="94161-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="94161-136">Cancelar arquivar os arquivos para sua área de trabalho ou outros fáceis de alcançar o local.</span><span class="sxs-lookup"><span data-stu-id="94161-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="94161-137">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="94161-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="94161-138">Observações</span><span class="sxs-lookup"><span data-stu-id="94161-138">Notes</span></span>

* <span data-ttu-id="94161-139">"Habilitar apenas meu código" no Visual Studio precisa ser desabilitado (*desmarcado*) em Ferramentas > Opções > depuração para usar pontos de interrupção em seu código.</span><span class="sxs-lookup"><span data-stu-id="94161-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="94161-140">Instalação do Unity</span><span class="sxs-lookup"><span data-stu-id="94161-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="94161-141">Inicie **Unity**.</span><span class="sxs-lookup"><span data-stu-id="94161-141">Start **Unity**.</span></span>
* <span data-ttu-id="94161-142">Selecione **New** para criar um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="94161-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="94161-143">Nomeie o projeto **Planetarium**.</span><span class="sxs-lookup"><span data-stu-id="94161-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="94161-144">Verifique se que o **3D** configuração é selecionada.</span><span class="sxs-lookup"><span data-stu-id="94161-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="94161-145">Clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="94161-145">Click **Create Project**.</span></span>
* <span data-ttu-id="94161-146">Depois que o Unity é iniciado, vá para **Editar > configurações do projeto > Player**.</span><span class="sxs-lookup"><span data-stu-id="94161-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="94161-147">No **Inspector** do painel, localize e selecione o verde **Windows Store** ícone.</span><span class="sxs-lookup"><span data-stu-id="94161-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="94161-148">Expandir **outras configurações**.</span><span class="sxs-lookup"><span data-stu-id="94161-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="94161-149">No **renderização** seção, verifique os **suporte de realidade Virtual** opção.</span><span class="sxs-lookup"><span data-stu-id="94161-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="94161-150">Verifique **Windows Holographic** aparece na lista de **SDKs de realidade Virtual**.</span><span class="sxs-lookup"><span data-stu-id="94161-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="94161-151">Se não estiver, selecione a **+** botão na parte inferior da lista e escolha **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="94161-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="94161-152">Expandir **configurações de publicação**.</span><span class="sxs-lookup"><span data-stu-id="94161-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="94161-153">No **recursos** seção, verifique as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="94161-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="94161-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="94161-154">InternetClientServer</span></span>
    * <span data-ttu-id="94161-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="94161-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="94161-156">Microfone</span><span class="sxs-lookup"><span data-stu-id="94161-156">Microphone</span></span>
    * <span data-ttu-id="94161-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="94161-157">SpatialPerception</span></span>
* <span data-ttu-id="94161-158">Vá para **Editar > configurações do projeto > qualidade**</span><span class="sxs-lookup"><span data-stu-id="94161-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="94161-159">No **Inspector** do painel, sob o ícone do Windows Store, selecione a seta suspensa preta sob a linha de 'Default' e altere a configuração padrão para **mais rápido**.</span><span class="sxs-lookup"><span data-stu-id="94161-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Fastest**.</span></span>
* <span data-ttu-id="94161-160">Vá para **ativos > Importar pacote > pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="94161-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="94161-161">Navegue até a **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** pasta.</span><span class="sxs-lookup"><span data-stu-id="94161-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="94161-162">Clique em **Planetarium.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="94161-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="94161-163">Clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="94161-163">Click **Open**.</span></span>
* <span data-ttu-id="94161-164">Uma **Importar pacote do Unity** janela deve ser exibida, clique no **importação** botão.</span><span class="sxs-lookup"><span data-stu-id="94161-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="94161-165">Aguarde até que o Unity importar todos os ativos de que precisamos para concluir este projeto.</span><span class="sxs-lookup"><span data-stu-id="94161-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="94161-166">No **hierarquia** do painel, exclua o **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="94161-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="94161-167">No **projeto** painel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** pasta, localize o **câmera principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="94161-168">Arraste e solte a **câmera principal** pré-fabricado para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="94161-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="94161-169">No **hierarquia** do painel, exclua o **luz direcional** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="94161-170">No **projeto** painel **hologramas** pasta, localize o **Cursor** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="94161-171">Arrastar e soltar os **Cursor** pré-fabricado para o **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="94161-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="94161-172">No **hierarquia** painel, selecione o **Cursor** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="94161-173">No **Inspetor** do painel, clique no **camada** lista suspensa e selecione **camadas editar...** .</span><span class="sxs-lookup"><span data-stu-id="94161-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="94161-174">Nome da **usuário camada 31** como "**SpatialMapping**".</span><span class="sxs-lookup"><span data-stu-id="94161-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="94161-175">Salve a nova cena: **Arquivo > Salvar cena como...**</span><span class="sxs-lookup"><span data-stu-id="94161-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="94161-176">Clique em **nova pasta** e nomeie a pasta **cenas**.</span><span class="sxs-lookup"><span data-stu-id="94161-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="94161-177">Nomeie o arquivo "**Planetarium**" e salve-o na **cenas** pasta.</span><span class="sxs-lookup"><span data-stu-id="94161-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="94161-178">Capítulo 1 - varredura</span><span class="sxs-lookup"><span data-stu-id="94161-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="94161-179">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="94161-179">**Objectives**</span></span>
* <span data-ttu-id="94161-180">Saiba mais sobre o SurfaceObserver e como experiência seu impacto de configurações e o desempenho.</span><span class="sxs-lookup"><span data-stu-id="94161-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="94161-181">Crie uma sala de experiência para coletar as malhas de sua sala de verificação.</span><span class="sxs-lookup"><span data-stu-id="94161-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="94161-182">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="94161-182">**Instructions**</span></span>
* <span data-ttu-id="94161-183">No **projeto** painel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** pasta, localize o **SpatialMapping** pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="94161-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="94161-184">Arrastar e soltar os **SpatialMapping** pré-fabricado para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="94161-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="94161-185">**Compilação e implantação (parte 1)**</span><span class="sxs-lookup"><span data-stu-id="94161-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="94161-186">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="94161-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="94161-187">Clique em **adicionar cenas aberto** para adicionar o **Planetarium** cena para a compilação.</span><span class="sxs-lookup"><span data-stu-id="94161-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="94161-188">Selecione **plataforma Universal do Windows** na **plataforma** lista e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="94161-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="94161-189">Definir **SDK** à **10 Universal** e **tipo de Build de UWP** para **D3D**.</span><span class="sxs-lookup"><span data-stu-id="94161-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="94161-190">Verifique **Unity C# projetos**.</span><span class="sxs-lookup"><span data-stu-id="94161-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="94161-191">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="94161-191">Click **Build**.</span></span>
* <span data-ttu-id="94161-192">Criar uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="94161-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="94161-193">Único clique a **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="94161-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="94161-194">Pressione a **Selecionar pasta** botão.</span><span class="sxs-lookup"><span data-stu-id="94161-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="94161-195">Quando o Unity é feito criando, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="94161-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="94161-196">Clique duas vezes no **aplicativo** pasta para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="94161-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="94161-197">Clique duas vezes em **Planetarium.sln** para carregar o projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94161-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="94161-198">No Visual Studio, use a barra de ferramentas superior para alterar a configuração de **versão**.</span><span class="sxs-lookup"><span data-stu-id="94161-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="94161-199">Alterar a plataforma **x86**.</span><span class="sxs-lookup"><span data-stu-id="94161-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="94161-200">Clique na seta suspensa à direita de 'Local Machine' e selecione **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="94161-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="94161-201">Insira [endereço IP do dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) o endereço de campo e alterar o modo de autenticação **Universal (protocolo não criptografado)**.</span><span class="sxs-lookup"><span data-stu-id="94161-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="94161-202">Clique em **Depurar -> Iniciar sem depuração** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="94161-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="94161-203">Assista a **saída** painel do Visual Studio para compilação e status de implantação.</span><span class="sxs-lookup"><span data-stu-id="94161-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="94161-204">Depois que tiver implantado seu aplicativo, percorrer a sala.</span><span class="sxs-lookup"><span data-stu-id="94161-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="94161-205">Você verá as superfícies ao redor cobertas por malhas de wireframe preto e branco.</span><span class="sxs-lookup"><span data-stu-id="94161-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="94161-206">Examina seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="94161-206">Scan your surroundings.</span></span> <span data-ttu-id="94161-207">Certifique-se de examinar paredes, tetos e à base.</span><span class="sxs-lookup"><span data-stu-id="94161-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="94161-208">**Compilação e implantação (parte 2)**</span><span class="sxs-lookup"><span data-stu-id="94161-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="94161-209">Agora vamos explorar como mapeamento espacial pode afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="94161-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="94161-210">No Unity, selecione **Janela > Profiler**.</span><span class="sxs-lookup"><span data-stu-id="94161-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="94161-211">Clique em **adicionar Profiler > GPU**.</span><span class="sxs-lookup"><span data-stu-id="94161-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="94161-212">Clique em **Profiler Active Directory > <Enter IP>** .</span><span class="sxs-lookup"><span data-stu-id="94161-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="94161-213">Insira o **endereço IP** de seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="94161-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="94161-214">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="94161-214">Click **Connect**.</span></span>
* <span data-ttu-id="94161-215">Observe o número de milissegundos que leva para a GPU renderizar um quadro.</span><span class="sxs-lookup"><span data-stu-id="94161-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="94161-216">Interrompa o aplicativo seja executado no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="94161-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="94161-217">Retorne ao Visual Studio e abra **SpatialMappingObserver.cs**.</span><span class="sxs-lookup"><span data-stu-id="94161-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="94161-218">Você o encontrará na pasta HoloToolkit\SpatialMapping do projeto Assembly-CSharp (Windows Universal).</span><span class="sxs-lookup"><span data-stu-id="94161-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="94161-219">Localizar o **Awake()** de função e adicione a seguinte linha de código: **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="94161-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="94161-220">Reimplantar o projeto em seu dispositivo e, em seguida **reconectar-se o criador de perfil**.</span><span class="sxs-lookup"><span data-stu-id="94161-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="94161-221">Observe a alteração no número de milissegundos para renderizar um quadro.</span><span class="sxs-lookup"><span data-stu-id="94161-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="94161-222">Interrompa o aplicativo seja executado no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="94161-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="94161-223">**Salvar e carregar no Unity**</span><span class="sxs-lookup"><span data-stu-id="94161-223">**Save and load in Unity**</span></span>

<span data-ttu-id="94161-224">Por fim, vamos salvar nosso malha sala e carregá-los no Unity.</span><span class="sxs-lookup"><span data-stu-id="94161-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="94161-225">Retorne ao Visual Studio e remover as **TrianglesPerCubicMeter** que você adicionou na linha a **Awake()** função durante a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="94161-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="94161-226">Reimplante o projeto em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="94161-226">Redeploy the project to your device.</span></span> <span data-ttu-id="94161-227">Podemos agora deve ser executado com **500** triângulos por metro cúbico.</span><span class="sxs-lookup"><span data-stu-id="94161-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="94161-228">Abra um navegador e insira no seu HoloLens IPAddress para navegar até a **Windows Device Portal**.</span><span class="sxs-lookup"><span data-stu-id="94161-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="94161-229">Selecione o **exibição 3D** opção no painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="94161-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="94161-230">Sob **reconstrução da superfície** selecionar a **atualização** botão.</span><span class="sxs-lookup"><span data-stu-id="94161-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="94161-231">Assista como as áreas que examinados em seu HoloLens aparecem na janela de exibição.</span><span class="sxs-lookup"><span data-stu-id="94161-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="94161-232">Para salvar sua verificação de espaço, pressione a **salvar** botão.</span><span class="sxs-lookup"><span data-stu-id="94161-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="94161-233">Abra seu **baixa** pasta para encontrar o modelo salvo sala **SRMesh.obj**.</span><span class="sxs-lookup"><span data-stu-id="94161-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="94161-234">Cópia **SRMesh.obj** para o **ativos** pasta do projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="94161-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="94161-235">No Unity, selecione o **SpatialMapping** objeto de **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="94161-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="94161-236">Localize o **observador de superfície do objeto (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="94161-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="94161-237">Clique no círculo à direita do **sala modelo** propriedade.</span><span class="sxs-lookup"><span data-stu-id="94161-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="94161-238">Localize e selecione o **SRMesh** do objeto e, em seguida, feche a janela.</span><span class="sxs-lookup"><span data-stu-id="94161-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="94161-239">Verificar se o **modelo de sala** propriedade no **Inspetor** painel agora é definido como **SRMesh**.</span><span class="sxs-lookup"><span data-stu-id="94161-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="94161-240">Pressione a **reproduzir** botão para entrar no modo de visualização do Unity.</span><span class="sxs-lookup"><span data-stu-id="94161-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="94161-241">O componente SpatialMapping carregará as malhas do modelo de sala salvo para que você pode usá-los no Unity.</span><span class="sxs-lookup"><span data-stu-id="94161-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="94161-242">Alterne para **cena** modo de exibição para ver todos os seu modelo de espaço exibido com o sombreador de wireframe.</span><span class="sxs-lookup"><span data-stu-id="94161-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="94161-243">Pressione a **reproduzir** botão novamente para sair do modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="94161-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="94161-244">**OBSERVAÇÃO:** Na próxima vez que você entra no modo de visualização no Unity, ele carregará a malha de sala salvos por padrão.</span><span class="sxs-lookup"><span data-stu-id="94161-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="94161-245">Capítulo 2 - visualização</span><span class="sxs-lookup"><span data-stu-id="94161-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="94161-246">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="94161-246">**Objectives**</span></span>
* <span data-ttu-id="94161-247">Conheça os fundamentos de sombreadores.</span><span class="sxs-lookup"><span data-stu-id="94161-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="94161-248">Visualize o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="94161-248">Visualize your surroundings.</span></span>

<span data-ttu-id="94161-249">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="94161-249">**Instructions**</span></span>
* <span data-ttu-id="94161-250">Do Unity **hierarquia** painel, selecione o **SpatialMapping** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="94161-251">No **Inspector** do painel, localize a **Gerenciador de mapeamento espacial (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="94161-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="94161-252">Clique no círculo à direita do **Material da superfície** propriedade.</span><span class="sxs-lookup"><span data-stu-id="94161-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="94161-253">Localize e selecione o **BlueLinesOnWalls** material e feche a janela.</span><span class="sxs-lookup"><span data-stu-id="94161-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="94161-254">No **Project** painel **sombreadores** pasta, clique duas vezes em **BlueLinesOnWalls** para abrir o sombreador no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94161-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="94161-255">Isso é um pixel simple (vértice para fragmentar) sombreador, que realiza as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="94161-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="94161-256">Converte o local de um vértice espaço de mundo.</span><span class="sxs-lookup"><span data-stu-id="94161-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="94161-257">Verifica que o vértice 's normal para determinar se um pixel é vertical.</span><span class="sxs-lookup"><span data-stu-id="94161-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="94161-258">Define a cor do pixel para renderização.</span><span class="sxs-lookup"><span data-stu-id="94161-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="94161-259">**Criar e implantar**</span><span class="sxs-lookup"><span data-stu-id="94161-259">**Build and Deploy**</span></span>
* <span data-ttu-id="94161-260">Retorne ao Unity e pressione **reproduzir** para entrar no modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="94161-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="94161-261">Linhas azuis serão renderizadas em todas as superfícies verticais da malha sala (o que automaticamente carregado de nossos dados de verificação salvos).</span><span class="sxs-lookup"><span data-stu-id="94161-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="94161-262">Alterne para o **cena** tab para ajustar a exibição da sala e veja como a malha inteira espaço será exibida no Unity.</span><span class="sxs-lookup"><span data-stu-id="94161-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="94161-263">No **Project** do painel, localize a **materiais** pasta e selecione o **BlueLinesOnWalls** material.</span><span class="sxs-lookup"><span data-stu-id="94161-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="94161-264">Modificar algumas propriedades e ver como as alterações aparecem no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="94161-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="94161-265">No **Inspector** do painel, ajuste a **LineScale** valor para tornar as linhas aparecem mais espessa ou mais fina.</span><span class="sxs-lookup"><span data-stu-id="94161-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="94161-266">No **Inspector** do painel, ajuste a **LinesPerMeter** valor para alterar o número de linhas aparecem em cada parede.</span><span class="sxs-lookup"><span data-stu-id="94161-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="94161-267">Clique em **reproduzir** novamente para sair do modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="94161-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="94161-268">Criar e implantar para o HoloLens e observar como o sombreador de renderização aparece em superfícies real.</span><span class="sxs-lookup"><span data-stu-id="94161-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="94161-269">Unity faz um excelente trabalho de visualização de materiais, mas é sempre uma boa ideia check-out de renderização no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="94161-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="94161-270">Capítulo 3 - processamento</span><span class="sxs-lookup"><span data-stu-id="94161-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="94161-271">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="94161-271">**Objectives**</span></span>
* <span data-ttu-id="94161-272">Aprenda técnicas para processar dados de mapeamento espacial para uso em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94161-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="94161-273">Analise dados de mapeamento espacial para localizar planos e remover triângulos.</span><span class="sxs-lookup"><span data-stu-id="94161-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="94161-274">Use planos para posicionamento holograma.</span><span class="sxs-lookup"><span data-stu-id="94161-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="94161-275">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="94161-275">**Instructions**</span></span>
* <span data-ttu-id="94161-276">Do Unity **Project** painel, **hologramas** pasta, localize o **SpatialProcessing** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="94161-277">Arrastar e soltar os **SpatialProcessing** do objeto para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="94161-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="94161-278">Pré-fabricado SpatialProcessing inclui componentes para processar os dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="94161-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="94161-279">**SurfaceMeshesToPlanes.cs** encontrará e gerar planos com base nos dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="94161-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="94161-280">Nós usaremos planos para representar paredes, andares e tetos em nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94161-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="94161-281">Também inclui esse pré-fabricado **RemoveSurfaceVertices.cs** que pode remover os vértices da malha mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="94161-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="94161-282">Isso pode ser usado para criar buracos na malha, ou remover em excesso triângulos que não são mais necessários (porque os planos podem ser usados em vez disso).</span><span class="sxs-lookup"><span data-stu-id="94161-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="94161-283">Do Unity **Project** painel, **hologramas** pasta, localize o **SpaceCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="94161-284">Arraste e solte a **SpaceCollection** do objeto para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="94161-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="94161-285">No **hierarquia** painel, selecione o **SpatialProcessing** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="94161-286">No **Inspector** do painel, localize a **reproduzir o Gerenciador de espaço (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="94161-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="94161-287">Clique duas vezes em **PlaySpaceManager.cs** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94161-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="94161-288">PlaySpaceManager.cs contém código específico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="94161-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="94161-289">Vamos adicionar funcionalidade a esse script para habilitar o seguinte comportamento:</span><span class="sxs-lookup"><span data-stu-id="94161-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="94161-290">Pare de coletar dados de mapeamento espacial, depois de exceder o limite de tempo de varredura (10 segundos).</span><span class="sxs-lookup"><span data-stu-id="94161-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="94161-291">Processe os dados de mapeamento espacial:</span><span class="sxs-lookup"><span data-stu-id="94161-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="94161-292">Use SurfaceMeshesToPlanes para criar uma representação mais simples do mundo como planos (paredes, andares, tetos, etc.).</span><span class="sxs-lookup"><span data-stu-id="94161-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="94161-293">Use RemoveSurfaceVertices para remover a superfície triângulos que caem dentro dos limites do plano.</span><span class="sxs-lookup"><span data-stu-id="94161-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="94161-294">Gerar uma coleção de hologramas no mundo e colocá-los em planos de parede e andar próxima ao usuário.</span><span class="sxs-lookup"><span data-stu-id="94161-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="94161-295">Concluir os exercícios de codificação marcados em PlaySpaceManager.cs ou substitua o script com a solução concluída abaixo:</span><span class="sxs-lookup"><span data-stu-id="94161-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="94161-296">**Criar e implantar**</span><span class="sxs-lookup"><span data-stu-id="94161-296">**Build and Deploy**</span></span>
* <span data-ttu-id="94161-297">Antes de implantar o HoloLens, pressione a **reproduzir** botão no Unity para entrar no modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="94161-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="94161-298">Depois que a sala malha é carregada do arquivo, aguarde 10 segundos antes do início do processamento da malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="94161-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="94161-299">Quando o processamento for concluído, os planos serão exibida para representar o chão, paredes, ceiling etc.</span><span class="sxs-lookup"><span data-stu-id="94161-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="94161-300">Afinal de contas dos planos foram encontrados, você deverá ver um sistema solar aparecem em uma tabela de Chão de perto a câmera.</span><span class="sxs-lookup"><span data-stu-id="94161-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="94161-301">Dois pôsteres devem aparecer no paredes perto da câmera muito.</span><span class="sxs-lookup"><span data-stu-id="94161-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="94161-302">Alterne para o **cena** guia se você não pode vê-los na **jogo** modo.</span><span class="sxs-lookup"><span data-stu-id="94161-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="94161-303">Pressione a **reproduzir** botão novamente para sair do modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="94161-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="94161-304">Crie e implante como de costume para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="94161-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="94161-305">Aguarde a verificação e processamento dos dados espaciais de mapeamento para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="94161-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="94161-306">Depois de ver planos, tente localizar o sistema solar e cartazes em seu mundo.</span><span class="sxs-lookup"><span data-stu-id="94161-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="94161-307">Capítulo 4 - posicionamento</span><span class="sxs-lookup"><span data-stu-id="94161-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="94161-308">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="94161-308">**Objectives**</span></span>
* <span data-ttu-id="94161-309">Determine se um holograma serão ajustadas em uma superfície.</span><span class="sxs-lookup"><span data-stu-id="94161-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="94161-310">Fornece comentários ao usuário quando um holograma pode/não couberem em uma superfície.</span><span class="sxs-lookup"><span data-stu-id="94161-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="94161-311">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="94161-311">**Instructions**</span></span>
* <span data-ttu-id="94161-312">Do Unity **hierarquia** painel, selecione o **SpatialProcessing** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="94161-313">No **Inspector** do painel, localize a **malhas para planos superfície (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="94161-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="94161-314">Alterar o **desenhar planos** propriedade **nada** para limpar a seleção.</span><span class="sxs-lookup"><span data-stu-id="94161-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="94161-315">Alterar o **desenhar planos** propriedade **parede**, de modo que apenas os planos de parede serão renderizados.</span><span class="sxs-lookup"><span data-stu-id="94161-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="94161-316">No **projeto** painel **Scripts** pasta, clique duas vezes em **Placeable.cs** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94161-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="94161-317">O **Placeable** script já está anexado ao cartazes e caixa de projeção que são criados após a conclusão da localização do plano.</span><span class="sxs-lookup"><span data-stu-id="94161-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="94161-318">Tudo que precisamos fazer é remover os comentários de código, e esse script irá obter o seguinte:</span><span class="sxs-lookup"><span data-stu-id="94161-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="94161-319">Determine se um holograma serão ajustadas em uma superfície de raycasting do centro e quatro cantos do cubo delimitadora.</span><span class="sxs-lookup"><span data-stu-id="94161-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="94161-320">Verificar a superfície normal para determinar se ele é suave para o holograma de liberação esperar na.</span><span class="sxs-lookup"><span data-stu-id="94161-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="94161-321">Processa um cubo delimitadora em torno de holograma para mostrar o tamanho real ao que está sendo colocado.</span><span class="sxs-lookup"><span data-stu-id="94161-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="94161-322">Converta uma sombra em/atrás do holograma para mostrar onde ele será colocado na parede/andar.</span><span class="sxs-lookup"><span data-stu-id="94161-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="94161-323">Renderize a sombra como vermelho, se o holograma não pode ser colocado na superfície ou verde, se possível.</span><span class="sxs-lookup"><span data-stu-id="94161-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="94161-324">O holograma para alinhar com o tipo de superfície (horizontal ou vertical) que tem afinidade para re-Oriente.</span><span class="sxs-lookup"><span data-stu-id="94161-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="94161-325">Sem problemas coloca o holograma na superfície de selecionado para evitar saltar ou comportamento de encaixe.</span><span class="sxs-lookup"><span data-stu-id="94161-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="94161-326">Remova todo o código no exercício codificação abaixo ou usar essa solução concluída em **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="94161-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="94161-327">**Criar e implantar**</span><span class="sxs-lookup"><span data-stu-id="94161-327">**Build and Deploy**</span></span>
* <span data-ttu-id="94161-328">Como antes, compile o projeto e implantar para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="94161-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="94161-329">Aguarde a verificação e processamento dos dados espaciais de mapeamento para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="94161-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="94161-330">Quando você vir o sistema solar, mantenha o foco em caixa projeção abaixo e execute um gesto de select movê-lo.</span><span class="sxs-lookup"><span data-stu-id="94161-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="94161-331">Enquanto a caixa de projeção é selecionada, um cubo delimitadora ficará visível em torno da caixa de projeção.</span><span class="sxs-lookup"><span data-stu-id="94161-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="94161-332">Mova head para mantenha o foco em um local diferente na sala.</span><span class="sxs-lookup"><span data-stu-id="94161-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="94161-333">A caixa de projeção deve siga seu foco.</span><span class="sxs-lookup"><span data-stu-id="94161-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="94161-334">Quando a sombra abaixo da caixa de projeção fica vermelha, você não pode colocar o holograma em que são exibidos.</span><span class="sxs-lookup"><span data-stu-id="94161-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="94161-335">Quando a sombra abaixo da caixa de projeção fica verde, você pode colocar o holograma executando gesto selecione outro.</span><span class="sxs-lookup"><span data-stu-id="94161-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="94161-336">Localize e selecione um dos cartazes holográfico uma parede para movê-lo para um novo local.</span><span class="sxs-lookup"><span data-stu-id="94161-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="94161-337">Observe que você não pode colocar o cartaz na base ou ceiling e que ele permaneça orientado corretamente para cada parede move ao redor.</span><span class="sxs-lookup"><span data-stu-id="94161-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="94161-338">Capítulo 5 - oclusão</span><span class="sxs-lookup"><span data-stu-id="94161-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="94161-339">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="94161-339">**Objectives**</span></span>
* <span data-ttu-id="94161-340">Determine se um holograma é obstruído pela malha mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="94161-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="94161-341">Aplicar as técnicas de oclusão diferentes para alcançar um divertido em vigor.</span><span class="sxs-lookup"><span data-stu-id="94161-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="94161-342">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="94161-342">**Instructions**</span></span>

<span data-ttu-id="94161-343">Primeiro, vamos permitir que a malha de mapeamento espacial para occlude outras hologramas sem occluding do mundo real:</span><span class="sxs-lookup"><span data-stu-id="94161-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="94161-344">No **hierarquia** painel, selecione o **SpatialProcessing** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="94161-345">No **Inspector** do painel, localize a **reproduzir o Gerenciador de espaço (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="94161-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="94161-346">Clique no círculo à direita do **Material secundário** propriedade.</span><span class="sxs-lookup"><span data-stu-id="94161-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="94161-347">Localize e selecione o **oclusão** material e feche a janela.</span><span class="sxs-lookup"><span data-stu-id="94161-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="94161-348">Em seguida, vamos adicionar um comportamento especial a Terra, para que ele tenha um realce azul sempre que ele se torna obstruído pelo outro holograma (como o sol) ou pela malha mapeamento espacial:</span><span class="sxs-lookup"><span data-stu-id="94161-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="94161-349">No **Project** painel, o **hologramas** pasta, expanda o **SolarSystem** objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="94161-350">Clique em **Terra**.</span><span class="sxs-lookup"><span data-stu-id="94161-350">Click on **Earth**.</span></span>
* <span data-ttu-id="94161-351">No **Inspetor** painel, localizar o material da Terra (componente inferior).</span><span class="sxs-lookup"><span data-stu-id="94161-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="94161-352">No **suspensa sombreador**, altere o sombreador **personalizado > OcclusionRim**.</span><span class="sxs-lookup"><span data-stu-id="94161-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="94161-353">Isso será renderizado um realce azul ao redor de terra sempre que ele é obstruído por outro objeto.</span><span class="sxs-lookup"><span data-stu-id="94161-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="94161-354">Por fim, vamos habilitar um efeito de visão de raios-x para planetas em nosso sistema solar.</span><span class="sxs-lookup"><span data-stu-id="94161-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="94161-355">Precisaremos editar **PlanetOcclusion.cs** (encontrado na pasta Scripts\SolarSystem) para alcançar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="94161-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="94161-356">Determine se um planeta é obstruído pela camada de SpatialMapping (sala malhas e planos).</span><span class="sxs-lookup"><span data-stu-id="94161-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="94161-357">Mostre a representação de wireframe de um planeta sempre que ele é obstruído pela camada de SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="94161-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="94161-358">Oculte a representação de wireframe de um planeta quando ele não está bloqueado pela camada de SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="94161-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="94161-359">Siga o exercício de codificação em PlanetOcclusion.cs ou usar a solução a seguir:</span><span class="sxs-lookup"><span data-stu-id="94161-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="94161-360">**Criar e implantar**</span><span class="sxs-lookup"><span data-stu-id="94161-360">**Build and Deploy**</span></span>
* <span data-ttu-id="94161-361">Crie e implante o aplicativo para o HoloLens, como de costume.</span><span class="sxs-lookup"><span data-stu-id="94161-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="94161-362">Aguarde a verificação e processamento dos dados espaciais de mapeamento para ser concluída (você deve ver linhas azuis na paredes).</span><span class="sxs-lookup"><span data-stu-id="94161-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="94161-363">Localize e selecione a caixa de projeção do sistema solar e, em seguida, defina a caixa ao lado de uma parede ou atrás de um contador.</span><span class="sxs-lookup"><span data-stu-id="94161-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="94161-364">Você pode exibir oclusão básica esconder atrás superfícies emparelhar a caixa de pôster ou projeção.</span><span class="sxs-lookup"><span data-stu-id="94161-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="94161-365">Procure a Terra, deve haver um efeito de realce azul sempre que ele fica atrás de outro holograma ou superfície.</span><span class="sxs-lookup"><span data-stu-id="94161-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="94161-366">Assista como planetas mover por trás de parede ou outras superfícies na sala.</span><span class="sxs-lookup"><span data-stu-id="94161-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="94161-367">Agora você tem a visão de raios-x e pode ver seus esqueletos de wireframe!</span><span class="sxs-lookup"><span data-stu-id="94161-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="94161-368">Fim</span><span class="sxs-lookup"><span data-stu-id="94161-368">The End</span></span>

<span data-ttu-id="94161-369">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="94161-369">Congratulations!</span></span> <span data-ttu-id="94161-370">Agora você concluiu **MR de 230 espacial: Mapeamento espacial**.</span><span class="sxs-lookup"><span data-stu-id="94161-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="94161-371">Você sabe como fazer a varredura de seus dados de ambiente e carga mapeamento espacial para o Unity.</span><span class="sxs-lookup"><span data-stu-id="94161-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="94161-372">Você compreender os fundamentos de sombreadores e como os materiais podem ser usados para visualizar novamente o mundo.</span><span class="sxs-lookup"><span data-stu-id="94161-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="94161-373">Você aprendeu sobre novas técnicas de processamento para localizar planos e removendo os triângulos de uma malha.</span><span class="sxs-lookup"><span data-stu-id="94161-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="94161-374">Você conseguiu mover e coloque hologramas em superfícies que fazia sentido.</span><span class="sxs-lookup"><span data-stu-id="94161-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="94161-375">Você apresentou técnicas diferentes de oclusão e aproveitar a potência da visão de raios-x!</span><span class="sxs-lookup"><span data-stu-id="94161-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>

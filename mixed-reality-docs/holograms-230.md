---
title: Sr espacial 230-mapeamento espacial
description: Siga este passo a passo de codificação usando o Unity, o Visual Studio e o HoloLens para aprender os detalhes dos conceitos espaciais de mapeamento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, mapeamento espacial, reconstrução de superfície, malha
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993556"
---
>[!NOTE]
><span data-ttu-id="1e89a-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1e89a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1e89a-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1e89a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1e89a-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1e89a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1e89a-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="1e89a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1e89a-108">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1e89a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1e89a-109">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="1e89a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="1e89a-110">MR espacial 230: Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="1e89a-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="1e89a-111">O [mapeamento espacial](spatial-mapping.md) combina o mundo real e o mundo virtual juntos ao ensinar hologramas sobre o ambiente.</span><span class="sxs-lookup"><span data-stu-id="1e89a-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="1e89a-112">No Sr espacial 230 (projeto Planetarium), aprenderemos a:</span><span class="sxs-lookup"><span data-stu-id="1e89a-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="1e89a-113">Examine o ambiente e transfira dados do HoloLens para seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1e89a-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="1e89a-114">Explore os sombreadores e saiba como usá-los para visualizar seu espaço.</span><span class="sxs-lookup"><span data-stu-id="1e89a-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="1e89a-115">Divida a malha Room em planos simples usando o processamento de malha.</span><span class="sxs-lookup"><span data-stu-id="1e89a-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="1e89a-116">Vá além das técnicas de posicionamento que aprendemos no [Sr basics 101](holograms-101.md)e forneça comentários sobre onde um holograma pode ser colocado no ambiente.</span><span class="sxs-lookup"><span data-stu-id="1e89a-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="1e89a-117">Explore os efeitos do oclusão, portanto, quando o holograma estiver atrás de um objeto do mundo real, você ainda poderá vê-lo com a visão x-ray!</span><span class="sxs-lookup"><span data-stu-id="1e89a-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="1e89a-118">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="1e89a-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1e89a-119">Course</span><span class="sxs-lookup"><span data-stu-id="1e89a-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1e89a-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1e89a-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1e89a-121"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="1e89a-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1e89a-122">MR espacial 230: Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="1e89a-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="1e89a-123">✔️</span><span class="sxs-lookup"><span data-stu-id="1e89a-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1e89a-124">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="1e89a-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1e89a-125">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1e89a-125">Prerequisites</span></span>

* <span data-ttu-id="1e89a-126">Um PC com Windows 10 configurado com as [ferramentas](install-the-tools.md)corretas instaladas.</span><span class="sxs-lookup"><span data-stu-id="1e89a-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="1e89a-127">Alguma capacidade C# básica de programação.</span><span class="sxs-lookup"><span data-stu-id="1e89a-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="1e89a-128">Você deve ter concluído o [Sr noções básicas 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="1e89a-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="1e89a-129">Um dispositivo HoloLens [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="1e89a-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="1e89a-130">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="1e89a-130">Project files</span></span>

* <span data-ttu-id="1e89a-131">Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) exigidos pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="1e89a-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="1e89a-132"> Requer o Unity 2017,2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="1e89a-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="1e89a-133">Se você ainda precisar de suporte do Unity 5,6, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="1e89a-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="1e89a-134">Se você ainda precisar de suporte do Unity 5,5, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="1e89a-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="1e89a-135">Se você ainda precisar de suporte do Unity 5,4, use [esta versão](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="1e89a-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="1e89a-136">Cancele o arquivamento dos arquivos em sua área de trabalho ou outro local fácil de acessar.</span><span class="sxs-lookup"><span data-stu-id="1e89a-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="1e89a-137">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="1e89a-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="1e89a-138">Observações</span><span class="sxs-lookup"><span data-stu-id="1e89a-138">Notes</span></span>

* <span data-ttu-id="1e89a-139">"Habilitar Apenas Meu Código" no Visual Studio precisa ser desabilitado (desmarcado) em Ferramentas > Opções > depuração para acessar pontos de interrupção em seu código.</span><span class="sxs-lookup"><span data-stu-id="1e89a-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="1e89a-140">Configuração do Unity</span><span class="sxs-lookup"><span data-stu-id="1e89a-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="1e89a-141">Inicie o **Unity**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-141">Start **Unity**.</span></span>
* <span data-ttu-id="1e89a-142">Selecione **novo** para criar um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="1e89a-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="1e89a-143">Nomeie o projeto **Planetarium**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="1e89a-144">Verifique se a configuração **3D** está selecionada.</span><span class="sxs-lookup"><span data-stu-id="1e89a-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="1e89a-145">Clique em **Criar Projeto**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-145">Click **Create Project**.</span></span>
* <span data-ttu-id="1e89a-146">Depois que o Unity for iniciado, vá para **Editar configurações do projeto > > Player**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="1e89a-147">No painel **Inspetor** , localize e selecione o ícone verde da **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="1e89a-148">Expanda **outras configurações**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="1e89a-149">Na seção **renderização** , verifique a opção **suporte à realidade virtual** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="1e89a-150">Verifique se o **Windows Holographic** aparece na lista de **SDKs de realidade virtual**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="1e89a-151">Caso contrário, selecione o **+** botão na parte inferior da lista e escolha **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="1e89a-152">Expanda **configurações de publicação**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="1e89a-153">Na seção **recursos** , verifique as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="1e89a-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="1e89a-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="1e89a-154">InternetClientServer</span></span>
    * <span data-ttu-id="1e89a-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="1e89a-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="1e89a-156">Microfone</span><span class="sxs-lookup"><span data-stu-id="1e89a-156">Microphone</span></span>
    * <span data-ttu-id="1e89a-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="1e89a-157">SpatialPerception</span></span>
* <span data-ttu-id="1e89a-158">Vá para **Editar configurações de projeto > > qualidade**</span><span class="sxs-lookup"><span data-stu-id="1e89a-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="1e89a-159">No painel **Inspetor** , sob o ícone Windows Store, selecione a seta suspensa preta na linha ' padrão ' e altere a configuração padrão para **muito baixa**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="1e89a-160">Acesse **ativos > importar pacote > pacote personalizado**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="1e89a-161">Navegue até a pasta **. ..\holographicacademy-holograms-230-SpatialMapping\Starting** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="1e89a-162">Clique em **Planetarium. unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="1e89a-163">Clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-163">Click **Open**.</span></span>
* <span data-ttu-id="1e89a-164">Uma janela **Importar pacote do Unity** deve aparecer, clique no botão **importar** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="1e89a-165">Aguarde até que o Unity importe todos os ativos para os quais precisaremos concluir este projeto.</span><span class="sxs-lookup"><span data-stu-id="1e89a-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="1e89a-166">No painel **hierarquia** , exclua a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="1e89a-167">No painel **projeto** , pasta **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** , localize o objeto **principal da câmera** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="1e89a-168">Arraste e solte o pré-fabricado da **câmera principal** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1e89a-169">No painel **hierarquia** , exclua o objeto de **luz direcional** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="1e89a-170">No painel **projeto** , pasta **hologramas** , localize o objeto **cursor** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="1e89a-171">Arraste & solte o **cursor** pré-fabricado na **hierarquia**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="1e89a-172">No painel **hierarquia** , selecione o objeto **cursor** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="1e89a-173">No painel **Inspetor** , clique na lista suspensa **camada** e selecione **Editar camadas...** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="1e89a-174">Nome a **camada de usuário 31** como "**SpatialMapping**".</span><span class="sxs-lookup"><span data-stu-id="1e89a-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="1e89a-175">Salve a nova cena: **Arquivo > salvar cena como...**</span><span class="sxs-lookup"><span data-stu-id="1e89a-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="1e89a-176">Clique em **nova pasta** e nomeie a pasta **cenas**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="1e89a-177">Nomeie o arquivo como "**Planetarium**" e salve-o na pasta de **cenas** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="1e89a-178">Capítulo 1-verificando</span><span class="sxs-lookup"><span data-stu-id="1e89a-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="1e89a-179">**Seus**</span><span class="sxs-lookup"><span data-stu-id="1e89a-179">**Objectives**</span></span>
* <span data-ttu-id="1e89a-180">Saiba mais sobre o SurfaceObserver e como suas configurações impactam a experiência e o desempenho.</span><span class="sxs-lookup"><span data-stu-id="1e89a-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="1e89a-181">Crie uma experiência de verificação de sala para coletar as malhas da sua sala.</span><span class="sxs-lookup"><span data-stu-id="1e89a-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="1e89a-182">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="1e89a-182">**Instructions**</span></span>
* <span data-ttu-id="1e89a-183">Na pasta **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** do painel de **projeto** , localize o **SpatialMapping** pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="1e89a-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="1e89a-184">Arraste & soltar o pré-fabricado **SpatialMapping** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="1e89a-185">**Compilar e implantar (parte 1)**</span><span class="sxs-lookup"><span data-stu-id="1e89a-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="1e89a-186">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="1e89a-187">Clique em **Adicionar abrir cenas** para adicionar a cena **Planetarium** à compilação.</span><span class="sxs-lookup"><span data-stu-id="1e89a-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="1e89a-188">Selecione **plataforma universal do Windows** na lista **plataforma** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="1e89a-189">Defina o **SDK** para o **tipo de compilação** **Universal 10** e UWP como **D3D**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="1e89a-190">Verifique **os C# projetos do Unity**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="1e89a-191">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-191">Click **Build**.</span></span>
* <span data-ttu-id="1e89a-192">Crie uma **nova pasta** chamada "app".</span><span class="sxs-lookup"><span data-stu-id="1e89a-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="1e89a-193">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="1e89a-194">Pressione o botão **Selecionar pasta** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="1e89a-195">Quando o Unity terminar a compilação, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="1e89a-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="1e89a-196">Clique duas vezes na pasta do **aplicativo** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="1e89a-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="1e89a-197">Clique duas vezes em **Planetarium. sln** para carregar o projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e89a-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="1e89a-198">No Visual Studio, use a barra de ferramentas superior para alterar a configuração a ser liberada.</span><span class="sxs-lookup"><span data-stu-id="1e89a-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="1e89a-199">Altere a plataforma para **x86**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="1e89a-200">Clique na seta suspensa à direita de ' máquina local ' e selecione **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="1e89a-201">Insira [o endereço IP do dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) no campo endereço e altere o modo de autenticação para **Universal (protocolo não criptografado)** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="1e89a-202">Clique em **depurar-> iniciar sem Depurar** ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="1e89a-203">Assista ao painel de **saída** no Visual Studio para o status de compilação e implantação.</span><span class="sxs-lookup"><span data-stu-id="1e89a-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="1e89a-204">Depois que seu aplicativo for implantado, percorra a sala.</span><span class="sxs-lookup"><span data-stu-id="1e89a-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="1e89a-205">Você verá as superfícies ao redor cobertas por malhas de wireframe preto e branco.</span><span class="sxs-lookup"><span data-stu-id="1e89a-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="1e89a-206">Examine seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="1e89a-206">Scan your surroundings.</span></span> <span data-ttu-id="1e89a-207">Certifique-se de examinar as paredes, os tetos e os andares.</span><span class="sxs-lookup"><span data-stu-id="1e89a-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="1e89a-208">**Compilar e implantar (parte 2)**</span><span class="sxs-lookup"><span data-stu-id="1e89a-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="1e89a-209">Agora vamos explorar como o mapeamento espacial pode afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="1e89a-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="1e89a-210">No Unity, selecione **Window >** Profiler.</span><span class="sxs-lookup"><span data-stu-id="1e89a-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="1e89a-211">Clique em **Adicionar criador de perfil > GPU**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="1e89a-212">Clique em **Active Profiler > <Enter IP>** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="1e89a-213">Insira o **endereço IP** do seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1e89a-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="1e89a-214">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-214">Click **Connect**.</span></span>
* <span data-ttu-id="1e89a-215">Observe o número de milissegundos que leva para a GPU renderizar um quadro.</span><span class="sxs-lookup"><span data-stu-id="1e89a-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="1e89a-216">Impedir que o aplicativo seja executado no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="1e89a-217">Retorne ao Visual Studio e abra **SpatialMappingObserver.cs**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="1e89a-218">Você o encontrará na pasta HoloToolkit\SpatialMapping do projeto assembly-CSharp (universal do Windows).</span><span class="sxs-lookup"><span data-stu-id="1e89a-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="1e89a-219">Localize a função **ativo ()** e adicione a seguinte linha de código: **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="1e89a-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="1e89a-220">Implante novamente o projeto em seu dispositivo e **reconecte o criador de perfil**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="1e89a-221">Observe a alteração no número de milissegundos para renderizar um quadro.</span><span class="sxs-lookup"><span data-stu-id="1e89a-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="1e89a-222">Impedir que o aplicativo seja executado no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="1e89a-223">**Salvar e carregar no Unity**</span><span class="sxs-lookup"><span data-stu-id="1e89a-223">**Save and load in Unity**</span></span>

<span data-ttu-id="1e89a-224">Por fim, vamos salvar nossa malha Room e carregá-la no Unity.</span><span class="sxs-lookup"><span data-stu-id="1e89a-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="1e89a-225">Retorne ao Visual Studio e remova a linha **TrianglesPerCubicMeter** que você adicionou na função de **ativo ()** durante a seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1e89a-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="1e89a-226">Reimplante o projeto em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-226">Redeploy the project to your device.</span></span> <span data-ttu-id="1e89a-227">Agora devemos estar executando com **500** triângulos por medidor cúbico.</span><span class="sxs-lookup"><span data-stu-id="1e89a-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="1e89a-228">Abra um navegador e insira o endereço IP do seu HoloLens para navegar até o **portal do dispositivo Windows**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="1e89a-229">Selecione a opção **exibição 3D** no painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="1e89a-230">Em **reconstrução da superfície** , selecione o botão **Atualizar** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="1e89a-231">Observe como as áreas que você examinou em seu HoloLens aparecem na janela de exibição.</span><span class="sxs-lookup"><span data-stu-id="1e89a-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="1e89a-232">Para salvar sua verificação de sala, pressione o botão **salvar** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="1e89a-233">Abra a pasta **downloads** para localizar o modelo de sala salvo **SRMesh. obj**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="1e89a-234">Copie **SRMesh. obj** para a pasta **ativos** do seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="1e89a-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="1e89a-235">No Unity, selecione o objeto **SpatialMapping** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1e89a-236">Localize o componente observador de **superfície de objeto (script)** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="1e89a-237">Clique no círculo à direita da propriedade de **modelo de sala** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="1e89a-238">Localize e selecione o objeto **SRMesh** e feche a janela.</span><span class="sxs-lookup"><span data-stu-id="1e89a-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="1e89a-239">Verifique se a propriedade **modelo de sala** no painel **Inspetor** agora está definida como **SRMesh**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="1e89a-240">Pressione o botão **reproduzir** para inserir o modo de visualização do Unity.</span><span class="sxs-lookup"><span data-stu-id="1e89a-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="1e89a-241">O componente SpatialMapping carregará as malhas do modelo de sala salvo para que você possa usá-las no Unity.</span><span class="sxs-lookup"><span data-stu-id="1e89a-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="1e89a-242">Alterne para a exibição de **cena** para ver todo o modelo de sala exibido com o sombreador delineado.</span><span class="sxs-lookup"><span data-stu-id="1e89a-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="1e89a-243">Pressione o botão **reproduzir** novamente para sair do modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="1e89a-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="1e89a-244">**OBSERVAÇÃO:** Na próxima vez que você inserir o modo de visualização no Unity, ele carregará a malha de sala salva por padrão.</span><span class="sxs-lookup"><span data-stu-id="1e89a-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="1e89a-245">Capítulo 2 – visualização</span><span class="sxs-lookup"><span data-stu-id="1e89a-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="1e89a-246">**Seus**</span><span class="sxs-lookup"><span data-stu-id="1e89a-246">**Objectives**</span></span>
* <span data-ttu-id="1e89a-247">Aprenda os fundamentos dos sombreadores.</span><span class="sxs-lookup"><span data-stu-id="1e89a-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="1e89a-248">Visualize seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="1e89a-248">Visualize your surroundings.</span></span>

<span data-ttu-id="1e89a-249">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="1e89a-249">**Instructions**</span></span>
* <span data-ttu-id="1e89a-250">No painel **hierarquia** do Unity, selecione o objeto **SpatialMapping** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="1e89a-251">No painel **Inspetor** , localize o componente do **Gerenciador de mapeamento espacial (script)** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="1e89a-252">Clique no círculo à direita da propriedade **material da superfície** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="1e89a-253">Localize e selecione o material de **BlueLinesOnWalls** e feche a janela.</span><span class="sxs-lookup"><span data-stu-id="1e89a-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="1e89a-254">Na pasta sombreadores  do painel de **projeto** , clique duas vezes em **BlueLinesOnWalls** para abrir o sombreador no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e89a-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="1e89a-255">Este é um sombreador simples de pixel (vértice para fragmento), que realiza as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="1e89a-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="1e89a-256">Converte o local de um vértice no espaço do mundo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="1e89a-257">Verifica o normal do vértice para determinar se um pixel é vertical.</span><span class="sxs-lookup"><span data-stu-id="1e89a-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="1e89a-258">Define a cor do pixel para renderização.</span><span class="sxs-lookup"><span data-stu-id="1e89a-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="1e89a-259">**Compilar e implantar**</span><span class="sxs-lookup"><span data-stu-id="1e89a-259">**Build and Deploy**</span></span>
* <span data-ttu-id="1e89a-260">Retorne ao Unity e pressione **reproduzir** para entrar no modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="1e89a-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="1e89a-261">As linhas azuis serão renderizadas em todas as superfícies verticais da malha Room (que são carregadas automaticamente de nossos dados de verificação salvos).</span><span class="sxs-lookup"><span data-stu-id="1e89a-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="1e89a-262">Alterne para a guia **cena** para ajustar sua exibição da sala e ver como a malha de sala inteira aparece no Unity.</span><span class="sxs-lookup"><span data-stu-id="1e89a-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="1e89a-263">No painel **projeto** , localize a pasta **materiais** e selecione o material **BlueLinesOnWalls** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="1e89a-264">Modifique algumas propriedades e veja como as alterações aparecem no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="1e89a-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="1e89a-265">No painel **Inspetor** , ajuste o valor **LineScale** para que as linhas pareçam mais espessas ou mais finas.</span><span class="sxs-lookup"><span data-stu-id="1e89a-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="1e89a-266">No painel **Inspetor** , ajuste o valor **LinesPerMeter** para alterar a quantidade de linhas exibidas em cada parede.</span><span class="sxs-lookup"><span data-stu-id="1e89a-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="1e89a-267">Clique em **reproduzir** novamente para sair do modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="1e89a-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="1e89a-268">Crie e implante no HoloLens e observe como a renderização do sombreador aparece em superfícies reais.</span><span class="sxs-lookup"><span data-stu-id="1e89a-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="1e89a-269">O Unity faz um ótimo trabalho de visualização de materiais, mas é sempre uma boa ideia fazer check-out do processamento no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="1e89a-270">Capítulo 3-processando</span><span class="sxs-lookup"><span data-stu-id="1e89a-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="1e89a-271">**Seus**</span><span class="sxs-lookup"><span data-stu-id="1e89a-271">**Objectives**</span></span>
* <span data-ttu-id="1e89a-272">Aprenda técnicas para processar dados de mapeamento espacial para uso em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="1e89a-273">Analise os dados de mapeamento espacial para localizar planos e remover triângulos.</span><span class="sxs-lookup"><span data-stu-id="1e89a-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="1e89a-274">Use planos para posicionamento de holograma.</span><span class="sxs-lookup"><span data-stu-id="1e89a-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="1e89a-275">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="1e89a-275">**Instructions**</span></span>
* <span data-ttu-id="1e89a-276">Na pasta painel de **projeto** do Unity, **hologramas** , localize o objeto **SpatialProcessing** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="1e89a-277">Arraste & solte o objeto **SpatialProcessing** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="1e89a-278">O SpatialProcessing pré-fabricado inclui componentes para processar os dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="1e89a-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="1e89a-279">**SurfaceMeshesToPlanes.cs** encontrará e gerará planos com base nos dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="1e89a-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="1e89a-280">Usaremos planos em nosso aplicativo para representar paredes, andares e tetos.</span><span class="sxs-lookup"><span data-stu-id="1e89a-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="1e89a-281">Esse pré-fabricado também inclui **RemoveSurfaceVertices.cs** que pode remover vértices da malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="1e89a-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="1e89a-282">Isso pode ser usado para criar buracos na malha ou para remover triângulos excedentes que não são mais necessários (porque os planos podem ser usados em vez disso).</span><span class="sxs-lookup"><span data-stu-id="1e89a-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="1e89a-283">Na pasta painel de **projeto** do Unity, **hologramas** , localize o objeto **spacecollection** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="1e89a-284">Arraste e solte o  objeto spacecollection no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1e89a-285">No painel **hierarquia** , selecione o objeto **SpatialProcessing** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="1e89a-286">No painel **Inspetor** , localize o componente **Gerenciador de espaço de reprodução (script)** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="1e89a-287">Clique duas vezes em **PlaySpaceManager.cs** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e89a-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="1e89a-288">PlaySpaceManager.cs contém código específico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="1e89a-289">Adicionaremos funcionalidade a esse script para habilitar o seguinte comportamento:</span><span class="sxs-lookup"><span data-stu-id="1e89a-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="1e89a-290">Parar de coletar dados de mapeamento espacial depois de excedermos o limite de tempo de verificação (10 segundos).</span><span class="sxs-lookup"><span data-stu-id="1e89a-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="1e89a-291">Processar os dados de mapeamento espacial:</span><span class="sxs-lookup"><span data-stu-id="1e89a-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="1e89a-292">Use o SurfaceMeshesToPlanes para criar uma representação mais simples do mundo como planos (paredes, andares, tetos, etc.).</span><span class="sxs-lookup"><span data-stu-id="1e89a-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="1e89a-293">Use RemoveSurfaceVertices para remover triângulos de superfície que se enquadram em limites de plano.</span><span class="sxs-lookup"><span data-stu-id="1e89a-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="1e89a-294">Gere uma coleção de hologramas no mundo e coloque-os nos planos de parede e piso próximos ao usuário.</span><span class="sxs-lookup"><span data-stu-id="1e89a-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="1e89a-295">Conclua os exercícios de codificação marcados em PlaySpaceManager.cs ou substitua o script pela solução concluída abaixo:</span><span class="sxs-lookup"><span data-stu-id="1e89a-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

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

<span data-ttu-id="1e89a-296">**Compilar e implantar**</span><span class="sxs-lookup"><span data-stu-id="1e89a-296">**Build and Deploy**</span></span>
* <span data-ttu-id="1e89a-297">Antes de implantar no HoloLens, pressione o botão **reproduzir** no Unity para entrar no modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="1e89a-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="1e89a-298">Depois que a malha de sala é carregada do arquivo, aguarde 10 segundos antes de o processamento começar na malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="1e89a-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="1e89a-299">Quando o processamento for concluído, os planos aparecerão para representar o piso, as paredes, o teto etc.</span><span class="sxs-lookup"><span data-stu-id="1e89a-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="1e89a-300">Depois que todos os planos forem encontrados, você verá que um sistema solar aparecerá em uma tabela de piso perto da câmera.</span><span class="sxs-lookup"><span data-stu-id="1e89a-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="1e89a-301">Dois cartazes devem aparecer em paredes próximas à câmera também.</span><span class="sxs-lookup"><span data-stu-id="1e89a-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="1e89a-302">Alterne para a guia **cena** se você não puder vê-las no modo de **jogo** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="1e89a-303">Pressione o botão **reproduzir** novamente para sair do modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="1e89a-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="1e89a-304">Crie e implante no HoloLens, como de costume.</span><span class="sxs-lookup"><span data-stu-id="1e89a-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="1e89a-305">Aguarde a verificação e o processamento dos dados de mapeamento espacial a serem concluídos.</span><span class="sxs-lookup"><span data-stu-id="1e89a-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="1e89a-306">Depois de ver os planos, tente encontrar o sistema solar e os pôsteres em seu mundo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="1e89a-307">Capítulo 4-posicionamento</span><span class="sxs-lookup"><span data-stu-id="1e89a-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="1e89a-308">**Seus**</span><span class="sxs-lookup"><span data-stu-id="1e89a-308">**Objectives**</span></span>
* <span data-ttu-id="1e89a-309">Determine se um holograma se ajustará em uma superfície.</span><span class="sxs-lookup"><span data-stu-id="1e89a-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="1e89a-310">Forneça comentários para o usuário quando um holograma puder/não couber em uma superfície.</span><span class="sxs-lookup"><span data-stu-id="1e89a-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="1e89a-311">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="1e89a-311">**Instructions**</span></span>
* <span data-ttu-id="1e89a-312">No painel **hierarquia** do Unity, selecione o objeto **SpatialProcessing** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="1e89a-313">No painel **Inspetor** , encontre as malhas da **superfície para o componente planos (script)** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="1e89a-314">Altere a propriedade **desenhar planos** para **nada** para limpar a seleção.</span><span class="sxs-lookup"><span data-stu-id="1e89a-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="1e89a-315">Altere a propriedade **desenhar planos** para a **parede**, de modo que somente os planos de parede serão renderizados.</span><span class="sxs-lookup"><span data-stu-id="1e89a-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="1e89a-316">Na pasta painel do **projeto** , **scripts** , clique duas vezes em **Placeable.cs** para abri-lo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e89a-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="1e89a-317">O  script posicionável já está anexado aos cartazes e à caixa de projeção criados após a conclusão da localização do plano.</span><span class="sxs-lookup"><span data-stu-id="1e89a-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="1e89a-318">Tudo o que precisamos fazer é remover o comentário de algum código, e esse script irá obter o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1e89a-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="1e89a-319">Determine se um holograma caberá em uma superfície por raycasting do centro e quatro cantos do cubo delimitador.</span><span class="sxs-lookup"><span data-stu-id="1e89a-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="1e89a-320">Verifique a superfície normal para determinar se ela é tranqüila o suficiente para que o holograma fique liberado.</span><span class="sxs-lookup"><span data-stu-id="1e89a-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="1e89a-321">Renderize um cubo delimitador em volta do holograma para mostrar seu tamanho real durante a colocação.</span><span class="sxs-lookup"><span data-stu-id="1e89a-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="1e89a-322">Converta uma sombra em/atrás do holograma para mostrar onde ele será colocado no chão/parede.</span><span class="sxs-lookup"><span data-stu-id="1e89a-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="1e89a-323">Renderize a sombra como vermelha, se o holograma não puder ser colocado na superfície, ou verde, se puder.</span><span class="sxs-lookup"><span data-stu-id="1e89a-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="1e89a-324">Reorientar o holograma para alinhar com o tipo de superfície (vertical ou horizontal) ao qual ele tem afinidade.</span><span class="sxs-lookup"><span data-stu-id="1e89a-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="1e89a-325">Posicione suavemente o holograma na superfície selecionada para evitar o comportamento de salto ou de ajuste.</span><span class="sxs-lookup"><span data-stu-id="1e89a-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="1e89a-326">Remova a marca de comentário de todo o código no exercício de codificação abaixo ou use essa solução concluída no **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="1e89a-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

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

<span data-ttu-id="1e89a-327">**Compilar e implantar**</span><span class="sxs-lookup"><span data-stu-id="1e89a-327">**Build and Deploy**</span></span>
* <span data-ttu-id="1e89a-328">Como antes, compile o projeto e implante-o no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1e89a-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="1e89a-329">Aguarde a verificação e o processamento dos dados de mapeamento espacial a serem concluídos.</span><span class="sxs-lookup"><span data-stu-id="1e89a-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="1e89a-330">Quando você vir o sistema solar, olhar na caixa de projeção abaixo e executar um gesto de seleção para movê-lo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="1e89a-331">Enquanto a caixa de projeção estiver selecionada, um cubo delimitador ficará visível na caixa de projeção.</span><span class="sxs-lookup"><span data-stu-id="1e89a-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="1e89a-332">Mova você para o olhar em um local diferente na sala.</span><span class="sxs-lookup"><span data-stu-id="1e89a-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="1e89a-333">A caixa de projeção deve seguir seu olhar.</span><span class="sxs-lookup"><span data-stu-id="1e89a-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="1e89a-334">Quando a sombra abaixo da caixa de projeção fica vermelha, não é possível posicionar o holograma nessa superfície.</span><span class="sxs-lookup"><span data-stu-id="1e89a-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="1e89a-335">Quando a sombra abaixo da caixa de projeção fica verde, você pode posicionar o holograma executando outro gesto de seleção.</span><span class="sxs-lookup"><span data-stu-id="1e89a-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="1e89a-336">Localize e selecione um dos pôsteres do Holographic em uma parede para movê-lo para um novo local.</span><span class="sxs-lookup"><span data-stu-id="1e89a-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="1e89a-337">Observe que você não pode posicionar o pôster no chão ou no teto e que ele permanece corretamente orientado a cada parede à medida que você se movimenta.</span><span class="sxs-lookup"><span data-stu-id="1e89a-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="1e89a-338">Capítulo 5-oclusão</span><span class="sxs-lookup"><span data-stu-id="1e89a-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="1e89a-339">**Seus**</span><span class="sxs-lookup"><span data-stu-id="1e89a-339">**Objectives**</span></span>
* <span data-ttu-id="1e89a-340">Determine se um holograma é obstruído pela malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="1e89a-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="1e89a-341">Aplique diferentes técnicas de oclusão para obter um efeito divertido.</span><span class="sxs-lookup"><span data-stu-id="1e89a-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="1e89a-342">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="1e89a-342">**Instructions**</span></span>

<span data-ttu-id="1e89a-343">Primeiro, vamos permitir que a malha de mapeamento espacial occlude outros hologramas sem occluding o mundo real:</span><span class="sxs-lookup"><span data-stu-id="1e89a-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="1e89a-344">No painel **hierarquia** , selecione o objeto **SpatialProcessing** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="1e89a-345">No painel **Inspetor** , localize o componente **Gerenciador de espaço de reprodução (script)** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="1e89a-346">Clique no círculo à direita da propriedade **material secundário** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="1e89a-347">Localize e selecione o material de **oclusão** e feche a janela.</span><span class="sxs-lookup"><span data-stu-id="1e89a-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="1e89a-348">Em seguida, vamos adicionar um comportamento especial à terra, para que ele tenha um realce azul sempre que ele se tornar obstruído por outro holograma (como o sol) ou pela malha de mapeamento espacial:</span><span class="sxs-lookup"><span data-stu-id="1e89a-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="1e89a-349">No painel **projeto** , na pasta **hologramas** , expanda o objeto **SolarSystem** .</span><span class="sxs-lookup"><span data-stu-id="1e89a-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="1e89a-350">Clique em **terra**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-350">Click on **Earth**.</span></span>
* <span data-ttu-id="1e89a-351">No painel **Inspetor** , encontre o material da terra (componente inferior).</span><span class="sxs-lookup"><span data-stu-id="1e89a-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="1e89a-352">Na **lista suspensa sombreador**, altere o sombreador para **personalizado > OcclusionRim**.</span><span class="sxs-lookup"><span data-stu-id="1e89a-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="1e89a-353">Isso processará um realce azul em volta da terra sempre que for obstruído por outro objeto.</span><span class="sxs-lookup"><span data-stu-id="1e89a-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="1e89a-354">Por fim, vamos habilitar um efeito de visão x-ray para planetas em nosso sistema solar.</span><span class="sxs-lookup"><span data-stu-id="1e89a-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="1e89a-355">Precisaremos editar **PlanetOcclusion.cs** (encontrado na pasta Scripts\SolarSystem) para obter o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1e89a-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="1e89a-356">Determine se um planeta é obstruídodo pela camada SpatialMapping (malhas e planos de sala).</span><span class="sxs-lookup"><span data-stu-id="1e89a-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="1e89a-357">Mostre a representação delineada de um planeta sempre que ele for obstruído pela camada SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="1e89a-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="1e89a-358">Oculte a representação delineada de um planeta quando ela não estiver bloqueada pela camada SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="1e89a-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="1e89a-359">Siga o exercício de codificação no PlanetOcclusion.cs ou use a seguinte solução:</span><span class="sxs-lookup"><span data-stu-id="1e89a-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

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

<span data-ttu-id="1e89a-360">**Compilar e implantar**</span><span class="sxs-lookup"><span data-stu-id="1e89a-360">**Build and Deploy**</span></span>
* <span data-ttu-id="1e89a-361">Crie e implante o aplicativo no HoloLens, como de costume.</span><span class="sxs-lookup"><span data-stu-id="1e89a-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="1e89a-362">Aguarde a verificação e o processamento dos dados de mapeamento espacial a serem concluídos (você deverá ver as linhas azuis aparecerem nas paredes).</span><span class="sxs-lookup"><span data-stu-id="1e89a-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="1e89a-363">Localize e selecione a caixa projeção do sistema solar e, em seguida, defina a caixa ao lado de uma parede ou atrás de um contador.</span><span class="sxs-lookup"><span data-stu-id="1e89a-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="1e89a-364">Você pode exibir os oclusão básicos ocultando as superfícies para o ponto no pôster ou na caixa de projeção.</span><span class="sxs-lookup"><span data-stu-id="1e89a-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="1e89a-365">Procure a terra, deve haver um efeito de realce azul sempre que ele ficar atrás de outro holograma ou de uma superfície.</span><span class="sxs-lookup"><span data-stu-id="1e89a-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="1e89a-366">Observe como os planetas se movem para trás da parede ou de outras superfícies na sala.</span><span class="sxs-lookup"><span data-stu-id="1e89a-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="1e89a-367">Agora você tem a visão x-ray e pode ver seus esqueletos de wireframe!</span><span class="sxs-lookup"><span data-stu-id="1e89a-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="1e89a-368">Fim</span><span class="sxs-lookup"><span data-stu-id="1e89a-368">The End</span></span>

<span data-ttu-id="1e89a-369">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="1e89a-369">Congratulations!</span></span> <span data-ttu-id="1e89a-370">Agora você concluiu **o Sr Spatial 230: Mapeamento**espacial.</span><span class="sxs-lookup"><span data-stu-id="1e89a-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="1e89a-371">Você sabe como verificar seu ambiente e carregar dados de mapeamento espacial para o Unity.</span><span class="sxs-lookup"><span data-stu-id="1e89a-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="1e89a-372">Você entende os conceitos básicos dos sombreadores e como os materiais podem ser usados para revisualizar o mundo.</span><span class="sxs-lookup"><span data-stu-id="1e89a-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="1e89a-373">Você aprendeu com novas técnicas de processamento para localizar planos e remover triângulos de uma malha.</span><span class="sxs-lookup"><span data-stu-id="1e89a-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="1e89a-374">Você conseguiu mover e posicionar hologramas em superfícies que faziam sentido.</span><span class="sxs-lookup"><span data-stu-id="1e89a-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="1e89a-375">Você experimentou técnicas oclusãos diferentes e aproveitou a potência da visão x-ray!</span><span class="sxs-lookup"><span data-stu-id="1e89a-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>

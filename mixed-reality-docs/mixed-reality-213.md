---
title: Entrada MR 213
description: Siga este tutorial de codificação usando o Unity, o Visual Studio e os headsets de imersão para aprender os detalhes dos controladores de movimento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, imersiva, controlador de movimento, Academia, tutorial
ms.openlocfilehash: e2199c3afed21f9396ed84f71093a8b2fb3bb23b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438550"
---
>[!NOTE]
><span data-ttu-id="c4366-104">Os tutoriais misturados do Academia de realidade foram projetados com o HoloLens (1º gen) e com o fone de cabeça de imersão de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4366-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c4366-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estão procurando orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c4366-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c4366-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas e as interações mais recentes usados para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c4366-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c4366-107">Eles serão mantidos para continuar a trabalhar nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="c4366-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c4366-108">[Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c4366-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="c4366-109">Entrada MR 213: controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="c4366-109">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="c4366-110">Os controladores de movimento no mundo da realidade misturada adicionam outro nível de interatividade.</span><span class="sxs-lookup"><span data-stu-id="c4366-110">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="c4366-111">Com os [controladores de movimento](motion-controllers.md), podemos interagir diretamente com objetos de forma mais natural, semelhante às nossas interações físicas na vida real, aumentando imersão e fascinam em sua experiência de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4366-111">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="c4366-112">No Sr Input 213, exploraremos os eventos de entrada do controlador de movimento criando uma experiência de pintura espacial simples.</span><span class="sxs-lookup"><span data-stu-id="c4366-112">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="c4366-113">Com esse aplicativo, os usuários podem pintar em espaço tridimensional com vários tipos de pincéis e cores.</span><span class="sxs-lookup"><span data-stu-id="c4366-113">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="c4366-114">Tópicos abordados neste tutorial</span><span class="sxs-lookup"><span data-stu-id="c4366-114">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="c4366-118">**Visualização do controlador**</span><span class="sxs-lookup"><span data-stu-id="c4366-118">**Controller visualization**</span></span>|<span data-ttu-id="c4366-119">**Eventos de entrada do controlador**</span><span class="sxs-lookup"><span data-stu-id="c4366-119">**Controller input events**</span></span>|<span data-ttu-id="c4366-120">**Controlador personalizado e interface do usuário**</span><span class="sxs-lookup"><span data-stu-id="c4366-120">**Custom controller and UI**</span></span>|
|<span data-ttu-id="c4366-121">Saiba como renderizar modelos de controlador de movimento no modo de jogo e em tempo de execução do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4366-121">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="c4366-122">Entenda os diferentes tipos de eventos de botão e seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c4366-122">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="c4366-123">Saiba como sobrepor elementos de interface do usuário na parte superior do controlador ou personalizá-lo totalmente.</span><span class="sxs-lookup"><span data-stu-id="c4366-123">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="c4366-124">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="c4366-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c4366-125">Course</span><span class="sxs-lookup"><span data-stu-id="c4366-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c4366-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c4366-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c4366-127"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="c4366-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c4366-128">Entrada MR 213: controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="c4366-128">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="c4366-129">✔️</span><span class="sxs-lookup"><span data-stu-id="c4366-129">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c4366-130">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="c4366-130">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c4366-131">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c4366-131">Prerequisites</span></span>

<span data-ttu-id="c4366-132">Consulte a lista de verificação da instalação para headsets de imersão nesta [página](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c4366-132">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="c4366-133">Este tutorial requer o [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="c4366-133">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="c4366-134">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="c4366-134">Project files</span></span>

* <span data-ttu-id="c4366-135">[Baixe os arquivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) exigidos pelo projeto e extraia os arquivos para a área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c4366-135">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="c4366-136">Se você quiser examinar o código-fonte antes de baixá-lo, ele [estará disponível no GitHub](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="c4366-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="c4366-137">Configuração do Unity</span><span class="sxs-lookup"><span data-stu-id="c4366-137">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="c4366-138">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4366-138">Objectives</span></span>

* <span data-ttu-id="c4366-139">Otimizar o Unity para o desenvolvimento de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="c4366-139">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="c4366-140">Configuração da câmera de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c4366-140">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="c4366-141">Ambiente de instalação</span><span class="sxs-lookup"><span data-stu-id="c4366-141">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="c4366-142">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-142">Instructions</span></span>

* <span data-ttu-id="c4366-143">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="c4366-143">Start Unity.</span></span>
* <span data-ttu-id="c4366-144">Selecione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="c4366-144">Select **Open**.</span></span>
* <span data-ttu-id="c4366-145">Navegue até sua área de trabalho e localize a pasta **MixedReality213-Master** que você desarquivou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c4366-145">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="c4366-146">Clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="c4366-146">Click **Select Folder**.</span></span>
* <span data-ttu-id="c4366-147">Depois que o Unity terminar de carregar arquivos de projeto, você poderá ver o editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4366-147">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="c4366-148">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="c4366-148">In Unity, select **File > Build Settings**.</span></span>

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* <span data-ttu-id="c4366-150">Selecione **plataforma universal do Windows** na lista **plataforma** e clique no botão **alternar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="c4366-150">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="c4366-151">Definir o dispositivo de destino para **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="c4366-151">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="c4366-152">Definir tipo de compilação como **D3D**</span><span class="sxs-lookup"><span data-stu-id="c4366-152">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="c4366-153">Definir o SDK para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="c4366-153">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="c4366-154">Verificar **projetos C# do Unity**</span><span class="sxs-lookup"><span data-stu-id="c4366-154">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="c4366-155">Isso permite que você modifique os arquivos de script no projeto do Visual Studio sem recriar o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4366-155">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="c4366-156">Clique em **configurações do Player**.</span><span class="sxs-lookup"><span data-stu-id="c4366-156">Click **Player Settings**.</span></span>
* <span data-ttu-id="c4366-157">No painel **Inspetor** , role para baixo até a parte inferior</span><span class="sxs-lookup"><span data-stu-id="c4366-157">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="c4366-158">Em configurações de XR, verifique a **realidade virtual com suporte**</span><span class="sxs-lookup"><span data-stu-id="c4366-158">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="c4366-159">Em SDKs de realidade virtual, selecione **realidade mista do Windows**</span><span class="sxs-lookup"><span data-stu-id="c4366-159">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* <span data-ttu-id="c4366-161">Feche a janela **configurações de compilação** .</span><span class="sxs-lookup"><span data-stu-id="c4366-161">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="c4366-162">Estrutura do projeto</span><span class="sxs-lookup"><span data-stu-id="c4366-162">Project structure</span></span>

<span data-ttu-id="c4366-163">Este tutorial usa o **[Kit de ferramentas de realidade misturada-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** .</span><span class="sxs-lookup"><span data-stu-id="c4366-163">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="c4366-164">Você pode encontrar as versões nesta [página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="c4366-164">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="c4366-166">**Cenas concluídas para sua referência**</span><span class="sxs-lookup"><span data-stu-id="c4366-166">**Completed scenes for your reference**</span></span>

* <span data-ttu-id="c4366-167">Você encontrará duas cenas de Unity concluídas na pasta de **cenas** .</span><span class="sxs-lookup"><span data-stu-id="c4366-167">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="c4366-168">**MixedReality213**: cena concluída com pincel único</span><span class="sxs-lookup"><span data-stu-id="c4366-168">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="c4366-169">**MixedReality213Advanced**: cena concluída para design avançado com vários pincéis</span><span class="sxs-lookup"><span data-stu-id="c4366-169">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="c4366-170">**Nova configuração de cena para o tutorial**</span><span class="sxs-lookup"><span data-stu-id="c4366-170">**New Scene setup for the tutorial**</span></span>

* <span data-ttu-id="c4366-171">No Unity, clique em **arquivo > nova cena**</span><span class="sxs-lookup"><span data-stu-id="c4366-171">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="c4366-172">Excluir a **câmera principal** e a **luz direcional**</span><span class="sxs-lookup"><span data-stu-id="c4366-172">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="c4366-173">No **painel Projeto**, pesquise e arraste o seguinte pré-fabricados para o painel **hierarquia** :</span><span class="sxs-lookup"><span data-stu-id="c4366-173">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="c4366-174">Assets/HoloToolkit/Input/pré-fabricados/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="c4366-174">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="c4366-175">Ativos/AppPrefabs/**ambiente**</span><span class="sxs-lookup"><span data-stu-id="c4366-175">Assets/AppPrefabs/**Environment**</span></span>

    ![Câmera e ambiente](images/mr213-cameraenvironment-300px.jpg)

* <span data-ttu-id="c4366-177">Há duas pré-fabricados de câmera no kit de ferramentas de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="c4366-177">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="c4366-178">**MixedRealityCamera. pré-fabricado**: câmera somente</span><span class="sxs-lookup"><span data-stu-id="c4366-178">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="c4366-179">**MixedRealityCameraParent. pré-fabricado**: câmera + Teleportation + limite</span><span class="sxs-lookup"><span data-stu-id="c4366-179">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="c4366-180">Neste tutorial, usaremos o **MixedRealityCamera** sem o recurso de Teleportation.</span><span class="sxs-lookup"><span data-stu-id="c4366-180">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="c4366-181">Por isso, adicionamos um **ambiente** simples pré-fabricado que contém uma base básica para fazer com que o usuário se sinta à vontade.</span><span class="sxs-lookup"><span data-stu-id="c4366-181">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="c4366-182">Para saber mais sobre a teleportabilidade com o **MixedRealityCameraParent**, consulte [design avançado – Teleportation e Locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="c4366-182">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="c4366-183">**Configuração do Skybox**</span><span class="sxs-lookup"><span data-stu-id="c4366-183">**Skybox setup**</span></span>

* <span data-ttu-id="c4366-184">Clique em **janela > iluminação > configurações**</span><span class="sxs-lookup"><span data-stu-id="c4366-184">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="c4366-185">Clique no círculo no lado direito do **campo material de Skybox**</span><span class="sxs-lookup"><span data-stu-id="c4366-185">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="c4366-186">Digite "Gray" e selecione **SkyboxGray** (ativos/AppPrefabs/suporte/materiais/SkyboxGray. passe-partout)</span><span class="sxs-lookup"><span data-stu-id="c4366-186">Type in ‘gray’ and select **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

    ![Configurando Skybox](images/mr123-skyboxsetting-400px.jpg)

* <span data-ttu-id="c4366-188">Marque a opção **Skybox** para poder ver Skybox gradiente cinza atribuído</span><span class="sxs-lookup"><span data-stu-id="c4366-188">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

    ![Alternar opção Skybox](images/mr213-skyboxcheck-400px.jpg)

* <span data-ttu-id="c4366-190">A cena com MixedRealityCamera, ambiente e Skybox cinza terá a seguinte aparência.</span><span class="sxs-lookup"><span data-stu-id="c4366-190">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

    ![Ambiente MixedReality213](images/mr213-environment-600px.jpg)

* <span data-ttu-id="c4366-192">Clique em **arquivo > salvar cena como**</span><span class="sxs-lookup"><span data-stu-id="c4366-192">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="c4366-193">**Salve** sua cena na pasta de cenas com qualquer nome</span><span class="sxs-lookup"><span data-stu-id="c4366-193">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="c4366-194">Capítulo 1-visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="c4366-194">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="c4366-195">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4366-195">Objectives</span></span>

* <span data-ttu-id="c4366-196">Saiba como renderizar modelos de controlador de movimento no modo de jogo do Unity e em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c4366-196">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="c4366-197">O Windows Mixed Reality fornece um modelo de controlador animado para a visualização do controlador.</span><span class="sxs-lookup"><span data-stu-id="c4366-197">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="c4366-198">Há várias abordagens que você pode tomar para a visualização do controlador em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c4366-198">There are several approaches you can take for controller visualization in your app:</span></span>

* <span data-ttu-id="c4366-199">Padrão-usando o controlador padrão sem modificação</span><span class="sxs-lookup"><span data-stu-id="c4366-199">Default - Using default controller without modification</span></span>
* <span data-ttu-id="c4366-200">Híbrido-usando o controlador padrão, mas Personalizando alguns de seus elementos ou sobrepondo componentes de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c4366-200">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="c4366-201">Substituição-usando seu próprio modelo 3D personalizado para o controlador</span><span class="sxs-lookup"><span data-stu-id="c4366-201">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="c4366-202">Neste capítulo, aprenderemos sobre os exemplos dessas personalizações do controlador.</span><span class="sxs-lookup"><span data-stu-id="c4366-202">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="c4366-203">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-203">Instructions</span></span>

* <span data-ttu-id="c4366-204">No painel **projeto** , digite **MotionControllers** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c4366-204">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="c4366-205">Você também pode encontrá-lo em assets/HoloToolkit/Input/pré-fabricados/.</span><span class="sxs-lookup"><span data-stu-id="c4366-205">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="c4366-206">Arraste **MotionControllers** pré-fabricado para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-206">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-207">Clique em **MotionControllers** pré-fabricado no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-207">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="c4366-208">**MotionControllers pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="c4366-208">**MotionControllers prefab**</span></span>

<span data-ttu-id="c4366-209">**MotionControllers** pré-fabricado tem um script **MotionControllerVisualizer** que fornece os slots para modelos de controlador alternativos.</span><span class="sxs-lookup"><span data-stu-id="c4366-209">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="c4366-210">Se você atribuir seus próprios modelos 3D personalizados, como uma mão ou um gumes, e marcar a opção ' sempre usar o modelo alternativo esquerdo/direito ', você os verá em vez do modelo padrão.</span><span class="sxs-lookup"><span data-stu-id="c4366-210">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="c4366-211">Usaremos esse slot no capítulo 4 para substituir o modelo do controlador por um pincel.</span><span class="sxs-lookup"><span data-stu-id="c4366-211">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="c4366-213">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="c4366-213">**Instructions**</span></span>

* <span data-ttu-id="c4366-214">No painel **Inspetor** , clique duas vezes em script **MotionControllerVisualizer** para ver o código no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c4366-214">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="c4366-215">**Script MotionControllerVisualizer**</span><span class="sxs-lookup"><span data-stu-id="c4366-215">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="c4366-216">As classes **MotionControllerVisualizer** e **MotionControllerInfo** fornecem os meios para acessar & modificar os modelos de controlador padrão.</span><span class="sxs-lookup"><span data-stu-id="c4366-216">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="c4366-217">**MotionControllerVisualizer** assina o evento **InteractionSourceDetected** do Unity e instancia automaticamente os modelos do controlador quando eles são encontrados.</span><span class="sxs-lookup"><span data-stu-id="c4366-217">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="c4366-218">Os modelos de controlador são fornecidos de acordo com [a especificação glTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="c4366-218">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="c4366-219">Esse formato foi criado para fornecer um formato comum, ao mesmo tempo em que melhora o processo por trás da transmissão e desempacotamento de ativos 3D.</span><span class="sxs-lookup"><span data-stu-id="c4366-219">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="c4366-220">Nesse caso, precisamos recuperar e carregar os modelos de controlador em tempo de execução, pois queremos tornar a experiência do usuário o mais direta possível e não há garantia de qual versão dos controladores de movimento o usuário pode estar usando.</span><span class="sxs-lookup"><span data-stu-id="c4366-220">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="c4366-221">Este curso, por meio do kit de ferramentas de realidade misturada, usa uma versão do [projeto UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)do grupo Khronos.</span><span class="sxs-lookup"><span data-stu-id="c4366-221">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="c4366-222">Depois que o controlador foi entregue, os scripts podem usar o **MotionControllerInfo** para localizar as transformações de elementos específicos do controlador para que eles possam se posicionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="c4366-222">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="c4366-223">Em um capítulo posterior, veremos como usar esses scripts para anexar elementos de interface do usuário aos controladores.</span><span class="sxs-lookup"><span data-stu-id="c4366-223">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="c4366-224">*Em alguns scripts, você encontrará blocos de código com **#if! UNITY_EDITOR** ou **UNITY_WSA**. Esses blocos de código são executados somente no tempo de execução do UWP quando você implanta no Windows. Isso ocorre porque o conjunto de APIs usado pelo editor do Unity e o tempo de execução do aplicativo UWP são diferentes.*</span><span class="sxs-lookup"><span data-stu-id="c4366-224">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>

* <span data-ttu-id="c4366-225">**Salve** a cena e clique no botão **reproduzir** .</span><span class="sxs-lookup"><span data-stu-id="c4366-225">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="c4366-226">Você poderá ver a cena com os controladores de movimento em seu headset.</span><span class="sxs-lookup"><span data-stu-id="c4366-226">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="c4366-227">Você pode ver animações detalhadas para cliques de botão, movimentação de Thumbstick e realce de toque do touchpad.</span><span class="sxs-lookup"><span data-stu-id="c4366-227">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![Padrão de visualização de MR213_Controller](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="c4366-229">Capítulo 2-anexando elementos da interface do usuário ao controlador</span><span class="sxs-lookup"><span data-stu-id="c4366-229">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="c4366-230">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4366-230">Objectives</span></span>

* <span data-ttu-id="c4366-231">Saiba mais sobre os elementos dos controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="c4366-231">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="c4366-232">Saiba como anexar objetos a partes específicas dos controladores</span><span class="sxs-lookup"><span data-stu-id="c4366-232">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="c4366-233">Neste capítulo, você aprenderá a adicionar elementos de interface do usuário ao controlador que o usuário pode acessar e manipular facilmente a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="c4366-233">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="c4366-234">Você também aprenderá a adicionar uma interface do usuário de seletor de cor simples usando a entrada do touchpad.</span><span class="sxs-lookup"><span data-stu-id="c4366-234">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="c4366-235">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-235">Instructions</span></span>

* <span data-ttu-id="c4366-236">No painel **projeto** , pesquise o script **MotionControllerInfo** .</span><span class="sxs-lookup"><span data-stu-id="c4366-236">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="c4366-237">No resultado da pesquisa, clique duas vezes em **MotionControllerInfo** script para ver o código no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4366-237">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="c4366-238">**Script MotionControllerInfo**</span><span class="sxs-lookup"><span data-stu-id="c4366-238">**MotionControllerInfo script**</span></span>

<span data-ttu-id="c4366-239">A primeira etapa é escolher o elemento do controlador ao qual você deseja que a interface do usuário seja anexada.</span><span class="sxs-lookup"><span data-stu-id="c4366-239">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="c4366-240">Esses elementos são definidos em **ControllerElementEnum** em **MotionControllerInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="c4366-240">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* <span data-ttu-id="c4366-242">**Casa**</span><span class="sxs-lookup"><span data-stu-id="c4366-242">**Home**</span></span>
* <span data-ttu-id="c4366-243">**AdicionarMenu**</span><span class="sxs-lookup"><span data-stu-id="c4366-243">**Menu**</span></span>
* <span data-ttu-id="c4366-244">**Compreendi**</span><span class="sxs-lookup"><span data-stu-id="c4366-244">**Grasp**</span></span>
* <span data-ttu-id="c4366-245">**Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="c4366-245">**Thumbstick**</span></span>
* <span data-ttu-id="c4366-246">**Não**</span><span class="sxs-lookup"><span data-stu-id="c4366-246">**Select**</span></span>
* <span data-ttu-id="c4366-247">**Touchpad**</span><span class="sxs-lookup"><span data-stu-id="c4366-247">**Touchpad**</span></span>
* <span data-ttu-id="c4366-248">**Pose de ponteiro** – esse elemento representa a ponta da direção do encaminhamento do controlador.</span><span class="sxs-lookup"><span data-stu-id="c4366-248">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="c4366-249">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="c4366-249">**Instructions**</span></span>

* <span data-ttu-id="c4366-250">No painel **projeto** , pesquise o script **AttachToController** .</span><span class="sxs-lookup"><span data-stu-id="c4366-250">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="c4366-251">No resultado da pesquisa, clique duas vezes em **AttachToController** script para ver o código no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4366-251">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="c4366-252">**Script AttachToController**</span><span class="sxs-lookup"><span data-stu-id="c4366-252">**AttachToController script**</span></span>

<span data-ttu-id="c4366-253">O script **AttachToController** fornece uma maneira simples de anexar quaisquer objetos a um elemento e destro/canhoto do controlador especificado.</span><span class="sxs-lookup"><span data-stu-id="c4366-253">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="c4366-254">Em **AttachElementToController ()** ,</span><span class="sxs-lookup"><span data-stu-id="c4366-254">In **AttachElementToController()**,</span></span>

* <span data-ttu-id="c4366-255">Confira destromente usando **MotionControllerInfo. destroly**</span><span class="sxs-lookup"><span data-stu-id="c4366-255">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="c4366-256">Obter um elemento específico do controlador usando **MotionControllerInfo. TryGetElement ()**</span><span class="sxs-lookup"><span data-stu-id="c4366-256">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="c4366-257">Depois de recuperar a transformação do elemento do modelo do controlador, pai o objeto abaixo dele e definir a posição local do objeto & rotação como zero.</span><span class="sxs-lookup"><span data-stu-id="c4366-257">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="c4366-258">A maneira mais simples de usar o script **AttachToController** é herdar dele, como fizemos no caso de **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="c4366-258">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="c4366-259">Basta substituir as funções **OnAttachToController** e **OnDetatchFromController** para executar sua configuração/divisão quando o controlador for detectado/desconectado.</span><span class="sxs-lookup"><span data-stu-id="c4366-259">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="c4366-260">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="c4366-260">**Instructions**</span></span>

* <span data-ttu-id="c4366-261">No painel **projeto** , digite na caixa de pesquisa **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="c4366-261">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="c4366-262">Você também pode encontrá-lo em ativos/AppPrefabs/.</span><span class="sxs-lookup"><span data-stu-id="c4366-262">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="c4366-263">Arraste **ColorPickerWheel** pré-fabricado para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-263">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-264">Clique no **ColorPickerWheel** pré-fabricado no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-264">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-265">No painel **Inspetor** , clique duas vezes em **ColorPickerWheel** script para ver o código no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4366-265">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel pré-fabricado](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="c4366-267">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="c4366-267">**ColorPickerWheel script**</span></span>

<span data-ttu-id="c4366-268">Como **ColorPickerWheel** herda **AttachToController**, ele mostra **destroly** e **Element** no painel de **inspetores** .</span><span class="sxs-lookup"><span data-stu-id="c4366-268">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="c4366-269">Vamos anexar a interface do usuário ao elemento Touchpad no controlador à esquerda.</span><span class="sxs-lookup"><span data-stu-id="c4366-269">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="c4366-271">**ColorPickerWheel** substitui o **OnAttachToController** e o **OnDetatchFromController** para assinar o evento de entrada que será usado no próximo capítulo para seleção de cores com entrada do touchpad.</span><span class="sxs-lookup"><span data-stu-id="c4366-271">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* <span data-ttu-id="c4366-272">**Salve** a cena e clique no botão **reproduzir** .</span><span class="sxs-lookup"><span data-stu-id="c4366-272">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="c4366-273">**Método alternativo para anexar objetos aos controladores**</span><span class="sxs-lookup"><span data-stu-id="c4366-273">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="c4366-274">É recomendável que seus scripts herdem de **AttachToController** e substituam **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="c4366-274">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="c4366-275">No entanto, isso nem sempre pode ser possível.</span><span class="sxs-lookup"><span data-stu-id="c4366-275">However, this may not always be possible.</span></span> <span data-ttu-id="c4366-276">Uma alternativa é usá-lo como um componente autônomo.</span><span class="sxs-lookup"><span data-stu-id="c4366-276">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="c4366-277">Isso pode ser útil quando você deseja anexar um pré-fabricado existente a um controlador sem refatorar seus scripts.</span><span class="sxs-lookup"><span data-stu-id="c4366-277">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="c4366-278">Basta ter a sua classe aguardar que isanexou seja definido como true antes de executar qualquer configuração.</span><span class="sxs-lookup"><span data-stu-id="c4366-278">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="c4366-279">A maneira mais simples de fazer isso é usando uma corrotina para ' Iniciar '.</span><span class="sxs-lookup"><span data-stu-id="c4366-279">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="c4366-280">Capítulo 3-trabalhando com entrada do Touchpad</span><span class="sxs-lookup"><span data-stu-id="c4366-280">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="c4366-281">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4366-281">Objectives</span></span>

* <span data-ttu-id="c4366-282">Saiba como obter eventos de dados de entrada do Touchpad</span><span class="sxs-lookup"><span data-stu-id="c4366-282">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="c4366-283">Saiba como usar informações de posição do eixo do Touchpad para sua experiência de aplicativo</span><span class="sxs-lookup"><span data-stu-id="c4366-283">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="c4366-284">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-284">Instructions</span></span>

* <span data-ttu-id="c4366-285">No painel **hierarquia** , clique em **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="c4366-285">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="c4366-286">No painel **Inspetor** , em **animatior**, clique duas vezes em **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="c4366-286">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="c4366-287">Você poderá ver a guia **Animator** aberta</span><span class="sxs-lookup"><span data-stu-id="c4366-287">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="c4366-288">**Mostrando/ocultando a interface do usuário com o controlador de animação do Unity**</span><span class="sxs-lookup"><span data-stu-id="c4366-288">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="c4366-289">Para mostrar e ocultar a interface do usuário do **amColorPickerWheel** com animação, estamos usando o [sistema de animação do Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="c4366-289">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="c4366-290">Definir a propriedade **Visible** do **ColorPickerWheel**como true ou false triggers **mostra** e **oculta** os gatilhos de animação.</span><span class="sxs-lookup"><span data-stu-id="c4366-290">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="c4366-291">Os parâmetros **show** e **Hide** são definidos no controlador de animação **ColorPickerWheelController** .</span><span class="sxs-lookup"><span data-stu-id="c4366-291">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Controlador de animação Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="c4366-293">**Sobre**</span><span class="sxs-lookup"><span data-stu-id="c4366-293">**Instructions**</span></span>

* <span data-ttu-id="c4366-294">No painel **hierarquia** , selecione **ColorPickerWheel** pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="c4366-294">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="c4366-295">No painel **Inspetor** , clique duas vezes em script **ColorPickerWheel** para ver o código no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c4366-295">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="c4366-296">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="c4366-296">**ColorPickerWheel script**</span></span>

<span data-ttu-id="c4366-297">**ColorPickerWheel** assina o evento **InteractionSourceUpdated** do Unity para escutar eventos do touchpad.</span><span class="sxs-lookup"><span data-stu-id="c4366-297">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="c4366-298">Em **InteractionSourceUpdated ()** , o script primeiro verifica se ele:</span><span class="sxs-lookup"><span data-stu-id="c4366-298">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>

* <span data-ttu-id="c4366-299">é, na verdade, um evento de Touchpad (obj. State. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="c4366-299">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="c4366-300">origina-se do controlador à esquerda (obj. State. Source. **destro/canhoto**)</span><span class="sxs-lookup"><span data-stu-id="c4366-300">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="c4366-301">Se ambos forem verdadeiros, a posição do Touchpad (obj. State. **touchpadPosition**) é atribuído a **selectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="c4366-301">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="c4366-302">Em **Update ()** , com base na propriedade **Visible** , ele dispara mostrar e ocultar gatilhos de animação no componente Animator do seletor de cores</span><span class="sxs-lookup"><span data-stu-id="c4366-302">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="c4366-303">Em **Update ()** , **selectorPosition** é usado para converter um raio no Colisor de malha da roda de cores, que retorna uma posição UV.</span><span class="sxs-lookup"><span data-stu-id="c4366-303">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="c4366-304">Essa posição pode ser usada para localizar a coordenada de pixel e o valor de cor da textura da roda de cores.</span><span class="sxs-lookup"><span data-stu-id="c4366-304">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="c4366-305">Esse valor é acessível a outros scripts por meio da propriedade **SelectedColor** .</span><span class="sxs-lookup"><span data-stu-id="c4366-305">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Seletor de cores raycasting de roda](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="c4366-307">Capítulo 4-substituindo modelo de controlador</span><span class="sxs-lookup"><span data-stu-id="c4366-307">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="c4366-308">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4366-308">Objectives</span></span>

* <span data-ttu-id="c4366-309">Saiba como substituir o modelo do controlador por um modelo 3D personalizado.</span><span class="sxs-lookup"><span data-stu-id="c4366-309">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="c4366-311">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-311">Instructions</span></span>

* <span data-ttu-id="c4366-312">Clique em **MotionControllers** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-312">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-313">Clique no círculo no lado direito do campo **controlador alternativo direito** .</span><span class="sxs-lookup"><span data-stu-id="c4366-313">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="c4366-314">Digite **' BrushController**' e selecione o pré-fabricado do resultado.</span><span class="sxs-lookup"><span data-stu-id="c4366-314">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="c4366-315">Você pode encontrá-lo em ativos/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="c4366-315">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="c4366-316">Marque **sempre usar modelo alternativo correto**</span><span class="sxs-lookup"><span data-stu-id="c4366-316">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="c4366-318">O **BrushController** pré-fabricado não precisa ser incluído no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-318">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="c4366-319">No entanto, para conferir seus componentes filho:</span><span class="sxs-lookup"><span data-stu-id="c4366-319">However, to check out its child components:</span></span>

* <span data-ttu-id="c4366-320">No painel **projeto** , digite **BrushController** e arraste **BrushController** pré-fabricado para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-320">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="c4366-322">Você encontrará o componente de **dica** em **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="c4366-322">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="c4366-323">Usaremos sua transformação para iniciar/parar as linhas de desenho.</span><span class="sxs-lookup"><span data-stu-id="c4366-323">We will use its transform to start/stop drawing lines.</span></span>

* <span data-ttu-id="c4366-324">Exclua o **BrushController** do painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-324">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-325">**Salve** a cena e clique no botão **reproduzir** .</span><span class="sxs-lookup"><span data-stu-id="c4366-325">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="c4366-326">Você poderá ver o modelo de pincel substituiu o controlador de movimento à direita.</span><span class="sxs-lookup"><span data-stu-id="c4366-326">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="c4366-327">Capítulo 5-pintura com selecionar entrada</span><span class="sxs-lookup"><span data-stu-id="c4366-327">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="c4366-328">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4366-328">Objectives</span></span>

* <span data-ttu-id="c4366-329">Saiba como usar o evento de botão SELECT para iniciar e parar um desenho de linha</span><span class="sxs-lookup"><span data-stu-id="c4366-329">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="c4366-330">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-330">Instructions</span></span>

* <span data-ttu-id="c4366-331">Pesquise **BrushController** pré-fabricado no painel de **projeto** .</span><span class="sxs-lookup"><span data-stu-id="c4366-331">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="c4366-332">No painel **Inspetor** , clique duas vezes em script **BrushController** para ver o código no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c4366-332">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="c4366-333">**Script BrushController**</span><span class="sxs-lookup"><span data-stu-id="c4366-333">**BrushController script**</span></span>

<span data-ttu-id="c4366-334">**BrushController** assina os eventos **InteractionSourcePressed** e **InteractionSourceReleased** de interactionmanager.</span><span class="sxs-lookup"><span data-stu-id="c4366-334">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="c4366-335">Quando o evento **InteractionSourcePressed** é disparado, a propriedade **draw** do pincel é definida como true; Quando o evento **InteractionSourceReleased** é disparado, a propriedade **draw** do pincel é definida como false.</span><span class="sxs-lookup"><span data-stu-id="c4366-335">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="c4366-336">Enquanto **draw** estiver definido como true, o pincel gerará pontos em um **LineRenderer**de Unity instanciado.</span><span class="sxs-lookup"><span data-stu-id="c4366-336">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="c4366-337">Uma referência a esse pré-fabricado é mantida no campo de **pré-fabricado de traço** do pincel.</span><span class="sxs-lookup"><span data-stu-id="c4366-337">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="c4366-338">Para usar a cor atualmente selecionada na interface do usuário da roda do seletor de cores, **BrushController** precisa ter uma referência ao objeto **ColorPickerWheel** .</span><span class="sxs-lookup"><span data-stu-id="c4366-338">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="c4366-339">Como o **BrushController** pré-fabricado é instanciado em tempo de execução como um controlador de substituição, todas as referências a objetos na cena precisarão ser definidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c4366-339">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="c4366-340">Nesse caso, usamos **gameobject. FindObjectOfType** para localizar o **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="c4366-340">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* <span data-ttu-id="c4366-341">**Salve** a cena e clique no botão **reproduzir** .</span><span class="sxs-lookup"><span data-stu-id="c4366-341">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="c4366-342">Você poderá desenhar as linhas e pintar usando o botão Selecionar no controlador à direita.</span><span class="sxs-lookup"><span data-stu-id="c4366-342">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="c4366-343">Capítulo 6-gerando objeto com a entrada SELECT</span><span class="sxs-lookup"><span data-stu-id="c4366-343">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="c4366-344">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c4366-344">Objectives</span></span>

* <span data-ttu-id="c4366-345">Saiba como usar os eventos de entrada do botão Selecionar e entender</span><span class="sxs-lookup"><span data-stu-id="c4366-345">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="c4366-346">Saiba como criar uma instância de objetos</span><span class="sxs-lookup"><span data-stu-id="c4366-346">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="c4366-347">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-347">Instructions</span></span>

* <span data-ttu-id="c4366-348">No painel **projeto** , digite **objectgerador** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c4366-348">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="c4366-349">Você também pode encontrá-lo em ativos/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="c4366-349">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="c4366-350">Arraste o **Objectgerador** pré-fabricado para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-350">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-351">Clique em **Objectgerador** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-351">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-352">**Objectgerador** tem um campo denominado **fonte de cores**.</span><span class="sxs-lookup"><span data-stu-id="c4366-352">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="c4366-353">No painel **hierarquia** , arraste a referência **ColorPickerWheel** para esse campo.</span><span class="sxs-lookup"><span data-stu-id="c4366-353">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

    ![Inspetor de objeto](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* <span data-ttu-id="c4366-355">Clique no pré-fabricado do **Objectgerador** no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-355">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-356">No painel **Inspetor** , clique duas vezes em script de **objectgerador** para ver o código no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4366-356">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="c4366-357">**Script objectgerador**</span><span class="sxs-lookup"><span data-stu-id="c4366-357">**ObjectSpawner script**</span></span>

<span data-ttu-id="c4366-358">O **Objectgerador** instancia cópias de uma malha primitiva (cubo, esfera, cilindro) para o espaço.</span><span class="sxs-lookup"><span data-stu-id="c4366-358">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="c4366-359">Quando um **InteractionSourcePressed** é detectado, ele verifica a destro/canhoto e, se for um evento **InteractionSourcePressType. Segure** ou **InteractionSourcePressType. Select** .</span><span class="sxs-lookup"><span data-stu-id="c4366-359">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="c4366-360">Para um evento **Segure** , ele incrementa o índice do tipo de malha atual (Sphere, Cube, cilindro)</span><span class="sxs-lookup"><span data-stu-id="c4366-360">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="c4366-361">Para um evento **Select** , em CodeObject **()** , um novo objeto é instanciado, não pai e liberado no mundo.</span><span class="sxs-lookup"><span data-stu-id="c4366-361">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="c4366-362">O **Objectgerador** usa o **ColorPickerWheel** para definir a cor do material do objeto de exibição.</span><span class="sxs-lookup"><span data-stu-id="c4366-362">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="c4366-363">Os objetos gerados recebem uma instância desse material para que eles retenham sua cor.</span><span class="sxs-lookup"><span data-stu-id="c4366-363">Spawned objects are given an instance of this material so they will retain their color.</span></span>

* <span data-ttu-id="c4366-364">**Salve** a cena e clique no botão **reproduzir** .</span><span class="sxs-lookup"><span data-stu-id="c4366-364">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="c4366-365">Você poderá alterar os objetos com o botão compreender e gerar objetos com o botão Selecionar.</span><span class="sxs-lookup"><span data-stu-id="c4366-365">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="c4366-366">Criar e implantar o aplicativo no portal de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c4366-366">Build and deploy app to Mixed Reality Portal</span></span>

* <span data-ttu-id="c4366-367">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="c4366-367">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="c4366-368">Clique em **Adicionar abrir cenas** para adicionar a cena atual às **cenas na compilação**.</span><span class="sxs-lookup"><span data-stu-id="c4366-368">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="c4366-369">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="c4366-369">Click **Build**.</span></span>
* <span data-ttu-id="c4366-370">Crie uma **nova pasta** chamada "app".</span><span class="sxs-lookup"><span data-stu-id="c4366-370">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="c4366-371">Clique uma vez na pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="c4366-371">Single click the **App** folder.</span></span>
* <span data-ttu-id="c4366-372">Clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="c4366-372">Click **Select Folder**.</span></span>
* <span data-ttu-id="c4366-373">Quando o Unity for concluído, uma janela Explorador de arquivos será exibida.</span><span class="sxs-lookup"><span data-stu-id="c4366-373">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="c4366-374">Abra a pasta do **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="c4366-374">Open the **App** folder.</span></span>
* <span data-ttu-id="c4366-375">Clique duas vezes em arquivo de solução do Visual Studio **YourSceneName. sln** .</span><span class="sxs-lookup"><span data-stu-id="c4366-375">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="c4366-376">Usando a barra de ferramentas superior no Visual Studio, altere o destino de debug para **Release** e de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="c4366-376">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="c4366-377">Clique na seta suspensa ao lado do botão dispositivo e selecione **computador local**.</span><span class="sxs-lookup"><span data-stu-id="c4366-377">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="c4366-378">Clique em **depurar-> iniciar sem Depurar** no menu ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c4366-378">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="c4366-379">Agora, o aplicativo é criado e instalado no portal de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4366-379">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="c4366-380">Você pode iniciá-lo novamente por meio do menu iniciar no portal de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c4366-380">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="c4366-381">Design avançado – ferramentas de pincel com layout radial</span><span class="sxs-lookup"><span data-stu-id="c4366-381">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 principal](images/mr213-main-600px.jpg)

<span data-ttu-id="c4366-383">Neste capítulo, você aprenderá a substituir o modelo de controlador de movimento padrão por uma coleção de ferramentas de pincel personalizada.</span><span class="sxs-lookup"><span data-stu-id="c4366-383">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="c4366-384">Para sua referência, você pode encontrar o **MixedReality213Advanced** de cena concluído na pasta de **cenas** .</span><span class="sxs-lookup"><span data-stu-id="c4366-384">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="c4366-385">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-385">Instructions</span></span>

* <span data-ttu-id="c4366-386">No painel **projeto** , digite **BrushSelector** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c4366-386">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="c4366-387">Você também pode encontrá-lo em ativos/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="c4366-387">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="c4366-388">Arraste **BrushSelector** pré-fabricado para o painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-388">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-389">Para a organização, crie um gameobject vazio chamado **pincéis**</span><span class="sxs-lookup"><span data-stu-id="c4366-389">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="c4366-390">Arraste o pré-fabricados a seguir do painel de **projeto** para **pincéis**</span><span class="sxs-lookup"><span data-stu-id="c4366-390">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="c4366-391">Ativos/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="c4366-391">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="c4366-392">Ativos/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="c4366-392">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="c4366-393">Ativos/AppPrefabs/**borracha**</span><span class="sxs-lookup"><span data-stu-id="c4366-393">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="c4366-394">Ativos/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="c4366-394">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="c4366-395">Ativos/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="c4366-395">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="c4366-396">Ativos/AppPrefabs/**lápis**</span><span class="sxs-lookup"><span data-stu-id="c4366-396">Assets/AppPrefabs/**Pencil**</span></span>

    ![Pincéis](images/mixedreality213-brushes-250px.png)

* <span data-ttu-id="c4366-398">Clique em **MotionControllers** pré-fabricado no painel **hierarquia** .</span><span class="sxs-lookup"><span data-stu-id="c4366-398">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="c4366-399">No painel **Inspetor** , desmarque **sempre usar o modelo alternativo à direita** no **Visualizador do controlador de movimento**</span><span class="sxs-lookup"><span data-stu-id="c4366-399">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="c4366-400">No painel **hierarquia** , clique em **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="c4366-400">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="c4366-401">**BrushSelector** tem um campo chamado **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="c4366-401">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="c4366-402">No painel **hierarquia** , arraste o **ColorPickerWheel** para o campo **ColorPicker** no painel **Inspetor** .</span><span class="sxs-lookup"><span data-stu-id="c4366-402">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

    ![Atribuir ColorPickerWheel ao seletor de pincel](images/mr213-brushselector-500px.jpg)

* <span data-ttu-id="c4366-404">No painel **hierarquia** , em **BrushSelector** pré-fabricado, selecione o objeto de **menu** .</span><span class="sxs-lookup"><span data-stu-id="c4366-404">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="c4366-405">No painel **Inspetor** , no componente **LineObjectCollection** , abra a lista suspensa **objetos** matriz.</span><span class="sxs-lookup"><span data-stu-id="c4366-405">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="c4366-406">Você verá seis slots vazios.</span><span class="sxs-lookup"><span data-stu-id="c4366-406">You will see 6 empty slots.</span></span>
* <span data-ttu-id="c4366-407">No painel **hierarquia** , arraste cada um dos pré-fabricados pais sob os **pincéis** gameobject nesses slots em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="c4366-407">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="c4366-408">(Certifique-se de que você está arrastando o pré-fabricados da cena, não o pré-fabricados na pasta do projeto.)</span><span class="sxs-lookup"><span data-stu-id="c4366-408">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Seletor de pincel](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="c4366-410">**BrushSelector pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="c4366-410">**BrushSelector prefab**</span></span>

<span data-ttu-id="c4366-411">Como o **BrushSelector** herda **AttachToController**, ele mostra opções de **redireção** e **elemento** no painel **Inspetor** .</span><span class="sxs-lookup"><span data-stu-id="c4366-411">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="c4366-412">Selecionamos **direita** e **apontando** para a pose para anexar ferramentas de pincel ao controlador à direita com direção de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="c4366-412">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="c4366-413">O **BrushSelector** usa dois utilitários:</span><span class="sxs-lookup"><span data-stu-id="c4366-413">The **BrushSelector** makes use of two utilities:</span></span>

* <span data-ttu-id="c4366-414">**Ellipse**: usada para gerar pontos no espaço ao longo de uma forma Ellipse.</span><span class="sxs-lookup"><span data-stu-id="c4366-414">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="c4366-415">**LineObjectCollection**: distribui objetos usando os pontos gerados por qualquer classe de linha (por exemplo, Ellipse).</span><span class="sxs-lookup"><span data-stu-id="c4366-415">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="c4366-416">Isso é o que usaremos para colocar nossos pincéis ao longo da forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="c4366-416">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="c4366-417">Quando combinados, esses utilitários podem ser usados para criar um menu radial.</span><span class="sxs-lookup"><span data-stu-id="c4366-417">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="c4366-418">**Script LineObjectCollection**</span><span class="sxs-lookup"><span data-stu-id="c4366-418">**LineObjectCollection script**</span></span>

<span data-ttu-id="c4366-419">**LineObjectCollection** tem controles para o tamanho, a posição e a rotação de objetos distribuídos ao longo de sua linha.</span><span class="sxs-lookup"><span data-stu-id="c4366-419">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="c4366-420">Isso é útil para criar menus radiais como o seletor de pincel.</span><span class="sxs-lookup"><span data-stu-id="c4366-420">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="c4366-421">Para criar a aparência de pincéis que se expandem de nada à medida que eles se aproximam da posição selecionada central, os picos de curva de **objectscale** no centro e nas fitas são desativados nas bordas.</span><span class="sxs-lookup"><span data-stu-id="c4366-421">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="c4366-422">**Script BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="c4366-422">**BrushSelector script**</span></span>

<span data-ttu-id="c4366-423">No caso do **BrushSelector**, optamos por usar a animação de procedimento.</span><span class="sxs-lookup"><span data-stu-id="c4366-423">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="c4366-424">Primeiro, os modelos de pincel são distribuídos em uma elipse pelo script **LineObjectCollection** .</span><span class="sxs-lookup"><span data-stu-id="c4366-424">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="c4366-425">Em seguida, cada pincel é responsável por manter sua posição na mão do usuário com base em seu valor de **DisplayMode** , que é alterado com base na seleção.</span><span class="sxs-lookup"><span data-stu-id="c4366-425">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="c4366-426">Escolhemos uma abordagem de procedimento devido à alta probabilidade de transições de posição de pincel serem interrompidas à medida que o usuário seleciona pincéis.</span><span class="sxs-lookup"><span data-stu-id="c4366-426">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="c4366-427">As animações Mecanim podem lidar com as interrupções normalmente, mas tendem a ser mais complicadas do que uma operação simples de Lerp.</span><span class="sxs-lookup"><span data-stu-id="c4366-427">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="c4366-428">**BrushSelector** usa uma combinação de ambos.</span><span class="sxs-lookup"><span data-stu-id="c4366-428">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="c4366-429">Quando a entrada do Touchpad é detectada, as opções de pincel tornam-se visíveis e escaladas para cima ao longo do menu radial.</span><span class="sxs-lookup"><span data-stu-id="c4366-429">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="c4366-430">Após um período de tempo limite (que indica que o usuário fez uma seleção), as opções de pincel são reduzidas novamente, deixando apenas o pincel selecionado.</span><span class="sxs-lookup"><span data-stu-id="c4366-430">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="c4366-431">**Visualizando entrada do Touchpad**</span><span class="sxs-lookup"><span data-stu-id="c4366-431">**Visualizing touchpad input**</span></span>

<span data-ttu-id="c4366-432">Mesmo nos casos em que o modelo do controlador foi completamente substituído, pode ser útil mostrar a entrada nas entradas do modelo original.</span><span class="sxs-lookup"><span data-stu-id="c4366-432">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="c4366-433">Isso ajuda a aterrar as ações do usuário na realidade.</span><span class="sxs-lookup"><span data-stu-id="c4366-433">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="c4366-434">Para o **BrushSelector** , escolhemos tornar o touchpad visível brevemente quando a entrada é recebida.</span><span class="sxs-lookup"><span data-stu-id="c4366-434">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="c4366-435">Isso foi feito recuperando o elemento Touchpad do controlador, substituindo seu material por um material personalizado e aplicando um gradiente à cor desse material com base na última vez que a entrada do Touchpad foi recebida.</span><span class="sxs-lookup"><span data-stu-id="c4366-435">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="c4366-436">**Seleção da ferramenta pincel com entrada do Touchpad**</span><span class="sxs-lookup"><span data-stu-id="c4366-436">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="c4366-437">Quando o seletor de pincel detecta a entrada pressionada do Touchpad, ele verifica a posição da entrada para determinar se ela foi à esquerda ou à direita.</span><span class="sxs-lookup"><span data-stu-id="c4366-437">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="c4366-438">**Espessura do traço com selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="c4366-438">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="c4366-439">Em vez do evento **InteractionSourcePressType. Select** no **InteractionSourcePressed ()** , você pode obter o valor analógico do valor pressionado por meio de **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="c4366-439">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="c4366-440">Esse valor pode ser recuperado em **InteractionSourceUpdated ()** .</span><span class="sxs-lookup"><span data-stu-id="c4366-440">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="c4366-441">**Script de borracha**</span><span class="sxs-lookup"><span data-stu-id="c4366-441">**Eraser script**</span></span>

<span data-ttu-id="c4366-442">**Borracha** é um tipo especial de pincel que substitui a função **DrawOverTime ()** do **pincel**de base.</span><span class="sxs-lookup"><span data-stu-id="c4366-442">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="c4366-443">Embora Draw seja true, o apagador verifica se a sua gorjeta está interseccionada com qualquer traçado de pincel existente.</span><span class="sxs-lookup"><span data-stu-id="c4366-443">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="c4366-444">Em caso afirmativo, eles são adicionados a uma fila para serem reduzidos e excluídos.</span><span class="sxs-lookup"><span data-stu-id="c4366-444">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="c4366-445">Design avançado – portabilidade e Locomotion</span><span class="sxs-lookup"><span data-stu-id="c4366-445">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="c4366-446">Se você quiser permitir que o usuário se mova pela cena com a Teleportation usando Thumbstick, use **MixedRealityCameraParent** em vez de **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="c4366-446">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="c4366-447">Você também precisa adicionar **InputManager** e **DefaultCusor**.</span><span class="sxs-lookup"><span data-stu-id="c4366-447">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="c4366-448">Como **o MixedRealityCameraParent** já inclui **MotionControllers** e **limite** como componentes filho, você deve remover o **MotionControllers** existente e o **ambiente** pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="c4366-448">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="c4366-449">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4366-449">Instructions</span></span>

* <span data-ttu-id="c4366-450">No painel **hierarquia** , exclua **MixedRealityCamera**, **Environment** e **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="c4366-450">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="c4366-451">No **painel Projeto**, pesquise e arraste o seguinte pré-fabricados para o painel **hierarquia** :</span><span class="sxs-lookup"><span data-stu-id="c4366-451">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="c4366-452">Assets/AppPrefabs/Input/pré-fabricados/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="c4366-452">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="c4366-453">Assets/AppPrefabs/Input/pré-fabricados/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="c4366-453">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="c4366-454">Ativos/AppPrefabs/entrada/pré-fabricados/cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="c4366-454">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

    ![Pai da câmera de realidade misturada](images/mr213-cameraparent-300px.png)

* <span data-ttu-id="c4366-456">No painel **hierarquia** , clique em **Gerenciador de entrada**</span><span class="sxs-lookup"><span data-stu-id="c4366-456">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="c4366-457">No painel **Inspetor** , role para baixo até a seção **simples do seletor de ponteiro único**</span><span class="sxs-lookup"><span data-stu-id="c4366-457">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="c4366-458">No painel **hierarquia** , arraste **DefaultCursor** para o campo **cursor**</span><span class="sxs-lookup"><span data-stu-id="c4366-458">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

    ![Atribuindo DefaultCursor](images/mr213-defaultcursor-500px.png)

* <span data-ttu-id="c4366-460">**Salve** a cena e clique no botão **reproduzir** .</span><span class="sxs-lookup"><span data-stu-id="c4366-460">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="c4366-461">Você poderá usar o Thumbstick para girar para a esquerda/direita ou teleport.</span><span class="sxs-lookup"><span data-stu-id="c4366-461">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="c4366-462">Fim</span><span class="sxs-lookup"><span data-stu-id="c4366-462">The end</span></span>

<span data-ttu-id="c4366-463">E esse é o fim deste tutorial!</span><span class="sxs-lookup"><span data-stu-id="c4366-463">And that's the end of this tutorial!</span></span> <span data-ttu-id="c4366-464">Você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="c4366-464">You learned:</span></span>

* <span data-ttu-id="c4366-465">Como trabalhar com modelos de controlador de movimento no modo de jogo e no tempo de execução do Unity.</span><span class="sxs-lookup"><span data-stu-id="c4366-465">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="c4366-466">Como usar diferentes tipos de eventos de botão e seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c4366-466">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="c4366-467">Como sobrepor elementos de interface do usuário na parte superior do controlador ou personalizá-lo totalmente.</span><span class="sxs-lookup"><span data-stu-id="c4366-467">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="c4366-468">Agora você está pronto para começar a criar sua própria experiência de imersão com os controladores de movimento!</span><span class="sxs-lookup"><span data-stu-id="c4366-468">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="c4366-469">Cenas concluídas</span><span class="sxs-lookup"><span data-stu-id="c4366-469">Completed scenes</span></span>

* <span data-ttu-id="c4366-470">No painel de **projeto** do Unity, clique na pasta **cenas** .</span><span class="sxs-lookup"><span data-stu-id="c4366-470">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="c4366-471">Você encontrará dois Unity sceens **MixedReality213** e **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="c4366-471">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="c4366-472">**MixedReality213**: cena concluída com pincel único</span><span class="sxs-lookup"><span data-stu-id="c4366-472">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="c4366-473">**MixedReality213Advanced**: cena concluída com vários Brushes com o exemplo de valor de pressionar do botão Selecionar</span><span class="sxs-lookup"><span data-stu-id="c4366-473">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="c4366-474">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4366-474">See also</span></span>

* [<span data-ttu-id="c4366-475">Arquivos de projeto 213 de entrada do MR</span><span class="sxs-lookup"><span data-stu-id="c4366-475">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="c4366-476">Kit de ferramentas de realidade misturada – cena de teste do controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="c4366-476">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="c4366-477">Kit de ferramentas de realidade misturada-capturar mecânica</span><span class="sxs-lookup"><span data-stu-id="c4366-477">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="c4366-478">Diretrizes de desenvolvimento do controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="c4366-478">Motion controller development guidelines</span></span>](motion-controllers.md)

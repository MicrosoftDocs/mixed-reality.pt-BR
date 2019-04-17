---
title: Entrada MR 213
description: Siga este tutorial de codificação usando o Unity, o Visual Studio e fones imersivos em exposição para saber os detalhes dos controladores de movimento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, imersivo, controlador, academy, tutorial de movimento
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590940"
---
>[!NOTE]
><span data-ttu-id="464b3-104">Os tutoriais da academia de realidade mista foram criados com o HoloLens (1º gen) e misto realidade fones Imersivos em exposição em mente.</span><span class="sxs-lookup"><span data-stu-id="464b3-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="464b3-105">Como tal, achamos que é importante deixar esses tutoriais em vigor para os desenvolvedores que ainda estiver procurando por orientação no desenvolvimento para esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="464b3-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="464b3-106">Esses tutoriais serão **_não_** ser atualizados com os conjuntos de ferramentas ou interações que está sendo usadas para o HoloLens 2 a mais recente.</span><span class="sxs-lookup"><span data-stu-id="464b3-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="464b3-107">Eles serão mantidos para continuar trabalhando nos dispositivos com suporte.</span><span class="sxs-lookup"><span data-stu-id="464b3-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="464b3-108">Haverá uma nova série de tutoriais que serão lançados no futuro e que demonstra como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="464b3-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="464b3-109">Este aviso será atualizado com um link para esses tutoriais quando são lançadas.</span><span class="sxs-lookup"><span data-stu-id="464b3-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="464b3-110">Entrada MR 213: Controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="464b3-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="464b3-111">Controladores de movimento do mundo de realidade misturada adicionam outro nível de interatividade.</span><span class="sxs-lookup"><span data-stu-id="464b3-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="464b3-112">Com o [controladores de movimento](motion-controllers.md), podemos diretamente interagir com objetos de forma mais natural, semelhante às nossas interações físicas na vida real, aumentando a imersão e gostar de sua experiência de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="464b3-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="464b3-113">MR 213 de entrada, vamos explorar eventos de entrada do controlador de movimento, criando uma experiência de pintura espacial simples.</span><span class="sxs-lookup"><span data-stu-id="464b3-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="464b3-114">Com este aplicativo, os usuários podem pintar no espaço tridimensional com diversos tipos de pincéis e cores.</span><span class="sxs-lookup"><span data-stu-id="464b3-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="464b3-115">Tópicos abordados neste tutorial</span><span class="sxs-lookup"><span data-stu-id="464b3-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="464b3-119">**Visualização do controlador**</span><span class="sxs-lookup"><span data-stu-id="464b3-119">**Controller visualization**</span></span>|<span data-ttu-id="464b3-120">**Eventos de entrada do controlador**</span><span class="sxs-lookup"><span data-stu-id="464b3-120">**Controller input events**</span></span>|<span data-ttu-id="464b3-121">**Controlador personalizado e a interface do usuário**</span><span class="sxs-lookup"><span data-stu-id="464b3-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="464b3-122">Saiba como processar modelos de controlador de animação no modo de jogo do Unity e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="464b3-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="464b3-123">Entenda os diferentes tipos de eventos do botão e seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="464b3-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="464b3-124">Aprenda a sobreposição de elementos de interface do usuário sobre o controlador ou totalmente personalizá-lo.</span><span class="sxs-lookup"><span data-stu-id="464b3-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="464b3-125">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="464b3-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="464b3-126">Curso</span><span class="sxs-lookup"><span data-stu-id="464b3-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="464b3-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="464b3-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="464b3-128"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="464b3-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="464b3-129">Entrada MR 213: Controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="464b3-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="464b3-130">✔️</span><span class="sxs-lookup"><span data-stu-id="464b3-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="464b3-131">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="464b3-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="464b3-132">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="464b3-132">Prerequisites</span></span>

<span data-ttu-id="464b3-133">Consulte a lista de verificação de instalação para fones imersivos em exposição no [nesta página](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="464b3-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="464b3-134">Este tutorial requer [2017.2.1p2 do Unity](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="464b3-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="464b3-135">Arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="464b3-135">Project files</span></span>

* <span data-ttu-id="464b3-136">[Baixar os arquivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) exigidos pelo projeto e extraia os arquivos na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="464b3-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="464b3-137">Se você quiser examinar o código-fonte antes de baixar, ele tem [disponível no GitHub](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="464b3-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="464b3-138">Instalação do Unity</span><span class="sxs-lookup"><span data-stu-id="464b3-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="464b3-139">Objetivos</span><span class="sxs-lookup"><span data-stu-id="464b3-139">Objectives</span></span>

* <span data-ttu-id="464b3-140">Otimizar o desenvolvimento do Unity para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="464b3-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="464b3-141">Câmera de realidade misturada da instalação</span><span class="sxs-lookup"><span data-stu-id="464b3-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="464b3-142">Ambiente de configuração</span><span class="sxs-lookup"><span data-stu-id="464b3-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="464b3-143">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-143">Instructions</span></span>

* <span data-ttu-id="464b3-144">Inicie o Unity.</span><span class="sxs-lookup"><span data-stu-id="464b3-144">Start Unity.</span></span>
* <span data-ttu-id="464b3-145">Selecione **aberto**.</span><span class="sxs-lookup"><span data-stu-id="464b3-145">Select **Open**.</span></span>
* <span data-ttu-id="464b3-146">Navegue até a área de trabalho e localizar o **MixedReality213 mestre** pasta você anteriormente não arquivados.</span><span class="sxs-lookup"><span data-stu-id="464b3-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="464b3-147">Clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="464b3-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="464b3-148">Depois que o Unity termina de carregar arquivos de projeto, você poderá ver o editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="464b3-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="464b3-149">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="464b3-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="464b3-151">Selecione **plataforma Universal do Windows** na **plataforma** lista e clique no **alternar plataforma** botão.</span><span class="sxs-lookup"><span data-stu-id="464b3-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="464b3-152">Defina o dispositivo de destino **qualquer dispositivo**</span><span class="sxs-lookup"><span data-stu-id="464b3-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="464b3-153">Defina o tipo de compilação como **D3D**</span><span class="sxs-lookup"><span data-stu-id="464b3-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="464b3-154">Defina o SDK **mais recente instalada**</span><span class="sxs-lookup"><span data-stu-id="464b3-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="464b3-155">Verifique **Unity C# projetos**</span><span class="sxs-lookup"><span data-stu-id="464b3-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="464b3-156">Isso permite que você modifique os arquivos de script no projeto do Visual Studio sem recompilar o projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="464b3-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="464b3-157">Clique em **configurações do Player**.</span><span class="sxs-lookup"><span data-stu-id="464b3-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="464b3-158">No **Inspetor** painel, role para baixo até a parte inferior</span><span class="sxs-lookup"><span data-stu-id="464b3-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="464b3-159">Nas configurações de XR verificar **suporte de realidade Virtual**</span><span class="sxs-lookup"><span data-stu-id="464b3-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="464b3-160">Em SDKs de realidade Virtual, selecione **realidade mista do Windows**</span><span class="sxs-lookup"><span data-stu-id="464b3-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="464b3-162">Fechar **configurações de Build** janela.</span><span class="sxs-lookup"><span data-stu-id="464b3-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="464b3-163">Estrutura do projeto</span><span class="sxs-lookup"><span data-stu-id="464b3-163">Project structure</span></span>

<span data-ttu-id="464b3-164">Este tutorial usa  **[Toolkit de realidade misturada - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span><span class="sxs-lookup"><span data-stu-id="464b3-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="464b3-165">Você pode encontrar as versões na [nesta página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="464b3-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="464b3-167">**Concluído nos bastidores para sua referência**</span><span class="sxs-lookup"><span data-stu-id="464b3-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="464b3-168">Você encontrará duas cenas concluídas do Unity sob **cenas** pasta.</span><span class="sxs-lookup"><span data-stu-id="464b3-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="464b3-169">**MixedReality213**: Cena concluída com pincel único</span><span class="sxs-lookup"><span data-stu-id="464b3-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="464b3-170">**MixedReality213Advanced**: Concluída a cena para design avançado com vários pincéis</span><span class="sxs-lookup"><span data-stu-id="464b3-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="464b3-171">**Nova configuração de cena para o tutorial**</span><span class="sxs-lookup"><span data-stu-id="464b3-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="464b3-172">No Unity, clique em **arquivo > Nova cena**</span><span class="sxs-lookup"><span data-stu-id="464b3-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="464b3-173">Exclua **câmera principal** e **luz direcional**</span><span class="sxs-lookup"><span data-stu-id="464b3-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="464b3-174">Do **painel projeto**, a pesquisa e arraste os seguintes pré-fabricados para o **hierarquia** painel:</span><span class="sxs-lookup"><span data-stu-id="464b3-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="464b3-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="464b3-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="464b3-176">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="464b3-176">Assets/AppPrefabs/**Environment**</span></span>

![Câmera e ambiente](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="464b3-178">Há dois pré-fabricados câmera no Kit de ferramentas de realidade mista:</span><span class="sxs-lookup"><span data-stu-id="464b3-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="464b3-179">**MixedRealityCamera.prefab**: Somente a câmera</span><span class="sxs-lookup"><span data-stu-id="464b3-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="464b3-180">**MixedRealityCameraParent.prefab**: Câmera + Teleportation + limites</span><span class="sxs-lookup"><span data-stu-id="464b3-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="464b3-181">Neste tutorial, usaremos **MixedRealityCamera** sem teleportation recurso.</span><span class="sxs-lookup"><span data-stu-id="464b3-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="464b3-182">Por isso, adicionamos simples **ambiente** pré-fabricado que contém um piso básico para fazer com que o usuário sentir com aterramento.</span><span class="sxs-lookup"><span data-stu-id="464b3-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="464b3-183">Para saber mais sobre o teleportation com **MixedRealityCameraParent**, consulte [avançadas de design - Teleportation e locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="464b3-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="464b3-184">**Instalação de skybox**</span><span class="sxs-lookup"><span data-stu-id="464b3-184">**Skybox setup**</span></span>
* <span data-ttu-id="464b3-185">Clique em **Janela > iluminação > configurações**</span><span class="sxs-lookup"><span data-stu-id="464b3-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="464b3-186">Clique no círculo no lado direito do **campo Skybox Material**</span><span class="sxs-lookup"><span data-stu-id="464b3-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="464b3-187">Digite 'cinza' e selecione **SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="464b3-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="464b3-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="464b3-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Definindo skybox](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="464b3-190">Verifique **Skybox** permite que você poderá ver atribuído skybox gradação de cinza</span><span class="sxs-lookup"><span data-stu-id="464b3-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Ativar/desativar opção de skybox](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="464b3-192">A cena com MixedRealityCamera, ambiente e cinza skybox terá esta aparência.</span><span class="sxs-lookup"><span data-stu-id="464b3-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![Ambiente MixedReality213](images/mr213-environment-600px.jpg)
* <span data-ttu-id="464b3-194">Clique em **arquivo > Salvar cena como**</span><span class="sxs-lookup"><span data-stu-id="464b3-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="464b3-195">**Salvar** sua cena na pasta de cenas com qualquer nome</span><span class="sxs-lookup"><span data-stu-id="464b3-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="464b3-196">Capítulo 1 - visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="464b3-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="464b3-197">Objetivos</span><span class="sxs-lookup"><span data-stu-id="464b3-197">Objectives</span></span>

* <span data-ttu-id="464b3-198">Saiba como processar modelos de controlador no modo de jogo do Unity e em tempo de execução de movimento.</span><span class="sxs-lookup"><span data-stu-id="464b3-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="464b3-199">Realidade mista do Windows fornece um modelo de controlador animado para visualização do controlador.</span><span class="sxs-lookup"><span data-stu-id="464b3-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="464b3-200">Há várias abordagens que você pode adotar para visualização do controlador em seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="464b3-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="464b3-201">Padrão - usando o controlador padrão sem modificação</span><span class="sxs-lookup"><span data-stu-id="464b3-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="464b3-202">Hybrid - usando padrão de controlador, mas personalizando alguns de seus elementos ou sobreposição de componentes de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="464b3-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="464b3-203">Substituição - usando seu próprio personalizado a modelo 3D para o controlador</span><span class="sxs-lookup"><span data-stu-id="464b3-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="464b3-204">Neste capítulo, podemos aprenderá sobre os exemplos dessas personalizações de controlador.</span><span class="sxs-lookup"><span data-stu-id="464b3-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="464b3-205">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-205">Instructions</span></span>

* <span data-ttu-id="464b3-206">No **Project** do painel, digite **MotionControllers** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="464b3-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="464b3-207">Você também pode encontrá-la em ativos/HoloToolkit/entrada/pré-fabricados /.</span><span class="sxs-lookup"><span data-stu-id="464b3-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="464b3-208">Arraste o **MotionControllers** pré-fabricado para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-209">Clique no **MotionControllers** pré-fabricado na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="464b3-210">**MotionControllers pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="464b3-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="464b3-211">**MotionControllers** pré-fabricado tem uma **MotionControllerVisualizer** script que fornece os slots para modelos de controlador alternativo.</span><span class="sxs-lookup"><span data-stu-id="464b3-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="464b3-212">Se você atribuir seus próprios modelos personalizados 3D como uma mão ou uma gumes e marque 'Sempre usar alternativo esquerda/direita Model', você verá em vez do modelo padrão.</span><span class="sxs-lookup"><span data-stu-id="464b3-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="464b3-213">Usaremos esse slot no capítulo 4 para substituir o modelo de controlador com um pincel.</span><span class="sxs-lookup"><span data-stu-id="464b3-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="464b3-215">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="464b3-215">**Instructions**</span></span>
* <span data-ttu-id="464b3-216">No **Inspector** do painel, clique duas vezes **MotionControllerVisualizer** script para ver o código no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="464b3-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="464b3-217">**Script MotionControllerVisualizer**</span><span class="sxs-lookup"><span data-stu-id="464b3-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="464b3-218">O **MotionControllerVisualizer** e **MotionControllerInfo** classes fornecem os meios para acessar e modificar os modelos de controlador padrão.</span><span class="sxs-lookup"><span data-stu-id="464b3-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="464b3-219">**MotionControllerVisualizer** assina do Unity **InteractionSourceDetected** eventos e automaticamente cria uma instância de modelos de controlador quando eles forem encontrados.</span><span class="sxs-lookup"><span data-stu-id="464b3-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="464b3-220">Os modelos de controlador são entregues de acordo com a [a especificação de glTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="464b3-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="464b3-221">Esse formato foi criado para fornecer um formato comum, melhorando o processo por trás de transmissão e desempacotar os ativos 3D.</span><span class="sxs-lookup"><span data-stu-id="464b3-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="464b3-222">Nesse caso, é necessário recuperar e carregar os modelos de controlador no tempo de execução, pois queremos fazer o experiência do usuário mais simples possível, e não tem garantia de qual versão dos controladores de movimento que o usuário pode estar usando.</span><span class="sxs-lookup"><span data-stu-id="464b3-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="464b3-223">Neste curso, via o Kit de ferramentas de realidade misturada, usa uma versão do grupo de Khronos [UnityGLTF projeto](https://github.com/KhronosGroup/UnityGLTF).</span><span class="sxs-lookup"><span data-stu-id="464b3-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="464b3-224">Depois que o controlador foi entregue, os scripts podem usar **MotionControllerInfo** para localizar as transformações para elementos do controlador específico para que eles posicionam corretamente por conta própria.</span><span class="sxs-lookup"><span data-stu-id="464b3-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="464b3-225">Um capítulo posterior, aprenderemos a usar esses scripts para anexar os elementos de interface do usuário para os controladores.</span><span class="sxs-lookup"><span data-stu-id="464b3-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="464b3-226">*Em alguns scripts, você encontrará blocos de código com **#if! UNITY_EDITOR** ou **UNITY_WSA**. Esses blocos de código executadas somente em tempo de execução do UWP quando você implanta no Windows. Isso ocorre porque o conjunto de APIs usados pelo editor do Unity e o tempo de execução do aplicativo UWP são diferentes.*</span><span class="sxs-lookup"><span data-stu-id="464b3-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="464b3-227">**Salve** a cena e clique em de **reproduzir** botão.</span><span class="sxs-lookup"><span data-stu-id="464b3-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="464b3-228">Você será capaz de ver a cena com controladores de movimento em fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="464b3-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="464b3-229">Você pode ver as animações detalhadas para cliques de botão direcional movimentação e touchpad realce de toque.</span><span class="sxs-lookup"><span data-stu-id="464b3-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller visualização padrão](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="464b3-231">Capítulo 2 – anexar elementos de interface do usuário para o controlador</span><span class="sxs-lookup"><span data-stu-id="464b3-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="464b3-232">Objetivos</span><span class="sxs-lookup"><span data-stu-id="464b3-232">Objectives</span></span>

* <span data-ttu-id="464b3-233">Saiba mais sobre os elementos dos controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="464b3-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="464b3-234">Saiba como anexar objetos para partes específicas de controladores</span><span class="sxs-lookup"><span data-stu-id="464b3-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="464b3-235">Neste capítulo, você aprenderá como adicionar elementos da interface do usuário para o controlador que o usuário pode facilmente acessar e manipular a qualquer momento no.</span><span class="sxs-lookup"><span data-stu-id="464b3-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="464b3-236">Você também aprenderá como adicionar um selecionador de cores simples da interface do usuário usando o touchpad de entrada.</span><span class="sxs-lookup"><span data-stu-id="464b3-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="464b3-237">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-237">Instructions</span></span>

* <span data-ttu-id="464b3-238">No **Project** do painel, pesquise **MotionControllerInfo** script.</span><span class="sxs-lookup"><span data-stu-id="464b3-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="464b3-239">Os resultados de pesquisa, clique duas vezes **MotionControllerInfo** script para ver o código no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="464b3-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="464b3-240">**Script MotionControllerInfo**</span><span class="sxs-lookup"><span data-stu-id="464b3-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="464b3-241">A primeira etapa é escolher qual elemento do controlador que você deseja anexar a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="464b3-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="464b3-242">Esses elementos são definidos no **ControllerElementEnum** na **MotionControllerInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="464b3-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="464b3-244">**Casa**</span><span class="sxs-lookup"><span data-stu-id="464b3-244">**Home**</span></span>
* <span data-ttu-id="464b3-245">**Menu**</span><span class="sxs-lookup"><span data-stu-id="464b3-245">**Menu**</span></span>
* <span data-ttu-id="464b3-246">**Grasp**</span><span class="sxs-lookup"><span data-stu-id="464b3-246">**Grasp**</span></span>
* <span data-ttu-id="464b3-247">**Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="464b3-247">**Thumbstick**</span></span>
* <span data-ttu-id="464b3-248">**Select**</span><span class="sxs-lookup"><span data-stu-id="464b3-248">**Select**</span></span>
* <span data-ttu-id="464b3-249">**Touchpad**</span><span class="sxs-lookup"><span data-stu-id="464b3-249">**Touchpad**</span></span>
* <span data-ttu-id="464b3-250">**Apontador pose** – este elemento representa a dica do controlador que aponta para a direção de avanço.</span><span class="sxs-lookup"><span data-stu-id="464b3-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="464b3-251">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="464b3-251">**Instructions**</span></span>
* <span data-ttu-id="464b3-252">No **Project** do painel, pesquise **AttachToController** script.</span><span class="sxs-lookup"><span data-stu-id="464b3-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="464b3-253">Os resultados de pesquisa, clique duas vezes **AttachToController** script para ver o código no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="464b3-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="464b3-254">**Script AttachToController**</span><span class="sxs-lookup"><span data-stu-id="464b3-254">**AttachToController script**</span></span>

<span data-ttu-id="464b3-255">O **AttachToController** script fornece uma maneira simples de todos os objetos se conectar a um destro/canhoto do controlador especificado e o elemento.</span><span class="sxs-lookup"><span data-stu-id="464b3-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="464b3-256">In **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="464b3-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="464b3-257">Verificar o uso de destro/canhoto **MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="464b3-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="464b3-258">Obter o elemento específico de controlador usando **MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="464b3-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="464b3-259">Depois de recuperar o elemento transformar a partir do modelo de controlador, o objeto sob ele pai e defina a posição local e a rotação do objeto como zero.</span><span class="sxs-lookup"><span data-stu-id="464b3-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="464b3-260">A maneira mais simples de usar **AttachToController** script é herdar dele, assim como fizemos no caso de **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="464b3-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="464b3-261">Basta substituir a **OnAttachToController** e **OnDetatchFromController** funções para executar a instalação / divisão quando o controlador é detectado / desconectado.</span><span class="sxs-lookup"><span data-stu-id="464b3-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="464b3-262">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="464b3-262">**Instructions**</span></span>
* <span data-ttu-id="464b3-263">No **Project** do painel, digite na caixa de pesquisa **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="464b3-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="464b3-264">Você também pode encontrá-la em ativos/AppPrefabs /.</span><span class="sxs-lookup"><span data-stu-id="464b3-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="464b3-265">Arraste **ColorPickerWheel** pré-fabricado para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-266">Clique o **ColorPickerWheel** pré-fabricado na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-267">No **Inspector** do painel, clique duas vezes **ColorPickerWheel** Script para ver o código no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="464b3-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel pré-fabricado](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="464b3-269">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="464b3-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="464b3-270">Uma vez que **ColorPickerWheel** herda **AttachToController**, ele mostra **destro/canhoto** e **elemento** no  **Inspetor de** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="464b3-271">Podemos anexará a interface do usuário para o elemento Touchpad no controlador à esquerda.</span><span class="sxs-lookup"><span data-stu-id="464b3-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="464b3-273">**ColorPickerWheel** substitui o **OnAttachToController** e **OnDetatchFromController** para assinar o evento de entrada que será usado no próximo capítulo para seleção de cores com touchpad de entrada.</span><span class="sxs-lookup"><span data-stu-id="464b3-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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
* <span data-ttu-id="464b3-274">**Salve** a cena e clique em de **reproduzir** botão.</span><span class="sxs-lookup"><span data-stu-id="464b3-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="464b3-275">**Método alternativo para anexar objetos para os controladores**</span><span class="sxs-lookup"><span data-stu-id="464b3-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="464b3-276">Recomendamos que seus scripts herdam **AttachToController** e substituir **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="464b3-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="464b3-277">No entanto, isso talvez nem sempre seja possível.</span><span class="sxs-lookup"><span data-stu-id="464b3-277">However, this may not always be possible.</span></span> <span data-ttu-id="464b3-278">Uma alternativa é usá-lo como um componente autônomo.</span><span class="sxs-lookup"><span data-stu-id="464b3-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="464b3-279">Isso pode ser útil quando você deseja anexar um pré-fabricado existente a um controlador sem refatoração seus scripts.</span><span class="sxs-lookup"><span data-stu-id="464b3-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="464b3-280">Simplesmente faça a sua classe aguardar IsAttached ser definido como verdadeiro antes de executar qualquer programa de instalação.</span><span class="sxs-lookup"><span data-stu-id="464b3-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="464b3-281">A maneira mais simples de fazer isso é por meio de uma corrotina para 'Start'.</span><span class="sxs-lookup"><span data-stu-id="464b3-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="464b3-282">Capítulo 3 – trabalhando com entrada touchpad</span><span class="sxs-lookup"><span data-stu-id="464b3-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="464b3-283">Objetivos</span><span class="sxs-lookup"><span data-stu-id="464b3-283">Objectives</span></span>

* <span data-ttu-id="464b3-284">Saiba como obter eventos de dados de entrada touchpad</span><span class="sxs-lookup"><span data-stu-id="464b3-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="464b3-285">Saiba como usar informações de posição do eixo touchpad para a sua experiência de aplicativo</span><span class="sxs-lookup"><span data-stu-id="464b3-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="464b3-286">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-286">Instructions</span></span>

* <span data-ttu-id="464b3-287">No **hierarquia** do painel, clique em **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="464b3-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="464b3-288">No **Inspector** do painel, em **Animatior**, clique duas vezes em **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="464b3-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="464b3-289">Você será capaz de ver **Animator** guia aberta</span><span class="sxs-lookup"><span data-stu-id="464b3-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="464b3-290">**Mostrar/ocultar a interface de usuário com o controlador de animação do Unity**</span><span class="sxs-lookup"><span data-stu-id="464b3-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="464b3-291">Para mostrar e ocultar os **ColorPickerWheel** interface do usuário com a animação, estamos usando [sistema de animação do Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="464b3-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="464b3-292">Definindo o **ColorPickerWheel**do **Visible** propriedade como true ou falsos gatilhos **Mostrar** e **ocultar** disparadores de animação.</span><span class="sxs-lookup"><span data-stu-id="464b3-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="464b3-293">**Mostrar** e **ocultar** os parâmetros são definidos na **ColorPickerWheelController** controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="464b3-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Controlador de animação do Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="464b3-295">**Instruções**</span><span class="sxs-lookup"><span data-stu-id="464b3-295">**Instructions**</span></span>
* <span data-ttu-id="464b3-296">No **hierarquia** painel, selecione **ColorPickerWheel** pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="464b3-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="464b3-297">No **Inspector** do painel, clique duas vezes **ColorPickerWheel** script para ver o código no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="464b3-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="464b3-298">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="464b3-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="464b3-299">**ColorPickerWheel** assina do Unity **InteractionSourceUpdated** eventos para escutar eventos de teclado sensível ao toque.</span><span class="sxs-lookup"><span data-stu-id="464b3-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="464b3-300">Na **InteractionSourceUpdated()**, o script primeiro verifica para garantir que ele:</span><span class="sxs-lookup"><span data-stu-id="464b3-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="464b3-301">é, na verdade, um evento touchpad (obj.state. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="464b3-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="464b3-302">o controlador esquerdo se origina (obj.state.source. **destro/canhoto**)</span><span class="sxs-lookup"><span data-stu-id="464b3-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="464b3-303">Se ambos forem verdadeiros, o touchpad posicionar (obj.state. **touchpadPosition**) é atribuído a **selectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="464b3-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="464b3-304">Na **Update ()**, com base nas **visíveis** propriedade, ele dispara mostrar e ocultar gatilhos de animação no componente animator do seletor de cor</span><span class="sxs-lookup"><span data-stu-id="464b3-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="464b3-305">Na **Update ()**, **selectorPosition** é usado para converter um raio em colisor de malha da roda de cores, que retorna uma posição UV.</span><span class="sxs-lookup"><span data-stu-id="464b3-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="464b3-306">Nessa posição, em seguida, pode ser usada para localizar a coordenada de pixel e valor de textura do círculo de cores de cor.</span><span class="sxs-lookup"><span data-stu-id="464b3-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="464b3-307">Esse valor é acessível para outros scripts por meio de **SelectedColor** propriedade.</span><span class="sxs-lookup"><span data-stu-id="464b3-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Raycasting de roda de seletor de cor](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="464b3-309">Capítulo 4 - modelo do controlador de substituição</span><span class="sxs-lookup"><span data-stu-id="464b3-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="464b3-310">Objetivos</span><span class="sxs-lookup"><span data-stu-id="464b3-310">Objectives</span></span>

* <span data-ttu-id="464b3-311">Saiba como substituir o modelo de controlador com um modelo 3D personalizado.</span><span class="sxs-lookup"><span data-stu-id="464b3-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="464b3-313">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-313">Instructions</span></span>

* <span data-ttu-id="464b3-314">Clique em **MotionControllers** na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-315">Clique no círculo no lado direito do **controlador da direita alternativo** campo.</span><span class="sxs-lookup"><span data-stu-id="464b3-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="464b3-316">Digite **' BrushController**' e selecione pré-fabricado do resultado.</span><span class="sxs-lookup"><span data-stu-id="464b3-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="464b3-317">Você pode encontrá-la no ativos/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="464b3-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="464b3-318">Verificar **sempre usam o modelo certo alternativo**</span><span class="sxs-lookup"><span data-stu-id="464b3-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="464b3-320">O **BrushController** pré-fabricado não precisa ser incluído na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="464b3-321">No entanto, fazer check-out de seus componentes filho:</span><span class="sxs-lookup"><span data-stu-id="464b3-321">However, to check out its child components:</span></span>
* <span data-ttu-id="464b3-322">No **Project** do painel, digite **BrushController** e arraste **BrushController** pré-fabricado no **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="464b3-324">Você encontrará a **dica** componente **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="464b3-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="464b3-325">Nós usaremos sua transformação para iniciar/parar de desenhar linhas.</span><span class="sxs-lookup"><span data-stu-id="464b3-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="464b3-326">Excluir o **BrushController** da **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-327">**Salve** a cena e clique em de **reproduzir** botão.</span><span class="sxs-lookup"><span data-stu-id="464b3-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="464b3-328">Você será capaz de ver que o modelo do pincel substituído o controlador de movimento à direita.</span><span class="sxs-lookup"><span data-stu-id="464b3-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="464b3-329">Capítulo 5 - entrada de pintura com Select</span><span class="sxs-lookup"><span data-stu-id="464b3-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="464b3-330">Objetivos</span><span class="sxs-lookup"><span data-stu-id="464b3-330">Objectives</span></span>

* <span data-ttu-id="464b3-331">Saiba como usar o evento do botão de seleção para iniciar e parar um desenho de linha</span><span class="sxs-lookup"><span data-stu-id="464b3-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="464b3-332">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-332">Instructions</span></span>

* <span data-ttu-id="464b3-333">Pesquisa **BrushController** pré-fabricado na **projeto** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="464b3-334">No **Inspector** do painel, clique duas vezes **BrushController** Script para ver o código no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="464b3-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="464b3-335">**Script BrushController**</span><span class="sxs-lookup"><span data-stu-id="464b3-335">**BrushController script**</span></span>

<span data-ttu-id="464b3-336">**BrushController** assina o InteractionManager **InteractionSourcePressed** e **InteractionSourceReleased** eventos.</span><span class="sxs-lookup"><span data-stu-id="464b3-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="464b3-337">Quando **InteractionSourcePressed** evento é disparado, o pincel **desenhar** estiver definida como true; quando **InteractionSourceReleased** evento é disparado, o pincel **Desenhar** propriedade é definida como false.</span><span class="sxs-lookup"><span data-stu-id="464b3-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="464b3-338">Embora **desenhar** é definido como true, o pincel gerarão os pontos em uma Unity instanciada **LineRenderer**.</span><span class="sxs-lookup"><span data-stu-id="464b3-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="464b3-339">Uma referência a esse pré-fabricado é mantida no pincel **traço pré-fabricado** campo.</span><span class="sxs-lookup"><span data-stu-id="464b3-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="464b3-340">Para usar a cor atualmente selecionada do disco de seletor de cores da interface do usuário, **BrushController** precisa ter uma referência para o **ColorPickerWheel** objeto.</span><span class="sxs-lookup"><span data-stu-id="464b3-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="464b3-341">Porque o **BrushController** pré-fabricado é instanciado em tempo de execução como um controlador de substituição, todas as referências a objetos na cena precisará ser definida em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="464b3-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="464b3-342">Nesse caso, usamos **gameobject. Findobjectoftype** para localizar o **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="464b3-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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
* <span data-ttu-id="464b3-343">**Salve** a cena e clique em de **reproduzir** botão.</span><span class="sxs-lookup"><span data-stu-id="464b3-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="464b3-344">Você poderá desenhar as linhas e pintar usando o botão de seleção no controlador do lado direito.</span><span class="sxs-lookup"><span data-stu-id="464b3-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="464b3-345">Capítulo 6 - geração de objeto com Select de entrada</span><span class="sxs-lookup"><span data-stu-id="464b3-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="464b3-346">Objetivos</span><span class="sxs-lookup"><span data-stu-id="464b3-346">Objectives</span></span>

* <span data-ttu-id="464b3-347">Saiba como usar Select e compreender os eventos de entrada de botão</span><span class="sxs-lookup"><span data-stu-id="464b3-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="464b3-348">Saiba como criar uma instância de objetos</span><span class="sxs-lookup"><span data-stu-id="464b3-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="464b3-349">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-349">Instructions</span></span>

* <span data-ttu-id="464b3-350">No **Project** do painel, digite **ObjectSpawner** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="464b3-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="464b3-351">Você também pode encontrá-la em ativos/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="464b3-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="464b3-352">Arraste o **ObjectSpawner** pré-fabricado para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-353">Clique em **ObjectSpawner** na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-354">**ObjectSpawner** tem um campo nomeado **cor fonte**.</span><span class="sxs-lookup"><span data-stu-id="464b3-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="464b3-355">Dos **hierarquia** do painel, arraste o **ColorPickerWheel** referência neste campo.</span><span class="sxs-lookup"><span data-stu-id="464b3-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![Inspetor de Spawner de objetos](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="464b3-357">Clique o **ObjectSpawner** pré-fabricado na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-358">No **Inspector** do painel, clique duas vezes **ObjectSpawner** Script para ver o código no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="464b3-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="464b3-359">**Script ObjectSpawner**</span><span class="sxs-lookup"><span data-stu-id="464b3-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="464b3-360">O **ObjectSpawner** cria uma instância de cópias de uma malha primitiva (cubo, esfera, cilindro) para o espaço.</span><span class="sxs-lookup"><span data-stu-id="464b3-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="464b3-361">Quando um **InteractionSourcePressed** for detectado, ele verifica a direção e se é um **InteractionSourcePressType.Grasp** ou **InteractionSourcePressType.Select** evento.</span><span class="sxs-lookup"><span data-stu-id="464b3-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="464b3-362">Para um **segure** evento, ele incrementa o índice do tipo atual de malha (esfera, cubo, cilindro)</span><span class="sxs-lookup"><span data-stu-id="464b3-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="464b3-363">Para um **selecionar** evento, na **SpawnObject()**, um novo objeto é instanciado, não parented e liberados para o mundo.</span><span class="sxs-lookup"><span data-stu-id="464b3-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

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

<span data-ttu-id="464b3-364">O **ObjectSpawner** usa o **ColorPickerWheel** para definir a cor do material do objeto de exibição.</span><span class="sxs-lookup"><span data-stu-id="464b3-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="464b3-365">Objetos gerados recebem uma instância deste material para que ele manterá sua cor.</span><span class="sxs-lookup"><span data-stu-id="464b3-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="464b3-366">**Salve** a cena e clique em de **reproduzir** botão.</span><span class="sxs-lookup"><span data-stu-id="464b3-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="464b3-367">Você poderá alterar os objetos com o botão de compreensão e gerar objetos com o botão de seleção.</span><span class="sxs-lookup"><span data-stu-id="464b3-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="464b3-368">Criar e implantar o aplicativo no Portal de realidade mista</span><span class="sxs-lookup"><span data-stu-id="464b3-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="464b3-369">No Unity, selecione **arquivo > configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="464b3-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="464b3-370">Clique em **adicionar cenas aberto** para adicionar a cena atual para o **cenas em compilação**.</span><span class="sxs-lookup"><span data-stu-id="464b3-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="464b3-371">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="464b3-371">Click **Build**.</span></span>
* <span data-ttu-id="464b3-372">Criar uma **nova pasta** chamado "App".</span><span class="sxs-lookup"><span data-stu-id="464b3-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="464b3-373">Único clique a **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="464b3-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="464b3-374">Clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="464b3-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="464b3-375">Quando Unity é feito, será exibida uma janela do Explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="464b3-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="464b3-376">Abra o **aplicativo** pasta.</span><span class="sxs-lookup"><span data-stu-id="464b3-376">Open the **App** folder.</span></span>
* <span data-ttu-id="464b3-377">Clique duas vezes **YourSceneName.sln** arquivo de solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="464b3-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="464b3-378">Usando a barra de ferramentas superior do Visual Studio, alterar o destino de depuração para **Release** e do ARM para **X64**.</span><span class="sxs-lookup"><span data-stu-id="464b3-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="464b3-379">Clique na seta suspensa ao lado do botão de dispositivo e selecione **computador Local**.</span><span class="sxs-lookup"><span data-stu-id="464b3-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="464b3-380">Clique em **Depurar -> Iniciar sem depuração** na barra de menus ou pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="464b3-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="464b3-381">Agora o aplicativo é criado e instalado no Portal de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="464b3-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="464b3-382">Você pode iniciá-lo novamente por meio do menu Iniciar no Portal de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="464b3-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="464b3-383">Design avançado - ferramentas Pincel com layout radial</span><span class="sxs-lookup"><span data-stu-id="464b3-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 principal](images/mr213-main-600px.jpg)

<span data-ttu-id="464b3-385">Neste capítulo, você aprenderá como substituir o modelo de controlador de movimento padrão com um conjunto de ferramentas Pincel personalizado.</span><span class="sxs-lookup"><span data-stu-id="464b3-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="464b3-386">Para referência, você pode encontrar a cena concluída **MixedReality213Advanced** sob **cenas** pasta.</span><span class="sxs-lookup"><span data-stu-id="464b3-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="464b3-387">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-387">Instructions</span></span>

* <span data-ttu-id="464b3-388">No **Project** do painel, digite **BrushSelector** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="464b3-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="464b3-389">Você também pode encontrá-la em ativos/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="464b3-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="464b3-390">Arraste o **BrushSelector** pré-fabricado para o **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-391">Para a organização, criar um GameObject vazio chamado **pincéis**</span><span class="sxs-lookup"><span data-stu-id="464b3-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="464b3-392">Arraste as seguir pré-fabricados do **Project** do painel em **pincéis**</span><span class="sxs-lookup"><span data-stu-id="464b3-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="464b3-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="464b3-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="464b3-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="464b3-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="464b3-395">Assets/AppPrefabs/**Eraser**</span><span class="sxs-lookup"><span data-stu-id="464b3-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="464b3-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="464b3-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="464b3-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="464b3-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="464b3-398">Assets/AppPrefabs/**Pencil**</span><span class="sxs-lookup"><span data-stu-id="464b3-398">Assets/AppPrefabs/**Pencil**</span></span>

![Pincéis](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="464b3-400">Clique em **MotionControllers** pré-fabricado na **hierarquia** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="464b3-401">No **Inspector** do painel, desmarque a opção **sempre usar alternativas à direita o modelo de** no **Visualizador do controlador de movimento**</span><span class="sxs-lookup"><span data-stu-id="464b3-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="464b3-402">No **hierarquia** do painel, clique em **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="464b3-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="464b3-403">**BrushSelector** tem um campo chamado **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="464b3-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="464b3-404">Do **hierarquia** do painel, arraste o **ColorPickerWheel** em **ColorPicker** campo o **Inspetor** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![Atribuir ColorPickerWheel ao seletor de pincel](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="464b3-406">No **hierarquia** do painel, em **BrushSelector** pré-fabricado, selecione o **Menu** objeto.</span><span class="sxs-lookup"><span data-stu-id="464b3-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="464b3-407">No **Inspector** do painel, na **LineObjectCollection** componente, abra o **objetos** lista suspensa de matriz.</span><span class="sxs-lookup"><span data-stu-id="464b3-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="464b3-408">Você verá 6 slots vazios.</span><span class="sxs-lookup"><span data-stu-id="464b3-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="464b3-409">Dos **hierarquia** do painel, arraste cada um as pai em pré-fabricados a **pincéis** GameObject nestes slots em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="464b3-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="464b3-410">(Verifique se que você estiver arrastando os pré-fabricados da cena, não os pré-fabricados na pasta do projeto.)</span><span class="sxs-lookup"><span data-stu-id="464b3-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Seletor de pincel](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="464b3-412">**BrushSelector pré-fabricado**</span><span class="sxs-lookup"><span data-stu-id="464b3-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="464b3-413">Uma vez que o **BrushSelector** herda **AttachToController**, ele mostra **destro/canhoto** e **elemento** opções no  **Inspetor de** painel.</span><span class="sxs-lookup"><span data-stu-id="464b3-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="464b3-414">Selecionamos **direita** e **apontando para representar** anexar ferramentas de pincel para o controlador de mão direita com direção para frente.</span><span class="sxs-lookup"><span data-stu-id="464b3-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="464b3-415">O **BrushSelector** faz uso de dois utilitários:</span><span class="sxs-lookup"><span data-stu-id="464b3-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="464b3-416">**Elipse**: usado para gerar pontos no espaço ao longo de uma forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="464b3-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="464b3-417">**LineObjectCollection**: distribui objetos usando os pontos de gerados por qualquer classe de linha (por exemplo, a elipse).</span><span class="sxs-lookup"><span data-stu-id="464b3-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="464b3-418">Esse é o que usaremos para colocar nosso pincéis ao longo da forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="464b3-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="464b3-419">Quando combinados, esses utilitários podem ser usados para criar um menu radial.</span><span class="sxs-lookup"><span data-stu-id="464b3-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="464b3-420">**Script LineObjectCollection**</span><span class="sxs-lookup"><span data-stu-id="464b3-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="464b3-421">**LineObjectCollection** tem controles para o tamanho, posição e rotação de objetos distribuídos ao longo de sua linha.</span><span class="sxs-lookup"><span data-stu-id="464b3-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="464b3-422">Isso é útil para a criação de menus radiais como o seletor de pincel.</span><span class="sxs-lookup"><span data-stu-id="464b3-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="464b3-423">Para criar a aparência de pincéis que se ajustam-se de nada como eles abordam a posição do Centro de selecionado, o **ObjectScale** curva picos no centro e menos acentuada desativado nas bordas.</span><span class="sxs-lookup"><span data-stu-id="464b3-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="464b3-424">**Script BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="464b3-424">**BrushSelector script**</span></span>

<span data-ttu-id="464b3-425">No caso do **BrushSelector**, escolhemos usar animação procedural.</span><span class="sxs-lookup"><span data-stu-id="464b3-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="464b3-426">Primeiro, modelos de pincel são distribuídos em uma elipse, o **LineObjectCollection** script.</span><span class="sxs-lookup"><span data-stu-id="464b3-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="464b3-427">Em seguida, cada pincel é responsável por manter sua posição em mãos do usuário com base em seu **DisplayMode** valor, que as alterações com base na seleção.</span><span class="sxs-lookup"><span data-stu-id="464b3-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="464b3-428">Devido à alta probabilidade de transições de posição de pincel que está sendo interrompida conforme o usuário seleciona pincéis, escolhemos uma abordagem de procedimentos.</span><span class="sxs-lookup"><span data-stu-id="464b3-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="464b3-429">Animações Mecanim podem lidar com interrupções normalmente, mas ela costuma ser mais complicado do que uma operação de Lerp simples.</span><span class="sxs-lookup"><span data-stu-id="464b3-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="464b3-430">**BrushSelector** usa uma combinação de ambos.</span><span class="sxs-lookup"><span data-stu-id="464b3-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="464b3-431">Quando for detectada entrada touchpad, opções de pincel se tornam visíveis e escalar verticalmente ao longo do menu radial.</span><span class="sxs-lookup"><span data-stu-id="464b3-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="464b3-432">Após um período de tempo limite (o que indica que o usuário tiver feito uma seleção) o pincel de opções de dimensionamento para baixo novamente, deixando apenas o pincel selecionado.</span><span class="sxs-lookup"><span data-stu-id="464b3-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="464b3-433">**Visualizando touchpad entrada**</span><span class="sxs-lookup"><span data-stu-id="464b3-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="464b3-434">Mesmo nos casos em que o modelo do controlador foi substituído completamente, pode ser útil mostrar a entrada em entradas do modelo original.</span><span class="sxs-lookup"><span data-stu-id="464b3-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="464b3-435">Isso ajuda a Terra as ações do usuário, na realidade.</span><span class="sxs-lookup"><span data-stu-id="464b3-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="464b3-436">Para o **BrushSelector** que escolhemos para tornar o touchpad brevemente visíveis quando a entrada é recebida.</span><span class="sxs-lookup"><span data-stu-id="464b3-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="464b3-437">Isso foi feito, recuperando o elemento Touchpad do controlador, substituindo seu material com um material personalizado, em seguida, aplicar um gradiente para a cor do material que baseia o touchpad de tempo a última entrada foi recebida.</span><span class="sxs-lookup"><span data-stu-id="464b3-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="464b3-438">**Seleção de ferramenta pincel com a entrada do teclado sensível ao toque**</span><span class="sxs-lookup"><span data-stu-id="464b3-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="464b3-439">Quando o seletor de pincel detecta a entrada de pressionado do touchpad, ele verifica a posição da entrada para determinar se ele foi para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="464b3-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="464b3-440">**Espessura do traço com selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="464b3-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="464b3-441">Em vez do **InteractionSourcePressType.Select** evento na **InteractionSourcePressed()**, você pode obter o valor analógico do valor pressionado por meio de **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="464b3-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="464b3-442">Esse valor pode ser recuperado no **InteractionSourceUpdated()**.</span><span class="sxs-lookup"><span data-stu-id="464b3-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="464b3-443">**Script de borracha**</span><span class="sxs-lookup"><span data-stu-id="464b3-443">**Eraser script**</span></span>

<span data-ttu-id="464b3-444">**Borracha** é um tipo especial de pincel que substitui a base **pincel**do **DrawOverTime()** função.</span><span class="sxs-lookup"><span data-stu-id="464b3-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="464b3-445">Enquanto o desenho for true, a borracha verifica para ver se sua dica faz interseção com todos os traços do pincel existente.</span><span class="sxs-lookup"><span data-stu-id="464b3-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="464b3-446">Se isso acontecer, eles são adicionados a uma fila para ser reduzido para baixo e excluídos.</span><span class="sxs-lookup"><span data-stu-id="464b3-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="464b3-447">Design avançado - Teleportation e locomotion</span><span class="sxs-lookup"><span data-stu-id="464b3-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="464b3-448">Se você quiser permitir que o usuário move a cena com teleportation usando direcional, use **MixedRealityCameraParent** em vez de **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="464b3-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="464b3-449">Você também precisa adicionar **InputManager** e **DefaultCusor**.</span><span class="sxs-lookup"><span data-stu-id="464b3-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="464b3-450">Uma vez que **MixedRealityCameraParent** já inclui **MotionControllers** e **limite** como componentes filho, você deve remover existente  **MotionControllers** e **ambiente** pré-fabricado.</span><span class="sxs-lookup"><span data-stu-id="464b3-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="464b3-451">Instruções</span><span class="sxs-lookup"><span data-stu-id="464b3-451">Instructions</span></span>

* <span data-ttu-id="464b3-452">No **hierarquia** do painel, exclua **MixedRealityCamera**, **ambiente** e **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="464b3-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="464b3-453">Do **painel projeto**, a pesquisa e arraste os seguintes pré-fabricados para o **hierarquia** painel:</span><span class="sxs-lookup"><span data-stu-id="464b3-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="464b3-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="464b3-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="464b3-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="464b3-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="464b3-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="464b3-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Realidade misturada câmera pai](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="464b3-458">No **hierarquia** do painel, clique em **Input Manager**</span><span class="sxs-lookup"><span data-stu-id="464b3-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="464b3-459">No **Inspector** do painel, role para baixo até a **seletor único de ponteiro simples** seção</span><span class="sxs-lookup"><span data-stu-id="464b3-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="464b3-460">Dos **hierarquia** do painel, arraste **DefaultCursor** na **Cursor** campo</span><span class="sxs-lookup"><span data-stu-id="464b3-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![Atribuição de DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="464b3-462">**Salve** a cena e clique em de **reproduzir** botão.</span><span class="sxs-lookup"><span data-stu-id="464b3-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="464b3-463">Você poderá usar o analógico para girar esquerda/direita ou ser transportado.</span><span class="sxs-lookup"><span data-stu-id="464b3-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="464b3-464">Fim</span><span class="sxs-lookup"><span data-stu-id="464b3-464">The end</span></span>

<span data-ttu-id="464b3-465">E esse é o final deste tutorial!</span><span class="sxs-lookup"><span data-stu-id="464b3-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="464b3-466">Você aprendeu:</span><span class="sxs-lookup"><span data-stu-id="464b3-466">You learned:</span></span>
* <span data-ttu-id="464b3-467">Como trabalhar com modelos de controlador de movimento no modo de jogo do Unity e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="464b3-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="464b3-468">Como usar diferentes tipos de eventos do botão e seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="464b3-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="464b3-469">Como elementos de interface do usuário sobre o controlador de sobreposição ou totalmente personalizá-lo.</span><span class="sxs-lookup"><span data-stu-id="464b3-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="464b3-470">Agora você está pronto para começar a criar sua própria experiência de imersão com controladores de movimento!</span><span class="sxs-lookup"><span data-stu-id="464b3-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="464b3-471">Cenas concluídas</span><span class="sxs-lookup"><span data-stu-id="464b3-471">Completed scenes</span></span>

* <span data-ttu-id="464b3-472">Do Unity **projeto** no painel, clique o **cenas** pasta.</span><span class="sxs-lookup"><span data-stu-id="464b3-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="464b3-473">Você encontrará duas telas do Unity **MixedReality213** e **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="464b3-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="464b3-474">**MixedReality213**: Cena concluída com pincel único</span><span class="sxs-lookup"><span data-stu-id="464b3-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="464b3-475">**MixedReality213Advanced**: Concluído cena com vários pincel com exemplo de valor pressione do botão de seleção</span><span class="sxs-lookup"><span data-stu-id="464b3-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="464b3-476">Consulte também</span><span class="sxs-lookup"><span data-stu-id="464b3-476">See also</span></span>

* [<span data-ttu-id="464b3-477">Arquivos de projeto MR entrada 213</span><span class="sxs-lookup"><span data-stu-id="464b3-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="464b3-478">Toolkit de realidade misturada - cena de teste de movimento do controlador</span><span class="sxs-lookup"><span data-stu-id="464b3-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="464b3-479">Kit de ferramentas de realidade misturada - mecânica de captura</span><span class="sxs-lookup"><span data-stu-id="464b3-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="464b3-480">Diretrizes de desenvolvimento de controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="464b3-480">Motion controller development guidelines</span></span>](motion-controllers.md)

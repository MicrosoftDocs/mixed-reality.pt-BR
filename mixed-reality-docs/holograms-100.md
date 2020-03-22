---
title: Sr-noções básicas 100 – introdução ao Unity
description: Saiba como criar seu primeiro aplicativo "Hello World" básico de realidade misturada.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidade misturada, realidade do Windows Mixed, HoloLens, imersão, VR, Sr, introdução, holograma, Academia, tutorial
ms.openlocfilehash: fe0fb256e5aed7aa83f8bb9b1e8ba7bb873a0613
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082058"
---
>[!NOTE]
><span data-ttu-id="997d7-104">Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.</span><span class="sxs-lookup"><span data-stu-id="997d7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="997d7-105">Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="997d7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="997d7-106">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="997d7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="997d7-107">Eles serão mantidos para continuar funcionando nos dispositivos compatíveis.</span><span class="sxs-lookup"><span data-stu-id="997d7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="997d7-108">[Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="997d7-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="997d7-109">Sr noções básicas 100: introdução ao Unity</span><span class="sxs-lookup"><span data-stu-id="997d7-109">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="997d7-110">Este tutorial orientará você na criação de um aplicativo básico de realidade misturada criado com o Unity.</span><span class="sxs-lookup"><span data-stu-id="997d7-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="997d7-111">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="997d7-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="997d7-112">Curso</span><span class="sxs-lookup"><span data-stu-id="997d7-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="997d7-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="997d7-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="997d7-114"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="997d7-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="997d7-115">Sr noções básicas 100: introdução ao Unity</span><span class="sxs-lookup"><span data-stu-id="997d7-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="997d7-116">✔️</span><span class="sxs-lookup"><span data-stu-id="997d7-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="997d7-117">✔️</span><span class="sxs-lookup"><span data-stu-id="997d7-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="997d7-118">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="997d7-118">Prerequisites</span></span>

* <span data-ttu-id="997d7-119">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="997d7-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="997d7-120">Capítulo 1-criar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="997d7-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="997d7-121">Para criar um aplicativo com o Unity, primeiro você precisa criar um projeto.</span><span class="sxs-lookup"><span data-stu-id="997d7-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="997d7-122">Esse projeto é organizado em algumas pastas, o mais importante deles é sua pasta de ativos.</span><span class="sxs-lookup"><span data-stu-id="997d7-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="997d7-123">Essa é a pasta que contém todos os ativos que você importa das ferramentas de criação de conteúdo digital, como Maya, Max cinema 4D ou Photoshop, todo o código que você cria com o Visual Studio ou seu editor de código favorito e qualquer quantidade de arquivos de conteúdo que o Unity cria conforme as cenas de composição , animações e outros tipos de ativos de Unity no editor.</span><span class="sxs-lookup"><span data-stu-id="997d7-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="997d7-124">Para compilar e implantar aplicativos UWP, o Unity pode exportar o projeto como uma solução do Visual Studio que conterá todos os arquivos de ativos e de código necessários.</span><span class="sxs-lookup"><span data-stu-id="997d7-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="997d7-125">Iniciar o Unity</span><span class="sxs-lookup"><span data-stu-id="997d7-125">Start Unity</span></span>
2. <span data-ttu-id="997d7-126">Selecionar **novo**</span><span class="sxs-lookup"><span data-stu-id="997d7-126">Select **New**</span></span>
3. <span data-ttu-id="997d7-127">Insira um nome de projeto (por exemplo, "MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="997d7-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="997d7-128">Insira um local para salvar seu projeto</span><span class="sxs-lookup"><span data-stu-id="997d7-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="997d7-129">Verifique se a alternância **3D** está selecionada</span><span class="sxs-lookup"><span data-stu-id="997d7-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="997d7-130">Selecione **criar projeto**</span><span class="sxs-lookup"><span data-stu-id="997d7-130">Select **Create project**</span></span>

<span data-ttu-id="997d7-131">Parabéns, você está pronto para começar a usar suas personalizações de realidade misturada agora.</span><span class="sxs-lookup"><span data-stu-id="997d7-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="997d7-132">Capítulo 2 – configurar a câmera</span><span class="sxs-lookup"><span data-stu-id="997d7-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="997d7-133">A câmera principal do Unity lida com o controle de cabeçalho e a renderização de estereoscópico.</span><span class="sxs-lookup"><span data-stu-id="997d7-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="997d7-134">Há algumas alterações a serem feitas na câmera principal para usá-la com realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="997d7-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="997d7-135">Selecionar arquivo > nova cena</span><span class="sxs-lookup"><span data-stu-id="997d7-135">Select File > New Scene</span></span>

<span data-ttu-id="997d7-136">Primeiro, será mais fácil definir o layout de seu aplicativo se você imaginar a posição inicial do usuário como (**X**: 0, **Y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="997d7-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="997d7-137">Como a câmera principal está acompanhando a movimentação do cabeçalho do usuário, a posição inicial do usuário pode ser definida definindo a posição inicial da câmera principal.</span><span class="sxs-lookup"><span data-stu-id="997d7-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="997d7-138">Selecione a **câmera principal** no painel **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="997d7-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="997d7-139">No painel **Inspetor** , localize o componente **transformação** e altere a **posição** de (**x**: 0, **y**: 1, **z**:-10) para (**x**: 0, **y**: 0, **z**: 0)</span><span class="sxs-lookup"><span data-stu-id="997d7-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="997d7-140">Em segundo lugar, o plano de fundo da câmera padrão precisa de algum pensamento.</span><span class="sxs-lookup"><span data-stu-id="997d7-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="997d7-141">**Para aplicativos de HoloLens**, o mundo real deve aparecer atrás de tudo que a câmera renderiza, não uma textura Skybox.</span><span class="sxs-lookup"><span data-stu-id="997d7-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="997d7-142">Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e altere a lista suspensa **limpar sinalizadores** de **Skybox** para **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="997d7-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="997d7-143">Selecione o seletor de cor do **plano de fundo** e altere os valores de **RGBA** para (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="997d7-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="997d7-144">**Para aplicativos de realidade misturados direcionados a headsets de imersão**, podemos usar a textura padrão do Skybox que o Unity fornece.</span><span class="sxs-lookup"><span data-stu-id="997d7-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="997d7-145">Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e mantenha o menu suspenso **limpar sinalizadores** em **Skybox**.</span><span class="sxs-lookup"><span data-stu-id="997d7-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="997d7-146">Em terceiro lugar, vamos considerar o próximo clipe no Unity e impedir que os objetos sejam renderizados muito próximos dos olhos dos usuários, uma vez que um usuário se aproxima de um objeto ou um objeto se aproxima de um usuário.</span><span class="sxs-lookup"><span data-stu-id="997d7-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="997d7-147">**Para aplicativos do HoloLens**, o próximo clipe pode ser definido como o [hololens recomendado](camera-in-unity.md#clip-planes) 0,85 metros.</span><span class="sxs-lookup"><span data-stu-id="997d7-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="997d7-148">Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e altere o campo **próximo do plano do clipe** do padrão **0,3** para o HoloLens recomendado **0,85**.</span><span class="sxs-lookup"><span data-stu-id="997d7-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="997d7-149">**Para aplicativos de realidade misturados direcionados a headsets de imersão**, podemos usar a configuração padrão que o Unity fornece.</span><span class="sxs-lookup"><span data-stu-id="997d7-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="997d7-150">Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e mantenha o campo **próximo do plano do clipe** para o padrão **0,3**.</span><span class="sxs-lookup"><span data-stu-id="997d7-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="997d7-151">Por fim, vamos salvar nosso progresso até o momento.</span><span class="sxs-lookup"><span data-stu-id="997d7-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="997d7-152">Para salvar as alterações de cena, selecione **arquivo > salvar cena como**, nomeie a cena **principal**e selecione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="997d7-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="997d7-153">Capítulo 3-configurar as configurações do projeto</span><span class="sxs-lookup"><span data-stu-id="997d7-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="997d7-154">Neste capítulo, definiremos algumas configurações de projeto do Unity que nos ajudam a direcionar o SDK do Windows Holographic para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="997d7-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="997d7-155">Também definiremos algumas configurações de qualidade para nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="997d7-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="997d7-156">Por fim, garantiremos que nossos destinos de compilação estejam definidos como Windows Store.</span><span class="sxs-lookup"><span data-stu-id="997d7-156">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="997d7-157">Configurações de desempenho e qualidade do Unity</span><span class="sxs-lookup"><span data-stu-id="997d7-157">Unity performance and quality settings</span></span>

<span data-ttu-id="997d7-158">**Configurações de qualidade do Unity para o HoloLens**</span><span class="sxs-lookup"><span data-stu-id="997d7-158">**Unity quality settings for HoloLens**</span></span>

![Configurações de qualidade do Unity para o HoloLens](images/qualitysettings.png)

<span data-ttu-id="997d7-160">Como a manutenção da alta taxa de quadros no HoloLens é tão importante, queremos que as configurações de qualidade sejam ajustadas para um desempenho mais rápido.</span><span class="sxs-lookup"><span data-stu-id="997d7-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="997d7-161">Para obter informações de desempenho mais detalhadas, [recomendações de desempenho para o Unity](performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="997d7-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="997d7-162">Selecione **Editar configurações do projeto > > qualidade**</span><span class="sxs-lookup"><span data-stu-id="997d7-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="997d7-163">Selecione o **menu suspenso** sob o logotipo da **Windows Store** e selecione **muito baixo**.</span><span class="sxs-lookup"><span data-stu-id="997d7-163">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="997d7-164">Você saberá que a configuração é aplicada corretamente quando a caixa na coluna da Windows Store e a linha **muito baixa** estiverem verdes.</span><span class="sxs-lookup"><span data-stu-id="997d7-164">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="997d7-165">**Para aplicativos de realidade misturados direcionados a exibições do obstruído**, você pode deixar as configurações de qualidade com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="997d7-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="997d7-166">SDK do Windows 10 de destino</span><span class="sxs-lookup"><span data-stu-id="997d7-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="997d7-167">**SDK do Windows Holographic de destino**</span><span class="sxs-lookup"><span data-stu-id="997d7-167">**Target Windows Holographic SDK**</span></span>

![SDK do Windows Holographic de destino](images/xrsettings.png)

<span data-ttu-id="997d7-169">Precisamos deixar que o Unity saiba que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D.</span><span class="sxs-lookup"><span data-stu-id="997d7-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="997d7-170">Fazemos isso habilitando o suporte de realidade virtual no Unity direcionando o SDK do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="997d7-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="997d7-171">Vá para **Editar configurações de projeto > > Player**.</span><span class="sxs-lookup"><span data-stu-id="997d7-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="997d7-172">No **painel Inspetor** para configurações do Player, selecione o ícone **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="997d7-172">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="997d7-173">Expanda o grupo de **configurações XR** .</span><span class="sxs-lookup"><span data-stu-id="997d7-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="997d7-174">Na seção **renderização** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **SDKs de realidade virtual** .</span><span class="sxs-lookup"><span data-stu-id="997d7-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="997d7-175">Verifique se a **realidade mista do Windows** aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="997d7-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="997d7-176">Caso contrário, selecione o botão **+** na parte inferior da lista e escolha **realidade mista do Windows**.</span><span class="sxs-lookup"><span data-stu-id="997d7-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="997d7-177">Se você não vir o ícone **Windows Store** , verifique se selecionou o back-end de script do .NET da Windows Store antes da instalação.</span><span class="sxs-lookup"><span data-stu-id="997d7-177">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="997d7-178">Caso contrário, talvez seja necessário reinstalar o Unity com a instalação correta do Windows.</span><span class="sxs-lookup"><span data-stu-id="997d7-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="997d7-179">**Verificar configuração do .NET**</span><span class="sxs-lookup"><span data-stu-id="997d7-179">**Verify .NET Configuration**</span></span>

![Verificar configuração do .NET](images/configoptions-375px.png)

1. <span data-ttu-id="997d7-181">Vá para **Editar configurações de projeto > > Player** (talvez você ainda tenha isso na etapa anterior).</span><span class="sxs-lookup"><span data-stu-id="997d7-181">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="997d7-182">No **painel Inspetor** para configurações do Player, selecione o ícone **Windows Store** .</span><span class="sxs-lookup"><span data-stu-id="997d7-182">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="997d7-183">Na seção configuração de **outras configurações** , verifique se o **back-end de script** está definido como **.net**</span><span class="sxs-lookup"><span data-stu-id="997d7-183">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="997d7-184">Trabalho incrível ao obter todas as configurações de projeto aplicadas.</span><span class="sxs-lookup"><span data-stu-id="997d7-184">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="997d7-185">Em seguida, vamos adicionar um holograma!</span><span class="sxs-lookup"><span data-stu-id="997d7-185">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="997d7-186">Capítulo 4-criar um cubo</span><span class="sxs-lookup"><span data-stu-id="997d7-186">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="997d7-187">Criar um cubo em seu projeto de Unity é como criar qualquer outro objeto no Unity.</span><span class="sxs-lookup"><span data-stu-id="997d7-187">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="997d7-188">Colocar um cubo na frente do usuário é fácil porque o sistema de coordenadas do Unity é mapeado para o mundo real, em que um medidor no Unity é aproximadamente um medidor no mundo real.</span><span class="sxs-lookup"><span data-stu-id="997d7-188">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="997d7-189">No canto superior esquerdo do painel **hierarquia** , selecione a lista suspensa **criar** e escolha o **objeto 3D > cubo**.</span><span class="sxs-lookup"><span data-stu-id="997d7-189">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="997d7-190">Selecione o **cubo** recém-criado no painel **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="997d7-190">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="997d7-191">No **Inspetor** , localize o componente de **transformação** e altere a **posição** para (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="997d7-191">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="997d7-192">*Isso posiciona o cubo 2 metros na frente da posição inicial do usuário.*</span><span class="sxs-lookup"><span data-stu-id="997d7-192">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="997d7-193">No componente **transformar** , altere a **rotação** para (**x**: 45, **y**: 45, **z**: 45) e altere a **escala** para (**x**: 0,25, **y**: 0,25, **z**: 0,25).</span><span class="sxs-lookup"><span data-stu-id="997d7-193">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="997d7-194">*Isso dimensiona o cubo para 0,25 metros.*</span><span class="sxs-lookup"><span data-stu-id="997d7-194">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="997d7-195">Para salvar as alterações de cena, selecione **arquivo > salvar cena**.</span><span class="sxs-lookup"><span data-stu-id="997d7-195">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="997d7-196">Capítulo 5 – verificar no dispositivo do editor do Unity</span><span class="sxs-lookup"><span data-stu-id="997d7-196">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="997d7-197">Agora que criamos nosso cubo, é hora de fazer um check-in rápido no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="997d7-197">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="997d7-198">Você pode fazer isso diretamente de dentro do editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="997d7-198">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="997d7-199">Configuração inicial</span><span class="sxs-lookup"><span data-stu-id="997d7-199">Initial setup</span></span>

1. <span data-ttu-id="997d7-200">No seu PC de desenvolvimento, no Unity, abra o **arquivo > janela configurações de Build** .</span><span class="sxs-lookup"><span data-stu-id="997d7-200">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="997d7-201">Altere a **plataforma** para **plataforma universal do Windows** e clique em **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="997d7-201">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="997d7-202">Para o HoloLens, use a comunicação remota do Unity</span><span class="sxs-lookup"><span data-stu-id="997d7-202">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="997d7-203">No seu HoloLens, instale e execute o [Holographic Remoting Player](holographic-remoting-player.md), disponível na Windows Store.</span><span class="sxs-lookup"><span data-stu-id="997d7-203">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="997d7-204">Inicie o aplicativo no dispositivo e ele entrará em um estado de espera e mostrará o endereço IP do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="997d7-204">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="997d7-205">Anote o IP.</span><span class="sxs-lookup"><span data-stu-id="997d7-205">Note down the IP.</span></span>
2. <span data-ttu-id="997d7-206">Abra o **Window > XR > emulação Holographic**.</span><span class="sxs-lookup"><span data-stu-id="997d7-206">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="997d7-207">Altere o **modo de emulação** de **nenhum** para **remoto para dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="997d7-207">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="997d7-208">Em **computador remoto**, insira o endereço IP do seu HoloLens observado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="997d7-208">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="997d7-209">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="997d7-209">Click **Connect**.</span></span>
6. <span data-ttu-id="997d7-210">Verifique se o **status da conexão** é alterado para verde **conectado**.</span><span class="sxs-lookup"><span data-stu-id="997d7-210">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="997d7-211">Agora você pode clicar em **reproduzir** no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="997d7-211">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="997d7-212">Agora, você poderá ver o cubo no dispositivo e no editor.</span><span class="sxs-lookup"><span data-stu-id="997d7-212">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="997d7-213">Você pode pausar, inspecionar objetos e depurá-los da mesma forma que está executando um aplicativo no editor, pois isso é basicamente o que está acontecendo, mas com entrada de vídeo, áudio e dispositivo transmitida e horizontal pela rede entre a máquina host e o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="997d7-213">You can pause, inspect objects, and debug just like you are running an app in the editor, because that's essentially what's happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="997d7-214">Para outros fones de ouvido com suporte da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="997d7-214">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="997d7-215">Conecte o headset ao seu computador de desenvolvimento usando o cabo USB e o HDMI ou o cabo de porta de vídeo.</span><span class="sxs-lookup"><span data-stu-id="997d7-215">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="997d7-216">Inicie o **portal de realidade misturada** e verifique se você concluiu a experiência de primeira execução.</span><span class="sxs-lookup"><span data-stu-id="997d7-216">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="997d7-217">No Unity, agora você pode pressionar o botão reproduzir.</span><span class="sxs-lookup"><span data-stu-id="997d7-217">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="997d7-218">Agora, você poderá ver a renderização do cubo em seu headset de realidade misturada e no editor.</span><span class="sxs-lookup"><span data-stu-id="997d7-218">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="997d7-219">Capítulo 6-criar e implantar no dispositivo a partir do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="997d7-219">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="997d7-220">Agora estamos prontos para compilar nosso projeto no Visual Studio e implantá-lo em nosso dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="997d7-220">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="997d7-221">Exportar para a solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="997d7-221">Export to the Visual Studio solution</span></span>

1.  <span data-ttu-id="997d7-222">Abra o **arquivo > janela configurações de Build** .</span><span class="sxs-lookup"><span data-stu-id="997d7-222">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="997d7-223">Clique em **Adicionar abrir cenas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="997d7-223">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="997d7-224">Altere a **plataforma** para **plataforma universal do Windows** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="997d7-224">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="997d7-225">Nas configurações da **Windows Store** , verifique se o **SDK** é **Universal 10**.</span><span class="sxs-lookup"><span data-stu-id="997d7-225">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="997d7-226">Para o dispositivo de destino, deixe para **qualquer dispositivo** para o obstruído exibir ou alternar para o **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="997d7-226">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="997d7-227">O **tipo de compilação UWP** deve ser **D3D**.</span><span class="sxs-lookup"><span data-stu-id="997d7-227">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="997d7-228">O **SDK do UWP** pode ser deixado no **mais recente instalado**.</span><span class="sxs-lookup"><span data-stu-id="997d7-228">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="997d7-229">Verifique **os C# projetos do Unity** em depuração.</span><span class="sxs-lookup"><span data-stu-id="997d7-229">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="997d7-230">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="997d7-230">Click **Build**.</span></span>
10. <span data-ttu-id="997d7-231">No explorador de arquivos, clique em **nova pasta** e nomeie a pasta como **"aplicativo"** .</span><span class="sxs-lookup"><span data-stu-id="997d7-231">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="997d7-232">Com a pasta do **aplicativo** selecionada, clique no botão **Selecionar pasta** .</span><span class="sxs-lookup"><span data-stu-id="997d7-232">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="997d7-233">Quando o Unity terminar a compilação, uma janela do explorador de arquivos do Windows será exibida.</span><span class="sxs-lookup"><span data-stu-id="997d7-233">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="997d7-234">Abra a pasta do **aplicativo** no explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="997d7-234">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="997d7-235">Abrir a solução do Visual Studio gerada (MixedRealityIntroduction. sln neste exemplo)</span><span class="sxs-lookup"><span data-stu-id="997d7-235">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="997d7-236">Compilar a solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="997d7-236">Compile the Visual Studio solution</span></span>

<span data-ttu-id="997d7-237">Por fim, compilaremos a solução do Visual Studio exportada, a implantaremos e a experimentaremos no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="997d7-237">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="997d7-238">Usando a barra de ferramentas superior no Visual Studio, altere o destino de **debug** para **Release** e de **ARM** para **x86**.</span><span class="sxs-lookup"><span data-stu-id="997d7-238">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="997d7-239">As instruções são diferentes para a implantação em um dispositivo versus o emulador.</span><span class="sxs-lookup"><span data-stu-id="997d7-239">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="997d7-240">Siga as instruções que correspondem à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="997d7-240">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="997d7-241">Implantar em um dispositivo de realidade mista por Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="997d7-241">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="997d7-242">Clique na seta ao lado do botão **computador local** e altere o destino de implantação para **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="997d7-242">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="997d7-243">Insira o endereço IP do dispositivo de realidade misturada e altere o **modo de autenticação** para universal (protocolo não criptografado) para o HoloLens e o **Windows** para outros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="997d7-243">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="997d7-244">Clique em **depurar > iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="997d7-244">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="997d7-245">**Para o HoloLens**, se esta for a primeira vez que você está implantando em seu dispositivo, você precisará emparelhar [usando o Visual Studio](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="997d7-245">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="997d7-246">Implantar no dispositivo de realidade mista sobre USB</span><span class="sxs-lookup"><span data-stu-id="997d7-246">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="997d7-247">Verifique se o dispositivo está conectado via cabo USB.</span><span class="sxs-lookup"><span data-stu-id="997d7-247">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="997d7-248">**Para o HoloLens**, clique na seta ao lado do botão **computador local** e altere o destino de implantação para **dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="997d7-248">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="997d7-249">**Para direcionar dispositivos obstruído conectados ao seu PC**, mantenha a configuração para computador local.</span><span class="sxs-lookup"><span data-stu-id="997d7-249">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="997d7-250">Verifique se você tem o **portal de realidade misturada** em execução.</span><span class="sxs-lookup"><span data-stu-id="997d7-250">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="997d7-251">Clique em **depurar > iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="997d7-251">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="997d7-252">Implantar no emulador</span><span class="sxs-lookup"><span data-stu-id="997d7-252">Deploy to Emulator</span></span>

1. <span data-ttu-id="997d7-253">Clique na seta ao lado do botão **dispositivo** e, na lista suspensa, selecione **emulador do HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="997d7-253">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="997d7-254">Clique em **depurar > iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="997d7-254">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="997d7-255">Experimente seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="997d7-255">Try out your app</span></span>

<span data-ttu-id="997d7-256">Agora que seu aplicativo está implantado, tente mover tudo em todo o cubo e observe que ele permanece no mundo inteiro.</span><span class="sxs-lookup"><span data-stu-id="997d7-256">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="997d7-257">Consulte também</span><span class="sxs-lookup"><span data-stu-id="997d7-257">See also</span></span>

* [<span data-ttu-id="997d7-258">Visão geral do desenvolvimento do Unity</span><span class="sxs-lookup"><span data-stu-id="997d7-258">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="997d7-259">Melhores práticas para trabalhar com o Unity e o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="997d7-259">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="997d7-260">Informações básicas do Sr 101</span><span class="sxs-lookup"><span data-stu-id="997d7-260">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="997d7-261">101E noções básicas do Sr</span><span class="sxs-lookup"><span data-stu-id="997d7-261">MR Basics 101E</span></span>](holograms-101e.md)

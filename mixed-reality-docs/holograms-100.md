---
title: Sr-noções básicas 100 – introdução ao Unity
description: Saiba como criar seu primeiro aplicativo "Hello World" básico de realidade misturada.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidade misturada, realidade do Windows Mixed, HoloLens, imersão, VR, Sr, introdução, holograma, Academia, tutorial
ms.openlocfilehash: 58a1785ef74872c633cf65d6a32e24d517367359
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570310"
---
# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="1963e-104">Noções básicas do MR 100: introdução ao Unity</span><span class="sxs-lookup"><span data-stu-id="1963e-104">MR Basics 100: Getting started with Unity</span></span>

>[!IMPORTANT]
><span data-ttu-id="1963e-105">Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.</span><span class="sxs-lookup"><span data-stu-id="1963e-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1963e-106">Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1963e-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1963e-107">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1963e-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1963e-108">Eles serão mantidos para continuar funcionando nos dispositivos compatíveis.</span><span class="sxs-lookup"><span data-stu-id="1963e-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1963e-109">[Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1963e-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="1963e-110">Este tutorial orientará você na criação de um aplicativo básico de realidade misturada criado com o Unity.</span><span class="sxs-lookup"><span data-stu-id="1963e-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="1963e-111">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="1963e-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1963e-112">Curso</span><span class="sxs-lookup"><span data-stu-id="1963e-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1963e-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1963e-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1963e-114"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="1963e-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1963e-115">Noções básicas do MR 100: introdução ao Unity</span><span class="sxs-lookup"><span data-stu-id="1963e-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="1963e-116">✔️</span><span class="sxs-lookup"><span data-stu-id="1963e-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1963e-117">✔️</span><span class="sxs-lookup"><span data-stu-id="1963e-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="1963e-118">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1963e-118">Prerequisites</span></span>

* <span data-ttu-id="1963e-119">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1963e-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="1963e-120">Capítulo 1-criar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="1963e-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="1963e-121">Para criar um aplicativo com o Unity, primeiro você precisa criar um projeto.</span><span class="sxs-lookup"><span data-stu-id="1963e-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="1963e-122">Esse projeto é organizado em algumas pastas, o mais importante deles é sua pasta de ativos.</span><span class="sxs-lookup"><span data-stu-id="1963e-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="1963e-123">Essa é a pasta que contém todos os ativos que você importa das ferramentas de criação de conteúdo digital, como Maya, Max cinema 4D ou Photoshop, todo o código criado com o Visual Studio ou seu editor de código favorito, e qualquer quantidade de arquivos de conteúdo que o Unity cria à medida que você compõe cenas, animações e outros tipos de ativos de Unity no editor.</span><span class="sxs-lookup"><span data-stu-id="1963e-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="1963e-124">Para compilar e implantar aplicativos UWP, o Unity pode exportar o projeto como uma solução do Visual Studio que conterá todos os arquivos de ativos e de código necessários.</span><span class="sxs-lookup"><span data-stu-id="1963e-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="1963e-125">Iniciar o Unity</span><span class="sxs-lookup"><span data-stu-id="1963e-125">Start Unity</span></span>
2. <span data-ttu-id="1963e-126">Selecionar **novo**</span><span class="sxs-lookup"><span data-stu-id="1963e-126">Select **New**</span></span>
3. <span data-ttu-id="1963e-127">Insira um nome de projeto (por exemplo, "MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="1963e-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="1963e-128">Insira um local para salvar seu projeto</span><span class="sxs-lookup"><span data-stu-id="1963e-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="1963e-129">Verifique se a alternância **3D** está selecionada</span><span class="sxs-lookup"><span data-stu-id="1963e-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="1963e-130">Selecione **criar projeto**</span><span class="sxs-lookup"><span data-stu-id="1963e-130">Select **Create project**</span></span>

<span data-ttu-id="1963e-131">Parabéns, você está pronto para começar a usar suas personalizações de realidade misturada agora.</span><span class="sxs-lookup"><span data-stu-id="1963e-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="1963e-132">Capítulo 2 – configurar a câmera</span><span class="sxs-lookup"><span data-stu-id="1963e-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="1963e-133">A câmera principal do Unity lida com o controle de cabeçalho e a renderização de estereoscópico.</span><span class="sxs-lookup"><span data-stu-id="1963e-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="1963e-134">Há algumas alterações a serem feitas na câmera principal para usá-la com realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1963e-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="1963e-135">Selecionar arquivo > nova cena</span><span class="sxs-lookup"><span data-stu-id="1963e-135">Select File > New Scene</span></span>

<span data-ttu-id="1963e-136">Primeiro, será mais fácil definir o layout de seu aplicativo se você imaginar a posição inicial do usuário como (**X**: 0, **Y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="1963e-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="1963e-137">Como a câmera principal está acompanhando a movimentação do cabeçalho do usuário, a posição inicial do usuário pode ser definida definindo a posição inicial da câmera principal.</span><span class="sxs-lookup"><span data-stu-id="1963e-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="1963e-138">Selecione a **câmera principal** no painel **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="1963e-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="1963e-139">No painel **Inspetor** , localize o componente **transformação** e altere a **posição** de (**x**: 0, **y**: 1, **z**:-10) para (**x**: 0, **y**: 0, **z**: 0)</span><span class="sxs-lookup"><span data-stu-id="1963e-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="1963e-140">Em segundo lugar, o plano de fundo da câmera padrão precisa de algum pensamento.</span><span class="sxs-lookup"><span data-stu-id="1963e-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="1963e-141">**Para aplicativos de HoloLens**, o mundo real deve aparecer atrás de tudo que a câmera renderiza, não uma textura Skybox.</span><span class="sxs-lookup"><span data-stu-id="1963e-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="1963e-142">Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e altere a lista suspensa **limpar sinalizadores** de **Skybox** para **cor sólida**.</span><span class="sxs-lookup"><span data-stu-id="1963e-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="1963e-143">Selecione o seletor de cor do **plano de fundo** e altere os valores de **RGBA** para (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="1963e-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="1963e-144">**Para aplicativos de realidade misturados direcionados a headsets de imersão**, podemos usar a textura padrão do Skybox que o Unity fornece.</span><span class="sxs-lookup"><span data-stu-id="1963e-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="1963e-145">Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e mantenha o menu suspenso **limpar sinalizadores** em **Skybox**.</span><span class="sxs-lookup"><span data-stu-id="1963e-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="1963e-146">Em terceiro lugar, vamos considerar o próximo clipe no Unity e impedir que os objetos sejam renderizados muito próximos dos olhos dos usuários, uma vez que um usuário se aproxima de um objeto ou um objeto se aproxima de um usuário.</span><span class="sxs-lookup"><span data-stu-id="1963e-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="1963e-147">**Para aplicativos do HoloLens**, o próximo clipe pode ser definido como o [hololens recomendado](camera-in-unity.md#clip-planes) 0,85 metros.</span><span class="sxs-lookup"><span data-stu-id="1963e-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="1963e-148">Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e altere o campo **próximo do plano do clipe** do padrão **0,3** para o HoloLens recomendado **0,85**.</span><span class="sxs-lookup"><span data-stu-id="1963e-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="1963e-149">**Para aplicativos de realidade misturados direcionados a headsets de imersão**, podemos usar a configuração padrão que o Unity fornece.</span><span class="sxs-lookup"><span data-stu-id="1963e-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="1963e-150">Com a **câmera principal** ainda selecionada no painel **hierarquia** , localize o componente **câmera** no painel **Inspetor** e mantenha o campo **próximo do plano do clipe** para o padrão **0,3**.</span><span class="sxs-lookup"><span data-stu-id="1963e-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="1963e-151">Por fim, vamos salvar nosso progresso até o momento.</span><span class="sxs-lookup"><span data-stu-id="1963e-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="1963e-152">Para salvar as alterações de cena, selecione **arquivo > salvar cena como**, nomeie a cena **principal**e selecione **salvar**.</span><span class="sxs-lookup"><span data-stu-id="1963e-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="1963e-153">Capítulo 3-configurar as configurações do projeto</span><span class="sxs-lookup"><span data-stu-id="1963e-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="1963e-154">Neste capítulo, definiremos algumas configurações de projeto do Unity que nos ajudam a direcionar o SDK do Windows Holographic para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1963e-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="1963e-155">Também definiremos algumas configurações de qualidade para nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1963e-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="1963e-156">Por fim, garantiremos que nossos destinos de compilação sejam definidos como Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="1963e-156">Finally, we will ensure our build targets are set to Universal Windows Platform.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="1963e-157">Configurações de desempenho e qualidade do Unity</span><span class="sxs-lookup"><span data-stu-id="1963e-157">Unity performance and quality settings</span></span>

<span data-ttu-id="1963e-158">**Configurações de qualidade do Unity para o HoloLens**</span><span class="sxs-lookup"><span data-stu-id="1963e-158">**Unity quality settings for HoloLens**</span></span>

![Configurações de qualidade do Unity para o HoloLens](images/qualitysettings.png)

<span data-ttu-id="1963e-160">Como a manutenção da alta taxa de quadros no HoloLens é tão importante, queremos que as configurações de qualidade sejam ajustadas para um desempenho mais rápido.</span><span class="sxs-lookup"><span data-stu-id="1963e-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="1963e-161">Para obter informações de desempenho mais detalhadas, [recomendações de desempenho para o Unity](performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="1963e-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="1963e-162">Selecione **Editar configurações do projeto > > qualidade**</span><span class="sxs-lookup"><span data-stu-id="1963e-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="1963e-163">Selecione o **menu suspenso** sob o logotipo **plataforma universal do Windows** e selecione **muito baixo**.</span><span class="sxs-lookup"><span data-stu-id="1963e-163">Select the **dropdown** under the **Universal Windows Platform** logo and select **Very Low**.</span></span> <span data-ttu-id="1963e-164">Você saberá que a configuração é aplicada corretamente quando a caixa na coluna Plataforma Universal do Windows e a linha **muito baixa** estiver verde.</span><span class="sxs-lookup"><span data-stu-id="1963e-164">You'll know the setting is applied correctly when the box in the Universal Windows Platform column and **Very Low** row is green.</span></span>

<span data-ttu-id="1963e-165">**Para aplicativos de realidade misturados direcionados a exibições do obstruído**, você pode deixar as configurações de qualidade com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="1963e-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="1963e-166">SDK do Windows 10 de destino</span><span class="sxs-lookup"><span data-stu-id="1963e-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="1963e-167">**SDK do Windows Holographic de destino**</span><span class="sxs-lookup"><span data-stu-id="1963e-167">**Target Windows Holographic SDK**</span></span>

![SDK do Windows Holographic de destino](images/xrsettings.png)

<span data-ttu-id="1963e-169">Precisamos deixar que o Unity saiba que o aplicativo que estamos tentando exportar deve criar uma [exibição imersiva](app-views.md) em vez de uma exibição 2D.</span><span class="sxs-lookup"><span data-stu-id="1963e-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="1963e-170">Fazemos isso habilitando o suporte de realidade virtual no Unity direcionando o SDK do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="1963e-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="1963e-171">Vá para **Editar configurações de projeto > > Player**.</span><span class="sxs-lookup"><span data-stu-id="1963e-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="1963e-172">No **painel Inspetor** para configurações do Player, selecione o ícone de **plataforma universal do Windows** .</span><span class="sxs-lookup"><span data-stu-id="1963e-172">In the **Inspector Panel** for Player Settings, select the **Universal Windows Platform** icon.</span></span>
3. <span data-ttu-id="1963e-173">Expanda o grupo **Configurações de XR**.</span><span class="sxs-lookup"><span data-stu-id="1963e-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="1963e-174">Na seção **renderização** , marque a caixa de seleção **suporte à realidade virtual** para adicionar uma nova lista de **SDKs de realidade virtual** .</span><span class="sxs-lookup"><span data-stu-id="1963e-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="1963e-175">Verifique se **Windows Mixed Reality** aparece na lista.</span><span class="sxs-lookup"><span data-stu-id="1963e-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="1963e-176">Se não aparecer, selecione o botão **+** na parte inferior da lista e escolha **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="1963e-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="1963e-177">Se você não vir o ícone de **plataforma universal do Windows** , verifique se selecionou o suporte de plataforma universal do Windows Build durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="1963e-177">If you do not see the **Universal Windows Platform** icon, double check to make sure you selected Universal Windows Platform Build Support during installation.</span></span> <span data-ttu-id="1963e-178">Caso contrário, talvez seja necessário reinstalar o Unity com a instalação correta do Windows.</span><span class="sxs-lookup"><span data-stu-id="1963e-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="1963e-179">Trabalho incrível ao obter todas as configurações de projeto aplicadas.</span><span class="sxs-lookup"><span data-stu-id="1963e-179">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="1963e-180">Em seguida, vamos adicionar um holograma!</span><span class="sxs-lookup"><span data-stu-id="1963e-180">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="1963e-181">Capítulo 4-criar um cubo</span><span class="sxs-lookup"><span data-stu-id="1963e-181">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="1963e-182">Criar um cubo em seu projeto de Unity é como criar qualquer outro objeto no Unity.</span><span class="sxs-lookup"><span data-stu-id="1963e-182">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="1963e-183">Colocar um cubo na frente do usuário é fácil porque o sistema de coordenadas do Unity é mapeado para o mundo real, em que um medidor no Unity é aproximadamente um medidor no mundo real.</span><span class="sxs-lookup"><span data-stu-id="1963e-183">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="1963e-184">No canto superior esquerdo do painel **hierarquia** , selecione a lista suspensa **criar** e escolha o **objeto 3D > cubo**.</span><span class="sxs-lookup"><span data-stu-id="1963e-184">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="1963e-185">Selecione o **cubo** recém-criado no painel **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="1963e-185">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="1963e-186">No **Inspetor** , localize o componente de **transformação** e altere a **posição** para (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="1963e-186">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="1963e-187">*Isso posiciona o cubo 2 metros na frente da posição inicial do usuário.*</span><span class="sxs-lookup"><span data-stu-id="1963e-187">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="1963e-188">No componente **transformar** , altere a **rotação** para (**x**: 45, **y**: 45, **z**: 45) e altere a **escala** para (**x**: 0,25, **y**: 0,25, **z**: 0,25).</span><span class="sxs-lookup"><span data-stu-id="1963e-188">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="1963e-189">*Isso dimensiona o cubo para 0,25 metros.*</span><span class="sxs-lookup"><span data-stu-id="1963e-189">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="1963e-190">Para salvar as alterações de cena, selecione **arquivo > salvar cena**.</span><span class="sxs-lookup"><span data-stu-id="1963e-190">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="1963e-191">Capítulo 5 – verificar no dispositivo do editor do Unity</span><span class="sxs-lookup"><span data-stu-id="1963e-191">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="1963e-192">Agora que criamos nosso cubo, é hora de fazer um check-in rápido no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1963e-192">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="1963e-193">Você pode fazer isso diretamente de dentro do editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="1963e-193">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="1963e-194">Instalação inicial</span><span class="sxs-lookup"><span data-stu-id="1963e-194">Initial setup</span></span>

1. <span data-ttu-id="1963e-195">No seu PC de desenvolvimento, no Unity, abra o **arquivo > janela configurações de Build** .</span><span class="sxs-lookup"><span data-stu-id="1963e-195">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="1963e-196">Altere a **plataforma** para **plataforma universal do Windows** e clique em **alternar plataforma**</span><span class="sxs-lookup"><span data-stu-id="1963e-196">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="1963e-197">Para o HoloLens, use a comunicação remota do Unity</span><span class="sxs-lookup"><span data-stu-id="1963e-197">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="1963e-198">No seu HoloLens, instale e execute o [Holographic Remoting Player](holographic-remoting-player.md), disponível na Windows Store.</span><span class="sxs-lookup"><span data-stu-id="1963e-198">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="1963e-199">Inicie o aplicativo no dispositivo e ele entrará em um estado de espera e mostrará o endereço IP do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1963e-199">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="1963e-200">Anote o IP.</span><span class="sxs-lookup"><span data-stu-id="1963e-200">Note down the IP.</span></span>
2. <span data-ttu-id="1963e-201">Abra o **Window > XR > emulação Holographic**.</span><span class="sxs-lookup"><span data-stu-id="1963e-201">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="1963e-202">Altere o **modo de emulação** de **nenhum** para **remoto para dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="1963e-202">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="1963e-203">Em **computador remoto**, insira o endereço IP do seu HoloLens observado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1963e-203">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="1963e-204">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="1963e-204">Click **Connect**.</span></span>
6. <span data-ttu-id="1963e-205">Verifique se o **status da conexão** é alterado para verde **conectado**.</span><span class="sxs-lookup"><span data-stu-id="1963e-205">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="1963e-206">Agora você pode clicar em **reproduzir** no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="1963e-206">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="1963e-207">Agora, você poderá ver o cubo no dispositivo e no editor.</span><span class="sxs-lookup"><span data-stu-id="1963e-207">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="1963e-208">Você pode pausar, inspecionar objetos e depurá-los da mesma forma que está executando um aplicativo no editor, pois isso é basicamente o que está acontecendo, mas com entrada de vídeo, áudio e dispositivo transmitida e horizontal pela rede entre a máquina host e o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1963e-208">You can pause, inspect objects, and debug just like you are running an app in the editor, because that's essentially what's happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="1963e-209">Para outros fones de ouvido com suporte da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="1963e-209">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="1963e-210">Conecte o headset ao seu computador de desenvolvimento usando o cabo USB e o HDMI ou o cabo de porta de vídeo.</span><span class="sxs-lookup"><span data-stu-id="1963e-210">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="1963e-211">Inicie o **portal de realidade misturada** e verifique se você concluiu a experiência de primeira execução.</span><span class="sxs-lookup"><span data-stu-id="1963e-211">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="1963e-212">No Unity, agora você pode pressionar o botão reproduzir.</span><span class="sxs-lookup"><span data-stu-id="1963e-212">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="1963e-213">Agora, você poderá ver a renderização do cubo em seu headset de realidade misturada e no editor.</span><span class="sxs-lookup"><span data-stu-id="1963e-213">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="1963e-214">Capítulo 6-criar e implantar no dispositivo a partir do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1963e-214">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="1963e-215">Agora estamos prontos para compilar nosso projeto no Visual Studio e implantá-lo em nosso dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="1963e-215">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="1963e-216">Exportar para a solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1963e-216">Export to the Visual Studio solution</span></span>

1. <span data-ttu-id="1963e-217">Abra o **arquivo > janela configurações de Build** .</span><span class="sxs-lookup"><span data-stu-id="1963e-217">Open **File > Build Settings** window.</span></span>
1. <span data-ttu-id="1963e-218">Clique em **Adicionar abrir cenas** para adicionar a cena.</span><span class="sxs-lookup"><span data-stu-id="1963e-218">Click **Add Open Scenes** to add the scene.</span></span>
1. <span data-ttu-id="1963e-219">Altere a **plataforma** para **plataforma universal do Windows** e clique em **alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="1963e-219">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
1. <span data-ttu-id="1963e-220">Em configurações de **plataforma universal do Windows** , verifique se o **SDK** é **Universal 10**.</span><span class="sxs-lookup"><span data-stu-id="1963e-220">In **Universal Windows Platform** settings, ensure **SDK** is **Universal 10**.</span></span>
1. <span data-ttu-id="1963e-221">Para o dispositivo de destino, deixe para **qualquer dispositivo** para o obstruído exibir ou alternar para o **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1963e-221">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
1. <span data-ttu-id="1963e-222">O **tipo de compilação UWP** deve ser **D3D**.</span><span class="sxs-lookup"><span data-stu-id="1963e-222">**UWP Build Type** should be **D3D**.</span></span>
1. <span data-ttu-id="1963e-223">O **SDK do UWP** pode ser deixado no **mais recente instalado**.</span><span class="sxs-lookup"><span data-stu-id="1963e-223">**UWP SDK** could be left at **Latest installed**.</span></span>
1. <span data-ttu-id="1963e-224">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="1963e-224">Click **Build**.</span></span>
1. <span data-ttu-id="1963e-225">No explorador de arquivos, clique em **nova pasta** e nomeie a pasta como **"aplicativo"**.</span><span class="sxs-lookup"><span data-stu-id="1963e-225">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
1. <span data-ttu-id="1963e-226">Com a pasta do **aplicativo** selecionada, clique no botão **Selecionar pasta** .</span><span class="sxs-lookup"><span data-stu-id="1963e-226">With the **App** folder selected, click the **Select Folder** button.</span></span>
1. <span data-ttu-id="1963e-227">Quando o Unity terminar a compilação, uma janela do explorador de arquivos do Windows será exibida.</span><span class="sxs-lookup"><span data-stu-id="1963e-227">When Unity is done building, a Windows File Explorer window will appear.</span></span>
1. <span data-ttu-id="1963e-228">Abra a pasta do **aplicativo** no explorador de arquivos.</span><span class="sxs-lookup"><span data-stu-id="1963e-228">Open the **App** folder in file explorer.</span></span>
1. <span data-ttu-id="1963e-229">Abrir a solução do Visual Studio gerada (MixedRealityIntroduction. sln neste exemplo)</span><span class="sxs-lookup"><span data-stu-id="1963e-229">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="1963e-230">Compilar a solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1963e-230">Compile the Visual Studio solution</span></span>

<span data-ttu-id="1963e-231">Por fim, compilaremos a solução do Visual Studio exportada, a implantaremos e a experimentaremos no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1963e-231">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="1963e-232">Usando a barra de ferramentas superior no Visual Studio, altere o destino de **debug** para **Release** e de **ARM** para **x86**.</span><span class="sxs-lookup"><span data-stu-id="1963e-232">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="1963e-233">As instruções são diferentes para a implantação em um dispositivo versus o emulador.</span><span class="sxs-lookup"><span data-stu-id="1963e-233">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="1963e-234">Siga as instruções que correspondem à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="1963e-234">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="1963e-235">Implantar em um dispositivo de realidade mista por Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="1963e-235">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="1963e-236">Clique na seta ao lado do botão **computador local** e altere o destino de implantação para **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="1963e-236">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="1963e-237">Insira o endereço IP do dispositivo de realidade misturada e altere o **modo de autenticação** para universal (protocolo não criptografado) para o HoloLens e o **Windows** para outros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1963e-237">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="1963e-238">Clique em **depurar > iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="1963e-238">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="1963e-239">**Para o HoloLens**, se esta for a primeira vez que você está implantando em seu dispositivo, você precisará emparelhar [usando o Visual Studio](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1963e-239">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="1963e-240">Implantar no dispositivo de realidade mista sobre USB</span><span class="sxs-lookup"><span data-stu-id="1963e-240">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="1963e-241">Verifique se o dispositivo está conectado via cabo USB.</span><span class="sxs-lookup"><span data-stu-id="1963e-241">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="1963e-242">**Para o HoloLens**, clique na seta ao lado do botão **computador local** e altere o destino de implantação para **dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="1963e-242">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="1963e-243">**Para direcionar dispositivos obstruído conectados ao seu PC**, mantenha a configuração para computador local.</span><span class="sxs-lookup"><span data-stu-id="1963e-243">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="1963e-244">Verifique se você tem o **portal de realidade misturada** em execução.</span><span class="sxs-lookup"><span data-stu-id="1963e-244">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="1963e-245">Clique em **depurar > iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="1963e-245">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="1963e-246">Implantar no emulador</span><span class="sxs-lookup"><span data-stu-id="1963e-246">Deploy to Emulator</span></span>

1. <span data-ttu-id="1963e-247">Clique na seta ao lado do botão **dispositivo** e, na lista suspensa, selecione **emulador do HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1963e-247">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="1963e-248">Clique em **depurar > iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="1963e-248">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="1963e-249">Experimente seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1963e-249">Try out your app</span></span>

<span data-ttu-id="1963e-250">Agora que seu aplicativo está implantado, tente mover tudo em todo o cubo e observe que ele permanece no mundo inteiro.</span><span class="sxs-lookup"><span data-stu-id="1963e-250">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="1963e-251">Confira também</span><span class="sxs-lookup"><span data-stu-id="1963e-251">See also</span></span>

* [<span data-ttu-id="1963e-252">Visão geral do desenvolvimento do Unity</span><span class="sxs-lookup"><span data-stu-id="1963e-252">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="1963e-253">Melhores práticas para trabalhar com o Unity e o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1963e-253">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="1963e-254">Noções básicas do MR 101</span><span class="sxs-lookup"><span data-stu-id="1963e-254">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="1963e-255">Noções básicas do MR 101E</span><span class="sxs-lookup"><span data-stu-id="1963e-255">MR Basics 101E</span></span>](holograms-101e.md)

---
title: Tutoriais de introdução – 2. Como inicializar o seu projeto e implantar o primeiro aplicativo
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5cac7d6f776619cbc2a0e0891b7915b656708726
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376648"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="d7d88-105">2. Como inicializar o seu projeto e implantar o primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7d88-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="d7d88-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d7d88-106">Overview</span></span>

<span data-ttu-id="d7d88-107">Neste tutorial, você aprenderá a criar um projeto do Unity, configurá-lo para o desenvolvimento do <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> e importar o MRTK.</span><span class="sxs-lookup"><span data-stu-id="d7d88-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="d7d88-108">Você também aprenderá sobre a configuração, a criação e a implantação da cena de amostra do Unity básica do Visual Studio para o seu próprio HoloLens 2 ou emulador.</span><span class="sxs-lookup"><span data-stu-id="d7d88-108">You'll also walk through configuring, building, and deploying the basic Unity sample scene from Visual Studio to your HoloLens 2 or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="d7d88-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d7d88-109">Objectives</span></span>

* <span data-ttu-id="d7d88-110">Saiba como configurar o Unity para o desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="d7d88-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="d7d88-111">Saiba como criar e implantar o seu aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="d7d88-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="d7d88-112">Experimente a malha de mapeamento espacial, as malhas de mão e o contador da taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="d7d88-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="d7d88-113">Como criar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="d7d88-113">Creating the Unity project</span></span>

<span data-ttu-id="d7d88-114">Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:</span><span class="sxs-lookup"><span data-stu-id="d7d88-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="d7d88-116">Na lista suspensa, selecione a **versão** do Unity especificada em [Pré-requisitos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="d7d88-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="d7d88-118">Se a versão específica do Unity não estiver disponível no Hub do Unity, você poderá iniciar a instalação em <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Arquivos de Download</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="d7d88-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="d7d88-119">Na janela Criar um novo projeto:</span><span class="sxs-lookup"><span data-stu-id="d7d88-119">In the Create a new project window:</span></span>

* <span data-ttu-id="d7d88-120">Verifique se **Modelos** está definido como **3D**</span><span class="sxs-lookup"><span data-stu-id="d7d88-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="d7d88-121">Insira um **Nome de Projeto** adequado, por exemplo, _Tutoriais do MRTK_</span><span class="sxs-lookup"><span data-stu-id="d7d88-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="d7d88-122">Escolha um **Local** adequado para armazenar seu projeto, por exemplo, _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="d7d88-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="d7d88-123">Clique no botão **Criar** para criar e iniciar o novo projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="d7d88-123">Click the **Create** button to create and launch your new Unity project</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="d7d88-125">Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="d7d88-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="d7d88-126">Consequentemente, você deve salvar o projeto do Unity próximo à raiz da unidade.</span><span class="sxs-lookup"><span data-stu-id="d7d88-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="d7d88-127">Aguarde até que o Unity crie o projeto:</span><span class="sxs-lookup"><span data-stu-id="d7d88-127">Wait for Unity to create the project:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="d7d88-129">Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="d7d88-129">Switching the build platform</span></span>

<span data-ttu-id="d7d88-130">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build:</span><span class="sxs-lookup"><span data-stu-id="d7d88-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="d7d88-132">Na janela Configurações de Build, selecione **Plataforma Universal do Windows** e clique no botão **Mudar Plataforma**:</span><span class="sxs-lookup"><span data-stu-id="d7d88-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="d7d88-134">Aguarde até que o Unity termine de mudar a plataforma:</span><span class="sxs-lookup"><span data-stu-id="d7d88-134">Wait for Unity to finish switching the platform:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="d7d88-136">Quando o Unity terminar de mudar a plataforma, clique no ícone vermelho **x** para fechar a janela Configurações de Build:</span><span class="sxs-lookup"><span data-stu-id="d7d88-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="d7d88-138">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="d7d88-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="d7d88-139">No menu do Unity, selecione **Janela** > **TextMeshPro** > **Importar Recursos Essenciais do TMP** para abrir a janela Importar Pacote do Unity:</span><span class="sxs-lookup"><span data-stu-id="d7d88-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="d7d88-141">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="d7d88-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="d7d88-143">Os Recursos Essenciais do TextMeshPro são exigidos pelos elementos da interface do usuário do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d7d88-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="d7d88-144">Você poderá ignorar esta etapa se não estiver planejando usar os elementos da interface do usuário do MRTK no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d7d88-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="d7d88-145">Como importar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="d7d88-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="d7d88-146">Baixe o pacote personalizado do Unity:</span><span class="sxs-lookup"><span data-stu-id="d7d88-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="d7d88-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d7d88-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="d7d88-148">No menu do Unity, selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:</span><span class="sxs-lookup"><span data-stu-id="d7d88-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="d7d88-150">Na janela Importar pacote..., selecione o **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** que você baixou e clique no botão **Abrir**:</span><span class="sxs-lookup"><span data-stu-id="d7d88-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="d7d88-152">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="d7d88-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="d7d88-154">Como configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="d7d88-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="d7d88-155">1. Aplicar as configurações do Configurador de Projeto do MRTK</span><span class="sxs-lookup"><span data-stu-id="d7d88-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="d7d88-156">Depois que o Unity terminar de importar o pacote da seção anterior, a janela Configurador de Projeto do MRTK deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="d7d88-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="d7d88-157">Se ela não aparecer, abra a janela do Configurador acessando o menu do Unity e selecionando **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar o Projeto do Unity**:</span><span class="sxs-lookup"><span data-stu-id="d7d88-157">If it doesn't, open the Configurator window by going to the Unity menu and selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="d7d88-159">Na janela Configurador de Projeto do MRTK, expanda a seção **Modificar Configurações**, verifique se todas as opções estão marcadas e clique no botão **Aplicar** para aplicar as configurações:</span><span class="sxs-lookup"><span data-stu-id="d7d88-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="d7d88-161">2. Definir configurações adicionais do projeto</span><span class="sxs-lookup"><span data-stu-id="d7d88-161">2. Configure additional project settings</span></span>

<span data-ttu-id="d7d88-162">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="d7d88-162">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="d7d88-164">Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR**, clique no ícone **+** e selecione Windows Mixed Reality para adicionar o SDK do Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="d7d88-164">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="d7d88-166">Depois que o Unity terminar de importar o SDK do Windows Mixed Reality, a janela Configurador de Projeto do MRTK deverá aparecer novamente.</span><span class="sxs-lookup"><span data-stu-id="d7d88-166">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="d7d88-167">Se ela não aparecer, use o menu do Unity para abri-la.</span><span class="sxs-lookup"><span data-stu-id="d7d88-167">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="d7d88-168">Na janela Configurador de Projeto do MRTK, use a lista suspensa **Espacializador de áudio** para selecionar o **Espacializador MS HRTF** e clique no botão **Aplicar** para aplicar a configuração:</span><span class="sxs-lookup"><span data-stu-id="d7d88-168">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="d7d88-170">Na janela Configurações do Projeto, selecione **Player** > **Configurações de XR** e, em seguida, use a lista suspensa **Formato de Profundidade** para selecionar a **Profundidade de 16 bits**:</span><span class="sxs-lookup"><span data-stu-id="d7d88-170">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="d7d88-172">Na janela Configurações do Projeto, selecione **Player** > **Configurações de Publicação** e, em seguida, no campo **Nome do pacote**, insira um nome adequado, por exemplo, _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="d7d88-172">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="d7d88-174">O 'Nome do pacote' é o identificador exclusivo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7d88-174">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="d7d88-175">Você deve alterar esse identificador antes de implantar o aplicativo para evitar a substituição de aplicativos instalados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d7d88-175">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="d7d88-176">O 'Nome do Produto' é o nome exibido no menu Iniciar do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7d88-176">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="d7d88-177">Para facilitar a localização do aplicativo durante o desenvolvimento, adicione um sublinhado na frente do nome para que ele seja classificado para o topo.</span><span class="sxs-lookup"><span data-stu-id="d7d88-177">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="d7d88-178">Como criar e configurar a cena</span><span class="sxs-lookup"><span data-stu-id="d7d88-178">Creating and configuring the scene</span></span>

<span data-ttu-id="d7d88-179">No menu do Unity, selecione **Arquivo** > **Nova Cena** para criar uma cena:</span><span class="sxs-lookup"><span data-stu-id="d7d88-179">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="d7d88-181">No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** para adicionar o MRTK à cena atual:</span><span class="sxs-lookup"><span data-stu-id="d7d88-181">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="d7d88-183">Com o objeto **MixedRealityToolkit** selecionado na janela Hierarquia, na janela Inspetor, verifique se o perfil de configuração **MixedRealityToolkit** está definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="d7d88-183">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="d7d88-185">Normalmente, você usará o DefaultHoloLens2ConfigurationProfile ao desenvolver para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7d88-185">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="d7d88-186">No entanto, neste tutorial, você usará o DefaultMixedRealityToolkitConfigurationProfile. Depois, no próximo tutorial, [Como configurar os perfis do MRTK](mr-learning-base-03.md), altere para o DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="d7d88-186">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="d7d88-187">No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:</span><span class="sxs-lookup"><span data-stu-id="d7d88-187">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="d7d88-189">Na janela Salvar cena, navegue até a pasta **Cenas** do seu projeto, dê um nome adequado à sua cena (por exemplo, _Introdução_) e clique no botão **Salvar** para salvar a cena:</span><span class="sxs-lookup"><span data-stu-id="d7d88-189">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="d7d88-191">Como criar o aplicativo para o seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d7d88-191">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="d7d88-192">1. Compilar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="d7d88-192">1. Build the Unity project</span></span>

<span data-ttu-id="d7d88-193">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="d7d88-193">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="d7d88-194">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar sua cena atual à lista **Cenas no Build** e clique no botão **Build** para abrir a janela Compilar Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="d7d88-194">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="d7d88-196">Na janela Compilar Plataforma Universal do Windows, escolha um local adequado para armazenar seu build, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma nova pasta e dê a ela um nome adequado, por exemplo, _GettingStarted_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="d7d88-196">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="d7d88-198">Aguarde até que o Unity conclua o processo de build:</span><span class="sxs-lookup"><span data-stu-id="d7d88-198">Wait for Unity to finish the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="d7d88-200">2. Compilar e implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7d88-200">2. Build and deploy the application</span></span>

<span data-ttu-id="d7d88-201">Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra a localização em que você armazenou o build.</span><span class="sxs-lookup"><span data-stu-id="d7d88-201">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="d7d88-202">Navegue dentro da pasta e clique duas vezes no arquivo da solução para abri-lo no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="d7d88-202">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d7d88-204">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar-se de que você tenha todos os componentes de pré-requisitos na documentação **[Instalar as Ferramentas](install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="d7d88-204">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="d7d88-205">Configure o Visual Studio para o HoloLens selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM64** e o **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="d7d88-205">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="d7d88-207">Se você estiver implantando no HoloLens (1ª geração), selecione a arquitetura **x86**.</span><span class="sxs-lookup"><span data-stu-id="d7d88-207">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="d7d88-208">Para o HoloLens, você normalmente criará para a arquitetura ARM.</span><span class="sxs-lookup"><span data-stu-id="d7d88-208">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="d7d88-209">No entanto, há um <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conhecido</strong></a> no Unity 2019.3 que causa erros ao selecionar o ARM como a arquitetura de build no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7d88-209">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="d7d88-210">A solução alternativa recomendada é criar para o ARM64.</span><span class="sxs-lookup"><span data-stu-id="d7d88-210">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="d7d88-211">Se essa não for uma opção, acesse **Editar > Configurações de Projeto > Player > Outras Configurações** e desabilite **Trabalhos Gráficos**.</span><span class="sxs-lookup"><span data-stu-id="d7d88-211">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="d7d88-212">Se o Dispositivo não for exibido como uma opção de destino, talvez seja necessário alterar o projeto de inicialização para a solução do Visual Studio do projeto IL2CPP para o projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="d7d88-212">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="d7d88-213">Para fazer isso, no Gerenciador de Soluções, clique com o botão direito do mouse no NomeDoSeuProjeto (Universal do Windows) e selecione **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="d7d88-213">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="d7d88-214">Conecte o seu HoloLens ao seu computador e, em seguida, selecione **Depurar** > **Iniciar sem Depuração** para criar e implantar no seu dispositivo:</span><span class="sxs-lookup"><span data-stu-id="d7d88-214">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="d7d88-216">Antes de compilar no dispositivo, ele precisa estar no Modo de Desenvolvedor e emparelhado com o computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d7d88-216">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="d7d88-217">Essas duas etapas podem ser concluídas seguindo [estas instruções](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d7d88-217">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="d7d88-218">Você também pode implantar no [Emulador do HoloLens](using-the-hololens-emulator.md) ou criar um [Pacote do Aplicativo](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para sideload.</span><span class="sxs-lookup"><span data-stu-id="d7d88-218">You can also deploy to the [HoloLens Emulator](using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="d7d88-219">O uso de Iniciar sem Depuração inicia automaticamente o aplicativo no seu dispositivo sem o depurador do Visual Studio anexado.</span><span class="sxs-lookup"><span data-stu-id="d7d88-219">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="d7d88-220">Selecione **Criar > Implantar Solução** para implantar no seu dispositivo sem iniciar o aplicativo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d7d88-220">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="d7d88-221">Observe o criador de perfil de Diagnóstico no aplicativo, você pode ativar ou desativar a sua visibilidade usando o comando de fala **Alternar Diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="d7d88-221">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="d7d88-222">É recomendável que você mantenha o criador de perfil visível na maior parte do tempo durante o desenvolvimento para entender quando as alterações no aplicativo podem afetar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="d7d88-222">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="d7d88-223">Por exemplo, os aplicativos do HoloLens devem [ser executados continuamente em 60 FPS](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="d7d88-223">For example, HoloLens apps should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="d7d88-224">Parabéns</span><span class="sxs-lookup"><span data-stu-id="d7d88-224">Congratulations</span></span>

<span data-ttu-id="d7d88-225">Você acabou de implantar o seu primeiro aplicativo do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7d88-225">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="d7d88-226">Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies detectadas pelo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7d88-226">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="d7d88-227">Além disso, você verá indicadores em suas mãos e dedos para o acompanhamento de mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7d88-227">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="d7d88-228">Esses recursos são apenas alguns dos componentes fundamentais incluídos no MRTK.</span><span class="sxs-lookup"><span data-stu-id="d7d88-228">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="d7d88-229">Nos próximos tutoriais, você adicionará o conteúdo à sua cena para explorar as funcionalidades do HoloLens e do MRTK.</span><span class="sxs-lookup"><span data-stu-id="d7d88-229">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

[<span data-ttu-id="d7d88-230">Próximo tutorial: 3. Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="d7d88-230">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)

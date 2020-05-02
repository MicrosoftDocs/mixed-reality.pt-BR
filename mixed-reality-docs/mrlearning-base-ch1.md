---
title: Tutoriais de introdução – 2. Inicializar o projeto e seu primeiro aplicativo
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 56adb4bfc66768684c8269c0f0cafd70c486ea8a
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376203"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="1d204-105">2. Inicializar o projeto e seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="1d204-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="1d204-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="1d204-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="1d204-107">Neste primeiro tutorial, você aprenderá mais sobre algumas das funcionalidades que o <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Kit de Ferramentas de Realidade Misturada)</a> tem a oferecer, iniciará seu primeiro aplicativo do HoloLens 2 e o implantará no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1d204-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="1d204-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1d204-108">Objectives</span></span>

* <span data-ttu-id="1d204-109">Configurar o Unity para o desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="1d204-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="1d204-110">Importar ativos e configurar a cena</span><span class="sxs-lookup"><span data-stu-id="1d204-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="1d204-111">Visualização da malha de mapeamento espacial, das malhas de mão e do contador da taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="1d204-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1d204-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1d204-112">Prerequisites</span></span>

* <span data-ttu-id="1d204-113">Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="1d204-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="1d204-114">SDK do Windows 10 10.0.18362.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="1d204-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="1d204-115">Alguma habilidade básica de programação em C#</span><span class="sxs-lookup"><span data-stu-id="1d204-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="1d204-116">Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="1d204-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="1d204-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado</span><span class="sxs-lookup"><span data-stu-id="1d204-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d204-118">A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="1d204-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="1d204-119">Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.</span><span class="sxs-lookup"><span data-stu-id="1d204-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="1d204-120">Crie um novo projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="1d204-120">Create new Unity project</span></span>

<span data-ttu-id="1d204-121">Inicie o **Hub do Unity**, selecione a guia **Projetos** e clique na **seta para baixo** ao lado do botão **Novo**:</span><span class="sxs-lookup"><span data-stu-id="1d204-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="1d204-123">Selecione a versão do Unity especificada na seção [Pré-requisitos](#prerequisites) acima:</span><span class="sxs-lookup"><span data-stu-id="1d204-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="1d204-125">Na janela Criar um novo projeto:</span><span class="sxs-lookup"><span data-stu-id="1d204-125">In the Create a new project window:</span></span>

* <span data-ttu-id="1d204-126">Verifique se **Modelos** está definido como **3D**</span><span class="sxs-lookup"><span data-stu-id="1d204-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="1d204-127">Insira um **Nome de Projeto** adequado, por exemplo, _Tutoriais do MRTK_</span><span class="sxs-lookup"><span data-stu-id="1d204-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="1d204-128">Escolha um **Local** adequado para armazenar seu projeto, por exemplo, _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="1d204-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="1d204-129">Clique no botão **Criar** para criar e iniciar o novo projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="1d204-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="1d204-131">Ao trabalhar no Windows, há um limite de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d204-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="1d204-132">O Unity é afetado por esses limites e pode falhar ao compilar se algum caminho de arquivo tiver mais de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d204-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="1d204-133">Consequentemente, é altamente recomendável armazenar seu projeto do Unity o mais próximo possível da raiz da unidade.</span><span class="sxs-lookup"><span data-stu-id="1d204-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="1d204-134">Aguarde até que o Unity crie o projeto:</span><span class="sxs-lookup"><span data-stu-id="1d204-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="1d204-136">Configure o projeto do Unity para o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1d204-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="1d204-137">Nesta seção, você mudará a plataforma de build, habilitará a realidade virtual e habilitará a percepção espacial.</span><span class="sxs-lookup"><span data-stu-id="1d204-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="1d204-138">1. Alternar plataforma de build</span><span class="sxs-lookup"><span data-stu-id="1d204-138">1. Switch build platform</span></span>

<span data-ttu-id="1d204-139">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build:</span><span class="sxs-lookup"><span data-stu-id="1d204-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="1d204-141">Na janela Configurações de Build, selecione **Plataforma Universal do Windows** e clique no botão **Mudar Plataforma**:</span><span class="sxs-lookup"><span data-stu-id="1d204-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="1d204-143">Aguarde até que o Unity termine de mudar a plataforma:</span><span class="sxs-lookup"><span data-stu-id="1d204-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="1d204-145">Quando o Unity terminar de mudar a plataforma, clique no ícone vermelho **x** para fechar a janela Configurações de Build:</span><span class="sxs-lookup"><span data-stu-id="1d204-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="1d204-147">2. Habilitar realidade virtual</span><span class="sxs-lookup"><span data-stu-id="1d204-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="1d204-148">Habilitar a realidade virtual também se aplica aos headsets de realidade misturada e realidade aumentada, pois se refere à habilitação da visão estereoscópica, ou seja, renderização de imagens diferentes para cada olho.</span><span class="sxs-lookup"><span data-stu-id="1d204-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="1d204-149">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:</span><span class="sxs-lookup"><span data-stu-id="1d204-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="1d204-151">Na janela Configurações de Projeto, selecione **Player** > **Configurações de XR** para expandir as Configurações de XR:</span><span class="sxs-lookup"><span data-stu-id="1d204-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="1d204-153">Nas Configurações de XR, marque a caixa de seleção **Realidade Virtual Compatível** para habilitar a realidade virtual e, em seguida, clique no ícone **+** e selecione **Windows Mixed Reality** para adicionar o SDK do Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="1d204-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="1d204-155">Aguarde até que o Unity termine de adicionar o SDK:</span><span class="sxs-lookup"><span data-stu-id="1d204-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="1d204-157">Quando o Unity terminar de adicionar o SDK, otimize as Configurações de XR da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1d204-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="1d204-158">Defina o **Formato de Profundidade** do Windows Mixed Reality como **Profundidade de 16 bits**</span><span class="sxs-lookup"><span data-stu-id="1d204-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="1d204-159">Marque a caixa de seleção **Habilitar Compartilhamento de Profundidade** do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1d204-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="1d204-160">Defina o **Modo de Renderização\*** de Estéreo como **Instância de Passagem Única**</span><span class="sxs-lookup"><span data-stu-id="1d204-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="1d204-162">Para saber mais sobre a otimização do Unity para o Windows Mixed Reality, consulte a documentação [Configurações recomendadas para o Unity](recommended-settings-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="1d204-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="1d204-163">3. Habilitar percepção espacial</span><span class="sxs-lookup"><span data-stu-id="1d204-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="1d204-164">A percepção espacial permite a visualização da malha de mapeamento espacial em dispositivos com Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1d204-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="1d204-165">Na janela Configurações de Projeto, selecione **Player** > **Configurações de Publicação** para expandir as Configurações de Publicação:</span><span class="sxs-lookup"><span data-stu-id="1d204-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="1d204-167">Nas Configurações de Publicação, role para baixo até a seção **Recursos** e marque a caixa de seleção **SpatialPerception**:</span><span class="sxs-lookup"><span data-stu-id="1d204-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="1d204-169">Feche a janela Configurações do Projeto.</span><span class="sxs-lookup"><span data-stu-id="1d204-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="1d204-170">Importar recursos do TextMesh Pro Essential</span><span class="sxs-lookup"><span data-stu-id="1d204-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="1d204-171">Estamos importando este pacote porque ele é necessário para elementos da interface do usuário do Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="1d204-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="1d204-172">No menu do Unity, selecione **Janela** > **TextMeshPro** > **Importar recursos essenciais do TMP**:</span><span class="sxs-lookup"><span data-stu-id="1d204-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="1d204-174">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="1d204-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="1d204-176">Importe o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="1d204-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="1d204-177">Baixe o pacote personalizado do Unity:</span><span class="sxs-lookup"><span data-stu-id="1d204-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="1d204-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="1d204-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

<span data-ttu-id="1d204-179">No menu do Unity, selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:</span><span class="sxs-lookup"><span data-stu-id="1d204-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="1d204-181">Na janela Importar pacote..., selecione o **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** que você baixou e clique no botão **Abrir**:</span><span class="sxs-lookup"><span data-stu-id="1d204-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="1d204-183">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="1d204-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="1d204-185">Configurar o projeto do Unity para o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="1d204-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="1d204-186">Depois que o pacote tiver sido importado, a janela Configurador de Projeto do MRTK deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="1d204-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="1d204-187">Se não aparecer, abra a janela selecionando **Kit de Ferramentas de Realidade Misturada** > **Utilidades** > **Configurar Projeto do Unity** no menu do Unity.</span><span class="sxs-lookup"><span data-stu-id="1d204-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="1d204-189">Na janela Configurador de Projeto do MRTK, expanda a seção **Modificar Configurações**, <u>desmarque</u> a caixa de seleção **Habilitar MSBuild para Unity**, verifique se todas as outras opções estão marcadas e clique no botão **Aplicar** para aplicar as configurações:</span><span class="sxs-lookup"><span data-stu-id="1d204-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="1d204-191">O MSBuild para Unity pode não ser compatível com todos os SDKs que você usará e pode ser complicado desabilitá-lo depois que ele tiver sido habilitado.</span><span class="sxs-lookup"><span data-stu-id="1d204-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="1d204-192">Consequentemente, é altamente recomendável não habilitar o MSBuild para o Unity.</span><span class="sxs-lookup"><span data-stu-id="1d204-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="1d204-193">Configure o Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="1d204-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="1d204-194">No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Adicionar à Cena e Configurar...** para adicionar o Kit de Ferramentas de Realidade Misturada à cena atual:</span><span class="sxs-lookup"><span data-stu-id="1d204-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="1d204-196">Com o objeto MixedRealityToolkit selecionado na janela Hierarquia, na janela Inspetor, verifique se o perfil de configuração do Kit de Ferramentas de Realidade Misturada está definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="1d204-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, verify the Mixed Reality Toolkit configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> <span data-ttu-id="1d204-198">Normalmente, você usará o DefaultHoloLens2ConfigurationProfile ao desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d204-198">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens 2.</span></span> <span data-ttu-id="1d204-199">No entanto, para fins deste tutorial, você usará o DefaultMixedRealityToolkitConfigurationProfile. Depois, no próximo tutorial, [Como criar a interface do usuário e configurar o Kit de Ferramentas de Realidade Misturada](mrlearning-base-ch2.md), altere para o DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="1d204-199">However, for the purpose of this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="1d204-200">No menu do Unity, selecione **Arquivo** > **Salvar Como...** para abrir a janela Salvar Cena:</span><span class="sxs-lookup"><span data-stu-id="1d204-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="1d204-202">Na janela Salvar cena, navegue até a pasta **Cenas** do seu projeto, dê um nome adequado à sua cena (por exemplo, _Introdução_) e clique no botão **Salvar** para salvar a cena:</span><span class="sxs-lookup"><span data-stu-id="1d204-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="1d204-204">Crie o aplicativo para seu dispositivo</span><span class="sxs-lookup"><span data-stu-id="1d204-204">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="1d204-205">1. Compilar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="1d204-205">1. Build the Unity project</span></span>

<span data-ttu-id="1d204-206">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="1d204-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="1d204-207">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar sua cena atual à lista **Cenas no Build** e clique no botão **Build** para abrir a janela Compilar Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="1d204-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="1d204-209">Na janela Compilar Plataforma Universal do Windows, escolha um local adequado para armazenar seu build, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma nova pasta e dê a ela um nome adequado, por exemplo, _GettingStarted_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="1d204-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="1d204-211">Aguarde até que o Unity conclua o processo de build:</span><span class="sxs-lookup"><span data-stu-id="1d204-211">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="1d204-213">2. Compilar e implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="1d204-213">2. Build and deploy the application</span></span>

<span data-ttu-id="1d204-214">Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra o local em que você armazenou o build.</span><span class="sxs-lookup"><span data-stu-id="1d204-214">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="1d204-215">Navegue dentro da pasta e clique duas vezes no arquivo da solução para abri-lo no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="1d204-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="1d204-217">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar que todos os componentes necessários estejam instalados conforme especificado na documentação [Instalar as Ferramentas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1d204-217">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="1d204-218">Configure o Visual Studio para o HoloLens 2 selecionando a configuração **Mestre** ou **Versão**, a arquitetura **ARM** e o **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="1d204-218">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

> [!NOTE]
> <span data-ttu-id="1d204-220">Se você não vir o dispositivo como uma opção, talvez seja necessário alterar o projeto de inicialização padrão do projeto IC2Lpp para seu Projeto UWP.</span><span class="sxs-lookup"><span data-stu-id="1d204-220">If you don't see Device as an option you may need to change the default start up project from the IC2Lpp project to your UWP Project.</span></span> <span data-ttu-id="1d204-221">No **Gerenciador de Soluções**, clique com o botão direito do mouse em **nomedoseuprojeto (Windows Universal)** e selecione **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="1d204-221">In the **Solution Explorer**, right click on **yourprojectname (Universal Windows)** and select **Set as StartUp Project**.</span></span> 

<span data-ttu-id="1d204-222">Conecte o HoloLens 2 ao seu computador.</span><span class="sxs-lookup"><span data-stu-id="1d204-222">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d204-223">Antes de compilar no dispositivo, ele precisa estar no Modo de Desenvolvedor e emparelhado com o computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1d204-223">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="1d204-224">Essas duas etapas podem ser concluídas seguindo [estas instruções](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1d204-224">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="1d204-225">A etapa final é compilar e implantar no dispositivo selecionando **Depurar** > **Iniciar Sem Depuração**:</span><span class="sxs-lookup"><span data-stu-id="1d204-225">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="1d204-227">Embora essas instruções pressuponham que você esteja implantando em um dispositivo HoloLens 2, você também pode implantar no [emulador do HoloLens 2](using-the-hololens-emulator.md) ou criar um [pacote do aplicativo para sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="1d204-227">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="1d204-228">A seleção de Iniciar sem Depuração faz com que o aplicativo seja iniciado imediatamente no dispositivo após um build bem-sucedido, mas sem o depurador anexado e sem exibir as informações no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d204-228">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="1d204-229">Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d204-229">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="1d204-230">Para implantar em seu dispositivo sem iniciar o aplicativo automaticamente, selecione Build > Implantar Solução.</span><span class="sxs-lookup"><span data-stu-id="1d204-230">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="1d204-231">Parabéns</span><span class="sxs-lookup"><span data-stu-id="1d204-231">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="1d204-232">Você acabou de implantar seu primeiro aplicativo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d204-232">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="1d204-233">Enquanto caminha, você deverá ver uma malha de mapeamento espacial cobrindo todas as superfícies que foram percebidas pelo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d204-233">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="1d204-234">Além disso, você deverá ver indicadores em suas mãos e seus dedos para o acompanhamento da mão e um contador da taxa de quadros para monitorar o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d204-234">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="1d204-235">Essas são apenas algumas das partes fundamentais predefinidas no Kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="1d204-235">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="1d204-236">Nos próximos tutoriais, você começará a adicionar mais conteúdo e interatividade à cena, de modo a explorar totalmente as funcionalidades do HoloLens 2 e do Kit de Ferramentas de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="1d204-236">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="1d204-237">No aplicativo, note o criador de perfil de Diagnóstico; você pode alternar sua visibilidade usando o comando de fala **Alternar Diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="1d204-237">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="1d204-238">No entanto, geralmente é recomendável manter o criador de perfil visível o tempo todo durante o desenvolvimento para entender quando as alterações no aplicativo podem impactar o desempenho, por exemplo, o aplicativo HoloLens 2 deve [ser executado continuamente a 60 FPS](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="1d204-238">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="1d204-239">Próximo tutorial: 3. Criar a interface do usuário e configurar o Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="1d204-239">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)

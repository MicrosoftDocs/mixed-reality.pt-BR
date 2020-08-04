---
title: Tutoriais de Âncoras Espaciais do Azure – 5. Âncoras Espaciais do Azure para o Android e o iOS
description: Conclua este curso para aprender a implantar um projeto do Unity com o Kit de Ferramentas de Realidade Misturada e Âncoras Espaciais do Azure para Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, android, ios
ms.localizationpriority: high
ms.openlocfilehash: 8c63204948b3e4aa3d25e5b2ca948798726f0838
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376538"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="dae7d-105">5. Âncoras Espaciais do Azure para o Android e o iOS</span><span class="sxs-lookup"><span data-stu-id="dae7d-105">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="dae7d-106">Neste tutorial, você aprenderá a criar seu projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="dae7d-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="dae7d-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="dae7d-107">Objectives</span></span>

* <span data-ttu-id="dae7d-108">Saiba como criar o projeto para seu dispositivo Android usando o Plug-in ARCore XR e o AR Foundation do Unity</span><span class="sxs-lookup"><span data-stu-id="dae7d-108">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="dae7d-109">Saiba como criar o projeto para seu dispositivo iOS usando o Plug-in ARKit XR e o AR Foundation do Unity</span><span class="sxs-lookup"><span data-stu-id="dae7d-109">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="dae7d-110">Instalar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="dae7d-110">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="dae7d-111">Nesta seção, você atualizará e instalará os seguintes pacotes embutidos:</span><span class="sxs-lookup"><span data-stu-id="dae7d-111">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="dae7d-112">AR Foundation 3.1.3</span><span class="sxs-lookup"><span data-stu-id="dae7d-112">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="dae7d-113">Auxiliares de entrada herdados 2.1.4</span><span class="sxs-lookup"><span data-stu-id="dae7d-113">Legacy Input Helpers 2.1.4</span></span>
* <span data-ttu-id="dae7d-114">Plug-in ARCore XR 3.1.3 para suporte ao Android</span><span class="sxs-lookup"><span data-stu-id="dae7d-114">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="dae7d-115">Plug-in ARKit XR 3.1.3 para suporte a iOS</span><span class="sxs-lookup"><span data-stu-id="dae7d-115">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="dae7d-116">Nem todas as versões são compatíveis com o MRTK e apenas determinadas versões funcionam em conjunto, portanto, instale as versões exatas listadas acima.</span><span class="sxs-lookup"><span data-stu-id="dae7d-116">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="dae7d-117">No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes** para abrir a janela Gerenciador de Pacotes e selecione **AR Foundation** > **3.1.3** e clique no botão **Atualizar para 3.1.3** para atualizar o pacote:</span><span class="sxs-lookup"><span data-stu-id="dae7d-117">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="dae7d-119">Siga o mesmo processo para importar os pacotes restantes, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="dae7d-119">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="dae7d-120">Se você estiver desenvolvendo esse projeto para Android, não será necessário instalar o pacote Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="dae7d-120">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="dae7d-121">Da mesma forma, se você estiver desenvolvendo esse projeto para iOS, não será necessário instalar o Plug-in ARCore XR.</span><span class="sxs-lookup"><span data-stu-id="dae7d-121">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="dae7d-122">Configurar o MRTK para a Câmera do AR Foundation</span><span class="sxs-lookup"><span data-stu-id="dae7d-122">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="dae7d-123">Nesta seção, você aprenderá a configurar o MRTK para implantação em um dispositivo móvel.</span><span class="sxs-lookup"><span data-stu-id="dae7d-123">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="dae7d-124">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="dae7d-124">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="dae7d-125">Em seguida, na janela Inspetor, selecione a guia **Câmera**, clone o perfil da câmera e dê a ele um nome adequado, por exemplo, **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="dae7d-125">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="dae7d-127">Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do Kit de Ferramentas de Realidade Misturada](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="dae7d-127">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="dae7d-128">Com a guia **Câmera** ainda selecionada na janela Inspetor, expanda os **Provedores de Configuração da Câmera** e clique no botão **+ Adicionar Provedor de Configuração de Câmera** e, em seguida, expanda o **Novo provedor de dados 1** adicionado recentemente:</span><span class="sxs-lookup"><span data-stu-id="dae7d-128">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="dae7d-130">Usando a lista suspensa **Tipo**, altere o tipo para **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="dae7d-130">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="dae7d-132">Com o objeto **MixedRealityToolkit** ainda selecionado na janela Hierarquia, use o botão **Adicionar Componente** na janela Inspetor para adicionar os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="dae7d-132">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="dae7d-133">AR Anchor Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="dae7d-133">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="dae7d-134">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="dae7d-134">DisableDiagnosticsSystem (Script)</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="dae7d-136">Quando você adiciona o componente AR Reference Point Manager (Script), o componente AR Session Origin (Script) é adicionado automaticamente, pois é exigido pelo componente AR Reference Point Manager (Script).</span><span class="sxs-lookup"><span data-stu-id="dae7d-136">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="dae7d-137">Compilar o aplicativo para seu dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="dae7d-137">Building your application to your Android device</span></span>

<span data-ttu-id="dae7d-138">Nesta seção, você aprenderá a configurar seu projeto para compilá-lo e implantá-lo em um dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="dae7d-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="dae7d-139">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build e, em seguida, alterne a plataforma para Android:</span><span class="sxs-lookup"><span data-stu-id="dae7d-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="dae7d-141">Para lembrar como mudar a plataforma de build, consulte as instruções em [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="dae7d-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="dae7d-142">Feche a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="dae7d-142">Close the Build Settings window.</span></span>

<span data-ttu-id="dae7d-143">No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity** para abrir a janela do **Configurador de Projeto do MRTK**, confirme se todas as opções estão selecionadas e clique no botão **Aplicar** para aplicar as configurações:</span><span class="sxs-lookup"><span data-stu-id="dae7d-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="dae7d-145">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Outras Configurações**, selecione **Vulkan** e remova-o clicando no símbolo de **"-"** :</span><span class="sxs-lookup"><span data-stu-id="dae7d-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="dae7d-147">Feche a janela Configurações do Player e abra a janela Configurações de Build novamente.</span><span class="sxs-lookup"><span data-stu-id="dae7d-147">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="dae7d-148">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**.</span><span class="sxs-lookup"><span data-stu-id="dae7d-148">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="dae7d-149">Em seguida, use um cabo USB, conecte seu dispositivo Android ao seu computador e selecione-o na lista suspensa **Executar Dispositivo**:</span><span class="sxs-lookup"><span data-stu-id="dae7d-149">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="dae7d-151">Se o dispositivo não aparecer na lista suspensa Executar Dispositivo, pode ser necessário pressionar o botão Atualizar ao lado do menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="dae7d-151">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="dae7d-152">Na janela Configurações de Build, clique no botão **Compilar e Executar** para abrir a janela Compilar Android.</span><span class="sxs-lookup"><span data-stu-id="dae7d-152">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="dae7d-153">Escolha um local adequado para armazenar o build, por exemplo, _D:\MixedRealityLearning\Builds_ e dê ao APK um nome adequado, por exemplo, _MRTKTutorials-AzureSpatialAnchors_ e clique no botão **Salvar** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="dae7d-153">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="dae7d-155">Se você receber algum erro na janela do Console do Unity relacionado aos módulos SDK, NDK ou JDK do Android, será necessário abrir o Hub do Unity e instalar os módulos de Suporte de Build do Android associados.</span><span class="sxs-lookup"><span data-stu-id="dae7d-155">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="dae7d-156">Quando o processo de build for concluído, os aplicativos deverão ser carregados automaticamente em seu dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="dae7d-156">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="dae7d-157">Compilar o aplicativo para seu dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="dae7d-157">Building your application to your iOS device</span></span>

<span data-ttu-id="dae7d-158">Nesta seção, você aprenderá a configurar seu projeto para compilá-lo e implantá-lo em seu dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="dae7d-158">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="dae7d-159">No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build e alterne a plataforma para iOS:</span><span class="sxs-lookup"><span data-stu-id="dae7d-159">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="dae7d-161">Para lembrar como mudar a plataforma de build, consulte as instruções em [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="dae7d-161">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="dae7d-162">Feche a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="dae7d-162">Close the Build Settings window.</span></span>

<span data-ttu-id="dae7d-163">No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity** para abrir a janela do **Configurador de Projeto do MRTK**, confirme se todas as opções estão selecionadas e clique no botão **Aplicar** para aplicar as configurações:</span><span class="sxs-lookup"><span data-stu-id="dae7d-163">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="dae7d-165">No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Outras Configurações**, desmarque a caixa de seleção **Remover Código do Mecanismo** para desabilitá-la:</span><span class="sxs-lookup"><span data-stu-id="dae7d-165">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="dae7d-167">Feche a janela Configurações do Player e abra a janela **Configurações de Build** novamente.</span><span class="sxs-lookup"><span data-stu-id="dae7d-167">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="dae7d-168">Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**:</span><span class="sxs-lookup"><span data-stu-id="dae7d-168">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="dae7d-170">Na janela Configurações de Build, clique no botão **Compilar** para abrir a janela Compilar iOS.</span><span class="sxs-lookup"><span data-stu-id="dae7d-170">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="dae7d-171">Escolha um local adequado para armazenar o projeto do Xcode, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma pasta e dê a ela um nome adequado, por exemplo, _MRTKTutorials-AzureSpatialAnchors_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="dae7d-171">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="dae7d-173">Quando o processo de build for concluído, siga as instruções de [Exportar o projeto do Xcode](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implantar o projeto do Xcode em seu dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="dae7d-173">When the build process is complete, follow the [Export the Xcode project](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="dae7d-174">Parabéns</span><span class="sxs-lookup"><span data-stu-id="dae7d-174">Congratulations</span></span>

<span data-ttu-id="dae7d-175">Neste tutorial, você aprendeu a criar o projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="dae7d-175">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

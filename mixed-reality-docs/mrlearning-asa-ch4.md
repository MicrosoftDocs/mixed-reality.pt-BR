---
title: Tutoriais de Âncoras Espaciais do Azure – 4. Âncoras Espaciais do Azure para o Android e o iOS
description: Conclua este tutorial para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, curso, hololens, azure, âncoras espaciais
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867618"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="9be07-105">4. Âncoras Espaciais do Azure para o Android e o iOS</span><span class="sxs-lookup"><span data-stu-id="9be07-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="9be07-106">Neste tutorial, você aprenderá a criar seu projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="9be07-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="9be07-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9be07-107">Objectives</span></span>

* <span data-ttu-id="9be07-108">Saiba como criar seu projeto para o dispositivos Android usando o Unity AR Foundation e o Plug-in ARCore XR.</span><span class="sxs-lookup"><span data-stu-id="9be07-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="9be07-109">Saiba como criar seu projeto para dispositivos iOS usando o Unity AR Foundation e o Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="9be07-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

[!NOTE] <span data-ttu-id="9be07-110">Antes deste tutorial, recomendamos que você conclua os Tutoriais de Âncoras Espaciais do Azure -> [Introdução às Âncoras Espaciais do Azure](mrlearning-asa-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="9be07-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="9be07-111">Como adicionar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="9be07-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="9be07-112">Nesta seção, você instalará os pacotes do AR Foundation interno do Unity, do Plug-in ARCore XR e do Plug-in ARKit XR necessários para dar suporte a dispositivos Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="9be07-112">In this section, you will install Unity's inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="9be07-113">Certifique-se de instalar a versão correta dos pacotes do Unity, conforme listado abaixo:</span><span class="sxs-lookup"><span data-stu-id="9be07-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="9be07-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="9be07-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="9be07-115">**Plug-in ARCore XR 2.2.0 versão prévia 2**</span><span class="sxs-lookup"><span data-stu-id="9be07-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="9be07-116">**Plug-in ARKit XR 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="9be07-116">**ARKit XR plugin 2.1.1**</span></span>

[!NOTE] <span data-ttu-id="9be07-117">Se você estiver desenvolvendo esse projeto para Android, não será necessário instalar o pacote Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="9be07-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="9be07-118">Da mesma forma, se você estiver desenvolvendo esse projeto para iOS, não será necessário instalar o Plug-in ARCore XR.</span><span class="sxs-lookup"><span data-stu-id="9be07-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="9be07-119">No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes**:</span><span class="sxs-lookup"><span data-stu-id="9be07-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="9be07-121">Pode demorar alguns segundos até que todos os pacotes apareçam na lista.</span><span class="sxs-lookup"><span data-stu-id="9be07-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="9be07-122">Para exibir pacotes em versão prévia, clique na opção Avançado e selecione "**Mostrar pacotes em versão prévia**".</span><span class="sxs-lookup"><span data-stu-id="9be07-122">Display preview packages by clicking on Advanced option and select "**Show preview packages.**"</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="9be07-124">Na janela Gerenciador de Pacotes, selecione **AR Foundation**. Entre as muitas versões, você deverá selecionar a versão 2.1.4 e atualizar o pacote clicando no botão **Atualizar para 2.1.4**:</span><span class="sxs-lookup"><span data-stu-id="9be07-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select version 2.1.4 and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="9be07-126">Para dar suporte a dispositivos Android, siga o mesmo processo para importar o Plug-in ARCore XR 2.2.0 versão prévia 2.</span><span class="sxs-lookup"><span data-stu-id="9be07-126">To support Android devices, follow the same process to import ARCore XR Plugin 2.2.0 preview 2.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="9be07-128">Para dar suporte a dispositivos iOS, você deve importar o pacote **Plugin ARKit XR 2.1.1** do Unity no Gerenciador de Pacotes.</span><span class="sxs-lookup"><span data-stu-id="9be07-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="9be07-130">Personalizar o MRTK para dar suporte à câmera do AR Foundation</span><span class="sxs-lookup"><span data-stu-id="9be07-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="9be07-131">Personalize as configurações de MRTK para dar suporte ao AR Foundation selecionando o MixedRealityToolKit na janela Hierarquia e clique no botão **Clonar** no Kit de Ferramentas de Realidade Misturada na janela Inspetor.</span><span class="sxs-lookup"><span data-stu-id="9be07-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="9be07-133">Ao clicar no botão **clone**, uma nova janela Clonar Perfil será exibida, clique então novamente no botão Clonar para clonar o DefaultMixedRealityToolkitProfile.</span><span class="sxs-lookup"><span data-stu-id="9be07-133">When you click the **Clone** button, a new Clone Profile window will appear, click on the Clone button again to clone the DefaultMixedRealityToolkitProfile.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="9be07-135">Da mesma forma, clone o perfil da câmera na janela do Inspetor e renomeie o perfil para "UnityARConfigurationProfile" e clique no botão **Clonar**.</span><span class="sxs-lookup"><span data-stu-id="9be07-135">Similarly, clone the camera profile in the Inspector window and rename the profile to “UnityARConfigurationProfile” and click on the **Clone** button.</span></span> <span data-ttu-id="9be07-136">Na janela Inspetor, localize o MixedReality, selecione a guia Câmera. Expanda os provedores de configuração de câmera na janela Inspetor e clique em **+ Adicionar Provedor de Configuração de Câmera** > expandir **Novo provedor de dados 1** > selecionar Tipo **Nenhum** > selecionar **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > selecionar **UnityARCameraSettings**.</span><span class="sxs-lookup"><span data-stu-id="9be07-136">In the Inspector window, locate the MixedReality, select the Camera tab Expand the camera setting providers in the inspector window and click on **+Add Camera Setting Provider** > expand **New data provider 1**> select Type **None** >select **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** > Select **UnityARCameraSettings**.</span></span>


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="9be07-138">Com o objeto MixedRealityToolKit selecionado na janela Hierarquia, anexe os scripts de suporte à janela Inspetor ao clicar no botão **Adicionar componente**, digite AR reference Point manager e selecione o script.</span><span class="sxs-lookup"><span data-stu-id="9be07-138">With the MixedRealityToolKit object selected in the Hierarchy window, in the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="9be07-139">Adicionar o script "AR Reference Point Manager" adicionará junto "AR session origin" automaticamente na janela Inspetor.</span><span class="sxs-lookup"><span data-stu-id="9be07-139">Adding the  "AR Reference Point Manager" script will automatically add "AR session origin" along with it in the Inspector window.</span></span> <span data-ttu-id="9be07-140">Depois de adicionar os scripts de suporte, a janela Inspetor deverá ficar com esta aparência.</span><span class="sxs-lookup"><span data-stu-id="9be07-140">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a><span data-ttu-id="9be07-142">Compilar aplicativo para dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="9be07-142">Build application to Android device</span></span>

<span data-ttu-id="9be07-143">Para compilar esse aplicativo para seu dispositivo Android, clique em **Arquivo** na parte superior da janela e selecione **Configurações de Build.**</span><span class="sxs-lookup"><span data-stu-id="9be07-143">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="9be07-144">Uma nova janela aparecerá na tela, selecione **Android** e clique em **Alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="9be07-144">A new window will appear on the screen, select **Android,** and click on the **Switch Platform**.</span></span> <span data-ttu-id="9be07-145">Levará alguns minutos para mudar de plataforma.</span><span class="sxs-lookup"><span data-stu-id="9be07-145">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="9be07-146">Depois de alternar para a plataforma Android, clique em **Adicionar Cenas Abertas** e verifique se a cena atual é a única cena selecionada na lista de **Cenas em Build**.</span><span class="sxs-lookup"><span data-stu-id="9be07-146">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="9be07-148">Feche a janela de **Configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="9be07-148">Close the **Build Settings** window.</span></span> <span data-ttu-id="9be07-149">No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar o Projeto do Unity** e clique em **Aplicar** para configurar o projeto do Unity para a plataforma Android.</span><span class="sxs-lookup"><span data-stu-id="9be07-149">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="9be07-151">No menu do Unity, selecione **Editar** > **Configurações de Projeto** para abrir a janela Configurações de Projeto.</span><span class="sxs-lookup"><span data-stu-id="9be07-151">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="9be07-152">Na janela Configurações do Projeto, selecione a guia **Player**, expanda a seção Outras Configurações, selecione **Vulkan** e remova-o clicando no símbolo "-".</span><span class="sxs-lookup"><span data-stu-id="9be07-152">In the Project Settings, window selects the **Player** tab, expand the Other Settings section, select **Vulkan,** and remove it by clicking the "-" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="9be07-154">Feche a janela Configurações do Player e abra a janela Configurações de Build novamente.</span><span class="sxs-lookup"><span data-stu-id="9be07-154">Close the Player Settings window and open the Build Settings window again.</span></span> <span data-ttu-id="9be07-155">Em seguida, usando um cabo USB, conecte seu dispositivo Android ao seu computador e selecione o dispositivo no **Compilar e executar no** menu suspenso e, em seguida, clique em **Compilar e executar**.</span><span class="sxs-lookup"><span data-stu-id="9be07-155">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run on** the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="9be07-156">Você será solicitado a salvar um arquivo .apk, para o qual pode escolher qualquer nome.</span><span class="sxs-lookup"><span data-stu-id="9be07-156">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="9be07-158">Se você receber algum erro na janela do Console do Unity relacionado aos módulos SDK, NDK e/ou JDK do Android, será necessário abrir o Hub do Unity e instalar os módulos SDK, NDK e JDK associados para o módulo de Suporte de Build do Android.</span><span class="sxs-lookup"><span data-stu-id="9be07-158">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="9be07-159">Quando o processo de compilação for concluído, seus aplicativos deverão ser carregados automaticamente em seu dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="9be07-159">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-application-to-ios-device"></a><span data-ttu-id="9be07-160">Compilar aplicativo para dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="9be07-160">Build application to iOS Device</span></span>

<span data-ttu-id="9be07-161">Para compilar esse aplicativo para seu dispositivo iOS, clique em **Arquivo** na parte superior da janela e selecione **Configurações de compilação.**</span><span class="sxs-lookup"><span data-stu-id="9be07-161">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="9be07-162">Uma nova janela aparecerá na tela, selecione então **iOS** e clique em **Alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="9be07-162">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="9be07-164">Feche a janela de **Configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="9be07-164">Close the **Build Settings** window.</span></span> <span data-ttu-id="9be07-165">No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar o Projeto do Unity** e clique em **Aplicar** para configurar o projeto do Unity para a plataforma iOS.</span><span class="sxs-lookup"><span data-stu-id="9be07-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="9be07-167">Para compilar o projeto do XCode do iOS, vá para Configurações de compilação e clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="9be07-167">To build the iOS XCode project, go to Build Settings and, click on **Build**.</span></span>

<span data-ttu-id="9be07-168">Siga [este guia](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implantar esse projeto em seu dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="9be07-168">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9be07-169">Parabéns</span><span class="sxs-lookup"><span data-stu-id="9be07-169">Congratulations</span></span>

<span data-ttu-id="9be07-170">Neste tutorial, você aprendeu a compilar seu projeto para dispositivos Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="9be07-170">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="9be07-171">Você também aprendeu a usar o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR para fazer seu projeto funcionar em dispositivos Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="9be07-171">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>
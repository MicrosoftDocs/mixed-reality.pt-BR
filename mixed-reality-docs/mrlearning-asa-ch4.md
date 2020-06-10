---
title: Tutoriais de Âncoras Espaciais do Azure – 4. Âncoras Espaciais do Azure para o Android e o iOS
description: Conclua este tutorial para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, curso, hololens, azure, âncoras espaciais
ms.localizationpriority: high
ms.openlocfilehash: 78fa6a2cdd29bd424ec3016a5467760063b87a14
ms.sourcegitcommit: 7011ac6fde80e5c45f04192fa1db6e1eb559e3b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84327916"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="b9641-105">4. Âncoras Espaciais do Azure para o Android e o iOS</span><span class="sxs-lookup"><span data-stu-id="b9641-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="b9641-106">Neste tutorial, você aprenderá a criar seu projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="b9641-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="b9641-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b9641-107">Objectives</span></span>

* <span data-ttu-id="b9641-108">Saiba como criar seu projeto para o dispositivos Android usando o Unity AR Foundation e o Plug-in ARCore XR.</span><span class="sxs-lookup"><span data-stu-id="b9641-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="b9641-109">Saiba como criar seu projeto para dispositivos iOS usando o Unity AR Foundation e o Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="b9641-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

> [!NOTE]
> <span data-ttu-id="b9641-110">Antes deste tutorial, recomendamos que você conclua os Tutoriais de Âncoras Espaciais do Azure -> [Introdução às Âncoras Espaciais do Azure](mrlearning-asa-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="b9641-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="b9641-111">Como adicionar pacotes internos do Unity</span><span class="sxs-lookup"><span data-stu-id="b9641-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="b9641-112">Nesta seção, você instalará os pacotes do AR Foundation interno do Unity, do Plug-in ARCore XR e do Plug-in ARKit XR necessários para compatibilidade com dispositivos Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="b9641-112">In this section, you will install Unity inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="b9641-113">Certifique-se de instalar a versão correta dos pacotes do Unity, conforme listado abaixo:</span><span class="sxs-lookup"><span data-stu-id="b9641-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="b9641-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="b9641-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="b9641-115">**Plug-in ARCore XR 2.2.0 versão prévia 2**</span><span class="sxs-lookup"><span data-stu-id="b9641-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="b9641-116">**Plug-in ARKit XR 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="b9641-116">**ARKit XR plugin 2.1.1**</span></span>

> [!NOTE]
> <span data-ttu-id="b9641-117">Se você estiver desenvolvendo esse projeto para Android, não será necessário instalar o pacote Plug-in ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="b9641-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="b9641-118">Da mesma forma, se você estiver desenvolvendo esse projeto para iOS, não será necessário instalar o Plug-in ARCore XR.</span><span class="sxs-lookup"><span data-stu-id="b9641-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="b9641-119">No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes**:</span><span class="sxs-lookup"><span data-stu-id="b9641-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="b9641-121">Pode demorar alguns segundos até que todos os pacotes apareçam na lista.</span><span class="sxs-lookup"><span data-stu-id="b9641-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="b9641-122">Para exibir pacotes em versão prévia, clique na opção Avançado e selecione **Mostrar pacotes em versão prévia**.</span><span class="sxs-lookup"><span data-stu-id="b9641-122">Display preview packages by clicking on Advanced option and select **Show preview packages.**</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="b9641-124">Na janela Gerenciador de Pacotes, selecione **AR Foundation**. Entre as muitas versões, você deverá selecionar a **versão 2.1.4** e atualizar o pacote clicando no botão **Atualizar para 2.1.4**:</span><span class="sxs-lookup"><span data-stu-id="b9641-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select **version 2.1.4** and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="b9641-126">Para compatibilidade com dispositivos Android, siga o mesmo processo para importar o **Plug-in ARCore XR 2.2.0 versão prévia 2**.</span><span class="sxs-lookup"><span data-stu-id="b9641-126">To support Android devices, follow the same process to import **ARCore XR Plugin 2.2.0 preview 2**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="b9641-128">Para dar suporte a dispositivos iOS, você deve importar o pacote **Plugin ARKit XR 2.1.1** do Unity no Gerenciador de Pacotes.</span><span class="sxs-lookup"><span data-stu-id="b9641-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="b9641-130">Personalizar o MRTK para dar suporte à câmera do AR Foundation</span><span class="sxs-lookup"><span data-stu-id="b9641-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="b9641-131">Personalize as configurações de MRTK para dar suporte ao AR Foundation selecionando o MixedRealityToolKit na janela Hierarquia e clique no botão **Clonar** no Kit de Ferramentas de Realidade Misturada na janela Inspetor.</span><span class="sxs-lookup"><span data-stu-id="b9641-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="b9641-133">Ao clicar no botão **Clonar**, uma nova janela Clonar Perfil será exibida, clique então novamente no botão **Clonar** para clonar o **DefaultMixedRealityToolkitProfile**.</span><span class="sxs-lookup"><span data-stu-id="b9641-133">When you click the **Clone** button, a new clone Profile window will appear, click on the **Clone** button again to clone the **DefaultMixedRealityToolkitProfile**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="b9641-135">De maneira similar, clone o **Perfil da Câmera** na janela do Inspetor.</span><span class="sxs-lookup"><span data-stu-id="b9641-135">Similarly, clone the **Camera Profile** in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="b9641-137">Na janela Inspetor, localize o MixedReality e selecione a guia **Câmera**. Expanda os provedores de configuração de câmera na janela Inspetor e clique em **+ Adicionar Provedor de Configuração de Câmera** > expanda **Novo provedor de dados 1** > selecione o tipo **Nenhum** > selecione **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > selecione **UnityARCameraSettings**.</span><span class="sxs-lookup"><span data-stu-id="b9641-137">In the Inspector window, locate the MixedReality, select the **Camera** tab. Expand the camera setting providers in the inspector window and click on **+ Add Camera Setting Provider** > expand **New data provider 1** > select type **None** > select **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > select **UnityARCameraSettings**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

<span data-ttu-id="b9641-139">Com o objeto MixedRealityToolKit selecionado na janela Hierarquia, anexe os scripts de suporte na janela Inspetor clicando no botão **Adicionar componente**, digite "AR Reference Point Manager" e selecione o script.</span><span class="sxs-lookup"><span data-stu-id="b9641-139">With the MixedRealityToolKit object selected in the Hierarchy window, In the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="b9641-140">Adicionar o script **AR Reference Point Manager** adicionará **AR session origin** automaticamente à janela Inspetor.</span><span class="sxs-lookup"><span data-stu-id="b9641-140">Adding the  **AR Reference Point Manager** script will automatically add **AR session origin** to the Inspector window.</span></span> <span data-ttu-id="b9641-141">Depois de adicionar os scripts de suporte, a janela Inspetor deverá ficar com esta aparência.</span><span class="sxs-lookup"><span data-stu-id="b9641-141">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-5.png)

## <a name="build-an-application-to-an-android-device"></a><span data-ttu-id="b9641-143">Compilar um aplicativo para um dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="b9641-143">Build an application to an Android device</span></span>

<span data-ttu-id="b9641-144">Para compilar esse aplicativo para seu dispositivo Android, clique em **Arquivo** na parte superior da janela e selecione **Configurações de Build.**</span><span class="sxs-lookup"><span data-stu-id="b9641-144">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="b9641-145">Uma nova janela aparecerá na tela. Selecione **Android** e clique em **Alternar Plataforma**.</span><span class="sxs-lookup"><span data-stu-id="b9641-145">A new window will appear on the screen, select **Android**, and click on the **Switch Platform**.</span></span> <span data-ttu-id="b9641-146">Levará alguns minutos para mudar de plataforma.</span><span class="sxs-lookup"><span data-stu-id="b9641-146">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="b9641-147">Depois de alternar para a plataforma Android, clique em **Adicionar Cenas Abertas** e verifique se a cena atual é a única cena selecionada na lista de **Cenas em Build**.</span><span class="sxs-lookup"><span data-stu-id="b9641-147">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="b9641-149">Feche a janela de **Configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="b9641-149">Close the **Build Settings** window.</span></span> <span data-ttu-id="b9641-150">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > Configurar o Projeto do Unity e clique em **Aplicar** para configurar o projeto do Unity para a plataforma Android.</span><span class="sxs-lookup"><span data-stu-id="b9641-150">In the Unity menu, select Mixed Reality Toolkit > Utilities > Configure Unity Project and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="b9641-152">No menu do Unity, selecione **Editar** > **Configurações de Projeto** para abrir a janela Configurações de Projeto.</span><span class="sxs-lookup"><span data-stu-id="b9641-152">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="b9641-153">Na janela Configurações do Projeto, selecione a guia **Jogador**, expanda a seção **Outras Configurações**, selecione **Vulkan** e remova-o clicando no símbolo " **-** ".</span><span class="sxs-lookup"><span data-stu-id="b9641-153">In the Project Settings, window selects the **Player** tab, expand the **Other Settings** section, select **Vulkan**, and remove it by clicking the "**-**" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="b9641-155">Feche a janela **Configurações do Jogador** e abra a janela **Configurações de Build** novamente.</span><span class="sxs-lookup"><span data-stu-id="b9641-155">Close the **Player Settings** window and open the **Build Settings** window again.</span></span> <span data-ttu-id="b9641-156">Em seguida, usando um cabo USB, conecte seu dispositivo Android ao seu computador e selecione o dispositivo no menu suspenso **Compilar e Executar** e, em seguida, clique em **Compilar e Executar**.</span><span class="sxs-lookup"><span data-stu-id="b9641-156">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run** on the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="b9641-157">Você será solicitado a salvar um arquivo .apk, para o qual pode escolher qualquer nome.</span><span class="sxs-lookup"><span data-stu-id="b9641-157">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="b9641-159">Se você receber algum erro na janela do Console do Unity relacionado aos módulos SDK, NDK e/ou JDK do Android, será necessário abrir o Hub do Unity e instalar os módulos SDK, NDK e JDK associados para o módulo de Suporte de Build do Android.</span><span class="sxs-lookup"><span data-stu-id="b9641-159">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="b9641-160">Quando o processo de compilação for concluído, seus aplicativos deverão ser carregados automaticamente em seu dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="b9641-160">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-an-application-to-ios-device"></a><span data-ttu-id="b9641-161">Compilar um aplicativo para dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="b9641-161">Build an application to iOS Device</span></span>

<span data-ttu-id="b9641-162">Para compilar esse aplicativo para seu dispositivo iOS, clique em **Arquivo** na parte superior da janela e selecione **Configurações de compilação.**</span><span class="sxs-lookup"><span data-stu-id="b9641-162">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="b9641-163">Uma nova janela aparecerá na tela, selecione então **iOS** e clique em **Alternar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="b9641-163">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="b9641-165">Feche a janela de **Configurações de Build**.</span><span class="sxs-lookup"><span data-stu-id="b9641-165">Close the **Build Settings** window.</span></span> <span data-ttu-id="b9641-166">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > Configurar o Projeto do Unity e clique em **Aplicar** para configurar o projeto do Unity para a plataforma iOS.</span><span class="sxs-lookup"><span data-stu-id="b9641-166">In the Unity menu, select Mixed Reality Toolkit > Utilities > Configure Unity Project, and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="b9641-168">Para compilar o projeto do XCode do iOS, vá para Configurações de Build e clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="b9641-168">To build the iOS XCode project, go to Build Settings, and click on **Build**.</span></span>

<span data-ttu-id="b9641-169">Siga [este guia](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implantar esse projeto em seu dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="b9641-169">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b9641-170">Parabéns</span><span class="sxs-lookup"><span data-stu-id="b9641-170">Congratulations</span></span>

<span data-ttu-id="b9641-171">Neste tutorial, você aprendeu a compilar seu projeto para dispositivos Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="b9641-171">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="b9641-172">Você também aprendeu a usar o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR para fazer seu projeto funcionar em dispositivos Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="b9641-172">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>

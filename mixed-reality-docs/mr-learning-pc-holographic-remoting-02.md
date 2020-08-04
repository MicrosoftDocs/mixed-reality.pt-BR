---
title: Tutoriais de Comunicação Remota Holográfica para PC – 2. Criar um aplicativo de Comunicação Remota Holográfica para PC
description: Conclua este curso para aprender como criar a experiência de realidade misturada remota do seu PC para o HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6d11d91a0e08c48c09f676171dcb9bb8a0ff74de
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376368"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="2559e-105">2. Como criar um aplicativo de Comunicação Remota Holográfica para PC</span><span class="sxs-lookup"><span data-stu-id="2559e-105">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="2559e-106">Neste tutorial, você aprenderá a criar um aplicativo para PC de Comunicação Remota Holográfica e a conectar-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo em 3D na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2559e-106">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="2559e-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2559e-107">Objectives</span></span>

* <span data-ttu-id="2559e-108">Configurar o Unity para Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="2559e-108">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="2559e-109">Saber como criar e implantar o aplicativo com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2559e-109">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="2559e-110">Desenvolver o aplicativo de Comunicação Remota Holográfica e conectar-se ao HoloLens</span><span class="sxs-lookup"><span data-stu-id="2559e-110">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="2559e-111">Configurar a sua cena para a Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="2559e-111">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="2559e-112">Nesta seção, você vai configurar o projeto para transmitir a sua experiência de Realidade Misturada do seu PC para o dispositivo de HoloLens 2 em tempo real em uma conexão Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="2559e-112">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="2559e-113">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.PCHolograhicRemoting** > **Pré-fabricados** e clique e arraste o pré-fabricado **HolographicRemoting** para a sua cena.</span><span class="sxs-lookup"><span data-stu-id="2559e-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="2559e-115">Criar o aplicativo para PC</span><span class="sxs-lookup"><span data-stu-id="2559e-115">Build your application to PC</span></span>

<span data-ttu-id="2559e-116">O seu aplicativo de Comunicação Remota Holográfica agora está pronto para ser criado no PC.</span><span class="sxs-lookup"><span data-stu-id="2559e-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="2559e-117">Siga as etapas abaixo e faça estas alterações para criar esse aplicativo no seu PC.</span><span class="sxs-lookup"><span data-stu-id="2559e-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="2559e-118">1. Definir as configurações do player</span><span class="sxs-lookup"><span data-stu-id="2559e-118">1. Set the player settings</span></span>

<span data-ttu-id="2559e-119">No menu do Unity, selecione Editar > Configurações do Projeto para abrir a janela Configurações do Player.</span><span class="sxs-lookup"><span data-stu-id="2559e-119">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="2559e-120">Na seção **Configurações de XR**, marque a caixa de seleção **Comunicação Remota Holográfica do WSA com Suporte** e habilite a Comunicação Remota Holográfica.</span><span class="sxs-lookup"><span data-stu-id="2559e-120">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="2559e-122">2. Criar o Projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="2559e-122">2. Build the Unity Project</span></span>

<span data-ttu-id="2559e-123">No menu do Unity, selecione Arquivo > Configurações de Build para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="2559e-123">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="2559e-124">Na janela Configurações de Build, clique no botão ***Adicionar Cenas Abertas*** para adicionar a cena atual às Cenas.</span><span class="sxs-lookup"><span data-stu-id="2559e-124">In the Build Settings window, click the ***Add Open Scenes*** button to add your current scene to the Scenes.</span></span> <span data-ttu-id="2559e-125">Na lista Criar, clique no botão ***Criar*** para abrir a janela Criar a Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="2559e-125">In the Build list, then click the ***Build button*** to open the Build Universal Windows Platform window:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="2559e-127">Na janela Criar Plataforma Universal do Windows, escolha uma localização adequada para armazenar o seu build, por exemplo, Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="2559e-127">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="2559e-128">Crie uma pasta e dê a ela um nome adequado, por exemplo, PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="2559e-128">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="2559e-129">Em seguida, clique no botão ***Selecionar Pasta*** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="2559e-129">Then click the ***Select Folder*** button to start the build process:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="2559e-131">Aguarde até que o Unity conclua o processo de build.</span><span class="sxs-lookup"><span data-stu-id="2559e-131">Wait for Unity to finish the build process.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="2559e-133">3. Compilar e implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="2559e-133">3. Build and deploy the application</span></span>

<span data-ttu-id="2559e-134">Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra o local em que você armazenou o build.</span><span class="sxs-lookup"><span data-stu-id="2559e-134">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="2559e-135">Navegue dentro da pasta e clique duas vezes no arquivo .sln para abri-lo no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="2559e-135">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="2559e-137">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar que todos os componentes necessários estejam instalados conforme especificado na documentação Instalar as Ferramentas.</span><span class="sxs-lookup"><span data-stu-id="2559e-137">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="2559e-138">Configure o Visual Studio para PC selecionando a configuração da Versão, a arquitetura x64 e o Computador Local como um destino:</span><span class="sxs-lookup"><span data-stu-id="2559e-138">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="2559e-140">Clique no botão ***Computador Local***.</span><span class="sxs-lookup"><span data-stu-id="2559e-140">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="2559e-141">Ele começa a criar e implantar o aplicativo no seu PC.</span><span class="sxs-lookup"><span data-stu-id="2559e-141">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="2559e-142">O aplicativo será instalado no seu PC por padrão.</span><span class="sxs-lookup"><span data-stu-id="2559e-142">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="2559e-143">Como testar o aplicativo remoto de Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="2559e-143">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="2559e-144">Para conectar o seu aplicativo para PC ao seu HoloLens 2, siga o processo abaixo:</span><span class="sxs-lookup"><span data-stu-id="2559e-144">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="2559e-145">1. Instale o aplicativo de Player de Comunicação Remota no dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2559e-145">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="2559e-146">No seu HoloLens 2, visite a Loja de aplicativos e pesquise por "**Player de Comunicação Remota**".</span><span class="sxs-lookup"><span data-stu-id="2559e-146">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="2559e-147">Selecione o aplicativo **Player de Comunicação Remota**.</span><span class="sxs-lookup"><span data-stu-id="2559e-147">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="2559e-148">Toque em **Instalar** para baixar e instalar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2559e-148">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="2559e-149">2. Conectar o aplicativo de Comunicação Remota Holográfica para PC ao Player de Comunicação Remota</span><span class="sxs-lookup"><span data-stu-id="2559e-149">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="2559e-150">Inicie o **Player de Comunicação Remota** no seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2559e-150">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="2559e-151">Anote o **endereço IP** do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2559e-151">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="2559e-152">Ele será exibido como um holograma pelo **Player de Comunicação Remota** assim que for iniciado.</span><span class="sxs-lookup"><span data-stu-id="2559e-152">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="2559e-153">Abra um aplicativo de Comunicação Remota Holográfica para PC no seu PC.</span><span class="sxs-lookup"><span data-stu-id="2559e-153">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="2559e-154">Depois que o aplicativo for iniciado, insira o **endereço IP** e clique no botão **Conectar** para se conectar.</span><span class="sxs-lookup"><span data-stu-id="2559e-154">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2559e-155">Parabéns</span><span class="sxs-lookup"><span data-stu-id="2559e-155">Congratulations</span></span>

<span data-ttu-id="2559e-156">Neste tutorial, você aprendeu como criar um aplicativo remoto para PC de Comunicação Remota Holográfica e a conectar-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo em 3D na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2559e-156">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="2559e-157">Depois que o HoloLens estiver conectado ao aplicativo de Comunicação Remota Holográfica para PC, você deverá ver a transmissão da experiência de realidade misturada no seu dispositivo de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2559e-157">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>

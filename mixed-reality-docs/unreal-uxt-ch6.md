---
title: 6. Como empacotar e implantar no dispositivo ou emulador
description: Parte 6 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 99c431920c72cf85fed5a0eec6fc72ddf9fb112c
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330223"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="071b7-104">6. Como empacotar e implantar no dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="071b7-104">6. Packaging & deploying to device or emulator</span></span>

## <a name="overview"></a><span data-ttu-id="071b7-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="071b7-105">Overview</span></span>

<span data-ttu-id="071b7-106">No tutorial anterior, você adicionou um botão simples que redefine a peça de xadrez para a posição original dela.</span><span class="sxs-lookup"><span data-stu-id="071b7-106">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="071b7-107">Nesta seção final, você fará com que o aplicativo esteja pronto para ser executado em um HoloLens 2 ou em um emulador.</span><span class="sxs-lookup"><span data-stu-id="071b7-107">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="071b7-108">Se você tem um HoloLens 2, pode transmitir do seu computador ou empacotar o aplicativo para ser executado diretamente no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="071b7-108">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="071b7-109">Se você não tem um dispositivo, você está empacotando o aplicativo para ser executado no emulador.</span><span class="sxs-lookup"><span data-stu-id="071b7-109">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="071b7-110">Ao final desta seção, você terá um aplicativo de realidade misturada implantado que você poderá jogar, completo, com interações e interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="071b7-110">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="071b7-111">Objetivos</span><span class="sxs-lookup"><span data-stu-id="071b7-111">Objectives</span></span>

* <span data-ttu-id="071b7-112">[Somente para dispositivo] Transmitir para o HoloLens 2 por meio de comunicação remota holográfica do aplicativo</span><span class="sxs-lookup"><span data-stu-id="071b7-112">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="071b7-113">Empacotar e implantar seu aplicativo em um emulador ou dispositivo do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="071b7-113">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="071b7-114">[Somente para dispositivo] Streaming</span><span class="sxs-lookup"><span data-stu-id="071b7-114">[Device Only] Streaming</span></span>
<span data-ttu-id="071b7-115">A [comunicação remota holográfica](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting), nesse caso, significa transmitir dados de um computador ou dispositivo UWP autônomo para o HoloLens 2, sem mudar de canal.</span><span class="sxs-lookup"><span data-stu-id="071b7-115">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in this case means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="071b7-116">Isso funciona com um aplicativo host de comunicação remota que recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo de volta para o HoloLens por Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="071b7-116">The way this works is a remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="071b7-117">O streaming permite que você adicione exibições imersivas remotas a software de PC desktop existente e tenha acesso a mais recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="071b7-117">Streaming allows you to add remote immersive views into existing desktop PC software and has access to more system resources.</span></span> 

<span data-ttu-id="071b7-118">Se você estiver seguindo por esse caminho com o aplicativo de xadrez, precisará fazer algumas coisas:</span><span class="sxs-lookup"><span data-stu-id="071b7-118">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="071b7-119">Instale o **Player de Comunicação Remota Holográfica** por meio da Microsoft Store no seu HoloLens 2 e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="071b7-119">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span>

2.  <span data-ttu-id="071b7-120">Acesse **Editar > Configurações do Projeto** e marque **habilitar a comunicação remota** na seção **Comunicação Remota Holográfica**.</span><span class="sxs-lookup"><span data-stu-id="071b7-120">Go to **Edit > Project Settings** and check **enable remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="071b7-121">Reinicie o editor, [encontre o endereço IP do dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi), insira-o e clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="071b7-121">Restart the editor, [find your device's IP address](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi) and enter it, then click **Connect**.</span></span>

<span data-ttu-id="071b7-122">Quando estiver conectado, clique na seta suspensa à direita do botão **Jogar** e selecione a **Visualização de VR**.</span><span class="sxs-lookup"><span data-stu-id="071b7-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="071b7-123">Isso executará o aplicativo na Janela de Visualização de VR, que é transmitida para o headset do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="071b7-123">This will run the app in the VR Preview Window, which is streamed to the HoloLens headset.</span></span> 

## <a name="packaging-and-deploying-the-app"></a><span data-ttu-id="071b7-124">Como empacotar e implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="071b7-124">Packaging and deploying the app</span></span> 

>[!NOTE]
><span data-ttu-id="071b7-125">Se esta for a primeira vez que você empacota um aplicativo Unreal para o HoloLens, precisará baixar os arquivos de suporte do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="071b7-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> 
>- <span data-ttu-id="071b7-126">Vá para a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** > e clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="071b7-126">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span> 
>- <span data-ttu-id="071b7-127">Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="071b7-127">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="071b7-128">![Configurações do projeto – Descrição](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="071b7-128">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="071b7-129">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="071b7-129">Go to **Edit > Project Settings**.</span></span> 
    * <span data-ttu-id="071b7-130">Em **Projeto > Descrição > Sobre > Nome do Projeto**, adicione um nome de projeto.</span><span class="sxs-lookup"><span data-stu-id="071b7-130">Add a project name under **Project > Description > About > Project Name**.</span></span> 
    * <span data-ttu-id="071b7-131">Em **Projeto > Descrição > Publicador > Nome Diferenciado da Empresa**, adicione **CN={INSIRA O NOME DA EMPRESA}** .</span><span class="sxs-lookup"><span data-stu-id="071b7-131">Add **CN={INSERT COMPANY NAME}** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="071b7-132">Deixar qualquer um desses campos em branco resultará em um erro.</span><span class="sxs-lookup"><span data-stu-id="071b7-132">Leaving either of these fields blank will result in an error.</span></span> 

![Configurações do projeto – descrição](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="071b7-134">Habilite **Compilar para Emulação no HoloLens** e/ou **Compilar para Dispositivo do HoloLens** em **Plataformas > HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="071b7-134">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="071b7-135">Clique em **Gerar novo** na seção **Empacotamento** (ao lado de **Certificado de Assinatura**) e, em seguida, volte para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="071b7-135">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**), then return to the Main window.</span></span>

![Configurações do projeto – Plataformas – HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="071b7-137">Acesse **Arquivo > Empacotar Projeto** e selecione **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="071b7-137">Go to **File > Package Project** and select **HoloLens**.</span></span> 
    * <span data-ttu-id="071b7-138">Crie uma pasta para salvar o pacote e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="071b7-138">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="071b7-139">Depois que o aplicativo tiver sido empacotado, abra o [Portal de Dispositivos do Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), acesse **Exibições > Aplicativos** e localize a seção **Implantar aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="071b7-139">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="071b7-140">Clique em **Procurar...** , encontre o arquivo **ChessApp.appxbundle** e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="071b7-140">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span> 

    * <span data-ttu-id="071b7-141">Se esta é a primeira vez que você está instalando o aplicativo em seu dispositivo, marque a caixa ao lado de **Permitir que eu selecione pacotes de estrutura**.</span><span class="sxs-lookup"><span data-stu-id="071b7-141">Check the box next to **Allow me to select framework packages** if this is the first time you're installing the app on your device.</span></span> 
    * <span data-ttu-id="071b7-142">Na próxima caixa de diálogo, inclua os arquivos **VCLibs** e **appx** apropriados (arm64 para dispositivo, x64 para emulador).</span><span class="sxs-lookup"><span data-stu-id="071b7-142">In the next dialogue, include the appropriate **VCLibs** and **appx** files (arm64 for device, x64 for emulator).</span></span> <span data-ttu-id="071b7-143">Você pode encontrá-los em **HoloLens**, dentro da pasta em que você salvou o pacote.</span><span class="sxs-lookup"><span data-stu-id="071b7-143">You can find these under **HoloLens** inside the folder where you saved your package.</span></span>

7.  <span data-ttu-id="071b7-144">Clique em **Instalar**</span><span class="sxs-lookup"><span data-stu-id="071b7-144">Click **Install**</span></span>
    * <span data-ttu-id="071b7-145">Agora você pode acessar **Todos os Aplicativos** e tocar no aplicativo recém-instalado para executá-lo ou pode iniciar o aplicativo diretamente do **Portal de Dispositivos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="071b7-145">You can now go to **All Apps** and tap the the newly installed app to run it, or you can start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="071b7-146">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="071b7-146">Congratulations!</span></span> <span data-ttu-id="071b7-147">O seu aplicativo de realidade misturada do HoloLens está concluído e pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="071b7-147">You're HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="071b7-148">No entanto, esse não é o fim da jornada.</span><span class="sxs-lookup"><span data-stu-id="071b7-148">However, this isn't the end of the road.</span></span> <span data-ttu-id="071b7-149">O MRTK tem muitos recursos autônomos que você pode adicionar aos seus projetos, incluindo entrada por foco e voz, mapeamento espacial e até mesmo códigos QR.</span><span class="sxs-lookup"><span data-stu-id="071b7-149">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="071b7-150">Mais informações sobre esses recursos podem ser encontradas na [Visão geral do desenvolvimento com o Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="071b7-150">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>
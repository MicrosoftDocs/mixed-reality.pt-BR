---
title: 6. Como empacotar e implantar no dispositivo ou emulador
description: Parte 6 de um tutorial para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519958"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="93cf7-104">6. Como empacotar e implantar no dispositivo ou emulador</span><span class="sxs-lookup"><span data-stu-id="93cf7-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="93cf7-105">Esta seção orienta nas etapas de preparação de seu aplicativo para ser executado em um dispositivo ou emulador do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="93cf7-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="93cf7-106">Se você tem um dispositivo, pode transmitir do seu computador para o dispositivo ou empacotar o aplicativo para ser executado diretamente no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="93cf7-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="93cf7-107">Se você não tiver um dispositivo, será necessário empacotar o aplicativo para que ele seja executado no Emulador.</span><span class="sxs-lookup"><span data-stu-id="93cf7-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="93cf7-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="93cf7-108">Objectives</span></span>

* <span data-ttu-id="93cf7-109">[Somente para dispositivo] Transmitir seu aplicativo para o HoloLens 2 por meio de comunicação remota holográfica do aplicativo</span><span class="sxs-lookup"><span data-stu-id="93cf7-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="93cf7-110">Empacotar e implantar seu aplicativo em um dispositivo ou emulador do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="93cf7-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="93cf7-111">[Somente para dispositivo] Transmitir</span><span class="sxs-lookup"><span data-stu-id="93cf7-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="93cf7-112">Instale o **Player de Comunicação Remota Holográfica** por meio da Microsoft Store no seu HoloLens 2 e execute o aplicativo</span><span class="sxs-lookup"><span data-stu-id="93cf7-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="93cf7-113">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="93cf7-114">Na seção Comunicação Remota Holográfica, marque a caixa para habilitar a comunicação remota e reinicie o editor.</span><span class="sxs-lookup"><span data-stu-id="93cf7-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="93cf7-115">Insira o endereço IP do seu dispositivo e clique em Conectar.</span><span class="sxs-lookup"><span data-stu-id="93cf7-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="93cf7-116">Quando estiver conectado, no editor do UE4, clique na seta suspensa à direita do botão Reproduzir e selecione a visualização VR.</span><span class="sxs-lookup"><span data-stu-id="93cf7-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="93cf7-117">Empacotar e implantar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="93cf7-117">Package and deploy your app</span></span> 

>[!NOTE]
><span data-ttu-id="93cf7-118">Se esta for a primeira vez que você empacota um aplicativo Unreal para o HoloLens, precisará baixar os arquivos de suporte do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="93cf7-118">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> <span data-ttu-id="93cf7-119">Para fazer isso, acesse a guia **Biblioteca** no Epic Games Launcher.</span><span class="sxs-lookup"><span data-stu-id="93cf7-119">To do so, go to the **Library** tab in the Epic Games Launcher.</span></span> <span data-ttu-id="93cf7-120">Selecione a seta suspensa ao lado de **Iniciar** e clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-120">Select the dropdown arrow next to **Launch** and select **Options**.</span></span> <span data-ttu-id="93cf7-121">Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-121">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="93cf7-122">![Configurações do projeto – Descrição](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="93cf7-122">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="93cf7-123">Acesse **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-123">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="93cf7-124">Em **Projeto > Descrição > Sobre > Nome do Projeto**, dê um nome ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="93cf7-124">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="93cf7-125">Em **Projeto > Descrição > Publicador > Nome Diferenciado da Empresa**, coloque “CN={INSERT COMPANY NAME}”.</span><span class="sxs-lookup"><span data-stu-id="93cf7-125">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="93cf7-126">Deixar qualquer um desses campos em branco resultará em um erro.</span><span class="sxs-lookup"><span data-stu-id="93cf7-126">Leaving either of these fields blank will result in an error.</span></span> 

![Configurações do projeto – descrição](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="93cf7-128">Em **Plataformas > HoloLens**, escolha Emulação e/ou Dispositivo com base em qual você deseja direcionar.</span><span class="sxs-lookup"><span data-stu-id="93cf7-128">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="93cf7-129">Na seção **Empacotamento**, ao lado de **Certificado de Assinatura**, clique no botão **Gerar novo** para gerar um novo certificado de autenticação.</span><span class="sxs-lookup"><span data-stu-id="93cf7-129">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="93cf7-130">Volte para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="93cf7-130">Return to the Main window.</span></span>

![Configurações do projeto – Plataformas – HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="93cf7-132">Acesse **Arquivo > Empacotar Projeto** e selecione **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-132">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="93cf7-133">Crie uma pasta para salvar o pacote e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-133">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="93cf7-134">Depois que o aplicativo tiver sido empacotado com êxito, abra o **Portal de Dispositivo do Windows**, acesse **Exibições > Aplicativos** e localize a seção **Implantar aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-134">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="93cf7-135">Clique em **Procurar...** e navegue até o arquivo **ChessApp.appxbundle**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-135">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="93cf7-136">Clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-136">Click **Open**.</span></span> 

    * <span data-ttu-id="93cf7-137">Se esta é a primeira vez que você está instalando o aplicativo em seu dispositivo, marque a caixa ao lado de **Permitir que eu selecione pacotes da estrutura**.</span><span class="sxs-lookup"><span data-stu-id="93cf7-137">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="93cf7-138">Na próxima caixa de diálogo, inclua o arquivo appx VCLibs apropriado (arm64 para dispositivo, x64 para emulador).</span><span class="sxs-lookup"><span data-stu-id="93cf7-138">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="93cf7-139">Clique em **Instalar**</span><span class="sxs-lookup"><span data-stu-id="93cf7-139">Click **Install**</span></span>

<span data-ttu-id="93cf7-140">Parabéns por concluir este tutorial!</span><span class="sxs-lookup"><span data-stu-id="93cf7-140">Congratulations on finishing this tutorial!</span></span>  
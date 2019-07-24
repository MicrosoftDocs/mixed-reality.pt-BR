---
title: Modo de reprodução do Unity
description: Usando o modo de reprodução no editor do Unity para visualizar as alterações em um dispositivo sem implantar um aplicativo.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicação remota, comunicação remota Holographic, player de comunicação remota Holographic
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548722"
---
# <a name="unity-play-mode"></a><span data-ttu-id="223f1-104">Modo de reprodução do Unity</span><span class="sxs-lookup"><span data-stu-id="223f1-104">Unity Play Mode</span></span>

<span data-ttu-id="223f1-105">Uma maneira rápida de trabalhar em seu projeto de Unity é usar o "modo de reprodução".</span><span class="sxs-lookup"><span data-stu-id="223f1-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="223f1-106">Isso executa seu aplicativo localmente no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="223f1-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="223f1-107">O Unity usa a comunicação remota do Holographic para fornecer uma maneira rápida de visualizar o conteúdo em um dispositivo de HoloLens real.</span><span class="sxs-lookup"><span data-stu-id="223f1-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="223f1-108">Modo de reprodução do Unity com comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="223f1-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="223f1-109">Com a comunicação remota do Holographic, você pode experimentar seu aplicativo no HoloLens, enquanto ele é executado no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="223f1-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="223f1-110">Olhar, gesto, voz e entrada de mapeamento espacial são enviados do seu HoloLens para o seu PC.</span><span class="sxs-lookup"><span data-stu-id="223f1-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="223f1-111">Os quadros renderizados são enviados de volta ao seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="223f1-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="223f1-112">Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.</span><span class="sxs-lookup"><span data-stu-id="223f1-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="223f1-113">No seu HoloLens, vá para a **Microsoft Store** e instale o aplicativo de **[player de comunicação remota do Holographic](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .</span><span class="sxs-lookup"><span data-stu-id="223f1-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="223f1-114">No seu HoloLens, inicie o aplicativo do **player de comunicação remota do Holographic** .</span><span class="sxs-lookup"><span data-stu-id="223f1-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="223f1-115">No Unity, vá para o menu **janela** e selecione **emulação Holographic**.</span><span class="sxs-lookup"><span data-stu-id="223f1-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="223f1-116">Defina o **modo** de emulação como **remoto para dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="223f1-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="223f1-117">Para **computador remoto**, insira o endereço IP do seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="223f1-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="223f1-118">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="223f1-118">Click **Connect**.</span></span> <span data-ttu-id="223f1-119">Você deve ver o **status da conexão** alterado para **conectado** e ver a tela ficar em branco no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="223f1-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="223f1-120">Clique no botão **reproduzir** para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="223f1-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="223f1-121">A comunicação remota do Holographic exige um PC rápido e uma conexão Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="223f1-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="223f1-122">Consulte [Holographic Remoting Player](holographic-remoting-player.md) para obter detalhes completos.</span><span class="sxs-lookup"><span data-stu-id="223f1-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="223f1-123">Para obter melhores resultados, verifique se seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="223f1-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="223f1-124">Isso ajuda a Holographic a comunicação remota a melhor adaptação à sua cena com a latência de sua conexão sem fio.</span><span class="sxs-lookup"><span data-stu-id="223f1-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="223f1-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="223f1-125">See Also</span></span>
* [<span data-ttu-id="223f1-126">Player de Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="223f1-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)

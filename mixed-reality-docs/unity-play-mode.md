---
title: Modo de reprodução do Unity
description: Usando o modo de reprodução no editor do Unity para visualizar as alterações em um dispositivo sem implantar um aplicativo.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicação remota, comunicação remota Holographic, player de comunicação remota Holographic
ms.openlocfilehash: dca7ffba1270802fcabed8a88fe7428ef2981553
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277554"
---
# <a name="unity-play-mode"></a><span data-ttu-id="3b07e-104">Modo de reprodução do Unity</span><span class="sxs-lookup"><span data-stu-id="3b07e-104">Unity Play Mode</span></span>

<span data-ttu-id="3b07e-105">Uma maneira rápida de trabalhar em seu projeto de Unity é usar o "modo de reprodução".</span><span class="sxs-lookup"><span data-stu-id="3b07e-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="3b07e-106">Isso executa seu aplicativo localmente no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="3b07e-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="3b07e-107">O Unity usa a comunicação remota do Holographic para fornecer uma maneira rápida de visualizar o conteúdo em um dispositivo de HoloLens real.</span><span class="sxs-lookup"><span data-stu-id="3b07e-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="3b07e-108">O modo de reprodução também pode ser usado com um headset de realidade mista do Windows anexado ao seu PC de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3b07e-108">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="3b07e-109">Modo de reprodução do Unity com comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="3b07e-109">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="3b07e-110">Com a comunicação remota do Holographic, você pode experimentar seu aplicativo no HoloLens, enquanto ele é executado no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="3b07e-110">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="3b07e-111">Olhar, gesto, voz e entrada de mapeamento espacial são enviados do seu HoloLens para o seu PC.</span><span class="sxs-lookup"><span data-stu-id="3b07e-111">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="3b07e-112">Os quadros renderizados são enviados de volta ao seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3b07e-112">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="3b07e-113">Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.</span><span class="sxs-lookup"><span data-stu-id="3b07e-113">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="3b07e-114">No seu HoloLens, vá para a **Microsoft Store** e instale o aplicativo de **[player de comunicação remota do Holographic](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .</span><span class="sxs-lookup"><span data-stu-id="3b07e-114">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="3b07e-115">No seu HoloLens, inicie o aplicativo do **player de comunicação remota do Holographic** .</span><span class="sxs-lookup"><span data-stu-id="3b07e-115">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="3b07e-116">No Unity, vá para o menu **janela** e selecione **emulação Holographic**.</span><span class="sxs-lookup"><span data-stu-id="3b07e-116">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="3b07e-117">Defina o **modo de emulação** como **remoto para dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="3b07e-117">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="3b07e-118">Para **computador remoto**, insira o endereço IP do seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3b07e-118">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="3b07e-119">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="3b07e-119">Click **Connect**.</span></span> <span data-ttu-id="3b07e-120">Você deve ver o **status da conexão** alterado para **conectado** e ver a tela ficar em branco no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3b07e-120">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="3b07e-121">Clique no botão **reproduzir** para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3b07e-121">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="3b07e-122">A comunicação remota do Holographic exige um PC rápido e uma conexão Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="3b07e-122">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="3b07e-123">Consulte [Holographic Remoting Player](holographic-remoting-player.md) para obter detalhes completos.</span><span class="sxs-lookup"><span data-stu-id="3b07e-123">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="3b07e-124">Para obter melhores resultados, verifique se seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="3b07e-124">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="3b07e-125">Isso ajuda a Holographic a comunicação remota a melhor adaptação à sua cena com a latência de sua conexão sem fio.</span><span class="sxs-lookup"><span data-stu-id="3b07e-125">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b07e-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="3b07e-126">See Also</span></span>
* [<span data-ttu-id="3b07e-127">Player de Comunicação Remota Holográfica</span><span class="sxs-lookup"><span data-stu-id="3b07e-127">Holographic Remoting Player</span></span>](holographic-remoting-player.md)

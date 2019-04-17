---
title: Modo de jogo do Unity
description: Usando o modo de reprodução no editor do Unity para visualizar as alterações em um dispositivo sem implantar um aplicativo.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicação remota, comunicação remota holográfica, player holográfica remoting
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589137"
---
# <a name="unity-play-mode"></a><span data-ttu-id="11b46-104">Modo de jogo do Unity</span><span class="sxs-lookup"><span data-stu-id="11b46-104">Unity Play Mode</span></span>

<span data-ttu-id="11b46-105">Uma maneira rápida de trabalhar em seu projeto do Unity é usar o "Modo de reprodução".</span><span class="sxs-lookup"><span data-stu-id="11b46-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="11b46-106">Isso executa seu aplicativo localmente no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="11b46-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="11b46-107">O Unity usa comunicação remota holográfica para fornecer uma maneira rápida de visualizar o conteúdo em um dispositivo real do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="11b46-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="11b46-108">Modo de jogo do Unity com a comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="11b46-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="11b46-109">Com a comunicação remota holográfica, você pode experimentar seu aplicativo em HoloLens, enquanto ele é executado no editor do Unity em seu computador.</span><span class="sxs-lookup"><span data-stu-id="11b46-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="11b46-110">Olhar, gesto, voz e mapeamento espacial de entrada é enviada do seu HoloLens a seu computador.</span><span class="sxs-lookup"><span data-stu-id="11b46-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="11b46-111">Quadros renderizados, em seguida, são enviados para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="11b46-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="11b46-112">Isso é uma ótima maneira de depurar rapidamente seu aplicativo sem compilar e implantar um projeto completo.</span><span class="sxs-lookup"><span data-stu-id="11b46-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="11b46-113">Em seu HoloLens, vá para o **Microsoft Store** e instale o **[holográfica Player de comunicação remota](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11b46-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="11b46-114">No seu HoloLens, inicie o **holográfica Player de comunicação remota** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11b46-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="11b46-115">No Unity, vá para o **janela** menu e selecione **emulação holográfica**.</span><span class="sxs-lookup"><span data-stu-id="11b46-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="11b46-116">Definir **modo de emulação** à **remoto ao dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="11b46-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="11b46-117">Para **máquina remota**, insira o endereço IP do seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="11b46-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="11b46-118">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="11b46-118">Click **Connect**.</span></span> <span data-ttu-id="11b46-119">Você deve ver **Status de Conexão** alterar para **conectado** e ver a tela ficar em branco no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="11b46-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="11b46-120">Clique o **reproduzir** botão para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="11b46-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="11b46-121">Comunicação remota holográfica requer uma conexão rápida de PC e Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="11b46-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="11b46-122">Ver [holográfica Player de comunicação remota](holographic-remoting-player.md) para obter detalhes completos.</span><span class="sxs-lookup"><span data-stu-id="11b46-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="11b46-123">Para obter melhores resultados, verifique se seu aplicativo corretamente define o [focar ponto](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="11b46-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="11b46-124">Isso ajuda a comunicação remota holográfica melhor adaptar sua cena para a latência de sua conexão sem fio.</span><span class="sxs-lookup"><span data-stu-id="11b46-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="11b46-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11b46-125">See Also</span></span>
* [<span data-ttu-id="11b46-126">Comunicação remota holográfica Player</span><span class="sxs-lookup"><span data-stu-id="11b46-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)

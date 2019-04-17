---
title: Comunicação remota holográfica Player
description: O Player holográfica de comunicação remota é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota holográfica. Remoting holográfica transmite holográfico conteúdo de um PC para o Microsoft HoloLens em tempo real, usando uma conexão Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Comunicação remota do HoloLens, comunicação remota, Holographic
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591000"
---
# <a name="holographic-remoting-player"></a><span data-ttu-id="7a156-105">Comunicação remota holográfica Player</span><span class="sxs-lookup"><span data-stu-id="7a156-105">Holographic Remoting Player</span></span>

<span data-ttu-id="7a156-106">O Player holográfica de comunicação remota é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="7a156-106">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="7a156-107">Remoting holográfica transmite holográfico conteúdo de um PC para o Microsoft HoloLens em tempo real, usando uma conexão Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="7a156-107">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection.</span></span>

<span data-ttu-id="7a156-108">O Player de comunicação remota holográfica só pode ser usado com aplicativos de PC projetados especificamente para dar suporte à comunicação remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="7a156-108">The Holographic Remoting Player can only be used with PC apps that are specifically designed to support Holographic Remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="7a156-109">Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="7a156-109">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="connecting-to-the-holographic-remoting-player"></a><span data-ttu-id="7a156-110">Conectar-se para o Player de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="7a156-110">Connecting to the Holographic Remoting Player</span></span>

<span data-ttu-id="7a156-111">Siga as instruções do seu aplicativo para se conectar ao Player de comunicação remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="7a156-111">Follow your app's instructions to connect to the Holographic Remoting Player.</span></span> <span data-ttu-id="7a156-112">Você precisará inserir o endereço IP do dispositivo HoloLens, o que você pode ver na tela principal de comunicação remota do Player da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="7a156-112">You will need to enter the IP address of your HoloLens device, which you can see on the Remoting Player's main screen as follows:</span></span>

![Comunicação remota holográfica Player](images/holographicremotingplayer.png)

<span data-ttu-id="7a156-114">Sempre que você vir a tela principal, você saberá que você não tem um aplicativo conectado.</span><span class="sxs-lookup"><span data-stu-id="7a156-114">Whenever you see the main screen, you will know that you do not have an app connected.</span></span>

<span data-ttu-id="7a156-115">Observe que a conexão de comunicação remota holographic **não criptografado**.</span><span class="sxs-lookup"><span data-stu-id="7a156-115">Note that the holographic remoting connection is **not encrypted**.</span></span> <span data-ttu-id="7a156-116">Você sempre deve usar a comunicação remota holográfica ao longo de uma conexão segura de Wi-Fi que você confia.</span><span class="sxs-lookup"><span data-stu-id="7a156-116">You should always use Holographic Remoting over a secure Wi-Fi connection that you trust.</span></span>

## <a name="quality-and-performance"></a><span data-ttu-id="7a156-117">Desempenho e qualidade</span><span class="sxs-lookup"><span data-stu-id="7a156-117">Quality and Performance</span></span>

<span data-ttu-id="7a156-118">A qualidade e o desempenho de sua experiência variará com base em três fatores:</span><span class="sxs-lookup"><span data-stu-id="7a156-118">The quality and performance of your experience will vary based on three factors:</span></span>
* <span data-ttu-id="7a156-119">**A experiência holográfica estiver executando** -aplicativos que processam conteúdo de alta resolução ou altamente detalhadas podem exigir um PC mais rápido ou mais rapidamente a conexão sem fio.</span><span class="sxs-lookup"><span data-stu-id="7a156-119">**The holographic experience you're running** - Apps that render high-resolution or highly-detailed content may require a faster PC or faster wireless connection.</span></span>
* <span data-ttu-id="7a156-120">**O hardware do computador** -seu PC precisa ser capaz de executar e codificar sua experiência holográfica 60 quadros por segundo.</span><span class="sxs-lookup"><span data-stu-id="7a156-120">**Your PC's hardware** - Your PC needs to be able to run and encode your holographic experience at 60 frames per second.</span></span> <span data-ttu-id="7a156-121">Para uma placa gráfica, geralmente recomendamos um GeForce GTX 970 ou AMD Radeon R9 290 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="7a156-121">For a graphics card, we generally recommend a GeForce GTX 970 or AMD Radeon R9 290 or better.</span></span> <span data-ttu-id="7a156-122">Novamente, sua experiência específica pode exigir um cartão mais alto ou low-end.</span><span class="sxs-lookup"><span data-stu-id="7a156-122">Again, your particular experience may require a higher or lower-end card.</span></span>
* <span data-ttu-id="7a156-123">**Sua conexão Wi-Fi** -sua experiência holográfica é transmitida por Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="7a156-123">**Your Wi-Fi connection** - Your holographic experience is streamed over Wi-Fi.</span></span> <span data-ttu-id="7a156-124">Use uma rede rápida com o congestionamento de baixo para melhorar a qualidade.</span><span class="sxs-lookup"><span data-stu-id="7a156-124">Use a fast network with low congestion to maximize quality.</span></span> <span data-ttu-id="7a156-125">Usando um computador que está conectado por um cabo Ethernet, em vez de Wi-Fi, poderá também melhorar a qualidade.</span><span class="sxs-lookup"><span data-stu-id="7a156-125">Using a PC that is connected over an Ethernet cable, rather than Wi-Fi, may also improve quality.</span></span>

## <a name="diagnostics"></a><span data-ttu-id="7a156-126">Diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7a156-126">Diagnostics</span></span>

<span data-ttu-id="7a156-127">Para medir a qualidade da sua conexão, digamos **"Ativar diagnóstico"** enquanto na tela principal do Player holográfica comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="7a156-127">To measure the quality of your connection, say **"enable diagnostics"** while on the main screen of the Holographic Remoting Player.</span></span> <span data-ttu-id="7a156-128">Quando os diagnósticos são habilitados, o aplicativo mostrará a você:</span><span class="sxs-lookup"><span data-stu-id="7a156-128">When diagnostics are enabled, the app will show you:</span></span>
* <span data-ttu-id="7a156-129">**FPS** – o número médio de quadros renderizados o player de comunicação remota está recebendo e renderização por segundo.</span><span class="sxs-lookup"><span data-stu-id="7a156-129">**FPS** - The average number of rendered frames the remoting player is receiving and rendering per second.</span></span> <span data-ttu-id="7a156-130">O ideal é de 60 FPS.</span><span class="sxs-lookup"><span data-stu-id="7a156-130">The ideal is 60 FPS.</span></span>
* <span data-ttu-id="7a156-131">**Latência** -a quantidade média de tempo que leva para um quadro ir do seu computador para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7a156-131">**Latency** - The average amount of time it takes for a frame to go from your PC to the HoloLens.</span></span> <span data-ttu-id="7a156-132">Quanto menor, melhor.</span><span class="sxs-lookup"><span data-stu-id="7a156-132">The lower the better.</span></span> <span data-ttu-id="7a156-133">Isso é altamente dependente em sua rede Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="7a156-133">This is largely dependent on your Wi-Fi network.</span></span>

<span data-ttu-id="7a156-134">Enquanto estiver na tela principal, você pode dizer **"desabilitar o diagnóstico"** para desativar o diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="7a156-134">While on the main screen, you can say **"disable diagnostics"** to turn off diagnostics.</span></span>

## <a name="pc-system-requirements"></a><span data-ttu-id="7a156-135">Requisitos do sistema de PC</span><span class="sxs-lookup"><span data-stu-id="7a156-135">PC System Requirements</span></span>
* <span data-ttu-id="7a156-136">Seu PC **deve** estar executando a atualização de aniversário do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="7a156-136">Your PC **must** be running the Windows 10 Anniversary Update.</span></span>
* <span data-ttu-id="7a156-137">É recomendável um GeForce GTX 970 ou AMD Radeon R9 290 ou placa de vídeo melhor.</span><span class="sxs-lookup"><span data-stu-id="7a156-137">We recommend a GeForce GTX 970 or AMD Radeon R9 290 or better graphics card.</span></span>
* <span data-ttu-id="7a156-138">É recomendável que você conecte seu PC à sua rede por meio de ethernet para reduzir o número de saltos de sem fio.</span><span class="sxs-lookup"><span data-stu-id="7a156-138">We recommend you connect your PC to your network via ethernet to reduce the number of Wireless hops.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a156-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a156-139">See Also</span></span>
* [<span data-ttu-id="7a156-140">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="7a156-140">Holographic remoting software license terms</span></span>](microsoft-holographic-remoting-software-license-terms.md)
* [<span data-ttu-id="7a156-141">Declaração de privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="7a156-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)

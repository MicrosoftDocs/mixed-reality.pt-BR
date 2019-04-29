---
title: Visão geral de desenvolvimento
description: Este artigo descreve os blocos de construção básicos do desenvolvimento de um aplicativo de realidade mista do Windows.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: ao obter Introdução, Noções básicas, HoloLens, HoloLens 2, fone de ouvido imersivo, unity, o visual studio
ms.openlocfilehash: 1d23e458477cc23252ccd4c44f67c400aa356965
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591022"
---
# <a name="development-overview"></a><span data-ttu-id="d9f6b-104">Visão geral de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="d9f6b-104">Development overview</span></span>

<span data-ttu-id="d9f6b-105">Aplicativos de realidade misturada podem ser desenvolvidos usando uma variedade de tecnologias para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-105">Mixed reality apps can be developed using a variety of developer technologies.</span></span>  <span data-ttu-id="d9f6b-106">HoloLens executa aplicativos criados com o [plataforma Universal do Windows](https://dev.windows.com/getstarted).</span><span class="sxs-lookup"><span data-stu-id="d9f6b-106">HoloLens runs apps that are built with the [Universal Windows Platform](https://dev.windows.com/getstarted).</span></span>  <span data-ttu-id="d9f6b-107">Fones imersivos em exposição executar aplicativos da plataforma Universal do Windows, bem como aplicativos Win32.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-107">Immersive headsets run Universal Windows Platform apps as well as Win32 applications.</span></span>
<span data-ttu-id="d9f6b-108">Obtendo familiarizado com as ferramentas de middleware como o Unity, você pode começar criando experiências de realidade misturada hoje.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-108">By getting familiar with middleware tools like Unity, you can start building mixed reality experiences today.</span></span>  <span data-ttu-id="d9f6b-109">Aproveitar o código-fonte aberto [Kit de ferramentas de realidade misturada](install-the-tools.md) para se familiarizar rapidamente.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-109">Leverage the open source [Mixed Reality Toolkit](install-the-tools.md) to get started quickly.</span></span>
<span data-ttu-id="d9f6b-110"><a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Misto dos serviços de realidade</a>, como <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, têm SDKs que podem integrar várias tecnologias de desenvolvedor de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-110"><a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Mixed reality services</a>, such as <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, have SDKs that can integrate into various cross-platform developer technologies as well.</span></span>

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a><span data-ttu-id="d9f6b-111">Noções básicas do desenvolvimento de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="d9f6b-111">Basics of mixed reality development</span></span>

<span data-ttu-id="d9f6b-112">[Realidade misturada](mixed-reality.md) experiências são habilitadas por novos recursos do Windows para compreensão ambiental.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-112">[Mixed reality](mixed-reality.md) experiences are enabled by new Windows features for environmental understanding.</span></span> <span data-ttu-id="d9f6b-113">Eles permitem que os desenvolvedores colocar uma [holograma](hologram.md) no mundo real, e permitir que os usuários percorrer os mundos digitais percorrendo sobre literalmente.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-113">These enable developers to place a [hologram](hologram.md) in the real world, and allow users to move through digital worlds by literally walking about.</span></span> 

<span data-ttu-id="d9f6b-114">Estes são os principais blocos de construção para o desenvolvimento de realidade mista:</span><span class="sxs-lookup"><span data-stu-id="d9f6b-114">These are the core building blocks for mixed reality development:</span></span>

<table>
<tr>
<th><span data-ttu-id="d9f6b-115">Entrada</span><span class="sxs-lookup"><span data-stu-id="d9f6b-115">Input</span></span></th><th style="width:150px"> <span data-ttu-id="d9f6b-116"><a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-116"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d9f6b-117">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d9f6b-117">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="d9f6b-118"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-118"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d9f6b-119"><a href="gaze.md">Mantenha o foco principal</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-119"><a href="gaze.md">Head gaze</a></span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-120">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-120">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-121">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-121">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-122">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9f6b-123"><a href="gaze.md">Eye gaze</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-123"><a href="gaze.md">Eye gaze</a></span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="d9f6b-124">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-124">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="d9f6b-125">Mãos / <a href="gestures.md">gestos</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-125">Hands / <a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-126">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-127">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-127">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="d9f6b-128"><a href="voice-input.md">Voz</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-128"><a href="voice-input.md">Voice</a></span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-129">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-130">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-131">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-131">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9f6b-132"><a href="hardware-accessories.md">Gamepad</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-132"><a href="hardware-accessories.md">Gamepad</a></span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-133">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-133">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-134">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-134">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-135">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-135">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9f6b-136"><a href="motion-controllers.md">Controladores de movimento</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-136"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td></td><td style="text-align: center;"><span data-ttu-id="d9f6b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-137">✔️</span></span></td>
</tr><tr>
<th> <span data-ttu-id="d9f6b-138">Percepção e recursos espaciais</span><span class="sxs-lookup"><span data-stu-id="d9f6b-138">Perception and spatial features</span></span></th><th style="width:150px"> <span data-ttu-id="d9f6b-139"><a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-139"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d9f6b-140">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d9f6b-140">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="d9f6b-141"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-141"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d9f6b-142"><a href="coordinate-systems.md">Coordenadas de mundo</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-142"><a href="coordinate-systems.md">World coordinates</a></span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-143">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-144">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-144">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-145">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-145">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9f6b-146"><a href="spatial-sound.md">Som espacial</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-146"><a href="spatial-sound.md">Spatial sound</a></span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-147">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-147">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-148">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-148">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-149">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-149">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9f6b-150"><a href="spatial-mapping.md">Mapeamento espacial</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-150"><a href="spatial-mapping.md">Spatial mapping</a></span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-151">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-151">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="d9f6b-152">✔️</span><span class="sxs-lookup"><span data-stu-id="d9f6b-152">✔️</span></span></td><td></td>
</tr>
</table>



<span data-ttu-id="d9f6b-153">O modelo de interação básico para [HoloLens](hololens-hardware-details.md) é [olhares](gaze.md), [gesto](gestures.md), e [voz](voice-input.md), às vezes chamados de *GGV* .</span><span class="sxs-lookup"><span data-stu-id="d9f6b-153">The basic interaction model for [HoloLens](hololens-hardware-details.md) is [gaze](gaze.md), [gesture](gestures.md), and [voice](voice-input.md), sometimes referred to as *GGV*.</span></span> <span data-ttu-id="d9f6b-154">[Fones imersivos em exposição Windows Mixed Reality](immersive-headset-hardware-details.md) também olhar de uso e voz, mas troca [controladores de movimento](motion-controllers.md) para gestos.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-154">[Windows Mixed Reality immersive headsets](immersive-headset-hardware-details.md) also use gaze and voice, but swap [motion controllers](motion-controllers.md) for gestures.</span></span>


<span data-ttu-id="d9f6b-155">Todos os dispositivos de realidade misturada com base no Windows se beneficiar o ecossistema de entrada disponível para Windows, incluindo o mouse, teclado, gamepads e muito mais.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-155">All Windows-based mixed reality devices benefit from the input ecosystem available to Windows, including mouse, keyboard, gamepads, and more.</span></span> <span data-ttu-id="d9f6b-156">Com o HoloLens, [Acessórios de hardware](hardware-accessories.md) estão conectados via Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-156">With HoloLens, [hardware accessories](hardware-accessories.md) are connected via Bluetooth.</span></span> <span data-ttu-id="d9f6b-157">Com fones imersivos em exposição, Acessórios conecte-se ao PC host via Bluetooth, USB e outros protocolos com suporte.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-157">With immersive headsets, accessories connect to the host PC via Bluetooth, USB, and other supported protocols.</span></span>

<span data-ttu-id="d9f6b-158">Os recursos de compreensão ambientais, como [coordenadas](coordinate-systems.md), [espacial som](spatial-sound.md), e [mapeamento espacial](spatial-mapping.md) fornecem os recursos necessários para misturar a realidade.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-158">The environmental understanding features like [coordinates](coordinate-systems.md), [spatial sound](spatial-sound.md), and [spatial mapping](spatial-mapping.md) provide the necessary capabilities for mixing reality.</span></span> <span data-ttu-id="d9f6b-159">Mapeamento espacial é exclusivo para o HoloLens e permite hologramas interagir com o usuário e o mundo físico ao redor deles.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-159">Spatial mapping is unique to HoloLens, and enables holograms to interact with both the user and the physical world around them.</span></span> <span data-ttu-id="d9f6b-160">Sistemas de coordenadas permitem que o movimento do usuário afetar o movimento no mundo digital.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-160">Coordinate systems allow the user's movement to affect movement in the digital world.</span></span>

<span data-ttu-id="d9f6b-161">[Hologramas](hologram.md) são feitas de luz e som, que contam [renderização holográfica](rendering.md).</span><span class="sxs-lookup"><span data-stu-id="d9f6b-161">[Holograms](hologram.md) are made of light and sound, which rely on [holographic rendering](rendering.md).</span></span> <span data-ttu-id="d9f6b-162">Noções básicas sobre a experiência de posicionamento e persistência, conforme demonstrado a [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) (às vezes chamado de "shell") é uma ótima maneira Proteja-se na experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-162">Understanding the experience of placement and persistence, as demonstrated in the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) (sometimes called the "shell") is a great way ground yourself in the user experience.</span></span>

## <a name="tools-for-developing-for-mixed-reality"></a><span data-ttu-id="d9f6b-163">Ferramentas de desenvolvimento para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="d9f6b-163">Tools for developing for mixed reality</span></span>

<span data-ttu-id="d9f6b-164">As ferramentas que você usar dependerá do [estilo de aplicativo](app-views.md) você deseja compilar.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-164">The tools you use will depend on the [style of app](app-views.md) you want to build.</span></span>
* <span data-ttu-id="d9f6b-165">[Aplicativos com uma exibição 2D](building-2d-apps.md) aproveite as ferramentas para criação de aplicativos da plataforma Universal do Windows adequada para ambientes, como tablets, PC e Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-165">[Apps with a 2D view](building-2d-apps.md) leverage tools for building Universal Windows Platform apps suited for environments like Windows Phone, PC, and tablets.</span></span> <span data-ttu-id="d9f6b-166">Esses aplicativos têm experiência como 2D projeções colocadas no Windows Mixed Reality doméstica e podem funcionar através de vários tipos de dispositivos (incluindo o telefone e PC).</span><span class="sxs-lookup"><span data-stu-id="d9f6b-166">These apps are experienced as 2D projections placed in the Windows Mixed Reality home, and can work across multiple device types (including phone and PC).</span></span>
* <span data-ttu-id="d9f6b-167">Aplicativos envolventes e holográfico precisam de ferramentas projetadas para tirar proveito das APIs de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-167">Immersive and holographic apps need tools designed to take advantage of the Windows Mixed Reality APIs.</span></span> <span data-ttu-id="d9f6b-168">Estamos [recomendável usar o Unity](unity-development-overview.md) para criar aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="d9f6b-168">We [recommend using Unity](unity-development-overview.md) to build mixed reality apps.</span></span> <span data-ttu-id="d9f6b-169">Os desenvolvedores interessados em criar sua próprias mecanismo podem [usar DirectX e outras APIs do Windows](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9f6b-169">Developers interested in building their own engine can [use DirectX and other Windows APIs](directx-development-overview.md).</span></span>

<span data-ttu-id="d9f6b-170">Independentemente do tipo de aplicativo que você está compilando, essas ferramentas facilitará a sua experiência de desenvolvimento de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d9f6b-170">Regardless of the type of app you're building, these tools will facilitate your app development experience:</span></span>
* [<span data-ttu-id="d9f6b-171">O Visual Studio e o SDK do Windows</span><span class="sxs-lookup"><span data-stu-id="d9f6b-171">Visual Studio and the Windows SDK</span></span>](using-visual-studio.md)
* [<span data-ttu-id="d9f6b-172">Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="d9f6b-172">Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* <span data-ttu-id="d9f6b-173">[Emulador do HoloLens](using-the-hololens-emulator.md) (emulador do HoloLens 2 em breve)</span><span class="sxs-lookup"><span data-stu-id="d9f6b-173">[HoloLens emulator](using-the-hololens-emulator.md) (HoloLens 2 emulator coming soon)</span></span>
* [<span data-ttu-id="d9f6b-174">Simulador de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="d9f6b-174">Windows Mixed Reality simulator</span></span>](using-the-windows-mixed-reality-simulator.md)
* [<span data-ttu-id="d9f6b-175">Critérios de qualidade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d9f6b-175">App quality criteria</span></span>](app-quality-criteria.md)

## <a name="see-also"></a><span data-ttu-id="d9f6b-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9f6b-176">See also</span></span>
* [<span data-ttu-id="d9f6b-177">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="d9f6b-177">Install the tools</span></span>](install-the-tools.md)
* <span data-ttu-id="d9f6b-178"><a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Serviços de realidade misturada</a></span><span class="sxs-lookup"><span data-stu-id="d9f6b-178"><a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Mixed reality services</a></span></span>
* [<span data-ttu-id="d9f6b-179">Tutoriais de realidade mistas</span><span class="sxs-lookup"><span data-stu-id="d9f6b-179">Mixed Reality tutorials</span></span>](academy.md)
* [<span data-ttu-id="d9f6b-180">Projetos de software livre</span><span class="sxs-lookup"><span data-stu-id="d9f6b-180">Open source projects</span></span>](open-source-projects.md)
* [<span data-ttu-id="d9f6b-181">Noções básicas sobre MR 100: Guia de Introdução com o Unity</span><span class="sxs-lookup"><span data-stu-id="d9f6b-181">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="d9f6b-182">Diretrizes de compatibilidade de hardware do Windows Mixed Reality mínimas PC</span><span class="sxs-lookup"><span data-stu-id="d9f6b-182">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [<span data-ttu-id="d9f6b-183">Enviar um aplicativo para a Windows Store</span><span class="sxs-lookup"><span data-stu-id="d9f6b-183">Submitting an app to the Windows Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
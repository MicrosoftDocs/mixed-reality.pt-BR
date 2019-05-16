---
title: Critérios de qualidade do aplicativo
description: Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: critérios de qualidade do aplicativo, realidade, misturada misto de aplicativo de realidade
ms.openlocfilehash: e9f6cd5a6017e11cd167c8141d29b82f89af08e4
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628985"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="804a3-104">Critérios de qualidade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="804a3-104">App quality criteria</span></span>

<span data-ttu-id="804a3-105">Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="804a3-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="804a3-106">Para cada fator as informações a seguir são fornecidas</span><span class="sxs-lookup"><span data-stu-id="804a3-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="804a3-107">Visão geral – uma breve descrição de como o fator de qualidade e por que é importante.</span><span class="sxs-lookup"><span data-stu-id="804a3-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="804a3-108">Impacto do dispositivo - qual tipo de dispositivo de realidade misturada da janela é afetado.</span><span class="sxs-lookup"><span data-stu-id="804a3-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="804a3-109">Critérios de qualidade – como avaliar o fator de qualidade.</span><span class="sxs-lookup"><span data-stu-id="804a3-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="804a3-110">Como medir – métodos de medir (ou experiência) o problema.</span><span class="sxs-lookup"><span data-stu-id="804a3-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="804a3-111">Recomendações – resumidas das abordagens para proporcionar uma melhor experiência de usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="804a3-112">Recursos – desenvolvedor relevante e recursos de design que são úteis para criar melhores experiências de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="804a3-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="804a3-113">Taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="804a3-113">Frame rate</span></span>

<span data-ttu-id="804a3-114">Taxa de quadros é o primeiro pilar de conforto holograma de estabilidade e o usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="804a3-115">Taxa de quadros abaixo os destinos de recomendada pode causar hologramas apareçam instável, afetando negativamente a credibilidade da experiência e possivelmente causando fadiga olho.</span><span class="sxs-lookup"><span data-stu-id="804a3-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="804a3-116">A taxa de quadros de destino para a sua experiência em fones imersivos em exposição Windows Mixed Reality será 60Hz ou 90Hz, dependendo de quais computadores de compatível com Windows misto realidade você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="804a3-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="804a3-117">Para HoloLens a taxa de quadros de destino é 60Hz.</span><span class="sxs-lookup"><span data-stu-id="804a3-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-118">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-120"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-121">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="804a3-122">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-123">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-123">Quality criteria</span></span>

|  <span data-ttu-id="804a3-124">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-124">Best</span></span>  |  <span data-ttu-id="804a3-125">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-125">Meets</span></span> |  <span data-ttu-id="804a3-126">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="804a3-127">O aplicativo atender consistentemente quadros por segundo objetivo (FPS) para o dispositivo de destino: 60fps em HoloLens; 90fps em PCs Ultra; e 60fps em PCs de base.</span><span class="sxs-lookup"><span data-stu-id="804a3-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="804a3-128">O aplicativo tem descartes de intermitente de quadro não prejudicam a experiência de principal; ou FPS é consistentemente inferiores a meta desejada, mas não impessa a experiência de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="804a3-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="804a3-129">O aplicativo está passando por uma queda na taxa de quadros em média a cada dez segundos ou menos.</span><span class="sxs-lookup"><span data-stu-id="804a3-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="804a3-130">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-130">How to measure</span></span>

* <span data-ttu-id="804a3-131">Um gráfico de taxa de quadro em tempo real é fornecido por meio de pela [Windows Device Portal](using-the-windows-device-portal.md#system-performance) sob "Desempenho do sistema".</span><span class="sxs-lookup"><span data-stu-id="804a3-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="804a3-132">Para desenvolvimento de depuração, adicione um contador de diagnóstico de taxa de quadros no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="804a3-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="804a3-133">Consulte os recursos de um contador de exemplo.</span><span class="sxs-lookup"><span data-stu-id="804a3-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="804a3-134">Descartes de taxa de quadros podem ser experimentadas no dispositivo, enquanto o aplicativo está em execução, movendo sua cabeça de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="804a3-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="804a3-135">Se o holograma mostra movimentação trêmulo inesperada, em seguida, baixa taxa de quadros ou o plano de estabilidade provavelmente é a causa.</span><span class="sxs-lookup"><span data-stu-id="804a3-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-136">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-136">Recommendations</span></span>

* <span data-ttu-id="804a3-137">Adicione um contador da taxa de quadros no início do trabalho de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="804a3-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="804a3-138">As alterações que incorrem em uma queda na taxa de quadros devem ser avaliadas e resolvidas adequadamente como um bug de desempenho.</span><span class="sxs-lookup"><span data-stu-id="804a3-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-140">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-140">Documentation</span></span>

* [<span data-ttu-id="804a3-141">Noções básicas sobre desempenho para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="804a3-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="804a3-142">Taxa de quadros e a estabilidade de holograma</span><span class="sxs-lookup"><span data-stu-id="804a3-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="804a3-143">Orçamento de desempenho de ativos</span><span class="sxs-lookup"><span data-stu-id="804a3-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="804a3-144">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="804a3-145">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="804a3-145">Tools and tutorials</span></span>

* [<span data-ttu-id="804a3-146">MRToolkit, exibição de contador FPS</span><span class="sxs-lookup"><span data-stu-id="804a3-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="804a3-147">MRToolkit, sombreadores</span><span class="sxs-lookup"><span data-stu-id="804a3-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="804a3-148">Referências externas</span><span class="sxs-lookup"><span data-stu-id="804a3-148">External references</span></span>

* [<span data-ttu-id="804a3-149">Unity, otimização de aplicativos móveis</span><span class="sxs-lookup"><span data-stu-id="804a3-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="804a3-150">Estabilidade holograma</span><span class="sxs-lookup"><span data-stu-id="804a3-150">Hologram stability</span></span>

<span data-ttu-id="804a3-151">Hologramas estáveis aumentar a usabilidade e a credibilidade do seu aplicativo e criar uma experiência de exibição mais à vontade para o usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="804a3-152">A qualidade da estabilidade holograma é um resultado de desenvolvimento de aplicativos boa e capacidade do dispositivo entender (faixa) seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="804a3-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="804a3-153">Embora a taxa de quadros é o primeiro pilar de estabilidade, outros fatores podem afetar a estabilidade incluindo:</span><span class="sxs-lookup"><span data-stu-id="804a3-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="804a3-154">Uso do plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="804a3-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="804a3-155">Distância até âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="804a3-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="804a3-156">Acompanhamento</span><span class="sxs-lookup"><span data-stu-id="804a3-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-157">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-159"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-160">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-161">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-161">Quality criteria</span></span>

|  <span data-ttu-id="804a3-162">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-162">Best</span></span>  |  <span data-ttu-id="804a3-163">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-163">Meets</span></span> |  <span data-ttu-id="804a3-164">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-165">Hologramas consistentemente aparecem estáveis.</span><span class="sxs-lookup"><span data-stu-id="804a3-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="804a3-166">Exibe o conteúdo secundário movimentação inesperada; ou movimentação inesperada não impede a experiência geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="804a3-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="804a3-167">Conteúdo principal em quadro exibe movimentação inesperada.</span><span class="sxs-lookup"><span data-stu-id="804a3-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="804a3-168">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-168">How to measure</span></span>

<span data-ttu-id="804a3-169">Ao mesmo tempo usando o dispositivo e a experiência de exibição:</span><span class="sxs-lookup"><span data-stu-id="804a3-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="804a3-170">Mover sua cabeça de lado a lado, se o hologramas mostram a movimentação inesperada, em seguida, baixa taxa de quadros ou alinhamento incorreto do plano de estabilidade para o plano focal é a causa provável.</span><span class="sxs-lookup"><span data-stu-id="804a3-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="804a3-171">Mover-se o ambiente e hologramas, procure comportamentos como raias e jumpiness.</span><span class="sxs-lookup"><span data-stu-id="804a3-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="804a3-172">Esse tipo de movimento provavelmente é causado pelo dispositivo não controla o ambiente ou a distância para a âncora espacial.</span><span class="sxs-lookup"><span data-stu-id="804a3-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="804a3-173">Se for grande ou vários hologramas estão no quadro, observar o comportamento de holograma em várias intensidades enquanto mover sua posição principal de lado a lado, se shakiness for exibida, isso provavelmente causado por plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="804a3-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="804a3-174">Recomendações de</span><span class="sxs-lookup"><span data-stu-id="804a3-174">Recomendations</span></span>

* <span data-ttu-id="804a3-175">Adicione um contador da taxa de quadros no início do trabalho de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="804a3-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="804a3-176">Use o plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="804a3-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="804a3-177">Sempre processa hologramas ancoradas dentro de 3 medidores de sua âncora.</span><span class="sxs-lookup"><span data-stu-id="804a3-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="804a3-178">Verifique se o que seu ambiente está configurado para o controle apropriado.</span><span class="sxs-lookup"><span data-stu-id="804a3-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="804a3-179">Projetar sua experiência para evitar hologramas em vários níveis de profundidade focal dentro do quadro.</span><span class="sxs-lookup"><span data-stu-id="804a3-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-180">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-181">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-181">Documentation</span></span>

* [<span data-ttu-id="804a3-182">Taxa de quadros e a estabilidade de holograma</span><span class="sxs-lookup"><span data-stu-id="804a3-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="804a3-183">Estudo de caso, usando o plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="804a3-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="804a3-184">Noções básicas sobre desempenho para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="804a3-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="804a3-185">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="804a3-186">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="804a3-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="804a3-187">Rastreamento de tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="804a3-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="804a3-188">Quadro estacionário de referência</span><span class="sxs-lookup"><span data-stu-id="804a3-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="804a3-189">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="804a3-189">Tools and tutorials</span></span>

* [<span data-ttu-id="804a3-190">Kit de complementar MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="804a3-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="804a3-191">Posição hologramas em superfícies real</span><span class="sxs-lookup"><span data-stu-id="804a3-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="804a3-192">Misalignments de hologramas com objetos físicos (se se destina a ser colocado em relação a um outro) é uma indicação clara do que a não-união hologramas e reais.</span><span class="sxs-lookup"><span data-stu-id="804a3-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="804a3-193">Precisão da colocação deve ser relativo às necessidades do cenário. Por exemplo, posicionamento superfície geral pode usar o mapa espacial, mas o posicionamento mais preciso exigirá algum uso de marcadores e de calibração.</span><span class="sxs-lookup"><span data-stu-id="804a3-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-194">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-196"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-197">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-198">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-198">Quality criteria</span></span>

|  <span data-ttu-id="804a3-199">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-199">Best</span></span>  |  <span data-ttu-id="804a3-200">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-200">Meets</span></span> |  <span data-ttu-id="804a3-201">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="804a3-202">Hologramas alinham para a superfície normalmente nos centímetros para intervalo polegadas.</span><span class="sxs-lookup"><span data-stu-id="804a3-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="804a3-203">Se mais precisão for necessária, o aplicativo deve fornecer um meio eficaz para colaboração entre as especificações do aplicativo desejado.</span><span class="sxs-lookup"><span data-stu-id="804a3-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="804a3-204">N/D</span><span class="sxs-lookup"><span data-stu-id="804a3-204">NA</span></span> | <span data-ttu-id="804a3-205">As hologramas aparecem não alinhadas com o objeto de destino físico, quebrando o plano de superfície ou que aparecem para float para fora da superfície de.</span><span class="sxs-lookup"><span data-stu-id="804a3-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="804a3-206">Se a precisão for necessária, hologramas devem atender a especificação de proximidade do cenário.</span><span class="sxs-lookup"><span data-stu-id="804a3-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="804a3-207">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-207">How to measure</span></span>

* <span data-ttu-id="804a3-208">Hologramas que são colocadas no mapa espacial não devem aparecer drasticamente flutuando acima ou abaixo da superfície.</span><span class="sxs-lookup"><span data-stu-id="804a3-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="804a3-209">Hologramas que exigem colocação precisa devem ter alguma forma de marcador e calibragem sistema que tem a precisão do requisito do cenário.</span><span class="sxs-lookup"><span data-stu-id="804a3-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-210">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-210">Recommendations</span></span>

* <span data-ttu-id="804a3-211">Mapa espacial é útil para colocar objetos em superfícies quando a precisão não é necessária.</span><span class="sxs-lookup"><span data-stu-id="804a3-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="804a3-212">Para obter a melhor precisão, use marcadores ou cartazes para definir as hologramas e um controlador do Xbox (ou algum mecanismo de alinhamento manual) para calibragem final.</span><span class="sxs-lookup"><span data-stu-id="804a3-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="804a3-213">Considere dividir hologramas extra grandes em partes lógicas e alinhar cada parte para a superfície.</span><span class="sxs-lookup"><span data-stu-id="804a3-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="804a3-214">Incorretamente conjunto interpupilary distância (IPD) também pode afetar o alinhamento de holograma.</span><span class="sxs-lookup"><span data-stu-id="804a3-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="804a3-215">Sempre configure HoloLens para IPD do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-216">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-217">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-217">Documentation</span></span>

* [<span data-ttu-id="804a3-218">Posicionamento de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="804a3-219">Processo de verificação de espaço</span><span class="sxs-lookup"><span data-stu-id="804a3-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="804a3-220">Práticas recomendadas de âncoras espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="804a3-221">Rastreamento de tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="804a3-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="804a3-222">Mapeamento espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="804a3-223">Visão geral do desenvolvimento Vuforia</span><span class="sxs-lookup"><span data-stu-id="804a3-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="804a3-224">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="804a3-224">Tools and tutorials</span></span>

* [<span data-ttu-id="804a3-225">MR Espacial 230: mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="804a3-226">MR o Kit de ferramentas, bibliotecas de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="804a3-227">Kit de complementar MR, exemplo de calibragem de pôster</span><span class="sxs-lookup"><span data-stu-id="804a3-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="804a3-228">Kit de complementar MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="804a3-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="804a3-229">Referências externas</span><span class="sxs-lookup"><span data-stu-id="804a3-229">External references</span></span>

* [<span data-ttu-id="804a3-230">Estudo de caso de Lowes, alinhamento de precisão</span><span class="sxs-lookup"><span data-stu-id="804a3-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="804a3-231">Exibição de zona de conforto</span><span class="sxs-lookup"><span data-stu-id="804a3-231">Viewing zone of comfort</span></span>

<span data-ttu-id="804a3-232">Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergirem colocando conteúdo e hologramas em várias intensidades.</span><span class="sxs-lookup"><span data-stu-id="804a3-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="804a3-233">Os usuários vestindo HoloLens sempre acomodará 2.0 m para manter uma imagem clara como HoloLens exibe são corrigidos em uma distância óptica aproximadamente 2.0m do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="804a3-234">Profundidade do conteúdo inadequada pode levar a discomfort visual ou fadiga.</span><span class="sxs-lookup"><span data-stu-id="804a3-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-235">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-237"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-238">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-239">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="804a3-240">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="804a3-241">Colocar o conteúdo em 2m.</span><span class="sxs-lookup"><span data-stu-id="804a3-241">Place content at 2m.</span></span></li><li><span data-ttu-id="804a3-242">Quando hologramas não podem ser colocadas em 2m, e não podem ser evitados conflitos entre a convergência e acomodação, a zona ideal para posicionamento holograma é entre 1,25 milhões e milhões de 5.</span><span class="sxs-lookup"><span data-stu-id="804a3-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="804a3-243">Em todos os casos, designers devem estruturar o conteúdo a fim de incentivar os usuários interajam 1 + m imediatamente (por exemplo, ajustar o tamanho do conteúdo e padrão de parâmetros de posicionamento).</span><span class="sxs-lookup"><span data-stu-id="804a3-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="804a3-244">A menos que especificamente não exigido pelo cenário, um plano de corte deve ser implementar com fadeout começando em 1 milhão.</span><span class="sxs-lookup"><span data-stu-id="804a3-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="804a3-245">Em casos onde uma observação mais próxima de um holograma imóvel é necessária, o conteúdo não deve ser mais próximo do que 50cm.</span><span class="sxs-lookup"><span data-stu-id="804a3-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="804a3-246">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-246">Meets</span></span></td><td> <span data-ttu-id="804a3-247">O conteúdo é dentro a orientação de exibição e movimento, mas o uso inadequado ou nenhum uso do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="804a3-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="804a3-248">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-248">Fail</span></span> </td><td> <span data-ttu-id="804a3-249">O conteúdo é apresentado muito próximas (normalmente &lt;1,25 m, ou &lt;50 cm para hologramas estáticos que exigem mais próxima Observação.)</span><span class="sxs-lookup"><span data-stu-id="804a3-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="804a3-250">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-250">How to measure</span></span>

* <span data-ttu-id="804a3-251">Conteúdo deve ser 2m geralmente ausente, mas não mais próximo que 1,25 ou mais de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="804a3-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="804a3-252">Com poucas exceções, a distância de renderização de recorte do HoloLens deve ser definida como .85CM com fadeout começando em 1 milhão de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="804a3-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="804a3-253">Abordar o conteúdo e observe o efeito de plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="804a3-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="804a3-254">Conteúdo estático não deve ficar mais próximo do que 50cm de distância.</span><span class="sxs-lookup"><span data-stu-id="804a3-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-255">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-255">Recommendations</span></span>

* <span data-ttu-id="804a3-256">Criar conteúdo para a distância de exibição ideal de 2M.</span><span class="sxs-lookup"><span data-stu-id="804a3-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="804a3-257">Defina a distância de renderização de recorte para 85cm com fadeout começando em 1 milhão de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="804a3-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="804a3-258">Para hologramas estacionários que precisam exibir mais próximo, o plano de corte deve ser não mais próximo do que 30cm e fadeout deve começar pelo menos 10cm para longe do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="804a3-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-259">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-259">Resources</span></span>

* [<span data-ttu-id="804a3-260">Renderizar distância</span><span class="sxs-lookup"><span data-stu-id="804a3-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="804a3-261">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="804a3-262">Experimentar a escala</span><span class="sxs-lookup"><span data-stu-id="804a3-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="804a3-263">Texto, tamanho da fonte recomendado</span><span class="sxs-lookup"><span data-stu-id="804a3-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="804a3-264">Alternância de profundidade</span><span class="sxs-lookup"><span data-stu-id="804a3-264">Depth switching</span></span>

<span data-ttu-id="804a3-265">Independentemente da zona de exibição de problemas de conforto, as exigências do usuário alterne rapidamente ou com frequência entre quase e muito focal objetos (incluindo hologramas e conteúdo do mundo real) podem levar a fadiga oculomotor e discomfort geral.</span><span class="sxs-lookup"><span data-stu-id="804a3-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-266">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-268"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-269">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="804a3-270">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-271">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-271">Quality criteria</span></span>

|  <span data-ttu-id="804a3-272">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-272">Best</span></span>  |  <span data-ttu-id="804a3-273">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-273">Meets</span></span> |  <span data-ttu-id="804a3-274">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-275">Profundidade natural ou limitada alternância que não fazem com que o usuário se concentre em unnaturally.</span><span class="sxs-lookup"><span data-stu-id="804a3-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="804a3-276">Comutador de profundidade abrupta esse é o núcleo e projetado para a experiência de aplicativo, ou comutador de profundidade abrupta causada por conteúdo inesperado do mundo real.</span><span class="sxs-lookup"><span data-stu-id="804a3-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="804a3-277">Comutador de profundidade consistente, ou profundidade abrupta alternância que não é necessário ou núcleo para a experiência de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="804a3-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="804a3-278">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-278">How to measure</span></span>

* <span data-ttu-id="804a3-279">Se o aplicativo requer que o usuário para consistentemente e/ou abruptamente mudar o foco de profundidade, não há profundidade, alternando o problema.</span><span class="sxs-lookup"><span data-stu-id="804a3-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-280">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-280">Recommendations</span></span>

* <span data-ttu-id="804a3-281">Manter o conteúdo principal em um plano focal consistente e verifique se que o plano de estabilização corresponde ao plano focal.</span><span class="sxs-lookup"><span data-stu-id="804a3-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="804a3-282">Isso irá aliviar fadiga oculomotor e movimentação holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="804a3-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-283">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-283">Resources</span></span>

* [<span data-ttu-id="804a3-284">Renderizar distância</span><span class="sxs-lookup"><span data-stu-id="804a3-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="804a3-285">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="804a3-286">Uso de som espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-286">Use of spatial sound</span></span>

<span data-ttu-id="804a3-287">Na realidade mista do Windows, o mecanismo de áudio fornece o componente auricular da experiência de realidade misturada, simulando 3D som usando simulações ambientais, distância e direção.</span><span class="sxs-lookup"><span data-stu-id="804a3-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="804a3-288">Usando o som espacial em um aplicativo permite aos desenvolvedores colocar convincingly sons em um espaço dimensional 3 (esfera) em todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="804a3-289">Os sons, em seguida, parecerá como se eles foram provenientes de objetos físicos real ou as hologramas de realidade misturada no ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="804a3-290">Som espacial é uma ferramenta poderosa para uma imersão, acessibilidade e design UX em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="804a3-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-291">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-293"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-294">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="804a3-295">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-296">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-296">Quality criteria</span></span>

|  <span data-ttu-id="804a3-297">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-297">Best</span></span>  |  <span data-ttu-id="804a3-298">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-298">Meets</span></span> |  <span data-ttu-id="804a3-299">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-300">Som é logicamente spatialized e a experiência do usuário adequadamente usa som para ajudá-lo com comentários de usuário e a descoberta de objeto.</span><span class="sxs-lookup"><span data-stu-id="804a3-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="804a3-301">Som é natural e relevantes para objetos e normalizada entre o cenário.</span><span class="sxs-lookup"><span data-stu-id="804a3-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="804a3-302">Áudio espacial é usada adequadamente para credibilidade mas ausente como meio para ajudar com a capacidade de descoberta e comentários do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="804a3-303">Som não é spatialized conforme o esperado, e/ou falta de som para auxiliar o usuário dentro a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="804a3-304">Ou áudio espacial não foi considerado ou usado no design do cenário.</span><span class="sxs-lookup"><span data-stu-id="804a3-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="804a3-305">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-305">How to measure</span></span>

* <span data-ttu-id="804a3-306">Em geral, os sons relevantes devem emitir de hologramas de destino (por exemplo,., som latido provenientes de dog holográfica.)</span><span class="sxs-lookup"><span data-stu-id="804a3-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="804a3-307">Indicações de som devem ser usadas em toda a experiência do usuário para ajudar o usuário com reconhecimento de ações fora do quadro holográfica ou comentários.</span><span class="sxs-lookup"><span data-stu-id="804a3-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-308">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-308">Recommendations</span></span>

* <span data-ttu-id="804a3-309">Use o áudio espacial para ajudá-lo com interfaces de usuário e a descoberta de objeto.</span><span class="sxs-lookup"><span data-stu-id="804a3-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="804a3-310">Sons real funcionam melhor do que sintetização ou som não natural.</span><span class="sxs-lookup"><span data-stu-id="804a3-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="804a3-311">A maioria dos sons devem ser spatialized.</span><span class="sxs-lookup"><span data-stu-id="804a3-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="804a3-312">Evite os emissores invisíveis.</span><span class="sxs-lookup"><span data-stu-id="804a3-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="804a3-313">Evite mascaramento espacial.</span><span class="sxs-lookup"><span data-stu-id="804a3-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="804a3-314">Normalize todos os sons.</span><span class="sxs-lookup"><span data-stu-id="804a3-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-315">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-316">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-316">Documentation</span></span>

* [<span data-ttu-id="804a3-317">Som espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="804a3-318">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="804a3-319">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="804a3-320">Estudo de caso, espacial som para HoloTour</span><span class="sxs-lookup"><span data-stu-id="804a3-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="804a3-321">Estudo de caso, usando o som espacial RoboRaid</span><span class="sxs-lookup"><span data-stu-id="804a3-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="804a3-322">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="804a3-322">Tools and tutorials</span></span>

* [<span data-ttu-id="804a3-323">MR Espacial 220: som espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="804a3-324">MRToolkit, áudio espacial</span><span class="sxs-lookup"><span data-stu-id="804a3-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="804a3-325">Concentre-se em limites de quadro holográfica (FOV)</span><span class="sxs-lookup"><span data-stu-id="804a3-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="804a3-326">Experiências de usuário bem projetado podem criar e manter o contexto úteis do ambiente virtual que se estende em torno dos usuários.</span><span class="sxs-lookup"><span data-stu-id="804a3-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="804a3-327">Reduzir o efeito dos limites FOV envolve um design elaborado de escala de conteúdo e contexto, o uso de áudio espacial, sistemas de orientação e a posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="804a3-328">Se feito corretamente, o usuário se sentirão que menor prejudicada por limites de FOV tendo uma experiência de aplicativo à vontade.</span><span class="sxs-lookup"><span data-stu-id="804a3-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-329">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-331"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-332">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-333">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-333">Quality criteria</span></span>

|  <span data-ttu-id="804a3-334">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-334">Best</span></span>  |  <span data-ttu-id="804a3-335">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-335">Meets</span></span> |  <span data-ttu-id="804a3-336">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-337">Usuário nunca perde o contexto e exibição se sente confortável.</span><span class="sxs-lookup"><span data-stu-id="804a3-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="804a3-338">Assistência de contexto é fornecida para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="804a3-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="804a3-339">Detectabilidade e exibindo a orientação é fornecida para objetos fora do quadro.</span><span class="sxs-lookup"><span data-stu-id="804a3-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="804a3-340">Em geral, o design de movimento e a escala das hologramas são apropriadas para uma experiência visual confortável.</span><span class="sxs-lookup"><span data-stu-id="804a3-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="804a3-341">Usuário nunca perde o contexto, mas o movimento do pescoço extra pode ser necessário em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="804a3-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="804a3-342">Em algumas situações escala faz com que hologramas quebrar tanto o quadro vertical ou horizontal, fazendo com que algum movimento pescoço exibir hologramas.</span><span class="sxs-lookup"><span data-stu-id="804a3-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="804a3-343">Usuário poderá perder o contexto e/ou movimento do pescoço consistente é necessária para exibir hologramas.</span><span class="sxs-lookup"><span data-stu-id="804a3-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="804a3-344">Nenhuma orientação de contexto para objetos grandes holográfica, mover objetos muito fácil perder fora do quadro sem diretrizes de capacidade de descoberta ou a altura hologramas requer movimento pescoço regular para exibir.</span><span class="sxs-lookup"><span data-stu-id="804a3-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="804a3-345">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-345">How to measure</span></span>

* <span data-ttu-id="804a3-346">Contexto para um holograma (grande) for perdido ou não é compreendido devido ao que está sendo cortado nos limites.</span><span class="sxs-lookup"><span data-stu-id="804a3-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="804a3-347">Local do hologramas são difíceis de encontrar devido à falta de diretores de atenção ou conteúdo que se move rapidamente para dentro e fora do quadro holográfico.</span><span class="sxs-lookup"><span data-stu-id="804a3-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="804a3-348">Cenário requer regular e repetitivas para cima e para a animação principal para ver totalmente um holograma resultando em fadiga pescoço.</span><span class="sxs-lookup"><span data-stu-id="804a3-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-349">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-349">Recommendations</span></span>

* <span data-ttu-id="804a3-350">Inicie a experiência com objetos pequenos que se ajustar a FOV, em seguida, fazer a transição com visuais para versões maiores.</span><span class="sxs-lookup"><span data-stu-id="804a3-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="804a3-351">Use espaciais diretores de áudio e atenção para conteúdo de localizar o usuário que está fora do FOV da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="804a3-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="804a3-352">Tanto quanto possível, evite hologramas que recortar verticalmente o FOV.</span><span class="sxs-lookup"><span data-stu-id="804a3-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="804a3-353">Fornece ao usuário uma diretriz no aplicativo para melhor visualização local.</span><span class="sxs-lookup"><span data-stu-id="804a3-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-354">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-355">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-355">Documentation</span></span>

* [<span data-ttu-id="804a3-356">Quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="804a3-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="804a3-357">Estudo de caso, a UI HoloStudio e lições aprendidas de design de interação</span><span class="sxs-lookup"><span data-stu-id="804a3-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="804a3-358">Escala de objetos e ambientes</span><span class="sxs-lookup"><span data-stu-id="804a3-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="804a3-359">Cursores, indicações visuais</span><span class="sxs-lookup"><span data-stu-id="804a3-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="804a3-360">Referências externas</span><span class="sxs-lookup"><span data-stu-id="804a3-360">External references</span></span>

* [<span data-ttu-id="804a3-361">Muitos ados sobre o FOV</span><span class="sxs-lookup"><span data-stu-id="804a3-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="804a3-362">Conteúdo reage a posição do usuário</span><span class="sxs-lookup"><span data-stu-id="804a3-362">Content reacts to user position</span></span>

<span data-ttu-id="804a3-363">Hologramas devem reagir para a posição do usuário aproximadamente da mesma maneira que objetos de "real".</span><span class="sxs-lookup"><span data-stu-id="804a3-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="804a3-364">Uma consideração de design importantes é a elementos de interface do usuário que não não necessariamente assumem que a posição de um usuário está parados e adaptar-se a animação do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="804a3-365">Criação de um aplicativo que corretamente se adapta a posição de usuário criar uma experiência mais verossímeis e torná-lo mais fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="804a3-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-366">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-368"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-369">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="804a3-370">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-371">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="804a3-372">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-372">Best</span></span> </td><td> <span data-ttu-id="804a3-373">Conteúdo e a interface do usuário se adaptar às posições de usuário, permitindo que o usuário interagir naturalmente com o conteúdo dentro do escopo de movimentação do usuário esperado.</span><span class="sxs-lookup"><span data-stu-id="804a3-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="804a3-374">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-374">Meets</span></span> </td><td> <span data-ttu-id="804a3-375">Interface do usuário se adapta para a posição do usuário, mas pode impedir a exibição do conteúdo da chave exigir que o usuário ajustar sua posição.</span><span class="sxs-lookup"><span data-stu-id="804a3-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="804a3-376">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="804a3-377">Elementos de interface do usuário são perdidos ou bloqueados durante usuário causando movimentação controles unnaturally retornar a (ou encontrar).</span><span class="sxs-lookup"><span data-stu-id="804a3-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="804a3-378">Elementos de interface do usuário limitam a exibição do conteúdo principal.</span><span class="sxs-lookup"><span data-stu-id="804a3-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="804a3-379">Movimentação da interface do usuário não é otimizada para exibição de distância e momentum particularmente com <a href="billboarding-and-tag-along.md">tag-along</a> elementos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="804a3-380">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-380">How to measure</span></span>

* <span data-ttu-id="804a3-381">Todas as medidas devem ser feitas dentro de um escopo razoável do cenário.</span><span class="sxs-lookup"><span data-stu-id="804a3-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="804a3-382">Enquanto o movimento do usuário irá variar, não tente fazer o aplicativo com a movimentação de usuário extremo.</span><span class="sxs-lookup"><span data-stu-id="804a3-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="804a3-383">Para elementos de interface do usuário, controles relevantes devem estar disponíveis, independentemente de movimentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="804a3-384">Por exemplo, se o usuário está exibindo e andar de um mapa 3D com o zoom, o controle de zoom deve ser prontamente disponível para o usuário, independentemente do local.</span><span class="sxs-lookup"><span data-stu-id="804a3-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-385">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-385">Recommendations</span></span>

* <span data-ttu-id="804a3-386">O usuário é a câmera e eles controlam a movimentação.</span><span class="sxs-lookup"><span data-stu-id="804a3-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="804a3-387">Deixe-os da unidade.</span><span class="sxs-lookup"><span data-stu-id="804a3-387">Let them drive.</span></span>
* <span data-ttu-id="804a3-388">Considere billboarding para texto e os sistemas de menus que caso contrário, seriam bloqueada pelo mundo ou obscurecidos se um usuário eram mover-se.</span><span class="sxs-lookup"><span data-stu-id="804a3-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="804a3-389">Use tag-along conteúdo que precisa acompanhar o usuário enquanto ainda permite que o usuário veja o que está na frente delas.</span><span class="sxs-lookup"><span data-stu-id="804a3-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-390">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-391">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-391">Documentation</span></span>

* [<span data-ttu-id="804a3-392">Design de interação</span><span class="sxs-lookup"><span data-stu-id="804a3-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="804a3-393">Cor, luz e material</span><span class="sxs-lookup"><span data-stu-id="804a3-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="804a3-394">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="804a3-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="804a3-395">Conceitos básicos de interação</span><span class="sxs-lookup"><span data-stu-id="804a3-395">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="804a3-396">O motion Self e locomotion do usuário</span><span class="sxs-lookup"><span data-stu-id="804a3-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="804a3-397">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="804a3-397">Tools and tutorials</span></span>

* [<span data-ttu-id="804a3-398">Entrada do MR 210: foco</span><span class="sxs-lookup"><span data-stu-id="804a3-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="804a3-399">Clareza de interação de entrada</span><span class="sxs-lookup"><span data-stu-id="804a3-399">Input interaction clarity</span></span>

<span data-ttu-id="804a3-400">Clareza de interação de entrada é essencial para facilidade de uso do aplicativo e inclui a entrada consistência, acessibilidade, detectabilidade de métodos de interação.</span><span class="sxs-lookup"><span data-stu-id="804a3-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="804a3-401">Usuário deve ser capaz de usar toda a plataforma de interações comuns sem que eles reaprendessem.</span><span class="sxs-lookup"><span data-stu-id="804a3-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="804a3-402">Se o aplicativo tem uma entrada personalizada, ele deve ser claramente comunicado e demonstrado.</span><span class="sxs-lookup"><span data-stu-id="804a3-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-403">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-405"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-406">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="804a3-407">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-408">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-408">Quality criteria</span></span>

|  <span data-ttu-id="804a3-409">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-409">Best</span></span>  |  <span data-ttu-id="804a3-410">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-410">Meets</span></span> |  <span data-ttu-id="804a3-411">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-412">Métodos de interação de entrada são consistentes com o Windows Mixed Reality fornecidos [orientação](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="804a3-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="804a3-413">Qualquer entrada personalizada não deve ser redundante com a entrada padrão (em vez disso, use padrão interação) e deve ser comunicada claramente e demonstrou que o usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="804a3-414">Semelhante às entradas melhor, mas personalizadas são redundantes com métodos de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="804a3-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="804a3-415">Usuário ainda pode alcançar a meta e o progresso por meio da experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="804a3-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="804a3-416">Difícil de entender o mapeamento de método ou o botão de entrada.</span><span class="sxs-lookup"><span data-stu-id="804a3-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="804a3-417">Entrada é muito personalizado, não dá suporte a entrada padrão, não há instruções, ou pode causar problemas de fadiga e conforto.</span><span class="sxs-lookup"><span data-stu-id="804a3-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="804a3-418">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-418">How to measure</span></span>

* <span data-ttu-id="804a3-419">O aplicativo usa consistente [métodos de entrada padrão.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="804a3-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="804a3-420">Se o aplicativo tem uma entrada de Customer, ele claramente é comunicado por meio de:</span><span class="sxs-lookup"><span data-stu-id="804a3-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="804a3-421">Experiência de primeira execução</span><span class="sxs-lookup"><span data-stu-id="804a3-421">First-run experience</span></span>
* <span data-ttu-id="804a3-422">Telas introdutórias</span><span class="sxs-lookup"><span data-stu-id="804a3-422">Introductory screens</span></span>
* <span data-ttu-id="804a3-423">Dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="804a3-423">Tooltips</span></span>
* <span data-ttu-id="804a3-424">Coach mão</span><span class="sxs-lookup"><span data-stu-id="804a3-424">Hand coach</span></span>
* <span data-ttu-id="804a3-425">Seção de ajuda</span><span class="sxs-lookup"><span data-stu-id="804a3-425">Help section</span></span>
* <span data-ttu-id="804a3-426">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="804a3-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-427">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-427">Recommendations</span></span>

* <span data-ttu-id="804a3-428">Use os métodos de entrada padrão sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="804a3-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="804a3-429">Fornece demonstrações, tutoriais e dicas de ferramenta para métodos de entrada não padrão.</span><span class="sxs-lookup"><span data-stu-id="804a3-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="804a3-430">Use um modelo de interação consistente em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="804a3-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-431">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-432">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-432">Documentation</span></span>

* [<span data-ttu-id="804a3-433">Conceitos básicos de interação de Windows MR</span><span class="sxs-lookup"><span data-stu-id="804a3-433">Windows MR interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="804a3-434">Objetos interagível</span><span class="sxs-lookup"><span data-stu-id="804a3-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="804a3-435">Focar direcionamento</span><span class="sxs-lookup"><span data-stu-id="804a3-435">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="804a3-436">Cursores</span><span class="sxs-lookup"><span data-stu-id="804a3-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="804a3-437">Conforto e olhar</span><span class="sxs-lookup"><span data-stu-id="804a3-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="804a3-438">Gestos</span><span class="sxs-lookup"><span data-stu-id="804a3-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="804a3-439">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="804a3-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="804a3-440">Design de voz</span><span class="sxs-lookup"><span data-stu-id="804a3-440">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="804a3-441">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="804a3-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="804a3-442">Guia de portabilidade de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="804a3-443">Entrada do teclado no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="804a3-444">Foco no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="804a3-445">Gestos e controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="804a3-446">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="804a3-447">Teclado, mouse e entrada do controlador no DirectX</span><span class="sxs-lookup"><span data-stu-id="804a3-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="804a3-448">Cabeçalho e olho olhar no DirectX</span><span class="sxs-lookup"><span data-stu-id="804a3-448">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="804a3-449">Mãos e controladores de movimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="804a3-449">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="804a3-450">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="804a3-450">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="804a3-451">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="804a3-451">Tools and tutorials</span></span>

* [<span data-ttu-id="804a3-452">Estudo de caso: A busca de computação mais pessoais</span><span class="sxs-lookup"><span data-stu-id="804a3-452">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="804a3-453">Estudo de conversão: UI HoloStudio e lições aprendidas de design de interação</span><span class="sxs-lookup"><span data-stu-id="804a3-453">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="804a3-454">Aplicativo de exemplo: Tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="804a3-454">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="804a3-455">Aplicativo de exemplo: Módulo Lunar</span><span class="sxs-lookup"><span data-stu-id="804a3-455">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="804a3-456">Entrada do MR 210: foco</span><span class="sxs-lookup"><span data-stu-id="804a3-456">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="804a3-457">Entrada do MR 211: Gestos</span><span class="sxs-lookup"><span data-stu-id="804a3-457">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="804a3-458">Entrada do MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="804a3-458">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="804a3-459">Objetos interagível</span><span class="sxs-lookup"><span data-stu-id="804a3-459">Interactable objects</span></span>

<span data-ttu-id="804a3-460">Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D.</span><span class="sxs-lookup"><span data-stu-id="804a3-460">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="804a3-461">No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais.</span><span class="sxs-lookup"><span data-stu-id="804a3-461">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="804a3-462">Nada pode ser um objeto Interagível que dispara um evento.</span><span class="sxs-lookup"><span data-stu-id="804a3-462">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="804a3-463">Um objeto interagível pode ser representado como qualquer coisa uma xícara de café na tabela para um balão flutuar no ar.</span><span class="sxs-lookup"><span data-stu-id="804a3-463">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="804a3-464">Independentemente da forma, objetos interagível devem ser claramente reconhecíveis por usuário por meio de indicações de áudio e vídeo.</span><span class="sxs-lookup"><span data-stu-id="804a3-464">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-465">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-465">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-466"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-466"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-467"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-468">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-468">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="804a3-469">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-469">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-470">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-470">Quality criteria</span></span>

|  <span data-ttu-id="804a3-471">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-471">Best</span></span>  |  <span data-ttu-id="804a3-472">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-472">Meets</span></span> |  <span data-ttu-id="804a3-473">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-473">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-474">Independentemente do formulário, objetos interagível são reconhecidos por meio de indicações de áudio e vídeo em três estados: ocioso, direcionadas e selecionado.</span><span class="sxs-lookup"><span data-stu-id="804a3-474">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="804a3-475">"Consulte, diga" é claro e consistente usado em toda a experiência.</span><span class="sxs-lookup"><span data-stu-id="804a3-475">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="804a3-476">Objetos são dimensionados e distribuídos para permitir o direcionamento de sem erros.</span><span class="sxs-lookup"><span data-stu-id="804a3-476">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="804a3-477">Usuário pode reconhecer o objeto como interagível por meio de comentários de áudio ou de visual e de destino e ativar o objeto.</span><span class="sxs-lookup"><span data-stu-id="804a3-477">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="804a3-478">Considerando sem indicações de áudio ou de visual, usuário não pode reconhecer um objeto interagível.</span><span class="sxs-lookup"><span data-stu-id="804a3-478">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="804a3-479">As interações são propenso a falhas devido a escala do objeto ou a distância entre os objetos.</span><span class="sxs-lookup"><span data-stu-id="804a3-479">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="804a3-480">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-480">How to measure</span></span>

* <span data-ttu-id="804a3-481">Objetos interagível podem ser reconhecidos como 'interagível'; incluindo conteúdo específico do aplicativo, menus e botões.</span><span class="sxs-lookup"><span data-stu-id="804a3-481">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="804a3-482">Como regra geral deve haver uma indicação visual e áudio ao direcionar objetos interagível.</span><span class="sxs-lookup"><span data-stu-id="804a3-482">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-483">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-483">Recommendations</span></span>

* <span data-ttu-id="804a3-484">Use comentários de áudio e vídeo para interações.</span><span class="sxs-lookup"><span data-stu-id="804a3-484">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="804a3-485">Feedback visual deve ser diferenciada para cada estado (ocioso, destino, selecionado) de entrada</span><span class="sxs-lookup"><span data-stu-id="804a3-485">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="804a3-486">Objetos interagível devem ser dimensionados e colocados para direcionamento de sem erros.</span><span class="sxs-lookup"><span data-stu-id="804a3-486">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="804a3-487">Os objetos agrupados interagível (por exemplo, uma barra de menus ou lista) devem ter espaçamento correto para o direcionamento.</span><span class="sxs-lookup"><span data-stu-id="804a3-487">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="804a3-488">Botões e menus que dão suporte ao comando de voz devem fornecer rótulos de texto para a palavra-chave de comando ("vê-lo, diga")</span><span class="sxs-lookup"><span data-stu-id="804a3-488">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-489">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-489">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-490">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-490">Documentation</span></span>

* [<span data-ttu-id="804a3-491">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="804a3-491">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="804a3-492">Texto no Unity</span><span class="sxs-lookup"><span data-stu-id="804a3-492">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="804a3-493">Barra de aplicativos e caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="804a3-493">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="804a3-494">Design de voz</span><span class="sxs-lookup"><span data-stu-id="804a3-494">Voice design</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="804a3-495">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="804a3-495">Tools and tutorials</span></span>

* [<span data-ttu-id="804a3-496">Kit de ferramentas de realidade misturada - UX</span><span class="sxs-lookup"><span data-stu-id="804a3-496">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="804a3-497">Espaço disponível para verificação</span><span class="sxs-lookup"><span data-stu-id="804a3-497">Room scanning</span></span>

<span data-ttu-id="804a3-498">Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="804a3-498">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="804a3-499">A integridade e a qualidade dos dados depende de vários fatores, incluindo a quantidade de exploração que o usuário tenha feito, quanto tempo se passou desde a exploração e se os objetos como móveis e portas foram movidas desde a área de verificação de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="804a3-499">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="804a3-500">Muitos aplicativos analisará os dados de mapeamento espacial no início da experiência para avaliar se o usuário deve executar etapas adicionais para melhorar a integridade e a qualidade do mapa espacial.</span><span class="sxs-lookup"><span data-stu-id="804a3-500">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="804a3-501">Se o usuário é necessário para verificar o ambiente, desmarque diretrizes devem ser fornecida durante a experiência de verificação.</span><span class="sxs-lookup"><span data-stu-id="804a3-501">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-502">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-502">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-503"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-503"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-504"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-505">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-505">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-506">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-506">Quality criteria</span></span>

|  <span data-ttu-id="804a3-507">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-507">Best</span></span>  |  <span data-ttu-id="804a3-508">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-508">Meets</span></span> |  <span data-ttu-id="804a3-509">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-509">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-510">Visualização da malha espacial informar os usuários de verificação está em andamento.</span><span class="sxs-lookup"><span data-stu-id="804a3-510">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="804a3-511">Claramente o usuário sabe o que fazer e quando a varredura inicia e para.</span><span class="sxs-lookup"><span data-stu-id="804a3-511">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="804a3-512">Visualização da malha espacial for fornecida, mas o usuário pode não sabe claramente o que fazer e nenhuma informação de progresso é fornecida.</span><span class="sxs-lookup"><span data-stu-id="804a3-512">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="804a3-513">Nenhuma visualização da malha.</span><span class="sxs-lookup"><span data-stu-id="804a3-513">No visualization of mesh.</span></span> <span data-ttu-id="804a3-514">Nenhuma informação de orientação fornecida ao usuário sobre onde procurar, ou quando a varredura inicia/para.</span><span class="sxs-lookup"><span data-stu-id="804a3-514">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="804a3-515">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-515">How to measure</span></span>

* <span data-ttu-id="804a3-516">Durante uma verificação de espaço necessário, são fornecidas orientações de áudio e vídeo que indica onde procurar e quando iniciar e Parar verificação.</span><span class="sxs-lookup"><span data-stu-id="804a3-516">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-517">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-517">Recommendations</span></span>

* <span data-ttu-id="804a3-518">Indica quanto o volume total nas proximidades usuários precisa fazer parte da experiência.</span><span class="sxs-lookup"><span data-stu-id="804a3-518">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="804a3-519">Comunicar-se quando a verificação é iniciado e é interrompido, como um indicador de progresso.</span><span class="sxs-lookup"><span data-stu-id="804a3-519">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="804a3-520">Use uma visualização da malha durante a verificação.</span><span class="sxs-lookup"><span data-stu-id="804a3-520">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="804a3-521">Fornece indicações de áudio e vídeo para incentivar o usuário procure e mover-se na sala.</span><span class="sxs-lookup"><span data-stu-id="804a3-521">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="804a3-522">Informar ao usuário aonde ir para melhorar os dados.</span><span class="sxs-lookup"><span data-stu-id="804a3-522">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="804a3-523">Em muitos casos, talvez seja melhor informar ao usuário o que precisam (por exemplo, examinar o limite, procure por trás de móveis), para obter a qualidade de verificação necessárias.</span><span class="sxs-lookup"><span data-stu-id="804a3-523">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-524">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-524">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="804a3-525">Documentação</span><span class="sxs-lookup"><span data-stu-id="804a3-525">Documentation</span></span>

* [<span data-ttu-id="804a3-526">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="804a3-526">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="804a3-527">Estudo de caso: Expandindo os recursos de mapeamento espacial do HoloLens</span><span class="sxs-lookup"><span data-stu-id="804a3-527">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="804a3-528">Estudo de caso: Projeto de som espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="804a3-528">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="804a3-529">Estudo de caso: Criando uma experiência imersiva em fragmentos</span><span class="sxs-lookup"><span data-stu-id="804a3-529">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="804a3-530">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="804a3-530">Tools and tutorials</span></span>

* [<span data-ttu-id="804a3-531">Kit de ferramentas de realidade misturada - UX</span><span class="sxs-lookup"><span data-stu-id="804a3-531">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="804a3-532">Indicadores direcionais</span><span class="sxs-lookup"><span data-stu-id="804a3-532">Directional indicators</span></span>

<span data-ttu-id="804a3-533">Em um aplicativo de realidade misturada, o conteúdo pode estar fora de vista do campo ou obstruídos pelo objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="804a3-533">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="804a3-534">Um aplicativo bem projetado tornará mais fácil para o usuário localizar conteúdo não visíveis.</span><span class="sxs-lookup"><span data-stu-id="804a3-534">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="804a3-535">Indicadores direcionais alertam um usuário ao conteúdo importante e fornecem orientação para o conteúdo em relação à posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-535">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="804a3-536">Diretrizes para o conteúdo não visíveis podem assumir a forma de emissores de som, as setas direcionais ou indicações visuais diretas.</span><span class="sxs-lookup"><span data-stu-id="804a3-536">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-537">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-537">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-538"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-538"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-539"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-540">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-540">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="804a3-541">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-541">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-542">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-542">Quality criteria</span></span>

|  <span data-ttu-id="804a3-543">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-543">Best</span></span>  |  <span data-ttu-id="804a3-544">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-544">Meets</span></span> |  <span data-ttu-id="804a3-545">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-545">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-546">As indicações de áudio e vídeo diretamente guiam o usuário ao conteúdo relevante fora o campo de visualização.</span><span class="sxs-lookup"><span data-stu-id="804a3-546">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="804a3-547">Uma seta ou alguns indicador que aponta para o usuário na direção geral do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="804a3-547">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="804a3-548">Conteúdo relevante é fora do campo de visão e ruim ou nenhuma orientação para a localização é fornecida ao usuário.</span><span class="sxs-lookup"><span data-stu-id="804a3-548">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="804a3-549">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-549">How to measure</span></span>

* <span data-ttu-id="804a3-550">O conteúdo relevante fora do campo de vista do usuário é descoberto por meio de indicações visuais e/ou áudio.</span><span class="sxs-lookup"><span data-stu-id="804a3-550">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-551">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-551">Recommendations</span></span>

* <span data-ttu-id="804a3-552">Quando o conteúdo relevante estiver fora de vista de campo do usuário, use indicadores direcionais e as indicações de áudio para orientar o usuário ao conteúdo.</span><span class="sxs-lookup"><span data-stu-id="804a3-552">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="804a3-553">Em muitos casos, um guia visual direto é preferível as setas direcionais.</span><span class="sxs-lookup"><span data-stu-id="804a3-553">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="804a3-554">Indicadores direcionais não devem ser criados no cursor.</span><span class="sxs-lookup"><span data-stu-id="804a3-554">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-555">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-555">Resources</span></span>

* [<span data-ttu-id="804a3-556">Quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="804a3-556">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="804a3-557">Carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="804a3-557">Data loading</span></span>

<span data-ttu-id="804a3-558">Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.</span><span class="sxs-lookup"><span data-stu-id="804a3-558">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="804a3-559">Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso é visível e também pode indicar quanto tempo o tempo de espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="804a3-559">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="804a3-560">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="804a3-560">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="804a3-561"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="804a3-561"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="804a3-562"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="804a3-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="804a3-563">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-563">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="804a3-564">✔️</span><span class="sxs-lookup"><span data-stu-id="804a3-564">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="804a3-565">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="804a3-565">Quality criteria</span></span>

|  <span data-ttu-id="804a3-566">Melhor</span><span class="sxs-lookup"><span data-stu-id="804a3-566">Best</span></span>  |  <span data-ttu-id="804a3-567">Atenda às</span><span class="sxs-lookup"><span data-stu-id="804a3-567">Meets</span></span> |  <span data-ttu-id="804a3-568">falhar</span><span class="sxs-lookup"><span data-stu-id="804a3-568">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="804a3-569">Indicador visual animado, na forma de uma barra de progresso ou um anel, mostrando o progresso durante qualquer carregando ou processamento de dados.</span><span class="sxs-lookup"><span data-stu-id="804a3-569">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="804a3-570">O indicador visual fornece orientações sobre quanto tempo de espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="804a3-570">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="804a3-571">Usuário é informado de que o carregamento de dados está em andamento, mas não há nenhuma indicação de quanto tempo de espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="804a3-571">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="804a3-572">Nenhum carregamento de dados ou indicadores de processo para a tarefa demorando mais do que 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="804a3-572">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="804a3-573">Como medir</span><span class="sxs-lookup"><span data-stu-id="804a3-573">How to measure</span></span>

* <span data-ttu-id="804a3-574">Durante o carregamento de dados, verifique se que não houver nenhum estado em branco por mais de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="804a3-574">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="804a3-575">Recomendações</span><span class="sxs-lookup"><span data-stu-id="804a3-575">Recommendations</span></span>

* <span data-ttu-id="804a3-576">Forneça um animator de carregamento de dados mostrando o progresso em qualquer situação, quando o usuário poderão perceber esse aplicativo tenha interrompido ou falhou.</span><span class="sxs-lookup"><span data-stu-id="804a3-576">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="804a3-577">Uma regra prática razoável é qualquer atividade de 'carregamento' que pode levar mais de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="804a3-577">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="804a3-578">Recursos</span><span class="sxs-lookup"><span data-stu-id="804a3-578">Resources</span></span>

* [<span data-ttu-id="804a3-579">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="804a3-579">Displaying progress</span></span>](progress.md)

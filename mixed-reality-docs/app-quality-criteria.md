---
title: Critérios de qualidade do aplicativo
description: Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: critérios de qualidade do aplicativo, realidade, misturada misto de aplicativo de realidade
ms.openlocfilehash: dfa1390190fad8d84982171dfbcfa101b20501dc
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750323"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="98cd9-104">Critérios de qualidade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="98cd9-104">App quality criteria</span></span>

<span data-ttu-id="98cd9-105">Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="98cd9-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="98cd9-106">Para cada fator as informações a seguir são fornecidas</span><span class="sxs-lookup"><span data-stu-id="98cd9-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="98cd9-107">Visão geral – uma breve descrição de como o fator de qualidade e por que é importante.</span><span class="sxs-lookup"><span data-stu-id="98cd9-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="98cd9-108">Impacto do dispositivo - qual tipo de dispositivo de realidade misturada da janela é afetado.</span><span class="sxs-lookup"><span data-stu-id="98cd9-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="98cd9-109">Critérios de qualidade – como avaliar o fator de qualidade.</span><span class="sxs-lookup"><span data-stu-id="98cd9-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="98cd9-110">Como medir – métodos de medir (ou experiência) o problema.</span><span class="sxs-lookup"><span data-stu-id="98cd9-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="98cd9-111">Recomendações – resumidas das abordagens para proporcionar uma melhor experiência de usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="98cd9-112">Recursos – desenvolvedor relevante e recursos de design que são úteis para criar melhores experiências de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="98cd9-113">Taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="98cd9-113">Frame rate</span></span>

<span data-ttu-id="98cd9-114">Taxa de quadros é o primeiro pilar de conforto holograma de estabilidade e o usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="98cd9-115">Taxa de quadros abaixo os destinos de recomendada pode causar hologramas apareçam instável, afetando negativamente a credibilidade da experiência e possivelmente causando fadiga olho.</span><span class="sxs-lookup"><span data-stu-id="98cd9-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="98cd9-116">A taxa de quadros de destino para a sua experiência em fones imersivos em exposição Windows Mixed Reality será 60Hz ou 90Hz, dependendo de quais computadores de compatível com Windows misto realidade você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="98cd9-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="98cd9-117">Para HoloLens a taxa de quadros de destino é 60Hz.</span><span class="sxs-lookup"><span data-stu-id="98cd9-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-118">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-120"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-121">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-121">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-122">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-123">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-123">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-124">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-124">Best</span></span>  |  <span data-ttu-id="98cd9-125">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-125">Meets</span></span> |  <span data-ttu-id="98cd9-126">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="98cd9-127">O aplicativo atender consistentemente quadros por segundo objetivo (FPS) para o dispositivo de destino: 60fps em HoloLens; 90fps em PCs Ultra; e 60fps em PCs de base.</span><span class="sxs-lookup"><span data-stu-id="98cd9-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="98cd9-128">O aplicativo tem descartes de intermitente de quadro não prejudicam a experiência de principal; ou FPS é consistentemente inferiores a meta desejada, mas não impessa a experiência de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="98cd9-129">O aplicativo está passando por uma queda na taxa de quadros em média a cada dez segundos ou menos.</span><span class="sxs-lookup"><span data-stu-id="98cd9-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-130">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-130">How to measure</span></span>

* <span data-ttu-id="98cd9-131">Um gráfico de taxa de quadro em tempo real é fornecido por meio de pela [Windows Device Portal](using-the-windows-device-portal.md#system-performance) sob "Desempenho do sistema".</span><span class="sxs-lookup"><span data-stu-id="98cd9-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="98cd9-132">Para desenvolvimento de depuração, adicione um contador de diagnóstico de taxa de quadros no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="98cd9-133">Consulte os recursos de um contador de exemplo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="98cd9-134">Descartes de taxa de quadros podem ser experimentadas no dispositivo, enquanto o aplicativo está em execução, movendo sua cabeça de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="98cd9-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="98cd9-135">Se o holograma mostra movimentação trêmulo inesperada, em seguida, baixa taxa de quadros ou o plano de estabilidade provavelmente é a causa.</span><span class="sxs-lookup"><span data-stu-id="98cd9-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-136">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-136">Recommendations</span></span>

* <span data-ttu-id="98cd9-137">Adicione um contador da taxa de quadros no início do trabalho de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="98cd9-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="98cd9-138">As alterações que incorrem em uma queda na taxa de quadros devem ser avaliadas e resolvidas adequadamente como um bug de desempenho.</span><span class="sxs-lookup"><span data-stu-id="98cd9-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-140">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-140">Documentation</span></span>

* [<span data-ttu-id="98cd9-141">Noções básicas sobre desempenho para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="98cd9-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="98cd9-142">Taxa de quadros e a estabilidade de holograma</span><span class="sxs-lookup"><span data-stu-id="98cd9-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="98cd9-143">Orçamento de desempenho de ativos</span><span class="sxs-lookup"><span data-stu-id="98cd9-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="98cd9-144">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="98cd9-145">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="98cd9-145">Tools and tutorials</span></span>

* [<span data-ttu-id="98cd9-146">MRToolkit, exibição de contador FPS</span><span class="sxs-lookup"><span data-stu-id="98cd9-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="98cd9-147">MRToolkit, sombreadores</span><span class="sxs-lookup"><span data-stu-id="98cd9-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="98cd9-148">Referências externas</span><span class="sxs-lookup"><span data-stu-id="98cd9-148">External references</span></span>

* [<span data-ttu-id="98cd9-149">Unity, otimização de aplicativos móveis</span><span class="sxs-lookup"><span data-stu-id="98cd9-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="98cd9-150">Estabilidade holograma</span><span class="sxs-lookup"><span data-stu-id="98cd9-150">Hologram stability</span></span>

<span data-ttu-id="98cd9-151">Hologramas estáveis aumentar a usabilidade e a credibilidade do seu aplicativo e criar uma experiência de exibição mais à vontade para o usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="98cd9-152">A qualidade da estabilidade holograma é um resultado de desenvolvimento de aplicativos boa e capacidade do dispositivo entender (faixa) seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="98cd9-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="98cd9-153">Embora a taxa de quadros é o primeiro pilar de estabilidade, outros fatores podem afetar a estabilidade incluindo:</span><span class="sxs-lookup"><span data-stu-id="98cd9-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="98cd9-154">Uso do plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="98cd9-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="98cd9-155">Distância até âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="98cd9-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="98cd9-156">Acompanhamento</span><span class="sxs-lookup"><span data-stu-id="98cd9-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-157">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-159"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-160">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-160">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-161">❌</span><span class="sxs-lookup"><span data-stu-id="98cd9-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-162">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-162">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-163">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-163">Best</span></span>  |  <span data-ttu-id="98cd9-164">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-164">Meets</span></span> |  <span data-ttu-id="98cd9-165">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-166">Hologramas consistentemente aparecem estáveis.</span><span class="sxs-lookup"><span data-stu-id="98cd9-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="98cd9-167">Exibe o conteúdo secundário movimentação inesperada; ou movimentação inesperada não impede a experiência geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="98cd9-168">Conteúdo principal em quadro exibe movimentação inesperada.</span><span class="sxs-lookup"><span data-stu-id="98cd9-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-169">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-169">How to measure</span></span>

<span data-ttu-id="98cd9-170">Ao mesmo tempo usando o dispositivo e a experiência de exibição:</span><span class="sxs-lookup"><span data-stu-id="98cd9-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="98cd9-171">Mover sua cabeça de lado a lado, se o hologramas mostram a movimentação inesperada, em seguida, baixa taxa de quadros ou alinhamento incorreto do plano de estabilidade para o plano focal é a causa provável.</span><span class="sxs-lookup"><span data-stu-id="98cd9-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="98cd9-172">Mover-se o ambiente e hologramas, procure comportamentos como raias e jumpiness.</span><span class="sxs-lookup"><span data-stu-id="98cd9-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="98cd9-173">Esse tipo de movimento provavelmente é causado pelo dispositivo não controla o ambiente ou a distância para a âncora espacial.</span><span class="sxs-lookup"><span data-stu-id="98cd9-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="98cd9-174">Se for grande ou vários hologramas estão no quadro, observar o comportamento de holograma em várias intensidades enquanto mover sua posição principal de lado a lado, se shakiness for exibida, isso provavelmente causado por plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="98cd9-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="98cd9-175">Recomendações de</span><span class="sxs-lookup"><span data-stu-id="98cd9-175">Recomendations</span></span>

* <span data-ttu-id="98cd9-176">Adicione um contador da taxa de quadros no início do trabalho de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="98cd9-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="98cd9-177">Use o plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="98cd9-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="98cd9-178">Sempre processa hologramas ancoradas dentro de 3 medidores de sua âncora.</span><span class="sxs-lookup"><span data-stu-id="98cd9-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="98cd9-179">Verifique se o que seu ambiente está configurado para o controle apropriado.</span><span class="sxs-lookup"><span data-stu-id="98cd9-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="98cd9-180">Projetar sua experiência para evitar hologramas em vários níveis de profundidade focal dentro do quadro.</span><span class="sxs-lookup"><span data-stu-id="98cd9-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-181">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-182">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-182">Documentation</span></span>

* [<span data-ttu-id="98cd9-183">Taxa de quadros e a estabilidade de holograma</span><span class="sxs-lookup"><span data-stu-id="98cd9-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="98cd9-184">Estudo de caso, usando o plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="98cd9-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="98cd9-185">Noções básicas sobre desempenho para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="98cd9-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="98cd9-186">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="98cd9-187">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="98cd9-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="98cd9-188">Rastreamento de tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="98cd9-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="98cd9-189">Quadro estacionário de referência</span><span class="sxs-lookup"><span data-stu-id="98cd9-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="98cd9-190">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="98cd9-190">Tools and tutorials</span></span>

* [<span data-ttu-id="98cd9-191">Kit de complementar MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="98cd9-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="98cd9-192">Posição hologramas em superfícies real</span><span class="sxs-lookup"><span data-stu-id="98cd9-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="98cd9-193">Misalignments de hologramas com objetos físicos (se se destina a ser colocado em relação a um outro) é uma indicação clara do que a não-união hologramas e reais.</span><span class="sxs-lookup"><span data-stu-id="98cd9-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="98cd9-194">Precisão da colocação deve ser relativo às necessidades do cenário. Por exemplo, posicionamento superfície geral pode usar o mapa espacial, mas o posicionamento mais preciso exigirá algum uso de marcadores e de calibração.</span><span class="sxs-lookup"><span data-stu-id="98cd9-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-195">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-197"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-198">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-198">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-199">❌</span><span class="sxs-lookup"><span data-stu-id="98cd9-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-200">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-200">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-201">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-201">Best</span></span>  |  <span data-ttu-id="98cd9-202">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-202">Meets</span></span> |  <span data-ttu-id="98cd9-203">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="98cd9-204">Hologramas alinham para a superfície normalmente nos centímetros para intervalo polegadas.</span><span class="sxs-lookup"><span data-stu-id="98cd9-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="98cd9-205">Se mais precisão for necessária, o aplicativo deve fornecer um meio eficaz para colaboração entre as especificações do aplicativo desejado.</span><span class="sxs-lookup"><span data-stu-id="98cd9-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="98cd9-206">N/D</span><span class="sxs-lookup"><span data-stu-id="98cd9-206">NA</span></span> | <span data-ttu-id="98cd9-207">As hologramas aparecem não alinhadas com o objeto de destino físico, quebrando o plano de superfície ou que aparecem para float para fora da superfície de.</span><span class="sxs-lookup"><span data-stu-id="98cd9-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="98cd9-208">Se a precisão for necessária, hologramas devem atender a especificação de proximidade do cenário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-209">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-209">How to measure</span></span>

* <span data-ttu-id="98cd9-210">Hologramas que são colocadas no mapa espacial não devem aparecer drasticamente flutuando acima ou abaixo da superfície.</span><span class="sxs-lookup"><span data-stu-id="98cd9-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="98cd9-211">Hologramas que exigem colocação precisa devem ter alguma forma de marcador e calibragem sistema que tem a precisão do requisito do cenário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-212">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-212">Recommendations</span></span>

* <span data-ttu-id="98cd9-213">Mapa espacial é útil para colocar objetos em superfícies quando a precisão não é necessária.</span><span class="sxs-lookup"><span data-stu-id="98cd9-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="98cd9-214">Para obter a melhor precisão, use marcadores ou cartazes para definir as hologramas e um controlador do Xbox (ou algum mecanismo de alinhamento manual) para calibragem final.</span><span class="sxs-lookup"><span data-stu-id="98cd9-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="98cd9-215">Considere dividir hologramas extra grandes em partes lógicas e alinhar cada parte para a superfície.</span><span class="sxs-lookup"><span data-stu-id="98cd9-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="98cd9-216">Incorretamente conjunto interpupilary distância (IPD) também pode afetar o alinhamento de holograma.</span><span class="sxs-lookup"><span data-stu-id="98cd9-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="98cd9-217">Sempre configure HoloLens para IPD do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-218">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-219">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-219">Documentation</span></span>

* [<span data-ttu-id="98cd9-220">Posicionamento de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="98cd9-221">Processo de verificação de espaço</span><span class="sxs-lookup"><span data-stu-id="98cd9-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="98cd9-222">Práticas recomendadas de âncoras espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="98cd9-223">Rastreamento de tratamento de erros</span><span class="sxs-lookup"><span data-stu-id="98cd9-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="98cd9-224">Mapeamento espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="98cd9-225">Visão geral do desenvolvimento Vuforia</span><span class="sxs-lookup"><span data-stu-id="98cd9-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="98cd9-226">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="98cd9-226">Tools and tutorials</span></span>

* [<span data-ttu-id="98cd9-227">MR Espacial 230: mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="98cd9-228">MR o Kit de ferramentas, bibliotecas de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="98cd9-229">Kit de complementar MR, exemplo de calibragem de pôster</span><span class="sxs-lookup"><span data-stu-id="98cd9-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="98cd9-230">Kit de complementar MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="98cd9-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="98cd9-231">Referências externas</span><span class="sxs-lookup"><span data-stu-id="98cd9-231">External references</span></span>

* [<span data-ttu-id="98cd9-232">Estudo de caso de Lowes, alinhamento de precisão</span><span class="sxs-lookup"><span data-stu-id="98cd9-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="98cd9-233">Exibição de zona de conforto</span><span class="sxs-lookup"><span data-stu-id="98cd9-233">Viewing zone of comfort</span></span>

<span data-ttu-id="98cd9-234">Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergirem colocando conteúdo e hologramas em várias intensidades.</span><span class="sxs-lookup"><span data-stu-id="98cd9-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="98cd9-235">Os usuários vestindo HoloLens sempre acomodará 2.0 m para manter uma imagem clara como HoloLens exibe são corrigidos em uma distância óptica aproximadamente 2.0m do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="98cd9-236">Profundidade do conteúdo inadequada pode levar a discomfort visual ou fadiga.</span><span class="sxs-lookup"><span data-stu-id="98cd9-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-237">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-239"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-240">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-240">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-241">❌</span><span class="sxs-lookup"><span data-stu-id="98cd9-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-242">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="98cd9-243">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="98cd9-244">Colocar o conteúdo em 2m.</span><span class="sxs-lookup"><span data-stu-id="98cd9-244">Place content at 2m.</span></span></li><li><span data-ttu-id="98cd9-245">Quando hologramas não podem ser colocadas em 2m, e não podem ser evitados conflitos entre a convergência e acomodação, a zona ideal para posicionamento holograma é entre 1,25 milhões e milhões de 5.</span><span class="sxs-lookup"><span data-stu-id="98cd9-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="98cd9-246">Em todos os casos, designers devem estruturar o conteúdo a fim de incentivar os usuários interajam 1 + m imediatamente (por exemplo, ajustar o tamanho do conteúdo e padrão de parâmetros de posicionamento).</span><span class="sxs-lookup"><span data-stu-id="98cd9-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="98cd9-247">A menos que especificamente não exigido pelo cenário, um plano de corte deve ser implementar com fadeout começando em 1 milhão.</span><span class="sxs-lookup"><span data-stu-id="98cd9-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="98cd9-248">Em casos onde uma observação mais próxima de um holograma imóvel é necessária, o conteúdo não deve ser mais próximo do que 50cm.</span><span class="sxs-lookup"><span data-stu-id="98cd9-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="98cd9-249">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-249">Meets</span></span></td><td> <span data-ttu-id="98cd9-250">O conteúdo é dentro a orientação de exibição e movimento, mas o uso inadequado ou nenhum uso do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="98cd9-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="98cd9-251">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-251">Fail</span></span> </td><td> <span data-ttu-id="98cd9-252">O conteúdo é apresentado muito próximas (normalmente &lt;1,25 m, ou &lt;50 cm para hologramas estáticos que exigem mais próxima Observação.)</span><span class="sxs-lookup"><span data-stu-id="98cd9-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-253">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-253">How to measure</span></span>

* <span data-ttu-id="98cd9-254">Conteúdo deve ser 2m geralmente ausente, mas não mais próximo que 1,25 ou mais de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="98cd9-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="98cd9-255">Com poucas exceções, a distância de renderização de recorte do HoloLens deve ser definida como .85CM com fadeout começando em 1 milhão de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="98cd9-256">Abordar o conteúdo e observe o efeito de plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="98cd9-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="98cd9-257">Conteúdo estático não deve ficar mais próximo do que 50cm de distância.</span><span class="sxs-lookup"><span data-stu-id="98cd9-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-258">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-258">Recommendations</span></span>

* <span data-ttu-id="98cd9-259">Criar conteúdo para a distância de exibição ideal de 2M.</span><span class="sxs-lookup"><span data-stu-id="98cd9-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="98cd9-260">Defina a distância de renderização de recorte para 85cm com fadeout começando em 1 milhão de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="98cd9-261">Para hologramas estacionários que precisam exibir mais próximo, o plano de corte deve ser não mais próximo do que 30cm e fadeout deve começar pelo menos 10cm para longe do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="98cd9-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-262">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-262">Resources</span></span>

* [<span data-ttu-id="98cd9-263">Renderizar distância</span><span class="sxs-lookup"><span data-stu-id="98cd9-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="98cd9-264">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="98cd9-265">Experimentar a escala</span><span class="sxs-lookup"><span data-stu-id="98cd9-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="98cd9-266">Texto, tamanho da fonte recomendado</span><span class="sxs-lookup"><span data-stu-id="98cd9-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="98cd9-267">Alternância de profundidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-267">Depth switching</span></span>

<span data-ttu-id="98cd9-268">Independentemente da zona de exibição de problemas de conforto, as exigências do usuário alterne rapidamente ou com frequência entre quase e muito focal objetos (incluindo hologramas e conteúdo do mundo real) podem levar a fadiga oculomotor e discomfort geral.</span><span class="sxs-lookup"><span data-stu-id="98cd9-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-269">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-271"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-272">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-272">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-273">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-274">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-274">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-275">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-275">Best</span></span>  |  <span data-ttu-id="98cd9-276">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-276">Meets</span></span> |  <span data-ttu-id="98cd9-277">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-278">Profundidade natural ou limitada alternância que não fazem com que o usuário se concentre em unnaturally.</span><span class="sxs-lookup"><span data-stu-id="98cd9-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="98cd9-279">Comutador de profundidade abrupta esse é o núcleo e projetado para a experiência de aplicativo, ou comutador de profundidade abrupta causada por conteúdo inesperado do mundo real.</span><span class="sxs-lookup"><span data-stu-id="98cd9-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="98cd9-280">Comutador de profundidade consistente, ou profundidade abrupta alternância que não é necessário ou núcleo para a experiência de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-281">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-281">How to measure</span></span>

* <span data-ttu-id="98cd9-282">Se o aplicativo requer que o usuário para consistentemente e/ou abruptamente mudar o foco de profundidade, não há profundidade, alternando o problema.</span><span class="sxs-lookup"><span data-stu-id="98cd9-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-283">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-283">Recommendations</span></span>

* <span data-ttu-id="98cd9-284">Manter o conteúdo principal em um plano focal consistente e verifique se que o plano de estabilização corresponde ao plano focal.</span><span class="sxs-lookup"><span data-stu-id="98cd9-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="98cd9-285">Isso irá aliviar fadiga oculomotor e movimentação holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="98cd9-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-286">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-286">Resources</span></span>

* [<span data-ttu-id="98cd9-287">Renderizar distância</span><span class="sxs-lookup"><span data-stu-id="98cd9-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="98cd9-288">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="98cd9-289">Uso de som espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-289">Use of spatial sound</span></span>

<span data-ttu-id="98cd9-290">Na realidade mista do Windows, o mecanismo de áudio fornece o componente auricular da experiência de realidade misturada, simulando 3D som usando simulações ambientais, distância e direção.</span><span class="sxs-lookup"><span data-stu-id="98cd9-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="98cd9-291">Usando o som espacial em um aplicativo permite aos desenvolvedores colocar convincingly sons em um espaço dimensional 3 (esfera) em todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="98cd9-292">Os sons, em seguida, parecerá como se eles foram provenientes de objetos físicos real ou as hologramas de realidade misturada no ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="98cd9-293">Som espacial é uma ferramenta poderosa para uma imersão, acessibilidade e design UX em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="98cd9-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-294">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-296"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-297">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-297">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-298">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-299">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-299">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-300">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-300">Best</span></span>  |  <span data-ttu-id="98cd9-301">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-301">Meets</span></span> |  <span data-ttu-id="98cd9-302">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-303">Som é logicamente spatialized e a experiência do usuário adequadamente usa som para ajudá-lo com comentários de usuário e a descoberta de objeto.</span><span class="sxs-lookup"><span data-stu-id="98cd9-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="98cd9-304">Som é natural e relevantes para objetos e normalizada entre o cenário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="98cd9-305">Áudio espacial é usada adequadamente para credibilidade mas ausente como meio para ajudar com a capacidade de descoberta e comentários do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="98cd9-306">Som não é spatialized conforme o esperado, e/ou falta de som para auxiliar o usuário dentro a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="98cd9-307">Ou áudio espacial não foi considerado ou usado no design do cenário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-308">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-308">How to measure</span></span>

* <span data-ttu-id="98cd9-309">Em geral, os sons relevantes devem emitir de hologramas de destino (por exemplo,., som latido provenientes de dog holográfica.)</span><span class="sxs-lookup"><span data-stu-id="98cd9-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="98cd9-310">Indicações de som devem ser usadas em toda a experiência do usuário para ajudar o usuário com reconhecimento de ações fora do quadro holográfica ou comentários.</span><span class="sxs-lookup"><span data-stu-id="98cd9-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-311">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-311">Recommendations</span></span>

* <span data-ttu-id="98cd9-312">Use o áudio espacial para ajudá-lo com interfaces de usuário e a descoberta de objeto.</span><span class="sxs-lookup"><span data-stu-id="98cd9-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="98cd9-313">Sons real funcionam melhor do que sintetização ou som não natural.</span><span class="sxs-lookup"><span data-stu-id="98cd9-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="98cd9-314">A maioria dos sons devem ser spatialized.</span><span class="sxs-lookup"><span data-stu-id="98cd9-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="98cd9-315">Evite os emissores invisíveis.</span><span class="sxs-lookup"><span data-stu-id="98cd9-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="98cd9-316">Evite mascaramento espacial.</span><span class="sxs-lookup"><span data-stu-id="98cd9-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="98cd9-317">Normalize todos os sons.</span><span class="sxs-lookup"><span data-stu-id="98cd9-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-318">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-319">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-319">Documentation</span></span>

* [<span data-ttu-id="98cd9-320">Som espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="98cd9-321">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="98cd9-322">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="98cd9-323">Estudo de caso, espacial som para HoloTour</span><span class="sxs-lookup"><span data-stu-id="98cd9-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="98cd9-324">Estudo de caso, usando o som espacial RoboRaid</span><span class="sxs-lookup"><span data-stu-id="98cd9-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="98cd9-325">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="98cd9-325">Tools and tutorials</span></span>

* [<span data-ttu-id="98cd9-326">MR Espacial 220: som espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="98cd9-327">MRToolkit, áudio espacial</span><span class="sxs-lookup"><span data-stu-id="98cd9-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="98cd9-328">Concentre-se em limites de quadro holográfica (FOV)</span><span class="sxs-lookup"><span data-stu-id="98cd9-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="98cd9-329">Experiências de usuário bem projetado podem criar e manter o contexto úteis do ambiente virtual que se estende em torno dos usuários.</span><span class="sxs-lookup"><span data-stu-id="98cd9-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="98cd9-330">Reduzir o efeito dos limites FOV envolve um design elaborado de escala de conteúdo e contexto, o uso de áudio espacial, sistemas de orientação e a posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="98cd9-331">Se feito corretamente, o usuário se sentirão que menor prejudicada por limites de FOV tendo uma experiência de aplicativo à vontade.</span><span class="sxs-lookup"><span data-stu-id="98cd9-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-332">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-334"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-335">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-335">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-336">❌</span><span class="sxs-lookup"><span data-stu-id="98cd9-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-337">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-337">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-338">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-338">Best</span></span>  |  <span data-ttu-id="98cd9-339">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-339">Meets</span></span> |  <span data-ttu-id="98cd9-340">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-341">Usuário nunca perde o contexto e exibição se sente confortável.</span><span class="sxs-lookup"><span data-stu-id="98cd9-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="98cd9-342">Assistência de contexto é fornecida para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="98cd9-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="98cd9-343">Detectabilidade e exibindo a orientação é fornecida para objetos fora do quadro.</span><span class="sxs-lookup"><span data-stu-id="98cd9-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="98cd9-344">Em geral, o design de movimento e a escala das hologramas são apropriadas para uma experiência visual confortável.</span><span class="sxs-lookup"><span data-stu-id="98cd9-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="98cd9-345">Usuário nunca perde o contexto, mas o movimento do pescoço extra pode ser necessário em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="98cd9-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="98cd9-346">Em algumas situações escala faz com que hologramas quebrar tanto o quadro vertical ou horizontal, fazendo com que algum movimento pescoço exibir hologramas.</span><span class="sxs-lookup"><span data-stu-id="98cd9-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="98cd9-347">Usuário poderá perder o contexto e/ou movimento do pescoço consistente é necessária para exibir hologramas.</span><span class="sxs-lookup"><span data-stu-id="98cd9-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="98cd9-348">Nenhuma orientação de contexto para objetos grandes holográfica, mover objetos muito fácil perder fora do quadro sem diretrizes de capacidade de descoberta ou a altura hologramas requer movimento pescoço regular para exibir.</span><span class="sxs-lookup"><span data-stu-id="98cd9-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-349">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-349">How to measure</span></span>

* <span data-ttu-id="98cd9-350">Contexto para um holograma (grande) for perdido ou não é compreendido devido ao que está sendo cortado nos limites.</span><span class="sxs-lookup"><span data-stu-id="98cd9-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="98cd9-351">Local do hologramas são difíceis de encontrar devido à falta de diretores de atenção ou conteúdo que se move rapidamente para dentro e fora do quadro holográfico.</span><span class="sxs-lookup"><span data-stu-id="98cd9-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="98cd9-352">Cenário requer regular e repetitivas para cima e para a animação principal para ver totalmente um holograma resultando em fadiga pescoço.</span><span class="sxs-lookup"><span data-stu-id="98cd9-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-353">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-353">Recommendations</span></span>

* <span data-ttu-id="98cd9-354">Inicie a experiência com objetos pequenos que se ajustar a FOV, em seguida, fazer a transição com visuais para versões maiores.</span><span class="sxs-lookup"><span data-stu-id="98cd9-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="98cd9-355">Use espaciais diretores de áudio e atenção para conteúdo de localizar o usuário que está fora do FOV da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="98cd9-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="98cd9-356">Tanto quanto possível, evite hologramas que recortar verticalmente o FOV.</span><span class="sxs-lookup"><span data-stu-id="98cd9-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="98cd9-357">Fornece ao usuário uma diretriz no aplicativo para melhor visualização local.</span><span class="sxs-lookup"><span data-stu-id="98cd9-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-358">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-359">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-359">Documentation</span></span>

* [<span data-ttu-id="98cd9-360">Quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="98cd9-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="98cd9-361">Estudo de caso, a UI HoloStudio e lições aprendidas de design de interação</span><span class="sxs-lookup"><span data-stu-id="98cd9-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="98cd9-362">Escala de objetos e ambientes</span><span class="sxs-lookup"><span data-stu-id="98cd9-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="98cd9-363">Cursores, indicações visuais</span><span class="sxs-lookup"><span data-stu-id="98cd9-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="98cd9-364">Referências externas</span><span class="sxs-lookup"><span data-stu-id="98cd9-364">External references</span></span>

* [<span data-ttu-id="98cd9-365">Muitos ados sobre o FOV</span><span class="sxs-lookup"><span data-stu-id="98cd9-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="98cd9-366">Conteúdo reage a posição do usuário</span><span class="sxs-lookup"><span data-stu-id="98cd9-366">Content reacts to user position</span></span>

<span data-ttu-id="98cd9-367">Hologramas devem reagir para a posição do usuário aproximadamente da mesma maneira que objetos de "real".</span><span class="sxs-lookup"><span data-stu-id="98cd9-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="98cd9-368">Uma consideração de design importantes é a elementos de interface do usuário que não não necessariamente assumem que a posição de um usuário está parados e adaptar-se a animação do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="98cd9-369">Criação de um aplicativo que corretamente se adapta a posição de usuário criar uma experiência mais verossímeis e torná-lo mais fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="98cd9-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-370">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-372"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-373">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-373">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-374">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-375">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="98cd9-376">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-376">Best</span></span> </td><td> <span data-ttu-id="98cd9-377">Conteúdo e a interface do usuário se adaptar às posições de usuário, permitindo que o usuário interagir naturalmente com o conteúdo dentro do escopo de movimentação do usuário esperado.</span><span class="sxs-lookup"><span data-stu-id="98cd9-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="98cd9-378">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-378">Meets</span></span> </td><td> <span data-ttu-id="98cd9-379">Interface do usuário se adapta para a posição do usuário, mas pode impedir a exibição do conteúdo da chave exigir que o usuário ajustar sua posição.</span><span class="sxs-lookup"><span data-stu-id="98cd9-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="98cd9-380">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="98cd9-381">Elementos de interface do usuário são perdidos ou bloqueados durante usuário causando movimentação controles unnaturally retornar a (ou encontrar).</span><span class="sxs-lookup"><span data-stu-id="98cd9-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="98cd9-382">Elementos de interface do usuário limitam a exibição do conteúdo principal.</span><span class="sxs-lookup"><span data-stu-id="98cd9-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="98cd9-383">Movimentação da interface do usuário não é otimizada para exibição de distância e momentum particularmente com <a href="billboarding-and-tag-along.md">tag-along</a> elementos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-384">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-384">How to measure</span></span>

* <span data-ttu-id="98cd9-385">Todas as medidas devem ser feitas dentro de um escopo razoável do cenário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="98cd9-386">Enquanto o movimento do usuário irá variar, não tente fazer o aplicativo com a movimentação de usuário extremo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="98cd9-387">Para elementos de interface do usuário, controles relevantes devem estar disponíveis, independentemente de movimentação do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="98cd9-388">Por exemplo, se o usuário está exibindo e andar de um mapa 3D com o zoom, o controle de zoom deve ser prontamente disponível para o usuário, independentemente do local.</span><span class="sxs-lookup"><span data-stu-id="98cd9-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-389">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-389">Recommendations</span></span>

* <span data-ttu-id="98cd9-390">O usuário é a câmera e eles controlam a movimentação.</span><span class="sxs-lookup"><span data-stu-id="98cd9-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="98cd9-391">Deixe-os da unidade.</span><span class="sxs-lookup"><span data-stu-id="98cd9-391">Let them drive.</span></span>
* <span data-ttu-id="98cd9-392">Considere billboarding para texto e os sistemas de menus que caso contrário, seriam bloqueada pelo mundo ou obscurecidos se um usuário eram mover-se.</span><span class="sxs-lookup"><span data-stu-id="98cd9-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="98cd9-393">Use tag-along conteúdo que precisa acompanhar o usuário enquanto ainda permite que o usuário veja o que está na frente delas.</span><span class="sxs-lookup"><span data-stu-id="98cd9-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-394">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-395">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-395">Documentation</span></span>

* [<span data-ttu-id="98cd9-396">Design de interação</span><span class="sxs-lookup"><span data-stu-id="98cd9-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="98cd9-397">Cor, luz e material</span><span class="sxs-lookup"><span data-stu-id="98cd9-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="98cd9-398">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="98cd9-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="98cd9-399">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="98cd9-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="98cd9-400">O motion Self e locomotion do usuário</span><span class="sxs-lookup"><span data-stu-id="98cd9-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="98cd9-401">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="98cd9-401">Tools and tutorials</span></span>

* [<span data-ttu-id="98cd9-402">Entrada do MR 210: foco</span><span class="sxs-lookup"><span data-stu-id="98cd9-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="98cd9-403">Clareza de interação de entrada</span><span class="sxs-lookup"><span data-stu-id="98cd9-403">Input interaction clarity</span></span>

<span data-ttu-id="98cd9-404">Clareza de interação de entrada é essencial para facilidade de uso do aplicativo e inclui a entrada consistência, acessibilidade, detectabilidade de métodos de interação.</span><span class="sxs-lookup"><span data-stu-id="98cd9-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="98cd9-405">Usuário deve ser capaz de usar toda a plataforma de interações comuns sem que eles reaprendessem.</span><span class="sxs-lookup"><span data-stu-id="98cd9-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="98cd9-406">Se o aplicativo tem uma entrada personalizada, ele deve ser claramente comunicado e demonstrado.</span><span class="sxs-lookup"><span data-stu-id="98cd9-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-407">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-409"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-410">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-410">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-411">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-412">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-412">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-413">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-413">Best</span></span>  |  <span data-ttu-id="98cd9-414">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-414">Meets</span></span> |  <span data-ttu-id="98cd9-415">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-416">Métodos de interação de entrada são consistentes com o Windows Mixed Reality fornecidos [orientação](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="98cd9-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="98cd9-417">Qualquer entrada personalizada não deve ser redundante com a entrada padrão (em vez disso, use padrão interação) e deve ser comunicada claramente e demonstrou que o usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="98cd9-418">Semelhante às entradas melhor, mas personalizadas são redundantes com métodos de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="98cd9-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="98cd9-419">Usuário ainda pode alcançar a meta e o progresso por meio da experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="98cd9-420">Difícil de entender o mapeamento de método ou o botão de entrada.</span><span class="sxs-lookup"><span data-stu-id="98cd9-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="98cd9-421">Entrada é muito personalizado, não dá suporte a entrada padrão, não há instruções, ou pode causar problemas de fadiga e conforto.</span><span class="sxs-lookup"><span data-stu-id="98cd9-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-422">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-422">How to measure</span></span>

* <span data-ttu-id="98cd9-423">O aplicativo usa consistente [métodos de entrada padrão.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="98cd9-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="98cd9-424">Se o aplicativo tem uma entrada de Customer, ele claramente é comunicado por meio de:</span><span class="sxs-lookup"><span data-stu-id="98cd9-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="98cd9-425">Experiência de primeira execução</span><span class="sxs-lookup"><span data-stu-id="98cd9-425">First-run experience</span></span>
* <span data-ttu-id="98cd9-426">Telas introdutórias</span><span class="sxs-lookup"><span data-stu-id="98cd9-426">Introductory screens</span></span>
* <span data-ttu-id="98cd9-427">Dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="98cd9-427">Tooltips</span></span>
* <span data-ttu-id="98cd9-428">Coach mão</span><span class="sxs-lookup"><span data-stu-id="98cd9-428">Hand coach</span></span>
* <span data-ttu-id="98cd9-429">Seção de ajuda</span><span class="sxs-lookup"><span data-stu-id="98cd9-429">Help section</span></span>
* <span data-ttu-id="98cd9-430">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="98cd9-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-431">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-431">Recommendations</span></span>

* <span data-ttu-id="98cd9-432">Use os métodos de entrada padrão sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="98cd9-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="98cd9-433">Fornece demonstrações, tutoriais e dicas de ferramenta para métodos de entrada não padrão.</span><span class="sxs-lookup"><span data-stu-id="98cd9-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="98cd9-434">Use um modelo de interação consistente em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-435">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-436">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-436">Documentation</span></span>

* [<span data-ttu-id="98cd9-437">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="98cd9-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="98cd9-438">Objetos interagível</span><span class="sxs-lookup"><span data-stu-id="98cd9-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="98cd9-439">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="98cd9-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="98cd9-440">Cursores</span><span class="sxs-lookup"><span data-stu-id="98cd9-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="98cd9-441">Conforto e olhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="98cd9-442">Gestos</span><span class="sxs-lookup"><span data-stu-id="98cd9-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="98cd9-443">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="98cd9-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="98cd9-444">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="98cd9-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="98cd9-445">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="98cd9-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="98cd9-446">Guia de portabilidade de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="98cd9-447">Entrada do teclado no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="98cd9-448">Foco no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="98cd9-449">Gestos e controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="98cd9-450">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="98cd9-451">Teclado, mouse e entrada do controlador no DirectX</span><span class="sxs-lookup"><span data-stu-id="98cd9-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="98cd9-452">Olhar fixo com cabeça e olhos no DirectX</span><span class="sxs-lookup"><span data-stu-id="98cd9-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="98cd9-453">Controladores de mãos e emovimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="98cd9-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="98cd9-454">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="98cd9-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="98cd9-455">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="98cd9-455">Tools and tutorials</span></span>

* [<span data-ttu-id="98cd9-456">Estudo de caso: A busca de computação mais pessoais</span><span class="sxs-lookup"><span data-stu-id="98cd9-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="98cd9-457">Estudo de conversão: UI HoloStudio e lições aprendidas de design de interação</span><span class="sxs-lookup"><span data-stu-id="98cd9-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="98cd9-458">Aplicativo de exemplo: Tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="98cd9-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="98cd9-459">Aplicativo de exemplo: Módulo Lunar</span><span class="sxs-lookup"><span data-stu-id="98cd9-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="98cd9-460">Entrada do MR 210: foco</span><span class="sxs-lookup"><span data-stu-id="98cd9-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="98cd9-461">Entrada do MR 211: Gestos</span><span class="sxs-lookup"><span data-stu-id="98cd9-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="98cd9-462">Entrada do MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="98cd9-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="98cd9-463">Objetos interagível</span><span class="sxs-lookup"><span data-stu-id="98cd9-463">Interactable objects</span></span>

<span data-ttu-id="98cd9-464">Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D.</span><span class="sxs-lookup"><span data-stu-id="98cd9-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="98cd9-465">No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais.</span><span class="sxs-lookup"><span data-stu-id="98cd9-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="98cd9-466">Nada pode ser um objeto Interagível que dispara um evento.</span><span class="sxs-lookup"><span data-stu-id="98cd9-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="98cd9-467">Um objeto interagível pode ser representado como qualquer coisa uma xícara de café na tabela para um balão flutuar no ar.</span><span class="sxs-lookup"><span data-stu-id="98cd9-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="98cd9-468">Independentemente da forma, objetos interagível devem ser claramente reconhecíveis por usuário por meio de indicações de áudio e vídeo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-469">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-471"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-472">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-472">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-473">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-474">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-474">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-475">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-475">Best</span></span>  |  <span data-ttu-id="98cd9-476">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-476">Meets</span></span> |  <span data-ttu-id="98cd9-477">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-478">Independentemente do formulário, objetos interagível são reconhecidos por meio de indicações de áudio e vídeo em três estados: ocioso, direcionadas e selecionado.</span><span class="sxs-lookup"><span data-stu-id="98cd9-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="98cd9-479">"Consulte, diga" é claro e consistente usado em toda a experiência.</span><span class="sxs-lookup"><span data-stu-id="98cd9-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="98cd9-480">Objetos são dimensionados e distribuídos para permitir o direcionamento de sem erros.</span><span class="sxs-lookup"><span data-stu-id="98cd9-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="98cd9-481">Usuário pode reconhecer o objeto como interagível por meio de comentários de áudio ou de visual e de destino e ativar o objeto.</span><span class="sxs-lookup"><span data-stu-id="98cd9-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="98cd9-482">Considerando sem indicações de áudio ou de visual, usuário não pode reconhecer um objeto interagível.</span><span class="sxs-lookup"><span data-stu-id="98cd9-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="98cd9-483">As interações são propenso a falhas devido a escala do objeto ou a distância entre os objetos.</span><span class="sxs-lookup"><span data-stu-id="98cd9-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-484">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-484">How to measure</span></span>

* <span data-ttu-id="98cd9-485">Objetos interagível podem ser reconhecidos como 'interagível'; incluindo conteúdo específico do aplicativo, menus e botões.</span><span class="sxs-lookup"><span data-stu-id="98cd9-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="98cd9-486">Como regra geral deve haver uma indicação visual e áudio ao direcionar objetos interagível.</span><span class="sxs-lookup"><span data-stu-id="98cd9-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-487">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-487">Recommendations</span></span>

* <span data-ttu-id="98cd9-488">Use comentários de áudio e vídeo para interações.</span><span class="sxs-lookup"><span data-stu-id="98cd9-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="98cd9-489">Feedback visual deve ser diferenciada para cada estado (ocioso, destino, selecionado) de entrada</span><span class="sxs-lookup"><span data-stu-id="98cd9-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="98cd9-490">Objetos interagível devem ser dimensionados e colocados para direcionamento de sem erros.</span><span class="sxs-lookup"><span data-stu-id="98cd9-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="98cd9-491">Os objetos agrupados interagível (por exemplo, uma barra de menus ou lista) devem ter espaçamento correto para o direcionamento.</span><span class="sxs-lookup"><span data-stu-id="98cd9-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="98cd9-492">Botões e menus que dão suporte ao comando de voz devem fornecer rótulos de texto para a palavra-chave de comando ("vê-lo, diga")</span><span class="sxs-lookup"><span data-stu-id="98cd9-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-493">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-494">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-494">Documentation</span></span>

* [<span data-ttu-id="98cd9-495">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="98cd9-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="98cd9-496">Texto no Unity</span><span class="sxs-lookup"><span data-stu-id="98cd9-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="98cd9-497">Barra de aplicativos e caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="98cd9-497">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="98cd9-498">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="98cd9-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="98cd9-499">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="98cd9-499">Tools and tutorials</span></span>

* [<span data-ttu-id="98cd9-500">Kit de ferramentas de realidade misturada - UX</span><span class="sxs-lookup"><span data-stu-id="98cd9-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="98cd9-501">Espaço disponível para verificação</span><span class="sxs-lookup"><span data-stu-id="98cd9-501">Room scanning</span></span>

<span data-ttu-id="98cd9-502">Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="98cd9-503">A integridade e a qualidade dos dados depende de vários fatores, incluindo a quantidade de exploração que o usuário tenha feito, quanto tempo se passou desde a exploração e se os objetos como móveis e portas foram movidas desde a área de verificação de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="98cd9-504">Muitos aplicativos analisará os dados de mapeamento espacial no início da experiência para avaliar se o usuário deve executar etapas adicionais para melhorar a integridade e a qualidade do mapa espacial.</span><span class="sxs-lookup"><span data-stu-id="98cd9-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="98cd9-505">Se o usuário é necessário para verificar o ambiente, desmarque diretrizes devem ser fornecida durante a experiência de verificação.</span><span class="sxs-lookup"><span data-stu-id="98cd9-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-506">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-508"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-509">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-509">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-510">❌</span><span class="sxs-lookup"><span data-stu-id="98cd9-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-511">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-511">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-512">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-512">Best</span></span>  |  <span data-ttu-id="98cd9-513">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-513">Meets</span></span> |  <span data-ttu-id="98cd9-514">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-515">Visualização da malha espacial informar os usuários de verificação está em andamento.</span><span class="sxs-lookup"><span data-stu-id="98cd9-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="98cd9-516">Claramente o usuário sabe o que fazer e quando a varredura inicia e para.</span><span class="sxs-lookup"><span data-stu-id="98cd9-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="98cd9-517">Visualização da malha espacial for fornecida, mas o usuário pode não sabe claramente o que fazer e nenhuma informação de progresso é fornecida.</span><span class="sxs-lookup"><span data-stu-id="98cd9-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="98cd9-518">Nenhuma visualização da malha.</span><span class="sxs-lookup"><span data-stu-id="98cd9-518">No visualization of mesh.</span></span> <span data-ttu-id="98cd9-519">Nenhuma informação de orientação fornecida ao usuário sobre onde procurar, ou quando a varredura inicia/para.</span><span class="sxs-lookup"><span data-stu-id="98cd9-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-520">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-520">How to measure</span></span>

* <span data-ttu-id="98cd9-521">Durante uma verificação de espaço necessário, são fornecidas orientações de áudio e vídeo que indica onde procurar e quando iniciar e Parar verificação.</span><span class="sxs-lookup"><span data-stu-id="98cd9-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-522">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-522">Recommendations</span></span>

* <span data-ttu-id="98cd9-523">Indica quanto o volume total nas proximidades usuários precisa fazer parte da experiência.</span><span class="sxs-lookup"><span data-stu-id="98cd9-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="98cd9-524">Comunicar-se quando a verificação é iniciado e é interrompido, como um indicador de progresso.</span><span class="sxs-lookup"><span data-stu-id="98cd9-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="98cd9-525">Use uma visualização da malha durante a verificação.</span><span class="sxs-lookup"><span data-stu-id="98cd9-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="98cd9-526">Fornece indicações de áudio e vídeo para incentivar o usuário procure e mover-se na sala.</span><span class="sxs-lookup"><span data-stu-id="98cd9-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="98cd9-527">Informar ao usuário aonde ir para melhorar os dados.</span><span class="sxs-lookup"><span data-stu-id="98cd9-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="98cd9-528">Em muitos casos, talvez seja melhor informar ao usuário o que precisam (por exemplo, examinar o limite, procure por trás de móveis), para obter a qualidade de verificação necessárias.</span><span class="sxs-lookup"><span data-stu-id="98cd9-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-529">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="98cd9-530">Documentação</span><span class="sxs-lookup"><span data-stu-id="98cd9-530">Documentation</span></span>

* [<span data-ttu-id="98cd9-531">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="98cd9-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="98cd9-532">Estudo de caso: Expandindo os recursos de mapeamento espacial do HoloLens</span><span class="sxs-lookup"><span data-stu-id="98cd9-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="98cd9-533">Estudo de caso: Projeto de som espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="98cd9-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="98cd9-534">Estudo de caso: Criando uma experiência imersiva em fragmentos</span><span class="sxs-lookup"><span data-stu-id="98cd9-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="98cd9-535">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="98cd9-535">Tools and tutorials</span></span>

* [<span data-ttu-id="98cd9-536">Kit de ferramentas de realidade misturada - UX</span><span class="sxs-lookup"><span data-stu-id="98cd9-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="98cd9-537">Indicadores direcionais</span><span class="sxs-lookup"><span data-stu-id="98cd9-537">Directional indicators</span></span>

<span data-ttu-id="98cd9-538">Em um aplicativo de realidade misturada, o conteúdo pode estar fora de vista do campo ou obstruídos pelo objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="98cd9-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="98cd9-539">Um aplicativo bem projetado tornará mais fácil para o usuário localizar conteúdo não visíveis.</span><span class="sxs-lookup"><span data-stu-id="98cd9-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="98cd9-540">Indicadores direcionais alertam um usuário ao conteúdo importante e fornecem orientação para o conteúdo em relação à posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="98cd9-541">Diretrizes para o conteúdo não visíveis podem assumir a forma de emissores de som, as setas direcionais ou indicações visuais diretas.</span><span class="sxs-lookup"><span data-stu-id="98cd9-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-542">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-544"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-545">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-545">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-546">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-547">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-547">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-548">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-548">Best</span></span>  |  <span data-ttu-id="98cd9-549">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-549">Meets</span></span> |  <span data-ttu-id="98cd9-550">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-551">As indicações de áudio e vídeo diretamente guiam o usuário ao conteúdo relevante fora o campo de visualização.</span><span class="sxs-lookup"><span data-stu-id="98cd9-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="98cd9-552">Uma seta ou alguns indicador que aponta para o usuário na direção geral do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="98cd9-553">Conteúdo relevante é fora do campo de visão e ruim ou nenhuma orientação para a localização é fornecida ao usuário.</span><span class="sxs-lookup"><span data-stu-id="98cd9-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-554">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-554">How to measure</span></span>

* <span data-ttu-id="98cd9-555">O conteúdo relevante fora do campo de vista do usuário é descoberto por meio de indicações visuais e/ou áudio.</span><span class="sxs-lookup"><span data-stu-id="98cd9-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-556">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-556">Recommendations</span></span>

* <span data-ttu-id="98cd9-557">Quando o conteúdo relevante estiver fora de vista de campo do usuário, use indicadores direcionais e as indicações de áudio para orientar o usuário ao conteúdo.</span><span class="sxs-lookup"><span data-stu-id="98cd9-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="98cd9-558">Em muitos casos, um guia visual direto é preferível as setas direcionais.</span><span class="sxs-lookup"><span data-stu-id="98cd9-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="98cd9-559">Indicadores direcionais não devem ser criados no cursor.</span><span class="sxs-lookup"><span data-stu-id="98cd9-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-560">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-560">Resources</span></span>

* [<span data-ttu-id="98cd9-561">Quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="98cd9-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="98cd9-562">Carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="98cd9-562">Data loading</span></span>

<span data-ttu-id="98cd9-563">Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.</span><span class="sxs-lookup"><span data-stu-id="98cd9-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="98cd9-564">Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso é visível e também pode indicar quanto tempo o tempo de espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="98cd9-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="98cd9-565">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="98cd9-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="98cd9-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="98cd9-567"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="98cd9-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="98cd9-568">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-568">✔️</span></span></td>
        <td><span data-ttu-id="98cd9-569">✔️</span><span class="sxs-lookup"><span data-stu-id="98cd9-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="98cd9-570">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="98cd9-570">Quality criteria</span></span>

|  <span data-ttu-id="98cd9-571">Melhor</span><span class="sxs-lookup"><span data-stu-id="98cd9-571">Best</span></span>  |  <span data-ttu-id="98cd9-572">Atenda às</span><span class="sxs-lookup"><span data-stu-id="98cd9-572">Meets</span></span> |  <span data-ttu-id="98cd9-573">falhar</span><span class="sxs-lookup"><span data-stu-id="98cd9-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="98cd9-574">Indicador visual animado, na forma de uma barra de progresso ou um anel, mostrando o progresso durante qualquer carregando ou processamento de dados.</span><span class="sxs-lookup"><span data-stu-id="98cd9-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="98cd9-575">O indicador visual fornece orientações sobre quanto tempo de espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="98cd9-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="98cd9-576">Usuário é informado de que o carregamento de dados está em andamento, mas não há nenhuma indicação de quanto tempo de espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="98cd9-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="98cd9-577">Nenhum carregamento de dados ou indicadores de processo para a tarefa demorando mais do que 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="98cd9-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="98cd9-578">Como medir</span><span class="sxs-lookup"><span data-stu-id="98cd9-578">How to measure</span></span>

* <span data-ttu-id="98cd9-579">Durante o carregamento de dados, verifique se que não houver nenhum estado em branco por mais de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="98cd9-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="98cd9-580">Recomendações</span><span class="sxs-lookup"><span data-stu-id="98cd9-580">Recommendations</span></span>

* <span data-ttu-id="98cd9-581">Forneça um animator de carregamento de dados mostrando o progresso em qualquer situação, quando o usuário poderão perceber esse aplicativo tenha interrompido ou falhou.</span><span class="sxs-lookup"><span data-stu-id="98cd9-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="98cd9-582">Uma regra prática razoável é qualquer atividade de 'carregamento' que pode levar mais de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="98cd9-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="98cd9-583">Recursos</span><span class="sxs-lookup"><span data-stu-id="98cd9-583">Resources</span></span>

* [<span data-ttu-id="98cd9-584">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="98cd9-584">Displaying progress</span></span>](progress.md)

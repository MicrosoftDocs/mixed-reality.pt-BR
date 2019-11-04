---
title: Critérios de qualidade do aplicativo
description: Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: critérios de qualidade do aplicativo, realidade misturada, aplicativo de realidade misturada
ms.openlocfilehash: f98111ebe9aacc30778e86501be41e6ac5f6d165
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437042"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="157fa-104">Critérios de qualidade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="157fa-104">App quality criteria</span></span>

<span data-ttu-id="157fa-105">Este documento descreve os principais fatores que afetam a qualidade dos aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="157fa-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="157fa-106">Para cada fator, as informações a seguir são fornecidas</span><span class="sxs-lookup"><span data-stu-id="157fa-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="157fa-107">Visão geral – uma breve descrição do fator de qualidade e por que ele é importante.</span><span class="sxs-lookup"><span data-stu-id="157fa-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="157fa-108">Impacto do dispositivo – qual tipo de o dispositivo de realidade misturada da janela é afetado.</span><span class="sxs-lookup"><span data-stu-id="157fa-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="157fa-109">Critérios de qualidade – como avaliar o fator de qualidade.</span><span class="sxs-lookup"><span data-stu-id="157fa-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="157fa-110">Como medir – métodos para medir (ou experimentar) o problema.</span><span class="sxs-lookup"><span data-stu-id="157fa-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="157fa-111">Recomendações – Resumo de abordagens para fornecer uma melhor experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="157fa-112">Recursos – desenvolvedor relevante e recursos de design que são úteis para criar melhores experiências de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="157fa-113">Taxa de quadros</span><span class="sxs-lookup"><span data-stu-id="157fa-113">Frame rate</span></span>

<span data-ttu-id="157fa-114">A taxa de quadros é o primeiro pilar da estabilidade do holograma e do conforto do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="157fa-115">A taxa de quadros abaixo dos destinos recomendados pode fazer com que os hologramas pareçam tremulação, afetando negativamente a believability da experiência e potencialmente causando fadiga de olho.</span><span class="sxs-lookup"><span data-stu-id="157fa-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="157fa-116">A taxa de quadros de destino para sua experiência em headsets de imersão de realidade mista do Windows será de 60Hz ou 90Hz, dependendo de quais computadores compatíveis com o Windows Mixed Reality você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="157fa-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="157fa-117">Para o HoloLens, a taxa de quadros de destino é 60.</span><span class="sxs-lookup"><span data-stu-id="157fa-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-118">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-120"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-121">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-121">✔️</span></span></td>
        <td><span data-ttu-id="157fa-122">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-123">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-123">Quality criteria</span></span>

|  <span data-ttu-id="157fa-124">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-124">Best</span></span>  |  <span data-ttu-id="157fa-125">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-125">Meets</span></span> |  <span data-ttu-id="157fa-126">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="157fa-127">O aplicativo atende consistentemente a meta de quadros por segundo (FPS) para o dispositivo de destino: 60fps no HoloLens; 90fps em ultra PCs; e 60fps nos PCs de base.</span><span class="sxs-lookup"><span data-stu-id="157fa-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="157fa-128">O aplicativo tem quedas de quadros intermitentes que não impedem a experiência principal; ou FPS é consistentemente menor do que a meta desejada, mas não impede a experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="157fa-129">O aplicativo está apresentando uma queda na taxa de quadros em média a cada dez segundos ou menos.</span><span class="sxs-lookup"><span data-stu-id="157fa-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="157fa-130">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-130">How to measure</span></span>

* <span data-ttu-id="157fa-131">Um grafo de taxa de quadros em tempo real é fornecido pelo [portal do dispositivo do Windows](using-the-windows-device-portal.md#system-performance) em "desempenho do sistema".</span><span class="sxs-lookup"><span data-stu-id="157fa-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="157fa-132">Para a depuração de desenvolvimento, adicione um contador de diagnóstico de taxa de quadros ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="157fa-133">Consulte recursos para um contador de exemplo.</span><span class="sxs-lookup"><span data-stu-id="157fa-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="157fa-134">Quedas de taxa de quadros podem ser experimentadas no dispositivo enquanto o aplicativo está em execução, movendo seu cabeçalho de lado para o outro.</span><span class="sxs-lookup"><span data-stu-id="157fa-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="157fa-135">Se o holograma mostrar uma movimentação de tremulação inesperada, a taxa de quadros baixa ou o plano de estabilidade provavelmente será a causa.</span><span class="sxs-lookup"><span data-stu-id="157fa-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-136">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-136">Recommendations</span></span>

* <span data-ttu-id="157fa-137">Adicione um contador de taxa de quadros no início do trabalho de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="157fa-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="157fa-138">As alterações que incorrem em uma taxa de quadros de queda devem ser avaliadas e resolvidas adequadamente como um bug de desempenho.</span><span class="sxs-lookup"><span data-stu-id="157fa-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-140">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-140">Documentation</span></span>

* [<span data-ttu-id="157fa-141">Entendendo o desempenho da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="157fa-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="157fa-142">Estabilidade e taxa de quadros do holograma</span><span class="sxs-lookup"><span data-stu-id="157fa-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="157fa-143">Orçamento de desempenho do ativo</span><span class="sxs-lookup"><span data-stu-id="157fa-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="157fa-144">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="157fa-145">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="157fa-145">Tools and tutorials</span></span>

* [<span data-ttu-id="157fa-146">MRToolkit, exibição do contador de FPS</span><span class="sxs-lookup"><span data-stu-id="157fa-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="157fa-147">MRToolkit, sombreadores</span><span class="sxs-lookup"><span data-stu-id="157fa-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="157fa-148">Referências externas</span><span class="sxs-lookup"><span data-stu-id="157fa-148">External references</span></span>

* [<span data-ttu-id="157fa-149">Unity, otimizando aplicativos móveis</span><span class="sxs-lookup"><span data-stu-id="157fa-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="157fa-150">Estabilidade do holograma</span><span class="sxs-lookup"><span data-stu-id="157fa-150">Hologram stability</span></span>

<span data-ttu-id="157fa-151">Os hologramas estáveis aumentarão a usabilidade e a believability de seu aplicativo e criarão uma experiência de exibição mais confortável para o usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="157fa-152">A qualidade da estabilidade do holograma é um resultado do bom desenvolvimento de aplicativos e da capacidade do dispositivo de entender (controlar) seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="157fa-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="157fa-153">Embora a taxa de quadros seja o primeiro pilar da estabilidade, outros fatores podem afetar a estabilidade, incluindo:</span><span class="sxs-lookup"><span data-stu-id="157fa-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="157fa-154">Uso do plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="157fa-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="157fa-155">Distâncias para âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="157fa-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="157fa-156">Controle alterações</span><span class="sxs-lookup"><span data-stu-id="157fa-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-157">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-159"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-160">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-161">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-161">Quality criteria</span></span>

|  <span data-ttu-id="157fa-162">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-162">Best</span></span>  |  <span data-ttu-id="157fa-163">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-163">Meets</span></span> |  <span data-ttu-id="157fa-164">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-165">Os hologramas parecem consistentemente estáveis.</span><span class="sxs-lookup"><span data-stu-id="157fa-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="157fa-166">Conteúdo secundário exibe movimento inesperado; ou o movimento inesperado não impede a experiência geral do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="157fa-167">O conteúdo principal no quadro exibe movimento inesperado.</span><span class="sxs-lookup"><span data-stu-id="157fa-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="157fa-168">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-168">How to measure</span></span>

<span data-ttu-id="157fa-169">Ao desgastar o dispositivo e exibir a experiência:</span><span class="sxs-lookup"><span data-stu-id="157fa-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="157fa-170">Mova seu cabeçalho do lado a lado, se os hologramas mostrarem movimento inesperado, a taxa de quadros baixa ou o alinhamento impróprio do plano de estabilidade para o plano focal é a causa provável.</span><span class="sxs-lookup"><span data-stu-id="157fa-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="157fa-171">Mova-se para os hologramas e o ambiente, procure comportamentos como, por exemplo, nada e salto.</span><span class="sxs-lookup"><span data-stu-id="157fa-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="157fa-172">Esse tipo de movimento é provavelmente causado pelo dispositivo não rastreando o ambiente ou pela distância para a âncora espacial.</span><span class="sxs-lookup"><span data-stu-id="157fa-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="157fa-173">Se houver grandes ou vários hologramas no quadro, observe o comportamento do holograma em várias profundidades ao mover sua posição de cabeçalho de lado a lado, se shakiness parecer que isso é provavelmente causado pelo plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="157fa-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="157fa-174">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-174">Recomendations</span></span>

* <span data-ttu-id="157fa-175">Adicione um contador de taxa de quadros no início do trabalho de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="157fa-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="157fa-176">Use o plano de estabilização.</span><span class="sxs-lookup"><span data-stu-id="157fa-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="157fa-177">Sempre renderizar hologramas ancorados dentro de 3 metros de sua âncora.</span><span class="sxs-lookup"><span data-stu-id="157fa-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="157fa-178">Verifique se o ambiente está configurado para o acompanhamento adequado.</span><span class="sxs-lookup"><span data-stu-id="157fa-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="157fa-179">Projete sua experiência para evitar hologramas em vários níveis de profundidade focal dentro do quadro.</span><span class="sxs-lookup"><span data-stu-id="157fa-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-180">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-181">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-181">Documentation</span></span>

* [<span data-ttu-id="157fa-182">Estabilidade e taxa de quadros do holograma</span><span class="sxs-lookup"><span data-stu-id="157fa-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="157fa-183">Estudo de caso, usando o plano de estabilização</span><span class="sxs-lookup"><span data-stu-id="157fa-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="157fa-184">Entendendo o desempenho da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="157fa-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="157fa-185">Recomendações de desempenho para Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="157fa-186">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="157fa-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="157fa-187">Manipulação de erros de controle</span><span class="sxs-lookup"><span data-stu-id="157fa-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="157fa-188">Quadro estacionário de referência</span><span class="sxs-lookup"><span data-stu-id="157fa-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="157fa-189">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="157fa-189">Tools and tutorials</span></span>

* [<span data-ttu-id="157fa-190">Sr Companion Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="157fa-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="157fa-191">Posição dos hologramas em superfícies reais</span><span class="sxs-lookup"><span data-stu-id="157fa-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="157fa-192">Os desalinhamentos de hologramas com objetos físicos (se a intenção de serem colocados em relação uns aos outros) são uma indicação clara da não União de hologramas e do mundo real.</span><span class="sxs-lookup"><span data-stu-id="157fa-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="157fa-193">A precisão do posicionamento deve ser relativa às necessidades do cenário; por exemplo, o posicionamento de superfície geral pode usar o mapa espacial, mas o posicionamento mais preciso exigirá algum uso de marcadores e calibragem.</span><span class="sxs-lookup"><span data-stu-id="157fa-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-194">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-196"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-197">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-198">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-198">Quality criteria</span></span>

|  <span data-ttu-id="157fa-199">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-199">Best</span></span>  |  <span data-ttu-id="157fa-200">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-200">Meets</span></span> |  <span data-ttu-id="157fa-201">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="157fa-202">Os hologramas se alinham à superfície normalmente no intervalo de centímetros para polegadas.</span><span class="sxs-lookup"><span data-stu-id="157fa-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="157fa-203">Se for necessário mais precisão, o aplicativo deverá fornecer um meio eficiente de colaboração na especificação do aplicativo desejado.</span><span class="sxs-lookup"><span data-stu-id="157fa-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="157fa-204">N/D</span><span class="sxs-lookup"><span data-stu-id="157fa-204">NA</span></span> | <span data-ttu-id="157fa-205">Os hologramas aparecem desalinhados com o objeto de destino físico, dividindo o plano de superfície ou aparecendo flutuando para fora da superfície.</span><span class="sxs-lookup"><span data-stu-id="157fa-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="157fa-206">Se a precisão for necessária, os hologramas devem atender à especificação de proximidade do cenário.</span><span class="sxs-lookup"><span data-stu-id="157fa-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="157fa-207">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-207">How to measure</span></span>

* <span data-ttu-id="157fa-208">Os hologramas que são colocados no mapa espacial não devem parecer muito flutuar acima ou abaixo da superfície.</span><span class="sxs-lookup"><span data-stu-id="157fa-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="157fa-209">Os hologramas que exigem posicionamento preciso devem ter alguma forma de marcador e sistema de calibração que seja precisa do requisito do cenário.</span><span class="sxs-lookup"><span data-stu-id="157fa-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-210">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-210">Recommendations</span></span>

* <span data-ttu-id="157fa-211">O mapa espacial é útil para colocar objetos em superfícies quando a precisão não é necessária.</span><span class="sxs-lookup"><span data-stu-id="157fa-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="157fa-212">Para obter a melhor precisão, use marcadores ou cartazes para definir os hologramas e um controlador Xbox (ou algum mecanismo de alinhamento manual) para a calibragem final.</span><span class="sxs-lookup"><span data-stu-id="157fa-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="157fa-213">Considere quebrar hologramas grandes e extras em partes lógicas e alinhar cada parte à superfície.</span><span class="sxs-lookup"><span data-stu-id="157fa-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="157fa-214">O IPD (Interpupilary Distance) definido incorretamente também pode afetar o alinhamento do holograma.</span><span class="sxs-lookup"><span data-stu-id="157fa-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="157fa-215">Sempre configure o HoloLens para o IPD do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-216">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-217">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-217">Documentation</span></span>

* [<span data-ttu-id="157fa-218">Posicionamento de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="157fa-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="157fa-219">Processo de verificação de sala</span><span class="sxs-lookup"><span data-stu-id="157fa-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="157fa-220">Práticas recomendadas das âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="157fa-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="157fa-221">Manipulação de erros de controle</span><span class="sxs-lookup"><span data-stu-id="157fa-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="157fa-222">Mapeamento espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="157fa-223">Visão geral do desenvolvimento do Vuforia</span><span class="sxs-lookup"><span data-stu-id="157fa-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="157fa-224">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="157fa-224">Tools and tutorials</span></span>

* [<span data-ttu-id="157fa-225">MR espacial 230: mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="157fa-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="157fa-226">Sr Toolkit, bibliotecas de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="157fa-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="157fa-227">Sr Companion Kit, exemplo de calibração de pôster</span><span class="sxs-lookup"><span data-stu-id="157fa-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="157fa-228">Sr Companion Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="157fa-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="157fa-229">Referências externas</span><span class="sxs-lookup"><span data-stu-id="157fa-229">External references</span></span>

* [<span data-ttu-id="157fa-230">Estudo de caso do Lowes, alinhamento de precisão</span><span class="sxs-lookup"><span data-stu-id="157fa-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="157fa-231">Exibindo a zona de conforto</span><span class="sxs-lookup"><span data-stu-id="157fa-231">Viewing zone of comfort</span></span>

<span data-ttu-id="157fa-232">Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergem colocando o conteúdo e os hologramas em várias profundidades.</span><span class="sxs-lookup"><span data-stu-id="157fa-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="157fa-233">Os usuários com o HoloLens serão sempre acomodados a 2,0 m para manter uma imagem clara porque as exibições do HoloLens são corrigidas a uma distância óptica de aproximadamente 2,0 m para longe do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="157fa-234">A profundidade de conteúdo inadequado pode levar ao Visual discomfort ou fadiga.</span><span class="sxs-lookup"><span data-stu-id="157fa-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-235">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-237"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-238">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-239">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="157fa-240">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="157fa-241">Coloque o conteúdo em 2m.</span><span class="sxs-lookup"><span data-stu-id="157fa-241">Place content at 2m.</span></span></li><li><span data-ttu-id="157fa-242">Quando os hologramas não podem ser colocados em 2m e os conflitos entre a convergência e a acomodação não podem ser evitados, a zona ideal para o posicionamento do holograma é entre 1,25 m e 5 min.</span><span class="sxs-lookup"><span data-stu-id="157fa-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="157fa-243">Em todos os casos, os designers devem estruturar o conteúdo para incentivar os usuários a interagir de 1 + m (por exemplo, ajustar o tamanho do conteúdo e os parâmetros de posicionamento padrão).</span><span class="sxs-lookup"><span data-stu-id="157fa-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="157fa-244">A menos que não seja especificamente exigido pelo cenário, um plano de recorte deve ser implementado com FadeOut a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="157fa-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="157fa-245">Nos casos em que a observação mais próxima de um holograma sem movimento é necessária, o conteúdo não deve ser mais próximo de 50cm.</span><span class="sxs-lookup"><span data-stu-id="157fa-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="157fa-246">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-246">Meets</span></span></td><td> <span data-ttu-id="157fa-247">O conteúdo está dentro das diretrizes de visualização e movimentação, mas uso inadequado ou não uso do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="157fa-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="157fa-248">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-248">Fail</span></span> </td><td> <span data-ttu-id="157fa-249">O conteúdo é apresentado muito próximo (normalmente &lt;1,25 m ou &lt;50cm para hologramas fixos que exigem uma observação mais detalhada.)</span><span class="sxs-lookup"><span data-stu-id="157fa-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="157fa-250">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-250">How to measure</span></span>

* <span data-ttu-id="157fa-251">O conteúdo normalmente deve ser de 2m, mas não mais de 1,25 ou mais do que 5 min.</span><span class="sxs-lookup"><span data-stu-id="157fa-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="157fa-252">Com poucas exceções, a distância de renderização de recorte de HoloLens deve ser definida como. 85CM com esmaecimento de conteúdo a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="157fa-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="157fa-253">Aborde o conteúdo e observe o efeito do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="157fa-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="157fa-254">O conteúdo estacionário não deve estar mais próximo do que 50cm.</span><span class="sxs-lookup"><span data-stu-id="157fa-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-255">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-255">Recommendations</span></span>

* <span data-ttu-id="157fa-256">Crie conteúdo para a distância de exibição ideal de 2m.</span><span class="sxs-lookup"><span data-stu-id="157fa-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="157fa-257">Defina a distância de renderização de recorte como 85cm com esmaecimento de conteúdo a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="157fa-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="157fa-258">Para hologramas estáticos que precisam de exibição mais próxima, o plano de recorte não deve ser mais próximo que 30cm e FadeOut deve iniciar pelo menos 10cm fora do plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="157fa-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-259">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-259">Resources</span></span>

* [<span data-ttu-id="157fa-260">Distância de renderização</span><span class="sxs-lookup"><span data-stu-id="157fa-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="157fa-261">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="157fa-262">Experimentando a escala</span><span class="sxs-lookup"><span data-stu-id="157fa-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="157fa-263">Texto, tamanho de fonte recomendado</span><span class="sxs-lookup"><span data-stu-id="157fa-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="157fa-264">Alternância de profundidade</span><span class="sxs-lookup"><span data-stu-id="157fa-264">Depth switching</span></span>

<span data-ttu-id="157fa-265">Independentemente da exibição da zona de problemas de conforto, as demandas pelo usuário de alternar com frequência ou rapidamente entre objetos focalmente próximos e distantes (incluindo hologramas e conteúdo do mundo real) podem levar a oculomotor fadiga e discomfort geral.</span><span class="sxs-lookup"><span data-stu-id="157fa-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-266">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-268"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-269">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-269">✔️</span></span></td>
        <td><span data-ttu-id="157fa-270">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-271">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-271">Quality criteria</span></span>

|  <span data-ttu-id="157fa-272">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-272">Best</span></span>  |  <span data-ttu-id="157fa-273">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-273">Meets</span></span> |  <span data-ttu-id="157fa-274">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-275">Alternância de profundidade limitada ou natural que não faz com que o usuário se concentre de volta natural.</span><span class="sxs-lookup"><span data-stu-id="157fa-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="157fa-276">A mudança de profundidade abrupta é fundamental e projetada para a experiência do aplicativo ou para o interruptor de profundidade abrupta que é causado pelo conteúdo real do mundo inesperado.</span><span class="sxs-lookup"><span data-stu-id="157fa-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="157fa-277">Opção de profundidade consistente ou alternância de profundidade abrupta que não é necessária ou essencial para a experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="157fa-278">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-278">How to measure</span></span>

* <span data-ttu-id="157fa-279">Se o aplicativo exigir que o usuário altere o foco de profundidade de forma consistente e/ou abruptamente, haverá um problema de alternância de profundidade.</span><span class="sxs-lookup"><span data-stu-id="157fa-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-280">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-280">Recommendations</span></span>

* <span data-ttu-id="157fa-281">Mantenha o conteúdo principal em um plano focal consistente e verifique se o plano de estabilização corresponde ao plano focal.</span><span class="sxs-lookup"><span data-stu-id="157fa-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="157fa-282">Isso aliviará o oculomotor fadiga e o movimento de holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="157fa-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-283">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-283">Resources</span></span>

* [<span data-ttu-id="157fa-284">Distância de renderização</span><span class="sxs-lookup"><span data-stu-id="157fa-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="157fa-285">Ponto de foco no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="157fa-286">Uso de som espacial</span><span class="sxs-lookup"><span data-stu-id="157fa-286">Use of spatial sound</span></span>

<span data-ttu-id="157fa-287">No Windows Mixed Reality, o mecanismo de áudio fornece o componente auricular da experiência de realidade misturada por meio da simulação de som 3D usando a direção, a distância e as simulações ambientais.</span><span class="sxs-lookup"><span data-stu-id="157fa-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="157fa-288">O uso de som espacial em um aplicativo permite que os desenvolvedores coloquem os sons de forma convincente em um espaço 3 dimensional (esfera) em todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="157fa-289">Esses sons parecerão como se estivessem vindo de objetos físicos reais ou de hologramas de realidade misturada no ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="157fa-290">O som espacial é uma ferramenta poderosa para imersão, acessibilidade e design de UX em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="157fa-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-291">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-293"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-294">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-294">✔️</span></span></td>
        <td><span data-ttu-id="157fa-295">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-296">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-296">Quality criteria</span></span>

|  <span data-ttu-id="157fa-297">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-297">Best</span></span>  |  <span data-ttu-id="157fa-298">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-298">Meets</span></span> |  <span data-ttu-id="157fa-299">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-300">O som é logicamente espacial e o UX usa o som adequadamente para auxiliar na descoberta de objetos e nos comentários dos usuários.</span><span class="sxs-lookup"><span data-stu-id="157fa-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="157fa-301">O som é natural e relevante para objetos e normalizados em todo o cenário.</span><span class="sxs-lookup"><span data-stu-id="157fa-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="157fa-302">O áudio espacial é usado adequadamente para believability, mas ausente como meio de ajudar com os comentários do usuário e a descoberta.</span><span class="sxs-lookup"><span data-stu-id="157fa-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="157fa-303">O som não está espacial como esperado e/ou falta de som para auxiliar o usuário no UX.</span><span class="sxs-lookup"><span data-stu-id="157fa-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="157fa-304">Ou o áudio espacial não foi considerado ou usado no design do cenário.</span><span class="sxs-lookup"><span data-stu-id="157fa-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="157fa-305">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-305">How to measure</span></span>

* <span data-ttu-id="157fa-306">Em geral, os sons relevantes devem emitir de hologramas de destino (por exemplo, som latido proveniente do Holographic Dog.)</span><span class="sxs-lookup"><span data-stu-id="157fa-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="157fa-307">As indicações de som devem ser usadas em todo o UX para ajudar o usuário com comentários ou conscientização de ações fora do quadro do Holographic.</span><span class="sxs-lookup"><span data-stu-id="157fa-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-308">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-308">Recommendations</span></span>

* <span data-ttu-id="157fa-309">Use o áudio espacial para auxiliar na descoberta de objeto e nas interfaces do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="157fa-310">Os sons reais funcionam melhor que o sintetizado ou o som não natural.</span><span class="sxs-lookup"><span data-stu-id="157fa-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="157fa-311">A maioria dos sons deve ser espacial.</span><span class="sxs-lookup"><span data-stu-id="157fa-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="157fa-312">Evite emissores invisíveis.</span><span class="sxs-lookup"><span data-stu-id="157fa-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="157fa-313">Evite mascaramento espacial.</span><span class="sxs-lookup"><span data-stu-id="157fa-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="157fa-314">Normalizar todos os sons.</span><span class="sxs-lookup"><span data-stu-id="157fa-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-315">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-316">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-316">Documentation</span></span>

* [<span data-ttu-id="157fa-317">Som espacial</span><span class="sxs-lookup"><span data-stu-id="157fa-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="157fa-318">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="157fa-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="157fa-319">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="157fa-320">Estudo de caso, som espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="157fa-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="157fa-321">Estudo de caso, usando o som espacial em RoboRaid</span><span class="sxs-lookup"><span data-stu-id="157fa-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="157fa-322">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="157fa-322">Tools and tutorials</span></span>

* [<span data-ttu-id="157fa-323">MR espacial 220: som espacial</span><span class="sxs-lookup"><span data-stu-id="157fa-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="157fa-324">MRToolkit, áudio espacial</span><span class="sxs-lookup"><span data-stu-id="157fa-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="157fa-325">Foco nos limites do quadro Holographic (FOV)</span><span class="sxs-lookup"><span data-stu-id="157fa-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="157fa-326">Experiências de usuário bem projetadas podem criar e manter um contexto útil do ambiente virtual que se estende pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="157fa-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="157fa-327">Reduzir o efeito dos limites de FOV envolve um design elaborado de escala e contexto de conteúdo, uso de áudio espacial, sistemas de orientação e posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="157fa-328">Se for feito certo, o usuário se sentirá menos prejudicado pelos limites do FOV enquanto tem uma experiência de aplicativo confortável.</span><span class="sxs-lookup"><span data-stu-id="157fa-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-329">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-329">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-331"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-332">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-332">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-333">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-333">Quality criteria</span></span>

|  <span data-ttu-id="157fa-334">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-334">Best</span></span>  |  <span data-ttu-id="157fa-335">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-335">Meets</span></span> |  <span data-ttu-id="157fa-336">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-337">O usuário nunca perde o contexto e a exibição é confortável.</span><span class="sxs-lookup"><span data-stu-id="157fa-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="157fa-338">A assistência de contexto é fornecida para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="157fa-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="157fa-339">As diretrizes de descoberta e exibição são fornecidas para objetos fora do quadro.</span><span class="sxs-lookup"><span data-stu-id="157fa-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="157fa-340">Em geral, o design de movimento e a escala dos hologramas são apropriados para uma experiência de exibição confortável.</span><span class="sxs-lookup"><span data-stu-id="157fa-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="157fa-341">O usuário nunca perde o contexto, mas o movimento de pescoço extra pode ser necessário em situações limitadas.</span><span class="sxs-lookup"><span data-stu-id="157fa-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="157fa-342">Em situações limitadas, a escala faz com que os hologramas quebrem o quadro vertical ou horizontal, fazendo com que um movimento de pescoço exiba os hologramas.</span><span class="sxs-lookup"><span data-stu-id="157fa-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="157fa-343">O usuário provavelmente perderá o contexto e/ou o movimento de pescoço consistente é necessário para exibir hologramas.</span><span class="sxs-lookup"><span data-stu-id="157fa-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="157fa-344">Não há diretrizes de contexto para objetos Holographic grandes, movendo objetos fáceis de serem perdidos fora do quadro sem orientação de descoberta ou hologramas altos requer movimento de pescoço regular para exibição.</span><span class="sxs-lookup"><span data-stu-id="157fa-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="157fa-345">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-345">How to measure</span></span>

* <span data-ttu-id="157fa-346">O contexto de um holograma (grande) é perdido ou não compreendido devido a ser recortado nos limites.</span><span class="sxs-lookup"><span data-stu-id="157fa-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="157fa-347">É difícil encontrar o local dos hologramas devido à falta de diretores de atenção ou conteúdo que se movem rapidamente para dentro e para fora do quadro do Holographic.</span><span class="sxs-lookup"><span data-stu-id="157fa-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="157fa-348">O cenário requer um movimento regular e repetitivo para cima e para baixo para ver totalmente um holograma, resultando em fadiga de pescoço.</span><span class="sxs-lookup"><span data-stu-id="157fa-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-349">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-349">Recommendations</span></span>

* <span data-ttu-id="157fa-350">Inicie a experiência com objetos pequenos que se ajustam ao FOV e, em seguida, migre com indicações visuais para versões maiores.</span><span class="sxs-lookup"><span data-stu-id="157fa-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="157fa-351">Use os diretores espaciais de áudio e atenção para ajudar o usuário a encontrar conteúdo fora do FOV.</span><span class="sxs-lookup"><span data-stu-id="157fa-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="157fa-352">Tanto quanto possível, evite hologramas que recortem verticalmente o FOV.</span><span class="sxs-lookup"><span data-stu-id="157fa-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="157fa-353">Forneça ao usuário diretrizes no aplicativo para melhor localização de exibição.</span><span class="sxs-lookup"><span data-stu-id="157fa-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-354">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-355">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-355">Documentation</span></span>

* [<span data-ttu-id="157fa-356">Quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="157fa-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="157fa-357">Estudo de caso, interface do usuário do HoloStudio e aprendizado de design de interação</span><span class="sxs-lookup"><span data-stu-id="157fa-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="157fa-358">Escala de objetos e ambientes</span><span class="sxs-lookup"><span data-stu-id="157fa-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="157fa-359">Cursores, indicações visuais</span><span class="sxs-lookup"><span data-stu-id="157fa-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="157fa-360">Referências externas</span><span class="sxs-lookup"><span data-stu-id="157fa-360">External references</span></span>

* [<span data-ttu-id="157fa-361">Muito ado sobre o FOV</span><span class="sxs-lookup"><span data-stu-id="157fa-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="157fa-362">O conteúdo reage à posição do usuário</span><span class="sxs-lookup"><span data-stu-id="157fa-362">Content reacts to user position</span></span>

<span data-ttu-id="157fa-363">Os hologramas devem reagir à posição do usuário praticamente da mesma maneira que os objetos "reais".</span><span class="sxs-lookup"><span data-stu-id="157fa-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="157fa-364">Uma consideração de design notável são os elementos da interface do usuário que não podem, necessariamente, supor que a posição dos usuários seja imóvel e se adapte ao movimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="157fa-365">A criação de um aplicativo que se adapta corretamente à posição do usuário criará uma experiência mais verossímeis e facilitará o uso.</span><span class="sxs-lookup"><span data-stu-id="157fa-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-366">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-366">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-368"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-369">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-369">✔️</span></span></td>
        <td><span data-ttu-id="157fa-370">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-370">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-371">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="157fa-372">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-372">Best</span></span> </td><td> <span data-ttu-id="157fa-373">O conteúdo e a interface do usuário se adaptam às posições dos usuários, permitindo que o usuário interaja naturalmente com o conteúdo dentro do escopo do movimento de usuário esperado.</span><span class="sxs-lookup"><span data-stu-id="157fa-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="157fa-374">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-374">Meets</span></span> </td><td> <span data-ttu-id="157fa-375">A IU se adapta à posição do usuário, mas pode impedir a exibição do conteúdo da chave que exige que o usuário ajuste sua posição.</span><span class="sxs-lookup"><span data-stu-id="157fa-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="157fa-376">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="157fa-377">Os elementos da interface do usuário são perdidos ou bloqueados durante a movimentação, fazendo com que o usuário volte de volta para (ou localize) controles.</span><span class="sxs-lookup"><span data-stu-id="157fa-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="157fa-378">Os elementos da interface do usuário limitam a exibição do conteúdo primário.</span><span class="sxs-lookup"><span data-stu-id="157fa-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="157fa-379">O movimento da interface do usuário não é otimizado para exibir a distância e a dinâmica particularmente com elementos de interface do usuário com <a href="billboarding-and-tag-along.md">marcas</a> .</span><span class="sxs-lookup"><span data-stu-id="157fa-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="157fa-380">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-380">How to measure</span></span>

* <span data-ttu-id="157fa-381">Todas as medidas devem ser feitas dentro de um escopo razoável do cenário.</span><span class="sxs-lookup"><span data-stu-id="157fa-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="157fa-382">Embora a movimentação do usuário varie, não tente enganar o aplicativo com movimento extremo do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="157fa-383">Para elementos de interface do usuário, os controles relevantes devem estar disponíveis independentemente do movimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="157fa-384">Por exemplo, se o usuário estiver exibindo e percorrendo um mapa 3D com zoom, o controle de zoom deverá estar prontamente disponível para o usuário, independentemente do local.</span><span class="sxs-lookup"><span data-stu-id="157fa-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-385">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-385">Recommendations</span></span>

* <span data-ttu-id="157fa-386">O usuário é a câmera e controla o movimento.</span><span class="sxs-lookup"><span data-stu-id="157fa-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="157fa-387">Deixe-os na unidade.</span><span class="sxs-lookup"><span data-stu-id="157fa-387">Let them drive.</span></span>
* <span data-ttu-id="157fa-388">Considere a mensagem para os sistemas de texto e de menu que, de outra forma, seriam bloqueados no mundo, se um usuário fosse se movimentando.</span><span class="sxs-lookup"><span data-stu-id="157fa-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="157fa-389">Use uma marca para o conteúdo que precisa seguir o usuário enquanto ainda permite que o usuário veja o que está na frente deles.</span><span class="sxs-lookup"><span data-stu-id="157fa-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-390">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-391">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-391">Documentation</span></span>

* [<span data-ttu-id="157fa-392">Design de interação</span><span class="sxs-lookup"><span data-stu-id="157fa-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="157fa-393">Cor, luz e material</span><span class="sxs-lookup"><span data-stu-id="157fa-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="157fa-394">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="157fa-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="157fa-395">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="157fa-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="157fa-396">Locomotion de automovimento e usuário</span><span class="sxs-lookup"><span data-stu-id="157fa-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="157fa-397">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="157fa-397">Tools and tutorials</span></span>

* [<span data-ttu-id="157fa-398">Entrada MR 210: olhar</span><span class="sxs-lookup"><span data-stu-id="157fa-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="157fa-399">Clareza da interação de entrada</span><span class="sxs-lookup"><span data-stu-id="157fa-399">Input interaction clarity</span></span>

<span data-ttu-id="157fa-400">A clareza da interação de entrada é essencial para a usabilidade de um aplicativo e inclui consistência de entrada, capacidade de detecção, descoberta de métodos de interação.</span><span class="sxs-lookup"><span data-stu-id="157fa-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="157fa-401">O usuário deve ser capaz de usar interações comuns em toda a plataforma sem reaprender.</span><span class="sxs-lookup"><span data-stu-id="157fa-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="157fa-402">Se o aplicativo tiver uma entrada personalizada, ele deverá ser claramente comunicado e demonstrado.</span><span class="sxs-lookup"><span data-stu-id="157fa-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-403">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-403">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-405"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-406">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-406">✔️</span></span></td>
        <td><span data-ttu-id="157fa-407">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-407">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-408">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-408">Quality criteria</span></span>

|  <span data-ttu-id="157fa-409">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-409">Best</span></span>  |  <span data-ttu-id="157fa-410">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-410">Meets</span></span> |  <span data-ttu-id="157fa-411">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-412">Os métodos de interação de entrada são consistentes com as [diretrizes](interaction-fundamentals.md)do Windows Mixed Reality fornecidas.</span><span class="sxs-lookup"><span data-stu-id="157fa-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="157fa-413">Qualquer entrada personalizada não deve ser redundante com entrada padrão (em vez disso, usar a interação padrão) e deve ser claramente comunicada e demonstrada para o usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="157fa-414">Semelhante à melhor, mas as entradas personalizadas são redundantes com métodos de entrada padrão.</span><span class="sxs-lookup"><span data-stu-id="157fa-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="157fa-415">O usuário ainda pode alcançar a meta e o progresso por meio da experiência do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="157fa-416">É difícil entender o método de entrada ou o mapeamento de botão.</span><span class="sxs-lookup"><span data-stu-id="157fa-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="157fa-417">A entrada é bastante personalizada, não dá suporte à entrada padrão, não há instruções ou provavelmente causar problemas de fadiga e conforto.</span><span class="sxs-lookup"><span data-stu-id="157fa-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="157fa-418">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-418">How to measure</span></span>

* <span data-ttu-id="157fa-419">O aplicativo usa [métodos de entrada padrão](interaction-fundamentals.md) consistentes.</span><span class="sxs-lookup"><span data-stu-id="157fa-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="157fa-420">Se o aplicativo tiver uma entrada personalizada, ele será claramente comunicado por meio de:</span><span class="sxs-lookup"><span data-stu-id="157fa-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="157fa-421">Experiência de primeira execução</span><span class="sxs-lookup"><span data-stu-id="157fa-421">First-run experience</span></span>
* <span data-ttu-id="157fa-422">Telas introdutórias</span><span class="sxs-lookup"><span data-stu-id="157fa-422">Introductory screens</span></span>
* <span data-ttu-id="157fa-423">Dicas de ferramenta</span><span class="sxs-lookup"><span data-stu-id="157fa-423">Tooltips</span></span>
* <span data-ttu-id="157fa-424">Mão-executiva</span><span class="sxs-lookup"><span data-stu-id="157fa-424">Hand coach</span></span>
* <span data-ttu-id="157fa-425">Seção de ajuda</span><span class="sxs-lookup"><span data-stu-id="157fa-425">Help section</span></span>
* <span data-ttu-id="157fa-426">Voz sobre</span><span class="sxs-lookup"><span data-stu-id="157fa-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-427">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-427">Recommendations</span></span>

* <span data-ttu-id="157fa-428">Use métodos de entrada padrão sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="157fa-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="157fa-429">Forneça demonstrações, tutoriais e dicas de ferramenta para métodos de entrada não padrão.</span><span class="sxs-lookup"><span data-stu-id="157fa-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="157fa-430">Use um modelo de interação consistente em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-431">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-432">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-432">Documentation</span></span>

* [<span data-ttu-id="157fa-433">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="157fa-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="157fa-434">Objetos que interagem</span><span class="sxs-lookup"><span data-stu-id="157fa-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="157fa-435">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="157fa-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="157fa-436">Cursores</span><span class="sxs-lookup"><span data-stu-id="157fa-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="157fa-437">Conforto e olhar</span><span class="sxs-lookup"><span data-stu-id="157fa-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="157fa-438">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="157fa-438">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="157fa-439">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="157fa-439">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="157fa-440">Guia de portabilidade de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-440">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="157fa-441">Entrada do teclado no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-441">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="157fa-442">Foco no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-442">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="157fa-443">Gestos e controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-443">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="157fa-444">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-444">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="157fa-445">Teclado, mouse e entrada do controlador no DirectX</span><span class="sxs-lookup"><span data-stu-id="157fa-445">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="157fa-446">Olhar fixo com cabeça e olhos no DirectX</span><span class="sxs-lookup"><span data-stu-id="157fa-446">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="157fa-447">Controladores de mãos e emovimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="157fa-447">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="157fa-448">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="157fa-448">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="157fa-449">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="157fa-449">Tools and tutorials</span></span>

* [<span data-ttu-id="157fa-450">Estudo de caso: a busca de mais computação pessoal</span><span class="sxs-lookup"><span data-stu-id="157fa-450">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="157fa-451">Estudo de conversão: aprendizado de HoloStudio de interface do usuário e interação do projeto</span><span class="sxs-lookup"><span data-stu-id="157fa-451">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="157fa-452">Aplicativo de exemplo: tabela periódica dos elementos</span><span class="sxs-lookup"><span data-stu-id="157fa-452">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="157fa-453">Aplicativo de exemplo: módulo lunar</span><span class="sxs-lookup"><span data-stu-id="157fa-453">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="157fa-454">Entrada MR 210: olhar</span><span class="sxs-lookup"><span data-stu-id="157fa-454">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="157fa-455">Entrada MR 211: gestos</span><span class="sxs-lookup"><span data-stu-id="157fa-455">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="157fa-456">Entrada MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="157fa-456">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="157fa-457">Objetos que interagem</span><span class="sxs-lookup"><span data-stu-id="157fa-457">Interactable objects</span></span>

<span data-ttu-id="157fa-458">Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D.</span><span class="sxs-lookup"><span data-stu-id="157fa-458">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="157fa-459">No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração.</span><span class="sxs-lookup"><span data-stu-id="157fa-459">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="157fa-460">Qualquer coisa pode ser um objeto que possa ser interagindo que dispara um evento.</span><span class="sxs-lookup"><span data-stu-id="157fa-460">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="157fa-461">Um objeto de interação pode ser representado como qualquer coisa de uma xícara de café na mesa até um balão flutuante no ar.</span><span class="sxs-lookup"><span data-stu-id="157fa-461">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="157fa-462">Independentemente do formulário, os objetos interajantes devem ser claramente reconhecidos pelo usuário por meio de indicações visuais e de áudio.</span><span class="sxs-lookup"><span data-stu-id="157fa-462">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-463">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-463">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-465"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-466">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-466">✔️</span></span></td>
        <td><span data-ttu-id="157fa-467">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-467">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-468">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-468">Quality criteria</span></span>

|  <span data-ttu-id="157fa-469">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-469">Best</span></span>  |  <span data-ttu-id="157fa-470">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-470">Meets</span></span> |  <span data-ttu-id="157fa-471">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-471">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-472">Independentemente do formulário, os objetos que podem interagir são reconhecidos por meio de indicações visuais e de áudio em três Estados: ocioso, direcionado e selecionado.</span><span class="sxs-lookup"><span data-stu-id="157fa-472">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="157fa-473">"Vê-lo, digamos que" é claro e consistentemente usado em toda a experiência.</span><span class="sxs-lookup"><span data-stu-id="157fa-473">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="157fa-474">Os objetos são dimensionados e distribuídos para permitir o direcionamento livre de erros.</span><span class="sxs-lookup"><span data-stu-id="157fa-474">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="157fa-475">O usuário pode reconhecer o objeto como interagindo por meio de áudio ou comentários visuais e pode direcionar e ativar o objeto.</span><span class="sxs-lookup"><span data-stu-id="157fa-475">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="157fa-476">Não devido a indicações visuais ou de áudio, o usuário não consegue reconhecer um objeto que pode ser interagindo.</span><span class="sxs-lookup"><span data-stu-id="157fa-476">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="157fa-477">As interações são propensas a erros devido à escala ou à distância do objeto entre objetos.</span><span class="sxs-lookup"><span data-stu-id="157fa-477">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="157fa-478">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-478">How to measure</span></span>

* <span data-ttu-id="157fa-479">Os objetos que podem interagir são reconhecíveis como ' interagindo '; incluindo botões, menus e conteúdo específico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-479">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="157fa-480">Como regra prática, deve haver um Visual e uma indicação de áudio ao direcionar objetos que podem interagir.</span><span class="sxs-lookup"><span data-stu-id="157fa-480">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-481">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-481">Recommendations</span></span>

* <span data-ttu-id="157fa-482">Use comentários visuais e de áudio para interações.</span><span class="sxs-lookup"><span data-stu-id="157fa-482">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="157fa-483">Os comentários visuais devem ser diferenciados para cada Estado de entrada (ocioso, direcionado, selecionado)</span><span class="sxs-lookup"><span data-stu-id="157fa-483">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="157fa-484">Os objetos que podem ser interagindo devem ser dimensionados e colocados para direcionamento de erro livre.</span><span class="sxs-lookup"><span data-stu-id="157fa-484">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="157fa-485">Objetos de interação agrupada (como uma barra de menus ou lista) devem ter o espaçamento adequado para o direcionamento.</span><span class="sxs-lookup"><span data-stu-id="157fa-485">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="157fa-486">Os botões e menus que dão suporte ao comando de voz devem fornecer rótulos de texto para a palavra-chave Command ("vê-lo, digamos")</span><span class="sxs-lookup"><span data-stu-id="157fa-486">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-487">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-487">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-488">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-488">Documentation</span></span>

* [<span data-ttu-id="157fa-489">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="157fa-489">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="157fa-490">Texto no Unity</span><span class="sxs-lookup"><span data-stu-id="157fa-490">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="157fa-491">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="157fa-491">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="157fa-492">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="157fa-492">Voice input</span></span>](voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="157fa-493">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="157fa-493">Tools and tutorials</span></span>

* [<span data-ttu-id="157fa-494">Kit de ferramentas de realidade misturada-UX</span><span class="sxs-lookup"><span data-stu-id="157fa-494">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="157fa-495">Verificação de sala</span><span class="sxs-lookup"><span data-stu-id="157fa-495">Room scanning</span></span>

<span data-ttu-id="157fa-496">Os aplicativos que exigem dados de mapeamento espacial dependem do dispositivo para coletar automaticamente esses dados ao longo do tempo e entre as sessões, à medida que o usuário explora seu ambiente com o dispositivo ativo.</span><span class="sxs-lookup"><span data-stu-id="157fa-496">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="157fa-497">A integridade e a qualidade desses dados dependem de vários fatores, incluindo a quantidade de explorações que o usuário fez, quanto tempo passou desde a exploração e se os objetos como mobília e portas foram movidos desde que o dispositivo examinou a área.</span><span class="sxs-lookup"><span data-stu-id="157fa-497">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="157fa-498">Muitos aplicativos analisarão os dados de mapeamento espacial no início da experiência para avaliar se o usuário deve executar etapas adicionais para melhorar a integridade e a qualidade do mapa espacial.</span><span class="sxs-lookup"><span data-stu-id="157fa-498">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="157fa-499">Se o usuário for solicitado a verificar o ambiente, as diretrizes claras devem ser fornecidas durante a experiência de verificação.</span><span class="sxs-lookup"><span data-stu-id="157fa-499">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-500">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-500">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-502"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-503">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-503">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-504">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-504">Quality criteria</span></span>

|  <span data-ttu-id="157fa-505">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-505">Best</span></span>  |  <span data-ttu-id="157fa-506">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-506">Meets</span></span> |  <span data-ttu-id="157fa-507">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-507">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-508">A visualização da malha espacial informa aos usuários que a verificação está em andamento.</span><span class="sxs-lookup"><span data-stu-id="157fa-508">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="157fa-509">O usuário sabe claramente o que fazer e quando a verificação é iniciada e interrompida.</span><span class="sxs-lookup"><span data-stu-id="157fa-509">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="157fa-510">A visualização da malha espacial é fornecida, mas o usuário pode não saber claramente o que fazer e nenhuma informação de progresso é fornecida.</span><span class="sxs-lookup"><span data-stu-id="157fa-510">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="157fa-511">Nenhuma visualização da malha.</span><span class="sxs-lookup"><span data-stu-id="157fa-511">No visualization of mesh.</span></span> <span data-ttu-id="157fa-512">Nenhuma informação de orientação fornecida ao usuário sobre onde procurar ou quando a verificação é iniciada/interrompida.</span><span class="sxs-lookup"><span data-stu-id="157fa-512">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="157fa-513">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-513">How to measure</span></span>

* <span data-ttu-id="157fa-514">Durante uma verificação de sala necessária, as diretrizes de áudio e visuais são fornecidas, indicando onde procurar e quando iniciar e parar a verificação.</span><span class="sxs-lookup"><span data-stu-id="157fa-514">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-515">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-515">Recommendations</span></span>

* <span data-ttu-id="157fa-516">Indique quanto do volume total nos arredores dos usuários precisa fazer parte da experiência.</span><span class="sxs-lookup"><span data-stu-id="157fa-516">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="157fa-517">Comunique-se quando a verificação for iniciada e parada como um indicador de progresso.</span><span class="sxs-lookup"><span data-stu-id="157fa-517">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="157fa-518">Use uma visualização da malha durante a verificação.</span><span class="sxs-lookup"><span data-stu-id="157fa-518">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="157fa-519">Forneça visuais e indicações de áudio para incentivar o usuário a procurar e se movimentar pela sala.</span><span class="sxs-lookup"><span data-stu-id="157fa-519">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="157fa-520">Informe ao usuário onde ir para melhorar os dados.</span><span class="sxs-lookup"><span data-stu-id="157fa-520">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="157fa-521">Em muitos casos, pode ser melhor informar ao usuário o que eles precisam fazer (por exemplo, examinar o teto, examinar os móveis) para obter a qualidade de digitalização necessária.</span><span class="sxs-lookup"><span data-stu-id="157fa-521">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-522">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-522">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="157fa-523">Documentação</span><span class="sxs-lookup"><span data-stu-id="157fa-523">Documentation</span></span>

* [<span data-ttu-id="157fa-524">Visualização de varredura do ambiente</span><span class="sxs-lookup"><span data-stu-id="157fa-524">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="157fa-525">Estudo de caso: expandindo os recursos de mapeamento espacial do HoloLens</span><span class="sxs-lookup"><span data-stu-id="157fa-525">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="157fa-526">Estudo de caso: design de som espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="157fa-526">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="157fa-527">Estudo de caso: criando uma experiência de imersão em fragmentos</span><span class="sxs-lookup"><span data-stu-id="157fa-527">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="157fa-528">Ferramentas e tutoriais</span><span class="sxs-lookup"><span data-stu-id="157fa-528">Tools and tutorials</span></span>

* [<span data-ttu-id="157fa-529">Kit de ferramentas de realidade misturada-UX</span><span class="sxs-lookup"><span data-stu-id="157fa-529">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="157fa-530">Indicadores direcionais</span><span class="sxs-lookup"><span data-stu-id="157fa-530">Directional indicators</span></span>

<span data-ttu-id="157fa-531">Em um aplicativo de realidade misturada, o conteúdo pode estar fora do campo de exibição ou obstruído por objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="157fa-531">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="157fa-532">Um aplicativo bem projetado tornará mais fácil para o usuário encontrar conteúdo não visível.</span><span class="sxs-lookup"><span data-stu-id="157fa-532">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="157fa-533">Indicadores direcionais alertam um usuário sobre o conteúdo importante e fornecem orientação para o conteúdo relativo à posição do usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-533">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="157fa-534">As diretrizes para conteúdo não visível podem assumir a forma de emissores de som, setas direcionais ou indicações visuais diretas.</span><span class="sxs-lookup"><span data-stu-id="157fa-534">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-535">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-535">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-537"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-538">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-538">✔️</span></span></td>
        <td><span data-ttu-id="157fa-539">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-539">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-540">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-540">Quality criteria</span></span>

|  <span data-ttu-id="157fa-541">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-541">Best</span></span>  |  <span data-ttu-id="157fa-542">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-542">Meets</span></span> |  <span data-ttu-id="157fa-543">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-543">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-544">As indicações visuais e de áudio orientam diretamente o usuário ao conteúdo relevante fora do campo de exibição.</span><span class="sxs-lookup"><span data-stu-id="157fa-544">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="157fa-545">Uma seta ou algum indicador que aponta o usuário na direção geral do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="157fa-545">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="157fa-546">O conteúdo relevante está fora do campo de exibição e uma orientação de localização ruim ou nenhuma é fornecida ao usuário.</span><span class="sxs-lookup"><span data-stu-id="157fa-546">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="157fa-547">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-547">How to measure</span></span>

* <span data-ttu-id="157fa-548">O conteúdo relevante fora do campo de exibição do usuário é detectável por meio de indicações visuais e/ou de áudio.</span><span class="sxs-lookup"><span data-stu-id="157fa-548">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-549">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-549">Recommendations</span></span>

* <span data-ttu-id="157fa-550">Quando o conteúdo relevante está fora do campo de exibição do usuário, use indicadores direcionais e indicações de áudio para orientar o usuário no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="157fa-550">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="157fa-551">Em muitos casos, um guia visual direto é preferencial sobre setas direcionais.</span><span class="sxs-lookup"><span data-stu-id="157fa-551">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="157fa-552">Indicadores direcionais não devem ser incorporados ao cursor.</span><span class="sxs-lookup"><span data-stu-id="157fa-552">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-553">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-553">Resources</span></span>

* [<span data-ttu-id="157fa-554">Quadro holográfico</span><span class="sxs-lookup"><span data-stu-id="157fa-554">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="157fa-555">Carregamento de dados</span><span class="sxs-lookup"><span data-stu-id="157fa-555">Data loading</span></span>

<span data-ttu-id="157fa-556">Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.</span><span class="sxs-lookup"><span data-stu-id="157fa-556">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="157fa-557">Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar quanto tempo de espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="157fa-557">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="157fa-558">Impacto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="157fa-558">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="157fa-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="157fa-560"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="157fa-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="157fa-561">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-561">✔️</span></span></td>
        <td><span data-ttu-id="157fa-562">✔️</span><span class="sxs-lookup"><span data-stu-id="157fa-562">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="157fa-563">Critérios de qualidade</span><span class="sxs-lookup"><span data-stu-id="157fa-563">Quality criteria</span></span>

|  <span data-ttu-id="157fa-564">Recomendá</span><span class="sxs-lookup"><span data-stu-id="157fa-564">Best</span></span>  |  <span data-ttu-id="157fa-565">Corresponde</span><span class="sxs-lookup"><span data-stu-id="157fa-565">Meets</span></span> |  <span data-ttu-id="157fa-566">Recuperação</span><span class="sxs-lookup"><span data-stu-id="157fa-566">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="157fa-567">Indicador visual animado, na forma de uma barra de progresso ou anel, mostrando o progresso durante qualquer carregamento ou processamento de dados.</span><span class="sxs-lookup"><span data-stu-id="157fa-567">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="157fa-568">O indicador visual fornece orientação sobre quanto tempo a espera pode ser.</span><span class="sxs-lookup"><span data-stu-id="157fa-568">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="157fa-569">O usuário é informado de que o carregamento de dados está em andamento, mas não há nenhuma indicação de quanto tempo a espera poderia ser.</span><span class="sxs-lookup"><span data-stu-id="157fa-569">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="157fa-570">Nenhum indicador de carregamento ou processo de dados para a tarefa demorando mais do que 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="157fa-570">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="157fa-571">Como medir</span><span class="sxs-lookup"><span data-stu-id="157fa-571">How to measure</span></span>

* <span data-ttu-id="157fa-572">Durante o carregamento de dados, verifique se não há nenhum estado em branco por mais de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="157fa-572">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="157fa-573">Recomendações</span><span class="sxs-lookup"><span data-stu-id="157fa-573">Recommendations</span></span>

* <span data-ttu-id="157fa-574">Forneça um Animator de carregamento de dados mostrando o progresso em qualquer situação em que o usuário possa perceber que esse aplicativo está parado ou falhou.</span><span class="sxs-lookup"><span data-stu-id="157fa-574">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="157fa-575">Uma regra prática razoável é qualquer atividade de ' carregamento ' que pode levar mais de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="157fa-575">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="157fa-576">Recursos</span><span class="sxs-lookup"><span data-stu-id="157fa-576">Resources</span></span>

* [<span data-ttu-id="157fa-577">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="157fa-577">Displaying progress</span></span>](progress.md)

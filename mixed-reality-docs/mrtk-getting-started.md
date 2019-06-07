---
title: Introdução ao MRTK versão 2
description: Para novos desenvolvedores que estejam interessados em aproveitando MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, testar, Kit de ferramentas de realidade misturada, MRTK versão 2, MRTK, ferramentas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750386"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="0038d-104">Introdução ao MRTK v2</span><span class="sxs-lookup"><span data-stu-id="0038d-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="0038d-105">MRTK guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="0038d-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="0038d-106">Consulte a [MRTK guia de Introdução](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obter informações sobre como começar com MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="0038d-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="0038d-107">O que é o Kit de ferramentas de realidade misturada (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="0038d-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="0038d-108">O MRTK é um kit de ferramentas incríveis do código-fonte aberto que já existe, pois o HoloLens foi lançado pela primeira vez e não seria onde está sem o trabalho pesado de nossa comunidade de desenvolvedores que contribuíram para ele.</span><span class="sxs-lookup"><span data-stu-id="0038d-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="0038d-109">Nos últimos 3 anos, temos ouviu os comentários de nossa comunidade de desenvolvedores e criados MRTK v2 para levar as maiores preocupações em conta.</span><span class="sxs-lookup"><span data-stu-id="0038d-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="0038d-110">O v2 MRTK com o Unity é um kit de desenvolvimento de plataforma cruzada do código-fonte aberto para aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="0038d-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="0038d-111">MRTK versão 2 destina-se a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens, headsets do Windows Mixed Reality imersivos (VR) e plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="0038d-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="0038d-112">O projeto é voltado para reduzir as barreiras à entrada para criar aplicativos de realidade mista e contribuem na comunidade, como todos nós crescer.</span><span class="sxs-lookup"><span data-stu-id="0038d-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="0038d-113">Consulte a [portal de documentação MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="0038d-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="0038d-114">Áreas de recurso</span><span class="sxs-lookup"><span data-stu-id="0038d-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema de entrada" width="105"> <span data-ttu-id="0038d-116">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="0038d-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Mão de acompanhamento (HoloLens 2)" width="105"> <span data-ttu-id="0038d-118">Mão de acompanhamento (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="0038d-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="(HoloLens 2) de acompanhamento a olho nu" width="105">
    <span data-ttu-id="0038d-120">(HoloLens 2) de acompanhamento a olho nu</span><span class="sxs-lookup"><span data-stu-id="0038d-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comandos de voz" width="105"> <span data-ttu-id="0038d-122">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="0038d-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Mantenha o foco + selecionar (HoloLens (1º gen))" width="105">
    <span data-ttu-id="0038d-124">Mantenha o foco + selecionar (HoloLens (1º gen))</span><span class="sxs-lookup"><span data-stu-id="0038d-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> <span data-ttu-id="0038d-126">Teleportation</span><span class="sxs-lookup"><span data-stu-id="0038d-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controles de interface de usuário" width="105"> <span data-ttu-id="0038d-128">Controles de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="0038d-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Solver e interações" width="105"> <span data-ttu-id="0038d-130">Solver e interações</span><span class="sxs-lookup"><span data-stu-id="0038d-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualização do controlador" width="105"> <span data-ttu-id="0038d-132">Visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="0038d-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Noções básicas sobre espacial" width="105"> <span data-ttu-id="0038d-134">Noções básicas sobre espacial</span><span class="sxs-lookup"><span data-stu-id="0038d-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Ferramenta de diagnóstico" width="105"> <span data-ttu-id="0038d-136">Ferramenta de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="0038d-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Sombreador MRTK padrão" width="105"> <span data-ttu-id="0038d-138">Sombreador MRTK padrão</span><span class="sxs-lookup"><span data-stu-id="0038d-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="0038d-139">Blocos da interface do usuário e a criação de interação</span><span class="sxs-lookup"><span data-stu-id="0038d-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Botão" width="250"><br>
    <span data-ttu-id="0038d-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="0038d-141">**Button**</span></span><br>
    <span data-ttu-id="0038d-142">Um controle de botão que dá suporte a vários métodos de entrada, incluindo a mão de articuladas do HoloLens 2 <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Caixa delimitadora" width="250"><br>
    <span data-ttu-id="0038d-144">**Caixa delimitadora**</span><span class="sxs-lookup"><span data-stu-id="0038d-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="0038d-145">Interface do usuário padrão para manipular objetos no espaço 3D <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Manipulador de manipulação" width="250"><br>
    <span data-ttu-id="0038d-147">**Manipulador de manipulação**</span><span class="sxs-lookup"><span data-stu-id="0038d-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="0038d-148">Script para manipular objetos com uma ou duas mãos <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Tablet" width="250"><br>
    <span data-ttu-id="0038d-150">**Tablet**</span><span class="sxs-lookup"><span data-stu-id="0038d-150">**Slate**</span></span> <br>
    <span data-ttu-id="0038d-151">Plano de estilo 2D que oferece suporte à rolagem com uma entrada articuladas mão <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Teclado do sistema" width="250"><br>
    <span data-ttu-id="0038d-153">**Teclado do sistema**</span><span class="sxs-lookup"><span data-stu-id="0038d-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="0038d-154">Script de exemplo de como usar o teclado de sistema no Unity <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interagível" width="250"><br>
     <span data-ttu-id="0038d-156">**Interagível**</span><span class="sxs-lookup"><span data-stu-id="0038d-156">**Interactable**</span></span> <br>
     <span data-ttu-id="0038d-157">Um script para fazer objetos interagível com estados visuais e suporte de tema <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    <span data-ttu-id="0038d-159">**Solver**</span><span class="sxs-lookup"><span data-stu-id="0038d-159">**Solver**</span></span> <br>
    <span data-ttu-id="0038d-160">Vários comportamentos de posicionamento como tag-along, o bloqueio de corpo, tamanho de modo constante e magnetismo superfície do objeto <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Coleção de objetos" width="250"><br>
    <span data-ttu-id="0038d-162">**Coleção de objetos**</span><span class="sxs-lookup"><span data-stu-id="0038d-162">**Object Collection**</span></span><br>
    <span data-ttu-id="0038d-163">Script para dispor de uma matriz de objetos em uma forma tridimensional <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Dica de ferramenta" width="250">  <br>
    <span data-ttu-id="0038d-165">**Dica de ferramenta**</span><span class="sxs-lookup"><span data-stu-id="0038d-165">**Tooltip**</span></span><br>
    <span data-ttu-id="0038d-166">Anotação da interface do usuário com o sistema de âncora/dinâmico flexível que pode ser usado para rotular o objeto e controladores de movimento <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra de aplicativo" width="250"><br>
    <span data-ttu-id="0038d-168">**Barra de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="0038d-168">**App Bar**</span></span><br>
    <span data-ttu-id="0038d-169">Interface do usuário para a ativação manual da caixa delimitadora <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Ponteiros" width="250"><br>
    <span data-ttu-id="0038d-171">**Ponteiros**</span><span class="sxs-lookup"><span data-stu-id="0038d-171">**Pointers**</span></span><br>
    <span data-ttu-id="0038d-172">Saiba mais sobre os vários tipos de ponteiros <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualização de ponta do dedo" width="250"><br>
     <span data-ttu-id="0038d-174">**Visualização de ponta do dedo**</span><span class="sxs-lookup"><span data-stu-id="0038d-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="0038d-175">Funcionalidade Visual na ponta do dedo que melhora a confiança para a interação direta <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Controle deslizante" width="250"><br>
    <span data-ttu-id="0038d-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="0038d-177">**Slider**</span></span><br>
    <span data-ttu-id="0038d-178">Controle deslizante de interface do usuário para ajustar valores suporte mão direto de interação de controle <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Sombreador MRTK padrão" width="250"><br>
    <span data-ttu-id="0038d-180">**Sombreador MRTK padrão**</span><span class="sxs-lookup"><span data-stu-id="0038d-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="0038d-181">Sombreador de padrão do MRTK dá suporte a vários elementos de design Fluent com desempenho <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Chaser conjunta de mão" width="250"><br>
     <span data-ttu-id="0038d-183">**Chaser conjunta de mão**</span><span class="sxs-lookup"><span data-stu-id="0038d-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="0038d-184">Demonstra como usar o Solver anexar objetos junções mão <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Acompanhamento a olho nu: Seleção de destino" width="250"><br>
    <span data-ttu-id="0038d-186">**Acompanhamento a olho nu: Seleção de destino**</span><span class="sxs-lookup"><span data-stu-id="0038d-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="0038d-187">Combinar os olhos, voz e mão rapidamente e facilmente selecionar hologramas entre sua cena de entrada <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Acompanhamento a olho nu: Navegação" width="250"><br>
    <span data-ttu-id="0038d-189">**Acompanhamento a olho nu: Navegação**</span><span class="sxs-lookup"><span data-stu-id="0038d-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="0038d-190">Saiba como auto texto de rolagem ou ampliar fluentemente focalizado conteúdo com base no qual você está examinando <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Acompanhamento a olho nu: Mapa de calor" width="250"><br>
    <span data-ttu-id="0038d-192">**Acompanhamento a olho nu: Mapa de calor**</span><span class="sxs-lookup"><span data-stu-id="0038d-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="0038d-193">Exemplos para registro em log, carregar e visualizar o que os usuários têm sido observando em seu aplicativo <a/></span><span class="sxs-lookup"><span data-stu-id="0038d-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="0038d-194">Requisito mínimo para MRTK v2</span><span class="sxs-lookup"><span data-stu-id="0038d-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="0038d-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="0038d-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="0038d-196">Microsoft Visual Studio 2017 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0038d-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="0038d-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="0038d-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="0038d-198">Windows 10 1803 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0038d-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="0038d-199">Novo com MRTK v2</span><span class="sxs-lookup"><span data-stu-id="0038d-199">New with MRTK v2</span></span>
<span data-ttu-id="0038d-200">Gostaríamos de enfatizar o nosso compromisso com essas ferramentas de plataforma.</span><span class="sxs-lookup"><span data-stu-id="0038d-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="0038d-201">Na verdade, aproveitamos MRTK versão 2 para desenvolver nossas experiências de caixa de entrada, como a experiência de instalação (OOBE) e o nosso aplicativo de aprendizado de realidade mista.</span><span class="sxs-lookup"><span data-stu-id="0038d-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="0038d-202">Você também pode esperar ver os novos recursos do HoloLens 2 expostos pela primeira vez por meio de MRTK porque acreditamos que é a melhor maneira de desenvolver em nossa plataforma.</span><span class="sxs-lookup"><span data-stu-id="0038d-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="0038d-203">Modular</span><span class="sxs-lookup"><span data-stu-id="0038d-203">Modular</span></span>
<span data-ttu-id="0038d-204">Criamos-lo de forma modular, para que você não precise levar cada bit do Kit de ferramentas em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="0038d-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="0038d-205">Há, na verdade, alguns benefícios para isso.</span><span class="sxs-lookup"><span data-stu-id="0038d-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="0038d-206">Ele mantém o tamanho do seu projeto menores, como também torna mais fácil de gerenciar.</span><span class="sxs-lookup"><span data-stu-id="0038d-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="0038d-207">Acima disso, porque ele foi criado com objetos passíveis de script e é controlado por interface, também é possível substituir os componentes que estão incluídos com seu próprio, para dar suporte a outros serviços, sistemas e plataformas.</span><span class="sxs-lookup"><span data-stu-id="0038d-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="0038d-208">Plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="0038d-208">Cross-platform</span></span>
<span data-ttu-id="0038d-209">Falando em outras plataformas, ele tem suporte de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="0038d-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="0038d-210">E, embora isso não significa que todas as plataformas única é suporte imediato, nós nos certificamos de que nenhum código Kit de ferramentas será interrompido quando você alternar o seu destino de compilação para outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="0038d-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="0038d-211">A robustez e a extensibilidade com o design modular define você em um caminho bom ser capaz de dar suporte a várias plataformas, como ARCore, ARKit e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="0038d-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="0038d-212">Alto desempenho</span><span class="sxs-lookup"><span data-stu-id="0038d-212">Performant</span></span>
<span data-ttu-id="0038d-213">Trabalhando com plataformas móveis, nós criamos-lo com o desempenho em mente.</span><span class="sxs-lookup"><span data-stu-id="0038d-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="0038d-214">Isso é muito importante, e queremos garantir que as ferramentas não vão funcionar contra você.</span><span class="sxs-lookup"><span data-stu-id="0038d-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="0038d-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0038d-215">See also</span></span>
* [<span data-ttu-id="0038d-216">MRTK guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="0038d-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="0038d-217">Página inicial da documentação MRTK</span><span class="sxs-lookup"><span data-stu-id="0038d-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="0038d-218">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="0038d-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="0038d-219">Portabilidade de HTK/MRTK para MRTK versão 2</span><span class="sxs-lookup"><span data-stu-id="0038d-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)

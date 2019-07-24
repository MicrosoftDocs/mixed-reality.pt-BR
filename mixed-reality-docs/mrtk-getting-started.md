---
title: Introdução ao MRTK versão 2
description: Para novos desenvolvedores interessados em aproveitar o MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, teste, kit de ferramentas de realidade mista, MRTK versão 2, MRTK, ferramentas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750386"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="a8029-104">Introdução ao MRTK v2</span><span class="sxs-lookup"><span data-stu-id="a8029-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="a8029-105">Guia de Introdução do MRTK</span><span class="sxs-lookup"><span data-stu-id="a8029-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="a8029-106">Consulte o [Guia de introdução do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obter informações sobre como começar a usar o MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="a8029-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="a8029-107">O que é o MRTK (Kit de ferramentas de realidade mista)?</span><span class="sxs-lookup"><span data-stu-id="a8029-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="a8029-108">O MRTK é um incrível kit de ferramentas de código-fonte aberto que já existe desde que o HoloLens foi lançado pela primeira vez e não seria onde ele está hoje sem o trabalho árduo de nossa comunidade de desenvolvedores que contribuiu para ele.</span><span class="sxs-lookup"><span data-stu-id="a8029-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="a8029-109">Nos últimos três anos, ouvimos os comentários da nossa comunidade de desenvolvedores e criamos o MRTK v2 para levar em conta as maiores preocupações.</span><span class="sxs-lookup"><span data-stu-id="a8029-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="a8029-110">O MRTK V2 com Unity é um kit de desenvolvimento de plataforma cruzada de software livre para aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a8029-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="a8029-111">A versão 2 do MRTK tem como objetivo acelerar o desenvolvimento de aplicativos destinados ao Microsoft HoloLens, fones de ouvido (VR) de realidade mista do Windows e plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="a8029-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="a8029-112">O projeto visa reduzir as barreiras de entrada para criar aplicativos de realidade misturada e contribuir com a comunidade à medida que todos nós crescemos.</span><span class="sxs-lookup"><span data-stu-id="a8029-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="a8029-113">Consulte o [portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="a8029-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="a8029-114">Áreas de recursos</span><span class="sxs-lookup"><span data-stu-id="a8029-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema de entrada" width="105"> <span data-ttu-id="a8029-116">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="a8029-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Acompanhamento à mão (HoloLens 2)" width="105"> <span data-ttu-id="a8029-118">Acompanhamento à mão (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="a8029-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Acompanhamento de olho (HoloLens 2)" width="105">
    <span data-ttu-id="a8029-120">Acompanhamento de olho (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="a8029-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comando de voz" width="105"> <span data-ttu-id="a8029-122">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="a8029-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Olhar + Select (HoloLens (1ª gen))" width="105">
    <span data-ttu-id="a8029-124">Olhar + Select (HoloLens (1ª gen))</span><span class="sxs-lookup"><span data-stu-id="a8029-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportação" width="105"> <span data-ttu-id="a8029-126">Teleportação</span><span class="sxs-lookup"><span data-stu-id="a8029-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controles de interface de usuário" width="105"> <span data-ttu-id="a8029-128">Controles de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="a8029-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Resolvedor e interações" width="105"> <span data-ttu-id="a8029-130">Resolvedor e interações</span><span class="sxs-lookup"><span data-stu-id="a8029-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualização do controlador" width="105"> <span data-ttu-id="a8029-132">Visualização do controlador</span><span class="sxs-lookup"><span data-stu-id="a8029-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Compreensão espacial" width="105"> <span data-ttu-id="a8029-134">Compreensão espacial</span><span class="sxs-lookup"><span data-stu-id="a8029-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Ferramenta de diagnóstico" width="105"> <span data-ttu-id="a8029-136">Ferramenta de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="a8029-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Sombreador padrão MRTK" width="105"> <span data-ttu-id="a8029-138">Sombreador padrão MRTK</span><span class="sxs-lookup"><span data-stu-id="a8029-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="a8029-139">Blocos de construção da interface do usuário e da interação</span><span class="sxs-lookup"><span data-stu-id="a8029-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Botão" width="250"><br>
    <span data-ttu-id="a8029-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="a8029-141">**Button**</span></span><br>
    <span data-ttu-id="a8029-142">Um controle de botão que dá suporte a vários métodos de entrada, incluindo a mão articulada do HoloLens 2<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Caixa delimitadora" width="250"><br>
    <span data-ttu-id="a8029-144">**Caixa delimitadora**</span><span class="sxs-lookup"><span data-stu-id="a8029-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="a8029-145">Interface do usuário padrão para manipular objetos no espaço 3D<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Manipulador de manipulação" width="250"><br>
    <span data-ttu-id="a8029-147">**Manipulador de manipulação**</span><span class="sxs-lookup"><span data-stu-id="a8029-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="a8029-148">Script para manipular objetos com uma ou duas mãos<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Slate" width="250"><br>
    <span data-ttu-id="a8029-150">**Slate**</span><span class="sxs-lookup"><span data-stu-id="a8029-150">**Slate**</span></span> <br>
    <span data-ttu-id="a8029-151">plano de estilo 2D que dá suporte à rolagem com entrada de mão articulada<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Teclado do sistema" width="250"><br>
    <span data-ttu-id="a8029-153">**Teclado do sistema**</span><span class="sxs-lookup"><span data-stu-id="a8029-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="a8029-154">Exemplo de script de uso do teclado do sistema no Unity<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interagir" width="250"><br>
     <span data-ttu-id="a8029-156">**Interagir**</span><span class="sxs-lookup"><span data-stu-id="a8029-156">**Interactable**</span></span> <br>
     <span data-ttu-id="a8029-157">Um script para tornar os objetos interagirem com os Estados visuais e o suporte a temas<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    <span data-ttu-id="a8029-159">**Solver**</span><span class="sxs-lookup"><span data-stu-id="a8029-159">**Solver**</span></span> <br>
    <span data-ttu-id="a8029-160">Vários comportamentos de posicionamento de objeto, como marca, bloqueio de corpo, tamanho de exibição constante e Magnetism de superfície<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Coleção de objetos" width="250"><br>
    <span data-ttu-id="a8029-162">**Coleção de objetos**</span><span class="sxs-lookup"><span data-stu-id="a8029-162">**Object Collection**</span></span><br>
    <span data-ttu-id="a8029-163">Script para dispor uma matriz de objetos em uma forma tridimensional<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Dica de ferramenta" width="250">  <br>
    <span data-ttu-id="a8029-165">**Dessa**</span><span class="sxs-lookup"><span data-stu-id="a8029-165">**Tooltip**</span></span><br>
    <span data-ttu-id="a8029-166">IU de anotações com sistema âncora/dinâmico flexível que pode ser usado para rotular os controladores de movimento e o objeto<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra de aplicativos" width="250"><br>
    <span data-ttu-id="a8029-168">**Barra de aplicativos**</span><span class="sxs-lookup"><span data-stu-id="a8029-168">**App Bar**</span></span><br>
    <span data-ttu-id="a8029-169">Interface do usuário para ativação manual da caixa delimitadora<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Ponteiros" width="250"><br>
    <span data-ttu-id="a8029-171">**Ponteiro**</span><span class="sxs-lookup"><span data-stu-id="a8029-171">**Pointers**</span></span><br>
    <span data-ttu-id="a8029-172">Saiba mais sobre os vários tipos de ponteiros<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualização de mãos" width="250"><br>
     <span data-ttu-id="a8029-174">**Visualização de mãos**</span><span class="sxs-lookup"><span data-stu-id="a8029-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="a8029-175">A condireção Visual está no alcance que melhora a confiança da interação direta<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Controle deslizante" width="250"><br>
    <span data-ttu-id="a8029-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="a8029-177">**Slider**</span></span><br>
    <span data-ttu-id="a8029-178">Interface do usuário do slider para ajustar valores que dão suporte à interação de rastreamento direto<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Sombreador padrão MRTK" width="250"><br>
    <span data-ttu-id="a8029-180">**Sombreador padrão MRTK**</span><span class="sxs-lookup"><span data-stu-id="a8029-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="a8029-181">O sombreador padrão de MRTK dá suporte a vários elementos de design fluentes com desempenho<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Conjunto de conjunção à mão" width="250"><br>
     <span data-ttu-id="a8029-183">**Conjunto de conjunção à mão**</span><span class="sxs-lookup"><span data-stu-id="a8029-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="a8029-184">Demonstra como usar o Solver para anexar objetos às junções de mão<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Acompanhamento de olho: Seleção de destino" width="250"><br>
    <span data-ttu-id="a8029-186">**Acompanhamento de olho: Seleção de destino**</span><span class="sxs-lookup"><span data-stu-id="a8029-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="a8029-187">Combine a entrada de olhos, voz e mão para selecionar com rapidez e facilidade os hologramas em sua cena<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Acompanhamento de olho: Navegação" width="250"><br>
    <span data-ttu-id="a8029-189">**Acompanhamento de olho: Navega**</span><span class="sxs-lookup"><span data-stu-id="a8029-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="a8029-190">Saiba como rolar automaticamente o texto ou ampliar de forma fluente o conteúdo focado com base no que você está vendo<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Acompanhamento de olho: Mapa de calor" width="250"><br>
    <span data-ttu-id="a8029-192">**Acompanhamento de olho: Mapa de calor**</span><span class="sxs-lookup"><span data-stu-id="a8029-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="a8029-193">Exemplos de registro em log, carregamento e visualização do que os usuários estão olhando em seu aplicativo<a/></span><span class="sxs-lookup"><span data-stu-id="a8029-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="a8029-194">Requisito mínimo para MRTK v2</span><span class="sxs-lookup"><span data-stu-id="a8029-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="a8029-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="a8029-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="a8029-196">Microsoft Visual Studio 2017 ou posterior</span><span class="sxs-lookup"><span data-stu-id="a8029-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="a8029-197">SDK do Windows 18362 +</span><span class="sxs-lookup"><span data-stu-id="a8029-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="a8029-198">Windows 10 1803 ou posterior</span><span class="sxs-lookup"><span data-stu-id="a8029-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="a8029-199">Novo com MRTK v2</span><span class="sxs-lookup"><span data-stu-id="a8029-199">New with MRTK v2</span></span>
<span data-ttu-id="a8029-200">Queremos enfatizar nosso compromisso com essas ferramentas de plataforma.</span><span class="sxs-lookup"><span data-stu-id="a8029-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="a8029-201">Na verdade, aproveitamos o MRTK versão 2 para desenvolver nossas experiências de caixa de entrada, como a OOBE (experiência de configuração) e nosso aplicativo de aprendizado de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="a8029-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="a8029-202">Você também pode esperar ver os novos recursos do HoloLens 2 apresentados pela primeira vez por meio de MRTK, pois acreditamos que é a melhor maneira de desenvolver em nossa plataforma.</span><span class="sxs-lookup"><span data-stu-id="a8029-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="a8029-203">Modula</span><span class="sxs-lookup"><span data-stu-id="a8029-203">Modular</span></span>
<span data-ttu-id="a8029-204">Nós o criamos de uma maneira modular, para que você não precise usar todos os trechos do kit de ferramentas em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a8029-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="a8029-205">Na verdade, há alguns benefícios para isso.</span><span class="sxs-lookup"><span data-stu-id="a8029-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="a8029-206">Ele mantém o tamanho do projeto menor, bem como torna mais fácil de gerenciar.</span><span class="sxs-lookup"><span data-stu-id="a8029-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="a8029-207">Além disso, como ele é criado com objetos programáveis e é orientado por interface, também é possível substituir os componentes que estão incluídos com os seus próprios, para dar suporte a outros serviços, sistemas e plataformas.</span><span class="sxs-lookup"><span data-stu-id="a8029-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="a8029-208">Plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="a8029-208">Cross-platform</span></span>
<span data-ttu-id="a8029-209">Falando em outras plataformas, ele tem suporte para várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="a8029-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="a8029-210">E, embora isso não signifique que todas as plataformas tenham suporte pronto para uso, garantimos que nenhum código do kit de ferramentas será interrompido quando você mudar seu destino de Build para outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="a8029-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="a8029-211">A robustez e a extensibilidade com o design modular definem um bom caminho para poder dar suporte a várias plataformas, como ARCore, ARKit e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="a8029-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="a8029-212">Alto desempenho</span><span class="sxs-lookup"><span data-stu-id="a8029-212">Performant</span></span>
<span data-ttu-id="a8029-213">Trabalhando com plataformas móveis, nós a construímos com o desempenho em mente.</span><span class="sxs-lookup"><span data-stu-id="a8029-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="a8029-214">Isso é extremamente importante, e queríamos garantir que as ferramentas não funcionarão em você.</span><span class="sxs-lookup"><span data-stu-id="a8029-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="a8029-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8029-215">See also</span></span>
* [<span data-ttu-id="a8029-216">Guia de introdução do MRTK</span><span class="sxs-lookup"><span data-stu-id="a8029-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="a8029-217">Página inicial da documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="a8029-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="a8029-218">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="a8029-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="a8029-219">Portando de HTK/MRTK para MRTK versão 2</span><span class="sxs-lookup"><span data-stu-id="a8029-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)

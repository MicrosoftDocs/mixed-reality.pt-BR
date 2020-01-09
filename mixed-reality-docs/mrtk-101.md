---
title: MRTK 101 – como usar a Unity do kit de ferramentas da realidade misturada para interações básicas (HoloLens 2, HoloLens, realidade do Windows Mixed, Open VR)
description: Como usar a Unity do kit de ferramentas da realidade misturada para interações básicas (HoloLens 2, HoloLens, realidade do Windows Mixed, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, kit de ferramentas de realidade misturada, realidade misturada do Windows, design, aplicativo de exemplo, controles
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623504"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="f8d2d-104">MRTK 101: como usar a Unity do kit de ferramentas da realidade misturada para interações básicas (HoloLens 2, HoloLens, realidade do Windows Mixed, Open VR)</span><span class="sxs-lookup"><span data-stu-id="f8d2d-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="f8d2d-106">Saiba mais sobre como usar o MRTK para obter alguns dos padrões comuns de interação mais amplamente usados na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="f8d2d-107">Como simular interações de entrada no editor do Unity?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="f8d2d-108">Como pegar e mover um objeto?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-108">How to grab and move an object?</span></span>
- <span data-ttu-id="f8d2d-109">Como redimensionar um objeto?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-109">How to resize an object?</span></span>
- <span data-ttu-id="f8d2d-110">Como mover ou girar um objeto com precisão?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="f8d2d-111">Como fazer um objeto responder a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="f8d2d-112">Como adicionar comentários visuais?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-112">How to add visual feedback?</span></span>
- <span data-ttu-id="f8d2d-113">Como adicionar comentários de áudio?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-113">How to add audio feedback?</span></span>
- <span data-ttu-id="f8d2d-114">Como usar o botão de estilo do HoloLens 2 pré-fabricados?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="f8d2d-115">Como fazer um objeto seguir você?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-115">How to make an object follow you?</span></span>
- <span data-ttu-id="f8d2d-116">Como fazer um objeto lhe encarar?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="f8d2d-117">Como simular interações de entrada no editor do Unity?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="f8d2d-118">O MRTK dá suporte à simulação de entrada no editor.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="f8d2d-119">Basta executar sua cena clicando no botão reproduzir do Unity.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="f8d2d-120">Use essas chaves para simular a entrada.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="f8d2d-121">Pressione W, A, S, as teclas D para mover a câmera.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="f8d2d-122">Mantenha o botão direito do mouse e mova o mouse para examinar.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="f8d2d-123">Para exibir as mãos simuladas, pressione a barra de espaço (à direita) ou a tecla SHIFT esquerda (à esquerda) para manter as mãos simuladas na exibição, pressione T ou a tecla Y para girar as mãos simuladas, pressione Q ou E (horizontal)/R ou F (vertical)</span><span class="sxs-lookup"><span data-stu-id="f8d2d-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="f8d2d-124">Saiba mais sobre a simulação de entrada na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="f8d2d-125">Como pegar e mover um objeto?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-125">How to grab and move an object?</span></span>
<span data-ttu-id="f8d2d-126">Para tornar um objeto que seja impossibilitado, atribua estes dois scripts: ManipulationHandler.cs e NearInteractionGrabbable. cs (para captura direta com entrada de acompanhamento à mão) ManipulationHandler dá suporte a interações tanto à direita quanto à extrema.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="f8d2d-127">Você pode pegar e mover um objeto com a entrada de controle de mão articulada do HoloLens 2 (próximo), Hand Ray (longe), feixe do controlador de movimento (muito), cursor olhar do HoloLens & Air-TAP (longe).</span><span class="sxs-lookup"><span data-stu-id="f8d2d-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="f8d2d-128">Como redimensionar um objeto?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-128">How to resize an object?</span></span>
<span data-ttu-id="f8d2d-129">O ManipulationHandler.cs dá suporte à escala/rotação de duas mãos.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="f8d2d-130">Isso funciona com vários tipos de entrada, como entrada de mão articulada do HoloLens 2, entrada do olhar + gesto do HoloLens 1 e entrada do controlador de movimento do headset de imersão do Windows Mixed realm.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="f8d2d-131">Saiba mais sobre o manipulador de manipulação na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="f8d2d-132">Como mover ou girar um objeto com precisão?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="f8d2d-133">Atribua BoundingBox.cs a um objeto para usar a caixa delimitadora, que é a interface para dimensionar e girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="f8d2d-134">Por padrão, ele mostra os cabos e identificadores azuis do estilo do HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="f8d2d-135">Para usar os identificadores animados com base em proximidades no estilo do HoloLens 2, você precisa atribuir pré-fabricados e materiais.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="f8d2d-136">Veja a [documentação da caixa delimitadora](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) e a cena BoundingBoxExamples. Unity para obter os detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="f8d2d-137">Saiba mais sobre a caixa delimitadora na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="f8d2d-138">Como fazer um objeto responder a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="f8d2d-139">Atribua PointerHandler.cs a um objeto.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="f8d2d-140">No Inspetor, você poderá usar os eventos OnPointerDown (), OnPointerUp (), OnPointerClicked (), OnPointerDragged () para usar esses eventos em um script, implementar IMixedRealityPointerHandler.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="f8d2d-141">Saiba mais sobre o sistema de entrada na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="f8d2d-142">Como adicionar comentários visuais?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-142">How to add visual feedback?</span></span>
<span data-ttu-id="f8d2d-143">Atribua Interactable.cs a um objeto.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="f8d2d-144">No Inspetor, crie um novo tema.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="f8d2d-145">Usando perfis de tema de interação, você pode adicionar facilmente comentários visuais a todos os Estados de interação de entrada disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="f8d2d-146">O interagir fornece vários tipos de temas, incluindo o tema do sombreador, que permite controlar as propriedades do sombreador por estado de interação.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="f8d2d-147">Saiba mais sobre o interagir na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="f8d2d-148">Outro bloco de construção importante para comentários visuais é o sombreador padrão MRTK.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="f8d2d-149">Com o sombreador MRTK Standard, você pode adicionar facilmente efeitos de comentários visuais, como luz de foco e luz de proximidade.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="f8d2d-150">Como o sombreador MRTK Standard executa significativamente menos cálculos do que o sombreador padrão do Unity, você pode criar uma experiência de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="f8d2d-151">Crie um novo material e selecione o sombreador "Mixed Reality Toolkit > Standard".</span><span class="sxs-lookup"><span data-stu-id="f8d2d-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="f8d2d-152">Ou você pode escolher um dos materiais existentes que usam o sombreador padrão MRTK.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="f8d2d-153">Saiba mais sobre o sombreador Standard MRTK na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="f8d2d-154">Como adicionar comentários de áudio?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-154">How to add audio feedback?</span></span>
<span data-ttu-id="f8d2d-155">Adicione o Áudioname a um objeto.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-155">Add AudioSource to an object.</span></span> <span data-ttu-id="f8d2d-156">Em seguida, nos scripts que expõem eventos de entrada (por exemplo, Interactable.cs ou PointerHandler.cs), atribua o objeto ao evento e selecione Audioname. PlayOneShot ().</span><span class="sxs-lookup"><span data-stu-id="f8d2d-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="f8d2d-157">Você pode usar seus clipes de áudio ou escolher um dos ativos de áudio do MRTK.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="f8d2d-158">Como usar o botão de estilo do HoloLens 2 pré-fabricados?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="f8d2d-159">O MRTK fornece vários tipos de botões de estilo do Shell (SO) do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="f8d2d-160">Ele fornece comentários visuais sofisticados, como luz de proximidade, caixa de compactação e um efeito de ondulação na superfície do botão.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="f8d2d-161">Basta arrastar e soltar um dos botões de pré-fabricado de estilo do HoloLens 2 em sua cena.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="f8d2d-162">O pré-fabricado usa Interactable.cs que é apresentado acima.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="f8d2d-163">Você pode usar eventos expostos, como OnClick (), em ações de gatilho de interação.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="f8d2d-164">Saiba mais sobre o botão pré-fabricados na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="f8d2d-165">Como fazer um objeto seguir você?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-165">How to make an object follow you?</span></span>
<span data-ttu-id="f8d2d-166">Atribua o script RadialView.cs a um objeto.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="f8d2d-167">Ele faz parte da série de script do Solver que permite alcançar vários tipos de posicionamento de objeto no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="f8d2d-168">SolverHandler.cs será adicionado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="f8d2d-169">Veja abaixo um exemplo de configuração do RadialView para obter a marca "acompanhamento lento" – ao longo do comportamento, assim como o menu iniciar no Shell do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="f8d2d-170">Você pode especificar a distância mínima/máxima e os graus de exibição mínimo/máximo.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="f8d2d-171">O exemplo a seguir mostra o posicionamento do objeto entre o intervalo de 0.4 m e 0,8 m dentro de 15 °.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="f8d2d-172">Ajuste os valores de tempo de Lerp para tornar a atualização posicional mais rápida ou mais lenta.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="f8d2d-173">Saiba mais sobre os resolvedores na documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="f8d2d-174">Como fazer um objeto lhe encarar?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-174">How to make an object face you?</span></span>
<span data-ttu-id="f8d2d-175">Atribua o script Billboard.cs a um objeto.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="f8d2d-176">Ele sempre vai encarar você, independentemente da sua posição.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="f8d2d-177">Você pode especificar a opção de eixo dinâmico.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="f8d2d-178">Pronto para criar experiências incríveis para realidade misturada?</span><span class="sxs-lookup"><span data-stu-id="f8d2d-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="f8d2d-179">Visite as páginas abaixo e saiba mais sobre MRTK e realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="f8d2d-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="f8d2d-180">Sobre o autor</span><span class="sxs-lookup"><span data-stu-id="f8d2d-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f8d2d-181"><b>Parque Yoon Dong</b></span><span class="sxs-lookup"><span data-stu-id="f8d2d-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="f8d2d-182">@Microsoft do designer de UX</span><span class="sxs-lookup"><span data-stu-id="f8d2d-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="f8d2d-183">Veja também</span><span class="sxs-lookup"><span data-stu-id="f8d2d-183">See also</span></span>

* [<span data-ttu-id="f8d2d-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="f8d2d-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="f8d2d-185">Portal de documentação do MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="f8d2d-186">Introdução com MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="f8d2d-187">Diretrizes de portabilidade do HoloToolkit para MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d2d-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

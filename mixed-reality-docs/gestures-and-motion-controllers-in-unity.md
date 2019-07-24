---
title: Gestos e controladores de movimento no Unity
description: Há duas maneiras principais de agir em seu olhar no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, Unity, olhar, entrada
ms.openlocfilehash: f0d2835a08ef534af1310db35ccb81888e49aeb8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525767"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="a5d9d-104">Gestos e controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="a5d9d-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="a5d9d-105">Há duas maneiras principais de agir em sua [olhar no Unity](gaze-in-unity.md), gestos de [mão](gestures.md) e [controladores de movimento](motion-controllers.md) no HoloLens e HMD de imersão.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="a5d9d-106">Você acessa os dados de ambas as fontes de entrada espacial por meio das mesmas APIs no Unity.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="a5d9d-107">O Unity fornece duas maneiras principais de acessar dados de entrada espaciais para a realidade mista do Windows, as APIs comuns *Input. getbutton/Input. getaxis* que funcionam em vários SDKs do Unity XR e uma API interactionmanager */GestureRecognizer* específica para A realidade mista do Windows que expõe o conjunto completo de dados de entrada espaciais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="a5d9d-108">Tabela de mapeamento de botões/eixos do Unity</span><span class="sxs-lookup"><span data-stu-id="a5d9d-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="a5d9d-109">As IDs de botão e eixo na tabela abaixo têm suporte no Gerenciador de entrada do Unity para controladores de movimento de realidade mista do Windows por meio das APIs *Input. getbutton/getaxis* , enquanto a coluna "Windows Mr-specific" refere-se às propriedades disponíveis no Tipo de *InteractionSourceState* .</span><span class="sxs-lookup"><span data-stu-id="a5d9d-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="a5d9d-110">Cada uma dessas APIs é descrita detalhadamente nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="a5d9d-111">Os mapeamentos de ID de botão/eixo para a realidade mista do Windows geralmente correspondem às IDs de eixo/botão Oculus.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="a5d9d-112">Os mapeamentos de ID de botão/eixo para a realidade mista do Windows diferem dos mapeamentos do OpenVR de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="a5d9d-113">O mapeamento usa IDs de touchpad que são diferentes de Thumbstick para dar suporte a controladores com Thumbsticks e touchpads.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="a5d9d-114">O mapeamento evita sobrecarregar as IDs de botão a e X para os botões de menu, para deixá-las disponíveis para botões físicos de ABXY.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="a5d9d-115">Entrada</span><span class="sxs-lookup"><span data-stu-id="a5d9d-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="a5d9d-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">APIs comuns do Unity</a></span><span class="sxs-lookup"><span data-stu-id="a5d9d-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="a5d9d-117">(Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="a5d9d-118"><a href="gestures-and-motion-controllers-in-unity.md#">API de entrada específica do Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="a5d9d-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="a5d9d-119">XR. WSA. Entrada</span><span class="sxs-lookup"><span data-stu-id="a5d9d-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="a5d9d-120">À esquerda</span><span class="sxs-lookup"><span data-stu-id="a5d9d-120">Left hand</span></span> </th><th> <span data-ttu-id="a5d9d-121">À direita</span><span class="sxs-lookup"><span data-stu-id="a5d9d-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a5d9d-122">Selecionar gatilho pressionado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="a5d9d-123">Eixo 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="a5d9d-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="a5d9d-124">Eixo 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="a5d9d-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="a5d9d-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="a5d9d-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-126">Selecionar valor analógico do gatilho</span><span class="sxs-lookup"><span data-stu-id="a5d9d-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="a5d9d-127">Eixo 9</span><span class="sxs-lookup"><span data-stu-id="a5d9d-127">Axis 9</span></span> </td><td> <span data-ttu-id="a5d9d-128">Eixo 10</span><span class="sxs-lookup"><span data-stu-id="a5d9d-128">Axis 10</span></span> </td><td> <span data-ttu-id="a5d9d-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="a5d9d-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-130">Selecionar gatilho parcialmente pressionado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="a5d9d-131">Botão 14 <i>(compatível com gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a5d9d-132">Botão 15 <i>(compatível com gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a5d9d-133">selectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="a5d9d-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-134">Botão de menu pressionado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="a5d9d-135">Botão 6 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-135">Button 6\*</span></span> </td><td> <span data-ttu-id="a5d9d-136">Botão 7 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-136">Button 7\*</span></span> </td><td> <span data-ttu-id="a5d9d-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="a5d9d-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-138">Botão de alça pressionado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="a5d9d-139">Eixo 11 = 1,0 (sem valores analógicos)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="a5d9d-140">Botão 4 <i>(compatível com gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a5d9d-141">Eixo 12 = 1,0 (sem valores analógicos)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="a5d9d-142">Botão 5 <i>(compatível com gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a5d9d-143">compreenderam</span><span class="sxs-lookup"><span data-stu-id="a5d9d-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-144">Thumbstick X <i>(esquerda:-1,0, direita: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="a5d9d-145">Eixo 1</span><span class="sxs-lookup"><span data-stu-id="a5d9d-145">Axis 1</span></span> </td><td> <span data-ttu-id="a5d9d-146">Eixo 4</span><span class="sxs-lookup"><span data-stu-id="a5d9d-146">Axis 4</span></span> </td><td> <span data-ttu-id="a5d9d-147">thumbstickPosition. x</span><span class="sxs-lookup"><span data-stu-id="a5d9d-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-148">Thumbstick Y <i>(superior:-1,0, inferior: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="a5d9d-149">Eixo 2</span><span class="sxs-lookup"><span data-stu-id="a5d9d-149">Axis 2</span></span> </td><td> <span data-ttu-id="a5d9d-150">Eixo 5</span><span class="sxs-lookup"><span data-stu-id="a5d9d-150">Axis 5</span></span> </td><td> <span data-ttu-id="a5d9d-151">thumbstickPosition. y</span><span class="sxs-lookup"><span data-stu-id="a5d9d-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-152">Thumbstick pressionado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="a5d9d-153">Botão 8</span><span class="sxs-lookup"><span data-stu-id="a5d9d-153">Button 8</span></span> </td><td> <span data-ttu-id="a5d9d-154">Botão 9</span><span class="sxs-lookup"><span data-stu-id="a5d9d-154">Button 9</span></span> </td><td> <span data-ttu-id="a5d9d-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="a5d9d-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-156">Touchpad X <i>(esquerda:-1,0, direita: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="a5d9d-157">Eixo 17 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="a5d9d-158">Eixo 19 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="a5d9d-159">touchpadPosition. x</span><span class="sxs-lookup"><span data-stu-id="a5d9d-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-160">Touchpad Y <i>(superior:-1,0, inferior: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="a5d9d-161">Eixo 18 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="a5d9d-162">Eixo 20 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="a5d9d-163">touchpadPosition. y</span><span class="sxs-lookup"><span data-stu-id="a5d9d-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-164">Touchpad tocado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="a5d9d-165">Botão 18 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-165">Button 18\*</span></span> </td><td> <span data-ttu-id="a5d9d-166">Botão 19 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-166">Button 19\*</span></span> </td><td> <span data-ttu-id="a5d9d-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="a5d9d-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-168">Touchpad pressionado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="a5d9d-169">Botão 16 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-169">Button 16\*</span></span> </td><td> <span data-ttu-id="a5d9d-170">Botão 17 \*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-170">Button 17\*</span></span> </td><td> <span data-ttu-id="a5d9d-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="a5d9d-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-172">pose da alça de 6DoF de pose ou de ponteiro</span><span class="sxs-lookup"><span data-stu-id="a5d9d-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="a5d9d-173"><i>Segurar</i> somente pose: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="a5d9d-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="a5d9d-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="a5d9d-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="a5d9d-175">Passar <i>alça</i> ou <i>ponteiro</i> como um argumento: SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="a5d9d-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="a5d9d-176">origemstate. sourcePose. TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="a5d9d-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-177">Estado de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="a5d9d-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="a5d9d-178"><i>A precisão da posição e o risco de perda de origem só estão disponíveis por meio da API específica do MR</i> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="a5d9d-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">origemstate. sourcePose. positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="a5d9d-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="a5d9d-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="a5d9d-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="a5d9d-181">Essas IDs de botão/eixo diferem das IDs que o Unity usa para OpenVR devido a colisões nos mapeamentos usados por gamepads, Oculus Touch e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="a5d9d-182">Segurar pose vs. ponto de apontar</span><span class="sxs-lookup"><span data-stu-id="a5d9d-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="a5d9d-183">O Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma, sendo que o design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural "encaminhar" que os aplicativos devem usar para apontar ao renderizar o controle.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="a5d9d-184">Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada origem de interação, a **pose de alça** e a pose do **ponteiro**.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="a5d9d-185">As coordenadas de pose pose e ponteiro representam expressas por todas as APIs do Unity nas coordenadas do mundo global do Unity.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="a5d9d-186">Segurar pose</span><span class="sxs-lookup"><span data-stu-id="a5d9d-186">Grip pose</span></span>

<span data-ttu-id="a5d9d-187">A **alça de pose** representa o local da palma de uma mão detectada por um HoloLens ou o Palm que está segurando um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="a5d9d-188">Em headsets de imersão, a alça de fixação é mais bem usada para renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**, como uma gumes ou uma arma.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="a5d9d-189">A pose de alça também é usada ao visualizar um controlador de movimento, pois o **modelo renderizado** fornecido pelo Windows para um controlador de movimento usa a alça de pose como sua origem e o centro de rotação.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="a5d9d-190">A pose de alça é definida especificamente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="a5d9d-191">A **posição da alça**: O Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="a5d9d-192">No controlador de movimento de realidade mista do Windows, essa posição geralmente se alinha com o botão compreender.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="a5d9d-193">O **eixo direito da orientação de alça**: Quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="a5d9d-194">O **eixo de avanço da orientação de alça**: Quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="a5d9d-195">O **eixo superior da orientação de alça**: O eixo superior implícito pelas definições direita e avançar.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="a5d9d-196">Você pode acessar a alça de pose por meio da API de entrada entre fornecedores do Unity ( *[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) ou por meio da API específica do Windows Mr (*SourceState. SourcePose. TryGetPosition/Rotation*, solicitando dados de pose para o nó de **fixação** ).</span><span class="sxs-lookup"><span data-stu-id="a5d9d-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="a5d9d-197">Pose de ponteiro</span><span class="sxs-lookup"><span data-stu-id="a5d9d-197">Pointer pose</span></span>

<span data-ttu-id="a5d9d-198">A **pose do ponteiro** representa a ponta do controlador que está apontando para frente.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="a5d9d-199">A pose de ponteiro fornecida pelo sistema é mais bem usada para Raycast quando você está **renderizando o próprio modelo de controlador**.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="a5d9d-200">Se você estiver renderizando algum outro objeto virtual no lugar do controlador, como uma arma virtual, você deve apontar com um raio mais natural para esse objeto virtual, como um Ray que viaja ao longo do cilindro do modelo de pressão definido pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="a5d9d-201">Como os usuários podem ver o objeto virtual e não o controlador físico, apontar com o objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="a5d9d-202">Atualmente, a pose do ponteiro está disponível no Unity somente por meio da API específica do Windows Sr, *SourceState. sourcePose. TryGetPosition/Rotation*, passando *InteractionSourceNode. pointer* como o argumento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="a5d9d-203">Estado de controle do controlador</span><span class="sxs-lookup"><span data-stu-id="a5d9d-203">Controller tracking state</span></span>

<span data-ttu-id="a5d9d-204">Assim como os headsets, o controlador de movimento do Windows Mixed Reality não requer nenhuma configuração de sensores de controle externo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="a5d9d-205">Em vez disso, os controladores são acompanhados por sensores no próprio headset.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="a5d9d-206">Se o usuário mover os controladores para fora do campo de exibição do headset, na maioria dos casos, o Windows continuará inferindo as posições do controlador e as fornecerá ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="a5d9d-207">Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="a5d9d-208">Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a5d9d-209">Muitos aplicativos que usam controladores para apontar e ativar elementos de interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="a5d9d-210">A melhor maneira de ter uma ideia para isso é experimentá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="a5d9d-211">Confira este vídeo com exemplos de conteúdo de imersão que funciona com controladores de movimento em vários Estados de controle:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="a5d9d-212">Raciocínio sobre o estado de rastreamento explicitamente</span><span class="sxs-lookup"><span data-stu-id="a5d9d-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="a5d9d-213">Os aplicativos que desejam tratar as posições de forma diferente com base no estado de controle podem ir além e inspecionar as propriedades no estado do controlador, como *SourceLossRisk* e *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="a5d9d-214">Estado de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="a5d9d-214">Tracking state</span></span> </th><th> <span data-ttu-id="a5d9d-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="a5d9d-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="a5d9d-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="a5d9d-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="a5d9d-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="a5d9d-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a5d9d-218"><b>Alta precisão</b> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="a5d9d-219">&lt;1,0</span><span class="sxs-lookup"><span data-stu-id="a5d9d-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a5d9d-220">Alto</span><span class="sxs-lookup"><span data-stu-id="a5d9d-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a5d9d-221">true</span><span class="sxs-lookup"><span data-stu-id="a5d9d-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-222"><b>Alta precisão (com risco de perda)</b> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a5d9d-223">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="a5d9d-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a5d9d-224">Alto</span><span class="sxs-lookup"><span data-stu-id="a5d9d-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a5d9d-225">true</span><span class="sxs-lookup"><span data-stu-id="a5d9d-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-226"><b>Precisão aproximada</b> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a5d9d-227">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="a5d9d-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a5d9d-228">Aproximado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a5d9d-229">true</span><span class="sxs-lookup"><span data-stu-id="a5d9d-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a5d9d-230"><b>Sem posição</b> </span><span class="sxs-lookup"><span data-stu-id="a5d9d-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a5d9d-231">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="a5d9d-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a5d9d-232">Aproximado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a5d9d-233">false</span><span class="sxs-lookup"><span data-stu-id="a5d9d-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="a5d9d-234">Esses Estados de acompanhamento do controlador de movimento são definidos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="a5d9d-235">**Alta precisão:** Embora o controlador de movimento esteja dentro do campo de exibição do headset, ele geralmente fornecerá posições de alta precisão, com base no rastreamento visual.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="a5d9d-236">Observe que um controlador móvel que deixa momentaneamente o campo de exibição ou que é momentaneamente obscurecido dos sensores do headset (por exemplo, por outro lado do usuário) continuará retornando poses de alta precisão por um curto período, com base no acompanhamento inércia do controlador próprio.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="a5d9d-237">**Alta precisão (com risco de perda):** Quando o usuário move o controlador de movimento para cima da borda do campo de exibição do headset, o headset em breve não será capaz de rastrear visualmente a posição do controlador.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="a5d9d-238">O aplicativo sabe quando o controlador atingiu esse limite de FOV vendo o **SourceLossRisk** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="a5d9d-239">Nesse ponto, o aplicativo pode optar por pausar gestos do controlador que exigem um fluxo constante de poses de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="a5d9d-240">**Precisão aproximada:** Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="a5d9d-241">Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a5d9d-242">Muitos aplicativos que usam controladores para apontar para e ativar elementos da interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="a5d9d-243">Os aplicativos com requisitos de entrada mais pesados podem optar por detectar essa queda de **alta** precisão à precisão **aproximada** inspecionando a propriedade **PositionAccuracy** , por exemplo, para dar ao usuário um hitbox mais generosa nos destinos fora da tela durante esse tempo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="a5d9d-244">**Sem posição:** Embora o controlador possa operar com precisão aproximada por um longo tempo, às vezes o sistema sabe que até mesmo uma posição bloqueada pelo corpo não é significativa no momento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="a5d9d-245">Por exemplo, um controlador que acabou de ser ativado pode nunca ter sido observado visualmente ou um usuário pode colocar um controlador selecionado por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="a5d9d-246">Naqueles momentos, o sistema não fornecerá nenhuma posição para o aplicativo e *TryGetPosition* retornará false.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="a5d9d-247">APIs comuns do Unity (Input. getbutton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="a5d9d-248">**Namespace:** *UnityEngine*, *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="a5d9d-249">**Tipos**: *Entrada*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="a5d9d-250">No momento, o Unity usa suas APIs de *entrada geral. getbutton/Input. getaxis* para expor a entrada para [o SDK do OCULUS](https://docs.unity3d.com/Manual/OculusControllers.html), [o SDK do OpenVR e a](https://docs.unity3d.com/Manual/OpenVRControllers.html) realidade mista do Windows, incluindo controladores de mãos e de movimento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="a5d9d-251">Se seu aplicativo usa essas APIs para entrada, ele pode facilmente dar suporte a controladores de movimento em vários SDKs do XR, incluindo a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="a5d9d-252">Obtendo o estado pressionado de um botão lógico</span><span class="sxs-lookup"><span data-stu-id="a5d9d-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="a5d9d-253">Para usar as APIs de entrada gerais da Unity, você normalmente começará com a vinculação de botões e eixos a nomes lógicos no [Gerenciador de entrada do Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), ligando um botão ou IDs de eixo a cada nome.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="a5d9d-254">Em seguida, você pode escrever código que se refere a esse botão lógico/nome do eixo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="a5d9d-255">Por exemplo, para mapear o botão de gatilho do controlador de movimento à esquerda para a ação enviar, acesse **editar > configurações do projeto > entrada** no Unity e expanda as propriedades da seção enviar em eixos.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="a5d9d-256">Altere o **botão** de postagem ou a propriedade do **botão Alt positivo** para ler o **botão 14 do joystick**, desta forma:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="a5d9d-257">![InputManager do Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="a5d9d-258">*InputManager do Unity*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-258">*Unity InputManager*</span></span>

<span data-ttu-id="a5d9d-259">O script pode, então, verificar a ação de envio usando *Input. getbutton*:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="a5d9d-260">Você pode adicionar mais botões lógicos alterando a propriedade **tamanho** em **eixos**.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="a5d9d-261">Obtendo um estado de botão físico pressionado diretamente</span><span class="sxs-lookup"><span data-stu-id="a5d9d-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="a5d9d-262">Você também pode acessar os botões manualmente por seu nome totalmente qualificado, usando *Input. GetKey*:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="a5d9d-263">Obter uma pose do controlador de movimento ou mão</span><span class="sxs-lookup"><span data-stu-id="a5d9d-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="a5d9d-264">Você pode acessar a posição e a rotação do controlador, usando o *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="a5d9d-265">Observe que isso representa a pose de alça do controlador (onde o usuário mantém o controlador), que é útil para renderizar uma gumes ou uma arma na mão do usuário ou um modelo do próprio controlador.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="a5d9d-266">Observe que a relação entre essa pose de alça e a pose do ponteiro (onde a ponta do controlador está apontando) pode diferir entre os controladores.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="a5d9d-267">Neste momento, o acesso à pose do ponteiro do controlador só é possível por meio da API de entrada específica do MR, descrita nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="a5d9d-268">APIs específicas do Windows (XR. WSA. Entrada</span><span class="sxs-lookup"><span data-stu-id="a5d9d-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="a5d9d-269">**Namespace:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="a5d9d-270">**Tipos**: Interactionmanager, *InteractionSourceState*, peractionname, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="a5d9d-271">Para obter informações mais detalhadas sobre a entrada da mão de realidade mista do Windows (para o HoloLens) e os controladores de movimento, você pode optar por usar as APIs de entrada espaciais específicas do Windows no namespace *UnityEngine. XR. WSA. Input* .</span><span class="sxs-lookup"><span data-stu-id="a5d9d-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="a5d9d-272">Isso permite que você acesse informações adicionais, como precisão de posição ou tipo de fonte, permitindo que você diga as mãos e os controladores.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="a5d9d-273">Sondando o estado dos controladores de mãos e de movimento</span><span class="sxs-lookup"><span data-stu-id="a5d9d-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="a5d9d-274">Você pode sondar o estado deste quadro para cada fonte de interação (controlador de mão ou de movimento) usando o método *GetCurrentReading* .</span><span class="sxs-lookup"><span data-stu-id="a5d9d-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="a5d9d-275">Cada *InteractionSourceState* que você retorna representa uma fonte de interação no momento atual.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="a5d9d-276">O *InteractionSourceState* expõe informações como:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="a5d9d-277">Que [tipos de prensas](motion-controllers.md) estão ocorrendo (Select/menu/Segure/Touchpad/Thumbstick)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="a5d9d-278">Outros dados específicos de controladores de movimento, como as coordenadas XY do Touchpad e/ou do Thumbstick e o estado tocado</span><span class="sxs-lookup"><span data-stu-id="a5d9d-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="a5d9d-279">O InteractionSourceKind para saber se a origem é uma mão ou um controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="a5d9d-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="a5d9d-280">Sondagem para encaminhar representações de renderização previstas</span><span class="sxs-lookup"><span data-stu-id="a5d9d-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="a5d9d-281">Durante a sondagem de dados de origem de interação de mãos e controladores, as poses que você obtém são as mais previstas para o momento em que o fótons do quadro atingirá os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="a5d9d-282">Essas poses previstas antecipadas são mais  bem usadas para renderizar o controlador ou um objeto mantido em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="a5d9d-283">Se você estiver direcionando um determinado Press ou Release com o controlador, isso será mais preciso se você usar as APIs de eventos de histórico descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="a5d9d-284">Você também pode obter a pose de cabeça prevista para este quadro atual.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="a5d9d-285">Assim como acontece com o pose de origem, isso  é útil para renderizar um cursor, embora o direcionamento de uma determinada prensa ou versão seja mais preciso se você usar as APIs de evento históricas descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="a5d9d-286">Tratamento de eventos de origem de interação</span><span class="sxs-lookup"><span data-stu-id="a5d9d-286">Handling interaction source events</span></span>

<span data-ttu-id="a5d9d-287">Para lidar com eventos de entrada à medida que eles acontecem com seus dados históricos de histórico precisos, você pode manipular eventos de origem de interação em vez de sondagem.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="a5d9d-288">Para lidar com eventos de origem de interação:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-288">To handle interaction source events:</span></span>
* <span data-ttu-id="a5d9d-289">Registre-se para um evento de entrada entre *ações* .</span><span class="sxs-lookup"><span data-stu-id="a5d9d-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="a5d9d-290">Para cada tipo de evento de interação em que você está interessado, você precisa assiná-lo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="a5d9d-291">Manipule o evento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-291">Handle the event.</span></span> <span data-ttu-id="a5d9d-292">Depois de se inscrever em um evento de interação, você receberá o retorno de chamada quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="a5d9d-293">No exemplo de *SourcePressed* , isso será depois que a origem for detectada e antes de ser liberada ou perdida.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="a5d9d-294">Como parar de lidar com um evento</span><span class="sxs-lookup"><span data-stu-id="a5d9d-294">How to stop handling an event</span></span>

<span data-ttu-id="a5d9d-295">Você precisa parar de lidar com um evento quando não estiver mais interessado no evento ou se estiver destruindo o objeto que assinou o evento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="a5d9d-296">Para parar de lidar com o evento, cancele a assinatura do evento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="a5d9d-297">Lista de eventos de origem de interação</span><span class="sxs-lookup"><span data-stu-id="a5d9d-297">List of interaction source events</span></span>

<span data-ttu-id="a5d9d-298">Os eventos de origem de interação disponíveis são:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-298">The available interaction source events are:</span></span>
* <span data-ttu-id="a5d9d-299">*InteractionSourceDetected* (a origem se torna ativa)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="a5d9d-300">*InteractionSourceLost* (torna-se inativo)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="a5d9d-301">*InteractionSourcePressed* (toque, pressionamento de botão ou "selecionar" com total)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="a5d9d-302">*InteractionSourceReleased* (fim de um toque, botão liberado ou fim de "selecionar" com liberação)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="a5d9d-303">*InteractionSourceUpdated* (move ou altera algum outro Estado)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="a5d9d-304">Os eventos de direcionamento histórico representam que correspondem mais precisamente a uma prensa ou liberação</span><span class="sxs-lookup"><span data-stu-id="a5d9d-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="a5d9d-305">As APIs de sondagem descritas anteriormente fornecem às suas representações previstas de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="a5d9d-306">Embora essas poses previstas sejam melhores para renderizar o controlador ou um objeto portátil Virtual, as poses futuras não são ideais para o direcionamento, por dois motivos principais:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="a5d9d-307">Quando o usuário pressiona um botão em um controlador, pode haver cerca de 20 ms de latência sem fio sobre o Bluetooth antes que o sistema receba a prensa.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="a5d9d-308">Em seguida, se você estiver usando uma pose prevista para o futuro, haveria mais 10 20 ms de previsão de encaminhamento aplicada ao destino quando o fótons do quadro atual atingirá os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="a5d9d-309">Isso significa que a sondagem fornece uma pose de origem ou uma pose de cabeça que é de 30 a 40ms para frente, de onde a cabeça do usuário e as mãos realmente estavam de volta quando a imprensa ou a versão ocorreu.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="a5d9d-310">Para entrada à mão do HoloLens, enquanto não há atraso de transmissão sem fio, há um atraso de processamento semelhante para detectar a prensa.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="a5d9d-311">Para ter um destino com precisão com base na intenção original do usuário para um pressionamento de mão ou de controlador, você deve usar a pose de origem histórica ou de cabeçalho desse evento de entrada *InteractionSourcePressed* ou *InteractionSourceReleased* .</span><span class="sxs-lookup"><span data-stu-id="a5d9d-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="a5d9d-312">Você pode direcionar um Press ou Release com dados históricos de pose do cabeçalho do usuário ou de seu controlador:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="a5d9d-313">A parte de cabeça no momento em que uma ocorrência de gesto ou controlador ocorreu, que pode ser **usada para determinar** o que o usuário estava [nuvensndo](gaze.md) :</span><span class="sxs-lookup"><span data-stu-id="a5d9d-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="a5d9d-314">A origem representa no momento em que uma ocorrência de controlador de movimento ocorreu, que pode ser **usada para determinar** a que o usuário estava apontando o controlador.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="a5d9d-315">Esse será o estado do controlador que sofreu a prensa.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="a5d9d-316">Se você estiver renderizando o próprio controlador, poderá solicitar a pose do ponteiro em vez da pose de alça, para atingir o direcionamento de raio a partir do que o usuário considerará a dica natural desse controlador renderizado:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="a5d9d-317">Exemplo de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-317">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="a5d9d-318">APIs de gesto de composição de alto nível (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="a5d9d-319">**Namespace:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="a5d9d-320">**Tipos**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="a5d9d-321">Seu aplicativo também pode reconhecer gestos de composição de nível superior para fontes de entrada espaciais, toque, retenção, manipulação e gestos de navegação.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="a5d9d-322">Você pode reconhecer esses gestos compostos entre os controladores de [mão](gestures.md) e de [movimento](motion-controllers.md) usando o GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="a5d9d-323">Cada evento de gesto no GestureRecognizer fornece o SourceKind para a entrada, bem como a cabeça de destino Ray no momento do evento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="a5d9d-324">Alguns eventos fornecem informações adicionais específicas do contexto.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="a5d9d-325">Há apenas algumas etapas necessárias para capturar gestos usando um reconhecedor de gestos:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="a5d9d-326">Criar um novo reconhecedor de gestos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="a5d9d-327">Especificar quais gestos observar</span><span class="sxs-lookup"><span data-stu-id="a5d9d-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="a5d9d-328">Assinar eventos para esses gestos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="a5d9d-329">Começar a capturar gestos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="a5d9d-330">Criar um novo reconhecedor de gestos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="a5d9d-331">Para usar o *GestureRecognizer*, você deve ter criado um *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="a5d9d-332">Especificar quais gestos observar</span><span class="sxs-lookup"><span data-stu-id="a5d9d-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="a5d9d-333">Especifique em quais gestos você está interessado por meio de *SetRecognizableGestures ()* :</span><span class="sxs-lookup"><span data-stu-id="a5d9d-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="a5d9d-334">Assinar eventos para esses gestos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="a5d9d-335">Assine eventos para os gestos nos quais você está interessado.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-335">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="a5d9d-336">Os gestos de navegação e manipulação são mutuamente exclusivos em uma instância de um *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="a5d9d-337">Começar a capturar gestos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-337">Start capturing gestures</span></span>

<span data-ttu-id="a5d9d-338">Por padrão, um *GestureRecognizer* não monitora a entrada até que *StartCapturingGestures ()* seja chamado.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="a5d9d-339">É possível que um evento de gesto possa ser gerado após *StopCapturingGestures ()* ser chamado se a entrada tiver sido executada antes do quadro em que *StopCapturingGestures ()* foi processado.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="a5d9d-340">O *GestureRecognizer* se lembrará se ele estava ligado ou desligado durante o quadro Previou no qual o gesto realmente ocorreu e, portanto, é confiável para iniciar e parar o monitoramento de gestos com base no direcionamento olhar do quadro.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="a5d9d-341">Parar a captura de gestos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-341">Stop capturing gestures</span></span>

<span data-ttu-id="a5d9d-342">Para interromper o reconhecimento de gesto:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="a5d9d-343">Removendo um reconhecedor de gesto</span><span class="sxs-lookup"><span data-stu-id="a5d9d-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="a5d9d-344">Lembre-se de cancelar a assinatura de eventos assinados antes de destruir um objeto *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="a5d9d-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="a5d9d-345">Renderizando o modelo de controlador de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="a5d9d-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="a5d9d-346">![Modelo de controlador de movimento e teleportação](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="a5d9d-347">*Modelo de controlador de movimento e teleportação*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="a5d9d-348">Para renderizar os controladores de movimento em seu aplicativo que correspondam aos controladores físicos que os usuários estão mantendo e articulados conforme vários botões são pressionados, você pode usar o **MotionController pré-fabricado** no [Kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="a5d9d-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="a5d9d-349">Esse pré-fabricado dinamicamente carrega o modelo de glTF correto em tempo de execução do driver do controlador de movimento instalado do sistema.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="a5d9d-350">É importante carregar esses modelos dinamicamente, em vez de importá-los manualmente no editor, para que seu aplicativo mostre modelos 3D fisicamente precisos para todos os controladores atuais e futuros que seus usuários possam ter.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="a5d9d-351">Siga as instruções de [introdução](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) para baixar o kit de ferramentas de realidade misturada e adicioná-lo ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="a5d9d-352">Se você substituiu a câmera pelo *MixedRealityCameraParent* pré-fabricado como parte das etapas introdução, está pronto!</span><span class="sxs-lookup"><span data-stu-id="a5d9d-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="a5d9d-353">Esse pré-fabricado inclui a renderização do controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="a5d9d-354">Caso contrário, adicione *assets/HoloToolkit/Input/pré-fabricados/MotionControllers. pré-fabricado* à sua cena no painel do projeto.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="a5d9d-355">Você desejará adicionar esse pré-fabricado como um filho de qualquer objeto pai usado para mover a câmera quando o usuário estiver em sua cena, para que os controladores acompanhem o usuário.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="a5d9d-356">Se seu aplicativo não envolver a teleportabilidade, basta adicionar o pré-fabricado na raiz da sua cena.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="a5d9d-357">Lançando objetos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-357">Throwing objects</span></span>

<span data-ttu-id="a5d9d-358">A geração de objetos na realidade virtual é um problema mais difícil e, em primeiro lugar, pode parecer.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="a5d9d-359">Assim como acontece com a maioria das interações com base fisicamente, quando o jogo atua de forma inesperada, ele é imediatamente óbvio e quebra imersão.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="a5d9d-360">Nós gastamos algum tempo pensando em como representar um comportamento de lançamento fisicamente correto e apresentamos algumas diretrizes, habilitadas por meio de atualizações em nossa plataforma, que gostaríamos de compartilhar com você.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="a5d9d-361">Você pode encontrar um exemplo de como é recomendável implementar o lançamento [aqui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="a5d9d-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="a5d9d-362">Este exemplo segue estas quatro diretrizes:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="a5d9d-363">**Use a *velocidade* do controlador em vez da posição**.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="a5d9d-364">Na atualização de novembro do Windows, apresentamos uma alteração no comportamento no estado de [controle posicional ' ' aproximado](motion-controllers.md#controller-tracking-state)'.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="a5d9d-365">Quando nesse estado, as informações de velocidade sobre o controlador continuarão sendo relatadas durante o período em que acreditamos que seja alta precisão, o que geralmente é maior que a posição permanece com alta precisão.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="a5d9d-366">**Incorpore a *velocidade angular* do controlador**.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="a5d9d-367">Essa lógica está todas contidas no `throwing.cs` arquivo `GetThrownObjectVelAngVel` no método estático, dentro do pacote vinculado acima:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="a5d9d-368">À medida que a velocidade angular é conservada, o objeto gerado deve manter a mesma velocidade angular que tinha no momento do lançamento:`objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="a5d9d-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="a5d9d-369">Como o centro da massa do objeto gerado provavelmente não está na origem da pose de alça, ele provavelmente tem uma velocidade diferente do controlador no quadro de referência do usuário.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="a5d9d-370">A parte da velocidade do objeto que contribuiu dessa forma é a velocidade tangential instantânea do centro da massa do objeto gerado em relação à origem do controlador.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="a5d9d-371">Essa velocidade de tangential é o produto cruzado da velocidade angular do controlador com o vetor que representa a distância entre a origem do controlador e o centro da massa do objeto gerado.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="a5d9d-372">A velocidade total do objeto gerado é, portanto, a soma da velocidade do controlador e dessa velocidade de tangential:`objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="a5d9d-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="a5d9d-373">**Preste muita atenção à *hora* em que aplicamos a velocidade**.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="a5d9d-374">Quando um botão é pressionado, pode levar até 20 ms para que esse evento seja emergido por meio do Bluetooth para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="a5d9d-375">Isso significa que, se você sondar uma alteração de estado do controlador de pressionado para não pressionado ou vice-versa, o controlador apresentará as informações que você obtém com ele, na verdade, estará à frente dessa alteração no estado.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="a5d9d-376">Além disso, a pose do controlador apresentada por nossa API de sondagem está prevista para refletir uma causa provável no momento em que o quadro será exibido, o que poderia ser mais 20 ms no futuro.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="a5d9d-377">Isso é bom para *renderizar* objetos mantidos, mas aumenta nosso problema de  tempo para direcionar o objeto à medida que calculamos a trajetória para o momento em que o usuário lançou o seu lançamento.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="a5d9d-378">Felizmente, com a atualização de novembro, quando um evento do Unity como *InteractionSourcePressed* ou *InteractionSourceReleased* é enviado, o estado inclui os dados históricos de back quando o botão foi realmente pressionado ou liberado.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="a5d9d-379">Para obter a renderização de controlador e o direcionamento de controlador mais precisos durante as jogadas, você deve usar corretamente a sondagem e o evento, conforme apropriado:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="a5d9d-380">Para renderizar cada quadro do **controlador** , seu aplicativo deve posicionar o *gameobject* do controlador no controlador previsto para o momento da Photon do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="a5d9d-381">Você obtém esses dados de APIs de sondagem do Unity como a *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* ou *[XR. WSA. Entrada. interactionmanager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span><span class="sxs-lookup"><span data-stu-id="a5d9d-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="a5d9d-382">Para **direcionamento de controlador** em uma prensa ou liberação, seu aplicativo deve Raycast e calcular as trajetórias com base na pose do controlador histórico para esse evento de Press ou Release.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="a5d9d-383">Você obtém esses dados das APIs de eventos do Unity, como interactionmanager *[. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span><span class="sxs-lookup"><span data-stu-id="a5d9d-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="a5d9d-384">**Use a pose de alça**.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-384">**Use the grip pose**.</span></span> <span data-ttu-id="a5d9d-385">A velocidade angular e a velocidade são relatadas em relação à pose de alça, não à pose de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="a5d9d-386">O lançamento continuará a melhorar com futuras atualizações do Windows e você poderá esperar mais informações sobre ela aqui.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="a5d9d-387">Controladores de gesto e movimento no MRTK v2</span><span class="sxs-lookup"><span data-stu-id="a5d9d-387">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="a5d9d-388">Você pode acessar o gesto e o controlador de movimento do Gerenciador de entrada.</span><span class="sxs-lookup"><span data-stu-id="a5d9d-388">You can access gesture and motion controller from the input Manager.</span></span> 
* [<span data-ttu-id="a5d9d-389">Gesto no MRTK v2</span><span class="sxs-lookup"><span data-stu-id="a5d9d-389">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="a5d9d-390">Controlador de movimento no MRTK v2</span><span class="sxs-lookup"><span data-stu-id="a5d9d-390">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="a5d9d-391">Siga junto com os tutoriais</span><span class="sxs-lookup"><span data-stu-id="a5d9d-391">Follow along with tutorials</span></span>

<span data-ttu-id="a5d9d-392">Os tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis na Academia de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="a5d9d-392">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="a5d9d-393">Entrada do MR 211: gesto</span><span class="sxs-lookup"><span data-stu-id="a5d9d-393">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="a5d9d-394">Entrada do MR 213: controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-394">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="a5d9d-395">[![Entrada MR 213-controlador de movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="a5d9d-395">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="a5d9d-396">*Entrada MR 213-controlador de movimento*</span><span class="sxs-lookup"><span data-stu-id="a5d9d-396">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="a5d9d-397">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5d9d-397">See also</span></span>

* [<span data-ttu-id="a5d9d-398">Gestos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-398">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="a5d9d-399">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="a5d9d-399">Motion controllers</span></span>](motion-controllers.md)



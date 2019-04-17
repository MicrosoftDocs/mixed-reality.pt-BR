---
title: Gestos e controladores de movimento no Unity
description: Há duas maneiras principais para agir em seu foco no Unity, gestos de mão e controladores de movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimento, unity, olhar, de entrada
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589103"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="1989f-104">Gestos e controladores de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="1989f-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="1989f-105">Há duas maneiras principais para agir em seu [contempla Unity](gaze-in-unity.md), [gestos de mão](gestures.md) e [controladores de movimento](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="1989f-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="1989f-106">Você acessa os dados para ambas as fontes de entrada espacial por meio de APIs mesmas no Unity.</span><span class="sxs-lookup"><span data-stu-id="1989f-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="1989f-107">Unity fornece duas maneiras principais de acessar dados espaciais de entrada para o Windows Mixed Reality, comum *Input.GetButton/Input.GetAxis* APIs que funcionam entre vários SDKs para XR Unity, e um *InteractionManager / GestureRecognizer* API específica para o Windows Mixed Reality que expõe o conjunto completo de dados espaciais de entrada disponíveis.</span><span class="sxs-lookup"><span data-stu-id="1989f-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="1989f-108">Tabela de mapeamento de botão/eixo do Unity</span><span class="sxs-lookup"><span data-stu-id="1989f-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="1989f-109">As IDs de eixo e botão na tabela a seguir têm suporte no Unity Input Manager para controladores de movimento de realidade mista do Windows por meio de *Input.GetButton/GetAxis* APIs, enquanto a coluna "MR do Windows específica" refere-se às propriedades disponíveis para desativar o *InteractionSourceState* tipo.</span><span class="sxs-lookup"><span data-stu-id="1989f-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="1989f-110">Cada uma dessas APIs são descritos em detalhes nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="1989f-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="1989f-111">Os mapeamentos de ID do botão/eixo para Windows Mixed Reality geralmente corresponde ao botão Oculus/eixo IDs.</span><span class="sxs-lookup"><span data-stu-id="1989f-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="1989f-112">Os mapeamentos de ID do botão/eixo para Windows Mixed Reality diferem de mapeamentos do OpenVR de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="1989f-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="1989f-113">O mapeamento usa as IDs de touchpad são distintas de direcional, para dar suporte a controladores com alavancas direcionais e touchpads.</span><span class="sxs-lookup"><span data-stu-id="1989f-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="1989f-114">O mapeamento evita sobrecarregar o botão A e X IDs para os botões de Menu, deixar aqueles disponíveis para os botões ABXY físicos.</span><span class="sxs-lookup"><span data-stu-id="1989f-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="1989f-115">Entrada</span><span class="sxs-lookup"><span data-stu-id="1989f-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="1989f-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">APIs comuns do Unity</a></span><span class="sxs-lookup"><span data-stu-id="1989f-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="1989f-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="1989f-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="1989f-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">API de entrada específicos do Windows MR</a></span><span class="sxs-lookup"><span data-stu-id="1989f-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="1989f-119">(XR.WSA.Input)</span><span class="sxs-lookup"><span data-stu-id="1989f-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="1989f-120">À esquerda</span><span class="sxs-lookup"><span data-stu-id="1989f-120">Left hand</span></span> </th><th> <span data-ttu-id="1989f-121">Mão direita</span><span class="sxs-lookup"><span data-stu-id="1989f-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="1989f-122">Selecione o gatilho pressionado</span><span class="sxs-lookup"><span data-stu-id="1989f-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="1989f-123">Eixo 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="1989f-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="1989f-124">Eixo 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="1989f-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="1989f-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="1989f-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-126">Selecionar valor analógica do gatilho</span><span class="sxs-lookup"><span data-stu-id="1989f-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="1989f-127">Eixo 9</span><span class="sxs-lookup"><span data-stu-id="1989f-127">Axis 9</span></span> </td><td> <span data-ttu-id="1989f-128">Axis 10</span><span class="sxs-lookup"><span data-stu-id="1989f-128">Axis 10</span></span> </td><td> <span data-ttu-id="1989f-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="1989f-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-130">Selecione o gatilho parcialmente pressionado</span><span class="sxs-lookup"><span data-stu-id="1989f-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="1989f-131">Botão 14 <i>(compat gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="1989f-132">Botão 15 <i>(compat gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="1989f-133">selectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="1989f-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-134">Botão de menu pressionado</span><span class="sxs-lookup"><span data-stu-id="1989f-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="1989f-135">Botão 6 \*</span><span class="sxs-lookup"><span data-stu-id="1989f-135">Button 6\*</span></span> </td><td> <span data-ttu-id="1989f-136">Botão 7 \*</span><span class="sxs-lookup"><span data-stu-id="1989f-136">Button 7\*</span></span> </td><td> <span data-ttu-id="1989f-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="1989f-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-138">Botão alça pressionado</span><span class="sxs-lookup"><span data-stu-id="1989f-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="1989f-139">Eixo 11 = 1.0 (nenhum valor analógico)</span><span class="sxs-lookup"><span data-stu-id="1989f-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="1989f-140">Botão 4 <i>(compat gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="1989f-141">Eixo 12 = 1.0 (nenhum valor analógico)</span><span class="sxs-lookup"><span data-stu-id="1989f-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="1989f-142">Botão 5 <i>(compat gamepad)</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="1989f-143">foi segurado</span><span class="sxs-lookup"><span data-stu-id="1989f-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-144">X analógico <i>(à esquerda: -1,0, à direita: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="1989f-145">Axis 1</span><span class="sxs-lookup"><span data-stu-id="1989f-145">Axis 1</span></span> </td><td> <span data-ttu-id="1989f-146">Eixo 4</span><span class="sxs-lookup"><span data-stu-id="1989f-146">Axis 4</span></span> </td><td> <span data-ttu-id="1989f-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="1989f-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-148">Y analógico <i>(parte superior: -1,0, parte inferior: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="1989f-149">Axis 2</span><span class="sxs-lookup"><span data-stu-id="1989f-149">Axis 2</span></span> </td><td> <span data-ttu-id="1989f-150">Eixo 5</span><span class="sxs-lookup"><span data-stu-id="1989f-150">Axis 5</span></span> </td><td> <span data-ttu-id="1989f-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="1989f-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-152">Direcional pressionado</span><span class="sxs-lookup"><span data-stu-id="1989f-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="1989f-153">8 de botão</span><span class="sxs-lookup"><span data-stu-id="1989f-153">Button 8</span></span> </td><td> <span data-ttu-id="1989f-154">9 de botão</span><span class="sxs-lookup"><span data-stu-id="1989f-154">Button 9</span></span> </td><td> <span data-ttu-id="1989f-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="1989f-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-156">X touchpad <i>(à esquerda: -1,0, à direita: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="1989f-157">Eixo 17 \*</span><span class="sxs-lookup"><span data-stu-id="1989f-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="1989f-158">Axis 19\*</span><span class="sxs-lookup"><span data-stu-id="1989f-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="1989f-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="1989f-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-160">Y touchpad <i>(parte superior: -1,0, parte inferior: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="1989f-161">Axis 18\*</span><span class="sxs-lookup"><span data-stu-id="1989f-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="1989f-162">Axis 20\*</span><span class="sxs-lookup"><span data-stu-id="1989f-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="1989f-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="1989f-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-164">Touchpad tocada</span><span class="sxs-lookup"><span data-stu-id="1989f-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="1989f-165">Botão 18 \*</span><span class="sxs-lookup"><span data-stu-id="1989f-165">Button 18\*</span></span> </td><td> <span data-ttu-id="1989f-166">Botão 19 \*</span><span class="sxs-lookup"><span data-stu-id="1989f-166">Button 19\*</span></span> </td><td> <span data-ttu-id="1989f-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="1989f-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-168">Touchpad pressionado</span><span class="sxs-lookup"><span data-stu-id="1989f-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="1989f-169">Botão 16 \*</span><span class="sxs-lookup"><span data-stu-id="1989f-169">Button 16\*</span></span> </td><td> <span data-ttu-id="1989f-170">Botão 17 \*</span><span class="sxs-lookup"><span data-stu-id="1989f-170">Button 17\*</span></span> </td><td> <span data-ttu-id="1989f-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="1989f-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-172">6DoF alça pose ou ponteiro pose</span><span class="sxs-lookup"><span data-stu-id="1989f-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="1989f-173"><i>Alça</i> representam apenas: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="1989f-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="1989f-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="1989f-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="1989f-175">Passar <i>alça</i> ou <i>ponteiro</i> como um argumento: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="1989f-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="1989f-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="1989f-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="1989f-177">Estado de controle</span><span class="sxs-lookup"><span data-stu-id="1989f-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="1989f-178"><i>Posição precisão e a origem do risco de perda disponível apenas por meio da API específica MR</i> </span><span class="sxs-lookup"><span data-stu-id="1989f-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="1989f-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="1989f-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="1989f-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="1989f-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="1989f-181">Essas IDs de botão/eixo difere as IDs que usa o Unity para OpenVR devido a colisões nos mapeamentos usados pelo gamepads, toque Oculus e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="1989f-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="1989f-182">Alça pose versus pose apontador</span><span class="sxs-lookup"><span data-stu-id="1989f-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="1989f-183">Realidade mista do Windows oferece suporte a controladores de movimento em uma variedade de fatores forma, com o design de cada controlador difere em sua relação entre a posição do usuário mão e natural "encaminhar" direção que aplicativos deve usar para apontando ao renderizar o controlador.</span><span class="sxs-lookup"><span data-stu-id="1989f-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="1989f-184">Para melhor representar esses controladores, há dois tipos de poses, você pode investigar para cada fonte de interação, o **alça pose** e o **pose ponteiro**.</span><span class="sxs-lookup"><span data-stu-id="1989f-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="1989f-185">Ambas as as alça pose e ponteiro representam as coordenadas são expressas por todas as APIs do Unity em coordenadas de mundo globais do Unity.</span><span class="sxs-lookup"><span data-stu-id="1989f-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="1989f-186">Alça pose</span><span class="sxs-lookup"><span data-stu-id="1989f-186">Grip pose</span></span>

<span data-ttu-id="1989f-187">O **alça pose** representa o local de palma da mão detectada por um HoloLens ou palma mantendo um controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="1989f-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="1989f-188">Em fones imersivos em exposição, a alça pose é melhor usada para renderizar **mão do usuário** ou **um objeto é mantido em mãos do usuário**, como uma espada ou elétrons.</span><span class="sxs-lookup"><span data-stu-id="1989f-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="1989f-189">A alça pose também é usada quando visualizando um controlador de animação, como o **que podem ser renderizado modelo** fornecida pelo Windows para um movimento controlador usa a alça pose como sua origem e o Centro de rotação.</span><span class="sxs-lookup"><span data-stu-id="1989f-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="1989f-190">A alça pose é definida especificamente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1989f-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="1989f-191">O **segure posição**: O centroide de palm pressionando o controlador naturalmente, ajustado esquerda ou direita para centralizar a posição dentro a alça.</span><span class="sxs-lookup"><span data-stu-id="1989f-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="1989f-192">No controlador de animação do Windows Mixed Reality, essa posição geralmente se alinha com o botão de compreensão.</span><span class="sxs-lookup"><span data-stu-id="1989f-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="1989f-193">O **Segure o eixo à direita da orientação**: Quando você abre completamente sua mão para formar uma dedo simples 5 pose, raio que é normal para o palm (para a frente da esquerda palm, com versões anteriores do palm à direita)</span><span class="sxs-lookup"><span data-stu-id="1989f-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="1989f-194">O **Segure o eixo de encaminhamento da orientação**: Quando você fecha sua mão parcialmente (como se que mantém o controlador), o raio que aponta "forward" por meio de tubo formado por seus dedos não thumb.</span><span class="sxs-lookup"><span data-stu-id="1989f-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="1989f-195">O **segure orientação backup eixo**: O eixo de cima indicado pelas definições de direito e Avançar.</span><span class="sxs-lookup"><span data-stu-id="1989f-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="1989f-196">Você pode acessar a alça pose por meio da API de entrada entre fornecedores do Unity, qualquer um dos (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) ou por meio da API do Windows MR específica (*sourceState.sourcePose.TryGetPosition/Rotation*, solicitando apresentam dados para o **alça** nó).</span><span class="sxs-lookup"><span data-stu-id="1989f-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="1989f-197">Ponteiro pose</span><span class="sxs-lookup"><span data-stu-id="1989f-197">Pointer pose</span></span>

<span data-ttu-id="1989f-198">O **ponteiro pose** representa a dica do controlador que aponta para a frente.</span><span class="sxs-lookup"><span data-stu-id="1989f-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="1989f-199">O ponteiro fornecido pelo sistema pose é melhor usado para raycast quando você estiver **Renderizando o próprio modelo de controlador**.</span><span class="sxs-lookup"><span data-stu-id="1989f-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="1989f-200">Se você estiver renderizando algum outro objeto virtual no lugar do controlador, como um de elétrons virtual, você deve apontar com um raio que seja mais natural para esse objeto virtual, como um raio que viaja ao longo do corpo do modelo de elétrons definidas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1989f-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="1989f-201">Porque os usuários podem ver o objeto virtual e não o controlador de físico, que aponta para ao objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1989f-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="1989f-202">Atualmente, pose o ponteiro está disponível no Unity apenas pela API do Windows MR específico, *sourceState.sourcePose.TryGetPosition/Rotation*, passando *InteractionSourceNode.Pointer* como o argumento.</span><span class="sxs-lookup"><span data-stu-id="1989f-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="1989f-203">Estado do controlador de rastreamento</span><span class="sxs-lookup"><span data-stu-id="1989f-203">Controller tracking state</span></span>

<span data-ttu-id="1989f-204">Como fones de ouvido, o controlador de animação do Windows Mixed Reality não exige nenhuma configuração de sensores de controle externo.</span><span class="sxs-lookup"><span data-stu-id="1989f-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="1989f-205">Em vez disso, os controladores são controlados pelos sensores no fone de ouvido em si.</span><span class="sxs-lookup"><span data-stu-id="1989f-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="1989f-206">Se o usuário move os controladores de exibição de campo do fone de ouvido, na maioria dos casos Windows continuará inferir posições de controlador e fornecê-los para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1989f-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="1989f-207">Quando o controlador perdeu visual de acompanhamento de tempo suficiente, posições do controlador descartará a precisão aproximados posições.</span><span class="sxs-lookup"><span data-stu-id="1989f-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="1989f-208">Neste ponto, o sistema será o bloqueio de corpo de controlador para o controle do usuário, a posição do usuário conforme eles se movimentam, enquanto ainda expor orientação true do controlador, usando seus sensores de orientação interna.</span><span class="sxs-lookup"><span data-stu-id="1989f-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="1989f-209">Muitos aplicativos que usam controladores de apontar e ativar os elementos de interface do usuário podem operar normalmente enquanto estiver em precisão aproximado sem perceber o usuário.</span><span class="sxs-lookup"><span data-stu-id="1989f-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="1989f-210">A melhor maneira de ter uma noção do que isso é para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="1989f-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="1989f-211">Confira este vídeo com exemplos de conteúdo de imersão que funciona com os controladores de movimento em vários estados de controle:</span><span class="sxs-lookup"><span data-stu-id="1989f-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="1989f-212">Pensando sobre explicitamente o estado de controle</span><span class="sxs-lookup"><span data-stu-id="1989f-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="1989f-213">Aplicativos que deseja tratar as posições de maneira diferente com base no estado de controle podem ir além e inspecione as propriedades no estado do controlador, como *SourceLossRisk* e *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="1989f-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="1989f-214">Estado de controle</span><span class="sxs-lookup"><span data-stu-id="1989f-214">Tracking state</span></span> </th><th> <span data-ttu-id="1989f-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="1989f-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="1989f-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="1989f-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="1989f-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="1989f-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="1989f-218"><b>Alta precisão</b> </span><span class="sxs-lookup"><span data-stu-id="1989f-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="1989f-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="1989f-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="1989f-220">Alto</span><span class="sxs-lookup"><span data-stu-id="1989f-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="1989f-221">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="1989f-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-222"><b>Alta precisão (correm o risco de perda)</b> </span><span class="sxs-lookup"><span data-stu-id="1989f-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="1989f-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="1989f-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="1989f-224">Alto</span><span class="sxs-lookup"><span data-stu-id="1989f-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="1989f-225">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="1989f-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-226"><b>Precisão aproximado</b> </span><span class="sxs-lookup"><span data-stu-id="1989f-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="1989f-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="1989f-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="1989f-228">Aproximado</span><span class="sxs-lookup"><span data-stu-id="1989f-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="1989f-229">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="1989f-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1989f-230"><b>Nenhuma posição</b> </span><span class="sxs-lookup"><span data-stu-id="1989f-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="1989f-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="1989f-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="1989f-232">Aproximado</span><span class="sxs-lookup"><span data-stu-id="1989f-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="1989f-233">false</span><span class="sxs-lookup"><span data-stu-id="1989f-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="1989f-234">Esses estados de acompanhamento do movimento controlador são definidos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1989f-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="1989f-235">**Alta precisão:** Enquanto o controlador de animação estiver dentro do campo de visão do fone de ouvido, geralmente fornecerá posições de alta precisão, com base no acompanhamento visual.</span><span class="sxs-lookup"><span data-stu-id="1989f-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="1989f-236">Observe que um controlador de movimentação que momentaneamente deixa o campo de visualização ou obscurecida momentaneamente dos sensores fone de ouvido (por exemplo, por outro lado do usuário) continuarão a retornar apresenta alta precisão por um curto período, com base em controle inércia do controlador em si.</span><span class="sxs-lookup"><span data-stu-id="1989f-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="1989f-237">**Alta precisão (correm o risco de perda):** Quando o usuário move o controlador de animação além da borda da exibição de campo do fone de ouvido, o fone de ouvido em breve será possível rastrear visualmente a posição do controlador.</span><span class="sxs-lookup"><span data-stu-id="1989f-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="1989f-238">O aplicativo sabe quando o controlador atingiu esse limite FOV vendo os **SourceLossRisk** alcançar 1.0.</span><span class="sxs-lookup"><span data-stu-id="1989f-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="1989f-239">Nesse ponto, o aplicativo pode optar por pausar gestos de controlador que exigem um fluxo constante de poses de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="1989f-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="1989f-240">**Precisão aproximado:** Quando o controlador perdeu visual de acompanhamento de tempo suficiente, posições do controlador descartará a precisão aproximados posições.</span><span class="sxs-lookup"><span data-stu-id="1989f-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="1989f-241">Neste ponto, o sistema será o bloqueio de corpo de controlador para o controle do usuário, a posição do usuário conforme eles se movimentam, enquanto ainda expor orientação true do controlador, usando seus sensores de orientação interna.</span><span class="sxs-lookup"><span data-stu-id="1989f-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="1989f-242">Muitos aplicativos que usam controladores de apontar e ativar os elementos de interface do usuário podem funcionar como tempo normal em precisão aproximado sem perceber o usuário.</span><span class="sxs-lookup"><span data-stu-id="1989f-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="1989f-243">Aplicativos com requisitos de entrada pesados podem optar por sentido Essa queda da **alta** precisão **aproximado** precisão inspecionando o **PositionAccuracy** propriedade, para exemplo para dar ao usuário um hitbox mais amplas em destinos de fora da tela durante esse tempo.</span><span class="sxs-lookup"><span data-stu-id="1989f-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="1989f-244">**Nenhuma posição:** Enquanto o controlador pode operar em precisão aproximado por um longo tempo, às vezes, o sistema sabe que até mesmo uma posição bloqueada de corpo não é significativa no momento.</span><span class="sxs-lookup"><span data-stu-id="1989f-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="1989f-245">Por exemplo, um controlador que foi ativado apenas talvez nunca foram observado visualmente, ou um usuário pode colocar para baixo de um controlador que é capturado por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="1989f-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="1989f-246">Nesses momentos, o sistema não fornecerá qualquer posição para o aplicativo, e *TryGetPosition* retornará false.</span><span class="sxs-lookup"><span data-stu-id="1989f-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="1989f-247">APIs comuns do Unity (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="1989f-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="1989f-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="1989f-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="1989f-249">**Tipos de**: *Input*, *XR.InputTracking*</span><span class="sxs-lookup"><span data-stu-id="1989f-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="1989f-250">Atualmente, o Unity usa seu gerais *Input.GetButton/Input.GetAxis* APIs para expor a entrada para [o SDK do Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [SDK OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html) e realidade mista do Windows, incluindo mãos e controladores de movimento.</span><span class="sxs-lookup"><span data-stu-id="1989f-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="1989f-251">Se seu aplicativo usa essas APIs para entrada, ele pode facilmente dar suporte a controladores de movimento entre vários SDKs XR, incluindo Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1989f-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="1989f-252">Ao obter o estado pressionado de um botão lógica</span><span class="sxs-lookup"><span data-stu-id="1989f-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="1989f-253">Para usar as APIs de entrada Unity geral, normalmente comece por conectando botões e eixos para nomes lógicos na [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), associando um botão ou eixo IDs a cada nome.</span><span class="sxs-lookup"><span data-stu-id="1989f-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="1989f-254">Em seguida, você pode escrever código que se refere a esse nome lógico de botão/eixo.</span><span class="sxs-lookup"><span data-stu-id="1989f-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="1989f-255">Por exemplo, para mapear o botão de gatilho do controlador de movimento à esquerda para a ação de envio, vá para **Editar > configurações do projeto > entrada** dentro do Unity e expandir as propriedades na seção de envio em eixos.</span><span class="sxs-lookup"><span data-stu-id="1989f-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="1989f-256">Alterar o **botão positivo** ou **botão positivo de Alt** propriedade ler **botão joystick 14**, semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="1989f-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="1989f-257">![InputManager do Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="1989f-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="1989f-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="1989f-258">*Unity InputManager*</span></span>

<span data-ttu-id="1989f-259">Seu script, em seguida, pode verificar a ação de enviar usando *Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="1989f-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="1989f-260">Você pode adicionar botões mais lógica, alterando a **tamanho** propriedade sob **eixos**.</span><span class="sxs-lookup"><span data-stu-id="1989f-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="1989f-261">Obtendo o estado pressionado de um botão físico diretamente</span><span class="sxs-lookup"><span data-stu-id="1989f-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="1989f-262">Você também pode acessar botões manualmente por seus totalmente qualificado nome, usando *Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="1989f-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="1989f-263">Obtendo uma mão ou pose do controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="1989f-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="1989f-264">Você pode acessar a posição e rotação do controlador, usando *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="1989f-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="1989f-265">Observe que isso representa alça pose do controlador (em que o usuário mantém o controlador), que é útil para renderizar uma espada ou elétrons em mãos do usuário ou um modelo do controlador em si.</span><span class="sxs-lookup"><span data-stu-id="1989f-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="1989f-266">Observe que a relação entre essa pose alça e a pose de ponteiro (em que a dica do controlador está apontando) pode ser diferente em controladores.</span><span class="sxs-lookup"><span data-stu-id="1989f-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="1989f-267">No momento, só é possível por meio de entrada específicos MR API, descrito nas seções a seguir acessar pose do ponteiro do controlador.</span><span class="sxs-lookup"><span data-stu-id="1989f-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="1989f-268">APIs específicas do Windows (XR. WSA. Entrada)</span><span class="sxs-lookup"><span data-stu-id="1989f-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="1989f-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="1989f-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="1989f-270">**Tipos de**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="1989f-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="1989f-271">Para obter informações mais detalhadas sobre controladores de movimento e de entrada de mão de realidade mista do Windows (para HoloLens), você pode optar por usar as APIs de entrada espaciais específicos do Windows sob a *UnityEngine.XR.WSA.Input* namespace.</span><span class="sxs-lookup"><span data-stu-id="1989f-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="1989f-272">Isso lhe permite acessar informações adicionais, como precisão de posição ou o tipo de fonte, permitindo que você conte mãos e controladores separados.</span><span class="sxs-lookup"><span data-stu-id="1989f-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="1989f-273">Sondagem para o estado das mãos e controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="1989f-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="1989f-274">Você pode sondar para o estado desse quadro para cada fonte (manualmente ou movimento controlador) de interação usando o *GetCurrentReading* método.</span><span class="sxs-lookup"><span data-stu-id="1989f-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="1989f-275">Cada *InteractionSourceState* você obter back representa uma fonte de interação no momento atual no tempo.</span><span class="sxs-lookup"><span data-stu-id="1989f-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="1989f-276">O *InteractionSourceState* expõe informações como:</span><span class="sxs-lookup"><span data-stu-id="1989f-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="1989f-277">Qual [tipos de pressionamentos de](motion-controllers.md) estão ocorrendo (selecione/Menu/compreensão/Touchpad/direcional)</span><span class="sxs-lookup"><span data-stu-id="1989f-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="1989f-278">Outros dados específicos para controladores de movimento, tal o touchpad e/ou do direcional coordenadas XY e estado tocado</span><span class="sxs-lookup"><span data-stu-id="1989f-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="1989f-279">O InteractionSourceKind saber se a fonte é uma mão ou um controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="1989f-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="1989f-280">Sondagem para renderização prevista de avanço poses</span><span class="sxs-lookup"><span data-stu-id="1989f-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="1989f-281">Ao sondar dados de origem de interação de mãos e controladores, a apresenta a que você obter é poses prevista de encaminhamento para o ponto no tempo quando photons desse quadro serão chegar a atenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="1989f-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="1989f-282">Esses poses prevista de avanço são melhor usadas para **renderização** o controlador ou um mantido cada quadro do objeto.</span><span class="sxs-lookup"><span data-stu-id="1989f-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="1989f-283">Se você estiver direcionando um determinado pressionamento ou com o controlador de versão, que será mais preciso, se você usar as APIs descritas abaixo de eventos históricos.</span><span class="sxs-lookup"><span data-stu-id="1989f-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="1989f-284">Você também pode obter a pose principal prevista de encaminhamento para este quadro atual.</span><span class="sxs-lookup"><span data-stu-id="1989f-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="1989f-285">Como com a fonte pose, isso é útil para **renderização** um cursor, embora direcionado para uma determinada pressione ou versão sejam mais preciso, se você usar as APIs descritas abaixo de eventos históricos.</span><span class="sxs-lookup"><span data-stu-id="1989f-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="1989f-286">Manipulação de eventos de fonte de interação</span><span class="sxs-lookup"><span data-stu-id="1989f-286">Handling interaction source events</span></span>

<span data-ttu-id="1989f-287">Para lidar com eventos de entrada conforme acontecem com seus dados precisos pose históricos, você pode manipular eventos de fonte de interação, em vez de sondagem.</span><span class="sxs-lookup"><span data-stu-id="1989f-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="1989f-288">Para lidar com eventos de fonte de interação:</span><span class="sxs-lookup"><span data-stu-id="1989f-288">To handle interaction source events:</span></span>
* <span data-ttu-id="1989f-289">Registre-se para uma *InteractionManager* evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="1989f-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="1989f-290">Para cada tipo de evento de interação que você está interessado, você precisará assiná-lo.</span><span class="sxs-lookup"><span data-stu-id="1989f-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="1989f-291">Manipule o evento.</span><span class="sxs-lookup"><span data-stu-id="1989f-291">Handle the event.</span></span> <span data-ttu-id="1989f-292">Depois que você se inscreveu para um evento de interação, você obterá o retorno de chamada quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="1989f-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="1989f-293">No *SourcePressed* exemplo, este será depois que o código-fonte foi detectado e antes de ser liberado ou perdido.</span><span class="sxs-lookup"><span data-stu-id="1989f-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="1989f-294">Como parar manipulando um evento</span><span class="sxs-lookup"><span data-stu-id="1989f-294">How to stop handling an event</span></span>

<span data-ttu-id="1989f-295">Você precisa parar manipulando um evento quando você não estiver mais interessado no evento ou destruição de objeto que tiver assinado o evento.</span><span class="sxs-lookup"><span data-stu-id="1989f-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="1989f-296">Para interromper a manipulação do evento, você cancelar o evento.</span><span class="sxs-lookup"><span data-stu-id="1989f-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="1989f-297">Lista de eventos de fonte de interação</span><span class="sxs-lookup"><span data-stu-id="1989f-297">List of interaction source events</span></span>

<span data-ttu-id="1989f-298">Os eventos de origem de interação disponíveis são:</span><span class="sxs-lookup"><span data-stu-id="1989f-298">The available interaction source events are:</span></span>
* <span data-ttu-id="1989f-299">*InteractionSourceDetected* (código-fonte se torne ativa)</span><span class="sxs-lookup"><span data-stu-id="1989f-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="1989f-300">*InteractionSourceLost* (se torna inativo)</span><span class="sxs-lookup"><span data-stu-id="1989f-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="1989f-301">*InteractionSourcePressed* (toque, pressionar o botão ou "Select" proferidos)</span><span class="sxs-lookup"><span data-stu-id="1989f-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="1989f-302">*InteractionSourceReleased* (final de um toque, o botão foi liberado ou o fim do "Select" proferidos)</span><span class="sxs-lookup"><span data-stu-id="1989f-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="1989f-303">*InteractionSourceUpdated* (move ou caso contrário, altera algum estado)</span><span class="sxs-lookup"><span data-stu-id="1989f-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="1989f-304">Eventos para poses históricos de direcionamento que correspondem a um press ou uma versão com mais precisão</span><span class="sxs-lookup"><span data-stu-id="1989f-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="1989f-305">As APIs de sondagem descritas anteriormente dar ao seu aplicativo poses prevista de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="1989f-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="1989f-306">Enquanto essas poses previstas são melhores para o controlador ou um objeto mão virtual de renderização, poses futuros não são ideais para direcionamento por dois motivos principais:</span><span class="sxs-lookup"><span data-stu-id="1989f-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="1989f-307">Quando o usuário pressiona um botão em um controlador, pode haver aproximadamente 20 ms de latência sem fio via Bluetooth antes do sistema recebe o toque.</span><span class="sxs-lookup"><span data-stu-id="1989f-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="1989f-308">Em seguida, se você estiver usando uma pose prevista de encaminhamento, existe seria outro 20ms de 10 de encaminhamento previsão aplicada para direcionar o tempo quando photons do quadro atual serão chegar a atenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="1989f-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="1989f-309">Isso significa que sondagem lhe dá uma pose do código-fonte ou head representam o que é 30 40ms avanço de onde o usuário head e mãos, na verdade, estavam quando a versão ou pressione aconteceu.</span><span class="sxs-lookup"><span data-stu-id="1989f-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="1989f-310">Para a entrada de mão do HoloLens, embora não haja nenhum atraso de transmissão sem fio, há um atraso de processamento semelhante para detectar o toque.</span><span class="sxs-lookup"><span data-stu-id="1989f-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="1989f-311">Com precisão direcionar com base na intenção do usuário original para um pressionamento de mão ou controlador, você deve usar a fonte históricos pose ou pose principal de que *InteractionSourcePressed* ou *InteractionSourceReleased* eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="1989f-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="1989f-312">Você pode direcionar um pressionamento de ou liberar com dados de pose históricos de cabeça do usuário ou seu controlador:</span><span class="sxs-lookup"><span data-stu-id="1989f-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="1989f-313">A principal pose no momento no tempo quando um controlador ou um gesto de pressionar ocorreu, o que pode ser usado para **direcionamento** para determinar o que o usuário estava [Observação](gaze.md) em:</span><span class="sxs-lookup"><span data-stu-id="1989f-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

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

* <span data-ttu-id="1989f-314">Ocorreu a pose de origem no momento no tempo quando pressiona um controlador de animação, que pode ser usado para **direcionamento** para determinar o que o usuário estava apontando o controlador na.</span><span class="sxs-lookup"><span data-stu-id="1989f-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="1989f-315">Esse será o estado do controlador que apresentou a imprensa.</span><span class="sxs-lookup"><span data-stu-id="1989f-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="1989f-316">Se você estiver Renderizando o próprio controlador, você pode solicitar a pose de ponteiro em vez de pose a alça, para acertar o raio de direcionamento do que o usuário considerará a dica natural do que renderizado controlador:</span><span class="sxs-lookup"><span data-stu-id="1989f-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="1989f-317">Exemplo de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="1989f-317">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="1989f-318">Gesto de composição de alto nível APIs (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="1989f-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="1989f-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="1989f-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="1989f-320">**Tipos de**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="1989f-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="1989f-321">Seu aplicativo também pode reconhecer gestos de composição de nível superior para gestos de espera, navegação e manipulação de fontes de entrada espacial, toque.</span><span class="sxs-lookup"><span data-stu-id="1989f-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="1989f-322">Você pode reconhecer esses gestos compostos entre ambos [mãos](gestures.md) e [controladores de movimento](motion-controllers.md) usando o GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="1989f-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="1989f-323">Cada evento de gesto no GestureRecognizer fornece o SourceKind para a entrada, bem como o raio de cabeçalho de direcionamento no momento do evento.</span><span class="sxs-lookup"><span data-stu-id="1989f-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="1989f-324">Alguns eventos fornecem informações específicas de contexto adicionais.</span><span class="sxs-lookup"><span data-stu-id="1989f-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="1989f-325">Há apenas algumas etapas necessárias para capturar os gestos usando um reconhecedor de gestos:</span><span class="sxs-lookup"><span data-stu-id="1989f-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="1989f-326">Criar um novo reconhecedor de gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="1989f-327">Especifique quais gestos para inspecionar</span><span class="sxs-lookup"><span data-stu-id="1989f-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="1989f-328">Inscrever-se em eventos para esses gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="1989f-329">Iniciar a captura de gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="1989f-330">Criar um novo reconhecedor de gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="1989f-331">Para usar o *GestureRecognizer*, você deve ter criado uma *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="1989f-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="1989f-332">Especifique quais gestos para inspecionar</span><span class="sxs-lookup"><span data-stu-id="1989f-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="1989f-333">Especifique quais gestos, você está interessado via *SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="1989f-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="1989f-334">Inscrever-se em eventos para esses gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="1989f-335">Assine eventos para os gestos que você está interessado.</span><span class="sxs-lookup"><span data-stu-id="1989f-335">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="1989f-336">Gestos de navegação e manipulação são mutuamente exclusivos em uma instância de um *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="1989f-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="1989f-337">Iniciar a captura de gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-337">Start capturing gestures</span></span>

<span data-ttu-id="1989f-338">Por padrão, uma *GestureRecognizer* não monitora o processo de entrada até *StartCapturingGestures()* é chamado.</span><span class="sxs-lookup"><span data-stu-id="1989f-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="1989f-339">É possível que um evento de gesto pode ser gerado após *StopCapturingGestures()* é chamado se a entrada foi realizada antes do quadro no qual *StopCapturingGestures()* foi processada.</span><span class="sxs-lookup"><span data-stu-id="1989f-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="1989f-340">O *GestureRecognizer* irão se lembrar se ela foi ativada ou desativada durante o quadro previou no qual o gesto realmente ocorreu e então é confiável para iniciar e parar monitoramento de gesto baseado no olhar desse quadro direcionamento.</span><span class="sxs-lookup"><span data-stu-id="1989f-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="1989f-341">Parar a captura de gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-341">Stop capturing gestures</span></span>

<span data-ttu-id="1989f-342">Para interromper o reconhecimento de gesto:</span><span class="sxs-lookup"><span data-stu-id="1989f-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="1989f-343">Removendo um reconhecedor de gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="1989f-344">Lembre-se de cancelar a assinatura de eventos assinados antes de destruir uma *GestureRecognizer* objeto.</span><span class="sxs-lookup"><span data-stu-id="1989f-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="1989f-345">Renderizando o modelo de controlador de animação no Unity</span><span class="sxs-lookup"><span data-stu-id="1989f-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="1989f-346">![Teleportation e modelo do controlador de movimento](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="1989f-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="1989f-347">*Teleportation e modelo do controlador de movimento*</span><span class="sxs-lookup"><span data-stu-id="1989f-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="1989f-348">Para renderizar os controladores de movimento em seu aplicativo que correspondem aos controladores de física, seus usuários estão mantendo e articulam como vários botões são pressionados, você pode usar o **MotionController pré-fabricado** no [Kit de ferramentas de realidade mista ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="1989f-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="1989f-349">Este pré-fabricado dinamicamente carrega o modelo de glTF correto em tempo de execução do driver de controlador de movimento instalado do sistema.</span><span class="sxs-lookup"><span data-stu-id="1989f-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="1989f-350">É importante carregar esses modelos dinamicamente em vez de importá-los manualmente no editor, para que seu aplicativo Mostrar modelos 3D fisicamente precisos para quaisquer controladores atuais e futuras de seus usuários pode ter.</span><span class="sxs-lookup"><span data-stu-id="1989f-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="1989f-351">Siga as [guia de Introdução](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instruções para baixar o Kit de ferramentas de realidade mista e adicioná-lo ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="1989f-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="1989f-352">Se você substituiu a câmera com a *MixedRealityCameraParent* pré-fabricado como parte das etapas de Introdução, você está pronto para começar!</span><span class="sxs-lookup"><span data-stu-id="1989f-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="1989f-353">Esse pré-fabricado inclui a renderização de controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="1989f-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="1989f-354">Caso contrário, adicione *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* na sua cena do painel de projeto.</span><span class="sxs-lookup"><span data-stu-id="1989f-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="1989f-355">Você desejará adicionar pré-fabricado como um filho de qualquer objeto pai usar para mover a câmera ao redor quando teleports o usuário dentro de sua cena, para que os controladores vêm junto com o usuário.</span><span class="sxs-lookup"><span data-stu-id="1989f-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="1989f-356">Se seu aplicativo envolve teleporting, basta adicione pré-fabricado na raiz da sua cena.</span><span class="sxs-lookup"><span data-stu-id="1989f-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="1989f-357">Gerando objetos</span><span class="sxs-lookup"><span data-stu-id="1989f-357">Throwing objects</span></span>

<span data-ttu-id="1989f-358">Lançamento de objetos em realidade virtual é um problema mais difícil, em seguida, ele pode primeiramente parecer.</span><span class="sxs-lookup"><span data-stu-id="1989f-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="1989f-359">Assim como acontece com interações mais fisicamente com base, ao lançar no jogo atua de forma inesperada, ela é imediatamente óbvia e quebras de imersão.</span><span class="sxs-lookup"><span data-stu-id="1989f-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="1989f-360">Passamos algum tempo pensando profundamente como representar um comportamento gerando fisicamente correto e surgir com algumas diretrizes, habilitadas por meio de atualizações para nossa plataforma, que gostaríamos de compartilhar com você.</span><span class="sxs-lookup"><span data-stu-id="1989f-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="1989f-361">Você pode encontrar um exemplo de como é recomendável implementar lançando [aqui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="1989f-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="1989f-362">Este exemplo segue essas quatro diretrizes:</span><span class="sxs-lookup"><span data-stu-id="1989f-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="1989f-363">**Usar o controlador *velocity* em vez de posição**.</span><span class="sxs-lookup"><span data-stu-id="1989f-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="1989f-364">A atualização de novembro para Windows, apresentamos uma alteração no comportamento quando estiver na [' aproximar ' o estado do acompanhamento posicionais](motion-controllers.md#controller-tracking-state).</span><span class="sxs-lookup"><span data-stu-id="1989f-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="1989f-365">Quando nesse estado, informações de velocidade sobre o controlador continuará a ser relatado para desde que acreditamos que é alta precisão, que é geralmente mais do que a posição permanecerá alta precisão.</span><span class="sxs-lookup"><span data-stu-id="1989f-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="1989f-366">**Incorporar o *velocidade angular* do controlador**.</span><span class="sxs-lookup"><span data-stu-id="1989f-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="1989f-367">Essa lógica está contida na `throwing.cs` arquivo o `GetThrownObjectVelAngVel` método estático, dentro do pacote no link acima:</span><span class="sxs-lookup"><span data-stu-id="1989f-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="1989f-368">Como a velocidade angular é conservada, o objeto gerado deve manter a mesma velocidade angular como ela tinha no momento do lançamento: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="1989f-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="1989f-369">Como a centro de massa do objeto gerado provavelmente que não na origem do pose a alça, provavelmente ele tem uma velocidade diferente e depois o do controlador no quadro de referência do usuário.</span><span class="sxs-lookup"><span data-stu-id="1989f-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="1989f-370">A parte da velocidade do objeto contribuída dessa maneira é a velocidade de tangenciais instantânea da Centro de massa do objeto lançada em torno da origem do controlador.</span><span class="sxs-lookup"><span data-stu-id="1989f-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="1989f-371">Essa velocidade tangenciais é o produto cruzado da velocidade angular do controlador com o vetor que representa a distância entre a origem do controlador e a centro de massa do objeto gerado.</span><span class="sxs-lookup"><span data-stu-id="1989f-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="1989f-372">A velocidade total do objeto lançada, portanto, é a soma da velocidade do controlador e essa velocidade tangenciais: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="1989f-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="1989f-373">**Preste muita atenção para o *tempo* em que podemos aplicar a velocidade**.</span><span class="sxs-lookup"><span data-stu-id="1989f-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="1989f-374">Quando um botão é pressionado, pode levar até 20 ms para o evento de emergirem Bluetooth para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="1989f-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="1989f-375">Isso significa que, se você sondagem de uma alteração de estado do controlador de pressionado não pressionado ou vice-versa, as informações do controlador pose que obter com ele, na verdade, estará à frente dessa alteração no estado.</span><span class="sxs-lookup"><span data-stu-id="1989f-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="1989f-376">Além disso, a pose controlador apresentada por nossa API de sondagem para frente é prevista para refletir uma probabilidade pose ao tempo que poderia ser mais 20ms, em seguida, no futuro o quadro será exibido.</span><span class="sxs-lookup"><span data-stu-id="1989f-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="1989f-377">Isso é bom para *renderização* mantidos objetos, mas aumenta ainda mais o nosso problema de tempo para *direcionamento* o objeto conforme calculamos a trajetória para o momento em que o usuário soltou seu throw.</span><span class="sxs-lookup"><span data-stu-id="1989f-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="1989f-378">Felizmente, com a atualização de novembro, quando um evento do Unity, como *InteractionSourcePressed* ou *InteractionSourceReleased* é enviada, o estado inclui os dados históricos pose de novamente quando o botão era, na verdade, pressionado ou liberado.</span><span class="sxs-lookup"><span data-stu-id="1989f-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="1989f-379">Para obter a renderização mais precisa do controlador e o direcionamento de controlador durante gera, você deve usar corretamente uma sondagem e eventos, conforme apropriado:</span><span class="sxs-lookup"><span data-stu-id="1989f-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="1989f-380">Para **renderização de controlador** cada quadro, seu aplicativo deve posicionar o controlador *GameObject* no controlador prevista de avanço representar para o tempo de photon do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="1989f-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="1989f-381">Você obtém esses dados do Unity, como APIs de sondagem *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* ou  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="1989f-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="1989f-382">Para **direcionamento de controlador** após um press ou versão, seu aplicativo deve raycast e calcular trajetórias com base em pose os históricos de controlador para o evento pressione ou versão.</span><span class="sxs-lookup"><span data-stu-id="1989f-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="1989f-383">Obter esses dados de eventos do Unity APIs, como  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="1989f-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="1989f-384">**Use a alça pose**.</span><span class="sxs-lookup"><span data-stu-id="1989f-384">**Use the grip pose**.</span></span> <span data-ttu-id="1989f-385">Velocidade angular e a velocidade são relatados em relação a pose alça, não pose de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="1989f-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="1989f-386">Lançando continuará a melhorar com as atualizações futuras do Windows, e você pode esperar encontrar mais informações sobre ele aqui.</span><span class="sxs-lookup"><span data-stu-id="1989f-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="1989f-387">Acelere o desenvolvimento com o Kit de ferramentas de realidade mista</span><span class="sxs-lookup"><span data-stu-id="1989f-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="1989f-388">Há duas cenas de exemplo sobre InputManager e MotionController no Unity.</span><span class="sxs-lookup"><span data-stu-id="1989f-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="1989f-389">Por meio desses cenas, você pode aprender como usar InputManager do MRTK e acessar dados tratar eventos dentre os botões do controlador de animação.</span><span class="sxs-lookup"><span data-stu-id="1989f-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="1989f-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="1989f-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="1989f-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="1989f-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="1989f-392">Detalhes técnicos arquivo Leiame</span><span class="sxs-lookup"><span data-stu-id="1989f-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="1989f-393">![Exemplo de entrada cenas no MRTK](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="1989f-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="1989f-394">*Exemplo de entrada cenas no MRTK*</span><span class="sxs-lookup"><span data-stu-id="1989f-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="1989f-395">Instalação automática de cena</span><span class="sxs-lookup"><span data-stu-id="1989f-395">Automatic scene setup</span></span>

<span data-ttu-id="1989f-396">Quando você importa [MRTK liberar pacotes do Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) ou clonar o projeto a partir o [repositório GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), você vai encontrar um novo menu 'Toolkit de realidade mista' no Unity.</span><span class="sxs-lookup"><span data-stu-id="1989f-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="1989f-397">No menu 'Configurar', você verá o menu 'Aplicar misto realidade cena configurações'.</span><span class="sxs-lookup"><span data-stu-id="1989f-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="1989f-398">Quando você clica nele, ele remove a câmera padrão e adiciona os componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="1989f-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="1989f-399">![Menu MRTK para a instalação de cena](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="1989f-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="1989f-400">*Menu MRTK para a instalação de cena*</span><span class="sxs-lookup"><span data-stu-id="1989f-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="1989f-401">![Instalação automática de cena no MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="1989f-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="1989f-402">*Instalação automática de cena no MRTK*</span><span class="sxs-lookup"><span data-stu-id="1989f-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="1989f-403">MixedRealityCamera pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="1989f-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="1989f-404">Você também pode adicionar manualmente esses do painel de projeto.</span><span class="sxs-lookup"><span data-stu-id="1989f-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="1989f-405">Você pode encontrar esses componentes como pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="1989f-405">You can find these components as prefabs.</span></span> <span data-ttu-id="1989f-406">Quando você procura **MixedRealityCamera**, você poderá ver duas pré-fabricados de câmera diferente.</span><span class="sxs-lookup"><span data-stu-id="1989f-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="1989f-407">A diferença é que **MixedRealityCamera** é a câmera apenas pré-fabricado enquanto que o **MixedRealityCameraParent** inclui componentes adicionais para os fones imersivos em exposição como Teleportation, movimento Controlador e, limite.</span><span class="sxs-lookup"><span data-stu-id="1989f-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="1989f-408">![Pré-fabricados de câmera em MRTK](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="1989f-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="1989f-409">*Pré-fabricados de câmera em MRTK*</span><span class="sxs-lookup"><span data-stu-id="1989f-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="1989f-410">**MixedRealtyCamera** dá suporte ao HoloLens e envolvente fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="1989f-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="1989f-411">Ele detecta o tipo de dispositivo e otimiza as propriedades como sinalizadores claras e Skybox.</span><span class="sxs-lookup"><span data-stu-id="1989f-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="1989f-412">Abaixo você encontrará algumas das propriedades úteis que você pode personalizar como o Cursor personalizado, modelos de controlador de movimento e Floor.</span><span class="sxs-lookup"><span data-stu-id="1989f-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="1989f-413">![Propriedades para o controlador de movimento, Cursor e Floor](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="1989f-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="1989f-414">*Propriedades para o controlador de movimento, Cursor e Floor*</span><span class="sxs-lookup"><span data-stu-id="1989f-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="1989f-415">Siga tutoriais</span><span class="sxs-lookup"><span data-stu-id="1989f-415">Follow along with tutorials</span></span>

<span data-ttu-id="1989f-416">Tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis na academia de realidade mista:</span><span class="sxs-lookup"><span data-stu-id="1989f-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="1989f-417">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="1989f-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="1989f-418">Entrada MR 213: Controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="1989f-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="1989f-419">[![Entrada de MR 213 - controlador de movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="1989f-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="1989f-420">*Entrada de MR 213 - controlador de movimento*</span><span class="sxs-lookup"><span data-stu-id="1989f-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="1989f-421">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1989f-421">See also</span></span>

* [<span data-ttu-id="1989f-422">Gestos</span><span class="sxs-lookup"><span data-stu-id="1989f-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="1989f-423">Controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="1989f-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="1989f-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="1989f-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="1989f-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="1989f-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="1989f-426">InteractionInputSource.cs no Unity MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1989f-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)

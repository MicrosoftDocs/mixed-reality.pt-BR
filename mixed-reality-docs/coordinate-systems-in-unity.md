---
title: Sistemas de coordenadas no Unity
description: Aprenda a criar sentado, aguardando, sala de escala e dimensionamento do mundo misturadas realidade experiências no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espacial, somente orientação, encaixado em escala, escala de pé, sala de escala, escala mundial, 360 graus, encaixado, permanente, sala, mundo, escala, posição, orientação, Unity, âncora, âncora espacial, âncora do mundo, mundo bloqueado, bloqueio de mundo, corpo bloqueado, corpo bloqueio, perda, locatability, limites, centralizar novamente de acompanhamento
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591010"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="d603f-104">Sistemas de coordenadas no Unity</span><span class="sxs-lookup"><span data-stu-id="d603f-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="d603f-105">Realidade mista do Windows dá suporte a aplicativos em uma ampla variedade de [experiência escalas](coordinate-systems.md), dos aplicativos apenas orientação e escala encaixado backup por meio de aplicativos de escala de sala.</span><span class="sxs-lookup"><span data-stu-id="d603f-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="d603f-106">Em HoloLens, você pode ir além e compilar aplicativos de escala mundial que permitem aos usuários percorrer além dos 5 metros, explorando um andar inteiro de um edifício e muito mais.</span><span class="sxs-lookup"><span data-stu-id="d603f-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="d603f-107">A primeira etapa na criação de uma experiência de realidade misturada no Unity é determinar quais [experiência escala](coordinate-systems.md) seu aplicativo se destinará.</span><span class="sxs-lookup"><span data-stu-id="d603f-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="d603f-108">Criação de uma experiência somente orientação ou encaixado em escala</span><span class="sxs-lookup"><span data-stu-id="d603f-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="d603f-109">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="d603f-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="d603f-110">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="d603f-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="d603f-111">Para criar uma **somente orientação** ou **escala encaixado experiência**, você deve definir Unity como o papel de carta acompanhamento do tipo de espaço.</span><span class="sxs-lookup"><span data-stu-id="d603f-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="d603f-112">Isso define o sistema de coordenadas de mundo do Unity para acompanhar as [quadro estacionário de referência](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="d603f-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="d603f-113">No modo de acompanhamento parado, o conteúdo é colocado no editor de apenas na frente do local de padrão da câmera (para frente é -Z) será exibido na frente do usuário quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="d603f-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="d603f-114">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="d603f-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="d603f-115">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="d603f-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="d603f-116">Para um puro **experiência somente orientação** como um visualizador de vídeo de 360 graus (onde posicionais atualizações principais seriam arruinando a ilusão), em seguida, você pode definir [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) como true:</span><span class="sxs-lookup"><span data-stu-id="d603f-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="d603f-117">Para um **experiência de escala encaixado**, para permitir que o usuário mais tarde centralizar novamente a origem sentada, você pode chamar o [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) método:</span><span class="sxs-lookup"><span data-stu-id="d603f-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="d603f-118">Criar uma experiência de escala permanente ou de escala de espaço</span><span class="sxs-lookup"><span data-stu-id="d603f-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="d603f-119">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="d603f-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="d603f-120">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="d603f-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="d603f-121">Para um **escala permanente** ou **experiência sala escala**, você precisará colocar o conteúdo em relação ao chão.</span><span class="sxs-lookup"><span data-stu-id="d603f-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="d603f-122">Justificar o usuário floor usando o  **[estágio espacial](coordinate-systems.md#spatial-coordinate-systems)**, que representa o usuário definidas origem do nível do chão e limite de espaço opcional, definido durante a primeira execução.</span><span class="sxs-lookup"><span data-stu-id="d603f-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="d603f-123">Para garantir que o Unity está operando com seu sistema de coordenadas de mundo no nível do chão, você pode definir o Unity para o acompanhamento do tipo de espaço de RoomScale e certifique-se de que o conjunto tenha êxito:</span><span class="sxs-lookup"><span data-stu-id="d603f-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="d603f-124">Se SetTrackingSpaceType retornar true, o Unity alternou com êxito seu sistema de coordenadas de mundo para acompanhar as [estágio quadro de referência](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="d603f-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="d603f-125">Se SetTrackingSpaceType retornar false, o Unity pôde alternar para o estágio quadro de referência, provavelmente porque o usuário não tiver configurado até mesmo um piso em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="d603f-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="d603f-126">Isso não é comum, mas pode acontecer se o estágio foi configurado em um local diferente e o dispositivo foi movido para a sala atual sem a configuração de usuário do backup de um novo estágio.</span><span class="sxs-lookup"><span data-stu-id="d603f-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="d603f-127">Depois que seu aplicativo com êxito define o RoomScale espaço tipo de controle, conteúdo colocado y = 0 plano aparecerá no chão.</span><span class="sxs-lookup"><span data-stu-id="d603f-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="d603f-128">A origem (0, 0, 0) será o local específico no chão de onde o usuário resistiu durante a instalação da sala, com a -Z que representa a direção de avançada que estavam enfrentando durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="d603f-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="d603f-129">**Namespace:** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="d603f-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="d603f-130">**Tipo:** *Limite*</span><span class="sxs-lookup"><span data-stu-id="d603f-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="d603f-131">No código de script, você pode, em seguida, chame o método TryGetGeometry você é do tipo de UnityEngine.Experimental.XR.Boundary para obter um polígono do limite, especificando um tipo de limite de TrackedArea.</span><span class="sxs-lookup"><span data-stu-id="d603f-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="d603f-132">Se o usuário definido um limite (você obter uma lista de vértices), você sabe que é seguro fornecer um **experiência de escala de sala** para o usuário, onde eles podem orientá-lo ao redor do cenário criar.</span><span class="sxs-lookup"><span data-stu-id="d603f-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="d603f-133">Observe que o sistema automaticamente renderizará o limite quando o usuário se aproxima dela.</span><span class="sxs-lookup"><span data-stu-id="d603f-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="d603f-134">Seu aplicativo não precisa usar este polígono para renderizar o limite em si.</span><span class="sxs-lookup"><span data-stu-id="d603f-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="d603f-135">No entanto, você pode optar por dispor os objetos de cena usando este polígono do limite, para garantir que o usuário fisicamente pode atingir esses objetos sem teleporting:</span><span class="sxs-lookup"><span data-stu-id="d603f-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="d603f-136">Criar uma experiência de dimensionamento do mundo</span><span class="sxs-lookup"><span data-stu-id="d603f-136">Building a world-scale experience</span></span>

<span data-ttu-id="d603f-137">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="d603f-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="d603f-138">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="d603f-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="d603f-139">Para verdadeiro **experiências do mundo em escala** em HoloLens que permitem aos usuários percorrer além dos medidores de 5, você precisará de novas técnicas além daquelas usadas para experiências de sala em escala.</span><span class="sxs-lookup"><span data-stu-id="d603f-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="d603f-140">Uma técnica chave que você usará é criar uma [âncora espacial](coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente em vigor no mundo físico, independentemente do quanto o usuário tem de roaming e, em seguida, [encontrar esses hologramas novamente em mais tarde sessões](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="d603f-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="d603f-141">No Unity, você cria uma âncora espacial, adicionando a **WorldAnchor** componente do Unity para um GameObject.</span><span class="sxs-lookup"><span data-stu-id="d603f-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="d603f-142">Adicionando uma âncora de mundo</span><span class="sxs-lookup"><span data-stu-id="d603f-142">Adding a World Anchor</span></span>

<span data-ttu-id="d603f-143">Para adicionar uma âncora de mundo, chame AddComponent<WorldAnchor>() no objeto do jogo com a transformação que você deseja ancorar no mundo real.</span><span class="sxs-lookup"><span data-stu-id="d603f-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="d603f-144">É só isso!</span><span class="sxs-lookup"><span data-stu-id="d603f-144">That's it!</span></span> <span data-ttu-id="d603f-145">Esse objeto do jogo agora será ancorado seu local atual no mundo físico – você poderá ver suas coordenadas de mundo Unity ajustar um pouco ao longo do tempo para garantir que o alinhamento físico.</span><span class="sxs-lookup"><span data-stu-id="d603f-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="d603f-146">Use [persistência](persistence-in-unity.md) para encontrá-la ancorada local novamente em uma sessão de aplicativo futuras.</span><span class="sxs-lookup"><span data-stu-id="d603f-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="d603f-147">Removendo uma âncora de mundo</span><span class="sxs-lookup"><span data-stu-id="d603f-147">Removing a World Anchor</span></span>

<span data-ttu-id="d603f-148">Se não desejar que o GameObject bloqueada para um local do mundo físico e não pretende movê-lo neste quadro, em seguida, você pode simplesmente chamar Destroy no componente de âncora do mundo.</span><span class="sxs-lookup"><span data-stu-id="d603f-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="d603f-149">Se você quiser mover o GameObject este quadro, você precisará chamar DestroyImmediate em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d603f-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="d603f-150">Mover um mundo ancorado GameObject</span><span class="sxs-lookup"><span data-stu-id="d603f-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="d603f-151">Não pode ser movido do GameObject, enquanto uma âncora de mundo está nele.</span><span class="sxs-lookup"><span data-stu-id="d603f-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="d603f-152">Se você precisar mover o GameObject este quadro, você precisa:</span><span class="sxs-lookup"><span data-stu-id="d603f-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="d603f-153">DestroyImmediate o componente de âncora do mundo</span><span class="sxs-lookup"><span data-stu-id="d603f-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="d603f-154">Mover o GameObject</span><span class="sxs-lookup"><span data-stu-id="d603f-154">Move the GameObject</span></span>
3. <span data-ttu-id="d603f-155">Adicione um novo componente de âncora do mundo para o GameObject.</span><span class="sxs-lookup"><span data-stu-id="d603f-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="d603f-156">Tratando alterações Locatability</span><span class="sxs-lookup"><span data-stu-id="d603f-156">Handling Locatability Changes</span></span>

<span data-ttu-id="d603f-157">Um WorldAnchor pode não ser localizáveis no mundo físico em um ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="d603f-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="d603f-158">Se isso ocorrer, Unity não atualizará a transformação do objeto ancorado.</span><span class="sxs-lookup"><span data-stu-id="d603f-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="d603f-159">Isso também pode alterar enquanto um aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="d603f-159">This also can change while an app is running.</span></span> <span data-ttu-id="d603f-160">Falha em lidar com a alteração no locatability fará com que o objeto não apareça no local físico correto no mundo.</span><span class="sxs-lookup"><span data-stu-id="d603f-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="d603f-161">Para ser notificado sobre alterações de locatability:</span><span class="sxs-lookup"><span data-stu-id="d603f-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="d603f-162">Assinar o evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="d603f-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="d603f-163">Manipular o evento</span><span class="sxs-lookup"><span data-stu-id="d603f-163">Handle the event</span></span>

<span data-ttu-id="d603f-164">O **OnTrackingChanged** evento será chamado sempre que a âncora espacial subjacente é alterado entre um estado de ser localizáveis versus não sendo localizáveis.</span><span class="sxs-lookup"><span data-stu-id="d603f-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="d603f-165">Em seguida, manipule o evento:</span><span class="sxs-lookup"><span data-stu-id="d603f-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="d603f-166">Às vezes, as âncoras estão localizadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="d603f-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="d603f-167">Nesse caso, essa propriedade isLocated da âncora será definida como true quando AddComponent<WorldAnchor>() retorna.</span><span class="sxs-lookup"><span data-stu-id="d603f-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="d603f-168">Como resultado, o evento OnTrackingChanged não será disparado.</span><span class="sxs-lookup"><span data-stu-id="d603f-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="d603f-169">Um padrão de limpar seria chamar seu manipulador OnTrackingChanged com o estado inicial do IsLocated depois de anexar uma âncora.</span><span class="sxs-lookup"><span data-stu-id="d603f-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="d603f-170">Compartilhando as âncoras entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="d603f-170">Sharing anchors across devices</span></span>

<span data-ttu-id="d603f-171">Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para criar uma âncora de nuvem durável de um local WorldAnchor, o que seu aplicativo pode, em seguida, localizar em vários HoloLens, dispositivos iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="d603f-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="d603f-172">Compartilhando uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="d603f-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="d603f-173">Isso permite experiências compartilhadas em tempo real.</span><span class="sxs-lookup"><span data-stu-id="d603f-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="d603f-174">Para começar a criação de experiências compartilhadas no Unity, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guias de início rápido do Azure espacial âncoras Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="d603f-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="d603f-175">Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar as âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="d603f-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="d603f-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d603f-176">See Also</span></span>
* [<span data-ttu-id="d603f-177">Escalas de experiência</span><span class="sxs-lookup"><span data-stu-id="d603f-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="d603f-178">Estágio espacial</span><span class="sxs-lookup"><span data-stu-id="d603f-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="d603f-179">Controlando a perda no Unity</span><span class="sxs-lookup"><span data-stu-id="d603f-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="d603f-180">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="d603f-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="d603f-181">Persistência no Unity</span><span class="sxs-lookup"><span data-stu-id="d603f-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="d603f-182">Experiências compartilhadas no Unity</span><span class="sxs-lookup"><span data-stu-id="d603f-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="d603f-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="d603f-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="d603f-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Âncoras espaciais do Azure SDK para Unity</a></span><span class="sxs-lookup"><span data-stu-id="d603f-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
---
title: Coordenar sistemas no Unity
description: Saiba como criar experiências de realidade misturada, em posição de sala e em escala mundial no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciais, somente orientação, escala em posição, escala de pé, escala de sala, escala mundial, 360 graus, encaixado, posicionado, sala, mundo, escala, posição, orientação, Unity, âncora, âncora espacial, âncora mundial, bloqueado pelo mundo, World-Lock, corpo bloqueado, bloqueio de corpo, perda de rastreamento, locatability, limites, recentralizar
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375763"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="b627e-104">Coordenar sistemas no Unity</span><span class="sxs-lookup"><span data-stu-id="b627e-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="b627e-105">O Windows Mixed Reality dá suporte a aplicativos em uma ampla variedade de [escalas de experiência](coordinate-systems.md), desde aplicativos de dimensionamento e de orientação e escalados até aplicativos em escala de sala.</span><span class="sxs-lookup"><span data-stu-id="b627e-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="b627e-106">No HoloLens, você pode ir além e criar aplicativos de escala mundial que permitem que os usuários passem além de 5 metros, explorando um andar inteiro de um edifício e além disso.</span><span class="sxs-lookup"><span data-stu-id="b627e-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="b627e-107">Sua primeira etapa na criação de uma experiência de realidade mista no Unity é determinar qual [escala de experiência](coordinate-systems.md) seu aplicativo será direcionada.</span><span class="sxs-lookup"><span data-stu-id="b627e-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="b627e-108">Criando uma experiência somente de orientação ou de escala assentada</span><span class="sxs-lookup"><span data-stu-id="b627e-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="b627e-109">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b627e-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b627e-110">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="b627e-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="b627e-111">Para criar uma experiência **somente de orientação** ou **de escala colocada**, você deve definir o Unity para o tipo de espaço de rastreamento estacionário.</span><span class="sxs-lookup"><span data-stu-id="b627e-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="b627e-112">Isso define o sistema de coordenadas mundiais do Unity para acompanhar o [quadro estacionário de referência](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="b627e-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="b627e-113">No modo de rastreamento estacionário, o conteúdo colocado no editor apenas na frente do local padrão da câmera (Forward is-Z) aparecerá na frente do usuário quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="b627e-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="b627e-114">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b627e-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b627e-115">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="b627e-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="b627e-116">Para uma **experiência pura somente de orientação** , como um visualizador de vídeo de 360 graus (em que as atualizações de cabeça posicional poderiam arruinar a ilusão), você pode então definir a [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) para true:</span><span class="sxs-lookup"><span data-stu-id="b627e-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="b627e-117">Para uma **experiência em escala**, para permitir que o usuário recentralize a origem encaixada novamente, você pode chamar a [XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="b627e-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="b627e-118">Criando uma experiência em escala ou em escala de sala</span><span class="sxs-lookup"><span data-stu-id="b627e-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="b627e-119">**Namespace:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b627e-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b627e-120">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="b627e-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="b627e-121">Para uma experiência **de escala de** colocação ou de escala de **espaço**, você precisará colocar o conteúdo em relação ao andar.</span><span class="sxs-lookup"><span data-stu-id="b627e-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="b627e-122">Você se deparar com o andar do usuário usando o **[estágio espacial](coordinate-systems.md#spatial-coordinate-systems)** , que representa a origem definida do nível de chão do usuário e o limite de sala opcional, configurado durante a primeira execução.</span><span class="sxs-lookup"><span data-stu-id="b627e-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="b627e-123">Para garantir que o Unity esteja operando com seu sistema de coordenadas mundiais no nível do andar, você pode definir o Unity para o tipo de espaço de rastreamento RoomScale e garantir que o conjunto tenha sucesso:</span><span class="sxs-lookup"><span data-stu-id="b627e-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="b627e-124">Se SetTrackingSpaceType retornar true, o Unity alternará com êxito seu sistema de coordenadas mundiaI para acompanhar o [quadro de referência de estágio](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="b627e-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="b627e-125">Se SetTrackingSpaceType retornar false, o Unity não poderá alternar para o quadro de referência de estágio, provavelmente porque o usuário não configurou até mesmo um andar em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="b627e-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="b627e-126">Isso não é comum, mas pode acontecer se o estágio foi configurado em uma sala diferente e o dispositivo foi movido para o espaço atual sem que o usuário configure um novo estágio.</span><span class="sxs-lookup"><span data-stu-id="b627e-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="b627e-127">Depois que o aplicativo definir o tipo de espaço de acompanhamento RoomScale com êxito, o conteúdo colocado no plano y = 0 aparecerá no chão.</span><span class="sxs-lookup"><span data-stu-id="b627e-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="b627e-128">A origem em (0, 0) será o local específico no andar em que o usuário se baseou durante a configuração da sala, com-Z representando a direção de encaminhamento que ele estava enfrentando durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="b627e-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="b627e-129">**Namespace:** *UnityEngine. experimental. XR*</span><span class="sxs-lookup"><span data-stu-id="b627e-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="b627e-130">**Tipo:** *limite*</span><span class="sxs-lookup"><span data-stu-id="b627e-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="b627e-131">No código de script, você pode chamar o método TryGetGeometry em você é o tipo UnityEngine. experimental. XR. limite para obter um polígono de limite, especificando um tipo de limite de TrackedArea.</span><span class="sxs-lookup"><span data-stu-id="b627e-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="b627e-132">Se o usuário definiu um limite (você obtém uma lista de vértices), sabe que é seguro fornecer uma **experiência de escala de sala** ao usuário, onde eles podem percorrer a cena que você criar.</span><span class="sxs-lookup"><span data-stu-id="b627e-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="b627e-133">Observe que o sistema renderizará automaticamente o limite quando o usuário o aproximar.</span><span class="sxs-lookup"><span data-stu-id="b627e-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="b627e-134">Seu aplicativo não precisa usar este polígono para renderizar o limite em si.</span><span class="sxs-lookup"><span data-stu-id="b627e-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="b627e-135">No entanto, você pode optar por definir o layout de seus objetos de cena usando esse polígono de limite, para garantir que o usuário possa alcançar fisicamente esses objetos sem teleportação:</span><span class="sxs-lookup"><span data-stu-id="b627e-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="b627e-136">Criando uma experiência de escala mundial</span><span class="sxs-lookup"><span data-stu-id="b627e-136">Building a world-scale experience</span></span>

<span data-ttu-id="b627e-137">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="b627e-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="b627e-138">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="b627e-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="b627e-139">Para experiências reais em grande **escala** sobre o HoloLens que permitem aos usuários percorrer mais de 5 metros, você precisará de novas técnicas além das usadas para experiências em escala de sala.</span><span class="sxs-lookup"><span data-stu-id="b627e-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="b627e-140">Uma técnica importante que você usará é criar uma [âncora espacial](coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente no mundo físico, independentemente de quanto o usuário está em roaming e, em seguida, [encontrar esses hologramas novamente em sessões posteriores](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="b627e-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="b627e-141">No Unity, você cria uma âncora espacial adicionando o componente **WorldAnchor** Unity a um gameobject.</span><span class="sxs-lookup"><span data-stu-id="b627e-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="b627e-142">Adicionando uma âncora mundial</span><span class="sxs-lookup"><span data-stu-id="b627e-142">Adding a World Anchor</span></span>

<span data-ttu-id="b627e-143">Para adicionar uma âncora mundial, chame addComponent<WorldAnchor>() no objeto Game com a transformação que você deseja ancorar no mundo real.</span><span class="sxs-lookup"><span data-stu-id="b627e-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="b627e-144">Pronto!</span><span class="sxs-lookup"><span data-stu-id="b627e-144">That's it!</span></span> <span data-ttu-id="b627e-145">Este objeto de jogo agora será ancorado ao seu local atual no mundo físico – você pode ver que suas coordenadas do Unity World se ajustam um pouco ao longo do tempo para garantir que o alinhamento físico.</span><span class="sxs-lookup"><span data-stu-id="b627e-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="b627e-146">Use a [persistência](persistence-in-unity.md) para localizar esse local ancorado novamente em uma sessão de aplicativo futura.</span><span class="sxs-lookup"><span data-stu-id="b627e-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="b627e-147">Removendo uma âncora mundial</span><span class="sxs-lookup"><span data-stu-id="b627e-147">Removing a World Anchor</span></span>

<span data-ttu-id="b627e-148">Se você não quiser mais que o gameobject seja bloqueado em um local físico do mundo e não pretenda movê-lo para esse quadro, você pode simplesmente chamar Destroy no componente de âncora mundial.</span><span class="sxs-lookup"><span data-stu-id="b627e-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="b627e-149">Se você quiser mover o gameobject para este quadro, precisará chamar DestroyImmediate em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b627e-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="b627e-150">Movendo um jogo de jogos ancorado</span><span class="sxs-lookup"><span data-stu-id="b627e-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="b627e-151">O gameobject não pode ser movido enquanto uma âncora mundial está nele.</span><span class="sxs-lookup"><span data-stu-id="b627e-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="b627e-152">Se você precisar mover o gameobject para este quadro, precisará:</span><span class="sxs-lookup"><span data-stu-id="b627e-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="b627e-153">DestroyImmediate o componente de âncora mundial</span><span class="sxs-lookup"><span data-stu-id="b627e-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="b627e-154">Mover o gameobject</span><span class="sxs-lookup"><span data-stu-id="b627e-154">Move the GameObject</span></span>
3. <span data-ttu-id="b627e-155">Adicione um novo componente de âncora mundial ao gameobject.</span><span class="sxs-lookup"><span data-stu-id="b627e-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="b627e-156">Manipulando alterações de Locatability</span><span class="sxs-lookup"><span data-stu-id="b627e-156">Handling Locatability Changes</span></span>

<span data-ttu-id="b627e-157">Um WorldAnchor pode não ser localizável no mundo físico em um ponto no tempo.</span><span class="sxs-lookup"><span data-stu-id="b627e-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="b627e-158">Se isso ocorrer, o Unity não estará atualizando a transformação do objeto ancorado.</span><span class="sxs-lookup"><span data-stu-id="b627e-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="b627e-159">Isso também pode ser alterado enquanto um aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="b627e-159">This also can change while an app is running.</span></span> <span data-ttu-id="b627e-160">A falha ao manipular a alteração em locatability fará com que o objeto não apareça no local físico correto do mundo.</span><span class="sxs-lookup"><span data-stu-id="b627e-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="b627e-161">Para ser notificado sobre as alterações de locatability:</span><span class="sxs-lookup"><span data-stu-id="b627e-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="b627e-162">Assinar o evento onrastreiechanged</span><span class="sxs-lookup"><span data-stu-id="b627e-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="b627e-163">Manipular o evento</span><span class="sxs-lookup"><span data-stu-id="b627e-163">Handle the event</span></span>

<span data-ttu-id="b627e-164">O evento **Oncontrolchanged** será chamado sempre que a âncora espacial subjacente for alterada entre o estado de ser localizável versus não ser localizável.</span><span class="sxs-lookup"><span data-stu-id="b627e-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="b627e-165">Em seguida, manipule o evento:</span><span class="sxs-lookup"><span data-stu-id="b627e-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="b627e-166">Às vezes, as âncoras estão localizadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b627e-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="b627e-167">Nesse caso, essa propriedade islocalizada da âncora será definida como true quando addComponent<WorldAnchor>() retornar.</span><span class="sxs-lookup"><span data-stu-id="b627e-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="b627e-168">Como resultado, o evento onrastreiechanged não será disparado.</span><span class="sxs-lookup"><span data-stu-id="b627e-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="b627e-169">Um padrão limpo seria chamar o manipulador oncontrolchanged com o estado inicial IsDeleted depois de anexar uma âncora.</span><span class="sxs-lookup"><span data-stu-id="b627e-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="b627e-170">Compartilhando âncoras entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="b627e-170">Sharing anchors across devices</span></span>

<span data-ttu-id="b627e-171">Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem durável de um WorldAnchor local, que seu aplicativo pode localizar em vários dispositivos de HoloLens, Ios e Android.</span><span class="sxs-lookup"><span data-stu-id="b627e-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="b627e-172">Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="b627e-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="b627e-173">Isso permite experiências compartilhadas em tempo real.</span><span class="sxs-lookup"><span data-stu-id="b627e-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="b627e-174">Para começar a criar experiências compartilhadas no Unity, experimente os guias de início rápido dos separadores <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">espaciais do Azure</a>de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="b627e-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="b627e-175">Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar âncoras no Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="b627e-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b627e-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b627e-176">See Also</span></span>
* [<span data-ttu-id="b627e-177">Escalas de experiência</span><span class="sxs-lookup"><span data-stu-id="b627e-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="b627e-178">Estágio espacial</span><span class="sxs-lookup"><span data-stu-id="b627e-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="b627e-179">Como controlar a perda no Unity</span><span class="sxs-lookup"><span data-stu-id="b627e-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="b627e-180">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="b627e-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="b627e-181">Persistência no Unity</span><span class="sxs-lookup"><span data-stu-id="b627e-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="b627e-182">Experiências compartilhadas no Unity</span><span class="sxs-lookup"><span data-stu-id="b627e-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="b627e-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="b627e-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="b627e-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de âncoras espaciais do Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="b627e-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
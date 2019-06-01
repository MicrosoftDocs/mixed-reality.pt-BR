---
title: Mantenha o foco no Unity
description: Olhar é dos principais meios para que os usuários as hologramas que seu aplicativo cria na realidade mista de destino.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: Mantenha o foco, unity, holograma, realidade mista
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453724"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="29323-104">Head olhar no Unity</span><span class="sxs-lookup"><span data-stu-id="29323-104">Head gaze in Unity</span></span>

<span data-ttu-id="29323-105">[Olhares](gaze.md) é dos principais meios para que os usuários de destino do [hologramas](hologram.md) seu aplicativo cria no [realidade misturada](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="29323-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="29323-106">Implementação de olhar principal</span><span class="sxs-lookup"><span data-stu-id="29323-106">Implementing head gaze</span></span>

<span data-ttu-id="29323-107">Conceitualmente, [olhares](gaze.md) é implementado com a projeção de um raio de cabeça do usuário em que é o fone de ouvido, da direção para frente estão enfrentando e determinar o que ray colide com.</span><span class="sxs-lookup"><span data-stu-id="29323-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="29323-108">No Unity, a posição do usuário principal e direção são expostas por meio de principal do Unity [câmera](camera-in-unity.md), especificamente [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="29323-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="29323-109">Chamando [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) resulta em uma [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) estrutura que contém informações sobre a colisão, incluindo o ponto 3D em que ocorreu a colisão e o outro GameObject raio olhar colidiram com.</span><span class="sxs-lookup"><span data-stu-id="29323-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="29323-110">Exemplo: Implemente olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="29323-110">Example: Implement head gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="29323-111">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="29323-111">Best Practices</span></span>

<span data-ttu-id="29323-112">Embora o exemplo acima demonstra como fazer uma única raycast em um loop de atualização para localizar o destino de olhar, é recomendável fazer isso em um único objeto Gerenciando olhar em vez de fazer isso em qualquer objeto que está potencialmente interessado no objeto que está sendo gazed em.</span><span class="sxs-lookup"><span data-stu-id="29323-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="29323-113">Isso permite que seu aplicativo salvar processamento, fazendo apenas uma raycast de olhar cada quadro.</span><span class="sxs-lookup"><span data-stu-id="29323-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="29323-114">Visualizando olhar</span><span class="sxs-lookup"><span data-stu-id="29323-114">Visualizing Gaze</span></span>

<span data-ttu-id="29323-115">Assim como na área de trabalho onde você usa um ponteiro do mouse para direcionar e interagir com o conteúdo, você deve implementar uma [cursor](cursors.md) que representa a olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="29323-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="29323-116">Isso dá a confiança do usuário no qual ele estão prestes a interagir com.</span><span class="sxs-lookup"><span data-stu-id="29323-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="29323-117">Mantenha o foco na realidade mista Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="29323-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="29323-118">Você pode acessar um olhar do [Gerenciador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) no MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="29323-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="29323-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29323-119">See also</span></span>
* [<span data-ttu-id="29323-120">Câmera</span><span class="sxs-lookup"><span data-stu-id="29323-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="29323-121">Olhar entrada</span><span class="sxs-lookup"><span data-stu-id="29323-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="29323-122">Cursores</span><span class="sxs-lookup"><span data-stu-id="29323-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="29323-123">Focar direcionamento</span><span class="sxs-lookup"><span data-stu-id="29323-123">Gaze targeting</span></span>](gaze-targeting.md)

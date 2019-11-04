---
title: Olhar no Unity
description: Olhar é uma maneira primária para os usuários direcionarem os hologramas que seu aplicativo cria em realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: olho-olhar, cabeça olhar, Unity, holograma, realidade misturada
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435299"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="b3484-104">Cabeça-olhar no Unity</span><span class="sxs-lookup"><span data-stu-id="b3484-104">Head-gaze in Unity</span></span>

<span data-ttu-id="b3484-105">[Olhar](gaze-and-commit.md) é uma maneira primária para os usuários direcionarem os [hologramas](hologram.md) que seu aplicativo cria em [realidade misturada](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="b3484-105">[Gaze](gaze-and-commit.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="b3484-106">Implementando o Head-olhar</span><span class="sxs-lookup"><span data-stu-id="b3484-106">Implementing head-gaze</span></span>

<span data-ttu-id="b3484-107">Conceitualmente, o [Head-olhar](gaze-and-commit.md) é implementado projetando um raio a partir da cabeça do usuário onde o headset está, na direção de encaminhamento que estão enfrentando e determinando o que o raio colide com.</span><span class="sxs-lookup"><span data-stu-id="b3484-107">Conceptually, [head-gaze](gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="b3484-108">No Unity, a posição e a direção da cabeça do usuário são expostas por meio da [câmera](camera-in-unity.md)principal do Unity, especificamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="b3484-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="b3484-109">Chamar o [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) resulta em uma estrutura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contém informações sobre a colisão, incluindo o ponto 3D em que ocorreu a colisão e o outro gameobject com o cabeçalho-olhar Ray colisado.</span><span class="sxs-lookup"><span data-stu-id="b3484-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="b3484-110">Exemplo: implementar Head-olhar</span><span class="sxs-lookup"><span data-stu-id="b3484-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="b3484-111">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b3484-111">Best practices</span></span>

<span data-ttu-id="b3484-112">Embora o exemplo acima demonstre como fazer um único Raycast em um loop de atualização para localizar o destino dos pontos de partida do usuário em, é recomendável fazer isso em um único objeto Gerenciando Head-olhar em vez de fazer isso em qualquer objeto potencialmente interessado no obje t está sendo gazed em.</span><span class="sxs-lookup"><span data-stu-id="b3484-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="b3484-113">Isso permite que seu aplicativo salve o processamento fazendo apenas uma cabeça-olhar Raycast cada quadro.</span><span class="sxs-lookup"><span data-stu-id="b3484-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="b3484-114">Visualizando a cabeça-olhar</span><span class="sxs-lookup"><span data-stu-id="b3484-114">Visualizing head-gaze</span></span>

<span data-ttu-id="b3484-115">Assim como no desktop em que você usa um ponteiro do mouse para direcionar e interagir com o conteúdo, você deve implementar um [cursor](cursors.md) que represente o olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="b3484-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="b3484-116">Isso dá ao usuário confiança no que eles estão prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="b3484-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="b3484-117">Head-olhar no kit de ferramentas da realidade misturada v2</span><span class="sxs-lookup"><span data-stu-id="b3484-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="b3484-118">Você pode acessar o Head-olhar do [Gerenciador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) no MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="b3484-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3484-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3484-119">See also</span></span>
* [<span data-ttu-id="b3484-120">Câmera</span><span class="sxs-lookup"><span data-stu-id="b3484-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="b3484-121">Cursores</span><span class="sxs-lookup"><span data-stu-id="b3484-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b3484-122">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="b3484-122">Head-gaze and commit</span></span>](gaze-and-commit.md)

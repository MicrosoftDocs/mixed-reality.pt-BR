---
title: Mantenha o foco no Unity
description: Olhar é dos principais meios para que os usuários as hologramas que seu aplicativo cria na realidade mista de destino.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Mantenha o foco, unity, holograma, realidade mista
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590960"
---
# <a name="gaze-in-unity"></a><span data-ttu-id="f9fad-104">Mantenha o foco no Unity</span><span class="sxs-lookup"><span data-stu-id="f9fad-104">Gaze in Unity</span></span>

<span data-ttu-id="f9fad-105">[Olhares](gaze.md) é dos principais meios para que os usuários de destino do [hologramas](hologram.md) seu aplicativo cria no [realidade misturada](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="f9fad-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="f9fad-106">Implementando olhar</span><span class="sxs-lookup"><span data-stu-id="f9fad-106">Implementing Gaze</span></span>

<span data-ttu-id="f9fad-107">Conceitualmente, [olhares](gaze.md) é implementado com a projeção de um raio de cabeça do usuário em que é o fone de ouvido, da direção para frente estão enfrentando e determinar o que ray colide com.</span><span class="sxs-lookup"><span data-stu-id="f9fad-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="f9fad-108">No Unity, a posição do usuário principal e direção são expostas por meio de principal do Unity [câmera](camera-in-unity.md), especificamente [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="f9fad-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="f9fad-109">Chamando [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) resulta em uma [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) estrutura que contém informações sobre a colisão, incluindo o ponto 3D em que ocorreu a colisão e o outro GameObject raio olhar colidiram com.</span><span class="sxs-lookup"><span data-stu-id="f9fad-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="f9fad-110">Exemplo: Implemente olhar</span><span class="sxs-lookup"><span data-stu-id="f9fad-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="f9fad-111">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="f9fad-111">Best Practices</span></span>

<span data-ttu-id="f9fad-112">Embora o exemplo acima demonstra como fazer uma única raycast em um loop de atualização para localizar o destino de olhar, é recomendável fazer isso em um único objeto Gerenciando olhar em vez de fazer isso em qualquer objeto que está potencialmente interessado no objeto que está sendo gazed em.</span><span class="sxs-lookup"><span data-stu-id="f9fad-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="f9fad-113">Isso permite que seu aplicativo salvar processamento, fazendo apenas uma raycast de olhar cada quadro.</span><span class="sxs-lookup"><span data-stu-id="f9fad-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="f9fad-114">Visualizando olhar</span><span class="sxs-lookup"><span data-stu-id="f9fad-114">Visualizing Gaze</span></span>

<span data-ttu-id="f9fad-115">Assim como na área de trabalho onde você usa um ponteiro do mouse para direcionar e interagir com o conteúdo, você deve implementar uma [cursor](cursors.md) que representa a olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="f9fad-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="f9fad-116">Isso dá a confiança do usuário no qual ele estão prestes a interagir com.</span><span class="sxs-lookup"><span data-stu-id="f9fad-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="f9fad-117">Mantenha o foco no Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f9fad-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="f9fad-118">Quando você importa [MRTK liberar pacotes do Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) ou clonar o projeto a partir o [repositório GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), você vai encontrar um novo menu 'Toolkit de realidade mista' no Unity.</span><span class="sxs-lookup"><span data-stu-id="f9fad-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="f9fad-119">No menu 'Configurar', você verá o menu 'Aplicar misto realidade cena configurações'.</span><span class="sxs-lookup"><span data-stu-id="f9fad-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="f9fad-120">Quando você clica nele, ele remove a câmera padrão e adiciona os componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="f9fad-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="f9fad-121">![Menu MRTK para a instalação de cena](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="f9fad-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="f9fad-122">*Menu MRTK para a instalação de cena*</span><span class="sxs-lookup"><span data-stu-id="f9fad-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="f9fad-123">![Instalação automática de cena no MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="f9fad-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="f9fad-124">*Instalação automática de cena no MRTK*</span><span class="sxs-lookup"><span data-stu-id="f9fad-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="f9fad-125">Mantenha o foco de scripts relacionados no Kit de ferramentas de realidade mista</span><span class="sxs-lookup"><span data-stu-id="f9fad-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="f9fad-126">Misto do Kit de ferramentas da realidade InputManager pré-fabricado inclui [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) e [olhares estabilizador](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span><span class="sxs-lookup"><span data-stu-id="f9fad-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="f9fad-127">Sob [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), você pode atribuir o Cursor personalizado.</span><span class="sxs-lookup"><span data-stu-id="f9fad-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="f9fad-128">Em default, animados [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) é atribuído.</span><span class="sxs-lookup"><span data-stu-id="f9fad-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="f9fad-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) e [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) mostra como visualizar o seu foco no uso de cursores.</span><span class="sxs-lookup"><span data-stu-id="f9fad-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9fad-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9fad-130">See also</span></span>
* [<span data-ttu-id="f9fad-131">Câmera</span><span class="sxs-lookup"><span data-stu-id="f9fad-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="f9fad-132">Gaze</span><span class="sxs-lookup"><span data-stu-id="f9fad-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="f9fad-133">Cursores</span><span class="sxs-lookup"><span data-stu-id="f9fad-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f9fad-134">Mantenha o foco de direcionamento</span><span class="sxs-lookup"><span data-stu-id="f9fad-134">Gaze targeting</span></span>](gaze-targeting.md)

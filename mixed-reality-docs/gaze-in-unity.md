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
# <a name="head-gaze-in-unity"></a>Head olhar no Unity

[Olhares](gaze.md) é dos principais meios para que os usuários de destino do [hologramas](hologram.md) seu aplicativo cria no [realidade misturada](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementação de olhar principal

Conceitualmente, [olhares](gaze.md) é implementado com a projeção de um raio de cabeça do usuário em que é o fone de ouvido, da direção para frente estão enfrentando e determinar o que ray colide com. No Unity, a posição do usuário principal e direção são expostas por meio de principal do Unity [câmera](camera-in-unity.md), especificamente [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Chamando [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) resulta em uma [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) estrutura que contém informações sobre a colisão, incluindo o ponto 3D em que ocorreu a colisão e o outro GameObject raio olhar colidiram com.

### <a name="example-implement-head-gaze"></a>Exemplo: Implemente olhar de cabeçalho

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

### <a name="best-practices"></a>Práticas recomendadas

Embora o exemplo acima demonstra como fazer uma única raycast em um loop de atualização para localizar o destino de olhar, é recomendável fazer isso em um único objeto Gerenciando olhar em vez de fazer isso em qualquer objeto que está potencialmente interessado no objeto que está sendo gazed em. Isso permite que seu aplicativo salvar processamento, fazendo apenas uma raycast de olhar cada quadro.

## <a name="visualizing-gaze"></a>Visualizando olhar

Assim como na área de trabalho onde você usa um ponteiro do mouse para direcionar e interagir com o conteúdo, você deve implementar uma [cursor](cursors.md) que representa a olhar do usuário. Isso dá a confiança do usuário no qual ele estão prestes a interagir com.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Mantenha o foco na realidade mista Toolkit v2
Você pode acessar um olhar do [Gerenciador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) no MRTK v2.

## <a name="see-also"></a>Consulte também
* [Câmera](camera-in-unity.md)
* [Olhar entrada](gaze.md)
* [Cursores](cursors.md)
* [Focar direcionamento](gaze-targeting.md)

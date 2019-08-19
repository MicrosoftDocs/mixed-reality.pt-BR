---
title: Olhar no Unity
description: Olhar é uma maneira primária para os usuários direcionarem os hologramas que seu aplicativo cria em realidade misturada.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: olhar, Unity, holograma, realidade misturada
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453724"
---
# <a name="head-gaze-in-unity"></a>Olhar de cabeçalho no Unity

[Olhar](gaze.md) é uma maneira primária para os usuários direcionarem os [hologramas](hologram.md) que seu aplicativo cria em [realidade misturada](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementando o Head olhar

Conceitualmente, o [olhar](gaze.md) é implementado projetando-se um raio a partir da cabeça do usuário onde o headset está, na direção de encaminhamento que estão enfrentando e determinando o que o raio colide com. No Unity, a posição e a direção da cabeça do usuário são expostas por meio da [câmera](camera-in-unity.md)principal do Unity, especificamente [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Chamar o [física. RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) resulta em uma estrutura [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) que contém informações sobre a colisão, incluindo o ponto 3D em que ocorreu a colisão e a outra gameobject com a qual o olhar Ray colidiu.

### <a name="example-implement-head-gaze"></a>Exemplo: Implementar olhar de cabeçalho

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

Embora o exemplo acima demonstre como fazer um único Raycast em um loop de atualização para localizar o destino olhar, é recomendável fazer isso em um único objeto Gerenciando olhar em vez de fazer isso em qualquer objeto que esteja potencialmente interessado no objeto sendo gazed em. Isso permite que seu aplicativo salve o processamento fazendo apenas um olhar Raycast cada quadro.

## <a name="visualizing-gaze"></a>Visualizando o olhar

Assim como no desktop em que você usa um ponteiro do mouse para direcionar e interagir com o conteúdo, você deve implementar um [cursor](cursors.md) que represente o olhar do usuário. Isso dá ao usuário confiança no que eles estão prestes a interagir.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Olhar no kit de ferramentas de realidade misturada v2
Você pode acessar o olhar do [Gerenciador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) no MRTK v2.

## <a name="see-also"></a>Consulte também
* [Câmera](camera-in-unity.md)
* [Entrada olhar](gaze.md)
* [Cursores](cursors.md)
* [Focar direcionamento](gaze-targeting.md)

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
# <a name="head-gaze-in-unity"></a>Cabeça-olhar no Unity

[Olhar](gaze-and-commit.md) é uma maneira primária para os usuários direcionarem os [hologramas](hologram.md) que seu aplicativo cria em [realidade misturada](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementando o Head-olhar

Conceitualmente, o [Head-olhar](gaze-and-commit.md) é implementado projetando um raio a partir da cabeça do usuário onde o headset está, na direção de encaminhamento que estão enfrentando e determinando o que o raio colide com. No Unity, a posição e a direção da cabeça do usuário são expostas por meio da [câmera](camera-in-unity.md)principal do Unity, especificamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

Chamar o [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) resulta em uma estrutura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contém informações sobre a colisão, incluindo o ponto 3D em que ocorreu a colisão e o outro gameobject com o cabeçalho-olhar Ray colisado.

### <a name="example-implement-head-gaze"></a>Exemplo: implementar Head-olhar

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

Embora o exemplo acima demonstre como fazer um único Raycast em um loop de atualização para localizar o destino dos pontos de partida do usuário em, é recomendável fazer isso em um único objeto Gerenciando Head-olhar em vez de fazer isso em qualquer objeto potencialmente interessado no obje t está sendo gazed em. Isso permite que seu aplicativo salve o processamento fazendo apenas uma cabeça-olhar Raycast cada quadro.

## <a name="visualizing-head-gaze"></a>Visualizando a cabeça-olhar

Assim como no desktop em que você usa um ponteiro do mouse para direcionar e interagir com o conteúdo, você deve implementar um [cursor](cursors.md) que represente o olhar do usuário. Isso dá ao usuário confiança no que eles estão prestes a interagir.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Head-olhar no kit de ferramentas da realidade misturada v2
Você pode acessar o Head-olhar do [Gerenciador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) no MRTK v2.

## <a name="see-also"></a>Consulte também
* [Câmera](camera-in-unity.md)
* [Cursores](cursors.md)
* [Focar com a cabeça e confirmar](gaze-and-commit.md)

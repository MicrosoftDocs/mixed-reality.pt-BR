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
# <a name="gaze-in-unity"></a>Mantenha o foco no Unity

[Olhares](gaze.md) é dos principais meios para que os usuários de destino do [hologramas](hologram.md) seu aplicativo cria no [realidade misturada](mixed-reality.md).

## <a name="implementing-gaze"></a>Implementando olhar

Conceitualmente, [olhares](gaze.md) é implementado com a projeção de um raio de cabeça do usuário em que é o fone de ouvido, da direção para frente estão enfrentando e determinar o que ray colide com. No Unity, a posição do usuário principal e direção são expostas por meio de principal do Unity [câmera](camera-in-unity.md), especificamente [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Chamando [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) resulta em uma [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) estrutura que contém informações sobre a colisão, incluindo o ponto 3D em que ocorreu a colisão e o outro GameObject raio olhar colidiram com.

### <a name="example-implement-gaze"></a>Exemplo: Implemente olhar

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

## <a name="gaze-in-mixed-reality-toolkit"></a>Mantenha o foco no Kit de ferramentas de realidade misturada
Quando você importa [MRTK liberar pacotes do Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) ou clonar o projeto a partir o [repositório GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), você vai encontrar um novo menu 'Toolkit de realidade mista' no Unity. No menu 'Configurar', você verá o menu 'Aplicar misto realidade cena configurações'. Quando você clica nele, ele remove a câmera padrão e adiciona os componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), e [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menu MRTK para a instalação de cena](images/MRTK_Input_Menu.png)<br>
*Menu MRTK para a instalação de cena*

![Instalação automática de cena no MRTK](images/MRTK_HowTo_Input1.png)<br>
*Instalação automática de cena no MRTK*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>Mantenha o foco de scripts relacionados no Kit de ferramentas de realidade mista
Misto do Kit de ferramentas da realidade InputManager pré-fabricado inclui [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) e [olhares estabilizador](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs). Sob [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), você pode atribuir o Cursor personalizado. Em default, animados [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) é atribuído.

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) e [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) mostra como visualizar o seu foco no uso de cursores.

## <a name="see-also"></a>Consulte também
* [Câmera](camera-in-unity.md)
* [Gaze](gaze.md)
* [Cursores](cursors.md)
* [Mantenha o foco de direcionamento](gaze-targeting.md)

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
# <a name="coordinate-systems-in-unity"></a>Sistemas de coordenadas no Unity

Realidade mista do Windows dá suporte a aplicativos em uma ampla variedade de [experiência escalas](coordinate-systems.md), dos aplicativos apenas orientação e escala encaixado backup por meio de aplicativos de escala de sala. Em HoloLens, você pode ir além e compilar aplicativos de escala mundial que permitem aos usuários percorrer além dos 5 metros, explorando um andar inteiro de um edifício e muito mais.

A primeira etapa na criação de uma experiência de realidade misturada no Unity é determinar quais [experiência escala](coordinate-systems.md) seu aplicativo se destinará.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Criação de uma experiência somente orientação ou encaixado em escala

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para criar uma **somente orientação** ou **escala encaixado experiência**, você deve definir Unity como o papel de carta acompanhamento do tipo de espaço. Isso define o sistema de coordenadas de mundo do Unity para acompanhar as [quadro estacionário de referência](coordinate-systems.md#spatial-coordinate-systems). No modo de acompanhamento parado, o conteúdo é colocado no editor de apenas na frente do local de padrão da câmera (para frente é -Z) será exibido na frente do usuário quando o aplicativo for iniciado.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *InputTracking*

Para um puro **experiência somente orientação** como um visualizador de vídeo de 360 graus (onde posicionais atualizações principais seriam arruinando a ilusão), em seguida, você pode definir [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) como true:

```cs
InputTracking.disablePositionalTracking = true;
```

Para um **experiência de escala encaixado**, para permitir que o usuário mais tarde centralizar novamente a origem sentada, você pode chamar o [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) método:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Criar uma experiência de escala permanente ou de escala de espaço

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para um **escala permanente** ou **experiência sala escala**, você precisará colocar o conteúdo em relação ao chão. Justificar o usuário floor usando o  **[estágio espacial](coordinate-systems.md#spatial-coordinate-systems)**, que representa o usuário definidas origem do nível do chão e limite de espaço opcional, definido durante a primeira execução.

Para garantir que o Unity está operando com seu sistema de coordenadas de mundo no nível do chão, você pode definir o Unity para o acompanhamento do tipo de espaço de RoomScale e certifique-se de que o conjunto tenha êxito:

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
* Se SetTrackingSpaceType retornar true, o Unity alternou com êxito seu sistema de coordenadas de mundo para acompanhar as [estágio quadro de referência](coordinate-systems.md#spatial-coordinate-systems).
* Se SetTrackingSpaceType retornar false, o Unity pôde alternar para o estágio quadro de referência, provavelmente porque o usuário não tiver configurado até mesmo um piso em seu ambiente. Isso não é comum, mas pode acontecer se o estágio foi configurado em um local diferente e o dispositivo foi movido para a sala atual sem a configuração de usuário do backup de um novo estágio.

Depois que seu aplicativo com êxito define o RoomScale espaço tipo de controle, conteúdo colocado y = 0 plano aparecerá no chão. A origem (0, 0, 0) será o local específico no chão de onde o usuário resistiu durante a instalação da sala, com a -Z que representa a direção de avançada que estavam enfrentando durante a instalação.

**Namespace:** *UnityEngine.Experimental.XR*<br>
**Tipo:** *Limite*

No código de script, você pode, em seguida, chame o método TryGetGeometry você é do tipo de UnityEngine.Experimental.XR.Boundary para obter um polígono do limite, especificando um tipo de limite de TrackedArea. Se o usuário definido um limite (você obter uma lista de vértices), você sabe que é seguro fornecer um **experiência de escala de sala** para o usuário, onde eles podem orientá-lo ao redor do cenário criar.

Observe que o sistema automaticamente renderizará o limite quando o usuário se aproxima dela. Seu aplicativo não precisa usar este polígono para renderizar o limite em si. No entanto, você pode optar por dispor os objetos de cena usando este polígono do limite, para garantir que o usuário fisicamente pode atingir esses objetos sem teleporting:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Criar uma experiência de dimensionamento do mundo

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldAnchor*

Para verdadeiro **experiências do mundo em escala** em HoloLens que permitem aos usuários percorrer além dos medidores de 5, você precisará de novas técnicas além daquelas usadas para experiências de sala em escala. Uma técnica chave que você usará é criar uma [âncora espacial](coordinate-systems.md#spatial-anchors) para bloquear um cluster de hologramas precisamente em vigor no mundo físico, independentemente do quanto o usuário tem de roaming e, em seguida, [encontrar esses hologramas novamente em mais tarde sessões](coordinate-systems.md#spatial-anchor-persistence).

No Unity, você cria uma âncora espacial, adicionando a **WorldAnchor** componente do Unity para um GameObject.

### <a name="adding-a-world-anchor"></a>Adicionando uma âncora de mundo

Para adicionar uma âncora de mundo, chame AddComponent<WorldAnchor>() no objeto do jogo com a transformação que você deseja ancorar no mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

É só isso! Esse objeto do jogo agora será ancorado seu local atual no mundo físico – você poderá ver suas coordenadas de mundo Unity ajustar um pouco ao longo do tempo para garantir que o alinhamento físico. Use [persistência](persistence-in-unity.md) para encontrá-la ancorada local novamente em uma sessão de aplicativo futuras.

### <a name="removing-a-world-anchor"></a>Removendo uma âncora de mundo

Se não desejar que o GameObject bloqueada para um local do mundo físico e não pretende movê-lo neste quadro, em seguida, você pode simplesmente chamar Destroy no componente de âncora do mundo.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Se você quiser mover o GameObject este quadro, você precisará chamar DestroyImmediate em vez disso.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Mover um mundo ancorado GameObject

Não pode ser movido do GameObject, enquanto uma âncora de mundo está nele. Se você precisar mover o GameObject este quadro, você precisa:
1. DestroyImmediate o componente de âncora do mundo
2. Mover o GameObject
3. Adicione um novo componente de âncora do mundo para o GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Tratando alterações Locatability

Um WorldAnchor pode não ser localizáveis no mundo físico em um ponto no tempo. Se isso ocorrer, Unity não atualizará a transformação do objeto ancorado. Isso também pode alterar enquanto um aplicativo está em execução. Falha em lidar com a alteração no locatability fará com que o objeto não apareça no local físico correto no mundo.

Para ser notificado sobre alterações de locatability:
1. Assinar o evento OnTrackingChanged
2. Manipular o evento

O **OnTrackingChanged** evento será chamado sempre que a âncora espacial subjacente é alterado entre um estado de ser localizáveis versus não sendo localizáveis.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Em seguida, manipule o evento:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Às vezes, as âncoras estão localizadas imediatamente. Nesse caso, essa propriedade isLocated da âncora será definida como true quando AddComponent<WorldAnchor>() retorna. Como resultado, o evento OnTrackingChanged não será disparado. Um padrão de limpar seria chamar seu manipulador OnTrackingChanged com o estado inicial do IsLocated depois de anexar uma âncora.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Compartilhando as âncoras entre dispositivos

Você pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para criar uma âncora de nuvem durável de um local WorldAnchor, o que seu aplicativo pode, em seguida, localizar em vários HoloLens, dispositivos iOS e Android.  Compartilhando uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

Para começar a criação de experiências compartilhadas no Unity, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guias de início rápido do Azure espacial âncoras Unity</a>.

Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">criar e localizar as âncoras no Unity</a>.

## <a name="see-also"></a>Consulte também
* [Escalas de experiência](coordinate-systems.md#mixed-reality-experience-scales)
* [Estágio espacial](coordinate-systems.md#stage-frame-of-reference)
* [Controlando a perda no Unity](tracking-loss-in-unity.md)
* [Âncoras espaciais](spatial-anchors.md)
* [Persistência no Unity](persistence-in-unity.md)
* [Experiências compartilhadas no Unity](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Âncoras espaciais do Azure SDK para Unity</a>
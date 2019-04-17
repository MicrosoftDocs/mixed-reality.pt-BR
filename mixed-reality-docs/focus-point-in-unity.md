---
title: Ponto de foco no Unity
description: Ajuste manual estabilidade holograma no Unity, definindo o ponto de foco
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, ponto de foco, o plano de foco, o plano de estabilização, ponto de estabilização, reprojection, LSR, buffers de profundidade
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590976"
---
# <a name="focus-point-in-unity"></a>Ponto de foco no Unity

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo**: *HolographicSettings*

O [focar ponto](hologram-stability.md#stabilization-plane) pode ser definido para fornecer uma dica sobre como executar melhor estabilização nas hologramas atualmente de HoloLens que está sendo exibido.

Se você deseja definir o ponto de foco no Unity, ele precisa ser definido usando cada quadro *HolographicSettings.SetFocusPointForFrame()*. Se o ponto de foco não está definido para um quadro, o plano de estabilização padrão será usado.

> [!NOTE]
> Por padrão, a novos projetos do Unity tem a opção "Habilitar profundidade Buffer compartilhamento" a definir.  Com essa opção, um aplicativo Unity em execução em um fone de ouvido imersivo da área de trabalho ou um HoloLens executando o Windows 10 de abril de 2018 Update (RS4) ou posterior enviará seu buffer de profundidade para Windows para otimizar a estabilidade holograma automaticamente, sem especificar seu aplicativo um ponto de foco:
> * Em um fone de ouvido imersivo da área de trabalho, isso permitirá reprojection com base em profundidade por pixel.
> * Em um HoloLens executando o Windows 10 de abril de 2018 Update ou posterior, isso irá analisar o buffer de profundidade para escolher um plano de estabilização ideal automaticamente.
>
> Qualquer uma das abordagens deve fornecer ainda melhor qualidade de imagem sem trabalho explícita pelo seu aplicativo para selecionar um ponto de foco cada quadro.  Observe que se você fornecer manualmente um ponto de foco, que substituirá o comportamento automático descrito acima e geralmente reduzirá estabilidade holograma.  Em geral, você deve especificar somente um ponto de foco manual quando seu aplicativo está em execução em um HoloLens que ainda não foi atualizado para o Windows Update 10 de abril de 2018.

### <a name="example"></a>Exemplo

Há várias maneiras para definir o ponto de foco, conforme sugerido pelas sobrecargas disponíveis na *SetFocusPointForFrame* função estática. Apresentada a seguir está um exemplo simples para definir o plano de foco para o objeto fornecido a cada quadro:

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

Observe que o código simples acima pode acabar reduzindo estabilidade holograma se o objeto com foco acaba por trás do usuário.  É por isso você geralmente deve definir a ""habilitar a profundidade de Buffer compartilhamento em vez de especificar manualmente um ponto de foco.

### <a name="see-also"></a>Consulte também
* [Plano de estabilização](hologram-stability.md#stabilization-plane)

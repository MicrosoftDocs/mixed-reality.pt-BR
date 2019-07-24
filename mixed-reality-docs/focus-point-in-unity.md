---
title: Ponto de foco no Unity
description: Ajuste manual da estabilidade do holograma no Unity definindo o ponto de foco
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, ponto de foco, plano de foco, plano de estabilização, ponto de estabilização, Reprojeção, LSR, buffer de profundidade
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525464"
---
# <a name="focus-point-in-unity"></a>Ponto de foco no Unity

**Namespace:** *UnityEngine. XR. WSA*<br>
**Tipo**: *HolographicSettings*

O [ponto de foco](hologram-stability.md#stabilization-plane) pode ser definido para fornecer uma dica sobre como executar melhor a estabilização nos hologramas que estão sendo exibidos no momento.

Se você quiser definir o ponto de foco no Unity, ele precisará ser definido a cada quadro usando *HolographicSettings. SetFocusPointForFrame ()* . Se o ponto de foco não estiver definido para um quadro, o plano de estabilização padrão será usado.

> [!NOTE]
> Por padrão, novos projetos do Unity têm a opção "Habilitar compartilhamento de buffer de profundidade" definida.  Com essa opção, um aplicativo do Unity em execução em um headset de área de trabalho imersiva ou um HoloLens executando a atualização de abril de 2018 do Windows (RS4) ou posterior enviará seu buffer de profundidade para o Windows para otimizar a estabilidade do holograma automaticamente, sem que seu aplicativo especifique um ponto de foco:
> * Em um headset de área de trabalho imersiva, isso habilitará a Reprojeção baseada em profundidade por pixel.
> * Em um HoloLens executando a atualização de abril de 2018 do Windows 10 ou posterior, isso analisará o buffer de profundidade para escolher um plano de estabilização ideal automaticamente.
>
> Qualquer uma das abordagens deve fornecer uma qualidade de imagem ainda melhor sem trabalho explícito por seu aplicativo para selecionar um ponto de foco em cada quadro.  Observe que, se você fornecer um ponto de foco manualmente, isso substituirá o comportamento automático descrito acima e geralmente reduzirá a estabilidade do holograma.  Em geral, você deve especificar apenas um ponto de foco manual quando seu aplicativo estiver em execução em um HoloLens que ainda não foi atualizado para a atualização do Windows 10 de abril de 2018.

### <a name="example"></a>Exemplo

Há várias maneiras de definir o ponto de foco, conforme sugerido pelas sobrecargas disponíveis na função estática *SetFocusPointForFrame* . Veja abaixo um exemplo simples para definir o plano de foco para o objeto fornecido em cada quadro:

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

Observe que o código simples acima pode acabar reduzindo a estabilidade do holograma se o objeto focalizado terminar por trás do usuário.  É por isso que você geralmente deve definir "habilitar o compartilhamento de buffer de profundidade" em vez de especificar manualmente um ponto de foco.

### <a name="see-also"></a>Consulte também
* [Plano de estabilização](hologram-stability.md#stabilization-plane)

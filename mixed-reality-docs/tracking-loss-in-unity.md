---
title: Controlando a perda no Unity
description: Tratamento de perda de dentro de um aplicativo do Unity de acompanhamento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, controlando a perda, a imagem de perda de controle
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590491"
---
# <a name="tracking-loss-in-unity"></a>Controlando a perda no Unity

Quando o dispositivo não pode localizar-se no mundo, o aplicativo passa por "perda de controle". Por padrão, o Unity pausar o loop de atualização e exibir uma imagem de abertura para o usuário. Quando o rastreamento é recuperado, a imagem inicial desaparece e continua o loop de atualização.

Como alternativa, o usuário pode manipular manualmente essa transição ao recusar a configuração. Todo o conteúdo parecerá tornam-se o corpo bloqueado durante a perda de controle se nada é feito para manipulá-lo.

## <a name="default-handling"></a>O tratamento padrão

Por padrão, o loop de atualização do aplicativo, bem como todos os eventos e mensagens será interrompido para a duração da perda de controle. Ao mesmo tempo, uma imagem será exibida ao usuário. Você pode personalizar essa imagem ao ir até Editar -> Configurações -> Player, clicando em imagem inicial e definir a imagem holográfica perda de controle.

## <a name="manual-handling"></a>Manipulação manual

Para lidar manualmente com a perda de controle, você precisará ir para **edite** > **configurações do projeto** > **Player**  >   **Guia de configurações de plataforma Windows universal** > **imagem inicial** > **Windows Holographic** e desmarque a opção "no controle perda pausa e Mostrar imagem ". Depois disso, você precisa lidar com o controle de alterações com as APIs especificadas abaixo.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldManager*

* Gerenciador de mundo expõe um evento para detectar obtidas/perdidas acompanhamento (*WorldManager.OnPositionalLocatorStateChanged*) e uma propriedade para consultar o estado atual (*WorldManager.state*)
* Quando o estado de controle não está ativo, a câmera não aparecerá converter no mundo virtual, até mesmo quando o usuário converte. Isso significa que os objetos não corresponderá ao qualquer local físico e todos aparecerão corpo bloqueado.

Ao lidar com o controle de alterações em seus próprios, você precisará sondar a propriedade state cada quadro ou identificador a *OnPositionalLocatorStateChanged* eventos.

### <a name="polling"></a>sondagem

É o estado mais importante *PositionalLocatorState.Active* que significa que o acompanhamento está totalmente funcional. Qualquer outro estado resulta em apenas rotacional deltas para a câmera principal. Por exemplo: 

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Manipulando o evento OnPositionalLocatorStateChanged

Como alternativa e mais conveniente, você também pode assinar *OnPositionalLocatorStateChanged* para lidar com as transições:

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>Consulte também
* [Tratamento de perda de acompanhamento no DirectX](coordinate-systems-in-directx.md#handling-tracking-loss)

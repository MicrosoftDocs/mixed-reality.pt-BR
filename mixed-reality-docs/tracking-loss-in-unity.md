---
title: Perda de rastreamento no Unity
description: Tratamento da perda de controle em um aplicativo do Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, perda de controle, imagem de perda de rastreamento
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548749"
---
# <a name="tracking-loss-in-unity"></a>Perda de rastreamento no Unity

Quando o dispositivo não consegue se localizar no mundo, o aplicativo tem "perda de rastreamento". Por padrão, o Unity pausará o loop de atualização e exibirá uma imagem de abertura para o usuário. Quando o rastreamento é retomado, a imagem de abertura desaparece e o loop de atualização continua.

Como alternativa, o usuário pode lidar com essa transição manualmente, recusando a configuração. Todo o conteúdo parecerá ficar bloqueado durante a perda de rastreamento se nada for feito para tratá-lo.

## <a name="default-handling"></a>Manipulação padrão

Por padrão, o loop Update do aplicativo, bem como todas as mensagens e eventos, serão interrompidos durante a perda de rastreamento. Ao mesmo tempo, uma imagem será exibida para o usuário. Você pode personalizar essa imagem acessando configurações de > de edição – > Player, clicando em imagem de abertura e definindo a imagem de perda de rastreamento de Holographic.

## <a name="manual-handling"></a>Manipulação manual

Para lidar manualmente com a perda de controle, você precisa ir para **Editar** > **configurações** >  > do projeto plataforma universal do Windows**imagem**  > deSplashdaguiaConfigurações >  **Windows Holographic** e desmarque "ao rastrear a perda e mostrar imagem". Depois, você precisa lidar com as alterações de controle com as APIs especificadas abaixo.

**Namespace:** *UnityEngine. XR. WSA*<br>
**Escreva** *Worldmanager*

* O World Manager expõe um evento para detectar o controle perdido/obtido (*worldmanager. OnPositionalLocatorStateChanged*) e uma propriedade para consultar o estado atual (*worldmanager. State*)
* Quando o estado de acompanhamento não estiver ativo, a câmera não parecerá traduzir no mundo virtual mesmo que o usuário se traduz. Isso significa que os objetos não corresponderão mais a qualquer local físico e todos serão exibidos no corpo bloqueado.

Ao lidar com alterações de controle por conta própria, você precisa sondar a propriedade de estado em cada quadro ou manipular o evento *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Poll

O estado mais importante é *PositionalLocatorState. Active* , o que significa que o controle é totalmente funcional. Qualquer outro Estado resultará em apenas deltas rotacionais para a câmera principal. Por exemplo:

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

Como alternativa e mais conveniente, você também pode assinar o *OnPositionalLocatorStateChanged* para lidar com as transições:

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
* [Lidando com a perda de controle no DirectX](coordinate-systems-in-directx.md#handling-tracking-loss)

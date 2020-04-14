---
title: Transferências de âncora local no Unity
description: Transfira âncoras entre vários dispositivos HoloLens em um aplicativo Unity.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Compartilhamento, ancoragem, WorldAnchor, Sr Sharing 250, WorldAnchorTransferBatch, SpatialPerception, transferência, transferência de âncora local, exportação de ancoragem, importação de âncora
ms.openlocfilehash: fd071f736add094fd65ae4d889f8008eefd8515d
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278054"
---
# <a name="local-anchor-transfers-in-unity"></a>Transferências de âncora local no Unity

Em situações em que você não pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espaciais do Azure</a>, as transferências de âncora local permitem que um dispositivo de hololens exporte uma âncora a ser importada por um segundo dispositivo hololens.

>[!NOTE]
>As transferências de âncora local fornecem uma recall de ancoragem menos robusta do que as <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espaciais do Azure</a>, e os dispositivos IOS e Android não são compatíveis com essa abordagem.

### <a name="setting-the-spatialperception-capability"></a>Configurando o recurso SpatialPerception

Para que um aplicativo transfira âncoras espaciais, o recurso *SpatialPerception* deve ser habilitado.

Como habilitar o recurso *SpatialPerception* :
1. No editor do Unity, abra o painel **"configurações do Player"** (Editar > configurações do projeto > Player)
2. Clique na guia **"Windows Store"**
3. Expanda **"configurações de publicação"** e verifique o recurso **"SpatialPerception"** na lista **"recursos"**

>[!NOTE]
>Se você já tiver exportado seu projeto do Unity para uma solução do Visual Studio, será necessário exportar para uma nova pasta ou [definir manualmente esse recurso no AppxManifest no Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Transferência de âncora

**Namespace:** *UnityEngine. XR. WSA. Sharing*<br>
**Tipo**: *WorldAnchorTransferBatch*

Para transferir um [WorldAnchor](coordinate-systems-in-unity.md), um deve estabelecer a âncora a ser transferida. O usuário de um HoloLens examina seu ambiente e, manual ou programaticamente, escolhe um ponto no espaço para ser a âncora para a experiência compartilhada. Os dados que representam esse ponto podem ser serializados e transmitidos para os outros dispositivos que estão compartilhando na experiência. Em seguida, cada dispositivo desserializa os dados de âncora e tenta localizar esse ponto no espaço. Para que a transferência de âncora funcione, cada dispositivo deve ser examinado em suficiente no ambiente, de modo que o ponto representado pela âncora possa ser identificado.

### <a name="setup"></a>Instalação

O código de exemplo nesta página tem alguns campos que deverão ser inicializados:
1. *Gameobject rootGameObject* é um *gameobject* no Unity que tem um componente *WorldAnchor* . Um usuário na experiência compartilhada coloca esse *gameobject* e exporta os dados para os outros usuários.
2. *WorldAnchor gameRootAnchor* é *UnityEngine. XR. WSA. WorldAnchor* que está em *rootGameObject*.
3. *byte [] importedData* é uma matriz de bytes para a âncora serializada que cada cliente está recebendo pela rede.

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>Exportar

Para exportar, precisamos apenas de um *WorldAnchor* e saber o que iremos chamá-lo de modo que faça sentido para o aplicativo de recebimento. Um cliente na experiência compartilhada executará estas etapas para exportar a âncora compartilhada:
1. Criar um *WorldAnchorTransferBatch*
2. Adicionar o *WorldAnchors* para transferência
3. Iniciar a exportação
4. Manipular o evento *OnExportDataAvailable* à medida que os dados ficam disponíveis
5. Manipular o evento *OnExportComplete*

Criamos um *WorldAnchorTransferBatch* para encapsular o que iremos transferir e, em seguida, exportá-lo em bytes:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

À medida que os dados ficam disponíveis, envie os bytes para o cliente ou buffer, pois os segmentos de dados estão disponíveis e envie por qualquer meio desejado:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Quando a exportação for concluída, se a transferência de dados e a serialização falharem, diga ao cliente para descartar os dados. Se a serialização tiver sido bem-sucedida, informe ao cliente que todos os dados foram transferidos e a importação pode começar:

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>Importar

Depois de receber todos os bytes do remetente, podemos importar os dados de volta para um *WorldAnchorTransferBatch* e bloquear nosso objeto de jogo raiz para o mesmo local físico. Observação: a importação, às vezes, falha transitória e precisa ser repetida:

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

Depois que um *gameobject* é bloqueado por meio da chamada *lockobject* , ele terá um *WorldAnchor* que o manterá na mesma posição física do mundo, mas pode estar em um local diferente no espaço de coordenadas do Unity do que outros usuários.


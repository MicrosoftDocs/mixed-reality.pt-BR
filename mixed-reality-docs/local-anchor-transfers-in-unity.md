---
title: Transferências de local de âncora no Unity
description: Transferir as âncoras entre vários dispositivos do HoloLens em um aplicativo do Unity.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Compartilhamento, âncora, WorldAnchor, MR compartilhamento 250, WorldAnchorTransferBatch, SpatialPerception, transferência, transferência de local de ancoragem, exportação de âncora, importação de âncora
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591011"
---
# <a name="local-anchor-transfers-in-unity"></a>Transferências de local de âncora no Unity

Em situações em que você não pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, transferências de local de ancoragem permitem que um dispositivo de HoloLens exportar uma âncora para ser importado por um segundo dispositivo HoloLens.

>[!NOTE]
>As transferências de âncora local fornecem o recall de âncora menos robusta do que <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, e não há suporte para dispositivos iOS e Android por essa abordagem.

### <a name="setting-the-spatialperception-capability"></a>Definindo a capacidade de SpatialPerception

Para que um aplicativo transferir espaciais âncoras, o *SpatialPerception* recurso deve ser ativado.

Como habilitar o *SpatialPerception* funcionalidade:
1. No Editor do Unity, abra o **"Configurações do Player"** painel (Editar > configurações do projeto > Player)
2. Clique no **"Windows Store"** guia
3. Expandir **"Configurações de publicação"** e verifique o **"SpatialPerception"** funcionalidade no **"Recursos"** lista

>[!NOTE]
>Se você já tiver exportado seu projeto do Unity para uma solução do Visual Studio, você precisará exportar para uma nova pasta ou manualmente [definir esse recurso em que o AppxManifest no Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Transferência de âncora

**Namespace:** *UnityEngine.XR.WSA.Sharing*<br>
**Tipo**: *WorldAnchorTransferBatch*

Para transferir uma [WorldAnchor](coordinate-systems-in-unity.md), um deve estabelecer a âncora a serem transferidos. O usuário de um HoloLens examina o seu ambiente e manualmente ou por meio de programação escolhe um ponto no espaço para ser a âncora para a experiência compartilhada. Os dados que representa este ponto podem ser serializados e transmitidos para os outros dispositivos que estão compartilhando a experiência. Cada dispositivo, em seguida, desserializa os dados de âncora e tenta localizar esse ponto no espaço. Em ordem para transferir a âncora para funcionar, cada dispositivo deve ter digitalizado parte suficiente do ambiente, de modo que o ponto representado por âncora pode ser identificado.

### <a name="setup"></a>Configuração

O código de exemplo nesta página tem alguns campos que precisam ser inicializados:
1. *GameObject rootGameObject* é um *GameObject* no Unity que tem um *WorldAnchor* componente nele. Um usuário na experiência de compartilhado Isso colocará *GameObject* e exportar os dados para os outros usuários.
2. *WorldAnchor gameRootAnchor* é o *UnityEngine.XR.WSA.WorldAnchor* que está na *rootGameObject*.
3. *Byte [] importedData* é uma matriz de bytes para a âncora serializada de cada cliente está recebendo pela rede.

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

### <a name="exporting"></a>Exportando

Para exportar, precisamos apenas de uma *WorldAnchor* e saber o que podemos chamá-lo, de modo que ele faça sentido para o aplicativo de recebimento. Um cliente na experiência de compartilhado executará estas etapas para exportar a âncora compartilhada:
1. Criar um *WorldAnchorTransferBatch*
2. Adicione a *WorldAnchors* para transferir
3. Iniciar a exportação
4. Lidar com o *OnExportDataAvailable* eventos como dados se torna disponível
5. Lidar com o *OnExportComplete* evento

Podemos criar uma *WorldAnchorTransferBatch* para encapsular o que podemos será transferência e, em seguida, fazer a exportação em bytes:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Como os dados ficam disponíveis, enviar os bytes para o cliente ou o buffer, como segmentos de dados está disponível e enviar por meio de qualquer meio desejado:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Quando a exportação for concluída, se podemos ter sido transferência de dados e Falha na serialização, dizer ao cliente descartar os dados. Se a serialização for bem-sucedida, dizer ao cliente que todos os dados foram transferidos e pode começar a importar:

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

### <a name="importing"></a>Importando

Depois de receber todos os bytes do remetente, podemos importar os dados de volta para um *WorldAnchorTransferBatch* e bloquear o nosso objeto de jogo de raiz no mesmo local físico. Observação: a importação falhará, às vezes, transiently e deverá ser repetida:

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

Após um *GameObject* seja bloqueada pelo *LockObject* chamada, ele terá um *WorldAnchor* que irá mantê-lo na mesma posição no mundo física, mas pode ser em um o espaço que outros usuários de coordenadas de local diferente no Unity.


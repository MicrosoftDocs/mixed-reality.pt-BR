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
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="cb984-104">Transferências de local de âncora no Unity</span><span class="sxs-lookup"><span data-stu-id="cb984-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="cb984-105">Em situações em que você não pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, transferências de local de ancoragem permitem que um dispositivo de HoloLens exportar uma âncora para ser importado por um segundo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cb984-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="cb984-106">As transferências de âncora local fornecem o recall de âncora menos robusta do que <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, e não há suporte para dispositivos iOS e Android por essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="cb984-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="cb984-107">Definindo a capacidade de SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="cb984-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="cb984-108">Para que um aplicativo transferir espaciais âncoras, o *SpatialPerception* recurso deve ser ativado.</span><span class="sxs-lookup"><span data-stu-id="cb984-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="cb984-109">Como habilitar o *SpatialPerception* funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="cb984-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="cb984-110">No Editor do Unity, abra o **"Configurações do Player"** painel (Editar > configurações do projeto > Player)</span><span class="sxs-lookup"><span data-stu-id="cb984-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="cb984-111">Clique no **"Windows Store"** guia</span><span class="sxs-lookup"><span data-stu-id="cb984-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="cb984-112">Expandir **"Configurações de publicação"** e verifique o **"SpatialPerception"** funcionalidade no **"Recursos"** lista</span><span class="sxs-lookup"><span data-stu-id="cb984-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="cb984-113">Se você já tiver exportado seu projeto do Unity para uma solução do Visual Studio, você precisará exportar para uma nova pasta ou manualmente [definir esse recurso em que o AppxManifest no Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="cb984-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="cb984-114">Transferência de âncora</span><span class="sxs-lookup"><span data-stu-id="cb984-114">Anchor Transfer</span></span>

<span data-ttu-id="cb984-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="cb984-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="cb984-116">**Tipo**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="cb984-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="cb984-117">Para transferir uma [WorldAnchor](coordinate-systems-in-unity.md), um deve estabelecer a âncora a serem transferidos.</span><span class="sxs-lookup"><span data-stu-id="cb984-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="cb984-118">O usuário de um HoloLens examina o seu ambiente e manualmente ou por meio de programação escolhe um ponto no espaço para ser a âncora para a experiência compartilhada.</span><span class="sxs-lookup"><span data-stu-id="cb984-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="cb984-119">Os dados que representa este ponto podem ser serializados e transmitidos para os outros dispositivos que estão compartilhando a experiência.</span><span class="sxs-lookup"><span data-stu-id="cb984-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="cb984-120">Cada dispositivo, em seguida, desserializa os dados de âncora e tenta localizar esse ponto no espaço.</span><span class="sxs-lookup"><span data-stu-id="cb984-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="cb984-121">Em ordem para transferir a âncora para funcionar, cada dispositivo deve ter digitalizado parte suficiente do ambiente, de modo que o ponto representado por âncora pode ser identificado.</span><span class="sxs-lookup"><span data-stu-id="cb984-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="cb984-122">Configuração</span><span class="sxs-lookup"><span data-stu-id="cb984-122">Setup</span></span>

<span data-ttu-id="cb984-123">O código de exemplo nesta página tem alguns campos que precisam ser inicializados:</span><span class="sxs-lookup"><span data-stu-id="cb984-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="cb984-124">*GameObject rootGameObject* é um *GameObject* no Unity que tem um *WorldAnchor* componente nele.</span><span class="sxs-lookup"><span data-stu-id="cb984-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="cb984-125">Um usuário na experiência de compartilhado Isso colocará *GameObject* e exportar os dados para os outros usuários.</span><span class="sxs-lookup"><span data-stu-id="cb984-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="cb984-126">*WorldAnchor gameRootAnchor* é o *UnityEngine.XR.WSA.WorldAnchor* que está na *rootGameObject*.</span><span class="sxs-lookup"><span data-stu-id="cb984-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="cb984-127">*Byte [] importedData* é uma matriz de bytes para a âncora serializada de cada cliente está recebendo pela rede.</span><span class="sxs-lookup"><span data-stu-id="cb984-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="cb984-128">Exportando</span><span class="sxs-lookup"><span data-stu-id="cb984-128">Exporting</span></span>

<span data-ttu-id="cb984-129">Para exportar, precisamos apenas de uma *WorldAnchor* e saber o que podemos chamá-lo, de modo que ele faça sentido para o aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="cb984-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="cb984-130">Um cliente na experiência de compartilhado executará estas etapas para exportar a âncora compartilhada:</span><span class="sxs-lookup"><span data-stu-id="cb984-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="cb984-131">Criar um *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="cb984-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="cb984-132">Adicione a *WorldAnchors* para transferir</span><span class="sxs-lookup"><span data-stu-id="cb984-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="cb984-133">Iniciar a exportação</span><span class="sxs-lookup"><span data-stu-id="cb984-133">Begin the export</span></span>
4. <span data-ttu-id="cb984-134">Lidar com o *OnExportDataAvailable* eventos como dados se torna disponível</span><span class="sxs-lookup"><span data-stu-id="cb984-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="cb984-135">Lidar com o *OnExportComplete* evento</span><span class="sxs-lookup"><span data-stu-id="cb984-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="cb984-136">Podemos criar uma *WorldAnchorTransferBatch* para encapsular o que podemos será transferência e, em seguida, fazer a exportação em bytes:</span><span class="sxs-lookup"><span data-stu-id="cb984-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="cb984-137">Como os dados ficam disponíveis, enviar os bytes para o cliente ou o buffer, como segmentos de dados está disponível e enviar por meio de qualquer meio desejado:</span><span class="sxs-lookup"><span data-stu-id="cb984-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="cb984-138">Quando a exportação for concluída, se podemos ter sido transferência de dados e Falha na serialização, dizer ao cliente descartar os dados.</span><span class="sxs-lookup"><span data-stu-id="cb984-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="cb984-139">Se a serialização for bem-sucedida, dizer ao cliente que todos os dados foram transferidos e pode começar a importar:</span><span class="sxs-lookup"><span data-stu-id="cb984-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="cb984-140">Importando</span><span class="sxs-lookup"><span data-stu-id="cb984-140">Importing</span></span>

<span data-ttu-id="cb984-141">Depois de receber todos os bytes do remetente, podemos importar os dados de volta para um *WorldAnchorTransferBatch* e bloquear o nosso objeto de jogo de raiz no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="cb984-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="cb984-142">Observação: a importação falhará, às vezes, transiently e deverá ser repetida:</span><span class="sxs-lookup"><span data-stu-id="cb984-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="cb984-143">Após um *GameObject* seja bloqueada pelo *LockObject* chamada, ele terá um *WorldAnchor* que irá mantê-lo na mesma posição no mundo física, mas pode ser em um o espaço que outros usuários de coordenadas de local diferente no Unity.</span><span class="sxs-lookup"><span data-stu-id="cb984-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>


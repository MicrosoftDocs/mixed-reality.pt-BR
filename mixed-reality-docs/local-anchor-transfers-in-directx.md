---
title: Transferências de local de âncora no DirectX
description: Explica como sincronizar dois dispositivos HoloLens transferindo âncoras espaciais.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, sincronizar, âncora espacial, transferência, com vários participantes, exibir, cenário, passo a passo, código de exemplo, transferência, transferência de local de ancoragem, exportação de âncora, importação de âncora
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591013"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="b0a86-104">Transferências de local de âncora no DirectX</span><span class="sxs-lookup"><span data-stu-id="b0a86-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="b0a86-105">Em situações em que você não pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, transferências de local de ancoragem permitem que um dispositivo de HoloLens exportar uma âncora para ser importado por um segundo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b0a86-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="b0a86-106">As transferências de âncora local fornecem o recall de âncora menos robusta do que <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, e não há suporte para dispositivos iOS e Android por essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="b0a86-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="b0a86-107">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="b0a86-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="b0a86-108">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="b0a86-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="b0a86-109">Transferindo âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="b0a86-109">Transferring spatial anchors</span></span>

<span data-ttu-id="b0a86-110">Você pode transferir âncoras espaciais entre dispositivos de realidade mista do Windows usando o [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0a86-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="b0a86-111">Essa API permite reunir uma âncora com todos os dados de sensor suporte necessários para localizar o local exato no mundo e, em seguida, importar esse pacote em outro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b0a86-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="b0a86-112">Depois que o aplicativo no segundo dispositivo tiver importado que ancoram, cada aplicativo pode processar hologramas usando que compartilhados do sistema de coordenadas da âncora espacial, que, em seguida, será exibida no mesmo lugar no mundo real.</span><span class="sxs-lookup"><span data-stu-id="b0a86-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="b0a86-113">Observe que âncoras espaciais não são capazes de transferir entre tipos diferentes de dispositivos, por exemplo uma âncora de espacial HoloLens pode não ser localizáveis usando um fone de ouvido envolvente.</span><span class="sxs-lookup"><span data-stu-id="b0a86-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="b0a86-114">Âncoras transferidas também não são compatíveis com dispositivos iOS ou Android.</span><span class="sxs-lookup"><span data-stu-id="b0a86-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="b0a86-115">Configurar seu aplicativo para usar o recurso de spatialPerception</span><span class="sxs-lookup"><span data-stu-id="b0a86-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="b0a86-116">Seu aplicativo deve ter a permissão para usar o recurso de spatialPerception antes de poder usar o [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0a86-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="b0a86-117">Isso é necessário porque a transferência de uma âncora espacial envolve compartilhando imagens de sensor coletadas ao longo do tempo na vizinhança dessa âncora, que pode incluir informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="b0a86-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="b0a86-118">Declare esse recurso no arquivo Package. appxmanifest para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0a86-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="b0a86-119">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="b0a86-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="b0a86-120">O recurso é proveniente de **uap2** namespace.</span><span class="sxs-lookup"><span data-stu-id="b0a86-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="b0a86-121">Para obter acesso a esse namespace em seu manifesto, incluí-lo como um *xlmns* atributo no &lt;pacote > elemento.</span><span class="sxs-lookup"><span data-stu-id="b0a86-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="b0a86-122">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="b0a86-122">Here's an example:</span></span>

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="b0a86-123">**OBSERVAÇÃO:** Seu aplicativo precisará solicitar o recurso em tempo de execução antes que ele possa acessar SpatialAnchor importação/exportação de APIs.</span><span class="sxs-lookup"><span data-stu-id="b0a86-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="b0a86-124">Ver [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0a86-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="b0a86-125">Serializar os dados de âncora exportando-as com o SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="b0a86-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="b0a86-126">Uma função auxiliar está incluída no exemplo de código para exportar (serializar) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) dados.</span><span class="sxs-lookup"><span data-stu-id="b0a86-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="b0a86-127">Essa API exportação serializa todas as âncoras em uma coleção de pares chave-valor associando a âncoras de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b0a86-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

<span data-ttu-id="b0a86-128">Primeiro, precisamos configurar o fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="b0a86-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="b0a86-129">Isso nos permitirá como 1.) Use o TryExportAnchorsAsync para colocar os dados em um buffer de propriedade do aplicativo e 2). ler dados de fluxo de buffer de bytes exportado, que é um fluxo de dados do WinRT - em nosso próprio buffer de memória, que é um std:: Vector&lt;bytes >.</span><span class="sxs-lookup"><span data-stu-id="b0a86-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="b0a86-130">É necessário solicitar permissão para acessar os dados espaciais, incluindo as âncoras que são exportadas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="b0a86-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

<span data-ttu-id="b0a86-131">Se podemos obter permissão e âncoras são exportadas, podemos ler o fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="b0a86-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="b0a86-132">Aqui, também vamos mostrar como criar o DataReader e InputStream que usaremos para ler os dados.</span><span class="sxs-lookup"><span data-stu-id="b0a86-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="b0a86-133">Depois que lemos os bytes do fluxo, podemos pode salvá-los em nosso próprio buffer de dados da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="b0a86-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="b0a86-134">Desserializar dados de âncora por importá-los para o sistema usando o SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="b0a86-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="b0a86-135">Uma função auxiliar está incluída no exemplo de código para carregar dados exportados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b0a86-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="b0a86-136">Essa função de desserialização fornece uma coleção de pares chave-valor, semelhantes a que fornece o SpatialAnchorStore - exceto que obtivemos esses dados de outra origem, como um soquete de rede.</span><span class="sxs-lookup"><span data-stu-id="b0a86-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="b0a86-137">Você pode processar e ponderar sobre esses dados antes de armazená-lo offline, usando memória no aplicativo, ou (se aplicável) SpatialAnchorStore do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0a86-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

<span data-ttu-id="b0a86-138">Primeiro, precisamos criar objetos de fluxo para acessar os dados de âncora.</span><span class="sxs-lookup"><span data-stu-id="b0a86-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="b0a86-139">Podemos gravará os dados de nosso buffer em um buffer de sistema, portanto, vamos criar um DataWriter que grava em um fluxo de dados na memória para realizar a nossa meta de obter as âncoras de um buffer de bytes no sistema como SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="b0a86-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="b0a86-140">Mais uma vez, precisamos garantir que o aplicativo tem permissão para exportar os dados espaciais âncora, que pode incluir informações particulares sobre o ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0a86-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="b0a86-141">Se o acesso é permitido, podemos escrever bytes do buffer em um fluxo de dados do sistema.</span><span class="sxs-lookup"><span data-stu-id="b0a86-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

<span data-ttu-id="b0a86-142">Se estivéssemos bem-sucedido ao armazenar os bytes no fluxo de dados, podemos pode tentar importar dados usando o SpatialAnchorTransferManager.</span><span class="sxs-lookup"><span data-stu-id="b0a86-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

<span data-ttu-id="b0a86-143">Se os dados podem ser importados, obtemos uma exibição de mapa de pares chave-valor associando a âncoras de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b0a86-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="b0a86-144">Podemos carregar isso em nossa própria coleção de dados na memória e usar essa coleção para procurar as âncoras de que estamos interessados em usar.</span><span class="sxs-lookup"><span data-stu-id="b0a86-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

<span data-ttu-id="b0a86-145">**OBSERVAÇÃO:** Só porque você pode importar uma âncora, não significa necessariamente que você pode usá-lo imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b0a86-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="b0a86-146">A âncora pode estar em uma sala diferente, ou em outro local físico totalmente; a âncora não será localizáveis até que o dispositivo que ele a recebeu, tem informações suficientes visual sobre o ambiente que a âncora foi criada, para restaurar a posição da âncora em relação ao ambiente atual conhecido.</span><span class="sxs-lookup"><span data-stu-id="b0a86-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="b0a86-147">A implementação do cliente deve tentar localizar a âncora em relação ao seu sistema de coordenada local ou o quadro de referência antes de prosseguir tentar usá-lo para o conteúdo ao vivo.</span><span class="sxs-lookup"><span data-stu-id="b0a86-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="b0a86-148">Por exemplo, tente localizar a âncora em relação a um sistema de coordenadas atual periodicamente até que a âncora começa a ser localizado.</span><span class="sxs-lookup"><span data-stu-id="b0a86-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="b0a86-149">Considerações especiais</span><span class="sxs-lookup"><span data-stu-id="b0a86-149">Special Considerations</span></span>

<span data-ttu-id="b0a86-150">O [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API permite que vários [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) para ser exportada para o mesmo blob binário opaco.</span><span class="sxs-lookup"><span data-stu-id="b0a86-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="b0a86-151">No entanto, há uma diferença sutil na quais dados incluir o blob, dependendo do SpatialAnchor um único ou vários SpatialAnchors são exportados em uma única chamada.</span><span class="sxs-lookup"><span data-stu-id="b0a86-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="b0a86-152">Exportação de um único SpatialAnchor</span><span class="sxs-lookup"><span data-stu-id="b0a86-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="b0a86-153">O blob contém uma representação do ambiente de perto o SpatialAnchor para que o ambiente pode ser reconhecido no dispositivo que importa o SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="b0a86-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="b0a86-154">Depois que a importação for concluída, o novo SpatialAnchor estarão disponível para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b0a86-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="b0a86-155">Supondo que o usuário foi recentemente no ambiente de rede da âncora, ele será localizáveis e hologramas anexadas para o SpatialAnchor podem ser renderizadas.</span><span class="sxs-lookup"><span data-stu-id="b0a86-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="b0a86-156">Esses hologramas aparecerão no mesmo local físico que ele realizou no dispositivo original que exportou o SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="b0a86-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![Exportação de um único SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="b0a86-158">Exportação de vários SpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="b0a86-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="b0a86-159">Como a exportação de um único SpatialAnchor, o blob contém uma representação do ambiente perto todos os SpatialAnchors especificados.</span><span class="sxs-lookup"><span data-stu-id="b0a86-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="b0a86-160">Além disso, o blob contém informações sobre as conexões entre o SpatialAnchors incluído, se eles estiverem localizados no mesmo espaço físico.</span><span class="sxs-lookup"><span data-stu-id="b0a86-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="b0a86-161">Isso significa que se SpatialAnchors próximos dois são importados, em seguida, um holograma anexado à *segundo* SpatialAnchor seria localizáveis, mesmo se o dispositivo reconhece apenas o ambiente em torno de *primeiro* SpatialAnchor, porque há dados suficientes para computação transform entre os dois SpatialAnchors foi incluído no blob.</span><span class="sxs-lookup"><span data-stu-id="b0a86-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="b0a86-162">Se os dois SpatialAnchors foram exportados individualmente (duas chamadas separam para TryExportSpatialAnchors) e em seguida, pode não haver dados suficientes incluídos no blob para hologramas anexados para o segundo SpatialAnchor poderá ser localizáveis quando o primeiro deles estão localizados.</span><span class="sxs-lookup"><span data-stu-id="b0a86-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![Várias âncoras exportadas usando uma única chamada de TryExportAnchorsAsync](images/multipleanchors.png) ![Várias âncoras exportadas usando uma chamada TryExportAnchorsAsync separada para cada âncora](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="b0a86-165">Exemplo: Enviar dados de âncora usando um Windows::Networking::StreamSocket</span><span class="sxs-lookup"><span data-stu-id="b0a86-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="b0a86-166">Aqui, fornecemos um exemplo de como usar os dados exportados de âncora, enviando-as em uma rede TCP.</span><span class="sxs-lookup"><span data-stu-id="b0a86-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="b0a86-167">Isso é do HolographicSpatialAnchorTransferSample.</span><span class="sxs-lookup"><span data-stu-id="b0a86-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="b0a86-168">A classe StreamSocket do WinRT usa a biblioteca de tarefas PPL.</span><span class="sxs-lookup"><span data-stu-id="b0a86-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="b0a86-169">No caso de erros de rede, o erro é retornado para a próxima tarefa na cadeia usando uma exceção que é lançada novamente.</span><span class="sxs-lookup"><span data-stu-id="b0a86-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="b0a86-170">A exceção contém um HRESULT que indica o status de erro.</span><span class="sxs-lookup"><span data-stu-id="b0a86-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="b0a86-171">Usar um Windows::Networking::StreamSocketListener com TCP para enviar os dados exportados de âncora</span><span class="sxs-lookup"><span data-stu-id="b0a86-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="b0a86-172">Crie uma instância de servidor que escuta para uma conexão.</span><span class="sxs-lookup"><span data-stu-id="b0a86-172">Create a server instance that listens for a connection.</span></span>

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

<span data-ttu-id="b0a86-173">Quando uma conexão é recebida, use a conexão de soquete de cliente para enviar dados de âncora.</span><span class="sxs-lookup"><span data-stu-id="b0a86-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

<span data-ttu-id="b0a86-174">Agora, podemos começar a enviar uma transmissão de dados que contém os dados exportados de âncora.</span><span class="sxs-lookup"><span data-stu-id="b0a86-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

<span data-ttu-id="b0a86-175">Para que possa enviar o próprio fluxo, vamos primeiro deve enviar um pacote de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="b0a86-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="b0a86-176">Esse pacote de cabeçalho deve ser de comprimento fixo, e ele também deve indicar o comprimento da matriz de bytes de variável que é o fluxo de dados de âncora; no caso deste exemplo não temos outros cabeçalho dados para enviar, então, nosso cabeçalho 4 bytes de comprimento e contém um inteiro sem sinal de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b0a86-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

<span data-ttu-id="b0a86-177">Depois que o comprimento do fluxo, em bytes, foi enviado ao cliente, poderemos continuar para gravar o fluxo de dados no fluxo de soquete.</span><span class="sxs-lookup"><span data-stu-id="b0a86-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="b0a86-178">Isso fará com que os bytes de armazenamento de âncora sejam enviados ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b0a86-178">This will cause the anchor store bytes to get sent to the client.</span></span>

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

<span data-ttu-id="b0a86-179">Conforme observado no início deste tópico, devemos estar preparados para lidar com exceções que contém mensagens de status de erro de rede.</span><span class="sxs-lookup"><span data-stu-id="b0a86-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="b0a86-180">Para erros que não são esperados, podemos escrever as informações de exceção para o console de depuração da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="b0a86-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="b0a86-181">Isso nos dará uma dica em relação o que aconteceu se nossa amostra de código não conseguiu concluir a conexão, ou se não for possível terminou de enviar os dados de âncora.</span><span class="sxs-lookup"><span data-stu-id="b0a86-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="b0a86-182">Usar um Windows::Networking::StreamSocket com TCP para receber os dados exportados de âncora</span><span class="sxs-lookup"><span data-stu-id="b0a86-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="b0a86-183">Primeiro, precisamos conectar ao servidor.</span><span class="sxs-lookup"><span data-stu-id="b0a86-183">First, we have to connect to the server.</span></span> <span data-ttu-id="b0a86-184">Este exemplo de código mostra como criar e configurar um StreamSocket e criar um DataReader que você pode usar para adquirir dados de rede usando a conexão de soquete.</span><span class="sxs-lookup"><span data-stu-id="b0a86-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="b0a86-185">**OBSERVAÇÃO:** Se você executar esse código de exemplo, certifique-se de que você configure e inicie o servidor antes de iniciar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b0a86-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

<span data-ttu-id="b0a86-186">Assim que tivermos uma conexão, podemos esperar para o servidor enviar dados.</span><span class="sxs-lookup"><span data-stu-id="b0a86-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="b0a86-187">Fazemos isso chamando LoadAsync no leitor de fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="b0a86-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="b0a86-188">O primeiro conjunto de bytes que recebemos sempre deve ser o pacote de cabeçalho, que indica o que comprimento em bytes do fluxo de dados a âncora conforme descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="b0a86-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

<span data-ttu-id="b0a86-189">...</span><span class="sxs-lookup"><span data-stu-id="b0a86-189">...</span></span>

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

<span data-ttu-id="b0a86-190">Depois de recebermos o pacote de cabeçalho, nós sabemos quantos bytes de dados de âncora, devemos esperar.</span><span class="sxs-lookup"><span data-stu-id="b0a86-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="b0a86-191">Podemos pode prosseguir para os bytes lidos do fluxo.</span><span class="sxs-lookup"><span data-stu-id="b0a86-191">We can proceed to read those bytes from the stream.</span></span>

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

<span data-ttu-id="b0a86-192">Aqui está nosso código para receber o fluxo de dados de âncora.</span><span class="sxs-lookup"><span data-stu-id="b0a86-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="b0a86-193">Novamente, estamos será carregado primeiro os bytes do fluxo; Essa operação pode levar algum tempo para ser concluída conforme o StreamSocket espera para receber essa quantidade de bytes de rede.</span><span class="sxs-lookup"><span data-stu-id="b0a86-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="b0a86-194">Quando a operação de carregamento for concluída, podemos ler esse número de bytes.</span><span class="sxs-lookup"><span data-stu-id="b0a86-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="b0a86-195">Se recebemos o número de bytes que esperamos âncora fluxo de dados, podemos ir em frente e importar os dados de âncora; Caso contrário, deve ter havido algum tipo de erro.</span><span class="sxs-lookup"><span data-stu-id="b0a86-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="b0a86-196">Por exemplo, isso pode acontecer quando a instância do servidor for encerrado antes que ele pode terminou de enviar o fluxo de dados ou a rede fica inoperante antes que o fluxo de dados inteira pode ser recebido pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="b0a86-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

<span data-ttu-id="b0a86-197">Novamente, devemos estar preparados para lidar com erros de rede desconhecido.</span><span class="sxs-lookup"><span data-stu-id="b0a86-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="b0a86-198">É só isso!</span><span class="sxs-lookup"><span data-stu-id="b0a86-198">That's it!</span></span> <span data-ttu-id="b0a86-199">Agora, você deve ter informações suficientes para tentar localizar as âncoras recebidas pela rede.</span><span class="sxs-lookup"><span data-stu-id="b0a86-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="b0a86-200">Novamente, observe que o cliente deve ter dados suficientes acompanhamento visual para o espaço a ser localizado com êxito a âncora; Se não funcionar imediatamente, tente andando por algum tempo.</span><span class="sxs-lookup"><span data-stu-id="b0a86-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="b0a86-201">Se ainda não funcionar, ter o servidor enviar mais âncoras e usar as comunicações de rede concordar sobre o que funciona para o cliente.</span><span class="sxs-lookup"><span data-stu-id="b0a86-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="b0a86-202">Você pode experimentar isso baixando o HolographicSpatialAnchorTransferSample, configuração de IPs de servidor e cliente e implantá-lo em dispositivos do HoloLens cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="b0a86-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0a86-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0a86-203">See also</span></span>
* [<span data-ttu-id="b0a86-204">Biblioteca de padrões paralelos (PPL)</span><span class="sxs-lookup"><span data-stu-id="b0a86-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="b0a86-205">Windows.Networking.StreamSocket</span><span class="sxs-lookup"><span data-stu-id="b0a86-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="b0a86-206">Windows.Networking.StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="b0a86-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)

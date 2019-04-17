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
# <a name="local-anchor-transfers-in-directx"></a>Transferências de local de âncora no DirectX

Em situações em que você não pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, transferências de local de ancoragem permitem que um dispositivo de HoloLens exportar uma âncora para ser importado por um segundo dispositivo HoloLens.

>[!NOTE]
>As transferências de âncora local fornecem o recall de âncora menos robusta do que <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, e não há suporte para dispositivos iOS e Android por essa abordagem.

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

## <a name="transferring-spatial-anchors"></a>Transferindo âncoras espaciais

Você pode transferir âncoras espaciais entre dispositivos de realidade mista do Windows usando o [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Essa API permite reunir uma âncora com todos os dados de sensor suporte necessários para localizar o local exato no mundo e, em seguida, importar esse pacote em outro dispositivo. Depois que o aplicativo no segundo dispositivo tiver importado que ancoram, cada aplicativo pode processar hologramas usando que compartilhados do sistema de coordenadas da âncora espacial, que, em seguida, será exibida no mesmo lugar no mundo real.

Observe que âncoras espaciais não são capazes de transferir entre tipos diferentes de dispositivos, por exemplo uma âncora de espacial HoloLens pode não ser localizáveis usando um fone de ouvido envolvente.  Âncoras transferidas também não são compatíveis com dispositivos iOS ou Android.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurar seu aplicativo para usar o recurso de spatialPerception

Seu aplicativo deve ter a permissão para usar o recurso de spatialPerception antes de poder usar o [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Isso é necessário porque a transferência de uma âncora espacial envolve compartilhando imagens de sensor coletadas ao longo do tempo na vizinhança dessa âncora, que pode incluir informações confidenciais.

Declare esse recurso no arquivo Package. appxmanifest para seu aplicativo. Veja um exemplo:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

O recurso é proveniente de **uap2** namespace. Para obter acesso a esse namespace em seu manifesto, incluí-lo como um *xlmns* atributo no &lt;pacote > elemento. Veja um exemplo:

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**OBSERVAÇÃO:** Seu aplicativo precisará solicitar o recurso em tempo de execução antes que ele possa acessar SpatialAnchor importação/exportação de APIs. Ver [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) nos exemplos a seguir.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serializar os dados de âncora exportando-as com o SpatialAnchorTransferManager

Uma função auxiliar está incluída no exemplo de código para exportar (serializar) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) dados. Essa API exportação serializa todas as âncoras em uma coleção de pares chave-valor associando a âncoras de cadeias de caracteres.

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

Primeiro, precisamos configurar o fluxo de dados. Isso nos permitirá como 1.) Use o TryExportAnchorsAsync para colocar os dados em um buffer de propriedade do aplicativo e 2). ler dados de fluxo de buffer de bytes exportado, que é um fluxo de dados do WinRT - em nosso próprio buffer de memória, que é um std:: Vector&lt;bytes >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

É necessário solicitar permissão para acessar os dados espaciais, incluindo as âncoras que são exportadas pelo sistema.

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

Se podemos obter permissão e âncoras são exportadas, podemos ler o fluxo de dados. Aqui, também vamos mostrar como criar o DataReader e InputStream que usaremos para ler os dados.

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

Depois que lemos os bytes do fluxo, podemos pode salvá-los em nosso próprio buffer de dados da seguinte forma.

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Desserializar dados de âncora por importá-los para o sistema usando o SpatialAnchorTransferManager

Uma função auxiliar está incluída no exemplo de código para carregar dados exportados anteriormente. Essa função de desserialização fornece uma coleção de pares chave-valor, semelhantes a que fornece o SpatialAnchorStore - exceto que obtivemos esses dados de outra origem, como um soquete de rede. Você pode processar e ponderar sobre esses dados antes de armazená-lo offline, usando memória no aplicativo, ou (se aplicável) SpatialAnchorStore do seu aplicativo.

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

Primeiro, precisamos criar objetos de fluxo para acessar os dados de âncora. Podemos gravará os dados de nosso buffer em um buffer de sistema, portanto, vamos criar um DataWriter que grava em um fluxo de dados na memória para realizar a nossa meta de obter as âncoras de um buffer de bytes no sistema como SpatialAnchors.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Mais uma vez, precisamos garantir que o aplicativo tem permissão para exportar os dados espaciais âncora, que pode incluir informações particulares sobre o ambiente do usuário.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Se o acesso é permitido, podemos escrever bytes do buffer em um fluxo de dados do sistema.

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

Se estivéssemos bem-sucedido ao armazenar os bytes no fluxo de dados, podemos pode tentar importar dados usando o SpatialAnchorTransferManager.

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

Se os dados podem ser importados, obtemos uma exibição de mapa de pares chave-valor associando a âncoras de cadeias de caracteres. Podemos carregar isso em nossa própria coleção de dados na memória e usar essa coleção para procurar as âncoras de que estamos interessados em usar.

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

**OBSERVAÇÃO:** Só porque você pode importar uma âncora, não significa necessariamente que você pode usá-lo imediatamente. A âncora pode estar em uma sala diferente, ou em outro local físico totalmente; a âncora não será localizáveis até que o dispositivo que ele a recebeu, tem informações suficientes visual sobre o ambiente que a âncora foi criada, para restaurar a posição da âncora em relação ao ambiente atual conhecido. A implementação do cliente deve tentar localizar a âncora em relação ao seu sistema de coordenada local ou o quadro de referência antes de prosseguir tentar usá-lo para o conteúdo ao vivo. Por exemplo, tente localizar a âncora em relação a um sistema de coordenadas atual periodicamente até que a âncora começa a ser localizado.

## <a name="special-considerations"></a>Considerações especiais

O [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API permite que vários [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) para ser exportada para o mesmo blob binário opaco. No entanto, há uma diferença sutil na quais dados incluir o blob, dependendo do SpatialAnchor um único ou vários SpatialAnchors são exportados em uma única chamada.

### <a name="export-of-a-single-spatialanchor"></a>Exportação de um único SpatialAnchor

O blob contém uma representação do ambiente de perto o SpatialAnchor para que o ambiente pode ser reconhecido no dispositivo que importa o SpatialAnchor. Depois que a importação for concluída, o novo SpatialAnchor estarão disponível para o dispositivo. Supondo que o usuário foi recentemente no ambiente de rede da âncora, ele será localizáveis e hologramas anexadas para o SpatialAnchor podem ser renderizadas. Esses hologramas aparecerão no mesmo local físico que ele realizou no dispositivo original que exportou o SpatialAnchor.

![Exportação de um único SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Exportação de vários SpatialAnchors

Como a exportação de um único SpatialAnchor, o blob contém uma representação do ambiente perto todos os SpatialAnchors especificados. Além disso, o blob contém informações sobre as conexões entre o SpatialAnchors incluído, se eles estiverem localizados no mesmo espaço físico. Isso significa que se SpatialAnchors próximos dois são importados, em seguida, um holograma anexado à *segundo* SpatialAnchor seria localizáveis, mesmo se o dispositivo reconhece apenas o ambiente em torno de *primeiro* SpatialAnchor, porque há dados suficientes para computação transform entre os dois SpatialAnchors foi incluído no blob. Se os dois SpatialAnchors foram exportados individualmente (duas chamadas separam para TryExportSpatialAnchors) e em seguida, pode não haver dados suficientes incluídos no blob para hologramas anexados para o segundo SpatialAnchor poderá ser localizáveis quando o primeiro deles estão localizados.

![Várias âncoras exportadas usando uma única chamada de TryExportAnchorsAsync](images/multipleanchors.png) ![Várias âncoras exportadas usando uma chamada TryExportAnchorsAsync separada para cada âncora](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Exemplo: Enviar dados de âncora usando um Windows::Networking::StreamSocket

Aqui, fornecemos um exemplo de como usar os dados exportados de âncora, enviando-as em uma rede TCP. Isso é do HolographicSpatialAnchorTransferSample.

A classe StreamSocket do WinRT usa a biblioteca de tarefas PPL. No caso de erros de rede, o erro é retornado para a próxima tarefa na cadeia usando uma exceção que é lançada novamente. A exceção contém um HRESULT que indica o status de erro.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Usar um Windows::Networking::StreamSocketListener com TCP para enviar os dados exportados de âncora

Crie uma instância de servidor que escuta para uma conexão.

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

Quando uma conexão é recebida, use a conexão de soquete de cliente para enviar dados de âncora.

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

Agora, podemos começar a enviar uma transmissão de dados que contém os dados exportados de âncora.

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

Para que possa enviar o próprio fluxo, vamos primeiro deve enviar um pacote de cabeçalho. Esse pacote de cabeçalho deve ser de comprimento fixo, e ele também deve indicar o comprimento da matriz de bytes de variável que é o fluxo de dados de âncora; no caso deste exemplo não temos outros cabeçalho dados para enviar, então, nosso cabeçalho 4 bytes de comprimento e contém um inteiro sem sinal de 32 bits.

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

Depois que o comprimento do fluxo, em bytes, foi enviado ao cliente, poderemos continuar para gravar o fluxo de dados no fluxo de soquete. Isso fará com que os bytes de armazenamento de âncora sejam enviados ao cliente.

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

Conforme observado no início deste tópico, devemos estar preparados para lidar com exceções que contém mensagens de status de erro de rede. Para erros que não são esperados, podemos escrever as informações de exceção para o console de depuração da seguinte forma. Isso nos dará uma dica em relação o que aconteceu se nossa amostra de código não conseguiu concluir a conexão, ou se não for possível terminou de enviar os dados de âncora.

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Usar um Windows::Networking::StreamSocket com TCP para receber os dados exportados de âncora

Primeiro, precisamos conectar ao servidor. Este exemplo de código mostra como criar e configurar um StreamSocket e criar um DataReader que você pode usar para adquirir dados de rede usando a conexão de soquete.

**OBSERVAÇÃO:** Se você executar esse código de exemplo, certifique-se de que você configure e inicie o servidor antes de iniciar o cliente.

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

Assim que tivermos uma conexão, podemos esperar para o servidor enviar dados. Fazemos isso chamando LoadAsync no leitor de fluxo de dados.

O primeiro conjunto de bytes que recebemos sempre deve ser o pacote de cabeçalho, que indica o que comprimento em bytes do fluxo de dados a âncora conforme descrito na seção anterior.

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

...

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

Depois de recebermos o pacote de cabeçalho, nós sabemos quantos bytes de dados de âncora, devemos esperar. Podemos pode prosseguir para os bytes lidos do fluxo.

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

Aqui está nosso código para receber o fluxo de dados de âncora. Novamente, estamos será carregado primeiro os bytes do fluxo; Essa operação pode levar algum tempo para ser concluída conforme o StreamSocket espera para receber essa quantidade de bytes de rede.

Quando a operação de carregamento for concluída, podemos ler esse número de bytes. Se recebemos o número de bytes que esperamos âncora fluxo de dados, podemos ir em frente e importar os dados de âncora; Caso contrário, deve ter havido algum tipo de erro. Por exemplo, isso pode acontecer quando a instância do servidor for encerrado antes que ele pode terminou de enviar o fluxo de dados ou a rede fica inoperante antes que o fluxo de dados inteira pode ser recebido pelo cliente.

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

Novamente, devemos estar preparados para lidar com erros de rede desconhecido.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

É só isso! Agora, você deve ter informações suficientes para tentar localizar as âncoras recebidas pela rede. Novamente, observe que o cliente deve ter dados suficientes acompanhamento visual para o espaço a ser localizado com êxito a âncora; Se não funcionar imediatamente, tente andando por algum tempo. Se ainda não funcionar, ter o servidor enviar mais âncoras e usar as comunicações de rede concordar sobre o que funciona para o cliente. Você pode experimentar isso baixando o HolographicSpatialAnchorTransferSample, configuração de IPs de servidor e cliente e implantá-lo em dispositivos do HoloLens cliente e servidor.

## <a name="see-also"></a>Consulte também
* [Biblioteca de padrões paralelos (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows.Networking.StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows.Networking.StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)

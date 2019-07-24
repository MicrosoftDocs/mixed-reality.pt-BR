---
title: Mapeamento espacial no DirectX
description: Explica como implementar o mapeamento espacial em seu aplicativo DirectX. Isso inclui uma explicação detalhada do aplicativo de exemplo de mapeamento espacial incluído no SDK do Plataforma Universal do Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, mapeamento espacial, ambiente, interação, DirectX, winrt, API, código de exemplo, UWP, SDK, passo a passos
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550690"
---
# <a name="spatial-mapping-in-directx"></a>Mapeamento espacial no DirectX

Este tópico descreve como implementar o [mapeamento espacial](spatial-mapping.md) em seu aplicativo DirectX. Isso inclui uma explicação detalhada do aplicativo de exemplo de mapeamento espacial incluído no SDK do Plataforma Universal do Windows.

Este tópico usa código do exemplo de código [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP.

>[!NOTE]
>Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.

## <a name="directx-development-overview"></a>Visão geral de desenvolvimento do DirectX

O desenvolvimento de aplicativos nativos para o mapeamento espacial usa as APIs no namespace [Windows. percepção. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) . Essas APIs fornecem controle total da funcionalidade de mapeamento espacial, de uma maneira diretamente análoga às APIs de mapeamento espacial expostas pelo [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>APIs de percepção

Os tipos primários fornecidos para o desenvolvimento de mapeamentos espaciais são os seguintes:
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornece informações sobre superfícies em regiões especificadas pelo aplicativo de espaço próximo ao usuário, na forma de objetos SpatialSurfaceInfo.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descreve uma superfície espacial existentes única, incluindo uma ID exclusiva, o volume delimitador e a hora da última alteração. Ele fornecerá um SpatialSurfaceMesh de forma assíncrona após a solicitação.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contém parâmetros usados para personalizar os objetos SpatialSurfaceMesh solicitados de SpatialSurfaceInfo.
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa os dados de malha de uma única superfície espacial. Os dados para posições de vértice, normais de vértice e índices de triângulo estão contidos em objetos member SpatialSurfaceMeshBuffer.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) encapsula um único tipo de dados de malha.

Ao desenvolver um aplicativo usando essas APIs, o fluxo de programa básico terá esta aparência (conforme demonstrado no aplicativo de exemplo descrito abaixo):
- **Configurar seu SpatialSurfaceObserver**
  - Chame [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)para garantir que o usuário tenha concedido permissão para que seu aplicativo use os recursos de mapeamento espacial do dispositivo.
  - Crie uma instância de um objeto SpatialSurfaceObserver.
  - Chame [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar as regiões de espaço nas quais você deseja obter informações sobre superfícies espaciais. Você pode modificar essas regiões no futuro simplesmente chamando essa função novamente. Cada região é especificada usando um [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Registre-se no evento [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , que será acionado sempre que novas informações estiverem disponíveis sobre as superfícies espaciais nas regiões de espaço que você especificou.
- **Processar eventos ObservedSurfacesChanged**
  - Em seu manipulador de eventos, chame [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para receber um mapa de objetos SpatialSurfaceInfo. Usando esse mapa, você pode atualizar os registros dos quais as superfícies espaciais [existem no ambiente do usuário](spatial-mapping.md#mesh-caching).
  - Para cada objeto SpatialSurfaceInfo, você pode consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) para determinar as extensões espaciais da superfície, expressas em um [sistema de coordenadas espaciais](coordinate-systems.md) de sua escolha.
  - Se você decidir solicitar malha para uma superfície espacial, chame [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). Você pode fornecer opções especificando a densidade desejada de triângulos e o formato dos dados de malha retornados.
- **Receber e processar malha**
  - Cada chamada para TryComputeLatestMeshAsync irá aysnchronously retornar um objeto SpatialSurfaceMesh.
  - Desse objeto, você pode acessar os objetos SpatialSurfaceMeshBuffer contidos para acessar os índices de triângulo, as posições de vértice e (se solicitado) vértices normais da malha. Esses dados estarão em um formato diretamente compatível com as [APIs do Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usadas para renderizar malhas.
  - A partir daqui, o aplicativo pode opcionalmente executar a análise ou o [processamento](spatial-mapping.md#mesh-processing) dos dados de malha e usá-lo para [renderização](spatial-mapping.md#rendering) e [raycasting física e colisão](spatial-mapping.md#raycasting-and-collision).
  - Um detalhe importante a ser observado é que você deve aplicar uma escala às posições de vértice de malha (por exemplo, no sombreador de vértice usado para renderizar as malhas), para convertê-las das unidades de inteiros otimizadas nas quais elas são armazenadas no buffer, em metros. Você pode recuperar essa escala chamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Solução de problemas
* Não se esqueça de dimensionar as posições de vértice de malha em seu sombreador de vértice, usando a escala retornada por [SpatialSurfaceMesh. VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Instruções de exemplo de código de mapeamento espacial

O exemplo de código de [mapeamento espacial Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) inclui o código que você pode usar para começar a carregar malhas de superfície em seu aplicativo, incluindo a infraestrutura para gerenciar e renderizar malhas de superfície.

Agora, vamos examinar como adicionar o recurso de mapeamento de superfície ao seu aplicativo DirectX. Você pode adicionar esse código ao seu projeto de [modelo de aplicativo Holographic do Windows](creating-a-holographic-directx-project.md) ou pode acompanhar navegando pelo exemplo de código mencionado acima. Este exemplo de código é baseado no modelo de aplicativo Holographic do Windows.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurar seu aplicativo para usar o recurso spatialPerception

Seu aplicativo deve ser capaz de usar o recurso de mapeamento espacial. Isso é necessário porque a malha espacial é uma representação do ambiente do usuário, que pode ser considerado dados privados. Declare esse recurso no arquivo Package. appxmanifest para seu aplicativo. Veja um exemplo:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

A funcionalidade vem do namespace **uap2** . Para obter acesso a esse namespace em seu manifesto, inclua-o como um atributo *xlmns* no &lt;elemento > do pacote. Veja um exemplo:

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Verificar o suporte a recursos de mapeamento espacial

O Windows Mixed Reality dá suporte a uma ampla variedade de dispositivos, incluindo dispositivos que não dão suporte ao mapeamento espacial. Se seu aplicativo pode usar o mapeamento espacial ou deve usar o mapeamento espacial, para fornecer funcionalidade, ele deve verificar se há suporte para o mapeamento espacial antes de tentar usá-lo. Por exemplo, se o mapeamento espacial for exigido pelo seu aplicativo de realidade misturada, ele deverá exibir uma mensagem para esse efeito se um usuário tentar executá-lo em um dispositivo sem o mapeamento espacial. Ou, seu aplicativo pode ser capaz de renderizar seu próprio ambiente virtual no lugar do ambiente do usuário, fornecendo uma experiência semelhante ao que aconteceria se o mapeamento espacial estivesse disponível. Em qualquer evento, essa API permite que seu aplicativo fique atento quando não obter dados de mapeamento espacial e responder da maneira apropriada.

Para verificar o dispositivo atual quanto ao suporte de mapeamento espacial, primeiro verifique se o contrato UWP está no nível 4 ou superior e, em seguida, chame SpatialSurfaceObserver:: IsSupported (). Veja como fazer isso no contexto do exemplo de código de [mapeamento espacial do Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) . O suporte é verificado logo antes de solicitar acesso.

A API SpatialSurfaceObserver:: IsSupported () está disponível a partir da versão 15063 do SDK. Se necessário, redirecione seu projeto para a versão da plataforma 15063 antes de usar essa API.

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

Observe que, quando o contrato UWP é menor que o nível 4, o aplicativo deve continuar como se o dispositivo fosse capaz de fazer o mapeamento espacial.

### <a name="request-access-to-spatial-mapping-data"></a>Solicitar acesso aos dados de mapeamento espacial

Seu aplicativo precisa solicitar permissão para acessar dados de mapeamento espacial antes de tentar criar qualquer observador de superfície. Veja um exemplo com base no exemplo de código de mapeamento de superfície, com mais detalhes fornecidos mais adiante nesta página:

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Criar um observador de superfície

O namespace **Windows::P erception:: Spatial:: superfícies** inclui a classe [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , que observa um ou mais volumes que você especifica em um [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Use uma instância de [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) para acessar dados de malha de superfície em tempo real.

De **AppMain. h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Conforme observado na seção anterior, você deve solicitar acesso aos dados de mapeamento espacial antes que seu aplicativo possa usá-lo. Esse acesso é concedido automaticamente no HoloLens.

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

Em seguida, você precisa configurar o observador de superfície para observar um volume delimitador específico. Aqui, observamos uma caixa que é 20x20x5 metros, centralizada na origem do sistema de coordenadas.

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

Observe que você pode definir vários volumes delimitadores em vez disso.

*Este é o pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

Também é possível usar outras formas delimitadoras, como uma exibição frustum, ou uma caixa delimitadora que não esteja alinhada ao eixo.

*Este é o pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Se seu aplicativo precisar fazer algo diferente quando os dados de mapeamento de superfície não estiverem disponíveis, você poderá escrever código para responder ao caso em que o [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) não é **permitido** ; por exemplo, ele não será permitido em PCs com imersão dispositivos anexados porque esses dispositivos não têm hardware para mapeamento espacial. Para esses dispositivos, você deve confiar no estágio espacial para obter informações sobre a configuração do ambiente e do dispositivo do usuário.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inicializar e atualizar a coleção de malha da superfície

Se o observador de superfície foi criado com êxito, podemos continuar a inicializar nossa coleção de malha de superfície. Aqui, usamos a API do modelo de pull para obter o conjunto atual de superfícies observadas imediatamente:

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

Há também um modelo de push disponível para obter dados de malha de superfície. Você tem a liberdade de criar seu aplicativo para usar apenas o modelo de pull se escolher, caso em que você vai sondar os dados a cada hora, com frequência, uma vez por quadro ou durante um período de tempo específico, como durante a configuração do jogo. Nesse caso, o código acima é o que você precisa.

Em nosso exemplo de código, optamos por demonstrar o uso de ambos os modelos para fins de pedagógicos. Aqui, assinamos um evento para receber dados de malha de superfície atualizados sempre que o sistema reconhece uma alteração.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Nosso exemplo de código também é configurado para responder a esses eventos. Vamos examinar como fazemos isso.

**OBSERVAÇÃO:** Essa pode não ser a maneira mais eficiente para seu aplicativo manipular dados de malha. Esse código é escrito para fins de clareza e não é otimizado.

Os dados de malha de superfície são fornecidos em um mapa somente leitura que armazena objetos [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) usando [Platform:: GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de chave.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Para processar esses dados, examinamos primeiro os valores de chave que não estão em nossa coleção. Os detalhes sobre como os dados são armazenados em nosso aplicativo de exemplo serão apresentados posteriormente neste tópico.

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

Também precisamos remover as malhas de superfície que estão em nossa coleção de malha de superfície, mas que não estão mais na coleção do sistema. Para fazer isso, precisamos fazer algo semelhante ao oposto do que acabamos de mostrar para adicionar e atualizar malhas; Fazemos um loop sobre a coleção do aplicativo e verificamos se o **GUID** que temos está na coleção System. Se não estiver na coleção do sistema, remova-o da nossa.

Do nosso manipulador de eventos em AppMain. cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

A implementação da remoção de malha no RealtimeSurfaceMeshRenderer. cpp:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Adquirir e usar buffers de dados de malha de superfície

Obter as informações de malha de superfície era tão fácil quanto extrair uma coleta de dados e processar atualizações para essa coleção. Agora, entraremos em detalhes sobre como você pode usar os dados.

Em nosso exemplo de código, optamos por usar as malhas de superfície para renderização. Esse é um cenário comum para os hologramas occluding por trás das superfícies do mundo real. Você também pode renderizar as malhas ou renderizar as versões processadas delas para mostrar ao usuário quais áreas da sala são verificadas antes de começar a fornecer a funcionalidade do aplicativo ou do jogo.

O exemplo de código inicia o processo quando recebe atualizações de malha de superfície do manipulador de eventos que descrevemos na seção anterior. A linha importante de código nessa função é a chamada para atualizar a *malha*de superfície: neste momento, já processamos as informações de malha e estamos prestes a obter os dados de vértice e de índice para uso, como vemos.

De RealtimeSurfaceMeshRenderer. cpp:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

Nosso código de exemplo foi projetado para que uma classe de dados, **SurfaceMesh**, lide com processamento e renderização de dados de malha. Essas malhas são o que o **RealtimeSurfaceMeshRenderer** realmente mantém um mapa. Cada um tem uma referência para o SpatialSurfaceMesh de origem e nós o usamos sempre que precisamos acessar o vértice de malha ou buffers de índice, ou obter uma transformação para a malha. Por enquanto, sinalizamos a malha como precisa de uma atualização.

De SurfaceMesh. cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Na próxima vez que a malha for solicitada a desenhar, ela verificará o sinalizador primeiro. Se uma atualização for necessária, os buffers de vértice e de índice serão atualizados na GPU.

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

Primeiro, adquirimos os buffers de dados brutos:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Em seguida, criamos buffers de dispositivo Direct3D com os dados de malha fornecidos pelo HoloLens:

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**OBSERVAÇÃO:** Para a função auxiliar CreateDirectXBuffer usada no trecho anterior, consulte o exemplo de código de mapeamento de superfície: SurfaceMesh. cpp, GetDataFromIBuffer. h. Agora a criação do recurso do dispositivo está concluída e a malha é considerada como carregada e pronta para atualização e renderização.

### <a name="update-and-render-surface-meshes"></a>Atualizar e renderizar malhas de superfície

Nossa classe SurfaceMesh tem uma função de atualização especializada. Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tem sua própria transformação, e nosso exemplo usa o sistema de coordenadas atual para nosso **SpatialStationaryReferenceFrame** para adquirir a transformação. Em seguida, ele atualiza o buffer de constante do modelo na GPU.

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

Quando é hora de renderizar malhas de superfície, fazemos um trabalho de preparação antes de renderizar a coleção. Configuramos o pipeline do sombreador para a configuração de renderização atual e configuramos o estágio do assembler de entrada. Observe que a classe auxiliar da câmera Holographic **CameraResources. cpp** já configurou o buffer constante de exibição/projeção agora.

De **RealtimeSurfaceMeshRenderer:: render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

Quando isso for feito, vamos fazer um loop em nossas malhas e dizer a cada uma delas para se desenhar. **OBSERVAÇÃO:** Este código de exemplo não é otimizado para usar qualquer tipo de remoção de frustum, mas você deve incluir esse recurso em seu aplicativo.

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

As malhas individuais são responsáveis pela configuração do vértice e do buffer de índice, Stride e buffer constante de transformação de modelo. Assim como no cubo de rotação no modelo de aplicativo Holographic do Windows, renderizamos para buffers estereoscópico usando instanciação.

De **SurfaceMesh::D bruto**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>Opções de renderização com mapeamento de superfície

O exemplo de código de mapeamento de superfície oferece código para renderização oclusão de dados de malha de superfície e para renderização na tela de dados de malha de superfície. Qual caminho você escolhe-ou ambos-depende do seu aplicativo. Vamos percorrer as duas configurações deste documento.

**Renderizando buffers oclusão para efeito Holographic**

Comece limpando a exibição de destino de renderização para a câmera virtual atual.

De AppMain. cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Essa é uma passagem de "pré-processamento". Aqui, criamos um buffer oclusão solicitando que o processador de malha processe apenas a profundidade. Nessa configuração, não anexamos uma exibição de destino de renderização e o processador de malha define o estágio do sombreador de pixel como **nullptr** para que a GPU não se preocupe em desenhar pixels. A geometria será rasterizada para o buffer de profundidade e o pipeline de gráficos será interrompido.

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

Podemos desenhar hologramas com um teste de profundidade extra em relação ao buffer oclusão de mapeamento de superfície. Neste exemplo de código, renderizaremos pixels no cubo em uma cor diferente se estiverem atrás de uma superfície.

De AppMain. cpp:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

Com base no código de SpecialEffectPixelShader. HLSL:

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**Observação:** Para nossa rotina **GatherDepthLess** , consulte o exemplo de código de mapeamento de superfície: SpecialEffectPixelShader. HLSL.

**Renderizando dados de malha da superfície para a exibição**

Também podemos simplesmente desenhar as malhas de superfície para os buffers de vídeo estéreo. Optamos por desenhar faces completas com iluminação, mas você está livre para desenhar wireframe, processar malhas antes de renderizar, aplicar um mapa de textura e assim por diante.

Aqui, nosso exemplo de código diz ao renderizador de malha para desenhar a coleção. Desta vez, não especificamos uma passagem somente de profundidade, portanto, ele anexará um sombreador de pixel e concluirá o pipeline de renderização usando os destinos que especificamos para a câmera virtual atual.

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Consulte também
* [Como criar um projeto holográfico do DirectX](creating-a-holographic-directx-project.md)
* [API Windows. percepção. espacial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)

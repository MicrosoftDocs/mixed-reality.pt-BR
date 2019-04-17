---
title: Mapeamento espacial no DirectX
description: Explica como implementar o mapeamento espacial em seu aplicativo DirectX. Isso inclui uma explicação detalhada do que o aplicativo de exemplo de mapeamento espacial que está incluído no SDK da plataforma Universal do Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows misturadas realidade, mapeamento espacial, ambiente, interação, directx, winrt, api, código de exemplo, UWP, SDK, passo a passo
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591027"
---
# <a name="spatial-mapping-in-directx"></a>Mapeamento espacial no DirectX

Este tópico descreve como implementar [mapeamento espacial](spatial-mapping.md) em seu aplicativo DirectX. Isso inclui uma explicação detalhada do que o aplicativo de exemplo de mapeamento espacial que está incluído no SDK da plataforma Universal do Windows.

Este tópico usa o código a partir de [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) exemplo de código da UWP.

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

## <a name="directx-development-overview"></a>Visão geral de desenvolvimento do DirectX

Desenvolvimento de aplicativos nativos para mapeamento espacial usa as APIs sob o [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace. Essas APIs fornecem controle total da funcionalidade de mapeamento espacial, de maneira análoga diretamente para o mapeamento espacial APIs expostas pelos [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>APIs de percepção

Os principais tipos fornecidos para o desenvolvimento de mapeamento espacial são da seguinte maneira:
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornece informações sobre as superfícies em regiões especificado pelo aplicativo de espaço próxima ao usuário, na forma de objetos SpatialSurfaceInfo.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descreve uma única empacotamentos espacial superfície, incluindo uma ID exclusiva, delimitadora volume e a hora da última alteração. Ele fornecerá um SpatialSurfaceMesh assincronamente mediante solicitação.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contém os parâmetros usados para personalizar os objetos de SpatialSurfaceMesh solicitados do SpatialSurfaceInfo.
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa os dados de malha para uma única superfície espacial. Os dados para as posições de vértice, normais de vértice e índices de triângulo estão contidos nos objetos do membro SpatialSurfaceMeshBuffer.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) encapsula um único tipo de dados da malha.

Ao desenvolver um aplicativo usando essas APIs, o fluxo de programa básico terá esta aparência (conforme demonstrado no aplicativo de exemplo descrito abaixo):
- **Configurar seu SpatialSurfaceObserver**
  - Chame [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), para garantir que o usuário concedeu permissão para seu aplicativo para usar recursos de mapeamento espacial do dispositivo.
  - Criar uma instância de um objeto SpatialSurfaceObserver.
  - Chame [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar as regiões de espaço no qual você deseja obter informações sobre as superfícies espaciais. Você pode modificar essas regiões no futuro, simplesmente chamando essa função novamente. Cada região é especificado usando um [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Inscreva-se a [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) evento, que será acionado sempre que novas informações sobre as superfícies espaciais nas regiões de espaço que você especificou estão disponíveis.
- **Processar eventos ObservedSurfacesChanged**
  - No manipulador de eventos, chame [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para receber um mapa de objetos SpatialSurfaceInfo. Usando esse mapa, você pode atualizar seus registros de quais espaciais superfícies [existem no ambiente do usuário](spatial-mapping.md#mesh-caching).
  - Para cada objeto SpatialSurfaceInfo, você pode consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) determinar as extensões espaciais da superfície, expresso em uma [sistema de coordenadas espacial](coordinate-systems.md) de sua escolha.
  - Se você optar por solicitar malha para uma superfície espacial, chame [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). Você pode fornecer opções que especificam o formato dos dados retornados de malha e a densidade desejada de triângulos.
- **Receber e processar a malha**
  - Cada chamada para TryComputeLatestMeshAsync será aysnchronously retornar um objeto SpatialSurfaceMesh.
  - Deste objeto, você pode acessar os objetos SpatialSurfaceMeshBuffer contidos para acessar os índices de triângulo, posições de vértice e (se solicitado) normais de vértices da malha. Estes dados serão em um formato diretamente compatível com o [APIs do Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usados para renderizar as malhas.
  - A partir daqui seu aplicativo pode, opcionalmente, executar análise ou [processando](spatial-mapping.md#mesh-processing) dos dados de malha e usá-lo para [renderização](spatial-mapping.md#rendering) e física [raycasting e colisão](spatial-mapping.md#raycasting-and-collision).
  - Um detalhe importante a observar é que você deve aplicar uma escala para as posições de vértice de malha (por exemplo, no sombreador de vértice usados para renderizar as malhas), para convertê-los das unidades otimizado inteiro no qual eles são armazenados no buffer, para medidores. Você pode recuperar essa escala chamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Solução de problemas
* Não se esqueça de dimensionar as posições de vértice de malha em seu sombreador de vértice, usando a escala retornada por [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Passo a passo o exemplo de código mapeamento espacial

O [mapeamento espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) exemplo de código inclui o código que você pode usar para começar a carregar malhas superfície em seu aplicativo, incluindo a infraestrutura para gerenciar e malhas de superfície de renderização.

Agora, veremos como adicionar funcionalidade de mapeamento de superfície para seu aplicativo DirectX. Você pode adicionar este código ao seu [modelo de aplicativo do Windows Holographic](creating-a-holographic-directx-project.md) projeto, ou você pode acompanhar navegando-se o código de exemplo mencionado acima. Este exemplo de código se baseia no modelo de aplicativo do Windows Holographic.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configurar seu aplicativo para usar o recurso de spatialPerception

Seu aplicativo deve ser capaz de usar o recurso de mapeamento espacial. Isso é necessário porque a malha espacial é uma representação do ambiente do usuário, que pode ser considerado dados privados. Declare esse recurso no arquivo Package. appxmanifest para seu aplicativo. Veja um exemplo:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

O recurso é proveniente de **uap2** namespace. Para obter acesso a esse namespace em seu manifesto, incluí-lo como um *xlmns* atributo no &lt;pacote > elemento. Veja um exemplo:

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Verificar se há suporte ao recurso de mapeamento espacial

Realidade mista do Windows oferece suporte a uma ampla variedade de dispositivos, incluindo dispositivos que não dão suporte a mapeamento espacial. Se seu aplicativo pode usar o mapeamento espacial, ou deve usar o mapeamento espacial, para fornecer a funcionalidade, ele deve verificar para certificar-se de que há suporte para mapeamento espacial antes de tentar usá-lo. Por exemplo, se o mapeamento espacial é exigido pelo seu aplicativo de realidade misturada, ele deve exibir uma mensagem para esse efeito se um usuário tentar executá-lo em um dispositivo sem mapeamento espacial. Ou então, seu aplicativo pode ser capaz de renderizar seu próprio ambiente virtual no lugar do ambiente do usuário, proporcionando uma experiência semelhante a que aconteceria se o mapeamento espacial estava disponível. Em qualquer evento, essa API permite que seu aplicativo a serem consideradas quando ele não será obter dados de mapeamento espacial e responder da maneira apropriada.

Para verificar se o dispositivo atual para o suporte de mapeamento espacial, primeiro verifique se que o contrato UWP está no nível 4 ou superior e, em seguida, chame SpatialSurfaceObserver::IsSupported(). Aqui está como fazer isso no contexto do [mapeamento espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) exemplo de código. O suporte é verificado antes de solicitar acesso.

A API de SpatialSurfaceObserver::IsSupported() está disponível a partir do SDK versão 15063. Se necessário, redirecione seu projeto para a versão de plataforma 15063 antes de usar essa API.

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

Observe que, quando o contrato UWP é menor que o nível 4, o aplicativo deve continuar como se o dispositivo é capaz de fazer o mapeamento espacial.

### <a name="request-access-to-spatial-mapping-data"></a>Solicitar acesso a dados de mapeamento espacial

Seu aplicativo precisa solicitar permissão para acessar dados de mapeamento espacial antes de tentar criar qualquer superfície observadores. Aqui está um exemplo com base em nosso exemplo de código de mapeamento de superfície, com mais detalhes posteriormente fornecidas nesta página:

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

O **Windows::Perception::Spatial::Surfaces** namespace inclui as [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) classe, que observa um ou mais volumes que você especificar em uma [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Use uma [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instância para acessar dados de malha superficial em tempo real.

Partir **AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Conforme observado na seção anterior, você deve solicitar acesso aos dados de mapeamento espacial antes de seu aplicativo pode usá-lo. Esse acesso é concedido automaticamente o HoloLens.

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

Em seguida, você precisará configurar o observador de superfície para observar um volume específico por delimitador. Aqui, podemos observar uma caixa que é 20 x 20 x 5 metros, centralizada na origem do sistema de coordenadas.

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

Observe que você pode definir vários volumes delimitadora.

*Este é o pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

Também é possível usar outras formas de delimitadoras - como frustum um modo de exibição, ou uma caixa delimitadora que não é o eixo alinhado.

*Este é o pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Se seu aplicativo precisa fazer nada diferente quando dados de mapeamento de superfície não estiverem disponíveis, você pode escrever código para responder ao caso em que o [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) não está **permitidos** - por exemplo, ele será permitido em PCs com dispositivos de imersão anexados porque esses dispositivos não têm o hardware para mapeamento espacial. Para esses dispositivos, em vez disso, você deve confiar no Palco espacial para obter informações sobre o ambiente e a configuração do dispositivo do usuário.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inicializar e atualizar a coleção de malha superficial

Se o observador de superfície foi criado com êxito, poderemos continuar para inicializar nossa coleção de malha superficial. Aqui, podemos usar a API do modelo de pull para obter o conjunto atual de superfícies observadas imediatamente:

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

Também é um modelo de push disponível para obter dados de malha superficial. Você é livre para projetar seu aplicativo para usar somente o modelo de pull se você escolher, caso em que você vai pesquisar dados frequência - por exemplo, uma vez por quadro - ou durante um período de tempo específico, como durante a instalação do jogo. Nesse caso, o código acima é o que você precisa.

Em nosso exemplo de código, que escolhemos demonstrar o uso de ambos os modelos para fins de pedagógico. Aqui, podemos assinar um evento para receber dados de malha superficial atualizadas sempre que o sistema reconhece uma alteração.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Nosso exemplo de código também está configurado para responder a esses eventos. Vamos examinar como fazemos isso.

**OBSERVAÇÃO:** Isso pode não ser a maneira mais eficiente para seu aplicativo lidar com dados da malha. Esse código é gravado para maior clareza e não é otimizado.

Os dados de malha superficial são fornecidos em um mapa de somente leitura que armazena [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objetos usando [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de chave.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Para processar esses dados, vamos primeiros para valores de chave que não estão em nossa coleção. Obter detalhes sobre como os dados são armazenados em nosso aplicativo de exemplo serão apresentadas neste tópico.

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

Também precisamos remover malhas de superfície que estão em nossa coleção de malha superficial, mas que não estão na coleção de sistema mais. Para fazer isso, precisamos fazer algo semelhante ao oposto do que acabamos de Mostrar para adição e atualização de malhas; executamos um loop na coleção de nosso aplicativo e verificar se o **Guid** temos está na coleção de sistema. Se não estiver na coleção de sistema, podemos removê-lo da nossa.

Nosso manipulador de eventos em AppMain.cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

A implementação da remoção de malha no RealtimeSurfaceMeshRenderer.cpp:

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Adquirir e usar buffers de dados de malha superficial

Como obter as informações de malha superficial foi tão fácil quanto efetuar pull de uma coleção de dados e processamento de atualizações a essa coleção. Agora, podemos entrarei em detalhes sobre como você pode usar os dados.

Em nosso exemplo de código, optamos por usar as malhas de superfície para renderização. Isso é um cenário comum para hologramas occluding por trás de superfícies do mundo real. Você também pode renderizar as malhas, ou renderizar processadas versões deles, para mostrar ao usuário quais áreas do sala são verificados antes de começar a fornecer a funcionalidade do aplicativo ou jogo.

O exemplo de código inicia o processo quando ele recebe atualizações de malha superficial do manipulador de eventos que foram descritos na seção anterior. A linha importante do código nessa função é chamada para atualizar a superfície *malha*: nesse momento podemos já processadas as informações de malha, e estamos prestes a se tornar os dados de índice e vértice para uso como podemos ver melhor.

From RealtimeSurfaceMeshRenderer.cpp:

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

Nosso código de exemplo é projetado para que uma classe de dados **SurfaceMesh**, lida com dados de malha de processamento e renderização. Esses malhas são o que o **RealtimeSurfaceMeshRenderer** realmente mantém um mapa de. Cada um deles tem uma referência para o SpatialSurfaceMesh ele veio e usá-lo sempre que é necessário para acessar os buffers de vértice ou o índice de malha, ou obter uma transformação para a malha. Por enquanto, vamos sinalizador a malha como precisando de uma atualização.

De SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Próxima vez em que a malha é solicitada a desenhar a próprio, ele verificará o sinalizador pela primeira vez. Se uma atualização for necessária, os buffers de índice e vértice serão atualizados na GPU.

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

Primeiro, vamos adquirir os buffers de dados brutos:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Em seguida, podemos criar buffers de dispositivo Direct3D com os dados de malha fornecidos pelo HoloLens:

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

**OBSERVAÇÃO:** Para a função de auxiliar CreateDirectXBuffer usada no trecho anterior, consulte o exemplo de código de mapeamento de superfície: SurfaceMesh.cpp, GetDataFromIBuffer.h. Agora, a criação de recursos do dispositivo for concluída e a malha é considerada para ser carregado e pronto para atualização e renderizar.

### <a name="update-and-render-surface-meshes"></a>Atualizar e renderizar a superfície de malhas

Nossa classe SurfaceMesh tem uma função especializada de atualização. Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tem sua própria transformação e, em nosso exemplo usa o sistema de coordenadas atual para o nosso **SpatialStationaryReferenceFrame** para adquirir a transformação. Em seguida, ele atualiza o buffer de constantes de modelo na GPU.

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

Quando chegou a hora para renderizar a superfície de malhas, podemos fazer algum trabalho de preparação antes de renderizar a coleção. Configuramos o pipeline sombreador para a configuração atual de renderização e configuramos o estágio do assembler de entrada. Observe que a classe do auxiliar de câmera holographic **CameraResources.cpp** já tiver configurado o buffer de constantes de projeção de exibição/agora.

Partir **RealtimeSurfaceMeshRenderer::Render**:

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

Depois que isso for feito, podemos loop em nosso malhas e informar a cada um para desenhar a mesmo. **OBSERVAÇÃO:** Esse código de exemplo não é otimizado para usar qualquer tipo de frustum traseira, mas você deve incluir esse recurso em seu aplicativo.

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

As malhas individuais são responsáveis por configurar o buffer de índice e vértice, o stride e o buffer de constantes de transformação do modelo. Assim como acontece com o cubo giratório no modelo de aplicativo do Windows Holographic, podemos renderizar buffers estereoscópica usando a criação de instância.

Partir **SurfaceMesh::Draw**:

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

### <a name="rendering-choices-with-surface-mapping"></a>Opções de renderização com o mapeamento de superfície

O exemplo de código de mapeamento de superfície oferece para renderização somente oclusão dos dados de malha superficial e na tela de processamento de dados de malha superficial de código. Qual caminho você escolher - ou ambos - dependem do seu aplicativo. Vamos examinar ambas as configurações neste documento.

**Buffers de oclusão de renderização para efeito holográfico**

Começar limpando a exibição de destino de renderização para a câmera virtual atual.

De AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Essa é uma passagem de "pré-processamento". Aqui, podemos criar um buffer de oclusão pedindo que o renderizador de malha para renderizar apenas profundidade. Nessa configuração, não anexamos um modo de exibição de destino de renderização e o renderizador de malha define o estágio de sombreador de pixel para **nullptr** , de modo que a GPU não se preocupa em Desenhar pixels. A geometria será rasterizado no buffer de profundidade e o pipeline gráfico irá parar por aqui.

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

É possível desenhar hologramas com um teste de profundidade extra contra o buffer de oclusão de superfície de mapeamento. No exemplo de código, podemos renderizar pixels no cubo de uma cor diferente se eles estiverem protegidos por uma superfície.

De AppMain.cpp:

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

Com base no código do SpecialEffectPixelShader.hlsl:

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

**Observação:** Para nosso **GatherDepthLess** rotina, consulte o exemplo de código de mapeamento de superfície: SpecialEffectPixelShader.hlsl.

**Dados de malha superficial de renderização para a exibição**

Também podemos tirar as malhas de superfície para os buffers de exibição estéreo. Optamos por desenhar faces completos com iluminação, mas fique à vontade para desenhar wireframe, processar as malhas antes da renderização, aplicar um mapa de textura e assim por diante.

Aqui, nosso exemplo de código informa o renderizador de malha para desenhar a coleção. Neste momento, não especifique uma passagem somente de profundidade, para que ele irá anexar um sombreador de pixel e concluir o pipeline de renderização usando os destinos que especificamos para a câmera virtual atual.

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
* [Criando um projeto holográfico do DirectX](creating-a-holographic-directx-project.md)
* [Windows.Perception.Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)

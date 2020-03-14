---
title: Coordenar sistemas no DirectX
description: Explica como usar localizadores espaciais de realidade mista do Windows, quadros de referência, âncoras espaciais e sistemas de coordenadas, como usar o SpatialStage, como lidar com a perda de rastreamento, como salvar e carregar âncoras e como fazer a estabilização de imagem.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, localizador espacial, quadro de referência espacial, sistema de coordenadas espaciais, estágio espacial, código de exemplo, estabilização de imagem, âncora espacial, repositório de âncora espacial, perda de controle, passo a passos
ms.openlocfilehash: a0bce897c1982715af24f0bf7c398cdee10f017f
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375613"
---
# <a name="coordinate-systems-in-directx"></a>Coordenar sistemas no DirectX

Os [sistemas de coordenadas](coordinate-systems.md) formam a base da compreensão espacial oferecida pelas APIs de realidade mista do Windows.

Os dispositivos VR de hoje em dia ou VR de sala única estabelecem um sistema de coordenadas primário para representar seu espaço controlado. Os dispositivos Windows Mixed Reality, como o HoloLens, foram projetados para serem usados em grandes ambientes indefinidos, com o dispositivo descobrindo e aprendendo sobre seus arredores à medida que o usuário percorre. Isso permite que o dispositivo se adapte para melhorar continuamente o conhecimento sobre as salas do usuário, mas resulta em sistemas de coordenadas que mudarão sua relação entre si até o tempo de vida do aplicativo. O Windows Mixed Reality dá suporte a uma ampla gama de dispositivos, variando de headsets de imersão enfeitas por meio de quadros de referência conectados ao mundo.

>[!NOTE]
>Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemas de coordenadas espaciais no Windows

O tipo de núcleo usado para ponderar os sistemas de coordenadas do mundo real no Windows é o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Uma instância desse tipo representa um sistema de coordenadas arbitrário e fornece um método para obter uma matriz de transformação que você pode usar para transformar entre dois sistemas de coordenadas sem compreender os detalhes de cada um.

Os métodos que retornam informações espaciais, representadas como pontos, raios ou volumes no ambiente do usuário, aceitarão um parâmetro SpatialCoordinateSystem para permitir que você decida o sistema de coordenadas no qual é mais útil que essas coordenadas sejam retornadas. As unidades dessas coordenadas sempre estarão em metros.

Um SpatialCoordinateSystem tem uma relação dinâmica com outros sistemas de coordenadas, incluindo aqueles que representam a posição do dispositivo. A qualquer momento, o dispositivo pode localizar alguns sistemas de coordenadas e não outros. Para a maioria dos sistemas de coordenadas, seu aplicativo deve estar pronto para lidar com períodos de tempo durante os quais eles não podem ser localizados.

Seu aplicativo não deve criar SpatialCoordinateSystems diretamente-em vez disso, eles devem ser consumidos por meio de APIs de percepção. Há três fontes principais de sistemas de coordenadas nas APIs de percepção, cada uma das quais são mapeadas para um conceito descrito na página de [sistemas de coordenadas](coordinate-systems.md) :
* Para obter um quadro estacionário de referência, crie um <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> ou obtenha um do <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>atual.
* Para obter uma âncora espacial, crie um <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Para obter um quadro de referência anexado, crie um <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Todos os sistemas de coordenadas retornados por esses objetos são destros, com + y up, + x à direita e + z para trás. Você pode se lembrar de qual direção os pontos positivos do eixo z apontando os dedos de sua mão esquerda ou direita na direção x positiva e enrolando-os para a direção y positiva. A direção do seu polegar aponta em sua direção ou para longe de você, é a direção em que o eixo z positivo aponta para esse sistema de coordenadas. A ilustração a seguir mostra esses dois sistemas de coordenadas.

![sistemas de coordenadas à esquerda e à direita](images/left-hand-right-hand.gif)<br>
*Sistemas de coordenadas do lado esquerdo e direito*

Para se inicializar em um SpatialCoordinateSystem com base na posição de um HoloLens, use a classe <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> para criar um quadro de referência ou em anexo, conforme descrito nas seções abaixo.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Coloque os hologramas no mundo inteiro usando um estágio espacial

O sistema de coordenadas para headsets de imersão de realidade mista do Windows é acessado usando a propriedade estática <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> . Essa API fornece um sistema de coordenadas, informações sobre se o jogador está conectado ou móvel, o limite de uma área segura para se movimentar se o jogador for móvel e uma indicação de se o headset é ou não direcional. Há também um manipulador de eventos para atualizações no estágio espacial.

Primeiro, obtemos o estágio espacial e assinamos atualizações para ele: 

Código para **inicialização de estágio espacial**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

No método OnCurrentChanged, seu aplicativo deve inspecionar o estágio espacial e atualizar a experiência do jogador de acordo. Neste exemplo, fornecemos uma visualização do limite de estágio, bem como a posição inicial especificada pelo usuário e o intervalo de exibição e intervalo de propriedades de movimentação do estágio. Também retornamos ao nosso próprio sistema de coordenadas do seu próprio, quando não é possível fornecer um estágio.


Código para **atualização de estágio espacial**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

O conjunto de vértices que definem o limite de estágio é fornecido na ordem horária. O Shell de realidade mista do Windows desenha uma cerca no limite quando o usuário a aproxima; Talvez você queira triangular a área que pode ser orientada para suas próprias finalidades. O algoritmo a seguir pode ser usado para triangular o palco.


Código para **triangularização de estágio espacial**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Coloque os hologramas no mundo usando um quadro estacionário de referência

A classe [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) representa um quadro de referência que [permanece estacionário](coordinate-systems.md#stationary-frame-of-reference) em relação ao ambiente do usuário à medida que o usuário se movimenta. Esse quadro de referência prioriza a manutenção de coordenadas perto do dispositivo. Um uso importante de um SpatialStationaryFrameOfReference é agir como o sistema de coordenadas do mundo subjacente em um mecanismo de renderização ao renderizar hologramas.

Para obter um SpatialStationaryFrameOfReference, use a classe [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) e chame [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

No código de modelo do aplicativo Holographic do Windows:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Quadros de referência estacionários são projetados para fornecer uma posição de melhor ajuste em relação ao espaço geral. Posições individuais dentro desse quadro de referência têm permissão para serem descompassos um pouco. Isso é normal, pois o dispositivo aprende mais sobre o ambiente.
* Quando o posicionamento preciso de hologramas individuais é necessário, um SpatialAnchor deve ser usado para ancorar o holograma individual em uma posição no mundo real – por exemplo, um ponto que o usuário indica para ser de interesse especial. As posições de âncora não descompassom, mas podem ser corrigidas; a âncora usará a posição corrigida a partir do próximo quadro depois que a correção tiver ocorrido.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Coloque os hologramas no mundo usando âncoras espaciais

As [âncoras espaciais](coordinate-systems.md#spatial-anchors) são uma ótima maneira de posicionar os hologramas em um local específico no mundo real, com o sistema, garantindo que a âncora permaneça em vigor ao longo do tempo. Este tópico explica como criar e usar uma âncora e como trabalhar com dados de âncora.

Você pode criar um SpatialAnchor em qualquer posição e orientação dentro do SpatialCoordinateSystem de sua escolha. O dispositivo deve ser capaz de localizar o sistema de coordenadas no momento e o sistema não deve ter atingido seu limite de âncoras espaciais.

Uma vez definido, o sistema de coordenadas de um SpatialAnchor ajusta-se continuamente para manter a posição e a orientação exatas de seu local inicial. Você pode usar esse SpatialAnchor para renderizar hologramas que aparecerão fixos no ambiente do usuário nesse local exato.

Os efeitos dos ajustes que mantêm a âncora em vigor são ampliados à medida que a distância da âncora aumenta. Portanto, você deve evitar a renderização de conteúdo em relação a uma âncora com mais de cerca de 3 metros da origem da âncora.

A propriedade [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) Obtém um sistema de coordenadas que permite que você coloque o conteúdo em relação à âncora, com a atenuação aplicada quando o dispositivo ajusta o local preciso da âncora.

Use a propriedade [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) e o evento [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) correspondente para gerenciar esses ajustes por conta própria.

### <a name="persist-and-share-spatial-anchors"></a>Persistir e compartilhar âncoras espaciais

Você pode persistir um SpatialAnchor localmente usando a classe [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) e, em seguida, colocá-lo novamente em uma sessão de aplicativo futura no mesmo dispositivo de HoloLens.

Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a>, você pode criar uma âncora de nuvem durável a partir de um SpatialAnchor local, que seu aplicativo pode localizar em vários dispositivos HoloLens, Ios e Android.  Ao compartilhar uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a> para persistência assíncrona de holograma em dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial em nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que os dispositivos não estejam presentes ao mesmo tempo.

Para começar a criar experiências compartilhadas em seu aplicativo de HoloLens, experimente o início rápido de 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">do Azure espaciais do hololens</a>.

Quando estiver em execução com as âncoras espaciais do Azure, você poderá <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">criar e localizar âncoras no HoloLens</a>.  Os passo a passos também estão disponíveis para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e Ios</a> , permitindo que você compartilhe as mesmas âncoras em todos os dispositivos.

### <a name="create-spatialanchors-for-holographic-content"></a>Criar SpatialAnchors para conteúdo Holographic

Para este exemplo de código, modificamos o modelo de aplicativo Holographic do Windows para criar âncoras quando o gesto **pressionado** é detectado. Em seguida, o cubo é colocado na âncora durante a passagem de renderização.

Como há suporte para várias âncoras na classe auxiliar, podemos inserir tantos cubos quantos desejarmos usando este exemplo de código!

Observe que as IDs de âncoras são algo que você controla em seu aplicativo. Neste exemplo, criamos um esquema de nomenclatura sequencial com base no número de âncoras atualmente armazenados na coleção de âncoras do aplicativo.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Carga assíncrona e cache, o SpatialAnchorStore

Vejamos como escrever uma classe SampleSpatialAnchorHelper que ajuda a lidar com essa persistência, incluindo:
* Armazenamento de uma coleção de âncoras na memória, indexados por uma chave Platform:: String.
* Carregando âncoras do SpatialAnchorStore do sistema, que é mantido separado da coleção na memória local.
* Salvar a coleção na memória local de âncoras para o SpatialAnchorStore quando o aplicativo opta por fazer isso.

Veja como salvar objetos [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) no [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Quando a classe é iniciada, solicitamos o SpatialAnchorStore de forma assíncrona. Isso envolve a e/s do sistema à medida que a API carrega o armazenamento de âncoras, e essa API é assíncrona para que a e/s seja sem bloqueio.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Você receberá um SpatialAnchorStore que pode ser usado para salvar as âncoras. Esse é um IMapView que associa os valores de chave que são cadeias de caracteres, com valores de dados que são SpatialAnchors. Em nosso código de exemplo, armazenamos isso em uma variável de membro de classe privada que pode ser acessada por meio de uma função pública de nossa classe auxiliar.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Não se esqueça de conectar os eventos suspender/retomar para salvar e carregar o repositório de âncoras.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Salvar conteúdo no repositório de âncora

Quando o sistema suspende seu aplicativo, você precisa salvar suas âncoras espaciais no repositório de âncora. Você também pode optar por salvar âncoras no repositório de âncora em outros momentos, pois você deve ser necessário para a implementação do seu aplicativo.

Quando estiver pronto para tentar salvar as âncoras na memória para o SpatialAnchorStore, você poderá executar um loop por meio de sua coleção e tentar salvar cada uma delas.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Carregar conteúdo do repositório de âncora quando o aplicativo for retomado

Quando o aplicativo for retomado, ou a qualquer outro momento necessário para o implementaiton do seu aplicativo, você poderá restaurar âncoras que foram salvas anteriormente no AnchorStore transferindo-as do IMapView do repositório de ancoragem para seu próprio banco de dados na memória de SpatialAnchors.

Para restaurar âncoras do SpatialAnchorStore, restaure cada uma das quais você está interessado em sua própria coleção na memória.

Você precisa de seu próprio banco de dados na memória de SpatialAnchors; alguma maneira de associar cadeias de caracteres ao SpatialAnchors que você cria. Em nosso código de exemplo, optamos por usar um Windows:: Foundation:: Collections:: IMap para armazenar as âncoras, o que facilita o uso da mesma chave e valor de dados para o SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Uma âncora restaurada pode não ser localizável imediatamente. Por exemplo, pode ser uma âncora em uma sala separada ou em um prédio diferente. As âncoras recuperadas do AnchorStore devem ser testadas para locatability antes de usá-las.

<br>

>[!NOTE]
>Neste código de exemplo, recuperamos todas as âncoras do AnchorStore. Isso não é um requisito; seu aplicativo também poderia escolher um determinado subconjunto de âncoras usando valores de chave de cadeia de caracteres que são significativos para sua implementação.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Limpar o repositório de âncora, quando necessário

Às vezes, você precisa limpar o estado do aplicativo e gravar novos dados. Veja como fazer isso com o [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Usando nossa classe auxiliar, é quase desnecessário encapsular a função Clear. Optamos por fazer isso em nossa implementação de exemplo, porque nossa classe auxiliar recebe a responsabilidade de possuir a instância SpatialAnchorStore.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Exemplo: relacionando sistemas de coordenadas de âncora a sistemas de coordenadas de quadros de referência de estacionários

Digamos que você tenha uma âncora e queira relacionar algo no sistema de coordenadas da âncora ao SpatialStationaryReferenceFrame que você já está usando para a maior parte de seu outro conteúdo. Você pode usar [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) para obter uma transformação do sistema de coordenadas da âncora para a do quadro de referência estacionário:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Esse processo é útil de duas maneiras:
1. Ele informa se os dois quadros de referência podem ser compreendidos em relação uns aos outros, e;
2. Nesse caso, ele fornece uma transformação para ir diretamente de um sistema de coordenadas para o outro.

Com essas informações, você tem uma compreensão da relação espacial entre objetos entre os dois quadros de referência.

Para a renderização, muitas vezes você pode obter resultados melhores agrupando objetos de acordo com seu quadro de referência original ou âncora. Execute uma passagem de desenho separada para cada grupo. As matrizes de exibição são mais precisas para objetos com transformações de modelo que são criadas inicialmente usando o mesmo sistema de coordenadas.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Criar hologramas usando um quadro de referência anexado ao dispositivo

Há ocasiões em que você deseja renderizar um holograma que [permanece anexado](coordinate-systems.md#attached-frame-of-reference) ao local do dispositivo, por exemplo, um painel com informações de depuração ou uma mensagem informativa quando o dispositivo só consegue determinar sua orientação e não sua posição no espaço. Para fazer isso, usamos um quadro de referência anexado.

A classe SpatialLocatorAttachedFrameOfReference define os sistemas de coordenadas que são relativos ao dispositivo em vez do mundo real. Esse quadro tem um título fixo em relação ao ambiente do usuário que aponta na direção em que o usuário estava voltado quando o quadro de referência foi criado. A partir desse momento, todas as orientações nesse quadro de referência são relativas a esse cabeçalho fixo, mesmo quando o usuário gira o dispositivo.

Para o HoloLens, a origem do sistema de coordenadas deste quadro está localizada no centro da rotação do cabeçalho do usuário, para que sua posição não seja afetada pela rotação de cabeçalho. Seu aplicativo pode especificar um deslocamento relativo a esse ponto para posicionar os hologramas na frente do usuário.

Para obter um SpatialLocatorAttachedFrameOfReference, use a classe SpatialLocator e chame CreateAttachedFrameOfReferenceAtCurrentHeading.

Observe que isso se aplica a todo o intervalo de dispositivos do Windows Mixed Reality.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Usar um quadro de referência anexado ao dispositivo

Estas seções falam sobre o que alteramos no modelo de aplicativo Holographic do Windows para habilitar um quadro de referência anexado ao dispositivo usando essa API. Observe que esse holograma "anexado" funcionará junto com hologramas fixos ou ancorados e também poderá ser usado quando o dispositivo estiver temporariamente incapaz de encontrar sua posição no mundo.

Primeiro, alteramos o modelo para armazenar um SpatialLocatorAttachedFrameOfReference em vez de um SpatialStationaryFrameOfReference:

De **HolographicTagAlongSampleMain. h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

De **HolographicTagAlongSampleMain. cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante a atualização, agora obtemos o sistema de coordenadas no carimbo de data/hora obtido com a previsão de quadros.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Obter uma pose de ponteiro espacial e seguir o olhar do usuário

Queremos que nosso holograma de exemplo siga o [olhar](gaze-and-commit.md)do usuário, semelhante a como o Shell Holographic pode seguir o olhar do usuário. Para isso, precisamos obter o SpatialPointerPose do mesmo carimbo de data/hora.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Esse SpatialPointerPose tem as informações necessárias para posicionar o holograma de acordo com o [cabeçalho atual do usuário](gaze-in-directx.md).

Por motivos de conforto do usuário, usamos interpolação linear ("Lerp") para suavizar a alteração na posição de forma que ela ocorra durante um período de tempo. Isso é mais confortável para o usuário do que bloquear o holograma para seu olhar. Lerping a posição da marca no holograma também nos permite estabilizar o holograma ao retardar o movimento; Se não fizermos esse retardamento, o usuário veria a tremulação do holograma por causa do que normalmente é considerado como movimentos imperceptívels do cabeçalho do usuário.

De **StationaryQuadRenderer::P ositionhologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>No caso de um painel de depuração, você pode optar por reposicionar o holograma no lado um pouco para que ele não obstrua o seu modo de exibição. Aqui está um exemplo de como você pode fazer isso.

Para **StationaryQuadRenderer::P ositionhologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Girar o holograma para encarar a câmera

Não é suficiente simplesmente posicionar o holograma, que nesse caso é um quádruplo; também devemos girar o objeto para que ele fique à frente do usuário. Observe que essa rotação ocorre no espaço de mundo, pois esse tipo de mensagem permite que o holograma permaneça como parte do ambiente do usuário. A apresentação de espaço de exibição não é tão confortável porque o holograma se torna bloqueado para a orientação de exibição; Nesse caso, você também precisaria fazer a interpolação entre as matrizes da exibição esquerda e direita para adquirir uma transformação do mural do espaço de exibição que não interrompa a renderização de estéreo. Aqui, giramos nos eixos X e Z para enfrentar o usuário.

De **StationaryQuadRenderer:: Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Renderizar o holograma anexado

Para este exemplo, também optamos por renderizar o holograma no sistema de coordenadas do SpatialLocatorAttachedReferenceFrame, que é onde posicionamos o holograma. (Se tivéssemos decidido renderizar usando outro sistema de coordenadas, precisaremos adquirir uma transformação do sistema de coordenadas do quadro de referência anexado ao dispositivo para esse sistema de coordenadas.)

De **HolographicTagAlongSampleMain:: render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

Pronto! O holograma agora "colocará" uma posição que seja de 2 metros na frente da direção do olhar do usuário.

>[!NOTE]
>Este exemplo também carrega conteúdo adicional-consulte StationaryQuadRenderer. cpp.

## <a name="handling-tracking-loss"></a>Lidando com a perda de controle

Quando o dispositivo não consegue se localizar no mundo, o aplicativo tem "perda de rastreamento". Os aplicativos de realidade mista do Windows devem ser capazes de lidar com essas interrupções no sistema de controle posicional. Essas interrupções podem ser observadas e as respostas criadas usando o evento LocatabilityChanged no SpatialLocator padrão.

De **AppMain:: SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Quando seu aplicativo recebe um evento LocatabilityChanged, ele pode alterar o comportamento conforme necessário. Por exemplo, no estado PositionalTrackingInhibited, seu aplicativo pode pausar a operação normal e renderizar um [holograma de marca](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) que exibe uma mensagem de aviso.

O modelo de aplicativo Holographic do Windows vem com um manipulador de LocatabilityChanged já criado para você. Por padrão, ele exibe um aviso no console de depuração quando o controle posicional está indisponível. Você pode adicionar código a esse manipulador para fornecer uma resposta, conforme necessário, do seu aplicativo.

De **AppMain. cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>mapeamento espacial

As APIs de [mapeamento espacial](spatial-mapping-in-directx.md) fazem uso de sistemas de coordenadas para obter transformações de modelo para malhas de superfície.

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas](coordinate-systems.md)
* [Âncoras espaciais](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)

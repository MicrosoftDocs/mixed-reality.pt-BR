---
title: Sistemas de coordenadas no DirectX
description: Explica como usar o Windows Mixed Reality espaciais localizadores, quadros de referência, espaciais âncoras e sistemas de coordenadas, como usar o SpatialStage, como lidar com a perda de controle, como salvar e carregar as âncoras e como criar uma imagem de estabilização.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realidade, o localizador espacial, quadro de referência espacial, o sistema de coordenadas espacial, estágio espacial, de exemplo código, estabilização da imagem, âncora espacial, armazenamento espacial de âncora, perda de acompanhamento, passo a passo
ms.openlocfilehash: c8cdb39cbf4634edb4ed0a595381fc70f1388ce4
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591030"
---
# <a name="coordinate-systems-in-directx"></a>Sistemas de coordenadas no DirectX

[Sistemas de coordenadas](coordinate-systems.md) formam a base para a compreensão espacial oferecida pelas APIs de realidade mista do Windows.

Hoje encaixado VR ou dispositivos VR única sala estabelecer um sistema de coordenadas primário para representar seu espaço controlado. Dispositivos de realidade mista do Windows, como o HoloLens são projetados para ser usada durante grandes ambientes indefinidos, com o dispositivo de descobrir e aprender sobre seu ambiente, como o usuário conduz ao redor. Isso permite que o dispositivo para se adaptar a melhorar continuamente o conhecimento sobre o usuário salas, mas resulta em sistemas de coordenadas que irá alterar sua relação umas às outras por meio do tempo de vida do aplicativo. Realidade mista do Windows oferece suporte a um amplo espectro de dispositivos, desde sentado fones imersivos em exposição por meio de quadros de referência anexado ao mundo.

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemas de coordenadas espaciais no Windows

O tipo de principal usado para ponderar sobre sistemas de coordenadas do mundo real no Windows é o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Uma instância desse tipo representa um sistema de coordenadas arbitrário e fornece um método para obter uma matriz de transformação que você pode usar para transformar entre dois sistemas de coordenadas sem compreender os detalhes de cada.

Os métodos que retornam informações espaciais, representadas como pontos, raios ou volumes no ambiente do usuário, aceitará um parâmetro de SpatialCoordinateSystem para permitir que você decida o sistema de coordenadas no qual ele é mais útil para essas coordenadas a serem retornados. As unidades para essas coordenadas sempre será em metros.

Um SpatialCoordinateSystem tem uma relação dinâmica com outros sistemas de coordenadas, inclusive aqueles que representam a posição do dispositivo. A qualquer momento, o dispositivo pode ser capaz de localizar alguns sistemas de coordenadas e outros não. Para a maioria dos sistemas de coordenadas, seu aplicativo deve estar pronto para lidar com períodos de tempo durante o qual eles não podem ser localizados.

Seu aplicativo não deve criar SpatialCoordinateSystems diretamente – em vez disso, eles devem ser consumidos por meio das APIs de percepção. Há três fontes principais de sistemas de coordenadas nas APIs de percepção, cada um dos quais são mapeados para um conceito descrito na [sistemas de coordenadas](coordinate-systems.md) página:
* Para obter um quadro estacionário de referência, crie uma <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> ou obtenha um atuais <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.
* Para obter uma âncora espacial, crie uma <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Para obter um quadro de referência anexado, crie uma <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Todos os sistemas de coordenadas retornados por esses objetos são destros, com + y cima + x à direita e + z com versões anteriores. Você pode lembrar a direção na qual os pontos positivos do eixo z apontando os dedos de sua mão direita ou esquerda na direção x positivo e ondulação-los na direção y positivo. A direção do seu polegar aponta em sua direção ou para longe de você, é a direção em que o eixo z positivo aponta para esse sistema de coordenadas. A ilustração a seguir mostra esses dois sistemas de coordenadas.

![Sistemas de coordenadas do lado esquerdos e direito](images/left-hand-right-hand.gif)<br>
*Sistemas de coordenadas do lado esquerdos e direito*

Para inicializar em um SpatialCoordinateSystem com base na posição de um HoloLens, use o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> classe para criar qualquer um anexada ou parado quadro de referência, conforme descrito nas seções a seguir.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Hologramas lugar do mundo usando um estágio espacial

O sistema de coordenadas para opaco Windows Mixed Reality fones imersivos em exposição é acessado usando estático <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> propriedade. Essa API fornece um sistema de coordenadas, informações sobre se o jogador está encaixado ou móvel, o limite de uma área segura para andar se o player é móvel, e uma indicação de se deseja ou não o fone de ouvido é direcional. Também há um manipulador de eventos para atualizações para o estágio espacial.

Em primeiro lugar, vamos obter o estágio espacial e assine atualizações a ele: 

O código de **inicialização estágio espacial**

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

No método OnCurrentChanged, seu aplicativo deve inspecionar o estágio espacial e atualizar a experiência de player adequadamente. Neste exemplo, fornecemos uma visualização de limite do estágio, bem como a posição de início especificada pelo usuário e o intervalo do estágio de modo de exibição e o intervalo das propriedades de movimentação. Também voltamos ao nosso próprio sistema de coordenadas estático, quando um estágio não pode ser fornecido.


O código de **atualização estágio espacial**

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

O conjunto de vértices que definem os limites de estágio são fornecidos na ordem no sentido horário. O shell do Windows Mixed Reality desenha um limite no limite quando o usuário se aproxima dela; Talvez você queira triangularize a área a ser examinável para suas próprias finalidades. O algoritmo a seguir pode ser usado para triangularize o estágio.


O código de **triangularization estágio espacial**

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Hologramas lugar do mundo usando um quadro estacionário de referência

O [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) classe representa um quadro de referência que [permanece estático](coordinate-systems.md#stationary-frame-of-reference) em relação ao ambiente do usuário como o usuário move. Esse quadro de referência prioriza manter coordenadas estável perto do dispositivo. É um uso de chave de um SpatialStationaryFrameOfReference atuar como o sistema de coordenadas de mundo subjacente dentro de um mecanismo de renderização durante a renderização hologramas.

Para obter um SpatialStationaryFrameOfReference, use o [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) classe e chame [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

O Windows Holographic modelo do código do aplicativo:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Quadros de referência estáticos são projetados para fornecer uma melhor ajuste posição em relação ao espaço total. Posições individuais dentro desse quadro de referência são permitidas se um pouco. Isso é normal, pois o dispositivo aprende mais sobre o ambiente.
* Quando o posicionamento exato dos hologramas individuais é necessário, um SpatialAnchor deve ser usado para ancorar o holograma individual para uma posição no mundo real – por exemplo, um ponto do usuário indica para ser de interesse especial. Posições de âncora não descompasso, mas podem ser corrigidas; a âncora usará a posição corrigida a partir o próximo quadro após a correção ocorreu.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Hologramas lugar do mundo usando âncoras espaciais

[Âncoras espaciais](coordinate-systems.md#spatial-anchors) são uma ótima maneira de colocar hologramas em um local específico no mundo real, com o sistema garantindo a âncora permanece em vigor ao longo do tempo. Este tópico explica como criar e usar uma âncora e como trabalhar com dados de âncora.

Você pode criar um SpatialAnchor em qualquer posição e orientação dentro a SpatialCoordinateSystem de sua escolha. O dispositivo deve ser capaz de localizar esse sistema de coordenadas no momento, e o sistema não deve ter alcançado o limite das âncoras espaciais.

Depois de definido, o sistema de coordenadas de um SpatialAnchor ajusta continuamente para manter a posição exata e a orientação de sua localização inicial. Você pode usar este SpatialAnchor para renderizar hologramas aparecerão fixas no ambiente do usuário em que local exato.

Os efeitos dos ajustes que mantêm a âncora em vigor são ampliados como distância entre a âncora aumenta. Portanto, você deve evitar processar o conteúdo em relação a uma âncora que é mais do que cerca de 3 medidores da origem dessa âncora.

O [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) propriedade obtém um sistema de coordenadas que permite que você colocar o conteúdo em relação à âncora, com a atenuação aplicada quando o dispositivo ajusta o local exato da âncora.

Use o [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) propriedade e o correspondente [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) eventos para gerenciar esses ajustes por conta própria.

### <a name="persist-and-share-spatial-anchors"></a>Persistir e compartilhar âncoras espaciais

Você pode manter um SpatialAnchor localmente usando o [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) de classe e, em seguida, colocá-lo novamente em uma sessão de aplicativo futuras no mesmo dispositivo HoloLens.

Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a>, você pode criar uma âncora de nuvem durável de um local SpatialAnchor, o que seu aplicativo pode, em seguida, localizar em vários HoloLens, dispositivos iOS e Android.  Compartilhando uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.  Isso permite experiências compartilhadas em tempo real.

Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para persistência holograma assíncrona em dispositivos Android, iOS e HoloLens.  Compartilhando uma âncora de nuvem durável espacial, vários dispositivos podem observar o holograma persistente mesmo ao longo do tempo, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo.

Para começar a criação de experiências compartilhadas em seu aplicativo HoloLens, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">guia de início rápido do Azure espacial âncoras HoloLens</a>.

Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">criar e localizar as âncoras em HoloLens</a>.  Instruções passo a passo está disponível para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> também, permitindo que você compartilhe as âncoras mesmas em todos os dispositivos.

### <a name="create-spatialanchors-for-holographic-content"></a>Criar SpatialAnchors para conteúdo holográfico

Para este exemplo de código, modificamos o Windows Holographic modelo de aplicativo para criar âncoras quando o **pressionado** gesto é detectado. O cubo, em seguida, é colocado na âncora durante a passagem de renderização.

Como várias âncoras são suportadas pela classe auxiliar, já podemos colocar como muitos cubos que podemos usar esse exemplo de código!

Observe que as IDs para âncoras são algo que controlar em seu aplicativo. Neste exemplo, criamos um esquema de nomenclatura é sequencial com base no número de âncoras armazenados atualmente na coleção do aplicativo das âncoras.

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>De forma assíncrona de carga e armazenar em cache, o SpatialAnchorStore

Vamos ver como escrever uma classe SampleSpatialAnchorHelper que ajuda a lidar com essa persistência, incluindo:
* Armazenar uma coleção de âncoras de na memória, indexados por uma chave de Platform:: String.
* Carregando as âncoras de SpatialAnchorStore do sistema, que é mantido separado da coleção na memória local.
* Salvando a coleção na memória local âncoras a SpatialAnchorStore quando o aplicativo opta por fazê-lo.

Aqui está como economizar [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objetos na [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Quando a classe é iniciado, solicitamos o SpatialAnchorStore assincronamente. Isso envolve a e/s do sistema como a API carrega o repositório de âncora e essa API é feita assíncrona, de modo que a e/s é sem bloqueio.

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

Você receberá um SpatialAnchorStore que você pode usar para salvar as âncoras. Este é um IMapView que associa os valores de chave que são cadeias de caracteres, com valores de dados que são SpatialAnchors. Em nosso código de exemplo, armazenamos isso em uma variável de membro de classe privada é acessível por meio de uma função pública de nossa classe auxiliar.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Não se esqueça de ligar os eventos de suspender/retomar para salvar e carregar o repositório de âncora.

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

### <a name="save-content-to-the-anchor-store"></a>Salve o conteúdo para o repositório de âncora

Quando o sistema suspende o seu aplicativo, você precisará salvar suas âncoras espaciais para o repositório de âncora. Você também pode optar por salvar as âncoras para o repositório de âncora em outras ocasiões, como você pode encontrar necessários para a implementação do seu aplicativo.

Quando estiver pronto para tentar salvar as âncoras de memória para o SpatialAnchorStore, pode executar um loop por meio de sua coleção e tente salvar cada um deles.

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Carregar o conteúdo do armazenamento de âncora quando o aplicativo é retomado

Quando seu aplicativo é retomado, ou a qualquer momento necessário para implementaiton do seu aplicativo, você pode restaurar as âncoras que foram salvos anteriormente para o AnchorStore por transferi-las da IMapView âncora da loja ao seu próprio banco de dados na memória de SpatialAnchors.

Para restaurar as âncoras do SpatialAnchorStore, restaure cada um deles que você está interessado em sua própria coleção na memória.

Você precisa de seu próprio banco de dados na memória de SpatialAnchors; alguma maneira para associar as cadeias de caracteres com o SpatialAnchors criado por você. Em nosso código de exemplo, podemos optar por usar um IMAP para armazenar as âncoras, que torna mais fácil de usar o mesmo valor de chave e os dados para o SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Uma âncora que é restaurada pode não ser localizáveis imediatamente. Por exemplo, ele pode ser uma âncora em uma sala separada ou em um prédio diferentes completamente. Âncoras recuperadas do AnchorStore devem ser testadas para locatability antes de usá-los.

<br>

>[!NOTE]
>Nesse código de exemplo, podemos recuperar todas as âncoras do AnchorStore. Isso não é um requisito; seu aplicativo poderia assim como escolher um certo subconjunto de âncoras usando valores de chave de cadeia de caracteres que são significativas para sua implementação.

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

Às vezes, você precisará limpar o estado do aplicativo e gravar novos dados. Aqui está como fazer isso com o [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Usando a nossa classe auxiliar, é praticamente desnecessário encapsular a função Clear. Podemos optar por fazer isso em nossa implementação de exemplo, porque nossa classe auxiliar recebe a responsabilidade de proprietário de instância SpatialAnchorStore.

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Exemplo: Relacionados a sistemas de coordenadas de âncora para sistemas de coordenadas de quadro estacionário de referência

Digamos que você tem uma âncora, e você deseja relacionar algo no sistema de coordenadas da sua âncora para o SpatialStationaryReferenceFrame que você já está usando para a maioria dos seus outros tipos de conteúdo. Você pode usar [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) para obter uma transformação do sistema de coordenadas da âncora para que um quadro estacionário de referência:

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

Esse processo é útil para você de duas maneiras:
1. Informa se os dois quadros de referência pode ser compreendido em relação a um do outro, e;
2. Nesse caso, ele fornece uma transformação para ir diretamente de um sistema de coordenadas para outro.

Com essas informações, você tem uma compreensão da relação entre objetos entre dois quadros de referência espacial.

Para renderização, você geralmente pode obter resultados melhores através do agrupamento de objetos de acordo com seu quadro de referência original ou âncora. Execute uma passagem de desenho separada para cada grupo. As matrizes de exibição são mais precisas para objetos com transformações de modelo que são criadas inicialmente com o mesmo sistema de coordenadas.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Criar hologramas usando um dispositivo anexado quadro de referência

Há momentos em que você deseja renderizar um holograma que [permanece anexado](coordinate-systems.md#attached-frame-of-reference) para o local do dispositivo, por exemplo, um painel com informações ou uma mensagem informativa de depuração quando o dispositivo só é capaz de determinar sua orientação e não é sua posição no espaço. Para fazer isso, usamos um quadro de referência anexado.

A classe SpatialLocatorAttachedFrameOfReference define os sistemas de coordenadas que estão em relação ao dispositivo em vez de para o mundo real. Este quadro tem um título fixo em relação ao ambiente do usuário que aponta para a direção do usuário estava enfrentando quando o quadro de referência foi criado. Daí em seguida diante, todas as orientações nesse quadro de referência são relativos ao título fixo, mesmo que o usuário gira o dispositivo.

Para HoloLens, a origem do sistema de coordenadas desse quadro está localizada no Centro de rotação da cabeça do usuário, para que sua posição não é afetada pela rotação principal. Seu aplicativo pode especificar um deslocamento em relação a esse ponto para posicionar hologramas na frente do usuário.

Para obter um SpatialLocatorAttachedFrameOfReference, use a classe SpatialLocator e chame CreateAttachedFrameOfReferenceAtCurrentHeading.

Observe que isso se aplica aos dispositivos todo intervalo do Windows Mixed Reality.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Use um quadro de referência anexado ao dispositivo

Essas seções falam sobre o que mudou no modelo de aplicativo do Windows Holographic para habilitar um dispositivo anexado quadro de referência usando essa API. Observe que esse "anexada" holograma coexistirão hologramas estáticos ou ancoradas e também pode ser usada quando o dispositivo estiver temporariamente não é possível localizar sua posição no mundo.

Primeiro, alteramos o modelo para armazenar um SpatialLocatorAttachedFrameOfReference em vez de um SpatialStationaryFrameOfReference:

Partir **HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Partir **HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante a atualização, agora podemos obter o sistema de coordenadas em que o carimbo de hora obtido com a previsão de quadro.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Obter uma ponteiro espacial pose e siga a olhar do usuário

Queremos que nosso holograma de exemplo a seguir do usuário [olhares](gaze.md), semelhante a como o shell holográfico pode seguir olhar do usuário. Para isso, precisamos obter o SpatialPointerPose do mesmo carimbo de hora.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Este SpatialPointerPose tem as informações necessárias para posicionar o holograma de acordo com o [rumo atual do usuário](gaze,-gestures,-and-motion-controllers-in-directx.md).

Por motivos de conforto de usuário, podemos usar interpolação linear ("lerp") para suavizar a alteração na posição, de modo que ele ocorre durante um período de tempo. Isso é mais à vontade para o usuário que o holograma para seu olhar o bloqueio. Lerping que posição do holograma de tag-along também nos permite estabilizar o holograma por retardamento movimentação; Se não fizermos essa interrupção, o usuário veria o holograma tremulação devido a que normalmente é considerado como sendo imperceptível movimentos da cabeça do usuário.

Partir **StationaryQuadRenderer::PositionHologram**:

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
>No caso de um painel de depuração, você pode optar reposicionar o holograma desativado para o lado um pouco para que ele não obstruir sua exibição. Aqui está um exemplo de como você pode fazer isso.

Para **StationaryQuadRenderer::PositionHologram**:

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

### <a name="rotate-the-hologram-to-face-the-camera"></a>Girar o holograma para enfrentar a câmera

Não é suficiente simplesmente posicionar holograma, que nesse caso é um quad; podemos também deve girar o objeto para o usuário. Observe que essa rotação ocorre no espaço de mundo, porque esse tipo de billboarding permite o holograma permaneça uma parte do ambiente do usuário. Espaço do modo de exibição billboarding não é tão à vontade porque o holograma fica bloqueado para a orientação da tela; Nesse caso, você também teria que interpolar entre as matrizes de exibição da esquerda e direita para adquirir uma transformação de mensagem de instalação de espaço do modo de exibição que não interrompa a renderização estéreo. Aqui, vamos girar nos eixos X e Z para enfrentar o usuário.

Partir **StationaryQuadRenderer::Update**:

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

Para este exemplo, podemos também optar por processar o holograma no sistema de coordenadas de SpatialLocatorAttachedReferenceFrame, que é onde podemos posicionado o holograma. (Se tivéssemos decidido sejam renderizados usando outro sistema de coordenadas, podemos precisaria adquirir uma transformação de sistema de coordenadas do quadro de referência do dispositivo anexado a esse sistema de coordenadas.)

Partir **HolographicTagAlongSampleMain::Render**:

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

É só isso! O holograma será agora "Procurar" uma posição que é em metros 2 na frente de direção de olhar do usuário.

>[!NOTE]
>Este exemplo também carrega o conteúdo adicional - consulte StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Tratamento de perda de controle

Quando o dispositivo não pode localizar-se no mundo, o aplicativo passa por "perda de controle". Aplicativos de realidade mista do Windows devem ser capazes de lidar com tais interrupções para o sistema de acompanhamento posicionais. Essas interrupções podem ser observadas e respostas criado usando o evento LocatabilityChanged na SpatialLocator padrão.

De **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Quando seu aplicativo recebe um evento LocatabilityChanged, ele pode alterar o comportamento conforme necessário. Por exemplo, no estado PositionalTrackingInhibited, seu aplicativo pode pausar uma operação normal e renderizar uma [holograma tag-along](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) que exibe uma mensagem de aviso.

O modelo de aplicativo do Windows Holographic vem com um manipulador de LocatabilityChanged já criado para você. Por padrão, ele exibirá um aviso no console de depuração quando o controle de posição não está disponível. Você pode adicionar código a esse manipulador para fornecer uma resposta, conforme a necessidade do seu aplicativo.

De **AppMain.cpp:**

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

## <a name="spatial-mapping"></a>Mapeamento espacial

O [mapeamento espacial](spatial-mapping-in-directx.md) APIs tornam o uso de sistemas de coordenadas para obter as transformações de modelo para a superfície de malhas.

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas](coordinate-systems.md)
* [Âncoras espaciais](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a>
* [Olhar, gestos e controladores de movimento no DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)

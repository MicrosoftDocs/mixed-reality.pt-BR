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
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="53c4e-104">Sistemas de coordenadas no DirectX</span><span class="sxs-lookup"><span data-stu-id="53c4e-104">Coordinate systems in DirectX</span></span>

<span data-ttu-id="53c4e-105">[Sistemas de coordenadas](coordinate-systems.md) formam a base para a compreensão espacial oferecida pelas APIs de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="53c4e-105">[Coordinate systems](coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="53c4e-106">Hoje encaixado VR ou dispositivos VR única sala estabelecer um sistema de coordenadas primário para representar seu espaço controlado.</span><span class="sxs-lookup"><span data-stu-id="53c4e-106">Today's seated VR or single-room VR devices establish one primary coordinate system to represent their tracked space.</span></span> <span data-ttu-id="53c4e-107">Dispositivos de realidade mista do Windows, como o HoloLens são projetados para ser usada durante grandes ambientes indefinidos, com o dispositivo de descobrir e aprender sobre seu ambiente, como o usuário conduz ao redor.</span><span class="sxs-lookup"><span data-stu-id="53c4e-107">Windows Mixed Reality devices such as HoloLens are designed to be used throughout large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="53c4e-108">Isso permite que o dispositivo para se adaptar a melhorar continuamente o conhecimento sobre o usuário salas, mas resulta em sistemas de coordenadas que irá alterar sua relação umas às outras por meio do tempo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-108">This allows the device to adapt to continually-improving knowledge about the user's rooms, but results in coordinate systems that will change their relationship to one another through the lifetime of the app.</span></span> <span data-ttu-id="53c4e-109">Realidade mista do Windows oferece suporte a um amplo espectro de dispositivos, desde sentado fones imersivos em exposição por meio de quadros de referência anexado ao mundo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-109">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="53c4e-110">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="53c4e-110">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="53c4e-111">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="53c4e-111">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="53c4e-112">Sistemas de coordenadas espaciais no Windows</span><span class="sxs-lookup"><span data-stu-id="53c4e-112">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="53c4e-113">O tipo de principal usado para ponderar sobre sistemas de coordenadas do mundo real no Windows é o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span><span class="sxs-lookup"><span data-stu-id="53c4e-113">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="53c4e-114">Uma instância desse tipo representa um sistema de coordenadas arbitrário e fornece um método para obter uma matriz de transformação que você pode usar para transformar entre dois sistemas de coordenadas sem compreender os detalhes de cada.</span><span class="sxs-lookup"><span data-stu-id="53c4e-114">An instance of this type represents an arbitrary coordinate system and provides a method to get a transformation matrix that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="53c4e-115">Os métodos que retornam informações espaciais, representadas como pontos, raios ou volumes no ambiente do usuário, aceitará um parâmetro de SpatialCoordinateSystem para permitir que você decida o sistema de coordenadas no qual ele é mais útil para essas coordenadas a serem retornados.</span><span class="sxs-lookup"><span data-stu-id="53c4e-115">Methods that return spatial information, represented as points, rays, or volumes in the user's surroundings, will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="53c4e-116">As unidades para essas coordenadas sempre será em metros.</span><span class="sxs-lookup"><span data-stu-id="53c4e-116">The units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="53c4e-117">Um SpatialCoordinateSystem tem uma relação dinâmica com outros sistemas de coordenadas, inclusive aqueles que representam a posição do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-117">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="53c4e-118">A qualquer momento, o dispositivo pode ser capaz de localizar alguns sistemas de coordenadas e outros não.</span><span class="sxs-lookup"><span data-stu-id="53c4e-118">At any point in time, the device may be able to locate some coordinate systems and not others.</span></span> <span data-ttu-id="53c4e-119">Para a maioria dos sistemas de coordenadas, seu aplicativo deve estar pronto para lidar com períodos de tempo durante o qual eles não podem ser localizados.</span><span class="sxs-lookup"><span data-stu-id="53c4e-119">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="53c4e-120">Seu aplicativo não deve criar SpatialCoordinateSystems diretamente – em vez disso, eles devem ser consumidos por meio das APIs de percepção.</span><span class="sxs-lookup"><span data-stu-id="53c4e-120">Your application should not create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="53c4e-121">Há três fontes principais de sistemas de coordenadas nas APIs de percepção, cada um dos quais são mapeados para um conceito descrito na [sistemas de coordenadas](coordinate-systems.md) página:</span><span class="sxs-lookup"><span data-stu-id="53c4e-121">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](coordinate-systems.md) page:</span></span>
* <span data-ttu-id="53c4e-122">Para obter um quadro estacionário de referência, crie uma <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> ou obtenha um atuais <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="53c4e-122">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="53c4e-123">Para obter uma âncora espacial, crie uma <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span><span class="sxs-lookup"><span data-stu-id="53c4e-123">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="53c4e-124">Para obter um quadro de referência anexado, crie uma <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="53c4e-124">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="53c4e-125">Todos os sistemas de coordenadas retornados por esses objetos são destros, com + y cima + x à direita e + z com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="53c4e-125">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="53c4e-126">Você pode lembrar a direção na qual os pontos positivos do eixo z apontando os dedos de sua mão direita ou esquerda na direção x positivo e ondulação-los na direção y positivo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-126">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="53c4e-127">A direção do seu polegar aponta em sua direção ou para longe de você, é a direção em que o eixo z positivo aponta para esse sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="53c4e-127">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="53c4e-128">A ilustração a seguir mostra esses dois sistemas de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="53c4e-128">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="53c4e-129">![Sistemas de coordenadas do lado esquerdos e direito](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="53c4e-129">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="53c4e-130">*Sistemas de coordenadas do lado esquerdos e direito*</span><span class="sxs-lookup"><span data-stu-id="53c4e-130">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="53c4e-131">Para inicializar em um SpatialCoordinateSystem com base na posição de um HoloLens, use o <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> classe para criar qualquer um anexada ou parado quadro de referência, conforme descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="53c4e-131">To bootstrap into a SpatialCoordinateSystem based on the position of a HoloLens, use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference, as described in the sections below.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="53c4e-132">Hologramas lugar do mundo usando um estágio espacial</span><span class="sxs-lookup"><span data-stu-id="53c4e-132">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="53c4e-133">O sistema de coordenadas para opaco Windows Mixed Reality fones imersivos em exposição é acessado usando estático <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> propriedade.</span><span class="sxs-lookup"><span data-stu-id="53c4e-133">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="53c4e-134">Essa API fornece um sistema de coordenadas, informações sobre se o jogador está encaixado ou móvel, o limite de uma área segura para andar se o player é móvel, e uma indicação de se deseja ou não o fone de ouvido é direcional.</span><span class="sxs-lookup"><span data-stu-id="53c4e-134">This API provides a coordinate system, information about whether the player is seated or mobile, the boundary of a safe area for walking around if the player is mobile, and an indication of whether or not the headset is directional.</span></span> <span data-ttu-id="53c4e-135">Também há um manipulador de eventos para atualizações para o estágio espacial.</span><span class="sxs-lookup"><span data-stu-id="53c4e-135">There is also an event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="53c4e-136">Em primeiro lugar, vamos obter o estágio espacial e assine atualizações a ele:</span><span class="sxs-lookup"><span data-stu-id="53c4e-136">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="53c4e-137">O código de **inicialização estágio espacial**</span><span class="sxs-lookup"><span data-stu-id="53c4e-137">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="53c4e-138">No método OnCurrentChanged, seu aplicativo deve inspecionar o estágio espacial e atualizar a experiência de player adequadamente.</span><span class="sxs-lookup"><span data-stu-id="53c4e-138">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience accordingly.</span></span> <span data-ttu-id="53c4e-139">Neste exemplo, fornecemos uma visualização de limite do estágio, bem como a posição de início especificada pelo usuário e o intervalo do estágio de modo de exibição e o intervalo das propriedades de movimentação.</span><span class="sxs-lookup"><span data-stu-id="53c4e-139">In this example, we provide a visualization of the stage boundary, as well as the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="53c4e-140">Também voltamos ao nosso próprio sistema de coordenadas estático, quando um estágio não pode ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="53c4e-140">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="53c4e-141">O código de **atualização estágio espacial**</span><span class="sxs-lookup"><span data-stu-id="53c4e-141">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="53c4e-142">O conjunto de vértices que definem os limites de estágio são fornecidos na ordem no sentido horário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-142">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="53c4e-143">O shell do Windows Mixed Reality desenha um limite no limite quando o usuário se aproxima dela; Talvez você queira triangularize a área a ser examinável para suas próprias finalidades.</span><span class="sxs-lookup"><span data-stu-id="53c4e-143">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it; you may wish to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="53c4e-144">O algoritmo a seguir pode ser usado para triangularize o estágio.</span><span class="sxs-lookup"><span data-stu-id="53c4e-144">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="53c4e-145">O código de **triangularization estágio espacial**</span><span class="sxs-lookup"><span data-stu-id="53c4e-145">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="53c4e-146">Hologramas lugar do mundo usando um quadro estacionário de referência</span><span class="sxs-lookup"><span data-stu-id="53c4e-146">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="53c4e-147">O [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) classe representa um quadro de referência que [permanece estático](coordinate-systems.md#stationary-frame-of-reference) em relação ao ambiente do usuário como o usuário move.</span><span class="sxs-lookup"><span data-stu-id="53c4e-147">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="53c4e-148">Esse quadro de referência prioriza manter coordenadas estável perto do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-148">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="53c4e-149">É um uso de chave de um SpatialStationaryFrameOfReference atuar como o sistema de coordenadas de mundo subjacente dentro de um mecanismo de renderização durante a renderização hologramas.</span><span class="sxs-lookup"><span data-stu-id="53c4e-149">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="53c4e-150">Para obter um SpatialStationaryFrameOfReference, use o [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) classe e chame [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span><span class="sxs-lookup"><span data-stu-id="53c4e-150">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="53c4e-151">O Windows Holographic modelo do código do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="53c4e-151">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="53c4e-152">Quadros de referência estáticos são projetados para fornecer uma melhor ajuste posição em relação ao espaço total.</span><span class="sxs-lookup"><span data-stu-id="53c4e-152">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="53c4e-153">Posições individuais dentro desse quadro de referência são permitidas se um pouco.</span><span class="sxs-lookup"><span data-stu-id="53c4e-153">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="53c4e-154">Isso é normal, pois o dispositivo aprende mais sobre o ambiente.</span><span class="sxs-lookup"><span data-stu-id="53c4e-154">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="53c4e-155">Quando o posicionamento exato dos hologramas individuais é necessário, um SpatialAnchor deve ser usado para ancorar o holograma individual para uma posição no mundo real – por exemplo, um ponto do usuário indica para ser de interesse especial.</span><span class="sxs-lookup"><span data-stu-id="53c4e-155">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="53c4e-156">Posições de âncora não descompasso, mas podem ser corrigidas; a âncora usará a posição corrigida a partir o próximo quadro após a correção ocorreu.</span><span class="sxs-lookup"><span data-stu-id="53c4e-156">Anchor positions do not drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="53c4e-157">Hologramas lugar do mundo usando âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="53c4e-157">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="53c4e-158">[Âncoras espaciais](coordinate-systems.md#spatial-anchors) são uma ótima maneira de colocar hologramas em um local específico no mundo real, com o sistema garantindo a âncora permanece em vigor ao longo do tempo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-158">[Spatial anchors](coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="53c4e-159">Este tópico explica como criar e usar uma âncora e como trabalhar com dados de âncora.</span><span class="sxs-lookup"><span data-stu-id="53c4e-159">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="53c4e-160">Você pode criar um SpatialAnchor em qualquer posição e orientação dentro a SpatialCoordinateSystem de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="53c4e-160">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="53c4e-161">O dispositivo deve ser capaz de localizar esse sistema de coordenadas no momento, e o sistema não deve ter alcançado o limite das âncoras espaciais.</span><span class="sxs-lookup"><span data-stu-id="53c4e-161">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="53c4e-162">Depois de definido, o sistema de coordenadas de um SpatialAnchor ajusta continuamente para manter a posição exata e a orientação de sua localização inicial.</span><span class="sxs-lookup"><span data-stu-id="53c4e-162">Once defined, the coordinate system of a SpatialAnchor adjusts continually to retain the precise position and orientation of its initial location.</span></span> <span data-ttu-id="53c4e-163">Você pode usar este SpatialAnchor para renderizar hologramas aparecerão fixas no ambiente do usuário em que local exato.</span><span class="sxs-lookup"><span data-stu-id="53c4e-163">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="53c4e-164">Os efeitos dos ajustes que mantêm a âncora em vigor são ampliados como distância entre a âncora aumenta.</span><span class="sxs-lookup"><span data-stu-id="53c4e-164">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="53c4e-165">Portanto, você deve evitar processar o conteúdo em relação a uma âncora que é mais do que cerca de 3 medidores da origem dessa âncora.</span><span class="sxs-lookup"><span data-stu-id="53c4e-165">Therefore, you should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="53c4e-166">O [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) propriedade obtém um sistema de coordenadas que permite que você colocar o conteúdo em relação à âncora, com a atenuação aplicada quando o dispositivo ajusta o local exato da âncora.</span><span class="sxs-lookup"><span data-stu-id="53c4e-166">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="53c4e-167">Use o [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) propriedade e o correspondente [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) eventos para gerenciar esses ajustes por conta própria.</span><span class="sxs-lookup"><span data-stu-id="53c4e-167">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="53c4e-168">Persistir e compartilhar âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="53c4e-168">Persist and share spatial anchors</span></span>

<span data-ttu-id="53c4e-169">Você pode manter um SpatialAnchor localmente usando o [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) de classe e, em seguida, colocá-lo novamente em uma sessão de aplicativo futuras no mesmo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53c4e-169">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="53c4e-170">Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a>, você pode criar uma âncora de nuvem durável de um local SpatialAnchor, o que seu aplicativo pode, em seguida, localizar em vários HoloLens, dispositivos iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="53c4e-170">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="53c4e-171">Compartilhando uma âncora espacial comum em vários dispositivos, cada usuário pode ver o conteúdo renderizado em relação a essa âncora no mesmo local físico.</span><span class="sxs-lookup"><span data-stu-id="53c4e-171">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="53c4e-172">Isso permite experiências compartilhadas em tempo real.</span><span class="sxs-lookup"><span data-stu-id="53c4e-172">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="53c4e-173">Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para persistência holograma assíncrona em dispositivos Android, iOS e HoloLens.</span><span class="sxs-lookup"><span data-stu-id="53c4e-173">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="53c4e-174">Compartilhando uma âncora de nuvem durável espacial, vários dispositivos podem observar o holograma persistente mesmo ao longo do tempo, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-174">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="53c4e-175">Para começar a criação de experiências compartilhadas em seu aplicativo HoloLens, experimente o 5 minutos <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">guia de início rápido do Azure espacial âncoras HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="53c4e-175">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="53c4e-176">Quando estiver em funcionamento com âncoras espacial do Azure, você pode então <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">criar e localizar as âncoras em HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="53c4e-176">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="53c4e-177">Instruções passo a passo está disponível para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> também, permitindo que você compartilhe as âncoras mesmas em todos os dispositivos.</span><span class="sxs-lookup"><span data-stu-id="53c4e-177">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="53c4e-178">Criar SpatialAnchors para conteúdo holográfico</span><span class="sxs-lookup"><span data-stu-id="53c4e-178">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="53c4e-179">Para este exemplo de código, modificamos o Windows Holographic modelo de aplicativo para criar âncoras quando o **pressionado** gesto é detectado.</span><span class="sxs-lookup"><span data-stu-id="53c4e-179">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="53c4e-180">O cubo, em seguida, é colocado na âncora durante a passagem de renderização.</span><span class="sxs-lookup"><span data-stu-id="53c4e-180">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="53c4e-181">Como várias âncoras são suportadas pela classe auxiliar, já podemos colocar como muitos cubos que podemos usar esse exemplo de código!</span><span class="sxs-lookup"><span data-stu-id="53c4e-181">Since multiple anchors are supported by the helper class, we can place as many cubes as we want using this code sample!</span></span>

<span data-ttu-id="53c4e-182">Observe que as IDs para âncoras são algo que controlar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-182">Note that the IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="53c4e-183">Neste exemplo, criamos um esquema de nomenclatura é sequencial com base no número de âncoras armazenados atualmente na coleção do aplicativo das âncoras.</span><span class="sxs-lookup"><span data-stu-id="53c4e-183">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="53c4e-184">De forma assíncrona de carga e armazenar em cache, o SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="53c4e-184">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="53c4e-185">Vamos ver como escrever uma classe SampleSpatialAnchorHelper que ajuda a lidar com essa persistência, incluindo:</span><span class="sxs-lookup"><span data-stu-id="53c4e-185">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="53c4e-186">Armazenar uma coleção de âncoras de na memória, indexados por uma chave de Platform:: String.</span><span class="sxs-lookup"><span data-stu-id="53c4e-186">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="53c4e-187">Carregando as âncoras de SpatialAnchorStore do sistema, que é mantido separado da coleção na memória local.</span><span class="sxs-lookup"><span data-stu-id="53c4e-187">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="53c4e-188">Salvando a coleção na memória local âncoras a SpatialAnchorStore quando o aplicativo opta por fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-188">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="53c4e-189">Aqui está como economizar [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objetos na [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="53c4e-189">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="53c4e-190">Quando a classe é iniciado, solicitamos o SpatialAnchorStore assincronamente.</span><span class="sxs-lookup"><span data-stu-id="53c4e-190">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="53c4e-191">Isso envolve a e/s do sistema como a API carrega o repositório de âncora e essa API é feita assíncrona, de modo que a e/s é sem bloqueio.</span><span class="sxs-lookup"><span data-stu-id="53c4e-191">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="53c4e-192">Você receberá um SpatialAnchorStore que você pode usar para salvar as âncoras.</span><span class="sxs-lookup"><span data-stu-id="53c4e-192">You will be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="53c4e-193">Este é um IMapView que associa os valores de chave que são cadeias de caracteres, com valores de dados que são SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="53c4e-193">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="53c4e-194">Em nosso código de exemplo, armazenamos isso em uma variável de membro de classe privada é acessível por meio de uma função pública de nossa classe auxiliar.</span><span class="sxs-lookup"><span data-stu-id="53c4e-194">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="53c4e-195">Não se esqueça de ligar os eventos de suspender/retomar para salvar e carregar o repositório de âncora.</span><span class="sxs-lookup"><span data-stu-id="53c4e-195">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="53c4e-196">Salve o conteúdo para o repositório de âncora</span><span class="sxs-lookup"><span data-stu-id="53c4e-196">Save content to the anchor store</span></span>

<span data-ttu-id="53c4e-197">Quando o sistema suspende o seu aplicativo, você precisará salvar suas âncoras espaciais para o repositório de âncora.</span><span class="sxs-lookup"><span data-stu-id="53c4e-197">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="53c4e-198">Você também pode optar por salvar as âncoras para o repositório de âncora em outras ocasiões, como você pode encontrar necessários para a implementação do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-198">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="53c4e-199">Quando estiver pronto para tentar salvar as âncoras de memória para o SpatialAnchorStore, pode executar um loop por meio de sua coleção e tente salvar cada um deles.</span><span class="sxs-lookup"><span data-stu-id="53c4e-199">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="53c4e-200">Carregar o conteúdo do armazenamento de âncora quando o aplicativo é retomado</span><span class="sxs-lookup"><span data-stu-id="53c4e-200">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="53c4e-201">Quando seu aplicativo é retomado, ou a qualquer momento necessário para implementaiton do seu aplicativo, você pode restaurar as âncoras que foram salvos anteriormente para o AnchorStore por transferi-las da IMapView âncora da loja ao seu próprio banco de dados na memória de SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="53c4e-201">When your app resumes, or at any other time necessary for your app's implementaiton, you can restore anchors that were previously saved to the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors.</span></span>

<span data-ttu-id="53c4e-202">Para restaurar as âncoras do SpatialAnchorStore, restaure cada um deles que você está interessado em sua própria coleção na memória.</span><span class="sxs-lookup"><span data-stu-id="53c4e-202">To restore anchors from the SpatialAnchorStore, restore each one that you are interested in to your own in-memory collection.</span></span>

<span data-ttu-id="53c4e-203">Você precisa de seu próprio banco de dados na memória de SpatialAnchors; alguma maneira para associar as cadeias de caracteres com o SpatialAnchors criado por você.</span><span class="sxs-lookup"><span data-stu-id="53c4e-203">You need your own in-memory database of SpatialAnchors; some way to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="53c4e-204">Em nosso código de exemplo, podemos optar por usar um IMAP para armazenar as âncoras, que torna mais fácil de usar o mesmo valor de chave e os dados para o SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="53c4e-204">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="53c4e-205">Uma âncora que é restaurada pode não ser localizáveis imediatamente.</span><span class="sxs-lookup"><span data-stu-id="53c4e-205">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="53c4e-206">Por exemplo, ele pode ser uma âncora em uma sala separada ou em um prédio diferentes completamente.</span><span class="sxs-lookup"><span data-stu-id="53c4e-206">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="53c4e-207">Âncoras recuperadas do AnchorStore devem ser testadas para locatability antes de usá-los.</span><span class="sxs-lookup"><span data-stu-id="53c4e-207">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="53c4e-208">Nesse código de exemplo, podemos recuperar todas as âncoras do AnchorStore.</span><span class="sxs-lookup"><span data-stu-id="53c4e-208">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="53c4e-209">Isso não é um requisito; seu aplicativo poderia assim como escolher um certo subconjunto de âncoras usando valores de chave de cadeia de caracteres que são significativas para sua implementação.</span><span class="sxs-lookup"><span data-stu-id="53c4e-209">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="53c4e-210">Limpar o repositório de âncora, quando necessário</span><span class="sxs-lookup"><span data-stu-id="53c4e-210">Clear the anchor store, when needed</span></span>

<span data-ttu-id="53c4e-211">Às vezes, você precisará limpar o estado do aplicativo e gravar novos dados.</span><span class="sxs-lookup"><span data-stu-id="53c4e-211">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="53c4e-212">Aqui está como fazer isso com o [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="53c4e-212">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="53c4e-213">Usando a nossa classe auxiliar, é praticamente desnecessário encapsular a função Clear.</span><span class="sxs-lookup"><span data-stu-id="53c4e-213">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="53c4e-214">Podemos optar por fazer isso em nossa implementação de exemplo, porque nossa classe auxiliar recebe a responsabilidade de proprietário de instância SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="53c4e-214">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="53c4e-215">Exemplo: Relacionados a sistemas de coordenadas de âncora para sistemas de coordenadas de quadro estacionário de referência</span><span class="sxs-lookup"><span data-stu-id="53c4e-215">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="53c4e-216">Digamos que você tem uma âncora, e você deseja relacionar algo no sistema de coordenadas da sua âncora para o SpatialStationaryReferenceFrame que você já está usando para a maioria dos seus outros tipos de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-216">Let's say that you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame that you’re already using for most of your other content.</span></span> <span data-ttu-id="53c4e-217">Você pode usar [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) para obter uma transformação do sistema de coordenadas da âncora para que um quadro estacionário de referência:</span><span class="sxs-lookup"><span data-stu-id="53c4e-217">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to obtain a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="53c4e-218">Esse processo é útil para você de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="53c4e-218">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="53c4e-219">Informa se os dois quadros de referência pode ser compreendido em relação a um do outro, e;</span><span class="sxs-lookup"><span data-stu-id="53c4e-219">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="53c4e-220">Nesse caso, ele fornece uma transformação para ir diretamente de um sistema de coordenadas para outro.</span><span class="sxs-lookup"><span data-stu-id="53c4e-220">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="53c4e-221">Com essas informações, você tem uma compreensão da relação entre objetos entre dois quadros de referência espacial.</span><span class="sxs-lookup"><span data-stu-id="53c4e-221">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="53c4e-222">Para renderização, você geralmente pode obter resultados melhores através do agrupamento de objetos de acordo com seu quadro de referência original ou âncora.</span><span class="sxs-lookup"><span data-stu-id="53c4e-222">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="53c4e-223">Execute uma passagem de desenho separada para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-223">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="53c4e-224">As matrizes de exibição são mais precisas para objetos com transformações de modelo que são criadas inicialmente com o mesmo sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="53c4e-224">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="53c4e-225">Criar hologramas usando um dispositivo anexado quadro de referência</span><span class="sxs-lookup"><span data-stu-id="53c4e-225">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="53c4e-226">Há momentos em que você deseja renderizar um holograma que [permanece anexado](coordinate-systems.md#attached-frame-of-reference) para o local do dispositivo, por exemplo, um painel com informações ou uma mensagem informativa de depuração quando o dispositivo só é capaz de determinar sua orientação e não é sua posição no espaço.</span><span class="sxs-lookup"><span data-stu-id="53c4e-226">There are times when you want to render a hologram that [remains attached](coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="53c4e-227">Para fazer isso, usamos um quadro de referência anexado.</span><span class="sxs-lookup"><span data-stu-id="53c4e-227">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="53c4e-228">A classe SpatialLocatorAttachedFrameOfReference define os sistemas de coordenadas que estão em relação ao dispositivo em vez de para o mundo real.</span><span class="sxs-lookup"><span data-stu-id="53c4e-228">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="53c4e-229">Este quadro tem um título fixo em relação ao ambiente do usuário que aponta para a direção do usuário estava enfrentando quando o quadro de referência foi criado.</span><span class="sxs-lookup"><span data-stu-id="53c4e-229">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="53c4e-230">Daí em seguida diante, todas as orientações nesse quadro de referência são relativos ao título fixo, mesmo que o usuário gira o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-230">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="53c4e-231">Para HoloLens, a origem do sistema de coordenadas desse quadro está localizada no Centro de rotação da cabeça do usuário, para que sua posição não é afetada pela rotação principal.</span><span class="sxs-lookup"><span data-stu-id="53c4e-231">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="53c4e-232">Seu aplicativo pode especificar um deslocamento em relação a esse ponto para posicionar hologramas na frente do usuário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-232">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="53c4e-233">Para obter um SpatialLocatorAttachedFrameOfReference, use a classe SpatialLocator e chame CreateAttachedFrameOfReferenceAtCurrentHeading.</span><span class="sxs-lookup"><span data-stu-id="53c4e-233">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="53c4e-234">Observe que isso se aplica aos dispositivos todo intervalo do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="53c4e-234">Note that this applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="53c4e-235">Use um quadro de referência anexado ao dispositivo</span><span class="sxs-lookup"><span data-stu-id="53c4e-235">Use a reference frame attached to the device</span></span>

<span data-ttu-id="53c4e-236">Essas seções falam sobre o que mudou no modelo de aplicativo do Windows Holographic para habilitar um dispositivo anexado quadro de referência usando essa API.</span><span class="sxs-lookup"><span data-stu-id="53c4e-236">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="53c4e-237">Observe que esse "anexada" holograma coexistirão hologramas estáticos ou ancoradas e também pode ser usada quando o dispositivo estiver temporariamente não é possível localizar sua posição no mundo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-237">Note that this "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="53c4e-238">Primeiro, alteramos o modelo para armazenar um SpatialLocatorAttachedFrameOfReference em vez de um SpatialStationaryFrameOfReference:</span><span class="sxs-lookup"><span data-stu-id="53c4e-238">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="53c4e-239">Partir **HolographicTagAlongSampleMain.h**:</span><span class="sxs-lookup"><span data-stu-id="53c4e-239">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="53c4e-240">Partir **HolographicTagAlongSampleMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="53c4e-240">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="53c4e-241">Durante a atualização, agora podemos obter o sistema de coordenadas em que o carimbo de hora obtido com a previsão de quadro.</span><span class="sxs-lookup"><span data-stu-id="53c4e-241">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="53c4e-242">Obter uma ponteiro espacial pose e siga a olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="53c4e-242">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="53c4e-243">Queremos que nosso holograma de exemplo a seguir do usuário [olhares](gaze.md), semelhante a como o shell holográfico pode seguir olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-243">We want our example hologram to follow the user's [gaze](gaze.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="53c4e-244">Para isso, precisamos obter o SpatialPointerPose do mesmo carimbo de hora.</span><span class="sxs-lookup"><span data-stu-id="53c4e-244">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="53c4e-245">Este SpatialPointerPose tem as informações necessárias para posicionar o holograma de acordo com o [rumo atual do usuário](gaze,-gestures,-and-motion-controllers-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="53c4e-245">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze,-gestures,-and-motion-controllers-in-directx.md).</span></span>

<span data-ttu-id="53c4e-246">Por motivos de conforto de usuário, podemos usar interpolação linear ("lerp") para suavizar a alteração na posição, de modo que ele ocorre durante um período de tempo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-246">For reasons of user comfort, we use linear interpolation ("lerp") to smooth the change in position such that it occurs over a period of time.</span></span> <span data-ttu-id="53c4e-247">Isso é mais à vontade para o usuário que o holograma para seu olhar o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="53c4e-247">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="53c4e-248">Lerping que posição do holograma de tag-along também nos permite estabilizar o holograma por retardamento movimentação; Se não fizermos essa interrupção, o usuário veria o holograma tremulação devido a que normalmente é considerado como sendo imperceptível movimentos da cabeça do usuário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-248">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement; if we did not do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="53c4e-249">Partir **StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="53c4e-249">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="53c4e-250">No caso de um painel de depuração, você pode optar reposicionar o holograma desativado para o lado um pouco para que ele não obstruir sua exibição.</span><span class="sxs-lookup"><span data-stu-id="53c4e-250">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it does not obstruct your view.</span></span> <span data-ttu-id="53c4e-251">Aqui está um exemplo de como você pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="53c4e-251">Here's an example of how you might do that.</span></span>

<span data-ttu-id="53c4e-252">Para **StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="53c4e-252">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="53c4e-253">Girar o holograma para enfrentar a câmera</span><span class="sxs-lookup"><span data-stu-id="53c4e-253">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="53c4e-254">Não é suficiente simplesmente posicionar holograma, que nesse caso é um quad; podemos também deve girar o objeto para o usuário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-254">It is not enough to simply position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="53c4e-255">Observe que essa rotação ocorre no espaço de mundo, porque esse tipo de billboarding permite o holograma permaneça uma parte do ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-255">Note that this rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="53c4e-256">Espaço do modo de exibição billboarding não é tão à vontade porque o holograma fica bloqueado para a orientação da tela; Nesse caso, você também teria que interpolar entre as matrizes de exibição da esquerda e direita para adquirir uma transformação de mensagem de instalação de espaço do modo de exibição que não interrompa a renderização estéreo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-256">View-space billboarding is not as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices in order to acquire a view-space billboard transform that does not disrupt stereo rendering.</span></span> <span data-ttu-id="53c4e-257">Aqui, vamos girar nos eixos X e Z para enfrentar o usuário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-257">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="53c4e-258">Partir **StationaryQuadRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="53c4e-258">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="53c4e-259">Renderizar o holograma anexado</span><span class="sxs-lookup"><span data-stu-id="53c4e-259">Render the attached hologram</span></span>

<span data-ttu-id="53c4e-260">Para este exemplo, podemos também optar por processar o holograma no sistema de coordenadas de SpatialLocatorAttachedReferenceFrame, que é onde podemos posicionado o holograma.</span><span class="sxs-lookup"><span data-stu-id="53c4e-260">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="53c4e-261">(Se tivéssemos decidido sejam renderizados usando outro sistema de coordenadas, podemos precisaria adquirir uma transformação de sistema de coordenadas do quadro de referência do dispositivo anexado a esse sistema de coordenadas.)</span><span class="sxs-lookup"><span data-stu-id="53c4e-261">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="53c4e-262">Partir **HolographicTagAlongSampleMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="53c4e-262">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="53c4e-263">É só isso!</span><span class="sxs-lookup"><span data-stu-id="53c4e-263">That's it!</span></span> <span data-ttu-id="53c4e-264">O holograma será agora "Procurar" uma posição que é em metros 2 na frente de direção de olhar do usuário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-264">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="53c4e-265">Este exemplo também carrega o conteúdo adicional - consulte StationaryQuadRenderer.cpp.</span><span class="sxs-lookup"><span data-stu-id="53c4e-265">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="53c4e-266">Tratamento de perda de controle</span><span class="sxs-lookup"><span data-stu-id="53c4e-266">Handling tracking loss</span></span>

<span data-ttu-id="53c4e-267">Quando o dispositivo não pode localizar-se no mundo, o aplicativo passa por "perda de controle".</span><span class="sxs-lookup"><span data-stu-id="53c4e-267">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="53c4e-268">Aplicativos de realidade mista do Windows devem ser capazes de lidar com tais interrupções para o sistema de acompanhamento posicionais.</span><span class="sxs-lookup"><span data-stu-id="53c4e-268">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="53c4e-269">Essas interrupções podem ser observadas e respostas criado usando o evento LocatabilityChanged na SpatialLocator padrão.</span><span class="sxs-lookup"><span data-stu-id="53c4e-269">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="53c4e-270">De **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="53c4e-270">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="53c4e-271">Quando seu aplicativo recebe um evento LocatabilityChanged, ele pode alterar o comportamento conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="53c4e-271">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="53c4e-272">Por exemplo, no estado PositionalTrackingInhibited, seu aplicativo pode pausar uma operação normal e renderizar uma [holograma tag-along](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) que exibe uma mensagem de aviso.</span><span class="sxs-lookup"><span data-stu-id="53c4e-272">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="53c4e-273">O modelo de aplicativo do Windows Holographic vem com um manipulador de LocatabilityChanged já criado para você.</span><span class="sxs-lookup"><span data-stu-id="53c4e-273">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="53c4e-274">Por padrão, ele exibirá um aviso no console de depuração quando o controle de posição não está disponível.</span><span class="sxs-lookup"><span data-stu-id="53c4e-274">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="53c4e-275">Você pode adicionar código a esse manipulador para fornecer uma resposta, conforme a necessidade do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53c4e-275">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="53c4e-276">De **AppMain.cpp:**</span><span class="sxs-lookup"><span data-stu-id="53c4e-276">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="53c4e-277">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="53c4e-277">Spatial mapping</span></span>

<span data-ttu-id="53c4e-278">O [mapeamento espacial](spatial-mapping-in-directx.md) APIs tornam o uso de sistemas de coordenadas para obter as transformações de modelo para a superfície de malhas.</span><span class="sxs-lookup"><span data-stu-id="53c4e-278">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="53c4e-279">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53c4e-279">See also</span></span>
* [<span data-ttu-id="53c4e-280">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="53c4e-280">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="53c4e-281">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="53c4e-281">Spatial anchors</span></span>](spatial-anchors.md)
* <span data-ttu-id="53c4e-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a></span><span class="sxs-lookup"><span data-stu-id="53c4e-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="53c4e-283">Olhar, gestos e controladores de movimento no DirectX</span><span class="sxs-lookup"><span data-stu-id="53c4e-283">Gaze, gestures, and motion controllers in DirectX</span></span>](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="53c4e-284">Mapeamento espacial no DirectX</span><span class="sxs-lookup"><span data-stu-id="53c4e-284">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)

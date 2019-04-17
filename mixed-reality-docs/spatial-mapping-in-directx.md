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
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="dc956-105">Mapeamento espacial no DirectX</span><span class="sxs-lookup"><span data-stu-id="dc956-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="dc956-106">Este tópico descreve como implementar [mapeamento espacial](spatial-mapping.md) em seu aplicativo DirectX.</span><span class="sxs-lookup"><span data-stu-id="dc956-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="dc956-107">Isso inclui uma explicação detalhada do que o aplicativo de exemplo de mapeamento espacial que está incluído no SDK da plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="dc956-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="dc956-108">Este tópico usa o código a partir de [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) exemplo de código da UWP.</span><span class="sxs-lookup"><span data-stu-id="dc956-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="dc956-109">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="dc956-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="dc956-110">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="dc956-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="dc956-111">Visão geral de desenvolvimento do DirectX</span><span class="sxs-lookup"><span data-stu-id="dc956-111">DirectX development overview</span></span>

<span data-ttu-id="dc956-112">Desenvolvimento de aplicativos nativos para mapeamento espacial usa as APIs sob o [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span><span class="sxs-lookup"><span data-stu-id="dc956-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="dc956-113">Essas APIs fornecem controle total da funcionalidade de mapeamento espacial, de maneira análoga diretamente para o mapeamento espacial APIs expostas pelos [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="dc956-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="dc956-114">APIs de percepção</span><span class="sxs-lookup"><span data-stu-id="dc956-114">Perception APIs</span></span>

<span data-ttu-id="dc956-115">Os principais tipos fornecidos para o desenvolvimento de mapeamento espacial são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="dc956-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="dc956-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornece informações sobre as superfícies em regiões especificado pelo aplicativo de espaço próxima ao usuário, na forma de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="dc956-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="dc956-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descreve uma única empacotamentos espacial superfície, incluindo uma ID exclusiva, delimitadora volume e a hora da última alteração.</span><span class="sxs-lookup"><span data-stu-id="dc956-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="dc956-118">Ele fornecerá um SpatialSurfaceMesh assincronamente mediante solicitação.</span><span class="sxs-lookup"><span data-stu-id="dc956-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="dc956-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contém os parâmetros usados para personalizar os objetos de SpatialSurfaceMesh solicitados do SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="dc956-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="dc956-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa os dados de malha para uma única superfície espacial.</span><span class="sxs-lookup"><span data-stu-id="dc956-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="dc956-121">Os dados para as posições de vértice, normais de vértice e índices de triângulo estão contidos nos objetos do membro SpatialSurfaceMeshBuffer.</span><span class="sxs-lookup"><span data-stu-id="dc956-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="dc956-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) encapsula um único tipo de dados da malha.</span><span class="sxs-lookup"><span data-stu-id="dc956-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="dc956-123">Ao desenvolver um aplicativo usando essas APIs, o fluxo de programa básico terá esta aparência (conforme demonstrado no aplicativo de exemplo descrito abaixo):</span><span class="sxs-lookup"><span data-stu-id="dc956-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="dc956-124">**Configurar seu SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="dc956-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="dc956-125">Chame [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), para garantir que o usuário concedeu permissão para seu aplicativo para usar recursos de mapeamento espacial do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dc956-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="dc956-126">Criar uma instância de um objeto SpatialSurfaceObserver.</span><span class="sxs-lookup"><span data-stu-id="dc956-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="dc956-127">Chame [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar as regiões de espaço no qual você deseja obter informações sobre as superfícies espaciais.</span><span class="sxs-lookup"><span data-stu-id="dc956-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="dc956-128">Você pode modificar essas regiões no futuro, simplesmente chamando essa função novamente.</span><span class="sxs-lookup"><span data-stu-id="dc956-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="dc956-129">Cada região é especificado usando um [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="dc956-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="dc956-130">Inscreva-se a [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) evento, que será acionado sempre que novas informações sobre as superfícies espaciais nas regiões de espaço que você especificou estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="dc956-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="dc956-131">**Processar eventos ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="dc956-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="dc956-132">No manipulador de eventos, chame [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para receber um mapa de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="dc956-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="dc956-133">Usando esse mapa, você pode atualizar seus registros de quais espaciais superfícies [existem no ambiente do usuário](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="dc956-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="dc956-134">Para cada objeto SpatialSurfaceInfo, você pode consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) determinar as extensões espaciais da superfície, expresso em uma [sistema de coordenadas espacial](coordinate-systems.md) de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="dc956-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="dc956-135">Se você optar por solicitar malha para uma superfície espacial, chame [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="dc956-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="dc956-136">Você pode fornecer opções que especificam o formato dos dados retornados de malha e a densidade desejada de triângulos.</span><span class="sxs-lookup"><span data-stu-id="dc956-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="dc956-137">**Receber e processar a malha**</span><span class="sxs-lookup"><span data-stu-id="dc956-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="dc956-138">Cada chamada para TryComputeLatestMeshAsync será aysnchronously retornar um objeto SpatialSurfaceMesh.</span><span class="sxs-lookup"><span data-stu-id="dc956-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="dc956-139">Deste objeto, você pode acessar os objetos SpatialSurfaceMeshBuffer contidos para acessar os índices de triângulo, posições de vértice e (se solicitado) normais de vértices da malha.</span><span class="sxs-lookup"><span data-stu-id="dc956-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="dc956-140">Estes dados serão em um formato diretamente compatível com o [APIs do Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usados para renderizar as malhas.</span><span class="sxs-lookup"><span data-stu-id="dc956-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="dc956-141">A partir daqui seu aplicativo pode, opcionalmente, executar análise ou [processando](spatial-mapping.md#mesh-processing) dos dados de malha e usá-lo para [renderização](spatial-mapping.md#rendering) e física [raycasting e colisão](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="dc956-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="dc956-142">Um detalhe importante a observar é que você deve aplicar uma escala para as posições de vértice de malha (por exemplo, no sombreador de vértice usados para renderizar as malhas), para convertê-los das unidades otimizado inteiro no qual eles são armazenados no buffer, para medidores.</span><span class="sxs-lookup"><span data-stu-id="dc956-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="dc956-143">Você pode recuperar essa escala chamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="dc956-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="dc956-144">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="dc956-144">Troubleshooting</span></span>
* <span data-ttu-id="dc956-145">Não se esqueça de dimensionar as posições de vértice de malha em seu sombreador de vértice, usando a escala retornada por [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="dc956-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="dc956-146">Passo a passo o exemplo de código mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="dc956-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="dc956-147">O [mapeamento espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) exemplo de código inclui o código que você pode usar para começar a carregar malhas superfície em seu aplicativo, incluindo a infraestrutura para gerenciar e malhas de superfície de renderização.</span><span class="sxs-lookup"><span data-stu-id="dc956-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="dc956-148">Agora, veremos como adicionar funcionalidade de mapeamento de superfície para seu aplicativo DirectX.</span><span class="sxs-lookup"><span data-stu-id="dc956-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="dc956-149">Você pode adicionar este código ao seu [modelo de aplicativo do Windows Holographic](creating-a-holographic-directx-project.md) projeto, ou você pode acompanhar navegando-se o código de exemplo mencionado acima.</span><span class="sxs-lookup"><span data-stu-id="dc956-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="dc956-150">Este exemplo de código se baseia no modelo de aplicativo do Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="dc956-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="dc956-151">Configurar seu aplicativo para usar o recurso de spatialPerception</span><span class="sxs-lookup"><span data-stu-id="dc956-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="dc956-152">Seu aplicativo deve ser capaz de usar o recurso de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="dc956-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="dc956-153">Isso é necessário porque a malha espacial é uma representação do ambiente do usuário, que pode ser considerado dados privados.</span><span class="sxs-lookup"><span data-stu-id="dc956-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="dc956-154">Declare esse recurso no arquivo Package. appxmanifest para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc956-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="dc956-155">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="dc956-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="dc956-156">O recurso é proveniente de **uap2** namespace.</span><span class="sxs-lookup"><span data-stu-id="dc956-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="dc956-157">Para obter acesso a esse namespace em seu manifesto, incluí-lo como um *xlmns* atributo no &lt;pacote > elemento.</span><span class="sxs-lookup"><span data-stu-id="dc956-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="dc956-158">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="dc956-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="dc956-159">Verificar se há suporte ao recurso de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="dc956-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="dc956-160">Realidade mista do Windows oferece suporte a uma ampla variedade de dispositivos, incluindo dispositivos que não dão suporte a mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="dc956-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="dc956-161">Se seu aplicativo pode usar o mapeamento espacial, ou deve usar o mapeamento espacial, para fornecer a funcionalidade, ele deve verificar para certificar-se de que há suporte para mapeamento espacial antes de tentar usá-lo.</span><span class="sxs-lookup"><span data-stu-id="dc956-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="dc956-162">Por exemplo, se o mapeamento espacial é exigido pelo seu aplicativo de realidade misturada, ele deve exibir uma mensagem para esse efeito se um usuário tentar executá-lo em um dispositivo sem mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="dc956-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="dc956-163">Ou então, seu aplicativo pode ser capaz de renderizar seu próprio ambiente virtual no lugar do ambiente do usuário, proporcionando uma experiência semelhante a que aconteceria se o mapeamento espacial estava disponível.</span><span class="sxs-lookup"><span data-stu-id="dc956-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="dc956-164">Em qualquer evento, essa API permite que seu aplicativo a serem consideradas quando ele não será obter dados de mapeamento espacial e responder da maneira apropriada.</span><span class="sxs-lookup"><span data-stu-id="dc956-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="dc956-165">Para verificar se o dispositivo atual para o suporte de mapeamento espacial, primeiro verifique se que o contrato UWP está no nível 4 ou superior e, em seguida, chame SpatialSurfaceObserver::IsSupported().</span><span class="sxs-lookup"><span data-stu-id="dc956-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="dc956-166">Aqui está como fazer isso no contexto do [mapeamento espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="dc956-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="dc956-167">O suporte é verificado antes de solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="dc956-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="dc956-168">A API de SpatialSurfaceObserver::IsSupported() está disponível a partir do SDK versão 15063.</span><span class="sxs-lookup"><span data-stu-id="dc956-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="dc956-169">Se necessário, redirecione seu projeto para a versão de plataforma 15063 antes de usar essa API.</span><span class="sxs-lookup"><span data-stu-id="dc956-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="dc956-170">Observe que, quando o contrato UWP é menor que o nível 4, o aplicativo deve continuar como se o dispositivo é capaz de fazer o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="dc956-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="dc956-171">Solicitar acesso a dados de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="dc956-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="dc956-172">Seu aplicativo precisa solicitar permissão para acessar dados de mapeamento espacial antes de tentar criar qualquer superfície observadores.</span><span class="sxs-lookup"><span data-stu-id="dc956-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="dc956-173">Aqui está um exemplo com base em nosso exemplo de código de mapeamento de superfície, com mais detalhes posteriormente fornecidas nesta página:</span><span class="sxs-lookup"><span data-stu-id="dc956-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="dc956-174">Criar um observador de superfície</span><span class="sxs-lookup"><span data-stu-id="dc956-174">Create a surface observer</span></span>

<span data-ttu-id="dc956-175">O **Windows::Perception::Spatial::Surfaces** namespace inclui as [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) classe, que observa um ou mais volumes que você especificar em uma [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="dc956-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="dc956-176">Use uma [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instância para acessar dados de malha superficial em tempo real.</span><span class="sxs-lookup"><span data-stu-id="dc956-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="dc956-177">Partir **AppMain.h**:</span><span class="sxs-lookup"><span data-stu-id="dc956-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="dc956-178">Conforme observado na seção anterior, você deve solicitar acesso aos dados de mapeamento espacial antes de seu aplicativo pode usá-lo.</span><span class="sxs-lookup"><span data-stu-id="dc956-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="dc956-179">Esse acesso é concedido automaticamente o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dc956-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="dc956-180">Em seguida, você precisará configurar o observador de superfície para observar um volume específico por delimitador.</span><span class="sxs-lookup"><span data-stu-id="dc956-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="dc956-181">Aqui, podemos observar uma caixa que é 20 x 20 x 5 metros, centralizada na origem do sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="dc956-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="dc956-182">Observe que você pode definir vários volumes delimitadora.</span><span class="sxs-lookup"><span data-stu-id="dc956-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="dc956-183">*Este é o pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="dc956-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="dc956-184">Também é possível usar outras formas de delimitadoras - como frustum um modo de exibição, ou uma caixa delimitadora que não é o eixo alinhado.</span><span class="sxs-lookup"><span data-stu-id="dc956-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="dc956-185">*Este é o pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="dc956-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="dc956-186">Se seu aplicativo precisa fazer nada diferente quando dados de mapeamento de superfície não estiverem disponíveis, você pode escrever código para responder ao caso em que o [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) não está **permitidos** - por exemplo, ele será permitido em PCs com dispositivos de imersão anexados porque esses dispositivos não têm o hardware para mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="dc956-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="dc956-187">Para esses dispositivos, em vez disso, você deve confiar no Palco espacial para obter informações sobre o ambiente e a configuração do dispositivo do usuário.</span><span class="sxs-lookup"><span data-stu-id="dc956-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="dc956-188">Inicializar e atualizar a coleção de malha superficial</span><span class="sxs-lookup"><span data-stu-id="dc956-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="dc956-189">Se o observador de superfície foi criado com êxito, poderemos continuar para inicializar nossa coleção de malha superficial.</span><span class="sxs-lookup"><span data-stu-id="dc956-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="dc956-190">Aqui, podemos usar a API do modelo de pull para obter o conjunto atual de superfícies observadas imediatamente:</span><span class="sxs-lookup"><span data-stu-id="dc956-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="dc956-191">Também é um modelo de push disponível para obter dados de malha superficial.</span><span class="sxs-lookup"><span data-stu-id="dc956-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="dc956-192">Você é livre para projetar seu aplicativo para usar somente o modelo de pull se você escolher, caso em que você vai pesquisar dados frequência - por exemplo, uma vez por quadro - ou durante um período de tempo específico, como durante a instalação do jogo.</span><span class="sxs-lookup"><span data-stu-id="dc956-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="dc956-193">Nesse caso, o código acima é o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="dc956-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="dc956-194">Em nosso exemplo de código, que escolhemos demonstrar o uso de ambos os modelos para fins de pedagógico.</span><span class="sxs-lookup"><span data-stu-id="dc956-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="dc956-195">Aqui, podemos assinar um evento para receber dados de malha superficial atualizadas sempre que o sistema reconhece uma alteração.</span><span class="sxs-lookup"><span data-stu-id="dc956-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="dc956-196">Nosso exemplo de código também está configurado para responder a esses eventos.</span><span class="sxs-lookup"><span data-stu-id="dc956-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="dc956-197">Vamos examinar como fazemos isso.</span><span class="sxs-lookup"><span data-stu-id="dc956-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="dc956-198">**OBSERVAÇÃO:** Isso pode não ser a maneira mais eficiente para seu aplicativo lidar com dados da malha.</span><span class="sxs-lookup"><span data-stu-id="dc956-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="dc956-199">Esse código é gravado para maior clareza e não é otimizado.</span><span class="sxs-lookup"><span data-stu-id="dc956-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="dc956-200">Os dados de malha superficial são fornecidos em um mapa de somente leitura que armazena [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objetos usando [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de chave.</span><span class="sxs-lookup"><span data-stu-id="dc956-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="dc956-201">Para processar esses dados, vamos primeiros para valores de chave que não estão em nossa coleção.</span><span class="sxs-lookup"><span data-stu-id="dc956-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="dc956-202">Obter detalhes sobre como os dados são armazenados em nosso aplicativo de exemplo serão apresentadas neste tópico.</span><span class="sxs-lookup"><span data-stu-id="dc956-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="dc956-203">Também precisamos remover malhas de superfície que estão em nossa coleção de malha superficial, mas que não estão na coleção de sistema mais.</span><span class="sxs-lookup"><span data-stu-id="dc956-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="dc956-204">Para fazer isso, precisamos fazer algo semelhante ao oposto do que acabamos de Mostrar para adição e atualização de malhas; executamos um loop na coleção de nosso aplicativo e verificar se o **Guid** temos está na coleção de sistema.</span><span class="sxs-lookup"><span data-stu-id="dc956-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="dc956-205">Se não estiver na coleção de sistema, podemos removê-lo da nossa.</span><span class="sxs-lookup"><span data-stu-id="dc956-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="dc956-206">Nosso manipulador de eventos em AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="dc956-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="dc956-207">A implementação da remoção de malha no RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="dc956-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="dc956-208">Adquirir e usar buffers de dados de malha superficial</span><span class="sxs-lookup"><span data-stu-id="dc956-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="dc956-209">Como obter as informações de malha superficial foi tão fácil quanto efetuar pull de uma coleção de dados e processamento de atualizações a essa coleção.</span><span class="sxs-lookup"><span data-stu-id="dc956-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="dc956-210">Agora, podemos entrarei em detalhes sobre como você pode usar os dados.</span><span class="sxs-lookup"><span data-stu-id="dc956-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="dc956-211">Em nosso exemplo de código, optamos por usar as malhas de superfície para renderização.</span><span class="sxs-lookup"><span data-stu-id="dc956-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="dc956-212">Isso é um cenário comum para hologramas occluding por trás de superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="dc956-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="dc956-213">Você também pode renderizar as malhas, ou renderizar processadas versões deles, para mostrar ao usuário quais áreas do sala são verificados antes de começar a fornecer a funcionalidade do aplicativo ou jogo.</span><span class="sxs-lookup"><span data-stu-id="dc956-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="dc956-214">O exemplo de código inicia o processo quando ele recebe atualizações de malha superficial do manipulador de eventos que foram descritos na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="dc956-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="dc956-215">A linha importante do código nessa função é chamada para atualizar a superfície *malha*: nesse momento podemos já processadas as informações de malha, e estamos prestes a se tornar os dados de índice e vértice para uso como podemos ver melhor.</span><span class="sxs-lookup"><span data-stu-id="dc956-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="dc956-216">From RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="dc956-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="dc956-217">Nosso código de exemplo é projetado para que uma classe de dados **SurfaceMesh**, lida com dados de malha de processamento e renderização.</span><span class="sxs-lookup"><span data-stu-id="dc956-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="dc956-218">Esses malhas são o que o **RealtimeSurfaceMeshRenderer** realmente mantém um mapa de.</span><span class="sxs-lookup"><span data-stu-id="dc956-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="dc956-219">Cada um deles tem uma referência para o SpatialSurfaceMesh ele veio e usá-lo sempre que é necessário para acessar os buffers de vértice ou o índice de malha, ou obter uma transformação para a malha.</span><span class="sxs-lookup"><span data-stu-id="dc956-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="dc956-220">Por enquanto, vamos sinalizador a malha como precisando de uma atualização.</span><span class="sxs-lookup"><span data-stu-id="dc956-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="dc956-221">De SurfaceMesh.cpp:</span><span class="sxs-lookup"><span data-stu-id="dc956-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="dc956-222">Próxima vez em que a malha é solicitada a desenhar a próprio, ele verificará o sinalizador pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="dc956-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="dc956-223">Se uma atualização for necessária, os buffers de índice e vértice serão atualizados na GPU.</span><span class="sxs-lookup"><span data-stu-id="dc956-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="dc956-224">Primeiro, vamos adquirir os buffers de dados brutos:</span><span class="sxs-lookup"><span data-stu-id="dc956-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="dc956-225">Em seguida, podemos criar buffers de dispositivo Direct3D com os dados de malha fornecidos pelo HoloLens:</span><span class="sxs-lookup"><span data-stu-id="dc956-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="dc956-226">**OBSERVAÇÃO:** Para a função de auxiliar CreateDirectXBuffer usada no trecho anterior, consulte o exemplo de código de mapeamento de superfície: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span><span class="sxs-lookup"><span data-stu-id="dc956-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="dc956-227">Agora, a criação de recursos do dispositivo for concluída e a malha é considerada para ser carregado e pronto para atualização e renderizar.</span><span class="sxs-lookup"><span data-stu-id="dc956-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="dc956-228">Atualizar e renderizar a superfície de malhas</span><span class="sxs-lookup"><span data-stu-id="dc956-228">Update and render surface meshes</span></span>

<span data-ttu-id="dc956-229">Nossa classe SurfaceMesh tem uma função especializada de atualização.</span><span class="sxs-lookup"><span data-stu-id="dc956-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="dc956-230">Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tem sua própria transformação e, em nosso exemplo usa o sistema de coordenadas atual para o nosso **SpatialStationaryReferenceFrame** para adquirir a transformação.</span><span class="sxs-lookup"><span data-stu-id="dc956-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="dc956-231">Em seguida, ele atualiza o buffer de constantes de modelo na GPU.</span><span class="sxs-lookup"><span data-stu-id="dc956-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="dc956-232">Quando chegou a hora para renderizar a superfície de malhas, podemos fazer algum trabalho de preparação antes de renderizar a coleção.</span><span class="sxs-lookup"><span data-stu-id="dc956-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="dc956-233">Configuramos o pipeline sombreador para a configuração atual de renderização e configuramos o estágio do assembler de entrada.</span><span class="sxs-lookup"><span data-stu-id="dc956-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="dc956-234">Observe que a classe do auxiliar de câmera holographic **CameraResources.cpp** já tiver configurado o buffer de constantes de projeção de exibição/agora.</span><span class="sxs-lookup"><span data-stu-id="dc956-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="dc956-235">Partir **RealtimeSurfaceMeshRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="dc956-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="dc956-236">Depois que isso for feito, podemos loop em nosso malhas e informar a cada um para desenhar a mesmo.</span><span class="sxs-lookup"><span data-stu-id="dc956-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="dc956-237">**OBSERVAÇÃO:** Esse código de exemplo não é otimizado para usar qualquer tipo de frustum traseira, mas você deve incluir esse recurso em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc956-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="dc956-238">As malhas individuais são responsáveis por configurar o buffer de índice e vértice, o stride e o buffer de constantes de transformação do modelo.</span><span class="sxs-lookup"><span data-stu-id="dc956-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="dc956-239">Assim como acontece com o cubo giratório no modelo de aplicativo do Windows Holographic, podemos renderizar buffers estereoscópica usando a criação de instância.</span><span class="sxs-lookup"><span data-stu-id="dc956-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="dc956-240">Partir **SurfaceMesh::Draw**:</span><span class="sxs-lookup"><span data-stu-id="dc956-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="dc956-241">Opções de renderização com o mapeamento de superfície</span><span class="sxs-lookup"><span data-stu-id="dc956-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="dc956-242">O exemplo de código de mapeamento de superfície oferece para renderização somente oclusão dos dados de malha superficial e na tela de processamento de dados de malha superficial de código.</span><span class="sxs-lookup"><span data-stu-id="dc956-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="dc956-243">Qual caminho você escolher - ou ambos - dependem do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc956-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="dc956-244">Vamos examinar ambas as configurações neste documento.</span><span class="sxs-lookup"><span data-stu-id="dc956-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="dc956-245">**Buffers de oclusão de renderização para efeito holográfico**</span><span class="sxs-lookup"><span data-stu-id="dc956-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="dc956-246">Começar limpando a exibição de destino de renderização para a câmera virtual atual.</span><span class="sxs-lookup"><span data-stu-id="dc956-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="dc956-247">De AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="dc956-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="dc956-248">Essa é uma passagem de "pré-processamento".</span><span class="sxs-lookup"><span data-stu-id="dc956-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="dc956-249">Aqui, podemos criar um buffer de oclusão pedindo que o renderizador de malha para renderizar apenas profundidade.</span><span class="sxs-lookup"><span data-stu-id="dc956-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="dc956-250">Nessa configuração, não anexamos um modo de exibição de destino de renderização e o renderizador de malha define o estágio de sombreador de pixel para **nullptr** , de modo que a GPU não se preocupa em Desenhar pixels.</span><span class="sxs-lookup"><span data-stu-id="dc956-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="dc956-251">A geometria será rasterizado no buffer de profundidade e o pipeline gráfico irá parar por aqui.</span><span class="sxs-lookup"><span data-stu-id="dc956-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="dc956-252">É possível desenhar hologramas com um teste de profundidade extra contra o buffer de oclusão de superfície de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="dc956-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="dc956-253">No exemplo de código, podemos renderizar pixels no cubo de uma cor diferente se eles estiverem protegidos por uma superfície.</span><span class="sxs-lookup"><span data-stu-id="dc956-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="dc956-254">De AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="dc956-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="dc956-255">Com base no código do SpecialEffectPixelShader.hlsl:</span><span class="sxs-lookup"><span data-stu-id="dc956-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="dc956-256">**Observação:** Para nosso **GatherDepthLess** rotina, consulte o exemplo de código de mapeamento de superfície: SpecialEffectPixelShader.hlsl.</span><span class="sxs-lookup"><span data-stu-id="dc956-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="dc956-257">**Dados de malha superficial de renderização para a exibição**</span><span class="sxs-lookup"><span data-stu-id="dc956-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="dc956-258">Também podemos tirar as malhas de superfície para os buffers de exibição estéreo.</span><span class="sxs-lookup"><span data-stu-id="dc956-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="dc956-259">Optamos por desenhar faces completos com iluminação, mas fique à vontade para desenhar wireframe, processar as malhas antes da renderização, aplicar um mapa de textura e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="dc956-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="dc956-260">Aqui, nosso exemplo de código informa o renderizador de malha para desenhar a coleção.</span><span class="sxs-lookup"><span data-stu-id="dc956-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="dc956-261">Neste momento, não especifique uma passagem somente de profundidade, para que ele irá anexar um sombreador de pixel e concluir o pipeline de renderização usando os destinos que especificamos para a câmera virtual atual.</span><span class="sxs-lookup"><span data-stu-id="dc956-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dc956-262">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc956-262">See also</span></span>
* [<span data-ttu-id="dc956-263">Criando um projeto holográfico do DirectX</span><span class="sxs-lookup"><span data-stu-id="dc956-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="dc956-264">Windows.Perception.Spatial API</span><span class="sxs-lookup"><span data-stu-id="dc956-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)

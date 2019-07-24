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
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="a6e75-105">Mapeamento espacial no DirectX</span><span class="sxs-lookup"><span data-stu-id="a6e75-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="a6e75-106">Este tópico descreve como implementar o [mapeamento espacial](spatial-mapping.md) em seu aplicativo DirectX.</span><span class="sxs-lookup"><span data-stu-id="a6e75-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="a6e75-107">Isso inclui uma explicação detalhada do aplicativo de exemplo de mapeamento espacial incluído no SDK do Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="a6e75-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="a6e75-108">Este tópico usa código do exemplo de código [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP.</span><span class="sxs-lookup"><span data-stu-id="a6e75-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="a6e75-109">Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="a6e75-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a6e75-110">Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="a6e75-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="a6e75-111">Visão geral de desenvolvimento do DirectX</span><span class="sxs-lookup"><span data-stu-id="a6e75-111">DirectX development overview</span></span>

<span data-ttu-id="a6e75-112">O desenvolvimento de aplicativos nativos para o mapeamento espacial usa as APIs no namespace [Windows. percepção. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) .</span><span class="sxs-lookup"><span data-stu-id="a6e75-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="a6e75-113">Essas APIs fornecem controle total da funcionalidade de mapeamento espacial, de uma maneira diretamente análoga às APIs de mapeamento espacial expostas pelo [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="a6e75-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="a6e75-114">APIs de percepção</span><span class="sxs-lookup"><span data-stu-id="a6e75-114">Perception APIs</span></span>

<span data-ttu-id="a6e75-115">Os tipos primários fornecidos para o desenvolvimento de mapeamentos espaciais são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="a6e75-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="a6e75-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornece informações sobre superfícies em regiões especificadas pelo aplicativo de espaço próximo ao usuário, na forma de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="a6e75-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descreve uma superfície espacial existentes única, incluindo uma ID exclusiva, o volume delimitador e a hora da última alteração.</span><span class="sxs-lookup"><span data-stu-id="a6e75-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="a6e75-118">Ele fornecerá um SpatialSurfaceMesh de forma assíncrona após a solicitação.</span><span class="sxs-lookup"><span data-stu-id="a6e75-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="a6e75-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contém parâmetros usados para personalizar os objetos SpatialSurfaceMesh solicitados de SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="a6e75-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa os dados de malha de uma única superfície espacial.</span><span class="sxs-lookup"><span data-stu-id="a6e75-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="a6e75-121">Os dados para posições de vértice, normais de vértice e índices de triângulo estão contidos em objetos member SpatialSurfaceMeshBuffer.</span><span class="sxs-lookup"><span data-stu-id="a6e75-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="a6e75-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) encapsula um único tipo de dados de malha.</span><span class="sxs-lookup"><span data-stu-id="a6e75-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="a6e75-123">Ao desenvolver um aplicativo usando essas APIs, o fluxo de programa básico terá esta aparência (conforme demonstrado no aplicativo de exemplo descrito abaixo):</span><span class="sxs-lookup"><span data-stu-id="a6e75-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="a6e75-124">**Configurar seu SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="a6e75-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="a6e75-125">Chame [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)para garantir que o usuário tenha concedido permissão para que seu aplicativo use os recursos de mapeamento espacial do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="a6e75-126">Crie uma instância de um objeto SpatialSurfaceObserver.</span><span class="sxs-lookup"><span data-stu-id="a6e75-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="a6e75-127">Chame [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar as regiões de espaço nas quais você deseja obter informações sobre superfícies espaciais.</span><span class="sxs-lookup"><span data-stu-id="a6e75-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="a6e75-128">Você pode modificar essas regiões no futuro simplesmente chamando essa função novamente.</span><span class="sxs-lookup"><span data-stu-id="a6e75-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="a6e75-129">Cada região é especificada usando um [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="a6e75-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="a6e75-130">Registre-se no evento [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , que será acionado sempre que novas informações estiverem disponíveis sobre as superfícies espaciais nas regiões de espaço que você especificou.</span><span class="sxs-lookup"><span data-stu-id="a6e75-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="a6e75-131">**Processar eventos ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="a6e75-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="a6e75-132">Em seu manipulador de eventos, chame [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para receber um mapa de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="a6e75-133">Usando esse mapa, você pode atualizar os registros dos quais as superfícies espaciais [existem no ambiente do usuário](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="a6e75-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="a6e75-134">Para cada objeto SpatialSurfaceInfo, você pode consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) para determinar as extensões espaciais da superfície, expressas em um [sistema de coordenadas espaciais](coordinate-systems.md) de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="a6e75-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="a6e75-135">Se você decidir solicitar malha para uma superfície espacial, chame [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="a6e75-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="a6e75-136">Você pode fornecer opções especificando a densidade desejada de triângulos e o formato dos dados de malha retornados.</span><span class="sxs-lookup"><span data-stu-id="a6e75-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="a6e75-137">**Receber e processar malha**</span><span class="sxs-lookup"><span data-stu-id="a6e75-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="a6e75-138">Cada chamada para TryComputeLatestMeshAsync irá aysnchronously retornar um objeto SpatialSurfaceMesh.</span><span class="sxs-lookup"><span data-stu-id="a6e75-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="a6e75-139">Desse objeto, você pode acessar os objetos SpatialSurfaceMeshBuffer contidos para acessar os índices de triângulo, as posições de vértice e (se solicitado) vértices normais da malha.</span><span class="sxs-lookup"><span data-stu-id="a6e75-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="a6e75-140">Esses dados estarão em um formato diretamente compatível com as [APIs do Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usadas para renderizar malhas.</span><span class="sxs-lookup"><span data-stu-id="a6e75-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="a6e75-141">A partir daqui, o aplicativo pode opcionalmente executar a análise ou o [processamento](spatial-mapping.md#mesh-processing) dos dados de malha e usá-lo para [renderização](spatial-mapping.md#rendering) e [raycasting física e colisão](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="a6e75-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="a6e75-142">Um detalhe importante a ser observado é que você deve aplicar uma escala às posições de vértice de malha (por exemplo, no sombreador de vértice usado para renderizar as malhas), para convertê-las das unidades de inteiros otimizadas nas quais elas são armazenadas no buffer, em metros.</span><span class="sxs-lookup"><span data-stu-id="a6e75-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="a6e75-143">Você pode recuperar essa escala chamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="a6e75-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="a6e75-144">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="a6e75-144">Troubleshooting</span></span>
* <span data-ttu-id="a6e75-145">Não se esqueça de dimensionar as posições de vértice de malha em seu sombreador de vértice, usando a escala retornada por [SpatialSurfaceMesh. VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="a6e75-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="a6e75-146">Instruções de exemplo de código de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="a6e75-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="a6e75-147">O exemplo de código de [mapeamento espacial Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) inclui o código que você pode usar para começar a carregar malhas de superfície em seu aplicativo, incluindo a infraestrutura para gerenciar e renderizar malhas de superfície.</span><span class="sxs-lookup"><span data-stu-id="a6e75-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="a6e75-148">Agora, vamos examinar como adicionar o recurso de mapeamento de superfície ao seu aplicativo DirectX.</span><span class="sxs-lookup"><span data-stu-id="a6e75-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="a6e75-149">Você pode adicionar esse código ao seu projeto de [modelo de aplicativo Holographic do Windows](creating-a-holographic-directx-project.md) ou pode acompanhar navegando pelo exemplo de código mencionado acima.</span><span class="sxs-lookup"><span data-stu-id="a6e75-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="a6e75-150">Este exemplo de código é baseado no modelo de aplicativo Holographic do Windows.</span><span class="sxs-lookup"><span data-stu-id="a6e75-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="a6e75-151">Configurar seu aplicativo para usar o recurso spatialPerception</span><span class="sxs-lookup"><span data-stu-id="a6e75-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="a6e75-152">Seu aplicativo deve ser capaz de usar o recurso de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="a6e75-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="a6e75-153">Isso é necessário porque a malha espacial é uma representação do ambiente do usuário, que pode ser considerado dados privados.</span><span class="sxs-lookup"><span data-stu-id="a6e75-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="a6e75-154">Declare esse recurso no arquivo Package. appxmanifest para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="a6e75-155">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6e75-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="a6e75-156">A funcionalidade vem do namespace **uap2** .</span><span class="sxs-lookup"><span data-stu-id="a6e75-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="a6e75-157">Para obter acesso a esse namespace em seu manifesto, inclua-o como um atributo *xlmns* no &lt;elemento > do pacote.</span><span class="sxs-lookup"><span data-stu-id="a6e75-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="a6e75-158">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6e75-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="a6e75-159">Verificar o suporte a recursos de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="a6e75-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="a6e75-160">O Windows Mixed Reality dá suporte a uma ampla variedade de dispositivos, incluindo dispositivos que não dão suporte ao mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="a6e75-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="a6e75-161">Se seu aplicativo pode usar o mapeamento espacial ou deve usar o mapeamento espacial, para fornecer funcionalidade, ele deve verificar se há suporte para o mapeamento espacial antes de tentar usá-lo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="a6e75-162">Por exemplo, se o mapeamento espacial for exigido pelo seu aplicativo de realidade misturada, ele deverá exibir uma mensagem para esse efeito se um usuário tentar executá-lo em um dispositivo sem o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="a6e75-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="a6e75-163">Ou, seu aplicativo pode ser capaz de renderizar seu próprio ambiente virtual no lugar do ambiente do usuário, fornecendo uma experiência semelhante ao que aconteceria se o mapeamento espacial estivesse disponível.</span><span class="sxs-lookup"><span data-stu-id="a6e75-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="a6e75-164">Em qualquer evento, essa API permite que seu aplicativo fique atento quando não obter dados de mapeamento espacial e responder da maneira apropriada.</span><span class="sxs-lookup"><span data-stu-id="a6e75-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="a6e75-165">Para verificar o dispositivo atual quanto ao suporte de mapeamento espacial, primeiro verifique se o contrato UWP está no nível 4 ou superior e, em seguida, chame SpatialSurfaceObserver:: IsSupported ().</span><span class="sxs-lookup"><span data-stu-id="a6e75-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="a6e75-166">Veja como fazer isso no contexto do exemplo de código de [mapeamento espacial do Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .</span><span class="sxs-lookup"><span data-stu-id="a6e75-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="a6e75-167">O suporte é verificado logo antes de solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="a6e75-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="a6e75-168">A API SpatialSurfaceObserver:: IsSupported () está disponível a partir da versão 15063 do SDK.</span><span class="sxs-lookup"><span data-stu-id="a6e75-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="a6e75-169">Se necessário, redirecione seu projeto para a versão da plataforma 15063 antes de usar essa API.</span><span class="sxs-lookup"><span data-stu-id="a6e75-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="a6e75-170">Observe que, quando o contrato UWP é menor que o nível 4, o aplicativo deve continuar como se o dispositivo fosse capaz de fazer o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="a6e75-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="a6e75-171">Solicitar acesso aos dados de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="a6e75-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="a6e75-172">Seu aplicativo precisa solicitar permissão para acessar dados de mapeamento espacial antes de tentar criar qualquer observador de superfície.</span><span class="sxs-lookup"><span data-stu-id="a6e75-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="a6e75-173">Veja um exemplo com base no exemplo de código de mapeamento de superfície, com mais detalhes fornecidos mais adiante nesta página:</span><span class="sxs-lookup"><span data-stu-id="a6e75-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="a6e75-174">Criar um observador de superfície</span><span class="sxs-lookup"><span data-stu-id="a6e75-174">Create a surface observer</span></span>

<span data-ttu-id="a6e75-175">O namespace **Windows::P erception:: Spatial:: superfícies** inclui a classe [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , que observa um ou mais volumes que você especifica em um [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="a6e75-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="a6e75-176">Use uma instância de [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) para acessar dados de malha de superfície em tempo real.</span><span class="sxs-lookup"><span data-stu-id="a6e75-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="a6e75-177">De **AppMain. h**:</span><span class="sxs-lookup"><span data-stu-id="a6e75-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="a6e75-178">Conforme observado na seção anterior, você deve solicitar acesso aos dados de mapeamento espacial antes que seu aplicativo possa usá-lo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="a6e75-179">Esse acesso é concedido automaticamente no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a6e75-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="a6e75-180">Em seguida, você precisa configurar o observador de superfície para observar um volume delimitador específico.</span><span class="sxs-lookup"><span data-stu-id="a6e75-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="a6e75-181">Aqui, observamos uma caixa que é 20x20x5 metros, centralizada na origem do sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="a6e75-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="a6e75-182">Observe que você pode definir vários volumes delimitadores em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a6e75-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="a6e75-183">*Este é o pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="a6e75-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="a6e75-184">Também é possível usar outras formas delimitadoras, como uma exibição frustum, ou uma caixa delimitadora que não esteja alinhada ao eixo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="a6e75-185">*Este é o pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="a6e75-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="a6e75-186">Se seu aplicativo precisar fazer algo diferente quando os dados de mapeamento de superfície não estiverem disponíveis, você poderá escrever código para responder ao caso em que o [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) não é **permitido** ; por exemplo, ele não será permitido em PCs com imersão dispositivos anexados porque esses dispositivos não têm hardware para mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="a6e75-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="a6e75-187">Para esses dispositivos, você deve confiar no estágio espacial para obter informações sobre a configuração do ambiente e do dispositivo do usuário.</span><span class="sxs-lookup"><span data-stu-id="a6e75-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="a6e75-188">Inicializar e atualizar a coleção de malha da superfície</span><span class="sxs-lookup"><span data-stu-id="a6e75-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="a6e75-189">Se o observador de superfície foi criado com êxito, podemos continuar a inicializar nossa coleção de malha de superfície.</span><span class="sxs-lookup"><span data-stu-id="a6e75-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="a6e75-190">Aqui, usamos a API do modelo de pull para obter o conjunto atual de superfícies observadas imediatamente:</span><span class="sxs-lookup"><span data-stu-id="a6e75-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="a6e75-191">Há também um modelo de push disponível para obter dados de malha de superfície.</span><span class="sxs-lookup"><span data-stu-id="a6e75-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="a6e75-192">Você tem a liberdade de criar seu aplicativo para usar apenas o modelo de pull se escolher, caso em que você vai sondar os dados a cada hora, com frequência, uma vez por quadro ou durante um período de tempo específico, como durante a configuração do jogo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="a6e75-193">Nesse caso, o código acima é o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="a6e75-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="a6e75-194">Em nosso exemplo de código, optamos por demonstrar o uso de ambos os modelos para fins de pedagógicos.</span><span class="sxs-lookup"><span data-stu-id="a6e75-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="a6e75-195">Aqui, assinamos um evento para receber dados de malha de superfície atualizados sempre que o sistema reconhece uma alteração.</span><span class="sxs-lookup"><span data-stu-id="a6e75-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="a6e75-196">Nosso exemplo de código também é configurado para responder a esses eventos.</span><span class="sxs-lookup"><span data-stu-id="a6e75-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="a6e75-197">Vamos examinar como fazemos isso.</span><span class="sxs-lookup"><span data-stu-id="a6e75-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="a6e75-198">**OBSERVAÇÃO:** Essa pode não ser a maneira mais eficiente para seu aplicativo manipular dados de malha.</span><span class="sxs-lookup"><span data-stu-id="a6e75-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="a6e75-199">Esse código é escrito para fins de clareza e não é otimizado.</span><span class="sxs-lookup"><span data-stu-id="a6e75-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="a6e75-200">Os dados de malha de superfície são fornecidos em um mapa somente leitura que armazena objetos [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) usando [Platform:: GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de chave.</span><span class="sxs-lookup"><span data-stu-id="a6e75-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="a6e75-201">Para processar esses dados, examinamos primeiro os valores de chave que não estão em nossa coleção.</span><span class="sxs-lookup"><span data-stu-id="a6e75-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="a6e75-202">Os detalhes sobre como os dados são armazenados em nosso aplicativo de exemplo serão apresentados posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="a6e75-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="a6e75-203">Também precisamos remover as malhas de superfície que estão em nossa coleção de malha de superfície, mas que não estão mais na coleção do sistema.</span><span class="sxs-lookup"><span data-stu-id="a6e75-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="a6e75-204">Para fazer isso, precisamos fazer algo semelhante ao oposto do que acabamos de mostrar para adicionar e atualizar malhas; Fazemos um loop sobre a coleção do aplicativo e verificamos se o **GUID** que temos está na coleção System.</span><span class="sxs-lookup"><span data-stu-id="a6e75-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="a6e75-205">Se não estiver na coleção do sistema, remova-o da nossa.</span><span class="sxs-lookup"><span data-stu-id="a6e75-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="a6e75-206">Do nosso manipulador de eventos em AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="a6e75-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="a6e75-207">A implementação da remoção de malha no RealtimeSurfaceMeshRenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="a6e75-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="a6e75-208">Adquirir e usar buffers de dados de malha de superfície</span><span class="sxs-lookup"><span data-stu-id="a6e75-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="a6e75-209">Obter as informações de malha de superfície era tão fácil quanto extrair uma coleta de dados e processar atualizações para essa coleção.</span><span class="sxs-lookup"><span data-stu-id="a6e75-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="a6e75-210">Agora, entraremos em detalhes sobre como você pode usar os dados.</span><span class="sxs-lookup"><span data-stu-id="a6e75-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="a6e75-211">Em nosso exemplo de código, optamos por usar as malhas de superfície para renderização.</span><span class="sxs-lookup"><span data-stu-id="a6e75-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="a6e75-212">Esse é um cenário comum para os hologramas occluding por trás das superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="a6e75-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="a6e75-213">Você também pode renderizar as malhas ou renderizar as versões processadas delas para mostrar ao usuário quais áreas da sala são verificadas antes de começar a fornecer a funcionalidade do aplicativo ou do jogo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="a6e75-214">O exemplo de código inicia o processo quando recebe atualizações de malha de superfície do manipulador de eventos que descrevemos na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="a6e75-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="a6e75-215">A linha importante de código nessa função é a chamada para atualizar a *malha*de superfície: neste momento, já processamos as informações de malha e estamos prestes a obter os dados de vértice e de índice para uso, como vemos.</span><span class="sxs-lookup"><span data-stu-id="a6e75-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="a6e75-216">De RealtimeSurfaceMeshRenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="a6e75-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="a6e75-217">Nosso código de exemplo foi projetado para que uma classe de dados, **SurfaceMesh**, lide com processamento e renderização de dados de malha.</span><span class="sxs-lookup"><span data-stu-id="a6e75-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="a6e75-218">Essas malhas são o que o **RealtimeSurfaceMeshRenderer** realmente mantém um mapa.</span><span class="sxs-lookup"><span data-stu-id="a6e75-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="a6e75-219">Cada um tem uma referência para o SpatialSurfaceMesh de origem e nós o usamos sempre que precisamos acessar o vértice de malha ou buffers de índice, ou obter uma transformação para a malha.</span><span class="sxs-lookup"><span data-stu-id="a6e75-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="a6e75-220">Por enquanto, sinalizamos a malha como precisa de uma atualização.</span><span class="sxs-lookup"><span data-stu-id="a6e75-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="a6e75-221">De SurfaceMesh. cpp:</span><span class="sxs-lookup"><span data-stu-id="a6e75-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="a6e75-222">Na próxima vez que a malha for solicitada a desenhar, ela verificará o sinalizador primeiro.</span><span class="sxs-lookup"><span data-stu-id="a6e75-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="a6e75-223">Se uma atualização for necessária, os buffers de vértice e de índice serão atualizados na GPU.</span><span class="sxs-lookup"><span data-stu-id="a6e75-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="a6e75-224">Primeiro, adquirimos os buffers de dados brutos:</span><span class="sxs-lookup"><span data-stu-id="a6e75-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="a6e75-225">Em seguida, criamos buffers de dispositivo Direct3D com os dados de malha fornecidos pelo HoloLens:</span><span class="sxs-lookup"><span data-stu-id="a6e75-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="a6e75-226">**OBSERVAÇÃO:** Para a função auxiliar CreateDirectXBuffer usada no trecho anterior, consulte o exemplo de código de mapeamento de superfície: SurfaceMesh. cpp, GetDataFromIBuffer. h.</span><span class="sxs-lookup"><span data-stu-id="a6e75-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="a6e75-227">Agora a criação do recurso do dispositivo está concluída e a malha é considerada como carregada e pronta para atualização e renderização.</span><span class="sxs-lookup"><span data-stu-id="a6e75-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="a6e75-228">Atualizar e renderizar malhas de superfície</span><span class="sxs-lookup"><span data-stu-id="a6e75-228">Update and render surface meshes</span></span>

<span data-ttu-id="a6e75-229">Nossa classe SurfaceMesh tem uma função de atualização especializada.</span><span class="sxs-lookup"><span data-stu-id="a6e75-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="a6e75-230">Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tem sua própria transformação, e nosso exemplo usa o sistema de coordenadas atual para nosso **SpatialStationaryReferenceFrame** para adquirir a transformação.</span><span class="sxs-lookup"><span data-stu-id="a6e75-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="a6e75-231">Em seguida, ele atualiza o buffer de constante do modelo na GPU.</span><span class="sxs-lookup"><span data-stu-id="a6e75-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="a6e75-232">Quando é hora de renderizar malhas de superfície, fazemos um trabalho de preparação antes de renderizar a coleção.</span><span class="sxs-lookup"><span data-stu-id="a6e75-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="a6e75-233">Configuramos o pipeline do sombreador para a configuração de renderização atual e configuramos o estágio do assembler de entrada.</span><span class="sxs-lookup"><span data-stu-id="a6e75-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="a6e75-234">Observe que a classe auxiliar da câmera Holographic **CameraResources. cpp** já configurou o buffer constante de exibição/projeção agora.</span><span class="sxs-lookup"><span data-stu-id="a6e75-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="a6e75-235">De **RealtimeSurfaceMeshRenderer:: render**:</span><span class="sxs-lookup"><span data-stu-id="a6e75-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="a6e75-236">Quando isso for feito, vamos fazer um loop em nossas malhas e dizer a cada uma delas para se desenhar.</span><span class="sxs-lookup"><span data-stu-id="a6e75-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="a6e75-237">**OBSERVAÇÃO:** Este código de exemplo não é otimizado para usar qualquer tipo de remoção de frustum, mas você deve incluir esse recurso em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="a6e75-238">As malhas individuais são responsáveis pela configuração do vértice e do buffer de índice, Stride e buffer constante de transformação de modelo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="a6e75-239">Assim como no cubo de rotação no modelo de aplicativo Holographic do Windows, renderizamos para buffers estereoscópico usando instanciação.</span><span class="sxs-lookup"><span data-stu-id="a6e75-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="a6e75-240">De **SurfaceMesh::D bruto**:</span><span class="sxs-lookup"><span data-stu-id="a6e75-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="a6e75-241">Opções de renderização com mapeamento de superfície</span><span class="sxs-lookup"><span data-stu-id="a6e75-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="a6e75-242">O exemplo de código de mapeamento de superfície oferece código para renderização oclusão de dados de malha de superfície e para renderização na tela de dados de malha de superfície.</span><span class="sxs-lookup"><span data-stu-id="a6e75-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="a6e75-243">Qual caminho você escolhe-ou ambos-depende do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="a6e75-244">Vamos percorrer as duas configurações deste documento.</span><span class="sxs-lookup"><span data-stu-id="a6e75-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="a6e75-245">**Renderizando buffers oclusão para efeito Holographic**</span><span class="sxs-lookup"><span data-stu-id="a6e75-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="a6e75-246">Comece limpando a exibição de destino de renderização para a câmera virtual atual.</span><span class="sxs-lookup"><span data-stu-id="a6e75-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="a6e75-247">De AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="a6e75-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="a6e75-248">Essa é uma passagem de "pré-processamento".</span><span class="sxs-lookup"><span data-stu-id="a6e75-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="a6e75-249">Aqui, criamos um buffer oclusão solicitando que o processador de malha processe apenas a profundidade.</span><span class="sxs-lookup"><span data-stu-id="a6e75-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="a6e75-250">Nessa configuração, não anexamos uma exibição de destino de renderização e o processador de malha define o estágio do sombreador de pixel como **nullptr** para que a GPU não se preocupe em desenhar pixels.</span><span class="sxs-lookup"><span data-stu-id="a6e75-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="a6e75-251">A geometria será rasterizada para o buffer de profundidade e o pipeline de gráficos será interrompido.</span><span class="sxs-lookup"><span data-stu-id="a6e75-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="a6e75-252">Podemos desenhar hologramas com um teste de profundidade extra em relação ao buffer oclusão de mapeamento de superfície.</span><span class="sxs-lookup"><span data-stu-id="a6e75-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="a6e75-253">Neste exemplo de código, renderizaremos pixels no cubo em uma cor diferente se estiverem atrás de uma superfície.</span><span class="sxs-lookup"><span data-stu-id="a6e75-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="a6e75-254">De AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="a6e75-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="a6e75-255">Com base no código de SpecialEffectPixelShader. HLSL:</span><span class="sxs-lookup"><span data-stu-id="a6e75-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="a6e75-256">**Observação:** Para nossa rotina **GatherDepthLess** , consulte o exemplo de código de mapeamento de superfície: SpecialEffectPixelShader. HLSL.</span><span class="sxs-lookup"><span data-stu-id="a6e75-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="a6e75-257">**Renderizando dados de malha da superfície para a exibição**</span><span class="sxs-lookup"><span data-stu-id="a6e75-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="a6e75-258">Também podemos simplesmente desenhar as malhas de superfície para os buffers de vídeo estéreo.</span><span class="sxs-lookup"><span data-stu-id="a6e75-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="a6e75-259">Optamos por desenhar faces completas com iluminação, mas você está livre para desenhar wireframe, processar malhas antes de renderizar, aplicar um mapa de textura e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a6e75-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="a6e75-260">Aqui, nosso exemplo de código diz ao renderizador de malha para desenhar a coleção.</span><span class="sxs-lookup"><span data-stu-id="a6e75-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="a6e75-261">Desta vez, não especificamos uma passagem somente de profundidade, portanto, ele anexará um sombreador de pixel e concluirá o pipeline de renderização usando os destinos que especificamos para a câmera virtual atual.</span><span class="sxs-lookup"><span data-stu-id="a6e75-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a6e75-262">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6e75-262">See also</span></span>
* [<span data-ttu-id="a6e75-263">Como criar um projeto holográfico do DirectX</span><span class="sxs-lookup"><span data-stu-id="a6e75-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="a6e75-264">API Windows. percepção. espacial</span><span class="sxs-lookup"><span data-stu-id="a6e75-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)

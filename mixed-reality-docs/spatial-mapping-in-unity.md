---
title: Mapeamento espacial no Unity
description: Renderizando e colide com a geometria do mundo real em relação a você no Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapeamento espacial, renderizador, colisor, malha, verificação, componente
ms.openlocfilehash: 452e629a877df585ffbc0a6466ffeb2588b66ecf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438038"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="ba28c-104">Mapeamento espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="ba28c-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="ba28c-105">Este tópico descreve como usar o [mapeamento espacial](spatial-mapping.md) em seu projeto do Unity, recuperando as malhas de triângulos que representam as superfícies do mundo em um dispositivo HoloLens, para posicionamento, oclusão, análise de sala e muito mais.</span><span class="sxs-lookup"><span data-stu-id="ba28c-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="ba28c-106">O Unity inclui suporte completo para o mapeamento espacial, que é exposto aos desenvolvedores das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="ba28c-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="ba28c-107">Componentes de mapeamento espacial disponíveis no MixedRealityToolkit, que fornecem um caminho conveniente e rápido para introdução ao mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="ba28c-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="ba28c-108">APIs de mapeamento espacial de nível inferior, que fornecem controle total e permitem uma personalização mais sofisticada específica do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ba28c-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="ba28c-109">Para usar o mapeamento espacial em seu aplicativo, o recurso spatialPerception precisa ser definido em seu AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="ba28c-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="ba28c-110">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="ba28c-110">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ba28c-111"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="ba28c-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="ba28c-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba28c-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="ba28c-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ba28c-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="ba28c-114"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="ba28c-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ba28c-115">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="ba28c-115">Spatial mapping</span></span></td>
        <td><span data-ttu-id="ba28c-116">✔️</span><span class="sxs-lookup"><span data-stu-id="ba28c-116">✔️</span></span></td>
        <td><span data-ttu-id="ba28c-117">✔️</span><span class="sxs-lookup"><span data-stu-id="ba28c-117">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="ba28c-118">Configurando o recurso SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="ba28c-118">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="ba28c-119">Para que um aplicativo consuma dados de mapeamento espacial, o recurso SpatialPerception deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="ba28c-119">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="ba28c-120">Como habilitar o recurso SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="ba28c-120">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="ba28c-121">No editor do Unity, abra o painel **"configurações do Player"** (Editar > configurações do projeto > Player)</span><span class="sxs-lookup"><span data-stu-id="ba28c-121">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="ba28c-122">Clique na guia **"Windows Store"**</span><span class="sxs-lookup"><span data-stu-id="ba28c-122">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="ba28c-123">Expanda **"configurações de publicação"** e verifique o recurso **"SpatialPerception"** na lista **"recursos"**</span><span class="sxs-lookup"><span data-stu-id="ba28c-123">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="ba28c-124">Observe que, se você já tiver exportado seu projeto do Unity para uma solução do Visual Studio, será necessário exportar para uma nova pasta ou [definir manualmente esse recurso no AppxManifest no Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="ba28c-124">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="ba28c-125">O mapeamento espacial também requer um MaxVersionTested de pelo menos 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="ba28c-125">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="ba28c-126">No Visual Studio, clique com o botão direito do mouse em **Package. appxmanifest** na Gerenciador de soluções e selecione **Exibir código**</span><span class="sxs-lookup"><span data-stu-id="ba28c-126">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="ba28c-127">Localize a linha especificando **TargetDeviceFamily** e altere **MaxVersionTested = "10.0.10240.0"** para **MaxVersionTested = "10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="ba28c-127">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="ba28c-128">**Salve** o Package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="ba28c-128">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="ba28c-129">Introdução aos componentes de mapeamento espacial interno do Unity</span><span class="sxs-lookup"><span data-stu-id="ba28c-129">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="ba28c-130">O Unity oferece 2 componentes para adicionar facilmente o mapeamento espacial ao seu aplicativo, o **renderizador de mapeamento espacial** e o **Colisor de mapeamento espacial**.</span><span class="sxs-lookup"><span data-stu-id="ba28c-130">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="ba28c-131">Renderizador de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="ba28c-131">Spatial Mapping Renderer</span></span>

<span data-ttu-id="ba28c-132">O renderizador de mapeamento espacial permite a visualização da malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="ba28c-132">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Renderizador de mapeamento espacial no Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="ba28c-134">Colisor de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="ba28c-134">Spatial Mapping Collider</span></span>

<span data-ttu-id="ba28c-135">O colisor de mapeamento espacial permite a interação de conteúdo Holographic (ou caractere), como a física, com a malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="ba28c-135">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Colisor de mapeamento espacial no Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="ba28c-137">Usando os componentes internos de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="ba28c-137">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="ba28c-138">Você pode adicionar ambos os componentes ao seu aplicativo se desejar visualizar e interagir com superfícies físicas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-138">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="ba28c-139">Para usar esses dois componentes em seu aplicativo do Unity:</span><span class="sxs-lookup"><span data-stu-id="ba28c-139">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="ba28c-140">Selecione um gameobject no centro da área na qual você gostaria de detectar malhas de superfície espacial.</span><span class="sxs-lookup"><span data-stu-id="ba28c-140">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="ba28c-141">Na janela Inspetor, **adicione o componente** > **XR** > **Colisor de mapeamento espacial** ou o **renderizador de mapeamento espacial**.</span><span class="sxs-lookup"><span data-stu-id="ba28c-141">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="ba28c-142">Você pode encontrar mais detalhes sobre como usar esses componentes no site de <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">documentação do Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="ba28c-142">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="ba28c-143">Indo além dos componentes internos de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="ba28c-143">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="ba28c-144">Esses componentes o tornam fácil de arrastar e soltar para começar a usar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="ba28c-144">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="ba28c-145"> Quando quiser ir além, há dois caminhos principais a serem explorados:</span><span class="sxs-lookup"><span data-stu-id="ba28c-145"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="ba28c-146">Para fazer seu próprio processamento de malha de nível inferior, consulte a seção abaixo sobre a API de script de mapeamento espacial de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="ba28c-146">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="ba28c-147">Para fazer uma análise de malha de nível superior, consulte a seção abaixo sobre a biblioteca SpatialUnderstanding em <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="ba28c-147">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="ba28c-148">Usando a API de mapeamento espacial do Unity de nível baixo</span><span class="sxs-lookup"><span data-stu-id="ba28c-148">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="ba28c-149">Se você precisar de mais controle do que obter do renderizador de mapeamento espacial e dos componentes do colisor de mapeamento espacial, poderá usar as APIs de script de mapeamento espacial de nível baixo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-149">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="ba28c-150">**Namespace:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="ba28c-150">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="ba28c-151">**Tipos**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *surfaceid*</span><span class="sxs-lookup"><span data-stu-id="ba28c-151">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="ba28c-152">Veja a seguir uma descrição do fluxo sugerido para um aplicativo que usa as APIs de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="ba28c-152">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="ba28c-153">Configurar SurfaceObserver (s)</span><span class="sxs-lookup"><span data-stu-id="ba28c-153">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="ba28c-154">Crie uma instância de um objeto SurfaceObserver para cada região de espaço definida pelo aplicativo para a qual você precisa de dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="ba28c-154">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="ba28c-155">Especifique a região de espaço para a qual cada objeto SurfaceObserver fornecerá dados chamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox ou SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="ba28c-155">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="ba28c-156">Você pode redefinir a região do espaço no futuro simplesmente chamando um desses métodos novamente.</span><span class="sxs-lookup"><span data-stu-id="ba28c-156">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="ba28c-157">Ao chamar SurfaceObserver. Update (), você deve fornecer um manipulador para cada superfície espacial na região de espaço do SurfaceObserver para a qual o sistema de mapeamento espacial tem novas informações.</span><span class="sxs-lookup"><span data-stu-id="ba28c-157">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="ba28c-158">O manipulador recebe, para uma superfície espacial:</span><span class="sxs-lookup"><span data-stu-id="ba28c-158">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="ba28c-159">Lidando com alterações de superfície</span><span class="sxs-lookup"><span data-stu-id="ba28c-159">Handling Surface Changes</span></span>

<span data-ttu-id="ba28c-160">Há vários casos principais a serem manipulados.</span><span class="sxs-lookup"><span data-stu-id="ba28c-160">There are several main cases to handle.</span></span> <span data-ttu-id="ba28c-161">Adicionado & atualizado que pode usar o mesmo caminho de código e removido.</span><span class="sxs-lookup"><span data-stu-id="ba28c-161">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="ba28c-162">Nos casos adicionados & atualizados no exemplo, adicionamos ou obtemos o gameobject que representa essa malha do dicionário, criamos uma estrutura SurfaceData com os componentes necessários e, em seguida, chamamos RequestMeshDataAsync para preencher o gameobject com os dados de malha e posição na cena.</span><span class="sxs-lookup"><span data-stu-id="ba28c-162">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="ba28c-163">No caso removido, removemos o gameobject que representa a malha do dicionário e o destruimos.</span><span class="sxs-lookup"><span data-stu-id="ba28c-163">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="ba28c-164">Manipulando dados prontos</span><span class="sxs-lookup"><span data-stu-id="ba28c-164">Handling Data Ready</span></span>

<span data-ttu-id="ba28c-165">O manipulador OnDataReady recebe um objeto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="ba28c-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="ba28c-166">Os objetos WorldAnchor, MeshFilter e (opcionalmente) MeshCollider que ele contém refletem o estado mais recente da superfície espacial associada.</span><span class="sxs-lookup"><span data-stu-id="ba28c-166">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="ba28c-167">Opcionalmente, execute a análise e/ou o [processamento](spatial-mapping.md#mesh-processing) dos dados de malha acessando o membro de malha do objeto MeshFilter.</span><span class="sxs-lookup"><span data-stu-id="ba28c-167">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="ba28c-168">Renderize a superfície espacial com a malha mais recente e (opcionalmente) Use-a para colisões de física e raycasts.</span><span class="sxs-lookup"><span data-stu-id="ba28c-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="ba28c-169">É importante confirmar que o conteúdo de SurfaceData não é nulo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-169">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="ba28c-170">Iniciar processamento em atualizações</span><span class="sxs-lookup"><span data-stu-id="ba28c-170">Start processing on updates</span></span>

<span data-ttu-id="ba28c-171">SurfaceObserver. Update () deve ser chamado em um atraso, e não em todos os quadros.</span><span class="sxs-lookup"><span data-stu-id="ba28c-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="ba28c-172">Análise de malha de nível superior: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="ba28c-172">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="ba28c-173">O <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> é uma coleção de código de utilidade útil para desenvolvimento de Holographic com base nas APIs do Unity Holographic.</span><span class="sxs-lookup"><span data-stu-id="ba28c-173">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="ba28c-174">Compreensão espacial</span><span class="sxs-lookup"><span data-stu-id="ba28c-174">Spatial Understanding</span></span>

<span data-ttu-id="ba28c-175">Ao colocar os hologramas no mundo físico, geralmente é desejável ir além dos planos de malha e superfície do mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="ba28c-175">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="ba28c-176">Quando o posicionamento é feito de procedimento, um nível mais alto de compreensão ambiental é desejável.</span><span class="sxs-lookup"><span data-stu-id="ba28c-176">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="ba28c-177">Isso geralmente requer tomar decisões sobre o que é andar, teto e paredes.</span><span class="sxs-lookup"><span data-stu-id="ba28c-177">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="ba28c-178">Além disso, a capacidade de otimizar contra um conjunto de restrições de posicionamento para determinar os locais físicos mais desejáveis para objetos Holographic.</span><span class="sxs-lookup"><span data-stu-id="ba28c-178">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="ba28c-179">Durante o desenvolvimento de jovens conkers e fragmentos, Asobo estúdios enfrentou esse problema, desenvolvendo um resolvedor de sala para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="ba28c-179">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="ba28c-180">Cada um desses jogos tinha necessidades específicas de jogos, mas compartilhou a tecnologia de compreensão espacial principal.</span><span class="sxs-lookup"><span data-stu-id="ba28c-180">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="ba28c-181">A biblioteca HoloToolkit. SpatialUnderstanding encapsula essa tecnologia, permitindo que você encontre rapidamente espaços vazios nas paredes, coloque os objetos no teto, identifique-os com relação ao caractere a ser colocado e uma infinidade de outras consultas de compreensão espacial.</span><span class="sxs-lookup"><span data-stu-id="ba28c-181">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="ba28c-182">Todo o código-fonte está incluído, permitindo personalizá-lo às suas necessidades e compartilhar suas melhorias com a Comunidade.</span><span class="sxs-lookup"><span data-stu-id="ba28c-182">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="ba28c-183">O código do C++ resolvedor foi encapsulado em uma DLL UWP e exposto ao Unity com uma queda no pré-fabricado contido no MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="ba28c-183">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="ba28c-184">Noções básicas sobre módulos</span><span class="sxs-lookup"><span data-stu-id="ba28c-184">Understanding Modules</span></span>

<span data-ttu-id="ba28c-185">Há três interfaces primárias expostas pelo módulo: topologia para consultas espaciais e de superfície simples, forma de detecção de objeto e o resolvedor de posicionamento de objetos para o posicionamento baseado em restrição de conjuntos de objetos.</span><span class="sxs-lookup"><span data-stu-id="ba28c-185">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="ba28c-186">Cada um deles é descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-186">Each of these is described below.</span></span> <span data-ttu-id="ba28c-187">Além das três interfaces de módulo principais, uma interface de conversão Ray pode ser usada para recuperar tipos de superfície marcada e uma malha Watertight Playspace personalizada pode ser copiada.</span><span class="sxs-lookup"><span data-stu-id="ba28c-187">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="ba28c-188">Conversão de Ray</span><span class="sxs-lookup"><span data-stu-id="ba28c-188">Ray Casting</span></span>

<span data-ttu-id="ba28c-189">Depois que a sala tiver sido verificada e finalizada, os rótulos serão gerados internamente para superfícies como o piso, o teto e as paredes.</span><span class="sxs-lookup"><span data-stu-id="ba28c-189">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="ba28c-190">A função "PlayspaceRaycast" usa um raio e retorna se o raio colide com uma superfície conhecida e, nesse caso, informações sobre essa superfície na forma de um "RaycastResult".</span><span class="sxs-lookup"><span data-stu-id="ba28c-190">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="ba28c-191">Internamente, o Raycast é calculado em relação à representação computada 8cm cúbico VOXEL do Playspace.</span><span class="sxs-lookup"><span data-stu-id="ba28c-191">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="ba28c-192">Cada voxel contém um conjunto de elementos Surface com dados de topologia processados (também conhecido como surfels).</span><span class="sxs-lookup"><span data-stu-id="ba28c-192">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="ba28c-193">As surfels contidas na célula VOXEL interseccionada são comparadas e a melhor correspondência usada para pesquisar as informações de topologia.</span><span class="sxs-lookup"><span data-stu-id="ba28c-193">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="ba28c-194">Esses dados de topologia contêm o rótulo retornado na forma da enumeração "SurfaceTypes", bem como a área de superfície da superfície interseccionada.</span><span class="sxs-lookup"><span data-stu-id="ba28c-194">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="ba28c-195">No exemplo de Unity, o cursor converte um raio cada quadro.</span><span class="sxs-lookup"><span data-stu-id="ba28c-195">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="ba28c-196">Primeiro, em relação aos conflitantes da Unity.</span><span class="sxs-lookup"><span data-stu-id="ba28c-196">First, against Unity’s colliders.</span></span> <span data-ttu-id="ba28c-197">Em segundo lugar, em relação à representação Mundial do módulo de compreensão.</span><span class="sxs-lookup"><span data-stu-id="ba28c-197">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="ba28c-198">E, finalmente, os elementos da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="ba28c-198">And finally, again UI elements.</span></span> <span data-ttu-id="ba28c-199">Neste aplicativo, a interface do usuário obtém prioridade, em seguida o resultado da compreensão e, por fim, os coliders do Unity.</span><span class="sxs-lookup"><span data-stu-id="ba28c-199">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="ba28c-200">O Surfacetype é relatado como texto ao lado do cursor.</span><span class="sxs-lookup"><span data-stu-id="ba28c-200">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="ba28c-201">![tipo de superfície é rotulado ao lado do cursor](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba28c-201">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="ba28c-202">*O tipo de superfície é rotulado ao lado do cursor*</span><span class="sxs-lookup"><span data-stu-id="ba28c-202">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="ba28c-203">Consultas de topologia</span><span class="sxs-lookup"><span data-stu-id="ba28c-203">Topology Queries</span></span>

<span data-ttu-id="ba28c-204">Dentro da DLL, o Gerenciador de topologia lida com a rotulagem do ambiente.</span><span class="sxs-lookup"><span data-stu-id="ba28c-204">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="ba28c-205">Conforme mencionado acima, grande parte dos dados é armazenada no surfels, contido em um volume VOXEL.</span><span class="sxs-lookup"><span data-stu-id="ba28c-205">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="ba28c-206">Além disso, a estrutura "PlaySpaceInfos" é usada para armazenar informações sobre o Playspace, incluindo o alinhamento Mundial (mais detalhes sobre isso abaixo), piso e altura do teto.</span><span class="sxs-lookup"><span data-stu-id="ba28c-206">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="ba28c-207">A heurística é usada para determinar piso, teto e paredes.</span><span class="sxs-lookup"><span data-stu-id="ba28c-207">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="ba28c-208">Por exemplo, a maior e menor superfície horizontal com uma área de superfície maior que 1 m2 é considerada a base.</span><span class="sxs-lookup"><span data-stu-id="ba28c-208">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="ba28c-209">Observe que o caminho da câmera durante o processo de verificação também é usado nesse processo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-209">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="ba28c-210">Um subconjunto das consultas expostas pelo Gerenciador de topologia é exposto por meio da dll.</span><span class="sxs-lookup"><span data-stu-id="ba28c-210">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="ba28c-211">As consultas de topologia expostas são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="ba28c-211">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="ba28c-212">Cada uma das consultas tem um conjunto de parâmetros, específico ao tipo de consulta.</span><span class="sxs-lookup"><span data-stu-id="ba28c-212">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="ba28c-213">No exemplo a seguir, o usuário especifica a altura mínima & largura do volume desejado, a altura mínima de posicionamento acima do andar e a quantidade mínima de espaço livre na frente do volume.</span><span class="sxs-lookup"><span data-stu-id="ba28c-213">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="ba28c-214">Todas as medidas estão em metros.</span><span class="sxs-lookup"><span data-stu-id="ba28c-214">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="ba28c-215">Cada uma dessas consultas usa uma matriz pré-configurada de estruturas "TopologyResult".</span><span class="sxs-lookup"><span data-stu-id="ba28c-215">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="ba28c-216">O parâmetro "locationCount" especifica o comprimento da matriz passada.</span><span class="sxs-lookup"><span data-stu-id="ba28c-216">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="ba28c-217">O valor de retorno informa o número de locais retornados.</span><span class="sxs-lookup"><span data-stu-id="ba28c-217">The return value reports the number of returned locations.</span></span> <span data-ttu-id="ba28c-218">Esse número nunca é maior que o passado no parâmetro "locationCount".</span><span class="sxs-lookup"><span data-stu-id="ba28c-218">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="ba28c-219">O "TopologyResult" contém a posição central do volume retornado, a direção oposta (ou seja, normal) e as dimensões do espaço encontrado.</span><span class="sxs-lookup"><span data-stu-id="ba28c-219">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="ba28c-220">Observe que, no exemplo de Unity, cada uma dessas consultas é vinculada a um botão no painel de interface do usuário virtual.</span><span class="sxs-lookup"><span data-stu-id="ba28c-220">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="ba28c-221">Os códigos de exemplo codificam os parâmetros de cada uma dessas consultas para valores razoáveis.</span><span class="sxs-lookup"><span data-stu-id="ba28c-221">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="ba28c-222">Consulte SpaceVisualizer.cs no código de exemplo para obter mais exemplos.</span><span class="sxs-lookup"><span data-stu-id="ba28c-222">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="ba28c-223">Consultas de forma</span><span class="sxs-lookup"><span data-stu-id="ba28c-223">Shape Queries</span></span>

<span data-ttu-id="ba28c-224">Dentro da dll, o analisador de forma ("ShapeAnalyzer_W") usa o analisador de topologia para corresponder às formas personalizadas definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="ba28c-224">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="ba28c-225">O exemplo de Unity define um conjunto de formas e expõe os resultados por meio do menu consulta no aplicativo, dentro da guia forma. A intenção é que o usuário possa definir suas próprias consultas de forma de objeto e usá-las, conforme a necessidade de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-225">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="ba28c-226">Observe que a análise de forma funciona apenas em superfícies horizontais.</span><span class="sxs-lookup"><span data-stu-id="ba28c-226">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="ba28c-227">Um sofá, por exemplo, é definido pela superfície de estação plana e a parte superior do sofá de volta.</span><span class="sxs-lookup"><span data-stu-id="ba28c-227">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="ba28c-228">A consulta de forma procura duas superfícies de um tamanho, altura e intervalo de aspecto específicos, com as duas superfícies alinhadas e conectadas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-228">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="ba28c-229">Usando a terminologia de APIs, a estação de sofá e a parte superior são componentes de forma e os requisitos de alinhamento são restrições de componente de forma.</span><span class="sxs-lookup"><span data-stu-id="ba28c-229">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="ba28c-230">Uma consulta de exemplo definida no exemplo de Unity (ShapeDefinition.cs) para objetos "sittable" é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ba28c-230">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="ba28c-231">Cada consulta de forma é definida por um conjunto de componentes de forma, cada um com um conjunto de restrições de componente e um conjunto de restrições de forma que listam as dependências entre os componentes.</span><span class="sxs-lookup"><span data-stu-id="ba28c-231">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="ba28c-232">Este exemplo inclui três restrições em uma única definição de componente e nenhuma restrição de forma entre os componentes (já que há apenas um componente).</span><span class="sxs-lookup"><span data-stu-id="ba28c-232">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="ba28c-233">Por outro lado, a forma de sofá tem dois componentes Shape e quatro restrições Shape.</span><span class="sxs-lookup"><span data-stu-id="ba28c-233">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="ba28c-234">Observe que os componentes são identificados por seu índice na lista de componentes do usuário (0 e 1 neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="ba28c-234">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="ba28c-235">As funções de wrapper são fornecidas no módulo do Unity para facilitar a criação de definições de formas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-235">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="ba28c-236">A lista completa de restrições de componente e forma pode ser encontrada em "SpatialUnderstandingDll.cs" nas estruturas "ShapeComponentConstraint" e "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="ba28c-236">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="ba28c-237">![forma de retângulo é encontrada nesta superfície](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba28c-237">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="ba28c-238">*A forma de retângulo foi encontrada nesta superfície*</span><span class="sxs-lookup"><span data-stu-id="ba28c-238">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="ba28c-239">Resolvedor de posicionamento de objeto</span><span class="sxs-lookup"><span data-stu-id="ba28c-239">Object Placement Solver</span></span>

<span data-ttu-id="ba28c-240">O resolvedor de posicionamento de objetos pode ser usado para identificar locais ideais no espaço físico para colocar seus objetos.</span><span class="sxs-lookup"><span data-stu-id="ba28c-240">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="ba28c-241">O solucionador encontrará o local mais adequado, considerando as regras e restrições do objeto.</span><span class="sxs-lookup"><span data-stu-id="ba28c-241">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="ba28c-242">Além disso, as consultas de objeto persistem até que o objeto seja removido com chamadas "Solver_RemoveObject" ou "Solver_RemoveAllObjects", permitindo o posicionamento restrito de vários objetos.</span><span class="sxs-lookup"><span data-stu-id="ba28c-242">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="ba28c-243">As consultas de posicionamento de objetos consistem em três partes: tipo de posicionamento com parâmetros, uma lista de regras e uma lista de restrições.</span><span class="sxs-lookup"><span data-stu-id="ba28c-243">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="ba28c-244">Para executar uma consulta, use a API a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba28c-244">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="ba28c-245">Essa função usa um nome de objeto, uma definição de posicionamento e uma lista de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="ba28c-245">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="ba28c-246">Os C# wrappers fornecem funções auxiliares de construção para facilitar a construção da regra e da restrição.</span><span class="sxs-lookup"><span data-stu-id="ba28c-246">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="ba28c-247">A definição de posicionamento contém o tipo de consulta – ou seja, uma das opções a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba28c-247">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="ba28c-248">Cada um dos tipos de posicionamento tem um conjunto de parâmetros exclusivos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-248">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="ba28c-249">A estrutura "ObjectPlacementDefinition" contém um conjunto de funções auxiliares estáticas para a criação dessas definições.</span><span class="sxs-lookup"><span data-stu-id="ba28c-249">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="ba28c-250">Por exemplo, para encontrar um local para colocar um objeto no chão, você pode usar a função a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba28c-250">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="ba28c-251">Public estática ObjectPlacementDefinition Create_OnFloor (Vector3 halfDims) Além do tipo de posicionamento, você pode fornecer um conjunto de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="ba28c-251">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="ba28c-252">As regras não podem ser violadas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-252">Rules cannot be violated.</span></span> <span data-ttu-id="ba28c-253">Os locais de posicionamento possíveis que atendem ao tipo e às regras são então otimizados em relação ao conjunto de restrições para selecionar o local de posicionamento ideal.</span><span class="sxs-lookup"><span data-stu-id="ba28c-253">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="ba28c-254">Cada uma das regras e restrições pode ser criada pelas funções de criação estática fornecidas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-254">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="ba28c-255">Uma regra de exemplo e uma função de construção de restrição são fornecidas abaixo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-255">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="ba28c-256">A consulta de posicionamento de objeto abaixo está procurando um local para colocar um cubo de meio medidor na borda de uma superfície, longe de outros objetos anteriormente posicionados e perto do centro da sala.</span><span class="sxs-lookup"><span data-stu-id="ba28c-256">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="ba28c-257">Se for bem-sucedida, uma estrutura "ObjectPlacementResult" contendo a posição de posicionamento, as dimensões e a orientação serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-257">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="ba28c-258">Além disso, o posicionamento é adicionado à lista interna de objetos posicionados da dll.</span><span class="sxs-lookup"><span data-stu-id="ba28c-258">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="ba28c-259">As consultas de posicionamento subsequentes levarão esse objeto à conta.</span><span class="sxs-lookup"><span data-stu-id="ba28c-259">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="ba28c-260">O arquivo "LevelSolver.cs" no exemplo de Unity contém mais consultas de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-260">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="ba28c-261">![resultados da colocação do objeto](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba28c-261">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="ba28c-262">*Figura 3: as caixas azuis como o resultado de três lugares em consultas de piso com afastamento das regras de posição da câmera*</span><span class="sxs-lookup"><span data-stu-id="ba28c-262">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="ba28c-263">Ao resolver o local de posicionamento de vários objetos necessários para um cenário de nível ou aplicativo, primeiro resolva os objetos indispensável e grandes para maximizar a probabilidade de que um espaço possa ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="ba28c-263">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="ba28c-264">A ordem de posicionamento é importante.</span><span class="sxs-lookup"><span data-stu-id="ba28c-264">Placement order is important.</span></span> <span data-ttu-id="ba28c-265">Se os posicionamentos de objeto não puderem ser encontrados, tente configurações menos restritas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-265">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="ba28c-266">Ter um conjunto de configurações de fallback é essencial para dar suporte à funcionalidade em várias configurações de sala.</span><span class="sxs-lookup"><span data-stu-id="ba28c-266">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="ba28c-267">Processo de verificação de sala</span><span class="sxs-lookup"><span data-stu-id="ba28c-267">Room Scanning Process</span></span>

<span data-ttu-id="ba28c-268">Embora a solução de mapeamento espacial fornecida pelo HoloLens seja projetada para ser genérica o suficiente para atender às necessidades de toda a gama de espaços problemáticos, o módulo de compreensão espacial foi criado para dar suporte às necessidades de dois jogos específicos.</span><span class="sxs-lookup"><span data-stu-id="ba28c-268">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="ba28c-269">Sua solução é estruturada em um processo específico e um conjunto de suposições, resumido abaixo.</span><span class="sxs-lookup"><span data-stu-id="ba28c-269">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="ba28c-270">"Pintura" Playspace orientada por usuário – durante a fase de verificação, o usuário se move e procura o ritmo das jogas, pintando efetivamente as áreas que devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-270">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="ba28c-271">A malha gerada é importante para fornecer comentários do usuário durante essa fase.</span><span class="sxs-lookup"><span data-stu-id="ba28c-271">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="ba28c-272">Inportações domésticas ou de configuração do Office – as funções de consulta são projetadas em relação a superfícies simples e paredes em ângulos retos.</span><span class="sxs-lookup"><span data-stu-id="ba28c-272">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="ba28c-273">Essa é uma limitação flexível.</span><span class="sxs-lookup"><span data-stu-id="ba28c-273">This is a soft limitation.</span></span> <span data-ttu-id="ba28c-274">No entanto, durante a fase de verificação, uma análise de eixo primário é concluída para otimizar o mosaico de malha ao longo do eixo principal e secundário.</span><span class="sxs-lookup"><span data-stu-id="ba28c-274">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="ba28c-275">O arquivo SpatialUnderstanding.cs incluído gerencia o processo da fase de verificação.</span><span class="sxs-lookup"><span data-stu-id="ba28c-275">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="ba28c-276">Ele chama as funções a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba28c-276">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="ba28c-277">O fluxo de verificação, controlado pelo comportamento "SpatialUnderstanding", chama InitScan e, em seguida, UpdateScan cada quadro.</span><span class="sxs-lookup"><span data-stu-id="ba28c-277">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="ba28c-278">Quando a consulta de estatísticas relata cobertura razoável, o usuário tem permissão para airtap chamar RequestFinish para indicar o fim da fase de verificação.</span><span class="sxs-lookup"><span data-stu-id="ba28c-278">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="ba28c-279">UpdateScan continua sendo chamado até que o valor de retorno indique que a dll concluiu o processamento.</span><span class="sxs-lookup"><span data-stu-id="ba28c-279">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="ba28c-280">Entendendo a malha</span><span class="sxs-lookup"><span data-stu-id="ba28c-280">Understanding Mesh</span></span>

<span data-ttu-id="ba28c-281">A DLL de compreensão armazena internamente o Playspace como uma grade de cubos VOXEL dimensionados do 8cm.</span><span class="sxs-lookup"><span data-stu-id="ba28c-281">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="ba28c-282">Durante a parte inicial da verificação, uma análise de componente primário é concluída para determinar os eixos da sala.</span><span class="sxs-lookup"><span data-stu-id="ba28c-282">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="ba28c-283">Internamente, ele armazena seu espaço VOXEL alinhado a esses eixos.</span><span class="sxs-lookup"><span data-stu-id="ba28c-283">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="ba28c-284">Uma malha é gerada aproximadamente a cada segundo, extraindo o isosurface do volume VOXEL.</span><span class="sxs-lookup"><span data-stu-id="ba28c-284">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="ba28c-285">![malha gerada produzida do volume VOXEL](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba28c-285">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="ba28c-286">*Malha gerada produzida a partir do volume VOXEL*</span><span class="sxs-lookup"><span data-stu-id="ba28c-286">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="ba28c-287">Painel de controle da</span><span class="sxs-lookup"><span data-stu-id="ba28c-287">Troubleshooting</span></span>
* <span data-ttu-id="ba28c-288">Verifique se você definiu o recurso [SpatialPerception](#setting-the-spatialperception-capability)</span><span class="sxs-lookup"><span data-stu-id="ba28c-288">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="ba28c-289">Quando o rastreamento for perdido, o próximo evento onsurfacechanged removerá todas as malhas.</span><span class="sxs-lookup"><span data-stu-id="ba28c-289">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="ba28c-290">Mapeamento espacial no kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="ba28c-290">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="ba28c-291">Para obter mais informações sobre como usar o mapeamento espacial com o kit de ferramentas de realidade misturada v2, consulte a <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">seção reconhecimento espacial</a> do docs MRTK.</span><span class="sxs-lookup"><span data-stu-id="ba28c-291">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba28c-292">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba28c-292">See also</span></span>
* [<span data-ttu-id="ba28c-293">MR espacial 230: mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="ba28c-293">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="ba28c-294">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="ba28c-294">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="ba28c-295">Sistemas de coordenadas no Unity</span><span class="sxs-lookup"><span data-stu-id="ba28c-295">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="ba28c-296"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="ba28c-296"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="ba28c-297"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="ba28c-297"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="ba28c-298"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="ba28c-298"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="ba28c-299"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a></span><span class="sxs-lookup"><span data-stu-id="ba28c-299"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>

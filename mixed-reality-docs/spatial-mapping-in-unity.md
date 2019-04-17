---
title: Mapeamento espacial no Unity
description: Renderização e colidam a geometria do mundo real ao seu redor no Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapeamento espacial, processador, colisor, malha, varredura, componente
ms.openlocfilehash: f938f5921cb2c06342a9ebcd376d690c10584df9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591031"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="547b9-104">Mapeamento espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="547b9-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="547b9-105">Este tópico descreve como usar [mapeamento espacial](spatial-mapping.md) em seu projeto do Unity, recuperando as malhas de triângulos que representam as superfícies do mundo em torno de um dispositivo HoloLens, posicionamento, oclusão, análise de sala e muito mais.</span><span class="sxs-lookup"><span data-stu-id="547b9-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="547b9-106">A Unity inclui suporte completo para o mapeamento espacial, que é exposto aos desenvolvedores das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="547b9-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="547b9-107">Mapeamento de componentes disponíveis no MixedRealityToolkit espacial, que fornecem um caminho rápido e conveniente para começar o mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="547b9-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="547b9-108">Mapeamento espacial de nível inferior das APIs, que fornecem completo controlar e habilitar a personalização de específico de aplicativo mais sofisticada</span><span class="sxs-lookup"><span data-stu-id="547b9-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="547b9-109">Para usar o mapeamento espacial em seu aplicativo, a capacidade de spatialPerception precisa ser definido em seu AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="547b9-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="547b9-110">Definindo a capacidade de SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="547b9-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="547b9-111">Para um aplicativo consumir dados de mapeamento espacial, a capacidade de SpatialPerception deve ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="547b9-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="547b9-112">Como habilitar a funcionalidade de SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="547b9-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="547b9-113">No Editor do Unity, abra o **"Configurações do Player"** painel (Editar > configurações do projeto > Player)</span><span class="sxs-lookup"><span data-stu-id="547b9-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="547b9-114">Clique no **"Windows Store"** guia</span><span class="sxs-lookup"><span data-stu-id="547b9-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="547b9-115">Expandir **"Configurações de publicação"** e verifique o **"SpatialPerception"** funcionalidade no **"Recursos"** lista</span><span class="sxs-lookup"><span data-stu-id="547b9-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="547b9-116">Observe que, se você já tiver exportado seu projeto do Unity para uma solução do Visual Studio, você precisará para exportar para uma nova pasta ou manualmente [definir esse recurso em que o AppxManifest no Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="547b9-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="547b9-117">Mapeamento espacial também requer um MaxVersionTested pelo menos 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="547b9-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="547b9-118">No Visual Studio, clique com botão direito **Package. appxmanifest** no Gerenciador de soluções e selecione **Exibir código**</span><span class="sxs-lookup"><span data-stu-id="547b9-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="547b9-119">Localize a linha especificando **TargetDeviceFamily** e altere **MaxVersionTested = "10.0.10240.0"** para **MaxVersionTested = "10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="547b9-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="547b9-120">**Salvar** Package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="547b9-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="547b9-121">Introdução aos componentes de mapeamento espacial interna do Unity</span><span class="sxs-lookup"><span data-stu-id="547b9-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="547b9-122">2 componentes para facilmente adicionar mapeamento espacial ao seu aplicativo do Unity oferece **renderizador de mapeamento espacial** e **Colisor de mapeamento espacial**.</span><span class="sxs-lookup"><span data-stu-id="547b9-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="547b9-123">Renderizador de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="547b9-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="547b9-124">O renderizador de mapeamento espacial permite a visualização da malha mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="547b9-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Renderizador de mapeamento espacial no Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="547b9-126">Mapeamento espacial Colisor</span><span class="sxs-lookup"><span data-stu-id="547b9-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="547b9-127">Permite que o Colisor mapeamento espacial holográfico conteúdo (ou caractere) interação, como física, com a malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="547b9-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Mapeamento espacial Colisor no Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="547b9-129">Usando os componentes internos mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="547b9-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="547b9-130">Você pode adicionar os dois componentes ao seu aplicativo se você gostaria de visualizar e interagir com as superfícies de físico.</span><span class="sxs-lookup"><span data-stu-id="547b9-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="547b9-131">Para usar esses dois componentes em seu aplicativo do Unity:</span><span class="sxs-lookup"><span data-stu-id="547b9-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="547b9-132">Selecione um GameObject no centro da área na qual você deseja detectar malhas de superfície espaciais.</span><span class="sxs-lookup"><span data-stu-id="547b9-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="547b9-133">Na janela Inspetor, **Add Component** > **XR** > **Colisor de mapeamento espacial** ou **espacial Mapeamento de renderizador**.</span><span class="sxs-lookup"><span data-stu-id="547b9-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="547b9-134">Você pode encontrar mais detalhes sobre como usar esses componentes na <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">site de documentação do Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="547b9-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="547b9-135">Indo além dos componentes internos mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="547b9-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="547b9-136">Esses componentes torná-lo arrastar e soltar fácil começar a usar com o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="547b9-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="547b9-137"> Quando você deseja ir além disso, há dois caminhos principais para explorar:</span><span class="sxs-lookup"><span data-stu-id="547b9-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="547b9-138">Para fazer seu próprio processamento de malha de nível inferior, consulte a seção abaixo sobre o script de nível baixo de mapeamento espacial API.</span><span class="sxs-lookup"><span data-stu-id="547b9-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="547b9-139">Para fazer a análise de malha de alto nível, consulte a seção abaixo sobre a biblioteca SpatialUnderstanding na <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="547b9-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="547b9-140">Usando o Unity espacial mapeamento de API de nível inferior</span><span class="sxs-lookup"><span data-stu-id="547b9-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="547b9-141">Se você precisar de mais controle do que obter os componentes do renderizador de mapeamento espacial e Colisor de mapeamento espacial, você pode usar o script de nível baixo de mapeamento espacial APIs.</span><span class="sxs-lookup"><span data-stu-id="547b9-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="547b9-142">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="547b9-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="547b9-143">**Tipos de**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="547b9-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="547b9-144">A seguir é uma estrutura de tópicos do fluxo sugerido para um aplicativo que usa o mapeamento espacial APIs.</span><span class="sxs-lookup"><span data-stu-id="547b9-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="547b9-145">Configurar o SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="547b9-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="547b9-146">Criar uma instância de um objeto SurfaceObserver para cada região definida pelo aplicativo de espaço que você precisa de dados de mapeamento espacial para.</span><span class="sxs-lookup"><span data-stu-id="547b9-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="547b9-147">Especifique a região de espaço que cada objeto SurfaceObserver fornecerá dados para chamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox ou SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="547b9-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="547b9-148">Você pode redefinir a região de espaço no futuro, simplesmente chamando um dos seguintes métodos novamente.</span><span class="sxs-lookup"><span data-stu-id="547b9-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="547b9-149">Quando você chama SurfaceObserver.Update(), você deve fornecer um manipulador para cada superfície espacial na região do SurfaceObserver de espaço que o sistema de mapeamento espacial tem novas informações para.</span><span class="sxs-lookup"><span data-stu-id="547b9-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="547b9-150">O manipulador recebe, para uma superfície espacial:</span><span class="sxs-lookup"><span data-stu-id="547b9-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="547b9-151">Tratando alterações de superfície</span><span class="sxs-lookup"><span data-stu-id="547b9-151">Handling Surface Changes</span></span>

<span data-ttu-id="547b9-152">Há vários casos principais para lidar com.</span><span class="sxs-lookup"><span data-stu-id="547b9-152">There are several main cases to handle.</span></span> <span data-ttu-id="547b9-153">Adicionado & atualizado que pode usar o mesmo código caminho e removido.</span><span class="sxs-lookup"><span data-stu-id="547b9-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="547b9-154">Nos casos adicionadas e atualizadas no exemplo, podemos adicionar ou obter o GameObject que representa isso do dicionário de malha, crie um struct SurfaceData com os componentes necessários, então chamar RequestMeshDataAsync para preencher o GameObject com os dados de malha e Posicione na cena.</span><span class="sxs-lookup"><span data-stu-id="547b9-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="547b9-155">No caso de removido, podemos remover o GameObject que representa essa malha do dicionário e destruí-lo.</span><span class="sxs-lookup"><span data-stu-id="547b9-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="547b9-156">Manipulação de dados pronto</span><span class="sxs-lookup"><span data-stu-id="547b9-156">Handling Data Ready</span></span>

<span data-ttu-id="547b9-157">O manipulador de OnDataReady recebe um objeto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="547b9-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="547b9-158">O WorldAnchor, MeshFilter e (opcionalmente) MeshCollider objetos que ele contém refletem o estado mais recente da superfície espacial associado.</span><span class="sxs-lookup"><span data-stu-id="547b9-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="547b9-159">Opcionalmente, executar análise de e/ou [processamento](spatial-mapping.md#mesh-processing) dos dados de malha, acessando o membro de malha do objeto MeshFilter.</span><span class="sxs-lookup"><span data-stu-id="547b9-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="547b9-160">Renderizar a superfície espacial com a malha mais recente e (opcionalmente) use-o para colisões de física e raycasts.</span><span class="sxs-lookup"><span data-stu-id="547b9-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="547b9-161">É importante confirmar que o conteúdo do SurfaceData não é nulo.</span><span class="sxs-lookup"><span data-stu-id="547b9-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="547b9-162">Iniciar o processamento de atualizações</span><span class="sxs-lookup"><span data-stu-id="547b9-162">Start processing on updates</span></span>

<span data-ttu-id="547b9-163">SurfaceObserver.Update() deve ser chamado em um atraso, não cada quadro.</span><span class="sxs-lookup"><span data-stu-id="547b9-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="547b9-164">Análise da malha de nível superior: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="547b9-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="547b9-165">O <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> é uma coleção de códigos de utilitários úteis para desenvolvimento holográfico baseado as APIs do Unity holográfica.</span><span class="sxs-lookup"><span data-stu-id="547b9-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="547b9-166">Noções básicas sobre espacial</span><span class="sxs-lookup"><span data-stu-id="547b9-166">Spatial Understanding</span></span>

<span data-ttu-id="547b9-167">Ao colocar hologramas no mundo físico geralmente é desejável para ir além do mapeamento espacial de malha e planos de superfície.</span><span class="sxs-lookup"><span data-stu-id="547b9-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="547b9-168">Quando o posicionamento é feito de maneira procedimental, um nível mais alto de compreensão ambiental é desejável.</span><span class="sxs-lookup"><span data-stu-id="547b9-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="547b9-169">Isso geralmente exige a tomada de decisões sobre o que é paredes, ceiling e floor.</span><span class="sxs-lookup"><span data-stu-id="547b9-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="547b9-170">Além disso, a capacidade de otimizar em relação a um conjunto de restrições de posicionamento para determinar os locais físicos mais desejáveis para objetos holographic.</span><span class="sxs-lookup"><span data-stu-id="547b9-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="547b9-171">Durante o desenvolvimento de fragmentos e Conker Young, Asobo estúdios enfrentado head esse problema no desenvolvimento de um solucionador de espaço para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="547b9-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="547b9-172">Cada um desses jogos tinha jogos necessidades específicas, mas eles compartilhados espacial Compreendendo a tecnologia de núcleo.</span><span class="sxs-lookup"><span data-stu-id="547b9-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="547b9-173">O HoloToolkit.SpatialUnderstanding biblioteca encapsula dessa tecnologia, permitindo que você rapidamente localize de espaços vazios nas paredes, coloque os objetos no teto, identifica colocados por caractere sentar e uma grande variedade de outras consultas espaciais compreensão.</span><span class="sxs-lookup"><span data-stu-id="547b9-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="547b9-174">Todo o código-fonte está incluído, permitindo que você personalizá-lo às suas necessidades e compartilhar suas melhorias com a comunidade.</span><span class="sxs-lookup"><span data-stu-id="547b9-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="547b9-175">O código para o C++ solver foi encapsulado em uma dll UWP e exposto a Unity com uma queda no pré-fabricado contido dentro de MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="547b9-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="547b9-176">Noções básicas sobre módulos</span><span class="sxs-lookup"><span data-stu-id="547b9-176">Understanding Modules</span></span>

<span data-ttu-id="547b9-177">Existem três interfaces principais expostas pelo módulo: topologia para a superfície simple e consultas espaciais, forma para detecção de objetos e o Solucionador de posicionamento de objeto para o posicionamento de baseado em restrição de conjuntos de objetos.</span><span class="sxs-lookup"><span data-stu-id="547b9-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="547b9-178">Cada um deles é descrita abaixo.</span><span class="sxs-lookup"><span data-stu-id="547b9-178">Each of these is described below.</span></span> <span data-ttu-id="547b9-179">Além das três interfaces do módulo principal, uma interface de conversão de ray pode ser usada para recuperar tipos de superfície com marcas de formatação e uma malha playspace watertight personalizados pode ser copiada-out.</span><span class="sxs-lookup"><span data-stu-id="547b9-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="547b9-180">Conversão de Ray</span><span class="sxs-lookup"><span data-stu-id="547b9-180">Ray Casting</span></span>

<span data-ttu-id="547b9-181">Depois que a sala foi verificada e finalizada, rótulos são gerados internamente para superfícies de como o floor, ceiling e paredes.</span><span class="sxs-lookup"><span data-stu-id="547b9-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="547b9-182">O "PlayspaceRaycast" função usa um raio e retorna se o raio entra em conflito com uma superfície conhecida e caso, nesse, informações sobre o que são exibidos na forma de "RaycastResult".</span><span class="sxs-lookup"><span data-stu-id="547b9-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="547b9-183">Internamente, o raycast é calculado em relação a representação do playspace voxel do computada cm 8 ao cubo.</span><span class="sxs-lookup"><span data-stu-id="547b9-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="547b9-184">Cada voxel contém um conjunto de elementos de superfície com os dados processados topologia (também conhecido como surfels).</span><span class="sxs-lookup"><span data-stu-id="547b9-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="547b9-185">Os surfels contidos dentro da célula voxel interseccionadas são comparadas e a melhor correspondência usada para pesquisar as informações de topologia.</span><span class="sxs-lookup"><span data-stu-id="547b9-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="547b9-186">Esses dados de topologia contém os rótulos retornados na forma de enumeração "SurfaceTypes", bem como a área de superfície da superfície de interseccionada.</span><span class="sxs-lookup"><span data-stu-id="547b9-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="547b9-187">No exemplo de Unity, o cursor converte um raio a cada quadro.</span><span class="sxs-lookup"><span data-stu-id="547b9-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="547b9-188">Em primeiro lugar, em relação a colisores do Unity.</span><span class="sxs-lookup"><span data-stu-id="547b9-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="547b9-189">Em segundo lugar, em relação a representação do mundo do módulo de compreensão.</span><span class="sxs-lookup"><span data-stu-id="547b9-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="547b9-190">E por fim, novamente elementos interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="547b9-190">And finally, again UI elements.</span></span> <span data-ttu-id="547b9-191">Neste aplicativo, interface do usuário obtém prioridade, em seguida o resultado de compreensão e, por fim, colisores do Unity.</span><span class="sxs-lookup"><span data-stu-id="547b9-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="547b9-192">O SurfaceType é relatado como texto ao lado do cursor.</span><span class="sxs-lookup"><span data-stu-id="547b9-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="547b9-193">![Tipo de superfície é rotulado ao lado do cursor](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="547b9-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="547b9-194">*Tipo de superfície é rotulado ao lado do cursor*</span><span class="sxs-lookup"><span data-stu-id="547b9-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="547b9-195">Consultas de topologia</span><span class="sxs-lookup"><span data-stu-id="547b9-195">Topology Queries</span></span>

<span data-ttu-id="547b9-196">Dentro da DLL, o Gerenciador de topologia manipula a rotulagem do ambiente.</span><span class="sxs-lookup"><span data-stu-id="547b9-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="547b9-197">Conforme mencionado acima, muitos dos dados é armazenado em surfels, contidos dentro de um volume voxel.</span><span class="sxs-lookup"><span data-stu-id="547b9-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="547b9-198">Além disso, a estrutura de "PlaySpaceInfos" é usada para armazenar informações sobre o playspace, incluindo o alinhamento do mundo (para obter mais detalhes sobre isso abaixo), andar e altura de teto.</span><span class="sxs-lookup"><span data-stu-id="547b9-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="547b9-199">Heurística é usada para determinar as paredes, ceiling e floor.</span><span class="sxs-lookup"><span data-stu-id="547b9-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="547b9-200">Por exemplo, a superfície maior e menor horizontal com maior que 1 área da superfície m2 é considerada o chão.</span><span class="sxs-lookup"><span data-stu-id="547b9-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="547b9-201">Observe que o caminho de câmera durante o processo de verificação também é usado neste processo.</span><span class="sxs-lookup"><span data-stu-id="547b9-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="547b9-202">Um subconjunto de consultas expostas pelo Gerenciador de topologia são expostos por meio da dll.</span><span class="sxs-lookup"><span data-stu-id="547b9-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="547b9-203">As consultas de topologia expostos são da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="547b9-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="547b9-204">Cada uma das consultas tem um conjunto de parâmetros, específicos para o tipo de consulta.</span><span class="sxs-lookup"><span data-stu-id="547b9-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="547b9-205">No exemplo a seguir, o usuário Especifica a altura mínima & largura do volume desejado, a altura mínima de posicionamento acima do chão e a quantidade mínima de espaço livre na frente do volume.</span><span class="sxs-lookup"><span data-stu-id="547b9-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="547b9-206">Todas as medidas são em metros.</span><span class="sxs-lookup"><span data-stu-id="547b9-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="547b9-207">Cada uma dessas consultas usarão uma matriz alocada previamente de estruturas de "TopologyResult".</span><span class="sxs-lookup"><span data-stu-id="547b9-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="547b9-208">O parâmetro "locationCount" Especifica o comprimento da matriz passado.</span><span class="sxs-lookup"><span data-stu-id="547b9-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="547b9-209">O valor de retorno relata o número de locais retornados.</span><span class="sxs-lookup"><span data-stu-id="547b9-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="547b9-210">Esse número nunca é maior que o que for passado no parâmetro "locationCount".</span><span class="sxs-lookup"><span data-stu-id="547b9-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="547b9-211">"TopologyResult" contém a posição central do volume retornado, a direção oposta (ou seja, normal) e as dimensões do espaço encontrado.</span><span class="sxs-lookup"><span data-stu-id="547b9-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="547b9-212">Observe que a amostra do Unity, cada uma dessas consultas é vinculada a um botão no painel de interface do usuário virtual.</span><span class="sxs-lookup"><span data-stu-id="547b9-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="547b9-213">O disco rígido do exemplo codifica os parâmetros para cada uma dessas consultas para valores razoáveis.</span><span class="sxs-lookup"><span data-stu-id="547b9-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="547b9-214">Consulte SpaceVisualizer.cs no código de exemplo para obter mais exemplos.</span><span class="sxs-lookup"><span data-stu-id="547b9-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="547b9-215">Consultas de forma</span><span class="sxs-lookup"><span data-stu-id="547b9-215">Shape Queries</span></span>

<span data-ttu-id="547b9-216">Dentro de dll, o analisador de forma ("ShapeAnalyzer_W") usa o analisador de topologia para correspondência com formas personalizadas definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="547b9-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="547b9-217">O exemplo do Unity define um conjunto de formas e expõe os resultados-out por meio do menu de consulta no aplicativo, dentro da guia de forma. A intenção é que o usuário pode definir suas próprias consultas de forma do objeto e fazer usar desses, conforme exigido pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="547b9-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="547b9-218">Observe que a análise de forma funciona em superfícies horizontais apenas.</span><span class="sxs-lookup"><span data-stu-id="547b9-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="547b9-219">Por exemplo, um sofá, é definido, a superfície de estação simples e simples parte superior do sofá novamente.</span><span class="sxs-lookup"><span data-stu-id="547b9-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="547b9-220">A consulta de forma procura duas superfícies de um intervalo de tamanho, altura e os aspectos específico, com as superfícies de dois alinhada e conectado.</span><span class="sxs-lookup"><span data-stu-id="547b9-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="547b9-221">Com a terminologia de APIs, o assento sofá e o back-top são componentes de forma e os requisitos de alinhamento são as restrições de componentes de forma.</span><span class="sxs-lookup"><span data-stu-id="547b9-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="547b9-222">Um exemplo de consulta definido no exemplo Unity (ShapeDefinition.cs) para objetos "sittable" é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="547b9-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="547b9-223">Cada consulta de forma é definida por um conjunto de componentes de forma, cada um com um conjunto de restrições de componente e um conjunto de restrições de forma que listando as dependências entre os componentes.</span><span class="sxs-lookup"><span data-stu-id="547b9-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="547b9-224">Este exemplo inclui três restrições na definição de um único componente e sem restrições de forma entre os componentes (como há apenas um componente).</span><span class="sxs-lookup"><span data-stu-id="547b9-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="547b9-225">Por outro lado, a forma de sofá tem dois componentes de forma e quatro restrições de forma.</span><span class="sxs-lookup"><span data-stu-id="547b9-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="547b9-226">Observe que os componentes são identificados por seu índice na lista de componentes do usuário (0 e 1 neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="547b9-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="547b9-227">Funções de wrapper são fornecidas no módulo do Unity para facilitar a criação de definições de forma personalizada.</span><span class="sxs-lookup"><span data-stu-id="547b9-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="547b9-228">A lista completa de restrições de componente e a forma pode ser encontrada em "SpatialUnderstandingDll.cs" em "ShapeComponentConstraint" e as estruturas de "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="547b9-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="547b9-229">![Forma de retângulo é encontrada nessa superfície](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="547b9-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="547b9-230">*Forma de retângulo é encontrada nessa superfície*</span><span class="sxs-lookup"><span data-stu-id="547b9-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="547b9-231">Solucionador de posicionamento de objeto</span><span class="sxs-lookup"><span data-stu-id="547b9-231">Object Placement Solver</span></span>

<span data-ttu-id="547b9-232">O Solucionador de posicionamento de objeto pode ser usado para identificar locais ideais na sala de físico para colocar seus objetos.</span><span class="sxs-lookup"><span data-stu-id="547b9-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="547b9-233">O solucionador encontrará que o melhor local fornecido a restrições e regras de objeto.</span><span class="sxs-lookup"><span data-stu-id="547b9-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="547b9-234">Além disso, as consultas de objeto persistem até que o objeto for removido com "Solver_RemoveObject" ou "Solver_RemoveAllObjects" chamadas, permitindo que restrito posicionamento de vários objeto.</span><span class="sxs-lookup"><span data-stu-id="547b9-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="547b9-235">Consultas de posicionamento de objetos consistem em três partes: o tipo de posicionamento com parâmetros, uma lista de regras e uma lista de restrições.</span><span class="sxs-lookup"><span data-stu-id="547b9-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="547b9-236">Para executar uma consulta, use a seguinte API.</span><span class="sxs-lookup"><span data-stu-id="547b9-236">To run a query, use the following API.</span></span>

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

<span data-ttu-id="547b9-237">Essa função usa um nome de objeto, definição de posicionamento e uma lista de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="547b9-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="547b9-238">O C# wrappers funções auxiliares para facilitar a construção de restrição e regra de construção fornece.</span><span class="sxs-lookup"><span data-stu-id="547b9-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="547b9-239">A definição de posicionamento contém o tipo de consulta – ou seja, um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="547b9-239">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="547b9-240">Cada um dos tipos de posicionamento tem um conjunto de parâmetros exclusivos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="547b9-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="547b9-241">A estrutura de "ObjectPlacementDefinition" contém um conjunto de funções auxiliares estáticos para criar essas definições.</span><span class="sxs-lookup"><span data-stu-id="547b9-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="547b9-242">Por exemplo, para encontrar um local para colocar um objeto no chão, você pode usar a função a seguir.</span><span class="sxs-lookup"><span data-stu-id="547b9-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="547b9-243">público estático ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) em adição ao tipo de posicionamento, você pode fornecer um conjunto de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="547b9-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="547b9-244">As regras não podem ser violadas.</span><span class="sxs-lookup"><span data-stu-id="547b9-244">Rules cannot be violated.</span></span> <span data-ttu-id="547b9-245">Locais possíveis para posicionamento que satisfazem o tipo e as regras são otimizados, em seguida, em relação ao conjunto de restrições para selecionar o local ideal de posicionamento.</span><span class="sxs-lookup"><span data-stu-id="547b9-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="547b9-246">Cada uma das regras e restrições pode ser criada pelas funções de criação estáticos fornecido.</span><span class="sxs-lookup"><span data-stu-id="547b9-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="547b9-247">Uma função de construção de restrição e regra de exemplo é fornecida abaixo.</span><span class="sxs-lookup"><span data-stu-id="547b9-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="547b9-248">O abaixo do objeto de consulta de posicionamento está procurando um lugar para colocar um cubo de metade do medidor na borda de uma superfície, longe outros anteriormente colocar objetos e próximo ao centro da sala.</span><span class="sxs-lookup"><span data-stu-id="547b9-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="547b9-249">Se for bem-sucedido, uma estrutura de "ObjectPlacementResult" que contém a posição de posicionamento, dimensões e a orientação é retornado.</span><span class="sxs-lookup"><span data-stu-id="547b9-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="547b9-250">Além disso, o posicionamento é adicionado à lista interna da dll de objetos inseridos.</span><span class="sxs-lookup"><span data-stu-id="547b9-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="547b9-251">Consultas subsequentes posicionamento levarão a esse objeto em conta.</span><span class="sxs-lookup"><span data-stu-id="547b9-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="547b9-252">O arquivo "LevelSolver.cs" na amostra Unity contém mais consultas de exemplo.</span><span class="sxs-lookup"><span data-stu-id="547b9-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="547b9-253">![Resultados do posicionamento de objeto](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="547b9-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="547b9-254">*Figura 3: O azul caixas como o resultado de três lugar no chão as consultas com longe as regras de posição de câmera*</span><span class="sxs-lookup"><span data-stu-id="547b9-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="547b9-255">Quando a solução para o local de posicionamento de vários objetos necessários para um cenário de nível ou do aplicativo, primeiro solucione indispensáveis e grandes objetos na ordem para maximizar a probabilidade de um espaço pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="547b9-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="547b9-256">Posicionamento de ordem é importante.</span><span class="sxs-lookup"><span data-stu-id="547b9-256">Placement order is important.</span></span> <span data-ttu-id="547b9-257">Se os posicionamentos de objeto não for encontrados, tente configurações menos restritas.</span><span class="sxs-lookup"><span data-stu-id="547b9-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="547b9-258">Ter um conjunto de configurações de fallback é essencial para dar suporte a funcionalidade em muitas configurações de espaço.</span><span class="sxs-lookup"><span data-stu-id="547b9-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="547b9-259">Processo de verificação de espaço</span><span class="sxs-lookup"><span data-stu-id="547b9-259">Room Scanning Process</span></span>

<span data-ttu-id="547b9-260">Enquanto a solução de mapeamento espacial fornecida pelo HoloLens é projetada para ser genérico o suficiente para atender às necessidades de toda a gama de problemas de espaço, o módulo de compreensão espacial foi criado para suportar as necessidades de dois jogos específicos.</span><span class="sxs-lookup"><span data-stu-id="547b9-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="547b9-261">Sua solução é estruturada em torno de um processo específico e um conjunto de suposições, resumidas abaixo.</span><span class="sxs-lookup"><span data-stu-id="547b9-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="547b9-262">Usuário controlado por playspace "pintura" – durante a fase de verificação, o usuário move e procura ao redor de desempenha o ritmo, pintura com eficiência as áreas que devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="547b9-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="547b9-263">A malha gerada é importante fornecer comentários do usuário durante essa fase.</span><span class="sxs-lookup"><span data-stu-id="547b9-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="547b9-264">Em locais fechados home ou configuração do office – a consulta, as funções são projetadas em torno de superfícies simples e paredes ângulos retos.</span><span class="sxs-lookup"><span data-stu-id="547b9-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="547b9-265">Essa é uma limitação suave.</span><span class="sxs-lookup"><span data-stu-id="547b9-265">This is a soft limitation.</span></span> <span data-ttu-id="547b9-266">No entanto, durante a fase de verificação, uma análise de eixo primário é concluída para otimizar o mosaico de malha ao longo do eixo principal e secundário.</span><span class="sxs-lookup"><span data-stu-id="547b9-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="547b9-267">O arquivo SpatialUnderstanding.cs incluído gerencia o processo de fase de verificação.</span><span class="sxs-lookup"><span data-stu-id="547b9-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="547b9-268">Ele chama as funções a seguir.</span><span class="sxs-lookup"><span data-stu-id="547b9-268">It calls the following functions.</span></span>

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

<span data-ttu-id="547b9-269">O fluxo de varredura, acompanhando o comportamento de "SpatialUnderstanding" chama InitScan e, em seguida, UpdateScan cada quadro.</span><span class="sxs-lookup"><span data-stu-id="547b9-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="547b9-270">Quando a consulta de estatísticas relata a cobertura razoável, o usuário tem permissão para airtap chamar RequestFinish para indicar o final da fase de verificação.</span><span class="sxs-lookup"><span data-stu-id="547b9-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="547b9-271">UpdateScan continua a ser chamada até que ele é retornado o valor indica que a dll foi concluído o processamento.</span><span class="sxs-lookup"><span data-stu-id="547b9-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="547b9-272">Noções básicas sobre malha</span><span class="sxs-lookup"><span data-stu-id="547b9-272">Understanding Mesh</span></span>

<span data-ttu-id="547b9-273">A dll de Noções básicas sobre armazena internamente o playspace como uma grade de cubos de voxel 8cm em tamanho.</span><span class="sxs-lookup"><span data-stu-id="547b9-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="547b9-274">Durante a parte inicial da verificação, uma análise de componente principal é concluída para determinar os eixos da sala.</span><span class="sxs-lookup"><span data-stu-id="547b9-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="547b9-275">Internamente, ele armazena seu espaço de voxel alinhado com esses eixos.</span><span class="sxs-lookup"><span data-stu-id="547b9-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="547b9-276">Uma malha é gerada aproximadamente a cada segundo por meio da extração do isosurface do volume voxel.</span><span class="sxs-lookup"><span data-stu-id="547b9-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="547b9-277">![Malha gerada produzida a partir do volume voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="547b9-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="547b9-278">*Malha gerada produzida a partir do volume voxel*</span><span class="sxs-lookup"><span data-stu-id="547b9-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="547b9-279">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="547b9-279">Troubleshooting</span></span>
* <span data-ttu-id="547b9-280">Verifique se você tiver definido o [SpatialPerception](#setting-the-spatialperception-capability) capacidade</span><span class="sxs-lookup"><span data-stu-id="547b9-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="547b9-281">Quando o controle for perdido, o próximo evento OnSurfaceChanged removerá todas as malhas.</span><span class="sxs-lookup"><span data-stu-id="547b9-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="547b9-282">Mapeamento espacial no Kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="547b9-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="547b9-283">Para obter mais informações sobre como usar o mapeamento espacial com o Kit de ferramentas de realidade misturada v2, consulte o <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">seção reconhecimento espacial</a> do docs MRTK.</span><span class="sxs-lookup"><span data-stu-id="547b9-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="547b9-284">Consulte também</span><span class="sxs-lookup"><span data-stu-id="547b9-284">See also</span></span>
* [<span data-ttu-id="547b9-285">MR Spatial 230: Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="547b9-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="547b9-286">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="547b9-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="547b9-287">Sistemas de coordenadas no Unity</span><span class="sxs-lookup"><span data-stu-id="547b9-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="547b9-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="547b9-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="547b9-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="547b9-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="547b9-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="547b9-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="547b9-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="547b9-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>

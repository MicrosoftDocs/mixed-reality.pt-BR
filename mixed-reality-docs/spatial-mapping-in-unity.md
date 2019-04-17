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
# <a name="spatial-mapping-in-unity"></a>Mapeamento espacial no Unity

Este tópico descreve como usar [mapeamento espacial](spatial-mapping.md) em seu projeto do Unity, recuperando as malhas de triângulos que representam as superfícies do mundo em torno de um dispositivo HoloLens, posicionamento, oclusão, análise de sala e muito mais.

A Unity inclui suporte completo para o mapeamento espacial, que é exposto aos desenvolvedores das seguintes maneiras:
1. Mapeamento de componentes disponíveis no MixedRealityToolkit espacial, que fornecem um caminho rápido e conveniente para começar o mapeamento espacial
2. Mapeamento espacial de nível inferior das APIs, que fornecem completo controlar e habilitar a personalização de específico de aplicativo mais sofisticada

Para usar o mapeamento espacial em seu aplicativo, a capacidade de spatialPerception precisa ser definido em seu AppxManifest.

## <a name="setting-the-spatialperception-capability"></a>Definindo a capacidade de SpatialPerception

Para um aplicativo consumir dados de mapeamento espacial, a capacidade de SpatialPerception deve ser habilitada.

Como habilitar a funcionalidade de SpatialPerception:
1. No Editor do Unity, abra o **"Configurações do Player"** painel (Editar > configurações do projeto > Player)
2. Clique no **"Windows Store"** guia
3. Expandir **"Configurações de publicação"** e verifique o **"SpatialPerception"** funcionalidade no **"Recursos"** lista

Observe que, se você já tiver exportado seu projeto do Unity para uma solução do Visual Studio, você precisará para exportar para uma nova pasta ou manualmente [definir esse recurso em que o AppxManifest no Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Mapeamento espacial também requer um MaxVersionTested pelo menos 10.0.10586.0:
1. No Visual Studio, clique com botão direito **Package. appxmanifest** no Gerenciador de soluções e selecione **Exibir código**
2. Localize a linha especificando **TargetDeviceFamily** e altere **MaxVersionTested = "10.0.10240.0"** para **MaxVersionTested = "10.0.10586.0"**
3. **Salvar** Package. appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introdução aos componentes de mapeamento espacial interna do Unity

2 componentes para facilmente adicionar mapeamento espacial ao seu aplicativo do Unity oferece **renderizador de mapeamento espacial** e **Colisor de mapeamento espacial**.

### <a name="spatial-mapping-renderer"></a>Renderizador de mapeamento espacial

O renderizador de mapeamento espacial permite a visualização da malha mapeamento espacial.

![Renderizador de mapeamento espacial no Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Mapeamento espacial Colisor

Permite que o Colisor mapeamento espacial holográfico conteúdo (ou caractere) interação, como física, com a malha de mapeamento espacial.

![Mapeamento espacial Colisor no Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Usando os componentes internos mapeamento espacial

Você pode adicionar os dois componentes ao seu aplicativo se você gostaria de visualizar e interagir com as superfícies de físico.

Para usar esses dois componentes em seu aplicativo do Unity:
1. Selecione um GameObject no centro da área na qual você deseja detectar malhas de superfície espaciais.
2. Na janela Inspetor, **Add Component** > **XR** > **Colisor de mapeamento espacial** ou **espacial Mapeamento de renderizador**.

Você pode encontrar mais detalhes sobre como usar esses componentes na <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">site de documentação do Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Indo além dos componentes internos mapeamento espacial

Esses componentes torná-lo arrastar e soltar fácil começar a usar com o mapeamento espacial.  Quando você deseja ir além disso, há dois caminhos principais para explorar:
* Para fazer seu próprio processamento de malha de nível inferior, consulte a seção abaixo sobre o script de nível baixo de mapeamento espacial API.
* Para fazer a análise de malha de alto nível, consulte a seção abaixo sobre a biblioteca SpatialUnderstanding na <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Usando o Unity espacial mapeamento de API de nível inferior

Se você precisar de mais controle do que obter os componentes do renderizador de mapeamento espacial e Colisor de mapeamento espacial, você pode usar o script de nível baixo de mapeamento espacial APIs.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipos de**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

A seguir é uma estrutura de tópicos do fluxo sugerido para um aplicativo que usa o mapeamento espacial APIs.

### <a name="set-up-the-surfaceobservers"></a>Configurar o SurfaceObserver(s)

Criar uma instância de um objeto SurfaceObserver para cada região definida pelo aplicativo de espaço que você precisa de dados de mapeamento espacial para.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Especifique a região de espaço que cada objeto SurfaceObserver fornecerá dados para chamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox ou SetVolumeAsFrustum. Você pode redefinir a região de espaço no futuro, simplesmente chamando um dos seguintes métodos novamente.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Quando você chama SurfaceObserver.Update(), você deve fornecer um manipulador para cada superfície espacial na região do SurfaceObserver de espaço que o sistema de mapeamento espacial tem novas informações para. O manipulador recebe, para uma superfície espacial:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Tratando alterações de superfície

Há vários casos principais para lidar com. Adicionado & atualizado que pode usar o mesmo código caminho e removido.
* Nos casos adicionadas e atualizadas no exemplo, podemos adicionar ou obter o GameObject que representa isso do dicionário de malha, crie um struct SurfaceData com os componentes necessários, então chamar RequestMeshDataAsync para preencher o GameObject com os dados de malha e Posicione na cena.
* No caso de removido, podemos remover o GameObject que representa essa malha do dicionário e destruí-lo.

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

### <a name="handling-data-ready"></a>Manipulação de dados pronto

O manipulador de OnDataReady recebe um objeto SurfaceData. O WorldAnchor, MeshFilter e (opcionalmente) MeshCollider objetos que ele contém refletem o estado mais recente da superfície espacial associado. Opcionalmente, executar análise de e/ou [processamento](spatial-mapping.md#mesh-processing) dos dados de malha, acessando o membro de malha do objeto MeshFilter. Renderizar a superfície espacial com a malha mais recente e (opcionalmente) use-o para colisões de física e raycasts. É importante confirmar que o conteúdo do SurfaceData não é nulo.

### <a name="start-processing-on-updates"></a>Iniciar o processamento de atualizações

SurfaceObserver.Update() deve ser chamado em um atraso, não cada quadro.

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Análise da malha de nível superior: SpatialUnderstanding

O <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> é uma coleção de códigos de utilitários úteis para desenvolvimento holográfico baseado as APIs do Unity holográfica.

### <a name="spatial-understanding"></a>Noções básicas sobre espacial

Ao colocar hologramas no mundo físico geralmente é desejável para ir além do mapeamento espacial de malha e planos de superfície. Quando o posicionamento é feito de maneira procedimental, um nível mais alto de compreensão ambiental é desejável. Isso geralmente exige a tomada de decisões sobre o que é paredes, ceiling e floor. Além disso, a capacidade de otimizar em relação a um conjunto de restrições de posicionamento para determinar os locais físicos mais desejáveis para objetos holographic.

Durante o desenvolvimento de fragmentos e Conker Young, Asobo estúdios enfrentado head esse problema no desenvolvimento de um solucionador de espaço para essa finalidade. Cada um desses jogos tinha jogos necessidades específicas, mas eles compartilhados espacial Compreendendo a tecnologia de núcleo. O HoloToolkit.SpatialUnderstanding biblioteca encapsula dessa tecnologia, permitindo que você rapidamente localize de espaços vazios nas paredes, coloque os objetos no teto, identifica colocados por caractere sentar e uma grande variedade de outras consultas espaciais compreensão.

Todo o código-fonte está incluído, permitindo que você personalizá-lo às suas necessidades e compartilhar suas melhorias com a comunidade. O código para o C++ solver foi encapsulado em uma dll UWP e exposto a Unity com uma queda no pré-fabricado contido dentro de MixedRealityToolkit.

### <a name="understanding-modules"></a>Noções básicas sobre módulos

Existem três interfaces principais expostas pelo módulo: topologia para a superfície simple e consultas espaciais, forma para detecção de objetos e o Solucionador de posicionamento de objeto para o posicionamento de baseado em restrição de conjuntos de objetos. Cada um deles é descrita abaixo. Além das três interfaces do módulo principal, uma interface de conversão de ray pode ser usada para recuperar tipos de superfície com marcas de formatação e uma malha playspace watertight personalizados pode ser copiada-out.

### <a name="ray-casting"></a>Conversão de Ray

Depois que a sala foi verificada e finalizada, rótulos são gerados internamente para superfícies de como o floor, ceiling e paredes. O "PlayspaceRaycast" função usa um raio e retorna se o raio entra em conflito com uma superfície conhecida e caso, nesse, informações sobre o que são exibidos na forma de "RaycastResult".

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

Internamente, o raycast é calculado em relação a representação do playspace voxel do computada cm 8 ao cubo. Cada voxel contém um conjunto de elementos de superfície com os dados processados topologia (também conhecido como surfels). Os surfels contidos dentro da célula voxel interseccionadas são comparadas e a melhor correspondência usada para pesquisar as informações de topologia. Esses dados de topologia contém os rótulos retornados na forma de enumeração "SurfaceTypes", bem como a área de superfície da superfície de interseccionada.

No exemplo de Unity, o cursor converte um raio a cada quadro. Em primeiro lugar, em relação a colisores do Unity. Em segundo lugar, em relação a representação do mundo do módulo de compreensão. E por fim, novamente elementos interface do usuário. Neste aplicativo, interface do usuário obtém prioridade, em seguida o resultado de compreensão e, por fim, colisores do Unity. O SurfaceType é relatado como texto ao lado do cursor.

![Tipo de superfície é rotulado ao lado do cursor](images/su-raycastresults-300px.jpg)<br>
*Tipo de superfície é rotulado ao lado do cursor*

### <a name="topology-queries"></a>Consultas de topologia

Dentro da DLL, o Gerenciador de topologia manipula a rotulagem do ambiente. Conforme mencionado acima, muitos dos dados é armazenado em surfels, contidos dentro de um volume voxel. Além disso, a estrutura de "PlaySpaceInfos" é usada para armazenar informações sobre o playspace, incluindo o alinhamento do mundo (para obter mais detalhes sobre isso abaixo), andar e altura de teto. Heurística é usada para determinar as paredes, ceiling e floor. Por exemplo, a superfície maior e menor horizontal com maior que 1 área da superfície m2 é considerada o chão. Observe que o caminho de câmera durante o processo de verificação também é usado neste processo.

Um subconjunto de consultas expostas pelo Gerenciador de topologia são expostos por meio da dll. As consultas de topologia expostos são da seguinte maneira.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Cada uma das consultas tem um conjunto de parâmetros, específicos para o tipo de consulta. No exemplo a seguir, o usuário Especifica a altura mínima & largura do volume desejado, a altura mínima de posicionamento acima do chão e a quantidade mínima de espaço livre na frente do volume. Todas as medidas são em metros.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada uma dessas consultas usarão uma matriz alocada previamente de estruturas de "TopologyResult". O parâmetro "locationCount" Especifica o comprimento da matriz passado. O valor de retorno relata o número de locais retornados. Esse número nunca é maior que o que for passado no parâmetro "locationCount".

"TopologyResult" contém a posição central do volume retornado, a direção oposta (ou seja, normal) e as dimensões do espaço encontrado.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Observe que a amostra do Unity, cada uma dessas consultas é vinculada a um botão no painel de interface do usuário virtual. O disco rígido do exemplo codifica os parâmetros para cada uma dessas consultas para valores razoáveis. Consulte SpaceVisualizer.cs no código de exemplo para obter mais exemplos.

### <a name="shape-queries"></a>Consultas de forma

Dentro de dll, o analisador de forma ("ShapeAnalyzer_W") usa o analisador de topologia para correspondência com formas personalizadas definidas pelo usuário. O exemplo do Unity define um conjunto de formas e expõe os resultados-out por meio do menu de consulta no aplicativo, dentro da guia de forma. A intenção é que o usuário pode definir suas próprias consultas de forma do objeto e fazer usar desses, conforme exigido pelo seu aplicativo.

Observe que a análise de forma funciona em superfícies horizontais apenas. Por exemplo, um sofá, é definido, a superfície de estação simples e simples parte superior do sofá novamente. A consulta de forma procura duas superfícies de um intervalo de tamanho, altura e os aspectos específico, com as superfícies de dois alinhada e conectado. Com a terminologia de APIs, o assento sofá e o back-top são componentes de forma e os requisitos de alinhamento são as restrições de componentes de forma.

Um exemplo de consulta definido no exemplo Unity (ShapeDefinition.cs) para objetos "sittable" é o seguinte:

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

Cada consulta de forma é definida por um conjunto de componentes de forma, cada um com um conjunto de restrições de componente e um conjunto de restrições de forma que listando as dependências entre os componentes. Este exemplo inclui três restrições na definição de um único componente e sem restrições de forma entre os componentes (como há apenas um componente).

Por outro lado, a forma de sofá tem dois componentes de forma e quatro restrições de forma. Observe que os componentes são identificados por seu índice na lista de componentes do usuário (0 e 1 neste exemplo).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Funções de wrapper são fornecidas no módulo do Unity para facilitar a criação de definições de forma personalizada. A lista completa de restrições de componente e a forma pode ser encontrada em "SpatialUnderstandingDll.cs" em "ShapeComponentConstraint" e as estruturas de "ShapeConstraint".

![Forma de retângulo é encontrada nessa superfície](images/su-shapequery-300px.jpg)<br>
*Forma de retângulo é encontrada nessa superfície*

### <a name="object-placement-solver"></a>Solucionador de posicionamento de objeto

O Solucionador de posicionamento de objeto pode ser usado para identificar locais ideais na sala de físico para colocar seus objetos. O solucionador encontrará que o melhor local fornecido a restrições e regras de objeto. Além disso, as consultas de objeto persistem até que o objeto for removido com "Solver_RemoveObject" ou "Solver_RemoveAllObjects" chamadas, permitindo que restrito posicionamento de vários objeto. Consultas de posicionamento de objetos consistem em três partes: o tipo de posicionamento com parâmetros, uma lista de regras e uma lista de restrições. Para executar uma consulta, use a seguinte API.

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

Essa função usa um nome de objeto, definição de posicionamento e uma lista de regras e restrições. O C# wrappers funções auxiliares para facilitar a construção de restrição e regra de construção fornece. A definição de posicionamento contém o tipo de consulta – ou seja, um dos seguintes.

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

Cada um dos tipos de posicionamento tem um conjunto de parâmetros exclusivos para o tipo. A estrutura de "ObjectPlacementDefinition" contém um conjunto de funções auxiliares estáticos para criar essas definições. Por exemplo, para encontrar um local para colocar um objeto no chão, você pode usar a função a seguir. público estático ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) em adição ao tipo de posicionamento, você pode fornecer um conjunto de regras e restrições. As regras não podem ser violadas. Locais possíveis para posicionamento que satisfazem o tipo e as regras são otimizados, em seguida, em relação ao conjunto de restrições para selecionar o local ideal de posicionamento. Cada uma das regras e restrições pode ser criada pelas funções de criação estáticos fornecido. Uma função de construção de restrição e regra de exemplo é fornecida abaixo.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

O abaixo do objeto de consulta de posicionamento está procurando um lugar para colocar um cubo de metade do medidor na borda de uma superfície, longe outros anteriormente colocar objetos e próximo ao centro da sala.

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

Se for bem-sucedido, uma estrutura de "ObjectPlacementResult" que contém a posição de posicionamento, dimensões e a orientação é retornado. Além disso, o posicionamento é adicionado à lista interna da dll de objetos inseridos. Consultas subsequentes posicionamento levarão a esse objeto em conta. O arquivo "LevelSolver.cs" na amostra Unity contém mais consultas de exemplo.

![Resultados do posicionamento de objeto](images/su-objectplacement-1000px.jpg)<br>
*Figura 3: O azul caixas como o resultado de três lugar no chão as consultas com longe as regras de posição de câmera*

Quando a solução para o local de posicionamento de vários objetos necessários para um cenário de nível ou do aplicativo, primeiro solucione indispensáveis e grandes objetos na ordem para maximizar a probabilidade de um espaço pode ser encontrado. Posicionamento de ordem é importante. Se os posicionamentos de objeto não for encontrados, tente configurações menos restritas. Ter um conjunto de configurações de fallback é essencial para dar suporte a funcionalidade em muitas configurações de espaço.

### <a name="room-scanning-process"></a>Processo de verificação de espaço

Enquanto a solução de mapeamento espacial fornecida pelo HoloLens é projetada para ser genérico o suficiente para atender às necessidades de toda a gama de problemas de espaço, o módulo de compreensão espacial foi criado para suportar as necessidades de dois jogos específicos. Sua solução é estruturada em torno de um processo específico e um conjunto de suposições, resumidas abaixo.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

Usuário controlado por playspace "pintura" – durante a fase de verificação, o usuário move e procura ao redor de desempenha o ritmo, pintura com eficiência as áreas que devem ser incluídas. A malha gerada é importante fornecer comentários do usuário durante essa fase. Em locais fechados home ou configuração do office – a consulta, as funções são projetadas em torno de superfícies simples e paredes ângulos retos. Essa é uma limitação suave. No entanto, durante a fase de verificação, uma análise de eixo primário é concluída para otimizar o mosaico de malha ao longo do eixo principal e secundário. O arquivo SpatialUnderstanding.cs incluído gerencia o processo de fase de verificação. Ele chama as funções a seguir.

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

O fluxo de varredura, acompanhando o comportamento de "SpatialUnderstanding" chama InitScan e, em seguida, UpdateScan cada quadro. Quando a consulta de estatísticas relata a cobertura razoável, o usuário tem permissão para airtap chamar RequestFinish para indicar o final da fase de verificação. UpdateScan continua a ser chamada até que ele é retornado o valor indica que a dll foi concluído o processamento.

### <a name="understanding-mesh"></a>Noções básicas sobre malha

A dll de Noções básicas sobre armazena internamente o playspace como uma grade de cubos de voxel 8cm em tamanho. Durante a parte inicial da verificação, uma análise de componente principal é concluída para determinar os eixos da sala. Internamente, ele armazena seu espaço de voxel alinhado com esses eixos. Uma malha é gerada aproximadamente a cada segundo por meio da extração do isosurface do volume voxel. 

![Malha gerada produzida a partir do volume voxel](images/su-custommesh.jpg)<br>
*Malha gerada produzida a partir do volume voxel*

## <a name="troubleshooting"></a>Solução de problemas
* Verifique se você tiver definido o [SpatialPerception](#setting-the-spatialperception-capability) capacidade
* Quando o controle for perdido, o próximo evento OnSurfaceChanged removerá todas as malhas.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mapeamento espacial no Kit de ferramentas de realidade misturada
Para obter mais informações sobre como usar o mapeamento espacial com o Kit de ferramentas de realidade misturada v2, consulte o <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">seção reconhecimento espacial</a> do docs MRTK.

## <a name="see-also"></a>Consulte também
* [MR Spatial 230: Mapeamento espacial](holograms-230.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Sistemas de coordenadas no Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>

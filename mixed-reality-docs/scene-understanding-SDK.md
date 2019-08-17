---
title: SDK de compreensão da cena
description: Guia de programação para o SDK de compreensão da cena
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: Compreensão da cena, mapeamento espacial, realidade do Windows Mixed, Unity
ms.openlocfilehash: 152ffdbd84798c164963717a8dc41beb2e1a0902
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559857"
---
## <a name="scene-understanding-sdk-overview"></a>Visão geral do SDK de compreensão da cena

A meta da compreensão da cena é transformar os dados do sensor de ambiente não estruturado que o dispositivo da realidade misturada captura e convertê-lo em uma representação avançada, mas abstrata, intuitiva e fácil de desenvolver para o. O SDK atua como a camada de comunicação entre seu aplicativo e o tempo de execução de compreensão da cena. Ele é destinado a imitar construções padrão existentes, como grafos de cena 3D para representações 3D e retângulos/painéis 2D para aplicativos 2D. Embora as construções que compreendem as imitações da cena sejam mapeadas para as estruturas concretas que você pode usar, em geral SceneUnderstanding é a estrutura independente, permitindo a interoperabilidade entre estruturas variadas que interagem com ela. Conforme a compreensão da cena desenvolve a função do SDK, para garantir que novas representações e funcionalidades continuem a ser expostas em uma estrutura unificada. Neste documento, primeiro apresentaremos conceitos de alto nível que ajudarão você a se familiarizar com o uso/ambiente de desenvolvimento e, em seguida, fornecer uma documentação mais detalhada para classes e construções específicas.

## <a name="where-do-i-get-the-sdk"></a>Onde obtenho o SDK?

O SDK do SceneUnderstanding é baixável via NuGet.

[SDK do SceneUnderstanding](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

Antes de começar, observe que o SDK é executado na parte superior do UWP e requer SDK do Windows versão 18362 ou superior. 

### <a name="the-scene"></a>A cena

Seu dispositivo de realidade misturada está constantemente integrando informações sobre o que vê em seu ambiente. A compreensão da cena funil todas essas fontes de dados e produz uma única abstração coesa. A compreensão da cena gera cenas que são uma composição de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representam uma instância de uma única coisa (por exemplo, uma parede/teto/andar). Os próprios objetos de cena são uma composição de [SceneComponents](scene-understanding-SDK.md#scenecomponents) que representam partes mais granulares que compõem esse sceneobject. Exemplos de componentes são quádruplos e malhas, mas no futuro poderiam representar caixas delimitadoras, mehses de colisão, metadados, etc...

O processo de converter os dados brutos do sensor em uma cena é uma operação potencialmente cara que pode levar segundos para espaços médios (~ 10x10m) a minutos para espaços muito grandes (~ 50x50m) e, portanto, não é algo que está sendo computado pelo dispositivo sem solicitação de aplicativo. Em vez disso, a geração de cena é disparada por seu aplicativo sob demanda. A classe SceneObserver tem métodos estáticos que podem calcular ou desserializar uma cena, com a qual você pode enumerar/interagir. A ação de "computação" é executada sob demanda e é executada na CPU, mas em um processo separado (o driver de realidade misturada). No entanto, enquanto fazemos a computação em outro processo, os dados de cena resultantes são armazenados e mantidos em seu aplicativo no objeto de cena. 

Veja abaixo um diagrama que ilustra esse fluxo de processo e mostra exemplos de dois aplicativos que se destinam ao tempo de execução de compreensão da cena. 

![Diagrama de processo](images/SU-ProcessFlow.png)

No lado esquerdo, há um diagrama do tempo de execução misto da realidade que está sempre ligado e em execução em seu próprio processo. Esse tempo de execução é responsável por executar o rastreamento de dispositivos, a reconstrução da superfície e outras operações que a cena entende para entender e o motivo do mundo em torno de você. No lado direito do diagrama, mostramos dois aplicativos teóricos que fazem uso da compreensão da cena. As primeiras interfaces de aplicativo com MRTK que usam o SDK de compreensão da cena internamente, o segundo aplicativo computa e usa duas instâncias de cena sepereate. Todos os 3 bastidores neste diagrama geram instâncias distintas dos bastidores, o driver não está acompanhando o estado global que é compartilhado entre aplicativos e objetos de cena em uma cena não é encontrado em outro. A compreensão da cena fornece um mecanismo para controlar ao longo do tempo, mas isso é feito usando o SDK e o código que executa esse controle é executado no SDK no processo do aplicativo.

Como cada cena armazena os dados no espaço de memória do seu aplicativo, você pode pressupor que toda a função do objeto de cena ou de seus dados internos sempre seja executada no processo do aplicativo.

#### <a name="layout"></a>Layout

Para trabalhar com a compreensão da cena, pode ser importante saber e entender como o tempo de execução representa os componentes logicamente e fisicamente. A cena representa dados com um layout específico que foi escolhido para ser simples enquanto mantém uma estrutura subjacente que é pliable para atender aos requisitos futuros sem precisar de revisões principais. A cena faz isso armazenando todos os componentes (blocos de construção para todos os objetos de cena) em uma lista simples e definindo a hierarquia e a composição por meio de referências em que componentes específicos fazem referência a outros.

Abaixo, apresentamos um exemplo de uma estrutura em sua forma fixa e lógica.

<table>
<tr><th>Layout lógico</th><th>Layout físico</th></tr>
<tr>
<td>
<ul>
  Cena
  <ul>
  <li>SceneObject_1
    <ul>
      <li>Mesh_1</li>
      <li>Quad_1</li>
      <li>Quad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>Quad_1</li>
      <li>Quad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>Mesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>Quad_1</li>
  <li>Quad_2</li>
  <li>Quad_3</li>
  <li>Mesh_1</li>
  <li>Mesh_2</li>
</ul>
</td>
</tr>
</table>

Esta ilustração realça a diferença entre o layout lógico e físico da cena. À direita, vemos o layout hierárquico dos dados que seu aplicativo vê ao enumerar a cena. À esquerda, vemos que a cena é realmente composta de 12 componentes distintos acessíveis individualmente, se necessário. Ao processar uma nova cena, esperamos que os aplicativos orientem essa hierarquia logicamente, no entanto, ao controlar entre as atualizações de cena, alguns aplicativos só podem estar interessados em direcionar componentes específicos que são compartilhados entre duas cenas.

### <a name="high-level-overview"></a>Visão geral de alto nível

A seção a seguir fornece uma visão geral de alto nível das construções na compreensão da cena. A leitura desta seção lhe dará uma compreensão de como as cenas são representadas e de quais os vários componentes do/são usados. A próxima seção fornecerá exemplos de código concretos e detalhes adicionais que são brilhantes nesta visão geral.

#### <a name="scenecomponents"></a>SceneComponents

Agora que você entende o layout lógico de cenas, agora podemos apresentar o conceito de SceneComponents e como eles são usados para compor a hierarquia. SceneComponents são as decomposiçãos mais granulares em SceneUnderstanding que representam uma única coisa principal, por exemplo, uma malha ou uma caixa delimitadora ou quádrupla. SceneComponents são coisas que podem ser atualizadas de forma independente e podem ser referenciadas por outras SceneComponents, portanto, elas têm uma única propriedade global uma ID exclusiva, que permite esse tipo de mecanismo de controle/referência. As IDs são usadas para a composição lógica da hierarquia de cena, bem como a persistência de objeto (o ato de atualizar uma cena em relação a outra). 

Se você estiver tratando cada cena recém calculada como distinta e simplesmente enumerando todos os dados dentro dela, as IDs serão amplamente transparentes para você. No entanto, se você estiver planejando rastrear componentes em várias atualizações, usará as IDs para indexar e localizar SceneComponents entre objetos de cena.

#### <a name="sceneobjects"></a>SceneObjects

Um Sceneobject é um SceneComponent que representa uma instância de uma "coisa", por exemplo, uma parede, um andar, um teto, etc... expresso por sua propriedade Kind. SceneObjects são geométricos e, portanto, têm funções e propriedades que representam sua localização no espaço, no entanto, elas não contêm nenhuma estrutura geométrica ou lógica. Em vez disso, SceneObjects referenciam outros SceneComponents, especificamente SceneQuads e SceneMeshes, que fornecem as representações variadas que são suportadas pelo sistema. Quando uma nova cena é computada, seu aplicativo provavelmente irá enumerar o SceneObjects da cena para processar o que está interessado.

SceneObjects pode ter qualquer um dos seguintes:

<table>
<tr>
<th>SceneObjectKind</th> <th>Descrição</th>
</tr>
<tr><td>Informações preliminares</td><td>O Sceneobject é conhecido como <b>não</b> um dos outros tipos reconhecidos de objeto de cena. Essa classe não deve ser confundida quando o plano de fundo não for conhecido como parede/piso/teto, etc... Embora desconhecido ainda não esteja categorizado.</b></td></tr>
<tr><td>Meu</td><td>Uma parede física. As paredes são presumidas como estruturas ambientais immovíveis.</td></tr>
<tr><td>Floor</td><td>Os andares são quaisquer superfícies nas quais um pode ser movimentado. Observação: escadas não são andares. Observe também que os andares assumem qualquer superfície que seja orientada e, portanto, não há nenhuma suposição explícita de um piso singular. Estruturas de vários níveis, rampas, etc... todos devem ser classificados como piso.</td></tr>
<tr><td>Limite</td><td>A superfície superior de uma sala.</td></tr>
<tr><td>Plataforma</td><td>Uma grande superfície plana na qual você pode posicionar os hologramas. Elas tendem a representar tabelas, Intertops e outras superfícies horizontais grandes.</td></tr>
<tr><td>World</td><td>Um rótulo reservado para dados geométricos que são independentes de rotulagem. A malha gerada pela configuração do sinalizador de atualização EnableWorldMesh seria classificada como mundo.</td></tr>
<tr><td>Unknown</td><td>Este objeto de cena ainda deve ser classificado e atribuído a um tipo. Isso não deve ser confundido com o plano de fundo, pois esse objeto pode ser qualquer coisa, o sistema simplesmente não surgiu com uma classificação suficientemente forte para ele.</td></tr>
</tr>
</table>

#### <a name="scenemesh"></a>SceneMesh

Um SceneMesh é um SceneComponent que aproxima a geometria de objetos geométricos arbitrários usando uma lista de triângulos. SceneMeshes são usados em vários contextos diferentes, eles podem representar componentes da estrutura de célula Watertight ou como WorldMesh, que representa a reconstrução de superfície não associada associada à cena. Os dados de índice e vértice fornecidos com cada malha usam o mesmo layout familiar que os buffers de [vértice e de índice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) usados para renderizar malhas de triângulo em todas as APIs de renderização modernas. Observe que, na compreensão da cena, as malhas usam índices de 32 bits e talvez precisem ser divididas em partes para determinados mecanismos de renderização.

#### <a name="scenequad"></a>SceneQuad

Um SceneQuad é um SceneComponent que representa superfícies 2D que ocupam o mundo 3D. SceneQuads pode ser usado de forma semelhante aos planos ARKit ARPlaneAnchor ou ARCore, mas eles oferecem funcionalidade de nível mais alto como telas 2D a serem usadas por aplicativos simples, ou UX aumentada. as APIs específicas de 2D são fornecidas para quatro processadores que tornam o posicionamento e o layout simples de usar, e o desenvolvimento (com exceção de renderização) com quádruplos deve se sentir mais parecido com o trabalho com telas 2D do que com malhas 3D.

### <a name="scene-understanding-sdk-details-and-reference"></a>Detalhes do SDK de compreensão da cena e referência

#### <a name="sdk"></a>SDK

A seção a seguir ajudará você a se familiarizar com os conceitos básicos do SceneUnderstanding. Esta seção deve fornecer as noções básicas, em que ponto você deve ter contexto suficiente para navegar pelos aplicativos de exemplo para ver como o SceneUnderstanding é usado de forma holística.

#### <a name="initialization"></a>Inicialização

A primeira etapa para trabalhar com SceneUnderstanding é para seu aplicativo obter referência a um objeto de cena. Isso pode ser feito de duas maneiras, uma cena pode ser computada pelo driver ou uma cena existente que foi computada no passado pode ser desserializada. O último é particularmente útil para trabalhar com SceneUnderstanding durante o desenvolvimento, em que aplicativos e experiências podem ser protótipos rapidamente sem um dispositivo de realidade misturada.

As cenas são computadas usando um SceneObserver. Antes de criar uma cena, seu aplicativo deve consultar seu dispositivo para garantir que ele dê suporte a SceneUnderstanding, bem como solicitar acesso de usuário para obter informações de que o SceneUnderstanding precisa.

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Se RequestAccessAsync () não for chamado, a computação de uma nova cena falhará. Em seguida, computaremos uma nova cena com raiz em relação ao headset da realidade misturada e que tem um raio de 10 medidores.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.Compute(querySettings, 10.0f);
```

#### <a name="initialization-from-data-aka-the-pc-path"></a>Inicialização a partir de dados (também conhecido como. o caminho do PC)

Embora as cenas possam ser computadas para consumo direto, elas também podem ser computadas em formato serializado para uso posterior. Isso provou ser muito útil para o desenvolvimento, pois permite que os desenvolvedores trabalhem e testem a compreensão da cena sem a necessidade de um dispositivo. O ato de serializar uma cena é quase idêntico a computar a ti, os dados são retornados ao seu aplicativo em vez de serem desserializados localmente pelo SDK. Você pode desserializá-lo por conta própria ou salvá-lo para uso futuro.

```cs
// Create Query settings for the scene update
SceneUnderstanding.QuerySettings querySettings;

// Compute a scene but serialized as a byte array
byte[] newSceneBlob = SceneObserver.ComputeSerialized(querySettings, 10.0f);

// If we want to use it immediatley we can de-serialize the scene ourselves
Scene mySceneDeSerialized = Scene.Deserialize(newSceneBlob);

// Save newSceneBlob for later
```

#### <a name="sceneobject-enumeration"></a>Enumeração de sceneobject

Agora que seu aplicativo tem uma cena, seu aplicativo irá examinar e interagir com o SceneObjects. Isso é feito acessando a propriedade **SceneObjects** :

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

#### <a name="component-update-and-re-finding-components"></a>Atualização de componente e redescoberta de componentes

Há outra função que recupera componentes na cena chamada ***FindComponent***. Essa função é útil ao atualizar objetos de acompanhamento e localizá-los em cenas subsequentes. O código a seguir calculará uma nova cena em relação a uma cena anterior e, em seguida, encontrará o andar na nova cena.

```cs
// Compute a new scene, but tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.Compute(querySettings, 10.0f, myScene);

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attatched to this floor transform
}
```

### <a name="accessing-meshes-and-quads-from-scene-objects"></a>Acessando malhas e quatros de objetos de cena

Depois que SceneObjects tiver sido localizado, o aplicativo provavelmente desejará acessar os dados contidos em n os quatro quádruplos/malhas dos quais ele é composto. Esses dados são acessados com as propriedades de quádruplas e de ***malhas*** . O código a seguir enumerará todos os quádruplos e malhas do nosso objeto Floor.

```cs

// Get the matrix for the SceneObject
System.Numerics.Matrix4x4 floorTransform = firstFloor.LocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Observe que é o Sceneobject que tem a transformação relativa à origem da cena. Isso ocorre porque o Sceneobject representa uma instância de "coisa" e é localizável no espaço, as quádruplas e as malhas representam a geometria transformada em relação ao seu pai. É possível que SceneObjects separadas referenciem o mesmo SceneMesh/SceneQuad SceneComponewnts, e também é possível que um Sceneobject tenha mais de um SceneMesh/SceneQuad.

### <a name="dealing-with-transforms"></a>Lidando com transformações

A compreensão da cena fez uma tentativa deliberada de se alinhar com as representações tradicionais de cena 3D ao lidar com transformações. Portanto, cada cena é confinada a um único sistema de coordenadas, assim como as representações de ambiente 3D mais comuns. Se seu aplicativo estiver lidando com cenas que ampliam o limite do que uma única origem fornece, ela pode ancorar SceneObjects para SpatialAnchors ou gerar várias cenas e mesclá-las, mas para simplificar, vamos supor que as cenas de Watertight existam por conta própria origem localizada por um NodeId definido por Scene:: OriginSpatialGraphNodeId.

O seguinte código de Unity, por exemplo, mostra como usar a percepção do Windows e as APIs do Unity para alinhar os sistemas de coordenadas em conjunto:


```cs
    public static System.Numerics.Matrix4x4? GetSceneToUnityTransform(Guid nodeId)
    {
        System.Numerics.Matrix4x4? sceneToUnityTransform; 
       
        SpatialCoordinateSystem sceneSpatialCoordinateSystem = Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(nodeId);
        SpatialCoordinateSystem unitySpatialCoordinateSystem = (SpatialCoordinateSystem)System.Runtime.InteropServices.Marshal.GetObjectForIUnknown(UnityEngine.XR.WSA.WorldManager.GetNativeISpatialCoordinateSystemPtr());

        sceneToUnityTransform = sceneSpatialCoordinateSystem.TryGetTransformTo(unitySpatialCoordinateSystem);

        if (sceneToUnityTransform != null)
        {
            sceneToUnityTransform = TransformUtils.ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
        }
        
        return sceneToUnityTransform;
    }

    /// <summary>
    /// Converts a transformation matrix from right handed (+x is right, +y is up, +z is back) to left handed (+x is right, +y is up, +z is front).
    /// </summary>
    /// <param name="transformationMatrix">Right-handed transformation matrix to convert.</param>
    /// <returns>Converted left-handed matrix.</returns>
    public System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 transformationMatrix)
    {
        transformationMatrix.M13 = -transformationMatrix.M13;
        transformationMatrix.M23 = -transformationMatrix.M23;
        transformationMatrix.M43 = -transformationMatrix.M43;

        transformationMatrix.M31 = -transformationMatrix.M31;
        transformationMatrix.M32 = -transformationMatrix.M32;
        transformationMatrix.M34 = -transformationMatrix.M34;

        return transformationMatrix;
    }
```

E o código a seguir chama essa função:

```cs
System.Numerics.Matrix4x4? sceneToUnityTransform = TransformUtils.GetSceneToUnityTransform(scene.OriginSpatialGraphNodeId);

// Set the root transform
Vector3 t;
Quaternion r;
Vector3 s;

System.Numerics.Matrix4x4.Decompose(sceneToUnityTransform, out s, out r, out t);
SceneRoot.Transform.SetPositionAndRotation(t, r);
```

### <a name="quad"></a>Quadra

Os quatro processadores foram projetados para facilitar os cenários de posicionamento de 2D e devem ser considerados como extensões para elementos de UX de tela 2D. Embora os quatro processadores sejam componentes de SceneObjects e possam ser renderizados em 3D, as APIs quádruplas em si pressupõem que as quatro são estruturas 2D. Eles oferecem informações como extensão, forma e fornecem APIs para posicionamento.

Os quatro processadores têm extensões retangulares, mas representam superfícies 2D com formato arbitrário. Para habilitar o posicionamento nessas superfícies 2D que interagem com o ambiente 3D, as quatro ofertas oferecem utilitários para tornar essa interação possível. Atualmente, a compreensão da cena fornece duas funções desse tipo, **FindCentermostPlacement** e **GetOcclusionMask**. FindCentermostPlacement é uma API de alto nível que localiza uma posição no Quad em que um objeto pode ser colocado e tentará encontrar o melhor local para seu objeto, garantindo que a caixa delimitadora que você fornece residirá na superfície subjacente.

O exemplo a seguir mostra como localizar o local centermost posicionável e ancorar um holograma para o quad.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new node QuadTransformNode as a child of Root, and set the transform from quad[0].Transform
                // Step 2: Create your hologram and set it as a child of QuadTransformNode
                // Step 3: Set the QuadTransformNode tranform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

As etapas 1-3 são altamente dependentes de sua estrutura/implementação específica, mas os temas devem ser semelhantes. É importante observar que o quad normalmente não se destina a ser, representa apenas um plano 2D limitado que é localizado no espaço. Tendo seu mecanismo/estrutura sabendo onde o Quad é e criando a raiz de seus objetos em relação ao Quad, seus hologramas estarão localizados corretamente. Para obter informações mais detalhadas, consulte nossos exemplos em quatro processadores que mostram implementações específicas.

### <a name="mesh"></a>Integrada

As malhas representam representações geométricas de objetos ou ambientes. Assim como o [mapeamento espacial](spatial-mapping.md), o índice de malha e os dados de vértice fornecidos com cada malha de superfície espacial usam o mesmo layout familiar que os buffers de vértice e de índice usados para renderizar malhas de triângulo em todas as APIs de renderização modernas. As APIs específicas usadas para fazer referência a esses dados são as seguintes:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(float[] vertices);
```

\* * Observação: Getvértices retorna uma lista de vértices onde cada 3 tupla de valores de ponto flutuante representa uma única coordenada em espaço cartesiano x, y e z.

O código a seguir fornece um exemplo de como gerar uma lista de triângulos a partir da estrutura de malha:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
float[] positions = new float[mesh.VertexCount * 3];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Os buffers de índice/vértice devem ser > = as contagens de índice/vértice, mas, caso contrário, podem ser arbitrariamente dimensionados permitindo uma reutilização de memória eficiente.

### <a name="developing-with-scene-understandings"></a>Desenvolvendo com entendimentos em cena

Neste ponto, você deve entender os principais blocos de construção da cena que compreendem o tempo de execução e o SDK. A maior parte do poder e da complexidade está em padrões de acesso, interação com estruturas 3D e ferramentas que podem ser escritas sobre essas APIs para executar tarefas mais avançadas como planejamento espacial, análise de sala, navegação, física, etc... Esperamos capturá-los em exemplos que esperamos orientá-lo na direção correta para fazer seus cenários brilharem. Se houver amostras/cenários que não estão sendo abordados, informe-nos e tentaremos documentar/criar um protótipo do que você precisa.

## <a name="see-also"></a>Consulte também

* [mapeamento espacial](spatial-mapping.md)

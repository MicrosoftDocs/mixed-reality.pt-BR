---
title: Estudo de caso - expandindo os recursos de mapeamento espacial do HoloLens
description: Ao criar nossos primeiros aplicativos para o Microsoft HoloLens, estávamos ansiosos para ver o quanto estamos pode ultrapassar os limites do mapeamento espacial no dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Mapeamento espacial do Windows Mixed Reality, HoloLens,
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590504"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Estudo de caso - expandindo os recursos de mapeamento espacial do HoloLens

Ao criar nossos primeiros aplicativos para o Microsoft HoloLens, estávamos ansiosos para ver o quanto estamos pode ultrapassar os limites do mapeamento espacial no dispositivo. Jeff Evertt, engenheiro de software da Microsoft Studios, explica como uma nova tecnologia foi desenvolvida sem a necessidade de mais controle sobre como hologramas são colocadas em um ambiente de usuário reais.

## <a name="watch-the-video"></a>Assista ao vídeo

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Além do mapeamento espacial

Enquanto que estávamos trabalhando [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8) e [Conker Young](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), dois dos jogos de primeira para HoloLens, descobrimos que, quando estávamos fazendo procedural posicionamento de hologramas no mundo físico, é necessário um nível mais alto compreensão sobre o ambiente do usuário. Cada jogo tinha suas próprias necessidades de posicionamento específico: Em fragmentos, por exemplo, queremos ser capaz de distinguir entre diferentes superfícies — como o chão ou uma tabela — para colocar pistas em localizações relevantes. Também queremos ser capaz de identificar as superfícies que caracteres holográfica life-size poderia ficar, como um sofá ou uma cadeira. Conker Young, queríamos Conker e seus adversários para poder usar superfícies geradas na sala de um jogador como plataformas.

[Asobo estúdios](http://www.asobostudio.com/index.html), nossos parceiros de desenvolvimento para esses jogos, enfrentam esse problema frente e criado uma tecnologia que estende os recursos de mapeamento espacial do HoloLens. Usando isso, poderíamos analisar sala de um jogador e identificar as superfícies, como tabelas, paredes, cadeiras e andares. Ela também nos proporcionou a capacidade de otimizar em relação a um conjunto de restrições para determinar a melhor disposição dos objetos holographic.

## <a name="the-spatial-understanding-code"></a>O código de compreensão espacial

Podemos levou o código original do Asobo e criou uma biblioteca que encapsula a essa tecnologia. Microsoft e Asobo agora têm esse código de software livre e disponibilizados no [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) para uso em seus próprios projetos. O código-fonte está incluído, permitindo que você personalizá-lo às suas necessidades e compartilhar suas melhorias com a comunidade. O código para o C++ solver foi encapsulado em uma DLL UWP e exposto a Unity com um [pré-fabricado para soltar contido MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).

Há muitas consultas úteis incluídas no exemplo Unity que permitirá que você encontre espaços vazios em paredes, colocar objetos no limite máximo ou em grandes espaços no chão, identificar locais em busca de caracteres para ficar e uma grande variedade de outras consultas espaciais compreensão.

Enquanto a solução de mapeamento espacial fornecida pelo HoloLens é projetada para ser genérico o suficiente para atender às necessidades de toda a gama de problemas de espaço, o módulo de compreensão espacial foi criado para suportar as necessidades de dois jogos específicos. Assim, sua solução é estruturada em torno de um processo específico e um conjunto de suposições:
* **Corrigido tamanho playspace**: O usuário Especifica o tamanho máximo playspace na chamada de inicialização.
* **O processo de verificação única**: O processo requer um discretos fase em que os usuários se deslocam em torno de varredura, definindo o playspace. Funções de consulta não funcionará até depois que a verificação tiver sido finalizada.
* **Usuário controlado por playspace "pintura"**: Durante a fase de verificação, o usuário move e procura ao redor de playspace, pintura com eficiência as áreas que devem ser incluídas. A malha gerada é importante fornecer comentários do usuário durante essa fase.
* **Em locais fechados instalação de casa ou escritório**: As funções de consulta são projetadas em torno de superfícies simples e paredes ângulos retos. Essa é uma limitação suave. No entanto, durante a fase de verificação, uma análise de eixo primário é concluída para otimizar o mosaico de malha ao longo do eixo principal e secundário.

### <a name="room-scanning-process"></a>Processo de verificação de espaço

Quando você carrega o módulo de compreensão espacial, a primeira coisa a fazer é verificar o seu espaço, portanto, todas as superfícies utilizáveis — como o floor, ceiling e paredes — são identificados e rotulados. Durante o processo de digitalização, poderá olhar em volta de sua sala e "pintura ' as áreas que devem ser incluídas na verificação.

A malha Vista durante essa fase é uma parte importante de feedback visual que permite que os usuários saber quais partes da sala estão sendo examinados. A DLL para o módulo de compreensão espacial armazena internamente o playspace como uma grade de cubos de voxel 8cm em tamanho. Durante a parte inicial da verificação, uma análise de componente principal é concluída para determinar os eixos da sala. Internamente, ele armazena seu espaço de voxel alinhado com esses eixos. Uma malha é gerada aproximadamente a cada segundo por meio da extração do isosurface do volume voxel.

![Mapeamento de malha em branco e Noções básicas sobre playspace espacial de malha em verde](images/spatial-mapping-500px.png)

Mapeamento de malha em branco e Noções básicas sobre playspace espacial de malha em verde



O arquivo SpatialUnderstanding.cs incluído gerencia o processo de fase de verificação. Ele chama as funções a seguir:
* **SpatialUnderstanding_Init**: Chamado uma vez no início.
* **GeneratePlayspace_InitScan**: Indica que a fase de verificação deve começar.
* **GeneratePlayspace_UpdateScan_DynamicScan**: Chamado a cada quadro para o processo de verificação de atualização. A posição da câmera e a orientação é passado e é usado para o processo de pintura playspace, descrito acima.
* **GeneratePlayspace_RequestFinish**: Chamado para finalizar o playspace. As áreas "pintadas" durante a fase de verificação serão usadas para definir e bloquear o playspace. O aplicativo pode consultar as estatísticas durante a verificação fase, bem como a consulta a malha personalizada para fornecer comentários do usuário.
* **Import_UnderstandingMesh**: Durante a verificação, o **SpatialUnderstandingCustomMesh** comportamento fornecido pelo módulo e colocado no pré-fabricado Noções básicas sobre periodicamente consultará a malha personalizada gerada pelo processo. Além disso, isso é feito mais uma vez após a verificação tiver sido finalizada.

O fluxo de varredura, orientado pelo **SpatialUnderstanding** chamadas do comportamento **InitScan**, em seguida, **UpdateScan** cada quadro. Quando a consulta de estatísticas relata a cobertura razoável, o usuário pode airtap chamar **RequestFinish** para indicar o final da fase de verificação. **UpdateScan** continua a ser chamada até que ele é retornado o valor indica que a DLL foi concluído o processamento.

## <a name="the-queries"></a>As consultas

Depois que a verificação for concluída, você poderá acessar os três tipos diferentes de consultas na interface:
* **Consultas de topologia**: Essas são consultas rápidas com base na topologia da sala digitalizada.
* **Consultas de forma**: Eles utilizam os resultados de suas consultas de topologia para localizar as superfícies horizontais que são uma boa correspondência para formas personalizadas que você definir.
* **Consultas de posicionamento de objeto**: Essas são as consultas mais complexas que encontrar o local de fallback de melhor ajuste com base em um conjunto de regras e restrições para o objeto.

Além das três consultas primárias, há uma interface de raycasting, que pode ser usada para recuperar tipos de superfície com marcas de formatação e uma malha de sala watertight personalizados pode ser copiada-out.

### <a name="topology-queries"></a>Consultas de topologia

Dentro da DLL, o Gerenciador de topologia manipula a rotulagem do ambiente. Conforme mencionado acima, muitos dos dados é armazenado em surfels, que estão contidos dentro de um volume voxel. Além disso, o **PlaySpaceInfos** estrutura é usada para armazenar informações sobre o playspace, incluindo o alinhamento do mundo (para obter mais detalhes sobre isso abaixo), andar e altura de teto.

Heurística é usada para determinar as paredes, ceiling e floor. Por exemplo, a superfície maior e menor horizontal com maior que 1 área da superfície m2 é considerada o chão. Observe que o caminho de câmera durante o processo de verificação também é usado neste processo.

Um subconjunto de consultas expostas pelo Gerenciador de topologia são expostos por meio da DLL. As consultas de topologia expostos são da seguinte maneira:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Cada uma das consultas tem um conjunto de parâmetros, específicos para o tipo de consulta. No exemplo a seguir, o usuário Especifica a altura mínima & largura do volume desejado, a altura mínima de posicionamento acima do chão e a quantidade mínima de espaço livre na frente do volume. Todas as medidas são em metros.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada uma dessas consultas usarão uma matriz alocada previamente de **TopologyResult** estruturas. O **locationCount** parâmetro especifica o comprimento da matriz passada. O valor de retorno relata o número de locais retornados. Esse número nunca é maior que passado **locationCount** parâmetro.

O **TopologyResult** contém a posição do centro do volume retornado, a direção oposta (ou seja, normal) e as dimensões do espaço encontrado.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Observe que a amostra do Unity, cada uma dessas consultas é vinculada a um botão no painel de interface do usuário virtual. O disco rígido do exemplo codifica os parâmetros para cada uma dessas consultas para valores razoáveis. Ver *SpaceVisualizer.cs* no código de exemplo para obter mais exemplos.

### <a name="shape-queries"></a>Consultas de forma

Dentro de DLL, o analisador de forma (**ShapeAnalyzer_W**) usa o analisador de topologia para correspondência com formas personalizadas definidas pelo usuário. A amostra do Unity tem um conjunto predefinido de formas que são mostrados no menu de consulta, na guia de forma.

Observe que a análise de forma funciona em superfícies horizontais apenas. Por exemplo, um sofá, é definido, a superfície de estação simples e simples parte superior do sofá novamente. A consulta de forma procura duas superfícies de um intervalo de tamanho, altura e os aspectos específico, com as superfícies de dois alinhada e conectado. Com a terminologia de APIs, o assento sofá e a parte superior da parte traseira do sofá são forma de componentes e o alinhamento de requisitos são as restrições de componentes de forma.

Um exemplo de consulta definido no exemplo Unity (**ShapeDefinition.cs**), para objetos "sittable" é o seguinte:




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

Cada consulta de forma é definida por um conjunto de componentes de forma, cada um com um conjunto de restrições de componente e um conjunto de restrições de forma que lista as dependências entre os componentes. Este exemplo inclui três restrições na definição de um único componente e sem restrições de forma entre os componentes (como há apenas um componente).

Por outro lado, a forma de sofá tem dois componentes de forma e quatro restrições de forma. Observe que os componentes são identificados por seu índice na lista de componentes do usuário (0 e 1 neste exemplo).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Funções de wrapper são fornecidas no módulo do Unity para facilitar a criação de definições de forma personalizada. A lista completa de restrições de componente e forma pode ser encontrada no **SpatialUnderstandingDll.cs** dentro de **ShapeComponentConstraint** e o **ShapeConstraint** estruturas.

![O retângulo azul realça os resultados da consulta shape cadeira.](images/chair-shape-query-500px.png)

O retângulo azul realça os resultados da consulta shape cadeira.



### <a name="object-placement-solver"></a>Solucionador de posicionamento de objeto

Consultas de posicionamento de objeto podem ser usadas para identificar locais ideais na sala de físico para colocar seus objetos. O solucionador encontrará o local de fallback de melhor ajuste dado as regras de objeto e restrições. Além disso, as consultas de objeto persistem até que o objeto for removido com **Solver_RemoveObject** ou **Solver_RemoveAllObjects** restrita de chamadas, permitindo que o posicionamento de vários objeto.

Consultas de posicionamento de objeto consistem em três partes: o tipo de posicionamento com parâmetros, uma lista de regras e uma lista de restrições. Para executar uma consulta, use a seguinte API:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
Essa função usa um nome de objeto, definição de posicionamento e uma lista de regras e restrições. O C# wrappers funções auxiliares para facilitar a construção de restrição e regra de construção de fornecer. A definição de posicionamento contém o tipo de consulta — ou seja, um dos seguintes:




```
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

Cada um dos tipos de posicionamento tem um conjunto de parâmetros exclusivos para o tipo. O **ObjectPlacementDefinition** estrutura contém um conjunto de funções auxiliares estáticos para criar essas definições. Por exemplo, para encontrar um local para colocar um objeto no chão, você pode usar a função a seguir: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Além do tipo de posicionamento, você pode fornecer um conjunto de regras e restrições. As regras não podem ser violadas. Locais possíveis para posicionamento que satisfazem o tipo e as regras são otimizados, em seguida, em relação ao conjunto de restrições para selecionar o local ideal de posicionamento. Cada uma das regras e restrições pode ser criada pelas funções de criação estáticos fornecido. Uma função de construção de restrição e regra de exemplo é fornecida abaixo.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

A consulta de posicionamento de objeto abaixo está procurando um lugar para colocar um cubo de metade do medidor na borda de uma superfície, longe outros anteriormente colocar objetos e próximo ao centro da sala.




```
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

Se for bem-sucedido, uma **ObjectPlacementResult** estrutura que contém a posição de posicionamento, dimensões e orientação é retornada. Além disso, o posicionamento é adicionado à lista interna da DLL de objetos inseridos. Consultas subsequentes posicionamento levarão a esse objeto em conta. O **LevelSolver.cs** arquivo no exemplo Unity contém mais consultas de exemplo.

![As caixas azuis mostram o resultado de três consultas lugar no chão com regras de "fora de posição da câmera".](images/away-from-camera-position-500px.png)

As caixas azuis mostram o resultado de três consultas lugar no chão com regras de "fora de posição da câmera".


**Dicas:**
* Quando a solução para o local de posicionamento de vários objetos necessários para um cenário de nível ou do aplicativo, primeiro solucione objetos grandes e indispensáveis para maximizar a probabilidade de um espaço pode ser encontrado.
* Posicionamento de ordem é importante. Se os posicionamentos de objeto não for encontrados, tente configurações menos restritas. Ter um conjunto de configurações de fallback é essencial para dar suporte a funcionalidade em muitas configurações de espaço.

### <a name="ray-casting"></a>Ray conversão

Além das três principais consultas, uma interface de conversão de ray pode ser usada para recuperar tipos de superfície com marcas de formatação e uma malha playspace watertight personalizados pode ser copiada-out depois que a sala foi verificada e concluída, rótulos são gerados internamente para superfícies, como o Floor, ceiling e paredes. O **PlayspaceRaycast** função usa um raio e retorna se o raio entra em conflito com uma superfície conhecida e, nesse caso, informações sobre o que são exibidos na forma de uma **RaycastResult**. 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

Internamente, o raycast é calculado em relação a representação do playspace voxel do computada cm 8 ao cubo. Cada voxel contém um conjunto de elementos de superfície com os dados processados topologia (também conhecido como surfels). Os surfels contidos dentro da célula voxel interseccionadas são comparadas e a melhor correspondência usada para pesquisar as informações de topologia. Esses dados de topologia contém os rótulos retornados na forma do **SurfaceTypes** enum, bem como a área de superfície da superfície de interseccionada.

No exemplo de Unity, o cursor converte um raio a cada quadro. Em primeiro lugar, em relação a colisores do Unity; em segundo lugar, em relação a representação do mundo do módulo Noções básicas sobre; e por fim, em relação aos elementos da interface do usuário. Neste aplicativo, a interface do usuário obtém prioridade, em seguida, o resultado de compreensão e, finalmente, colisores do Unity. O **SurfaceType** é relatada como texto ao lado do cursor.

![Resultado de Raycast reporting interseção com o chão.](images/raycast-result-500px.jpg)

Resultado de Raycast reporting interseção com o chão.


## <a name="get-the-code"></a>Obter o código

O código-fonte aberto está disponível no [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity). Envie seus comentários sobre o [fóruns de desenvolvedores do HoloLens](https://forums.hololens.com/) se você usar o código em um projeto. Estamos ansiosos para ver o que fazer com ele!

## <a name="about-the-author"></a>Sobre o autor

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> é um líder de engenharia de software que já trabalharam nesse HoloLens desde o início, de incubação para experimentar o desenvolvimento. Antes de HoloLens, ele trabalhou na Xbox Kinect e do setor de jogos em uma ampla variedade de plataformas e jogos. Jeff é apaixonado por robótica, gráficos e coisas com luzes pisca-pisca que vão do aviso sonoro. Ele gosta de aprender coisas novas e trabalhando em software, hardware e particularmente no espaço de interseção entre os dois.</td>
</tr>
</table>



## <a name="see-also"></a>Consulte também
* [Mapeamento espacial](spatial-mapping.md)
* [Design de mapeamento espacial](spatial-mapping-design.md)
* [Visualização de verificação de espaço](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: Lições da linha de frente do desenvolvimento HoloLens](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)

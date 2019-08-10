---
title: Compreensão da cena
description: Introdução aos recursos de compreensão da cena para o HoloLens
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: Compreensão da cena, mapeamento espacial, realidade do Windows Mixed, Unity
ms.openlocfilehash: fc77126958c653cac2d82f02cceeed9a29bffdf4
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2019
ms.locfileid: "68941213"
---
# <a name="scene-understanding"></a>Compreensão da cena

A compreensão da cena fornece aos desenvolvedores de realidade misturada uma representação de ambiente estruturada e de alto nível, projetada para tornar o desenvolvimento de aplicativos com reconhecimento de ambiente intuitivo. O entendimento da cena faz isso combinando o poder dos tempos de execução de realidade misturada existentes, como o [mapeamento espacial](spatial-mapping.md) menos estruturado e altamente preciso, e novos tempos de execução orientados a ia. Ao combinar essas tecnologias, a compreensão da cena gera representações de ambientes 3D semelhantes aos que você pode ter usado em estruturas como Unity ou ARKit/ARCore. O ponto de entrada de compreensão da cena começa com um observador de cena, que é chamado pelo seu aplicativo para computar uma nova cena. Hoje, a tecnologia é capaz de gerar 3 categorias de objetos diferentes, mas relacionadas: malhas de ambiente Watertight simplificadas que inferem na estrutura de sala planar sem confusão, regiões de plano para posicionamento que chamamos de quatro e um instantâneo do [ malha de mapeamento espacial](spatial-mapping.md) que se alinha com os dados quádruplos/Watertight que fazemos.

![Malha de mapeamento espacial, superfícies de planar rotuladas, malha Watertight](images/SUScenarios.png)

Este documento destina-se a fornecer uma visão geral do cenário e esclarecer a relação que a cena compreende e o compartilhamento de mapeamento espacial. Para obter detalhes sobre como a compreensão da cena funciona e como desenvolvê-la, consulte a documentação [visão geral do SDK](scene-understanding-SDK.md) de compreensão da cena.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Compreensão da cena</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="common-usage-scenarios"></a>Cenários de uso comuns

![Ilustrações de cenários de uso de mapeamento espacial comum: Posicionamento, oclusão, física e navegação](images/sm-concepts-1000px.png)

Muitos dos principais cenários de aplicativos com reconhecimento de ambiente (posicionamento, oclusão, física etc...) são endereçáveis pelo mapeamento espacial e pela compreensão da cena, esta seção destaca essas diferenças. Uma diferença importante entre a compreensão da cena e o mapeamento espacial é uma compensação da precisão e da latência máximas até a estrutura e a simplicidade. Se seu aplicativo requer a menor latência possível e requer triângulos de malha somente você desejará acessar o mapeamento espacial diretamente, no entanto, se você estiver executando processamento de nível superior, poderá considerar mudar para o modelo de compreensão da cena como ele deve fornecer um superconjunto de funcionalidades. Observe também que, como a compreensão da cena fornece a malha de mapeamento espacial como parte de sua representação, você sempre terá acesso aos dados de mapeamento espacial mais completos e precisos possíveis.

 As seções a seguir revisitam os cenários principais de mapeamento espacial no contexto do SDK de compreensão da nova cena.

### <a name="placement"></a>Colocação

A compreensão da cena fornece novas construções projetadas especificamente para simplificar os cenários de posicionamento. Uma cena pode computar primitivos chamados SceneQuads, que descrevem superfícies planas nas quais os hologramas podem ser colocados. A SceneQuads foi projetada especificamente para posicionamento e descreve uma superfície 2D e fornece uma API para posicionamento nessa superfície. Anteriormente, ao usar a malha de triângulo para realizar o posicionamento, era necessário verificar todas as áreas do Quad e executar o preenchimento/pós-processamento de orifício para identificar bons locais para o posicionamento do objeto. Isso nem sempre é necessário com o quads, pois o tempo de execução da cena é capaz de inferir quais áreas do Quad que não foram verificadas e invalidar áreas do Quad que não fazem parte da superfície.

![SceneQuads com inferência desabilitada, capturando áreas de posicionamento para regiões digitalizadas.](images/SUQuads.png)
##### <a name="1-scenequads-with-inference-disabled-capturing-placement-areas-for-scanned-regions"></a>[1] "SceneQuads com inferência desabilitada, capturando áreas de posicionamento para regiões verificadas".

![Quatro processadores com inferência habilitada, o posicionamento não é mais limitado a áreas digitalizadas.](images/SUWatertight.png)
##### <a name="2-quads-with-inference-enabled-placement-is-no-longer-limited-to-scanned-areas"></a>[2] "quádruplos com inferência habilitada, o posicionamento não está mais limitado a áreas digitalizadas".

Se seu aplicativo pretende colocar hologramas 2D ou 3D em estruturas rígidas de seu ambiente, a simplicidade e a conveniência do SceneQuads para posicionamento é preferível a computar essas informações da malha de superfície. Para obter mais detalhes sobre este tópico, consulte a [referência do SDK de compreensão da cena](scene-understanding-SDK.md)

**Observação** Para o código herdado que depende da malha da superfície, uma cena pode ser computada que contém a saída de mapeamento espacial junto com SceneQuads, garantindo que quaisquer requisitos herdados para o posicionamento possam ser mantidos. Se a cena que entende os dados da malha não atender aos requisitos de latência do seu aplicativo, recomendamos que você continue a usar as APIs de mapeamento espacial documentadas aqui: [Posicionamento de mapeamento espacial](spatial-mapping.md#placement)

### <a name="occlusion"></a>Oclusão

O [mapeamento espacial oclusão](spatial-mapping.md#occlusion) permanece o modo menos latente de capturar o estado em tempo real do ambiente. Embora isso possa ser útil para fornecer oclusão em cenas altamente dinâmicas, talvez você queira considerar a compreensão da cena para o oclusão por vários motivos. Se você usar a malha de mapeamento espacial gerada pela compreensão da cena, poderá solicitar dados do mapeamento espacial que não seria armazenado no cache local e, portanto, não WDS disponível a você das APIs de percepção. Usar o mapeamento espacial para oclusão juntamente com malhas Watertight fornecerá valor adicional, especificamente a conclusão da estrutura de sala não verificada.

Se seus requisitos puderem tolerar a maior latência de compreensão da cena, os desenvolvedores de aplicativos devem considerar o uso da malha de compreensão Watertight da cena e, supostamente, a malha de mapeamento espacial em harmonia com representações planares. Isso forneceria um "melhor dos dois mundos", em que simplificava a Watertight oclusão é casado com uma geometria mais realista, fornecendo os mapas oclusão mais realistas possíveis.

### <a name="physics"></a>Professor

A compreensão da cena gera malhas Watertight que decompõem o espaço com a semântica especificamente para lidar com muitas limitações na física que as malhas de superfície impõem. As estruturas Watertight garantem que as conversões de raio de física sejam sempre pressionadas, e a decomposição semântica permite uma geração mais simples de malhas de NAV para navegação em interno. Conforme descrito na seção em [oclusão](#occlusion) , a criação de uma cena com EnableSceneObjectMeshes e EnableWorldMesh produzirá a malha de conclusão mais física possível. A propriedade Watertight da malha do ambiente impedirá que testes de colisão falhem em superfícies e os dados de malha assegurarão que a física esteja interagindo com todos os objetos da cena e não apenas com a estrutura de sala.

### <a name="navigation"></a>Navegação

As malhas de planar decomposta por classe semântica são construções ideais para navegação e planejamento de caminho, facilitando muitos dos problemas descritos na visão geral de [navegação de mapeamento espacial](spatial-mapping.md#navigation) . Os objetos SceneMesh computados na cena já são descompostos por tipo de superfície, garantindo que a geração de malha de NAV seja limitada a superfícies que podem ser percorridos. Devido à simplicidade da estrutura de piso, a geração de malha de navegação dinâmica em mecanismos 3D, como o Unity, é atingível dependendo dos requisitos em tempo real.

A geração de malhas de navegação precisas ainda requer pós-processamento, ou seja, os aplicativos ainda precisam projetar occluders no chão para garantir que a navegação não passe por resíduos/tabelas etc... A maneira mais precisa de fazer isso é projetar os dados de malha mundial que serão fornecidos se a cena for computada com o sinalizador EnableWorldMesh.

### <a name="visualization"></a>Visualização

Embora a [visualização de mapeamento espacial](spatial-mapping.md#visualization) possa ser usada para comentários em tempo real do ambiente, há muitos cenários em que a simplicidade dos objetos planar e Watertight fornece mais desempenho ou qualidade visual. A projeção de sombra e técnicas de aterramento que são descritas usando o mapeamento espacial podem ser mais agradáveis se projetadas nas superfícies do planar fornecidas por quads ou pela malha Watertight do planar. Isso é especialmente verdadeiro para ambientes/cenários nos quais a pré-verificação não é ideal devido ao fato de que a cena inferirá, e os ambientes completos e suposições de planar minimizarão artefatos.

Além disso, o número total de superfícies retornado pelo mapeamento espacial é limitado pelo cache espacial interno, enquanto a versão de compreensão da cena da malha de mapeamento espacial é capaz de acessar dados de mapeamento espacial que não são armazenados em cache. Por isso, a compreensão da cena é mais adequada à captura de representações de malha para espaços maiores (por exemplo, mais de um único espaço) para visualização ou processamento de malha adicional. A malha mundial retornada com EnableWorldMesh terá um nível consistente de detalhes em todo o mundo, o que pode gerar uma visualização mais agradável se for renderizado como wireframe.

### <a name="see-also"></a>Consulte também

* [SDK de compreensão da cena](scene-understanding-SDK.md)
* [Mapeamento espacial](spatial-mapping.md)

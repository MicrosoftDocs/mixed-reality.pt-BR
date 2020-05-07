---
title: Reconhecimento de cena
description: Introdução aos recursos de compreensão da cena para o HoloLens
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Compreensão da cena, mapeamento espacial, realidade do Windows Mixed, Unity
ms.openlocfilehash: 615da20df95f4a435216457e8b9f16bb7d7d069b
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604957"
---
# <a name="scene-understanding"></a>Reconhecimento de cena

A compreensão da cena fornece aos desenvolvedores de realidade misturada uma representação de ambiente estruturada e de alto nível, projetada para tornar o desenvolvimento de aplicativos com reconhecimento de ambiente intuitivo. O entendimento da cena faz isso combinando o poder dos tempos de execução de realidade misturados existentes, como o [mapeamento espacial](spatial-mapping.md) menos estruturado e altamente preciso e novos tempos de execução orientados a ia. Ao combinar essas tecnologias, a compreensão da cena gera representações de ambientes 3D semelhantes aos que você pode ter usado em estruturas como Unity ou ARKit/ARCore. O ponto de entrada de compreensão da cena começa com um observador de cena, que é chamado pelo seu aplicativo para computar uma nova cena. Hoje, a tecnologia é capaz de gerar 3 categorias de objeto diferentes, mas relacionadas: malhas de ambiente Watertight simplificadas que inferem na estrutura de sala planar sem aglomeração, regiões de plano para posicionamento que chamamos de quatro processadores e um instantâneo da malha de [mapeamento espacial](spatial-mapping.md) que se alinha com os dados de quatro Watertight que fazemos.

![Malha de mapeamento espacial, superfícies de planar rotuladas, malha Watertight](images/SUScenarios.png)

Este documento destina-se a fornecer uma visão geral do cenário e esclarecer a relação que a cena compreende e o compartilhamento de mapeamento espacial.

## <a name="developing-with-scene-understanding"></a>Desenvolvendo com compreensão da cena

Este artigo só serve para apresentar a cena que entende o tempo de execução e os conceitos. Se você estiver procurando documentação sobre como desenvolver com a compreensão da cena, você pode estar interessado no seguinte:

[Visão geral do SDK de compreensão da cena](scene-understanding-SDK.md)

Você pode baixar o aplicativo de exemplo de compreensão da cena no site do GitHub de exemplo:

[Exemplo de compreensão da cena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Se você não tiver um dispositivo e desejar acessar cenas de exemplo para experimentar a compreensão da cena, há cenas na pasta de ativos de exemplo:

[Cenas de exemplo de compreensão de cena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>.

Se você estiver procurando detalhes específicos sobre como desenvolver para compreensão da cena ou detalhes sobre como o entendimento da cena funciona e como desenvolvê-lo, consulte a documentação [visão geral do SDK de compreensão da cena](scene-understanding-SDK.md) .


### <a name="sample"></a>Amostra


## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1º gen)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Reconhecimento de cena</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>Cenários de uso comuns

![Ilustrações de cenários de uso de mapeamento espacial comum: posicionamento, oclusão, física e navegação](images/sm-concepts-1000px.png)<br>
*Cenários de uso de mapeamento espacial comum: posicionamento, oclusão, física e navegação.*

<br>

Muitos dos principais cenários de aplicativos com reconhecimento de ambiente (posicionamento, oclusão, física, etc.) são endereçáveis pelo mapeamento espacial e pela compreensão da cena, e esta seção destaca essas diferenças. Uma diferença importante entre a compreensão da cena e o mapeamento espacial é uma compensação da precisão e da latência máximas até a estrutura e a simplicidade. Se seu aplicativo exigir a menor latência possível e os triângulos de malha que só você deseja acessar, use o mapeamento espacial diretamente. Se você estiver executando um processamento de nível mais alto, considere a possibilidade de alternar para o modelo de compreensão da cena, pois ele deve fornecer um superconjunto de funcionalidades. Observe também que, como a compreensão da cena fornece um instantâneo da malha de mapeamento espacial como parte de sua representação, você sempre terá acesso aos dados de mapeamento espacial mais completos e precisos possíveis.

As seções a seguir revisitam os cenários principais de mapeamento espacial no contexto do SDK de compreensão da nova cena.

### <a name="placement"></a>Posicionamento

A compreensão da cena fornece novas construções projetadas especificamente para simplificar os cenários de posicionamento. Uma cena pode computar primitivos chamados SceneQuads, que descrevem superfícies planas nas quais os hologramas podem ser colocados. A SceneQuads foi projetada especificamente para posicionamento e descreve uma superfície 2D e fornece uma API para posicionamento nessa superfície. Anteriormente, ao usar a malha de triângulo para realizar o posicionamento, era necessário verificar todas as áreas do Quad e executar o preenchimento/pós-processamento de orifício para identificar bons locais para o posicionamento do objeto. Isso nem sempre é necessário com o quads, pois o tempo de execução da cena é capaz de inferir quais áreas do Quad que não foram verificadas e invalidar áreas do Quad que não fazem parte da superfície.

:::row:::
    :::column:::
       ![SceneQuads com inferência desabilitada, capturando áreas de posicionamento para regiões digitalizadas.](images/SUQuads.png)<br>
       **Imagem #1** -SceneQuads com inferência desabilitada, capturando áreas de posicionamento para regiões digitalizadas.
    :::column-end:::
        :::column:::
       ![Quatro processadores com inferência habilitada, o posicionamento não é mais limitado a áreas digitalizadas.](images/SUWatertight.png)<br>
        **#2 de imagem** -quads com inferência habilitada, o posicionamento não está mais limitado a áreas digitalizadas.
    :::column-end:::
:::row-end:::

<br>


Se seu aplicativo pretende colocar hologramas 2D ou 3D em estruturas rígidas de seu ambiente, a simplicidade e a conveniência do SceneQuads para posicionamento é preferível a computar essas informações da malha de [mapeamento espacial](spatial-mapping.md) . Para obter mais detalhes sobre este tópico, consulte a [referência do SDK de compreensão da cena](scene-understanding-SDK.md)

**Observação** Para o código de posicionamento herdado que depende da malha de mapeamento espacial, a malha de mapeamento espacial pode ser computada junto com SceneQuads definindo a configuração EnableWorldMesh. Se a API de compreensão da cena não atender aos requisitos de latência do aplicativo, recomendamos que você continue a usar a [API de mapeamento espacial](spatial-mapping.md#placement).

### <a name="occlusion"></a>Oclusão

O [mapeamento espacial oclusão](spatial-mapping.md#occlusion) permanece o modo menos latente de capturar o estado em tempo real do ambiente. Embora isso possa ser útil para fornecer oclusão em cenas altamente dinâmicas, talvez você queira considerar a compreensão da cena para o oclusão por vários motivos. Se você usar a malha de mapeamento espacial gerada pela compreensão da cena, poderá solicitar dados do mapeamento espacial que não seriam armazenados no cache local e, portanto, não disponíveis para você por meio das APIs de percepção. Usar o mapeamento espacial para oclusão juntamente com malhas Watertight fornecerá valor adicional, especificamente a conclusão da estrutura de sala não verificada.

Se seus requisitos puderem tolerar a maior latência de compreensão da cena, os desenvolvedores de aplicativos devem considerar o uso da malha de compreensão Watertight da cena e, supostamente, a malha de mapeamento espacial em harmonia com representações planares. Isso forneceria um cenário "o melhor de ambos os mundos", em que simplificava a Watertight oclusão é casado com uma geometria mais realista que fornece os mapas oclusão mais realistas possíveis.

### <a name="physics"></a>Professor

O entendimento da cena gera malhas Watertight que decompõem o espaço com a semântica, especificamente para resolver muitas limitações na física que as malhas de mapeamento espacial impõem. As estruturas Watertight garantem que as conversões de raio de física sejam sempre pressionadas, e a decomposição semântica permite uma geração mais simples de malhas de NAV para navegação em interno. Conforme descrito na seção sobre [oclusão](#occlusion), a criação de uma cena com EnableSceneObjectMeshes e EnableWorldMesh produzirá a malha de conclusão mais física possível. A propriedade Watertight da malha do ambiente impedirá que testes de colisão falhem em superfícies e os dados de malha assegurarão que a física esteja interagindo com todos os objetos da cena e não apenas com a estrutura de sala.

### <a name="navigation"></a>Navegação

As malhas de planar decomposta por classe semântica são construções ideais para navegação e planejamento de caminho, facilitando muitos dos problemas descritos na visão geral de [navegação de mapeamento espacial](spatial-mapping.md#navigation) . Os objetos SceneMesh computados na cena já são descompostos por tipo de superfície, garantindo que a geração de malha de NAV seja limitada a superfícies que podem ser percorridos. Devido à simplicidade da estrutura de piso, a geração de malha de navegação dinâmica em mecanismos 3D, como o Unity, é atingível dependendo dos requisitos em tempo real.

A geração de malhas de navegação precisas ainda requer pós-processamento, ou seja, os aplicativos ainda precisam projetar occluders no chão para garantir que a navegação não passe por resíduos/tabelas etc... A maneira mais precisa de fazer isso é projetar os dados de malha mundial que serão fornecidos se a cena for computada com o sinalizador EnableWorldMesh.

### <a name="visualization"></a>Visualização

Embora a [visualização de mapeamento espacial](spatial-mapping.md#visualization) possa ser usada para comentários em tempo real do ambiente, há muitos cenários em que a simplicidade dos objetos planar e Watertight fornece mais desempenho ou qualidade visual. A projeção de sombra e técnicas de aterramento que são descritas usando o mapeamento espacial podem ser mais agradáveis se projetadas nas superfícies do planar fornecidas por quads ou pela malha Watertight do planar. Isso é especialmente verdadeiro para ambientes/cenários em que a pré-verificação completa não é ideal devido ao fato de que a cena inferirá, e os ambientes completos e as suposições de planar minimizarão artefatos.

Além disso, o número total de superfícies retornado pelo mapeamento espacial é limitado pelo cache espacial interno, enquanto a versão de compreensão da cena da malha de mapeamento espacial é capaz de acessar dados de mapeamento espacial que não são armazenados em cache. Por isso, a compreensão da cena é mais adequada à captura de representações de malha para espaços maiores (por exemplo, mais de um único espaço) para visualização ou processamento de malha adicional. A malha mundial retornada com EnableWorldMesh terá um nível consistente de detalhes em todo o mundo, o que pode gerar uma visualização mais agradável se for renderizado como wireframe.

### <a name="see-also"></a>Consulte Também

* [SDK de compreensão da cena](scene-understanding-SDK.md)
* [Mapeamento espacial](spatial-mapping.md)

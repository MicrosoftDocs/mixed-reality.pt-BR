---
title: Âncoras espaciais
description: Práticas recomendadas para usar âncoras espaciais para renderizar hologramas estáveis.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espacial, dimensionamento do mundo, mundo, escala, posição, orientação, âncora, âncora espacial, bloqueado pelo mundo, bloqueio de mundo, persistência, compartilhamento
ms.openlocfilehash: eb0fae7881f1b6517da57305ef2fa3cb1ed78648
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591021"
---
# <a name="spatial-anchors"></a>Âncoras espaciais

Uma âncora espacial representa um ponto importante no mundo do que o sistema deve manter o controle de ao longo do tempo. Cada âncora tem um [sistema de coordenadas](coordinate-systems.md) que ajusta conforme necessário, em relação a outras âncoras ou quadros de referência, a fim de garantir que os hologramas ancoradas fiquem com precisão em colocar.  Renderizar um holograma no sistema de coordenadas de uma âncora lhe dá o posicionamento mais precisos para esse holograma a qualquer momento. Isso vem às custas de pequenos ajustes ao longo do tempo para a posição do holograma, como o sistema continuamente, ela será movida para o lugar em relação ao mundo real.

Você também pode persistir e compartilhar âncoras espaciais entre sessões do aplicativo e em todos os dispositivos:
* Salvando âncoras espaciais locais em disco e carregando-os novamente mais tarde, seu aplicativo pode justificar o mesmo local no mundo real em várias sessões do aplicativo em um único dispositivo HoloLens.
* Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para criar uma âncora de nuvem, seu aplicativo pode compartilhar uma âncora espacial entre vários HoloLens, dispositivos iOS e Android. Fazendo com que cada dispositivo renderizar um holograma usando a mesma âncora espacial, todos os usuários verão o holograma aparecem no mesmo lugar no mundo real.  Isso permite experiências compartilhadas em tempo real.
* Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espacial do Azure</a> para persistência holograma assíncrona em dispositivos Android, iOS e HoloLens.  Compartilhando uma âncora de nuvem durável espacial, vários dispositivos podem observar o holograma persistente mesmo ao longo do tempo, mesmo se esses dispositivos não estão presentes em conjunto ao mesmo tempo.

Para dimensionamento permanente ou escala de sala de experiências para headsets da área de trabalho vinculados que permanecerão em um diâmetro do medidor de 5, você pode geralmente apenas usar o [estágio quadro de referência](coordinate-systems.md#stage-frame-of-reference) em vez de espaciais âncoras, fornecendo um único sistema de coordenadas no qual processar todo o conteúdo. No entanto, se seu aplicativo pretende permitir que os usuários Peregrino além dos 5 metros em HoloLens, talvez operando em todo um andar inteiro de um prédio, você precisará âncoras espaciais para manter o conteúdo estável.

Enquanto as âncoras espaciais são ótimas para hologramas devem permanecem fixas no mundo, depois que uma âncora é colocada, ele não pode ser movido. Existem alternativas para âncoras são mais adequadas para hologramas dinâmicas que devem marcar, juntamente com o usuário. É melhor posicionar hologramas dinâmicas usando um quadro estacionário de referência (a fundação para coordenadas de mundo do Unity) ou um quadro de referência anexado.

## <a name="best-practices"></a>Práticas recomendadas

Essas diretrizes de âncora espacial ajudará você a renderizar hologramas estáveis que rastreiam com precisão o mundo real.

### <a name="create-spatial-anchors-where-users-place-them"></a>Criar âncoras espaciais no qual os usuários colocá-los

Na maioria das vezes, os usuários devem ser aqueles explicitamente colocar âncoras espaciais.

Por exemplo, em HoloLens, um aplicativo pode se cruzar o usuário [olhares](gaze.md) ray com o [mapeamento espacial](spatial-mapping.md) malha para permitir que o usuário decidir onde colocar um holograma. Quando o usuário toca para colocar esse holograma, crie uma âncora espacial no ponto de interseção e, em seguida, coloque o holograma na origem do sistema de coordenadas dessa âncora.

Âncoras espaciais locais são fáceis e de alto desempenho para criar e o sistema serão consolidar seus dados internos se várias âncoras podem compartilhar seus dados de sensor subjacentes. Normalmente, você deve criar uma nova âncora espacial local para cada holograma que um usuário coloca explicitamente, exceto nos casos descritos abaixo, como grupos rígidos de hologramas.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Sempre processar hologramas ancoradas dentro de 3 medidores de sua âncora

Âncoras espaciais estabilizem o sistema de coordenadas perto de origem da âncora. Se você renderizar hologramas mais do que cerca de 3 medidores partir dessa origem, esses hologramas podem enfrentar erros posicionais perceptíveis proporcionalmente sua distância dessa origem, devido a efeitos alavanca arm. Isso funciona se o usuário significa próximo a âncora, pois o holograma está longe do usuário, que significa que o erro angular do holograma distante será pequeno. No entanto, se o usuário percorre a esse holograma distante, em seguida, será grande em sua exibição, tornando os efeitos de arm a alavanca da origem âncora longínqua bastante óbvia.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Hologramas de grupo que devem formar um cluster rígido

Hologramas vários podem compartilhar a mesma âncora espacial se o aplicativo espera que essas hologramas manter relações fixas um ao outro.

Por exemplo, se você estiver animando um sistema solar holographic em uma sala, é melhor ligar todos os objetos do sistema solar a um único âncora no centro, para que eles são movidos sem problemas relativos uns aos outros. Nesse caso, é o sistema solar como um todo para o qual está ancorado, mesmo que suas partes do componente estiver movendo dinamicamente em torno da âncora.

A limitação chave para manter a estabilidade do holograma é seguir a regra de medidor 3 acima.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Renderizar hologramas altamente dinâmicas usando o quadro estacionário de referência em vez de uma âncora espacial local

Se você tiver um holograma altamente dinâmico, como um caractere andando sala ou uma interface do usuário flutuante que acompanha a parede próxima ao usuário, é melhor ignorar âncoras espaciais locais e processar essas hologramas diretamente no sistema de coordenadas fornecido pelo [</C0>quadroestacionáriodereferência<spanclass="notranslate">](coordinate-systems.md#stationary-frame-of-reference) (ou seja, no Unity, você fazer isso colocando hologramas diretamente nas coordenadas de mundo sem um WorldAnchor).</span> Hologramas em um quadro estacionário de referência podem enfrentar descompasso quando o usuário está longe de ser o holograma, mas isso é menos provável de ser perceptível para hologramas dinâmicas: o holograma está sempre se movendo mesmo assim, tanto o movimento mantém constantemente perto do usuário , onde será minimizado descompasso.

Um caso interessante de hologramas dinâmicos é um objeto que é animada de um sistema de coordenadas ancorado para outro. Por exemplo, você pode ter dois Castelos 10 metros de distância, cada um em seu próprio espacial âncora, com um castle Disparando um cannonball em outro castelo. No momento em que o cannonball é disparado, você pode renderizar no local apropriado no quadro estacionário de referência, para coincidir com o cannon no sistema de coordenadas do castle primeiro ancorado. Ele pode seguir sua trajetória em quadro estacionário de referência conforme ela surge por meio de ondas de rádio de 10 metros. À medida que o cannonball atinge o castle outro, você pode optar por mover-o na segunda do castelo ancorado sistema de coordenadas para permitir cálculos com corpos rígidos do que a do castle física.

Se você estiver compartilhando um holograma altamente dinâmico em todos os dispositivos, você precisará escolher alguns âncora de nuvem espacial para atuar como pai, como quadros de referência estáticos não podem ser compartilhados entre dispositivos.  No entanto, nesse caso, você deve garantir que tanto o holograma dinâmico ou os dispositivos exibindo-permaneçam em radius de medidor 3 da âncora, para garantir que o holograma apareça estável em todos os dispositivos.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitar a criação de uma grade espacial âncoras

Você pode ficar tentado a ter seu aplicativo descartar uma grade regular espacial âncoras, pois o orienta o usuário ao redor, transição objetos dinâmicos de âncora a âncora de medida que se movimentam. No entanto, isso envolve muita de gerenciamento para seu aplicativo, sem o benefício dos dados de sensor profunda que o próprio sistema mantém internamente. Nesses casos, você geralmente obterá resultados melhores com menos esforço, colocando seu hologramas no quadro estacionário de referência, conforme descrito na seção acima.

Ao posicionar previamente um conjunto de âncoras de nuvem espacial em torno de um espaço estático, considere colocar as âncoras espaciais nos locais das chave hologramas que encontrarão o usuário pelo princípio acima, em vez de criar uma grade arbitrária de âncoras de.  Isso garante que você obterá o máximo estabilidade para essas chaves hologramas.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Versão locais âncoras espaciais que você não precisa mais

Quando uma âncora espacial local estiver ativa, o sistema será priorizar manter em torno dos dados de sensor que esteja perto essa âncora. Se você não estiver usando uma âncora espacial, stop acessando seu sistema de coordenadas. Isso permitirá que seus dados de sensor de base a ser removida conforme necessário.

Isso é especialmente importante para âncoras locais que tiver mantido no armazenamento de âncora espacial. Os dados de sensor por trás essas âncoras serão mantidos em torno de permanentemente para permitir que seu aplicativo para encontrar essa âncora em futuras sessões do aplicativo, que reduzirão o espaço disponível para acompanhar outras âncoras. Manter apenas essas âncoras locais que você precisa localizar novamente em futuras sessões e removê-los do repositório quando eles não são mais significativos para o usuário.

Para âncoras espacial de nuvem, o armazenamento pode dimensionar conforme seu cenário exigir.  Você pode armazenar tantas âncoras de nuvem conforme necessário, liberando-os somente quando souber que os usuários não precisarão localizar hologramas no que ancoram novamente.

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas](coordinate-systems.md)
* [Compartilhado experiências na realidade mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras espaciais do Azure</a>
* [Persistência no Unity](persistence-in-unity.md)
* [Âncoras espaciais no DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Estudo de caso - examinando buracos na sua realidade](case-study-looking-through-holes-in-your-reality.md)

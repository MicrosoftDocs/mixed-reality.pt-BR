---
title: Âncoras espaciais
description: Práticas recomendadas para usar âncoras espaciais para renderizar hologramas estáveis.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: sistema de coordenadas, sistema de coordenadas espaciais, dimensionamento do mundo, mundo, escala, posição, orientação, âncora, âncora espacial, bloqueado pelo mundo, bloqueio de mundo, persistência, compartilhamento
ms.openlocfilehash: 16165194d040ad22f7885897eddcc65cf9dcaec3
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730857"
---
# <a name="spatial-anchors"></a>Âncoras espaciais

Uma âncora espacial representa um ponto importante no mundo que o sistema deve acompanhar ao longo do tempo. Cada âncora tem um [sistema de coordenadas](coordinate-systems.md) que é ajustado conforme necessário em relação a outras âncoras ou quadros de referência, a fim de garantir que os hologramas ancorados fiquem no lugar estabelecido.  Renderizar um holograma no sistema de coordenadas de uma âncora oferece o posicionamento mais preciso para esse holograma a qualquer momento. Isso acontece graças a pequenos ajustes ao longo do tempo na posição do holograma, conforme o sistema continuamente o move de volta ao lugar relativo ao mundo real.

Você também pode persistir e compartilhar âncoras espaciais entre sessões do aplicativo e em todos os dispositivos:
* Se você salvar âncoras espaciais locais em disco e carregá-las novamente mais tarde, o aplicativo poderá chegar mais ou menos no mesmo local no mundo real entre várias sessões do aplicativo em um único dispositivo HoloLens.
* Se você usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a> para criar uma âncora de nuvem, o aplicativo poderá compartilhar uma âncora espacial entre vários dispositivos HoloLens, iOS e Android. Ao fazer cada dispositivo renderizar um holograma usando a mesma âncora espacial, todos os usuários verão o holograma aparecer no mesmo lugar no mundo real.  Isso permite experiências compartilhadas em tempo real.
* Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a> para persistência assíncrona de holograma em dispositivos HoloLens, iOS e Android.  Ao compartilhar uma âncora espacial em nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que os dispositivos não estejam presentes ao mesmo tempo.

Para experiências de escala permanentes ou de escala do cômodo com headsets de desktop vinculados que ficarão em um diâmetro de 5 metros, você normalmente pode usar o [estágio quadro de referência](coordinate-systems.md#stage-frame-of-reference) em vez de âncoras espaciais, fornecendo um único sistema de coordenadas no qual renderizar todo o conteúdo. No entanto, se o seu aplicativo pretende deixar que os usuários vão além de 5 metros no HoloLens, talvez operar em todo um andar de um prédio, você precisará de âncoras espaciais para manter o conteúdo estável.

Ainda que as âncoras espaciais sejam excelentes para hologramas que devam permanecer fixos no mundo, quando uma âncora é colocada, ela não pode ser movida. Existem alternativas para âncoras que são mais apropriadas para hologramas dinâmicos que devem acompanhar o usuário. É melhor posicionar os hologramas dinâmicos usando um quadro de referência fixo (a base das coordenadas do mundo Unity) ou um quadro de referência anexado.

## <a name="best-practices"></a>Práticas recomendadas

Essas diretrizes de âncora espacial vão ajudá-lo a renderizar hologramas estáveis que acompanham com precisão o mundo real.

### <a name="create-spatial-anchors-where-users-place-them"></a>Criar âncoras espaciais onde os usuários as posicionam

Na maioria das vezes, os usuários devem ser aqueles que posicionam explicitamente as âncoras espaciais.

Por exemplo, no HoloLens, um aplicativo pode cruzar o raio de [foco](gaze.md) do usuário com a malha do [mapeamento espacial](spatial-mapping.md) para permitir que o usuário decida onde posicionar o holograma. Quando o usuário toca para posicionar o holograma, crie uma âncora espacial no ponto de interseção e, em seguida, posicione o holograma na origem do sistema de coordenadas do sistema.

Âncoras espaciais locais são fáceis e de alto desempenho para criar e o sistema vai consolidar seus dados internos se várias âncoras puderem compartilhar seus dados de sensor subjacentes. Normalmente, você deve criar uma nova âncora espacial local para cada holograma que um usuário posiciona explicitamente, exceto nos casos descritos abaixo, como grupos rígidos de hologramas.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Sempre processe hologramas ancorados a 3 metros de sua âncora

Âncoras espaciais estabilizam o sistema de coordenadas perto da origem da âncora. Se você processar hologramas a mais de cerca de 3 metros da origem, esses hologramas podem enfrentar erros perceptíveis de posicionamento de forma proporcional à distância da origem, devido a efeitos da alavanca arm. Isso funciona se o usuário fica perto da âncora, pois o holograma também está longe do usuário, o que significa que o erro angular do holograma distante será pequeno. No entanto, se o usuário anda até o holograma distante, ele ficará grande na visão dele, tornando óbvios os efeitos da alavanca arm da origem da âncora distante.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Agrupe hologramas que devem formar um cluster rígido

Vários hologramas podem compartilhar a mesma âncora espacial se o aplicativo espera que esses hologramas mantenham relações fixas uns com os outros.

Por exemplo, se você estiver animando um sistema solar holográfico em uma sala, é melhor ligar todos os objetos do sistema solar a uma única âncora no centro para que eles se movam sem problemas relacionados uns aos outros. Nesse caso, é o sistema solar como um todo que está ancorado, mesmo que as partes do componente estejam se momento de forma dinâmica em torno da âncora.

O principal aqui para manter a estabilidade do holograma é seguir a regra dos 3 metros acima.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Renderizar hologramas altamente dinâmicos usando o quadro fixo de referência em vez de uma âncora espacial local

Se você tiver um holograma altamente dinâmico, como um personagem andando pela sala ou uma interface do usuário flutuante que acompanha a parede próxima ao usuário, é melhor ignorar âncoras espaciais locais e processar esses hologramas diretamente no sistema de coordenadas fornecido pelo [quadro de referência fixo](coordinate-systems.md#stationary-frame-of-reference) (ou seja, no Unity você faz isso posicionando os hologramas direto nas coordenadas do mundo sem um WorldAnchor). Os hologramas em um quadro de referência fixo podem passar por descompassos quando o usuário que está do holograma, mas isso é menos provável de ser perceptível para hologramas dinâmicos: o holograma está sempre se movendo de qualquer forma ou o movimento dele o mantém constantemente perto do usuário , onde o descompasso será minimizado.

Um caso interessante de hologramas dinâmicos é o de um objeto que é animado de um sistema de coordenadas ancorado para outro. Por exemplo, você pode ter dois castelos a 10 metros de distância um do outro, cada um em sua própria âncora espacial, com um castelo disparando um canhão no outro castelo. No momento em que o canhão é disparado, você pode renderizar no local apropriado no quadro de referência fixo para coincidir com o canhão no primeiro sistema de coordenadas ancoradas do primeiro castelo. Ele pode seguir sua trajetória no quadro de referência fixo, já que voa por 10 metros pelo ar. À medida que o tiro de canhão atinge o outro castelo, você poderá optar por movê-lo para o sistema de coordenadas ancoradas do segundo castelo para permitir cálculos físicos dos corpos rígidos do castelo.

Se estiver compartilhando um holograma altamente dinâmico entre dispositivos, você precisará escolher algumas âncoras de nuvem espacial para atuar como pai, já que os quadros de referência fixos não podem ser compartilhados entre dispositivos.  No entanto, nesse caso, você deve garantir que o holograma dinâmico e os dispositivos que o visualizam estejam no raio de 3 metros da âncora, para garantir que o holograma apareça estável em todos os dispositivos.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evite a criação de uma grade de âncoras espaciais

Você pode ficar tentado a deixar que o aplicativo tenha uma grade regular de âncoras espaciais conforme o usuário se movimenta, transicionando objetos dinâmicos de âncora a âncora à medida que se movimentam. No entanto, isso envolve um grande trabalho de gerenciamento do aplicativo, sem o benefício dos dados de sensor detalhados que o próprio sistema mantém internamente. Nesses casos, você geralmente obterá resultados melhores com menos esforço posicionando os hologramas no quadro de referência fixo, conforme descrito na seção acima.

Ao posicionar previamente um conjunto de âncoras de nuvem espacial em torno de um espaço estático, considere posicionar as âncoras espaciais nos locais dos principais hologramas que o usuário encontrará pelo princípio acima, em vez de criar uma grade arbitrária de âncoras.  Isso garante que você obterá estabilidade máxima para esses hologramas importantes.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Libere as ancoras âncoras espaciais locais de que não precisa mais

Quando uma âncora espacial local está ativa, o sistema vai priorizar mantê-la perto dos dados do sensor que estão perto da âncora. Se não estiver usando mais uma âncora espacial, pare de acessar o sistema de coordenadas dela. Isso permitirá que seus dados de sensor subjacentes sejam removidos como necessário.

Isso é especialmente importante para âncoras locais que você tenha mantido no armazenamento de âncoras espaciais. Os dados de sensor por trás dessas âncoras serão mantidos permanentemente para permitir que seu aplicativo encontre essa âncora em sessões futuras do aplicativo, que reduzirão o espaço disponível para acompanhar outras âncoras. Mantenha apenas essas âncoras locais que você precisa localizar novamente em futuras sessões e as remova do armazenamento quando elas não forem mais significativas para o usuário.

Nas âncoras espaciais de nuvem, o armazenamento pode ser dimensionado conforme seu cenário exigir.  Você pode armazenar quantas âncoras de nuvem forem necessárias, liberando-as somente quando souber que os usuários não precisarão mais localizar hologramas naquela âncora.

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas](coordinate-systems.md)
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* [Persistência no Unity](persistence-in-unity.md)
* [Âncoras espaciais no DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Estudo de caso - Como olhar através dos buracos na sua realidade](case-study-looking-through-holes-in-your-reality.md)

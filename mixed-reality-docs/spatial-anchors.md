---
title: Âncoras espaciais
description: Práticas recomendadas para usar âncoras espaciais para renderizar hologramas estáveis.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciais, dimensionamento do mundo, mundo, escala, posição, orientação, âncora, âncora espacial, bloqueado pelo mundo, bloqueio de mundo, persistência, compartilhamento
ms.openlocfilehash: f65cf582db43399814737d581ece4694646a144c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438023"
---
# <a name="spatial-anchors"></a>Âncoras espaciais

Uma âncora espacial representa um ponto importante no mundo em que o sistema mantém o controle ao longo do tempo. Cada âncora tem um [sistema de coordenadas](coordinate-systems.md) que é ajustado conforme necessário em relação a outras âncoras ou quadros de referência, a fim de garantir que os hologramas ancorados fiquem no lugar estabelecido.  Renderizar um holograma no sistema de coordenadas de uma âncora oferece o posicionamento mais preciso para esse holograma a qualquer momento. Isso é voltado ao custo de pequenos ajustes ao longo do tempo até a posição do holograma, pois o sistema o move continuamente de volta para o mundo real.

Você também pode persistir e compartilhar âncoras espaciais entre sessões de aplicativo e entre dispositivos:
* Ao salvar âncoras espaciais locais em disco e carregá-las novamente mais tarde, seu aplicativo pode calcular o mesmo local no mundo real entre várias sessões de aplicativo em um único HoloLens.
* Usando <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">âncoras espaciais do Azure</a> para criar uma âncora de nuvem, seu aplicativo pode compartilhar uma âncora espacial entre vários dispositivos HoloLens, Ios e Android. Ao fazer com que cada dispositivo processe um holograma usando a mesma âncora espacial, os usuários verão que o holograma aparecerá no mesmo lugar do mundo real. Isso permite experiências compartilhadas em tempo real.
* Você também pode usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Âncoras Espaciais do Azure</a> para persistência assíncrona de holograma em dispositivos HoloLens, iOS e Android. Ao compartilhar uma âncora espacial em nuvem durável, vários dispositivos podem observar o mesmo holograma persistente ao longo do tempo, mesmo que os dispositivos não estejam presentes ao mesmo tempo.

Para experiências em escala de pé ou de sala para headsets de área de trabalho que permanecerão dentro de um diâmetro de 5 metros, você normalmente pode usar o [quadro de referência](coordinate-systems.md#stage-frame-of-reference) em vez de âncoras espaciais, que fornece um único sistema de coordenadas no qual renderiza todo o conteúdo. No entanto, se seu aplicativo pretende permitir que os usuários perfrentem mais de 5 metros no HoloLens, talvez operando em todo um andar de um edifício, você precisará de âncoras espaciais para manter o conteúdo estável.

Ainda que as âncoras espaciais sejam excelentes para hologramas que devam permanecer fixos no mundo, quando uma âncora é colocada, ela não pode ser movida. Há alternativas para âncoras que são mais apropriadas para hologramas dinâmicos que marcam junto com o usuário. É melhor posicionar os hologramas dinâmicos usando um quadro de referência fixo (a base das coordenadas do mundo Unity) ou um quadro de referência anexado.

## <a name="best-practices"></a>Práticas recomendadas

Essas diretrizes de âncora espacial vão ajudá-lo a renderizar hologramas estáveis que acompanham com precisão o mundo real.

### <a name="create-spatial-anchors-where-users-place-them"></a>Criar âncoras espaciais onde os usuários as posicionam

Normalmente, os usuários são aqueles explicitamente colocando âncoras espaciais.

Por exemplo, no HoloLens, um aplicativo pode interceptar o [olhar](gaze-and-commit.md) Ray do usuário com a malha de [mapeamento espacial](spatial-mapping.md) para permitir que o usuário decida onde posicionar um holograma. Quando o usuário toca para posicionar esse holograma, crie uma âncora espacial no ponto de interseção e coloque o holograma na origem do sistema de coordenadas da âncora.

Âncoras espaciais locais são fáceis e de alto desempenho para criar. O sistema consolidará seus dados internos se várias âncoras puderem compartilhar seus dados de sensor subjacentes. Normalmente, você deve criar uma nova âncora espacial local para cada holograma que um usuário insere explicitamente, exceto nos casos descritos abaixo, como grupos rígidos de hologramas.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Sempre processe hologramas ancorados a 3 metros de sua âncora

Âncoras espaciais estabilizam o sistema de coordenadas perto da origem da âncora. Se você renderizar hologramas mais de três metros dessa origem, esses hologramas poderão apresentar erros posicionais perceptíveis em proporção à distância dessa origem devido a efeitos de braço de alavanca. Isso funcionará se o usuário estiver próximo da âncora, já que o holograma está longe do usuário. Em outras palavras, o erro angular do holograma distante será pequeno. No entanto, se o usuário se movimentar até esse holograma distante, ele será grande em sua exibição, fazendo com que os efeitos de braço de alavanca da origem da âncora distante sejam bastante óbvios.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Agrupe hologramas que devem formar um cluster rígido

Vários hologramas podem compartilhar a mesma âncora espacial se o aplicativo espera que esses hologramas mantenham as relações fixas entre si.

Por exemplo, se você estiver animando um sistema solar Holographic em uma sala, é melhor vincular todos os objetos do sistema solar a uma única âncora no centro para que eles se movimentem suavemente em relação uns aos outros. Nesse caso, é o sistema solar como um todo que está ancorado, mesmo que as partes do componente estejam se momento de forma dinâmica em torno da âncora.

A principal advertência para manter a estabilidade do holograma é seguir a regra de 3 medidores acima.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Renderizar hologramas altamente dinâmicos usando o quadro fixo de referência em vez de uma âncora espacial local

Se você tiver um holograma altamente dinâmico, como um caractere percorrendo uma sala ou uma interface do usuário flutuante que segue ao longo da parede, é melhor ignorar âncoras espaciais locais e renderizar esses hologramas diretamente no sistema de coordenadas fornecido pelo [ quadro estacionário de referência](coordinate-systems.md#stationary-frame-of-reference). I Unity, você consegue fazer isso colocando os hologramas diretamente em coordenadas mundiais sem um WorldAnchor. Os hologramas em um quadro estacionário de referência podem apresentar descompasso quando o usuário estiver longe do holograma. Mas isso é menos provável de ser perceptível para hologramas dinâmicos: ou o holograma está constantemente se movendo de forma constante ou seu movimento o mantém constantemente perto do usuário onde a descompasso será minimizada.

Um caso interessante de hologramas dinâmicos é o de um objeto que é animado de um sistema de coordenadas ancorado para outro. Por exemplo, você pode ter dois castelos 10 metros de distância, cada um em sua própria âncora espacial com um Castle acionando um Cannonball no outro Castle. No momento em que o Cannonball é acionado, você pode renderizá-lo no local apropriado no quadro estacionário de referência para coincidir com o Cannon no sistema de coordenadas ancorado do primeiro Castle. Ele pode seguir sua trajetória no quadro de referência fixo, já que voa por 10 metros pelo ar. Como o Cannonball atinge o outro Castle, você pode optar por movê-lo para o sistema de coordenadas ancorado da segunda Castle para permitir cálculos de física com os corpos rígidos de Castle.

Se estiver compartilhando um holograma altamente dinâmico entre dispositivos, você precisará escolher uma âncora espacial de nuvem para atuar como pai, pois os quadros de referência estáticos não podem ser compartilhados entre dispositivos.  No entanto, nesse caso, você deve garantir que o holograma dinâmico ou os dispositivos que o estão exibindo permanecem no raio de 3 metros da âncora para garantir que o holograma pareça estável em todos os dispositivos.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evite a criação de uma grade de âncoras espaciais

Você pode estar tentado a fazer com que seu aplicativo descartar uma grade comum de âncoras espaciais enquanto o usuário percorra, fazendo a transição de objetos dinâmicos da âncora para a âncora à medida que eles se movimentam. No entanto, isso envolve uma grande quantidade de gerenciamento para seu aplicativo, sem o benefício dos dados de sensor profundo que o próprio sistema mantém internamente. Para esses casos, você geralmente obterá resultados melhores com menos esforço colocando seus hologramas no quadro de referência, conforme descrito na seção acima.
Ao posicionar previamente um conjunto de âncoras espaciais de nuvem em um espaço estático, considere colocar as âncoras espaciais nos locais dos hologramas-chave que o usuário encontrará de acordo com o princípio acima, em vez de criar uma grade arbitrária de âncoras. Isso garante que você obterá estabilidade máxima para esses hologramas importantes.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Libere as ancoras âncoras espaciais locais de que não precisa mais

Enquanto uma âncora espacial local está ativa, o sistema prioriza a retenção dos dados do sensor que estão próximos dessa âncora. Se não estiver usando mais uma âncora espacial, pare de acessar o sistema de coordenadas dela. Isso permite que seus dados de sensor subjacentes sejam removidos conforme necessário.

Isso é especialmente importante para âncoras locais que você tenha mantido no armazenamento de âncoras espaciais. Os dados do sensor por trás dessas âncoras serão mantidos permanentemente para permitir que seu aplicativo encontre essa âncora em sessões futuras, o que reduz o espaço disponível para controlar outras âncoras. Mantenha somente as âncoras locais que você precisa localizar novamente em sessões futuras e remova-as da loja quando elas não forem mais significativas para o usuário.

Nas âncoras espaciais de nuvem, o armazenamento pode ser dimensionado conforme seu cenário exigir. Você pode armazenar quantas âncoras de nuvem forem necessárias, liberando-as somente quando souber que os usuários não precisarão localizar os hologramas nessa âncora novamente.

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas](coordinate-systems.md)
* [Experiências compartilhadas em realidade misturada](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Âncoras Espaciais do Azure</a>
* [Persistência no Unity](persistence-in-unity.md)
* [Âncoras espaciais no DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Estudo de caso - Como olhar através dos buracos na sua realidade](case-study-looking-through-holes-in-your-reality.md)

---
title: Usar o HoloLens em novos espaços
description: O HoloLens aprende a aparência de um espaço ao longo do tempo. Os usuários podem facilitar esse processo movendo o HoloLens de determinadas maneiras por meio do espaço.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Realidade mista do Windows, design, mapeamento espacial, HoloLens, reconstrução da superfície, malha, acompanhamento de cabeçalho, mapeamento
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566015"
---
# <a name="use-hololens-in-new-spaces"></a>Usar o HoloLens em novos espaços

O HoloLens *mapeia*ou aprende informações sobre o seu ambiente à medida que o usuário se move em torno de um espaço. Ao longo do tempo, o HoloLens cria um *mapa espacial* de todas as partes do ambiente que foram observadas. O HoloLens atualiza o mapa conforme as alterações no ambiente são observadas. Essa verificação persistirá automaticamente entre as inicializações do aplicativo.

O HoloLens criará e atualizará os mapas enquanto o dispositivo estiver ligado e um usuário estiver conectado. Se você mantiver ou usar o dispositivo com as câmeras apontadas por um espaço, o dispositivo tentará mapear a área. Embora o HoloLens Aprenda um espaço naturalmente ao longo do tempo, há dicas e truques disponíveis para mapear o espaço com mais rapidez e eficiência. 

Se o seu HoloLens não puder mapear seu espaço ou estiver sem calibragem, você poderá entrar no modo limitado. No modo limitado, você não poderá posicionar os hologramas no ambiente.

## <a name="tips-and-tricks-for-mapping-spaces"></a>Dicas e truques para espaços de mapeamento

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a>Verifique se o espaço está configurado para realidade misturada

Os recursos em um ambiente podem dificultar que o HoloLens interprete um espaço. Os níveis de luz, os materiais no espaço, o layout dos objetos e muito mais podem afetar como o HoloLens mapeia uma área.

As dicas para configurar seu espaço para o HoloLens e outros dispositivos de realidade misturada podem ser encontradas em [considerações de ambiente para o hololens](environment-considerations-for-hololens.md).

### <a name="understand-the-scenarios-for-the-area"></a>Entender os cenários da área

É importante gastar a maior parte do tempo em que você usará o HoloLens para que o mapa seja relevante e concluído. 

Por exemplo, se um cenário de usuário para o HoloLens envolve a mudança do ponto a para o ponto B, percorra esse caminho de duas a três vezes, examinando todas as direções à medida que você mover. 

### <a name="walk-slowly-around-the-space"></a>Explore lentamente ao contrário do espaço

Se você se movimentar muito rapidamente pela área, é provável que o HoloLens perca áreas de mapeamento. Percorra lentamente o espaço, interrompendo a cada 5-8 pés para olhar ao seu lado.

Movimentos suaves também ajudam o mapeamento de HoloLens mais automatizados.

### <a name="look-in-all-directions"></a>Examinar todas as direções

Examinar enquanto você mapeia o espaço fornece ao HoloLens mais dados sobre onde os pontos são relativos entre si. 

Se você não procurar, por exemplo, o HoloLens pode não saber onde está o teto em uma sala. 

Não se esqueça de examinar o piso enquanto mapeia o espaço.

### <a name="cover-key-areas-multiple-times"></a>Cobrir áreas-chave várias vezes

A movimentação por uma área várias vezes ajudará a pegar os recursos que você pode ter perdido no primeiro guia. Tente percorrer uma área duas a três vezes para criar um mapa ideal.

Se possível, ao repetir esses movimentos, gaste tempo percorrendo uma área em uma direção e, em seguida, gire e volte da maneira que você veio.

### <a name="take-your-time-mapping-the-area"></a>Reserve seu tempo mapeando a área

Pode levar entre 15 e 20 minutos para que o HoloLens se mapeie totalmente e se ajuste para seus arredores. Se você tiver um espaço no qual planeja usar um HoloLens frequentemente, levar esse tempo até o mapeamento do espaço pode evitar problemas posteriormente. 

## <a name="possible-errors-in-the-spatial-map"></a>Possíveis erros no mapa espacial

Os erros nos dados de mapeamento espacial se enquadram em uma das três categorias:

* *Buracos*: As superfícies do mundo real estão ausentes dos dados de mapeamento espacial.
* *Hallucinations*: Existem superfícies nos dados de mapeamento espacial que não existem no mundo real.
* *Fendas espaciais*: O HoloLens ' perde parte do mapa espacial, pensando que ele está em uma parte diferente do mapa do que realmente é.
* *Tendência*: As superfícies nos dados de mapeamento espacial são alinhadas de forma inperfeita com as superfícies do mundo real, enviadas ou retiradas.

Muitos desses erros podem ser atenuados com a [exclusão](environment-considerations-for-hololens.md) de hologramas e o novo mapeamento do espaço.
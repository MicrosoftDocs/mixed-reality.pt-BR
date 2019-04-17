---
title: Billboarding e tag-along
description: Objetos com billboarding sempre orientá-los para o usuário.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, billboarding tag-along
ms.openlocfilehash: 8215b96aff1f3c2d43e959f04ad83d41ffd32b2a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590581"
---
# <a name="billboarding-and-tag-along"></a>Billboarding e tag-along

Billboarding é um conceito de comportamento que pode ser aplicado a objetos na realidade mista. Objetos com billboarding sempre orientá-los para o usuário. Isso é especialmente útil com texto e sistemas de menus, onde os objetos estáticos são colocados no ambiente do usuário (bloqueada pelo mundo) seriam obscurecidas ou ilegíveis se mover em torno de um usuário.

![HoloLens perspectiva de um sistema de menu que sempre enfrenta o usuário](images/billboarding-fragments.gif)<br>
*HoloLens perspectiva de um sistema de menu que sempre enfrenta o usuário*

Objetos com billboarding habilitado podem girar livremente no ambiente do usuário. Eles também podem ser restritos a um único eixo dependendo das considerações de design. Tenha em mente, objetos billboarded podem recortar ou occlude em si se elas estão muito perto de outros objetos, ou em HoloLens, muito próximas verificados superfícies. Para evitar isso, pense sobre a superfície total que um objeto pode produzir quando girado no eixo habilitado para billboarding.

## <a name="what-is-a-tag-along"></a>O que é um tag-along?

Tag-Along é um conceito de comportamento que pode ser adicionado a hologramas, incluindo objetos billboarded. Essa interação é uma maneira mais natural e amigável de conseguir o efeito de conteúdo bloqueado de cabeça. Um objeto tag-along tenta nunca deixar o modo de exibição do usuário. Isso permite que o usuário interagir livremente com What ' s frente ao mesmo tempo ainda observando as hologramas fora de sua exibição direta.

![O painel de pinos do HoloLens é um ótimo exemplo de como se comporta de tag-along](images/tagalong-1000px.jpg)<br>
*O menu Iniciar do HoloLens é um ótimo exemplo de comportamento tag-along*

Objetos tag-Along têm parâmetros que podem ajustar a maneira como eles se comportam. Conteúdo pode ser dentro ou fora de linha de visão do usuário conforme desejado, enquanto o usuário gira em torno de seu ambiente. Quando o usuário move, o conteúdo será tentar permanecer dentro a periferia do usuário deslizando em direção à extremidade da exibição, dependendo de quão rapidamente um usuário move pode deixar o conteúdo temporariamente para fora da exibição. Quando o usuário gazes para o objeto tag-along, se trata mais detalhadamente no modo de exibição. Pense conteúdo sempre sendo "rapidamente distância" para que os usuários jamais se esqueça de qual direção seu conteúdo está em.

Parâmetros adicionais podem fazer com que o objeto tag-along se sentir anexado para o início do usuário por um retângulo Elástico. Retardamento aceleração ou desaceleração dá um peso para o objeto tornando-a se sentir mais fisicamente presente. Esse comportamento de spring é uma funcionalidade que ajuda o usuário a criar um modelo mental preciso de como funciona o tag-along. Áudio ajuda a fornecer capacidades adicionais para quando os usuários têm objetos no modo de tag-along. Áudio deve reforçar a velocidade do movimento; um turno fast principal deve fornecer um efeito mais visível de som e percorrendo a uma velocidade natural o deve ter efeitos de áudio se houver mínimo em todos os.

Assim como o conteúdo realmente bloqueado head, objetos tag-along podem provar sobrecarregar ou nauseating se mover totalmente ou da primavera de muita no modo de exibição do usuário. Como um usuário procura ao redor e, em seguida, rapidamente stop, seus sentidos informe ter parado. Seu equilíbrio informando que suas cabeças parou de ativação, bem como vê sua visão a parada do mundo a ativação. No entanto, se tag-along diante continua se movimentando quando o usuário tiver sido interrompido, ele pode confundir seus sentidos.

## <a name="see-also"></a>Consulte também
* [Cursores](cursors.md)
* [Conceitos básicos de interação](interaction-fundamentals.md)
* [Conforto](comfort.md)

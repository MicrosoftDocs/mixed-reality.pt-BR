---
title: Contorno e marcação
description: Os objetos com o mural sempre se orientam para enfrentar o usuário.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade misturada do Windows, mensagem de contorno
ms.openlocfilehash: 032e665d94a73b94b59f693e452874af0b45f021
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436993"
---
# <a name="billboarding-and-tag-along"></a>Contorno e marcação

<br>

<img src="images/billboarding-fragments.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">

A mensagem é um conceito comportamental que pode ser aplicado a objetos em realidade misturada. Os objetos com o mural sempre se orientam para enfrentar o usuário. Isso é especialmente útil com os sistemas de texto e de menu em que os objetos estáticos colocados no ambiente do usuário (bloqueado pelo mundo) seriam obscuros ou ilegíveis se um usuário fosse migrado.

Os objetos com o mural habilitado podem girar livremente no ambiente do usuário. Eles também podem ser restritos a um único eixo, dependendo das considerações de design. Lembre-se de que os objetos configurados podem recortar ou occlude-los se forem colocados muito próximos a outros objetos, ou no HoloLens, fechar as superfícies digitalizadas. Para evitar isso, pense na superfície total que um objeto pode produzir quando girado no eixo habilitado para a mensagem.

## <a name="what-is-a-tag-along"></a>O que é uma marca?

A marcação é um conceito comportamental que pode ser adicionado a hologramas, incluindo objetos de mensagem. Essa interação é uma maneira mais natural e amigável de obter o efeito do conteúdo bloqueado no cabeçalho. Um objeto de marca ao longo das tentativas de nunca sair da exibição do usuário. Isso permite que o usuário interaja livremente com o que está na frente deles enquanto ainda vê os hologramas fora de sua exibição direta.

![o painel Pins do HoloLens é um ótimo exemplo de como a tag se comporta](images/tagalong-1000px.jpg)<br>
*O menu Iniciar do HoloLens é um ótimo exemplo de comportamento de marcação*

Os objetos de marcação têm parâmetros que podem ajustar a forma com que se comportam. O conteúdo pode estar dentro ou fora da linha de visão do usuário, conforme desejado, enquanto o usuário se move em torno de seu ambiente. À medida que o usuário se move, o conteúdo tentará permanecer dentro do periferia do usuário, deslizando para a borda da exibição, dependendo da rapidez com que um usuário se move pode deixar o conteúdo temporariamente fora da exibição. Quando o usuário gazes em direção ao objeto de marca, ele é mais totalmente na exibição. Imagine que o conteúdo esteja sempre sendo "um relance" para que os usuários nunca se esqueçam em que direção seu conteúdo está.

Parâmetros adicionais podem fazer com que a marca de objeto seja anexada à cabeça do usuário por uma faixa de borracha. A aceleração ou a desaceleração proporciona peso ao objeto, fazendo com que ele fique mais fisicamente presente. Esse comportamento de mola é uma forma que ajuda o usuário a criar um modelo mental preciso de como o Tag-by funciona. O áudio ajuda a fornecer capacidades adicionais para quando os usuários têm objetos no modo de marca. O áudio deve reforçar a velocidade de movimento; uma rodada de cabeça rápida deve fornecer um efeito de som mais perceptível enquanto a movimentação em uma velocidade natural deve ter um áudio mínimo se houver algum efeito.

Assim como o conteúdo realmente bloqueado, os objetos de marca podem se comprovar de forma exagerada ou nauseating se se moverem intensamente ou se acabarem muito na exibição do usuário. Como um usuário procura e, em seguida, pára rapidamente, seus sentidos dizem que eles foram interrompidos. Seu saldo informa que sua cabeça parou de ser ativada, bem como sua visão vê o mundo parar de ligar. No entanto, se a marca ainda mantiver a movimentação quando o usuário for interrompido, ele poderá confundir seus sentidos.

## <a name="see-also"></a>Consulte também
* [Cursores](cursors.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Conforto](comfort.md)

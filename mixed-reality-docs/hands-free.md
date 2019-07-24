---
title: Viva voz
description: Otimizando seu aplicativo para as mãos
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade misturada, mãos gratuitas, olhar, direcionamento olhar, interação, design
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414391"
---
# <a name="hands-free"></a>Viva voz



## <a name="scenarios"></a>Cenários

Conforme descrito na [visão geral do modelo de interação](interaction-fundamentals.md), depois de identificar os usuários e suas metas, pergunte-se quais desafios ambientais ou de situação eles podem enfrentar enquanto trabalham para realizar suas tarefas. Por exemplo, muitos usuários precisam usar suas mãos para realizar suas metas reais e terão dificuldade para interagir com uma interface baseada em controladores e mãos. 

Alguns cenários específicos podem ser: 
* Guiado por uma tarefa, enquanto as mãos estão ocupadas
* Fazendo referência a materiais enquanto suas mãos estão ocupadas
* Fadiga mão
* Luvas que não podem ser rastreados
* Carregando algo


## <a name="hands-free-modalities"></a>Modalidades sem intervenção

### <a name="voice-commandingvoice-designmd"></a>[Comando de voz](voice-design.md)

Usar sua voz para comando e controlar uma interface só pode permitir que o usuário opere Handsfree, mas também ignore várias etapas. O uso dessa modalidade pode variar de permitir que o usuário simplesmente Leia o nome de qualquer botão para ativá-lo, como em consulte-it-diga-it, para conversar com um agente que pode realizar tarefas para você.



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[Focar com a cabeça e esperar](gaze-and-dwell.md)

Em algumas situações práticas, usar sua voz não é ideal ou até mesmo possível. Ambientes de fábrica altos, privacidade ou normas sociais podem ser restrições. O modelo Head olhar + de pesquisa permite que o usuário navegue pelo aplicativo usando seu vetor de cabeçalho para apontar, enquanto o modo de navegação ou de pausar em um botão o ativará após um determinado período de tempo, geralmente em cerca de 1 segundo ou assim por diante. 


## <a name="transitioning-in-and-out-of-hands-free"></a>Transição para dentro e para fora de mãos gratuitas

Para esses cenários, liberar suas mãos de interagir com hologramas para comando e navegação pode variar de ser um requisito absoluto para operar o aplicativo, de ponta a ponta, a uma conveniência adicional de que o usuário pode fazer a transição para dentro e fora de qualquer momento. 

Se o requisito do aplicativo for que ele sempre será usado sem intervenções, seja usando a pesquisa, comandos de voz ou o comando de voz simples, "Select", certifique-se de tornar o accomodations apropriado em sua interface do usuário. 

Se o seu usuário de destino precisar ser capaz de alternar de mãos para mãos gratuitas a seu critério, é importante levar os princípios a seguir em conta.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Suponha que o usuário já esteja no modo que deseja alternar para
Por exemplo, se o usuário estiver no chão de fábrica, observando uma referência de vídeo em seu Hololens e decidir pegar uma chave de fenda para começar a trabalhar, ela provavelmente começaria a trabalhar no handsfree sem precisar colocar a chave de fenda para pressionar um botão. Ela deve ser capaz de invocar uma sessão de voz com um comando de voz, a pesquisa em uma interface do usuário já visível para iniciar a pesquisa ou dizer a palavra "Select".

O usuário deve ter a capacidade de: 
* Mude para o hands sem intervenção
* Mude para as mãos com suas mãos
* Alternar para o controlador usando um controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Criar maneiras redundantes de alternar entre modos
Embora o primeiro princípio seja sobre o acesso, o segundo é sobre a disponibilidade. Não deve haver apenas uma única maneira de fazer a transição para dentro e para fora de um modo. 

Alguns exemplos seriam: 
* Um botão para iniciar as interações de voz
* Um comando de voz para fazer a transição para usar o olhar + a pesquisa

### <a name="add-a-dash-of-drama"></a>Adicionar um traço de baixo-claro
Uma opção de modo é um grande problema – é importante que, quando essas transições acontecem, elas sejam um interruptor explícito e até mesmo drástico, para permitir que o usuário saiba o que aconteceu. 


## <a name="usability-checklist"></a>Lista de verificação de usabilidade

**O usuário pode fazer tudo e tudo sem intervenção, de ponta a ponta?**
* Todos os interactible devem estar acessíveis sem intervenções
* Certifique-se de que haja uma substituição para todos os gestos personalizados, como redimensionamento, colocação, passes, toques, etc.
* Certifique-se de que o usuário tenha o controle seguro de presença, posicionamento e detalhes de interface do usuário em todos os momentos
    * Obtendo a interface do usuário fora do caminho
    * Endereçando a interface do usuário que está fora do campo de visão (FOV)
    * Quanto vejo, onde, quando

**A mecânica da interação está sendo ensinada e reforçada com a capacidades correta?**

O usuário entende...
* ... Em que modo eles estão?
* ... O que eles podem fazer neste modo?
* ... O que é o estado atual?
* ... Como eles podem fazer a transição?
    
**A interface do usuário é otimizada para mãos gratuitas?**   

* Exemplo: Capacidades de pesquisa não são internos para padrões 2D típicos
* Exemplo: O direcionamento de voz é melhor com o realce de objeto
* Exemplo: As interações de voz são melhores com legendas que precisam ser ativadas


## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Manipulação direta com as mãos](direct-manipulation.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)

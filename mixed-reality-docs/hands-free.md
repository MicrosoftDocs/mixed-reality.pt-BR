---
title: Viva voz
description: Otimizando seu aplicativo para as mãos
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade misturada, mãos gratuitas, olhar, direcionamento olhar, interação, design
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435076"
---
# <a name="hands-free"></a>Viva voz

## <a name="scenarios"></a>Cenários

Conforme descrito na [visão geral do modelo de interação](interaction-fundamentals.md), depois de identificar os usuários e suas metas, pergunte-se quais desafios ambientais ou de situação eles podem enfrentar enquanto trabalham para realizar suas tarefas. Por exemplo, muitos usuários precisam usar suas mãos para realizar suas metas reais e terão dificuldade para interagir com uma interface baseada em controladores e mãos. 

Alguns cenários específicos incluem: 
* Guiado por uma tarefa, enquanto as mãos do usuário estão ocupadas
* Fazendo referência a materiais enquanto as mãos do usuário estão ocupadas
* Fadiga mão
* Luvas que não podem ser rastreados
* Executando algo em suas mãos
* Inconveniente social para executar gestos de grande mão
* Espaços apertados


## <a name="hands-free-modalities"></a>Modalidades sem intervenção

### <a name="voice-inputvoice-inputmd"></a>[Entrada de voz](voice-input.md)

Usar sua voz para comando e controlar uma interface oferece uma maneira conveniente de operar sem interrupções e usar atalhos para ignorar várias etapas de forma flexível, se desejado. Com a entrada de voz, o usuário pode simplesmente ler o nome de qualquer botão para ativá-lo _("vê-lo, dizer")_ e conversar com um agente digital que pode realizar tarefas para você.


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[Focar e esperar](gaze-and-dwell.md)

Em algumas situações práticas, usar sua voz não é ideal ou até mesmo possível. Ambientes de fábrica altos, privacidade ou normas sociais podem ser restrições. O modelo de olhar + de duração permite que o usuário navegue por um aplicativo sem nenhuma entrada adicional além de seu olho ou olhar de cabeça: o usuário simplesmente mantém nuvens (com seus cabeçotes ou olhos) no destino e permanece lá por um momento para ativá-lo. Para saber mais sobre as considerações de design individuais para olhar + acessation, confira os [olhos-olhar +](gaze-and-dwell-eyes.md) acessation e [Head-olhar +](gaze-and-dwell-head.md)acessation.


## <a name="transitioning-in-and-out-of-hands-free"></a>Transição para dentro e para fora de mãos gratuitas

Para esses cenários, liberar suas mãos de interagir com hologramas para comando e navegação pode variar de ser um requisito absoluto para operar o aplicativo, de ponta a ponta, a uma conveniência adicional de que o usuário pode fazer a transição para dentro e fora de qualquer momento. 

Se o requisito do aplicativo for que ele sempre será usado sem intervenções, seja usando a pesquisa, comandos de voz personalizados ou o comando de voz simples, "Select", certifique-se de fazer as acomodações apropriadas em sua interface do usuário. 

Se o seu usuário de destino precisar ser capaz de alternar de mãos para mãos gratuitas a seu critério, é importante levar os princípios a seguir em conta.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Suponha que o usuário já esteja no modo que deseja alternar para
Por exemplo, se o usuário estiver no chão de fábrica, observando uma referência de vídeo em seu HoloLens e decidir pegar uma chave inglesa para começar a trabalhar, ela provavelmente começaria a trabalhar em mãos sem precisar colocar a chave de fenda para pressionar um botão. Ela deve ser capaz de invocar uma sessão de voz com um comando de voz, a pesquisa em uma interface do usuário já visível para iniciar a pesquisa ou dizer a palavra "Select".

O usuário deve ter a capacidade de: 
* Mude para o hands sem intervenção
* Mude para as mãos com suas mãos
* Alternar para o controlador usando um controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Criar maneiras redundantes de alternar entre modos
Embora o primeiro princípio seja sobre o acesso, o segundo é sobre a disponibilidade. Não deve haver apenas uma única maneira de fazer a transição para dentro e para fora de um modo. 

Alguns exemplos seriam: 
* Um botão para iniciar as interações de voz
* Um comando de voz para o qual fazer a transição, usando Head-olhar e a pesquisa

### <a name="add-a-dash-of-drama"></a>Adicionar um traço de baixo-claro
Uma opção de modo é um grande problema – é importante que, quando essas transições acontecem, elas sejam um interruptor explícito, até mesmo um drástico, para permitir que o usuário saiba o que aconteceu. 


## <a name="usability-checklist"></a>Lista de verificação de usabilidade

**O usuário pode fazer tudo e tudo sem intervenção, de ponta a ponta?**
* Todos os interagir devem estar acessíveis sem intervenções
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

* Exemplo: a capacidades de pesquisa não é interna a padrões 2D típicos
* Exemplo: o direcionamento de voz é melhor com o realce de objeto
* Exemplo: as interações de voz são melhores com legendas que precisam ser ativadas


## <a name="see-also"></a>Consulte também
* [Acompanhamento de olho no HoloLens 2](eye-tracking.md)
* [Olhar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Manipulação de mãos direta](direct-manipulation.md)
* [Gestos práticos](gaze-and-commit.md#composite-gestures)
* [Ponto de mãos e confirmação](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)

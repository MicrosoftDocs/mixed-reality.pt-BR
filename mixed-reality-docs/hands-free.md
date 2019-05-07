---
title: Otimizando seu aplicativo para mãos livres
description: Otimizando seu aplicativo para mãos livres
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade misturada, viva-voz, mantenha o foco, olhares direcionamento, interação, design
ms.openlocfilehash: b64dec802d8ed2886021a54f302ba4a948c4f5b9
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581026"
---
# <a name="optimizing-your-app-for-hands-free"></a>Otimizando seu aplicativo para mãos livres



## <a name="scenarios"></a>Cenários

Conforme descrito na [visão geral do modelo de interação](interaction-fundamentals.md), depois de você ter identificado os usuários e suas metas, pergunte-se que desafios ambientais ou situacional eles poderá enfrentar como eles trabalham para realizar suas tarefas. Por exemplo, muitos usuários precisam usar suas mãos para alcançar seus objetivos do mundo real e será ter dificuldade para interagir com uma interface com base prática e controladores. 

Alguns cenários específicos podem ser: 
* Que está sendo guiado por meio de uma tarefa, enquanto as mãos estão ocupadas
* Referenciando materiais enquanto suas mãos estão ocupadas
* Fadiga mão
* Luvas que não podem ser controladas
* Portando algo


## <a name="hands-free-modalities"></a>Viva-voz modalidades

### <a name="voice-commanding"></a>Comandos de voz

Usando a voz para comando e controle de que uma interface pode não apenas permitir que o usuário opere para mãos livres, mas também ignorar várias etapas. O uso desse modalidade pode variar de permitindo que o usuário simplesmente lê o nome do qualquer botão em voz alta para ativá-lo, como em Consulte-it-say-it, para conversar com um agente que pode realizar tarefas para você.

* [Design de voz](voice-design.md)


### <a name="head-gaze-and-dwell"></a>Olhar head e duração

Em algumas situações viva-voz, usando a voz não é ideal ou até mesmo possível. Ambientes fabris alto, privacidade ou sociais normas podem ser restrições. O cabeçalho olhares + lidam bem com modelo permite que o usuário navegue o aplicativo usando seu principal vetor para apontar ao remanescentes, ou dwelling em um botão irá ativá-lo após um determinado período de tempo (normalmente, de cerca de 1 segundo ou menos). 

* [Olhar e duração](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a>A transição para dentro e fora de mãos livres

Liberar as mãos de interagir com hologramas para comandos e navegação pode variar para esses cenários, seja um requisito absoluto para operar o aplicativo, de ponta a ponta para uma conveniência adicional que o usuário pode fazer a transição da qualquer momento. 

Se o requisito do aplicativo é que ela será sempre usada viva-voz, usando o único comando de voz, comandos de voz ou duração, "select" e, em seguida, certifique-se de fazer as acomodações apropriadas em sua interface do usuário. 

Se o usuário de destino precisa ser capaz de alternar de mãos para mãos livres a seu critério, é importante levar esses princípios em conta:

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Suponha que o usuário já está no modo que eles desejam mudar para
Por exemplo, se o usuário estiver no chão de fábrica, assistindo a uma referência de vídeo em seu Hololens e decide pegar uma chave inglesa para começar a trabalhar, ela provavelmente gostaria de começar a trabalhar para mãos livres sem a necessidade de criar a chave inglesa ao pressionar um botão. Ela deve ser capaz de invocar uma sessão de voz com um comando de voz, lidam bem com já visíveis da interface do usuário para começar a duração ou, digamos que a palavra "select".

O usuário deve ter a capacidade de: 
* Alterne para mãos livres, enquanto para mãos livres
* Alterne para mãos com suas mãos
* Alterne para o controlador usando um controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Criar formas redundantes para alternar entre modos
Embora seja o primeiro princípio sobre o acesso, a segunda é sobre a disponibilidade. Apenas não deve haver uma única maneira de fazer a transição para dentro e fora de um modo. 

Alguns exemplos seriam: 
* Um botão para começar a interações de voz
* Um comando de voz para fazer a transição usando olhar + duração

### <a name="add-a-dash-of-drama"></a>Adicionar um traço de drama
Uma opção do modo é muito importante – é importante que quando ocorrem essas transições, que eles sejam uma opção explícita, até mesmo dramática, para que o usuário saiba o que aconteceu. 


## <a name="usability-checklist"></a>Lista de verificação de usabilidade

**O usuário pode fazer tudo e qualquer coisa viva-voz, de ponta a ponta?**
* Cada interactible deve ser acessível viva-voz
* Certifique-se de que há uma substituição para todos os gestos personalizados, como o redimensionamento, colocando, dedo, toques, etc.
* Certifique-se de que o usuário tem certeza de controle de presença de interface do usuário, o posicionamento, o detalhamento em todos os momentos
    * Obtendo a interface do usuário do caminho
    * Endereçamento de interface do usuário que está fora do campo de exibição (FOV)
    * Quanto eu vejo, onde, quando

**São a mecânica da interação que está sendo ensinada e reforçada com as capacidades certas?**

O usuário entender...
* ... O modo que eles estão em?
* ... O que eles podem fazer nesse modo?
* ... O que é o estado atual?
* ... Como eles podem fazer a transição-out?
    
**É a interface do usuário otimizada para mãos livres?**   

* Ex. Capacidades de duração não são recursos internas para os padrões típicos de 2D
* Ex. O direcionamento de voz é melhor com realce de objeto
* Ex. Interações de voz são melhores com legendas que precisam ser ligado


## <a name="see-also"></a>Consulte também
* [Olhar e confirmar](gaze-and-commit.md)
* [Manipulação direta](direct-manipulation.md)
* [Ponto e confirmar](point-and-commit.md)

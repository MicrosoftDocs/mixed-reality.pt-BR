---
title: Módulo básico da aprendizagem de MR - Solucionadores e posicionamento de conteúdo dinâmico
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 4baee7ba8643f5bb80e0456eb97d915405431654
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387711"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Colocando conteúdo dinâmico e usando os solveres

Os hologramas ganham vida no HoloLens 2 quando seguem intuitivamente o usuário e são posicionados no ambiente físico de maneira a tornar a interação simples e elegante. Neste tutorial, exploraremos maneiras de colocar os hologramas dinamicamente usando as ferramentas de posicionamento disponíveis do MRTK, conhecidas como resolvedores para a forma como resolvem cenários de posicionamento espacial complexos. No MRTK, os resolvedores são um sistema de scripts e comportamentos que são usados para permitir que elementos da interface do usuário sigam você, o usuário ou outros objetos de jogo na cena. Também podem ser usados para se ajustarem a determinadas posições rapidamente, tornando seu aplicativo mais intuitivo. 

## <a name="objectives"></a>Objetivos

* Apresentar os solucionadores do MRTK
* Usar os solucionadores para fazer um conjunto de botões seguir o usuário
* Usar os solucionadores para fazer um objeto do jogo seguir as mãos do usuário

## <a name="instructions"></a>Instruções

### <a name="location-of-solvers-in-the-mrtk"></a>Localização dos solucionadores no MRTK
 Para localizar os solucionadores disponíveis em seu projeto, procure na pasta do SDK do MRTK (MixedRealityToolkit.SDK) e, dentro da pasta de utilitários, você verá a pasta de solucionadores, conforme mostrado na imagem abaixo.

![Solucionadores](images/lesson3_chapter1_step1im.PNG)

>Observação: Nesta lição, vamos abordar apenas a implementação do resolvedor orbital e do resolvedor RadialView. Para saber mais sobre a gama completa de solucionadores disponíveis no MRTK, acesse: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Usar um solucionador para seguir o usuário
O objetivo deste capítulo é aprimorar a coleção de botões criada anteriormente para que ele siga a direção do olhar do usuário. Na versão anterior do MRTK e do HoloToolkit, isso era conhecido como uma funcionalidade que.

1. Selecione o objeto pai do conjunto de botões da lição anterior.

![Lição3 Capítulo2 Etapa1im](images/Lesson3_chapter2_step1im.PNG)

2. No painel Inspetor, clique no botão Adicionar componente e procure orbital. O componente orbital deve aparecer. Selecione-o para adicionar o componente orbital ao objeto do jogo Conjunto de botões.

![Lição3 Capítulo2 Etapa2im](images/Lesson3_Chapter2_step2im.PNG)

>Observação: quando você adicionar o componente, verá que o sistema adiciona o script orbital e o script do manipulador do solucionador na guia do inspetor, que é um componente necessário. 

3. Para configurar a coleção de botões para seguir o usuário, precisamos implementar os seguintes ajustes (consulte a imagem abaixo):
- No script orbital, defina a lista suspensa tipo de orientação como somente guinada. Isso permite que apenas um eixo do objeto gire conforme ele segue o usuário.
- Defina o deslocamento local como 0 em todos os eixos. Defina o deslocamento do mundo para x = 0, y =-0.1 e z = 0.6. Isso bloqueia a movimentação do objeto, de modo que, se o usuário alterar a altura, o objeto permanecerá em uma altura fixa no ambiente físico, além de permitir que o objeto siga o usuário quando este se mover pelo ambiente. Esses valores podem ser ajustados para obter uma ampla variedade de comportamentos.
- Para um comportamento de acompanhamento em que os botões seguem apenas o modo de exibição do usuário depois que o usuário virar seu próprio rumo de forma suficiente, você pode marcar a caixa de seleção usar a depuração de ângulo para o deslocamento do mundo (Observação: este título pode aparecer truncado em algumas telas, como na imagem abaixo.) Por exemplo, para que o objeto siga o usuário apenas a cada 90 graus, defina o número de incrementos para 4 (indicados por uma seta verde no exemplo à esquerda). 

![Lição3 Capítulo2 Etapa3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Habilitando objetos para seguir as mãos controladas

Nesta seção, configuraremos o objeto do jogo de cubo criado anteriormente para seguir as mãos do usuário usando o solucionador RadialView.

1. Selecione o objeto de cubo na hierarquia da cena base. Clique em Adicionar componente no painel inspetor. 

![Lição3 Capítulo3 Etapa1im](images/Lesson3_Chapter3_step1im.PNG)

2. Digite RadialView na caixa de pesquisa e selecione o componente RadialView para adicioná-lo ao cubo. O componente do manipulador do solucionador também será adicionado automaticamente ao cubo.

3. Altere a exibição radial para não seguir a cabeça, e sim a mão esquerda. Selecione o menu suspenso ao lado da opção objeto acompanhado para referência. Em seguida, selecione junta à esquerda no menu.

![Lição3 Capítulo3 Etapa3im](images/Lesson3_chapter3_step3im.PNG)

4. Depois de selecionar a articulação da mão, você pode escolher qual parte da mão o cubo deve seguir. Para este exemplo, usaremos o pulso. Ao lado da opção junta de mão controlada, selecione o menu suspenso e selecione pulso. 

![Lição3 Capítulo3 Etapa4im](images/Lesson3_chapter3_step4im.PNG)

5. Defina as distâncias mínima e máxima como 0, para que não haja distância entre o cubo e o pulso do usuário. Depois de definido, o cubo estará devidamente alinhado ao pulso. Você também pode ajustar o campo direção de referência para ajustar o comportamento de como o cubo é orientado, como se você quiser permitir que o objeto gire com o pulso do usuário definindo a direção de referência para orientar com o objeto rastreado.

![Lição3 Capítulo3 Etapa5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>Parabéns
Neste tutorial, você aprendeu a usar os resolvedores do MRTK para ter uma interface do usuário intuitivamente seguir o User. Você também aprendeu a anexar um solucionador a um objeto do jogo (ou seja, o cubo) para seguir as mãos do usuário. Para saber mais sobre esses e outros solucionadores incluídos com o MRTK, fique à vontade para visitar a [página da documentação dos solucionadores do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Próxima lição: Interação de objetos 3D](mrlearning-base-ch4.md)


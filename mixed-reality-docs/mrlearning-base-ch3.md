---
title: Tutoriais de introdução-4. Colocando conteúdo dinâmico e usando os solveres
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 93fcdcdfb7941f377b2f3f7786368783415b1ef2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438405"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. colocando o conteúdo dinâmico e usando os solveres

Os hologramas ganham vida no HoloLens 2 quando acompanham intuitivamente o usuário e são colocados no ambiente físico de forma a tornar a interação direta e elegante. Neste tutorial, exploraremos maneiras de colocar os hologramas dinamicamente usando as ferramentas de posicionamento disponíveis do MRTK (conhecidas como solveres) para resolver cenários de posicionamento espacial complexos. No MRTK, os resolvedores são um sistema de scripts e comportamentos que são usados para permitir que elementos da interface do usuário sigam você, o usuário ou outros objetos de jogo na cena. Também podem ser usados para se ajustarem a determinadas posições rapidamente, tornando seu aplicativo mais intuitivo. 

## <a name="objectives"></a>Objetivos

* Apresentar os solucionadores do MRTK
* Usar os solucionadores para fazer um conjunto de botões seguir o usuário
* Usar os solucionadores para fazer um objeto do jogo seguir as mãos do usuário

## <a name="instructions"></a>Instruções

### <a name="location-of-solvers-in-the-mrtk"></a>Localização dos solucionadores no MRTK
 Para localizar os resolvedores disponíveis em seu projeto, procure na pasta MRTK SDK (pasta MixedRealityToolkit. SDK). Na pasta Utilitários, você verá a pasta solveres, conforme mostrado na imagem abaixo.

![Solucionadores](images/lesson3_chapter1_step1im.PNG)

>Observação: nesta lição, examinaremos apenas a implementação do resolvedor orbital e do resolvedor RadialView. Para saber mais sobre a gama completa de resolvedores disponíveis no MRTK, visite: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Usar um solucionador para seguir o usuário
O objetivo deste capítulo é aprimorar a coleção de botões criada anteriormente para que ele siga a direção do olhar do usuário. Na versão anterior do MRTK e do HoloToolkit, isso era conhecido como uma funcionalidade que.

1. Selecione o objeto pai do conjunto de botões da lição anterior.

![Lição3 Capítulo2 Etapa1im](images/Lesson3_chapter2_step1im.PNG)

2. No painel Inspetor, clique no botão Adicionar componente e procure orbital. O componente orbital deve aparecer. Selecione-o para adicionar o componente orbital ao objeto de jogo de coleção de botões.

![Lição3 Capítulo2 Etapa2im](images/Lesson3_Chapter2_step2im.PNG)

>Observação: ao adicionar o componente orbital, você observará que o sistema também adiciona o componente SolverHandler, que é um componente necessário. 

3. Para configurar a coleção de botões para seguir o usuário, precisamos implementar os seguintes ajustes (consulte a imagem abaixo):
- No script orbital, defina a lista suspensa tipo de orientação como somente guinada. Isso permite que apenas um eixo do objeto gire conforme ele segue o usuário.
- Defina o deslocamento local como 0 em todos os eixos. Defina o deslocamento do mundo como x = 0, y =-0,1 e z = 0,6. Isso bloqueia a movimentação do objeto para que, quando o usuário alterar a altura, o objeto permaneça em uma altura fixa no ambiente físico e, ao mesmo tempo, permita que ele acompanhe o usuário quando o usuário se mover sobre o ambiente. Esses valores podem ser ajustados para obter uma ampla variedade de comportamentos.
- Para um comportamento de acompanhamento em que os botões seguem apenas o modo de exibição do usuário depois que o usuário virar seu cabeçalho de forma suficiente, você pode marcar a caixa de seleção usar a depuração de ângulo para o deslocamento do mundo (Observação: esse título pode ser truncado em algumas telas, como está na imagem abaixo). Por exemplo, para que o objeto siga o usuário apenas a cada 90 graus, defina o número de etapas iguais a 4 (marcado por uma seta verde no exemplo abaixo). 

![Lição3 Capítulo2 Etapa3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Habilitando objetos para seguir as mãos controladas

Nesta seção, configuraremos o objeto de jogo do cubo criado anteriormente para seguir as mãos rastreadas do usuário usando o resolvedor RadialView.

1. Selecione o objeto de cubo na hierarquia BaseScene. Clique em Adicionar componente no painel inspetor. 

![Lição3 Capítulo3 Etapa1im](images/Lesson3_Chapter3_step1im.PNG)

2. Digite RadialView na caixa de pesquisa e selecione o componente RadialView para adicioná-lo ao cubo. O componente SolverHandler também será adicionado automaticamente ao cubo.

3. Para alterar o RadialView para seguir o lado esquerdo, em vez do cabeçalho, selecione o menu suspenso ao lado da opção objeto acompanhado para referência e, em seguida, selecione mão conjunta à esquerda no menu.

![Lição3 Capítulo3 Etapa3im](images/Lesson3_chapter3_step3im.PNG)

4. Depois de selecionar a articulação da mão, você pode escolher qual parte da mão o cubo deve seguir. Para este exemplo, usaremos o pulso. Ao lado da opção listada em conjunto, selecione o menu suspenso e selecione pulso. 

![Lição3 Capítulo3 Etapa4im](images/Lesson3_chapter3_step4im.PNG)

5. Defina as distâncias mínima e máxima como 0, para que não haja distância entre o cubo e o pulso do usuário. Depois de definido, o cubo estará devidamente alinhado ao pulso. Você também pode ajustar o campo direção de referência para ajustar o comportamento de como o cubo é orientado, como se você quiser permitir que o objeto gire com o pulso do usuário definindo a direção de referência para orientar com o objeto rastreado.

![Lição3 Capítulo3 Etapa5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>Parabéns
Neste tutorial, você aprendeu a usar os resolvedores do MRTK para ter uma interface do usuário intuitivamente seguir o User. Você também aprendeu a anexar um solucionador a um objeto do jogo (ou seja, o cubo) para seguir as mãos do usuário. Para saber mais sobre esses e outros solucionadores incluídos com o MRTK, fique à vontade para visitar a [página da documentação dos solucionadores do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Próxima lição: 5. interagindo com objetos 3D](mrlearning-base-ch4.md)


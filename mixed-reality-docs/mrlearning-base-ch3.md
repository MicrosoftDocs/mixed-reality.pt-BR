---
title: Módulo MR Learning Base - Solvers e o posicionamento de conteúdo dinâmico
description: Conclua este curso para aprender a implementar o reconhecimento de Face do Azure dentro de um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidade misturada, hololens de tutoriais, unity,
ms.openlocfilehash: 04ed2217c473c5649c1850fcc757d866e23b9b56
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730901"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>Módulo MR Learning Base - Solvers e o posicionamento de conteúdo dinâmico

Hologramas ganham vida no HoloLens 2 quando intuitivamente siga o usuário e são colocados no ambiente físico de uma maneira que torna a interação direta e elegante. Lição 3, vamos explorar maneiras de colocar dinamicamente hologramas usando ferramentas de posicionamento disponíveis do MRTK, conhecidas como "solvers". Elas são conhecidas como "solvers" para a maneira que elas solucionam algoritmos complexos posicionamento espacial. Em MRTK, solvers são um sistema de scripts e comportamentos que usamos para ser capaz de permitir que os elementos de interface do usuário a seguir você, o usuário ou outros objetos do jogo na cena. Eles podem também ser usados para ajustar a determinadas posições rapidamente, fazendo com que seu aplicativo mais intuitiva. 

## <a name="objectives"></a>Objetivos

* Introduzir solvers do MRTK
* O usuário execute as solvers de uso para ter uma coleção de botões
* Use solvers para ter um objeto do jogo siga mãos de rastreados do usuário

## <a name="instructions"></a>Instruções

### <a name="location-of-solvers-in-the-mrtk"></a>Local do solvers no MRTK
 Para localizar os solvers disponíveis em seu projeto, procure na pasta SDK MRTK (MixedRealityToolkit.SDK pasta), em seguida, sob a pasta utilitários você verá a pasta solvers, conforme mostrado na imagem abaixo.

![Solvers](images/lesson3_chapter1_step1im.PNG)

>Observação: Nesta lição apenas, passaremos pela implementação do solver "Orbital" e "RadialView" solver. Para saber mais sobre a gama completa de solvers disponíveis no MRTK, visite: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Use um solucionador de seguir o usuário
O objetivo deste capítulo é aprimorar a coleção de botões criada anteriormente, de modo que ele segue a direção de olhar do usuário. Na versão anterior do MRTK e HoloToolkit, isso era conhecido como uma funcionalidade "taglong".

1. Selecione o objeto de pai da coleção de botões na lição anterior.

![Lição 3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. No painel Inspetor, clique o botão "adicionar o componente" e pesquise por "orbital". O componente orbital deve aparecer. Selecione para adicionar o componente orbital ao objeto do jogo de coleção de botões.

![Lição 3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>Observação: Quando você adiciona o componente, você observará que o sistema adiciona o script orbital e o manipulador do solver na guia do Inspetor, o que é um componente necessário. 

3. Para configurar a coleção de botões para seguir o usuário, precisamos implementar os seguintes ajustes (também consulte a imagem abaixo):
- No script Orbital, defina a lista suspensa "tipo de orientação" para "Somente Yaw." Isso permite que, para que apenas um eixo do objeto gira conforme ele segue o usuário.
- Defina o deslocamento local como 0 em todos os eixos. Definir o deslocamento do mundo para x = 0, y =-0.1 e z = 0.6. Isso bloqueia a movimentação do objeto, de modo que quando o usuário altera a altura, o objeto permanecerá uma altura fixa no ambiente físico, enquanto ainda permite que ele siga o usuário quando o usuário se move sobre o ambiente. Esses valores podem ser ajustados para atingir um intervalo de wade de comportamentos.
- Para um comportamento de acompanhamento na qual os botões apenas siga a visão do usuário depois que o usuário virar a cabeça seu suficientemente bem, você pode selecionar a caixa de seleção "Usar a revisão de ângulo do deslocamento de mundo" (Observação: Este título pode ser truncado em algumas telas, como ele está na imagem abaixo.) Por exemplo, para que o objeto siga o usuário apenas a cada 90 graus, defina o número de etapas igual a 4 (marcado por uma seta verde no exemplo à esquerda). 

![Lição 3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Ativando objetos a seguir mãos controladas

Nesta seção, configuraremos o objeto do jogo cubo criado anteriormente para seguir as mãos rastreados do usuário, usando o solver RadialView.

1. Selecione o objeto de cubo na hierarquia de BaseScene. Clique em "Adicionar componente" no painel Inspetor. 

![Lição 3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. Digite "RadialView" na caixa de pesquisa e selecione o componente RadialView para adicioná-lo ao cubo. O componente de manipulador solver também será adicionado automaticamente ao cubo.

3. Altere a exibição radial para não seguem a cabeça, mas siga a mão esquerda. Selecione o menu suspenso ao lado da opção "controladas de objeto para fazer referência a". Em seguida, selecione "joint deixado de lado" no menu.

![Lição 3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. Depois de selecionar o conjunto de mão, você pode escolher qual parte da mão deseja que o cubo a seguir. Neste exemplo, vamos usar o pulso. Ao lado da opção "conjuntas de mão controladas" Selecione o menu suspenso e pulso. 

![Lição 3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. Defina as distâncias de mínimas e máxima como 0 para que o cubo não terá qualquer distância entre ele e o pulso do usuário. Depois de definido, o cubo será ser devidamente alinhado com o pulso. Você também pode ajustar o campo "Referência de direção" para ajustar o comportamento de como o cubo é orientado (por exemplo, se você gostaria de permitir que o objeto gira com pulso do usuário, defina a direção de referência para "Orientação com rastreadas o objeto")

![Lição 3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>Parabéns!
Parabéns! Nesta lição, você aprendeu a usar solvers do MRTK para ter uma interface do usuário intuitiva siga o usuário. Você também aprendeu como anexar um solucionador de um objeto do jogo (ou seja, o cubo) para seguir as mãos de rastreados do usuário. Para saber mais sobre esses e outros solvers incluídos com o MRTK, fique à vontade visitar o [página de documentação do MRTK solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Próxima lição: Interação do objeto 3D](mrlearning-base-ch4.md)


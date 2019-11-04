---
title: Menu do lado
description: Os menus à mão permitem que os usuários tragam rapidamente a interface do usuário conectada à mão para funções usadas com frequência. Essas são nossas práticas recomendadas e recomendações para menus à mão.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mão, menu, botão, acesso rápido, layout
ms.openlocfilehash: ee958806ac462535b33164bb4faa4bf1aa29e709
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439247"
---
# <a name="hand-menu"></a>Menu do lado

![Local do ulnar](images/MRTK_UX_HandMenu.png)

Os menus à mão permitem que os usuários tragam rapidamente a interface do usuário conectada à mão para funções usadas com frequência. 

Veja abaixo as práticas recomendadas que encontramos para os menus à mão. Você também pode encontrar uma cena de exemplo demonstrando o menu à mão em [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).

<br>

---

## <a name="behavior-best-practices"></a>Práticas recomendadas de comportamento
**A. Mantenha o número de botões pequenos:** devido à distância de proximidade entre um menu protegido por mão e os olhos, e também a tendência do usuário de se concentrar em uma área Visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), recomendamos mantendo o número de botões pequenos. Com base em nossa exploração, uma coluna com três botões funciona bem, mantendo todo o conteúdo dentro do campo de exibição (FOV), mesmo quando os usuários movem suas mãos para o centro do FOV. 

**B. Utilize o menu à mão para ação rápida:** gerar um ARM e manter a posição pode facilmente causar fadiga ARM. Use um método protegido por mão para o menu que requer uma pequena interação. Se o seu menu for complexo e exigir tempos de interação estendidos, considere usar o World-Locked ou o corpo bloqueado em vez disso. 

**C. botão/ângulo do painel:** os menus devem ser contratados em direção ao ressalto oposto e ao meio do cabeçalho: isso permite que uma mudança natural interaja com o menu com o lado oposto e evite qualquer posição de mão estranha ou desconfortável ao tocar botões. 

**D. considere o suporte a uma operação única ou viva-mão:** não presuma que as mãos do usuário estejam sempre disponíveis. Considere uma ampla gama de contextos quando um ou ambos os Hands não estiverem disponíveis e certifique-se de que suas contas de design para essas situações. Para dar suporte a um menu de mão única, você pode tentar fazer a transição do posicionamento do menu de bloqueio manual para mundo bloqueado quando a mão é invertida (vai para o Palm). Para cenários sem intervenção, considere usar um comando de voz para invocar os botões de menu do lado.

**Invocação de duas etapas:** se você usar apenas o Palm-up como um evento para disparar o menu à mão, ele poderá ser exibido acidentalmente quando você não precisar dele (falso-positivo), pois as pessoas movem suas mãos muito intencionalmente (para comunicação e manipulação de objetos) e não intencionalmente. Se você tiver falsos positivos em seu aplicativo, considere adicionar uma etapa adicional além do evento de palmeira para invocar o menu à mão, como dedos totalmente abertos.

**F. Evite adicionar botões próximos ao pulso (botão início do sistema):** se os botões do menu à mão estiverem posicionados muito próximos ao botão página inicial, ele poderá ser disparado acidentalmente ao interagir com o menu à mão.

**G. testar, testar, testar:** as pessoas têm corpos diferentes, com limites diferentes para conforto e discomfort, etc. Certifique-se de testar seu design e obter comentários de uma variedade de pessoas.

<br>

---

## <a name="hand-menu-placement-best-practices"></a>Práticas recomendadas de posicionamento do menu à mão

Na anatomia humana, o ulnar núcleo é um núcleo que é executado próximo ao Bone ulna. O ulna é um Bone longo encontrado no forearm que se estende do cotovelo para o menor dedo.

Abaixo estão dois posicionamentos recomendados com base em nossas explorações:


:::row:::
    :::column:::
        ![local do ulnar](images/UlnarSideHandMenu.gif)<br>
        **A. ulnar dentro do Palm**<br>
        Essa posição é confiável porque as mãos não se sobrepõem. Isso é essencial para a detecção e o acompanhamento precisos.
    :::column-end:::
    :::column:::
        ![local do ulnar](images/UlnarAboveHandMenu.gif)<br>
        **B. ulnar acima da mão**<br>
        Esse local é confortável para os usuários porque eles não precisam aumentar seu braço para interagir com o menu à mão. É recomendável colocar os menus **13cm** acima do Palm e alinhar os botões dentro do Palm ulnar. [Leia mais sobre o tamanho do botão ideal](interactable-object.md)<br>
        <br>
        Por motivos técnicos, recomendamos esse local com uma implementação necessária: o desenvolvedor precisará congelar o menu quando a mão oposta do usuário ficar próxima de interagir com ele. Isso evitará a tremulação de mãos sobrepostas e também permite um direcionamento mais rápido dos botões.<br>
        <br>
        As câmeras do HoloLens 2 identificam as mãos com precisão quando são separadas umas das outras. Qualquer mão sobreposta pode fazer com que os menus à mão se afastem do local de ancoragem.<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>Posições de menu que não são recomendadas
Fizemos a pesquisa de usuários com diferentes layouts e locais de menus, os locais de menu a seguir **não são recomendados**, encontre os contras de cada estudo abaixo:


:::row:::
    :::column:::
        ![](images/AboveArm.gif) do ARM<br>
        **Acima do ARM**<br>
        1-difícil de manter o acompanhamento de bom alcance<br>
        2-causa fadiga de usuário devido à posição não natural
    :::column-end:::
    :::column:::
        ![de dedos acima](images/AboveFingers.gif)<br>
        **Acima dos dedos**<br>
        fadiga de 1 mão devido à suspensão por muito tempo<br>
        problemas de acompanhamento de duas mãos no índice e no meio do dedo
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![](images/handCenter.gif) de Palm central<br>
        **Acima do centro-Palm**<br>
        problemas de acompanhamento de uma mão devido a sobreposição de mãos<br>
        fadiga de 2 mãos devido à suspensão de mãos por muito tempo para interagir com os menus
    :::column-end:::
    :::column:::
        ![superior](images/TopFingerTip.gif) **ponta**<br>
        problemas de acompanhamento de uma mão<br>
        fadiga de duas mãos mantendo a postura normal<br>
        3-problemas ao pressionar os botões com outros dedos por acidente devido ao espaço limitado entre os dedos
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![de trás do ARM](images/BackOfTheArm.gif)<br>
        **Trás do ARM**<br>
        1-pode disparar o botão página inicial por acidente<br>
        2-não é uma posição natural ou confortável para os usuários
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a>Consulte também

* [Objeto interativo](interactable-object.md)
* [Manipulação direta com as mãos](direct-manipulation.md)
* [Controladores de movimentos e mãos](hands-and-tools.md)

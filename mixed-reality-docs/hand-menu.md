---
title: Menu lateral
description: Os menus à mão permitem que os usuários tragam rapidamente a interface do usuário conectada à mão para funções usadas com frequência. Essas são nossas práticas recomendadas e recomendações para menus à mão.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mão, menu, botão, acesso rápido, layout
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061159"
---
# <a name="hand-menu"></a>Menu lateral

![Local do ulnar](images/UX/UX_Hero_HandMenu.jpg)

O menu à mão é um dos padrões mais exclusivos de UX no HoloLens 2. Ele permite que você traga rapidamente a interface do usuário anexada à mão. Como ele é acessível a qualquer momento e pode ser mostrado e ocultado facilmente, é ótimo para ações rápidas.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Você encontrará nossas práticas recomendadas para trabalhar com menus à mão na lista abaixo. Você também pode encontrar uma cena de exemplo demonstrando o menu à mão em [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).

<br>


---

## <a name="best-practices"></a>Práticas recomendadas
**Manter o número de botões pequenos** 

Devido à distância de proximidade entre um menu protegido por mão e os olhos, e também a tendência do usuário de se concentrar em uma área Visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), recomendamos manter o número de botões pequenos. Com base em nossa exploração, uma coluna com três botões funciona bem mantendo todo o conteúdo dentro do campo de exibição (FOV) mesmo quando um usuário move suas mãos para o centro do FOV. 

**Utilizar menu à mão para ação rápida** 

Elevar um ARM e manter a posição pode facilmente causar fadiga ARM. Use um método protegido por mão para o menu que requer uma pequena interação. Se o seu menu for complexo e exigir tempos de interação estendidos, considere usar o World-Locked ou o corpo bloqueado em vez disso. 

**Ângulo do botão/painel**

Os menus devem ser contratados em direção ao colado oposto e ao meio do cabeçalho: isso permite uma movimentação natural para interagir com o menu com o lado oposto e evita qualquer posição de mão estranha ou desconfortável ao tocar nos botões. 

**Considere dar suporte a uma operação única ou viva-mão**

Não presuma que as mãos do usuário estejam sempre disponíveis. Considere uma ampla gama de contextos quando um ou ambos os Hands não estiverem disponíveis e certifique-se de que suas contas de design para essas situações. Para dar suporte a um menu de mão única, você pode tentar fazer a transição do posicionamento do menu de bloqueio manual para mundo bloqueado quando a mão é invertida (vai para o Palm). Para cenários sem intervenção, considere usar um comando de voz para invocar o menu à mão.

**Evite adicionar botões próximos ao pulso (botão início do sistema)**

Se os botões do menu à mão forem colocados muito perto do botão página inicial, ele poderá ser disparado acidentalmente ao interagir com o menu da mão.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Menu à mão com controles de interface do usuário grandes e complexos
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
É recomendável limitar o número de botões ou controles de interface do usuário em menus anexados à mão. Isso ocorre porque a interação estendida com um grande número de elementos da interface do usuário pode causar fadiga ARM. Se sua experiência exigir um menu grande, forneça uma maneira fácil para o usuário para o mundo bloquear o menu. Uma técnica que recomendamos é bloquear, em seguida, o menu quando a mão cai ou sai do usuário. Uma segunda técnica é permitir que o usuário pegue diretamente o menu por outro lado. Quando o usuário libera o menu, o menu deve ser bloqueado pelo mundo. Dessa forma, um usuário pode interagir com vários elementos de interface de usuário confortavelmente e com confiança em um longo período de tempo. 

Quando o menu estiver bloqueado pelo mundo, certifique-se de fornecer uma maneira de mover o menu e fechar o menu quando ele não for mais necessário. Torne o menu móvel fornecendo identificadores nos lados ou no início do menu. Adicione um botão fechar para permitir que o menu seja fechado. Permita que o menu seja anexado novamente à mão quando o usuário se conectar ao usuário. Também é recomendável exigir que os usuários gazesm à sua mão para evitar ativações falsas (veja abaixo).

**Menu grande que mostra um problema de usabilidade**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**Menu suspenso ao lado do mundo**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Captura manual & pull para o mundo-bloquear o menu**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a>Como evitar a ativação falsa

Se você usar apenas o Palm-up como um evento para disparar o menu à mão, ele poderá parecer acidentalmente quando você não precisar dele (falso-positivo), pois as pessoas movem suas mãos de forma intencional (para a manipulação de comunicação e objeto) e não intencionalmente. Para reduzir as ativações falsas, adicione uma etapa adicional além do evento de Palm para invocar o menu à mão (como dedos totalmente abertos ou o usuário intencionalmente nuvens em sua mão).

**Exigir Palm simples**

Ao exigir uma mão aberta simples, você pode evitar a ativação falsa que pode ocorrer, pois o usuário manipula objetos ou gestos enquanto se comunica em um ambiente. 

**Exigir olhar**

Ao exigir que o usuário olhar a sua mão (com os olhos olhar ou Head olhar), ele impede as ativações falsas devido ao usuário precisar direcionar intencionalmente sua atenção para a mão como uma etapa de ativação secundária (com um limite de distância ajustável usado para permitir o conforto do usuário).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Práticas recomendadas de posicionamento do menu à mão

Na anatomia humana, o ulnar núcleo é um núcleo que é executado próximo ao Bone ulna. O ulna é um Bone longo encontrado no forearm que se estende do cotovelo para o menor dedo.

Abaixo estão dois posicionamentos recomendados com base em nossas explorações:


:::row:::
    :::column:::
        ![Local do ulnar](images/UlnarSideHandMenu.gif)<br>
        **A. ulnar dentro do Palm**<br>
        Essa posição é confiável porque as mãos não se sobrepõem. Isso é essencial para a detecção e o acompanhamento precisos.
    :::column-end:::
    :::column:::
        ![Local do ulnar](images/UlnarAboveHandMenu.gif)<br>
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
        ![Acima do ARM](images/AboveArm.gif)<br>
        **Acima do ARM**<br>
        1-difícil de manter o acompanhamento de bom alcance<br>
        2-causa fadiga de usuário devido à posição não natural
    :::column-end:::
    :::column:::
        ![Acima dos dedos](images/AboveFingers.gif)<br>
        **Acima dos dedos**<br>
        fadiga de 1 mão devido à falta de mão por muito tempo<br>
        problemas de acompanhamento de duas mãos no índice e nos dedos centrais
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Acima do centro do Palm](images/handCenter.gif)<br>
        **Acima do centro-Palm**<br>
        problemas de acompanhamento de uma mão devido a sobreposição de mãos<br>
        fadiga de 2 mãos devido à suspensão de mãos por muito tempo para interagir com os menus
    :::column-end:::
    :::column:::
        ![Topo ](images/TopFingerTip.gif) **superior** da ponta<br>
        problemas de acompanhamento de uma mão<br>
        fadiga de duas mãos da manutenção da postura normal<br>
        3-problemas ao pressionar os botões com outros dedos por acidente devido ao espaço limitado entre os dedos
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Trás do ARM](images/BackOfTheArm.gif)<br>
        **Trás do ARM**<br>
        1-pode disparar o botão página inicial por acidente<br>
        2-não é uma posição natural ou confortável
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Menu de mão no MRTK (Kit de ferramentas de realidade misturada) para Unity
O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e exemplos de cenas para o menu da mão. O script do resolvedor HandConstraintPalmUp permite que você anexe qualquer objeto às mãos com várias opções configuráveis. Os exemplos de menu do MRTK incluem opções úteis, como o requisito simples de Palm e olhar para impedir a ativação falsa.

* [Documentações de menus à mão](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [Cenário de exemplo do menu à mão](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

Você pode experimentar exemplos de menu à mão no HoloLens 2 com exemplos de MRTK aplicativo de Hub. 
* [Cena de menu do lado no Hub de exemplos do MRTK](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a>Consulte também

* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)

---
title: Foco com a cabeça e confirmação
description: Visão geral do modelo de entrada de foco com a cabeça e confirmação
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441090"
---
# <a name="head-gaze-and-commit"></a>Foco com a cabeça e confirmação
_Head-olhar e commit_ é um caso especial do modelo de entrada [olhar e commit](gaze-and-commit.md) que envolve o direcionamento de um objeto com a direção da sua cabeça apontando para a frente (direção da cabeça) e, em seguida, agindo com uma entrada secundária, como o gesto de toque à mão toque ou o comando de voz "Select". 

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Foco com a cabeça e confirmação</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado (terceira opção – <a href="interaction-fundamentals.md">confira as outras opções</a>)</td>
        <td>➕ Opção alternativa</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>Dimensionamento e comentários sobre o alvo
O vetor olhar de cabeçalho foi mostrado repetidamente para ser usado para direcionamento fino, mas geralmente funciona melhor para direcionamento bruto, adquirindo destinos um pouco maiores. Os tamanhos de destino mínimos de 1 a 1,5 graus permitem ações de usuário bem-sucedidas na maioria dos cenários, embora os destinos de 3 graus geralmente permitam maior velocidade. Observe que o tamanho do alvo escolhido pelo usuário é efetivamente uma área 2D até mesmo para elementos 3D – qualquer que seja a projeção que esteja voltada para eles deverá ser a área de alvo. Fornecer uma indicação evidente de que um elemento é "ativo" (que o usuário está direcionando para ele) é extremamente útil. Isso pode incluir tratamentos como efeitos "focalizar" visíveis, realces ou cliques de áudio ou alinhamento claro de um cursor com um elemento.

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho ideal do alvo em uma distância de 2 metros*

<br>

![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-940px.jpg)<br>
*Um exemplo de realce de um objeto direcionado por foco*

## <a name="target-placement"></a>Posicionamento do alvo
Geralmente, os usuários não conseguem localizar elementos da interface do usuário que estão posicionados muito altos ou muito baixos em seu campo de exibição, concentrando a maior parte de sua atenção em áreas em torno do foco principal, que é aproximadamente no nível dos olhos. O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar. Dada a tendência dos usuários de se concentrarem em uma área visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), o agrupamento de elementos de interface do usuário na medida em que eles estejam relacionados conceitualmente pode aproveitar os comportamentos de encadeamento da atenção de item a item conforme um usuário move o foco por uma área. Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.

![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Como melhorar os comportamentos de direcionamento
Se a intenção do usuário para o destino de algo puder ser determinada (ou aproximada), pode ser muito útil aceitar tentativas quase sem erros na interação, como se elas estivessem corretas. Aqui estão alguns métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:

### <a name="head-gaze-stabilization-gravity-wells"></a>Estabilização do foco com a cabeça ("poços gravitacionais")
Isso deve ser ativado na maior parte das vezes. Essa técnica remove a cabeça natural e as tremulações do pescoço que os usuários podem ter também movimento devido a comportamentos de aparência e fala.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo mais próximo
Eles funcionam melhor em áreas com conteúdo interativo esparso. Se houver uma alta probabilidade de que você possa determinar o que um usuário estava tentando interagir, você pode complementar seus recursos de direcionamento assumindo algum nível de intenção.

### <a name="backdating-and-postdating-actions"></a>Ações de backencontros e de reencontros
Esse mecanismo é útil para tarefas que exigem velocidade. Quando um usuário passa por uma série de manobras de direcionamento e ativação em velocidade, é útil assumir alguma intenção e permitir que as etapas perdidas atuem em destinos que o usuário tinha em foco ligeiramente antes ou ligeiramente após o toque (50 ms antes/depois era efetivo em ea teste de Rly).

### <a name="smoothing"></a>Suavização
Esse mecanismo é útil para a trajetória de movimentos, reduzindo a ligeira tremulação e Wobble devido a características de movimento de cabeçalho natural. Ao suavizar movimentos de caminho, Smooth pelo tamanho e distância dos movimentos em vez de ao longo do tempo.

### <a name="magnetism"></a>Magnetismo
Esse mecanismo pode ser considerado como uma versão mais comum dos algoritmos de link mais próximos – desenhar um cursor em direção a um destino ou simplesmente aumentar o hitboxes, seja visivelmente ou não, à medida que os usuários abordam os alvos prováveis usando algum conhecimento do layout interativo para melhor objetivo de usuário da abordagem. Isso pode ser particularmente eficiente para alvos pequenos.

### <a name="focus-stickiness"></a>Adesão do foco
Ao determinar a quais elementos interativos próximos dar foco, a adesão do foco fornece uma tendência para o elemento que está atualmente focado. Isso ajuda a reduzir os comportamentos incorretos de alternância de foco ao flutuar em um ponto médio entre dois elementos com ruído natural.


## <a name="see-also"></a>Consulte também
* [Interação com base nos olhos](eye-gaze-interaction.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Manipulação de mãos direta](direct-manipulation.md)
* [Gestos práticos](gaze-and-commit.md#composite-gestures)
* [Ponto de mãos e confirmação](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)




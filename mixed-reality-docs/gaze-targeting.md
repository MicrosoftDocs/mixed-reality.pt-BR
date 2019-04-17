---
title: Mantenha o foco de direcionamento
description: Todas as interações baseiam-se a capacidade de um usuário para o elemento que eles querem interagir, independentemente da modalidade de entrada de destino.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realidade, olhar, olhar direcionamento, interação, de design
ms.openlocfilehash: c3225e27331f8afcda65469eb84fe5470bf6ee8c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589708"
---
# <a name="gaze-targeting"></a>Mantenha o foco de direcionamento

Todas as interações baseiam-se a capacidade de um usuário para o elemento que eles querem interagir, independentemente da modalidade de entrada de destino. Na realidade mista do Windows, isso geralmente é feito usando olhar do usuário.

Para habilitar um usuário trabalhar com uma experiência com êxito, as Noções básicas sobre calculado do sistema de intenção do usuário e a intenção do usuário real, deve se alinhar o mais próximo possível. Para o grau que o sistema interpreta as ações do usuário pretendida corretamente, aumenta a satisfação e o desempenho melhora.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> Mantenha o foco de direcionamento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️ </td>
</tr><tr>
<td> Direcionamento de olhos</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

## <a name="target-sizing-and-feedback"></a>Comentários e dimensionamento de destino

O vetor de olhar mostrado repetidamente para ser usado para direcionar tudo bem, mas geralmente funciona melhor para brutos direcionamento (ao adquirir um pouco maiores destinos). Tamanhos de destino mínimo de 1 a 1,5 graus devem permitir que as ações do usuário bem-sucedida na maioria dos cenários, embora normalmente permitem destinos de graus de 3 para maior velocidade. Observe que o tamanho que os destinos de usuário é efetivamente uma área 2D até mesmo para elementos 3D – qualquer projeção é voltado para a eles deve ser a área a ser direcionada. Fornecer alguma indicação evidente que um elemento está "ativo" (que o usuário está direcionando-la) é extremamente útil – isso pode incluir tratamentos como efeitos de "passagem" visível, destaques de áudio ou cliques ou desmarque o alinhamento de um cursor com um elemento.

![Tamanho de destino ideal a distância do medidor 2](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho de destino ideal a distância do medidor 2*

![Um exemplo de realce de um objeto de destino de olhar](images/gazetargeting-highlighting-640px.jpg)<br>
*Um exemplo de realce de um objeto de destino de olhar*

## <a name="target-placement"></a>Posicionamento de destino

Os usuários geralmente não encontrarão encontrar elementos de interface do usuário são posicionados muito alto ou muito baixo em seu campo de visão, concentrando-se a maior parte de sua atenção nas áreas em torno de seu foco principal (geralmente aproximadamente nível dos olhos). Pode ajudar a colocar a maioria dos destinos em alguns banda razoável em torno do nível dos olhos. Dada a tendência para os usuários para se concentrar em uma área visual relativamente pequena a qualquer momento (attentional cone de visão é aproximadamente 10 graus), agrupar elementos de interface do usuário para o grau que elas estão relacionadas conceitualmente pode aproveitar comportamentos de encadeamento de atenção do item a item como um usuário move seu olhar por meio de uma área. Ao projetar a interface do usuário, tenha em mente a variação grande potencial no campo de exibição entre HoloLens e fones imersivos em exposição.

![Um exemplo dos elementos de interface do usuário agrupados para olhar mais fáceis de direcionamento no Explorer Galaxy](images/gazetargeting-grouping-1000px.jpg)<br>
*Um exemplo dos elementos de interface do usuário agrupados para olhar mais fáceis de direcionamento no Explorer Galaxy*

## <a name="improving-targeting-behaviors"></a>Melhorando a comportamentos de direcionamento

Se a intenção do usuário para algo de destino pode ser determinada (ou aproximada de perto), ele pode ser muito útil aceitar "near Srta" tenta a interação como se eles foram direcionados corretamente. Há um punhado de métodos bem-sucedidas que podem ser incorporados em experiências de realidade mista:

### <a name="gaze-stabilization-gravity-wells"></a>Estabilização olhar ("wells gravidade")

Essa deve ser ligado a maioria ou todos do tempo. Essa técnica remove os jitters head/pescoço natural que os usuários podem ter. Também movimento devido a comportamentos de busca/falando.

### <a name="closest-link-algorithms"></a>Algoritmos mais próximo do link

Eles funcionam melhor em áreas com conteúdo interativo esparsa. Se houver uma grande probabilidade de que você pode determinar o que um usuário estava tentando interagir com, você pode complementar suas habilidades de direcionamento por simplesmente supondo que algum nível de intenção.

### <a name="backdatingpostdating-actions"></a>Ações backdating/postdating

Esse mecanismo é útil para tarefas que precisam de velocidade. Quando um usuário está se movendo por meio de uma série de direcionamento/ativação evasivas na velocidade, pode ser útil a assumir algum intenção e permitir *perdeu etapas* para atuar em destinos que o usuário tinha em foco um pouco antes ou depois de um pouco o tap ( 50 ms antes/depois foi eficaz em testes iniciais).

### <a name="smoothing"></a>Suavização

Esse mecanismo é útil para movimentos de caminhos, reduzindo a tremulação/wobble pequena devido às características de movimentação do cabeçote natural. Quando a suavização ao longo de movimentos de caminhos, suaves por tamanho/distância de movimentos em vez de ao longo do tempo

### <a name="magnetism"></a>Magnetism

Esse mecanismo pode ser pensado como uma versão mais geral de algoritmos "Vincular mais próximo" - desenhar um cursor em direção a um destino ou simplesmente aumentar hitboxes (seja visivelmente ou não) como os usuários provavelmente destinos de abordagem, usando algum conhecimento sobre o layout interativo para intenção do usuário abordagem melhor. Isso pode ser particularmente poderoso para destinos pequeno.

### <a name="focus-stickiness"></a>Adesão de foco

Ao determinar qual próximos elementos interativos para dar o foco para o, forneça uma tendência para o elemento que tem o foco. Isso ajudará a reduzir o foco irregular alternância comportamentos quando flutuante em um ponto médio entre dois elementos com ruído natural.

## <a name="see-also"></a>Consulte também
* [Gestos](gestures.md)
* [Design de voz](voice-design.md)
* [Cursores](cursors.md)

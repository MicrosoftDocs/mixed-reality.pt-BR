---
title: Direcionamento olhar
description: Todas as interações baseiam-se na capacidade de um usuário direcionar seu foco para o elemento com o qual deseja interagir, independentemente da modalidade de entrada.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, olhar, direcionamento olhar, interação, design
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829844"
---
# <a name="gaze-and-dwell"></a>Olhar e a pesquisa
Há várias maneiras diferentes de confirmar uma _confirmação_ , como combinar olhar com gestos de _voz_ ou _mão_.
No entanto, há vários cenários de usuário, nos quais as mãos dos usuários podem estar ocupadas ou não podem ser controladas (por exemplo, funcionários de fábrica com luvas de imposto pesado muito grandes). A entrada de voz também pode não estar disponível devido a preferências do usuário, contexto social ou ambientes altos.
Como uma solução de fallback, outra opção para executar uma _confirmação_ é simplesmente manter a estrela em um elemento de interface do usuário que nos referimos como uma _pesquisa_.
Uma _pesquisa_ pode ser executada com olhar de cabeça ou de olho. A ideia é simples e pode ser dividida nas seguintes fases: 
1. O usuário inicia o nuvens em um botão Holographic

2. Após um breve atraso de início (por exemplo, 150 ms), algumas animações de comentários visuais são iniciadas. O atraso de início é usado para evitar sobrecarregar o usuário imediatamente ao mesmo tempo.
    - Para _olhar de olho_, recomendamos o seguinte para o design dos comentários sobre a pesquisa Visual:
      - **Misturar**: Mescle suavemente os comentários do mal visíveis a princípio para totalmente opaco. Isso torna os comentários menos confusos e overwhlemings e alinha-se perfeitamente com a confiança que o sistema tem que o usuário realmente deseja envolver com esse botão.
      - Efetuar **pull**: Crie um comentário visual que diminui em tamanho e se move para o centro do destino, puxando a atenção visual do usuário. 

3. Após uma duração de uma pesquisa predefinida (por exemplo, 800 MS), a pesquisa é concluída e um evento associado é disparado.
    - Forneça alguns comentários de auditoria ou visuais finais para realmente colocar em casa que o item foi selecionado agora.

![Estados de pesquisa](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>Direcionamento olhar

Todas as interações baseiam-se na capacidade de um usuário direcionar seu foco para o elemento com o qual deseja interagir, independentemente da modalidade de entrada. No Windows Mixed Reality, isso geralmente é feito com o foco do usuário.

Para permitir que um usuário trabalhe com uma experiência bem-sucedida, o entendimento calculado do sistema da intenção de um usuário e a intenção real do usuário devem estar os mais alinhados possíveis. Na medida em que o sistema interpreta as ações pretendidas do usuário corretamente, a satisfação e o desempenho melhoram.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Direcionamento olhar</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Direcionamento de olho</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Mais diretrizes específicas para o HoloLens 2 em [breve](index.md).

## <a name="target-sizing-and-feedback"></a>Dimensionamento e comentários sobre o alvo

O vetor de foco demonstrou repetidamente ser utilizável para o direcionamento refinado, mas geralmente funciona melhor para o direcionamento bruto (adquirindo, de certa forma, alvos maiores). Os tamanhos mínimos do alvo de 1 a 1,5 grau devem permitir ações bem-sucedidas do usuário na maioria dos cenários, embora os alvos de 3 graus normalmente permitam uma maior velocidade. Observe que o tamanho do alvo escolhido pelo usuário é efetivamente uma área 2D até mesmo para elementos 3D – qualquer que seja a projeção que esteja voltada para eles deverá ser a área de alvo. O fornecimento de alguma indicação evidente de que um elemento está "ativo" (ao qual o usuário está direcionando o foco) é extremamente útil – isso pode incluir tratamentos como efeitos de "focalização" visíveis, destaques de áudio ou cliques ou alinhamento claro de um cursor com um elemento.

![Tamanho ideal do alvo em uma distância de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamanho ideal do alvo em uma distância de 2 metros*

![Um exemplo de realce de um objeto direcionado por foco](images/gazetargeting-highlighting-640px.jpg)<br>
*Um exemplo de realce de um objeto direcionado por foco*

## <a name="target-placement"></a>Posicionamento do alvo

Em geral, os usuários não encontrarão elementos de interface do usuário posicionados muito acima ou muito abaixo de seu campo de visão, concentrando a maior parte de sua atenção nas áreas em torno de seu foco principal (em geral, aproximadamente no nível dos olhos). O posicionamento da maioria dos alvos em uma faixa razoável em torno do nível dos olhos pode ajudar. Dada a tendência dos usuários de se concentrarem em uma área visual relativamente pequena a qualquer momento (o cone de atenção da visão é de aproximadamente 10 graus), o agrupamento de elementos de interface do usuário na medida em que eles estejam relacionados conceitualmente pode aproveitar os comportamentos de encadeamento da atenção de item a item conforme um usuário move o foco por uma área. Ao projetar a interface do usuário, tenha em mente a grande variação potencial no campo de visão entre o HoloLens e os headsets imersivos.

![Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Um exemplo de elementos de interface do usuário agrupados para um direcionamento do foco mais fácil no Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Como melhorar os comportamentos de direcionamento

Se a intenção do usuário de direcionar o foco para algo puder ser determinada (ou aproximada), poderá ser muito útil aceitar tentativas "quase certas" na interação como se elas tivessem sido direcionadas corretamente. Há diversos métodos bem-sucedidos que podem ser incorporados em experiências de realidade misturada:

### <a name="gaze-stabilization-gravity-wells"></a>Estabilização de olhar ("gravidade caixas")

Isso deve estar ligado na maior parte do tempo ou todo o tempo. Essa técnica remove as tremulações naturais da cabeça/do pescoço que os usuários possam ter. Além disso, o movimento devido a comportamentos de visão/fala.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo mais próximo

Eles funcionam melhor em áreas com conteúdo interativo esparso. Se houver uma grande probabilidade de que você determine com o que um usuário estava tentando interagir, você poderá complementar suas habilidades de direcionamento apenas supondo algum nível de intenção.

### <a name="backdatingpostdating-actions"></a>Ações de antedatar/pós-datar

Esse mecanismo é útil para tarefas que exigem velocidade. Quando um usuário passa por uma série de manobras de direcionamento/ativação em velocidade, pode ser útil assumir alguma intenção e permitir que *as etapas perdidas* atuem em destinos que o usuário tinha em foco um pouco antes ou ligeiramente após o toque (50 ms antes/depois foi eficaz em testes iniciais).

### <a name="smoothing"></a>Suavização

Esse mecanismo é útil para movimentos de caminhos, reduzindo leve tremulação/tremor devido às características de movimentação natural da cabeça. Durante a suavização em movimentos de caminhos, aplique a suavização por tamanho/distância de movimentos em vez de ao longo do tempo

### <a name="magnetism"></a>Magnetismo

Esse mecanismo pode ser considerado uma versão mais geral dos algoritmos de "Vínculo mais próximo" – desenhar um cursor em direção a um alvo ou apenas aumentar os hitboxes (seja visivelmente ou não) conforme os usuários se aproximam de prováveis alvos, usando algum conhecimento sobre o layout interativo para uma melhor abordagem da intenção do usuário. Isso pode ser particularmente eficiente para alvos pequenos.

### <a name="focus-stickiness"></a>Adesão do foco

Ao determinar a quais elementos interativos nas proximidades o foco deve ser dado, forneça um desvio para o elemento que tem o foco atualmente. Isso ajudará a reduzir os comportamentos de alternância de foco instável durante a flutuação em um ponto médio entre dois elementos com ruído natural.

## <a name="see-also"></a>Consulte também
* [Gestos](gestures.md)
* [Comando de voz](voice-design.md)
* [Cursores](cursors.md)

---
title: Escala
description: A chave para exibir o conteúdo que se parece realista na forma holográfica é para simular as estatísticas de visual do mundo real mais próximo possível.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Design do Windows Mixed Reality, estilo,
ms.openlocfilehash: f13414bff7d84692e8e87aa2abdcded15627346f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589355"
---
# <a name="scale"></a>Escala

A chave para exibir o conteúdo que se parece realista na forma holográfica é para simular as estatísticas de visual do mundo real mais próximo possível. Isso significa incorporar como muitas das indicações visuais que pudermos que nos (no mundo real) ajudam a entender onde os objetos são, quão grande que eles são e o que eles composto. A escala de um objeto é um dos mais importantes desses visuais, dando uma ideia do tamanho de um objeto, bem como dicas de um visualizador para seu local (especialmente para objetos que têm um tamanho conhecido). Além disso, exibindo objetos em escala real é visto como um dos principais experiência diferenciadores para realidade misturada em geral – algo que não era possível em baseado em tela exibindo anteriormente.

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Como sugerir a escala dos ambientes e objetos

Há várias maneiras para sugerir a escala de um objeto, algumas das quais com possíveis efeitos em outros fatores de percepção. A chave é simplesmente exibir objetos em um tamanho de 'real' e manter esse tamanho realista à medida que os usuários navegam. Isso significa hologramas ocupar uma quantidade diferente de ângulo visual de um usuário de um usuário conforme eles entram mais próximo ou mais distante, da mesma maneira que objetos reais.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Utilizar a distância dos objetos que são apresentados ao usuário

Um método comum é utilizar a distância dos objetos que são apresentados ao usuário. Por exemplo, considere a possibilidade de visualizar um carro família grande na frente do usuário. Se o carro foram diretamente na frente delas, no comprimento do arm, seria muito grande para caber no campo de visão do usuário. Isso exigiria que o usuário mova seu cabeçalho e corpo para entender a totalidade do objeto. Se o carro foram colocado adicional imediatamente (dentro de uma sala), o usuário pode estabelecer um senso de escala vendo a totalidade do objeto em seu campo de visão, movendo próprios mais próximo a ele para inspecionar as áreas em detalhes.

[Volvo](https://www.youtube.com/watch?v=DilzwF90vec) usou essa técnica para criar uma experiência de sala de exposições para um novo carro, utilizando a escala do carro holográfica de forma que exigiam realista e intuitiva para o usuário. A experiência começa com um holograma do carro em uma tabela física, permitindo que o usuário entender o tamanho total e a forma do modelo. Mais tarde na experiência, o carro se expande para uma escala maior (além do tamanho do campo de visão do dispositivo), mas, desde que o usuário já adquiriu um quadro de referência do modelo menor, eles poderão navegar adequadamente com base em recursos do carro.

![Experiência de carros Volvo para HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
*Experiência de carros Volvo para HoloLens*

### <a name="use-holograms-to-modify-the-users-real-space"></a>Use hologramas para modificar o espaço de real do usuário

Outro método é usar hologramas para modificar o espaço real do usuário, substituindo as paredes ou tetos existente com os ambientes ou acrescentar 'buracos' ou 'windows', permitindo que objetos superdimensionados para aparentemente 'break-through' o espaço físico. Por exemplo, uma grande árvore talvez não caibam em salas de estar a maioria dos usuários, mas colocando um céu virtual em seu limite máximo, o espaço físico expande em virtual. Isso permite que o usuário sair andando com a base da árvore virtual e reunir um senso de escala de como ele seria aparecem na vida real, em seguida, pesquisar para vê-lo a se estender bem além do espaço físico da sala.

[Minecraft](https://minecraft.net/) desenvolveu uma experiência de conceito usando uma técnica semelhante. Adicionando uma janela virtual a uma superfície física em uma sala, os objetos existentes na sala são colocados no contexto de um ambiente muito maior, além das limitações físicas de escala da sala.

![Experiência do conceito de Minecraft para HoloLens](images/800px-minecraftwindow-640px.jpg)<br>
*Experiência do conceito de Minecraft para HoloLens*

## <a name="experimenting-with-scale"></a>Experimentar a escala

Em alguns casos, os designers tem experiência com a modificação de escala (alterando o tamanho exibido 'real' do objeto), mantendo uma única posição do objeto, para aproximar a um objeto obtendo mais próximo ou posteriormente a um visualizador sem qualquer movimentação real. Isso foi testado em alguns casos, como uma maneira de simular os detalhes sobre exibição de itens enquanto ainda respeitam possíveis limitações de conforto de exibição virtual conteúdo mais próximo do que "zona de conforto" poderia sugerir.

No entanto isso pode criar alguns artefatos possíveis na experiência:
* Para objetos virtuais que representam alguns objetos com um tamanho de 'conhecido' para o visualizador, a alteração da escala sem alterar a posição leva a conflitantes indicações visuais – os olhos ainda podem ser 'ver' o objeto em algum nível de profundidade devido a indicações vergence (consulte a [conforto ](comfort.md) artigo para saber mais sobre isso), mas o tamanho atua como uma indicação monocular que o objeto pode estar obtendo mais próximo. Essas indicações conflitantes levam a percepções confusos – visualizadores geralmente verá o objeto como manter-se em vigor (devido a sinalização de profundidade constante), mas crescendo rapidamente.
* Em alguns casos, a alteração da escala é vista como uma indicação 'looming' em vez disso, em que o objeto pode ou não pode ser visto para alterar a escala por um visualizador, mas parece ser mudar diretamente para os olhos do visualizador (que podem ser uma sensação desconfortável).
* Com superfícies de comparação no mundo real, essas alterações de dimensionamento são às vezes, vistas que a alteração de posição ao longo de vários eixos – objetos podem aparecer descartar inferior, em vez de ficar mais perto (semelhante uma projeção 2D do movimento 3D em alguns casos).
* Por fim, para objetos sem um tamanho conhecido 'reais' (formas arbitrárias, por exemplo, com tamanhos arbitrários, elementos de interface do usuário, etc.), a alteração da escala pode agir funcionalmente como uma maneira de simular alterações na distância – visualizadores não têm tantos preexistentes indicações de cima para baixo pela qual Entenda o tamanho real do objeto ou o local, para que a escala pode ser processada como uma indicação mais importante.

## <a name="see-also"></a>Consulte também
* [Cor, luz e materiais](color,-light-and-materials.md)
* [Tipografia](typography.md)
* [Design de som espacial](spatial-sound-design.md)

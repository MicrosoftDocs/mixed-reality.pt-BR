---
title: Escala
description: Para exibir conteúdo com aparência realista no formulário holográfico é fundamental imitar, do modo mais próximo possível, as estatísticas visuais do mundo real.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, estilo, design
ms.openlocfilehash: eeec28fbf98cf4386a57cde4452cd3f8977d7780
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437511"
---
# <a name="scale"></a>Escala

Para exibir conteúdo com aparência realista no formulário holográfico é fundamental imitar, do modo mais próximo possível, as estatísticas visuais do mundo real. Isso significa incorporar o máximo de dicas visuais que podem nos ajudar (no mundo real) a entender onde estão os objetos, quão grandes são e do que eles são feitos. A escala de um objeto é uma das mais importantes das indicações visuais, dando a um visualizador um sentido do tamanho de um objeto, bem como de indicações para seu local (especialmente para objetos que têm um tamanho conhecido). Além disso, a exibição de objetos em escala real foi vista como um dos principais diferenciais de experiência para a realidade misturada em geral – algo que não era possível na exibição baseada em tela anteriormente.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Como sugerir a escala de objetos e ambientes

Há várias maneiras de sugerir a escala de um objeto, alguns dos quais têm possíveis efeitos em outros fatores de perceptiva. A chave a é simplesmente exibir objetos com um tamanho "real" e manter esse tamanho realista à medida que os usuários se movem. Isso significa que os hologramas ocuparão uma quantidade diferente do ângulo visual do usuário de um usuário à medida que eles ficarem mais próximos ou mais distantes, da mesma forma que os objetos reais.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Utilize a distância dos objetos conforme eles são apresentados ao usuário

Um método comum é utilizar a distância dos objetos conforme eles são apresentados ao usuário. Por exemplo, considere a visualização de um carro de família grande na frente do usuário. Se o carro estivesse diretamente em frente, dentro do comprimento do ARM, seria muito grande para caber no campo de exibição do usuário. Isso exige que o usuário mova a cabeça e o corpo para entender todo o objeto. Se o carro fosse colocado mais distante (em toda a sala), o usuário pode estabelecer uma noção de escala ao ver todo o objeto em seu campo de exibição e, em seguida, se aproximar mais perto dele para inspecionar áreas em detalhes.

:::row:::
    :::column:::
        A **[Volvo usou essa técnica para criar uma](https://www.youtube.com/watch?v=DilzwF90vec)** experiência de showroom para um novo carro, utilizando a escala do carro Holographic de uma forma que parecia realista e intuitiva ao usuário. A experiência começa com um holograma do carro em uma tabela física, permitindo que o usuário entenda o tamanho total e a forma do modelo. Mais tarde, na experiência, o carro se expande para uma escala maior (além do tamanho do campo de exibição do dispositivo), mas, como o usuário já adquiriu um quadro de referência do modelo menor, ele pode navegar adequadamente pelos recursos do carro.<br>
        <br>
        *Imagem: experiência de carros Volvo para o HoloLens*
    :::column-end:::
        :::column:::
       ![Experiência de carros Volvo para o HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usar hologramas para modificar o espaço real do usuário

Outro método é usar hologramas para modificar o espaço real do usuário, substituindo as paredes ou os tetos existentes por ambientes ou acrescentando "buracos" ou "Windows", permitindo que os objetos de tamanho mais longo pareçam "dividir" o espaço físico. Por exemplo, uma árvore grande pode não se ajustar à maioria das salas de vida dos usuários, mas ao colocar um céu virtual em seu teto, o espaço físico se expande para a máquina virtual. Isso permite que o usuário percorra a base da árvore virtual e reúna uma noção de como ela seria exibida na vida real e, em seguida, veja que ela se estende muito além do espaço físico da sala.

:::row:::
    :::column:::
        **[Minecraft desenvolveu uma experiência de conceito](https://minecraft.net/)** usando uma técnica semelhante. Ao adicionar uma janela virtual a uma superfície física em uma sala, os objetos existentes na sala são colocados no contexto de um ambiente amplamente maior, além das limitações de escala física da sala.<br>
        <br>
        *Imagem: experiência de conceito de Minecraft para o HoloLens*
    :::column-end:::
        :::column:::
       ![Experiência de conceito de Minecraft para o HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Experimentando a escala

Em alguns casos, os designers experimentaram modificar a escala (alterando o tamanho ' real ' exibido do objeto) mantendo, ao mesmo tempo, uma única posição do objeto para aproximar um objeto que está ficando mais próximo ou mais de um visualizador sem qualquer movimento real. Isso foi testado em alguns casos como uma maneira de simular a visualização de itens e, ao mesmo tempo, respeitar possíveis limitações de conforto de exibir conteúdo virtual mais próximo do que a "zona de conforto" sugere.

No entanto, isso pode criar alguns artefatos possíveis na experiência:
* Para objetos virtuais que representam algum objeto com um tamanho "conhecido" para o visualizador, alterar a escala sem alterar a posição leva a indicações visuais conflitantes – os olhos ainda podem "ver" o objeto em alguma profundidade devido a indicações de Vergence (consulte o [conforto](comfort.md) artigo para obter mais informações sobre isso), mas o tamanho atua como uma indicação monocular de que o objeto pode estar ficando mais próximo. Essas indicações conflitantes levam a percepções confusas – os visualizadores geralmente veem o objeto como estando em vigor (devido à indicação de profundidade constante), mas crescendo rapidamente.
* Em alguns casos, a alteração de escala é vista como uma indicação ' surgindo ', em que o objeto pode ou não ser visto para alterar a escala por um visualizador, mas parece estar se movendo diretamente para os olhos do visualizador (o que pode ser um sensação desconfortável).
* Com superfícies de comparação no mundo real, tais alterações de dimensionamento às vezes são vistas como alteração na posição ao longo de vários eixos. os objetos podem parecer mais baixos em vez de avançar (semelhante em uma projeção 2D do movimento 3D em alguns casos).
* Por fim, para objetos sem um tamanho "Real World" conhecido (por exemplo, formas arbitrárias com tamanhos arbitrários, elementos de interface do usuário, etc.), a escala de alteração pode funcionar funcionalmente como uma forma de imitar alterações em distância – os visualizadores não têm tantas indicações de cima para baixo pré-existentes pelas quais Entenda o tamanho ou o local verdadeiro do objeto, para que a escala possa ser processada como uma indicação mais importante.

<br>

---

## <a name="see-also"></a>Consulte também
* [Cor, luz e materiais](color,-light-and-materials.md)
* [Tipografia](typography.md)
* [Projeto de som espacial](spatial-sound-design.md)

---
title: Apontar e confirmar com as mãos
description: Visão geral do modelo de entrada de apontar e confirmar
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade misturada, interação, design, hololens, mãos, à distância, apontar e confirmar
ms.openlocfilehash: 30f85d2bb455abab3a533e0a829b4fba8cea0a7a
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402378"
---
# <a name="point-and-commit-with-hands"></a>Apontar e confirmar com as mãos
Apontar e confirmar com as mãos é um modelo de entrada que permite aos usuários focalizar, selecionar e manipular objetos 3D e conteúdo 2D à distância. Essa técnica de interação "à distância" é exclusiva da realidade misturada e não é uma forma natural de interação humana com o mundo real. Por exemplo, no filme de super-heróis *X-Men*, o personagem [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) é capaz de pegar e manipular um objeto à distância com suas mãos. Isso não é algo que os humanos podem fazer na realidade. No HoloLens (RA) e na Realidade misturada (VR), nós equipamos os usuários com esse poder mágico, quebrando a restrição física do mundo real para não somente permitir uma experiência divertida com o conteúdo holográfico, como também tornar a interação mais eficaz e eficiente.

## <a name="device-support"></a>Suporte a dispositivos

Modelo de entrada | [HoloLens (1ª geração)](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [Headsets imersivos](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
Apontar e confirmar com as mãos | ❌ Sem suporte | ✔️ Recomendado | ✔️ Recomendado

O modelo Apontar e confirmar, também conhecido como mãos à distância, é um dos novos recursos que utiliza o novo sistema articulado de acompanhamento da mão. Esse modelo de entrada também é o modelo de entrada primário em headsets imersivos com o uso de controladores de movimento.

## <a name="hand-rays"></a>Raios de mão

No HoloLens 2, criamos um raio de mão que é disparado do centro da palma da mão. Este raio é tratado como uma extensão da mão. Um cursor em forma de rosca é anexado ao final do raio para indicar o local onde o raio cruza com um objeto-alvo. O objeto sobre o cursor pode receber comandos gestuais da mão.

Esse comando gestual básico é disparado usando o polegar e o dedo indicador para executar uma ação de fechar e abrir os dedos indicador e polegar. Usando o raio de mão para apontar e a ação de fechar e abrir os dedos indicador e polegar para confirmar, os usuários podem ativar um botão ou um hiperlink em um conteúdo da Web. Com gestos mais complexos, os usuários podem navegar pelo conteúdo da Web e manipular objetos 3D à distância. O design visual do raio de mão também deve reagir com esses estados de apontar e confirmar, conforme descrito e mostrado abaixo: 

* Ao *apontar*, o raio é mostrado como uma linha tracejada e o cursor assume a forma de uma rosca.
* Ao *confirmar*, o raio se transforma em uma linha sólida e o cursor se reduz a um ponto.

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>Transição entre próximo e distante

Em vez de usar um gesto específico, como "apontar com o dedo indicador" para direcionar o raio, projetamos o raio de modo a sair do centro da palma da mão, liberando e reservando os cinco dedos para gestos mais manipulativos, como pinçar e segurar. Com esse design, podemos criar um só modelo mental, dando suporte a exatamente o mesmo conjunto de gestos de mão para uma interação próxima e distante. Você pode usar o mesmo gesto de captura para manipular objetos em distâncias diferentes. A invocação dos raios é automática e baseada na proximidade:

*  Quando um objeto está dentro da distância de alcance do braço (aproximadamente 50 cm), os raios são desativados automaticamente, incentivando a interação próxima.
*  Quando o objeto está mais distante do que 50 cm, os raios são ativados. A transição deve ser simples e direta.

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>Interação do slate 2D

Um slate 2D é um contêiner holográfico que hospeda o conteúdo do aplicativo 2D, como um navegador da Web. O conceito de design da interação distante com um slate 2D é usar os raios de mão para focalizar e fechar e abrir os dedos indicador e polegar para selecionar. Após focalizar com um raio de mão, os usuários podem fechar e abrir os dedos indicador e polegar para disparar um hiperlink ou um botão. Eles podem usar uma mão para "fechar e abrir os dedos indicador e polegar" para rolar o conteúdo de um slate para cima e para baixo. O movimento relativo do uso das duas mãos para fechar e abrir os dedos indicador e polegar e arrastar pode aumentar e diminuir o zoom do conteúdo do slate.

Focalizar o raio de mão nos cantos e bordas revela a funcionalidade de manipulação mais próxima. Ao "segurar e arrastar" as funcionalidades de manipulação, os usuários podem realizar o dimensionamento uniforme utilizando as funcionalidades de canto, e refluir o slate utilizando as funcionalidades de borda. Ao segurar e arrastar a barra holográfica na parte superior do slate 2D, os usuários podem mover todo o slate.

![](images/2D-Slate-Interaction-Far-720px.jpg)

Para manipular o slate 2D em si:<br>

* Os usuários apontam o raio de mão para os cantos ou bordas para revelar a funcionalidade de manipulação mais próxima. 
* Aplicando um gesto de manipulação na funcionalidade, os usuários podem realizar o dimensionamento uniforme utilizando a funcionalidade de canto, e podem refluir o slate utilizando a funcionalidade de borda. 
* Aplicando um gesto de manipulação na barra holográfica na parte superior do slate 2D, os usuários podem mover todo o slate.<br>

<br>

## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D

Na manipulação direta, há duas maneiras de os usuários manipularem o objeto 3D: a manipulação baseada em funcionalidade e a manipulação não baseada em funcionalidade. No modelo de apontar e confirmar, os usuários podem realizar exatamente as mesmas tarefas utilizando os raios de mão. Nenhum aprendizado adicional é necessário.<br>

### <a name="affordance-based-manipulation"></a>Manipulação baseada em funcionalidade
Os usuários podem usar os raios de mão para apontar e revelar a caixa delimitadora e as funcionalidades de manipulação. Os usuários podem aplicar o gesto de manipulação na caixa delimitadora para mover todo o objeto, nas funcionalidades de borda para girá-lo e nas funcionalidades de canto para dimensioná-lo de maneira uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Manipulação não baseada em funcionalidade
Os usuários apontam com os raios de mão para revelar a caixa delimitadora e aplicam gestos de manipulação diretamente nela. Com uma mão, a translação e a rotação do objeto estão associadas ao movimento e à orientação da mão. Com as duas mãos, os usuários podem transladar, dimensionar e girar o objeto de acordo com os movimentos relativos das duas mãos.<br>

<br>

## <a name="instinctual-gesturers"></a>Gestos instintuais
O conceito de gestos instintuais para a ação de apontar e confirmar é semelhante ao da manipulação direta. Os gestos que os usuários devem realizar em um objeto 3D são orientados pelo design de funcionalidades da interface do usuário. Por exemplo, um ponto de controle pequeno pode motivar os usuários a pinçar com o polegar e o dedo indicador, enquanto que, para um objeto maior, os usuários podem preferir segurar usando todos os 5 dedos.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Design simétrico entre os controladores de mão e DoF 6 
O conceito de apontar e confirmar para interações à distância foi inicialmente criado e definido para o Portal de Realidade Misturada (MRP), no qual um usuário usa um headset imersivo e interage com objetos 3D por meio de controladores de movimento. Os controladores de movimento disparam raios para apontar e manipular objetos distantes. Existem botões nos controladores para confirmar diferentes ações. Utilizamos o modelo de interação de raios e os anexamos às duas mãos. Com esse design simétrico, os usuários que estão familiarizados com o MRP não precisarão aprender a usar outro modelo de interação para apontar e manipular à distância quando usarem o HoloLen 2 e vice-versa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Gestos instintuais

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Manipulação direta com as mãos](direct-manipulation.md)
* [Interações instinctuais](interaction-fundamentals.md)


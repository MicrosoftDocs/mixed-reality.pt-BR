---
title: Ponto e o modo de confirmação com mãos
description: Visão geral do modelo confirmação e de ponto de entrada
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Misto realidade, interação, design, hololens, mãos, agora, aponte e confirmar
ms.openlocfilehash: e69c8ff2091beff7d8fbbde4e6f24d909302290a
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730812"
---
# <a name="point-and-commit-with-hands"></a>Ponto e o modo de confirmação com mãos
Ponto e o modo de confirmação com mãos é um modelo de entrada que permite aos usuários de destino, selecione e manipular objetos 3D e conteúdos 2D na distância. Essa técnica de interação "agora" é exclusiva para a realidade misturada e não é um humanos de maneira naturalmente intereact com o mundo real. Por exemplo, no filme super hero *X-homens*, o caractere [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) é capaz de contatar e manipular um objeto mais distante na distância com suas mãos. Isso não é algo que os humanos podem fazer na realidade. No HoloLens (AR) e realidade mista (VR), nós equipar os usuários com esse poder mágica, quebrando a restrição física do mundo real não apenas para ter uma experiência e interessantes com conteúdo holográfica, mas também para tornar a interação mais eficaz e eficiente.

## <a name="device-support"></a>Suporte a dispositivos

Modelo de entrada | [HoloLens (1ª geração)](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [Fones imersivos em exposição](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
Ponto e confirmação (interação mão distante) | ❌ Não tem suportada | ✔️ Recomendado | ✔️ Recomendado

Ponto e a confirmação, também conhecido como mãos agora, é um dos novos recursos que utiliza o novo sistema de controle de mão articulado. Esse modelo de entrada também é o modelo de entrada primário em fones imersivos em exposição com o uso de controladores de movimento.

## <a name="hand-rays"></a>Raios de mão

Em 2 HoloLens, criamos um raio de mão Atira do Centro de um palm. Este ray é tratado como uma extensão da mão. Um cursor em forma de rosca é anexado ao final do raio para indicar o local onde o raio cruza com um objeto de destino. O objeto que o cursor chega à, em seguida, pode receber comandos gestual de mão.

Esse comando gestual básico é disparado, usando o polegar e o dedo para executar a ação de toque de ar. Usando o raio de mão para apontar e polegar para confirmar, os usuários podem ativar um botão ou um hiperlink em um conteúdo da web. Com os gestos de composição mais, os usuários são capazes de navegar o conteúdo da web e manipular objetos 3D à distância. O design visual do raio mão também deve reagir a esses estados de confirmação e de ponto, como descrito e mostrado abaixo: 

* No *apontando* de estado, o raio é uma linha de traço e o cursor é uma forma de rosca.
* No *confirmação* de estado, o raio se transforma em uma linha sólida e reduz o cursor para um ponto.

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>Faça a transição entre próximo e distante

Em vez de usar o gesto específico, como "apontando com dedo indicador" para direcionar o raio, projetamos o raio provenientes de fora do centro do palm, liberando e reservar os cinco dedos para gestos manipulative mais, como aperto e pegar. Com esse design, podemos criar apenas um modelo mental, que dão suporte a exatamente o mesmo conjunto de gestos de mão para interação próxima e distante. Você pode usar o mesmo gesto de captura para manipular objetos em distâncias diferentes. A invocação dos raios é automático e a proximidade com base em:

*  Quando um objeto está dentro do arm atingido distância (aproximadamente 50 cm), os raios são desativados automaticamente incentivando para interação com o próxima.
*  Quando o objeto está mais distante 50 cm, raios são ativados. A transição deve ser simples e direta.

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>Interação slate 2D

Um Slate 2D é um contêiner de holográfico hospedando conteúdo do aplicativo 2D, como o navegador da web. O conceito de design para o momento interagir com um slate 2D é usar os raios de mão para tap de destino e ar para selecionar. Após o direcionamento com um raio de mão, os usuários podem polegar para disparar um hiperlink ou um botão. Eles podem usar uma mão para "ar tocar e arrastar" rolar um slate conteúdo para cima para baixo. O movimento relativo da usando duas mãos para tocar e arrastar de ar pode aplicar zoom e o conteúdo de imagem fixa.

Direcionar o raio de mão nos cantos e bordas revela a funcionalidade de manipulação mais próximo. Por "captura e arrastar" as capacidades de manipulação, os usuários podem executar uniforme de dimensionamento por meio de capacidades de canto e pode refluir o slate por meio de capacidades de borda. Pegando e arrastando o holobar na parte superior do slate 2D a usuários podem mover o slate inteiro.

![](images/2D-Slate-Interaction-Far-720px.jpg)

Para a manipulação de 2D de imagem fixa em si:<br>

* Os usuários apontam o raio de mão nos cantos ou bordas para revelar a funcionalidade de manipulação mais próximo. 
* Aplicando um gesto de manipulação de funcionalidade, os usuários podem executar a escala uniforme por meio da funcionalidade de canto e podem refluir o slate via a funcionalidade de borda. 
* Aplicando um gesto de manipulação de holobar na parte superior do slate 2D, os usuários podem mover o slate inteiro.<br>

<br>

## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D

Na manipulação direta, há duas maneiras para os usuários manipular o objeto 3D, manipulação de funcionalidade e manipulação de não-funcionalidade com base. No modelo de ponto e a confirmação, os usuários são capazes de alcançar o exatamente as mesmas tarefas por meio de raios de mão. Nenhum aprendizado adicional é necessária.<br>

### <a name="affordance-based-manipulation"></a>Manipulação de funcionalidade
Os usuários usar raios de mão para apontar e revelar a caixa delimitadora e capacidades de manipulação. Os usuários podem aplicar o gesto de manipulação na caixa delimitadora para mover o objeto inteiro, nas capacidades de borda para girar e em coner de capacidades para dimensionar de maneira uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Funcionalidade não com base em manipulação
Ponto de usuários com raios de mão para revelar a caixa delimitadora e em seguida, aplicar diretamente a gestos de manipulação nele. Com um lado, a translação e rotação do objeto são associados ao movimento e a orientação da mão. Com duas mãos, os usuários podem traduzir, dimensionar e girá-lo de acordo com os movimentos relativos de duas mãos.<br>

<br>

## <a name="instinctual-gesturers"></a>Gesturers instinctual
O conceito de gestos instinctual para ponto e a confirmação é semelhante de manipulação direta. Os gestos os usuários são suponha que para executar em um objeto 3D são orientados pelo design de capacidades de interface do usuário. Por exemplo, um ponto de controle pequeno pode motivar usuários aperto com seus polegar e o dedo, enquanto um usuário pode querer obter um objeto maior usando todos os 5 dedos.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Design simétrica entre mãos e controlador de DoF 6 
O conceito de ponto e confirmação de interação mais distante foi inicialmente criado e definido para misto realidade Portal (MRP), onde um usuário executa um fone de ouvido envolvente e interage com objetos 3D por meio de controladores de movimento. Os controladores de movimento envie out raios para apontando e manipular objetos distantes. Existem botões nos controladores para confirmar ainda mais ações diferentes. Podemos aproveitar o modelo de interação de raios e anexados-los para ambas as mãos. Com esse design simétrica, o que os usuários que estão familiarizados com MRP não precisarão aprender outro modelo de interação que aponta para o momento e a manipulação de quando eles usam HoloLen 2 e vice-versa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Gestos instinctual

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Manipulação direta com mãos](direct-manipulation.md)
* [Interações instinctuais](interaction-fundamentals.md)


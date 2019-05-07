---
title: Ponto e confirmar
description: Visão geral do modelo confirmação e de ponto de entrada
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: Misto realidade, interação, de design
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581306"
---
# <a name="point-and-commit"></a>Ponto e confirmar
Ponto e a confirmação é um modelo de entrada permite que os usuários de destino, selecione e manipular conteúdo 2D e 3D objetos em uma distância. Essa técnica de interação do "Extremo" é uma experiência interativa de umbigo humano sendo não tinha realmente durante sua interação diária com o mundo real. Por exemplo, um filme de super hero, Magneto é capaz de contatar e manipular um objeto distante via mãos em uma distância, mas humanos não é possível fazer isso em realidade. No Microsoft HoloLens (AR) e realidade mista do Microsoft (VR), nós equipar os usuários esse poder mágica, quebrando a restrição física do mundo real não apenas para ter experiência e interessantes com conteúdo holográfica, mas para tornar a interação mais eficaz e eficiente.

## <a name="device-support"></a>Suporte a dispositivos
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Ponto e confirmação (interação mão distante)</td>
        <td>❌ Não tem suportada</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>
<br>
Ponto e confirmação tem sido um dos modelos de entrada primários em 2 HoloLens, utilizando a mão articulada novo sistema de controle. Esse modelo de entrada também é o modelo de entrada primário em fones imersivos em exposição com o uso de controladores de movimento. Ponto e a confirmação é o modelo de entrada que sugerimos para substituir o cabeçalho olhares e confirmada no HoloLens (1º gen). 

## <a name="hand-rays"></a>Raios de mão
Em 2 HoloLens, criamos um raio de mão de solução do Centro de um palm. O raio é tratado como uma extensão da mão. Um cursor de forma de rosca é anexado ao final do raio implica, o local onde o raio cruza com um objeto hitted. O objeto que o cursor chega receberá gestual comandos da mão. 

O comando gestual muito básico é acionado usando o polegar e o dedo para executar o gesto de ar. Usando ray mão para apontar e polegar para confirmar, os usuários podem ativar um botão ou um hiperlink em um conteúdo da web. Com os gestos de composição mais, os usuários são capazes de navegar o conteúdo da web e manipular objetos 3D em uma distância. O design visual do raio mão também deve reagir para apontar e estados de confirmação: <br>
* No estado apontador, o raio é dash com linhas e o cursor é uma forma de rosca.
* no estado de confirmação, o raio se transforma em uma linha sólida e o cursor é reduzido para um ponto.<br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a>Faça a transição entre próximo e distante
Em vez de usar gestos específicos, como apontá-lo com o dedo para direcionar o raio, criamos o raio saindo do centro do palm, liberando e reservar os cinco dedos para manipulações gestual mais. Portanto, o HoloLens 2 oferece suporte a exatamente o mesmo conjunto de gestos de mão para interação próxima e distante. Adicionais de aprendizado é necessária quando os usuários de trânsito de perto de interações mais distantes e vice-versa. Os usuários podem usar o mesmo gesto de captura para manipular objetos em distâncias diferentes. A invocação dos raios é automático e a proximidade com base em: <br>
* Quando um objeto está dentro do arm atingido distância (aproximadamente 50 cm), os raios são desativados automaticamente incentivando para interação com o próxima. 
* Quando o objeto está mais distante 50 cm, raios são ativados.

Esse mecanismo faz a transição suave e sem problemas.<br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>Interação slate 2D
Um slate 2D é um contêiner de holográfico hospedando conteúdo do aplicativo 2D, como o navegador da web. O conceito de design para o momento interagir com um slate 2D é usar raios de mão para apontar e polegar para confirmar.<br>

Para interagir com da constante slate:<br>

* Os usuários podem apontar para um hiperlink ou um botão, em seguida, indicador e polegar para ativá-lo. 
* Os usuários podem usar uma mão para executar um gesto de navegação para rolar um slate conteúdo para cima para baixo. 
* Os usuários podem usar duas mãos executar gestos de navegação para aumentar o zoom e o conteúdo de imagem fixa.<br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

Para a manipulação de 2D de imagem fixa em si:<br>

* Os usuários apontam o raio de mão nos cantos ou bordas para revelar a funcionalidade de manipulação mais próximo. 
* Aplicando um gesto de manipulação de funcionalidade, os usuários podem executar a escala uniforme por meio da funcionalidade de canto e podem refluir o slate via a funcionalidade de borda. 
* Aplicando um gesto de manipulação de holobar na parte superior do slate 2D, os usuários podem mover o slate inteiro.<br>

<br>

## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D
Na manipulação direta, há duas maneiras para os usuários manipular o objeto 3D, manipulação de com base em funcionalidade e não affordnace com base em manipulação. No modelo de ponto e a confirmação, os usuários são capazes de alcançar o exatamente as mesmas tarefas por meio de raios de mão. Nenhum aprendizado adicional é necessária.<br>

### <a name="affordance-based-manipulation"></a>Manipulação de funcionalidade com base em
Os usuários usar raios de mão para apontar e revelar a caixa delimitadora e capacidades de manipulação. Os usuários podem aplicar o gesto de manipulação na caixa delimitadora para mover o objeto inteiro, nas capacidades de borda para girar e em coner de capacidades para dimensionar de maneira uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Funcionalidade não com base em manipulação
Ponto de usuários com raios de mão para revelar a caixa delimitadora e em seguida, aplicar diretamente a gestos de manipulação nele. Com um lado, a translação e rotação do objeto são associados ao movimento e a orientação da mão. Com duas mãos, os usuários podem traduzir, dimensionar e girá-lo de acordo com os movimentos relativos de duas mãos.<br>

<br>

## <a name="instinctual-gesturers"></a>Gesturers instinctual
O conceito de gestos instinctual para ponto e confirmação está em sincronizado com isso para manipulação direta. Quais gestos os usuários suponha que para executar em um objeto 3D são orientados pelo design de capacidades de interface do usuário. Um ponto de controle pequeno seria motivar os usuários aperto com o polegar e o dedo, enquanto um objeto grande faz com que os usuários para captar com dedo 5.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Design simétrica entre mãos e controlador de DoF 6 
O conceito de modelo de ponto e confirmação para interação mais distante em primeiro lugar é criado e definido para misto realidade Portal (MRP), onde os usuários wear um fone de ouvido envolvente e interagem com o objeto 3d por meio de controladores de movimento. Os controladores de movimento envie out raios para apontando e manipular objetos distantes. Existem botões nos controladores para confirmar ainda mais funcionalidades diferentes. Podemos aproveitar o modelo de interação de raios e anexá-los em ambas as mãos. Com esse design simétrica, os usuários que estão familiarizados com MRP não precisarão aprender outro modelo de interação para o momento apontando e manipulação durante a primeira vez usando HoloLen 2 e vice-versa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>Consulte também
* [Olhar e confirmar](gaze-and-commit.md)
* [Manipulação direta](direct-manipulation.md)
* [Conceitos básicos de interação](interaction-fundamentals.md)

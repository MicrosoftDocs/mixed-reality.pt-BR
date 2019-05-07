---
title: Manipulação direta
description: Visão geral do modelo de entrada a manipulação direta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
keywords: Misto realidade, olhar, olhar direcionamento, interação, de design
ms.openlocfilehash: d855955d44c1cf074849992e5dd7b36b54675fdd
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581326"
---
# <a name="direct-manipulation"></a>Manipulação direta
A manipulação direta é um modelo de entrada que envolve a tocar hologramas diretamente com suas mãos. O objetivo com a manipulação direta é objetos se comportam exatamente como funcionaria no mundo real. Botões podem ser ativada simplesmente pressionando-los, objetos possam ser retirados captando-los e conteúdo 2D se comporta como uma tela de toque virtual.  Por isso, direta manipulação é mais fácil para os usuários saber mais, e isso divertido muito.  Ele é considerado um modelo de entrada "próximo", que significa que ele é mais adequado para interagir com o conteúdo que está dentro de braços atingir.

Um ingrediente principal que torna fácil de aprender a manipulação direta é o que é baseada na funcionalidade. Não há nenhum gestos simbólicos para ensinar os usuários. Todas as interações devem ser criadas em torno de um elemento visual que pode ser tocado ou capturado.

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Manipulação direta (próximo interação disponível)</td>
        <td>❌ Não tem suportada</td>
        <td>✔️ Recomendado</td>
        <td>➕ Uma opção alternativa, mas <a href="point-and-commit.md">ponto e confirmação (interação distante)</a> é recomendado</td>
    </tr>
</table>

A manipulação direta é um modelo de entrada primário em 2 HoloLens, utilizando a mão articulada novo sistema de controle. O modelo de entrada também está disponível no fones imersivos em exposição com o uso de controladores de movimento, mas não é recomendado para que o principal meio de interação fora de manipulação de objetos.  Manipluation direto não está disponível no HoloLens v1.

## <a name="collidable-fingertip"></a>Ponta do dedo collidable
Em 2 HoloLens, mãos de real do usuário são reconhecidas e interpretadas como modelos de esqueleto esquerda e direita. Para implementar a ideia de tocar hologramas diretamente com mãos, idealmente, 5 colisores pode ser anexados a 5 alcance de cada modelo estrutural de mão. No entanto, na prática, devido à falta de comentários táteis, 10 alcance collidable causar muita colisões inesperadas e imprevisíveis com hologramas. Portanto, sugerimos para colocar somente um colisor em cada dedo. O índice collidable alcance ainda pode servir como pontos de toque ativo para gestos de toque diferentes que envolvam outros dedos, como pressione 1 dedo, 1 dedo tocar, 2 Pressione dedo e 5 dedo.

![Imagem de ponta do dedo collidable](images/Collidable-Fingertip-720px.jpg)<br>

### <a name="sphere-collider"></a>Colisor esfera
Em vez de usar de forma genérica aleatória, sugerimos usar um colisor esfera e para processar visualmente para fornecer as melhores indicações para direcionamento quase. Diâmetro da esfera deve corresponder a espessura do dedo para aumentar a precisão de toque. Será fácil recuperar a variável de espessura dedo chamando a API de mão.

<br>

### <a name="fingertip-cursor"></a>Cursor de ponta do dedo
Além de renderizar uma esfera collidable na ponta do dedo índice, podemos criar uma solução de avanço, o cursor de ponta do dedo, para alcançar melhor quase direcionamento experiência interativamente. Ele é um cursor de forma de rosca anexado a ponta do dedo índice. De acordo com a proximidade, ele dinamicamente reage a um destino em termos de orientação e tamanho, conforme mostrado a seguir:
* Quando um dedo se move em direção a um holograma, o cursor sempre é paralelo à superfície do holograma e gradualmente diminui seu tamanho adequadamente. 
* Assim que o dedo tocar a superfície, o cursor é reduzido em um ponto e emite um evento de toque.

<br> Com os comentários interativo, os usuários podem alcançar alta precisão perto de direcionamento de tarefas, como disparar um hiperlink em um conteúdo da web ou pressionar um botão. <br>

![Imagem do cursor de ponta do dedo](images/Fingertip-Cursor-720px.jpg)<br>

## <a name="bounding-box-with-proximity-shader"></a>Caixa delimitadora com o sombreador de proximidade
Também requer o holograma em si para fornecer comentários visuais e de áudio para compensar a falta de comentários táteis. Para fazer isso, geramos o conceito da caixa com o sombreador de proximidade delimitadora. Uma caixa delimitadora é uma área volumétricas mínimas que inclui um objeto 3D. A caixa delimitadora tem um mecanismo de renderização interativo chamado sombreador de proximidade. O sombreador de proximidade se comporta conforme mostrado abaixo:

* Quando o dedo estiver dentro de um intervalo, destaque uma ponta do dedo é convertido na superfície da caixa delimitadora. 
* Quando a ponta do dedo se aproxime para a superfície, destaque condensa adequadamente. 
* Assim que a superfície de toque de ponta do dedo, toda a caixa delimitadora altera a cor ou gerar um efeito visual para refletir o estado do toque. 
* Enquanto isso, um efeito de som pode ser ativado para aprimorar os comentários de toque visual.

![Caixa delimitadora com a imagem do sombreador de proximidade](images/Bounding-Box-With-Proximity-Shader-720px.jpg)<br>

## <a name="pressable-button"></a>Botão pressable
Com a ponta do dedo collidable, os usuários agora estão prontos para interagir com o fundamental componente da interface do usuário holográfico, botão pressable. Um botão pressable é um botão holográfico adaptado para press dedo direto. Novamente, devido à falta de comentários táteis, um botão pressable equipa alguns mecanismos para lidar com comentários táteis problemas relacionados. 
* O primeiro mecanismo é delimitadora caixa com o sombreador de proximidade, que já foi resolvido no parágrafo acima. Ela serve para fornecer um senso melhor de proximidade para usuários abordar e fazer contato com um botão. 
* A segunda é depressão. Ele cria o senso de press, depois que a ponta do dedo entra em contato com o botão. O mecanismo é que o botão se move intimamente com a ponta do dedo ao longo do eixo de profundidade. O botão pode ser disparado assim que atingir uma profundidade designada (em press) ou deixando a profundidade (na versão) depois de passar por ele. 
* O efeito de som deve ser adicionado para melhorar a comentários, quando o botão for disparado. 

![Imagem do botão pressable](images/Pressable-Button-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>Interação slate 2D
Um slate 2D é um contêiner de holográfico hospedando conteúdo do aplicativo 2D, como o navegador da web. O conceito de design para interagir com um slate 2D por meio da manipulação direta é aproveitar o modelo mental de interagir com uma tela touch físico.<br> <br>
Para interagir com o slate contato:<br> 
* Os usuários usar um dedo ao pressionar um botão ou um hiperlink. 
* Usuários usam o dedo para rolar um slate conteúdo para cima para baixo. 
* Os usuários usar dois dedos para aplicar zoom e o conteúdo slate de acordo com relativo movimento dos dedos. 
![Imagem de slate 2D](images/2D-Slate-Interaction-720px.jpg)<br>

<br>Para a manipulação de 2D de imagem fixa em si:<br>
* Os usuários podem abordar a mão na direção de vértices e bordas para revelar as capacidades de manipulação mais próximo. 
* Capturando as capacidades de manipulação, os usuários podem executar dimensionamento uniforme por meio de affordnaces de canto e refluir por meio de capacidades de borda. 
* Pegando o holobar na parte superior do slate 2D podem usuários mover o slate inteiro.<br><br>

![Imagem de manipulação de imagem fixa](images/Manipulate-2d-slate-720px.jpg)


## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D
Em 2 HoloLens, os usuários estão habilitados para usar suas mãos direta manipular objetos 3D hologramphic aplicando uma caixa delimitadora para cada objeto 3D. A caixa delimitadora fornece melhor percepção de profundidade por meio de seu sombreador de proximidade. Com a caixa delimitadora, há duas abordagens de design para manipulação de objetos 3D:      
### <a name="affordance-based-manipulation"></a>Funcionalidade com base em manipulação:
É uma maneira para os usuários manipular o objeto 3D por meio de delimitação de caixa e as capacidades de manipulação em torno dele. Assim que a mão de um usuário estiver prestes a um objeto 3D, a caixa delimitadora e a funcionalidade mais próxima são reveladas. Os usuários podem pegar a caixa delimitadora para mover o objeto inteiro, as capacidades de borda para girar e coner de capacidades para dimensionar de maneira uniforme.<br>

![Imagem de manipulação de objeto 3D](images/3D-Object-Manipulation-720px.jpg)<br>

### <a name="non-affordance-based-manipulation"></a>Funcionalidade não com base em manipulação:
Este mechanisom nenhuma funcionalidade está conectada na caixa delimitadora. Os usuários podem revelar apenas a caixa delimitadora e interagem diretamente com ele. Se a caixa delimitadora é capturada com uma mão, a conversão e rotação do objeto estão associadas a animação e a orientação da mão. Quando o objeto é capturado com duas mãos, os usuários podem traduzir, dimensionar e girá-lo de acordo com os movimentos relativos de duas mãos.<br><br> 

<br><br>
Para manipulação exige a precisão, é recomendável manipulação afforance com base, fornecendo um alto nível de granularidade. Para a manipulação flexível, a manipulação de não-funcionalidade será uma boa opção, oferecer aos usuários experiências instantâneas e divertidas.


## <a name="instinctual-gestures"></a>Gestos instinctual
Ao contrário do HoloLens (1º gen), os usuários de ensino predefinida de alguns gestos, como Bloom e tocar no ar, HoloLens 2, podemos não pergunte aos usuários memorizar quaisquer gesto simbólico. Todos os gestos que os usuários precisam para interagir com hologramas e conteúdo são instinctual. A forma de atingir o gesto instinctual é orientar os usuários a executar gestos por meio do design de capacidades de interface do usuário. Por exemplo, se nós o encorajamos que os usuários captura um objeto ou um ponto de controle com a situação de emergência de dois dedos, o objeto ou o ponto de controle deve ser pequeno. Se quisermos que os usuários realizem captura de cinco dedo, o objeto ou o ponto de controle deve ser relativamente grande. Assim como botões, um pequeno botão limitaria usuários para pressioná-lo com um único dedo, enquanto um botão grande seria encorajar os usuários a pressioná-lo com as mãos.
![](images/Instinctual-Gestures-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Design simétrica entre mãos e controladores de DoF 6
Você talvez tenha observado que agora há parallels interação que podemos tirar entre as mãos em controladores de AR e movimento no VR. Ambas as entradas podem ser usadas para disparar a manipulações diretas em seus respectivos ambientes. 2 HoloLens, captando e arrastando com mãos Works uma distância próxima grande parte da mesma maneira como o botão de captura faz nos controladores de movimento em WMR. Isso fornece aos usuários com a familiaridade da interação entre as duas plataformas e pode ser úteis se você nunca decidir portar seu aplicativo de um para o outro.

## <a name="optimizing-with-eye-tracking"></a>Otimizando com acompanhamento a olho nu
A manipulação direta pode se sentir mágica se ele funciona conforme o esperado, mas pode também rapidamente se tornar frustrante, se você não pode mover sua mão em qualquer lugar mais sem disparar inadvertidamente um holograma.
Acompanhamento a olho nu potencialmente pode ajudar a identificar melhor o que é a intenção do usuário. 

* **When**: Reduza falsamente acionar uma resposta de manipulação. Permite o acompanhamento a olho nu para entender melhor o que um usuário atualmente envolvido com. Por exemplo, imagine que você está lendo por meio de um texto (instrutivos) holográfico ao atingir mais para pegar a você a ferramenta de trabalho do mundo real.
Ao fazer isso, você acidentalmente mover sua mão em alguns botões holográfica interativo que você ainda não tenha notado, mesmo antes de (talvez que ele até mesmo estava fora do campo de exibição do usuário).
Em resumo: Se o usuário ainda não examinou um holograma por algum tempo, mas foi detectado um evento de toque ou compreensão para ele, é provável que o usuário realmente não pretendida interagir com esse holograma. 

* **Qual deles**: Além do endereçamento de ativações positivas falsas, outro exemplo inclui melhor identificar quais hologramas para capturar ou examinar o que o ponto de interseção precisos não pode ser clara da sua perspectiva, especialmente se vários hologramas são posicionadas próximos um outros. Enquanto o acompanhamento de olho no HoloLens 2 tem uma limitação certa sobre como com precisão, ele pode determinar olho o olhar, isso pode ainda ser muito útil para perto de interações devido a disparidade de profundidade ao interagir com mão de entrada. Isso significa que, às vezes, é difícil determinar se sua mão é atrás ou na frente de um holograma precisamente pegar um widget de manipulação, por exemplo.

 * **Onde**: Use as informações sobre o que um usuário está observando com gestos gerando rápidos. Pegue um holograma e aproximadamente esclarecer isso para seu destino pretendido. Enquanto isso, às vezes, pode funcionar muito bem, rapidamente executar gestos de mão pode resultar em destinos altamente imprecisos.
Isso é onde acompanhamento a olho nu poderia ajudar de confiar a mão lançando o vetor de volta para a posição desejada.

## <a name="see-also"></a>Consulte também
* [Olhar e confirmar](gaze-and-commit.md)
* [Ponto e confirmar](point-and-commit.md)
* [Conceitos básicos de interação](interaction-fundamentals.md)


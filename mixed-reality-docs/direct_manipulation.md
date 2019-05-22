---
title: Manipulação direta
description: Visão geral do modelo de entrada a manipulação direta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
keywords: Misto realidade, olhar, olhar direcionamento, interação, de design, mãos perto, HoloLens
ms.openlocfilehash: a9e67f21587381dbc1090f89935eaa2b88630dae
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974751"
---
# <a name="direct-manipulation"></a>Manipulação direta

O HoloLens 2 tem um modelo de entrada de manipulação direta que permite que você toque hologramas dircly com suas mãos. O objetivo com a manipulação direta é para os objetos se comportam exatamente como funcionaria no mundo real. Você pode ativar botões, simplesmente pressionando-los e até mesmo pegar, pegar e mover objetos. Nesses cenários, o conteúdo 2D se comporta como uma tela de toque virtual.

Direcionar a manipulação é mais fácil para os usuários saber mais, e tem divertidos muito. Ele é considerado um modelo de entrada "entrega perto de", que significa que ele é mais adequado para interagir com o conteúdo que está dentro do alcance do arm.

A manipulação direta é baseado em funcionalidade, que significa amigável do usuário. Não há nenhum gestos simbólicos para ensinar os usuários. Todas as interações são criadas em torno de um elemento visual que você pode tocar ou capturar.

## <a name="device-support"></a>Suporte a dispositivos

| Modelo de entrada | [HoloLens (1st Gen)](https://review.docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details?branch=master) | HoloLens 2 |[Fones imersivos em exposição](https://review.docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details?branch=master)|
|:-------- | :-------| :--------| :------------|
| Manipulação direta | ❌ Não tem suportada | ✔️ Recomendado | Uma alternativa ➕ [aponte e confirmar](https://review.docs.microsoft.com/en-us/windows/mixed-reality/point-and-commit?branch=master) é recomendado.

A manipulação direta é um modelo de entrada primário em 2 HoloLens e utiliza o novo sistema de controle de mão articulado. O modelo de entrada também está disponível no fones imersivos em exposição com o uso de controladores de movimento, mas não é recomendado como o principal meio de interação fora de manipulação de objetos.  Manipluation direto não está disponível no HoloLens v1.

## <a name="collidable-fingertip"></a>Ponta do dedo collidable

Em 2 HoloLens, mãos de real do usuário são reconhecidas e interpretadas como modelos de esqueleto esquerda e direita. Para implementar a ideia de tocar hologramas diretamente com mãos, idealmente, 5 colisores pode ser anexados a 5 alcance de cada modelo estrutural de mão. No entanto, na prática, devido à falta de comentários táteis, alcance collidable 10 causado colisões inesperadas e imprevisíveis com hologramas. 

Portanto, sugerimos para colocar somente um colisor em cada dedo. O alcance de índice collidable ainda pode servir como pontos de toque ativo para gestos de toque diferentes que envolvam outros dedos, como pressione dedo 1, 1 dedo tocar, pressione 2 dedo e 5 dedo press, conforme mostrado na imagem abaixo.

![Imagem de ponta do dedo collidable](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Colisor esfera

Em vez de usar uma forma genérica aleatória, sugerimos usar um colisor esfera e para processar visualmente para fornecer as melhores indicações para direcionamento quase. Diâmetro da esfera deve corresponder a espessura do dedo para aumentar a precisão de toque. Será fácil recuperar a variável de espessura dedo chamando a API de mão.

### <a name="fingertip-cursor"></a>Cursor de ponta do dedo

Além de renderizar uma esfera collidable na ponta do dedo índice, criamos uma solução avançada, o cursor de ponta do dedo, para obter a melhor experiência de perto o direcionamento interativamente. É um cursor em forma de rosca anexado a ponta do dedo índice. De acordo com a proximidade, ele reage dinamicamente para um destino em termos de orientação e tamanho conforme detalhado abaixo:

* Quando um dedo se move em direção a um holograma, o cursor sempre é paralelo à superfície do holograma e gradualmente diminui seu tamanho adequadamente.
* Assim que o dedo toca a superfície, o cursor é reduzido em um ponto e emite um evento de toque.

Com os comentários interativo, os usuários podem alcançar alta precisão perto de direcionamento de tarefas, como disparar um hiperlink no conteúdo da web ou pressionar um botão, como mostrado abaixo. 

![Imagem do cursor de ponta do dedo](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Caixa delimitadora com o sombreador de proximidade

O holograma em si também requer a capacidade de fornecer comentários visuais e de áudio para compensar a falta de comentários táteis. Para fazer isso, geramos o conceito de uma caixa delimitadora com o sombreador de proximidade. Uma caixa delimitadora é uma área mínima volumétricas que inclui um objeto 3D. A caixa delimitadora tem um mecanismo de renderização interativo chamado sombreador de proximidade. O sombreador de proximidade comporta-se:

* Quando o dedo estiver dentro de um intervalo, destaque uma ponta do dedo é convertido na superfície da caixa delimitadora.
* Quando a ponta do dedo se aproxime para a superfície, destaque condensa adequadamente.
* Assim que a superfície de toque de ponta do dedo, toda a caixa delimitadora altera a cor ou gerar um efeito visual para refletir o estado do toque.
* Enquanto isso, um efeito de som pode ser ativado para aprimorar os comentários de toque visual.

![Caixa delimitadora com a imagem do sombreador de proximidade](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Botão pressable

Com a ponta do dedo collidable, os usuários agora estão prontos para interagir com o fundamental componente da interface do usuário holográfico, botão pressable. Um botão pressable é um botão holográfico adaptado para press dedo direto. Novamente, devido à falta de comentários táteis, um botão pressable equipa alguns mecanismos para lidar com problemas relacionados a comentários de táteis.

* O primeiro mecanismo é uma caixa delimitadora com o sombreador de proximidade, detalhado na seção anterior. Ela serve para fornecer um senso melhor de proximidade para usuários abordar e fazer contato com um botão.
* A segunda é depressão. Ele cria o senso de press, depois que a ponta do dedo entra em contato com o botão. O mecanismo é que o botão se move intimamente com a ponta do dedo ao longo do eixo de profundidade. O botão pode ser disparado quando ele atinge uma profundidade designada (em press) ou deixa o comprimento (em versão) depois de passar por ele.
* O efeito de som deve ser adicionado para melhorar a comentários, quando o botão for disparado.

![Imagem do botão pressable](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>Interação slate 2D

Um slate 2D é um contêiner de holográfico hospedando conteúdo do aplicativo 2D, como o navegador da web. O conceito de design para interagir com um slate 2D por meio da manipulação direta é aproveitar o modelo mental de interagir com uma tela touch físico.

Para interagir com o slate contato:

* Use o dedo para pressionar um botão ou um hiperlink.
* Use o dedo para rolar um slate conteúdo para cima para baixo.
* Os usuários usar dois dedos para aplicar zoom e o conteúdo slate de acordo com relativo movimento dos dedos.

![Imagem de slate 2D](images/2D-Slate-Interaction-720px.jpg)

Para a manipulação de 2D de imagem fixa em si:

* Aborde as mãos na direção de vértices e bordas para revelar as capacidades de manipulação mais próximo.
* Pegue as capacidades de manipulação e executar um dimensionamento uniforme por meio de capacidades de canto e refluir por meio de capacidades de borda.
* Pegue o holobar na parte superior do slate 2D, que permite que você mova o slate inteiro.

![Imagem de manipulação de imagem fixa](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D

HoloLens 2 permite que permite que os usuários habilitam a mão direcionar a manipular objetos 3D hologramphic aplicando uma caixa delimitadora para cada objeto 3D. A caixa delimitadora fornece melhor percepção de profundidade por meio de seu sombreador de proximidade. Com a caixa delimitadora, há duas abordagens de design para manipulação de objetos 3D.

### <a name="affordance-based-manipulation"></a>Manipulação de funcionalidade

Isso permite manipular o objeto 3D por meio de uma caixa delimitadora e as capacidades de manipulação em torno dele. Assim que a mão de um usuário estiver prestes a um objeto 3D, a caixa delimitadora e a funcionalidade mais próxima são reveladas. Os usuários podem pegar a caixa delimitadora para mover todo o objeto, as capacidades de borda para girar e as capacidades de canto para dimensionar de maneira uniforme.

![Imagem de manipulação de objeto 3D](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>Funcionalidade não com base em manipulação

Esse mecanismo, nenhuma funcionalidade está conectada na caixa delimitadora. Os usuários podem revelar apenas a caixa delimitadora e interagem diretamente com ele. Se a caixa delimitadora é capturada com uma mão, a conversão e rotação do objeto estão associadas a animação e a orientação da mão. Quando o objeto é capturado com duas mãos, os usuários podem traduzir, dimensionar e girá-lo de acordo com os movimentos relativos de duas mãos.

Manipulação específica exige a precisão, recomendamos que você use **manipulação com base em funcionalidade**, pois ele fornece um alto nível de granularidade. Para a manipulação flexível, recomendamos que você usa **manipulação não funcionalidade** é pois ela permite experiências instantâneas e divertidas.

## <a name="instinctual-gestures"></a>Gestos instinctual

Ao contrário do HoloLens (1º gen), podemos ensinado usuários alguns gestos predefinidos, como Bloom e toque em ondas de rádio. 2 HoloLens, não solicitamos memorizar quaisquer simbólicos gestos aos usuários. Todos os gestos do usuário exigida, os usuários precisam interagir com hologramas e conteúdo, são instinctual. A forma de atingir o gesto instinctual é orientar os usuários a executar gestos por meio do design de capacidades de interface do usuário.

Por exemplo, se nós o incentivamos a captura de um objeto ou um ponto de controle com a situação de emergência de dois dedos, o objeto ou o ponto de controle deve ser pequeno. Se quisermos realizar a captura de cinco dedo, o objeto ou o ponto de controle deve ser relativamente grande. Assim como botões, um pequeno botão limitaria usuários para pressioná-lo com um único dedo, enquanto um botão grande seria encorajar os usuários a pressioná-lo com as mãos.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Design simétrica entre mãos e controladores de DoF 6

Você talvez tenha observado que agora há parallels interação que podemos tirar entre as mãos em controladores de AR e movimento no VR. Ambas as entradas podem ser usadas para disparar a manipulações diretas em seus respectivos ambientes. 2 HoloLens, captando e arrastando com mãos Works uma distância próxima grande parte da mesma maneira como o botão de captura faz nos controladores de movimento em WMR. Isso fornece aos usuários com a familiaridade da interação entre as duas plataformas e pode ser úteis se você nunca decidir portar seu aplicativo de um para o outro.

## <a name="optimize-with-eye-tracking"></a>Otimizar com acompanhamento a olho nu

A manipulação direta pode se sentir mágica se ele funciona conforme o esperado, mas pode também rapidamente se tornar frustrante, se você não pode mover sua mão em qualquer lugar mais sem disparar inadvertidamente um holograma.
Acompanhamento a olho nu potencialmente pode ajudar a identificar melhor o que é a intenção do usuário.

* **When**: Reduza falsamente acionar uma resposta de manipulação. Permite o acompanhamento a olho nu para entender melhor o que um usuário atualmente envolvido com.
Por exemplo, imagine que você está lendo por meio de um texto (instrutivos) holográfico ao atingir mais para pegar a você a ferramenta de trabalho do mundo real.

  Ao fazer isso, mova acidentalmente sua mão em alguns botões holográfica interativo que você ainda não tenha notado, mesmo antes de (talvez até mesmo era fora campo de exibição do usuário, o (FOV)).

  Em resumo: Se o usuário ainda não examinou um holograma por algum tempo, mas foi detectado um evento de toque ou compreensão para ele, é provável que o usuário realmente não pretendida interagir com esse holograma.

* **Qual deles**:  Além do endereçamento de ativações positivas falsas, outro exemplo inclui melhor identificar quais hologramas para capturar ou examinar o que o ponto de interseção precisos não pode ser clara da sua perspectiva, especialmente se vários hologramas são posicionadas próximos um outros.

  Enquanto o acompanhamento de olho no HoloLens 2 tem uma limitação certa sobre como com precisão, ele pode determinar olho o olhar, isso pode ainda ser muito útil para perto de interações devido a disparidade de profundidade ao interagir com mão de entrada.  Isso significa que, às vezes, é difícil determinar se sua mão é atrás ou na frente de um holograma precisamente pegar um widget de manipulação, por exemplo.

* **Onde**: Informações de uso sobre o que um usuário está analisando com rápido - gerando gestos. Pegue um holograma e aproximadamente esclarecer isso para seu destino pretendido.  

    Enquanto isso, às vezes, funciona muito bem, rapidamente executando gestos de mão pode resultar em destinos altamente imprecisos. Isso é onde acompanhamento a olho nu poderia ajudar de confiar a mão lançando o vetor de volta para a posição desejada.

## <a name="see-also"></a>Consulte também

* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)

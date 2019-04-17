---
title: Objeto interagível
description: Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D. No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, experiência do usuário
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589808"
---
# <a name="interactable-object"></a>Objeto interagível

Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D. No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais. Nada pode ser um **Interagível objeto** que dispara um evento. Um objeto interagível pode ser representado como qualquer coisa uma xícara de café na tabela para um balão flutuar no ar. Estamos ainda fazer uso dos botões tradicionais em determinada situação como a caixa de diálogo da interface do usuário. A representação visual do botão depende do contexto.

![Imagem do herói de objeto interactible](images/640px-interactibleobject-hero-640px.jpg)


No  **[Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, criamos uma série de scripts do Unity e pré-fabricados que ajudarão você a criar objetos Interagível. Você pode usá-los para criar qualquer tipo de objeto que o usuário pode interagir com o, usando esses estados de interação padrão: Observação, direcionadas e pressionado. Você pode personalizar facilmente o design visual com seus próprios ativos. Animações detalhadas podem ser personalizadas criando e atribuindo clipes de animação correspondente para os estados de interação no controlador de animação do Unity ou usando o deslocamento e a escala. 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a>Comentários visuais para os estados diferentes de interação de entrada

Na realidade mista, como os objetos holográfico são combinados com o ambiente do mundo real, pode ser difícil de entender quais objetos são interagível. Para quaisquer objetos interagível em sua experiência, é importante fornecer comentários visuais diferenciados para cada estado de entrada. Isso ajuda o usuário a entender qual parte da sua experiência é interagível e faz com que o usuário confiantes com o método de interação consistente.

Para todos os objetos que o usuário pode interagir com, é recomendável ter comentários visuais diferentes para esses três estados de entrada:
* **Observação**: Estado ocioso de padrão do objeto.
* **Destino**: Quando o objeto é afetado com o cursor de olhar, finger ponteiro do controlador proximidade ou a animação.
* **Pressionado**: Quando o objeto é pressionado com gestos de toque de ar, pressione dedo ou botão de seleção do controlador de animação.

![Botão holographic](images/640px-interactibleobject-holographicbutton-650px.jpg)<br>
*Observação de estado, estado de destino e estado pressionado*

Na realidade mista do Windows, você pode encontrar os exemplos de visualizar estados diferentes de entrada no menu Iniciar e botões da barra de aplicativo. Você pode usar técnicas, como realce ou dimensionamento para fornecer comentários visuais para estados de entrada do usuário.

Em 2 de HoloLens, já que ele dá suporte à mão completamente articulado rastreamento de entrada, podemos fornecer capacidades adicionais com base na proximidade para mãos. O [botão no HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) mostra este exemplo.

![Botão pressable](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a>Exemplos de objeto interagível

### <a name="mesh-button"></a>Botão de malha

![Botão de malha](images/640px-interactibleobject-meshbutton.jpg)

Estes são exemplos usando primitivos e malhas 3D importadas como objetos Interagível. Você pode facilmente atribuir valores diferentes de escala, deslocamento e a cor para responder a cada estado de interação de entrada.

### <a name="toolbar"></a>Barra de ferramentas

![Barra de ferramentas](images/640px-interactibleobject-toolbar.jpg)

Uma barra de ferramentas é um padrão amplamente usado em experiências de realidade misturada. Ele é uma coleção simples de botões com comportamentos adicionais, como [Billboarding e tag-along](billboarding-and-tag-along.md). Este exemplo usa um script Billboarding e tag-along do MixedRealityToolkit. Você pode controlar comportamentos detalhados, incluindo a distância, movendo a velocidade e os valores limite.

### <a name="traditional-button"></a>Botão tradicional

![Botão tradicional](images/640px-interactibleobject-traditionalbutton.jpg)

Este exemplo mostra um botão no tradicional estilo 2D. O estado de cada entrada tem uma profundidade ligeiramente diferente e a propriedade de animação.

### <a name="other-examples"></a>Outros exemplos

![Botão de ação](images/640px-interactibleobject-pushbutton.jpg)<br>
*Botão de ação*
<br>
![Objeto de vida real](images/640px-interactibleobject-reallifeobject.jpg)<br>
*Objeto da vida real*

Com o HoloLens, você pode aproveitar o espaço físico. Imagine um botão de envio por push holographic em uma parede físico. Ou tal uma xícara de café em uma tabela real? Usando modelos 3D importados do software de modelagem, podemos criar um objeto Interagível que se parece com o objeto da vida real. Uma vez que ele é um objeto digital, podemos adicionar interações mágicas a ele.

## <a name="interactable-object-in-mixed-reality-toolkit"></a>Objeto interagível no Kit de ferramentas de realidade mista
Você pode encontrar o [exemplos de Interactable do objeto no Kit de ferramentas de realidade mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)


## <a name="see-also"></a>Consulte também
* [Botão pressable no Kit de ferramentas de realidade misturada-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Coleção de objetos](object-collection.md)
* [Billboarding e tag-along](billboarding-and-tag-along.md)

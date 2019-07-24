---
title: Objeto que interage
description: Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D. No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, UX
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415358"
---
# <a name="interactable-object"></a>Objeto que interage

Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D. No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração. Qualquer coisa pode ser um **objeto** que possa ser interagindo que dispara um evento. Um objeto de interação pode ser representado como qualquer coisa de uma xícara de café na mesa até um balão flutuante no ar. Ainda fazemos uso de botões tradicionais em determinadas situações, como na interface do usuário da caixa de diálogo. A representação visual do botão depende do contexto.

![Objetos Interactible](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Propriedades importantes do objeto que interage

### <a name="visual-cue"></a>Indicação visual

As indicações visuais são indicações de sensor recebidas pelo olho na forma de luz e processadas pelo sistema visual durante a percepção visual. Como o sistema visual é dominante em muitas espécies, especialmente nas pessoas, as indicações visuais são uma grande fonte de informações sobre como o mundo é percebido.

Em realidade misturada, como os objetos Holographic são misturados com o ambiente do mundo real, pode ser difícil entender quais objetos podem ser interagindo. Para qualquer objeto interagindo em sua experiência, é importante fornecer uma indicação visual diferenciada para cada Estado de entrada. Isso ajuda o usuário a entender qual parte da sua experiência é interagindo e faz com que o usuário esteja confiante com o método de interação consistente.

#### <a name="far-interactions"></a>Interações distantes

Para todos os objetos que o usuário pode interagir com olhar, Hand Ray e Ray Controller ' s, é recomendável ter uma indicação visual diferente para esses três Estados de entrada:
* **Padrão (observação)** : Estado ocioso padrão do objeto.
* **Direcionado (focalizado)** : Quando o objeto é direcionado com o cursor olhar, a proximidade do dedo ou o ponteiro do controlador de movimento.
* **Pressionado**: Quando o objeto for pressionado com gesto de toque de ar, pressione o botão de seleção de dedo ou controlador de movimento.

Você pode usar técnicas como realce ou dimensionamento para fornecer uma indicação visual aos Estados de entrada do usuário. No Windows Mixed Reality, você pode encontrar os exemplos de visualização de diferentes Estados de entrada no menu iniciar e nos botões da barra de aplicativos. 

![Exemplo de visualização do estado de observação, estado de destino e estado pressionado](images/640px-interactibleobject-states.png)<br>
*Exemplo de visualização do estado de observação, estado de destino e estado pressionado*

![Estado de observação, estado de destino e estado pressionado no botão Holographic](images/MRTK_InteractableState.png)<br>
*Estado de observação, estado de destino e estado pressionado no botão Holographic*

#### <a name="neardirect-interactions"></a>Interações próximas (diretas)

O HoloLens 2 dá suporte à entrada de controle de mão articulada que permite interagir com objetos. Sem comentários haptics e percepção de profundidade perfeita, às vezes pode ser difícil dizer a distância de sua mão a partir de um objeto ou se você está se tocando. É importante fornecer indicações visuais suficientes para comunicar o estado do objeto e, em particular, de suas mãos em relação a hologramas.

Use comentários visuais para comunicar o seguinte:
* **Padrão (observação)** : Estado ocioso padrão do objeto.
* **Focalizar**: Quando a mão está perto de um holograma, altere os visuais para se comunicar que essa mão está direcionando o holograma. 
* **Distância e ponto de interação**: As mãos abordam o holograma, os comentários do design para comunicar o ponto de interação projetado, bem como a distância do objeto que o dedo é
* **Início do contato**: Alterar visuais (Light, Color) para comunicar que o toque ocorreu
* **Segure**: Altere os visuais (Light, Color) quando o objeto for compreendido.
* **Fim do contato**: Alterar visuais (Light, Color) quando o toque terminar.

![Exemplo de visualização de Estados de interação próxima](images/640px-interactibleobject-states-near.jpg)<br>
*Exemplo de visualização de Estados de interação próxima*

O [botão no HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) mostra o exemplo de visualização de Estados de interação de entrada diferentes.

![Exemplo de botão pressionável no HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Exemplo de botão pressionável no HoloLens 2*

No HoloLens 2, há uma indicação visual adicional que melhora a confiança do usuário na percepção de profundidade. O anel na ponta é exibido e reduzido conforme o alcance fica mais próximo do objeto. O anel, eventualmente, convergi em um ponto no estado de pressionamento. Essa unificação Visual ajuda o usuário a entender a distância do objeto.

![Visualização de anel de alcance](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*Visualização do anel de alcance no HoloLens 2*

![Comentário visual sobre a proximidade](images/HoloLens2_Proximity.gif)<br>
*Exemplo de comentários visuais com base na caixa delimitadora de proximidade*


### <a name="audio-cue"></a>Sinalização de áudio
Para as interações diretas, os comentários de áudio adequados podem melhorar drasticamente a experiência do usuário. Use comentários de áudio para comunicar o seguinte:
* **Início do contato**: Tocar som quando o toque começar
* **Fim do contato**: Tocar som no fim do toque
* **Início da captura**: Tocar som quando a captura começar
* **Fim da captura**: Reproduzir som na extremidade de captura

### <a name="voice-command"></a>Comando de voz
Para qualquer objeto que interaja, é importante dar suporte a opções de interação alternativas. Em padrão, é recomendável dar suporte ao comando de voz para todos os objetos que estiverem interagindo. Para melhorar a descoberta, você pode fornecer a dica de ferramenta no estado de foco.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="Dica de ferramenta para o comando de voz" width="350"><br/>*Dica de ferramenta para o comando de voz*

## <a name="sizing"></a>Dimensionamento
Para garantir que todos os objetos interajantes possam ser facilmente tocadas pelos usuários, recomendamos que você verifique se o que pode interagir atende a um tamanho mínimo (o ângulo visual geralmente medido em graus de arco Visual) com base na distância em que ele é colocado do usuário. O ângulo visual se baseia na distância entre os olhos do usuário e o objeto e permanece constante, enquanto o tamanho físico do destino pode mudar à medida que a distância do usuário é alterada. Para determinar o tamanho físico necessário de um objeto com base na distância do usuário, tente usar uma calculadora de ângulo visual como [esta](http://elvers.us/perception/visualAngle/).

Abaixo estão as recomendações para tamanhos mínimos de conteúdo de interação.

### <a name="target-size-for-direct-hand-interaction"></a>Tamanho de destino para interação direta
| alcance | Ângulo de exibição | Size |
|---------|---------|---------|
| 45cm  | Não é menor que 2 ° | 1,6 x 1,6 cm |

![Tamanho de destino para interação direta](images/TargetSizingNear.jpg)<br>
*Tamanho de destino para interação direta*

Ao criar botões para interação direta, recomendamos um tamanho mínimo maior de 3,2 x 3,2 cm para garantir que haja espaço suficiente para conter um ícone e potencialmente algum texto * *

| alcance | Tamanho mínimo |
|---------|---------|
| 45cm  | 3,2 x 3,2 cm |

![Tamanho do destino dos botões](images/TargetSizingButtons.png)<br>
*Tamanho do destino dos botões*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamanho de destino para interação de olhar
| alcance | Ângulo de exibição | Size |
|---------|---------|---------|
| m  | Não é menor que 1 ° | 3,5 x 3,5 cm |

![Tamanho de destino para interação de olhar](images/TargetSizingFar.jpg)<br>
*Tamanho de destino para interação de olhar*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Criando objeto de interação com o MRTK (Kit de ferramentas de realidade misturada)

No **[Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , você pode encontrar a série de scripts de Unity e pré-fabricados que ajudarão a criar objetos que possam ser interagindo. Você pode usá-los para fazer com que os objetos respondam a vários tipos de Estados de interação de entrada.

* [Interagir](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Exemplos de interação de mão cena](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

O sombreador padrão de MixedRealityToolkit fornece várias opções, como a **luz de proximidade** que ajuda você a criar indicações visuais e de áudio.
* [Sombreador padrão MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>Consulte também

* [Caixa delimitadora](app-bar-and-bounding-box.md)
* [Coleção de objetos](object-collection.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
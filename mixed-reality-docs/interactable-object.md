---
title: Objeto interagível
description: Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D. No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, experiência do usuário
ms.openlocfilehash: b0397e00763f70e4caf55a84b6541085e56fafd4
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148750"
---
# <a name="interactable-object"></a>Objeto interagível

Um botão tem sido uma metáfora usada para disparar um evento no mundo abstrato 2D. No mundo tridimensional realidade misturada, não precisamos ser restrito a esse mundo de abstração mais. Nada pode ser um **interagível objeto** que dispara um evento. Um objeto interagível pode ser representado como qualquer coisa uma xícara de café na tabela para um balão flutuar no ar. Estamos ainda fazer uso dos botões tradicionais em determinada situação como a caixa de diálogo da interface do usuário. A representação visual do botão depende do contexto.

![Objetos interactible](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Propriedades importantes do objeto interagível

### <a name="visual-cue"></a>Indicação visual

Indicações visuais são indicações de aparelhos recebido pelo olho na forma de luz e processados pelo sistema visual durante a percepção visual. Uma vez que o sistema visual é dominante na espécies de muitos, especialmente os seres humanos, indicações visuais são uma grande fonte de informações em como o mundo é percebido.

Na realidade mista, como os objetos holográfico são combinados com o ambiente do mundo real, pode ser difícil de entender quais objetos são interagível. Para quaisquer objetos interagível em sua experiência, é importante fornecer diferenciada indicação visual para cada estado de entrada. Isso ajuda o usuário a entender qual parte da sua experiência é interagível e faz com que o usuário confiantes com o método de interação consistente.

#### <a name="far-interactions"></a>Interações mais distantes

Para todos os objetos que o usuário pode interagir com olhar, ray mão e ray do controlador de movimento, é recomendável ter diferente indicação visual para esses três estados de entrada:
* **Padrão (Observação)** : Estado ocioso de padrão do objeto.
* **Destino (em foco)** : Quando o objeto é afetado com o cursor de olhar, finger ponteiro do controlador proximidade ou a animação.
* **Pressionado**: Quando o objeto é pressionado com gestos de toque de ar, pressione dedo ou botão de seleção do controlador de animação.

Você pode usar técnicas, como realce ou dimensionamento para fornecer uma indicação visual para estados de entrada do usuário. Na realidade mista do Windows, você pode encontrar os exemplos de visualizar estados diferentes de entrada no menu Iniciar e botões da barra de aplicativo. 

![Exemplo de visualizar o estado de observação, estado de destino e estado pressionado](images/640px-interactibleobject-states.png)<br>
*Exemplo de visualizar o estado de observação, estado de destino e estado pressionado*

![Estado de observação, estado de destino e estado pressionado no botão holographic](images/MRTK_InteractableState.png)<br>
*Estado de observação, estado de destino e estado pressionado no botão holographic*

#### <a name="neardirect-interactions"></a>Interações de near(Direct)

HoloLens 2 dá suporte a mão articulada entrada que permite que você interaja com objetos de acompanhamento. Sem comentários hápticos e percepção de profundidade perfeita, às vezes, pode ser difícil dizer o quão distante você sua mão é de um objeto, ou se você se tocam. É importante suficiente para fornecer dicas visuais comunicar o estado do objeto e, em particular de suas mãos em relação à hologramas.

Use comentários visuais para comunicar o seguinte:
* **Padrão (Observação)** : Estado ocioso de padrão do objeto.
* **Hover**: Quando a mão é quase um holograma, visuais de alteração para se comunicar mão está direcionando holograma. 
* **A distância e ponto de interação**: Medida holograma se aproxima de mão, projetar seus comentários para comunicar-se o ponto projetado de interação, bem como longe de ser o objeto é o dedo
* **Entre em contato com Begin**: Elementos visuais de alteração (luz, cor) para se comunicar que toque ocorreu
* **Foi segurado**: Alterar os elementos visuais (luz, cor) quando o objeto é foi segurado.
* **Entre em contato com o final**: Alterar os elementos visuais (luz, cor) que o toque foi finalizada.

![Exemplo de visualizar perto de estados de interação](images/640px-interactibleobject-states-near.jpg)<br>
*Exemplo de visualizar perto de estados de interação*

O [botão no HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) mostra o exemplo de visualizar estados diferentes de interação de entrada.

![Exemplo de botão pressable no HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Exemplo de botão pressable no HoloLens 2*

Em 2 de HoloLens, há uma sugestão visual adicional que melhora a confiança do usuário sobre a percepção de profundidade. O anel de ponta do dedo é exibido e reduz verticalmente conforme a ponta do dedo se aproxime ao objeto. O anel converge eventualmente em um ponto no estado pressione. Essa funcionalidade visual ajuda o usuário a entender a distância do objeto.

![Visualização de anel de ponta do dedo](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*Visualização de anel de ponta do dedo em HoloLens 2*

![Comentários visuais na proximidade de mão](images/HoloLens2_Proximity.gif)<br>
*Exemplo de comentários visuais com base na proximidade - caixa delimitadora*


### <a name="audio-cue"></a>Indicação de áudio
Para interações diretas de mão, comentários de áudio adequado podem melhorar consideravelmente a experiência do usuário. Use comentários de áudio para comunicar o seguinte:
* **Entre em contato com begin**: Reproduzir som quando começa a toque
* **Entre em contato com final**: Reproduz o som no final de toque
* **Iniciar captura**: Reproduzir som quando a captura é iniciado
* **Pegue final**: Reproduz o som no final de captura

### <a name="voice-command"></a>Comando de voz
Para todos os objetos interagível, é importante dar suporte a opções alternativas de interação. Em default, é recomendável para dar suporte ao comando de voz para todos os objetos que são interagível. Para melhorar a capacidade de descoberta, você pode fornecer a dica de ferramenta no estado focalizado.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="Dica de ferramenta para o comando de voz" width="350"><br/>*Dica de ferramenta para o comando de voz*

## <a name="sizing"></a>Dimensionamento
Para garantir que todos os objetos interagível podem ser facilmente tocadas pelos usuários, sugerimos garantindo o interagível atende um tamanho mínimo (geralmente medido em graus de ângulo visual), com base na distância em que ele é colocado do usuário. Ângulo de graus visual baseia-se na distância entre o usuário e o objeto e permanece constante, enquanto o tamanho físico do destino pode alterar como a distância das alterações do usuário. Para determinar o tamanho necessário físico de um objeto com base na distância de uma certeza e pelo grau ângulo visual tente usar uma calculadora, como: http://elvers.us/perception/visualAngle/

Abaixo estão as recomendações para os tamanhos mínimos de conteúdo interagível

### <a name="target-size-for-direct-hand-interaction"></a>Tamanho de destino para a interação direta de mão
| distância | Ângulo de exibição | Tamanho |
|---------|---------|---------|
| 45cm  | não menor do que 2° | 1.6 x 1,6 cm |

![Tamanho de destino para a interação direta de mão](images/TargetSizingNear.jpg)<br>
*Tamanho de destino para a interação direta de mão*

Ao criar botões para interação direta, recomendamos um tamanho mínimo maior de cm de 3,2 x 3.2 para garantir que existe espaço suficiente para conter um ícone e potencialmente algum texto * *

| distância | Tamanho mínimo |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![Tamanho de destino para os botões](images/TargetSizingButtons.png)<br>
*Tamanho de destino para os botões*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamanho de ray mão do destino ou mantenha o foco de interação
| distância | Ângulo de exibição | Tamanho |
|---------|---------|---------|
| 2 min  | não menor do que 1° | 3.5 3,5 cm |

![Tamanho de ray mão do destino ou mantenha o foco de interação](images/TargetSizingFar.jpg)<br>
*Tamanho de ray mão do destino ou mantenha o foco de interação*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Criar objeto interagível com o Kit de ferramentas de realidade misturada (MRTK)

No  **[Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , você pode encontrar a série de scripts do Unity e pré-fabricados que ajudarão você a criar objetos interagível. Você pode usar esses para tornar os objetos a responder a vários tipos de estados de interação de entrada.

* [Interagível](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Cena de exemplos de interação de mão](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Sombreador de padrão do MixedRealityToolkit fornece várias opções, como **luz proximidade** que ajuda a criar as indicações de áudio e vídeo.
* [Sombreador MRTK padrão](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>Consulte também

* [caixa delimitadora](app-bar-and-bounding-box.md)
* [Coleção de objetos](object-collection.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
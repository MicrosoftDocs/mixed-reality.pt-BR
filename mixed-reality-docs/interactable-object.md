---
title: Objeto que interage
description: Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D. No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realidade misturada, controles, interação, interface do usuário, UX
ms.openlocfilehash: 87979d2d7b7de4a384b42b5059239e9b830a92e8
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723225"
---
# <a name="interactable-object"></a>Objeto que interage

![Objetos Interactible](images/UX/UX_Hero_Interactable.jpg)

Um botão tem muito tempo uma metáfora usada para disparar um evento no mundo abstrato de 2D. No mundo de realidade misturada tridimensional, não precisamos mais ser confinado para esse mundo de abstração. Qualquer coisa pode ser um objeto que possa ser **interagindo** que dispara um evento. Um objeto de interação pode ser representado como qualquer coisa de uma xícara de café na mesa até um balão flutuante no ar. Ainda fazemos uso de botões tradicionais em determinadas situações, como na interface do usuário da caixa de diálogo. A representação visual do botão depende do contexto.

<br>

---


## <a name="important-properties-of-the-interactable-object"></a>Propriedades importantes do objeto que interage

### <a name="visual-cues"></a>Indicações visuais

As indicações visuais são indicações de sensor recebidas pelo olho na forma de luz e processadas pelo sistema visual durante a percepção visual. Como o sistema visual é dominante em muitas espécies, especialmente nas pessoas, as indicações visuais são uma grande fonte de informações sobre como o mundo é percebido.

Como os objetos Holographic são mesclados com o ambiente do mundo real em realidade misturada, pode ser difícil entender de quais objetos você pode interagir. Para qualquer objeto interagindo em sua experiência, é importante fornecer indicações visuais diferenciadas para cada Estado de entrada. Isso ajuda o usuário a entender qual parte da sua experiência é interagir e torna o usuário confiante usando um método de interação consistente.

<br>

---

### <a name="far-interactions"></a>Interações distantes

Para todos os objetos que o usuário pode interagir com olhar, Hand Ray e Ray Controller ' s, é recomendável ter uma indicação visual diferente para esses três Estados de entrada:

:::row:::
    :::column:::
       ![interactibleobject-padrão](images/interactibleobject-states-default.jpg)<br>
       **Estado padrão (observação)**<br>
        Estado ocioso padrão do objeto.
    O cursor não está no objeto. A mão não foi detectada.
    :::column-end:::
    :::column:::
       ![interactibleobject-direcionados](images/interactibleobject-states-targeted.jpg)<br>
        **Estado de destino (focalizar)**<br>
        Quando o objeto é direcionado com o cursor olhar, a proximidade do dedo ou o ponteiro do controlador de movimento.
    O cursor está no objeto. A mão foi detectada, pronto.
    :::column-end:::
    :::column:::
       ![interactibleobject-](images/interactibleobject-states-pressed.jpg) pressionadas<br>
       **Estado pressionado**<br>
        Quando o objeto for pressionado com um gesto de toque de ar, pressione o botão de seleção de dedo ou controlador de movimento.
    O cursor está no objeto. A mão é detectada, o ar está tocado.
    :::column-end:::
:::row-end:::

<br>

---

Você pode usar técnicas como realce ou dimensionamento para fornecer indicações visuais para o estado de entrada do usuário. Em realidade misturada, você pode encontrar os exemplos de visualização de diferentes Estados de entrada no menu iniciar e com os botões da barra de aplicativos. 

Veja como esses Estados se parecem em um **botão de Holographic**:

:::row:::
    :::column:::
       ![interactibleobject-padrão](images/MRTK_InteractableState-default.jpg)<br>
       **Estado padrão (observação)**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-direcionados](images/MRTK_InteractableState-targeted.jpg)<br>
        **Estado de destino (focalizar)**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-](images/MRTK_InteractableState-pressed.jpg) pressionadas<br>
       **Estado pressionado**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Interações próximas (diretas) 

O HoloLens 2 dá suporte à entrada de controle de mão articulada que permite interagir com objetos. Sem comentários haptics e percepção de profundidade perfeita, às vezes pode ser difícil dizer de quanto longe sua mão é de um objeto ou se você está tocando. É importante fornecer indicações visuais suficientes para comunicar o estado do objeto e, em particular, o estado de suas mãos em relação a esse objeto.

Use comentários visuais para comunicar o seguinte:
* **Padrão (observação)** : estado ocioso padrão do objeto.
* **Focalizar**: quando uma mão está perto de um holograma, alterar elementos visuais para se comunicar que essa mão está direcionando o holograma. 
* **Distância e ponto de interação**: à medida que a mão se aproxima de um holograma, o design de comentários para comunicar o ponto de interação projetado, bem como a distância do objeto que o dedo é
* **Contato começa**: alterar visuais (claro, cor) para comunicar que um toque ocorreu
* **Segure**: alterar visuais (Light, Color) quando o objeto for Segure
* **Contatos termina**: alterar visuais (claro, cor) quando o toque terminar

<br>

---

:::row:::
    :::column:::
        ![focalizar (longe)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Focalizar (longe)**<br>
        Realce com base na proximidade da mão.
    :::column-end:::
    :::column:::
        ![em foco (próximo)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Focalizar (próximo)**<br>
        Realçar alterações de tamanho com base na distância para a mão.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![toque/pressione](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Toque/pressione**<br>
        Comentários sobre áudio visual Plus.
    :::column-end:::
    :::column:::
        ![Segure](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Compreendi**<br>
        Comentários sobre áudio visual Plus.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Um [botão no HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) é um exemplo de como os diferentes Estados de interação de entrada são visualizados:

:::row:::
    :::column:::
        ![Padrão](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Padrão**<br>
    :::column-end:::
    :::column:::
        ![](images/640px-interactibleobject-pressablebutton-hover.jpg) em foco<br>
        **Operação**<br>
        Revelar um efeito de iluminação baseada em proximidade.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Tocar](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Tocar**<br>
        Mostrar efeito de ondulação.
    :::column-end:::
    :::column:::
        ![Pressione](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Pressione**<br>
        Mova a placa frontal.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>A indicação visual "anel" no HoloLens 2<br>
        No HoloLens 2, há uma indicação visual adicional que pode ajudar a percepção de profundidade do usuário. Um anel próximo a ele é exibido e escala verticalmente conforme o alcance fica mais próximo do objeto. O anel, eventualmente, convergi em um ponto quando o estado pressionado é atingido. Essa unificação Visual ajuda o usuário a entender a distância deles do objeto.<br>
        <br>
        *Loop de vídeo: exemplo de comentários visuais com base na proximidade a uma caixa delimitadora*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![os comentários visuais sobre a proximidade](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Indicações de áudio

Para interações diretas, os comentários de áudio adequados podem melhorar drasticamente a experiência do usuário. Use comentários de áudio para comunicar o seguinte:
* **Contato começa**: Tocar som quando o toque começar
* **Contatos termina**: Tocar som no ponto de toque
* **Captura começa**: reproduzir som quando a captura começar
* **Captações de captura**: Tocar som quando a captura terminar

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Comando de voz<br>
        Para qualquer objeto que interaja, é importante dar suporte a opções de interação alternativas. Por padrão, recomendamos que os [comandos de voz](voice-design.md) tenham suporte para todos os objetos que estiverem interagindo. Para melhorar a descoberta, você também pode fornecer uma dica de ferramenta durante o estado de foco.<br>
        <br>
        *Imagem: dica de ferramenta para o comando de voz*
    :::column-end:::
        :::column:::
       ![comando de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>Recomendações de dimensionamento 

Para garantir que todos os objetos interajantes possam ser facilmente tocadas pelos usuários, recomendamos que você verifique se o que pode interagir atende a um tamanho mínimo (o ângulo visual geralmente medido em graus de arco Visual) com base na distância em que ele é colocado do usuário. O ângulo visual se baseia na distância entre os olhos do usuário e o objeto e permanece constante, enquanto o tamanho físico do destino pode mudar à medida que a distância do usuário é alterada. Para determinar o tamanho físico necessário de um objeto com base na distância do usuário, tente usar uma calculadora de ângulo visual como [esta](https://elvers.us/perception/visualAngle/).

Abaixo estão as recomendações para tamanhos mínimos de conteúdo de interação.


### <a name="target-size-for-direct-hand-interaction"></a>Tamanho de destino para interação direta

| Distância | Ângulo de exibição | Size |
|---------|---------|---------|
| 45cm  | Não é menor que 2 ° | 1,6 x 1,6 cm |

![tamanho de destino para interação direta](images/TargetSizingNear.jpg)<br>
*Tamanho de destino para interação direta*

<br>

### <a name="target-size-for-buttons"></a>Tamanho de destino para botões

Ao criar botões para interação direta, recomendamos um tamanho mínimo maior de 3,2 x 3,2 cm para garantir que haja espaço suficiente para conter um ícone e potencialmente algum texto.

| Distância | Tamanho mínimo |
|---------|---------|
| 45cm  | 3,2 x 3,2 cm |

![tamanho do destino para os botões](images/TargetSizingButtons.png)<br>
*Tamanho do destino dos botões*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamanho de destino para interação de olhar
| Distância | Ângulo de exibição | Size |
|---------|---------|---------|
| m  | Não é menor que 1 ° | 3,5 x 3,5 cm |

![o tamanho de destino para a interação de olhar de raio ou para a direita](images/TargetSizingFar.jpg)<br>
*Tamanho de destino para interação de olhar*


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Objeto de interação no MRTK (Kit de ferramentas de realidade misturada) para Unity

No **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , você pode usar o script de forma a [**interagir**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para fazer com que os objetos respondam a vários tipos de Estados de interação de entrada. Ele dá suporte a vários tipos de temas que permitem definir estados visuais controlando Propriedades de objeto, como cor, tamanho, material e sombreador.

* [Interagir](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Botão](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Exemplos de interação de mão cena](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

O sombreador padrão de MixedRealityToolkit fornece várias opções, como a **luz de proximidade** que ajuda você a criar indicações visuais e de áudio.
* [Sombreador padrão MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a>Veja também

* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)

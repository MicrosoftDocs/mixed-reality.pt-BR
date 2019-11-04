---
title: Tipografia
description: O texto é um elemento importante para entregar informações em sua experiência de aplicativo.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Realidade mista do Windows, design, estilo, fonte, tipografia, interface do usuário, UX
ms.openlocfilehash: 9664d355e941d800ac1ac862860fc5889b6b7686
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437409"
---
# <a name="typography"></a>Tipografia

![Exemplo de tipografia no HoloLens](images/typography-cover.png)<br>


O texto é um elemento importante para entregar informações em sua experiência de aplicativo. Assim como a tipografia em telas 2D, a meta é ser claro e legível. Com o aspecto tridimensional da realidade misturada, há uma oportunidade de afetar o texto e a experiência geral do usuário de uma maneira ainda maior.

Quando falamos sobre o tipo em 3D, tendemos a pensar em texto com extrusão, volumétricos em 3D. Exceto para alguns designs de logotipo e alguns outros aplicativos limitados, o texto extrudada tende a degradar a legibilidade do texto. Embora estejamos criando experiências para 3D, usamos 2D para o tipo, pois ele é mais legível e mais fácil de ler.

No HoloLens, o tipo é construído com hologramas usando Light com base no sistema de cores aditivo. Assim como outros hologramas, o tipo pode ser colocado no ambiente real em que ele pode ser bloqueado pelo mundo e observado em qualquer ângulo. O efeito de [da Parallax](https://en.wikipedia.org/wiki/Parallax) entre o tipo e o ambiente também adiciona profundidade à experiência.

## <a name="typography-in-mixed-reality"></a>Tipografia em realidade misturada

Regras tipográficas em realidade misturada não são diferentes de nenhum outro lugar. O texto no mundo físico e no mundo virtual precisa ser legível e legível. O texto pode estar em uma parede ou sobreposto em um objeto físico. Ele pode ser flutuante junto com uma interface de usuário digital. Independentemente do contexto, aplicamos as mesmas regras tipográficas para leitura e reconhecimento.

### <a name="create-clear-hierarchy"></a>Criar hierarquia clara

Crie contraste e hierarquia usando diferentes tamanhos e pesos de tipo. Definir uma rampa de tipo e seguir em toda a experiência do aplicativo fornecerá uma excelente experiência do usuário com a hierarquia de informações consistente.

exemplos de rampa de ![tipo](images/typography-ramp-1000px.jpg)<br>
*Defina a rampa de tipo e siga-a em toda a experiência do aplicativo*

### <a name="limit-your-fonts"></a>Limitar suas fontes

Evite usar mais de duas famílias de fontes diferentes em um único contexto. Isso interromperá a harmonia e a consistência da sua experiência e dificultará o consumo de informações. No HoloLens, como as informações são sobrepostas sobre o ambiente físico, o uso de muitos estilos de fonte diminuirá a experiência. Segoe UI é a fonte de todos os designs digitais da Microsoft. Ele é usado consistentemente no Shell do Windows Mixed Reality. Você pode baixar o arquivo de fonte Segoe UI na [página do kit de ferramentas de design do Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Mais informações sobre o tipo de Segoe UI](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evitar pesos de fontes finas

Evite usar pesos de fontes leves ou semilight para tamanhos de tipo em 42pt, uma vez que traços verticais finos irão vibrar e degradar a legibilidade. Fontes modernas com espessura de traço suficiente funcionam bem. Por exemplo, Helvetica e Arial são muito legíveis no HoloLens usando pesos regulares ou em negrito.

### <a name="color"></a>Cor

No HoloLens, como os hologramas são construídos com um sistema leve aditivo, o texto em branco é altamente legível. Você pode encontrar exemplos de texto em branco no menu iniciar e na barra de aplicativos. Embora o texto em branco funcione bem sem uma chapa de apoio no HoloLens, um plano de fundo físico complexo poderia dificultar a leitura do tipo. Para melhorar o foco do usuário e minimizar a distração de um plano de fundo físico, é recomendável usar o texto em branco em uma chapa de apoio escuro ou colorido.

<br>


![é recomendável usar o texto branco em uma chapa de fundo escura ou colorida.](images/typography-whiteonblack2-1000px.jpg)
*exemplos de texto em branco em uma chapa de fundo escura ou colorida.*
<br>

Para usar texto escuro, você deve usar uma chapa de fundo brilhante para torná-la legível. Em sistemas de cores aditivos, o preto é exibido como transparente. Isso significa que você não poderá ver o texto em preto sem uma chapa de fundo colorida.

:::row:::
    :::column:::
        ![exemplos de texto em preto](images/typography-whiteonblack.png)<br>
        *Exemplos de branco em preto e preto em texto branco*<br>
    :::column-end:::
    :::column:::
        ![exemplos de texto em preto](images/640px-typography-blackonwhite.jpg)<br>
        *Exemplos de texto preto nos aplicativos do sistema – armazenamento e configurações*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>Tamanho de fonte recomendado

Como você pode esperar, os tamanhos de tipo que usamos em um PC ou um dispositivo Tablet (normalmente entre 12 e 32pt) parecem muito pequenos em uma distância de 2 metros. Depende das características de cada fonte, mas, em geral, o ângulo de exibição mínimo recomendado e a altura da fonte para legibilidade estão em torno de 0.35 °-0.4 °/12.21-13.97mm, com base em nossos estudos de pesquisa de usuários. É cerca de 35 40pt com o fator de dimensionamento introduzido no [texto na página do Unity](text-in-unity.md) . 

Para a interação próxima no 0.45 m (45cm), o ângulo de exibição da fonte mínimo legível e a altura são 0.4 °-0,5 °/3.14 – 3.9 mm. É cerca de 9 12 pt com o fator de dimensionamento introduzido no [texto no Unity](text-in-unity.md).

![intervalo de interação próximo e longe](images/typography-distance-1000px.jpg)
*conteúdo em um intervalo de interação próximo e longe*

### <a name="the-minimum-legible-font-size"></a>O tamanho mínimo de fonte legível
| Alcance | Ângulo de exibição | Altura do texto | Tamanho da fonte * * |
|---------|---------|---------|---------|
| 45cm (distância de manipulação direta) | 0.4 °-0,5 ° | 3.14 – 3.9 mm | 8.9 – 11.13 pt |
| m | 0.35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>O tamanho de fonte legível confortavelmente
| Alcance | Ângulo de exibição | Altura do texto | Tamanho da fonte * * |
|---------|---------|---------|---------|
| 45cm (distância de manipulação direta) | 0.65 °-0,8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| m | 0,6 ° a 0,75 ° | 20,9-26.2 mm | 59.4-74.2 pt |


Segoe UI (a fonte padrão do Windows) funciona bem na maioria dos casos. No entanto, evite usar famílias de fontes leves ou semileves em tamanho pequeno, uma vez que traços verticais finos serão vibrantes e diminuirá a legibilidade. Fontes modernas com espessura de traço suficiente funcionam bem. Por exemplo, Helvetica e Arial parecem grandioso e são muito legíveis no HoloLens com pesos normais ou em negrito.

**Para obter informações mais detalhadas sobre o cálculo do tamanho do texto no Unity, consulte [texto no Unity](text-in-unity.md)**

![ângulo de exibição](images/Text_In_Unity_ViewingAngle.jpg)
*exibição da distância, do ângulo e da altura do texto*

<br>

---

## <a name="resources"></a>Recursos

:::row:::
    :::column:::
    ### <a name="segoe-fontshttpsdownloadmicrosoftcomdownload1bc1bcf071a-78ee-4968-acbe-15461c274b61segoe20fonts20v1705zipbr"></a>[Fontes Segoe](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (Arquivo zip)<br>
    ### <a name="hololens-fonthttpsdownloadmicrosoftcomdownload38d38d659e2-4b9c-413a-b2e7-1956181dc427hololens20fontzipbr"></a>[Fonte do HoloLens](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (Arquivo zip)<br>
    <br>
    *Imagem: a fonte do HoloLens fornece os glifos de símbolo usados na realidade mista do Windows.*
    :::column-end:::
        :::column:::
        ![A fonte do HoloLens fornece os glifos de símbolo usados na realidade misturada do Windows](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a>Consulte também
* [Texto no Unity](text-in-unity.md)
* [Cor, luz e materiais](color,-light-and-materials.md)

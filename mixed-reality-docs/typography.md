---
title: Tipografia
description: Texto é um elemento importante para distribuição de informações de sua experiência de aplicativo.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, estilo, fonte, tipografia, interface do usuário, experiência do usuário
ms.openlocfilehash: b4bac35cbc412ec7102748350c2f5c1e236c2f7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590601"
---
# <a name="typography"></a>Tipografia

Texto é um elemento importante para distribuição de informações de sua experiência de aplicativo. Assim como tipografia nas telas 2D, o objetivo é ser claro e legível. Com o aspecto tridimensional da realidade misturada, há uma oportunidade para afetar o texto e o usuário geral experiência de forma ainda maior.

![Exemplo de tipografia no HoloLens](images/640px-typography-hero2.jpg)<br>
*Exemplo de tipografia no HoloLens*

Quando falamos sobre o tipo em 3D, tendemos a pensar extrusão, volumétricos texto 3D. Exceto para alguns designs de logotipo e alguns outros aplicativos limitados, o texto extrusão tende a degradar a legibilidade do texto. Mesmo que estamos criando experiências para 3D, podemos usar 2D para o tipo porque ele é mais legível e fácil de ler.

No HoloLens, o tipo é construído com hologramas usando luz com base no sistema de Cores aditivas. Assim como outras hologramas tipo pode ser colocado no ambiente real em que pode ser bloqueado e observado de qualquer ângulo de mundo. O [parallax](https://en.wikipedia.org/wiki/Parallax) efeito entre o tipo e o ambiente também adiciona profundidade para a experiência.

## <a name="typography-in-mixed-reality"></a>Tipografia na realidade mista

Regras tipográficas na realidade mista não são diferentes de qualquer outra coisa. O texto no mundo físico e o mundo virtual precisa ser legíveis e legíveis. Texto pode ser em uma parede ou sobrepostas em um objeto físico. Ele poderia ser flutuante junto com uma interface do usuário digital. Independentemente do contexto, aplicamos as mesmas regras tipográficas para leitura e reconhecimento.

### <a name="create-clear-hierarchy"></a>Criar hierarquia clara

Crie hierarquia e contraste usando pesos e diversos tamanhos de tipo. Definindo uma rampa de tipo e depois dele em toda a experiência de aplicativo fornece uma excelente experiência de usuário com a hierarquia de informações consistente.

![Exemplos de rampa de tipo](images/typography-ramp-1000px.jpg)<br>
*Exemplos de rampa de tipo*

### <a name="limit-your-fonts"></a>Limitar as fontes

Evite usar mais de duas famílias de fontes diferentes em um único contexto. Isso interromperá a harmonia e a consistência de sua experiência e torná-lo mais difícil de consumir informações. No HoloLens, já que as informações são sobrepostas sobre o ambiente físico, usar vários estilos de fonte poderá degradar a experiência. Segoe UI é a fonte para todos os designs de digital da Microsoft. Ele é usado consistentemente no shell do Windows Mixed Reality. Você pode baixar o arquivo de fonte do Segoe UI a [página de kit de ferramentas de design do Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Para obter mais informações sobre a face de tipos do Segoe UI](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evite pesos fonte dinâmico

Evite usar pesos de fonte de luz ou semilight para tamanhos de tipo em 42pt, como traços verticais finos serão Vibrar e prejudicar a legibilidade. Fontes modernos com suficiente espessura do traço funcionam muito bem. Por exemplo, Helvetica e Arial são muito legível em HoloLens usar pesos regulares ou em negrito.

### <a name="color"></a>Cor

HoloLens, desde que o hologramas são construídas com um sistema leve aditivo, texto em branco é altamente legível. Você pode encontrar exemplos de texto em branco no menu Iniciar e barra de aplicativos. Mesmo que o texto em branco funciona bem sem um prato voltar em HoloLens, um plano de fundo físico complexo poderia tornar o tipo difíceis de ler. Para melhorar o foco do usuário e minimizar a distração de um plano de fundo físico, é recomendável usar texto em branco em um prato colorido novamente ou escuro.

<br>


![É recomendável usar texto em branco em um prato fundo colorido ou escuro.](images/typography-whiteonblack2-1000px.jpg)

É recomendável usar texto em branco em um prato fundo colorido ou escuro.

<br>


![Exemplos de texto em preto](images/640px-typography-textcolors.jpg)

Para usar texto escuro, você deve usar um prato back brilhante para torná-lo mais legível. Em sistemas de Cores aditivas, preto é exibido como transparente. Isso significa que você não poderá ver o texto preto sem um coloridas placa traseira.

<br>


![Exemplos de texto em preto](images/640px-typography-blackonwhite.jpg)

Você pode encontrar exemplos de texto preto em aplicativos UWP, como as configurações ou Store.

## <a name="recommended-font-size"></a>Tamanho da fonte recomendado

![Dois medidores é a distância ideal para a exibição de texto.](images/typography-distance-1000px.jpg)

Dois medidores é a distância ideal para a exibição de texto.

Como a realidade misturada envolve profundidade tridimensional, não é sempre fácil para se comunicar o tamanho da fonte. Para o conforto do usuário, dois medidores é a distância ideal para posicionamento hologramas. Podemos usar essa distância como base para encontrar o tamanho da fonte ideal.

Como você pode esperar, tamanhos de tipo que usamos em um computador ou um dispositivo de tablet (normalmente entre 12 – 32 pt) parecer muito pequenos em uma distância de 2 metros. Ele depende das características de cada fonte, mas em geral, o tamanho do tipo mínimo recomendado para manter a legibilidade sem vibração traço é cerca de 30pt. Se seu aplicativo deve ser usado em uma distância mais próxima, tamanhos menores de tipo pode ser usados. **O tamanho do ponto se baseia em texto de interface do usuário e de malha texto 3D do Unity. Para as métricas detalhadas e os fatores de dimensionamento, consulte [texto no Unity](text-in-unity.md).**

## <a name="resources"></a>Recursos
* [Fontes do Segoe](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [HoloLens font](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![A fonte do HoloLens lhe dá os glifos de símbolo usados na realidade mista do Windows](images/300px-hololensmdl2symbols.jpg)

A fonte do HoloLens fornece os glifos de símbolo usados na realidade mista do Windows.

## <a name="see-also"></a>Consulte também
* [Texto no Unity](http://holodocsfuture/index.php?title=Text_in_Unity&action=edit&redlink=1)
* [Cor, luz e materiais](color,-light-and-materials.md)

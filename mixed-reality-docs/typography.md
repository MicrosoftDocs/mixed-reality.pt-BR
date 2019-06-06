---
title: Tipografia
description: Texto é um elemento importante para distribuição de informações de sua experiência de aplicativo.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, estilo, fonte, tipografia, interface do usuário, experiência do usuário
ms.openlocfilehash: debf125a7f82ac79fe3ad776ba9c8c0b69396848
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692383"
---
# <a name="typography"></a>Tipografia

Texto é um elemento importante para distribuição de informações de sua experiência de aplicativo. Assim como tipografia nas telas 2D, o objetivo é ser claro e legível. Com o aspecto tridimensional da realidade misturada, há uma oportunidade para afetar o texto e o usuário geral experiência de forma ainda maior.

![Exemplo de tipografia no HoloLens](images/typography-cover.png)<br>
*Exemplo de tipografia no HoloLens*

Quando falamos sobre o tipo em 3D, tendemos a pensar extrusão, volumétricos texto 3D. Exceto para alguns designs de logotipo e alguns outros aplicativos limitados, o texto extrusão tende a degradar a legibilidade do texto. Mesmo que estamos criando experiências para 3D, podemos usar 2D para o tipo porque ele é mais legível e fácil de ler.

No HoloLens, o tipo é construído com hologramas usando luz com base no sistema de Cores aditivas. Assim como outras hologramas tipo pode ser colocado no ambiente real em que pode ser bloqueado e observado de qualquer ângulo de mundo. O [parallax](https://en.wikipedia.org/wiki/Parallax) efeito entre o tipo e o ambiente também adiciona profundidade para a experiência.

## <a name="typography-in-mixed-reality"></a>Tipografia na realidade mista

Regras tipográficas na realidade mista não são diferentes de qualquer outra coisa. O texto no mundo físico e o mundo virtual precisa ser legíveis e legíveis. Texto pode ser em uma parede ou sobrepostas em um objeto físico. Ele poderia ser flutuante junto com uma interface do usuário digital. Independentemente do contexto, aplicamos as mesmas regras tipográficas para leitura e reconhecimento.

### <a name="create-clear-hierarchy"></a>Criar hierarquia clara

Crie hierarquia e contraste usando pesos e diversos tamanhos de tipo. Definindo uma rampa de tipo e depois dele em toda a experiência de aplicativo fornece uma excelente experiência de usuário com a hierarquia de informações consistente.

![Exemplos de rampa de tipo](images/typography-ramp-1000px.jpg)<br>
*Definir seu rampa de tipo e segui-lo em toda a experiência de aplicativo*

### <a name="limit-your-fonts"></a>Limitar as fontes

Evite usar mais de duas famílias de fontes diferentes em um único contexto. Isso interromperá a harmonia e a consistência de sua experiência e torná-lo mais difícil de consumir informações. No HoloLens, já que as informações são sobrepostas sobre o ambiente físico, usar vários estilos de fonte poderá degradar a experiência. Segoe UI é a fonte para todos os designs de digital da Microsoft. Ele é usado consistentemente no shell do Windows Mixed Reality. Você pode baixar o arquivo de fonte do Segoe UI a [página de kit de ferramentas de design do Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Para obter mais informações sobre a face de tipos do Segoe UI](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evite pesos fonte dinâmico

Evite usar pesos de fonte de luz ou semilight para tamanhos de tipo em 42pt, como traços verticais finos serão Vibrar e prejudicar a legibilidade. Fontes modernos com suficiente espessura do traço funcionam muito bem. Por exemplo, Helvetica e Arial são muito legível em HoloLens usar pesos regulares ou em negrito.

### <a name="color"></a>Cor

HoloLens, desde que o hologramas são construídas com um sistema leve aditivo, texto em branco é altamente legível. Você pode encontrar exemplos de texto em branco no menu Iniciar e barra de aplicativos. Mesmo que o texto em branco funciona bem sem um prato voltar em HoloLens, um plano de fundo físico complexo poderia tornar o tipo difíceis de ler. Para melhorar o foco do usuário e minimizar a distração de um plano de fundo físico, é recomendável usar texto em branco em um prato colorido novamente ou escuro.

<br>


![É recomendável usar texto em branco em um prato fundo colorido ou escuro. ](images/typography-whiteonblack2-1000px.jpg)
 *Exemplos de texto em branco em um prato fundo colorido ou escuro.*
<br>

Para usar texto escuro, você deve usar um prato back brilhante para torná-lo mais legível. Em sistemas de Cores aditivas, preto é exibido como transparente. Isso significa que você não poderá ver o texto preto sem um coloridas placa traseira.

![Exemplos de texto em preto](images/typography-whiteonblack.png)
<br>*Exemplos de na traseira preto e branco no texto em branco*


![Exemplos de texto em preto](images/640px-typography-blackonwhite.jpg)
<br>*Exemplos de texto preto em aplicativos do sistema - Store e configurações*

## <a name="recommended-font-size"></a>Tamanho da fonte recomendado

Como você pode esperar, tamanhos de tipo que usamos em um computador ou um dispositivo de tablet (normalmente entre 12 – 32 pt) parecer muito pequenos em uma distância de 2 metros. Ele depende das características de cada fonte, mas em geral, são o mínimo recomendado, exibindo o ângulo e a altura da fonte para manter a legibilidade em torno de 0.35°-0.4°/12.21-13.97mm com base em nossos estudos de pesquisa do usuário. Trata-se 35 40pt com o fator de escala apresentado acima. 

Para a interação quase em 0.45m(45cm), ângulo de exibição da fonte legível mínima e a altura são 0.4 °-0,5 ° / 3.14 – 3.9 mm. Trata-se 9-12 pt com o fator de escala apresentado acima.

![Próximo e longe intervalo interação](images/typography-distance-1000px.jpg)
*intervalo de interação de conteúdo no próximo e distante*

### <a name="the-minimum-legible-font-size"></a>O tamanho mínimo da fonte legível
| distância | Ângulo de exibição | Altura do texto | Tamanho de fonte * * |
|---------|---------|---------|---------|
| 45cm (distância manipulação direta) | 0.4°-0.5° | 3.14 – 3.9 mm | 8.9 – 11.13pt |
| 2 min | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>O tamanho da fonte confortavelmente legível
| distância | Ângulo de exibição | Altura do texto | Tamanho de fonte * * |
|---------|---------|---------|---------|
| 45cm (distância manipulação direta) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8pt |
| 2 min | 0.6°-0.75° | 20,9-26.2 mm | 59.4-74.2pt |


Segoe UI (a fonte padrão para Windows) funciona bem na maioria dos casos. No entanto, evite usando as famílias de fontes de luz de luz ou semi de tamanho pequeno, pois traços verticais finos serão Vibrar e ele prejudicará a legibilidade. Fontes modernos com suficiente espessura do traço funcionam muito bem. Por exemplo, Helvetica e Arial parecer bonitas e são muito legível em HoloLens com pesos regulares ou em negrito.

* * Para obter mais informações sobre o cálculo do tamanho do texto no Unity, consulte a página [texto no Unity](text-in-unity.md)

![Ângulo de visualização](images/Text_In_Unity_ViewingAngle.jpg)
*exibindo a altura de distância, ângulo e texto*

## <a name="resources"></a>Recursos
* [Fontes do Segoe](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [HoloLens font](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![A fonte do HoloLens lhe dá os glifos de símbolo usados na realidade mista do Windows](images/300px-hololensmdl2symbols.jpg)
<br>*A fonte do HoloLens fornece os glifos de símbolo usados na realidade mista do Windows.*

## <a name="see-also"></a>Consulte também
* [Texto no Unity](text-in-unity.md)
* [Cor, luz e materiais](color,-light-and-materials.md)

---
title: Texto no Unity
description: Para exibir o texto no Unity, há dois tipos de componentes de texto, você pode usar — o texto de interface do usuário e o texto 3D de malha.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, design, controles, fonte, tipografia, interface do usuário, experiência do usuário
ms.openlocfilehash: 7d40db2e0571e835e28e444c7921e1a086800936
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829971"
---
# <a name="text-in-unity"></a>Texto no Unity

Texto é um dos componentes mais importantes em aplicativos holographic. Para exibir o texto no Unity, há três tipos de componentes de texto, você pode usar — texto de interface do usuário, de malha 3D texto e texto de malha Pro. Por padrão o texto de interface do usuário e de malha 3D texto aparecem desfocado e são muito grandes. É preciso ajustar algumas variáveis para obter texto nítido e de alta qualidade que tem um tamanho gerenciável em HoloLens. Ao aplicar o fator de escala para obter as dimensões apropriadas ao usar o texto de interface do usuário e os componentes de texto de malha 3D, você pode obter a melhor qualidade de renderização.

![Como obter o texto nítido e Belo](images/hug-text-02-640px.png)<br>
*Texto desfocado padrão no Unity*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>Trabalhando com texto 3D (texto malha) e o texto da interface do usuário do Unity

Unity pressupõe que todos os novos elementos adicionados a uma cena 1 unidade do Unity no tamanho ou escala de transformação de 100%, que se traduz em cerca de 1 metro em HoloLens. No caso de fontes, a caixa delimitadora para um TextMesh 3D vem em por padrão, em cerca de 1 metro de altura.

![Trabalhando com fontes no Unity](images/640px-hug-text-03.png)<br>
*Texto 3D do Unity padrão (texto de malha) ocupa 1 unidade do Unity, que é de 1 metro*

<br>
A maioria dos designers visuais usam pontos para definir tamanhos de fonte no mundo real. Há cerca de 2835 (2,834.645666399962) pontos em 1 metro. Com base na conversão de sistema de ponto de 1 metro e texto de malha tamanho da fonte padrão do Unity de 13, o cálculo simple de 13 dividido por 2835 é igual a 0.0046 (0.004586111116 para ser mais exato) fornece um bom padrão de dimensionamento para começar (alguns talvez queira arredondar como 0,005). Dimensionar o objeto de texto ou no contêiner para esses valores não permitirá somente para a conversão de 1:1 da fonte tamanhos em um programa de design, mas também fornece um padrão para que possa manter a consistência em toda a sua experiência.

![Unity malha texto 3D com diferentes tamanhos de fontes](images/Text_In_Unity_Measurements1.png)<br>
*Valores de escala para o texto 3D do Unity e o texto de interface do usuário*

![Unity malha texto 3D com diferentes tamanhos de fontes](images/hug-text-05-1000px.png)<br>
*Unity malha texto 3D com valores otimizados*

<br>
Ao adicionar um elemento de texto com base da interface do usuário ou de tela a uma cena, a diferença de tamanho é ainda maior. As diferenças em dois tamanhos é aproximadamente 1000%, que trará o fator de escala para componentes da interface do usuário com base em texto 0.00046 (0.0004586111116 para ser mais exato) ou 0,0005 para o valor arredondado.

![Texto de interface do usuário do Unity com diferentes pixels dinâmicas por valores de unidade](images/hug-text-04-1000px.png)<br>
*Texto de interface do usuário do Unity com valores otimizados*

<br>

>[!NOTE]
>O valor padrão de qualquer fonte que pode ser afetado pelo tamanho da textura de fonte ou como a fonte foi importada para o Unity. Esses testes foram executados com base em como a fonte Arial de padrão no Unity, bem como uma outra fonte importada.

## <a name="working-with-text-mesh-pro"></a>Trabalhar com texto de malha Pro

Com o texto de malha Pro do Unity, você pode garantir a qualidade de renderização de texto. Ele dá suporte à estrutura de tópicos de textos, independentemente da distância usando a [SDF (campo de distância assinado)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) técnica. Usando o mesmo método de cálculo que usamos acima para o texto 3D de malha e o texto de interface do usuário, podemos encontrar os valores de escala apropriados usar ponto tipográfico convencional. Uma vez que a fonte de texto de malha Pro 3D padrão com o tamanho de 36 mostra o delimitador de 2,5 Unit(2.5m) do Unity, podemos usar o valor de escala 0,005 para usar o tamanho de ponto. O texto de malha Pro no menu de interface do usuário tem o padrão de limitação de tamanho de 25 Unit(25m) do Unity. Isso nos dá 0,0005 para o valor de escala.

![Unity malha texto 3D com diferentes tamanhos de fontes](images/Text_In_Unity_Measurements2.png)<br>
*Valores de escala para o texto 3D do Unity e o texto de interface do usuário*

## <a name="recommended-text-size"></a>Tamanho do texto recomendada
Como você pode esperar, tamanhos de tipo que usamos em um computador ou um dispositivo de tablet (normalmente entre 12 – 32 pt) parecer muito pequenos em uma distância de 2 metros. Ele depende das características de cada fonte, mas em geral, são o mínimo recomendado, exibindo o ângulo e a altura da fonte para manter a legibilidade em torno de 0.35°-0.4°/12.21-13.97mm com base em nossos estudos de pesquisa do usuário. Trata-se 35 40pt com o fator de escala apresentado acima. 

Para a interação quase em 0.45m(45cm), ângulo de exibição da fonte legível mínima e a altura são 0.4 °-0,5 ° / 3.14 – 3.9 mm. Trata-se 9-12 pt com o fator de escala apresentado acima.

![Próximo e longe intervalo interação](images/typography-distance-1000px.jpg)
*intervalo de interação de conteúdo no próximo e distante*

### <a name="the-minimum-legible-font-size"></a>O tamanho mínimo da fonte legível
| distância | Ângulo de exibição | Altura do texto | Tamanho da fonte |
|---------|---------|---------|---------|
| 45cm (distância manipulação direta) | 0.4°-0.5° | 3.14 – 3.9 mm | 8.9 – 11.13pt |
| 2 min | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>O tamanho da fonte confortavelmente legível
| distância | Ângulo de exibição | Altura do texto | Tamanho da fonte |
|---------|---------|---------|---------|
| 45cm (distância manipulação direta) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8pt |
| 2 min | 0.6°-0.75° | 20,9-26.2 mm | 59.4-74.2pt |

Segoe UI (a fonte padrão para Windows) funciona bem na maioria dos casos. No entanto, evite usando as famílias de fontes de luz de luz ou semi de tamanho pequeno, pois traços verticais finos serão Vibrar e ele prejudicará a legibilidade. Fontes modernos com suficiente espessura do traço funcionam muito bem. Por exemplo, Helvetica e Arial parecer bonitas e são muito legível em HoloLens com pesos regulares ou em negrito.


![Ângulo de visualização](images/Text_In_Unity_ViewingAngle.jpg)
*exibindo a altura de distância, ângulo e texto*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Qualidade de renderização de texto com dimensões adequadas de sustenido

Com base nesses fatores de dimensionamento, nós criamos [pré-fabricados de texto com texto de interface do usuário e de malha 3D texto](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text). Os desenvolvedores podem usar essas pré-fabricados para obter o tamanho da fonte consistente e texto nítidos.

![Qualidade de renderização de texto com dimensões adequadas de sustenido](images/hug-text-06-1000px.png)<br>
*Qualidade de renderização de texto com dimensões adequadas de sustenido*

## <a name="shader-with-occlusion-support"></a>Sombreador com suporte de oclusão

Material de fonte padrão do Unity não oferece suporte a oclusão. Por isso, você verá o texto atrás dos objetos por padrão. Incluímos um simples [sombreador que dá suporte à oclusão](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader). A imagem abaixo mostra o texto com o material de fonte padrão (à esquerda) e o texto com oclusão adequada (à direita).

![Sombreador com suporte de oclusão](images/hug-text-07-1000px.png)<br>
*Sombreador com suporte de oclusão*


## <a name="see-also"></a>Consulte também
* [Texto pré-fabricado no MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [Tipografia](typography.md)

 

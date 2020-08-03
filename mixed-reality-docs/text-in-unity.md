---
title: Texto no Unity
description: Para exibir texto no Unity, há dois tipos de componentes de texto que você pode usar — texto da interface do usuário e malha de texto 3D.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, design, controles, fonte, tipografia, interface do usuário, UX
ms.openlocfilehash: 63f0992a4623cf91c1b9c62c4ebf30de12529515
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476938"
---
# <a name="text-in-unity"></a>Texto no Unity

O texto é um dos componentes mais importantes nos aplicativos Holographic. Para exibir texto no Unity, há três tipos de componentes de texto que você pode usar — texto da interface do usuário, malha de texto 3D e malha de texto pro. Por padrão, o texto da interface do usuário e a malha de texto 3D aparecem borrados e são muito grandes. Você precisa ajustar algumas variáveis para obter um texto nítido e de alta qualidade que tenha um tamanho gerenciável no HoloLens. Ao aplicar um fator de dimensionamento para obter dimensões adequadas ao usar o texto da interface do usuário e componentes de malha de texto 3D, você pode obter uma melhor qualidade de renderização.

![Como obter texto nítido e bonito](images/hug-text-02-640px.png)<br>
*Texto padrão borrado no Unity*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Trabalhando com texto 3D do Unity (malha de texto) e texto da interface do usuário

O Unity pressupõe que todos os novos elementos adicionados a uma cena tenham uma unidade Unity de tamanho ou uma escala de transformação de 100%, o que traduz em cerca de 1 metro no HoloLens. No caso de fontes, a caixa delimitadora para um textmesh 3D entra por padrão em aproximadamente 1 metro de altura.

![Trabalhando com fontes no Unity](images/640px-hug-text-03.png)<br>
*O texto 3D de Unity (malha de texto) padrão ocupa uma unidade Unity que é de 1 metro*

<br>
A maioria dos designers visuais usa pontos para definir tamanhos de fonte no mundo real. Há cerca de 2835 pontos (2, 834.645666399962) em 1 metro. Com base na conversão de sistema de ponto para 1 medidor e tamanho de fonte de malha de texto padrão de Unity de 13, a matemática simples de 13 dividido por 2835 é igual a 0, 46 (0.004586111116 para ser exato), que fornece uma boa escala padrão para começar (algumas podem ser arredondadas para 0, 5). Dimensionar o objeto de texto ou o contêiner para esses valores não só permitirá a conversão 1:1 de tamanhos de fonte em um programa de design, mas também fornecerá um padrão para que você possa manter a consistência em toda a sua experiência.

![Malha de texto 3D do Unity com tamanhos de fonte diferentes](images/Text_In_Unity_Measurements1.png)<br>
*Dimensionamento de valores para texto 3D do Unity e texto da interface do usuário*

<br>

![Malha de texto 3D do Unity com tamanhos de fonte diferentes](images/hug-text-05-1000px.png)<br>
*Malha de texto 3D do Unity com valores otimizados*

<br>
Ao adicionar um elemento de texto baseado na interface do usuário ou tela a uma cena, o tamanho da disparidade ainda é maior. As diferenças nos dois tamanhos são cerca de 1000%, o que levaria o fator de escala para componentes de texto baseados na interface do usuário a 0, 46 (0.0004586111116 para ser exato) ou 0, 5 para o valor arredondado.

![Texto da interface do usuário do Unity com diferentes pixels dinâmicos por valores de unidade](images/hug-text-04-1000px.png)<br>
*Texto da interface do usuário do Unity com valores otimizados*

<br>

>[!NOTE]
>O valor padrão de qualquer fonte pode ser afetado pelo tamanho da textura dessa fonte ou como a fonte foi importada para o Unity. Esses testes foram executados com base na fonte Arial padrão no Unity, bem como uma outra fonte importada.

## <a name="working-with-text-mesh-pro"></a>Trabalhando com a malha de texto pro

Com o Text mesh pro da Unity, você pode proteger a qualidade de renderização do texto. Ele dá suporte a contornos de texto nítidos, independentemente da distância usando a técnica de [SDF (conexão de campo de distância) assinada](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) . Usando o mesmo método de cálculo que usamos acima para a malha de texto 3D e o texto da interface do usuário, podemos encontrar os valores de dimensionamento adequados a serem usados com pontos tipográficos convencionais. Como a fonte pro de malha de texto 3D padrão com o tamanho de 36 tem um tamanho delimitador de 2,5 unidades de Unity (2,5 m), podemos usar um valor de dimensionamento de 0, 5 para obter o tamanho do ponto. O Text mesh pro no menu da interface do usuário tem um tamanho delimitador padrão de 25 unidades de Unity (25m). Isso nos dá 0, 5 para o valor de dimensionamento.

![Malha de texto 3D do Unity com tamanhos de fonte diferentes](images/Text_In_Unity_Measurements2.png)<br>
*Dimensionamento de valores para texto 3D do Unity e texto da interface do usuário*

## <a name="recommended-text-size"></a>Tamanho de texto recomendado
Como você pode esperar, os tamanhos de tipo que usamos em um PC ou um dispositivo Tablet (normalmente entre 12 e 32pt) parecem muito pequenos em uma distância de 2 metros. Depende das características de cada fonte, mas, em geral, o ângulo de exibição mínimo recomendado e a altura da fonte para legibilidade estão em torno de 0.35 °-0.4 °/12.21-13.97mm, com base em nossos estudos de pesquisa de usuários. É cerca de 35 40pt com o fator de dimensionamento apresentado acima. 

Para a interação próxima no 0.45 m (45cm), o ângulo de exibição da fonte mínimo legível e a altura são 0.4 °-0,5 °/3.14 – 3.9 mm. É cerca de 9 12 pt com o fator de dimensionamento apresentado acima.

![Conteúdo de intervalo de interação próxima e longe ](images/typography-distance-1000px.jpg)
 *em um intervalo de interação próximo e longe*

### <a name="the-minimum-legible-font-size"></a>O tamanho mínimo de fonte legível
| Distância | Ângulo de exibição | Altura do texto | Tamanho da fonte |
|---------|---------|---------|---------|
| 45cm (distância de manipulação direta) | 0.4 °-0,5 ° | 3.14 – 3.9 mm | 8.9 – 11.13 pt |
| m | 0.35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>O tamanho de fonte legível confortavelmente
| Distância | Ângulo de exibição | Altura do texto | Tamanho da fonte |
|---------|---------|---------|---------|
| 45cm (distância de manipulação direta) | 0.65 °-0,8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| m | 0,6 ° a 0,75 ° | 20,9-26.2 mm | 59.4-74.2 pt |

Segoe UI (a fonte padrão do Windows) funciona bem na maioria dos casos. No entanto, evite usar famílias de fontes leves ou semileves em tamanho pequeno, uma vez que traços verticais finos serão vibrantes e diminuirá a legibilidade. Fontes modernas com espessura de traço suficiente funcionam bem. Por exemplo, Helvetica e Arial parecem grandioso e são muito legíveis no HoloLens com pesos normais ou em negrito.


![Exibindo ângulo ](images/Text_In_Unity_ViewingAngle.jpg)
 *exibindo a distância, o ângulo e a altura do texto*

## <a name="text-with-mixed-reality-toolkit-v2"></a>Texto com o kit de ferramentas de realidade misturada v2

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Qualidade de renderização de texto nítido com dimensão adequada

Com base nesses fatores de dimensionamento, criamos [texto pré-fabricados com o texto da interface do usuário e a malha de texto 3D](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text). Os desenvolvedores podem usar esses pré-fabricados para obter texto nítido e tamanho de fonte consistente.

![Qualidade de renderização de texto nítido com dimensão adequada](images/hug-text-06-1000px.png)<br>
*Qualidade de renderização de texto nítido com dimensão adequada*

### <a name="shader-with-occlusion-support"></a>Sombreador com suporte a oclusão

O material de fonte padrão do Unity não oferece suporte a oclusão. Por isso, você verá o texto por trás dos objetos por padrão. Incluímos um [sombreador simples que dá suporte ao oclusão](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MRTK/Core/StandardAssets/Shaders/Text3DShader.shader). A imagem abaixo mostra o texto com material de fonte padrão (esquerda) e o texto com oclusão apropriado (direita).

![Sombreador com suporte a oclusão](images/hug-text-07-1000px.png)<br>
*Sombreador com suporte a oclusão*


## <a name="see-also"></a>Consulte também
* [Pré-fabricado de texto no MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [Tipografia](typography.md)

 

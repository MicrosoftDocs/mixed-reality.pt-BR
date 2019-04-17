---
title: Texto no Unity
description: Para exibir o texto no Unity, há dois tipos de componentes de texto, você pode usar — o texto de interface do usuário e o texto 3D de malha.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, controles, fonte, tipografia, interface do usuário, experiência do usuário
ms.openlocfilehash: 02f282ab80a44190d21d2dadefeb7a624c862d04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590707"
---
# <a name="text-in-unity"></a>Texto no Unity

Texto é um dos componentes mais importantes em aplicativos holographic. Para exibir o texto no Unity, há dois tipos de componentes de texto, você pode usar — o texto de interface do usuário e o texto 3D de malha. Por padrão, eles aparecem desfocados e são muito grandes. É preciso ajustar algumas variáveis para obter texto nítido e de alta qualidade que tem um tamanho gerenciável em HoloLens. Ao aplicar o fator de escala para obter as dimensões apropriadas ao usar o texto de interface do usuário e os componentes de texto de malha 3D, você pode obter a melhor qualidade de renderização.

![Como obter o texto nítido e Belo](images/hug-text-02-640px.png)<br>
*Texto desfocado padrão no Unity*

## <a name="working-with-fonts-in-unity"></a>Trabalhando com fontes no Unity

Unity pressupõe que todos os novos elementos adicionados a uma cena 1 unidade do Unity no tamanho ou escala de transformação de 100%, que se traduz em cerca de 1 metro em HoloLens. No caso de fontes, a caixa delimitadora para um TextMesh 3D vem em por padrão, em cerca de 1 metro de altura.

![Trabalhando com fontes no Unity](images/640px-hug-text-03.png)<br>
*Texto do Unity padrão ocupa 1 unidade do Unity, que é de 1 metro*

<br>
A maioria dos designers visuais usam pontos para definir tamanhos de fonte no mundo real. Há cerca de 2835 (2,834.645666399962) pontos em 1 metro. Com base na conversão de sistema de ponto de 1 metro e texto de malha tamanho da fonte padrão do Unity de 13, o cálculo simple de 13 dividido por 2835 é igual a 0.0046 (0.004586111116 para ser mais exato) fornece um bom padrão de dimensionamento para começar (alguns talvez queira arredondar como 0,005). Dimensionar o objeto de texto ou no contêiner para esses valores não só permitirá para conversão da fonte 1:1, os tamanhos em um programa de design, mas também fornece um padrão para que você possa manter a consistência em todo o seu aplicativo ou jogo.

![Unity malha texto 3D com diferentes tamanhos de fontes](images/hug-text-05-1000px.png)<br>
*Unity malha texto 3D com valores otimizados*

<br>
Ao adicionar um elemento de texto com base da interface do usuário ou de tela a uma cena, a diferença de tamanho é ainda maior. As diferenças em dois tamanhos é aproximadamente 1000%, que trará o fator de escala para componentes da interface do usuário com base em texto 0.00046 (0.0004586111116 para ser mais exato) ou 0,0005 para o valor arredondado.

![Texto de interface do usuário do Unity com diferentes pixels dinâmicas por valores de unidade](images/hug-text-04-1000px.png)<br>
*Texto de interface do usuário do Unity com valores otimizados*

<br>

>[!NOTE]
>O valor padrão de qualquer fonte que pode ser afetado pelo tamanho da textura de fonte ou como a fonte foi importada para o Unity. Esses testes foram executados com base em como a fonte Arial de padrão no Unity, bem como uma outra fonte importada.

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Qualidade de renderização de texto com dimensões adequadas de sustenido

Com base nesses fatores de dimensionamento, nós criamos [dois pré-fabricados - texto de interface do usuário e a malha de texto 3D](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs). Os desenvolvedores podem usar essas pré-fabricados para obter o tamanho da fonte consistente e texto nítidos.

![Qualidade de renderização de texto com dimensões adequadas de sustenido](images/hug-text-06-1000px.png)<br>
*Qualidade de renderização de texto com dimensões adequadas de sustenido*

## <a name="shader-with-occlusion-support"></a>Sombreador com suporte de oclusão

Material de fonte padrão do Unity não oferece suporte a oclusão. Por isso, você verá o texto atrás dos objetos por padrão. Incluímos um simples [sombreador que dá suporte à oclusão](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders). A imagem abaixo mostra o texto com o material de fonte padrão (à esquerda) e o texto com oclusão adequada (à direita).

![Sombreador com suporte de oclusão](images/hug-text-07-1000px.png)<br>
*Sombreador com suporte de oclusão*

## <a name="recommended-type-size"></a>Tamanho do tipo recomendado

Como você pode esperar, tamanhos de tipo que usamos em um computador ou um dispositivo de tablet (normalmente entre 12 – 32 pt) parecer muito pequenos em uma distância de 2 metros. Ele depende das características de cada fonte, mas em geral o tamanho do tipo mínimo recomendado para manter a legibilidade sem vibração traço é em torno de 30pt, com base no fator de dimensionamento apresentado acima. Se seu aplicativo deve ser usado em uma distância mais próxima, tamanhos menores de tipo pode ser usados. Para a seleção de fonte, a Segoe UI (a fonte padrão para Windows) funciona bem na maioria dos casos. No entanto, evite usar fontes de luz light ou semi tamanhos de tipo em 42pt como traços verticais finos serão Vibrar e ele prejudicará a legibilidade. Fontes modernos com suficiente espessura do traço funcionam muito bem. Por exemplo, Helvetica e Arial parecer bonitas e são muito legível em HoloLens com pesos regulares ou em negrito.

![Tamanho do tipo recomendado](images/hug-text-08-1000px.png)<br>
*Exemplo de rampa de tipo*

## <a name="see-also"></a>Consulte também
* [Texto pré-fabricado no MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [Cena e layout de texto de exemplo pré-fabricado](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [Tipografia](typography.md)

 

---
title: Cor, luz e materiais
description: A criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cor, iluminação e materiais para cada um dos ativos visuais usados em sua experiência.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, cor, luz, materiais
ms.openlocfilehash: b29fe8da92e67d15592f9d4503bc278d4fe9fd95
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835082"
---
# <a name="color-light-and-materials"></a>Cor, luz e materiais

A criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cor, iluminação e materiais para cada um dos ativos visuais usados em sua experiência. Essas decisões podem ser para ambos os fins de estética, como o uso de luz e material para definir o tom de um ambiente de imersão e finalidades funcionais, como o uso de cores surpreendentes para alertar os usuários de uma ação iminente. Cada uma dessas decisões deve ser avaliada em relação às oportunidades e restrições do dispositivo de destino de sua experiência.

Veja abaixo as diretrizes específicas para renderizar ativos em headsets de imersão e Holographic. Muitos deles estão fortemente ligados a outras áreas técnicas e uma lista de assuntos relacionados pode ser encontrada na seção [Consulte também](color,-light-and-materials.md#see-also) no final deste artigo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Renderização em dispositivos de imersão versus Holographic

O conteúdo renderizado em headsets de imersão aparecerá visualmente diferente quando comparado ao conteúdo renderizado em headsets Holographic. Embora os headsets de imersão geralmente processem o conteúdo como você esperaria em uma tela 2D, os headsets Holographic como o HoloLens usam a seqüência de cores, consulte o RGB é exibido para renderizar hologramas.

Sempre Reserve um tempo para testar suas experiências de Holographic em um headset Holographic. A aparência do conteúdo, mesmo que seja criado especificamente para dispositivos Holographic, será diferente, como visto nos monitores secundários, instantâneos e na exibição do Spectator. Lembre-se de acompanhar experiências com um dispositivo, testar a iluminação de hologramas e observar de todos os lados (bem como de acima e abaixo) como o conteúdo é renderizado. Certifique-se de testar em um intervalo de configurações de brilho no dispositivo, pois é improvável que todos os usuários compartilhem um padrão presumido, bem como um conjunto diversificado de condições de iluminação.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Conceitos básicos de renderização em dispositivos Holographic
* **Dispositivos Holographic têm exibições aditivas** – os hologramas são criados com a adição de luz à luz do mundo real – o branco aparecerá com brilho, enquanto preto aparecerá transparente.
* **O impacto das cores varia de acordo com o ambiente do usuário** – há muitas condições de iluminação diferentes na sala do usuário. Crie conteúdo com níveis apropriados de contraste para ajudar com a clareza.
* **Evite a iluminação dinâmica** – os hologramas que são acesos uniformemente em experiências de Holographic são os mais eficientes. Usando a luminosidade avançada, a iluminação dinâmica provavelmente excederá os recursos de dispositivos móveis. Quando a iluminação dinâmica é necessária, é recomendável usar o [sombreador standard do kit de ferramentas da realidade misturada](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md). 

## <a name="designing-with-color"></a>Criando com cor

Devido à natureza de exibições aditivas, determinadas cores podem aparecer diferentes em exibições de Holographic. Algumas cores serão exibidas em ambientes de iluminação, enquanto outras aparecerão menos impactantes. As cores legais tendem a receder em segundo plano enquanto cores quentes saltam para o primeiro plano. Considere esses fatores à medida que explorar a cor em suas experiências:
* Os benefícios da **gama** -HoloLens de uma "ampla gama" de cores, conceitualmente semelhante ao Adobe RGB. Como resultado, algumas cores podem apresentar qualidades e representação diferentes no dispositivo.
* **Gama** -o brilho e o contraste da imagem renderizada irão variar entre os dispositivos de imersão e Holographic. Essas diferenças de dispositivo geralmente parecem tornar áreas escuras de cores e sombras, mais ou menos brilhantes.
* **Separação de cores** – também chamada de "cor divisão" ou "borda colorida", a separação de cores geralmente ocorre com o movimento de holograma (incluindo o cursor) quando um usuário rastreia objetos com seus olhos.
* **Uniformidade de cores** -normalmente, os hologramas são renderizados com brilho suficiente para que mantenham a uniformidade de cores, independentemente do plano de fundo. Áreas grandes podem se tornar blotchy. Evite grandes regiões de cores brilhantes e sólidas.
* **Renderizando cores claras** -o branco parece muito brilhante e deve ser usado com moderação. Na maioria dos casos, considere um valor branco em volta de R 235 G 235 B 235. Grandes áreas brilhantes podem causar discomfort do usuário.

**Renderizando cores escuras**

Devido à natureza de exibições aditivas, as cores escuras aparecem transparentes. Um objeto preto sólido não aparecerá de forma diferente do mundo real. Consulte canal alfa abaixo. Para dar a aparência de "preto", experimente um valor RGB cinza muito escuro, como 16, 16, 16.

![gama de cores normal versus ampla](images/640px-widegamut.png)<br>
*Gama de cores normal versus ampla*

## <a name="technical-considerations"></a>Considerações técnicas
* **Alias** -seja considerem de alias, denteado ou "etapas da escada", em que a borda da geometria de um holograma atende ao mundo real. O uso de texturas com alto detalhe pode aggravate esse efeito. As texturas devem ser mapeadas e habilitadas para filtragem. Considere desbotar as bordas de hologramas ou adicionar uma textura que cria uma borda de borda preta em torno de objetos. Evite a geometria fina sempre que possível.
* **Canal alfa** -você deve limpar o canal alfa para totalmente transparente para todas as partes em que você não está renderizando um holograma. Deixar o alfa não definido leva a artefatos visuais ao tirar imagens/vídeos do dispositivo ou com a exibição Spectator.
* **Suavização de textura** -como a luz é aditiva em exibições de Holographic, é melhor evitar grandes regiões de cores sólidas e brilhantes, pois elas geralmente não produzem o efeito visual pretendido.

## <a name="storytelling-with-light-and-color"></a>Narração com luz e cor

A luz e a cor podem ajudar a tornar seus hologramas mais naturalmente no ambiente de um usuário, bem como orientações de oferta e ajuda para o usuário. Para experiências de Holographic, considere esses fatores ao explorar a iluminação e a cor:

:::row:::
    :::column:::
* **Vignetting** -um efeito ' Vignette ' para escurecer materiais pode ajudar a concentrar a atenção do usuário no centro do campo de exibição. Esse efeito escurece o material do holograma em algum raio do vetor olhar do usuário. Observe que isso também é eficaz quando o usuário exibe os hologramas de um ângulo oblíquo ou glancing.<br>
* **Ênfase** -desenhando a atenção para objetos ou pontos de interação por contraste com cores, brilho e iluminação. Para obter uma visão mais detalhada dos métodos de iluminação no narração, consulte [pixel Cinematography-uma abordagem de iluminação para gráficos de computador](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Imagem: uso de cor para mostrar ênfase para elementos narração, mostrados aqui em uma cena de [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*
    :::column-end:::
        :::column:::
        ![Uso de cor para mostrar ênfase para elementos narração, mostrados aqui em uma cena de fragmentos.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>Consulte também
* [Separação de cores](hologram-stability.md#color-separation)
* [Hologramas](hologram.md)
* [Linguagem de design da Microsoft-cor](https://www.microsoft.com/design/color)
* [Plataforma Universal do Windows-cor](https://docs.microsoft.com/windows/uwp/style/color)

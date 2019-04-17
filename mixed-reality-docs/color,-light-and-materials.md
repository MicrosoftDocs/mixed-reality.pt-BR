---
title: Cor, luz e materiais
description: Criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cor, iluminação e materiais para cada um dos ativos visuais usados em sua experiência.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, cor, luz, materiais
ms.openlocfilehash: 3f8ee8edfe4cbbaf8a55b3c4a9125f752823be9c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589848"
---
# <a name="color-light-and-materials"></a>Cor, luz e materiais

Criação de conteúdo para realidade misturada requer uma consideração cuidadosa de cor, iluminação e materiais para cada um dos ativos visuais usados em sua experiência. Essas decisões podem ser para fins estéticos, como o uso de luz e material para definir o tom de um ambiente imersivo e finalidades funcionais, como o uso de cores surpreendentes para alertar os usuários de uma ação iminente. Cada uma dessas decisões deve ser contra as oportunidades e restrições de dispositivo de destino da sua experiência.

Abaixo estão as diretrizes específicas para ativos de renderização em headsets envolventes e holographic. Muitos deles estão estreitamente relacionados a outras áreas técnicas e uma lista de tópicos relacionados pode ser encontrada na [Consulte também](color,-light-and-materials.md#see-also) seção no final deste artigo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Renderização em imersivo versus dispositivos holográfico

Conteúdo renderizado no fones imersivos em exposição aparecerá visualmente diferente quando comparado ao conteúdo renderizado no holográfica fones de ouvido. Enquanto fones imersivos em exposição geralmente renderizar conteúdo quanto você esperaria em uma tela 2D, headsets holográfica como HoloLens use transparente, sequencial de cor RGB exibe para hologramas processa.

Sempre têm tempo para testar suas experiências holográfica um Headset holográfica. A aparência do conteúdo, mesmo se ele foi desenvolvido especificamente para dispositivos holográfico, serão diferentes conforme visto no secundários monitores, instantâneos e no modo de exibição spectator. Lembre-se para fazer a ronda experiências com um dispositivo, teste a iluminação de hologramas e observando de todos os lados (bem como acima e abaixo) como seu conteúdo é renderizado. Certifique-se de testar em uma variedade de configurações de brilho no dispositivo, porque é improvável que todos os usuários compartilharão um padrão assumido, bem como um conjunto diversificado de condições de iluminação.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Conceitos básicos de renderização em dispositivos holographic
* **Dispositivos holográfico têm exibe aditivas** – hologramas são criadas com a adição de luz à luz do mundo real – branco aparecerá muito clara, enquanto preta aparecerá transparente.
* **Impacto de cores varia de acordo com o ambiente do usuário** – há muitas condições de iluminação diversificado na sala de um usuário. Crie conteúdo com níveis apropriados de contraste para proporcionar maior clareza.
* **Evite iluminação dinâmica** – hologramas estão acesos uniformemente nas experiências holográfica são mais eficientes. Usando a iluminação avançada e dinâmica provavelmente excederá os recursos de sombreadores móveis.

## <a name="designing-with-color"></a>Criando com cor

Devido à natureza exibe aditiva, determinadas cores podem parecer diferentes em telas holographic. Algumas cores serão exibida em ambientes de iluminação, enquanto outros serão exibidos como o menor impacto. As cores frias tendem a recuam na tela de fundo, enquanto as cores quentes saltar para o primeiro plano. Considere estes fatores conforme você explora a cor em suas experiências:
* **A gama** -HoloLens se beneficia de uma "gama ampla" de cor, conceitualmente semelhante a Adobe RGB. Como resultado, algumas cores podem apresentar diferentes qualidades e representação no dispositivo.
* **Gama** -o brilho e contraste da imagem renderizada irão variar entre dispositivos envolventes e holographic. Geralmente, essas diferenças em dispositivos aparecem tornar áreas escuras de cores e sombras, mais ou menos brilhante.
* **Separação de cores** -também chamado de "divisão de cor" ou "margem das cores", separação de cores ocorre com mais frequência movendo hologramas (incluindo o cursor) quando um usuário controla objetos com seus olhos.
* **Cor uniformidade** -normalmente hologramas são renderizadas com brilho bastante para que eles mantenham a uniformidade de cores, independentemente da tela de fundo. Grandes áreas podem se tornar toques. Evite grandes regiões da brilhante, cor sólida.
* **Renderização de cores claras** -branco aparece muito claro e deve ser usado com moderação. Na maioria dos casos, considere um valor em branco em torno de R 235 G 235 B 235. Grandes áreas brilhantes podem causar discomfort do usuário.

**Renderização de cores escuras**

Devido à natureza exibe aditivas, as cores escuras aparecem transparentes. Um objeto preto sólido aparecerá não é diferente do mundo real. Canal alfa de consulte abaixo. Para dar a aparência de "preto" Tente um valor RGB cinza escuro muito como 16,16,16.

![Normal versus gama de cores](images/640px-widegamut.png)<br>
*Normal versus gama de cores*

## <a name="technical-considerations"></a>Considerações técnicas
* **Alias** -considerar o alias, irregulares ou "degraus" em que a borda da geometria de um holograma atinge o mundo real. Usando texturas com maior nível de detalhes pode agravados esse efeito. Texturas devem ser mapeadas e a filtragem habilitada. Considere as bordas do hologramas-dégradé ou adicionando uma textura que cria uma borda preta de borda em torno de objetos. Sempre que possível, evite geometria fina.
* **Canal alfa** -você deve limpar o canal alfa para totalmente transparente para todas as partes em que você não estiver renderizando um holograma. Deixando os leads indefinidos alfabéticos para artefatos visuais ao fazer vídeos/imagens do dispositivo ou com o modo de exibição Spectator.
* **Suavização de textura** – uma vez que a luz é aditivos exibe holográfica, é melhor evitar grandes regiões da brilhante, cor sólida, conforme eles geralmente não produzir o efeito visual desejado.

## <a name="storytelling-with-light-and-color"></a>Storytelling com luz e a cor

Luz e a cor podem ajudar a tornar seu hologramas aparecer mais naturalmente em de um usuário ambiente, bem como oferecem diretrizes e ajuda para o usuário. Para obter experiências holográfica, considere estes fatores conforme você explora a cor e iluminação:
* **Vinheta** -um efeito 'vignette' para escurecer materiais pode ajudar a se concentrar a atenção do usuário no centro do campo de visualização. Esse efeito escurece material do holograma em alguns radius do vetor de olhar do usuário. Observe que isso também é eficaz quando o usuário vê hologramas a partir de um ângulo Oblíquo ou glancing.
* **Ênfase** -chamar a atenção para objetos ou pontos de interação de contraste de cores, brilho, e de iluminação. Para uma visão mais detalhada de métodos de iluminação na narração, consulte [cinematografia Pixel - uma abordagem de iluminação para gráficos de computador](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).

![Uso de cores para mostrar a ênfase para elementos de narração, mostrada aqui em uma cena de fragmentos.](images/640px-fragments.jpg)<br>
*Uso de cores para mostrar a ênfase para elementos de narração, mostrada aqui em uma cena [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*

## <a name="see-also"></a>Consulte também
* [Separação de cores](hologram-stability.md#color-separation)
* [Hologramas](hologram.md)
* [Linguagem de Design da Microsoft - cor](https://www.microsoft.com/design/color)
* [Plataforma universal do Windows - cor](https://docs.microsoft.com/windows/uwp/style/color)

---
title: O que é a realidade misturado?
description: Este artigo define realidade mista e demonstra em que os dispositivos de AR e VR simples, bem como dispositivos de realidade mista do Windows, como Microsoft HoloLens e o Windows Mixed Reality fones imersivos em exposição, ficam juntamente com o espectro de realidade misturada.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realidade misturada, holográfica, ar, vr, mr, xr, realidade aumentada, de realidade virtual, explicação
ms.openlocfilehash: 3f6000b3d700d7c13f1efa13a81561464f8fdad1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590962"
---
# <a name="what-is-mixed-reality"></a>O que é a realidade misturado?

Realidade mista é o resultado da combinação do mundo físico com o mundo digital. Realidade misturada é a próxima evolução na interação humana, o computador e o ambiente e desbloqueia as possibilidades que antes eram restritas a nossa imaginação. Ele é possibilitado por avanços na pesquisa Visual computacional, poder de processamento de gráficos, tecnologia de exibição e sistemas de entrada. O termo *realidade misturada* foi originariamente introduzido em um documento de 1994, Paul Milgram e Fumio Kishino, "[uma taxonomia de Mixed exibe Visual da realidade](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)." Seu papel introduziu o conceito do *continuum virtuality* e focado em como a categorização de taxonomia aplicada a exibe. Desde então, o aplicativo de realidade misturada vai além dele exibe, mas também inclui a entrada ambiental, som espacial e local.

## <a name="environmental-input-and-perception"></a>Percepção e entrada ambiental

![Diagrama de Venn mostrando as interações entre computadores, seres humanos e ambientes](images/mixed-reality-venn-diagram-300px.png)<br> 

Ao longo dos últimas décadas, a relação entre a entrada de computador e informações humanas tem sido bem explorada. Ele tem até mesmo uma disciplina estudada amplamente conhecida como *interação humana computador* ou HCI. Informações humanas ocorre por meio de uma variedade de meios incluindo teclados, mouses, toque, tinta, voz e até mesmo acompanhamento de esqueleto Kinect.

Avanços em sensores e processamento permitirá que o aumento para uma nova área de entrada do computador de ambientes. A interação entre os computadores e ambientes é efetivamente ambiental compreensão, ou *percepção*. Portanto, os nomes de API no Windows que revelam informações sobre o ambiente são chamados a [percepção APIs](https://docs.microsoft.com/uwp/api/Windows.Perception). Entrada ambiental captura coisas como a posição de uma pessoa no mundo (, por exemplo, [acompanhamento principal](coordinate-systems.md)), superfícies e os limites (por exemplo, [mapeamento espacial](spatial-mapping.md) e [espacial Noções básicas sobre](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), luz ambiente, som ambiental, reconhecimento de objeto e local.

Agora, a combinação de todos os três – de processamento do computador, informações humanas e entrada ambiental – define a oportunidade de criar experiências de realidade misturada true. Movimento no mundo físico pode traduzir a movimentação do mundo digital. Os limites no mundo físico podem influenciar as experiências de aplicativos, como o jogo no mundo digital. Sem entrada ambiental, experiências não é possível misturar entre as realidades digitais e físicas.

## <a name="the-mixed-reality-spectrum"></a>O espectro de realidade misturada

Como realidade misturada é a combinação do mundo físico e do mundo digital, essas duas realidades definem as extremidades polares de um espectro conhecido como o continuum virtuality. Para manter a simplicidade, nos referimos a isso como o *espectro de realidade misturada*. No lado esquerdo, temos realidade física em que nós, humanos, existem. Em seguida, no lado direito, temos a realidade digital correspondente.

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

A maioria dos celulares no mercado atualmente não têm pouco ou nenhum recursos ambientais Noções básicas sobre. Assim, as experiências que eles oferecem não é possível misturar entre realidades digitais e físicas. São as experiências pelas quais elementos gráficos em fluxos de vídeo do mundo físico de sobreposição *aumentada realidade*, e as experiências pelas quais occlude sua exibição para apresentar uma experiência digital são *realidade virtual*. Como você pode ver, as experiências habilitadas entre esses dois extremos está *realidade misturada*:
* Começando com o mundo físico, colocar um objeto digital, como um holograma, como se fosse realmente existe.
* Começando com o mundo físico, uma representação digital de outra pessoa – um avatar – mostra o local em que estavam aguardando ao sair de notas. Em outras palavras, experiências que representam a colaboração assíncrona em diferentes pontos no tempo.
* Os limites físicos do mundo físico, como paredes e móveis, começando com um mundo digital, aparecem digitalmente dentro a experiência para ajudar os usuários a evitar objetos físicos.

![O espectro de realidade misturada](images/mixed-reality-spectrum-550px.png)

Mais realidade aumentada e ofertas de realidade virtual disponíveis hoje representam uma parte muito pequena deste espectro. Eles são, no entanto, subconjuntos de maior espectro de realidade misturada. Windows 10 é compilado com todo o espectro, lembre-se e permite a combinação digitais representações de pessoas, lugares e coisas com o mundo real.

![Tipos de dispositivo no espectro de realidade misturada](images/mixed-reality-spectrum-device-types-550px.png)

Há dois tipos principais de dispositivos que oferecem experiências de realidade mista do Windows:
1. **Dispositivos holographic.** Essas são caracterizadas por capacidade do dispositivo para colocar conteúdo digital no mundo real, como se fosse realmente existe.
2. **Dispositivos envolventes.** Essas são caracterizadas por capacidade do dispositivo para criar uma noção de "presença" – ocultando mundo físico e substituí-la com uma experiência digital.

<table>
<tr>
<th width="20%"> Característica</th><th width="40%"> Dispositivos holographic</th><th width="40%"> Dispositivos de imersão</th>
</tr><tr>
<td> Dispositivo de exemplo</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Windows Acer misturadas realidade Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> Vídeo</td><td> <i>Exibição transparente.</i> Permite que o usuário veja o ambiente físico durante o uso de fone de ouvido.</td><td> <i>Opaque display.</i> Bloqueia o ambiente físico durante o uso de fone de ouvido.</td>
</tr><tr>
<td> Movimentação</td><td> Total de seis graus de liberdade movimentação, rotação e translação.</td><td> Total de seis graus de liberdade movimentação, rotação e translação.</td>
</tr>
</table>

Observe que, se um dispositivo está conectado ao ou vinculado a um PC separado (via cabo USB ou WiFi) ou autocontido faz (ilimitado) não reflete se um dispositivo é holographic ou imersivos. Certamente, recursos que melhoram a líder de mobilidade para dispositivos de holographic e envolventes e experiências melhores pode ser vinculados ou ilimitados.

## <a name="devices-and-experiences"></a>Dispositivos e experiências

Avanço tecnológico é o que tiver habilitado as experiências de realidade misturada. Não existem dispositivos hoje que podem ser executados experiências por todo o espectro; No entanto, o Windows 10 fornece uma plataforma comum de realidade mista para fabricantes de dispositivos e desenvolvedores. Dispositivos hoje podem dar suporte a um intervalo específico dentro do espectro de realidade mista e ao longo do tempo novos dispositivos devem expandir nesse intervalo. No futuro, dispositivos holográfico se tornará mais envolventes e imersivos dispositivos se tornará mais holographic.

![Em que os dispositivos dispor no espectro de realidade misturada](images/mixed-reality-spectrum-device-placement-550px.png)

Muitas vezes, é melhor considerar que tipo de experiência de um aplicativo ou jogo desenvolvedor quer criar. As experiências geralmente serão direcionada a um ponto específico ou a parte no espectro. Em seguida, os desenvolvedores devem considerar os recursos dos dispositivos que eles desejam de destino. Por exemplo, experiências que se baseiam no mundo físico executará melhor em HoloLens.
* **Para a esquerda (próximo da realidade física).** Os usuários permanecem presentes em seus ambientes físicos e nunca são feitos para acreditar que eles têm restantes nesse ambiente.
* **No meio (realidade misturada totalmente).** Essas experiências do mundo real e o mundo digital blend perfeitamente. Os visualizadores que acompanham o filme [Jumanji](https://en.wikipedia.org/wiki/Jumanji) pode reconciliar como a estrutura física da casa onde ocorreu a história foi combinada com um ambiente de floresta.
* **Para a direita (próximo da realidade digital).** Os usuários a experiência de um ambiente completamente digital e são alheios a que ocorre no ambiente físico em torno deles.


## <a name="see-also"></a>Consulte também
* [Referência da API: Windows.Perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [Referência da API: Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [Referência da API: Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)

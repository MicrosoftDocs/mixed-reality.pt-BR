---
title: O que é realidade misturada?
description: Este artigo define a realidade misturada e demonstra onde os dispositivos AR e VR simples, bem como dispositivos Windows Mixed Reality, como o Microsoft HoloLens e o Windows Mixed Realm, os headsets, ficam ao longo do espectro de realidade misturada.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realidade misturada, Holographic, ar, VR, Sr, XR, realidade aumentada, realidade virtual, explicação
ms.openlocfilehash: e3205590ce46e0fc9113421e0dbaeb87fe6bc0c2
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376033"
---
# <a name="what-is-mixed-reality"></a>O que é realidade misturada?

![Apontar e confirmar com mãos no HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

A realidade misturada é o resultado da mistura do mundo físico com o mundo digital. A realidade misturada é a próxima evolução em interação humana, computacional e de ambiente e proporciona possibilidades que antes eram restritas à nossa imaginação. Isso é possível por avanços na pesquisa Visual computacional, na capacidade de processamento gráfico, na tecnologia de vídeo e nos sistemas de entrada. O termo *misto de realidade* foi introduzido originalmente em um papel de 1994 por Paul Milgram e Fumio Kishino, "[uma taxonomia de exibições visuais de realidade misturada](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)". Seu documento introduziu o conceito do *continuidade de virtualização*e se concentrou em como a categorização de taxonomia é aplicada a exibições. Desde então, a aplicação da realidade misturada vai além dos monitores. Ele também inclui entrada ambiental, som espacial e local.

![o espectro de realidade misturada](images/mixedrealityspectrum-worlds.png)<br>
*Imagem: a realidade mista é o resultado da mesclagem do mundo físico com o mundo digital.*

<br>

---

## <a name="environmental-input-and-perception"></a>Entrada e percepção ambiental

Nas últimas décadas, a relação entre a entrada humana e a do computador foi bem explorada. Ele até mesmo tem uma disciplina amplamente estudada conhecida como *interação humana do computador* ou HCI. A entrada humana ocorre por meio de uma variedade de meios, incluindo teclados, mouses, toque, tinta, voz e até mesmo controle estrutural Kinect.

Os avanços nos sensores e no processamento estão proporcionando aumento para uma nova área de entrada do computador de ambientes. A interação entre computadores e ambientes é efetivamente a compreensão ou *percepção*ambiental. Portanto, os nomes de API no Windows que revelam informações ambientais são chamados de [APIs de percepção](https://docs.microsoft.com/uwp/api/Windows.Perception). A entrada ambiental captura coisas como a posição de uma pessoa no mundo (por exemplo, [acompanhamento de cabeçalho](coordinate-systems.md)), superfícies e limites (por exemplo, [mapeamento espacial](spatial-mapping.md) e [compreensão da cena](scene-understanding.md)), iluminação ambiente, som ambiental, reconhecimento de objeto e local.

<br>

![diagrama de Venn mostrando interações entre computadores, seres humanos e ambientes](images/mixed-reality-venn-diagram-300px.png)<br>*imagem de  
: as interações entre os computadores, os seres humanos e os ambientes.*

<br>

Agora, a combinação de todo o processamento de três**computadores, entrada humana e entrada ambiental**– define a oportunidade de criar experiências de realidade misturadas verdadeiras. A movimentação pelo mundo físico pode ser traduzida para o movimento no mundo digital. Os limites no mundo físico podem influenciar experiências de aplicativos, como jogos de jogo, no mundo digital. Sem a entrada ambiental, as experiências não podem misturar entre as realidades físicas e digitais.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>O espectro de realidade misturada

Como a realidade mista mistura mundos físicos e digitais, essas duas realidades definem as extremidades polares de um espectro conhecido como o continuum de virtualização. Para simplificar, nós nos referimos a isso como o *espectro de realidade misturada*. No lado esquerdo, temos realidade física em que nós, seres humanos, existem; no lado direito, temos a realidade digital correspondente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realidade aumentada versus virtualização

A maioria dos telefones celulares no mercado atualmente tem pouco ou nenhum recurso de compreensão ambiental. Portanto, as experiências que eles oferecem não podem misturar entre realidades físicas e digitais. As experiências que sobrepõem gráficos em fluxos de vídeo do mundo físico são uma *realidade aumentada*. As experiências que occludem sua exibição para apresentar uma experiência digital são a *realidade virtual*. Como você pode ver, as experiências habilitadas entre esses dois extremos são *realidade misturada*:
* Começando com o mundo físico, colocando um objeto digital, como um holograma, como se ele estivesse realmente lá.
* A partir do mundo físico, uma representação digital de outra pessoa – um avatar – mostra o local onde eles estavam quando saem das anotações. Em outras palavras, as experiências que representam a colaboração assíncrona em diferentes pontos no tempo.
* Começando com um mundo digital, os limites físicos do mundo físico, como paredes e mobília, aparecem digitalmente dentro da experiência para ajudar os usuários a evitar objetos físicos.


<br>

![o espectro de realidade misturada](images/mixedrealityspectrum.png)<br>
*Imagem: o espectro de realidade misturada*

<br>

A realidade mais aumentada e as ofertas de realidade virtual disponíveis hoje representam uma parte muito pequena desse espectro. No entanto, eles são subconjuntos do espectro maior de realidade misturada. O Windows 10 foi criado com o espectro inteiro em mente e permite a mesclagem de representações digitais de pessoas, lugares e coisas com o mundo real.




## <a name="devices-and-experiences"></a>Dispositivos e experiências


Há dois tipos principais de dispositivos que fornecem experiências do Windows Mixed Reality:
1. **Dispositivos Holographic.** Elas são caracterizadas pela capacidade do dispositivo de posicionar o conteúdo digital no mundo real como se estivesse realmente lá.
2. **Dispositivos de imersão.** Elas são caracterizadas pela capacidade do dispositivo de criar uma noção de "presença" – ocultando o mundo físico e substituindo-o por uma experiência digital.

<table>
<tr>
<th width="30%"> Característica</th><th width="35%"> Dispositivos Holographic</th><th width="35%"> Dispositivos de imersão</th>
</tr><tr>
<td><strong>Dispositivo de exemplo</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey +<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Display</strong></td><td> Exibição de visualização. Permite que o usuário veja o ambiente físico ao gastar o headset.</td><td> Exibição opaca. Bloqueia o ambiente físico ao gastar o headset.</td>
</tr><tr>
<td><strong>Migração</strong></td><td> Movimentação completa de seis graus de liberdade, rotação e conversão.</td><td> Movimentação completa de seis graus de liberdade, rotação e conversão.</td>
</tr>
</table>



Observe se um dispositivo está conectado ou de compartilhamento de Internet a um PC separado (via cabo USB ou Wi-Fi) ou autônomo (sem compartilhamento de Internet) não reflete se um dispositivo é Holographic ou envolvente. Certamente, os recursos que melhoram a mobilidade levam a experiências melhores, e os dispositivos Holographic e imersiva podem ser vinculados ou não são de compartilhamento de Internet.


O avanço tecnológico é o que habilitou experiências mistas de realidade. Atualmente, não há dispositivos que possam executar experiências em todo o espectro. No entanto, o Windows 10 fornece uma plataforma comum de realidade misturada para fabricantes e desenvolvedores de dispositivos. Os dispositivos atualmente podem dar suporte a um intervalo específico dentro do espectro de realidade misturada. Ao longo do tempo, novos dispositivos expandirão esse intervalo. No futuro, os dispositivos Holographic se tornarão mais imersivas e os dispositivos de imersão se tornarão mais Holographic.

<br>

![tipos de dispositivo no espectro de realidade misturada](images/Final_WhatIsMixedReality07.png)<br>
*Imagem: onde os dispositivos existem no espectro de realidade misturada*

Geralmente, é melhor considerar o tipo de experiência que um desenvolvedor de aplicativo ou jogo deseja criar. Normalmente, as experiências visam um ponto específico ou parte do espectro. Em seguida, os desenvolvedores devem considerar os recursos dos dispositivos que desejam direcionar. Por exemplo, experiências que dependem do mundo físico serão executadas melhor no HoloLens.
* **Em direção à esquerda (perto da realidade física).** Os usuários permanecem presentes em seu ambiente físico e nunca são feitos para acreditar que eles saíram desse ambiente.
* **No meio (realidade totalmente misturada).** Essas experiências combinam o mundo real e o mundo digital. Os visualizadores que viram o filme [Jumanji](https://en.wikipedia.org/wiki/Jumanji) podem reconciliar como a estrutura física da casa onde a história ocorreu foi combinada com um ambiente selva.
* **Em direção à direita (quase a realidade digital).** Os usuários experimentam um ambiente completamente digital e não sabem o que ocorre no ambiente físico em relação a eles.


## <a name="see-also"></a>Consulte também

* [O que é um holograma?](hologram.md)
* [Entenda os conceitos básicos da realidade misturada](index.md#understand-the-basics)
* [Comece a criar a criação de protótipos](design.md)
* [Conheça as ferramentas e a arquitetura](development.md)


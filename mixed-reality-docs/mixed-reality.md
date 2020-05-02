---
title: O que é realidade misturada?
description: Este artigo define realidade misturada e demonstra o local em que os dispositivos de RA e VR simples, bem como dispositivos Windows Mixed Reality, como headsets imersivos do Windows Mixed Reality e Microsoft HoloLens, ficam ao longo do espectro de realidade misturada.
author: brandonbray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realidade misturada, holográfico, ra, vr, mr, xr, realidade aumentada, realidade virtual, explicação
ms.localizationpriority: high
ms.openlocfilehash: 7b0dcbdb88f880d4c1632fae874ba6a610f023fb
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81278044"
---
# <a name="what-is-mixed-reality"></a>O que é realidade misturada?

![Apontar e confirmar com as mãos no HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

A realidade misturada é o resultado da mistura do mundo físico com o mundo digital. A realidade misturada é a próxima evolução em interação humana, computacional e de ambiente e proporciona possibilidades que antes eram restritas à nossa imaginação. Isso é possível devido a aprimoramentos na pesquisa visual computacional, na capacidade de processamento gráfico, na tecnologia de vídeo e em sistemas de entrada. O termo *realidade misturada* foi introduzido originalmente em um artigo de 1994 de Paul Milgram e Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)." Esse artigo introduziu o conceito de *continuum de virtualização* e concentrou-se em como a categorização de taxonomia se aplicava a monitores. Desde então, o aplicativo de realidade misturada vai além dos monitores. Ele também inclui entrada de ambiente, som espacial e local.

![O espectro da realidade misturada](images/mixedrealityspectrum-worlds.png)<br>
*Imagem: a realidade misturada é o resultado da mistura do mundo físico com o mundo digital.*

<br>

---

## <a name="environmental-input-and-perception"></a>Entrada e percepção do ambiente

Nas últimas décadas, a relação entre a entrada humana e a do computador foi bem explorada. Ela teve até mesmo uma disciplina amplamente estudada conhecida como *interação entre humanos e computadores* ou HCI. A entrada humana acontece por meio de uma variedade de meios, incluindo teclados, mouses, toque, tinta, voz e até mesmo controle estrutural Kinect.

Os avanços nos sensores e no processamento estão proporcionando aumento em uma nova área de entrada computacional de ambientes. A interação entre computadores e ambientes é efetivamente a noção ou a *percepção* do ambiente. Portanto, os nomes de API no Windows que revelam informações do ambiente são chamados de [APIs de percepção](https://docs.microsoft.com/uwp/api/Windows.Perception). A entrada do ambiente captura coisas como a posição de uma pessoa no mundo (por ex., [acompanhamento de cabeça](coordinate-systems.md)), superfícies e limites (por ex., [mapeamento espacial](spatial-mapping.md) e [noção de cena](scene-understanding.md)), iluminação do ambiente, som do ambiente, reconhecimento de objetos e local.

<br>

![Diagrama de Venn mostrando interações entre computadores, seres humanos e ambientes](images/mixed-reality-venn-diagram-300px.png)<br> 
*Imagem: as interações entre computadores, seres humanos e ambientes.*

<br>

Agora, a combinação de todos os três – **processamento do computador, entrada humana e entrada do ambiente** – define a oportunidade de criar experiências de realidade misturada verdadeiras. A movimentação no mundo físico pode ser convertida em movimento no mundo digital. Os limites no mundo físico podem influenciar as experiências de aplicativos, como jogos, no mundo digital. Sem a entrada do ambiente, as experiências não podem ser combinadas entre realidades físicas e digitais.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>O espectro da realidade misturada

Como a realidade misturada combina mundos físicos e digitais, elas definem as extremidades polares de um espectro conhecido como o continuum de virtualização. Para simplificar, nós nos referimos a isso como o *espectro de realidade misturada*. Do lado esquerdo, temos a realidade física, em que nós, humanos, existimos; do lado direito, temos a realidade digital correspondente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realidade aumentada versus virtual

A maioria dos celulares no mercado atualmente tem pouca ou nenhuma funcionalidade de noção do ambiente. Portanto, as experiências que eles oferecem não podem ser misturadas entre realidades físicas e digitais. As experiências que sobrepõem elementos gráficos em fluxos de vídeo do mundo físico são *realidade aumentada*. As experiências que ocultam sua exibição para apresentar uma experiência digital são *realidade virtual*. Como você pode ver, as experiências habilitadas entre esses dois extremos são *realidade misturada*:
* Com base no mundo físico, colocando um objeto digital, como um holograma, como se ele realmente estivesse lá.
* Com base no mundo físico, uma representação digital de outra pessoa – um avatar – mostra o local em que ela estava quando deixou anotações. Em outras palavras, as experiências que representam a colaboração assíncrona em diferentes pontos no tempo.
* Com base em um mundo digital, os limites físicos do mundo físico, como paredes e mobília, são exibidos digitalmente dentro da experiência para ajudar os usuários a evitar objetos físicos.


<br>

![O espectro da realidade misturada](images/mixedrealityspectrum.png)<br>
*Imagem: o espectro da realidade misturada*

<br>

Atualmente, a maioria das ofertas de realidade aumentada e realidade virtual representa uma parte muito pequena desse espectro. No entanto, elas são subconjuntos do espectro maior de realidade misturada. O Windows 10 é criado com todo o espectro em mente e permite a combinação de representações digitais de pessoas, locais e coisas com o mundo real.




## <a name="devices-and-experiences"></a>Dispositivos e experiências


Há dois tipos principais de dispositivos que fornecem experiências do Windows Mixed Reality:
1. **Dispositivos holográficos.** Eles são caracterizados pela capacidade do dispositivo de colocar conteúdo digital no mundo real como se realmente estivesse lá.
2. **Dispositivos imersivos.** Eles são caracterizados pela capacidade do dispositivo de criar uma sensação de “presença”, ocultando o mundo físico e substituindo-o por uma experiência digital.

<table>
<tr>
<th width="30%"> Característica</th><th width="35%"> Dispositivos holográficos</th><th width="35%"> Dispositivos imersivos</th>
</tr><tr>
<td><strong>Dispositivo de exemplo</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Monitor</strong></td><td> Monitor transparente. Permite que o usuário veja o ambiente físico ao usar o headset.</td><td> Monitor opaco. Bloqueia o ambiente físico ao usar o headset.</td>
</tr><tr>
<td><strong>Movimentação</strong></td><td> Movimentação completa de seis graus de liberdade, rotação e conversão.</td><td> Movimentação completa de seis graus de liberdade, rotação e conversão.</td>
</tr>
</table>



Observação: um dispositivo estar conectado ou vinculado a um computador separado (por cabo USB ou Wi-Fi) ou ser autônomo (não conectado) não refletirá se um dispositivo é holográfico ou imersivo. Certamente, os recursos que aprimoram a mobilidade produzem melhores experiências, e os dispositivos holográficos e imersivos podem estar conectados ou não.


O avanço tecnológico é o que habilitou experiências de realidade misturada. Não há dispositivos atualmente que podem executar experiências em todo o espectro. No entanto, o Windows 10 oferece uma plataforma comum de realidade misturada para fabricantes e desenvolvedores de dispositivos. Atualmente, os dispositivos podem dar suporte a um intervalo específico dentro do espectro de realidade misturada. Ao longo do tempo, novos dispositivos expandirão esse intervalo. No futuro, dispositivos holográficos ficarão mais imersivos, e os dispositivos imersivos ficarão mais holográficos.

<br>

![Tipos de dispositivo no espectro de realidade misturada](images/Final_WhatIsMixedReality07.png)<br>
*Imagem: local no qual os dispositivos existem no espectro de realidade misturada*

Geralmente, é melhor considerar qual tipo de experiência um desenvolvedor de aplicativo ou jogo deseja criar. As experiências normalmente direcionarão uma parte ou ponto específico no espectro. Em seguida, os desenvolvedores devem considerar as funcionalidades dos dispositivos que desejam direcionar. Por exemplo, experiências que dependerem do mundo físico serão mais bem executadas no HoloLens.
* **Em direção à esquerda (perto da realidade física).** Os usuários permanecem presentes no ambiente físico deles e nunca são induzidos a acreditar que saíram desse ambiente.
* **No meio (realidade totalmente misturada).** Essas experiências combinam o mundo real e o mundo digital. Os espectadores que viram o filme [Jumanji](https://en.wikipedia.org/wiki/Jumanji) podem reconciliar como a estrutura física da casa em que a história ocorreu foi combinada com um ambiente de selva.
* **Em direção à direita (perto da realidade digital).** Os usuários experimentam um ambiente completamente digital e não sabem o que ocorre no ambiente físico ao redor deles.


## <a name="see-also"></a>Veja também

* [O que é um holograma?](hologram.md)
* [Noções básicas da realidade misturada](index.md#understand-the-basics)
* [Comece a projetar e a criar protótipos](design.md)
* [Conheça as ferramentas e a arquitetura](development.md)


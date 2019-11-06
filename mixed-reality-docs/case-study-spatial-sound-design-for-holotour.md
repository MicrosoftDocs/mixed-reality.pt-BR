---
title: Estudo de caso-design de som espacial para HoloTour
description: Para criar um tour virtual 3D verdadeiramente envolvente para o Microsoft HoloLens, os vídeos panorâmicos e o cenário Holographic são apenas parte da fórmula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, HoloTour, som espacial, estudo de caso
ms.openlocfilehash: e1da80bd647084aa4d7839c0f1b1848b46c2b1b4
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641150"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>Estudo de caso-design de som espacial para HoloTour

Para criar um tour virtual 3D verdadeiramente envolvente para o Microsoft HoloLens, os vídeos panorâmicos e o cenário Holographic são apenas parte da fórmula. O designer de áudio Jason Syltebo fala sobre como o som foi capturado e processado para fazer você sentir como você realmente está em cada um dos locais em HoloTour.

## <a name="the-tech"></a>O Tech

As belas imagens e cenas de Holographic que você vê em HoloTour são apenas uma parte da criação de uma experiência de realidade mista de verossímeis. Embora os hologramas só possam aparecer visualmente na frente de um usuário, o recurso de [som espacial](spatial-sound.md) do HoloLens permite que o áudio venha de todas as direções, o que dá ao usuário uma experiência de sensor mais completa.

O som espacial nos permite dar indicações de áudio para indicar uma direção na qual o usuário deve ativar ou para permitir que o usuário saiba que há mais hologramas para que eles vejam dentro de seu espaço. Também podemos anexar um som diretamente a um holograma e atualizar continuamente a direção e a distância que o holograma é de um usuário para que pareça que o som é proveniente diretamente desse objeto.

Com o HoloTour, queríamos aproveitar os recursos de som espacial do HoloLens para criar um ambiente de 360 graus, sincronizado com o vídeo para revelar os destaques da Sonic de locais específicos.

## <a name="behind-the-scenes"></a>Nos bastidores

Criamos experiências HoloTour de dois locais diferentes: Roma e Machu Picchu. Para fazer esses Tours parecerem autênticos e atraentes, queríamos evitar o uso de sons genéricos e, em vez disso, capturar áudio diretamente dos locais onde estávamos filmings.

### <a name="capturing-the-audio"></a>Capturando o áudio

Em nosso [estudo de caso sobre como capturar o conteúdo visual para HoloTour](case-study-capturing-and-creating-content-for-holotour.md), falamos sobre o design personalizado do nosso Rig de câmera. Ele consistiu em 14 câmeras GoPros contidas em uma estrutura 3D, projetada para as dimensões específicas do tripod. Para capturar áudio desse Rig, adicionamos uma matriz de microfone quádruplo sob as câmeras, que entraram em uma unidade de gravação compactada de 4 canais que se SAT na base do tripod. Escolhemos microfones que não só eram bem executados, mas que tinham um espaço muito pequeno, para não occlude a exibição da câmera.

![a câmera personalizada e o Rig do microfone](images/camera-rig-microphones-300px.png)<br>
*Câmera personalizada e Rig do microfone*

Essa configuração capturou som em quatro direções do local preciso de nossa câmera, fornecendo informações suficientes para recriar um panorama de auricular 3D usando som espacial, que poderíamos, posteriormente, ser sincronizado com o vídeo de 360 graus.

Um dos desafios com o áudio da matriz de câmera é que você está no mercê do que está registrado no momento da captura. Mesmo que a captura de vídeo seja boa, a captura de som pode se tornar problemática devido a sons fora da câmera, como Sirens, aviões ou altos ventos. Para garantir que tínhamos todos os elementos de que precisamos, usamos uma série de unidades de gravação móvel estéreo e mono para obter elementos de ambiente assíncronos em pontos de interesse específicos em cada local. Essa captura é importante, pois dá ao designer de som a capacidade de buscar conteúdo limpo e utilizável, que pode ser usado em produção após o interesse e adicionar direção adicional.

Qualquer dia de captura determinado geraria um grande número de arquivos. Era importante desenvolver um sistema para controlar quais arquivos correspondem a um local ou uma captura de câmera específica. Nossa unidade de gravação foi configurada para nomear automaticamente os arquivos por data e pegar o número e devemos fazer o backup no final do dia para unidades externas. Na pior das hipóteses, a slat verbal do início das gravações de áudio foi importante, pois isso permite que a identificação contextual fácil do conteúdo se torne um problema. Também foi importante para que possamos visualmente a captura de Rig da câmera, pois o vídeo e o áudio foram registrados como mídia separada e precisavam ser sincronizados durante o post.

### <a name="editing-the-audio"></a>Editando o áudio

De volta ao estúdio após a viagem de captura, a primeira etapa na montagem de uma experiência de auricular direcional e de imersão é examinar toda a captura de áudio de um local, escolher a melhor forma e identificar os destaques que poderiam ser aplicados criativamente durante integrar. O áudio é então editado e limpo. Por exemplo, uma haste de carro alta, com duração de um segundo, e repetidas vezes, pode ser substituída e grampeada com seções de áudio silencioso e ambiente da mesma captura.

Quando a edição de vídeo de um local tiver sido estabelecida, o designer de som poderá sincronizar o áudio correspondente. Neste ponto, trabalhamos com a captura de Rig de câmera e a captura móvel para decidir quais elementos, ou combinação deles, funcionarão para criar uma cena de áudio de imersão. Uma técnica que encontramos útil foi adicionar todos os elementos de som em um editor de áudio e criar uma simulação rápida linear para experimentar com diferentes ideias de combinação. Isso nos ofereceu ideias melhores formadas quando chegou a hora de criar os bastidores de HoloTour reais.

### <a name="assembling-the-scene"></a>Montando a cena

A primeira etapa para a criação de uma cena de ambiente 3D é criar uma base de sons gerais de loop de ambiente em segundo plano que dará suporte a outros recursos e elementos de som interativos em uma cena. Ao fazer isso, pegamos uma abordagem holística em relação às diferentes técnicas de implementação determinadas pelas necessidades específicas e os critérios de design de qualquer cena específica. Algumas cenas podem ser indexadas em direção ao uso da captura de câmera sincronizada, enquanto outras podem exigir uma abordagem mais organizada que usa sons mais discretos, elementos interativos e música e efeitos sonoros para o mais Cinematic momentos no HoloTour.

Ao indexar o uso do áudio de captura de câmera, colocamos emissores de áudio de ambiente habilitados para sons espaciais correspondentes às coordenadas direcionais da orientação da câmera, de modo que a exibição da câmera do Norte reproduza áudio do microfone norte e da mesma forma para as outras direções de cardinal. Esses emissores são bloqueados mundialmente, o que significa que o usuário pode transformar seu cabeçalho livremente em relação a esses emissores e o som será alterado de forma adequada, modelando efetivamente o som de pé nesse local. Ouça o Piazza Navona ou o Pantheon para obter exemplos de cenas que usam uma boa mistura de áudio capturado de câmera.

Uma abordagem diferente envolvida na reprodução de um Ambience de estéreo de loop em conjunto com emissores de som espaciais colocados em volta da cena que executa sons únicos que são aleatórios em termos de frequência de volume, densidade e gatilho. Isso cria um Ambience com um aspecto aprimorado de direcionalidade. No Aguas Calientes, por exemplo, você pode ouvir como cada quadrante do panorama tem emissores específicos que realçam áreas específicas da geografia, mas trabalham em conjunto para criar um Ambience de imersão geral.

## <a name="tips-and-tricks"></a>Dicas e truques

Quando você está reunindo áudio para uma cena, há alguns métodos adicionais que podem ser usados para realçar ainda mais a direção e o imersão, fazendo uso completo dos recursos de som espacial do HoloLens. Fornecemos uma lista de alguns itens abaixo — escute-os na próxima vez que tentar HoloTour.
* **Procurar destinos**: esses são sons que são disparados somente quando você está olhando para um objeto ou área específica do quadro Holographic. Por exemplo, examinar a direção do café do lado da rua no Piazza Navona de Roma disparará sutilmente os sons de um restaurante ocupado.
* **Visão local**: a jornada, embora HoloTour, contém determinados batidas em que o guia do Tour, auxiliado por hologramas, explorará um tópico em detalhes. Por exemplo, como a fachada do Pantheon é resolvida para revelar o Oculus, o reverberating Audio colocado como um emissor 3D do interior do Pantheon incentiva o usuário a explorar o modelo interior.
* **Direcionalidade aprimorada**: em muitas cenas, colocamos sons de várias maneiras de adicionar à direcionalidade. Na cena Pantheon, por exemplo, o som do Fountain foi colocado como um emissor separado, próximo o suficiente para o usuário, para que pudesse ter uma noção de ' Sonic da Parallax ' conforme eles percorrem o espaço de jogo. Na cena Salinas de Maras do Peru, a perspectiva individual de alguns dos pequenos fluxos foi colocada como emissores separados para criar um ambiente ambiente mais imersiva, ao redor do usuário com os sons autênticos desse local.
* **Emissor de spline**: esse emissor de som espacial especial se move em espaço 3D em relação à posição visual do objeto ao qual ele está anexado. Um exemplo disso foi o treinamento no Machu Picchu, no qual usamos um emissor de spline para dar uma noção distinta de direcionalidade e movimento.
* **Music e SFX**: determinados aspectos de HoloTour que representam uma abordagem mais estilizada ou Cinematic usam efeitos de música e som para reforçar o impacto emocional. Na batalha de Gladiator ao final do Tour de Roma, efeitos especiais como whooshes ou Stingers foram usados para ajudar a reforçar o efeito dos rótulos que aparecem em cenas.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>@Microsoft do designer de áudio</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Som espacial no Unity](spatial-sound-in-unity.md)
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 

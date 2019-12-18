---
title: Estudo de caso-design de som espacial para HoloTour
description: Para criar um tour virtual 3D verdadeiramente envolvente para o Microsoft HoloLens, os vídeos panorâmicos e o cenário Holographic são apenas parte da fórmula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, HoloTour, som espacial, estudo de caso
ms.openlocfilehash: f2dd704089d9c76b7ba175a4a1ad5cebf9ec6c68
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181921"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>Estudo de caso: design de som espacial para HoloTour

Vídeos panorâmicos e cenários holographics são apenas parte da fórmula para um tour virtual do Microsoft HoloLens verdadeiramente envolvente. Este artigo descreve como o som foi usado para fazer você sentir como você realmente está em cada local HoloTour.

## <a name="the-tech"></a>O Tech

As belas imagens e cenas holographics que você vê em HoloTour são apenas uma parte de uma experiência de realidade mista verossímeis. Embora os hologramas só possam aparecer visualmente na frente de um usuário, o [som espacial](spatial-sound.md) que o HoloLens entrega de todas as direções fornece uma experiência de sensor mais completa.

O som espacial fornece indicações para indicar uma direção que o usuário deve ativar ou para permitir que o usuário saiba que há mais hologramas para ver dentro de seu espaço. Também podemos anexar um som diretamente a um holograma e atualizar continuamente a direção e a distância que o holograma é do usuário. Essa técnica faz parecer que o som é proveniente diretamente desse objeto.

Para o HoloTour, queríamos aproveitar os recursos de som espacial do HoloLens para criar um ambiente de 360 graus que é sincronizado com o vídeo para revelar os destaques da Sonic de locais específicos.

## <a name="behind-the-scenes"></a>Nos bastidores

Criamos experiências HoloTour de dois locais diferentes: Roma e Machu Picchu. Para fazer esses Tours se sentirem autênticos e atraentes, queríamos capturar áudio dos locais onde nos refilmemos em vez de usar sons genéricos.

### <a name="capture-the-audio"></a>Capturar o áudio

Em nosso [estudo de caso sobre como capturar o conteúdo visual para HoloTour](case-study-capturing-and-creating-content-for-holotour.md), falamos sobre o design do nosso Rig de câmera. Ele consistiu em 14 câmeras GoPro em um invólucro 3D que foi projetado para se ajustar ao Tripod. Para capturar áudio, adicionamos uma matriz de microfone quádruplo abaixo das câmeras. O som foi alimentado em uma unidade de gravação compactada de quatro canais na base do tripod. Escolhemos os microfones que executaram bem, mas eram pequenos o suficiente para evitar interferir nas câmeras.

![equipamentos de câmera e microfone personalizados](images/camera-rig-microphones-300px.png)<br>
*Câmera personalizada e Rig do microfone*

Essa configuração captura som em quatro direções. Registramos informações suficientes para recriar um panorama 3D auricular de som espacial, que poderíamos ser sincronizado posteriormente com o vídeo de 360 graus.

Um desafio do áudio da matriz de câmera é que você está na mercê de sons fora da câmera, como Sirens, aviões ou altos ventos. Para certificar-se de que tínhamos todos os elementos de som que precisávamos, também usamos os gravadores móveis estéreo e mono para capturar o som ambiente assíncrono em pontos de interesse específicos em cada local. Essas gravações fornecem ao designer de som o conteúdo limpo para adicionar interesse e melhorar a direcionalidade na produção.

Cada dia de captura gera muitos arquivos. Portanto, era importante desenvolver um sistema para controlar quais arquivos correspondem a um local ou uma captura de câmera específica. Nossa unidade de gravação foi configurada para nomear automaticamente os arquivos por data e o número "Take". Fazemos backup de arquivos em unidades externas no final de cada dia. Também achamos importante para o início verbal das gravações de áudio. Essa precaução permite uma identificação contextual fácil do conteúdo caso ocorram problemas de nome de arquivo. Também era importante remediar visualmente a captura de Rig da câmera, pois o vídeo e o áudio foram registrados como mídia separada e precisavam ser sincronizados durante a produção.

### <a name="edit-the-audio"></a>Editar o áudio

De volta ao estúdio após a viagem de captura, a primeira etapa na montagem de uma experiência de auricular direcional e de imersão é examinar todo o áudio que foi capturado para um local. Escolhemos a melhor forma e identificamos os destaques que podem ser aplicados durante a integração. O áudio é então editado e limpo. Por exemplo, uma haste de carro que dura um segundo ou então repete algumas vezes pode ser substituída por áudio de ambiente mais silencioso da mesma sessão de captura.

Depois que a edição de vídeo de um local é definida, o designer de som pode sincronizar o áudio correspondente. Neste ponto, avaliamos as capturas de câmera e de som móvel para decidir quais elementos funcionariam para criar uma cena de áudio de imersão. Descobrimos que é útil colocar todos os elementos Sound em um editor de áudio e criar simulações lineares rápidas para experimentar diferentes ideias de combinação. Esta etapa nos forneceu ideias mais bem formadas para quando chegou a hora de criar os bastidores de HoloTour reais.

### <a name="assemble-the-scene"></a>Montar a cena

A primeira etapa para a criação de uma cena de ambiente 3D é criar uma base de sons gerais de loop de ambiente em segundo plano que dará suporte a outros recursos e elementos de som interativos em uma cena. Pegamos uma abordagem holística à implementação, conforme determinado pelos critérios de design de qualquer cena específica. Algumas cenas podem ser indexadas para usar a captura de câmera sincronizada. Mais "Cinematic" momentos pode exigir uma abordagem organizada que dependa de sons, elementos interativos e música inseridos de maneira discreta.

Quando indexamos o áudio de captura de câmera, colocamos emissores de áudio de ambiente habilitados para som espacial que corresponderam à orientação direcional das câmeras. A exibição da câmera do Norte Reproduz áudio do microfone norte e, da mesma forma, para as outras direções Cardeal. Esses emissores são bloqueados pelo mundo, o que significa que, quando o usuário transforma sua cabeça em relação a eles, o som muda. Essa técnica modela efetivamente o som de pé nesse local. Ouça o Piazza Navona ou o Pantheon para obter exemplos de cenas que usam uma boa combinação de áudio capturado na câmera.

Em uma abordagem diferente, às vezes executamos loops estéreo de Ambience em conjunto com emissores de som espaciais que são colocados em volta da cena. Esses emissores reproduzem sons únicos de frequência aleatória de volume, densidade e gatilho. Essa técnica cria Ambience que tem um aspecto aprimorado de direcionalidade. No Aguas Alienates, por exemplo, você pode saber como cada quadrante do panorama tem emissores específicos que realçam áreas específicas da geografia, mas trabalham em conjunto para criar um Ambience de imersão geral.

## <a name="tips-and-tricks"></a>Dicas e truques

Há algumas maneiras adicionais de destacar a direcionalidade e melhorar o imersão para fazer uso completo dos recursos de som espacial do HoloLens. Fornecemos uma lista aqui. Escute esses efeitos na próxima vez que tentar HoloTour.
* **Procurar destinos:** Esses sons são disparados quando você examina um objeto ou uma área específica do quadro Holographic. Por exemplo, procure o café do lado da rua no Piazza Navona de Roma para disparar sutilmente sons de Busy-restaurante.
* **Visão local:** Embora a jornada HoloTour contenha determinados "batidas", onde o guia do Tour, auxiliado por holograma, explora um tópico em detalhes. Por exemplo, à medida que a fachada do Pantheon é resolvida para revelar o Oculus, o áudio do reverberating que foi colocado como um emissor 3D de dentro do Pantheon incentiva o usuário a explorar o interior.
* **Direcionalidade aprimorada:** Em muitos bastidores, colocamos sons de várias maneiras de adicionar à direcionalidade. Na cena Pantheon, por exemplo, o som do Fountain foi colocado como um emissor separado próximo o suficiente para que o usuário pudesse ter uma noção de "Sonic da Parallax" à medida que eles se encaminharem pelo espaço de jogo. Na cena Salinas de Maras do Peru, os sons de pequenos fluxos individuais foram colocados como emissores separados para criar um ambiente ambiente mais imersiva, ao redor do usuário com os sons autênticos desse local.
* **Emissor de spline:** Esses emissores se movem em espaço 3D em relação à posição visual do objeto ao qual estão anexados. Um exemplo é o treinamento no Machu Picchu, no qual usamos um emissor de spline para dar uma noção distinta de direcionalidade e movimento.
* **Música e SFX:** Determinados aspectos de HoloTour que representam uma abordagem mais estilizada ou Cinematic usam efeitos de música e som para reforçar o impacto emocional. Na batalha de Gladiator no final do Tour de Roma, por exemplo, efeitos especiais como whooshes e Stingers ajudam a reforçar o efeito dos rótulos que aparecem nos bastidores.

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Som espacial no Unity](spatial-sound-in-unity.md)
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

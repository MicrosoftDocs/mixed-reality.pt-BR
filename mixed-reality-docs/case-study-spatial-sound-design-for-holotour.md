---
title: Estudo de caso - espacial design som para HoloTour
description: Para criar um tour virtual de 3D verdadeiramente imersivo para o Microsoft HoloLens, os vídeos panorâmicas e o cenário holográfico são apenas uma parte da fórmula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, HoloTour, estudo de caso, som espacial
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590699"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>Estudo de caso - espacial design som para HoloTour

Para criar um tour virtual de 3D verdadeiramente imersivo para o Microsoft HoloLens, os vídeos panorâmicas e o cenário holográfico são apenas uma parte da fórmula. Jason Syltebo fala sobre como o som do designer de áudio foi capturado e processado para torná-lo a sentir como está, na verdade, em cada um dos locais a HoloTour.

## <a name="the-tech"></a>O técnico

O belas imagens e cenas holográfica, que você vê no HoloTour são apenas uma parte da criação de uma experiência de realidade misturada verossímeis. Embora hologramas só podem aparecer visualmente na frente de um usuário, o [som espacial](spatial-sound.md) recurso do HoloLens permite áudio provenientes de todas as direções, que dá ao usuário uma experiência mais completa de aparelhos.

Som espacial nos permite fornecer indicações de áudio para indicar uma direção na qual o usuário deve ativar ou Avisar ao usuário que há mais hologramas para que eles possam ver dentro de seu espaço. Podemos também anexar um som diretamente a um holograma e atualizar continuamente a direção e a distância que de holograma é de um usuário para torná-lo parecer como se o som é provenientes diretamente do objeto.

Com HoloTour, queremos aproveitar os recursos de som espaciais do HoloLens, para criar um ambiente de ambiente de 360 graus, sincronizado com o vídeo para revelar os destaques sonic locais específicos.

## <a name="behind-the-scenes"></a>Nos bastidores

Criamos experiências HoloTour dos dois locais diferentes: Roma e Machu Picchu. Para fazer esses tours se sintam autêntica e atraente queremos evitar o uso de genéricos sons e capturar o áudio diretamente nos locais em que podemos foram filmagem em vez disso.

### <a name="capturing-the-audio"></a>Captura de áudio

No nosso [estudo de caso sobre como capturar o conteúdo visual para HoloTour](case-study-capturing-and-creating-content-for-holotour.md), falamos sobre o design personalizado do nosso simuladores de carga de câmera. Consistiu em 14 câmeras GoPro contidas em um invólucro 3D-impresso, projetado para as dimensões específicas a tripé. Para capturar esse simulador de carga de áudio, adicionamos uma matriz de microfone quad abaixo as câmeras, que são inseridos em uma unidade de gravação de 4 canais compact sentei na base do tripé. Escolhemos microfones que não apenas executadas bem, mas que tinha um volume muito pequeno, para não occlude o modo de exibição da câmera.

![Simulador de carga personalizada de câmera e microfone](images/camera-rig-microphones-300px.png)<br>
*Simulador de carga personalizada de câmera e microfone*

Esta instalação capturada som em quatro direções o local exato da nossa câmera, dando informações suficientes para recriar um panorama auricular 3D usando o som espacial, o que nós pudéssemos sincronizar posteriormente para o vídeo de 360 graus.

Um dos desafios com o áudio de matriz da câmera é que você está à mercê do que é gravado no momento da captura. Mesmo se a captura de vídeo for boa, a captura de som pode se tornar problemática devido a sons de fora da câmera como sirenes, aviões ou ventos alta. Para garantir que tínhamos todos os elementos que precisamos, usamos uma série de unidades de gravação de móveis estéreo e mono obter elementos de assíncronos, o ambientes em pontos específicos de interesse em cada local. Esta captura é importante, pois ele permite que o designer de som para buscar o conteúdo limpo e utilizável que pode ser usado na produção após a criação de seu interesse e adicionar mais direcionalidade.

Qualquer dia determinado captura geraria um grande número de arquivos. Ele era importante desenvolver um sistema para controlar quais arquivos correspondem a um local específico ou a câmera captura. Nossa unidade de gravação foi configurada para arquivos de nome automático por data e número tirado e podemos faria backup esses no final do dia para unidades externas. Na pior das hipóteses, verbalmente slating início de gravações de áudio era importante, pois isso permite a fácil identificação contextual do conteúdo devem nomes de arquivos se tornar um problema. Também foi importante para que possamos visualmente como o vídeo e áudio foram registrados como mídia separada e necessários a serem sincronizados durante o post de imagem fixa a captura da câmera simuladores de carga.

### <a name="editing-the-audio"></a>Edição de áudio

Novamente no studio após a viagem de captura, montando uma experiência auricular direcional e envolvente a primeira etapa é examinar a captura de áudio para um local, escolher a melhor usa e identificar qualquer destaques que pudesse ser aplicados de forma criativa durante todos integração. O áudio é, em seguida, editado e limpos. Por exemplo, uma haste carro barulhento que dura um segundo e repetir algumas vezes, pode ser substituído e montada com seções de áudio silenciosa, o ambiente da mesma captura.

Quando a edição de vídeo para um local tiver sido estabelecida com o que Designer de som pode sincronizar o áudio correspondente. Neste ponto, nós trabalhamos com captura com câmera simuladores de carga e captura móvel para decidir quais elementos ou combinação delas funcionarão para criar uma cena do áudio envolvente. Uma técnica que encontramos útil era adicionar todos os elementos de som em um áudio editor e compilação rápida linear fictício no-break para fazer experiências com ideias de mistura de diferentes. Isso nos deu melhor ideias formadas quando chegou a hora de criar o plano HoloTour real.

### <a name="assembling-the-scene"></a>Montando a cena

A primeira etapa para criar uma cena 3D de ambiente é criar um ambiente de geral sons em segundo plano ambiente loop que dará suporte a outros recursos e elementos interativos de som em uma cena. Fazer isso, usamos uma abordagem holística para determinado pelas necessidades específicas e os critérios de design de qualquer determinado cena de técnicas de implementação diferentes. Alguns cenas podem de índice na direção do uso da captura de câmera sincronizado, enquanto outros podem exigir uma abordagem mais estruturada que usa mais discretamente colocados sons, elementos interativos e música e som efeitos para os momentos mais Cinemático em HoloTour.

Ao indexar sobre o uso de áudio de captura de câmera, colocamos espaciais habilitado o som ambientes áudio emissores correspondente às coordenadas direcionais da orientação da câmera, de modo que a visualização da câmera Norte reproduz áudio do microfone do Norte e da mesma forma para outras direções cardinais. Esses emissores são bloqueados ao mundo, que significa que o usuário pode livremente ativar suas cabeças em relação a essas emissores e o som será alterada da mesma forma, modelagem efetivamente o som de pé nesse local. Ouça a Piazza Navona ou o Pantheon para obter exemplos de segundo plano que usam uma combinação válida de áudio de câmera capturado.

Uma abordagem diferente envolvidos brincando um ambiente estéreo em loop em conjunto com os emissores de som espaciais colocados ao redor do cenário de reprodução de sons únicas que são randomizados em termos de frequência de volume, densidade e o gatilho. Isso cria um ambiente com uma maior sensação de direcionalidade. No Aguas Calientes, por exemplo, você pode ouvir como cada quadrante do panorama tem os emissores específicos que destacam intencionalmente as áreas específicas da geografia, mas funcionam em conjunto para criar um ambiente imersivo geral.

## <a name="tips-and-tricks"></a>Dicas e truques

Quando você está colocando juntos áudio para uma cena, existem alguns métodos adicionais que você pode usar para realçar ainda mais a direcionalidade e imersão, fazer uso total de recursos espaciais som do HoloLens. Nós fornecemos uma lista de alguns abaixo — ouça-os na próxima vez que você tente HoloTour.
* **Procurar destinos**: Esses são os sons que disparam somente quando você está examinando um objeto específico ou a área do quadro holográfica. Por exemplo, procurando na direção de café o lado da rua em Piazza Navona do Roma disparará um pouco os sons de um restaurante ocupado.
* **Visão local**: A jornada embora HoloTour contenha determinados vence onde orientar seu tour, auxiliado pelos hologramas, irá explorar um assunto em detalhes. Por exemplo, à medida que a fachada do Pantheon se dissolva para revelar o oculus, áudio reverberating colocados como um emissor 3D de dentro do Pantheon incentiva o usuário para explorar o modelo interior.
* **Aprimorada a direcionalidade**: Em muitos cenas, colocamos sons de várias maneiras para adicionar à direcionalidade. Na cena Pantheon, por exemplo, o som de fica a fonte foi colocado como um emissor separado feche suficiente para o usuário, para que eles poderiam ter uma ideia do 'sonic parallax' como percorrida por eles em todo o espaço de execução. Na cena de Salinas de Maras do Peru, sob a perspectiva individual de alguns fluxos pouco foram colocados como emissores separados para criar um ambiente de ambiente mais imersivo, envolvendo o usuário com os sons autênticos do local.
* **Emissor de spline**: Move este emissor de som espacial especial no espaço 3D em relação a posição visual do objeto a que é anexado. Um exemplo disso foi o treinamento em Machu Picchu, em que usamos um emissor de spline para dar uma noção distinta de direcionalidade e movimentação.
* **Música e SFX**: Determinados aspectos de HoloTour que representam uma abordagem mais estilizada ou animação da usarem música e efeitos de som para aumentar o impacto emocional. Na batalha gladiator no final do tour Roma, efeitos especiais, como whooshes ou stingers foram usados para ajudar a fortalecer o efeito dos rótulos que aparecem em segundo plano.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>Designer de áudio @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Som espacial](spatial-sound.md)
* [Design de som espacial](spatial-sound-design.md)
* [Som espacial no Unity](spatial-sound-in-unity.md)
* [MR Spatial 220](holograms-220.md)
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 

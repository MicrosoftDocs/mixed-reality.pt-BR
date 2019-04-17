---
title: Conceitos básicos de interação
description: Como criamos experiências em HoloLens (1º gen), 2 HoloLens e fones imersivos em exposição, iniciamos anotar algumas coisas que encontramos útil para compartilhar.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realidade, interação, de design
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589082"
---
# <a name="interaction-fundamentals"></a>Conceitos básicos de interação

Como criamos experiências em HoloLens e fones imersivos em exposição, começamos a escrever algumas coisas que encontramos útil para compartilhar. Pense nisso como blocos de construção fundamentais para o design de interação de realidade misturada.

## <a name="device-support"></a>Suporte a dispositivos

Aqui está uma estrutura de tópicos de artigos de design de interação disponíveis e o tipo de dispositivo ou tipos que se aplicam a.
<br>

<table>

<th>
<tr>

<td style="width:150px;"><strong>entrada</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
</tr>
</th>
 
<tr>
<td> <a href="gestures.md">Mãos articuladas</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td></td>

</tr><tr>
<td> <a href="gaze-targeting.md">Direcionamento de olhos</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;"></td>
</tr><tr>
<td> <a href="gaze-targeting.md">Mantenha o foco de direcionamento</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gestures.md">Gestos</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-design.md">Design de voz</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> Gamepad</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
<tr>
<td> <a href="motion-controllers.md">Controladores de movimento</a></td><td></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>

</tr>
<th>
<tr>
<td style="width:150px;"><strong>Percepção e recursos espaciais</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
</tr>
</th>
<tr>

<td> <a href="spatial-sound-design.md">Design de som espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping-design.md">Design de mapeamento espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="hologram.md">Hologramas</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a>O usuário é a câmera

![Usuário é a câmera](images/useriscamera-640px.jpg)

Sempre pense sobre design para o ponto de vista do seu usuário quando eles passam sobre seus mundos reais e virtuais.

**Algumas perguntas a serem feitas**
* É o usuário sentado, reclinável, aguardando ou percorrer durante o uso de sua experiência?
* Como o seu conteúdo se ajustará para posições diferentes?
* O usuário poderá ajustá-lo?
* O usuário estará familiarizado com o uso de seu aplicativo?

**Práticas recomendadas**
* O usuário é a câmera e eles controlam a movimentação. Deixe-os da unidade.
* Se você precisar praticamente o usuário de transporte, se sensível a problemas de discomfort vestibular.
* Usar animações mais curtas
* Animar de inferior/esquerda/direita ou aplicar fade-in, em vez de Z
* Reduzir a velocidade de medição de tempo
* Permitir que o usuário ver o mundo em segundo plano

**O que evitar**
* Não shake a câmera ou propositadamente bloqueá-la para 3DOF (apenas orientação, nenhuma conversão), ele pode fazer com que os usuários não se sinta confortável.
* Nenhum movimento abrupto. Se você precisar levar conteúdo de ou para o usuário, movê-lo lentamente e sem problemas em direção a eles para máximo conforto. Os usuários serão reagir a menus grandes, chegando até eles.
* Não acelerar ou ativar a câmera do usuário. Os usuários são sensíveis a aceleração (angular e conversão).

## <a name="leverage-the-users-perspective"></a>Aproveite a perspectiva do usuário

Os usuários veem o mundo da realidade misturada por meio de exibições em dispositivos envolventes e holographic. Em HoloLens, essa exibição é chamada a [quadro holográfico](holographic-frame.md).

No desenvolvimento de 2D, configurações e conteúdo acessado com frequência podem ser colocadas nos cantos de uma tela para torná-los facilmente acessíveis. No entanto, nos aplicativos holográfico, o conteúdo nos cantos do modo de exibição do usuário pode ser desconfortável para acesso. Nesse caso, o centro do quadro holográfico é o local principal para o conteúdo.

O usuário talvez precise ser guiado para ajudar a localizar os eventos importantes ou objetos além do modo de exibição de imediato. Você pode usar as setas, trilhas de luz, movimentação do cabeçote de caractere, balões de pensamento, ponteiros, som espacial e prompts de voz para ajudar a orientar o usuário ao conteúdo importante em seu aplicativo.

É recomendável não bloqueio de conteúdo na tela de conforto do usuário. Se você precisar manter o conteúdo no modo de exibição, coloque-o no mundo e tornar o conteúdo "tag-along" como o menu Iniciar. Conteúdo que é retirado, juntamente com a perspectiva do usuário se sentirão mais natural no ambiente.

![No menu Iniciar segue o modo de exibição do usuário quando ele atinge a borda do quadro](images/tagalong-1000px.jpg)<br>
*No menu Iniciar segue o modo de exibição do usuário quando ele atinge a borda do quadro*

Em HoloLens, hologramas se sentir reais quando eles se ajustarem dentro do quadro holográfico, pois eles não sejam cortados. Os usuários se moverá para ver os limites de um holograma dentro do quadro. Em HoloLens, é importante simplificar sua interface do usuário para se ajustar no modo de exibição do usuário e mantém o foco na ação principal. Para fones imersivos em exposição, é importante manter a ilusão de um mundo virtual persistente dentro do campo de visão do dispositivo.

## <a name="user-comfort"></a>Conforto do usuário

Para garantir a máxima [conforto](comfort.md) em telas de fone de ouvido, é importante para designers e desenvolvedores criar e apresentar o conteúdo de uma maneira que simule como humanos interpretam formas 3D e a posição relativa dos objetos no natural mundo. De uma perspectiva de física, também é importante projetar o conteúdo que não exija fatiguing movimentos do pescoço ou braços.

Desenvolvendo para HoloLens ou fones imersivos em exposição, é importante renderizar elementos visuais para ambos os olhos. Renderizar uma exibição de alerta em um olho só pode fazer uma interface difíceis de entender, bem como causando uneasiness olho e o cérebro do usuário.

## <a name="share-your-experience"></a>Compartilhe sua experiência

Usando o [misto captura realidade](mixed-reality-capture.md), os usuários podem capturar uma foto ou vídeo de sua experiência a qualquer momento. Considere a possibilidade de experiências em seu aplicativo em que você talvez queira incentivar instantâneos ou vídeos.

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a>Aproveite os elementos de interface do usuário básicos do Windows Mixed Reality inicial

Assim como a experiência de PC do Windows é iniciado com a área de trabalho, Windows Mixed Reality começa com a página inicial. O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) usa nossa capacidade inata para compreender e navegar lugares 3D. Com o HoloLens, sua página inicial é o espaço físico. Com fones imersivos em exposição, sua página inicial é um lugar virtual.

Sua casa também é onde você usará o menu Iniciar para abrir e colocar aplicativos e conteúdo. Você pode preencher sua casa com conteúdo de realidade mista e multitarefa com o uso de vários aplicativos ao mesmo tempo. As coisas que você coloca na sua casa permanecem lá, mesmo se você reiniciar seu dispositivo.

## <a name="see-also"></a>Consulte também
* [Mantenha o foco de direcionamento](gaze-targeting.md)
* [Gestos](gestures.md)
* [Design de voz](voice-design.md)
* [Controladores de movimento](motion-controllers.md)
* [Design de som espacial](spatial-sound-design.md)
* [Design de mapeamento espacial](spatial-mapping-design.md)
* [Conforto](comfort.md)
* [Navegando o Windows Mixed Reality inicial](navigating-the-windows-mixed-reality-home.md)

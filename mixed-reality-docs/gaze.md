---
title: Focar
description: Olhar é a primeira forma de entrada e é uma forma primária de direcionamento dentro de realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, olhar, interação, design
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414375"
---
# <a name="gaze"></a>Focar

**Olhar** é a primeira forma de entrada e é uma forma primária de direcionamento dentro de realidade misturada. O olhar informa o que o usuário está procurando no mundo e permite que você determine sua intenção. No mundo real, você normalmente examinará um objeto com o qual você pretende interagir. Isso é o mesmo com olhar.

Os headsets de realidade misturada usam a posição e a orientação da cabeça do usuário para determinar o vetor olhar de cabeça. Você pode considerar esse vetor como um ponteiro laser diretamente entre os olhos do usuário. À medida que o usuário olha pela sala, seu aplicativo pode Interseccionar esse raio, ambos com seus próprios hologramas e com a malha de [mapeamento espacial](spatial-mapping.md) para determinar qual objeto virtual ou real seu usuário pode estar olhando.

No HoloLens 2, as interações podem ser direcionadas pela cabeça do usuário olhar, olho olhar ou pelas interações de perto ou longe da mão.
No HoloLens (1º gen), as interações geralmente devem derivar seu direcionamento do olhar de cabeça do usuário, em vez de tentar renderizar ou interagir diretamente no local da mão. Depois que uma interação for iniciada, movimentos relativos da mão poderão ser usados para controlar o [gesto](gestures.md), assim como com o gesto de [manipulação ou de navegação](gestures.md#composite-gestures) . Com headsets de imersão, você pode direcionar usando olhar de cabeça ou [controladores de movimento](motion-controllers.md)com capacidade de apontamento.

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Olhar de cabeçalho</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Olhar de olho</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Mais diretrizes específicas para o HoloLens 2 em [breve](index.md#news-and-notes).


## <a name="uses-of-gaze"></a>Usos de olhar

Como um desenvolvedor de realidade misturada, você pode fazer muito com olhar de cabeça ou olho:
* Seu aplicativo pode Interseccionar olhar com os hologramas em sua cena para determinar onde está a atenção do usuário.
* Seu aplicativo pode direcionar gestos e pressionamentos de controlador com base no olhar do usuário, permitindo que o usuário selecione, ative, pegue, role ou, de outra forma, interaja com seus hologramas.
* Seu aplicativo pode permitir que o usuário Coloque os hologramas em superfícies do mundo real, interseccionando seu olhar Ray com a malha de mapeamento espacial.
* Seu aplicativo pode saber quando o usuário *não* está olhando para a direção de um objeto importante, o que pode levar seu aplicativo a dar indicações visuais e de áudio para virar esse objeto.

## <a name="cursor"></a>Cursor

Para o Head olhar, a maioria dos aplicativos deve usar um [cursor](cursors.md) (ou outra indicação de auditoria/Visual) para dar ao usuário a confiança no que eles estão prestes a interagir. Normalmente, você posiciona esse cursor no mundo em que o Head olhar Ray primeiro cruza um objeto, que pode ser um holograma ou uma superfície do mundo real.

![Um cursor visual de exemplo para mostrar olhar](images/cursor.jpg)<br>
*Um cursor visual de exemplo para mostrar olhar*

Para olhar de olho, geralmente recomendamos *não* mostrar um cursor, pois isso pode rapidamente se tornar confuso e irritante para o usuário. Em vez disso, destaque sutilmente os destinos visuais ou use um cursor de olho muito fraco para fornecer confiança sobre o que o usuário está prestes a interagir. Para obter mais informações, confira nossas [diretrizes de design para entrada baseada em olhos](eye-tracking.md) no HoloLens 2.

## <a name="giving-action-to-the-users-gaze"></a>Dando ação ao olhar do usuário

Depois que o usuário tiver direcionado um holograma ou um objeto do mundo real usando seus olhar, a próxima etapa será executar uma ação nesse objeto. As principais maneiras de um usuário executar ações são por meio de [gestos](gestures.md), [controladores de movimento](motion-controllers.md) e [voz](voice-input.md).

## <a name="see-also"></a>Consulte também
* [Entrada do MR 210: Olhar de cabeçalho](holograms-210.md)
* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Olhar de cabeçalho no Unity](gaze-in-unity.md)
* [Olho-olhar no HoloLens 2](eye-tracking.md)
* [Olho olhar no Unity usando o kit de ferramentas da realidade misturada](https://aka.ms/mrtk-eyes)

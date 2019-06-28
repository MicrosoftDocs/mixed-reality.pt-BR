---
title: Focar
description: Olhar é o primeiro formulário de entrada e um formulário principal de direcionamento de dentro de realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realidade, olhar, interação, de design
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414375"
---
# <a name="gaze"></a>Focar

**Mantenha o foco** é o primeiro formulário de entrada e é uma forma principal de direcionamento dentro de realidade misturada. Olhar informa onde o usuário está procurando no mundo e permite que você determine sua intenção. No mundo real, você geralmente verá um objeto que você pretende interagir com. Isso é o mesmo com olhar.

Realidade misturada headsets usarem a posição e orientação da cabeça do usuário para determinar seu vetor olhar principal. Você pode pensar esse vetor como um ponteiro a laser diretamente para frente da diretamente entre a atenção do usuário. Como o usuário procura ao redor de sala, seu aplicativo pode se cruzar essa ray com seus próprio hologramas e com o [mapeamento espacial](spatial-mapping.md) malha para determinar que o usuário pode estar olhando de objeto reais ou virtual.

Em 2 HoloLens, interações podem ser alvo de olhar de principal do usuário, olhar olho ou por meio de perto ou muito entregar as interações.
No HoloLens (1º gen), as interações geralmente devem derivar seu direcionamento de olhar de principal do usuário, em vez de tentar renderizar ou interagir diretamente no local da mão. Após o início de uma interação relativos movimentos da mão podem ser usado para controlar a [gesto](gestures.md), assim como acontece com as [manipulação ou navegação](gestures.md#composite-gestures) gesto. Com fones imersivos em exposição, você pode direcionar usando qualquer um dos olhar principal ou compatíveis com apontando [controladores de movimento](motion-controllers.md).

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
        <td>Mantenha o foco principal</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Olhar olho</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).


## <a name="uses-of-gaze"></a>Usos de olhar

Como um desenvolvedor de realidade misturada, você pode fazer muito com olhar head ou olhos:
* Seu aplicativo pode se cruzar olhar com os hologramas na sua cena para determinar onde está a atenção do usuário.
* Seu aplicativo pode direcionar gestos e pressionamentos de controlador com base em olhar do usuário, permitindo que o usuário selecione, ativar, pegue, role ou caso contrário, interagir com seus hologramas.
* Seu aplicativo pode permitir que o usuário coloque hologramas em superfícies do mundo real, por meio de interseção seu ray olhar com a malha de mapeamento espacial.
* Seu aplicativo possa saber quando o usuário estiver *não* procurando na direção de um objeto importante, que pode levar seu aplicativo para dar indicações de áudio e vídeo para ativar em direção esse objeto.

## <a name="cursor"></a>Cursor

Para olhar principal, a maioria dos aplicativos deve usar um [cursor](cursors.md) (ou outra indicação auditivo/visual) para dar a confiança do usuário no que está prestes a interagir com. Você normalmente posicionar esse cursor no mundo onde seu ray olhar principal primeiro faz interseção com um objeto, que pode ser um holograma ou uma superfície do mundo real.

![Um cursor visual de exemplo para mostrar a olhar](images/cursor.jpg)<br>
*Um cursor visual de exemplo para mostrar a olhar*

Para olhar olho, geralmente recomendamos *não* para mostrar um cursor, pois isso pode rapidamente se tornar causa distração e irritante do usuário. Em vez disso, um pouco realce visual destinos ou usar um cursor muito fraco olho para fornecer confiança sobre o que o usuário está prestes a interagir com. Para obter mais informações, Confira nossos [diretrizes de design para a entrada baseada em olho](eye-tracking.md) em HoloLens 2.

## <a name="giving-action-to-the-users-gaze"></a>Dando a ação para olhar do usuário

Depois que o usuário direcionou um holograma ou o objeto real usando seu olhar, sua próxima etapa é executar ação no objeto. As formas básicas para um usuário tomar medidas são feitas por meio [gestos](gestures.md), [controladores de movimento](motion-controllers.md) e [voz](voice-input.md).

## <a name="see-also"></a>Consulte também
* [Entrada do MR 210: Mantenha o foco principal](holograms-210.md)
* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Head olhar no Unity](gaze-in-unity.md)
* [Eye-gaze on HoloLens 2](eye-tracking.md)
* [Olhar de olho no Unity usando o Kit de ferramentas de realidade mista](https://aka.ms/mrtk-eyes)

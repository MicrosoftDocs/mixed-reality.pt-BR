---
title: Olhar e a pesquisa
description: Visão geral do olhar e do modelo de entrada de duração
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidade misturada, olhar, pesquisa, interação, design, acompanhamento de olho, acompanhamento de cabeçalho
ms.openlocfilehash: d87406d0b2695cd86c40f27cb132af54ed525b25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435358"
---
# <a name="gaze-and-dwell"></a>Olhar e a pesquisa

Quando as mãos estão ocupadas com ferramentas e peças, os gestos podem ser entediantes ou impossíveis. Os comandos de voz também podem não ser confiáveis em determinados contextos, por exemplo, sob condições excessivamente alta. A olhar e a pesquisa oferecem um mecanismo familiar e fácil de dominar para as cabeças de trabalho e as mãos gratuitas no HoloLens. Além disso, o olhar e a pesquisa são um ótimo fallback que é independente da interferência de ruído ou restrições de silêncio no ambiente operacional.
Distinguimos duas variantes de _olhar e de duração_: [Head-olhar e de pesquisa](gaze-and-dwell-head.md) e [olho-olhar e a pesquisa](gaze-and-dwell-eyes.md).

## <a name="scenarios"></a>Cenários

A olhar e a pesquisa são Excel em cenários em que as mãos de uma pessoa estão ocupadas com outras tarefas, e a voz não é 100% confiável ou está disponível devido a restrições de ambiente ou sociais. Um bom exemplo é uma pessoa que usa o HoloLens para sobrepor informações de referência ao realizar reparos no motor de um carro. Suas mãos estão ocupadas com ferramentas ou para apoiar o corpo conforme acessa o compartimento do motor. O ambiente da garagem é barulhento, com estrondos e zumbidos constantes de ferramentas, o que dificulta os comandos de voz. A olhar e a pesquisa permitem que a pessoa que usa o HoloLens Navegue com confiança no material de referência sem interromper o fluxo de trabalho. 

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Focar com a cabeça e esperar</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
     <tr>
        <td>Olho-olhar e a pesquisa</td>
        <td>❌ não disponível</td>
        <td>✔️ Recomendado</td>
        <td>❌ não disponível</td>
    </tr>
</table>


<br>

---
 
 ## <a name="see-also"></a>Consulte também
* [Interação com base nos olhos](eye-gaze-interaction.md)
* [Acompanhamento de olho no HoloLens 2](eye-tracking.md)
* [Olhar e confirmar](gaze-and-commit.md)
* [Manipulação de mãos direta](direct-manipulation.md)
* [Gestos práticos](gaze-and-commit.md#composite-gestures)
* [Ponto de mãos e confirmação](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)

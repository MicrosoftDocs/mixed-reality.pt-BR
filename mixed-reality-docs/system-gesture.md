---
title: Gesto do sistema
description: Gesto do sistema para chamar o menu iniciar.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidade misturada, gestos, interação, design
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064235"
---
# <a name="system-gesture"></a>Gesto do sistema

O gesto do sistema é um gesto de mão usado para invocar o menu iniciar. É o equivalente a pressionar a tecla Windows no teclado, o botão Xbox em um controlador Xbox ou o botão Windows no controlador de movimento de headsets de imersão. É importante entender quais gestos são reservados para o sistema em cada dispositivo de realidade misturada para evitar conflitos ao projetar suas interações.

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Cair</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Botão do pulso</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Olho olhar e Palm up pinçar</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Cair
Para abrir o menu iniciar no HoloLens (1º gen), projetamos "flor", que é um gesto simbólico imitando Blossom de flor. É distintivo para a interação Surefooted, fácil de executar e rápida de se recuperar. Para fazer o gesto de cair no HoloLens (1º gen), mantenha sua mão em dia com seu Palm para cima e, em seguida, abra sua mão distribuindo os dedos.

:::row:::
    :::column:::
        ![de cair perto](images/bloom-close.png)<br>
        **Etapa 1: Palm juntos**<br>
    :::column-end:::
    :::column:::
        ![abertura](images/bloom-open.png)<br>
        **Etapa 2: Palm up com as mãos espalhadas**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a>Botão do pulso
No HoloLens 2, substituímos o gesto de cair com um botão de pulso virtual que permite interações mais instinctuals que não exigem ensino adicional. Ao mostrar os usuários o botão no pulso, eles podem acessá-lo intuitivamente e pressioná-lo com a outra mão.

:::row:::
    :::column:::
        ![botão do punho pronto](images/wrist-button-ready.png)<br>
        **Etapa 1: Palm up para mostrar o botão do pulso**<br>
    :::column-end:::
    :::column:::
        ![pressionar o botão do pulso](images/wrist-button-press.png)<br>
        **Etapa 2: Pressione o botão do pulso**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a>Olho-olhar e Palm up pinçar
Também projetamos uma solução única para facilitar o acesso no HoloLens 2. Esse gesto exige que os usuários olho olhar no botão do pulso e, em seguida, usam a mesma mão para realizar uma pinçagem para cima usando seu polegar e um dedo de índice.<br>
:::row:::
    :::column:::
        ![botão do punho pronto](images/wrist-button-ready.png)<br>
        **Etapa 1: Palm up para mostrar o botão do pulso**<br>
    :::column-end:::
    :::column:::
        ![botão do pulso de pinçagem](images/wrist-button-pinch.png)<br>
        **Etapa 2: olho olhar no botão e, em seguida, aperte**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Consulte também

* [Interações instinctuais](interaction-fundamentals.md)
* [Olhar fixo](eye-tracking.md)
* [Entrada de voz](voice-input.md)
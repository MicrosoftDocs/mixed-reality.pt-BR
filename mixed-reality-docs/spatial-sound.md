---
title: Áudio em realidade misturada
description: O áudio em realidade misturada pode aumentar a confiança do usuário em interações de interface de usuário e aprofundar os usuários na experiência.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: som espacial, som surround, áudio 3D, som 3D, áudio espacial
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181976"
---
# <a name="audio-in-mixed-reality"></a>Áudio em realidade misturada
O áudio é uma parte essencial do design e da produtividade na realidade misturada. O som pode:
* Aumente a confiança do usuário em interações de gesto e voz.
* Oriente os usuários para as próximas etapas.
* Combine efetivamente os objetos virtuais com o mundo real.

O rastreamento de cabeça de baixa latência de headsets de realidade misturada, incluindo o HoloLens, dá suporte à espacial de alta qualidade baseada em HRTF. Você pode espacialar o áudio em seu aplicativo para:
* Chame atenção para elementos visuais.
* Ajude os usuários a manter a conscientização de seus arredores do mundo real.

A acústica conecta mais profundamente os hologramas ao mundo da realidade misturada. Ele fornece indicações sobre o ambiente e o estado do objeto.

Consulte exemplos detalhados [de design que usa áudio](spatial-sound-design.md).

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (primeira gen)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Espacialização</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Aceleração de hardware de espacial</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>Uso de sons em realidade misturada
O [uso de sons em realidade misturada](spatial-sound-design.md) requer uma abordagem diferente do que em aplicativos de toque e teclado e mouse. As decisões de design de sons-chave incluem quais sons são espaciais e quais interações sonify. Essas decisões afetam altamente a confiança do usuário, a produtividade e a curva de aprendizado.

### <a name="case-studies"></a>Estudos de caso
O HoloTour praticamente leva os usuários para os sites Tourist e históricos em todo o mundo. Consulte o [projeto de som para o estudo de caso do HoloTour](case-study-spatial-sound-design-for-holotour.md) . Um microfone especial e uma configuração de renderização foram usados para capturar os espaços de assunto.

RoboRaid é um shooter de alta energia para o HoloLens. O [projeto de som para](case-study-using-spatial-sound-in-roboraid.md) o estudo de caso do RoboRaid descreve as opções de design que foram feitas para garantir que o áudio espacial foi usado para o efeito significativo mais completo.

## <a name="spatialization"></a>Espacialização
A espacialização é o componente direcional do áudio espacial. Para uma configuração de Home Theater 7,1, a espacial é tão simples quanto a panorâmica entre loudspeakers. Mas para fones de ouvido em realidade misturada, é essencial usar uma tecnologia baseada em HRTF para precisão e conforto. O Windows oferece a espacial baseada em HRTF, e esse suporte é acelerado por hardware no HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Devo me esespacial?
A espacialização pode melhorar muitos sons em aplicativos de realidade misturada. A espacial tira um som da cabeça do ouvinte e a coloca no mundo. Para obter sugestões sobre o uso efetivo da espacialização em seu aplicativo, consulte [design de som espacial](spatial-sound-design.md).

### <a name="spatializer-personalization"></a>Personalização de Spatializer
HRTFs Manipule as diferenças de nível e fase entre os ouvidos pelo espectro de frequência. Elas se baseiam em modelos físicos e medidas de pinnae (torso), de cabeça humana e de formas Ear. Nosso cérebro responde a essas diferenças para fornecer uma direção percebida em som.

Cada indivíduo tem uma forma Ear exclusiva, tamanho da cabeça e posição Ear. Portanto, a melhor HRTFs está em conformidade com você. Para aumentar a precisão da espacialização, o HoloLens usa a Pupilary de distância (IPD) do headset para ajustar o HRTFs para o tamanho da cabeça.

### <a name="spatializer-platform-support"></a>Suporte à plataforma Spatializer
O Windows oferece a espacialização, incluindo HRTFs, por meio da [API do ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound). Essa API expõe a aceleração de hardware de HRTF do HoloLens 2 para aplicativos.

### <a name="spatializer-middleware-support"></a>Suporte de middleware Spatializer
O suporte para o Windows ' HRTFs está disponível para os seguintes mecanismos de áudio de terceiros.
* Um [plug-in do mecanismo de áudio do Unity](spatial-sound-in-unity.md)
* Um [plug-in do mecanismo de áudio WWise](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>Acústica
O áudio espacial é maior que a direção. Outras dimensões incluem oclusão, obstrução, reverberação, portal e modelagem de origem. Coletivamente, essas dimensões são chamadas de *acústicas*. Sem acústicas, os sons espaciais não têm distância percebida.

Os tratamentos acústicos variam de simples a muito complexo. Você pode usar um simples reverbo com suporte em qualquer mecanismo de áudio para enviar sons espaciais para o ambiente do ouvinte. Sistemas acústicos como [acústicas de projetos](https://aka.ms/acoustics) fornecem tratamento acústico mais rico e mais atraente. Os acústicos de projeto podem modelar o efeito de paredes, portas e outras geometrias de cena em um som. É uma opção eficaz para casos em que a geometria de cena relevante é conhecida no momento do desenvolvimento.

## <a name="next-steps"></a>Próximas etapas
- [Som espacial no Unity](spatial-sound-in-unity.md)
- [Como usar o som em aplicativos de realidade mista](spatial-sound-design.md)

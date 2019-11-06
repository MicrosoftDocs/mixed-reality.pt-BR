---
title: Áudio em realidade misturada
description: O áudio em realidade misturada pode aumentar a confiança do usuário em interações de interface de usuário e aprofundar os usuários na experiência.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: som espacial, som surround, áudio 3D, som 3D, áudio espacial
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641112"
---
# <a name="audio-in-mixed-reality"></a>Áudio em realidade misturada
O áudio é uma parte essencial do design e da produtividade na realidade misturada e pode:
* Aumentar a confiança do usuário em interações baseadas em gestos e em voz
* Orientar os usuários para as próximas etapas
* Combine efetivamente os objetos virtuais com o mundo real

O rastreamento de cabeça de baixa latência de headsets de realidade misturada, incluindo o HoloLens, permite o uso de alta qualidade de espacial baseada em HRTF. A espacial de áudio em seu aplicativo pode:
* Chame atenção para elementos visuais
* Ajude os usuários a manter a conscientização de seus arredores do mundo real

A adição de acústicos conecta mais profundamente os hologramas ao mundo misto e pode fornecer indicações sobre o ambiente e o estado do objeto.

Para obter exemplos mais detalhados de design usando áudio, confira [design de som](spatial-sound-design.md).

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
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

## <a name="using-sounds-in-mixed-reality"></a>Usando sons em realidade misturada
[Usar sons em realidade mista](spatial-sound-design.md) pode exigir uma abordagem diferente do que em aplicativos de toque e teclado e mouse. As decisões de design de sons-chave incluem quais sons são espaciais e quais interações sonify. Essas decisões podem ter um efeito forte na confiança do usuário, na produtividade e na curva de aprendizado.

### <a name="case-studies"></a>Estudos de caso
O HoloTour praticamente leva os usuários para os sites Tourist e históricos em todo o mundo. O seguinte estudo de caso descreve o design de som para HoloTour: [design de som para HoloTour](case-study-spatial-sound-design-for-holotour.md). Um microfone especial e uma configuração de renderização foram usados para capturar os espaços de assunto.

RoboRaid é um shooter de alta energia para o HoloLens. O seguinte estudo de caso descreve as opções de design feitas para garantir que o áudio espacial foi usado para um efeito mais completo: [design de som para RoboRaid](case-study-using-spatial-sound-in-roboraid.md).

## <a name="spatialization"></a>Espacialização
A espacialização é o componente direcional do áudio espacial. Ao usar uma configuração de Home Theater 7,1, a espacial é tão simples quanto a visão panorâmica entre alto-falantes. Mas com fones de ouvido em realidade misturada, é essencial usar uma tecnologia baseada em HRTF para precisão e conforto. O Windows oferece a espacial baseada em HRTF, e esse suporte é acelerado por hardware no HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Devo me esespacial?
Muitos sons em aplicativos de realidade misturados se beneficiam da espacial, que tira um som da cabeça do ouvinte e o coloca no mundo. Consulte [design de som espacial](spatial-sound-design.md) para obter sugestões sobre os usos mais eficientes da espacialização em seu aplicativo.

### <a name="spatializer-personalization"></a>Personalização de Spatializer
HRTFs Manipule as diferenças de nível e fase entre os ouvidos pelo espectro de frequência. Elas se baseiam em modelos físicos e medidas de pinnae (torso), de cabeça humana e de formas Ear. Nosso cérebro responde a essas diferenças para dar uma percepção de direção em som. 

Cada indivíduo tem uma forma Ear exclusiva, tamanho da cabeça e posição ear, portanto, os melhores HRTFs são aqueles que estão em conformidade com você. O HoloLens aumenta a precisão da espacial usando a pupilaryy (distância) do headset exibido para ajustar o HRTFs para o tamanho da cabeça.

### <a name="spatializer-platform-support"></a>Suporte à plataforma Spatializer
O Windows oferece a espacialização, incluindo HRTFs, por meio da [API do ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound). Essa API expõe a aceleração de hardware de HRTF do HoloLens 2 para aplicativos.

### <a name="spatializer-middleware-support"></a>Suporte de middleware Spatializer
O suporte para o Windows ' HRTFs está disponível para alguns mecanismos de áudio de terceiros:
* Um plug-in do [mecanismo de áudio do Unity](spatial-sound-in-unity.md) chama o HRTF XAPO
* Um [plug-in do mecanismo de áudio WWise](https://www.audiokinetic.com/products/plug-ins/msspatial/) chama a API ISpatialAudioClient

## <a name="acoustics"></a>Acústica
O áudio espacial pode ser maior que a direção. Outras dimensões, incluindo oclusão, obstrução, reverberação, portal e modelagem de origem, são coletivamente chamadas de ' acústicas '. Sem acústicas, os sons espaciais não têm uma distância percebida.

O tratamento acústico pode variar de simples a muito complexo. Usando um simples reverbo, como o que tem suporte de qualquer mecanismo de áudio, você pode enviar sons espaciais para o ambiente ao redor do ouvinte. O tratamento acústico mais atrativo e mais atraente está disponível em sistemas acústicos como [acústicos de projetos](https://aka.ms/acoustics). Os acústicos de projeto podem modelar o efeito de paredes, portas e outras geometrias de cena em um som e é uma opção eficaz para casos em que a geometria de cena relevante é conhecida no momento do desenvolvimento.


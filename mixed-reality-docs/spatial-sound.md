---
title: Som espacial
description: Usar o som espacial em um aplicativo de realidade misturada permite que você coloque os sons de forma convincente em um espaço 3D.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: som espacial, som surround, áudio 3D, som 3D, áudio espacial
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829920"
---
# <a name="spatial-sound"></a>Som espacial

Quando os objetos estão fora de nossa linha de visão, uma das maneiras de percebermos o que está acontecendo em torno deles é por som. No Windows Mixed Reality, o mecanismo de áudio fornece o componente auricular da experiência de realidade misturada por meio da simulação de som 3D usando a direção, a distância e as simulações ambientais. O uso de som espacial em um aplicativo permite que os desenvolvedores coloquem os sons de forma convincente em um espaço 3 dimensional (esfera) em todo o usuário. Esses sons parecerão como se estivessem vindo de objetos físicos reais ou de hologramas de realidade misturada no ambiente do usuário. Considerando que os [hologramas](hologram.md) são objetos compostos de luz e, às vezes, som, o componente de som ajuda a aterrar os hologramas, tornando-os mais verossímeiss e criando uma experiência mais imersiva.

Embora os hologramas só possam aparecer visualmente em que o olhar do usuário esteja apontando, o som do seu aplicativo pode vir de todas as direções; acima, abaixo, atrás, ao lado, etc. Você pode usar esse recurso para chamar a atenção para um objeto que pode não estar no modo de exibição do usuário no momento. Um usuário pode perceber que os sons estão emanando de uma fonte no mundo de realidade misturada. Por exemplo, à medida que o usuário fica mais próximo de um objeto ou o objeto se aproxima deles, o volume aumenta. Da mesma forma, à medida que os objetos se movem em torno de um usuário, ou vice-versa, os sons espaciais fornecem a ilusão de que os sons são provenientes diretamente do objeto.

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

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
        <td>Som espacial</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (com fones de ouvido)</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>Simulando o local percebido e a distância dos sons

Ao analisar como o som atinge ambos os ouvidos, nosso cérebro determina a distância e a direção do objeto que emite o som. Uma HRTF (ou função de transferência relacionada à cabeça) simula essa interação modelando a resposta Spectral que caracteriza como um Ear recebe som de um ponto no espaço. O mecanismo de áudio espacial usa HRTFs personalizadas para expandir a experiência de realidade misturada e simular sons provenientes de várias direções e distâncias.

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

Indicações de áudio esquerda ou direita (Azimuth) originam-se das diferenças no momento em que o som chega a cada Ear. As indicações para cima e para baixo se originam de alterações Spectral produzidas pela forma de Ear externa (pinnae). Ao designar a origem do áudio, o sistema pode simular a experiência de som chegando em momentos diferentes para nossos ouvidos. Observe que no HoloLens, enquanto a espacial Azimuth é personalizada, a simulação de elevação é baseada em um conjunto médio de anthropometrics. Portanto, a precisão da elevação pode ser menos precisa do que a precisão do Azimuth.

As características dos sons também são alteradas com base no ambiente no qual existem. Por exemplo, gritar em um côncavo fará com que sua voz salte as paredes, os andares e os tetos, criando um efeito de eco. A configuração de modelo de sala de som espacial reproduz essas reflexos para inserir sons em um ambiente de áudio específico. Você pode usar essa configuração para corresponder o local real do usuário para simulação de sons nesse espaço para criar uma experiência de áudio mais imersiva.

## <a name="integrating-spatial-sound"></a>Integrando som espacial

Como o princípio geral da realidade misturada é o aterramento de [hologramas](hologram.md) no mundo físico do usuário ou no ambiente virtual, a maioria dos sons de hologramas deve ser espacial. No HoloLens, há considerações de orçamento de memória e CPU naturalmente, mas você pode usar vozes de som espacial de 10-12 ao usar menos de aproximadamente 12% da CPU (aproximadamente 70% de um dos quatro núcleos). O uso recomendado para vozes de som espacial inclui:
* Combinação de olhar (realce de objetos, particularmente quando fora da exibição). Quando um holograma precisar de atenção de um usuário, jogue um som nesse holograma (por exemplo, tenha um latido Virtual Dog). Isso ajuda o usuário a encontrar o holograma quando ele não está no modo de exibição.
* Áudio haptics (áudio reativo para interações sem toque). Por exemplo, jogue um som quando o controlador da mão ou de movimento do usuário entra e sai do quadro de gesto. Ou tocar um som quando o usuário selecionar um holograma.
* Imersão (sons de ambiente em torno do usuário).

Também é importante observar que, embora misturar sons estéreo padrão com som espacial possa ser eficaz na criação de ambientes realistas, os sons estéreos devem ser relativamente silenciosos para deixar espaço para os aspectos sutis do som espacial, como reflexos ( indicações de distância) que podem ser difíceis de ouvir em um ambiente barulhento.

O mecanismo de som espacial do Windows só dá suporte a uma taxa de amostra de 48K para reprodução. A maioria dos middlewares, como o Unity, converterá automaticamente os arquivos de som no formato com suporte, mas ao usar as APIs de áudio do Windows diretamente, corresponda ao formato do conteúdo ao formato suportado pelo efeito.

## <a name="see-also"></a>Consulte também
* [MR espacial 220](holograms-220.md)
* [Som espacial no Unity](spatial-sound-in-unity.md)
* [Som espacial no DirectX](spatial-sound-in-directx.md)
* [Projeto de som espacial](spatial-sound-design.md)

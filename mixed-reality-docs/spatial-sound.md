---
title: Som espacial
description: Usando o som espacial em um aplicativo de realidade misturada permite que você coloque convincingly sons em um espaço 3D.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: som espacial, som surround, áudio 3d, áudio de som, espacial 3d
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829920"
---
# <a name="spatial-sound"></a>Som espacial

Quando objetos são fora de nossa linha de visão, uma das maneiras que podemos pode perceber que está acontecendo ao nosso redor é por meio de som. Na realidade mista do Windows, o mecanismo de áudio fornece o componente auricular da experiência de realidade misturada, simulando o som 3D usando simulações ambientais, distância e direção. Usando o som espacial em um aplicativo permite aos desenvolvedores colocar convincingly sons em um espaço dimensional 3 (esfera) em todo o usuário. Os sons, em seguida, parecerá como se eles foram provenientes de objetos físicos real ou as hologramas de realidade misturada no ambiente do usuário. Considerando que [hologramas](hologram.md) são feitos de objetos de luz e ajuda o componente de som, às vezes, som, hologramas de zero, tornando-os mais verossímeis e criando uma experiência mais imersiva.

Embora hologramas só podem aparecer visualmente onde olhar do usuário está apontando, o som do seu aplicativo pode vir de todas as direções; acima, abaixo, por trás, para o lado, etc. Você pode usar esse recurso para chamar a atenção para um objeto que não pode ser atualmente no modo de exibição do usuário. Um usuário pode perceber sons para ser procedentes de uma fonte do mundo de realidade misturada. Por exemplo, à medida que o usuário fique próximo a um objeto ou o objeto fique próximo a eles, aumenta o volume. Da mesma forma, como objetos se movem em torno de um usuário, ou vice-versa, sons espaciais dar a ilusão de que os sons são provenientes diretamente do objeto.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Som espacial</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (com fones de ouvido)</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>Simulando a localização percebida e a distância de sons

Analisando como o som atinge ambos os nossos ouvidos, nosso cérebro determina a distância e direção do objeto emitir o som. Um HRTF (ou uma função de transferência de cabeçalho relacionados) simula essa interação, a resposta spectral que caracteriza como um ear recebe o som de um ponto no espaço de modelagem. O mecanismo de áudio espacial usa HRTFs personalizadas para expandir a experiência de realidade mista e simular sons que são provenientes de várias instruções e distâncias.

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

As indicações de áudio esquerdo ou direito (azimuth) originam diferenças no tempo de som chega à cada ear. Para cima e para indicações originadas spectral alterações produzidas pela forma outer ear (pinnae). Ao designar onde o áudio vem, o sistema pode simular a experiência de som que chegam em momentos diferentes para nossos ouvidos. Observe que no HoloLens, enquanto o funcionamento de em azimuth é personalizado, a simulação de elevação se baseia em um conjunto de média de anthropometrics. Assim, a precisão de elevação pode ser menos precisa do que a precisão de azimuth.

As características de sons também alterar com base no ambiente no qual elas existem. Por exemplo, shouting em uma caverna fará com que a voz para salte nas paredes, andares e os tetos, criando um efeito de eco. A configuração do modelo de sala de som espacial reproduz esses reflexos para colocar os sons em um ambiente específico de áudio. Você pode usar essa configuração para corresponder ao local real do usuário para a simulação de sons em que o espaço para criar uma experiência mais imersiva de áudio.

## <a name="integrating-spatial-sound"></a>A integração do som espacial

Como o princípio geral de realidade misturada é Terra [hologramas](hologram.md) no mundo físico ou o ambiente virtual do usuário, a maioria dos sons de hologramas devem spatialized. Em HoloLens, há naturalmente CPU e memória orçamento considerações, mas você pode usar 10 a 12 espaciais som vozes lá durante o uso de menos de aproximadamente 12% da CPU (cerca de 70% de um dos quatro núcleos). Uso recomendado de vozes de som espaciais incluem:
* Mantenha o foco usando (realce de objetos, particularmente quando estiver fora do modo de exibição). Quando um holograma precisa de atenção de um usuário, reproduzir um som em que holograma (por exemplo, ter uma casca de dog virtual). Isso ajuda o usuário localize o holograma quando ele não está no modo de exibição.
* Áudio Haptics (áudio reativo para interações touchless). Por exemplo, tocar um som quando o controlador de mão ou movimento do usuário entra e sai do quadro de gesto. Ou reproduzir um som quando o usuário seleciona um holograma.
* Imersão (sons de ambientes em torno do usuário).

Também é importante observar que, embora sons estéreo padrão com som espacial de mesclagem pode ser eficaz na criação de ambientes reais, os sons estéreo devem ser relativamente silencioso deixar espaço para os aspectos sutis de som espacial, como reflexos ( as indicações de distância) que podem ser difíceis de ouvir em um ambiente barulhento.

O mecanismo de som espacial dos Windows só oferece suporte a uma taxa de amostragem de mil 48 para reprodução. A maioria dos middleware, como Unity, automaticamente converter arquivos de som no formato com suporte, mas ao usar APIs de áudio do Windows diretamente por favor, corresponde ao formato do conteúdo para o formato com suporte pelo efeito.

## <a name="see-also"></a>Consulte também
* [MR Spatial 220](holograms-220.md)
* [Som espacial no Unity](spatial-sound-in-unity.md)
* [Som espacial no DirectX](spatial-sound-in-directx.md)
* [Projeto de som espacial](spatial-sound-design.md)

---
title: Visualização da verificação de sala
description: Os aplicativos que exigem dados de mapeamento espacial dependem do dispositivo para coletar automaticamente esses dados ao longo do tempo e entre as sessões, à medida que o usuário explora seu ambiente com o dispositivo ativo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, padrões de aplicativo, design, HoloLens, verificação de sala, mapeamento espacial, reconstrução de superfície, malha
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829909"
---
# <a name="room-scan-visualization"></a>Visualização da verificação de sala

Os aplicativos que exigem dados de mapeamento espacial dependem do dispositivo para coletar automaticamente esses dados ao longo do tempo e entre as sessões, à medida que o usuário explora seu ambiente com o dispositivo ativo. A integridade e a qualidade desses dados dependem de vários fatores, incluindo a quantidade de explorações que o usuário fez, quanto tempo passou desde a exploração e se os objetos como mobília e portas foram movidos desde que o dispositivo examinou a área.

Para garantir dados de mapeamento espacial úteis, os desenvolvedores de aplicativos têm várias opções:
* Conte com o que já pode ter sido coletado. Esses dados podem estar incompletos inicialmente.
* Peça ao usuário para usar o gesto de cair para chegar à página inicial do Windows Mixed Reality e, em seguida, explorar a área que desejam usar para a experiência. Eles podem usar o Air-TAP para confirmar se toda a área necessária é conhecida pelo dispositivo.
* Crie uma experiência de exploração personalizada em seu próprio aplicativo.

Observe que, em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Visualização da verificação de sala</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Criando uma experiência de verificação personalizada

Os aplicativos podem decidir analisar os dados de mapeamento espacial no início da experiência para avaliar se desejam que o usuário execute etapas adicionais para melhorar sua integridade e qualidade. Se a análise indicar que a qualidade deve ser melhorada, os desenvolvedores devem fornecer uma visualização para sobreposição no mundo para indicar:
* Quanto do volume total nos arredores dos usuários precisa fazer parte da experiência
* Onde o usuário deve ir para melhorar os dados

Os usuários não sabem o que faz uma verificação "boa". Eles precisam ser mostrados ou disseram o que procurar se forem solicitados a avaliar uma verificação – Flatness, distância de paredes reais etc. O desenvolvedor deve implementar um loop de comentários que inclua a atualização dos dados de mapeamento espacial durante a fase de verificação ou exploração.

Em muitos casos, pode ser melhor informar ao usuário o que eles precisam fazer (por exemplo, examinar o teto, examinar os móveis) para obter a qualidade de digitalização necessária.

## <a name="cached-versus-continuous-spatial-mapping"></a>Mapeamento espacial em cache versus contínua

Os dados de mapeamento espacial são os aplicativos de fonte de dados de peso mais intenso que podem ser consumidos. Para evitar problemas de desempenho como quadros descartados ou excedentes, o consumo desses dados deve ser feito com cuidado.

A verificação ativa durante uma experiência pode ser benéfica ou prejudicial, e o desenvolvedor precisará decidir qual método usar com base na experiência.

### <a name="cached-spatial-mapping"></a>Mapeamento espacial armazenado em cache

No caso do mapeamento espacial armazenado em cache, o aplicativo normalmente tira um instantâneo dos dados de mapeamento espacial e usa esse instantâneo pela duração da experiência.

**Benefícios**
* Redução da sobrecarga no sistema, enquanto a experiência está em execução levando a uma potência drástica, ganhos térmicos e de desempenho da CPU.
* Uma implementação mais simples da experiência principal, uma vez que ela não é interrompida por alterações nos dados espaciais.
* Um único custo individual em qualquer pós-processamento dos dados espaciais de física, elementos gráficos e outras finalidades.

**Desvantagens**
* A movimentação de objetos do mundo real ou de pessoas não é refletida pelos dados armazenados em cache. Ex. o aplicativo pode considerar uma porta aberta quando está realmente fechado agora.
* Possivelmente mais memória de aplicativo para manter a versão em cache dos dados.

Um bom caso para esse método é um ambiente controlado ou um jogo de topo de tabela.

### <a name="continuous-spatial-mapping"></a>Mapeamento espacial contínuo

Determinados aplicativos podem depender da varredura para atualizar dados de mapeamento espacial.

**Benefícios**
* Você não precisa criar uma experiência separada de verificação ou exploração antecipada em seu aplicativo.
* A movimentação de objetos do mundo real pode ser refletida pelo jogo, embora com algum atraso.

**Desvantagens**
* Maior complexidade na implementação da experiência principal.
* Sobrecarga potencial do processamento adicional para gráfico ou física, pois as alterações precisam ser ingeridas incrementalmente por esses sistemas.
* Maior capacidade, impacto térmico e de CPU.

Um bom caso para esse método é um em que os hologramas são esperados para interagir com a movimentação de objetos, por exemplo, um carro Holographic que as unidades no chão podem desejar aumentar corretamente em uma porta dependendo se ela está aberta ou fechada.

## <a name="see-also"></a>Consulte também
* [Projeto de mapeamento espacial](spatial-mapping-design.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Projeto de som espacial](spatial-sound-design.md)

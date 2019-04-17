---
title: Visualização de verificação de espaço
description: Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, padrões de aplicativo, design, HoloLens, verificação de espaço, espacial de mapeamento, superfície reconstrução, da malha
ms.openlocfilehash: 8ffde9d476e25016f986321377dce8125ee3a596
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590929"
---
# <a name="room-scan-visualization"></a>Visualização de verificação de espaço

Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo. A integridade e a qualidade dos dados depende de vários fatores, incluindo a quantidade de exploração que o usuário tenha feito, quanto tempo se passou desde a exploração e se os objetos como móveis e portas foram movidas desde a área de verificação de dispositivo.

Para garantir que os dados de mapeamento espacial úteis, os desenvolvedores de aplicativos tem várias opções:
* Contar o que talvez já foram coletado. Esses dados podem estar incompletos inicialmente.
* Peça ao usuário para usar o gesto de bloom para obter o Windows Mixed Reality inicial e, em seguida, explore a área que eles desejam usar para a experiência. Eles podem usar o toque de ar para confirmar que toda a área necessária é conhecida para o dispositivo.
* Crie uma experiência de exploração personalizado em seu próprio aplicativo.

Observe que em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> Visualização de verificação de espaço</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Criar uma experiência de verificação personalizada

Aplicativos podem decidir analisar os dados de mapeamento espacial no início da experiência para avaliar se eles desejam que o usuário execute etapas adicionais para melhorar sua integridade e a qualidade. Se a análise indica que deve ser melhor qualidade, os desenvolvedores devem fornecer uma visualização para o mundo para indicar de sobreposição:
* Quanto o volume total nas proximidades usuários precisa fazer parte da experiência do
* Em que o usuário deve ir para melhorar a dados

Os usuários não sabem o que faz uma verificação de "boa". Eles precisam ser mostrado ou informado o que procurar se eles são solicitados para avaliar uma verificação – planeza, distância das paredes reais, etc. O desenvolvedor deve implementar um loop de comentários que inclui a atualização de dados de mapeamento espacial durante a fase de verificação ou exploração.

Em muitos casos, talvez seja melhor informar ao usuário o que precisam (por exemplo, examinar o limite, procure por trás de móveis), para obter a qualidade de verificação necessárias.

## <a name="cached-versus-continuous-spatial-mapping"></a>Armazenados em cache versus contínuo mapeamento espacial

Os dados de mapeamento espacial serão mais pesada aplicativos de fonte de dados podem consumir. Para evitar problemas de desempenho, como quadros ignorados ou falhas, consumo de dados deve ser feito com cuidado.

Verificando ativa durante uma experiência pode ser benéfico ou prejudicial e o desenvolvedor precisará decidir qual método usar com base na experiência.

### <a name="cached-spatial-mapping"></a>Mapeamento espacial em cache

No caso do mapeamento espacial em cache, o aplicativo geralmente tira um instantâneo dos dados de mapeamento espacial e usa esse instantâneo para a duração da experiência.

**Benefícios**
* Redução sobrecarga no sistema enquanto a experiência está em execução líder a enorme potência, térmica e ganhos de desempenho de cpu.
* Uma implementação mais simples da experiência de principal, pois ele não é interrompido por alterações nos dados espaciais.
* Um único custo em qualquer pós-processamento dos dados espaciais para outros fins, gráficos e física de uma vez.

**Desvantagens**
* A movimentação de objetos do mundo real ou pessoas não será refletida pelos dados armazenados em cache. Ex. o aplicativo pode considerar uma porta aberta quando, na verdade, é fechada agora.
* Potencialmente mais memória do aplicativo para manter a versão em cache dos dados.

Um bom caso para esse método é um jogo de tabela superior ou de um ambiente controlado.

### <a name="continuous-spatial-mapping"></a>Mapeamento espacial contínuo

Determinados aplicativos podem se basear em continua a varredura para atualizar os dados de mapeamento espacial.

**Benefícios**
* Você não precisa compilar em uma separada de verificação ou exploração experiência com antecedência em seu aplicativo.
* A movimentação de objetos do mundo real pode ser refletida com o jogo, embora com algum atraso.

**Desvantagens**
* Maior complexidade na implementação da experiência de principal.
* Potencial de sobrecarga do processamento adicional para o elemento gráfico ou física como alterações precisam ser ingeridos incrementalmente por esses sistemas.
* Maior capacidade, térmico e impacto sobre a CPU.

Um bom caso para esse método é que um onde hologramas devem interagir com a movimentação de objetos, por exemplo, um carro holográfico unidades no chão talvez queira corretamente se deparar com uma porta dependendo se ele for aberto ou fechado.

## <a name="see-also"></a>Consulte também
* [Design de mapeamento espacial](spatial-mapping-design.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Design de som espacial](spatial-sound-design.md)

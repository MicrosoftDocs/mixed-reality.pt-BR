---
title: Design de mapeamento espacial
description: O uso efetivo do mapeamento espacial dentro do HoloLens requer uma consideração cuidadosa de muitos fatores.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, mapeamento espacial, HoloLens, reconstrução da superfície, malha
ms.openlocfilehash: 02e64727f9a23bea28e018d7c4e5a8b89c152447
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566013"
---
# <a name="spatial-mapping-design"></a>Design de mapeamento espacial

O uso efetivo do mapeamento espacial dentro do HoloLens requer uma consideração cuidadosa de muitos fatores.

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
        <td>Design de mapeamento espacial</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="why-is-spatial-mapping-important"></a>Por que o mapeamento espacial é importante?

O mapeamento espacial torna possível posicionar objetos em superfícies reais. Isso ajuda a ancorar objetos no mundo do usuário e aproveita as indicações de profundidade do mundo real. Occluding seus hologramas com base em outros hologramas e objetos do mundo real ajudam a convencer o usuário de que esses hologramas estão na verdade em seu espaço. Os hologramas flutuam no espaço ou quando se movem com o usuário não se sentirão reais. Quando possível, coloque os itens em conforto.

Visualize superfícies ao colocar ou mover hologramas (use uma grade projetada simples). Isso ajudará o usuário a saber onde eles podem posicionar melhor seus hologramas e mostrará o usuário se o ponto em que eles estão tentando posicionar o holograma ainda não tiver sido mapeado. Você pode "itens do mural" em direção ao usuário se eles acabarem em muito um ângulo.

## <a name="what-influences-spatial-mapping-quality"></a>O que influencia a qualidade do mapeamento espacial?

Vários fatores, detalhados [aqui](environment-considerations-for-hololens.md), podem afetar a frequência e a severidade desses erros.  No entanto, você deve projetar seu aplicativo para que o usuário possa atingir suas metas mesmo na presença de erros nos dados de mapeamento espacial.

## <a name="the-environment-scanning-experience"></a>A experiência de verificação do ambiente

Cada aplicativo que usa o mapeamento espacial deve considerar a possibilidade de fornecer uma "experiência de verificação"; o processo pelo qual o aplicativo orienta o usuário a verificar as superfícies necessárias para que o aplicativo funcione corretamente.

![Exemplo de verificação](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Exemplo de verificação*

A natureza dessa experiência de verificação pode variar muito dependendo das necessidades de cada aplicativo, mas dois princípios principais devem guiar seu design.

Em primeiro lugar, **a comunicação clara com o usuário é a principal preocupação**. O usuário deve estar sempre atento se os requisitos do aplicativo estão sendo atendidos. Quando eles não estão sendo atendidos, deve ser imediatamente claro para o usuário por que isso é feito e eles devem ser rapidamente administrados para executar a ação apropriada.

Em segundo lugar, **os aplicativos devem tentar um equilíbrio entre a eficiência e a confiabilidade**. Quando é possível fazer isso de forma **confiável**, os aplicativos devem analisar automaticamente os dados de mapeamento espacial para salvar a hora do usuário. Quando não é possível fazer isso de forma confiável, os aplicativos devem permitir que o usuário forneça rapidamente ao aplicativo as informações adicionais necessárias.

Para ajudar a criar a experiência de verificação correta, considere quais das seguintes possibilidades são aplicáveis ao seu aplicativo:

* **Nenhuma experiência de verificação**
   * Um aplicativo pode funcionar perfeitamente sem nenhuma experiência de verificação guiada; Ele aprenderá sobre as superfícies observadas no decorrer do movimento de usuário natural.
   * Por exemplo, um aplicativo que permite que o usuário desenhe superfícies com tinta de irrigação Holographic requer conhecimento apenas das superfícies visíveis no momento para o usuário.
   * O ambiente pode ser completamente verificado, já que é aquele em que o usuário já gastou muito tempo usando o HoloLens.
   * No entanto, lembre-se de que a câmera usada pelo mapeamento espacial só pode ver 3,1 m na frente do usuário, portanto, o mapeamento espacial não saberá sobre nenhuma superfície mais distante, a menos que o usuário as tenha observado de uma distância mais próxima no passado.
   * Portanto, o usuário entende quais superfícies foram verificadas, o aplicativo deve fornecer comentários visuais para esse efeito, por exemplo, converter sombras virtuais em superfícies digitalizadas pode ajudar o usuário a posicionar os hologramas nessas superfícies.
   * Nesse caso, os volumes delimitados do observador de superfície espacial devem ser atualizados cada quadro para um [sistema de coordenadas espaciais](coordinate-systems.md)bloqueadas pelo corpo, para que eles sigam o usuário.

* **Encontrar um local adequado**
   * Um aplicativo pode ser projetado para uso em um local com requisitos específicos.
   * Por exemplo, o aplicativo pode exigir uma área vazia em todo o usuário para que possa praticar com segurança Holographic Kung-Fu.
   * Os aplicativos devem comunicar quaisquer requisitos específicos para o usuário antes e reforce-los com comentários visuais claros.
   * Neste exemplo, o aplicativo deve Visualizar a extensão da área vazia necessária e realçar visualmente a presença de qualquer objeto indesejado nessa zona.
   * Para esse caso, os volumes delimitados do observador de superfície espacial devem usar um [sistema de coordenadas espaciais](coordinate-systems.md) bloqueados pelo mundo no local escolhido.

* **Encontre uma configuração adequada de superfícies**
   * Um aplicativo pode exigir uma configuração específica de superfícies, por exemplo, duas paredes grandes e simples e opostas para criar um Holographic Hall de espelhos.
   * Nesses casos, o aplicativo precisará analisar as superfícies fornecidas pelo mapeamento espacial para detectar superfícies adequadas e direcionar o usuário para eles.
   * O usuário deverá ter uma opção de fallback se a análise da superfície do aplicativo não for totalmente confiável. Por exemplo, se o aplicativo identificar incorretamente um porta como uma parede simples, o usuário precisará de uma maneira simples de corrigir esse erro.

* **Examinar parte do ambiente**
   * Um aplicativo pode desejar capturar apenas parte do ambiente, conforme indicado pelo usuário.
   * Por exemplo, o aplicativo examina parte de uma sala para que o usuário possa postar um anúncio Holographic classificado para móveis que desejam vender.
   * Nesse caso, o aplicativo deve capturar dados de mapeamento espacial dentro das regiões observadas pelo usuário durante a verificação.

* **Verificar a sala inteira**
   * Um aplicativo pode exigir uma verificação de todas as superfícies no espaço atual, incluindo aquelas por trás do usuário.
   * Por exemplo, um jogo pode colocar o usuário na função de Gulliver, sob o Siege de centenas de pequenas Lilliputians abordagens de todas as direções.
   * Nesses casos, o aplicativo precisará determinar quantas superfícies na sala atual já foram verificadas e direcionar o olhar do usuário para preencher lacunas significativas.
   * A chave para esse processo é fornecer comentários visuais que o tornam claro para o usuário quais superfícies ainda não foram verificadas. O aplicativo poderia, por exemplo, usar a [neblina baseada em distância](https://msdn.microsoft.com/library/windows/desktop/bb173401%28v=vs.85%29.aspx) para realçar visualmente as regiões que não são cobertas por superfícies de mapeamento espacial.

* **Tirar um instantâneo inicial do ambiente**
   * Um aplicativo pode desejar ignorar todas as alterações no ambiente depois de usar um ' instantâneo ' inicial.
   * Isso pode ser apropriado para evitar a interrupção de dados criados pelo usuário que estejam rigidamente acoplados ao estado inicial do ambiente.
   * Nesse caso, o aplicativo deve fazer uma cópia dos dados de mapeamento espacial em seu estado inicial quando a verificação for concluída.
   * Os aplicativos devem continuar recebendo atualizações para dados de mapeamento espacial se os hologramas ainda estiverem obstruídodos corretamente pelo ambiente.
   * Atualizações continuadas para dados de mapeamento espacial também permitem visualizar todas as alterações que ocorreram, esclarecendo ao usuário as diferenças entre os Estados anterior e o presente do ambiente.

* **Fazer instantâneos iniciados pelo usuário do ambiente**
   * Um aplicativo pode querer responder apenas a alterações ambientais quando instruído pelo usuário.
   * Por exemplo, o usuário poderia criar várias ' Statues ' 3D de um amigo capturando suas poses em momentos diferentes.

* **Permitir que o usuário altere o ambiente**
   * Um aplicativo pode ser projetado para responder em tempo real a qualquer alteração feita no ambiente do usuário.
   * Por exemplo, o usuário que desenha um Curtain poderia disparar a "mudança de cena" para uma reprodução de Holographic em andamento no outro lado.

* **Orientar o usuário para evitar erros nos dados de mapeamento espacial**
   * Um aplicativo pode desejar fornecer orientações ao usuário enquanto eles estão verificando seu ambiente.
   * Isso pode ajudar o usuário a evitar determinados tipos de [erros nos dados de mapeamento espacial](spatial-mapping-design.md#what-influences-spatial-mapping-quality), por exemplo, mantendo-se afastados das janelas sunlit ou dos espelhos.

Um detalhe adicional a ser considerado é que o ' intervalo ' de dados de mapeamento espacial não é ilimitado. Apesar de o mapeamento espacial criar um banco de dados permanente de espaços grandes, ele disponibiliza apenas os dados para os aplicativos em uma "bolha" de tamanho limitado em relação ao usuário. Portanto, se você começar no início de um longo corredor e ir longe o suficiente do início, eventualmente as superfícies espaciais no início desaparecerão. É claro que você pode reduzir isso armazenando em cache essas superfícies em seu aplicativo depois que elas desaparecerem dos dados de mapeamento espacial disponíveis.

## <a name="mesh-processing"></a>Processamento de malha

Pode ajudar a detectar tipos comuns de erros em superfícies e filtrar, remover ou modificar os dados de mapeamento espacial conforme apropriado.

Tenha em mente que os dados de mapeamento espacial devem ser tão fiels quanto possível para superfícies reais, de modo que qualquer processamento que você aplique riscos mudará suas superfícies além da ' verdade '.

Aqui estão alguns exemplos de diferentes tipos de processamento de malha que podem ser úteis:

* **Preenchimento de orifício**
   * Se um pequeno objeto formado por um material escuro falhar ao digitalizar, ele deixará um orifício na superfície ao redor.
   * Os buracos afetam o oclusão: os hologramas podem ser vistos "por meio de um buraco em uma superfície do mundo real opaca supostamente.
   * Os buracos afetam o raycasts: se você estiver usando o raycasts para ajudar os usuários a interagir com as superfícies, pode ser indesejável que esses raios passem por buracos. Uma mitigação é usar um pacote de vários raycasts cobrindo uma região de tamanho adequado. Isso permitirá que você filtre os resultados de "exceção", de modo que, mesmo que um Raycast passe por uma pequena brecha, o resultado da agregação ainda será válido. No entanto, lembre-se de que essa abordagem vem com um custo computacional.
   * Os buracos afetam as colisões de física: um objeto controlado pela simulação física pode derrubar um orifício no chão e se tornar perdido.
   * É possível forma algorítmica o preenchimento desses buracos na malha da superfície. No entanto, você precisará ajustar seu algoritmo para que "buracos reais", como Windows e doorways, não sejam preenchidos. Pode ser difícil diferenciar de forma confiável ' buracos reais ' de ' buracos imaginários ', portanto, você precisará experimentar uma heurística diferente, como ' tamanho ' e ' forma de limite '.

* **Remoção de hallucination**
   * Reflexos, luzes brilhantes e movimentação de objetos podem deixar o ' hallucinations ' remanescente pequeno no ar médio.
   * Hallucinations afeta oclusão: hallucinations pode se tornar visível como formas escuras se movendo na frente e occluding outros hologramas.
   * Hallucinations afeta raycasts: se você estiver usando o raycasts para ajudar os usuários a interagir com superfícies, esses raios poderão atingir um hallucination em vez da superfície por trás dele. Assim como acontece com os buracos, uma mitigação é usar muitas raycasts em vez de um único Raycast, mas novamente isso será fornecido a um custo computacional.
   * Hallucinations afetam as colisões de física: um objeto controlado pela simulação física pode ficar preso contra um hallucination e não pode passar por uma área de espaço aparentemente nítida.
   * É possível filtrar esses hallucinations da malha de superfície. No entanto, assim como com os buracos, você precisará ajustar seu algoritmo para que os objetos reais pequenos, como a lâmpada e os identificadores de porta, não sejam removidos.

* **Suavização**
   * O mapeamento espacial pode retornar superfícies que parecem ser aproximadas ou "ruidosas" em comparação com suas contrapartes do mundo real.
   * A suavidade afeta as colisões de física: se o piso for aproximado, uma bola de golfe fisicamente simulada poderá não ser organizada sem problemas em uma linha reta.
   * A suavidade afeta a renderização: se uma superfície for visualizada diretamente, os Normals da superfície aproximada poderão afetar sua aparência e interromper uma aparência "limpa". É possível mitigar isso usando a iluminação e texturas apropriadas no sombreador que é usado para renderizar a superfície.
   * É possível suavizar a áspero em uma malha de superfície. No entanto, isso pode empurrar a superfície para longe da superfície real correspondente. Manter uma correspondência próxima é importante para produzir oclusão de holograma precisos e para permitir que os usuários obtenham interações precisas e previsíveis com superfícies holographics.
   * Se apenas uma alteração superficial for necessária, pode ser suficiente para suavizar Normals de vértice sem alterar as posições de vértice.

* **Localização do plano**
   * Há muitas formas de análise que um aplicativo pode desejar executar nas superfícies fornecidas pelo mapeamento espacial.
   * Um exemplo simples é ' Localizar plano '; identificação das regiões de superfícies limitadas e em grande-planar.
   * As regiões planar podem ser usadas como superfícies de trabalho Holographic, regiões em que o conteúdo Holographic pode ser colocado automaticamente pelo aplicativo.
   * As regiões planar podem restringir a interface do usuário, para orientar os usuários a interagir com as superfícies que melhor atendam às suas necessidades.
   * As regiões planar podem ser usadas como no mundo real, para contrapartes Holographic a objetos funcionais, como telas de LCD, tabelas ou quadros de comunicações.
   * As regiões planar podem definir áreas de reprodução, formando a base dos níveis de videogame.
   * As regiões planar podem ajudar os agentes virtuais a navegar pelo mundo real, identificando as áreas de piso que as pessoas realmente têm a probabilidade de acompanhar.

## <a name="prototyping-and-debugging"></a>Protótipo e depuração

### <a name="useful-tools"></a>Ferramentas úteis
* O [emulador do HoloLens](using-the-hololens-emulator.md) pode ser usado para desenvolver aplicativos usando o mapeamento espacial sem acesso a um HoloLens físico. Ele permite simular uma sessão ao vivo em um HoloLens em um ambiente realista, com todos os dados que seu aplicativo normalmente consumiria, incluindo movimento de HoloLens, sistemas de coordenadas espaciais e malhas de mapeamento espacial. Isso pode ser usado para fornecer entradas confiáveis e reproduzíveis, que podem ser úteis para depurar problemas e avaliar alterações em seu código.
* Para reproduzir um cenário, Capture dados de mapeamento espacial pela rede de um HoloLens ao vivo e, em seguida, salve-os no disco e reutilize-os em sessões de depuração subsequentes.
* O [modo de exibição 3D do portal de dispositivo do Windows](using-the-windows-device-portal.md#3d-view) fornece uma maneira de ver todas as superfícies espaciais disponíveis atualmente por meio do sistema de mapeamento espacial. Isso fornece uma base de comparação para as superfícies espaciais dentro de seu aplicativo; por exemplo, você pode identificar facilmente se alguma superfície espacial está ausente ou sendo exibida no local errado.

### <a name="general-prototyping-guidance"></a>Diretrizes gerais de protótipo
* Como os [erros](spatial-mapping-design.md#what-influences-spatial-mapping-quality) nos dados de mapeamento espacial podem afetar seriamente a experiência do usuário, recomendamos que você teste seu aplicativo em uma ampla variedade de ambientes.
* Não se preocupe com o hábito de testar sempre no mesmo local, por exemplo, em sua mesa. Certifique-se de testar várias superfícies de diferentes posições, formas, tamanhos e materiais.
* Da mesma forma, embora os dados sintéticos ou registrados possam ser úteis para depuração, não se tornem muito dependentes dos mesmos casos de teste. Isso pode atrasar a localização de problemas importantes que os testes mais variados teriam detectados anteriormente.
* É uma boa ideia executar testes com usuários reais (e idealmente desconhecidos), pois eles não podem usar o HoloLens ou seu aplicativo exatamente da mesma maneira que você. Na verdade, ele pode surpreender você como o comportamento das pessoas, o conhecimento e as suposições mais divergentes podem ser!

## <a name="see-also"></a>Consulte também
* [Visualização de varredura do ambiente](room-scan-visualization.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Persistência no Unity](persistence-in-unity.md)

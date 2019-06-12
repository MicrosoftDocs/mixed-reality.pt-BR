---
title: Design de mapeamento espacial
description: Uso eficiente do mapeamento espacial dentro do HoloLens requer uma consideração cuidadosa de vários fatores.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Mapeamento de Windows Mixed Reality, design, espacial, HoloLens, surface reconstrução, da malha
ms.openlocfilehash: 451213a79e1d482d64725ce750065611830beec3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829966"
---
# <a name="spatial-mapping-design"></a>Design de mapeamento espacial

Uso eficiente do mapeamento espacial dentro do HoloLens requer uma consideração cuidadosa de vários fatores.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Design de mapeamento espacial</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="why-is-spatial-mapping-important"></a>Por que o mapeamento espacial é importante?

Mapeamento espacial torna possível colocar objetos em superfícies real. Isso ajuda a objetos de âncora no mundo do usuário e se beneficia das indicações de profundidade do mundo real. Occluding seu hologramas com base em outros hologramas e objetos do mundo real ajuda convencer o usuário que esses hologramas estão realmente em seu espaço. Hologramas flutuando no espaço ou movendo-se com o usuário não se sinta como real. Quando possível, coloque itens de conforto.

Visualize as superfícies ao colocar ou mover hologramas (usar uma grade projetada simple). Isso ajudará o usuário saiba onde melhor pode colocar suas hologramas e mostra que o usuário se o ponto em que eles estão tentando colocar o holograma ainda não foram mapeado. Você pode "de mensagem de itens" em direção ao usuário se eles terminam no muito de um ângulo.

## <a name="what-influences-spatial-mapping-quality"></a>O que influencia a qualidade de mapeamento espacial?

Para fornecer a melhor experiência de usuário, é importante entender os fatores que afetam a qualidade dos dados de mapeamento espacial coletados pelo HoloLens.

Erros em dados de mapeamento espacial se enquadram em uma das três categorias:
* **Buracos**: As superfícies do mundo real estão ausentes dos dados de mapeamento espacial.
* **Hallucinations**: Superfícies existem nos dados de mapeamento espacial que não existem no mundo real.
* **Tendência**: Superfícies nos dados de mapeamento espacial modo imperfeito são alinhadas com as superfícies de mundo real, seja enviada por push ou retirar as.

Vários fatores podem afetar a frequência e a gravidade desses erros:

* **Movimento de usuário**
   * Como o usuário se move pelo seu ambiente determina quão bem o ambiente será verificado, o usuário poderá exigir orientações para alcançar uma verificação de boa.
   * Câmera usada para verificação fornece os dados dentro de um cone de 70 graus, entre o mínimo de 0,8 metros a um máximo de 3.1 metros de distância da câmera. As superfícies do mundo real serão verificadas apenas dentro este campo de visão. Observe que esses valores estão sujeitos a alterações em versões futuras.
   * Se o usuário nunca dentro 3.1 medidores de um objeto, em seguida, ele não será verificado.
   * Se o usuário exibe somente um objeto de uma distância de menos de 0,8 metros, não serão verificado (Isso evita a verificação de mãos do usuário).
   * Se o usuário nunca olhar para cima (que é bastante normal), em seguida, o teto provavelmente não será verificado.
   * Se um usuário nunca procura por trás mobiliário ou uma parede os objetos obstruídos por eles não serão verificados.
   * Superfícies tendem a ser verificado com melhor qualidade quando eles são exibidos frente, em vez de em um ângulo superficial.
   * Se o sistema de controle de cabeçalho do HoloLens momentaneamente falhar (que pode acontecer devido ao movimento de usuário rápida, iluminação ruim, paredes featureless ou câmeras se tornando coberto), isso pode introduzir erros nos dados espaciais de mapeamento. Esses erros serão corrigidos ao longo do tempo conforme o usuário continua a mover-se e verificar seu ambiente.

* **Materiais de superfície**
   * Os materiais encontrados em superfícies reais variam muito. Elas afetam a qualidade dos dados porque elas afetam a luz como infravermelho são refletidos de mapeamento espacial.
   * Superfícies escuras não podem verificar até que eles se aproximarem da câmera, porque elas refletem menos luz.
   * Alguns superfícies talvez-escuras que eles refletem luz muito pouco a ser verificado de qualquer distância, para que eles apresentará erros buraco no local da superfície e, às vezes, também por trás da superfície de.
   * Superfícies brilhantes particularmente podem verificar somente quando visualizado em frente e não quando visualizado em um ângulo superficial.
   * Espelhos, pois elas criam illusory reflexos de espaços real e superfícies, podem causar erros de buraco e erros hallucination.

* **Movimento de cena**
   * Mapeamento espacial adapta-se rapidamente às mudanças no ambiente, como mover as pessoas ou abrindo e fechando portas.
   * No entanto, mapeamento espacial só pode adaptar a alterações em uma área quando nessa área é claramente visível para a câmera é usada para verificação.
   * Por isso, é possível que essa adaptação atrasar a realidade, o que pode causar erros de falha ou hallucination.
   * Por exemplo, um usuário examina um amigo e os transforma em torno de enquanto o amigo deixa a sala. Uma representação de 'ghost' do amigo (um erro de hallucination) será mantido nos dados de mapeamento espacial, até que o usuário ativa novamente ao redor e examina novamente o espaço em que o amigo apoiava.

* **Interferência de iluminação**
   * Luz ambiente de infravermelho na cena pode interferir com a varredura, por exemplo forte luz do sol recebidas por meio de uma janela.
   * Superfícies brilhantes particularmente podem interferir com a varredura de superfícies próximas, a luz saltando off-las causando erros de ajuste.
   * Superfícies brilhantes refletir a luz diretamente volta para a câmera podem interferir com o próximo espaço, fazendo com que flutuante hallucinations de ar intermediário ou atrasando adaptação ao movimento da cena.
   * Dois dispositivos HoloLens na mesma sala não devem interferir uns com os outros, mas a presença de mais de cinco dispositivos HoloLens pode causar interferências.

É possível evitar ou corrigir alguns desses erros. No entanto, você deve projetar seu aplicativo para que o usuário seja capaz de alcançar suas metas, mesmo na presença de erros nos dados de mapeamento espacial.

## <a name="the-environment-scanning-experience"></a>O ambiente de experiência de verificação

HoloLens aprende sobre as superfícies em seu ambiente, conforme o usuário levar analisando-os. Ao longo do tempo, o HoloLens cria uma verificação de todas as partes do ambiente que foram observados. Ele também atualiza a verificação como alterações no ambiente são observadas. Essa verificação será mantido automaticamente entre o aplicativo é iniciado.

Cada aplicativo que usa o mapeamento espacial deve considerar a fornecer uma "experiência de verificação;' o processo por meio do qual o aplicativo orienta o usuário para verificar as superfícies que são necessárias para o aplicativo funcione corretamente.

![Exemplo de verificação](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Exemplo de verificação*

A natureza dessa experiência de verificação pode variar consideravelmente dependendo das necessidades de cada aplicativo, mas os dois principais princípios devem orientar seu design.

Em primeiro lugar, **clara comunicação com o usuário é a principal preocupação**. O usuário deve estar ciente de que se os requisitos do aplicativo estão sendo atendidos. Quando eles não estão sendo atendidos, deve ficar claro imediatamente para o usuário porque este é o caso e deve ser levados rapidamente para tomar as devidas providências.

Em segundo lugar, **aplicativos devem tentar obter um equilíbrio entre a eficiência e confiabilidade**. Quando é possível fazer isso **confiável**, aplicativos automaticamente devem analisar os dados de mapeamento espacial para economizar o tempo do usuário. Quando não é possível fazer isso de forma confiável, aplicativos em vez disso, devem permitir que o usuário forneça rapidamente o aplicativo com as informações adicionais necessárias.

Para ajudar o direito de experiência de verificação de design, considere qual das seguintes possibilidades são aplicáveis ao seu aplicativo:

* **Nenhuma experiência de verificação**
   * Um aplicativo pode funcionar perfeitamente, sem qualquer experiência interativa de verificação; ele irá aprender sobre as superfícies que são observadas no decorrer de movimento natural do usuário.
   * Por exemplo, um aplicativo que permite que o usuário desenhar em superfícies com spraypaint holográfica requer conhecimento somente de superfícies visíveis no momento para o usuário.
   * O ambiente pode ser examinado completamente já se ele for um no qual o usuário já passou muito tempo usando o HoloLens.
   * Tenha em mente entretanto que a câmera usada pelo mapeamento espacial só poderá ver 3.1m na frente do usuário, para que o mapeamento espacial não saberá sobre qualquer superfícies mais distantes, a menos que o usuário tem observá-los à distância mais próxima no passado.
   * Para que ele entende que cobrem foram verificados, o aplicativo deve fornecer comentários visuais para esse efeito, por exemplo, conversão sombras virtuais em superfícies digitalizadas pode ajudar o usuário colocar hologramas dessas superfícies.
   * Nesse caso, os volumes do observador de superfície espacial delimitador devem ser atualizado de cada quadro para um corpo bloqueado [sistema de coordenadas espacial](coordinate-systems.md), de modo que eles seguem o usuário.

* **Encontre um local adequado**
   * Um aplicativo pode ser projetado para uso em um local com requisitos específicos.
   * Por exemplo, o aplicativo pode exigir uma área vazia em torno do usuário para que eles podem praticar com segurança mais Feroz holográfica.
   * Aplicativos devem se comunicar os requisitos específicos para o usuário inicial e reforçá-los com o feedback visual.
   * Neste exemplo, o aplicativo deverá visualizar a extensão da área vazia necessária e destacar visualmente a presença de qualquer objeto indesejada dentro dessa zona.
   * Para esse caso, os volumes do observador de superfície espacial delimitadora devem usar um mundo bloqueado [sistema de coordenadas espacial](coordinate-systems.md) no local escolhido.

* **Localizar uma configuração adequada de superfícies**
   * Um aplicativo pode exigir uma configuração específica de superfícies, por exemplo dois grandes, simples, opostos paredes para criar uma sala holográfica de espelhos.
   * Nesses casos, o aplicativo precisará analisar as superfícies de fornecido pelo mapeamento espacial para detectar superfícies adequadas e direcionar o usuário em direção a eles.
   * O usuário deve ter uma opção de fallback se a análise da superfície do aplicativo não é totalmente confiável. Por exemplo, se o aplicativo identifica incorretamente uma porta de entrada como uma parede simples, o usuário precisa de uma maneira simples de corrigir esse erro.

* **Verificar a parte do ambiente**
   * Um aplicativo talvez queira capturar somente a parte do ambiente, conforme indicado pelo usuário.
   * Por exemplo, o aplicativo examina a parte de um espaço para que o usuário pode lançar um holográfico classificados para móveis que desejam vender.
   * Nesse caso, o aplicativo deve capturar dados de mapeamento espacial dentro de regiões observados pelo usuário durante sua verificação.

* **Verificar o espaço inteiro**
   * Um aplicativo pode exigir uma verificação de todas as superfícies da sala atual, incluindo aqueles por trás do usuário.
   * Por exemplo, um jogo pode colocar o usuário na função de Gulliver, cerco de centenas de pequenos Lilliputians se aproximando de todas as direções.
   * Nesses casos, o aplicativo precisará determinar o espaço disponível para quantos de superfícies atual já foram examinados e direcionar olhar do usuário para preencher lacunas significativas.
   * A chave para esse processo é fornecer comentários visuais que deixa claro para o usuário que cobrem ainda não foram verificados. O aplicativo pode usar por exemplo [com base em distância Névoa](https://msdn.microsoft.com/library/windows/desktop/bb173401%28v=vs.85%29.aspx) para destacar visualmente regiões que não são cobertas por superfícies de mapeamento espacial.

* **Crie um instantâneo inicial do ambiente**
   * Um aplicativo pode querer ignorar todas as alterações no ambiente depois de tirar um inicial 'snapshot'.
   * Isso pode ser apropriado para evitar a interrupção de dados criados pelo usuário que está intimamente ligados ao estado inicial do ambiente.
   * Nesse caso, o aplicativo deve fazer uma cópia dos dados de mapeamento espacial em seu estado inicial após a verificação for concluída.
   * Aplicativos devem continuar recebendo atualizações aos dados de mapeamento espacial se hologramas ainda devem ser corretamente obstruídos pelo ambiente.
   * Atualizações contínuas para dados de mapeamento espacial também permitem visualizar as alterações que ocorreram, esclarecendo ao usuário as diferenças entre os estados anteriores e presentes do ambiente.

* **Tirar instantâneos iniciada pelo usuário do ambiente**
   * Um aplicativo só poderá responder a alterações ambientais quando instruído pelo usuário.
   * Por exemplo, o usuário poderia criar vários 3D statues de um amigo, capturando seus poses em momentos diferentes.

* **Permitir que o usuário altere o ambiente**
   * Um aplicativo pode ser projetado para responder em tempo real para todas as alterações feitas no ambiente do usuário.
   * Por exemplo, o usuário uma cortina de desenho pode disparar 'alteração de cena' para um play holográfica estão ocorrendo no outro lado.

* **Guia do usuário para evitar erros nos dados de mapeamento espacial**
   * Um aplicativo talvez queira fornecer orientação para o usuário enquanto eles estiver verificando seu ambiente.
   * Isso pode ajudar o usuário para evitar determinados tipos de [erros nos dados de mapeamento espacial](spatial-mapping-design.md#what-influences-spatial-mapping-quality), por exemplo, manter-se para fora do windows sunlit ou espelhos.

Um detalhe adicional estar atento é que 'range' de dados de mapeamento espacial não é ilimitado. Durante o mapeamento espacial criar um banco de dados permanente de grandes espaços, ele apenas torna os dados disponíveis para aplicativos em uma bolha' ' tamanho limitado em torno do usuário. Portanto, se você começa do início de um longo caminhar e exame de longe o suficiente para longe de início, eventualmente as superfícies espaciais início desaparecerá. É claro, você pode mitigar isso ao armazenar em cache esses superfícies em seu aplicativo depois que eles desapareceram dos dados de mapeamento espacial disponível.

## <a name="mesh-processing"></a>Processamento de malha

Talvez seja útil para detectar tipos comuns de erros em superfícies e filtrar, remover ou modificar os dados de mapeamento espacial conforme apropriado.

Tenha em mente que esse mapeamento espacial dados deve ser tão fiel possível superfícies do mundo real, para qualquer processamento que você aplicar os riscos de mudança de suas superfícies mais longe da verdade.

Aqui estão alguns exemplos de diferentes tipos de processamento de malha que podem ser úteis:

* **Preenchimento de buraco**
   * Se um objeto pequeno feito de um material escuro ocorra falha na verificação, ele deixará um buraco na superfície de ao redor.
   * Buracos afetam oclusão: hologramas podem ser vistas 'por meio de' um buraco em uma superfície supostamente opaco do mundo real.
   * Buracos afetam raycasts: se você estiver usando raycasts para ajudar os usuários interagem com superfícies, ele pode ser indesejável para esses raios passar através de falhas. Uma mitigação é usar um pacote de vários raycasts que abrangem uma região dimensionada adequadamente. Isso permitirá que você filtre os resultados de 'exceções', para que, mesmo se um raycast passa por um pequeno orifício, o resultado da agregação ainda serão válido. No entanto, lembre-se de que essa abordagem tem um custo computacional.
   * Buracos afetam as colisões de física: um objeto controlado pela simulação de física pode remover por meio de um buraco no chão e se percam.
   * É possível algoritmicamente preencher esses buracos na malha superfície. No entanto, você precisará ajustar seu algoritmo para que 'buracos real' como o windows e entradas de acesso não são preenchidos. Pode ser difícil diferenciar confiável 'brechas real' de 'imaginários buracos', portanto, você precisará experimentar diferente heurística, como o 'Tamanho' e 'forma limite'.

* **Remoção de hallucination**
   * Reflexos, luzes brilhantes e movimentação de objetos pode deixar o pequeno remanescentes 'hallucinations' flutuando no ar intermediário.
   * Hallucinations afetam oclusão: hallucinations podem se tornar visíveis como formas escuras movendo na frente do e occluding outras hologramas.
   * Hallucinations afetam raycasts: se você estiver usando raycasts para ajudar os usuários interagem com superfícies, esses raios conseguiram acertar um hallucination em vez da superfície por trás dele. Assim como acontece com falhas, uma mitigação é usar muitas raycasts em vez de um único raycast mas, novamente, ele será recebido por um custo computacional.
   * Hallucinations afetam colisões de física: um objeto controlado pela simulação de física pode ficar preso em relação a um hallucination e ser possível mover através de uma área aparentemente clara de espaço.
   * É possível filtrar esses hallucinations da malha superfície. No entanto, assim como acontece com falhas, você precisará ajustar seu algoritmo para que real pequenos objetos, como lamp significa e identificadores de porta não foram removidas.

* **Suavização**
   * Mapeamento espacial pode retornar as superfícies que parecem ser aproximada ou ruídos em comparação com suas contrapartes do mundo real.
   * Suavidade afeta as colisões de física: se o chão é aproximado, uma bola de Golfe fisicamente simulado pode não são transferidas suavemente por ele em uma linha reta.
   * Suavidade afeta a renderização: se uma superfície é visualizada diretamente, normais da superfície aproximadas podem afetar sua aparência e interromper uma aparência 'limpa'. É possível atenuar isso por meio de iluminação apropriada e texturas no sombreador que é usado para renderizar a superfície.
   * É possível suavizar Aspereza em uma malha de superfície. No entanto, isso pode enviar por push a superfície para fora da superfície do mundo real correspondente. Manter uma correspondência de fechamento é importante para produzir oclusão holograma precisos e permitir que os usuários alcançar interações precisas e previsíveis com superfícies holográfica.
   * Se apenas uma alteração superficial for necessária, ela pode ser suficiente suavizar normais de vértice sem alterar as posições de vértice.

* **Localização do plano**
   * Há muitas formas de análise que um aplicativo talvez queira executar nas superfícies de fornecido pelo mapeamento espacial.
   * Um exemplo simple é 'Localização do plano'; Identificando limitadas, principalmente planar regiões de superfícies.
   * Planares regiões podem ser usados como holográfica-as superfícies de trabalho, regiões onde holográfico conteúdo pode ser colocado automaticamente pelo aplicativo.
   * Regiões planares podem restringir a interface do usuário, orientar os usuários a interagir com as superfícies que melhor se adequar às suas necessidades.
   * Planares regiões podem ser usados como no mundo real, para contrapartes holographic para objetos funcionais, como telas de LCD, tabelas ou quadros de comunicações.
   * Planares regiões podem definir áreas play, formando a base dos níveis de videogame.
   * Planares regiões podem ajudar a virtuais agentes para navegar no mundo real, por meio da identificação de áreas de piso que provavelmente as pessoas reais para guiá-lo no.

## <a name="prototyping-and-debugging"></a>Criação de protótipos e depuração

### <a name="useful-tools"></a>Ferramentas úteis
* O [HoloLens emulador](using-the-hololens-emulator.md) pode ser usado para desenvolver aplicativos usando o mapeamento espacial sem acesso a um HoloLens físico. Ele permite que você simule uma sessão ao vivo em um HoloLens em um ambiente realista, com todos os dados de seu aplicativo normalmente consumiria, incluindo HoloLens movimento, sistemas de coordenadas espaciais e mapeamento espacial malhas. Isso pode ser usado para fornecer entrada confiável, repetível, que pode ser útil para depuração de problemas e avaliar as alterações ao seu código.
* Para reproduzir um cenários, capturar dados de mapeamento espacial pela rede a partir de um HoloLens ao vivo e, em seguida, salvá-lo para o disco e reutilizá-la nas sessões subsequentes de depuração.
* O [exibição 3D do Windows dispositivo portal](using-the-windows-device-portal.md#3d-view) fornece uma maneira de ver todas as superfícies espaciais está disponíveis por meio do sistema de mapeamento espacial. Isso fornece uma base de comparação para as superfícies espaciais dentro de seu aplicativo. Por exemplo, você pode perceber facilmente se qualquer superfícies espaciais estão falta ou estão sendo exibidas no lugar errado.

### <a name="general-prototyping-guidance"></a>Diretrizes gerais de criação de protótipos
* Porque [erros](spatial-mapping-design.md#what-influences-spatial-mapping-quality) no mapeamento espacial dados fortemente podem afetar a experiência do usuário, é recomendável que você teste seu aplicativo em uma ampla variedade de ambientes.
* Não obter interceptadas o hábito de sempre testando no mesmo local, por exemplo, em sua mesa. Certifique-se de testar em várias superfícies de posições diferentes, formas, tamanhos e materiais.
* Da mesma forma, enquanto dados sintéticos ou gravados podem ser útil para depuração, não se tornam muito depende do mesmos poucos casos de teste. Isso pode atrasar a localizar problemas importantes que mais testes variado seriam ter capturada anteriormente.
* É uma boa ideia para executar o teste com usuários reais (e o ideal é que não coached), pois eles não podem usar o HoloLens ou seu aplicativo exatamente da mesma maneira que você faz. Na verdade, talvez você se surpreenda comportamento das pessoas como divergentes, suposições e dados de Conhecimento podem ser!

## <a name="see-also"></a>Consulte também
* [Visualização de varredura do ambiente](room-scan-visualization.md)
* [Projeto de som espacial](spatial-sound-design.md)
* [Persistência no Unity](persistence-in-unity.md)

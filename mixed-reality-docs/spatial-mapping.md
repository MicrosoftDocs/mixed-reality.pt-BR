---
title: Mapeamento espacial
description: O mapeamento espacial fornece uma representação detalhada das superfícies do mundo real no ambiente em volta do HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: mapeamento espacial, HoloLens, realidade misturada, reconstrução de superfície, malha, Sr
ms.openlocfilehash: 4914cf5b7864ecb2430a39af73729eb6dfc0e2bd
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937065"
---
# <a name="spatial-mapping"></a>Mapeamento espacial

O mapeamento espacial fornece uma representação detalhada das superfícies do mundo real no ambiente em todo o HoloLens, permitindo que os desenvolvedores criem uma experiência de realidade misturada convincente. Ao mesclar o mundo real com o mundo virtual, um aplicativo pode fazer com que os hologramas pareçam reais. Os aplicativos também podem se alinhar naturalmente com as expectativas do usuário, fornecendo comportamentos e interações do mundo real.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Mapeamento espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="conceptual-overview"></a>Visão geral conceitual

![Superfícies de malha que abrangem uma sala](images/SurfaceReconstruction.jpg)<br>
*Um exemplo de uma malha de mapeamento espacial que abrange uma sala*

Os dois tipos de objeto primários usados para o mapeamento espacial são o ' observador de superfície espacial ' e a ' superfície espacial '.

O aplicativo fornece o observador de superfície espacial com um ou mais volumes delimitadores para definir as regiões de espaço em que o aplicativo deseja receber dados de mapeamento espacial. Para cada um desses volumes, o mapeamento espacial fornecerá ao aplicativo um conjunto de superfícies espaciais.

Esses volumes podem ser fixos (em um local fixo em relação ao mundo real) ou podem ser anexados ao HoloLens (eles se movem, mas não giram, com o HoloLens à medida que se movem pelo ambiente). Cada superfície espacial descreve as superfícies do mundo real em um pequeno volume de espaço, representado como uma malha de triângulo anexada a um [sistema de coordenadas espaciais](coordinate-systems.md)bloqueados pelo mundo.

Como o HoloLens reúne novos dados sobre o ambiente e, conforme ocorrem alterações no ambiente, as superfícies espaciais aparecerão, desaparecerão e serão alteradas.

## <a name="common-usage-scenarios"></a>Cenários de uso comuns

![Ilustrações de cenários de uso de mapeamento espacial comum: Posicionamento, oclusão, física e navegação](images/sm-concepts-1000px.png)

### <a name="placement"></a>Colocação

O mapeamento espacial fornece aos aplicativos a oportunidade de apresentar formas naturais e familiares de interação para o usuário; o que poderia ser mais natural do que colocar seu telefone na mesa?

Restringir o posicionamento de hologramas (ou mais geralmente, qualquer seleção de locais espaciais) para se situar em superfícies fornece um mapeamento natural de 3D (ponto no espaço) para 2D (ponto na superfície). Isso reduz a quantidade de informações que o usuário precisa fornecer ao aplicativo e, portanto, torna as interações do usuário mais rápidas, fáceis e mais precisas. Isso é particularmente verdadeiro porque a ' distância ' distante ' não é algo que estamos acostumados a se comunicar fisicamente com outras pessoas ou computadores. Quando apontamos para o dedo, estamos especificando uma direção, mas não uma distância.

Uma limitação importante aqui é que, quando um aplicativo infere distância da direção (por exemplo, executando um Raycast ao longo da direção do olhar do usuário para encontrar a superfície espacial mais próxima), isso deve produzir resultados que o usuário é capaz de prever de forma confiável. Caso contrário, o usuário perderá sua noção de controle e isso pode rapidamente se tornar frustrante. Um método que ajuda com isso é executar vários raycasts em vez de apenas um. Os resultados agregados devem ser mais suaves e mais previsíveis, menos suscetíveis a influenciar de resultados transitórios "de exceção" (como pode ser causado por raios que passam por pequenos orifícios ou atingindo pequenos bits de geometria que o usuário não está ciente). A agregação ou a suavização também pode ser executada ao longo do tempo; por exemplo, você pode limitar a velocidade máxima na qual um holograma pode variar em distância do usuário. Simplesmente limitar o valor de distância mínimo e máximo também pode ajudar, de modo que o holograma que está sendo movido não acabe repentinamente na distância ou venha a falhar novamente na face do usuário.

Os aplicativos também podem usar a forma e a direção das superfícies para orientar o posicionamento do holograma. Uma cadeira Holographic não deve penetrar em paredes e deve ficar com o andar, mesmo se for um pouco desigual. Esse tipo de funcionalidade provavelmente dependeria do uso de colisões de física em vez de apenas raycasts, mas preocupações semelhantes serão aplicadas. Se o holograma que está sendo posicionado tiver muitos polígonos pequenos que se destinam, como os lados de uma cadeira, pode fazer sentido expandir a representação física desses polígonos para algo mais largo e suave, para que eles possam deslizar por superfícies espaciais sem realce em captura.

Em seu extremo, a entrada do usuário pode ser simplificada de maneira totalmente e as superfícies espaciais podem ser usadas para executar o posicionamento totalmente automático do holograma. Por exemplo, o aplicativo poderia fazer um interruptor de Holographic em algum lugar na parede para que o usuário pressione. A mesma limitação sobre previsibilidade se aplica duplamente; Se o usuário espera o controle sobre o posicionamento do holograma, mas o aplicativo nem sempre coloca os hologramas onde eles esperam (se a opção de luz aparecer em algum lugar que o usuário não consegue alcançar), essa será uma experiência frustrante. Na verdade, pode ser pior executar o posicionamento automático que exige a correção do usuário, em vez de exigir que o usuário sempre execute o mesmo posicionamento; como *espera*-se um posicionamento automático bem-sucedido, a correção manual parece ser um fardo!

Observe também que a capacidade de um aplicativo de usar superfícies espaciais para posicionamento depende muito da experiência de [verificação](spatial-mapping-design.md#the-environment-scanning-experience)do aplicativo. Se uma superfície não tiver sido verificada, ela não poderá ser usada para posicionamento. Cabe ao aplicativo ficar claro para o usuário, para que eles possam ajudar a examinar novas superfícies ou selecionar um novo local.

Os comentários visuais para o usuário são de extrema importância durante o posicionamento. O usuário precisa saber onde o holograma está em relação à superfície mais próxima com efeitos de [aterramento](spatial-mapping.md#visualization). Eles devem entender por que a movimentação de seu holograma está sendo restrita (por exemplo, devido à colisão com outra superfície próxima). Se não puderem colocar um holograma no local atual, os comentários visuais devem deixá-lo claro por que não. Por exemplo, se o usuário estiver tentando posicionar um Holographic sofá preso na parede, as partes do sofá que estão atrás da parede devem pulsater em uma cor irritado. Ou inversamente, se o aplicativo não puder encontrar uma superfície espacial em um local onde o usuário possa ver uma superfície do mundo real, o aplicativo deverá tornar isso claro. A ausência óbvia de um efeito de aterramento nessa área pode atingir essa finalidade.

### <a name="occlusion"></a>Oclusão

Um dos principais usos das superfícies de mapeamento espacial é simplesmente para os hologramas occlude. Esse comportamento simples tem um grande impacto sobre o realm de hologramas percebido, ajudando a criar um sensor de visceral que realmente estar o mesmo espaço físico que o usuário.

O oclusão também fornece informações para o usuário; Quando um holograma parece ser obstruídodo por uma superfície do mundo real, isso fornece comentários visuais adicionais sobre o local espacial desse holograma no mundo. Por outro lado, o oclusão também pode *ocultar* informações de forma útil do usuário; os hologramas occluding por trás das paredes podem reduzir a desordem Visual de uma maneira intuitiva. Para ocultar ou revelar um holograma, o usuário precisa apenas mover sua cabeça.

O oclusão também pode ser usado para obter as principais expectativas de uma interface do usuário natural com base em interações físicas familiares; se um holograma for obstruídodo por uma superfície, isso ocorre porque essa superfície é sólida e, portanto, o usuário deve esperar que o holograma colidirá com essa superfície e não simplesmente passará por ela.

Às vezes, oclusão de hologramas é indesejável. Se um usuário precisa ser capaz de interagir com um holograma, ele precisa ser capaz de vê-lo-mesmo que esteja por trás de uma superfície do mundo real. Nesses casos, geralmente faz sentido renderizar esse holograma de forma diferente quando é obstruído (por exemplo, reduzindo seu brilho). Dessa forma, o usuário poderá localizar visualmente o holograma, mas ainda saberá que está por trás de algo.

### <a name="physics"></a>Professor

O uso da simulação de física é outra maneira na qual o mapeamento espacial pode ser usado para reforçar a *presença* de hologramas no espaço físico do usuário. Quando minha bola de borracha Holographic é realista na minha mesa, passa pelo andar e desaparece sob o sofá, pode ser difícil acreditar que não está realmente lá.

A simulação de física também oferece a oportunidade de um aplicativo usar interações baseadas em física e natural. Mover uma peça de mobília de Holographic no chão provavelmente será mais fácil para o usuário se as mobília responderem como se estivessem deslizando em todo o andar com a inércia e a fricção apropriadas.

Para gerar comportamentos físicos realistas, você provavelmente precisará executar algum processamento de [malha](spatial-mapping.md#mesh-processing) , como o preenchimento de buracos, a remoção de hallucinations flutuantes e a suavização de superfícies de ásperos.

Você também precisará considerar como a [experiência de verificação](spatial-mapping-design.md#the-environment-scanning-experience) do seu aplicativo influencia sua simulação física. Em primeiro lugar, as superfícies ausentes não colidirão nada; o que acontece quando a bola de borracha faz o corredor e o final do mundo conhecido? Em segundo lugar, você precisa decidir se continuará a responder às alterações no ambiente ao longo do tempo. Em alguns casos, você desejará responder o mais rápido possível; Digamos que se o usuário estiver usando portas e móveis como Barricades móveis em defesa contra uma Tempest de setas romanos de entrada. Em outros casos, no entanto, talvez você queira ignorar novas atualizações; dirigir seu carro Holographic em volta ao Racetrack em seu andar pode repentinamente não ser tão divertido se seu cão decidir ficar no meio do controle.

### <a name="navigation"></a>Navegação

Os aplicativos podem usar dados de mapeamento espacial para conceder aos Holographic caracteres (ou agentes) a capacidade de navegar pelo mundo real da mesma maneira que uma pessoa real. Isso pode ajudar a reforçar a presença de caracteres Holographic restringindo-os ao mesmo conjunto de comportamentos naturais e conhecidos que os do usuário e seus amigos.

Os recursos de navegação também podem ser úteis para os usuários. Depois que um mapa de navegação tiver sido criado em uma determinada área, ele poderá ser compartilhado para fornecer instruções de Holographic para novos usuários que não conhecem esse local. Esse mapa poderia ser criado para ajudar a manter o tráfego do básicos em trânsito sem problemas, ou para evitar acidentes em locais perigosos, como sites de construção.

Os principais desafios técnicos envolvidos na implementação da funcionalidade de navegação serão a detecção confiável de superfícies que poderão ser perfeitas (as pessoas não se movimentam nas tabelas!) e a adaptação normal às alterações no ambiente (as pessoas não percorrem as portas fechadas!). A malha pode exigir algum [processamento](spatial-mapping.md#mesh-processing) antes de ser utilizável para o planejamento e a navegação de caminho por um caractere virtual. Suavizar a malha e remover hallucinations pode ajudar a evitar que os caracteres se tornem presos. Você também pode desejar simplificar drasticamente a malha para acelerar os cálculos de navegação e de planejamento de caminho do caractere. Esses desafios receberam muita atenção no desenvolvimento da tecnologia videogame, e há uma infinidade de literatura de pesquisa disponível sobre esses tópicos.

Observe que a funcionalidade interna NavMesh no Unity não pode ser usada com superfícies de mapeamento espacial. Isso ocorre porque as superfícies de mapeamento espacial não são conhecidas até que o aplicativo seja iniciado, enquanto os arquivos de dados do NavMesh precisam ser gerados a partir dos ativos de origem antes do tempo. Observe também que, o sistema de mapeamento espacial não fornecerá [informações sobre superfícies longe](spatial-mapping-design.md#the-environment-scanning-experience) da localização atual do usuário. Portanto, o aplicativo deve "se lembrar" dessas superfícies se for criar um mapa de uma área muito grande.

### <a name="visualization"></a>Visualização

Na maioria das vezes, é apropriado que as superfícies espaciais fiquem invisíveis; para minimizar a desordem Visual e deixar o mundo real se falar de si mesmo. No entanto, às vezes é útil visualizar as superfícies de mapeamento espacial diretamente, apesar do fato de que suas contrapartes reais já estão visíveis.

Por exemplo, quando o usuário está tentando colocar um holograma em uma superfície (colocando um gabinete Holographic na parede, digamos), pode ser útil "aterrar" o holograma ao converter uma sombra na superfície. Isso dá ao usuário um sentido muito mais claro da proximidade física exata entre o holograma e a superfície. Este também é um exemplo da prática mais geral de ' Visualizar visualmente ' uma alteração antes de o usuário confirmá-la.

Ao visualizar as superfícies, o aplicativo pode compartilhar com o usuário sua compreensão do ambiente. Por exemplo, um jogo de tabuleiro de Holographic poderia visualizar as superfícies horizontais identificadas como "tabelas", de modo que o usuário saiba onde elas devem ir para interagir.

A visualização de superfícies pode ser uma maneira útil de mostrar os espaços próximos do usuário que estão ocultos na exibição. Isso pode fornecer uma maneira simples de fornecer ao usuário acesso à sua cozinha (e a todos os seus hologramas contidos) a partir de sua sala de vida.

As malhas de superfície fornecidas pelo mapeamento espacial podem não ser particularmente ' limpas '. Portanto, é importante visualizá-los adequadamente. Os cálculos de iluminação tradicionais podem realçar erros em normalidades de superfície de maneira Visual, embora as texturas ' limpas ' projetadas na superfície possam ajudar a dar uma aparência mais organizada. Também é possível executar o [processamento de malha](spatial-mapping.md#mesh-processing) para melhorar as propriedades de malha, antes que as superfícies sejam renderizadas.

## <a name="using-the-surface-observer"></a>Usando o observador de superfície

O ponto de partida para o mapeamento espacial é o observador de superfície. O fluxo do programa é o seguinte:
* Criar um objeto de observador de superfície
   * Forneça um ou mais volumes espaciais para definir as regiões de interesse em que o aplicativo deseja receber dados de mapeamento espacial. Um volume espacial é simplesmente uma forma que define uma região de espaço, como uma esfera ou uma caixa.
   * Use um volume espacial com um sistema de coordenadas espaciais bloqueados pelo mundo para identificar uma região fixa do mundo físico.
   * Use um volume espacial, atualizado cada quadro com um sistema de coordenadas espaciais bloqueados pelo corpo, para identificar uma região de espaço que se move (mas não gira) com o usuário.
   * Esses volumes espaciais podem ser alterados posteriormente a qualquer momento, à medida que o status do aplicativo ou do usuário é alterado.
* Usar sondagem ou notificação para recuperar informações sobre superfícies espaciais
   * Você pode ' sondar ' o observador de superfície para o status da superfície espacial a qualquer momento. Como alternativa, você pode se registrar para o evento ' superfícies alteradas ' do observador de superfície, que notificará o aplicativo quando as superfícies espaciais forem alteradas.
   * Para um volume espacial dinâmico, como o modo de exibição frustum ou um volume bloqueado por corpo, os aplicativos precisarão sondar as alterações em cada quadro definindo a região de interesse e, em seguida, obtendo o conjunto atual de superfícies espaciais.
   * Para um volume estático, como um cubo protegido por mundo que cobre uma única sala, os aplicativos podem se registrar para que o evento ' superfícies alteradas ' seja notificado quando as superfícies espaciais dentro desse volume podem ter sido alteradas.
* Alterações de superfícies de processo
   * Itere o conjunto de superfícies espaciais fornecido.
   * Classifique as superfícies espaciais como adicionadas, alteradas ou removidas.
   * Para cada superfície espacial adicionada ou alterada, se apropriado, envie uma solicitação assíncrona para receber a malha atualizada que representa o estado atual da superfície no nível de detalhe desejado.
* Processe a solicitação de malha assíncrona (mais detalhes nas seções a seguir).

## <a name="mesh-caching"></a>Cache de malha

As superfícies espaciais são representadas por malhas de triângulo densas. Armazenar, renderizar e processar essas malhas pode consumir recursos de computação e armazenamento significativos. Assim, cada aplicativo deve adotar um esquema de cache de malha apropriado às suas necessidades, a fim de minimizar os recursos usados para processamento e armazenamento de malha. Esse esquema deve determinar quais malhas devem ser retidas e quais descartar, bem como quando atualizar a malha para cada superfície espacial.

Muitas das considerações discutidas aqui informarão diretamente como seu aplicativo deve abordar o cache de malha. Você deve considerar como o usuário passa pelo ambiente, quais superfícies são necessárias, quando superfícies diferentes serão observadas e quando as alterações no ambiente devem ser capturadas.

Ao interpretar o evento "superfícies alteradas" fornecido pelo observador de superfície, a lógica de cache de malha básica é a seguinte:
* Se o aplicativo vê uma ID de superfície espacial que não foi vista antes, ele deve tratá-lo como uma nova superfície espacial.
* Se o aplicativo vir uma superfície espacial com uma ID conhecida, mas com uma nova hora de atualização, ela deverá tratá-la como uma superfície espacial atualizada.
* Se o aplicativo não vir mais uma superfície espacial com uma ID conhecida, ele deverá tratá-lo como uma superfície espacial removida.

Cabe a cada aplicativo, então, fazer as seguintes escolhas:
* Para novas superfícies espaciais, a malha deve ser solicitada?
   * Geralmente, a malha deve ser solicitada imediatamente para novas superfícies espaciais, o que pode fornecer novas informações úteis ao usuário.
   * No entanto, novas superfícies espaciais perto e na frente do usuário devem receber prioridade e sua malha deve ser solicitada primeiro.
   * Se a nova malha não for necessária, se, por exemplo, o aplicativo tiver ' congelado ' permanentemente ou temporariamente seu modelo do ambiente, ele não deverá ser solicitado.
* Para superfícies espaciais atualizadas, a malha deve ser solicitada?
   * As superfícies espaciais atualizadas perto e na frente do usuário devem receber prioridade e sua malha deve ser solicitada primeiro.
   * Também pode ser apropriado fornecer prioridade mais alta para novas superfícies do que para superfícies atualizadas, especialmente durante a experiência de verificação.
   * Para limitar os custos de processamento, os aplicativos podem querer limitar a taxa na qual eles processam atualizações em superfícies espaciais.
   * Pode ser possível inferir que as alterações em uma superfície espacial sejam secundárias, por exemplo, se os limites da superfície forem pequenos, caso em que a atualização pode não ser importante para ser processada.
   * As atualizações para superfícies espaciais fora da região atual de interesse do usuário podem ser ignoradas inteiramente, embora, nesse caso, seja mais eficiente modificar os volumes delimitadores espaciais em uso pelo observador de superfície.
* Para superfícies espaciais removidas, a malha deve ser descartada?
   * Em geral, a malha deve ser descartada imediatamente para superfícies espaciais removidas, de forma que o holograma oclusão permaneça correto.
   * No entanto, se o aplicativo tiver motivo para acreditar que uma superfície espacial reaparecerá em breve (talvez com base no design da experiência do usuário), pode ser mais eficiente mantê-la do que descartar sua malha e recriá-la mais tarde.
   * Se o aplicativo estiver criando um modelo de grande escala do ambiente do usuário, talvez não queira descartar todas as malhas. No entanto, ele ainda precisará limitar o uso de recursos, possivelmente colocando em spool as malhas em disco, pois as superfícies espaciais desaparecem.
   * Observe que alguns eventos relativamente raros durante a geração de superfície espacial podem fazer com que superfícies espaciais sejam substituídas por novas superfícies espaciais em um local semelhante, mas com IDs diferentes. Consequentemente, os aplicativos que optam por não descartar uma superfície removida devem ter cuidado para não terminar com várias malhas de superfície espacial altamente sobrepostas que abrangem o mesmo local.
* A malha deve ser descartada para outras superfícies espaciais?
   * Mesmo que exista uma superfície espacial, se ela não for mais útil para a experiência do usuário, ela deverá ser descartada. Por exemplo, se o aplicativo "substituir" a sala do outro lado de um porta com um espaço virtual alternativo, as superfícies espaciais nessa sala não serão mais importantes.

Aqui está um exemplo de estratégia de cache de malha, usando histerese espacial e temporal:
* Considere um aplicativo que deseja usar um volume de interesse espacial em forma de frustum que segue o olhar do usuário à medida que eles buscam e percorrem.
* Uma superfície espacial pode desaparecer temporariamente desse volume simplesmente porque o usuário fica longe da superfície ou das etapas mais distantes dela... apenas para olhar de volta ou se aproximar mais de um momento mais tarde. Nesse caso, descartar e recriar a malha para essa superfície representa muitos processamentos redundantes.
* Para reduzir o número de alterações processadas, o aplicativo usa dois observadores de superfície espacial, um contido dentro do outro. O volume maior é esférico e segue o usuário ' lentamente '; Ele só se move quando necessário para garantir que seu centro esteja dentro de 2,0 metres do usuário.
* As malhas de superfície espacial novas e atualizadas são sempre processadas do observador de superfície interna menor, mas as malhas são armazenadas em cache até que desapareçam do observador de superfície externa maior. Isso permite que o aplicativo Evite processar muitas alterações redundantes devido à movimentação de usuário local.
* Como uma superfície espacial também pode desaparecer temporariamente devido à perda de rastreamento, o aplicativo também adia a descartação de superfícies espaciais removidas durante a perda de rastreamento.
* Em geral, um aplicativo deve avaliar a compensação entre o processamento de atualização reduzido e o maior uso de memória para determinar sua estratégia de cache ideal.

## <a name="rendering"></a>Tratamento

Há três maneiras principais pelas quais as malhas de mapeamento espacial tendem a ser usadas para renderização:
* Para visualização de superfície
   * Geralmente, é útil Visualizar superfícies espaciais diretamente. Por exemplo, a conversão de ' Shadows ' de objetos em superfícies espaciais pode fornecer comentários visuais úteis ao usuário enquanto eles estão colocando hologramas em superfícies.
   * Uma coisa a ser lembrada é que as malhas espaciais são diferentes para o tipo de malha que um artista 3D pode criar. A topologia de triângulo não será tão "limpa" quanto a topologia criada por humanos, e a malha será afetada de [vários erros](spatial-mapping-design.md#what-influences-spatial-mapping-quality).
   * Para criar uma estética visual agradável, você pode, portanto, executar algum processamento de [malha](spatial-mapping.md#mesh-processing), por exemplo, para preencher buracos ou normais de superfície suave. Você também pode querer usar um sombreador para projetar texturas criadas pelo artista em sua malha, em vez de Visualizar diretamente a topologia de malha e os normais.
* Para os hologramas occluding por trás das superfícies do mundo real
   * As superfícies espaciais podem ser renderizadas em uma passagem somente de profundidade, o que afeta apenas o [buffer de profundidade](https://msdn.microsoft.com/library/windows/desktop/bb219616(v=vs.85).aspx) e não afeta os destinos de renderização de cor.
   * Isso Prime o buffer de profundidade para occluder os hologramas subsequentemente renderizados por trás das superfícies espaciais. A oclusão precisa dos hologramas melhora o sentido de que os hologramas realmente existem dentro do espaço físico do usuário.
   * Para habilitar a renderização de profundidade, atualize seu estado de mesclagem para definir o [RenderTargetWriteMask](https://msdn.microsoft.com/library/windows/desktop/hh404492(v=vs.85).aspx) como zero para todos os destinos de renderização de cor.
* Para modificar a aparência de hologramas obstruído por superfícies do mundo real
   * Normalmente, a geometria renderizada fica oculta quando é obstruído. Isso é feito definindo a função Depth em seu [estado de estêncil de profundidade](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx) como "menor ou igual a", o que faz com que a geometria fique visível apenas onde está **mais perto** da câmera do que toda a geometria renderizada anteriormente.
   * No entanto, pode ser útil manter determinada geometria visível mesmo quando é obstruído e modificar sua aparência quando obstruído como uma forma de fornecer comentários visuais ao usuário. Por exemplo, isso permite que o aplicativo mostre ao usuário o local de um objeto enquanto estiver claro que está por trás de uma superfície do mundo real.
   * Para conseguir isso, renderize a geometria uma segunda vez com um sombreador diferente que cria a aparência desejada de ' obstruído '. Antes de renderizar a geometria pela segunda vez, faça duas alterações em seu [estado de estêncil de profundidade](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Primeiro, defina a função Depth como "maior que ou igual a" para que a geometria seja visível somente onde estiver **além** da câmera do que toda a geometria renderizada anteriormente. Em segundo lugar, defina DepthWriteMask como zero, para que o buffer de profundidade não seja modificado (o buffer de profundidade deve continuar a representar a profundidade da geometria **mais próxima** da câmera).

O [desempenho](understanding-performance-for-mixed-reality.md) é uma preocupação importante ao renderizar malhas de mapeamento espacial. Aqui estão algumas técnicas de desempenho de renderização específicas para renderizar malhas de mapeamento espacial:
* Ajustar densidade do triângulo
   * Ao solicitar malhas de superfície espacial do seu observador de superfície, solicite a menor densidade de malhas de triângulo que será suficiente para suas necessidades.
   * Pode fazer sentido variar a densidade do triângulo em uma superfície por superfície, dependendo da distância da superfície do usuário e de sua relevância para a experiência do usuário.
   * Reduzir as contagens de triângulos reduzirá o uso de memória e os custos de processamento de vértice na GPU, embora não afete os custos de processamento de pixel.
* Executar a remoção de frustum
   * A remoção de frustum ignora objetos de desenho que não podem ser vistos porque estão fora do frustum de exibição atual. Isso reduz os custos de processamento de CPU e GPU.
   * Como a remoção é realizada em uma base por malha e as superfícies espaciais podem ser grandes, dividir cada malha de superfície espacial em partes menores pode resultar em uma remoção mais eficiente (na medida em que menos triângulos de fora da tela são renderizados). No entanto, há uma compensação; Quanto mais malhas você tiver, mais chamadas de desenho deverão ser feitas, o que pode aumentar os custos de CPU. Em um caso extremo, os próprios cálculos de remoção de frustum podem até mesmo ter um custo de CPU mensurável.
* Ajustar a ordem de renderização
   * As superfícies espaciais tendem a ser grandes, pois representam o ambiente inteiro do usuário em torno delas. Os custos de processamento de pixel na GPU podem, portanto, ser altos, especialmente em casos em que há mais de uma camada de geometria visível (incluindo superfícies espaciais e outros hologramas). Nesse caso, a camada mais próxima do usuário será occluding as camadas mais distantes, portanto, qualquer tempo de GPU gasto renderizando essas camadas mais distantes é desperdiçado.
   * Para reduzir esse trabalho redundante na GPU, ele ajuda a renderizar superfícies opacas na ordem de frente para trás (mais próximas primeiro, mais distantes). Por ' opaco ', queremos dizer superfícies para as quais o DepthWriteMask está definido como um em seu [estado de estêncil de profundidade](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Quando as superfícies mais próximas são renderizadas, elas primem o buffer de profundidade para que as superfícies mais distantes sejam ignoradas com eficiência pelo processador de pixel na GPU.

## <a name="mesh-processing"></a>Processamento de malha

Um aplicativo pode querer executar [várias operações](spatial-mapping.md#mesh-processing) em malhas de superfície espacial para atender às suas necessidades. Os dados de índice e vértice fornecidos com cada malha de superfície espacial usam o mesmo layout familiar que os buffers de [vértice e de índice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) usados para renderizar malhas de triângulo em todas as APIs de renderização modernas. No entanto, um fator importante a ser considerado é que os triângulos de mapeamento espacial têm uma **ordem de vento no sentido anti-horário**. Cada triângulo é representado por três índices de vértice no buffer de índice da malha e esses índices identificarão os vértices do triângulo em um pedido no **sentido horário** , quando o triângulo for exibido do lado **frontal** . O lado frontal (ou externo) de malhas de superfície espacial corresponde à medida que você esperaria para o lado frontal (visível) das superfícies do mundo real.

Os aplicativos só devem executar a simplificação de malha se a densidade de triângulo mais grosseira fornecida pelo observador de superfície ainda for muito grande: esse trabalho é computacionalmente caro e já está sendo executado pelo tempo de execução para gerar os vários níveis de detalhes fornecidos.

Como cada observador de superfície pode fornecer várias superfícies espaciais desconectadas, alguns aplicativos talvez queiram recortar essas malhas de superfície espacial entre si e, em seguida, zipper-las em conjunto. Em geral, a etapa de recorte é necessária, pois as malhas de superfície espacial próximas geralmente se sobrepõem ligeiramente.

## <a name="raycasting-and-collision"></a>Raycasting e colisão

Para que uma API física (como [Havok](http://www.havok.com/)) forneça um aplicativo com raycasting e funcionalidade de colisão para superfícies espaciais, o aplicativo deve fornecer malhas de superfície espacial para a API física. As malhas usadas para a física geralmente têm as seguintes propriedades:
* Eles contêm apenas pequenos números de triângulos. As operações de física são mais intensivas em computação do que as operações de renderização.
* Elas são ' d' água. As superfícies destinadas a serem sólidas não devem ter pequenos buracos; até mesmo os orifícios muito pequenos para serem visíveis podem causar problemas.
* Eles são convertidos em convexa hulls. Convexa hulls têm poucos polígonos e são livres de orifícios, e são muito mais eficientes em termos computacionais para serem processados do que as malhas de triângulo brutos.

Ao executar raycasts em superfícies espaciais, tenha em mente que essas superfícies são muitas vezes complexas, formas desorganizadas com detalhes de pouco confusos, assim como sua mesa! Isso significa que uma única Raycast geralmente é insuficiente para fornecer a você informações suficientes sobre a forma da superfície e a forma do espaço vazio perto dela. Geralmente, é uma boa ideia executar muitas raycasts em uma área pequena e usar os resultados agregados para obter uma compreensão mais confiável da superfície. Por exemplo, usar a média de 10 raycasts para orientar o posicionamento do holograma em uma superfície produzirá um resultado muito mais suave e menos "tremulação" que usa apenas um único Raycast.

No entanto, tenha em mente que cada Raycast pode ter um alto custo computacional. Portanto, dependendo do seu cenário de uso, você deve compensar o custo computacional de raycasts adicionais (executado todos os quadros) em relação ao custo computacional do [processamento de malha](spatial-mapping.md#mesh-processing) para suavizar e remover buracos em superfícies espaciais (realizadas quando espaciais as malhas são atualizadas).

## <a name="troubleshooting"></a>Solução de problemas
* Para que as malhas de superfície sejam orientadosdas corretamente, cada gameobject precisa estar ativo antes de ser enviado para o SurfaceObeserver para que sua malha seja construída. Caso contrário, as malhas serão exibidas no seu espaço, mas giradas em ângulos estranhos.
* O gameobject que executa o script que se comunica com o SurfaceObserver precisa ser definido para a origem. Caso contrário, todos os GameObjects que você criar e enviar para o SurfaceObserver ter suas malhas construídas terão um deslocamento igual ao deslocamento do objeto do jogo pai. Isso pode fazer com que suas malhas mostrem vários medidores de distância, o que torna muito difícil depurar o que está acontecendo.

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas](coordinate-systems.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Projeto de mapeamento espacial](spatial-mapping-design.md)
* [Compreensão da cena](scene-understanding.md)
* [Estudo de caso - Como olhar através dos buracos na sua realidade](case-study-looking-through-holes-in-your-reality.md)

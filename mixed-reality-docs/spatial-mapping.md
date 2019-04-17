---
title: Mapeamento espacial
description: Mapeamento espacial fornece uma representação detalhada das superfícies do mundo real no ambiente em torno do HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: mapeamento espacial, HoloLens, realidade mista, superfície reconstrução, malha, sr
ms.openlocfilehash: 31abeca624512f1d5e721dbe879ca2243cf41345
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591008"
---
# <a name="spatial-mapping"></a>Mapeamento espacial

Mapeamento espacial fornece uma representação detalhada das superfícies do mundo real no ambiente em torno do HoloLens, permitindo que os desenvolvedores criem uma experiência de realidade misturada convincente. Mesclando o mundo real com o mundo virtual, um aplicativo pode fazer hologramas parecer real. Aplicativos também podem alinhar mais naturalmente com as expectativas dos usuários, fornecendo as interações e comportamentos familiares do mundo real.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> Mapeamento espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="conceptual-overview"></a>Visão geral conceitual

![As superfícies que abrangem uma sala de malha](images/SurfaceReconstruction.jpg)<br>
*Um exemplo de uma malha de mapeamento espacial que abrangem uma sala*

Os dois tipos de objeto primário usados para mapeamento espacial são 'Observador de superfície espacial' e a 'superfície espacial'.

O aplicativo fornece o observador de superfície espacial com um ou mais volumes delimitadoras, para definir as regiões de espaço no qual o aplicativo deseja receber os dados de mapeamento espacial. Para cada um desses volumes, o mapeamento espacial fornecerá o aplicativo com um conjunto de superfícies espacial.

Esses volumes podem ser estáticos (em um local fixo em relação ao mundo real) ou eles podem ser anexados para o HoloLens (eles movem, mas não giram, com o HoloLens enquanto se movimentam através do ambiente). Cada superfície espacial descreve as superfícies do mundo real em um pequeno volume de espaço, representado como uma malha de triângulos anexada a um mundo bloqueada [sistema de coordenadas espacial](coordinate-systems.md).

Como o HoloLens coletam novos dados sobre o ambiente e quando ocorrem alterações no ambiente, superfícies espaciais aparecerá, desaparecem e alterar.

## <a name="common-usage-scenarios"></a>Cenários de uso comuns

![Ilustrações de cenários de uso comuns do mapeamento espacial: Posicionamento, oclusão, física e navegação](images/sm-concepts-1000px.png)

### <a name="placement"></a>Colocação

Mapeamento espacial fornece aplicativos com a oportunidade de apresentar formas naturais e familiares de interação ao usuário; o que poderia ser mais natural do que colocar seu telefone para baixo sobre a mesa?

Restringir o posicionamento de hologramas (ou de modo geral, qualquer seleção de locais espaciais) para ficar em superfícies fornece um mapeamento natural de 3D (ponto no espaço) para 2D (ponto na superfície). Isso reduz a quantidade de informações que o usuário precisa fornecer para o aplicativo e, portanto, torna as interações do usuário mais rápida, fácil e mais preciso. Isso é especialmente verdadeiro porque 'distância' não é algo que usamos fisicamente comunicando-se a outras pessoas ou computadores. Quando podemos apontar com nosso dedo, estamos especificando uma direção, mas não uma distância.

Uma limitação importante aqui é que, quando um aplicativo infere a distância da direção (por exemplo, executando um raycast ao longo da direção de olhar do usuário para localizar mais próximo superfície espacial), isso deverá produzir resultados que o usuário é capaz de prever com confiança. Caso contrário, o usuário perderá seu senso de controle, e isso pode rapidamente se tornar frustrante. Um método que ajuda com isso é executar vários raycasts em vez de apenas um. Os resultados de agregação devem ser mais suave e mais previsível, menos suscetíveis a influenciar dos resultados de 'exceções' transitório (como pode ser causado por raios passando buracos pequenos ou atingindo pequenos pedaços de geometria que o usuário não está ciente do). Agregação ou Suavização também pode ser executada ao longo do tempo; Por exemplo, você pode limitar a velocidade máxima na qual um holograma pode variar em termos de distância do usuário. Também pode ajudar apenas limitando o valor de distância mínima e máxima, portanto, o holograma que está sendo movido não, de repente, distância voar na distância ou vêm falhando volta para a face do usuário.

Aplicativos também podem usar a forma e a direção de superfícies de posicionamento de holograma de guia. Uma cadeira holográfica não deve invadir por meio de paredes e deve estar liberação com o chão, mesmo se ele está ligeiramente irregular. Esse tipo de funcionalidade seria provavelmente contam com o uso de colisões de física, em vez de apenas raycasts, preocupações semelhantes porém serão aplicada. Se o holograma que está sendo colocado tem vários polígonos pequeno protuberantes, como os segmentos em um cadeira, talvez faça sentido para expandir a representação física desses polígonos para algo mais amplo e mais suave, para que fiquem mais pode deslizar ao longo de superfícies espaciais sem Realce em captura.

No extremo, entrada do usuário pode ser simplificada distância inteiramente e superfícies espaciais podem ser usadas para executar o posicionamento de holograma totalmente automáticas. Por exemplo, o aplicativo pode colocar um comutador de luz holográfico em algum lugar na parede para o usuário pressione. A mesma advertência sobre previsibilidade aplica duplamente aqui; Se o usuário espera que o controle sobre o posicionamento de holograma, mas o aplicativo não sempre coloca hologramas onde eles esperam (se a opção de luz aparece em algum lugar que o usuário não conseguir acessar), isso será uma experiência frustrante. Ele pode ser, na verdade, pior executar o posicionamento automático que requer correção de usuário parte do tempo, que ao exigem apenas o usuário execute sempre posicionamento em si; como é o posicionamento automático bem-sucedida *esperado*, correção manual parece um fardo!

Observe também que, a capacidade de um aplicativo para usar superfícies espaciais para posicionamento depende intensamente do aplicativo [experiência de verificação](spatial-mapping-design.md#the-environment-scanning-experience). Se uma superfície não foi examinada, ele não pode ser usado para posicionamento. É responsabilidade do aplicativo para tornar isso claro para o usuário, para que eles também podem ajudar a verificar novas superfícies ou selecione um novo local.

Os comentários visuais para o usuário são de suma importância durante o posicionamento. O usuário precisa saber onde o holograma é em relação à superfície mais próxima com [efeitos de aterramento](spatial-mapping.md#visualization). Eles devem entender por que a movimentação de seu holograma está sendo restrito (por exemplo, devido a conflito com outra mais próxima de superfície). Se eles não é possível colocar um holograma no local atual, em seguida, comentários visuais devem esclarecer por que não. Por exemplo, se o usuário está tentando colocar um sofá holográfico fica preso metade no mural, em seguida, as partes do sofá que estão atrás de parede devem pulsate em uma cor irritada. Ou, por outro lado, se o aplicativo não conseguir encontrar uma superfície espacial em um local em que o usuário pode ver uma superfície do mundo real, em seguida, o aplicativo deve tornar isso claro. A ausência evidente de um efeito de aterramento nessa área pode alcançar esse propósito.

### <a name="occlusion"></a>Oclusão

Um dos principais usos de superfícies de mapeamento espacial é simplesmente occlude hologramas. Esse comportamento simple tem um grande impacto sobre o realismo percebido de hologramas, ajudando a criar um senso visceral que habitam realmente o mesmo espaço físico que o usuário.

Oclusão também fornece informações para o usuário; Quando um holograma parece ser obstruídos por uma superfície do mundo real, isso fornece comentários visuais adicionais sobre o local espacial do que holograma no mundo. Por outro lado, oclusão pode também utilmente *ocultar* informações do usuário; occluding hologramas atrás paredes pode reduzir a desordem visual de maneira intuitiva. Para ocultar ou revelar um holograma, o usuário simplesmente precisa mover suas cabeças.

Oclusão também pode ser usado para preparar as expectativas para uma interface de usuário naturais com base em interações físicas familiares; Se um holograma é obstruído por uma superfície é porque essa superfície sólida, portanto, o usuário deve esperar que o holograma serão *colidem* com essa superfície e não simplesmente passam por ela.

Às vezes, oclusão de hologramas é indesejável. Se um usuário precisa ser capaz de interagir com um holograma, eles precisam conseguir vê-lo – mesmo se ele estiver atrás de uma superfície do mundo real. Nesses casos, geralmente faz sentido para renderizar tal holograma um forma diferente quando ele é obstruído (por exemplo, reduzindo seu brilho). Dessa forma, o usuário será capaz de localizar visualmente o holograma, mas ainda estará cientes de que ele está protegido por algo.

### <a name="physics"></a>Física

O uso de simulação de física é outra maneira quais mapeamento espacial pode ser usado para reforçar os *presença* de hologramas em um espaço físico do usuário. Quando meu bola de borracha holográfica realisticamente efetua logoff minha mesa, bounces entre o piso e desaparece no sofá, talvez seja difícil para mim acreditar que não é realmente existe.

Simulação de física também fornece a oportunidade para um aplicativo para usar naturais e familiares de interações baseadas em física. Mover uma parte do holográfica móveis ao redor no chão provavelmente será mais fácil para o usuário se os móveis responde como se ele foram deslizante entre o piso com a inércia apropriada e atrito.

Para gerar comportamentos físicos realistas, você provavelmente precisará executar algumas [processamento de malha](spatial-mapping.md#mesh-processing) , como preenchimento de brechas, removendo flutuante hallucinations e suavização aproximado superfícies.

Você também precisa considerar como seu aplicativo [experiência de verificação](spatial-mapping-design.md#the-environment-scanning-experience) influencia seu simulação de física. Em primeiro lugar, falta superfícies não entrem em conflito com qualquer coisa; o que acontece quando a bola de borracha efetua logoff para baixo a caminhar e após o fim do mundo conhecido? Em segundo lugar, você precisa decidir se você continuará a responder a alterações no ambiente ao longo do tempo. Em alguns casos, convém responder mais rapidamente possível; Digamos que se o usuário está usando as portas e móveis como barricades Movível na defesa contra um tempest setas Roman entrada. Em outros casos, você pode querer ignorar novas atualizações; orientando seu carro esportivo holographic em torno da pista em suas instalações, de repente, não pode ser muito divertida se seu cachorro decide ficam no meio da faixa.

### <a name="navigation"></a>Navegação

Aplicativos podem usar dados de mapeamento espacial conceder holográfica caracteres (ou agentes) a capacidade de navegar do mundo real da mesma forma que seria uma pessoa real. Isso pode ajudar a reforçar a presença de caracteres holográfica, restringindo-os para o mesmo conjunto de comportamentos naturais e familiares, como aquelas do usuário e seus amigos.

Recursos de navegação pode ser útil para os usuários também. Após a criação de um mapa de navegação em uma determinada área, ele poderia ser compartilhado para fornecer instruções holographic para novos usuários desconhecidos nesse local. Este mapa pode ser criado para ajudar a manter um 'tráfego' fluindo sem problemas, ou para evitar acidentes em locais perigosas, como sites de construção.

Os principais desafios técnicos envolvidos na implementação de funcionalidade de navegação será confiável detecção de superfícies ser examinável (os seres humanos não guiá-lo no tabelas!) e normal adaptação a alterações no ambiente (os seres humanos não percorrer portas fechadas!). A malha pode exigir algumas [processamento](spatial-mapping.md#mesh-processing) antes de ser usado para o planejamento de caminho e a navegação por um caractere virtual. Suavização de malha e removendo hallucinations podem ajudar a evitar caracteres se tornando paralisadas. Você também poderá simplificar drasticamente a malha para acelerar o planejamento de caminho do seu caractere e cálculos de navegação. Esses desafios receberam uma grande quantidade de atenção no desenvolvimento de tecnologia de videogame e há uma grande quantidade de literatura de pesquisa disponíveis sobre esses tópicos.

Observe que a funcionalidade interna de NavMesh no Unity não pode ser usada com as superfícies de mapeamento espacial. Isso ocorre porque as superfícies de mapeamento espacial não são conhecidas até que o aplicativo é iniciado, enquanto NavMesh os arquivos de dados precisam ser gerados a partir de ativos de código-fonte antes do tempo. Observe também que, o sistema de mapeamento espacial não fornecerá [informações sobre as superfícies muito longe](spatial-mapping-design.md#the-environment-scanning-experience) do local atual do usuário. Portanto, o aplicativo deve 'Lembre-se' superfícies em si se é criar um mapa de uma área muito grande.

### <a name="visualization"></a>Visualização

Na maioria das vezes, ela é adequada para superfícies espaciais seja invisível; para minimizar a desordem visual e permitir que o real world falarem por si mesmo. No entanto, às vezes é útil visualizar as superfícies de mapeamento espacial diretamente, apesar do fato de que suas contrapartes do mundo real já estão visíveis.

Por exemplo, quando o usuário está tentando colocar um holograma em uma superfície (colocando um gabinete holográfico no mural, digamos) pode ser útil ' Terra ' o holograma convertendo uma sombra para a superfície. Isso fornece ao usuário um senso muito mais claro de proximidade física exata entre o holograma e a superfície. Isso também é um exemplo de como a prática mais geral de visualmente 'Visualizar' uma alteração antes do usuário confirma a ele.

Visualizando superfícies, o aplicativo pode compartilhar com o usuário sua compreensão do ambiente. Por exemplo, um jogo de tabuleiro holográfico pudesse visualizar as superfícies horizontais que ela identificou como 'tabelas', para que o usuário saiba onde eles devem ir para interagir.

Visualizar superfícies pode ser uma maneira útil para mostrar ao usuário nas proximidades de espaços que estão ocultos da exibição. Isso poderá fornecer uma maneira simples de conceder o acesso de usuário a sua cozinha (e todos os seus hologramas independentes) na sua sala de estar.

As malhas de superfície fornecidas pelo mapeamento espacial não podem ser particularmente 'limpas'. Portanto, é importante para visualizá-las adequadamente. Cálculos de iluminação tradicional podem realçar erros em normais da superfície de uma maneira de distração Visual, enquanto 'limpas' texturas projetadas para a superfície podem ajudar a dar a ele uma aparência mais organizada. Também é possível realizar [processamento de malha](spatial-mapping.md#mesh-processing) para melhorar a propriedades de malha, antes das superfícies são renderizadas.

## <a name="using-the-surface-observer"></a>Usando o observador de superfície

O ponto de partida para mapeamento espacial é o observador de superfície. Fluxo do programa é da seguinte maneira:
* Criar um objeto observador superfície
   * Forneça um ou mais volumes espaciais, para definir as regiões de interesse em que o aplicativo deseja receber os dados de mapeamento espacial. Um volume espacial é simplesmente uma forma de definir uma região do espaço, como uma esfera ou uma caixa.
   * Use um volume espacial com um sistema de coordenadas espacial bloqueado pelo mundo para identificar uma região fixa do mundo físico.
   * Use um volume espacial, atualizado de cada quadro com um corpo bloqueada espacial sistema de coordenadas, para identificar uma região de espaço que move (mas não gira) com o usuário.
   * Esses volumes espaciais podem ser alterados posteriormente a qualquer momento, como o status do aplicativo ou as alterações do usuário.
* Use sondagem ou notificação para recuperar informações sobre as superfícies espaciais
   * Você pode 'sondar' o observador de superfície para o status de superfície espacial a qualquer momento. Como alternativa, você pode se registrar para 'alterado de superfícies de' evento do observador superfície, que notificará o aplicativo quando superfícies espaciais foram alterados.
   * Para um volume dinâmico espacial, como frustum o modo de exibição, ou um volume bloqueado de corpo, aplicativos precisam sondar alterações cada quadro, definindo a região de interesse e, em seguida, obter o conjunto atual de superfícies espaciais.
   * Para um volume estático, como um cubo bloqueado pelo mundo, que abrangem uma única sala, aplicativos podem se registrar para o evento 'alterado de superfícies' ser notificado quando superfícies espaciais dentro desse volume podem ter sido alterado.
* Alterações de superfícies de processo
   * Itere o conjunto fornecido de superfícies espaciais.
   * Classificar espaciais superfícies como adicionado, alterado ou removido.
   * Para cada superfície espacial adicionado ou alterado, se apropriado, envie uma solicitação assíncrona para receber a malha atualizada que representa o estado atual de superfície no nível desejado de detalhes.
* Processe a solicitação assíncrona de malha (mais detalhes nas seções a seguir).

## <a name="mesh-caching"></a>Malha de armazenamento em cache

Superfícies espaciais são representadas por malhas de triângulos densa. Armazenar, renderizar e processar essas malhas podem consumir recursos significativos de computação e armazenamento. Assim, cada aplicativo deve adotar uma malha de esquema apropriada às suas necessidades, para minimizar os recursos usados para processamento de malha e o armazenamento de cache. Esse esquema deve determinar quais malhas para manter e qual descartar, bem como quando atualizar a malha para cada superfície espacial.

Muitas das considerações discutidas ali informará diretamente como o seu aplicativo deve abordar a malha de armazenamento em cache. Você deve considerar como o usuário se move através do ambiente, que cobrem é necessários, quando serão observadas diferentes superfícies e quando as alterações no ambiente devem ser capturadas.

Ao interpretar o evento 'alterado de superfícies' fornecido pelo observador superfície, a lógica de cache de malha básica é o seguinte:
* Se o aplicativo vê uma ID de superfície espacial que ele não tenha visto antes, ele deve tratar isso como uma nova superfície espacial.
* Se o aplicativo vê uma superfície espacial com uma ID conhecida, mas com um novo tempo de atualização, ele deve tratar isso como uma superfície espacial atualizada.
* Se o aplicativo não vê uma superfície espacial com uma ID conhecida, ele deve tratar isso como uma superfície espacial removida.

Cabe a cada aplicativo, em seguida, faça o seguinte:
* Para novas superfícies espaciais, a malha deve ser solicitada?
   * Geralmente, malha deve ser solicitada imediatamente para novas superfícies espaciais, que podem fornecer informações úteis de novo para o usuário.
   * No entanto, novas superfícies espaciais perto e na frente do usuário devem ser dada prioridade e sua malha deve ser solicitada pela primeira vez.
   * Se a nova malha não for necessário, se por exemplo o aplicativo tem permanente ou temporariamente "congelado' seu modelo do ambiente, em seguida, ele deve não ser solicitado.
* Para a superfície espacial atualizada, a malha deve ser solicitada?
   * Superfície espacial atualizada quase e na frente do usuário deve ser dada prioridade e sua malha deve ser solicitada pela primeira vez.
   * Ele também pode ser apropriado deem mais prioridade para novas superfícies que para atualizada superfícies, especialmente durante a experiência de verificação.
   * Para limitar os custos de processamento, os aplicativos talvez queiram limitar a taxa em que eles processem as atualizações para superfícies espaciais.
   * É possível inferir que as alterações a uma superfície espacial são pequenas, por exemplo, se os limites da superfície forem pequenos, caso em que a atualização pode não ser importante suficiente ao processo.
   * Atualizações para espaciais superfícies fora da região de interesse do usuário atual podem ser ignoradas totalmente, mesmo nesse caso, pode ser mais eficiente para modificar os volumes delimitadora espaciais usando o observador de superfície.
* Para superfícies espaciais removidas, a malha deve ser descartada?
   * Geralmente, malha deve ser descartada imediatamente para superfícies espaciais removidas, para que oclusão holograma permaneça correto.
   * No entanto, se o aplicativo tiver motivos para acreditar que uma superfície espacial reaparecerá em breve (talvez com base no design da experiência do usuário), ele poderá ser mais eficiente para retê-lo que to descartar sua malha e recriá-lo novamente mais tarde.
   * Se o aplicativo está criando um modelo em larga escala do ambiente do usuário, em seguida, ele não poderá descartar qualquer malhas em todos os. Ele ainda será necessário limitar o uso de recursos, possivelmente por malhas de spool para disco conforme superfícies espaciais desaparecerem.
   * Observe que alguns eventos relativamente raros durante a geração de superfície espacial podem causar superfícies espaciais a ser substituído por novas superfícies espaciais em um local semelhante, mas com IDs diferentes. Consequentemente, os aplicativos que escolha não para descartar uma superfície removida devem ter cuidado não ao final backup com vários altamente sobreposta espaciais superfície malhas que abrangem o mesmo local.
* Malha deve ser descartada para quaisquer outras superfícies espaciais?
   * Mesmo enquanto uma superfície espacial existe, se ele não é mais útil para a experiência do usuário e em seguida, ele deve ser descartado. Por exemplo, se o aplicativo 'substitui' sala no outro lado de uma porta de entrada com um espaço virtual alternativo, em seguida, as superfícies espaciais na sala não importam.

Aqui está uma exemplo malha estratégia de cache, usando Histerese espacial e temporal:
* Considere um aplicativo que deseja usar um volume espacial em forma de frustum de interesse que segue a olhar do usuário conforme eles olhar em volta e percorrer.
* Uma superfície espacial pode desaparecer temporariamente este volume simplesmente porque o usuário procura longe a superfície ou etapas adicionais para longe dela... somente a olhar para trás ou aproxima novamente um momento posterior. Nesse caso, descartando e recriando a malha para essa superfície representam muito processamento redundante.
* Para reduzir o número de alterações processadas, o aplicativo usa dois espaciais superfície observadores, um contido dentro do outro. O volume maior é Esférico e segue o usuário 'lentamente'; ele move somente quando necessário para garantir que seu centre esteja dentro do 2.0 metres do usuário.
* Malhas de superfície espaciais novas e atualizadas são sempre processadas do observador superfície interno menor, mas as malhas são armazenados em cache até que elas desaparecem o observador de superfície externo maior. Isso permite que o aplicativo para evitar o processamento de muitas alterações redundantes devido à movimentação de usuário local.
* Uma vez que uma superfície espacial também pode desaparecer temporariamente devido a perda de controle, o aplicativo também adia a descarte superfícies espaciais removidas durante a perda de controle.
* Em geral, um aplicativo deve avaliar a compensação entre o processamento de atualização reduzida e maior uso de memória para determinar sua estratégia de cache ideal.

## <a name="rendering"></a>Renderização

Há três maneiras principais em que as malhas de mapeamento espacial tendem a ser usada para renderização:
* Para visualização de superfície
   * Geralmente é útil visualizar as superfícies espaciais diretamente. Por exemplo, conversão como 'shadows' dos objetos em superfícies espaciais podem fornecer comentários visuais úteis para o usuário enquanto eles estão colocando hologramas em superfícies.
   * Uma coisa a se ter em mente é que as malhas espaciais são diferentes para o tipo de malhas que um artista 3D pode criar. A topologia de triângulo não será tão 'limpa' como topologia criada por humanos e sofrerão a malha [vários erros](spatial-mapping-design.md#what-influences-spatial-mapping-quality).
   * Para criar uma estética visual agradável, portanto, convém executar algumas [processamento de malha](spatial-mapping.md#mesh-processing), por exemplo, falhas de preenchimento ou normais da superfície suaves. Você também poderá usar um sombreador de texturas projetado por artista do projeto em sua malha, em vez de diretamente visualizando a topologia de malha e normais.
* Para occluding hologramas por trás de superfícies do mundo real
   * Superfícies espaciais podem ser renderizadas em uma passagem somente de profundidade que afeta apenas o [buffer de profundidade](https://msdn.microsoft.com/library/windows/desktop/bb219616(v=vs.85).aspx) e não afeta os destinos de renderização de cor.
   * Isso inicia o buffer de profundidade para occlude hologramas subsequentemente renderizados por trás de superfícies espaciais. Oclusão preciso de hologramas aprimora o sentido de que realmente existem hologramas dentro do espaço de física do usuário.
   * Para habilitar a renderização de profundidade, atualize seu estado do blend para definir a [RenderTargetWriteMask](https://msdn.microsoft.com/library/windows/desktop/hh404492(v=vs.85).aspx) como zero para a cor de todos os destinos de renderização.
* Para modificar a aparência de hologramas obstruídos pelo superfícies do mundo real
   * Geometria normalmente renderizada é ocultada quando ele é obstruído. Isso é feito definindo-se a função de profundidade no seu [estado de estêncil de profundidade](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx) para "menor que ou igual", que faz com que a geometria a ser visível apenas quando são **mais próximo** para a câmera que todos processado anteriormente geometria.
   * No entanto, pode ser útil para manter certa geometria visíveis mesmo quando ele é obstruído e modificar sua aparência quando obstruídos como uma maneira de fornecer comentários visuais ao usuário. Por exemplo, isso permite que o aplicativo para mostrar o usuário o local de um objeto ao mesmo tempo, deixando claro que está por trás de uma superfície do mundo real.
   * Para fazer isso, renderizar a geometria de uma segunda vez com um sombreador diferente que cria a aparência desejada de 'occluded'. Antes de renderizar a geometria pela segunda vez, faça duas alterações para seu [estado de estêncil de profundidade](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Primeiro, defina a função de profundidade para "maior que ou igual" para que a geometria estará visível apenas quando ele for **ainda mais** da câmera que geometria anteriormente renderizada todos os. Em segundo lugar, defina o DepthWriteMask como zero, para que o buffer de profundidade não será modificado (o buffer de profundidade deve continuar representar a profundidade da geometria **mais próximo** à câmera).

[Desempenho](understanding-performance-for-mixed-reality.md) é uma preocupação importante durante a renderização de malhas de mapeamento espacial. Estas são algumas técnicas de desempenho de renderização específico à renderização de malhas de mapeamento espacial:
* Ajustar a densidade de triângulo
   * Quando o solicitante superfície espacial malhas de sua superfície observador, solicite a menor densidade de malhas de triângulos que será suficiente para suas necessidades.
   * Talvez faça sentido para variar a densidade de triângulo em uma base de superfície a superfície, dependendo da distância de superfície do usuário e sua relevância para a experiência do usuário.
   * Contagens de triângulo reduzindo reduzirá o uso de memória e os custos de processamento de vértice no GPU, embora isso não afetará os custos de processamento de pixel.
* Executar frustum traseira
   * Frustum traseira ignora os objetos de desenho que não podem ser vistos porque eles estão fora de frustum de exibição atual. Isso reduz os custos de processamento de CPU e GPU.
   * Como traseira é executada em uma base por malha e superfícies espaciais podem ser grandes, dividir cada malha superfície espacial em partes menores pode resultar na seleção mais eficiente (que são renderizados menos triângulos fora da tela). Há uma compensação, no entanto; as malhas mais que você tem, as mais chamadas de desenho deve fazer, que podem aumentar os custos de CPU. Em casos extremos, a frustum traseira cálculos próprios poderia ter um custo de CPU mensurável.
* Ajustar a ordem de renderização
   * Superfícies espaciais tendem a ser grandes, porque eles representam todo o ambiente do usuário ao redor deles. Os custos na GPU de processamento de pixel, portanto, pode ser alto, especialmente em casos onde há mais de uma camada de geometria visível (incluindo superfícies espaciais e outras hologramas). Nesse caso, a camada mais próximo do usuário será ser occluding ainda mais as camadas cara, portanto, qualquer GPU desperdiçar um tempo gasto na renderização essas camadas mais distantes.
   * Para reduzir esse trabalho redundante na GPU, ele ajuda a renderizar superfícies opacas na ordem de frente para trás (mais próximo que aqueles em primeiro lugar, mais distantes da última). Por 'opaco', queremos dizer superfícies para o qual o DepthWriteMask é definido como um em sua [estado de estêncil de profundidade](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Quando são processadas as superfícies mais próximos, elas comandarão o buffer de profundidade, de modo que mais distantes superfícies com eficiência são ignoradas pelo processador de pixel na GPU.

## <a name="mesh-processing"></a>Processamento de malha

Um aplicativo talvez queira realizar [várias operações](spatial-mapping.md#mesh-processing) em malhas de superfície espaciais para atender às suas necessidades. Os dados de índice e vértice fornecidos com cada malha superfície espacial usam o mesmo layout familiar como o [buffers de índice e vértice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) que são usadas para renderizar as malhas de triângulos em todas as APIs de renderização moderno. No entanto, fatos principais a serem consideradas é que os triângulos de mapeamento espacial tem um **front-no sentido horário Enrolamento ordem**. Cada triângulo é representado por três índices de vértice no buffer de índices da malha e esses índices identificará os vértices do triângulo em uma **no sentido horário** ordem, quando o triângulo é visualizado a partir de **front** lado. Frente lado (ou externa) de malhas de superfície espaciais corresponde a como você esperaria, ao lado frontal (visível) das superfícies do mundo real.

Aplicativos devem ser executadas somente se a densidade de triângulo mais simples fornecida pelo observador superfície for ainda suficientemente grosseiro, esse trabalho é dispendioso em termos de simplificação de malha e já que está sendo executada pelo tempo de execução para gerar os vários níveis de detalhe de fornecido.

Porque cada observador superfície pode fornecer várias superfícies espaciais desconectadas, alguns aplicativos talvez queiram Recortar esses espacial superfície malhas em relação a cada outro, em seguida, compactador-los juntos. Em geral, a etapa de recorte é necessária, como nas proximidades de malhas de superfície espaciais geralmente se sobrepõem um pouco.

## <a name="raycasting-and-collision"></a>Raycasting e colisão

Para que uma API física (como [Havok](http://www.havok.com/)) para fornecer um aplicativo com a funcionalidade de raycasting e colisão para superfícies espaciais, o aplicativo deve fornecer a superfície espacial malhas para a API de física. Malhas usadas para física geralmente têm as seguintes propriedades:
* Elas contêm somente um pequeno número de triângulos. Operações de física são mais intensos de computação que as operações de renderização.
* Eles são 'd'água-rígidas'. Superfícies que se destina a ser sólido não devem ter pequeno orifícios neles; até mesmo buracos muito pequenos para ser visível podem causar problemas.
* Elas são convertidas em hulls convexos. Hulls convexos têm alguns polígonos e são livres de brechas, e são computacionalmente muito mais eficientes para processar de malhas de triângulo bruto.

Quando o desempenho raycasts contra espaciais superfícies, lembre-se de que estas superfícies costumam ser complexas, o desorganizado formas completos dos detalhes pouco confusos - apenas como sua mesa! Isso significa que um único raycast geralmente é insuficiente para lhe dar informações suficientes sobre a forma da superfície e a forma de espaço vazio próximo a ele. Ele é, portanto, geralmente uma boa ideia para realizar muitas raycasts dentro de uma área pequena e usar os resultados de agregação para derivar uma compreensão mais confiável da superfície. Por exemplo, usando a média de 10 raycasts guia holograma posicionamento em uma superfície produzirá um resultado menor 'trêmulo' e muito mais suave que usando apenas um único raycast.

No entanto, tenha em mente que cada raycast pode ter um alto custo computacional. Assim, dependendo do cenário de uso você deve compensar o custo computacional de raycasts adicionais (executada a cada quadro) contra o custo computacional da [processamento de malha](spatial-mapping.md#mesh-processing) suave e remover buracos em superfícies espacial ( executada quando as malhas espaciais são atualizadas).

## <a name="troubleshooting"></a>Solução de problemas
* Para as malhas de superfície sejam corretamente na orientação, cada GameObject precisa estar ativo antes de serem enviado para o SurfaceObeserver ter sua malha construída. Caso contrário, as malhas aparecerão em seu espaço, mas girado em ângulos estranhos.
* O GameObject que executa o script que se comunica com o SurfaceObserver precisa ser definido para a origem. Caso contrário, todos os GameObjects que você crie e envie para o SurfaceObserver ter suas malhas construídas terá um deslocamento igual ao deslocamento do objeto pai do jogo. Isso pode tornar seu malhas aparecem várias metros de distância que torna muito difícil de depurar o que está acontecendo.

## <a name="see-also"></a>Consulte também
* [Sistemas de coordenadas](coordinate-systems.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Design de mapeamento espacial](spatial-mapping-design.md)
* [Estudo de caso - examinando buracos na sua realidade](case-study-looking-through-holes-in-your-reality.md)

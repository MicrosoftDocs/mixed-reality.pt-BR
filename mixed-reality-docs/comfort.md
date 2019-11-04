---
title: Conforto
description: Durante a visualização natural, o sistema visual humano se baseia em várias fontes de informações, ou "indicações", para interpretar formas 3D e a posição relativa de objetos.
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: Realidade misturada, design, conforto, HoloLens 2, HoloLens (1º gen)
ms.openlocfilehash: e71b8d73a37a5d10a07d37d91cf14c88b7a85687
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436388"
---
# <a name="comfort"></a>Conforto

Durante a visualização natural, o sistema visual humano conta com várias fontes de informações, ou "indicações", para interpretar as formas 3D e as posições relativas dos objetos. Algumas indicações se baseiam apenas em um único olho (indicações de monocular), incluindo [perspectiva linear](https://en.wikipedia.org/wiki/Perspective_(graphical)), [tamanho familiar](https://en.wikipedia.org/wiki/Size#Perception_of_size), oclusão, [Desfoque de profundidade de campo](https://en.wikipedia.org/wiki/Depth_of_field)e [acomodação](https://en.wikipedia.org/wiki/Accommodation_(eye)). Outras indicações dependem de ambos os olhos (pistas de binóculo) e incluem [Vergence](https://en.wikipedia.org/wiki/Vergence) (essencialmente as rotações relativas dos olhos necessários para examinar um objeto) e a [disparidade de binóculo](https://en.wikipedia.org/wiki/Stereopsis) (o padrão de diferenças entre as projeções da cena no de trás dos dois olhos). Para garantir o máximo de conforto em capacetes de realidade virtual, é importante que os designers e os desenvolvedores criem e apresentem conteúdo de forma a imitar como essas indicações funcionam no mundo natural. Do ponto de vista físico, também é importante projetar conteúdo que não exija movimentos fatiguings do pescoço ou dos braços. Neste artigo, abordaremos as principais considerações que você deve ter em mente para atingir essas metas.

## <a name="vergence-accommodation-conflict"></a>Vergence-conflito de acomodação

Para exibir os objetos claramente, os seres humanos devem [acomodar](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)ou ajustar o foco dos seus olhos até a distância do objeto. Ao mesmo tempo, a rotação de ambos os olhos deve [convergir](https://en.wikipedia.org/wiki/Convergence_(eye)) para a distância do objeto para evitar a exibição de imagens duplas. Na exibição natural, Vergence e acomodação são vinculados. Quando você exibe algo próximo (por exemplo, um housefly perto do seu nariz), seus olhos se cruzam e acomodam a um ponto próximo. Por outro lado, se você exibir algo em um infinito (aproximadamente começando em 6 minutos ou mais distante para visão normal), as linhas de visão dos olhos se tornarão paralelas e as lentes dos seus olhos se acomodam ao infinito. 

Na maioria dos monitores, os usuários serão sempre acomodados na distância focal da tela (para obter uma imagem nítida), mas convergem para a distância do objeto de interesse (para obter uma única imagem). Quando os usuários acomodam e convergem para distâncias diferentes, o link natural entre as duas indicações deve ser quebrado e isso pode levar ao Visual discomfort ou fadiga.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos Holographic

Os vídeos do HoloLens são corrigidos a uma distância óptica de aproximadamente 2,0 m para longe do usuário. Portanto, os usuários sempre devem acomodar quase 2,0 m para manter uma imagem clara no dispositivo. Os desenvolvedores de aplicativos podem guiar onde os olhos dos usuários convergem colocando o conteúdo e os hologramas em várias profundidades. O discomfort do conflito Vergence pode ser evitado ou minimizado, mantendo o conteúdo ao qual os usuários convergem o mais próximo de 2,0 m quanto possível (ou seja, em uma cena com muito profundidade, coloque as áreas de interesse perto de 2,0 m do usuário quando possível). Quando o conteúdo não pode ser colocado perto de 2,0 m, discomfort do conflito Vergence é maior quando o olhar do usuário alterna entre distâncias diferentes. Em outras palavras, é muito mais confortável examinar um holograma estacionário que permaneça 50cm longe do que examinar uma 50cm de holograma que se move para frente e para fora de você ao longo do tempo.

![a distância ideal para colocar os hologramas do usuário.](images/distanceguiderendering-950px.png)<br>
*Distância ideal para colocar os hologramas do usuário*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Práticas recomendadas para o HoloLens (1º gen) e o HoloLens 2

Para maior conforto, **a zona ideal para posicionamento de holograma é entre 1,25 m e 5 min**. Em todos os casos, os designers devem tentar estruturar cenas de conteúdo para encorajar os usuários a interagir com 1 milhão ou longe do conteúdo (por exemplo, ajustar o [tamanho do conteúdo e os parâmetros de posicionamento padrão](gaze-and-commit.md)). 

Embora o conteúdo possa ocasionalmente precisar ser exibido em mais de 1 milhão, é recomendável que você já apresente os hologramas mais próximos de 40cm. Portanto, é recomendável começar a **esmaecer o conteúdo em 40cm e colocar um plano de recorte de renderização em 30cm** para evitar objetos mais próximos.

Os objetos que se movem em profundidade são mais prováveis do que os objetos estacionários para produzir discomfort devido ao conflito de Vergence. Da mesma forma, exigir que os usuários alternem rapidamente entre o foco próximo e o foco (por exemplo, devido a um holograma pop-up que exija interação direta) podem causar Visual discomfort e fadiga. Portanto, **deve-se tomar cuidado extra para minimizar a frequência com que os usuários estão: exibindo o conteúdo que está se movendo em profundidade; ou alternando rapidamente o foco entre os hologramas próximos e distantes**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Considerações adicionais para o HoloLens 2 e distâncias de interação próxima

Ao criar conteúdo para interação direta (Near) no HoloLens 2, ou **em qualquer aplicativo em que o conteúdo deva ser posicionado mais de 1m, deve-se tomar cuidado extra para garantir o conforto do usuário**. As chances de discomfort devido ao conflito entre Vergence aumentam exponencialmente com a redução da distância da exibição. Além disso, os usuários podem enfrentar um aumento de desfoque ao exibir o conteúdo em distâncias de interação próxima, portanto, é recomendável testar o conteúdo renderizado na zona de posicionamento ideal de holograma, bem como mais próximo (menos de 1,0 m para o plano de recorte) para Certifique-se de que ele permaneça claro e confortável para exibir. 

É **recomendável criar um "orçamento de profundidade" para aplicativos com base na quantidade de tempo que um usuário deve exibir o conteúdo próximo (menos de 1,0 m) e se mover em profundidade**. Um exemplo é evitar colocar o usuário nessas situações mais de 25% do tempo. Se o orçamento de profundidade for excedido, recomendamos um teste de usuário cuidadoso para garantir que ele permaneça uma experiência confortável. 

Em geral, também recomendamos testes cuidadosos para garantir que todos os requisitos de interação (por exemplo, velocidade de movimentação, acessibilidade, etc.) em distâncias de interação ao mesmo tempo permaneçam confortáveis para os usuários. 


### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos de imersão

Para dispositivos de imersão, as diretrizes e práticas recomendadas para o HoloLens ainda se aplicam, mas os valores específicos para a zona de conforto são deslocados dependendo da distância focal da exibição. Em geral, as distâncias focal para essas telas estão entre 1,25 m e 2,5 m. Em caso de dúvida, evite renderizar objetos de interesse muito próximos dos usuários e, em vez disso, tente manter a maior parte do conteúdo 1 ou mais distante.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distância interpupillary e deslocamento vertical

Ao exibir o conteúdo digital nas exibições montadas no cabeçalho (HMD), a posição dos olhos de um visualizador em relação à posição de exibição do conteúdo digital é crítica. Especificamente, a Interpupillary Distance ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) e o deslocamento vertical (VO) são importantes para a exibição confortável do conteúdo digital em HMDs. 

O IPD se refere à distância entre o Pupils ou os centros dos olhos de um indivíduo. O VO se refere ao deslocamento vertical potencial do conteúdo digital mostrado para cada olho relativo ao eixo horizontal dos olhos do visualizador (notavelmente, isso não é o mesmo que o deslocamento horizontal ou a disparidade de binóculo). A correspondência de mis ou ambos os fatores para um usuário individual podem worsen os efeitos da discomfort causada pelo conflito de Vergence de acomodação, mas pode até mesmo causar discomfort quando um conflito é minimizado (por exemplo, para o conteúdo exibido no focal de 2,0 m distância do HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos Holographic

#### <a name="hololens-1st-gen"></a>HoloLens (1ª geração)

Para o HoloLens (1º gen), o IPD é estimado e definido durante a [calibragem](calibration.md)do dispositivo. Para novos usuários para um dispositivo já configurado, a calibragem deve ser executada ou o IPD deve ser definido manualmente. O VO depende totalmente do ajuste do dispositivo. Especificamente, para minimizar o VO, o dispositivo precisa ser posicionado na cabeça de um usuário, de modo que os monitores sejam nivelados com o eixo de seus olhos. 

#### <a name="hololens-2"></a>HoloLens 2

Para o HoloLens 2, o IPD é estimado e definido durante o olho/ [calibragem](calibration.md)do dispositivo. Para novos usuários para um dispositivo já configurado, a calibragem deve ser executada para garantir que o IPD esteja definido corretamente. O VO é contabilizado automaticamente no HoloLens 2. 

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos de imersão

O Windows Mixed Realm HMDs de imersão não têm nenhuma calibragem automática para IPD ou VO. O IPD pode ser definido manualmente no software (em configurações do portal de realidade misturada, confira [calibragem](calibration.md)) ou alguns HMDs têm um controle deslizante mecânico que permite ao usuário ajustar o espaçamento das lentes para uma posição confortável (ou seja, que corresponda aproximadamente ao seu IPD). 

## <a name="rendering-rates"></a>Taxas de renderização

Os aplicativos de realidade misturada são exclusivos porque os usuários podem se mover livremente no mundo e interagir com conteúdo virtual como se fossem objetos reais. Para manter essa impressão, é essencial renderizar os hologramas para que eles pareçam estáveis no mundo e sejam animados sem problemas. A renderização de, no [mínimo, 60 quadros por segundo (FPS)](understanding-performance-for-mixed-reality.md) ajuda a atingir essa meta. Há alguns dispositivos de realidade misturados que dão suporte à renderização em quadros de taxas maiores que 60 FPS e para esses dispositivos é altamente recomendável renderizar nas taxas de quadros mais altas para fornecer uma experiência de usuário ideal.

**Aprofundando-se**

Para desenhar hologramas para parecer [que eles são estáveis no mundo real ou virtual](hologram-stability.md), os aplicativos precisam renderizar imagens da posição do usuário. Como a renderização de imagem leva tempo, o HoloLens e outros dispositivos do Windows Mixed Reality preveem onde o cabeçalho de um usuário será quando as imagens forem mostradas nas exibições. Esse algoritmo de previsão é uma aproximação. Os algoritmos de realidade mista do Windows e o hardware ajustam a imagem renderizada para considerar a discrepância entre a posição de cabeçalho prevista e a posição real. Esse processo faz com que a imagem vista pelo usuário apareça como se fosse processada do local correto, e os hologramas sentem-se estáveis. As atualizações funcionam melhor para pequenas alterações na posição de cabeçalho e não podem considerar completamente algumas diferenças de imagem renderizadas, como as causadas por motion-da Parallax.

**Ao renderizar uma taxa de quadros mínima de 60 FPS, você está fazendo duas coisas para ajudar a tornar os hologramas estáveis:**
1. Reduzir a aparência do judder, que é caracterizado por imagens duplas e de movimento desiguais. O movimento de holograma mais rápido e as taxas de renderização mais baixas estão associados a um judder mais pronunciado. Portanto, a busca de sempre manter 60 FPS (ou a taxa máxima de renderização do seu dispositivo) ajudará a evitar judder para a movimentação de hologramas.
2. Minimizando a latência geral. Em um mecanismo com um thread de jogo e um thread de renderização em execução no atrelada, a execução em 30FPS pode adicionar 33,3 ms de latência extra. Ao reduzir a latência, isso diminui o erro de previsão e aumenta a estabilidade do holograma.

**Análise de desempenho**

Há uma variedade de ferramentas que podem ser usadas para avaliar a taxa de quadros de seu aplicativo, como:
* GPUView
* Depurador de gráficos do Visual Studio
* Os criação de perfil criados em mecanismos 3D, como o depurador de quadros no Unity

## <a name="self-motion-and-user-locomotion"></a>Locomotion de automovimento e usuário

A única limitação é o tamanho do seu espaço físico; Se você quiser permitir que os usuários se movimentem mais distantes no ambiente virtual do que em suas salas reais, uma forma de um movimento puramente virtual deverá ser implementada. No entanto, o movimento virtual sustentado que não corresponde ao movimento físico real do usuário pode, muitas vezes, induzir sicknesss de movimento. Esse resultado se deve às *indicações visuais* para o Automotion do *mundo virtual* em conflito com as indicações de [vestibular](https://en.wikipedia.org/wiki/Vestibular_system) para o Automotion proveniente do *mundo real*.

Felizmente, há dicas para implementar Locomotion de usuário que podem ajudar a evitar o problema:
* Sempre coloque o usuário no controle de seus movimentos; o Automotion inesperado é particularmente problemático
* Os seres humanos são muito sensíveis à direção da gravidade. Portanto, os movimentos verticais não iniciados pelo usuário, especialmente, devem ser evitados.

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos Holographic

Um método para permitir que o usuário se mova para outro local em um grande ambiente virtual é dar a impressão de que eles estão movendo um pequeno objeto na cena. Esse efeito pode ser obtido da seguinte maneira:
   1. Forneça uma interface na qual o usuário possa selecionar um ponto no ambiente virtual onde deseja mover.
   2. Após a seleção, reduza a renderização da cena para um disco em volta do ponto desejado.
   3. Ao manter o local selecionado, permita que o usuário o mova como se fosse um objeto pequeno. O usuário pode mover a seleção perto de seus pés.
   4. Após a desseleção, retome a renderização da cena inteira.

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos de imersão

A abordagem do dispositivo Holographic anterior não funciona bem em um dispositivo de imersão porque requer que o aplicativo processe um grande preto vazio ou outro ambiente padrão ao mover o "disco". Esse tratamento interrompe uma ideia de imersão. Um truque para o usuário locomotion em um headset de imersão é a abordagem "piscar". Essa implementação fornece ao usuário controle sobre o seu movimento e oferece uma breve impressão da movimentação, mas faz com que seja tão breve que o usuário tem menos probabilidade de se sentir desorientado pelo Automotion virtual:
   1. Forneça uma interface na qual o usuário possa selecionar um ponto no ambiente virtual onde deseja mover.
   2. Na seleção, comece um movimento simulado (100 m/s) muito rápido em direção a esse local enquanto reduza rapidamente a renderização.
   3. Esmaecer a renderização novamente depois de concluir a tradução.

## <a name="heads-up-displays"></a>Exibições de cabeçotes

No shooter videogames, a HUDs (exibição de cabeçotes-up) apresenta informações persistentes como, por exemplo, integridade do jogador, mini-mapas e inventários diretamente na tela. HUDs funcionam bem para manter o jogador informado sem invasos na experiência de jogos. Em experiências de realidade misturada, o HUDs tem o potencial de causar discomfort significativas e deve ser adaptado para o contexto mais imersiva. Especificamente, HUDs que são rigidamente bloqueados para a orientação da cabeça do usuário provavelmente produzirão discomfort. Se um aplicativo exigir um HUD, recomendamos o bloqueio de *corpo* em vez do bloqueio de cabeçalho. Esse tratamento pode ser implementado como um conjunto de exibições que se convertem imediatamente com o usuário, mas não giram com a cabeça do usuário até que um limite de rotação seja atingido. Depois que essa rotação é alcançada, o HUD pode se reorientar para apresentar as informações dentro do campo de exibição do usuário. A implementação da rotação de 1:1 HUD e da conversão em relação aos movimentos de cabeçalho do usuário sempre deve ser evitada.

## <a name="text-legibility"></a>Legibilidade do texto

A legibilidade do texto ideal pode ajudar a reduzir os olhos e manter o conforto do usuário, especialmente em aplicativos ou cenários que exigem que os usuários leiam em um HMD. A legibilidade do texto depende de uma variedade de fatores, incluindo várias propriedades de exibição (por exemplo, densidade de pixel, brilho, contraste), propriedades de lentes (por exemplo, desvio aberração) e propriedades de texto/fonte (por exemplo, a fonte específica características como peso, espaçamento, serifas, etc., cor da fonte, cor do plano de fundo).  

Em geral, é recomendável testar aplicativos específicos para legibilidade e tornar os tamanhos de fonte tão grandes quanto são viáveis para uma experiência confortável. Abaixo, oferecemos orientações gerais como um ponto de partida para o desenvolvimento. Observe que todos os tamanhos de fonte são relatados em graus de [ângulo visual](https://en.wikipedia.org/wiki/Visual_angle) em vez de tamanhos físicos específicos, que fornece orientação para qualquer distância na zona de posicionamento ideal de holograma, pois ele conta o tamanho do texto e a distância que ele aparece para o visualizador. 

Consulte [tipografia](typography.md) e [texto em](text-in-unity.md) páginas do Unity para obter diretrizes mais detalhadas.

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos Holographic

Para dispositivos Holographic, a renderização de texto preto/escuro em um plano de fundo branco/leve fornece a taxa de contraste mais consistente, pois o plano de fundo occlude a interferência do mundo real por trás da renderização. A renderização de texto branco/leve em um plano de fundo preto/escuro permite que mais de um ambiente do mundo real apareça, o que pode interferir na legibilidade do texto. 

#### <a name="hololens-1st-gen"></a>HoloLens (1ª geração)

O tamanho mínimo de fonte legível (medindo de linha de base de fonte para ascendente) é de aproximadamente 0,35 ° e um tamanho de fonte confortável é de, pelo menos, aproximadamente 0,5 ° para ler o conteúdo apresentado a uma distância de 2 milhões para o usuário. 

#### <a name="hololens-2"></a>HoloLens 2

O tamanho mínimo de fonte legível (medindo de linha de base de fonte para ascendente) é pelo menos aproximadamente: 
   - 0.4 ° a 0,5 ° a 45cm (distância de manipulação direta) 
   - 0.35 °-0,4 ° às 2,0 m
   
O tamanho de fonte legível confortavelmente (medindo de linha de base de fonte para ascendente) é pelo menos aproximadamente: 
   - 0.65 ° a 0,8 ° a 45cm (distância de manipulação direta)
   - 0,6 ° a 0,75 ° às 2,0 m

Observe que os tamanhos de fonte precisam ser um pouco maiores para o texto em distâncias de manipulação direta devido ao conflito de Vergence descrito acima (os olhos dos usuários são acomodados a uma distância de 2,0 m na tela do HoloLens, portanto, o conteúdo renderizado em, por exemplo, 45cm pode parecer mais desfoque para os usuários). 

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos de imersão

Os dispositivos de imersão geralmente têm taxas de contraste mais altas devido à oclusão completa do ambiente externo, mas podem ter uma densidade de pixel mais baixa em parte devido à ampliação das lentes na frente das telas. 

Para a HMDs de imersão de realidade mista do Windows, o tamanho mínimo da fonte vertical legível (medindo da linha de base para ascendente) é de aproximadamente 0,7-0,9 ° e um tamanho de fonte vertical confortável é de aproximadamente 1,0 ° para ler o conteúdo apresentado a uma distância de 2 a usuário.

## <a name="gaze-direction"></a>Direção do olhar

Para evitar que o conteúdo de olho e de pescoço deva ser projetado para que os movimentos de olho e pescoço excessivos sejam evitados.
* **Evitar** ângulos de olhar mais de 10 graus acima do horizonte (movimento vertical)
* **Evite** ângulos olhar mais de 60 graus abaixo do horizonte (movimento vertical)
* **Evitar** rotações de pescoço com mais de 45 graus fora do centro (movimento horizontal)

O ângulo de olhar ideal (repouso) é considerado entre 10-20 graus abaixo da horizontal, pois a cabeça tende a inclinar ligeiramente para baixo, especialmente durante as atividades.

![FOV (campo de exibição) permitido conforme determinado pelo intervalo de movimento do pescoço](images/optimal-field-of-view-2.png)<br>
*FOV (campo de exibição) permitido conforme determinado pelo intervalo de movimento do pescoço*

## <a name="arm-positions"></a>Posições do ARM

Capacidade fadiga pode se acumular quando espera-se que os usuários tenham uma mão levantada durante toda a duração de uma experiência. Ele também pode ser fatiguing para exigir que o usuário faça gestos de toque de ar repetidamente por longas durações. Portanto, recomendamos que as experiências evitem exigir entradas de gesto constantes e repetidas. Essa meta pode ser obtida incorporando pequenas interrupções ou oferecendo uma mistura de gesto e entrada de fala para interagir com o aplicativo.

## <a name="see-also"></a>Consulte também
* [Foco](gaze-and-commit.md)
* [Estabilidade do holograma](hologram-stability.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Quadro holográfico](holographic-frame.md)
* [Calibragem](calibration.md)

---
title: Conforto
description: Durante a visualização natural, o sistema visual humano depende de várias fontes de informação, ou "indicações", para interpretar formas 3D e a posição relativa dos objetos.
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: Realidade, design, misturada conforto, HoloLens 2, HoloLens (1ª geração)
ms.openlocfilehash: 8dea3765f01a6a82fccc002d1cd5c7c9c77d0980
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974774"
---
# <a name="comfort"></a>Conforto

Durante a visualização natural, o sistema visual humano depende de várias fontes de informação, ou "indicações", para interpretar formas 3D e as posições relativas dos objetos. Algumas indicações contam somente com um único olho (monocular indicações), incluindo [perspectiva linear](https://en.wikipedia.org/wiki/Perspective_(graphical)), [tamanho familiar](https://en.wikipedia.org/wiki/Size#Perception_of_size), oclusão, [campo profundidade desfoque](https://en.wikipedia.org/wiki/Depth_of_field), e [ acomodação](https://en.wikipedia.org/wiki/Accommodation_(eye)). Outras indicações contam com ambos os olhos (indicações binocular) e incluir [vergence](https://en.wikipedia.org/wiki/Vergence) (essencialmente as rotações relativas dos olhos necessários para examinar o objeto) e [disparidade binocular](https://en.wikipedia.org/wiki/Stereopsis) (o padrão de diferenças entre as projeções da cena na parte de trás dos duas olhos). Para garantir o máximo conforto no controlava head, é importante para designers e desenvolvedores criar e apresentar o conteúdo de uma maneira que simule como essas indicações operam no mundo natural. De uma perspectiva de física, também é importante projetar o conteúdo que não exija fatiguing movimentos do pescoço ou braços. Neste artigo, vamos examinar as considerações importantes para ter em mente para atingir essas metas.

## <a name="vergence-accommodation-conflict"></a>Conflito de acomodação vergence

Para exibir objetos claramente, seres humanos devem [acomodar](https://en.wikipedia.org/wiki/Accommodation_%28eye%29), ou ajustar o foco dos seus olhos para a distância do objeto. Ao mesmo tempo, a rotação de ambos os olhos deve [convergem](https://en.wikipedia.org/wiki/Convergence_(eye)) à distância do objeto para impedir a exibição de imagens de double. Na exibição natural, vergence e acomodação estão vinculadas. Quando você exibir algo perto (por exemplo, um housefly perto o nariz) seus olhos cruzam e acomodar a um ponto de near. Por outro lado, se você exibir algo em mídia óptico infinito (aproximadamente começando em 6 minutos ou mais distante para visão normal), linhas diretas dos seus olhos se tornam paralelas e lentes dos seus olhos acomodar até o infinito. 

No cabeçalho controlava mais usuários irão conter sempre à distância focal da tela (para obter uma imagem sharp), mas convergem para a distância do objeto de interesse (para obter uma única imagem). Quando os usuários acomodam e convergem para distâncias diferentes, o link natural entre as duas indicações deve ser interrompido e isso pode levar a discomfort visual ou fadiga.

<br>

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos holographic

HoloLens exibe é corrigidos em uma distância óptica aproximadamente 2.0m do usuário. Assim, os usuários sempre devem acomodar quase 2.0m para manter uma imagem clara no dispositivo. Os desenvolvedores de aplicativos podem guiar onde convergirem os olhos dos usuários, colocando o conteúdo e hologramas na intensidades de vários. Discomfort conflito vergence acomodação pode ser evitada ou minimizada, mantendo o conteúdo para o qual os usuários convergirem mais próximo m 2.0 possível (ou seja, em uma cena com muita intensidade, coloque as áreas de interesse próximo 2.0 m do usuário quando possível). Quando o conteúdo não pode ser colocado perto 2.0 m, discomfort conflito vergence acomodação é maior quando olhar do usuário vai e volta entre distâncias diferentes. Em outras palavras, é muito mais à vontade examinar um holograma estacionário que permanece 50cm distante ao examinar um holograma 50cm distância que se move na direção e afastada de você ao longo do tempo.

![Distância ideal para posicionamento hologramas do usuário.](images/distanceguiderendering-950px.png)<br>
*Distância ideal para posicionamento hologramas do usuário*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Práticas recomendadas para o HoloLens (1º gen) e 2 do HoloLens

Para o máximo conforto, **a zona ideal para posicionamento holograma está entre m 1,25 e 5M**. Em todos os casos, designers devem tentar cenas de conteúdo de estrutura para encorajar os usuários interajam 1 milhão ou mais longe o conteúdo (por exemplo, ajustar [padrão parâmetros de posicionamento e tamanho do conteúdo](gaze-targeting.md)). 

Embora o conteúdo, ocasionalmente, talvez precise ser exibido em menos de 1 milhão, é recomendável nunca apresentando hologramas mais perto de 40cm. Portanto, é recomendável começar a **esmaecer o conteúdo em 40cm e a colocação de um plano de recorte de renderização em 30cm** para evitar qualquer mais próximo de objetos.

Objetos que se movem em camadas serão mais prováveis que os objetos estáticos para produzir discomfort devido a conflito de acomodação vergence. Da mesma forma, exigir que os usuários alternar rapidamente entre foco próximo e distante de foco (por exemplo, devido a um pop-up holograma exigir interação direta) pode causar fadiga e discomfort visual. Portanto, **extra deve ter cuidado para minimizar a frequência com que os usuários são: exibindo o conteúdo que está se movendo em profundidade; ou rapidamente alternar o foco entre hologramas próximos e distantes**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>Considerações adicionais para o HoloLens 2 e ao lado de distâncias de interação

Durante a criação de conteúdo diretamente a (interação em 2 HoloLens, quase) ou **em todos os aplicativos em que o conteúdo deve ser colocado mais próximo do que 1 milhão, extra tome cuidado para garantir que o conforto do usuário**. A probabilidade de discomfort devido a conflito de acomodação vergence aumenta exponencialmente com diminuindo a distância de visualização. Além disso, os usuários podem enfrentar maior bluriness quando visualizar o conteúdo em quase distâncias de interação, portanto, é recomendável que o teste de conteúdo renderizado ambos dentro da zona de posicionamento de holograma ideal, bem como mais próximo (menor que 1,0 m para baixo até o plano de corte) para Certifique-se de que ele permanecerá clara e à vontade exibir. 

**É recomendável criar um "budget profundidade" para aplicativos com base na quantidade de tempo de espera-se que um usuário exibir o conteúdo que está próxima (menor que 1.0 m) e mover em profundidade**. Um exemplo é para evitar colocar o usuário nessas situações mais de 25% do tempo. Se o orçamento de profundidade for excedido, recomendamos que você teste do usuário cuidado para garantir que ele permaneça uma experiência confortável. 

Em geral, é recomendável também cuidadoso de testes para garantir a quaisquer requisitos de interação (por exemplo, velocidade do movimento, acessibilidade, etc.) em quase distâncias de interação permanecem à vontade para os usuários. 


### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos de imersão

Para dispositivos imersivos, as diretrizes e práticas recomendadas para HoloLens ainda se aplica, mas os valores específicos para a zona de conforto são deslocados dependendo da distância focal para a exibição. Em geral, as distâncias focal para estes vídeos são entre 1,25 a 2,5 milhões. Em caso de dúvida, evitar o processamento de objetos de interesse muito próximo aos usuários e em vez disso, tentam manter a maior parte do conteúdo 1 milhão ou mais distantes.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distância interpupillary e o deslocamento vertical

Quando a exibição de conteúdo digital na cabeça montado exibe (HMD), a posição dos olhos do visualizador em relação a posição de exibição de conteúdo digital é essencial. Especificamente, ambas as distância interpupillary ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) e o deslocamento vertical (VO) são importantes para a exibição de conteúdo digital no HMDs confortável. 

IPD refere-se à distância entre a alunos ou centros de olhos de um indivíduo. VO refere-se ao potencial deslocamento vertical do conteúdo digital mostrado para cada olho em relação ao eixo horizontal dos olhos do visualizador (particularmente, isso não é o mesmo como o deslocamento horizontal ou disparidade binocular). Correspondência incorretamente um ou ambos esses fatores para um usuário individual pode agravar os efeitos de discomfort causado por um conflito de acomodação vergence, mas ele pode até mesmo causa discomfort quando V um conflito é minimizado (por exemplo, para o conteúdo exibido no m 2.0 focal distância do HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos holographic

#### <a name="hololens-1st-gen"></a>HoloLens (1ª geração)

Para o HoloLens (1º gen), IPD é estimada e definido durante o dispositivo [calibragem](calibration.md). Novos usuários já definido o dispositivo, deve ser executada a calibragem ou IPD deve ser definido manualmente. VO depende inteiramente do dispositivo que se ajustar. Especificamente, para minimizar VO, o dispositivo precisa ser pairando sobre cabeça de um usuário, de modo que as exibições são o nível com o eixo de seus olhos. 

#### <a name="hololens-2"></a>HoloLens 2

2 HoloLens, IPD é estimada e definido durante a dispositivo/olho [calibragem](calibration.md). Novos usuários já definido o dispositivo, calibração deve ser executada para garantir IPD está definida corretamente. VO é contabilizada automaticamente no HoloLens 2. 

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos de imersão

Windows Mixed Reality HMDs de imersão não tem nenhum calibragem automática para o IPD ou VO. IPD pode ser definido manualmente no software (em configurações do Portal de realidade mista, consulte [calibragem](calibration.md)), ou algumas HMDs tem um controle deslizante mecânico que permite ao usuário ajustar o espaçamento entre as lentes para uma posição confortável (ou seja, ou aproximadamente corresponde a seu IPD). 

## <a name="rendering-rates"></a>Taxas de processamento

Aplicativos de realidade misturada são exclusivos, porque os usuários podem ser movidos livremente no mundo e interagir com conteúdo virtual como como se fossem objetos reais. Para manter essa impressão, é essencial para renderizar hologramas para que eles aparecem estáveis do mundo e animar suavemente. Processamento em um [mínimo de 60 quadros por segundo (FPS)](understanding-performance-for-mixed-reality.md) ajuda a atingir esse objetivo. Há alguns dispositivos de realidade mista que dão suporte à renderização no framerates maior do que 60 FPS e para esses dispositivos é altamente recomendável para renderizar no framerates maior para fornecer uma excelente experiência do usuário.

**Mergulhando mais fundo**

Para desenhar hologramas a aparência [estiver estáveis do mundo real ou virtual](hologram-stability.md), os aplicativos precisam renderizar imagens da posição do usuário. Uma vez que a renderização de imagem leva tempo, HoloLens e outros dispositivos de realidade mista do Windows preveem onde cabeça de um usuário será quando as imagens são mostradas no exibe. Esse algoritmo de previsão é uma aproximação. Hardware e os algoritmos de Windows Mixed Reality ajustam a imagem renderizada para levar em conta a discrepância entre a posição de cabeçalho prevista e a posição de cabeçalho real. Esse processo faz com que a imagem vista pelo usuário aparecem como se ela tiver sido renderizada no local correto e hologramas se sentir estáveis. As atualizações funcionam melhor para pequenas alterações na posição principal, e eles não consegue contabilizar algumas diferenças de imagem renderizada, como aquelas causadas por movimento parallax completamente.

**Por renderização em uma taxa de quadros mínimo de 60 FPS, você está fazendo duas coisas para ajudar a tornar estável vntana:**
1. Reduzindo a aparência de judder, que é caracterizado por movimento irregular e imagens duplas. Movimento de holograma mais rápido e renderização inferior taxas estão associadas com mais evidentes judder. Portanto, se esforçam para manter sempre 60 FPS (ou taxa de renderização máxima do dispositivo) ajudará a evitar judder para mover hologramas.
2. Minimizar a latência geral. Em um mecanismo com um jogo e um thread de renderização em execução ao mesmo tempo, em execução em 30FPS pode adicionar 33.3ms de latência adicional. Reduzindo a latência, isso diminui o erro de previsão e aumenta a estabilidade do holograma.

**Análise de desempenho**

Há uma variedade de ferramentas que podem ser usados para avaliar o desempenho de sua taxa de quadros do aplicativo, como:
* GPUView
* Depurador de gráficos do Visual Studio
* Os criadores de perfil incorporados a mecanismos de 3D, como o depurador do quadro no Unity

## <a name="self-motion-and-user-locomotion"></a>O motion Self e locomotion do usuário

A única limitação é o tamanho do seu espaço físico; Se você quiser permitir que os usuários afastar no ambiente virtual do que em suas salas real, um formulário de movimento puramente virtual deve ser implementado. No entanto, sustentado movimento virtual que não corresponde ao movimento de real, físico do usuário geralmente pode induzir movimento doença. Esse resultado é devido à *indicações visuais* para Self de movimento do *mundo virtual* em conflito com o [indicações vestibular](https://en.wikipedia.org/wiki/Vestibular_system) para Self de movimento, provenientes da *reais*.

Felizmente, existem dicas para implementar locomotion de usuário que pode ajudar a evitar o problema:
* Sempre colocar o usuário no controle de seus movimentos; inesperado automática de movimento é particularmente problemático
* Os seres humanos são muito sensíveis a direção da gravidade. Portanto, iniciada pelo usuário verticais movimentos especialmente devem ser evitados.

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos holographic

Um método para permitir que o usuário mover para outro local em um grande ambiente virtual é para dar a impressão que elas estão mudando um pequeno objeto na cena. Esse efeito pode ser obtido da seguinte maneira:
   1. Fornece uma interface em que o usuário pode selecionar um ponto no ambiente virtual onde eles desejam mover.
   2. Após a seleção, reduza a renderização da cena para baixo até um disco ao redor no ponto desejado.
   3. Enquanto mantém o ponto selecionado, permitir que o usuário movê-la como se fosse um objeto pequeno. O usuário pode, em seguida, mover a seleção perto de seus pés.
   4. Após a deselection, retome a renderização da cena inteira.

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos de imersão

A abordagem de dispositivo holográfica anterior não funciona bem em um dispositivo de imersão porque ele requer que o aplicativo para processar uma grande lacuna preta ou outro ambiente padrão ao mover o "disco". Esse tratamento interrompe um senso de imersão. Um truque para locomotion de usuário em um fone de ouvido imersivo é a abordagem de "intermitência". Essa implementação fornece aos usuários controle sobre seu movimento e fornece uma breve impressão de movimento, mas torna tão breves que o usuário é menos provável se sentir disoriented por puramente virtual automática de movimento:
   1. Fornece uma interface em que o usuário pode selecionar um ponto no ambiente virtual onde eles desejam mover.
   2. Após a seleção, iniciar um movimento muito rápida simulado (100 m/s) para esse local durante o desaparecimento rapidamente a renderização.
   3. A renderização de volta depois de concluir a tradução de esmaecimento.

## <a name="heads-up-displays"></a>Exibe Heads-Up

Tiro em pessoa primeiro videogames, heads-up exibe (HUDs) persistentemente apresentar informações como a integridade do jogador, mini mapas e inventários diretamente na tela. HUDs funcionam bem para manter o jogador informado sem intruso na experiência do jogo. Nas experiências de realidade misturada, HUDs têm o potencial de causar discomfort significativa em devem ser adaptados para o contexto mais imersivo. Especificamente, HUDs são rigidamente bloqueados para orientação de principal do usuário provavelmente produzir discomfort. Se um aplicativo exige um HUD, recomendamos *corpo* bloqueio em vez de bloqueio principal. Esse tratamento pode ser implementado como um conjunto de exibições imediatamente traduzir com o usuário, mas não gira com head do usuário até que um limite de rotação é atingido. Depois que a rotação é obtida, o HUD pode reorientar para apresentar as informações dentro do campo de visão do usuário. Implementação de rotação de HUD 1:1 e tradução em relação ao cabeçalho do usuário movimentos sempre devem ser evitados.

## <a name="text-legibility"></a>Legibilidade do texto

Legibilidade do texto ideal pode ajudar a reduzir os olhos e manter o conforto do usuário, especialmente em cenários que exigem que os usuários ler enquanto estiver em um HMD ou aplicativos. Depende de legibilidade do texto em uma variedade de fatores, incluindo várias propriedades de exibição (por exemplo, densidade de pixels, brilho, contraste), propriedades de lente (por exemplo, o desvio cromático) e propriedades de fonte do texto (por exemplo, a fonte específica características, como peso, espaçamento, serifas, etc., cor da fonte, cor do plano de fundo).  

Em geral, é recomendável testar aplicativos específicos para manter a legibilidade e tornando os tamanhos de fonte tão grande quanto for viável para uma experiência confortável. Abaixo, oferecemos orientações gerais como ponto de partida para o desenvolvimento. Observe que todos os tamanhos de fonte são relatados em graus [ângulo visual](https://en.wikipedia.org/wiki/Visual_angle) em vez de tamanhos específicos de físicos, que fornece diretrizes para qualquer distância dentro da zona de posicionamento holograma ideal porque ela é considerada para os dois o tamanho das texto e a distância é exibida no visualizador. 

### <a name="guidance-for-holographic-devices"></a>Diretrizes para dispositivos holographic

Para dispositivos holográfico, renderização de texto preto/escuro em um plano de fundo branco/leve fornece a taxa de contraste mais consistente porque o plano de fundo será occlude interferência de mundo real por trás de renderização. Processamento de texto em branco/leve em um plano de fundo preto/escuro permite que mais de um ambiente do mundo real para mostrar, que pode interferir na legibilidade do texto. 

#### <a name="hololens-1st-gen"></a>HoloLens (1ª geração)

O tamanho mínimo da fonte legível (medição da linha de base da fonte para ascender) é de aproximadamente 0,35 ° e um tamanho de fonte confortável é pelo menos aproximadamente 0,5 ° para ler o conteúdo apresentado em uma distância de 2m para o usuário. 

#### <a name="hololens-2"></a>HoloLens 2

O tamanho mínimo da fonte legível (medição da linha de base da fonte para ascender) é pelo menos aproximadamente: 
   - 0,4-0,5 ° em 45cm (distância manipulação direta) 
   - 0,35-0,4 ° em m 2.0
   
O tamanho da fonte confortavelmente legível (medição da linha de base da fonte para ascender) é pelo menos aproximadamente: 
   - 0,65-0,8 ° em 45cm (distância manipulação direta)
   - 0,6-0,75 ° em m 2.0

Observe que os tamanhos de fonte precisam ser ligeiramente maior para texto em distâncias de manipulação direta devido a conflito vergence acomodação descrito acima (olhos dos usuários são acomodando a uma distância de m 2.0 na exibição do HoloLens, portanto, o conteúdo renderizado, por exemplo, 45 cm pode parecer mais desfocado aos usuários). 

### <a name="guidance-for-immersive-devices"></a>Diretrizes para dispositivos de imersão

Dispositivos imersivos geralmente têm taxas de contraste mais alto devido à oclusão completa do ambiente externo, mas podem ter mais baixa densidade de pixel efetivo em parte devido a ampliação lentes na frente a exibe. 

Para Windows Mixed Reality HMDs de imersão, o tamanho da fonte de vertical legível mínimo (medição da linha de base da fonte para ascender) é aproximadamente 0,7-0.9 ° e um tamanho confortável fonte vertical é aproximadamente 1.0° para ler o conteúdo apresentado em uma distância de 2m para o usuário.

## <a name="gaze-direction"></a>Mantenha o foco de direção

Para evitar a sobrecarga de olho e pescoço conteúdo deve ser projetado para que movimentações de olho e pescoço excessivas são evitadas.
* **Evite** ângulos de olhar mais de 10 graus acima horizonte (movimento vertical)
* **Evite** ângulos de olhar mais de 60 graus abaixo o horizonte (movimento vertical)
* **Evite** rotações do pescoço mais de 45 graus fora do centro (movimento horizontal)

O ângulo de olhar (repouso) ideal é considerado entre 10 a 20 graus abaixo horizontal, conforme a cabeça tende a inclinação para baixo um pouco, especialmente durante as atividades.

![Campo de visão permitido (FOV), conforme determinado pelo intervalo do pescoço do movimento](images/optimal-field-of-view-2-750px.png)<br>
*Campo de visão permitido (FOV), conforme determinado pelo intervalo do pescoço do movimento*

## <a name="arm-positions"></a>Posições de ARM

Fadiga músculo pode acumular quando os usuários devem manter uma mão gerada por toda a duração de uma experiência. Ele também pode ser fatiguing para exigir que o usuário faça repetidamente ar toque gestos por longos períodos. Portanto, recomendamos experiências de evitem a necessidade de entrada do gesto de constante, repetidas. Essa meta pode ser feita com a incorporação de quebras de curtas ou oferecendo uma mistura de gestos e fala para interagir com o aplicativo de entrada.

## <a name="see-also"></a>Consulte também
* [Foco](gaze.md)
* [Estabilidade do holograma](hologram-stability.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Quadro holográfico](holographic-frame.md)
* [Calibragem](calibration.md)

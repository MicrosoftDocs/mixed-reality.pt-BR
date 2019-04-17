---
title: Estabilidade holograma
description: HoloLens hologramas se estabilize automaticamente, mas há etapas que os desenvolvedores podem tirar para melhorar a estabilidade do holograma ainda mais.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: hologramas, estabilidade, hololens
ms.openlocfilehash: 9b0227102934650d5640a4ac1c4d6f59ecd8e6dd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589726"
---
# <a name="hologram-stability"></a>Estabilidade holograma

Para obter hologramas estáveis, HoloLens tem um pipeline de estabilização da imagem interna. O pipeline de estabilização funciona automaticamente em segundo plano, portanto, não há nenhuma etapa adicional necessária para habilitá-lo. No entanto, os desenvolvedores devem exercitar técnicas que melhoram a estabilidade de holograma e evitar cenários em que reduzem a estabilidade.

## <a name="hologram-quality-terminology"></a>Terminologia de qualidade holograma

A qualidade do hologramas é um resultado do ambiente boa e desenvolvimento de aplicativos boa. Aplicativos que atingem uma constante 60 quadros por segundo em um ambiente onde o HoloLens podem acompanhar os arredores garantirá que o holograma e o sistema de coordenadas correspondente estejam em sincronia. Da perspectiva do usuário, não serão movido hologramas devem ser estáticos em relação ao ambiente.

Ao ambiente de problemas, as taxas de processamento inconsistentes ou baixa, ou outros problemas de aplicativo aparecer, a seguinte terminologia é útil para identificar o problema.
* **Precisão.** Depois que o holograma é bloqueado pelo mundo e colocado no mundo real, devem permanecer em que ele foi colocado, em relação ao ambiente, independentemente do movimento do usuário ou as alterações de ambiente pequeno e esparsos. Se um holograma é exibido mais tarde em um local inesperado, é um *precisão* problema. Nesses cenários, podem acontecer se duas salas distintas parecem idênticas.
* **Jitter.** Os usuários observam isso como agitando de alta frequência de um holograma. Isso pode acontecer quando degrada o acompanhamento do ambiente. Para os usuários, a solução está em execução [sensor ajuste](sensor-tuning.md).
* **Judder.** As frequências de renderização de baixa resultam em movimento irregular e imagens duplas de hologramas. Isso é particularmente perceptível em hologramas com movimento. Os desenvolvedores precisam manter uma [constante 60 FPS](hologram-stability.md#frame-rate).
* **Descompasso.** Os usuários veem isso como holograma aparece para deixar de onde ele foi colocado originalmente. Isso acontece quando hologramas são colocadas longe da [âncoras espaciais](spatial-anchors.md), especialmente em partes do ambiente que não foram totalmente mapeados. Criar hologramas perto âncoras espaciais reduz a probabilidade de descompasso.
* **Jumpiness.** Quando um holograma "pops" ou "salta" para fora do local ocasionalmente. Isso pode ocorrer como acompanhamento ajusta hologramas para corresponder à compreensão atualizada do seu ambiente.
* **Raias.** Quando um holograma parece sway correspondente para o movimento da cabeça do usuário. Isso ocorre quando não constem hologramas a [plano de estabilização](hologram-stability.md#stabilization-plane), e se o HoloLens não estiver [calibrados](calibration.md) para o usuário atual. O usuário pode executar novamente o [calibragem](calibration.md) aplicativo para corrigir esse problema. Os desenvolvedores podem atualizar o plano de estabilização para aprimorar a estabilidade.
* **Separação de cores.** O exibe no HoloLens é uma exibição em cores sequencial, que flash canais de cor de vermelho-verde-azul-verde a 60Hz (os campos são mostrados a 240Hz cor individual). Sempre que um usuário rastreia um movimentação holograma com suas respectiva olhos, bordas direita e líderes que holograma separar em suas cores constituintes, produzindo um efeito Arco-íris. O grau de separação depende da velocidade do holograma. Em alguns casos raros, movendo aqueles head rapidamente ao examinar um holograma estacionário também pode resultar em um efeito de arco-íris. Isso é chamado  *[separação de cores](hologram-stability.md#color-separation)*.

## <a name="frame-rate"></a>Taxa de quadros

Taxa de quadros é o primeiro pilar da estabilidade holograma. Para hologramas apareçam estável do mundo, cada imagem apresentada ao usuário deve ter as hologramas desenhadas no lugar correto. O exibe na atualização do HoloLens 240 vezes por segundo, Mostrar quatro campos de cor separada para cada recentemente renderizado imagem, resultando em uma experiência de usuário de 60 FPS (quadros por segundo). Para fornecer a melhor experiência possível, os desenvolvedores de aplicativos devem manter 60 FPS, que se traduz em consistentemente fornecendo uma nova imagem para o sistema operacional de cada 16 milissegundos.

**60 FPS** para desenhar hologramas se pareçam com elas residem no mundo real, HoloLens precisa renderizar imagens da posição do usuário. Uma vez que a renderização de imagem leva tempo, HoloLens prevê onde a cabeça de um usuário será quando as imagens são mostradas no exibe. Esse algoritmo de previsão é uma aproximação. HoloLens tem o hardware que ajusta a imagem renderizada à conta a discrepância entre a posição de cabeçalho prevista e a posição de cabeçalho real. Isso faz com que a imagem, o usuário vê aparecem como se ele foi renderizado no local correto e hologramas se sentir estáveis. A imagem atualiza o trabalho melhor com pequenas alterações e não foi possível corrigir certos procedimentos na imagem renderizada como movimento parallax completamente.

Renderizando em 60 FPS, você está fazendo três coisas para ajudar a tornar estáveis hologramas:
1. Minimizar a latência geral entre a renderização de uma imagem e essa imagem sendo vistos pelo usuário. Em um mecanismo com um jogo e um thread de renderização em execução ao mesmo tempo, em execução em 30FPS pode adicionar 33.3ms de latência adicional. Reduzindo a latência, isso diminui o erro de previsão e aumenta a estabilidade do holograma.
2. Tornando-o para que cada imagem atingir a atenção do usuário tenha uma quantidade consistente de latência. Se você renderizar em 30fps, a exibição ainda exibe imagens em 60 FPS. Isso significa que a mesma imagem que será exibida duas vezes em uma linha. O segundo quadro terá 16.6ms latência mais do que o primeiro quadro e precisará corrigir uma quantidade mais pronuncia-se do erro. Essa inconsistência na magnitude de erro pode causar indesejados judder de 60hz.
3. Reduzindo a aparência de judder, que é caracterizado por movimento irregular e imagens duplas. Movimento de holograma mais rápido e renderização inferior taxas estão associadas com mais evidentes judder. Portanto, se esforçam para manter o 60 FPS em todos os tempos de ajudará a evitar judder para um determinado holograma de movimentação.

**Consistência de taxa de quadros** consistência de taxa de quadro é tão importante quanto um alta quadros por segundo. Ocasionalmente descartava quadros são inevitáveis para qualquer aplicativo ricas em conteúdo, e o HoloLens implementa alguns algoritmos sofisticados para se recuperar de falhas ocasionais. No entanto, uma taxa de quadros flutuante constantemente é muito mais notável a um usuário que a execução de forma consistente em taxas de quadro inferiores. Por exemplo, um aplicativo que renderiza sem problemas para 5 quadros (60 FPS durante esses 5 quadros) e, em seguida, descarta todos os outros quadros para os próximos 10 quadros (30 FPS durante essas 10 quadros) aparecerão mais instáveis que um aplicativo ou de forma consistente processa em 30 FPS.

Em uma anotação relacionada, o sistema operacional limitará aplicativos até 30 FPS quando [misto captura realidade](mixed-reality-capture.md) está em execução.

**Análise de desempenho** há uma variedade de ferramentas que podem ser usados para avaliar o desempenho de sua taxa de quadros do aplicativo, como:
* GPUView
* Depurador de gráficos do Visual Studio
* Os criadores de perfil incorporados a mecanismos 3D, como o Unity

## <a name="hologram-render-distances"></a>Distâncias de renderização holograma

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

O sistema visual humano integra-se vários sinais depende da distância quando ele fixates e se concentra em um objeto.
* [Acomodação](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) -o foco de olho individual.
* [Convergência](https://en.wikipedia.org/wiki/Convergence_(eye)) - dois olhos mover para dentro ou para fora para o centro em um objeto.
* [Visão binocular](https://en.wikipedia.org/wiki/Stereopsis) -disparidades entre as imagens de olho de esquerda e direita que são dependentes de distância de um objeto para fora de seu ponto de fixation.
* Sombreamento, tamanho relativo do angular e outras indicações monocular (olho único).

Convergência e acomodação são exclusivas porque são indicações de retina extra relacionadas a como os olhos alterar para perceber objetos em distâncias diferentes. Na exibição natural, a convergência e acomodação estão vinculadas. Quando os olhos exibir algo perto (por exemplo, o nariz) os olhos cruzam e acomodar a um ponto de near. Quando os olhos exibir algo em infinito que os olhos se tornam paralelos e o olho acomode até o infinito. Os usuários vestindo HoloLens sempre acomodará 2.0 m para manter uma imagem clara como o HoloLens exibe são corrigidos em uma distância óptica aproximadamente 2.0m do usuário. Os desenvolvedores de aplicativos controlam onde os olhos dos usuários convergirem colocando conteúdo e hologramas em várias intensidades. Quando os usuários acomodam e convergem para distâncias diferentes, o link natural entre as duas indicações são interrompidas e isso pode levar a discomfort visual ou fadiga, especialmente quando a magnitude do conflito é grande. Discomfort conflito vergence acomodação pode ser evitada ou minimizada, mantendo o conteúdo que os usuários convergem para o mais próximo m 2.0 possível (ou seja, em uma cena com muita intensidade de colocar as áreas de interesse próximo m 2.0 quando possível). Quando o conteúdo não pode ser colocado quase discomfort m 2.0 conflito vergence acomodação é maior quando o usuário do olhares em ambas as direções entre distâncias diferentes. Em outras palavras, é muito mais à vontade examinar um holograma estacionário que permanece 50cm distante ao examinar um holograma 50cm distância que se move na direção e afastada de você ao longo do tempo.

Colocando o conteúdo em m 2.0 também é vantajoso porque as duas exibições são projetadas para se sobrepõem totalmente a essa distância. Para imagens colocadas esse plano, quando eles passam do lado do quadro holográfico eles desaparecerá de um vídeo enquanto ainda visível no outro. Este rivalry binocular pode ser perturbador para a percepção de profundidade do holograma.

**Distância ideal para posicionamento hologramas do usuário**

![Distância ideal para posicionamento hologramas do usuário](images/distanceguiderendering-750px.png)

**Clip-planos** para máximo conforto, recomendamos distância de renderização de recorte em 85 cm com fadeout começando em 1 milhão de conteúdo. Em aplicativos onde hologramas e os usuários são os dois hologramas estáticos podem ser exibidos confortavelmente tão próximo como 50cm. Nesses casos, aplicativos devem colocar um plano de recorte próximo de 30cm e fade out deve ser iniciado pelo menos 10cm para longe do plano de recorte. Sempre que o conteúdo está mais próximo que 85cm é importante garantir que os usuários não são frequentemente mudam mais próximo ou mais distante hologramas ou que hologramas não são frequentemente se aproximar a ou mais distante do usuário conforme essas situações são mais prováveis que causam discomfort das conflito de acomodação vergence. Conteúdo deve ser projetado para minimizar a necessidade de interação mais perto de 85cm do usuário, mas quando o conteúdo deve ser renderizado mais próximo do que uma boa regra geral para desenvolvedores de 85cm é para cenários em que os usuários e/ou hologramas não mova detalhadamente mais do que 25% de t de design ele tempo.

**Práticas recomendadas** quando hologramas não podem ser colocadas em 2 m e não podem ser evitados conflitos entre a convergência e acomodação, a zona ideal para posicionamento holograma é entre 1,25 milhões e milhões de 5. Em todos os casos, designers devem estruturar o conteúdo a fim de incentivar os usuários interajam 1 + m imediatamente (por exemplo, ajustar o tamanho do conteúdo e padrão de parâmetros de posicionamento).

## <a name="stabilization-plane"></a>Plano de estabilização
> [!NOTE]
> Para a área de trabalho fones imersivos em exposição, definir um plano de estabilização é geralmente contraproducente, pois ele oferece menos qualidade visual que fornecer o buffer de profundidade do seu aplicativo para o sistema para habilitar reprojection com base em profundidade por pixel. A menos que em execução em um HoloLens, geralmente você deve evitar definir o plano de estabilização.

HoloLens executa uma técnica de estabilização holográfica sofisticados assistida por hardware. Isso é basicamente automático e tem a ver com o motion e a alteração do ponto de Vista (CameraPose) como a cena é animado e o usuário move suas cabeças. Um único plano chamado plano de estabilização, é escolhido para maximizar a este estabilização. Enquanto todos os hologramas na cena recebem alguns estabilização, hologramas no plano de estabilização recebem a estabilização do máximo de hardware.

![Plano de estabilização para objetos 3D](images/stab-plane-500px.jpg)

O dispositivo tentará automaticamente escolha esse plano, mas o aplicativo pode ajudar nesse processo, selecionando o ponto de foco na cena. Aplicativos do Unity em execução em um HoloLens devem escolher a melhor se concentrar ponto com base na sua cena e passá-la em [SetFocusPoint()](focus-point-in-unity.md). Um exemplo de como definir o ponto de foco no DirectX é incluído no modelo de cubo de rotação padrão.

Observe que, quando seu aplicativo do Unity é executado em uma imersão headset conectado a um PC desktop, Unity enviará seu buffer de profundidade para Windows para habilitar reprojection por pixel, que geralmente fornecerá ainda melhor qualidade de imagem sem trabalho explícita pelo aplicativo. Se você fornecer um ponto de foco, que substituirá o reprojection por pixel, portanto, você deve fazer isso somente quando o aplicativo é executado em um HoloLens.




```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

Posicionamento do ponto de foco seja depende em grande parte o holograma está observando. O aplicativo tem o vetor de olhar para referência e o designer de aplicativo sabe que o conteúdo que eles querem que o usuário a ser observado.

É a única coisa mais importante, que um desenvolvedor pode fazer para se estabilizar hologramas renderizar em 60 FPS. Descartando abaixo de 60 FPS reduzirá drasticamente estabilidade holograma, independentemente da otimização do plano de estabilização.

**Práticas recomendadas** não é possível configurar o plano de estabilização universal e é específico do aplicativo, portanto, a recomendação principal é testá-las e ver o que funciona melhor para seus cenários. No entanto, ao tente alinhar o plano de estabilização com muito conteúdo possível, porque todo o conteúdo desse plano é estabilizado perfeitamente.

Por exemplo: 
* Se você tiver apenas planar conteúdo (aplicativo de leitura, o aplicativo de reprodução de vídeo), alinhar o plano de estabilização com o plano que tem seu conteúdo.
* Se houver 3 esferas pequenas que estão bloqueados pelo mundo, verifique o plano de estabilização "cortar" Embora os centros de todas as esferas que estão atualmente no modo de exibição do usuário.
* Se sua cena tem conteúdo no fundo substancialmente diferente, favoreça ainda mais objetos.
* Certifique-se de ajustar cada quadro para coincidir com o holograma o usuário está observando o ponto de estabilização

**Coisas a serem Evite** o plano de estabilização é uma ótima ferramenta para alcançar hologramas estáveis, mas se usado indevidamente-lo pode resultar em instabilidade de imagem graves.
* Não "disparar e esquecer", uma vez que você pode acabar com a estabilização do plano por trás do usuário ou anexado a um objeto que não está mais no modo de exibição do usuário. Verifique se que o plano de estabilização normal está definido (por exemplo, - camera.forward) de câmera encaminhamento oposto
* Não são alterados rapidamente o plano de estabilização e voltar entre extremos
* Não deixe o plano de estabilização definido como uma distância/orientação fixa
* Não deixe que o plano de estabilização acabando com o usuário
* Não definir o ponto de foco durante a execução em um desktop PC em vez de um HoloLens e, em vez disso, contar reprojection com base em profundidade por pixel.

## <a name="color-separation"></a>Separação de cores 

Devido à natureza do HoloLens exibe, às vezes, poderá ser visto um artefato chamado "separação de cores". Ela se manifesta como a imagem a separação em cores individuais base - vermelhas, verdes e azuis. O artefato pode ser especialmente visível ao exibir objetos em branco, pois eles têm grandes quantidades de vermelho, verde e azul. É mais pronunciada quando um usuário visualmente rastreia um holograma que está se movendo em quadro holográfico em alta velocidade. Outra maneira de que artefato pode se manifestar está distorcendo/deformação de objetos. Se um objeto tiver alto contraste e/ou em cores puras separação de cor (vermelha, verde, azul), será percebida como deformação de partes diferentes do objeto.

**Exemplo de que a separação de cor de um cursor de arredondamento branco bloqueado de cabeçalho pode ser semelhante como um usuário gira suas cabeças para o lado:**

![Exemplo de que a separação de cor de um cursor de arredondamento branco bloqueado de cabeça seria semelhante como um usuário gira suas cabeças ao lado.](images/colorseparationofroundwhitecursor-300px.png)

Embora seja difícil evitar completamente a separação de cores, há várias técnicas disponíveis para resolvê-lo.

**Separação de cores pode ser vista em:**
* Objetos que estão mudando rapidamente, incluindo objetos bloqueados de cabeçalho, como o [cursor](cursors.md).
* Objetos que são substancialmente longe do [plano de estabilização](hologram-stability.md#stabilization-plane).

**Para atenuam os efeitos de separação de cores:**
* Fazer com que o objeto de retardo olhar do usuário. Ele deve aparecer como se ele tem alguns inércia e está anexado o olhar "on springs". Isso reduz o cursor (reduzindo a distância de separação) e coloca-o por trás do ponto de olhar provável do usuário. Desde que ele rapidamente o alcança quando o usuário para mudar seu olhar parece bastante natural.
* Se você quiser mover um holograma, tente manter sua velocidade do movimento abaixo 5 graus por segundo, se você prevê que o usuário segui-lo com seus olhos.
* Use *light* em vez de *geometry* para o cursor. Uma fonte de iluminação virtual anexada ao olhar será vista como um ponteiro de interativo, mas não fará com que a separação de cores.
* Ajuste o plano de estabilização para coincidir com as hologramas em que o usuário é Observação.
* Verifique o vermelho de objeto, verde ou azul.
* Mudar para uma versão desfocada do conteúdo. Por exemplo, um cursor branco round poderia ser alteração em uma linha um pouco desfocada orientada na direção de movimento.

Como antes, renderização de 60 FPS e definir o plano de estabilização são as técnicas mais importantes para estabilidade holograma. Se voltado para a separação de cores perceptível, primeiro verifique se que a taxa de quadros atende às expectativas.

## <a name="see-also"></a>Consulte também
* [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)
* [Cor, luz e materiais](color,-light-and-materials.md)
* [Conceitos básicos de interação](interaction-fundamentals.md)
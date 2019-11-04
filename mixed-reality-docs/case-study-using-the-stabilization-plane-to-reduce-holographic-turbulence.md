---
title: Estudo de caso-usando o plano de estabilização para reduzir Holographic turbulência
description: Usando o plano de estabilização para reduzir Holographic turbulência
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, hologramas, estabilização, estudo de caso
ms.openlocfilehash: d31f3128ba10d6fc7bd57f3068db3dd16b23f901
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436437"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Estudo de caso-usando o plano de estabilização para reduzir Holographic turbulência

Trabalhar com hologramas pode ser complicado. O fato de que você pode se movimentar em seu espaço e ver seus hologramas de todos os ângulos diferentes fornece um nível de imersão que você não pode obter com uma tela de computador normal. Manter esses hologramas em vigor e parecer realista é um feito pelo hardware do Microsoft HoloLens e pelo design inteligente de aplicativos Holographic.

## <a name="the-tech"></a>O Tech

Para fazer com que os hologramas pareçam estar realmente compartilhando o espaço com você, eles devem ser renderizados corretamente, sem a separação de cores. Isso é obtido, em parte, por tecnologia interna ao hardware do HoloLens, que mantém os hologramas ancorados no que chamamos de um [plano de estabilização](hologram-stability.md#reprojection).

Um plano é definido por um ponto e um normal, mas como sempre queremos que o plano fique à câmera, estamos realmente preocupados com a definição do ponto do plano. Podemos informar ao HoloLens que aponta para concentrar seu processamento para manter tudo ancorado e estável, mas como definir esse ponto de foco é específico do aplicativo e pode fazer ou interromper seu aplicativo dependendo do conteúdo.

Resumindo, os hologramas funcionam melhor quando o plano de estabilização é aplicado corretamente, mas o que isso realmente significa depende do tipo de aplicativo que você está criando. Vamos dar uma olhada em como alguns dos aplicativos disponíveis atualmente para o HoloLens resolvem esse problema.

## <a name="behind-the-scenes"></a>Nos bastidores

Ao desenvolver os aplicativos a seguir, observamos que, quando não usamos o plano, os objetos seriam sways quando nossa cabeça mudou e veremos a separação de cores com movimentos de cabeça ou de holograma rápidos. No decorrer do período de desenvolvimento, aprendemos por meio de avaliação e erro como melhor usar o plano de estabilização e como projetar nossos aplicativos em relação aos problemas que ele não pode corrigir.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: conteúdo de carta, interatividade 3D

O [Galaxy Explorer](galaxy-explorer.md) tem dois elementos principais na cena: a visão principal do conteúdo do celestes e a barra de ferramentas da interface do usuário pequena que segue o olhar. Para a lógica de estabilização, examinamos o que o seu vetor olhar atual intersecciona em cada quadro para determinar se ele atinge qualquer coisa em uma camada de colisão especificada. Nesse caso, as camadas nas quais estamos interessados são os planetas, portanto, se seu olhar cair em um planeta, o plano de estabilização será colocado lá. Se nenhum dos objetos na camada de colisão de destino for atingido, o aplicativo usará uma camada secundária "plano B". Se nada estiver sendo gazeddo em, o plano de estabilização será mantido à mesma distância que era quando nuvens no conteúdo. As ferramentas de interface do usuário são deixadas como um destino plano, pois descobrimos que o salto entre perto e longe reduziu a estabilidade da cena geral.

O design do Galaxy Explorer se presta bem para manter as coisas estáveis e reduzir o efeito da separação de cores. O usuário é incentivado a percorrer e girar o conteúdo em vez de movê-lo de lado a lado, e os planetas estão girando de forma lenta o suficiente para que a separação de cores não seja perceptível. Além disso, uma constante 60 FPS é mantida, o que leva muito tempo para impedir que a separação de cores ocorra.

Para verificar isso por conta própria, procure um arquivo chamado LSRPlaneModifier.cs no [código do Galaxy Explorer no GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: conteúdo estacionário com um foco na interface do usuário

No HoloStudio, você passa a maior parte do seu tempo olhando para o mesmo modelo em que está trabalhando. Seu olhar não move uma quantidade significativa, exceto quando você seleciona uma nova ferramenta ou deseja navegar pela interface do usuário, para que possamos manter a lógica de configuração do plano simples. Ao examinar a interface do usuário, o plano é definido como qualquer elemento da interface do usuário ao qual seu olhar se ajusta. Ao olhar para o modelo, o plano é uma distância definida, correspondendo à distância padrão entre você e o modelo.

![O plano de estabilização é visualizado em HoloStudio como o usuário gazes no botão página inicial](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour e visualizador 3D: conteúdo estacionário com animação e filmes

No HoloTour e no visualizador 3D, você está examinando um objeto animado solitários ou um filme com efeitos 3D adicionados sobre ele. A estabilização nesses aplicativos é definida como o que você está exibindo no momento.

O HoloTour também impede que você se afaste muito do mundo virtual, fazendo com que ele se mova com você em vez de permanecer em um local fixo. Isso garante que você não ficará muito longe de outros hologramas para que os problemas de estabilidade sejam deslizados.

![Neste exemplo de HoloTour, o plano de estabilização seria definido como este filme de Pantheon de Hadrian.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: conteúdo dinâmico e interações ambientais

Definir o plano de estabilização em RoboRaid é surpreendentemente simples, apesar de ser o aplicativo que exige o movimento mais repentino. O plano é direcionado para se adequar às paredes ou aos objetos ao redor e flutuar em uma distância fixa na frente de você quando estiver longe de fazê-lo.

O RoboRaid foi projetado com o plano de estabilização em mente. O reticle, que move o máximo, já que ele é bloqueado, evita isso usando apenas vermelho e azul, o que minimiza qualquer sangramento de cor. Ele também contém uma pequena profundidade entre as partes, minimizando qualquer sangramento de cor que poderia ocorrer mascarando-a com um efeito de da Parallax já esperado. Os robôs não se movem muito rapidamente e só viajam a pequenas distâncias em intervalos regulares. Eles tendem a ficar cerca de 2 metros na frente, onde a estabilização é definida por padrão.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Fragmentos e jovens Conker: conteúdo dinâmico com interação ambiental

Escrito pelo Asobo Studio em C++, fragmentos e jovens Conker usam uma abordagem diferente para definir o plano de estabilização. Os pontos de interesse (POI) são definidos no código e ordenados em termos de prioridade. Em inglês, temos conteúdo em jogo, como o modelo Conker em jovens Conker, menus, Reticle de mira e logotipos. O em diante é interseccionado pelo olhar do usuário e o plano é definido como o centro do objeto com a prioridade mais alta. Se nenhuma interseção ocorrer, o plano será definido como a distância padrão.

Fragmentos e jovens de Conker também criam um design para você se afastar muito dos hologramas, pausando o aplicativo se você se mover para fora do que foi previamente examinado como seu espaço de reprodução. Dessa forma, eles mantêm você dentro dos limites encontrados para fornecer a experiência mais estável.

## <a name="do-it-yourself"></a>Faça você mesmo

Se você tiver um HoloLens e quiser brincar com os conceitos discutidos, poderá baixar uma cena de teste e experimentar os exercícios abaixo. Ele usa a API Gizmo interna do Unity e ele deve ajudá-lo a visualizar onde seu plano está sendo definido. Esse código também foi usado para capturar as capturas de tela nesse estudo de caso.
1. Sincronize a versão mais recente do [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Abra a cena [HoloToolkit-examples/Utilities/cenas/StabilizationPlaneSetting. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) .
3. Crie e configure o projeto gerado.
4. Execute em seu dispositivo.

### <a name="exercise-1"></a>Exercício 1

Você verá vários pontos brancos em orientações diferentes. Na frente de você, você verá três pontos em diferentes profundidades. Toque de ar para alterar a qual ponto o plano está definido. Para este exercício e para os outros dois, mova-se pelo seu espaço enquanto nuvens nos pontos. Transforme seu cabeçalho à esquerda, à direita, acima e abaixo. Aproxime-se e pai dos pontos. Veja como eles reagem quando o plano de estabilização é definido como destinos diferentes.

### <a name="exercise-2"></a>Exercício 2

Agora, mude para a direita até ver dois pontos de movimentação, um oscillating em um caminho horizontal e outro em um caminho vertical. Mais uma vez, toque em ar para alterar a qual ponto o plano está definido. Observe como a separação de cores é reduzida aparece no ponto que está conectado ao plano. Toque novamente para usar a velocidade do ponto na função de configuração do plano. Esse parâmetro fornece uma dica para o HoloLens sobre o movimento pretendido do objeto. É importante saber quando usar isso, como você observará quando a velocidade é usada em um ponto, o outro ponto de movimentação mostrará uma separação de cores maior. Tenha isso em mente ao projetar seus aplicativos – ter um fluxo coeso para o movimento de seus objetos pode ajudar a evitar que os artefatos sejam exibidos.

### <a name="exercise-3"></a>Exercício 3

Vá para o seu direito mais uma vez até ver uma nova configuração de pontos. Nesse caso, há pontos na distância e um ponto em espiral e escapados na frente deles. Toque de ar para alterar a qual ponto o plano está definido, alternando entre os pontos na parte de trás e o ponto em movimento. Observe como definir a posição do plano e a velocidade para aquela do ponto de espiral faz com que os artefatos apareçam em qualquer lugar.

**Sobre**
* Mantenha a lógica de configuração do plano simples. Como vimos, você não precisa de algoritmos de configuração de plano complexos para fazer uma experiência de imersão. O plano de estabilização é apenas uma peça do quebra-cabeça.
* Quando possível, sempre mova o plano entre destinos sem problemas. A troca instantânea de destinos distantes pode interromper visualmente a cena.
* Considere ter uma opção em sua lógica de configuração de plano para bloquear em um destino muito específico. Dessa forma, você pode ter o plano bloqueado em um objeto, como uma tela de logotipo ou de título, se necessário.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>Engenheiro de software @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Sr noções básicas 100: introdução ao Unity](holograms-100.md)
* [Ponto de foco no Unity](focus-point-in-unity.md)
* [Estabilidade do holograma](hologram-stability.md)

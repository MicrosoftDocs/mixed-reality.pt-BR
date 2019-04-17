---
title: Estudo de caso - usando o plano de estabilização para reduzir a Turbulência holográfica
description: Usando o plano de estabilização para reduzir a Turbulência holográfica
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, estabilização, estudo de caso
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589078"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Estudo de caso - usando o plano de estabilização para reduzir a Turbulência holográfica

Trabalhar com hologramas pode ser complicado. O fato de que você pode mover-se o seu espaço e consulte seu hologramas de todos os ângulos diferentes fornece um nível de imersão que não é possível obter com uma tela de computador normal. Mantendo esses hologramas em vigor e procurando realista são um recurso técnico realizado com o hardware da Microsoft HoloLens e o design inteligente de aplicativos holographic.

## <a name="the-tech"></a>O técnico

Para tornar hologramas aparecer mesmo que eles realmente estiver compartilhando o espaço com você, eles devem ser renderizados corretamente, sem separação de cores. Isso é obtido, em parte, pela tecnologia integrada para o hardware do HoloLens que mantém hologramas ancoradas no que chamamos de um [plano de estabilização](hologram-stability.md#stabilization-plane).

Um plano é definido por um ponto e um normal, mas como queremos sempre que o plano para enfrentar a câmera, estamos realmente apenas preocupados com a configuração de ponto do plano. Podemos dizer HoloLens que apontam para se concentrar seu processamento para manter que tudo ancorada e estável, mas como definir esse ponto de foco é específico do aplicativo e pode fazer ou interromper seu aplicativo, dependendo do conteúdo.

Em resumo, hologramas funcionam melhor quando o plano de estabilização é aplicado corretamente, mas o que realmente significa que depende do tipo de aplicativo que você está criando. Vamos dar uma olhada em como alguns dos aplicativos atualmente disponíveis para o HoloLens enfrentar esse problema.

## <a name="behind-the-scenes"></a>Nos bastidores

Ao desenvolver os aplicativos a seguir, observamos que, quando não usamos o plano, objetos seriam sway quando movido de cabeça e veremos a separação de cores com head rápida ou movimentações holograma. Ao longo do período de tempo de desenvolvimento, aprendemos através de tentativa e erro como usar melhor o plano de estabilização e como criar nossos aplicativos em torno dos problemas que ele não pode corrigir.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: Conteúdo estático, a interatividade 3D

[Explorer Galaxy](galaxy-explorer.md) tem dois elementos principais na cena: Exibição do conteúdo celestiais e a pequena barra de ferramentas da interface do usuário que segue o seu foco principal. Para a lógica de estabilização, vamos examinar o que seu vetor atual de olhar faz interseção com em cada quadro para determinar se ela atingir qualquer coisa em uma camada de colisão especificado. Nesse caso, estamos interessados em camadas são planetas, portanto, se seu foco cair em um planeta, o plano de estabilização é colocado nesse local. Se nenhum dos objetos na camada de colisão de destino são atingidos, o aplicativo usa uma camada secundária "Plano B". Se nada estiver sendo gazed no, o plano de estabilização é mantido na mesma distância como ele era quando Observação o conteúdo. As ferramentas de interface do usuário são deixadas como um destino de plano encontrado o salto entre perto e muito reduzida a estabilidade da cena geral.

O design do Explorer Galaxy presta-se bem a manter as coisas estável e reduzir o efeito de separação de cores. O usuário é incentivado a percorrer e órbita o conteúdo em vez de movem de lado a lado e planetas são orbiting bastante lenta que a separação de cor não é perceptível. Além disso, uma constante 60 FPS é mantida, que percorre um longo caminho na prevenção de separação de cores aconteça.

Para verificar isso por conta própria, procure um arquivo chamado LSRPlaneModifier.cs na [código do Gerenciador de Galaxy no GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: Conteúdo estático com um foco de interface do usuário

No HoloStudio, gastar a maior parte do seu tempo observando o mesmo modelo que você está trabalhando. Seu foco não é movido uma quantidade significativa, exceto para quando você seleciona uma nova ferramenta ou deseja navegar a interface do usuário, portanto, podemos manter a lógica de configuração do plano simples. Ao examinar a interface do usuário, o plano é definido como qualquer elemento de interface do usuário que seu foco se encaixa. Ao examinar o modelo, o plano é uma conjunto de distância, correspondente com a distância padrão entre você e o modelo.

![O plano de estabilização visualizados no HoloStudio como o usuário gazes no botão página inicial](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour e visualizador 3D: Conteúdo estático com animação e filmes

No visualizador 3D e de HoloTour, você vê um filme ou um objeto animado solitário com efeitos 3D adicionados sobre ele. A estabilização nesses aplicativos é definida como tudo o que você está exibindo no momento.

HoloTour também impede que você straying muito longe do seu mundo virtual fazendo com que ele mover com você, em vez de manter-se em um local fixo. Isso garante que você não obterá o suficiente para longe de outras hologramas de problemas de estabilidade a surgir.

![Neste exemplo de HoloTour, o plano de estabilização seria definido para este filme do Pantheon de Hadrian.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: Interações de ambientais e de conteúdo dinâmicas

Definir o plano de estabilização em RoboRaid é surpreendentemente simple, apesar de ser o aplicativo que requer a movimentação mais repentina. O plano está voltado para adequar-se às paredes ou os que envolvem objetos e flutuará em uma distância fixa na sua frente quando você estiver longe o suficiente para longe-los.

RoboRaid foi desenvolvido com o plano de estabilização em mente. Reticle, que move a maioria, pois ele é bloqueado de cabeça, contorna isso usando somente vermelho e azul que minimiza qualquer cor mais avançadas. Ele também contém um pouco de profundidade entre as partes, minimizando sangramento qualquer cor que ocorreria mascarando-os com um efeito parallax já esperado. Robôs não moverá muito rápido e apenas trafegar distâncias curtas em intervalos regulares. Eles tendem a se manter em torno de 2 metros na sua frente, onde a estabilização é definida por padrão.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Fragmentos e Conker jovens: Conteúdo dinâmico com interação ambiental

Escrito por Asobo Studio em C++, fragmentos e Young Conker adotar uma abordagem diferente para definir o plano de estabilização. Pontos de interesse (POI) são definidos no código e ordenados em termos de prioridade. POIs são o conteúdo no jogo, como o modelo Conker no Conker Young, menus, reticle mira e logotipos. Os POIs são intersectadas por olhar do usuário e o plano é definido como o centro do objeto com a prioridade mais alta. Se nenhuma interseção ocorrer, o plano é definido como a distância padrão.

Fragmentos e Young Conker também projetar em torno de você straying longe demais das hologramas ao pausar o aplicativo se você ultrapassar o que é foram examinado anteriormente como seu espaço de execução. Como tal, eles mantêm dentro dos limites que são encontrados para fornecer uma experiência mais estável.

## <a name="do-it-yourself"></a>Faça você mesmo

Se você tiver um HoloLens e gostaria de brincar com os conceitos discutidos, você pode baixar uma cena de teste e testar os exercícios abaixo. Ele usa gizmo internos do Unity API e deve ajudá-lo a visualizar no qual o plano está sendo definido. Esse código também foi usado para capturar as capturas de tela este estudo de caso.
1. A versão mais recente de sincronização [MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Abra o [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) cena.
3. Criar e configurar o projeto gerado.
4. Execute no dispositivo.

### <a name="exercise-1"></a>Exercício 1

Você verá vários pontos brancos ao redor em diferentes orientações. Na sua frente, você verá três pontos no profundidades diferentes. Indicador e polegar para alterar qual ponto o plano é definido como. Para este exercício e para os outros dois, mova seu espaço ao redor Observação em pontos. Ative seu principal à esquerda, direita, para cima e para baixo. Mova próximo de e father de pontos. Veja como elas reagem quando o plano de estabilização é definido como destinos diferentes.

### <a name="exercise-2"></a>Exercício 2

Agora, ative para a direita até ver dois pontos movendo um oscilando para parar em um caminho horizontal e outro em um caminho vertical. Mais uma vez,-polegar para alterar qual ponto o plano é definido como. Observe como a separação de cores é diminuída é exibida no ponto que está conectado ao plano. Toque novamente para usar a velocidade do ponto em que a função de configuração do plano. Esse parâmetro oferece uma dica ao HoloLens sobre o movimento do objeto pretendido. É importante saber quando usá-lo, como você verá quando a velocidade é usada em um ponto, o outro ponto móvel mostrará maior separação de cores. Tenha isso em mente ao projetar seus aplicativos — ter um fluxo coeso para o movimento dos seus objetos pode ajudar a impedir que os artefatos que aparecem.

### <a name="exercise-3"></a>Exercício 3

Vá para o seu direito de mais uma vez até que você veja uma nova configuração de pontos. Nesse caso, há pontos na distância e um ponto de entrada e saída enrolados na frente delas. Indicador e polegar para alterar qual ponto o plano é definido como, alternando entre os pontos no volta e o ponto em movimento. Observe como definir a posição de plano e a velocidade do ponto crescente torna artefatos aparecem em todos os lugares.

**Dicas**
* Simplificar sua lógica de configuração do plano. Como você viu, você não precisa algoritmos de configuração do plano complexo para tornar uma experiência imersiva. O plano de estabilização é apenas uma peça do quebra-cabeça.
* Quando todos os possíveis, sempre mova o plano entre os destinos sem problemas. Alternar instantaneamente destinos distantes pode interromper visualmente a cena.
* Considere a possibilidade de ter uma opção em sua lógica de configuração do plano para bloquear até um destino muito específico. Dessa forma, você pode ter o plano bloqueado em um objeto, como uma tela de logotipo ou título, se necessário.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>Engenheiro de software @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Noções básicas sobre MR 100: Guia de Introdução com o Unity](holograms-100.md)
* [Ponto de foco no Unity](focus-point-in-unity.md)
* [Estabilidade holograma](hologram-stability.md)

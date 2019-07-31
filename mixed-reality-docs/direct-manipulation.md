---
title: Manipulação direta com as mãos
description: Visão geral do modelo de entrada de manipulação direta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design, mãos nas proximidades, HoloLens
ms.openlocfilehash: 8047d7549309d293b805dc43e44da99f9139e5c6
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414445"
---
# <a name="direct-manipulation-with-hands"></a>Manipulação direta com as mãos
A manipulação direta é um modelo de entrada que envolve tocar hologramas diretamente com suas mãos. A ideia por trás da manipulação direta é que os objetos se comportem exatamente como no mundo real. Os botões podem ser ativados simplesmente pressionando-os, os objetos podem ser pegados e o conteúdo 2D se comporta como uma tela de toque virtual. Isso torna a manipulação direta fácil para os usuários aprenderem, além de divertida. A manipulação direta é considerada um modelo de entrada "próximo", ou seja, é mais adequado para interagir com o conteúdo que está no alcance dos braços.

A manipulação direta é baseada em funcionalidade, o que significa que é amigável ao usuário. Não há nenhum gesto simbólico para ensinar aos usuários. Todas as interações são criadas em torno de um elemento visual que você pode tocar ou pegar.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Modelo de entrada</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
</tr>
<tr>
     <td>Manipulação direta com as mãos</td>
     <td>❌ Sem suporte</td>
     <td>✔️ Recomendado</td>
     <td>➕ Uma alternativa, <a href="point-and-commit.md">apontar e confirmar com as mãos</a> é recomendado.</td>
    
</tr>
</table>


A manipulação direta é um modelo de entrada primário no HoloLens 2 e utiliza o novo sistema de acompanhamento da mão articulado. O modelo de entrada também está disponível nos headsets imersivos com o uso de controladores de movimento, mas não é recomendado como o principal meio de interação, apenas para a manipulação de objetos. A manipulação direta não está disponível no HoloLens (1ª geração).


## <a name="collidable-fingertip"></a>Ponta do dedo colidente

No HoloLens 2, as mãos do usuário são reconhecidas e interpretadas como modelos estruturais esquerdo e direito. Para implementar a ideia de tocar hologramas diretamente com mãos, idealmente, cinco colisores podem ser anexados às pontas dos cinco dedos de cada modelo estrutural de mão. No entanto, devido à falta de retorno tátil, dez pontas de dedo colidentes podem causar colisões inesperadas e imprevisíveis com os hologramas. 

Portanto, sugerimos colocar somente um colisor em cada dedo indicador. As pontas de dedo indicador colidentes ainda podem servir como pontos de toque ativo para diversos gestos de toque que envolvam outros dedos, como ao pressionar com um dedo, tocar com um dedo e pressionar com dois e cinco dedos, conforme mostrado na imagem abaixo.

![Imagem da ponta do dedo colidente](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Colisor esférico

Em vez de usar uma forma genérica aleatória, sugerimos que você use um colisor esférico. Em seguida, renderize-o visualmente para fornecer indicações melhores para direcionamento próximo. O diâmetro da esfera deve corresponder à espessura do dedo indicador para aumentar a precisão do toque. É mais fácil recuperar a variável de espessura do dedo chamando a API da mão.

### <a name="fingertip-cursor"></a>Cursor de ponta do dedo

Além de renderizar uma esfera colidente na ponta do dedo indicador, criamos um cursor avançado de ponta do dedo para obter uma melhor experiência de direcionamento próximo, de maneira interativa. É um cursor em forma de rosca anexado à ponta do dedo indicador. De acordo com a proximidade, ele reage dinamicamente a um alvo em termos de orientação e tamanho, conforme especificado abaixo:

* Quando um dedo indicador se move em direção a um holograma, o cursor sempre está paralelo à superfície do holograma e diminui gradualmente seu tamanho.
* Assim que o dedo toca a superfície, o cursor é reduzido a um ponto e emite um evento de toque.

Com o retorno interativo, os usuários podem realizar tarefas de direcionamento próximo com alta precisão, como disparar um hiperlink ou pressionar um botão, conforme mostrado abaixo. 

![Imagem do cursor de ponta do dedo](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Caixa delimitadora com o sombreador de proximidade

O holograma em si também requer a capacidade de fornecer retorno visual e sonoro para compensar a falta do retorno tátil. Para isso, criamos o conceito de uma caixa delimitadora com um sombreador de proximidade. Uma caixa delimitadora é uma área volumétrica mínima que inclui um objeto 3D. A caixa delimitadora tem um mecanismo de renderização interativo chamado de sombreador de proximidade. O sombreador de proximidade se comporta da seguinte maneira:

* Quando o dedo indicador está em um intervalo, um destaque da ponta do dedo é mostrado na superfície da caixa delimitadora.
* Quando a ponta do dedo se aproxima da superfície, o destaque é reduzido correspondentemente.
* Quando a ponta do dedo toca a superfície, toda a caixa delimitadora tem sua cor alterada ou gera efeitos visuais para refletir o estado de toque.
* Um efeito sonoro pode ser ativado para aprimorar o retorno visual do toque.

![Imagem da caixa delimitadora com o sombreador de proximidade](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Botão de pressão

Com uma ponta do dedo colidente, os usuários podem interagir com o mais fundamental dos componentes holográficos da interface do usuário, o botão de pressão. Um botão de pressão é um botão holográfico adaptado para o pressionar direto do dedo. Novamente, devido à falta de retorno tátil, um botão de pressão ativa alguns mecanismos para lidar com os problemas relacionados ao retorno tátil.

* O primeiro mecanismo é uma caixa delimitadora com um sombreador de proximidade, o qual é detalhado na seção anterior. Ele fornece aos usuários uma melhor sensação de proximidade ao abordarem e fazerem contato com um botão.
* O segundo mecanismo é o de liberação. A liberação cria uma ideia de pressionar para baixo depois da ponta de um dedo entrar em contato com um botão. O botão se move intimamente com a ponta do dedo ao longo do eixo de profundidade. O botão pode ser disparado quando atinge uma profundidade designada (ao pressionar) ou ao ser liberado depois de passar por ela.
* O efeito sonoro deve ser adicionado para melhorar o retorno quando o botão é disparado.

![Imagem do botão de pressão](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>Interação slate 2D

Um slate 2D é um contêiner holográfico que hospeda o conteúdo do aplicativo 2D, como um navegador da web. O conceito de design para interagir com um slate 2D por meio da manipulação direta é aproveitar o modelo mental da interação com uma tela de toque física.

Para interagir com o contato slate:

* Use o dedo indicador para pressionar um botão ou hiperlink.
* Use o dedo indicador para rolar um slate de conteúdo para cima e para baixo.
* O usuário usa os dois dedos indicadores para aumentar e diminuir o zoom no conteúdo do slate, de acordo com o movimento relativo dos dedos.

![Imagem do slate 2D](images/2D-Slate-Interaction-720px.jpg)

Para manipular o slate 2D em si:

* Aproxime as mãos dos cantos e bordas para revelar as funcionalidades de manipulação mais próximas.
* Segure as funcionalidades de manipulação, realize um dimensionamento uniforme utilizando as funcionalidades de canto e reflua utilizando as funcionalidades de borda.
* Segure a barra holográfica na parte superior do slate 2D, o que permite mover todo o slate.

![Imagem da manipulação do slate](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D

O HoloLens 2 permite que os usuários habilitem suas mãos para manipular diretamente objetos holográficos 3D, aplicando uma caixa delimitadora a cada objeto 3D. A caixa delimitadora fornece uma melhor percepção da profundidade por meio do sombreador de proximidade. Com a caixa delimitadora, há duas abordagens de design para a manipulação de objetos 3D.

### <a name="affordance-based-manipulation"></a>Manipulação baseada em funcionalidade

A manipulação com base em funcionalidade permite manipular o objeto 3D por meio de uma caixa delimitadora, junto com as funcionalidades de manipulação em torno dela. Quando a mão de um usuário estiver próxima a um objeto 3D, a caixa delimitadora e a funcionalidade mais próxima são reveladas. Os usuários podem pegar a caixa delimitadora para mover todo o objeto, as funcionalidades de borda para girar e as funcionalidades de canto para dimensionar de maneira uniforme.

![Imagem da manipulação de objetos 3D](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>Manipulação não baseada em funcionalidade

A manipulação que não é baseada em funcionalidade não anexa a funcionalidade à caixa delimitadora. Os usuários podem revelar apenas a caixa delimitadora e interagir diretamente com ela. Se a caixa delimitadora for pega com uma mão, a translação e rotação do objeto estarão associadas ao movimento e à orientação da mão. Quando o objeto é pego com as duas mãos, os usuários podem transladá-lo, dimensioná-lo e girá-lo de acordo com os movimentos relativos das duas mãos.

A manipulação específica requer precisão. Recomendamos usar a **manipulação baseada em funcionalidade**, pois ela fornece um alto nível de granularidade. Para a manipulação flexível, recomendamos usar a **manipulação não baseada em funcionalidade**, pois ela permite experiências instantâneas e divertidas.

## <a name="instinctual-gestures"></a>Gestos instintuais

Com o HoloLens (1ª geração), ensinamos aos usuários alguns gestos predefinidos, como abrir a mão e fechar e abrir os dedos indicador e polegar. Para o HoloLens 2, não pedimos para os usuários memorizarem gestos simbólicos. Todos os gestos exigidos do usuário, em que os usuários precisam interagir com os hologramas e o conteúdo, são instintuais. A forma de atingir gestos instintuais é ajudar os usuários a realizar os gestos por meio do design de funcionalidades da interface do usuário.

Por exemplo, se nós incentivarmos o usuário a segurar um objeto ou um ponto de controle com uma pinçagem de dois dedos, o objeto ou o ponto de controle deverá ser pequeno. Se quisermos que o usuário segure com cinco dedos, o objeto ou o ponto de controle deverá ser relativamente grande. Isso funciona de modo semelhante para os botões: um botão pequeno limitaria os usuários a pressioná-lo com apenas um dedo, enquanto que um botão grande encorajaria os usuários a pressioná-lo com as mãos.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Design simétrico entre os controladores de mão e DoF 6

Talvez você tenha observado que há interações paralelas que podemos utilizar entre as mãos no RA e controladores de movimentos na VR. Ambas as entradas podem ser usadas para disparar manipulações diretas em seus respectivos ambientes. No HoloLens 2, os movimentos de segurar e arrastar com mãos em distância próxima funcionam da mesma maneira que o botão para segurar nos controladores de movimentos do WMR. Isso fornece aos usuários familiaridade de interação entre as duas plataformas e pode ser útil se você decidir portar seu aplicativo de uma para a outra.

## <a name="optimize-with-eye-tracking"></a>Otimizar com acompanhamento ocular

A manipulação direta poderá proporcionar uma sensação mágica se funcionar conforme o esperado. No entanto, ela também poderá se tornar frustrante rapidamente se você não puder mover sua mão para algum lugar sem disparar inadvertidamente um holograma. O acompanhamento ocular pode ajudar a identificar melhor a intenção do usuário.

* **Quando**: reduzir o disparo involuntário de uma resposta de manipulação. O acompanhamento ocular permite entender melhor o que um usuário realmente deseja fazer.
Por exemplo, imagine que você esteja lendo um texto (instrutivo) holográfico e se aproxime para pegar uma ferramenta de trabalho do mundo real.

Ao fazer isso, você move acidentalmente sua mão sobre alguns botões holográficos interativos que não tinha observado (que podem inclusive estar fora do FoV (campo de visão) do usuário).

  Em resumo: se o usuário não olhar para um holograma por algum tempo, mas for detectado um evento de toque ou compreensão, provavelmente não foi a intenção do usuário interagir com esse holograma.

* **Qual deles**:  além de lidar com ativações falso-positivas, outro exemplo inclui a melhor identificação dos hologramas a serem segurados ou tocados, já que o ponto de interseção preciso pode não ser claro da sua perspectiva, especialmente se vários hologramas estão posicionados próximos uns dos outros.

  Embora o acompanhamento ocular tenha uma certa limitação de precisão no HoloLens 2, ele pode determinar o foco do olhar e isso ainda pode ser muito útil para interações próximas devido à disparidade de profundidade ao interagir com a entrada de mão. Isso significa que, às vezes, é difícil determinar se sua mão está atrás ou na frente de um holograma para segurar precisamente um widget de manipulação, por exemplo.

* **Onde**: usar informações sobre o que um usuário está vendo com gestos de lançamento rápido. Segure um holograma e lance-o para seu destino pretendido.  

    Embora isso geralmente funcione bem, gestos de mão muito rápidos podem resultar em destinos altamente imprecisos. Nesse cenário, a inclusão de controle ocular pode melhorar a precisão do gesto.

## <a name="see-also"></a>Consulte também

* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)


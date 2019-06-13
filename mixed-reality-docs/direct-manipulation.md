---
title: Manipulação direta com as mãos
description: Visão geral do modelo de entrada de manipulação direta
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidade Misturada, foco, direcionamento do foco, interação, design, mãos nas proximidades, HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402389"
---
# <a name="direct-manipulation-with-hands"></a>Manipulação direta com as mãos
A manipulação direta é um modelo de entrada que envolve tocar hologramas diretamente com suas mãos. O objetivo da manipulação direta é fazer os objetos se comportarem exatamente como no mundo real. Os botões podem ser ativados simplesmente pressionando-os, os objetos podem ser pegados e o conteúdo 2D se comporta como uma tela de toque virtual.  Por isso, a manipulação direta é fácil para os usuários aprenderem e é muito divertida.  Ele é considerado um modelo de entrada "próximo", ou seja, é mais adequado para interagir com o conteúdo que está no alcance dos braços.

A manipulação direta é baseada em funcionalidade, o que significa que é amigável ao usuário. Não há nenhum gesto simbólico para ensinar aos usuários. Todas as interações são criadas em torno de um elemento visual que você pode tocar ou pegar.

## <a name="device-support"></a>Suporte a dispositivos


| Modelo de entrada | [HoloLens (1ª geração)](hololens-hardware-details.md) | HoloLens 2 |[Headsets imersivos](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| Manipulação direta com as mãos | ❌ Sem suporte | ✔️ Recomendado | ➕ Uma alternativa, [apontar e confirmar com as mãos](point-and-commit.md) é recomendado.

A manipulação direta é um modelo de entrada primário no HoloLens 2 e utiliza o novo sistema de acompanhamento da mão articulado. O modelo de entrada também está disponível nos headsets imersivos com o uso de controladores de movimento, mas não é recomendado como o principal meio de interação, apenas para a manipulação de objetos.  A manipulação direta não está disponível no HoloLens (1ª geração).


## <a name="collidable-fingertip"></a>Ponta do dedo colidente

No HoloLens 2, as mãos reais do usuário são reconhecidas e interpretadas como modelos estruturais esquerdo e direito. Para implementar a ideia de tocar hologramas diretamente com mãos, idealmente, 5 colisores podem ser anexados a 5 pontas de dedo de cada modelo estrutural de mão. No entanto, devido à falta de retorno tátil, na prática, 10 pontas de dedo colidentes causam colisões inesperadas e imprevisíveis com os hologramas. 

Portanto, sugerimos colocar somente um colisor em cada dedo indicador. As pontas de dedo indicador colidentes ainda podem servir como pontos de toque ativo para diversos gestos de toque que envolvam outros dedos, como ao pressionar com um dedo, tocar com um dedo e pressionar com dois e cinco dedos, conforme mostrado na imagem abaixo.

![Imagem da ponta do dedo colidente](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Colisor esférico

Em vez de usar uma forma genérica aleatória, sugerimos usar um colisor esférico e renderizá-lo visualmente para fornecer as melhores indicações para direcionamento próximo. O diâmetro da esfera deve corresponder à espessura do dedo indicador para aumentar a precisão do toque. Será fácil recuperar a variável de espessura do dedo chamando a API da mão.

### <a name="fingertip-cursor"></a>Cursor de ponta do dedo

Além de renderizar uma esfera colidente na ponta do dedo indicador, criamos uma solução avançada, o cursor de ponta do dedo, para obter a melhor experiência de direcionamento próximo de maneira interativa. É um cursor em forma de rosca anexado à ponta do dedo indicador. De acordo com a proximidade, ele reage dinamicamente a um alvo em termos de orientação e tamanho, conforme especificado abaixo:

* Quando um dedo indicador se move em direção a um holograma, o cursor sempre está paralelo à superfície do holograma e diminui gradualmente seu tamanho.
* Assim que o dedo toca a superfície, o cursor é reduzido a um ponto e emite um evento de toque.

Com o retorno interativo, os usuários podem realizar tarefas de focalização próxima com alta precisão, como disparar um hiperlink no conteúdo da web ou pressionar um botão, conforme mostrado abaixo. 

![Imagem do cursor de ponta do dedo](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Caixa delimitadora com o sombreador de proximidade

O holograma em si também requer a capacidade de fornecer retorno visual e sonoro para compensar a falta do retorno tátil. Para isso, criamos o conceito de uma caixa delimitadora com o sombreador de proximidade. Uma caixa delimitadora é uma área volumétrica mínima que inclui um objeto 3D. A caixa delimitadora tem um mecanismo de renderização interativo chamado sombreador de proximidade. O sombreador de proximidade se comporta da seguinte maneira:

* Quando o dedo indicador está em um intervalo de distância, um destaque da ponta do dedo é mostrado na superfície da caixa delimitadora.
* Quando a ponta do dedo se aproxima da superfície, o destaque se condensa.
* Quando a ponta do dedo toca a superfície, toda a caixa delimitadora tem sua cor alterada ou é gerado um efeito visual para refletir o estado de toque.
* Enquanto isso, um efeito sonoro pode ser ativado para aprimorar o retorno visual do toque.

![Imagem da caixa delimitadora com o sombreador de proximidade](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Botão de pressão

Com uma ponta do dedo colidente, os usuários podem interagir com o mais fundamental dos componentes holográficos da UI, o botão de pressão. Um botão de pressão é um botão holográfico adaptado para a pressão direta do dedo. Novamente, devido à falta de retorno tátil, um botão de pressão ativa alguns mecanismos para lidar com os problemas relacionados ao retorno tátil.

* O primeiro mecanismo é uma caixa delimitadora com o sombreador de proximidade, detalhado na seção anterior. Ele serve para fornecer uma melhor sensação de proximidade para os usuários abordarem e fazerem contato com um botão.
* O segundo é a depressão. Ele cria a sensação de pressão, depois que a ponta do dedo entra em contato com o botão. O botão se move intimamente com a ponta do dedo ao longo do eixo de profundidade. O botão pode ser disparado quando atinge uma profundidade designada (ao pressionar) ou ao ser liberado depois de passar por ela.
* O efeito sonoro deve ser adicionado para melhorar o retorno quando o botão for disparado.

![Imagem do botão de pressão](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>Interação slate 2D

Um slate 2D é um contêiner holográfico que hospeda o conteúdo do aplicativo 2D, como um navegador da web. O conceito de design para interagir com um slate 2D por meio da manipulação direta é aproveitar o modelo mental da interação com uma tela de toque física.

Para interagir com o contato slate:

* Use o dedo indicador para pressionar um botão ou hiperlink.
* Use o dedo indicador para rolar um slate de conteúdo para cima e para baixo.
* Os usuários usam os dois dedos indicadores para aumentar e diminuir o zoom no conteúdo slate de acordo com o movimento relativo dos dedos.

![Imagem do slate 2D](images/2D-Slate-Interaction-720px.jpg)

Para manipular o slate 2D em si:

* Aproxime as mãos dos cantos e bordas para revelar as funcionalidades de manipulação mais próximas.
* Segure as funcionalidades de manipulação e realize um dimensionamento uniforme utilizando as funcionalidades de canto, e redimensione utilizando as funcionalidades de borda.
* Segure a barra holográfica na parte superior do slate 2D, o que permite mover todo o slate.

![Imagem da manipulação do slate](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>Manipulação de objetos 3D

O HoloLens 2 permite que os usuários habilitem suas mãos para manipular diretamente objetos holográficos 3D, aplicando uma caixa delimitadora a cada objeto 3D. A caixa delimitadora fornece uma melhor percepção da profundidade por meio do sombreador de proximidade. Com a caixa delimitadora, há duas abordagens de design para a manipulação de objetos 3D.

### <a name="affordance-based-manipulation"></a>Manipulação baseada em funcionalidade

Permite manipular o objeto 3D por meio de uma caixa delimitadora e das funcionalidades de manipulação em torno dela. Quando a mão de um usuário estiver próxima a um objeto 3D, a caixa delimitadora e a funcionalidade mais próxima são reveladas. Os usuários podem pegar a caixa delimitadora para mover todo o objeto, as funcionalidades de borda para girar e as funcionalidades de canto para dimensionar de maneira uniforme.

![Imagem da manipulação de objetos 3D](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>Manipulação não baseada em funcionalidade

Neste mecanismo, nenhuma funcionalidade está anexada à caixa delimitadora. Os usuários podem revelar apenas a caixa delimitadora e interagir diretamente com ela. Se a caixa delimitadora for pega com uma mão, a translação e rotação do objeto estarão associadas ao movimento e à orientação da mão. Quando o objeto é pego com as duas mãos, os usuários podem transladá-lo, dimensioná-lo e girá-lo de acordo com os movimentos relativos das duas mãos.

A manipulação específica exige precisão; recomendamos usar a **manipulação baseada em funcionalidade**, pois ela fornece um alto nível de granularidade. Para a manipulação flexível, recomendamos usar a **manipulação não baseada em funcionalidade**, pois ela permite experiências instantâneas e divertidas.

## <a name="instinctual-gestures"></a>Gestos instintuais

Com o HoloLens (1ª geração), ensinamos aos usuários alguns gestos predefinidos, como abrir a mão e fechar e abrir os dedos indicador e polegar. Para o HoloLens 2, não pedimos para os usuários memorizarem gestos simbólicos. Todos os gestos exigidos do usuário para interagir com os hologramas e o conteúdo são instintuais. A forma de atingir o gesto instintual é orientar os usuários a realizar os gestos por meio do design de funcionalidades da interface do usuário.

Por exemplo, se nós o incentivarmos a segurar um objeto ou um ponto de controle com a pinçagem de dois dedos, o objeto ou o ponto de controle deve ser pequeno. Se quisermos que você segure com cinco dedos, o objeto ou o ponto de controle deve ser relativamente grande. Semelhante aos botões, um botão pequeno limitaria os usuários a pressioná-lo com apenas um dedo, enquanto que um botão grande encorajaria os usuários a pressioná-lo com as mãos.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Design simétrico entre os controladores de mão e DoF 6

Talvez você tenha observado que agora há interações paralelas que podemos utilizar entre as mãos em controladores de RA e de movimento na VR. Ambas as entradas podem ser usadas para disparar manipulações diretas em seus respectivos ambientes. No HoloLens 2, os movimentos de segurar e arrastar com mãos em distância próxima funcionam da mesma maneira que o botão para segurar nos controladores de movimento no WMR. Isso fornece aos usuários familiaridade de interação entre as duas plataformas e pode ser útil se você decidir portar seu aplicativo de um para o outro.

## <a name="optimize-with-eye-tracking"></a>Otimizar com acompanhamento ocular

A manipulação direta pode ser mágica se funcionar conforme o esperado, mas também pode se tornar frustrante rapidamente se você não puder mover sua mão para algum lugar sem disparar inadvertidamente um holograma.
O acompanhamento ocular pode ajudar a identificar melhor a intenção do usuário.

* **Quando**: Reduzir o disparo falso de uma resposta de manipulação. O acompanhamento ocular permite entender melhor o que um usuário realmente deseja fazer.
Por exemplo, imagine que você esteja lendo um texto (instrutivo) holográfico e se aproxime para pegar uma ferramenta de trabalho do mundo real.

Ao fazer isso, você move acidentalmente sua mão sobre alguns botões holográficos interativos que não tinha observado (que podem inclusive estar fora campo de visão (FOV) do usuário).

  Em resumo: se o usuário não olhar para um holograma por algum tempo, mas for detectado um evento de toque ou compreensão, provavelmente não foi a intenção do usuário interagir com esse holograma.

* **Qual deles**:  além de lidar com ativações falso-positivas, outro exemplo inclui a melhor identificação dos hologramas a serem segurados ou tocados, já que o ponto de interseção preciso pode não ser claro da sua perspectiva, especialmente se vários hologramas estiverem posicionados próximos uns dos outros.

  Embora o acompanhamento ocular tenha uma certa limitação de precisão no HoloLens 2, ele pode determinar o foco do olhar e isso ainda pode ser muito útil para interações próximas devido à disparidade de profundidade ao interagir com a entrada de mão.  Isso significa que, às vezes, é difícil determinar se sua mão está atrás ou na frente de um holograma para segurar precisamente um widget de manipulação, por exemplo.

* **Onde**: usar informações sobre o que um usuário está vendo com gestos de lançamento rápido. Segure um holograma e lance-o para seu destino pretendido.  

    Embora isso geralmente funcione bem, gestos de mão muito rápidos podem resultar em destinos altamente imprecisos. É aqui que o acompanhamento ocular poderia ajudar para direcionar o vetor de lançamento da mão de volta para a posição desejada.

## <a name="see-also"></a>Consulte também

* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Apontar e confirmar com as mãos](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)


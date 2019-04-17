---
title: Estudo de caso - HoloStudio 3 da interface do usuário e a interação de design lições aprendidas
description: UI HoloStudio e lições aprendidas de design de interação
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloLens, HoloStudio, realidade misturada
ms.openlocfilehash: 217c489fed3c0588dae1c2753db6ba15da3522c8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590591"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Estudo de caso - HoloStudio 3 da interface do usuário e a interação de design lições aprendidas

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) foi um dos aplicativos da Microsoft primeiro para o HoloLens. Por isso, tivemos que criar novas práticas recomendadas para 3D da interface do usuário e design de interação. Fizemos isso por meio de um lote de teste do usuário, criação de protótipos e tentativa e erro.

Nós sabemos que nem todo mundo tem os recursos à sua disposição para fazer esse tipo de pesquisa, portanto, tínhamos nosso Designer holográfica sênior, Marcus Ghaly, compartilhar três coisas que aprendemos durante o desenvolvimento de HoloStudio sobre design de interface do usuário e a interação para aplicativos do HoloLens.

## <a name="watch-the-video"></a>Assista ao vídeo

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problema 1 #: As pessoas não desejam mover suas criações

Originalmente projetamos o workbench no HoloStudio como um retângulo, muito como faria no mundo real. O problema é que as pessoas têm uma vida útil de experiência que lhes diga para permanecer ainda quando elas são sentada em uma mesa ou trabalhando na frente de um computador, portanto, eles não eram movendo-se a Bancada de trabalho e explorar sua criação 3D de todos os lados.

![O design retangular da Bancada de trabalho em HoloStudio dissuaded usuários de mover-se e ver suas criações de todos os lados.](images/rectangular-workbench-500px.jpg)

Tínhamos o insight para tornar o workbench de ida e volta, para que não havia nenhum "front" ou desmarque o que deveria ser colocados. Quando testamos isso, as pessoas começaram repentinamente mover-se e explorar suas criações por conta própria.

![O design da Bancada de trabalho circular incentivados usuários para fazer a ronda totalmente suas criações.](images/circular-workbench-500px.jpg)

**O que aprendemos**

Sempre ser pensar sobre o que está à vontade para o usuário. Tirar proveito de seu espaço físico é um recurso interessante do HoloLens e algo que você não pode fazer com outros dispositivos.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problema #2: Caixas de diálogo modais, às vezes, estão fora do quadro holográfico

Às vezes, o usuário pode estar procurando em outra direção de algo que precisa de sua atenção em seu aplicativo. Em um PC, você pode apenas pop backup uma caixa de diálogo, mas se você fizer isso em da alguém face em um ambiente 3D, ele pode se sentir como a caixa de diálogo está obtendo sua maneira. Você precisará delas para ler a mensagem, mas seu instinto é tentar obter para longe dela. Essa reação é ótima se você estiver reproduzindo um jogo, mas uma ferramenta projetada para o trabalho, é inferior ao ideal.

Depois de tentar algumas coisas diferentes, podemos finalmente optou por usar um sistema de "pensados bolha" para nossas caixas de diálogo e adicionado tendrils que os usuários podem seguir para onde a atenção é necessário em nosso aplicativo. Também fizemos o pulso tendrils, o que significava um senso de direcionalidade, de modo que os usuários sabiam onde ir.

![O sistema de "Bolha considerado" incluído tendrils pulsando em que forneceu um senso de direção, levando os usuários a onde sua atenção era necessário no aplicativo.](images/thought-bubble-500px.jpg)

**O que aprendemos**

É muito mais difícil em 3D para alertar os usuários as coisas precisam prestar atenção. Usando os diretores de atenção, como [som espacial](spatial-sound.md), raios de luz ou bolhas de pensamento, podem levar os usuários para onde elas precisam ser.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problema #3: Às vezes, interface do usuário pode ser bloqueado por outras hologramas

Há vezes quando um usuário deseja interagir com um holograma e seus controles de interface do usuário associados, mas eles estão bloqueados do modo de exibição porque outro holograma está na frente delas. Enquanto desenvolvíamos HoloStudio, nós usamos a tentativa e erro para chegar a uma solução para isso.

![Um controle de interface do usuário associado a um holograma pode ser bloqueado se não houver outro holograma entre ele e o usuário vestindo HoloLens.](images/ui-blocked-500px.jpg)

Tentamos movendo o controle de interface do usuário mais próximo ao usuário para que ele não foi possível obter bloqueado, mas encontrado que não estava confortável para o usuário observar um controle que estava perto de você ao mesmo tempo, observando simultaneamente um holograma que estava longe. Se, no entanto, movemos o controle na frente de holograma mais próximo ao usuário, eles sentiram como ele foi desanexado do holograma deveria afetar.

Por fim terminou o espelhamento no controle de interface do usuário e colocá-lo na mesma distância do usuário como o holograma que ele está associado, portanto, ambos se sinta conectados. Isso permite que o usuário interaja com o controle, mesmo que ele é foram ocultado.

![A solução: estamos fantasma o controle de interface do usuário, que tanto permitido a interação com o controle e fez se sinta conectado ao holograma ela estava afetando.](images/ghosting-ui-500px.jpg)

**O que aprendemos**

Os usuários precisam ser capazes de acessar facilmente os controles de interface do usuário, mesmo se eles já foram bloqueados, por isso, descubra métodos para garantir que os usuários podem concluir suas tarefas, independentemente de onde seus hologramas estão no mundo real.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Designer holográfica sênior @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Conceitos básicos de interação](interaction-fundamentals.md)

 

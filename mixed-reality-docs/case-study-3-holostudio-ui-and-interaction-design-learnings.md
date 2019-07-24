---
title: Estudo de caso-3 HoloStudio de interface do usuário e de design de interação
description: HoloStudio da interface do usuário e de design de interação
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, realidade misturada do Windows
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974825"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Estudo de caso-3 HoloStudio de interface do usuário e de design de interação

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) foi um dos primeiros aplicativos da Microsoft para o HoloLens. Por isso, tivemos que criar novas práticas recomendadas para a interface do usuário 3D e o design de interação. Fizemos isso por vários testes de usuário, protótipos e avaliação e erro.

Sabemos que nem todos têm os recursos em sua disposição para fazer esse tipo de pesquisa, então tivemos nosso designer Sr. Holographic, Marcus Ghaly, compartilhamos três coisas que aprendemos durante o desenvolvimento de HoloStudio sobre o design de interação e a interface do usuário para aplicativos do HoloLens.

## <a name="watch-the-video"></a>Assista ao vídeo

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>#1 do problema: As pessoas não desejavam se mover em suas criações

Originalmente, criamos o Workbench em HoloStudio como um retângulo, assim como você encontraria no mundo real. O problema é que as pessoas têm um tempo de vida de experiência que os instrui a permanecer ainda quando estiverem sentado em uma mesa ou trabalhando na frente de um computador, de modo que não se estivessem passando pelo Workbench e explorando a criação de 3D de todos os lados.

![O design retangular do Workbench em HoloStudio dissuaded os usuários de se movimentar e ver suas criações de todos os lados.](images/rectangular-workbench-500px.jpg)

Tivemos a percepção de fazer o Workbench ser arredondado, de forma que não houvesse nenhuma "frente" ou claro que você deveria parar. Quando testamos isso, as pessoas repentinamente começaram a percorrer e explorar suas próprias criações por conta própria.

![O design do Workbench circular incentiva os usuários a percorrer o caminho em relação às suas criações.](images/circular-workbench-500px.jpg)

**O que aprendemos**

Sempre esteja pensando sobre o que é confortável para o usuário. Tirar proveito do espaço físico é um recurso interessante do HoloLens e algo que você não pode fazer com outros dispositivos.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>#2 do problema: As caixas de diálogo modais às vezes estão fora do quadro Holographic

Às vezes, o usuário pode estar olhando em uma direção diferente de algo que precisa de sua atenção em seu aplicativo. Em um PC, você pode simplesmente exibir uma caixa de diálogo, mas se fizer isso na face de alguém em um ambiente 3D, pode parecer que a caixa de diálogo está ficando de seu jeito. Você precisa deles para ler a mensagem, mas seu instinto é tentar sair dela. Essa reação será excelente se você estiver jogando um jogo, mas em uma ferramenta projetada para o trabalho, será menos do que o ideal.

Depois de experimentar algumas coisas diferentes, finalmente temos liquidado o uso de um sistema de "bolha pensada" para nossas caixas de diálogo e adicionamos tendrils que os usuários podem seguir para onde a atenção é necessária em nosso aplicativo. Também fizemos o pulso tendrils, que implícita uma noção de direcionalidade para que os usuários soubessem aonde ir.

![O sistema de "bolha pensada" incluiu Pulsing tendrils que fornecia uma noção de direção, levando os usuários a onde sua atenção era necessária no aplicativo.](images/thought-bubble-500px.jpg)

**O que aprendemos**

É muito mais difícil em 3D alertar os usuários sobre as coisas de que precisam para prestar atenção. O uso de diretores de atenção, como [som espacial](spatial-sound.md), raios leves ou bolhas de pensamento, pode levar os usuários a onde precisam.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>#3 do problema: Às vezes, a interface do usuário pode ser bloqueada por outros hologramas

Há ocasiões em que um usuário deseja interagir com um holograma e seus controles de interface do usuário associados, mas eles são bloqueados da exibição porque outro holograma está na frente deles. Enquanto estávamos desenvolvendo o HoloStudio, usamos a avaliação e o erro para chegar a uma solução para isso.

![Um controle de interface do usuário associado a um holograma pode se tornar bloqueado se houver outro holograma entre ele e o usuário com o HoloLens.](images/ui-blocked-500px.jpg)

Tentamos mover o controle da interface do usuário para mais perto de quando ele não podia ser bloqueado, mas descobriu que não era confortável que o usuário examinasse um controle que estava perto de você ao olhar simultaneamente um holograma que estava muito distante. No entanto, se movermos o controle na frente do holograma mais próximo para o usuário, eles acharam que ele foi desanexado do holograma que deveria estar afetando.

Finalmente acabamos de duplicar o controle de interface do usuário e colocá-lo com a mesma distância de um User como o holograma ao qual ele está associado, para que ambos se sintam conectados. Isso permite que o usuário interaja com o controle, mesmo que ele tenha sido obscurecido.

![A solução: fantasmas o controle da interface do usuário, que permitia a interação com o controle e o fizemos conectado ao holograma que estava afetando.](images/ghosting-ui-500px.jpg)

**O que aprendemos**

Os usuários precisam ser capazes de acessar facilmente os controles da interface do usuário, mesmo que tenham sido bloqueados; portanto, descubra métodos para garantir que os usuários possam concluir suas tarefas, independentemente de onde estão os hologramas no mundo real.

## <a name="about-the-author"></a>Sobre o autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Designer do Sr. Holographic@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte também
* [Interações instinctuais](interaction-fundamentals.md)

 

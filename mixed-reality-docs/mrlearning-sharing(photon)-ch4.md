---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416007"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>Sincronizando os movimentos de objetos compartilhados

Nesta lição, vamos aprenderá como compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada podem colaborar em conjunto e exibir as interações uns dos outros. Essa lição aproveita o iniciador Lunar que foi criado como parte do [base de dados de módulo tutoriais](mrlearning-base.md).

Objetivos:

- Inclua o iniciador Lunar como o modelo 3D para ser compartilhado
- Configure seu projeto para compartilhar os movimentos do modelo 3D.
- Saiba como criar um aplicativo básico de colaboração de multiusuário

### <a name="instructions"></a>Instruções

1. Salve a cena da lição anterior (CTRL + S). Você pode renomeá-lo "HLSharedProjectMainPart4.unity" para que ele seja mais fácil de encontrar quando precisar dele novamente.

2. Na janela do projeto, os ativos > pasta de Scripts, clique duas vezes na GenericNetSync para abri-lo no Visual Studio ou que nunca code editor que você está usando.  ![](images/module3chapter4updatestep2.png)

3. Em linhas 34 e 38, remova o "/ /" para ativar o código para a tabela que serão usadas nesta lição.  Em seguida, salve o arquivo. ![](images/module3chapter4updatestep3.png)

4. Na janela do projeto, clique duas vezes no arquivo PhotonRoom.cs nos ativos > pasta de Scripts novamente abri-lo no Visual Studio. ![](images/module3chapter4updatestep4.png)

5. Assim como na etapa 3, é preciso remover o "/ /" para ativar o código em linhas, 25, 26 e 106.![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. Na exibição de hierarquia, selecione o objeto NetworkRoom.![](images/module3chapter4updatestep6.png)

7. Na exibição do projeto, navegue até ativos > recursos > pré-fabricados. Primeiro, arraste e solte pré-fabricado tabela para o slot de "Tableprefab" na classe PhotonRoom. Em seguida arraste e solte pré-fabricado LunarModule para o slot "Módulo pré-fabricado" na classe PhotonRoom. ![](images/module3chapter4updatestep7.png)

   Observação: Se você clicar em um dos objetos pré-fabricado e versão, o Inspetor de alternará para o objeto. Clique em, arraste, solte e liberar cada objeto em seu slot apropriado.



8. Agora, clique na seta à esquerda de "MixedRealityPlayspace" e mover o objeto do jogo filho, "MainCamera" para baixo em pré-fabricado "SharedPlayground". Em seguida, exclua o pré-fabricado "MixedRealityPlayspace" (para excluir, selecione pré-fabricado e toque em "excluir" em seu teclado).

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

Observação:  Certifique-se de que as posições de câmera principal e o SharedPlayground serão definidas como 0, 0,0.

9. Crie um novo objeto do jogo definido como um objeto filho ao objeto pai "SharedPlayground" (para criar um novo objeto, clique com botão direito no objeto pai e selecione "criar vazio"). 

10. Com o novo objeto selecionado na sua hierarquia, altere o nome do objeto para "TableAnchor" no painel Inspetor. Além disso, clique em "adicionar o componente" e pesquise o componente "TableAnchor". Selecioná-lo e adicioná-lo ao objeto. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Observação: definir o posicionamento para x = 1, 0,55 = y e z = 2. Além disso, definir a rotação com y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. Agora no painel de projeto, na pasta "pré-fabricados", arraste pré-fabricado "table" para o objeto filho de "TableAnchor" você acabou de criar.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. Por fim, no objeto "DebugWindow", altere a largura para 80 e a altura para 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Parabéns

Quando isso for concluído, todos os usuários que unem a seu projeto do Unity podem se mover o iniciador Lunar. Todos os movimentos são sincronizados para que cada usuário possa ver as interações uns dos outros. Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhado completos. 

Embora todos os usuários estão conectados como parte de uma experiência de compartilhado e podem ver os movimentos relativos dos objetos, o aplicativo é ainda não é possível alinhar com precisão avatares e objetos para que os usuários locais veem uns aos outros e objetos no mesmo local físico dentro do mundo. Para ancorar um local experiências compartilhadas, cada dispositivo requer um entendimento comum do ambiente físico. Neste módulo, vamos fazer isso usando [âncoras espacial do Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), que será implementado na próxima lição.

Antes de prosseguir para a próxima lição, é necessário concluir o módulo de aprendizagem do ASA, que abordará Noções básicas do ASA, conta do Azure e criação de recursos e outros blocos de prédios fundamentais necessárias antes de nós pode integrar isso em nossa experiência compartilhada.

[Próxima lição: Sharing(Photon) lição 5](mrlearning-sharing(photon)-ch5.md)


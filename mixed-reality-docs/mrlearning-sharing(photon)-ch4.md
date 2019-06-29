---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b729de818dfa21df8fbce782a24a611a365ac795
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465221"
---
# <a name="synchronizing-shared-object-movements"></a>Sincronizando as movimentações de objeto compartilhadas

Nesta lição, aprendemos como compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada podem colaborar em conjunto e exibir as interações uns dos outros. Essa lição aproveita o iniciador Lunar que foi criado como parte do [base de dados de módulo tutoriais](mrlearning-base.md).

Objetivos:

- Inclua o iniciador lunar como o modelo 3D para ser compartilhado
- Configure seu projeto para compartilhar os movimentos do modelo 3D.
- Saiba como criar um aplicativo básico de colaboração de multiusuário

### <a name="instructions"></a>Instruções


1. Salve a cena da lição anterior (CTRL + + S). Você pode chamá-lo HLSharedProjectMainPart4.unity para que ele seja mais fácil de encontrar quando necessário.

2. Na janela do projeto, nos ativos -> pasta de Scripts, clique duas vezes em GenericNetSync para abri-lo no Visual Studio ou que nunca code editor que você está usando.  ![](images/module3chapter4updatestep2.png)

3. Em linhas 34 e 38, remova o / / para ativar o código para a tabela que serão usadas nesta lição. em seguida, salve o arquivo. ![](images/module3chapter4updatestep3.png)

4. Na janela do projeto, clique duas vezes no arquivo PhotonRoom.cs nos ativos -> pasta de Scripts para abri-lo no Visual Studio. ![](images/module3chapter4updatestep4.png)

5. Assim como na etapa 3, é preciso remover o / / para ativar o código em linhas, 25, 26 e 106.![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. Na exibição de hierarquia, selecione o objeto NetworkRoom.![](images/module3chapter4updatestep6.png)

7. Na exibição do projeto, navegue até ativos -> recursos -> pré-fabricados. Primeiro, arraste e solte pré-fabricado tabela para o slot Tableprefab na classe PhotonRoom. Em seguida arraste e solte pré-fabricado LunarModule no módulo pré-fabricado slot na classe PhotonRoom. ![](images/module3chapter4updatestep7.png)

   Observação: Se você clicar em um dos objetos pré-fabricado e versão, o Inspetor de alternará para o objeto. Clique em, arraste, solte e liberar cada objeto em seu slot apropriado.



8. Clique na seta à esquerda do MixedRealityPlayspace e mover o objeto do jogo filho, MainCamera para baixo em SharedPlayground pré-fabricado. Em seguida, exclua pré-fabricado, MixedRealityPlayspace, excluir, selecione pré-fabricado e toque em "excluir" em seu teclado).
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

Observação:  Certifique-se de que as posições de câmera principal e o SharedPlayground serão definidas como 0, 0,0.

9. Crie um novo objeto do jogo definido como um objeto filho ao objeto pai SharedPlayground para criar um novo objeto. Clique com o botão direito no objeto pai e selecione Criar vazio. 

10. Com o novo objeto selecionado na sua hierarquia, altere o nome do objeto para TableAnchor no painel Inspetor. Além disso, clique em Adicionar componente e pesquise o componente TableAnchor. Selecioná-lo e adicioná-lo ao objeto. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Observação: Definir o posicionamento para x = 1, 0,55 = y e z = 2. Além disso, definir a rotação com y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. Agora no painel do projeto na pasta pré-fabricados, arraste pré-fabricado tabela para o objeto filho de "TableAnchor" você acabou de criar.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. Por fim, no objeto DebugWindow, altere a largura para 80 e a altura para 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Parabéns


Quando isso for concluído, todos os usuários que unem a seu projeto do Unity podem se mover o iniciador lunar. Todos os movimentos são sincronizados para que cada usuário possa ver as interações uns dos outros. Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhado e completo. 

Embora todos os usuários estão conectados como parte de uma experiência de compartilhado e podem ver os movimentos relativos dos objetos, o aplicativo é ainda não é possível alinhar com precisão avatares e objetos para que os usuários locais veem uns aos outros e objetos no mesmo local físico dentro do mundo. Para ancorar um local experiências compartilhadas, cada dispositivo requer um entendimento comum do ambiente físico. Neste módulo, podemos vai fazer isso usando [âncoras espacial do Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) que serão implementados na próxima lição.

Antes de prosseguir para a próxima lição, é necessário concluir o módulo de aprendizagem do ASA que abrange conceitos básicos do ASA, conta do Azure e criação de recursos e outros blocos de prédios fundamentais necessárias antes de nós pode integrar isso em nossa experiência compartilhada.

[Próxima lição: Sharing(Photon) lição 5](mrlearning-sharing(photon)-ch5.md)


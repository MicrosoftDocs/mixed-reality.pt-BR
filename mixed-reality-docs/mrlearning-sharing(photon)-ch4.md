---
title: Módulo de compartilhamento de aprendizagem do MR para o HoloLens 2
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 77ae779b4bb32dd66a722c9793d1b83c4a64ae2e
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485671"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Compartilhando movimentos de objetos com vários usuários

Neste tutorial, aprenderemos como compartilhar os movimentos dos objetos para que todos os participantes de uma sessão compartilhada possam colaborar juntos e exibir as interações de cada um deles. Esta lição baseia-se no iniciador lunar criado como parte dos [tutoriais do módulo base](mrlearning-base.md).

Seus

- Traga o iniciador lunar como o modelo 3D a ser compartilhado
- Configure seu projeto para compartilhar os movimentos do modelo 3D.
- Saiba como criar um aplicativo de colaboração de vários usuários básico

## <a name="instructions"></a>Instruções


1. Salve a cena da lição anterior (Control + S). Você pode nomeá-lo, HLSharedProjectMainPart4. Unity, para que seja mais fácil encontrá-lo quando precisar.

2. Na janela do projeto, na pasta ativos-> scripts, clique duas vezes em GenericNetSync para abri-lo no Visual Studio ou no editor de código que você está usando.  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. Nas linhas 34 e 38, remova o//para ativar o código da tabela que usaremos nesta lição. em seguida, salve o arquivo. 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. Na janela do projeto, clique duas vezes no arquivo PhotonRoom.cs na pasta Assets-> scripts para abri-lo no Visual Studio. 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Assim como na etapa 3, precisamos remover o//para ativar o código nas linhas 25, 26 e 106.

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. Na exibição hierarquia, selecione o objeto NetworkRoom.

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. Na exibição do projeto, navegue até ativos-> recursos-> pré-fabricados. Primeiro, arraste e solte a tabela pré-fabricado para o slot Tableprefab na classe PhotonRoom. Em seguida, arraste e solte o RocketLauncherCompleteVariantprefab para o slot pré-fabricado do módulo na classe PhotonRoom.

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   Observação: Se você clicar em um dos objetos pré-fabricado e liberar, o Inspetor alternará para esse objeto. Clique em, arraste, solte e libere cada objeto para seu slot apropriado.

8. Clique na seta à esquerda de MixedRealityPlayspace e mova o objeto de jogo filho, MainCamera para baixo até o SharedPlayground pré-fabricado. Em seguida, exclua o pré-fabricado, MixedRealityPlayspace, para excluir, selecione o pré-fabricado e toque em "excluir" no teclado).
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

>Observação:  Verifique se as posições principal da câmera e do SharedPlayground estão definidas como 0, 0, 0.
>

9. Crie um novo objeto Game definido como um objeto filho para o objeto pai SharedPlayground para criar um novo objeto. Clique com o botão direito do mouse no objeto pai e selecione criar vazio. 

10. Com o novo objeto selecionado em sua hierarquia, altere o nome do objeto para TableAnchor no painel de Inspetor. Além disso, clique em Adicionar componente e procure o componente TableAnchor. Selecione-o e adicione-o ao objeto. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. Agora, no painel projeto na pasta pré-fabricados, arraste a tabela pré-fabricado para o objeto filho "TableAnchor" que você acabou de criar.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. Por fim, no objeto DebugWindow, altere a largura para 50 e a altura para 20.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a>Parabéns


Depois que isso for concluído, todos os usuários que ingressarem em seu projeto do Unity poderão mover o iniciador lunar. Todos os movimentos são sincronizados para que cada usuário possa ver as interações das outras pessoas. Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhadas com recursos completos. 

Embora todos os usuários estejam conectados como parte de uma experiência compartilhada e possam ver os movimentos relativos dos objetos, o aplicativo ainda não consegue alinhar com precisão os avatars e os objetos para que os usuários locais vejam uns aos outros e os objetos no mesmo local dentro do físico países. Para ancorar experiências compartilhadas locais, cada dispositivo requer uma compreensão comum do ambiente físico. Neste módulo, faremos isso usando o asa ( [âncoras espaciais) do Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) que será implementado na próxima lição.

Antes de prosseguir para a próxima lição, precisaremos concluir o módulo de aprendizado do ASA que aborda noções básicas do ASA, criação de contas e recursos do Azure e outros blocos de edifícios fundamentais necessários para que possamos integrá-lo à nossa experiência compartilhada.

[Próxima lição: 5. Integrar Âncoras Espaciais do Azure em uma experiência compartilhada](mrlearning-sharing(photon)-ch5.md)


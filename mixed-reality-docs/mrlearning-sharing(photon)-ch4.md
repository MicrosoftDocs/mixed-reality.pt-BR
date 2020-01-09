---
title: Tutoriais de funcionalidades de vários usuários-4. Compartilhando movimentos de objetos com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: f523aabd74b9267b3f7f5024d8af46110e43c32a
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334280"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. compartilhando movimentos de objeto com vários usuários

Neste tutorial, você aprenderá a compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada possam colaborar e exibir as interações de cada uma das outras. Esta lição baseia-se no iniciador lunar criado como parte dos [tutoriais do módulo base](mrlearning-base.md).

## <a name="objectives"></a>Objetivos

- Traga o iniciador lunar como o modelo 3D a ser compartilhado
- Configurar seu projeto para compartilhar os movimentos do modelo 3D
- Saiba como criar um aplicativo de colaboração de vários usuários básico

## <a name="instructions"></a>Instruções

1. Salve a cena da lição anterior (Control + S). Você pode nomeá-lo de HLSharedProjectMainPart4. Unity para que seja mais fácil encontrá-lo quando precisar.

2. Na janela do projeto, na pasta ativos-> scripts, clique duas vezes em GenericNetSync para abri-lo no Visual Studio ou no editor de código que você está usando.  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. Nas linhas 34 e 38, remova "//" para ativar o código da tabela que será usada nesta lição. Em seguida, salve o arquivo.

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. Na janela do projeto, clique duas vezes no arquivo PhotonRoom.cs na pasta Assets-> scripts para abri-lo no Visual Studio.

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Assim como na etapa 3, precisamos remover "//" para ativar o código nas linhas 25, 26 e 106.

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. Na exibição hierarquia, selecione o objeto NetworkRoom.

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. Na exibição do projeto, navegue até ativos-> recursos-> pré-fabricados. Primeiro, arraste e solte a tabela pré-fabricado para o slot Tableprefab na classe PhotonRoom. Em seguida, arraste e solte o RocketLauncherCompleteVariantprefab para o slot pré-fabricado do módulo na classe PhotonRoom.

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >Se você clicar em um dos objetos pré-fabricado e liberar, o Inspetor alternará para esse objeto. Clique em, arraste, solte e libere cada objeto para seu slot apropriado.

8. Clique na seta à esquerda de MixedRealityPlayspace e mova o objeto de jogo filho MainCamera para baixo para o SharedPlayground pré-fabricado. Em seguida, exclua o pré-fabricado, MixedRealityPlayspace selecionando o pré-fabricado e toque em "excluir" no teclado).

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >Verifique se as posições principal da câmera e do SharedPlayground estão definidas como 0, 0, 0.

9. Selecione o objeto "SharedPlayground" e clique com o botão direito do mouse para escolher a opção "criar vazio" para criar um objeto de jogo vazio como um filho do objeto de jogo "SharedPlayground".

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. Com o novo objeto selecionado em sua hierarquia, altere o nome do objeto para TableAnchor no painel de Inspetor. Além disso, clique em Adicionar componente e procure o componente TableAnchor. Selecione-o e adicione-o ao objeto.

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. No painel projeto na pasta pré-fabricados, arraste a tabela pré-fabricado para o objeto filho "TableAnchor" que você acabou de criar.

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. No objeto DebugWindow, altere a largura para 50 e a altura para 20.

    ![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a>Parabéns

Quando isso for concluído, procure localizar o módulo lunar. Depois disso, todos os usuários que ingressarem em seu projeto do Unity poderão mover o iniciador lunar.  Todos os movimentos são sincronizados para que cada usuário possa ver as interações das outras pessoas. Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhadas com recursos completos.

Embora todos os usuários estejam conectados como parte de uma experiência compartilhada e possam ver os movimentos relativos dos objetos, o aplicativo ainda não consegue alinhar precisamente os avatars e objetos para que os usuários locais não possam ver uns aos outros e os objetos no mesmo local dentro do mundo físico. Para ancorar experiências compartilhadas locais, cada dispositivo requer uma compreensão comum do ambiente físico. Neste módulo, faremos isso usando o asa ( [âncoras espaciais) do Azure](<https://azure.microsoft.com//services/spatial-anchors/>) que será implementado na próxima lição.

Antes de prosseguir para a próxima lição, precisaremos concluir o módulo de aprendizagem do ASA que aborda as noções básicas do ASA, a criação de contas e recursos do Azure, bem como outros blocos de edifícios fundamentais necessários para que possamos integrá-lo à nossa experiência compartilhada.

[Próxima lição: 5. integração das âncoras espaciais do Azure em uma experiência compartilhada](mrlearning-sharing(photon)-ch5.md)

---
title: Tutoriais de recursos multiusuário – 4. Compartilhar movimentações de objeto com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031245"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Compartilhar movimentações de objeto com vários usuários

Neste tutorial, você aprenderá a compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada possam colaborar e exibir as interações uns dos outros. Esta lição baseia-se no Iniciador Lunar criado como parte dos [Tutoriais do Módulo Base](mrlearning-base.md).

## <a name="objectives"></a>Objetivos

- Traga o iniciador lunar como o modelo 3D a ser compartilhado
- Configurar seu projeto para compartilhar os movimentos do modelo 3D
- Saiba como criar um aplicativo básico de colaboração de vários usuários

## <a name="instructions"></a>Instruções

1. Salve a cena da lição anterior (Control+S). Você pode dar a ela o nome de HLSharedProjectMainPart4.Unity para que seja mais fácil encontrá-la quando precisar.

2. Na janela Projeto, na pasta Ativos->Scripts, clique duas vezes em GenericNetSync para abri-la no Visual Studio ou no editor de código que você está usando.  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. Nas linhas 34 e 38, remova "//" para ativar o código da tabela que será usada nesta lição. Em seguida, salve o arquivo.

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. Na janela Projeto, clique duas vezes no arquivo PhotonRoom.cs na pasta Ativos->Scripts para abri-lo no Visual Studio.

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Assim como na Etapa 3, precisamos remover "//" para ativar o código nas linhas 25, 26 e 106.

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. Na exibição Hierarquia, selecione o objeto NetworkRoom.

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. Na exibição do projeto, navegue até Ativos->Recursos->Pré-Fabricados. Primeiro, arraste e solte o pré-fabricado Tabela para o slot Tableprefab na classe PhotonRoom. Em seguida, arraste e solte o RocketLauncherCompleteVariantprefab para o slot Pré-Fabricado do Módulo na classe PhotonRoom.

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >Se você clicar em um dos objetos pré-fabricado e soltar, o Inspetor alternará para esse objeto. Clique, arraste, solte e libere cada objeto para seu slot apropriado.

8. Clique na seta à esquerda de MixedRealityPlayspace e mova o objeto de jogo filho MainCamera para baixo para o pré-fabricado SharedPlayground. Em seguida, exclua o pré-fabricado MixedRealityPlayspace selecionando o pré-fabricado e toque em "delete" no teclado).

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >Verifique se as posições de SharedPlayground e Câmera Principal estão definidas como 0,0,0.

9. Selecione o objeto "SharedPlayground" e clique com o botão direito do mouse para escolher a opção "criar vazio" para criar um objeto de jogo vazio como um filho do objeto de jogo "SharedPlayground".

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. Com o novo objeto selecionado em sua hierarquia, altere o nome do objeto para TableAnchor no painel de Inspetor. Além disso, clique em Adicionar Componente e pesquise o componente TableAnchor. Selecione-o e adicione-o ao objeto.

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. No painel Projeto na pasta Pré-Fabricados, arraste a tabela Pré-Fabricado para o objeto filho "TableAnchor" que você acabou de criar.

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>Parabéns

Quando isso for concluído, procure localizar o módulo lunar. Depois disso, todos os usuários que ingressarem em seu projeto do Unity poderão mover o iniciador lunar.  Todos os movimentos são sincronizados para que cada usuário possa ver as interações das outras pessoas. Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhadas com recursos completos.

Embora todos os usuários estejam conectados como parte de uma experiência compartilhada e possam ver os movimentos relativos dos objetos, o aplicativo ainda não consegue alinhar os avatars e os objetos com precisão, de modo que os usuários locais não conseguem ver uns aos outros e os objetos no mesmo local dentro do mundo físico. Para ancorar experiências compartilhadas locais, cada dispositivo requer uma compreensão comum do ambiente físico. Neste módulo, faremos isso usando ASA ([Âncoras Espaciais do Azure](<https://azure.microsoft.com//services/spatial-anchors/>)), que serão implementadas na próxima lição.

Antes de prosseguir para a próxima lição, precisaremos concluir o Módulo de Aprendizagem de ASA que aborda as noções básicas do ASA, a criação de contas e recursos do Azure, bem como outros blocos de construção fundamentais necessários antes que seja possível integrá-los à nossa experiência compartilhada.

[Próxima lição: 5. Integrar Âncoras Espaciais do Azure em uma experiência compartilhada](mrlearning-sharing(photon)-ch5.md)

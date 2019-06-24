---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326579"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>Sincronizando os movimentos de objetos compartilhados

Nesta lição, vamos aprenderá como compartilhar os movimentos de objetos para que todos os participantes de uma sessão compartilhada podem colaborar em conjunto e exibir as interações uns dos outros. Essa lição aproveita o iniciador Lunar que foi criado como parte do [base de dados de módulo tutoriais](mrlearning-base.md).

Objetivos:

- Importar o iniciador Lunar concluído como o modelo 3D sejam compartilhados
- Configure seu projeto para compartilhar os movimentos do modelo 3D.
- Saiba como criar um aplicativo básico de colaboração de multiusuário

### <a name="instructions"></a>Instruções

1. Salve a cena da lição anterior (CTRL + S). Você pode renomeá-lo "HLSharedProjectMainPart4.unity" para que ele seja mais fácil de encontrar quando precisar dele novamente.

2. Exclua o objeto "NetworkLobby" (selecionando-o e pressionando a tecla delete). Além disso, vá para a pasta "pré-fabricados" da lição 2 e excluir pré-fabricado "NetworkLobby" também.

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. Importar um novo pacote personalizado (como na etapa 2 da lição 2) e importe as [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) e o [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. Agora, na pasta "pré-fabricados", arraste pré-fabricado "NetworkLobby" novo para a hierarquia. 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> Observação: os dois pacotes que importamos nas etapas anteriores atualizado pré-fabricado "NetworkLobby". Ele evita que você muita digitação!

5. Agora, clique na seta à esquerda de "MixedRealityPlayspace" e mover o objeto do jogo filho, "MainCamera" para baixo em pré-fabricado "SharedPlayground". Em seguida, exclua o pré-fabricado "MixedRealityPlayspace" (para excluir, selecione pré-fabricado e toque em "excluir" em seu teclado).

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. Crie um novo objeto do jogo definido como um objeto filho ao objeto pai "SharedPlayground" (para criar um novo objeto, clique com botão direito no objeto pai e selecione "criar vazio").
7. Com o novo objeto selecionado na sua hierarquia, altere o nome do objeto para "TableAnchor" no painel Inspetor. Além disso, clique em "adicionar o componente" e pesquise o componente "TableAnchor". Selecioná-lo e adicioná-lo ao objeto.

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Observação: definir o posicionamento para x = 1, 0,55 = y e z = 2. Além disso, definir a rotação com y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. Agora no painel de projeto, na pasta "pré-fabricados", arraste pré-fabricado "table" para o objeto filho de "TableAnchor" você acabou de criar.

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. Selecione "NetworkRoom", um objeto filho em "NetworkLobby" na hierarquia e clique em "Adicionar componente" no painel Inspetor e procure "PhotonView" e adicione o script para o "*NetworkRoom*" objeto.

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. Por fim, no objeto "DebugWindow", altere a largura para 80 e a altura para 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Parabéns

Quando isso for concluído, todos os usuários que unem a seu projeto do Unity podem se mover o iniciador Lunar. Todos os movimentos são sincronizados para que cada usuário possa ver as interações uns dos outros. Esses conceitos servem como os blocos de construção fundamentais para experiências de colaboração compartilhado completos. 

Embora todos os usuários estão conectados como parte de uma experiência de compartilhado e podem ver os movimentos relativos dos objetos, o aplicativo é ainda não é possível alinhar com precisão avatares e objetos para que os usuários locais veem uns aos outros e objetos no mesmo local físico dentro do mundo. Para ancorar um local experiências compartilhadas, cada dispositivo requer um entendimento comum do ambiente físico. Neste módulo, vamos fazer isso usando [âncoras espacial do Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), que será implementado na próxima lição.

Antes de prosseguir para a próxima lição, é necessário concluir o módulo de aprendizagem do ASA, que abordará Noções básicas do ASA, conta do Azure e criação de recursos e outros blocos de prédios fundamentais necessárias antes de nós pode integrar isso em nossa experiência compartilhada.

[Próxima lição: Sharing(Photon) lição 5](mrlearning-sharing(photon)-ch5.md)


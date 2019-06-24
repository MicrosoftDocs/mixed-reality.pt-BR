---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327890"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Âncoras espaciais do Azure e experiências compartilhadas

Nesta lição, podemos aprenderá a integrar espacial âncoras ASA (Azure) em nossa experiência compartilhada. ASA permite que vários dispositivos localizados ter um entendimento comum se o seu ambiente físico para virtual de ancoragem experiências, de modo que todos os participantes ver objetos no mesmo local físico.

Antes de continuar com esta lição, é necessário concluir o módulo de aprendizagem do ASA, que abordará Noções básicas do ASA, conta do Azure e criação de recursos e outros blocos de prédios fundamentais que são necessários para que podemos pode integrar o ASA em nossa experiência compartilhada.

Objetivos:

- Integrar o ASA em uma experiência de compartilhado para o alinhamento de vários dispositivo
- Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência de compartilhado local

### <a name="instructions"></a>Instruções

1. Salve o projeto da lição anterior (CTRL + S) e nome "HLSharedProjectMainPart5.unity" para que ele seja mais fácil de encontrar quando precisar dele novamente.

2. Selecione pré-fabricado TableAnchor sob o objeto pai "MixedRealityPlayspace" e excluí-lo.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. Assim como algumas das lições anteriores, importar um novo pacote personalizado que você pode obter [aqui.](placeholderlink)

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. Depois que ele é importado, pegue a âncora de tabela atualizada recentemente (a partir do pacote do unity importado na etapa anterior) da pasta "pré-fabricados" no painel de projeto e solte-o no objeto pai "MixedRealityPlayspace".

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. Expanda o objeto pai "MixedRealityPlayspace" e, em seguida, o objeto "TableAnchor" e, em seguida, expanda o objeto "botões". 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. Agora, na hierarquia, selecione "ShareAzureAnchorButton" e mover sua atenção para o painel do Inspetor. Role para baixo até o menu suspenso, mostrado na imagem abaixo e selecione "AnchorModuleScript" e clique em "ShareAnchorNetework()".

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. Assim como a etapa 6, selecione "GetAzureAnchorButton" e mova sua atenção para o painel do Inspetor. Role para baixo até o menu suspenso, mostrado na imagem abaixo e selecione "AnchorModuleScript" e clique em "GetSharedAnchorNetwork()". Em seguida, salve.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Parabéns

Nesta lição, você aprendeu como a integração poderosas novas espacial âncoras do Azure para alinhar os dispositivos localizados em uma experiência compartilhada! Esta lição também conclui o módulo de compartilhamento. Aprendemos como definir uma nova conta Photon, integrar Photon e TROCADILHO em um novo aplicativo do Unity, configurando avatares e objetos compartilhados e, finalmente, alinhando vários participantes usando o ASA. 


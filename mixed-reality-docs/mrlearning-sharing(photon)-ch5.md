---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465209"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Âncoras espacial do Azure e experiências compartilhadas

Nesta lição, aprendemos como integrar espacial âncoras ASA (Azure) em nossa experiência compartilhada. ASA permite que vários dispositivos localizados ter uma referência comum se o ambiente físico for para experiências de âncora virtual, de modo que todos os participantes ver objetos no mesmo local físico.

Antes de continuar com esta lição, é necessário concluir o módulo de aprendizagem do ASA, que abordará Noções básicas do ASA, conta do Azure e criação de recursos e outros blocos de prédios fundamentais que são necessários para que podemos pode integrar o ASA em nossa experiência compartilhada.

Objetivos:

- Integrar o ASA em uma experiência de compartilhado para o alinhamento de vários dispositivo
- Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência de compartilhado local

### <a name="instructions"></a>Instruções

1. Salve o projeto da lição anterior (CTRL + S) e nome "HLSharedProjectMainPart5.unity" para que ele seja mais fácil de encontrar quando precisar dele novamente.

2. Selecione pré-fabricado TableAnchor sob o objeto pai MixedRealityPlayspace e excluí-lo.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  Na exibição do projeto, acesse ativos -> recursos -> pré-fabricados e, em seguida, arraste pré-fabricado TableAnchor sobre o objeto SharedPlayground para torná-lo um filho.
4.  Expanda o objeto pai de MixedRealityPlayspace, objeto TableAnchor e também o objeto de botões. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Agora na hierarquia, selecione ShareAzureAnchorButton e mover sua atenção para o painel Inaspector. Role para baixo até o menu suspenso mostrado na imagem abaixo e selecione AnchorModuleScript e clique em ShareAnchorNetework().

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Selecione GetAzureAnchorButton (consulte a etapa 4), e mover sua atenção para o painel do Inspetor. Role para baixo até o menu suspenso mostrado na imagem abaixo, AnchorModuleScript e clique em GetSharedAnchorNetwork() e selecione Salvar.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Parabéns

Nesta lição, você aprendeu como a integração poderosas novas espacial âncoras do Azure para alinhar os dispositivos localizados em uma experiência compartilhada! Esta lição também conclui o módulo de compartilhamento. Aprendemos como definir uma nova conta Photon, integrar Photon e TROCADILHO em um novo aplicativo do Unity, configurando avatares e objetos compartilhados e, finalmente, alinhando vários participantes usando o ASA. 


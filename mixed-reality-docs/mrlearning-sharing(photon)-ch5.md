---
title: Tutoriais de funcionalidades de vários usuários-5. Integrando âncoras espaciais do Azure em uma experiência compartilhada
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: cb4645d197238d8712719625bf11eac0650a8246
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701865"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integrando âncoras espaciais do Azure em uma experiência compartilhada

Nesta lição, aprenderemos a integrar o ASA (âncoras espaciais) do Azure em nossa experiência compartilhada. O ASA permite que vários dispositivos colocalizados tenham uma referência comum se o seu ambiente físico for ancorar experiências virtuais de forma que todos os participantes vejam objetos no mesmo local físico.

Antes de prosseguir com esta lição, precisaremos concluir o módulo de aprendizagem do ASA, que abordará as noções básicas do ASA, a criação de contas e recursos do Azure e outros blocos de edifícios fundamentais que são necessários antes que possamos integrar o ASA à nossa experiência compartilhada.

Seus

- Integre o ASA em uma experiência compartilhada para o alinhamento de vários dispositivos.
- Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência compartilhada local.

### <a name="instructions"></a>Instruções

1. Salve o projeto da lição anterior (Control + S) e nomeie-o como "HLSharedProjectMainPart5. Unity" para que seja mais fácil localizá-lo quando você precisar dele novamente.

2. Selecione TableAnchor pré-fabricado abaixo do objeto pai MixedRealityPlayspace e exclua-o.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  Na exibição de projeto, acesse ativos-> recursos-> pré-fabricados e arraste o TableAnchor pré-fabricado sobre o objeto SharedPlayground para torná-lo um filho.
4.  Expanda o objeto pai MixedRealityPlayspace, o objeto TableAnchor e expanda o objeto Buttons também. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Agora, na hierarquia, selecione ShareAzureAnchorButton e mova sua atenção para o painel do inaspectr. Role para baixo até o menu suspenso mostrado na imagem abaixo e selecione AnchorModuleScript e clique em ShareAnchorNetework ().

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Selecione GetAzureAnchorButton (consulte a etapa 4) e mude sua atenção de volta para o painel inspetor. Role para baixo até o menu suspenso mostrado na imagem abaixo e selecione AnchorModuleScript e clique em GetSharedAnchorNetwork () e em salvar.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Para testar o módulo de compartilhamento, clique no botão "iniciar sessão do ASA do Azure", que iniciará a sessão de âncoras espaciais do Azure e, em seguida, criará a âncora do Azure clicando no botão "criar âncora do Azure" e aguarde um momento até que a âncora do Azure seja criada. Depois que a âncora do Azure for criada, clique no botão "compartilhar âncora do Azure" para compartilhar a âncora do Azure criada do HoloLens.

7. Para receber a âncora do Azure compartilhada em outro HoloLens, clique em "iniciar a sessão do ASA do Azure" para iniciar e entrar na sessão atual do ASA e clique no botão "obter âncora do Azure" para obter a âncora do Azure compartilhada do outro HoloLens.

   > Observação: Todos os detalhes das ações correspondentes nos botões individuais serão exibidos na janela Depurar.

## <a name="congratulations"></a>Parabéns

Nesta lição, você aprendeu a integrar as novas âncoras espaciais do Azure para alinhar dispositivos colocalizados em uma experiência compartilhada! Esta lição também conclui o módulo de compartilhamento. Aprendemos como configurar uma nova conta do Photon, integrar o Photon e o trocadilho em um novo aplicativo Unity, configurar avatars e objetos compartilhados e, finalmente, alinhar vários participantes usando o ASA. 


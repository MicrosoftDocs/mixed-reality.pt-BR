---
title: Módulo do ASA do Sr Learning âncora espacial do Azure no HoloLens 2
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: cfd6ac9997a8a5d962603922f473bd6fc5d708ed
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485731"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Exibindo comentários de âncora espacial do Azure

Nesta lição, você aprenderá a fornecer aos usuários comentários sobre a descoberta de âncora, eventos e status ao usar âncoras espaciais do Azure.

## <a name="objectives"></a>Objetivos

* Saiba como configurar um painel de interface do usuário que exibe informações importantes sobre a sessão atual do ASA

* Entender e explorar os elementos de comentários que o SDK do ASA disponibiliza para os usuários

## <a name="instructions"></a>Instruções

### <a name="set-up-asa-feedback-ui-panel"></a>Configurar o painel de IU de comentários do ASA

1. Nesta lição, não estamos usando os botões "SaveAnchorToDisk" e "ShareAnchor", portanto, selecione ambos os botões e desmarque a caixa de seleção no painel de Inspetor (como mostrado abaixo) para ocultar esses botões.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Em seguida, crie o painel de instruções. Comece clicando com o botão direito no botão "instruções", passe o mouse sobre "objeto 3D" e selecione "textmeshpro-Text".

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. Ajuste a escala e o posicionamento do texto para que ele corresponda às instruções em sua cena. Além disso, verifique se o alinhamento de todo o texto está centralizado. Em seguida, exclua o texto de exemplo do editor de texto, conforme mostrado na imagem abaixo.

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Altere o nome do objeto TextMeshPro para "FeedbackPanel".
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. No painel projeto, selecione "ativos" e clique com o botão direito do mouse e selecione "Mostrar no Explorer".
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Agora, clique [aqui](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) para baixar os arquivos necessários nas próximas etapas.

6. Quando o Explorer for aberto, selecione a pasta ativos, em seguida, a pasta "ASAmodulesAssets" e copie o script de comentários âncora e os arquivos de script do módulo âncora para a pasta. 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Observação: se você receber um pop-up perguntando se deseja substituir o antigo ou manter o antigo, certifique-se de selecionar substituir.

7. Agora, retorne à pasta ativos. Em seguida, vá para a pasta "AzureSpatialAnchorsPlugin" e, em seguida, a pasta de exemplos e, por fim, a pasta scripts e copie o wrapper de demonstração de âncoras espaciais do Azure nessa pasta. 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Agora que os arquivos foram carregados, verifique se o texto "feedbackpanel" está selecionado na hierarquia ASA_feedback e clique em "Adicionar componente" e adicione o script de comentários de âncora pesquisando-o e selecionando-o quando ele for exibido. 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Arraste o objeto de texto "feedbackPanel" da hierarquia ASA_Feedback para o slot vazio abaixo do script, como mostrado na imagem abaixo. 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>Parabéns

Nesta lição, aprendemos como criar um painel de interface do usuário para exibir o status atual da experiência de ancoragem espacial do Azure para fornecer aos usuários comentários em tempo real.



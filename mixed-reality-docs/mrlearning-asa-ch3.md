---
title: Módulo do ASA de aprendizado do MR âncora espacial do Azure em 2 HoloLens
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326351"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Exibindo comentários de âncora espacial do Azure

Nesta lição, você saberá mais sobre como fornecer aos usuários com comentários sobre a descoberta de âncora, eventos e status ao usar âncoras espacial do Azure.

Objetivos:

* Saiba como configurar um painel de interface do usuário que exibe informações importantes sobre a sessão atual do ASA

* Compreender e explorar os elementos de comentários que o SDK do ASA torna disponível para usuários

  

## <a name="instructions"></a>Instruções

### <a name="set-up-asa-feedback-ui-panel"></a>Configurar o painel de interface do usuário de comentários do ASA

1. Nesta lição, não estamos usando "SaveAnchorToDisk" e botões de "ShareAnchor" então, selecione ambos os botões e desmarque a caixa de seleção no painel Inspetor (conforme mostrado abaixo) para ocultar esses botões.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Em seguida, crie o painel de instrução. Inicie clicando com o botão direito no botão "instruções", passe o mouse sobre "objetos 3D" e selecione "textmeshpro-text".

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. Ajuste a escala e o posicionamento do texto para que corresponda com as instruções na sua cena. Além disso, verifique se que o alinhamento para todo o texto é centralizado. Exclua o texto de exemplo do editor de texto, conforme mostrado na imagem abaixo.


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Altere o nome do objeto TextMeshPro para "FeedbackPanel".
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. No painel de projeto, selecione "ativos" e clique com botão direito e selecione "Mostrar no explorer".
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Agora, clique em [aqui](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) baixar os arquivos necessários nas próximas etapas.

6. Depois que o explorer é aberta, selecione a pasta ativos e, em seguida, a pasta "ASAmodulesAssets" e copie o script de comentários de âncora e os arquivos de script de módulo de âncora para a pasta. 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Observação: se você receber um pop-up perguntando se você gostaria de substituir o antigo ou manter o antigo Certifique-se de selecione Substituir.

7. Agora, volte para a pasta ativos. Em seguida, vá para a pasta "AzureSpatialAnchorsPlugin", a pasta de exemplos e, finalmente, a pasta de scripts e copie o wrapper de demonstração âncoras espacial do Azure para essa pasta. 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Agora que os arquivos são carregados, verifique se o texto "feedbackpanel" está selecionado na hierarquia de ASA_feedback e clique em "adicionar o componente" e adicione o script de comentários de âncora procurá-lo e selecioná-la depois que ela for exibida. 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Arraste o objeto de texto "feedbackPanel" da hierarquia de ASA_Feedback no slot vazio abaixo o script conforme mostrado na figura abaixo. 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a>Parabéns

Nesta lição, aprendemos como criar um painel de interface do usuário para exibir o status atual da experiência de âncora espacial do Azure para fornecer o usuário com comentários em tempo real.



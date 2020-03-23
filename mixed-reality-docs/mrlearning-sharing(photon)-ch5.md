---
title: Tutoriais de recursos multiusuário – 5. Integrar Âncoras Espaciais do Azure a uma experiência compartilhada
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031682"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integrar Âncoras Espaciais do Azure a uma experiência compartilhada

Nesta lição, você aprenderá a integrar ASA (Âncoras Espaciais do Azure) à nossa experiência compartilhada. O ASA permitirá que vários dispositivos colocalizados tenham uma referência comum se o seu ambiente físico precisar ancorar experiências virtuais de maneira que todos os participantes vejam objetos no mesmo local físico.

## <a name="objectives"></a>Objetivos

* Integre o ASA a uma experiência compartilhada para o alinhamento de vários dispositivos.
* Conheça os conceitos básicos de como o ASA funciona no contexto de uma experiência compartilhada local.

## <a name="instructions"></a>Instruções

1. Selecione o pré-fabricado TableAnchor abaixo do objeto pai MixedRealityPlayspace e exclua-a.

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. Na exibição de projeto, acesse Ativos->Recursos->Pré-Fabricados e arraste o pré-fabricado TableAnchor para cima do objeto SharedPlayground para torná-lo um filho.

3. Expanda o objeto pai MixedRealityPlayspace, o objeto TableAnchor e expanda o objeto Botões também.

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Agora, na hierarquia, selecione ShareAzureAnchorButton e concentre-se no painel Inspetor. Role para baixo até o menu suspenso mostrado na imagem abaixo, selecione AnchorModuleScript e clique em ShareAnchorNetwork().

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Selecione GetAzureAnchorButton (consulte a Etapa 4) e concentre sua atenção de volta no painel Inspetor. Role para baixo até o menu suspenso exibido na imagem abaixo, selecione AnchorModuleScript, clique em GetSharedAnchorNetwork() e salve.

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Repita a etapa 4 para conectar a função StartAzureSession() ao StartAzureSessionButton.

7. Repita a etapa 4 para conectar a função CreateAzureAnchor () ao CreateAzureAnchorButton e verificar se o objeto TableAnchor está atribuído ao campo "Objeto do Jogo" do parâmetro da função.

8. Siga as instruções em [Conectar a cena ao recurso do Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) para adicionar suas credenciais de serviço de Âncoras Espaciais do Azure.

9. Para testar o módulo de compartilhamento, clique no botão "Iniciar Sessão do ASA do Azure", que iniciará a sessão de âncoras espaciais do Azure e, em seguida, criará a âncora do Azure clicando no botão "Criar Âncora do Azure". Aguarde até a âncora do Azure ser criada. Depois que a âncora do Azure for criada, clique no botão "Compartilhar Âncora do Azure" para compartilhar a âncora do Azure criada do HoloLens.

10. Para receber a Âncora do Azure compartilhada em outro HoloLens, clique em "Iniciar a Sessão do ASA do Azure" para iniciar e entrar na sessão do ASA atual

11. Clique no botão "Obter Âncora do Azure" para obter a âncora do Azure compartilhada do outro HoloLens.

## <a name="congratulations"></a>Parabéns

Nesta lição, você aprendeu a integrar as novas Âncoras Espaciais do Azure eficientes para alinhar dispositivos colocalizados em uma experiência compartilhada! Isso também conclui o módulo de compartilhamento. Aprendemos a configurar uma nova conta do Photon, integrar o Photon e o PUN a um novo aplicativo Unity, configurar avatars e objetos compartilhados e, por fim, alinhar vários participantes usando o ASA.

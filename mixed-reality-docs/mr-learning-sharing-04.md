---
title: Tutoriais de recursos multiusuário – 4. Compartilhar movimentações de objeto com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cd8f0cb8888e7225566acc8c4b26aced3e4d977e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304008"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Compartilhar movimentações de objeto com vários usuários

Neste tutorial, você aprenderá a compartilhar os movimentos de objetos, de modo que todos os participantes de uma experiência compartilhada possam colaborar e exibir as interações uns dos outros.

## <a name="objectives"></a>Objetivos

* Configurar o projeto para compartilhar os movimentos de objetos
* Saber como criar um aplicativo básico de colaboração de vários usuários

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você vai preparar a cena adicionando o pré-fabricado do tutorial.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e arraste o pré-fabricado **TableAnchor** sobre o objeto **SharedPlayground** na janela Hierarquia para adicioná-lo à cena como um filho do objeto SharedPlayground:

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Como configurar o PUN para criar uma instância dos objetos

Nesta seção, você vai configurar o projeto para usar a experiência do Explorador do Rover criada durante os [Tutoriais de introdução](mr-learning-base-01.md) e definir onde ele será instanciado.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:

* Para o campo **Pré-fabricado do Rover Explorer**, atribua o pré-fabricado **RoverExplorer_Complete_Variant** da pasta Recursos

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Com o objeto filho **NetworkRoom** ainda selecionado, na janela Hierarquia, expanda o objeto **TableAnchor** e, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:

* No campo **Localização do Explorador do Rover**, atribua o objeto filho TableAnchor > **Table** por meio da janela Hierarquia

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Como testar a experiência com a movimentação de objetos compartilhados

Se você criar e implantar agora o projeto do Unity no HoloLens e, no Unity, selecionar o botão Reproduzir para entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá o objeto se mover no Unity ao mover o objeto no HoloLens:

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Parabéns

Você configurou com êxito o projeto para sincronizar os movimentos do objeto para que os usuários possam ver os objetos se moverem quando os outros usuários os moverem. No próximo tutorial, você implementará a funcionalidade para alinhar a experiência no mundo físico. Isso garantirá que os usuários vejam uns aos outros na sua localização física real e, portanto, os objetos aparecerão na mesma posição física e rotação para todos os usuários.

[Próximo tutorial: 5. Integrar âncoras espaciais do Azure a uma experiência compartilhada](mr-learning-sharing-05.md)

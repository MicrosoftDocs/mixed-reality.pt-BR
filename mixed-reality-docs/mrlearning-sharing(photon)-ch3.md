---
title: Tutoriais de recursos multiusuário – 4. Compartilhar movimentações de objeto com vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610658"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a>3. Compartilhar movimentações de objeto com vários usuários

Neste tutorial, você aprenderá a compartilhar os movimentos de objetos, de modo que todos os participantes de uma experiência compartilhada possam colaborar e ver as interações uns dos outros.

## <a name="objectives"></a>Objetivos

* Configurar o projeto para compartilhar os movimentos de objetos
* Saiba como criar um aplicativo básico de colaboração de vários usuários

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você vai preparar a cena adicionando o pré-fabricado do tutorial.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e arraste o pré-fabricado **TableAnchor** sobre o objeto **SharedPlayground** na janela Hierarquia para adicioná-lo à cena como um filho do objeto SharedPlayground:

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Como configurar o PUN para criar uma instância dos objetos

Nesta seção, você vai configurar o projeto para usar o pré-fabricado RocketLauncher_Complete_Variant criado na seção anterior e definir em que local a instância dele será criada.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:

* Ao campo **Pré-fabricado do Usuário do Photon**, atribua o pré-fabricado **PhotonUser** da pasta Recursos

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

Com o objeto filho **NetworkRoom** ainda selecionado, na janela Hierarquia, expanda o objeto **TableAnchor** e, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:

* Ao campo **Localização do Rocket Launcher**, atribua o objeto filho **Table** por meio da janela Hierarquia

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Como testar a experiência com a movimentação de objetos compartilhados

Se você criar e implantar agora o projeto do Unity no HoloLens e, no Unity, selecionar o botão Reproduzir para entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá o objeto se mover no Unity ao mover o objeto no HoloLens:

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a>Parabéns

Você configurou com êxito o projeto, para que os movimentos de objeto sejam sincronizados e os usuários possam ver os objetos se moverem quando os outros usuários moverem os objetos. No próximo tutorial, você implementará uma funcionalidade para que a experiência compartilhada seja alinhada no mundo físico e os usuários vejam uns aos outros na respectiva localização física real e para que os objetos apareçam na mesma posição física e rotação para todos os usuários.

[Próximo tutorial: 4. Integrar âncoras espaciais do Azure a uma experiência compartilhada](mrlearning-sharing(photon)-ch4.md)

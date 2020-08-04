---
title: Tutoriais de recursos multiusuário – 3. Como conectar vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376388"
---
# <a name="3-connecting-multiple-users"></a>3. Como conectar vários usuários

Neste tutorial, você aprenderá a conectar vários usuários como parte de uma experiência compartilhada ao vivo. Ao final do tutorial, você estará apto a executar o aplicativo em vários dispositivos e fazer com que cada usuário veja o avatar dos outros usuários se mover em tempo real.

## <a name="objectives"></a>Objetivos

* Saiba como conectar vários usuários em uma experiência compartilhada

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:

* Pré-fabricado **NetworkLobby**
* Pré-fabricado **SharedPlayground**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureSpatialAnchors** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:

* **DebugWindow** pré-fabricado

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>Como criar o pré-fabricado do usuário

Nesta seção, você criará um pré-fabricado que será usado para representar os usuários na experiência compartilhada.

### <a name="1-create-and-configure-the-user"></a>1. Criar e configurar o usuário

Na janela Hierarquia, clique com o botão direito do mouse em uma área vazia e selecione **Criar Vazio** para adicionar um objeto vazio à cena, nomeie o objeto **PhotonUser** e configure-o da seguinte maneira:

* Verifique se a **Posição** da transformação está definida como X = 0, Y = 0 e Z = 0:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

Na janela Hierarquia, selecione o objeto **PhotonUser**, então, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Usuário do Photon (Script)** ao objeto PhotonUser:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

Na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Sincronização de Rede Genérica (Script)** ao objeto PhotonUser e configure-o da seguinte maneira:

* Marque a caixa de seleção **É um Usuário**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

Na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Exibição do Photon (Script)** ao objeto PhotonUser e configure-o da seguinte maneira:

* Ao campo **Componentes Observados**, atribua o componente **Sincronização de Rede Genérica (Script)**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. Criar o avatar

Na janela do projeto, navegue até a pasta **Ativos** > **MRTK** > **SDK** > **StandardAssets** > **Materiais** para localizar os materiais do MRTK.

Em seguida, na janela Hierarquia, clique com o botão direito do mouse no objeto **PhotonUser** e selecione **Objeto 3D** > **Esfera** para criar um objeto de esfera como um filho do objeto PhotonUser e configure-o da seguinte maneira:

* Verifique se a **Posição** da transformação está definida como X = 0, Y = 0 e Z = 0
* Altere a **Escala** da transformação para um tamanho adequado, por exemplo, X = 0,15, Y = 0,15 e Z = 0,15
* Para o campo MeshRenderer > Materiais > **Elemento 0**, atribua o material **MRTK_Standard_White**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. Criar o pré-fabricado

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

Com a pasta Recursos ainda selecionada, **clique e arraste** o objeto **PhotonUser** da janela Hierarquia para a pasta **Recursos** a fim de tornar o objeto PhotonUser um pré-fabricado:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

Na janela Hierarquia, clique com o botão direito do mouse no objeto **PhotonUser** e selecione **Excluir** para removê-lo da cena:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Como configurar o PUN para criar uma instância do pré-fabricado do usuário

Nesta seção, você vai configurar o projeto para usar o pré-fabricado do PhotonUser criado na seção anterior.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:

* Ao campo **Pré-fabricado do Usuário do Photon**, atribua o pré-fabricado **PhotonUser** da pasta Recursos

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Como testar a experiência com vários usuários

Se você criar e implantar agora o projeto do Unity no HoloLens, então, no Unity, entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá a movimentação do avatar do usuário do HoloLens quando mover a cabeça (HoloLens):

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> O aplicativo precisa se conectar ao Photon; portanto, verifique se o computador/o dispositivo está conectado à Internet.

## <a name="congratulations"></a>Parabéns

Você configurou com êxito seu projeto para permitir que vários usuários se conectem à mesma experiência e vejam os movimentos uns dos outros. No próximo tutorial, você implementará uma funcionalidade para que os movimentos dos objetos também sejam compartilhados entre vários dispositivos.

[Próximo tutorial: 4. Compartilhar movimentações de objeto com vários usuários](mr-learning-sharing-04.md)

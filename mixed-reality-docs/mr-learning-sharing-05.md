---
title: Tutoriais de recursos multiusuário – 5. Integrar Âncoras Espaciais do Azure a uma experiência compartilhada
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: fc8e20a9ddaa595db0a3d59975e7c785d01c0a6d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376578"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integrar Âncoras Espaciais do Azure a uma experiência compartilhada

Neste tutorial, você aprenderá a integrar a ASA (Âncoras Espaciais do Azure) à experiência compartilhada. A ASA permite que vários dispositivos tenham uma referência comum ao mundo físico, de modo que os usuários vejam uns aos outros na respectiva localização física real e vejam a experiência compartilhada no mesmo lugar.

## <a name="objectives"></a>Objetivos

* Integrar a ASA a uma experiência compartilhada para o alinhamento de vários dispositivos
* Conhecer os conceitos básicos de como a ASA funciona no contexto de uma experiência compartilhada local

## <a name="preparing-the-scene"></a>Preparando a cena

Na janela Hierarquia, expanda o objeto **SharedPlayground** e expanda o objeto **TableAnchor** para expor os objetos filho:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e arraste o pré-fabricado **Buttons** sobre o objeto filho **TableAnchor** para adicioná-lo à cena como um filho do objeto TableAnchor:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Como configurar os botões para operar a cena

Nesta seção, você vai configurar uma série de eventos de botão que demonstram os conceitos básicos de como as Âncoras Espaciais do Azure podem ser usadas para obter o alinhamento espacial em uma experiência compartilhada.

Na janela Hierarquia, expanda o objeto **Button** e selecione o primeiro objeto de botão filho chamado **StartAzureSession**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

Na janela Inspetor, localize o componente **Interativo (Script)** e configure o evento **OnClick ()** da seguinte maneira:

* Ao campo **Nenhum (Objeto)** , atribua o objeto **TableAnchor**
* No menu suspenso **Nenhuma Função**, selecione a função **AnchorModuleScript** > **StartAzureSession ()**

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

Na janela Hierarquia, selecione o segundo objeto de botão filho chamado **CreateAzureAnchor**. Em seguida, na janela Inspetor, localize o componente **Interativo (Script)** e configure o evento **OnClick ()** da seguinte maneira:

* Ao campo **Nenhum (Objeto)** , atribua o objeto **TableAnchor**
* No menu suspenso **Nenhuma Função**, selecione a função **AnchorModuleScript** > **CreateAzureAnchor ()**
* Ao novo campo **Nenhum (Objeto de Jogo)** exibido, atribua o objeto **TableAnchor**

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

Na janela Hierarquia, selecione o terceiro objeto de botão filho chamado **ShareAzureAnchor**. Em seguida, na janela Inspetor, localize o componente **Interativo (Script)** e configure o evento **OnClick ()** da seguinte maneira:

* Ao campo **Nenhum (Objeto)** , atribua o objeto **TableAnchor**
* No menu suspenso **Nenhuma Função**, selecione a função **SharingModuleScript** > **ShareAzureAnchor ()**

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

Na janela Hierarquia, selecione o quarto objeto de botão filho chamado **GetAzureAnchor**. Em seguida, na janela Inspetor, localize o componente **Interativo (Script)** e configure o evento **OnClick ()** da seguinte maneira:

* Ao campo **Nenhum (Objeto)** , atribua o objeto **TableAnchor**
* No menu suspenso **Nenhuma Função**, selecione a função **SharingModuleScript** > **GetAzureAnchor ()**

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Como conectar a cena ao recurso do Azure

Na janela Hierarquia, expanda o objeto **SharedPlayground** e selecione o objeto **TableAnchor**.

Na janela Inspetor, localize o componente **Gerenciador de Âncora Espacial (Script)** e configure a seção **Credenciais** com as credenciais da conta das Âncoras Espaciais do Azure criada como parte dos [Pré-requisitos](mr-learning-sharing-01.md#prerequisites) desta série de tutoriais:

* No campo **ID da Conta das Âncoras Espaciais**, cole a **ID da Conta** da sua conta das Âncoras Espaciais do Azure
* No campo **Chave de Conta das Âncoras Espaciais**, cole a **Chave de Acesso** primária ou secundária da sua conta das Âncoras Espaciais do Azure

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> Em vez de definir a ID da Conta de Âncoras Espaciais e a chave na cena, você pode defini-la para todo o seu projeto, isso poderá ser vantajoso se você tiver várias cenas usando o ASA. Para fazer isso, na janela do projeto, navegue até o ativo em Ativos > AzureSpatialAnchors.SDK > Recursos > **SpatialAnchorConfig** e defina os valores na janela Inspetor.

Na janela Hierarquia, selecione o objeto **TableAnchor** e, em seguida, na janela Inspetor, localize o componente **Módulo de Âncora (Script)** e configure-o da seguinte maneira:

* No campo **PIN de Compartilhamento Público**, altere alguns dígitos para que o PIN se torne exclusivo ao seu projeto

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

Com o objeto **TableAnchor** ainda selecionado, na janela Inspetor, verifique se todos os componentes de script estão **habilitados**:

* Marque a caixa de seleção ao lado dos componentes **Gerenciador de Âncora Espacial (Script)** para habilitá-los
* Marque a caixa de seleção ao lado dos componentes **Script do Módulo de Âncora (Script)** para habilitá-los
* Marque a caixa de seleção ao lado dos componentes **Script do Módulo de Compartilhamento (Script)** para habilitá-los

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>Como testar a experiência com o alinhamento espacial

> [!NOTE]
> As Âncoras Espaciais do Azure não podem ser executadas no Unity. Consequentemente, para testar a funcionalidade das Âncoras Espaciais do Azure, você precisará implantar o projeto em um mínimo de dois dispositivos.

Se você criar e implantar agora o projeto do Unity em dois dispositivos, poderá obter o alinhamento espacial entre os dispositivos compartilhando a ID da Âncora do Azure. Para testá-lo, você pode seguir estas etapas:

1. No dispositivo 1: **Iniciar o aplicativo** (o Gerenciador de Rover é instanciado e colocado na tabela)
2. No dispositivo 2: **Inicie o aplicativo** (os dois usuários veem a mesa com o Rover Explorer, mas ela não aparece no mesmo lugar, e os avatars do usuário não aparecem no local em que os usuários estão)
3. No dispositivo 1: Selecione o botão **Iniciar Sessão do Azure**
4. No dispositivo 1: Selecione o botão **Criar Âncora do Azure** (cria a âncora na localização do objeto TableAnchor e armazena as informações de âncora no recurso do Azure).
5. No dispositivo 1: Selecione o botão **Compartilhar Âncora do Azure** (compartilha a ID da âncora com os outros usuários em tempo real)
6. No dispositivo 2: Selecione o botão **Iniciar Sessão do Azure**
7. No dispositivo 2: Selecione o botão **Obter Âncora do Azure** (conecta-se ao recurso do Azure para recuperar as informações de âncora da ID da âncora compartilhada e, em seguida, move o objeto TableAnchor para a localização em que a âncora foi criada com o dispositivo 1)

> [!TIP]
> Se você não tiver acesso a dois dispositivos HoloLens, poderá seguir [Como criar Âncoras Espaciais do Azure para dispositivos móveis](mr-learning-asa-05.md) para implantar o projeto em seu dispositivo móvel.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a integrar as Âncoras Espaciais do Azure avançadas para alinhar dispositivos em uma experiência compartilhada.

Isso também conclui esta série de tutoriais em que você aprendeu a configurar uma conta do Photon, criar um aplicativo PUN, integrar o PUN ao projeto do Unity, configurar os avatars e objetos compartilhados do usuário e, por fim, alinhar vários participantes usando as Âncoras Espaciais do Azure.

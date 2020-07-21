---
title: Tutoriais de Âncoras Espaciais do Azure – 2. Introdução às Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a24b6b03ce75a57db49b3d0c875d123ea87c8162
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303966"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Introdução às Âncoras Espaciais do Azure

## <a name="overview"></a>Visão geral

Neste tutorial, você vai explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure e criar, carregar e baixá-las em apenas um dispositivo.

## <a name="objectives"></a>Objetivos

* Conheça os conceitos básicos do desenvolvimento com Âncoras Espaciais do Azure para o HoloLens 2
* Saber como criar âncoras espaciais e buscá-las no Azure

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Como inicializar o seu projeto e implantar o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar o seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*
1. [Como alternar a plataforma de build](mr-learning-base-02.md#configuring-the-unity-project)
1. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [Como configurar o projeto do Unity](mr-learning-base-02.md#configuring-the-unity-project)
1. [Criar e configurar a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar um nome adequado à cena, por exemplo, *AzureSpatialAnchors*

Em seguida, siga as instruções em [Alterar a opção de exibição de reconhecimento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:

1. Alterar o **perfil de configuração do MRTK** para **DefaultHoloLens2ConfigurationProfile**
1. Alterar as **opções de exibição da malha de reconhecimento espacial** para **Oclusão**.

## <a name="installing-inbuilt-unity-packages"></a>Instalar pacotes internos do Unity

No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes** para abrir a janela Gerenciador de Pacotes e selecione **AR Foundation** e clique no botão **Instalar** para instalar o pacote:

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure e será importado na próxima seção.

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versão 2.2.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções em [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureSpatialAnchors** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:

* Pré-fabricados **ButtonParent**
* Pré-fabricados **DebugWindow**
* Pré-fabricados **Instructions**
* Pré-fabricados **ParentAnchor**

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Se você considerar que ícones grandes na sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Utensílio</a> para a posição de desligado, conforme mostrado na imagem acima.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Como configurar os botões para operar a cena

Nesta seção, você adicionará scripts à cena para criar uma série de eventos de botão que demonstram os conceitos básicos de como as âncoras locais e as Âncoras Espaciais do Azure se comportam em um aplicativo.

Na janela Hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **StartAzureSession ()** para definir essa função como a ação a ser executada quando o evento for disparado

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

Na janela Hierarquia, selecione o próximo botão denominado **StopAzureSession**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **StopAzureSession ()** para definir essa função como a ação a ser executada quando o evento for disparado

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

Na janela Hierarquia, selecione o próximo botão denominado **CreateAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **CreateAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado
* Atribua o objeto **ParentAnchor** ao campo vazio **Nenhum (Objeto de Jogo)** para torná-lo o argumento para a função CreateAzureAnchor ()

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

Na janela Hierarquia, selecione o próximo botão denominado **RemoveLocalAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **RemoveLocalAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado
* Atribua o objeto **ParentAnchor** ao campo vazio **Nenhum (Objeto de Jogo)** para torná-lo o argumento para a função RemoveLocalAnchor ()

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

Na janela Hierarquia, selecione o próximo botão denominado **FindAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **FindAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

Na janela Hierarquia, selecione o próximo botão denominado **DeleteAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **DeleteAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Como conectar a cena ao recurso do Azure

Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, localize o componente **Gerenciador de Âncora Espacial (Script)** . Configure a seção **Credenciais** com as credenciais da conta das Âncoras Espaciais do Azure criada como parte dos [Pré-requisitos](mr-learning-asa-01.md#prerequisites) desta série de tutoriais:

* No campo **ID da Conta das Âncoras Espaciais**, cole a **ID da Conta** da sua conta das Âncoras Espaciais do Azure
* No campo **Chave de Conta das Âncoras Espaciais**, cole a **Chave de Acesso** primária ou secundária da sua conta das Âncoras Espaciais do Azure

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Experimentando os comportamentos básicos das Âncoras Espaciais do Azure

As Âncoras Espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade delas, você precisa criar o projeto e implantar o aplicativo no seu dispositivo.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Quando o aplicativo for executado no seu dispositivo, siga as instruções na tela exibidas no painel Instruções do Tutorial de Âncora Espacial do Azure:

1. Mover o cubo para uma localização diferente
1. Iniciar a Sessão do Azure
1. Criar Âncora do Azure (cria uma âncora na localização do cubo).
1. Interromper a Sessão do Azure
1. Remover a Âncora Local (permite que o usuário mova o cubo)
1. Mover o cubo para outro lugar
1. Iniciar a Sessão do Azure
1. Localizar a Âncora do Azure (posiciona o cubo na localização da etapa 3)
1. Excluir a Âncora do Azure
1. Interromper a sessão do Azure

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> As Âncoras Espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.

## <a name="anchoring-an-experience"></a>Como ancorar uma experiência

Nas seções anteriores, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure. Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada. Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.

Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:

* Altere a **Escala X** para 1,1
* Altere a **Escala Z** para 1,1

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados** > **Rover** e, em seguida, clique e arraste o pré-fabricado **RoverExplorer_Complete** na janela Hierarquia para adicioná-lo à cena:

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

Com o objeto RocketLauncher_Complete recém-adicionado ainda selecionado na janela Hierarquia, arraste-o sobre o objeto **ParentAnchor** para torná-lo um filho do objeto ParentAnchor:

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

Se agora você recompilar o projeto e implantar o aplicativo no seu dispositivo, você poderá reposicionar toda a experiência do Explorador do Rover movendo o cubo redimensionado.

> [!TIP]
> Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de utensílios de posição e rotação e muito mais.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure. Este tutorial forneceu vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure. Além disso, para criar, carregar e baixar Âncoras Espaciais do Azure em um único dispositivo.

No próximo tutorial, você aprenderá a salvar as IDs de âncora do Azure no seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado, bem como a transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.

[Próximo tutorial: 3. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure](mr-learning-asa-03.md)

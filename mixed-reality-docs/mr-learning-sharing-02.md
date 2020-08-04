---
title: Tutoriais de recursos multiusuário – 2. Configurar o Photon Unity Networking
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ed55d1f84db7ee8dc33f0f738de2b6b98a305fd3
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376398"
---
# <a name="2-setting-up-photon-unity-networking"></a>2. Configurar o Photon Unity Networking

## <a name="overview"></a>Visão geral

Neste tutorial, você vai se preparar para criar uma experiência compartilhada usando o PUN (Photon Unity Networking). Você aprenderá a criar um aplicativo PUN, importar ativos PUN para seu projeto do Unity e conectar seu projeto do Unity ao aplicativo PUN.

## <a name="objectives"></a>Objetivos

* Saiba como criar um aplicativo PUN
* Saber como encontrar e importar os ativos PUN
* Saiba como conectar seu projeto do Unity ao aplicativo PUN

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Como inicializar o seu projeto e implantar o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar o seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*
1. [Como alternar a plataforma de build](mr-learning-base-02.md#configuring-the-unity-project)
1. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [Como configurar o projeto do Unity](mr-learning-base-02.md#configuring-the-unity-project)
1. [Criar e configurar a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar um nome adequado à cena, por exemplo, *MultiUserCapabilities*

Em seguida, siga as instruções em [Alterar a opção de exibição de reconhecimento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:

1. Alterar o **perfil de configuração do MRTK** para **DefaultHoloLens2ConfigurationProfile**
1. Alterar as **opções de exibição da malha de reconhecimento espacial** para **Oclusão**.

## <a name="enabling-additional-capabilities"></a>Como habilitar funcionalidades adicionais

No menu do Unity, selecione **Editar** > **Configurações de projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Configurações de Publicação**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

Em **Configurações de publicação**, role para baixo até a seção **Funcionalidades** e verifique novamente se as funcionalidades **InternetClient**, **Microfone**, **SpatialPerception** e **GazeInput**, que você habilitou durante a etapa [Como configurar o projeto Unity](mr-learning-base-02.md#configuring-the-unity-project) acima estão habilitadas.

Em seguida, habilite as seguintes funcionalidades adicionais:

* Funcionalidade **InternetClientServer**
* Funcionalidade **PrivateNetworkClientServer**

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a>Instalar pacotes internos do Unity

No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes** para abrir a janela Gerenciador de Pacotes e selecione **AR Foundation** e clique no botão **Instalar** para instalar o pacote:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure que você importará na próxima seção.

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versão 2.2.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções em [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

> [!NOTE]
> Depois de importar o pacote de ativos do tutorial de MultiUserCapabilities, você verá vários erros [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) na janela do console informando que o tipo ou o namespace está ausente. Isso deve ser esperado e será resolvido na próxima seção quando você importar os ativos PUN.

## <a name="importing-the-pun-assets"></a>Como importar os ativos PUN

No menu do Unity, selecione **Janela** > **Asset Store** para abrir a janela da Asset Store, pesquise e selecione **PUN 2 – GRATUITO** em Sair dos Jogos e clique no botão **Baixar** para baixar o pacote de ativos para a sua conta do Unity.

Quando o download for concluído, clique no botão **Importar** para abrir a janela Importar Pacote do Unity:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

Depois que o Unity concluir o processo de importação, a janela do Assistente do PUN será exibida com o menu Instalação do PUN carregado; ignore ou feche essa janela por enquanto:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>Como criar o aplicativo PUN

Nesta seção, você criará uma conta do Photon, se ainda não tiver uma, e criará um aplicativo PUN.

Navegue até o <a href="https://dashboard.photonengine.com/account/signin" target="_blank">painel</a> do Photon e entre nele caso já tenha uma conta que deseja usar; caso contrário, clique no link **Criar Uma** e siga as instruções para registrar uma nova conta:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

Depois que estiver conectado, clique no botão **Criar um Aplicativo**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

Na página Criar um Aplicativo, insira os seguintes valores:

* Para o tipo Photon, selecione PUN
* Em Nome, insira um nome adequado, por exemplo, _Tutoriais do MRTK_
* Em Descrição, opcionalmente, insira uma descrição adequada
* Em URL, deixe o campo vazio

Em seguida, clique no botão **Criar** para criar o aplicativo:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

Depois que o Photon tiver concluído o processo de criação, o novo aplicativo PUN será exibido no painel:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Como conectar o projeto do Unity ao aplicativo PUN

Nesta seção, você conectará seu projeto do Unity ao aplicativo PUN criado na seção anterior.

No painel do Photon, clique no campo **ID do Aplicativo** para revelar a ID do aplicativo e, em seguida, copie-o para a área de transferência:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

No menu do Unity, selecione **Janela** > **Photon Unity Networking** > **Assistente do PUN** para abrir a janela do Assistente do PUN, clique no botão **Projeto de Instalação** para abrir o menu Instalação do PUN e configure-o da seguinte maneira:

* No campo **ID do Aplicativo ou Email**, cole a ID do aplicativo PUN copiado na etapa anterior

Em seguida, clique no botão **Projeto de Instalação** para aplicar a ID do aplicativo:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

Depois que o Unity concluir o processo de configuração do PUN, o menu Instalação do PUN exibirá a mensagem **Concluído!** e selecionará automaticamente o ativo **PhotonServerSettings** na janela Projeto, de modo que as propriedades sejam exibidas na janela Inspetor:

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>Parabéns

Você criou um aplicativo PUN com êxito e o conectou ao seu projeto do Unity. A próxima etapa será permitir conexões com outros usuários para que vários usuários possam ver uns aos outros.

[Próximo tutorial: 3. Conectar vários usuários](mr-learning-sharing-03.md)

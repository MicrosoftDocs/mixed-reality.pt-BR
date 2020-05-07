---
title: Tutoriais de recursos multiusuário – 1. Configurar o Photon Unity Networking
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610768"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Configurar o Photon Unity Networking

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a se preparar para criar uma experiência compartilhada usando o PUN (Photon Unity Networking). O Photon é uma das várias opções de rede disponíveis para os desenvolvedores de realidade misturada criarem experiências compartilhadas. Você aprenderá a criar um aplicativo Photon PUN, importar ativos do Photon PUN para o seu projeto do Unity e conectá-lo ao aplicativo Photon PUN.

## <a name="objectives"></a>Objetivos

* Aprender a criar um aplicativo Photon PUN
* Aprender a encontrar e importar os ativos do Photon PUN
* Aprender a conectar seu projeto do Unity ao aplicativo Photon PUN

## <a name="prerequisites"></a>Pré-requisitos

>[!TIP]
>Se você ainda não concluiu os [Tutoriais de introdução](mrlearning-base.md) e a série de [Tutoriais das Âncoras Espaciais do Azure](mrlearning-asa-ch1.md), recomendamos que você conclua esses tutoriais primeiro.

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado
* Conclua a seção [Criar um recurso de Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Guia de início rápido: Criar um aplicativo HoloLens do Unity que usa as Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)

> [!IMPORTANT]
> A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mrlearning-base-ch1.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mrlearning-base-ch1.md#create-new-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*

2. [Configurar o projeto do Unity para o Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importar recursos do TextMesh Pro Essential](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configurar o projeto do Unity para o Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Adicionar o Kit de Ferramentas de Realidade Misturada à cena do Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e dar um nome adequado à cena, por exemplo, *MultiUserCapabilities*

Então siga as instruções de [Como configurar os perfis do Mixed Reality Toolkit (Opção de Alterar Exibição de Reconhecimento Espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição para a malha de reconhecimento espacial para **Oclusão**.

> [!CAUTION]
> Conforme mencionado nas instruções de [Como configurar o projeto do Unity para o Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) vinculadas acima, é altamente recomendável não habilitar o MSBuild para o Unity.

## <a name="configuring-the-capabilities"></a>Como configurar as funcionalidades

No menu do Unity, selecione **Editar** > **Configurações de projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Configurações de Publicação**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

Em **Configurações de Publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas. Em seguida, habilite as funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** e **RemovableStorage**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a>Como adicionar pacotes internos do Unity
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

Nesta seção, você instalará o pacote interno da AR Foundation do Unity porque ele é exigido pelo SDK de Âncoras Espaciais do Azure que será importado na próxima seção.

No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> Pode levar alguns segundos até que o pacote de AR Foundation seja exibido na lista.

Na janela Gerenciador de Pacotes, selecione **AR Foundation** e instale o pacote clicando no botão **Instalar**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versão 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> Depois de importar o pacote de ativos do tutorial de MultiUserCapabilities, você verá vários erros [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) na janela do console informando que o tipo ou o namespace está ausente. Isso deve ser esperado e será resolvido na próxima seção quando você importar os ativos do Photon.

## <a name="importing-the-photon-assets"></a>Como importar os ativos do Photon

Nesta seção, você importará os ativos do PUN (Photon Unity Network) na Asset Store do Unity.

No menu do Unity, selecione **Janela** > **Asset Store** para abrir a janela da Asset Store, procure e selecione **PUN 2 – GRATUITO** em Sair dos Jogos e clique no botão **Baixar** para baixar o pacote de ativos para a sua conta do Unity:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

Quando o download for concluído, clique no botão **Importar** para abrir a janela Importar Pacote do Unity:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

Depois que o Unity concluir o processo de importação, a janela do Assistente do PUN será exibida com o menu Instalação do PUN carregado; ignore ou feche essa janela por enquanto:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a>Como configurar o Photon

Nesta seção, você criará uma conta do Photon, se ainda não tiver uma, e criará um aplicativo PUN.

Navegue até o <a href="https://dashboard.photonengine.com/account/signin" target="_blank">painel</a> do Photon e entre nele caso já tenha uma conta que deseja usar; caso contrário, clique no link **Criar Uma** e siga as instruções para registrar uma nova conta:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

Depois que estiver conectado, clique no botão **Criar um Aplicativo**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

Na página Criar um Aplicativo, insira os seguintes valores:

* Em Tipo do Photon, selecione Photon PUN
* Em Nome, insira um nome adequado, por exemplo, _Tutoriais do MRTK_
* Em Descrição, opcionalmente, insira uma descrição adequada
* Em URL, deixe o campo vazio

Em seguida, clique no botão **Criar** para criar o aplicativo:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

Depois que o Photon tiver concluído o processo de criação, o novo aplicativo PUN será exibido no painel:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Como conectar o projeto do Unity ao aplicativo PUN

Nesta seção, você conectará seu projeto do Unity ao aplicativo PUN criado na seção anterior.

No painel do Photon, clique no campo **ID do Aplicativo** para revelar a ID do aplicativo e, em seguida, copie-o para a área de transferência:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

No menu do Unity, selecione **Janela** > **Photon Unity Networking** > **Assistente do PUN** para abrir a janela do Assistente do PUN, clique no botão **Projeto de Instalação** para abrir o menu Instalação do PUN e configure-o da seguinte maneira:

* No campo **ID do Aplicativo ou Email**, cole a ID do aplicativo PUN copiado na etapa anterior

Em seguida, clique no botão **Projeto de Instalação** para aplicar a ID do aplicativo:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

Depois que o Unity concluir o processo de configuração do PUN, o menu Instalação do PUN exibirá a mensagem **Concluído!** e selecionará automaticamente o ativo **PhotonServerSettings** na janela Projeto, de modo que as propriedades sejam exibidas na janela Inspetor:

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a>Parabéns

Você criou um aplicativo Photon PUN com êxito e o conectou ao seu projeto do Unity. A próxima etapa será permitir conexões com outros usuários para que vários usuários possam ver uns aos outros.

[Próximo tutorial: 2. Conectar vários usuários](mrlearning-sharing(photon)-ch2.md)

---
title: Tutoriais de recursos multiusuário – 1. Configurar o Photon Unity Networking
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031337"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Configurar o Photon Unity Networking

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a se preparar para criar uma experiência compartilhada importando o PUN (Photon Unity Networking) para seu projeto do Unity. O Photon é uma das várias opções de rede disponíveis para os desenvolvedores de realidade misturada criarem experiências compartilhadas. Você aprenderá a criar uma conta do Photon, a importar o Photon e a criar um servidor local opcional

## <a name="objectives"></a>Objetivos

* Saiba como criar uma conta do Photon
* Saiba como localizar e importar o Photon Unity Networking
* Configurar um servidor local do Photon

## <a name="prerequisites"></a>Pré-requisitos

>[!TIP]
>Se você ainda não concluiu os [Tutoriais de introdução](mrlearning-base.md) e a série de [Tutoriais de introdução de Âncoras Espaciais do Azure](mrlearning-asa-ch1.md), recomendamos que você conclua esses tutoriais primeiro.

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)

>[!IMPORTANT]
> A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.

## <a name="setting-up-photon"></a>Como configurar o Photon

1. Configure uma conta do [Photon](https://dashboard.photonengine.com//Account/SignUp). Navegue até a página de Inscrição do Photon clicando [neste link](https://dashboard.photonengine.com//Account/SignUp). Siga as instruções na página de inscrição para criar a conta.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Crie uma ID de aplicativo clicando no botão Criar um Aplicativo.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Selecione o PUN do Photon no menu suspenso, em Tipo de Photon. Em seguida, dê um nome a ele. Neste exemplo, demos o nome HoloLensPhotonProject. Depois de terminar, clique no botão Criar.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Volte para a página de aplicativos e você verá algo semelhante à imagem abaixo. Clique na ID do aplicativo e copie-a. Cole-a em algum lugar que você possa acessar facilmente.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Crie um projeto do Unity e dê a ele o nome de HLSharingProject. Para obter instruções sobre como criar um projeto do Unity, confira a [seção "Criar projeto do Unity" do Módulo Base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Depois que o projeto for carregado, clique na guia Repositório de Ativos, conforme mostrado na imagem abaixo. Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite PUN e selecione o ativo Photon PUN 2 – FREE nos resultados da pesquisa.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Baixe e importe esse ativo pressionando os botões Baixar e Importar.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Depois que o Photon tiver concluído o processo de importação, o Assistente do PUN será exibido. Pegue a ID do aplicativo (que deve estar na área de transferência) da etapa 4, cole-a na caixa AppID e pressione o botão Configurar Projeto.

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Depois de adicionar com sucesso a AppID, navegue até Photon-> PhotonUnityNetworking->Recursos->PhotonServerSettings em Ativos. Selecione a opção Usar Servidor de Nomes e defina a região fixa como EUA ou sua região de serviço do Photon.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Parabéns

Você criou uma conta do Photon com êxito, configurou um servidor Photon local e importou o PUN para o Unity. A próxima etapa é configurar o projeto e permitir conexões com outros usuários para que vários usuários possam ver seu trabalho.

[Próximo tutorial: 2. Preparar o Unity para o desenvolvimento](mrlearning-sharing(photon)-ch2.md)

---
title: Tutoriais de funcionalidades de vários usuários-1. Configurando a rede do Photon Unity
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: d879144c7097d8b3873618f986b9f169e8553fa8
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553814"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Configurando a rede do Photon Unity

## <a name="overview"></a>Visão geral

Neste tutorial, você aprenderá a se preparar para criar uma experiência compartilhada importando o trocadilho (Photon Unity Networking) para seu projeto do Unity. O Photon é uma das várias opções de rede disponíveis para que os desenvolvedores de realidade mista criem experiências compartilhadas. Você aprenderá a criar uma conta do Photon, a importar Photon e a criar um servidor local opcional

## <a name="objectives"></a>Objetivos

* Saiba como criar uma conta do Photon
* Saiba como localizar e importar a rede Photon Unity
* Configurar um servidor Photon local

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

>[!TIP]
>Se você ainda não tiver concluído os tutoriais de [introdução](mrlearning-base.md) e os tutoriais de [âncoras espaciais iniciados do Azure](mrlearning-asa-ch1.md) , é recomendável que você conclua esses tutoriais primeiro.

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)

>[!IMPORTANT]
> A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.

## <a name="setting-up-photon"></a>Configurando o Photon

1. Configure uma conta do [Photon](https://dashboard.photonengine.com//Account/SignUp) . Navegue até a página de inscrição do Photon clicando neste [link](https://dashboard.photonengine.com//Account/SignUp). Siga as instruções na página de inscrição para criar a conta.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Crie uma ID de aplicativo clicando no botão criar um novo aplicativo.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Selecione Photon trocadilho no menu suspenso, em Photon Type. Em seguida, dê um nome a ele. Neste exemplo, nomeamos HoloLensPhotonProject. Quando terminar, clique no botão criar.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Volte para a página de aplicativos e você verá algo semelhante à imagem abaixo. Clique na ID do aplicativo e copie-a. Cole em algum lugar que você possa acessar facilmente.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Crie um novo projeto do Unity e nomeie-o HLSharingProject. Para obter instruções sobre como criar um novo projeto do Unity, consulte [a seção "criar projeto do Unity" do módulo base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Depois que o projeto for carregado, clique na guia repositório de ativos, conforme mostrado na imagem abaixo. Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite trocadilho e selecione o ativo Photon trocadilho 2-FREE "nos resultados da pesquisa.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Baixe e importe esse ativo pressionando os botões baixar e importar.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Depois que o Photon tiver concluído o processo de importação, o assistente de trocadilho será exibido. Pegue a ID do aplicativo (que deve estar na área de transferência) da etapa 4, Cole-a na caixa AppID e pressione o botão configurar projeto.

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Depois de adicionar o AppID com êxito, navegue até Photon-> PhotonUnityNetworking-> recursos-> PhotonServerSettings em ativos. Selecione a opção usar servidor de nomes e defina a região fixa como US ou sua região de serviço Photon.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Parabéns

Você criou uma conta do Photon com êxito, configurou um servidor Photon local e importou o trocadilho para o Unity. A próxima etapa é configurar o projeto e permitir conexões com outros usuários para que vários usuários possam ver seu trabalho.

[Próximo tutorial: 2. obtendo o Unity pronto para desenvolvimento](mrlearning-sharing(photon)-ch2.md)

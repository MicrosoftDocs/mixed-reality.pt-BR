---
title: Módulo de compartilhamento de aprendizagem do MR para o HoloLens 2
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: e40cd50f75ca509c601d215cb865161ea3596565
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293650"
---
#  <a name="setting-up-photon-unity-networking"></a>Configurando a rede do Photon Unity

Neste tutorial, aprenderemos como preparar-se para criar uma experiência compartilhada importando o trocadilho (Photon Unity Networking) para seu projeto do Unity. O Photon é uma das várias opções de rede disponíveis para que os desenvolvedores de realidade mista criem experiências compartilhadas. Nós aprenderemos como criar uma conta do Photon, importar Photon e criar um servidor local opcional

Seus

* Saiba como criar uma conta do Photon

* Saiba como localizar e importar a rede Photon Unity

* Configurar um servidor Photon local

  

### <a name="setting-up-photon"></a>Configurando o Photon

1. Configure uma conta do [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) . Navegue até a página de inscrição do Photon clicando neste [link](https://dashboard.photonengine.com/en-US/Account/SignUp). Siga as instruções na página de inscrição para criar a conta. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Crie uma ID de aplicativo clicando no botão criar um novo aplicativo.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Selecione Photon trocadilho no menu suspenso, em Photon Type. Em seguida, dê um nome a ele. Neste exemplo, nomeamos HoloLensPhotonProject. Quando terminar, clique no botão criar.

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Depois disso, volte para a página de aplicativos e você verá algo semelhante à imagem abaixo. Clique na ID do aplicativo e copie-a. Cole em algum lugar que você possa acessar facilmente.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Crie um novo projeto do Unity e nomeie-o HLSharingProject. Para obter instruções sobre como criar um novo projeto do Unity, consulte [a seção "criar projeto do Unity" do módulo base](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Depois que o projeto for carregado, clique na guia repositório de ativos, conforme mostrado na imagem abaixo. Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite trocadilho e selecione o ativo Photon trocadilho 2-FREE "nos resultados da pesquisa. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Baixe e importe esse ativo pressionando os botões baixar e importar.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Depois que o Photon tiver concluído o processo de importação, o assistente de trocadilho será exibido. Pegue a ID do aplicativo (que deve estar na área de transferência) da etapa 4 e cole-a na caixa AppID e pressione o botão configurar projeto. 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Depois de adicionar o AppID com êxito, navegue até Photon-> PhotonUnityNetworking-> recursos-> PhotonServerSettings em ativos. Selecione a opção usar servidor de nomes e defina a região fixa como US ou sua região de serviço Photon.

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Parabéns

Você criou uma conta do Photon com êxito, configurou um servidor Photon local e importou o trocadilho para o Unity. A próxima etapa é configurar o projeto e, em seguida, permitir conexões com outros usuários para que vários usuários possam ver seu trabalho. 

[Próximo tutorial: Preparar o Unity para o desenvolvimento](mrlearning-sharing(photon)-ch2.md)


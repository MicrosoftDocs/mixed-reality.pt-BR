---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416117"
---
# <a name="setting-up-photon"></a>Configurando Photon

Nesta lição, vamos aprenderá como se preparar para a criação de uma experiência de compartilhado com a importação de sistema de rede de Unity Photon (TROCADILHO) no projeto do Unity. Photon é uma das várias opções de rede disponíveis para desenvolvedores de realidade mista para criar experiências compartilhadas. Podemos, aprenderemos a criar uma conta de Photon, importar Photon e criar um servidor de local opcional

Objetivos:

* Saiba como criar conta Photon

* Saiba como localizar e importar Photon Unity de rede

* Configurar um servidor local do Photon

  

### <a name="setting-up-photon"></a>Configurando Photon

1. Configurar uma [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) conta. Navegue até a página de inscrição Photon clicando em [esse link](https://dashboard.photonengine.com/en-US/Account/SignUp). Siga as instruções na página de inscrição para criar a conta. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Crie uma ID de aplicativo clicando no botão "criar um novo aplicativo".

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Selecione "Photon TROCADILHO" no menu suspenso em "tipo de photon". Em seguida, dê a ele um nome, neste exemplo, podemos denominado "HoloLensPhotonProject". Quando terminar, clique no botão "Criar".

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Depois disso, retornar à página de seus aplicativos e você deverá ver algo semelhante à imagem abaixo. Clique na ID do aplicativo e copie-o. Colar é em algum lugar, que você pode acessar facilmente.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Crie um novo projeto do unity e nomeie-a como "HLSharingProject". Para obter instruções sobre como criar um novo projeto do Unity, consulte [seção de "Criar o projeto do Unity" Base do módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Depois que o projeto é carregado, clique na guia "loja de ativos", conforme mostrado na imagem abaixo. Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite "TROCADILHO" e selecione o ativo de "Photon TROCADILHO 2 - livre" nos resultados da pesquisa. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Baixe e importe este ativo ao pressionar os botões "Download" e "Importar".

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Depois de Photon tiver concluído o processo de importação, o Assistente de trocadilho será exibido. Levar a ID do aplicativo (que deve estar na sua área de transferência) da etapa 4 e cole-o na caixa de AppID e pressione o botão de "Projeto de instalação". 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Depois de adicionar com êxito o AppID, navegue até "Photon"->"PhotonUnityNetworking" -> "Recursos" -> "PhotonServerSettings" em ativos. Selecionar a opção "Usar servidor de nome" e defina a região fixa como "EUA" ou sua região do serviço photon.

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Parabéns

Com êxito ter criado uma conta de Photon, configurar um servidor local do Photon e importados TROCADILHO para Unity. A próxima etapa é configurar o projeto e, em seguida, permitir conexões com outros usuários para que vários usuários podem ver seu trabalho. 

[Próxima lição: Sharing(Photon) lição 2](mrlearning-sharing(photon)-ch2.md)


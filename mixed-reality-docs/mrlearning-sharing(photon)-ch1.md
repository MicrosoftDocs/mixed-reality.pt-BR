---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327727"
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

2. Depois que você se inscreveu, clique em SDKs. Quando você estiver nessa página, clique em "servidor" e faça a garantir que ela diz, "auto-hospedado." Em seguida, role para baixo e clique em "servidor", como visto na segunda imagem abaixo.

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. Isso fará com que uma caixa de texto aparecer rotulados, "Leia-me". Vá em frente e lê-lo. Quando terminar, clique no link ao lado de "downloadSDK" para baixá-lo.


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. Clique duas vezes na pasta após a conclusão do download.  Depois que o Explorador de arquivos é aberto, revelando a pasta do SDK, copie a pasta do SDK.
   
   - A próxima etapa seria ir na unidade c: windows e criar uma nova pasta chamada 'server'.
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - Agora abra a pasta e cole a pasta do SDK que você copiou anteriormente.
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. Após a conclusão, abra a pasta do SDK e vá para "implantar", em seguida, "bin_Win64", em seguida, clique duas vezes em "controle photon".


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> Observação: Se você tiver dúvidas sobre o endereço IP, ou quaisquer outras perguntas semelhantes, você pode encontrar a maior parte das suas informações na barra de ferramentas (conforme mostrado na imagem abaixo).
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. Agora que o servidor está configurado e iniciado, volte para o site Photon e certifique-se de que você ainda está conectado (ou entre novamente, se você não estiver). Clique no ícone do perfil (demarcado no canto superior direito da imagem abaixo) e selecione "seus aplicativos".
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. Crie uma ID de aplicativo clicando no botão "criar um novo aplicativo".

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - Selecione "Photon TROCADILHO" no menu suspenso em "tipo de photon". Em seguida, dê a ele um nome, neste exemplo, podemos denominado "HoloLensPhotonProject". Quando terminar, clique no botão "Criar".

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. Depois disso, retornar à página de seus aplicativos e você deverá ver algo semelhante à imagem abaixo. Clique na ID do aplicativo e copie-o. Colar é em algum lugar, que você pode acessar facilmente.  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. Crie um novo projeto do unity e nomeie-a como "HLSharingProject". Para obter instruções sobre como criar um novo projeto do Unity, consulte [seção de "Criar o projeto do Unity" Base do módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 


10. Depois que o projeto é carregado, clique na guia "loja de ativos", conforme mostrado na imagem abaixo. Em seguida, na caixa de pesquisa realçada na imagem abaixo, digite "TROCADILHO" e selecione o ativo "Photon TROCADILHO-2" gratuito"nos resultados da pesquisa. 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. Baixe e importe este ativo ao pressionar os botões "Download" e "Importar".
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>Parabéns

Com êxito ter criado uma conta de Photon, configurar um servidor local do Photon e importados TROCADILHO para Unity. A próxima etapa é configurar o projeto e, em seguida, permitir conexões com outros usuários para que vários usuários podem ver seu trabalho. 

[Próxima lição: Sharing(Photon) lição 2](mrlearning-sharing(photon)-ch2.md)


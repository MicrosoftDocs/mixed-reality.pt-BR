---
title: Módulo do ASA de aprendizado MR do Azure âncora espacial no HoloLens 2
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327978"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (corrigir-me se eu estiver errado)

Nesta lição, 

Objetivos:

* Saiba como _

* Saiba como _

  

## <a name="instructions"></a>Instruções

### <a name="setting-up-photon"></a>Configurando Photon

1. Configurar uma [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) conta. Isso consistirá de entrada de seu email e passando por algumas etapas de verificação.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Depois que você se inscreveu, clique em SDKs. Quando você estiver nessa página, clique em "servidor" e faça a garantir que ela diz, "auto-hospedado." Em seguida, role para baixo e clique em "servidor", como visto na segunda imagem abaixo.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. Isso fará com que uma caixa de texto aparecer rotulados, "Leia-me". Vá em frente e lê-lo. Quando terminar, clique no link ao lado de "downloadSDK" para baixá-lo.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Clique duas vezes na pasta após a conclusão do download.  Depois que o Explorador de arquivos é aberto, revelando a pasta do SDK, copie a pasta do SDK.
   
   - A próxima etapa seria ir na unidade c: windows e criar uma nova pasta chamada 'server'.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - Agora abra a pasta e cole a pasta do SDK que você copiou anteriormente.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. Após a conclusão, abra a pasta do SDK e vá para "implantar", em seguida, "bin_Win64", em seguida, clique duas vezes em "controle photon".


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Observação: Se você tiver dúvidas sobre o endereço IP, ou quaisquer outras perguntas semelhantes, você pode encontrar a maior parte das suas informações na barra de ferramentas (conforme mostrado na imagem abaixo).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Agora que o servidor está configurado e iniciado, volte para o site Photon e clique no ícone do perfil (boxed na imagem abaixo) e selecione "seus aplicativos".
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Crie uma ID de aplicativo clicando no botão "criar um novo aplicativo".

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Selecione "Photon RUN" no menu suspenso em "tipo de photon". Em seguida, dê a ele um nome, (algo que você deve se lembrar). Neste exemplo, demos o nome "HoloLensPhotonProject". Quando terminar, clique em "criar".

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. Depois disso, retornar à página de seus aplicativos e você deverá ver algo semelhante à imagem abaixo. Clique na ID do aplicativo e copie-o. Colar é em algum lugar, que você pode acessar facilmente.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Crie um novo projeto do unity. Abra o Hub do Unity e clique em "nova". Nomeie-a como "HLSharingProject". Clique em criar. 

   > Observação: Isso pode levar até 2 minutos para carregar, com base na velocidade do seu computador.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Observação: escolha um local para salvar seu projeto em seu computador, alterando a opção "local". Salve-o em um lugar você lembrar e ter acesso fácil a.

10. Depois que o projeto é carregado, clique em "repositório de ativos". Em seguida, na caixa de pesquisa mostrada na imagem abaixo, digite "TROCADILHO" e selecione o ativo "Photon TROCADILHO-2" gratuito". 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. Baixe e importe!
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Configurar o projeto do Unity** 

11. Baixe um novo ativo necessário para configurar Photon no Unity clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. No Unity, clique no menu de ativos e selecione "Importar ativos", clique em "ativos personalizados".

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Selecione o pacote do Unity que você acabou de baixar o link fornecido na etapa 1. Uma vez que aparece no botão Importar no Unity, clique nele.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Observação: sempre que você baixou o pacote será onde encontrá-lo. A imagem acima não apresentação para onde você encontrará o pacote.

14. Criar uma nova cena (Isso pode ser feito usando o controle / command + N ou clicando em "file" e selecionando "nova cena."). Salve a cena como "HLSharedProjectMain".

> Observação: você pode receber um pop-up que é semelhante à imagem a seguir. Por enquanto, basta clicar em "não".
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. Em, clique em "Toolkit de realidade mista" em "Adicionar à cena e configurar".

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. Assim que estiver concluído, um novo arquivo de configuração será exibida, oferecendo a opção para personalizar o perfil. Clique em "copiar e personalizar."

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Role para baixo e desmarque a opção "Habilitar sistema de diagnóstico". Isso tornará mais fácil de configurar esse projeto.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Abra as configurações de compilação (controle + shift + B). Observe que o programa está atualmente definido na plataforma "PC, Mac e Linux autônomo". Para este projeto, defina a plataforma a ser "plataforma universal do windows". Selecione-o e clique em "alternar plataforma".

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. Uma vez concluído, clique na caixa que diz "Adicionar cenas abertas". Agora, vá para o painel do Inspetor e certifique-se de que a caixa de seleção à direita de "suportada de realidade virtual" (conforme mostrado na imagem abaixo) é verificada. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Observação: Certifique-se também de que a caixa de seleção ao lado de "cenas/HLSharedProjectMain" também é verificada.

20. Sob as "configurações de publicação" no painel Inspetor Role para baixo até "recursos" e certifique-se apenas as seguintes caixas de seleção são marcadas:

- cliente da Internet
- servidor de cliente da Internet
- servidor de cliente de rede privada
- camera/webcam
- Microfone

21. Assim como a etapa 12, a próxima etapa seria importar outro pacote personalizado chamado "Da lição 2", que pode ser baixado [aqui]. [link lesson2.unitypackage aqui] Importe o pacote.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. Agora, no painel de projeto, vá para a pasta "pré-fabricados", já que nas próximas etapas você irá implementar alguns pré-fabricados na cena. Na pasta "pré-fabricados", clique e arraste pré-fabricado, "DebugWindow" na hierarquia. Quando terminar, salve o projeto (clique em arquivo, em seguida, salvar, ou CTRL + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Observação: Você pode perceber um pop-up são exibidas à medida que você clicar no pré-fabricado, solicitando que você sobre o Essentials TMP. Clique em "Importar TMP Essentials" como eles serão necessários.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Conectar-se vários usuários**

23. Como na etapa 22, na pasta "pré-fabricados" no painel de projeto, a próxima etapa é arrastar e soltar "NetworkLobby" pré-fabricado na hierarquia. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. Quando você abrir pré-fabricado pai, "NetworkLobby", você deverá ver um filho pré-fabricado, "NetworkRoom". Com ele selecionado, vá para o painel do Inspetor e clique em "Adicionar componente". Pesquise "PhotonView" e adicione o componente.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Crie um novo objeto jogo vazio na hierarquia (botão direito do mouse na hierarquia e selecione "empty"). Verifique se o posicionamento é definido como x = 0, y = 0, z = 0 e nomear o objeto, "PhotonUser".

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Parabéns




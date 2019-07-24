---
title: Módulo do ASA do Sr Learning âncora espacial do Azure no HoloLens 2
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

Seus

* Saiba como _____________________________________________

* Saiba como _________________________________________________

  

## <a name="instructions"></a>Instruções

### <a name="setting-up-photon"></a>Configurando o Photon

1. Configure uma conta do [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) . Fazer isso consistirá em entrada seu email e passar por algumas etapas de verificação.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Depois de se inscrever, clique em SDKs. Quando você estiver nessa página, clique em "servidor" e verifique se ele diz "auto-hospedado". Em seguida, role para baixo e clique em "servidor", como visto na segunda imagem abaixo.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. Isso fará com que uma caixa de texto apareça rotulada, "Leia-me". Vá em frente e leia-o. Quando terminar, clique no link ao lado de "downloadSDK" para baixá-lo.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Clique duas vezes na pasta após a conclusão do download.  Quando o explorador de arquivos abrir revelar a pasta do SDK, copie a pasta do SDK.
   
   - A próxima etapa seria ir para a unidade C: do Windows e criar uma nova pasta chamada ' Server '.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - Agora, abra a pasta e cole a pasta do SDK que você copiou anteriormente.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. Após a conclusão, abra a pasta do SDK e vá para "implantar", em seguida, "bin_Win64" e clique duas vezes em "controle Photon".


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Observação: Se você tiver alguma dúvida sobre o endereço IP ou outras perguntas semelhantes, poderá encontrar a maioria das suas informações na barra de ferramentas (conforme mostrado na imagem abaixo).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Agora que o servidor está configurado e iniciado, volte para o site do photon e clique no ícone de perfil (na imagem abaixo) e selecione "seus aplicativos".
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Crie uma ID de aplicativo clicando no botão "criar um novo aplicativo".

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Selecione "Photon RUN" no menu suspenso em "Photon Type". Em seguida, dê um nome a ele (algo que você se lembraria). Neste exemplo, nomeamos "HoloLensPhotonProject". Quando terminar, clique em "criar".

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. Depois disso, volte para a página de aplicativos e você verá algo semelhante à imagem abaixo. Clique na ID do aplicativo e copie-a. Colar é em algum lugar que você pode acessar facilmente.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Crie um novo projeto do Unity. Abra o Hub do Unity e clique em "novo". Nomeie-o como "HLSharingProject". Em seguida, clique em criar. 

   > Anotações Isso pode levar até 2 minutos para ser carregado, com base na velocidade do seu computador.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Observação: escolha um local para salvar o projeto em seu computador alterando a opção "local". Salve-o em um lugar onde você se lembrará e terá acesso fácil ao.

10. Depois que o projeto for carregado, clique em "repositório de ativos". Em seguida, na caixa de pesquisa mostrada na imagem abaixo, digite "trocadilho" e selecione o ativo "Photon trocadilho-2 FREE". 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. Baixe e importe!
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Configurando o projeto do Unity** 

11. Baixe um novo ativo necessário para configurar o Photon no Unity clicando [aqui.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. No Unity, clique no menu ativos e selecione "importar ativos" e clique em "ativos personalizados".

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Selecione o pacote do Unity que você acabou de baixar do link fornecido na etapa 1. Depois que o botão importar aparecer no Unity, clique nele.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Observação: sempre que você baixou o pacote para será onde você o encontrará. A imagem acima não retrata onde você encontrará o pacote.

14. Crie uma nova cena (isso pode ser feito usando o controle/comando + N ou clicando em "arquivo" e selecionando "nova cena."). Salve a cena como "HLSharedProjectMain".

> Observação: você pode receber um pop-up parecido com a imagem abaixo. Por enquanto, basta clicar em "não".
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. Em "Mixed Reality Toolkit", clique em "adicionar à cena e configurar".

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. Quando isso for concluído, um novo arquivo de configuração será exibido, oferecendo a você a opção de personalizar o perfil. Clique em "copiar e personalizar".

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Role para baixo e desmarque "habilitar o sistema de diagnóstico". Isso facilitará a configuração deste projeto.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Abra as configurações de compilação (Control + Shift + B). Observe que o programa está definido atualmente na plataforma "PC, Mac e Linux standalone". Para este projeto, defina a plataforma como "plataforma universal do Windows". Selecione-o e clique em "alternar plataforma".

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. Após a conclusão, clique na caixa que diz "Adicionar cenas abertas". Agora, acesse o painel Inspetor e verifique se a caixa de seleção à direita de "realidade virtual com suporte" (conforme mostrado na imagem abaixo) está marcada. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Anotações Verifique também se a caixa de seleção ao lado de "cenas/HLSharedProjectMain" também está marcada.

20. Em "configurações de publicação" no painel Inspetor, role para baixo até "recursos" e verifique se apenas as seguintes caixas de seleção estão marcadas:

- cliente de Internet
- servidor de cliente de Internet
- servidor de cliente de rede privada
- câmera/Webcam
- Microfone

21. Da mesma forma que a etapa 12, a próxima etapa seria importar outro pacote personalizado chamado "lição 2", que pode ser baixado [aqui.] [o link do lição 2. unitypackage é inserido aqui] Importe esse pacote.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. Agora, no painel projeto, vá para a pasta "pré-fabricados", já que, nas próximas etapas, você implementará algumas pré-fabricados na cena. Na pasta "pré-fabricados", clique e arraste o pré-fabricado, "DebugWindow" para a hierarquia. Quando terminar, salve o projeto (clique em arquivo, salvar ou controle + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Anotações Você pode observar que um pop-up aparece ao clicar no pré-fabricado, solicitando-lhe informações sobre o TMP Essentials. Clique em "importar os fundamentos do TMP", pois eles serão necessários.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Conectando vários usuários**

23. Como a etapa 22, na pasta "pré-fabricados" no painel projeto, a próxima etapa é arrastar e soltar o pré-fabricado "NetworkLobby" na hierarquia. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. Quando você abrir o pré-fabricado pai, "NetworkLobby", verá um pré-fabricado filho, "NetworkRoom". Com ele selecionado, vá para o painel Inspetor e clique em "Adicionar componente". Pesquise por "PhotonView" e adicione o componente.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Crie um novo objeto de jogo vazio na hierarquia (clique com o botão direito do mouse na hierarquia e selecione "vazio"). Verifique se o posicionamento está definido como x = 0, y = 0, z = 0 e nomeie o objeto "PhotonUser".

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Parabéns




---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465210"
---
# <a name="connecting-multiple-users"></a>**Conectar-se vários usuários** 

Nesta lição, aprendemos como se conectar a vários usuários como parte de uma experiência de compartilhada em tempo real. No final desta lição, você poderá abrir o aplicativo em vários dispositivos e ver o avatar, representado por uma esfera, representações de cada pessoa que une. 

Objetivos:

- Configurar o TROCADILHO dentro de seu aplicativo
- Configurar os jogadores
- Saiba como se conectar a vários usuários em uma experiência de compartilhado

### <a name="instructions"></a>Instruções

1. Os ativos -> recursos -> pasta pré-fabricados no painel de projeto, arraste e solte pré-fabricado NetworkLobby à hierarquia, conforme mostrado na imagem abaixo.


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Quando você expande NetworkLobby, você verá um objeto filho chamado NetworkRoom. Com NetworkRoom selecionado, vá para o painel do Inspetor e clique em Adicionar componente. Pesquisar PhotonView e adicione o componente.

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Crie um novo objeto jogo vazio na hierarquia. Clique com o botão direito na hierarquia e selecione vazio no menu de contexto. Verifique se o posicionamento é definido como x = 0, y = 0, z = 0 e nomear o objeto, PhotonUser.

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Clique em Adicionar componente e de tipo genérico de sincronização de Net. Selecione a classe genérica sincronização Net. Quando a classe for exibida, clique na caixa de seleção do usuário para ativá-lo. 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Clique em Adicionar componente novamente e digite Photon exibição. Selecione a classe de exibição Photon que aparece na lista suspensa.

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Clique no ícone de arquivo para a classe genérica sincronização Net. Arraste e solte-o no campo de componentes observada Photon da exibição. ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. Em seguida, criamos esferas para representar cada pessoa que une uma experiência compartilhada. Clique com botão direito o objeto PhotonUser que você acabou de criar e scrolldown para "objeto 3D e clique em esfera. Isso criará um objeto do jogo esfera como um filho do objeto PhotonUser.

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Dimensionar a esfera até x = 0,06, y = 0,06, ad z = 0,06.

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Arraste o objeto do jogo PhotonUser na pasta pré-fabricados no painel de projeto e, em seguida, excluí-la da cena. Agora, criamos um pré-fabricado que pode ser usado quando ao gerar ou criando novos jogadores em uma experiência compartilhado.

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Observação: Certifique-se de que o objeto do jogo tem copiados com êxito para a pasta pré-fabricados antes de excluí-la da sua hierarquia.

10. Criar um novo objeto na hierarquia, seguindo as instruções na etapa 3 e nomeie-a como SharedPlayground. Em seguida, clique em Add Component, pesquise o Gerenciador de rede genérica e clique nele para adicionar o componente de Gerenciador de rede genérica. Altere a posição do objeto para x = 0, y = 0 e z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Parabéns

Depois que todas as etapas acima forem concluídas, e o processo de compilação também é concluído, pressione o botão Reproduzir e conecte sua 2 HoloLens. Você deve ver uma esfera mover-se, ao mudar sua cabeça. Isso será exibido para qualquer usuário que associa o seu projeto do Unity!

[Próxima lição: Lição 4 para Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)


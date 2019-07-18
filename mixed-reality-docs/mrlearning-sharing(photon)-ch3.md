---
title: Módulo de compartilhamento de aprendizagem do MR para o HoloLens 2
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 92bea1f3130f67645c10e36fe40cd4bc6f8b9151
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293660"
---
# <a name="connecting-multiple-users"></a>Conectando vários usuários

Nesta lição, aprenderemos como conectar vários usuários como parte de uma experiência compartilhada ao vivo. Ao final desta lição, você poderá abrir o aplicativo em vários dispositivos e ver o Avatar, representado por uma esfera, representações de cada pessoa que ingressar. 

Seus

- Configurar o trocadilho em seu aplicativo
- Configurar players
- Saiba como conectar vários usuários em uma experiência compartilhada

### <a name="instructions"></a>Instruções

1. Na pasta ativos-> recursos-> pré-fabricados no painel projeto, arraste e solte o NetworkLobby pré-fabricado para a hierarquia, conforme mostrado na imagem abaixo.

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Ao expandir NetworkLobby, você verá um objeto filho chamado NetworkRoom. Com NetworkRoom selecionado, vá para o painel Inspetor e clique em Adicionar componente. Procure PhotonView e adicione o componente.

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Crie um novo objeto de jogo vazio na hierarquia. Clique com o botão direito do mouse na hierarquia e selecione vazio no menu de contexto. Verifique se o posicionamento está definido como x = 0, y = 0, z = 0 e nomeie o objeto, PhotonUser.

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Clique em Adicionar componente e digite sincronização de rede genérica. Selecione a classe genérica net Sync. Quando a classe for exibida, clique na caixa de seleção do usuário para ativá-la. 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Clique em Adicionar componente novamente e digite Photon exibição. Selecione a classe de exibição Photon que aparece na lista suspensa.

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Clique no ícone de arquivo para a classe genérica net Sync. Arraste e solte-o no campo componentes observados da exibição de Photon. 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. Em seguida, criamos um aqui para representar cada pessoa que une uma experiência compartilhada. Clique com o botão direito do mouse no objeto PhotonUser que você acabou de criar e scrolldown para "objeto 3D e clique em esfera. Isso criará um objeto de jogo de esfera como um filho do objeto PhotonUser.

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Dimensione a esfera para baixo para x = 0.06, y = 0.06, AD z = 0.06.

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Arraste o objeto de jogo PhotonUser para a pasta pré-fabricados no painel projeto e, em seguida, exclua-o da cena. Agora, criamos um pré-fabricado que pode ser usado ao gerar ou criar uma instância de novos jogadores em uma experiência compartilhada.

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Observação: Verifique se o objeto de jogo foi copiado com êxito na pasta pré-fabricados antes de excluí-lo da sua hierarquia.

10. Crie um novo objeto na hierarquia seguindo as instruções na etapa 3 e nomeie-o SharedPlayground. Em seguida, clique em Adicionar componente e pesquise Gerenciador de rede genérico e clique nele para adicionar o componente do Gerenciador de rede genérico. Altere a posição do objeto para x = 0, y = 0 e z = 0.

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Parabéns

Depois que todas as etapas acima forem concluídas e o processo de compilação também for concluído, pressione o botão reproduzir e conecte seu HoloLens 2. Você deve ver uma esfera se movimentando à medida que move sua cabeça. Isso será mostrado para qualquer usuário que ingressar em seu projeto do Unity!

[Próxima lição: Compartilhamento (Photon) lição 4](mrlearning-sharing(photon)-ch4.md)


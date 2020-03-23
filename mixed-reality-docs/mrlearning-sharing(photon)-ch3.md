---
title: Tutoriais de recursos multiusuário – 3. Como conectar vários usuários
description: Conclua este curso para aprender a implementar experiências compartilhadas de vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031226"
---
# <a name="3-connecting-multiple-users"></a>3. Como conectar vários usuários

Nesta lição, aprenderemos a conectar vários usuários como parte de uma experiência compartilhada ao vivo. Ao final desta lição, você poderá abrir o aplicativo em vários dispositivos e ver o avatar, representado por uma esfera, para cada pessoa que entra.

## <a name="objectives"></a>Objetivos

* Configurar o PUN em seu aplicativo
* Configurar jogadores
* Saiba como conectar vários usuários em uma experiência compartilhada

## <a name="instructions"></a>Instruções

1. Na pasta Ativos->Recursos->Pré-fabricados do painel Projeto, arraste e solte o pré-fabricado NetworkLobby para a hierarquia, conforme mostra a imagem abaixo.

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Ao expandir NetworkLobby, você verá um objeto filho chamado NetworkRoom. Com NetworkRoom selecionado, vá para o painel Inspetor e clique em Adicionar Componente. Procure PhotonView e adicione o componente.

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Crie um objeto de jogo vazio na hierarquia. Clique com o botão direito do mouse na hierarquia e selecione Vazio no menu de contexto. Verifique se o posicionamento está definido como x=0, y=0, z=0 e dê ao objeto o nome de PhotonUser.

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Clique em Adicionar Componente e digite Generic Net Sync. Selecione a classe Generic Net Sync. Quando a classe for exibida, clique na caixa de seleção do usuário para ativá-la.

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Clique em Adicionar Componente outra vez e digite Exibição do Photon. Selecione a classe de Exibição do Photon que aparece na lista suspensa.

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Clique no ícone Arquivo para a classe Generic Net Sync. Arraste e solte-o no campo Componentes Observados da Exibição do Photon.

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. Em seguida, criamos esferas para representar cada pessoa que entra para uma experiência compartilhada. Clique com o botão direito do mouse no objeto PhotonUser que você acabou de criar, role para baixo até "Objeto 3D" e clique em Esfera. Isso criará um objeto de jogo de esfera como um filho do objeto PhotonUser.

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Dimensione a esfera para baixo para x=0,06, y=0,06, ad z=0,06.

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Arraste o objeto de jogo PhotonUser para a pasta Pré-Fabricados no painel Projeto e, em seguida, exclua-o da cena. Agora você criou um pré-fabricado que pode ser usado ao gerar ou criar uma instância de novos jogadores em uma experiência compartilhada.

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >Verifique se o objeto de jogo foi copiado com êxito para a pasta Pré-Fabricados antes de excluí-lo da sua hierarquia.

10. Crie um objeto na hierarquia seguindo as instruções na etapa 3 e dê a ele o nome de SharedPlayground. Em seguida, clique em Adicionar Componente e pesquise o gerenciador de rede genérico.  Clique novamente para adicionar o componente Gerenciador de Rede Genérico. Altere a posição do objeto para x=0, y=0 e z=0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>Parabéns

Depois que todas as etapas acima e o processo de build também forem concluídos, pressione o botão Reproduzir e conecte seu HoloLens 2. Você deverá ver uma esfera se movimentando à medida que move a cabeça. Isso será mostrado para qualquer usuário que ingressar em seu projeto do Unity.

[Próxima lição: 4. Compartilhar movimentações de objeto com vários usuários](mrlearning-sharing(photon)-ch4.md)

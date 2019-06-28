---
title: MR aprendizado compartilhando módulo para HoloLens 2
description: Conclua este curso para saber como implementar a experiências compartilhadas com vários usuários dentro de um aplicativo de 2 HoloLens.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415907"
---
# <a name="connecting-multiple-users"></a>**Conectar-se vários usuários** 

Nesta lição, aprenderemos para se conectar a vários usuários como parte de uma experiência de compartilhada em tempo real. No final desta lição, você será capaz de abrir o aplicativo em vários dispositivos e ver representações do "avatar" de cada pessoa que une (avatares representados por uma esfera). 

Objetivos:

- Configurar o TROCADILHO dentro de seu aplicativo
- Configurar os jogadores
- Saiba como se conectar a vários usuários em uma experiência de compartilhado

### <a name="instructions"></a>Instruções

1. Nos ativos > recursos > pré-fabricados pasta do painel projeto, arrastar e soltar o "NetworkLobby" pré-fabricado à hierarquia, conforme mostrado na imagem abaixo.


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Quando você expande o pré-fabricado "NetworkLobby", você deverá ver um objeto filho chamado "NetworkRoom". Com ele selecionado, vá para o painel do Inspetor e clique em "Adicionar componente". Pesquise "PhotonView" e adicione o componente.

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Criar um novo objeto jogo vazio na hierarquia (clique com o botão direito na hierarquia e selecione "Vazio" no menu de contexto). Verifique se o posicionamento é definido como x = 0, y = 0, z = 0 e nomear o objeto, "PhotonUser".

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Clique no botão "Adicionar componente" e digite "Sync Net genérico" e selecione a classe genérica sincronização Net. Depois que a classe for exibida, clique na caixa de seleção de "Usuário" para ativá-lo. 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Novamente clique em "Adicionar componente" e, em seguida, digite "Photon exibição" e selecione a classe de exibição Photon que aparece na lista suspensa.

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Agora clique no ícone no arquivo para a classe de sincronização Net genérico, em seguida, arraste e solte-o ao campo de "Componentes observada" Photon da exibição. ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. Em seguida, queremos criar esferas para representar cada pessoa que une uma experiência compartilhada. Clique com botão direito no objeto "PhotonUser" que você acabou de criar, vá para baixo para o "objeto 3D" e clique em "Esfera". Isso criará um objeto do jogo esfera como um filho do objeto PhotonUser.

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Dimensionar a esfera até x = 0,06, y = 0,06, ad z = 0,06.

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Arraste o objeto do jogo "PhotonUser" para a pasta de "pré-fabricados" no painel de projeto. Em seguida, exclua-o da cena. Agora, criamos um pré-fabricado que será usado ao gerar ou criar uma instância novos jogadores em uma experiência compartilhado.

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Observação: Certifique-se de que o objeto do jogo tem copiados com êxito para a pasta "prefabs" antes de excluí-la da sua hierarquia.

10. Crie um novo objeto na hierarquia (usando instruções semelhantes da etapa 3) e nomeie-a como "SharedPlayground". Em seguida, clique em "Adicionar componente" e pesquise "Gerenciador de rede genérica" e clique nele para adicionar o componente de Gerenciador de rede genérica. Altere a posição do objeto para x = 0, y = 0 e z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Parabéns

Depois que todas as etapas acima forem concluídas, e o processo de compilação for concluído, quando você pressiona o botão Reproduzir e conectar sua 2 HoloLens, você deverá ver uma esfera mover-se à medida que você move a cabeça! Isso será exibido para qualquer usuário que associa o seu projeto do Unity!

[Próxima lição: Lição 4 para Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)


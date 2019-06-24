---
title: Módulo do ASA de aprendizado do MR âncora espacial do Azure em 2 HoloLens
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 4dc36aec4d885fa75ea490446c2d682264049725
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326421"
---
# <a name="persistence-and-sharing-of-azure-spatial-anchors"></a>Persistência e o compartilhamento de âncoras espaciais do Azure

Nesta lição, aprenderemos manter nossos âncoras espacial do Azure em várias sessões do aplicativo salvando nossas informações de âncora para o disco do 2 o HoloLens. Podemos também aprenderá como compartilhar essas informações de ancoragem para outros dispositivos para um alinhamento de âncora de vários dispositivos.

## <a name="objectives"></a>Objetivos

* Saiba como salvar e recuperar informações de ancoragem espacial do Azure do disco local 2 HoloLens, para persistência entre sessões do aplicativo

* Aprenda a compartilhar informações de ancoragem espacial do Azure entre usuários em um cenário de vários dispositivo

  

## <a name="instructions"></a>Instruções

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Persistir âncoras do Azure entre as sessões do aplicativo - salvar a ID da âncora para o disco

1. Pesquisar e adicionar pré-fabricado "SaveAnchorToDisk" à sua cena. Isso inclui dois botões, um botão para salvar quaisquer IDs de âncora do Azure disponíveis para o disco 2 HoloLens e outra para recuperar quaisquer IDs de disco.

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Configurar cada botão de acordo com as instruções abaixo
   - Para o botão chamado "SaveToDisk", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método SaveAzureAnchorIDToDisk() do componente de ASAmoduleScript ParentAnchor do objeto.
   
     > Observação: alguns dos botões podem aparecer sobrepostos os outros botões na cena. Fique à vontade ajustar o posicionamento do botão.
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - Para o botão chamado "GetFromDisk", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método LoadAzureAnchorIDsFromDisk() do componente de ASAmoduleScript ParentAnchor do objeto.

3. Siga as instruções da lição 1 para compilar o aplicativo atualizado para seu dispositivo. Depois de pressionar o botão "Criar âncora do Azure", como você fez na lição anterior, você pode agora salvar a ID de âncora do Azure para o disco, pressionando o botão Salvar no disco.

4. Reinicie o aplicativo, iniciar a sessão do Azure, pressione o botão de "ID de ancoragem de carga" e, em seguida, pressione o botão de "Localizar âncora do Azure" para localizar a âncora associada com a ID é salvo no disco. Toda a cena agora deve ser ajustados para a posição, no local salvo a âncora anteriormente!

### <a name="share-azure-anchors-between-multiple-devices"></a>Compartilhar Azure âncoras entre vários dispositivos

Nesta seção, aprenderemos como compartilhar a ID de âncora do Azure entre vários dispositivos. Isso permitirá que vários dispositivos para consultar o Azure para a mesma ID de ancoragem, permitindo que o nosso hologramas ancoradas e cenas espacialmente alinhados. Alinhamento espacial (vendo as mesmas hologramas no mesmo local físico entre os vários dispositivos) é chaves local para local experiências compartilhadas no HoloLens 2. Há várias maneiras para transferir informações sobre IDs do azure entre dispositivos, incluindo os métodos descritos nas experiências compartilhadas âncoras espacial do Azure tutoriais (TODO: Adicionar link.) Este exemplo usa um serviço web simples para carregar e baixar as IDs de âncora entre dispositivos.

1. Adicione pré-fabricado "ShareAnchor" em sua hierarquia. Este pré-fabricado adiciona dois novos botões à sua cena; outro para carregar informações de ID de ancoragem e outro para baixar informações de ID de ancoragem. 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Configurar cada botão de acordo com as instruções abaixo

   - Para o botão chamado "SendSharedAnchor", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método ShareAnchor() do componente de ASAmoduleScript ParentAnchor do objeto.

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - Para o botão chamado "GetSharedAnchor", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método GetSharedAzureAnchor() do componente de ASAmoduleScript ParentAnchor do objeto.

3. Siga as instruções do [lição 1](mrlearning-base-ch1.md). para compilar o aplicativo atualizado para seu dispositivo. Depois de pressionar o botão "Criar âncora do Azure", como você fez na lição anterior, você pode agora compartilhar a ID de âncora do Azure para outros dispositivos pressionando o botão de compartilhamento para outro dispositivo.

   > Observação: Selecione a âncora de pai e role para baixo até o script de âncora do pai. Certifique-se de que o "público compartilhamento pin" é exclusivo, para que quando você compartilhá-lo, você saberá que é seu que você está compartilhando. Pode haver milhares de usuários compartilhando suas âncoras do Azure, portanto, isso permitirá que você verifique se que você estiver compartilhando as âncoras correto do Azure.

4. Se você tiver outro dispositivo 2 HoloLens, inicie o aplicativo e, em seguida, iniciar a sessão do Azure. Pressione o botão "Obter a ID de ancoragem compartilhados" e, em seguida, pressione o botão de "Localizar âncora do Azure" para localizar a âncora associada com a ID é salvo no disco. Toda a cena agora deve ser ajustados para a posição, onde ele foi colocado no dispositivo de 2 HoloLens! Se você tiver apenas um 2 do HoloLens, você pode ainda testar a funcionalidade reiniciando o aplicativo iniciando a sessão do Azure, em seguida, pressione o botão "Obter a ID de ancoragem compartilhados" e, em seguida, pressione o botão de "Localize Azure âncora" para localizar a âncora associada com a ID é salvo no disco. Toda a cena agora deve ser ajustados para a posição, no local salvo a âncora anteriormente!

## <a name="congratulations"></a>Parabéns
Nesta lição, você aprendeu como persistir âncoras espacial do Azure entre sessões do aplicativo e reinicializações de aplicativo, salvando a ID da âncora espacial do Azure para o disco local do HoloLens 2. Você também aprendeu como compartilhar âncoras espacial do Azure entre vários dispositivos para uma experiência básica holograma de multiusuário, estática compartilhada!

Podemos aprenderá a implementar âncoras espacial do Azure como parte de uma experiência de compartilhado local totalmente interativa durante a última lição do módulo de compartilhamento. Uma experiência de compartilhamento local pode incluir a funcionalidade, como identificadores de objeto 3D sincronizado posição, rotação e escala, para cada usuário e compartilhados de estados do aplicativo. Âncoras espacial do Azure aprimora esses cenários compartilhados, fornecendo cada participante com uma âncora comum que permite que todos os usuários vejam os objetos virtuais no mesmo local físico. Isso é verdadeiro em uma variedade de plataformas de dispositivos, incluindo dispositivos HoloLens, Android e iOS. Para saber como desenvolver uma experiência compartilhada, conclua todas as lições no módulo do compartilhamento.

Na próxima lição, aprenderemos fornecer aos usuários com comentários em tempo real. Esses comentários incluirá informações sobre a criação de ancoragem, a qualidade das noções básicas sobre o ambiente e o estado da sessão do Azure. Sem comentários, os usuários talvez não saibam se uma âncora foi com êxito o upload para o Azure, se a qualidade do ambiente é suficiente para a criação de âncora, ou o estado atual.

[Próxima lição: Lição 3 para ASA](mrlearning-asa-ch3.md)


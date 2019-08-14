---
title: Tutoriais de âncoras espaciais do Azure-2. Salvando, recuperando e compartilhando âncoras espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 70f84c1ec03919a15bed486ffa51fb57db39deec
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977968"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Salvando, recuperando e compartilhando âncoras espaciais do Azure

Neste tutorial, aprenderemos como salvar nossas âncoras espaciais do Azure em várias sessões de aplicativo salvando nossas informações de âncora no disco do HoloLens 2. Também aprenderemos como compartilhar essas informações de âncora para outros dispositivos para um alinhamento de âncora de vários dispositivos.

## <a name="objectives"></a>Objetivos

* Saiba como salvar e recuperar informações de âncora espacial do Azure do disco local do HoloLens 2, para persistência entre sessões de aplicativo

* Saiba como compartilhar informações de âncora espacial do Azure entre usuários em um cenário de vários dispositivos

## <a name="instructions"></a>Instruções

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Persistir âncoras do Azure entre sessões de aplicativo-salvar ID de âncora em disco

1. Pesquise e adicione o SaveAnchorToDisk pré-fabricado à sua cena. Isso inclui dois botões, um botão para salvar quaisquer IDs de âncora do Azure disponíveis no disco do HoloLens 2 e outro para recuperar quaisquer IDs do disco.

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Configure cada botão de acordo com as instruções abaixo

   - Para o botão chamado SaveToDisk, crie um novo evento sob o botão pressionado evento acionado, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método SaveAzureAnchorIDToDisk () do componente ASAmoduleScript do objeto ParentAnchor.
   
     > Observação: alguns dos botões podem aparecer sobrepondo os outros botões na cena. Fique à vontade para ajustar o posicionamento do botão.

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - Para o botão chamado GetFromDisk, crie um novo evento sob o botão pressionado evento acionado, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método LoadAzureAnchorIDsFromDisk () do componente ASAmoduleScript do objeto ParentAnchor.

3. Siga as instruções do tutorial 1 para criar o aplicativo atualizado para seu dispositivo. Depois de pressionar o botão criar âncora do Azure, como fez na lição anterior, você pode salvar a ID de âncora do Azure em disco pressionando o botão salvar em disco.

4. Reinicie o aplicativo, inicie a sessão do Azure, pressione carregar ID de âncora e, em seguida, pressione localizar âncora do Azure para localizar a âncora associada à ID salva no disco. A cena inteira agora deve se ajustar à posição, no local em que você salvou a âncora anteriormente!

### <a name="share-azure-anchors-between-multiple-devices"></a>Compartilhar âncoras do Azure entre vários dispositivos

Nesta seção, aprenderemos como compartilhar a ID de âncora do Azure entre vários dispositivos. Isso permitirá que vários dispositivos consultem o Azure para a mesma ID de âncora, permitindo que nossos hologramas ancorados e cenas sejam alinhados espacialmente. O alinhamento espacial (Ver os mesmos hologramas no mesmo local físico entre vários dispositivos) é a chave para experiências compartilhadas locais no HoloLens 2. Há várias maneiras de transferir informações sobre as IDs do Azure entre os dispositivos, incluindo métodos descritos nos [tutoriais](mrlearning-sharing(photon)-ch1.md)de tutoriais de experiências compartilhadas do Azure. Este exemplo usa um serviço Web simples para carregar e baixar IDs de âncora entre dispositivos.

1. Adicione o ShareAnchor pré-fabricado à sua hierarquia. Este pré-fabricado adiciona dois novos botões à sua cena; uma para carregar informações de ID de âncora e outra para baixar informações de ID de âncora. 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Configure cada botão de acordo com as instruções abaixo

   - Para o botão chamado, SendSharedAnchor, crie um novo evento sob o botão pressionado evento acionado, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método ShareAnchor () do componente ASAmoduleScript do objeto ParentAnchor.

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - Para o botão chamado, GetSharedAnchor, crie um novo evento sob o botão pressionado evento acionado, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método GetSharedAzureAnchor () do componente ASAmoduleScript do objeto ParentAnchor.

3. Siga as instruções do [tutorial 1](mrlearning-base-ch1.md). para criar o aplicativo atualizado para seu dispositivo. Depois de pressionar o botão criar âncora do Azure, como você fez na lição anterior, você pode compartilhar a ID de âncora do Azure para outros dispositivos pressionando o botão compartilhar para outro dispositivo.

   > Observação: Selecione a âncora pai e role para baixo até o script de âncora pai. Verifique se seu PIN de compartilhamento público é exclusivo, para que, ao compartilhá-lo, você saiba que ele é seu compartilhado. Pode haver milhares de usuários compartilhando suas âncoras do Azure, portanto, fazer isso permitirá que você esteja compartilhando as âncoras do Azure corretas.

4. Se você tiver outro dispositivo HoloLens 2, inicie o aplicativo e inicie a sessão do Azure. Pressione o botão obter ID de âncora compartilhada e, em seguida, pressione o botão Localizar âncora do Azure para localizar a âncora associada à ID salva no disco. A cena inteira agora deve se ajustar à posição, no local onde ele foi colocado no outro dispositivo de HoloLens 2! Se você tiver apenas um HoloLens 2, ainda poderá testar a funcionalidade reiniciando o aplicativo, iniciando a sessão do Azure e, em seguida, pressionando o botão de botão "obter ID de âncora compartilhada" e, em seguida, pressione o botão Localizar âncora do Azure para localizar a âncora associada ao ID que salvamos no disco. A cena inteira agora deve se ajustar à posição, no local em que você salvou a âncora anteriormente!

## <a name="congratulations"></a>Parabéns
Nesta lição, você aprendeu como persistir as âncoras espaciais do Azure entre as sessões do aplicativo e reinicializações do aplicativo salvando a ID de âncora espacial do Azure no disco local no HoloLens 2. Você também aprendeu a compartilhar as âncoras espaciais do Azure entre vários dispositivos para uma experiência compartilhada básica com vários usuários e com holograma estático.

Aprendemos como implementar as âncoras espaciais do Azure como parte de uma experiência compartilhada de local totalmente interativa durante a lição final do módulo de compartilhamento. Uma experiência de compartilhamento local pode incluir funcionalidades como a posição de objeto 3D sincronizada, rotação e escala, identificadores para cada usuário e Estados de aplicativos compartilhados. As âncoras espaciais do Azure aprimoram esses cenários compartilhados, fornecendo a cada participante uma âncora comum que permite que todos os usuários vejam objetos virtuais no mesmo local físico. Isso é verdadeiro em uma variedade de plataformas de dispositivo, incluindo o HoloLens, Android e dispositivos iOS. Para saber como desenvolver uma experiência compartilhada, conclua todas as lições no módulo de compartilhamento.

Na próxima lição, aprenderemos a fornecer aos usuários comentários em tempo real. Esses comentários incluirão informações sobre a criação de âncora, a qualidade da compreensão do ambiente e o estado da sessão do Azure. Sem comentários, os usuários podem não saber se uma âncora foi carregada com êxito no Azure, se a qualidade do ambiente é suficiente para a criação de âncora ou para o estado atual.

[Próxima lição: 3. Exibir comentários da Âncora Espacial do Azure](mrlearning-asa-ch3.md)


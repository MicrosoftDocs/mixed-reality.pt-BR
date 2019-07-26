---
title: Módulo do ASA do Sr Learning âncora espacial do Azure no HoloLens 2
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 391e797ad9cc8933b057366ab47a3f453c68723e
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485770"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introdução às âncoras espaciais do Azure

Bem-vindo ao segundo módulo dos tutoriais do HoloLens 2. Antes de começar, certifique-se de que todos os [pré-requisitos](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) estejam concluídos. Se você ainda não concluiu o primeiro [módulo base](mrlearning-base.md) , é recomendável que você conclua o módulo primeiro. Se você estiver iniciando em um novo projeto do Unity, siga as etapas de criação do novo projeto no [módulo base](mrlearning-base.md). 

## <a name="objectives"></a>Objetivos

* Conheça os conceitos básicos do desenvolvimento com âncoras espaciais do Azure com o HoloLens 2

* Criar, carregar e baixar âncoras espaciais

## <a name="instructions"></a>Instruções

### <a name="downloading-and-importing-assets"></a>Baixando e importando ativos
Antes de começar, baixe e importe os seguintes ativos:

[Âncoras Espaciais do Azure](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Pacote de ativos do módulo de base do MR](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2)

[Pacote de ativos do módulo ASA](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)

[Kit de ferramentas de realidade misturada](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)

> Observação: Consulte a etapa 5 para obter instruções específicas sobre como importar âncoras espaciais do Azure, etapa 6 para obter instruções específicas sobre o pacote de ativos do módulo base do MR e as etapas 3 a 4 para obter instruções específicas sobre o MRKT (Kit de ferramentas de realidade mista).

1. Crie uma nova cena em seu projeto. Clique com o botão direito do mouse na sua pasta de cena, clique em criar e em cena. Nomeie a nova cena ASALearningmodule.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Clique duas vezes em ASALearningmodule para ver alguns itens predefinidos que aparecem junto com a nova cena. 
3. Configure a cena para o desenvolvimento de realidade misturada. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Observação: Você verá um pop-up que diz, você deve escolher um arquivo para o kit de ferramentas de realidade misturada. Clicar em OK leva você para a etapa 4.

4. Ao escolher um arquivo para o MRTK, selecione, DefaultMixedRealityToolkitConfigurationProfile.

> Observação: Se você tiver seu próprio perfil de configuração, sinta-se à vontade para usá-lo.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Agora a cena está configurada para realidade misturada. Certifique-se de salvar sua cena (faça isso com controle/comando + S ou clique no arquivo e clique em salvar). 

5. Importe as [âncoras espaciais do Azure](https://github.com/azure/azure-spatial-anchors-samples/releases). Para usar âncoras espaciais, você deve importar esse ativo. Clique no link acima e clique com o botão direito em AzureSpatialAnchors. unitypackage. Clique em salvar destino como e salve-o em seu computador. 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

Depois de salvá-lo, volte para o Unity, clique em ativos, vá para baixo até importar pacote. Em seguida, clique em pacote personalizado... Os arquivos do computador serão abertos. Ao fazer isso, localize onde você salvou o pacote de âncoras espaciais do Azure e selecione-o. Em seguida, clique em abrir.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

Um pop-up é exibido, providingg uma lista de ferramentas e configurações e solicitando o que deve ser importado. Selecione ***todas*** as opções disponíveis e clique em importar.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> Observação: Seja paciente, levará alguns minutos para ser importado. 

6. Importar [pacote de ativos do módulo base https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) do Mr] avançar. Assim como a etapa 5, clique no link acima. Em seguida, clique com o botão direito do mouse em BasemoduleAssetsV1 1. unitypackag e clique em salvar destino como e salve-o em seu computador.

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> Dica: Salve todos esses ativos na mesma pasta para que eles sejam mais fáceis de localizar e tenham acesso ao. Ele mantém tudo bom e organizado.

Assim como a etapa 5, volte para o Unity, clique em ativos e passe o mouse sobre importar pacote. Clique em pacote personalizado... Os arquivos do computador serão exibidos novamente. Vá para onde você armazenou o pacote de ativos do módulo base. e selecione-o. Clique em Abrir.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> Observação: Pode haver mais ativos necessários posteriormente neste módulo. Siga estas etapas para importar todos os ativos mencionados neste ponto em diante. 

7. Importe o [pacote de módulo asa](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1) usando a mesma abordagem que importar os pacotes anteriores.

### <a name="configuring-your-scene"></a>Configurando sua cena

Nesta seção, adicionaremos pré-fabricados e scripts à cena para criar uma série de botões que demonstram os conceitos básicos de como as âncoras locais e as âncoras espaciais do Azure se comportam em um aplicativo.

8. Na guia projeto, abaixo da pasta ativos, clique em ASAmoduleAssets. Depois de selecionado, você verá dois pré-fabricados: ButtonParent e ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. Arraste ambos os pré-fabricados para a cena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. Clique duas vezes na âncora pai para selecioná-la. Talvez seja necessário ajustar sua exibição para ver toda a cena. Ajuste sua cena conforme necessário.

Familiarize-se com o pré-fabricado ParentAnchor. Atualmente, o objeto de jogo chamado, ParentAnchor, é um cubo colorido para fins de demonstração. Eventualmente, vamos ocultar o cubo e posicionar nosso conteúdo como um filho do ParentAnchor. Esse pré-fabricado inclui o script AzureSpatialAnchorsDemoWrapper.cs (incluído no SDK do ASA) e o script ASAmoduleScript.cs, incluído como parte desse módulo para o objeto ParentAnchor. 

11. Configurar botões. No ButtonParent pré-fabricado, observe vários botões rotulados. Esses botões são criados a partir do MRTK PressableButton pré-fabricados. Saiba mais sobre como criar botões pressionáveis a partir do [módulo base](mrlearning-base-ch2.md). Para cada botão, adicione um evento que será disparado quando o usuário pressionar ou selecionar o botão de acordo com a lista abaixo. 

- Para o botão chamado, StartAzureSession, crie um novo evento sob o botão pressionado evento acionado, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método StartAzureSession () do componente ASAmoduleScript do objeto ParentAnchor.

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Para o nome do botão, StopAzureSession, crie um novo evento sob o botão pressionado evento acionado, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método StopAzureSession () do componente ASAmoduleScript do objeto ParentAnchor.

- Para o botão chamado, createanchor, crie um novo evento sob o botão pressionado evento acionado, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método CreateAzureAnchor () do componente ASAmoduleScript do objeto ParentAnchor.

- Para o botão chamado, comece a procurar âncora, crie um novo evento sob o botão Presse "gatilho de evento, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método FindAzureAnchor () do componente ASAmoduleScript do objeto ParentAnchor.

- Para o botão chamado, DeleteAzureAnchor, crie um novo evento sob o botão pressionado evento acionado, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método DeleteAzureAnchor () do componente ASAmoduleScript do objeto ParentAnchor.

- Para o botão chamado, excluir âncora local, crie um novo evento sob o gatilho de evento pressionado do botão, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método RemoveLocalAnchor () do componente ASAmoduleScript do objeto ParentAnchor.

### <a name="build-and-demonstrate-base-application"></a>Crie e demonstre o aplicativo base

Agora que sua cena está configurada para demonstrar os conceitos básicos das âncoras espaciais do Azure, criaremos e demonstraremos o comportamento básico das âncoras espaciais do Azure. 

1. Se você fechou a janela de Configurações de compilação das seções anteriores, abra-a novamente em Arquivo > Configurações de Compilação.
![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Verifique se a cena que você deseja tentar está nos bastidores na lista de Build clicando no botão Adicionar cenas abertas.

3. Pressione o botão Compilar para iniciar o processo de compilação.
![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome aplicativo foi criada para conter o aplicativo. Clique em Selecionar pasta para começar a criar na pasta recém-criada. Depois que a compilação for concluída, você poderá fechar a janela de configuração de compilação "no Unity. 
![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > OBSERVAÇÃO: se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro, como "Erro: CS0246 = o nome de digite ou namespace "XX" não foi encontrado (está faltando uma diretiva using ou uma referência de assembly?). Talvez seja necessário instalar o [SDK do Windows 10 (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes na solução "MixedRealityBase. sln ou no nome correspondente. Se você usou um nome alternativo para o seu projeto abrir o arquivo de solução no Visual Studio.

  > Observação: Certifique-se de abrir a pasta recém-criada (ou seja, a pasta do aplicativo, se seguir as convenções de nomenclatura das etapas anteriores, pois haverá um arquivo. sln nomeado de forma semelhante fora dessa pasta que não deve ser confundido com o arquivo. sln dentro da pasta de compilação. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> Observação: Se o Visual Studio solicitar a instalação de novos componentes, Reserve um momento para garantir que todos os componentes de pré-requisito sejam instalados como específicos na [página "instalar as ferramentas"](install-the-tools.md) 

6. Conecte o HoloLens 2 ao computador usando o cabo USB. Embora essas instruções de lição presumam que você implantará um teste com um dispositivo de HoloLens 2, você também pode optar por implantar no emulador do [hololens 2](using-the-hololens-emulator.md) ou optar por criar um [pacote de aplicativo para Sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Antes de compilar para seu dispositivo, verifique se ele está no Modo de Desenvolvedor. Se for a primeira vez que você implanta o HoloLens 2, o Visual Studio pode solicitar o emparelhamento do seu HoloLens 2 com um pin. Siga [estas instruções](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se você precisar habilitar o modo de desenvolvedor ou emparelhar com o Visual Studio.

8. Configure o Visual Studio para a criação de seu HoloLens 2 selecionando a configuração de versão, bem como a arquitetura do RM.
![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. A etapa final é criar seu dispositivo selecionando Debug > Iniciar sem depuração. Selecionar Iniciar sem depuração faz com que o aplicativo inicie imediatamente em seu dispositivo após a criação bem-sucedida de informações de depuração ithout que aparecem no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo. Você também pode selecionar compilar > implantar solução para implantar em seu dispositivo sem que o aplicativo seja iniciado automaticamente.
![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
   
10. Siga as instruções. Quando o aplicativo estiver em execução no seu dispositivo, siga as instruções na tela. Pressione os botões de cena correspondentes às etapas abaixo.

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Inicie a sessão de âncoras espaciais.
    
    2. Mova o cubo para um local diferente.
    
    3. Salve as âncoras espaciais do Azure no local do cubo.
    
    4. Pare a sessão de âncoras espaciais do Azure.
    
    5. Remova a âncora local no cubo para permitir que o usuário mova o cubo.
    
    6. Mova o cubo para outro lugar.
    
    7. Iniciar sessão de âncoras espaciais do Azure.
    
    8. Localize âncoras espaciais do Azure. 
    Você deve voltar para o local original em que o colocou quando criou a âncora.
    
    9. Excluir âncora espacial do Azure.
    
    10. Pare a sessão do Azure.

### <a name="anchoring-an-experience"></a>Ancorando uma experiência

Nas seções anteriores, você aprendeu os conceitos básicos das âncoras espaciais do Azure. Nós usamos um cubo para representar e visualizar o objeto do jogo pai com a âncora anexada. Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor. Para este exemplo, usamos o aplicativo de demonstração de assembly de módulo lunar que foi criado durante a [lição 6 do módulo base](mrlearning-base-ch6.md).

1. Pesquise o assembly do módulo lunar Complete pré-fabricado e arraste-o para sua hierarquia como um filho do AnchorParent gameobject, conforme mostrado na imagem abaixo.

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Posicione a experiência de montagem do módulo para que o cubo ainda seja exposto, conforme mostrado na imagem abaixo. No aplicativo, os usuários podem reposicionar toda a experiência movendo o cubo. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> Observação: Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de um objeto de reposicionamento (como o cubo usado nesta etapa), o uso de utensílios de posição e rotação e muito mais.

## <a name="congratulations"></a>Parabéns
Neste tutorial, você aprendeu os conceitos básicos das âncoras espaciais do Azure. Esse Esson forneceu a você vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão do Azure, criar, carregar e baixar âncoras do Azure em um único dispositivo. Na próxima lição, aprenderemos como salvar IDs de âncora do Azure em seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado. Durante a série, você aprenderá também a transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial e aprender sobre sessões compartilhadas de vários usuários, em breve como parte do tutorial de compartilhamento.

[Próxima lição: 2. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure](mrlearning-asa-ch2.md)


---
title: Módulo do ASA de aprendizado do MR âncora espacial do Azure em 2 HoloLens
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327321"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>Introdução ao Azure âncoras espaciais em HoloLens 2

Bem-vindo ao segundo módulo do Tutorial 2 HoloLens! Antes de começar, certifique-se que todos do [pré-requisitos](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) forem concluídas. Se você não tiver concluído a primeira [módulo base](mrlearning-base.md) ainda, é altamente recomendável que você conclua primeiro. Se você estiver começando um novo projeto do unity, siga as etapas de criação de projeto novo na [módulo base](mrlearning-base.md). 

## <a name="objectives"></a>Objetivos

* Conheça os conceitos básicos do desenvolvimento com âncoras espacial do Azure com o HoloLens 2

* Criar, carregar e baixar âncoras espaciais

  

## <a name="instructions"></a>Instruções

### <a name="downloading-and-importing-assets"></a>Baixar e importar os ativos
Antes de começar, você deve baixar e importar os seguintes ativos:

[Âncoras Espaciais do Azure](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Módulo Base MR pacote de ativos](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[Pacote de ativos de módulo do ASA](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Kit de ferramentas de realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> Observação: consulte a etapa 5 para obter instruções específicas sobre como importar o âncoras espacial do Azure, etapa 6 para obter instruções específicas sobre o módulo de Base MR pacote de ativos e as etapas 3 e 4 para obter instruções específicas sobre o Kit de ferramentas de realidade mista.

1. Crie uma nova cena no seu projeto. Clique com botão direito no sua pasta de cena, clique em "criar", em seguida, a cena. Nomeie a nova cena "ASALearningmodule".

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Clique duas vezes em "ASALearningmodule" para ver alguns itens predefinidos são exibidos, juntamente com a nova cena. 
3. Configure a cena para desenvolvimento de realidade misturada. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Observação: Você verá um pop-up que diz, "você deve escolher um arquivo para o Kit de ferramentas de realidade misturada." Clicar em "okey" o levará para a etapa 4.

4. Ao escolher um arquivo para o Kit de ferramentas de realidade misturada, selecionar, "DefaultMixedRealityToolkitConfigurationProfile".

   > Observação: Se você tiver sua própria configuração perfil vontade para usá-lo em vez disso.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Agora a cena é configurada para realidade misturada. Verifique se você salvar sua cena (fazer isso com qualquer um dos controles / command + S, ou clique no arquivo em seguida, clique em salva). 

5. Importar o [âncoras espaciais Azure](https://github.com/azure/azure-spatial-anchors-samples/releases). Para usar âncoras espaciais, você deve importar esse ativo. Então, clique no link acima e clique com o botão direito em "AzureSpatialAnchors.unitypackage". Clique em "Salvar destino como" e salve-o em seu computador. 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   Em seguida, depois, ele será salvo, volte para o unity, clique em "ativos" Vá para baixo até "Importar pacote", em seguida, clique em "pacote personalizado..." Arquivos de seu computador serão aberta. Uma vez que eles, encontre onde você salvou o pacote âncoras espacial do Azure e selecioná-lo. Em seguida, clique em "abrir".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   Agora haverá um pop-up oferecendo uma lista de ferramentas e configurações, solicitando que você o que importar. Selecione ***todos os*** das opções disponíveis, em seguida, clique em "importar".

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > Observação: levará alguns minutos para importar, isso, seja paciente. 

   6. Importação [pacote de ativos de módulo de Base MR](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) Avançar. Assim como a etapa 5, clique no link acima, clique com botão direito "BasemoduleAssetsV1 1.unitypackage" e clique em "Salvar destino como" e salve-o em seu computador.

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > Dica: Salve todos esses ativos na mesma pasta para que eles são mais fáceis de localizar e ter acesso ao. Isso manterá tudo organizado e interessante!

   Assim como a etapa 5, acesse novamente para o unity, clique em "ativos", passe o mouse sobre "Importar pacote", em seguida, clique em "pacote personalizado..." Portanto, arquivos de seu computador devem aparecer novamente, vá até onde você armazenou o pacote de ativos o módulo básico e selecioná-lo. Em seguida, clique em "abrir".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > Observação: pode haver mais ativos necessários neste módulo. Siga estas etapas para importar todos os ativos mencionados desse ponto em diante. 

7. Importe o módulo do ASA usando a mesma abordagem que para importar os pacotes anteriores do pacote.

### <a name="configuring-your-scene"></a>Configurando sua cena

Nesta seção, vamos adicionar scripts e pré-fabricados na cena para criar uma série de botões que demonstram os conceitos básicos de como âncoras locais e âncoras espacial do Azure se comportar em um aplicativo.

7. Na guia "projeto", abaixo da pasta "ativos", clique em "ASAmoduleAssets". Uma vez selecionada, você verá 2 pré-fabricados, "ButtonParent" e "ParentAnchor".

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. Arraste ambos os pré-fabricados na cena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. Clique duas vezes sobre a âncora de pai para selecioná-lo. Talvez você precise ajustar a exibição para ver toda a cena, então, ajuste sua cena, conforme necessário.

    Familiarize-se com ParentAnchor pré-fabricado. Atualmente, o objeto do jogo chamado "ParentAnchor" é um cubo colorido, para fins de demonstração. Por fim, vamos ocultar o cubo e colocar o nosso conteúdo como um filho de ParentAnchor. Este pré-fabricado inclui o script AzureSpatialAnchorsDemoWrapper.cs (incluído com o SDK do ASA) e o script de ASAmoduleScript.cs (incluído como parte deste módulo) para o objeto ParentAnchor. 

10. Configure os botões. Em pré-fabricado ParentAnchor, você notará vários botões rotulados. Esses botões são criados com base em prefabs do MRTK PressableButton. Saiba mais sobre como criar botões Pressable do [módulo Base](mrlearning-base-ch2.md). Para cada botão, adicione um evento que será acionado quando o usuário pressiona ou seleciona o botão de acordo com a lista a seguir. 

- Para o botão chamado "StartAzureSession", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método StartAzureSession() do componente de ASAmoduleScript ParentAnchor do objeto.

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Para o botão chamado "StopAzureSession", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método StopAzureSession() do componente de ASAmoduleScript ParentAnchor do objeto.

- Para o botão chamado "CreateAnchor", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método CreateAzureAnchor() do componente de ASAmoduleScript ParentAnchor do objeto.

- Para o botão chamado "Iniciar procurando para âncora", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método FindAzureAnchor() do componente de ASAmoduleScript ParentAnchor do objeto.

- Para o botão chamado "DeleteAzureAnchor", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método DeleteAzureAnchor() do componente de ASAmoduleScript ParentAnchor do objeto.

- Para o botão chamado "Excluir âncora Local", crie um novo evento sob o gatilho de evento "Pressionado", bem como o disparador de eventos "No clique". Arraste o objeto ParentAnchor para o campo vazio e atribuir o método RemoveLocalAnchor() do componente de ASAmoduleScript ParentAnchor do objeto.

### <a name="build-and-demonstrate-base-application"></a>Criar e demonstrar aplicativos básico

Agora que sua cena está configurada para demonstrar os conceitos básicos das âncoras espacial do Azure, vamos compilar e demonstrar o comportamento básico de âncoras espacial do Azure. 

1. Se você fechou a janela de Configurações de compilação das seções anteriores, abra-a novamente em Arquivo > Configurações de Compilação.
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Verifique se a cena que você deseja experimentar está na lista de "Cenas em Compilação", clicando no botão "Adicionar Cenas Abertas".

3. Pressione o botão Compilar para iniciar o processo de compilação.
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome "Aplicativo" foi criada para armazenar o aplicativo. Clique em "Selecionar Pasta" para começar a compilar na pasta recém-criada. Após a compilação, você pode fechar a janela "Configurações de Compilação" no Unity. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > OBSERVAÇÃO: se a compilação falhar, tente compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro, como "Erro: Erro CS0246 = o nome do namespace ou digite "XX" não pôde ser encontrado (está faltando um usando diretiva ou uma referência de assembly?) ", em seguida, você talvez precise instalar [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes na solução "MixedRealityBase.sln" (ou no nome correspondente, se você usou um nome alternativo para o seu projeto) para abrir o arquivo de solução no Visual Studio.

  > Observação: certifique-se de abrir a pasta recém-criada (ou seja, "Aplicativo", se estiver seguindo as convenções de nomenclatura das etapas anteriores), pois haverá um arquivo .sln com nome semelhante fora dessa pasta que não deve ser confundido com o arquivo .sln dentro da pasta de compilação. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > Observação: Se o visual studio pede para instalar novos componentes, reserve um momento para garantir que todos os componentes de pré-requisito estão instalados tão específico no [a página de "Instalar as ferramentas"](install-the-tools.md) 

6. Conecte o HoloLens 2 ao computador usando o cabo USB. Enquanto essas instruções de lição pressupõem que você estiver implantando um teste com um dispositivo de 2 HoloLens, você também pode optar por implantar o [HoloLens 2 emulador](using-the-hololens-emulator.md) ou optar por criar um [pacote do aplicativo para o sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Antes de compilar para seu dispositivo, verifique se ele está no Modo de Desenvolvedor. Se for a primeira vez que você implanta o HoloLens 2, o Visual Studio pode solicitar o emparelhamento do seu HoloLens 2 com um pin. Siga [estas instruções](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) se você precisar ativar o modo de desenvolvedor ou emparelhar com o Visual Studio.

8. Configure o Visual Studio para compilar seu HoloLens 2, selecionando a configuração "Versão" e a arquitetura "ARM".
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
    
9. A etapa final é criar ao seu dispositivo, selecionando Depurar > Iniciar sem depuração. Selecionar "Iniciar sem Depuração" fará com que o aplicativo inicie imediatamente em seu dispositivo após uma compilação bem-sucedida, mas sem exibir informações de Depuração no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo. Você também pode selecionar Compilação > Implantar Solução para implantar seu dispositivo sem iniciar o aplicativo automaticamente.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. Quando o aplicativo está em execução em seu dispositivo, siga na tela instruções. Pressione os botões de cena correspondente com as etapas abaixo.
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Inicie a sessão do Azure âncoras espacial.
    
    2. Mova o cubo para um local diferente.
    
    3. Salve as âncoras espaciais do Azure no local do cubo.
    
    4. Interrompa a sessão do Azure âncoras espacial.
    
    5. Remova a âncora local ao cubo para permitir que o usuário mover o cubo.
    6. Mova o cubo em outro lugar.
    
    7. Inicie sessão âncoras espacial do Azure.
    
    8. Encontre âncoras espaciais do Azure.
    (agora o cubo deve voltar para o local original você colocá-lo quando você criou a âncora).
    9. Exclua âncora espacial do Azure.
    
    10. Pare a sessão do Azure.

### <a name="anchoring-an-experience"></a>Ancoragem de uma experiência

Nas seções anteriores, você aprendeu os conceitos básicos das âncoras espacial do Azure. Usamos um cubo para representar e visualizar o objeto pai do jogo com a âncora anexado. Nesta seção, você wiill Saiba como toda a experiência de ancoragem, colocando-o como um filho do objeto ParentAnchor. Neste exemplo, usaremos o aplicativo de demonstração do Assembly de módulo Lunar que foi criado durante [módulo Base lição 6](mrlearning-base-ch6.md).

1. Pesquisar pré-fabricado Lunar módulo Assembly completo e arraste-o para sua hierarquia como um filho do gameobject AnchorParent, conforme mostrado na imagem abaixo.

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Posicione a experiência de assembly do módulo de tal forma que o cubo ainda é exposto, conforme mostrado na imagem abaixo. No aplicativo, os usuários podem reposicionar toda a experiência, movendo o cubo. 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > Observação: Há uma variedade de fluxos de experiência do usuário para reposicionamento experiências, incluindo o uso de um botão para alternar uma caixa delimitadora que circunda a experiência, o uso de um objeto repositioning (como o cubo usado nesta etapa), o uso de utensílios de posição e rotação e muito mais.

## <a name="congratulations"></a>Parabéns
Nesta lição, você aprendeu os conceitos básicos das âncoras espacial do Azure. Nesta lição você fornecido com vários botões, permitindo que você explore as várias etapas necessárias para iniciar e parar uma sessão do Azure e criar, carregar e baixar as âncoras do azure em um único dispositivo. Na próxima lição, aprenderemos como salvar as IDs de âncora do Azure em sua 2 HoloLens para recuperação, mesmo depois que o aplicativo for reiniciado. Durante a série, você também aprenderá a transferência de IDs de âncora entre vários dispositivos para obter o alinhamento espacial e, eventualmente, saiba mais sobre multiusuário compartilhado sessões (em breve como parte do módulo de compartilhamento).

[Próxima lição: Lição 2 para ASA](mrlearning-asa-ch2.md)


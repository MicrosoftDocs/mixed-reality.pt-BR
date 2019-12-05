---
title: Tutoriais de âncoras espaciais do Azure-1. Introdução às âncoras espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: b615f1135f5d2947f8f718e080ef45a3c1fcc576
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830844"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introdução às âncoras espaciais do Azure

Bem-vindo ao segundo módulo dos tutoriais do HoloLens 2. Antes de começar, certifique-se de que todos os [pré-requisitos](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) estejam concluídos. Se você ainda não concluiu o primeiro [módulo base](mrlearning-base.md) , é recomendável que você conclua o módulo primeiro. Se você estiver iniciando em um novo projeto do Unity, siga as etapas de criação do novo projeto no [módulo base](mrlearning-base.md). 

## <a name="objectives"></a>Objetivos

* Conheça os conceitos básicos do desenvolvimento com âncoras espaciais do Azure com o HoloLens 2

* Criar, carregar e baixar âncoras espaciais

## <a name="instructions"></a>Instruções

### <a name="downloading-and-importing-assets"></a>Baixando e importando ativos
Antes de começar, baixe e importe os seguintes ativos:

[Âncoras espaciais do Azure v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[Unity. HoloLens2. GettingStarted. tutoriais. Asset. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[Unity. HoloLens2. AzureSpatialAnchor. tutoriais. Asset. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[2.1.0 do pacote do kit de ferramentas de realidade misto](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. Crie uma nova cena em seu projeto. Clique com o botão direito do mouse na sua pasta de cena, clique em criar e em cena. Nomeie a nova cena como "ASALearningModule".

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Clique duas vezes em cena "ASALearningmodule" para ver alguns itens predefinidos a serem exibidos junto com a nova cena. 
3. Configure a cena para o desenvolvimento de realidade misturada. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Observação: você pode ver uma caixa de diálogo pop-up para selecionar um [perfil para o kit de ferramentas de realidade misturada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Escolha o perfil chamado *DefaultHoloLens2ConfigurationProfile* clicando duas vezes nele.

4. Ao escolher um arquivo para o MRTK, selecione DefaultMixedRealityToolkitConfigurationProfile.

> Observação: se você tiver seu próprio perfil de configuração, fique à vontade para usá-lo.
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

A cena agora está configurada para realidade misturada. Certifique-se de salvar sua cena (faça isso com controle/comando + S ou clique em arquivo, seguido por salvar). 

5. Importe o pacote da Unity das [âncoras espaciais do Azure v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) que baixamos na etapa 1. Para isso, clique em ativos, vá para baixo para importar pacote e, em seguida, clique em pacote personalizado... Os arquivos do computador serão abertos. Ao fazer isso, localize onde você salvou o pacote de âncoras espaciais do Azure e selecione-o. Em seguida, clique em abrir.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

Um pop-up é exibido, fornecendo uma lista de ferramentas e configurações e perguntando o que importar. Selecione ***todas*** as opções disponíveis e clique em importar.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> Observação: seja paciente, levará alguns minutos para ser importado. 

6. Importe [Unity. HoloLens2. gettingstarted. tutoriais. Asset. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) avançar. De forma semelhante à etapa 5, volte para o Unity, clique em ativos e passe o mouse sobre o pacote de importação. Clique em pacote personalizado... Os arquivos do computador serão exibidos novamente. Vá para onde você armazenou o pacote de ativos do módulo base. e selecione-o. Clique em Abrir.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> Observação: pode haver mais ativos necessários posteriormente neste módulo. Siga estas etapas para importar todos os ativos mencionados neste ponto em diante. 

7. Importe o [pacote de módulo asa 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage), usando as mesmas etapas de importação dos pacotes anteriores.

### <a name="configuring-your-scene"></a>Configurando sua cena

Nesta seção, adicionaremos pré-fabricados e scripts à cena para criar uma série de botões que demonstram os conceitos básicos de como as âncoras locais e as âncoras espaciais do Azure se comportam em um aplicativo.

8. Na guia projeto, abaixo da pasta ativos, clique em ASAmoduleAssets. Depois de selecionado, você verá dois pré-fabricados: ButtonParent e ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. Arraste ambos os pré-fabricados para a cena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

Observação: depois de adicionar o ButtonParent à cena, um pop-up será exibido solicitando que você importe os ativos TMP. Importe o "TMP Essentials". Depois disso, se você vir qualquer texto de fonte grande na cena, exclua o objeto ButtonParent e adicione-o novamente da pasta ASAmoduleAssets.

Observação: se você quiser verificar os logs de depuração no HoloLens, poderá arrastar e soltar o DebugWindow pré-fabricado da pasta ASAModuleAssets para a cena. Anexe o script DebugWindowMessaging no painel Inspetor de DebugWindow e habilite a opção janela de depuração habilitada. Depois disso, arraste e solte o DebugWindow pré-fabricado no campo DebugText vazio. Você também pode ajustar a posição DebugWindow sempre que for apropriado para você.

10. Para ampliar a cena, clique duas vezes na âncora pai na hierarquia e ajuste sua exibição para ver toda a cena, conforme necessário. Atualmente, ParentAnchor é um cubo colorido usado apenas para fins de demonstração. Por fim, ocultaremos o cubo e colocaremos nosso conteúdo como um filho do ParentAnchor. 

11. Agora, vamos configurar os botões para operar a cena. Para isso, expanda o ButtonParent pré-fabricado e você observará vários botões rotulados, que são criados a partir do PressableButton pré-fabricados do MRTK. Saiba mais sobre como criar PressableButton a partir do [módulo base](mrlearning-base-ch2.md). Para que esses botões funcionem, você precisa adicionar um evento que será disparado quando o usuário pressionar ou selecionar os botões individuais. 

- Para o botão chamado StartAzureSession, crie um novo evento no gatilho de evento pressionado por botão, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método StartAzureSession () do componente ASAmoduleScript do objeto ParentAnchor, conforme mostrado na captura de tela abaixo.
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Para o botão chamado StopAzureSession, crie um novo evento no gatilho de evento pressionado por botão, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método StopAzureSession () do componente ASAmoduleScript do objeto ParentAnchor.

- Para o botão chamado createanchor, crie um novo evento no gatilho de evento pressionado por botão, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método CreateAzureAnchor () do componente ASAmoduleScript do objeto ParentAnchor.  **Depois disso, arraste o ParentAnchor novamente para o próximo campo "objeto de jogo" vazio.**

- Para o botão chamado start procurando ancoragem, crie um novo evento sob o botão pressione "gatilho de evento, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método FindAzureAnchor () do componente ASAmoduleScript do objeto ParentAnchor.

- Para o botão chamado DeleteAzureAnchor, crie um novo evento no gatilho de evento pressionado por botão, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método DeleteAzureAnchor () do componente ASAmoduleScript do objeto ParentAnchor.  

- Para o botão chamado excluir âncora local, crie um novo evento sob o gatilho de evento pressionado do botão, bem como o gatilho de evento on Click. Arraste o objeto ParentAnchor para o campo vazio e atribua o método RemoveLocalAnchor () do componente ASAmoduleScript do objeto ParentAnchor. **Depois disso, arraste o objeto ParentAnchor novamente para o próximo campo "objeto de jogo" vazio.**

12. Para configurar as âncoras espaciais do Azure, vá para a pasta AzureSpatialAnchorsPlugin na pasta ativos e navegue até exemplos – > recursos-> arquivo AzureSpatialAnchorsDemoConfig. No painel Inspetor, adicione a ID da conta do Azure e a chave de conta que você criou anteriormente. Se você não os criou ou não os tiver, siga os [pré-requisitos](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens). 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a>Crie e demonstre o aplicativo base

Agora que sua cena está configurada para demonstrar os conceitos básicos das âncoras espaciais do Azure, criaremos e demonstraremos o comportamento básico das âncoras espaciais do Azure. 

1. Abra a janela configurações de compilação novamente, acessando arquivo > configurações de compilação.
    ![mrlearning-asa-CH1-3-etapa 1](images/mrlearning-asa-ch1-3-step1.jpg)
2. Verifique se a cena que você deseja experimentar está nos bastidores na lista de Build clicando no botão Adicionar cenas abertas.
3. Verifique se a plataforma está definida para a Plataforma Universal do Windows. Caso contrário, defina-o como o mesmo.
4. Pressione o botão Configurações do Player e vá para publicando configurações. Em recursos, habilite: Internet, servidor de cliente de Internet, servidor cliente de rede privada, armazenamento removível, webcam, microfone e percepção espacial.
5. Nas mesmas configurações do Player, vá para configurações de XR e selecione a realidade virtual com suporte para ativado.
6. Pressione o botão Compilar para iniciar o processo de compilação.
   ![mrlearning-asa-CH1-3-etapa 6](images/mrlearning-asa-ch1-3-step6.jpg)
7. Crie e dê um nome para uma nova pasta para o seu aplicativo. Na imagem abaixo, uma pasta com o nome aplicativo foi criada para conter o aplicativo. Clique em Selecionar pasta para começar a criar na pasta recém-criada. Depois que a compilação for concluída, você poderá fechar a janela de configuração de compilação "no Unity.

    ![mrlearning-asa-CH1-3-Step7](images/mrlearning-asa-ch1-3-step7.jpg)

    > Observação: se a compilação falhar, tente Compilar novamente ou reiniciar o Unity e compilar novamente. Se você vir um erro como "erro: CS0246 = o tipo ou nome do namespace" XX "não pôde ser encontrado (está faltando uma diretiva using ou uma referência de assembly?), talvez seja necessário instalar o [SDK do Windows 10 (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) 


8. Mesmo após uma compilação bem-sucedida, você pode receber alguns erros, conforme mostrado abaixo, mas se a compilação for bem-sucedida, você poderá ignorá-las e prosseguir com as próximas etapas.

    ![mrlearning-asa-CH1-3-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. Depois que a compilação for concluída, abra a pasta recém-criada que contém os arquivos do novo aplicativo. Clique duas vezes na solução "MixedRealityBase. sln" ou no nome correspondente, se você usou um nome alternativo para o seu projeto abrir o arquivo de solução no Visual Studio.

    > Observação: não se esqueça de abrir a pasta recém-criada (ou seja, a pasta do aplicativo, se seguir as convenções de nomenclatura das etapas anteriores, pois haverá um arquivo. sln nomeado de forma semelhante fora dessa pasta que não deve ser confundido com o arquivo. sln dentro da pasta de compilação.

    ![mrlearning-asa-CH1-3-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > Observação: se o Visual Studio solicitar a instalação de novos componentes, verifique se todos os componentes de pré-requisito estão instalados como específicos na [página "instalar as ferramentas"](install-the-tools.md)


9. Conecte o HoloLens 2 ao computador usando o cabo USB. Embora essas instruções de lição presumam que você implantará um teste com um dispositivo de HoloLens 2, você também pode optar por implantar no [emulador do hololens 2](using-the-hololens-emulator.md) ou optar por criar um [pacote de aplicativo para Sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

10. Antes de criar seu dispositivo, verifique se ele está no modo de desenvolvedor. Se esta for a primeira vez que você está implantando no HoloLens 2, o Visual Studio pode solicitar que você emparelhe o seu HoloLens 2 com um PIN. Siga [estas instruções](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) se você precisar habilitar o modo de desenvolvedor ou emparelhar com o Visual Studio.

11. Configure o Visual Studio para a criação de seu HoloLens 2, selecionando a configuração de versão, bem como a arquitetura ARM.

    ![mrlearning-asa-CH1-3-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. A etapa final é compilar para seu dispositivo, selecionando Depurar > Iniciar sem Depuração. Selecionar Iniciar sem depuração faz com que o aplicativo inicie imediatamente em seu dispositivo após uma compilação bem-sucedida sem que as informações de depuração apareçam no Visual Studio. Isso também significa que você pode desconectar o cabo USB enquanto o aplicativo estiver em execução no HoloLens 2 sem interromper o aplicativo. Você também pode selecionar compilar > implantar solução para implantar em seu dispositivo sem que o aplicativo seja iniciado automaticamente.

    ![mrlearning-asa-CH1-3-step12](images/mrlearning-asa-ch1-3-step12.jpg)

>Observação: as âncoras espaciais do Azure usam a Internet para salvar e carregar os dados de âncora, portanto, verifique se o dispositivo está conectado à Internet antes de testar o aplicativo ASA.

13. Siga as instruções. 
    Quando o aplicativo estiver em execução no seu dispositivo, siga as instruções na tela. Pressione os botões de cena correspondentes às etapas abaixo. Se você adicionou a janela de depuração conforme mencionado nas etapas anteriores, poderá ver os comentários para a prensa de botão individual e o progresso de operações individuais relacionadas às âncoras espaciais do Azure.

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

1. Pesquise o pré-fabricado "Rocket Launcher completo" e arraste-o para sua hierarquia como um filho do objeto (consulte a imagem abaixo).

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Posicione a experiência de montagem do módulo para que o cubo ainda seja exposto, conforme mostrado na imagem abaixo. No aplicativo, os usuários podem reposicionar toda a experiência movendo o cubo. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> Observação: há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de um objeto de reposicionamento (como o cubo usado nesta etapa), o uso de posição e rotação utensílios e muito mais.

## <a name="congratulations"></a>Parabéns
Neste tutorial, você aprendeu os conceitos básicos das âncoras espaciais do Azure. Esta lição forneceu a você vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão do Azure e criar, carregar e baixar âncoras do Azure em um único dispositivo. Na próxima lição, você aprenderá a salvar as IDs de âncora do Azure em seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado. Durante a série, você aprenderá também a transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial e aprender sobre sessões compartilhadas de vários usuários, em breve como parte do tutorial de compartilhamento.

[Próxima lição: 2. salvando, recuperando e compartilhando âncoras espaciais do Azure](mrlearning-asa-ch2.md)


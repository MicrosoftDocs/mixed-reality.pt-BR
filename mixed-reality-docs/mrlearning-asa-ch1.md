---
title: Tutoriais de âncoras espaciais do Azure-1. Introdução às âncoras espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940894"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introdução às âncoras espaciais do Azure

## <a name="overview"></a>Visão geral

Bem-vindo à segunda série dos tutoriais do HoloLens 2. Nesta série de tutoriais de três partes, você aprenderá os conceitos básicos das âncoras espaciais do Azure.

Neste primeiro tutorial, [introdução às âncoras espaciais do Azure](mrlearning-asa-ch1.md), você irá explorar as várias etapas necessárias para iniciar e parar uma sessão do Azure e criar, carregar e baixar âncoras do Azure em um único dispositivo.

No segundo tutorial, [salvando, recuperando e compartilhando âncoras espaciais do Azure](mrlearning-asa-ch2.md), você aprenderá como salvar âncoras espaciais do Azure em várias sessões de aplicativo salvando informações de âncora no armazenamento do HoloLens 2 e como compartilhar essas informações de âncora para outros dispositivos para um alinhamento de âncora de vários dispositivos.

No terceiro tutorial, [exibindo comentários de âncora espacial do Azure](mrlearning-asa-ch3.md), você aprenderá a fornecer aos usuários comentários sobre eventos de âncora e status ao usar âncoras espaciais do Azure.

## <a name="objectives"></a>Objetivos

* Conheça os conceitos básicos do desenvolvimento com âncoras espaciais do Azure para o HoloLens 2
* Criar, carregar e baixar âncoras espaciais

## <a name="prerequisites"></a>Pré-requisitos

* Atenda aos requisitos listados na seção [pré-requisitos](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) do tutorial [: criar um aplicativo de HoloLens do Unity que usa âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .
* Conclua a seção [criar um recurso de âncoras espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [início rápido: criar um aplicativo de HoloLens do Unity que usa âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .
* Se você ainda não concluiu a série de [tutoriais de introdução](mrlearning-base.md) , é recomendável que você conclua esses tutoriais primeiro.

## <a name="creating-the-unity-project"></a>Criando o projeto do Unity

Nesta seção, você criará um novo projeto do Unity e o configurará para a realidade mista do Windows.

1. Crie um projeto do Unity e dê a ele um nome adequado, por exemplo, _tutorial de âncoras espaciais do Azure_.

2. Configure o projeto do Unity para a realidade mista do Windows.

    >[!TIP]
    >Para um lembrete sobre como criar um projeto do Unity e configurá-lo para a realidade mista do Windows, você pode consultar as seções [criar novo projeto](mrlearning-base-ch1.md#create-new-unity-project) do Unity e [Configurar o projeto do Unity para a realidade mista do Windows](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) do tutorial [inicializando seu projeto e primeiro aplicativo](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) que faz parte da série de [tutoriais de introdução](mrlearning-base.md) .

## <a name="adding-inbuilt-unity-packages"></a>Adicionando pacotes de Unity embutidos

Nesta seção, você adicionará ativos e pacotes de Unity embutidos exigidos pelos kits de recursos e SDKs que você usará no projeto.

1. Importar recursos essenciais do TMP.

    >[!NOTE]
    >Estamos adicionando este pacote porque ele é exigido pelo kit de ferramentas da realidade misturada.

    No menu do Unity, selecione **janela** > **TextMeshPro** > **importar recursos essenciais do tmp**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    Na janela pop-up importar pacote do Unity, primeiro verifique se todos os ativos estão selecionados clicando no botão **tudo** e, em seguida, importe os ativos clicando no botão **importar** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. Instale o AR Foundation.

    >[!NOTE]
    >Estamos adicionando este pacote porque ele é exigido pelo SDK de âncoras espaciais do Azure.

    No menu do Unity, selecione **janela** > **Gerenciador de pacotes**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    Na janela Gerenciador de pacotes, selecione **ar Foundation** e instale o pacote clicando no botão **instalar** .

    >[!IMPORTANT]
    >Pode levar alguns segundos até que o pacote do AR Foundation seja exibido na lista.

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a>Importando os ativos do tutorial

Nesta seção, você baixará e importará todos os ativos do tutorial.

1. Baixe os ativos.

    * [AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versão 2.0.0)
    * [Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [MRTK. HoloLens2. Unity. tutoriais. assets. GettingStarted. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [MRTK. HoloLens2. Unity. tutoriais. assets. AzureSpatialAnchors. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. Importe os ativos.

    No menu do Unity, selecione **ativos** > **Importar pacote** > **pacote personalizado...** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    No pacote de importação... janela pop-up, selecione **AzureSpatialAnchors. unitypackage** e clique no botão **abrir** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    Na janela pop-up importar pacote do Unity, primeiro verifique se todos os ativos estão selecionados clicando no botão **tudo** e, em seguida, importe os ativos clicando no botão **importar** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    Repita essas etapas para importar os pacotes de ativos restantes. Depois de concluído, a pasta de **ativos** do seu projeto de Unity deve conter essas subpastas.

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a>Criando e preparando a cena

Nesta seção, você criará e preparará a cena adicionando o kit de ferramentas de realidade misturada e algumas das pré-fabricados do tutorial.

1. Crie uma nova cena.

    No menu do Unity, selecione **arquivo** > **nova cena**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    No menu do Unity, selecione **arquivo** > **salvar como...** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    Na janela pop-up salvar cena, navegue até a pasta de **cenas** do projeto, dê um nome adequado à sua cena, por exemplo, _ASATutorialScene_, e salve a cena clicando no botão **salvar** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    >Você pode salvar a cena em qualquer lugar em que desejar, desde que ela esteja dentro da pasta de ativos do projeto. No entanto, para manter seu projeto organizado, é geralmente recomendável salvá-lo na pasta de cenas do projeto.

2. Adicione o kit de ferramentas de realidade misturada.

    No menu do Unity, selecione o **Kit de ferramentas de realidade misturada** > **Adicionar à cena e configurar...** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    Na janela pop-up selecionar MixedRealityToolkitConfigurationProfile, clique no **DefaultHoloLens2ConfigurationProfile** para defini-lo como o perfil de configuração de MRTK da cena.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    No menu do Unity, selecione **arquivo** > **salvar** para salvar a cena.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    >Você pode usar o atalho de teclado CTRL + S (comando + S no macOS) para salvar rapidamente sua cena enquanto estiver trabalhando neste tutorial.

3. Adicione o tutorial pré-fabricados.

    No painel projeto, navegue até **ativos** > **MRTK. Tutoriais. AzureSpatialAnchors** > pasta **pré-fabricados** Enquanto pressiona o botão CTRL (comando no macOS), clique em **ButtonParent**, **DebugWindow**e **ParentAnchor** para selecionar os três pré-fabricados.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    Com os três pré-fabricados ainda selecionados, arraste-os para o painel hierarquia para adicioná-los à cena.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    Para se concentrar nos objetos da cena, você pode clicar duas vezes no objeto ParentAnchor e, em seguida, aplicar um pouco mais zoom novamente.

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    >Se você encontrar os ícones grandes em sua cena, por exemplo, os ícones grandes, você poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o utensílios</a> para a posição desligado.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurando os botões para operar a cena

Nesta seção, você adicionará pré-fabricados e scripts à cena para criar uma série de botões que demonstram os conceitos básicos de como as âncoras locais e as âncoras espaciais do Azure se comportam em um aplicativo.

1. Configure o componente de botão pressionável holo Lens 2 (script).

    No painel hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    No painel Inspetor, role para baixo até o componente de **botão pressionável holo lente 2 (script)** e adicione um novo ouvinte de eventos ao evento **botão pressionado ()** clicando no ícone de **+** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    Com o objeto StartAzureSession ainda selecionado no painel hierarquia, clique e arraste o objeto **ParentAnchor** do painel hierarquia para o campo **nenhum (objeto)** vazio do ouvinte de eventos que você acabou de adicionar para fazer com que o objeto ParentAnchor escute eventos pressionados desse botão.

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    Clique no menu suspenso **sem função** do mesmo ouvinte de evento e selecione **AnchorModuleScript** > **StartAzureSession ()** para definir a função StartAzureSession () como a ação disparada quando os eventos pressionados pelo botão são acionados desse botão.

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. Configure o componente de interação (script).

    Com o objeto StartAzureSession ainda selecionado no painel hierarquia, no painel Inspetor, role para baixo até o componente **interagir (script)** e repita o mesmo processo como na etapa 1 acima para o evento **OnClick ()** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. Configurar os botões restantes

    Para cada um dos botões restantes, conclua o processo descrito na etapa 1 e 2 acima para atribuir funções a ambos os eventos de botão pressionado () e OnClick () a seguir:

    * Para o objeto **StopAzureSession** , atribua a função **StopAzureSession ()** .
    * Para o objeto **createanchor** , atribua a função **CreateAzureAnchor ()** e, em seguida, arraste o **ParentAnchor** novamente para o campo **nenhum (objeto de jogo)** vazio.
    * Para o objeto **começar a procurar âncora** , atribua a função **FindAzureAnchor ()** .
    * Para o objeto **excluir âncora do Azure** , atribua a função **DeleteAzureAnchor ()** .
    * Para o objeto **excluir âncora local** , atribua a função **RemoveLocalAnchor ()** e, em seguida, arraste o **ParentAnchor** novamente para o campo **nenhum (objeto de jogo)** vazio.

4. Conectar a cena ao recurso do Azure

    No painel hierarquia, selecione o objeto **ParentAnchor** e, no painel Inspetor, role para baixo até o componente **Gerenciador de âncora espacial (script)** .

    Em seguida, na seção **credenciais** , Cole a ID da conta de âncoras espaciais e a chave nos campos ID da conta das **âncoras espaciais** e **âncoras** espaciais correspondentes.

    >[!NOTE]
    >Você criou sua ID e chave de conta de âncoras espaciais como parte dos [pré-requisitos](mrlearning-asa-ch1.md#prerequisites)deste tutorial.

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    >Certifique-se de salvar sua cena.

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Experimentando os comportamentos básicos das âncoras espaciais do Azure

Agora que sua cena está configurada para demonstrar os conceitos básicos das âncoras espaciais do Azure, é hora de implantar o aplicativo para que você possa experimentar as âncoras espaciais do Azure em primeira mão.

1. Adicione recursos adicionais necessários.

    No menu do Unity, selecione **editar** > **configurações do projeto...** para abrir o painel configurações do Player.

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    No painel configurações do Player, selecione **Player** e, em seguida, **Publicar configurações**.

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    Nas **configurações de publicação**, role para baixo até a seção **recursos** e verifique se o **SpatialPerception**, que você habilitou quando criou o projeto no início do tutorial, está habilitado. Em seguida, habilitou os recursos **internetclient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **webcam**e **Microphone** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. Implante o aplicativo no seu HoloLens 2.

    >[!TIP]
    >Para obter um lembrete sobre como criar e implantar seu projeto do Unity no HoloLens 2, você pode consultar as seções [criar seu aplicativo em seu dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) do tutorial [inicializando seu projeto e primeiro aplicativo](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , que faz parte da série de [tutoriais de introdução](mrlearning-base.md) .

3. Execute o aplicativo e siga as instruções no aplicativo.

    >[!CAUTION]
    >As âncoras espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.

    Quando o aplicativo estiver em execução no seu dispositivo, siga as instruções na tela exibidas no painel de **instruções do módulo âncora espacial do Azure** .

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a>Ancorando uma experiência

Nas seções anteriores, você aprendeu os conceitos básicos das âncoras espaciais do Azure. Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada. Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.

1. Adicione a experiência do Rocket Launcher.

    No painel projeto, navegue até **ativos** > **MRTK. Tutoriais. GettingStarted** > pasta **pré-fabricados** e selecione o **Rocket Launcher_Complete** pré-fabricado.

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    Com o Rocket Launcher_Complete pré-fabricado ainda selecionado, arraste-o sobre o objeto **ParentAnchor** no painel hierarquia para torná-lo um filho do objeto ParentAnchor.

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. Reposicione a experiência do Rocket Launcher.

    Mova o objeto de Launcher_Complete do módulo **Rocket** para que o **ParentAnchor** (o cubo) ainda seja exposto.

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    No aplicativo, os usuários agora podem reposicionar toda a experiência do Rocket Launcher movendo o cubo.

    >[!TIP]
    >Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de posição e rotação utensílios e muito mais.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu os conceitos básicos das âncoras espaciais do Azure. Esta lição forneceu a você vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão do Azure e criar, carregar e baixar âncoras do Azure em um único dispositivo.

Na próxima lição, você aprenderá a salvar as IDs de âncora do Azure em seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado e como transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.

[Próxima lição: 2. salvando, recuperando e compartilhando âncoras espaciais do Azure](mrlearning-asa-ch2.md)

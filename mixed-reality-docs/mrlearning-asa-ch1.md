---
title: Tutoriais de âncoras espaciais do Azure-1. Introdução às âncoras espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 0163b61bfbf8bd583532092581d94f63e1c2a624
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554594"
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

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

>[!TIP]
>Se você ainda não concluiu a série de [tutoriais de introdução](mrlearning-base.md) , é recomendável que você conclua esses tutoriais primeiro.

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado
* Conclua a seção [criar um recurso de âncoras espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [início rápido: criar um aplicativo de HoloLens do Unity que usa âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .

> [!IMPORTANT]
> A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.

## <a name="creating-the-unity-project"></a>Criando o projeto do Unity
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

Nesta seção, você criará um novo projeto do Unity e o tornará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga a [inicialização do projeto e do primeiro aplicativo](mrlearning-base-ch1.md), excluindo as instruções [criar seu aplicativo para o dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) , que inclui as seguintes etapas:

1. [Crie um novo projeto do Unity](mrlearning-base-ch1.md#create-new-unity-project) e dê a ele um nome adequado, por exemplo, *tutoriais do MRTK*.

2. [Configurar o projeto do Unity para a realidade mista do Windows](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importar recursos do textmesh pro Essentials](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importar o kit de ferramentas de realidade misturada](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configurar o projeto do Unity para o kit de ferramentas da realidade misturada](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Adicione o kit de ferramentas da realidade misturada à cena do Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e dê um nome adequado à cena, por exemplo, *AzureSpatialAnchors*

Em seguida, siga as instruções sobre [como configurar os perfis do kit de ferramentas de realidade misturada (opção alterar exibição de conscientização espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição para a malha de conscientização espacial para **oclusão**.

> [!CAUTION]
> Conforme mencionado no [projeto configurar o Unity para as instruções do kit de ferramentas da realidade misturada](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) vinculadas acima, é altamente recomendável não habilitar o MSBuild para o Unity.

## <a name="adding-inbuilt-unity-packages"></a>Adicionando pacotes de Unity embutidos
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

Nesta seção, você instalará o pacote do AR Foundation embutido do Unity porque ele é exigido pelo SDK de âncoras espaciais do Azure que será importado na próxima seção.

No menu do Unity, selecione **janela** > **Gerenciador de pacotes**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Pode levar alguns segundos até que o pacote do AR Foundation seja exibido na lista.

Na janela Gerenciador de pacotes, selecione **ar Foundation** e instale o pacote clicando no botão **instalar** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importando os ativos do tutorial

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versão 2.1.1)
* [MRTK. HoloLens2. Unity. tutoriais. assets. GettingStarted. 2.3.0.2. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [MRTK. HoloLens2. Unity. tutoriais. assets. AzureSpatialAnchors. 2.3.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções de [importação do kit de ferramentas da realidade misturada](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Criando e preparando a cena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

Nesta seção, você irá preparar a cena adicionando algumas das pré-fabricados do tutorial.

Na janela do projeto, navegue até **ativos** > **MRTK. Tutoriais. AzureSpatialAnchors** > pasta **pré-fabricados** Ao manter pressionado o botão CTRL, clique em **ButtonParent**, **DebugWindow**, **instruções**e **ParentAnchor** para selecionar os quatro pré-fabricados:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Com os quatro pré-fabricados ainda selecionados, arraste-os para a janela hierarquia para adicioná-los à cena:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Para se concentrar nos objetos da cena, você pode clicar duas vezes no objeto ParentAnchor e, em seguida, aumentar o zoom novamente:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Se você encontrar os ícones grandes em sua cena, por exemplo, os ícones grandes, você poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o utensílios</a> para a posição desligado.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configurando os botões para operar a cena

Nesta seção, você adicionará scripts à cena para criar uma série de eventos de botão que demonstram os conceitos básicos de como as âncoras locais e as âncoras espaciais do Azure se comportam em um aplicativo.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. configurar o componente de botão pressionável holo Lens 2 (script)

Na janela hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

Na janela Inspetor, localize o componente de **botão pressionável do holo Lens 2 (script)** e adicione um novo ouvinte de eventos ao evento **botão pressionado ()** clicando no ícone de **+** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Com o objeto StartAzureSession ainda selecionado na janela hierarquia, clique e arraste o objeto **ParentAnchor** da janela hierarquia para o campo **nenhum (objeto)** vazio do ouvinte de eventos que você acabou de adicionar para fazer com que o objeto ParentAnchor escute eventos pressionados desse botão:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Clique no menu suspenso **sem função** do mesmo ouvinte de evento e selecione **AnchorModuleScript** > **StartAzureSession ()** para definir a função StartAzureSession () como a ação disparada quando os eventos pressionados pelo botão são acionados deste botão:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. configurar o componente de interação (script)

Com o objeto StartAzureSession ainda selecionado na janela hierarquia, na janela Inspetor, localize o componente **interajaável (script)** e repita o mesmo processo que na etapa 1 acima para o evento **OnClick ()** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. configurar os botões restantes

Para cada um dos botões restantes, conclua o processo descrito na etapa 1 e 2 acima para atribuir funções a ambos os eventos de **botão pressionado ()** e **OnClick ()** :

* Para o objeto **StopAzureSession** , atribua a função AnchorModuleScript > **StopAzureSession ()** .
* Para o objeto **CreateAzureAnchor** , atribua a função AnchorModuleScript > **CreateAzureAnchor ()** ,
  * em seguida, arraste o **ParentAnchor** novamente para o campo **nenhum (objeto de jogo)** vazio.
* Para o objeto **RemoveLocalAnchor** , atribua a função AnchorModuleScript > **RemoveLocalAnchor ()** ,
  * em seguida, arraste o **ParentAnchor** novamente para o campo **nenhum (objeto de jogo)** vazio.
* Para o objeto **FindAzureAnchor** , atribua a função AnchorModuleScript > **FindAzureAnchor ()** .
* Para o objeto **DeleteAzureAnchor** , atribua a função AnchorModuleScript > **DeleteAzureAnchor ()** .

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. conectar a cena ao recurso do Azure

Na janela hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, role para baixo até o componente **Gerenciador de âncora espacial (script)** .

Em seguida, na seção **credenciais** , Cole a ID e a chave de sua conta de âncoras espaciais, que você criou como parte dos [pré-requisitos](mrlearning-asa-ch1.md#prerequisites)deste tutorial, nos campos chave de conta das **âncoras espaciais correspondentes ID** da conta e **âncoras espaciais** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Experimentando os comportamentos básicos das âncoras espaciais do Azure

Agora que sua cena está configurada para demonstrar os conceitos básicos das âncoras espaciais do Azure, é hora de implantar o aplicativo para que você possa experimentar as âncoras espaciais do Azure em primeira mão.

### <a name="1-add-additional-required-capabilities"></a>1. adicionar recursos adicionais necessários

No menu do Unity, selecione **editar** > **configurações do projeto...** para abrir a janela Configurações do Player:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

Na janela Configurações do Player, selecione **Player** e, em seguida, **configurações de publicação**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

Nas **configurações de publicação**, role para baixo até a seção **recursos** e verifique se os recursos de **internetclient**, **microfone**e **SpatialPerception** , que você habilitou quando criou o projeto no início do tutorial, estão habilitados. Em seguida, habilite os recursos **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**e **webcam** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. implante o aplicativo no seu HoloLens 2

As âncoras espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade de âncoras espaciais do Azure, você precisa implantar o projeto em seu dispositivo.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar seu projeto do Unity no HoloLens 2, você pode consultar as instruções [criar seu aplicativo para o dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) .

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Execute o aplicativo no seu HoloLens 2 e siga as instruções no aplicativo

> [!CAUTION]
> As âncoras espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.

Quando o aplicativo estiver em execução no seu dispositivo, siga as instruções na tela exibidas no painel de instruções do tutorial de âncora espacial do Azure:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Ancorando uma experiência

Nas seções anteriores, você aprendeu os conceitos básicos das âncoras espaciais do Azure. Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada. Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.

### <a name="1-add-the-rocket-launcher-experience"></a>1. adicionar a experiência do Rocket Launcher

Na janela do projeto, navegue até os **ativos** > **MRTK. Tutoriais. GettingStarted** > **pré-fabricados** > **RocketLauncher** pasta e selecione o **RocketLauncher_Complete** pré-fabricado:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Com o RocketLauncher_Complete pré-fabricado ainda selecionado, arraste-o sobre o objeto **ParentAnchor** na janela hierarquia para torná-lo um filho do objeto ParentAnchor:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. reposicionar a experiência do Rocket Launcher

Posicione, gire e dimensione o objeto **RocketLauncher_Complete** para uma escala e orientação adequadas, enquanto também garante que o objeto **ParentAnchor** ainda seja exposto, por exemplo:

* **Posição** de transformação X = 0, Y = 0, Z = 3,75
* **Rotação** de transformação X = 0, Y = 90, Z = 0
* **Escala** de transformação X = 10, Y = 10, Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

No aplicativo, os usuários agora podem reposicionar toda a experiência do Rocket Launcher movendo o cubo.

> [!TIP]
> Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de posição e rotação utensílios e muito mais.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu os conceitos básicos das âncoras espaciais do Azure. O tutorial forneceu a você vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão de âncoras espaciais do Azure e criar, carregar e baixar âncoras espaciais do Azure em um único dispositivo.

Na próxima lição, você aprenderá a salvar as IDs de âncora do Azure em seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado e como transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.

[Próxima lição: 2. salvando, recuperando e compartilhando âncoras espaciais do Azure](mrlearning-asa-ch2.md)

---
title: Tutoriais de Âncoras Espaciais do Azure – 1. Introdução às Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar o reconhecimento facial do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d0fd22ad6fbefc6889373b00847721cfc0655ce3
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604997"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introdução às Âncoras Espaciais do Azure

## <a name="overview"></a>Visão geral

Bem-vindo à segunda série de tutoriais do HoloLens 2. Nesta série de tutoriais de três partes, você aprenderá os conceitos básicos das Âncoras Espaciais do Azure.

Neste primeiro tutorial, [Introdução às Âncoras Espaciais do Azure](mrlearning-asa-ch1.md), você vai explorar as várias etapas necessárias para iniciar e parar uma sessão do Azure e criar, carregar e baixar âncoras do Azure em um dispositivo.

No segundo tutorial, [Salvar, recuperar e compartilhar Âncoras Espaciais do Azure](mrlearning-asa-ch2.md), você aprenderá a salvar Âncoras Espaciais do Azure em várias sessões de aplicativo salvando informações de âncora no armazenamento do HoloLens 2 e como compartilhar essas informações de âncora para outros dispositivos para um alinhamento de âncora de vários dispositivos.

No terceiro tutorial, [Exibir feedback de Âncora Espacial do Azure](mrlearning-asa-ch3.md), você aprenderá a fornecer aos usuários comentários sobre eventos de âncora e status ao usar Âncoras Espaciais do Azure.

## <a name="objectives"></a>Objetivos

* Conheça os conceitos básicos do desenvolvimento com Âncoras Espaciais do Azure para o HoloLens 2
* Criar, carregar e baixar âncoras espaciais

## <a name="prerequisites"></a>Pré-requisitos

>[!TIP]
>Se você ainda não concluiu a série de [Tutoriais de introdução](mrlearning-base.md), recomendamos que você a conclua primeiro.

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.2.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado
* Conclua a seção [Criar um recurso de Âncoras Espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) do tutorial [Guia de início rápido: criar um aplicativo HoloLens do Unity que usa Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).

> [!IMPORTANT]
> A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.2.X. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.

## <a name="creating-the-unity-project"></a>Como criar o projeto do Unity
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mrlearning-base-ch1.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mrlearning-base-ch1.md#create-new-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*

2. [Configurar o projeto do Unity para o Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importar recursos do TextMesh Pro Essential](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Configurar o projeto do Unity para o Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Adicionar o Mixed Reality Toolkit à cena do Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) e dar um nome adequado à cena, por exemplo, *AzureSpatialAnchors*

Então siga as instruções de [Como configurar os perfis do Mixed Reality Toolkit (Opção de Alterar Exibição de Reconhecimento Espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição para a malha de reconhecimento espacial para **Oclusão**.

> [!CAUTION]
> Conforme mencionado nas instruções de [Como configurar o projeto do Unity para o Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) vinculadas acima, é altamente recomendável não habilitar o MSBuild para o Unity.

## <a name="adding-inbuilt-unity-packages"></a>Como adicionar pacotes internos do Unity
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

Nesta seção, você instalará o pacote interno da AR Foundation do Unity porque ele é exigido pelo SDK de Âncoras Espaciais do Azure que será importado na próxima seção.

No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Pode levar alguns segundos até que o pacote de AR Foundation seja exibido na lista.

Na janela Gerenciador de Pacotes, selecione **AR Foundation** e instale o pacote clicando no botão **Instalar**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versão 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Como criar e preparar a cena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.AzureSpatialAnchors** > **Pré-Fabricados**. Mantendo o botão CTRL pressionado, clique em **ButtonParent**, **DebugWindow**, **Instruções** e **ParentAnchor** para selecionar os quatro pré-fabricados:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Com os quatro pré-fabricados ainda selecionados, arraste-os para a janela Hierarquia para adicioná-los à cena:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Para se concentrar nos objetos da cena, você pode clicar duas vezes no objeto ParentAnchor e, em seguida, reduzir levemente o zoom de novo:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Se você considerar que ícones grandes em sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição de desligado.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Como configurar os botões para operar a cena

Nesta seção, você adicionará scripts à cena para criar uma série de eventos de botão que demonstram os conceitos básicos de como as âncoras locais e as Âncoras Espaciais do Azure se comportam em um aplicativo.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. Configurar o componente de botão pressionável HoloLens 2 (Script)

Na janela Hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

Na janela Inspetor, localize o componente **Botão Pressionável HoloLens 2 (Script)** e adicione um novo ouvinte de eventos ao evento **Botão Pressionado ()** clicando no ícone **+** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Com o objeto StartAzureSession ainda selecionado na janela Hierarquia, clique e arraste o objeto **ParentAnchor** da janela Hierarquia para o campo **Nenhum (Objeto)** vazio do ouvinte de eventos que você acabou de adicionar para fazer com que o objeto ParentAnchor escute eventos pressionados desse botão:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Clique no menu suspenso **Nenhuma Função** do mesmo ouvinte de eventos e selecione **AnchorModuleScript** > **StartAzureSession ()** para definir a função StartAzureSession () como a ação disparada quando os eventos pressionados pelo botão são acionados desse botão:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. Configurar o componente Interação (Script)

Com o objeto StartAzureSession ainda selecionado na janela hierarquia, na janela Inspetor, localize o componente **Interação (Script)** e repita o mesmo processo, como na etapa 1 acima, para o evento **OnClick ()** :

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. Configurar os botões restantes

Para cada um dos botões restantes, conclua o processo descrito nas etapas 1 e 2 acima para atribuir funções aos eventos **Botão Pressionado ()** e **OnClick ()** :

* Para o objeto **StopAzureSession**, atribua a função AnchorModuleScript > **StopAzureSession ()** .
* Para o objeto **CreateAzureAnchor**, atribua a função AnchorModuleScript > **CreateAzureAnchor ()** ,
  * em seguida, arraste **ParentAnchor** novamente para o campo **Nenhum (Objeto de Jogo)** vazio.
* Para o objeto **RemoveLocalAnchor**, atribua a função AnchorModuleScript > **RemoveLocalAnchor ()** ,
  * em seguida, arraste **ParentAnchor** novamente para o campo **Nenhum (Objeto de Jogo)** vazio.
* Para o objeto **FindAzureAnchor**, atribua a função AnchorModuleScript > **FindAzureAnchor ()** .
* Para o objeto **DeleteAzureAnchor**, atribua a função AnchorModuleScript > **DeleteAzureAnchor ()** .

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. Conectar a cena ao recurso do Azure

Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, role para baixo até o componente **Gerenciador de Âncora Espacial (Script)** .

Em seguida, na seção **Credenciais**, cole a ID e a chave de conta de Âncoras Espaciais que você criou como parte dos [Pré-requisitos](mrlearning-asa-ch1.md#prerequisites) do tutorial, para os campos **ID da Conta de Âncoras Espaciais** e **Chave da Conta de Âncoras Espaciais** correspondentes:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Experimentando os comportamentos básicos das Âncoras Espaciais do Azure

Agora que sua cena está configurada para demonstrar os conceitos básicos das âncoras espaciais do Azure, é hora de implantar o aplicativo para que você possa experimentar as Âncoras Espaciais do Azure em primeira mão.

### <a name="1-add-additional-required-capabilities"></a>1. Adicionar funcionalidades adicionais necessárias

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Jogador:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

Na janela Configurações do Jogador, selecione **Jogador** e **Configurações de Publicação**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

Em **Configurações de Publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas. Em seguida, habilite as funcionalidades **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** e **Webcam**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Implantar o aplicativo em seu HoloLens 2

As Âncoras Espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade delas, você precisa implantar o projeto em seu dispositivo.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar seu projeto do Unity no HoloLens 2, confira as instruções para [Criar o aplicativo para seu dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Execute o aplicativo no seu HoloLens 2 e siga as instruções no aplicativo

> [!CAUTION]
> As Âncoras Espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.

Quando o aplicativo estiver em execução no seu dispositivo, siga as instruções na tela exibidas no painel Instruções do Tutorial de Âncora Espacial do Azure:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Como ancorar uma experiência

Nas seções anteriores, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure. Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada. Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.

### <a name="1-add-the-rocket-launcher-experience"></a>1. Adicionar a experiência do Lançador de Foguete

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutoriais.GettingStarted** > **Pré-fabricados** > **RocketLauncher** e selecione o pré-fabricado **RocketLauncher_Complete**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Com o pré-fabricado RocketLauncher_Complete ainda selecionado, arraste-o sobre o objeto **ParentAnchor** na janela Hierarquia para torná-lo um filho do objeto ParentAnchor:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. Reposicionar a experiência do Lançador de Foguete

Posicione, gire e dimensione o objeto **RocketLauncher_Complete** para uma escala e uma orientação adequadas e, ao mesmo tempo, garanta que o objeto **ParentAnchor** ainda seja exposto, por exemplo:

* **Posição** da Transformação X = 0, Y = 0, Z = 3,75
* **Rotação** da Transformação X = 0, Y = 90, Z = 0
* **Escala** da Transformação X = 10, Y = 10, Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

No aplicativo, os usuários agora podem reposicionar toda a experiência do Lançador de Foguete movendo o cubo.

> [!TIP]
> Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar uma caixa delimitadora que envolve a experiência, o uso de utensílios de posição e rotação e muito mais.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure. O tutorial forneceu vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure e criar, carregar e baixar as Âncoras Espaciais do Azure em um dispositivo.

Na próxima lição, você aprenderá a salvar as IDs de âncora do Azure em seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado, bem como a transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.

[Próxima lição: 2. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure](mrlearning-asa-ch2.md)

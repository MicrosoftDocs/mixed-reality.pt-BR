---
title: Tutoriais de Nuvem do Azure – 1. Serviços de Nuvem do Azure para HoloLens 2
description: Conclua este curso para aprender a implementar diversos serviços do Azure em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: azure, mixed reality, unity, tutorial, hololens, hololens 2, azure blob storage, azure table storage, azure spatial anchors, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: d69ce965718e31bb5a261631f3f40217e8f7c7d6
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376478"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. Serviços de Nuvem do Azure para HoloLens 2

## <a name="overview"></a>Visão geral

Bem-vindo(a) a esta série de tutoriais voltados para colocar serviços de **Nuvem do Azure** em um aplicativo do **HoloLens 2**. Nesta série de tutoriais em cinco partes, você aprenderá a integrar vários serviços de **Nuvem do Azure** em um projeto **Unity** para o **HoloLens 2**. Ao passar em cada capítulo, você adicionará novos serviços de **Nuvem do Azure** para expandir os recursos do aplicativo e a experiência do usuário, aprendendo ao mesmo tempo os conceitos básicos de cada serviço de **Nuvem do Azure**.

> [!NOTE]
> Esta série de tutoriais se concentrará no **HoloLens 2** mas, devido à natureza multiplataforma do Unity, a maioria dos seus aprendizados também se aplicará a aplicativos para Desktop e Smartphone.

Neste primeiro tutorial, [Apresentação dos Serviços de Nuvem do Azure para o HoloLens 2](mr-learning-azure-01.md), você vai começar explicando as metas do aplicativo, vai apresentar brevemente cada serviço de Nuvem do Azure e vai configurar o projeto do Unity.

No segundo tutorial, [Integração do Armazenamento do Azure](mr-learning-azure-02.md), você vai começar integrando o Armazenamento do Azure como a solução de persistência para o aplicativo de demonstração, vai aprender as diferenças entre Armazenamento de Blobs e Armazenamento de Tabelas, vai preparar os recursos de projeto necessários, vai configurar a cena e vai verificar as operações de leitura, atualização e exclusão de dados.

Continuando com o terceiro tutorial, [Integração da Visão Personalizada do Azure](mr-learning-azure-03.md), você usará a Visão Personalizada do Azure para treinar e detectar imagens no aplicativo do HoloLens 2. O capítulo começa com a configuração de seu próprio recurso de Visão Personalizada do Azure, preparando os componentes da cena e entrando em ação treinando e detectando suas próprias imagens de dentro do aplicativo.

Em seguida, você avançará para o quarto tutorial, [Integração de Âncoras Espaciais do Azure](mr-learning-azure-04.md), com a exploração do serviço Âncoras Espaciais do Azure para salvar e encontrar locais, aprender os principais conceitos, preparar os recursos necessários, configurar a cena e começar a usar o novo recurso no aplicativo.

Com o quinto tutorial, [Integração do Serviço de Bot do Azure com o LUIS](mr-learning-azure-05.md), você finaliza fornecendo ao aplicativo um novo método de interação do usuário: idioma natural! Esse recurso será realizado usando o Azure Bot Framework junto com o LUIS (Reconhecimento Vocal). Este capítulo final ensina os conceitos básicos do Serviço de Bot do Azure e para acelerar o processo, você usará o Bot Framework Composer como uma solução sem código. Depois que o bot for criado, você o integrará à cena e fará com que ele seja executado com o estágio final do aplicativo do HoloLens 2.

## <a name="application-goals"></a>Metas do aplicativo

Nesta série de tutoriais, você criará um aplicativo do **HoloLens 2** que poderá detectar objetos em imagens e encontrar seu local espacial. Para definir um idioma de domínio, essas entidades passarão a ser chamadas de **Objeto Rastreado**.
O usuário pode criar um **Objeto Rastreado** para associar um conjunto de imagens por meio da pesquisa visual computacional e/ou de um local espacial. Todos os dados devem ser persistidos na nuvem. Além disso, alguns aspectos do aplicativo serão controlados opcionalmente pelo idioma natural por meio de um bot.

### <a name="features"></a>Recursos

* Gerenciamento básico de dados e imagens
* Treinamento e detecção de imagem
* Armazenamento de um local espacial e diretrizes para ele
* Assistente de bot para usar alguns recursos por meio de linguagem natural

## <a name="azure-cloud-services"></a>Serviços de Nuvem do Azure

Para resolver os recursos necessários para o aplicativo, você usará esses serviços de **Nuvem do Azure**:

### <a name="azure-storage"></a>Armazenamento do Azure

Você usará o [Armazenamento do Azure](https://azure.microsoft.com/services/storage/) para a solução de persistência. Ele permite que você armazene dados em uma tabela e carregue binários grandes, como imagens.

### <a name="azure-custom-vision"></a>Visão Personalizada do Azure

Com a [Visão Personalizada do Azure](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (parte dos [Serviços Cognitivos do Azure](https://azure.microsoft.com/services/cognitive-services/)), você pode associar um conjunto de imagens a *Objetos Rastreados*, treinar um modelo de machine learning no conjunto e detectar o *Objeto Rastreado*.

### <a name="azure-spatial-anchors"></a>Âncoras Espaciais do Azure

Para armazenar o local de um *Objeto Rastreado* e fornecer instruções guiadas para encontrá-lo, você usa [Âncoras Espaciais do Azure](https://azure.microsoft.com/services/spatial-anchors/).

### <a name="azure-bot-service"></a>Serviço de Bot do Azure

O aplicativo é conduzido principalmente pela interface do usuário tradicional, por isso você usa o [Serviço de Bot do Azure](https://azure.microsoft.com/services/bot-service/) para adicionar alguma personalidade e agir como um novo método de interação.

## <a name="prerequisites"></a>Pré-requisitos

>[!TIP]
>Se você ainda não concluiu a série de [Tutoriais de introdução](mr-learning-base-01.md), recomendamos que você a conclua primeiro.

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](using-visual-studio.md#enabling-developer-mode)
* Uma webcam conectada se você quiser testar no editor do Unity
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2019.3.X instalado e o módulo de suporte de Build da Plataforma Universal do Windows adicionado

> [!CAUTION]
> A versão recomendada do Unity para esta série de tutoriais é o Unity 2019.3.X. Ela substitui todos os requisitos de versão do Unity ou as recomendações indicadas nos pré-requisitos vinculados acima.

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Para isso, primeiro siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais de Nuvem do Azure*
2. [Como alternar a plataforma de build](mr-learning-base-02.md#configuring-the-unity-project)
3. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Como importar o Kit de Ferramentas de Realidade Misturada](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Como configurar o projeto do Unity](mr-learning-base-02.md#configuring-the-unity-project)
6. [Criar e configurar a cena](mr-learning-base-02.md#creating-and-configuring-the-scene) e dar um nome adequado à cena, por exemplo, *AzureCloudServices*

Então siga as instruções em [Alterar a opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para alterar o perfil de configuração do MRTK para sua cena para o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição para a malha de reconhecimento espacial para **Oclusão**.

## <a name="installing-inbuilt-unity-packages"></a>Instalar pacotes internos do Unity

No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes** para abrir a janela Gerenciador de Pacotes e selecione **AR Foundation** e clique no botão **Instalar** para instalar o pacote:

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Você está instalando o pacote do AR Foundation porque ele é exigido pelo SDK de Âncoras Espaciais do Azure e será importado na próxima seção.

## <a name="importing-the-tutorial-assets"></a>Como importar os ativos do tutorial

Baixe e **importe** os seguintes pacotes personalizados do Unity **na ordem em que estão listados**:

* [Armazenamento do Azure para Unity](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [Âncoras Espaciais do Azure](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [MRTK.Tutorials.AzureCloudServices](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> Para obter um lembrete sobre como importar um pacote personalizado do Unity, você pode consultar as instruções [Importar o Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Como criar e preparar a cena
<!-- TODO: Consider renaming to 'Preparing the scene' -->

Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.

Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**. Mantendo pressionada a tecla CTRL, clique em **SceneController**, **RootMenu** e **DataManager** para selecionar os três pré-fabricados:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

O **SceneController (prefab)** contém dois scripts: **SceneController (script)** e **UnityDispatcher (script)** . O componente de script **SceneController** contém várias funções de UX e facilita a funcionalidade de captura de fotos e o **UnityDispatcher** é uma classe auxiliar para permitir a execução de ações no thread principal do Unity.

O **RootMenu (prefab)** é o pré-fabricado da interface do usuário principal que mantém todas as janelas da interface do usuário conectadas entre si por meio de vários pequenos componentes de script e que controla o fluxo geral de UX do aplicativo.

O **DataManager (prefab)** é responsável por conversar com o armazenamento do Azure e será explicado mais detalhadamente no próximo tutorial.

Agora, com os três pré-fabricados ainda selecionados, arraste-os para a janela Hierarquia para adicioná-los à cena:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

Para se concentrar nos objetos da cena, clique duas vezes no objeto **RootMenu** e, em seguida, reduzir levemente o zoom de novo:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> Se você considerar que ícones grandes em sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição de desligado.

## <a name="configuring-the-scene"></a>Configurando a cena

Nesta seção, você conectará *SceneManager*, *DataManager* e *RootMenu* juntos para ter uma cena funcional pronta para o seguinte tutorial, [Integrar o armazenamento do Azure](mr-learning-azure-01.md).

### <a name="connect-the-objects"></a>Conectar os objetos

Na janela Hierarquia, selecione o objeto **DataManager**:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

Na janela do Inspetor, localize o componente **DataManager (script)** e você verá um slot vazio no evento **On Data Manager Ready ()** . Agora, na janela Hierarquia, arraste o objeto **SceneController** para o evento **On Data Manager Ready ()** .

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

Você observará que o menu suspenso do evento se tornou ativo; clique no menu suspenso e navegue até **SceneController** e, no submenu, selecione a opção **Init ()** :

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

Na janela Hierarquia, selecione o objeto **SceneController**; então, no Inspetor, você encontrará o componente **SceneController** (script).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

Você verá que há vários campos não preenchidos; nós vamos alterar isso. Mova o objeto **DataManager** da Hierarquia para o campo *Gerenciador de Dados* e mova o GameObject **RootMenu** da Hierarquia para o campo *Menu Principal*.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

Agora, sua cena está pronta para os próximos tutoriais. Não se esqueça de salvá-la em seu projeto.

## <a name="prepare-project-build-pipeline"></a>Preparar pipeline de Build do projeto

Embora o projeto ainda tenha que ser preenchido com conteúdo, você precisa executar alguns preparativos para que o projeto fique pronto para a compilação para o **HoloLens 2**.

### <a name="1-add-additional-required-capabilities"></a>1. Adicionar funcionalidades adicionais necessárias

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

Na janela Configurações do Projeto, selecione **Jogador** e **Configurações de Publicação**:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

Em **Configurações de Publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas. Em seguida, habilite as funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** e **Webcam**:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Implantar o aplicativo em seu HoloLens 2

Nem todos os recursos que você usará nesta série de tutoriais podem ser executados dentro do editor do Unity; isso significa que você precisa estar familiarizado com a implantação do aplicativo em seu dispositivo do HoloLens 2.

> [!TIP]
> Para se lembrar de como criar e implantar seu projeto do Unity no HoloLens 2, confira as instruções em [Tutoriais de introdução – Criar o aplicativo para seu dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Execute o aplicativo no seu HoloLens 2 e siga as instruções no aplicativo

> [!CAUTION]
> Todos os Serviços do Azure usam a Internet, portanto, verifique se o dispositivo está conectado à Internet.

Quando o aplicativo estiver em execução no dispositivo, aceite o acesso às seguintes funcionalidades solicitadas:

* Microfone
* Câmera

Esses recursos são necessários para serviços como *Chat Bot* e *Visão Personalizada* funcionarem corretamente.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você foi apresentado à série de tutoriais, aprendeu sobre os recursos que você implementará e como os serviços de **Nuvem do Azure** se unem para dar vida ao seu aplicativo do *HoloLens 2*. Você adicionou os componentes necessários ao projeto e preparou a cena para esta série de tutoriais.

Na próxima lição, você usará o armazenamento do Azure como uma solução de persistência baseada em nuvem para armazenar dados e imagens.

[Próximo tutorial: 2. Integrar o armazenamento do Azure](mr-learning-azure-02.md)

---
title: Tutoriais de Âncoras Espaciais do Azure – 5. Âncoras Espaciais do Azure para o Android e o iOS
description: Conclua este curso para aprender a implantar um projeto do Unity com o Kit de Ferramentas de Realidade Misturada e Âncoras Espaciais do Azure para Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, android, ios
ms.localizationpriority: high
ms.openlocfilehash: 8c63204948b3e4aa3d25e5b2ca948798726f0838
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376538"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Âncoras Espaciais do Azure para o Android e o iOS

Neste tutorial, você aprenderá a criar seu projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.

## <a name="objectives"></a>Objetivos

* Saiba como criar o projeto para seu dispositivo Android usando o Plug-in ARCore XR e o AR Foundation do Unity
* Saiba como criar o projeto para seu dispositivo iOS usando o Plug-in ARKit XR e o AR Foundation do Unity

## <a name="installing-inbuilt-unity-packages"></a>Instalar pacotes internos do Unity

Nesta seção, você atualizará e instalará os seguintes pacotes embutidos:

* AR Foundation 3.1.3
* Auxiliares de entrada herdados 2.1.4
* Plug-in ARCore XR 3.1.3 para suporte ao Android
* Plug-in ARKit XR 3.1.3 para suporte a iOS

> [!CAUTION]
> Nem todas as versões são compatíveis com o MRTK e apenas determinadas versões funcionam em conjunto, portanto, instale as versões exatas listadas acima.

No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes** para abrir a janela Gerenciador de Pacotes e selecione **AR Foundation** > **3.1.3** e clique no botão **Atualizar para 3.1.3** para atualizar o pacote:

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

Siga o mesmo processo para importar os pacotes restantes, conforme necessário.

> [!NOTE]
> Se você estiver desenvolvendo esse projeto para Android, não será necessário instalar o pacote Plug-in ARKit XR. Da mesma forma, se você estiver desenvolvendo esse projeto para iOS, não será necessário instalar o Plug-in ARCore XR.

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Configurar o MRTK para a Câmera do AR Foundation

Nesta seção, você aprenderá a configurar o MRTK para implantação em um dispositivo móvel.

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**. Em seguida, na janela Inspetor, selecione a guia **Câmera**, clone o perfil da câmera e dê a ele um nome adequado, por exemplo, **AzureSpatialAnchors_ARCameraProfile**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do Kit de Ferramentas de Realidade Misturada](mr-learning-base-03.md).

Com a guia **Câmera** ainda selecionada na janela Inspetor, expanda os **Provedores de Configuração da Câmera** e clique no botão **+ Adicionar Provedor de Configuração de Câmera** e, em seguida, expanda o **Novo provedor de dados 1** adicionado recentemente:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

Usando a lista suspensa **Tipo**, altere o tipo para **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

Com o objeto **MixedRealityToolkit** ainda selecionado na janela Hierarquia, use o botão **Adicionar Componente** na janela Inspetor para adicionar os seguintes componentes:

* AR Anchor Manager (Script)
* DisableDiagnosticsSystem (Script)

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> Quando você adiciona o componente AR Reference Point Manager (Script), o componente AR Session Origin (Script) é adicionado automaticamente, pois é exigido pelo componente AR Reference Point Manager (Script).

## <a name="building-your-application-to-your-android-device"></a>Compilar o aplicativo para seu dispositivo Android

Nesta seção, você aprenderá a configurar seu projeto para compilá-lo e implantá-lo em um dispositivo Android.

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build e, em seguida, alterne a plataforma para Android:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Para lembrar como mudar a plataforma de build, consulte as instruções em [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform).

Feche a janela Configurações de Build.

No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity** para abrir a janela do **Configurador de Projeto do MRTK**, confirme se todas as opções estão selecionadas e clique no botão **Aplicar** para aplicar as configurações:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Outras Configurações**, selecione **Vulkan** e remova-o clicando no símbolo de **"-"** :

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

Feche a janela Configurações do Player e abra a janela Configurações de Build novamente.

Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**. Em seguida, use um cabo USB, conecte seu dispositivo Android ao seu computador e selecione-o na lista suspensa **Executar Dispositivo**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Se o dispositivo não aparecer na lista suspensa Executar Dispositivo, pode ser necessário pressionar o botão Atualizar ao lado do menu suspenso.

Na janela Configurações de Build, clique no botão **Compilar e Executar** para abrir a janela Compilar Android.

Escolha um local adequado para armazenar o build, por exemplo, _D:\MixedRealityLearning\Builds_ e dê ao APK um nome adequado, por exemplo, _MRTKTutorials-AzureSpatialAnchors_ e clique no botão **Salvar** para iniciar o processo de build:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
Se você receber algum erro na janela do Console do Unity relacionado aos módulos SDK, NDK ou JDK do Android, será necessário abrir o Hub do Unity e instalar os módulos de Suporte de Build do Android associados.

Quando o processo de build for concluído, os aplicativos deverão ser carregados automaticamente em seu dispositivo Android.

## <a name="building-your-application-to-your-ios-device"></a>Compilar o aplicativo para seu dispositivo iOS

Nesta seção, você aprenderá a configurar seu projeto para compilá-lo e implantá-lo em seu dispositivo iOS.

No menu do Unity, selecione **Arquivo** > **Configurações de Build...** para abrir a janela Configurações de Build e alterne a plataforma para iOS:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Para lembrar como mudar a plataforma de build, consulte as instruções em [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform).

Feche a janela Configurações de Build.

No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar Projeto do Unity** para abrir a janela do **Configurador de Projeto do MRTK**, confirme se todas as opções estão selecionadas e clique no botão **Aplicar** para aplicar as configurações:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações do Player, então localize a seção **Player** >  **Outras Configurações**, desmarque a caixa de seleção **Remover Código do Mecanismo** para desabilitá-la:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

Feche a janela Configurações do Player e abra a janela **Configurações de Build** novamente.

Na janela Configurações de Build, clique no botão **Adicionar Cenas Abertas** para adicionar a cena atual à lista de **Cenas no Build**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

Na janela Configurações de Build, clique no botão **Compilar** para abrir a janela Compilar iOS.

Escolha um local adequado para armazenar o projeto do Xcode, por exemplo, _D:\MixedRealityLearning\Builds_, crie uma pasta e dê a ela um nome adequado, por exemplo, _MRTKTutorials-AzureSpatialAnchors_ e, em seguida, clique no botão **Selecionar Pasta** para iniciar o processo de build:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

Quando o processo de build for concluído, siga as instruções de [Exportar o projeto do Xcode](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implantar o projeto do Xcode em seu dispositivo iOS.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar o projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.

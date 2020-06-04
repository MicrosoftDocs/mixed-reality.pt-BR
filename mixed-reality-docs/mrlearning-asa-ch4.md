---
title: Tutoriais de Âncoras Espaciais do Azure – 4. Âncoras Espaciais do Azure para o Android e o iOS
description: Conclua este tutorial para saber como implementar as Âncoras Espaciais do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, curso, hololens, azure, âncoras espaciais
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867618"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a>4. Âncoras Espaciais do Azure para o Android e o iOS

Neste tutorial, você aprenderá a criar seu projeto para dispositivos Android e iOS usando o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR.

## <a name="objectives"></a>Objetivos

* Saiba como criar seu projeto para o dispositivos Android usando o Unity AR Foundation e o Plug-in ARCore XR.
* Saiba como criar seu projeto para dispositivos iOS usando o Unity AR Foundation e o Plug-in ARKit XR.

[!NOTE] Antes deste tutorial, recomendamos que você conclua os Tutoriais de Âncoras Espaciais do Azure -> [Introdução às Âncoras Espaciais do Azure](mrlearning-asa-ch1.md).

## <a name="adding-inbuilt-unity-packages"></a>Como adicionar pacotes internos do Unity

Nesta seção, você instalará os pacotes do AR Foundation interno do Unity, do Plug-in ARCore XR e do Plug-in ARKit XR necessários para dar suporte a dispositivos Android e iOS.

Certifique-se de instalar a versão correta dos pacotes do Unity, conforme listado abaixo:

* **AR Foundation 2.1.4**
* **Plug-in ARCore XR 2.2.0 versão prévia 2**
* **Plug-in ARKit XR 2.1.1**

[!NOTE] Se você estiver desenvolvendo esse projeto para Android, não será necessário instalar o pacote Plug-in ARKit XR. Da mesma forma, se você estiver desenvolvendo esse projeto para iOS, não será necessário instalar o Plug-in ARCore XR.

No menu do Unity, selecione **Janela** > **Gerenciador de Pacotes**:

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

Pode demorar alguns segundos até que todos os pacotes apareçam na lista. Para exibir pacotes em versão prévia, clique na opção Avançado e selecione "**Mostrar pacotes em versão prévia**".

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

Na janela Gerenciador de Pacotes, selecione **AR Foundation**. Entre as muitas versões, você deverá selecionar a versão 2.1.4 e atualizar o pacote clicando no botão **Atualizar para 2.1.4**:

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

Para dar suporte a dispositivos Android, siga o mesmo processo para importar o Plug-in ARCore XR 2.2.0 versão prévia 2.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

Para dar suporte a dispositivos iOS, você deve importar o pacote **Plugin ARKit XR 2.1.1** do Unity no Gerenciador de Pacotes.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a>Personalizar o MRTK para dar suporte à câmera do AR Foundation

Personalize as configurações de MRTK para dar suporte ao AR Foundation selecionando o MixedRealityToolKit na janela Hierarquia e clique no botão **Clonar** no Kit de Ferramentas de Realidade Misturada na janela Inspetor.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

Ao clicar no botão **clone**, uma nova janela Clonar Perfil será exibida, clique então novamente no botão Clonar para clonar o DefaultMixedRealityToolkitProfile.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

Da mesma forma, clone o perfil da câmera na janela do Inspetor e renomeie o perfil para "UnityARConfigurationProfile" e clique no botão **Clonar**. Na janela Inspetor, localize o MixedReality, selecione a guia Câmera. Expanda os provedores de configuração de câmera na janela Inspetor e clique em **+ Adicionar Provedor de Configuração de Câmera** > expandir **Novo provedor de dados 1** > selecionar Tipo **Nenhum** > selecionar **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > selecionar **UnityARCameraSettings**.


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

Com o objeto MixedRealityToolKit selecionado na janela Hierarquia, anexe os scripts de suporte à janela Inspetor ao clicar no botão **Adicionar componente**, digite AR reference Point manager e selecione o script.

Adicionar o script "AR Reference Point Manager" adicionará junto "AR session origin" automaticamente na janela Inspetor. Depois de adicionar os scripts de suporte, a janela Inspetor deverá ficar com esta aparência.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a>Compilar aplicativo para dispositivo Android

Para compilar esse aplicativo para seu dispositivo Android, clique em **Arquivo** na parte superior da janela e selecione **Configurações de Build.** Uma nova janela aparecerá na tela, selecione **Android** e clique em **Alternar plataforma**. Levará alguns minutos para mudar de plataforma. Depois de alternar para a plataforma Android, clique em **Adicionar Cenas Abertas** e verifique se a cena atual é a única cena selecionada na lista de **Cenas em Build**.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

Feche a janela de **Configurações de Build**. No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar o Projeto do Unity** e clique em **Aplicar** para configurar o projeto do Unity para a plataforma Android.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

No menu do Unity, selecione **Editar** > **Configurações de Projeto** para abrir a janela Configurações de Projeto. Na janela Configurações do Projeto, selecione a guia **Player**, expanda a seção Outras Configurações, selecione **Vulkan** e remova-o clicando no símbolo "-".

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

Feche a janela Configurações do Player e abra a janela Configurações de Build novamente. Em seguida, usando um cabo USB, conecte seu dispositivo Android ao seu computador e selecione o dispositivo no **Compilar e executar no** menu suspenso e, em seguida, clique em **Compilar e executar**. Você será solicitado a salvar um arquivo .apk, para o qual pode escolher qualquer nome.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> Se você receber algum erro na janela do Console do Unity relacionado aos módulos SDK, NDK e/ou JDK do Android, será necessário abrir o Hub do Unity e instalar os módulos SDK, NDK e JDK associados para o módulo de Suporte de Build do Android.

Quando o processo de compilação for concluído, seus aplicativos deverão ser carregados automaticamente em seu dispositivo Android.

## <a name="build-application-to-ios-device"></a>Compilar aplicativo para dispositivo iOS

Para compilar esse aplicativo para seu dispositivo iOS, clique em **Arquivo** na parte superior da janela e selecione **Configurações de compilação.** Uma nova janela aparecerá na tela, selecione então **iOS** e clique em **Alternar plataforma**.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

Feche a janela de **Configurações de Build**. No menu do Unity, selecione **Kit de Ferramentas de Realidade Misturada** > **Utilitários** > **Configurar o Projeto do Unity** e clique em **Aplicar** para configurar o projeto do Unity para a plataforma iOS.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

Para compilar o projeto do XCode do iOS, vá para Configurações de compilação e clique em **Compilar**.

Siga [este guia](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implantar esse projeto em seu dispositivo iOS.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a compilar seu projeto para dispositivos Android e iOS. Você também aprendeu a usar o AR Foundation, o Plug-in ARCore XR e o Plug-in ARKit XR para fazer seu projeto funcionar em dispositivos Android e iOS.
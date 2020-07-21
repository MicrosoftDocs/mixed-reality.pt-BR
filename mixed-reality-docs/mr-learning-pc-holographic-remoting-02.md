---
title: Tutoriais de Comunicação Remota Holográfica para PC – 2. Criar um aplicativo de Comunicação Remota Holográfica para PC
description: Conclua este curso para aprender como criar a experiência de realidade misturada remota do seu PC para o HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 32fccbaf6bae8031572ff716f3c9fc26a43849e5
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304069"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Como criar um aplicativo de Comunicação Remota Holográfica para PC

Neste tutorial, você aprenderá a criar um aplicativo para PC de Comunicação Remota Holográfica e a conectar-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo em 3D na realidade misturada.

## <a name="objectives"></a>Objetivos

* Configurar o Unity para Comunicação Remota Holográfica
* Saber como criar e implantar o aplicativo com o Visual Studio
* Desenvolver o aplicativo de Comunicação Remota Holográfica e conectar-se ao HoloLens

## <a name="configuring-your-scene-for-holographic-remoting"></a>Configurar a sua cena para a Comunicação Remota Holográfica

Nesta seção, você vai configurar o projeto para transmitir a sua experiência de Realidade Misturada do seu PC para o dispositivo de HoloLens 2 em tempo real em uma conexão Wi-Fi.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.PCHolograhicRemoting** > **Pré-fabricados** e clique e arraste o pré-fabricado **HolographicRemoting** para a sua cena.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>Criar o aplicativo para PC

O seu aplicativo de Comunicação Remota Holográfica agora está pronto para ser criado no PC. Siga as etapas abaixo e faça estas alterações para criar esse aplicativo no seu PC.

### <a name="1-set-the-player-settings"></a>1. Definir as configurações do player

No menu do Unity, selecione Editar > Configurações do Projeto para abrir a janela Configurações do Player.

Na seção **Configurações de XR**, marque a caixa de seleção **Comunicação Remota Holográfica do WSA com Suporte** e habilite a Comunicação Remota Holográfica.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Criar o Projeto do Unity

No menu do Unity, selecione Arquivo > Configurações de Build para abrir a janela Configurações de Build.

Na janela Configurações de Build, clique no botão ***Adicionar Cenas Abertas*** para adicionar a cena atual às Cenas. Na lista Criar, clique no botão ***Criar*** para abrir a janela Criar a Plataforma Universal do Windows:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

Na janela Criar Plataforma Universal do Windows, escolha uma localização adequada para armazenar o seu build, por exemplo, Documents\MixedRealityLearning. Crie uma pasta e dê a ela um nome adequado, por exemplo, PCHolographicRemoting. Em seguida, clique no botão ***Selecionar Pasta*** para iniciar o processo de build:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Aguarde até que o Unity conclua o processo de build.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Compilar e implantar o aplicativo

Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra o local em que você armazenou o build. Navegue dentro da pasta e clique duas vezes no arquivo .sln para abri-lo no Visual Studio:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar que todos os componentes necessários estejam instalados conforme especificado na documentação Instalar as Ferramentas.

Configure o Visual Studio para PC selecionando a configuração da Versão, a arquitetura x64 e o Computador Local como um destino:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Clique no botão ***Computador Local***. Ele começa a criar e implantar o aplicativo no seu PC. O aplicativo será instalado no seu PC por padrão.

## <a name="testing-holographic-remoting-remote-application"></a>Como testar o aplicativo remoto de Comunicação Remota Holográfica

Para conectar o seu aplicativo para PC ao seu HoloLens 2, siga o processo abaixo:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Instale o aplicativo de Player de Comunicação Remota no dispositivo HoloLens 2

* No seu HoloLens 2, visite a Loja de aplicativos e pesquise por "**Player de Comunicação Remota**".
* Selecione o aplicativo **Player de Comunicação Remota**.
* Toque em **Instalar** para baixar e instalar o aplicativo.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Conectar o aplicativo de Comunicação Remota Holográfica para PC ao Player de Comunicação Remota

* Inicie o **Player de Comunicação Remota** no seu HoloLens.
* Anote o **endereço IP** do HoloLens. Ele será exibido como um holograma pelo **Player de Comunicação Remota** assim que for iniciado.
* Abra um aplicativo de Comunicação Remota Holográfica para PC no seu PC.
* Depois que o aplicativo for iniciado, insira o **endereço IP** e clique no botão **Conectar** para se conectar.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como criar um aplicativo remoto para PC de Comunicação Remota Holográfica e a conectar-se ao HoloLens 2 a qualquer momento, fornecendo um modo de visualizar o conteúdo em 3D na realidade misturada. Depois que o HoloLens estiver conectado ao aplicativo de Comunicação Remota Holográfica para PC, você deverá ver a transmissão da experiência de realidade misturada no seu dispositivo de HoloLens 2.

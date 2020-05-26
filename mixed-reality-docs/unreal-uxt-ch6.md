---
title: 6. Como empacotar e implantar no dispositivo ou emulador
description: Parte 6 de um tutorial para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519958"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Como empacotar e implantar no dispositivo ou emulador

Esta seção orienta nas etapas de preparação de seu aplicativo para ser executado em um dispositivo ou emulador do HoloLens 2. Se você tem um dispositivo, pode transmitir do seu computador para o dispositivo ou empacotar o aplicativo para ser executado diretamente no dispositivo. Se você não tiver um dispositivo, será necessário empacotar o aplicativo para que ele seja executado no Emulador. 

## <a name="objectives"></a>Objetivos

* [Somente para dispositivo] Transmitir seu aplicativo para o HoloLens 2 por meio de comunicação remota holográfica do aplicativo
* Empacotar e implantar seu aplicativo em um dispositivo ou emulador do HoloLens 2

## <a name="device-only-stream"></a>[Somente para dispositivo] Transmitir

1.  Instale o **Player de Comunicação Remota Holográfica** por meio da Microsoft Store no seu HoloLens 2 e execute o aplicativo

2.  Acesse **Editar > Configurações do Projeto**. Na seção Comunicação Remota Holográfica, marque a caixa para habilitar a comunicação remota e reinicie o editor.

3.  Insira o endereço IP do seu dispositivo e clique em Conectar.

4.  Quando estiver conectado, no editor do UE4, clique na seta suspensa à direita do botão Reproduzir e selecione a visualização VR.

## <a name="package-and-deploy-your-app"></a>Empacotar e implantar seu aplicativo 

>[!NOTE]
>Se esta for a primeira vez que você empacota um aplicativo Unreal para o HoloLens, precisará baixar os arquivos de suporte do Epic Launcher. Para fazer isso, acesse a guia **Biblioteca** no Epic Games Launcher. Selecione a seta suspensa ao lado de **Iniciar** e clique em **Opções**. Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**. 
>![Configurações do projeto – Descrição](images/unreal-uxt/6-installationoptions.PNG)

1.  Acesse **Editar > Configurações do Projeto**. Em **Projeto > Descrição > Sobre > Nome do Projeto**, dê um nome ao seu projeto. Em **Projeto > Descrição > Publicador > Nome Diferenciado da Empresa**, coloque “CN={INSERT COMPANY NAME}”. Deixar qualquer um desses campos em branco resultará em um erro. 

![Configurações do projeto – descrição](images/unreal-uxt/6-cn.PNG)

2.  Em **Plataformas > HoloLens**, escolha Emulação e/ou Dispositivo com base em qual você deseja direcionar.

3.  Na seção **Empacotamento**, ao lado de **Certificado de Assinatura**, clique no botão **Gerar novo** para gerar um novo certificado de autenticação. Volte para a Janela principal.

![Configurações do projeto – Plataformas – HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  Acesse **Arquivo > Empacotar Projeto** e selecione **HoloLens**. Crie uma pasta para salvar o pacote e clique em **Selecionar Pasta**. 

5.  Depois que o aplicativo tiver sido empacotado com êxito, abra o **Portal de Dispositivo do Windows**, acesse **Exibições > Aplicativos** e localize a seção **Implantar aplicativos**.

6.  Clique em **Procurar...** e navegue até o arquivo **ChessApp.appxbundle**. Clique em **Abrir**. 

    * Se esta é a primeira vez que você está instalando o aplicativo em seu dispositivo, marque a caixa ao lado de **Permitir que eu selecione pacotes da estrutura**. Na próxima caixa de diálogo, inclua o arquivo appx VCLibs apropriado (arm64 para dispositivo, x64 para emulador). 

7.  Clique em **Instalar**

Parabéns por concluir este tutorial!  
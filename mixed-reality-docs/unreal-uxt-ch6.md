---
title: 6. Como empacotar e implantar no dispositivo ou emulador
description: Parte 6 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 99407a4069f914bf077e6323dde3e12978f6b765
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345686"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Como empacotar e implantar no dispositivo ou emulador

## <a name="overview"></a>Visão geral

No tutorial anterior, você adicionou um botão simples que redefine a peça de xadrez para a posição original dela. Nesta seção final, você fará com que o aplicativo esteja pronto para ser executado em um HoloLens 2 ou em um emulador. Se você tem um HoloLens 2, pode transmitir do seu computador ou empacotar o aplicativo para ser executado diretamente no dispositivo. Se você não tem um dispositivo, você está empacotando o aplicativo para ser executado no emulador. Ao final desta seção, você terá um aplicativo de realidade misturada implantado que você poderá jogar, completo, com interações e interface do usuário.

## <a name="objectives"></a>Objetivos

* [Somente para dispositivo] Transmitir para o HoloLens 2 por meio de comunicação remota holográfica do aplicativo
* Empacotar e implantar seu aplicativo em um emulador ou dispositivo do HoloLens 2

## <a name="device-only-streaming"></a>[Somente para dispositivo] Streaming
A [comunicação remota holográfica](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting), nesse caso, significa transmitir dados de um computador ou dispositivo UWP autônomo para o HoloLens 2, sem mudar de canal. Isso funciona com um aplicativo host de comunicação remota que recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo de volta para o HoloLens por Wi-Fi. O streaming permite que você adicione exibições imersivas remotas a software de PC desktop existente e tenha acesso a mais recursos do sistema. 

Se você estiver seguindo por esse caminho com o aplicativo de xadrez, precisará fazer algumas coisas:

1.  Instale o **Player de Comunicação Remota Holográfica** por meio da Microsoft Store no seu HoloLens 2 e execute o aplicativo.

2.  Acesse **Editar > Configurações do Projeto** e marque **habilitar a comunicação remota** na seção **Comunicação Remota Holográfica**.

3.  Reinicie o editor, [encontre o endereço IP do dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi), insira-o e clique em **Conectar**.

Quando estiver conectado, clique na seta suspensa à direita do botão **Jogar** e selecione a **Visualização de VR**. Isso executará o aplicativo na Janela de Visualização de VR, que é transmitida para o headset do HoloLens. 

## <a name="packaging-and-deploying-the-app"></a>Como empacotar e implantar o aplicativo 

>[!NOTE]
>Se esta for a primeira vez que você empacota um aplicativo Unreal para o HoloLens, precisará baixar os arquivos de suporte do Epic Launcher. 
>- Vá para a guia **Biblioteca** no Inicializador da Epic Games, selecione a seta suspensa ao lado de **Iniciar** > e clique em **Opções**. 
>- Em **Plataformas de Destino**, selecione **HoloLens 2** e clique em **Aplicar**. 
>![Configurações do projeto – Descrição](images/unreal-uxt/6-installationoptions.PNG)

1.  Acesse **Editar > Configurações do Projeto**. 
    * Em **Projeto > Descrição > Sobre > Nome do Projeto**, adicione um nome de projeto. 
    * Adicione **CN=NomeDaSuaEmpresa** em **Projeto > Descrição > Editor > Nome Diferenciado da Empresa**.

> [!IMPORTANT]
> Se você deixar um desses campos em branco, isso resultará em um erro quando você tentar e gerar um novo certificado na etapa 3. 

> [!IMPORTANT]
> O nome do editor precisa estar no [Formato de Nomes Diferenciados LADPv3](https://www.ietf.org/rfc/rfc2253.txt). Um nome malformado do editor gera o erro "Chave de assinatura não encontrada. Não foi possível assinar o aplicativo digitalmente." durante o empacotamento.

![Configurações do projeto – descrição](images/unreal-uxt/6-cn.PNG)

2.  Habilite **Compilar para Emulação no HoloLens** e/ou **Compilar para Dispositivo do HoloLens** em **Plataformas > HoloLens**.

3.  Clique em **Gerar novo** na seção **Empacotamento** (ao lado de **Certificado de Autenticação**).

> [!IMPORTANT]
> Se você está usando um certificado que já foi gerado, o nome do editor do certificado precisa ser igual ao nome do editor do aplicativo. Caso contrário, isso gera o erro "Chave de assinatura não encontrada. Não foi possível assinar o aplicativo digitalmente." erro.

![Configurações do projeto – Plataformas – HoloLens](images/unreal-uxt/6-packaging.PNG)

4. Clique em **Nenhum** para fins de teste quando precisar criar uma senha da chave privada.

![Como gerar um novo certificado](images/unreal-uxt/6-private-key-testing.png)

5. Acesse **Arquivo > Empacotar Projeto** e selecione **HoloLens**. 
    * Crie uma pasta para salvar o pacote e clique em **Selecionar Pasta**. 

6.  Depois que o aplicativo tiver sido empacotado, abra o [Portal de Dispositivos do Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), acesse **Exibições > Aplicativos** e localize a seção **Implantar aplicativos**.

7.  Clique em **Procurar...** , encontre o arquivo **ChessApp.appxbundle** e clique em **Abrir**. 

    * Se esta é a primeira vez que você está instalando o aplicativo em seu dispositivo, marque a caixa ao lado de **Permitir que eu selecione pacotes de estrutura**. 
    * Na próxima caixa de diálogo, inclua os arquivos **VCLibs** e **appx** apropriados (arm64 para dispositivo, x64 para emulador). Você pode encontrá-los em **HoloLens**, dentro da pasta em que você salvou o pacote.

8.  Clique em **Instalar**
    * Agora você pode acessar **Todos os Aplicativos** e tocar no aplicativo recém-instalado para executá-lo ou pode iniciar o aplicativo diretamente do **Portal de Dispositivos do Windows**. 

Parabéns! Seu aplicativo de realidade misturada do HoloLens está concluído e pronto para uso. No entanto, esse não é o fim da jornada. O MRTK tem muitos recursos autônomos que você pode adicionar aos seus projetos, incluindo entrada por foco e voz, mapeamento espacial e até mesmo códigos QR. Mais informações sobre esses recursos podem ser encontradas na [Visão geral do desenvolvimento com o Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).

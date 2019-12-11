---
title: Como usar o Visual Studio para implantação e depuração
description: Saiba como compilar, depurar e implantar aplicativos para o HoloLens e o Windows Mixed Reality usando o Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realidade misturada, depurar, implantar
ms.openlocfilehash: b7e6a8d538670a53de20a2f3a2850639e756da1a
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830836"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Como usar o Visual Studio para implantação e depuração

Se deseja usar o DirectX ou o Unity para desenvolver seu aplicativo de realidade misturada, você usará o Visual Studio para depuração e implantação. Nesta seção, você aprenderá a:
* Implantar aplicativos no HoloLens ou no headset imersivo do Windows Mixed Reality por meio do Visual Studio.
* Usar o emulador do HoloLens incorporado no Visual Studio.
* Depurar aplicativos de realidade misturada.

## <a name="prerequisites"></a>Pré-requisitos
1. Confira [Instalar as ferramentas](install-the-tools.md) para obter instruções de instalação.
2. Crie um projeto de aplicativo universal do Windows no Visual Studio.  Para o HoloLens (1ª geração), use o Visual Studio 2017 ou mais recente.  Para o HoloLens 2, use o Visual Studio 2019 16.2 ou mais recente. Há suporte para C# e C++. (Ou siga as instruções para [criar um aplicativo no Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Habilitar o modo de desenvolvedor

Comece habilitando o **Modo de Desenvolvedor** no dispositivo, para que o Visual Studio possa se conectar a ele.

### <a name="hololens"></a>HoloLens
1. Ligue o HoloLens e coloque o dispositivo.
2. Faça o gesto [bloom](system-gesture.md#bloom) para iniciar o menu principal.
3. Foque o bloco **Configurações** e faça o gesto de [fechar e abrir os dedos indicador e polegar](gaze-and-commit.md#composite-gestures). Faça um segundo air tap para colocar o aplicativo em seu ambiente. O aplicativo Configurações será iniciado depois disso.
4. Selecione item de menu **Atualização**.
5. Selecione o item de menu **Para desenvolvedores**.
6. Habilite o **Modo de Desenvolvedor**. Isso permitirá que você [implante aplicativos do Visual Studio](using-visual-studio.md) no HoloLens.
7. Opcional: Role a página para baixo e habilite também o **Portal de Dispositivos**. Isso também permitirá que você se conecte ao [Portal de Dispositivos do Windows](using-the-windows-device-portal.md) no HoloLens em um navegador da Web.

### <a name="windows-pc"></a>Computador Windows

Se você estiver trabalhando com um headset do Windows Mixed Reality conectado ao computador, habilite o **Modo de Desenvolvedor** no computador.
1. Ir para **Configurações**
2. Selecione **Atualização e Segurança**
3. Selecione **Para desenvolvedores**
4. Habilite o **Modo de Desenvolvedor**, leia o aviso de isenção de responsabilidade da configuração escolhida e, em seguida, clique em Sim para aceitar a alteração.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Como implantar um aplicativo via Wi-Fi – HoloLens (1ª geração)
1. Selecione uma configuração de build **x86** para o aplicativo ![Configuração de build x86 no Visual Studio](images/x86setting.png)
2. Selecione **Computador Remoto** no menu suspenso do destino de implantação ![Destino de implantação no computador remoto no Visual Studio](images/remotemachinesetting.png)
3. Para projetos C++ e JavaScript, acesse **Projeto > Propriedades > Propriedades de Configuração > Depuração**. Para projetos C#, uma caixa de diálogo será exibida automaticamente para configurar a conexão.
  a. Insira o endereço IP do dispositivo no campo **Endereço** ou **Nome do Computador**. Localize o endereço IP no HoloLens em **Configurações > Rede e Internet > Opções Avançadas** ou pergunte à Cortana "Qual é meu endereço IP?"
  b. Defina o Modo de Autenticação como **Universal (Protocolo não criptografado)** ![caixa de diálogo Conexão remota no Visual Studio](images/remotedeploy.png)
4. Selecione **Depurar > Iniciar a depuração** para implantar o aplicativo e iniciar a depuração![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)
5. Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN. Siga as instruções de **Como emparelhar o dispositivo** abaixo.

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Como implantar um aplicativo via Wi-Fi – HoloLens 2
1. Selecione uma configuração de build **ARM** ou **ARM64** para o aplicativo ![configuração de build ARM64 no Visual Studio](images/arm64setting.png)
2. Selecione **Computador Remoto** no menu suspenso do destino de implantação ![Destino de implantação no computador remoto no Visual Studio](images/remotemachinesetting_arm64.png)
3. Para projetos C++ e JavaScript, acesse **Projeto > Propriedades > Propriedades de Configuração > Depuração**. Para projetos C#, uma caixa de diálogo será exibida automaticamente para configurar a conexão.
  a. Insira o endereço IP do dispositivo no campo **Endereço** ou **Nome do Computador**. Localize o endereço IP no HoloLens em **Configurações > Rede e Internet > Opções Avançadas** ou pergunte à Cortana "Qual é meu endereço IP?"
  b. Defina o Modo de Autenticação como **Universal (Protocolo não criptografado)** ![caixa de diálogo Conexão remota no Visual Studio](images/remotedeploy.png)
4. Selecione **Depurar > Iniciar a depuração** para implantar o aplicativo e iniciar a depuração![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)
5. Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN. Siga as instruções de **Como emparelhar o dispositivo** abaixo.

Se o endereço IP do HoloLens for alterado, você poderá alterar o endereço IP do computador de destino acessando **Projeto > Propriedades > Propriedades de Configuração > Depuração**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Como implantar um aplicativo via USB – HoloLens (1ª geração)
1. Selecione uma configuração de build **x86** para o aplicativo ![Configuração de build x86 no Visual Studio](images/x86setting.png)
2. Selecione **Dispositivo** no menu suspenso do destino de implantação![Implantação de dispositivo no Visual Studio](images/buildsettingsusbdeploy.png)
3. Selecione **Depurar > Iniciar a depuração** para implantar o aplicativo e iniciar a depuração![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)
4. Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN. Siga as instruções de **Como emparelhar o dispositivo** abaixo.

## <a name="deploying-an-app-over-usb---hololens-2"></a>Como implantar um aplicativo via USB – HoloLens 2
1. Selecione uma configuração de build **ARM** ou **ARM64** para o aplicativo ![configuração de build ARM64 no Visual Studio](images/arm64setting.png)
2. Selecione **Dispositivo** no menu suspenso do destino de implantação![Implantação de dispositivo no Visual Studio](images/buildsettingsusbdeploy_arm64.png)
3. Selecione **Depurar > Iniciar a depuração** para implantar o aplicativo e iniciar a depuração![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)
4. Na primeira vez que implantar um aplicativo no HoloLens por meio do computador, você deverá fornecer um PIN. Siga as instruções de **Como emparelhar o dispositivo** abaixo.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Como implantar um aplicativo no computador local – headset imersivo

Siga estas instruções ao usar um headset imersivo do Windows Mixed Reality que se conecta ao computador ou o [simulador de realidade misturada](using-the-windows-mixed-reality-simulator.md). Nesses casos, basta implantar e executar o aplicativo no computador local.
1. Selecione uma configuração de build **x86** ou **x64** para o aplicativo
2. Selecione **Computador Local** no menu suspenso do destino de implantação
3. Selecione **Depurar > Iniciar depuração** para implantar o aplicativo e iniciar a depuração

## <a name="pairing-your-device"></a>Como emparelhar o dispositivo

Na primeira vez que implantar um aplicativo no HoloLens por meio do Visual Studio, você deverá fornecer um PIN. No HoloLens, gere um PIN iniciando o aplicativo Configurações, acesse **Atualizar > Para Desenvolvedores** e toque em **Emparelhar**. Um PIN será exibido no HoloLens; digite este PIN no Visual Studio. Após a conclusão do emparelhamento, toque em **Concluído** no HoloLens para ignorar a caixa de diálogo. Este computador agora está emparelhado com o HoloLens, e você poderá implantar aplicativos automaticamente. Repita essas etapas para todos os computadores seguintes usados para implantar aplicativos no HoloLens.

Para desemparelhar o HoloLens de todos os computadores com os quais ele foi emparelhado, inicie o aplicativo **Configurações**, acesse **Atualizar > Para Desenvolvedores** e toque em **Limpar**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Como implantar um aplicativo no Emulador do HoloLens (1ª geração)
1. Verifique se você **[instalou o Emulador do HoloLens](install-the-tools.md)** .
2. Selecione uma configuração de build **x86** para o aplicativo.
![Configuração de build x86 no Visual Studio](images/x86setting.png)
3. Selecione **Emulador do HoloLens** no menu suspenso do destino de implantação![Destino do emulador no Visual Studio](images/deployemulator.png)
4. Selecione **Depurar > Iniciar a depuração** para implantar o aplicativo e iniciar a depuração![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Como implantar um aplicativo no Emulador do HoloLens 2
1. Verifique se você **[instalou o Emulador do HoloLens](install-the-tools.md)** .
2. Selecione uma configuração de build **x86** ou **x64** para o aplicativo.
![Configuração de build x86 no Visual Studio](images/x86setting.png)
3. Selecione **Emulador do HoloLens 2** no menu suspenso do destino de implantação![Destino do emulador no Visual Studio](images/deployemulator2.png)
4. Selecione **Depurar > Iniciar a depuração** para implantar o aplicativo e iniciar a depuração![Iniciar sem Depuração no Visual Studio](images/deploywithdebugging.png)

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Depurador de Gráficos do HoloLens (1ª geração)

As ferramentas Diagnóstico de Gráficos do Visual Studio são muito úteis ao escrever e otimizar um aplicativo holográfico. Confira [Diagnóstico de Gráficos do Visual Studio no MSDN](https://msdn.microsoft.com/library/hh315751.aspx) para obter detalhes completos.

**Para iniciar o Depurador de Gráficos**
1. Siga as instruções acima para definir um dispositivo ou um emulador como destino
2. Acesse **Depurar > Gráficos > Iniciar Diagnóstico**
3. Na primeira vez que fizer isso com um HoloLens, talvez você receba um erro de "acesso negado". Reinicialize o HoloLens para permitir que as permissões atualizadas entrem em vigor e tente novamente.

## <a name="profiling"></a>Criação de perfil

As ferramentas de criação de perfil do Visual Studio permitem que você analise o desempenho e o uso de recursos do seu aplicativo. Isso inclui ferramentas para otimizar a CPU, a memória, os elementos gráficos e o uso da rede. Confira [Executar ferramentas de diagnóstico sem depuração no MSDN](https://msdn.microsoft.com/library/dn957936.aspx) para obter detalhes completos.

**Para iniciar as ferramentas de criação de perfil com o HoloLens**
1. Siga as instruções acima para definir um dispositivo ou um emulador como destino
2. Acesse **Depurar > Iniciar Ferramentas de Diagnóstico sem Depuração...**
3. Selecione as ferramentas que deseja usar
4. Clique em **Iniciar**
5. Na primeira vez que fizer isso com um HoloLens, talvez você receba um erro de "acesso negado". Reinicialize o HoloLens para permitir que as permissões atualizadas entrem em vigor e tente novamente.

## <a name="debugging-an-installed-or-running-app"></a>Como depurar um aplicativo instalado ou em execução

Use o Visual Studio para depurar um aplicativo universal do Windows que é instalado sem a implantação por meio de um projeto do Visual Studio. Isso será útil se você quiser depurar um pacote do aplicativo instalado ou um aplicativo que já esteja em execução.
1. Acesse **Depurar -> Outros Destinos de Depuração-> Depurar Pacote do Aplicativo Instalado**
2. Selecione o destino **Computador Remoto** para o HoloLens ou **Computador Local** para headsets imersivos.
3. Insira o endereço IP do **dispositivo**
4. Escolha o Modo de Autenticação **Universal**
5. A janela mostrará os aplicativos em execução e inativos. Escolha aquele que deseja depurar.
6. Escolha o tipo de código para depuração (Gerenciado, Nativo, Misto)
7. Clique em **Anexar** ou **Iniciar**

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Como implantar e depurar aplicativos UWP (Plataforma Universal do Windows)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Habilitar o dispositivo para desenvolvimento](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)

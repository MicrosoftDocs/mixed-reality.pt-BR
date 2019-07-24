---
title: Usando o Visual Studio para implantar e depurar
description: Como compilar, depurar e implantar aplicativos para o HoloLens e o Windows Mixed Reality usando o Visual Studio.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, realidade misturada, depurar, implantar
ms.openlocfilehash: 36ed428d69802084c3b953ac2fdce46844dfdc88
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387730"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Usando o Visual Studio para implantar e depurar

Se você deseja usar o DirectX ou o Unity para desenvolver seu aplicativo de realidade misturada, você usará o Visual Studio para depuração e implantação. Nesta seção, você aprenderá a:
* Como implantar aplicativos para seu HoloLens ou o headset de imersão de realidade misturada do Windows por meio do Visual Studio.
* Como usar o emulador do HoloLens interno para o Visual Studio.
* Como depurar aplicativos de realidade misturada.

## <a name="prerequisites"></a>Pré-requisitos
1. Consulte [instalar as ferramentas](install-the-tools.md) para obter instruções de instalação.
2. Crie um novo projeto de aplicativo universal do Windows no Visual Studio 2015 atualização 1, Visual Studio 2017 ou Visual Studio 2019. C#, C++e os projetos JavaScript têm suporte. (Ou siga as instruções para [criar uma compilação de um aplicativo no Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Habilitar o modo de desenvolvedor

Comece habilitando o **modo de desenvolvedor** em seu dispositivo para que o Visual Studio possa se conectar a ele.

### <a name="hololens"></a>HoloLens
1. Ligue seu HoloLens e coloque-o no dispositivo.
2. Faça o gesto [bloom](gestures.md#bloom) para iniciar o menu principal.
3. Olhar no bloco **configurações** e execute o gesto de [toque de ar](gestures.md#air-tap) . Faça um segundo air tap para colocar o aplicativo em seu ambiente. O aplicativo Configurações será iniciado depois disso.
4. Selecione item de menu **Atualização**.
5. Selecione o item de menu **Para desenvolvedores**.
6. Habilite o **Modo de Desenvolvedor**. Isso permitirá que você [implante aplicativos do Visual Studio](using-visual-studio.md) em seu HoloLens.
7. Opcional: Role para baixo e habilite também o **portal do dispositivo**. Isso também permitirá que você se conecte ao [portal do dispositivo Windows](using-the-windows-device-portal.md) no seu HoloLens em um navegador da Web.

### <a name="windows-pc"></a>Computador Windows

Se você estiver trabalhando com um headset de realidade mista do Windows conectado ao seu PC, deverá habilitar o **modo de desenvolvedor** no PC.
1. Ir para **configurações**
2. Selecionar **atualização e segurança**
3. Selecionar **para desenvolvedores**
4. Habilite o **modo de desenvolvedor**, leia o aviso de isenção para a configuração escolhida e clique em Sim para aceitar a alteração.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Implantando um aplicativo por Wi-Fi-HoloLens (1ª gen)
1. Selecione uma configuração de Build **x86** para sua ![configuração de Build do aplicativo x86 no Visual Studio](images/x86setting.png)
2. Selecione **computador remoto** no menu ![suspenso destino de implantação destino de implantação de máquina remota no Visual Studio](images/remotemachinesetting.png)
3. Para C++ projetos do e do JavaScript, vá para **projeto > Propriedades > propriedades de configuração > depuração**. Para C# projetos, uma caixa de diálogo será automaticamente exibida para configurar sua conexão.
  a. Insira o endereço IP do seu dispositivo no campo nome do **computador** ou **endereço** . Localize o endereço IP em seu HoloLens em **configurações > rede & Internet > opções avançadas**ou você pode solicitar ao Cortana "Qual é meu endereço IP?"
  b. Definir o modo de autenticação para a caixa de diálogo de conexão remota **(protocolo não criptografado)** ![no Visual Studio](images/remotedeploy.png)
4. Selecione **Depurar > iniciar a depuração** para implantar seu aplicativo e iniciar![depuração iniciar sem depuração no Visual Studio](images/deploynodebugging.png)
5. Na primeira vez que você implantar um aplicativo no seu HoloLens do seu PC, você será solicitado a fornecer um PIN. Siga as instruções de **emparelhamento do seu dispositivo** abaixo.

Se o endereço IP do HoloLens for alterado, você poderá alterar o endereço IP do computador de destino indo para **projeto > propriedades > Propriedades de configuração > depuração**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Implantando um aplicativo por meio de USB-HoloLens (1º gen)
1. Selecione uma configuração de Build **x86** para sua ![configuração de Build do aplicativo x86 no Visual Studio](images/x86setting.png)
2. Selecione o **dispositivo** no menu![suspenso destino de implantação implantação de dispositivo no Visual Studio](images/buildsettingsusbdeploy.png)
3. Selecione **Depurar > iniciar a depuração** para implantar seu aplicativo e iniciar![depuração iniciar sem depuração no Visual Studio](images/deploynodebugging.png)
4. Na primeira vez que você implantar um aplicativo no seu HoloLens do seu PC, você será solicitado a fornecer um PIN. Siga as instruções de **emparelhamento do seu dispositivo** abaixo.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Implantando um aplicativo em seu PC local-headsets de imersão

Siga estas instruções ao usar um headset de imersão de realidade mista do Windows que se conecta ao seu PC ou ao simulador de [realidade misturada](using-the-windows-mixed-reality-simulator.md). Nesses casos, basta implantar e executar seu aplicativo no PC local.
1. Selecione uma configuração de compilação **x86** ou **x64** para seu aplicativo
2. Selecione **computador local** no menu suspenso destino de implantação
3. Selecione **depurar > iniciar a depuração** para implantar seu aplicativo e iniciar a depuração

## <a name="pairing-your-device---hololens-1st-gen"></a>Emparelhamento de seu dispositivo-HoloLens (1ª gen)

Na primeira vez que você implantar um aplicativo do Visual Studio para seu HoloLens, você será solicitado a fornecer um PIN. No HoloLens, gere um PIN iniciando o aplicativo configurações, vá para **atualizar > para desenvolvedores** e toque em emparelhar . Um PIN será exibido em seu HoloLens; Digite este PIN no Visual Studio. Após a conclusão do emparelhamento, toque em **concluído** em seu HoloLens para ignorar a caixa de diálogo. Este computador agora está emparelhado com o HoloLens e você poderá implantar aplicativos automaticamente. Repita essas etapas para todos os computadores subsequentes que são usados para implantar aplicativos em seu HoloLens.

Para desemparelhar seu HoloLens de todos os computadores com os quais ele foi emparelhado, inicie o aplicativo **configurações** , vá para **Atualizar > para desenvolvedores** e toque em **claro**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Implantando um aplicativo no emulador do HoloLens (1º gen)
1. Verifique se você **[instalou o emulador do HoloLens](install-the-tools.md)** .
2. Selecione uma configuração de compilação **x86** para seu aplicativo.
![configuração de build x86 no Visual Studio](images/x86setting.png)
3. Selecione o emulador do **HoloLens** no menu![suspenso destino de implantação destino do emulador no Visual Studio](images/deployemulator.png)
4. Selecione **Depurar > iniciar a depuração** para implantar seu aplicativo e iniciar![depuração iniciar sem depuração no Visual Studio](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>Depurador de gráficos

As ferramentas de Diagnóstico de Gráficos do Visual Studio são muito úteis ao escrever e otimizar um aplicativo Holographic. Consulte o [Visual Studio diagnóstico de gráficos no MSDN](https://msdn.microsoft.com/library/hh315751.aspx) para obter detalhes completos.

**Para iniciar o depurador de gráficos**
1. Siga as instruções acima para direcionar um dispositivo ou emulador
2. Vá para **depurar > gráficos > iniciar diagnóstico**
3. Na primeira vez que você fizer isso com um HoloLens, você poderá receber um erro de "acesso negado". Reinicialize seu HoloLens para permitir que as permissões atualizadas entrem em vigor e tente novamente.

## <a name="profiling"></a>Perfil

As ferramentas de criação de perfil do Visual Studio permitem que você analise o desempenho e o uso de recursos do seu aplicativo. Isso inclui ferramentas para otimizar a CPU, a memória, os gráficos e o uso da rede. Consulte [executar ferramentas de diagnóstico sem depuração no MSDN](https://msdn.microsoft.com/library/dn957936.aspx) para obter detalhes completos.

**Para iniciar o Ferramentas de Criação de Perfil com o HoloLens**
1. Siga as instruções acima para direcionar um dispositivo ou emulador
2. Vá para **Debug > iniciar ferramentas de diagnóstico sem depuração...**
3. Selecione as ferramentas que você deseja usar
4. Clique em **Iniciar**
5. Na primeira vez que você fizer isso com um HoloLens, você poderá receber um erro de "acesso negado". Reinicialize seu HoloLens para permitir que as permissões atualizadas entrem em vigor e tente novamente.

## <a name="debugging-an-installed-or-running-app"></a>Depurando um aplicativo instalado ou em execução

Você pode usar o Visual Studio para depurar um aplicativo universal do Windows que é instalado sem a implantação de um projeto do Visual Studio. Isso será útil se você quiser depurar um pacote do aplicativo instalado ou se quiser depurar um aplicativo que já esteja em execução.
1. Vá para **depuração-> outros destinos de depuração-> depurar pacote do aplicativo instalado**
2. Selecione o destino da **máquina remota** para o HoloLens ou **computador local** para headsets de imersão.
3. Insira o **endereço IP** do dispositivo
4. Escolha o modo de autenticação **Universal**
5. A janela mostra os aplicativos em execução e inativos. Escolha aquela que você deseja depurar.
6. Escolha o tipo de código a ser depurado (gerenciado, nativo, misto)
7. Clique em **anexar** ou **Iniciar**

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Implantando e Depurando aplicativos Plataforma Universal do Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Habilitar seu dispositivo para desenvolvimento](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)

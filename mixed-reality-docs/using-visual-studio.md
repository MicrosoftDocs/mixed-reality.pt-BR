---
title: Usando o Visual Studio para implantar e depurar
description: Como compilar, depurar e implantar aplicativos para o HoloLens e realidade mista do Windows usando o Visual Studio.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, realidade mista, depurar, implantar
ms.openlocfilehash: 6bd47d7212d321791a11ff4db91c3e172c91f463
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589846"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Usando o Visual Studio para implantar e depurar

Se você quiser usar DirectX ou Unity para desenvolver seu aplicativo de realidade misturada, você usará o Visual Studio para depuração e implantação. Nesta seção, você aprenderá:
* Como implantar aplicativos no HoloLens ou Windows Mixed Reality imersivo fone de ouvido por meio do Visual Studio.
* Como usar o emulador do HoloLens integrado ao Visual Studio.
* Como depurar aplicativos de realidade misturada.

## <a name="prerequisites"></a>Pré-requisitos
1. Ver [instalar as ferramentas](install-the-tools.md) para instruções de instalação.
2. Crie um novo projeto de aplicativo Windows Universal no Visual Studio 2015 atualização 1 ou o Visual Studio 2017. C#, C++, e projetos em JavaScript são suportados. (Ou siga as instruções para [criar um aplicativo de uma compilação no Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Habilitar o modo de desenvolvedor

Inicie permitindo **modo de desenvolvedor** em seu dispositivo para Visual Studio possa se conectar a ele.

### <a name="hololens"></a>HoloLens
1. Ative o HoloLens e colocado no dispositivo.
2. Faça o gesto [bloom](gestures.md#bloom) para iniciar o menu principal.
3. Mantenha o foco na **as configurações** lado a lado e executar o [polegar](gestures.md#air-tap) gesto. Faça um segundo air tap para colocar o aplicativo em seu ambiente. O aplicativo Configurações será iniciado depois disso.
4. Selecione item de menu **Atualização**.
5. Selecione o item de menu **Para desenvolvedores**.
6. Habilite o **Modo de Desenvolvedor**. Isso permitirá que você [implantar aplicativos do Visual Studio](using-visual-studio.md) para o HoloLens.
7. Opcional: Role para baixo e também permitem **Portal do dispositivo**. Isso também permitirá que a conexão com o [Windows Device Portal](using-the-windows-device-portal.md) em seu HoloLens em um navegador da web.

### <a name="windows-pc"></a>Computador Windows

Se você estiver trabalhando com um headset de realidade mista do Windows conectado ao seu computador, você deve habilitar **modo de desenvolvedor** no PC.
1. Vá para **configurações**
2. Selecione **atualização e segurança**
3. Selecione **para desenvolvedores**
4. Habilitar **modo de desenvolvedor**, leia o aviso de isenção para a configuração escolhida e, em seguida, clique em Sim para aceitar a alteração.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Implantando um aplicativo por Wi-Fi - HoloLens (1ª geração)
1. Selecione uma **x86** compilar a configuração do seu aplicativo ![x86 compilar a configuração no Visual Studio](images/x86setting.png)
2. Selecione **computador remoto** no menu de lista suspensa de destino de implantação ![destino de implantação do computador remoto no Visual Studio](images/remotemachinesetting.png)
3. Para C++ e projetos em JavaScript, acesse **projeto > Propriedades > Propriedades de configuração > Debugging**. Para C# projetos, uma caixa de diálogo será automaticamente pop-up para configurar sua conexão.
  a. Insira o endereço IP do seu dispositivo na **endereço** ou **nome da máquina** campo. Localizar o endereço IP em seu HoloLens sob **Configurações > rede e Internet > Opções avançadas de**, ou você pode perguntar ao Cortana "Qual é meu endereço IP?"
  b. Definir o modo de autenticação **Universal (protocolo não criptografado)**![caixa de diálogo de conexão remota no Visual Studio](images/remotedeploy.png)
4. Selecione **Depurar > Iniciar depuração** para implantar seu aplicativo e iniciar a depuração![iniciar sem depuração no Visual Studio](images/deploynodebugging.png)
5. Na primeira vez que você implanta um aplicativo para o HoloLens do seu computador, você será solicitado um PIN. Siga as **emparelhar seu dispositivo** instruções a seguir.

Se seu endereço HoloLens IP for alterado, você pode alterar o endereço IP do computador de destino, acessando **projeto > Propriedades > Propriedades de configuração > depuração**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Implantando um aplicativo por USB - HoloLens (1ª geração)
1. Selecione uma **x86** compilar a configuração do seu aplicativo ![x86 compilar a configuração no Visual Studio](images/x86setting.png)
2. Selecione **dispositivo** no menu de lista suspensa de destino de implantação![implantação de dispositivo no Visual Studio](images/buildsettingsusbdeploy.png)
3. Selecione **Depurar > Iniciar depuração** para implantar seu aplicativo e iniciar a depuração![iniciar sem depuração no Visual Studio](images/deploynodebugging.png)
4. Na primeira vez que você implanta um aplicativo para o HoloLens do seu computador, você será solicitado um PIN. Siga as **emparelhar seu dispositivo** instruções a seguir.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Implantando um aplicativo em seu computador Local - imersivo fone de ouvido

Siga estas instruções ao usar um Windows Mixed Reality imersivo fone de ouvido que se conecta ao seu PC ou o [simulador de realidade misturada](using-the-windows-mixed-reality-simulator.md). Nesses casos, implantar e executar seu aplicativo no computador local.
1. Selecione uma **x86** ou **x64** compilar a configuração do seu aplicativo
2. Selecione **computador Local** no menu de lista suspensa de destino de implantação
3. Selecione **Depurar > Iniciar depuração** para implantar seu aplicativo e iniciar a depuração

## <a name="pairing-your-device---hololens-1st-gen"></a>Emparelhamento do seu dispositivo - HoloLens (1ª geração)

Na primeira vez que você implanta um aplicativo do Visual Studio para o HoloLens, você será solicitado um PIN. Em HoloLens, gerar um PIN ao iniciar o aplicativo de configurações, vá para **atualização > para desenvolvedores** e toque no **par**. Um PIN será exibido no seu HoloLens; Digite esse PIN no Visual Studio. Após o emparelhamento for concluído, toque em **feito** em seu HoloLens para ignorar a caixa de diálogo. Este PC agora é emparelhado com o HoloLens e você poderá implantar aplicativos automaticamente. Repita essas etapas para cada PC subsequente que é usado para implantar aplicativos para o HoloLens.

Para un-par iniciar os HoloLens de todos os computadores que ele foi associado a **as configurações** aplicativo, vá para **atualização > para desenvolvedores** e toque no **clara**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Implantando um aplicativo para o HoloLens (1º gen) emulador
1. Verifique se você tem  **[instalou o emulador do HoloLens](install-the-tools.md)**.
2. Selecione uma **x86** compilar a configuração do seu aplicativo.
![x86 compilar a configuração no Visual Studio](images/x86setting.png)
3. Selecione **HoloLens emulador** no menu de lista suspensa de destino de implantação![destino de emulador no Visual Studio](images/deployemulator.png)
4. Selecione **Depurar > Iniciar depuração** para implantar seu aplicativo e iniciar a depuração![iniciar sem depuração no Visual Studio](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>Depurador de gráficos

As ferramentas de diagnóstico de gráficos do Visual Studio são muito úteis durante a gravação e otimizar um aplicativo Holographic. Ver [diagnóstico de gráficos do Visual Studio no MSDN](https://msdn.microsoft.com/library/hh315751.aspx) para obter detalhes completos.

**Para iniciar o depurador de gráficos**
1. Siga as instruções acima para um dispositivo ou emulador de destino
2. Vá para **Depurar > gráficos > Iniciar diagnóstico**
3. Na primeira vez em que você pode fazer isso com um HoloLens, você pode receber um erro "acesso negado". Reinicialize o HoloLens para permitir que as permissões atualizadas entrar em vigor e tente novamente.

## <a name="profiling"></a>Criação de perfil

As ferramentas de criação de perfil do Visual Studio permitem que você analise o uso de recursos e desempenho do seu aplicativo. Isso inclui ferramentas para otimizar a CPU, memória, gráficos e uso de rede. Ver [executar ferramentas de diagnóstico sem depuração no MSDN](https://msdn.microsoft.com/library/dn957936.aspx) para obter detalhes completos.

**Para iniciar as ferramentas de criação de perfil com HoloLens**
1. Siga as instruções acima para um dispositivo ou emulador de destino
2. Vá para **Depurar > iniciar ferramentas de diagnóstico sem depuração...**
3. Selecione as ferramentas que você deseja usar
4. Clique em **iniciar**
5. Na primeira vez em que você pode fazer isso com um HoloLens, você pode receber um erro "acesso negado". Reinicialize o HoloLens para permitir que as permissões atualizadas entrar em vigor e tente novamente.

## <a name="debugging-an-installed-or-running-app"></a>Depurar um aplicativo instalado ou em execução

Você pode usar o Visual Studio para depurar um aplicativo Windows Universal que é instalado sem implantar a partir de um projeto do Visual Studio. Isso é útil se você quiser depurar um pacote do aplicativo instalado, ou se você quiser depurar um aplicativo que já está em execução.
1. Vá para **Depurar -> outra depuração destinos -> Depurar pacote do aplicativo instalado**
2. Selecione o **computador remoto** alvo para HoloLens ou **Máquina Local** para fones imersivos em exposição.
3. Insira o seu dispositivo **endereço IP**
4. Escolha o **Universal** modo de autenticação
5. A janela mostra os aplicativos em execução e inativos. Escolha a que o que você deseja depurar.
6. Escolha o tipo de código para depurar (gerenciados, nativos, Mixed)
7. Clique em **anexe** ou **iniciar**

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* [Usando o emulador do HoloLens](using-the-hololens-emulator.md)
* [Implantar e depurar aplicativos da plataforma Universal do Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Habilitar seu dispositivo para desenvolvimento](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)

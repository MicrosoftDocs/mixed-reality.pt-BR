---
title: Usando o emulador do HoloLens
description: O emulador do HoloLens permite testar aplicativos de realidade misturada em seu computador sem um HoloLens físico.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: HoloLens, emulator
ms.openlocfilehash: 0a8fa6bb7c7c5bb846604b7a1878911f028d8cba
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580649"
---
# <a name="using-the-hololens-emulator"></a>Usando o emulador do HoloLens

O emulador do HoloLens permite que você teste holográfico aplicativos em seu computador sem um HoloLens físico e é fornecido com o conjunto de ferramentas de desenvolvimento HoloLens. O emulador usa uma máquina virtual Hyper-V. As entradas humanas e ambientais que normalmente seriam lidos pelos sensores no HoloLens em vez disso, são simuladas usando seu teclado, mouse ou controlador do Xbox. Aplicativos não precisam ser modificado para ser executado no emulador e não souber o que eles não estão sendo executados em um HoloLens real.

Se você pretende para desenvolver aplicativos do Windows Mixed Reality imersivos (VR) fone de ouvido ou jogos para PCs desktop, confira a [simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), que permite que você simule headsets da área de trabalho em vez disso.


## <a name="installing-the-hololens-emulator"></a>Instalação do emulador do HoloLens
Baixe o emulador do HoloLens e modelos de projeto holographic.

Versões: 
* [Emulador do HoloLens 2 e modelos de projeto holográfica](https://go.microsoft.com/fwlink/?linkid=2087187).
* [Emulador do HoloLens (1º Gen) e modelos de projeto holográfica](https://go.microsoft.com/fwlink/?linkid=2065980).

Você pode encontrar versões mais antigas do emulador do HoloLens sobre o [HoloLens emulador de arquivo](hololens-emulator-archive.md) página.

### <a name="hololens-emulator-system-requirements"></a>Requisitos de sistema do emulador do HoloLens

O emulador do HoloLens usa o Hyper-V com o RemoteFx (1º Gen emulador) ou acelerado de GPU PV (emulador de 2 HoloLens) para hardware de gráficos. Para usar o emulador, verifique se que seu PC atende a esses requisitos de hardware:
* 64-bit Windows 10 Pro, Enterprise ou educação 
    >[!NOTE]
    >Windows 10 Home edition não oferece suporte a Hyper-V ou o emulador do HoloLens.  
    >O emulador do HoloLens 2 exige o Windows 10 de outubro de 2018 update ou mais recente.
* CPU de 64 bits
* CPU com 4 núcleos (ou várias CPUs com um total de 4 núcleos)
* 8 GB de RAM ou mais
* No BIOS, os recursos a seguir devem ser [com suporte e habilitado](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Virtualização assistida por hardware
   * Conversão de Endereços de Segundo Nível (SLAT)
   * Prevenção de Execução de Dados baseados em hardware (DEP)
* Requisitos de GPU
   * DirectX 11.0 ou posterior
   * Driver de gráficos do WDDM 1.2 ou posterior (1º Gen)
   * Driver de gráficos do WDDM 2.5 (HoloLens 2 emulador)
   * O emulador pode funcionar com uma GPU sem suporte, mas pode ser significativamente mais lento

Se seu sistema atende aos requisitos acima, **Certifique-se de que o recurso de "Hyper-V" foi habilitado em seu sistema** por meio do painel de controle -> Programas -> Programas e recursos -> Ativar recursos do Windows ou off -> Certifique-se Se "Hyper-V" está selecionado para a instalação do emulador para ter êxito.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Implantação de aplicativos para o emulador do HoloLens

1. Carrega sua solução de aplicativo no Visual Studio.
    >[!NOTE]
    >Ao usar o Unity, compile o projeto do Unity e, em seguida, carregue a solução criada no Visual Studio como de costume.
2. Para o emulador do HoloLens (1º Gen), verifique se a plataforma é definida como **x86**. O emulador de 2 HoloLens Certifique-se a plataforma é definida como **x86** ou **x64**.
3. Selecione o desejado **HoloLens emulador** versão como o dispositivo de destino para a depuração.
4. Vá para **Depurar > Iniciar depuração** ou pressione **F5** para iniciar o emulador e implantar seu aplicativo para depuração.

O emulador pode levar um minuto ou mais para inicializar ao iniciar pela primeira vez. É recomendável que você mantenha o emulador aberto durante a sessão de depuração para que você pode implantar rapidamente aplicativos para o emulador em execução.

## <a name="basic-emulator-input"></a>Entrada de emulador básico

Controlar o emulador é muito semelhante a muitos jogos de vídeo 3D comuns. Há opções de entrada disponíveis usando o teclado, mouse ou controlador do Xbox. Você pode controlar o emulador, direcionando as ações de um usuário simulado usando um HoloLens. Suas ações Mover usuário simulado ao redor e aplicativos em execução no emulador de respondem, como faria em um dispositivo real.

O cursor no HoloLens (1º Gen) segue a movimentação do cabeçote e rotação.  No emulador 2 HoloLens, o cursor segue o movimento de mão e orientação.

* **Percorrer para frente, novamente, à esquerda e logo** -usar W, D, S e um teclas do teclado ou o pen drive à esquerda em um controlador do Xbox.
* **Pesquisar, para baixo, esquerda e o botão direito do mouse** -clicar e arrastar o mouse, use as teclas de direção no teclado ou o pen drive à direita em um controlador do Xbox.
* **Gestos de toque de ar** – com o botão direito do mouse, pressione a tecla Enter no teclado ou usar o botão em um controlador do Xbox.
* **Gesto do sistema/bloom** – pressione a tecla do Windows ou F2 no teclado ou pressione o botão de B em um controlador do Xbox.
* **Entregar o movimento de rolagem** - mantenha pressionada a tecla Alt, mantenha pressionado o botão direito do mouse, arraste o mouse para cima / para baixo, ou em um controlador do Xbox pressionado o gatilho certo e um botão para baixo e mover o pen drive certo para cima para baixo.
* **Entregar a movimentação e a orientação** (apenas 2 HoloLens emulador) - mantenha pressionada a tecla Alt e arraste o mouse para cima / baixo / à esquerda / direito para ir a mão ou usar as teclas de direção e Q / E girar e inclinar a mão.  Para um controlador do Xbox, mantenha o Amortecedor esquerda ou direita e usar o analógico esquerdo para mover a mão esquerda / direita / encaminhamento / voltar, o analógico certo para girá-lo e para cima / para baixo no Dpad para aumentar ou diminuir a mão.

## <a name="anatomy-of-the-hololens-2-emulator"></a>Anatomia do emulador HoloLens 2 

### <a name="main-window"></a>Janela principal

![Janela principal do emulador do HoloLens 2](images/emulator2-900px.png)

### <a name="toolbar"></a>Barra de ferramentas

À direita da janela principal, você encontrará a barra de ferramentas do emulador. A barra de ferramentas contém os seguintes botões:
* ![Ícone Fechar](images/emulator-close.png) **fechar**: Fecha o emulador.
* ![Ícone de minimizar](images/emulator-minimize.png) **minimizar**: Minimiza a janela do emulador.
* ![Simulation_icon](images/emulator-simulation-panel.png) **painel de controle de simulação**: Mostrar ou ocultar a [painel de controle de simulação](#simulation-control-panel) para configurar e controlar [de entrada para o emulador](#basic-emulator-input).
* ![Ícone de tela de ajustar à](images/emulator-fit.png) **ajustar à tela**: Ajusta o emulador à tela.
* ![Ícone de zoom](images/emulator-zoom.png) **Zoom**: Fazer com que o emulador maiores e menores.
* ![Ícone de Ajuda](images/emulator-help.png) **ajudar**: Abra a Ajuda do emulador.
* ![Ícone do portal de dispositivo aberto](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra o Windows Device Portal para o sistema de operacional HoloLens no emulador.
* ![Ícone de ferramentas](images/emulator-tools.png) **ferramentas**: Abra o **ferramentas adicionais** painel.

### <a name="simulation-control-panel"></a>Painel de controle de simulação

O painel de controle de simulação permite que você exiba a atual posição e orientação dos dispositivos de entrada humanas e simulados simulados.  Ele também permite configurar entrada simulados, como mostrar ou ocultar uma ou ambas as mãos e dispositivos usados para controlar a entrada simulada como teclado, mouse e gamepad do seu computador.

![Painel de controle de simulação](images/emulator-simulation-control-panel.png)

* Para ocultar ou mostrar o painel de simulação, clique no botão de barra de ferramentas ou pressione F7 no teclado.
* Passe o mouse sobre um controle ou um campo para exibir uma dica de ferramenta que contém os controles de teclado, mouse e gamepad para ele.
* Para mostrar ou ocultar uma mão, alterne a opção apropriada à esquerda ou direita.
* Para controlar a mão, use as teclas Alt direita ou esquerdas do teclado ou o Amortecedor esquerdo ou direito no gamepad.
* Para direcionar todas as entradas para uma ou ambas as mãos, clique no botão de pino sob a chave de alternância.  Isso é o equivalente do mantendo pressionada a tecla Alt para a mão.
* Para controlar a direção de olhar olho, clique no apontador na seção "Olhos".  Isso é o equivalente do mantendo pressionada a tecla 'Y' no teclado.
* Para carregar uma sala de gravação, clique no botão "Carregar" na seção "Gravação".  Ver [simulada salas](#simulated-rooms) para obter mais informações.
* Para ajustar a velocidade em que os dispositivos de entrada humanos ou simulados simulados mover ou girar em resposta a teclado, mouse ou gamepad de entrada, clique no ícone de engrenagem ao lado de "Configurações de entrada" e ajustar os controles deslizantes.
* Por padrão, a entrada do teclado controles de entrada humana e simulada simulada.  Para que a entrada do teclado do PC enviada para o HoloLens, desmarque a opção "Use o teclado para simulação".  F4 é a tecla de atalho para essa configuração.
* Se o painel de simulação já estiver visível, pressionando F8 para mover o foco do teclado a ela.
* Para desencaixar o painel de simulação da janela do emulador, clique no botão na parte inferior do painel ou pressione F9 no teclado.  Fechar a janela ou pressionando F9 novamente retornará a janela para o emulador.
* O painel de controle de simulação pode ser iniciado como um aplicativo separado, permitindo que você se conectar e controlar o emulador de 2 HoloLens, um dispositivo 2 HoloLens ou simulação Windows Mixed Reality executando PerceptionSimulationInput.exe de % ProgramFiles(x86) % \ Windows Kits\10\Microsoft XDE\10.0.18362.0\.

### <a name="account-tab"></a>Guia de Notificação

Guia conta permite que você configure o emulador para entrar com uma Account da Microsoft. Isso é útil para testar as APIs que exigem o usuário estar conectado com uma conta.  Ativar/desativar essa opção exigirá que você completamente feche e reinicie o emulador do HoloLens para a configuração tenha efeito.  Se essa opção estiver habilitada, inicializações subsequentes do emulador solicitará a entrada, assim como um usuário faria na primeira vez em que o HoloLens é iniciado.  Para inserir rapidamente suas credenciais usando o teclado do PC, primeiro desative "Use o teclado para simulação" no painel de controle de simulação, ou pressione F4 em seu teclado para ativar ou desativar a configuração de teclado.

### <a name="optional-settings-tab"></a>Guia de configurações opcionais

Na guia Configurações opcionais exibirá um controle para habilitar ou desabilitar o hardware acelerada de elementos gráficos.  Gráfico acelerado de hardware será usado por padrão, se compatível com o driver do adaptador de gráficos do seu PC.  Se o driver do adaptador de seus elementos gráficos não suporta VP de GPU, essa opção não estará visível.

### <a name="diagnostics-tab"></a>Guia Diagnóstico

Na guia diagnóstico mostra o endereço IP do emulador na forma de um link para o Windows Device Portal junto com o status da GPU virtual.


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>Anatomia do HoloLens (1º Gen) emulador

### <a name="main-window"></a>Janela principal

Quando o emulador é iniciado, você verá uma janela que exibe o sistema operacional HoloLens.

![Janela principal do emulador do HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barra de ferramentas

À direita da janela principal, você encontrará a barra de ferramentas do emulador. A barra de ferramentas contém os seguintes botões:
* ![Ícone Fechar](images/emulator-close.png) **fechar**: Fecha o emulador.
* ![Ícone de minimizar](images/emulator-minimize.png) **minimizar**: Minimiza a janela do emulador.
* ![Ícone de entrada humana](images/emulator-control.png) **humana entrada**: Mouse e teclado são usados para simular humana [de entrada para o emulador](#basic-emulator-input).
* ![Ícone de entrada do mouse e teclado](images/emulator-input.png) **entrada de Mouse e teclado**: Entrada de mouse e teclado são passados diretamente para o sistema operacional HoloLens como eventos de teclado e mouse como se tivesse conectado um teclado e mouse Bluetooth.
* ![Ícone de tela de ajustar à](images/emulator-fit.png) **ajustar à tela**: Ajusta o emulador à tela.
* ![Ícone de zoom](images/emulator-zoom.png) **Zoom**: Fazer com que o emulador maiores e menores.
* ![Ícone de Ajuda](images/emulator-help.png) **ajudar**: Abra a Ajuda do emulador.
* ![Ícone do portal de dispositivo aberto](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra o Windows Device Portal para o sistema de operacional HoloLens no emulador.
* ![Ícone de ferramentas](images/emulator-tools.png) **ferramentas**: Abra o **ferramentas adicionais** painel.

### <a name="simulation-tab"></a>Guia de simulação

A guia padrão dentro de **ferramentas adicionais** painel é o **simulação** guia.

![Painel do emulador do HoloLens 'Ferramentas adicionais'](images/emulator-simulation-500px.png)

A guia de simulação mostra o estado atual dos sensores simulados usado para orientar o sistema operacional de HoloLens no emulador. Passar o mouse sobre qualquer valor na guia de simulação fornecerá uma dica de ferramenta que descreve como controlar esse valor.

### <a name="room-tab"></a>Guia sala

O emulador simula a entrada do mundo na forma da malha de simulado "salas" mapeamento espacial. Esta guia permite escolher qual espaço para, em vez de sala de padrão de carga.

![Guia de 'Quartos têm' emulador HoloLens](images/emulator-room-500px.png)

Ver [simulada salas](#simulated-rooms) para obter mais informações.

### <a name="account-tab"></a>Guia de Notificação

Guia conta permite que você configure o emulador para entrar com uma Account da Microsoft. Isso é útil para testar a API que exigem o usuário estar conectado com uma conta. Depois de verificar se a caixa nesta página, inicializações subsequentes do emulador serão que você entrar, exatamente como faria de um usuário na primeira vez que o HoloLens é iniciado.

## <a name="simulated-rooms"></a>Salas simuladas

Salas simuladas são úteis para testar um aplicativo em vários ambientes. Várias salas são fornecidas com o emulador e depois de instalar a emulação, você irá encontrá-los em % ProgramFiles (x86) %\Windows Kits\10\Microsoft XDE\\\Plugins\Rooms (versão). Todos esses ambientes foram capturados em ambientes reais usando um HoloLens:
* **DefaultRoom.xef** -uma sala pequena com uma TV, a tabela de café e dois sofas. Carregado por padrão quando você inicia o emulador.
* **Bedroom1.xef** -um quarto pequeno com um suporte técnico.
* **Bedroom2.xef** -um quarto com um ambiente de tamanho Rainha, cômoda, nightstands e walk-in armário.
* **GreatRoom.xef** -uma sala de excelente grande espaço aberto com sala de estar, mesa de jantar e cozinha.
* **LivingRoom.xef** – uma sala com uma lareira, sofá, armchairs e uma tabela de café com um vaso.

Você também pode registrar seus próprios ambientes para usar no emulador usando a página de simulação do [Windows Device Portal](using-the-windows-device-portal.md) em seu HoloLens (1º Gen).

No emulador, você só verá hologramas que você renderizar e você não verá a sala simulada por trás de hologramas. Isso está em contraste com o HoloLens real onde você pode ver ambos combinado juntos. Se você quiser ver a sala simulada no emulador do HoloLens, você precisará atualizar seu aplicativo para renderizar a malha de mapeamento espacial na cena.

## <a name="troubleshooting"></a>Solução de problemas

Você verá um erro durante a instalação do emulador que você precisa *"Visual Studio 2015 atualização 1 e UWP ferramentas versão 1.2"*. Há três possíveis causas desse erro:
* Você não tem uma versão suficientemente recente do Visual Studio (2019 do Visual Studio, Visual Studio 2017 ou Visual Studio 2015 atualização 1 ou posterior). Para corrigir isso, instale a versão mais recente do Visual Studio.
* Você tem uma versão suficientemente recente do Visual Studio, mas você não tiver instaladas as ferramentas de plataforma Universal do Windows (UWP). Esse é um recurso opcional para o Visual Studio.

Você também poderá ver um erro ao instalar o emulador em uma não-Pro/Enterprise/educação SKU do Windows ou se você não tem o recurso Hyper-V habilitada.
* Leia as [requisitos de sistema](#hololens-emulator-system-requirements) seção acima para um conjunto completo de requisitos.
* Também verifique se que o recurso Hyper-V foi ativado no seu sistema.

Se a instalação for concluída com êxito, mas você não vir o emulador do HoloLens como uma opção para implantação e depuração, verifique o seguinte:
* A configuração de projeto do Visual Studio é definida como x86 (1º dia do HoloLens Gen) ou x86 ou x64 (HoloLens 2 emulador).
* Se usando o Visual Studio de 2019, o conjunto de ferramentas de plataforma em sua configuração de projeto é definido como v142.

Se a instalação for concluída com êxito, mas o Visual Studio exibe um erro ao tentar iniciar o emulador do HoloLens, tente o seguinte:
* Executar o Visual Studio como administrador
* Se você tiver apenas teve 2019 Visual do Studio instalado, verifique se o valor do Registro "KitsRoot10" em HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed raízes aponta para a pasta de arquivos de programas de 32 bits (por exemplo, "C:\Program Files (x86) \Windows Kits \10 ").  Se isso não acontecer, desinstale o emulador do HoloLens, altere o valor do registro para sua pasta de arquivos de programas de 32 bits e reinstale o emulador do HoloLens.  Esse problema é resolvido no Visual Studio 2019 16.0.3.

Se o emulador exibe uma caixa de diálogo de erro "Codificação de bytes inválida" na inicialização:
* Exclua todos os arquivos no %localappdata%\Microsoft\XDE\HCS e tente novamente.

Se sua lista de destino de depuração no Visual Studio está vazia (por exemplo, "Start" é a única opção) e você tiver seguido todas as etapas de solução de problemas acima:
* Exclua a pasta 'ConfigurationCache' em %localappdata%\Microsoft\VisualStudio\\<*id de instalação*> \CoreCon e tente novamente.

Se o sistema congela quando o emulador está iniciando, desative a aceleração de hardware para gráficos de emulador.
* Crie um valor do Registro DWORD chamado "DisableGPU" em HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 e defina seu valor como 1.

## <a name="see-also"></a>Consulte também
* [Entrada avançada do Emulador do HoloLens e do Simulador de Realidade Misturada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Histórico de software do emulador do HoloLens](hololens-emulator-archive.md)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)

---
title: Usando o emulador do HoloLens
description: O emulador do HoloLens permite testar aplicativos de realidade misturada em seu computador sem um HoloLens físico.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, emulator
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590814"
---
# <a name="using-the-hololens-emulator"></a>Usando o emulador do HoloLens

O emulador do HoloLens permite que você teste holográfico aplicativos em seu computador sem um HoloLens físico e é fornecido com o conjunto de ferramentas de desenvolvimento HoloLens. O emulador usa uma máquina virtual Hyper-V. As entradas humanas e ambientais que normalmente seriam lidos pelos sensores no HoloLens em vez disso, são simuladas usando seu teclado, mouse ou controlador do Xbox. Aplicativos não precisam ser modificado para ser executado no emulador e não souber o que eles não estão sendo executados em um HoloLens real.

Se você pretende para desenvolver aplicativos do Windows Mixed Reality imersivos (VR) fone de ouvido ou jogos para PCs desktop, confira a [simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), que permite que você simule headsets da área de trabalho em vez disso.

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

## <a name="installing-the-hololens-emulator"></a>Instalação do emulador do HoloLens

Baixe o [HoloLens (1º gen) emulador e modelos de projeto holográfica](https://go.microsoft.com/fwlink/?linkid=2065980).

Você pode encontrar versões mais antigas do emulador do HoloLens sobre o [arquivo morto de emulador do HoloLens](hololens-emulator-archive.md) página.

### <a name="hololens-emulator-system-requirements"></a>Requisitos de sistema do emulador HoloLens

O emulador do HoloLens se baseia no Hyper-V e usa o RemoteFx para hardware acelerada de elementos gráficos. Para usar o emulador, verifique se que seu PC atende a esses requisitos de hardware:
* 64-bit Windows 10 Pro, Enterprise ou educação 
    >[!NOTE]
    >Windows 10 Home edition não oferece suporte a Hyper-V ou o emulador do HoloLens
* CPU de 64 bits
* CPU com 4 núcleos (ou várias CPUs com um total de 4 núcleos)
* 8 GB de RAM ou mais
* No BIOS, os recursos a seguir devem ser [com suporte e habilitado](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Virtualização assistida por hardware
   * Conversão de Endereços de Segundo Nível (SLAT)
   * Prevenção de Execução de Dados baseados em hardware (DEP)
* Requisitos de GPU (o emulador pode funcionar com uma GPU sem suporte, mas pode ser significativamente mais lento)
   * DirectX 11.0 ou posterior
   * Driver WDDM 1.2 ou posterior

Se seu sistema atende aos requisitos acima, **Certifique-se de que o recurso de "Hyper-V" foi habilitado em seu sistema** por meio do painel de controle -> Programas -> Programas e recursos -> Ativar recursos do Windows ou off -> Certifique-se Se "Hyper-V" está selecionado para a instalação do emulador para ter êxito.

### <a name="installation-troubleshooting"></a>Solucionando problemas de instalação

Você verá um erro durante a instalação do emulador que você precisa *"Visual Studio 2015 atualização 1 e UWP ferramentas versão 1.2"*. Há três possíveis causas desse erro:
* Você não tem uma versão suficientemente recente do Visual Studio (Visual Studio 2017 ou Visual Studio 2015 atualização 1 ou posterior). Para corrigir isso, instale a versão mais recente do Visual Studio.
* Você tem uma versão suficientemente recente do Visual Studio, mas você não tiver instaladas as ferramentas de plataforma Universal do Windows (UWP). Esse é um recurso opcional para o Visual Studio.

Você também poderá ver um erro ao instalar o emulador em uma não-PRO/Enterprise/educação SKU do Windows ou se você não tem o recurso Hyper-V habilitada.
* Leia as [requisitos de sistema](#hololens-emulator-system-requirements) seção acima para um conjunto completo de requisitos.
* Também verifique se que o recurso Hyper-V foi ativado no seu sistema.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Implantação de aplicativos para o emulador do HoloLens

1. Carrega sua solução de aplicativo no Visual Studio 2015.
    >[!NOTE]
    >Ao usar o Unity, compile o projeto do Unity e, em seguida, carregue a solução criada no Visual Studio como de costume.
2. Verifique se a plataforma é definida como **x86**.
3. Selecione o **HoloLens emulador** como dispositivo de destino para a depuração.
4. Vá para **Depurar > Iniciar depuração** ou pressione **F5** para iniciar o emulador e implantar seu aplicativo para depuração.

O emulador pode levar um minuto ou mais para inicializar ao iniciar pela primeira vez. É recomendável que você mantenha o emulador aberto durante a sessão de depuração para que você pode implantar rapidamente aplicativos para o emulador em execução.

## <a name="basic-emulator-input"></a>Entrada de emulador básico

Controlar o emulador é muito semelhante a muitos jogos de vídeo 3D comuns. Há opções de entrada disponíveis usando o teclado, mouse ou controlador do Xbox. Você pode controlar o emulador, direcionando as ações de um usuário simulado usando um HoloLens. Suas ações Mover usuário simulado ao redor e aplicativos em execução no emulador de respondem, como faria em um dispositivo real.
* **Percorrer para frente, novamente, à esquerda e logo** -usar W, D, S e um teclas do teclado ou o pen drive à esquerda em um controlador do Xbox.
* **Pesquisar, para baixo, esquerda e o botão direito do mouse** -clicar e arrastar o mouse, use as teclas de direção no teclado ou o pen drive à direita em um controlador do Xbox.
* **Gestos de toque de ar** – com o botão direito do mouse, pressione a tecla Enter no teclado ou usar o botão em um controlador do Xbox.
* **Desabrochassem gesto** – pressione a tecla do Windows ou F2 no teclado ou pressione o botão de B em um controlador do Xbox.
* **Entregar o movimento de rolagem** - mantenha pressionada a tecla Alt, mantenha pressionado o botão direito do mouse, arraste o mouse para cima / para baixo, ou em um controlador do Xbox pressionado o gatilho certo e um botão para baixo e mover o pen drive certo para cima para baixo.

## <a name="anatomy-of-the-hololens-emulator"></a>Anatomia do emulador do HoloLens

### <a name="main-window"></a>Janela principal

Quando o emulador é iniciado, você verá uma janela que exibe o sistema operacional HoloLens.

![Janela principal do emulador HoloLens](images/emulator-890px.png)

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

![Painel do HoloLens emulador 'Ferramentas adicionais'](images/emulator-simulation-500px.png)

A guia de simulação mostra o estado atual dos sensores simulados usado para orientar o sistema operacional de HoloLens no emulador. Passar o mouse sobre qualquer valor na guia de simulação fornecerá uma dica de ferramenta que descreve como controlar esse valor.

### <a name="room-tab"></a>Guia sala

O emulador simula a entrada do mundo na forma da malha de simulado "salas" mapeamento espacial. Esta guia permite escolher qual espaço para, em vez de sala de padrão de carga.

![Guia do HoloLens emulador 'Salas'](images/emulator-room-500px.png)

Salas simuladas são úteis para testar um aplicativo em vários ambientes. Várias salas são fornecidas com o emulador e depois de instalar a emulação, você irá encontrá-los em % ProgramFiles(x86) %\Program arquivos (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms. Todos esses ambientes foram capturados em ambientes reais usando um HoloLens:
* **DefaultRoom.xef** -uma sala pequena com uma TV, a tabela de café e dois sofas. Carregado por padrão quando você inicia o emulador.
* **Bedroom1.xef** -um quarto pequeno com um suporte técnico.
* **Bedroom2.xef** -um quarto com um ambiente de tamanho Rainha, cômoda, nightstands e walk-in armário.
* **GreatRoom.xef** -uma sala de excelente grande espaço aberto com sala de estar, mesa de jantar e cozinha.
* **LivingRoom.xef** – uma sala com uma lareira, sofá, armchairs e uma tabela de café com um vaso.

Você também pode registrar seus próprios ambientes para usar no emulador usando a página de simulação do [Windows Device Portal](using-the-windows-device-portal.md) em seu HoloLens.

No emulador, você só verá hologramas que você renderizar e você não verá a sala simulada por trás de hologramas. Isso está em contraste com o HoloLens real onde você pode ver ambos combinado juntos. Se você quiser ver a sala simulada no emulador do HoloLens, você precisará atualizar seu aplicativo para renderizar a malha de mapeamento espacial na cena.

### <a name="account-tab"></a>Guia de Notificação

Guia conta permite que você configure o emulador para entrar com uma Account da Microsoft. Isso é útil para testar a API que exigem o usuário estar conectado com uma conta. Depois de verificar se a caixa nesta página, inicializações subsequentes do emulador serão que você entrar, exatamente como faria de um usuário na primeira vez que o HoloLens é iniciado.

## <a name="see-also"></a>Consulte também
* [Entrada de emulador HoloLens e o simulador de realidade mista avançada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Histórico de software de emulador do HoloLens](hololens-emulator-archive.md)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)

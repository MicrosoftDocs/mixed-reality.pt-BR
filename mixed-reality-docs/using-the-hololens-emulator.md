---
title: Usando o Emulador do HoloLens
description: Usar o Emulador do HoloLens para testar aplicativos de realidade misturada em seu computador sem um HoloLens físico.
author: pbarnettms
ms.author: pbarnett
ms.date: 5/12/2020
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, emulador
ms.openlocfilehash: f525276d127bc0bbb682d7cea6821028258c6177
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83227981"
---
# <a name="using-the-hololens-emulator"></a>Usando o Emulador do HoloLens

O Emulador do HoloLens permite testar aplicativos holográficos em seu computador sem um HoloLens físico. Ele também inclui o conjunto de ferramentas de desenvolvimento do HoloLens. O emulador usa uma máquina virtual Hyper-V. As entradas humanas e ambientais que normalmente são lidas pelos sensores no HoloLens são simuladas usando seu teclado, mouse ou controle Xbox. Os aplicativos não precisam ser modificados para serem executados no emulador e não sabem que não estão sendo executados em um HoloLens real.

Se você pretende desenvolver aplicativos de headset imersivo do Windows Mixed Reality (VR) ou jogos para computadores desktop, confira o [Simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), que permite que você simule headsets para desktop.

## <a name="hololens-2-emulator-overview"></a>Visão Geral do Emulador do HoloLens 2

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/HoloLens-2-Emulator-Overview/player?format=ny]

## <a name="installing-the-hololens-emulator"></a>Instalando o Emulador do HoloLens
Baixar o Emulador do HoloLens.

Versões: 
* [Emulador do HoloLens 2 (Windows Holographic, versão 2004)](https://go.microsoft.com/fwlink/?linkid=2129088).
* [Emulador do HoloLens (1ª geração) e modelos de projeto holográfico](https://go.microsoft.com/fwlink/?linkid=2065980).

É possível encontrar notas de versão e builds mais antigos do Emulador do HoloLens na página [Arquivo do Emulador do HoloLens](hololens-emulator-archive.md).

### <a name="hololens-emulator-system-requirements"></a>Requisitos de sistema do Emulador do HoloLens

O Emulador do HoloLens usa o Hyper-V com o RemoteFx (1ª geração do Emulador) ou a GPU-PV (Emulador do HoloLens 2) para elementos gráficos acelerados de hardware. Para usar o emulador, verifique se o seu computador atende aos requisitos de hardware a seguir:
* Windows 10 Pro, Enterprise ou Education de 64 bits 
    >[!NOTE]
    >O Windows 10 Home Edition não é compatível com o Hyper-V ou o Emulador do HoloLens.  
    >O emulador do HoloLens 2 exige a Atualização de outubro de 2018 para o Windows 10 ou posterior.
* CPU de 64 bits
* CPU com 4 núcleos (ou várias CPUs com um total de 4 núcleos)
* 8 GB de RAM ou mais
* No BIOS, os recursos a seguir devem [ser compatíveis e estar habilitados](https://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Virtualização assistida por hardware
   * SLAT (Conversão de Endereços de Segundo Nível)
   * DEP (Prevenção de Execução de Dados) baseados em hardware
* Requisitos de GPU
   * DirectX 11.0 ou posterior
   * Driver gráfico do WDDM 1.2 ou posterior (1ª geração)
   * Driver gráfico do WDDM 2.5 (emulador do HoloLens 2)
   * O emulador pode funcionar com uma GPU não compatível, mas será significativamente mais lento

Se o seu sistema atende aos requisitos listados acima, **verifique se o recurso "Hyper-V" foi habilitado em seu sistema** por meio do Painel de Controle -> Programas -> Programas e Recursos -> Ativar ou desativar Recursos do Windows -> verifique se “Hyper-V” está selecionado para que a instalação do emulador tenha êxito.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Implantando aplicativos para o Emulador do HoloLens

1. Carregue a solução do aplicativo no Visual Studio.
    >[!NOTE]
    >Ao usar o Unity, crie o projeto do Unity e, em seguida, carregue a solução criada no Visual Studio como de costume.
2. Para o Emulador do HoloLens (1ª geração), verifique se a plataforma está definida como **x86**. Para o emulador do HoloLens 2, verifique se a plataforma está definida como **x86** ou **x64**.
3. Selecione a versão desejada do **Emulador do HoloLens** como o dispositivo de destino para a depuração.
4. Vá para **Depurar > Iniciar Depuração** ou pressione **F5** para iniciar o emulador e implantar o aplicativo para depuração.

O emulador pode levar um minuto ou mais para inicializar ao abri-lo pela primeira vez. É recomendável que você mantenha o emulador aberto durante a sessão de depuração para que você possa implantar aplicativos rapidamente no emulador.

## <a name="basic-emulator-input"></a>Entrada básica do emulador

Controlar o emulador é muito semelhante a muitos videogames 3D comuns. As opções de entrada estão disponíveis para usar o teclado, o mouse ou o controle Xbox. Você controla o emulador direcionando as ações de um usuário simulado, por meio do uso de um HoloLens. Suas ações movem o usuário simulado pelo ambiente. Os aplicativos em execução no emulador respondem como responderiam em um dispositivo real.

O cursor no HoloLens (1ª geração) segue o movimento e a rotação da cabeça. No emulador do HoloLens 2, o cursor segue o movimento e a orientação da mão.

* **Andar para a frente, para trás, para a esquerda e para a direita** – use as teclas W, A, S e D no teclado ou o joystick esquerdo em um controle Xbox.
* **Olhar para cima, para baixo, para a esquerda e para a direita** – clique e arraste o mouse, use as teclas de seta no teclado ou o joystick direito em um controle Xbox.
* **Gesto de fechar e abrir dedos indicador e polegar** – clique com o botão direito do mouse, pressione a tecla Enter no teclado ou use o botão A em um controle Xbox.
* **Gesto do sistema/de abrir a mão** – pressione a tecla Windows ou F2 no teclado ou pressione o botão B em um controle Xbox.
* **Movimento da mão para rolagem** – simultaneamente, mantenha pressionada a tecla Alt e o botão direito do mouse e arraste o mouse para cima ou para baixo ou, em um controle Xbox, mantenha o gatilho direito e o botão A pressionados e mova o joystick direito para cima e para baixo.
* **Movimento e orientação da mão** (apenas para o Emulador do HoloLens 2) – mantenha a tecla Alt pressionada e arraste o mouse para cima ou para baixo, para a esquerda ou para a direita para mover a mão. Alternativamente, use as teclas de seta e Q ou E para girar e inclinar a mão. Para um controle Xbox, mantenha o botão superior esquerdo ou direito pressionado e use o thumbstick esquerdo para mover a mão para a esquerda, para a direita, para a frente e para trás, o thumbstick direito para girá-la e para cima ou para baixo no Dpad para levantar ou abaixar a mão.

Você tem um headset imersivo do Windows Mixed Reality?  Começando com o Emulador do HoloLens 2 (Windows Holographic, versão 2004), você pode usar os controladores de movimentos e o headset imersivo do Windows Mixed Reality para controlar o Emulador do HoloLens 2 e exibi-lo em estéreo.  Confira [Usando controladores de movimentos e o headset imersivo do Windows Mixed Reality com o Emulador do HoloLens 2](#using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator)

## <a name="anatomy-of-the-hololens-2-emulator"></a>Anatomia do emulador do HoloLens 2 

### <a name="main-window"></a>Janela principal

![Janela principal do emulador do HoloLens 2](images/emulator2-900px.png)

### <a name="toolbar"></a>Barra de ferramentas

À direita da janela principal, você encontra a barra de ferramentas do emulador. A barra de ferramentas contém os seguintes botões:
* ![Ícone Fechar](images/emulator-close.png) **Fechar**: Fecha o emulador.
* ![Ícone Minimizar](images/emulator-minimize.png) **Minimizar**: Minimiza a janela do emulador.
* ![Simulation_icon](images/emulator-simulation-panel.png) **Painel de Controle da Simulação**: mostre ou oculte o [Painel de Controle da Simulação](#simulation-control-panel) para configurar e controlar a [entrada para o emulador](#basic-emulator-input).
* ![Ícone Ajustar à Tela](images/emulator-fit.png) **Ajustar à tela**: Ajusta o emulador à tela.
* ![Ícone Zoom](images/emulator-zoom.png) **Zoom**: Deixa o emulador maior e menor.
* ![Ícone Ajuda](images/emulator-help.png) **Ajuda**: Abre a ajuda do emulador.
* ![Ícone Abrir Portal de Dispositivos](images/emulator-deviceportal.png) **Abrir Portal de Dispositivos**: Abre o Portal de Dispositivos do Windows para o sistema operacional HoloLens no emulador.
* ![Ícone Ferramentas](images/emulator-tools.png) **Ferramentas**: Abre o painel **Ferramentas Adicionais**.

### <a name="simulation-control-panel"></a>Painel de controle da simulação

O Painel de controle da simulação permite que você exiba a posição e a orientação atuais do humano e dos dispositivos de entrada simulados. Ele também permite configurar a entrada simulada, como mostrar ou ocultar uma ou as duas mãos, bem como dispositivos usados para controlar a entrada simulada, como o teclado, o mouse e o gamepad do seu computador.

![Painel de controle da simulação](images/emulator-simulation-control-panel.png)

* Para ocultar ou mostrar o painel da simulação, clique no botão de barra de ferramentas ou pressione F7 no teclado.
* Passe o mouse sobre um controle ou um campo para exibir uma dica de ferramenta que contém os controles de teclado, mouse e gamepad para ele.
* Para mostrar ou ocultar uma mão, alterne a opção apropriada em Mão esquerda ou Mão direita.
* Para controlar a mão, use as teclas Alt direita ou esquerda do teclado ou o botão superior esquerdo ou direito no gamepad.
* Para direcionar todas as entradas para uma ou ambas as mãos, clique no botão de pino abaixo do switch de alternância. Isso é o equivalente a manter a tecla Alt pressionada para a mão.
* Para controlar a direção do foco do olhar, clique no pino na seção Olhos. Isso é o equivalente a manter a tecla Y pressionada no teclado.
* Para carregar uma gravação de sala, clique no botão Carregar na seção Gravação. Veja [Salas simuladas](#simulated-rooms) para obter mais informações.
* Para ajustar a velocidade em que o humano ou os dispositivos de entrada simulados se moverão ou girarão em resposta à entrada do teclado, mouse ou gamepad, clique no ícone de engrenagem ao lado de Configurações de entrada e ajuste os controles deslizantes.
* Por padrão, a entrada do teclado controla o humano e a entrada simulados. Para que a entrada do teclado do computador seja enviada pelo HoloLens, desmarque a opção Usar o teclado para simulação. F4 é a tecla de atalho para essa configuração.
* Se o painel da simulação já estiver visível, pressionar F8 moverá o foco do teclado para ele.
* Para desencaixar o painel da simulação da janela do emulador, clique no botão na parte inferior do painel ou pressione F9 no teclado.  Fechar a janela ou pressionar F9 novamente retornará a janela para o emulador.
* O Painel de Controle da Simulação pode ser iniciado como um aplicativo separado, permitindo que você se conecte e controle o emulador do HoloLens 2, um dispositivo HoloLens 2 ou a simulação do Windows Mixed Reality executando o PerceptionSimulationInput.exe de %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\.

### <a name="account-tab"></a>Guia Conta

A guia Conta permite que você configure o emulador para entrar com uma Conta Microsoft. Isso é útil para testar as APIs que exigem que o usuário esteja conectado com uma conta. Ativar/desativar essa opção exigirá que você feche e reinicie completamente o Emulador do HoloLens para que a configuração entre em vigor. Se essa opção estiver habilitada, as inicializações subsequentes do emulador solicitarão a entrada, assim como um usuário faria na primeira vez em que o HoloLens fosse iniciado. Para inserir suas credenciais usando o teclado do computador, primeiro desative a opção Usar o teclado para simulação no Painel de Controle da Simulação ou pressione F4 em seu teclado para ativar ou desativar a configuração de teclado.

### <a name="optional-settings-tab"></a>Guia Configurações opcionais

A guia Configurações opcionais exibe um controle para habilitar ou desabilitar os elementos gráficos acelerados de hardware. Os elementos gráficos acelerados de hardware serão usados por padrão se forem compatíveis com o driver do adaptador gráfico do seu computador. Se o driver do adaptador gráfico não for compatível com GPU-PV, essa opção não estará visível.

### <a name="diagnostics-tab"></a>Guia Diagnóstico

A guia Diagnóstico mostra o endereço IP do emulador na forma de um link para o Portal de Dispositivos do Windows, juntamente com o status da GPU virtual.

### <a name="network-tab"></a>Guia Rede

A guia Rede mostra os detalhes do adaptador de rede para o emulador, bem como detalhes do adaptador de rede para o computador host. Observe que, para o Emulador do HoloLens 2, esta guia só será exibida ao executar o emulador na Atualização de maio de 2019 para o Windows 10 ou mais recente.

### <a name="nat-configuration-tab"></a>Guia Configuração de NAT

Esta guia só será exibida ao executar o emulador na Atualização de maio de 2019 para o Windows 10 ou mais recente.

O emulador usa a conexão de rede do seu computador e fica atrás de um NAT.  Esta guia permite mapear portas do seu computador host para o emulador, o que permite que dispositivos remotos se conectem a aplicativos e serviços em execução no emulador.

Por exemplo, se você desejar acessar o Portal de Dispositivos no emulador em um computador remoto:

1. Adicione uma entrada para a porta 80 interna (a porta na qual o Portal de Dispositivos está escutando) clicando duas vezes em uma linha livre na tabela.  Para outros aplicativos, insira o número da porta na qual o aplicativo está escutando.
2. Escolha qualquer porta externa disponível.  Neste exemplo, usaremos a porta 8080 como a porta externa.
3. Selecione o protocolo.  O padrão é TCP.  Como o Portal de Dispositivos usa o TCP, deixaremos o padrão.
4. Clique em "Aplicar Alterações" para habilitar o mapeamento.  O “Status” mudará de “Pendente” para “Ativo”.
5. No computador remoto, abra um navegador e navegue até (IP-of-the-PC-running-the-emulator):8080.  A interface do Portal de Dispositivos será exibida.  Observe que o endereço IP usado em um computador remoto deve ser o endereço IP do PC que está executando o emulador, não o próprio emulador.  Você pode recuperar o IP por meio de vários meios, como o aplicativo Configurações no PC na categoria "Rede e Internet", "ipconfig" em um prompt de comando e na guia Rede na caixa de diálogo Ferramentas do emulador procurando a entrada Adaptador de Área de Trabalho.

Observe também que, se você adicionar um mapeamento para o Portal de Dispositivos, poderá controlar o emulador remotamente usando a ferramenta Controle de Simulação de Percepção incluída na instalação do emulador ou com as APIs de Simulação de Percepção conectando-se ao endereço IP do computador host e à porta externa do Portal de Dispositivos, como a 8080 no exemplo acima.  Ao usar o Controle de Simulação de Percepção para ao emulador e controlá-lo remotamente, especifique o endereço IP do computador e a porta configurada.  Não inclua “https://”.

Não há mapeamentos de porta por padrão.  Os mapeamentos que você configurar serão persistentes em inicializações do Emulador do HoloLens 2 e serão habilitados automaticamente quando o emulador tiver sido inicializado completamente.

Use o botão “Exportar” para salvar seus mapeamentos em um arquivo.  Você pode compartilhar este arquivo com outros membros da equipe que podem usar o botão “Importar” para configurar automaticamente os mesmos mapeamentos.

![Guia “Configuração NAT” do Emulador do HoloLens](images/emulator-natconfig-500px.png)

### <a name="updates-tab"></a>Guia Atualizações

Esta guia só será exibida ao executar o emulador na Atualização de maio de 2019 para o Windows 10 ou mais recente.

Na inicialização, o emulador verificará se há novas versões.  Se uma nova versão estiver disponível, o emulador exibirá um prompt mostrando a versão que você tem, junto com a versão disponível, e perguntando se você deseja atualizar.  Se você selecionar “Sim”, o instalador da nova versão será baixado.

A guia Atualizações permite que você controle se o emulador verifica ou não se há novas versões alternando a caixa de seleção "Verificar automaticamente se há atualizações" nesta guia.  Ela também permite que você veja e baixe outras versões do emulador disponíveis, começando com a Atualização de setembro de 2019.  Para versões diferentes da que está em execução no momento, é fornecido um link de download.  Clicar nesse link baixará o instalador dessa versão.

![Guia “Atualizações” do Emulador do HoloLens](images/emulator-updates-500px.png)

### <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Usando controladores de movimentos e o headset imersivo do Windows Mixed Reality com o Emulador do HoloLens 2

Começando com o Emulador do HoloLens 2 (Windows Holographic, versão 2004), você pode usar controladores de movimentos e um headset do Windows Mixed Reality para exibir e interagir com o Emulador do HoloLens 2 em estéreo.  Isso permite que você faça movimentos mais rápidos e naturais com a cabeça e as mãos sem um dispositivo HoloLens 2.  Observe que não se trata de uma substituição completa de um dispositivo HoloLens 2, mas sim da oferta de uma experiência aprimorada além da interação com o emulador usando o teclado, o mouse e o gamepad em uma janela 2D da área de trabalho.  Para habilitar esse recurso:

1. Verifique se o Windows Mixed Reality está configurado em seu PC e se o headset imersivo do Windows Mixed Reality está conectado.
2. Inicie o Emulador do HoloLens 2
3. Abra o painel de Simulação clicando no botão da barra de ferramentas ou pressionando F7.
4. Role o painel até a parte inferior.
5. Marque a caixa "Usar HMD para simulação"
6. O Windows Mixed Reality será iniciado e a exibição do emulador mudará ligeiramente.  Sem um headset, o emulador coloca os dois olhos no centro da cabeça e exibe apenas um olho.  Com o headset, ele gera uma saída estéreo verdadeira, mas renderiza apenas um olho na janela da área de trabalho, enquanto os dois olhos são renderizados no headset.
7. Opcionalmente, ligue um ou ambos os controladores de movimentos.  A entrada do controlador é mapeada para a entrada manual no emulador.  Por exemplo, para tocar, puxe o gatilho no controlador de movimentos.  Para se movimentar, use o thumbstick.  Para ver a lista completa dos controles, confira [Entrada avançada do Emulador do HoloLens e do Simulador de Realidade Misturada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)

Problemas para ver o conteúdo no headset?

- Se a exibição está em branco no headset e no Portal de Realidade Misturada, mas você vê o conteúdo na janela do Emulador do HoloLens 2 em sua área de trabalho, verifique se a aceleração de gráficos de hardware está habilitada no emulador.  O suporte ao headset imersivo do Windows Mixed Reality requer que a aceleração de gráficos de hardware esteja habilitada no emulador.
- Se você vê o conteúdo no headset, mas os hologramas estão desfocados ou você vê uma imagem dupla, use as seguintes etapas para ajustar a exibição de estéreo para seus olhos:

1. Desligue temporariamente "Usar HMD para simulação".
2. Inicie o Editor do Registro (regedit.exe)
3. Navegue até HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation
4. Crie um valor de DWORD chamado "EnableEyePoseControl" e defina seu valor como 1.
5. Habilite "Usar HMD para simulação" no emulador.
6. Quando o conteúdo aparecer no headset, use as teclas de direção para ajustar a rotação de olhos.  Mantenha pressionada a tecla Alt esquerda para ajustar o olho esquerdo e a tecla Alt direita para ajustar o olho direito.  Use "Q" e "E" para ajustar a rolagem de cada olho, mantendo pressionada a tecla Alt referente ao olho em questão.  Use as teclas "+" e "-" para ajustar a distância entre os olhos.  (Observe que usar +/- no teclado numérico não funcionará.  Use os botões do teclado principal.)
7. Quando a exibição estéreo parecer correta, pressione "S" para salvar as alterações.  A nova configuração será salva para inicializações futuras do emulador.
8. Se quiser abandonar as alterações e reverter para a configuração anterior, pressione "L" para carregar a configuração padrão ou a anterior.
9. Altere o valor de "EnableEyePoseControl" no registro para 0 e alterne a opção "Usar HMD para simulação".

Observe que, se você salvou uma configuração e deseja removê-la, é possível excluir o valor "DisplayConfiguration" em HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulation.  Se estiver usando o headset com o emulador no momento, você precisará desligar a opção "Usar HMD para simulação" e ligá-la novamente para ver a alteração entrar em vigor.

## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>Anatomia do Emulador do HoloLens (1ª geração)

### <a name="main-window"></a>Janela principal

Quando o emulador é iniciado, você vê uma janela que exibe o sistema operacional HoloLens.

![Janela principal do Emulador do HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barra de ferramentas

À direita da janela principal, você encontrará a barra de ferramentas do emulador. A barra de ferramentas contém os seguintes botões:
* ![Ícone Fechar](images/emulator-close.png) **Fechar**: Fecha o emulador.
* ![Ícone Minimizar](images/emulator-minimize.png) **Minimizar**: Minimiza a janela do emulador.
* ![Ícone de entrada humana](images/emulator-control.png) **Entrada humana**: O mouse e o teclado são usados para simular a [entrada humana para o emulador](#basic-emulator-input).
* ![Ícone de entrada de mouse e teclado](images/emulator-input.png) **Entrada de mouse e teclado**: a entrada de mouse e teclado é passada diretamente para o sistema operacional do HoloLens como eventos de teclado e mouse, como se tivesse conectado um teclado e um mouse Bluetooth.
* ![Ícone Ajustar à Tela](images/emulator-fit.png) **Ajustar à tela**: Ajusta o emulador à tela.
* ![Ícone Zoom](images/emulator-zoom.png) **Zoom**: Deixa o emulador maior e menor.
* ![Ícone Ajuda](images/emulator-help.png) **Ajuda**: Abre a ajuda do emulador.
* ![Ícone Abrir Portal de Dispositivos](images/emulator-deviceportal.png) **Abrir Portal de Dispositivos**: Abre o Portal de Dispositivos do Windows para o sistema operacional HoloLens no emulador.
* ![Ícone Ferramentas](images/emulator-tools.png) **Ferramentas**: Abre o painel **Ferramentas Adicionais**.

### <a name="simulation-tab"></a>Guia Simulação

A guia padrão no painel **Ferramentas adicionais** é a guia **Simulação**.

![Painel “Ferramentas adicionais” do Emulador do HoloLens](images/emulator-simulation-500px.png)

A guia Simulação mostra o estado atual dos sensores simulados usados para orientar o sistema operacional HoloLens no emulador. Passar o mouse sobre qualquer valor na guia Simulação fornece uma dica de ferramenta que descreve como controlar esse valor.

### <a name="room-tab"></a>Guia Sala

O emulador simula a entrada do mundo na forma da malha de mapeamento espacial de salas simuladas. Essa guia permite escolher a sala para carregar em vez da sala padrão.

![Guia “Salas” do Emulador do HoloLens](images/emulator-room-500px.png)

Veja [Salas simuladas](#simulated-rooms) para obter mais informações.

### <a name="account-tab"></a>Guia Conta

A guia Conta permite que você configure o emulador para entrar com uma Conta Microsoft. Isso é útil para testar as APIs que exigem que o usuário esteja conectado com uma conta. Após marcar a caixa nessa página, as inicializações subsequentes do emulador solicitarão a entrada, assim como um usuário faria na primeira vez em que o HoloLens fosse iniciado.

## <a name="simulated-rooms"></a>Salas simuladas

As salas simuladas são úteis para testar o aplicativo em vários ambientes. Várias salas são fornecidas com o emulador. Após instalar a emulação, você as encontrará em %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(versão)\Plugins\Rooms. Todos esses ambientes foram capturados em ambientes reais usando um HoloLens:
* **DefaultRoom.xef** – uma sala de estar pequena com uma TV, uma mesa de centro e dois sofás. Carregada por padrão quando você inicia o emulador.
* **Bedroom1.xef** – um quarto pequeno com uma escrivaninha.
* **Bedroom2.xef** – um quarto com uma cama queen size, uma cômoda, criados-mudos e um closet.
* **GreatRoom.xef** – uma sala principal com um grande espaço aberto com sala de estar, mesa de jantar e cozinha.
* **LivingRoom.xef** – uma sala de estar com uma lareira, sofá, poltronas e uma mesa de centro com um vaso.

Você também pode gravar suas próprias salas para usar no emulador utilizando a página Simulação do [Portal de Dispositivos do Windows](using-the-windows-device-portal.md) no seu HoloLens (1ª geração).

No emulador, você verá apenas os hologramas que renderizar. Mas você não verá a sala simulada por trás dos hologramas. Isso contrasta com o HoloLens real, em que você pode ver ambos, combinados. Se desejar ver a sala simulada no Emulador do HoloLens, você precisará atualizar seu aplicativo para renderizar a malha de mapeamento espacial na cena.

## <a name="known-issues"></a>Problemas conhecidos

* Ao desinstalar o Emulador do HoloLens 2, a imagem do disco rígido (Flash.vhdx) pode ser deixada no disco rígido na pasta Windows Kits\10\Emulation\HoloLens\<número do build.  É seguro excluir esse arquivo.
* A aceleração de gráficos de hardware pode fazer com que os aplicativos do Holographic falhem em alguns sistemas com gráficos AMD ou Intel.  Desabilitar a aceleração de gráficos de hardware na janela Ferramentas do emulador é uma solução alternativa para esse problema.

## <a name="troubleshooting"></a>Solução de problemas

Você pode encontrar uma mensagem de erro durante a instalação do emulador, indicando que você precisa do *"Visual Studio 2015 Atualização 1 e das ferramentas de UWP versão 1.2"* . Há três causas possíveis para esse erro:
* Você não tem uma versão suficientemente recente do Visual Studio (Visual Studio 2019, Visual Studio 2017 ou Visual Studio 2015 Atualização 1 ou posterior). Para corrigir isso, instale a versão mais recente do Visual Studio.
* Você tem uma versão recente do Visual Studio, mas você não tem as ferramentas da UWP (Plataforma Universal do Windows) instaladas. Esse é um recurso opcional para o Visual Studio. Para o HoloLens (1ª geração), você precisará de ferramentas da UWP para o Visual Studio 2015 ou o Visual Studio 2017.

Você também poderá encontrar um erro ao instalar o emulador em um SKU do Windows que não seja Pro/Enterprise/Education ou se não tiver o recurso Hyper-V habilitado.
* Leia a seção sobre [requisitos do sistema](#hololens-emulator-system-requirements) acima para um conjunto completo de requisitos.
* Também verifique se o recurso Hyper-V foi habilitado no seu sistema.

Se a instalação for concluída com êxito, mas você não vir o Emulador do HoloLens como uma opção para implantação e depuração, verifique o seguinte:
* A configuração de projeto do Visual Studio está definida como x86 (1ª geração do HoloLens) ou x86 ou x64 (Emulador do HoloLens 2).
* Se estiver usando o Visual Studio 2019, o conjunto de ferramentas da Plataforma na configuração do seu projeto será definido como v142.

Se a instalação for concluída com êxito, mas o Visual Studio exibir um erro ao tentar iniciar o Emulador do HoloLens, tente o seguinte:
* Execute o Visual Studio como administrador
* Se o Visual Studio 2019 for o único que você já teve instalado, verifique se o valor do Registro "KitsRoot10" em HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots aponta para sua pasta Arquivos de Programas de 32 bits (por exemplo, "C:\Arquivos de Programas (x86)\Windows Kits\10").  Se não, desinstale o Emulador do HoloLens, altere o valor de Registro para sua pasta Arquivos de Programas de 32 bits e reinstale o Emulador do HoloLens.  Esse problema é resolvido no Visual Studio 2019 16.0.3.

Se o emulador exibir uma caixa de diálogo de erro "Codificação de bytes inválida" na inicialização:
* Exclua todos os arquivos em %localappdata%\Microsoft\XDE\HCS e tente novamente.

Se sua lista de destino de depuração no Visual Studio estiver vazia (por exemplo, se Iniciar for a única opção) e você tiver seguido todas as etapas de solução de problemas acima:
* Exclua a pasta ConfigurationCache em %localappdata%\Microsoft\VisualStudio\\<*ID da instalação*>\CoreCon e tente novamente.

Se o sistema congela quando o emulador está iniciando, desabilite a aceleração de hardware para gráficos do emulador.
* Crie um valor do Registro DWORD chamado "DisableGPU" em HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 e defina seu valor como 1.

## <a name="see-also"></a>Veja também
* [Entrada avançada do Emulador do HoloLens e do Simulador de Realidade Misturada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Histórico de software do Emulador do HoloLens](hololens-emulator-archive.md)
* [Mapeamento espacial no Unity](spatial-mapping-in-unity.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)

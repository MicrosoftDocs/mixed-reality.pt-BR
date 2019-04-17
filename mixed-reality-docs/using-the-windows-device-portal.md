---
title: Usando o Windows Device Portal
description: O do Windows Device Portal para HoloLens permite configurar e gerenciar seu dispositivo remotamente via Wi-Fi ou USB. O Device Portal é um servidor Web no HoloLens ao qual você pode se conectar usando um navegador da Web em seu computador. O Portal de dispositivos inclui várias ferramentas que ajudarão você a gerenciar seus HoloLens e depurar e otimizar seus aplicativos.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal, HoloLens
ms.openlocfilehash: 8b9935d6b64abfd22e2e856e0142c953a6366008
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589765"
---
# <a name="using-the-windows-device-portal"></a>Usando o Windows Device Portal

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

O do Windows Device Portal para HoloLens permite configurar e gerenciar seu dispositivo remotamente via Wi-Fi ou USB. O Device Portal é um servidor Web no HoloLens ao qual você pode se conectar usando um navegador da Web em seu computador. O Portal de dispositivos inclui várias ferramentas que ajudarão você a gerenciar seus HoloLens e depurar e otimizar seus aplicativos.

Esta documentação é especificamente sobre a do Windows Device Portal para HoloLens. Para usar o portal de dispositivos do Windows para área de trabalho (incluindo para Windows Mixed Reality), consulte [visão geral do Windows Device Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configurando o HoloLens para usar o Windows Device Portal

1. Ligue seu HoloLens e coloque o dispositivo.
2. Faça o gesto [bloom](gestures.md#bloom) para iniciar o menu principal.
3. Mantenha o foco na **as configurações** lado a lado e executar o [polegar](gestures.md#air-tap) gesto. Execute um segundo polegar para colocar o aplicativo em seu ambiente. O aplicativo Configurações será iniciado depois disso.
4. Selecione item de menu **Atualização**.
5. Selecione o item de menu **Para desenvolvedores**.
6. Habilite o **Modo de Desenvolvedor**.
7. [Role para baixo](gestures.md#composite-gestures) e habilite **Portal do dispositivo**.
8. Se você estiver configurando o Windows Device Portal que você possa implantar aplicativos para este HoloLens via USB ou Wi-Fi, clique em **par** à [gerar um PIN de emparelhamento](using-visual-studio.md#pairing-your-device-hololens). Deixe o aplicativo de configurações com o pop-up do PIN até que você insira o PIN para o Visual Studio durante a primeira implantação.

   ![Habilitando o modo de desenvolvedor no aplicativo de configurações para o Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Conectar-se por Wi-Fi

1. [Conectar seu HoloLens ao Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Pesquise o endereço IP do seu dispositivo.
   * Localizar o endereço IP do dispositivo sob **Configurações > rede e Internet > Wi-Fi > Opções avançadas de**.
3. Em um navegador da web em seu computador, vá para https://<YOUR_HOLOLENS_IP_ADDRESS>
   * O navegador exibirá a seguinte mensagem: "Há um problema com o certificado de segurança do site". Isso acontece porque o certificado emitido para o Device Portal é um certificado de teste. Você pode ignorar esse erro de certificado por enquanto e continuar.

## <a name="connecting-over-usb"></a>Conectando através de USB

1. [Instalar as ferramentas](install-the-tools.md) para certificar-se de ter o Visual Studio atualização 1 com as ferramentas de desenvolvedor do Windows 10 instaladas em seu computador. Isso permite a conectividade por USB.
2. Conecte seu HoloLens ao computador com um cabo Micro USB.
3. Usando um navegador da Web em seu computador, acesse http://127.0.0.1:10080.

## <a name="connecting-to-an-emulator"></a>Conectar-se em um emulador

Você também pode usar o Device Portal com seu emulador. Para se conectar ao Portal do dispositivo, use o [barra de ferramentas](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator). Clique neste ícone: ![Ícone do Portal do dispositivo aberto](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra o Windows Device Portal para o sistema de operacional HoloLens no emulador.

## <a name="creating-a-username-and-password"></a>Criar um nome de usuário e senha

![Configurar o acesso ao Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurar o acesso ao Windows Device Portal*

Na primeira vez que se conectar ao Device Portal em seu HoloLens, você precisará criar um nome de usuário e senha.
1. Em um navegador da Web em seu computador, digite o endereço IP do HoloLens. A página Set up access é aberta.
2. Clique ou toque em **solicitação de pin** e olhar a tela HoloLens para obter o PIN gerado.
3. Insira o PIN na **PIN exibido em seu dispositivo** caixa de texto.
4. Insira o nome de usuário que você usará para se conectar ao Device Portal. Não é necessário ser um nome de MSA (conta da Microsoft) ou um nome de domínio.
5. Insira uma senha e confirme-a. A senha deve ter pelo menos sete caracteres de comprimento. Não é necessário ser uma senha de MSA ou de domínio.
6. Clique em **par** para se conectar ao Windows Device Portal sobre o HoloLens.

Se você quiser alterar este nome de usuário ou senha a qualquer momento, você pode repetir esse processo, visitando a página de segurança do dispositivo clicando o **segurança** link na parte superior direita ou navegação para: https://<YOUR_HOLOLENS_IP_ ENDEREÇO > / devicesecurity.htm.

## <a name="security-certificate"></a>Certificado de segurança

Se você vir um "erro de certificado" no navegador, poderá corrigi-lo criando uma relação de confiança com o dispositivo.

Cada HoloLens gera um certificado autoassinado exclusivo para sua conexão SSL. Por padrão, esse certificado não é confiável pelo navegador da Web do seu computador e você poderá receber um "erro de certificado". Ao baixar esse certificado do seu HoloLens (por USB ou uma rede Wi-Fi confiável) e torná-lo confiável em seu computador, você poderá se conectar com segurança ao seu dispositivo.
1. **Verifique se que você estiver usando uma rede segura (USB ou uma rede Wi-Fi que você confia).**
2. Baixe o certificado do dispositivo da página "Segurança" no Portal do dispositivo.
   * Clique no **segurança** link na lista à direita superior dos ícones ou navegue até: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicesecurity.htm
3. Instale o certificado na "raiz autoridades de certificação confiáveis" armazenar em seu computador.
   * No menu do Windows, digite: Gerenciar certificados de computador e inicie o miniaplicativo.
   * Expanda o **autoridade de certificação raiz confiável** pasta.
   * Clique no **certificados** pasta.
   * No menu Ação, selecione: Todas as tarefas > Importar...
   * Conclua o Assistente para Importação de Certificados, usando o arquivo de certificado baixado do Device Portal.
4. Reinicie o navegador.

## <a name="device-portal-pages"></a>Páginas do Device Portal

### <a name="home"></a>Início

![Windows Device Portal home page no Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Windows Device Portal home page no Microsoft HoloLens*

A sessão do Device Portal é iniciada na home page. Acesse outras páginas a partir da barra de navegação no lado esquerdo da página inicial.

A barra de ferramentas na parte superior da página fornece acesso a recursos e status normalmente usados.
* **Online**: Indica se o dispositivo está conectado ao Wi-Fi.
* **Desligamento**: Desativa o dispositivo.
* **Reiniciar**: Os ciclos de energia no dispositivo.
* **Segurança**: Abre a página de segurança do dispositivo.
* **Legal**: Indica a temperatura do dispositivo.
* **A/C**: Indica se o dispositivo está conectado e cobrança.
* **Ajudar a**: Abre a página de documentação de interface REST.

A página inicial mostra as seguintes informações:
* **Status do dispositivo:** monitora a integridade do seu dispositivo e relata erros críticos.
* **Informações do Windows:** mostra o nome do HoloLens e a versão atualmente instalada do Windows.
* A seção **Preferências** contém as seguintes configurações:
   * **IPD**: Define a distância interpupillary (IPD), que é a distância, em milímetros, entre o Centro de alunos do usuário quando o antecipação diretamente. A configuração entra em vigor imediatamente. O valor padrão é calculado automaticamente quando você configura seu dispositivo.
   * **Nome do dispositivo**: Atribua um nome para o HoloLens. Você deve reinicializar o dispositivo depois de alterar esse valor para que ele entre em vigor. Depois de clicar em **salvar**, uma caixa de diálogo perguntará se você deseja reiniciar o dispositivo imediatamente ou reinicializar mais tarde.
   * **Configurações de suspensão**: Define o período de tempo de espera antes do dispositivo entra em suspensão quando está conectado e quando ele está na bateria.

### <a name="3d-view"></a>Modo de exibição 3D

![Página de exibição 3D no Windows Device Portal no Microsoft HoloLens](images/3dview-1000px.png)<br>
*Página de exibição 3D no Windows Device Portal no Microsoft HoloLens*

Use a página Modo de exibição 3D para ver como o HoloLens interpreta seus arredores. Navegue pelo modo de exibição usando o mouse:
* Girar: com o botão esquerdo + mouse;
* PAN: com o botão direito clique em + mouse;
* Zoom: a rolagem do mouse.
* **Opções de controle**
   * Ativar o acompanhamento de visual contínuo verificando **acompanhamento visual de força**. 
   * **Pausar** interrompe o acompanhamento visual.
* **As opções de exibição**: Definir opções no modo de exibição 3D:
  * **Controle**: Indica se o acompanhamento visual está ativo.
  * **Mostrar base**: Exibe um plano de chão quadriculada.
  * **Mostrar frustum**: Exibe o frustum do modo de exibição.
  * **Mostrar plano de estabilização**: Exibe o plano que usa o HoloLens para estabilizar o movimento.
  * **Mostrar malha**: Exibe a malha de mapeamento espacial que representa o seu ambiente.
  * **Mostrar âncoras espaciais**: Exibe as âncoras espaciais para o aplicativo do Active Directory. Você deve clicar no botão de atualização para obter e atualizar as âncoras.
  * **Mostrar detalhes**: Exibe lado posições, quatérnios rotação principal e o vetor de origem do dispositivo à medida que eles se altera em tempo real.
  * **Botão de tela inteira**: Mostra a exibição 3D em modo de tela inteira. Pressione ESC para sair do modo de exibição de tela inteira.
* **Reconstrução de superfície**: Clique ou toque em **atualização** para exibir a malha de mais recente mapeamento espacial do dispositivo. Uma passagem completa pode levar um tempo para ser concluída, cerca de alguns segundos. A malha não atualiza automaticamente no modo de exibição 3D, e você deve clicar manualmente **atualizar** para obter a malha mais recente do dispositivo. Clique em **salvar** para salvar a malha de mapeamento espacial atual como um arquivo obj em seu computador.
* **Âncoras espaciais**: Clique em atualizar para exibir ou atualizar as âncoras espaciais para o aplicativo do Active Directory.

### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![Página de capturar realidade mista no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Página de capturar realidade mista no Windows Device Portal no Microsoft HoloLens*

Use o [capturar de realidade misturada](mixed-reality-capture.md) página para salvar fluxos de mídia do HoloLens.
* **Configurações de**: Controle os fluxos de mídia que são capturados, verificando as configurações a seguir:
  * **Hologramas**: Captura o conteúdo holográfico no fluxo de vídeo. Hologramas são renderizados em mono, não em estéreo.
  * **Câmera PV**: Captura a transmissão de vídeo da câmera foto e vídeo.
  * **Áudio de MIC**: Captura de áudio da matriz de microfone.
  * **Áudio aplicativos**: Captura de áudio do aplicativo em execução no momento.
  * **Qualidade de visualização de Live**: Selecione a resolução da tela, a taxa de quadros e a taxa de transmissão para a visualização dinâmica.
* Clique ou toque a **a visualização dinâmica** botão para mostrar o fluxo de captura. **A visualização dinâmica Stop** interrompe o fluxo de captura.
* Clique ou toque em **registro** para começar a gravar no fluxo de realidade misturada, usando as configurações especificadas. **Parar a gravação** termina a gravação e salva-o.
* Clique ou toque em **tirar foto** tirar uma foto estática do fluxo de captura.
* **Fotos e vídeos**: Mostra uma lista de capturas de vídeo e foto realizada no dispositivo.

Observe que os aplicativos do HoloLens não poderão capturar uma foto ou um vídeo MRC enquanto você estiver gravando ou transmitindo uma visualização dinâmica do Device Portal.

### <a name="performance-tracing"></a>Rastreamento de desempenho

![Desempenho, rastreamento de página no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Desempenho, rastreamento de página no Windows Device Portal no Microsoft HoloLens*

Capturar [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) rastreamentos (WPR) do seu HoloLens.
* **Perfis disponíveis**: Selecione o perfil do WPR da lista suspensa e clique ou toque **iniciar** para iniciar o rastreamento.
* **Perfis personalizados**: Clique ou toque em **procurar** para escolher um perfil do WPR do seu computador. Clique ou toque em **Carregar e iniciar** para iniciar o rastreamento.

Para parar o rastreamento, clique no link para parar. Permaneça nesta página até que o arquivo de rastreamento concluiu o download.

Os arquivos ETL capturados podem ser abertos para análise no [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Processos

![Processa a página no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Processa a página no Windows Device Portal no Microsoft HoloLens*

Mostra detalhes sobre processos em execução no momento. Isso inclui aplicativos e processos do sistema.

### <a name="system-performance"></a>Desempenho do sistema

![Página de desempenho do sistema no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Página de desempenho do sistema no Windows Device Portal no Microsoft HoloLens*

Mostra gráficos em tempo real de informações de diagnóstico do sistema, como o uso de energia, a taxa de quadros e a carga da CPU.

Estas são as métricas disponíveis:
* **SoC power**: Média de utilização de energia do sistema no chip instantânea, mais de um minuto
* **Energia do sistema**: Utilização de energia do sistema instantânea, medida ao longo de um minuto
* **Taxa de quadros**: Quadros por segundo, perdeu VBlanks por segundo e consecutivos VBlanks perdidas
* **GPU**: Utilização do mecanismo de GPU, percentual do total disponível
* **CPU**: porcentagem do total disponível
* **I/O**: Leituras e gravações
* **Rede**: Recebidos e enviados
* **Memória**: Total, em uso, confirmado, paginável e não-paginável

### <a name="apps"></a>Aplicativos

![Página de aplicativos no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Página de aplicativos no Windows Device Portal no Microsoft HoloLens*

Gerencia os aplicativos que estão instalados no HoloLens.
* **Aplicativos instalados**: Remova e iniciar aplicativos.
* **Executando aplicativos**: Lista os aplicativos que estão em execução no momento.
* **Instalar aplicativo**: Selecione pacotes de aplicativos para instalação em uma pasta no computador/da rede.
* **Dependência**: Adicione as dependências para o aplicativo que você pretende instalar.
* **Implantar**: Implante o aplicativo selecionado + dependências para o HoloLens.

### <a name="app-crash-dumps"></a>Despejos de memória do aplicativo

![Página de despejos de aplicativo no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Página de despejos de aplicativo no Windows Device Portal no Microsoft HoloLens*

Essa página permite que você colete despejos de memória para seus aplicativos de sideload. Verifique as **falha despejos de memória habilitado** caixa de seleção para cada aplicativo para o qual você deseja coletar os despejos de memória. Retorne a essa página para coletar despejos de memória. Arquivos de despejo podem ser [abertos no Visual Studio para depuração](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Explorador de Arquivos

![Página do Gerenciador de arquivo em Windows Device Portal no Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Página do Gerenciador de arquivo em Windows Device Portal no Microsoft HoloLens*

Use o Explorador de arquivos para procurar, carregar e baixar arquivos. Você pode trabalhar com arquivos na pasta documentos, pasta de imagens e nas pastas de armazenamento local para aplicativos que você implantou no Visual Studio ou no Portal do dispositivo.

### <a name="kiosk-mode"></a>Modo de quiosque

>[!NOTE]
>Modo de quiosque só está disponível com o [Microsoft HoloLens Commercial Suite](commercial-features.md).

Verifique se o [configurar HoloLens no modo de quiosque](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) artigo na Windows IT Pro Center para obter instruções sobre como habilitar o modo de quiosque por meio do Windows Device Portal atualizados.

### <a name="logging"></a>Registrando em log

![Página de registro em log no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Página de registro em log no Windows Device Portal no Microsoft HoloLens*

Gerencia em tempo real Event Tracing for Windows (ETW) em que o HoloLens.

Verifique **ocultar provedores** para mostrar a **eventos** lista apenas.
* **Provedores registrados**: Selecione o provedor ETW e o nível de rastreamento. O nível de rastreamento é um destes valores:
   1. Saída anormal ou encerramento
   2. Erros graves
   3. Avisos
   4. Avisos que não são de erro

Clique ou toque em **Habilitar** para iniciar o rastreamento. O provedor é adicionado à lista suspensa **Provedores Habilitados**.
* **Provedores personalizados**: Selecione um provedor ETW personalizado e o nível de rastreamento. Identifique o provedor pelo GUID. Não inclua colchetes no GUID.
* **Provedores habilitados**: Lista de provedores habilitados. Selecione um provedor da lista suspensa e clique ou toque em **Desabilitar** para parar o rastreamento. Clique ou toque em **Parar todos** para suspender todo o rastreamento.
* **Histórico de provedores**: Mostra os provedores ETW que foram habilitados durante a sessão atual. Clique ou toque em **Habilitar** para ativar um provedor que foi desabilitado. Clique ou toque em **Limpar** para limpar o histórico.
* **Eventos**: Lista os eventos ETW de provedores selecionados em formato de tabela. Essa tabela é atualizada em tempo real. Abaixo da tabela, clique no **clara** botão para excluir todos os eventos ETW da tabela. Isso não desabilita os provedores. Você pode clicar em **Salvar no arquivo** para exportar os atuais eventos ETW coletados para um arquivo CSV localmente.
* **Filtros**: Permitem que você filtre os eventos ETW coletados pela palavra-chave, ID, nome do provedor, nível, nome da tarefa ou texto. Você pode combinar vários critérios:
   1. Para critérios de aplicação para a mesma propriedade – eventos podem atender a qualquer um desses critérios são mostrados.
   2. Para critérios de aplicar a propriedade diferente - eventos devem satisfazer todos os critérios

Por exemplo, você pode especificar os critérios de *(nome da tarefa contém 'Foo' ou 'Barra') e (texto contém 'error' ou 'aviso')*

### <a name="simulation"></a>Simulation

![Página de simulação no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Página de simulação no Windows Device Portal no Microsoft HoloLens*

Permite que você grave e reproduza dados de entrada para testes.
* **Capturar sala**: Usada para baixar um arquivo de sala simulado que contém a malha de mapeamento espacial para o ambiente do usuário. Nomear a sala e, em seguida, clique em **capturar** para salvar os dados como um arquivo .xef em seu computador. Esse arquivo de sala pode ser carregado no emulador do HoloLens.
* **Gravação**: Verificar os fluxos para gravar, nomeie a gravação e clique ou toque **registro** para iniciar a recodificação. Executar ações com o HoloLens e, em seguida, clique em **parar** para salvar os dados como um arquivo .xef em seu computador. Esse arquivo pode ser carregado no emulador ou dispositivo HoloLens.
* **Reprodução**: Clique ou toque em **gravação de Upload** para selecionar um arquivo xef do seu computador e enviar os dados para o HoloLens.
* **Modo de controle**: Selecione **padrão** ou **simulação** partir do menu suspenso e clique ou toque a **definir** botão para selecionar o modo em que o HoloLens. Escolher "Simulação" desabilita os sensores reais em seu HoloLens e usa dados simulados carregados em vez disso. Se você alternar para "Simulação", o HoloLens não responderá ao usuário real até que você volte para "Padrão".

### <a name="networking"></a>Rede

![Página de rede no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Página de rede no Windows Device Portal no Microsoft HoloLens*

Gerencia conexões Wi-Fi no HoloLens.
* **Adaptadores Wi-Fi**: Selecione um perfil e um adaptador Wi-Fi usando os controles de lista suspensa. Clique ou toque em **Connect** para usar o adaptador selecionado.
* **Redes disponíveis**: Lista as redes Wi-Fi o HoloLens podem se conectar ao. Clique ou toque em **Refresh** para atualizar a lista.
* **Configuração de IP**: Mostra o endereço IP e outros detalhes de conexão de rede.

### <a name="virtual-input"></a>Entrada virtual

![Página de entrada virtual no Windows Device Portal no Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Página de entrada virtual no Windows Device Portal no Microsoft HoloLens*

Envia entrada do teclado da máquina remota para o HoloLens.

Clique ou toque na região sob **Teclado Virtual** para habilitar o envio de pressionamentos de teclas para o HoloLens. Digite a **entrada de texto** caixa de texto e clique ou toque **enviar** para enviar os pressionamentos de tecla para o aplicativo Active Directory.

## <a name="device-portal-rest-apis"></a>API de REST de Portal a dispositivo

Tudo no portal do dispositivo é criado na parte superior da [da API REST](device-portal-api-reference.md) que, opcionalmente, você pode usar para acessar os dados e controlar seu dispositivo por meio de programação.

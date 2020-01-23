---
title: Usando o portal do dispositivo Windows
description: O portal de dispositivo do Windows para o HoloLens permite que você configure e gerencie seu dispositivo remotamente por Wi-Fi ou USB. O Device Portal é um servidor Web no HoloLens ao qual você pode se conectar usando um navegador da Web em seu computador. O portal do dispositivo inclui muitas ferramentas que ajudarão você a gerenciar seu HoloLens e a depurar e otimizar seus aplicativos.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Portal de dispositivos Windows, HoloLens
ms.openlocfilehash: b22c70305076e3b2c18f880878b48c3142efdbfe
ms.sourcegitcommit: cf3b662cfcf3fb05a554c302e595eb018f01abf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76521687"
---
# <a name="using-the-windows-device-portal"></a>Usando o portal do dispositivo Windows

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Portal de Dispositivos do Windows</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

O portal de dispositivo do Windows para o HoloLens permite que você configure e gerencie seu dispositivo remotamente por Wi-Fi ou USB. O Device Portal é um servidor Web no HoloLens ao qual você pode se conectar usando um navegador da Web em seu computador. O portal do dispositivo inclui muitas ferramentas que ajudarão você a gerenciar seu HoloLens e a depurar e otimizar seus aplicativos.

Esta documentação é especificamente sobre o portal de dispositivos do Windows para o HoloLens. Para usar o portal de dispositivos do Windows para desktop (incluindo o Windows Mixed Reality), consulte [visão geral do portal de dispositivos do Windows](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configurando o HoloLens para usar o portal de dispositivos do Windows

1. Ligue seu HoloLens e coloque o dispositivo.
2. Execute o [gesto de início](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) para HoloLens2 ou [flor](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) no HoloLens (1ª gen) para iniciar o menu principal. 
3. Olhar no bloco **configurações** e execute o gesto de [toque aéreo](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) no hololens (1º gen) ou selecione-o no hololens 2 [tocando-o ou usando um raio de mão](https://docs.microsoft.com/hololens/hololens2-basic-usage). 
4. Selecione item de menu **Atualização**.
5. Selecione o item de menu **Para desenvolvedores**.
6. Habilite o **Modo de Desenvolvedor**.
7. [Role para baixo](gaze-and-commit.md#composite-gestures) e habilite o **portal do dispositivo**.
8. Se você estiver configurando o portal de dispositivos do Windows para que possa implantar aplicativos nesse HoloLens em USB ou Wi-Fi, clique em **emparelhar** para [gerar um PIN de emparelhamento](using-visual-studio.md). Deixe o aplicativo configurações no pop-up de PIN até inserir o PIN no Visual Studio durante a primeira implantação.

   ![Habilitando o modo de desenvolvedor no aplicativo de configurações para Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Conectando por Wi-Fi

1. [Conecte seu HoloLens ao Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Pesquise o endereço IP do dispositivo.
   * Localize o endereço IP no dispositivo em **configurações > rede & Internet > opções de Wi-Fi > avançadas**.
3. Em um navegador da Web em seu computador, vá para https://< YOUR_HOLOLENS_IP_ADDRESS >
   * O navegador exibirá a seguinte mensagem: "há um problema com o certificado de segurança deste site". Isso acontece porque o certificado emitido para o Device Portal é um certificado de teste. Você pode ignorar esse erro de certificado por enquanto e continuar.

## <a name="connecting-over-usb"></a>Conectando-se via USB

1. [Instale as ferramentas](install-the-tools.md) para verificar se você tem o Visual Studio Update 1 com as ferramentas de desenvolvedor do Windows 10 instaladas em seu computador. Isso permite a conectividade por USB.
2. Conecte seu HoloLens ao seu PC com um cabo micro USB para o HoloLens (1º gen) ou USB-C para o HoloLens 2.
3. Em um navegador da Web em seu computador, vá para [https://127.0.0.1:10080](https://127.0.0.1:10080).

## <a name="connecting-to-an-emulator"></a>Conectando a um emulador

Você também pode usar o Device Portal com seu emulador. Para se conectar ao portal do dispositivo, use a [barra de ferramentas](using-the-hololens-emulator.md). Clique neste ícone: ![ícone abrir o portal do dispositivo](images/emulator-deviceportal.png) **abrir o portal do dispositivo**: Abra o portal do dispositivo do Windows para o sistema operacional do HoloLens no emulador.

## <a name="creating-a-username-and-password"></a>Criando um nome de usuário e senha

![configurar o acesso ao portal de dispositivos do Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurar o acesso ao portal de dispositivos do Windows*

Na primeira vez que se conectar ao Device Portal em seu HoloLens, você precisará criar um nome de usuário e senha.
1. Em um navegador da Web em seu computador, digite o endereço IP do HoloLens. A página Set up access é aberta.
2. Clique ou toque em **solicitar PIN** e examine a exibição do HoloLens para obter o PIN gerado.
3. Insira o PIN na caixa de texto do **PIN exibido em seu dispositivo** .
4. Insira o nome de usuário que você usará para se conectar ao Device Portal. Não é necessário ser um nome de MSA (conta da Microsoft) ou um nome de domínio.
5. Insira uma senha e confirme-a. A senha deve ter pelo menos sete caracteres de comprimento. Não é necessário ser uma senha de MSA ou de domínio.
6. Clique em **emparelhar** para se conectar ao portal de dispositivo do Windows no HoloLens.

Se você quiser alterar esse nome de usuário ou senha a qualquer momento, poderá repetir esse processo visitando a página de segurança do dispositivo navegando até: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm.

## <a name="security-certificate"></a>Certificado de segurança

Se você vir um "erro de certificado" no navegador, poderá corrigi-lo criando uma relação de confiança com o dispositivo.

Cada HoloLens gera um certificado autoassinado exclusivo para sua conexão SSL. Por padrão, esse certificado não é confiável pelo navegador da Web do seu computador e você poderá receber um "erro de certificado". Ao baixar esse certificado do seu HoloLens (por USB ou uma rede Wi-Fi confiável) e torná-lo confiável em seu computador, você poderá se conectar com segurança ao seu dispositivo.
1. **Verifique se você está em uma rede segura (USB ou uma rede Wi-Fi confiável).**
2. Baixe o certificado desse dispositivo na página "segurança" no portal do dispositivo.
   * Navegue até: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm
3. Instale o certificado no repositório "autoridades de certificação raiz confiáveis" no seu computador.
   * No menu do Windows, digite: gerenciar certificados de computador e iniciar o applet.
   * Expanda a pasta **autoridade de certificação raiz confiável** .
   * Clique na pasta **Certificados**.
   * No menu Ações, selecione: Todas as tarefas > Importar...
   * Conclua o Assistente para Importação de Certificados, usando o arquivo de certificado baixado do Device Portal.
4. Reinicie o navegador.

## <a name="device-portal-pages"></a>Páginas do Device Portal

### <a name="home"></a>Página Inicial

![home page do portal de dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*home page do portal do dispositivo Windows no Microsoft HoloLens*

A sessão do Device Portal é iniciada na home page. Acesse outras páginas a partir da barra de navegação no lado esquerdo da página inicial.

A barra de ferramentas na parte superior da página fornece acesso a recursos e status normalmente usados.
* **Online**: indica se o dispositivo está conectado ao Wi-Fi.
* **Desligar**: desativa o dispositivo.
* **Reiniciar**: repete o ciclo de energia no dispositivo.
* **Segurança**: abre a página Device Security.
* **Frio**: indica a temperatura do dispositivo.
* **A/C**: indica se o dispositivo está conectado e carregando.
* **Ajuda**: abre a página de documentação de interface REST.

A página inicial mostra as seguintes informações:
* **Status do dispositivo:** monitora a integridade do seu dispositivo e relata erros críticos.
* **Informações do Windows:** mostra o nome do HoloLens e a versão atualmente instalada do Windows.
* A seção **Preferências** contém as seguintes configurações:
   * **IPD**: define a DIP (distância interpupilar), que é a distância, em milímetros, entre o centro das pupilas do usuário quando ele olha para a frente. A configuração entra em vigor imediatamente. O valor padrão é calculado automaticamente quando você configura seu dispositivo.
   * **Nome do dispositivo**: atribua um nome para o HoloLens. Você deve reinicializar o dispositivo depois de alterar esse valor para que ele entre em vigor. Depois de clicar em **salvar**, uma caixa de diálogo perguntará se você deseja reinicializar o dispositivo imediatamente ou reinicializar mais tarde.
   * **Configurações de suspensão**: define o tempo de espera antes que o dispositivo entre em suspensão quando ele estiver conectado e quando estiver na bateria.

### <a name="3d-view"></a>Modo de exibição 3D

![página de exibição 3D no portal de dispositivo do Windows no Microsoft HoloLens](images/3dview-1000px.png)<br>
*página exibição 3D no portal do dispositivo Windows no Microsoft HoloLens*

Use a página Modo de exibição 3D para ver como o HoloLens interpreta seus arredores. Navegue pelo modo de exibição usando o mouse:
* Girar: clique com o botão esquerdo + mouse;
* Pan: clique com o botão direito do mouse em + rato;
* Zoom: rolagem do mouse.
* **Opções de controle**
   * Ative o controle visual contínuo verificando o **controle visual forçado**. 
   * **Pause** interrompe o rastreamento visual.
* **Opções de exibição**: definir opções no modo de exibição 3D:
  * **Acompanhamento**: indica se o rastreamento visual está ativo.
  * **Mostrar piso**: exibe um plano de chão quadriculado.
  * **Mostrar tronco**: exibe o tronco de exibição.
  * **Mostrar o plano de estabilização**: exibe o plano que o HoloLens usa para estabilizar o movimento.
  * **Mostrar malha**: exibe a malha de mapeamento espacial que representa o ambiente.
  * **Mostrar âncoras espaciais**: exibe âncoras espaciais para o aplicativo ativo. Você deve clicar no botão atualizar para obter e atualizar as âncoras.
  * **Mostrar detalhes**: exibe as posições das mãos, os quatérnios de rotação da cabeça e o vetor de origem do dispositivo conforme eles mudam em tempo real.
  * **Botão tela inteira**: mostra o Modo de exibição 3D em modo de tela inteira. Pressione ESC para sair do modo de exibição de tela inteira.
* **Reconstrução da superfície**: clique ou toque em **Atualizar** para exibir a malha de mapeamento espacial mais recente do dispositivo. Uma passagem completa pode levar algum tempo para ser concluída (até alguns segundos). A malha não é atualizada automaticamente no modo de exibição 3D e você deve clicar em **Atualizar** manualmente para obter a malha mais recente do dispositivo. Clique em **salvar** para salvar a malha de mapeamento espacial atual como um arquivo obj em seu computador.
* **Âncoras espaciais**: clique em atualizar para exibir ou atualizar as âncoras espaciais do aplicativo ativo.

### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![página de captura de realidade misturada no portal de dispositivo do Windows no Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Página de captura da realidade misturada no portal do dispositivo Windows no Microsoft HoloLens*

Use a página Mixed Reality Capture para salvar fluxos de mídia do HoloLens.
* **Configurações**: controle os fluxos de mídia que são capturados verificando as seguintes configurações:
  * **Hologramas**: captura o conteúdo de Holographic no fluxo de vídeo. Hologramas são renderizados em mono, não em estéreo.
  * **Câmera de PV**: captura o fluxo de vídeo da câmera de foto/vídeo.
  * **Mic Audio**: captura o áudio do grupo de microfones.
  * **App Audio**: captura o áudio do aplicativo em execução no momento.
  * **Renderizar da câmera**: alinha a captura para ser da perspectiva da câmera de foto/vídeo, se [houver suporte do aplicativo em execução](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (somente HoloLens 2).
  * **Qualidade de visualização dinâmica**: selecione a resolução de tela, a taxa de quadros e a taxa de streaming para a visualização dinâmica.
* Clique ou toque no botão **Visualização dinâmica** para mostrar o fluxo de captura. **Parar a visualização dinâmica** interrompe o fluxo de captura.
* Clique ou toque em **gravar** para iniciar a gravação do fluxo de realidade misturada, usando as configurações especificadas. **Parar gravação** encerra a gravação e salva-a.
* Clique ou toque em **tirar foto** para tirar uma imagem ainda do fluxo de captura.
* **Vídeos e fotos**: mostra uma lista de capturas de vídeos e fotos feitas no dispositivo.

> [!NOTE]
> Há [limitações para a MRC simultânea](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * Se um aplicativo tentar acessar a câmera de foto/vídeo enquanto o portal de dispositivo do Windows estiver gravando um vídeo, a gravação de vídeo será interrompida.
>   * O HoloLens 2 não interromperá a gravação de vídeo se o aplicativo acessar a câmera de foto/vídeo com o modo SharedReadOnly.
> * Se um aplicativo estiver usando ativamente a câmera de foto/vídeo, o portal de dispositivo do Windows poderá tirar uma foto ou gravar um vídeo.
> * Transmissão ao vivo:
>   * O HoloLens (1º gen) impede que um aplicativo acesse a câmera de foto/vídeo enquanto realiza a transmissão ao vivo do portal de dispositivos do Windows.
>   * O HoloLens (1º gen) falhará ao gerar uma transmissão ao vivo se um aplicativo estiver usando ativamente a câmera de foto/vídeo.
>   * O HoloLens 2 interrompe automaticamente a transmissão ao vivo quando um aplicativo tenta acessar a câmera de foto/vídeo no modo ExclusiveControl.
>   * O HoloLens 2 é capaz de iniciar uma transmissão ao vivo enquanto um aplicativo está usando ativamente a câmera VP.

### <a name="performance-tracing"></a>Rastreamento de desempenho

página de rastreamento de desempenho ![no portal de dispositivo do Windows no Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Página de rastreamento de desempenho no portal do dispositivo Windows no Microsoft HoloLens*

Capture os rastreamentos do [gravador de desempenho do Windows](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) do seu HoloLens.
* **Perfis disponíveis**: selecione o perfil WPR na lista suspensa e clique ou toque em **Iniciar** para iniciar o rastreamento.
* **Perfis personalizados**: clique ou toque em **Procurar** para escolher um perfil WPR do seu computador. Clique ou toque em **Carregar e iniciar** para iniciar o rastreamento.

Para interromper o rastreamento, clique no link parar. Permaneça nesta página até que o arquivo de rastreamento tenha concluído o download.

Os arquivos ETL capturados podem ser abertos para análise no [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Processos

![página de processos no portal do dispositivo Windows no Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Página de processos no portal de dispositivos do Windows no Microsoft HoloLens*

Mostra detalhes sobre processos em execução no momento. Isso inclui aplicativos e processos do sistema.

### <a name="system-performance"></a>Desempenho do sistema

![página desempenho do sistema no portal do dispositivo Windows no Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Página desempenho do sistema no portal do dispositivo Windows no Microsoft HoloLens*

Mostra gráficos em tempo real de informações de diagnóstico do sistema, como o uso de energia, a taxa de quadros e a carga da CPU.

Estas são as métricas disponíveis:
* **Energia SoC**: utilização instantânea de energia do sistema-em-um-chip, com base na média de um minuto
* **Energia do sistema**: utilização instantânea de energia do sistema, com base na média de um minuto
* **Taxa de quadros**: quadros por segundo, VBlanks perdidos por segundo e VBlanks perdidos consecutivos
* **GPU**: utilização do mecanismo GPU, porcentagem do total disponível
* **CPU**: porcentagem do total disponível
* **E/S**: lê e grava
* **Rede**: recepção e envio
* **Memória**: total, em uso, confirmada, paginada e não paginável

### <a name="apps"></a>Aplicativos

página de aplicativos ![no portal de dispositivo do Windows no Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Página de aplicativos no portal do dispositivo Windows no Microsoft HoloLens*

Gerencia os aplicativos que estão instalados no HoloLens.
* **Aplicativos instalados**: remove e inicia aplicativos.
* **Aplicativos em execução**: lista os aplicativos que estão em execução no momento.
* **Instalar aplicativo**: selecione pacotes de aplicativos para instalação de uma pasta em seu computador/rede.
* **Dependência**: adiciona dependências para o aplicativo que você pretende instalar.
* **Implantar**: implante o aplicativo selecionado + dependências para o HoloLens.

### <a name="app-crash-dumps"></a>Despejos de memória do aplicativo

página ![despejos de memória do aplicativo no portal do dispositivo Windows no Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Página despejos de memória do aplicativo no portal do dispositivo Windows no Microsoft HoloLens*

Essa página permite que você colete despejos de memória para seus aplicativos de sideload. Marque a caixa de seleção de **despejos de memória habilitados** para cada aplicativo para o qual você deseja coletar despejos de memória. Retorne a essa página para coletar despejos de memória. Os arquivos de despejo podem ser [abertos no Visual Studio para depuração](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Explorador de Arquivos

![página explorador de arquivos no portal de dispositivos do Windows no Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Página explorador de arquivos no portal do dispositivo Windows no Microsoft HoloLens*

Use o explorador de arquivos para procurar, carregar e baixar arquivos. Você pode trabalhar com arquivos na pasta documentos, na pasta imagens e nas pastas de armazenamento local para aplicativos implantados no Visual Studio ou no portal do dispositivo.

### <a name="kiosk-mode"></a>Modo de quiosque

>[!NOTE]
>O modo de quiosque só está disponível com o [pacote comercial Microsoft HoloLens](commercial-features.md).

Verifique o artigo [Configurar o HoloLens no modo de quiosque](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) no Windows it pro Center para obter instruções atualizadas sobre como habilitar o modo de quiosque por meio do portal de dispositivos Windows.

### <a name="logging"></a>Registro em log

![página de log no portal de dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Página de registro em log no portal de dispositivo do Windows no Microsoft HoloLens*

Gerencia o ETW (rastreamento de eventos em tempo real para Windows) no HoloLens.

Marque **ocultar provedores** para mostrar somente a lista de **eventos** .
* **Provedores registrados**: seleciona o provedor ETW e o nível de rastreamento. O nível de rastreamento é um destes valores:
   1. Saída anormal ou encerramento
   2. Erros graves
   3. Avisos
   4. Avisos que não são de erro

Clique ou toque em **Habilitar** para iniciar o rastreamento. O provedor é adicionado à lista suspensa **Provedores Habilitados**.
* **Provedores personalizados**: selecione um provedor ETW personalizado e o nível de rastreamento. Identifique o provedor pelo GUID. Não inclua colchetes no GUID.
* **Provedores habilitados**: lista os provedores habilitados. Selecione um provedor da lista suspensa e clique ou toque em **Desabilitar** para parar o rastreamento. Clique ou toque em **Parar todos** para suspender todo o rastreamento.
* **Histórico de provedores**: mostra os provedores ETW que foram habilitados durante a sessão atual. Clique ou toque em **Habilitar** para ativar um provedor que foi desabilitado. Clique ou toque em **Limpar** para limpar o histórico.
* **Eventos**: lista os eventos ETW dos provedores selecionados no formato de tabela. Essa tabela é atualizada em tempo real. Abaixo da tabela, clique no botão **Limpar** para excluir todos os eventos ETW da tabela. Isso não desabilita os provedores. Você pode clicar em **Salvar no arquivo** para exportar os atuais eventos ETW coletados para um arquivo CSV localmente.
* **Filtros**: permite filtrar os eventos de ETW coletados por ID, palavra-chave, nível, nome do provedor, nome da tarefa ou texto. Você pode combinar vários critérios juntos:
   1. Para critérios aplicados à mesma propriedade, os eventos que podem atender a qualquer um desses critérios são mostrados.
   2. Para critérios aplicados a uma propriedade diferente, os eventos devem atender a todos os critérios

Por exemplo, você pode especificar os critérios *(o nome da tarefa contém ' foo ' ou ' barra ') e (o texto contém ' erro ' ou ' aviso ')*

### <a name="simulation"></a>Simulation

página de simulação de ![no portal de dispositivo do Windows no Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Página simulação no portal do dispositivo Windows no Microsoft HoloLens*

Permite que você grave e reproduza dados de entrada para testes.
* **Capturar sala**: usado para baixar um arquivo de sala simulada que contém a malha de mapeamento espacial para os arredores do usuário. Nomeie a sala e clique em **capturar** para salvar os dados como um arquivo. XeF em seu computador. Esse arquivo de sala pode ser carregado no emulador do HoloLens.
* **Gravação**: Verifique os fluxos a serem gravados, nomeie a gravação e clique ou toque em **gravar** para iniciar a recodificação. Execute ações com seu HoloLens e clique em **parar** para salvar os dados como um arquivo. XeF em seu PC. Esse arquivo pode ser carregado no emulador ou dispositivo HoloLens.
* **Reprodução**: clique ou toque em **carregar gravação** para selecionar um arquivo XeF do seu PC e enviar os dados para o HoloLens.
* **Modo de controle**: selecione **padrão** ou **simulação** na lista suspensa e clique ou toque no botão **definir** para selecionar o modo no HoloLens. Escolher "Simulação" desabilita os sensores reais em seu HoloLens e usa dados simulados carregados em vez disso. Se você alternar para "Simulação", o HoloLens não responderá ao usuário real até que você volte para "Padrão".

### <a name="networking"></a>Rede do

página de rede ![no portal de dispositivo do Windows no Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Página rede no portal do dispositivo Windows no Microsoft HoloLens*

Gerencia conexões Wi-Fi no HoloLens.
* **Adaptadores WiFi**: selecione um adaptador e perfil de Wi-Fi usando os controles suspensos. Clique ou toque em **conectar** para usar o adaptador selecionado.
* **Redes disponíveis**: lista as redes Wi-Fi às quais o HoloLens pode se conectar. Clique ou toque em **Atualizar** para atualizar a lista.
* **Configuração de IP**: mostra o endereço IP e outros detalhes da conexão de rede.

### <a name="virtual-input"></a>Entrada virtual

![página de entrada virtual no portal de dispositivo do Windows no Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Página de entrada virtual no portal de dispositivo do Windows no Microsoft HoloLens*

Envia entrada do teclado da máquina remota para o HoloLens.

Clique ou toque na região em **teclado virtual** para habilitar o envio de pressionamentos de teclas para o HoloLens. Digite a caixa de **texto entrada** e clique ou toque em **Enviar** para enviar os pressionamentos de tecla para o aplicativo ativo.

## <a name="device-portal-rest-apis"></a>API REST do portal do dispositivo

Tudo no portal do dispositivo é criado sobre as [APIs REST](device-portal-api-reference.md) que você pode opcionalmente usar para acessar os dados e controlar seu dispositivo de forma programática.

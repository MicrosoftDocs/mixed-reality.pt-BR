---
title: Usar o Portal de Dispositivos do Windows
description: O Portal de Dispositivos do Windows para HoloLens permite que você configure e gerencie seu dispositivo remotamente por Wi-Fi ou USB. O Device Portal é um servidor Web no HoloLens ao qual você pode se conectar usando um navegador da Web em seu computador. O Portal de Dispositivos inclui muitas ferramentas que ajudarão você a gerenciar seu HoloLens e a depurar e otimizar seus aplicativos.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Portal de Dispositivos do Windows, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 6a5a0ef164cbbe80f74f0fe6cc42e08834d2a4b4
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082092"
---
# <a name="using-the-windows-device-portal"></a>Usar o Portal de Dispositivos do Windows

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> Portal de Dispositivos do Windows</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

O Portal de Dispositivos do Windows para HoloLens permite que você configure e gerencie seu dispositivo remotamente por Wi-Fi ou USB. O Device Portal é um servidor Web no HoloLens ao qual você pode se conectar usando um navegador da Web em seu computador. O Portal de Dispositivos inclui muitas ferramentas que ajudarão você a gerenciar seu HoloLens e a depurar e otimizar seus aplicativos.

Essa documentação trata especificamente do Portal de Dispositivos do Windows para HoloLens. Para usar o Portal de Dispositivos do Windows para desktop (inclusive para Windows Mixed Reality), confira [Visão geral do Portal de Dispositivos do Windows](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configurar o HoloLens para usar o Portal de Dispositivos do Windows

1. Ligue seu HoloLens e coloque o dispositivo.
2. Execute a ação [Iniciar gesto](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) para HoloLens2 ou [Abrir a mão](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) no HoloLens (1ª geração) para iniciar o menu principal. 
3. Olhe no bloco **Configurações** e execute o gesto [fechar e abrir os dedos indicador e polegar](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) no HoloLens (1ª geração) ou selecione-o no HoloLens 2 [tocando nele ou usando um raio de mão](https://docs.microsoft.com/hololens/hololens2-basic-usage). 
4. Selecione item de menu **Atualização**.
5. Selecione o item de menu **Para desenvolvedores**.
6. Habilite o **Modo de Desenvolvedor**.
7. [Role para baixo](gaze-and-commit.md#composite-gestures) e habilite o **Portal de Dispositivos**.
8. Se você estiver configurando o Portal de Dispositivos do Windows para poder implantar aplicativos nesse HoloLens por USB ou Wi-Fi, clique em **Emparelhar** para [gerar um PIN de emparelhamento](using-visual-studio.md). Saia do aplicativo Configurações no pop-up do PIN até inserir o PIN no Visual Studio durante sua primeira implantação.

   ![Habilitar o modo de desenvolvedor no aplicativo Configurações para Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Conectar-se por Wi-Fi

1. [Conecte seu HoloLens ao Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Pesquise o endereço IP do seu dispositivo.
   * Localize o endereço IP do dispositivo em **Configurações > Rede e Internet > Wi-Fi > Opções Avançadas**.
3. Em um navegador da Web em seu computador, acesse https://<SEU_ENDEREÇO_IP_DO_HOLOLENS>
   * O navegador exibirá a seguinte mensagem: “Há um problema com o certificado de segurança desse site”. Isso acontece porque o certificado emitido para o Device Portal é um certificado de teste. Você pode ignorar esse erro de certificado por enquanto e continuar.

## <a name="connecting-over-usb"></a>Conectar-se por USB

1. [Instale as ferramentas](install-the-tools.md) para verificar se você tem o Visual Studio Atualização 1 com as ferramentas para desenvolvedores do Windows 10 instaladas no computador. Isso permite a conectividade por USB.
2. Conecte seu HoloLens ao seu computador com um cabo Micro USB para HoloLens (1ª geração) ou USB-C para HoloLens 2.
3. Em um navegador da Web em seu computador, acesse [https://127.0.0.1:10080](https://127.0.0.1:10080).

## <a name="connecting-to-an-emulator"></a>Conectar-se a um emulador

Você também pode usar o Device Portal com seu emulador. Para se conectar ao Portal de Dispositivos, use a [barra de ferramentas](using-the-hololens-emulator.md). Clique neste ícone: ![Ícone Abrir o Portal de Dispositivos](images/emulator-deviceportal.png) **Abrir o Portal de Dispositivos**: Abre o Portal de Dispositivos do Windows para o sistema operacional HoloLens no emulador.

## <a name="creating-a-username-and-password"></a>Criar um nome de usuário e senha

![Configurar o acesso ao Portal de Dispositivos do Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurar o acesso ao Portal de Dispositivos do Windows*

Na primeira vez que se conectar ao Device Portal em seu HoloLens, você precisará criar um nome de usuário e senha.
1. Em um navegador da Web em seu computador, digite o endereço IP do HoloLens. A página Set up access é aberta.
2. Clique ou toque em **Solicitar pin** e examine a tela do HoloLens para obter o PIN gerado.
3. Insira o PIN na caixa de texto **PIN exibido em seu dispositivo**.
4. Insira o nome de usuário que você usará para se conectar ao Device Portal. Não é necessário ser um nome de MSA (conta da Microsoft) ou um nome de domínio.
5. Insira uma senha e confirme-a. A senha deve ter pelo menos sete caracteres de comprimento. Não é necessário ser uma senha de MSA ou de domínio.
6. Clique em **Emparelhar** para se conectar ao Portal de Dispositivos do Windows no HoloLens.

Se desejar alterar o nome de usuário ou a senha, você poderá repetir esse processo a qualquer momento acessando a página de segurança do dispositivo navegando até: https://<SEU_ENDEREÇO_IP_DO_HOLOLENS>/devicepair.htm.

## <a name="security-certificate"></a>Certificado de segurança

Se você vir um "erro de certificado" no navegador, poderá corrigi-lo criando uma relação de confiança com o dispositivo.

Cada HoloLens gera um certificado autoassinado exclusivo para sua conexão SSL. Por padrão, esse certificado não é confiável pelo navegador da Web do seu computador e você poderá receber um "erro de certificado". Ao baixar esse certificado do seu HoloLens (por USB ou uma rede Wi-Fi confiável) e torná-lo confiável em seu computador, você poderá se conectar com segurança ao seu dispositivo.
1. **Verifique se você está em uma rede segura (por USB ou uma rede Wi-Fi confiável).**
2. Baixe o certificado desse dispositivo da página "Segurança" no Portal de Dispositivos.
   * Navegue até: https://<SEU_ENDEREÇO_IP_DO_HOLOLENS>/devicepair.htm
   * Abra o nó de Sistema > Preferências. 
   * Role para baixo até Segurança do Dispositivo e clique no botão “Baixar o certificado deste dispositivo”.
3. Instale o certificado no repositório “Autoridades de Certificação Raiz Confiáveis” em seu computador.
   * No menu do Windows, digite: Gerencie Certificados de Computador e inicie o applet.
   * Expanda a pasta **Autoridade de Certificação Raiz Confiável**.
   * Clique na pasta **Certificados**.
   * No menu Ação, selecione: Todas as Tarefas > Importar...
   * Conclua o Assistente para Importação de Certificados, usando o arquivo de certificado baixado do Device Portal.
4. Reinicie o navegador.

>[!NOTE]
> Esse certificado só será confiável para o dispositivo e o usuário precisará passar pelo processo novamente se o dispositivo for atualizado.


## <a name="device-portal-pages"></a>Páginas do Device Portal

### <a name="home"></a>Inicial

![Página inicial do Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Página inicial do Portal de Dispositivos do Windows no Microsoft HoloLens*

A sessão do Device Portal é iniciada na home page. Acesse outras páginas a partir da barra de navegação no lado esquerdo da página inicial.

A barra de ferramentas na parte superior da página fornece acesso a recursos e status normalmente usados.
* **Online**: indica se o dispositivo está conectado ao Wi-Fi.
* **Desligamento**: desativa o dispositivo.
* **Reinicialização**: repete o ciclo de energia no dispositivo.
* **Segurança**: abre a página Segurança do Dispositivo.
* **Frio**: indica a temperatura do dispositivo.
* **A/C**: indica se o dispositivo está conectado e carregando.
* **Ajuda**: abre a página de documentação de interface REST.

A página inicial mostra as seguintes informações:
* **Status do Dispositivo:** monitora a integridade do dispositivo e relata erros críticos.
* **Informações do Windows:** mostra o nome do HoloLens e a versão do Windows instalada atualmente.
* A seção **Preferências** contém as seguintes configurações:
   * **DIP**: define a DIP (distância entre pupilas), que é a distância, em milímetros, entre o centro das pupilas do usuário quando ele olha para frente. A configuração entra em vigor imediatamente. O valor padrão é calculado automaticamente quando você configura seu dispositivo.
   * **Nome do dispositivo**: atribui um nome ao HoloLens. Você deve reinicializar o dispositivo depois de alterar esse valor para que ele entre em vigor. Depois de clicar em **Salvar**, uma caixa de diálogo perguntará se você deseja reiniciar o dispositivo imediatamente ou mais tarde.
   * **Configurações de suspensão**: define o tempo de espera antes que o dispositivo entre em suspensão quando ele estiver conectado e quando estiver na bateria.

### <a name="3d-view"></a>Modo de exibição 3D

![Página Modo de exibição 3D no Portal de Dispositivos do Windows no Microsoft HoloLens](images/3dview-1000px.png)<br>
*Página Modo de exibição 3D no Portal de Dispositivos do Windows no Microsoft HoloLens*

Use a página Modo de exibição 3D para ver como o HoloLens interpreta seus arredores. Navegue pelo modo de exibição usando o mouse:
* Rotação: clique com o botão esquerdo do mouse;
* Panorâmico: clique com o botão direito do mouse;
* Zoom: a rolagem do mouse.
* **Opções de acompanhamento**
   * ative o acompanhamento visual contínuo ao marcar **Forçar o acompanhamento visual**. 
   * **Pausar** interrompe o acompanhamento visual.
* **Opções de exibição**: define opções no modo de exibição 3D:
  * **Acompanhamento**: indica se o acompanhamento visual está ativo.
  * **Mostrar piso**: exibe um plano de piso quadriculado.
  * **Mostrar tronco**: exibe o tronco da exibição.
  * **Mostrar o plano de estabilização**: exibe o plano que o HoloLens usa para estabilizar o movimento.
  * **Mostrar malha**: exibe a malha de mapeamento espacial que representa seus arredores.
  * **Mostrar âncoras espaciais**: exibe âncoras espaciais para o aplicativo ativo. Você deve clicar no botão Atualizar para obter e atualizar as âncoras.
  * **Mostrar detalhes**: exibe as posições das mãos, os quatérnios de rotação da cabeça e o vetor de origem do dispositivo conforme eles mudam em tempo real.
  * **Botão tela inteira**: mostra o Modo de Exibição 3D em modo de tela inteira. Pressione ESC para sair do modo de exibição de tela inteira.
* **Reconstrução da superfície**: clique ou toque em **Atualizar** para exibir a malha de mapeamento espacial mais recente do dispositivo. Uma passagem completa pode levar um tempo para ser concluída (cerca de alguns segundos). A malha não é atualizada automaticamente no modo de exibição 3D, e você deve clicar manualmente em **Atualizar** para obter a malha mais recente do dispositivo. Clique em **Salvar** para salvar a malha de mapeamento espacial atual como um arquivo obj em seu computador.
* **Âncoras espaciais**: clique em Atualizar para exibir ou atualizar as âncoras espaciais do aplicativo ativo.

### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![Página Captura de Realidade Misturada no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Página Captura de Realidade Misturada no Portal de Dispositivos do Windows no Microsoft HoloLens*

Use a página Mixed Reality Capture para salvar fluxos de mídia do HoloLens.
* **Configurações**: controle os fluxos de mídia capturados verificando as seguintes configurações:
  * **Hologramas**: captura o conteúdo holográfico no fluxo de vídeo. Hologramas são renderizados em mono, não em estéreo.
  * **Câmera de PV**: captura o fluxo de vídeo da câmera de foto/vídeo.
  * **Áudio de microfone**: captura o áudio da matriz de microfones.
  * **Áudio de aplicativo**: captura o áudio do aplicativo em execução no momento.
  * **Renderizar da Câmera**: alinha a captura para ser da perspectiva da câmera de foto/vídeo, se [compatível com o aplicativo em execução](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (somente HoloLens 2).
  * **Qualidade da visualização dinâmica**: selecione a resolução de tela, a taxa de quadros e a taxa de streaming para a visualização dinâmica.
* Clique ou toque no botão **Visualização dinâmica** para mostrar o fluxo de captura. **Interromper a visualização dinâmica** interrompe o fluxo de captura.
* Clique ou toque em **Gravar** para iniciar a gravação do fluxo de realidade combinada, usando as configurações especificadas. **Interromper a gravação** encerra a gravação e a salva.
* Clique ou toque em **Tirar foto** para tirar uma imagem estática do fluxo de captura.
* **Vídeos e fotos**: mostra uma lista de capturas de vídeos e fotos feitas no dispositivo.

> [!NOTE]
> Há [limitações ao MRC simultâneo](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * se um aplicativo tentar acessar a câmera de foto/vídeo enquanto o Portal de Dispositivos do Windows estiver gravando um vídeo, a gravação será interrompida.
>   * O HoloLens 2 não interromperá a gravação de vídeo se o aplicativo acessar a câmera de foto/vídeo com o modo SharedReadOnly.
> * Se um aplicativo estiver usando a câmera de foto/vídeo, o Portal de Dispositivos do Windows poderá tirar uma foto ou gravar um vídeo.
> * Streaming ao vivo:
>   * O HoloLens (1ª geração) impede que um aplicativo acesse a câmera de foto/vídeo durante o streaming ao vivo do Portal de Dispositivos do Windows.
>   * O HoloLens (1ª geração) falhará ao realizar transmissão ao vivo se um aplicativo estiver usando ativamente a câmera de foto/vídeo.
>   * O HoloLens 2 interrompe automaticamente o streaming ao vivo quando um aplicativo tenta acessar a câmera de foto/vídeo no modo ExclusiveControl.
>   * O HoloLens 2 é capaz de iniciar uma transmissão ao vivo enquanto um aplicativo está usando ativamente a câmera de PV.

### <a name="performance-tracing"></a>Rastreamento de Desempenho

![Página Rastreamento de Desempenho no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Página Rastreamento de Desempenho no Portal de Dispositivos do Windows no Microsoft HoloLens*

Capture rastreamentos do [WPR](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (Windows Performance Recorder) no seu HoloLens.
* **Perfis disponíveis**: selecione o perfil WPR na lista suspensa e clique ou toque em **Iniciar** para iniciar o rastreamento.
* **Perfis personalizados**: clique ou toque em **Procurar** para escolher um perfil WPR do seu computador. Clique ou toque em **Carregar e iniciar** para iniciar o rastreamento.

Para interromper o rastreamento, clique no link para interromper. Fique nesta página até que o download do arquivo de rastreamento seja concluído.

Os arquivos ETL capturados podem ser abertos para análise no [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Processos

![Página Processos no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Página Processos no Portal de Dispositivos do Windows no Microsoft HoloLens*

Mostra detalhes sobre processos em execução no momento. Isso inclui aplicativos e processos do sistema.

### <a name="system-performance"></a>Desempenho do sistema

![Página Desempenho do Sistema no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Página Desempenho do Sistema no Portal de Dispositivos do Windows no Microsoft HoloLens*

Mostra gráficos em tempo real de informações de diagnóstico do sistema, como o uso de energia, a taxa de quadros e a carga da CPU.

Estas são as métricas disponíveis:
* **Energia SoC**: utilização instantânea de energia do sistema-em-um-chip, com base na média de um minuto
* **Energia do sistema**: utilização instantânea da energia do sistema, com base na média de um minuto
* **Taxa de quadros**: quadros por segundo, VBlanks perdidos por segundo e VBlanks perdidos consecutivos
* **GPU**: utilização do mecanismo GPU, percentual do total disponível
* **CPU**: porcentagem do total disponível
* **E/S**: lê e grava
* **Rede**: recebido e enviado
* **Memória**: total, em uso, confirmada, paginada e não paginada

### <a name="apps"></a>Aplicativos

![Página Aplicativos no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Página Aplicativos no Portal de Dispositivos do Windows no Microsoft HoloLens*

Gerencia os aplicativos instalados no HoloLens.
* **Aplicativos instalados**: remove e inicia aplicativos.
* **Aplicativos em execução**: lista os aplicativos que estão em execução no momento.
* **Instalar aplicativo**: seleciona pacotes de aplicativos para a instalação de uma pasta em seu computador/rede.
* **Dependência**: adiciona dependências para o aplicativo que você pretende instalar.
* **Implantar**: implanta o aplicativo selecionado + dependências no HoloLens.

### <a name="app-crash-dumps"></a>Despejos de Memória do Aplicativo

![Página Despejos de Memória do Aplicativo no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Página Despejos de Memória do Aplicativo no Portal de Dispositivos do Windows no Microsoft HoloLens*

Essa página permite que você colete despejos de memória para seus aplicativos de sideload. Marque a caixa de seleção **Despejos de Memória Habilitados** para cada aplicativo para o qual você deseja coletar despejos de memória. Retorne a essa página para coletar despejos de memória. Arquivos de despejo podem ser [abertos no Visual Studio para depuração](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Explorador de Arquivos

![Página Explorador de Arquivos no Portal de Dispositivos do Windows no Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Página Explorador de Arquivos no Portal de Dispositivos do Windows no Microsoft HoloLens*

Use o explorador de arquivos para procurar, carregar e baixar arquivos. Você pode trabalhar com arquivos na pasta Documentos, na pasta Imagens e nas pastas de armazenamento local para aplicativos implantados no Visual Studio ou no Portal de Dispositivos.

### <a name="kiosk-mode"></a>Modo de quiosque

>[!NOTE]
>O Modo de Quiosque só está disponível com o [Microsoft HoloLens Commercial Suite](commercial-features.md).

Confira o artigo [Configurar o HoloLens no modo de quiosque](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) no Windows IT Pro Center para obter instruções atualizadas sobre como habilitar o modo de quiosque por meio do Portal de Dispositivos do Windows.

### <a name="logging"></a>Log

![Página Log no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Página Log no Portal de Dispositivos do Windows no Microsoft HoloLens*

Gerencia o ETW (Rastreamento de Eventos para Windows) em tempo real no HoloLens.

Marque **Ocultar provedores** para mostrar somente a lista **Eventos**.
* **Provedores registrados**: seleciona o provedor ETW e o nível de rastreamento. O nível de rastreamento é um destes valores:
   1. Saída anormal ou encerramento
   2. Erros graves
   3. Avisos
   4. Avisos que não são de erro

Clique ou toque em **Habilitar** para iniciar o rastreamento. O provedor é adicionado à lista suspensa **Provedores Habilitados**.
* **Provedores personalizados**: seleciona um provedor ETW personalizado e o nível de rastreamento. Identifique o provedor pelo GUID. Não inclua colchetes no GUID.
* **Provedores habilitados**: lista os provedores habilitados. Selecione um provedor da lista suspensa e clique ou toque em **Desabilitar** para parar o rastreamento. Clique ou toque em **Parar todos** para suspender todo o rastreamento.
* **Histórico de provedores**: mostra os provedores ETW que foram habilitados durante a sessão atual. Clique ou toque em **Habilitar** para ativar um provedor que foi desabilitado. Clique ou toque em **Limpar** para limpar o histórico.
* **Eventos**: lista os eventos ETW dos provedores selecionados no formato de tabela. Essa tabela é atualizada em tempo real. Abaixo da tabela, clique no botão **Limpar** para excluir todos os eventos ETW da tabela. Isso não desabilita os provedores. Você pode clicar em **Salvar no arquivo** para exportar os atuais eventos ETW coletados para um arquivo CSV localmente.
* **Filtros**: permitem filtrar os eventos ETW coletados por ID, Palavra-chave, Nível, Nome do Provedor, Nome da Tarefa ou Texto. Você pode combinar vários critérios juntos:
   1. para critérios que se aplicam à mesma propriedade, os eventos que podem atender a qualquer um desses critérios são mostrados.
   2. Para critérios que se aplicam a uma propriedade diferente, os eventos devem atender a todos os critérios

Por exemplo, você pode especificar os critérios *(o Nome da Tarefa contém 'Foo' ou 'Bar') E (o Texto contém 'erro' ou 'aviso')*

### <a name="simulation"></a>Simulation

![Página Simulação no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Página Simulação no Portal de Dispositivos do Windows no Microsoft HoloLens*

Permite que você grave e reproduza dados de entrada para testes.
* **Sala de captura**: usado para baixar um arquivo de sala simulada que contém a malha de mapeamento espacial para os arredores do usuário. Dê um nome à sala e clique em **Capturar** para salvar os dados como um arquivo .xef em seu computador. Esse arquivo de sala pode ser carregado no emulador do HoloLens.
* **Gravação**: verifique os fluxos a serem gravados, dê um nome para a gravação e clique ou toque em **Gravar** para iniciar a gravação. Execute ações com o HoloLens e, em seguida, clique em **Interromper** para salvar os dados como um arquivo .xef em seu computador. Esse arquivo pode ser carregado no emulador ou dispositivo HoloLens.
* **Reprodução**: clique ou toque em **Carregar gravação** para selecionar um arquivo xef do computador e enviar os dados ao HoloLens.
* **Modo de controle**: selecione **Padrão** ou **Simulação** na lista suspensa e clique ou toque no botão **Definir** para selecionar o modo no HoloLens. Escolher "Simulação" desabilita os sensores reais em seu HoloLens e usa dados simulados carregados em vez disso. Se você alternar para "Simulação", o HoloLens não responderá ao usuário real até que você volte para "Padrão".

### <a name="networking"></a>Rede

![Página Rede no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Página Rede no Portal de Dispositivos do Windows no Microsoft HoloLens*

Gerencia conexões Wi-Fi no HoloLens.
* **Adaptadores WiFi**: selecione um adaptador e perfil de Wi-Fi usando os controles suspensos. Clique ou toque em **Conectar** para usar o adaptador selecionado.
* **Redes disponíveis**: lista as redes Wi-Fi às quais o HoloLens pode se conectar. Clique ou toque em **Atualizar** para atualizar a lista.
* **Configuração de IP**: mostra o endereço IP e outros detalhes da conexão de rede.

### <a name="virtual-input"></a>Entrada virtual

![Página Entrada Virtual no Portal de Dispositivos do Windows no Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Página Entrada Virtual no Portal de Dispositivos do Windows no Microsoft HoloLens*

Envia entrada do teclado da máquina remota para o HoloLens.

Clique ou toque na região abaixo de **Teclado virtual** para habilitar o envio de pressionamento de teclas ao HoloLens. Digite na caixa de texto **Texto da entrada** e clique ou toque em **Enviar** para enviar os pressionamentos de teclas ao aplicativo ativo.

## <a name="device-portal-rest-apis"></a>APIs REST do Portal de Dispositivos

Tudo no Portal de Dispositivos foi criado com base em [APIs REST](device-portal-api-reference.md), que você tem a opção de usar para acessar os dados e controlar o dispositivo de maneira programática.

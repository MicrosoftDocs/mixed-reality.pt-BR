---
title: Referência da API do portal de dispositivos
description: Referência da API para o do Windows Device Portal no HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, do Windows Device Portal, API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590608"
---
# <a name="device-portal-api-reference"></a>Referência da API do portal de dispositivos

Tudo na [Windows Device Portal](using-the-windows-device-portal.md) baseia-se em REST da API que você pode usar para acessar os dados e controlar seu dispositivo por meio de programação.

## <a name="app-deloyment"></a>Implantação de aplicativo

**/api/app/packagemanager/package (DELETE)**

Desinstala um aplicativo

Parâmetros
* pacote: Nome do arquivo do pacote a ser desinstalado.

**/API/App/packagemanager/Package (POST)**

Instala um aplicativo

Parâmetros
* pacote: Nome do arquivo do pacote a ser instalado.

carga
* corpo de http em conformidade com várias partes

**/api/app/packagemanager/packages (GET)**

Recupera a lista de aplicativos instalados no sistema, com detalhes

Retornar dados
* Lista de pacotes instalados com detalhes

**/api/app/packagemanager/state (GET)**

Obtém o status na instalação do aplicativo de progresso

## <a name="dump-collection"></a>Coleta de despejo

**/api/debug/dump/usermode/crashcontrol (DELETE)**

Desabilita a coleta de despejo para um aplicativo com sideload de falhas

Parâmetros
* packageFullname: nome do pacote

**/api/debug/dump/usermode/crashcontrol (GET)**

Obtém as configurações para aplicativos de sideload a coleta de despejo de memória

Parâmetros
* packageFullname: nome do pacote

**/api/debug/dump/usermode/crashcontrol (POST)**

Habilita e define as configurações de controle de despejo para um aplicativo de sideload

Parâmetros
* packageFullname: nome do pacote

**/api/debug/dump/usermode/crashdump (DELETE)**

Exclui um despejo de memória para um aplicativo de sideload

Parâmetros
* packageFullname: nome do pacote
* nome do arquivo: nome do arquivo de despejo

**/api/debug/dump/usermode/crashdump (GET)**

Recupera um despejo de memória para um aplicativo de sideload

Parâmetros
* packageFullname: nome do pacote
* nome do arquivo: nome do arquivo de despejo

Retornar dados
* Arquivo de despejo. Inspecionar com o Visual Studio ou WinDbg

**/api/debug/dump/usermode/dumps (GET)**

Retorna a lista de todos os despejos de memória para aplicativos sideloaded

Retornar dados
* Despejos de lista de falhas por aplicativo carregado do lado do

## <a name="etw"></a>ETW

**/API/ETW/Providers (GET)**

Enumera os provedores registrados

Retornar dados
* Lista de provedores, o nome amigável e o GUID

**/api/etw/session/realtime (GET/WebSocket)**

Cria uma sessão ETW em tempo real; gerenciado por um websocket.

Retornar dados
* Eventos ETW de provedores habilitados

## <a name="holographic-os"></a>Sistema operacional holográfico

**/API/holographic/os/ETW/customproviders (GET)**

Retorna uma lista de provedores ETW específicos HoloLens que não estão registrados com o sistema

**/api/holographic/os/services (GET)**

Retorna os estados de todos os serviços em execução.

**/api/holographic/os/settings/ipd (GET)**

Obtém o IPD armazenado (Interpupillary distância) em milímetros

**/api/holographic/os/settings/ipd (POST)**

Define o IPD

Parâmetros
* IPD: Novo valor IPD a ser definido em milímetros

**/API/holographic/os/webmanagement/Settings/HTTPS (GET)**

Obter requisitos de HTTPS para o Device Portal

**/API/holographic/os/webmanagement/Settings/HTTPS (POST)**

Define os requisitos de HTTPS para o Portal de dispositivos

Parâmetros
* obrigatório: Sim, não ou padrão

## <a name="holographic-perception"></a>Percepção holográfica

**/api/holographic/perception/client (GET/WebSocket)**

Aceita o websocket upgrades e executa o cliente percepção que envia as atualizações em 30 fps.

Parâmetros
* clientmode: "ativo" força o modo de controle visual quando não puder ser estabelecida passivamente

## <a name="holographic-thermal"></a>Holográfico térmico

**/api/holographic/thermal/stage (GET)**

Obter o estágio térmico do dispositivo (0 normal, 1 passiva, 2 crítico)

## <a name="perception-simulation-control"></a>Controle de simulação de percepção

**/API/holographic/Simulation/Control/Mode (GET)**

Obter o modo de simulação

**/API/holographic/Simulation/Control/Mode (POST)**

Definir o modo de simulação

Parâmetros
* modo: modo de simulação: padrão, a simulação, remoto, herdado

**/API/holographic/Simulation/Control/Stream (excluir)**

Exclua um fluxo de controle.

**/api/holographic/simulation/control/stream (GET/WebSocket)**

Abra uma conexão de soquete da web para um fluxo de controle.

**/API/holographic/Simulation/Control/Stream (POST)**

Criar um fluxo de controle (prioridade é necessária) ou dados de postagem em um fluxo criado (o streamId é necessário). Os dados postados deve ser do tipo ' application/octet-stream'.

## <a name="perception-simulation-playback"></a>Reprodução de simulação de percepção

**/API/holographic/Simulation/playback/File (excluir)**

Exclua uma gravação.

Parâmetros
* gravação: Nome do registro para excluir.

**/API/holographic/Simulation/playback/File (POST)**

Carregue uma gravação.

**/API/holographic/Simulation/playback/Files (GET)**

Obtenha todas as gravações.

**/API/holographic/Simulation/playback/Session (GET)**

Obter o estado atual de reprodução de uma gravação.

Parâmetros
* gravação: Nome de gravação.

**/API/holographic/Simulation/playback/Session/File (excluir)**

Descarrega uma gravação.

Parâmetros
* gravação: Nome do registro para descarregar.

**/API/holographic/Simulation/playback/Session/File (POST)**

Uma gravação de carga.

Parâmetros
* gravação: Nome do registro para carregar.

**/API/holographic/Simulation/playback/Session/Files (GET)**

Obter todos carregadas gravações.

**/API/holographic/Simulation/playback/Session/pause (POST)**

Pause uma gravação.

Parâmetros
* gravação: Nome de gravação.

**/API/holographic/Simulation/playback/Session/Play (POST)**

Reproduzir uma gravação.

Parâmetros
* gravação: Nome de gravação.

**/API/holographic/Simulation/playback/Session/Stop (POST)**

Pare uma gravação.

Parâmetros
* gravação: Nome de gravação.

**/API/holographic/Simulation/playback/Session/Types (GET)**

Obtenha os tipos de dados em uma gravação carregada.

Parâmetros
* gravação: Nome de gravação.

## <a name="perception-simulation-recording"></a>Gravação de simulação de percepção

**/API/holographic/Simulation/Recording/Start (POST)**

Inicie uma gravação. Apenas uma única gravação pode estar ativa ao mesmo tempo. Um cabeçalho, mãos, spatialMapping ou ambiente deve ser definido.

Parâmetros
* cabeçalho: Definido como 1 para o registro de dados principal.
* mãos: Definido como 1 para registrar dados de mão.
* spatialMapping: Definido como 1 para registrar o mapeamento espacial.
* ambiente: Definido como 1 para registrar dados de ambiente.
* nome: Nome da gravação.
* singleSpatialMappingFrame : Definido como 1 para registrar somente um quadro de mapeamento espacial único.

**/API/holographic/Simulation/Recording/status (GET)**

Obter gravação de estado.

**/API/holographic/Simulation/Recording/Stop (GET)**

Interrompa a gravação atual. Gravação será retornada como um arquivo.

## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/api/holographic/mrc/file (DELETE)**

Exclui uma registro do dispositivo de realidade misturada.

Parâmetros
* nome do arquivo: O nome, hex64 codificado, do arquivo a ser excluído

**/API/holographic/MRC/Settings (GET)**

Obtém o padrão realidade misturada configurações de captura

**/api/holographic/mrc/file (GET)**

Baixa um arquivo de realidade mista do dispositivo. Op uso = parâmetro de consulta do stream para streaming.

Parâmetros
* nome do arquivo: O nome, hex64 codificado, do arquivo de vídeo para obter
* op : stream

**/api/holographic/mrc/thumbnail (GET)**

Obtém a imagem em miniatura para o arquivo especificado.

Parâmetros
* nome do arquivo: O nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada.

**/api/holographic/mrc/status (GET)**

Obtém o status da realidade misturada registrado (em execução, parado)

**/api/holographic/mrc/files (GET)**

Retorna a lista de arquivos de realidade misturada armazenados no dispositivo

**/API/holographic/MRC/Settings (POST)**

Define o padrão realidade misturada configurações de captura

**/API/holographic/MRC/Video/Control/Start (POST)**

Inicia uma gravação de realidade misturada

Parâmetros
* holo: capturar vntana: true ou false
* VP: captura PV câmera: true ou false
* MIC: captura microfone: true ou false
* loopback: capturar o áudio do aplicativo: true ou false

**/API/holographic/MRC/Video/Control/Stop (POST)**

Paradas de gravação de realidade mista do atual

**/API/holographic/MRC/Photo (POST)**

Tira uma foto de realidade mista e cria um arquivo no dispositivo

Parâmetros
* holo: capturar vntana: true ou false
* VP: captura PV câmera: true ou false

Realidade mista de Streaming

**/api/holographic/stream/live.mp4 (GET)**

Inicia um download em partes de um mp4 fragmentado

Parâmetros
* holo: capturar vntana: true ou false
* VP: captura PV câmera: true ou false
* MIC: captura microfone: true ou false
* loopback: capturar o áudio do aplicativo: true ou false

**/api/holographic/stream/live_high.mp4 (GET)**

Inicia um download em partes de um mp4 fragmentado

Parâmetros
* holo: capturar vntana: true ou false
* VP: captura PV câmera: true ou false
* MIC: captura microfone: true ou false
* loopback: capturar o áudio do aplicativo: true ou false

**/api/holographic/stream/live_low.mp4 (GET)**

Inicia um download em partes de um mp4 fragmentado

Parâmetros
* holo: capturar vntana: true ou false
* VP: captura PV câmera: true ou false
* MIC: captura microfone: true ou false
* loopback: capturar o áudio do aplicativo: true ou false

**/api/holographic/stream/live_med.mp4 (GET)**

Inicia um download em partes de um mp4 fragmentado

Parâmetros
* holo: capturar vntana: true ou false
* VP: captura PV câmera: true ou false
* MIC: captura microfone: true ou false
* loopback: capturar o áudio do aplicativo: true ou false

## <a name="networking"></a>Rede

**/api/networking/ipconfig (GET)**

Obtém a configuração de ip atual

## <a name="os-information"></a>Informações do sistema operacional

**/api/os/info (GET)**

Obtém informações do sistema operacional

**/api/os/machinename (GET)**

Obtém o nome do computador

**/api/os/machinename (POST)**

Define o nome do computador

Parâmetros
* nome: Novo nome de máquina, hex64 codificado, para definir como

## <a name="performance-data"></a>Dados de desempenho

**/api/resourcemanager/processes (GET)**

Retorna a lista de processos em execução com detalhes

Retornar dados
* JSON com a lista de processos e os detalhes de cada processo.

**/api/resourcemanager/systemperf (GET)**

Retorna estatísticas de desempenho do sistema (e/s de leitura/gravação, estatísticas de memória etc.

Retornar dados
* JSON com informações do sistema: CPU, GPU, memória, rede e e/s

## <a name="power"></a>Potência

**/api/power/battery (GET)**

Obtém o estado atual da bateria

**/api/power/state (GET)**

Verifica se o sistema está em um estado de baixo consumo de energia

## <a name="remote-control"></a>Controle Remoto

**/api/control/restart (POST)**

Reinicia o dispositivo de destino

**/API/Control/Shutdown (POST)**

Desliga o dispositivo de destino

## <a name="task-manager"></a>Gerenciador de Tarefas

**/api/taskmanager/app (DELETE)**

Interrompe um aplicativo moderno

Parâmetros
* pacote: Nome completo do pacote de aplicativo, hex64 codificado
* forcestop: Forçar todos os processos para parar (= Sim)

**/api/taskmanager/app (POST)**

Inicia um aplicativo moderno

Parâmetros
* AppID: Codificação de hex64 PRAID do aplicativo para iniciar,
* pacote: Nome completo do pacote de aplicativo, hex64 codificado

## <a name="wifi-management"></a>Gerenciamento de Wi-Fi

**/api/wifi/interfaces (GET)**

Enumera as interfaces de rede sem fio

Retornar dados
* Lista de interfaces sem fio com detalhes (GUID, descrição etc.)

**/api/wifi/network (DELETE)**

Exclui um perfil associado a uma rede em uma interface especificada

Parâmetros
* interface: guid da interface de rede
* perfil: nome do perfil

**/api/wifi/networks (GET)**

Enumera as redes sem fio na interface de rede especificado

Parâmetros
* interface: guid da interface de rede

Retornar dados
* Lista de redes sem fio encontrado na interface de rede com detalhes

**/API/WiFi/Network (POST)**

Se conecta ou desconecta-se a uma rede na interface especificada

Parâmetros
* interface: guid da interface de rede
* SSID: ssid, hex64 codificado, para se conectar a
* op: conectar ou desconectar
* CreateProfile: Sim ou não
* chave: compartilhado hex64 chave, codificado

## <a name="windows-performance-recorder"></a>Gravador de desempenho do Windows

**/API/WPR/customtrace (POST)**

Carrega um perfil do WPR e inicia o rastreamento usando o perfil carregado.

carga
* corpo de http em conformidade com várias partes

Retornar dados
* Retorna o status da sessão WPR.

**/api/wpr/status (GET)**

Recupera o status da sessão do WPR

Retornar dados
* Status da sessão WPR.

**/api/wpr/trace (GET)**

Interrompe uma sessão de rastreamento do WPR (desempenho)

Retornar dados
* Retorna o arquivo de ETL de rastreamento

**/API/WPR/trace (POST)**

Inicia um WPR (desempenho) sessões de rastreamento

Parâmetros
* perfil: Nome do perfil. Perfis disponíveis são armazenados em perfprofiles/profiles.json

Retornar dados
* No início, retorna o status da sessão WPR.

## <a name="see-also"></a>Consulte também
* [Usando o Windows Device Portal](using-the-windows-device-portal.md)
* [Núcleo do Portal de dispositivo referência da API (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

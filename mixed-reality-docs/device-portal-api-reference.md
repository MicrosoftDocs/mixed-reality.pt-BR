---
title: Referência da API do portal do dispositivo
description: Referência de API para o portal de dispositivo do Windows no HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portal de dispositivos Windows, API
ms.openlocfilehash: 236de35c2c736fc5a0289b7be1f1548f0a08fa26
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278234"
---
# <a name="device-portal-api-reference"></a>Referência da API do portal do dispositivo

Tudo no [portal de dispositivos do Windows](using-the-windows-device-portal.md) é criado sobre as APIs REST que você pode usar para acessar os dados e controlar seu dispositivo de forma programática.

## <a name="app-deloyment"></a>Implantação do aplicativo

**/API/app/PackageManager/Package (excluir)**

Desinstala um aplicativo

Parâmetros
* Package: nome de arquivo do pacote a ser desinstalado.

**/API/app/PackageManager/Package (POST)**

Instala um aplicativo

Parâmetros
* Package: nome do arquivo do pacote a ser instalado.

Carga
* corpo http de conformidade de várias partes

**/API/app/PackageManager/Packages (GET)**

Recupera a lista de aplicativos instalados no sistema, com detalhes

Retornar dados
* Lista de pacotes instalados com detalhes

**/API/app/PackageManager/State (GET)**

Obtém o status da instalação do aplicativo em andamento

## <a name="dump-collection"></a>Coleta de despejo

**/API/Debug/dump/UserMode/crashcontrol (excluir)**

Desabilita a coleta de despejo de memória para um aplicativo Sideload

Parâmetros
* packageFullname: nome do pacote

**/API/Debug/dump/UserMode/crashcontrol (GET)**

Obtém as configurações para coleta de despejo de memória de aplicativos Sideload

Parâmetros
* packageFullname: nome do pacote

**/API/Debug/dump/UserMode/crashcontrol (POST)**

Habilita e define as configurações de controle de despejo para um aplicativo Sideload

Parâmetros
* packageFullname: nome do pacote

**/API/Debug/dump/UserMode/crashdump (excluir)**

Exclui um despejo de memória para um aplicativo Sideload

Parâmetros
* packageFullname: nome do pacote
* fileName: nome do arquivo de despejo

**/API/Debug/dump/UserMode/crashdump (GET)**

Recupera um despejo de memória para um aplicativo Sideload

Parâmetros
* packageFullname: nome do pacote
* fileName: nome do arquivo de despejo

Retornar dados
* Arquivo de despejo. Inspecione com o WinDbg ou o Visual Studio

**/API/Debug/dump/UserMode/dumps (GET)**

Retorna a lista de todos os despejos de memória para aplicativos Sideload

Retornar dados
* Lista de despejos de memória por aplicativo carregado por lado

## <a name="etw"></a>ETW

**/API/ETW/Providers (GET)**

Enumera provedores registrados

Retornar dados
* Lista de provedores, nome amigável e GUID

**/API/ETW/Session/Realtime (obter/WebSocket)**

Cria uma sessão de ETW em tempo real; gerenciado em um WebSocket.

Retornar dados
* Eventos ETW dos provedores habilitados

## <a name="holographic-os"></a>Sistema operacional holográfico

**/API/Holographic/os/ETW/customproviders (GET)**

Retorna uma lista de provedores de ETW específicos do HoloLens que não estão registrados no sistema

**/API/Holographic/os/Services (GET)**

Retorna os Estados de todos os serviços em execução.

**/API/Holographic/os/Settings/IPD (GET)**

Obtém o IPD armazenado (distância interpupillary) em milímetros

**/API/Holographic/os/Settings/IPD (POST)**

Define o IPD

Parâmetros
* IPD: novo valor de IPD a ser definido em milímetros

**/API/Holographic/os/webmanagement/Settings/HTTPS (GET)**

Obter requisitos de HTTPS para o Device Portal

**/API/Holographic/os/webmanagement/Settings/HTTPS (POST)**

Define os requisitos de HTTPS para o portal do dispositivo

Parâmetros
* obrigatório: Sim, não ou padrão

## <a name="holographic-perception"></a>Percepção de Holographic

**/API/Holographic/Perception/Client (obter/WebSocket)**

Aceita atualizações do WebSocket e executa um cliente de percepção que envia atualizações a 30 fps.

Parâmetros
* clientmode: "ativo" força o modo de controle visual quando ele não pode ser estabelecido passivamente

## <a name="holographic-thermal"></a>Holographic térmico

**/API/Holographic/Thermal/Stage (GET)**

Obter o estágio térmico do dispositivo (0 normal, 1 quente, 2 crítico)

## <a name="perception-simulation-control"></a>Controle de simulação de percepção

**/API/Holographic/Simulation/Control/Mode (GET)**

Obter o modo de simulação

**/API/Holographic/Simulation/Control/Mode (POST)**

Definir o modo de simulação

Parâmetros
* modo: modo de simulação: padrão, simulação, remoto, herdado

**/API/Holographic/Simulation/Control/Stream (excluir)**

Excluir um fluxo de controle.

**/API/Holographic/Simulation/Control/Stream (obter/WebSocket)**

Abra uma conexão de soquete da Web para um fluxo de controle.

**/API/Holographic/Simulation/Control/Stream (POST)**

Crie um fluxo de controle (prioridade necessária) ou poste dados em um fluxo criado (streamid necessário). Espera-se que os dados postados sejam do tipo ' application/octet-stream '.

## <a name="perception-simulation-playback"></a>Reprodução da simulação de percepção

**/API/Holographic/Simulation/playback/File (excluir)**

Excluir uma gravação.

Parâmetros
* gravação: o nome da gravação a ser excluída.

**/API/Holographic/Simulation/playback/File (POST)**

Carregar uma gravação.

**/API/Holographic/Simulation/playback/Files (GET)**

Obter todas as gravações.

**/API/Holographic/Simulation/playback/Session (GET)**

Obter o estado de reprodução atual de uma gravação.

Parâmetros
* gravação: nome da gravação.

**/API/Holographic/Simulation/playback/Session/File (excluir)**

Descarregar uma gravação.

Parâmetros
* gravação: nome da gravação a ser descarregada.

**/API/Holographic/Simulation/playback/Session/File (POST)**

Carregar uma gravação.

Parâmetros
* gravação: o nome da gravação a ser carregada.

**/API/Holographic/Simulation/playback/Session/Files (GET)**

Obter todas as gravações carregadas.

**/API/Holographic/Simulation/playback/Session/PAUSE (POST)**

Pausar uma gravação.

Parâmetros
* gravação: nome da gravação.

**/API/Holographic/Simulation/playback/Session/Play (POST)**

Reproduzir uma gravação.

Parâmetros
* gravação: nome da gravação.

**/API/Holographic/Simulation/playback/Session/Stop (POST)**

Parar uma gravação.

Parâmetros
* gravação: nome da gravação.

**/API/Holographic/Simulation/playback/Session/Types (GET)**

Obter os tipos de dados em uma gravação carregada.

Parâmetros
* gravação: nome da gravação.

## <a name="perception-simulation-recording"></a>Gravação da simulação de percepção

**/API/Holographic/Simulation/Recording/Start (POST)**

Inicie uma gravação. Apenas uma única gravação pode estar ativa de uma vez. É necessário definir um dos cabeçalhos, as mãos, spatialMapping ou ambiente.

Parâmetros
* Cabeçalho: Defina como 1 para registrar dados de cabeçalho.
* Hands: Defina como 1 para gravar dados de mão.
* spatialMapping: Defina como 1 para registrar o mapeamento espacial.
* ambiente: Defina como 1 para gravar dados do ambiente.
* Nome: o nome da gravação.
* singleSpatialMappingFrame: Defina como 1 para gravar apenas um único quadro de mapeamento espacial.

**/API/Holographic/Simulation/Recording/status (GET)**

Obter estado de gravação.

**/API/Holographic/Simulation/Recording/Stop (GET)**

Parar a gravação atual. A gravação será retornada como um arquivo.

## <a name="mixed-reality-capture"></a>Mixed Reality Capture

**/API/Holographic/MRC/File (GET)**

Baixa um arquivo de realidade misturada do dispositivo. Use op = Stream Query parâmetro para streaming.

Parâmetros
* filename: nome, hex64 codificado, do arquivo de vídeo a ser obtido
* op: fluxo

**/API/Holographic/MRC/File (excluir)**

Exclui uma gravação de realidade misturada do dispositivo.

Parâmetros
* filename: nome, hex64 codificado, do arquivo a ser excluído

**/API/Holographic/MRC/Files (GET)**

Retorna a lista de arquivos de realidade misturada armazenados no dispositivo

**/API/Holographic/MRC/Photo (POST)**

Usa uma foto de realidade misturada e cria um arquivo no dispositivo

Parâmetros
* holo: capturar hologramas: true ou false (o padrão é false)
* PV: capturar câmera PV: true ou false (o padrão é false)
* RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)

**/API/Holographic/MRC/Settings (GET)**

Obtém as configurações padrão da captura de realidade misturada

**/API/Holographic/MRC/Settings (POST)**

Define as configurações padrão de captura de realidade misturada.  Algumas dessas configurações são aplicadas à captura de vídeo e foto da MRC do sistema.

**/API/Holographic/MRC/status (GET)**

Obtém o status da realidade misturada registrada (em execução, parada)

**/API/Holographic/MRC/Thumbnail (GET)**

Obtém a imagem em miniatura do arquivo especificado.

Parâmetros
* filename: nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada

**/API/Holographic/MRC/Video/Control/Start (POST)**

Inicia uma gravação de realidade misturada

Parâmetros
* holo: capturar hologramas: true ou false (o padrão é false)
* PV: capturar câmera PV: true ou false (o padrão é false)
* MIC: capturar microfone: true ou false (o padrão é false)
* loopback: capturar o áudio do aplicativo: true ou false (o padrão é false)
* RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)
* Vstab: (somente HoloLens 2) habilitar estabilização de vídeo: true ou false (o padrão é true)
* vstabbuffer: (somente HoloLens 2) latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)

**/API/Holographic/MRC/Video/Control/Stop (POST)**

Interrompe a gravação atual da realidade misturada

## <a name="mixed-reality-streaming"></a>Streaming de realidade misturada

O HoloLens dá suporte à visualização dinâmica de realidade misturada por meio do download em partes de um MP4 fragmentado.

Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:
* holo: capturar hologramas: verdadeiro ou falso
* PV: capturar câmera PV: verdadeiro ou falso
* MIC: capturar microfone: verdadeiro ou falso
* loopback: capturar áudio do aplicativo: verdadeiro ou falso

Se nenhum deles for especificado: os hologramas, a câmera de foto/vídeo e o áudio do aplicativo serão capturados<br>
Se houver algum especificado: os parâmetros não especificados serão padronizados como false

Parâmetros opcionais (somente HoloLens 2)
* RenderFromCamera: Render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)
* Vstab: habilitar estabilização de vídeo: true ou false (o padrão é false)
* vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)

**/API/Holographic/Stream/Live.MP4 (GET)**

1280x720p 30fps 5Mbit Stream.

**/API/Holographic/Stream/live_high. MP4 (GET)**

1280x720p 30fps 5Mbit Stream.

**/API/Holographic/Stream/live_med. MP4 (GET)**

Um fluxo 854x480p 30fps 2.5 Mbit.

**/API/Holographic/Stream/live_low. MP4 (GET)**

Um fluxo 428x240p 15fps 0,6 Mbit.

## <a name="networking"></a>Rede

**/API/Networking/ipconfig (GET)**

Obter a configuração de IP atual

## <a name="os-information"></a>Informações do sistema operacional

**/API/os/info (GET)**

Obtém informações do sistema operacional

**/API/os/MachineName (GET)**

Obtém o nome do computador

**/API/os/MachineName (POST)**

Define o nome do computador

Parâmetros
* Nome: novo nome do computador, hex64 codificado, para definir como

## <a name="performance-data"></a>Dados de desempenho

**/API/ResourceManager/Processes (GET)**

Retorna a lista de processos em execução com detalhes

Retornar dados
* JSON com lista de processos e detalhes para cada processo

**/API/ResourceManager/systemperf (GET)**

Retorna estatísticas de desempenho do sistema (leitura/gravação de e/s, estatísticas de memória etc.)

Retornar dados
* JSON com informações do sistema: CPU, GPU, memória, rede, e/s

## <a name="power"></a>Energia

**/API/Power/Battery (GET)**

Obtém o estado da bateria atual

**/API/Power/State (GET)**

Verifica se o sistema está em um estado de baixa energia

## <a name="remote-control"></a>Controle Remoto

**/API/Control/Restart (POST)**

Reinicia o dispositivo de destino

**/API/Control/Shutdown (POST)**

Desliga o dispositivo de destino

## <a name="task-manager"></a>Gerenciador de Tarefas

**/API/taskmanager/app (excluir)**

Para um aplicativo moderno

Parâmetros
* pacote: nome completo do pacote do aplicativo, codificado hex64
* forcestop: forçar a interrupção de todos os processos (= Sim)

**/API/taskmanager/app (POST)**

Inicia um aplicativo moderno

Parâmetros
* AppID: PRAID do aplicativo a ser iniciado, hex64 codificado
* pacote: nome completo do pacote do aplicativo, codificado hex64

## <a name="wifi-management"></a>Gerenciamento de WiFi

**/API/WiFi/interfaces (GET)**

Enumera interfaces de rede sem fio

Retornar dados
* Lista de interfaces sem fio com detalhes (GUID, descrição, etc.)

**/API/WiFi/Network (excluir)**

Exclui um perfil associado a uma rede em uma interface especificada

Parâmetros
* interface: GUID de interface de rede
* Perfil: nome do perfil

**/API/WiFi/Networks (GET)**

Enumera redes sem fio na interface de rede especificada

Parâmetros
* interface: GUID de interface de rede

Retornar dados
* Lista de redes sem fio encontradas na interface de rede com detalhes

**/API/WiFi/Network (POST)**

Conecta ou desconecta-se a uma rede na interface especificada

Parâmetros
* interface: GUID de interface de rede
* SSID: SSID, hex64 codificado, para se conectar ao
* op: conectar ou desconectar
* CreateProfile: Sim ou não
* chave: chave compartilhada, hex64 codificada

## <a name="windows-performance-recorder"></a>Gravador de desempenho do Windows

**/API/WPR/customtrace (POST)**

Carrega um perfil WPR e inicia o rastreamento usando o perfil carregado.

Carga
* corpo http de conformidade de várias partes

Retornar dados
* Retorna o status da sessão WPR.

**/API/WPR/status (GET)**

Recupera o status da sessão WPR

Retornar dados
* Status da sessão WPR.

**/API/WPR/Trace (GET)**

Interrompe uma sessão de rastreamento de WPR (desempenho)

Retornar dados
* Retorna o arquivo ETL de rastreamento

**/API/WPR/Trace (POST)**

Inicia uma sessão de rastreamento WPR (desempenho)

Parâmetros
* Perfil: nome do perfil. Os perfis disponíveis são armazenados em perfprofiles/Profiles. JSON

Retornar dados
* Em Iniciar, retorna o status da sessão WPR.

## <a name="see-also"></a>Consulte também
* [Como usar o Portal de Dispositivos do Windows](using-the-windows-device-portal.md)
* [Referência da API principal do portal do dispositivo (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

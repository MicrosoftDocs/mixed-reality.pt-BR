---
title: Referência de API do portal de dispositivos
description: Referência de API para o portal de dispositivo do Windows no HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portal de dispositivos Windows, API
ms.openlocfilehash: 8c9d60f458cddd3ba258aed0ee82f7aa16c10ba6
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83227941"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="b97c4-104">Referência de API do portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="b97c4-104">Device portal API reference</span></span>

<span data-ttu-id="b97c4-105">Tudo no [portal de dispositivos do Windows](using-the-windows-device-portal.md) é criado sobre as APIs REST que você pode usar para acessar os dados e controlar seu dispositivo de forma programática.</span><span class="sxs-lookup"><span data-stu-id="b97c4-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="b97c4-106">Implantação do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b97c4-106">App deloyment</span></span>

<span data-ttu-id="b97c4-107">**/API/app/PackageManager/Package (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="b97c4-108">Desinstala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="b97c4-108">Uninstalls an app</span></span>

<span data-ttu-id="b97c4-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-109">Parameters</span></span>
* <span data-ttu-id="b97c4-110">Package: nome de arquivo do pacote a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="b97c4-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="b97c4-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="b97c4-112">Instala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="b97c4-112">Installs an App</span></span>

<span data-ttu-id="b97c4-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-113">Parameters</span></span>
* <span data-ttu-id="b97c4-114">Package: nome do arquivo do pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="b97c4-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="b97c4-115">Carga útil</span><span class="sxs-lookup"><span data-stu-id="b97c4-115">Payload</span></span>
* <span data-ttu-id="b97c4-116">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="b97c4-116">multi-part conforming http body</span></span>

<span data-ttu-id="b97c4-117">**/API/app/PackageManager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="b97c4-118">Recupera a lista de aplicativos instalados no sistema, com detalhes</span><span class="sxs-lookup"><span data-stu-id="b97c4-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="b97c4-119">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-119">Return data</span></span>
* <span data-ttu-id="b97c4-120">Lista de pacotes instalados com detalhes</span><span class="sxs-lookup"><span data-stu-id="b97c4-120">List of installed packages with details</span></span>

<span data-ttu-id="b97c4-121">**/API/app/PackageManager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="b97c4-122">Obtém o status da instalação do aplicativo em andamento</span><span class="sxs-lookup"><span data-stu-id="b97c4-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="b97c4-123">Despejar coleção</span><span class="sxs-lookup"><span data-stu-id="b97c4-123">Dump collection</span></span>

<span data-ttu-id="b97c4-124">**/API/Debug/dump/UserMode/crashcontrol (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="b97c4-125">Desabilita a coleta de despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="b97c4-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="b97c4-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-126">Parameters</span></span>
* <span data-ttu-id="b97c4-127">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="b97c4-127">packageFullname : package name</span></span>

<span data-ttu-id="b97c4-128">**/API/Debug/dump/UserMode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="b97c4-129">Obtém as configurações para coleta de despejo de memória de aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="b97c4-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="b97c4-130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-130">Parameters</span></span>
* <span data-ttu-id="b97c4-131">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="b97c4-131">packageFullname : package name</span></span>

<span data-ttu-id="b97c4-132">**/API/Debug/dump/UserMode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="b97c4-133">Habilita e define as configurações de controle de despejo para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="b97c4-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="b97c4-134">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-134">Parameters</span></span>
* <span data-ttu-id="b97c4-135">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="b97c4-135">packageFullname : package name</span></span>

<span data-ttu-id="b97c4-136">**/API/Debug/dump/UserMode/crashdump (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="b97c4-137">Exclui um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="b97c4-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="b97c4-138">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-138">Parameters</span></span>
* <span data-ttu-id="b97c4-139">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="b97c4-139">packageFullname : package name</span></span>
* <span data-ttu-id="b97c4-140">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="b97c4-140">fileName : dump file name</span></span>

<span data-ttu-id="b97c4-141">**/API/Debug/dump/UserMode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="b97c4-142">Recupera um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="b97c4-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="b97c4-143">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-143">Parameters</span></span>
* <span data-ttu-id="b97c4-144">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="b97c4-144">packageFullname : package name</span></span>
* <span data-ttu-id="b97c4-145">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="b97c4-145">fileName : dump file name</span></span>

<span data-ttu-id="b97c4-146">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-146">Return data</span></span>
* <span data-ttu-id="b97c4-147">Arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="b97c4-147">Dump file.</span></span> <span data-ttu-id="b97c4-148">Inspecione com o WinDbg ou o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b97c4-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="b97c4-149">**/API/Debug/dump/UserMode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="b97c4-150">Retorna a lista de todos os despejos de memória para aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="b97c4-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="b97c4-151">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-151">Return data</span></span>
* <span data-ttu-id="b97c4-152">Lista de despejos de memória por aplicativo carregado por lado</span><span class="sxs-lookup"><span data-stu-id="b97c4-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="b97c4-153">ETW</span><span class="sxs-lookup"><span data-stu-id="b97c4-153">ETW</span></span>

<span data-ttu-id="b97c4-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="b97c4-155">Enumera provedores registrados</span><span class="sxs-lookup"><span data-stu-id="b97c4-155">Enumerates registered providers</span></span>

<span data-ttu-id="b97c4-156">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-156">Return data</span></span>
* <span data-ttu-id="b97c4-157">Lista de provedores, nome amigável e GUID</span><span class="sxs-lookup"><span data-stu-id="b97c4-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="b97c4-158">**/API/ETW/Session/Realtime (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="b97c4-159">Cria uma sessão de ETW em tempo real; gerenciado em um WebSocket.</span><span class="sxs-lookup"><span data-stu-id="b97c4-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="b97c4-160">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-160">Return data</span></span>
* <span data-ttu-id="b97c4-161">Eventos ETW dos provedores habilitados</span><span class="sxs-lookup"><span data-stu-id="b97c4-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="b97c4-162">Sistema operacional holográfico</span><span class="sxs-lookup"><span data-stu-id="b97c4-162">Holographic OS</span></span>

<span data-ttu-id="b97c4-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="b97c4-164">Retorna uma lista de provedores de ETW específicos do HoloLens que não estão registrados no sistema</span><span class="sxs-lookup"><span data-stu-id="b97c4-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="b97c4-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="b97c4-166">Retorna os Estados de todos os serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="b97c4-166">Returns the states of all services running.</span></span>

<span data-ttu-id="b97c4-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="b97c4-168">Obtém o IPD armazenado (distância interpupillary) em milímetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="b97c4-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="b97c4-170">Define o IPD</span><span class="sxs-lookup"><span data-stu-id="b97c4-170">Sets the IPD</span></span>

<span data-ttu-id="b97c4-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-171">Parameters</span></span>
* <span data-ttu-id="b97c4-172">IPD: novo valor de IPD a ser definido em milímetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="b97c4-173">**/API/Holographic/os/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="b97c4-174">Obter requisitos de HTTPS para o Device Portal</span><span class="sxs-lookup"><span data-stu-id="b97c4-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="b97c4-175">**/API/Holographic/os/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="b97c4-176">Define os requisitos de HTTPS para o portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="b97c4-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="b97c4-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-177">Parameters</span></span>
* <span data-ttu-id="b97c4-178">obrigatório: Sim, não ou padrão</span><span class="sxs-lookup"><span data-stu-id="b97c4-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="b97c4-179">Percepção de Holographic</span><span class="sxs-lookup"><span data-stu-id="b97c4-179">Holographic Perception</span></span>

<span data-ttu-id="b97c4-180">**/API/Holographic/Perception/Client (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="b97c4-181">Aceita atualizações do WebSocket e executa um cliente de percepção que envia atualizações a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="b97c4-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="b97c4-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-182">Parameters</span></span>
* <span data-ttu-id="b97c4-183">clientmode: "ativo" força o modo de controle visual quando ele não pode ser estabelecido passivamente</span><span class="sxs-lookup"><span data-stu-id="b97c4-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="b97c4-184">Holographic térmico</span><span class="sxs-lookup"><span data-stu-id="b97c4-184">Holographic Thermal</span></span>

<span data-ttu-id="b97c4-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="b97c4-186">Obter o estágio térmico do dispositivo (0 normal, 1 quente, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="b97c4-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="b97c4-187">Controle de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="b97c4-187">Perception Simulation Control</span></span>

<span data-ttu-id="b97c4-188">**/API/Holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="b97c4-189">Obter o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="b97c4-189">Get the simulation mode</span></span>

<span data-ttu-id="b97c4-190">**/API/Holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="b97c4-191">Definir o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="b97c4-191">Set the simulation mode</span></span>

<span data-ttu-id="b97c4-192">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-192">Parameters</span></span>
* <span data-ttu-id="b97c4-193">modo: modo de simulação: padrão, simulação, remoto, herdado</span><span class="sxs-lookup"><span data-stu-id="b97c4-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="b97c4-194">**/API/Holographic/Simulation/Control/Stream (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="b97c4-195">Excluir um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="b97c4-195">Delete a control stream.</span></span>

<span data-ttu-id="b97c4-196">**/API/Holographic/Simulation/Control/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="b97c4-197">Abra uma conexão de soquete da Web para um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="b97c4-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="b97c4-198">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="b97c4-199">Crie um fluxo de controle (prioridade necessária) ou poste dados em um fluxo criado (streamid necessário).</span><span class="sxs-lookup"><span data-stu-id="b97c4-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="b97c4-200">Espera-se que os dados postados sejam do tipo ' application/octet-stream '.</span><span class="sxs-lookup"><span data-stu-id="b97c4-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="b97c4-201">**/API/Holographic/Simulation/display/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="b97c4-202">Solicite um fluxo de vídeo de simulação contendo o conteúdo renderizado para a exibição do sistema quando estiver no modo ' Simulation '.</span><span class="sxs-lookup"><span data-stu-id="b97c4-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="b97c4-203">Um cabeçalho de descritor de formato simples será enviado inicialmente, seguido de texturas codificadas H. 264, cada um precedido por um cabeçalho que indica o índice de olho e o tamanho da textura.</span><span class="sxs-lookup"><span data-stu-id="b97c4-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="b97c4-204">Reprodução da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="b97c4-204">Perception Simulation Playback</span></span>

<span data-ttu-id="b97c4-205">**/API/Holographic/Simulation/playback/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="b97c4-206">Excluir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-206">Delete a recording.</span></span>

<span data-ttu-id="b97c4-207">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-207">Parameters</span></span>
* <span data-ttu-id="b97c4-208">gravação: o nome da gravação a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="b97c4-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="b97c4-209">**/API/Holographic/Simulation/playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="b97c4-210">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-210">Upload a recording.</span></span>

<span data-ttu-id="b97c4-211">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="b97c4-212">Obter todas as gravações.</span><span class="sxs-lookup"><span data-stu-id="b97c4-212">Get all recordings.</span></span>

<span data-ttu-id="b97c4-213">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="b97c4-214">Obter o estado de reprodução atual de uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="b97c4-215">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-215">Parameters</span></span>
* <span data-ttu-id="b97c4-216">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-216">recording : Name of recording.</span></span>

<span data-ttu-id="b97c4-217">**/API/Holographic/Simulation/playback/Session/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="b97c4-218">Descarregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-218">Unload a recording.</span></span>

<span data-ttu-id="b97c4-219">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-219">Parameters</span></span>
* <span data-ttu-id="b97c4-220">gravação: nome da gravação a ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="b97c4-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="b97c4-221">**/API/Holographic/Simulation/playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="b97c4-222">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-222">Load a recording.</span></span>

<span data-ttu-id="b97c4-223">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-223">Parameters</span></span>
* <span data-ttu-id="b97c4-224">gravação: o nome da gravação a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="b97c4-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="b97c4-225">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="b97c4-226">Obter todas as gravações carregadas.</span><span class="sxs-lookup"><span data-stu-id="b97c4-226">Get all loaded recordings.</span></span>

<span data-ttu-id="b97c4-227">**/API/Holographic/Simulation/playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="b97c4-228">Pausar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-228">Pause a recording.</span></span>

<span data-ttu-id="b97c4-229">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-229">Parameters</span></span>
* <span data-ttu-id="b97c4-230">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-230">recording : Name of recording.</span></span>

<span data-ttu-id="b97c4-231">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="b97c4-232">Reproduzir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-232">Play a recording.</span></span>

<span data-ttu-id="b97c4-233">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-233">Parameters</span></span>
* <span data-ttu-id="b97c4-234">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-234">recording : Name of recording.</span></span>

<span data-ttu-id="b97c4-235">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="b97c4-236">Parar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-236">Stop a recording.</span></span>

<span data-ttu-id="b97c4-237">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-237">Parameters</span></span>
* <span data-ttu-id="b97c4-238">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-238">recording : Name of recording.</span></span>

<span data-ttu-id="b97c4-239">**/API/Holographic/Simulation/playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="b97c4-240">Obter os tipos de dados em uma gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="b97c4-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="b97c4-241">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-241">Parameters</span></span>
* <span data-ttu-id="b97c4-242">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="b97c4-243">Gravação da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="b97c4-243">Perception Simulation Recording</span></span>

<span data-ttu-id="b97c4-244">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="b97c4-245">Inicie uma gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-245">Start a recording.</span></span> <span data-ttu-id="b97c4-246">Apenas uma única gravação pode estar ativa de uma vez.</span><span class="sxs-lookup"><span data-stu-id="b97c4-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="b97c4-247">É necessário definir um dos cabeçalhos, as mãos, spatialMapping ou ambiente.</span><span class="sxs-lookup"><span data-stu-id="b97c4-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="b97c4-248">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-248">Parameters</span></span>
* <span data-ttu-id="b97c4-249">Cabeçalho: Defina como 1 para registrar dados de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="b97c4-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="b97c4-250">Hands: Defina como 1 para gravar dados de mão.</span><span class="sxs-lookup"><span data-stu-id="b97c4-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="b97c4-251">spatialMapping: Defina como 1 para registrar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="b97c4-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="b97c4-252">ambiente: Defina como 1 para gravar dados do ambiente.</span><span class="sxs-lookup"><span data-stu-id="b97c4-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="b97c4-253">Nome: o nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-253">name : Name of the recording.</span></span>
* <span data-ttu-id="b97c4-254">singleSpatialMappingFrame: Defina como 1 para gravar apenas um único quadro de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="b97c4-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="b97c4-255">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="b97c4-256">Obter estado de gravação.</span><span class="sxs-lookup"><span data-stu-id="b97c4-256">Get recording state.</span></span>

<span data-ttu-id="b97c4-257">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="b97c4-258">Parar a gravação atual.</span><span class="sxs-lookup"><span data-stu-id="b97c4-258">Stop the current recording.</span></span> <span data-ttu-id="b97c4-259">A gravação será retornada como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="b97c4-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="b97c4-260">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="b97c4-260">Mixed Reality Capture</span></span>

<span data-ttu-id="b97c4-261">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="b97c4-262">Baixa um arquivo de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b97c4-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="b97c4-263">Use op = Stream Query parâmetro para streaming.</span><span class="sxs-lookup"><span data-stu-id="b97c4-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="b97c4-264">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-264">Parameters</span></span>
* <span data-ttu-id="b97c4-265">filename: nome, hex64 codificado, do arquivo de vídeo a ser obtido</span><span class="sxs-lookup"><span data-stu-id="b97c4-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="b97c4-266">op: fluxo</span><span class="sxs-lookup"><span data-stu-id="b97c4-266">op : stream</span></span>

<span data-ttu-id="b97c4-267">**/API/Holographic/MRC/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="b97c4-268">Exclui uma gravação de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b97c4-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="b97c4-269">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-269">Parameters</span></span>
* <span data-ttu-id="b97c4-270">filename: nome, hex64 codificado, do arquivo a ser excluído</span><span class="sxs-lookup"><span data-stu-id="b97c4-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="b97c4-271">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="b97c4-272">Retorna a lista de arquivos de realidade misturada armazenados no dispositivo</span><span class="sxs-lookup"><span data-stu-id="b97c4-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="b97c4-273">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="b97c4-274">Usa uma foto de realidade misturada e cria um arquivo no dispositivo</span><span class="sxs-lookup"><span data-stu-id="b97c4-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="b97c4-275">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-275">Parameters</span></span>
* <span data-ttu-id="b97c4-276">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="b97c4-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="b97c4-277">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="b97c4-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="b97c4-278">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="b97c4-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="b97c4-279">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="b97c4-280">Obtém as configurações padrão da captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="b97c4-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="b97c4-281">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="b97c4-282">Define as configurações padrão de captura de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="b97c4-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="b97c4-283">Algumas dessas configurações são aplicadas à captura de vídeo e foto da MRC do sistema.</span><span class="sxs-lookup"><span data-stu-id="b97c4-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="b97c4-284">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="b97c4-285">Obtém o status da realidade misturada registrada (em execução, parada)</span><span class="sxs-lookup"><span data-stu-id="b97c4-285">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="b97c4-286">**/API/Holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-286">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="b97c4-287">Obtém a imagem em miniatura do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="b97c4-287">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="b97c4-288">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-288">Parameters</span></span>
* <span data-ttu-id="b97c4-289">filename: nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada</span><span class="sxs-lookup"><span data-stu-id="b97c4-289">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="b97c4-290">**/API/Holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-290">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="b97c4-291">Inicia uma gravação de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="b97c4-291">Starts a mixed reality recording</span></span>

<span data-ttu-id="b97c4-292">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-292">Parameters</span></span>
* <span data-ttu-id="b97c4-293">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="b97c4-293">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="b97c4-294">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="b97c4-294">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="b97c4-295">MIC: capturar microfone: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="b97c4-295">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="b97c4-296">loopback: capturar o áudio do aplicativo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="b97c4-296">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="b97c4-297">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="b97c4-297">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="b97c4-298">Vstab: (somente HoloLens 2) habilitar estabilização de vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="b97c4-298">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="b97c4-299">vstabbuffer: (somente HoloLens 2) latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="b97c4-299">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="b97c4-300">**/API/Holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-300">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="b97c4-301">Interrompe a gravação atual da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="b97c4-301">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="b97c4-302">Streaming de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="b97c4-302">Mixed Reality Streaming</span></span>

<span data-ttu-id="b97c4-303">O HoloLens dá suporte à visualização dinâmica de realidade misturada por meio do download em partes de um MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="b97c4-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="b97c4-304">Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:</span><span class="sxs-lookup"><span data-stu-id="b97c4-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="b97c4-305">holo: capturar hologramas: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="b97c4-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="b97c4-306">PV: capturar câmera PV: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="b97c4-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="b97c4-307">MIC: capturar microfone: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="b97c4-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="b97c4-308">loopback: capturar áudio do aplicativo: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="b97c4-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="b97c4-309">Se nenhum deles for especificado: os hologramas, a câmera de foto/vídeo e o áudio do aplicativo serão capturados</span><span class="sxs-lookup"><span data-stu-id="b97c4-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="b97c4-310">Se houver algum especificado: os parâmetros não especificados serão padronizados como false</span><span class="sxs-lookup"><span data-stu-id="b97c4-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="b97c4-311">Parâmetros opcionais (somente HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="b97c4-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="b97c4-312">RenderFromCamera: Render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="b97c4-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="b97c4-313">Vstab: habilitar estabilização de vídeo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="b97c4-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="b97c4-314">vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="b97c4-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="b97c4-315">**/API/Holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="b97c4-316">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="b97c4-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="b97c4-317">**/API/Holographic/Stream/live_high. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="b97c4-318">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="b97c4-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="b97c4-319">**/API/Holographic/Stream/live_med. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="b97c4-320">Um fluxo 854x480p 30fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="b97c4-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="b97c4-321">**/API/Holographic/Stream/live_low. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="b97c4-322">Um fluxo 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="b97c4-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="b97c4-323">Rede</span><span class="sxs-lookup"><span data-stu-id="b97c4-323">Networking</span></span>

<span data-ttu-id="b97c4-324">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="b97c4-325">Obter a configuração de IP atual</span><span class="sxs-lookup"><span data-stu-id="b97c4-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="b97c4-326">Informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="b97c4-326">OS Information</span></span>

<span data-ttu-id="b97c4-327">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="b97c4-328">Obtém informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="b97c4-328">Gets operating system information</span></span>

<span data-ttu-id="b97c4-329">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="b97c4-330">Obtém o nome do computador</span><span class="sxs-lookup"><span data-stu-id="b97c4-330">Gets the machine name</span></span>

<span data-ttu-id="b97c4-331">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="b97c4-332">Define o nome do computador</span><span class="sxs-lookup"><span data-stu-id="b97c4-332">Sets the machine name</span></span>

<span data-ttu-id="b97c4-333">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-333">Parameters</span></span>
* <span data-ttu-id="b97c4-334">Nome: novo nome do computador, hex64 codificado, para definir como</span><span class="sxs-lookup"><span data-stu-id="b97c4-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="b97c4-335">Dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="b97c4-335">Performance data</span></span>

<span data-ttu-id="b97c4-336">**/API/ResourceManager/Processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="b97c4-337">Retorna a lista de processos em execução com detalhes</span><span class="sxs-lookup"><span data-stu-id="b97c4-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="b97c4-338">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-338">Return data</span></span>
* <span data-ttu-id="b97c4-339">JSON com lista de processos e detalhes para cada processo</span><span class="sxs-lookup"><span data-stu-id="b97c4-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="b97c4-340">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="b97c4-341">Retorna estatísticas de desempenho do sistema (leitura/gravação de e/s, estatísticas de memória etc.)</span><span class="sxs-lookup"><span data-stu-id="b97c4-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="b97c4-342">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-342">Return data</span></span>
* <span data-ttu-id="b97c4-343">JSON com informações do sistema: CPU, GPU, memória, rede, e/s</span><span class="sxs-lookup"><span data-stu-id="b97c4-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="b97c4-344">Energia</span><span class="sxs-lookup"><span data-stu-id="b97c4-344">Power</span></span>

<span data-ttu-id="b97c4-345">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="b97c4-346">Obtém o estado da bateria atual</span><span class="sxs-lookup"><span data-stu-id="b97c4-346">Gets the current battery state</span></span>

<span data-ttu-id="b97c4-347">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="b97c4-348">Verifica se o sistema está em um estado de baixa energia</span><span class="sxs-lookup"><span data-stu-id="b97c4-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="b97c4-349">Controle remoto</span><span class="sxs-lookup"><span data-stu-id="b97c4-349">Remote Control</span></span>

<span data-ttu-id="b97c4-350">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="b97c4-351">Reinicia o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="b97c4-351">Restarts the target device</span></span>

<span data-ttu-id="b97c4-352">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="b97c4-353">Desliga o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="b97c4-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="b97c4-354">Gerenciador de Tarefas</span><span class="sxs-lookup"><span data-stu-id="b97c4-354">Task Manager</span></span>

<span data-ttu-id="b97c4-355">**/API/taskmanager/app (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="b97c4-356">Para um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="b97c4-356">Stops a modern app</span></span>

<span data-ttu-id="b97c4-357">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-357">Parameters</span></span>
* <span data-ttu-id="b97c4-358">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="b97c4-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="b97c4-359">forcestop: forçar a interrupção de todos os processos (= Sim)</span><span class="sxs-lookup"><span data-stu-id="b97c4-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="b97c4-360">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="b97c4-361">Inicia um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="b97c4-361">Starts a modern app</span></span>

<span data-ttu-id="b97c4-362">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-362">Parameters</span></span>
* <span data-ttu-id="b97c4-363">AppID: PRAID do aplicativo a ser iniciado, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="b97c4-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="b97c4-364">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="b97c4-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="b97c4-365">Gerenciamento de WiFi</span><span class="sxs-lookup"><span data-stu-id="b97c4-365">WiFi Management</span></span>

<span data-ttu-id="b97c4-366">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="b97c4-367">Enumera interfaces de rede sem fio</span><span class="sxs-lookup"><span data-stu-id="b97c4-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="b97c4-368">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-368">Return data</span></span>
* <span data-ttu-id="b97c4-369">Lista de interfaces sem fio com detalhes (GUID, descrição, etc.)</span><span class="sxs-lookup"><span data-stu-id="b97c4-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="b97c4-370">**/API/WiFi/Network (excluir)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="b97c4-371">Exclui um perfil associado a uma rede em uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="b97c4-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="b97c4-372">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-372">Parameters</span></span>
* <span data-ttu-id="b97c4-373">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="b97c4-373">interface : network interface guid</span></span>
* <span data-ttu-id="b97c4-374">Perfil: nome do perfil</span><span class="sxs-lookup"><span data-stu-id="b97c4-374">profile : profile name</span></span>

<span data-ttu-id="b97c4-375">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="b97c4-376">Enumera redes sem fio na interface de rede especificada</span><span class="sxs-lookup"><span data-stu-id="b97c4-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="b97c4-377">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-377">Parameters</span></span>
* <span data-ttu-id="b97c4-378">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="b97c4-378">interface : network interface guid</span></span>

<span data-ttu-id="b97c4-379">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-379">Return data</span></span>
* <span data-ttu-id="b97c4-380">Lista de redes sem fio encontradas na interface de rede com detalhes</span><span class="sxs-lookup"><span data-stu-id="b97c4-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="b97c4-381">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="b97c4-382">Conecta ou desconecta-se a uma rede na interface especificada</span><span class="sxs-lookup"><span data-stu-id="b97c4-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="b97c4-383">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-383">Parameters</span></span>
* <span data-ttu-id="b97c4-384">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="b97c4-384">interface : network interface guid</span></span>
* <span data-ttu-id="b97c4-385">SSID: SSID, hex64 codificado, para se conectar ao</span><span class="sxs-lookup"><span data-stu-id="b97c4-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="b97c4-386">op: conectar ou desconectar</span><span class="sxs-lookup"><span data-stu-id="b97c4-386">op : connect or disconnect</span></span>
* <span data-ttu-id="b97c4-387">CreateProfile: Sim ou não</span><span class="sxs-lookup"><span data-stu-id="b97c4-387">createprofile : yes or no</span></span>
* <span data-ttu-id="b97c4-388">chave: chave compartilhada, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="b97c4-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="b97c4-389">Gravador de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="b97c4-389">Windows Performance Recorder</span></span>

<span data-ttu-id="b97c4-390">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="b97c4-391">Carrega um perfil WPR e inicia o rastreamento usando o perfil carregado.</span><span class="sxs-lookup"><span data-stu-id="b97c4-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="b97c4-392">Carga útil</span><span class="sxs-lookup"><span data-stu-id="b97c4-392">Payload</span></span>
* <span data-ttu-id="b97c4-393">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="b97c4-393">multi-part conforming http body</span></span>

<span data-ttu-id="b97c4-394">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-394">Return data</span></span>
* <span data-ttu-id="b97c4-395">Retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="b97c4-395">Returns the WPR session status.</span></span>

<span data-ttu-id="b97c4-396">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="b97c4-397">Recupera o status da sessão WPR</span><span class="sxs-lookup"><span data-stu-id="b97c4-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="b97c4-398">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-398">Return data</span></span>
* <span data-ttu-id="b97c4-399">Status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="b97c4-399">WPR session status.</span></span>

<span data-ttu-id="b97c4-400">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="b97c4-401">Interrompe uma sessão de rastreamento de WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="b97c4-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="b97c4-402">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-402">Return data</span></span>
* <span data-ttu-id="b97c4-403">Retorna o arquivo ETL de rastreamento</span><span class="sxs-lookup"><span data-stu-id="b97c4-403">Returns the trace ETL file</span></span>

<span data-ttu-id="b97c4-404">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="b97c4-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="b97c4-405">Inicia uma sessão de rastreamento WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="b97c4-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="b97c4-406">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97c4-406">Parameters</span></span>
* <span data-ttu-id="b97c4-407">Perfil: nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="b97c4-407">profile : Profile name.</span></span> <span data-ttu-id="b97c4-408">Os perfis disponíveis são armazenados em perfprofiles/Profiles. JSON</span><span class="sxs-lookup"><span data-stu-id="b97c4-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="b97c4-409">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="b97c4-409">Return data</span></span>
* <span data-ttu-id="b97c4-410">Em Iniciar, retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="b97c4-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="b97c4-411">Veja também</span><span class="sxs-lookup"><span data-stu-id="b97c4-411">See also</span></span>
* [<span data-ttu-id="b97c4-412">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="b97c4-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="b97c4-413">Referência da API principal do portal do dispositivo (UWP)</span><span class="sxs-lookup"><span data-stu-id="b97c4-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

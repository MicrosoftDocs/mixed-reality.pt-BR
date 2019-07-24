---
title: Referência da API do portal do dispositivo
description: Referência de API para o portal de dispositivo do Windows no HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portal de dispositivos Windows, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694422"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="2c601-104">Referência da API do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="2c601-104">Device portal API reference</span></span>

<span data-ttu-id="2c601-105">Tudo no [portal de dispositivos do Windows](using-the-windows-device-portal.md) é criado sobre as APIs REST que você pode usar para acessar os dados e controlar seu dispositivo de forma programática.</span><span class="sxs-lookup"><span data-stu-id="2c601-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="2c601-106">Implantação do aplicativo</span><span class="sxs-lookup"><span data-stu-id="2c601-106">App deloyment</span></span>

<span data-ttu-id="2c601-107">**/API/app/PackageManager/Package (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="2c601-108">Desinstala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="2c601-108">Uninstalls an app</span></span>

<span data-ttu-id="2c601-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-109">Parameters</span></span>
* <span data-ttu-id="2c601-110">agrupa Nome do arquivo do pacote a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="2c601-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="2c601-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="2c601-112">Instala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="2c601-112">Installs an App</span></span>

<span data-ttu-id="2c601-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-113">Parameters</span></span>
* <span data-ttu-id="2c601-114">agrupa Nome do arquivo do pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="2c601-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="2c601-115">Carga</span><span class="sxs-lookup"><span data-stu-id="2c601-115">Payload</span></span>
* <span data-ttu-id="2c601-116">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="2c601-116">multi-part conforming http body</span></span>

<span data-ttu-id="2c601-117">**/API/app/PackageManager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="2c601-118">Recupera a lista de aplicativos instalados no sistema, com detalhes</span><span class="sxs-lookup"><span data-stu-id="2c601-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="2c601-119">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-119">Return data</span></span>
* <span data-ttu-id="2c601-120">Lista de pacotes instalados com detalhes</span><span class="sxs-lookup"><span data-stu-id="2c601-120">List of installed packages with details</span></span>

<span data-ttu-id="2c601-121">**/API/app/PackageManager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="2c601-122">Obtém o status da instalação do aplicativo em andamento</span><span class="sxs-lookup"><span data-stu-id="2c601-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="2c601-123">Coleta de despejo</span><span class="sxs-lookup"><span data-stu-id="2c601-123">Dump collection</span></span>

<span data-ttu-id="2c601-124">**/API/Debug/dump/UserMode/crashcontrol (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="2c601-125">Desabilita a coleta de despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="2c601-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="2c601-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-126">Parameters</span></span>
* <span data-ttu-id="2c601-127">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="2c601-127">packageFullname : package name</span></span>

<span data-ttu-id="2c601-128">**/API/Debug/dump/UserMode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="2c601-129">Obtém as configurações para coleta de despejo de memória de aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="2c601-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="2c601-130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-130">Parameters</span></span>
* <span data-ttu-id="2c601-131">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="2c601-131">packageFullname : package name</span></span>

<span data-ttu-id="2c601-132">**/API/Debug/dump/UserMode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="2c601-133">Habilita e define as configurações de controle de despejo para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="2c601-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="2c601-134">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-134">Parameters</span></span>
* <span data-ttu-id="2c601-135">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="2c601-135">packageFullname : package name</span></span>

<span data-ttu-id="2c601-136">**/API/Debug/dump/UserMode/crashdump (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="2c601-137">Exclui um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="2c601-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="2c601-138">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-138">Parameters</span></span>
* <span data-ttu-id="2c601-139">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="2c601-139">packageFullname : package name</span></span>
* <span data-ttu-id="2c601-140">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="2c601-140">fileName : dump file name</span></span>

<span data-ttu-id="2c601-141">**/API/Debug/dump/UserMode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="2c601-142">Recupera um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="2c601-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="2c601-143">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-143">Parameters</span></span>
* <span data-ttu-id="2c601-144">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="2c601-144">packageFullname : package name</span></span>
* <span data-ttu-id="2c601-145">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="2c601-145">fileName : dump file name</span></span>

<span data-ttu-id="2c601-146">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-146">Return data</span></span>
* <span data-ttu-id="2c601-147">Arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="2c601-147">Dump file.</span></span> <span data-ttu-id="2c601-148">Inspecione com o WinDbg ou o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2c601-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="2c601-149">**/API/Debug/dump/UserMode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="2c601-150">Retorna a lista de todos os despejos de memória para aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="2c601-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="2c601-151">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-151">Return data</span></span>
* <span data-ttu-id="2c601-152">Lista de despejos de memória por aplicativo carregado por lado</span><span class="sxs-lookup"><span data-stu-id="2c601-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="2c601-153">ETW</span><span class="sxs-lookup"><span data-stu-id="2c601-153">ETW</span></span>

<span data-ttu-id="2c601-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="2c601-155">Enumera provedores registrados</span><span class="sxs-lookup"><span data-stu-id="2c601-155">Enumerates registered providers</span></span>

<span data-ttu-id="2c601-156">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-156">Return data</span></span>
* <span data-ttu-id="2c601-157">Lista de provedores, nome amigável e GUID</span><span class="sxs-lookup"><span data-stu-id="2c601-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="2c601-158">**/API/ETW/Session/Realtime (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2c601-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="2c601-159">Cria uma sessão de ETW em tempo real; gerenciado em um WebSocket.</span><span class="sxs-lookup"><span data-stu-id="2c601-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="2c601-160">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-160">Return data</span></span>
* <span data-ttu-id="2c601-161">Eventos ETW dos provedores habilitados</span><span class="sxs-lookup"><span data-stu-id="2c601-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="2c601-162">Sistema operacional holográfico</span><span class="sxs-lookup"><span data-stu-id="2c601-162">Holographic OS</span></span>

<span data-ttu-id="2c601-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="2c601-164">Retorna uma lista de provedores de ETW específicos do HoloLens que não estão registrados no sistema</span><span class="sxs-lookup"><span data-stu-id="2c601-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="2c601-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="2c601-166">Retorna os Estados de todos os serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="2c601-166">Returns the states of all services running.</span></span>

<span data-ttu-id="2c601-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="2c601-168">Obtém o IPD armazenado (distância interpupillary) em milímetros</span><span class="sxs-lookup"><span data-stu-id="2c601-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="2c601-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="2c601-170">Define o IPD</span><span class="sxs-lookup"><span data-stu-id="2c601-170">Sets the IPD</span></span>

<span data-ttu-id="2c601-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-171">Parameters</span></span>
* <span data-ttu-id="2c601-172">IPD Novo valor de IPD a ser definido em milímetros</span><span class="sxs-lookup"><span data-stu-id="2c601-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="2c601-173">**/API/Holographic/os/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="2c601-174">Obter requisitos de HTTPS para o Device Portal</span><span class="sxs-lookup"><span data-stu-id="2c601-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="2c601-175">**/API/Holographic/os/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="2c601-176">Define os requisitos de HTTPS para o portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="2c601-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="2c601-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-177">Parameters</span></span>
* <span data-ttu-id="2c601-178">obrigatório: Sim, não ou padrão</span><span class="sxs-lookup"><span data-stu-id="2c601-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="2c601-179">Percepção de Holographic</span><span class="sxs-lookup"><span data-stu-id="2c601-179">Holographic Perception</span></span>

<span data-ttu-id="2c601-180">**/API/Holographic/Perception/Client (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2c601-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="2c601-181">Aceita atualizações do WebSocket e executa um cliente de percepção que envia atualizações a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="2c601-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="2c601-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-182">Parameters</span></span>
* <span data-ttu-id="2c601-183">clientmode: "ativo" força o modo de controle visual quando ele não pode ser estabelecido passivamente</span><span class="sxs-lookup"><span data-stu-id="2c601-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="2c601-184">Holographic térmico</span><span class="sxs-lookup"><span data-stu-id="2c601-184">Holographic Thermal</span></span>

<span data-ttu-id="2c601-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="2c601-186">Obter o estágio térmico do dispositivo (0 normal, 1 quente, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="2c601-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="2c601-187">Controle de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="2c601-187">Perception Simulation Control</span></span>

<span data-ttu-id="2c601-188">**/API/Holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="2c601-189">Obter o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="2c601-189">Get the simulation mode</span></span>

<span data-ttu-id="2c601-190">**/API/Holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="2c601-191">Definir o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="2c601-191">Set the simulation mode</span></span>

<span data-ttu-id="2c601-192">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-192">Parameters</span></span>
* <span data-ttu-id="2c601-193">modo: modo de simulação: padrão, simulação, remoto, herdado</span><span class="sxs-lookup"><span data-stu-id="2c601-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="2c601-194">**/API/Holographic/Simulation/Control/Stream (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="2c601-195">Excluir um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="2c601-195">Delete a control stream.</span></span>

<span data-ttu-id="2c601-196">**/API/Holographic/Simulation/Control/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2c601-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="2c601-197">Abra uma conexão de soquete da Web para um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="2c601-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="2c601-198">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="2c601-199">Crie um fluxo de controle (prioridade necessária) ou poste dados em um fluxo criado (streamid necessário).</span><span class="sxs-lookup"><span data-stu-id="2c601-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="2c601-200">Espera-se que os dados postados sejam do tipo ' application/octet-stream '.</span><span class="sxs-lookup"><span data-stu-id="2c601-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="2c601-201">Reprodução da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="2c601-201">Perception Simulation Playback</span></span>

<span data-ttu-id="2c601-202">**/API/Holographic/Simulation/playback/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="2c601-203">Excluir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-203">Delete a recording.</span></span>

<span data-ttu-id="2c601-204">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-204">Parameters</span></span>
* <span data-ttu-id="2c601-205">registra Nome da gravação a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="2c601-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="2c601-206">**/API/Holographic/Simulation/playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="2c601-207">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-207">Upload a recording.</span></span>

<span data-ttu-id="2c601-208">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="2c601-209">Obter todas as gravações.</span><span class="sxs-lookup"><span data-stu-id="2c601-209">Get all recordings.</span></span>

<span data-ttu-id="2c601-210">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="2c601-211">Obter o estado de reprodução atual de uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="2c601-212">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-212">Parameters</span></span>
* <span data-ttu-id="2c601-213">registra Nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-213">recording : Name of recording.</span></span>

<span data-ttu-id="2c601-214">**/API/Holographic/Simulation/playback/Session/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="2c601-215">Descarregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-215">Unload a recording.</span></span>

<span data-ttu-id="2c601-216">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-216">Parameters</span></span>
* <span data-ttu-id="2c601-217">registra Nome da gravação a ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="2c601-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="2c601-218">**/API/Holographic/Simulation/playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="2c601-219">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-219">Load a recording.</span></span>

<span data-ttu-id="2c601-220">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-220">Parameters</span></span>
* <span data-ttu-id="2c601-221">registra Nome da gravação a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="2c601-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="2c601-222">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="2c601-223">Obter todas as gravações carregadas.</span><span class="sxs-lookup"><span data-stu-id="2c601-223">Get all loaded recordings.</span></span>

<span data-ttu-id="2c601-224">**/API/Holographic/Simulation/playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="2c601-225">Pausar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-225">Pause a recording.</span></span>

<span data-ttu-id="2c601-226">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-226">Parameters</span></span>
* <span data-ttu-id="2c601-227">registra Nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-227">recording : Name of recording.</span></span>

<span data-ttu-id="2c601-228">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="2c601-229">Reproduzir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-229">Play a recording.</span></span>

<span data-ttu-id="2c601-230">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-230">Parameters</span></span>
* <span data-ttu-id="2c601-231">registra Nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-231">recording : Name of recording.</span></span>

<span data-ttu-id="2c601-232">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="2c601-233">Parar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-233">Stop a recording.</span></span>

<span data-ttu-id="2c601-234">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-234">Parameters</span></span>
* <span data-ttu-id="2c601-235">registra Nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-235">recording : Name of recording.</span></span>

<span data-ttu-id="2c601-236">**/API/Holographic/Simulation/playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="2c601-237">Obter os tipos de dados em uma gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="2c601-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="2c601-238">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-238">Parameters</span></span>
* <span data-ttu-id="2c601-239">registra Nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="2c601-240">Gravação da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="2c601-240">Perception Simulation Recording</span></span>

<span data-ttu-id="2c601-241">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="2c601-242">Inicie uma gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-242">Start a recording.</span></span> <span data-ttu-id="2c601-243">Apenas uma única gravação pode estar ativa de uma vez.</span><span class="sxs-lookup"><span data-stu-id="2c601-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="2c601-244">É necessário definir um dos cabeçalhos, as mãos, spatialMapping ou ambiente.</span><span class="sxs-lookup"><span data-stu-id="2c601-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="2c601-245">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-245">Parameters</span></span>
* <span data-ttu-id="2c601-246">principal Defina como 1 para registrar dados de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="2c601-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="2c601-247">participação Defina como 1 para gravar dados de mão.</span><span class="sxs-lookup"><span data-stu-id="2c601-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="2c601-248">spatialMapping : Defina como 1 para registrar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2c601-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="2c601-249">ambiente Defina como 1 para registrar os dados do ambiente.</span><span class="sxs-lookup"><span data-stu-id="2c601-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="2c601-250">nomes Nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-250">name : Name of the recording.</span></span>
* <span data-ttu-id="2c601-251">singleSpatialMappingFrame : Defina como 1 para gravar apenas um único quadro de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2c601-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="2c601-252">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="2c601-253">Obter estado de gravação.</span><span class="sxs-lookup"><span data-stu-id="2c601-253">Get recording state.</span></span>

<span data-ttu-id="2c601-254">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="2c601-255">Parar a gravação atual.</span><span class="sxs-lookup"><span data-stu-id="2c601-255">Stop the current recording.</span></span> <span data-ttu-id="2c601-256">A gravação será retornada como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2c601-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="2c601-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="2c601-257">Mixed Reality Capture</span></span>

<span data-ttu-id="2c601-258">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="2c601-259">Baixa um arquivo de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2c601-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="2c601-260">Use op = Stream Query parâmetro para streaming.</span><span class="sxs-lookup"><span data-stu-id="2c601-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="2c601-261">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-261">Parameters</span></span>
* <span data-ttu-id="2c601-262">nome do arquivo: Nome, hex64 codificado, do arquivo de vídeo a ser obtido</span><span class="sxs-lookup"><span data-stu-id="2c601-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="2c601-263">op: fluxo</span><span class="sxs-lookup"><span data-stu-id="2c601-263">op : stream</span></span>

<span data-ttu-id="2c601-264">**/API/Holographic/MRC/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="2c601-265">Exclui uma gravação de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2c601-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="2c601-266">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-266">Parameters</span></span>
* <span data-ttu-id="2c601-267">nome do arquivo: Nome, hex64 codificado, do arquivo a ser excluído</span><span class="sxs-lookup"><span data-stu-id="2c601-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="2c601-268">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="2c601-269">Retorna a lista de arquivos de realidade misturada armazenados no dispositivo</span><span class="sxs-lookup"><span data-stu-id="2c601-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="2c601-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="2c601-271">Usa uma foto de realidade misturada e cria um arquivo no dispositivo</span><span class="sxs-lookup"><span data-stu-id="2c601-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="2c601-272">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-272">Parameters</span></span>
* <span data-ttu-id="2c601-273">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="2c601-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="2c601-274">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="2c601-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="2c601-275">RenderFromCamera : (Somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="2c601-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="2c601-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="2c601-277">Obtém as configurações padrão da captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="2c601-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="2c601-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="2c601-279">Define as configurações padrão de captura de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2c601-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="2c601-280">Algumas dessas configurações são aplicadas à captura de vídeo e foto da MRC do sistema.</span><span class="sxs-lookup"><span data-stu-id="2c601-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="2c601-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="2c601-282">Obtém o status da realidade misturada registrada (em execução, parada)</span><span class="sxs-lookup"><span data-stu-id="2c601-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="2c601-283">**/API/Holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="2c601-284">Obtém a imagem em miniatura do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="2c601-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="2c601-285">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-285">Parameters</span></span>
* <span data-ttu-id="2c601-286">nome do arquivo: Nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada</span><span class="sxs-lookup"><span data-stu-id="2c601-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="2c601-287">**/API/Holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="2c601-288">Inicia uma gravação de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="2c601-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="2c601-289">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-289">Parameters</span></span>
* <span data-ttu-id="2c601-290">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="2c601-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="2c601-291">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="2c601-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="2c601-292">MIC: capturar microfone: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="2c601-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="2c601-293">loopback: capturar o áudio do aplicativo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="2c601-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="2c601-294">RenderFromCamera : (Somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="2c601-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="2c601-295">vstab : (Somente HoloLens 2) habilitar estabilização de vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="2c601-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="2c601-296">vstabbuffer: (Somente HoloLens 2) latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="2c601-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="2c601-297">**/API/Holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="2c601-298">Interrompe a gravação atual da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="2c601-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="2c601-299">Streaming de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="2c601-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="2c601-300">O HoloLens dá suporte à visualização dinâmica de realidade misturada por meio do download em partes de um MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="2c601-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="2c601-301">Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:</span><span class="sxs-lookup"><span data-stu-id="2c601-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="2c601-302">holo: capturar hologramas: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="2c601-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2c601-303">PV: capturar câmera PV: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="2c601-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="2c601-304">MIC: capturar microfone: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="2c601-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="2c601-305">loopback: capturar áudio do aplicativo: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="2c601-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="2c601-306">Se nenhum deles for especificado: os hologramas, a câmera de foto/vídeo e o áudio do aplicativo serão capturados</span><span class="sxs-lookup"><span data-stu-id="2c601-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="2c601-307">Se houver algum especificado: os parâmetros não especificados serão padronizados como false</span><span class="sxs-lookup"><span data-stu-id="2c601-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="2c601-308">Parâmetros opcionais (somente HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="2c601-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="2c601-309">RenderFromCamera: Render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="2c601-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="2c601-310">Vstab: habilitar estabilização de vídeo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="2c601-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="2c601-311">vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="2c601-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="2c601-312">**/API/Holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="2c601-313">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="2c601-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="2c601-314">**/API/Holographic/Stream/live_high.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="2c601-315">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="2c601-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="2c601-316">**/API/Holographic/Stream/live_med.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="2c601-317">Um fluxo 854x480p 30fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="2c601-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="2c601-318">**/API/Holographic/Stream/live_low.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="2c601-319">Um fluxo 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="2c601-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="2c601-320">Rede</span><span class="sxs-lookup"><span data-stu-id="2c601-320">Networking</span></span>

<span data-ttu-id="2c601-321">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="2c601-322">Obter a configuração de IP atual</span><span class="sxs-lookup"><span data-stu-id="2c601-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="2c601-323">Informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="2c601-323">OS Information</span></span>

<span data-ttu-id="2c601-324">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="2c601-325">Obtém informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="2c601-325">Gets operating system information</span></span>

<span data-ttu-id="2c601-326">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="2c601-327">Obtém o nome do computador</span><span class="sxs-lookup"><span data-stu-id="2c601-327">Gets the machine name</span></span>

<span data-ttu-id="2c601-328">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="2c601-329">Define o nome do computador</span><span class="sxs-lookup"><span data-stu-id="2c601-329">Sets the machine name</span></span>

<span data-ttu-id="2c601-330">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-330">Parameters</span></span>
* <span data-ttu-id="2c601-331">nomes Novo nome do computador, hex64 codificado, para definir como</span><span class="sxs-lookup"><span data-stu-id="2c601-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="2c601-332">Dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="2c601-332">Performance data</span></span>

<span data-ttu-id="2c601-333">**/API/ResourceManager/Processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="2c601-334">Retorna a lista de processos em execução com detalhes</span><span class="sxs-lookup"><span data-stu-id="2c601-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="2c601-335">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-335">Return data</span></span>
* <span data-ttu-id="2c601-336">JSON com lista de processos e detalhes para cada processo</span><span class="sxs-lookup"><span data-stu-id="2c601-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="2c601-337">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="2c601-338">Retorna estatísticas de desempenho do sistema (leitura/gravação de e/s, estatísticas de memória etc.)</span><span class="sxs-lookup"><span data-stu-id="2c601-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="2c601-339">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-339">Return data</span></span>
* <span data-ttu-id="2c601-340">JSON com informações do sistema: CPU, GPU, memória, rede, e/s</span><span class="sxs-lookup"><span data-stu-id="2c601-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="2c601-341">Potência</span><span class="sxs-lookup"><span data-stu-id="2c601-341">Power</span></span>

<span data-ttu-id="2c601-342">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="2c601-343">Obtém o estado da bateria atual</span><span class="sxs-lookup"><span data-stu-id="2c601-343">Gets the current battery state</span></span>

<span data-ttu-id="2c601-344">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="2c601-345">Verifica se o sistema está em um estado de baixa energia</span><span class="sxs-lookup"><span data-stu-id="2c601-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="2c601-346">Controle Remoto</span><span class="sxs-lookup"><span data-stu-id="2c601-346">Remote Control</span></span>

<span data-ttu-id="2c601-347">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="2c601-348">Reinicia o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="2c601-348">Restarts the target device</span></span>

<span data-ttu-id="2c601-349">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="2c601-350">Desliga o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="2c601-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="2c601-351">Gerenciador de Tarefas</span><span class="sxs-lookup"><span data-stu-id="2c601-351">Task Manager</span></span>

<span data-ttu-id="2c601-352">**/API/taskmanager/app (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="2c601-353">Para um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="2c601-353">Stops a modern app</span></span>

<span data-ttu-id="2c601-354">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-354">Parameters</span></span>
* <span data-ttu-id="2c601-355">agrupa Nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="2c601-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="2c601-356">forcestop : Forçar a interrupção de todos os processos (= Sim)</span><span class="sxs-lookup"><span data-stu-id="2c601-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="2c601-357">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="2c601-358">Inicia um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="2c601-358">Starts a modern app</span></span>

<span data-ttu-id="2c601-359">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-359">Parameters</span></span>
* <span data-ttu-id="2c601-360">AppID PRAID do aplicativo para iniciar, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="2c601-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="2c601-361">agrupa Nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="2c601-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="2c601-362">Gerenciamento de WiFi</span><span class="sxs-lookup"><span data-stu-id="2c601-362">WiFi Management</span></span>

<span data-ttu-id="2c601-363">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="2c601-364">Enumera interfaces de rede sem fio</span><span class="sxs-lookup"><span data-stu-id="2c601-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="2c601-365">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-365">Return data</span></span>
* <span data-ttu-id="2c601-366">Lista de interfaces sem fio com detalhes (GUID, descrição, etc.)</span><span class="sxs-lookup"><span data-stu-id="2c601-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="2c601-367">**/API/WiFi/Network (excluir)**</span><span class="sxs-lookup"><span data-stu-id="2c601-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="2c601-368">Exclui um perfil associado a uma rede em uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="2c601-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="2c601-369">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-369">Parameters</span></span>
* <span data-ttu-id="2c601-370">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="2c601-370">interface : network interface guid</span></span>
* <span data-ttu-id="2c601-371">Perfil: nome do perfil</span><span class="sxs-lookup"><span data-stu-id="2c601-371">profile : profile name</span></span>

<span data-ttu-id="2c601-372">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="2c601-373">Enumera redes sem fio na interface de rede especificada</span><span class="sxs-lookup"><span data-stu-id="2c601-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="2c601-374">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-374">Parameters</span></span>
* <span data-ttu-id="2c601-375">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="2c601-375">interface : network interface guid</span></span>

<span data-ttu-id="2c601-376">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-376">Return data</span></span>
* <span data-ttu-id="2c601-377">Lista de redes sem fio encontradas na interface de rede com detalhes</span><span class="sxs-lookup"><span data-stu-id="2c601-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="2c601-378">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="2c601-379">Conecta ou desconecta-se a uma rede na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2c601-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="2c601-380">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-380">Parameters</span></span>
* <span data-ttu-id="2c601-381">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="2c601-381">interface : network interface guid</span></span>
* <span data-ttu-id="2c601-382">SSID: SSID, hex64 codificado, para se conectar ao</span><span class="sxs-lookup"><span data-stu-id="2c601-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="2c601-383">op: conectar ou desconectar</span><span class="sxs-lookup"><span data-stu-id="2c601-383">op : connect or disconnect</span></span>
* <span data-ttu-id="2c601-384">CreateProfile: Sim ou não</span><span class="sxs-lookup"><span data-stu-id="2c601-384">createprofile : yes or no</span></span>
* <span data-ttu-id="2c601-385">chave: chave compartilhada, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="2c601-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="2c601-386">Gravador de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="2c601-386">Windows Performance Recorder</span></span>

<span data-ttu-id="2c601-387">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="2c601-388">Carrega um perfil WPR e inicia o rastreamento usando o perfil carregado.</span><span class="sxs-lookup"><span data-stu-id="2c601-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="2c601-389">Carga</span><span class="sxs-lookup"><span data-stu-id="2c601-389">Payload</span></span>
* <span data-ttu-id="2c601-390">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="2c601-390">multi-part conforming http body</span></span>

<span data-ttu-id="2c601-391">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-391">Return data</span></span>
* <span data-ttu-id="2c601-392">Retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="2c601-392">Returns the WPR session status.</span></span>

<span data-ttu-id="2c601-393">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="2c601-394">Recupera o status da sessão WPR</span><span class="sxs-lookup"><span data-stu-id="2c601-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="2c601-395">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-395">Return data</span></span>
* <span data-ttu-id="2c601-396">Status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="2c601-396">WPR session status.</span></span>

<span data-ttu-id="2c601-397">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="2c601-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="2c601-398">Interrompe uma sessão de rastreamento de WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="2c601-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="2c601-399">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-399">Return data</span></span>
* <span data-ttu-id="2c601-400">Retorna o arquivo ETL de rastreamento</span><span class="sxs-lookup"><span data-stu-id="2c601-400">Returns the trace ETL file</span></span>

<span data-ttu-id="2c601-401">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="2c601-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="2c601-402">Inicia uma sessão de rastreamento WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="2c601-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="2c601-403">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c601-403">Parameters</span></span>
* <span data-ttu-id="2c601-404">criar Nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="2c601-404">profile : Profile name.</span></span> <span data-ttu-id="2c601-405">Os perfis disponíveis são armazenados em perfprofiles/Profiles. JSON</span><span class="sxs-lookup"><span data-stu-id="2c601-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="2c601-406">Dados de retorno</span><span class="sxs-lookup"><span data-stu-id="2c601-406">Return data</span></span>
* <span data-ttu-id="2c601-407">Em Iniciar, retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="2c601-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c601-408">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c601-408">See also</span></span>
* [<span data-ttu-id="2c601-409">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="2c601-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="2c601-410">Referência da API principal do portal do dispositivo (UWP)</span><span class="sxs-lookup"><span data-stu-id="2c601-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

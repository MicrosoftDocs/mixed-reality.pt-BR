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
# <a name="device-portal-api-reference"></a><span data-ttu-id="c13da-104">Referência da API do portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="c13da-104">Device portal API reference</span></span>

<span data-ttu-id="c13da-105">Tudo no [portal de dispositivos do Windows](using-the-windows-device-portal.md) é criado sobre as APIs REST que você pode usar para acessar os dados e controlar seu dispositivo de forma programática.</span><span class="sxs-lookup"><span data-stu-id="c13da-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="c13da-106">Implantação do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c13da-106">App deloyment</span></span>

<span data-ttu-id="c13da-107">**/API/app/PackageManager/Package (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="c13da-108">Desinstala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="c13da-108">Uninstalls an app</span></span>

<span data-ttu-id="c13da-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-109">Parameters</span></span>
* <span data-ttu-id="c13da-110">Package: nome de arquivo do pacote a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="c13da-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="c13da-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="c13da-112">Instala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="c13da-112">Installs an App</span></span>

<span data-ttu-id="c13da-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-113">Parameters</span></span>
* <span data-ttu-id="c13da-114">Package: nome do arquivo do pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="c13da-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="c13da-115">Carga</span><span class="sxs-lookup"><span data-stu-id="c13da-115">Payload</span></span>
* <span data-ttu-id="c13da-116">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="c13da-116">multi-part conforming http body</span></span>

<span data-ttu-id="c13da-117">**/API/app/PackageManager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="c13da-118">Recupera a lista de aplicativos instalados no sistema, com detalhes</span><span class="sxs-lookup"><span data-stu-id="c13da-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="c13da-119">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-119">Return data</span></span>
* <span data-ttu-id="c13da-120">Lista de pacotes instalados com detalhes</span><span class="sxs-lookup"><span data-stu-id="c13da-120">List of installed packages with details</span></span>

<span data-ttu-id="c13da-121">**/API/app/PackageManager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="c13da-122">Obtém o status da instalação do aplicativo em andamento</span><span class="sxs-lookup"><span data-stu-id="c13da-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="c13da-123">Coleta de despejo</span><span class="sxs-lookup"><span data-stu-id="c13da-123">Dump collection</span></span>

<span data-ttu-id="c13da-124">**/API/Debug/dump/UserMode/crashcontrol (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="c13da-125">Desabilita a coleta de despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="c13da-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="c13da-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-126">Parameters</span></span>
* <span data-ttu-id="c13da-127">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c13da-127">packageFullname : package name</span></span>

<span data-ttu-id="c13da-128">**/API/Debug/dump/UserMode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="c13da-129">Obtém as configurações para coleta de despejo de memória de aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="c13da-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="c13da-130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-130">Parameters</span></span>
* <span data-ttu-id="c13da-131">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c13da-131">packageFullname : package name</span></span>

<span data-ttu-id="c13da-132">**/API/Debug/dump/UserMode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="c13da-133">Habilita e define as configurações de controle de despejo para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="c13da-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="c13da-134">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-134">Parameters</span></span>
* <span data-ttu-id="c13da-135">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c13da-135">packageFullname : package name</span></span>

<span data-ttu-id="c13da-136">**/API/Debug/dump/UserMode/crashdump (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="c13da-137">Exclui um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="c13da-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c13da-138">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-138">Parameters</span></span>
* <span data-ttu-id="c13da-139">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c13da-139">packageFullname : package name</span></span>
* <span data-ttu-id="c13da-140">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="c13da-140">fileName : dump file name</span></span>

<span data-ttu-id="c13da-141">**/API/Debug/dump/UserMode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="c13da-142">Recupera um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="c13da-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c13da-143">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-143">Parameters</span></span>
* <span data-ttu-id="c13da-144">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c13da-144">packageFullname : package name</span></span>
* <span data-ttu-id="c13da-145">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="c13da-145">fileName : dump file name</span></span>

<span data-ttu-id="c13da-146">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-146">Return data</span></span>
* <span data-ttu-id="c13da-147">Arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="c13da-147">Dump file.</span></span> <span data-ttu-id="c13da-148">Inspecione com o WinDbg ou o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c13da-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="c13da-149">**/API/Debug/dump/UserMode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="c13da-150">Retorna a lista de todos os despejos de memória para aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="c13da-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="c13da-151">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-151">Return data</span></span>
* <span data-ttu-id="c13da-152">Lista de despejos de memória por aplicativo carregado por lado</span><span class="sxs-lookup"><span data-stu-id="c13da-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="c13da-153">ETW</span><span class="sxs-lookup"><span data-stu-id="c13da-153">ETW</span></span>

<span data-ttu-id="c13da-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="c13da-155">Enumera provedores registrados</span><span class="sxs-lookup"><span data-stu-id="c13da-155">Enumerates registered providers</span></span>

<span data-ttu-id="c13da-156">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-156">Return data</span></span>
* <span data-ttu-id="c13da-157">Lista de provedores, nome amigável e GUID</span><span class="sxs-lookup"><span data-stu-id="c13da-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="c13da-158">**/API/ETW/Session/Realtime (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c13da-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="c13da-159">Cria uma sessão de ETW em tempo real; gerenciado em um WebSocket.</span><span class="sxs-lookup"><span data-stu-id="c13da-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="c13da-160">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-160">Return data</span></span>
* <span data-ttu-id="c13da-161">Eventos ETW dos provedores habilitados</span><span class="sxs-lookup"><span data-stu-id="c13da-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="c13da-162">Sistema operacional holográfico</span><span class="sxs-lookup"><span data-stu-id="c13da-162">Holographic OS</span></span>

<span data-ttu-id="c13da-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="c13da-164">Retorna uma lista de provedores de ETW específicos do HoloLens que não estão registrados no sistema</span><span class="sxs-lookup"><span data-stu-id="c13da-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="c13da-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="c13da-166">Retorna os Estados de todos os serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="c13da-166">Returns the states of all services running.</span></span>

<span data-ttu-id="c13da-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="c13da-168">Obtém o IPD armazenado (distância interpupillary) em milímetros</span><span class="sxs-lookup"><span data-stu-id="c13da-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="c13da-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="c13da-170">Define o IPD</span><span class="sxs-lookup"><span data-stu-id="c13da-170">Sets the IPD</span></span>

<span data-ttu-id="c13da-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-171">Parameters</span></span>
* <span data-ttu-id="c13da-172">IPD: novo valor de IPD a ser definido em milímetros</span><span class="sxs-lookup"><span data-stu-id="c13da-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="c13da-173">**/API/Holographic/os/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="c13da-174">Obter requisitos de HTTPS para o Device Portal</span><span class="sxs-lookup"><span data-stu-id="c13da-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c13da-175">**/API/Holographic/os/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="c13da-176">Define os requisitos de HTTPS para o portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="c13da-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c13da-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-177">Parameters</span></span>
* <span data-ttu-id="c13da-178">obrigatório: Sim, não ou padrão</span><span class="sxs-lookup"><span data-stu-id="c13da-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="c13da-179">Percepção de Holographic</span><span class="sxs-lookup"><span data-stu-id="c13da-179">Holographic Perception</span></span>

<span data-ttu-id="c13da-180">**/API/Holographic/Perception/Client (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c13da-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="c13da-181">Aceita atualizações do WebSocket e executa um cliente de percepção que envia atualizações a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="c13da-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="c13da-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-182">Parameters</span></span>
* <span data-ttu-id="c13da-183">clientmode: "ativo" força o modo de controle visual quando ele não pode ser estabelecido passivamente</span><span class="sxs-lookup"><span data-stu-id="c13da-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="c13da-184">Holographic térmico</span><span class="sxs-lookup"><span data-stu-id="c13da-184">Holographic Thermal</span></span>

<span data-ttu-id="c13da-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="c13da-186">Obter o estágio térmico do dispositivo (0 normal, 1 quente, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="c13da-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="c13da-187">Controle de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="c13da-187">Perception Simulation Control</span></span>

<span data-ttu-id="c13da-188">**/API/Holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="c13da-189">Obter o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="c13da-189">Get the simulation mode</span></span>

<span data-ttu-id="c13da-190">**/API/Holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="c13da-191">Definir o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="c13da-191">Set the simulation mode</span></span>

<span data-ttu-id="c13da-192">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-192">Parameters</span></span>
* <span data-ttu-id="c13da-193">modo: modo de simulação: padrão, simulação, remoto, herdado</span><span class="sxs-lookup"><span data-stu-id="c13da-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="c13da-194">**/API/Holographic/Simulation/Control/Stream (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="c13da-195">Excluir um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="c13da-195">Delete a control stream.</span></span>

<span data-ttu-id="c13da-196">**/API/Holographic/Simulation/Control/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c13da-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="c13da-197">Abra uma conexão de soquete da Web para um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="c13da-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="c13da-198">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="c13da-199">Crie um fluxo de controle (prioridade necessária) ou poste dados em um fluxo criado (streamid necessário).</span><span class="sxs-lookup"><span data-stu-id="c13da-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="c13da-200">Espera-se que os dados postados sejam do tipo ' application/octet-stream '.</span><span class="sxs-lookup"><span data-stu-id="c13da-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="c13da-201">Reprodução da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="c13da-201">Perception Simulation Playback</span></span>

<span data-ttu-id="c13da-202">**/API/Holographic/Simulation/playback/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="c13da-203">Excluir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-203">Delete a recording.</span></span>

<span data-ttu-id="c13da-204">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-204">Parameters</span></span>
* <span data-ttu-id="c13da-205">gravação: o nome da gravação a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="c13da-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="c13da-206">**/API/Holographic/Simulation/playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="c13da-207">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-207">Upload a recording.</span></span>

<span data-ttu-id="c13da-208">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="c13da-209">Obter todas as gravações.</span><span class="sxs-lookup"><span data-stu-id="c13da-209">Get all recordings.</span></span>

<span data-ttu-id="c13da-210">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="c13da-211">Obter o estado de reprodução atual de uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="c13da-212">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-212">Parameters</span></span>
* <span data-ttu-id="c13da-213">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-213">recording : Name of recording.</span></span>

<span data-ttu-id="c13da-214">**/API/Holographic/Simulation/playback/Session/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="c13da-215">Descarregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-215">Unload a recording.</span></span>

<span data-ttu-id="c13da-216">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-216">Parameters</span></span>
* <span data-ttu-id="c13da-217">gravação: nome da gravação a ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="c13da-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="c13da-218">**/API/Holographic/Simulation/playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="c13da-219">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-219">Load a recording.</span></span>

<span data-ttu-id="c13da-220">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-220">Parameters</span></span>
* <span data-ttu-id="c13da-221">gravação: o nome da gravação a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="c13da-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="c13da-222">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="c13da-223">Obter todas as gravações carregadas.</span><span class="sxs-lookup"><span data-stu-id="c13da-223">Get all loaded recordings.</span></span>

<span data-ttu-id="c13da-224">**/API/Holographic/Simulation/playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="c13da-225">Pausar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-225">Pause a recording.</span></span>

<span data-ttu-id="c13da-226">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-226">Parameters</span></span>
* <span data-ttu-id="c13da-227">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-227">recording : Name of recording.</span></span>

<span data-ttu-id="c13da-228">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="c13da-229">Reproduzir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-229">Play a recording.</span></span>

<span data-ttu-id="c13da-230">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-230">Parameters</span></span>
* <span data-ttu-id="c13da-231">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-231">recording : Name of recording.</span></span>

<span data-ttu-id="c13da-232">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="c13da-233">Parar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-233">Stop a recording.</span></span>

<span data-ttu-id="c13da-234">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-234">Parameters</span></span>
* <span data-ttu-id="c13da-235">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-235">recording : Name of recording.</span></span>

<span data-ttu-id="c13da-236">**/API/Holographic/Simulation/playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="c13da-237">Obter os tipos de dados em uma gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="c13da-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="c13da-238">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-238">Parameters</span></span>
* <span data-ttu-id="c13da-239">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="c13da-240">Gravação da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="c13da-240">Perception Simulation Recording</span></span>

<span data-ttu-id="c13da-241">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="c13da-242">Inicie uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-242">Start a recording.</span></span> <span data-ttu-id="c13da-243">Apenas uma única gravação pode estar ativa de uma vez.</span><span class="sxs-lookup"><span data-stu-id="c13da-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="c13da-244">É necessário definir um dos cabeçalhos, as mãos, spatialMapping ou ambiente.</span><span class="sxs-lookup"><span data-stu-id="c13da-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="c13da-245">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-245">Parameters</span></span>
* <span data-ttu-id="c13da-246">Cabeçalho: Defina como 1 para registrar dados de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="c13da-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="c13da-247">Hands: Defina como 1 para gravar dados de mão.</span><span class="sxs-lookup"><span data-stu-id="c13da-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="c13da-248">spatialMapping: Defina como 1 para registrar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="c13da-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="c13da-249">ambiente: Defina como 1 para gravar dados do ambiente.</span><span class="sxs-lookup"><span data-stu-id="c13da-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="c13da-250">Nome: o nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-250">name : Name of the recording.</span></span>
* <span data-ttu-id="c13da-251">singleSpatialMappingFrame: Defina como 1 para gravar apenas um único quadro de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="c13da-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="c13da-252">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="c13da-253">Obter estado de gravação.</span><span class="sxs-lookup"><span data-stu-id="c13da-253">Get recording state.</span></span>

<span data-ttu-id="c13da-254">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="c13da-255">Parar a gravação atual.</span><span class="sxs-lookup"><span data-stu-id="c13da-255">Stop the current recording.</span></span> <span data-ttu-id="c13da-256">A gravação será retornada como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c13da-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="c13da-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="c13da-257">Mixed Reality Capture</span></span>

<span data-ttu-id="c13da-258">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="c13da-259">Baixa um arquivo de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c13da-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="c13da-260">Use op = Stream Query parâmetro para streaming.</span><span class="sxs-lookup"><span data-stu-id="c13da-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="c13da-261">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-261">Parameters</span></span>
* <span data-ttu-id="c13da-262">filename: nome, hex64 codificado, do arquivo de vídeo a ser obtido</span><span class="sxs-lookup"><span data-stu-id="c13da-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="c13da-263">op: fluxo</span><span class="sxs-lookup"><span data-stu-id="c13da-263">op : stream</span></span>

<span data-ttu-id="c13da-264">**/API/Holographic/MRC/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="c13da-265">Exclui uma gravação de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c13da-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="c13da-266">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-266">Parameters</span></span>
* <span data-ttu-id="c13da-267">filename: nome, hex64 codificado, do arquivo a ser excluído</span><span class="sxs-lookup"><span data-stu-id="c13da-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="c13da-268">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="c13da-269">Retorna a lista de arquivos de realidade misturada armazenados no dispositivo</span><span class="sxs-lookup"><span data-stu-id="c13da-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="c13da-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="c13da-271">Usa uma foto de realidade misturada e cria um arquivo no dispositivo</span><span class="sxs-lookup"><span data-stu-id="c13da-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="c13da-272">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-272">Parameters</span></span>
* <span data-ttu-id="c13da-273">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c13da-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="c13da-274">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c13da-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="c13da-275">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="c13da-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="c13da-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="c13da-277">Obtém as configurações padrão da captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c13da-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="c13da-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="c13da-279">Define as configurações padrão de captura de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c13da-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="c13da-280">Algumas dessas configurações são aplicadas à captura de vídeo e foto da MRC do sistema.</span><span class="sxs-lookup"><span data-stu-id="c13da-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="c13da-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="c13da-282">Obtém o status da realidade misturada registrada (em execução, parada)</span><span class="sxs-lookup"><span data-stu-id="c13da-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="c13da-283">**/API/Holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="c13da-284">Obtém a imagem em miniatura do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="c13da-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="c13da-285">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-285">Parameters</span></span>
* <span data-ttu-id="c13da-286">filename: nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada</span><span class="sxs-lookup"><span data-stu-id="c13da-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="c13da-287">**/API/Holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="c13da-288">Inicia uma gravação de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c13da-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="c13da-289">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-289">Parameters</span></span>
* <span data-ttu-id="c13da-290">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c13da-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="c13da-291">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c13da-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="c13da-292">MIC: capturar microfone: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c13da-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="c13da-293">loopback: capturar o áudio do aplicativo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c13da-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="c13da-294">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="c13da-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="c13da-295">Vstab: (somente HoloLens 2) habilitar estabilização de vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="c13da-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="c13da-296">vstabbuffer: (somente HoloLens 2) latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="c13da-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="c13da-297">**/API/Holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="c13da-298">Interrompe a gravação atual da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c13da-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="c13da-299">Streaming de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c13da-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="c13da-300">O HoloLens dá suporte à visualização dinâmica de realidade misturada por meio do download em partes de um MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="c13da-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="c13da-301">Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:</span><span class="sxs-lookup"><span data-stu-id="c13da-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="c13da-302">holo: capturar hologramas: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="c13da-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c13da-303">PV: capturar câmera PV: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="c13da-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c13da-304">MIC: capturar microfone: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="c13da-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c13da-305">loopback: capturar áudio do aplicativo: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="c13da-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="c13da-306">Se nenhum deles for especificado: os hologramas, a câmera de foto/vídeo e o áudio do aplicativo serão capturados</span><span class="sxs-lookup"><span data-stu-id="c13da-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="c13da-307">Se houver algum especificado: os parâmetros não especificados serão padronizados como false</span><span class="sxs-lookup"><span data-stu-id="c13da-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="c13da-308">Parâmetros opcionais (somente HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="c13da-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="c13da-309">RenderFromCamera: Render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="c13da-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="c13da-310">Vstab: habilitar estabilização de vídeo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c13da-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="c13da-311">vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="c13da-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="c13da-312">**/API/Holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="c13da-313">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="c13da-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="c13da-314">**/API/Holographic/Stream/live_high. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="c13da-315">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="c13da-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="c13da-316">**/API/Holographic/Stream/live_med. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="c13da-317">Um fluxo 854x480p 30fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="c13da-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="c13da-318">**/API/Holographic/Stream/live_low. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="c13da-319">Um fluxo 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="c13da-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="c13da-320">Rede</span><span class="sxs-lookup"><span data-stu-id="c13da-320">Networking</span></span>

<span data-ttu-id="c13da-321">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="c13da-322">Obter a configuração de IP atual</span><span class="sxs-lookup"><span data-stu-id="c13da-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="c13da-323">Informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="c13da-323">OS Information</span></span>

<span data-ttu-id="c13da-324">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="c13da-325">Obtém informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="c13da-325">Gets operating system information</span></span>

<span data-ttu-id="c13da-326">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="c13da-327">Obtém o nome do computador</span><span class="sxs-lookup"><span data-stu-id="c13da-327">Gets the machine name</span></span>

<span data-ttu-id="c13da-328">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="c13da-329">Define o nome do computador</span><span class="sxs-lookup"><span data-stu-id="c13da-329">Sets the machine name</span></span>

<span data-ttu-id="c13da-330">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-330">Parameters</span></span>
* <span data-ttu-id="c13da-331">Nome: novo nome do computador, hex64 codificado, para definir como</span><span class="sxs-lookup"><span data-stu-id="c13da-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="c13da-332">Dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="c13da-332">Performance data</span></span>

<span data-ttu-id="c13da-333">**/API/ResourceManager/Processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="c13da-334">Retorna a lista de processos em execução com detalhes</span><span class="sxs-lookup"><span data-stu-id="c13da-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="c13da-335">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-335">Return data</span></span>
* <span data-ttu-id="c13da-336">JSON com lista de processos e detalhes para cada processo</span><span class="sxs-lookup"><span data-stu-id="c13da-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="c13da-337">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="c13da-338">Retorna estatísticas de desempenho do sistema (leitura/gravação de e/s, estatísticas de memória etc.)</span><span class="sxs-lookup"><span data-stu-id="c13da-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="c13da-339">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-339">Return data</span></span>
* <span data-ttu-id="c13da-340">JSON com informações do sistema: CPU, GPU, memória, rede, e/s</span><span class="sxs-lookup"><span data-stu-id="c13da-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="c13da-341">Energia</span><span class="sxs-lookup"><span data-stu-id="c13da-341">Power</span></span>

<span data-ttu-id="c13da-342">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="c13da-343">Obtém o estado da bateria atual</span><span class="sxs-lookup"><span data-stu-id="c13da-343">Gets the current battery state</span></span>

<span data-ttu-id="c13da-344">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="c13da-345">Verifica se o sistema está em um estado de baixa energia</span><span class="sxs-lookup"><span data-stu-id="c13da-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="c13da-346">Controle Remoto</span><span class="sxs-lookup"><span data-stu-id="c13da-346">Remote Control</span></span>

<span data-ttu-id="c13da-347">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="c13da-348">Reinicia o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="c13da-348">Restarts the target device</span></span>

<span data-ttu-id="c13da-349">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="c13da-350">Desliga o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="c13da-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="c13da-351">Gerenciador de Tarefas</span><span class="sxs-lookup"><span data-stu-id="c13da-351">Task Manager</span></span>

<span data-ttu-id="c13da-352">**/API/taskmanager/app (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="c13da-353">Para um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="c13da-353">Stops a modern app</span></span>

<span data-ttu-id="c13da-354">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-354">Parameters</span></span>
* <span data-ttu-id="c13da-355">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="c13da-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="c13da-356">forcestop: forçar a interrupção de todos os processos (= Sim)</span><span class="sxs-lookup"><span data-stu-id="c13da-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="c13da-357">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="c13da-358">Inicia um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="c13da-358">Starts a modern app</span></span>

<span data-ttu-id="c13da-359">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-359">Parameters</span></span>
* <span data-ttu-id="c13da-360">AppID: PRAID do aplicativo a ser iniciado, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="c13da-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="c13da-361">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="c13da-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="c13da-362">Gerenciamento de WiFi</span><span class="sxs-lookup"><span data-stu-id="c13da-362">WiFi Management</span></span>

<span data-ttu-id="c13da-363">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="c13da-364">Enumera interfaces de rede sem fio</span><span class="sxs-lookup"><span data-stu-id="c13da-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="c13da-365">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-365">Return data</span></span>
* <span data-ttu-id="c13da-366">Lista de interfaces sem fio com detalhes (GUID, descrição, etc.)</span><span class="sxs-lookup"><span data-stu-id="c13da-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="c13da-367">**/API/WiFi/Network (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c13da-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="c13da-368">Exclui um perfil associado a uma rede em uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="c13da-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="c13da-369">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-369">Parameters</span></span>
* <span data-ttu-id="c13da-370">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="c13da-370">interface : network interface guid</span></span>
* <span data-ttu-id="c13da-371">Perfil: nome do perfil</span><span class="sxs-lookup"><span data-stu-id="c13da-371">profile : profile name</span></span>

<span data-ttu-id="c13da-372">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="c13da-373">Enumera redes sem fio na interface de rede especificada</span><span class="sxs-lookup"><span data-stu-id="c13da-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="c13da-374">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-374">Parameters</span></span>
* <span data-ttu-id="c13da-375">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="c13da-375">interface : network interface guid</span></span>

<span data-ttu-id="c13da-376">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-376">Return data</span></span>
* <span data-ttu-id="c13da-377">Lista de redes sem fio encontradas na interface de rede com detalhes</span><span class="sxs-lookup"><span data-stu-id="c13da-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="c13da-378">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="c13da-379">Conecta ou desconecta-se a uma rede na interface especificada</span><span class="sxs-lookup"><span data-stu-id="c13da-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="c13da-380">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-380">Parameters</span></span>
* <span data-ttu-id="c13da-381">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="c13da-381">interface : network interface guid</span></span>
* <span data-ttu-id="c13da-382">SSID: SSID, hex64 codificado, para se conectar ao</span><span class="sxs-lookup"><span data-stu-id="c13da-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="c13da-383">op: conectar ou desconectar</span><span class="sxs-lookup"><span data-stu-id="c13da-383">op : connect or disconnect</span></span>
* <span data-ttu-id="c13da-384">CreateProfile: Sim ou não</span><span class="sxs-lookup"><span data-stu-id="c13da-384">createprofile : yes or no</span></span>
* <span data-ttu-id="c13da-385">chave: chave compartilhada, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="c13da-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="c13da-386">Gravador de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="c13da-386">Windows Performance Recorder</span></span>

<span data-ttu-id="c13da-387">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="c13da-388">Carrega um perfil WPR e inicia o rastreamento usando o perfil carregado.</span><span class="sxs-lookup"><span data-stu-id="c13da-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="c13da-389">Carga</span><span class="sxs-lookup"><span data-stu-id="c13da-389">Payload</span></span>
* <span data-ttu-id="c13da-390">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="c13da-390">multi-part conforming http body</span></span>

<span data-ttu-id="c13da-391">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-391">Return data</span></span>
* <span data-ttu-id="c13da-392">Retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="c13da-392">Returns the WPR session status.</span></span>

<span data-ttu-id="c13da-393">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="c13da-394">Recupera o status da sessão WPR</span><span class="sxs-lookup"><span data-stu-id="c13da-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="c13da-395">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-395">Return data</span></span>
* <span data-ttu-id="c13da-396">Status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="c13da-396">WPR session status.</span></span>

<span data-ttu-id="c13da-397">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="c13da-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="c13da-398">Interrompe uma sessão de rastreamento de WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="c13da-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="c13da-399">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-399">Return data</span></span>
* <span data-ttu-id="c13da-400">Retorna o arquivo ETL de rastreamento</span><span class="sxs-lookup"><span data-stu-id="c13da-400">Returns the trace ETL file</span></span>

<span data-ttu-id="c13da-401">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="c13da-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="c13da-402">Inicia uma sessão de rastreamento WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="c13da-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="c13da-403">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c13da-403">Parameters</span></span>
* <span data-ttu-id="c13da-404">Perfil: nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="c13da-404">profile : Profile name.</span></span> <span data-ttu-id="c13da-405">Os perfis disponíveis são armazenados em perfprofiles/Profiles. JSON</span><span class="sxs-lookup"><span data-stu-id="c13da-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="c13da-406">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c13da-406">Return data</span></span>
* <span data-ttu-id="c13da-407">Em Iniciar, retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="c13da-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="c13da-408">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c13da-408">See also</span></span>
* [<span data-ttu-id="c13da-409">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="c13da-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="c13da-410">Referência da API principal do portal do dispositivo (UWP)</span><span class="sxs-lookup"><span data-stu-id="c13da-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

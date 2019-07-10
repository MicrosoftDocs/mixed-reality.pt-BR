---
title: Referência da API do portal de dispositivos
description: Referência da API para o do Windows Device Portal no HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, do Windows Device Portal, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694422"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="160ee-104">Referência da API do portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="160ee-104">Device portal API reference</span></span>

<span data-ttu-id="160ee-105">Tudo na [Windows Device Portal](using-the-windows-device-portal.md) baseia-se em REST da API que você pode usar para acessar os dados e controlar seu dispositivo por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="160ee-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="160ee-106">Implantação de aplicativo</span><span class="sxs-lookup"><span data-stu-id="160ee-106">App deloyment</span></span>

<span data-ttu-id="160ee-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="160ee-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="160ee-108">Desinstala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="160ee-108">Uninstalls an app</span></span>

<span data-ttu-id="160ee-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-109">Parameters</span></span>
* <span data-ttu-id="160ee-110">pacote: Nome do arquivo do pacote a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="160ee-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="160ee-111">**/API/App/packagemanager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="160ee-112">Instala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="160ee-112">Installs an App</span></span>

<span data-ttu-id="160ee-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-113">Parameters</span></span>
* <span data-ttu-id="160ee-114">pacote: Nome do arquivo do pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="160ee-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="160ee-115">carga</span><span class="sxs-lookup"><span data-stu-id="160ee-115">Payload</span></span>
* <span data-ttu-id="160ee-116">corpo de http em conformidade com várias partes</span><span class="sxs-lookup"><span data-stu-id="160ee-116">multi-part conforming http body</span></span>

<span data-ttu-id="160ee-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="160ee-118">Recupera a lista de aplicativos instalados no sistema, com detalhes</span><span class="sxs-lookup"><span data-stu-id="160ee-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="160ee-119">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-119">Return data</span></span>
* <span data-ttu-id="160ee-120">Lista de pacotes instalados com detalhes</span><span class="sxs-lookup"><span data-stu-id="160ee-120">List of installed packages with details</span></span>

<span data-ttu-id="160ee-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="160ee-122">Obtém o status na instalação do aplicativo de progresso</span><span class="sxs-lookup"><span data-stu-id="160ee-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="160ee-123">Coleta de despejo</span><span class="sxs-lookup"><span data-stu-id="160ee-123">Dump collection</span></span>

<span data-ttu-id="160ee-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="160ee-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="160ee-125">Desabilita a coleta de despejo para um aplicativo com sideload de falhas</span><span class="sxs-lookup"><span data-stu-id="160ee-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="160ee-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-126">Parameters</span></span>
* <span data-ttu-id="160ee-127">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="160ee-127">packageFullname : package name</span></span>

<span data-ttu-id="160ee-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="160ee-129">Obtém as configurações para aplicativos de sideload a coleta de despejo de memória</span><span class="sxs-lookup"><span data-stu-id="160ee-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="160ee-130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-130">Parameters</span></span>
* <span data-ttu-id="160ee-131">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="160ee-131">packageFullname : package name</span></span>

<span data-ttu-id="160ee-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="160ee-133">Habilita e define as configurações de controle de despejo para um aplicativo de sideload</span><span class="sxs-lookup"><span data-stu-id="160ee-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="160ee-134">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-134">Parameters</span></span>
* <span data-ttu-id="160ee-135">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="160ee-135">packageFullname : package name</span></span>

<span data-ttu-id="160ee-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="160ee-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="160ee-137">Exclui um despejo de memória para um aplicativo de sideload</span><span class="sxs-lookup"><span data-stu-id="160ee-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="160ee-138">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-138">Parameters</span></span>
* <span data-ttu-id="160ee-139">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="160ee-139">packageFullname : package name</span></span>
* <span data-ttu-id="160ee-140">nome do arquivo: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="160ee-140">fileName : dump file name</span></span>

<span data-ttu-id="160ee-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="160ee-142">Recupera um despejo de memória para um aplicativo de sideload</span><span class="sxs-lookup"><span data-stu-id="160ee-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="160ee-143">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-143">Parameters</span></span>
* <span data-ttu-id="160ee-144">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="160ee-144">packageFullname : package name</span></span>
* <span data-ttu-id="160ee-145">nome do arquivo: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="160ee-145">fileName : dump file name</span></span>

<span data-ttu-id="160ee-146">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-146">Return data</span></span>
* <span data-ttu-id="160ee-147">Arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="160ee-147">Dump file.</span></span> <span data-ttu-id="160ee-148">Inspecionar com o Visual Studio ou WinDbg</span><span class="sxs-lookup"><span data-stu-id="160ee-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="160ee-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="160ee-150">Retorna a lista de todos os despejos de memória para aplicativos sideloaded</span><span class="sxs-lookup"><span data-stu-id="160ee-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="160ee-151">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-151">Return data</span></span>
* <span data-ttu-id="160ee-152">Despejos de lista de falhas por aplicativo carregado do lado do</span><span class="sxs-lookup"><span data-stu-id="160ee-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="160ee-153">ETW</span><span class="sxs-lookup"><span data-stu-id="160ee-153">ETW</span></span>

<span data-ttu-id="160ee-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="160ee-155">Enumera os provedores registrados</span><span class="sxs-lookup"><span data-stu-id="160ee-155">Enumerates registered providers</span></span>

<span data-ttu-id="160ee-156">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-156">Return data</span></span>
* <span data-ttu-id="160ee-157">Lista de provedores, o nome amigável e o GUID</span><span class="sxs-lookup"><span data-stu-id="160ee-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="160ee-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="160ee-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="160ee-159">Cria uma sessão ETW em tempo real; gerenciado por um websocket.</span><span class="sxs-lookup"><span data-stu-id="160ee-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="160ee-160">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-160">Return data</span></span>
* <span data-ttu-id="160ee-161">Eventos ETW de provedores habilitados</span><span class="sxs-lookup"><span data-stu-id="160ee-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="160ee-162">Sistema operacional holográfico</span><span class="sxs-lookup"><span data-stu-id="160ee-162">Holographic OS</span></span>

<span data-ttu-id="160ee-163">**/API/holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="160ee-164">Retorna uma lista de provedores ETW específicos HoloLens que não estão registrados com o sistema</span><span class="sxs-lookup"><span data-stu-id="160ee-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="160ee-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="160ee-166">Retorna os estados de todos os serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="160ee-166">Returns the states of all services running.</span></span>

<span data-ttu-id="160ee-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="160ee-168">Obtém o IPD armazenado (Interpupillary distância) em milímetros</span><span class="sxs-lookup"><span data-stu-id="160ee-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="160ee-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="160ee-170">Define o IPD</span><span class="sxs-lookup"><span data-stu-id="160ee-170">Sets the IPD</span></span>

<span data-ttu-id="160ee-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-171">Parameters</span></span>
* <span data-ttu-id="160ee-172">IPD: Novo valor IPD a ser definido em milímetros</span><span class="sxs-lookup"><span data-stu-id="160ee-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="160ee-173">**/API/holographic/os/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="160ee-174">Obter requisitos de HTTPS para o Device Portal</span><span class="sxs-lookup"><span data-stu-id="160ee-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="160ee-175">**/API/holographic/os/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="160ee-176">Define os requisitos de HTTPS para o Portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="160ee-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="160ee-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-177">Parameters</span></span>
* <span data-ttu-id="160ee-178">obrigatório: Sim, não ou padrão</span><span class="sxs-lookup"><span data-stu-id="160ee-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="160ee-179">Percepção holográfica</span><span class="sxs-lookup"><span data-stu-id="160ee-179">Holographic Perception</span></span>

<span data-ttu-id="160ee-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="160ee-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="160ee-181">Aceita o websocket upgrades e executa o cliente percepção que envia as atualizações em 30 fps.</span><span class="sxs-lookup"><span data-stu-id="160ee-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="160ee-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-182">Parameters</span></span>
* <span data-ttu-id="160ee-183">clientmode: "ativo" força o modo de controle visual quando não puder ser estabelecida passivamente</span><span class="sxs-lookup"><span data-stu-id="160ee-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="160ee-184">Holográfico térmico</span><span class="sxs-lookup"><span data-stu-id="160ee-184">Holographic Thermal</span></span>

<span data-ttu-id="160ee-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="160ee-186">Obter o estágio térmico do dispositivo (0 normal, 1 passiva, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="160ee-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="160ee-187">Controle de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="160ee-187">Perception Simulation Control</span></span>

<span data-ttu-id="160ee-188">**/API/holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="160ee-189">Obter o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="160ee-189">Get the simulation mode</span></span>

<span data-ttu-id="160ee-190">**/API/holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="160ee-191">Definir o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="160ee-191">Set the simulation mode</span></span>

<span data-ttu-id="160ee-192">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-192">Parameters</span></span>
* <span data-ttu-id="160ee-193">modo: modo de simulação: padrão, a simulação, remoto, herdado</span><span class="sxs-lookup"><span data-stu-id="160ee-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="160ee-194">**/API/holographic/Simulation/Control/Stream (excluir)**</span><span class="sxs-lookup"><span data-stu-id="160ee-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="160ee-195">Exclua um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="160ee-195">Delete a control stream.</span></span>

<span data-ttu-id="160ee-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="160ee-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="160ee-197">Abra uma conexão de soquete da web para um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="160ee-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="160ee-198">**/API/holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="160ee-199">Criar um fluxo de controle (prioridade é necessária) ou dados de postagem em um fluxo criado (o streamId é necessário).</span><span class="sxs-lookup"><span data-stu-id="160ee-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="160ee-200">Os dados postados deve ser do tipo ' application/octet-stream'.</span><span class="sxs-lookup"><span data-stu-id="160ee-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="160ee-201">Reprodução de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="160ee-201">Perception Simulation Playback</span></span>

<span data-ttu-id="160ee-202">**/API/holographic/Simulation/playback/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="160ee-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="160ee-203">Exclua uma gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-203">Delete a recording.</span></span>

<span data-ttu-id="160ee-204">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-204">Parameters</span></span>
* <span data-ttu-id="160ee-205">gravação: Nome do registro para excluir.</span><span class="sxs-lookup"><span data-stu-id="160ee-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="160ee-206">**/API/holographic/Simulation/playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="160ee-207">Carregue uma gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-207">Upload a recording.</span></span>

<span data-ttu-id="160ee-208">**/API/holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="160ee-209">Obtenha todas as gravações.</span><span class="sxs-lookup"><span data-stu-id="160ee-209">Get all recordings.</span></span>

<span data-ttu-id="160ee-210">**/API/holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="160ee-211">Obter o estado atual de reprodução de uma gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="160ee-212">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-212">Parameters</span></span>
* <span data-ttu-id="160ee-213">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-213">recording : Name of recording.</span></span>

<span data-ttu-id="160ee-214">**/API/holographic/Simulation/playback/Session/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="160ee-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="160ee-215">Descarrega uma gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-215">Unload a recording.</span></span>

<span data-ttu-id="160ee-216">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-216">Parameters</span></span>
* <span data-ttu-id="160ee-217">gravação: Nome do registro para descarregar.</span><span class="sxs-lookup"><span data-stu-id="160ee-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="160ee-218">**/API/holographic/Simulation/playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="160ee-219">Uma gravação de carga.</span><span class="sxs-lookup"><span data-stu-id="160ee-219">Load a recording.</span></span>

<span data-ttu-id="160ee-220">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-220">Parameters</span></span>
* <span data-ttu-id="160ee-221">gravação: Nome do registro para carregar.</span><span class="sxs-lookup"><span data-stu-id="160ee-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="160ee-222">**/API/holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="160ee-223">Obter todos carregadas gravações.</span><span class="sxs-lookup"><span data-stu-id="160ee-223">Get all loaded recordings.</span></span>

<span data-ttu-id="160ee-224">**/API/holographic/Simulation/playback/Session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="160ee-225">Pause uma gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-225">Pause a recording.</span></span>

<span data-ttu-id="160ee-226">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-226">Parameters</span></span>
* <span data-ttu-id="160ee-227">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-227">recording : Name of recording.</span></span>

<span data-ttu-id="160ee-228">**/API/holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="160ee-229">Reproduzir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-229">Play a recording.</span></span>

<span data-ttu-id="160ee-230">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-230">Parameters</span></span>
* <span data-ttu-id="160ee-231">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-231">recording : Name of recording.</span></span>

<span data-ttu-id="160ee-232">**/API/holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="160ee-233">Pare uma gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-233">Stop a recording.</span></span>

<span data-ttu-id="160ee-234">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-234">Parameters</span></span>
* <span data-ttu-id="160ee-235">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-235">recording : Name of recording.</span></span>

<span data-ttu-id="160ee-236">**/API/holographic/Simulation/playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="160ee-237">Obtenha os tipos de dados em uma gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="160ee-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="160ee-238">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-238">Parameters</span></span>
* <span data-ttu-id="160ee-239">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="160ee-240">Gravação de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="160ee-240">Perception Simulation Recording</span></span>

<span data-ttu-id="160ee-241">**/API/holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="160ee-242">Inicie uma gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-242">Start a recording.</span></span> <span data-ttu-id="160ee-243">Apenas uma única gravação pode estar ativa ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="160ee-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="160ee-244">Um cabeçalho, mãos, spatialMapping ou ambiente deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="160ee-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="160ee-245">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-245">Parameters</span></span>
* <span data-ttu-id="160ee-246">cabeçalho: Definido como 1 para o registro de dados principal.</span><span class="sxs-lookup"><span data-stu-id="160ee-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="160ee-247">mãos: Definido como 1 para registrar dados de mão.</span><span class="sxs-lookup"><span data-stu-id="160ee-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="160ee-248">spatialMapping: Definido como 1 para registrar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="160ee-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="160ee-249">ambiente: Definido como 1 para registrar dados de ambiente.</span><span class="sxs-lookup"><span data-stu-id="160ee-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="160ee-250">nome: Nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="160ee-250">name : Name of the recording.</span></span>
* <span data-ttu-id="160ee-251">singleSpatialMappingFrame : Definido como 1 para registrar somente um quadro de mapeamento espacial único.</span><span class="sxs-lookup"><span data-stu-id="160ee-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="160ee-252">**/API/holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="160ee-253">Obter gravação de estado.</span><span class="sxs-lookup"><span data-stu-id="160ee-253">Get recording state.</span></span>

<span data-ttu-id="160ee-254">**/API/holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="160ee-255">Interrompa a gravação atual.</span><span class="sxs-lookup"><span data-stu-id="160ee-255">Stop the current recording.</span></span> <span data-ttu-id="160ee-256">Gravação será retornada como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="160ee-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="160ee-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="160ee-257">Mixed Reality Capture</span></span>

<span data-ttu-id="160ee-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="160ee-259">Baixa um arquivo de realidade mista do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="160ee-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="160ee-260">Op uso = parâmetro de consulta do stream para streaming.</span><span class="sxs-lookup"><span data-stu-id="160ee-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="160ee-261">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-261">Parameters</span></span>
* <span data-ttu-id="160ee-262">nome do arquivo: O nome, hex64 codificado, do arquivo de vídeo para obter</span><span class="sxs-lookup"><span data-stu-id="160ee-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="160ee-263">op : stream</span><span class="sxs-lookup"><span data-stu-id="160ee-263">op : stream</span></span>

<span data-ttu-id="160ee-264">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="160ee-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="160ee-265">Exclui uma registro do dispositivo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="160ee-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="160ee-266">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-266">Parameters</span></span>
* <span data-ttu-id="160ee-267">nome do arquivo: O nome, hex64 codificado, do arquivo a ser excluído</span><span class="sxs-lookup"><span data-stu-id="160ee-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="160ee-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="160ee-269">Retorna a lista de arquivos de realidade misturada armazenados no dispositivo</span><span class="sxs-lookup"><span data-stu-id="160ee-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="160ee-270">**/API/holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="160ee-271">Tira uma foto de realidade mista e cria um arquivo no dispositivo</span><span class="sxs-lookup"><span data-stu-id="160ee-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="160ee-272">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-272">Parameters</span></span>
* <span data-ttu-id="160ee-273">holo: capturar vntana: verdadeiro ou falso (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="160ee-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="160ee-274">VP: captura PV câmera: verdadeiro ou falso (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="160ee-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="160ee-275">RenderFromCamera : Render (apenas para HoloLens 2) do ponto de vista da câmera de vídeo/foto: verdadeiro ou falso (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="160ee-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="160ee-276">**/API/holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="160ee-277">Obtém o padrão realidade misturada configurações de captura</span><span class="sxs-lookup"><span data-stu-id="160ee-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="160ee-278">**/API/holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="160ee-279">Define o padrão realidade misturada configurações de captura.</span><span class="sxs-lookup"><span data-stu-id="160ee-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="160ee-280">Algumas dessas configurações são aplicadas a foto MRC e captura de vídeo do sistema.</span><span class="sxs-lookup"><span data-stu-id="160ee-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="160ee-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="160ee-282">Obtém o status da realidade misturada registrado (em execução, parado)</span><span class="sxs-lookup"><span data-stu-id="160ee-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="160ee-283">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="160ee-284">Obtém a imagem em miniatura para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="160ee-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="160ee-285">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-285">Parameters</span></span>
* <span data-ttu-id="160ee-286">nome do arquivo: O nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="160ee-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="160ee-287">**/API/holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="160ee-288">Inicia uma gravação de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="160ee-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="160ee-289">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-289">Parameters</span></span>
* <span data-ttu-id="160ee-290">holo: capturar vntana: verdadeiro ou falso (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="160ee-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="160ee-291">VP: captura PV câmera: verdadeiro ou falso (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="160ee-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="160ee-292">MIC: captura microfone: verdadeiro ou falso (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="160ee-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="160ee-293">loopback: capturar o áudio do aplicativo: verdadeiro ou falso (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="160ee-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="160ee-294">RenderFromCamera : Render (apenas para HoloLens 2) do ponto de vista da câmera de vídeo/foto: verdadeiro ou falso (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="160ee-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="160ee-295">vstab : (Apenas para HoloLens 2) habilite estabilização de vídeo: verdadeiro ou falso (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="160ee-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="160ee-296">vstabbuffer: Latência de buffer de estabilização de vídeo (apenas para HoloLens 2): 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="160ee-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="160ee-297">**/API/holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="160ee-298">Paradas de gravação de realidade mista do atual</span><span class="sxs-lookup"><span data-stu-id="160ee-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="160ee-299">Realidade mista de Streaming</span><span class="sxs-lookup"><span data-stu-id="160ee-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="160ee-300">HoloLens dá suporte à visualização dinâmica de realidade misturada por meio de download em partes de um mp4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="160ee-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="160ee-301">Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:</span><span class="sxs-lookup"><span data-stu-id="160ee-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="160ee-302">holo: capturar vntana: true ou false</span><span class="sxs-lookup"><span data-stu-id="160ee-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="160ee-303">VP: captura PV câmera: true ou false</span><span class="sxs-lookup"><span data-stu-id="160ee-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="160ee-304">MIC: captura microfone: true ou false</span><span class="sxs-lookup"><span data-stu-id="160ee-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="160ee-305">loopback: capturar o áudio do aplicativo: true ou false</span><span class="sxs-lookup"><span data-stu-id="160ee-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="160ee-306">Se nenhum desses são especificados: serão capturados hologramas, foto/câmera de vídeo e áudio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="160ee-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="160ee-307">Se algum for especificado: os parâmetros não especificados usará como padrão false</span><span class="sxs-lookup"><span data-stu-id="160ee-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="160ee-308">Parâmetros opcionais (apenas para HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="160ee-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="160ee-309">RenderFromCamera: renderizar do ponto de vista da câmera de vídeo/foto: verdadeiro ou falso (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="160ee-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="160ee-310">vstab: habilitar a estabilização de vídeo: verdadeiro ou falso (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="160ee-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="160ee-311">vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="160ee-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="160ee-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="160ee-313">Um fluxo de 5Mbit 1280x720p 30fps.</span><span class="sxs-lookup"><span data-stu-id="160ee-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="160ee-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="160ee-315">Um fluxo de 5Mbit 1280x720p 30fps.</span><span class="sxs-lookup"><span data-stu-id="160ee-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="160ee-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="160ee-317">Um fluxo de 30fps 2.5Mbit 854x480p.</span><span class="sxs-lookup"><span data-stu-id="160ee-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="160ee-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="160ee-319">Um fluxo de 15 qps 0.6Mbit 428x240p.</span><span class="sxs-lookup"><span data-stu-id="160ee-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="160ee-320">Rede</span><span class="sxs-lookup"><span data-stu-id="160ee-320">Networking</span></span>

<span data-ttu-id="160ee-321">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="160ee-322">Obtém a configuração de ip atual</span><span class="sxs-lookup"><span data-stu-id="160ee-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="160ee-323">Informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="160ee-323">OS Information</span></span>

<span data-ttu-id="160ee-324">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="160ee-325">Obtém informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="160ee-325">Gets operating system information</span></span>

<span data-ttu-id="160ee-326">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="160ee-327">Obtém o nome do computador</span><span class="sxs-lookup"><span data-stu-id="160ee-327">Gets the machine name</span></span>

<span data-ttu-id="160ee-328">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="160ee-329">Define o nome do computador</span><span class="sxs-lookup"><span data-stu-id="160ee-329">Sets the machine name</span></span>

<span data-ttu-id="160ee-330">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-330">Parameters</span></span>
* <span data-ttu-id="160ee-331">nome: Novo nome de máquina, hex64 codificado, para definir como</span><span class="sxs-lookup"><span data-stu-id="160ee-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="160ee-332">Dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="160ee-332">Performance data</span></span>

<span data-ttu-id="160ee-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="160ee-334">Retorna a lista de processos em execução com detalhes</span><span class="sxs-lookup"><span data-stu-id="160ee-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="160ee-335">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-335">Return data</span></span>
* <span data-ttu-id="160ee-336">JSON com a lista de processos e os detalhes de cada processo.</span><span class="sxs-lookup"><span data-stu-id="160ee-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="160ee-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="160ee-338">Retorna estatísticas de desempenho do sistema (e/s de leitura/gravação, estatísticas de memória etc.</span><span class="sxs-lookup"><span data-stu-id="160ee-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="160ee-339">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-339">Return data</span></span>
* <span data-ttu-id="160ee-340">JSON com informações do sistema: CPU, GPU, memória, rede e e/s</span><span class="sxs-lookup"><span data-stu-id="160ee-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="160ee-341">Potência</span><span class="sxs-lookup"><span data-stu-id="160ee-341">Power</span></span>

<span data-ttu-id="160ee-342">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="160ee-343">Obtém o estado atual da bateria</span><span class="sxs-lookup"><span data-stu-id="160ee-343">Gets the current battery state</span></span>

<span data-ttu-id="160ee-344">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="160ee-345">Verifica se o sistema está em um estado de baixo consumo de energia</span><span class="sxs-lookup"><span data-stu-id="160ee-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="160ee-346">Controle Remoto</span><span class="sxs-lookup"><span data-stu-id="160ee-346">Remote Control</span></span>

<span data-ttu-id="160ee-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="160ee-348">Reinicia o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="160ee-348">Restarts the target device</span></span>

<span data-ttu-id="160ee-349">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="160ee-350">Desliga o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="160ee-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="160ee-351">Gerenciador de Tarefas</span><span class="sxs-lookup"><span data-stu-id="160ee-351">Task Manager</span></span>

<span data-ttu-id="160ee-352">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="160ee-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="160ee-353">Interrompe um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="160ee-353">Stops a modern app</span></span>

<span data-ttu-id="160ee-354">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-354">Parameters</span></span>
* <span data-ttu-id="160ee-355">pacote: Nome completo do pacote de aplicativo, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="160ee-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="160ee-356">forcestop: Forçar todos os processos para parar (= Sim)</span><span class="sxs-lookup"><span data-stu-id="160ee-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="160ee-357">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="160ee-358">Inicia um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="160ee-358">Starts a modern app</span></span>

<span data-ttu-id="160ee-359">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-359">Parameters</span></span>
* <span data-ttu-id="160ee-360">AppID: Codificação de hex64 PRAID do aplicativo para iniciar,</span><span class="sxs-lookup"><span data-stu-id="160ee-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="160ee-361">pacote: Nome completo do pacote de aplicativo, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="160ee-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="160ee-362">Gerenciamento de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="160ee-362">WiFi Management</span></span>

<span data-ttu-id="160ee-363">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="160ee-364">Enumera as interfaces de rede sem fio</span><span class="sxs-lookup"><span data-stu-id="160ee-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="160ee-365">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-365">Return data</span></span>
* <span data-ttu-id="160ee-366">Lista de interfaces sem fio com detalhes (GUID, descrição etc.)</span><span class="sxs-lookup"><span data-stu-id="160ee-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="160ee-367">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="160ee-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="160ee-368">Exclui um perfil associado a uma rede em uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="160ee-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="160ee-369">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-369">Parameters</span></span>
* <span data-ttu-id="160ee-370">interface: guid da interface de rede</span><span class="sxs-lookup"><span data-stu-id="160ee-370">interface : network interface guid</span></span>
* <span data-ttu-id="160ee-371">perfil: nome do perfil</span><span class="sxs-lookup"><span data-stu-id="160ee-371">profile : profile name</span></span>

<span data-ttu-id="160ee-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="160ee-373">Enumera as redes sem fio na interface de rede especificado</span><span class="sxs-lookup"><span data-stu-id="160ee-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="160ee-374">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-374">Parameters</span></span>
* <span data-ttu-id="160ee-375">interface: guid da interface de rede</span><span class="sxs-lookup"><span data-stu-id="160ee-375">interface : network interface guid</span></span>

<span data-ttu-id="160ee-376">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-376">Return data</span></span>
* <span data-ttu-id="160ee-377">Lista de redes sem fio encontrado na interface de rede com detalhes</span><span class="sxs-lookup"><span data-stu-id="160ee-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="160ee-378">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="160ee-379">Se conecta ou desconecta-se a uma rede na interface especificada</span><span class="sxs-lookup"><span data-stu-id="160ee-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="160ee-380">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-380">Parameters</span></span>
* <span data-ttu-id="160ee-381">interface: guid da interface de rede</span><span class="sxs-lookup"><span data-stu-id="160ee-381">interface : network interface guid</span></span>
* <span data-ttu-id="160ee-382">SSID: ssid, hex64 codificado, para se conectar a</span><span class="sxs-lookup"><span data-stu-id="160ee-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="160ee-383">op: conectar ou desconectar</span><span class="sxs-lookup"><span data-stu-id="160ee-383">op : connect or disconnect</span></span>
* <span data-ttu-id="160ee-384">CreateProfile: Sim ou não</span><span class="sxs-lookup"><span data-stu-id="160ee-384">createprofile : yes or no</span></span>
* <span data-ttu-id="160ee-385">chave: compartilhado hex64 chave, codificado</span><span class="sxs-lookup"><span data-stu-id="160ee-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="160ee-386">Gravador de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="160ee-386">Windows Performance Recorder</span></span>

<span data-ttu-id="160ee-387">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="160ee-388">Carrega um perfil do WPR e inicia o rastreamento usando o perfil carregado.</span><span class="sxs-lookup"><span data-stu-id="160ee-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="160ee-389">carga</span><span class="sxs-lookup"><span data-stu-id="160ee-389">Payload</span></span>
* <span data-ttu-id="160ee-390">corpo de http em conformidade com várias partes</span><span class="sxs-lookup"><span data-stu-id="160ee-390">multi-part conforming http body</span></span>

<span data-ttu-id="160ee-391">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-391">Return data</span></span>
* <span data-ttu-id="160ee-392">Retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="160ee-392">Returns the WPR session status.</span></span>

<span data-ttu-id="160ee-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="160ee-394">Recupera o status da sessão do WPR</span><span class="sxs-lookup"><span data-stu-id="160ee-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="160ee-395">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-395">Return data</span></span>
* <span data-ttu-id="160ee-396">Status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="160ee-396">WPR session status.</span></span>

<span data-ttu-id="160ee-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="160ee-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="160ee-398">Interrompe uma sessão de rastreamento do WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="160ee-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="160ee-399">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-399">Return data</span></span>
* <span data-ttu-id="160ee-400">Retorna o arquivo de ETL de rastreamento</span><span class="sxs-lookup"><span data-stu-id="160ee-400">Returns the trace ETL file</span></span>

<span data-ttu-id="160ee-401">**/API/WPR/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="160ee-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="160ee-402">Inicia um WPR (desempenho) sessões de rastreamento</span><span class="sxs-lookup"><span data-stu-id="160ee-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="160ee-403">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="160ee-403">Parameters</span></span>
* <span data-ttu-id="160ee-404">perfil: Nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="160ee-404">profile : Profile name.</span></span> <span data-ttu-id="160ee-405">Perfis disponíveis são armazenados em perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="160ee-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="160ee-406">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="160ee-406">Return data</span></span>
* <span data-ttu-id="160ee-407">No início, retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="160ee-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="160ee-408">Consulte também</span><span class="sxs-lookup"><span data-stu-id="160ee-408">See also</span></span>
* [<span data-ttu-id="160ee-409">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="160ee-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="160ee-410">Núcleo do Portal de dispositivo referência da API (UWP)</span><span class="sxs-lookup"><span data-stu-id="160ee-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

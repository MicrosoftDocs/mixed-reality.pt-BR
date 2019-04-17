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
# <a name="device-portal-api-reference"></a><span data-ttu-id="75fb2-104">Referência da API do portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="75fb2-104">Device portal API reference</span></span>

<span data-ttu-id="75fb2-105">Tudo na [Windows Device Portal](using-the-windows-device-portal.md) baseia-se em REST da API que você pode usar para acessar os dados e controlar seu dispositivo por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="75fb2-106">Implantação de aplicativo</span><span class="sxs-lookup"><span data-stu-id="75fb2-106">App deloyment</span></span>

<span data-ttu-id="75fb2-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="75fb2-108">Desinstala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="75fb2-108">Uninstalls an app</span></span>

<span data-ttu-id="75fb2-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-109">Parameters</span></span>
* <span data-ttu-id="75fb2-110">pacote: Nome do arquivo do pacote a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="75fb2-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="75fb2-111">**/API/App/packagemanager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="75fb2-112">Instala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="75fb2-112">Installs an App</span></span>

<span data-ttu-id="75fb2-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-113">Parameters</span></span>
* <span data-ttu-id="75fb2-114">pacote: Nome do arquivo do pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="75fb2-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="75fb2-115">carga</span><span class="sxs-lookup"><span data-stu-id="75fb2-115">Payload</span></span>
* <span data-ttu-id="75fb2-116">corpo de http em conformidade com várias partes</span><span class="sxs-lookup"><span data-stu-id="75fb2-116">multi-part conforming http body</span></span>

<span data-ttu-id="75fb2-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="75fb2-118">Recupera a lista de aplicativos instalados no sistema, com detalhes</span><span class="sxs-lookup"><span data-stu-id="75fb2-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="75fb2-119">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-119">Return data</span></span>
* <span data-ttu-id="75fb2-120">Lista de pacotes instalados com detalhes</span><span class="sxs-lookup"><span data-stu-id="75fb2-120">List of installed packages with details</span></span>

<span data-ttu-id="75fb2-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="75fb2-122">Obtém o status na instalação do aplicativo de progresso</span><span class="sxs-lookup"><span data-stu-id="75fb2-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="75fb2-123">Coleta de despejo</span><span class="sxs-lookup"><span data-stu-id="75fb2-123">Dump collection</span></span>

<span data-ttu-id="75fb2-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="75fb2-125">Desabilita a coleta de despejo para um aplicativo com sideload de falhas</span><span class="sxs-lookup"><span data-stu-id="75fb2-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="75fb2-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-126">Parameters</span></span>
* <span data-ttu-id="75fb2-127">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="75fb2-127">packageFullname : package name</span></span>

<span data-ttu-id="75fb2-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="75fb2-129">Obtém as configurações para aplicativos de sideload a coleta de despejo de memória</span><span class="sxs-lookup"><span data-stu-id="75fb2-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="75fb2-130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-130">Parameters</span></span>
* <span data-ttu-id="75fb2-131">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="75fb2-131">packageFullname : package name</span></span>

<span data-ttu-id="75fb2-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="75fb2-133">Habilita e define as configurações de controle de despejo para um aplicativo de sideload</span><span class="sxs-lookup"><span data-stu-id="75fb2-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="75fb2-134">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-134">Parameters</span></span>
* <span data-ttu-id="75fb2-135">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="75fb2-135">packageFullname : package name</span></span>

<span data-ttu-id="75fb2-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="75fb2-137">Exclui um despejo de memória para um aplicativo de sideload</span><span class="sxs-lookup"><span data-stu-id="75fb2-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="75fb2-138">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-138">Parameters</span></span>
* <span data-ttu-id="75fb2-139">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="75fb2-139">packageFullname : package name</span></span>
* <span data-ttu-id="75fb2-140">nome do arquivo: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="75fb2-140">fileName : dump file name</span></span>

<span data-ttu-id="75fb2-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="75fb2-142">Recupera um despejo de memória para um aplicativo de sideload</span><span class="sxs-lookup"><span data-stu-id="75fb2-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="75fb2-143">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-143">Parameters</span></span>
* <span data-ttu-id="75fb2-144">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="75fb2-144">packageFullname : package name</span></span>
* <span data-ttu-id="75fb2-145">nome do arquivo: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="75fb2-145">fileName : dump file name</span></span>

<span data-ttu-id="75fb2-146">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-146">Return data</span></span>
* <span data-ttu-id="75fb2-147">Arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="75fb2-147">Dump file.</span></span> <span data-ttu-id="75fb2-148">Inspecionar com o Visual Studio ou WinDbg</span><span class="sxs-lookup"><span data-stu-id="75fb2-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="75fb2-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="75fb2-150">Retorna a lista de todos os despejos de memória para aplicativos sideloaded</span><span class="sxs-lookup"><span data-stu-id="75fb2-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="75fb2-151">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-151">Return data</span></span>
* <span data-ttu-id="75fb2-152">Despejos de lista de falhas por aplicativo carregado do lado do</span><span class="sxs-lookup"><span data-stu-id="75fb2-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="75fb2-153">ETW</span><span class="sxs-lookup"><span data-stu-id="75fb2-153">ETW</span></span>

<span data-ttu-id="75fb2-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="75fb2-155">Enumera os provedores registrados</span><span class="sxs-lookup"><span data-stu-id="75fb2-155">Enumerates registered providers</span></span>

<span data-ttu-id="75fb2-156">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-156">Return data</span></span>
* <span data-ttu-id="75fb2-157">Lista de provedores, o nome amigável e o GUID</span><span class="sxs-lookup"><span data-stu-id="75fb2-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="75fb2-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="75fb2-159">Cria uma sessão ETW em tempo real; gerenciado por um websocket.</span><span class="sxs-lookup"><span data-stu-id="75fb2-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="75fb2-160">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-160">Return data</span></span>
* <span data-ttu-id="75fb2-161">Eventos ETW de provedores habilitados</span><span class="sxs-lookup"><span data-stu-id="75fb2-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="75fb2-162">Sistema operacional holográfico</span><span class="sxs-lookup"><span data-stu-id="75fb2-162">Holographic OS</span></span>

<span data-ttu-id="75fb2-163">**/API/holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="75fb2-164">Retorna uma lista de provedores ETW específicos HoloLens que não estão registrados com o sistema</span><span class="sxs-lookup"><span data-stu-id="75fb2-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="75fb2-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="75fb2-166">Retorna os estados de todos os serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="75fb2-166">Returns the states of all services running.</span></span>

<span data-ttu-id="75fb2-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="75fb2-168">Obtém o IPD armazenado (Interpupillary distância) em milímetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="75fb2-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="75fb2-170">Define o IPD</span><span class="sxs-lookup"><span data-stu-id="75fb2-170">Sets the IPD</span></span>

<span data-ttu-id="75fb2-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-171">Parameters</span></span>
* <span data-ttu-id="75fb2-172">IPD: Novo valor IPD a ser definido em milímetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="75fb2-173">**/API/holographic/os/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="75fb2-174">Obter requisitos de HTTPS para o Device Portal</span><span class="sxs-lookup"><span data-stu-id="75fb2-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="75fb2-175">**/API/holographic/os/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="75fb2-176">Define os requisitos de HTTPS para o Portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="75fb2-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="75fb2-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-177">Parameters</span></span>
* <span data-ttu-id="75fb2-178">obrigatório: Sim, não ou padrão</span><span class="sxs-lookup"><span data-stu-id="75fb2-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="75fb2-179">Percepção holográfica</span><span class="sxs-lookup"><span data-stu-id="75fb2-179">Holographic Perception</span></span>

<span data-ttu-id="75fb2-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="75fb2-181">Aceita o websocket upgrades e executa o cliente percepção que envia as atualizações em 30 fps.</span><span class="sxs-lookup"><span data-stu-id="75fb2-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="75fb2-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-182">Parameters</span></span>
* <span data-ttu-id="75fb2-183">clientmode: "ativo" força o modo de controle visual quando não puder ser estabelecida passivamente</span><span class="sxs-lookup"><span data-stu-id="75fb2-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="75fb2-184">Holográfico térmico</span><span class="sxs-lookup"><span data-stu-id="75fb2-184">Holographic Thermal</span></span>

<span data-ttu-id="75fb2-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="75fb2-186">Obter o estágio térmico do dispositivo (0 normal, 1 passiva, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="75fb2-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="75fb2-187">Controle de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="75fb2-187">Perception Simulation Control</span></span>

<span data-ttu-id="75fb2-188">**/API/holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="75fb2-189">Obter o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="75fb2-189">Get the simulation mode</span></span>

<span data-ttu-id="75fb2-190">**/API/holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="75fb2-191">Definir o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="75fb2-191">Set the simulation mode</span></span>

<span data-ttu-id="75fb2-192">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-192">Parameters</span></span>
* <span data-ttu-id="75fb2-193">modo: modo de simulação: padrão, a simulação, remoto, herdado</span><span class="sxs-lookup"><span data-stu-id="75fb2-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="75fb2-194">**/API/holographic/Simulation/Control/Stream (excluir)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="75fb2-195">Exclua um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="75fb2-195">Delete a control stream.</span></span>

<span data-ttu-id="75fb2-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="75fb2-197">Abra uma conexão de soquete da web para um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="75fb2-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="75fb2-198">**/API/holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="75fb2-199">Criar um fluxo de controle (prioridade é necessária) ou dados de postagem em um fluxo criado (o streamId é necessário).</span><span class="sxs-lookup"><span data-stu-id="75fb2-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="75fb2-200">Os dados postados deve ser do tipo ' application/octet-stream'.</span><span class="sxs-lookup"><span data-stu-id="75fb2-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="75fb2-201">Reprodução de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="75fb2-201">Perception Simulation Playback</span></span>

<span data-ttu-id="75fb2-202">**/API/holographic/Simulation/playback/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="75fb2-203">Exclua uma gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-203">Delete a recording.</span></span>

<span data-ttu-id="75fb2-204">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-204">Parameters</span></span>
* <span data-ttu-id="75fb2-205">gravação: Nome do registro para excluir.</span><span class="sxs-lookup"><span data-stu-id="75fb2-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="75fb2-206">**/API/holographic/Simulation/playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="75fb2-207">Carregue uma gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-207">Upload a recording.</span></span>

<span data-ttu-id="75fb2-208">**/API/holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="75fb2-209">Obtenha todas as gravações.</span><span class="sxs-lookup"><span data-stu-id="75fb2-209">Get all recordings.</span></span>

<span data-ttu-id="75fb2-210">**/API/holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="75fb2-211">Obter o estado atual de reprodução de uma gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="75fb2-212">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-212">Parameters</span></span>
* <span data-ttu-id="75fb2-213">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-213">recording : Name of recording.</span></span>

<span data-ttu-id="75fb2-214">**/API/holographic/Simulation/playback/Session/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="75fb2-215">Descarrega uma gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-215">Unload a recording.</span></span>

<span data-ttu-id="75fb2-216">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-216">Parameters</span></span>
* <span data-ttu-id="75fb2-217">gravação: Nome do registro para descarregar.</span><span class="sxs-lookup"><span data-stu-id="75fb2-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="75fb2-218">**/API/holographic/Simulation/playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="75fb2-219">Uma gravação de carga.</span><span class="sxs-lookup"><span data-stu-id="75fb2-219">Load a recording.</span></span>

<span data-ttu-id="75fb2-220">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-220">Parameters</span></span>
* <span data-ttu-id="75fb2-221">gravação: Nome do registro para carregar.</span><span class="sxs-lookup"><span data-stu-id="75fb2-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="75fb2-222">**/API/holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="75fb2-223">Obter todos carregadas gravações.</span><span class="sxs-lookup"><span data-stu-id="75fb2-223">Get all loaded recordings.</span></span>

<span data-ttu-id="75fb2-224">**/API/holographic/Simulation/playback/Session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="75fb2-225">Pause uma gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-225">Pause a recording.</span></span>

<span data-ttu-id="75fb2-226">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-226">Parameters</span></span>
* <span data-ttu-id="75fb2-227">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-227">recording : Name of recording.</span></span>

<span data-ttu-id="75fb2-228">**/API/holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="75fb2-229">Reproduzir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-229">Play a recording.</span></span>

<span data-ttu-id="75fb2-230">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-230">Parameters</span></span>
* <span data-ttu-id="75fb2-231">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-231">recording : Name of recording.</span></span>

<span data-ttu-id="75fb2-232">**/API/holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="75fb2-233">Pare uma gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-233">Stop a recording.</span></span>

<span data-ttu-id="75fb2-234">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-234">Parameters</span></span>
* <span data-ttu-id="75fb2-235">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-235">recording : Name of recording.</span></span>

<span data-ttu-id="75fb2-236">**/API/holographic/Simulation/playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="75fb2-237">Obtenha os tipos de dados em uma gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="75fb2-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="75fb2-238">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-238">Parameters</span></span>
* <span data-ttu-id="75fb2-239">gravação: Nome de gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="75fb2-240">Gravação de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="75fb2-240">Perception Simulation Recording</span></span>

<span data-ttu-id="75fb2-241">**/API/holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="75fb2-242">Inicie uma gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-242">Start a recording.</span></span> <span data-ttu-id="75fb2-243">Apenas uma única gravação pode estar ativa ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="75fb2-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="75fb2-244">Um cabeçalho, mãos, spatialMapping ou ambiente deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="75fb2-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="75fb2-245">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-245">Parameters</span></span>
* <span data-ttu-id="75fb2-246">cabeçalho: Definido como 1 para o registro de dados principal.</span><span class="sxs-lookup"><span data-stu-id="75fb2-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="75fb2-247">mãos: Definido como 1 para registrar dados de mão.</span><span class="sxs-lookup"><span data-stu-id="75fb2-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="75fb2-248">spatialMapping: Definido como 1 para registrar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="75fb2-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="75fb2-249">ambiente: Definido como 1 para registrar dados de ambiente.</span><span class="sxs-lookup"><span data-stu-id="75fb2-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="75fb2-250">nome: Nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="75fb2-250">name : Name of the recording.</span></span>
* <span data-ttu-id="75fb2-251">singleSpatialMappingFrame : Definido como 1 para registrar somente um quadro de mapeamento espacial único.</span><span class="sxs-lookup"><span data-stu-id="75fb2-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="75fb2-252">**/API/holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="75fb2-253">Obter gravação de estado.</span><span class="sxs-lookup"><span data-stu-id="75fb2-253">Get recording state.</span></span>

<span data-ttu-id="75fb2-254">**/API/holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="75fb2-255">Interrompa a gravação atual.</span><span class="sxs-lookup"><span data-stu-id="75fb2-255">Stop the current recording.</span></span> <span data-ttu-id="75fb2-256">Gravação será retornada como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="75fb2-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="75fb2-257">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="75fb2-257">Mixed Reality Capture</span></span>

<span data-ttu-id="75fb2-258">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="75fb2-259">Exclui uma registro do dispositivo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="75fb2-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="75fb2-260">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-260">Parameters</span></span>
* <span data-ttu-id="75fb2-261">nome do arquivo: O nome, hex64 codificado, do arquivo a ser excluído</span><span class="sxs-lookup"><span data-stu-id="75fb2-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="75fb2-262">**/API/holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="75fb2-263">Obtém o padrão realidade misturada configurações de captura</span><span class="sxs-lookup"><span data-stu-id="75fb2-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="75fb2-264">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="75fb2-265">Baixa um arquivo de realidade mista do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="75fb2-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="75fb2-266">Op uso = parâmetro de consulta do stream para streaming.</span><span class="sxs-lookup"><span data-stu-id="75fb2-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="75fb2-267">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-267">Parameters</span></span>
* <span data-ttu-id="75fb2-268">nome do arquivo: O nome, hex64 codificado, do arquivo de vídeo para obter</span><span class="sxs-lookup"><span data-stu-id="75fb2-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="75fb2-269">op : stream</span><span class="sxs-lookup"><span data-stu-id="75fb2-269">op : stream</span></span>

<span data-ttu-id="75fb2-270">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="75fb2-271">Obtém a imagem em miniatura para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="75fb2-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="75fb2-272">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-272">Parameters</span></span>
* <span data-ttu-id="75fb2-273">nome do arquivo: O nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="75fb2-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="75fb2-274">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="75fb2-275">Obtém o status da realidade misturada registrado (em execução, parado)</span><span class="sxs-lookup"><span data-stu-id="75fb2-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="75fb2-276">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="75fb2-277">Retorna a lista de arquivos de realidade misturada armazenados no dispositivo</span><span class="sxs-lookup"><span data-stu-id="75fb2-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="75fb2-278">**/API/holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="75fb2-279">Define o padrão realidade misturada configurações de captura</span><span class="sxs-lookup"><span data-stu-id="75fb2-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="75fb2-280">**/API/holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="75fb2-281">Inicia uma gravação de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="75fb2-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="75fb2-282">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-282">Parameters</span></span>
* <span data-ttu-id="75fb2-283">holo: capturar vntana: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="75fb2-284">VP: captura PV câmera: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="75fb2-285">MIC: captura microfone: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="75fb2-286">loopback: capturar o áudio do aplicativo: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="75fb2-287">**/API/holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="75fb2-288">Paradas de gravação de realidade mista do atual</span><span class="sxs-lookup"><span data-stu-id="75fb2-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="75fb2-289">**/API/holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="75fb2-290">Tira uma foto de realidade mista e cria um arquivo no dispositivo</span><span class="sxs-lookup"><span data-stu-id="75fb2-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="75fb2-291">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-291">Parameters</span></span>
* <span data-ttu-id="75fb2-292">holo: capturar vntana: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="75fb2-293">VP: captura PV câmera: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="75fb2-294">Realidade mista de Streaming</span><span class="sxs-lookup"><span data-stu-id="75fb2-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="75fb2-295">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="75fb2-296">Inicia um download em partes de um mp4 fragmentado</span><span class="sxs-lookup"><span data-stu-id="75fb2-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="75fb2-297">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-297">Parameters</span></span>
* <span data-ttu-id="75fb2-298">holo: capturar vntana: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="75fb2-299">VP: captura PV câmera: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="75fb2-300">MIC: captura microfone: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="75fb2-301">loopback: capturar o áudio do aplicativo: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="75fb2-302">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="75fb2-303">Inicia um download em partes de um mp4 fragmentado</span><span class="sxs-lookup"><span data-stu-id="75fb2-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="75fb2-304">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-304">Parameters</span></span>
* <span data-ttu-id="75fb2-305">holo: capturar vntana: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="75fb2-306">VP: captura PV câmera: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="75fb2-307">MIC: captura microfone: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="75fb2-308">loopback: capturar o áudio do aplicativo: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="75fb2-309">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="75fb2-310">Inicia um download em partes de um mp4 fragmentado</span><span class="sxs-lookup"><span data-stu-id="75fb2-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="75fb2-311">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-311">Parameters</span></span>
* <span data-ttu-id="75fb2-312">holo: capturar vntana: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="75fb2-313">VP: captura PV câmera: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="75fb2-314">MIC: captura microfone: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="75fb2-315">loopback: capturar o áudio do aplicativo: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="75fb2-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="75fb2-317">Inicia um download em partes de um mp4 fragmentado</span><span class="sxs-lookup"><span data-stu-id="75fb2-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="75fb2-318">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-318">Parameters</span></span>
* <span data-ttu-id="75fb2-319">holo: capturar vntana: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="75fb2-320">VP: captura PV câmera: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="75fb2-321">MIC: captura microfone: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="75fb2-322">loopback: capturar o áudio do aplicativo: true ou false</span><span class="sxs-lookup"><span data-stu-id="75fb2-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="75fb2-323">Rede</span><span class="sxs-lookup"><span data-stu-id="75fb2-323">Networking</span></span>

<span data-ttu-id="75fb2-324">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="75fb2-325">Obtém a configuração de ip atual</span><span class="sxs-lookup"><span data-stu-id="75fb2-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="75fb2-326">Informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="75fb2-326">OS Information</span></span>

<span data-ttu-id="75fb2-327">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="75fb2-328">Obtém informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="75fb2-328">Gets operating system information</span></span>

<span data-ttu-id="75fb2-329">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="75fb2-330">Obtém o nome do computador</span><span class="sxs-lookup"><span data-stu-id="75fb2-330">Gets the machine name</span></span>

<span data-ttu-id="75fb2-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="75fb2-332">Define o nome do computador</span><span class="sxs-lookup"><span data-stu-id="75fb2-332">Sets the machine name</span></span>

<span data-ttu-id="75fb2-333">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-333">Parameters</span></span>
* <span data-ttu-id="75fb2-334">nome: Novo nome de máquina, hex64 codificado, para definir como</span><span class="sxs-lookup"><span data-stu-id="75fb2-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="75fb2-335">Dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="75fb2-335">Performance data</span></span>

<span data-ttu-id="75fb2-336">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="75fb2-337">Retorna a lista de processos em execução com detalhes</span><span class="sxs-lookup"><span data-stu-id="75fb2-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="75fb2-338">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-338">Return data</span></span>
* <span data-ttu-id="75fb2-339">JSON com a lista de processos e os detalhes de cada processo.</span><span class="sxs-lookup"><span data-stu-id="75fb2-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="75fb2-340">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="75fb2-341">Retorna estatísticas de desempenho do sistema (e/s de leitura/gravação, estatísticas de memória etc.</span><span class="sxs-lookup"><span data-stu-id="75fb2-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="75fb2-342">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-342">Return data</span></span>
* <span data-ttu-id="75fb2-343">JSON com informações do sistema: CPU, GPU, memória, rede e e/s</span><span class="sxs-lookup"><span data-stu-id="75fb2-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="75fb2-344">Potência</span><span class="sxs-lookup"><span data-stu-id="75fb2-344">Power</span></span>

<span data-ttu-id="75fb2-345">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="75fb2-346">Obtém o estado atual da bateria</span><span class="sxs-lookup"><span data-stu-id="75fb2-346">Gets the current battery state</span></span>

<span data-ttu-id="75fb2-347">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="75fb2-348">Verifica se o sistema está em um estado de baixo consumo de energia</span><span class="sxs-lookup"><span data-stu-id="75fb2-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="75fb2-349">Controle Remoto</span><span class="sxs-lookup"><span data-stu-id="75fb2-349">Remote Control</span></span>

<span data-ttu-id="75fb2-350">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="75fb2-351">Reinicia o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="75fb2-351">Restarts the target device</span></span>

<span data-ttu-id="75fb2-352">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="75fb2-353">Desliga o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="75fb2-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="75fb2-354">Gerenciador de Tarefas</span><span class="sxs-lookup"><span data-stu-id="75fb2-354">Task Manager</span></span>

<span data-ttu-id="75fb2-355">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="75fb2-356">Interrompe um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="75fb2-356">Stops a modern app</span></span>

<span data-ttu-id="75fb2-357">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-357">Parameters</span></span>
* <span data-ttu-id="75fb2-358">pacote: Nome completo do pacote de aplicativo, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="75fb2-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="75fb2-359">forcestop: Forçar todos os processos para parar (= Sim)</span><span class="sxs-lookup"><span data-stu-id="75fb2-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="75fb2-360">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="75fb2-361">Inicia um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="75fb2-361">Starts a modern app</span></span>

<span data-ttu-id="75fb2-362">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-362">Parameters</span></span>
* <span data-ttu-id="75fb2-363">AppID: Codificação de hex64 PRAID do aplicativo para iniciar,</span><span class="sxs-lookup"><span data-stu-id="75fb2-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="75fb2-364">pacote: Nome completo do pacote de aplicativo, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="75fb2-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="75fb2-365">Gerenciamento de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="75fb2-365">WiFi Management</span></span>

<span data-ttu-id="75fb2-366">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="75fb2-367">Enumera as interfaces de rede sem fio</span><span class="sxs-lookup"><span data-stu-id="75fb2-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="75fb2-368">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-368">Return data</span></span>
* <span data-ttu-id="75fb2-369">Lista de interfaces sem fio com detalhes (GUID, descrição etc.)</span><span class="sxs-lookup"><span data-stu-id="75fb2-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="75fb2-370">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="75fb2-371">Exclui um perfil associado a uma rede em uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="75fb2-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="75fb2-372">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-372">Parameters</span></span>
* <span data-ttu-id="75fb2-373">interface: guid da interface de rede</span><span class="sxs-lookup"><span data-stu-id="75fb2-373">interface : network interface guid</span></span>
* <span data-ttu-id="75fb2-374">perfil: nome do perfil</span><span class="sxs-lookup"><span data-stu-id="75fb2-374">profile : profile name</span></span>

<span data-ttu-id="75fb2-375">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="75fb2-376">Enumera as redes sem fio na interface de rede especificado</span><span class="sxs-lookup"><span data-stu-id="75fb2-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="75fb2-377">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-377">Parameters</span></span>
* <span data-ttu-id="75fb2-378">interface: guid da interface de rede</span><span class="sxs-lookup"><span data-stu-id="75fb2-378">interface : network interface guid</span></span>

<span data-ttu-id="75fb2-379">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-379">Return data</span></span>
* <span data-ttu-id="75fb2-380">Lista de redes sem fio encontrado na interface de rede com detalhes</span><span class="sxs-lookup"><span data-stu-id="75fb2-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="75fb2-381">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="75fb2-382">Se conecta ou desconecta-se a uma rede na interface especificada</span><span class="sxs-lookup"><span data-stu-id="75fb2-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="75fb2-383">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-383">Parameters</span></span>
* <span data-ttu-id="75fb2-384">interface: guid da interface de rede</span><span class="sxs-lookup"><span data-stu-id="75fb2-384">interface : network interface guid</span></span>
* <span data-ttu-id="75fb2-385">SSID: ssid, hex64 codificado, para se conectar a</span><span class="sxs-lookup"><span data-stu-id="75fb2-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="75fb2-386">op: conectar ou desconectar</span><span class="sxs-lookup"><span data-stu-id="75fb2-386">op : connect or disconnect</span></span>
* <span data-ttu-id="75fb2-387">CreateProfile: Sim ou não</span><span class="sxs-lookup"><span data-stu-id="75fb2-387">createprofile : yes or no</span></span>
* <span data-ttu-id="75fb2-388">chave: compartilhado hex64 chave, codificado</span><span class="sxs-lookup"><span data-stu-id="75fb2-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="75fb2-389">Gravador de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="75fb2-389">Windows Performance Recorder</span></span>

<span data-ttu-id="75fb2-390">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="75fb2-391">Carrega um perfil do WPR e inicia o rastreamento usando o perfil carregado.</span><span class="sxs-lookup"><span data-stu-id="75fb2-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="75fb2-392">carga</span><span class="sxs-lookup"><span data-stu-id="75fb2-392">Payload</span></span>
* <span data-ttu-id="75fb2-393">corpo de http em conformidade com várias partes</span><span class="sxs-lookup"><span data-stu-id="75fb2-393">multi-part conforming http body</span></span>

<span data-ttu-id="75fb2-394">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-394">Return data</span></span>
* <span data-ttu-id="75fb2-395">Retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="75fb2-395">Returns the WPR session status.</span></span>

<span data-ttu-id="75fb2-396">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="75fb2-397">Recupera o status da sessão do WPR</span><span class="sxs-lookup"><span data-stu-id="75fb2-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="75fb2-398">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-398">Return data</span></span>
* <span data-ttu-id="75fb2-399">Status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="75fb2-399">WPR session status.</span></span>

<span data-ttu-id="75fb2-400">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="75fb2-401">Interrompe uma sessão de rastreamento do WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="75fb2-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="75fb2-402">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-402">Return data</span></span>
* <span data-ttu-id="75fb2-403">Retorna o arquivo de ETL de rastreamento</span><span class="sxs-lookup"><span data-stu-id="75fb2-403">Returns the trace ETL file</span></span>

<span data-ttu-id="75fb2-404">**/API/WPR/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="75fb2-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="75fb2-405">Inicia um WPR (desempenho) sessões de rastreamento</span><span class="sxs-lookup"><span data-stu-id="75fb2-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="75fb2-406">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75fb2-406">Parameters</span></span>
* <span data-ttu-id="75fb2-407">perfil: Nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="75fb2-407">profile : Profile name.</span></span> <span data-ttu-id="75fb2-408">Perfis disponíveis são armazenados em perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="75fb2-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="75fb2-409">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="75fb2-409">Return data</span></span>
* <span data-ttu-id="75fb2-410">No início, retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="75fb2-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="75fb2-411">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75fb2-411">See also</span></span>
* [<span data-ttu-id="75fb2-412">Usando o Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="75fb2-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="75fb2-413">Núcleo do Portal de dispositivo referência da API (UWP)</span><span class="sxs-lookup"><span data-stu-id="75fb2-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

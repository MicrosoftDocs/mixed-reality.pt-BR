---
title: Referência de API do portal de dispositivos
description: Referência de API para o portal de dispositivo do Windows no HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portal de dispositivos Windows, API
ms.openlocfilehash: b9b9ada49b4f9810dc97c9da2873d4ccb60df424
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441793"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="c73d0-104">Referência de API do portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="c73d0-104">Device portal API reference</span></span>

<span data-ttu-id="c73d0-105">Tudo no [portal de dispositivos do Windows](using-the-windows-device-portal.md) é criado sobre as APIs REST que você pode usar para acessar os dados e controlar seu dispositivo de forma programática.</span><span class="sxs-lookup"><span data-stu-id="c73d0-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="c73d0-106">Implantação do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c73d0-106">App deloyment</span></span>

<span data-ttu-id="c73d0-107">**/API/app/PackageManager/Package (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="c73d0-108">Desinstala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="c73d0-108">Uninstalls an app</span></span>

<span data-ttu-id="c73d0-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-109">Parameters</span></span>
* <span data-ttu-id="c73d0-110">Package: nome de arquivo do pacote a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="c73d0-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="c73d0-111">**/API/app/PackageManager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="c73d0-112">Instala um aplicativo</span><span class="sxs-lookup"><span data-stu-id="c73d0-112">Installs an App</span></span>

<span data-ttu-id="c73d0-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-113">Parameters</span></span>
* <span data-ttu-id="c73d0-114">Package: nome do arquivo do pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="c73d0-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="c73d0-115">Carga útil</span><span class="sxs-lookup"><span data-stu-id="c73d0-115">Payload</span></span>
* <span data-ttu-id="c73d0-116">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="c73d0-116">multi-part conforming http body</span></span>

<span data-ttu-id="c73d0-117">**/API/app/PackageManager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="c73d0-118">Recupera a lista de aplicativos instalados no sistema, com detalhes</span><span class="sxs-lookup"><span data-stu-id="c73d0-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="c73d0-119">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-119">Return data</span></span>
* <span data-ttu-id="c73d0-120">Lista de pacotes instalados com detalhes</span><span class="sxs-lookup"><span data-stu-id="c73d0-120">List of installed packages with details</span></span>

<span data-ttu-id="c73d0-121">**/API/app/PackageManager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="c73d0-122">Obtém o status da instalação do aplicativo em andamento</span><span class="sxs-lookup"><span data-stu-id="c73d0-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="c73d0-123">Despejar coleção</span><span class="sxs-lookup"><span data-stu-id="c73d0-123">Dump collection</span></span>

<span data-ttu-id="c73d0-124">**/API/Debug/dump/UserMode/crashcontrol (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="c73d0-125">Desabilita a coleta de despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="c73d0-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="c73d0-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-126">Parameters</span></span>
* <span data-ttu-id="c73d0-127">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c73d0-127">packageFullname : package name</span></span>

<span data-ttu-id="c73d0-128">**/API/Debug/dump/UserMode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="c73d0-129">Obtém as configurações para coleta de despejo de memória de aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="c73d0-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="c73d0-130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-130">Parameters</span></span>
* <span data-ttu-id="c73d0-131">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c73d0-131">packageFullname : package name</span></span>

<span data-ttu-id="c73d0-132">**/API/Debug/dump/UserMode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="c73d0-133">Habilita e define as configurações de controle de despejo para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="c73d0-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="c73d0-134">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-134">Parameters</span></span>
* <span data-ttu-id="c73d0-135">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c73d0-135">packageFullname : package name</span></span>

<span data-ttu-id="c73d0-136">**/API/Debug/dump/UserMode/crashdump (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="c73d0-137">Exclui um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="c73d0-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c73d0-138">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-138">Parameters</span></span>
* <span data-ttu-id="c73d0-139">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c73d0-139">packageFullname : package name</span></span>
* <span data-ttu-id="c73d0-140">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="c73d0-140">fileName : dump file name</span></span>

<span data-ttu-id="c73d0-141">**/API/Debug/dump/UserMode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="c73d0-142">Recupera um despejo de memória para um aplicativo Sideload</span><span class="sxs-lookup"><span data-stu-id="c73d0-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c73d0-143">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-143">Parameters</span></span>
* <span data-ttu-id="c73d0-144">packageFullname: nome do pacote</span><span class="sxs-lookup"><span data-stu-id="c73d0-144">packageFullname : package name</span></span>
* <span data-ttu-id="c73d0-145">fileName: nome do arquivo de despejo</span><span class="sxs-lookup"><span data-stu-id="c73d0-145">fileName : dump file name</span></span>

<span data-ttu-id="c73d0-146">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-146">Return data</span></span>
* <span data-ttu-id="c73d0-147">Arquivo de despejo.</span><span class="sxs-lookup"><span data-stu-id="c73d0-147">Dump file.</span></span> <span data-ttu-id="c73d0-148">Inspecione com o WinDbg ou o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c73d0-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="c73d0-149">**/API/Debug/dump/UserMode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="c73d0-150">Retorna a lista de todos os despejos de memória para aplicativos Sideload</span><span class="sxs-lookup"><span data-stu-id="c73d0-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="c73d0-151">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-151">Return data</span></span>
* <span data-ttu-id="c73d0-152">Lista de despejos de memória por aplicativo carregado por lado</span><span class="sxs-lookup"><span data-stu-id="c73d0-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="c73d0-153">ETW</span><span class="sxs-lookup"><span data-stu-id="c73d0-153">ETW</span></span>

<span data-ttu-id="c73d0-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="c73d0-155">Enumera provedores registrados</span><span class="sxs-lookup"><span data-stu-id="c73d0-155">Enumerates registered providers</span></span>

<span data-ttu-id="c73d0-156">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-156">Return data</span></span>
* <span data-ttu-id="c73d0-157">Lista de provedores, nome amigável e GUID</span><span class="sxs-lookup"><span data-stu-id="c73d0-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="c73d0-158">**/API/ETW/Session/Realtime (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="c73d0-159">Cria uma sessão de ETW em tempo real; gerenciado em um WebSocket.</span><span class="sxs-lookup"><span data-stu-id="c73d0-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="c73d0-160">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-160">Return data</span></span>
* <span data-ttu-id="c73d0-161">Eventos ETW dos provedores habilitados</span><span class="sxs-lookup"><span data-stu-id="c73d0-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="c73d0-162">Sistema operacional holográfico</span><span class="sxs-lookup"><span data-stu-id="c73d0-162">Holographic OS</span></span>

<span data-ttu-id="c73d0-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="c73d0-164">Retorna uma lista de provedores de ETW específicos do HoloLens que não estão registrados no sistema</span><span class="sxs-lookup"><span data-stu-id="c73d0-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="c73d0-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="c73d0-166">Retorna os Estados de todos os serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="c73d0-166">Returns the states of all services running.</span></span>

<span data-ttu-id="c73d0-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="c73d0-168">Obtém o IPD armazenado (distância interpupillary) em milímetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="c73d0-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="c73d0-170">Define o IPD</span><span class="sxs-lookup"><span data-stu-id="c73d0-170">Sets the IPD</span></span>

<span data-ttu-id="c73d0-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-171">Parameters</span></span>
* <span data-ttu-id="c73d0-172">IPD: novo valor de IPD a ser definido em milímetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="c73d0-173">**/API/Holographic/os/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="c73d0-174">Obter requisitos de HTTPS para o Device Portal</span><span class="sxs-lookup"><span data-stu-id="c73d0-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c73d0-175">**/API/Holographic/os/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="c73d0-176">Define os requisitos de HTTPS para o portal do dispositivo</span><span class="sxs-lookup"><span data-stu-id="c73d0-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c73d0-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-177">Parameters</span></span>
* <span data-ttu-id="c73d0-178">obrigatório: Sim, não ou padrão</span><span class="sxs-lookup"><span data-stu-id="c73d0-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="c73d0-179">Percepção de Holographic</span><span class="sxs-lookup"><span data-stu-id="c73d0-179">Holographic Perception</span></span>

<span data-ttu-id="c73d0-180">**/API/Holographic/Perception/Client (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="c73d0-181">Aceita atualizações do WebSocket e executa um cliente de percepção que envia atualizações a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="c73d0-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="c73d0-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-182">Parameters</span></span>
* <span data-ttu-id="c73d0-183">clientmode: "ativo" força o modo de controle visual quando ele não pode ser estabelecido passivamente</span><span class="sxs-lookup"><span data-stu-id="c73d0-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="c73d0-184">Holographic térmico</span><span class="sxs-lookup"><span data-stu-id="c73d0-184">Holographic Thermal</span></span>

<span data-ttu-id="c73d0-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="c73d0-186">Obter o estágio térmico do dispositivo (0 normal, 1 quente, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="c73d0-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="c73d0-187">Controle de simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="c73d0-187">Perception Simulation Control</span></span>

<span data-ttu-id="c73d0-188">**/API/Holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="c73d0-189">Obter o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="c73d0-189">Get the simulation mode</span></span>

<span data-ttu-id="c73d0-190">**/API/Holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="c73d0-191">Definir o modo de simulação</span><span class="sxs-lookup"><span data-stu-id="c73d0-191">Set the simulation mode</span></span>

<span data-ttu-id="c73d0-192">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-192">Parameters</span></span>
* <span data-ttu-id="c73d0-193">modo: modo de simulação: padrão, simulação, remoto, herdado</span><span class="sxs-lookup"><span data-stu-id="c73d0-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="c73d0-194">**/API/Holographic/Simulation/Control/Stream (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="c73d0-195">Excluir um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="c73d0-195">Delete a control stream.</span></span>

<span data-ttu-id="c73d0-196">**/API/Holographic/Simulation/Control/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="c73d0-197">Abra uma conexão de soquete da Web para um fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="c73d0-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="c73d0-198">**/API/Holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="c73d0-199">Crie um fluxo de controle (prioridade necessária) ou poste dados em um fluxo criado (streamid necessário).</span><span class="sxs-lookup"><span data-stu-id="c73d0-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="c73d0-200">Espera-se que os dados postados sejam do tipo ' application/octet-stream '.</span><span class="sxs-lookup"><span data-stu-id="c73d0-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="c73d0-201">**/API/Holographic/Simulation/display/Stream (obter/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="c73d0-202">Solicite um fluxo de vídeo de simulação contendo o conteúdo renderizado para a exibição do sistema quando estiver no modo ' Simulation '.</span><span class="sxs-lookup"><span data-stu-id="c73d0-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="c73d0-203">Um cabeçalho de descritor de formato simples será enviado inicialmente, seguido de texturas codificadas H. 264, cada um precedido por um cabeçalho que indica o índice de olho e o tamanho da textura.</span><span class="sxs-lookup"><span data-stu-id="c73d0-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="c73d0-204">Reprodução da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="c73d0-204">Perception Simulation Playback</span></span>

<span data-ttu-id="c73d0-205">**/API/Holographic/Simulation/playback/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="c73d0-206">Excluir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-206">Delete a recording.</span></span>

<span data-ttu-id="c73d0-207">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-207">Parameters</span></span>
* <span data-ttu-id="c73d0-208">gravação: o nome da gravação a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="c73d0-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="c73d0-209">**/API/Holographic/Simulation/playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="c73d0-210">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-210">Upload a recording.</span></span>

<span data-ttu-id="c73d0-211">**/API/Holographic/Simulation/playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="c73d0-212">Obter todas as gravações.</span><span class="sxs-lookup"><span data-stu-id="c73d0-212">Get all recordings.</span></span>

<span data-ttu-id="c73d0-213">**/API/Holographic/Simulation/playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="c73d0-214">Obter o estado de reprodução atual de uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="c73d0-215">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-215">Parameters</span></span>
* <span data-ttu-id="c73d0-216">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-216">recording : Name of recording.</span></span>

<span data-ttu-id="c73d0-217">**/API/Holographic/Simulation/playback/Session/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="c73d0-218">Descarregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-218">Unload a recording.</span></span>

<span data-ttu-id="c73d0-219">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-219">Parameters</span></span>
* <span data-ttu-id="c73d0-220">gravação: nome da gravação a ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="c73d0-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="c73d0-221">**/API/Holographic/Simulation/playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="c73d0-222">Carregar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-222">Load a recording.</span></span>

<span data-ttu-id="c73d0-223">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-223">Parameters</span></span>
* <span data-ttu-id="c73d0-224">gravação: o nome da gravação a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="c73d0-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="c73d0-225">**/API/Holographic/Simulation/playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="c73d0-226">Obter todas as gravações carregadas.</span><span class="sxs-lookup"><span data-stu-id="c73d0-226">Get all loaded recordings.</span></span>

<span data-ttu-id="c73d0-227">**/API/Holographic/Simulation/playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="c73d0-228">Pausar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-228">Pause a recording.</span></span>

<span data-ttu-id="c73d0-229">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-229">Parameters</span></span>
* <span data-ttu-id="c73d0-230">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-230">recording : Name of recording.</span></span>

<span data-ttu-id="c73d0-231">**/API/Holographic/Simulation/playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="c73d0-232">Reproduzir uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-232">Play a recording.</span></span>

<span data-ttu-id="c73d0-233">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-233">Parameters</span></span>
* <span data-ttu-id="c73d0-234">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-234">recording : Name of recording.</span></span>

<span data-ttu-id="c73d0-235">**/API/Holographic/Simulation/playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="c73d0-236">Parar uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-236">Stop a recording.</span></span>

<span data-ttu-id="c73d0-237">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-237">Parameters</span></span>
* <span data-ttu-id="c73d0-238">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-238">recording : Name of recording.</span></span>

<span data-ttu-id="c73d0-239">**/API/Holographic/Simulation/playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="c73d0-240">Obter os tipos de dados em uma gravação carregada.</span><span class="sxs-lookup"><span data-stu-id="c73d0-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="c73d0-241">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-241">Parameters</span></span>
* <span data-ttu-id="c73d0-242">gravação: nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="c73d0-243">Gravação da simulação de percepção</span><span class="sxs-lookup"><span data-stu-id="c73d0-243">Perception Simulation Recording</span></span>

<span data-ttu-id="c73d0-244">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="c73d0-245">Inicie uma gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-245">Start a recording.</span></span> <span data-ttu-id="c73d0-246">Apenas uma única gravação pode estar ativa de uma vez.</span><span class="sxs-lookup"><span data-stu-id="c73d0-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="c73d0-247">É necessário definir um dos cabeçalhos, as mãos, spatialMapping ou ambiente.</span><span class="sxs-lookup"><span data-stu-id="c73d0-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="c73d0-248">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-248">Parameters</span></span>
* <span data-ttu-id="c73d0-249">Cabeçalho: Defina como 1 para registrar dados de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="c73d0-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="c73d0-250">Hands: Defina como 1 para gravar dados de mão.</span><span class="sxs-lookup"><span data-stu-id="c73d0-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="c73d0-251">spatialMapping: Defina como 1 para registrar o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="c73d0-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="c73d0-252">ambiente: Defina como 1 para gravar dados do ambiente.</span><span class="sxs-lookup"><span data-stu-id="c73d0-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="c73d0-253">Nome: o nome da gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-253">name : Name of the recording.</span></span>
* <span data-ttu-id="c73d0-254">singleSpatialMappingFrame: Defina como 1 para gravar apenas um único quadro de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="c73d0-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="c73d0-255">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="c73d0-256">Obter estado de gravação.</span><span class="sxs-lookup"><span data-stu-id="c73d0-256">Get recording state.</span></span>

<span data-ttu-id="c73d0-257">**/API/Holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="c73d0-258">Parar a gravação atual.</span><span class="sxs-lookup"><span data-stu-id="c73d0-258">Stop the current recording.</span></span> <span data-ttu-id="c73d0-259">A gravação será retornada como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c73d0-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="c73d0-260">Mixed Reality Capture</span><span class="sxs-lookup"><span data-stu-id="c73d0-260">Mixed Reality Capture</span></span>

<span data-ttu-id="c73d0-261">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="c73d0-262">Baixa um arquivo de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c73d0-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="c73d0-263">Use op = Stream Query parâmetro para streaming.</span><span class="sxs-lookup"><span data-stu-id="c73d0-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="c73d0-264">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-264">Parameters</span></span>
* <span data-ttu-id="c73d0-265">filename: nome, hex64 codificado, do arquivo de vídeo a ser obtido</span><span class="sxs-lookup"><span data-stu-id="c73d0-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="c73d0-266">op: fluxo</span><span class="sxs-lookup"><span data-stu-id="c73d0-266">op : stream</span></span>

<span data-ttu-id="c73d0-267">**/API/Holographic/MRC/File (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="c73d0-268">Exclui uma gravação de realidade misturada do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c73d0-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="c73d0-269">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-269">Parameters</span></span>
* <span data-ttu-id="c73d0-270">filename: nome, hex64 codificado, do arquivo a ser excluído</span><span class="sxs-lookup"><span data-stu-id="c73d0-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="c73d0-271">**/API/Holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="c73d0-272">Retorna a lista de arquivos de realidade misturada armazenados no dispositivo</span><span class="sxs-lookup"><span data-stu-id="c73d0-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="c73d0-273">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="c73d0-274">Usa uma foto de realidade misturada e cria um arquivo no dispositivo</span><span class="sxs-lookup"><span data-stu-id="c73d0-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="c73d0-275">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-275">Parameters</span></span>
* <span data-ttu-id="c73d0-276">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c73d0-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="c73d0-277">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c73d0-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="c73d0-278">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="c73d0-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="c73d0-279">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="c73d0-280">Obtém as configurações padrão da captura de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c73d0-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="c73d0-281">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="c73d0-282">Define as configurações padrão de captura de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c73d0-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="c73d0-283">Algumas dessas configurações são aplicadas à captura de vídeo e foto da MRC do sistema.</span><span class="sxs-lookup"><span data-stu-id="c73d0-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="c73d0-284">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="c73d0-285">Obtém o estado da captura de realidade misturada no portal do dispositivo Windows.</span><span class="sxs-lookup"><span data-stu-id="c73d0-285">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="c73d0-286">***Resposta***</span><span class="sxs-lookup"><span data-stu-id="c73d0-286">***Response***</span></span>

<span data-ttu-id="c73d0-287">A resposta contém uma propriedade JSON que indica se o portal do dispositivo Windows está gravando vídeo ou não.</span><span class="sxs-lookup"><span data-stu-id="c73d0-287">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="c73d0-288">**/API/Holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-288">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="c73d0-289">Obtém a imagem em miniatura do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="c73d0-289">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="c73d0-290">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-290">Parameters</span></span>
* <span data-ttu-id="c73d0-291">filename: nome, hex64 codificado, do arquivo para o qual a miniatura está sendo solicitada</span><span class="sxs-lookup"><span data-stu-id="c73d0-291">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="c73d0-292">**/API/Holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-292">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="c73d0-293">Inicia uma gravação de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c73d0-293">Starts a mixed reality recording</span></span>

<span data-ttu-id="c73d0-294">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-294">Parameters</span></span>
* <span data-ttu-id="c73d0-295">holo: capturar hologramas: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c73d0-295">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="c73d0-296">PV: capturar câmera PV: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c73d0-296">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="c73d0-297">MIC: capturar microfone: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c73d0-297">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="c73d0-298">loopback: capturar o áudio do aplicativo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c73d0-298">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="c73d0-299">RenderFromCamera: (somente HoloLens 2) render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="c73d0-299">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="c73d0-300">Vstab: (somente HoloLens 2) habilitar estabilização de vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="c73d0-300">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="c73d0-301">vstabbuffer: (somente HoloLens 2) latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="c73d0-301">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="c73d0-302">**/API/Holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-302">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="c73d0-303">Interrompe a gravação atual da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c73d0-303">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="c73d0-304">Streaming de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c73d0-304">Mixed Reality Streaming</span></span>

<span data-ttu-id="c73d0-305">O HoloLens dá suporte à visualização dinâmica de realidade misturada por meio do download em partes de um MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="c73d0-305">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="c73d0-306">Fluxos de realidade misturada compartilham o mesmo conjunto de parâmetros para controlar o que é capturado:</span><span class="sxs-lookup"><span data-stu-id="c73d0-306">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="c73d0-307">holo: capturar hologramas: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="c73d0-307">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c73d0-308">PV: capturar câmera PV: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="c73d0-308">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c73d0-309">MIC: capturar microfone: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="c73d0-309">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c73d0-310">loopback: capturar áudio do aplicativo: verdadeiro ou falso</span><span class="sxs-lookup"><span data-stu-id="c73d0-310">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="c73d0-311">Se nenhum deles for especificado: os hologramas, a câmera de foto/vídeo e o áudio do aplicativo serão capturados</span><span class="sxs-lookup"><span data-stu-id="c73d0-311">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="c73d0-312">Se houver algum especificado: os parâmetros não especificados serão padronizados como false</span><span class="sxs-lookup"><span data-stu-id="c73d0-312">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="c73d0-313">Parâmetros opcionais (somente HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="c73d0-313">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="c73d0-314">RenderFromCamera: Render da perspectiva da câmera de foto/vídeo: true ou false (o padrão é true)</span><span class="sxs-lookup"><span data-stu-id="c73d0-314">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="c73d0-315">Vstab: habilitar estabilização de vídeo: true ou false (o padrão é false)</span><span class="sxs-lookup"><span data-stu-id="c73d0-315">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="c73d0-316">vstabbuffer: latência de buffer de estabilização de vídeo: 0 a 30 quadros (o padrão é 15 quadros)</span><span class="sxs-lookup"><span data-stu-id="c73d0-316">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="c73d0-317">**/API/Holographic/Stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-317">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="c73d0-318">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="c73d0-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="c73d0-319">**/API/Holographic/Stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-319">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="c73d0-320">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="c73d0-320">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="c73d0-321">**/API/Holographic/Stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-321">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="c73d0-322">Um fluxo 854x480p 30fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="c73d0-322">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="c73d0-323">**/API/Holographic/Stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-323">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="c73d0-324">Um fluxo 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="c73d0-324">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="c73d0-325">Rede</span><span class="sxs-lookup"><span data-stu-id="c73d0-325">Networking</span></span>

<span data-ttu-id="c73d0-326">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-326">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="c73d0-327">Obter a configuração de IP atual</span><span class="sxs-lookup"><span data-stu-id="c73d0-327">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="c73d0-328">Informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="c73d0-328">OS Information</span></span>

<span data-ttu-id="c73d0-329">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-329">**/api/os/info (GET)**</span></span>

<span data-ttu-id="c73d0-330">Obtém informações do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="c73d0-330">Gets operating system information</span></span>

<span data-ttu-id="c73d0-331">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-331">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="c73d0-332">Obtém o nome do computador</span><span class="sxs-lookup"><span data-stu-id="c73d0-332">Gets the machine name</span></span>

<span data-ttu-id="c73d0-333">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-333">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="c73d0-334">Define o nome do computador</span><span class="sxs-lookup"><span data-stu-id="c73d0-334">Sets the machine name</span></span>

<span data-ttu-id="c73d0-335">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-335">Parameters</span></span>
* <span data-ttu-id="c73d0-336">Nome: novo nome do computador, hex64 codificado, para definir como</span><span class="sxs-lookup"><span data-stu-id="c73d0-336">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="c73d0-337">Dados de desempenho</span><span class="sxs-lookup"><span data-stu-id="c73d0-337">Performance data</span></span>

<span data-ttu-id="c73d0-338">**/API/ResourceManager/Processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-338">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="c73d0-339">Retorna a lista de processos em execução com detalhes</span><span class="sxs-lookup"><span data-stu-id="c73d0-339">Returns the list of running processes with details</span></span>

<span data-ttu-id="c73d0-340">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-340">Return data</span></span>
* <span data-ttu-id="c73d0-341">JSON com lista de processos e detalhes para cada processo</span><span class="sxs-lookup"><span data-stu-id="c73d0-341">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="c73d0-342">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-342">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="c73d0-343">Retorna estatísticas de desempenho do sistema (leitura/gravação de e/s, estatísticas de memória etc.)</span><span class="sxs-lookup"><span data-stu-id="c73d0-343">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="c73d0-344">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-344">Return data</span></span>
* <span data-ttu-id="c73d0-345">JSON com informações do sistema: CPU, GPU, memória, rede, e/s</span><span class="sxs-lookup"><span data-stu-id="c73d0-345">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="c73d0-346">Energia</span><span class="sxs-lookup"><span data-stu-id="c73d0-346">Power</span></span>

<span data-ttu-id="c73d0-347">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-347">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="c73d0-348">Obtém o estado da bateria atual</span><span class="sxs-lookup"><span data-stu-id="c73d0-348">Gets the current battery state</span></span>

<span data-ttu-id="c73d0-349">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-349">**/api/power/state (GET)**</span></span>

<span data-ttu-id="c73d0-350">Verifica se o sistema está em um estado de baixa energia</span><span class="sxs-lookup"><span data-stu-id="c73d0-350">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="c73d0-351">Controle remoto</span><span class="sxs-lookup"><span data-stu-id="c73d0-351">Remote Control</span></span>

<span data-ttu-id="c73d0-352">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-352">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="c73d0-353">Reinicia o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="c73d0-353">Restarts the target device</span></span>

<span data-ttu-id="c73d0-354">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-354">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="c73d0-355">Desliga o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="c73d0-355">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="c73d0-356">Gerenciador de Tarefas</span><span class="sxs-lookup"><span data-stu-id="c73d0-356">Task Manager</span></span>

<span data-ttu-id="c73d0-357">**/API/taskmanager/app (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-357">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="c73d0-358">Para um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="c73d0-358">Stops a modern app</span></span>

<span data-ttu-id="c73d0-359">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-359">Parameters</span></span>
* <span data-ttu-id="c73d0-360">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="c73d0-360">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="c73d0-361">forcestop: forçar a interrupção de todos os processos (= Sim)</span><span class="sxs-lookup"><span data-stu-id="c73d0-361">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="c73d0-362">**/API/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-362">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="c73d0-363">Inicia um aplicativo moderno</span><span class="sxs-lookup"><span data-stu-id="c73d0-363">Starts a modern app</span></span>

<span data-ttu-id="c73d0-364">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-364">Parameters</span></span>
* <span data-ttu-id="c73d0-365">AppID: PRAID do aplicativo a ser iniciado, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="c73d0-365">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="c73d0-366">pacote: nome completo do pacote do aplicativo, codificado hex64</span><span class="sxs-lookup"><span data-stu-id="c73d0-366">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="c73d0-367">Gerenciamento de WiFi</span><span class="sxs-lookup"><span data-stu-id="c73d0-367">WiFi Management</span></span>

<span data-ttu-id="c73d0-368">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-368">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="c73d0-369">Enumera interfaces de rede sem fio</span><span class="sxs-lookup"><span data-stu-id="c73d0-369">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="c73d0-370">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-370">Return data</span></span>
* <span data-ttu-id="c73d0-371">Lista de interfaces sem fio com detalhes (GUID, descrição, etc.)</span><span class="sxs-lookup"><span data-stu-id="c73d0-371">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="c73d0-372">**/API/WiFi/Network (excluir)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-372">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="c73d0-373">Exclui um perfil associado a uma rede em uma interface especificada</span><span class="sxs-lookup"><span data-stu-id="c73d0-373">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="c73d0-374">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-374">Parameters</span></span>
* <span data-ttu-id="c73d0-375">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="c73d0-375">interface : network interface guid</span></span>
* <span data-ttu-id="c73d0-376">Perfil: nome do perfil</span><span class="sxs-lookup"><span data-stu-id="c73d0-376">profile : profile name</span></span>

<span data-ttu-id="c73d0-377">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-377">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="c73d0-378">Enumera redes sem fio na interface de rede especificada</span><span class="sxs-lookup"><span data-stu-id="c73d0-378">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="c73d0-379">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-379">Parameters</span></span>
* <span data-ttu-id="c73d0-380">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="c73d0-380">interface : network interface guid</span></span>

<span data-ttu-id="c73d0-381">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-381">Return data</span></span>
* <span data-ttu-id="c73d0-382">Lista de redes sem fio encontradas na interface de rede com detalhes</span><span class="sxs-lookup"><span data-stu-id="c73d0-382">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="c73d0-383">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-383">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="c73d0-384">Conecta ou desconecta-se a uma rede na interface especificada</span><span class="sxs-lookup"><span data-stu-id="c73d0-384">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="c73d0-385">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-385">Parameters</span></span>
* <span data-ttu-id="c73d0-386">interface: GUID de interface de rede</span><span class="sxs-lookup"><span data-stu-id="c73d0-386">interface : network interface guid</span></span>
* <span data-ttu-id="c73d0-387">SSID: SSID, hex64 codificado, para se conectar ao</span><span class="sxs-lookup"><span data-stu-id="c73d0-387">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="c73d0-388">op: conectar ou desconectar</span><span class="sxs-lookup"><span data-stu-id="c73d0-388">op : connect or disconnect</span></span>
* <span data-ttu-id="c73d0-389">CreateProfile: Sim ou não</span><span class="sxs-lookup"><span data-stu-id="c73d0-389">createprofile : yes or no</span></span>
* <span data-ttu-id="c73d0-390">chave: chave compartilhada, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="c73d0-390">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="c73d0-391">Gravador de desempenho do Windows</span><span class="sxs-lookup"><span data-stu-id="c73d0-391">Windows Performance Recorder</span></span>

<span data-ttu-id="c73d0-392">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-392">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="c73d0-393">Carrega um perfil WPR e inicia o rastreamento usando o perfil carregado.</span><span class="sxs-lookup"><span data-stu-id="c73d0-393">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="c73d0-394">Carga útil</span><span class="sxs-lookup"><span data-stu-id="c73d0-394">Payload</span></span>
* <span data-ttu-id="c73d0-395">corpo http de conformidade de várias partes</span><span class="sxs-lookup"><span data-stu-id="c73d0-395">multi-part conforming http body</span></span>

<span data-ttu-id="c73d0-396">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-396">Return data</span></span>
* <span data-ttu-id="c73d0-397">Retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="c73d0-397">Returns the WPR session status.</span></span>

<span data-ttu-id="c73d0-398">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-398">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="c73d0-399">Recupera o status da sessão WPR</span><span class="sxs-lookup"><span data-stu-id="c73d0-399">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="c73d0-400">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-400">Return data</span></span>
* <span data-ttu-id="c73d0-401">Status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="c73d0-401">WPR session status.</span></span>

<span data-ttu-id="c73d0-402">**/API/WPR/Trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-402">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="c73d0-403">Interrompe uma sessão de rastreamento de WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="c73d0-403">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="c73d0-404">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-404">Return data</span></span>
* <span data-ttu-id="c73d0-405">Retorna o arquivo ETL de rastreamento</span><span class="sxs-lookup"><span data-stu-id="c73d0-405">Returns the trace ETL file</span></span>

<span data-ttu-id="c73d0-406">**/API/WPR/Trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="c73d0-406">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="c73d0-407">Inicia uma sessão de rastreamento WPR (desempenho)</span><span class="sxs-lookup"><span data-stu-id="c73d0-407">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="c73d0-408">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c73d0-408">Parameters</span></span>
* <span data-ttu-id="c73d0-409">Perfil: nome do perfil.</span><span class="sxs-lookup"><span data-stu-id="c73d0-409">profile : Profile name.</span></span> <span data-ttu-id="c73d0-410">Os perfis disponíveis são armazenados em perfprofiles/profiles.jsem</span><span class="sxs-lookup"><span data-stu-id="c73d0-410">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="c73d0-411">Retornar dados</span><span class="sxs-lookup"><span data-stu-id="c73d0-411">Return data</span></span>
* <span data-ttu-id="c73d0-412">Em Iniciar, retorna o status da sessão WPR.</span><span class="sxs-lookup"><span data-stu-id="c73d0-412">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="c73d0-413">Veja também</span><span class="sxs-lookup"><span data-stu-id="c73d0-413">See also</span></span>
* [<span data-ttu-id="c73d0-414">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="c73d0-414">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="c73d0-415">Referência da API principal do portal do dispositivo (UWP)</span><span class="sxs-lookup"><span data-stu-id="c73d0-415">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)

---
title: Documentação do pacote de dados espaciais da realidade misturada
description: Documentação para usar o pacote de dados espaciais da realidade misturada
author: alfred-msft
ms.author: yuripek
ms.date: 05/16/2019
ms.topic: article
keywords: LBE, MixedRealitySpatialDataPackager. exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 3beb8f9168bfb6fd921d6d5c1eb6d250c70a714d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539686"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="0eb8d-104">Documentação do pacote de dados espaciais da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="0eb8d-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="0eb8d-105">Essa ferramenta e sua operação são oferecidas no estado em que se encontram.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="0eb8d-106">Ele está sujeito a alterações sem aviso e pode não ser compatível com versões futuras do Windows ou do Windows Mixed Reality HMD.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="0eb8d-107">Baixar</span><span class="sxs-lookup"><span data-stu-id="0eb8d-107">Download</span></span>
 <span data-ttu-id="0eb8d-108">Baixe o [MixedRealitySpatialDataPackager aqui](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="0eb8d-108">Download [MixedRealitySpatialDataPackager here](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="device-support"></a><span data-ttu-id="0eb8d-109">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="0eb8d-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0eb8d-110"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="0eb8d-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="0eb8d-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0eb8d-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="0eb8d-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0eb8d-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="0eb8d-113"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="0eb8d-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0eb8d-114">Empacotador de dados espaciais da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="0eb8d-114">Mixed Reality Spatial Data Packager</span></span></td>
        <td>❌</td>
        <td>❌</td>
        <td><span data-ttu-id="0eb8d-115">✔️</span><span class="sxs-lookup"><span data-stu-id="0eb8d-115">✔️</span></span></td>
    </tr>
</table>

## <a name="quickstart"></a><span data-ttu-id="0eb8d-116">TUTORIAIS</span><span class="sxs-lookup"><span data-stu-id="0eb8d-116">Quickstart</span></span>

<span data-ttu-id="0eb8d-117">A ferramenta de pacote de dados espaciais da realidade misturada copia os dados espaciais de um aplicativo de destino de um PC para outro por meio de um processo de exportação e importação de duas etapas.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-117">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="0eb8d-118">A ferramenta deve ser executada com privilégios de administrador e exclui os dados espaciais existentes na importação.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-118">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="0eb8d-119">A exportação deixa os dados espaciais existentes intactos.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-119">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="0eb8d-120">Principais requisitos e limitações:</span><span class="sxs-lookup"><span data-stu-id="0eb8d-120">Key requirements and limitations:</span></span>

1. <span data-ttu-id="0eb8d-121">A ferramenta deve ser executada com privilégios de administrador</span><span class="sxs-lookup"><span data-stu-id="0eb8d-121">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="0eb8d-122">Talvez seja necessário reiniciar o PC se o portal de realidade misturada estiver instável após a execução da ferramenta</span><span class="sxs-lookup"><span data-stu-id="0eb8d-122">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="0eb8d-123">A ferramenta não será executada ao encontrar incompatibilidades de versão de dados espaciais ou incompatíveis</span><span class="sxs-lookup"><span data-stu-id="0eb8d-123">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="0eb8d-124">A ferramenta apagará os dados espaciais existentes na importação</span><span class="sxs-lookup"><span data-stu-id="0eb8d-124">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="0eb8d-125">Se o processo de importação falhar, os dados anteriores não poderão ser restaurados, a menos que tenha sido feito o backup exportando anteriormente</span><span class="sxs-lookup"><span data-stu-id="0eb8d-125">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="0eb8d-126">Qualidade da funcionalidade de importação contingente no modo "somente leitura" para dados de mapa espacial</span><span class="sxs-lookup"><span data-stu-id="0eb8d-126">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="0eb8d-127">Práticas recomendadas de mapeamento</span><span class="sxs-lookup"><span data-stu-id="0eb8d-127">Mapping Best Practices</span></span>

1. <span data-ttu-id="0eb8d-128">Limpe os mapas existentes no painel de controle (Configurações-> realidade misturada-> ambiente-> limpar dados do ambiente)</span><span class="sxs-lookup"><span data-stu-id="0eb8d-128">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="0eb8d-129">Garanta uma iluminação suficiente para um bom acompanhamento e, se estiver executando o modo de mapa bloqueado, tente manter a mesma iluminação</span><span class="sxs-lookup"><span data-stu-id="0eb8d-129">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="0eb8d-130">Quando possível, mantenha o intervalo dinâmico de iluminação baixo, evitando áreas de alta iluminação ao lado de áreas sombreadas e escuras</span><span class="sxs-lookup"><span data-stu-id="0eb8d-130">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="0eb8d-131">Minimize as superfícies em branco e não texturas, por exemplo, colocar uma variedade de pôsteres diferentes em paredes brancas</span><span class="sxs-lookup"><span data-stu-id="0eb8d-131">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="0eb8d-132">Mapear o espaço sem objetos dinâmicos na cena, como mover pessoas</span><span class="sxs-lookup"><span data-stu-id="0eb8d-132">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="0eb8d-133">Bloquear o mapa na importação (disponível por meio do insider Preview)</span><span class="sxs-lookup"><span data-stu-id="0eb8d-133">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="0eb8d-134">Desbloquear o mapa e examinar novamente o ambiente quando o rastreamento de qualidade degrada e/ou se há alterações no ambiente (iluminação ou alterações no layout do objeto)</span><span class="sxs-lookup"><span data-stu-id="0eb8d-134">Unlock the map and rescan the environment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="0eb8d-135">Executando o Gerenciador de dados espaciais da realidade misturada com o script complementar</span><span class="sxs-lookup"><span data-stu-id="0eb8d-135">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="0eb8d-136">Fornecemos o MRSpatialPackagerHelperScript. ps1 que executa o MAP Packager das ferramentas.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-136">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="0eb8d-137">Os parâmetros de script são definidos abaixo:</span><span class="sxs-lookup"><span data-stu-id="0eb8d-137">The script parameters are defined below:</span></span>

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="0eb8d-138">Uso e saída de exemplo de script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0eb8d-138">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="0eb8d-139">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName modo de administrador Export-MapxPath D:\Temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="0eb8d-139">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="0eb8d-140">Como exportar usando o MixedRealityPackager. exe</span><span class="sxs-lookup"><span data-stu-id="0eb8d-140">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="0eb8d-141">A exportação de mapas fora do dispositivo gera dois arquivos MapX, Het. MapX e SA. MapX.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-141">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="0eb8d-142">Durante o processo de exportação, todas as âncoras espaciais são removidas, exceto o aplicativo especificado e o limite criado pelo usuário (se existir).</span><span class="sxs-lookup"><span data-stu-id="0eb8d-142">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="0eb8d-143">O nome da família do pacote de origem deve corresponder a um aplicativo instalado existente, ou o exe falhará.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-143">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="0eb8d-144">Como importar usando o MixedRealityPackager. exe</span><span class="sxs-lookup"><span data-stu-id="0eb8d-144">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="0eb8d-145">A importação exclui os dados espaciais existentes e os substitui pelos dados do diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-145">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="0eb8d-146">A entrada do nome do aplicativo especifica o nome do pacote do aplicativo de destino que, como as âncoras espaciais, deve ser importado para o e o SID do usuário de destino especifica o usuário que deve ter acesso às âncoras espaciais importadas.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-146">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="0eb8d-147">O nome da família de pacotes de destino e os SIDs de usuário devem corresponder aos valores existentes no computador ou o exe falhará.</span><span class="sxs-lookup"><span data-stu-id="0eb8d-147">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="0eb8d-148">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="0eb8d-148">Error Messages</span></span>
<span data-ttu-id="0eb8d-149">Além disso, as mensagens de erro abaixo também serão acompanhadas por um HRESULT</span><span class="sxs-lookup"><span data-stu-id="0eb8d-149">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="0eb8d-150">Se houvesse um erro de argumentos inválidos</span><span class="sxs-lookup"><span data-stu-id="0eb8d-150">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="0eb8d-151">Se o executável não foi executado no modo de administrador</span><span class="sxs-lookup"><span data-stu-id="0eb8d-151">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="0eb8d-152">Se houvesse um erro ao habilitar ou desabilitar o driver</span><span class="sxs-lookup"><span data-stu-id="0eb8d-152">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="0eb8d-153">Se houve um erro ao validar a versão espacial do banco de dados</span><span class="sxs-lookup"><span data-stu-id="0eb8d-153">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="0eb8d-154">Se houve um erro ao validar o nome da família de pacotes fornecido para o aplicativo de importação/exportação de destino</span><span class="sxs-lookup"><span data-stu-id="0eb8d-154">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="0eb8d-155">Se houve um erro ao validar o SID do usuário</span><span class="sxs-lookup"><span data-stu-id="0eb8d-155">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="0eb8d-156">Se houve um erro relacionado aos arquivos de dados espaciais de origem ou destino</span><span class="sxs-lookup"><span data-stu-id="0eb8d-156">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a><span data-ttu-id="0eb8d-157">Se houve um erro relacionado à inicialização e à interrupção do espectro/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="0eb8d-157">If there was an error related to starting and stopping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```

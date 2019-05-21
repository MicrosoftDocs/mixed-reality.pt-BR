---
title: Documentação do empacotador de dados espaciais de realidade misturada
description: Documentação para usar o Gerenciador de dados espaciais realidade mista
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942102"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="c26ec-104">Documentação do empacotador de dados espaciais de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="c26ec-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="c26ec-105">Essa ferramenta e sua operação são oferecidas como-está.</span><span class="sxs-lookup"><span data-stu-id="c26ec-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="c26ec-106">Ela está sujeita a alterações sem qualquer aviso e pode não ser compatível com Windows futuros ou libera HMD de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="c26ec-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="c26ec-107">Download</span><span class="sxs-lookup"><span data-stu-id="c26ec-107">Download</span></span>
 <span data-ttu-id="c26ec-108">Baixar [MixedRealitySpatialDataPackager aqui](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="c26ec-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="c26ec-109">Guia de início rápido</span><span class="sxs-lookup"><span data-stu-id="c26ec-109">Quickstart</span></span>

<span data-ttu-id="c26ec-110">A ferramenta de Gerenciador de dados espaciais realidade mista copia os dados espaciais de um aplicativo de destino de um PC para outro por meio de uma etapa dois exportar e importar o processo.</span><span class="sxs-lookup"><span data-stu-id="c26ec-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="c26ec-111">A ferramenta deve ser executada com privilégios de administrador e exclui os dados espaciais existentes na importação.</span><span class="sxs-lookup"><span data-stu-id="c26ec-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="c26ec-112">Exportação deixa os dados espaciais existentes intactas.</span><span class="sxs-lookup"><span data-stu-id="c26ec-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="c26ec-113">Principais requisitos e limitações:</span><span class="sxs-lookup"><span data-stu-id="c26ec-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="c26ec-114">Ferramenta deve ser executada com privilégios de administrador</span><span class="sxs-lookup"><span data-stu-id="c26ec-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="c26ec-115">Talvez você precise reiniciar o computador se o Portal de realidade mista é instável após executar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="c26ec-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="c26ec-116">Ferramenta não será executada quando se deparar com a incompatibilidade de versão de dados espaciais ou incompatibilidades</span><span class="sxs-lookup"><span data-stu-id="c26ec-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="c26ec-117">Ferramenta apagará os dados espaciais existentes na importação</span><span class="sxs-lookup"><span data-stu-id="c26ec-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="c26ec-118">Se o processo de importação falhará anterior dados não podem ser restaurados, a menos que ele tiver sido feito por meio da exportação anteriormente</span><span class="sxs-lookup"><span data-stu-id="c26ec-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="c26ec-119">Qualidade da funcionalidade de importação contingente no modo "Somente leitura" para dados espaciais do mapa</span><span class="sxs-lookup"><span data-stu-id="c26ec-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="c26ec-120">Práticas recomendadas de mapeamento</span><span class="sxs-lookup"><span data-stu-id="c26ec-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="c26ec-121">Limpar mapas existentes no painel de controle (Configurações -> realidade misturada -> ambiente -> ambiente limpar dados)</span><span class="sxs-lookup"><span data-stu-id="c26ec-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="c26ec-122">Certifique-se de iluminação suficiente para acompanhamento de BOM e se executando de modo de mapa bloqueado tenta manter a mesma luminosidade</span><span class="sxs-lookup"><span data-stu-id="c26ec-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="c26ec-123">Quando for possível manter o intervalo dinâmico de iluminação baixa, evitando áreas de iluminação alta ao lado de áreas sombreadas escuras</span><span class="sxs-lookup"><span data-stu-id="c26ec-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="c26ec-124">Minimizar em branco, textureless superfícies, por exemplo, coloque uma variedade de diferentes cartazes em brancos paredes</span><span class="sxs-lookup"><span data-stu-id="c26ec-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="c26ec-125">Mapear o espaço sem objetos dinâmicos na cena como mover as pessoas</span><span class="sxs-lookup"><span data-stu-id="c26ec-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="c26ec-126">Bloquear o mapa na importação (disponível por meio do Insider Preview)</span><span class="sxs-lookup"><span data-stu-id="c26ec-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="c26ec-127">Desbloqueie o mapa e examinar novamente o ambiente quando degrada o controle de qualidade e/ou há alterações no ambiente (iluminação ou alterações no layout do objeto)</span><span class="sxs-lookup"><span data-stu-id="c26ec-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="c26ec-128">Gerenciador de dados espaciais de realidade misturada em execução com Script complementar</span><span class="sxs-lookup"><span data-stu-id="c26ec-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="c26ec-129">Nós fornecemos MRSpatialPackagerHelperScript.ps1 que executa o Gerenciador de mapa as ferramentas.</span><span class="sxs-lookup"><span data-stu-id="c26ec-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="c26ec-130">Os parâmetros do script estão definidos abaixo:</span><span class="sxs-lookup"><span data-stu-id="c26ec-130">The script parameters are defined below:</span></span>

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
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="c26ec-131">Saída e o uso de exemplo de Script do Powershell</span><span class="sxs-lookup"><span data-stu-id="c26ec-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="c26ec-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span><span class="sxs-lookup"><span data-stu-id="c26ec-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="c26ec-133">Como exportar usando MixedRealityPackager.exe</span><span class="sxs-lookup"><span data-stu-id="c26ec-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="c26ec-134">Exportar mapas de dispositivo gera dois arquivos de mapx, het.mapx e sa.mapx.</span><span class="sxs-lookup"><span data-stu-id="c26ec-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="c26ec-135">Durante o processo de exportação todas as âncoras espaciais são removidas, exceto para o aplicativo especificado e o limite de usuário criado (se houver).</span><span class="sxs-lookup"><span data-stu-id="c26ec-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="c26ec-136">O nome da família de fonte deve corresponder a um aplicativo instalado existente ou o exe falhará.</span><span class="sxs-lookup"><span data-stu-id="c26ec-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="c26ec-137">Como importar usando MixedRealityPackager.exe</span><span class="sxs-lookup"><span data-stu-id="c26ec-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="c26ec-138">Importação excluirá os dados espaciais existentes e substitui-lo com os dados do diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="c26ec-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="c26ec-139">A entrada de nome de aplicativo especifica o nome do pacote do aplicativo de destino que, como as âncoras espaciais deve ser importado para e o SID de usuário de destino Especifica o usuário que deve ter acesso às âncoras espaciais importados.</span><span class="sxs-lookup"><span data-stu-id="c26ec-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="c26ec-140">O nome da família de destino e os SIDs dos usuários devem corresponder aos valores existentes no PC ou no exe falhará.</span><span class="sxs-lookup"><span data-stu-id="c26ec-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="c26ec-141">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="c26ec-141">Error Messages</span></span>
<span data-ttu-id="c26ec-142">Além das mensagens de erro abaixo falhas também serão acompanhadas de um HRESULT</span><span class="sxs-lookup"><span data-stu-id="c26ec-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="c26ec-143">Se ocorreu um erro argumentos inválidos</span><span class="sxs-lookup"><span data-stu-id="c26ec-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="c26ec-144">Se o executável não foi executado no modo de administrador</span><span class="sxs-lookup"><span data-stu-id="c26ec-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="c26ec-145">Se ocorreu um erro, habilitar ou desabilitar o driver</span><span class="sxs-lookup"><span data-stu-id="c26ec-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="c26ec-146">Se houve um erro ao validar a versão do banco de dados espaciais</span><span class="sxs-lookup"><span data-stu-id="c26ec-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="c26ec-147">Se houve um erro ao validar o nome de família do pacote fornecido para o aplicativo de importação/exportação de destino</span><span class="sxs-lookup"><span data-stu-id="c26ec-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="c26ec-148">Se houve um erro ao validar o SID de usuário</span><span class="sxs-lookup"><span data-stu-id="c26ec-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="c26ec-149">Se tiver ocorrido um erro para o destino ou a fonte de dados espaciais arquivos relacionados</span><span class="sxs-lookup"><span data-stu-id="c26ec-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="c26ec-150">Se houve um erro relacionado ao iniciar e parar o espectro/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="c26ec-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```

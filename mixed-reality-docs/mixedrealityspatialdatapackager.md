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
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Documentação do pacote de dados espaciais da realidade misturada

>[!NOTE]
> Essa ferramenta e sua operação são oferecidas no estado em que se encontram. Ele está sujeito a alterações sem aviso e pode não ser compatível com versões futuras do Windows ou do Windows Mixed Reality HMD.

## <a name="download"></a>Baixar
 Baixe o [MixedRealitySpatialDataPackager aqui](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Empacotador de dados espaciais da realidade misturada</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>TUTORIAIS

A ferramenta de pacote de dados espaciais da realidade misturada copia os dados espaciais de um aplicativo de destino de um PC para outro por meio de um processo de exportação e importação de duas etapas. A ferramenta deve ser executada com privilégios de administrador e exclui os dados espaciais existentes na importação. A exportação deixa os dados espaciais existentes intactos.

Principais requisitos e limitações:

1. A ferramenta deve ser executada com privilégios de administrador 
2. Talvez seja necessário reiniciar o PC se o portal de realidade misturada estiver instável após a execução da ferramenta
3. A ferramenta não será executada ao encontrar incompatibilidades de versão de dados espaciais ou incompatíveis
4. A ferramenta apagará os dados espaciais existentes na importação
5. Se o processo de importação falhar, os dados anteriores não poderão ser restaurados, a menos que tenha sido feito o backup exportando anteriormente
6. Qualidade da funcionalidade de importação contingente no modo "somente leitura" para dados de mapa espacial
***

## <a name="mapping-best-practices"></a>Práticas recomendadas de mapeamento

1. Limpe os mapas existentes no painel de controle (Configurações-> realidade misturada-> ambiente-> limpar dados do ambiente)
2. Garanta uma iluminação suficiente para um bom acompanhamento e, se estiver executando o modo de mapa bloqueado, tente manter a mesma iluminação
3. Quando possível, mantenha o intervalo dinâmico de iluminação baixo, evitando áreas de alta iluminação ao lado de áreas sombreadas e escuras
4. Minimize as superfícies em branco e não texturas, por exemplo, colocar uma variedade de pôsteres diferentes em paredes brancas
5. Mapear o espaço sem objetos dinâmicos na cena, como mover pessoas
6. Bloquear o mapa na importação (disponível por meio do insider Preview)
7. Desbloquear o mapa e examinar novamente o ambiente quando o rastreamento de qualidade degrada e/ou se há alterações no ambiente (iluminação ou alterações no layout do objeto)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Executando o Gerenciador de dados espaciais da realidade misturada com o script complementar

Fornecemos o MRSpatialPackagerHelperScript. ps1 que executa o MAP Packager das ferramentas. 


Os parâmetros de script são definidos abaixo:

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

### <a name="powershell-script-example-usage-and-output"></a>Uso e saída de exemplo de script do PowerShell

.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName modo de administrador Export-MapxPath D:\Temp\-LockMap 0
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>Como exportar usando o MixedRealityPackager. exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

A exportação de mapas fora do dispositivo gera dois arquivos MapX, Het. MapX e SA. MapX. Durante o processo de exportação, todas as âncoras espaciais são removidas, exceto o aplicativo especificado e o limite criado pelo usuário (se existir). O nome da família do pacote de origem deve corresponder a um aplicativo instalado existente, ou o exe falhará.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>Como importar usando o MixedRealityPackager. exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
A importação exclui os dados espaciais existentes e os substitui pelos dados do diretório especificado. A entrada do nome do aplicativo especifica o nome do pacote do aplicativo de destino que, como as âncoras espaciais, deve ser importado para o e o SID do usuário de destino especifica o usuário que deve ter acesso às âncoras espaciais importadas. O nome da família de pacotes de destino e os SIDs de usuário devem corresponder aos valores existentes no computador ou o exe falhará.


***
## <a name="error-messages"></a>Mensagens de erro
Além disso, as mensagens de erro abaixo também serão acompanhadas por um HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>Se houvesse um erro de argumentos inválidos
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Se o executável não foi executado no modo de administrador
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Se houvesse um erro ao habilitar ou desabilitar o driver
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Se houve um erro ao validar a versão espacial do banco de dados
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Se houve um erro ao validar o nome da família de pacotes fornecido para o aplicativo de importação/exportação de destino
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Se houve um erro ao validar o SID do usuário
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Se houve um erro relacionado aos arquivos de dados espaciais de origem ou destino
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>Se houve um erro relacionado à inicialização e à interrupção do espectro/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```

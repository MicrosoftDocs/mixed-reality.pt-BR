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
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Documentação do empacotador de dados espaciais de realidade misturada

>[!NOTE]
> Essa ferramenta e sua operação são oferecidas como-está. Ela está sujeita a alterações sem qualquer aviso e pode não ser compatível com Windows futuros ou libera HMD de realidade mista do Windows.

## <a name="download"></a>Download
 Baixar [MixedRealitySpatialDataPackager aqui](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>Guia de início rápido

A ferramenta de Gerenciador de dados espaciais realidade mista copia os dados espaciais de um aplicativo de destino de um PC para outro por meio de uma etapa dois exportar e importar o processo. A ferramenta deve ser executada com privilégios de administrador e exclui os dados espaciais existentes na importação. Exportação deixa os dados espaciais existentes intactas.

Principais requisitos e limitações:

1. Ferramenta deve ser executada com privilégios de administrador 
2. Talvez você precise reiniciar o computador se o Portal de realidade mista é instável após executar a ferramenta
3. Ferramenta não será executada quando se deparar com a incompatibilidade de versão de dados espaciais ou incompatibilidades
4. Ferramenta apagará os dados espaciais existentes na importação
5. Se o processo de importação falhará anterior dados não podem ser restaurados, a menos que ele tiver sido feito por meio da exportação anteriormente
6. Qualidade da funcionalidade de importação contingente no modo "Somente leitura" para dados espaciais do mapa
***

## <a name="mapping-best-practices"></a>Práticas recomendadas de mapeamento

1. Limpar mapas existentes no painel de controle (Configurações -> realidade misturada -> ambiente -> ambiente limpar dados)
2. Certifique-se de iluminação suficiente para acompanhamento de BOM e se executando de modo de mapa bloqueado tenta manter a mesma luminosidade
3. Quando for possível manter o intervalo dinâmico de iluminação baixa, evitando áreas de iluminação alta ao lado de áreas sombreadas escuras
4. Minimizar em branco, textureless superfícies, por exemplo, coloque uma variedade de diferentes cartazes em brancos paredes
5. Mapear o espaço sem objetos dinâmicos na cena como mover as pessoas
6. Bloquear o mapa na importação (disponível por meio do Insider Preview)
7. Desbloqueie o mapa e examinar novamente o ambiente quando degrada o controle de qualidade e/ou há alterações no ambiente (iluminação ou alterações no layout do objeto)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Gerenciador de dados espaciais de realidade misturada em execução com Script complementar

Nós fornecemos MRSpatialPackagerHelperScript.ps1 que executa o Gerenciador de mapa as ferramentas. 


Os parâmetros do script estão definidos abaixo:

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

### <a name="powershell-script-example-usage-and-output"></a>Saída e o uso de exemplo de Script do Powershell

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>Como exportar usando MixedRealityPackager.exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

Exportar mapas de dispositivo gera dois arquivos de mapx, het.mapx e sa.mapx. Durante o processo de exportação todas as âncoras espaciais são removidas, exceto para o aplicativo especificado e o limite de usuário criado (se houver). O nome da família de fonte deve corresponder a um aplicativo instalado existente ou o exe falhará.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>Como importar usando MixedRealityPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Importação excluirá os dados espaciais existentes e substitui-lo com os dados do diretório especificado. A entrada de nome de aplicativo especifica o nome do pacote do aplicativo de destino que, como as âncoras espaciais deve ser importado para e o SID de usuário de destino Especifica o usuário que deve ter acesso às âncoras espaciais importados. O nome da família de destino e os SIDs dos usuários devem corresponder aos valores existentes no PC ou no exe falhará.


***
## <a name="error-messages"></a>Mensagens de erro
Além das mensagens de erro abaixo falhas também serão acompanhadas de um HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>Se ocorreu um erro argumentos inválidos
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Se o executável não foi executado no modo de administrador
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Se ocorreu um erro, habilitar ou desabilitar o driver
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Se houve um erro ao validar a versão do banco de dados espaciais
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Se houve um erro ao validar o nome de família do pacote fornecido para o aplicativo de importação/exportação de destino
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Se houve um erro ao validar o SID de usuário
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Se tiver ocorrido um erro para o destino ou a fonte de dados espaciais arquivos relacionados
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>Se houve um erro relacionado ao iniciar e parar o espectro/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```

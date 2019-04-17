---
title: Implementar iniciadores de aplicativo 3D (aplicativos Win32)
description: Como criar inicializadores de aplicativos 3D e logotipos para aplicativos Win32 VR e jogos (distribuídos fora de fluxo) então eles aparecem no ambiente página inicial e o menu Iniciar de realidade mista do Windows.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, ícone, modelagem, iniciador, iniciador 3D, lado a lado, o cubo ao vivo, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589771"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementar iniciadores de aplicativo 3D (aplicativos Win32)

> [!NOTE]
> Esse recurso só está disponível para computadores que executam a versão mais recente [Windows Insider](https://insider.windows.com) voos (RS5), build 17704 e mais recente.

O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) é o ponto de partida em que os usuários cheguem antes de iniciar aplicativos. Por padrão, jogos e aplicativos Win32 VR imersivo precisam ser iniciados de fora o fone de ouvido e não aparecerão na lista "Todos os aplicativos" no menu Iniciar de realidade mista do Windows. No entanto, seguindo as instruções neste artigo para implementar um iniciador de aplicativos 3D, sua experiência de imersão VR Win32 pode ser iniciada de dentro do ambiente doméstico e menu Iniciar de realidade mista do Windows.

Isso somente é verdadeiro para imersivo distributied experiências de Win32 VR fora do fluxo. Para experiências de VR [distribuídos por meio do Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), temos [atualizado com o Windows Mixed Reality SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) voos de junto com o RS5 de Insider mais recente do Windows, de modo que SteamVR títulos show-se no Windows Misto menu Iniciar da realidade na lista "Todos os aplicativos" automaticamente usando um inicializador padrão. Em outras palavras, o método descrito neste artigo é desnecessário para títulos de SteamVR e será substituído pelo Windows Mixed Reality para a funcionalidade de SteamVR Beta.

## <a name="3d-app-launcher-creation-process"></a>Processo de criação de iniciador do aplicativo 3D

Há 3 etapas para criar um inicializador de aplicativos 3D:
1. [Criando e concepting](3d-app-launcher-design-guidance.md)
2. [Modelagem e exportando](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integração ao seu aplicativo (Este artigo)

Ativos 3D para serem usados como os inicializadores para seu aplicativo devem ser criados usando o [diretrizes de criação de realidade mista do Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantir a compatibilidade. Ativos que não atendem a essa especificação de criação não serão renderizados no Windows Mixed Reality inicial.

## <a name="configuring-the-3d-launcher"></a>Configurando o iniciador do 3D

Aplicativos do Win32 aparecerá na lista "Todos os aplicativos" no menu Iniciar de realidade mista do Windows se você criar um inicializador de aplicativos 3D para eles. Para fazer isso, crie uma [elementos visuais do manifesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) arquivo XML que referencia o iniciador do aplicativo 3D seguindo estas etapas:

1. Criar uma **3D arquivo do inicializador de aplicativos ativos GLB** (consulte [modelagem e exportando](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Criar uma **[elementos visuais do manifesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** para seu aplicativo.
    1. Você pode começar com o [exemplo a seguir](#sample-visual-elements-manifest).  Ver todo [elementos visuais do manifesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentação para obter mais detalhes.
    2. Atualização **Square150x150Logo** e **Square70x70Logo** com uma imagem PNG/JPG/GIF para seu aplicativo.
        * Eles serão usados para logotipo em 2D do aplicativo na lista de Windows misto realidade todos os aplicativos e para o Menu Iniciar na área de trabalho.
        * O caminho do arquivo é relativo à pasta que contém o manifesto de elementos visuais.
        * Você ainda precisa fornecer uma ícone do Menu Iniciar da área de trabalho para seu aplicativo por meio de mecanismos padrão. Isso pode ser diretamente no executável ou no atalho criado (por exemplo, por meio de IShellLink::SetIconLocation).
        * *Opcional:* Você pode usar um arquivo resources.pri se desejar MRT fornecer vários tamanhos de ativo para resolução diferentes escalas e temas de alto contraste.
    3. Atualizar o **MixedRealityModel caminho** para apontar para a GLB seu iniciador do aplicativo 3D
    4. Salve o arquivo com o mesmo nome que seu arquivo executável, com a extensão ". VisualElementsManifest.xml"e salve-o no mesmo diretório. Por exemplo, para o arquivo executável "contoso.exe", o arquivo XML que acompanha este artigo é chamado de "contoso.visualelementsmanifest.xml".
3. **Adicionar um atalho** ao seu aplicativo para desktops Windows Menu Iniciar. Consulte a [exemplo a seguir](#sample-app-launcher-shortcut-creation) para obter um exemplo C++ implementação. 
    * Criá-lo em %ALLUSERSPROFILE%\Microsoft\Windows\Start Iniciar\Programas (máquina) ou %APPDATA%\Microsoft\Windows\Start Iniciar\Programas (usuário)
    * Se uma atualização altera seu manifesto elementos visuais ou os ativos referenciados por ele, o instalador ou atualizador deve atualizar o atalho de tal forma que o manifesto é reanalisado e ativos armazenados em cache são atualizados.
4. *Opcional:* Se o atalho de sua área de trabalho não apontar diretamente para o EXE do seu aplicativo (por exemplo, se ele invoca um manipulador de protocolo personalizado, como "myapp: / /"), o Menu Iniciar automaticamente não localizará o arquivo de VisualElementsManifest.xml do aplicativo. Para resolver esse problema, o atalho deve especificar o caminho do arquivo do manifesto de elementos visuais, usando (System.AppUserModel.VisualElementsManifestHintPath). Isso pode ser definido no atalho usando as mesmas técnicas como System.AppUserModel.ID. Não é necessário usar System.AppUserModel.ID, mas você pode fazer isso se você desejar que o atalho coincidir com a ID de modelo de usuário aplicativo explícita do aplicativo, se um for usado.  Consulte a [criação de atalho de iniciador do aplicativo de exemplo](#sample-app-launcher-shortcut-creation) seção abaixo para um C++ exemplo.

### <a name="sample-visual-elements-manifest"></a>Exemplo de manifesto de elementos visuais

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>Criação de atalho do iniciador de aplicativo de exemplo

O código de exemplo abaixo mostra como você pode criar um atalho no C++, incluindo o caminho para o arquivo XML de manifesto Visual de elementos de substituição. Observe que a substituição é necessária somente em casos em que o atalho não aponta diretamente para o EXE associado ao manifesto (por exemplo o atalho de sua usa um manipulador de protocolo personalizado, como "myapp: / /").

#### <a name="sample-lnk-shortcut-creation-c"></a>Exemplo. Criação de atalho LNK (C++)

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>Exemplo. Atalho para URL iniciador 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>Consulte também

* [Exemplo de modelo de realidade misturada](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contendo um inicializador de aplicativos 3D.
* [Diretrizes de design de iniciador do aplicativo 3D](3d-app-launcher-design-guidance.md)
* [Criar modelos 3D para uso no ambiente doméstico Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementando os inicializadores de aplicativos 3D (aplicativos UWP)](implementing-3d-app-launchers.md)
* [Navegando o Windows Mixed Reality inicial](navigating-the-windows-mixed-reality-home.md)

---
title: Implementar inicializadores de aplicativo 3D (aplicativos Win32)
description: Como criar iniciadores e logotipos de aplicativos 3D para aplicativos e jogos do Win32 VR (distribuídos fora do fluxo) para que eles apareçam no menu Iniciar do Windows Mixed Reality e no ambiente doméstico.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, ícone, modelagem, iniciador, iniciador 3D, bloco, cubo ao vivo, Win32
ms.openlocfilehash: 87eadfb5184f9fb5f8d513ab00a2a954e71df376
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438577"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementar inicializadores de aplicativo 3D (aplicativos Win32)

> [!NOTE]
> Esse recurso só está disponível para computadores que executam os vôos mais recentes do [Windows Insider](https://insider.windows.com) (RS5), compilação 17704 e mais recente.

O [Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md) é o ponto de partida onde os usuários vão antes de iniciar os aplicativos. Por padrão, os aplicativos e jogos de imersão do Win32 devem ser iniciados de fora do headset e não aparecerão na lista "todos os aplicativos" no menu Iniciar da realidade do Windows Mixed. No entanto, seguindo as instruções neste artigo para implementar um inicializador de aplicativo 3D, sua experiência de imersão do Win32 VR pode ser iniciada no menu iniciar e no ambiente inicial do Windows Mixed Reality.

Isso só é verdadeiro para experiências de imersão do Win32 distributied fora do fluxo. Para experiências de VR [distribuídas por meio do vapor](updating-your-steamvr-application-for-windows-mixed-reality.md), [atualizamos a realidade mista do Windows para SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto com os vôos do Windows Insider RS5 mais recentes para que os títulos de SteamVR sejam exibidos no menu Iniciar do Windows Mixed Reality na lista "todos os aplicativos" automaticamente usando um iniciador padrão. Em outras palavras, o método descrito neste artigo é desnecessário para títulos SteamVR e será substituído pela funcionalidade Windows Mixed Reality para SteamVR beta.

## <a name="3d-app-launcher-creation-process"></a>processo de criação do inicializador de aplicativo 3D

Há três etapas para criar um iniciador de aplicativo 3D:
1. [Design e conceito](3d-app-launcher-design-guidance.md)
2. [Modelagem e exportação](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrando-o ao seu aplicativo (este artigo)

os ativos 3D a serem usados como iniciadores para seu aplicativo devem ser criados usando as [diretrizes de criação do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantir a compatibilidade. Os ativos que não atenderem a essa especificação de criação não serão renderizados na página inicial do Windows Mixed Reality.

## <a name="configuring-the-3d-launcher"></a>Configurando o iniciador 3D

Os aplicativos Win32 serão exibidos na lista "todos os aplicativos" no menu Iniciar do Windows Mixed Reality se você criar um inicializador de aplicativo 3D para eles. Para fazer isso, crie um arquivo XML de [manifesto de elementos visuais](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) referenciando o iniciador do aplicativo 3D seguindo estas etapas:

1. Crie um **arquivo glb do ativo do iniciador de aplicativo 3D** (consulte [modelagem e exportação](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Crie um **[manifesto de elementos visuais](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** para seu aplicativo.
    1. Você pode começar com o [exemplo abaixo](#sample-visual-elements-manifest).  Consulte a documentação de [manifesto de elementos visuais](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) completos para obter mais detalhes.
    2. Atualize **Square150x150Logo** e **SQUARE70X70LOGO** com um png/jpg/gif para seu aplicativo.
        * Eles serão usados para o logotipo 2D do aplicativo na lista todos os aplicativos do Windows Mixed Reality e para o menu iniciar na área de trabalho.
        * O caminho do arquivo é relativo à pasta que contém o manifesto dos elementos visuais.
        * Você ainda precisa fornecer um ícone do menu Iniciar do desktop para seu aplicativo por meio dos mecanismos padrão. Isso pode ser diretamente no executável ou no atalho que você criar (por exemplo, via IShellLink:: SetIconLocation).
        * *Opcional:* Você pode usar um arquivo Resources. pri se desejar que o MRT forneça vários tamanhos de ativos para diferentes escalas de resolução e temas de alto contraste.
    3. Atualize o **caminho do MixedRealityModel** para apontar para o glb para o iniciador do aplicativo 3D
    4. Salve o arquivo com o mesmo nome do arquivo executável, com uma extensão de ". VisualElementsManifest. xml "e salve-o no mesmo diretório. Por exemplo, para o arquivo executável "contoso. exe", o arquivo XML que o acompanha é denominado "contoso. visualelementsmanifest. xml".
3. **Adicione um atalho** ao seu aplicativo no menu Iniciar do Windows da área de trabalho. Consulte o [exemplo abaixo](#sample-app-launcher-shortcut-creation) para obter uma C++ implementação de exemplo. 
    * Criá-lo em%ALLUSERSPROFILE%\Microsoft\Windows\Start Iniciar\programas (Machine) ou%APPDATA%\Microsoft\Windows\Start Iniciar\programas (User)
    * Se uma atualização alterar o manifesto dos elementos visuais ou os ativos referenciados por ele, o atualizador ou o instalador deverá atualizar o atalho de modo que o manifesto seja analisado e os ativos em cache sejam atualizados.
4. *Opcional:* Se o seu atalho de área de trabalho não apontar diretamente para o EXE do seu aplicativo (por exemplo, se ele invocar um manipulador de protocolo personalizado como "myapp://"), o menu Iniciar não localizará automaticamente o arquivo VisualElementsManifest. XML do aplicativo. Para resolver isso, o atalho deve especificar o caminho do arquivo do manifesto dos elementos visuais usando System. AppUserModel. VisualElementsManifestHintPath (). Isso pode ser definido no atalho usando as mesmas técnicas que System.AppUserModel.ID. Não é necessário usar System.AppUserModel.ID, mas você pode fazer isso se desejar que o atalho corresponda à ID do modelo de usuário do aplicativo explícito, se um for usado.  Consulte a seção [criação de atalho do iniciador de aplicativo de exemplo](#sample-app-launcher-shortcut-creation) abaixo para obter um C++ exemplo.

### <a name="sample-visual-elements-manifest"></a>Manifesto de elementos visuais de exemplo

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
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

O código de exemplo abaixo mostra como você pode criar um atalho C++no, incluindo a substituição do caminho para o arquivo XML de manifesto dos elementos visuais. Observe que a substituição só é necessária nos casos em que o atalho não aponta diretamente para o EXE associado ao manifesto (por exemplo, o atalho usa um manipulador de protocolo personalizado como "myapp://").

#### <a name="sample-lnk-shortcut-creation-c"></a>Nova. Criação de atalho LNKC++()

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

#### <a name="sample-url-launcher-shortcut"></a>Nova. Atalho do inicializador de URL 

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

* [Exemplo de modelo de realidade misturada](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contém um iniciador de aplicativo 3D.
* [Diretrizes de projeto do inicializador de aplicativos 3D](3d-app-launcher-design-guidance.md)
* [Criando modelos 3D para uso na página inicial do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementando iniciadores de aplicativos 3D (aplicativos UWP)](implementing-3d-app-launchers.md)
* [Como navegar na página inicial do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)

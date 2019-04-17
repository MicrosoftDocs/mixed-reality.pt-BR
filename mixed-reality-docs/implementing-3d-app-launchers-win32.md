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
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="31401-104">Implementar iniciadores de aplicativo 3D (aplicativos Win32)</span><span class="sxs-lookup"><span data-stu-id="31401-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="31401-105">Esse recurso só está disponível para computadores que executam a versão mais recente [Windows Insider](https://insider.windows.com) voos (RS5), build 17704 e mais recente.</span><span class="sxs-lookup"><span data-stu-id="31401-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="31401-106">O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) é o ponto de partida em que os usuários cheguem antes de iniciar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="31401-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="31401-107">Por padrão, jogos e aplicativos Win32 VR imersivo precisam ser iniciados de fora o fone de ouvido e não aparecerão na lista "Todos os aplicativos" no menu Iniciar de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="31401-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="31401-108">No entanto, seguindo as instruções neste artigo para implementar um iniciador de aplicativos 3D, sua experiência de imersão VR Win32 pode ser iniciada de dentro do ambiente doméstico e menu Iniciar de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="31401-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="31401-109">Isso somente é verdadeiro para imersivo distributied experiências de Win32 VR fora do fluxo.</span><span class="sxs-lookup"><span data-stu-id="31401-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="31401-110">Para experiências de VR [distribuídos por meio do Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), temos [atualizado com o Windows Mixed Reality SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) voos de junto com o RS5 de Insider mais recente do Windows, de modo que SteamVR títulos show-se no Windows Misto menu Iniciar da realidade na lista "Todos os aplicativos" automaticamente usando um inicializador padrão.</span><span class="sxs-lookup"><span data-stu-id="31401-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="31401-111">Em outras palavras, o método descrito neste artigo é desnecessário para títulos de SteamVR e será substituído pelo Windows Mixed Reality para a funcionalidade de SteamVR Beta.</span><span class="sxs-lookup"><span data-stu-id="31401-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="31401-112">Processo de criação de iniciador do aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="31401-112">3D app launcher creation process</span></span>

<span data-ttu-id="31401-113">Há 3 etapas para criar um inicializador de aplicativos 3D:</span><span class="sxs-lookup"><span data-stu-id="31401-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="31401-114">Criando e concepting</span><span class="sxs-lookup"><span data-stu-id="31401-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="31401-115">Modelagem e exportando</span><span class="sxs-lookup"><span data-stu-id="31401-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="31401-116">Integração ao seu aplicativo (Este artigo)</span><span class="sxs-lookup"><span data-stu-id="31401-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="31401-117">Ativos 3D para serem usados como os inicializadores para seu aplicativo devem ser criados usando o [diretrizes de criação de realidade mista do Windows](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantir a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="31401-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="31401-118">Ativos que não atendem a essa especificação de criação não serão renderizados no Windows Mixed Reality inicial.</span><span class="sxs-lookup"><span data-stu-id="31401-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="31401-119">Configurando o iniciador do 3D</span><span class="sxs-lookup"><span data-stu-id="31401-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="31401-120">Aplicativos do Win32 aparecerá na lista "Todos os aplicativos" no menu Iniciar de realidade mista do Windows se você criar um inicializador de aplicativos 3D para eles.</span><span class="sxs-lookup"><span data-stu-id="31401-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="31401-121">Para fazer isso, crie uma [elementos visuais do manifesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) arquivo XML que referencia o iniciador do aplicativo 3D seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="31401-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="31401-122">Criar uma **3D arquivo do inicializador de aplicativos ativos GLB** (consulte [modelagem e exportando](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="31401-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="31401-123">Criar uma **[elementos visuais do manifesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31401-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="31401-124">Você pode começar com o [exemplo a seguir](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="31401-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="31401-125">Ver todo [elementos visuais do manifesto](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentação para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="31401-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="31401-126">Atualização **Square150x150Logo** e **Square70x70Logo** com uma imagem PNG/JPG/GIF para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31401-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="31401-127">Eles serão usados para logotipo em 2D do aplicativo na lista de Windows misto realidade todos os aplicativos e para o Menu Iniciar na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="31401-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="31401-128">O caminho do arquivo é relativo à pasta que contém o manifesto de elementos visuais.</span><span class="sxs-lookup"><span data-stu-id="31401-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="31401-129">Você ainda precisa fornecer uma ícone do Menu Iniciar da área de trabalho para seu aplicativo por meio de mecanismos padrão.</span><span class="sxs-lookup"><span data-stu-id="31401-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="31401-130">Isso pode ser diretamente no executável ou no atalho criado (por exemplo, por meio de IShellLink::SetIconLocation).</span><span class="sxs-lookup"><span data-stu-id="31401-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="31401-131">*Opcional:* Você pode usar um arquivo resources.pri se desejar MRT fornecer vários tamanhos de ativo para resolução diferentes escalas e temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="31401-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="31401-132">Atualizar o **MixedRealityModel caminho** para apontar para a GLB seu iniciador do aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="31401-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="31401-133">Salve o arquivo com o mesmo nome que seu arquivo executável, com a extensão ". VisualElementsManifest.xml"e salve-o no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="31401-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="31401-134">Por exemplo, para o arquivo executável "contoso.exe", o arquivo XML que acompanha este artigo é chamado de "contoso.visualelementsmanifest.xml".</span><span class="sxs-lookup"><span data-stu-id="31401-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="31401-135">**Adicionar um atalho** ao seu aplicativo para desktops Windows Menu Iniciar.</span><span class="sxs-lookup"><span data-stu-id="31401-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="31401-136">Consulte a [exemplo a seguir](#sample-app-launcher-shortcut-creation) para obter um exemplo C++ implementação.</span><span class="sxs-lookup"><span data-stu-id="31401-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="31401-137">Criá-lo em %ALLUSERSPROFILE%\Microsoft\Windows\Start Iniciar\Programas (máquina) ou %APPDATA%\Microsoft\Windows\Start Iniciar\Programas (usuário)</span><span class="sxs-lookup"><span data-stu-id="31401-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="31401-138">Se uma atualização altera seu manifesto elementos visuais ou os ativos referenciados por ele, o instalador ou atualizador deve atualizar o atalho de tal forma que o manifesto é reanalisado e ativos armazenados em cache são atualizados.</span><span class="sxs-lookup"><span data-stu-id="31401-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="31401-139">*Opcional:* Se o atalho de sua área de trabalho não apontar diretamente para o EXE do seu aplicativo (por exemplo, se ele invoca um manipulador de protocolo personalizado, como "myapp: / /"), o Menu Iniciar automaticamente não localizará o arquivo de VisualElementsManifest.xml do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31401-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="31401-140">Para resolver esse problema, o atalho deve especificar o caminho do arquivo do manifesto de elementos visuais, usando (System.AppUserModel.VisualElementsManifestHintPath).</span><span class="sxs-lookup"><span data-stu-id="31401-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="31401-141">Isso pode ser definido no atalho usando as mesmas técnicas como System.AppUserModel.ID.</span><span class="sxs-lookup"><span data-stu-id="31401-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="31401-142">Não é necessário usar System.AppUserModel.ID, mas você pode fazer isso se você desejar que o atalho coincidir com a ID de modelo de usuário aplicativo explícita do aplicativo, se um for usado.</span><span class="sxs-lookup"><span data-stu-id="31401-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="31401-143">Consulte a [criação de atalho de iniciador do aplicativo de exemplo](#sample-app-launcher-shortcut-creation) seção abaixo para um C++ exemplo.</span><span class="sxs-lookup"><span data-stu-id="31401-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="31401-144">Exemplo de manifesto de elementos visuais</span><span class="sxs-lookup"><span data-stu-id="31401-144">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="31401-145">Criação de atalho do iniciador de aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="31401-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="31401-146">O código de exemplo abaixo mostra como você pode criar um atalho no C++, incluindo o caminho para o arquivo XML de manifesto Visual de elementos de substituição.</span><span class="sxs-lookup"><span data-stu-id="31401-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="31401-147">Observe que a substituição é necessária somente em casos em que o atalho não aponta diretamente para o EXE associado ao manifesto (por exemplo</span><span class="sxs-lookup"><span data-stu-id="31401-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="31401-148">o atalho de sua usa um manipulador de protocolo personalizado, como "myapp: / /").</span><span class="sxs-lookup"><span data-stu-id="31401-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="31401-149">Exemplo. Criação de atalho LNK (C++)</span><span class="sxs-lookup"><span data-stu-id="31401-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="31401-150">Exemplo. Atalho para URL iniciador</span><span class="sxs-lookup"><span data-stu-id="31401-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="31401-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31401-151">See also</span></span>

* <span data-ttu-id="31401-152">[Exemplo de modelo de realidade misturada](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) contendo um inicializador de aplicativos 3D.</span><span class="sxs-lookup"><span data-stu-id="31401-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="31401-153">Diretrizes de design de iniciador do aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="31401-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="31401-154">Criar modelos 3D para uso no ambiente doméstico Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="31401-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="31401-155">Implementando os inicializadores de aplicativos 3D (aplicativos UWP)</span><span class="sxs-lookup"><span data-stu-id="31401-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="31401-156">Navegando o Windows Mixed Reality inicial</span><span class="sxs-lookup"><span data-stu-id="31401-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)

---
title: Implementar inicializadores de aplicativo 3D (aplicativos Win32)
description: Como criar iniciadores e logotipos de aplicativos 3D para aplicativos e jogos do Win32 VR (distribuídos fora do fluxo) para que eles apareçam no menu Iniciar do Windows Mixed Reality e no ambiente doméstico.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, ícone, modelagem, iniciador, iniciador 3D, bloco, cubo ao vivo, Win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515607"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="2a2d7-104">Implementar inicializadores de aplicativo 3D (aplicativos Win32)</span><span class="sxs-lookup"><span data-stu-id="2a2d7-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="2a2d7-105">Esse recurso só está disponível para computadores que executam os vôos mais recentes do [Windows](https://insider.windows.com) Insider (RS5), compilação 17704 e mais recente.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="2a2d7-106">O [Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md) é o ponto de partida onde os usuários vão antes de iniciar os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="2a2d7-107">Por padrão, os aplicativos e jogos de imersão do Win32 devem ser iniciados de fora do headset e não aparecerão na lista "todos os aplicativos" no menu Iniciar da realidade do Windows Mixed.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="2a2d7-108">No entanto, seguindo as instruções neste artigo para implementar um inicializador de aplicativo 3D, sua experiência de imersão do Win32 VR pode ser iniciada no menu iniciar e no ambiente inicial do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="2a2d7-109">Isso só é verdadeiro para experiências de imersão do Win32 distributied fora do fluxo.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="2a2d7-110">Para experiências de VR [distribuídas por meio do vapor](updating-your-steamvr-application-for-windows-mixed-reality.md), atualizamos [a realidade mista do Windows para SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto com os vôos do Windows Insider RS5 mais recentes para que os títulos de SteamVR sejam exibidos no menu Iniciar do Windows Mixed Reality na lista "todos os aplicativos" automaticamente usando um iniciador padrão.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="2a2d7-111">Em outras palavras, o método descrito neste artigo é desnecessário para títulos SteamVR e será substituído pela funcionalidade Windows Mixed Reality para SteamVR beta.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="2a2d7-112">processo de criação do inicializador de aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="2a2d7-112">3D app launcher creation process</span></span>

<span data-ttu-id="2a2d7-113">Há três etapas para criar um iniciador de aplicativo 3D:</span><span class="sxs-lookup"><span data-stu-id="2a2d7-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="2a2d7-114">Design e conceito</span><span class="sxs-lookup"><span data-stu-id="2a2d7-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="2a2d7-115">Modelagem e exportação</span><span class="sxs-lookup"><span data-stu-id="2a2d7-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="2a2d7-116">Integrando-o ao seu aplicativo (este artigo)</span><span class="sxs-lookup"><span data-stu-id="2a2d7-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="2a2d7-117">os ativos 3D a serem usados como iniciadores para seu aplicativo devem ser criados usando as [diretrizes de criação do Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantir a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="2a2d7-118">Os ativos que não atenderem a essa especificação de criação não serão renderizados na página inicial do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="2a2d7-119">Configurando o iniciador 3D</span><span class="sxs-lookup"><span data-stu-id="2a2d7-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="2a2d7-120">Os aplicativos Win32 serão exibidos na lista "todos os aplicativos" no menu Iniciar do Windows Mixed Reality se você criar um inicializador de aplicativo 3D para eles.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="2a2d7-121">Para fazer isso, crie um arquivo XML de [manifesto de elementos visuais](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) referenciando o iniciador do aplicativo 3D seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2a2d7-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="2a2d7-122">Crie um **arquivo glb do ativo do iniciador de aplicativo 3D** (consulte [modelagem e exportação](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="2a2d7-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="2a2d7-123">Crie um **[manifesto de elementos visuais](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="2a2d7-124">Você pode começar com o [exemplo abaixo](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="2a2d7-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="2a2d7-125">Consulte a documentação de [manifesto de elementos visuais](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) completos para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="2a2d7-126">Atualize **Square150x150Logo** e **SQUARE70X70LOGO** com um png/jpg/gif para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="2a2d7-127">Eles serão usados para o logotipo 2D do aplicativo na lista todos os aplicativos do Windows Mixed Reality e para o menu iniciar na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="2a2d7-128">O caminho do arquivo é relativo à pasta que contém o manifesto dos elementos visuais.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="2a2d7-129">Você ainda precisa fornecer um ícone do menu Iniciar do desktop para seu aplicativo por meio dos mecanismos padrão.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="2a2d7-130">Isso pode ser diretamente no executável ou no atalho que você criar (por exemplo, via IShellLink:: SetIconLocation).</span><span class="sxs-lookup"><span data-stu-id="2a2d7-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="2a2d7-131">*Adicional* Você pode usar um arquivo Resources. pri se desejar que o MRT forneça vários tamanhos de ativos para diferentes escalas de resolução e temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="2a2d7-132">Atualize o **caminho do MixedRealityModel** para apontar para o glb para o iniciador do aplicativo 3D</span><span class="sxs-lookup"><span data-stu-id="2a2d7-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="2a2d7-133">Salve o arquivo com o mesmo nome do arquivo executável, com uma extensão de ". VisualElementsManifest. xml "e salve-o no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="2a2d7-134">Por exemplo, para o arquivo executável "contoso. exe", o arquivo XML que o acompanha é denominado "contoso. visualelementsmanifest. xml".</span><span class="sxs-lookup"><span data-stu-id="2a2d7-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="2a2d7-135">**Adicione um atalho** ao seu aplicativo no menu Iniciar do Windows da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="2a2d7-136">Consulte o [exemplo abaixo](#sample-app-launcher-shortcut-creation) para obter uma C++ implementação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="2a2d7-137">Criá-lo em%ALLUSERSPROFILE%\Microsoft\Windows\Start Iniciar\programas (Machine) ou%APPDATA%\Microsoft\Windows\Start Iniciar\programas (User)</span><span class="sxs-lookup"><span data-stu-id="2a2d7-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="2a2d7-138">Se uma atualização alterar o manifesto dos elementos visuais ou os ativos referenciados por ele, o atualizador ou o instalador deverá atualizar o atalho de modo que o manifesto seja analisado e os ativos em cache sejam atualizados.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="2a2d7-139">*Adicional* Se o seu atalho de área de trabalho não apontar diretamente para o EXE do seu aplicativo (por exemplo, se ele invocar um manipulador de protocolo personalizado como "myapp://"), o menu Iniciar não localizará automaticamente o arquivo VisualElementsManifest. XML do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="2a2d7-140">Para resolver isso, o atalho deve especificar o caminho do arquivo do manifesto dos elementos visuais usando System. AppUserModel. VisualElementsManifestHintPath ().</span><span class="sxs-lookup"><span data-stu-id="2a2d7-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="2a2d7-141">Isso pode ser definido no atalho usando as mesmas técnicas que System.AppUserModel.ID.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="2a2d7-142">Não é necessário usar System.AppUserModel.ID, mas você pode fazer isso se desejar que o atalho corresponda à ID do modelo de usuário do aplicativo explícito, se um for usado.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="2a2d7-143">Consulte a seção [criação de atalho](#sample-app-launcher-shortcut-creation) do iniciador de aplicativo C++ de exemplo abaixo para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="2a2d7-144">Manifesto de elementos visuais de exemplo</span><span class="sxs-lookup"><span data-stu-id="2a2d7-144">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="2a2d7-145">Criação de atalho do iniciador de aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="2a2d7-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="2a2d7-146">O código de exemplo abaixo mostra como você pode criar um atalho C++no, incluindo a substituição do caminho para o arquivo XML de manifesto dos elementos visuais.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="2a2d7-147">Observe que a substituição só é necessária nos casos em que o atalho não aponta diretamente para o EXE associado ao manifesto (por exemplo,</span><span class="sxs-lookup"><span data-stu-id="2a2d7-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="2a2d7-148">o atalho usa um manipulador de protocolo personalizado como "myapp://").</span><span class="sxs-lookup"><span data-stu-id="2a2d7-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="2a2d7-149">Nova. Criação de atalho LNKC++()</span><span class="sxs-lookup"><span data-stu-id="2a2d7-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="2a2d7-150">Nova. Atalho do inicializador de URL</span><span class="sxs-lookup"><span data-stu-id="2a2d7-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="2a2d7-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a2d7-151">See also</span></span>

* <span data-ttu-id="2a2d7-152">[Exemplo de modelo de realidade misturada](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contém um iniciador de aplicativo 3D.</span><span class="sxs-lookup"><span data-stu-id="2a2d7-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="2a2d7-153">Diretrizes de projeto do inicializador de aplicativos 3D</span><span class="sxs-lookup"><span data-stu-id="2a2d7-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="2a2d7-154">Criando modelos 3D para uso na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2a2d7-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="2a2d7-155">Implementando iniciadores de aplicativos 3D (aplicativos UWP)</span><span class="sxs-lookup"><span data-stu-id="2a2d7-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="2a2d7-156">Como navegar na página inicial do Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2a2d7-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)

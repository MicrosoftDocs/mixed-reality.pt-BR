---
title: Usando o namespace do Windows com aplicativos do Unity para o HoloLens
description: Explica como fazer uso de APIs do WinRT em seu projeto do Unity para o HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, realidade do Windows Mixed, API, passo a passos
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548724"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="94813-104">Usando o namespace do Windows com aplicativos do Unity para o HoloLens</span><span class="sxs-lookup"><span data-stu-id="94813-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="94813-105">Esta página descreve como fazer uso de APIs do WinRT em seu projeto do Unity para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="94813-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="94813-106">Incluir condicionalmente chamadas à API do WinRT</span><span class="sxs-lookup"><span data-stu-id="94813-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="94813-107">As APIs do WinRT podem ser aproveitadas para projetos do Unity criados para o Plataforma Universal do Windows e para o Xbox One Platform; qualquer código que você escreve em scripts do Unity que visam APIs do WinRT deve ser incluído condicionalmente somente para as compilações.</span><span class="sxs-lookup"><span data-stu-id="94813-107">WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="94813-108">Isso pode ser feito por meio de duas etapas no Unity:</span><span class="sxs-lookup"><span data-stu-id="94813-108">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="94813-109">O nível de compatibilidade da API deve ser definido como **.net 4,6** ou **.net Standard 2,0** nas configurações do Player</span><span class="sxs-lookup"><span data-stu-id="94813-109">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="94813-110">**Editar** >  >    configurações do projeto nível de compatibilidade da API de configuração do Player para .NET 4,6 ou .net Standard 2,0 >  > </span><span class="sxs-lookup"><span data-stu-id="94813-110">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="94813-111">A diretiva de pré-processador **ENABLE_WINMD_SUPPORT** deve ser encapsulada em torno de qualquer código aproveitado por WinRT</span><span class="sxs-lookup"><span data-stu-id="94813-111">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="94813-112">O trecho de código a seguir é da página manual do [Unity para plataforma universal do Windows: API do WinRT C# em](http://docs.unity3d.com/Manual/windowsstore-scripts.html)scripts.</span><span class="sxs-lookup"><span data-stu-id="94813-112">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="94813-113">Neste exemplo, uma ID de anúncio é retornada, mas somente no UWP e no Xbox, uma compila:</span><span class="sxs-lookup"><span data-stu-id="94813-113">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="94813-114">Editar seus scripts em um projeto C# do Unity</span><span class="sxs-lookup"><span data-stu-id="94813-114">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="94813-115">Quando você clica duas vezes em um script no editor do Unity, ele inicia o script por padrão em um projeto do editor.</span><span class="sxs-lookup"><span data-stu-id="94813-115">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="94813-116">As APIs do WinRT parecerão desconhecidas, pois o projeto do Visual Studio não faz referência à Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="94813-116">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="94813-117">Além disso, a diretiva **ENALBE_WINMD_SUPPORT** será indefinida e qualquer *#if* código encapsulado será ignorado até que você compile seu projeto em uma solução UWP do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94813-117">Further, the **ENALBE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="94813-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94813-118">See also</span></span>
* [<span data-ttu-id="94813-119">Como exportar e criar uma solução do Visual Studio do Unity</span><span class="sxs-lookup"><span data-stu-id="94813-119">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="94813-120">Windows Runtime Unity de suporte</span><span class="sxs-lookup"><span data-stu-id="94813-120">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
---
title: Usando o namespace do Windows com aplicativos do Unity para HoloLens
description: Explica como usar APIs do WinRT no seu projeto do Unity para HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Passo a passo do Unity, WinRT, windows realidade misturada, API,
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589546"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="dddeb-104">Usando o namespace do Windows com aplicativos do Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="dddeb-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="dddeb-105">Esta página descreve como usar APIs do WinRT no seu projeto do Unity para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dddeb-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="dddeb-106">Incluir condicionalmente chamadas à API do WinRT</span><span class="sxs-lookup"><span data-stu-id="dddeb-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="dddeb-107">APIs do WinRT será usado apenas em builds de projeto do Unity que direcionam o Windows 8, Windows 8.1 ou a plataforma Universal do Windows; qualquer código que você escreve em scripts do Unity que tem como alvo a APIs do WinRT deve ser incluído condicionalmente para apenas esses builds.</span><span class="sxs-lookup"><span data-stu-id="dddeb-107">WinRT APIs will only be used in Unity project builds that target Windows 8, Windows 8.1, or the Universal Windows Platform; any code that you write in Unity scripts that targets WinRT APIs must be conditionally included for only those builds.</span></span> <span data-ttu-id="dddeb-108">Isso é feito usando as definições de pré-processador NETFX_CORE ou WINDOWS_UWP.</span><span class="sxs-lookup"><span data-stu-id="dddeb-108">This is done using the NETFX_CORE or WINDOWS_UWP preprocessor definitions.</span></span> <span data-ttu-id="dddeb-109">Essa regra se aplica ao uso de instruções, bem como outro código.</span><span class="sxs-lookup"><span data-stu-id="dddeb-109">This rule applies to using statements, as well as other code.</span></span>

<span data-ttu-id="dddeb-110">O trecho de código a seguir é da página de manual do Unity para [plataforma Universal do Windows: API do WinRT no C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="dddeb-110">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="dddeb-111">Neste exemplo, uma ID de anúncio for retornado, mas somente no Windows 8.0 ou superior destino compilações:</span><span class="sxs-lookup"><span data-stu-id="dddeb-111">In this example, an advertising ID is returned, but only on Windows 8.0 or higher target builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="dddeb-112">Editar seus scripts em um Unity C# projeto</span><span class="sxs-lookup"><span data-stu-id="dddeb-112">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="dddeb-113">Quando você clica duas vezes um script no editor do Unity, ele por padrão iniciará o script em um projeto do editor.</span><span class="sxs-lookup"><span data-stu-id="dddeb-113">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="dddeb-114">As APIs do WinRT parecerá ser desconhecido por dois motivos: NETFX_CORE não está definido nesse ambiente, e o projeto não faz referência a tempo de execução do Windows.</span><span class="sxs-lookup"><span data-stu-id="dddeb-114">The WinRT APIs will appear to be unknown for two reasons: NETFX_CORE is not defined in this environment, and the project does not reference the Windows Runtime.</span></span> <span data-ttu-id="dddeb-115">Se você usar o [recomendado de exportação e criado as configurações de](exporting-and-building-a-unity-visual-studio-solution.md)e editar os scripts nesse projeto em vez disso, ele será definir NETFX_CORE e também incluir uma referência para o tempo de execução do Windows; com essa configuração em vigor, APIs do WinRT será disponível para o IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="dddeb-115">If you use the [recommended export and built settings](exporting-and-building-a-unity-visual-studio-solution.md), and edit the scripts in that project instead, it will define NETFX_CORE and also include a reference to the Windows Runtime; with this configuration in place, WinRT APIs will be available for IntelliSense.</span></span>

<span data-ttu-id="dddeb-116">Observe que o Unity C# projeto também pode ser usado para depurar por meio de seus scripts usando F5 no Visual Studio de depuração remota.</span><span class="sxs-lookup"><span data-stu-id="dddeb-116">Note that your Unity C# project can also be used to debug through your scripts using F5 remote debugging in Visual Studio.</span></span> <span data-ttu-id="dddeb-117">Se você não vir a trabalhar na primeira vez que você abre a Unity do IntelliSense C# do projeto, feche o projeto e abra-o novamente.</span><span class="sxs-lookup"><span data-stu-id="dddeb-117">If you do not see IntelliSense working the first time that you open your Unity C# project, close the project and re-open it.</span></span> <span data-ttu-id="dddeb-118">IntelliSense deve começar a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="dddeb-118">IntelliSense should start working.</span></span>

## <a name="see-also"></a><span data-ttu-id="dddeb-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dddeb-119">See also</span></span>
* [<span data-ttu-id="dddeb-120">Exportando e criando uma solução do Visual Studio do Unity</span><span class="sxs-lookup"><span data-stu-id="dddeb-120">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)

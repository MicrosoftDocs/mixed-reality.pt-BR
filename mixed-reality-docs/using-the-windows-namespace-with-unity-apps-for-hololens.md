---
title: APIs do WinRT com Unity para HoloLens
description: Explica como fazer uso de APIs do WinRT (o namespace do Windows) em seu projeto do Unity para o HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, realidade do Windows Mixed, API, passo a passos
ms.openlocfilehash: 73764d191813f6dcae750e74ce3181af987c9e0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437237"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>APIs do WinRT com Unity para HoloLens

Esta página descreve como fazer uso de APIs do WinRT em seu projeto do Unity para o HoloLens.

## <a name="mixed-reality-apis"></a>APIs de realidade misturada

Um subconjunto focado na realidade misturada do SDK do Windows foi disponibilizado em uma projeção compatível com .NET Standard 2,0, que pode ser usada em seu projeto sem diretivas de pré-processador. Isso inclui a maioria das APIs nos namespaces Windows. percepção e Windows. UI. Input. espaciais e pode expandir para incluir APIs adicionais no futuro. As APIs projetadas podem ser usadas durante a execução no editor, o que permite o uso do [modo de reprodução](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode). Para usar essa projeção, faça as seguintes modificações em seu projeto:

1) Adicione uma referência ao pacote NuGet [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) usando o [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Referências de prefixo ao namespace `Windows` com `Microsoft.`:
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Substitua as conversões de ponteiro nativo por `FromNativePtr`:
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Incluir condicionalmente chamadas à API do WinRT

Como alternativa, as APIs do WinRT podem ser aproveitadas para projetos do Unity criados para o Plataforma Universal do Windows e o Xbox One Platform usando diretivas de pré-processador; qualquer código que você escreve em scripts do Unity que visam APIs do WinRT deve ser incluído condicionalmente somente para as compilações. 

Isso pode ser feito por meio de duas etapas no Unity:
1) O nível de compatibilidade da API deve ser definido como **.net 4,6** ou **.net Standard 2,0** nas configurações do Player
    - **Editar** **configurações do projeto** >  > **Player** > **configuração** > nível de **compatibilidade da API** para **.NET 4,6** ou **.net Standard 2,0**
2) A diretiva de pré-processador **ENABLE_WINMD_SUPPORT** deve ser encapsulada em torno de qualquer código aproveitado por WinRT

O trecho de código a seguir é da página manual do Unity para [plataforma universal do Windows: API C# do WinRT em scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html). Neste exemplo, uma ID de anúncio é retornada, mas somente no UWP e no Xbox, uma compila:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Editar seus scripts em um projeto C# do Unity

Quando você clica duas vezes em um script no editor do Unity, ele inicia o script por padrão em um projeto do editor. As APIs do WinRT parecerão desconhecidas, pois o projeto do Visual Studio não faz referência à Windows Runtime. Além disso, a diretiva **ENABLE_WINMD_SUPPORT** será indefinida e qualquer *#if* código encapsulado será ignorado até que você compile seu projeto em uma solução UWP do Visual Studio.

## <a name="see-also"></a>Consulte também
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Runtime Unity de suporte](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)

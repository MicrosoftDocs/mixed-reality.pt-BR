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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Usando o namespace do Windows com aplicativos do Unity para o HoloLens

Esta página descreve como fazer uso de APIs do WinRT em seu projeto do Unity para o HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Incluir condicionalmente chamadas à API do WinRT

As APIs do WinRT podem ser aproveitadas para projetos do Unity criados para o Plataforma Universal do Windows e para o Xbox One Platform; qualquer código que você escreve em scripts do Unity que visam APIs do WinRT deve ser incluído condicionalmente somente para as compilações. 

Isso pode ser feito por meio de duas etapas no Unity:
1) O nível de compatibilidade da API deve ser definido como **.net 4,6** ou **.net Standard 2,0** nas configurações do Player
    - **Editar** >  >    configurações do projeto nível de compatibilidade da API de configuração do Player para .NET 4,6 ou .net Standard 2,0 >  > 
2) A diretiva de pré-processador **ENABLE_WINMD_SUPPORT** deve ser encapsulada em torno de qualquer código aproveitado por WinRT

O trecho de código a seguir é da página manual do [Unity para plataforma universal do Windows: API do WinRT C# em](http://docs.unity3d.com/Manual/windowsstore-scripts.html)scripts. Neste exemplo, uma ID de anúncio é retornada, mas somente no UWP e no Xbox, uma compila:

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

Quando você clica duas vezes em um script no editor do Unity, ele inicia o script por padrão em um projeto do editor. As APIs do WinRT parecerão desconhecidas, pois o projeto do Visual Studio não faz referência à Windows Runtime. Além disso, a diretiva **ENALBE_WINMD_SUPPORT** será indefinida e qualquer *#if* código encapsulado será ignorado até que você compile seu projeto em uma solução UWP do Visual Studio.

## <a name="see-also"></a>Consulte também
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Runtime Unity de suporte](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
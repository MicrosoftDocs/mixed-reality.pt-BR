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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Usando o namespace do Windows com aplicativos do Unity para HoloLens

Esta página descreve como usar APIs do WinRT no seu projeto do Unity para HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Incluir condicionalmente chamadas à API do WinRT

APIs do WinRT será usado apenas em builds de projeto do Unity que direcionam o Windows 8, Windows 8.1 ou a plataforma Universal do Windows; qualquer código que você escreve em scripts do Unity que tem como alvo a APIs do WinRT deve ser incluído condicionalmente para apenas esses builds. Isso é feito usando as definições de pré-processador NETFX_CORE ou WINDOWS_UWP. Essa regra se aplica ao uso de instruções, bem como outro código.

O trecho de código a seguir é da página de manual do Unity para [plataforma Universal do Windows: API do WinRT no C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html). Neste exemplo, uma ID de anúncio for retornado, mas somente no Windows 8.0 ou superior destino compilações:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Editar seus scripts em um Unity C# projeto

Quando você clica duas vezes um script no editor do Unity, ele por padrão iniciará o script em um projeto do editor. As APIs do WinRT parecerá ser desconhecido por dois motivos: NETFX_CORE não está definido nesse ambiente, e o projeto não faz referência a tempo de execução do Windows. Se você usar o [recomendado de exportação e criado as configurações de](exporting-and-building-a-unity-visual-studio-solution.md)e editar os scripts nesse projeto em vez disso, ele será definir NETFX_CORE e também incluir uma referência para o tempo de execução do Windows; com essa configuração em vigor, APIs do WinRT será disponível para o IntelliSense.

Observe que o Unity C# projeto também pode ser usado para depurar por meio de seus scripts usando F5 no Visual Studio de depuração remota. Se você não vir a trabalhar na primeira vez que você abre a Unity do IntelliSense C# do projeto, feche o projeto e abra-o novamente. IntelliSense deve começar a trabalhar.

## <a name="see-also"></a>Consulte também
* [Exportando e criando uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)

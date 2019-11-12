---
title: Visão geral de desenvolvimento do DirectX
description: Crie um mecanismo de realidade misturada baseado em DirectX usando as APIs de realidade mista do Windows diretamente.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, renderização Holographic, nativo, aplicativo nativo, WinRT, aplicativo WinRT, APIs de plataforma, mecanismo personalizado, middleware
ms.openlocfilehash: 0af73314c3c93d230ef87ed468f718f5b3e1813c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926626"
---
# <a name="directx-development-overview"></a>Visão geral de desenvolvimento do DirectX


Os aplicativos do Windows Mixed Reality usam as APIs de [renderização Holographic](rendering.md), [olhar](gaze-and-commit.md), [gesto](gaze-and-commit.md#composite-gestures), [controlador de movimento](motion-controllers.md), [voz](voice-input.md)e [mapeamento espacial](spatial-mapping.md) para criar experiências de [realidade misturadas](mixed-reality.md) para o HoloLens e headsets de imersão. Você pode criar aplicativos de realidade misturada usando um mecanismo 3D, como o [Unity](unity-development-overview.md), ou pode codificar diretamente as APIs de realidade mista do Windows usando DirectX 11 ou DirectX 12. Se você estiver aproveitando a plataforma diretamente, será basicamente criar seu próprio middleware ou estrutura. As APIs do Windows dão suporte a aplicativos C++ escritos C#no e no. Se você optar por usar C#o, seu aplicativo poderá aproveitar a biblioteca de software de código aberto [SharpDX](https://sharpdx.org/) .


O Windows Mixed Reality dá suporte a [dois tipos de aplicativos](app-views.md):
* **Aplicativos de realidade misturada** (UWP ou Win32) que usam a [API HolographicSpace](getting-a-holographicspace.md) para renderizar uma [exibição de imersão](app-views.md) para o usuário que preenche a tela do headset.
* **aplicativos 2D** (UWP) que usam DirectX, XAML ou outras estruturas para renderizar [exibições 2D](app-views.md#2d-views) em slates na página inicial do Windows Mixed Reality.


As diferenças entre o desenvolvimento do DirectX para [exibições 2D e de imersão](app-views.md) estão relacionadas principalmente à renderização Holographic e à entrada espacial. O [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) do seu aplicativo UWP ou o HWND do seu aplicativo Win32 são necessários e permanecem basicamente os mesmos, assim como as APIs do WinRT disponíveis para seu aplicativo. No entanto, você deve usar um subconjunto diferente dessas APIs para aproveitar os recursos do Holographic. Por exemplo, a cadeia de permuta é gerenciada pelo sistema para aplicativos Holographic. Você trabalha com a API HolographicSpace em vez de DXGI para [apresentar os quadros](rendering-in-directx.md).

Para começar a desenvolver aplicativos de imersão:
* Para **aplicativos UWP**, [crie um novo projeto UWP usando os modelos no Visual Studio](creating-a-holographic-directx-project.md). Com base em seu idioma **, C++ Visual** ou **Visual C#** , você pode encontrar os modelos UWP no **Windows universal** > **Holographic**.
* Para **aplicativos Win32**, [inicie no exemplo do *BasicHologram* Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Essa é uma ótima maneira de obter o código de que você precisa para adicionar suporte à renderização de Holographic a um aplicativo ou mecanismo existente. O código e os conceitos são apresentados no modelo de uma forma que seja familiar para qualquer desenvolvedor de software interativo em tempo real.


## <a name="getting-started"></a>Introdução

Os tópicos a seguir abordam os requisitos básicos da adição do suporte do Windows Mixed Reality ao middleware baseado em DirectX:

* [Criando um projeto Holographic DirectX](creating-a-holographic-directx-project.md): o modelo de aplicativo Holographic, juntamente com a documentação, mostra as diferenças entre o que você está acostumado, bem como os requisitos especiais apresentados por um dispositivo que foi projetado para funcionar ao descansar em sua cabeça.
* [Obtendo um HolographicSpace](getting-a-holographicspace.md): primeiro, você precisará criar um HolographicSpace que fornecerá ao seu aplicativo a sequência de objetos HolographicFrame que representam cada posição de cabeçalho da qual você processará.
* [Renderização no DirectX](rendering-in-directx.md): como uma cadeia de permuta Holographic tem dois destinos de renderização, você precisará fazer algumas alterações na forma como seu aplicativo é renderizado.
* [Coordenar sistemas no DirectX](coordinate-systems-in-directx.md): a realidade mista do Windows aprende e atualiza sua compreensão do mundo à medida que o usuário percorra. Isso fornece sistemas de coordenadas espaciais que os aplicativos usam para o motivo do ambiente do usuário, incluindo âncoras espaciais e o estágio espacial definido do usuário.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Adicionando entradas e recursos de realidade misturada

Para habilitar a melhor experiência possível para os usuários do seu aplicativo de imersão, você desejará dar suporte aos seguintes blocos de construção:

* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)
* [Som espacial](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)


Há outros recursos principais que muitos aplicativos de imersão desejarão usar que também são expostos aos aplicativos do DirectX:

* [Âncoras espaciais compartilhadas no DirectX](shared-spatial-anchors-in-directx.md)
* [Teclado, mouse e entrada do controlador no DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Consulte também
* [Modelo de aplicativo](app-model.md)
* [Modos de exibição do aplicativo](app-views.md)

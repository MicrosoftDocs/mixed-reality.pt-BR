---
title: Visão geral de desenvolvimento do DirectX
description: Criando diretamente um mecanismo de realidade misturada baseado em DirectX usando as APIs de realidade mista do Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, renderização Holographic, nativo, aplicativo nativo, WinRT, aplicativo WinRT, APIs de plataforma, mecanismo personalizado, middleware
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414379"
---
# <a name="directx-development-overview"></a>Visão geral de desenvolvimento do DirectX


Os aplicativos do Windows Mixed Reality usam as APIs de [renderização Holographic](rendering.md), [olhar](gaze.md), [gesto](gestures.md), [controlador de movimento](motion-controllers.md), [voz](voice-input.md)e [mapeamento espacial](spatial-mapping.md) para criar experiências de [realidade misturadas](mixed-reality.md) para o HoloLens e headsets de imersão. Você pode criar aplicativos de realidade misturada usando um mecanismo 3D, como o [Unity](unity-development-overview.md), ou pode codificar diretamente as APIs de realidade mista do Windows usando DirectX 11 ou DirectX 12. Se você estiver aproveitando a plataforma diretamente, será basicamente criar seu próprio middleware ou estrutura. As APIs do Windows dão suporte a aplicativos C++ escritos C#no e no. Se você optar por usar C#o, seu aplicativo poderá aproveitar a biblioteca de software de código aberto [SharpDX](http://sharpdx.org/) .


O Windows Mixed Reality dá suporte a [dois tipos de aplicativos](app-views.md):
* **Aplicativos de realidade misturada** (UWP ou Win32) que usam a [API HolographicSpace](getting-a-holographicspace.md) para renderizar uma [exibição de imersão](app-views.md) para o usuário que preenche a tela do headset.
* **aplicativos 2D** (UWP) que usam DirectX, XAML ou outras estruturas para renderizar [exibições 2D](app-views.md#2d-views) em slates na página inicial do Windows Mixed Reality.


As diferenças entre o desenvolvimento do DirectX para [exibições 2D e de imersão](app-views.md) estão relacionadas principalmente à renderização Holographic e à entrada espacial. O [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) do seu aplicativo UWP ou o HWND do seu aplicativo Win32 são necessários e permanecem basicamente os mesmos, assim como as APIs do WinRT disponíveis para seu aplicativo. No entanto, você deve usar um subconjunto diferente dessas APIs para aproveitar os recursos do Holographic. Por exemplo, a cadeia de permuta é gerenciada pelo sistema para Holographic appslications. Você trabalha com a API HolographicSpace em vez de DXGI para [apresentar os quadros](rendering-in-directx.md).

Para começar a desenvolver aplicativos de imersão:
* Para **aplicativos UWP**, [crie um novo projeto UWP usando os modelos no Visual Studio](creating-a-holographic-directx-project.md). Com base em seu idioma **, C++ Visual** ou **Visual C#** , você pode encontrar os modelos UWP no **Windows universal** > **Holographic**.
* Para **aplicativos Win32**, [inicie no exemplo do *BasicHologram* Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Essa é uma ótima maneira de obter o código de que você precisa para adicionar suporte à renderização de Holographic a um aplicativo ou mecanismo existente. O código e os conceitos são apresentados no modelo de uma forma que seja familiar para qualquer desenvolvedor de software interativo em tempo real.


## <a name="getting-started"></a>Introdução

Os tópicos a seguir abordam os requisitos básicos da adição do suporte do Windows Mixed Reality ao middleware baseado em DirectX:

* [Criando um projeto do DirectX Holographic](creating-a-holographic-directx-project.md): O modelo de aplicativo Holographic, juntamente com a documentação, mostra as diferenças entre o que você está acostumado, bem como os requisitos especiais apresentados por um dispositivo que é projetado para funcionar enquanto estiver em sua cabeça.
* [Obtendo um HolographicSpace](getting-a-holographicspace.md): Primeiro, você precisará criar um HolographicSpace que fornecerá ao seu aplicativo a sequência de objetos HolographicFrame que representam cada posição de cabeçalho da qual você processará.
* [Renderização no DirectX](rendering-in-directx.md): Como uma cadeia de permuta Holographic tem dois destinos de renderização, você precisará fazer algumas alterações na maneira como seu aplicativo é renderizado.
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md): A realidade mista do Windows aprende e atualiza sua compreensão do mundo à medida que o usuário percorra. Isso fornece sistemas de coordenadas espaciais que os aplicativos usam para o motivo do ambiente do usuário, incluindo âncoras espaciais e o estágio espacial definido do usuário.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Adicionando entradas e recursos de realidade misturada

Para habilitar a melhor experiência possível para os usuários de sua appslication de imersão, você desejará dar suporte aos seguintes blocos de construção:

* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)
* [Som espacial no DirectX](spatial-sound-in-directx.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)


Há outros recursos principais que muitos aplicativos de imersão desejarão usar que também são expostos aos aplicativos do DirectX:

* [Âncoras espaciais compartilhadas no DirectX](shared-spatial-anchors-in-directx.md)
* [Câmera localizável no DirectX](locatable-camera-in-directx.md)
* [Teclado, mouse e entrada do controlador no DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Consulte também
* [Modelo de aplicativo](app-model.md)
* [Modos de exibição do aplicativo](app-views.md)

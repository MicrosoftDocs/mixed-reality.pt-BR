---
title: Visão geral de desenvolvimento do DirectX
description: Criando um mecanismo de realidade misturada baseado no DirectX usando as APIs de realidade mista do Windows diretamente.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Renderização de DirectX, holográfico, nativo aplicativo nativo, WinRT, aplicativo do WinRT, as APIs da plataforma, o mecanismo personalizado, middleware
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414379"
---
# <a name="directx-development-overview"></a>Visão geral de desenvolvimento do DirectX


Aplicativos de realidade mista do Windows usam o [renderização holográfica](rendering.md), [olhares](gaze.md), [gesto](gestures.md), [controlador movimento](motion-controllers.md), [voz](voice-input.md), e [mapeamento espacial](spatial-mapping.md) APIs para compilar [realidade misturada](mixed-reality.md) experiências para HoloLens e fones imersivos em exposição. Você pode criar aplicativos de realidade misturada usando um mecanismo 3D, como [Unity](unity-development-overview.md), ou você pode codificar diretamente para as APIs de realidade mista do Windows usando DirectX 11 ou DirectX 12. Se você está aproveitando a plataforma diretamente, você estará essencialmente criando seu próprio middleware ou estrutura. As APIs do Windows oferecem suporte a aplicativos escritos em ambos os C++ e C#. Se você optar por usar C#, seu aplicativo pode aproveitar o [SharpDX](http://sharpdx.org/) biblioteca de software livre.


Dá suporte ao Windows Mixed Reality [dois tipos de aplicativos](app-views.md):
* **Misto aplicativos de realidade** (UWP ou Win32) que usam o [API HolographicSpace](getting-a-holographicspace.md) para renderizar um [exibição imersiva](app-views.md) ao usuário que preenche a exibição de fone de ouvido.
* **Aplicativos 2D** (UWP) que usam outras estruturas, XAML ou DirectX para renderizar [modos de exibição 2D](app-views.md#2d-views) em slates no Windows Mixed Reality inicial.


As diferenças entre o desenvolvimento do DirectX para [modos de exibição 2D e envolventes](app-views.md) estão principalmente relacionados ao holographic renderização e entrada espacial. Seu aplicativo de UWP [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) ou HWND do seu aplicativo Win32 são necessário e permanecem basicamente os mesmos, assim como as APIs do WinRT disponíveis para seu aplicativo. No entanto, você deve usar um subconjunto diferente dessas APIs para tirar proveito dos recursos holographic. Por exemplo, a cadeia de troca é gerenciada pelo sistema para appslications holographic. Você trabalha com a API HolographicSpace em vez de DXGI para [apresentar quadros](rendering-in-directx.md).

Para começar a desenvolver aplicativos imersivos:
* Para **aplicativos da UWP**, [criar um novo projeto UWP usando os modelos do Visual Studio](creating-a-holographic-directx-project.md). Com base em sua linguagem **Visual C++**  ou **Visual C#** , você pode encontrar os modelos da UWP sob **Windows Universal**  >   **Holographic**.
* Para **aplicativos Win32**, [desde o *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).

Isso é uma ótima maneira de obter o código que você precisa adicionar suporte à renderização holográfica a um aplicativo ou mecanismo existente. Código e os conceitos são apresentados no modelo de forma que seja familiar para qualquer desenvolvedor de software interativo em tempo real.


## <a name="getting-started"></a>Introdução

Os tópicos a seguir discutem os requisitos de base da adição de suporte do Windows Mixed Reality ao middleware baseado no DirectX:

* [Criando um projeto de DirectX holográfico](creating-a-holographic-directx-project.md): O modelo de aplicativo holográfica juntamente com a documentação mostra as diferenças entre o que você está acostumado, bem como os requisitos especiais introduzidos por um dispositivo que foi projetado para funcionar pairando sobre sua cabeça.
* [Obtendo um HolographicSpace](getting-a-holographicspace.md): Primeiro, você precisará criar um HolographicSpace que fornecerá o seu aplicativo a sequência de objetos HolographicFrame que representam cada posição principal do qual serão renderizados.
* [Processamento no DirectX](rendering-in-directx.md): Como uma cadeia de troca holográfica tem dois destinos de renderização, você precisará fazer algumas alterações na maneira como seu aplicativo renderizar.
* [Sistemas de coordenadas no DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality aprende e atualiza seu conhecimento sobre o do mundo como os usuários se deslocam ao redor. Isso fornece sistemas de coordenadas espaciais que os aplicativos usam para pensar sobre o ambiente do usuário, incluindo âncoras espaciais e do usuário definido pelo estágio espacial.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Adicionando recursos de realidade mista e entradas

Para habilitar a melhor experiência possível para usuários do seu appslication imersivo, você desejará dar suporte os seguintes blocos de construção principais:

* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)
* [Som espacial no DirectX](spatial-sound-in-directx.md)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)


Há outros recursos importantes que muitos aplicativos imersivos vai querer usar que também são expostos a aplicativos de DirectX:

* [Âncoras espaciais compartilhadas no DirectX](shared-spatial-anchors-in-directx.md)
* [Câmera localizável no DirectX](locatable-camera-in-directx.md)
* [Teclado, mouse e entrada do controlador no DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>Consulte também
* [Modelo de aplicativo](app-model.md)
* [Modos de exibição do aplicativo](app-views.md)

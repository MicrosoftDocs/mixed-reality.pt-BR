---
title: Visão geral do desenvolvimento nativo
description: Crie um mecanismo de realidade mista com base em DirectX usando as APIs de realidade mista do Windows diretamente.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, renderização Holographic, nativo, aplicativo nativo, WinRT, aplicativo WinRT, APIs de plataforma, mecanismo personalizado, middleware
ms.openlocfilehash: 5c61739ea6c90b4547c5c9927cf2129304650926
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80159985"
---
# <a name="native-development-overview"></a>Visão geral do desenvolvimento nativo

Os aplicativos do Windows Mixed Reality usam as seguintes APIs para criar experiências de [realidade mista](mixed-reality.md) para o HoloLens e outros headsets de imersão:

 - [Renderização holográfica](rendering.md)
 - [Foco](gaze-and-commit.md)
 - [Gesture](gaze-and-commit.md#composite-gestures)
 - [Controlador de movimento](motion-controllers.md)
 - [Voz](voice-input.md)
 - [Mapeamento espacial](spatial-mapping.md)

Você pode criar aplicativos de realidade misturada usando um mecanismo 3D, como o [Unity](unity-development-overview.md). Ou você pode codificar diretamente para as APIs de realidade mista do Windows usando DirectX 11 ou DirectX 12. Se você aproveitar a plataforma diretamente, você essencialmente criará seu próprio middleware ou estrutura. As APIs do Windows dão suporte a aplicativos que são C++ gravados no e C#no. Se você usar C#o, seu aplicativo poderá aproveitar a biblioteca de software de código aberto [SharpDX](https://sharpdx.org/) .

O Windows Mixed Reality dá suporte a [dois tipos de aplicativos](app-views.md):
* **Aplicativos de realidade mista** (UWP ou Win32) que usam a API do [HOLOGRAPHICSPACE](getting-a-holographicspace.md) ou a [API do OpenXR](openxr.md) para processar uma exibição de [imersão](app-views.md) para o usuário que preenche a tela do headset
* **aplicativos 2D** (UWP) que usam DirectX, XAML ou outra estrutura para renderizar [exibições 2D](app-views.md#2d-views) em slates na página inicial do Windows Mixed Reality

As diferenças entre o desenvolvimento DirectX para [exibições 2D e exibições de imersão](app-views.md) envolvem principalmente a renderização Holographic e a entrada espacial. O [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) do seu aplicativo UWP ou o HWND do seu aplicativo Win32 são necessários e permanecem basicamente os mesmos. O mesmo é verdadeiro para as APIs do WinRT que estão disponíveis para seu aplicativo. Mas você deve usar um subconjunto diferente dessas APIs para aproveitar os recursos do Holographic. Por exemplo, o SwapChain e o quadro presente são gerenciados pelo sistema para aplicativos Holographic a fim de habilitar um loop de quadro previsto para pose.

## <a name="get-started-with-openxr"></a>Introdução ao OpenXR

Você pode desenvolver usando OpenXR em um headset de imersão de realidade 2 ou Windows misto na área de trabalho.  Se você não tiver acesso a um headset, poderá usar o emulador do HoloLens 2 ou o simulador de realidade mista do Windows.

Para começar a desenvolver aplicativos OpenXR para fones de ouvido do Windows com o HoloLens 2 ou de imersão, consulte como começar a usar [o desenvolvimento do OpenXR](openxr-getting-started.md).

## <a name="get-started-with-winrt"></a>Introdução ao WinRT

Para começar a desenvolver aplicativos de imersão:
* Para **aplicativos UWP**, [use os modelos no Visual Studio para criar um novo projeto UWP](creating-a-holographic-directx-project.md). Com base em seu idioma, C++ Visual ou C#Visual, encontre os modelos UWP no **Windows universal** > **Holographic**.
* Para **aplicativos Win32**, [inicie no exemplo do *BasicHologram* Win32](creating-a-holographic-directx-project.md#creating-a-win32-project).

Esta etapa é uma ótima maneira de obter o código de que você precisa para adicionar suporte à renderização de Holographic a um aplicativo ou mecanismo existente. O código e os conceitos são apresentados no modelo de uma forma que seja familiar para qualquer desenvolvedor de software interativo em tempo real.

Os tópicos a seguir descrevem os requisitos básicos ao adicionar o suporte do Windows Mixed Reality ao middleware baseado em DirectX.

* [Criar um projeto Holographic DirectX](creating-a-holographic-directx-project.md): o modelo de aplicativo Holographic junto com a documentação mostra as diferenças em comparação com o que você está acostumado. Ele também descreve os requisitos especiais para um dispositivo que é projetado para funcionar enquanto estiver em sua cabeça.
* [Obtenha um HolographicSpace](getting-a-holographicspace.md): primeiro, você precisa criar um HolographicSpace que dá ao seu aplicativo a sequência de objetos HolographicFrame que representam cada posição de cabeçalho da qual você vai renderizar.
* [Renderizar no DirectX](rendering-in-directx.md): como um Holographic SwapChain tem dois destinos de renderização, você deve fazer algumas alterações na maneira como seu aplicativo é renderizado.
* [Coordenar sistemas no DirectX](coordinate-systems-in-directx.md): a realidade mista do Windows aprende e atualiza sua compreensão do mundo à medida que o usuário percorra. Isso fornece sistemas de coordenadas espaciais que os aplicativos usam para o motivo do ambiente do usuário, incluindo âncoras espaciais e o estágio espacial definido do usuário.

## <a name="add-mixed-reality-capabilities-and-inputs"></a>Adicionar funcionalidades e entradas de realidade misturada

Para fornecer a melhor experiência possível para os usuários do seu aplicativo de imersão, você deve dar suporte aos seguintes blocos de construção de chave:

* [Olhar fixo com cabeça e olhos no DirectX](gaze-in-directx.md)
* [Controladores de mãos e emovimento no DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)
* [Som espacial](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [Mapeamento espacial no DirectX](spatial-mapping-in-directx.md)

Esses são outros recursos principais que muitos aplicativos de imersão usam que também são expostos aos aplicativos do DirectX:

* [Âncoras espaciais compartilhadas no DirectX](shared-spatial-anchors-in-directx.md)
* [Teclado, mouse e entrada do controlador no DirectX](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a>Consulte também
* [Modelo de aplicativo](app-model.md)
* [Modos de exibição do aplicativo](app-views.md)

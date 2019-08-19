---
title: Visão geral do desenvolvimento
description: Este artigo descreve os blocos de construção básicos do desenvolvimento de um aplicativo do Windows Mixed Reality.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: introdução, noções básicas, HoloLens, HoloLens 2, headsets de imersão, Unity, Visual Studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873985"
---
# <a name="development-overview"></a>Visão geral do desenvolvimento

Aplicativos de realidade misturada podem ser desenvolvidos usando uma variedade de tecnologias de desenvolvedor.  O HoloLens executa aplicativos criados com o [plataforma universal do Windows](https://dev.windows.com/getstarted).  Os headsets de imersão executam Plataforma Universal do Windows aplicativos, bem como aplicativos Win32.
Ao se familiarizar com ferramentas de middleware como o Unity, você pode começar a criar experiências de realidade misturadas hoje mesmo.  Aproveite o kit de [ferramentas de realidade misturada](install-the-tools.md) de software livre para começar rapidamente.
Os <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">serviços de realidade misturada</a>, como âncoras espaciais <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">do Azure</a>, têm SDKs que podem se integrar a várias tecnologias de desenvolvedor de plataforma cruzada também.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Conceitos básicos do desenvolvimento de realidade misturada

As experiências de [realidade misturada](mixed-reality.md) são possibilitadas pelos novos recursos do Windows para noção ambiental. Elas permitem que os desenvolvedores coloquem um [holograma](hologram.md) no mundo real e que os usuários percorram os mundos digitais literalmente caminhando. 

Estes são os blocos principais de construção para o desenvolvimento da realidade misturada:

<table>
<tr>
<th>Entrada</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> <a href="gaze.md">Foco da cabeça</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Foco com o olhar</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Mãos/ <a href="gestures.md">gestos</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voz</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Controladores de movimentos</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Percepção e recursos espaciais</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Coordenadas mundiais</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Som espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Mapeamento espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



O modelo de interação básico do [HoloLens](hololens-hardware-details.md) se baseia em [foco ocular](gaze.md), [gestos](gestures.md) e [vozes](voice-input.md), às vezes chamados de *GGV* . [Os headsets imersivos do Windows Mixed Reality](immersive-headset-hardware-details.md) também usam foco ocular e vozes, mas usam os [controladores de movimento](motion-controllers.md) para os gestos.


Todos os dispositivos de realidade misturada no Windows se beneficiam do ecossistema de entrada disponível para o Windows, incluindo mouse, teclado, gamepads e muito mais. Com o HoloLens, os [acessórios de hardware](hardware-accessories.md) são conectados por Bluetooth. Com os headsets imersivos, os acessórios se conectam ao computador host por Bluetooth, USB e outros protocolos compatíveis.

Os recursos de noção ambiental, como as [coordenadas](coordinate-systems.md), o [som espacial](spatial-sound.md) e o [mapeamento espacial](spatial-mapping.md), fornecem os recursos necessários para misturar a realidade. O mapeamento espacial é exclusivo do HoloLens e permite que os hologramas interajam com o usuário e o mundo físico ao redor deles. Os sistemas de coordenadas permitem que o movimento do usuário afete o movimento no mundo digital.

Os [hologramas](hologram.md) são compostos de luz e som, o que depende da [renderização Holographic](rendering.md). Ter noções básicas sobre a experiência de colocação e persistência, conforme demonstrado no [Windows Mixed Reality doméstico](navigating-the-windows-mixed-reality-home.md) (às vezes chamado de "shell") é uma ótima maneira de projetar-se na experiência do usuário.

## <a name="tools-for-developing-for-mixed-reality"></a>Ferramentas para o desenvolvimento de realidade misturada

As ferramentas utilizadas dependerão do [estilo do aplicativo](app-views.md) que você deseja compilar.
* Os [aplicativos com exibição 2D](building-2d-apps.md) utilizam as ferramentas para criar aplicativos da plataforma universal do Windows adequados para ambientes como tablets, computadores e Windows Phone. A experiência desses aplicativos ocorre como projeções 2D colocadas no Windows Mixed Reality doméstico e podem funcionar em vários tipos de dispositivos (incluindo telefones e computadores).
* Os aplicativos imersivos e holográficos precisam de ferramentas projetadas para tirar proveito das APIs do Windows Mixed Reality. [Recomendamos usar o Unity](unity-development-overview.md) para criar aplicativos de realidade misturada. Os desenvolvedores interessados em criar seus próprios mecanismos podem [usar DirectX e outras APIs do Windows](directx-development-overview.md).

Seja qual for o tipo de aplicativo que você esteja compilando, essas ferramentas facilitarão a sua experiência de desenvolvimento:
* [Visual Studio e o Windows SDK](using-visual-studio.md)
* [Portal de Dispositivos do Windows](using-the-windows-device-portal.md)
* [Emulador do HoloLens](using-the-hololens-emulator.md) (Emulador do HoloLens 2 em breve)
* [Simulador do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Critérios de qualidade do aplicativo](app-quality-criteria.md)

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Serviços de realidade misturada</a>
* [Tutoriais de realidade misturada](tutorials.md)
* [Projetos de código-fonte aberto](open-source-projects.md)
* [Noções básicas do MR 100: introdução ao Unity](holograms-100.md)
* [Diretrizes mínimas de compatibilidade de hardware do PC do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Enviando um aplicativo para a Windows Store](submitting-an-app-to-the-microsoft-store.md)

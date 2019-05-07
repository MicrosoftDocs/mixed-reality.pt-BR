---
title: Visão geral de desenvolvimento
description: Este artigo descreve os blocos de construção básicos do desenvolvimento de um aplicativo de realidade mista do Windows.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: ao obter Introdução, Noções básicas, HoloLens, HoloLens 2, fone de ouvido imersivo, unity, o visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873985"
---
# <a name="development-overview"></a>Visão geral de desenvolvimento

Aplicativos de realidade misturada podem ser desenvolvidos usando uma variedade de tecnologias para desenvolvedores.  HoloLens executa aplicativos criados com o [plataforma Universal do Windows](https://dev.windows.com/getstarted).  Fones imersivos em exposição executar aplicativos da plataforma Universal do Windows, bem como aplicativos Win32.
Obtendo familiarizado com as ferramentas de middleware como o Unity, você pode começar criando experiências de realidade misturada hoje.  Aproveitar o código-fonte aberto [Kit de ferramentas de realidade misturada](install-the-tools.md) para se familiarizar rapidamente.
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Misto dos serviços de realidade</a>, como <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">âncoras espacial do Azure</a>, têm SDKs que podem integrar várias tecnologias de desenvolvedor de plataforma cruzada.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>Noções básicas do desenvolvimento de realidade misturada

[Realidade misturada](mixed-reality.md) experiências são habilitadas por novos recursos do Windows para compreensão ambiental. Eles permitem que os desenvolvedores colocar uma [holograma](hologram.md) no mundo real, e permitir que os usuários percorrer os mundos digitais percorrendo sobre literalmente. 

Estes são os principais blocos de construção para o desenvolvimento de realidade mista:

<table>
<tr>
<th>Entrada</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> <a href="gaze.md">Mantenha o foco principal</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">Eye gaze</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> Mãos / <a href="gestures.md">gestos</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voz</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">Controladores de movimentos</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> Percepção e recursos espaciais</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">Coordenadas de mundo</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">Som espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">Mapeamento espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



O modelo de interação básico para [HoloLens](hololens-hardware-details.md) é [olhares](gaze.md), [gesto](gestures.md), e [voz](voice-input.md), às vezes chamados de *GGV* . [Fones imersivos em exposição Windows Mixed Reality](immersive-headset-hardware-details.md) também olhar de uso e voz, mas troca [controladores de movimento](motion-controllers.md) para gestos.


Todos os dispositivos de realidade misturada com base no Windows se beneficiar o ecossistema de entrada disponível para Windows, incluindo o mouse, teclado, gamepads e muito mais. Com o HoloLens, [Acessórios de hardware](hardware-accessories.md) estão conectados via Bluetooth. Com fones imersivos em exposição, Acessórios conecte-se ao PC host via Bluetooth, USB e outros protocolos com suporte.

Os recursos de compreensão ambientais, como [coordenadas](coordinate-systems.md), [espacial som](spatial-sound.md), e [mapeamento espacial](spatial-mapping.md) fornecem os recursos necessários para misturar a realidade. Mapeamento espacial é exclusivo para o HoloLens e permite hologramas interagir com o usuário e o mundo físico ao redor deles. Sistemas de coordenadas permitem que o movimento do usuário afetar o movimento no mundo digital.

[Hologramas](hologram.md) são feitas de luz e som, que contam [renderização holográfica](rendering.md). Noções básicas sobre a experiência de posicionamento e persistência, conforme demonstrado a [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) (às vezes chamado de "shell") é uma ótima maneira Proteja-se na experiência do usuário.

## <a name="tools-for-developing-for-mixed-reality"></a>Ferramentas de desenvolvimento para realidade misturada

As ferramentas que você usar dependerá do [estilo de aplicativo](app-views.md) você deseja compilar.
* [Aplicativos com uma exibição 2D](building-2d-apps.md) aproveite as ferramentas para criação de aplicativos da plataforma Universal do Windows adequada para ambientes, como tablets, PC e Windows Phone. Esses aplicativos têm experiência como 2D projeções colocadas no Windows Mixed Reality doméstica e podem funcionar através de vários tipos de dispositivos (incluindo o telefone e PC).
* Aplicativos envolventes e holográfico precisam de ferramentas projetadas para tirar proveito das APIs de realidade mista do Windows. Estamos [recomendável usar o Unity](unity-development-overview.md) para criar aplicativos de realidade misturada. Os desenvolvedores interessados em criar sua próprias mecanismo podem [usar DirectX e outras APIs do Windows](directx-development-overview.md).

Independentemente do tipo de aplicativo que você está compilando, essas ferramentas facilitará a sua experiência de desenvolvimento de aplicativo:
* [O Visual Studio e o SDK do Windows](using-visual-studio.md)
* [Portal de Dispositivos do Windows](using-the-windows-device-portal.md)
* [Emulador do HoloLens](using-the-hololens-emulator.md) (emulador do HoloLens 2 em breve)
* [Simulador de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md)
* [Critérios de qualidade do aplicativo](app-quality-criteria.md)

## <a name="see-also"></a>Consulte também
* [Instalar as ferramentas](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">Serviços de realidade misturada</a>
* [Tutoriais de realidade mistas](tutorials.md)
* [Projetos de software livre](open-source-projects.md)
* [Noções básicas do MR 100: introdução ao Unity](holograms-100.md)
* [Diretrizes de compatibilidade de hardware do Windows Mixed Reality mínimas PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Enviar um aplicativo para a Windows Store](submitting-an-app-to-the-microsoft-store.md)

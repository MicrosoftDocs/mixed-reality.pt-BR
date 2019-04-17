---
title: Modos de exibição do aplicativo
description: Os dois tipos de modos de exibição em aplicativos de realidade mista do Windows são modos de exibição envolventes e 2D.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: modo de exibição imersivo, aplicativo de exibição 2D, o slate,
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590946"
---
# <a name="app-views"></a>Modos de exibição do aplicativo

Aplicativos do Windows podem conter dois tipos de modos de exibição, **modos de exibição de imersão** e **exibições 2D**. Aplicativos podem alternar entre seus vários imersivos modos de exibição e 2D, mostrando seus modos de exibição 2D em um monitor, como uma janela ou um Headset como uma imagem fixa. Os aplicativos que têm pelo menos uma exibição imersiva são categorizados como **aplicativos de realidade mista**. São aplicativos que nunca terá uma exibição imersiva **aplicativos 2D**.

## <a name="immersive-views"></a>Exibições de imersão

Uma exibição de imersão dá ao seu aplicativo a capacidade de criar hologramas no mundo você ou Mergulhe o usuário em um ambiente virtual. Quando um aplicativo está desenhando na exibição de imersão, nenhum outro aplicativo está desenhando ao mesmo tempo&mdash;hologramas de vários aplicativos não são compostas juntos. Ajustando continuamente a perspectiva da qual seu [aplicativo renderiza](rendering.md) sua cena para corresponder os movimentos de principal do usuário, seu aplicativo pode renderizar [bloqueado pelo mundo](coordinate-systems.md) hologramas que permanecem em um ponto fixo no real mundo ou ele pode renderizar um mundo virtual que mantém sua posição como um usuário move dentro dele.

![Em uma exibição de imersão hologramas podem ser colocadas no mundo ao seu redor.](images/designoverview.jpg)<br>
*Em uma exibição de imersão hologramas podem ser colocadas no mundo em torno de você*

Na [HoloLens](hololens-hardware-details.md), seu aplicativo processa suas hologramas sobre o ambiente do mundo real do usuário. Em um [fone de ouvido imersivo Windows Mixed Reality](immersive-headset-hardware-details.md), o usuário não consegue ver o mundo real e para que seu aplicativo deve renderizar tudo o que o usuário verá.

O [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) (incluindo o menu Iniciar e hologramas você colocou em torno do ambiente) não é renderizado enquanto estiver em uma imersão exibir. No HoloLens, quaisquer notificações de sistema que ocorrem enquanto está mostrando uma exibição de imersão serão retransmitidas audível pela Cortana e o usuário pode responder com entrada de voz.

Enquanto estiver em uma exibição imersiva, seu aplicativo também é responsável por manipular todas as entradas. Entrada na realidade mista do Windows é composta por [olhares](gaze.md), [gesto](gestures.md) (apenas para HoloLens), [voz](voice-input.md) e [controladores de movimento](motion-controllers.md) (envolventes fones de ouvido apenas).

## <a name="2d-views"></a>Modos de exibição 2D

![Vários modos de exibição 2D dispostos em torno do Windows Mixed Reality inicial](images/teleportation-640px.png)<br>
*Vários aplicativos com uma exibição 2D colocado em torno do Windows Mixed Reality inicial*

Um aplicativo com uma exibição 2D aparece na [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) (às vezes chamado de "shell") como um slate virtual, processado juntamente com os inicializadores de aplicativos e outras hologramas o usuário tiver inserido no seu mundo. O usuário pode ajustar esse slate para mover e dimensioná-lo, embora ele permanece com uma resolução fixa, independentemente do tamanho. Se a primeira visualização do seu aplicativo é uma exibição 2D, seu conteúdo 2D preencherá o slate mesmo usado para iniciar o aplicativo.

Um Headset da área de trabalho, você pode executar todos os aplicativos Universal Windows Platform (UWP) que executam o monitor da área de trabalho hoje. Esses aplicativos já são exibições de renderização 2D hoje mesmo e seus conteúdos serão exibidos automaticamente em uma ficha no mundo do usuário quando iniciado. Aplicativos da UWP 2D podem direcionar o **universal** família do dispositivo para ser executado em ambos os fones de ouvido da área de trabalho e em HoloLens como slates.

Um dos modos de exibição 2D do uso da chave é mostrar um formulário de entrada de texto que pode tornar o uso de teclado sistema. Porque o shell não é possível renderizar na parte superior de uma exibição imersiva, o aplicativo deve alternar para uma exibição em 2D para mostrar o teclado do sistema. Aplicativos que deseja aceitar a entrada de texto podem alternar para uma exibição 2D com uma caixa de texto. Enquanto essa caixa de texto tem o foco, o sistema mostrará o teclado do sistema, permitindo que o usuário insira texto.

Observe que, em um computador desktop, um aplicativo pode ter modos de exibição 2D no monitor da área de trabalho e um Headset anexado. Por exemplo, você pode procurar o Edge no monitor da área de trabalho usando o modo de exibição principal 2D para localizar um vídeo de 360 graus. Quando você executa esse vídeo, borda iniciará uma exibição secundária imersiva dentro o fone de ouvido para exibir o conteúdo de vídeo envolvente.

## <a name="see-also"></a>Consulte também

* [Modelo de aplicativo](app-model.md)
* [Atualizando aplicativos da UWP 2D para realidade misturada](building-2d-apps.md)
* [Obtendo um HolographicSpace](getting-a-holographicspace.md)
* [Navegando o Windows Mixed Reality inicial](navigating-the-windows-mixed-reality-home.md)
* [Tipos de aplicativos de realidade misturada](types-of-mixed-reality-apps.md)

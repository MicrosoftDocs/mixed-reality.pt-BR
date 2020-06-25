---
title: Visualização de malha espacial
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realidade misturada, HoloLens, controles de interface do usuário, interação, interface do usuário, UX, design de UX, interface do usuário espacial, interação espacial, interface do usuário 3D, UX 3D
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346092"
---
# <a name="spatial-mesh"></a>Malha espacial

![Malha espacial](images/UX/MRTK_PulseShader_SpatialMesh.gif)

Por meio da visualização de malha espacial, o usuário pode aprender como um dispositivo percebe e entende o ambiente físico. Além de fornecer o contexto espacial, a visualização da malha espacial adequada pode criar uma experiência interessantes e mágico.  

## <a name="design-guideline"></a>Diretriz de design
Como é importante permitir que o usuário se concentre e interaja com o conteúdo, a visualização contínua e repetida da malha espacial em segundo plano poderia ser uma distração. É recomendável Visualizar o ambiente com moderação, seja apenas uma vez na inicialização inicial ou quando o usuário mostrar uma intenção clara de ver a malha ambiental por direcionamento e espaço de toque. Você pode observar esse comportamento no Shell do HoloLens.
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualização de malha espacial no MRTK (Kit de ferramentas de realidade mista) para Unity
O MRTK fornece vários materiais para a visualização de malha espacial.

- **MRTK_Wireframe. esteira, MRTK_Wireframe. passe-partout**: material de malha espacial estática padrão que mostra os contornos de malha sem animação. Esse material é útil para fins de depuração, pois mostra as geometrias de malha espacial inteiras. No entanto, não é recomendável para produção.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. passe-partout**: esse material oferece um efeito de pulso animado na malha espacial. Você pode usar esse material para visualizar o ambiente em um momento específico da sua experiência ou na entrada do toque do usuário. Consulte a cena **PulseShaderExamples. Unity** para ver os exemplos.
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* Consulte [reconhecimento espacial MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) e [sombreador MRTK-Pulse](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) para obter mais detalhes.

<br>

---

## <a name="see-also"></a>Veja também

* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)

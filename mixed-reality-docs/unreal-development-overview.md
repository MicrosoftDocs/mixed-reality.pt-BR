---
title: Visão geral do desenvolvimento com o Unreal
description: Visão geral do desenvolvimento de realidade misturada usando o Unreal Engine 4
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851560"
---
# <a name="unreal-development-overview"></a>Visão geral do desenvolvimento com o Unreal

O Unreal Engine 4 agora é totalmente compatível com o desenvolvimento tanto para dispositivos de VR (Windows Mixed Reality) quanto de RA (HoloLens 2)! Se você está conhecendo o desenvolvimento com o Unreal agora, a <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Introdução ao Unreal Engine 4</a> é uma ótima página a ser explorada. Caso você precise de ativos, o Unreal dispõe de um <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a> abrangente. 

Depois de obter uma compreensão básica do desenvolvimento no Unreal, confira o tutorial na próxima seção para saber como compilar e executar seus aplicativos no HoloLens. Não deixe de visitar os <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">fóruns sobre realidade misturada do Unreal</a> e envolva-se com a comunidade de criação de aplicativos de realidade misturada no Unreal. É um ótimo lugar para encontrar soluções para problemas que você se deparar.

## <a name="tutorial"></a>Tutorial

Saiba como [criar e implantar um aplicativo de xadrez simples](unreal-uxt-ch1.md) para o HoloLens 2 seguindo nosso tutorial de ponta a ponta. Este tutorial usa o plug-in Ferramentas de UX para acelerar o desenvolvimento de aplicativos com componentes de UX interativos, incluindo um botão e um manipulador. Para obter mais informações sobre o plug-in Ferramentas de UX, consulte a próxima seção sobre MRTK. 

## <a name="mixed-reality-toolkit-for-unreal"></a>Kit de Ferramentas de Realidade Misturada para Unreal

O [Kit de Ferramentas de Realidade Misturada para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) é um conjunto de componentes, na forma de plug-ins, exemplos e documentação, projetados para acelerar o desenvolvimento de aplicativos de realidade misturada usando o Unreal Engine. O primeiro componente lançado como parte desse kit de ferramentas é o [Ferramentas de UX para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), um plug-in que pode ser adicionado ao seu projeto do HoloLens 2 para fornecer recursos de UX para aplicativos do HoloLens 2. A documentação para o Kit de Ferramentas de Realidade Misturada e para as Ferramentas de UX para Unreal pode ser encontrada nos respectivos repositórios GitHub. 

## <a name="performance"></a>Desempenho

Um aplicativo do HoloLens 2 deve ser executado em 60 quadros por segundo para que os hologramas pareçam estáveis e dinâmicos. Para conseguir isso em seu aplicativo, é altamente recomendável seguir nossas [recomendações de desempenho de para Unreal](performance-recommendations-for-unreal.md). 

## <a name="guides-to-specific-features"></a>Guias para recursos específicos

Para saber como usar recursos específicos no Unreal, confira os guias a seguir: 
* [Acompanhamento da mão](unreal-hand-tracking.md)
* [Acompanhamento ocular](unreal-gaze-input.md)
* [Mapeamento espacial](unreal-spatial-mapping.md)
* [Âncoras espaciais](unreal-spatial-anchors.md)
* [Entrada de voz](unreal-voice-input.md)
* [Câmera do HoloLens](unreal-hololens-camera.md)
* [Códigos QR](unreal-qr-codes.md)

## <a name="supported-features"></a>Recursos compatíveis

| Recurso do HoloLens 2 | Versão do Unreal Engine compatível mais antiga |
| ----------- | ----------- |
| Compatibilidade com ARM64 | 4.23 |
| Streaming de um PC | 4.23 |
| mapeamento espacial | 4.23 |
| Controle de mão e junta | 4.23 |
| Acompanhamento ocular | 4.23 |
| Entrada de voz | 4.23 |
| Âncoras espaciais | 4.23 |
| Acesso à câmera | 4.23 |
| Códigos QR | 4.23 |
| Áudio espacial | 4.23 |
| Compatibilidade com tela Espectador para streaming | 4.24 |
| LSR Planar por streaming | 4.24 |
| Aplicativos de exemplo ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) e [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Exibição múltipla em dispositivos móveis: Desempenho alcança 60 quadros/s | 4.25 |
| Renderização de 3ª câmera | 4.25 |
| Streaming de um aplicativo da área de trabalho empacotado | 4.25 |
| Âncoras Espaciais do Azure para o HoloLens 2 (beta) | 4.25 |
| Compatibilidade com OpenXR (beta) | 4.25 |
| Compatibilidade com Ferramentas de UX (0.8) | 4.25 |
| Documentos do desenvolvedor e tutoriais | 4.25 |

## <a name="see-also"></a>Veja também
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Documentos do Unreal para streaming, implantação em emulador e em dispositivo</a>
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Diretrizes de desempenho do Unreal para dispositivos móveis</a>

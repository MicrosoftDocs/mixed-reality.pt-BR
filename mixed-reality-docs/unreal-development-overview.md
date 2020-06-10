---
title: Visão geral do desenvolvimento com o Unreal
description: Visão geral do desenvolvimento de realidade misturada usando o Unreal Engine 4
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development
ms.openlocfilehash: 3e3862bd701d6e873f623abc9f9cda0b3085e753
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330153"
---
# <a name="unreal-development-overview"></a>Visão geral do desenvolvimento com o Unreal

A introdução aos <a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="Documentos do Mixed Reality"> aplicativos de realidade misturada</a> é uma grande tarefa. Novos conceitos, plataformas e hardware de ponta podem ser vistos como barreiras. No entanto, se você é um desenvolvedor do Unreal, você está com sorte. O suporte aos <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="Documentos do Windows Mixed Reality">Windows Mixed Reality</a> (VR) e aos <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="Documentos do HoloLens 2">HoloLens 2</a> (RA) agora está incluído em <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Notas sobre a versão do Unreal Engine 4.25">versão</a> mais recente. Essa atualização inclui:
* Compatibilidade com o plug-in de Ferramentas de UX de Realidade Misturada
* Compatibilidade com OpenXR
* Comunicação remota com o aplicativo por meio de um aplicativo da área de trabalho
* Melhor desempenho
* Captura de realidade mista
* Suporte inicial para Âncoras Espaciais do Azure

Se você não estiver familiarizado com o desenvolvimento no Unreal, não prossiga às cegas. Explore a <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">série de tutoriais</a> do Unreal para se familiarizar e procure ativos e suporte no <a href="https://www.unrealengine.com/marketplace//store" target="_blank">marketplace</a> do Unreal e nos <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">fóruns</a> sobre realidade misturada. Esses recursos são seus links para a comunidade de criadores e solucionadores de problemas no mercado atual de realidade misturada.

## <a name="mixed-reality-toolkit-for-unreal"></a>Kit de Ferramentas de Realidade Misturada para Unreal

O [Kit de Ferramentas de Realidade Misturada para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) é um conjunto de componentes projetados para acelerar seu desenvolvimento no Unreal. Cada componente inclui plug-ins, exemplos e documentação para configurar experiências imersivas. 

As [Ferramentas de UX para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) são o primeiro componente a ser lançado e atualmente só são compatíveis com o HoloLens 2. O plug-in do componente inclui código, blueprints e ativos de exemplo de recursos comuns de UX, incluindo:
* Simulação de entrada
* Ator de interação à mão
* Componente de botão pressionável
* Componente de manipulador
* Componente de comportamento de acompanhamento

Você pode se aprofundar no repositório do GitHub das [Ferramentas de UX para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) para obter detalhes de recursos e informações sobre como configurar seu projeto.

## <a name="tutorial"></a>Tutorial

Criar algo com suas próprias mãos é a melhor maneira de aprender uma nova habilidade. Aprender a [criar e implantar um aplicativo de xadrez simples](unreal-uxt-ch1.md) para o HoloLens 2 com o plug-in de Ferramentas de UX é uma ótima maneira de começar. 

A série de tutoriais de ponta a ponta fornece contato prático com componentes e cenários comuns de UX interativa. Você trabalhará na configuração do projeto, adicionando interações à cena e implantando em um dispositivo ou emulador. Tudo o que você precisa é do Windows 10, de um emulador e do Visual Studio 2019.


## <a name="performance"></a>Desempenho

O desenvolvimento para realidade misturada vem com pontos de verificação de desempenho que dependem da plataforma. Um aplicativo do HoloLens 2 deve ser executado em 60 quadros por segundo para que os hologramas pareçam estáveis e dinâmicos. O Unreal fornece [recomendações de desempenho](performance-recommendations-for-unreal.md) para alcançar isso em seus aplicativos.

## <a name="guides-to-specific-features"></a>Guias para recursos específicos

Há vários recursos importantes de desenvolvimento de realidade misturada que nossa série de tutoriais não abrange. Confira os seguintes guias para obter detalhes e aplicações práticas: 
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

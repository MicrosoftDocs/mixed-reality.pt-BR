---
title: Visão geral do desenvolvimento com o Unreal
description: Introdução à criação de aplicativos de realidade misturada no Unreal.
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, streaming, comunicação remota, realidade misturada, desenvolvimento, introdução, novo projeto, emulador, documentação
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491176"
---
# <a name="unreal-development-overview"></a>Visão geral do desenvolvimento com o Unreal

Agora o suporte para realidade misturada no Unreal Engine 4 está em beta. Se você está conhecendo o desenvolvimento com o Unreal agora, a <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Introdução ao Unreal Engine 4</a> é uma ótima página a ser explorada. Caso você precise de ativos, o Unreal dispõe de um <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a> abrangente. 

Depois de obter um entendimento básico do Unreal Engine 4, visite a página do <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens Development</a> no site de documentação do Unreal Engine para saber como criar e executar seus aplicativos no HoloLens. Não deixe de visitar os <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">fóruns sobre realidade misturada do Unreal</a> para se envolver com a comunidade que cria aplicativos de realidade misturada no Unreal. É um ótimo lugar para encontrar soluções para problemas que possam ocorrer.

## <a name="installing-the-prerequisites"></a>Como instalar os pré-requisitos

Para começar a criar um aplicativo do HoloLens 2 no Unreal, você precisará do [Emulador do HoloLens 2](using-the-hololens-emulator.md) ou de um headset do HoloLens. Você também precisará instalar a última versão do Visual Studio com as cargas de trabalho e os componentes listados em <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">Pré-requisitos do HoloLens 2 para o Unreal</a>.

## <a name="building-and-running-your-unreal-app"></a>Como criar e executar seu aplicativo do Unreal

Primeiro, <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">empacote o aplicativo para o HoloLens 2</a>. Em seguida, escolha em que local deseja implantar o pacote:
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">Implantação no Emulador do HoloLens 2</a>
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">Implantação em um headset do HoloLens 2</a>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a>Como transmitir seu aplicativo para um headset por meio do Holographic Remoting Player

Transmitir seu aplicativo da área de trabalho para o aplicativo Holographic Remoting Player em um headset do HoloLens oferece duas vantagens principais: 
* Acelera o desenvolvimento, não havendo, portanto, a necessidade de reempacotar e carregar o aplicativo todas as vezes que você faz uma alteração
* Aproveita o poder da área de trabalho, de modo que você possa renderizar o máximo de polígonos que a GPU da área de trabalho permitir, sem as limitações impostas pelo computador disponível no headset

Para começar a usar o streaming, confira o <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">Início Rápido de streaming do HoloLens 2</a>[]().

## <a name="see-also"></a>Consulte também
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Diretrizes de desempenho do Unreal para dispositivos móveis</a>

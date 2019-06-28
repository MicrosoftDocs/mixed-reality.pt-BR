---
title: Visão geral de desenvolvimento do Unity
description: Começar a compilar obtendo misto aplicativos de realidade no Unity.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, misturadas realidade, desenvolvimento, introdução, novo projeto, portabilidade, funcionalidade, câmera, simulação, emulação, documentação
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414519"
---
# <a name="unity-development-overview"></a>Visão geral de desenvolvimento do Unity

O caminho mais rápido para criar uma [aplicativos de realidade misturada](app-views.md) é com [Unity](http://aka.ms/HoloLensUnity). É recomendável que você dedique tempo para explorar os [tutoriais do Unity](https://unity3d.com/learn/tutorials). Se você precisar de ativos, o Unity tem uma abrangente [Asset Store](https://www.assetstore.unity3d.com/). Depois que você tiver criado um backup de uma compreensão básica do Unity, você pode visitar o [tutoriais](tutorials.md) para conhecer as especificidades do desenvolvimento de realidade misturada com o Unity. Visite o [fóruns de realidade mista do Unity](http://forum.unity3d.com/forums/hololens.102/) interaja com o restante da comunidade da criação de aplicativos de realidade misturada no Unity e encontrar soluções para problemas que você pode enfrentar.


Para começar a criar aplicativos de realidade misturada com o Unity, primeiramente [instalar as ferramentas](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Novo projeto do Unity com o Kit de ferramentas de realidade misturada 

A maneira mais fácil de desenvolver no Unity é com a Ajuda do Kit de ferramentas de realidade mista. Ele ajuda você a instalação com o projeto automaticamente e fornecem um conjunto de recursos de realidade mista para acelerar seu desenvolvimento. Faça check-out [v2 do Kit de ferramentas de realidade misturada](mrtk-getting-started.md) para saber mais e começar a trabalhar. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portando um aplicativo existente do Unity para Windows Mixed Reality

Se você tiver um projeto existente do Unity que você estiver portando para Windows Mixed Reality, siga juntamente com o [guia de portabilidade do Unity](porting-guides.md) para começar a usar.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Configurar o novo projeto do Unity para Windows Mixed Reality

Se você deseja ter criado um novo projeto do Unity sem importar o Kit de ferramentas de realidade misturada, há um pequeno conjunto de configurações de Unity, que você precisará alterar manualmente para o Windows Mixed Reality. Essas são divididas em duas categorias: por projeto e por cena. Consulte aqui para o guia passo a passo para [configurar novo Unity projeto para o Windows Mixed Reality](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Adicionando recursos de realidade mista e entradas

Depois que você instalação MRTK V2 com seu projeto, ou configurado o projeto, conforme descrito acima, objetos padrão de jogos Unity (como a câmera) acenderão imediatamente para um **experiência de escala encaixado**, com a posição da câmera atualizada como o usuário move automaticamente suas cabeças por meio do mundo.

Adicionando suporte para recursos do Windows Mixed Reality, tais como [estágios espaciais](coordinate-systems.md#spatial-coordinate-systems), [gestos, os controladores de movimento](gestures-and-motion-controllers-in-unity.md) ou [entrada de voz](voice-input-in-unity.md) é feito usando as APIs criadas diretamente no Unity. 

Primeiro, examine os [experiência escalas](coordinate-systems.md) destinados a seu applicatioin:
* Se você deseja para criar uma **somente orientação** ou **experiência encaixado em escala**, você precisará definir tipo de espaço para rastreamento do Unity [estacionários](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se você estiver procurando para compilar um **escala permanente** ou **experiência de sala em escala**, você precisará garantir que a do Unity acompanhamento do tipo de espaço com êxito é definido como [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se você deseja para criar uma **escala mundial** experiência em HoloLens que permite aos usuários fazer roaming além dos medidores de 5, você precisará usar o [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) componente.

Todos os blocos de construção principais para aplicativos de realidade misturada são expostos de maneira consistente com as outras APIs do Unity. Eles também estão disponíveis por meio do Kit de ferramentas do realidade mista.
* [Câmera](camera-in-unity.md)
* [Sistemas de coordenadas](coordinate-systems-in-unity.md)
* [Foco](gaze-in-unity.md)
* [Gestos e controladores de movimento](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz](voice-input-in-unity.md)
* [Persistência](persistence-in-unity.md)
* [Som espacial](spatial-sound-in-unity.md)
* [Mapeamento espacial](spatial-mapping-in-unity.md)

Há outros recursos importantes que muitas misto realidade aplicativos vai querer usar que também são expostos aos aplicativos do Unity:
* [Experiências compartilhadas](shared-experiences-in-unity.md)
* [Câmera localizável](locatable-camera-in-unity.md)
* [Ponto de foco](focus-point-in-unity.md)
* [Perda de controle](tracking-loss-in-unity.md)
* [Teclado](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Execução do seu projeto do Unity em um dispositivo real ou simulado

Depois que seu projeto do Unity holográfico pronto para teste, a próxima etapa é para [exportar e compilar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md).

Com essa solução do VS em mãos, você pode executar seu aplicativo em uma das três maneiras, usando um dispositivo real ou simulado:
* [Implantar em um headset imersivo HoloLens ou Windows Mixed Reality real](using-visual-studio.md)
* [Implantar no emulador do HoloLens](using-the-hololens-emulator.md)
* [Implantar o simulador de imersivo headset de realidade mista do Windows](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentação do Unity

Além desta documentação disponível no Centro de desenvolvimento do Windows, o Unity instala documentação para a funcionalidade do Windows Mixed Reality junto com o Editor do Unity. O Unity fornecida a documentação inclui duas seções separadas:
1. **Referência de script do Unity**
    * Esta seção da documentação contém detalhes da API script do Unity fornece.
    * Acessível por meio do Editor do Unity **Ajuda > Referência de script**
2. **Manual do Unity**
    * Este manual foi projetado para ajudá-lo a aprender a usar o Unity, das técnicas básicas à avançados.
    * Acessível por meio do Editor do Unity **Ajuda > Manual**

## <a name="see-also"></a>Consulte também
* [Realidade misturada Toolkit v2](mrtk-getting-started.md)
* [Noções básicas do MR 100: introdução ao Unity](holograms-100.md)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Como usar o namespace do Windows com aplicativos Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Melhores práticas para trabalhar com o Unity e o Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de reprodução do Unity](unity-play-mode.md)
* [Portabilidade de guias](porting-guides.md)

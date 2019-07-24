---
title: Visão geral do desenvolvimento do Unity
description: Introdução à criação de aplicativos de realidade misturada no Unity.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, realidade mista, desenvolvimento, introdução, novo projeto, portabilidade, capacidade, câmera, simulação, emulação, documentação
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414519"
---
# <a name="unity-development-overview"></a>Visão geral do desenvolvimento do Unity

O caminho mais rápido para criar um [aplicativo de realidade misturada](app-views.md) é com o [Unity](http://aka.ms/HoloLensUnity). Recomendamos que você reserve um tempo para explorar os [tutoriais do Unity](https://unity3d.com/learn/tutorials). Se você precisar de ativos, o Unity terá um [repositório de ativos](https://www.assetstore.unity3d.com/)abrangente. Depois de criar uma compreensão básica do Unity, você pode visitar os [tutoriais](tutorials.md) para aprender as especificações do desenvolvimento de realidade misturada com o Unity. Visite os [fóruns de realidade misturada no Unity](http://forum.unity3d.com/forums/hololens.102/) para se envolver com o restante da Comunidade criando aplicativos de realidade misturada no Unity e encontre soluções para os problemas que você pode encontrar.


Para começar a criar aplicativos de realidade misturada com o Unity, primeiro [Instale as ferramentas](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Novo projeto do Unity com o Mixed Reality Toolkit 

A maneira mais fácil de desenvolver no Unity é com a ajuda do Mixed Reality Toolkit. Ele o ajudará a configurar com o projeto automaticamente e fornecerá um conjunto de recursos de realidade misturada para acelerar seu desenvolvimento. Confira o [Kit de ferramentas da realidade mista v2](mrtk-getting-started.md) para saber mais e começar. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portando um aplicativo de Unity existente para a realidade mista do Windows

Se você tiver um projeto de Unity existente que está portando para a realidade mista do Windows, acompanhe o [guia](porting-guides.md) de portagem do Unity para começar.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Configurando o novo projeto do Unity para a realidade mista do Windows

Se você quiser criar um novo projeto de Unity sem importar o kit de ferramentas de realidade misturada, há um pequeno conjunto de configurações de Unity que você precisará alterar manualmente para a realidade mista do Windows. Elas são divididas em duas categorias: por projeto e por cena. Consulte aqui para obter o guia passo a passo para [Configurar o novo projeto do Unity para a realidade mista do Windows](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Adicionando entradas e recursos de realidade misturada

Depois de configurar o MRTK V2 com seu projeto, ou configurar seu projeto conforme descrito acima, os objetos de jogo do Unity Standard (como a câmera) se acenderão imediatamente para uma **experiência em escala**, com a posição da câmera atualizada automaticamente como a o usuário move sua cabeça pelo mundo.

A adição de suporte para recursos de realidade mista do Windows, como [estágios espaciais](coordinate-systems.md#spatial-coordinate-systems), [gestos, controladores de movimento](gestures-and-motion-controllers-in-unity.md) ou entrada de [voz](voice-input-in-unity.md) , é obtida usando APIs criadas diretamente no Unity. 

Primeiro, examine as [escalas de experiência](coordinate-systems.md) que seu applicatioin pode atingir:
* Se você pretende criar uma **experiência**de dimensionamento ou **somente de orientação** , você precisará definir o tipo de espaço de rastreamento do Unity como [estático](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se você pretende criar uma experiência em **escala** ou em **escala de sala**, precisará garantir que o tipo de espaço de rastreamento do Unity seja definido com êxito como [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se você pretende criar uma experiência de **escala mundial** no HoloLens que permita que os usuários se movimentem além de 5 metros, você precisará usar o componente [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) .

Todos os principais blocos de construção para aplicativos de realidade misturada são expostos de maneira consistente com outras APIs do Unity. Eles também estão disponíveis por meio do kit de ferramentas de realidade misturada.
* [Câmera](camera-in-unity.md)
* [Sistemas de coordenadas](coordinate-systems-in-unity.md)
* [Foco](gaze-in-unity.md)
* [Gestos e controladores de movimento](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz](voice-input-in-unity.md)
* [Persistência](persistence-in-unity.md)
* [Som espacial](spatial-sound-in-unity.md)
* [Mapeamento espacial](spatial-mapping-in-unity.md)

Há outros recursos principais que muitos aplicativos de realidade misturados desejarão usar que também são expostos aos aplicativos do Unity:
* [Experiências compartilhadas](shared-experiences-in-unity.md)
* [Câmera localizável](locatable-camera-in-unity.md)
* [Ponto de foco](focus-point-in-unity.md)
* [Perda de rastreamento](tracking-loss-in-unity.md)
* [Teclado](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Executando o projeto do Unity em um dispositivo real ou simulado

Depois que o projeto do Holographic Unity estiver pronto para teste, a próxima etapa será [exportar e criar uma solução do Unity Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md).

Com essa solução VS em mãos, você pode executar o aplicativo de uma das três maneiras, usando um dispositivo real ou simulado:
* [Implantar para um verdadeiro HoloLens ou um headset de imersão de realidade mista do Windows](using-visual-studio.md)
* [Implantar no emulador do HoloLens](using-the-hololens-emulator.md)
* [Implantar no simulador de headset de imersão do Windows Mixed Realm](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentação do Unity

Além desta documentação disponível no centro de desenvolvimento do Windows, o Unity instala a funcionalidade de realidade mista do Windows junto com o editor do Unity. A documentação fornecida pelo Unity inclui duas seções separadas:
1. **Referência de script do Unity**
    * Esta seção da documentação contém detalhes da API de script que o Unity fornece.
    * Acessível do editor do Unity por meio da **ajuda > referência de script**
2. **Manual do Unity**
    * Este manual foi projetado para ajudá-lo a aprender a usar o Unity, de técnicas básicas a avançadas.
    * Acessível do editor do Unity por meio da **ajuda > manual**

## <a name="see-also"></a>Consulte também
* [Kit de ferramentas de realidade misturada v2](mrtk-getting-started.md)
* [Noções básicas do MR 100: introdução ao Unity](holograms-100.md)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Como usar o namespace do Windows com aplicativos Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Melhores práticas para trabalhar com o Unity e o Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de reprodução do Unity](unity-play-mode.md)
* [Guias de portabilidade](porting-guides.md)

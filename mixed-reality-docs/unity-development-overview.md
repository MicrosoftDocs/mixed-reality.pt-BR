---
title: Visão geral do desenvolvimento com o Unity
description: Introdução à criação de aplicativos de realidade misturada no Unity.
author: thetuvix
ms.author: kurtie
ms.date: 07/29/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realidade misturada, desenvolvimento, introdução, novo projeto, portabilidade, funcionalidade, câmera, simulação, emulação, documentação
ms.openlocfilehash: 4679e1a2b58a7e0d77e6b295803624a4de1fac19
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476708"
---
# <a name="unity-development-overview"></a>Visão geral do desenvolvimento com o Unity

O caminho mais rápido para a criação de um [aplicativo de realidade misturada](app-views.md) é com o [Unity](https://unity.com). Recomendamos que você reserve um tempo para explorar os [tutoriais do Unity](https://unity3d.com/learn/tutorials). Caso você precise de ativos, o Unity dispõe de uma [Asset Store](https://www.assetstore.unity3d.com/) abrangente. Depois de obter um entendimento básico do Unity, visite os [tutoriais](tutorials.md) para saber mais sobre os detalhes específicos do desenvolvimento de realidade misturada com o Unity. Não deixe de visitar os [fóruns sobre realidade misturada do Unity](https://forum.unity3d.com/forums/hololens.102/) para se envolver com o restante da comunidade que cria aplicativos de realidade misturada no Unity e encontrar soluções para os problemas que possam ocorrer.

Para começar a criar aplicativos de realidade misturada com o Unity, primeiro [instale as ferramentas](install-the-tools.md).

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Novo projeto do Unity com o Kit de Ferramentas de Realidade Misturada 

A maneira mais fácil de desenvolver aplicativos no Unity é com o Kit de Ferramentas de Realidade Misturada, que ajudará você a configurar o projeto automaticamente e fornecerá um conjunto de recursos de realidade misturada para acelerar seu desenvolvimento. Confira [Kit de Ferramentas de Realidade Misturada v2](mrtk-getting-started.md) para saber mais e obter uma introdução. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portabilidade de um aplicativo existente do Unity para o Windows Mixed Reality

Caso você tenha um projeto existente do Unity que esteja portando para o Windows Mixed Reality, siga o [guia de portabilidade do Unity](porting-guides.md) para obter uma introdução.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Como configurar um novo projeto do Unity para o Windows Mixed Reality

Caso você esteja criando um projeto do Unity sem importar o Kit de Ferramentas de Realidade Misturada, há um pequeno conjunto de configurações do Unity que precisará ser alterado no Windows Mixed Reality. Essas configurações são divididas em duas categorias: por projeto e por cena. Acesse aqui para obter um guia passo a passo para [Configurar um novo projeto do Unity para o Windows Mixed Reality](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Como adicionar funcionalidades e entradas de realidade misturada

Depois que você configurar o MRTK V2 com o projeto ou configurar o projeto, conforme descrito acima, os objetos de jogo padrão do Unity, como a câmera, serão acesos imediatamente para uma **experiência de escala em posição**, com a posição da câmera atualizada automaticamente à medida que o usuário move a cabeça pelo mundo.

A adição de suporte aos recursos do Windows Mixed Reality, como [estágios espaciais](coordinate-systems.md#spatial-coordinate-systems), [gestos, controladores de movimentos](gestures-and-motion-controllers-in-unity.md) ou [entrada de voz](voice-input-in-unity.md), é obtida por meio de APIs incorporadas diretamente no Unity. 

Primeiro, examine as [escalas de experiência](coordinate-systems.md) que o aplicativo pode ter como destino:
* Se você pretender criar uma **experiência somente orientação** ou de **escala em posição**, precisará definir o tipo de espaço de acompanhamento do Unity como [Fixo](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se você pretender criar uma **experiência de escala em pé** ou de **escala de sala**, precisará garantir que o tipo de espaço de rastreamento do Unity seja definido com êxito como [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Se você pretender criar uma experiência de **escala mundial** no HoloLens que permita que os usuários se movimentem para além de 5 metros, precisará usar o componente [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience).

Todos os principais blocos de construção para aplicativos de realidade misturada são expostos de maneira consistente com outras APIs do Unity. Eles também estão disponíveis por meio do Kit de Ferramentas de Realidade Misturada.
* [Câmera](camera-in-unity.md)
* [Sistemas de coordenadas](coordinate-systems-in-unity.md)
* [Foco](gaze-in-unity.md)
* [Gestos e controladores de movimentos](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz](voice-input-in-unity.md)
* [Persistência](persistence-in-unity.md)
* [Som espacial](spatial-sound-in-unity.md)
* [Mapeamento espacial](spatial-mapping-in-unity.md)

Há outros recursos essenciais que muitos aplicativos de realidade misturada desejarão usar que também são expostos aos aplicativos do Unity:
* [Experiências compartilhadas](shared-experiences-in-unity.md)
* [Câmera localizável](locatable-camera-in-unity.md)
* [Ponto de foco](focus-point-in-unity.md)
* [Controle de perda](tracking-loss-in-unity.md)
* [Teclado](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Como executar o projeto do Unity em um dispositivo real ou simulado

Depois que o projeto holográfico do Unity estiver pronto para teste, a próxima etapa será [exportar e criar uma solução do Unity para Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md).

Com essa solução do VS em mãos, você poderá executar o aplicativo de uma das três maneiras, usando um dispositivo real ou simulado:
* [Implantação em um HoloLens real ou um headset imersivo do Windows Mixed Reality](using-visual-studio.md)
* [Implantação no emulador do HoloLens](using-the-hololens-emulator.md)
* [Implantação no simulador de headset imersivo do Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Documentação do Unity

Além desta documentação disponível em docs.microsoft.com, o Unity instala a documentação da funcionalidade do Windows Mixed Reality junto com o Editor do Unity. A documentação fornecida pelo Unity inclui duas seções separadas:
1. **Referência de script do Unity**
    * Esta seção da documentação contém detalhes da API de script fornecida pelo Unity.
    * Acessível por meio do Editor do Unity em **Ajuda > Referência de Script**
2. **Manual do Unity**
    * Este manual foi projetado para ajudar você a aprender a usar o Unity, de técnicas básicas a avançadas.
    * Acessível por meio do Editor do Unity em **Ajuda > Manual**

## <a name="see-also"></a>Veja também
* [Kit de Ferramentas de Realidade Misturada v2](mrtk-getting-started.md)
* [Noções básicas do MR 100: introdução ao Unity](holograms-100.md)
* [Configurações recomendadas do Unity](recommended-settings-for-unity.md)
* [Recomendações de desempenho para Unity](performance-recommendations-for-unity.md)
* [Como exportar e criar uma solução do Visual Studio do Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Como usar o namespace do Windows com aplicativos Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Melhores práticas para trabalhar com o Unity e o Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de reprodução do Unity](unity-play-mode.md)
* [Guias de portabilidade](porting-guides.md)

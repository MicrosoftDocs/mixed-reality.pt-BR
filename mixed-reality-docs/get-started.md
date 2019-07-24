---
title: Introdução
description: Este guia descreve a maneira mais rápida de colocar em funcionamento o desenvolvimento de realidade misturada.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: introdução, noções básicas, HoloLens, headsets de imersão, ar, VR, Unity, Visual Studio, início rápido, como
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873967"
---
# <a name="get-started"></a>Introdução

Bem-vindo ao mundo do desenvolvimento de realidade misturada! Se você for novo no Sr, este guia será o seu hub para colocar em funcionamento o mais rápido possível. Ajudaremos você a configurar seu PC para desenvolvimento, colocar seus dispositivos prontos e instalar ferramentas que acelerarão o processo de desenvolvimento do MR. 

## <a name="intro-to-mixed-reality"></a>Introdução à realidade misturada

Você pode ter algumas perguntas sobre o que queremos dizer com "realidade misturada" e como ela se relaciona à realidade aumentada (AR) e realidade virtual (VR). Em suma, a realidade misturada é a mistura do mundo físico com o mundo digital, portanto, é um espectro que abrange tudo, desde a realidade aumentada, onde o conteúdo digital é colocado no mundo real, até a realidade virtual, em que seu mundo real está quase totalmente substituído pelo digital. 

![Exemplo de um aplicativo de realidade misturada que dá suporte a headsets de HoloLens e de imersão (VR)](images/mr-island.png)<br>
*Os aplicativos de realidade misturada podem dar suporte a headsets de HoloLens e de imersão (VR)*

Criamos a realidade mista do Windows como uma plataforma de desenvolvimento único e um conjunto de ferramentas que podem cobrir o espectro do Sr e atualmente damos suporte a dois tipos de dispositivos que abrangem o mesmo espectro: O [Microsoft HoloLens](https://www.microsoft.com/hololens), o primeiro fone de ouvido Holographic e os controladores de [movimento de realidade](https://www.microsoft.com/windows/windows-mixed-reality)do mundo misto do Windows, que se conectam a um PC para experiências de realidade virtual eficientes. Você pode conferir o que é [realidade misturada?] (artigo para obter uma resposta mais completa, se você estiver interessado.

## <a name="choose-your-development-path"></a>Escolha seu caminho de desenvolvimento

A maneira mais fácil de desenvolver um aplicativo de realidade misturada é usar o [Unity](https://unity3d.com), uma ferramenta de middleware poderosa e popular frequentemente usada para o desenvolvimento de jogos. Se você quiser usar um mecanismo personalizado, também poderá [criar com base no DirectX](directx-development-overview.md), mas a maioria dos desenvolvedores de Mr usa o Unity para seus jogos e aplicativos. Com o Unity, você poderá criar um aplicativo de realidade misturada que direcione os headsets de HoloLens, imersiva (VR) ou ambos!

## <a name="prepare-your-pc-and-devices-for-development"></a>Preparar seu PC e dispositivos para desenvolvimento

Independentemente de você estar criando um aplicativo de realidade misturado que direcione o HoloLens, headsets de imersão (VR) ou ambos, você usará um conjunto comum de ferramentas e APIs. Você também desejará garantir que seu PC seja potente o bastante para o desenvolvimento que você vai fazer. 

>[!NOTE]
>Você pode encontrar nossas recomendações em especificações do PC de desenvolvimento, versões com suporte de cada ferramenta de software e configurações relevantes ou notas de configuração para cada um deles no artigo [instalar as ferramentas](install-the-tools.md) . Examine esse artigo antes de instalar as ferramentas abaixo.

Ferramentas a serem instaladas:
* [Unity](https://store.unity.com/download)
* [Visual Studio (com o SDK do Windows 10)](https://developer.microsoft.com/windows/downloads)
* [Kit de ferramentas de realidade misturada para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

Você também desejará [colocar seu dispositivo de destino no modo de desenvolvedor e configurar o Visual Studio para implantar aplicativos no dispositivo de destino](using-visual-studio.md).

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Uma observação sobre o kit de ferramentas de realidade misturada para o Unity

![MRTK para Unity](images/mrtkandunity.png)<br>

***YOYOE ISSO E DIGA A TODOS PORQUE O MRTK-UNITY É TÃO INCRÍVEL E TODAS AS COISAS LEGAIS QUE ELE TEM DENTRO:)***

O kit de ferramentas de realidade misturada é uma coleção de scripts e componentes destinados a acelerar o desenvolvimento de aplicativos direcionados a headsets do Microsoft HoloLens e do Windows Mixed Reality. O projeto visa reduzir as barreiras de entrada para criar aplicativos de realidade misturada e contribuir com a comunidade à medida que todos nós crescemos.

## <a name="start-your-first-mr-project"></a>Inicie seu primeiro projeto MR

Agora que seu PC e dispositivo (s) estão configurados, você está pronto para criar seu primeiro projeto de realidade misturada no Unity. Acompanhe o nosso primeiro curso do Sr Academy, [o Sr Basics 100: Introdução ao Unity](holograms-100.md)e, no final, você terá um cubo em funcionamento em um headset de realidade misturada.

![Captura de tela de um cubo em um projeto de Unity de realidade misturada](images/mr-cube.PNG)<br>
*Seu primeiro projeto de realidade misturada no Unity-Olá, mundo!*

## <a name="learn-more-and-get-help"></a>Saiba mais e Obtenha ajuda

Agora que você criou com êxito seu primeiro projeto MR, provavelmente está se perguntando mais! Aqui estão alguns recursos que devem ajudar:
* [Documentação do desenvolvedor de realidade mista](mixed-reality.md) – você já está aqui, mas há muito mais a fazer check-out, incluindo documentação técnica, diretrizes de design, projetos de exemplo e estudos de caso.
* [Tutoriais de realidade misturada](tutorials.md) -acompanhe os tutoriais que abrangem tudo, desde a configuração de projetos até a implementação dos principais blocos de construção do Sr, a integração dos serviços de nuvem do Azure ao seu aplicativo Mr.
* [Aprenda](https://unity3d.com/learn) o site da Unity-Unity oferece tutoriais, projetos e sessões de treinamento ao vivo para criadores em cada estágio de aprendizado.

Você também pode obter ajuda desses ótimos recursos da Comunidade:
* [Fóruns de desenvolvedores de realidade misturada](https://forums.hololens.com/) – o fórum oficial para os desenvolvedores de realidade misturada para fazer e responder a perguntas, bem como ler notícias de desenvolvimento do Mr diretamente da Microsoft.
* [Canal de margem de atraso HoloDevelopers](https://holodevelopersslack.azurewebsites.net/) -o canal de desenvolvedor específico da realidade mista externa mais robusta e versátil; os desenvolvedoress aqui são úteis e útil.
* [Fóruns do Unity](https://forum.unity3d.com/) – fóruns oficiais do Unity.

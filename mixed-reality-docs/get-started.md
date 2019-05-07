---
title: Introdução
description: Este guia descreve a maneira mais rápida para entrar em funcionamento com o desenvolvimento de realidade misturada.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: começar a usar, básico, HoloLens, fone de ouvido imersivo, ar, vr, unity, o visual studio, início rápido, como
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873967"
---
# <a name="get-started"></a>Introdução

Bem-vindo ao mundo do desenvolvimento de realidade misturada! Se você for novo no MR, este guia será seu hub para colocá-lo em funcionamento o mais rápido possível. Ajudaremos você a obter seu conjunto de PC para o desenvolvimento, prepare-se a seus dispositivos e instalar as ferramentas que irão acelerar o processo de desenvolvimento MR. 

## <a name="intro-to-mixed-reality"></a>Introdução à realidade mista

Você pode ter algumas perguntas sobre o que queremos dizer com "realidade misturada" e como ele se relaciona com a realidade aumentada (AR) e a realidade virtual (VR). Em resumo, a realidade misturada é a mistura do mundo físico com o mundo digital, portanto, é um espectro que abrange tudo, desde a realidade aumentada, onde o conteúdo digital é colocado no mundo real, a realidade virtual, em que o mundo real é quase que totalmente substituído pela digital. 

![Exemplo de um aplicativo de realidade misturada com suporte para HoloLens e fones imersivos em exposição (VR)](images/mr-island.png)<br>
*Aplicativos de realidade misturada podem dar suporte a HoloLens e fones imersivos em exposição (VR)*

Criamos Windows Mixed Reality como uma plataforma de desenvolvimento único e o conjunto de ferramentas que abrangem o espectro MR e, atualmente, damos suporte a dois tipos de dispositivos que atendem a mesma: [Microsoft HoloLens](https://www.microsoft.com/hololens), primeiro autocontido holográfica fone de ouvido do mundo, e [fones imersivos em exposição Windows Mixed Reality e controladores de movimento](https://www.microsoft.com/windows/windows-mixed-reality), que se conectar a um PC para experiências de realidade virtual poderosa. Você pode verificar o nosso que é [realidade misturada?] (para obter uma resposta mais completa se você estiver interessado.

## <a name="choose-your-development-path"></a>Escolha seu caminho de desenvolvimento

Usando o a maneira mais fácil desenvolver um aplicativo de realidade misturada [Unity](https://unity3d.com), uma ferramenta avançada e popular middleware geralmente usada para desenvolvimento de jogos. Se você quiser usar um mecanismo personalizado, você também pode [seja criado no DirectX](directx-development-overview.md), mas a maioria dos desenvolvedores MR usar o Unity para seus jogos e aplicativos. Com o Unity, você poderá criar um aplicativo de realidade mista que tem como alvo o HoloLens, fones imersivos em exposição (VR) ou ambos!

## <a name="prepare-your-pc-and-devices-for-development"></a>Preparar seu computador e dispositivos para o desenvolvimento

Se você estiver criando um aplicativo de realidade mista que tem como alvo o HoloLens, fones imersivos em exposição (VR) ou ambos, você usará um conjunto comum de ferramentas e APIs. Você também desejará certificar-se de que seu PC é poderoso o suficiente para o desenvolvimento, que você fará. 

>[!NOTE]
>Você pode encontrar as especificações de nossas recomendações no computador de desenvolvimento, as versões com suporte de cada ferramenta de software, e configurações relevantes ou configuração de anotações para cada um na [instalar as ferramentas](install-the-tools.md) artigo. Leia esse artigo antes de instalar as ferramentas abaixo.

Ferramentas para instalar:
* [Unity](https://store.unity.com/download)
* [Visual Studio (com o Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [Kit de ferramentas de realidade mista para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

Você também desejará [colocar seu dispositivo de destino em modo de desenvolvedor e configurar o Visual Studio para implantar aplicativos no dispositivo de destino](using-visual-studio.md).

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Uma observação sobre o Kit de ferramentas de realidade mista para Unity

![MRTK para Unity](images/mrtkandunity.png)<br>

***YOYO COMPLETÁ-LA E INFORMAR A TODOS POR QUE MRTK UNITY É TÃO INCRÍVEL E TODAS AS COISAS LEGAIS TEM DENTRO :)***

O Kit de ferramentas de realidade mista é uma coleção de scripts e componentes se destina a acelerar o desenvolvimento de aplicativos voltados para o Microsoft HoloLens e o Windows Mixed Reality fones de ouvido. O projeto é voltado para reduzir as barreiras à entrada para criar aplicativos de realidade mista e contribuem na comunidade, como todos nós crescer.

## <a name="start-your-first-mr-project"></a>Iniciar seu primeiro projeto MR

Agora que seu PC e dispositivo (s) são configurados, você está pronto para criar seu primeiro projeto de realidade misturada no Unity. Acompanhe o nosso primeiro curso MR academy, [MR Noções básicas de 100: Guia de Introdução com o Unity](holograms-100.md), e por fim, você terá um cubo em funcionamento um Headset de realidade misturada.

![Captura de tela de um cubo em um projeto do Unity realidade mista](images/mr-cube.PNG)<br>
*Seu primeiro projeto de realidade misturada no Unity - Olá, mundo!*

## <a name="learn-more-and-get-help"></a>Saiba mais e obter ajuda

Agora que você criou seu primeiro projeto MR com êxito, você está provavelmente famintos para obter mais informações! Aqui estão alguns recursos que devem ajudar a:
* [Misto de documentação do desenvolvedor realidade](mixed-reality.md) - que já está aqui, mas há muito mais fazer check-out, incluindo documentação técnica, diretrizes de design, os projetos de exemplo e estudos de caso.
* [Misto tutoriais realidade](tutorials.md) -siga tutoriais abrangendo tudo, desde como configurar projetos para implementar os principais blocos de construção MR, para a integração do Azure serviços de nuvem em seu aplicativo MR.
* [Saiba o Unity](https://unity3d.com/learn) -site do Unity oferece tutoriais, projetos e sessões de treinamento ao vivo para os criadores de cada estágio de aprendizado.

Você também pode obter ajuda desses recursos de comunidade excelentes:
* [Fóruns para desenvolvedores de realidade misturada](https://forums.hololens.com/) -fórum oficial para desenvolvedores de realidade misturada perguntar e responder a perguntas, bem como ler notícias de desenvolvimento MR diretamente da Microsoft.
* [Canal do Slack HoloDevelopers](https://holodevelopersslack.azurewebsites.net/) -mais externo robusto e engenhoso misto canal de desenvolvedor específica de realidade; os desenvolvedores aqui são úteis e experientes.
* [Fóruns do Unity](https://forum.unity3d.com/) -fóruns de oficial do Unity.

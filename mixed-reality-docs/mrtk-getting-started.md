---
title: Introdução ao MRTK versão 2
description: Para novos desenvolvedores interessados em aproveitar o MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, teste, Kit de Ferramentas de Realidade Misturada, MRTK versão 2, MRTK, ferramentas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 64f5925154a2987cd04293fd4c04bbd9f48bacbf
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87477008"
---
# <a name="getting-started-with-mrtk-for-unity"></a>Introdução ao MRTK para Unity
![MRTK](images/UX/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>O que é o MRTK (Kit de Ferramentas de Realidade Misturada)?
O MRTK é um incrível kit de ferramentas de software livre disponível desde o primeiro lançamento do HoloLens e que não existiria sem os esforços de nossa comunidade de desenvolvedores que contribuiu para a evolução dele. Nos últimos três anos, ouvimos os comentários da nossa comunidade de desenvolvedores e criamos o MRTK v2 para levar em conta as principais preocupações.  

O MRTK para Unity é um kit de desenvolvimento de software livre multiplataforma para aplicativos de realidade misturada. O MRTK fornece um sistema de entrada multiplataforma, componentes básicos e blocos de construção comuns para interações espaciais. O MRTK versão 2 destina-se a acelerar o desenvolvimento de aplicativos voltados ao Microsoft HoloLens, aos headsets imersivos do Windows Mixed Reality (VR) e à plataforma OpenVR. O projeto visa reduzir as barreiras de entrada criando aplicativos de realidade misturada e contribuindo com a comunidade à medida que todos nós crescemos.

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

Confira a [documentação do MRTK no GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para explorar mais.

## <a name="new-with-mrtk-v2"></a>Novidades com o MRTK v2
Queremos enfatizar nosso compromisso com estas ferramentas de plataforma.  Na verdade, aproveitamos o MRTK versão 2 para desenvolver nossas experiências de caixa de entrada, como o OOBE (experiência de configuração) e nosso aplicativo de Aprendizado de Realidade Misturada.  Você também pode esperar ver as novas funcionalidades do HoloLens 2 apresentadas pela primeira vez por meio do MRTK, pois acreditamos que é a melhor maneira de realizar o desenvolvimento em nossa plataforma. 

### <a name="modular"></a>Modular
Nós o criamos de uma maneira modular, de modo que não seja necessário inserir todas as partes do kit de ferramentas no projeto.  Na verdade, há alguns benefícios nessa abordagem.  Ela reduz o tamanho do projeto e facilita o gerenciamento dele.  Além disso, como o kit foi criado com objetos programáveis e é orientado por interface, também é possível substituir os componentes incluídos pelos seus próprios, a fim de dar suporte a outros serviços, sistemas e plataformas.

### <a name="cross-platform"></a>Plataforma cruzada
Falando em outras plataformas, ele tem suporte multiplataforma.  E embora isso não signifique que todas as plataformas tenham suporte pronto para uso, garantimos que nenhum código do kit de ferramentas será desfeito quando você alternar o destino de build para outras plataformas.  A robustez e a extensibilidade com o design modular colocam você em um caminho ideal para poder dar suporte a várias plataformas, como ARCore, ARKit e OpenVR.

### <a name="performant"></a>Alto desempenho
Trabalhando com plataformas móveis, nós o construímos com o desempenho em mente.  Isso é extremamente importante, e queríamos garantir que as ferramentas não trabalharão contra você.

## <a name="see-also"></a>Veja também
* [Guia de introdução ao MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Página inicial da documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Instalar as ferramentas](install-the-tools.md)
* [Portabilidade do HTK/MRTK para o MRTK versão 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

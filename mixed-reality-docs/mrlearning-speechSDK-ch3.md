---
title: Módulo Sr Learning SpeechSDK – reconhecimento de fala e transcrição
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: e5d0919a69c9e6b0c4233d23bf6d370f3def6576
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460319"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a>3.    Adicionando o componente de tradução de fala dos serviços cognitivas do Azure

Neste tutorial, aprendemos a aabout o componente de tradução de fala dos serviços cognitivas do Azure em nosso projeto, além de traduzir em três idiomas diferentes. 

1. Selecione o objeto Lunarcom_Base na hierarquia e clique em Adicionar componente no painel inspetor. Procure e selecione LunarcomTranslationRecognizer.

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> Observação: Verifique se o simulador de modo offline está desabilitado antes de testar o tradutor do SDK de fala. Para traduzir, você deve estar conectado à Internet. Consulte a imagem abaixo sobre onde encontrar essa configuração. 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. Clique na lista suspensa no LunarcomTranslationRecognizer e selecione o idioma para o qual você deseja traduzir.

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Agora, execute o aplicativo e teste o tradutor clicando no botão satélite e comece a falar. Pressione o botão satélite novamente para interromper o reconhecimento. Veja abaixo um exemplo de como deve ser sua cena. Fique à vontade para alterar o idioma na lista suspensa "idioma de destino" (consulte a imagem acima) para explorar a tradução em outros idiomas.

> Observação: Antes de testar, verifique se o simulador offline está desabilitado, conforme mostrado na imagem abaixo.
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

Abaixo está um exemplo de como deve ser a aparência de sua cena:

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Parabéns

Agora seu projeto pode traduzir as palavras que você fala em vários idiomas diferentes. Fique à vontade para brincar com os idiomas e teste a precisão da tradução. 

[Próximo tutorial: 4.  Configurar a intenção e o reconhecimento vocal natural](mrlearning-speechSDK-ch4.md)


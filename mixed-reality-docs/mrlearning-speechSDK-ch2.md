---
title: TUTORIAIS dos serviços de fala do Azure-2. Adicionando um modo offline para tradução de fala em texto local
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 1dd6c01768ddf5dda954f50e0f7507022bd59c3b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701856"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. Adicionando um modo offline para tradução de fala em texto local

Neste tutorial, adicionaremos um modo offline que permite executar a tradução de fala para texto local quando não for possível se conectar ao serviço do Azure. Também simularemos um estado desconectado.

## <a name="instructions"></a>Instruções

1. Selecione o objeto Lunarcom_Base na hierarquia e clique em Adicionar componente no painel inspetor. Procure e selecione o reconhecimento offline do Lunarcom.

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. Clique na lista suspensa no LunarcomOfflineRecognizer e selecione habilitado. Este programa o projeto para agir como o usuário não tem uma conexão. 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. Agora, pressione reproduzir no editor do Unity e teste-o. Pressione o microfone no canto inferior esquerdo da cena e comece a falar. 

> [!NOTE]
> Como estamos offline, a funcionalidade wake Word foi desabilitada. Você precisará clicar fisicamente no microfone toda vez que desejar que sua fala seja reconhecida quando estiver offline. 

Veja abaixo um exemplo de como seria a sua cena.

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>Parabéns

O modo offline foi habilitado. Agora, quando você estiver offline, ainda poderá trabalhar em seu projeto com o Speech-SDK! 


[Próximo tutorial: 3.  Adicionando o componente de tradução de fala dos serviços cognitivas do Azure](mrlearning-speechSDK-ch3.md)


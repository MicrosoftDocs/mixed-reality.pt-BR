---
title: TUTORIAIS dos serviços de fala do Azure-2. Adicionando um modo offline para tradução de fala em texto local
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 962d7d4750cf59fe56de4af9088c90e8ecd0aa16
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913213"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. adicionando um modo offline para conversão de fala em texto local

Neste tutorial, adicionaremos um modo offline que permite executar a tradução de fala para texto local quando não for possível se conectar ao serviço do Azure. Também *simularemos* um estado desconectado.

## <a name="instructions"></a>Instruções

1. Selecione o objeto Lunarcom_Base na hierarquia.

2. Clique em Adicionar componente no painel inspetor. Procure e selecione o reconhecimento offline do Lunarcom.

    ![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. Clique na lista suspensa no LunarcomOfflineRecognizer e selecione habilitado. Este programa o projeto para agir como o usuário não tem uma conexão.

    ![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. Pressione reproduzir no editor do Unity e teste-o. Pressione o microfone no canto inferior esquerdo da cena e comece a falar.

    >[!NOTE]
    >Como estamos offline, a funcionalidade wake Word foi desabilitada. Você precisará clicar fisicamente no microfone toda vez que desejar que sua fala seja reconhecida quando estiver offline.

    Veja abaixo um exemplo de como seria a sua cena.

    ![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>Parabéns

O modo offline foi habilitado. Agora, quando você estiver offline, ainda poderá trabalhar em seu projeto com o Speech-SDK!

[Próximo tutorial: 3. adicionando o componente de tradução de fala dos serviços cognitivas do Azure](mrlearning-speechSDK-ch3.md)

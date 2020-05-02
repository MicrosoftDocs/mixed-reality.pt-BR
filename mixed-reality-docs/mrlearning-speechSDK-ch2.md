---
title: Tutoriais de Serviços de Fala do Azure – 2. Adicionar um modo offline para tradução de fala em texto local
description: Conclua este curso para saber como implementar o SDK de Fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031619"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a>2. Como usar o reconhecimento de fala para executar comandos

Neste tutorial, você adicionará a capacidade de executar comandos usando o reconhecimento de fala do Azure, que permitirá que você faça algo com base na palavra ou na frase que você definir.

## <a name="objectives"></a>Objetivos

* Saiba como o reconhecimento de fala do Azure pode ser usado para executar comandos

## <a name="instructions"></a>Instruções

Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Palavra de Despertar do Lunarcom (Script)** ao objeto Lunarcom e configure-o da seguinte maneira:

* No campo **Palavra de Despertar**, insira uma frase adequada, por exemplo, _Ativar o terminal_.
* No campo **Palavra de Ignorar**, insira uma frase adequada, por exemplo, _Ignorar o terminal_.

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> O componente Reconhecedor de Palavra de Despertar do Lunarcom (Script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

Se agora você inserir o modo de jogo, como no tutorial anterior, o painel do terminal será habilitado por padrão, mas você poderá desabilitá-lo dizendo a Palavra de Ignorar, **Ignorar terminal**:

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

E habilitá-la novamente dizendo a Palavra de Despertar, **Ativar terminal**:

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.

> [!TIP]
> Se você prever que frequentemente não poderá se conectar ao Azure, também poderá implementar comandos de fala usando o MRTK de acordo com as instruções [Habilitar Comandos de Voz](mrlearning-base-ch5.md#enabling-voice-commands).

## <a name="congratulations"></a>Parabéns

Você implementou comandos de fala da plataforma Azure. Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.

No próximo tutorial, você aprenderá a traduzir a fala usando a Tradução de Fala do Azure.

[Próximo tutorial: 3. Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure](mrlearning-speechSDK-ch3.md)

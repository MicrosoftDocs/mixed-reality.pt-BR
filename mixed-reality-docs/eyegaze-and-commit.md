---
title: Focar com o olhar e confirmar
description: Visão geral do modelo de entrada de focar com o olhar e confirmar
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Acompanhamento ocular, realidade misturada, entrada, focar com o olhar, focalização com os olhos, HoloLens 2, seleção ocular
ms.openlocfilehash: 9cc27f24e1275223f33becd1ff0ec6bdf5b43a57
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66455082"
---
# <a name="eye-gaze-and-commit"></a>Focar com o olhar e confirmar
Com o HoloLens 2, temos a excelente oportunidade de tornar o recurso de focar com o olhar e confirmar mais rápido e mais confortável usando o foco com o olhar em vez do foco com a cabeça. Isso permite estender o modelo de interação comum de [focar com a cabeça e confirmar](gaze-and-commit.md): 
1. Basta olhar para um alvo e 
2. Para confirmar sua intenção de selecionar o alvo, realize uma entrada secundária explícita, como:  
   - Gesto de mão (por exemplo, fechar e abrir os dedos indicador e polegar)
   - Pressionar botão (por exemplo, em um teclado Bluetooth ou controle)
   - Comando de voz (por exemplo, "Selecionar")
   - Espera (ou seja, o usuário simplesmente continua olhando para o alvo para selecioná-lo)

No entanto, o foco com o olhar se comporta de forma muito diferente do foco com a cabeça em determinadas circunstâncias e, portanto, traz alguns desafios únicos. Nas [Diretrizes de design de foco com o olhar](eye-tracking.md), resumimos as vantagens e desafios gerais a serem considerados ao usar o acompanhamento de olho como uma entrada em seu aplicativo holográfico. Nesta seção, abordaremos considerações de design específicas do foco com o olhar e confirmação.
Primeiro, nossos olhos se movem incrivelmente rápido e, portanto, são ótimos para focalizar rapidamente algo na exibição. Isso torna o foco com o olhar ideal para ações rápidas de foco e confirmação, especialmente quando combinadas a confirmações rápidas, como pressionar um botão ou fechar e abrir os dedos indicador e polegar.
   
Em seguida, abordaremos as diretrizes de design ao usar o foco com o olhar para esse tipo de interação e discutiremos as diferenças entre o foco com a cabeça e o foco com o olhar que você deve ter em mente.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Diretrizes de design para o foco com o olhar e confirmação

**Não mostrar um cursor**: Embora seja quase impossível interagir sem um cursor ao usar o foco com a cabeça, o cursor se transforma rapidamente em uma distração e irrita ao usar o foco com o olhar. Em vez de depender de um cursor para informar ao usuário que o acompanhamento de olho está funcionando e detectou corretamente o alvo que estava sendo observado no momento, use realces visuais sutis (mais detalhes abaixo).

**Dê preferência para retornos de focalização sutis**: O que pode funcionar como um ótimo retorno visual para o foco com a cabeça pode resultar em uma experiência terrível e cansativa usando o foco com o olhar. Lembre-se de que seus olhos são extremamente rápidos, que se movem rapidamente entre os pontos em seu campo de visão. Alterações de realce rápidas e repentinas (ativar/desativar) podem resultar em retornos oscilantes ao olhar ao redor. Portanto, ao fornecer o retorno de focalização, recomendamos usar um realce sutil de movimento de entrada (e de saída ao distanciar o olhar). Isso significa que, inicialmente, você mal notaria o retorno ao olhar para um alvo. No decorrer de 500 a 1000 ms, o realce aumentaria de intensidade. Enquanto os usuários menos experientes poderiam continuar olhando para o alvo para garantir que o sistema determinasse corretamente o alvo focalizado, os usuários experientes poderiam focar e confirmar rapidamente, sem esperar o retorno atingir sua intensidade máxima. Além disso, também recomendamos usar um movimento de saída ao esmaecer o retorno da focalização. As pesquisas mostram que alterações rápidas de movimento e contraste são bastante perceptíveis na visão periférica (ou seja, a área do campo de visão à qual você não está olhando). O esmaecimento não precisa ser tão lento quanto o movimento de entrada. Ele só é essencial quando você tiver alto contraste ou alterações de cor no realce. Se o retorno de focalização for bastante sutil, você provavelmente não perceberá uma diferença.

**Esteja atento à sincronização dos sinais de foco e confirmação**: A sincronização dos sinais de entrada pode ser mais acessível para comandos simples de foco e confirmação, então fique tranquilo! É algo que exige atenção caso você deseje usar ações de confirmação mais complexas, embora estas possam envolver comandos de voz longos ou gestos de mão complicados. Imagine que você olhe para um alvo e emita um comando de voz longo. Considerando o tempo necessário para falar e para o sistema detectar o que você disse, o foco do seu olhar provavelmente já vai ter mudado para um novo alvo no cenário. Portanto, informe aos usuários de que eles precisam manter o olhar fixo no alvo até que o comando seja reconhecido, ou lide com a entrada de maneira a determinar o início do comando e o que o usuário estava olhando naquele momento.

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Gestos de mão](gestures.md)
* [Entrada de voz](voice-design.md)
* [Controladores de movimentos](motion-controllers.md)

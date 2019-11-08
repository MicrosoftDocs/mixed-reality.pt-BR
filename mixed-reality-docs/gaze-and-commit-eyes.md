---
title: Focar com o olhar e confirmar
description: Visão geral do modelo de entrada de focar com o olhar e confirmar
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Acompanhamento ocular, realidade misturada, entrada, focar com o olhar, focalização com os olhos, HoloLens 2, seleção ocular
ms.openlocfilehash: 89f5031635f2b67ba4c9afdf605559c2b9da4ac2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437822"
---
# <a name="eye-gaze-and-commit"></a>Focar com o olhar e confirmar
_Focar com o olhar e confirmar_ é um caso especial do modelo de entrada de [focar com o olhar e confirmar](gaze-and-commit.md) que envolve o direcionamento de um objeto simplesmente olhando-o e executando ações com uma entrada de _confirmação_ secundária, como um gesto de mão, comando de voz ou entrada periférica (por ex., controlador de jogo). 

Com o HoloLens 2, temos a excelente oportunidade de tornar o recurso de _focar com o olhar e confirmar_ mais rápido e mais confortável usando o foco com o olhar em vez do foco com a cabeça. Isso permite estender o modelo de interação comum de [focar com a cabeça e confirmar](gaze-and-commit.md): 
1. Basta olhar para um alvo e 
2. Para confirmar sua intenção de selecionar o alvo, realize uma entrada secundária explícita, como:  
   - Gesto de mão (por exemplo, fechar e abrir os dedos indicador e polegar)
   - Pressionar botão (por exemplo, em um teclado Bluetooth ou controle)
   - Comando de voz (por exemplo, "Selecionar")
   - Espera (ou seja, o usuário simplesmente continua olhando para o alvo para selecioná-lo)

No entanto, o foco com o olhar se comporta de forma muito diferente do foco com a cabeça em determinadas circunstâncias e, portanto, traz alguns desafios únicos. Nas [Diretrizes de design de foco com o olhar](eye-tracking.md), resumimos as vantagens e desafios gerais a serem considerados ao usar o acompanhamento de olho como uma entrada em seu aplicativo holográfico. Nesta seção, abordaremos considerações de design específicas de _focar com o olhar e confirmar_.
Primeiro, nossos olhos se movem incrivelmente rápido e, portanto, são ótimos para focalizar rapidamente algo na exibição. Isso torna o foco com o olhar ideal para ações rápidas de foco com o olhar e confirmação, especialmente quando combinadas com confirmações rápidas, como pressionar um botão ou fechar e abrir dedos indicador e polegar.
   
Em seguida, abordaremos as diretrizes de design ao usar o foco com o olhar para esse tipo de interação e discutiremos as diferenças entre o foco com a cabeça e o foco com o olhar que você deve ter em mente.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Diretrizes de design para o foco com o olhar e confirmação

**Não mostrar um cursor**: Embora seja quase impossível interagir sem um cursor ao usar o foco com a cabeça, o cursor se transforma rapidamente em uma distração e irrita ao usar o foco com o olhar. Em vez de depender de um cursor para informar ao usuário que o acompanhamento de olho está funcionando e detectou corretamente o alvo que estava sendo observado no momento, use realces visuais sutis (mais detalhes abaixo).

**Dê preferência para retornos de focalização sutis**: O que pode funcionar como um ótimo retorno visual para o foco com a cabeça pode resultar em uma experiência terrível e cansativa usando o foco com o olhar. Lembre-se de que seus olhos são extremamente rápidos, que se movem rapidamente entre os pontos em seu campo de visão. Alterações de realce rápidas e repentinas (ativar/desativar) podem resultar em retornos oscilantes ao olhar ao redor. Portanto, ao fornecer o retorno de focalização, recomendamos usar um realce sutil de movimento de entrada (e de saída ao distanciar o olhar). Isso significa que, inicialmente, você mal notaria o retorno ao olhar para um alvo. No decorrer de 500 a 1000 ms, o realce aumentaria de intensidade. Enquanto os usuários novatos poderiam continuar olhando para o alvo para garantir que o sistema determinasse corretamente o alvo focalizado, os usuários experientes poderiam focar com o olhar e confirmar rapidamente, sem esperar o retorno atingir sua intensidade máxima. Além disso, também recomendamos usar um movimento de saída ao esmaecer o retorno da focalização. As pesquisas mostram que alterações rápidas de movimento e contraste são bastante perceptíveis na visão periférica (a área do campo de visão à qual você não está olhando).
O esmaecimento não precisa ser tão lento quanto o movimento de entrada. Ele só é essencial quando você tiver alto contraste ou alterações de cor no realce. Se o retorno de focalização for bastante sutil, você provavelmente não perceberá uma diferença.

**Esteja atento à sincronização dos sinais de foco e confirmação**: A sincronização dos sinais de entrada pode ser mais acessível para simples comandos de fechar e abrir dedos indicador e polegar e pressionamentos de botão. É algo que exige atenção caso você deseje usar ações de confirmação mais complexas que possam envolver comandos de voz longos ou gestos de mão complicados. Imagine que você olhe para um alvo e emita um comando de voz longo. Considerando o tempo necessário para dizer e para o sistema detectar o que você disse, o foco do seu olhar provavelmente já vai ter mudado para um novo alvo na cena. Portanto, informe aos usuários de que eles precisam manter o olhar fixo no alvo até que o comando seja reconhecido, ou lide com a entrada de maneira a determinar o início do comando e o que o usuário estava olhando naquele momento.

## <a name="see-also"></a>Consulte também
* [Interação ocular] (eye-gaze-interaction.md)
* [Acompanhamento ocular no HoloLens 2] (eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)

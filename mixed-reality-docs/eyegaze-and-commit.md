---
title: Olhar olho e confirmar
description: Visão geral do modelo de entrada olhar olho e confirmar
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Acompanhamento de olhos, misturadas realidade, entrada, olhar olho, direcionamento de olhos, HoloLens 2, seleção de olho
ms.openlocfilehash: 9cc27f24e1275223f33becd1ff0ec6bdf5b43a57
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66455082"
---
# <a name="eye-gaze-and-commit"></a>Olhar olho e confirmar
Com o HoloLens 2, temos a excelente oportunidade de tornar olhar & confirmação mais rápida e mais confortável usando olhar de olho em vez de olhar principal. Isso permite estender comuns [olhar head e confirmação](gaze-and-commit.md) modelo de interação: 
1. Basta examinar a um destino e 
2. Para confirmar sua intenção para selecionar o destino, execute um secundário explícito de entrada, como r:  
   - Gestos de mão (por exemplo, um ar toque)
   - Pressionar o botão (por exemplo, em um teclado Bluetooth ou clicker)
   - Comando de voz (por exemplo, "Select")
   - Dwelling (ou seja, o usuário simplesmente mantém examinando o destino para selecionar)

No entanto, a olhar de olho se comporta de forma muito diferente para olhar principal de determinadas maneiras e, portanto, é fornecido com um número de desafios únicos. No [diretrizes de Design de olhares olho](eye-tracking.md), resumimos vantagens gerais e desafios a serem considerados ao usar o controle como uma entrada em seu aplicativo holográfica de olho. Nesta seção, abordaremos as considerações de design específicas para olhar olho & confirmação.
Primeiro, seus olhos mover incrivelmente rápida e, portanto, são ótimos para direcionamento rapidamente no modo de exibição. Isso torna olho olhares ideal para ações rápidas que olhar e confirmação especialmente quando combinadas com confirmações rápidas como um pressionamento de botão-indicador e polegar.
   
A seguir, falaremos sobre as diretrizes de design quando usando olho mantenha o foco para esse tipo de interação e discutir as diferenças entre head e olho olhar que você deve ter em mente.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Diretrizes para olhar olho e confirmação de design

**Não mostrar um cursor**: Embora é quase impossível interagir sem um cursor ao usar o head olhares, o cursor se transforma rapidamente causa distração e irritantes ao usar um olhar de olho. Em vez de depender de um cursor para informar ao usuário se o acompanhamento a olho nu esteja funcionando e tenha corretamente detectada no momento pesquisado no destino, o visual sutis de uso destaca (mais detalhes abaixo).

**Se esforçam para comentários de focalização combinada sutis**: O que parece ótimo comentários visuais para olhar principal pode resultar em experiências terríveis enorme e cansativa usando olhar de olho. Lembre-se de que seus olhos são extremamente rápidos, darting rapidamente entre pontos em seu campo de exibição. Alterações rápidas realce repentina (ativado/desativado) podem resultar em comentários flickery ao procurar ao redor. Portanto, ao fornecer comentários em foco, recomendamos usar um realce perfeitamente combinada em (e combinada-out ao procurar distância). Isso significa que primeiro você mal Note os comentários ao examinar um destino. Durante o curso de 500 a 1000 ms, o realce aumentaria de intensidade. Enquanto usuários menos experientes poderiam continuar procurando no destino para garantir que o sistema tiver determinado corretamente o destino com foco, os usuários experientes poderiam rapidamente olhares & são confirmadas sem esperar até que os comentários são de sua intensidade total. Além disso, é também recomendável usar um mistura-out quando o desaparecimento dos comentários em foco. Pesquisa mostrou que alterações rápidas de movimento e contraste são muito perceptíveis no sua visão periférica (portanto, a área do campo visual em que você está procurando não). O esmaecimento não precisa ser tão lenta quanto o blend-in. Isso só é essencial quando você tiver alto contraste ou alterações de cor para o realce. Se os comentários em foco era bastante sutis para começar, você provavelmente não perceberá uma diferença.

**Fique atento sincronizando sinais olhar e confirmação**: A sincronização de sinais de entrada pode ser menor do desafio para olhar simple e a confirmação, portanto, não se preocupe! É algo que você fique atento caso você deseje usar ações de confirmação mais complicadas, embora o que pode envolver a comandos de voz longo ou gestos de mão complicada. Imagine que você examinar o destino e emitido um comando de voz longo. Levadas em conta o tempo necessário para falar e a hora em que o sistema precisava para detectar o que você disse, seu foco de olho geralmente tempo passou a algum novo destino na cena. Portanto, torne seus usuários cientes de que eles podem precisar continuar procurando em um destino até que o comando foi reconhecido ou lidar com a entrada de uma maneira para determinar o início do comando e que o usuário tivesse sido observando naquela época.

## <a name="see-also"></a>Consulte também
* [Focar com a cabeça e confirmar](gaze-and-commit.md)
* [Gestos de mão](gestures.md)
* [Entrada de voz](voice-design.md)
* [Controladores de movimentos](motion-controllers.md)

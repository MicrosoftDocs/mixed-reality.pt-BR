---
title: Focar com o olhar e esperar
description: Visão geral do modelo de entrada de focar com o olhar e esperar
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: Acompanhamento Ocular, Realidade Misturada, Entrada, Foco com o Olhar, Focalização com os Olhos, HoloLens 2, Seleção Ocular, Esperar
ms.openlocfilehash: ba793f6b1a95fe4b95aa9a043d36823487886b5e
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604897"
---
# <a name="eye-gaze-and-dwell"></a>Focar com o olhar e esperar

O modelo de interação de _"focar com o olhar e esperar"_ é um caso especial do modelo de interação de [focar com o olhar e esperar](gaze-and-commit.md):
1. Basta olhar para um alvo e 
2. Para confirmar sua intenção de selecionar o alvo, realize uma entrada secundária explícita: _Basta continuar olhando o alvo que você gostaria de selecionar_.

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a>Vantagens do modelo de interação “focar com o olhar e esperar” 
Quando as mãos já estiverem ocupadas com uma tarefa ou segurando ferramentas, usá-las para interagir com hologramas talvez não seja uma opção.
Uma alternativa de interação sem mãos para selecionar hologramas é “focar com o olhar e esperar” ou, em outras palavras, _"olhar e encarar"_ . A vantagem dessa abordagem é que mesmo os usuários com restrição severa, que talvez não consigam mexer completamente a cabeça ou o corpo, podem interagir com hologramas (por exemplo, em um ambiente de trabalho altamente confinado).
O usuário fica olhando o alvo que gostaria de selecionar e um comentário de espera diferente é exibido para indicar o processo.


## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a>Desafios do modelo de interação de “focar com o olhar e esperar”
Em geral, será recomendável usar apenas ativações baseadas em espera como o último fallback se nenhuma entrada de voz nem de mão estiver disponível. O motivo é que a opção de tempo de espera pode ser muito complicada. Usuários iniciantes aceitam tempos de espera mais longos, enquanto usuários experientes desejam navegar de maneira rápida e eficiente por suas experiências. Isso leva ao desafio de como ajustar o tempo de espera para as necessidades específicas de um usuário.
Se o tempo de espera for curto demais: O usuário poderá se sentir sobrecarregado por ter que fazer os hologramas reagirem ao foco visual o tempo todo. Se o tempo de espera for longo demais: A experiência poderá parecer muito lenta e interruptiva, já que o usuário precisará continuar olhando os alvos por um longo tempo.

## <a name="design-recommendations"></a>Recomendações sobre design
É recomendável usar uma abordagem de dois estados para comentários de espera:
1. *Atraso inicial*: quando o usuário começa a olhar um alvo, nada deve acontecer imediatamente, pois isso pode resultar em uma experiência de usuário desagradável e desanimadora. Em vez disso, inicie um temporizador para detectar se o usuário está encarando intencionalmente o alvo ou apenas passando os olhos por ele.
Recomendamos um tempo inicial de 150 a 250 ms em uma determinada proximidade (o que significa que o usuário está fitando um grande alvo em vez de passando os olhos por ele).  
2. *Iniciar comentários de espera:* depois de verificar se o usuário está olhando intencionalmente o alvo, comece a mostrar os comentários de espera para informar o usuário de que a ativação da espera está sendo iniciada. 
3. *Comentários contínuos:* embora o usuário continue olhando o alvo, mostre um indicador de progresso contínuo para que ele saiba que precisa continuar olhando. Especificamente para a entrada com foco de olhar, recomendamos _atrair a atenção visual do usuário_ começando com um círculo ou uma esfera maior que se contrai para uma versão menor. Mostrar um indicador para o estado final (círculo pequeno) ajudará a se comunicar com o usuário quando a espera for concluída. Uma ilustração de exemplo é mostrada abaixo. 
4. *Conclusão:* se o usuário continuou encarando o alvo (durante outros 650 a 850 ms), conclua a ativação da espera e selecione o alvo que você olhou.

![Estados de espera](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a>Veja também
* [Acompanhamento ocular](eye-tracking.md)
* [Focar com o olhar e confirmar](gaze-and-commit-eyes.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Entrada de voz](voice-design.md)

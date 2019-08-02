---
title: Módulo Sr Learning SpeechSDK – reconhecimento de fala e transcrição
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: fc65dccfcbc181af0c0b321374c721797e120e5d
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460332"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a>Módulo de aprendizagem do SDK de fala – controle de Rocket Launcher usando comandos de fala

Nesta lição, usaremos o recurso de intenção do serviço de fala do Azure para entender a intenção da fala. Usaremos a intenção de fala detectada como comandos de voz para controlar o iniciador do Rocket. Durante esta lição, iremos importar o ativo do Rocket Launcher e nós iremos modelar os comandos de voz de intenção detectados para botões de controle predefinidos para controlar o Rocket. 

## <a name="objectives"></a>Objetivos

- Saiba como conectar a intenção de fala como comandos de voz.
- Saiba como usar comandos de voz da intenção de fala como comandos de entrada de controle de Rocket.

## <a name="instructions"></a>Instruções
1. Neste tutorial, usaremos um ativo "BaseModule" para integrar o Rocket Launcher com os comandos de fala. Para isso, precisamos importar o ativo para nosso projeto. Você pode baixar o ativo "Rocket Launcher" usando este link (anexar o link). 

2. Para importar o ativo, acesse ativos-> Importar pacote-> pacote personalizado-> Navegue até o arquivo baixado e clique em importar.

![module4chapter5step1](images/module4chapter5step1.PNG)

3. Depois de importar o ativo "Rocket Launcher", navegue na pasta "Rocket Launcher"-> pré-fabricados-> selecione "Rocket Launcher_Complete" e, em seguida, arraste-o e solte-o na hierarquia de cena existente.

![module4chapter5step2](images/module4chapter5step2.PNG)

4. Agora, precisamos integrar nosso "iniciador do Rocket" com nosso projeto LUIS que trabalhamos em nossa lição anterior (link para lesson4). Para isso, expanda o pré-fabricado "Rocket Launcher_Complete" na hierarquia e encontre os botões "LaunchRoundButton", "ResetRoundButton" e "dicas de posicionamento".

![module4chapter5step3](images/module4chapter5step3.PNG)

5. Selecione "LaunchRoundButton" e, no painel Inspetor, vá para "interagir" e, em eventos "OnClick ()", arraste e solte o pré-fabricado "LunarModule". Em seguida, selecione a lista suspensa função e selecione "LunarModule" e, em seguida, navegue até a função "StartThruster ()" e selecione-a.

![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. Selecione "ResetRoundButton" e, no painel Inspetor, vá para "interagir" e, em eventos "OnClick ()", arraste e solte o pré-fabricado "LunarModule". Em seguida, selecione a lista suspensa função e selecione "LunarModule" e, em seguida, navegue até a função "resetModule ()" e selecione-a.

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. Selecione "dicas de posicionamento" e, no painel Inspetor, vá para "interagir" e, em eventos "OnClick ()", arraste e solte o pré-fabricado "LunarModule". Em seguida, selecione a lista suspensa função e selecione "LunarModule" e, em seguida, navegue até a função "TogglePlacementHints" e selecione ToggleGameOBjects ().

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  Em seguida, selecione Lunarcom_Completed pré-fabricado na hierarquia e navegue até o script "Lunarcom Recognizer" no Inspetor e, em seguida, arraste e solte os botões "LaunchRoundButton", "ResetRoundButton" e "dicas de posicionamento" em seus respectivos locais.

![module4chapter5step4](images/module4chapter5step4.PNG)

9. Pressione o botão reproduzir no editor do Unity e clique no botão "Rocket" e tenha preenchido as frases como "botão de inicialização do push Rocket", "Mostre-me uma dica de posicionamento", "Pressione o botão REST" ou quaisquer outras frases relacionadas à solicitação de inicialização, redefinição ou dica para o iniciador do Rocket.

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a>Parabéns

Nesta lição, aprendemos como conectar os comandos de fala habilitados para ia a comandos de voz para usá-lo como um método de entrada. Agora, nosso programa pode usar a intenção dos alto-falantes como comandos de voz para fornecer entradas para o iniciador do Rocket.

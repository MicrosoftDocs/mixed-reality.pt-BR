---
title: Módulo Sr Learning SpeechSDK – reconhecimento de fala e transcrição
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: 43a6f02eaf09fcf43775374fae4fbe2d0bc8c346
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977984"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="b1f04-104">Módulo de aprendizagem do SDK de fala – controle de Rocket Launcher usando comandos de fala</span><span class="sxs-lookup"><span data-stu-id="b1f04-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="b1f04-105">Nesta lição, usaremos o recurso de intenção do serviço de fala do Azure para entender a intenção da fala.</span><span class="sxs-lookup"><span data-stu-id="b1f04-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="b1f04-106">Usaremos a intenção de fala detectada como comandos de voz para controlar o iniciador do Rocket.</span><span class="sxs-lookup"><span data-stu-id="b1f04-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="b1f04-107">Durante esta lição, iremos importar o ativo do Rocket Launcher e nós iremos modelar os comandos de voz de intenção detectados para botões de controle predefinidos para controlar o Rocket.</span><span class="sxs-lookup"><span data-stu-id="b1f04-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span> 

## <a name="objectives"></a><span data-ttu-id="b1f04-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b1f04-108">Objectives</span></span>

- <span data-ttu-id="b1f04-109">Saiba como conectar a intenção de fala como comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="b1f04-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="b1f04-110">Saiba como usar comandos de voz da intenção de fala como comandos de entrada de controle de Rocket.</span><span class="sxs-lookup"><span data-stu-id="b1f04-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="b1f04-111">Instruções</span><span class="sxs-lookup"><span data-stu-id="b1f04-111">Instructions</span></span>
1. <span data-ttu-id="b1f04-112">Neste tutorial, usaremos um ativo "BaseModule" para integrar o Rocket Launcher com os comandos de fala.</span><span class="sxs-lookup"><span data-stu-id="b1f04-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="b1f04-113">Para isso, precisamos importar o ativo para nosso projeto.</span><span class="sxs-lookup"><span data-stu-id="b1f04-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="b1f04-114">Você pode baixar o ativo do "Rocket Launcher" usando este [link](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2).</span><span class="sxs-lookup"><span data-stu-id="b1f04-114">You can download the "Rocket Launcher" asset using this [link](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2).</span></span> 

2. <span data-ttu-id="b1f04-115">Para importar o ativo, acesse ativos-> Importar pacote-> pacote personalizado-> Navegue até o arquivo baixado e clique em importar.</span><span class="sxs-lookup"><span data-stu-id="b1f04-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="b1f04-117">Depois de importar o ativo "ativos do módulo base", navegue dentro da pasta "ativos do módulo base"-> pré-fabricados-> selecione "Rocket Launcher_Complete" e, em seguida, arraste-o e solte-o na hierarquia de cena existente.</span><span class="sxs-lookup"><span data-stu-id="b1f04-117">After importing the  "Base Module Assets" asset, navigate inside the "Base Module Assets" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="b1f04-119">Agora, precisamos integrar nosso "iniciador do Rocket" com nosso projeto LUIS que trabalhamos em nossa [lição](mrlearning-speechSDK-ch4.md)anterior da lição.</span><span class="sxs-lookup"><span data-stu-id="b1f04-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson [lesson](mrlearning-speechSDK-ch4.md).</span></span> <span data-ttu-id="b1f04-120">Para isso, expanda o pré-fabricado "Rocket Launcher_Complete" na hierarquia e encontre os botões "LaunchRoundButton", "ResetRoundButton" e "dicas de posicionamento".</span><span class="sxs-lookup"><span data-stu-id="b1f04-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="b1f04-122">Selecione "LaunchRoundButton" e, no painel Inspetor, vá para "interagir" e, em eventos "OnClick ()", arraste e solte o pré-fabricado "LunarModule".</span><span class="sxs-lookup"><span data-stu-id="b1f04-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="b1f04-123">Em seguida, selecione a lista suspensa função e selecione "LunarModule" e, em seguida, navegue até a função "StartThruster ()" e selecione-a.</span><span class="sxs-lookup"><span data-stu-id="b1f04-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="b1f04-126">Selecione "ResetRoundButton" e, no painel Inspetor, vá para "interagir" e, em eventos "OnClick ()", arraste e solte o pré-fabricado "LunarModule".</span><span class="sxs-lookup"><span data-stu-id="b1f04-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="b1f04-127">Em seguida, selecione a lista suspensa função e selecione "LunarModule" e, em seguida, navegue até a função "resetModule ()" e selecione-a.</span><span class="sxs-lookup"><span data-stu-id="b1f04-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="b1f04-129">Selecione "dicas de posicionamento" e, no painel Inspetor, vá para "interagir" e, em eventos "OnClick ()", arraste e solte o pré-fabricado "LunarModule".</span><span class="sxs-lookup"><span data-stu-id="b1f04-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="b1f04-130">Em seguida, selecione a lista suspensa função e selecione "LunarModule" e, em seguida, navegue até a função "TogglePlacementHints" e selecione ToggleGameOBjects ().</span><span class="sxs-lookup"><span data-stu-id="b1f04-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  <span data-ttu-id="b1f04-132">Em seguida, selecione Lunarcom_Completed pré-fabricado na hierarquia e navegue até o script "Lunarcom Recognizer" no Inspetor e, em seguida, arraste e solte os botões "LaunchRoundButton", "ResetRoundButton" e "dicas de posicionamento" em seus respectivos locais.</span><span class="sxs-lookup"><span data-stu-id="b1f04-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="b1f04-134">Pressione o botão reproduzir no editor do Unity e clique no botão "Rocket" e tenha preenchido as frases como "botão de inicialização do push Rocket", "Mostre-me uma dica de posicionamento", "Pressione o botão REST" ou quaisquer outras frases relacionadas à solicitação de inicialização, redefinição ou dica para o iniciador do Rocket.</span><span class="sxs-lookup"><span data-stu-id="b1f04-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="b1f04-138">Parabéns</span><span class="sxs-lookup"><span data-stu-id="b1f04-138">Congratulations</span></span>

<span data-ttu-id="b1f04-139">Nesta lição, aprendemos como conectar os comandos de fala habilitados para ia a comandos de voz para usá-lo como um método de entrada.</span><span class="sxs-lookup"><span data-stu-id="b1f04-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="b1f04-140">Agora, nosso programa pode usar a intenção dos alto-falantes como comandos de voz para fornecer entradas para o iniciador do Rocket.</span><span class="sxs-lookup"><span data-stu-id="b1f04-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>


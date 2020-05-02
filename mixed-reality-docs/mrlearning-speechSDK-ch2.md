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
# <a name="2-using-speech-recognition-to-execute-commands"></a><span data-ttu-id="6dffa-105">2. Como usar o reconhecimento de fala para executar comandos</span><span class="sxs-lookup"><span data-stu-id="6dffa-105">2. Using speech recognition to execute commands</span></span>

<span data-ttu-id="6dffa-106">Neste tutorial, você adicionará a capacidade de executar comandos usando o reconhecimento de fala do Azure, que permitirá que você faça algo com base na palavra ou na frase que você definir.</span><span class="sxs-lookup"><span data-stu-id="6dffa-106">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="6dffa-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6dffa-107">Objectives</span></span>

* <span data-ttu-id="6dffa-108">Saiba como o reconhecimento de fala do Azure pode ser usado para executar comandos</span><span class="sxs-lookup"><span data-stu-id="6dffa-108">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="6dffa-109">Instruções</span><span class="sxs-lookup"><span data-stu-id="6dffa-109">Instructions</span></span>

<span data-ttu-id="6dffa-110">Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Palavra de Despertar do Lunarcom (Script)** ao objeto Lunarcom e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6dffa-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="6dffa-111">No campo **Palavra de Despertar**, insira uma frase adequada, por exemplo, _Ativar o terminal_.</span><span class="sxs-lookup"><span data-stu-id="6dffa-111">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="6dffa-112">No campo **Palavra de Ignorar**, insira uma frase adequada, por exemplo, _Ignorar o terminal_.</span><span class="sxs-lookup"><span data-stu-id="6dffa-112">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="6dffa-114">O componente Reconhecedor de Palavra de Despertar do Lunarcom (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="6dffa-114">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="6dffa-115">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="6dffa-115">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="6dffa-116">Se agora você inserir o modo de jogo, como no tutorial anterior, o painel do terminal será habilitado por padrão, mas você poderá desabilitá-lo dizendo a Palavra de Ignorar, **Ignorar terminal**:</span><span class="sxs-lookup"><span data-stu-id="6dffa-116">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="6dffa-118">E habilitá-la novamente dizendo a Palavra de Despertar, **Ativar terminal**:</span><span class="sxs-lookup"><span data-stu-id="6dffa-118">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="6dffa-120">O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="6dffa-120">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="6dffa-121">Se você prever que frequentemente não poderá se conectar ao Azure, também poderá implementar comandos de fala usando o MRTK de acordo com as instruções [Habilitar Comandos de Voz](mrlearning-base-ch5.md#enabling-voice-commands).</span><span class="sxs-lookup"><span data-stu-id="6dffa-121">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Enabling Voice Commands](mrlearning-base-ch5.md#enabling-voice-commands) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6dffa-122">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6dffa-122">Congratulations</span></span>

<span data-ttu-id="6dffa-123">Você implementou comandos de fala da plataforma Azure.</span><span class="sxs-lookup"><span data-stu-id="6dffa-123">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="6dffa-124">Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="6dffa-124">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="6dffa-125">No próximo tutorial, você aprenderá a traduzir a fala usando a Tradução de Fala do Azure.</span><span class="sxs-lookup"><span data-stu-id="6dffa-125">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

[<span data-ttu-id="6dffa-126">Próximo tutorial: 3. Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure</span><span class="sxs-lookup"><span data-stu-id="6dffa-126">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

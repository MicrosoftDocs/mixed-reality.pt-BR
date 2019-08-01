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
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="6d033-105">2. Adicionando um modo offline para tradução de fala em texto local</span><span class="sxs-lookup"><span data-stu-id="6d033-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="6d033-106">Neste tutorial, adicionaremos um modo offline que permite executar a tradução de fala para texto local quando não for possível se conectar ao serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="6d033-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="6d033-107">Também simularemos um estado desconectado.</span><span class="sxs-lookup"><span data-stu-id="6d033-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="6d033-108">Instruções</span><span class="sxs-lookup"><span data-stu-id="6d033-108">Instructions</span></span>

1. <span data-ttu-id="6d033-109">Selecione o objeto Lunarcom_Base na hierarquia e clique em Adicionar componente no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="6d033-109">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="6d033-110">Procure e selecione o reconhecimento offline do Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="6d033-110">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="6d033-112">Clique na lista suspensa no LunarcomOfflineRecognizer e selecione habilitado.</span><span class="sxs-lookup"><span data-stu-id="6d033-112">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="6d033-113">Este programa o projeto para agir como o usuário não tem uma conexão.</span><span class="sxs-lookup"><span data-stu-id="6d033-113">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="6d033-115">Agora, pressione reproduzir no editor do Unity e teste-o.</span><span class="sxs-lookup"><span data-stu-id="6d033-115">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="6d033-116">Pressione o microfone no canto inferior esquerdo da cena e comece a falar.</span><span class="sxs-lookup"><span data-stu-id="6d033-116">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="6d033-117">Como estamos offline, a funcionalidade wake Word foi desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6d033-117">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="6d033-118">Você precisará clicar fisicamente no microfone toda vez que desejar que sua fala seja reconhecida quando estiver offline.</span><span class="sxs-lookup"><span data-stu-id="6d033-118">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="6d033-119">Veja abaixo um exemplo de como seria a sua cena.</span><span class="sxs-lookup"><span data-stu-id="6d033-119">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="6d033-121">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6d033-121">Congratulations</span></span>

<span data-ttu-id="6d033-122">O modo offline foi habilitado.</span><span class="sxs-lookup"><span data-stu-id="6d033-122">The offline mode has been enabled.</span></span> <span data-ttu-id="6d033-123">Agora, quando você estiver offline, ainda poderá trabalhar em seu projeto com o Speech-SDK!</span><span class="sxs-lookup"><span data-stu-id="6d033-123">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="6d033-124">Próximo tutorial: 3.  Adicionando o componente de tradução de fala dos serviços cognitivas do Azure</span><span class="sxs-lookup"><span data-stu-id="6d033-124">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)


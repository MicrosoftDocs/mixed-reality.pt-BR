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
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="6bee7-105">2. adicionando um modo offline para conversão de fala em texto local</span><span class="sxs-lookup"><span data-stu-id="6bee7-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="6bee7-106">Neste tutorial, adicionaremos um modo offline que permite executar a tradução de fala para texto local quando não for possível se conectar ao serviço do Azure.</span><span class="sxs-lookup"><span data-stu-id="6bee7-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="6bee7-107">Também *simularemos* um estado desconectado.</span><span class="sxs-lookup"><span data-stu-id="6bee7-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="6bee7-108">Instruções</span><span class="sxs-lookup"><span data-stu-id="6bee7-108">Instructions</span></span>

1. <span data-ttu-id="6bee7-109">Selecione o objeto Lunarcom_Base na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="6bee7-109">Select the Lunarcom_Base object in the hierarchy.</span></span>

2. <span data-ttu-id="6bee7-110">Clique em Adicionar componente no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="6bee7-110">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="6bee7-111">Procure e selecione o reconhecimento offline do Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="6bee7-111">Search for and select the Lunarcom Offline Recognition.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. <span data-ttu-id="6bee7-113">Clique na lista suspensa no LunarcomOfflineRecognizer e selecione habilitado.</span><span class="sxs-lookup"><span data-stu-id="6bee7-113">Click the drop-down in the LunarcomOfflineRecognizer and select Enabled.</span></span> <span data-ttu-id="6bee7-114">Este programa o projeto para agir como o usuário não tem uma conexão.</span><span class="sxs-lookup"><span data-stu-id="6bee7-114">This programs the project to act like the user doesn't have a connection.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. <span data-ttu-id="6bee7-116">Pressione reproduzir no editor do Unity e teste-o.</span><span class="sxs-lookup"><span data-stu-id="6bee7-116">Press Play in Unity Editor, and test it.</span></span> <span data-ttu-id="6bee7-117">Pressione o microfone no canto inferior esquerdo da cena e comece a falar.</span><span class="sxs-lookup"><span data-stu-id="6bee7-117">Press the microphone in the bottom-left corner in the scene and begin speaking.</span></span>

    >[!NOTE]
    ><span data-ttu-id="6bee7-118">Como estamos offline, a funcionalidade wake Word foi desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6bee7-118">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="6bee7-119">Você precisará clicar fisicamente no microfone toda vez que desejar que sua fala seja reconhecida quando estiver offline.</span><span class="sxs-lookup"><span data-stu-id="6bee7-119">You'll need to physically click the microphone every time you wish to have your speech recognized when offline.</span></span>

    <span data-ttu-id="6bee7-120">Veja abaixo um exemplo de como seria a sua cena.</span><span class="sxs-lookup"><span data-stu-id="6bee7-120">Below is an example of what your scene could look like.</span></span>

    ![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="6bee7-122">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6bee7-122">Congratulations</span></span>

<span data-ttu-id="6bee7-123">O modo offline foi habilitado.</span><span class="sxs-lookup"><span data-stu-id="6bee7-123">The offline mode has been enabled.</span></span> <span data-ttu-id="6bee7-124">Agora, quando você estiver offline, ainda poderá trabalhar em seu projeto com o Speech-SDK!</span><span class="sxs-lookup"><span data-stu-id="6bee7-124">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span>

[<span data-ttu-id="6bee7-125">Próximo tutorial: 3. adicionando o componente de tradução de fala dos serviços cognitivas do Azure</span><span class="sxs-lookup"><span data-stu-id="6bee7-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

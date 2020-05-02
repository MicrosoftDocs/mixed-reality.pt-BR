---
title: Tutoriais de Serviços de Fala do Azure – 3. Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure
description: Neste curso, você aprenderá a implementar o SDK de Fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028335"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="50d8e-105">3. Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure</span><span class="sxs-lookup"><span data-stu-id="50d8e-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="50d8e-106">Neste tutorial, você adicionará a tradução de fala ao seu projeto, o que permitirá que você traduza e transcreva sua fala em três idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="50d8e-106">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="50d8e-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="50d8e-107">Objectives</span></span>

* <span data-ttu-id="50d8e-108">Saiba como integrar a Tradução de Fala do Azure</span><span class="sxs-lookup"><span data-stu-id="50d8e-108">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="50d8e-109">Instruções</span><span class="sxs-lookup"><span data-stu-id="50d8e-109">Instructions</span></span>

<span data-ttu-id="50d8e-110">Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Tradução do Lunarcom (Script)** ao objeto Lunarcom e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="50d8e-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="50d8e-111">Altere o **Idioma de Destino** para um idioma de sua escolha, por exemplo, _Alemão_</span><span class="sxs-lookup"><span data-stu-id="50d8e-111">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="50d8e-113">O componente Reconhecedor de Tradução do Lunarcom (Script) não faz parte do MRTK.</span><span class="sxs-lookup"><span data-stu-id="50d8e-113">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="50d8e-114">Ele foi fornecido com os ativos deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="50d8e-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="50d8e-115">Se agora você entrar no modo de Jogo, poderá testar a tradução de fala primeiro pressionando o botão de satélite.</span><span class="sxs-lookup"><span data-stu-id="50d8e-115">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="50d8e-116">Em seguida, supondo que o computador tenha um microfone, quando você disser algo, sua fala será traduzida para o idioma escolhido e transcrita no painel do terminal:</span><span class="sxs-lookup"><span data-stu-id="50d8e-116">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="50d8e-118">O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="50d8e-118">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="50d8e-119">Parabéns</span><span class="sxs-lookup"><span data-stu-id="50d8e-119">Congratulations</span></span>

<span data-ttu-id="50d8e-120">Agora, seu projeto pode traduzir com êxito as palavras que você fala em vários idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="50d8e-120">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="50d8e-121">Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.</span><span class="sxs-lookup"><span data-stu-id="50d8e-121">Run the application on your device to ensure the feature is working properly.</span></span>

[<span data-ttu-id="50d8e-122">Próximo tutorial: 4. Configurar a intenção e o reconhecimento vocal natural</span><span class="sxs-lookup"><span data-stu-id="50d8e-122">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

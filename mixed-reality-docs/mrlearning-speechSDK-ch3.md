---
title: TUTORIAIS dos serviços de fala do Azure-3. Adicionando o componente de tradução de fala dos serviços cognitivas do Azure
description: Conclua este curso para aprender a implementar o SDK de fala do Azure em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens
ms.openlocfilehash: c7cbdca3c22253042a9be44a194fca8925f0f446
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977961"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="c4177-105">3. Adicionando o componente de tradução de fala dos serviços cognitivas do Azure</span><span class="sxs-lookup"><span data-stu-id="c4177-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="c4177-106">Neste tutorial, aprendemos sobre o componente de tradução de fala dos serviços cognitivas do Azure em nosso projeto, além de traduzir em três idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="c4177-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

## <a name="instructions"></a><span data-ttu-id="c4177-107">Instruções</span><span class="sxs-lookup"><span data-stu-id="c4177-107">Instructions</span></span>

1. <span data-ttu-id="c4177-108">Selecione o objeto Lunarcom_Base na hierarquia e clique em Adicionar componente no painel inspetor.</span><span class="sxs-lookup"><span data-stu-id="c4177-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="c4177-109">Procure e selecione LunarcomTranslationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="c4177-109">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="c4177-111">Observação: Verifique se o simulador de modo offline está desabilitado antes de testar o tradutor do SDK de fala.</span><span class="sxs-lookup"><span data-stu-id="c4177-111">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="c4177-112">Para traduzir, você deve estar conectado à Internet.</span><span class="sxs-lookup"><span data-stu-id="c4177-112">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="c4177-113">Consulte a imagem abaixo sobre onde encontrar essa configuração.</span><span class="sxs-lookup"><span data-stu-id="c4177-113">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="c4177-115">Clique na lista suspensa no LunarcomTranslationRecognizer e selecione o idioma para o qual você deseja traduzir.</span><span class="sxs-lookup"><span data-stu-id="c4177-115">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="c4177-117">Agora, execute o aplicativo e teste o tradutor clicando no botão satélite e comece a falar.</span><span class="sxs-lookup"><span data-stu-id="c4177-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="c4177-118">Pressione o botão satélite novamente para interromper o reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="c4177-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="c4177-119">Veja abaixo um exemplo de como deve ser sua cena.</span><span class="sxs-lookup"><span data-stu-id="c4177-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="c4177-120">Fique à vontade para alterar o idioma na lista suspensa "idioma de destino" (consulte a imagem acima) para explorar a tradução em outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="c4177-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="c4177-121">Observação: Antes de testar, verifique se o simulador offline está desabilitado, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="c4177-121">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="c4177-123">Abaixo está um exemplo de como deve ser a aparência de sua cena:</span><span class="sxs-lookup"><span data-stu-id="c4177-123">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="c4177-125">Parabéns</span><span class="sxs-lookup"><span data-stu-id="c4177-125">Congratulations</span></span>

<span data-ttu-id="c4177-126">Agora seu projeto pode traduzir as palavras que você fala em vários idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="c4177-126">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="c4177-127">Fique à vontade para brincar com os idiomas e teste a precisão da tradução.</span><span class="sxs-lookup"><span data-stu-id="c4177-127">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="c4177-128">Próximo tutorial: 4. Configurar a intenção e o reconhecimento vocal natural</span><span class="sxs-lookup"><span data-stu-id="c4177-128">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)


---
title: Estudo de caso - lições da cozinha do Lowe
description: A equipe do HoloLens deseja compartilhar algumas das práticas recomendadas derivadas do projeto do HoloLens do Lowe.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, do Lowe, HoloLens, cozinha, estudo de caso
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589541"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="e4e8c-104">Estudo de caso - lições da cozinha do Lowe</span><span class="sxs-lookup"><span data-stu-id="e4e8c-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="e4e8c-105">A equipe do HoloLens deseja compartilhar algumas das práticas recomendadas derivadas do projeto do HoloLens do Lowe.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="e4e8c-106">Veja abaixo um vídeo do HoloLens do Lowe projetada é demonstrado na palestra de Ignite de 2016 do Satya.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="e4e8c-107">Práticas recomendadas do HoloLens do Lowe</span><span class="sxs-lookup"><span data-stu-id="e4e8c-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="e4e8c-108">Os dois vídeos abordam as práticas recomendadas derivadas do piloto de HoloLens do Lowe que nos repositórios do dois Lowe desde abril de 2016.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="e4e8c-109">Os tópicos principais são:</span><span class="sxs-lookup"><span data-stu-id="e4e8c-109">The key topics are:</span></span>
* <span data-ttu-id="e4e8c-110">Maximizar o desempenho de um dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="e4e8c-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="e4e8c-111">Criar métodos de experiência do usuário com um quadro completo holográfico (2ª talk)</span><span class="sxs-lookup"><span data-stu-id="e4e8c-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="e4e8c-112">Alinhamento de precisão (2ª talk)</span><span class="sxs-lookup"><span data-stu-id="e4e8c-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="e4e8c-113">Compartilhado holográfica experiências (2ª talk)</span><span class="sxs-lookup"><span data-stu-id="e4e8c-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="e4e8c-114">Interagindo com os clientes (2ª talk)</span><span class="sxs-lookup"><span data-stu-id="e4e8c-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="e4e8c-115">Vídeo 1</span><span class="sxs-lookup"><span data-stu-id="e4e8c-115">Video 1</span></span>

<span data-ttu-id="e4e8c-116">**Maximizar o desempenho de um dispositivo móvel** HoloLens é um dispositivo de forma independente com todo o processamento que estão ocorrendo no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="e4e8c-117">Isso exige uma plataforma móvel e uma mentalidade semelhante à criação de aplicativos móveis.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="e4e8c-118">A Microsoft recomenda que o seu aplicativo HoloLens manter 60FPS para fornecer uma experiência deliciosa para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="e4e8c-119">Ter FPS baixa pode resultar em hologramas instáveis.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="e4e8c-120">Algumas das coisas mais importantes para observar ao desenvolver em HoloLens é otimização ativo/eliminação, usando os sombreadores personalizados (disponível gratuitamente na [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="e4e8c-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="e4e8c-121">Outra consideração importante é medir a taxa de quadros desde o início do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="e4e8c-122">Dependendo do projeto, a ordem de exibição de seus ativos também pode ser um grande colaborador</span><span class="sxs-lookup"><span data-stu-id="e4e8c-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="e4e8c-123">Vídeo 2</span><span class="sxs-lookup"><span data-stu-id="e4e8c-123">Video 2</span></span>

<span data-ttu-id="e4e8c-124">**Criar métodos de experiência do usuário com um quadro completo holográfico** é importante entender o posicionamento de hologramas em um mundo físico.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="e4e8c-125">Lowe podemos falar sobre os diferentes métodos UX que ajudam os usuários a experiência hologramas backup feche ao mesmo tempo em que continua observando o ambiente maior de hologramas.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="e4e8c-126">**Alinhamento de precisão** cenário para o Lowe, era essencial para a experiência tenha um alinhamento de precisão dos hologramas a cozinha física.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="e4e8c-127">Discutiremos técnicas ajuda a garantir uma experiência que convence os usuários que seu ambiente físico foi alterado.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="e4e8c-128">**Compartilhado experiências holográfica** associa às é a principal maneira de que a experiência do Lowe é consumida.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="e4e8c-129">Uma pessoa pode alterar o balcão e a outra pessoa poderá ver as alterações.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="e4e8c-130">Chamamos esse "experiências compartilhadas".</span><span class="sxs-lookup"><span data-stu-id="e4e8c-130">We called this "shared experiences".</span></span>

<span data-ttu-id="e4e8c-131">**Interagindo com os clientes** designers do Lowe não estiver usando um HoloLens, mas que precisam ver o que os clientes estão vendo.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="e4e8c-132">Vamos mostrar como capturar o que o cliente está vendo em um aplicativo UWP.</span><span class="sxs-lookup"><span data-stu-id="e4e8c-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]

---
title: Estudo de caso-lições da cozinha do Lowe
description: A equipe do HoloLens deseja compartilhar algumas das práticas recomendadas que foram derivadas do projeto HoloLens do Lowe.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade do Windows Mixed, Lowe, HoloLens, cozinha, estudo de caso
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278124"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="69821-104">Estudo de caso-lições da cozinha do Lowe</span><span class="sxs-lookup"><span data-stu-id="69821-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="69821-105">A equipe do HoloLens deseja compartilhar algumas das práticas recomendadas que foram derivadas do projeto HoloLens do Lowe.</span><span class="sxs-lookup"><span data-stu-id="69821-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="69821-106">Veja a seguir um vídeo do HoloLens projetado do Lowe na palestra Satya de 2016 Ignite.</span><span class="sxs-lookup"><span data-stu-id="69821-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="69821-107">Práticas recomendadas de HoloLens do Lowe</span><span class="sxs-lookup"><span data-stu-id="69821-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="69821-108">Os dois vídeos abrangem as práticas recomendadas que foram derivadas do piloto do HoloLens da Lowe que esteve em duas lojas de Lowe desde abril de 2016.</span><span class="sxs-lookup"><span data-stu-id="69821-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="69821-109">Os principais tópicos são:</span><span class="sxs-lookup"><span data-stu-id="69821-109">The key topics are:</span></span>
* <span data-ttu-id="69821-110">Maximizar o desempenho de um dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="69821-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="69821-111">Criar métodos UX com um quadro Holographic completo (2º palestra)</span><span class="sxs-lookup"><span data-stu-id="69821-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="69821-112">Alinhamento de precisão (2ª palestra)</span><span class="sxs-lookup"><span data-stu-id="69821-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="69821-113">Experiências de Holographic compartilhadas (2ª palestra)</span><span class="sxs-lookup"><span data-stu-id="69821-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="69821-114">Interagindo com clientes (2º palestra)</span><span class="sxs-lookup"><span data-stu-id="69821-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="69821-115">Vídeo 1</span><span class="sxs-lookup"><span data-stu-id="69821-115">Video 1</span></span>

<span data-ttu-id="69821-116">**Maximizar o desempenho de um dispositivo móvel** O HoloLens é um dispositivo sem compartilhamento de Internet com todo o processamento em andamento no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69821-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="69821-117">Isso requer uma plataforma móvel e requer uma mentalidade semelhante à criação de aplicativos móveis.</span><span class="sxs-lookup"><span data-stu-id="69821-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="69821-118">A Microsoft recomenda que seu aplicativo do HoloLens Mantenha o 60FPS para fornecer uma experiência deliciosa para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="69821-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="69821-119">Ter baixas FPS pode resultar em hologramas instáveis.</span><span class="sxs-lookup"><span data-stu-id="69821-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="69821-120">Algumas das coisas mais importantes a serem examinadas ao desenvolver no HoloLens são a otimização de ativos/Decimation, usando sombreadores personalizados (disponíveis gratuitamente no [Kit de ferramentas do hololens](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="69821-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="69821-121">Outra consideração importante é medir a taxa de quadros desde o início do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="69821-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="69821-122">Dependendo do projeto, a ordem de exibição de seus ativos também pode ser um grande colaborador</span><span class="sxs-lookup"><span data-stu-id="69821-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="69821-123">Vídeo 2</span><span class="sxs-lookup"><span data-stu-id="69821-123">Video 2</span></span>

<span data-ttu-id="69821-124">**Criar métodos UX com um quadro Holographic completo** É importante entender o posicionamento de hologramas em um mundo físico.</span><span class="sxs-lookup"><span data-stu-id="69821-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="69821-125">Com o Lowe, falamos sobre diferentes métodos de UX que ajudam os usuários a experimentar os hologramas de perto e ainda ver o ambiente maior de hologramas.</span><span class="sxs-lookup"><span data-stu-id="69821-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="69821-126">**Alinhamento de precisão** Para o cenário do Lowe, era fundamental para a experiência ter o alinhamento da precisão dos hologramas com a cozinha física.</span><span class="sxs-lookup"><span data-stu-id="69821-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="69821-127">Discutimos técnicas ajuda a garantir uma experiência que convença os usuários de que seu ambiente físico mudou.</span><span class="sxs-lookup"><span data-stu-id="69821-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="69821-128">**Experiências de Holographic compartilhadas** Os atestados são a principal maneira pela qual a experiência do Lowe é consumida.</span><span class="sxs-lookup"><span data-stu-id="69821-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="69821-129">Uma pessoa pode alterar o balcão e a outra pessoa verá as alterações.</span><span class="sxs-lookup"><span data-stu-id="69821-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="69821-130">Chamamos isso de "experiências compartilhadas".</span><span class="sxs-lookup"><span data-stu-id="69821-130">We called this "shared experiences".</span></span>

<span data-ttu-id="69821-131">**Interagindo com clientes** Os designers de Lowe não estão usando um HoloLens, mas precisam ver o que os clientes estão vendo.</span><span class="sxs-lookup"><span data-stu-id="69821-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="69821-132">Mostramos como capturar o que o cliente está vendo em um aplicativo UWP.</span><span class="sxs-lookup"><span data-stu-id="69821-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]

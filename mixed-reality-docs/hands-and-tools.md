---
title: Mãos e controladores de movimento
description: Visão geral das mãos e interação de controladores de movimento
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Misto realidade, mãos, controles de animação, interação, de design
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039173"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="13c1a-104">Mãos e controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="13c1a-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="13c1a-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="13c1a-105">Scenarios</span></span>
<span data-ttu-id="13c1a-106">Se você optar por adotar esse modelo de interação depois de ler o [diretrizes de design](interaction-fundamentals.md), isso significa que você está desenvolvendo um aplicativo exigir que os usuários para usar duas mãos para interagir com o mundo holographic.</span><span class="sxs-lookup"><span data-stu-id="13c1a-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="13c1a-107">Seu aplicativo vai para atingir o objetivo de remover o limite entre física e virtual.</span><span class="sxs-lookup"><span data-stu-id="13c1a-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="13c1a-108">Alguns cenários específicos podem ser:</span><span class="sxs-lookup"><span data-stu-id="13c1a-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="13c1a-109">Fornecer interfaces do usuário para exibir e controlar o conteúdo e telas de virtual 2D de trabalhadores de informações</span><span class="sxs-lookup"><span data-stu-id="13c1a-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="13c1a-110">Fornecendo tutoriais de trabalhadores primeira linha e guias de linhas de assembly de fábrica</span><span class="sxs-lookup"><span data-stu-id="13c1a-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="13c1a-111">Desenvolver ferramentas profissionais para ajudar e educar profissionais médicos</span><span class="sxs-lookup"><span data-stu-id="13c1a-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="13c1a-112">Usando objetos virtuais 3D para decorar o mundo real ou para criar um mundo de segundo</span><span class="sxs-lookup"><span data-stu-id="13c1a-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="13c1a-113">Criar local com base em serviços e jogos usando o mundo real, como plano de fundo</span><span class="sxs-lookup"><span data-stu-id="13c1a-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="13c1a-114">Mãos e modalidades de controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="13c1a-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="13c1a-115">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="13c1a-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="13c1a-116">Essa é uma modalidade aproveitando o poder de mãos, com a qual os usuários são capazes de tocar e manipulando as hologramas diretamente.</span><span class="sxs-lookup"><span data-stu-id="13c1a-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="13c1a-117">Por leaveraging experiências de vida diária e fornecer capacidades de visual adequadas, os usuários são capazes de usar da mesma forma de manipulação de objetos do mundo real para interagir com aquelas virtuais.</span><span class="sxs-lookup"><span data-stu-id="13c1a-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="13c1a-118">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="13c1a-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="13c1a-119">Este modalidade capacita os usuários interajam com hologramas em uma distância.</span><span class="sxs-lookup"><span data-stu-id="13c1a-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="13c1a-120">Ele permite aos usuários fazer o melhor uso do ambiente.</span><span class="sxs-lookup"><span data-stu-id="13c1a-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="13c1a-121">Os usuários podem colocar hologramas em qualquer lugar e ainda podem acessá-los de qualquer distâncias.</span><span class="sxs-lookup"><span data-stu-id="13c1a-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="13c1a-122">Os modelos mentais e os gestos de controle e manipulando hologramas 2D e 3D são altamente em sincronia com aqueles do manipulação direta.</span><span class="sxs-lookup"><span data-stu-id="13c1a-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="13c1a-123">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="13c1a-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="13c1a-124">Controladores de movimento são ferramentas que estendem os recursos físicos dos usuários, fornecendo interações precisas em uma grande variedade de distâncias durante o uso de uma ou ambas as mãos.</span><span class="sxs-lookup"><span data-stu-id="13c1a-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="13c1a-125">Esses acessórios de hardware fornecem atalhos para muitos usados interações e fornece surefooted táteis comentários para uma variedade de ações.</span><span class="sxs-lookup"><span data-stu-id="13c1a-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="13c1a-126">Atualmente, os controladores de movimento só estão disponíveis para cenários WMR.</span><span class="sxs-lookup"><span data-stu-id="13c1a-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="13c1a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13c1a-127">See also</span></span>
* [<span data-ttu-id="13c1a-128">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="13c1a-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="13c1a-129">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="13c1a-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="13c1a-130">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="13c1a-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="13c1a-131">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="13c1a-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="13c1a-132">Mãos livres</span><span class="sxs-lookup"><span data-stu-id="13c1a-132">Hands-free</span></span>](hands-free.md)

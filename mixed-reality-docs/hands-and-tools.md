---
title: Mãos e controladores de movimento
description: Visão geral das mãos e interação de controladores de movimento
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Misto realidade, mãos, controles de animação, interação, de design
ms.openlocfilehash: 583d284ee98b8ccbc0a9c2c8670551d0a7397074
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873990"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="d3c42-104">Mãos e controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="d3c42-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="d3c42-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="d3c42-105">Scenarios</span></span>
<span data-ttu-id="d3c42-106">Se você optar por adotar esse modelo de interação depois de ler o [diretrizes de design](interaction-fundamentals.md), isso significa que você está desenvolvendo um aplicativo exigir que os usuários para usar duas mãos para interagir com o mundo holographic.</span><span class="sxs-lookup"><span data-stu-id="d3c42-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="d3c42-107">Seu aplicativo vai para atingir o objetivo de remover o limite entre física e virtual.</span><span class="sxs-lookup"><span data-stu-id="d3c42-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="d3c42-108">Alguns cenários específicos podem ser:</span><span class="sxs-lookup"><span data-stu-id="d3c42-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="d3c42-109">Fornecer interfaces do usuário para exibir e controlar o conteúdo e telas de virtual 2D de trabalhadores de informações</span><span class="sxs-lookup"><span data-stu-id="d3c42-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="d3c42-110">Fornecendo tutoriais de trabalhadores primeira linha e guias de linhas de assembly de fábrica</span><span class="sxs-lookup"><span data-stu-id="d3c42-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="d3c42-111">Desenvolver ferramentas profissionais para ajudar e educar profissionais médicos</span><span class="sxs-lookup"><span data-stu-id="d3c42-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="d3c42-112">Usando objetos virtuais 3D para decorar o mundo real ou para criar um mundo de segundo</span><span class="sxs-lookup"><span data-stu-id="d3c42-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="d3c42-113">Criar local com base em serviços e jogos usando o mundo real, como plano de fundo</span><span class="sxs-lookup"><span data-stu-id="d3c42-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="d3c42-114">Mãos e modalidades de controladores de movimento</span><span class="sxs-lookup"><span data-stu-id="d3c42-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-near-hand-interactiondirect-manipulationmd"></a>[<span data-ttu-id="d3c42-115">Manipulação direta (próximo interação disponível)</span><span class="sxs-lookup"><span data-stu-id="d3c42-115">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
<span data-ttu-id="d3c42-116">Essa é uma modalidade aproveitando o poder de mãos, com a qual os usuários são capazes de tocar e manipulando as hologramas diretamente.</span><span class="sxs-lookup"><span data-stu-id="d3c42-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="d3c42-117">Por leaveraging experiências de vida diária e fornecer capacidades de visual adequadas, os usuários são capazes de usar da mesma forma de manipulação de objetos do mundo real para interagir com aquelas virtuais.</span><span class="sxs-lookup"><span data-stu-id="d3c42-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world obejcts to interact with virtual ones.</span></span>   

### <a name="point-and-commit-far-hand-interactionpoint-and-commitmd"></a>[<span data-ttu-id="d3c42-118">Ponto e confirmação (interação de mão Ásia)</span><span class="sxs-lookup"><span data-stu-id="d3c42-118">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
<span data-ttu-id="d3c42-119">Este modalidade fornece aos usuários super power para interagir com hologramas em uma distância.</span><span class="sxs-lookup"><span data-stu-id="d3c42-119">This modality provides users super power to interact with holograms in a distance.</span></span> <span data-ttu-id="d3c42-120">Ele permite aos usuários fazer o melhor uso da configuração ao redor.</span><span class="sxs-lookup"><span data-stu-id="d3c42-120">It enables users to make the best use of setting of surrounding.</span></span> <span data-ttu-id="d3c42-121">Os usuários podem colocar hologramas em qualquer lugar e ainda podem acessá-los de qualquer distâncias.</span><span class="sxs-lookup"><span data-stu-id="d3c42-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="d3c42-122">Os modelos mentais e os gestos de controle e manipulando hologramas 2D e 3D são altamente em sincronia com aqueles do manipulação direta.</span><span class="sxs-lookup"><span data-stu-id="d3c42-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="d3c42-123">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="d3c42-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="d3c42-124">Controladores de movimento são ferramentas que estendem os recursos físicos dos usuários, fornecendo interações precisas em uma grande variedade de distâncias durante o uso de uma ou ambas as mãos.</span><span class="sxs-lookup"><span data-stu-id="d3c42-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="d3c42-125">Esses acessórios de hardware fornecem atalhos para muitos usados interações e fornece surefooted táteis comentários para uma variedade de ações.</span><span class="sxs-lookup"><span data-stu-id="d3c42-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="d3c42-126">Atualmente, os controladores de movimento só estão disponíveis para cenários WMR.</span><span class="sxs-lookup"><span data-stu-id="d3c42-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="d3c42-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3c42-127">See also</span></span>
* [<span data-ttu-id="d3c42-128">Olhar e confirmar</span><span class="sxs-lookup"><span data-stu-id="d3c42-128">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d3c42-129">Manipulação direta (próximo interação disponível)</span><span class="sxs-lookup"><span data-stu-id="d3c42-129">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d3c42-130">Ponto e confirmação (interação de mão Ásia)</span><span class="sxs-lookup"><span data-stu-id="d3c42-130">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
* [<span data-ttu-id="d3c42-131">Mãos livres</span><span class="sxs-lookup"><span data-stu-id="d3c42-131">Hands-free</span></span>](hands-free.md)
* [<span data-ttu-id="d3c42-132">Focar direcionamento</span><span class="sxs-lookup"><span data-stu-id="d3c42-132">Gaze targeting</span></span>](gaze-targeting.md)

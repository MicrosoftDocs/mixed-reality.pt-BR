---
title: Controladores de mãos e de movimento
description: Visão geral da interação dos controladores de mão e de movimento
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Realidade misturada, mãos, controle de movimento, interação, design
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039173"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="eb5c6-104">Controladores de mãos e de movimento</span><span class="sxs-lookup"><span data-stu-id="eb5c6-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="eb5c6-105">Cenários</span><span class="sxs-lookup"><span data-stu-id="eb5c6-105">Scenarios</span></span>
<span data-ttu-id="eb5c6-106">Se você optar por adotar esse modelo de interação depois de ler as [diretrizes de design](interaction-fundamentals.md), isso significa que você está desenvolvendo um aplicativo que exige que os usuários usem duas mãos para interagir com o Holographic World.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="eb5c6-107">Seu aplicativo vai atingir o objetivo de remover o limite entre virtual e físico.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="eb5c6-108">Alguns cenários específicos podem ser:</span><span class="sxs-lookup"><span data-stu-id="eb5c6-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="eb5c6-109">Fornecer telas e UIs virtual 2D de operadores de informações para exibir e controlar o conteúdo</span><span class="sxs-lookup"><span data-stu-id="eb5c6-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="eb5c6-110">Fornecimento de tutoriais e guias de funcionários de primeira linha em linhas de assembly de fábrica</span><span class="sxs-lookup"><span data-stu-id="eb5c6-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="eb5c6-111">Desenvolvendo ferramentas profissionais para auxiliar e conscientizar profissionais médicos</span><span class="sxs-lookup"><span data-stu-id="eb5c6-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="eb5c6-112">Usando objetos virtuais 3D para decorar o mundo real ou para criar um segundo mundo</span><span class="sxs-lookup"><span data-stu-id="eb5c6-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="eb5c6-113">Criando serviços e jogos baseados na localização usando o mundo real como plano de fundo</span><span class="sxs-lookup"><span data-stu-id="eb5c6-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="eb5c6-114">Modalidades de controladores de mãos e de movimento</span><span class="sxs-lookup"><span data-stu-id="eb5c6-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="eb5c6-115">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="eb5c6-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="eb5c6-116">Essa é uma modalidade que aproveita o poder das mãos, com as quais os usuários são capazes de tocar e manipular os hologramas diretamente.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="eb5c6-117">Por leaveraging experiências diárias de vida e fornecimento de capacidades visuais adequados, os usuários podem usar a mesma maneira de manipular objetos reais para interagir com os virtuais.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="eb5c6-118">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="eb5c6-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="eb5c6-119">Essa modalidade permite que os usuários interajam com os hologramas em uma distância.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="eb5c6-120">Ele permite que os usuários façam o melhor uso de arredores.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="eb5c6-121">Os usuários podem posicionar os hologramas em qualquer lugar e ainda podem acessá-los de qualquer distância.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="eb5c6-122">Os modelos mentales e gestos para controlar e manipular os hologramas 2D e 3D são altamente sincronizados com aqueles de manipulação direta.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="eb5c6-123">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="eb5c6-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="eb5c6-124">Os controladores de movimento são ferramentas que estendem os recursos físicos dos usuários, fornecendo interações precisas em uma grande variedade de distâncias ao usar uma ou ambas as mãos.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="eb5c6-125">Esses acessórios de hardware fornecem atalhos para muitas interações usadas com frequência e fornecem comentários de Surefooted, tactile para uma variedade de ações.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="eb5c6-126">Atualmente, os controladores de movimento só estão disponíveis para cenários WMR.</span><span class="sxs-lookup"><span data-stu-id="eb5c6-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="eb5c6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb5c6-127">See also</span></span>
* [<span data-ttu-id="eb5c6-128">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="eb5c6-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="eb5c6-129">Focar com a cabeça e esperar</span><span class="sxs-lookup"><span data-stu-id="eb5c6-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="eb5c6-130">Manipulação direta com as mãos</span><span class="sxs-lookup"><span data-stu-id="eb5c6-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="eb5c6-131">Apontar e confirmar com as mãos</span><span class="sxs-lookup"><span data-stu-id="eb5c6-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="eb5c6-132">Mãos livres</span><span class="sxs-lookup"><span data-stu-id="eb5c6-132">Hands-free</span></span>](hands-free.md)

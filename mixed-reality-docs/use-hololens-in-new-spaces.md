---
title: Usar o HoloLens em novos espaços
description: O HoloLens aprende a aparência de um espaço ao longo do tempo. Os usuários podem facilitar esse processo movendo o HoloLens de determinadas maneiras por meio do espaço.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Realidade mista do Windows, design, mapeamento espacial, HoloLens, reconstrução da superfície, malha, acompanhamento de cabeçalho, mapeamento
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566015"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="a6d61-105">Usar o HoloLens em novos espaços</span><span class="sxs-lookup"><span data-stu-id="a6d61-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="a6d61-106">O HoloLens *mapeia*ou aprende informações sobre o seu ambiente à medida que o usuário se move em torno de um espaço.</span><span class="sxs-lookup"><span data-stu-id="a6d61-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="a6d61-107">Ao longo do tempo, o HoloLens cria um *mapa espacial* de todas as partes do ambiente que foram observadas.</span><span class="sxs-lookup"><span data-stu-id="a6d61-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="a6d61-108">O HoloLens atualiza o mapa conforme as alterações no ambiente são observadas.</span><span class="sxs-lookup"><span data-stu-id="a6d61-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="a6d61-109">Essa verificação persistirá automaticamente entre as inicializações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6d61-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="a6d61-110">O HoloLens criará e atualizará os mapas enquanto o dispositivo estiver ligado e um usuário estiver conectado.</span><span class="sxs-lookup"><span data-stu-id="a6d61-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="a6d61-111">Se você mantiver ou usar o dispositivo com as câmeras apontadas por um espaço, o dispositivo tentará mapear a área.</span><span class="sxs-lookup"><span data-stu-id="a6d61-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="a6d61-112">Embora o HoloLens Aprenda um espaço naturalmente ao longo do tempo, há dicas e truques disponíveis para mapear o espaço com mais rapidez e eficiência.</span><span class="sxs-lookup"><span data-stu-id="a6d61-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="a6d61-113">Se o seu HoloLens não puder mapear seu espaço ou estiver sem calibragem, você poderá entrar no modo limitado.</span><span class="sxs-lookup"><span data-stu-id="a6d61-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="a6d61-114">No modo limitado, você não poderá posicionar os hologramas no ambiente.</span><span class="sxs-lookup"><span data-stu-id="a6d61-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="a6d61-115">Dicas e truques para espaços de mapeamento</span><span class="sxs-lookup"><span data-stu-id="a6d61-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="a6d61-116">Verifique se o espaço está configurado para realidade misturada</span><span class="sxs-lookup"><span data-stu-id="a6d61-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="a6d61-117">Os recursos em um ambiente podem dificultar que o HoloLens interprete um espaço.</span><span class="sxs-lookup"><span data-stu-id="a6d61-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="a6d61-118">Os níveis de luz, os materiais no espaço, o layout dos objetos e muito mais podem afetar como o HoloLens mapeia uma área.</span><span class="sxs-lookup"><span data-stu-id="a6d61-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="a6d61-119">As dicas para configurar seu espaço para o HoloLens e outros dispositivos de realidade misturada podem ser encontradas em [considerações de ambiente para o hololens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="a6d61-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="a6d61-120">Entender os cenários da área</span><span class="sxs-lookup"><span data-stu-id="a6d61-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="a6d61-121">É importante gastar a maior parte do tempo em que você usará o HoloLens para que o mapa seja relevante e concluído.</span><span class="sxs-lookup"><span data-stu-id="a6d61-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="a6d61-122">Por exemplo, se um cenário de usuário para o HoloLens envolve a mudança do ponto a para o ponto B, percorra esse caminho de duas a três vezes, examinando todas as direções à medida que você mover.</span><span class="sxs-lookup"><span data-stu-id="a6d61-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="a6d61-123">Explore lentamente ao contrário do espaço</span><span class="sxs-lookup"><span data-stu-id="a6d61-123">Walk slowly around the space</span></span>

<span data-ttu-id="a6d61-124">Se você se movimentar muito rapidamente pela área, é provável que o HoloLens perca áreas de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="a6d61-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="a6d61-125">Percorra lentamente o espaço, interrompendo a cada 5-8 pés para olhar ao seu lado.</span><span class="sxs-lookup"><span data-stu-id="a6d61-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="a6d61-126">Movimentos suaves também ajudam o mapeamento de HoloLens mais automatizados.</span><span class="sxs-lookup"><span data-stu-id="a6d61-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="a6d61-127">Examinar todas as direções</span><span class="sxs-lookup"><span data-stu-id="a6d61-127">Look in all directions</span></span>

<span data-ttu-id="a6d61-128">Examinar enquanto você mapeia o espaço fornece ao HoloLens mais dados sobre onde os pontos são relativos entre si.</span><span class="sxs-lookup"><span data-stu-id="a6d61-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="a6d61-129">Se você não procurar, por exemplo, o HoloLens pode não saber onde está o teto em uma sala.</span><span class="sxs-lookup"><span data-stu-id="a6d61-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="a6d61-130">Não se esqueça de examinar o piso enquanto mapeia o espaço.</span><span class="sxs-lookup"><span data-stu-id="a6d61-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="a6d61-131">Cobrir áreas-chave várias vezes</span><span class="sxs-lookup"><span data-stu-id="a6d61-131">Cover key areas multiple times</span></span>

<span data-ttu-id="a6d61-132">A movimentação por uma área várias vezes ajudará a pegar os recursos que você pode ter perdido no primeiro guia.</span><span class="sxs-lookup"><span data-stu-id="a6d61-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="a6d61-133">Tente percorrer uma área duas a três vezes para criar um mapa ideal.</span><span class="sxs-lookup"><span data-stu-id="a6d61-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="a6d61-134">Se possível, ao repetir esses movimentos, gaste tempo percorrendo uma área em uma direção e, em seguida, gire e volte da maneira que você veio.</span><span class="sxs-lookup"><span data-stu-id="a6d61-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="a6d61-135">Reserve seu tempo mapeando a área</span><span class="sxs-lookup"><span data-stu-id="a6d61-135">Take your time mapping the area</span></span>

<span data-ttu-id="a6d61-136">Pode levar entre 15 e 20 minutos para que o HoloLens se mapeie totalmente e se ajuste para seus arredores.</span><span class="sxs-lookup"><span data-stu-id="a6d61-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="a6d61-137">Se você tiver um espaço no qual planeja usar um HoloLens frequentemente, levar esse tempo até o mapeamento do espaço pode evitar problemas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="a6d61-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="a6d61-138">Possíveis erros no mapa espacial</span><span class="sxs-lookup"><span data-stu-id="a6d61-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="a6d61-139">Os erros nos dados de mapeamento espacial se enquadram em uma das três categorias:</span><span class="sxs-lookup"><span data-stu-id="a6d61-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="a6d61-140">*Buracos*: As superfícies do mundo real estão ausentes dos dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="a6d61-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="a6d61-141">*Hallucinations*: Existem superfícies nos dados de mapeamento espacial que não existem no mundo real.</span><span class="sxs-lookup"><span data-stu-id="a6d61-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="a6d61-142">*Fendas espaciais*: O HoloLens ' perde parte do mapa espacial, pensando que ele está em uma parte diferente do mapa do que realmente é.</span><span class="sxs-lookup"><span data-stu-id="a6d61-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="a6d61-143">*Tendência*: As superfícies nos dados de mapeamento espacial são alinhadas de forma inperfeita com as superfícies do mundo real, enviadas ou retiradas.</span><span class="sxs-lookup"><span data-stu-id="a6d61-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="a6d61-144">Muitos desses erros podem ser atenuados com a [exclusão](environment-considerations-for-hololens.md) de hologramas e o novo mapeamento do espaço.</span><span class="sxs-lookup"><span data-stu-id="a6d61-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>
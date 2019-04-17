---
title: Visualização de verificação de espaço
description: Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, padrões de aplicativo, design, HoloLens, verificação de espaço, espacial de mapeamento, superfície reconstrução, da malha
ms.openlocfilehash: 8ffde9d476e25016f986321377dce8125ee3a596
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590929"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="f83bd-104">Visualização de verificação de espaço</span><span class="sxs-lookup"><span data-stu-id="f83bd-104">Room scan visualization</span></span>

<span data-ttu-id="f83bd-105">Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f83bd-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="f83bd-106">A integridade e a qualidade dos dados depende de vários fatores, incluindo a quantidade de exploração que o usuário tenha feito, quanto tempo se passou desde a exploração e se os objetos como móveis e portas foram movidas desde a área de verificação de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f83bd-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="f83bd-107">Para garantir que os dados de mapeamento espacial úteis, os desenvolvedores de aplicativos tem várias opções:</span><span class="sxs-lookup"><span data-stu-id="f83bd-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="f83bd-108">Contar o que talvez já foram coletado.</span><span class="sxs-lookup"><span data-stu-id="f83bd-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="f83bd-109">Esses dados podem estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="f83bd-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="f83bd-110">Peça ao usuário para usar o gesto de bloom para obter o Windows Mixed Reality inicial e, em seguida, explore a área que eles desejam usar para a experiência.</span><span class="sxs-lookup"><span data-stu-id="f83bd-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="f83bd-111">Eles podem usar o toque de ar para confirmar que toda a área necessária é conhecida para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f83bd-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="f83bd-112">Crie uma experiência de exploração personalizado em seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f83bd-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="f83bd-113">Observe que em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f83bd-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="f83bd-114">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="f83bd-114">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f83bd-115">Recurso</span><span class="sxs-lookup"><span data-stu-id="f83bd-115">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="f83bd-116"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f83bd-116"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f83bd-117"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="f83bd-117"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f83bd-118">Visualização de verificação de espaço</span><span class="sxs-lookup"><span data-stu-id="f83bd-118">Room scan visualization</span></span></td><td style="text-align: center;"> <span data-ttu-id="f83bd-119">✔️</span><span class="sxs-lookup"><span data-stu-id="f83bd-119">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="f83bd-120">Criar uma experiência de verificação personalizada</span><span class="sxs-lookup"><span data-stu-id="f83bd-120">Building a custom scanning experience</span></span>

<span data-ttu-id="f83bd-121">Aplicativos podem decidir analisar os dados de mapeamento espacial no início da experiência para avaliar se eles desejam que o usuário execute etapas adicionais para melhorar sua integridade e a qualidade.</span><span class="sxs-lookup"><span data-stu-id="f83bd-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="f83bd-122">Se a análise indica que deve ser melhor qualidade, os desenvolvedores devem fornecer uma visualização para o mundo para indicar de sobreposição:</span><span class="sxs-lookup"><span data-stu-id="f83bd-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="f83bd-123">Quanto o volume total nas proximidades usuários precisa fazer parte da experiência do</span><span class="sxs-lookup"><span data-stu-id="f83bd-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="f83bd-124">Em que o usuário deve ir para melhorar a dados</span><span class="sxs-lookup"><span data-stu-id="f83bd-124">Where the user should go to improve data</span></span>

<span data-ttu-id="f83bd-125">Os usuários não sabem o que faz uma verificação de "boa".</span><span class="sxs-lookup"><span data-stu-id="f83bd-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="f83bd-126">Eles precisam ser mostrado ou informado o que procurar se eles são solicitados para avaliar uma verificação – planeza, distância das paredes reais, etc. O desenvolvedor deve implementar um loop de comentários que inclui a atualização de dados de mapeamento espacial durante a fase de verificação ou exploração.</span><span class="sxs-lookup"><span data-stu-id="f83bd-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="f83bd-127">Em muitos casos, talvez seja melhor informar ao usuário o que precisam (por exemplo, examinar o limite, procure por trás de móveis), para obter a qualidade de verificação necessárias.</span><span class="sxs-lookup"><span data-stu-id="f83bd-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="f83bd-128">Armazenados em cache versus contínuo mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="f83bd-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="f83bd-129">Os dados de mapeamento espacial serão mais pesada aplicativos de fonte de dados podem consumir.</span><span class="sxs-lookup"><span data-stu-id="f83bd-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="f83bd-130">Para evitar problemas de desempenho, como quadros ignorados ou falhas, consumo de dados deve ser feito com cuidado.</span><span class="sxs-lookup"><span data-stu-id="f83bd-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="f83bd-131">Verificando ativa durante uma experiência pode ser benéfico ou prejudicial e o desenvolvedor precisará decidir qual método usar com base na experiência.</span><span class="sxs-lookup"><span data-stu-id="f83bd-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="f83bd-132">Mapeamento espacial em cache</span><span class="sxs-lookup"><span data-stu-id="f83bd-132">Cached spatial mapping</span></span>

<span data-ttu-id="f83bd-133">No caso do mapeamento espacial em cache, o aplicativo geralmente tira um instantâneo dos dados de mapeamento espacial e usa esse instantâneo para a duração da experiência.</span><span class="sxs-lookup"><span data-stu-id="f83bd-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="f83bd-134">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="f83bd-134">**Benefits**</span></span>
* <span data-ttu-id="f83bd-135">Redução sobrecarga no sistema enquanto a experiência está em execução líder a enorme potência, térmica e ganhos de desempenho de cpu.</span><span class="sxs-lookup"><span data-stu-id="f83bd-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="f83bd-136">Uma implementação mais simples da experiência de principal, pois ele não é interrompido por alterações nos dados espaciais.</span><span class="sxs-lookup"><span data-stu-id="f83bd-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="f83bd-137">Um único custo em qualquer pós-processamento dos dados espaciais para outros fins, gráficos e física de uma vez.</span><span class="sxs-lookup"><span data-stu-id="f83bd-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="f83bd-138">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="f83bd-138">**Drawbacks**</span></span>
* <span data-ttu-id="f83bd-139">A movimentação de objetos do mundo real ou pessoas não será refletida pelos dados armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="f83bd-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="f83bd-140">Ex.</span><span class="sxs-lookup"><span data-stu-id="f83bd-140">E.g.</span></span> <span data-ttu-id="f83bd-141">o aplicativo pode considerar uma porta aberta quando, na verdade, é fechada agora.</span><span class="sxs-lookup"><span data-stu-id="f83bd-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="f83bd-142">Potencialmente mais memória do aplicativo para manter a versão em cache dos dados.</span><span class="sxs-lookup"><span data-stu-id="f83bd-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="f83bd-143">Um bom caso para esse método é um jogo de tabela superior ou de um ambiente controlado.</span><span class="sxs-lookup"><span data-stu-id="f83bd-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="f83bd-144">Mapeamento espacial contínuo</span><span class="sxs-lookup"><span data-stu-id="f83bd-144">Continuous spatial mapping</span></span>

<span data-ttu-id="f83bd-145">Determinados aplicativos podem se basear em continua a varredura para atualizar os dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="f83bd-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="f83bd-146">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="f83bd-146">**Benefits**</span></span>
* <span data-ttu-id="f83bd-147">Você não precisa compilar em uma separada de verificação ou exploração experiência com antecedência em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f83bd-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="f83bd-148">A movimentação de objetos do mundo real pode ser refletida com o jogo, embora com algum atraso.</span><span class="sxs-lookup"><span data-stu-id="f83bd-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="f83bd-149">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="f83bd-149">**Drawbacks**</span></span>
* <span data-ttu-id="f83bd-150">Maior complexidade na implementação da experiência de principal.</span><span class="sxs-lookup"><span data-stu-id="f83bd-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="f83bd-151">Potencial de sobrecarga do processamento adicional para o elemento gráfico ou física como alterações precisam ser ingeridos incrementalmente por esses sistemas.</span><span class="sxs-lookup"><span data-stu-id="f83bd-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="f83bd-152">Maior capacidade, térmico e impacto sobre a CPU.</span><span class="sxs-lookup"><span data-stu-id="f83bd-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="f83bd-153">Um bom caso para esse método é que um onde hologramas devem interagir com a movimentação de objetos, por exemplo, um carro holográfico unidades no chão talvez queira corretamente se deparar com uma porta dependendo se ele for aberto ou fechado.</span><span class="sxs-lookup"><span data-stu-id="f83bd-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f83bd-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f83bd-154">See also</span></span>
* [<span data-ttu-id="f83bd-155">Design de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="f83bd-155">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="f83bd-156">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="f83bd-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="f83bd-157">Design de som espacial</span><span class="sxs-lookup"><span data-stu-id="f83bd-157">Spatial sound design</span></span>](spatial-sound-design.md)

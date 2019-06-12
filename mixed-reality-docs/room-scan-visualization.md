---
title: Visualização de verificação de espaço
description: Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, padrões de aplicativo, design, HoloLens, verificação de espaço, espacial de mapeamento, superfície reconstrução, da malha
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829909"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="60007-104">Visualização de verificação de espaço</span><span class="sxs-lookup"><span data-stu-id="60007-104">Room scan visualization</span></span>

<span data-ttu-id="60007-105">Aplicativos que exigem que os dados de mapeamento espacial se baseiam no dispositivo para automaticamente coletar esses dados ao longo do tempo e entre as sessões do usuário explora o seu ambiente com o Active Directory do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60007-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="60007-106">A integridade e a qualidade dos dados depende de vários fatores, incluindo a quantidade de exploração que o usuário tenha feito, quanto tempo se passou desde a exploração e se os objetos como móveis e portas foram movidas desde a área de verificação de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60007-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="60007-107">Para garantir que os dados de mapeamento espacial úteis, os desenvolvedores de aplicativos tem várias opções:</span><span class="sxs-lookup"><span data-stu-id="60007-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="60007-108">Contar o que talvez já foram coletado.</span><span class="sxs-lookup"><span data-stu-id="60007-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="60007-109">Esses dados podem estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="60007-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="60007-110">Peça ao usuário para usar o gesto de bloom para obter o Windows Mixed Reality inicial e, em seguida, explore a área que eles desejam usar para a experiência.</span><span class="sxs-lookup"><span data-stu-id="60007-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="60007-111">Eles podem usar o toque de ar para confirmar que toda a área necessária é conhecida para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60007-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="60007-112">Crie uma experiência de exploração personalizado em seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60007-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="60007-113">Observe que em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso.</span><span class="sxs-lookup"><span data-stu-id="60007-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="60007-114">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="60007-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="60007-115"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="60007-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="60007-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="60007-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="60007-117"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="60007-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="60007-118">Visualização de verificação de espaço</span><span class="sxs-lookup"><span data-stu-id="60007-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="60007-119">✔️</span><span class="sxs-lookup"><span data-stu-id="60007-119">✔️</span></span></td>
        <td><span data-ttu-id="60007-120">❌</span><span class="sxs-lookup"><span data-stu-id="60007-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="60007-121">Criar uma experiência de verificação personalizada</span><span class="sxs-lookup"><span data-stu-id="60007-121">Building a custom scanning experience</span></span>

<span data-ttu-id="60007-122">Aplicativos podem decidir analisar os dados de mapeamento espacial no início da experiência para avaliar se eles desejam que o usuário execute etapas adicionais para melhorar sua integridade e a qualidade.</span><span class="sxs-lookup"><span data-stu-id="60007-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="60007-123">Se a análise indica que deve ser melhor qualidade, os desenvolvedores devem fornecer uma visualização para o mundo para indicar de sobreposição:</span><span class="sxs-lookup"><span data-stu-id="60007-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="60007-124">Quanto o volume total nas proximidades usuários precisa fazer parte da experiência do</span><span class="sxs-lookup"><span data-stu-id="60007-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="60007-125">Em que o usuário deve ir para melhorar a dados</span><span class="sxs-lookup"><span data-stu-id="60007-125">Where the user should go to improve data</span></span>

<span data-ttu-id="60007-126">Os usuários não sabem o que faz uma verificação de "boa".</span><span class="sxs-lookup"><span data-stu-id="60007-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="60007-127">Eles precisam ser mostrado ou informado o que procurar se eles são solicitados para avaliar uma verificação – planeza, distância das paredes reais, etc. O desenvolvedor deve implementar um loop de comentários que inclui a atualização de dados de mapeamento espacial durante a fase de verificação ou exploração.</span><span class="sxs-lookup"><span data-stu-id="60007-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="60007-128">Em muitos casos, talvez seja melhor informar ao usuário o que precisam (por exemplo, examinar o limite, procure por trás de móveis), para obter a qualidade de verificação necessárias.</span><span class="sxs-lookup"><span data-stu-id="60007-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="60007-129">Armazenados em cache versus contínuo mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="60007-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="60007-130">Os dados de mapeamento espacial serão mais pesada aplicativos de fonte de dados podem consumir.</span><span class="sxs-lookup"><span data-stu-id="60007-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="60007-131">Para evitar problemas de desempenho, como quadros ignorados ou falhas, consumo de dados deve ser feito com cuidado.</span><span class="sxs-lookup"><span data-stu-id="60007-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="60007-132">Verificando ativa durante uma experiência pode ser benéfico ou prejudicial e o desenvolvedor precisará decidir qual método usar com base na experiência.</span><span class="sxs-lookup"><span data-stu-id="60007-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="60007-133">Mapeamento espacial em cache</span><span class="sxs-lookup"><span data-stu-id="60007-133">Cached spatial mapping</span></span>

<span data-ttu-id="60007-134">No caso do mapeamento espacial em cache, o aplicativo geralmente tira um instantâneo dos dados de mapeamento espacial e usa esse instantâneo para a duração da experiência.</span><span class="sxs-lookup"><span data-stu-id="60007-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="60007-135">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="60007-135">**Benefits**</span></span>
* <span data-ttu-id="60007-136">Redução sobrecarga no sistema enquanto a experiência está em execução líder a enorme potência, térmica e ganhos de desempenho de cpu.</span><span class="sxs-lookup"><span data-stu-id="60007-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="60007-137">Uma implementação mais simples da experiência de principal, pois ele não é interrompido por alterações nos dados espaciais.</span><span class="sxs-lookup"><span data-stu-id="60007-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="60007-138">Um único custo em qualquer pós-processamento dos dados espaciais para outros fins, gráficos e física de uma vez.</span><span class="sxs-lookup"><span data-stu-id="60007-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="60007-139">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="60007-139">**Drawbacks**</span></span>
* <span data-ttu-id="60007-140">A movimentação de objetos do mundo real ou pessoas não será refletida pelos dados armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="60007-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="60007-141">Ex.</span><span class="sxs-lookup"><span data-stu-id="60007-141">E.g.</span></span> <span data-ttu-id="60007-142">o aplicativo pode considerar uma porta aberta quando, na verdade, é fechada agora.</span><span class="sxs-lookup"><span data-stu-id="60007-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="60007-143">Potencialmente mais memória do aplicativo para manter a versão em cache dos dados.</span><span class="sxs-lookup"><span data-stu-id="60007-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="60007-144">Um bom caso para esse método é um jogo de tabela superior ou de um ambiente controlado.</span><span class="sxs-lookup"><span data-stu-id="60007-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="60007-145">Mapeamento espacial contínuo</span><span class="sxs-lookup"><span data-stu-id="60007-145">Continuous spatial mapping</span></span>

<span data-ttu-id="60007-146">Determinados aplicativos podem se basear em continua a varredura para atualizar os dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="60007-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="60007-147">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="60007-147">**Benefits**</span></span>
* <span data-ttu-id="60007-148">Você não precisa compilar em uma separada de verificação ou exploração experiência com antecedência em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60007-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="60007-149">A movimentação de objetos do mundo real pode ser refletida com o jogo, embora com algum atraso.</span><span class="sxs-lookup"><span data-stu-id="60007-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="60007-150">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="60007-150">**Drawbacks**</span></span>
* <span data-ttu-id="60007-151">Maior complexidade na implementação da experiência de principal.</span><span class="sxs-lookup"><span data-stu-id="60007-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="60007-152">Potencial de sobrecarga do processamento adicional para o elemento gráfico ou física como alterações precisam ser ingeridos incrementalmente por esses sistemas.</span><span class="sxs-lookup"><span data-stu-id="60007-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="60007-153">Maior capacidade, térmico e impacto sobre a CPU.</span><span class="sxs-lookup"><span data-stu-id="60007-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="60007-154">Um bom caso para esse método é que um onde hologramas devem interagir com a movimentação de objetos, por exemplo, um carro holográfico unidades no chão talvez queira corretamente se deparar com uma porta dependendo se ele for aberto ou fechado.</span><span class="sxs-lookup"><span data-stu-id="60007-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="60007-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60007-155">See also</span></span>
* [<span data-ttu-id="60007-156">Projeto de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="60007-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="60007-157">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="60007-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="60007-158">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="60007-158">Spatial sound design</span></span>](spatial-sound-design.md)

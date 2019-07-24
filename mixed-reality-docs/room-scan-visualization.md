---
title: Visualização da verificação de sala
description: Os aplicativos que exigem dados de mapeamento espacial dependem do dispositivo para coletar automaticamente esses dados ao longo do tempo e entre as sessões, à medida que o usuário explora seu ambiente com o dispositivo ativo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, padrões de aplicativo, design, HoloLens, verificação de sala, mapeamento espacial, reconstrução de superfície, malha
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829909"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="2c655-104">Visualização da verificação de sala</span><span class="sxs-lookup"><span data-stu-id="2c655-104">Room scan visualization</span></span>

<span data-ttu-id="2c655-105">Os aplicativos que exigem dados de mapeamento espacial dependem do dispositivo para coletar automaticamente esses dados ao longo do tempo e entre as sessões, à medida que o usuário explora seu ambiente com o dispositivo ativo.</span><span class="sxs-lookup"><span data-stu-id="2c655-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="2c655-106">A integridade e a qualidade desses dados dependem de vários fatores, incluindo a quantidade de explorações que o usuário fez, quanto tempo passou desde a exploração e se os objetos como mobília e portas foram movidos desde que o dispositivo examinou a área.</span><span class="sxs-lookup"><span data-stu-id="2c655-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="2c655-107">Para garantir dados de mapeamento espacial úteis, os desenvolvedores de aplicativos têm várias opções:</span><span class="sxs-lookup"><span data-stu-id="2c655-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="2c655-108">Conte com o que já pode ter sido coletado.</span><span class="sxs-lookup"><span data-stu-id="2c655-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="2c655-109">Esses dados podem estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="2c655-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="2c655-110">Peça ao usuário para usar o gesto de cair para chegar à página inicial do Windows Mixed Reality e, em seguida, explorar a área que desejam usar para a experiência.</span><span class="sxs-lookup"><span data-stu-id="2c655-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="2c655-111">Eles podem usar o Air-TAP para confirmar se toda a área necessária é conhecida pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2c655-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="2c655-112">Crie uma experiência de exploração personalizada em seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c655-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="2c655-113">Observe que, em todos esses casos, os dados reais coletados durante a exploração são armazenados pelo sistema e o aplicativo não precisa fazer isso.</span><span class="sxs-lookup"><span data-stu-id="2c655-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="2c655-114">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="2c655-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2c655-115"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="2c655-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2c655-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2c655-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2c655-117"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="2c655-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2c655-118">Visualização da verificação de sala</span><span class="sxs-lookup"><span data-stu-id="2c655-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="2c655-119">✔️</span><span class="sxs-lookup"><span data-stu-id="2c655-119">✔️</span></span></td>
        <td><span data-ttu-id="2c655-120">❌</span><span class="sxs-lookup"><span data-stu-id="2c655-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="2c655-121">Criando uma experiência de verificação personalizada</span><span class="sxs-lookup"><span data-stu-id="2c655-121">Building a custom scanning experience</span></span>

<span data-ttu-id="2c655-122">Os aplicativos podem decidir analisar os dados de mapeamento espacial no início da experiência para avaliar se desejam que o usuário execute etapas adicionais para melhorar sua integridade e qualidade.</span><span class="sxs-lookup"><span data-stu-id="2c655-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="2c655-123">Se a análise indicar que a qualidade deve ser melhorada, os desenvolvedores devem fornecer uma visualização para sobreposição no mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="2c655-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="2c655-124">Quanto do volume total nos arredores dos usuários precisa fazer parte da experiência</span><span class="sxs-lookup"><span data-stu-id="2c655-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="2c655-125">Onde o usuário deve ir para melhorar os dados</span><span class="sxs-lookup"><span data-stu-id="2c655-125">Where the user should go to improve data</span></span>

<span data-ttu-id="2c655-126">Os usuários não sabem o que faz uma verificação "boa".</span><span class="sxs-lookup"><span data-stu-id="2c655-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="2c655-127">Eles precisam ser mostrados ou disseram o que procurar se forem solicitados a avaliar uma verificação – Flatness, distância de paredes reais etc. O desenvolvedor deve implementar um loop de comentários que inclua a atualização dos dados de mapeamento espacial durante a fase de verificação ou exploração.</span><span class="sxs-lookup"><span data-stu-id="2c655-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="2c655-128">Em muitos casos, pode ser melhor informar ao usuário o que eles precisam fazer (por exemplo, examinar o teto, examinar os móveis) para obter a qualidade de digitalização necessária.</span><span class="sxs-lookup"><span data-stu-id="2c655-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="2c655-129">Mapeamento espacial em cache versus contínua</span><span class="sxs-lookup"><span data-stu-id="2c655-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="2c655-130">Os dados de mapeamento espacial são os aplicativos de fonte de dados de peso mais intenso que podem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="2c655-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="2c655-131">Para evitar problemas de desempenho como quadros descartados ou excedentes, o consumo desses dados deve ser feito com cuidado.</span><span class="sxs-lookup"><span data-stu-id="2c655-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="2c655-132">A verificação ativa durante uma experiência pode ser benéfica ou prejudicial, e o desenvolvedor precisará decidir qual método usar com base na experiência.</span><span class="sxs-lookup"><span data-stu-id="2c655-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="2c655-133">Mapeamento espacial armazenado em cache</span><span class="sxs-lookup"><span data-stu-id="2c655-133">Cached spatial mapping</span></span>

<span data-ttu-id="2c655-134">No caso do mapeamento espacial armazenado em cache, o aplicativo normalmente tira um instantâneo dos dados de mapeamento espacial e usa esse instantâneo pela duração da experiência.</span><span class="sxs-lookup"><span data-stu-id="2c655-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="2c655-135">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="2c655-135">**Benefits**</span></span>
* <span data-ttu-id="2c655-136">Redução da sobrecarga no sistema, enquanto a experiência está em execução levando a uma potência drástica, ganhos térmicos e de desempenho da CPU.</span><span class="sxs-lookup"><span data-stu-id="2c655-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="2c655-137">Uma implementação mais simples da experiência principal, uma vez que ela não é interrompida por alterações nos dados espaciais.</span><span class="sxs-lookup"><span data-stu-id="2c655-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="2c655-138">Um único custo individual em qualquer pós-processamento dos dados espaciais de física, elementos gráficos e outras finalidades.</span><span class="sxs-lookup"><span data-stu-id="2c655-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="2c655-139">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="2c655-139">**Drawbacks**</span></span>
* <span data-ttu-id="2c655-140">A movimentação de objetos do mundo real ou de pessoas não é refletida pelos dados armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="2c655-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="2c655-141">Ex.</span><span class="sxs-lookup"><span data-stu-id="2c655-141">E.g.</span></span> <span data-ttu-id="2c655-142">o aplicativo pode considerar uma porta aberta quando está realmente fechado agora.</span><span class="sxs-lookup"><span data-stu-id="2c655-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="2c655-143">Possivelmente mais memória de aplicativo para manter a versão em cache dos dados.</span><span class="sxs-lookup"><span data-stu-id="2c655-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="2c655-144">Um bom caso para esse método é um ambiente controlado ou um jogo de topo de tabela.</span><span class="sxs-lookup"><span data-stu-id="2c655-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="2c655-145">Mapeamento espacial contínuo</span><span class="sxs-lookup"><span data-stu-id="2c655-145">Continuous spatial mapping</span></span>

<span data-ttu-id="2c655-146">Determinados aplicativos podem depender da varredura para atualizar dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2c655-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="2c655-147">**Benefícios**</span><span class="sxs-lookup"><span data-stu-id="2c655-147">**Benefits**</span></span>
* <span data-ttu-id="2c655-148">Você não precisa criar uma experiência separada de verificação ou exploração antecipada em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c655-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="2c655-149">A movimentação de objetos do mundo real pode ser refletida pelo jogo, embora com algum atraso.</span><span class="sxs-lookup"><span data-stu-id="2c655-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="2c655-150">**Desvantagens**</span><span class="sxs-lookup"><span data-stu-id="2c655-150">**Drawbacks**</span></span>
* <span data-ttu-id="2c655-151">Maior complexidade na implementação da experiência principal.</span><span class="sxs-lookup"><span data-stu-id="2c655-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="2c655-152">Sobrecarga potencial do processamento adicional para gráfico ou física, pois as alterações precisam ser ingeridas incrementalmente por esses sistemas.</span><span class="sxs-lookup"><span data-stu-id="2c655-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="2c655-153">Maior capacidade, impacto térmico e de CPU.</span><span class="sxs-lookup"><span data-stu-id="2c655-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="2c655-154">Um bom caso para esse método é um em que os hologramas são esperados para interagir com a movimentação de objetos, por exemplo, um carro Holographic que as unidades no chão podem desejar aumentar corretamente em uma porta dependendo se ela está aberta ou fechada.</span><span class="sxs-lookup"><span data-stu-id="2c655-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c655-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c655-155">See also</span></span>
* [<span data-ttu-id="2c655-156">Projeto de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="2c655-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="2c655-157">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="2c655-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="2c655-158">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="2c655-158">Spatial sound design</span></span>](spatial-sound-design.md)

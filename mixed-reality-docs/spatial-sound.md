---
title: Áudio em realidade misturada
description: O áudio em realidade misturada pode aumentar a confiança do usuário em interações de interface de usuário e aprofundar os usuários na experiência.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: som espacial, som surround, áudio 3D, som 3D, áudio espacial
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641112"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="6db51-104">Áudio em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="6db51-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="6db51-105">O áudio é uma parte essencial do design e da produtividade na realidade misturada e pode:</span><span class="sxs-lookup"><span data-stu-id="6db51-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="6db51-106">Aumentar a confiança do usuário em interações baseadas em gestos e em voz</span><span class="sxs-lookup"><span data-stu-id="6db51-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="6db51-107">Orientar os usuários para as próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6db51-107">Guide users to next steps</span></span>
* <span data-ttu-id="6db51-108">Combine efetivamente os objetos virtuais com o mundo real</span><span class="sxs-lookup"><span data-stu-id="6db51-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="6db51-109">O rastreamento de cabeça de baixa latência de headsets de realidade misturada, incluindo o HoloLens, permite o uso de alta qualidade de espacial baseada em HRTF.</span><span class="sxs-lookup"><span data-stu-id="6db51-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="6db51-110">A espacial de áudio em seu aplicativo pode:</span><span class="sxs-lookup"><span data-stu-id="6db51-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="6db51-111">Chame atenção para elementos visuais</span><span class="sxs-lookup"><span data-stu-id="6db51-111">Call attention to visual elements</span></span>
* <span data-ttu-id="6db51-112">Ajude os usuários a manter a conscientização de seus arredores do mundo real</span><span class="sxs-lookup"><span data-stu-id="6db51-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="6db51-113">A adição de acústicos conecta mais profundamente os hologramas ao mundo misto e pode fornecer indicações sobre o ambiente e o estado do objeto.</span><span class="sxs-lookup"><span data-stu-id="6db51-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="6db51-114">Para obter exemplos mais detalhados de design usando áudio, confira [design de som](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="6db51-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="6db51-115">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="6db51-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6db51-116"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="6db51-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6db51-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6db51-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6db51-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6db51-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6db51-119"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="6db51-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6db51-120">Espacialização</span><span class="sxs-lookup"><span data-stu-id="6db51-120">Spatialization</span></span></td>
        <td><span data-ttu-id="6db51-121">✔️</span><span class="sxs-lookup"><span data-stu-id="6db51-121">✔️</span></span></td>
        <td><span data-ttu-id="6db51-122">✔️</span><span class="sxs-lookup"><span data-stu-id="6db51-122">✔️</span></span></td>
        <td><span data-ttu-id="6db51-123">✔️</span><span class="sxs-lookup"><span data-stu-id="6db51-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6db51-124">Aceleração de hardware de espacial</span><span class="sxs-lookup"><span data-stu-id="6db51-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6db51-125">✔️</span><span class="sxs-lookup"><span data-stu-id="6db51-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="6db51-126">Usando sons em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="6db51-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="6db51-127">[Usar sons em realidade mista](spatial-sound-design.md) pode exigir uma abordagem diferente do que em aplicativos de toque e teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="6db51-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="6db51-128">As decisões de design de sons-chave incluem quais sons são espaciais e quais interações sonify.</span><span class="sxs-lookup"><span data-stu-id="6db51-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="6db51-129">Essas decisões podem ter um efeito forte na confiança do usuário, na produtividade e na curva de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="6db51-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="6db51-130">Estudos de caso</span><span class="sxs-lookup"><span data-stu-id="6db51-130">Case studies</span></span>
<span data-ttu-id="6db51-131">O HoloTour praticamente leva os usuários para os sites Tourist e históricos em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="6db51-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="6db51-132">O seguinte estudo de caso descreve o design de som para HoloTour: [design de som para HoloTour](case-study-spatial-sound-design-for-holotour.md).</span><span class="sxs-lookup"><span data-stu-id="6db51-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="6db51-133">Um microfone especial e uma configuração de renderização foram usados para capturar os espaços de assunto.</span><span class="sxs-lookup"><span data-stu-id="6db51-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="6db51-134">RoboRaid é um shooter de alta energia para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6db51-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="6db51-135">O seguinte estudo de caso descreve as opções de design feitas para garantir que o áudio espacial foi usado para um efeito mais completo: [design de som para RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span><span class="sxs-lookup"><span data-stu-id="6db51-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="6db51-136">Espacialização</span><span class="sxs-lookup"><span data-stu-id="6db51-136">Spatialization</span></span>
<span data-ttu-id="6db51-137">A espacialização é o componente direcional do áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="6db51-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="6db51-138">Ao usar uma configuração de Home Theater 7,1, a espacial é tão simples quanto a visão panorâmica entre alto-falantes.</span><span class="sxs-lookup"><span data-stu-id="6db51-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="6db51-139">Mas com fones de ouvido em realidade misturada, é essencial usar uma tecnologia baseada em HRTF para precisão e conforto.</span><span class="sxs-lookup"><span data-stu-id="6db51-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="6db51-140">O Windows oferece a espacial baseada em HRTF, e esse suporte é acelerado por hardware no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6db51-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="6db51-141">Devo me esespacial?</span><span class="sxs-lookup"><span data-stu-id="6db51-141">Should I spatialize?</span></span>
<span data-ttu-id="6db51-142">Muitos sons em aplicativos de realidade misturados se beneficiam da espacial, que tira um som da cabeça do ouvinte e o coloca no mundo.</span><span class="sxs-lookup"><span data-stu-id="6db51-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="6db51-143">Consulte [design de som espacial](spatial-sound-design.md) para obter sugestões sobre os usos mais eficientes da espacialização em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6db51-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="6db51-144">Personalização de Spatializer</span><span class="sxs-lookup"><span data-stu-id="6db51-144">Spatializer personalization</span></span>
<span data-ttu-id="6db51-145">HRTFs Manipule as diferenças de nível e fase entre os ouvidos pelo espectro de frequência.</span><span class="sxs-lookup"><span data-stu-id="6db51-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="6db51-146">Elas se baseiam em modelos físicos e medidas de pinnae (torso), de cabeça humana e de formas Ear.</span><span class="sxs-lookup"><span data-stu-id="6db51-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="6db51-147">Nosso cérebro responde a essas diferenças para dar uma percepção de direção em som.</span><span class="sxs-lookup"><span data-stu-id="6db51-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="6db51-148">Cada indivíduo tem uma forma Ear exclusiva, tamanho da cabeça e posição ear, portanto, os melhores HRTFs são aqueles que estão em conformidade com você.</span><span class="sxs-lookup"><span data-stu-id="6db51-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="6db51-149">O HoloLens aumenta a precisão da espacial usando a pupilaryy (distância) do headset exibido para ajustar o HRTFs para o tamanho da cabeça.</span><span class="sxs-lookup"><span data-stu-id="6db51-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="6db51-150">Suporte à plataforma Spatializer</span><span class="sxs-lookup"><span data-stu-id="6db51-150">Spatializer platform support</span></span>
<span data-ttu-id="6db51-151">O Windows oferece a espacialização, incluindo HRTFs, por meio da [API do ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span><span class="sxs-lookup"><span data-stu-id="6db51-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="6db51-152">Essa API expõe a aceleração de hardware de HRTF do HoloLens 2 para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6db51-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="6db51-153">Suporte de middleware Spatializer</span><span class="sxs-lookup"><span data-stu-id="6db51-153">Spatializer middleware support</span></span>
<span data-ttu-id="6db51-154">O suporte para o Windows ' HRTFs está disponível para alguns mecanismos de áudio de terceiros:</span><span class="sxs-lookup"><span data-stu-id="6db51-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="6db51-155">Um plug-in do [mecanismo de áudio do Unity](spatial-sound-in-unity.md) chama o HRTF XAPO</span><span class="sxs-lookup"><span data-stu-id="6db51-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="6db51-156">Um [plug-in do mecanismo de áudio WWise](https://www.audiokinetic.com/products/plug-ins/msspatial/) chama a API ISpatialAudioClient</span><span class="sxs-lookup"><span data-stu-id="6db51-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="6db51-157">Acústica</span><span class="sxs-lookup"><span data-stu-id="6db51-157">Acoustics</span></span>
<span data-ttu-id="6db51-158">O áudio espacial pode ser maior que a direção.</span><span class="sxs-lookup"><span data-stu-id="6db51-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="6db51-159">Outras dimensões, incluindo oclusão, obstrução, reverberação, portal e modelagem de origem, são coletivamente chamadas de ' acústicas '.</span><span class="sxs-lookup"><span data-stu-id="6db51-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="6db51-160">Sem acústicas, os sons espaciais não têm uma distância percebida.</span><span class="sxs-lookup"><span data-stu-id="6db51-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="6db51-161">O tratamento acústico pode variar de simples a muito complexo.</span><span class="sxs-lookup"><span data-stu-id="6db51-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="6db51-162">Usando um simples reverbo, como o que tem suporte de qualquer mecanismo de áudio, você pode enviar sons espaciais para o ambiente ao redor do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="6db51-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="6db51-163">O tratamento acústico mais atrativo e mais atraente está disponível em sistemas acústicos como [acústicos de projetos](https://aka.ms/acoustics).</span><span class="sxs-lookup"><span data-stu-id="6db51-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="6db51-164">Os acústicos de projeto podem modelar o efeito de paredes, portas e outras geometrias de cena em um som e é uma opção eficaz para casos em que a geometria de cena relevante é conhecida no momento do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="6db51-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>


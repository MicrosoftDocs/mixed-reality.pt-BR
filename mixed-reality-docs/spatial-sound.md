---
title: Áudio em realidade misturada
description: O áudio em realidade misturada pode aumentar a confiança do usuário em interações de interface de usuário e aprofundar os usuários na experiência.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: som espacial, som surround, áudio 3D, som 3D, áudio espacial
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181976"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="bb5a9-104">Áudio em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="bb5a9-104">Audio in mixed reality</span></span>
<span data-ttu-id="bb5a9-105">O áudio é uma parte essencial do design e da produtividade na realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="bb5a9-106">O som pode:</span><span class="sxs-lookup"><span data-stu-id="bb5a9-106">Sound can:</span></span>
* <span data-ttu-id="bb5a9-107">Aumente a confiança do usuário em interações de gesto e voz.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="bb5a9-108">Oriente os usuários para as próximas etapas.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-108">Guide users to next steps.</span></span>
* <span data-ttu-id="bb5a9-109">Combine efetivamente os objetos virtuais com o mundo real.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="bb5a9-110">O rastreamento de cabeça de baixa latência de headsets de realidade misturada, incluindo o HoloLens, dá suporte à espacial de alta qualidade baseada em HRTF.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="bb5a9-111">Você pode espacialar o áudio em seu aplicativo para:</span><span class="sxs-lookup"><span data-stu-id="bb5a9-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="bb5a9-112">Chame atenção para elementos visuais.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="bb5a9-113">Ajude os usuários a manter a conscientização de seus arredores do mundo real.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="bb5a9-114">A acústica conecta mais profundamente os hologramas ao mundo da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="bb5a9-115">Ele fornece indicações sobre o ambiente e o estado do objeto.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="bb5a9-116">Consulte exemplos detalhados [de design que usa áudio](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="bb5a9-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="bb5a9-117">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="bb5a9-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bb5a9-118"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="bb5a9-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="bb5a9-119"><a href="hololens-hardware-details.md"><strong>HoloLens (primeira gen)</strong></a></span><span class="sxs-lookup"><span data-stu-id="bb5a9-119"><a href="hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="bb5a9-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="bb5a9-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="bb5a9-121"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="bb5a9-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bb5a9-122">Espacialização</span><span class="sxs-lookup"><span data-stu-id="bb5a9-122">Spatialization</span></span></td>
        <td><span data-ttu-id="bb5a9-123">✔️</span><span class="sxs-lookup"><span data-stu-id="bb5a9-123">✔️</span></span></td>
        <td><span data-ttu-id="bb5a9-124">✔️</span><span class="sxs-lookup"><span data-stu-id="bb5a9-124">✔️</span></span></td>
        <td><span data-ttu-id="bb5a9-125">✔️</span><span class="sxs-lookup"><span data-stu-id="bb5a9-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bb5a9-126">Aceleração de hardware de espacial</span><span class="sxs-lookup"><span data-stu-id="bb5a9-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="bb5a9-127">✔️</span><span class="sxs-lookup"><span data-stu-id="bb5a9-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="bb5a9-128">Uso de sons em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="bb5a9-128">Use of sounds in mixed reality</span></span>
<span data-ttu-id="bb5a9-129">O [uso de sons em realidade misturada](spatial-sound-design.md) requer uma abordagem diferente do que em aplicativos de toque e teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="bb5a9-130">As decisões de design de sons-chave incluem quais sons são espaciais e quais interações sonify.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="bb5a9-131">Essas decisões afetam altamente a confiança do usuário, a produtividade e a curva de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="bb5a9-132">Estudos de caso</span><span class="sxs-lookup"><span data-stu-id="bb5a9-132">Case studies</span></span>
<span data-ttu-id="bb5a9-133">O HoloTour praticamente leva os usuários para os sites Tourist e históricos em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="bb5a9-134">Consulte o [projeto de som para o estudo de caso do HoloTour](case-study-spatial-sound-design-for-holotour.md) .</span><span class="sxs-lookup"><span data-stu-id="bb5a9-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="bb5a9-135">Um microfone especial e uma configuração de renderização foram usados para capturar os espaços de assunto.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="bb5a9-136">RoboRaid é um shooter de alta energia para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="bb5a9-137">O [projeto de som para](case-study-using-spatial-sound-in-roboraid.md) o estudo de caso do RoboRaid descreve as opções de design que foram feitas para garantir que o áudio espacial foi usado para o efeito significativo mais completo.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="bb5a9-138">Espacialização</span><span class="sxs-lookup"><span data-stu-id="bb5a9-138">Spatialization</span></span>
<span data-ttu-id="bb5a9-139">A espacialização é o componente direcional do áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="bb5a9-140">Para uma configuração de Home Theater 7,1, a espacial é tão simples quanto a panorâmica entre loudspeakers.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="bb5a9-141">Mas para fones de ouvido em realidade misturada, é essencial usar uma tecnologia baseada em HRTF para precisão e conforto.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="bb5a9-142">O Windows oferece a espacial baseada em HRTF, e esse suporte é acelerado por hardware no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="bb5a9-143">Devo me esespacial?</span><span class="sxs-lookup"><span data-stu-id="bb5a9-143">Should I spatialize?</span></span>
<span data-ttu-id="bb5a9-144">A espacialização pode melhorar muitos sons em aplicativos de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="bb5a9-145">A espacial tira um som da cabeça do ouvinte e a coloca no mundo.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="bb5a9-146">Para obter sugestões sobre o uso efetivo da espacialização em seu aplicativo, consulte [design de som espacial](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="bb5a9-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="bb5a9-147">Personalização de Spatializer</span><span class="sxs-lookup"><span data-stu-id="bb5a9-147">Spatializer personalization</span></span>
<span data-ttu-id="bb5a9-148">HRTFs Manipule as diferenças de nível e fase entre os ouvidos pelo espectro de frequência.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="bb5a9-149">Elas se baseiam em modelos físicos e medidas de pinnae (torso), de cabeça humana e de formas Ear.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="bb5a9-150">Nosso cérebro responde a essas diferenças para fornecer uma direção percebida em som.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="bb5a9-151">Cada indivíduo tem uma forma Ear exclusiva, tamanho da cabeça e posição Ear.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="bb5a9-152">Portanto, a melhor HRTFs está em conformidade com você.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="bb5a9-153">Para aumentar a precisão da espacialização, o HoloLens usa a Pupilary de distância (IPD) do headset para ajustar o HRTFs para o tamanho da cabeça.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="bb5a9-154">Suporte à plataforma Spatializer</span><span class="sxs-lookup"><span data-stu-id="bb5a9-154">Spatializer platform support</span></span>
<span data-ttu-id="bb5a9-155">O Windows oferece a espacialização, incluindo HRTFs, por meio da [API do ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span><span class="sxs-lookup"><span data-stu-id="bb5a9-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="bb5a9-156">Essa API expõe a aceleração de hardware de HRTF do HoloLens 2 para aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="bb5a9-157">Suporte de middleware Spatializer</span><span class="sxs-lookup"><span data-stu-id="bb5a9-157">Spatializer middleware support</span></span>
<span data-ttu-id="bb5a9-158">O suporte para o Windows ' HRTFs está disponível para os seguintes mecanismos de áudio de terceiros.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="bb5a9-159">Um [plug-in do mecanismo de áudio do Unity](spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="bb5a9-159">A [Unity audio engine plugin](spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="bb5a9-160">Um [plug-in do mecanismo de áudio WWise](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="bb5a9-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="bb5a9-161">Acústica</span><span class="sxs-lookup"><span data-stu-id="bb5a9-161">Acoustics</span></span>
<span data-ttu-id="bb5a9-162">O áudio espacial é maior que a direção.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="bb5a9-163">Outras dimensões incluem oclusão, obstrução, reverberação, portal e modelagem de origem.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-163">Other dimensions include occlusion, obstruction, reverb, portalling, and source modeling.</span></span> <span data-ttu-id="bb5a9-164">Coletivamente, essas dimensões são chamadas de *acústicas*.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="bb5a9-165">Sem acústicas, os sons espaciais não têm distância percebida.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="bb5a9-166">Os tratamentos acústicos variam de simples a muito complexo.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-166">Acoustics treatments range from simple to very complex.</span></span> <span data-ttu-id="bb5a9-167">Você pode usar um simples reverbo com suporte em qualquer mecanismo de áudio para enviar sons espaciais para o ambiente do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-167">You can use a simple reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="bb5a9-168">Sistemas acústicos como [acústicas de projetos](https://aka.ms/acoustics) fornecem tratamento acústico mais rico e mais atraente.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-168">Acoustics systems such as [Project Acoustics](https://aka.ms/acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="bb5a9-169">Os acústicos de projeto podem modelar o efeito de paredes, portas e outras geometrias de cena em um som.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="bb5a9-170">É uma opção eficaz para casos em que a geometria de cena relevante é conhecida no momento do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bb5a9-171">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="bb5a9-171">Next steps</span></span>
- [<span data-ttu-id="bb5a9-172">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="bb5a9-172">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
- [<span data-ttu-id="bb5a9-173">Como usar o som em aplicativos de realidade mista</span><span class="sxs-lookup"><span data-stu-id="bb5a9-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)

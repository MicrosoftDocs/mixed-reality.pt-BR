---
title: Som espacial no Unity
description: Reproduzir o som espacial de um ponto 3D específico dentro de sua cena do Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, som espacial, HRTF, tamanho da sala
ms.openlocfilehash: 3e7d0ea231545d5112d182dffbc02f217ca4a4a7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181986"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="66284-104">Som espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="66284-104">Spatial sound in Unity</span></span>

<span data-ttu-id="66284-105">Esta página contém links para recursos de som espacial no Unity.</span><span class="sxs-lookup"><span data-stu-id="66284-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="66284-106">Opções de Spatializer</span><span class="sxs-lookup"><span data-stu-id="66284-106">Spatializer options</span></span>
<span data-ttu-id="66284-107">As opções de Spatializer para aplicativos de realidade misturada incluem:</span><span class="sxs-lookup"><span data-stu-id="66284-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="66284-108">*SPATIALIZER HRTF MS*.</span><span class="sxs-lookup"><span data-stu-id="66284-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="66284-109">O Unity fornece isso como parte do pacote opcional do *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="66284-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="66284-110">Isso é executado na CPU em uma arquitetura de ' fonte única ' de maior custo.</span><span class="sxs-lookup"><span data-stu-id="66284-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="66284-111">Isso é fornecido para compatibilidade com versões anteriores com aplicativos de HoloLens originais.</span><span class="sxs-lookup"><span data-stu-id="66284-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="66284-112">O *Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="66284-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="66284-113">Isso está disponível no [repositório GitHub do Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="66284-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="66284-114">Isso usa uma arquitetura de "várias fontes" de menor custo.</span><span class="sxs-lookup"><span data-stu-id="66284-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="66284-115">No HoloLens 2, isso é descarregado para um acelerador de hardware.</span><span class="sxs-lookup"><span data-stu-id="66284-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="66284-116">Para novos aplicativos, recomendamos o *Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="66284-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="66284-117">Habilitar a espacialização</span><span class="sxs-lookup"><span data-stu-id="66284-117">Enable spatialization</span></span>

<span data-ttu-id="66284-118">Use o [NuGet para o Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft. SpatialAudio. Spatializer. Unity_ e escolha **Microsoft Spatializer** nas configurações de áudio do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="66284-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="66284-119">Então:</span><span class="sxs-lookup"><span data-stu-id="66284-119">Then:</span></span>
* <span data-ttu-id="66284-120">Anexar uma **fonte de áudio** a um objeto na hierarquia</span><span class="sxs-lookup"><span data-stu-id="66284-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="66284-121">Marque a caixa de seleção **habilitar a espacial**</span><span class="sxs-lookup"><span data-stu-id="66284-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="66284-122">Mover o controle deslizante de **mistura espacial** para ' 1 '</span><span class="sxs-lookup"><span data-stu-id="66284-122">Move the **Spatial Blend** slider to '1'</span></span>

<span data-ttu-id="66284-123">Para obter mais detalhes, consulte:</span><span class="sxs-lookup"><span data-stu-id="66284-123">For more details, see:</span></span>
* [<span data-ttu-id="66284-124">Repositório GitHub do Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="66284-124">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="66284-125">Tutorial do spatializer da Microsoft</span><span class="sxs-lookup"><span data-stu-id="66284-125">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="66284-126">Documentação da fonte de áudio do Unity</span><span class="sxs-lookup"><span data-stu-id="66284-126">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="66284-127">Documentação do spatializer do Unity</span><span class="sxs-lookup"><span data-stu-id="66284-127">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="66284-128">Atenuação de distância</span><span class="sxs-lookup"><span data-stu-id="66284-128">Distance-based attenuation</span></span>
<span data-ttu-id="66284-129">O decaimento baseado em distância padrão da Unity tem uma distância mínima de 1 medidor e uma distância máxima de 500 metros, com um rolloff logarítmica.</span><span class="sxs-lookup"><span data-stu-id="66284-129">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="66284-130">Essas configurações podem funcionar para seu cenário, ou você pode achar que as fontes são atenuadas muito rapidamente ou lentas.</span><span class="sxs-lookup"><span data-stu-id="66284-130">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="66284-131">Para obter mais detalhes, consulte:</span><span class="sxs-lookup"><span data-stu-id="66284-131">For more details, see:</span></span>
* <span data-ttu-id="66284-132">[Design de som em realidade misturada](spatial-sound-design.md) para as configurações recomendadas.</span><span class="sxs-lookup"><span data-stu-id="66284-132">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="66284-133">[Documentação de fonte de áudio do Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obter instruções sobre como definir essas curvas.</span><span class="sxs-lookup"><span data-stu-id="66284-133">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="66284-134">Reverberação</span><span class="sxs-lookup"><span data-stu-id="66284-134">Reverb</span></span>
<span data-ttu-id="66284-135">Por padrão, o _Microsoft Spatializer_ desabilita os efeitos de Spatializer.</span><span class="sxs-lookup"><span data-stu-id="66284-135">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="66284-136">Para habilitar o reverberar e outros efeitos para fontes espaciais:</span><span class="sxs-lookup"><span data-stu-id="66284-136">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="66284-137">Anexar o componente de **nível de envio de efeito Room** a cada fonte</span><span class="sxs-lookup"><span data-stu-id="66284-137">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="66284-138">Ajuste a curva de nível de envio para cada fonte, para controlar o lucro do áudio enviado de volta ao grafo para o processamento de efeitos</span><span class="sxs-lookup"><span data-stu-id="66284-138">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="66284-139">Consulte [o capítulo 5 do tutorial do spatializer](unity-spatial-audio-ch5.md) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="66284-139">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="66284-140">Exemplos de som espacial do Unity</span><span class="sxs-lookup"><span data-stu-id="66284-140">Unity spatial sound examples</span></span>
<span data-ttu-id="66284-141">Para obter exemplos de som espacial no Unity, consulte:</span><span class="sxs-lookup"><span data-stu-id="66284-141">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="66284-142">Demonstrações do MRTK</span><span class="sxs-lookup"><span data-stu-id="66284-142">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="66284-143">O [projeto de exemplo Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="66284-143">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="66284-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="66284-144">Next steps</span></span>
* [<span data-ttu-id="66284-145">Design de som em realidade misturada</span><span class="sxs-lookup"><span data-stu-id="66284-145">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="66284-146">Tutorial do spatializer da Microsoft</span><span class="sxs-lookup"><span data-stu-id="66284-146">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)


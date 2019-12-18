---
title: Tutoriais de áudio espacial-3. Disespacial de áudio de um vídeo
description: Importar um ativo de vídeo para seu projeto do Unity e espacialar o áudio do vídeo.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidade misturada, Unity, tutorial, hololens2, áudio espacial
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182743"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="90634-105">Disespacial de áudio de um vídeo</span><span class="sxs-lookup"><span data-stu-id="90634-105">Spatializing audio from a video</span></span>
<span data-ttu-id="90634-106">Neste terceiro capítulo do módulo de áudio espacial dos tutoriais do HoloLens 2 Unity, você irá:</span><span class="sxs-lookup"><span data-stu-id="90634-106">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="90634-107">Importar um vídeo e adicionar um player de vídeo</span><span class="sxs-lookup"><span data-stu-id="90634-107">Import a video and add a Video Player</span></span>
* <span data-ttu-id="90634-108">Reproduza o vídeo em um Quadrangle</span><span class="sxs-lookup"><span data-stu-id="90634-108">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="90634-109">Rotear áudio do vídeo para o Quadrangle e espacialar o áudio</span><span class="sxs-lookup"><span data-stu-id="90634-109">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="90634-110">Importar um vídeo e adicionar um player de vídeo</span><span class="sxs-lookup"><span data-stu-id="90634-110">Import a video and add a Video Player</span></span>

<span data-ttu-id="90634-111">Arraste um arquivo de vídeo para o painel **projeto** em seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="90634-111">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="90634-112">Você pode usar [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) do projeto de exemplo de áudio espacial.</span><span class="sxs-lookup"><span data-stu-id="90634-112">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Pasta de ativos com vídeo](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="90634-114">Ajustar as configurações de qualidade no clipe de vídeo pode garantir uma reprodução suave no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="90634-114">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="90634-115">Clique no arquivo de vídeo no painel **projeto** .</span><span class="sxs-lookup"><span data-stu-id="90634-115">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="90634-116">Em seguida, no painel **Inspetor** do arquivo de vídeo, substitua as configurações para aplicativos da Windows Store e:</span><span class="sxs-lookup"><span data-stu-id="90634-116">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="90634-117">Habilitar **transcodificação**</span><span class="sxs-lookup"><span data-stu-id="90634-117">Enable **Transcode**</span></span>
* <span data-ttu-id="90634-118">Definir o **codec** como H264</span><span class="sxs-lookup"><span data-stu-id="90634-118">Set **Codec** to H264</span></span>
* <span data-ttu-id="90634-119">Definir o **modo de taxa de bits** como baixo</span><span class="sxs-lookup"><span data-stu-id="90634-119">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="90634-120">Definir **qualidade espacial** para qualidade espacial média</span><span class="sxs-lookup"><span data-stu-id="90634-120">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="90634-121">Após esses ajustes, o painel de **Inspetor** do arquivo de vídeo terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="90634-121">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Painel de propriedades de vídeo](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="90634-123">Em seguida, adicione um objeto **player de vídeo** à **hierarquia** clicando com o botão direito do mouse no painel **hierarquia** e escolhendo **vídeo-> player de vídeo**:</span><span class="sxs-lookup"><span data-stu-id="90634-123">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![Player de vídeo na hierarquia](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="90634-125">Reproduzir vídeo em um Quadrangle</span><span class="sxs-lookup"><span data-stu-id="90634-125">Play video onto a quadrangle</span></span>
<span data-ttu-id="90634-126">O objeto **player de vídeo** precisa de um objeto de jogo texturizado no qual renderizar o vídeo.</span><span class="sxs-lookup"><span data-stu-id="90634-126">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="90634-127">Primeiro, adicione um **Quad** à sua **hierarquia** clicando com o botão direito do mouse no painel **hierarquia** e escolhendo **objeto 3D-> Quad**:</span><span class="sxs-lookup"><span data-stu-id="90634-127">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![Adicionar quádruplo à hierarquia](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="90634-129">Para garantir que o **Quad** apareça na frente do usuário quando o aplicativo é iniciado, defina a propriedade **Position** de **Quad** para (0, 0, 2) e a propriedade **Scale** como (1,28, 0,72, 1).</span><span class="sxs-lookup"><span data-stu-id="90634-129">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="90634-130">Após essas alterações, o componente **transformação** no painel **Inspetor** para o **Quad** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="90634-130">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Transformação quádrupla](images/spatial-audio/quad-transform.png)

<span data-ttu-id="90634-132">Para Texturizar o **Quad** com vídeo, crie uma nova **textura de renderização**.</span><span class="sxs-lookup"><span data-stu-id="90634-132">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="90634-133">No painel **projeto** , clique com o botão direito do mouse e escolha **criar-> renderizar textura**:</span><span class="sxs-lookup"><span data-stu-id="90634-133">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![Criar textura de renderização](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="90634-135">No painel **Inspetor** da **textura renderizar**, defina a propriedade **tamanho** para corresponder à resolução nativa do vídeo de 1280x720.</span><span class="sxs-lookup"><span data-stu-id="90634-135">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="90634-136">Em seguida, para garantir um bom desempenho de renderização no HoloLens 2, defina a propriedade **buffer de profundidade** com **pelo menos 16 bits de profundidade**.</span><span class="sxs-lookup"><span data-stu-id="90634-136">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="90634-137">Após essas configurações, o painel de **Inspetor** para a **textura de renderização** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="90634-137">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Renderizar Propriedades de textura](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="90634-139">Em seguida, use sua nova **textura de renderização** como a textura para o **Quad**:</span><span class="sxs-lookup"><span data-stu-id="90634-139">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="90634-140">Arraste a **textura renderizar** do painel **projeto** para o **Quad** na **hierarquia**</span><span class="sxs-lookup"><span data-stu-id="90634-140">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="90634-141">Para garantir um bom desempenho no HoloLens 2, no painel do **Inspetor** para o **Quad**, selecione o **sombreador standard do kit de ferramentas da realidade misturada**.</span><span class="sxs-lookup"><span data-stu-id="90634-141">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="90634-142">Com essas configurações, o componente de **textura** no painel de **Inspetor** para o **Quad** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="90634-142">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Propriedades de textura quádrupla](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="90634-144">Para definir o novo **player de vídeo** e **renderizar a textura** para reproduzir o clipe de vídeo, abra o painel do **Inspetor** para o **player de vídeo** e:</span><span class="sxs-lookup"><span data-stu-id="90634-144">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="90634-145">Defina a propriedade **videoclipe** como seu arquivo de vídeo</span><span class="sxs-lookup"><span data-stu-id="90634-145">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="90634-146">Marque a caixa de seleção **loop**</span><span class="sxs-lookup"><span data-stu-id="90634-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="90634-147">Definir a **textura de destino** para sua nova textura de renderização</span><span class="sxs-lookup"><span data-stu-id="90634-147">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="90634-148">O painel **Inspetor** do **player de vídeo** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="90634-148">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Propriedades do player de vídeo](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="90634-150">Esespacialr o áudio do vídeo</span><span class="sxs-lookup"><span data-stu-id="90634-150">Spatialize the audio from the video</span></span>
<span data-ttu-id="90634-151">No painel de **Inspetor** para o **Quad**, crie uma **fonte de áudio** para a qual você encaminhará o áudio do vídeo:</span><span class="sxs-lookup"><span data-stu-id="90634-151">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="90634-152">Clique em **Adicionar componente** na parte inferior do painel</span><span class="sxs-lookup"><span data-stu-id="90634-152">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="90634-153">Adicionar uma **fonte de áudio**</span><span class="sxs-lookup"><span data-stu-id="90634-153">Add an **Audio Source**</span></span>

<span data-ttu-id="90634-154">Em seguida, na **fonte de áudio**:</span><span class="sxs-lookup"><span data-stu-id="90634-154">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="90634-155">Definir **saída** para o mixer</span><span class="sxs-lookup"><span data-stu-id="90634-155">Set **Output** to your mixer</span></span>
* <span data-ttu-id="90634-156">Marque a caixa **espacialize**</span><span class="sxs-lookup"><span data-stu-id="90634-156">Check the **Spatialize** box</span></span>
* <span data-ttu-id="90634-157">Mover o controle deslizante de **mistura espacial** para 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="90634-157">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="90634-158">Após essas alterações, o componente **fonte de áudio** no painel **Inspetor** para o **Quad** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="90634-158">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Inspetor de fonte de áudio quádruplo](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="90634-160">Para definir o **player de vídeo** para rotear seu áudio para a **fonte de áudio** no **Quad**, abra o painel do **Inspetor** para o **player de vídeo** e:</span><span class="sxs-lookup"><span data-stu-id="90634-160">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="90634-161">Definir o **modo de saída de áudio** como ' fonte de áudio '</span><span class="sxs-lookup"><span data-stu-id="90634-161">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="90634-162">Definir a propriedade **fonte de áudio** para o quad</span><span class="sxs-lookup"><span data-stu-id="90634-162">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="90634-163">Após essas alterações, o painel de **Inspetor** do **player de vídeo** terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="90634-163">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Fonte de áudio definida do player de vídeo](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="90634-165">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="90634-165">Next steps</span></span>
<span data-ttu-id="90634-166">Experimente seu aplicativo em um HoloLens 2 ou no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="90634-166">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="90634-167">Você verá e ouvirá o vídeo e o áudio do vídeo será espacial.</span><span class="sxs-lookup"><span data-stu-id="90634-167">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

<span data-ttu-id="90634-168">Continue no [capítulo 4](unity-spatial-audio-ch4.md) para usar o botão para habilitar e desabilitar a espacial em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="90634-168">Continue to [Chapter 4](unity-spatial-audio-ch4.md) to use the button to enable and disable spatialization at run time.</span></span>


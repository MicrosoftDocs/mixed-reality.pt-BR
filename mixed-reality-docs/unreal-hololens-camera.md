---
title: Câmera de foto/vídeo do HoloLens no Unreal
description: Guia para usar a câmera de foto/vídeo do HoloLens no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, PV camera, MRC
ms.openlocfilehash: e15ea593283a22dc31cd496de596159035d83799
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720322"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="04dea-104">Câmera de foto/vídeo do HoloLens no Unreal</span><span class="sxs-lookup"><span data-stu-id="04dea-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="04dea-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="04dea-105">Overview</span></span>

<span data-ttu-id="04dea-106">O HoloLens tem uma câmera de foto/vídeo (PV) que é usada para a MRC (captura de realidade misturada) e pode também ser usada por um aplicativo para acessar elementos visuais do mundo real.</span><span class="sxs-lookup"><span data-stu-id="04dea-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="04dea-107">Renderizar da câmera de PV para MRC</span><span class="sxs-lookup"><span data-stu-id="04dea-107">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="04dea-108">Isso requer o **Unreal Engine 4.25** ou posterior.</span><span class="sxs-lookup"><span data-stu-id="04dea-108">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="04dea-109">O sistema e os gravadores personalizados de MRC criam capturas de realidade misturada combinando a câmera de PV com hologramas renderizados pelo aplicativo de imersão.</span><span class="sxs-lookup"><span data-stu-id="04dea-109">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="04dea-110">Por padrão, a captura de realidade misturada usa a saída holográfica do olho direito.</span><span class="sxs-lookup"><span data-stu-id="04dea-110">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="04dea-111">Se um aplicativo de imersão optar por [renderizar da câmera de PV](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), isso será usado em vez do padrão citado acima.</span><span class="sxs-lookup"><span data-stu-id="04dea-111">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="04dea-112">Isso melhora o mapeamento entre o mundo real e os hologramas no vídeo do MRC.</span><span class="sxs-lookup"><span data-stu-id="04dea-112">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="04dea-113">Para aceitar a renderização da câmera de PV:</span><span class="sxs-lookup"><span data-stu-id="04dea-113">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="04dea-114">Chamar **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="04dea-114">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="04dea-115">Use os valores de **Tamanho X** e **Tamanho Y** para definir as dimensões do vídeo.</span><span class="sxs-lookup"><span data-stu-id="04dea-115">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Terceira câmera](images/unreal-camera-3rd.PNG)

<span data-ttu-id="04dea-117">Em seguida, o Unreal lidará com as solicitações da MRC para renderizar da perspectiva da câmera de PV.</span><span class="sxs-lookup"><span data-stu-id="04dea-117">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="04dea-118">Somente quando a [Captura de Realidade Misturada](mixed-reality-capture.md) for disparada, o aplicativo será solicitado a renderizar partindo da perspectiva da câmera de foto/vídeo.</span><span class="sxs-lookup"><span data-stu-id="04dea-118">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="04dea-119">Usando a câmera de PV</span><span class="sxs-lookup"><span data-stu-id="04dea-119">Using the PV Camera</span></span>

<span data-ttu-id="04dea-120">A textura de webcam pode ser recuperada no jogo em runtime, mas precisa ser habilitada no menu **Editar > Configurações de Projeto** do editor:</span><span class="sxs-lookup"><span data-stu-id="04dea-120">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="04dea-121">Acesse **Plataformas > HoloLens > Funcionalidades** e marque **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="04dea-121">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="04dea-122">Use a função **StartCameraCapture** para usar a webcam em runtime e a função **StopCameraCapture** para interromper a gravação.</span><span class="sxs-lookup"><span data-stu-id="04dea-122">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Iniciar/interromper câmera](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="04dea-124">Renderização de uma imagem</span><span class="sxs-lookup"><span data-stu-id="04dea-124">Rendering an image</span></span>
<span data-ttu-id="04dea-125">Para renderizar a imagem da câmera:</span><span class="sxs-lookup"><span data-stu-id="04dea-125">To render the camera image:</span></span>
1. <span data-ttu-id="04dea-126">Crie uma instância de material dinâmico com base em um material no projeto, nomeado **PVCamMat** na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="04dea-126">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="04dea-127">Defina a instância de material dinâmico para uma variável de **Referência de Objeto Dinâmico da Instância de Material**.</span><span class="sxs-lookup"><span data-stu-id="04dea-127">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="04dea-128">Defina o material do objeto na cena que renderizará o feed da câmera para essa nova instância de material dinâmico.</span><span class="sxs-lookup"><span data-stu-id="04dea-128">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="04dea-129">Inicie um temporizador que será usado para associar a imagem da câmera ao material.</span><span class="sxs-lookup"><span data-stu-id="04dea-129">Start a timer that will be used to bind the camera image to the material.</span></span> 

![Renderização da câmera](images/unreal-camera-render.PNG)

4. <span data-ttu-id="04dea-131">Crie uma função para esse temporizador (neste caso, **MaterialTimer**) e chame **GetARCameraImage** para obter a textura da webcam.</span><span class="sxs-lookup"><span data-stu-id="04dea-131">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="04dea-132">Se a textura for válida, defina um parâmetro de textura no sombreador para a imagem.</span><span class="sxs-lookup"><span data-stu-id="04dea-132">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="04dea-133">Caso contrário, inicie o temporizador de material novamente.</span><span class="sxs-lookup"><span data-stu-id="04dea-133">Otherwise, start the material timer again.</span></span> 

![Textura da câmera](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="04dea-135">Verifique se o material tem um parâmetro correspondente ao nome em **SetTextureParameterValue** que esteja associado a uma entrada de cor.</span><span class="sxs-lookup"><span data-stu-id="04dea-135">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="04dea-136">Sem isso, a imagem da câmera não pode ser exibida corretamente.</span><span class="sxs-lookup"><span data-stu-id="04dea-136">Without this, the camera image can't be properly displayed.</span></span>

![Textura da câmera](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="04dea-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="04dea-138">See also</span></span>
* [<span data-ttu-id="04dea-139">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="04dea-139">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="04dea-140">Captura de realidade misturada para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="04dea-140">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)

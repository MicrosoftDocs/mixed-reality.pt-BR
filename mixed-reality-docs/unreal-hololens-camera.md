---
title: Câmera de foto/vídeo do HoloLens no Unreal
description: Guia para usar a câmera de foto/vídeo do HoloLens no Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, PV camera, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451331"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="ac07d-104">Câmera de foto/vídeo do HoloLens no Unreal</span><span class="sxs-lookup"><span data-stu-id="ac07d-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="ac07d-105">O HoloLens tem uma câmera de foto/vídeo (PV) que é usada para a MRC (captura de realidade misturada) e pode também ser usada por um aplicativo para acessar elementos visuais do mundo real.</span><span class="sxs-lookup"><span data-stu-id="ac07d-105">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="ac07d-106">Renderizar da câmera de PV para MRC</span><span class="sxs-lookup"><span data-stu-id="ac07d-106">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="ac07d-107">Isso requer o **Unreal Engine 4.25** ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ac07d-107">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="ac07d-108">O sistema e os gravadores personalizados de MRC criam capturas de realidade misturada combinando a câmera de PV com hologramas renderizados pelo aplicativo de imersão.</span><span class="sxs-lookup"><span data-stu-id="ac07d-108">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="ac07d-109">Por padrão, a captura de realidade misturada usa a saída holográfica do olho direito.</span><span class="sxs-lookup"><span data-stu-id="ac07d-109">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="ac07d-110">Se um aplicativo de imersão optar por [renderizar da câmera de PV](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), isso será usado em vez do padrão citado acima.</span><span class="sxs-lookup"><span data-stu-id="ac07d-110">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="ac07d-111">Isso melhora o mapeamento entre o mundo real e os hologramas no vídeo do MRC.</span><span class="sxs-lookup"><span data-stu-id="ac07d-111">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="ac07d-112">Para aceitar a renderização da câmera de PV:</span><span class="sxs-lookup"><span data-stu-id="ac07d-112">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="ac07d-113">Chamar **SetEnabledMixedRealityCamera** e **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="ac07d-113">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="ac07d-114">Use os valores de **Tamanho X** e **Tamanho Y** para definir as dimensões do vídeo.</span><span class="sxs-lookup"><span data-stu-id="ac07d-114">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Terceira câmera](images/unreal-camera-3rd.PNG)

<span data-ttu-id="ac07d-116">Em seguida, o Unreal lidará com as solicitações da MRC para renderizar da perspectiva da câmera de PV.</span><span class="sxs-lookup"><span data-stu-id="ac07d-116">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="ac07d-117">Somente quando a [Captura de Realidade Misturada](mixed-reality-capture.md) for disparada, o aplicativo será solicitado a renderizar partindo da perspectiva da câmera de foto/vídeo.</span><span class="sxs-lookup"><span data-stu-id="ac07d-117">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="ac07d-118">Usando a câmera de PV</span><span class="sxs-lookup"><span data-stu-id="ac07d-118">Using the PV Camera</span></span>

<span data-ttu-id="ac07d-119">A textura de webcam pode ser recuperada no jogo em runtime, mas precisa ser habilitada no menu **Editar > Configurações de Projeto** do editor:</span><span class="sxs-lookup"><span data-stu-id="ac07d-119">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="ac07d-120">Acesse **Plataformas > HoloLens > Funcionalidades** e marque **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="ac07d-120">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="ac07d-121">Use a função **StartCameraCapture** para usar a webcam em runtime e a função **StopCameraCapture** para interromper a gravação.</span><span class="sxs-lookup"><span data-stu-id="ac07d-121">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Iniciar/interromper câmera](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="ac07d-123">Renderização de uma imagem</span><span class="sxs-lookup"><span data-stu-id="ac07d-123">Rendering an image</span></span>
<span data-ttu-id="ac07d-124">Para renderizar a imagem da câmera:</span><span class="sxs-lookup"><span data-stu-id="ac07d-124">To render the camera image:</span></span>
1. <span data-ttu-id="ac07d-125">Crie uma instância de material dinâmico com base em um material no projeto, nomeado **PVCamMat** na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="ac07d-125">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="ac07d-126">Defina a instância de material dinâmico para uma variável de **Referência de Objeto Dinâmico da Instância de Material**.</span><span class="sxs-lookup"><span data-stu-id="ac07d-126">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="ac07d-127">Defina o material do objeto na cena que renderizará o feed da câmera para essa nova instância de material dinâmico.</span><span class="sxs-lookup"><span data-stu-id="ac07d-127">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="ac07d-128">Inicie um temporizador que será usado para associar a imagem da câmera ao material.</span><span class="sxs-lookup"><span data-stu-id="ac07d-128">Start a timer that will be used to bind the camera image to the material.</span></span> 

![Renderização da câmera](images/unreal-camera-render.PNG)

4. <span data-ttu-id="ac07d-130">Crie uma função para esse temporizador (neste caso, **MaterialTimer**) e chame **GetARCameraImage** para obter a textura da webcam.</span><span class="sxs-lookup"><span data-stu-id="ac07d-130">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="ac07d-131">Se a textura for válida, defina um parâmetro de textura no sombreador para a imagem.</span><span class="sxs-lookup"><span data-stu-id="ac07d-131">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="ac07d-132">Caso contrário, inicie o temporizador de material novamente.</span><span class="sxs-lookup"><span data-stu-id="ac07d-132">Otherwise, start the material timer again.</span></span> 

![Textura da câmera](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="ac07d-134">Verifique se o material tem um parâmetro correspondente ao nome em **SetTextureParameterValue** que esteja associado a uma entrada de cor.</span><span class="sxs-lookup"><span data-stu-id="ac07d-134">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="ac07d-135">Sem isso, a imagem da câmera não pode ser exibida corretamente.</span><span class="sxs-lookup"><span data-stu-id="ac07d-135">Without this, the camera image can't be properly displayed.</span></span>

![Textura da câmera](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="ac07d-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="ac07d-137">See also</span></span>
* [<span data-ttu-id="ac07d-138">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="ac07d-138">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="ac07d-139">Captura de realidade misturada para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="ac07d-139">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)

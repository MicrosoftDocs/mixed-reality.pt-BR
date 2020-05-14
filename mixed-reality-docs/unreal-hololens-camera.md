---
title: Câmera do HoloLens no Unreal
description: Guia para usar a câmera do HoloLens no Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, camera, 3rd camera, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840115"
---
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="c62f9-104">Câmera do HoloLens no Unreal</span><span class="sxs-lookup"><span data-stu-id="c62f9-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="c62f9-105">Captura de realidade misturada de terceira câmera</span><span class="sxs-lookup"><span data-stu-id="c62f9-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="c62f9-106">A terceira câmera do MRC (Captura de Realidade Misturada) pode ser usada para renderizar uma captura de realidade misturada da perspectiva da câmera no visor do HoloLens em vez da perspectiva das texturas do olho.</span><span class="sxs-lookup"><span data-stu-id="c62f9-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="c62f9-107">Isso melhora o mapeamento entre o mundo real e os hologramas no vídeo do MRC.</span><span class="sxs-lookup"><span data-stu-id="c62f9-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="c62f9-108">Para optar por usar a terceira câmera do MRC, chame SetEnabledMixedRealityCamera e ResizeMixedRealityCamera com as dimensões de vídeo desejadas.</span><span class="sxs-lookup"><span data-stu-id="c62f9-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![Terceira câmera](images/unreal-camera-3rd.PNG)

<span data-ttu-id="c62f9-110">Em seguida, registre um vídeo do MRC no portal do dispositivo do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c62f9-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="c62f9-111">Câmera de PV</span><span class="sxs-lookup"><span data-stu-id="c62f9-111">PV Camera</span></span>

<span data-ttu-id="c62f9-112">A textura da webcam também pode ser recuperada no jogo em runtime.</span><span class="sxs-lookup"><span data-stu-id="c62f9-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="c62f9-113">Para obter a textura da webcam no HoloLens, primeiro a funcionalidade "Webcam" deve estar marcada no editor do Unreal em Configurações do Projeto > Plataforma > HoloLens > Funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="c62f9-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="c62f9-114">Opte por usar a webcam em runtime com a função StartCameraCapture.</span><span class="sxs-lookup"><span data-stu-id="c62f9-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="c62f9-115">Pare a captura com a função StopCameraCapture.</span><span class="sxs-lookup"><span data-stu-id="c62f9-115">Stop capturing with the StopCameraCapture function.</span></span> 

![Iniciar/interromper câmera](images/unreal-camera-startstop.PNG)

<span data-ttu-id="c62f9-117">Para renderizar a imagem da câmera, primeiro crie uma instância de material dinâmica com base em um material no projeto.</span><span class="sxs-lookup"><span data-stu-id="c62f9-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="c62f9-118">Nesse caso, com base em um material chamado PVCamMat.</span><span class="sxs-lookup"><span data-stu-id="c62f9-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="c62f9-119">Defina isso como uma variável com o tipo Referência de Objeto Dinâmico de Instância de Material.</span><span class="sxs-lookup"><span data-stu-id="c62f9-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="c62f9-120">Em seguida, defina o material do objeto na cena que renderizará o feed da câmera para essa nova instância de material dinâmica e inicie um temporizador que será usado para associar a imagem da câmera ao material.</span><span class="sxs-lookup"><span data-stu-id="c62f9-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![Renderização da câmera](images/unreal-camera-render.PNG)

<span data-ttu-id="c62f9-122">Crie uma função para esse temporizador, neste caso, MaterialTimer, e chame GetARCameraImage para obter a textura da webcam.</span><span class="sxs-lookup"><span data-stu-id="c62f9-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="c62f9-123">Se essa textura for válida, defina um parâmetro de textura no sombreador para esta imagem.</span><span class="sxs-lookup"><span data-stu-id="c62f9-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="c62f9-124">Caso contrário, inicie o temporizador de material novamente.</span><span class="sxs-lookup"><span data-stu-id="c62f9-124">Otherwise, start the material timer again.</span></span> 

![Textura da câmera](images/unreal-camera-texture.PNG)

<span data-ttu-id="c62f9-126">O material deve ter um parâmetro correspondente ao nome em SetTextureParameterValue associado a uma entrada de cor para exibir corretamente a imagem da câmera.</span><span class="sxs-lookup"><span data-stu-id="c62f9-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![Textura da câmera](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="c62f9-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="c62f9-128">See also</span></span>
* [<span data-ttu-id="c62f9-129">Câmera localizável</span><span class="sxs-lookup"><span data-stu-id="c62f9-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="c62f9-130">Captura de realidade misturada para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="c62f9-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)

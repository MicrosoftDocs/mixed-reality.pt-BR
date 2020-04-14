---
title: Usando o WebXR com o Windows Mixed Reality
description: Visão geral do uso e desenvolvimento para WebXR no Windows Mixed Reality
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 Content, imersão Web, immersiveweb, IW
ms.openlocfilehash: 01e6cd44e9879cd7fd9b11e178134eaf364cc53c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278437"
---
# <a name="webxr-overview"></a><span data-ttu-id="7d962-104">Visão geral do WebXR</span><span class="sxs-lookup"><span data-stu-id="7d962-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="7d962-105">O que é WebXR</span><span class="sxs-lookup"><span data-stu-id="7d962-105">What is WebXR</span></span>

<span data-ttu-id="7d962-106">A **API do dispositivo WebXR** é para acessar os dispositivos **VR (realidade virtual)** e **ar (realidade aumentada)** , incluindo **sensores** e **exibições montadas no cabeçalho** na **Web**.</span><span class="sxs-lookup"><span data-stu-id="7d962-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="7d962-107">A API do dispositivo WebXR está disponível atualmente no Microsoft Edge, e o Chrome versão 79 e versões posteriores dão suporte a WebXR como padrão.</span><span class="sxs-lookup"><span data-stu-id="7d962-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="7d962-108">Você pode verificar o status de suporte do navegador mais recente para WebXR em [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="7d962-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="7d962-109">Saiba mais sobre a [realidade mista do Windows e o novo Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)na seção [o que há de novo](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) .</span><span class="sxs-lookup"><span data-stu-id="7d962-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="7d962-110">Exibindo WebXR</span><span class="sxs-lookup"><span data-stu-id="7d962-110">Viewing WebXR</span></span>

<span data-ttu-id="7d962-111">Para testar se o navegador dá suporte a WebXR, você pode navegar até [exemplos de WebXR](https://immersive-web.github.io/webxr-samples/) no navegador.</span><span class="sxs-lookup"><span data-stu-id="7d962-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d962-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="7d962-112">See Also</span></span>

* [<span data-ttu-id="7d962-113">Especificação de API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="7d962-113">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="7d962-114">Documentação da API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="7d962-114">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="7d962-115">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="7d962-115">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="7d962-116">Exemplos de WebXR</span><span class="sxs-lookup"><span data-stu-id="7d962-116">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="7d962-117">Realidade mista do Windows e o novo Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7d962-117">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="7d962-118">GitHub W3C da Web de imersão</span><span class="sxs-lookup"><span data-stu-id="7d962-118">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="7d962-119">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d962-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="7d962-120">[API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="7d962-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="7d962-121">Manipulando o contexto perdido no WebGL</span><span class="sxs-lookup"><span data-stu-id="7d962-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="7d962-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="7d962-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="7d962-123">glTF</span><span class="sxs-lookup"><span data-stu-id="7d962-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="7d962-124">Usando Babylon. js para criar experiências de WebXR</span><span class="sxs-lookup"><span data-stu-id="7d962-124">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="7d962-125">Grupo de comunidades da Web de imersão</span><span class="sxs-lookup"><span data-stu-id="7d962-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)

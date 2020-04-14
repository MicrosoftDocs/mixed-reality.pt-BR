---
title: Visão geral do WebVR
description: Visão geral do uso e desenvolvimento para WebVR no Windows Mixed Reality
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 Content, imersiva Web, immersiveweb, IW
ms.openlocfilehash: fdff2acf7816f36129d867650b16d9760a92e375
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278447"
---
# <a name="webvr-overview"></a><span data-ttu-id="2cc6e-104">Visão geral do WebVR</span><span class="sxs-lookup"><span data-stu-id="2cc6e-104">WebVR Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2cc6e-105">As API s do **WebVR 1,1**foram preteridas e substituídas por **APIs de dispositivo do WebXR**s.</span><span class="sxs-lookup"><span data-stu-id="2cc6e-105">**WebVR 1.1 API**s are deprecated and replaced by **WebXR Device API**s.</span></span>

<span data-ttu-id="2cc6e-106">As APIs do WebVR 1,1 são preteridas e removidas do Chrome e do novo Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="2cc6e-106">WebVR 1.1 APIs are deprecated and removed from Chrome and the new Microsoft Edge.</span></span> <span data-ttu-id="2cc6e-107">As APIs WebVR são substituídas por APIs de dispositivo WebXR.</span><span class="sxs-lookup"><span data-stu-id="2cc6e-107">WebVR APIs are superseded by WebXR Device APIs.</span></span> <span data-ttu-id="2cc6e-108">Você pode verificar a lista de navegadores que atualmente dão suporte a APIs WebVR no [caniuse.com](https://caniuse.com/#search=webvr).</span><span class="sxs-lookup"><span data-stu-id="2cc6e-108">You can check the list of browsers currently supporting WebVR APIs on [caniuse.com](https://caniuse.com/#search=webvr).</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="2cc6e-109">Exibindo o conteúdo do WebVR em headsets de imersão de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="2cc6e-109">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="2cc6e-110">As instruções para acessar o conteúdo do WebVR em seus headsets de imersão com **versões mais antigas do Microsoft Edge (15-18)** podem ser encontradas no [Guia do entusiasta](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="2cc6e-110">Instructions for accessing WebVR content in your immersive headsets with **older versions of Microsoft Edge(15-18)** can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span> <span data-ttu-id="2cc6e-111">Você pode verificar sua versão de borda digitando "edge://version/" na barra de pesquisa de navegadores de borda.</span><span class="sxs-lookup"><span data-stu-id="2cc6e-111">You can check your edge version by typing "edge://version/" in your Edge browsers search bar.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cc6e-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="2cc6e-112">See Also</span></span>

* [<span data-ttu-id="2cc6e-113">Visão geral do WebXR</span><span class="sxs-lookup"><span data-stu-id="2cc6e-113">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="2cc6e-114">Especificação de API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="2cc6e-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="2cc6e-115">Realidade mista do Windows e o novo Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2cc6e-115">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge)
* [<span data-ttu-id="2cc6e-116">Informações de WebVR</span><span class="sxs-lookup"><span data-stu-id="2cc6e-116">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="2cc6e-117">Especificação de WebVR</span><span class="sxs-lookup"><span data-stu-id="2cc6e-117">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="2cc6e-118">[API WebVR](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="2cc6e-118">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="2cc6e-119">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="2cc6e-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="2cc6e-120">[API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="2cc6e-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="2cc6e-121">Manipulando o contexto perdido no WebGL</span><span class="sxs-lookup"><span data-stu-id="2cc6e-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="2cc6e-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="2cc6e-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="2cc6e-123">glTF</span><span class="sxs-lookup"><span data-stu-id="2cc6e-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="2cc6e-124">Usando Babylon. js para habilitar o WebVR</span><span class="sxs-lookup"><span data-stu-id="2cc6e-124">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

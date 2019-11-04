---
title: Usando o WebVR no Microsoft Edge com o Windows Mixed Reality
description: Visão geral do uso e desenvolvimento para WebVR no Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 Content, imersiva Web, immersiveweb, IW
ms.openlocfilehash: 87805d2c40e9e63cdf3e432189b9deb7d575a380
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437209"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="c2d95-104">Usando o WebVR no Microsoft Edge com o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c2d95-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="c2d95-105">Criando conteúdo de WebVR para headsets de imersão de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="c2d95-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="c2d95-106">O WebVR 1,1 está disponível no Microsoft Edge, começando com a atualização dos criadores de outono do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c2d95-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="c2d95-107">Os desenvolvedores agora podem usar essa API para criar experiências de VR envolventes na Web.</span><span class="sxs-lookup"><span data-stu-id="c2d95-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="c2d95-108">A API WebVR fornece HMD de dados de pose para a página que pode ser usada para renderizar uma cena WebGL estéreo de volta para o HMD.</span><span class="sxs-lookup"><span data-stu-id="c2d95-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="c2d95-109">Detalhes sobre o suporte à API estão disponíveis na [página status da plataforma Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="c2d95-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="c2d95-110">A área de superfície da API do WebVR está presente em todos os momentos no Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="c2d95-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="c2d95-111">No entanto, uma chamada para getVRDisplays () retornará um headset apenas se um headset estiver conectado ou se o simulador tiver sido ativado.</span><span class="sxs-lookup"><span data-stu-id="c2d95-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="c2d95-112">Exibindo o conteúdo do WebVR em headsets de imersão de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="c2d95-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="c2d95-113">As instruções para acessar o conteúdo do WebVR em seu headset de imersão podem ser encontradas no [Guia do entusiasta](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="c2d95-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2d95-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2d95-114">See Also</span></span>
* [<span data-ttu-id="c2d95-115">Informações de WebVR</span><span class="sxs-lookup"><span data-stu-id="c2d95-115">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="c2d95-116">Especificação de WebVR</span><span class="sxs-lookup"><span data-stu-id="c2d95-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="c2d95-117">[API WebVR](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="c2d95-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="c2d95-118">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="c2d95-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="c2d95-119">[API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="c2d95-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="c2d95-120">Manipulando o contexto perdido no WebGL</span><span class="sxs-lookup"><span data-stu-id="c2d95-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="c2d95-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="c2d95-121">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="c2d95-122">glTF</span><span class="sxs-lookup"><span data-stu-id="c2d95-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="c2d95-123">Usando Babylon. js para habilitar o WebVR</span><span class="sxs-lookup"><span data-stu-id="c2d95-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)


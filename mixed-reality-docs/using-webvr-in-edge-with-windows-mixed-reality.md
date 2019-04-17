---
title: Usando WebVR no Microsoft Edge com o Windows Mixed Reality
description: Visão geral de usar e desenvolver para WebVR na realidade mista do Windows
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, mr de web, web ar, 360, 360 vídeo, 360 vídeos, fotos 360, 360 fotos, conteúdo 360, web envolvente, immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590927"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="f3acc-104">Usando WebVR no Microsoft Edge com o Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f3acc-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="f3acc-105">Criando conteúdo de WebVR para realidade misturada Windows fones imersivos em exposição</span><span class="sxs-lookup"><span data-stu-id="f3acc-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="f3acc-106">WebVR 1.1 está disponível no início do Microsoft Edge com o Windows 10 Fall Creators Update.</span><span class="sxs-lookup"><span data-stu-id="f3acc-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="f3acc-107">Os desenvolvedores agora podem usar essa API para criar experiências de imersão VR na web.</span><span class="sxs-lookup"><span data-stu-id="f3acc-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="f3acc-108">A API de WebVR fornece dados de pose HMD para a página que pode ser usada para renderizar um cena WebGL estéreo volta para o HMD.</span><span class="sxs-lookup"><span data-stu-id="f3acc-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="f3acc-109">Detalhes sobre o suporte de API está disponível na [página de Status de plataforma do Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="f3acc-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="f3acc-110">A área de superfície de API WebVR está presente em todas as vezes dentro do Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="f3acc-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="f3acc-111">No entanto, uma chamada para getVRDisplays() retornará apenas um fone de ouvido se está conectado um headset ou o simulador foi ativado.</span><span class="sxs-lookup"><span data-stu-id="f3acc-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="f3acc-112">Visualizar o conteúdo de WebVR em fones imersivos em exposição realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="f3acc-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="f3acc-113">Instruções para acessar o conteúdo de WebVR seu Headset imersivo podem ser encontradas na [guia aficionado](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="f3acc-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3acc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3acc-114">See Also</span></span>
* [<span data-ttu-id="f3acc-115">Informações de WebVR</span><span class="sxs-lookup"><span data-stu-id="f3acc-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="f3acc-116">Especificação de WebVR</span><span class="sxs-lookup"><span data-stu-id="f3acc-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="f3acc-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="f3acc-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="f3acc-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="f3acc-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="f3acc-119">[API de Gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [Gamepad extensões](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="f3acc-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="f3acc-120">Tratamento de perdeu o contexto no WebGL</span><span class="sxs-lookup"><span data-stu-id="f3acc-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="f3acc-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="f3acc-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="f3acc-122">glTF</span><span class="sxs-lookup"><span data-stu-id="f3acc-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="f3acc-123">Usando o Babylon. js para habilitar WebVR</span><span class="sxs-lookup"><span data-stu-id="f3acc-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)


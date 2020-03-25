---
title: Desempenho do OpenXR
description: Depure o desempenho da GPU de seus aplicativos OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, aplicativo nativo, mecanismo personalizado, middleware, desempenho, otimização, depuração de GPU, RenderDoc, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163340"
---
# <a name="openxr-performance"></a><span data-ttu-id="a9ed7-104">Desempenho do OpenXR</span><span class="sxs-lookup"><span data-stu-id="a9ed7-104">OpenXR performance</span></span>

<span data-ttu-id="a9ed7-105">No HoloLens 2, há várias maneiras de enviar dados de composição por meio de `xrEndFrame`, o que resultará em pós-processamento que terá uma penalidade de desempenho perceptível.</span><span class="sxs-lookup"><span data-stu-id="a9ed7-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>
<span data-ttu-id="a9ed7-106">Para evitar o desempenho penalities, [envie um único `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) com as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="a9ed7-106">To avoid performance penalities, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="a9ed7-107">Usar uma matriz de textura SwapChain</span><span class="sxs-lookup"><span data-stu-id="a9ed7-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="a9ed7-108">Usar o formato SwapChain de cor primária</span><span class="sxs-lookup"><span data-stu-id="a9ed7-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="a9ed7-109">Usar as dimensões de exibição recomendadas</span><span class="sxs-lookup"><span data-stu-id="a9ed7-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="a9ed7-110">Não definir o sinalizador de `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`</span><span class="sxs-lookup"><span data-stu-id="a9ed7-110">Do not set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="a9ed7-111">Defina o `XrCompositionLayerDepthInfoKHR` `minDepth` como 0,0 f e `maxDepth` como 1,0 f</span><span class="sxs-lookup"><span data-stu-id="a9ed7-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="a9ed7-112">Considerações adicionais resultarão em melhor desempenho:</span><span class="sxs-lookup"><span data-stu-id="a9ed7-112">Additional considerations will result in better performance:</span></span>
* [<span data-ttu-id="a9ed7-113">Usar o formato de profundidade de 16 bits</span><span class="sxs-lookup"><span data-stu-id="a9ed7-113">Use the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="a9ed7-114">Fazer chamadas de desenho em instância</span><span class="sxs-lookup"><span data-stu-id="a9ed7-114">Make instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)

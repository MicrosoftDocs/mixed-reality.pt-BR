---
title: Visão geral do JavaScript Mixed Reality Development
description: Visão geral do desenvolvimento de realidade mista usando JavaScript para fones de ouvido de imersão Web, móvel e Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 Content, imersão Web, imersão-Web, IW, immersiveweb
ms.openlocfilehash: 5756af9f48f4bb25477e75fb1f7c09e7239bdab9
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278477"
---
# <a name="mixed-reality-development-with-javascript-overview"></a><span data-ttu-id="4d107-104">Desenvolvimento de realidade mista com visão geral do JavaScript</span><span class="sxs-lookup"><span data-stu-id="4d107-104">Mixed Reality Development with JavaScript Overview</span></span>

## <a name="mixed-reality-applications-on-the-web"></a><span data-ttu-id="4d107-105">Aplicativos de realidade misturada na Web</span><span class="sxs-lookup"><span data-stu-id="4d107-105">Mixed Reality applications on the web</span></span>

<span data-ttu-id="4d107-106">Os recursos de realidade misturada estão disponíveis na Web pelo uso de [APIs de dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) e [APIs preteridas do WebVR] ([visão geral do WebXR](webxr-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4d107-106">Mixed Reality features are available on the web by the use of [WebXR Device APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) and [deprecated WebVR APIs]([WebXR Overview](webxr-overview.md).</span></span> <span data-ttu-id="4d107-107">Para navegadores que não dão suporte a recursos completos do WebXR, você pode adicionar os [suportes retroativos do WebXR](https://github.com/immersive-web/webxr-polyfill) ao seu site.</span><span class="sxs-lookup"><span data-stu-id="4d107-107">For browsers that do not support full WebXR features, you can add [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) to your website.</span></span>

## <a name="what-is-webxr-polyfill"></a><span data-ttu-id="4d107-108">O que é o WebXR retroativo</span><span class="sxs-lookup"><span data-stu-id="4d107-108">What is WebXR Polyfill</span></span>

<span data-ttu-id="4d107-109">Uma implementação de JavaScript da API do dispositivo WebXR, bem como o módulo de gamepad do WebXR.</span><span class="sxs-lookup"><span data-stu-id="4d107-109">A JavaScript implementation of the WebXR Device API, as well as the WebXR Gamepad Module.</span></span> <span data-ttu-id="4d107-110">Este suporte retroativo permite aos desenvolvedores escrever em relação à especificação mais recente, fornecendo suporte quando executados em navegadores que implementam a especificação do WebVR 1,1 ou em dispositivos móveis sem nenhum WebVR/WebXR.</span><span class="sxs-lookup"><span data-stu-id="4d107-110">This polyfill allows developers to write against the latest specification, providing support when run on browsers that implement the WebVR 1.1 spec, or on mobile devices with no WebVR/WebXR support at all.</span></span>

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a><span data-ttu-id="4d107-111">Bibliotecas JavaScript para criar aplicativos de realidade misturada na Web</span><span class="sxs-lookup"><span data-stu-id="4d107-111">JavaScript libraries to build Mixed Reality applications on the web</span></span>

## <a name="babylonjs"></a><span data-ttu-id="4d107-112">Babylon. js</span><span class="sxs-lookup"><span data-stu-id="4d107-112">Babylon.js</span></span>

<span data-ttu-id="4d107-113">O Babylon é um mecanismo 3D de JavaScript que facilita o desenvolvimento de conteúdo 3D e de aplicativos de imersão.</span><span class="sxs-lookup"><span data-stu-id="4d107-113">Babylon is a JavaScript 3D engine that makes developing 3D content and immersive applications easy.</span></span> <span data-ttu-id="4d107-114">Antes de começar a usar aplicativos de imersão, é recomendável aprender os conceitos básicos do desenvolvimento do Babylon. js.</span><span class="sxs-lookup"><span data-stu-id="4d107-114">Before getting started with immersive applications, we recommend to learn the basics of Babylon.js development.</span></span>

<span data-ttu-id="4d107-115">Saiba como criar um aplicativo de realidade misturada com o Babylon na [seção Introdução](https://doc.babylonjs.com/).</span><span class="sxs-lookup"><span data-stu-id="4d107-115">Learn how to build a mixed reality application with Babylon in the [getting started section](https://doc.babylonjs.com/).</span></span> <span data-ttu-id="4d107-116">Jogue com exemplos 3D e seu código-fonte usando [Babylon playground](https://doc.babylonjs.com/examples/).</span><span class="sxs-lookup"><span data-stu-id="4d107-116">Play with 3D examples and their source code using [Babylon Playground](https://doc.babylonjs.com/examples/).</span></span> <span data-ttu-id="4d107-117">Aprofunde-se no desenvolvimento de realidade misturada na [seção WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr) da documentação.</span><span class="sxs-lookup"><span data-stu-id="4d107-117">Dive into mixed reality development on the [WebXR section](https://doc.babylonjs.com/how_to/introduction_to_webxr) of the documentation.</span></span> 

## <a name="a-frame"></a><span data-ttu-id="4d107-118">Um quadro</span><span class="sxs-lookup"><span data-stu-id="4d107-118">A-Frame</span></span>

<span data-ttu-id="4d107-119">Um quadro é uma estrutura de JavaScript declarativa para começar com a realidade virtual na Web.</span><span class="sxs-lookup"><span data-stu-id="4d107-119">A-frame is a declarative JavaScript framework to get started with Virtual Reality in the web.</span></span> <span data-ttu-id="4d107-120">Confira a [documentação de um quadro](https://aframe.io/) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="4d107-120">Check out the [A-Frame documentation](https://aframe.io/) to learn more.</span></span>

## <a name="threejs"></a><span data-ttu-id="4d107-121">Três. js</span><span class="sxs-lookup"><span data-stu-id="4d107-121">Three.js</span></span>

<span data-ttu-id="4d107-122">Três. js é uma biblioteca 3D popular para a criação de experiências de imersão.</span><span class="sxs-lookup"><span data-stu-id="4d107-122">Three.js is a popular 3D library for creating immersive experiences.</span></span> <span data-ttu-id="4d107-123">Saiba mais sobre [três. js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) na página de documentação e explorando [exemplos](https://threejs.org/examples/#webgl_animation_cloth).</span><span class="sxs-lookup"><span data-stu-id="4d107-123">Learn more about [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) in documentation page and by exploring [examples](https://threejs.org/examples/#webgl_animation_cloth).</span></span>

## <a name="webgl"></a><span data-ttu-id="4d107-124">WebGL</span><span class="sxs-lookup"><span data-stu-id="4d107-124">WebGL</span></span>

<span data-ttu-id="4d107-125">Você pode acessar as APIs do dispositivo WebXR diretamente usando APIs do WebGL.</span><span class="sxs-lookup"><span data-stu-id="4d107-125">You can access the WebXR Device APIs directly by using WebGL APIs.</span></span> <span data-ttu-id="4d107-126">WebGL (Web Graphics Library) é uma API de JavaScript para renderizar gráficos interativos 3D e 2D de alto desempenho em qualquer navegador da Web compatível sem o uso de plug-ins. saiba mais sobre as [APIs do WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).</span><span class="sxs-lookup"><span data-stu-id="4d107-126">WebGL (Web Graphics Library) is a JavaScript API for rendering high-performance interactive 3D and 2D graphics within any compatible web browser without the use of plug-ins. Learn more about the [WebGL APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).</span></span>

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a><span data-ttu-id="4d107-127">Aplicativos móveis nativos de realidade misturados usando JavaScript</span><span class="sxs-lookup"><span data-stu-id="4d107-127">Mixed Reality native mobile applications using JavaScript</span></span>

<span data-ttu-id="4d107-128">Com a ajuda de algumas bibliotecas JavaScript, você pode escrever suas experiências de realidade misturadas uma vez e implantá-las na Web e em plataformas nativas, como a realidade mista do Windows headsets, dispositivos Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="4d107-128">With the help of few JavaScript libraries you can write your mixed reality experiences once and deploy it to web and to native platforms like Windows Mixed Reality headsets, Android and iOS devices.</span></span>

## <a name="babylon-native"></a><span data-ttu-id="4d107-129">Babylon nativo</span><span class="sxs-lookup"><span data-stu-id="4d107-129">Babylon Native</span></span>

<span data-ttu-id="4d107-130">A plataforma [nativa Babylon](https://www.babylonjs.com/native/) permite que qualquer pessoa use seu código Babylon. js e crie um aplicativo nativo com ele, desbloqueando o poder das tecnologias nativas.</span><span class="sxs-lookup"><span data-stu-id="4d107-130">[Babylon Native](https://www.babylonjs.com/native/) platform allows anyone to take their Babylon.js code and build a native application with it, unlocking the power of native technologies.</span></span> <span data-ttu-id="4d107-131">Você pode baixar o [Babylon Native no GitHub](https://github.com/BabylonJS/BabylonNative) e ler mais sobre ele no [blog do Babylon. js](https://medium.com/@babylonjs/babylon-native-821f1694fffc).</span><span class="sxs-lookup"><span data-stu-id="4d107-131">You can download [Babylon native on github](https://github.com/BabylonJS/BabylonNative) and read more about it on [Babylon.js blog](https://medium.com/@babylonjs/babylon-native-821f1694fffc).</span></span>

## <a name="react-native"></a><span data-ttu-id="4d107-132">React Native</span><span class="sxs-lookup"><span data-stu-id="4d107-132">React Native</span></span>

<span data-ttu-id="4d107-133">[Reagir nativo](https://reactnative.dev/) é outra biblioteca de software livre que permite aos desenvolvedores criar usando JavaScript e implantar em várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="4d107-133">[React Native](https://reactnative.dev/) is another open source library that allows developers to build using JavaScript and deploy to multiple platforms.</span></span> <span data-ttu-id="4d107-134">Você pode baixar o [reajam nativo no GitHub](https://github.com/facebook/react-native) e saber mais sobre ele em [reagir em blog nativo](https://reactnative.dev/blog/).</span><span class="sxs-lookup"><span data-stu-id="4d107-134">You can download [React Native on Github](https://github.com/facebook/react-native) and learn more about it in [React Native Blog](https://reactnative.dev/blog/).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d107-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="4d107-135">See Also</span></span>

* [<span data-ttu-id="4d107-136">Visão geral do WebXR</span><span class="sxs-lookup"><span data-stu-id="4d107-136">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="4d107-137">Especificação de API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="4d107-137">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="4d107-138">Documentação da API do dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="4d107-138">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="4d107-139">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="4d107-139">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="4d107-140">Exemplos de WebXR</span><span class="sxs-lookup"><span data-stu-id="4d107-140">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="4d107-141">Usando Babylon. js para criar experiências de WebXR</span><span class="sxs-lookup"><span data-stu-id="4d107-141">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="4d107-142">Realidade mista do Windows e o novo Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4d107-142">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="4d107-143">GitHub W3C da Web de imersão</span><span class="sxs-lookup"><span data-stu-id="4d107-143">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="4d107-144">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="4d107-144">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="4d107-145">[API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="4d107-145">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="4d107-146">Visão geral do WebVR</span><span class="sxs-lookup"><span data-stu-id="4d107-146">WebVR Overview</span></span>](webvr-overview.md)

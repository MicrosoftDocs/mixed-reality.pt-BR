---
title: Visão geral do JavaScript Mixed Reality Development
description: Visão geral do desenvolvimento de realidade mista usando JavaScript para fones de ouvido de imersão Web, móvel e Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, Web XR, Web Mr, Web ar, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 fotos, 360 Content, imersão Web, imersão-Web, IW, immersiveweb
ms.openlocfilehash: a1288e8f477f42b0937e797623fb83fe8f63685c
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835605"
---
# <a name="mixed-reality-development-with-javascript-overview"></a>Desenvolvimento de realidade mista com visão geral do JavaScript

## <a name="mixed-reality-applications-on-the-web"></a>Aplicativos de realidade misturada na Web

Os recursos de realidade misturada estão disponíveis na Web pelo uso de [APIs de dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) e [APIs de WebVR preteridas](webxr-overview.md). Para navegadores que não dão suporte a recursos completos do WebXR, você pode adicionar os [suportes retroativos do WebXR](https://github.com/immersive-web/webxr-polyfill) ao seu site.

## <a name="what-is-webxr-polyfill"></a>O que é o WebXR retroativo

Uma implementação de JavaScript da API do dispositivo WebXR, bem como o módulo de gamepad do WebXR. Este suporte retroativo permite aos desenvolvedores escrever em relação à especificação mais recente, fornecendo suporte quando executados em navegadores que implementam a especificação do WebVR 1,1 ou em dispositivos móveis sem nenhum WebVR/WebXR.

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>Bibliotecas JavaScript para criar aplicativos de realidade misturada na Web

## <a name="babylonjs"></a>Babylon. js

O Babylon é um mecanismo 3D de JavaScript que facilita o desenvolvimento de conteúdo 3D e de aplicativos de imersão. Antes de começar a usar aplicativos de imersão, é recomendável aprender os conceitos básicos do desenvolvimento do Babylon. js.

Saiba como criar um aplicativo de realidade misturada com o Babylon na [seção Introdução](https://doc.babylonjs.com/). Jogue com exemplos 3D e seu código-fonte usando [Babylon playground](https://doc.babylonjs.com/examples/). Aprofunde-se no desenvolvimento de realidade misturada na [seção WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr) da documentação. 

## <a name="a-frame"></a>Um quadro

Um quadro é uma estrutura de JavaScript declarativa para começar com a realidade virtual na Web. Confira a [documentação de um quadro](https://aframe.io/) para saber mais.

## <a name="threejs"></a>Três. js

Três. js é uma biblioteca 3D popular para a criação de experiências de imersão. Saiba mais sobre [três. js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) na página de documentação e explorando [exemplos](https://threejs.org/examples/#webgl_animation_cloth).

## <a name="webgl"></a>WebGL

Você pode acessar as APIs do dispositivo WebXR diretamente usando APIs do WebGL. WebGL (Web Graphics Library) é uma API de JavaScript para renderizar gráficos interativos 3D e 2D de alto desempenho em qualquer navegador da Web compatível sem o uso de plug-ins. saiba mais sobre as [APIs do WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>Aplicativos móveis nativos de realidade misturados usando JavaScript

Com a ajuda de algumas bibliotecas JavaScript, você pode escrever suas experiências de realidade misturadas uma vez e implantá-las na Web e em plataformas nativas, como a realidade mista do Windows headsets, dispositivos Android e iOS.

## <a name="babylon-native"></a>Babylon nativo

A plataforma [nativa Babylon](https://www.babylonjs.com/native/) permite que qualquer pessoa use seu código Babylon. js e crie um aplicativo nativo com ele, desbloqueando o poder das tecnologias nativas. Você pode baixar o [Babylon Native no GitHub](https://github.com/BabylonJS/BabylonNative) e ler mais sobre ele no [blog do Babylon. js](https://medium.com/@babylonjs/babylon-native-821f1694fffc).

## <a name="react-native"></a>React Native

[Reagir nativo](https://reactnative.dev/) é outra biblioteca de software livre que permite aos desenvolvedores criar usando JavaScript e implantar em várias plataformas. Você pode baixar o [reajam nativo no GitHub](https://github.com/facebook/react-native) e saber mais sobre ele em [reagir em blog nativo](https://reactnative.dev/blog/).

## <a name="see-also"></a>Consulte Também

* [Visão geral do WebXR](webxr-overview.md)
* [Especificação de API do dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentação da API do dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb. dev](https://immersiveweb.dev/)
* [Exemplos de WebXR](https://immersive-web.github.io/webxr-samples/)
* [Usando Babylon. js para criar experiências de WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Realidade mista do Windows e o novo Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [GitHub W3C da Web de imersão](https://github.com/immersive-web)
* [API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Visão geral do WebVR](webvr-overview.md)

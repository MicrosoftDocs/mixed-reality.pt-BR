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
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Usando o WebVR no Microsoft Edge com o Windows Mixed Reality

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Criando conteúdo de WebVR para headsets de imersão de realidade mista do Windows

O WebVR 1,1 está disponível no Microsoft Edge, começando com a atualização dos criadores de outono do Windows 10. Os desenvolvedores agora podem usar essa API para criar experiências de VR envolventes na Web.

A API WebVR fornece HMD de dados de pose para a página que pode ser usada para renderizar uma cena WebGL estéreo de volta para o HMD. Detalhes sobre o suporte à API estão disponíveis na [página status da plataforma Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/). A área de superfície da API do WebVR está presente em todos os momentos no Microsoft Edge. No entanto, uma chamada para getVRDisplays () retornará um headset apenas se um headset estiver conectado ou se o simulador tiver sido ativado.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Exibindo o conteúdo do WebVR em headsets de imersão de realidade mista do Windows

As instruções para acessar o conteúdo do WebVR em seu headset de imersão podem ser encontradas no [Guia do entusiasta](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).

## <a name="see-also"></a>Consulte também
* [Informações de WebVR](https://webvr.info)
* [Especificação de WebVR](https://w3c.github.io/webvr/)
* [API WebVR](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [API de gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [extensões de gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Manipulando o contexto perdido no WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Usando Babylon. js para habilitar o WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)


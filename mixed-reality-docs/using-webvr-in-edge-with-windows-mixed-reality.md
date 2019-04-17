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
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Usando WebVR no Microsoft Edge com o Windows Mixed Reality

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Criando conteúdo de WebVR para realidade misturada Windows fones imersivos em exposição

WebVR 1.1 está disponível no início do Microsoft Edge com o Windows 10 Fall Creators Update. Os desenvolvedores agora podem usar essa API para criar experiências de imersão VR na web.

A API de WebVR fornece dados de pose HMD para a página que pode ser usada para renderizar um cena WebGL estéreo volta para o HMD. Detalhes sobre o suporte de API está disponível na [página de Status de plataforma do Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/). A área de superfície de API WebVR está presente em todas as vezes dentro do Microsoft Edge. No entanto, uma chamada para getVRDisplays() retornará apenas um fone de ouvido se está conectado um headset ou o simulador foi ativado.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Visualizar o conteúdo de WebVR em fones imersivos em exposição realidade mista do Windows

Instruções para acessar o conteúdo de WebVR seu Headset imersivo podem ser encontradas na [guia aficionado](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).

## <a name="see-also"></a>Consulte também
* [Informações de WebVR](http://webvr.info)
* [Especificação de WebVR](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [API de Gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e [Gamepad extensões](https://w3c.github.io/gamepad/extensions.html)
* [Tratamento de perdeu o contexto no WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Usando o Babylon. js para habilitar WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)


---
title: Modo de reprodução do Unity
description: Usando o modo de reprodução no editor do Unity para visualizar as alterações em um dispositivo sem implantar um aplicativo.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicação remota, comunicação remota Holographic, player de comunicação remota Holographic
ms.openlocfilehash: dca7ffba1270802fcabed8a88fe7428ef2981553
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277554"
---
# <a name="unity-play-mode"></a>Modo de reprodução do Unity

Uma maneira rápida de trabalhar em seu projeto de Unity é usar o "modo de reprodução". Isso executa seu aplicativo localmente no editor do Unity em seu computador. O Unity usa a comunicação remota do Holographic para fornecer uma maneira rápida de visualizar o conteúdo em um dispositivo de HoloLens real. O modo de reprodução também pode ser usado com um headset de realidade mista do Windows anexado ao seu PC de desenvolvimento.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reprodução do Unity com comunicação remota do Holographic

Com a comunicação remota do Holographic, você pode experimentar seu aplicativo no HoloLens, enquanto ele é executado no editor do Unity em seu computador. Olhar, gesto, voz e entrada de mapeamento espacial são enviados do seu HoloLens para o seu PC. Os quadros renderizados são enviados de volta ao seu HoloLens. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo.
1. No seu HoloLens, vá para a **Microsoft Store** e instale o aplicativo de **[player de comunicação remota do Holographic](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
2. No seu HoloLens, inicie o aplicativo do **player de comunicação remota do Holographic** .
3. No Unity, vá para o menu **janela** e selecione **emulação Holographic**.
4. Defina o **modo de emulação** como **remoto para dispositivo**.
5. Para **computador remoto**, insira o endereço IP do seu HoloLens.
6. Clique em **Conectar**. Você deve ver o **status da conexão** alterado para **conectado** e ver a tela ficar em branco no HoloLens.
7. Clique no botão **reproduzir** para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens.

A comunicação remota do Holographic exige um PC rápido e uma conexão Wi-Fi. Consulte [Holographic Remoting Player](holographic-remoting-player.md) para obter detalhes completos.

Para obter melhores resultados, verifique se seu aplicativo define corretamente o [ponto de foco](focus-point-in-unity.md). Isso ajuda a Holographic a comunicação remota a melhor adaptação à sua cena com a latência de sua conexão sem fio.

## <a name="see-also"></a>Veja também
* [Player de Comunicação Remota Holográfica](holographic-remoting-player.md)

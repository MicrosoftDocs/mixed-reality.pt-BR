---
title: Modo de jogo do Unity
description: Usando o modo de reprodução no editor do Unity para visualizar as alterações em um dispositivo sem implantar um aplicativo.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicação remota, comunicação remota holográfica, player holográfica remoting
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589137"
---
# <a name="unity-play-mode"></a>Modo de jogo do Unity

Uma maneira rápida de trabalhar em seu projeto do Unity é usar o "Modo de reprodução". Isso executa seu aplicativo localmente no editor do Unity em seu computador. O Unity usa comunicação remota holográfica para fornecer uma maneira rápida de visualizar o conteúdo em um dispositivo real do HoloLens.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de jogo do Unity com a comunicação remota holográfica

Com a comunicação remota holográfica, você pode experimentar seu aplicativo em HoloLens, enquanto ele é executado no editor do Unity em seu computador. Olhar, gesto, voz e mapeamento espacial de entrada é enviada do seu HoloLens a seu computador. Quadros renderizados, em seguida, são enviados para o HoloLens. Isso é uma ótima maneira de depurar rapidamente seu aplicativo sem compilar e implantar um projeto completo.
1. Em seu HoloLens, vá para o **Microsoft Store** e instale o **[holográfica Player de comunicação remota](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** aplicativo.
2. No seu HoloLens, inicie o **holográfica Player de comunicação remota** aplicativo.
3. No Unity, vá para o **janela** menu e selecione **emulação holográfica**.
4. Definir **modo de emulação** à **remoto ao dispositivo**.
5. Para **máquina remota**, insira o endereço IP do seu HoloLens.
6. Clique em **Conectar**. Você deve ver **Status de Conexão** alterar para **conectado** e ver a tela ficar em branco no HoloLens.
7. Clique o **reproduzir** botão para iniciar o modo de reprodução e experimentar o aplicativo em seu HoloLens.

Comunicação remota holográfica requer uma conexão rápida de PC e Wi-Fi. Ver [holográfica Player de comunicação remota](holographic-remoting-player.md) para obter detalhes completos.

Para obter melhores resultados, verifique se seu aplicativo corretamente define o [focar ponto](focus-point-in-unity.md). Isso ajuda a comunicação remota holográfica melhor adaptar sua cena para a latência de sua conexão sem fio.

## <a name="see-also"></a>Consulte também
* [Comunicação remota holográfica Player](holographic-remoting-player.md)

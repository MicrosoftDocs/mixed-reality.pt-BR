---
title: Comunicação remota holográfica Player
description: O Player holográfica de comunicação remota é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota holográfica. Remoting holográfica transmite holográfico conteúdo de um PC para o Microsoft HoloLens em tempo real, usando uma conexão Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Comunicação remota do HoloLens, comunicação remota, Holographic
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591000"
---
# <a name="holographic-remoting-player"></a>Comunicação remota holográfica Player

O Player holográfica de comunicação remota é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota holográfica. Remoting holográfica transmite holográfico conteúdo de um PC para o Microsoft HoloLens em tempo real, usando uma conexão Wi-Fi.

O Player de comunicação remota holográfica só pode ser usado com aplicativos de PC projetados especificamente para dar suporte à comunicação remota holográfica.

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

## <a name="connecting-to-the-holographic-remoting-player"></a>Conectar-se para o Player de comunicação remota holográfica

Siga as instruções do seu aplicativo para se conectar ao Player de comunicação remota holográfica. Você precisará inserir o endereço IP do dispositivo HoloLens, o que você pode ver na tela principal de comunicação remota do Player da seguinte maneira:

![Comunicação remota holográfica Player](images/holographicremotingplayer.png)

Sempre que você vir a tela principal, você saberá que você não tem um aplicativo conectado.

Observe que a conexão de comunicação remota holographic **não criptografado**. Você sempre deve usar a comunicação remota holográfica ao longo de uma conexão segura de Wi-Fi que você confia.

## <a name="quality-and-performance"></a>Desempenho e qualidade

A qualidade e o desempenho de sua experiência variará com base em três fatores:
* **A experiência holográfica estiver executando** -aplicativos que processam conteúdo de alta resolução ou altamente detalhadas podem exigir um PC mais rápido ou mais rapidamente a conexão sem fio.
* **O hardware do computador** -seu PC precisa ser capaz de executar e codificar sua experiência holográfica 60 quadros por segundo. Para uma placa gráfica, geralmente recomendamos um GeForce GTX 970 ou AMD Radeon R9 290 ou melhor. Novamente, sua experiência específica pode exigir um cartão mais alto ou low-end.
* **Sua conexão Wi-Fi** -sua experiência holográfica é transmitida por Wi-Fi. Use uma rede rápida com o congestionamento de baixo para melhorar a qualidade. Usando um computador que está conectado por um cabo Ethernet, em vez de Wi-Fi, poderá também melhorar a qualidade.

## <a name="diagnostics"></a>Diagnóstico

Para medir a qualidade da sua conexão, digamos **"Ativar diagnóstico"** enquanto na tela principal do Player holográfica comunicação remota. Quando os diagnósticos são habilitados, o aplicativo mostrará a você:
* **FPS** – o número médio de quadros renderizados o player de comunicação remota está recebendo e renderização por segundo. O ideal é de 60 FPS.
* **Latência** -a quantidade média de tempo que leva para um quadro ir do seu computador para o HoloLens. Quanto menor, melhor. Isso é altamente dependente em sua rede Wi-Fi.

Enquanto estiver na tela principal, você pode dizer **"desabilitar o diagnóstico"** para desativar o diagnóstico.

## <a name="pc-system-requirements"></a>Requisitos do sistema de PC
* Seu PC **deve** estar executando a atualização de aniversário do Windows 10.
* É recomendável um GeForce GTX 970 ou AMD Radeon R9 290 ou placa de vídeo melhor.
* É recomendável que você conecte seu PC à sua rede por meio de ethernet para reduzir o número de saltos de sem fio.

## <a name="see-also"></a>Consulte também
* [Termos de licença de software de comunicação remota holográfica](microsoft-holographic-remoting-software-license-terms.md)
* [Declaração de privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

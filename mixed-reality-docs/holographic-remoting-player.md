---
title: Player de comunicação remota do Holographic
description: O Holographic Remoting Player é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota do Holographic. O Holographicing Remoting transmite o conteúdo do Holographic de um PC para o Microsoft HoloLens em tempo real, usando uma conexão Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, comunicação remota e comunicação remota Holographic
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813713"
---
# <a name="holographic-remoting-player"></a>Player de comunicação remota do Holographic

O Holographic Remoting Player é um aplicativo complementar que se conecta a aplicativos de PC e jogos que dão suporte à comunicação remota do Holographic. O Holographicing Remoting transmite o conteúdo do Holographic de um PC para o Microsoft HoloLens em tempo real, usando uma conexão Wi-Fi.

O player de comunicação remota do Holographic só pode ser usado com aplicativos de PC projetados especificamente para dar suporte à comunicação remota do Holographic.

O player de comunicação remota do Holographic está disponível para o HoloLens e o HoloLens 2.  Aplicativos de PC com suporte para comunicação remota Holographic com o HoloLens precisam ser atualizados para dar suporte a Holographic Remtoing com o HoloLens 2.  Entre em contato com seu provedor de aplicativos se tiver dúvidas sobre quais versões têm suporte.

## <a name="connecting-to-the-holographic-remoting-player"></a>Conectando-se ao Player de comunicação remota do Holographic

Siga as instruções do aplicativo para se conectar ao Player de comunicação remota do Holographic. Você precisará inserir o endereço IP do seu dispositivo de HoloLens, que pode ser visto na tela principal do reprodutor de comunicação remota da seguinte maneira:

![Player de comunicação remota do Holographic](images/holographicremotingplayer.png)

Sempre que vir a tela principal, você saberá que não tem um aplicativo conectado.

Observe que a conexão remota Holographic **não**está criptografada. Você sempre deve usar a comunicação remota do Holographic em uma conexão Wi-Fi segura na qual você confia.

## <a name="quality-and-performance"></a>Qualidade e desempenho

A qualidade e o desempenho da sua experiência variam com base em três fatores:
* **A experiência do Holographic que você está executando** -aplicativos que processam alta resolução ou conteúdo altamente detalhado pode exigir um PC mais rápido ou uma conexão sem fio mais rápida.
* **Hardware do seu PC** -seu PC precisa ser capaz de executar e codificar sua experiência com o holographic em 60 quadros por segundo. Para uma placa gráfica, geralmente recomendamos um GeForce GTX 970 ou o AMD Radeon R9 290 ou superior. Novamente, sua experiência específica pode exigir um cartão maior ou menor.
* **Sua conexão Wi-Fi** -sua experiência com o Holographic é transmitida por Wi-Fi. Use uma rede rápida com baixo congestionamento para maximizar a qualidade. Usar um computador conectado por um cabo Ethernet, em vez de Wi-Fi, também pode melhorar a qualidade.

## <a name="diagnostics"></a>Diagnóstico

Para medir a qualidade de sua conexão, diga **"habilitar o diagnóstico"** enquanto estiver na tela principal do Holographic Remoting Player. Quando o diagnóstico estiver habilitado, o aplicativo mostrará:
* **FPS** -o número médio de quadros renderizados que o player de comunicação remota está recebendo e renderizando por segundo. O ideal é de 60 FPS.
* **Latência** -a quantidade média de tempo que leva para um quadro passar do seu PC para o HoloLens. Quanto menor for o melhor. Isso é amplamente dependente de sua rede Wi-Fi.

Na tela principal, você pode dizer **"desabilitar o diagnóstico"** para desativar o diagnóstico.

## <a name="pc-system-requirements"></a>Requisitos do sistema do PC
* Seu computador **deve** estar executando a atualização de aniversário do Windows 10 ou mais recente.
* Recomendamos uma placa gráfica GeForce GTX 970 ou AMD Radeon R9 290 ou superior.
* Recomendamos que você conecte seu PC à sua rede por meio de Ethernet para reduzir o número de saltos sem fio.

## <a name="see-also"></a>Consulte também
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

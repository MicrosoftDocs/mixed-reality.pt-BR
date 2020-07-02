---
title: Streaming no Unreal
description: Um guia de streaming no Unreal para o HoloLens 2
author: suwu
ms.author: suwu
ms.date: 6/8/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, streaming, computador, comunicação remota de aplicativo holográfico, Holographic Remoting Player, documentação
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 78a019f5b74b254c1f32ec85dc639df47648555f
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84888907"
---
# <a name="streaming-in-unreal"></a>Streaming no Unreal

## <a name="overview"></a>Visão geral
O streaming de um computador para o HoloLens fornece duas vantagens principais: 
* Ele permite que o aplicativo de realidade misturada aproveite a capacidade computacional dos seus computadores. 
* Ele ajuda a acelerar o tempo de iteração do desenvolvimento. 

Para começar, baixe o [Holographic Remoting Player](holographic-remoting-player.md) no seu dispositivo HoloLens. Isso permite que o seu aplicativo seja transmitido diretamente para o player de comunicação remota no HoloLens das seguintes fontes:

* O editor do Unreal Engine
* Um executável empacotado do Windows 

Durante o streaming, você tem acesso a quase todas as mesmas funcionalidades do HoloLens que teria ao executar um aplicativo em um dispositivo. Isso inclui o [rastreamento da articulação da mão](unreal-hand-tracking.md) (se você estiver usando um HoloLens 2), o [mapeamento espacial](unreal-spatial-mapping.md) e as [âncoras espaciais](unreal-spatial-anchors.md), mas exclui os recursos desta [lista de limitações](holographic-remoting-troubleshooting.md). 

> [!NOTE]
> A qualidade de streaming é altamente dependente da força da rede Wi-Fi.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Origem</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1ª geração</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Headsets imersivos</strong></td>
    </tr>
     <tr>
        <td>Editor do Unreal</td>
        <td>✔</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Pacote do Windows</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Streaming do editor do Unreal

Como desenvolvedor, você descobrirá que o streaming do editor do Unreal para o dispositivo HoloLens fornece grandes benefícios durante o teste, ou seja, você não precisa mais esperar que o aplicativo seja compilado e implantado antes de experimentar as atualizações.

Encontre instruções detalhadas em [Streaming do editor do Unreal](unreal-uxt-ch6.md#device-only-streaming) na última seção da Introdução com as séries de tutoriais do Unreal.

## <a name="streaming-from-a-packaged-windows-executable"></a>Streaming de um executável empacotado do Windows

No Unreal 4.25.1 em diante, você pode transmitir seu aplicativo para um dispositivo HoloLens 2 de um executável empacotado do Windows seguindo as etapas abaixo: 

1. Acesse **Arquivo > Projeto de Pacote > Windows** no menu do editor. 
    * Escolha uma localização para salvar o pacote e clique em **Selecionar Pasta**.

2. Depois que o pacote terminar de ser compilado, abra o **Holographic Remoting Player** no HoloLens 2 e anote o endereço IP. 
3. Deixe o **Holographic Remoting Player** aberto e use o prompt de linha de comando para: 
    * Executar cd no diretório local em que você salvou o pacote.
    * Digite o seguinte comando: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```

> [!NOTE]
> O nome do aplicativo nas configurações do projeto deverá ser usado automaticamente para criar o pacote do Windows. Se ele for diferente por algum motivo, use o nome do executável do Windows no prompt de comando.

Pressione ENTER e veja seu aplicativo começar a ser transmitido.

## <a name="see-also"></a>Veja também
* [Histórico de versões do Holographic Remoting](holographic-remoting-version-history.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](holographic-remoting-secure-connection.md)

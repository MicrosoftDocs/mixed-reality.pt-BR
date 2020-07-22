---
layout: LandingPage
title: Serviços de nuvem de realidade misturada
description: Recursos de serviços de nuvem de realidade misturada.
author: hferrone
ms.author: v-haferr
ms.date: 06/5/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Realidade Misturada, desenvolver, desenvolvimento, HoloLens, serviços de nuvem
ms.openlocfilehash: 80b0b802222684c1219987b197e4219eca8bfc56
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86451349"
---
# <a name="cloud-services"></a>Serviços de nuvem

## <a name="overview"></a>Visão geral

Serviços de nuvem de Realidade Misturada como **Azure Remote Rendering** e **Âncoras Espaciais do Azure** ajudam os desenvolvedores a criar experiências de imersão atraentes em uma variedade de plataformas. Esses serviços permitem que você integre o reconhecimento espacial aos seus projetos quando você cria aplicativos para treinamento 3D, manutenção preditiva do equipamento e revisão de design, tudo no contexto dos ambientes dos seus usuários.

Além disso, há outros serviços do Azure que você pode adicionar facilmente aos seus projetos existentes que não se enquadram no âmbito da Realidade Misturada. Se você está desenvolvendo para o Unity, temos uma ampla variedade de [tutoriais](#standalone-services) listada na parte inferior desta página para ajudar você a começar.

## <a name="mixed-reality-services"></a>Serviços de realidade misturada

### <a name="azure-remote-rendering"></a>Azure Remote Rendering
O ARR ([Azure Remote Rendering](https://docs.microsoft.com/azure/remote-rendering)) é um serviço que permite renderizar modelos 3D altamente complexos quase em tempo real. O ARR está em versão prévia pública no momento. Ele pode ser adicionado aos seus projetos C++ do Unity ou do Native direcionados ao HoloLens 2 ou ao computador desktop Windows.

![Exemplo do Azure Remote Rendering no aplicativo de demonstração do Unity](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Âncoras Espaciais do Azure
As [ASA](https://docs.microsoft.com/azure/spatial-anchors) (Âncoras Espaciais do Azure) são um serviço multiplataforma que permite criar aplicativos de realidade misturada com reconhecimento espacial. Com as Âncoras Espaciais do Azure, você pode mapear, persistir e compartilhar conteúdo holográfico entre vários dispositivos em escala do mundo real. 

![Exemplo de Âncoras Espaciais do Azure](images/persistence.gif)

O serviço pode ser desenvolvido em um host de ambientes e implantado em um grande grupo de dispositivos e plataformas. Isso lhes dá isenção especial para a própria lista de plataformas disponíveis:
* Unity para HoloLens
* Unity para iOS
* Unity para Android
* iOS nativo
* Android nativo
* C++/WinRT e DirectX para HoloLens
* Xamarin para iOS
* Xamarin para Android

## <a name="standalone-services"></a>Serviços autônomos
Os serviços autônomos listados abaixo não se aplicam à Realidade Misturada, mas podem ser úteis em uma ampla variedade de contextos de desenvolvimento. Se você estiver desenvolvendo no Unity, cada um desses serviços poderá ser integrado a seus projetos novos ou existentes.

### <a name="device-support"></a>Suporte a dispositivos
<table>
    <tr>
        <td><strong>Serviço de Nuvem do Azure</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens 1ª geração</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td><a href="mr-azure-301.md">Tradução de idioma</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302.md">Pesquisa Visual Computacional</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302b.md">Visão Personalizada</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-303.md">Notificações entre dispositivos</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-304.md">Reconhecimento facial</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-305.md">Funções e armazenamento</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-306.md">Streaming de vídeo</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-307.md">Aprendizado de máquina</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-308.md">Funções e armazenamento</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-309.md">Application Insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-310.md">Detecção de objetos</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-312.md">Integração de bots</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>
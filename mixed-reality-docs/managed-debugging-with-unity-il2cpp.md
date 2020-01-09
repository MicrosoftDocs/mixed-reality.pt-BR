---
title: Depuração gerenciada com o Unity IL2CPP
description: Este artigo aborda como executar um depurador gerenciado em seu projeto do IL2CPP UWP do Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, depuração, il2cpp
ms.openlocfilehash: 970d3000df995e7c6e331a41d10e25dc5aa370a8
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502657"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Depuração gerenciada com o Unity IL2CPP

Siga estas etapas para anexar um depurador gerenciado à sua compilação do IL2CPP UWP do Unity. Este guia foi desenvolvido originalmente para o HoloLens e o HoloLens 2.

1. Você precisará estar em uma rede que dê suporte a [multicast](https://en.wikipedia.org/wiki/Multicast).
1. Certifique-se de que **InternetClientServer** e **PrivateNetworkClientServer** sejam verificados no Unity nas funcionalidades de configurações de publicação do UWP.

    ![Funcionalidades de configurações de publicação do UWP](images/il2cpp-debugging-capabilities.png)

1. Defina as configurações de Build do Unity UWP:
    - Build de desenvolvimento
    - Depuração de scripts
    - Aguardar o depurador gerenciado (opcional)

    ![Configurações de Build do UWP](images/il2cpp-debugging-build.png)

1. Compilar no Unity.
1. Crie e implante a partir da solução do Visual Studio para seu dispositivo. Você deve criar com as configurações de **depuração** ou de **versão** . A configuração **mestra** desabilita o Unity Profiler e pode impedir a depuração ideal. Opcionalmente, verifique a **Internet (cliente & Server)** e as **redes privadas (cliente & Server)** na lista de recursos em Package. appxmanifest na solução.
1. Inicie o aplicativo em seu dispositivo. Verifique se o dispositivo está conectado à mesma rede que o seu PC.
1. Verifique se o dispositivo **não está** conectado ao seu PC via USB.
1. Vá para a solução do Visual Studio que é criada quando você clica duas vezes em um script no Unity, no qual você pode exibir C# e editar seus scripts.
1. Debug-> anexar o depurador Unity.

    ![Anexar depurador do Unity](images/il2cpp-debugging-attach.png)

1. Selecione seu dispositivo na lista e clique em "OK" para anexar.

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)

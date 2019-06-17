---
title: Depuração com o Unity IL2CPP gerenciada
description: Este artigo aborda como executar um depurador gerenciado no seu projeto do Unity IL2CPP UWP.
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: Unity, visual studio, depuração, il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148851"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Depuração com o Unity IL2CPP gerenciada

Siga estas etapas para anexar um depurador gerenciado ao seu build do Unity IL2CPP UWP. Este guia foi desenvolvido originalmente para HoloLens e HoloLens 2.

1. Certifique-se de que **InternetClientServer** e **PrivateNetworkClientServer** são verificadas no Unity sob os recursos de configurações de publicação do UWP.

    ![Recursos de configurações de publicação de UWP](images/il2cpp-debugging-capabilities.png)

1. Defina as configurações de build de UWP do Unity:
    - Compilação de desenvolvimento
    - Depuração de scripts
    - Aguarde o depurador gerenciado (opcional)

    ![Configurações de Build UWP](images/il2cpp-debugging-build.png)

1. Compile no Unity.
1. Compile e implante de solução do Visual Studio em seu dispositivo. Você deve compilar com o **Debug** ou **versão** configurações. O **mestre** configuração desabilita o criador de perfil do Unity e pode evitar a depuração ideal. Opcionalmente, verifique se **Internet (cliente e servidor)** e **redes privadas (cliente e servidor)** na lista de recursos no Package. appxmanifest na solução.
1. Inicie o aplicativo em seu dispositivo. Verifique se que seu dispositivo está conectado à rede mesma que seu computador.
1. Verifique se o dispositivo **não é** conectado ao computador via USB.
1. Vá para a solução do Visual Studio que é criada quando você clique duas vezes em um script no Unity, onde você pode exibir e editar seu C# scripts.
1. Depurar -> Anexar depurador do Unity.

    ![Anexar o depurador do Unity](images/il2cpp-debugging-attach.png)

1. Selecione seu dispositivo na lista e clique em "Okey" para anexar.

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)

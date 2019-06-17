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
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="072b0-104">Depuração com o Unity IL2CPP gerenciada</span><span class="sxs-lookup"><span data-stu-id="072b0-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="072b0-105">Siga estas etapas para anexar um depurador gerenciado ao seu build do Unity IL2CPP UWP.</span><span class="sxs-lookup"><span data-stu-id="072b0-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="072b0-106">Este guia foi desenvolvido originalmente para HoloLens e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="072b0-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="072b0-107">Certifique-se de que **InternetClientServer** e **PrivateNetworkClientServer** são verificadas no Unity sob os recursos de configurações de publicação do UWP.</span><span class="sxs-lookup"><span data-stu-id="072b0-107">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Recursos de configurações de publicação de UWP](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="072b0-109">Defina as configurações de build de UWP do Unity:</span><span class="sxs-lookup"><span data-stu-id="072b0-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="072b0-110">Compilação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="072b0-110">Development Build</span></span>
    - <span data-ttu-id="072b0-111">Depuração de scripts</span><span class="sxs-lookup"><span data-stu-id="072b0-111">Script Debugging</span></span>
    - <span data-ttu-id="072b0-112">Aguarde o depurador gerenciado (opcional)</span><span class="sxs-lookup"><span data-stu-id="072b0-112">Wait for Managed Debugger (optional)</span></span>

    ![Configurações de Build UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="072b0-114">Compile no Unity.</span><span class="sxs-lookup"><span data-stu-id="072b0-114">Build in Unity.</span></span>
1. <span data-ttu-id="072b0-115">Compile e implante de solução do Visual Studio em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="072b0-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="072b0-116">Você deve compilar com o **Debug** ou **versão** configurações.</span><span class="sxs-lookup"><span data-stu-id="072b0-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="072b0-117">O **mestre** configuração desabilita o criador de perfil do Unity e pode evitar a depuração ideal.</span><span class="sxs-lookup"><span data-stu-id="072b0-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="072b0-118">Opcionalmente, verifique se **Internet (cliente e servidor)** e **redes privadas (cliente e servidor)** na lista de recursos no Package. appxmanifest na solução.</span><span class="sxs-lookup"><span data-stu-id="072b0-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="072b0-119">Inicie o aplicativo em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="072b0-119">Start the app on your device.</span></span> <span data-ttu-id="072b0-120">Verifique se que seu dispositivo está conectado à rede mesma que seu computador.</span><span class="sxs-lookup"><span data-stu-id="072b0-120">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="072b0-121">Verifique se o dispositivo **não é** conectado ao computador via USB.</span><span class="sxs-lookup"><span data-stu-id="072b0-121">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="072b0-122">Vá para a solução do Visual Studio que é criada quando você clique duas vezes em um script no Unity, onde você pode exibir e editar seu C# scripts.</span><span class="sxs-lookup"><span data-stu-id="072b0-122">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="072b0-123">Depurar -> Anexar depurador do Unity.</span><span class="sxs-lookup"><span data-stu-id="072b0-123">Debug -> Attach Unity Debugger.</span></span>

    ![Anexar o depurador do Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="072b0-125">Selecione seu dispositivo na lista e clique em "Okey" para anexar.</span><span class="sxs-lookup"><span data-stu-id="072b0-125">Select your device in the list and click "OK" to attach.</span></span>

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)

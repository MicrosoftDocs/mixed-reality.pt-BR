---
title: Depuração gerenciada com o Unity IL2CPP
description: Este artigo aborda como executar um depurador gerenciado em seu projeto do IL2CPP UWP do Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, depuração, il2cpp
ms.openlocfilehash: fd09c3ca1bd410c56e46eb8e8815742f87482d08
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439627"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="4d150-104">Depuração gerenciada com o Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="4d150-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="4d150-105">Siga estas etapas para anexar um depurador gerenciado à sua compilação do IL2CPP UWP do Unity.</span><span class="sxs-lookup"><span data-stu-id="4d150-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="4d150-106">Este guia foi desenvolvido originalmente para o HoloLens e o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4d150-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="4d150-107">Você precisará estar em uma rede que dê suporte a [multicast](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="4d150-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="4d150-108">Certifique-se de que **InternetClientServer** e **PrivateNetworkClientServer** sejam verificados no Unity nas funcionalidades de configurações de publicação do UWP.</span><span class="sxs-lookup"><span data-stu-id="4d150-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Funcionalidades de configurações de publicação do UWP](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="4d150-110">Defina as configurações de Build do Unity UWP:</span><span class="sxs-lookup"><span data-stu-id="4d150-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="4d150-111">Build de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="4d150-111">Development Build</span></span>
    - <span data-ttu-id="4d150-112">Depuração de scripts</span><span class="sxs-lookup"><span data-stu-id="4d150-112">Script Debugging</span></span>
    - <span data-ttu-id="4d150-113">Aguardar o depurador gerenciado (opcional)</span><span class="sxs-lookup"><span data-stu-id="4d150-113">Wait for Managed Debugger (optional)</span></span>

    ![Configurações de Build do UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="4d150-115">Compilar no Unity.</span><span class="sxs-lookup"><span data-stu-id="4d150-115">Build in Unity.</span></span>
1. <span data-ttu-id="4d150-116">Crie e implante a partir da solução do Visual Studio para seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d150-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="4d150-117">Você deve criar com as configurações de **depuração** ou de **versão** .</span><span class="sxs-lookup"><span data-stu-id="4d150-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="4d150-118">A configuração **mestra** desabilita o Unity Profiler e pode impedir a depuração ideal.</span><span class="sxs-lookup"><span data-stu-id="4d150-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="4d150-119">Opcionalmente, verifique a **Internet (cliente & Server)** e as **redes privadas (cliente & Server)** na lista de recursos em Package. appxmanifest na solução.</span><span class="sxs-lookup"><span data-stu-id="4d150-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="4d150-120">Inicie o aplicativo em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d150-120">Start the app on your device.</span></span> <span data-ttu-id="4d150-121">Verifique se o dispositivo está conectado à mesma rede que o seu PC.</span><span class="sxs-lookup"><span data-stu-id="4d150-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="4d150-122">Verifique se o dispositivo **não está** conectado ao seu PC via USB.</span><span class="sxs-lookup"><span data-stu-id="4d150-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="4d150-123">Vá para a solução do Visual Studio que é criada quando você clica duas vezes em um script no Unity, no qual você pode C# exibir e editar seus scripts.</span><span class="sxs-lookup"><span data-stu-id="4d150-123">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="4d150-124">Debug-> anexar o depurador Unity.</span><span class="sxs-lookup"><span data-stu-id="4d150-124">Debug -> Attach Unity Debugger.</span></span>

    ![Anexar depurador do Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="4d150-126">Selecione seu dispositivo na lista e clique em "OK" para anexar.</span><span class="sxs-lookup"><span data-stu-id="4d150-126">Select your device in the list and click "OK" to attach.</span></span>

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)

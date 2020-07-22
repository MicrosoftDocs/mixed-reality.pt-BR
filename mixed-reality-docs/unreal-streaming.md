---
title: Streaming no Unreal
description: Um guia de streaming no Unreal para o HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, streaming, computador, comunicação remota de aplicativo holográfico, Holographic Remoting Player, documentação
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: d25efbcf83e45749cc4eb8b99581b71105c59c9d
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303527"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="b12b8-104">Streaming no Unreal</span><span class="sxs-lookup"><span data-stu-id="b12b8-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="b12b8-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b12b8-105">Overview</span></span>
<span data-ttu-id="b12b8-106">O streaming de um computador para o HoloLens fornece duas vantagens principais:</span><span class="sxs-lookup"><span data-stu-id="b12b8-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="b12b8-107">Ele permite que o aplicativo de realidade misturada aproveite a capacidade computacional dos seus computadores.</span><span class="sxs-lookup"><span data-stu-id="b12b8-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="b12b8-108">Ele ajuda a acelerar o tempo de iteração do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="b12b8-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="b12b8-109">Para começar, baixe o [Holographic Remoting Player](holographic-remoting-player.md) no seu dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b12b8-109">To get started, you'll need to download the [Holographic Remoting Player](holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="b12b8-110">Isso permite que o seu aplicativo seja transmitido diretamente para o player de comunicação remota no HoloLens das seguintes fontes:</span><span class="sxs-lookup"><span data-stu-id="b12b8-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="b12b8-111">O editor do Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="b12b8-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="b12b8-112">Um executável empacotado do Windows</span><span class="sxs-lookup"><span data-stu-id="b12b8-112">A packaged Windows executable</span></span> 

<span data-ttu-id="b12b8-113">Durante o streaming, você tem acesso a quase todas as mesmas funcionalidades do HoloLens que teria ao executar um aplicativo em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b12b8-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="b12b8-114">Isso inclui o [rastreamento da articulação da mão](unreal-hand-tracking.md) (se você estiver usando um HoloLens 2), o [mapeamento espacial](unreal-spatial-mapping.md) e as [âncoras espaciais](unreal-spatial-anchors.md), mas exclui os recursos desta [lista de limitações](holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="b12b8-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="b12b8-115">A qualidade de streaming é altamente dependente da força da rede Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="b12b8-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="b12b8-116">Todos os recursos são habilitados automaticamente para o player de comunicação remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="b12b8-116">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="b12b8-117">Se você encontrar uma funcionalidade que exija permissão de usuário (por exemplo, acompanhamento de olho) para funcionar por streaming, mas não durante a execução no dispositivo, verifique se você habilitou os recursos adequados nas configurações do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b12b8-117">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="b12b8-118">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="b12b8-118">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b12b8-119"><strong>Origem</strong></span><span class="sxs-lookup"><span data-stu-id="b12b8-119"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="b12b8-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1ª geração</strong></a></span><span class="sxs-lookup"><span data-stu-id="b12b8-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="b12b8-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="b12b8-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="b12b8-122"><strong>Headsets imersivos</strong></span><span class="sxs-lookup"><span data-stu-id="b12b8-122"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b12b8-123">Editor do Unreal</span><span class="sxs-lookup"><span data-stu-id="b12b8-123">Unreal editor</span></span></td>
        <td><span data-ttu-id="b12b8-124">✔️</span><span class="sxs-lookup"><span data-stu-id="b12b8-124">✔️</span></span></td>
        <td><span data-ttu-id="b12b8-125">✔️</span><span class="sxs-lookup"><span data-stu-id="b12b8-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="b12b8-126">Pacote do Windows</span><span class="sxs-lookup"><span data-stu-id="b12b8-126">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b12b8-127">✔️</span><span class="sxs-lookup"><span data-stu-id="b12b8-127">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="b12b8-128">Streaming do editor do Unreal</span><span class="sxs-lookup"><span data-stu-id="b12b8-128">Streaming from the Unreal editor</span></span>

<span data-ttu-id="b12b8-129">Como desenvolvedor, você descobrirá que o streaming do editor do Unreal para o dispositivo HoloLens fornece grandes benefícios durante o teste, ou seja, você não precisa mais esperar que o aplicativo seja compilado e implantado antes de experimentar as atualizações.</span><span class="sxs-lookup"><span data-stu-id="b12b8-129">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="b12b8-130">Encontre instruções detalhadas em [Streaming do editor do Unreal](unreal-uxt-ch6.md#device-only-streaming) na última seção da Introdução com as séries de tutoriais do Unreal.</span><span class="sxs-lookup"><span data-stu-id="b12b8-130">You can find detailed instructions on [streaming from the Unreal editor](unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="b12b8-131">Streaming de um executável empacotado do Windows</span><span class="sxs-lookup"><span data-stu-id="b12b8-131">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="b12b8-132">No Unreal 4.25.1 em diante, você pode transmitir seu aplicativo para um dispositivo HoloLens 2 de um executável empacotado do Windows seguindo as etapas abaixo:</span><span class="sxs-lookup"><span data-stu-id="b12b8-132">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="b12b8-133">Acesse **Arquivo > Projeto de Pacote > Windows** no menu do editor.</span><span class="sxs-lookup"><span data-stu-id="b12b8-133">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="b12b8-134">Escolha uma localização para salvar o pacote e clique em **Selecionar Pasta**.</span><span class="sxs-lookup"><span data-stu-id="b12b8-134">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="b12b8-135">Depois que o pacote terminar de ser compilado, abra o **Holographic Remoting Player** no HoloLens 2 e anote o endereço IP.</span><span class="sxs-lookup"><span data-stu-id="b12b8-135">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="b12b8-136">Deixe o **Holographic Remoting Player** aberto e use o prompt de linha de comando para:</span><span class="sxs-lookup"><span data-stu-id="b12b8-136">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="b12b8-137">Executar cd no diretório local em que você salvou o pacote.</span><span class="sxs-lookup"><span data-stu-id="b12b8-137">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="b12b8-138">Digite o seguinte comando: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="b12b8-138">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="b12b8-139">O nome do aplicativo nas configurações do projeto deverá ser usado automaticamente para criar o pacote do Windows.</span><span class="sxs-lookup"><span data-stu-id="b12b8-139">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="b12b8-140">Se ele for diferente por algum motivo, use o nome do executável do Windows no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="b12b8-140">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="b12b8-141">Pressione ENTER e veja seu aplicativo começar a ser transmitido.</span><span class="sxs-lookup"><span data-stu-id="b12b8-141">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="b12b8-142">Veja também</span><span class="sxs-lookup"><span data-stu-id="b12b8-142">See also</span></span>
* [<span data-ttu-id="b12b8-143">Histórico de versões do Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="b12b8-143">Holographic remoting version history</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="b12b8-144">Como escrever um aplicativo personalizado do Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="b12b8-144">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="b12b8-145">Como estabelecer uma conexão segura com o Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="b12b8-145">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)

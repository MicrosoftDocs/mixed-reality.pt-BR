---
title: Conectando-se ao Wi-Fi no HoloLens
description: Instruções sobre como se conectar à Internet sem fio com o HoloLens e como identificar o endereço IP do dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, WiFi, sem fio, Internet, IP, endereço IP
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670112"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="a9b8f-104">Conectando-se ao Wi-Fi no HoloLens</span><span class="sxs-lookup"><span data-stu-id="a9b8f-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="a9b8f-105">O HoloLens contém uma rádio Wi-Fi com capacidade para AC 802.11, 2x2.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="a9b8f-106">Conectar o HoloLens a uma rede Wi-Fi é semelhante a conectar um dispositivo Windows 10 desktop ou móvel a uma rede Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Configurações de Wi-Fi do HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="a9b8f-108">Conectando-se a uma rede Wi-Fi no HoloLens</span><span class="sxs-lookup"><span data-stu-id="a9b8f-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="a9b8f-109">[Cair](gestures.md#bloom) para o menu **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="a9b8f-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="a9b8f-110">Selecione o aplicativo **configurações** em iniciar ou na lista **todos os aplicativos** à direita do menu iniciar.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="a9b8f-111">O aplicativo de **configurações** será colocado automaticamente na frente de você.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="a9b8f-112">Selecione **rede & Internet**.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="a9b8f-113">Verifique se o Wi-Fi está ativado.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="a9b8f-114">Selecione uma rede Wi-Fi na lista.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="a9b8f-115">Digite a senha da rede Wi-Fi (se necessário).</span><span class="sxs-lookup"><span data-stu-id="a9b8f-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="a9b8f-116">Desabilitando Wi-Fi no HoloLens</span><span class="sxs-lookup"><span data-stu-id="a9b8f-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="a9b8f-117">Usando o aplicativo de configurações no HoloLens</span><span class="sxs-lookup"><span data-stu-id="a9b8f-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="a9b8f-118">[Cair](gestures.md#bloom) para o menu **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="a9b8f-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="a9b8f-119">Selecione o aplicativo **configurações** em iniciar ou na lista **todos os aplicativos** à direita do menu iniciar.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="a9b8f-120">O aplicativo de **configurações** será colocado automaticamente na frente de você.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="a9b8f-121">Selecione **rede & Internet**.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="a9b8f-122">Selecione a opção de controle deslizante Wi-Fi para movê-la para a posição "off".</span><span class="sxs-lookup"><span data-stu-id="a9b8f-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="a9b8f-123">Isso desligará os componentes RF da rádio Wi-Fi e desabilitará toda a funcionalidade de Wi-Fi no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="a9b8f-124">O HoloLens não poderá carregar seus [espaços](environment-considerations-for-hololens.md#WiFi fingerprint considerations) automaticamente quando o Wi-Fi Radio estiver desabilitado.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="a9b8f-125">Mova o controle deslizante para a posição "on" para ativar o rádio Wi-Fi e restaurar a funcionalidade Wi-Fi no Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="a9b8f-126">O estado de rádio Wi-Fi selecionado ("on" de "off") persistirá entre as reinicializações.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="a9b8f-127">Como confirmar que você está conectado a uma rede Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="a9b8f-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="a9b8f-128">[Incair](gestures.md#bloom) para abrir o menu **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="a9b8f-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="a9b8f-129">Examine a parte superior esquerda do menu Iniciar para status de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="a9b8f-130">O estado de Wi-Fi e o SSID da rede conectada serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="a9b8f-131">Identificando o endereço IP do seu HoloLens na rede Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="a9b8f-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="a9b8f-132">Usando o aplicativo configurações</span><span class="sxs-lookup"><span data-stu-id="a9b8f-132">Using the Settings app</span></span>

1. <span data-ttu-id="a9b8f-133">[Cair](gestures.md#bloom) para o menu **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="a9b8f-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="a9b8f-134">Selecione o aplicativo **configurações** em iniciar ou na lista **todos os aplicativos** à direita do menu iniciar.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="a9b8f-135">O aplicativo de **configurações** será colocado automaticamente na frente de você.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="a9b8f-136">Selecione **rede & Internet**.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="a9b8f-137">Role para baixo até a lista de redes Wi-Fi disponíveis e selecione **Propriedades de hardware**.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Propriedades de hardware nas configurações de Wi-Fi](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="a9b8f-139">O endereço IP será mostrado ao lado do **endereço IPv4**.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="a9b8f-140">Usando a Cortana</span><span class="sxs-lookup"><span data-stu-id="a9b8f-140">Using Cortana</span></span>

<span data-ttu-id="a9b8f-141">Diga "*Ei Cortana, qual é meu endereço IP?* "</span><span class="sxs-lookup"><span data-stu-id="a9b8f-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="a9b8f-142">e a Cortana exibirá e lerá seu endereço IP.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="a9b8f-143">Usando o portal de dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="a9b8f-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="a9b8f-144">Abra o [portal do dispositivo](using-the-windows-device-portal.md#networking) em um navegador da Web em seu computador.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="a9b8f-145">Navegue até a seção **rede** .</span><span class="sxs-lookup"><span data-stu-id="a9b8f-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="a9b8f-146">Seu endereço IP e outras informações de rede serão exibidos lá.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="a9b8f-147">Esse método permite copiar e colar facilmente o endereço IP no seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a9b8f-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>

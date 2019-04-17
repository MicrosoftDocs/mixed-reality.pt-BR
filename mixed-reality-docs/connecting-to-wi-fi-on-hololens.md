---
title: Conectar-se ao Wi-Fi em HoloLens
description: Instruções sobre como se conectar à internet sem fio com o HoloLens e como identificar o endereço IP do dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, wifi, wireless, internet, ip, ip address
ms.openlocfilehash: 0440c3dad48d73db51e7d730e79d6eb1e74a5694
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590816"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="c54f8-104">Conectar-se ao Wi-Fi em HoloLens</span><span class="sxs-lookup"><span data-stu-id="c54f8-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="c54f8-105">HoloLens contém um 802.11ac-capaz, 2 x 2 rádio de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="c54f8-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="c54f8-106">Conectar o HoloLens a uma rede Wi-Fi é semelhante a conectar um dispositivo Windows 10 Desktop ou Mobile a uma rede Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="c54f8-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Configurações de Wi-Fi HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="c54f8-108">Conectar a uma rede Wi-Fi em HoloLens</span><span class="sxs-lookup"><span data-stu-id="c54f8-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="c54f8-109">[Bloom](gestures.md#bloom) para o **iniciar** menu.</span><span class="sxs-lookup"><span data-stu-id="c54f8-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c54f8-110">Selecione o **as configurações** aplicativo de início ou do **todos os aplicativos** lista à direita do menu Iniciar.</span><span class="sxs-lookup"><span data-stu-id="c54f8-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c54f8-111">O **configurações** aplicativo será colocado automaticamente na sua frente.</span><span class="sxs-lookup"><span data-stu-id="c54f8-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c54f8-112">Selecione **rede e Internet**.</span><span class="sxs-lookup"><span data-stu-id="c54f8-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c54f8-113">Verifique se o Wi-Fi está ativado.</span><span class="sxs-lookup"><span data-stu-id="c54f8-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="c54f8-114">Selecione uma rede Wi-Fi na lista.</span><span class="sxs-lookup"><span data-stu-id="c54f8-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="c54f8-115">Digite a senha de rede Wi-Fi (se necessário).</span><span class="sxs-lookup"><span data-stu-id="c54f8-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="c54f8-116">Desabilitando o Wi-Fi em HoloLens</span><span class="sxs-lookup"><span data-stu-id="c54f8-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="c54f8-117">Usando o aplicativo de configurações em HoloLens</span><span class="sxs-lookup"><span data-stu-id="c54f8-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="c54f8-118">[Bloom](gestures.md#bloom) para o **iniciar** menu.</span><span class="sxs-lookup"><span data-stu-id="c54f8-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c54f8-119">Selecione o **as configurações** aplicativo de início ou do **todos os aplicativos** lista à direita do menu Iniciar.</span><span class="sxs-lookup"><span data-stu-id="c54f8-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c54f8-120">O **configurações** aplicativo será colocado automaticamente na sua frente.</span><span class="sxs-lookup"><span data-stu-id="c54f8-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c54f8-121">Selecione **rede e Internet**.</span><span class="sxs-lookup"><span data-stu-id="c54f8-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c54f8-122">Selecione a opção de controle deslizante de Wi-Fi para movê-lo para a posição "Desativado".</span><span class="sxs-lookup"><span data-stu-id="c54f8-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="c54f8-123">Isso irá desativar os componentes de RF do rádio Wi-Fi e desabilitar todas as funcionalidades de Wi-Fi em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c54f8-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="c54f8-124">HoloLens não poderão carregar automaticamente seus [espaços](environment-considerations-for-hololens.md#spaces) quando a opção de Wi-Fi está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="c54f8-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#spaces) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="c54f8-125">Mova a opção de controle deslizante para a posição de "On" para ativar a opção de Wi-Fi e restaurar a funcionalidade de Wi-Fi no Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c54f8-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="c54f8-126">O estado de rádio Wi-Fi selecionado ("ligado" de "Desativado") será mantido entre as reinicializações.</span><span class="sxs-lookup"><span data-stu-id="c54f8-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="c54f8-127">Como confirmar que você está conectado a uma rede Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="c54f8-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="c54f8-128">[Bloom](gestures.md#bloom) para abrir o **iniciar** menu.</span><span class="sxs-lookup"><span data-stu-id="c54f8-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="c54f8-129">Observe a parte superior esquerda do menu Iniciar para o status de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="c54f8-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="c54f8-130">O estado de Wi-Fi e o SSID da rede conectada serão mostrados.</span><span class="sxs-lookup"><span data-stu-id="c54f8-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="c54f8-131">Identificar o endereço IP do seu HoloLens na rede Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="c54f8-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="c54f8-132">Usando o aplicativo de configurações</span><span class="sxs-lookup"><span data-stu-id="c54f8-132">Using the Settings app</span></span>

1. <span data-ttu-id="c54f8-133">[Bloom](gestures.md#bloom) para o **iniciar** menu.</span><span class="sxs-lookup"><span data-stu-id="c54f8-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c54f8-134">Selecione o **as configurações** aplicativo de início ou do **todos os aplicativos** lista à direita do menu Iniciar.</span><span class="sxs-lookup"><span data-stu-id="c54f8-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c54f8-135">O **configurações** aplicativo será colocado automaticamente na sua frente.</span><span class="sxs-lookup"><span data-stu-id="c54f8-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c54f8-136">Selecione **rede e Internet**.</span><span class="sxs-lookup"><span data-stu-id="c54f8-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c54f8-137">Role para baixo até abaixo da lista de redes Wi-Fi disponíveis e selecione **propriedades de Hardware**.</span><span class="sxs-lookup"><span data-stu-id="c54f8-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Propriedades de hardware nas configurações de Wi-Fi](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="c54f8-139">O endereço IP será mostrado ao lado **endereço IPv4**.</span><span class="sxs-lookup"><span data-stu-id="c54f8-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="c54f8-140">Usando o Cortana</span><span class="sxs-lookup"><span data-stu-id="c54f8-140">Using Cortana</span></span>

<span data-ttu-id="c54f8-141">Dizer "*Ei Cortana, o que é meu endereço IP?*"</span><span class="sxs-lookup"><span data-stu-id="c54f8-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="c54f8-142">e Cortana exibirá e ler seu endereço IP.</span><span class="sxs-lookup"><span data-stu-id="c54f8-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="c54f8-143">Usando o Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="c54f8-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="c54f8-144">Abra o [portal do dispositivo](using-the-windows-device-portal.md#networking) em um navegador da web em seu computador.</span><span class="sxs-lookup"><span data-stu-id="c54f8-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="c54f8-145">Navegue até a **rede** seção.</span><span class="sxs-lookup"><span data-stu-id="c54f8-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="c54f8-146">Seu endereço IP e outras informações de rede serão exibidos lá.</span><span class="sxs-lookup"><span data-stu-id="c54f8-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="c54f8-147">Esse método permite fácil copiar e colar do endereço IP em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c54f8-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>

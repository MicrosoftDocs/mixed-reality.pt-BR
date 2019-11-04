---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor de dispositivo de chave (profundidade, acompanhamento de ambiente e IR-reflectivity).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de pesquisa, CV, RS4, visão computacional, pesquisa, HoloLens
ms.openlocfilehash: 307df0c226221422f13af09d8f4944c22ead3865
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438309"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="15822-104">Modo de pesquisa do HoloLens</span><span class="sxs-lookup"><span data-stu-id="15822-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="15822-105">Esse recurso foi adicionado como parte da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) para o HoloLens e não está disponível em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="15822-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="15822-106">O modo de pesquisa é um novo recurso do HoloLens que fornece acesso de aplicativo aos sensores de chave no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="15822-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="15822-107">São elas:</span><span class="sxs-lookup"><span data-stu-id="15822-107">These include:</span></span>
- <span data-ttu-id="15822-108">As quatro câmeras de acompanhamento de ambiente usadas pelo sistema para criação de mapa e acompanhamento de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="15822-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="15822-109">Duas versões dos dados da câmera de profundidade – uma para a detecção de alta frequência (30 FPS) de profundidade, normalmente usada e a outra para a detecção de profundidade de extrema frequência (1-5 FPS), atualmente usada pelo mapeamento espacial,</span><span class="sxs-lookup"><span data-stu-id="15822-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1-5 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="15822-110">Duas versões de um fluxo IR-reflectivity, usadas pelo HoloLens para computar a profundidade, mas valiosas por si só, à medida que essas imagens são acesas do HoloLens e não afetam razoavelmente por luz ambiente.</span><span class="sxs-lookup"><span data-stu-id="15822-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="15822-111">captura de tela do aplicativo do modo de pesquisa ![](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="15822-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="15822-112">*Uma captura de realidade misturada de um aplicativo de teste que exibe os oito fluxos de sensor disponíveis no modo de pesquisa*</span><span class="sxs-lookup"><span data-stu-id="15822-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="15822-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="15822-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="15822-114"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="15822-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="15822-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="15822-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="15822-116"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="15822-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="15822-117">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="15822-117">Research mode</span></span></td>
        <td><span data-ttu-id="15822-118">✔️</span><span class="sxs-lookup"><span data-stu-id="15822-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="15822-119">Antes de usar o modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="15822-119">Before using Research mode</span></span>

<span data-ttu-id="15822-120">O modo de pesquisa é bem nomeado: destina-se a pesquisadores acadêmicos e industriais experimentando novas ideias nos campos de Pesquisa Visual Computacional e robótica.</span><span class="sxs-lookup"><span data-stu-id="15822-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="15822-121">O modo de pesquisa não se destina a aplicativos que serão implantados em uma empresa ou disponibilizados no Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="15822-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="15822-122">O motivo disso é que o modo de pesquisa reduz a segurança do seu dispositivo e consome significativamente mais energia da bateria do que a operação normal.</span><span class="sxs-lookup"><span data-stu-id="15822-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="15822-123">A Microsoft não está confirmando o suporte a esse modo em nenhum dispositivo futuro.</span><span class="sxs-lookup"><span data-stu-id="15822-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="15822-124">Portanto, recomendamos que você o use para desenvolver e testar novas ideias; no entanto, você não poderá implantar amplamente aplicativos que usam o modo de pesquisa ou ter qualquer garantia de que ele continuará a funcionar no hardware futuro.</span><span class="sxs-lookup"><span data-stu-id="15822-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="15822-125">Habilitando o modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="15822-125">Enabling Research mode</span></span>

<span data-ttu-id="15822-126">O modo de pesquisa é um submodo do modo de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="15822-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="15822-127">Primeiro, você precisa habilitar o modo de desenvolvedor no aplicativo Configurações (**configurações > atualização & segurança > para desenvolvedores**):</span><span class="sxs-lookup"><span data-stu-id="15822-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="15822-128">Defina "usar recursos de desenvolvedor" como **on**</span><span class="sxs-lookup"><span data-stu-id="15822-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="15822-129">Defina "habilitar o portal do dispositivo" como **ativado**</span><span class="sxs-lookup"><span data-stu-id="15822-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="15822-130">Em seguida, usando um navegador da Web que está conectado à mesma rede Wi-Fi que o seu HoloLens, navegue até o endereço IP do seu HoloLens (obtido por meio **das configurações > rede & Internet > Wi-Fi > Propriedades de hardware**).</span><span class="sxs-lookup"><span data-stu-id="15822-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="15822-131">Este é o [portal do dispositivo](using-the-windows-device-portal.md)e você encontrará uma página "modo de pesquisa" na seção "sistema" do portal:</span><span class="sxs-lookup"><span data-stu-id="15822-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="15822-132">guia modo de pesquisa ![do portal do dispositivo de HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="15822-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="15822-133">*Modo de pesquisa no portal do dispositivo do HoloLens*</span><span class="sxs-lookup"><span data-stu-id="15822-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="15822-134">Depois de selecionar **permitir o acesso aos fluxos de sensor**, você precisará reinicializar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="15822-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="15822-135">Você pode fazer isso no portal do dispositivo, sob o item de menu "Power" na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="15822-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="15822-136">Depois que o dispositivo for reinicializado, os aplicativos que foram carregados por meio do portal do dispositivo deverão ser capazes de acessar os fluxos do modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="15822-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="15822-137">Usando dados de sensor em seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="15822-137">Using sensor data in your apps</span></span>

<span data-ttu-id="15822-138">Os aplicativos podem acessar dados de fluxo do sensor abrindo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) fluxos exatamente da mesma maneira que acessam o fluxo de foto/vídeo da câmera.</span><span class="sxs-lookup"><span data-stu-id="15822-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="15822-139">Todas as APIs que funcionam para o desenvolvimento do HoloLens também estão disponíveis no modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="15822-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="15822-140">Em particular, o aplicativo pode saber precisamente onde o HoloLens está no espaço 6DoF em cada tempo de captura do quadro do sensor.</span><span class="sxs-lookup"><span data-stu-id="15822-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="15822-141">Aplicativos de exemplo mostrando como você acessa os vários fluxos do modo de pesquisa, como usar os intrínsecos e as extrínsecos e como registrar os fluxos estão disponíveis no [repositório GitHub do HoloLensForCV](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="15822-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="15822-142">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="15822-142">Known issues</span></span>

<span data-ttu-id="15822-143">Consulte o Issue [Tracker](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV.</span><span class="sxs-lookup"><span data-stu-id="15822-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="15822-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15822-144">See also</span></span>

* [<span data-ttu-id="15822-145">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="15822-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="15822-146">Repositório GitHub HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="15822-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="15822-147">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="15822-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)

---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor do dispositivo de chave (profundidade, o ambiente de controle e reflexibilidade IV).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de pesquisa, cv, rs4, pesquisa Visual computacional, pesquisa, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829936"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="f3c39-104">Modo de pesquisa do HoloLens</span><span class="sxs-lookup"><span data-stu-id="f3c39-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="f3c39-105">Esse recurso foi adicionado como parte do [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) para HoloLens e não está disponível em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f3c39-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="f3c39-106">Modo de pesquisa é uma nova funcionalidade do HoloLens que fornece acesso a aplicativos para os sensores de chave no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f3c39-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="f3c39-107">Como por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f3c39-107">These include:</span></span>
- <span data-ttu-id="f3c39-108">Os quatro câmeras usadas pelo sistema para construção de mapa e acompanhamento de cabeçalho de controle do ambiente.</span><span class="sxs-lookup"><span data-stu-id="f3c39-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="f3c39-109">Duas versões dos dados de câmera de profundidade – um para detecção de perto de profundidade de (30 FPS) de alta frequência, comumente usados em mãos de controle e outro para frequência inferior (1 FPS) longe da profundidade detecção, sendo usavam atualmente por mapeamento espacial,</span><span class="sxs-lookup"><span data-stu-id="f3c39-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="f3c39-110">Duas versões de um fluxo de IR reflexibilidade, usada pelo HoloLens para computar a profundidade, mas valioso em si mesmo como essas imagens são iluminados do HoloLens e razoavelmente não serão afetadas pela luz ambiente.</span><span class="sxs-lookup"><span data-stu-id="f3c39-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="f3c39-111">![Captura de tela de aplicativo de modo de pesquisa](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="f3c39-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="f3c39-112">*Uma captura de realidade mista de um aplicativo de teste que exibe os fluxos de oito sensor disponíveis no modo de pesquisa*</span><span class="sxs-lookup"><span data-stu-id="f3c39-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="f3c39-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="f3c39-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3c39-114"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="f3c39-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f3c39-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3c39-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3c39-116"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3c39-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3c39-117">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="f3c39-117">Research mode</span></span></td>
        <td><span data-ttu-id="f3c39-118">✔️</span><span class="sxs-lookup"><span data-stu-id="f3c39-118">✔️</span></span></td>
        <td><span data-ttu-id="f3c39-119">❌</span><span class="sxs-lookup"><span data-stu-id="f3c39-119">❌</span></span></td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="f3c39-120">Antes de usar o modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="f3c39-120">Before using Research mode</span></span>

<span data-ttu-id="f3c39-121">Modo de pesquisa também é chamado: destina-se para pesquisadores acadêmicos e industriais experimentar novas ideias nos campos de pesquisa Visual computacional e robótica.</span><span class="sxs-lookup"><span data-stu-id="f3c39-121">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="f3c39-122">Modo de pesquisa não foi projetado para aplicativos que serão implantados em toda a empresa ou disponibilizados a Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="f3c39-122">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="f3c39-123">A razão para isso é que o modo de pesquisa reduz a segurança do seu dispositivo e consome significativamente mais bateria do que a operação normal.</span><span class="sxs-lookup"><span data-stu-id="f3c39-123">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="f3c39-124">Microsoft não está confirmando para dar suporte a esse modo em qualquer dispositivo futuras.</span><span class="sxs-lookup"><span data-stu-id="f3c39-124">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="f3c39-125">Dessa forma, recomendamos que você pode usá-lo para desenvolver e testar novas ideias; No entanto, você não poderá implantar amplamente os aplicativos que usam o modo de pesquisa ou têm qualquer garantia de que ele continuará a trabalhar em futuras de hardware.</span><span class="sxs-lookup"><span data-stu-id="f3c39-125">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="f3c39-126">Habilitar o modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="f3c39-126">Enabling Research mode</span></span>

<span data-ttu-id="f3c39-127">Modo de pesquisa é um modo de subpropriedades de modo de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="f3c39-127">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="f3c39-128">Primeiro, você precisa habilitar o modo de desenvolvedor no aplicativo configurações (**Configurações > atualização e segurança > para os desenvolvedores**):</span><span class="sxs-lookup"><span data-stu-id="f3c39-128">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="f3c39-129">Defina "Usar recursos de desenvolvedor" como **em**</span><span class="sxs-lookup"><span data-stu-id="f3c39-129">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="f3c39-130">Definido "Habilitar Portal do dispositivo" como **em**</span><span class="sxs-lookup"><span data-stu-id="f3c39-130">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="f3c39-131">Em seguida, usando um navegador da web que está conectado à mesma rede Wi-Fi como o HoloLens, navegue até o endereço IP do seu HoloLens (obtidas por meio **Configurações > rede e Internet > Wi-Fi > Propriedades de Hardware**).</span><span class="sxs-lookup"><span data-stu-id="f3c39-131">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="f3c39-132">Esse é o [Portal do dispositivo](using-the-windows-device-portal.md), e você verá uma página de "Modo de pesquisa" na seção "Sistema" do portal:</span><span class="sxs-lookup"><span data-stu-id="f3c39-132">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="f3c39-133">![Guia de modo de pesquisa do Portal de dispositivos do HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="f3c39-133">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="f3c39-134">*Modo de pesquisa no Portal de dispositivos do HoloLens*</span><span class="sxs-lookup"><span data-stu-id="f3c39-134">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="f3c39-135">Depois de selecionar **permitir o acesso a fluxos de sensor**, você precisará reiniciar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f3c39-135">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="f3c39-136">Você pode fazer isso no Portal de dispositivo, sob o item de menu "Power" na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="f3c39-136">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="f3c39-137">Depois que o dispositivo for reinicializado, os aplicativos que foram carregados por meio do Portal do dispositivo devem ser capazes de acessar fluxos de modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="f3c39-137">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="f3c39-138">Usando dados de sensor em seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="f3c39-138">Using sensor data in your apps</span></span>

<span data-ttu-id="f3c39-139">Aplicativos podem acessar dados de fluxo de sensor, abrindo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) fluxos exatamente da mesma forma que eles acessam o fluxo de câmera de vídeo/foto.</span><span class="sxs-lookup"><span data-stu-id="f3c39-139">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="f3c39-140">Todas as APIs que funcionam para o desenvolvimento HoloLens também estão disponíveis no modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="f3c39-140">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="f3c39-141">Em particular, o aplicativo possa saber exatamente onde HoloLens está no espaço de 6DoF no momento da captura de quadro cada sensor.</span><span class="sxs-lookup"><span data-stu-id="f3c39-141">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="f3c39-142">Aplicativos de exemplo que mostra como você pode acessar vários fluxos de modo de pesquisa, como usar os intrínsecos e extrinsics e como gravar fluxos estão disponíveis na [repositório HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="f3c39-142">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="f3c39-143">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="f3c39-143">Known issues</span></span>

<span data-ttu-id="f3c39-144">Consulte a [rastreador de problemas](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV.</span><span class="sxs-lookup"><span data-stu-id="f3c39-144">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3c39-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3c39-145">See also</span></span>

* [<span data-ttu-id="f3c39-146">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="f3c39-146">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="f3c39-147">Repositório HoloLensForCV GitHub</span><span class="sxs-lookup"><span data-stu-id="f3c39-147">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="f3c39-148">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="f3c39-148">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)

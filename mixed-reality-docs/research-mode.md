---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor do dispositivo de chave (profundidade, o ambiente de controle e reflexibilidade IV).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de pesquisa, cv, rs4, pesquisa Visual computacional, pesquisa, HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589074"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="a9bd1-104">Modo de pesquisa do HoloLens</span><span class="sxs-lookup"><span data-stu-id="a9bd1-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="a9bd1-105">Esse recurso foi adicionado como parte do [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) para HoloLens e não está disponível em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="a9bd1-106">Modo de pesquisa é uma nova funcionalidade do HoloLens que fornece acesso a aplicativos para os sensores de chave no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="a9bd1-107">Como por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a9bd1-107">These include:</span></span>
- <span data-ttu-id="a9bd1-108">Os quatro câmeras usadas pelo sistema para construção de mapa e acompanhamento de cabeçalho de controle do ambiente.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="a9bd1-109">Duas versões dos dados de câmera de profundidade – um para detecção de perto de profundidade de (30 FPS) de alta frequência, comumente usados em mãos de controle e outro para frequência inferior (1 FPS) longe da profundidade detecção, sendo usavam atualmente por mapeamento espacial,</span><span class="sxs-lookup"><span data-stu-id="a9bd1-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="a9bd1-110">Duas versões de um fluxo de IR reflexibilidade, usada pelo HoloLens para computar a profundidade, mas valioso em si mesmo como essas imagens são iluminados do HoloLens e razoavelmente não serão afetadas pela luz ambiente.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="a9bd1-111">![Captura de tela de aplicativo de modo de pesquisa](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="a9bd1-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="a9bd1-112">*Uma captura de realidade mista de um aplicativo de teste que exibe os fluxos de oito sensor disponíveis no modo de pesquisa*</span><span class="sxs-lookup"><span data-stu-id="a9bd1-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="a9bd1-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="a9bd1-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a9bd1-114">Recurso</span><span class="sxs-lookup"><span data-stu-id="a9bd1-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="a9bd1-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a9bd1-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a9bd1-116"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="a9bd1-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a9bd1-117">Modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="a9bd1-117">Research mode</span></span></td><td style="text-align: center;"> <span data-ttu-id="a9bd1-118">✔️</span><span class="sxs-lookup"><span data-stu-id="a9bd1-118">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="a9bd1-119">Antes de usar o modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="a9bd1-119">Before using Research mode</span></span>

<span data-ttu-id="a9bd1-120">Modo de pesquisa também é chamado: destina-se para pesquisadores acadêmicos e industriais experimentar novas ideias nos campos de pesquisa Visual computacional e robótica.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="a9bd1-121">Modo de pesquisa não foi projetado para aplicativos que serão implantados em toda a empresa ou disponibilizados a Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="a9bd1-122">A razão para isso é que o modo de pesquisa reduz a segurança do seu dispositivo e consome significativamente mais bateria do que a operação normal.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="a9bd1-123">Microsoft não está confirmando para dar suporte a esse modo em qualquer dispositivo futuras.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="a9bd1-124">Dessa forma, recomendamos que você pode usá-lo para desenvolver e testar novas ideias; No entanto, você não poderá implantar amplamente os aplicativos que usam o modo de pesquisa ou têm qualquer garantia de que ele continuará a trabalhar em futuras de hardware.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="a9bd1-125">Habilitar o modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="a9bd1-125">Enabling Research mode</span></span>

<span data-ttu-id="a9bd1-126">Modo de pesquisa é um modo de subpropriedades de modo de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="a9bd1-127">Primeiro, você precisa habilitar o modo de desenvolvedor no aplicativo configurações (**Configurações > atualização e segurança > para os desenvolvedores**):</span><span class="sxs-lookup"><span data-stu-id="a9bd1-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="a9bd1-128">Defina "Usar recursos de desenvolvedor" como **em**</span><span class="sxs-lookup"><span data-stu-id="a9bd1-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="a9bd1-129">Definido "Habilitar Portal do dispositivo" como **em**</span><span class="sxs-lookup"><span data-stu-id="a9bd1-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="a9bd1-130">Em seguida, usando um navegador da web que está conectado à mesma rede Wi-Fi como o HoloLens, navegue até o endereço IP do seu HoloLens (obtidas por meio **Configurações > rede e Internet > Wi-Fi > Propriedades de Hardware**).</span><span class="sxs-lookup"><span data-stu-id="a9bd1-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="a9bd1-131">Esse é o [Portal do dispositivo](using-the-windows-device-portal.md), e você verá uma página de "Modo de pesquisa" na seção "Sistema" do portal:</span><span class="sxs-lookup"><span data-stu-id="a9bd1-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="a9bd1-132">![Guia de modo de pesquisa do Portal de dispositivos do HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="a9bd1-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="a9bd1-133">*Modo de pesquisa no Portal de dispositivos do HoloLens*</span><span class="sxs-lookup"><span data-stu-id="a9bd1-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="a9bd1-134">Depois de selecionar **permitir o acesso a fluxos de sensor**, você precisará reiniciar o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="a9bd1-135">Você pode fazer isso no Portal de dispositivo, sob o item de menu "Power" na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="a9bd1-136">Depois que o dispositivo for reinicializado, os aplicativos que foram carregados por meio do Portal do dispositivo devem ser capazes de acessar fluxos de modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="a9bd1-137">Usando dados de sensor em seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="a9bd1-137">Using sensor data in your apps</span></span>

<span data-ttu-id="a9bd1-138">Aplicativos podem acessar dados de fluxo de sensor, abrindo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) fluxos exatamente da mesma forma que eles acessam o fluxo de câmera de vídeo/foto.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="a9bd1-139">Todas as APIs que funcionam para o desenvolvimento HoloLens também estão disponíveis no modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="a9bd1-140">Em particular, o aplicativo possa saber exatamente onde HoloLens está no espaço de 6DoF no momento da captura de quadro cada sensor.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="a9bd1-141">Aplicativos de exemplo que mostra como você pode acessar vários fluxos de modo de pesquisa, como usar os intrínsecos e extrinsics e como gravar fluxos estão disponíveis na [repositório HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="a9bd1-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="a9bd1-142">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="a9bd1-142">Known issues</span></span>

<span data-ttu-id="a9bd1-143">Consulte a [rastreador de problemas](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV.</span><span class="sxs-lookup"><span data-stu-id="a9bd1-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9bd1-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9bd1-144">See also</span></span>

* [<span data-ttu-id="a9bd1-145">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="a9bd1-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="a9bd1-146">Repositório HoloLensForCV GitHub</span><span class="sxs-lookup"><span data-stu-id="a9bd1-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="a9bd1-147">Usando o Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="a9bd1-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)

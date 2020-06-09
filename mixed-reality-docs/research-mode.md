---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor de dispositivo de chave (profundidade, acompanhamento de ambiente e IR-reflectivity).
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: modo de pesquisa, CV, RS4, pesquisa Visual computacional, Research, HoloLens, HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533098"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="b48be-104">Modo de pesquisa do HoloLens</span><span class="sxs-lookup"><span data-stu-id="b48be-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="b48be-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="b48be-105">Overview</span></span>

<span data-ttu-id="b48be-106">O modo de pesquisa foi introduzido no HoloLens de primeira geração para dar acesso aos principais sensores no dispositivo, especificamente para aplicativos de pesquisa que não se destinam à implantação.</span><span class="sxs-lookup"><span data-stu-id="b48be-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="b48be-107">Agora você pode coletar dados das seguintes entradas:</span><span class="sxs-lookup"><span data-stu-id="b48be-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="b48be-108">**Câmeras de rastreamento de ambiente leve visíveis** – usadas pelo sistema para rastreamento de cabeçalho e criação de mapa.</span><span class="sxs-lookup"><span data-stu-id="b48be-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="b48be-109">**Câmera de profundidade** – opera em dois modos:</span><span class="sxs-lookup"><span data-stu-id="b48be-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="b48be-110">Detecção de curto-short, de alta frequência (30 FPS) usada para [acompanhamento à mão](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="b48be-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="b48be-111">Detecção de longo alcance, de baixa frequência (1-5 FPS) de longa profundidade usada pelo [mapeamento espacial](spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="b48be-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="b48be-112">**Duas versões do fluxo ir-reflectivity** -usadas pelo HoloLens para calcular a profundidade.</span><span class="sxs-lookup"><span data-stu-id="b48be-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="b48be-113">Essas imagens são iluminadas por infravermelho e não são afetadas pela luz visível de ambiente.</span><span class="sxs-lookup"><span data-stu-id="b48be-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="b48be-114">Se você estiver usando um HoloLens 2, também poderá acessar as seguintes entradas:</span><span class="sxs-lookup"><span data-stu-id="b48be-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="b48be-115">**Acelerômetro** – usado pelo sistema para determinar a aceleração linear ao longo dos eixos X, Y e Z e gravidade.</span><span class="sxs-lookup"><span data-stu-id="b48be-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="b48be-116">**Giro** – usado pelo sistema para determinar rotações.</span><span class="sxs-lookup"><span data-stu-id="b48be-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="b48be-117">**Magnetômetro** – usado pelo sistema para estimar a orientação absoluta.</span><span class="sxs-lookup"><span data-stu-id="b48be-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="b48be-118">![Captura de tela do aplicativo de modo de pesquisa](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="b48be-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="b48be-119">*Uma captura de realidade misturada de um aplicativo de teste que exibe os oito fluxos de sensor disponíveis no modo de pesquisa*</span><span class="sxs-lookup"><span data-stu-id="b48be-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="b48be-120">O recurso de modo de pesquisa foi adicionado como parte da [atualização do Windows 10 de abril de 2018](release-notes-april-2018.md) para o HoloLens e não está disponível em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="b48be-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="b48be-121">Uso</span><span class="sxs-lookup"><span data-stu-id="b48be-121">Usage</span></span>

<span data-ttu-id="b48be-122">O modo de pesquisa foi projetado para pesquisadores acadêmicos e industriais que exploram novas ideias nos campos de Pesquisa Visual Computacional e robótica.</span><span class="sxs-lookup"><span data-stu-id="b48be-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="b48be-123">Ele não se destina a aplicativos implantados em ambientes corporativos ou disponíveis por meio do Microsoft Store ou de outros canais de distribuição.</span><span class="sxs-lookup"><span data-stu-id="b48be-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="b48be-124">Além disso, a Microsoft não fornece garantias de que o modo de pesquisa ou funcionalidade equivalente terá suporte em atualizações futuras de hardware ou sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="b48be-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="b48be-125">No entanto, isso não deve impedir que você o use para desenvolver e testar novas ideias!</span><span class="sxs-lookup"><span data-stu-id="b48be-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="b48be-126">Segurança e desempenho</span><span class="sxs-lookup"><span data-stu-id="b48be-126">Security and performance</span></span>

<span data-ttu-id="b48be-127">Lembre-se de que habilitar o modo de pesquisa usa mais energia da bateria do que usar o HoloLens 2 em condições normais.</span><span class="sxs-lookup"><span data-stu-id="b48be-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="b48be-128">Isso é verdadeiro mesmo que o aplicativo que usa os recursos do modo de pesquisa não esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="b48be-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="b48be-129">Habilitar esse modo também pode reduzir a segurança geral do seu dispositivo, pois os aplicativos podem indevidamente os dados do sensor.</span><span class="sxs-lookup"><span data-stu-id="b48be-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="b48be-130">Você pode encontrar mais informações sobre a segurança do dispositivo nas [perguntas frequentes sobre segurança do HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="b48be-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="b48be-131">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="b48be-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="b48be-132"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="b48be-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b48be-133"><a href="hololens-hardware-details.md"><strong>1ª Gen do HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b48be-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="b48be-134">Câmeras de acompanhamento de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="b48be-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="b48be-135">✔️</span><span class="sxs-lookup"><span data-stu-id="b48be-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="b48be-136">Profundidade & câmera IR</span><span class="sxs-lookup"><span data-stu-id="b48be-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="b48be-137">✔️</span><span class="sxs-lookup"><span data-stu-id="b48be-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="b48be-138">Acelerômetro</span><span class="sxs-lookup"><span data-stu-id="b48be-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="b48be-139">Giroscópio</span><span class="sxs-lookup"><span data-stu-id="b48be-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="b48be-140">Magnetômetro</span><span class="sxs-lookup"><span data-stu-id="b48be-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="b48be-141">O suporte ao modo de pesquisa para o HoloLens 2 deve estar disponível na visualização pública em julho de 2020 e incluirá todos os recursos listados acima.</span><span class="sxs-lookup"><span data-stu-id="b48be-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="b48be-142">Consulte novamente para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b48be-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="b48be-143">Habilitando o modo de pesquisa</span><span class="sxs-lookup"><span data-stu-id="b48be-143">Enabling Research mode</span></span>

<span data-ttu-id="b48be-144">O modo de pesquisa é uma extensão do modo de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="b48be-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="b48be-145">Antes de iniciar, os recursos do desenvolvedor do dispositivo precisam ser habilitados para acessar as configurações do modo de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="b48be-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="b48be-146">Abra o **menu iniciar > configurações** e selecione **atualizações**.</span><span class="sxs-lookup"><span data-stu-id="b48be-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="b48be-147">Selecione **para desenvolvedores** e habilite o **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="b48be-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="b48be-148">Role para baixo e habilite o **portal do dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="b48be-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="b48be-149">Depois que os recursos do desenvolvedor estiverem habilitados, [Conecte-se ao portal do dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar os recursos do modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b48be-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="b48be-150">Na *1ª Gen do HoloLens*:</span><span class="sxs-lookup"><span data-stu-id="b48be-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="b48be-151">Vá para o **sistema > modo de pesquisa** no **portal do dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="b48be-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="b48be-152">Selecione **permitir acesso ao fluxo do sensor**.</span><span class="sxs-lookup"><span data-stu-id="b48be-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="b48be-153">Reinicie o dispositivo a partir do item de menu de **energia** na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="b48be-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="b48be-154">Depois de reiniciar o dispositivo, os aplicativos carregados por meio do portal do **dispositivo** poderão acessar os fluxos do modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b48be-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="b48be-155">![Guia modo de pesquisa do portal do dispositivo do HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="b48be-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="b48be-156">*Janela do modo de pesquisa no portal do dispositivo do HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b48be-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="b48be-157">Usando dados de sensor em seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="b48be-157">Using sensor data in your apps</span></span>

<span data-ttu-id="b48be-158">*1ª Gen do HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b48be-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="b48be-159">Os aplicativos podem acessar os dados de fluxo do sensor da mesma maneira que os fluxos de foto e câmera de vídeo são acessados por meio de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="b48be-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="b48be-160">Todas as APIs que funcionam para o desenvolvimento do HoloLens também estão disponíveis no modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b48be-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="b48be-161">Em particular, o aplicativo sabe precisamente onde o HoloLens está no espaço 6DoF em cada tempo de captura do quadro do sensor.</span><span class="sxs-lookup"><span data-stu-id="b48be-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="b48be-162">Você pode encontrar aplicativos de exemplo sobre como acessar os vários fluxos do modo de pesquisa, como usar os [intrínsecos e as extrínsecos](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e como registrar fluxos no repositório do [repositório GitHub do HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="b48be-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="b48be-163">Neste momento, o exemplo HoloLensForCV não funciona no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b48be-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="b48be-164">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="b48be-164">Known issues</span></span>

<span data-ttu-id="b48be-165">Você pode usar o Issue [Tracker](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV para seguir os problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="b48be-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="b48be-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b48be-166">See also</span></span>

* [<span data-ttu-id="b48be-167">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="b48be-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="b48be-168">Repositório GitHub HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="b48be-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="b48be-169">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="b48be-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)

---
title: Modo de pesquisa do HoloLens
description: Usando o modo de pesquisa no HoloLens, um aplicativo pode acessar fluxos de sensor de dispositivo de chave (profundidade, acompanhamento de ambiente e IR-reflectivity).
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: Modo de pesquisa, CV, RS4, pesquisa Visual computacional, Research, HoloLens, HoloLens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507690"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="4211a-104">Modo de pesquisa do HoloLens</span><span class="sxs-lookup"><span data-stu-id="4211a-104">HoloLens Research Mode</span></span>

<span data-ttu-id="4211a-105">O modo de pesquisa foi introduzido no HoloLens de primeira geração para dar acesso aos principais sensores no dispositivo, especificamente para aplicativos de pesquisa que não se destinam à implantação.</span><span class="sxs-lookup"><span data-stu-id="4211a-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="4211a-106">O modo de pesquisa para o HoloLens 2 retém os recursos do HoloLens 1, adicionando acesso a fluxos adicionais:</span><span class="sxs-lookup"><span data-stu-id="4211a-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="4211a-107">**Câmeras de acompanhamento de ambiente leve visíveis** – câmeras em escala cinza usadas pelo sistema para rastreamento de cabeçalho e criação de mapa.</span><span class="sxs-lookup"><span data-stu-id="4211a-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="4211a-108">**Câmera de profundidade** – opera em dois modos:</span><span class="sxs-lookup"><span data-stu-id="4211a-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="4211a-109">Detecção de AHAT, alta frequência (45 FPS) usada para acompanhamento à mão.</span><span class="sxs-lookup"><span data-stu-id="4211a-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="4211a-110">Diferentemente do modo de curto-throw da primeira versão, AHAT dá uma pseudo profundidade com o encapsulamento de fase além de 1 medidor.</span><span class="sxs-lookup"><span data-stu-id="4211a-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="4211a-111">Detecção de longo alcance, de baixa frequência (1-5 FPS) de longa profundidade usada pelo [mapeamento espacial](spatial-mapping.md)</span><span class="sxs-lookup"><span data-stu-id="4211a-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>

* <span data-ttu-id="4211a-112">**Duas versões do fluxo ir-reflectivity** -usadas pelo HoloLens para calcular a profundidade.</span><span class="sxs-lookup"><span data-stu-id="4211a-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="4211a-113">Essas imagens são iluminadas por infravermelho e não são afetadas pela luz visível de ambiente.</span><span class="sxs-lookup"><span data-stu-id="4211a-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="4211a-114">Se você estiver usando um HoloLens 2, também terá acesso às entradas adicionais abaixo:</span><span class="sxs-lookup"><span data-stu-id="4211a-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="4211a-115">**Acelerômetro** – usado pelo sistema para determinar a aceleração linear ao longo dos eixos X, Y e Z e gravidade.</span><span class="sxs-lookup"><span data-stu-id="4211a-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="4211a-116">**Giro** – usado pelo sistema para determinar rotações.</span><span class="sxs-lookup"><span data-stu-id="4211a-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="4211a-117">**Magnetômetro** – usado pelo sistema para estimar a orientação absoluta.</span><span class="sxs-lookup"><span data-stu-id="4211a-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4211a-118">O modo de pesquisa está atualmente em visualização pública.</span><span class="sxs-lookup"><span data-stu-id="4211a-118">Research Mode is currently in Public Preview.</span></span> <span data-ttu-id="4211a-119">Os exemplos, tutoriais e a documentação da API completa do HoloLens 2 estarão disponíveis em [ECCV 2020](https://eccv2020.eu/
 ) no repositório Git do modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4211a-119">HoloLens 2 samples, tutorials, and full API documentation will be available at [ECCV 2020](https://eccv2020.eu/
 ) in the Research Mode Git repository.</span></span>

<span data-ttu-id="4211a-120">![Captura de tela do aplicativo de modo de pesquisa](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="4211a-120">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="4211a-121">*Uma captura de realidade misturada de um aplicativo de teste que exibe os oito fluxos de sensor disponíveis no modo de pesquisa*</span><span class="sxs-lookup"><span data-stu-id="4211a-121">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="4211a-122">Uso</span><span class="sxs-lookup"><span data-stu-id="4211a-122">Usage</span></span>

<span data-ttu-id="4211a-123">O modo de pesquisa foi projetado para pesquisadores acadêmicos e industriais que exploram novas ideias nos campos de Pesquisa Visual Computacional e robótica.</span><span class="sxs-lookup"><span data-stu-id="4211a-123">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="4211a-124">Ele não se destina a aplicativos implantados em ambientes corporativos ou disponíveis por meio do Microsoft Store ou de outros canais de distribuição.</span><span class="sxs-lookup"><span data-stu-id="4211a-124">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="4211a-125">Além disso, a Microsoft não fornece garantias de que o modo de pesquisa ou funcionalidade equivalente terá suporte em atualizações futuras de hardware ou sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="4211a-125">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="4211a-126">No entanto, isso não deve impedir que você o use para desenvolver e testar novas ideias!</span><span class="sxs-lookup"><span data-stu-id="4211a-126">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="4211a-127">Segurança e desempenho</span><span class="sxs-lookup"><span data-stu-id="4211a-127">Security and performance</span></span>

<span data-ttu-id="4211a-128">Lembre-se de que habilitar o modo de pesquisa usa mais energia da bateria do que usar o HoloLens 2 em condições normais.</span><span class="sxs-lookup"><span data-stu-id="4211a-128">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="4211a-129">Isso é verdadeiro mesmo que o aplicativo que usa os recursos do modo de pesquisa não esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="4211a-129">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="4211a-130">Habilitar esse modo também pode reduzir a segurança geral do seu dispositivo, pois os aplicativos podem indevidamente os dados do sensor.</span><span class="sxs-lookup"><span data-stu-id="4211a-130">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="4211a-131">Você pode encontrar mais informações sobre a segurança do dispositivo nas [perguntas frequentes sobre segurança do HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="4211a-131">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="4211a-132">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="4211a-132">Device support</span></span>
<table><span data-ttu-id="4211a-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="4211a-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="4211a-134"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="4211a-134"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="4211a-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1ª geração</strong></a></span><span class="sxs-lookup"><span data-stu-id="4211a-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="4211a-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="4211a-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4211a-137">Câmeras de acompanhamento de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="4211a-137">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="4211a-138">✔️</span><span class="sxs-lookup"><span data-stu-id="4211a-138">✔️</span></span></td>
        <td><span data-ttu-id="4211a-139">✔️</span><span class="sxs-lookup"><span data-stu-id="4211a-139">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4211a-140">Profundidade & câmera IR</span><span class="sxs-lookup"><span data-stu-id="4211a-140">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="4211a-141">✔️</span><span class="sxs-lookup"><span data-stu-id="4211a-141">✔️</span></span></td>
        <td><span data-ttu-id="4211a-142">✔️</span><span class="sxs-lookup"><span data-stu-id="4211a-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4211a-143">Acelerômetro</span><span class="sxs-lookup"><span data-stu-id="4211a-143">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="4211a-144">✔️</span><span class="sxs-lookup"><span data-stu-id="4211a-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4211a-145">Giroscópio</span><span class="sxs-lookup"><span data-stu-id="4211a-145">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="4211a-146">✔️</span><span class="sxs-lookup"><span data-stu-id="4211a-146">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4211a-147">Magnetômetro</span><span class="sxs-lookup"><span data-stu-id="4211a-147">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="4211a-148">✔️</span><span class="sxs-lookup"><span data-stu-id="4211a-148">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="4211a-149">Habilitando o modo de pesquisa (primeiro a partir do HoloLens e do HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="4211a-149">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="4211a-150">O modo de pesquisa é uma extensão do modo de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="4211a-150">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="4211a-151">Antes de iniciar, os recursos do desenvolvedor do dispositivo precisam ser habilitados para acessar as configurações do modo de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="4211a-151">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="4211a-152">Abra o **menu iniciar > configurações** e selecione **atualizações**.</span><span class="sxs-lookup"><span data-stu-id="4211a-152">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="4211a-153">Selecione **para desenvolvedores** e habilite o **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="4211a-153">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="4211a-154">Role para baixo e habilite o **Portal de Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="4211a-154">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="4211a-155">Depois que os recursos do desenvolvedor estiverem habilitados, [Conecte-se ao portal do dispositivo](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar os recursos do modo de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="4211a-155">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="4211a-156">Vá para o **sistema > modo de pesquisa** no **portal do dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="4211a-156">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="4211a-157">Selecione **permitir acesso ao fluxo do sensor**.</span><span class="sxs-lookup"><span data-stu-id="4211a-157">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="4211a-158">Reinicie o dispositivo a partir do item de menu de **energia** na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="4211a-158">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="4211a-159">Depois de reiniciar o dispositivo, os aplicativos carregados por meio do portal do **dispositivo** poderão acessar os fluxos do modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4211a-159">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="4211a-160">![Guia modo de pesquisa do portal do dispositivo do HoloLens](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="4211a-160">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="4211a-161">*Janela do modo de pesquisa no portal do dispositivo do HoloLens*</span><span class="sxs-lookup"><span data-stu-id="4211a-161">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4211a-162">O modo de pesquisa para o HoloLens 2 está disponível a partir do Build 19041,1356.</span><span class="sxs-lookup"><span data-stu-id="4211a-162">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="4211a-163">Se você precisar de acesso em uma compilação anterior, Inscreva-se em nosso programa [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) .</span><span class="sxs-lookup"><span data-stu-id="4211a-163">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="4211a-164">Usando dados de sensor em seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="4211a-164">Using sensor data in your apps</span></span>

<span data-ttu-id="4211a-165">Os aplicativos podem acessar os dados de fluxo do sensor da mesma maneira que os fluxos de foto e câmera de vídeo são acessados por meio de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="4211a-165">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="4211a-166">Todas as APIs que funcionam para o desenvolvimento do HoloLens também estão disponíveis no modo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4211a-166">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="4211a-167">Em particular, o aplicativo sabe precisamente onde o HoloLens está no espaço 6DoF em cada tempo de captura do quadro do sensor.</span><span class="sxs-lookup"><span data-stu-id="4211a-167">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="4211a-168">Você pode encontrar aplicativos de exemplo sobre como acessar os vários fluxos do modo de pesquisa, como usar os [intrínsecos e as extrínsecos](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e como registrar fluxos no repositório do [repositório GitHub do HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="4211a-168">You can find sample applications on how to access the various Research Mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="4211a-169">Neste momento, o exemplo HoloLensForCV não funciona no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4211a-169">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="support"></a><span data-ttu-id="4211a-170">Suporte</span><span class="sxs-lookup"><span data-stu-id="4211a-170">Support</span></span>

<span data-ttu-id="4211a-171">Use o Issue [Tracker](https://github.com/Microsoft/HololensForCV/issues) no repositório HoloLensForCV para postar comentários e acompanhar problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="4211a-171">Please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="4211a-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4211a-172">See also</span></span>

* [<span data-ttu-id="4211a-173">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="4211a-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="4211a-174">Repositório GitHub HoloLensForCV</span><span class="sxs-lookup"><span data-stu-id="4211a-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="4211a-175">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="4211a-175">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)

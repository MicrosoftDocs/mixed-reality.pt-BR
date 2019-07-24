---
title: Controle de código QR
description: Saiba como ativar o controle de código QR para seu fone de ouvido (VR) de realidade mista do Windows e implementar o recurso em seus aplicativos VR.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, LBE, entretenimento baseado na localização, VR de los, de los, de imersão, QR, QR Code
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829978"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="d987b-104">Controle de código QR</span><span class="sxs-lookup"><span data-stu-id="d987b-104">QR code tracking</span></span>

<span data-ttu-id="d987b-105">O controle de código QR é implementado no driver do Windows Mixed Reality para headsets de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="d987b-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="d987b-106">Ao habilitar o controlador de código QR no driver Headset, o headset verifica os códigos QR e eles são relatados aos aplicativos interessados.</span><span class="sxs-lookup"><span data-stu-id="d987b-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="d987b-107">Esse recurso só está disponível a partir da [atualização do Windows 10 de outubro de 2018 (também conhecida como RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="d987b-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="d987b-108">Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="d987b-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="d987b-109">Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="d987b-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="d987b-110">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="d987b-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d987b-111"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="d987b-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d987b-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d987b-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d987b-113"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="d987b-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d987b-114">Controle de código QR</span><span class="sxs-lookup"><span data-stu-id="d987b-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="d987b-115">❌</span><span class="sxs-lookup"><span data-stu-id="d987b-115">❌</span></span></td>
        <td><span data-ttu-id="d987b-116">✔️</span><span class="sxs-lookup"><span data-stu-id="d987b-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="d987b-117">Habilitando e desabilitando o controle de código QR para o headset</span><span class="sxs-lookup"><span data-stu-id="d987b-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="d987b-118">Observação: Esta seção só é válida para a [atualização do Windows 10 de outubro de 2018 (também conhecida como RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="d987b-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="d987b-119">Do 19h1 Builds em diante, você não precisará fazer isso.</span><span class="sxs-lookup"><span data-stu-id="d987b-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="d987b-120">Se você estiver desenvolvendo um aplicativo de realidade misturada que aproveitará o controle de código QR, ou se for um cliente de um desses aplicativos, precisará ativar manualmente o controle de código QR no driver do headset.</span><span class="sxs-lookup"><span data-stu-id="d987b-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="d987b-121">Para ativar o **controle de código QR** para seu headset de imersão (VR):</span><span class="sxs-lookup"><span data-stu-id="d987b-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="d987b-122">Feche o aplicativo portal da realidade misturada em seu PC.</span><span class="sxs-lookup"><span data-stu-id="d987b-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="d987b-123">Desconecte o headset do seu PC.</span><span class="sxs-lookup"><span data-stu-id="d987b-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="d987b-124">Execute o seguinte script no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="d987b-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="d987b-125">Reconecte o headset ao seu PC.</span><span class="sxs-lookup"><span data-stu-id="d987b-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="d987b-126">Para desativar o **controle de código QR** para seu headset de imersão (VR):</span><span class="sxs-lookup"><span data-stu-id="d987b-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="d987b-127">Feche o aplicativo portal da realidade misturada em seu PC.</span><span class="sxs-lookup"><span data-stu-id="d987b-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="d987b-128">Desconecte o headset do seu PC.</span><span class="sxs-lookup"><span data-stu-id="d987b-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="d987b-129">Execute o seguinte script no prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="d987b-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="d987b-130">Reconecte o headset ao seu PC.</span><span class="sxs-lookup"><span data-stu-id="d987b-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="d987b-131">Isso fará com que todos os códigos QR descobertos "não localizáveis".</span><span class="sxs-lookup"><span data-stu-id="d987b-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="d987b-132">Códigos de impressão</span><span class="sxs-lookup"><span data-stu-id="d987b-132">Printing codes</span></span>

<span data-ttu-id="d987b-133">Primeiro, a [especificação de códigos QR](https://www.qrcode.com/en/howto/code.html) diz "a área de símbolo de código QR requer uma margem ou" zona silenciosa "em relação a ela a ser usada.</span><span class="sxs-lookup"><span data-stu-id="d987b-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="d987b-134">A margem é uma área clara em um símbolo em que nada é impresso.</span><span class="sxs-lookup"><span data-stu-id="d987b-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="d987b-135">O código QR requer uma margem larga de quatro módulos em todos os lados de um símbolo. "</span><span class="sxs-lookup"><span data-stu-id="d987b-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="d987b-136">Isso precisa ter uma largura, em cada lado, de quatro vezes o tamanho de um módulo, um único quadrado preto no código.</span><span class="sxs-lookup"><span data-stu-id="d987b-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="d987b-137">A página de especificações contém conselhos sobre como imprimir códigos QR e descobrir a área necessária para fazer um determinado código QR de tamanho.</span><span class="sxs-lookup"><span data-stu-id="d987b-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="d987b-138">A qualidade de detecção de código QR no momento é suscetível a uma variação de iluminação e de fundo.</span><span class="sxs-lookup"><span data-stu-id="d987b-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="d987b-139">Para combater isso, Observe sua iluminação e imprima o código apropriado.</span><span class="sxs-lookup"><span data-stu-id="d987b-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="d987b-140">Em uma cena com iluminação particularmente brilhante, imprima um código preto em um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="d987b-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="d987b-141">Em uma cena de pouca luz, o preto em branco funciona.</span><span class="sxs-lookup"><span data-stu-id="d987b-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="d987b-142">Da mesma forma, se o pano de fundo para o código for particularmente escuro, experimente um preto no código cinza se a taxa de detecção for baixa.</span><span class="sxs-lookup"><span data-stu-id="d987b-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="d987b-143">Caso contrário, se o pano de fundo for mais leve, um código regular deverá funcionar bem.</span><span class="sxs-lookup"><span data-stu-id="d987b-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="d987b-144">API QRTracking</span><span class="sxs-lookup"><span data-stu-id="d987b-144">QRTracking API</span></span>

<span data-ttu-id="d987b-145">O plug-in QRTracking expõe as APIs para o controle de código QR.</span><span class="sxs-lookup"><span data-stu-id="d987b-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="d987b-146">Para usar o plug-in, você precisará usar os seguintes tipos do namespace *QRCodesTrackerPlugin* .</span><span class="sxs-lookup"><span data-stu-id="d987b-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="d987b-147">Implementando o controle de código QR no Unity</span><span class="sxs-lookup"><span data-stu-id="d987b-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="d987b-148">Cenas de exemplo do Unity em MRTK (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="d987b-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="d987b-149">Você pode encontrar um exemplo de como usar a API de controle QR no [site GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)do kit de ferramentas de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="d987b-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="d987b-150">O MRTK implementou os scripts necessários para simpilify o uso do controle QR.</span><span class="sxs-lookup"><span data-stu-id="d987b-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="d987b-151">Todos os ativos necessários para desenvolver aplicativos com controle QR estão na pasta "QRTracker".</span><span class="sxs-lookup"><span data-stu-id="d987b-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="d987b-152">Há duas cenas: a primeira é uma amostra para simplesmente mostrar detalhes dos códigos QR conforme eles são detectados e o segundo demonstra como usar o sistema de coordenadas anexado ao código QR para exibir hologramas.</span><span class="sxs-lookup"><span data-stu-id="d987b-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="d987b-153">Há um pré-fabricado "QRScanner" que adicionou todos os scripts necessários aos bastidores para usar o QRCodes.</span><span class="sxs-lookup"><span data-stu-id="d987b-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="d987b-154">O script QRCodeManager é uma classe singleton que implementa a API QRCode.</span><span class="sxs-lookup"><span data-stu-id="d987b-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="d987b-155">Isso precisa ser adicionado à sua cena.</span><span class="sxs-lookup"><span data-stu-id="d987b-155">This needs to be added to your scene.</span></span> <span data-ttu-id="d987b-156">O script "AttachToQRCode" é usado para anexar hologramas aos sistemas de coordenadas de código QR, esse script pode ser adicionado a qualquer um dos seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="d987b-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="d987b-157">O "SpatialGraphCoordinateSystem" mostra como usar o sistema de coordenadas QRCode.</span><span class="sxs-lookup"><span data-stu-id="d987b-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="d987b-158">Esses scripts podem ser usados no estado em que se encontram em seus bastidores de projeto ou você pode escrever seus próprios diretamente usando o plug-in, conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="d987b-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="d987b-159">Implementando o controle de código QR no Unity sem MRTK</span><span class="sxs-lookup"><span data-stu-id="d987b-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="d987b-160">Você também pode usar a API de controle QR no Unity sem usar uma dependência no MRTK.</span><span class="sxs-lookup"><span data-stu-id="d987b-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="d987b-161">Para usar a API, você precisará preparar seu projeto com a seguinte instrução:</span><span class="sxs-lookup"><span data-stu-id="d987b-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="d987b-162">Crie uma nova pasta na pasta ativos do projeto do Unity com o nome: "Plugins".</span><span class="sxs-lookup"><span data-stu-id="d987b-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="d987b-163">Copie todos os arquivos necessários [dessa pasta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) para a pasta "plugins" local que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="d987b-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="d987b-164">Você pode usar os scripts de controle QR na [pasta MRTK scripts](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) ou escrever o seu próprio.</span><span class="sxs-lookup"><span data-stu-id="d987b-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="d987b-165">Observação: Esses plug-ins são apenas para compilações de [atualização do Windows 10 de outubro de 2018 (também conhecidas como RS5)](release-notes-october-2018.md) .</span><span class="sxs-lookup"><span data-stu-id="d987b-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="d987b-166">Os plug-ins serão atualizados com a próxima versão do Windows.</span><span class="sxs-lookup"><span data-stu-id="d987b-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="d987b-167">Os plugins atuais foram experimentais e não funcionarão para versões futuras do Windows.</span><span class="sxs-lookup"><span data-stu-id="d987b-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="d987b-168">Novos plug-ins serão publicados, que podem ser usados na próxima versão do Windows e não serão compatíveis com versões anteriores e não funcionarão com o RS5).</span><span class="sxs-lookup"><span data-stu-id="d987b-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="d987b-169">Implementando o controle de código QR no DirectX</span><span class="sxs-lookup"><span data-stu-id="d987b-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="d987b-170">Para usar o QRTrackingPlugin no Visual Studio, você precisará adicionar a referência de QRTrackingPlugin ao. winmd.</span><span class="sxs-lookup"><span data-stu-id="d987b-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="d987b-171">Você pode encontrar os [arquivos necessários para as plataformas com suporte aqui](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span><span class="sxs-lookup"><span data-stu-id="d987b-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="d987b-172">Obtendo um sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="d987b-172">Getting a coordinate system</span></span>

<span data-ttu-id="d987b-173">Definimos um sistema de coordenadas à direita alinhado com o código QR no canto superior esquerdo do quadrado de detecção rápida na parte superior esquerda.</span><span class="sxs-lookup"><span data-stu-id="d987b-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="d987b-174">O sistema de coordenadas é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="d987b-174">The coordinate system is shown below.</span></span> <span data-ttu-id="d987b-175">O eixo Z está apontando para o papel (não mostrado), mas no Unity o eixo z está fora do papel e da mão esquerda.</span><span class="sxs-lookup"><span data-stu-id="d987b-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="d987b-176">Um SpatialCoordinateSystem é definido e alinhado como mostrado.</span><span class="sxs-lookup"><span data-stu-id="d987b-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="d987b-177">Esse sistema de coordenadas pode ser obtido da plataforma usando as janelas de API *::P erception:: Spatial::P revisar:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*.</span><span class="sxs-lookup"><span data-stu-id="d987b-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="d987b-179">No objeto de código QRCode ^, o código a seguir mostra como criar um retângulo e colocá-lo no sistema de coordenadas QR:</span><span class="sxs-lookup"><span data-stu-id="d987b-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

<span data-ttu-id="d987b-180">Você pode usar o tamanho físico para criar o retângulo QR:</span><span class="sxs-lookup"><span data-stu-id="d987b-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="d987b-181">O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas ao local:</span><span class="sxs-lookup"><span data-stu-id="d987b-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="d987b-182">Totalmente, seu *QRCodesTrackerPlugin:: QRCodeAddedHandler* pode ser semelhante a este:</span><span class="sxs-lookup"><span data-stu-id="d987b-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="d987b-183">Solução de problemas e perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="d987b-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="d987b-184">**Solução de problemas gerais**</span><span class="sxs-lookup"><span data-stu-id="d987b-184">**General troubleshooting**</span></span>

* <span data-ttu-id="d987b-185">Seu PC está executando a atualização do Windows 10 de outubro de 2018?</span><span class="sxs-lookup"><span data-stu-id="d987b-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="d987b-186">Você definiu a chave do registro?</span><span class="sxs-lookup"><span data-stu-id="d987b-186">Have you set the reg key?</span></span> <span data-ttu-id="d987b-187">O dispositivo foi reiniciado depois?</span><span class="sxs-lookup"><span data-stu-id="d987b-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="d987b-188">A versão do código QR é uma versão com suporte?</span><span class="sxs-lookup"><span data-stu-id="d987b-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="d987b-189">A API atual suporta até o código QR versão 20.</span><span class="sxs-lookup"><span data-stu-id="d987b-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="d987b-190">É recomendável usar a versão 5 para uso geral.</span><span class="sxs-lookup"><span data-stu-id="d987b-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="d987b-191">Você está perto o suficiente para o código QR?</span><span class="sxs-lookup"><span data-stu-id="d987b-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="d987b-192">Quanto mais próximo a câmera for o código QR, mais alta será a versão do código QR à qual a API pode dar suporte.</span><span class="sxs-lookup"><span data-stu-id="d987b-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="d987b-193">**Como é preciso ter o código QR para detectá-lo?**</span><span class="sxs-lookup"><span data-stu-id="d987b-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="d987b-194">Isso dependerá do tamanho do código QR e também da versão.</span><span class="sxs-lookup"><span data-stu-id="d987b-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="d987b-195">Para um código QR da versão 1 variando de 5 cm para os lados 25 cm, a distância mínima de detecção varia de 0,15 metros a 0,5 metros.</span><span class="sxs-lookup"><span data-stu-id="d987b-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="d987b-196">Os mais distantes deles podem ser detectados a partir de cerca de 0,3 metros para o código QR menor se destina a 1,4 metros para maior.</span><span class="sxs-lookup"><span data-stu-id="d987b-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="d987b-197">Para códigos QR maiores que isso, você pode estimar; a distância de detecção para o tamanho aumenta linearmente.</span><span class="sxs-lookup"><span data-stu-id="d987b-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="d987b-198">Nosso controlador não funciona com códigos QR com lados menores que 5 cm.</span><span class="sxs-lookup"><span data-stu-id="d987b-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="d987b-199">**Os códigos QR com logotipos funcionam?**</span><span class="sxs-lookup"><span data-stu-id="d987b-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="d987b-200">Códigos QR com logotipos não foram testados e não têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="d987b-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="d987b-201">**Como fazer limpar códigos QR do meu aplicativo para que eles não persistam?**</span><span class="sxs-lookup"><span data-stu-id="d987b-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="d987b-202">Os códigos QR só são persistidos na sessão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d987b-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="d987b-203">Depois que você reinicializar (ou reiniciar o driver), eles serão desfeitos e detectados como novos objetos na próxima vez.</span><span class="sxs-lookup"><span data-stu-id="d987b-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="d987b-204">O histórico de código QR é salvo no nível do sistema na sessão do driver, mas você pode configurar seu aplicativo para ignorar códigos QR mais antigos que um carimbo de data/hora específico, se desejar.</span><span class="sxs-lookup"><span data-stu-id="d987b-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="d987b-205">Atualmente, a API dá suporte à limpeza do histórico de código QR, pois vários aplicativos podem estar interessados nos dados.</span><span class="sxs-lookup"><span data-stu-id="d987b-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="d987b-206">**Os plug-ins para RS5 e versões futuras não são compatíveis** A versão RS5 do plug-in funciona apenas para RS5 e não funcionará para versões futuras.</span><span class="sxs-lookup"><span data-stu-id="d987b-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="d987b-207">O plug-in expermental será substituído pelo plug-in real e deverá ser o que pode ser usado em versões futuras do Windows.</span><span class="sxs-lookup"><span data-stu-id="d987b-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>

---
title: Código QR de acompanhamento
description: Saiba como ativar o código QR de acompanhamento para o Windows Mixed Reality imersivo (VR) fone de ouvido e implementar o recurso em seus aplicativos VR.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, lbe, entretenimento baseados na localização, vr arcade, código qr de arcade, imersivo, qr,
ms.openlocfilehash: b0f4480496c15f811979f76143acbd456d89e249
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59591023"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="9aca0-104">Código QR de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="9aca0-104">QR code tracking</span></span>

<span data-ttu-id="9aca0-105">Código QR de controle é implementado no driver do Windows Mixed Reality para fones imersivos em exposição (VR).</span><span class="sxs-lookup"><span data-stu-id="9aca0-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="9aca0-106">Habilitando o rastreador de código QR no driver fone de ouvido, o fone de ouvido examina os códigos QR e são relatados para aplicativos de seu interessados.</span><span class="sxs-lookup"><span data-stu-id="9aca0-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="9aca0-107">Esse recurso só está disponível desde o [atualização do Windows 10 de outubro de 2018 (também conhecido como RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="9aca0-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="9aca0-108">Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="9aca0-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9aca0-109">Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.</span><span class="sxs-lookup"><span data-stu-id="9aca0-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="9aca0-110">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="9aca0-110">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9aca0-111">Recurso</span><span class="sxs-lookup"><span data-stu-id="9aca0-111">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="9aca0-112"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9aca0-112"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9aca0-113"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="9aca0-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="9aca0-114">Código QR de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="9aca0-114">QR code tracking</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="9aca0-115">✔️</span><span class="sxs-lookup"><span data-stu-id="9aca0-115">✔️</span></span></td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="9aca0-116">Habilitando e desabilitando QR o acompanhamento de fone de ouvido de código</span><span class="sxs-lookup"><span data-stu-id="9aca0-116">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="9aca0-117">Observação: Esta seção só é válida para [atualização do Windows 10 de outubro de 2018 (também conhecido como RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="9aca0-117">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="9aca0-118">Compilações de 19h 1 em diante, não será preciso fazer isso.</span><span class="sxs-lookup"><span data-stu-id="9aca0-118">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="9aca0-119">Se você estiver desenvolvendo um aplicativo de realidade mista que otimizará o código QR de acompanhamento, ou você for um cliente de um desses aplicativos, você precisará ativar manualmente o código QR de acompanhamento no driver do seu fone de ouvido.</span><span class="sxs-lookup"><span data-stu-id="9aca0-119">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="9aca0-120">Para **ativar o código QR de acompanhamento** para imersivo fone de ouvido (VR):</span><span class="sxs-lookup"><span data-stu-id="9aca0-120">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="9aca0-121">Feche o aplicativo do Portal de realidade misturada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="9aca0-121">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="9aca0-122">Desconecte o fone de ouvido do seu computador.</span><span class="sxs-lookup"><span data-stu-id="9aca0-122">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="9aca0-123">Execute o seguinte script no Prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="9aca0-123">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="9aca0-124">Reconecte o fone de ouvido a seu computador.</span><span class="sxs-lookup"><span data-stu-id="9aca0-124">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="9aca0-125">Para **desativar o código QR de acompanhamento** para imersivo fone de ouvido (VR):</span><span class="sxs-lookup"><span data-stu-id="9aca0-125">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="9aca0-126">Feche o aplicativo do Portal de realidade misturada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="9aca0-126">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="9aca0-127">Desconecte o fone de ouvido do seu computador.</span><span class="sxs-lookup"><span data-stu-id="9aca0-127">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="9aca0-128">Execute o seguinte script no Prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="9aca0-128">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="9aca0-129">Reconecte o fone de ouvido a seu computador.</span><span class="sxs-lookup"><span data-stu-id="9aca0-129">Reconnect your headset to your PC.</span></span> <span data-ttu-id="9aca0-130">Isso fará com que todos os códigos QR descobertos "não-localizáveis."</span><span class="sxs-lookup"><span data-stu-id="9aca0-130">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="9aca0-131">Códigos de impressão</span><span class="sxs-lookup"><span data-stu-id="9aca0-131">Printing codes</span></span>

<span data-ttu-id="9aca0-132">Primeiramente, o [especificações para os códigos QR](https://www.qrcode.com/en/howto/code.html) diz "a área de símbolo de código QR exige uma margem ou"zona silenciosa"em torno da ser usado.</span><span class="sxs-lookup"><span data-stu-id="9aca0-132">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="9aca0-133">A margem é uma área clara em torno de um símbolo em que nada é impresso.</span><span class="sxs-lookup"><span data-stu-id="9aca0-133">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="9aca0-134">Código QR requer uma margem de ampla de quatro módulos em todos os lados de um símbolo".</span><span class="sxs-lookup"><span data-stu-id="9aca0-134">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="9aca0-135">Isso deve ter uma largura, em cada lado, de quatro vezes o tamanho de um módulo - um único quadrado preto no código.</span><span class="sxs-lookup"><span data-stu-id="9aca0-135">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="9aca0-136">A página spec contém recomendações sobre como imprimir códigos QR e descobrir a área necessária para fazer um determinado tamanho código QR.</span><span class="sxs-lookup"><span data-stu-id="9aca0-136">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="9aca0-137">Atualmente, qualidade de detecção de código QR é suscetível a iluminação e pano de fundo de variáveis.</span><span class="sxs-lookup"><span data-stu-id="9aca0-137">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="9aca0-138">Para combater isso, observe a iluminação e imprimir o código apropriado.</span><span class="sxs-lookup"><span data-stu-id="9aca0-138">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="9aca0-139">Em uma cena com iluminação particularmente brilhante, imprima um código que é preto em um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="9aca0-139">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="9aca0-140">Em uma cena pouca luz, uma preta sobre branca funciona.</span><span class="sxs-lookup"><span data-stu-id="9aca0-140">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="9aca0-141">Da mesma forma, se o pano de fundo para o código for particularmente escuro, tente um preto no código cinza se a taxa de detecção for baixa.</span><span class="sxs-lookup"><span data-stu-id="9aca0-141">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="9aca0-142">Caso contrário, se o pano de fundo é mais leve, um código regular deve funcionar bem.</span><span class="sxs-lookup"><span data-stu-id="9aca0-142">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="9aca0-143">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="9aca0-143">QRTracking API</span></span>

<span data-ttu-id="9aca0-144">O plug-in QRTracking expõe as APIs de código QR de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="9aca0-144">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="9aca0-145">Para usar o plug-in, você precisará usar os seguintes tipos dos *QRCodesTrackerPlugin* namespace.</span><span class="sxs-lookup"><span data-stu-id="9aca0-145">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="9aca0-146">Implementando o código QR de acompanhamento no Unity</span><span class="sxs-lookup"><span data-stu-id="9aca0-146">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="9aca0-147">Exemplo Unity cenas no MRTK (Toolkit de realidade mista)</span><span class="sxs-lookup"><span data-stu-id="9aca0-147">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="9aca0-148">Você pode encontrar um exemplo de como usar a API de controle de QR no Kit de ferramentas de realidade misturada [site do GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span><span class="sxs-lookup"><span data-stu-id="9aca0-148">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="9aca0-149">MRTK implementou os scripts necessários para simpilify o QR acompanhando o uso.</span><span class="sxs-lookup"><span data-stu-id="9aca0-149">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="9aca0-150">Todos os ativos necessários para desenvolver aplicativos de acompanhamento de QR estão na pasta "QRTracker".</span><span class="sxs-lookup"><span data-stu-id="9aca0-150">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="9aca0-151">Há duas cenas: o primeiro é um exemplo para mostrar apenas os detalhes dos códigos QR conforme eles são detectados e o segundo demonstra como usar o sistema de coordenadas anexado para o código QR para exibir hologramas.</span><span class="sxs-lookup"><span data-stu-id="9aca0-151">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="9aca0-152">Há um pré-fabricado "QRScanner" que adicionado todos os scrips necessários nos bastidores para usar QRCodes.</span><span class="sxs-lookup"><span data-stu-id="9aca0-152">There is a prefab "QRScanner" which added all the necessary scrips to the scenes to use QRCodes.</span></span> <span data-ttu-id="9aca0-153">O script QRCodeManager é uma classe singileton que implementa a API de QRCode, você pode adicioná-lo a você uma cena.</span><span class="sxs-lookup"><span data-stu-id="9aca0-153">The script QRCodeManager is a singileton class that implements the QRCode API you can add it to you scene.</span></span> <span data-ttu-id="9aca0-154">Os scripts "AttachToQRCode" é usado para anexar hologramas aos sistemas coodridnate código QR, esse script pode ser adicionado a qualquer um dos seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="9aca0-154">The scripts "AttachToQRCode" is used to attach holograms to the QR Code coodridnate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="9aca0-155">"SpatialGraphCoordinateSystem" mostra como usar o sistema de coordenadas QRCode.</span><span class="sxs-lookup"><span data-stu-id="9aca0-155">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="9aca0-156">Esses scripts podem ser usados porque está em seu plano de projeto, ou você pode escrever seu próprio diretamente usando o plug-in conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="9aca0-156">These scripts can be used as is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="9aca0-157">Implementando o código QR de acompanhamento no Unity sem MRTK</span><span class="sxs-lookup"><span data-stu-id="9aca0-157">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="9aca0-158">Você também pode usar a API de controle de QR no Unity sem assumir uma dependência MRTK.</span><span class="sxs-lookup"><span data-stu-id="9aca0-158">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="9aca0-159">Para usar a API, você precisará preparar seu projeto com a instrução a seguir:</span><span class="sxs-lookup"><span data-stu-id="9aca0-159">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="9aca0-160">Crie uma nova pasta na pasta ativos do seu projeto do unity com o nome: "Plug-ins".</span><span class="sxs-lookup"><span data-stu-id="9aca0-160">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="9aca0-161">Copie todos os arquivos necessários do [nessa pasta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) na pasta de "Plug-ins" local que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="9aca0-161">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="9aca0-162">Você pode usar o QR acompanhamento scripts na [pasta de scripts MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) ou escreva seu próprio.</span><span class="sxs-lookup"><span data-stu-id="9aca0-162">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="9aca0-163">Observação: Esses plug-ins são apenas para [atualização do Windows 10 de outubro de 2018 (também conhecido como RS5)](release-notes-october-2018.md) compilações.</span><span class="sxs-lookup"><span data-stu-id="9aca0-163">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="9aca0-164">Os plug-ins serão atualizados com a próxima versão do windows.</span><span class="sxs-lookup"><span data-stu-id="9aca0-164">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="9aca0-165">Os plug-ins atuais foram experimentais e não funcionará para uma versão futura do windows.</span><span class="sxs-lookup"><span data-stu-id="9aca0-165">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="9aca0-166">Novos plug-ins serão publicado que pode ser usada da próxima versão do windows e eles não serão retroativamente compatível e não funcionará com RS5).</span><span class="sxs-lookup"><span data-stu-id="9aca0-166">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="9aca0-167">Implementando o código QR de acompanhamento no DirectX</span><span class="sxs-lookup"><span data-stu-id="9aca0-167">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="9aca0-168">Para usar o QRTrackingPlugin no Visual Studio, você precisará adicionar referência do QRTrackingPlugin à. winmd.</span><span class="sxs-lookup"><span data-stu-id="9aca0-168">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="9aca0-169">Você pode encontrar o [os arquivos necessários para as plataformas com suporte aqui](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span><span class="sxs-lookup"><span data-stu-id="9aca0-169">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="9aca0-170">Obtendo um sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="9aca0-170">Getting a coordinate system</span></span>

<span data-ttu-id="9aca0-171">Definimos um sistema de coordenadas à direita alinhado com o código QR no canto superior esquerdo do quadrado detecção rápida no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="9aca0-171">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="9aca0-172">O sistema de coordenadas é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="9aca0-172">The coordinate system is shown below.</span></span> <span data-ttu-id="9aca0-173">O eixo z está apontando no documento de (não mostrado), mas no Unity o eixo z é sem o papel e mão esquerda.</span><span class="sxs-lookup"><span data-stu-id="9aca0-173">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="9aca0-174">Um SpatialCoordinateSystem é definida que está alinhada conforme mostrado.</span><span class="sxs-lookup"><span data-stu-id="9aca0-174">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="9aca0-175">Esse sistema de coordenadas podem ser obtido da plataforma usando a API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span><span class="sxs-lookup"><span data-stu-id="9aca0-175">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Sistema de coordenadas do código QR](images/Qr-coordinatesystem.png) 

<span data-ttu-id="9aca0-177">De QRCode ^ código de objeto, o código a seguir mostra como criar um retângulo e colocá-lo no sistema de coordenadas QR:</span><span class="sxs-lookup"><span data-stu-id="9aca0-177">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="9aca0-178">Você pode usar o tamanho físico para criar o retângulo QR:</span><span class="sxs-lookup"><span data-stu-id="9aca0-178">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="9aca0-179">O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas no local:</span><span class="sxs-lookup"><span data-stu-id="9aca0-179">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="9aca0-180">Completamente, sua *QRCodesTrackerPlugin::QRCodeAddedHandler* pode ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="9aca0-180">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="9aca0-181">Solução de problemas e perguntas Frequentes</span><span class="sxs-lookup"><span data-stu-id="9aca0-181">Troubleshooting and FAQ</span></span>

<span data-ttu-id="9aca0-182">**Solução de problemas gerais**</span><span class="sxs-lookup"><span data-stu-id="9aca0-182">**General troubleshooting**</span></span>

* <span data-ttu-id="9aca0-183">Seu PC está executando o Windows 10 de outubro de 2018 atualizar?</span><span class="sxs-lookup"><span data-stu-id="9aca0-183">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="9aca0-184">Você já definiu a chave do registro?</span><span class="sxs-lookup"><span data-stu-id="9aca0-184">Have you set the reg key?</span></span> <span data-ttu-id="9aca0-185">Reiniciado posteriormente o dispositivo?</span><span class="sxs-lookup"><span data-stu-id="9aca0-185">Restarted the device afterwards?</span></span>
* <span data-ttu-id="9aca0-186">É a versão do código QR em uma versão com suporte?</span><span class="sxs-lookup"><span data-stu-id="9aca0-186">Is the QR code version a supported version?</span></span> <span data-ttu-id="9aca0-187">Atual API dá suporte a até 20 de versão do código QR.</span><span class="sxs-lookup"><span data-stu-id="9aca0-187">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="9aca0-188">É recomendável usar a versão 5 para uso geral.</span><span class="sxs-lookup"><span data-stu-id="9aca0-188">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="9aca0-189">São que você feche suficiente para o código QR?</span><span class="sxs-lookup"><span data-stu-id="9aca0-189">Are you close enough to the QR code?</span></span> <span data-ttu-id="9aca0-190">Quanto mais próximo a câmera é o código QR, maior será a QR versão do código da API pode dar suporte.</span><span class="sxs-lookup"><span data-stu-id="9aca0-190">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="9aca0-191">**Como fechar precisa ser para o código QR para detectá-lo?**</span><span class="sxs-lookup"><span data-stu-id="9aca0-191">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="9aca0-192">Isso dependerá do tamanho do código QR e também qual versão é.</span><span class="sxs-lookup"><span data-stu-id="9aca0-192">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="9aca0-193">Para um código QR de versão 1 varia de lados 5 cm até lados 25 cm, a distância mínima detecção varia de medidores 0,15 aos medidores de 0,5.</span><span class="sxs-lookup"><span data-stu-id="9aca0-193">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="9aca0-194">Mais distantes imediatamente esses podem ser detectados de vai de cerca de 0,3 medidores para os destinos de código QR menores para medidores 1.4 para o maior.</span><span class="sxs-lookup"><span data-stu-id="9aca0-194">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="9aca0-195">Para os códigos QR maiores que isso, você pode estimar; a distância de detecção para o tamanho aumenta linearmente.</span><span class="sxs-lookup"><span data-stu-id="9aca0-195">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="9aca0-196">Nosso rastreador não funciona com os códigos QR com lados menor do que 5 cm.</span><span class="sxs-lookup"><span data-stu-id="9aca0-196">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="9aca0-197">**Fazer os códigos QR com logotipos de trabalho?**</span><span class="sxs-lookup"><span data-stu-id="9aca0-197">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="9aca0-198">Códigos QR com logotipos não foram testados e não têm suportados no momento.</span><span class="sxs-lookup"><span data-stu-id="9aca0-198">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="9aca0-199">**Como posso limpar códigos QR do meu aplicativo para que eles não são mantidas?**</span><span class="sxs-lookup"><span data-stu-id="9aca0-199">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="9aca0-200">Códigos QR somente são persistidos na sessão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="9aca0-200">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="9aca0-201">Depois de reinicializar (ou reiniciar o driver), eles serão passaram e detectados como novos objetos próxima vez.</span><span class="sxs-lookup"><span data-stu-id="9aca0-201">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="9aca0-202">Histórico do código QR é salvo no nível do sistema na sessão de driver, mas você pode configurar seu aplicativo para ignorar os códigos QR com mais de um carimbo de data específico se você quiser.</span><span class="sxs-lookup"><span data-stu-id="9aca0-202">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="9aca0-203">Atualmente a API dá suporte a histórico de código QR de limpeza, como vários aplicativos podem estar interessados nos dados.</span><span class="sxs-lookup"><span data-stu-id="9aca0-203">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="9aca0-204">**Os plug-ins para versões futuras e RS5 não são compatíveis** RS5 verzi o plug-in funciona apenas para RS5 e não funcionará para versões futuras.</span><span class="sxs-lookup"><span data-stu-id="9aca0-204">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="9aca0-205">O plug-in expermental será substituído com o plug-in real e deve ser aquele que podemos usar em futuras versões do windows.</span><span class="sxs-lookup"><span data-stu-id="9aca0-205">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>

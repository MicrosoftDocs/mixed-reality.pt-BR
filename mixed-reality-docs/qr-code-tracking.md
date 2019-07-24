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
# <a name="qr-code-tracking"></a>Controle de código QR

O controle de código QR é implementado no driver do Windows Mixed Reality para headsets de imersão (VR). Ao habilitar o controlador de código QR no driver Headset, o headset verifica os códigos QR e eles são relatados aos aplicativos interessados. Esse recurso só está disponível a partir da [atualização do Windows 10 de outubro de 2018 (também conhecida como RS5)](release-notes-october-2018.md).

>[!NOTE]
>Os trechos de código neste artigo demonstram atualmente o C++uso de/CX em vez de/WinRT em C++conformidade com C + +17, conforme usado no [ C++ modelo de projeto Holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes a C++um projeto/WinRT, embora você precise converter o código.

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Controle de código QR</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Habilitando e desabilitando o controle de código QR para o headset
Observação: Esta seção só é válida para a [atualização do Windows 10 de outubro de 2018 (também conhecida como RS5)](release-notes-october-2018.md). Do 19h1 Builds em diante, você não precisará fazer isso.
Se você estiver desenvolvendo um aplicativo de realidade misturada que aproveitará o controle de código QR, ou se for um cliente de um desses aplicativos, precisará ativar manualmente o controle de código QR no driver do headset.

Para ativar o **controle de código QR** para seu headset de imersão (VR):

1. Feche o aplicativo portal da realidade misturada em seu PC.
2. Desconecte o headset do seu PC.
3. Execute o seguinte script no prompt de comando:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Reconecte o headset ao seu PC.

Para desativar o **controle de código QR** para seu headset de imersão (VR):

1. Feche o aplicativo portal da realidade misturada em seu PC.
2. Desconecte o headset do seu PC.
3. Execute o seguinte script no prompt de comando:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Reconecte o headset ao seu PC. Isso fará com que todos os códigos QR descobertos "não localizáveis".

## <a name="printing-codes"></a>Códigos de impressão

Primeiro, a [especificação de códigos QR](https://www.qrcode.com/en/howto/code.html) diz "a área de símbolo de código QR requer uma margem ou" zona silenciosa "em relação a ela a ser usada. A margem é uma área clara em um símbolo em que nada é impresso. O código QR requer uma margem larga de quatro módulos em todos os lados de um símbolo. " Isso precisa ter uma largura, em cada lado, de quatro vezes o tamanho de um módulo, um único quadrado preto no código. A página de especificações contém conselhos sobre como imprimir códigos QR e descobrir a área necessária para fazer um determinado código QR de tamanho.

A qualidade de detecção de código QR no momento é suscetível a uma variação de iluminação e de fundo. Para combater isso, Observe sua iluminação e imprima o código apropriado. Em uma cena com iluminação particularmente brilhante, imprima um código preto em um plano de fundo cinza. Em uma cena de pouca luz, o preto em branco funciona. Da mesma forma, se o pano de fundo para o código for particularmente escuro, experimente um preto no código cinza se a taxa de detecção for baixa. Caso contrário, se o pano de fundo for mais leve, um código regular deverá funcionar bem.

## <a name="qrtracking-api"></a>API QRTracking

O plug-in QRTracking expõe as APIs para o controle de código QR. Para usar o plug-in, você precisará usar os seguintes tipos do namespace *QRCodesTrackerPlugin* .

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Implementando o controle de código QR no Unity

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Cenas de exemplo do Unity em MRTK (Mixed Reality Toolkit)

Você pode encontrar um exemplo de como usar a API de controle QR no [site GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)do kit de ferramentas de realidade misturada.

O MRTK implementou os scripts necessários para simpilify o uso do controle QR. Todos os ativos necessários para desenvolver aplicativos com controle QR estão na pasta "QRTracker". Há duas cenas: a primeira é uma amostra para simplesmente mostrar detalhes dos códigos QR conforme eles são detectados e o segundo demonstra como usar o sistema de coordenadas anexado ao código QR para exibir hologramas.
Há um pré-fabricado "QRScanner" que adicionou todos os scripts necessários aos bastidores para usar o QRCodes. O script QRCodeManager é uma classe singleton que implementa a API QRCode. Isso precisa ser adicionado à sua cena. O script "AttachToQRCode" é usado para anexar hologramas aos sistemas de coordenadas de código QR, esse script pode ser adicionado a qualquer um dos seus hologramas. O "SpatialGraphCoordinateSystem" mostra como usar o sistema de coordenadas QRCode. Esses scripts podem ser usados no estado em que se encontram em seus bastidores de projeto ou você pode escrever seus próprios diretamente usando o plug-in, conforme descrito acima.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Implementando o controle de código QR no Unity sem MRTK

Você também pode usar a API de controle QR no Unity sem usar uma dependência no MRTK. Para usar a API, você precisará preparar seu projeto com a seguinte instrução:

1. Crie uma nova pasta na pasta ativos do projeto do Unity com o nome: "Plugins".
2. Copie todos os arquivos necessários [dessa pasta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) para a pasta "plugins" local que você acabou de criar.
3. Você pode usar os scripts de controle QR na [pasta MRTK scripts](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) ou escrever o seu próprio.
Observação: Esses plug-ins são apenas para compilações de [atualização do Windows 10 de outubro de 2018 (também conhecidas como RS5)](release-notes-october-2018.md) . Os plug-ins serão atualizados com a próxima versão do Windows. Os plugins atuais foram experimentais e não funcionarão para versões futuras do Windows. Novos plug-ins serão publicados, que podem ser usados na próxima versão do Windows e não serão compatíveis com versões anteriores e não funcionarão com o RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Implementando o controle de código QR no DirectX

Para usar o QRTrackingPlugin no Visual Studio, você precisará adicionar a referência de QRTrackingPlugin ao. winmd. Você pode encontrar os [arquivos necessários para as plataformas com suporte aqui](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).

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

## <a name="getting-a-coordinate-system"></a>Obtendo um sistema de coordenadas

Definimos um sistema de coordenadas à direita alinhado com o código QR no canto superior esquerdo do quadrado de detecção rápida na parte superior esquerda. O sistema de coordenadas é mostrado abaixo. O eixo Z está apontando para o papel (não mostrado), mas no Unity o eixo z está fora do papel e da mão esquerda.

Um SpatialCoordinateSystem é definido e alinhado como mostrado. Esse sistema de coordenadas pode ser obtido da plataforma usando as janelas de API *::P erception:: Spatial::P revisar:: SpatialGraphInteropPreview:: CreateCoordinateSystemForNode*.

![Sistema de coordenadas de código QR](images/Qr-coordinatesystem.png) 

No objeto de código QRCode ^, o código a seguir mostra como criar um retângulo e colocá-lo no sistema de coordenadas QR:

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

Você pode usar o tamanho físico para criar o retângulo QR:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas ao local:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

Totalmente, seu *QRCodesTrackerPlugin:: QRCodeAddedHandler* pode ser semelhante a este:

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

## <a name="troubleshooting-and-faq"></a>Solução de problemas e perguntas frequentes

**Solução de problemas gerais**

* Seu PC está executando a atualização do Windows 10 de outubro de 2018?
* Você definiu a chave do registro? O dispositivo foi reiniciado depois?
* A versão do código QR é uma versão com suporte? A API atual suporta até o código QR versão 20. É recomendável usar a versão 5 para uso geral. 
* Você está perto o suficiente para o código QR? Quanto mais próximo a câmera for o código QR, mais alta será a versão do código QR à qual a API pode dar suporte.  

**Como é preciso ter o código QR para detectá-lo?**

Isso dependerá do tamanho do código QR e também da versão. Para um código QR da versão 1 variando de 5 cm para os lados 25 cm, a distância mínima de detecção varia de 0,15 metros a 0,5 metros. Os mais distantes deles podem ser detectados a partir de cerca de 0,3 metros para o código QR menor se destina a 1,4 metros para maior. Para códigos QR maiores que isso, você pode estimar; a distância de detecção para o tamanho aumenta linearmente. Nosso controlador não funciona com códigos QR com lados menores que 5 cm.

**Os códigos QR com logotipos funcionam?**

Códigos QR com logotipos não foram testados e não têm suporte no momento.

**Como fazer limpar códigos QR do meu aplicativo para que eles não persistam?**

* Os códigos QR só são persistidos na sessão de inicialização. Depois que você reinicializar (ou reiniciar o driver), eles serão desfeitos e detectados como novos objetos na próxima vez.
* O histórico de código QR é salvo no nível do sistema na sessão do driver, mas você pode configurar seu aplicativo para ignorar códigos QR mais antigos que um carimbo de data/hora específico, se desejar. Atualmente, a API dá suporte à limpeza do histórico de código QR, pois vários aplicativos podem estar interessados nos dados.

**Os plug-ins para RS5 e versões futuras não são compatíveis** A versão RS5 do plug-in funciona apenas para RS5 e não funcionará para versões futuras. O plug-in expermental será substituído pelo plug-in real e deverá ser o que pode ser usado em versões futuras do Windows.

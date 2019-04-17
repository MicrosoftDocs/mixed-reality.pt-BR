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
# <a name="qr-code-tracking"></a>Código QR de acompanhamento

Código QR de controle é implementado no driver do Windows Mixed Reality para fones imersivos em exposição (VR). Habilitando o rastreador de código QR no driver fone de ouvido, o fone de ouvido examina os códigos QR e são relatados para aplicativos de seu interessados. Esse recurso só está disponível desde o [atualização do Windows 10 de outubro de 2018 (também conhecido como RS5)](release-notes-october-2018.md).

>[!NOTE]
>Atualmente, os trechos de código neste artigo demonstram o uso de C++/CX em vez de C + + 17 compatíveis C++/WinRT como usado na [ C++ modelo de projeto holographic](creating-a-holographic-directx-project.md).  Os conceitos são equivalentes para um C++projeto de /WinRT, embora você precisará converter o código.

## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td> Código QR de acompanhamento</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Habilitando e desabilitando QR o acompanhamento de fone de ouvido de código
Observação: Esta seção só é válida para [atualização do Windows 10 de outubro de 2018 (também conhecido como RS5)](release-notes-october-2018.md). Compilações de 19h 1 em diante, não será preciso fazer isso.
Se você estiver desenvolvendo um aplicativo de realidade mista que otimizará o código QR de acompanhamento, ou você for um cliente de um desses aplicativos, você precisará ativar manualmente o código QR de acompanhamento no driver do seu fone de ouvido.

Para **ativar o código QR de acompanhamento** para imersivo fone de ouvido (VR):

1. Feche o aplicativo do Portal de realidade misturada em seu computador.
2. Desconecte o fone de ouvido do seu computador.
3. Execute o seguinte script no Prompt de comando:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Reconecte o fone de ouvido a seu computador.

Para **desativar o código QR de acompanhamento** para imersivo fone de ouvido (VR):

1. Feche o aplicativo do Portal de realidade misturada em seu computador.
2. Desconecte o fone de ouvido do seu computador.
3. Execute o seguinte script no Prompt de comando:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Reconecte o fone de ouvido a seu computador. Isso fará com que todos os códigos QR descobertos "não-localizáveis."

## <a name="printing-codes"></a>Códigos de impressão

Primeiramente, o [especificações para os códigos QR](https://www.qrcode.com/en/howto/code.html) diz "a área de símbolo de código QR exige uma margem ou"zona silenciosa"em torno da ser usado. A margem é uma área clara em torno de um símbolo em que nada é impresso. Código QR requer uma margem de ampla de quatro módulos em todos os lados de um símbolo". Isso deve ter uma largura, em cada lado, de quatro vezes o tamanho de um módulo - um único quadrado preto no código. A página spec contém recomendações sobre como imprimir códigos QR e descobrir a área necessária para fazer um determinado tamanho código QR.

Atualmente, qualidade de detecção de código QR é suscetível a iluminação e pano de fundo de variáveis. Para combater isso, observe a iluminação e imprimir o código apropriado. Em uma cena com iluminação particularmente brilhante, imprima um código que é preto em um plano de fundo cinza. Em uma cena pouca luz, uma preta sobre branca funciona. Da mesma forma, se o pano de fundo para o código for particularmente escuro, tente um preto no código cinza se a taxa de detecção for baixa. Caso contrário, se o pano de fundo é mais leve, um código regular deve funcionar bem.

## <a name="qrtracking-api"></a>QRTracking API

O plug-in QRTracking expõe as APIs de código QR de acompanhamento. Para usar o plug-in, você precisará usar os seguintes tipos dos *QRCodesTrackerPlugin* namespace.

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Implementando o código QR de acompanhamento no Unity

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Exemplo Unity cenas no MRTK (Toolkit de realidade mista)

Você pode encontrar um exemplo de como usar a API de controle de QR no Kit de ferramentas de realidade misturada [site do GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).

MRTK implementou os scripts necessários para simpilify o QR acompanhando o uso. Todos os ativos necessários para desenvolver aplicativos de acompanhamento de QR estão na pasta "QRTracker". Há duas cenas: o primeiro é um exemplo para mostrar apenas os detalhes dos códigos QR conforme eles são detectados e o segundo demonstra como usar o sistema de coordenadas anexado para o código QR para exibir hologramas.
Há um pré-fabricado "QRScanner" que adicionado todos os scrips necessários nos bastidores para usar QRCodes. O script QRCodeManager é uma classe singileton que implementa a API de QRCode, você pode adicioná-lo a você uma cena. Os scripts "AttachToQRCode" é usado para anexar hologramas aos sistemas coodridnate código QR, esse script pode ser adicionado a qualquer um dos seus hologramas. "SpatialGraphCoordinateSystem" mostra como usar o sistema de coordenadas QRCode. Esses scripts podem ser usados porque está em seu plano de projeto, ou você pode escrever seu próprio diretamente usando o plug-in conforme descrito acima.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Implementando o código QR de acompanhamento no Unity sem MRTK

Você também pode usar a API de controle de QR no Unity sem assumir uma dependência MRTK. Para usar a API, você precisará preparar seu projeto com a instrução a seguir:

1. Crie uma nova pasta na pasta ativos do seu projeto do unity com o nome: "Plug-ins".
2. Copie todos os arquivos necessários do [nessa pasta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) na pasta de "Plug-ins" local que você acabou de criar.
3. Você pode usar o QR acompanhamento scripts na [pasta de scripts MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) ou escreva seu próprio.
Observação: Esses plug-ins são apenas para [atualização do Windows 10 de outubro de 2018 (também conhecido como RS5)](release-notes-october-2018.md) compilações. Os plug-ins serão atualizados com a próxima versão do windows. Os plug-ins atuais foram experimentais e não funcionará para uma versão futura do windows. Novos plug-ins serão publicado que pode ser usada da próxima versão do windows e eles não serão retroativamente compatível e não funcionará com RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Implementando o código QR de acompanhamento no DirectX

Para usar o QRTrackingPlugin no Visual Studio, você precisará adicionar referência do QRTrackingPlugin à. winmd. Você pode encontrar o [os arquivos necessários para as plataformas com suporte aqui](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).

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

Definimos um sistema de coordenadas à direita alinhado com o código QR no canto superior esquerdo do quadrado detecção rápida no canto superior esquerdo. O sistema de coordenadas é mostrado abaixo. O eixo z está apontando no documento de (não mostrado), mas no Unity o eixo z é sem o papel e mão esquerda.

Um SpatialCoordinateSystem é definida que está alinhada conforme mostrado. Esse sistema de coordenadas podem ser obtido da plataforma usando a API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.

![Sistema de coordenadas do código QR](images/Qr-coordinatesystem.png) 

De QRCode ^ código de objeto, o código a seguir mostra como criar um retângulo e colocá-lo no sistema de coordenadas QR:

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

O sistema de coordenadas pode ser usado para desenhar o código QR ou anexar hologramas no local:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

Completamente, sua *QRCodesTrackerPlugin::QRCodeAddedHandler* pode ter esta aparência:

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

## <a name="troubleshooting-and-faq"></a>Solução de problemas e perguntas Frequentes

**Solução de problemas gerais**

* Seu PC está executando o Windows 10 de outubro de 2018 atualizar?
* Você já definiu a chave do registro? Reiniciado posteriormente o dispositivo?
* É a versão do código QR em uma versão com suporte? Atual API dá suporte a até 20 de versão do código QR. É recomendável usar a versão 5 para uso geral. 
* São que você feche suficiente para o código QR? Quanto mais próximo a câmera é o código QR, maior será a QR versão do código da API pode dar suporte.  

**Como fechar precisa ser para o código QR para detectá-lo?**

Isso dependerá do tamanho do código QR e também qual versão é. Para um código QR de versão 1 varia de lados 5 cm até lados 25 cm, a distância mínima detecção varia de medidores 0,15 aos medidores de 0,5. Mais distantes imediatamente esses podem ser detectados de vai de cerca de 0,3 medidores para os destinos de código QR menores para medidores 1.4 para o maior. Para os códigos QR maiores que isso, você pode estimar; a distância de detecção para o tamanho aumenta linearmente. Nosso rastreador não funciona com os códigos QR com lados menor do que 5 cm.

**Fazer os códigos QR com logotipos de trabalho?**

Códigos QR com logotipos não foram testados e não têm suportados no momento.

**Como posso limpar códigos QR do meu aplicativo para que eles não são mantidas?**

* Códigos QR somente são persistidos na sessão de inicialização. Depois de reinicializar (ou reiniciar o driver), eles serão passaram e detectados como novos objetos próxima vez.
* Histórico do código QR é salvo no nível do sistema na sessão de driver, mas você pode configurar seu aplicativo para ignorar os códigos QR com mais de um carimbo de data específico se você quiser. Atualmente a API dá suporte a histórico de código QR de limpeza, como vários aplicativos podem estar interessados nos dados.

**Os plug-ins para versões futuras e RS5 não são compatíveis** RS5 verzi o plug-in funciona apenas para RS5 e não funcionará para versões futuras. O plug-in expermental será substituído com o plug-in real e deve ser aquele que podemos usar em futuras versões do windows.

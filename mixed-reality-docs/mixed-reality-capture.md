---
title: Captura de realidade mista
description: Informações sobre como usar a captura de realidade misturada.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: MRC, captura de realidade mista, fotos, vídeo, câmera, captura, uso, fluxo, transmissão ao vivo, demonstração
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694508"
---
# <a name="mixed-reality-capture"></a>Captura de realidade mista

O HoloLens dá aos usuários a experiência de misturar o mundo real com o mundo digital. A MRC (Mixed Reality Capture) permite que você capture essa experiência como uma fotografia ou um vídeo. Isso permite que você compartilhe a experiência com outras pessoas, permitindo que elas vejam os hologramas à medida que você vê-las. Esses vídeos e fotos são de um ponto de vista de primeira pessoa. Para um ponto de vista de terceira pessoa, use a [exibição Spectator](spectator-view.md).

Casos de uso para a captura de realidade misturada vão além do compartilhamento de vídeos entre um círculo social. Vídeos podem ser usados para instruir outras pessoas sobre como usar um aplicativo. Os desenvolvedores podem usar vídeos ou ainda para melhorar as etapas de reprodução e depurar experiências de aplicativo.

## <a name="live-streaming-from-hololens"></a>Transmissão ao vivo do HoloLens

A [atualização do Windows 10 de outubro de 2018](release-notes-october-2018.md) adiciona suporte a Miracast ao HoloLens. Selecione o botão **conectar** na parte inferior do menu Iniciar para abrir um seletor para dispositivos e adaptadores habilitados para Miracast. Selecione o dispositivo para o qual você deseja iniciar o streaming. Quando terminar, selecione o  botão desconectar na parte inferior do menu iniciar.  **Conectar** e **Desconectar** também estão disponíveis no menu ações rápidas.

O [portal do dispositivo do Windows](using-the-windows-device-portal.md) e o [aplicativo Microsoft HoloLens Companion](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) expõem opções de transmissão ao vivo para dispositivos que estão no modo de desenvolvedor.

O Dynamic [Assist do Dynamics 365](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist) dá suporte à transmissão ao vivo do HoloLens para funcionários em locais remotos.

## <a name="taking-mixed-reality-captures"></a>Fazendo capturas de realidade misturada

![Clique no ícone da câmera na parte inferior do menu iniciar](images/cameraiconinpins-300px.png)<br>
*Clique no ícone da câmera na parte inferior do menu iniciar*

Há várias maneiras de iniciar uma captura de realidade misturada:
* O Cortana pode ser usado sempre, independentemente do aplicativo em execução no momento. Apenas digamos, "Ei Cortana, tirar uma foto" ou "Ei Cortana, iniciar a gravação". Para interromper um vídeo, diga "Ei Cortana, parar a gravação".
* No menu Iniciar, selecione **câmera** ou **vídeo**. Use o [Air-toque](gestures.md#air-tap) para abrir a interface do usuário da câmera da MRC interna.
* No menu ações rápidas, selecione **câmera** ou **vídeo** para abrir a interface do usuário da câmera da MRC interna.
* Os aplicativos são capazes de expor sua própria interface do usuário para a captura de realidade misturada usando Custom ou, a partir da [atualização do Windows 10 de outubro de 2018](release-notes-october-2018.md), [interface do usuário da câmera da MRC interna](mixed-reality-capture-for-developers.md).
* Exclusivo para o HoloLens: 
    * O [portal do dispositivo Windows](using-the-windows-device-portal.md) tem uma página de captura de realidade misturada que pode ser usada para tirar fotos, vídeos, transmissão ao vivo e exibir capturas.
    * Pressione os botões **volume up** e **volume down** simultaneamente para tirar uma foto, independentemente do aplicativo em execução no momento.
    * Segure os botões **volume up** e **volume down** por três segundos para começar a gravar um vídeo. Para interromper um vídeo, toque nos botões **volume up** e **volume down** simultaneamente.
* Únicos a headsets de imersão: 
    * Usando um controlador de movimento, mantenha o botão do **Windows** pressionado e, em seguida, toque no **gatilho** para tirar uma foto. 
    * Usando um controlador de movimento, mantenha o botão do **Windows** pressionado e, em seguida, toque no botão de **menu** para iniciar a gravação do vídeo. Mantenha o botão do **Windows** pressionado e, em seguida, toque no **gatilho** para parar de gravar o vídeo.
    
>[!NOTE]
>A [atualização do Windows 10 de outubro de 2018](release-notes-october-2018.md) muda a forma como o botão de cair e do Windows se comporta. Antes da atualização, o botão de gesto de cair ou do Windows interromperia a gravação. Após a atualização, o gesto de cair ou o botão do Windows abrirá o menu iniciar (ou o menu ações rápidas se você estiver em um aplicativo). No menu, selecione **parar vídeo** para interromper a gravação.

### <a name="limitations-of-mixed-reality-capture"></a>Limitações da captura de realidade misturada

No HoloLens, o sistema limitará a taxa de renderização a 30Hz. Isso cria algum espaço para que a MRC seja executada para que o aplicativo não precise manter uma reserva de orçamento constante e também corresponda à taxa de quadros de gravação de vídeo da MRC de (até) 30fps.

Os vídeos têm um comprimento máximo de cinco minutos.

A interface do usuário da câmera da MRC interna dá suporte apenas a uma única operação da MRC por vez (tirar uma imagem é mutuamente exclusiva de gravar um vídeo).

### <a name="file-formats"></a>Formatos de arquivo

A realidade misturada captura os comandos de voz do Cortana e as ferramentas do menu iniciar criam arquivos nos seguintes formatos:

|  type  |  Formatar  |  Extensão  |  Resolução  |  Áudio | 
|----------|----------|----------|----------|----------|
|  Fotografia  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px (headsets de imersão) |  N/D | 
|  Vídeo  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920x1080px em 30fps (HoloLens 2)<br> 1216x684px em 24fps (HoloLens)<br> 1632x918px em 30fps (headsets de imersão) |  Estéreo de 48kHz | 

>[!NOTE]
>A resolução de fotos e vídeos pode ser menor se a câmera de foto/vídeo já estiver em uso por outro aplicativo, enquanto a transmissão ao vivo ou quando os recursos do sistema estão baixos.

### <a name="video-stabilization"></a>Estabilização de vídeo

Por padrão:
* A estabilização de vídeo de latência zero é aplicada quando a transmissão ao vivo sobre Miracast.
* A estabilização de vídeo de latência longa é aplicada aos vídeos capturados usando a interface do usuário da câmera da MRC interna, os comandos de voz da Cortana e o portal de dispositivo do Windows.

## <a name="viewing-mixed-reality-captures"></a>Exibindo capturas de realidade misturada

A realidade mista captura fotos e vídeos são salvos na pasta "rolo de câmera" do dispositivo. Eles podem ser acessados por meio do [aplicativo de fotos](see-your-photos.md#photos-app) ou explorador de arquivos.

Em um PC conectado ao HoloLens, você também pode usar o [portal de dispositivo do Windows](using-the-windows-device-portal.md#mixed-reality-capture) ou o explorador de arquivos do seu PC ([via MTP](release-notes-april-2018.md#new-features-for-hololens)).

Se você instalar o [aplicativo do onedrive](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), poderá ativar o **carregamento da câmera** e suas fotos e vídeos da MRC serão sincronizados com o onedrive e seus outros dispositivos usando o onedrive.

>[!NOTE]
>A partir da atualização do Windows 10 de abril de 2018, o aplicativo de fotos não carregará mais suas fotos e vídeos no OneDrive.

## <a name="see-also"></a>Consulte também
* [Modo de exibição Espectador](spectator-view.md)
* [Câmera localizável](locatable-camera.md)
* [Captura de realidade misturada para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Ver suas fotos](see-your-photos.md)
* [Como usar o Portal de Dispositivos do Windows](using-the-windows-device-portal.md)

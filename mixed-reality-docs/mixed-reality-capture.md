---
title: Captura de realidade mista
description: Informações sobre como usar a captura de realidade misturada.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: MRC, misturadas captura realidade, fotos, vídeo, câmera, captura, uso, fluxo, transmissão ao vivo, demonstração
ms.openlocfilehash: 18a80083bd25974905874c6c2ec0de87dc7424ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590823"
---
# <a name="mixed-reality-capture"></a>Captura de realidade mista

HoloLens oferece aos usuários a experiência de mistura do mundo real com o mundo digital. Captura de realidade misturada (MRC) permitem que você capture essa experiência como uma fotografia ou um vídeo. Isso permite que você compartilhe a experiência com outras pessoas, permitindo que eles vejam as hologramas conforme você vê-los. Tais fotos e vídeos são de um ponto de vista de primeira pessoa. Para o ponto de vista da terceira pessoa, use [exibição spectator](spectator-view.md).

Casos de uso para a captura de realidade misturada vão além de compartilhar vídeos entre um círculo social. Vídeos podem ser usados para instruir a outras pessoas sobre como usar um aplicativo. Os desenvolvedores podem usar vídeos ou ainda pode melhorar as etapas de reprodução e depurar experiências de aplicativo.

## <a name="live-streaming-from-hololens"></a>Transmissão do HoloLens ao vivo

O [atualização do Windows 10 de outubro de 2018](release-notes-october-2018.md) adiciona o suporte do Miracast para o HoloLens. Selecione o **Connect** botão na parte inferior do menu Iniciar para abrir um seletor para dispositivos habilitados para Miracast e adaptadores. Selecione o dispositivo ao qual você deseja iniciar o streaming. Quando terminar, selecione a **desconectar** botão na parte inferior do menu Iniciar.  **Conectar-se** e **desconectar** também estão disponíveis no menu Ações rápidas. 

O [Windows Device Portal](using-the-windows-device-portal.md) expõe live opções de streaming para dispositivos que estão no modo de desenvolvedor.

## <a name="taking-mixed-reality-captures"></a>Levando a realidade misturada captura

![Clique no ícone da câmera na parte inferior do menu Iniciar](images/cameraiconinpins-300px.png)<br>
*Clique no ícone da câmera na parte inferior do menu Iniciar*

Há várias maneiras de iniciar uma captura de realidade mista:
* Cortana pode ser usado em todos os momentos, independentemente do aplicativo em execução no momento. Simplesmente dizer: "Ei Cortana, tirar uma foto" ou "Ei Cortana, inicie a gravação." Para interromper um vídeo, dizer "Ei Cortana, interromper a gravação."
* No menu Iniciar, selecione **câmera** ou **vídeo**. Use [polegar](gestures.md#air-tap) para abrir a câmera MRC interna da interface do usuário.
* No menu Ações rápidas, selecione **câmera** ou **vídeo** para abrir a câmera MRC interna da interface do usuário.
* Aplicativos são capazes de expor seu próprios da interface do usuário para a captura de realidade misturada usando personalizado ou, desde o [atualização do Windows 10 de outubro de 2018](release-notes-october-2018.md), [câmera interna de MRC da interface do usuário](mixed-reality-capture-for-developers.md).
* Exclusivo para o HoloLens: 
    * [Windows Device Portal](using-the-windows-device-portal.md) tem uma página de captura de realidade mista que pode ser usada para tirar fotos, vídeos, transmissão ao vivo e exibir capturas.
    * Pressione ambas as **aumentar volume** e **Diminuir volume** botões simultaneamente para tirar uma foto, independentemente do aplicativo em execução no momento.
    * Mantenha os **aumentar volume** e **Diminuir volume** botões para três segundos iniciar a gravação de um vídeo. Para interromper um vídeo, toque em ambos **aumentar volume** e **Diminuir volume** botões simultaneamente.
* Exclusivo para imersivo headsets: 
    * Usando um controlador de movimento, mantenha o **Windows** botão e, em seguida, toque o **gatilho** para tirar uma foto. 
    * Usando um controlador de movimento, mantenha o **Windows** botão e, em seguida, toque o **menu** botão para iniciar a gravação de vídeo. Mantenha os **Windows** botão e, em seguida, toque o **gatilho** Parar gravação de vídeo.
    
>[!NOTE]
>O [atualização do Windows 10 de outubro de 2018](release-notes-october-2018.md) altera o comportamento de bloom e o botão do Windows. Antes da atualização, o botão de Windows ou um gesto de bloom seria parar a gravação. Após a atualização, o gesto de bloom ou no botão Windows abre o menu Iniciar (ou o menu de ações rápidas se você estiver em um aplicativo). No menu, selecione **Stop vídeo** para interromper a gravação.

### <a name="limitations-of-mixed-reality-capture"></a>Limitações da captura de realidade misturada

Em HoloLens, o sistema limitará a taxa de processamento para 30Hz. Isso cria alguns sobra para MRC ser executado para que o aplicativo não precisa manter uma reserva de orçamento constante e também corresponde a taxa de quadros MRC gravação de vídeo de 30fps.

Vídeos de ter um comprimento máximo de cinco minutos.

A câmera MRC interna da interface do usuário só dá suporte a uma única operação MRC por vez (tirar uma foto é mutuamente exclusivo de gravar um vídeo).

### <a name="file-formats"></a>Formatos de arquivo

Captura de realidade misturada de comandos de voz Cortana e ferramentas do Menu Iniciar criam arquivos nos seguintes formatos:

|  Tipo  |  Formatar  |  Extensão  |  Resolução  |  Áudio | 
|----------|----------|----------|----------|----------|
|  Fotografia  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  1408x792px 1920x1080px<br>tamanho (HoloLens) (fones Imersivos em exposição) |  N/D | 
|  Vídeo  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1408x792px 1632x918px (HoloLens) (fones Imersivos em exposição) |  48kHz estéreo | 

## <a name="viewing-mixed-reality-captures"></a>Exibindo a realidade misturada captura

Realidade misturada captura fotos e vídeos são salvos "Rolo da câmera" pasta do dispositivo. Eles podem ser acessados por meio de [aplicativo fotos](see-your-photos.md#photos-app) ou Explorador de arquivos.

Em um PC conectado ao HoloLens, você também pode usar [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture) ou o Explorador de arquivos do seu PC ([por meio da consulta MTP](release-notes-april-2018.md#new-features-for-hololens)).

Se você instalar o [aplicativo OneDrive](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), você pode ativar **upload da câmera,** e suas MRC fotos e vídeos serão sincronizados com o OneDrive e outros dispositivos usando o OneDrive.

>[!NOTE]
>A partir do Windows 10 de abril de 2018 Update, o aplicativo de fotos não carregará suas fotos e vídeos no OneDrive.

## <a name="see-also"></a>Consulte também
* [Modo de exibição spectator](spectator-view.md)
* [Câmera localizáveis](locatable-camera.md)
* [Misto captura realidade para desenvolvedores](mixed-reality-capture-for-developers.md)
* [Ver suas fotos](see-your-photos.md)
* [Usando o Windows Device Portal](using-the-windows-device-portal.md)

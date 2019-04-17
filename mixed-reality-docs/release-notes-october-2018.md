---
title: Notas de versão – outubro de 2018
description: HoloLens e notas de versão de realidade mista do Windows para o Windows 10 de outubro de 2018 atualizam (também conhecido como RS5).
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: anotações, versão, windows 10, compilação, rs5, sistema operacional de versão
ms.openlocfilehash: 9838b4dcbdedc4bf2c94a8e31f3f8eb4c9634d36
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590829"
---
# <a name="release-notes---october-2018"></a>Notas de versão – outubro de 2018

O **[atualização do Windows 10 de outubro de 2018](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (também conhecido como RS5) inclui novos recursos para o HoloLens e o Windows Mixed Reality fones imersivos em exposição conectado aos computadores. 

Para atualizar para a versão mais recente em HoloLens ou PC (para Windows Mixed Reality fones imersivos (VR) em exposição), abra o **as configurações** aplicativo, vá para **atualização e segurança**, em seguida, selecione o **verificar atualizações** botão. Em um computador Windows 10, você também pode instalar manualmente o Windows 10 de outubro de 2018 atualizar usando o [ferramenta de criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

**Versão mais recente para a área de trabalho:** Atualização do Windows 10 de outubro de 2018 (**10.0.17763.107**)<br>
**Versão mais recente do HoloLens:** Atualização do Windows 10 de outubro de 2018 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Novos recursos para fones imersivos em exposição realidade mista do Windows

O Windows 10 de outubro de 2018 atualização inclui muitos aprimoramentos para o uso de fones de ouvido Windows Mixed Reality de imersão (VR) com seu computador.

### <a name="for-everyone"></a>Para todos

* **Misto realidade lanterna** - abrir um portal para o mundo real para localizar seu teclado, consulte alguém próximos ou dar uma olhada no seu ambiente sem remover o fone de ouvido! Você pode ativar lanterna de realidade mista do menu Iniciar, pressione Windows + captura em seu controlador de animação, ou dizendo "Lanterna liga/desliga". Aponte seu controlador na direção do que você deseja ver como o uso de uma lanterna no escuro.

    ![Realidade misturada lanterna](images/mr-flashlight.png)

* **Novos aplicativos e maneiras de inicializar o conteúdo a realidade misturada inicial**
    * Se você estiver usando [Windows Mixed Reality para SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality), seus títulos SteamVR agora aparecem no menu Iniciar e dos inicializadores de aplicativo para cada um podem ser colocados na realidade misturada inicial.
    
        ![SteamVR dos inicializadores de aplicativo](images/steamvr-launchers.png)
        
    * Novos *360 vídeos* aplicativo para a descoberta de uma seleção de curadoria regularmente de vídeos de 360 graus.
    * Novos *WebVR Showcase* experiências de aplicativo para a descoberta de uma seleção de curadoria regularmente de WebVR.
    * Os clientes do Windows Mixed Reality pela primeira vez entra o Cliff House e encontre que ele previamente preenchido com inicializadores de aplicativos 3D para alguns dos nossos aplicativos imersivos Favoritos e jogos desde o Microsoft Store.
    * Windows do Microsoft Edge agora incluem um *compartilhamento* botão.
* **Menu de ações rápidas** -de dentro de um aplicativo de realidade misturada envolvente, você pode pressionar o botão do Windows para acessar um novo menu de ações rápidas, com acesso fácil aos *menu SteamVR*, *captura de foto e vídeo*, *lanterna*, e *doméstica*.
* **Suporte para mochila PCs** -Windows Mixed Reality fones imersivos em exposição (VR) é executado na mochila PCs sem a necessidade de um emulador de exibição após a conclusão da instalação.
* **Novos recursos de áudio** -agora você pode espelhar o áudio de uma experiência de realidade mista do Windows para a tomada de áudio (ou fones de ouvido) o Headset *e* um dispositivo de áudio conectado ao seu computador (como alto-falantes externos). Também adicionamos um indicador visual para o nível de volume na exibição do seu fone de ouvido.
* **Outras melhorias**
    * Atualizações do Portal realidade mistas agora são entregues por meio da Microsoft Store, habilitando as atualizações mais rápidas entre as versões principais do Windows. Observe que isso se aplica somente ao aplicativo da área de trabalho e a experiência de headset de realidade mista do Windows ainda atualiza com o sistema operacional. 
    * Quando headsets entra em suspensão, aplicativos de realidade mista do Windows são suspensos, em vez de finalizado (até o Portal de realidade mista é fechado).
    
### <a name="for-developers"></a>Para desenvolvedores

* **[Código QR de acompanhamento](qr-code-tracking.md)**  -código QR de habilitar o rastreamento em seu aplicativo de realidade misturada, permitindo que o Windows Mixed Reality fones imersivos (VR) em exposição examinar códigos QR e relatá-los de volta para aplicativos de seu interessados.
* **Suporte a hardware DRM para aplicativos imersivos** – os desenvolvedores podem texturas de buffer de fundo hardware protegido de solicitação agora se compatível com o hardware de vídeo, permitindo que os aplicativos usar conteúdo protegido por hardware de fontes como o PlayReady.
* **[Integrar a captura de realidade misturada da interface do usuário em aplicativos imersivos](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)**  – os desenvolvedores podem integrar a captura de realidade misturada em seus aplicativos usando o Windows internas [captura com câmera da interface do usuário](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) com apenas algumas linhas de código.

## <a name="new-features-for-hololens"></a>Novos recursos para o HoloLens

O Windows 10 de outubro de 2018 atualização está disponível publicamente para todos os clientes do HoloLens e inclui uma série de aprimoramentos, como:

### <a name="for-everyone"></a>Para todos

* **Menu de ações rápidas** -de dentro de um aplicativo de realidade misturada envolvente, você pode pressionar o botão do Windows para acessar um novo menu de ações rápidas, com acesso fácil aos *Iniciar gravação de vídeo*, *tirar fotos*, *Página inicial de realidade mista*, *alterar volume*, e *Connect*.
* **Captura de vídeo de início/parada do início ou no menu Ações rápidas** -se você iniciar a captura de vídeo do menu Iniciar ou menu Ações rápidas, você poderá interromper a gravação do mesmo local. (Não se esqueça, você pode sempre fazer isso com comandos de voz muito.)
* **Projeto para um dispositivo habilitado para Miracast** -conteúdo da HoloLens para um dispositivo de superfície próximo ou TV/monitor de projeto se usando um adaptador ou exibição habilitados para Miracast.
* **Novas notificações** -modo de exibição e a responder a notificações sobre HoloLens, exatamente como faria em um PC.  
* **Sobreposições útil em aplicativos de realidade misturada envolvente** -agora, você verá as sobreposições, como o teclado, caixas de diálogo, o seletor de arquivos, aplicativos de realidade mista do etc. ao usar imersivos.
* **Indicador visual para alteração de volume** - quando você usar o volume de backup de/para baixo de botões em seu HoloLens, você verá um indicador visual de nível de volume em que o fone de ouvido.
* **Novos elementos visuais para inicialização de dispositivo** -um indicador de carregamento foi adicionado durante o processo de inicialização para fornecer comentários visuais que o sistema está sendo carregada.
* **Próximo compartilhamento** -experiência a compartilhar mais próximos do Windows permite que você compartilhe uma captura com um dispositivo Windows próximo.  
* **Compartilhamento do Microsoft Edge** – Microsoft Edge agora inclui um *compartilhamento* botão. 

### <a name="for-developers"></a>Para desenvolvedores

* **[Integrar a captura de realidade misturada da interface do usuário em aplicativos imersivos](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)**  – os desenvolvedores podem integrar a captura de realidade misturada em seus aplicativos usando o Windows internas [captura com câmera da interface do usuário](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) com apenas algumas linhas de código.

### <a name="for-commercial-customers"></a>Para clientes comerciais

* **Habilitar o provisionamento de pós-instalação** -agora você pode aplicar um pacote de provisionamento a qualquer momento usando as configurações de tempo de execução.
* **Acesso atribuído com grupos do Azure AD** -agora você pode usar grupos do Azure AD para a configuração do Windows o acesso atribuído para definir a configuração de quiosque único ou vários aplicativos.
* **FIXAR entrar no comutador de perfil da tela de entrada** -PIN entrar agora está disponível para "Outro usuário" na tela de entrada. 
* **Entrar com o provedor de credenciais da Web usando a senha** -agora você pode selecionar o ícone de globo para iniciar a entrada na web com a sua senha. 
* **Ler informações de hardware do dispositivo por meio do MDM** -os administradores de TI podem ver e controlar o HoloLens pelo número de série do dispositivo no seu console do MDM.
* **Definir nome do dispositivo HoloLens por meio do MDM (Renomear)** -os administradores de TI podem ver e renomear dispositivos HoloLens no seu console do MDM.

### <a name="for-international-customers"></a>Para clientes internacionais

Agora você pode usar o HoloLens com interface do usuário localizada para chinês simplificado ou japonês, incluindo teclado em Pinyin, ditado, texto em fala (TTS) e comandos de voz.

## <a name="known-issues"></a>Problemas conhecidos

Trabalhamos muito para fornecer uma ótima experiência de realidade mista do Windows, mas estamos ainda estiver acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, por favor [envie seus comentários](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Após a atualização
Você pode observar os seguintes problemas ao usando o Windows 10 de outubro de 2018 atualização em seu HoloLens:
* **Aplicativos podem terminar em loop de entrada quando iniciado a partir de uma notificação** – alguns aplicativos que exigem a entrada podem end-up em um sinal em loop infinito quando iniciado a partir de uma notificação. Por exemplo, isso pode ocorrer depois de instalar o aplicativo de Portal da empresa Microsoft da Microsoft Store e iniciá-lo a notificação de conclusão da instalação.
* **Página de entrada do aplicativo pode ser executadas com uma página em branco** – em alguns casos, quando uma solicitação de conexão mostra ao longo do seu aplicativo, a página de entrada não fecha e em vez disso, mostra uma página (preta) em branco após a conclusão. Você pode fechar a página em branco ou movê-la para revelar o aplicativo abaixo. Por exemplo, isso pode acontecer durante o registro de MDM do aplicativo configurações ao entrar. 

## <a name="provide-feedback-and-report-issues"></a>Fornecer comentários e relate problemas

Use o [aplicativo de Hub de comentários no computador com Windows 10 ou HoloLens](give-us-feedback.md) para fornecer comentários e relate problemas. Usar o Hub de comentários, você garante que todas as informações de diagnóstico necessárias estão incluídas para ajudar a nossos engenheiros de depurar e resolver o problema rapidamente.

>[!NOTE]
>Não se esqueça de aceitar o aviso que pergunta se você deseja que o Hub de comentários para acessar a pasta de documentos (selecione **Sim** quando solicitado).

## <a name="prior-release-notes"></a>Notas de versão prévia

* [Notas de versão – abril de 2018](release-notes-april-2018.md)
* [Notas de versão – outubro de 2017](release-notes-october-2017.md)
* [Notas de versão – agosto de 2016](release-notes-august-2016.md)
* [Notas de versão – maio de 2016](release-notes-may-2016.md)
* [Notas de versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Suporte de imersão fone de ouvido (link externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Suporte do HoloLens (link externo)](https://support.microsoft.com/products/hololens)
* [Instalar as ferramentas](install-the-tools.md)
* [Envie seus comentários](give-us-feedback.md)


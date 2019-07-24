---
title: Notas de versão – outubro de 2018
description: Notas de versão do HoloLens e do Windows Mixed Reality para a atualização de outubro de 2018 do Windows 10 (também conhecida como RS5).
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: notas de versão, versão, Windows 10, Build, RS5, so
ms.openlocfilehash: 794050910be40e7f98d0a1f67c2e1cf6963305dd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524265"
---
# <a name="release-notes---october-2018"></a>Notas de versão – outubro de 2018

A **[atualização do Windows 10 de outubro de 2018](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (também conhecida como RS5) inclui novos recursos para os fones de ouvido com o HoloLens e o Windows Mixed realm de imersão conectados aos PCs. 

Para atualizar para a versão mais recente no HoloLens ou no PC (para fones de ouvido com a realidade do Windows Mixed Realm), abra o aplicativo **configurações** , acesse **Atualizar & segurança**e, em seguida, selecione o botão **verificar atualizações** . Em um PC com Windows 10, você também pode instalar manualmente a atualização do Windows 10 de outubro de 2018 usando a [ferramenta de criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

**Versão mais recente do desktop:** Atualização de outubro de 2018 do Windows 10 (**10.0.17763.107**)<br>
**Versão mais recente para o HoloLens:** Atualização de outubro de 2018 do Windows 10 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Novos recursos para os headsets de imersão de realidade mista do Windows

A atualização do Windows 10 de outubro de 2018 inclui vários aprimoramentos para o uso de fones de ouvido (VR) de realidade misturada do Windows com seu PC desktop.

### <a name="for-everyone"></a>Para todos

* **Lanterna de realidade misturada** – Abra um portal no mundo real para encontrar o teclado, veja alguém próximo ou dê uma olhada em seus arredores sem remover o headset! Você pode ativar a lanterna de realidade misturada no menu Iniciar, pressionando Windows + pegue em seu controlador de movimento ou dizendo "lâmpada ligada/desligada". Aponte seu controlador na direção do que você deseja ver, como usar uma lanterna no escuro.

    ![Lanterna de realidade misturada](images/mr-flashlight.png)

* **Novos aplicativos e maneiras de iniciar o conteúdo na página inicial da realidade misturada**
    * Se você estiver usando a [realidade mista do Windows para SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality), seus títulos de SteamVR agora aparecerão no menu iniciar e os iniciadores de aplicativos para cada um podem ser colocados na página inicial misturada de realidade.
    
        ![Iniciadores de aplicativos SteamVR](images/steamvr-launchers.png)
        
    * Novo aplicativo de *vídeos 360* para descobrir uma seleção regular de vídeos de 360 graus.
    * Novo aplicativo *WebVR Showcase* para descobrir uma seleção regular de experiências de WebVR.
    * A primeira vez que os clientes do Windows Mixed Reality vão entrar na casa Cliff e encontrá-la preenchida previamente com iniciadores de aplicativos 3D para alguns dos nossos aplicativos e jogos de imersão favoritos da Microsoft Store.
    * As janelas do Microsoft Edge agora incluem um botão *compartilhar* .
* **Menu de ações rápidas** – de dentro de um aplicativo de realidade misturada de imersão, você pode pressionar o botão Windows para acessar um novo menu de ações rápidas, com acesso fácil ao *menu SteamVR*, *captura de foto/vídeo*, *lanterna*e *página inicial*.
* **Suporte para PCs mochila** -fones de ouvido (VR) de realidade misturada do Windows são executados em PCs mochila sem a necessidade de um emulador de exibição após a conclusão da instalação.
* **Novos recursos de áudio** – agora você pode espelhar o áudio de uma experiência de realidade mista do Windows para a tomada de áudio (ou fones de ouvido) em seu headset *e* um dispositivo de áudio conectado ao seu PC (como palestrantes externos). Também adicionamos um indicador visual para o nível de volume na tela do headset.
* **Outros aprimoramentos**
    * As atualizações do portal de realidade misturada agora são fornecidas por meio do Microsoft Store, permitindo atualizações mais rápidas entre as principais versões do Windows. Observe que isso só se aplica ao aplicativo da área de trabalho e a experiência do headset do Windows Mixed Reality ainda é atualizada com o sistema operacional. 
    * Quando os headsets vão para a suspensão, os aplicativos do Windows Mixed Reality são suspensos em vez de encerrados (até que o portal da realidade misturada seja fechado).
    
### <a name="for-developers"></a>Para desenvolvedores

* **[Controle de código QR](qr-code-tracking.md)** -habilite o controle de código QR em seu aplicativo de realidade misturada, permitindo que os fones de ouvido (VR) de realidade mista do Windows verifiquem os códigos QR e relate-os de volta aos aplicativos interessados.
* **Suporte de DRM de hardware para aplicativos de imersão** – os desenvolvedores agora podem solicitar texturas de BackBuffer protegidas por hardware, se houver suporte pelo hardware de vídeo, permitindo que os aplicativos usem conteúdo protegido por hardware de fontes como PlayReady.
* **[Integre a interface do usuário de captura de realidade misturada a aplicativos de imersão](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** – os desenvolvedores podem integrar a captura de realidade mista em seus aplicativos usando a [interface do usuário de captura de câmera](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) do Windows interna com apenas algumas linhas de código.

## <a name="new-features-for-hololens"></a>Novos recursos para o HoloLens

A atualização do Windows 10 de outubro de 2018 está disponível publicamente para todos os clientes do HoloLens e inclui vários aprimoramentos, como:

### <a name="for-everyone"></a>Para todos

* **Menu de ações rápidas** – de dentro de um aplicativo de realidade misturada de imersão, você pode pressionar o botão Windows para acessar um novo menu de ações rápidas, com acesso fácil para *iniciar a gravação de vídeo*, *tirar fotos*, *casa misturada de realidade*, *alterar volume*e *conectar*.
* **Iniciar/parar a captura de vídeo no menu iniciar ou ações rápidas** – se você iniciar a captura de vídeo no menu iniciar ou nos menus ações rápidas, poderá parar a gravação do mesmo local. (Não se esqueça de que você sempre pode fazer isso com comandos de voz.)
* **Projeto para um dispositivo habilitado para Miracast** -projeta seu conteúdo do HoloLens para um dispositivo de superfície ou TV/monitor próximo se estiver usando um adaptador ou uma exibição habilitado para Miracast.
* **Novas notificações** – exiba e responda a notificações no HoloLens, exatamente como você faz em um computador.  
* **Sobreposições úteis em aplicativos de realidade misturada de imersão** – agora você verá sobreposições como teclado, caixas de diálogo, seletor de arquivos, etc. ao usar aplicativos de realidade misturada de imersão.
* **Indicador visual para alteração de volume** -ao usar os botões de volume para cima/para baixo no seu HoloLens, você verá um indicador visual do nível de volume no headset.
* **Novos visuais para inicialização de dispositivo** -um indicador de carregamento foi adicionado durante o processo de inicialização para fornecer comentários visuais que o sistema está carregando.
* **Compartilhamento próximo** – a experiência de compartilhamento no próximo do Windows permite que você compartilhe uma captura com um dispositivo Windows próximo.  
* **Compartilhar do Microsoft Edge** -o Microsoft Edge agora inclui um botão de *compartilhamento* . 

### <a name="for-developers"></a>Para desenvolvedores

* **[Integre a interface do usuário de captura de realidade misturada a aplicativos de imersão](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** – os desenvolvedores podem integrar a captura de realidade mista em seus aplicativos usando a [interface do usuário de captura de câmera](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) do Windows interna com apenas algumas linhas de código.

### <a name="for-commercial-customers"></a>Para clientes comerciais

* **Habilitar provisionamento pós-instalação** – agora você pode aplicar um pacote de provisionamento de tempo de execução a qualquer momento usando configurações.
* **Acesso atribuído com grupos do Azure ad** – agora você pode usar grupos do Azure ad para configuração do acesso atribuído ao Windows para configurar a configuração de quiosque único ou de vários aplicativos.
* **Fixar entrada no perfil alternar da tela de entrada** -o PIN de entrada agora está disponível para "outro usuário" na tela de entrada. 
* **Ler informações de hardware do dispositivo por meio de MDM** -os administradores de ti podem ver e acompanhar o HoloLens pelo número de série do dispositivo no console do MDM.
* **Definir o nome do dispositivo do HoloLens por meio do MDM (renomear)** -os administradores de ti podem ver e renomear os dispositivos HoloLens no console do MDM

### <a name="for-international-customers"></a>Para clientes internacionais

Agora você pode usar o HoloLens com a interface do usuário localizada para chinês simplificado ou japonês, incluindo teclado de Pinyin localizado, ditado, conversão de texto em fala (TTS) e comandos de voz.

## <a name="known-issues"></a>Problemas conhecidos

Trabalhamos duro para fornecer uma ótima experiência de realidade mista do Windows, mas ainda estamos acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, envie [-nos seus comentários](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Após a atualização
Você pode observar os seguintes problemas ao usar a atualização do Windows 10 de outubro de 2018 em seu HoloLens:
* Os **aplicativos podem terminar no loop de entrada quando iniciados a partir de uma notificação** – alguns aplicativos que exigem entrada podem terminar em um loop de entrada interminável quando iniciados a partir de uma notificação. Por exemplo, isso pode acontecer depois de instalar o aplicativo Microsoft Portal da Empresa do Microsoft Store e iniciá-lo a partir da notificação de conclusão da instalação.
* A **página de entrada do aplicativo pode ser concluída com uma página em branco** – em alguns casos, quando um prompt de entrada mostra seu aplicativo, na conclusão, a página de entrada não é fechada e, em vez disso, mostra uma página em branco (preto). Você pode fechar a página em branco ou movê-la para descobrir o aplicativo abaixo. Por exemplo, isso pode ocorrer na entrada durante o registro de MDM do aplicativo de configurações. 

## <a name="provide-feedback-and-report-issues"></a>Fornecer comentários e relatar problemas

Use o [aplicativo de Hub de comentários em seu computador do HoloLens ou do Windows 10](give-us-feedback.md) para fornecer comentários e relatar problemas. O uso do hub de comentários garante que todas as informações de diagnóstico necessárias estejam incluídas para ajudar nossos engenheiros a depurar e resolver o problema rapidamente.

>[!NOTE]
>Lembre-se de aceitar o prompt que pergunta se você deseja que o Hub de comentários acesse sua pasta documentos (selecione **Sim** quando solicitado).

## <a name="prior-release-notes"></a>Notas de versão anteriores

* [Notas sobre a versão – abril de 2018](release-notes-april-2018.md)
* [Notas sobre a versão – outubro de 2017](release-notes-october-2017.md)
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Suporte a headsets de imersão (link externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Suporte ao HoloLens (link externo)](https://support.microsoft.com/products/hololens)
* [Instalar as ferramentas](install-the-tools.md)
* [Faça comentários](give-us-feedback.md)


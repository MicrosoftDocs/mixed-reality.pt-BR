---
title: Notas de versão – outubro de 2017
description: Notas de versão do Windows Mixed Reality para o do Windows 10 Fall Creators Update (outubro de 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: anotações, versão, windows 10, compilação, rs3, sistema operacional de versão
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589138"
---
# <a name="release-notes---october-2017"></a>Notas de versão – outubro de 2017

Bem-vindo ao Windows realidade misturada! A versão dos **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** introduz o suporte a novos [fones imersivos em exposição Windows Mixed Reality](immersive-headset-hardware-details.md) e [controladores de movimento ](motion-controllers.md), permitindo que você explore novos mundos, jogar VR e experiência de imersão entretenimento quando conectado a um [Windows Mixed Reality capable PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

O lançamento do headsets Windows Mixed Reality e controladores de movimento é o ápice de um esforço em equipe grande e um grande passo para o [plataforma Windows Mixed Reality](mixed-reality.md), que inclui [Microsoft HoloLens](hololens-hardware-details.md). Enquanto HoloLens não estão recebendo uma atualização com o lançamento do que o Windows 10 Fall Creators Update, sabe que o trabalho em HoloLens ainda não interrompido; teremos muitas lições aprendidas e insight para aplicar em nosso trabalho recente em realidade mista do Windows como um todo. Na verdade, fones imersivos em exposição Windows Mixed Reality e controladores representam um ótimo ponto de entrada do motion apontam para o desenvolvimento para o HoloLens também, como as mesmas APIs, ferramentas, e conceitos se aplicam a ambos.

Para atualizar para a versão mais recente para cada dispositivo, abra o **as configurações** aplicativo, vá para **atualização e segurança**, em seguida, selecione o **verificar se há atualizações** botão. Em um computador Windows 10, você também pode instalar manualmente o Windows 10 Fall Creators Update usando a [ferramenta de criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

 **Versão mais recente para a área de trabalho:** Área de trabalho do Windows 10 de outubro de 2017 (**10.0.16299.15**, do Windows 10 Fall Creators Update)<br>
 **Versão mais recente do HoloLens:** [Windows 10 Holographic de agosto de 2016](release-notes-august-2016.md) (**10.0.14393.0**, atualização de aniversário do Windows 10)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Introdução ao Windows Mixed Reality

O Windows 10 Fall Creators Update oficialmente introduz o suporte para headsets Windows Mixed Reality e controladores de movimento, como também fazendo o Windows 10 primeiro sistema de operacional espaciais do mundo. Eis alguns destaques:
* **[Variedade de fones de ouvido](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)**  -Windows Mixed Reality está permitindo que os parceiros oferecer uma variedade de fones de ouvido que começa em US $399 USD agrupado com os controladores de movimento.
* **[Controladores de movimento](motion-controllers.md)**  -controladores de movimento de realidade mista do Windows sem fio emparelhar com o PC via Bluetooth e seis graus de liberdade de acompanhamento, muitos métodos de entrada e IMUs de recursos.
* **[Instalação fácil e portabilidade](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)**  – defina se e comece em menos de 10 minutos. Fones imersivos em exposição usar o rastreamento de dentro para fora para rastrear o movimento e os controladores de movimento, com seis graus de liberdade. Nenhum câmeras externas ou marcadores de farol necessárias!
* **[Suporte para um intervalo mais amplo de PCs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)**  -Windows Mixed Reality permitirá que as pessoas mais experiência VR da área de trabalho que nunca, com suporte para, selecione integrado placas gráficas e PCs, iniciando em US $499 dólares.
* **[Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md)**  -primeiro sistema de operacional espaciais do mundo Fornece um ambiente de home familiar para multitarefa com aplicativos 2D, iniciar VR jogos e aplicativos e colocando hologramas decorativas.
* **[Incríveis aplicativos em que a Microsoft Store e jogos VR](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)**  – desde imersivo entretenimento como Hulu VR e 360 vídeo para epic games como SUPERHOT VR e Arizona sol, a Microsoft Store tem um intervalo de conteúdo a experiência no misto do Windows Realidade.
* **[Acesso antecipado de SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)**  – o Windows 10 Fall Creators Update habilita o suporte para títulos de SteamVR a ser reproduzido com headsets Windows Mixed Reality e controladores, tornando o catálogo de maior de VR títulos disponíveis para misto do Windows Usuários da realidade.

## <a name="known-issues"></a>Problemas conhecidos

Trabalhamos muito para fornecer uma ótima experiência de realidade mista do Windows, mas estamos ainda estiver acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, por favor [envie seus comentários](give-us-feedback.md).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicativo da área de trabalho no Windows Mixed Reality inicial
* Ferramenta de captura não funciona no aplicativo da área de trabalho.
* Aplicativo da área de trabalho não mantém a configuração na nova inicialização.
* Se você estiver usando a visualização do Portal de realidade mista na área de trabalho, ao abrir o aplicativo da área de trabalho no Windows Mixed Reality inicial, você pode perceber o efeito de espelho infinito. 
* Executar o aplicativo da área de trabalho pode causar problemas de desempenho em não - Ultra misto realidade PCs Windows; não é recomendável.  
* Aplicativo de desktop pode iniciar automaticamente porque uma janela invisível na área de trabalho tem o foco. 
* Controle de conta de usuário da área de trabalho prompt fará fone de ouvido exibir preto até que o prompt é concluído.

### <a name="windows-mixed-reality-setup"></a>Instalação do Windows Mixed Reality
* Ao configurar o Windows com um headset conectado, o monitor do PC poderá ficar em branco. Desconecte o headset para habilitar a saída para o monitor do PC para concluir a instalação do Windows.
* Ao criar um limite, o rastreamento poderá falhar. Nesse caso, tente novamente, como o sistema Saiba mais sobre o seu espaço ao longo do tempo.
* Se você ativar a Cortana ativada ou desativada durante a instalação do Windows Mixed Reality, essa alteração será aplicada às suas configurações da área de trabalho do Cortana.
* Se você não tiver fones de ouvido conectados, você poderá perder dicas adicionais quando visitar o Windows Mixed Reality inicial.
* Fones de ouvido Bluetooth podem causar interferências com controladores de movimento. É recomendável desemparelhamento ou desligar controladores de Bluetooth durante as sessões do Windows Mixed Reality.

### <a name="games-and-apps-from-windows-store"></a>Jogos e aplicativos da Windows Store
* Alguns jogos graficamente intensivos, como 6 do Forza Motorsports, podem causar problemas de desempenho em PCs com menor capacidade quando executados dentro de realidade mista do Windows.

### <a name="audio"></a>Áudio
* Conforme observado acima, periféricos de áudio de Bluetooth não funcionam bem com voz Windows Mixed Reality e experiências espaciais do som. Eles também negativamente podem afetar sua experiência de controlador de animação. Não recomendamos o uso de fones de ouvido Bluetooth áudio com a realidade mista do Windows.
* Você não pode usar o dispositivo conectado ao áudio (ou parte do) o fone de ouvido para reprodução de áudio quando o dispositivo não está sendo usado. Se você tiver apenas um fone de ouvido, você poderá se conectar o fone de ouvido ao PC host em vez do fone de ouvido. Se assim, em seguida, você deve desligar "alternar para o áudio de fone de ouvido" **as configurações** > **realidade misturada** > **áudio e fala**.
* Alguns aplicativos, incluindo muitos daqueles iniciado por meio de SteamVR, podem perder o áudio ou parar de responder quando o dispositivo de áudio muda à medida que você iniciar ou parar o Portal de realidade mista. Depois de abrir o aplicativo do Portal de realidade mista para corrigir isso, reinicie o aplicativo.
* Se você tiver habilitado em seu PC host antes de usar o headset de realidade mista do Windows a Cortana, você poderá perder a simulação de som espacial aplicada aos aplicativos que você coloque em torno do Windows Mixed Reality inicial. A solução alternativa é habilitar o "Windows Sonic para fones de ouvido" em todos os dispositivos de áudio conectados ao seu PC, até mesmo o fone de ouvido conectados ao dispositivo de áudio:
   1. Clique no ícone na barra de tarefas da área de trabalho e selecione na lista de dispositivos de áudio.
   2. Clique com botão direito no ícone na barra de tarefas da área de trabalho e selecione "Windows Sonic para fones de ouvido" no menu "A instalação do alto-falante".
   3. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).
>[!NOTE]
> - Como os fones de ouvido/alto-falantes conectados ao seu fone de ouvido não aparecerá, a menos que você o estiver usando, você precisará fazer isso de dentro da janela de aplicativo da área de trabalho do Windows Mixed Reality doméstica para aplicar essa configuração para o dispositivo de áudio conectado ao seu fone de ouvido (ou integrado em seu fone de ouvido).
> - Outra opção é desativar "Cortana permitem responder a Ei Cortana" na **as configurações** > **Cortana** na área de trabalho antes de iniciar o Windows Mixed Reality.

* Quando outro dispositivo USB multimídia (como uma webcam) compartilha o mesmo hub USB (externo ou dentro de seu PC) com o headset de realidade mista do Windows, em casos raros áudio jack/fones de ouvido do fone de ouvido pode ter um som zunido ou sem áudio em todos os. Você pode corrigir isso por fone de ouvido em uma porta USB que não compartilham o mesmo hub como o outro dispositivo ou outro dispositivo USB multimídia desconectar/desabilitar.
* Em casos raros, o hub USB do PC host não pode fornecer capacidade suficiente para o headset de realidade mista do Windows e você pode perceber uma intermitência de ruído dos fones de ouvido o fone de ouvido.

### <a name="speech"></a>Controle por voz
* Cortana pode falhar ao reproduzir-lhe as indicações de áudio para áudio e de escuta/pensamento respostas a comandos.
* Cortana na China e Japão mercados corretamente mostra texto abaixo do círculo do Cortana durante o uso.
* Cortana pode ficar lento na primeira vez que ela seja invocada em uma sessão do Portal de realidade mista. Você pode contornar isso, tornando-se de que "Let Cortana" responder a Ei Cortana sob **as configurações** > **Cortana** > **falar com o Cortana** é habilitada.
* Cortana podem ser executados mais lentamente em computadores que não são Windows Mixed Reality Ultra PCs.
* Quando o teclado do sistema é definido para um idioma diferente do idioma da interface do usuário do Windows Mixed Reality, usando o ditado de teclado no Windows Mixed Reality resultará em uma caixa de diálogo de erro sobre o ditado não está funcionando devido a não ter conexão Wi-Fi. Para corrigir o problema simplesmente Verifique se o idioma do teclado sistema corresponde ao idioma da interface de realidade mista do Windows.
* Espanha corretamente não está sendo reconhecida como um mercado de onde a fala está habilitada para Windows Mixed Reality.

### <a name="holograms"></a>Hologramas
* Se você colocou um grande número de hologramas no seu Windows Mixed Reality inicial, alguns podem desaparecer e reaparecer conforme você olha ao redor. Para evitar isso, remova algumas das hologramas o naquela área do Windows Mixed Reality inicial.

### <a name="motion-controllers"></a>Controladores de movimento
* Ocasionalmente, se você clicar em uma página da Web no Microsoft Edge, o conteúdo será zoom em vez de clique.
* Às vezes, quando você clica em um link na borda, a seleção não funcionará.

## <a name="prior-release-notes"></a>Notas de versão prévia
* [Notas de versão – agosto de 2016](release-notes-august-2016.md)
* [Notas de versão – maio de 2016](release-notes-may-2016.md)
* [Notas de versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Suporte de imersão fone de ouvido (link externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Problemas conhecidos do HoloLens](hololens-known-issues.md)
* [Instalar as ferramentas](install-the-tools.md)
* [Envie seus comentários](give-us-feedback.md)

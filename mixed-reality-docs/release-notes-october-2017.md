---
title: Notas de versão – outubro de 2017
description: Notas de versão do Windows Mixed Reality para a atualização dos criadores de outono do Windows 10 (outubro de 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: notas de versão, versão, Windows 10, Build, RS3, so
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524090"
---
# <a name="release-notes---october-2017"></a>Notas de versão – outubro de 2017

Bem-vindo ao Windows Mixed Reality! O lançamento da **[atualização do Windows 10 outono Creators](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** apresenta suporte para novos headsets de imersão e controladores de [movimento](motion-controllers.md)do [Windows Mixed Reality](immersive-headset-hardware-details.md) , permitindo que você Explore novos mundos, Jogue jogos de VR e experimente de imersão entretenimento quando conectado a um [PC com capacidade do Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

O lançamento de headsets e controladores de movimento do Windows Mixed Reality é a culminação de um grande esforço da equipe e um avanço importante para a [plataforma de realidade mista do Windows](mixed-reality.md), que inclui [o Microsoft HoloLens](hololens-hardware-details.md). Embora o HoloLens não esteja recebendo uma atualização com o lançamento da atualização dos criadores de outono do Windows 10, saiba que o trabalho no HoloLens não foi interrompido; Teremos muitos aprendizados e ideias para se aplicarem de nosso trabalho recente na realidade mista do Windows como um todo. Na verdade, os headsets e controladores de movimento da realidade misturada no Windows também representam um ótimo ponto de entrada para o desenvolvimento para o HoloLens, já que as mesmas APIs, ferramentas e conceitos se aplicam a ambos.

Para atualizar para a versão mais recente de cada dispositivo, abra o aplicativo **configurações** , acesse **Atualizar & segurança**e, em seguida, selecione o botão **verificar atualizações** . Em um PC com Windows 10, você também pode instalar manualmente a atualização dos criadores de outono do Windows 10 usando a [ferramenta de criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

 **Versão mais recente do desktop:** Windows 10 desktop de outubro de 2017 (**10.0.16299.15**, atualização para criadores de outono do Windows 10)<br>
 **Versão mais recente para o HoloLens:** [Windows 10 Holographic agosto de 2016](release-notes-august-2016.md) (**10.0.14393.0**, atualização de aniversário do Windows 10)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Apresentando o Windows Mixed Reality

A atualização de criadores de outono do Windows 10 introduz oficialmente o suporte para os headsets e controladores de movimento do Windows Mixed Reality, além de tornar o Windows 10 o primeiro sistema operacional espacial do mundo. Aqui estão os destaques:
* **[Variedade de headsets](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** – a realidade mista do Windows está permitindo que os parceiros ofereçam uma variedade de headsets que começam às $399 USD agrupadas com controladores de movimento.
* **[Controladores de movimento](motion-controllers.md)** -os controladores de movimento do Windows Mixed Reality são emparelhados sem fio com seu PC por meio de Bluetooth e apresentam um acompanhamento de seis graus de liberdade, muitos métodos de entrada e IMUs.
* **[Configuração e portabilidade fáceis](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)** – configure e comece em menos de 10 minutos. Headsets de imersão usam rastreamento interno para acompanhar seu movimento e seus controladores de movimento, com seis graus de liberdade. Não são necessárias câmeras externas ou marcadores de Lighthouse!
* **[Suporte para uma maior variedade de PCs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)** – a realidade mista do Windows permitirá que mais pessoas experimentem o trabalho de hoje, com suporte para selecionar placas gráficas integradas e PCs a partir de us $ $499.
* **[Início do Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)** – o primeiro sistema operacional espacial do mundo fornece um ambiente doméstico familiar para várias tarefas com aplicativos 2D, lançamento de jogos e aplicativos de VR e colocação de hologramas decorativos.
* Os **[jogos e aplicativos de VR incríveis na Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** -da diversão de imersão como o vídeo Hulu vr e 360 para jogos Epic como SUPERHOT VR e Arizona sol, a Microsoft Store tem uma variedade de conteúdo a ser experimentado no Windows Mixed Reality.
* **[SteamVR Early Access](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)** – a atualização do Windows 10 outono Creators permite que o suporte para títulos de SteamVR seja reproduzido com fones de ouvido e controladores do Windows Mixed Realm, tornando o maior catálogo de títulos VR disponíveis para usuários do Windows Mixed Reality.

## <a name="known-issues"></a>Problemas conhecidos

Trabalhamos duro para fornecer uma ótima experiência de realidade mista do Windows, mas ainda estamos acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, envie [-nos seus comentários](give-us-feedback.md).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicativo de desktop na página inicial do Windows Mixed Reality
* A ferramenta de recorte não funciona no aplicativo de desktop.
* O aplicativo de área de trabalho não mantém a configuração ao reiniciar.
* Se você estiver usando a visualização do portal de realidade misturada na sua área de trabalho, ao abrir o aplicativo de desktop na página inicial do Windows Mixed Reality, você poderá observar o efeito de espelho infinito. 
* A execução do aplicativo de área de trabalho pode causar problemas de desempenho em PCs com realidade não ultra Windows misturada; Não é recomendável.  
* O aplicativo de desktop pode ser iniciado automaticamente porque uma janela invisível no desktop tem foco. 
* O prompt de controle de conta de usuário da área de trabalho fará com que o headset apareça em preto até que o prompt seja concluído

### <a name="windows-mixed-reality-setup"></a>Configuração do Windows Mixed Reality
* Ao configurar o Windows com um headset conectado, o monitor do PC pode ficar em branco. Desconecte seu headset para habilitar a saída para o monitor do seu PC para concluir a instalação do Windows.
* Ao criar um limite, o rastreamento pode falhar. Nesse caso, tente novamente, pois o sistema aprenderá mais sobre o seu espaço ao longo do tempo.
* Se você ativar ou desativar a Cortana durante a configuração do Windows Mixed Reality, essa alteração será aplicada às configurações da Cortana da área de trabalho.
* Se você não tiver fones de ouvido conectados, poderá perder dicas adicionais ao visitar pela primeira vez o Windows Mixed Reality Home.
* Os fones de ouvido Bluetooth podem causar interferências com os controladores de movimento. É recomendável desemparelhar ou ligar controladores Bluetooth durante sessões de realidade mista do Windows.

### <a name="games-and-apps-from-windows-store"></a>Jogos e aplicativos da Windows Store
* Alguns jogos graficamente intensivos, como Forza Motorsports 6, podem causar problemas de desempenho em PCs com menos capacidade quando reproduzidos dentro da realidade mista do Windows.

### <a name="audio"></a>Áudio
* Conforme observado acima, os periféricos de áudio Bluetooth não funcionam bem com experiências de voz e de som espacial do Windows Mixed Reality. Eles também podem afetar negativamente a experiência do controlador de movimento. Não recomendamos o uso de headsets de áudio Bluetooth com a realidade mista do Windows.
* Você não pode usar o dispositivo de áudio conectado ao (ou parte do) fone de ouvido para reprodução de áudio quando o dispositivo não está sendo gasto. Se você tiver apenas um headset de áudio, talvez queira conectar o headset de áudio ao PC host em vez do headset. Nesse caso, você deve desativar "alternar para áudio de headset" em **configurações** > de**realidade** > misturada**áudio e fala**.
* Alguns aplicativos, incluindo muitos daqueles iniciados por meio de SteamVR, podem perder áudio ou parar quando o dispositivo de áudio muda conforme você inicia ou interrompe o portal de realidade misturada. Reinicie o aplicativo depois de abrir o aplicativo do portal de realidade misturada para corrigir isso.
* Se você tiver o Cortana habilitado em seu PC host antes de usar o headset de realidade mista do Windows, poderá perder a simulação de som espacial aplicada aos aplicativos que você coloca em casa ao Windows Mixed Reality. A solução alternativa é habilitar o "Windows Sonic para fones de ouvido" em todos os dispositivos de áudio conectados ao seu PC, até mesmo no dispositivo de áudio conectado ao headset:
   1. Clique com o botão esquerdo do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione na lista de dispositivos de áudio.
   2. Clique com o botão direito do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione "Windows Sonic para fones de ouvido" no menu "configuração do orador".
   3. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).
>[!NOTE]
> - Como os fones de ouvido/alto-falantes conectados ao seu headset não aparecerão a menos que você o esteja usando, você precisa fazer isso na janela do aplicativo de desktop na página inicial do Windows Mixed Reality para aplicar essa configuração ao dispositivo de áudio conectado ao fone de ouvido (ou integrado em seu headset).
> - Outra opção é desativar "permitir que a Cortana responda à Ei Cortana" em **configurações** > **Cortana** na sua área de trabalho antes de iniciar a realidade mista do Windows.

* Quando outro dispositivo USB de multimídia (como uma Web Cam) compartilha o mesmo hub USB (externo ou dentro de seu PC) com o headset de realidade mista do Windows, em casos raros, a tomada de áudio/fone de ouvido do headset pode ter um som de zumbi ou nenhum áudio. Você pode corrigir isso pelo seu headset em uma porta USB que não compartilha o mesmo Hub que o outro dispositivo, ou desconectar/desabilitar o outro dispositivo de multimídia USB.
* Em casos muito raros, o hub USB do PC host não pode fornecer energia suficiente para o headset de realidade mista do Windows e você pode notar uma intermitência de ruído dos fones de ouvido conectados ao headset.

### <a name="speech"></a>Controle por voz
* A Cortana pode falhar ao reproduzir suas indicações de áudio para ouvir/pensar e respostas de áudio para comandos.
* Os mercados da Cortana na China e no Japão não mostram corretamente o texto abaixo do círculo do Cortana durante o uso.
* A Cortana pode ser lenta na primeira vez que ela é invocada em uma sessão do portal da realidade misturada. Você pode contornar isso, certificando-se de que "permitir que a Cortana responda à Ei Cortana" em **configurações** > que Cortana > **falam com a Cortana** está habilitada
* A Cortana pode ser executada mais lentamente em computadores que não são o Windows Mixed Reality ultra PCs.
* Quando o teclado do sistema é definido como um idioma diferente do idioma da interface do usuário no Windows Mixed Reality, usar o ditado do teclado no Windows Mixed Reality resultará em uma caixa de diálogo de erro sobre o ditado que não está funcionando devido a não ter uma conexão Wi-Fi. Para corrigir o problema, basta verificar se o idioma do teclado do sistema corresponde ao idioma da interface do usuário do Windows Mixed Reality.
* A Espanha não está sendo reconhecida corretamente como um mercado em que a fala está habilitada para a realidade mista do Windows.

### <a name="holograms"></a>Hologramas
* Se você tiver colocado um grande número de hologramas em sua casa do Windows Mixed Reality, alguns poderão desaparecer e reaparecerem à medida que você examinar. Para evitar isso, remova alguns dos hologramas nessa área da página inicial do Windows Mixed Reality.

### <a name="motion-controllers"></a>Controladores de movimento
* Ocasionalmente, se você clicar em uma página da Web no Microsoft Edge, o conteúdo será ampliado em vez de clicar.
* Às vezes, quando você clica em um link no Microsoft Edge, a seleção não funciona.

## <a name="prior-release-notes"></a>Notas de versão anteriores
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte também
* [Suporte a headsets de imersão (link externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Problemas conhecidos do HoloLens](hololens-known-issues.md)
* [Instalar as ferramentas](install-the-tools.md)
* [Faça comentários](give-us-feedback.md)

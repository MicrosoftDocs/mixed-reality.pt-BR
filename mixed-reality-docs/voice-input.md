---
title: Entrada de voz
description: Entrada de voz é uma entrada de núcleo para HoloLens e o Windows Mixed Reality fones imersivos em exposição. Voz pode ser usado para comandos, ditado, Cortana e muito mais.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, voz, cortana, fala, de entrada
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829954"
---
# <a name="voice-input"></a>Entrada de voz

Voz é uma das três formas principais de entrada em HoloLens. Ele permite que um holograma de comando diretamente sem ter que usar [gestos](gestures.md). Você simplesmente [olhares](gaze.md) em um holograma e fale seu comando. Entrada de voz pode ser uma maneira natural para se comunicar sua intenção. Voz é especialmente bons atravessando interfaces complexas porque ele permite que os usuários acabando com menus aninhados com um único comando.

Entrada de voz é alimentada pela [mesmo mecanismo](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que dá suporte à conversão de fala em todos os outros aplicativos universais do Windows.

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></td>
    </tr>
     <tr>
        <td>Entrada de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (com o microfone)</td>
    </tr>
</table>

## <a name="the-select-command"></a>O comando "select"

Mesmo sem adicionar especificamente o suporte de voz ao seu aplicativo, os usuários podem ativar hologramas simplesmente dizendo "select". Esse comportamento é o mesmo que um [polegar](gestures.md#air-tap) em HoloLens, pressionando o botão de seleção no [clicker HoloLens](hardware-accessories.md#hololens-clicker), ou pressionando o gatilho em um [controlador de animação do Windows Mixed Reality](motion-controllers.md). Você ouvir um som e verá uma dica de ferramenta com "select" aparecem como confirmação. "Selecionar" é habilitado por um algoritmo de detecção de palavra-chave de baixa energia, para que ele esteja sempre disponível para você dizer a qualquer momento com o impacto de vida útil da bateria mínima, mesmo com as mãos ao seu lado.

> [!NOTE]
> Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).

![Diga "selecionar" usar o comando de voz para seleção](images/kma-voice-select-00170-800px.png)<br>
*Diga "selecionar" usar o comando de voz para seleção*

## <a name="hey-cortana"></a>Ei Cortana

Você também pode dizer "Ei Cortana" para abrir a Cortana a qualquer momento. Você não precisa esperar para ela aparecer continuar solicitando sua pergunta ou dar a ela uma instrução - por exemplo, tente dizendo "Ei Cortana o que é o clima?" como uma única sentença. Para obter mais informações sobre o Cortana e o que você pode fazer, simplesmente pergunte dela. Dizer "Ei Cortana, o que devo dizer?" e ela vai puxar uma lista de comandos de trabalho e sugerido. Se você já estiver no aplicativo do Cortana você também pode clicar o **?** ícone na barra lateral para efetuar pull de backup nesse mesmo menu.

**Comandos específicos ao HoloLens**
* "O que posso falar?"
* "Ir para casa" ou "Go to Start" – em vez de [bloom](gestures.md#bloom) para chegar ao [Menu Iniciar](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Iniciar <app>"
* "Mover <app> aqui"
* "Tirar uma foto"
* "Iniciar gravação"
* "Parar a gravação"
* "Increase o brilho"
* "Decrease o brilho"
* "Aumentar o volume"
* "Diminuir o volume"
* "Mudo" ou "Ativar"
* "Desligar o dispositivo"
* "Reiniciar o dispositivo"
* "Ir para o modo de suspensão"
* "Qual horário é?"
* "Quanto bateria restam?"
* "Chamar <contact>" (requer o Skype para HoloLens)

## <a name="see-it-say-it"></a>"Vê-lo, diga"

HoloLens tem um modelo de "vê-lo, diga" para entrada de voz, onde os rótulos de botões de dizer aos usuários quais comandos de voz também pode dizem. Por exemplo, ao examinar um aplicativo 2D, um usuário pode dizer o comando "Ajuste" que eles veem na barra de aplicativos para ajustar a posição do aplicativo do mundo.

![Ao examinar um aplicativo 2D ou holograma, um usuário pode dizer que o comando "Ajuste" que eles veem na barra de aplicativos para ajustar a posição do aplicativo do mundo](images/microphone-600px.png)

Quando os aplicativos seguem essa regra, os usuários podem facilmente entender o que dizer para o sistema de controle. Para reforçar isso, ao mesmo tempo Observação em um botão, você verá uma dica de ferramenta "duração de voz" que surge após um segundo, se o botão é habilitado para voz e exibe o comando falar para "pressionar"-lo.

![Veja, digamos que ele comandos aparecem abaixo dos botões](images/voice-seeitsayit-600px.png)<br>
*"Dificultando, diga" comandos aparecem abaixo dos botões*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para a manipulação rápida de holograma

Também há um número de voz comandos que você pode dizer ao Observação em um holograma para realizar rapidamente tarefas de manipulação. Esses comandos de voz funcionam em aplicativos 2D, bem como objetos 3D que você tenha colocado no mundo.

**Comandos de manipulação de holograma**
* Enfrentam me
* Maior | Aprimorar
* Menor

## <a name="dictation"></a>Ditado

Em vez de digitar com [toques de ar](gestures.md#air-tap), ditado de voz pode ser mais eficiente para inserir texto em um aplicativo. Isso pode acelerar a entrada com menos esforço do usuário bastante.

![Voz ditado inicia selecionando o botão de microfone](images/micbuttonfordictation.png)<br>
*Voz ditado inicia selecionando o botão de microfone no teclado*

Sempre que o teclado holográfico estiver ativo, você pode alternar para o modo de ditado em vez de digitar. Selecione o microfone no lado da caixa de texto de entrada para começar a usar.

## <a name="communication"></a>Comunicação

Para aplicativos que desejam aproveitar as opções fornecidas pelo HoloLens de processamento de entrada de áudio personalizada, é importante entender os vários [categorias de fluxo de áudio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) seu aplicativo pode consumir. Aceita de Windows 10 faz várias categorias diferentes de fluxo e HoloLens a utilização de esses três para habilitar o processamento personalizado otimizar a qualidade de áudio do microfone sob medida para fala, comunicação e outros que pode ser usado para áudio do ambiente do ambiente cenários de captura (isto é, "filmadoras").
* A categoria de fluxo de AudioCategory_Communications é personalizada para cenários de qualidade e narração de chamada e fornece ao cliente com um fluxo de áudio mono 16kHz 24 bits de voz do usuário
* A categoria de fluxo de AudioCategory_Speech é personalizada para o mecanismo de fala do HoloLens (Windows) e fornece-o com um fluxo de 16 bits de 24 kHz mono de voz do usuário. Esta categoria pode ser usada pelos mecanismos de fala 3ª parte, se necessário.
* A categoria de fluxo de AudioCategory_Other é personalizada para gravação de áudio do ambiente do ambiente e fornece ao cliente com um fluxo de áudio estéreo de 48kHz 24 bits.

Todo esse processamento de áudio é o que significa que os recursos drenar muito menos energia do que se o mesmo processamento foi feito na CPU HoloLens acelerados por hardware. Evite executar outra entrada de áudio de processamento na CPU para maximizar a vida útil da bateria de sistema e tirar proveito da compilação, descarregados o processamento de entrada de áudio.

## <a name="troubleshooting"></a>Solução de problemas

Se você estiver tendo quaisquer problemas usando "select" e "Ei Cortana", tente mover para um espaço mais discreta, a ativação para a fonte de ruído ou falando mais alto. Neste momento, todos os o reconhecimento de fala em HoloLens é ajustado e otimizado especificamente para nativos alto-falantes de inglês dos Estados Unidos.

Edição de desenvolvedor de realidade mista do Windows na versão de 2017, a lógica de gerenciamento de ponto de extremidade de áudio funcionarão bem (para sempre) após o registro em log fora e de volta na área de trabalho do computador após a conexão inicial do HMD. Antes de entrada primeiro out/no evento depois de passar por WMR OOBE, o usuário pode apresentar vários problemas de funcionalidade de áudio, variando de sem áudio para áudio de alternância, dependendo de como o sistema foi definido antes de conectar o HMD pela primeira vez.

## <a name="see-also"></a>Consulte também
* [Entrada de voz no DirectX](voice-input-in-directx.md)
* [Entrada de voz no Unity](voice-input-in-unity.md)
* [Entrada do MR 212: voz](holograms-212.md)

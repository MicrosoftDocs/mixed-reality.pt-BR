---
title: Entrada de voz
description: A entrada de voz é uma entrada principal para o HoloLens e os headsets de imersão de realidade mista do Windows. A voz pode ser usada para comandos, ditado, Cortana e muito mais.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, voz, Cortana, fala, entrada
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829954"
---
# <a name="voice-input"></a>Entrada de voz

Voz é uma das três formas principais de entrada no HoloLens. Ele permite que você comando diretamente um holograma sem precisar usar [gestos](gestures.md). Basta [olhar](gaze.md) um holograma e falar sobre o comando. A entrada de voz pode ser uma maneira natural de comunicar sua intenção. A voz é especialmente boa na passagem de interfaces complexas porque permite que os usuários recortem os menus aninhados com um único comando.

A entrada de voz é alimentada pelo [mesmo mecanismo](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que dá suporte à fala em todos os outros aplicativos universais do Windows.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Entrada de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (com microfone)</td>
    </tr>
</table>

## <a name="the-select-command"></a>O comando "Select"

Mesmo sem adicionar especificamente suporte de voz ao seu aplicativo, os usuários podem ativar os hologramas simplesmente dizendo "Select". Isso se comporta da mesma forma que um [toque de ar](gestures.md#air-tap) no HoloLens, pressionando o botão Selecionar no [clicador de HoloLens](hardware-accessories.md#hololens-clicker)ou pressionando o gatilho em um [controlador de movimento de realidade mista do Windows](motion-controllers.md). Você ouvirá um som e verá uma dica de ferramenta com "Select" aparecer como confirmação. "Selecionar" é habilitado por um algoritmo de detecção de palavra-chave de baixo consumo de energia para que ele esteja sempre disponível para você, a qualquer momento, com impacto mínimo na vida útil da bateria, mesmo com suas mãos no seu lado.

> [!NOTE]
> Mais diretrizes específicas para o HoloLens 2 em [breve](index.md#news-and-notes).

![Diga "Select" para usar o comando de voz para seleção](images/kma-voice-select-00170-800px.png)<br>
*Diga "Select" para usar o comando de voz para seleção*

## <a name="hey-cortana"></a>Ei Cortana

Você também pode dizer "Ei Cortana" para abrir a Cortana a qualquer momento. Você não precisa esperar que ela pareça continuar perguntando sua pergunta ou dando a ela uma instrução. por exemplo, tente dizer "Ei Cortana o que é o clima?" como uma única frase. Para obter mais informações sobre a Cortana e o que você pode fazer, basta perguntar a ela! Diga "Ei Cortana o que eu posso dizer?" e ela receberá uma lista de comandos de trabalho e sugeridos. Se você já estiver no aplicativo Cortana, também poderá clicar no botão **?** na barra lateral para extrair esse mesmo menu.

**Comandos específicos do HoloLens**
* "O que posso falar?"
* "Ir para a página inicial" ou "ir para o início"-em vez de [cair](gestures.md#bloom) para chegar ao [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Iniciar <app>"
* "Mover <app> aqui"
* "Tirar uma foto"
* "Iniciar gravação"
* "Parar gravação"
* "Aumentar o brilho"
* "Diminuir o brilho"
* "Aumentar o volume"
* "Diminuir o volume"
* "Mudo" ou "desativar mudo"
* "Desligar o dispositivo"
* "Reiniciar o dispositivo"
* "Ir para o estado de suspensão"
* "Qual é o tempo?"
* "A quantidade de bateria que resta?"
* "Call <contact>" (requer o Skype for HoloLens)

## <a name="see-it-say-it"></a>"Vê-lo, digamos"

O HoloLens tem um modelo "vê-lo, digamos" para entrada de voz, em que os rótulos nos botões informam aos usuários quais comandos de voz eles podem dizer também. Por exemplo, ao examinar um aplicativo 2D, um usuário pode dizer o comando "ajustar", que vê na barra de aplicativos para ajustar a posição do aplicativo no mundo.

![Ao examinar um aplicativo ou holograma 2D, um usuário pode dizer o comando "ajustar" que vê na barra de aplicativos para ajustar a posição do aplicativo no mundo](images/microphone-600px.png)

Quando os aplicativos seguem essa regra, os usuários podem entender facilmente o que dizer para controlar o sistema. Para reforçar isso, enquanto nuvens em um botão, você verá uma dica de ferramenta "pesquisa de voz" que aparecerá após um segundo se o botão estiver habilitado para voz e exibirá o comando para falar para "pressionar".

![Vê-lo, digamos que os comandos de ti apareçam abaixo dos botões](images/voice-seeitsayit-600px.png)<br>
*Os comandos "vê-lo, digamos" aparecem abaixo dos botões*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para manipulação rápida de holograma

Também há vários comandos de voz que você pode dizer enquanto nuvens em um holograma para executar rapidamente tarefas de manipulação. Esses comandos de voz funcionam em aplicativos 2D, bem como em objetos 3D que você colocou no mundo.

**Comandos de manipulação de holograma**
* Entre em frente
* Maior | Aprimorou
* Menor

## <a name="dictation"></a>Ditado

Em vez de digitar com [toques de ar](gestures.md#air-tap), o ditado de voz pode ser mais eficiente para inserir texto em um aplicativo. Isso pode acelerar muito a entrada com menos esforço para o usuário.

![O ditado de voz começa selecionando o botão de microfone](images/micbuttonfordictation.png)<br>
*O ditado de voz começa selecionando o botão de microfone no teclado*

Sempre que o teclado Holographic estiver ativo, você poderá alternar para o modo de ditado em vez de digitar. Selecione o microfone no lado da caixa de entrada de texto para começar.

## <a name="communication"></a>Comunicação

Para aplicativos que desejam aproveitar as opções de processamento de entrada de áudio personalizadas fornecidas pelo HoloLens, é importante entender as várias [categorias de fluxo de áudio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que seu aplicativo pode consumir. O Windows 10 dá suporte a várias categorias de fluxo diferentes e o HoloLens usa três delas para habilitar o processamento personalizado para otimizar a qualidade de áudio do microfone adaptada para fala, comunicação e outras que podem ser usadas para áudio de ambiente de ambientes cenários de captura (ou seja, "camcorder").
* A categoria de fluxo AudioCategory_Communications é personalizada para cenários de qualidade de chamada e narração e fornece ao cliente um fluxo de áudio 16kHz 24bit mono da voz do usuário
* A categoria de fluxo AudioCategory_Speech é personalizada para o mecanismo de fala do HoloLens (Windows) e fornece um fluxo 16kHz 24bit mono da voz do usuário. Essa categoria pode ser usada por mecanismos de fala de terceiros, se necessário.
* A categoria de fluxo AudioCategory_Other é personalizada para a gravação de áudio do ambiente ambiental e fornece ao cliente um fluxo de áudio estéreo de 48kHz de 24 bits.

Todo esse processamento de áudio é acelerado por hardware, o que significa que os recursos esgotam muito menos energia do que se o mesmo processamento foi feito na CPU do HoloLens. Evite executar outro processamento de entrada de áudio na CPU para maximizar a vida útil da bateria do sistema e aproveitar o processamento de entrada de áudio descarregado interno.

## <a name="troubleshooting"></a>Solução de problemas

Se você tiver problemas ao usar "Select" e "Ei Cortana", tente mudar para um espaço mais silencioso, desativando a fonte de ruído ou falando mais alto. Neste momento, todo o reconhecimento de fala no HoloLens é ajustado e otimizado especificamente para os palestrantes nativos do Estados Unidos Inglês.

Para o Windows Mixed Reality Developer Edition versão 2017, a lógica de gerenciamento de ponto de extremidade de áudio funcionará bem (para sempre) depois de fazer logoff e voltar para a área de trabalho do PC após a conexão inicial do HMD. Antes do primeiro evento de saída/entrada depois de passar pelo WMR OOBE, o usuário poderia experimentar vários problemas de funcionalidade de áudio, variando de sem áudio para nenhuma alternância de áudio, dependendo de como o sistema foi configurado antes de conectar o HMD pela primeira vez.

## <a name="see-also"></a>Consulte também
* [Entrada de voz no DirectX](voice-input-in-directx.md)
* [Entrada de voz no Unity](voice-input-in-unity.md)
* [Entrada do MR 212: voz](holograms-212.md)

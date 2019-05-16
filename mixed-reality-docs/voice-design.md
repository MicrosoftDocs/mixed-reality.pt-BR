---
title: Comandos de voz
description: Olhar, gesto e voz (GGV) são o principal meio de interação em HoloLens. Este artigo fornece orientação sobre design de voz.
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, design, interação de voz
ms.openlocfilehash: 49fa199b2656db95b15583ccfbee39f33942f180
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730796"
---
# <a name="voice-commanding"></a>Comandos de voz

Ao usar comandos de voz, olhar normalmente é usado como o direcionamento mechaninism, seja como um ponteiro ("select") ou para direcionar o comando para um aplicativo ("vê-lo, diga"). Obviamente, alguns comandos de voz não exigem um destino, como "Ir para iniciar o" ou "Ei, Cortana."


## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></th>
</tr><tr>
<td></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (com fone de ouvido anexado)</td>
</tr>
</table>



## <a name="how-to-use-voice"></a>Como usar voz

Considere a adição de comandos de voz para qualquer experiência que você criar. Voz é uma maneira poderosa e conveniente controlar o sistema e aplicativos. Como usuários falam com uma variedade de dialetos e acentos, a escolha adequada das palavras-chave de conversão de fala será Certifique-se de que comandos dos usuários são interpretados de maneira não ambígua.

### <a name="best-practices"></a>Práticas recomendadas

Abaixo estão algumas práticas que auxiliará no reconhecimento de fala suave.
* **Use comandos concisos** - quando possível, escolha as palavras-chave de duas ou mais sílabas. Uma Sílaba palavras tendem a usar os sons de vogais diferentes quando faladas por pessoas de diferentes acentos. Exemplo: "Reproduzir o vídeo" é melhor do que "Reproduzir o vídeo selecionado no momento"
* **Use o vocabulário simple** -exemplo: "Mostrar Observação" é melhor do que "Mostrar letreiro"
* **Verifique se os comandos são não destrutivos** - Certifique-se de qualquer ação que pode ser executada por um comando de voz é não destrutiva e pode ser facilmente desfeita no caso de outra pessoa que está falando próxima ao usuário acidentalmente aciona um comando.
* **Evitar comandos semelhantes de soar** -evitar registrar vários comandos de fala que parecem muito semelhantes. Exemplo: "Mostrar mais" e "Mostrar store" podem ser muito semelhante com som.
* **Cancelar o registro de seu aplicativo quando ele usa** - quando seu aplicativo não está em um estado em que um comando de fala em particular é válido, considere Cancelando o registro para que outros comandos não fiquem confusos para que um.
* **Teste com diferentes acentos** -testar seu aplicativo com usuários de diferentes acentos.
* **Manter a consistência de comando de voz** - se "Voltar" vai para a página anterior, manter esse comportamento em seus aplicativos.
* **Evite usar comandos do sistema** -os seguintes comandos de voz são reservados para o sistema. Eles não devem ser usados por aplicativos.
   * "Hey Cortana"
   * "Selecionar"

### <a name="select"></a>"Selecionar"

Dizer "selecionar" a qualquer momento ativará a tudo o que o cursor de olhar está apontando. 

>Observação: No HoloLens 2, o cursor olhar precisa primeiro ser invocado por informando que a palavra "select". Por exemplo, "select" novamente para ativar. Para ocultar o cursor de olhar, use suas mãos – airtap ou um objeto de toque. 

### <a name="see-it-say-it"></a>Veja, digamos que ele

Windows Mixed Reality contratou um modelo de voz "vê-lo, diga" onde **rótulos nos botões são idênticos aos comandos de voz associado**. Como não há qualquer dissonance entre o rótulo e o comando de voz, os usuários podem compreender melhor o que dizer para o sistema de controle. Para reforçar isso, enquanto dwelling em um botão, uma **"voz lidam bem com dica"** aparece para se comunicar quais botões são habilitados por voz.


![Vê-lo a dizer a ele exemplo 1](images/voice-seeitsayit1-640px.jpg)

![Vê-lo a dizer a ele exemplo 2](images/voice-seeitsayit2-640px.jpg)<br>
*Exemplos de "vê-lo, diga"*

### <a name="voices-strengths"></a>Vantagens da voz.

Entrada de voz é uma maneira natural para se comunicar nossas intenções. Voz é especialmente BOM na interface **passagens** porque ele pode ajudar os usuários Recortar por meio de várias etapas de uma interface (um usuário pode dizer "Voltar" ao procurar na página da Web, em vez de precisar ir até e pressionar o botão Voltar no aplicativo). Essa economia de tempo de pequenas tem um poderoso **efeito emocional** em usuário lhes potencializar uma pequena quantidade e da percepção da experiência. O uso da voz também é um método conveniente de entrada quando temos nosso braços completos ou estão **multitarefas**. Em dispositivos em que é difícil, digitar em um teclado **ditado de voz** pode ser uma maneira alternativa eficiente de entrada. Por fim, em alguns casos, quando o **intervalo de precisão** para olhar e gesto são limitadas, voz pode ser um usuário somente confiáveis de método de entrada.

**Como o uso da voz pode aproveitar o usuário**
* Reduz o tempo - ele deve fazer com que o objetivo final mais eficiente.
* Minimiza o esforço - ele deve tornar as tarefas mais fluida e sem esforço.
* Reduz a carga cognitiva - é intuitivos e fáceis de lembrar e aprender.
* Ela é socialmente aceitável; ele deve estar de acordo com normas e sociais em termos de comportamento.
* É um rotina - voz prontamente pode se tornar um comportamento habituais.

### <a name="voices-weaknesses"></a>Desvantagens da voz.

Voz também tem algumas desvantagens. Um controle refinado é um deles. (por exemplo um usuário pode dizer "alto", mas não pode dizer quanto. "Um pouco" é difícil quantificar. Movendo ou dimensionamento coisas com voz também é difícil (voz não oferece a granularidade do controle). Voz também pode ser imperfeita. Às vezes, um sistema de voz incorretamente ouve um comando ou não consegue ouvir um comando. Recuperação de tais erros é um desafio em qualquer interface. Por fim, voz pode não ser socialmente aceitável em locais públicos. Há algumas coisas que os usuários não podem ou não devem dizer. Esses cliffs permitem fala a ser usado para o que ele é melhor.

### <a name="voice-feedback-states"></a>Estados de comentários de voz

Quando a voz é aplicada corretamente, o usuário compreenderá **o que eles podem dizer e obtenha comentários claros** o sistema **ouvi-los corretamente**. Esses dois sinais fazer com que o usuário se sentir seguro usando a voz como uma entrada primária. Abaixo está um diagrama que mostra o que acontece com o cursor quando a entrada de voz é reconhecida e como ele se comunica que o usuário.

![Estados de comentários de voz de cursor](images/voicefeedbackstates.png)<br>
*Estados de comentários de voz de cursor*

## <a name="top-things-users-should-know-about-speech-on-windows-mixed-reality"></a>Usuários principais coisas que devem saber sobre "fala", na realidade mista do Windows
* Digamos **"Selecionar"** ao direcionar a um botão (você pode usar isso em qualquer lugar para clicar em um botão).
* Você pode dizer a **nome do rótulo de um botão de barra de aplicativo** em alguns aplicativos para tomar uma ação. Por exemplo, ao examinar um aplicativo, um usuário pode dizer o comando "Remover" para remover o aplicativo do mundo (Isso economiza tempo precise clique nele com a mão).
* Você pode iniciar o Cortana escutando dizendo **"Ei Cortana".** Faça suas perguntas ("Ei Cortana, qual a altura é Torre Eiffel"), diga a ela para abrir um aplicativo ("Ei Cortana, abra Netflix") ou diga a ela para abrir o Menu Iniciar ("Ei Cortana, take me home") e muito mais.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Usuários de perguntas e preocupações comuns têm sobre voz
* O que pode dizer?
* Como saber se que o sistema me ouviu corretamente?
   * O sistema mantém errar Meus comandos de voz.
   * Ele não reage quando posso dar a ele um comando de voz.
* Ele reage a maneira errada de quando eu dê a ele um comando de voz.
* Como direcionar o meu voz a um aplicativo específico ou um comando de aplicativo?
* Pode usar voz para algumas coisas comando quadro holographic em HoloLens?

## <a name="see-also"></a>Consulte também
* [Gestos](gestures.md)
* [Focar direcionamento](gaze-targeting.md)

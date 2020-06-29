---
title: Entrada de voz
description: A entrada de voz é uma entrada principal para o HoloLens e os headsets de imersão de realidade mista do Windows. A voz pode ser usada para comandos, ditado, Cortana e muito mais.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, voz, Cortana, fala, entrada
ms.openlocfilehash: 37364e90aa1d8a7b607a99f4c9b830972f7f80b3
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441823"
---
# <a name="voice-input"></a>Entrada de voz

![Entrada de voz](images/UX/UX_Hero_VoiceCommand.jpg)

A voz é uma das principais formas de entrada no HoloLens. Ele permite que você comando diretamente um holograma sem precisar usar [gestos de mão](gaze-and-commit.md#composite-gestures). A entrada de voz pode ser uma maneira natural de comunicar sua intenção. A voz é especialmente boa na passagem de interfaces complexas, pois permite que os usuários recortem os menus aninhados com um único comando.

A entrada de voz é alimentada pelo [mesmo mecanismo](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que dá suporte à fala em todos os outros _aplicativos universais do Windows_. No HoloLens, o reconhecimento de fala sempre funcionará na linguagem de exibição do Windows configurada em configurações. 

<br>

## <a name="voice-and-gaze"></a>Voz e olhar

Ao usar comandos de voz, o olhar normalmente é usado como o mecanismo de direcionamento, seja com um cursor ("Select") ou para canalizar implicitamente o comando para um aplicativo que você está vendo. Para isso, talvez nem seja necessário mostrar qualquer cursor olhar _("vê-lo, digamos")_. É claro que alguns comandos de voz não exigem um destino, como "ir para iniciar" ou "Ei Cortana".

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
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

**HoloLens (1ª geração)**

Mesmo sem adicionar especificamente suporte de voz ao seu aplicativo, os usuários podem ativar os hologramas simplesmente dizendo o comando de voz do sistema "Select". Isso se comporta da mesma forma que um [toque de ar](gaze-and-commit.md#composite-gestures) no HoloLens, pressionando o botão Selecionar no [clicador de HoloLens](https://docs.microsoft.com/hololens/hololens1-clicker)ou pressionando o gatilho em um [controlador de movimento de realidade mista do Windows](motion-controllers.md). Você ouvirá um som e verá uma dica de ferramenta com "Select" aparecer como confirmação. "Selecionar" é habilitado por um algoritmo de detecção de palavra-chave de baixo consumo de energia para que ele esteja sempre disponível para você, a qualquer momento, com impacto mínimo na vida útil da bateria, mesmo com suas mãos no seu lado.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Para usar o comando de voz "Select" no HoloLens 2, primeiro você precisa abrir o cursor olhar para usar como um ponteiro. O comando para trazê-lo é fácil de lembrar, apenas digamos, "Select".<br><br>
        Para sair do modo, basta usar suas mãos novamente, seja pelo ar tocando, abordando um botão com seus dedos ou usando o gesto do sistema.<br>
        <br>
        *Imagem: Diga "selecionar" para usar o comando de voz para seleção*
    :::column-end:::
        :::column:::
       ![Um usuário pode dizer "selecionar" para usar o comando de voz para uma seleção.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a>Ei Cortana

Você também pode dizer "Ei Cortana" para abrir a Cortana a qualquer momento. Você não precisa esperar que ela pareça continuar perguntando sua pergunta ou dando a ela uma instrução. por exemplo, tente dizer "Ei Cortana, qual é o clima?" como uma única frase. Para obter mais informações sobre a Cortana e o que você pode fazer, basta perguntar a ela! Diga "Ei Cortana, o que eu posso dizer?" e ela receberá uma lista de comandos de trabalho e sugeridos. Se você já estiver no aplicativo Cortana, também poderá clicar no botão **?** na barra lateral para extrair esse mesmo menu.

**Comandos específicos do HoloLens**
* "O que posso falar?"
* "Ir para o início"-em vez de [cair](system-gesture.md#bloom) para chegar ao [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Iniciar <app> "
* "Mover <app> aqui"
* "Tirar uma foto"
* "Iniciar gravação"
* "Parar gravação"
* "Mostrar lado raio"
* "Ocultar mão raio"
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



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"Vê-lo, digamos"<br>
        O HoloLens tem um modelo "vê-lo, digamos" para entrada de voz, em que os rótulos nos botões informam aos usuários quais comandos de voz eles podem dizer também. Por exemplo, ao examinar uma janela de aplicativo no HoloLens (1º gen), um usuário pode dizer o comando "ajustar" que eles veem na barra de aplicativos para ajustar a posição do aplicativo no mundo.<br>
        <br>
        *Imagem: um usuário pode dizer o comando "ajustar" que vê na barra de aplicativos para ajustar a posição do aplicativo*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![Ao examinar uma janela de aplicativo ou um holograma, um usuário pode dizer o comando "ajustar" que vê na barra de aplicativos para ajustar a posição do aplicativo no mundo](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        Quando os aplicativos seguem essa regra, os usuários podem entender facilmente o que dizer para controlar o sistema. Para reforçar isso, enquanto nuvens em um botão no HoloLens (1º gen), você verá uma dica de ferramenta de "pesquisa de voz" que aparecerá após um segundo se o botão estiver habilitado para voz e exibirá o comando para falar para "pressionar". Para revelar as dicas de ferramenta de voz no HoloLens 2, mostre o cursor de voz dizendo "Select" ou "o que eu posso dizer" (consulte a imagem). <br>
        <br>
        *Imagem: "vê-lo, digamos", os comandos aparecem abaixo dos botões*
    :::column-end:::
        :::column:::
       ![Vê-lo, digamos que os comandos de ti apareçam abaixo dos botões](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para manipulação rápida de holograma

Há vários comandos de voz que você pode dizer enquanto nuvens em um holograma para executar rapidamente tarefas de manipulação. Esses comandos de voz funcionam em janelas de aplicativos, bem como em objetos 3D que você colocou no mundo.

**Comandos de manipulação de holograma**
* Entre em frente
* Maior | Aprimorou
* Menor

No HoloLens 2, você também pode criar interações mais naturais em combinação com olhar, que implicitamente fornece informações contextuais sobre o que você está referindo. Por exemplo, você poderia simplesmente olhar para um holograma e dizer "colocar _isso_" e, em seguida, examinar onde deseja colocá-lo e dizer " _aqui_".
Ou você pode examinar uma parte Holographic em um computador complexo e dizer: "Dê-me mais informações sobre _isso_".



## <a name="discovering-voice-commands"></a>Descobrindo comandos de voz

Alguns comandos, como os comandos para manipulação rápida acima, podem ser ocultados. Para saber mais sobre os comandos que você pode usar, olhar em um objeto e, por exemplo, "o que eu posso dizer?". Uma lista de comandos possíveis é exibida. Você também pode usar o cursor olhar de cabeçalho para examinar e revelar as dicas de ferramenta de voz para cada botão na frente de você. 

Se você quiser uma lista completa, basta dizer "Mostrar todos os comandos" a qualquer momento. 


## <a name="dictation"></a>Ditado

Em vez de digitar com [toques de ar](gaze-and-commit.md#composite-gestures), o ditado de voz pode ser mais eficiente para inserir texto em um aplicativo. Isso pode acelerar muito a entrada com menos esforço para o usuário.

![O ditado de voz começa selecionando o botão de microfone](images/micbuttonfordictation.png)<br>
*O ditado de voz começa selecionando o botão de microfone no teclado*

Sempre que o teclado Holographic estiver ativo, você poderá alternar para o modo de ditado em vez de digitar. Selecione o microfone no lado da caixa de entrada de texto para começar.


## <a name="adding-voice-commands-to-your-app"></a>Adicionando comandos de voz ao seu aplicativo

Considere a adição de comandos de voz em qualquer experiência que você criar. A voz é uma maneira poderosa e conveniente de controlar o sistema e os aplicativos. Como os usuários falam com uma variedade de dialetos e sotaques, a escolha adequada das palavras garantirá que os comandos sejam interpretados de maneira inequívoca.

### <a name="best-practices"></a>Práticas recomendadas

A seguir, algumas práticas que auxiliarão em um reconhecimento de fala perfeito.
* **Use comandos concisos** - quando possível, escolha palavras com duas ou mais sílabas. Palavras com uma sílaba tendem a empregar sons de vogais diferentes quando faladas por pessoas com sotaques diferentes. Exemplo: "reproduzir vídeo" é melhor do que "reproduzir o vídeo selecionado no momento"
* **Usar vocabulário simples** -exemplo: "mostrar nota" é melhor do que "mostrar letreiro"
* **Certifique-se de que os comandos não sejam destrutivos** - certifique-se de que as ações que podem ser executadas por um comando de voz não sejam destrutivas e possam ser facilmente desfeitas caso outra pessoa falando nas proximidades do usuário acidentalmente acione um comando.
* **Evite comandos com sons semelhantes** - evite registrar vários comandos de fala muito semelhantes. Exemplo: "mostrar mais" e "mostrar armazenamento" pode ser um som muito semelhante.
* **Cancele o registro do aplicativo quando não estiver em uso** - quando seu aplicativo não estiver em um estado em que um determinado comando de fala seja válido, considere cancelar seu registro para evitar a confusão com outros comandos.
* **Teste com sotaques diferentes** - teste seu aplicativo com usuários que tenham sotaques diferentes.
* **Mantenha a consistência nos comandos de voz** - se "Voltar" vai para a página anterior, mantenha esse comportamento em seus aplicativos.
* **Evite usar comandos do sistema** - os comandos de voz a seguir são reservados para o sistema. Eles não devem ser usados pelos aplicativos.
   * "Ei, Cortana!"
   * "Selecionar"
   * "Ir para o início"

### <a name="advantages-of-voice-input"></a>Vantagens da entrada de voz

A entrada de voz é uma maneira natural de comunicarmos nossas intenções. A voz é especialmente boa em **atravessamentos** de interface porque pode ajudar os usuários a percorrer várias etapas de uma interface (um usuário pode dizer "voltar" ao olhar para uma página da Web, em vez de ter que ir para cima e pressionar o botão voltar no aplicativo). Esse pequeno tempo de salvamento tem um **efeito emocional** poderoso sobre a percepção do usuário da experiência e dá uma pequena quantia superpotência. O uso da voz também é um método de entrada conveniente quando nossos braços estão ocupados ou quando estamos **executando várias tarefas ao mesmo tempo**. Em dispositivos em que é difícil digitar um teclado, o **ditado de voz** pode ser uma maneira alternativa eficiente de inserir texto. Por fim, em alguns casos, quando o **intervalo de precisão** para olhar e gesto é limitado, a voz pode ajudar a desambiguar a intenção do usuário. 

**Como o uso da voz pode beneficiar o usuário?**
* Reduz o tempo - deve tornar o objetivo final mais eficiente.
* Minimiza o esforço - deve tornar as tarefas mais fluídas e simples.
* Reduz a carga cognitiva - é intuitivo e fácil de lembrar e aprender.
* É socialmente aceitável - deve estar de acordo com as normas sociais em termos de comportamento.
* É rotineiro - a voz pode facilmente se tornar um comportamento habitual.

### <a name="challenges-for-voice-input"></a>Desafios para entrada de voz

Embora a entrada de voz seja ótima para muitos aplicativos diferentes, ela também enfrenta vários desafios. Entender as vantagens e os desafios da entrada de voz permite que os desenvolvedores de aplicativos tomem decisões mais inteligentes sobre como e quando usar a entrada de voz e para criar uma ótima experiência para seus usuários.

**Entrada de voz para controle de entrada contínuo** O controle refinado é um deles. Por exemplo, um usuário pode querer alterar seu volume em seu aplicativo de música. Ela pode simplesmente dizer "mais alto", mas não fica claro quanto mais alto o sistema deve fazer o volume. O usuário poderia dizer: "torná-lo um pouco mais alto", mas "um pouco" é difícil quantificar. A movimentação ou o dimensionamento de hologramas com voz é difícil. 

**Confiabilidade da detecção de entrada de voz** Embora os sistemas de entrada de voz se tornem melhores e melhores, às vezes eles podem ouvir e interpretar um comando de voz incorretamente.
A chave é resolver esse desafio em seu aplicativo fornecendo comentários ao usuário quando o sistema está escutando e o que o sistema entendeu para criar uma clareza sobre possíveis problemas no entendimento correto do usuário.  

**Entrada de voz em espaços compartilhados** A voz pode não ser socialmente aceitável em espaços que você compartilha com outras pessoas.
Veja alguns exemplos:
* O usuário pode não querer perturbar outros (por exemplo, em uma biblioteca silenciosa ou em um escritório compartilhado)
* Os usuários podem se sentir inconvenientes sendo vistos por si mesmos em público,
* Um usuário pode sentir-se desconfortável ditando uma mensagem pessoal ou confidencial (incluindo senhas) enquanto outras estão ouvindo

**Entrada de voz de palavras exclusivas ou desconhecidas** As dificuldades de entrada de voz também são fornecidas quando os usuários estão ditando palavras que podem ser desconhecidas do sistema, como apelidos, determinadas palavras gírias ou abreviações. 

**Comandos de voz de aprendizagem** Embora o objetivo final seja conversar naturalmente com seu sistema, muitas vezes, os aplicativos ainda dependem de comandos de voz predefinidos específicos.
Um desafio associado a um grande conjunto de comandos de voz é como ensiná-los sem sobrecarregar o usuário e como ajudar o usuário a mantê-los. 

<br>

---

### <a name="voice-feedback-states"></a>Estados de retorno de voz

Quando a voz é aplicada corretamente, o usuário sabe **o que pode dizer e obtém um retorno claro**, e o sistema **o ouve corretamente**. Esses dois sinais fazem o usuário se sentir seguro para usar a Voz como uma entrada primária. A seguir, um diagrama mostrando o que acontece com o cursor quando a entrada de voz é reconhecida e como ele comunica isso ao usuário.


:::row:::
    :::column:::
       ![1. Estado regular do cursor](images/voicefeedbackstates-regular.jpg)<br>
       **1. Estado regular do cursor**<br>
    :::column-end:::
    :::column:::
       ![2. comunica os comentários de voz e, em seguida, desaparece](images/voicefeedbackstates-voice.jpg)<br>
        **2. comunica os comentários de voz e, em seguida, desaparece**<br>
    :::column-end:::
    :::column:::
       ![Beta. Estado de cursor regular](images/voicefeedbackstates-regular.jpg)<br>
       **3. retorna ao Estado regular do cursor**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>As principais coisas que os usuários devem saber sobre "fala" na realidade misturada
* Diga **"Selecionar"** ao focalizar um botão (você pode usar esse comando em qualquer lugar para clicar em um botão).
* Você pode dizer o **nome do rótulo de um botão da barra de aplicativos** em alguns aplicativos para realizar uma ação. Por exemplo, olhando para um aplicativo, um usuário pode dizer o comando "Remover" para remover o aplicativo do mundo (isso economiza tempo, pois você não precisa clicar nele com a mão).
* Você pode iniciar a escuta da Cortana dizendo **"Ei, Cortana".** Você pode fazer perguntas ("Ei, Cortana! Qual é a altura da Torre Eiffel?"), pedir para ela abrir um aplicativo ("Ei, Cortana! Abra o Netflix") ou pedir para ela abrir o Menu Iniciar ("Ei, Cortana! Abra o menu Iniciar") e muito mais.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Perguntas e preocupações comuns dos usuários em relação à voz
* O que posso falar?
* Como saberei que o sistema me ouviu corretamente?
   * O sistema não entende corretamente meus comandos de voz.
   * Ele não reage quando dou um comando de voz.
* Ele reage de maneira errada quando dou um comando de voz.
* Como direcionar minha voz a um aplicativo específico ou a um comando de aplicativo?
* Posso usar a voz para comandar as coisas no quadro holográfico do HoloLens?

## <a name="communication"></a>Comunicação

Para aplicativos que desejam aproveitar as opções de processamento de entrada de áudio personalizadas fornecidas pelo HoloLens, é importante entender as várias [categorias de fluxo de áudio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que seu aplicativo pode consumir. O Windows 10 dá suporte a várias categorias de fluxo diferentes e o HoloLens usa três delas para habilitar o processamento personalizado para otimizar a qualidade de áudio do microfone adaptada para fala, comunicação e outros que podem ser usados para cenários de captura de áudio de ambiente de ambientes (ou seja, "camcorder").
* A categoria AudioCategory_Communications Stream é personalizada para cenários de qualidade de chamada e narração e fornece ao cliente um fluxo de áudio 16kHz 24bit mono da voz do usuário
* A categoria AudioCategory_Speech Stream é personalizada para o mecanismo de fala do HoloLens (Windows) e fornece um fluxo 16kHz 24bit mono da voz do usuário. Essa categoria pode ser usada por mecanismos de fala de terceiros, se necessário.
* A categoria de AudioCategory_Other Stream é personalizada para a gravação de áudio do ambiente ambiental e fornece ao cliente um fluxo de áudio estéreo de 24 bits 48kHz.

Todo esse processamento de áudio é acelerado por hardware, o que significa que os recursos esgotam muito menos energia do que se o mesmo processamento foi feito na CPU do HoloLens. Evite executar outro processamento de entrada de áudio na CPU para maximizar a vida útil da bateria do sistema e aproveitar o processamento de entrada de áudio descarregado interno.

## <a name="languages"></a>Idiomas

O HoloLens 2 [dá suporte a vários idiomas](https://docs.microsoft.com/hololens/hololens2-language-support). Tenha em mente que os comandos de fala sempre serão executados no idioma de exibição do sistema, mesmo se vários teclados estiverem instalados ou se os aplicativos tentarem criar um reconhecedor de fala em um idioma diferente.

## <a name="troubleshooting"></a>Solução de problemas

Se você tiver problemas ao usar "Select" e "Ei Cortana", tente mudar para um espaço mais silencioso, desativando a fonte de ruído ou falando mais alto. Neste momento, todo o reconhecimento de fala no HoloLens é ajustado e otimizado especificamente para os palestrantes nativos do Estados Unidos Inglês.

Para o Windows Mixed Reality Developer Edition versão 2017, a lógica de gerenciamento de ponto de extremidade de áudio funcionará bem (para sempre) depois de fazer logoff e voltar para a área de trabalho do PC após a conexão inicial do HMD. Antes do primeiro evento de saída/entrada depois de passar pelo WMR OOBE, o usuário poderia experimentar vários problemas de funcionalidade de áudio, variando de sem áudio para nenhuma alternância de áudio, dependendo de como o sistema foi configurado antes de conectar o HMD pela primeira vez.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Entrada de voz em MRTK (Kit de ferramentas de realidade misturada) para Unity
Com o **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, você pode atribuir facilmente o comando de voz em qualquer objeto. Use o **perfil de entrada de fala** do MRTK para definir suas palavras-chave. Ao atribuir o script **SpeechInputHandler** , você pode fazer com que qualquer objeto responda às palavras-chave definidas no perfil de entrada de fala. O SpeechInputHandler também fornece um rótulo de confirmação de fala para melhorar a confiança do usuário.

* [MRTK-comando de voz](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a>Veja também
* [Focar e confirmar](gaze-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada do MR 212: voz](holograms-212.md)
* [Entrada de voz no DirectX](voice-input-in-directx.md)
* [Entrada de voz no Unity](voice-input-in-unity.md)

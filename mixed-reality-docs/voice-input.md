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
# <a name="voice-input"></a><span data-ttu-id="ce3d0-105">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="ce3d0-105">Voice input</span></span>

<span data-ttu-id="ce3d0-106">Voz é uma das três formas principais de entrada em HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="ce3d0-107">Ele permite que um holograma de comando diretamente sem ter que usar [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="ce3d0-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="ce3d0-108">Você simplesmente [olhares](gaze.md) em um holograma e fale seu comando.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="ce3d0-109">Entrada de voz pode ser uma maneira natural para se comunicar sua intenção.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="ce3d0-110">Voz é especialmente bons atravessando interfaces complexas porque ele permite que os usuários acabando com menus aninhados com um único comando.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="ce3d0-111">Entrada de voz é alimentada pela [mesmo mecanismo](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que dá suporte à conversão de fala em todos os outros aplicativos universais do Windows.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="ce3d0-112">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="ce3d0-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ce3d0-113"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="ce3d0-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="ce3d0-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="ce3d0-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="ce3d0-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ce3d0-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="ce3d0-116"><a href="immersive-headset-hardware-details.md"><strong>Fones imersivos em exposição</strong></a></span><span class="sxs-lookup"><span data-stu-id="ce3d0-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ce3d0-117">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="ce3d0-117">Voice input</span></span></td>
        <td><span data-ttu-id="ce3d0-118">✔️</span><span class="sxs-lookup"><span data-stu-id="ce3d0-118">✔️</span></span></td>
        <td><span data-ttu-id="ce3d0-119">✔️</span><span class="sxs-lookup"><span data-stu-id="ce3d0-119">✔️</span></span></td>
        <td><span data-ttu-id="ce3d0-120">✔️ (com o microfone)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="ce3d0-121">O comando "select"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-121">The "select" command</span></span>

<span data-ttu-id="ce3d0-122">Mesmo sem adicionar especificamente o suporte de voz ao seu aplicativo, os usuários podem ativar hologramas simplesmente dizendo "select".</span><span class="sxs-lookup"><span data-stu-id="ce3d0-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="ce3d0-123">Esse comportamento é o mesmo que um [polegar](gestures.md#air-tap) em HoloLens, pressionando o botão de seleção no [clicker HoloLens](hardware-accessories.md#hololens-clicker), ou pressionando o gatilho em um [controlador de animação do Windows Mixed Reality](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="ce3d0-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="ce3d0-124">Você ouvir um som e verá uma dica de ferramenta com "select" aparecem como confirmação.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="ce3d0-125">"Selecionar" é habilitado por um algoritmo de detecção de palavra-chave de baixa energia, para que ele esteja sempre disponível para você dizer a qualquer momento com o impacto de vida útil da bateria mínima, mesmo com as mãos ao seu lado.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="ce3d0-126">Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="ce3d0-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="ce3d0-127">![Diga "selecionar" usar o comando de voz para seleção](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="ce3d0-128">*Diga "selecionar" usar o comando de voz para seleção*</span><span class="sxs-lookup"><span data-stu-id="ce3d0-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="ce3d0-129">Ei Cortana</span><span class="sxs-lookup"><span data-stu-id="ce3d0-129">Hey Cortana</span></span>

<span data-ttu-id="ce3d0-130">Você também pode dizer "Ei Cortana" para abrir a Cortana a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="ce3d0-131">Você não precisa esperar para ela aparecer continuar solicitando sua pergunta ou dar a ela uma instrução - por exemplo, tente dizendo "Ei Cortana o que é o clima?"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="ce3d0-132">como uma única sentença.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-132">as a single sentence.</span></span> <span data-ttu-id="ce3d0-133">Para obter mais informações sobre o Cortana e o que você pode fazer, simplesmente pergunte dela.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="ce3d0-134">Dizer "Ei Cortana, o que devo dizer?"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="ce3d0-135">e ela vai puxar uma lista de comandos de trabalho e sugerido.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="ce3d0-136">Se você já estiver no aplicativo do Cortana você também pode clicar o **?**</span><span class="sxs-lookup"><span data-stu-id="ce3d0-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="ce3d0-137">ícone na barra lateral para efetuar pull de backup nesse mesmo menu.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="ce3d0-138">**Comandos específicos ao HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ce3d0-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="ce3d0-139">"O que posso falar?"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-139">"What can I say?"</span></span>
* <span data-ttu-id="ce3d0-140">"Ir para casa" ou "Go to Start" – em vez de [bloom](gestures.md#bloom) para chegar ao [Menu Iniciar](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="ce3d0-141">"Iniciar <app>"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-141">"Launch <app>"</span></span>
* <span data-ttu-id="ce3d0-142">"Mover <app> aqui"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-142">"Move <app> here"</span></span>
* <span data-ttu-id="ce3d0-143">"Tirar uma foto"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-143">"Take a picture"</span></span>
* <span data-ttu-id="ce3d0-144">"Iniciar gravação"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-144">"Start recording"</span></span>
* <span data-ttu-id="ce3d0-145">"Parar a gravação"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-145">"Stop recording"</span></span>
* <span data-ttu-id="ce3d0-146">"Increase o brilho"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-146">"Increase the brightness"</span></span>
* <span data-ttu-id="ce3d0-147">"Decrease o brilho"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="ce3d0-148">"Aumentar o volume"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-148">"Increase the volume"</span></span>
* <span data-ttu-id="ce3d0-149">"Diminuir o volume"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-149">"Decrease the volume"</span></span>
* <span data-ttu-id="ce3d0-150">"Mudo" ou "Ativar"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="ce3d0-151">"Desligar o dispositivo"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-151">"Shut down the device"</span></span>
* <span data-ttu-id="ce3d0-152">"Reiniciar o dispositivo"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-152">"Restart the device"</span></span>
* <span data-ttu-id="ce3d0-153">"Ir para o modo de suspensão"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-153">"Go to sleep"</span></span>
* <span data-ttu-id="ce3d0-154">"Qual horário é?"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-154">"What time is it?"</span></span>
* <span data-ttu-id="ce3d0-155">"Quanto bateria restam?"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="ce3d0-156">"Chamar <contact>" (requer o Skype para HoloLens)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="ce3d0-157">"Vê-lo, diga"</span><span class="sxs-lookup"><span data-stu-id="ce3d0-157">"See It, Say It"</span></span>

<span data-ttu-id="ce3d0-158">HoloLens tem um modelo de "vê-lo, diga" para entrada de voz, onde os rótulos de botões de dizer aos usuários quais comandos de voz também pode dizem.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="ce3d0-159">Por exemplo, ao examinar um aplicativo 2D, um usuário pode dizer o comando "Ajuste" que eles veem na barra de aplicativos para ajustar a posição do aplicativo do mundo.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![Ao examinar um aplicativo 2D ou holograma, um usuário pode dizer que o comando "Ajuste" que eles veem na barra de aplicativos para ajustar a posição do aplicativo do mundo](images/microphone-600px.png)

<span data-ttu-id="ce3d0-161">Quando os aplicativos seguem essa regra, os usuários podem facilmente entender o que dizer para o sistema de controle.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="ce3d0-162">Para reforçar isso, ao mesmo tempo Observação em um botão, você verá uma dica de ferramenta "duração de voz" que surge após um segundo, se o botão é habilitado para voz e exibe o comando falar para "pressionar"-lo.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="ce3d0-163">![Veja, digamos que ele comandos aparecem abaixo dos botões](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="ce3d0-164">*"Dificultando, diga" comandos aparecem abaixo dos botões*</span><span class="sxs-lookup"><span data-stu-id="ce3d0-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="ce3d0-165">Comandos de voz para a manipulação rápida de holograma</span><span class="sxs-lookup"><span data-stu-id="ce3d0-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="ce3d0-166">Também há um número de voz comandos que você pode dizer ao Observação em um holograma para realizar rapidamente tarefas de manipulação.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="ce3d0-167">Esses comandos de voz funcionam em aplicativos 2D, bem como objetos 3D que você tenha colocado no mundo.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="ce3d0-168">**Comandos de manipulação de holograma**</span><span class="sxs-lookup"><span data-stu-id="ce3d0-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="ce3d0-169">Enfrentam me</span><span class="sxs-lookup"><span data-stu-id="ce3d0-169">Face me</span></span>
* <span data-ttu-id="ce3d0-170">Maior | Aprimorar</span><span class="sxs-lookup"><span data-stu-id="ce3d0-170">Bigger | Enhance</span></span>
* <span data-ttu-id="ce3d0-171">Menor</span><span class="sxs-lookup"><span data-stu-id="ce3d0-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="ce3d0-172">Ditado</span><span class="sxs-lookup"><span data-stu-id="ce3d0-172">Dictation</span></span>

<span data-ttu-id="ce3d0-173">Em vez de digitar com [toques de ar](gestures.md#air-tap), ditado de voz pode ser mais eficiente para inserir texto em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="ce3d0-174">Isso pode acelerar a entrada com menos esforço do usuário bastante.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="ce3d0-175">![Voz ditado inicia selecionando o botão de microfone](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="ce3d0-176">*Voz ditado inicia selecionando o botão de microfone no teclado*</span><span class="sxs-lookup"><span data-stu-id="ce3d0-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="ce3d0-177">Sempre que o teclado holográfico estiver ativo, você pode alternar para o modo de ditado em vez de digitar.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="ce3d0-178">Selecione o microfone no lado da caixa de texto de entrada para começar a usar.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="ce3d0-179">Comunicação</span><span class="sxs-lookup"><span data-stu-id="ce3d0-179">Communication</span></span>

<span data-ttu-id="ce3d0-180">Para aplicativos que desejam aproveitar as opções fornecidas pelo HoloLens de processamento de entrada de áudio personalizada, é importante entender os vários [categorias de fluxo de áudio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) seu aplicativo pode consumir.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="ce3d0-181">Aceita de Windows 10 faz várias categorias diferentes de fluxo e HoloLens a utilização de esses três para habilitar o processamento personalizado otimizar a qualidade de áudio do microfone sob medida para fala, comunicação e outros que pode ser usado para áudio do ambiente do ambiente cenários de captura (isto é, "filmadoras").</span><span class="sxs-lookup"><span data-stu-id="ce3d0-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="ce3d0-182">A categoria de fluxo de AudioCategory_Communications é personalizada para cenários de qualidade e narração de chamada e fornece ao cliente com um fluxo de áudio mono 16kHz 24 bits de voz do usuário</span><span class="sxs-lookup"><span data-stu-id="ce3d0-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="ce3d0-183">A categoria de fluxo de AudioCategory_Speech é personalizada para o mecanismo de fala do HoloLens (Windows) e fornece-o com um fluxo de 16 bits de 24 kHz mono de voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="ce3d0-184">Esta categoria pode ser usada pelos mecanismos de fala 3ª parte, se necessário.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="ce3d0-185">A categoria de fluxo de AudioCategory_Other é personalizada para gravação de áudio do ambiente do ambiente e fornece ao cliente com um fluxo de áudio estéreo de 48kHz 24 bits.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="ce3d0-186">Todo esse processamento de áudio é o que significa que os recursos drenar muito menos energia do que se o mesmo processamento foi feito na CPU HoloLens acelerados por hardware.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="ce3d0-187">Evite executar outra entrada de áudio de processamento na CPU para maximizar a vida útil da bateria de sistema e tirar proveito da compilação, descarregados o processamento de entrada de áudio.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="ce3d0-188">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="ce3d0-188">Troubleshooting</span></span>

<span data-ttu-id="ce3d0-189">Se você estiver tendo quaisquer problemas usando "select" e "Ei Cortana", tente mover para um espaço mais discreta, a ativação para a fonte de ruído ou falando mais alto.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="ce3d0-190">Neste momento, todos os o reconhecimento de fala em HoloLens é ajustado e otimizado especificamente para nativos alto-falantes de inglês dos Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="ce3d0-191">Edição de desenvolvedor de realidade mista do Windows na versão de 2017, a lógica de gerenciamento de ponto de extremidade de áudio funcionarão bem (para sempre) após o registro em log fora e de volta na área de trabalho do computador após a conexão inicial do HMD.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="ce3d0-192">Antes de entrada primeiro out/no evento depois de passar por WMR OOBE, o usuário pode apresentar vários problemas de funcionalidade de áudio, variando de sem áudio para áudio de alternância, dependendo de como o sistema foi definido antes de conectar o HMD pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce3d0-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce3d0-193">See also</span></span>
* [<span data-ttu-id="ce3d0-194">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="ce3d0-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="ce3d0-195">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="ce3d0-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="ce3d0-196">Entrada do MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="ce3d0-196">MR Input 212: Voice</span></span>](holograms-212.md)

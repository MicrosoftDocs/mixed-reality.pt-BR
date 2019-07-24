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
# <a name="voice-input"></a><span data-ttu-id="2ee65-105">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="2ee65-105">Voice input</span></span>

<span data-ttu-id="2ee65-106">Voz é uma das três formas principais de entrada no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ee65-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="2ee65-107">Ele permite que você comando diretamente um holograma sem precisar usar [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="2ee65-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="2ee65-108">Basta [olhar](gaze.md) um holograma e falar sobre o comando.</span><span class="sxs-lookup"><span data-stu-id="2ee65-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="2ee65-109">A entrada de voz pode ser uma maneira natural de comunicar sua intenção.</span><span class="sxs-lookup"><span data-stu-id="2ee65-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="2ee65-110">A voz é especialmente boa na passagem de interfaces complexas porque permite que os usuários recortem os menus aninhados com um único comando.</span><span class="sxs-lookup"><span data-stu-id="2ee65-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="2ee65-111">A entrada de voz é alimentada pelo [mesmo mecanismo](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que dá suporte à fala em todos os outros aplicativos universais do Windows.</span><span class="sxs-lookup"><span data-stu-id="2ee65-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="2ee65-112">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="2ee65-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2ee65-113"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="2ee65-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2ee65-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2ee65-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2ee65-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2ee65-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2ee65-116"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="2ee65-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2ee65-117">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="2ee65-117">Voice input</span></span></td>
        <td><span data-ttu-id="2ee65-118">✔️</span><span class="sxs-lookup"><span data-stu-id="2ee65-118">✔️</span></span></td>
        <td><span data-ttu-id="2ee65-119">✔️</span><span class="sxs-lookup"><span data-stu-id="2ee65-119">✔️</span></span></td>
        <td><span data-ttu-id="2ee65-120">✔️ (com microfone)</span><span class="sxs-lookup"><span data-stu-id="2ee65-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="2ee65-121">O comando "Select"</span><span class="sxs-lookup"><span data-stu-id="2ee65-121">The "select" command</span></span>

<span data-ttu-id="2ee65-122">Mesmo sem adicionar especificamente suporte de voz ao seu aplicativo, os usuários podem ativar os hologramas simplesmente dizendo "Select".</span><span class="sxs-lookup"><span data-stu-id="2ee65-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="2ee65-123">Isso se comporta da mesma forma que um [toque de ar](gestures.md#air-tap) no HoloLens, pressionando o botão Selecionar no [clicador de HoloLens](hardware-accessories.md#hololens-clicker)ou pressionando o gatilho em um [controlador de movimento de realidade mista do Windows](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="2ee65-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="2ee65-124">Você ouvirá um som e verá uma dica de ferramenta com "Select" aparecer como confirmação.</span><span class="sxs-lookup"><span data-stu-id="2ee65-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="2ee65-125">"Selecionar" é habilitado por um algoritmo de detecção de palavra-chave de baixo consumo de energia para que ele esteja sempre disponível para você, a qualquer momento, com impacto mínimo na vida útil da bateria, mesmo com suas mãos no seu lado.</span><span class="sxs-lookup"><span data-stu-id="2ee65-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="2ee65-126">Mais diretrizes específicas para o HoloLens 2 em [breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="2ee65-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="2ee65-127">![Diga "Select" para usar o comando de voz para seleção](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="2ee65-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="2ee65-128">*Diga "Select" para usar o comando de voz para seleção*</span><span class="sxs-lookup"><span data-stu-id="2ee65-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="2ee65-129">Ei Cortana</span><span class="sxs-lookup"><span data-stu-id="2ee65-129">Hey Cortana</span></span>

<span data-ttu-id="2ee65-130">Você também pode dizer "Ei Cortana" para abrir a Cortana a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="2ee65-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="2ee65-131">Você não precisa esperar que ela pareça continuar perguntando sua pergunta ou dando a ela uma instrução. por exemplo, tente dizer "Ei Cortana o que é o clima?"</span><span class="sxs-lookup"><span data-stu-id="2ee65-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="2ee65-132">como uma única frase.</span><span class="sxs-lookup"><span data-stu-id="2ee65-132">as a single sentence.</span></span> <span data-ttu-id="2ee65-133">Para obter mais informações sobre a Cortana e o que você pode fazer, basta perguntar a ela!</span><span class="sxs-lookup"><span data-stu-id="2ee65-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="2ee65-134">Diga "Ei Cortana o que eu posso dizer?"</span><span class="sxs-lookup"><span data-stu-id="2ee65-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="2ee65-135">e ela receberá uma lista de comandos de trabalho e sugeridos.</span><span class="sxs-lookup"><span data-stu-id="2ee65-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="2ee65-136">Se você já estiver no aplicativo Cortana, também poderá clicar no botão **?**</span><span class="sxs-lookup"><span data-stu-id="2ee65-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="2ee65-137">na barra lateral para extrair esse mesmo menu.</span><span class="sxs-lookup"><span data-stu-id="2ee65-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="2ee65-138">**Comandos específicos do HoloLens**</span><span class="sxs-lookup"><span data-stu-id="2ee65-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="2ee65-139">"O que posso falar?"</span><span class="sxs-lookup"><span data-stu-id="2ee65-139">"What can I say?"</span></span>
* <span data-ttu-id="2ee65-140">"Ir para a página inicial" ou "ir para o início"-em vez de [cair](gestures.md#bloom) para chegar ao [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="2ee65-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="2ee65-141">"Iniciar <app>"</span><span class="sxs-lookup"><span data-stu-id="2ee65-141">"Launch <app>"</span></span>
* <span data-ttu-id="2ee65-142">"Mover <app> aqui"</span><span class="sxs-lookup"><span data-stu-id="2ee65-142">"Move <app> here"</span></span>
* <span data-ttu-id="2ee65-143">"Tirar uma foto"</span><span class="sxs-lookup"><span data-stu-id="2ee65-143">"Take a picture"</span></span>
* <span data-ttu-id="2ee65-144">"Iniciar gravação"</span><span class="sxs-lookup"><span data-stu-id="2ee65-144">"Start recording"</span></span>
* <span data-ttu-id="2ee65-145">"Parar gravação"</span><span class="sxs-lookup"><span data-stu-id="2ee65-145">"Stop recording"</span></span>
* <span data-ttu-id="2ee65-146">"Aumentar o brilho"</span><span class="sxs-lookup"><span data-stu-id="2ee65-146">"Increase the brightness"</span></span>
* <span data-ttu-id="2ee65-147">"Diminuir o brilho"</span><span class="sxs-lookup"><span data-stu-id="2ee65-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="2ee65-148">"Aumentar o volume"</span><span class="sxs-lookup"><span data-stu-id="2ee65-148">"Increase the volume"</span></span>
* <span data-ttu-id="2ee65-149">"Diminuir o volume"</span><span class="sxs-lookup"><span data-stu-id="2ee65-149">"Decrease the volume"</span></span>
* <span data-ttu-id="2ee65-150">"Mudo" ou "desativar mudo"</span><span class="sxs-lookup"><span data-stu-id="2ee65-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="2ee65-151">"Desligar o dispositivo"</span><span class="sxs-lookup"><span data-stu-id="2ee65-151">"Shut down the device"</span></span>
* <span data-ttu-id="2ee65-152">"Reiniciar o dispositivo"</span><span class="sxs-lookup"><span data-stu-id="2ee65-152">"Restart the device"</span></span>
* <span data-ttu-id="2ee65-153">"Ir para o estado de suspensão"</span><span class="sxs-lookup"><span data-stu-id="2ee65-153">"Go to sleep"</span></span>
* <span data-ttu-id="2ee65-154">"Qual é o tempo?"</span><span class="sxs-lookup"><span data-stu-id="2ee65-154">"What time is it?"</span></span>
* <span data-ttu-id="2ee65-155">"A quantidade de bateria que resta?"</span><span class="sxs-lookup"><span data-stu-id="2ee65-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="2ee65-156">"Call <contact>" (requer o Skype for HoloLens)</span><span class="sxs-lookup"><span data-stu-id="2ee65-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="2ee65-157">"Vê-lo, digamos"</span><span class="sxs-lookup"><span data-stu-id="2ee65-157">"See It, Say It"</span></span>

<span data-ttu-id="2ee65-158">O HoloLens tem um modelo "vê-lo, digamos" para entrada de voz, em que os rótulos nos botões informam aos usuários quais comandos de voz eles podem dizer também.</span><span class="sxs-lookup"><span data-stu-id="2ee65-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="2ee65-159">Por exemplo, ao examinar um aplicativo 2D, um usuário pode dizer o comando "ajustar", que vê na barra de aplicativos para ajustar a posição do aplicativo no mundo.</span><span class="sxs-lookup"><span data-stu-id="2ee65-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![Ao examinar um aplicativo ou holograma 2D, um usuário pode dizer o comando "ajustar" que vê na barra de aplicativos para ajustar a posição do aplicativo no mundo](images/microphone-600px.png)

<span data-ttu-id="2ee65-161">Quando os aplicativos seguem essa regra, os usuários podem entender facilmente o que dizer para controlar o sistema.</span><span class="sxs-lookup"><span data-stu-id="2ee65-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="2ee65-162">Para reforçar isso, enquanto nuvens em um botão, você verá uma dica de ferramenta "pesquisa de voz" que aparecerá após um segundo se o botão estiver habilitado para voz e exibirá o comando para falar para "pressionar".</span><span class="sxs-lookup"><span data-stu-id="2ee65-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="2ee65-163">![Vê-lo, digamos que os comandos de ti apareçam abaixo dos botões](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="2ee65-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="2ee65-164">*Os comandos "vê-lo, digamos" aparecem abaixo dos botões*</span><span class="sxs-lookup"><span data-stu-id="2ee65-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="2ee65-165">Comandos de voz para manipulação rápida de holograma</span><span class="sxs-lookup"><span data-stu-id="2ee65-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="2ee65-166">Também há vários comandos de voz que você pode dizer enquanto nuvens em um holograma para executar rapidamente tarefas de manipulação.</span><span class="sxs-lookup"><span data-stu-id="2ee65-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="2ee65-167">Esses comandos de voz funcionam em aplicativos 2D, bem como em objetos 3D que você colocou no mundo.</span><span class="sxs-lookup"><span data-stu-id="2ee65-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="2ee65-168">**Comandos de manipulação de holograma**</span><span class="sxs-lookup"><span data-stu-id="2ee65-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="2ee65-169">Entre em frente</span><span class="sxs-lookup"><span data-stu-id="2ee65-169">Face me</span></span>
* <span data-ttu-id="2ee65-170">Maior | Aprimorou</span><span class="sxs-lookup"><span data-stu-id="2ee65-170">Bigger | Enhance</span></span>
* <span data-ttu-id="2ee65-171">Menor</span><span class="sxs-lookup"><span data-stu-id="2ee65-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="2ee65-172">Ditado</span><span class="sxs-lookup"><span data-stu-id="2ee65-172">Dictation</span></span>

<span data-ttu-id="2ee65-173">Em vez de digitar com [toques de ar](gestures.md#air-tap), o ditado de voz pode ser mais eficiente para inserir texto em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ee65-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="2ee65-174">Isso pode acelerar muito a entrada com menos esforço para o usuário.</span><span class="sxs-lookup"><span data-stu-id="2ee65-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="2ee65-175">![O ditado de voz começa selecionando o botão de microfone](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="2ee65-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="2ee65-176">*O ditado de voz começa selecionando o botão de microfone no teclado*</span><span class="sxs-lookup"><span data-stu-id="2ee65-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="2ee65-177">Sempre que o teclado Holographic estiver ativo, você poderá alternar para o modo de ditado em vez de digitar.</span><span class="sxs-lookup"><span data-stu-id="2ee65-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="2ee65-178">Selecione o microfone no lado da caixa de entrada de texto para começar.</span><span class="sxs-lookup"><span data-stu-id="2ee65-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="2ee65-179">Comunicação</span><span class="sxs-lookup"><span data-stu-id="2ee65-179">Communication</span></span>

<span data-ttu-id="2ee65-180">Para aplicativos que desejam aproveitar as opções de processamento de entrada de áudio personalizadas fornecidas pelo HoloLens, é importante entender as várias [categorias de fluxo de áudio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que seu aplicativo pode consumir.</span><span class="sxs-lookup"><span data-stu-id="2ee65-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="2ee65-181">O Windows 10 dá suporte a várias categorias de fluxo diferentes e o HoloLens usa três delas para habilitar o processamento personalizado para otimizar a qualidade de áudio do microfone adaptada para fala, comunicação e outras que podem ser usadas para áudio de ambiente de ambientes cenários de captura (ou seja, "camcorder").</span><span class="sxs-lookup"><span data-stu-id="2ee65-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="2ee65-182">A categoria de fluxo AudioCategory_Communications é personalizada para cenários de qualidade de chamada e narração e fornece ao cliente um fluxo de áudio 16kHz 24bit mono da voz do usuário</span><span class="sxs-lookup"><span data-stu-id="2ee65-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="2ee65-183">A categoria de fluxo AudioCategory_Speech é personalizada para o mecanismo de fala do HoloLens (Windows) e fornece um fluxo 16kHz 24bit mono da voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="2ee65-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="2ee65-184">Essa categoria pode ser usada por mecanismos de fala de terceiros, se necessário.</span><span class="sxs-lookup"><span data-stu-id="2ee65-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="2ee65-185">A categoria de fluxo AudioCategory_Other é personalizada para a gravação de áudio do ambiente ambiental e fornece ao cliente um fluxo de áudio estéreo de 48kHz de 24 bits.</span><span class="sxs-lookup"><span data-stu-id="2ee65-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="2ee65-186">Todo esse processamento de áudio é acelerado por hardware, o que significa que os recursos esgotam muito menos energia do que se o mesmo processamento foi feito na CPU do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ee65-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="2ee65-187">Evite executar outro processamento de entrada de áudio na CPU para maximizar a vida útil da bateria do sistema e aproveitar o processamento de entrada de áudio descarregado interno.</span><span class="sxs-lookup"><span data-stu-id="2ee65-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="2ee65-188">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="2ee65-188">Troubleshooting</span></span>

<span data-ttu-id="2ee65-189">Se você tiver problemas ao usar "Select" e "Ei Cortana", tente mudar para um espaço mais silencioso, desativando a fonte de ruído ou falando mais alto.</span><span class="sxs-lookup"><span data-stu-id="2ee65-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="2ee65-190">Neste momento, todo o reconhecimento de fala no HoloLens é ajustado e otimizado especificamente para os palestrantes nativos do Estados Unidos Inglês.</span><span class="sxs-lookup"><span data-stu-id="2ee65-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="2ee65-191">Para o Windows Mixed Reality Developer Edition versão 2017, a lógica de gerenciamento de ponto de extremidade de áudio funcionará bem (para sempre) depois de fazer logoff e voltar para a área de trabalho do PC após a conexão inicial do HMD.</span><span class="sxs-lookup"><span data-stu-id="2ee65-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="2ee65-192">Antes do primeiro evento de saída/entrada depois de passar pelo WMR OOBE, o usuário poderia experimentar vários problemas de funcionalidade de áudio, variando de sem áudio para nenhuma alternância de áudio, dependendo de como o sistema foi configurado antes de conectar o HMD pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="2ee65-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ee65-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ee65-193">See also</span></span>
* [<span data-ttu-id="2ee65-194">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="2ee65-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="2ee65-195">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="2ee65-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="2ee65-196">Entrada do MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="2ee65-196">MR Input 212: Voice</span></span>](holograms-212.md)
